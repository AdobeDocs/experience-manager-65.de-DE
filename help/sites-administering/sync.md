---
title: Benutzersynchronisierung
seo-title: Benutzersynchronisierung
description: Erfahren Sie mehr über die Benutzersynchronisierung in AEM.
seo-description: Erfahren Sie mehr über die Benutzersynchronisierung in AEM.
uuid: 0a519daf-21b7-4adc-b419-eeb8c404c54f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: c061b358-8c0d-40d3-8090-dc9800309ab3
docset: aem65
translation-type: tm+mt
source-git-commit: 8ed7409740cdd3e45fad006dc6e470a06acc60fe
workflow-type: tm+mt
source-wordcount: '2436'
ht-degree: 73%

---


# Benutzersynchronisierung{#user-synchronization}

## Einführung {#introduction}

Wenn es sich bei der Bereitstellung um eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) handelt, müssen Mitglieder sich anmelden und ihre Daten auf allen Veröffentlichungsknoten einsehen können.

In der Veröffentlichungsumgebung erstellte Benutzer und Benutzergruppen (Benutzerdaten) werden in der Autorenumgebung nicht benötigt.

Die meisten in der Autorenumgebung erstellten Benutzerdaten sind auf einen Verbleib in der Autorenumgebung ausgelegt und werden nicht in Veröffentlichungsinstanzen kopiert.

Registrierungs- und Änderungsvorgänge in einer Veröffentlichungsinstanz müssen mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben.

Ab AEM 6.1 werden Benutzerdaten bei aktivierter Benutzersynchronisierung automatisch über alle Veröffentlichungsinstanzen in der Farm hinweg synchronisiert und nicht in Autoreninstanzen erstellt.

## Sling Distribution {#sling-distribution}

The user data, along with their [ACLs](/help/sites-administering/security.md), are stored in the [Oak Core](/help/sites-deploying/platform.md), the layer below Oak JCR, and are accessed using the [Oak API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). With infrequent updates, it is reasonable for user data to be synchronized with other publish instances using [Sling Content Distribution](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md) (Sling distribution).

Die Vorteile der Benutzersynchronisierung mit der Sling-Distribution im Vergleich zur herkömmlichen Replikation sind:

* In Veröffentlichungsinstanzen erstellte *Benutzer*, *Benutzerprofile* und *Benutzergruppen* werden nicht in Autoreninstanzen erstellt.

* Sling Distribution legt Eigenschaften in jcr-Ereignissen fest, sodass innerhalb veröffentlichungsseitiger Event-Listener agiert werden kann, ohne unendliche Replikationsschleifen berücksichtigen zu müssen.
* Sling Distribution sendet Benutzerdaten ausschließlich an nicht ursprüngliche Veröffentlichungsinstanzen, wodurch unnötiger Traffic beseitigt wird.
* [ACLs](/help/sites-administering/security.md) , die auf dem Benutzerknoten festgelegt sind, sind in der Synchronisierung enthalten

>[!NOTE]
>
>Wenn Sitzungen erforderlich sind, wird empfohlen, entweder eine SSO-Lösung oder eine fixierbare Sitzung zu verwenden und Kunden anzumelden, wenn sie zu einem anderen Herausgeber wechseln.

>[!CAUTION]
>
>Die Synchronisierung der ***Administratorgruppe*** wird nicht unterstützt, auch nicht bei aktivierter Benutzersynchronisierung. Stattdessen wird ein Fehler beim Diff-Import in das Fehlerprotokoll geschrieben.
>
>Therefore, when the deployment is a publish farm, if a user is added to or removed from the ***administrators** group, the modification must be manually made on each publish instance.

## Aktivieren der Benutzersynchronisierung {#enable-user-sync}

>[!NOTE]
>
>By default, user sync is `disabled`.
>
>Die Aktivierung der Benutzersynchronisierung beinhaltet die Änderung *vorhandener* OSGi-Konfigurationen.
>
>Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Die Benutzersynchronisierung ist davon abhängig, dass die Autorenumgebung die Verteilung der Benutzerdaten verwaltet, auch wenn die Benutzerdaten nicht in der Autoreninstanz erstellt werden. Viele, aber nicht alle der Konfigurationen finden in der Autorenkonfiguration statt und jeder Schritt gibt klar an, ob sie beim Autor oder beim Veröffentlichen durchgeführt werden soll.

Im Folgenden finden Sie eine Beschreibung der Schritte, die zum Aktivieren der Benutzersynchronisierung erforderlich sind, gefolgt von einem Abschnitt zur [Fehlerbehebung](#troubleshooting):

### Voraussetzungen {#prerequisites}

1. Wenn Benutzer und Benutzergruppen bereits auf einem Herausgeber erstellt wurden, wird empfohlen, die Benutzerdaten vor der Konfiguration und Aktivierung der Benutzersynchronisierung [manuell zu synchronisieren](#manually-syncing-users-and-user-groups).

Sobald die Benutzersynchronisierung aktiviert wurde, werden nur neu erstellte Benutzer und Gruppen synchronisiert.

1. Stellen Sie sicher, dass der neueste Code installiert wurde:

* [AEM-Plattformupdates](https://helpx.adobe.com/de/experience-manager/kb/aem62-available-hotfixes.html)
* [AEM Communities-Updates](/help/communities/deploy-communities.md#latestfeaturepack)

### 1. Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

**Aktivieren der Benutzersynchronisierung**

* **In der Autoreninstanz:**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * suchen `Apache Sling Distribution Agent - Sync Agents Factory`

      * select the existing configuration to open for edit (pencil icon)
Verify `name`: **`socialpubsync`**

      * select the `Enabled` checkbox
      * auswählen `Save`


![](assets/chlimage_1-20.png)

### 2. Erstellen autorisierter Benutzer {#createauthuser}

**Konfigurieren von Berechtigungen** Dieser autorisierte Benutzer wird in Schritt 3 zum Konfigurieren einer Sling Distribution in Autoreninstanzen verwendet.

* **In jeder Veröffentlichungsinstanz:**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Sicherheitskonsole](/help/sites-administering/security.md) auf.

      * for example, [https://localhost:4503/useradmin](https://localhost:4503/useradmin)
   * Erstellen Sie einen neuen Benutzer.

      * for example, `usersync-admin`
   * add this user to the **`administrators`** user group
   * [ACL für diesen Benutzer zu /home hinzufügen](#howtoaddacl)

      * `Allow jcr:all` mit Einschränkungen `rep:glob=*/activities/*`



>[!CAUTION]
>
>Ein neuer Benutzer muss erstellt werden.
>
>* Als Standardbenutzer wird **`admin`** zugewiesen.
>* Nicht verwenden `communities-user-admin user.`

>



#### Hinzufügen von ACLs {#addacls}

* Rufen Sie CRXDE Lite auf.

   * for example, [https://localhost:4503/crx/de](https://localhost:4503/crx/de)

* Knoten auswählen `/home`
* im rechten Bereich die `Access Control` Registerkarte
* select the `+` button to add an ACL entry

   * **Prinzipal**: *nach dem für die Benutzersynchronisierung erstellten Benutzer suchen*
   * **Typ**: `Allow`
   * **Berechtigungen**: `jcr:all`
   * **Einschränkungen** rep:glob: `*/activities/*`
   * Wählen Sie **OK** aus.

* Wählen Sie **Alle speichern** aus.

![](assets/chlimage_1-21.png)

Siehe auch

* [Verwalten von Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Troubleshooting section [Modify Operation Exception During Response Processing](#modify-operation-exception-during-response-processing).

### 3. Adobe Granite Distribution – Encrypted Password Transport Secret Provider {#adobegraniteencpasswrd}

**Konfigurieren von Berechtigungen**

Once an authorized user, a member of the **`administrators`**user group, has been created on all publish instances, that authorized user must be identified on author as having permission to sync user data from author to publish.

* **In der Autoreninstanz:**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * suchen `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`
   * select the existing configuration to open for edit (pencil icon)
Verify `property name`: **`socialpubsync-publishUser`**

   * Legen Sie den Benutzernamen und das Kennwort für den in der Veröffentlichungsinstanz in Schritt 2 erstellten [autorisierten Benutzer](#createauthuser) fest.

      * for example, `usersync-admin`


![](assets/chlimage_1-22.png)

### 4. Apache Sling Distribution Agent – Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Aktivieren der Benutzersynchronisierung**

* **In der Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * suchen `Apache Sling Distribution Agent - Queue Agents Factory`

      * select the existing configuration to open for edit (pencil icon)
Verify `Name`: `socialpubsync-reverse`

      * select the `Enabled` checkbox
      * auswählen `Save`
   * **Wiederholen **für jede Instanz im Veröffentlichungsmodus



![](assets/chlimage_1-23.png)

### 5. Adobe Social Sync - Diff Observer Factory {#diffobserver}

**Aktivieren der Gruppensynchronisierung**

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * suchen **`Adobe Social Sync - Diff Observer Factory`**

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

         Überprüfen `agent name`: `socialpubsync-reverse`

      * select the `Enabled` checkbox
      * auswählen `Save`


![](assets/screen-shot_2019-05-24at090809.png)

### 6. Apache Sling Distribution Trigger – Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Optional) Bearbeiten des Abrufintervalls**

Standardmäßig ruft der Autor Änderungen alle 30 Sekunden ab. So ändern Sie dieses Intervall:

* **In der Autoreninstanz:**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * suchen `Apache Sling Distribution Trigger - Scheduled Triggers Factory`

      * Wählen Sie die vorhandene Konfiguration aus, um sie zur Bearbeitung zu öffnen (Bleistiftsymbol).

         * Überprüfen `Name`: `socialpubsync-scheduled-trigger`
      * set the `Interval in Seconds` to the desired interval
      * auswählen `Save`



![](assets/chlimage_1-24.png)

## Konfigurieren für mehrere Veröffentlichungsinstanzen {#configure-for-multiple-publish-instances}

Die Standardkonfiguration ist für eine einzelne Veröffentlichungsinstanz vorgesehen. Da durch die Benutzersynchronisierung mehrere Veröffentlichungsinstanzen, etwa für eine Veröffentlichungsfarm, synchronisiert werden sollen, müssen die zusätzlichen Veröffentlichungsinstanzen der Synchronisierungsagenten-Factory hinzugefügt werden.

### 7. Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Hinzufügen von Veröffentlichungsinstanzen:**

* **In der Autoreninstanz:**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * suchen `Apache Sling Distribution Agent - Sync Agents Factory`

      * select the existing configuration to open for edit (pencil icon)
Verify `Name`: `socialpubsync`


![](assets/chlimage_1-25.png)

* **Exporter Endpoints** Es sollte für jeden Herausgeber einen Exporter-Endpunkt geben. Beispielsweise sollten bei 2 Herausgebern, localhost:4503 und 4504, 2 Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse`
   * `https://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse`

* **Importer-Endpunkte** Es sollte einen Importeur-Endpunkt für jeden Herausgeber geben. Beispielsweise sollten bei 2 Herausgebern, localhost:4503 und 4504, 2 Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/importers/socialpubsync`
   * `https://localhost:4504/libs/sling/distribution/services/importers/socialpubsync`

* auswählen `Save`

### 8. AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

**(Optional) Synchronisieren zusätzlicher JCR-Knoten**

Wenn benutzerdefinierte Daten vorliegen, die über mehrere Veröffentlichungsinstanzen hinweg synchronisiert werden sollen, gehen Sie wie folgt vor:

* **In jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

      * for example, `https://localhost:4503/system/console/configMgr`
   * suchen `AEM Communities User Sync Listener`
   * select the existing configuration to open for edit (pencil icon)
Verify `Name`: `socialpubsync-scheduled-trigger`


![](assets/chlimage_1-26.png)

* **Node Types** Hierbei handelt es sich um die Liste der Knotentypen, die synchronisiert werden. Mit Ausnahme von „sling:Folder“ müssen hier alle Knotentypen aufgeführt werden („sling:Folder“ wird separat abgewickelt).
Standardliste zu synchronisierender Knotentypen:

   * rep:User
   * nt:unstructured
   * nt:resource

* **Ignorable Properties** Hierbei handelt es sich um die Liste der Eigenschaften, die beim Erkennen von Änderungen ignoriert werden. Änderungen an diesen Eigenschaften werden möglicherweise im Zuge anderer Änderungen synchronisiert (da die Synchronisierung immer auf Knotenebene erfolgt), aber Änderungen an diesen Eigenschaften werden nicht von selbst durch eine Synchronisierung ausgelöst.
Zu ignorierende Standardeigenschaft:

   * cq:lastModified

* **Ignorable Nodes**Hierbei handelt es sich um Unterpfade, die während der Synchronisierung vollständig ignoriert werden. Elemente in diesen Unterpfaden werden nie synchronisiert.
Zu ignorierende Standardknoten:

   * .tokens
   * system

* **Distributed Folders**Die meisten Sling:Folders werden ignoriert, weil eine Synchronisierung nicht erforderlich ist. Die wenigen Ausnahmen finden Sie hier aufgeführt.
Zu synchronisierende Standardordner

   * segments/scoring
   * social/relationships
   * activities

### 9. Eindeutige Sling-ID {#unique-sling-id}

>[!CAUTION]
>
>Wenn die Sling-ID zwischen zwei oder mehr Veröffentlichungsinstanzen übereinstimmt, schlägt die Benutzergruppesynchronisierung fehl.

Wenn die Sling-ID für mehrere Veröffentlichungsinstanzen in einer Veröffentlichungsfarm identisch ist, werden Benutzergruppen nicht synchronisiert.

Um zu überprüfen, ob alle Sling-ID-Werte unterschiedlich sind, gehen Sie in jeder Veröffentlichungsinstanz wie folgt vor:

1. zu `http://<host>:<port>/system/console/status-slingsettings`
1. Überprüfen Sie den Wert unter **Sling ID**.

![](assets/chlimage_1-27.png)

Wenn die Sling-ID einer Veröffentlichungsinstanz der Sling-ID einer anderen Veröffentlichungsinstanz entspricht, gehen Sie wie folgt vor:

1. Halten Sie eine der Veröffentlichungsinstanzen mit übereinstimmender Sling-ID an.
1. Gehen Sie wie folgt im Verzeichnis „crx-quickstart/launchpad/felix“ vor:

   * Suchen und löschen Sie die Datei *sling.id.file*.

      * zum Beispiel auf einem Linux-System:
         `rm -i $(find . -type f -name sling.id.file)`

      * z. B. auf einem Windows-System:
         `use windows explorer and search for *sling.id.file*`

1. beginn der Veröffentlichungsinstanz

   * Beim Start wird der Instanz eine neue Sling-ID zugewiesen.

1. Vergewissern Sie sich, dass die **Sling-ID** nun eindeutig ist.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

## Vault Package Builder Factory {#vault-package-builder-factory}

Damit Updates ordnungsgemäß synchronisiert werden, muss der Vault-Paket-Builder zur Benutzersynchronisierung geändert werden:

* In jeder AEM-Veröffentlichungsinstanz:
* Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* suchen `Apache Sling Distribution Packaging - Vault Package Builder Factory`

   * `Builder name: socialpubsync-vlt`

* Wählen Sie das Bearbeitungssymbol aus.
* zwei hinzufügen `Package Node Filters`:

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* Richtlinienhandhabung:

   * Zum Überschreiben der vorhandenen Knoten „rep:policy“ mit neuen fügen Sie einen dritten Paketfilter hinzu:

      * `/home/users|+.*/rep:policy`
   * Um eine Richtlinienverteilung zu verhindern, stellen Sie Folgendes ein:

      * `Acl Handling:` `IGNORE`


![Vault Package Builder Factory](assets/vault-package-builder-factory.png)

## What Happens When ... {#what-happens-when}

### Selbstregistrierung oder Profilbearbeitung der Benutzer in der Veröffentlichungsumgebung {#user-self-registers-or-edits-profile-on-publish}

Per Design werden in der Veröffentlichungsumgebung erstellte Benutzer und Profile (Selbstregistrierung) nicht in der Autorenumgebung angezeigt.

When the topology is a [publish farm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) and user sync has been correctly configured, the *user *and *user profile* is synchronized across the publish farm using Sling distribution.

### Erstellung von Benutzern oder Benutzergruppen über die Sicherheitskonsole {#users-or-user-groups-are-created-using-security-console}

Per Design werden die in der Veröffentlichungsumgebung erstellten Benutzerdaten nicht in der Autorenumgebung angezeigt (und umgekehrt).

Wenn in der Veröffentlichungsumgebung neue Benutzer über die Konsole [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) hinzugefügt werden, werden die neuen Benutzer und ihre Gruppenmitgliedschaft im Rahmen der Benutzersynchronisierung ggf. mit anderen Veröffentlichungsinstanzen synchronisiert. Bei der Benutzersynchronisierung werden auch die über die Sicherheitskonsole erstellten Benutzergruppen synchronisiert.

## Fehlerbehebung {#troubleshooting}

### Offlineschalten der Benutzersynchronisierung {#how-to-take-user-sync-offline}

Zum Offlineschalten der Benutzersynchronisierung zwecks [Entfernung eines Herausgebers](#how-to-remove-a-publisher) oder [manueller Datensynchronisierung](#manually-syncing-users-and-user-groups) muss die Verteilungswarteschlange leer und störungsfrei sein.

So prüfen Sie den Status der Verteilungswarteschlange:

* In der Autoreninstanz:

   * using [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * look for entries in `/var/sling/distribution/packages`

         * die nach dem Muster `distrpackage_*` _* benannt sind.
   * Rufen Sie [Package Manager](/help/sites-administering/package-manager.md) auf.

      * Suchen Sie nach ausstehenden (noch nicht installierten) Paketen,

         * named with the pattern `socialpubsync-vlt*`
         * created by `communities-user-admin`


Wenn die Verteilungswarteschlange leer ist, deaktivieren Sie die Benutzersynchronisierung:

* In der Autoreninstanz:

   * *uncheck *the `Enabled` checkbox for [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

Um die Benutzersynchronisierung nach Durchführung der Aufgaben erneut zu aktivieren, gehen Sie wie folgt vor:

* In der Autoreninstanz:

   * check the `Enabled` checkbox for [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnose für Benutzersynchronisierung {#user-sync-diagnostics}

Die Diagnose für Benutzersynchronisierung ist ein Tool zur Überprüfung von Konfigurationen und zur Identifizierung etwaiger Probleme.

On author, simply navigate from the main console through **Tools, Operations, Diagnosis, User Sync Diagnostics.**

Die Ergebnisse werden einfach durch Aufrufen der Konsole „Diagnose für Benutzersynchronisierung“ angezeigt.

Folgendes wird angezeigt, wenn die Benutzersynchronisierung nicht aktiviert wurde:

![](assets/chlimage_1-28.png)

#### Ausführen der Diagnose für Herausgeber {#how-to-run-diagnostics-for-publishers}

When the diagnostic is run from the author environment, the pass/fail results will include an [INFO] section displaying the list of configured publish instances for confirmation.

In der Liste enthalten ist eine URL für jede Veröffentlichungsinstanz, die die Diagnose für diese Instanz ausführt. The url param `syncUser` is appended to the diagnostics URL with its value set to the *authorized sync user* created in [Step 2](#createauthuser).

**Hinweis**: Bevor Sie die URL aufrufen, muss der *autorisierte Synchronisierungsbenutzer* bereits bei dieser Veröffentlichungsinstanz angemeldet sein.

![](assets/chlimage_1-29.png)

### Falsch hinzugefügte Konfiguration {#configuration-improperly-added}

Wenn ein Fehler bei der Benutzersynchronisierung auftritt, ist dies im Allgemeinen darauf zurückzuführen, dass zusätzliche Konfigurationen *hinzugefügt* wurden. Instead, the *existing *default configuration should have been *edited*.

Im Folgende sehen Sie, wie die bearbeiteten Standardkonfigurationen in der Web-Konsole angezeigt werden sollten. Bei mehr als der einen Instanz sollte die hinzugefügte Konfiguration entfernt werden.

#### (Autor) Eine Konfiguration „Apache Sling Distribution Agent – Sync Agents Factory“{#author-one-apache-sling-distribution-agent-sync-agents-factory}

![](assets/chlimage_1-30.png)

#### (Autor) Eine Konfiguration „Apache Sling Distribution Transport Credentials – User Credentials based DistributionTransportSecretProvider“{#author-one-apache-sling-distribution-transport-credentials-user-credentials-based-distributiontransportsecretprovider}

![](assets/chlimage_1-31.png)

#### (Veröffentlichung) Eine Konfiguration „Apache Sling Distribution Agent – Queue Agents Factory“{#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![](assets/chlimage_1-32.png)

#### (Veröffentlichung) Eine Konfiguration „Adobe Social Sync – Diff Observer Factory“{#publish-one-adobe-social-sync-diff-observer-factory}

![](assets/chlimage_1-33.png)

#### (Autor) Eine Konfiguration „Apache Sling Distribution Trigger – Scheduled Triggers Factory“{#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![](assets/chlimage_1-34.png)

### Ausnahme bei Änderungsvorgang während Antwortverarbeitung {#modify-operation-exception-during-response-processing}

Wenn Folgendes im Protokoll steht:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

Then verify that the section [2. Create Authorized User](#createauthuser) was properly followed.

Dieser Abschnitt beschreibt, wie ein autorisierter Benutzer erstellt wird, wer in allen Veröffentlichungsinstanzen existiert und wie diese Benutzer in der OSGi-Konfiguration „Secret Provider“ der Autoreninstanz identifiziert werden. By default, the user is `admin`.

Der autorisierte Benutzer sollte als Mitglied der Benutzergruppe **`administrators`** aufgenommen werden. Außerdem sollten die Berechtigungen für diese Gruppe nicht geändert werden.

Für den autorisierten Benutzer sollten explizit die folgenden Rechte und Einschränkungen für alle Veröffentlichungsinstanzen gelten:

| **Pfad** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | */activities/* |
| /home/users | X | */activities/* |
| /home/groups | X | */activities/* |

As a member of the `administrators` group, the authorized user should have the following privileges on all publish instances:

| **Pfad** | **jcr:all** | **jcr:read** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Fehlgeschlagene Benutzergruppensynchronisierung {#user-group-sync-failed}

Wenn die Sling-ID zwischen zwei oder mehr Veröffentlichungsinstanzen übereinstimmt, schlägt die Benutzergruppesynchronisierung fehl.

Siehe Abschnitt [9. Eindeutige Sling-ID](#unique-sling-id)

### Manuelles Synchronisieren von Benutzern und Benutzergruppen {#manually-syncing-users-and-user-groups}

* Bei Herausgebern mit Benutzern und Benutzergruppen:

   * [Deaktivieren Sie ggf. die Benutzersynchronisierung.](#how-to-take-user-sync-offline)
   * [Erstellen eines Pakets](/help/sites-administering/package-manager.md#creating-a-new-package) von `/home`

      * Beim Bearbeiten des Pakets

         * Filters tab: Add Filter: Root path: `/home`
         * Advanced tab: AC Handling: `Overwrite`
   * [Exportieren Sie das Paket.](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* Bei anderen Veröffentlichungsinstanzen:

   * [Importieren Sie das Paket.](/help/sites-administering/package-manager.md#installing-packages)

To configure or enable user sync, go to step 1: [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Nichtverfügbarkeit von Herausgebern {#when-a-publisher-becomes-unavailable}

Wenn eine Veröffentlichungsinstanz nicht mehr verfügbar ist, sollte sie nicht entfernt werden, sofern sie zukünftig wieder online geschaltet wird. Änderungen für den Herausgeber werden in die Warteschlange gestellt und sobald dieser wieder online ist, werden die Änderungen verarbeitet.

Wenn die Instanz im Veröffentlichungsmodus nie wieder online ist, wenn sie dauerhaft offline ist, muss sie entfernt werden, da die Warteschlangenaufbauung zu einer merklichen Speichernutzung in der Autorendatei führt.

Wenn ein Herausgeber nicht mehr verfügbar ist, finden Sie im Autorprotokoll Ausnahmen wie die folgende:

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Entfernen von Herausgebern {#how-to-remove-a-publisher}

Um einen Herausgeber aus [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory) zu entfernen, muss die Verteilungswarteschlange leer und störungsfrei sein.

* In der Autoreninstanz:

   * [Schalten Sie die Benutzersynchronisierung offline.](#how-to-take-user-sync-offline)
   * Folgen Sie [Schritt 7](#apache-sling-distribution-agent-sync-agents-factory), um den Herausgeber aus beiden Serverlisten zu entfernen:

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * Erneutes Aktivieren der Benutzersynchronisierung

      * check the `Enabled` checkbox for [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)
