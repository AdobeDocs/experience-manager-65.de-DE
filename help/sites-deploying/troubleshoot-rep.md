---
title: Fehlerbehebung bei Replikationsproblemen
description: Dieser Artikel stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
exl-id: cfa822c8-f9a9-4122-9eac-0293d525f6b5
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 809e9f22a5e8c937a24f2d038a17febdaebe8b5e
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 64%

---

# Fehlerbehebung bei Replikationsproblemen{#troubleshooting-replication}

Diese Seite stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.

## Problem {#problem}

Die Replikation (nicht die Rückwärtsreplikation) schlägt aus irgendeinem Grund fehl.

## Auflösung {#resolution}

Es gibt verschiedene Gründe, warum eine Replikation fehlschlägt. Dieser Artikel beschreibt die mögliche Vorgehensweise beim Analysieren der Probleme.

**Werden beim Klicken auf die Schaltfläche „Aktivieren“ irgendwelche Replikationen ausgelöst? Falls NICHT, gehen Sie wie folgt vor:**

1. Navigieren Sie zu `/crx/explorer` und melden Sie sich als `admin` an.
1. Öffnen Sie „Content Explorer“
1. Überprüfen, ob ein Knoten `/bin/replicate` oder `/bin/replicate.json` vorhanden ist. Falls er vorhanden ist, löschen Sie den Knoten und speichern Sie die Änderung.

**Werden die Replikationen in den Warteschlangen der Replikationsagenten gespeichert?**

Überprüfen Sie dies, indem Sie zu `/etc/replication/agents.author.html` wechseln und dann auf die zu überprüfenden Replikationsagenten klicken.

**Wenn eine oder einige Agentenwarteschlangen hängen geblieben sind:**

1. Lautet der Status der Warteschlange **gesperrt**? Wenn dies der Fall ist, wird die Veröffentlichungsinstanz nicht ausgeführt oder reagiert sie nicht? Überprüfen Sie die Veröffentlichungsinstanz, um zu sehen, wo der Fehler liegt. Überprüfen Sie also die Protokolle, ob ein OutOfMemory-Fehler oder ein anderes Problem vorliegt. Wenn die Instanz nur langsam ist, analysieren Sie die Thread-Sicherungskopien.
1. Lautet der Status der Warteschlange **Warteschlange ist aktiv – x ausstehend**? Der Replikationsauftrag könnte in einem Socket-Lesevorgang stecken bleiben und darauf warten, dass die Veröffentlichungsinstanz oder Dispatcher reagieren. Das bedeutet, dass u. U. eine hohe Last auf der Veröffentlichungsinstanz oder dem Dispatcher vorliegt oder dass diese durch eine Sperre unterbrochen wurden. Überprüfen Sie in diesem Fall die Thread-Sicherungskopien der Autoren- und Veröffentlichungsinstanzen.

   * Öffnen Sie die Thread-Sicherungskopien der Autoreninstanz in einem Analyzer für Thread-Sicherungskopien und prüfen Sie, ob der Sling-Eventing-Auftrag des Replikationsagenten durch einen SocketRead-Vorgang unterbrochen wurde.
   * Öffnen Sie die Thread-Dumps aus der Veröffentlichungsinstanz in einem Thread-Dump-Analyzer und analysieren Sie, was möglicherweise dazu führt, dass die Veröffentlichungsinstanz nicht reagiert. Es sollte ein Thread mit POST-`/bin/receive` im Namen angezeigt werden. Das ist der Thread, der die Replikation vom Autor erhält.

**Wenn alle Agentenwarteschlangen hängen geblieben sind:**

1. Möglicherweise kann ein bestimmter Teil des Inhalts aufgrund eines beschädigten Repositorys oder eines anderen Problems nicht unter /var/replication/data serialisiert werden. Überprüfen Sie die Datei „logs/error.log“ auf einen entsprechenden Fehler. Gehen Sie wie folgt vor, um das fehlerhafte Replikationselement zu entfernen:

   1. Navigieren Sie zu `https://<host>:<port>/crx/de` und melden Sie sich als Administrator an.
   1. Klicken Sie im oberen Menü auf „Tools“.
   1. Klicken Sie auf die Lupenschaltfläche.
   1. Wählen Sie „XPath“ als Typ aus.
   1. Geben Sie in das Feld „Abfrage“ diese Abfrage `/jcr:root/var/eventing/jobs//element(*,slingevent:Job) order by @slingevent:created`
   1. Klicken Sie auf „Suchen“.
   1. Die in den Ergebnissen ganz oben angezeigten Elemente sind die aktuellen Sling-Eventing-Aufträge. Klicken Sie auf die einzelnen Aufträge, um nach den unterbrochenen Replikationen zu suchen, die mit dem oben in der Warteschlange Angezeigten übereinstimmen.

1. Möglicherweise liegt ein Problem mit den Auftragswarteschlangen des Sling-Eventing-Frameworks vor. Starten Sie das `org.apache.sling.event`-Bundle in `/system/console` neu.
1. Möglicherweise ist die Auftragsverarbeitung deaktiviert. Dies kann in der Felix-Konsole auf der Registerkarte „Sling Eventing“ überprüft werden. Prüfen Sie, ob Folgendes angezeigt wird: „Apache Sling Eventing (JOB PROCESSING IS DISABLED!“)

   * Ist dies der Fall, überprüfen Sie auf der Registerkarte „Configuration“ der Felix-Konsole den Apache Sling Job Event Handler. Das Kontrollkästchen „Job Processing Enabled“ konnte deaktiviert werden. Wenn diese Option aktiviert ist und weiterhin „Auftragsverarbeitung ist deaktiviert“ angezeigt wird, überprüfen Sie, ob unter &quot;`/apps/system/config`&quot; eine Überlagerung vorhanden ist, durch die die Auftragsverarbeitung deaktiviert wird. Erstellen Sie einen `osgi:config` Knoten für `jobmanager.enabled` mit dem booleschen Wert `true` und überprüfen Sie erneut, ob die Aktivierung gestartet wurde und keine Aufträge mehr in der Warteschlange sind.

1. Möglicherweise ist auch der Status der Konfiguration „DefaultJobManager“ inkonsistent. Dies kann vorkommen, wenn jemand die Konfiguration „Apache Sling Job Event Handler“ manuell über die OSGi-Konsole ändert (deaktivieren Sie beispielsweise die Eigenschaft „Job Processing Enabled“ und aktivieren Sie sie erneut und speichern Sie die Konfiguration).

   * An dieser Stelle wechselt die unter gespeicherte Konfiguration „DefaultJobManager“ in einen inkonsistenten Status. `crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config` Obwohl die Eigenschaft „Apache Sling Job Event Handler“ anzeigt, dass „Job Processing Enabled“ (Jobverarbeitung aktiviert) aktiviert ist, wird auf der Registerkarte „Sling Eventing“ die Meldung „JOB PROCESSING IS DISABLED“ (Auftragsverarbeitung ist deaktiviert) angezeigt und die Replikation funktioniert nicht.
   * Navigieren Sie zur Konfigurationsseite der OSGi-Konsole und löschen Sie die Konfiguration „Apache Sling Job Event Handler“, um dieses Problem zu beheben. Starten Sie dann den Primärknoten des Clusters neu, um den Status der Konfiguration wieder konsistent zu machen. Dadurch sollte das Problem behoben werden, und die Replikation sollte wieder funktionieren.

**Erstellen einer „replication.log“-Datei**

Manchmal ist es hilfreich, auf DEBUG-Ebene festzulegen, dass die gesamte Replikationsprotokollierung in einer separaten Protokolldatei hinzugefügt wird. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zu `https://<host>:<port>/system/console/configMgr` und melden Sie sich als Administrator an.
1. Suchen Sie nach der Apache Sling Logging Logger-Factory-Konfiguration und erstellen Sie eine Instanz, indem Sie auf die **+**-Schaltfläche rechts neben der Factory-Konfiguration klicken. Dadurch wird eine neue Logging Logger-Konfiguration erstellt.
1. Richten Sie die Konfiguration wie folgt ein:

   * Protokollebene: `DEBUG`
   * Pfad der Protokolldatei: `logs/replication.log`
   * Kategorien: `com.day.cq.replication`

1. Wenn Sie den Verdacht haben, dass das Problem mit Sling Eventing/Jobs in Verbindung steht, können Sie unter `categories:org.apache.sling.event` auch dieses Java; -Paket hinzufügen.

## Anhalten der Warteschlange des Replikationsagenten  {#pausing-replication-agent-queue}

In manchen Fällen ist es u. U. nützlich, die Replikations-Warteschlange anzuhalten, um die Last auf dem Autorensystem zu reduzieren, ohne dieses zu deaktivieren. Dies ist derzeit nur durch das vorübergehende Konfigurieren eines ungültigen Ports möglich. Seit Version 5.4 gibt es eine Schaltfläche Pause in der Warteschlange des Replikationsagenten mit einigen Einschränkungen:

1. Der Status wird nicht beibehalten. Das heißt, wenn Sie einen Server neu starten oder ein Replikations-Bundle recycelt wird, kehrt es in den Status „Wird ausgeführt“ zurück.
1. Die Pause steht für einen kürzeren Zeitraum im Leerlauf (OOB 1 Stunde nach ausbleibenden Aktivitäten mit Replikation durch andere Threads). Dies liegt daran, dass es in Sling eine Funktion gibt, die inaktive Threads vermeidet. Überprüfen Sie, ob ein Auftragswarteschlangen-Thread lange Zeit nicht verwendet wurde. Wenn ja, werden Bereinigungszyklen gestartet. Aufgrund des Bereinigungszyklus wird der Thread gestoppt, sodass die Einstellung zum Anhalten verloren geht. Da Aufträge persistent sind, wird ein neuer Thread zur Verarbeitung der Warteschlange initiiert, der nicht die Details der angehaltenen Konfiguration aufweist. Aus diesem Grund wechselt die Warteschlange in den Status „Wird ausgeführt“.

## Seitenberechtigungen werden bei der Benutzeraktivierung nicht repliziert {#page-permissions-are-not-replicated-on-user-activation}

Seitenberechtigungen werden nicht repliziert, da sie für die Knoten gespeichert werden, auf die Zugriff erteilt wird, und nicht für die Benutzer.

Im Allgemeinen sollten Seitenberechtigungen nicht von der Autoreninstanz in die Veröffentlichungsinstanz repliziert werden und dies ist standardmäßig auch nicht der Fall. Der Grund hierfür ist, dass die Zugriffsrechte in diesen beiden Umgebungen unterschiedlich sein sollten. Daher empfiehlt Adobe, dass Sie ACLs in der Veröffentlichungsinstanz separat von der Autoreninstanz konfigurieren.

## Replikationswarteschlange wird bei der Replikation von Namespace-Informationen von der Autoren- in die Veröffentlichungsinstanz blockiert {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Manchmal wird die Replikationswarteschlange beim Versuch blockiert, Namespace-Informationen von der Autoreninstanz in die Veröffentlichungsinstanz zu replizieren. Dies geschieht, weil der Replikationsbenutzer nicht die Berechtigung `jcr:namespaceManagement` hat. Um dieses Problem zu vermeiden, stellen Sie Folgendes sicher:

* Der Replikationsbenutzer (wie auf der Registerkarte [Transport](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) unter „Benutzer“ konfiguriert) existiert auch auf der Veröffentlichungsinstanz.
* Der Benutzer hat Lese- und Schreibrechte für den Pfad, in dem der Inhalt installiert ist.
* Der Benutzer hat die Berechtigung `jcr:namespaceManagement` auf Repository-Ebene. Sie können die Berechtigungen wie folgt erteilen:

1. Melden Sie sich als Admin bei CRX/DE (`https://<host>:<port>/crx/de/index.jsp`) an.
1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Wählen Sie **Repository** aus.
1. Klicken Sie auf **Eintrag hinzufügen** (das Plussymbol).
1. Geben Sie den Namen der Benutzerin bzw. des Benutzers ein.
1. Wählen Sie in der Liste der Berechtigungen `jcr:namespaceManagement` aus.
1. Klicken Sie auf **OK**.
