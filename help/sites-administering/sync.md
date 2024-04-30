---
title: Benutzersynchronisierung
description: Erfahren Sie mehr über die inneren Funktionen der Benutzersynchronisierung in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 89f55598-e749-42b8-8f2a-496f45face66
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '2433'
ht-degree: 100%

---


# Benutzersynchronisierung{#user-synchronization}

## Einführung {#introduction}

Wenn es sich bei der Bereitstellung um eine [Veröffentlichungs-Farm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) handelt, müssen Mitglieder sich anmelden und ihre Daten in allen Veröffentlichungsknoten einsehen können.

In der Veröffentlichungsumgebung erstellte Benutzer und Benutzergruppen (Benutzerdaten) werden in der Autorenumgebung nicht benötigt.

Die meisten in der Autorenumgebung erstellten Benutzerdaten sollen in der Autorenumgebung verbleiben und nicht in die Veröffentlichungsinstanzen kopiert werden.

Registrierungs- und Änderungsvorgänge in einer Veröffentlichungsinstanz müssen mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben.

Ab AEM 6.1 werden Benutzerdaten bei aktivierter Benutzersynchronisierung automatisch über alle Veröffentlichungsinstanzen in der Farm hinweg synchronisiert und nicht in Autoreninstanzen erstellt.

## Sling Distribution {#sling-distribution}

Die Benutzerdaten werden zusammen mit den zugehörigen [Zugriffssteuerungslisten](/help/sites-administering/security.md) (Access Control Lists, ACLs) im [Oak-Core](/help/sites-deploying/platform.md), der Ebene unter Oak JCR, gespeichert und über die [Oak-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/jackrabbit/oak/api/package-tree.html) aufgerufen. Im Falle unregelmäßiger Aktualisierungen ist es sinnvoll, Benutzerdaten mit anderen Veröffentlichungsinstanzen per [Sling Content Distribution](https://github.com/apache/sling-old-svn-mirror/blob/trunk/contrib/extensions/distribution/README.md) (Sling-Distribution) zu synchronisieren.

Eine Benutzersynchronisierung mit Sling Distribution weist im Vergleich zur herkömmlichen Replikation folgende Vorteile auf:

* In Veröffentlichungsinstanzen erstellte *Benutzende*, *Benutzerprofile* und *Benutzergruppen* werden nicht in Autoreninstanzen erstellt.

* Sling Distribution legt Eigenschaften in jcr-Ereignissen fest, sodass innerhalb veröffentlichungsseitiger Ereignis-Listener agiert werden kann, ohne unendliche Replikationsschleifen berücksichtigen zu müssen.
* Per Sling-Distribution werden Benutzerdaten ausschließlich an nicht ursprüngliche Veröffentlichungsinstanzen gesendet, wodurch unnötiger Traffic vermieden wird.
* Im Benutzerknoten festgelegte [ACLs](/help/sites-administering/security.md) werden bei der Synchronisierung eingeschlossen.

>[!NOTE]
>
>Wenn Sitzungen erforderlich sind, wird empfohlen, entweder eine SSO-Lösung oder eine „Sticky Session“ (auch als Sitzungspersistenz bezeichnet) zu verwenden und dafür zu sorgen, dass sich Kundinnen und Kunden beim Wechsel zu einer anderen Veröffentlichungsinstanz anmelden müssen.

>[!CAUTION]
>
>Die Synchronisierung der **Administratorgruppe** wird nicht unterstützt, auch nicht bei aktivierter Benutzersynchronisierung. Stattdessen wird ein Fehler beim „Diff-Import“ in das Fehlerprotokoll geschrieben.
>
>Wenn es sich bei der Bereitstellung um eine Veröffentlichungs-Farm handelt, muss daher beim Hinzufügen oder Entfernen von Benutzenden aus der **Administratorgruppe** die Änderung manuell für jede Veröffentlichungsinstanz durchgeführt werden.

## Aktivieren der Benutzersynchronisierung {#enable-user-sync}

>[!NOTE]
>
>Standardmäßig ist für die Benutzersynchronisierung `disabled` festgelegt.
>
>Die Aktivierung der Benutzersynchronisierung beinhaltet die Änderung *vorhandener* OSGi-Konfigurationen.
>
>Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Die Benutzersynchronisierung ist davon abhängig, dass die Autorenumgebung die Verteilung der Benutzerdaten verwaltet, auch wenn die Benutzerdaten nicht in der Autoreninstanz erstellt werden. Ein wesentlicher Teil, aber nicht die vollständige Konfiguration findet in der Autorenumgebung statt. Dabei ist für jeden Schritt klar festgelegt, ob er in der Autoren- oder Veröffentlichungsinstanz durchgeführt werden muss.

Im Folgenden finden Sie eine Beschreibung der Schritte, die zum Aktivieren der Benutzersynchronisierung erforderlich sind, gefolgt von einem Abschnitt zur [Fehlerbehebung](#troubleshooting):

### Voraussetzungen {#prerequisites}

1. Wenn Benutzende und Benutzergruppen bereits in einer Veröffentlichungsinstanz erstellt wurden, wird empfohlen, die Benutzerdaten für alle Veröffentlichungsinstanzen [manuell zu synchronisieren](#manually-syncing-users-and-user-groups), bevor Sie die Benutzersynchronisierung konfigurieren und aktivieren.

Sobald die Benutzersynchronisierung aktiviert wurde, werden nur neu erstellte Benutzende und Gruppen synchronisiert.

1. Stellen Sie sicher, dass der neueste Code installiert ist:

* [AEM-Plattform-Updates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de)
* [AEM Communities-Updates](/help/communities/deploy-communities.md#latestfeaturepack)

### 1. Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

**Aktivieren der Benutzersynchronisierung**

* **in der Autoreninstanz**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Agent - Sync Agents Factory`.

      * Wählen Sie die vorhandene Konfiguration aus, damit Sie sie zur Bearbeitung öffnen können (Bleistiftsymbol).
Vergewissern Sie sich, dass unter `name` der Eintrag **`socialpubsync`** angegeben ist.

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

![Apache Sling Distribution Agent](assets/chlimage_1-20.png)

### 2. Erstellen autorisierter Benutzer {#createauthuser}

**Konfigurieren von Berechtigungen**

Die autorisierte Benutzerin bzw. der autorisierte Benutzer wird in Schritt 3 zum Konfigurieren der Sling-Distribution in der Autoreninstanz verwendet.

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Sicherheitskonsole](/help/sites-administering/security.md) auf.

      * Beispiel: [https://localhost:4503/useradmin](https://localhost:4503/useradmin)

   * Erstellen Sie eine Benutzerin bzw. einen Benutzer.

      * Beispiel: `usersync-admin`

   * Fügen Sie diesen Benutzer der Benutzergruppe **`administrators`** hinzu.
   * [Fügen Sie für diesen Benutzer eine ACL unter /home hinzu.](#howtoaddacl)

      * `Allow jcr:all` mit der Einschränkung `rep:glob=*/activities/*`

>[!CAUTION]
>
>Es muss ein neuer Benutzer erstellt werden.
>
>* Als Standardbenutzer wird **`admin`** zugewiesen.
>* Verwenden Sie `communities-user-admin user.` nicht.
>

#### Hinzufügen von ACL {#addacls}

* Rufen Sie CRXDE Lite auf

   * Beispiel: [https://localhost:4503/crx/de](https://localhost:4503/crx/de)

* Wählen Sie den Knoten `/home` aus.
* Wählen Sie im rechten Bereich die Registerkarte `Access Control` aus.
* Wählen Sie die Schaltfläche `+` aus, um einen ACL-Eintrag hinzuzufügen. 

   * **Prinzipal**: *nach dem für die Benutzersynchronisierung erstellten Benutzer suchen*
   * **Typ**: `Allow`
   * **Berechtigungen**: `jcr:all`
   * **Einschränkungen** `rep:glob`: `*/activities/*`
   * Wählen Sie **OK** aus

* Wählen Sie **Alle speichern**

![ACL-Fenster hinzufügen](assets/chlimage_1-21.png)

Siehe auch

* [Verwalten von Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Fehlerbehebungsabschnitt [Ausnahme bei Änderungsvorgang während Antwortverarbeitung](#modify-operation-exception-during-response-processing).

### 3. Adobe Granite Distribution – Encrypted Password Transport Secret Provider {#adobegraniteencpasswrd}

**Konfigurieren von Berechtigungen**

Wenn eine autorisierte Benutzerin oder ein autorisierter Benutzer – ein Mitglied der Benutzergruppe **`administrators`** – in allen Veröffentlichungsinstanzen erstellt wird, muss diese autorisierte Benutzerin oder dieser autorisierte Benutzer in der Autoreninstanz als eine Person identifiziert werden, die zum Synchronisieren von Benutzerdaten zwischen Autoren- und Veröffentlichungsinstanzen berechtigt ist.

* **In der Autoreninstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`.
   * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).
Vergewissern Sie sich, dass unter `property name` der Eintrag **`socialpubsync-publishUser`** angegeben ist.

   * Legen Sie den Benutzernamen und das Kennwort für [die autorisierte Benutzerin bzw. den autorisierten Benutzer](#createauthuser) fest, die bzw. der in der Veröffentlichungsinstanz in Schritt 2 erstellt wurde.

      * Beispiel: `usersync-admin`

![Encrypted Password Transport Secret Provider](assets/chlimage_1-22.png)

### 4. Apache Sling Distribution Agent – Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Aktivieren der Benutzersynchronisierung**

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Agent - Queue Agents Factory`.

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).
Vergewissern Sie sich, dass unter `Name` der Eintrag `socialpubsync-reverse` angegeben ist.

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

   * **Wiederholen** Sie den Vorgang für jede Veröffentlichungsinstanz.

![Queue Agents Factory](assets/chlimage_1-23.png)

### 5. Adobe Social Sync – Diff Observer Factory {#diffobserver}

**Aktivieren der Gruppensynchronisierung**

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

   * Suchen Sie **`Adobe Social Sync - Diff Observer Factory`**.

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

        Überprüfen Sie `agent name`: `socialpubsync-reverse`

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

![Diff Observer Factory](assets/screen-shot_2019-05-24at090809.png)

### 6. Apache Sling Distribution Trigger – Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Optional) Bearbeiten des Abrufintervalls**

Standardmäßig werden Änderungen autorenseitig alle 30 Sekunden abgerufen. So ändern Sie dieses Intervall:

* **In der Autoreninstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Trigger - Scheduled Triggers Factory`.

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

         * Überprüfen Sie `Name`: `socialpubsync-scheduled-trigger`

      * Stellen Sie `Interval in Seconds` auf das gewünschte Intervall ein.
      * Wählen Sie `Save` aus.

![Scheduled Triggers Factory](assets/chlimage_1-24.png)

## Konfigurieren für mehrere Publishing-Instanzen {#configure-for-multiple-publish-instances}

Die Standardkonfiguration gilt für eine einzelne Veröffentlichungsinstanz. Da durch die Benutzersynchronisierung mehrere Veröffentlichungsinstanzen, etwa für eine Veröffentlichungs-Farm, synchronisiert werden sollen, müssen die zusätzlichen Veröffentlichungsinstanzen der Sync Agents Factory hinzugefügt werden.

### 7. Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Hinzufügen von Veröffentlichungsinstanzen:**

* **In der Autoreninstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Agent - Sync Agents Factory`.

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).
Vergewissern Sie sich, dass unter `Name` der Eintrag `socialpubsync` angegeben ist.

![Sync Agents Factory](assets/chlimage_1-25.png)

* **Exporter-Endpunkte**
Es sollte für jede Veröffentlichungsinstanz einen Exporter-Endpunkt geben. Beispielsweise sollten bei zwei Veröffentlichungsinstanzen, „localhost:4503“ und „localhost:4504“, zwei Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse`
   * `https://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse`

* **Importer-Endpunkte**
Es sollte für jede Veröffentlichungsinstanz einen Importer-Endpunkt geben. Beispielsweise sollten bei zwei Veröffentlichungsinstanzen, „localhost:4503“ und „localhost:4504“, zwei Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/importers/socialpubsync`
   * `https://localhost:4504/libs/sling/distribution/services/importers/socialpubsync`

* Wählen Sie `Save` aus.

### 8. AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

**(Optional) Synchronisieren zusätzlicher JCR-Knoten**

Wenn benutzerdefinierte Daten vorliegen, die über mehrere Veröffentlichungsinstanzen hinweg synchronisiert werden sollen, gehen Sie wie folgt vor:

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: `https://localhost:4503/system/console/configMgr`

   * Suchen Sie `AEM Communities User Sync Listener`.
   * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).
Vergewissern Sie sich, dass unter `Name` der Eintrag `socialpubsync-scheduled-trigger` angegeben ist.

![AEM Communities User Sync Listener](assets/chlimage_1-26.png)

* **Node Types (Knotentypen)**
Hierbei handelt es sich um die Liste der Knotentypen, die synchronisiert werden. Mit Ausnahme von „sling:Folder“ müssen hier alle Knotentypen aufgeführt werden („sling:Folder“ wird separat abgewickelt).
Standardliste zu synchronisierender Knotentypen:

   * rep:User
   * nt:unstructured
   * nt:resource

* **Ignorable Properties (Ignorierbare Eigenschaften)**
Hierbei handelt es sich um die Liste der Eigenschaften, die beim Erkennen von Änderungen ignoriert werden. Änderungen an diesen Eigenschaften werden möglicherweise im Zuge anderer Änderungen synchronisiert (da die Synchronisierung immer auf Knotenebene erfolgt), aber Änderungen an diesen Eigenschaften lösen nicht von selbst eine Synchronisierung aus.
Zu ignorierende Standardeigenschaft:

   * cq:lastModified

* **Ignorable Nodes (Ignorierbare Knoten)**
Hierbei handelt es sich um Unterpfade, die während der Synchronisierung ignoriert werden. Elemente in diesen Unterpfaden werden nie synchronisiert.
Zu ignorierende Standardknoten:

   * .tokens
   * system

* **Distributed Folders**
Die meisten Sling:Folders werden ignoriert, weil eine Synchronisierung nicht erforderlich ist. Die wenigen Ausnahmen finden Sie hier aufgeführt.
Zu synchronisierende Standardordner

   * segments/scoring
   * social/relationships
   * activities

### 9. Eindeutige Sling-ID {#unique-sling-id}

>[!CAUTION]
>
>Wenn die Sling-ID zwischen zwei oder mehr Veröffentlichungsinstanzen übereinstimmt, schlägt die Benutzergruppensynchronisierung fehl.

Wenn die Sling-ID für mehrere Veröffentlichungsinstanzen in einer Veröffentlichungs-Farm identisch ist, werden Benutzergruppen nicht synchronisiert.

Um zu überprüfen, ob alle Sling-ID-Werte unterschiedlich sind, gehen Sie in jeder Veröffentlichungsinstanz wie folgt vor:

1. Navigieren Sie zu `http://<host>:<port>/system/console/status-slingsettings`.
1. Überprüfen Sie den Wert unter **Sling ID**.

![Prüfen des Wertes der Sling-ID](assets/chlimage_1-27.png)

Wenn die Sling-ID einer Veröffentlichungsinstanz der Sling-ID einer anderen Veröffentlichungsinstanz entspricht, gehen Sie wie folgt vor:

1. Beenden Sie eine der Veröffentlichungsinstanzen mit übereinstimmender Sling-ID.
1. Gehen Sie wie folgt im Verzeichnis „crx-quickstart/launchpad/felix“ vor:

   * Suchen und löschen Sie die Datei *sling.id.file*

      * Beispiel für ein Linux®-System:
        `rm -i $(find . -type f -name sling.id.file)`

      * Beispiel für ein Windows-System:
        `use windows explorer and search for *sling.id.file*`

1. Starten Sie die Veröffentlichungsinstanz.

   * Beim Start wird der Instanz eine neue Sling-ID zugewiesen.

1. Vergewissern Sie sich, dass die **Sling-ID** nun eindeutig ist.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

## Vault Package Builder Factory {#vault-package-builder-factory}

Damit Aktualisierungen ordnungsgemäß synchronisiert werden, muss der Vault Package Builder zur Benutzersynchronisierung geändert werden:

* In jeder AEM-Veröffentlichungsinstanz:
* Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

   * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Suchen Sie `Apache Sling Distribution Packaging - Vault Package Builder Factory`.

   * `Builder name: socialpubsync-vlt`

* Wählen Sie das Bearbeitungssymbol aus.
* Fügen Sie zwei `Package Node Filters` hinzu:

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* Richtlinienhandhabung:

   * Zum Überschreiben der vorhandenen Knoten „rep:policy“ mit neuen fügen Sie einen dritten Paketfilter hinzu:

      * `/home/users|+.*/rep:policy`

   * Um eine Richtlinienverteilung zu verhindern, stellen Sie Folgendes ein:

      * `Acl Handling:` `IGNORE`

![Vault Package Builder Factory](assets/vault-package-builder-factory.png)

## Verfahren bei … {#what-happens-when}

### Selbstregistrierung oder Profilbearbeitung von Benutzenden in der Publishing-Umgebung {#user-self-registers-or-edits-profile-on-publish}

Per Design werden in der Veröffentlichungsumgebung erstellte Benutzer und Profile (Selbstregistrierung) nicht in der Autorenumgebung angezeigt.

Wenn es sich bei der Topologie um eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) handelt und die Benutzersynchronisierung korrekt konfiguriert wurde, werden *Benutzende* und *Benutzerprofil* über die Veröffentlichungsfarm hinweg mittels Sling Distribution synchronisiert.

### Erstellung von Benutzenden oder Benutzergruppen über die Sicherheitskonsole {#users-or-user-groups-are-created-using-security-console}

Per Design werden die in der Veröffentlichungsumgebung erstellten Benutzerdaten nicht in der Autorenumgebung angezeigt (und umgekehrt).

Wenn in der Veröffentlichungsmgebung neue Benutzende über die Konsole [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) hinzugefügt werden, werden die neuen Benutzenden und ihre Gruppenmitgliedschaft im Rahmen der Benutzersynchronisierung ggf. mit anderen Veröffentlichungsinstanzen synchronisiert. Bei der Benutzersynchronisierung werden auch die über die Sicherheitskonsole erstellten Benutzergruppen synchronisiert.

## Fehlerbehebung {#troubleshooting}

### So schalten Sie die Benutzersynchronisierung offline {#how-to-take-user-sync-offline}

Um die Benutzersynchronisierung zwecks [Entfernung einer Veröffentlichungsinstanz](#how-to-remove-a-publish-instance) oder [manueller Datensynchronisierung](#manually-syncing-users-and-user-groups) offline zu schalten, muss die Verteilungswarteschlange leer und störungsfrei sein.

So prüfen Sie den Status der Verteilungswarteschlange:

* In der Autoreninstanz:

   * Rufen Sie [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) auf.

      * Suchen Sie nach Einträgen in den Ordnerknoten `/var/sling/distribution/packages`,

         * die nach dem Muster `distrpackage_*` benannt sind.

   * Rufen Sie [Package Manager](/help/sites-administering/package-manager.md) auf

      * Suchen Sie nach ausstehenden (noch nicht installierten) Paketen,

         * die nach dem Muster `socialpubsync-vlt*` benannt sind,
         * die von `communities-user-admin` erstellt wurden.

Wenn die Verteilungswarteschlange leer ist, deaktivieren Sie die Benutzersynchronisierung:

* In der Autoreninstanz:

   * *Deaktivieren* Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

Um die Benutzersynchronisierung nach Durchführung der Aufgaben erneut zu aktivieren, gehen Sie wie folgt vor:

* In der Autoreninstanz:

   * Aktivieren Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

### Diagnose für Benutzersynchronisierung {#user-sync-diagnostics}

Die Diagnose für Benutzersynchronisierung ist ein Tool zur Überprüfung von Konfigurationen und zur Identifizierung etwaiger Probleme.

Navigieren Sie in der Autoreninstanz von der Hauptkonsole zu **Tools > Vorgänge > Diagnose > Diagnose für Benutzersynchronisierung**.

Die Ergebnisse werden einfach durch Aufrufen der Konsole „Diagnose für Benutzersynchronisierung“ angezeigt.

Folgendes wird angezeigt, wenn die Benutzersynchronisierung nicht aktiviert wurde:

![Warnung, dass die Diagnose der Benutzersynchronisierung nicht aktiviert ist](assets/chlimage_1-28.png)

#### Ausführen der Diagnose für Veröffentlichungsinstanzen {#how-to-run-diagnostics-for-publish-instances}

Wenn die Diagnose in der Autorenumgebung ausgeführt wird, umfassen die als bestanden oder fehlgeschlagen gekennzeichneten Ergebnisse einen [INFO]-Abschnitt mit einer Liste der konfigurierten Veröffentlichungsinstanzen zur Bestätigung.

In der Liste enthalten ist eine URL für jede Veröffentlichungsinstanz, die die Diagnose für diese Instanz ausführt. Der URL-Parameter `syncUser` ist an die Diagnose-URL angehängt. Der Wert lautet dabei auf den *autorisierten Sychronisierungsbenutzer*, der in [Schritt 2](#createauthuser) erstellt wurde.

**Hinweis**: Bevor Sie die URL aufrufen, muss *die autorisierte Synchronisierungsbenutzerin oder der autorisierte Synchronisierungsbenutzer* bereits bei dieser Veröffentlichungsinstanz angemeldet sein.

![Diagnose für Publishing-Instanzen](assets/chlimage_1-29.png)

### Fehlerhaft hinzugefügte Konfiguration {#configuration-improperly-added}

Wenn die Benutzersynchronisierung nicht funktioniert, besteht das häufigste Problem darin, dass zusätzliche Konfigurationen *hinzugefügt* wurden. Stattdessen sollte die *vorhandene* Standardkonfiguration *bearbeitet* werden.

Im Folgenden sehen Sie, wie die bearbeiteten Standardkonfigurationen in der Web-Konsole angezeigt werden sollten. Bei mehr als der einen Instanz sollte die hinzugefügte Konfiguration entfernt werden.

#### (Autoreninstanz) Eine Konfiguration „Apache Sling Distribution Agent – Sync Agents Factory“ {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-30.png)

#### (Autoreninstanz) Eine Konfiguration „Apache Sling Distribution Transport Credentials – User Credentials based DistributionTransportSecretProvider“ {#author-one-apache-sling-distribution-transport-credentials-user-credentials-based-distributiontransportsecretprovider}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-31.png)

#### (Veröffentlichungsinstanz) Eine Konfiguration „Apache Sling Distribution Agent – Queue Agents Factory“ {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-32.png)

#### (Veröffentlichungsinstanz) Eine Konfiguration „Adobe Social Sync – Diff Observer Factory“ {#publish-one-adobe-social-sync-diff-observer-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-33.png)

#### (Autoreninstanz) Eine Konfiguration „Apache Sling Distribution Trigger – Scheduled Triggers Factory“ {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-34.png)

### Ausnahme bei Änderungsvorgang während der Antwortverarbeitung {#modify-operation-exception-during-response-processing}

Wenn Folgendes im Protokoll steht:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

prüfen Sie, ob Abschnitt [2. Erstellen autorisierter Benutzer](#createauthuser) ordnungsgemäß befolgt wurde.

Dieser Abschnitt beschreibt, wie eine autorisierte Benutzerin oder ein autorisierter Benutzer erstellt wird, die oder der in allen Veröffentlichungsinstanzen vorhanden ist, und wie diese Benutzerin oder dieser Benutzer in der OSGi-Konfiguration „Secret Provider“ der Autoreninstanz identifiziert wird. Standardmäßig ist `admin` der Benutzer.

Der autorisierte Benutzer sollte als Mitglied der Benutzergruppe **`administrators`** aufgenommen werden. Außerdem sollten die Berechtigungen für diese Gruppe nicht geändert werden.

Für die autorisierte Benutzerin oder den autorisierten Benutzer sollten explizit die folgenden Rechte und Einschränkungen für alle Veröffentlichungsinstanzen gelten:

| **Pfad** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | &#42;/activities/&#42; |
| /home/users | X | &#42;/activities/&#42; |
| /home/groups | X | &#42;/activities/&#42; |

Als Mitglied der Gruppe `administrators` sollten für die autorisierte Benutzerin oder den autorisierten Benutzer die folgenden Rechte für alle Veröffentlichungsinstanzen gelten:

| **Pfad** | **jcr:all** | **jcr:read** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Fehlgeschlagene Benutzergruppensynchronisierung {#user-group-sync-failed}

Wenn die Sling-ID zwischen zwei oder mehr Veröffentlichungsinstanzen übereinstimmt, schlägt die Benutzergruppensynchronisierung fehl.

Siehe Abschnitt [9. Eindeutige Sling-ID](#unique-sling-id)

### Manuelles Synchronisieren von Benutzenden und Benutzergruppen {#manually-syncing-users-and-user-groups}

* In Veröffentlichungsinstanzen mit vorhandenen Benutzenden und Benutzergruppen:

   * [Deaktivieren Sie ggf. die Benutzersynchronisierung.](#how-to-take-user-sync-offline)
   * [Erstellen Sie ein Paket](/help/sites-administering/package-manager.md#creating-a-new-package) von `/home`.

      * Beim Bearbeiten des Pakets

         * Registerkarte „Filter“: „Filter hinzufügen“: > „Stammverzeichnis“: `/home`
         * Registerkarte „Erweitert“ > „AC-Handhabung“: `Overwrite`

   * [Exportieren Sie das Paket.](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)

* In anderen Veröffentlichungsinstanzen:

   * [Importieren Sie das Paket.](/help/sites-administering/package-manager.md#installing-packages)

Zum Konfigurieren oder Aktivieren der Benutzersynchronisierung gehen Sie zu Schritt 1: [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

### Bei Nichtverfügbarkeit einer Veröffentlichungsinstanz {#when-a-publish-instance-becomes-unavailable}

Wenn eine Veröffentlichungsinstanz nicht mehr verfügbar ist, sollte sie nicht entfernt werden, sofern sie in Zukunft wieder online geschaltet wird. Änderungen werden für die Veröffentlichungsinstanz in die Warteschlange gestellt. Sobald sie wieder online ist, werden die Änderungen verarbeitet.

Wenn die Veröffentlichungsinstanz nicht wieder online geschaltet wird, also dauerhaft offline ist, muss sie entfernt werden, weil durch das Auffüllen der Warteschlangen der Speicherplatz in der Autorenumgebung spürbar beansprucht wird.

Wenn eine Veröffentlichungsinstanz nicht verfügbar ist, werden im Autorenprotokoll Ausnahmen wie diese angezeigt:

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Entfernen einer Veröffentlichungsinstanz {#how-to-remove-a-publish-instance}

Um eine Veröffentlichungsinstanz aus der [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory) zu entfernen, muss die Verteilungswarteschlange leer und störungsfrei sein.

* In der Autoreninstanz:

   * [Schalten Sie die Benutzersynchronisierung offline.](#how-to-take-user-sync-offline)
   * Folgen Sie [Schritt 7](#apache-sling-distribution-agent-sync-agents-factory), um die Veröffentlichungsinstanz aus beiden Server-Listen zu entfernen:

      * `Exporter Endpoints`
      * `Importer Endpoints`

   * Erneutes Aktivieren der Benutzersynchronisierung

      * Aktivieren Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).
