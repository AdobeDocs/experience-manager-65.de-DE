---
title: Communities-Benutzersynchronisierung
description: Erfahren Sie, wie die Benutzersynchronisierung in Adobe Experience Manager Communities funktioniert.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: ecd30f5d-ad31-4482-96d3-c92f1cf91336
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2403'
ht-degree: 6%

---

# Communities-Benutzersynchronisierung {#communities-user-synchronization}

## Einführung {#introduction}

In Adobe Experience Manager (AEM) Communities können aus der Publish-Umgebung (je nach den konfigurierten Berechtigungen) *Site-*) *Mitglieder* werden, *Benutzergruppen* erstellen und ihr *Mitgliederprofil bearbeiten* .

*Benutzerdaten* beziehen sich auf **, *Benutzerprofile* und *Benutzergruppen*.

*Mitglieder* beziehen sich auf *Benutzer* die in der Publish-Umgebung registriert sind, im Gegensatz zu Benutzern, die in der Autorenumgebung registriert sind.

Weitere Informationen zu Benutzerdaten finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

## Synchronisieren von Benutzenden in einer Publish-Farm {#synchronizing-users-across-a-publish-farm}

Benutzerdaten, die in der Publish-Umgebung erstellt wurden, werden standardmäßig nicht in der Autorenumgebung angezeigt.

Die meisten in der Autorenumgebung erstellten Benutzerdaten sollen in der Autorenumgebung bleiben und werden nicht synchronisiert oder auf Publish-Instanzen repliziert.

Wenn die [Topologie](/help/communities/topologies.md) eine [Veröffentlichungsfarm) ](/help/sites-deploying/recommended-deploys.md#tarmk-farm), müssen Registrierung und Änderungen auf einer Publish-Instanz mit anderen Publish-Instanzen synchronisiert werden. Mitglieder müssen sich anmelden und ihre Daten auf jedem Publish-Knoten anzeigen können.

Wenn die Benutzersynchronisierung aktiviert ist, werden Benutzerdaten automatisch über alle Publish-Instanzen in der Farm hinweg synchronisiert.

### Anweisungen zur Benutzersynchronisierung {#user-sync-setup-instructions}

Detaillierte schrittweise Anweisungen zum Aktivieren der Synchronisierung in einer Veröffentlichungsfarm finden Sie unter [Benutzersynchronisierung](/help/sites-administering/sync.md).

## Benutzersynchronisierung im Hintergrund {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **vlt-Paket**

  Es handelt sich dabei um eine ZIP-Datei mit allen Änderungen, die an einem Publisher vorgenommen wurden, und die über Publisher verteilt werden muss. Änderungen an einem Herausgeber generieren Ereignisse, die vom Änderungsereignis-Listener ausgewählt werden. Dadurch wird ein vlt-Paket erstellt, das alle Änderungen enthält.

* **Verteilungspaket**

  Es enthält Verteilungsinformationen für Sling. Dabei handelt es sich um Informationen darüber, wo der Inhalt verteilt werden muss und wann er zuletzt verteilt wurde.

## Verfahren bei … {#what-happens-when}

### Publish-Site aus der Communities-Sites-Konsole {#publish-site-from-communities-sites-console}

Wenn eine Community-Site in der Autoreninstanz über die [Communities-Sites-Konsole](/help/communities/sites-console.md) veröffentlicht wird, führt dies dazu, dass [ die zugehörigen Seiten (repliziert) ](/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) und Sling die dynamisch erstellten Community-Benutzergruppen, einschließlich ihrer Mitgliedschaft, verteilt.

### Benutzer wird erstellt oder bearbeitet Profil in Publish {#user-is-created-or-edits-profile-on-publish}

Per Design werden in der Publish-Umgebung erstellte Benutzer und Profile (z. B. durch Selbstregistrierung, Social-Login, LDAP-Authentifizierung) nicht in der Authoring-Umgebung angezeigt.

Wenn es sich bei der Topologie um eine [Veröffentlichungsfarm](/help/communities/topologies.md) handelt und die Benutzersynchronisierung korrekt konfiguriert wurde, werden *Benutzende* und *Benutzerprofil* über die Veröffentlichungsfarm hinweg mittels Sling Distribution synchronisiert.

### Neue Community-Gruppe wird in Publish erstellt {#new-community-group-is-created-on-publish}

Die Erstellung einer Community-Gruppe, die zu neuen Site-Seiten und einer neuen Benutzergruppe führt, wird zwar von einer Publish-Instanz initiiert, findet aber tatsächlich in der Autoreninstanz statt.

Im Rahmen dieses Prozesses werden die neuen Site-Seiten auf allen Publish-Instanzen repliziert. Die dynamisch erstellte Community-Benutzergruppe und ihre Mitgliedschaft werden Sling-verteilt an alle Publish-Instanzen.

### Erstellung von Benutzenden oder Benutzergruppen über die Sicherheitskonsole {#users-or-user-groups-are-created-using-security-console}

Benutzerdaten, die in der Veröffentlichungsumgebung erstellt wurden, werden standardmäßig nicht in der Autorenumgebung angezeigt und umgekehrt.

Wenn die Konsole [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) verwendet wird, um neue Benutzer in der Veröffentlichungsumgebung hinzuzufügen, synchronisiert die Benutzersynchronisierung die neuen Benutzer und deren Gruppenmitgliedschaft bei Bedarf mit anderen Veröffentlichungsinstanzen. Bei der Benutzersynchronisierung werden auch die über die Sicherheitskonsole erstellten Benutzergruppen synchronisiert.

### Benutzer veröffentlicht Inhalte auf Publish {#user-posts-content-on-publish}

Bei benutzergenerierten Inhalten (User-Generated Content, UGC) erfolgt der Zugriff auf die in einer Veröffentlichungsinstanz eingegebenen Daten über das [konfigurierte SRP](/help/communities/srp-config.md).

## Best Practices {#bestpractices}

Standardmäßig ist die Benutzersynchronisierung **deaktiviert**. Die Aktivierung der Benutzersynchronisierung umfasst das Ändern *vorhandener* OSGi-Konfigurationen. Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Bei der Benutzersynchronisierung wird die Benutzerdatenverteilung von der Autorenumgebung verwaltet, auch wenn die Benutzerdaten nicht in der Autorenumgebung erstellt werden.

**Voraussetzungen**

1. Wenn Benutzer und Benutzergruppen bereits auf einem Herausgeber erstellt wurden, wird empfohlen, die Benutzerdaten vor der Konfiguration und Aktivierung der Benutzersynchronisierung [manuell zu synchronisieren](/help/sites-administering/sync.md#manually-syncing-users-and-user-groups).

   Nach der Aktivierung der Benutzersynchronisierung werden nur neu erstellte Benutzer und Gruppen synchronisiert .

1. Vergewissern Sie sich, dass der neueste Code installiert wurde:

   * [AEM-Plattform-Updates](https://helpx.adobe.com/de/experience-manager/kb/aem62-available-hotfixes.html)
   * [AEM Communities-Updates](/help/communities/deploy-communities.md#latestfeaturepack)

Die folgenden Konfigurationen sind erforderlich, um die Benutzersynchronisierung in AEM Communities zu aktivieren. Stellen Sie sicher, dass diese Konfigurationen korrekt sind, um zu verhindern, dass die Sling-Inhaltsverteilung fehlschlägt.

### Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

Diese Konfiguration ruft den Inhalt ab, der über die Herausgeber hinweg synchronisiert werden soll. Die Konfiguration befindet sich auf der Autoreninstanz. Der Autor muss alle Herausgeber verfolgen, die dort sind und wo alle Informationen synchronisiert werden sollen.

Die Standardwerte in der Konfiguration gelten für eine einzelne Veröffentlichungsinstanz. Da die Benutzersynchronisierung für die Synchronisierung mehrerer Veröffentlichungsinstanzen nützlich ist, z. B. für eine Veröffentlichungsfarm, müssen der Konfiguration zusätzliche Veröffentlichungsinstanzen hinzugefügt werden.

**Wie wird der Inhalt synchronisiert?**

Die Autoreninstanz pingt den Exporter-Endpunkt von Herausgebern an. Bei jeder Erstellung oder Aktualisierung von Inhalten für bestimmte Herausgeber (n) ruft der Autor den Inhalt von den Exporter-Endpunkten ab und [überträgt den Inhalt](/help/communities/sync.md#main-pars-image-1413756164) an andere Herausgeber (n-1, d. h. außerhalb der Herausgeber, von denen der Inhalt abgerufen wird).

So konfigurieren Sie die Konfiguration für Apache Sling Sync Agents:

1. Melden Sie sich mit Administratorrechten bei Ihrer AEM-Autoreninstanz an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf. Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Suchen Sie **Apache Sling Distribution Agent - Sync Agents Factory**.

   * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

     Name der Überprüfung: **socialpubsync.**

   * Aktivieren Sie das Kontrollkästchen **Aktiviert**.
   * Wählen Sie **Mehrere Warteschlangen verwenden.**
   * Geben Sie **Exporter-** und **Importer-Endpunkte** an (Sie können weitere Exporter- und Importer-Endpunkte hinzufügen).

     Diese Endpunkte definieren, woher Sie den Inhalt beziehen möchten und wohin Sie den Inhalt übertragen möchten. Der Autor ruft den Inhalt vom angegebenen Exporter-Endpunkt ab und überträgt den Inhalt an die Herausgeber (mit Ausnahme des Herausgebers, von dem der Inhalt abgerufen wurde).

   ![sync-agent-fact](assets/sync-agent-fact.png)

### Adobe Granite-Verteilung - Verschlüsselter Kennwortübertragungs-Geheimnis-Provider {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Dadurch kann der Autor den autorisierten Benutzer identifizieren, da er berechtigt ist, Benutzerdaten von der Autoren- zur Veröffentlichungsinstanz zu synchronisieren.

Der [autorisierte Benutzer erstellt](/help/sites-administering/sync.md#createauthuser) auf allen Veröffentlichungsinstanzen hilft Herausgebern, eine Verbindung mit der Autoreninstanz herzustellen und die Sling-Verteilung auf der Autoreninstanz zu konfigurieren. Dieser autorisierte Benutzer verfügt über alle erforderlichen [ACLs](/help/sites-administering/sync.md#howtoaddacl).

Wenn Daten auf Herausgebern installiert oder von diesen abgerufen werden sollen, stellt der Autor mithilfe der in dieser Konfiguration festgelegten Anmeldeinformationen (Benutzername und Kennwort) eine Verbindung zu den Herausgebern her.

So verbinden Sie Autoren- mit Herausgebern unter Verwendung autorisierter Benutzer:

1. Melden Sie sich mit Administratorrechten bei Ihrer AEM-Autoreninstanz an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Suchen Sie **Adobe Granite-Verteilung - Verschlüsseltes Passwort Transport Secret Provider.**
1. Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

   Verify-Eigenschaft **socialpubsync** - **publishUser.**

1. Legen Sie den Benutzernamen und das Kennwort für den [autorisierten Benutzer“ ](/help/sites-administering/sync.md#createauthorizeduser).

   Beispiel: **usersync - admin**

![granite-password-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent - Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

Diese Konfiguration wird verwendet, um die Daten zu konfigurieren, die Sie über Herausgeber hinweg synchronisieren möchten. Wenn Daten in Pfaden erstellt/aktualisiert werden, die in **Zulässige Stammordner** angegeben sind, wird „var/community/distribution/diff“ aktiviert und der erstellte Replikator ruft die Daten von einem Publisher ab und installiert sie auf anderen Publishern.

So konfigurieren Sie die zu synchronisierenden Daten (Knotenpfade):

1. Melden Sie sich mit Administratorrechten in Ihrer Veröffentlichungsinstanz an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Suchen Sie **Apache Sling Distribution Agent - Queue Agents Factory**.
1. Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

   Überprüfungsname: **socialPubSync -reverse**

1. Aktivieren Sie das **Aktiviert** und speichern Sie.
1. Geben Sie die Knotenpfade an, die in repliziert werden sollen **Zulässige Stammverzeichnisse**.
1. Wiederholen Sie den Vorgang für jede **Veröffentlichungs** Instanz.

   ![queue-agents-fact](assets/queue-agents-fact.png)

### Adobe Granite Distribution - Diff Observer Factory {#adobe-granite-distribution-diff-observer-factory}

Diese Konfiguration synchronisiert die Gruppenmitgliedschaft zwischen Herausgebern.
Wenn durch Ändern der Zugehörigkeit zu einer Gruppe in einem Herausgeber die Zugehörigkeit zu anderen Herausgebern nicht aktualisiert wird, stellen Sie sicher, dass **ref :members** zu „Looked **PropertiesNames“ hinzugefügt**.

So stellen Sie die Mitgliedersynchronisierung sicher:

1. Melden Sie sich mit Administratorrechten in Ihrer Veröffentlichungsinstanz an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Suchen Sie **Adobe Granite Distribution - Diff Observer Factory**.
1. Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

   Überprüfen Sie **Agentenname: socialpubsync -reverse**.

1. Aktivieren Sie das Kontrollkästchen **Aktiviert**.
1. Geben Sie **rep:members** als Beschreibung für propertyName in **Looked properties names** an und speichern Sie.

   ![diff-obs](assets/diff-obs.png)

### Apache Sling Distribution Trigger - Factory für geplante Trigger {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Mit dieser Konfiguration können Sie das Abrufintervall konfigurieren (nach dem Herausgeber gepingt und Änderungen von der Autoreninstanz abgerufen werden), um die Änderungen zwischen den Herausgebern zu synchronisieren.

Der Autor fragt Publisher alle 30 Sekunden ab (Standard). Wenn Pakete im Ordner `/var/sling/distribution/packages/  socialpubsync -  vlt /shared` vorhanden sind, ruft er diese Pakete ab und installiert sie auf anderen Herausgebern.

So ändern Sie das Abrufintervall:

1. Melden Sie sich mit Administratorrechten bei Ihrer AEM-Autoreninstanz an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf, z. B. [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Suchen Sie **Apache Sling Distribution Trigger - Scheduled Trigger Factory**

   * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

     Überprüfen Sie **socialPubSync -scheduled-Trigger**

   * Stellen Sie das Intervall in Sekunden auf das gewünschte Intervall ein und speichern Sie.

   ![scheduled-Trigger ](assets/scheduled-trigger.png)

### AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

Bei Problemen in der Sling-Verteilung, bei denen es eine Diskrepanz bei Abonnements und Folgendem gibt, überprüfen Sie, ob die folgenden Eigenschaften in den Konfigurationen **AEM Communities User Sync Listener** festgelegt sind:

* Knotentypen
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

So synchronisieren Sie Abonnements, Folts und Benachrichtigungen

In jeder AEM-Veröffentlichungsinstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf. Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Suchen Sie **AEM Communities User Sync Listener**.
1. Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

   Überprüfungsname: **socialPubSync -scheduled-Trigger**

1. Legen Sie die folgenden **NodeTypes** fest:

   `rep:User`

   `nt:unstructured`

   `nt:resource`

   `rep:ACL`

   `sling:Folder`

   `sling:OrderedFolder`

   Die in dieser Eigenschaft angegebenen Knotentypen werden synchronisiert, und die Benachrichtigungsinformationen (Blogs und Konfigurationen werden gefolgt) werden zwischen verschiedenen Herausgebern synchronisiert.

1. Fügen Sie alle Ordner hinzu, die in &quot;**&quot; synchronisiert** sollen. Zum Beispiel:

   `segments/scoring`

   `social/relationships`

   `activities`

1. Legen Sie die **ignorableNodes** auf fest:

   `.tokens`

   `system`

   `rep:cache` (Da Sticky-Sitzungen verwendet werden, müssen Sie diesen Knoten nicht mit verschiedenen Herausgebern synchronisieren).

   ![user-sync-listener](assets/user-sync-listner.png)

### Unique Sling ID {#unique-sling-id}

Die AEM-Autoreninstanz verwendet eine Sling-ID, um zu ermitteln, von wo die Daten kommen und an welche Publisher sie das Paket zurücksenden müssen (oder nicht).

Stellen Sie sicher, dass alle Herausgeber in einer Veröffentlichungsfarm über eine eindeutige Sling-ID verfügen. Wenn die Sling-ID für mehrere Veröffentlichungsinstanzen in einer Veröffentlichungsfarm identisch ist, schlägt die Benutzersynchronisierung fehl. Da der Autor nicht weiß, woher er das Paket abrufen soll und wo es installiert werden soll.

Um eine eindeutige Sling-ID von Herausgebern in der Veröffentlichungsfarm sicherzustellen, verwenden Sie in jeder Publish-Instanz:

1. Navigieren Sie zu [https://_host:port_/system/console/status-slingsettings](https://localhost:4503/system/console/status-slingsettings).
1. Überprüfen Sie den Wert von **Sling ID**.

   ![slingid](assets/slingid.png)

   Wenn die Sling-ID einer Veröffentlichungsinstanz der Sling-ID einer anderen Veröffentlichungsinstanz entspricht, gehen Sie wie folgt vor:

1. Beenden Sie eine der Publish-Instanzen, die über eine entsprechende Sling-ID verfügen.
1. Suchen Sie im Verzeichnis `crx-quickstart/launchpad/felix` nach der Datei *sling.id.file und löschen Sie sie*

   Beispiel für ein Linux-System:

   `rm -i $(find . -type f -name sling.id.file)`

   Beispielsweise auf einem Windows-System:

   Windows-Explorer verwenden und nach `sling.id.file` suchen

1. Publish-Instanz starten. Beim Start wird ihr eine neue Sling-ID zugewiesen.
1. Überprüfen Sie, ob **Sling-ID** jetzt eindeutig ist.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

### Vault Package Builder Factory {#vault-package-builder-factory}

Damit Aktualisierungen ordnungsgemäß synchronisiert werden können, muss der Vault-Paket-Builder für die Benutzersynchronisierung geändert werden.
In `/home/users` wird ein `*/rep:cache` Knoten erstellt. Es ist ein Cache, der verwendet wird, um zu ermitteln, dass dieser Cache direkt verwendet werden kann, wenn wir den Prinzipalnamen eines Knotens abfragen.

Die Benutzersynchronisierung kann angehalten werden, wenn `rep :cache` Knoten über Herausgeber hinweg synchronisiert werden.

Um sicherzustellen, dass Aktualisierungen auf jeder AEM Publish-Instanz ordnungsgemäß zwischen Publishern synchronisiert werden, gehen Sie folgendermaßen vor:

1. Zugreifen auf die [Web-Konsole](/help/sites-deploying/configuring-osgi.md)

   Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Suchen Sie die **Apache Sling Distribution Packaging - Vault Package Builder Factory**

   Builder-Name: socialpubsync-vlt.

1. Wählen Sie das Bearbeitungssymbol aus.
1. Fügen Sie zwei Paket-Knotenfilter hinzu:
   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`
1. Umgang mit Richtlinien
   * Um vorhandene rep :policy-Knoten mit neuen zu überschreiben, fügen Sie einen dritten Paketfilter hinzu: `/home/users|+.*/rep:policy`
   * Um zu verhindern, dass Richtlinien verteilt werden, legen Sie Folgendes fest: `Acl Handling: IGNORE`

   ![Vault Package Builder Factory](assets/vault-package-builder-factory.png)

## Fehlerbehebung bei der Sling-Verteilung in AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Wenn die Sling-Verteilung fehlschlägt, führen Sie die folgenden Debugging-Schritte aus:

1. **Prüfen auf [nicht ordnungsgemäß hinzugefügte Konfigurationen](/help/sites-administering/sync.md#improperconfig)**

   Stellen Sie sicher, dass nicht mehrere Konfigurationen hinzugefügt oder bearbeitet werden. Stattdessen sollten die vorhandenen Standardkonfigurationen bearbeitet werden.
1. **Überprüfen Sie die Konfigurationen**

   Stellen Sie sicher[ dass alle ](/help/communities/sync.md#bestpractices)Konfigurationen“ in Ihrer AEM-Autoreninstanz korrekt festgelegt sind, wie in den Best [ beschrieben](/help/communities/sync.md#main-pars-header-863110628).

1. **Überprüfen Sie die Berechtigungen autorisierter Benutzer**

   Wenn die Pakete nicht ordnungsgemäß installiert sind, überprüfen Sie, ob der [autorisierte Benutzer](/help/sites-administering/sync.md#createauthuser) der in der ersten Publish-Instanz erstellt wurde, die richtigen ACLs hat.

   Um dies zu validieren, ändern Sie anstelle des [erstellten autorisierten ](/help/sites-administering/sync.md#createauthuser) die Konfiguration [Adobe Granite Distribution - Encrypted Password Transport Secret Provider](/help/sites-administering/sync.md#adobegraniteencpasswrd) auf der Autoreninstanz so, dass Admin-Benutzeranmeldeinformationen verwendet werden. Versuchen Sie nun erneut, die Pakete zu installieren. Wenn die Benutzersynchronisierung mit Administratorberechtigungen problemlos funktioniert, bedeutet dies, dass der erstellte Veröffentlichungsbenutzer keine geeigneten ACLs hatte.

1. **Überprüfen Sie die Konfiguration der Diff Observer Factory**

   Wenn nur bestimmte Knoten nicht über die Veröffentlichungsfarm hinweg synchronisiert werden - z. B. wenn Gruppenmitglieder nicht synchronisiert werden - stellen Sie sicher, dass die Konfiguration [Adobe Granite Distribution - Diff Observer Factory](/help/sites-administering/sync.md#diffobserver) aktiviert ist und **rep: members** in den **Eigenschaftsnamen** festgelegt ist.

1. **Überprüfen Sie die Konfiguration des AEM Communities User Sync Listener.** Wenn die erstellten Benutzenden synchronisiert werden, Abonnements und Folgendes jedoch nicht funktionieren, stellen Sie sicher, dass die Konfiguration des AEM Communities-Benutzersynchronisierungs-Listeners Folgendes aufweist:

   * Knotentypen: festgelegt auf **rep:User, nt:**, **nt:resource**, **rep:ACL**, **sling:Folder** und **sling:OrderedFolder**.
   * Ignorable nodes- set to **.tokens**, **system**, and **rep :cache**.
   * Verteilte Ordner - Legen Sie die Ordner fest, die verteilt werden sollen.

1. **Überprüfen Sie die bei der Benutzererstellung in der Publish-Instanz generierten Protokolle**

   Wenn die oben genannten Konfigurationen richtig eingestellt sind und die Benutzersynchronisierung noch nicht funktioniert, überprüfen Sie die Protokolle, die bei der Benutzererstellung generiert wurden.

   Überprüfen Sie wie folgt, ob die Reihenfolge der Protokolle identisch ist:

   ```shell
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ2: ADD paths=[/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK], user=communities-user-admin
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ3: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy], user=communities-user-admin
   15.05.2016 18:33:01.757 *INFO* [sling-oak-observation-7431] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_ebb27ad9-a861-4405-9342-d64c916654e2:0.0.1
   15.05.2016 18:33:01.820 *INFO* [sling-oak-observation-7422] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_58811273-5861-48fe-95d2-4aff367b99c3:0.0.1
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK/profile]
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ4: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK/profile], user=communities-user-admin
   15.05.2016 18:33:02.273 *INFO* [sling-oak-observation-7430] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337182039_f34f4fa6-10b9-42eb-8740-4da9d4d38f99:0.0.1
   ```

Zu debuggen:

1. Deaktivieren Sie die Benutzersynchronisierung:
1. Melden Sie sich in der AEM-Autoreninstanz mit Administratorrechten an.

   1. Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf. Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Distribution Agent - Sync Agents Factory**.
   1. Deaktivieren Sie **Kontrollkästchen** Aktiviert“.

      Beim Deaktivieren der Benutzersynchronisierung werden die Endpunkte der Autoreninstanz (Exporter und Importer) deaktiviert und die Autoreninstanz ist statisch. Die **vlt**-Pakete werden vom Autor nicht gepingt oder abgerufen.

      Wenn jetzt ein Benutzer in der Veröffentlichungsinstanz erstellt wird, wird das **vlt**-Paket im Knoten */var/sling/distribution/packages/ socialpubsync - vlt /data* erstellt. Und wenn diese Pakete vom Autor an einen anderen Service gesendet werden. Sie können diese Daten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Services gepusht werden.

1. Wechseln Sie zu einem Herausgeber und erstellen Sie einen Benutzer im Herausgeber. Daher werden Ereignisse erstellt.
1. Überprüfen Sie die [Reihenfolge der Protokolle](/help/communities/sync.md#troubleshoot-sling-distribution-in-aem-communities) die bei der Benutzererstellung erstellt wurden.
1. Überprüfen Sie, ob ein **vlt**-Paket unter **/var/sling/distribution/packages/socialpubsync-vlt/data** erstellt wurde.
1. Aktivieren Sie nun die Benutzersynchronisierung auf der AEM-Autoreninstanz.
1. Ändern Sie auf dem Herausgeber die Exporter- oder Importer-Endpunkte in **Apache Sling Distribution Agent - Sync Agents Factory**.
Wir können Paketdaten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Herausgeber gepusht werden und welche Daten verloren gehen.
