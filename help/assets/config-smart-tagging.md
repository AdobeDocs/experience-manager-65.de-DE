---
title: Konfigurieren Sie das Asset-Tagging mit dem Smart Content Service.
description: Erfahren Sie, wie Sie mit dem Smart Content Service intelligentes Tagging und verbessertes intelligentes Tagging in Adobe Experience Manager konfigurieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Configure asset tagging using the Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

You can integrate [!DNL Adobe Experience Manager] with the Smart Content Service using Adobe I/O. Use this configuration to access the Smart Content Service from within [!DNL Experience Manager].

Der Artikel beschreibt die folgenden Hauptaufgaben, die zum Konfigurieren des Smart Content Service erforderlich sind. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe I/O gateway before forwarding your request to the Smart Content Service.

* Create a Smart Content Service configuration in [!DNL Experience Manager] to generate a public key. Erhalten Sie ein öffentliches Zertifikat für die OAuth-Integration.
* Erstellen Sie eine Integration in Adobe I/O und laden Sie den generierten öffentlichen Schlüssel hoch.
* Configure your [!DNL Experience Manager] instance using the API key and other credentials from Adobe I/O.
* Aktivieren Sie optional das automatische Tagging beim Hochladen eines Assets.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Verwendung des Smart Content Service Folgendes sicher, um eine Integration in Adobe I/O zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Der Smart Content Service ist für Ihre Organisation aktiviert.

## Erhalten eines öffentlichen Zertifikats {#obtain-public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge > Cloud-Services]**> **[!UICONTROL Legacy Cloud-Dienste]** auf.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Dienst-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld &quot;Experience Manager Smart Content Service&quot;, um die URL des Inhaltsdienstes bereitzustellen](assets/aem_scs.png)

1. Click **[!UICONTROL Download Public Certificate for OAuth Integration]**, and download the public certificate file `AEM-SmartTags.crt`.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/download_link.png)

### Reconfigure when a certificate expires {#certrenew}

Wenn das Zertifikat abläuft, wird es nicht mehr als vertrauenswürdig eingestuft. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus. Sie können ein abgelaufenes Zertifikat nicht verlängern.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klicken Sie auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.
1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag „similaritysearch“ (Ähnlichkeitssuche) in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)

   Löschen Sie den vorhandenen Eintrag „similaritysearch“ (Ähnlichkeitssuche) in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.
1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zu den vorhandenen Smart Content Services auf der Seite **[!UICONTROL Integrationen]**. Laden Sie das neue Zertifikat hoch. Weitere Informationen finden Sie in den Anweisungen unter [Adobe I/O-Integration erstellen](#create-adobe-i-o-integration).

## Adobe I/O-Integration erstellen {#create-adobe-i-o-integration}

Um Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in Adobe I/O zur Generierung von API-Schlüssel, ID des technischen Kontos, Organisations-ID und Client-Geheimnis.

1. Greifen Sie auf [https://console.adobe.io](https://console.adobe.io/) zu.
1. Wählen Sie auf der Seite &quot; **[!UICONTROL Integrationen]** &quot;das entsprechende Konto aus und vergewissern Sie sich, dass es sich bei der zugeordneten Organisationsrolle um einen Systemadministrator handelt.
1. Click **[!UICONTROL New integration]**.
1. Wählen Sie auf der Seite **[!UICONTROL Neue Integration erstellen]** die Option **[!UICONTROL Auf eine API zugreifen]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie unter **[!UICONTROL Experience Cloud]** die Option **[!UICONTROL Smart Content]**. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Auswählen der Option „Smart Content“ unter „Experience Cloud“ aus den verfügbaren Optionen beim Erstellen einer neuen Integration](assets/smart_content.png)

1. Wählen Sie auf der nächsten Seite **[!UICONTROL Neue Integration]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie auf der Seite **[!UICONTROL Integrationsdetails]** einen Namen für das Integrations-Gateway ein und fügen Sie eine Beschreibung hinzu.
1. Laden Sie in den **[!UICONTROL Zertifikaten zu öffentlichen Schlüsseln]** die Datei `AEM-SmartTags.crt` hoch, die Sie weiter oben heruntergeladen haben.
1. Click **[!UICONTROL Create Integration]**.
1. To view the integration information, click **[!UICONTROL Continue to integration details]**.

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

## Konfigurieren des Smart Content Service {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder „ID des technischen Kontos“, „Organisations-ID“, „Client-Geheimnis“, „Autorisierungsserver“ und „API-Schlüssel“ aus der Adobe I/O-Integration. Creating a Smart Tags cloud configuration allows authentication of API requests from the [!DNL Experience Manager] instance.

1. In [!DNL Experience Manager], navigate to **[!UICONTROL Tools > Cloud Service > Legacy Cloud Services]** to open the [!UICONTROL Cloud Services] console.
1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.
1. Verwenden Sie für die Felder **[!UICONTROL API-Schlüssel]**, **[!UICONTROL Technische Konto-ID]**, **[!UICONTROL Organisations-ID]** und **[!UICONTROL Geheimer Clientschlüssel]** die oben generierten Werte.

## Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie auf Ihren [!DNL Experience Manager] Server unter `https://[aem_server]:[port]`.

1. Öffnen Sie unter **[!UICONTROL Tools > Vorgänge > Web-Konsole]** die OSGi-Konsole. Klicken Sie auf **[!UICONTROL Haupt > JMX]**.
1. Klicken Sie auf **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Die Seite **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** wird geöffnet
1. Klicken Sie auf **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

## Aktivieren der Smart-Tagging-Funktion im Workflow „Update-Asset“ (optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Gehen Sie [!DNL Experience Manager]zu **[!UICONTROL Werkzeuge > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** das **[!UICONTROL DAM Update Asset]**-Workflowmodell.
1. Click **[!UICONTROL Edit]** from the toolbar.
1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Smart Tag-Asset]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![[!UICONTROL Schritt zum Hinzufügen von Smart Tag Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“]](assets/chlimage_1-105.png)

   *Abbildung: Hinzufügen Schritt für Smart-Tag-Assets nach dem Schritt für die Prozessminiaturansicht im Arbeitsablauf für[!UICONTROL DAM-Aktualisierung des Assets].*

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![chlimage_1-3](assets/chlimage_1-106.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![chlimage_1-4](assets/chlimage_1-107.png)

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Flag ignorieren]** aus.

   ![chlimage_1-5](assets/chlimage_1-108.png)

1. Click **[!UICONTROL OK]** to close the process step, and then save the workflow.

>[!MORELIKETHIS]
>
>* [Verwaltung intelligenter Tags](managing-smart-tags.md)
>* [Übersicht und Schulung von Smart-Tags](enhanced-smart-tags.md)
>* [Richtlinien und Regeln zur Schulung des intelligenten Inhaltsdienstes](smart-tags-training-guidelines.md)
>* [Videoschulung zum Konfigurieren von Smart-Tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

