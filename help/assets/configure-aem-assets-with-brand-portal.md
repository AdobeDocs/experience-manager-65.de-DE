---
title: Konfigurieren von AEM Assets mit Brand Portal
seo-title: Konfigurieren von AEM Assets mit Brand Portal
description: Erfahren Sie, wie Sie AEM Assets mit dem Markenportal für das Veröffentlichen von Assets und Sammlungen im Markenportal konfigurieren.
seo-description: Erfahren Sie, wie Sie AEM Assets mit dem Markenportal für das Veröffentlichen von Assets und Sammlungen im Markenportal konfigurieren.
uuid: b95c046e-9988-444c-b50e-ff5ec8cafe14
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: dca5a2ac-1fc8-4251-b073-730fd6f49b1c
docset: aem65
translation-type: tm+mt
source-git-commit: 9a27aabef07d5b5104c08c414138fbb22e284a68
workflow-type: tm+mt
source-wordcount: '2074'
ht-degree: 26%

---


# Konfigurieren von AEM Assets mit Brand Portal {#configure-integration-65}

Adobe Experience Manager (AEM)-Assets werden über die Adobe Developer Console mit dem Markenportal konfiguriert, wodurch ein IMS-Token zur Autorisierung Ihres Markenportal-Mandanten abgerufen wird.

>[!NOTE]
>
>Die Konfiguration von AEM Assets mit dem Markenportal über die Adobe Developer Console wird auf AEM 6.5.4.0 und höher unterstützt.
>
>Zuvor wurde Brand Portal über das alte OAuth-Gateway in der klassischen Benutzeroberfläche konfiguriert. Das Gateway ruft mithilfe des JWT-Token-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab.
>
>Die Konfiguration über Legacy-OAuth wird ab dem 6. April 2020 nicht mehr unterstützt. Die Konfiguration erfolgt nun über die Adobe Developer Console.


>[!TIP]
>
>***Nur für Bestandskunden***
>
>Es wird empfohlen, weiterhin die vorhandene alte OAuth-Gateway-Konfiguration zu verwenden. Falls Probleme mit der alten OAuth Gateway-Konfiguration auftreten, löschen Sie die vorhandene Konfiguration und erstellen Sie eine neue Konfiguration über Adobe Developer Console.



In dieser Hilfe werden die folgenden zwei Anwendungsfälle beschrieben:
* [Neue Konfiguration](#configure-new-integration-65): Wenn Sie ein neuer Markenportal-Benutzer sind und Ihre AEM Assets-Autoreninstanz mit dem Markenportal konfigurieren möchten, können Sie eine neue Konfiguration in der Adobe Developer Console erstellen.
* [Upgrade-Konfiguration](#upgrade-integration-65): Wenn Sie ein bestehender Brand Portal-Benutzer mit Ihrer AEM Assets-Autoreninstanz sind, die mit Brand Portal auf dem alten OAuth Gateway konfiguriert wurde, sollten Sie die vorhandenen Konfigurationen löschen und eine neue Konfiguration in der Adobe Developer Console erstellen.

Benutzer dieser Hilfe sollten mit den folgenden Technologien vertraut sein:

* Installieren, Konfigurieren und Verwalten von Adobe Experience Manager- und AEM-Paketen

* Verwenden von Linux- und Microsoft Windows-Betriebssystemen

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine betriebsbereite AEM Assets-Autoreninstanz mit dem neuesten Service Pack.
* Brand Portal-Mandanten-URL
* Ein Benutzer mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten


[Herunterladen und Installieren von AEM 6.5](#aemquickstart)

[Herunterladen und Installieren des neuesten AEM Service Packs](#servicepack)

### Herunterladen und Installieren von AEM 6.5 {#aemquickstart}

Es wird empfohlen, AEM 6.5 zum Einrichten einer AEM-Autoreninstanz zu verwenden. Wenn Sie AEM nicht eingerichtet haben, laden Sie es von den folgenden Speicherorten herunter:

* If you are an existing AEM customer, download AEM 6.5 from [Adobe Licensing website](http://licensing.adobe.com).

* If you are an Adobe partner, use [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) to request AEM 6.5.

Anweisungen zum Einrichten einer AEM- Autoreninstanz finden Sie nach dem Herunterladen von AEM unter [Bereitstellen und Verwalten](https://helpx.adobe.com/de/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Herunterladen und Installieren des neuesten AEM Service Packs{#servicepack}

Ausführliche Anweisungen finden Sie unter

* [Versionshinweise zum AEM 6.5 Service Pack](https://helpx.adobe.com/de/experience-manager/6-5/release-notes/sp-release-notes.html)

**Wenden Sie sich an den Kundendienst** , wenn Sie das neueste AEM-Paket oder Service Pack nicht finden können.

## Erstellen der Konfiguration {#configure-new-integration-65}

Zum Konfigurieren von AEM Assets mit dem Markenportal sind Konfigurationen sowohl in der Autoreninstanz von AEM Assets als auch in der Adobe Developer Console erforderlich.

1. Erstellen Sie in der Autoreninstanz von AEM Assets ein IMS-Konto und generieren Sie ein öffentliches Zertifikat (öffentlicher Schlüssel).

1. Erstellen Sie in Adobe Developer Console ein Projekt für Ihren Markenportal-Mandanten (Unternehmen).

1. Konfigurieren Sie unter dem Projekt eine API mithilfe des öffentlichen Schlüssels, um eine JWT-Verbindung (Dienstkonto) zu erstellen.

1. Rufen Sie die Anmeldeinformationen für das Dienstkonto und die JWT-Nutzdaten ab.

1. Konfigurieren Sie in der Autoreninstanz von AEM Assets das IMS-Konto unter Verwendung der Dienstkontoberechtigungen und der JWT-Payload.

1. Konfigurieren Sie in der Autoreninstanz von AEM Assets den Markenportal-Cloud-Dienst mit dem IMS-Konto und dem Markenportal-Endpunkt (Organisations-URL).

1. Testen Sie die Konfiguration, indem Sie ein Asset aus der Autoreninstanz von AEM Assets in Brand Portal veröffentlichen.


>[!NOTE]
>
>Ein Markenportal-Mandant darf nur mit einer AEM Assets-Autoreninstanz konfiguriert werden.
>
>Konfigurieren Sie keinen Markenportal-Mandanten mit mehreren AEM Assets-Autoreninstanzen.



Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge durch, wenn Sie AEM Assets mit Markenportal zum ersten Mal konfigurieren:
1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Verbindung zum Erstellen eines Dienstkontos (JWT)](#createnewintegration)
1. [IMS-Konto konfigurieren](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-integration)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Brand Portal-Mandanten mit der Autoreninstanz von AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [IMS-Konto konfigurieren](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Mit dem öffentlichen Zertifikat können Sie Ihr Profil in der Adobe Developer Console authentifizieren.

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an. Die Standardeinstellung ist
   `http:// localhost:4502/aem/start.html`
1. From the **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![Benutzeroberfläche der Adobe IMS-Kontokonfiguration](assets/ims-config1.png)

1. Klicken Sie auf der Seite &quot;Adobe IMS-Konfigurationen&quot;auf **[!UICONTROL Erstellen]**.

1. Sie werden zur Seite &quot;Konfiguration des technischen **[!UICONTROL Adobe IMS-Kontos]** &quot;weitergeleitet. By default, the **Certificate** tab opens.

   Wählen Sie die Cloud-Lösung **[!UICONTROL Adobe Brand Portal]**.

1. Mark the checkbox **[!UICONTROL Create new certificate]** and specify an **alias** for the certificate. Der Alias dient als Name des Dialogfelds.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Klicken Sie dann im Dialogfeld auf **[!UICONTROL OK]** , um das öffentliche Zertifikat zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Click **[!UICONTROL Download Public Key]** and save the certificate (.crt) file on your machine.

   Die Zertifikatdatei wird in weiteren Schritten zum Konfigurieren der API für Ihren Markenportal-Mandanten und zum Generieren von Dienstkontoanmeldeinformationen in der Adobe Developer Console verwendet.

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Auf der Registerkarte &quot; **Konto** &quot;erstellen Sie das Adobe IMS-Konto, dafür benötigen Sie jedoch die Dienstkontoanmeldeinformationen, die in der Adobe Developer Console generiert werden. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie eine JWT-Verbindung (Dienstkonto) in Adobe Developer Console](#createnewintegration) , um die Anmeldeinformationen und die JWT-Nutzlast zum Konfigurieren des IMS-Kontos abzurufen.

### Verbindung zum Erstellen eines Dienstkontos (JWT) {#createnewintegration}

In der Adobe Developer Console werden Projekte und APIs auf Unternehmensebene (Pächter des Markenportals) konfiguriert. Beim Konfigurieren einer API wird eine JWT-Verbindung (Service Account) in der Adobe Developer Console erstellt. Es gibt zwei Methoden zum Konfigurieren der API, indem ein Schlüsselpaar (private und öffentliche Schlüssel) generiert oder ein öffentlicher Schlüssel hochgeladen wird. Um die Autoreninstanz von AEM Assets mit dem Markenportal zu konfigurieren, müssen Sie ein öffentliches Zertifikat (öffentlicher Schlüssel) in der Autoreninstanz von AEM Assets generieren und Anmeldeinformationen in Adobe Developer Console erstellen, indem Sie den öffentlichen Schlüssel hochladen. Dieser öffentliche Schlüssel wird zum Konfigurieren der API für das ausgewählte Markenportal-Unternehmen verwendet und generiert die Anmeldeinformationen und die JWT-Nutzlast für das Dienstkonto. Diese Anmeldeinformationen werden außerdem zum Konfigurieren des IMS-Kontos in der Autoreninstanz von AEM Assets verwendet. Nachdem das IMS-Konto konfiguriert wurde, können Sie den Markenportal-Cloud-Dienst in der Autoreninstanz von AEM Assets konfigurieren.

Führen Sie die folgenden Schritte aus, um die Dienstkontoberechtigungen und die JWT-Nutzlast zu generieren:

1. Melden Sie sich bei der Adobe Developer Console mit Systemadministrator-Berechtigungen für die IMS-Organisation (Brand Portal-Mandant) an. Die Standardeinstellung ist

   [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui)


   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die richtige IMS-Organisation (Markenportal-Mieter) aus der Dropdown-Liste (Organisations-Liste) oben rechts ausgewählt haben.

1. Click **[!UICONTROL Create new project]**. Ein leeres Projekt wird für Ihre Organisation erstellt.

   Klicken Sie auf Projekt **[!UICONTROL bearbeiten]** , um den **[!UICONTROL Projekttitel]** und die **[!UICONTROL Projektbeschreibung]** zu aktualisieren, und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Projekt erstellen](assets/service-account1.png)

1. Klicken Sie auf der Registerkarte Projektübersicht auf **[!UICONTROL Hinzufügen API]**.

   ![Hinzufügen API](assets/service-account2.png)

1. Wählen Sie im Fenster Hinzufügen API die Option **[!UICONTROL AEM Brand Portal]** und klicken Sie auf **[!UICONTROL Weiter]**.

   Stellen Sie sicher, dass Sie Zugriff auf den AEM Brand Portal-Dienst haben.

1. Klicken Sie im Fenster &quot;API konfigurieren&quot;auf Ihren öffentlichen Schlüssel **[!UICONTROL hochladen]**. Klicken Sie dann auf &quot;Datei **** auswählen&quot;und laden Sie das öffentliche Zertifikat (.crt-Datei) hoch, das Sie im Abschnitt zum [Abrufen des öffentlichen Zertifikats](#public-certificate) heruntergeladen haben.

   Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Öffentlichen Schlüssel hochladen](assets/service-account3.png)

1. Überprüfen Sie das öffentliche Zertifikat und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie das Standardprodukt- **[!UICONTROL Asset-Markenportal]** aus und klicken Sie auf **[!UICONTROL Speicherkonfiguration]**.

   ![Profil auswählen](assets/service-account4.png)

1. Wenn die API konfiguriert ist, werden Sie zur API-Übersicht weitergeleitet. Klicken Sie in der linken Navigation unter **[!UICONTROL Berechtigungen]** auf **[!UICONTROL Dienstkonto (JWT)]**.

   >[!NOTE]
   >
   >Sie können die Anmeldeinformationen nach Bedarf Ansicht und andere Aktionen ausführen (JWT-Token generieren, Berechtigungsdetails kopieren, Clientgeheimnis abrufen usw.).

1. Kopieren Sie auf der Registerkarte &quot; **[!UICONTROL Clientanmeldeinformationen]** &quot;die **[!UICONTROL Client-ID]**.

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Dienstkontoberechtigungen](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]**.

Sie können jetzt die Client-ID (API-Schlüssel), das Clientgeheimnis und die JWT-Nutzlast verwenden, um das IMS-Konto [in der AEM Assets-Cloud-Instanz zu](#create-ims-account-configuration) konfigurieren.

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

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.
-->

### Erstellen der Konfiguration des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Verbindung zum Erstellen eines Dienstkontos (JWT)](#createnewintegration)

Führen Sie die folgenden Schritte aus, um das IMS-Konto zu konfigurieren, das Sie im [Abrufen des öffentlichen Zertifikats](#public-certificate)erstellt haben.

1. Öffnen Sie die IMS-Konfiguration und navigieren Sie zur Registerkarte &quot; **[!UICONTROL Konten]** &quot;. Sie haben die Seite geöffnet, während Sie ein öffentliches Zertifikat [erhalten haben](#public-certificate).

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie in **[!UICONTROL Autorisierungsserver]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Fügen Sie die Client-ID in den API-Schlüssel, den Clientschlüssel und die JWT-Nutzlast ein, die Sie beim [Erstellen der JWT-Verbindung](#createnewintegration)kopiert haben.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Das IMS-Konto ist konfiguriert.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)


1. Wählen Sie die IMS-Konfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**.

   Klicken Sie im Dialogfeld auf **[!UICONTROL Aktivieren]** . Bei erfolgreicher Konfiguration wird eine Meldung angezeigt, dass das *Token erfolgreich* abgerufen wurde.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben. Erstellen Sie nicht mehrere IMS-Konfigurationen.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Sie müssen sie löschen und eine neue gültige Konfiguration erstellen.



### Konfigurieren von Cloud Service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um den Brand Portal-Cloud-Dienst zu erstellen:

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an.

1. From the **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klicken Sie auf der Seite &quot;Markenportal-Konfigurationen&quot;auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die IMS-Konfiguration aus, die Sie beim [Konfigurieren des IMS-Kontos](#create-ims-account-configuration)erstellt haben.

   In the **[!UICONTROL Service URL]**, enter your Brand Portal tenant (organization) URL.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt. Ihre Autoreninstanz für AEM Assets ist jetzt mit dem Markenportal-Mandanten konfiguriert.

### Testen der Konfiguration {#test-integration}

Führen Sie die folgenden Schritte aus, um die Konfiguration zu validieren:

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Navigieren Sie im Bereich **Tools** ![Tools](assets/tools.png) zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**.

   ![](assets/test-integration1.png)

1. In the Replication page, click **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

1. Für jeden Mandanten werden vier Replizierungsagenten erstellt.

   Suchen Sie die Replizierungsagenten Ihres Markenportal-Mandanten.

   Klicken Sie auf die Replizierungsagenten-URL.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Die Replizierungsagenten arbeiten parallel und teilen die Auftragsverteilung gleichmäßig, wodurch die Veröffentlichungsgeschwindigkeit um das Vierfache der Originalgeschwindigkeit steigt. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.


1. Um die Verbindung zwischen AEM Assets und Brand Portal zu überprüfen, klicken Sie auf **[!UICONTROL Verbindung testen]**.

   ![](assets/test-integration4.png)

   Unten auf der Seite wird eine Meldung angezeigt, dass Ihr Testpaket erfolgreich bereitgestellt wurde.

   ![](assets/test-integration5.png)

1. Überprüfen Sie die Testergebnisse für alle vier Replizierungsagenten einzeln.


   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation einiger Assets fehlschlägt.

Ihre Autoreninstanz für AEM Assets wurde erfolgreich mit dem Markenportal konfiguriert. Jetzt können Sie:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](../assets/brand-portal-publish-assets.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](../assets/brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](../assets/brand-portal-publish-collection.md)
* [Konfigurieren Sie die Asset-Beschaffung](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) , damit die Benutzer des Markenportals Elemente in AEM Assets hinzufügen und veröffentlichen können.

## Upgrade der Konfiguration {#upgrade-integration-65}

Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge aus, um vorhandene Konfigurationen zu aktualisieren:
1. [Ausführen von Aufträgen überprüfen](#verify-jobs)
1. [Vorhandene Konfigurationen löschen](#delete-existing-configuration)
1. [Konfiguration erstellen](#configure-new-integration-65)

### Ausführen von Aufträgen überprüfen {#verify-jobs}

Vergewissern Sie sich, dass in Ihrer AEM Assets-Autoreninstanz kein Veröffentlichungsauftrag ausgeführt wird, bevor Sie Änderungen vornehmen. Dazu können Sie alle vier Replizierungsagenten überprüfen und sicherstellen, dass die Warteschlange ideal/leer ist.

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an.

1. Navigieren Sie im Bereich **Tools** ![Tools](assets/tools.png) zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Deployment Replication]**.

1. In the Replication page, click **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

1. Suchen Sie die Replizierungsagenten Ihres Markenportal-Mandanten.

   Stellen Sie sicher, dass die **Warteschlange für alle Replizierungsagenten &quot;Idle** &quot;lautet. Es ist kein Veröffentlichungsauftrag aktiv.

   ![](assets/test-integration3.png)

### Vorhandene Konfigurationen löschen {#delete-existing-configuration}

Sie müssen beim Löschen der vorhandenen Konfigurationen die folgende Liste ausführen.
* Alle vier Replizierungsagenten löschen
* Cloud-Dienst löschen
* MAC-Benutzer löschen

1. Melden Sie sich bei Ihrer Autoreninstanz für AEM Assets an und öffnen Sie CRX Lite als Administrator. Die Standardeinstellung ist

   `http:// localhost:4502/crx/de/index.jsp`

1. Navigieren Sie zu allen vier Replizierungsagenten Ihres Markenportal-Mandanten `/etc/replications/agents.author` und löschen Sie sie.

   ![](assets/delete-replication-agent.png)

1. Navigieren Sie zur `/etc/cloudservices/mediaportal` Cloud-Dienstkonfiguration **und löschen Sie sie**.

   ![](assets/delete-cloud-service.png)

1. Navigieren Sie zum `/home/users/mac` MAC-Benutzer **Ihres Markenportals-Mandanten** und löschen Sie ihn.

   ![](assets/delete-mac-user.png)


Sie können jetzt eine Konfiguration [in Ihrer AEM 6.5-Autoreninstanz](#configure-new-integration-65) erstellen.



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen in Brand Portal veröffentlichen. Weitere Details finden Sie unter:

* [Veröffentlichen von Assets in Brand Portal](/help/assets/brand-portal-publish-assets.md)
* [Veröffentlichen von Ordnern in Brand Portal](/help/assets/brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen in Brand Portal](/help/assets/brand-portal-publish-collection.md)
