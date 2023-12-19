---
title: Konfigurieren von AEM Assets mit Brand Portal
description: Erfahren Sie, wie AEM Assets mit Brand Portal integriert wird, um Assets und Sammlungen in Brand Portal zu veröffentlichen.
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
docset: aem65
feature: Brand Portal
role: Admin
exl-id: ae33181c-9eec-421c-be55-4bd019de40b8
hide: true
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 99%

---


# Konfigurieren von AEM Assets mit Brand Portal {#configure-integration-65}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Im Adobe Experience Manager Assets Brand Portal können Sie genehmigte Marken-Assets aus Adobe Experience Manager Assets in Brand Portal veröffentlichen und an die Brand Portal-Benutzenden verteilen.

AEM Assets wird über die Adobe Developer Console mit Brand Portal konfiguriert. Dadurch wird ein Adobe Identity Management Services (IMS)-Token zur Autorisierung Ihres Brand Portal-Mandanten abgerufen.

>[!NOTE]
>
>Die Konfiguration von AEM Assets mit Brand Portal über Adobe Developer Console wird unter AEM 6.5.4.0 und höher unterstützt.
>
>Zuvor wurde Brand Portal über das alte OAuth-Gateway konfiguriert. Das Gateway ruft mithilfe des JSON Web Token (JWT)-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab.
>
>Die Konfiguration über das alte OAuth-Protokoll wird ab dem 6. April 2020 nicht mehr unterstützt, sondern erfolgt nun über die Adobe Developer Console.

>[!TIP]
>
>***Nur für Bestandskunden***
>
>Adobe empfiehlt, weiterhin die bestehende OAuth-Gateway-Konfiguration zu verwenden. Wenn Probleme mit der alten OAuth-Gateway-Konfiguration auftreten, löschen Sie die vorhandene Konfiguration und erstellen Sie eine Konfiguration über die Adobe Developer Console.

In diesem Hilfeartikel werden die folgenden beiden Anwendungsfälle beschrieben:

* [Neue Konfiguration](#configure-new-integration-65): Neue Brand Portal-Benutzende, die ihre AEM Assets-Autoreninstanz mit Brand Portal konfigurieren möchten, können die Konfiguration über die Adobe Developer Console erstellen.
* [Upgrade der Konfiguration](#upgrade-integration-65): Bestehende Brand Portal-Benutzende, die eine Konfiguration auf dem alten OAuth-Gateway haben, löschen die vorhandene Konfiguration und erstellen eine neue Konfiguration über die Adobe Developer Console.

Benutzer dieser Hilfe sollten mit den folgenden Technologien vertraut sein:

* Installieren, Konfigurieren und Verwalten von Adobe Experience Manager- und AEM-Paketen.

* Verwenden von Linux®- und Microsoft® Windows-Betriebssystemen.

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine betriebsbereite AEM Assets-Autoreninstanz mit dem neuesten Service Pack
* Eine Brand Portal-Mandanten-URL
* Ein Anwender mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten

[Herunterladen und Installieren von AEM 6.5](#aemquickstart)

[Herunterladen und Installieren des aktuellen AEM Service Pack](#servicepack)

### Herunterladen und Installieren von AEM 6.5 {#aemquickstart}

Es wird empfohlen, AEM 6.5 zu verwenden, um eine AEM Autoreninstanz einzurichten. Wenn Sie AEM nicht eingerichtet haben, laden Sie es von den folgenden Speicherorten herunter:

* Wenn Sie bereits Kundin oder Kunde von AEM sind, laden Sie AEM 6.5 von der [Adobe-Lizenzierungs-Website](https://licensing.adobe.com) herunter.

* Wenn Sie ein Adobe-Partner sind, fordern Sie AEM 6.5 über das [Adobe Partner Training-Programm](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) an.

Anweisungen zum Einrichten einer AEM-Autoreninstanz finden Sie nach dem Herunterladen von AEM unter [Bereitstellen und Verwalten](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de#default-local-install).

### Herunterladen und Installieren des neuesten AEM Service Packs {#servicepack}

Detaillierte Anweisungen finden Sie in den aktuellen [Versionshinweisen zu AEM 6.5 Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de).

**Wenden Sie sich an den Adobe-Support**, wenn Sie das neueste AEM-Paket oder Service Pack nicht finden können.

## Erstellen einer Konfiguration {#configure-new-integration-65}

Für die Konfiguration von AEM Assets mit Brand Portal sind Konfigurationen sowohl in der AEM Assets-Autoreninstanz als auch in Adobe Developer Console erforderlich.

1. Erstellen Sie in AEM Assets ein IMS-Konto und erzeugen Sie ein öffentliches Zertifikat (einen öffentlichen Schlüssel).
1. Erstellen Sie in der Adobe Developer Console ein Projekt für Ihren Brand Portal-Mandanten (Unternehmen).
1. Konfigurieren Sie unter dem Projekt eine API mithilfe des öffentlichen Schlüssels, um eine JWT-Verbindung (Dienstkonto) zu erstellen.
1. Rufen Sie die Anmeldedaten für das Dienstkonto und die JWT-Payload-Informationen ab.
1. Konfigurieren Sie in AEM Assets das IMS-Konto mit den Anmeldedaten für das Service-Konto und die JWT-Payload.
1. Konfigurieren Sie in AEM Assets den Brand Portal-Cloud Service mit dem IMS-Konto und dem Brand Portal-Endpunkt (Organisations-URL).
1. Testen Sie die Konfiguration, indem Sie ein Asset aus AEM Assets in Brand Portal veröffentlichen.

>[!NOTE]
>
>Eine AEM Assets-Autoreninstanz darf nur mit einem Brand Portal-Mandanten konfiguriert werden.

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, wenn Sie AEM Assets zum ersten Mal mit Brand Portal konfigurieren:

1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen einer Verbindung für ein Service-Konto (JWT)](#createnewintegration)
1. [Konfigurieren eines IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-integration)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihre AEM Assets-Autoreninstanz beim Brand Portal-Mandanten.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Konfigurieren eines IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Der öffentliche Schlüssel (Zertifikat) authentifiziert Ihr Profil in der Adobe Developer Console.

1. Melden Sie sich bei der AEM Assets-Autorenistanz an. Die Standardeinstellung ist `http://localhost:4502/aem/start.html`.

1. Navigieren Sie im Bedienfeld **Tools** ![Tools](assets/do-not-localize/tools.png) zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.

1. Klicken Sie auf der Seite für Adobe IMS-Konfigurationen auf **[!UICONTROL Erstellen]**. Sie werden zur Seite für die **[!UICONTROL Konfiguration des technischen Adobe IMS-Kontos]** weitergeleitet. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.

1. Wählen Sie **[!UICONTROL Adobe Brand Portal]** in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** aus.

1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie einen **Alias** für den öffentlichen Schlüssel an. Der Alias dient als der Name des öffentlichen Schlüssels.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Klicken Sie auf **[!UICONTROL OK]**, um den öffentlichen Schlüssel zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die Public-Key-Datei (.crt) auf Ihrem Computer.

   Der öffentliche Schlüssel wird später zum Konfigurieren der API für Ihren Brand Portal-Mandanten und zum Generieren von Anmeldeinformationen für Service-Konten in der Adobe Developer Console verwendet.

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Auf der Registerkarte **Konto** wird das Adobe IMS-Konto erstellt. Dafür werden die Anmeldeinformationen für Service-Konten benötigt, die in der Adobe Developer Console generiert werden. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie in der Adobe Developer Console eine Service-Kontoverbindung (JWT)](#createnewintegration), um die Anmeldeinformationen und die JWT-Payload für die Konfiguration des IMS-Kontos abzurufen.

### Erstellen der Service-Kontoverbindung (JWT) {#createnewintegration}

In der Adobe Developer Console werden Projekte und APIs auf Brand Portal-Mandantenebene (Organisationsebene) konfiguriert. Beim Konfigurieren einer API wird eine Service-Konto-Verbindung (JWT-Verbindung) hergestellt. Es gibt zwei Methoden zum Konfigurieren der API: Generieren eines Schlüsselpaars (privater und öffentlicher Schlüssel) oder Hochladen eines öffentlichen Schlüssels. Um AEM Assets mit Brand Portal zu konfigurieren, müssen Sie einen öffentlichen Schlüssel (Zertifikat) in AEM Assets generieren und Anmeldedaten in der Adobe Developer Console erstellen, indem Sie den öffentlichen Schlüssel hochladen. Diese Anmeldedaten werden zum Konfigurieren des IMS-Kontos in AEM Assets benötigt. Sobald das IMS-Konto konfiguriert ist, können Sie den Brand Portal-Cloud Service in AEM Assets konfigurieren.

Gehen Sie wie folgt vor, um die Anmeldeinformationen für das Service-Konto und die JWT-Payload zu erstellen:

1. Melden Sie sich bei der Adobe Developer Console mit Systemadministratorrechten für die IMS-Organisation (den Brand Portal-Mandanten) an. Die Standard-URL lautet [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die richtige IMS-Organisation (den Brand Portal-Mandanten) aus der Dropdown-Liste (Organisation) oben rechts ausgewählt haben.

1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]**. Für Ihre Organisation wird ein leeres Projekt mit einem systemgenerierten Namen erstellt.

   Klicken Sie auf **[!UICONTROL Projekt bearbeiten]**, um den **[!UICONTROL Projekttitel]** und die **[!UICONTROL Projektbeschreibung]** zu aktualisieren, und klicken Sie auf **[!UICONTROL Speichern]**.

1. Klicken Sie auf der Registerkarte mit der **[!UICONTROL Projektübersicht]** auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie im Fenster **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL AEM Brand Portal]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   Stellen Sie sicher, dass Sie Zugriff auf den AEM Brand Portal-Service haben.

1. Klicken Sie im Fenster **[!UICONTROL API konfigurieren]** auf **[!UICONTROL Öffentlichen Schlüssel hochladen]**. Klicken Sie dann auf **[!UICONTROL Datei auswählen]** und laden Sie den öffentlichen Schlüssel (.crt-Datei) hoch, den Sie im Abschnitt zum [Abrufen des öffentlichen Zertifikats](#public-certificate) heruntergeladen haben.

   Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Öffentlichen Schlüssel hochladen](assets/service-account3.png)

1. Überprüfen Sie den öffentlichen Schlüssel und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL Assets Brand Portal]** als Standardproduktprofil aus und klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Profil auswählen](assets/service-account4.png)

1. Sobald die API konfiguriert ist, werden Sie zur Seite mit der API-Übersicht weitergeleitet. Klicken Sie in der linken Navigation unter **[!UICONTROL Anmeldeinformationen]** auf die Option **[!UICONTROL Service-Konto (JWT)]**. 

   >[!NOTE]
   >
   >Sie können die Anmeldeinformationen einsehen und weitere Aktionen durchführen, beispielsweise JWT-Token generieren, Anmeldeinformationen kopieren und Client-Geheimnisse abrufen.

1. Kopieren Sie auf der Registerkarte **[!UICONTROL Client-Anmeldedaten]** die **[!UICONTROL Client-ID]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie das **[!UICONTROL Client-Geheimnis]**.

   ![Service-Konto-Anmeldedaten](assets/service-account5.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT generieren]** und kopieren Sie die Informationen zur **[!UICONTROL JWT-Payload]**.

Sie können jetzt die Client-ID (API-Schlüssel), das Client-Geheimnis und die JWT-Payload verwenden, um das [IMS-Konto in AEM Assets zu konfigurieren](#create-ims-account-configuration).

<!--
### Create Adobe I/O integration {#createnewintegration}

Adobe I/O integration generates API Key, Client Secret, and Payload (JWT) which is required in setting up the IMS Account configurations.

1. Login to Adobe I/O Console with system administrator privileges on the IMS organization of the Brand Portal tenant.

   Default URL: [https://console.adobe.io/](https://console.adobe.io/) 

1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information that is used to create IMS account configuration.
-->

### Konfigurieren des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte bereits ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen einer Service-Kontoverbindung (JWT)](#createnewintegration)

So konfigurieren Sie das IMS-Konto:

1. Öffnen Sie die IMS-Konfiguration und navigieren Sie zur Registerkarte **[!UICONTROL Konto]**. Sie haben die Seite offen gelassen, während Sie das [öffentliche Zertifikat abgerufen](#public-certificate) haben.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Im **[!UICONTROL Autorisierungsserver]** Geben Sie die URL an: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).

   Fügen Sie die Client-ID im Feld **[!UICONTROL API-Schlüssel]** sowie das **[!UICONTROL Client-Geheimnis]** und die **[!UICONTROL Payload]** (JWT-Payload) ein, die Sie beim [Erstellen der JWT-Verbindung (Service-Konto)](#createnewintegration) kopiert haben.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Das IMS-Konto ist konfiguriert.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)

1. Wählen Sie die IMS-Kontokonfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**.

   Klicken Sie im Dialogfeld auf **[!UICONTROL Prüfen]**. Bei erfolgreicher Konfiguration wird eine Meldung angezeigt, dass das *Token erfolgreich abgerufen* wurde.

   ![Bestätigungsdialogfeld „Fehlerfreie Konfiguration“](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Löschen Sie sie und erstellen Sie eine weitere gültige Konfiguration.

### Konfigurieren des Brand Portal-Cloud-Service {#configure-the-cloud-service}

1. Melden Sie sich bei der AEM Assets-Autorenistanz an.

1. Navigieren Sie im **Tool** ![Tools](assets/do-not-localize/tools.png)-Bedienfeld zu **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klicken Sie auf der Seite mit den Brand Portal-Konfigurationen auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die IMS-Konfiguration aus, die Sie beim [Konfigurieren des IMS-Kontos](#create-ims-account-configuration) erstellt haben.

   Geben Sie im Feld **[!UICONTROL Dienst-URL]** Ihre Brand Portal-Mandanten-URL (Organisations-URL) ein.

   ![Fenster „Brand Portal-Konfiguration“](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt.

   Ihre AEM Assets-Autoreninstanz ist nun mit dem Brand Portal-Mandanten konfiguriert.

### Testen und Validieren der Konfiguration {#test-integration}

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Gehen Sie vom Bedienfeld **Tools** ![Tools](assets/do-not-localize/tools.png) zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**.

   ![Das Bedienfeld „Tools“](assets/test-integration1.png)

1. Klicken Sie auf der Seite „Replikation“ auf **[!UICONTROL Agenten für Autor]**.

   ![Replikationsseite](assets/test-integration2.png)

   Sie sehen die vier für Ihren Brand Portal-Mandanten erstellten Replikationsagenten.

   Suchen Sie die Replikationsagenten Ihres Brand Portal-Mandanten und klicken Sie auf die Replikationsagenten-URL.

   ![Konfiguration der Asset-Replikation](assets/test-integration3.png)

   >[!NOTE]
   >
   >Die Replikationsagenten arbeiten parallel und teilen die Auftragsverteilung gleichmäßig auf, sodass die Veröffentlichungsgeschwindigkeit im Vergleich zur ursprünglichen Geschwindigkeit vervierfacht wird. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.

1. Um die Verbindung zwischen AEM Assets und Brand Portal zu überprüfen, klicken Sie auf das Symbol **[!UICONTROL Verbindung testen]**.

   ![Überprüfen der Asset-Replikationseinstellungen](assets/test-integration4.png)

   Ihnen wird eine Meldung angezeigt, dass Ihr *Testpaket erfolgreich bereitgestellt wurde*.

   ![Ausgabe der Testbestätigung](assets/test-integration5.png)

1. Überprüfen Sie die Testergebnisse für alle vier Replikationsagenten.


   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation der Assets (in der Warteschlaife) fehlschlägt.
   >
   >Stellen Sie sicher, dass alle vier Replikationsagenten so konfiguriert sind, dass Zeitüberschreitungsfehler vermieden werden. Siehe [Beheben von Problemen beim parallelen Veröffentlichen in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html?lang=de#connection-timeout).
   >
   >Ändern Sie keine automatisch generierten Einstellungen.

Sie haben nun die folgenden Möglichkeiten:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](../assets/brand-portal-publish-assets.md)
* [Veröffentlichen von Assets von Brand Portal in AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=de) – Abruf von Assets in Brand Portal
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](../assets/brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](../assets/brand-portal-publish-collection.md)
* [Veröffentlichen von Vorgaben, Schemata und Facetten in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html?lang=de)
* [Veröffentlichen von Tags in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html?lang=de)

Weitere Informationen finden Sie in der [Brand Portal-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de).


## Upgrade der Konfiguration {#upgrade-integration-65}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um Ihre vorhandenen Konfigurationen auf der Adobe Developer Console zu aktualisieren:

1. [Überprüfen von laufenden Aufträgen](#verify-jobs)
1. [Löschen von vorhandenen Konfigurationen](#delete-existing-configuration)
1. [Erstellen einer Konfiguration](#configure-new-integration-65)

### Überprüfen von laufenden Aufträgen {#verify-jobs}

Stellen Sie sicher, dass in Ihrer AEM Assets-Autoreninstanz kein Veröffentlichungsvorgang ausgeführt wird, bevor Sie Änderungen vornehmen. Dazu können Sie den Status aktiver Aufträge für alle vier Replikationsagenten überprüfen und sicherstellen, dass sich die Warteschlangen im Leerlauf befinden.

1. Melden Sie sich bei der AEM Assets-Autorenistanz an.

1. Gehen Sie vom Bedienfeld **Tools** ![Tools](assets/do-not-localize/tools.png) zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation der Bereitstellung]**.

1. Klicken Sie auf der Seite „Replikation“ auf **[!UICONTROL Agenten für Autor]**.

   ![Replikationsagenten für Assets](assets/test-integration2.png)

1. Suchen Sie die Replikationsagenten Ihres Brand Portal-Mandanten.

   Stellen Sie sicher, dass für alle Replikationsagenten die **Warteschlange im Leerlauf ist** und kein Veröffentlichungsvorgang aktiv ist.

   ![Einstellungen für Replikationswarteschlangen](assets/test-integration3.png)

### Löschen von vorhandenen Konfigurationen {#delete-existing-configuration}

Arbeiten Sie beim Löschen der vorhandenen Konfigurationen die folgende Checkliste ab:

* Alle vier Replikationsagenten löschen
* Brand Portal Cloud Service löschen
* Mac-Benutzende löschen

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an und öffnen Sie CRX Lite als Admin. Die Standardeinstellung ist `http://localhost:4502/crx/de/index.jsp`.

1. Navigieren Sie zu `/etc/replications/agents.author` und löschen Sie alle vier Replikationsagenten Ihres Brand Portal-Mandanten.

   ![Replikationsagent in CRXDE](assets/delete-replication-agent.png)

1. Navigieren Sie zu `/etc/cloudservices/mediaportal` und löschen Sie die Cloud Service-Konfiguration von Brand Portal.

   ![Details zum Replikationsagenten in CRXDE](assets/delete-cloud-service.png)

1. Navigieren Sie zu `/home/users/mac` und löschen Sie die **Mac-Benutzenden** Ihres Brand Portal-Mandanten.

   ![Weitere Details zum Replikationsagenten in CRXDE](assets/delete-mac-user.png)


Sie können nun über die Adobe Developer Console eine Konfiguration in Ihrer AEM 6.5-Autoreninstanz [erstellen](#configure-new-integration-65).



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
