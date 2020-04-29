---
title: Communities-Benutzersynchronisierung
seo-title: Communities-Benutzersynchronisierung
description: Funktionsweise der Benutzersynchronisierung
seo-description: Funktionsweise der Benutzersynchronisierung
uuid: 772b82bd-a66c-4c1d-b80b-dcff77c873a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 97286c2c-f6e3-43ec-b1a9-2abb58616778
docset: aem65
translation-type: tm+mt
source-git-commit: acc758b83486e8c623e31bb4a68f3c29dd4848ba

---


# Communities-Benutzersynchronisierung {#communities-user-synchronization}

## Einführung {#introduction}

In AEM Communities können *Site-Besucher* aus der Umgebung &quot;Veröffentlichen&quot;(abhängig von den konfigurierten Berechtigungen) *Mitglieder* werden, *Benutzergruppen* erstellen und ihr *Member-Profil* bearbeiten.

*&quot;Benutzerdaten* &quot;bezeichnet *Benutzer*, *Profil* und *Benutzergruppen*.

*Mitglieder* beziehen sich auf *Benutzer* , die in der Veröffentlichungs-Umgebung registriert sind, im Gegensatz zu in der Autorenversion registrierten Benutzern.

Weitere Informationen zu Benutzerdaten finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

## Synchronisieren von Benutzern auf einer Veröffentlichungsfarm {#synchronizing-users-across-a-publish-farm}

Standardmäßig werden in der Umgebung &quot;Veröffentlichen&quot;erstellte Benutzerdaten nicht in der Umgebung &quot;Autor&quot;angezeigt.

Die meisten in der Authoring-Umgebung erstellten Benutzerdaten bleiben in der Autoreninstanz und werden nicht synchronisiert oder auf Veröffentlichungsinstanzen repliziert.

Wenn es sich bei der [Topologie](/help/communities/topologies.md) um eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm)handelt, müssen die Registrierungen und Änderungen, die an einer Veröffentlichungsinstanz vorgenommen wurden, mit anderen Instanzen im Veröffentlichungsmodus synchronisiert werden. Mitglieder müssen sich anmelden und ihre Daten auf jedem Veröffentlichungsknoten anzeigen können.

Wenn die Benutzersynchronisierung aktiviert ist, werden die Benutzerdaten automatisch über die Instanzen im Veröffentlichungsmodus in der Farm hinweg synchronisiert.

### Anweisungen zur Benutzersynchronisierung {#user-sync-setup-instructions}

Detaillierte Anweisungen zum Aktivieren der Synchronisierung über eine Veröffentlichungsfarm hinweg finden Sie unter:

* [Benutzersynchronisierung](/help/sites-administering/sync.md)

## Benutzersynchronisierung im Hintergrund {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **vlt-Paket**

   Es handelt sich um eine ZIP-Datei mit allen Änderungen, die an einem Herausgeber vorgenommen wurden und die über Herausgeber verteilt werden müssen. Änderungen an einem Herausgeber generieren Ereignis, die vom Ereignis-Listener change ausgewählt werden. Dadurch wird ein vlt-Paket erstellt, das alle Änderungen enthält.

* **Distributions-Paket**

   Es enthält Verteilungsinformationen für Sling. Das sind Informationen darüber, wo der Inhalt verteilt werden muss und wann er zuletzt verteilt wurde.

## What Happens When ... {#what-happens-when}

### Veröffentlichen von Sites in der Sites-Konsole der Communities {#publish-site-from-communities-sites-console}

Wenn beim Autor eine Community-Site über die [Communities Sites Console](/help/communities/sites-console.md)veröffentlicht wird, werden die verknüpften Seiten [repliziert](/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) , und Sling verteilt die dynamisch erstellten Community-Benutzergruppen, einschließlich ihrer Mitgliedschaft.

### Benutzer wird beim Veröffentlichen erstellt oder bearbeitet Profil {#user-is-created-or-edits-profile-on-publish}

Standardmäßig werden in der Umgebung &quot;Veröffentlichen&quot;erstellte Benutzer und Profil (z. B. durch Selbstregistrierung, Social-Login oder LDAP-Authentifizierung) nicht in der Umgebung &quot;Autor&quot;angezeigt.

When the topology is a [publish farm](/help/communities/topologies.md) and user sync has been correctly configured, the *user* and *user profile* is synchronized across the publish farm using Sling distribution.

### Neue Community-Gruppe wird bei der Veröffentlichung erstellt {#new-community-group-is-created-on-publish}

Obwohl sie von einer Instanz im Veröffentlichungsmodus initiiert wird, erfolgt die Erstellung einer Community-Gruppe, die zu neuen Site-Seiten und einer neuen Benutzergruppe führt, tatsächlich in der Autoreninstanz.

Während des Prozesses werden die neuen Siteseiten in alle Veröffentlichungsinstanzen repliziert. Die dynamisch erstellte Community-Benutzergruppe und ihre Mitgliedschaft werden an alle Veröffentlichungsinstanzen verteilt.

### Erstellung von Benutzern oder Benutzergruppen über die Sicherheitskonsole {#users-or-user-groups-are-created-using-security-console}

Per Design werden die in der Veröffentlichungsumgebung erstellten Benutzerdaten nicht in der Autorenumgebung angezeigt (und umgekehrt).

Wenn in der Veröffentlichungsumgebung neue Benutzer über die Konsole [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) hinzugefügt werden, werden die neuen Benutzer und ihre Gruppenmitgliedschaft im Rahmen der Benutzersynchronisierung ggf. mit anderen Veröffentlichungsinstanzen synchronisiert. Bei der Benutzersynchronisierung werden auch die über die Sicherheitskonsole erstellten Benutzergruppen synchronisiert.

### Inhalt von Benutzerbeiträgen bei der Veröffentlichung {#user-posts-content-on-publish}

Bei benutzergenerierten Inhalten (UGC) wird auf die in einer Veröffentlichungsinstanz eingegebenen Daten über das [konfigurierte SRP](/help/communities/srp-config.md)zugegriffen.

## Best Practices {#bestpractices}

Standardmäßig ist die Benutzersynchronisierung **deaktiviert**. Die Aktivierung der Benutzersynchronisierung beinhaltet die Änderung *vorhandener* OSGi-Konfigurationen. Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Die Benutzersynchronisierung ist davon abhängig, dass die Autorenumgebung die Verteilung der Benutzerdaten verwaltet, auch wenn die Benutzerdaten nicht in der Autoreninstanz erstellt werden .

**Voraussetzungen**

1. Wenn Benutzer und Benutzergruppen bereits auf einem Herausgeber erstellt wurden, wird empfohlen, die Benutzerdaten vor der Konfiguration und Aktivierung der Benutzersynchronisierung [manuell zu synchronisieren](/help/sites-administering/sync.md#manually-syncing-users-and-user-groups).

   Sobald die Benutzersynchronisierung aktiviert wurde, werden nur neu erstellte Benutzer und Gruppen synchronisiert .

1. Stellen Sie sicher, dass der neueste Code installiert wurde:

   * [AEM-Plattformupdates](https://helpx.adobe.com/de/experience-manager/kb/aem62-available-hotfixes.html)
   * [AEM Communities-Updates](/help/communities/deploy-communities.md#latestfeaturepack)

Die folgenden Konfigurationen sind erforderlich, um die Benutzersynchronisierung in AEM Communities zu aktivieren. Stellen Sie sicher, dass diese Konfigurationen korrekt sind, damit die Verteilung von Sling-Inhalten nicht fehlschlägt.

### Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

Diese Konfiguration ruft die Inhalte ab, die über die Herausgeber hinweg synchronisiert werden sollen. Die Konfiguration befindet sich in der Autoreninstanz. Der Autor muss alle Herausgeber, die vorhanden sind, verfolgen und alle Informationen synchronisieren.

Die Standardwerte in der Konfiguration beziehen sich auf eine einzelne Instanz im Veröffentlichungsmodus. Da die Benutzersynchronisierung zum Synchronisieren mehrerer Instanzen im Veröffentlichungsmodus nützlich ist, z. B. für eine Veröffentlichungsfarm, müssen der Konfiguration zusätzliche Instanzen im Veröffentlichungsmodus hinzugefügt werden.

**Wie werden die Inhalte synchronisiert?**

Die Autoreninstanz fügt den Endpunkt des Exporteurs von Herausgebern ein. Wenn ein Benutzer auf bestimmten Herausgebern (n) erstellt oder aktualisiert wird, ruft der Autor den Inhalt von seinen Exporteuren-Endpunkten ab und [sendet den Inhalt](/help/communities/sync.md#main-pars-image-1413756164) an andere Herausgeber (n-1, d. h. nicht an die Herausgeber, von denen der Inhalt abgerufen wird).

Konfigurieren der Konfiguration von Apache Sling Sync Agents:

1. Melden Sie sich mit Administratorrechten für Ihre AEM-Autoreninstanz an.
1. Access the [Web Console](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html). For example, [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Locate **Apache Sling Distribution Agent - Sync Agents Factory**.

   * Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

      Überprüfungsname: **socialpubsync.**

   * Select the **Enabled** checkbox.
   * Wählen Sie &quot;Mehrere Warteschlangen **verwenden&quot;.**
   * Geben Sie **Exporter-Endpunkte** und **Importer-Endpunkte** an (Sie können weitere Exporteur- und Importer-Endpunkte hinzufügen).

      Diese Endpunkte definieren, woher der Inhalt abgerufen werden soll und wohin der Inhalt verschoben werden soll. Der Autor ruft den Inhalt vom angegebenen Exporteur-Endpunkt ab und gibt den Inhalt an die Herausgeber weiter (mit Ausnahme des Herausgebers, von dem er den Inhalt abgerufen hat).
   ![sync-agent-fact](assets/sync-agent-fact.png)

### Adobe Granite Distribution – Encrypted Password Transport Secret Provider {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Dadurch kann der Autor den autorisierten Benutzer identifizieren, da er berechtigt ist, Benutzerdaten vom Autor zur Veröffentlichung zu synchronisieren.

Der [autorisierte Benutzer, der auf allen Instanzen im Veröffentlichungsmodus erstellt wurde](/help/sites-administering/sync.md#createauthuser) , hilft Herausgebern, eine Verbindung mit dem Autor herzustellen und die Sling-Distribution für den Autor zu konfigurieren. Dieser autorisierte Benutzer verfügt über alle erforderlichen [ACLs](/help/sites-administering/sync.md#howtoaddacl).

Wenn Daten auf Herausgebern installiert oder von diesen abgerufen werden sollen, stellt der Autor eine Verbindung mit den Herausgebern her, wobei die in dieser Konfiguration festgelegten Anmeldeinformationen (Benutzername und Kennwort) verwendet werden.

So verbinden Sie Autoren mit Herausgebern mit autorisierten Benutzern:

1. Melden Sie sich mit Administratorrechten für Ihre AEM-Autoreninstanz an.
1. Access the [Web Console](/help/sites-deploying/configuring-osgi.md).

   For example, [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Locate **Adobe Granite Distribution - Encrypted Password Transport Secret Provider.**
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Eigenschaft **socialpubsync** überprüfen - **publishUser.**

1. Legen Sie den Benutzernamen und das Kennwort auf den [autorisierten Benutzer](/help/sites-administering/sync.md#createauthorizeduser)fest.

   Beispiel: **usersync - admin**

![granite-paswrd-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent – Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

Diese Konfiguration wird verwendet, um die Daten zu konfigurieren, die Sie über Herausgeber hinweg synchronisieren möchten. Wenn Daten in Pfaden erstellt/aktualisiert werden, die in **Zulässige Stammordner** angegeben sind, wird &quot;var/community/distribution/diff&quot;aktiviert und der erstellte Replikator ruft die Daten von einem Herausgeber ab und installiert sie auf anderen Herausgebern.

So konfigurieren Sie die zu synchronisierenden Daten (Knotenpfade):

1. Melden Sie sich mit Administratorrechten für Ihre Autoreninstanz an.
1. Access the [Web Console](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html).

   For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Locate **Apache Sling Distribution Agent - Queue Agents Factory**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Überprüfungsname: **socialpubsync -reverse**

1. Aktivieren Sie das Kontrollkästchen &quot; **Aktiviert** &quot;und speichern Sie.
1. Geben Sie die Knotenpfade an, die in **Zulässigen Wurzeln** repliziert werden sollen.
1. Repeat for each **publish** instance.

   ![queue-agents-fact](assets/queue-agents-fact.png)

### Adobe Granite Distribution – Diff Observer Factory {#adobe-granite-distribution-diff-observer-factory}

Bei dieser Konfiguration wird die Gruppenmitgliedschaft über Herausgeber hinweg synchronisiert.
Wenn eine Änderung der Mitgliedschaft in einer Gruppe in einem Herausgeber die Mitgliedschaft nicht in anderen Herausgebern aktualisiert, stellen Sie sicher, dass **ref :members** den **Namen** der angezeigten Eigenschaften hinzugefügt wird.

So stellen Sie die Mitgliedersynchronisierung sicher:

1. Melden Sie sich mit Administratorrechten für Ihre AEM-Autoreninstanz an.
1. Access the [Web Console](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html).

   For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Locate **Adobe Granite Distribution - Diff Observer Factory**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Name des **Agenten überprüfen: socialpubsync -reverse**.

1. Select the **Enabled** checkbox.
1. Geben Sie **rep:members** als Beschreibung für propertyName in den Namen **der** gesuchten Eigenschaften an und speichern Sie.

   ![diff-obs](assets/diff-obs.png)

### Apache Sling Distribution Trigger – Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Mit dieser Konfiguration können Sie das Abfrageintervall konfigurieren (nach dem Herausgeber gepingt und Änderungen vom Autor gezogen werden), um die Änderungen zwischen Herausgebern zu synchronisieren.

Der Autor fragt Herausgeber alle 30 Sekunden ab (Standard). Wenn Pakete im Ordner vorhanden sind `/var/sling/distribution/packages/  socialpubsync -  vlt /shared`, werden diese Pakete abgerufen und auf anderen Herausgebern installiert.

So ändern Sie den Abfrageintervall:

1. Melden Sie sich mit Administratorrechten für Ihre AEM-Autoreninstanz an.
1. Auf die [Webkonsole](/help/sites-deploying/configuring-osgi.md)zugreifen, z. B. [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Locate **Apache Sling Distribution Trigger - Scheduled Triggers Factory**

   * Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

      Verify **socialpubsync -geplante-auslöser**

   * Legen Sie das Intervall in Sekunden auf das gewünschte Intervall fest und speichern Sie es.
   ![scheduled-trigger](assets/scheduled-trigger.png)

### AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

Überprüfen Sie bei Problemen in der Sling-Distribution, bei denen es zu einer Diskrepanz bei Abonnements kommt und darauf folgt, ob die folgenden Eigenschaften in **AEM Communities User Sync Listener** -Konfigurationen festgelegt sind:

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

So synchronisieren Sie Abonnements, Follower und Benachrichtigungen

Auf jeder AEM-Veröffentlichungsinstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Access the [Web Console](/help/sites-deploying/configuring-osgi.md). For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Locate **AEM Communities User Sync Listener**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol)

   Überprüfungsname: **socialpubsync -geplante-auslöser**

1. Legen Sie die folgenden **NodeTypes** fest:

   `rep:User`

   `nt:unstructured`

   `nt:resource`

   `rep:ACL`

   `sling:Folder`

   `sling:OrderedFolder`

   Die in dieser Eigenschaft angegebenen Node-Typen werden synchronisiert und die Benachrichtigungsinformationen (Blogs und Konfigurationen folgen) werden zwischen verschiedenen Herausgebern synchronisiert.

1. Hinzufügen alle Ordner, die in **DistributedFolders** synchronisiert werden sollen. Beispiel:

   `segments/scoring`

   `social/relationships`

   `activities`

1. Legen Sie die **ignorierten** Nodes wie folgt fest:

   `.tokens`

   `system`

   `rep:cache` (Da wir persistente Sitzungen verwenden, müssen wir diesen Knoten nicht mit anderen Herausgebern synchronisieren.)

   ![user-sync-listner](assets/user-sync-listner.png)

### Eindeutige Sling-ID {#unique-sling-id}

Die AEM-Autoreninstanz verwendet Sling-ID, um zu ermitteln, woher die Daten kommen und an welche Herausgeber das Paket zurückgesendet werden muss (oder muss).

Vergewissern Sie sich, dass alle Herausgeber in einer Veröffentlichungsfarm über eine eindeutige Sling-ID verfügen. Wenn die Sling-ID für mehrere Instanzen im Veröffentlichungsmodus identisch ist, schlägt die Benutzersynchronisierung fehl. Da der Autor nicht wissen, wo das Paket abgeholt und wo das Paket installiert werden soll.

So stellen Sie für jede Instanz im Veröffentlichungsmodus eine eindeutige Sling-ID für Herausgeber sicher:

1. Browse to [https://_host:port_/system/console/status-slingsettings](https://localhost:4503/system/console/status-slingsettings).
1. Check the value of **Sling ID**.

   ![slingid](assets/slingid.png)

   Wenn die Sling-ID einer Veröffentlichungsinstanz der Sling-ID einer anderen Veröffentlichungsinstanz entspricht, gehen Sie wie folgt vor:

1. Beenden Sie eine der Instanzen im Veröffentlichungsmodus, die über eine entsprechende Sling-ID verfügen.
1. Suchen Sie im `crx-quickstart/launchpad/felix` Verzeichnis nach der Datei &quot; *sling.id.file&quot;und löschen Sie sie.*

   Beispiel:

   `rm -i $(find . -type f -name sling.id.file)`

   Beispiel Windows:

   Windows Explorer verwenden und nach `sling.id.file`

1. Starten Sie die Veröffentlichungsinstanz. Beim Start wird ihm eine neue Sling-ID zugewiesen.
1. Validate that the **Sling ID** is now unique.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

### Vault Package Builder Factory {#vault-package-builder-factory}

Damit Updates ordnungsgemäß synchronisiert werden, müssen Sie den Vault Package Builder für die Benutzersynchronisierung ändern.
In `/home/users`wird ein `*/rep:cache` Knoten erstellt. Es ist ein Cache, der verwendet wird, um zu finden, dass, wenn wir Abfrage auf den Hauptnamen eines Knotens, dann dieser Cache direkt verwendet werden kann.

Die Benutzersynchronisierung kann beendet werden, wenn `rep :cache` Knoten über Herausgeber hinweg synchronisiert werden.

Um sicherzustellen, dass Updates ordnungsgemäß über Herausgeber hinweg synchronisiert werden, führen Sie für jede AEM-Veröffentlichungsinstanz folgende Schritte durch:

1. Access the [Web Console](/help/sites-deploying/configuring-osgi.md)

   For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Locate the **Apache Sling Distribution Packaging - Vault Package Builder Factory**

   Builder name: socialpubsync-vlt.

1. Wählen Sie das Bearbeitungssymbol aus.
1. Hinzufügen zwei Filter des Paketknotens:
   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`
1. Richtlinienverwaltung
   * To overwrite existing rep :policy nodes with new ones, add a third Package Filter: `/home/users|+.*/rep:policy`
   * To prevent policies from being distributed, set: `Acl Handling: IGNORE`
   ![Vault-Paketerstellung](assets/vault-package-builder-factory.png)

## Fehlerbehebung bei der Sling-Distribution in AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Wenn die Sling-Verteilung fehlschlägt, führen Sie die folgenden Debugging-Schritte aus:

1. **Auf[falsch hinzugefügte Konfigurationen prüfen](/help/sites-administering/sync.md#improperconfig)**

   Vergewissern Sie sich, dass nicht mehrere Konfigurationen hinzugefügt oder bearbeitet werden. Stattdessen sollten die vorhandenen Standardkonfigurationen bearbeitet werden.
1. **Konfigurationen prüfen**

   Vergewissern Sie sich, dass alle [Konfigurationen](/help/communities/sync.md#bestpractices) in Ihrer AEM-Autoreninstanz entsprechend eingestellt sind, wie in den [Best Practices](/help/communities/sync.md#main-pars-header-863110628)beschrieben.

1. **Berechtigungen autorisierter Benutzer überprüfen**

   Wenn die Pakete nicht ordnungsgemäß installiert sind, überprüfen Sie, ob der in der ersten Instanz im Veröffentlichungsmodus erstellte [autorisierte Benutzer](/help/sites-administering/sync.md#createauthuser) über die richtigen Zugriffssteuerungslisten verfügt.

   Um dies zu validieren, ändern Sie anstelle des [erstellten autorisierten Benutzers](/help/sites-administering/sync.md#createauthuser) die Konfiguration des [Adobe Granite Distribution - Encrypted Password Transport Secret Provider](/help/sites-administering/sync.md#adobegraniteencpasswrd) in der Autoreninstanz, um Administratorberechtigungen zu verwenden. Versuchen Sie nun, die Pakete erneut zu installieren. Wenn die Benutzersynchronisierung mit Administratorberechtigungen ordnungsgemäß funktioniert, bedeutet dies, dass der erstellte Veröffentlichungsbenutzer nicht über entsprechende Zugriffssteuerungslisten verfügte.

1. **Konfiguration des Werks des Beobachters überprüfen**

   Wenn nur bestimmte Knoten nicht über die Veröffentlichungsfarm synchronisiert werden (z. B. sind Gruppenmitglieder nicht synchronisiert), stellen Sie sicher, dass die [Adobe Granite Distribution - Diff Observer Factory](/help/sites-administering/sync.md#diffobserver) -Konfiguration aktiviert ist und **rep: Member** werden in Namen **ausgesuchter Eigenschaften** festgelegt.

1. **Überprüfen Sie die Konfiguration von AEM Communities User Sync Listener.** Wenn die erstellten Benutzer synchronisiert werden, Abonnement und folgende Elemente jedoch nicht funktionieren, stellen Sie sicher, dass die AEM Communities User Sync Listener-Konfiguration über Folgendes verfügt:

   * Knotentypen - festgelegt auf **rep:User, nt:unstructured**, **nt:resource**, **rep:ACL**, **sling:Folder** und **sling:OrderedFolder**.
   * Ignorierbare Knoten - auf **.tokens**, **system** und **rep:cache** eingestellt.
   * Verteilte Ordner: Legen Sie die Ordner fest, die verteilt werden sollen.

1. **Bei der Benutzererstellung in der Veröffentlichungsinstanz generierte Protokolle überprüfen**

   Wenn die oben genannten Konfigurationen angemessen eingestellt sind und die Benutzersynchronisierung nicht funktioniert, überprüfen Sie die Protokolle, die bei der Benutzererstellung generiert wurden.

   Überprüfen Sie, ob die Reihenfolge der Protokolle wie folgt ist:

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

Debugging:

1. Deaktivieren Sie die Benutzersynchronisierung:
1. Melden Sie sich in der AEM-Autoreninstanz mit Administratorberechtigungen an.

   1. Access the [Web Console](/help/sites-deploying/configuring-osgi.md). For example, [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Locate the configuration **Apache Sling Distribution Agent - Sync Agents Factory**.
   1. Deaktivieren Sie das Kontrollkästchen **Aktiviert** .

      Beim Deaktivieren der Benutzersynchronisierung in der Autoreninstanz sind (Exporteur und Importeur) Endpunkte deaktiviert und die Autoreninstanz ist statisch. Die **vlt** -Pakete werden vom Autor nicht pinged oder fetched.

      Wenn nun ein Benutzer in der Veröffentlichungsinstanz erstellt wird, wird das **vlt** -Paket im Knoten */var/sling/distribution/packages/ socialpubsync - vlt /data* erstellt. Und wenn diese Pakete vom Autor an einen anderen Dienst gesendet werden. Sie können diese Daten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Dienste gesendet werden.

1. Wechseln Sie zu einem Herausgeber und erstellen Sie einen Benutzer im Herausgeber. Daher werden Ereignis erstellt.
1. Überprüfen Sie die [Reihenfolge der Protokolle](/help/communities/sync.md#troubleshoot-sling-distribution-in-aem-communities), die beim Erstellen des Benutzers erstellt werden.
1. Überprüfen Sie, ob ein **vlt** -Paket unter **/var/sling/distribution/packages/socialpubsync-vlt/data** erstellt wurde.
1. Aktivieren Sie jetzt die Benutzersynchronisierung in der AEM-Autoreninstanz.
1. Ändern Sie beim Herausgeber die Endpunkte des Exporteurs oder Importeurs in **Apache Sling Distribution Agent - Sync Agents Factory**.
Wir können Paketdaten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Herausgeber gesendet werden und welche Daten verloren gehen.
