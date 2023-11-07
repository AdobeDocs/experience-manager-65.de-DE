---
title: Fehlerbehebung bei Replikationsproblemen
description: Dieser Artikel enthält Informationen zur Fehlerbehebung bei Replikationsproblemen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
exl-id: cfa822c8-f9a9-4122-9eac-0293d525f6b5
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 42%

---

# Fehlerbehebung bei Replikationsproblemen{#troubleshooting-replication}

Auf dieser Seite finden Sie Informationen zur Fehlerbehebung bei Replikationsproblemen.

## Problem {#problem}

Die Replikation (Nicht-Rückwärtsreplikation) schlägt aus irgendeinem Grund fehl.

## Auflösung {#resolution}

Es gibt verschiedene Gründe, warum eine Replikation fehlschlägt. In diesem Artikel wird der Ansatz erläutert, den man bei der Analyse dieser Probleme wählen könnte.

**Werden beim Klicken auf die Schaltfläche „Aktivieren“ irgendwelche Replikationen ausgelöst? Wenn NICHT, gehen Sie wie folgt vor:**

1. Wechseln Sie zu /crx/explorer und melden Sie sich als Admin an.
1. Öffnen Sie &quot;Content Explorer&quot;.
1. Überprüfen Sie, ob der Knoten „/bin/replicate“ oder „/bin/replicate.json“ vorhanden ist. Wenn der Knoten vorhanden ist, löschen Sie ihn und speichern Sie ihn.

**Werden die Replikationen in den Warteschlangen des Replikationsagenten in die Warteschlange gestellt?**

Gehen Sie dazu zu /etc/replication/agents.author.html und klicken Sie dann auf die zu prüfenden Replikationsagenten.

**Wenn eine oder einige Agentenwarteschlangen hängen geblieben sind:**

1. Lautet der Status der Warteschlange **gesperrt**? Wenn ja, wird die Veröffentlichungsinstanz nicht ausgeführt oder reagiert sie nicht? Überprüfen Sie die Veröffentlichungsinstanz, um zu sehen, was mit ihr nicht stimmt. Überprüfen Sie also die Protokolle und überprüfen Sie, ob ein OutOfMemory-Fehler oder ein anderes Problem vorliegt. Wenn es nur langsam ist, dann nehmen Sie Thread-Dumps und analysieren Sie sie.
1. Lautet der Status der Warteschlange **Warteschlange ist aktiv - x ausstehend**? Grundsätzlich kann der Replikationsauftrag in einem Socket-Lese stecken bleiben, der darauf wartet, dass die Veröffentlichungsinstanz oder der Dispatcher antwortet. Dies könnte bedeuten, dass die Veröffentlichungsinstanz oder der Dispatcher unter hoher Last oder in einem Schloss stecken bleibt. Nehmen Sie in diesem Fall Thread-Sicherheitskopien von der Autoren- und Veröffentlichungsinstanz vor.

   * Öffnen Sie die Thread-Sicherheitskopien von der Autoreninstanz in einem Thread-Dump-Analyzer und überprüfen Sie, ob der Sling-Ereignisauftrag des Replikationsagenten in einem socketRead-Vorgang feststeckt.
   * Öffnen Sie die Thread-Sicherungskopien der Veröffentlichungsinstanz in einem Analyzer für Thread-Sicherungskopien und analysieren Sie, aus welchen Grund die Veröffentlichungsinstanz möglicherweise nicht reagiert. Sie sollten einen Thread mit der POST /bin/receive im Namen sehen, der den Thread darstellt, der die Replikation von der Autoreninstanz erhält.

**Wenn alle Agentenwarteschlangen hängen geblieben sind:**

1. Möglicherweise kann ein bestimmter Teil des Inhalts aufgrund eines beschädigten Repositorys oder eines anderen Problems nicht unter /var/replication/data serialisiert werden. Überprüfen Sie die Datei „logs/error.log“ auf einen entsprechenden Fehler. Gehen Sie wie folgt vor, um das fehlerhafte Replikationselement zu entfernen:

   1. Wechseln Sie zu https://&lt;Host>:&lt;Port>/crx/de und melden Sie sich als Admin an.
   1. Klicken Sie im oberen Menü auf &quot;Tools&quot;.
   1. Klicken Sie auf die Lupe.
   1. Wählen Sie &quot;XPath&quot;als Typ aus.
   1. Geben Sie die folgende Abfrage in das Feld „Abfrage“ ein: /jcr:root/var/eventing/jobs//element(&#42;,slingevent:Job) order by @slingevent:created
   1. Klicken Sie auf &quot;Suchen&quot;.
   1. In den Ergebnissen sind die wichtigsten Elemente die neuesten Sling-Ereignisaufträge. Klicken Sie auf die einzelnen Replikationen und suchen Sie nach den fixierten Replikationen, die mit denen oben in der Warteschlange übereinstimmen.

1. Möglicherweise liegt ein Problem mit den Auftragswarteschlangen des Sling-Eventing-Frameworks vor. Versuchen Sie, das Bundle org.apache.sling.event in der /system/console neu zu starten.
1. Möglicherweise ist die Auftragsverarbeitung deaktiviert. Dies kann in der Felix-Konsole auf der Registerkarte „Sling Eventing“ überprüft werden. Überprüfen Sie, ob es angezeigt wird - Apache Sling Eventing (JOB PROCESSING IST DEAKTIVIERT!)

   * Ist dies der Fall, überprüfen Sie auf der Registerkarte „Configuration“ der Felix-Konsole den Apache Sling Job Event Handler. Möglicherweise ist das Kontrollkästchen für „Job Processing Enabled“ deaktiviert. Falls es aktiviert ist und weiter „Job Processing Disabled“ angezeigt wird, überprüfen Sie, ob unter „/apps/system/config“ eine Überlagerung vorhanden ist, die die Auftragsverarbeitung deaktiviert. Versuchen Sie, einen osgi:config -Knoten für jobmanager.enabled mit einem booleschen Wert &quot;true&quot;zu erstellen und überprüfen Sie erneut, ob die Aktivierung gestartet wurde und keine Aufträge mehr in der Warteschlange sind.

1. Möglicherweise ist auch der Status der Konfiguration „DefaultJobManager“ inkonsistent. Dies kann vorkommen, wenn jemand die Konfiguration &quot;Apache Sling Job Event Handler&quot;über die OSGiconsole manuell ändert (z. B. die Eigenschaft &quot;Job Processing Enabled&quot;deaktivieren und erneut aktivieren und die Konfiguration speichern).

   * Dies führt dazu, dass der Status der unter „crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config“ gespeicherten Konfiguration für „DefaultJobManager“ inkonsistent wird. Obwohl die Eigenschaft &quot;Apache Sling Job Event Handler&quot;anzeigt, dass &quot;Job Processing Enabled&quot;aktiviert ist, wird beim Navigieren zur Registerkarte &quot;Sling Eventing&quot;die Meldung &quot;JOB PROCESSING IS DISABLED&quot;angezeigt und die Replikation funktioniert nicht.
   * Um dieses Problem zu beheben, navigieren Sie zur Konfigurationsseite der OSGi-Konsole und löschen Sie die Konfiguration &quot;Apache Sling Job Event Handler&quot;. Starten Sie dann den Master-Knoten des Clusters neu, um den Status der Konfiguration wieder konsistent zu machen. Dadurch sollte das Problem behoben werden, und die Replikation funktioniert wieder.

**Erstellen Sie eine replication.log**

Manchmal ist es hilfreich, die gesamte Replikationsprotokollierung so festzulegen, dass sie in einer separaten Protokolldatei auf DEBUG-Ebene hinzugefügt wird. Gehen Sie hierfür wie folgt vor:

1. Wechseln Sie zu https://host:port/system/console/configMgr und melden Sie sich als Admin an.
1. Suchen Sie nach der Apache Sling Logging Logger-Factory-Konfiguration und erstellen Sie eine Instanz, indem Sie auf die **+**-Schaltfläche rechts neben der Factory-Konfiguration klicken. Dadurch wird ein neuer Logging Logger erstellt.
1. Legen Sie die Konfiguration wie folgt fest:

   * Protokollierungsebene: DEBUG
   * Pfad der Protokolldatei: logs/replication.log
   * Kategorien: com.day.cq.replication

1. Wenn Sie vermuten, dass das Problem in irgendeiner Weise mit Sling-Ereignissen/Aufträgen in Zusammenhang steht, können Sie dieses Java™-Paket auch unter Kategorien hinzufügen: org.apache.sling.event

## Anhalten der Replikationsagenten-Warteschlange  {#pausing-replication-agent-queue}

In manchen Fällen ist es u. U. nützlich, die Replikations-Warteschlange anzuhalten, um die Last auf dem Autorensystem zu reduzieren, ohne dieses zu deaktivieren. Dies ist derzeit nur durch einen Hack der zeitweiligen Konfiguration eines ungültigen Ports möglich. Ab Version 5.4 können Sie die Pausenschaltfläche in der Warteschlange des Replikationsagenten sehen, da sie einige Einschränkungen aufweist.

1. Der Status wird nicht beibehalten. Wenn Sie einen Server neu starten oder ein Replikations-Bundle recycelt wird, wird der Status wieder ausgeführt.
1. Beim Anhalten für kurze Zeiträume tritt ein Leerlauf ein (OOB nach einer Stunde ohne Aktivitäten mit Replikation durch andere Threads), nicht jedoch für längere Zeiträume. Da es eine Funktion in Sling gibt, die inaktive Threads vermeidet. Überprüfen Sie also, ob ein Auftragswarteschlangen-Thread länger nicht verwendet wurde. Ist dies der Fall, werden Bereinigungszyklen gestartet. Aufgrund des Bereinigungszyklus wird der Thread gestoppt, sodass die angehaltene Einstellung verloren geht. Da Aufträge beibehalten werden, initiiert sie einen neuen Thread, um die Warteschlange zu verarbeiten, der keine Details zur angehaltenen Konfiguration enthält. Aufgrund dieser Warteschlange wird der Status &quot;Wird ausgeführt&quot;.

## Seitenberechtigungen werden bei der Benutzeraktivierung nicht repliziert {#page-permissions-are-not-replicated-on-user-activation}

Seitenberechtigungen werden nicht repliziert, da sie für die Knoten gespeichert werden, auf die Zugriff erteilt wird, und nicht für die Benutzer.

Im Allgemeinen sollten Seitenberechtigungen nicht vom Autor zur Veröffentlichung repliziert werden und sind nicht standardmäßig. Der Grund hierfür ist, das die Zugriffsrechte in diesen beiden Umgebungen unterschiedlich sein müssen. Daher empfiehlt Adobe, dass Sie ACLs auf der Veröffentlichungsinstanz separat von der Autoreninstanz konfigurieren.

## Replikations-Warteschlange blockiert bei der Replikation von Namespace-Informationen vom Autor zur Veröffentlichung {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Manchmal wird die Replikationswarteschlange blockiert, wenn versucht wird, Namespace-Informationen aus der Autoreninstanz in die Veröffentlichungsinstanz zu replizieren. Dies geschieht, weil der Replikationsbenutzer nicht die Berechtigung `jcr:namespaceManagement` hat. Um dieses Problem zu vermeiden, stellen Sie Folgendes sicher:

* Der Replikationsbenutzer (wie auf der Registerkarte [Transport](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) unter „Benutzer“ konfiguriert) existiert auch auf der Veröffentlichungsinstanz.
* Der Benutzer hat Lese- und Schreibrechte für den Pfad, in dem der Inhalt installiert ist.
* Der Benutzer hat die Berechtigung `jcr:namespaceManagement` auf Repository-Ebene. Sie können die Berechtigungen wie folgt erteilen:

1. Melden Sie sich bei CRX/DE ( `https://localhost:4502/crx/de/index.jsp`) als Administrator.
1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Auswählen **Repository**.
1. Klicks **Eintrag hinzufügen** (das Pluszeichen).
1. Geben Sie den Namen des Benutzers ein.
1. Wählen Sie in der Liste der Berechtigungen `jcr:namespaceManagement` aus.
1. Klicken Sie auf **OK**.
