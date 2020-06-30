---
title: Konfigurieren Sie das Asset-Tagging mit dem Smart Content Service.
description: Learn how to configure smart tagging and enhanced smart tagging in [!DNL Adobe Experience Manager], using the Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfac819018e85e0e8221bfcc57bc1eaf43b7ff25
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 39%

---


# Configure asset tagging using the Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Sie können [!DNL Adobe Experience Manager] mit der Adobe Developer Console in den Smart Content Service integrieren. Use this configuration to access the Smart Content Service from within [!DNL Experience Manager].

Der Artikel beschreibt die folgenden Hauptaufgaben, die zum Konfigurieren des Smart Content Service erforderlich sind. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe Developer Console gateway before forwarding your request to the Smart Content Service.

1. Create a Smart Content Service configuration in [!DNL Experience Manager] to generate a public key. [Erhalten Sie ein öffentliches Zertifikat für die OAuth-Integration.](#obtain-public-certificate)
1. [Erstellen Sie eine Integration in Adobe Developer Console](#create-adobe-i-o-integration) und laden Sie den generierten öffentlichen Schlüssel hoch.
1. [Konfigurieren Sie Ihre Bereitstellung](#configure-smart-content-service) mithilfe des API-Schlüssels und anderer Anmeldedaten aus der Adobe Developer Console.
1. [Testen Sie die Konfiguration](#validate-the-configuration).
1. Optionally, [enable auto-tagging on asset upload](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Voraussetzungen {#prerequisites}

Bevor Sie den Smart Content Service verwenden können, stellen Sie Folgendes sicher, um eine Integration in der Adobe Developer Console zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Der Smart Content Service ist für Ihre Organisation aktiviert.

To enable Enhanced Smart Tags, in addition to the above, also install the latest [AEM service pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Abrufen eines öffentlichen Zertifikats {#obtain-public-certificate}

Mit einem öffentlichen Zertifikat können Sie Ihr Profil in der Adobe Developer Console authentifizieren.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy-Cloud Service]** auf.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Dienst-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld &quot;Experience Manager-Smart-Content-Dienst&quot;zur Bereitstellung der Content-Dienst-URL](assets/aem_scs.png)

   >[!NOTE]
   >
   >The URL provided as [!UICONTROL Service URL] is not accessible via browser and generates a 404 error. Die Konfiguration funktioniert mit demselben Wert des [!UICONTROL Service-URL-Parameters] . For the overall service status and maintenance schedule, see [https://status.adobe.com](https://status.adobe.com).

1. Click **[!UICONTROL Download Public Certificate for OAuth Integration]**, and download the public certificate file `AEM-SmartTags.crt`.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/smart-tags-download-public-cert.png)

### Reconfigure when a certificate expires {#certrenew}

Nach Ablauf eines Zertifikats wird es nicht mehr als vertrauenswürdig eingestuft. Sie können ein abgelaufenes Zertifikat nicht verlängern. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klicken Sie auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.
1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag für Ähnlichkeitssuche in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)

   *Abbildung: Löschen Sie den vorhandenen`similaritysearch`Eintrag in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.*

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.
1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zu den vorhandenen Smart Content Services auf der Seite **[!UICONTROL Integrationen]**. Laden Sie das neue Zertifikat hoch. For more information, see the instructions in [Create Adobe Developer Console integration](#create-adobe-i-o-integration).

## Adobe Developer Console-Integration erstellen {#create-adobe-i-o-integration}

Um Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in der Adobe Developer Console, um den API-Schlüssel, die technische Konto-ID, die Organisations-ID und den geheimen Clientschlüssel zu generieren.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Rolle Systemadministrator ist.
1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL Hinzufügen API]**.
1. Wählen Sie auf der Seite **[!UICONTROL Hinzufügen API]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]**. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie den öffentlichen Schlüssel **[!UICONTROL hochladen]**. Geben Sie die Zertifikatsdatei an, von der Sie heruntergeladen [!DNL Experience Manager]haben. Es wird eine Meldung [!UICONTROL Öffentliche Schlüssel (Schlüssel) angezeigt, die erfolgreich] hochgeladen wurden. Klicken Sie auf **[!UICONTROL Weiter]**.
1. [!UICONTROL Auf der Seite &quot;Neue Dienstkontoberechtigung] erstellen&quot;wird der öffentliche Schlüssel für das soeben konfigurierte Dienstkonto angezeigt. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie auf der Seite &quot; **[!UICONTROL Produktseiten]** auswählen&quot;die Option **[!UICONTROL &quot;Smart Content Services]**&quot;aus. Klicken Sie auf Konfigurierte API **[!UICONTROL speichern]**. Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite geöffnet, um diese Werte zu kopieren und in Experience Manager hinzuzufügen, wenn Sie Smart-Tags in weiter konfigurieren [!DNL Experience Manager].

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

## Konfigurieren des Smart Content Service {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder Technische Konto-ID, Organisations-ID, geheimer Clientschlüssel, Autorisierungsserver und API-Schlüssel aus der Adobe Developer Console-Integration. Creating a Smart Tags cloud configuration allows authentication of API requests from the [!DNL Experience Manager] deployment.

1. In [!DNL Experience Manager], navigate to **[!UICONTROL Tools > Cloud Service > Legacy Cloud Services]** to open the [!UICONTROL Cloud Services] console.
1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.
1. Verwenden Sie für die Felder **[!UICONTROL API-Schlüssel]**, **[!UICONTROL Technische Konto-ID]**, **[!UICONTROL Organisations-ID]** und **[!UICONTROL Geheimer Clientschlüssel]** die oben generierten Werte.

## Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie auf Ihren [!DNL Experience Manager] Server unter `https://[aem_server]:[port]`.
1. Öffnen Sie unter **[!UICONTROL Tools > Vorgänge > Web-Konsole]** die OSGi-Konsole. Klicken Sie auf **[!UICONTROL Haupt > JMX]**.
1. Klicken Sie auf **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.
1. Klicken Sie auf **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

## Enable smart tagging in the DAM Update Asset workflow (Optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Gehen Sie [!DNL Experience Manager]zu **[!UICONTROL Werkzeuge > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** das **[!UICONTROL DAM Update Asset]**-Workflowmodell.
1. Click **[!UICONTROL Edit]** from the toolbar.
1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Smart Tag-Asset]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart Tag Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Abbildung: Hinzufügen Schritt für Smart-Tag-Assets nach dem Schritt für die Prozessminiaturansicht im Arbeitsablauf für[!UICONTROL DAM-Aktualisierung des Assets].*

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren und Schritt zum Hinzufügen von Smarttags](assets/smart-tag-step-properties-workflow1.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren, um einen Schritt zum intelligenten Tag hinzuzufügen und Handler-Modus auszuwählen](assets/smart-tag-step-properties-workflow2.png)

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Flag ignorieren]** aus.

   ![Konfigurieren Sie den Arbeitsablauf für DAM-Aktualisierung für Assets, um einen Schritt für intelligente Tags hinzuzufügen, und wählen Sie &quot;Smart-Tag-Flag ignorieren&quot;](assets/smart-tag-step-properties-workflow3.png)

1. Click **[!UICONTROL OK]** to close the process step, and then save the workflow.

>[!MORELIKETHIS]
>
>* [Verwaltung intelligenter Tags](managing-smart-tags.md)
>* [Übersicht und Schulung von Smart-Tags](enhanced-smart-tags.md)
>* [Richtlinien und Regeln zur Schulung des intelligenten Inhaltsdienstes](smart-tags-training-guidelines.md)
>* [Videoschulung zum Konfigurieren von Smart-Tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

