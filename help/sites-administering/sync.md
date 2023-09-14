---
title: Benutzersynchronisierung
description: Erfahren Sie mehr über die Benutzersynchronisierung in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 89f55598-e749-42b8-8f2a-496f45face66
feature: Security
source-git-commit: fd8bb7d3d9040e0a7a6b2f65751445f41aeab73e
workflow-type: tm+mt
source-wordcount: '2498'
ht-degree: 48%

---


# Benutzersynchronisierung{#user-synchronization}

## Einführung {#introduction}

Wenn die Bereitstellung eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm)müssen Mitglieder sich anmelden und ihre Daten in einem beliebigen Veröffentlichungsknoten anzeigen können.

In der Veröffentlichungsumgebung erstellte Benutzer und Benutzergruppen (Benutzerdaten) werden in der Autorenumgebung nicht benötigt.

Die meisten in der Autorenumgebung erstellten Benutzerdaten sollen in der Autorenumgebung verbleiben und nicht in die Veröffentlichungsinstanzen kopiert werden.

Registrierungen und Änderungen, die an einer Veröffentlichungsinstanz vorgenommen werden, müssen mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben.

Ab AEM 6.1 werden bei aktivierter Benutzersynchronisierung Benutzerdaten automatisch über die Veröffentlichungsinstanzen in der Farm synchronisiert und nicht in der Autoreninstanz erstellt.

## Sling Distribution {#sling-distribution}

Die Benutzerdaten werden zusammen mit den zugehörigen [Zugriffssteuerungslisten](/help/sites-administering/security.md) (Access Control Lists, ACLs) im [Oak-Core](/help/sites-deploying/platform.md), der Ebene unter Oak JCR, gespeichert und über die [Oak-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/jackrabbit/oak/api/package-tree.html) aufgerufen. Bei seltenen Aktualisierungen ist es sinnvoll, Benutzerdaten mit anderen Veröffentlichungsinstanzen mit [Sling Content Distribution](https://github.com/apache/sling-old-svn-mirror/blob/trunk/contrib/extensions/distribution/README.md) (Sling-Verteilung).

Eine Benutzersynchronisierung mit Sling Distribution weist im Vergleich zur herkömmlichen Replikation folgende Vorteile auf:

* *Benutzer*, *Benutzerprofile*, und *Benutzergruppen* , die in der Veröffentlichungsinstanz erstellt wurden, nicht in der Autoreninstanz erstellt werden

* Sling Distribution legt Eigenschaften in jcr-Ereignissen fest, sodass innerhalb veröffentlichungsseitiger Ereignis-Listener agiert werden kann, ohne unendliche Replikationsschleifen berücksichtigen zu müssen.
* Die Sling-Verteilung sendet nur Benutzerdaten an nicht ursprüngliche Veröffentlichungsinstanzen, wodurch unnötiger Traffic vermieden wird
* Im Benutzerknoten festgelegte [ACLs](/help/sites-administering/security.md) werden bei der Synchronisierung eingeschlossen.

>[!NOTE]
>
>Wenn Sitzungen erforderlich sind, wird empfohlen, entweder eine SSO-Lösung zu verwenden oder eine fixierbare Sitzung zu verwenden und Kunden dazu zu veranlassen, sich anzumelden, wenn sie zu einer anderen Veröffentlichungsinstanz wechseln.

>[!CAUTION]
>
>Die Synchronisierung der **Administratorgruppe** wird nicht unterstützt, auch nicht bei aktivierter Benutzersynchronisierung. Stattdessen wird ein Fehler beim &quot;Importieren des Vergleichs&quot;im Fehlerprotokoll protokolliert.
>
>Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, wird daher ein Benutzer zum **Administratoren** -Gruppe, muss die Änderung manuell in jeder Veröffentlichungsinstanz vorgenommen werden.

## Aktivieren der Benutzersynchronisierung {#enable-user-sync}

>[!NOTE]
>
>Standardmäßig ist für die Benutzersynchronisierung `disabled` festgelegt.
>
>Die Aktivierung der Benutzersynchronisierung beinhaltet die Änderung *vorhandener* OSGi-Konfigurationen.
>
>Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Die Benutzersynchronisierung beruht bei der Verwaltung der Benutzerdatenverteilung auf der Autorenumgebung, auch wenn die Benutzerdaten nicht in der Autorenumgebung erstellt werden. Ein Großteil, aber nicht alle der Konfigurationen finden in der Autorenumgebung statt und jeder Schritt gibt klar an, ob er in der Autoren- oder Veröffentlichungsumgebung ausgeführt werden soll.

Im Folgenden finden Sie eine Beschreibung der Schritte, die zum Aktivieren der Benutzersynchronisierung erforderlich sind, gefolgt von einem Abschnitt zur [Fehlerbehebung](#troubleshooting):

### Voraussetzungen {#prerequisites}

1. Wenn Benutzer und Benutzergruppen bereits in einer Veröffentlichungsinstanz erstellt wurden, wird empfohlen, [Manuelle Synchronisierung](#manually-syncing-users-and-user-groups) die Benutzerdaten an alle Veröffentlichungsinstanzen vor dem Konfigurieren und Aktivieren der Benutzersynchronisierung.

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

      * Wählen Sie die vorhandene Konfiguration aus, damit Sie sie zur Bearbeitung öffnen können (Bleistiftsymbol) Überprüfen `name`: **`socialpubsync`**

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

![Apache Sling Distribution Agent](assets/chlimage_1-20.png)

### 2. Erstellen autorisierter Benutzer {#createauthuser}

**Konfigurieren von Berechtigungen**

Der autorisierte Benutzer wird in Schritt 3 zum Konfigurieren der Sling-Distribution in der Autoreninstanz verwendet.

* **auf jeder Veröffentlichungsinstanz**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Sicherheitskonsole](/help/sites-administering/security.md) auf.

      * Beispiel: [https://localhost:4503/useradmin](https://localhost:4503/useradmin)

   * Benutzer erstellen

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
* Um einen ACL-Eintrag hinzuzufügen, wählen Sie die `+` button

   * **Prinzipal**: *nach dem für die Benutzersynchronisierung erstellten Benutzer suchen*
   * **Typ**: `Allow`
   * **Berechtigungen**: `jcr:all`
   * **Einschränkungen**: rep:glob: `*/activities/*`
   * Wählen Sie **OK** aus

* Wählen Sie **Alle speichern**

![ACL-Fenster hinzufügen](assets/chlimage_1-21.png)

Siehe auch

* [Verwalten von Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Fehlerbehebungsabschnitt [Ausnahme bei Änderungsvorgang während Antwortverarbeitung](#modify-operation-exception-during-response-processing).

### 3. Adobe Granite Distribution – Encrypted Password Transport Secret Provider {#adobegraniteencpasswrd}

**Konfigurieren von Berechtigungen**

Einmal autorisierter Benutzer Mitglied der **`administrators`** -Benutzergruppe auf allen Veröffentlichungsinstanzen erstellt wird, muss der autorisierte Benutzer in der Autoreninstanz als Benutzer identifiziert werden, der berechtigt ist, Benutzerdaten von der Autoren- zur Veröffentlichungsinstanz zu synchronisieren.

* **zum Autor**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`.
   * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration (Stiftsymbol) Überprüfen `property name`: **`socialpubsync-publishUser`**

   * Legen Sie Benutzername und Kennwort auf die [autorisierter Benutzer](#createauthuser) erstellt in Schritt 2 zur Veröffentlichung

      * Beispiel: `usersync-admin`

![Verschlüsselter Kennwortübertragungsanbieter](assets/chlimage_1-22.png)

### 4. Apache Sling Distribution Agent – Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Aktivieren der Benutzersynchronisierung**

* **auf jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Agent - Queue Agents Factory`.

      * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration (Stiftsymbol) Überprüfen `Name`: `socialpubsync-reverse`

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

   * **repeat** für jede Veröffentlichungsinstanz

![Queue Agents Factory](assets/chlimage_1-23.png)

### 5. Adobe Social Sync – Diff Observer Factory {#diffobserver}

**Aktivieren der Gruppensynchronisierung**

* **auf jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

   * Suchen Sie **`Adobe Social Sync - Diff Observer Factory`**.

      * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration aus (Stiftsymbol).

        Überprüfen Sie `agent name`: `socialpubsync-reverse`

      * Aktivieren Sie das Kontrollkästchen `Enabled`.
      * Wählen Sie `Save` aus.

![Diff Observer Factory](assets/screen-shot_2019-05-24at090809.png)

### 6. Apache Sling Distribution Trigger – Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Optional) Bearbeiten des Abrufintervalls**

Standardmäßig fragt der Autor alle 30 Sekunden nach Änderungen ab. So ändern Sie dieses Intervall:

* **zum Autor**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Trigger - Scheduled Triggers Factory`.

      * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration aus (Stiftsymbol).

         * Überprüfen Sie `Name`: `socialpubsync-scheduled-trigger`

      * Stellen Sie `Interval in Seconds` auf das gewünschte Intervall ein.
      * Wählen Sie `Save` aus.

![Scheduled Triggers Factory](assets/chlimage_1-24.png)

## Konfigurieren für mehrere Publishing-Instanzen {#configure-for-multiple-publish-instances}

Die Standardkonfiguration gilt für eine einzelne Veröffentlichungsinstanz. Da der Grund für die Aktivierung der Benutzersynchronisierung darin besteht, mehrere Veröffentlichungsinstanzen zu synchronisieren, z. B. für eine Veröffentlichungsfarm, müssen die zusätzlichen Veröffentlichungsinstanzen zur Synchronisierungsagenten-Factory hinzugefügt werden.

### 7. Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Hinzufügen von Veröffentlichungsinstanzen:**

* **zum Autor**

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

   * Suchen Sie `Apache Sling Distribution Agent - Sync Agents Factory`.

      * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration (Stiftsymbol) Überprüfen `Name`: `socialpubsync`

![Sync Agents Factory](assets/chlimage_1-25.png)

* **Exporter Endpoints**
Für jede Veröffentlichungsinstanz sollte ein Exporter-Endpunkt vorhanden sein. Wenn es beispielsweise 2 Veröffentlichungsinstanzen gibt, localhost:4503 und 4504, sollten zwei Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse`
   * `https://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse`

* **Importer Endpoints**
Für jede Veröffentlichungsinstanz sollte ein Importer-Endpunkt vorhanden sein. Wenn es beispielsweise 2 Veröffentlichungsinstanzen gibt, localhost:4503 und 4504, sollten zwei Einträge vorhanden sein:

   * `https://localhost:4503/libs/sling/distribution/services/importers/socialpubsync`
   * `https://localhost:4504/libs/sling/distribution/services/importers/socialpubsync`

* Wählen Sie `Save` aus.

### 8. AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

**(Optional) Synchronisieren zusätzlicher JCR-Knoten**

Wenn es benutzerdefinierte Daten gibt, die über mehrere Veröffentlichungsinstanzen hinweg synchronisiert werden sollen, gehen Sie folgendermaßen vor:

* **auf jeder Veröffentlichungsinstanz**:

   * Melden Sie sich mit Administratorrechten an.
   * Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf

      * Beispiel: `https://localhost:4503/system/console/configMgr`

   * Suchen Sie `AEM Communities User Sync Listener`.
   * zum Öffnen zur Bearbeitung wählen Sie die vorhandene Konfiguration (Stiftsymbol) Überprüfen `Name`: `socialpubsync-scheduled-trigger`

![AEM Communities User Sync Listener](assets/chlimage_1-26.png)

* **Knotentypen**
Dies ist die Liste der Knotentypen, die synchronisiert werden. Jeder andere Knotentyp als sling:Folder muss hier aufgeführt werden (sling:folder wird separat verarbeitet).
Standardliste zu synchronisierender Knotentypen:

   * rep:User
   * nt:unstructured
   * nt:resource

* **Ignorierende Eigenschaften**
Dies ist die Liste der Eigenschaften, die ignoriert werden, wenn Änderungen erkannt werden. Änderungen an diesen Eigenschaften werden möglicherweise als Nebeneffekt anderer Änderungen synchronisiert (da die Synchronisierung immer auf Knotenebene erfolgt), Änderungen an diesen Eigenschaften führen jedoch nicht allein zur Synchronisierung der Trigger.
Zu ignorierende Standardeigenschaft:

   * cq:lastModified

* **Ignorierbare Knoten**
Unterpfade, die bei der Synchronisierung ignoriert werden. Nichts unter diesen Unterpfaden wird zu einem beliebigen Zeitpunkt synchronisiert.
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

Wenn die Sling-ID für mehrere Veröffentlichungsinstanzen in einer Veröffentlichungsfarm identisch ist, werden Benutzergruppen nicht synchronisiert.

Um zu überprüfen, ob sich alle Sling-ID-Werte unterscheiden, gehen Sie in jeder Veröffentlichungsinstanz folgendermaßen vor:

1. Navigieren Sie zu `http://<host>:<port>/system/console/status-slingsettings`.
1. Überprüfen Sie den Wert unter **Sling ID**.

![Prüfen des Wertes der Sling-ID](assets/chlimage_1-27.png)

Wenn die Sling-ID einer Veröffentlichungsinstanz mit der Sling-ID einer anderen Veröffentlichungsinstanz übereinstimmt, dann:

1. Beenden Sie eine der Veröffentlichungsinstanzen mit einer übereinstimmenden Sling-ID.
1. Gehen Sie wie folgt im Verzeichnis „crx-quickstart/launchpad/felix“ vor:

   * Suchen und löschen Sie die Datei *sling.id.file*

      * Beispiel für ein Linux®-System:
        `rm -i $(find . -type f -name sling.id.file)`

      * Beispiel für ein Windows-System:
        `use windows explorer and search for *sling.id.file*`

1. Starten Sie die Veröffentlichungsinstanz

   * Beim Start wird ihm eine neue Sling-ID zugewiesen

1. Vergewissern Sie sich, dass die **Sling-ID** nun eindeutig ist.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

## Vault Package Builder Factory {#vault-package-builder-factory}

Damit Updates ordnungsgemäß synchronisiert werden, müssen Sie den Vault Package Builder für die Benutzersynchronisierung ändern:

* auf jeder AEM Veröffentlichungsinstanz
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

Standardmäßig werden in der Veröffentlichungsumgebung erstellte Benutzerdaten nicht in der Autorenumgebung und umgekehrt angezeigt.

Wenn die Variable [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) -Konsole wird verwendet, um neue Benutzer in der Veröffentlichungsumgebung hinzuzufügen. Bei der Benutzersynchronisierung werden die neuen Benutzer und deren Gruppenmitgliedschaft ggf. mit anderen Veröffentlichungsinstanzen synchronisiert. Die Benutzersynchronisierung synchronisiert auch Benutzergruppen, die über die Sicherheitskonsole erstellt wurden.

## Fehlerbehebung {#troubleshooting}

### So schalten Sie die Benutzersynchronisierung offline {#how-to-take-user-sync-offline}

So führen Sie die Benutzersynchronisierung offline durch: [Entfernen einer Veröffentlichungsinstanz](#how-to-remove-a-publish-instance) oder [Daten manuell synchronisieren](#manually-syncing-users-and-user-groups), muss die Verteilungswarteschlange leer und ruhig sein.

So prüfen Sie den Status der Verteilungswarteschlange:

* auf Autor:

   * Rufen Sie [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) auf.

      * Suchen Sie nach Einträgen in den Ordnerknoten `/var/sling/distribution/packages`,

         * die nach dem Muster `distrpackage_*` benannt sind.

   * Rufen Sie [Package Manager](/help/sites-administering/package-manager.md) auf

      * Suchen Sie nach ausstehenden (noch nicht installierten) Paketen,

         * die nach dem Muster `socialpubsync-vlt*` benannt sind,
         * die von `communities-user-admin` erstellt wurden.

Wenn die Verteilungswarteschlange leer ist, deaktivieren Sie die Benutzersynchronisierung:

* zum Autor

   * *Deaktivieren* Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

Wenn Aufgaben abgeschlossen sind, um die Benutzersynchronisierung erneut zu aktivieren:

* zum Autor

   * Aktivieren Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

### Diagnose für Benutzersynchronisierung {#user-sync-diagnostics}

Die Diagnose für Benutzersynchronisierung ist ein Tool zur Überprüfung von Konfigurationen und zur Identifizierung etwaiger Probleme.

Navigieren Sie im Autorenmodus einfach von der Hauptkonsole durch **Tools, Vorgänge, Diagnose, Diagnose der Benutzersynchronisierung.**

Wenn Sie einfach in die Konsole &quot;Diagnose für Benutzersynchronisierung&quot;wechseln, werden die Ergebnisse angezeigt.

Folgendes wird angezeigt, wenn die Benutzersynchronisierung nicht aktiviert wurde:

![Warnung, dass die Diagnose der Benutzersynchronisierung nicht aktiviert ist](assets/chlimage_1-28.png)

#### Ausführen der Diagnose für Veröffentlichungsinstanzen {#how-to-run-diagnostics-for-publish-instances}

Wenn die Diagnose in der Autorenumgebung ausgeführt wird, enthalten die Ergebnisse für die Übermittlung/das Fehlschlagen eine [INFO] -Abschnitt mit der Liste der konfigurierten Veröffentlichungsinstanzen zur Bestätigung.

In der Liste ist eine URL für jede Veröffentlichungsinstanz enthalten, die die Diagnose für diese Instanz ausführt. Der URL-Parameter `syncUser` ist an die Diagnose-URL angehängt. Der Wert lautet dabei auf den *autorisierten Sychronisierungsbenutzer*, der in [Schritt 2](#createauthuser) erstellt wurde.

**Hinweis**: vor dem Start der URL wird die *autorisierter Synchronisierungsbenutzer* muss bereits bei dieser Veröffentlichungsinstanz angemeldet sein.

![Diagnose für Publishing-Instanzen](assets/chlimage_1-29.png)

### Fehlerhaft hinzugefügte Konfiguration {#configuration-improperly-added}

Wenn die Benutzersynchronisierung nicht funktioniert, besteht das häufigste Problem darin, dass zusätzliche Konfigurationen *hinzugefügt* wurden. Stattdessen sollte die *vorhandene* Standardkonfiguration *bearbeitet* werden.

Im Folgenden sehen Sie, wie die bearbeiteten Standardkonfigurationen in der Web-Konsole angezeigt werden sollten. Bei mehr als der einen Instanz sollte die hinzugefügte Konfiguration entfernt werden.

#### (Autor) Ein Apache Sling Distribution Agent - Sync Agents Factory {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-30.png)

#### (Autor) Eine Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider {#author-one-apache-sling-distribution-transport-credentials-user-credentials-based-distributiontransportsecretprovider}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-31.png)

#### (Veröffentlichen) Ein Apache Sling Distribution Agent - Queue Agents Factory {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-32.png)

#### (Publish) One Adobe Social Sync - Diff Observer Factory {#publish-one-adobe-social-sync-diff-observer-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-33.png)

#### (Autor) Ein Apache Sling Distribution Trigger - Scheduled Trigger Factory {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![Ansicht für bearbeitete Standardkonfigurationen in der Web-Konsole](assets/chlimage_1-34.png)

### Ausnahme bei Änderungsvorgang während der Antwortverarbeitung {#modify-operation-exception-during-response-processing}

Wenn Folgendes im Protokoll steht:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

prüfen Sie, ob Abschnitt [2. Erstellen autorisierter Benutzer](#createauthuser) ordnungsgemäß befolgt wurde.

In diesem Abschnitt wird beschrieben, wie Sie einen autorisierten Benutzer erstellen, der in allen Veröffentlichungsinstanzen vorhanden ist, und diese Benutzer in der OSGi-Konfiguration &quot;Geheimer Anbieter&quot;in der Autoreninstanz identifizieren. Standardmäßig ist `admin` der Benutzer.

Der autorisierte Benutzer sollte als Mitglied der Benutzergruppe **`administrators`** aufgenommen werden. Außerdem sollten die Berechtigungen für diese Gruppe nicht geändert werden.

Der autorisierte Benutzer sollte explizit über die folgenden Berechtigungen und Einschränkungen für alle Veröffentlichungsinstanzen verfügen:

| **Pfad** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | &#42;/activities/&#42; |
| /home/users | X | &#42;/activities/&#42; |
| /home/groups | X | &#42;/activities/&#42; |

Als Mitglied der `administrators` -Gruppe, sollte der autorisierte Benutzer in allen Veröffentlichungsinstanzen über die folgenden Berechtigungen verfügen:

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

* auf Veröffentlichungsinstanzen, auf denen Benutzer und Benutzergruppen vorhanden sind:

   * [Deaktivieren Sie ggf. die Benutzersynchronisierung.](#how-to-take-user-sync-offline)
   * [Erstellen Sie ein Paket](/help/sites-administering/package-manager.md#creating-a-new-package) von `/home`.

      * Beim Bearbeiten des Pakets

         * Registerkarte „Filter“: „Filter hinzufügen“: > „Stammverzeichnis“: `/home`
         * Registerkarte „Erweitert“ > „AC-Handhabung“: `Overwrite`

   * [Exportieren Sie das Paket.](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)

* auf anderen Veröffentlichungsinstanzen:

   * [Importieren Sie das Paket.](/help/sites-administering/package-manager.md#installing-packages)

Zum Konfigurieren oder Aktivieren der Benutzersynchronisierung gehen Sie zu Schritt 1: [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).

### Bei Nichtverfügbarkeit einer Veröffentlichungsinstanz {#when-a-publish-instance-becomes-unavailable}

Wenn eine Veröffentlichungsinstanz nicht mehr verfügbar ist, sollte sie nicht entfernt werden, wenn sie in Zukunft wieder online ist. Änderungen werden für die Veröffentlichungsinstanz in die Warteschlange gestellt und wenn sie wieder online sind, werden die Änderungen verarbeitet.

Wenn die Veröffentlichungsinstanz nie wieder online geht und dauerhaft offline ist, muss sie entfernt werden, da die Warteschlangen-Erstellung zu einer spürbaren Festplattenspeicherplatznutzung in der Autorenumgebung führt.

Wenn eine Veröffentlichungsinstanz deaktiviert ist, weist das Autorprotokoll ähnliche Ausnahmen auf:

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Entfernen einer Veröffentlichungsinstanz {#how-to-remove-a-publish-instance}

So entfernen Sie eine Veröffentlichungsinstanz aus dem [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory), muss die Verteilungswarteschlange leer und ruhig sein.

* auf Autor:

   * [Schalten Sie die Benutzersynchronisierung offline.](#how-to-take-user-sync-offline)
   * folgen [Schritt 7](#apache-sling-distribution-agent-sync-agents-factory) , um die Veröffentlichungsinstanz aus beiden Serverlisten zu entfernen:

      * `Exporter Endpoints`
      * `Importer Endpoints`

   * Erneutes Aktivieren der Benutzersynchronisierung

      * Aktivieren Sie das Kontrollkästchen `Enabled` für [Apache Sling Distribution Agent – Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory).
