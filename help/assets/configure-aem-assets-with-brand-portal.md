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
source-git-commit: fb59bd52be86894e93063f4b7c32aef0ed23250b
workflow-type: tm+mt
source-wordcount: '1748'
ht-degree: 64%

---


# Konfigurieren von AEM Assets mit Brand Portal {#configure-integration-65}

Adobe Experience Manager (AEM) Assets wird über Adobe I/O in Brand Portal konfiguriert. Dadurch wird ein IMS-Token zur Autorisierung Ihres Brand Portal-Mandanten abgerufen.

>[!NOTE]
>
>Die Konfiguration von AEM Assets mit Brand Portal über Adobe I/O wird auf AEM 6.5.4.0 und höher unterstützt.
>
>Zuvor wurde Brand Portal über das alte OAuth-Gateway in der klassischen Benutzeroberfläche konfiguriert. Das Gateway ruft mithilfe des JWT-Token-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab.
>
>Die Konfiguration über das alte OAuth-Protokoll wird ab dem 6. April 2020 nicht mehr unterstützt, sondern erfolgt nun über Adobe I/O.


>[!TIP]
>
>***Nur für Bestandskunden***
>
>Es wird empfohlen, weiterhin die vorhandene alte OAuth-Gateway-Konfiguration zu verwenden. Falls Probleme mit der alten OAuth-Gateway-Konfiguration auftreten, löschen Sie die vorhandene Konfiguration und erstellen Sie eine neue Konfiguration über Adobe I/O.



In dieser Hilfe werden die folgenden zwei Anwendungsfälle beschrieben:
* [Neue Konfiguration](#configure-new-integration-65): Wenn Sie ein neuer Brand Portal-Benutzer sind und Ihre AEM Assets-Autoreninstanz mit dem Markenportal konfigurieren möchten, können Sie eine neue Konfiguration auf der Adobe-E/A erstellen.
* [Upgrade-Konfiguration](#upgrade-integration-65): Wenn Sie ein bestehender Brand Portal-Benutzer mit Ihrer AEM Assets-Autoreninstanz sind, die mit Brand Portal auf dem alten OAuth Gateway konfiguriert wurde, sollten Sie die vorhandenen Konfigurationen löschen und eine neue Konfiguration auf der Adobe-E/A-Benutzeroberfläche erstellen.

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

Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge durch, wenn Sie AEM Assets mit Markenportal zum ersten Mal konfigurieren:
1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen der Adobe I/O-Integration](#createnewintegration)
1. [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-integration)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Brand Portal-Mandanten mit der Autoreninstanz von AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Anmelden bei der Autoreninstanz AEM AssetsStandard-URL: http:// localhost:4502/aem/start.html
1. From **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Security]** >> **[!UICONTROL Adobe IMS Configurations]**.

   ![Benutzeroberfläche der Adobe IMS-Kontokonfiguration](assets/ims-config1.png)

1. Die Seite für Adobe IMS-Konfigurationen wird geöffnet.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   This will take you to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page.

1. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.

   Wählen Sie in **Cloud-Lösung** die Option **[!UICONTROL Adobe Brand Portal]** aus.

1. Mark the checkbox **[!UICONTROL Create new certificate]** and specify an **alias** for the certificate. Der Alias dient als Name des Dialogfelds.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]**, um das öffentliche Zertifikat zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die Zertifikatdatei *AEM-Adobe-IMS.crt* auf Ihrem Computer. Die Zertifikatdatei wird verwendet, um die [Adobe I/O-Integration zu erstellen](#createnewintegration).

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Um auf der Registerkarte **Konto** das Adobe IMS-Konto zu erstellen, benötigen Sie die Integrationsdetails. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie die Adobe I/O-Integration](#createnewintegration), um die Integrationsdetails für IMS-Kontokonfigurationen abzurufen.

### Erstellen der Adobe I/O-Integration {#createnewintegration}

Die Adobe-I/O-Integration generiert API-Schlüssel, Client-Geheimnis und Payload (JWT), die zum Einrichten der IMS-Kontokonfigurationen erforderlich sind.

1. Melden Sie sich bei der Adobe I/O-Konsole mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten an.

   Standard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klicken Sie auf **[!UICONTROL Integration erstellen]**.

1. Wählen Sie **[!UICONTROL Auf API zugreifen]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Neue Integration erstellen](assets/create-new-integration1.png)

1. Eine neue Integrationsseite wird geöffnet.

   Wählen Sie Ihre Organisation aus der Dropdown-Liste aus.

   Wählen Sie in **[!UICONTROL Experience Cloud]** den Eintrag **[!UICONTROL AEM Brand Portal]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   Wenn die Option „Brand Portal“ für Sie deaktiviert ist, stellen Sie sicher, dass Sie die richtige Organisation aus dem Dropdown-Feld über der Option **[!UICONTROL Adobe Services]** ausgewählt haben. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Integration erstellen](assets/create-new-integration2.png)

1. Geben Sie einen Namen und eine Beschreibung für die Integration an. Klicken Sie auf **[!UICONTROL Eine Datei von Ihrem Computer auswählen]** und laden Sie die `AEM-Adobe-IMS.crt`-Datei hoch, die im Abschnitt [Öffentliche Zertifikate erhalten](#public-certificate) heruntergeladen wurde.

1. Wählen Sie das Profil Ihrer Organisation aus.

   Sie können auch das Standardprofil **[!UICONTROL Assets Brand Portal]** auswählen und auf **[!UICONTROL Integration erstellen]** klicken. Die Integration wird erstellt.

1. Klicken Sie auf **[!UICONTROL Weiter zu Integrationsdetails]**, um die Integrationsinformationen anzuzeigen.

   Kopieren Sie den **[!UICONTROL API-Schlüssel]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie den Client-Geheimnisschlüssel.

   ![API-Schlüssel, Client-Geheimnis und Payload-Daten einer Integration ](assets/create-new-integration3.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT]** und kopieren Sie die **[!UICONTROL JWT-Payload]**.

   API-Schlüssel, Client-Geheimnisschlüssel und JWT-Payload-Informationen werden verwendet, um eine IMS-Kontokonfiguration zu erstellen.

### Erstellen der Konfiguration des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen der Adobe I/O-Integration](#createnewintegration)

**Schritte zum Erstellen der Konfiguration des IMS-Kontos:**

1. Öffnen Sie die Seite „IMS-Konfiguration“, Registerkarte **[!UICONTROL Konten]**. Sie haben die Seite am Ende des Abschnitts [Abrufen eines öffentlichen Zertifikats](#public-certificate) geöffnet gelassen.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie in **[!UICONTROL Autorisierungsserver]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Fügen Sie den API-Schlüssel, den Client-Geheimnisschlüssel und die JWT-Payload ein, die Sie am Ende von [Erstellen der Adobe I/O-Integration](#createnewintegration) kopiert haben.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Die Integration wird erstellt.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)


1. Wählen Sie die IMS-Konfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**. Das folgende Dialogfeld wird angezeigt.

   Klicken Sie auf **[!UICONTROL Prüfen]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich abgerufen* angezeigt.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben. Erstellen Sie nicht mehrere IMS-Konfigurationen.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Sie müssen sie löschen und eine neue gültige Konfiguration erstellen.


### Konfigurieren von Cloud Service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um eine Cloud Service-Konfiguration für Brand Portal zu erstellen:

1. Bei Ihrer AEM Assets-Autoreninstanz anmelden

   Standard-URL: http:// localhost:4502/aem/start.html
1. From **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Cloud Services >> AEM Brand Portal]**.

   Die Seite zur Brand Portal-Konfiguration wird geöffnet.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die im Schritt erstellte IMS-Konfiguration aus und [erstellen Sie die IMS-Kontokonfiguration](#create-ims-account-configuration).

   Geben Sie in **[!UICONTROL Dienst-URL]** Ihre Brand Portal-Mandanten-URL ein.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt. Ihre Autoreninstanz für AEM Assets ist jetzt mit dem Markenportal-Mandanten integriert.

### Testen der Konfiguration {#test-integration}

1. Bei Ihrer AEM Assets-Autoreninstanz anmelden

   Standard-URL: http:// localhost:4502/aem/start.html

1. Navigieren Sie im Bereich **Tools** ![Tools](assets/tools.png) zu **[!UICONTROL Bereitstellung > Replikation]**.

   ![](assets/test-integration1.png)

1. Die Replikationsseite wird geöffnet.

   Klicken Sie auf **[!UICONTROL Agenten beim Autor]**.

   ![](assets/test-integration2.png)

1. Für jeden Mandanten werden vier Replizierungsagenten erstellt.

   Suchen Sie die Replizierungsagenten Ihres Markenportal-Mandanten.

   Klicken Sie auf die Replizierungsagenten-URL.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Die Replizierungsagenten arbeiten parallel und teilen die Auftragsverteilung gleichmäßig, wodurch die Veröffentlichungsgeschwindigkeit um das Vierfache der Originalgeschwindigkeit steigt. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.

   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation einiger Assets fehlschlägt.


1. To verify the connection between AEM Assets author and Brand Portal, click **[!UICONTROL Test Connection]**.

   ![](assets/test-integration4.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

   ![](assets/test-integration5.png)

   >[!NOTE]
   >
   >Die Replizierungsagenten arbeiten parallel und teilen die Auftragsverteilung gleichmäßig, wodurch die Veröffentlichungsgeschwindigkeit um das Vierfache der Originalgeschwindigkeit steigt. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.

1. Überprüfen Sie die Testergebnisse für alle vier Replizierungsagenten einzeln.


   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation einiger Assets fehlschlägt.

Markenportal wurde erfolgreich mit Ihrer AEM Assets-Autoreninstanz konfiguriert. Sie können jetzt:

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

1. Bei Ihrer AEM Assets-Autoreninstanz anmelden

   Standard-URL: http:// localhost:4502/aem/start.html

1. Navigieren Sie im Bereich **Tools** ![Tools](assets/tools.png) zu **[!UICONTROL Bereitstellung > Replikation]**.

1. Die Replikationsseite wird geöffnet.

   Klicken Sie auf **[!UICONTROL Agenten beim Autor]**.

   ![](assets/test-integration2.png)

1. Suchen Sie die Replizierungsagenten Ihres Markenportal-Mandanten.

   Stellen Sie sicher, dass die **Warteschlange für alle Replizierungsagenten &quot;Idle** &quot;lautet. Es ist kein Veröffentlichungsauftrag aktiv.

   ![](assets/test-integration3.png)

### Vorhandene Konfigurationen löschen {#delete-existing-configuration}

Sie müssen beim Löschen der vorhandenen Konfigurationen die folgende Liste ausführen.
* Alle vier Replizierungsagenten löschen
* Cloud-Dienst löschen
* MAC-Benutzer löschen

1. Melden Sie sich bei Ihrer Autoreninstanz für AEM Assets an und öffnen Sie CRX Lite als Administrator.

   Standard-URL: http:// localhost:4502/crx/de/index.jsp

1. Navigieren Sie zu allen vier Replizierungsagenten Ihres Markenportal-Mandanten `/etc/replications/agents.author` und löschen Sie sie.

   ![](assets/delete-replication-agent.png)

1. Navigieren Sie zur `/etc/cloudservices/mediaportal` Cloud-Dienstkonfiguration **und löschen Sie sie**.

   ![](assets/delete-cloud-service.png)

1. Navigieren Sie zum `/home/users/mac` MAC-Benutzer **Ihres Markenportals-Mandanten** und löschen Sie ihn.

   ![](assets/delete-mac-user.png)


Sie können jetzt eine Konfiguration [für Ihre AEM 6.5-Autoreninstanz auf der Adobe-I/O](#configure-new-integration-65) erstellen.



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
