---
title: Asset-Tags mit dem Smart Content Service konfigurieren
description: Learn how to configure smart tagging and enhanced smart tagging in [!DNL Adobe Experience Manager], using the Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5599e0d4a3e52a4ad98b776b9178722c7ac47cbc
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 60%

---


# Vorbereitung [!DNL Assets] für intelligente Tags {#configure-asset-tagging-using-the-smart-content-service}

Bevor Sie mit dem Tagging Ihrer Assets mit Smart Content Services beginnen können, müssen Sie sie [!DNL Experience ManageR Assets] in die Adobe Developer Console integrieren, um den intelligenten Dienst zu nutzen [!DNL Adobe Sensei]. Nach der Konfiguration trainieren Sie den Dienst mit ein paar Bildern und einem Tag.

Bevor Sie den Smart Content Service verwenden, stellen Sie Folgendes sicher:

* [Integration mit der Adobe Developer Console](#integrate-adobe-io).
* [Schulung des Smart Content Service](#training-the-smart-content-service).

   <!-- TBD: This link will update soon after the new articles goes live on docs.adobe.com. Change it when new URL is available.
  -->

* Installieren Sie das neueste [Experience Manager Service Pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Integration mit der Adobe Developer Console {#integrate-adobe-io}

Wenn Sie die Integration mit der Adobe Developer Console durchführen, authentifiziert der [!DNL Experience Manager] Server Ihre Dienstberechtigungen mit dem Adobe Developer Console Gateway, bevor Sie Ihre Anforderung an den Smart Content Service weiterleiten. Zur Integration benötigen Sie ein Adobe ID-Konto, das über Administratorberechtigungen für das Unternehmen verfügt, sowie eine Smart Content Service-Lizenz, die für Ihr Unternehmen erworben und aktiviert wurde.

Gehen Sie wie folgt vor, um den Dienst für intelligente Inhalte zu konfigurieren:

1. [Erstellen Sie in eine Konfiguration für den Smart Content Service, um einen öffentlichen Schlüssel zu erstellen. ](#obtain-public-certificate)[!DNL Experience Manager] [Erlangen Sie ein öffentliches Zertifikat](#obtain-public-certificate) für die OAuth-Integration.

1. [Erstellen Sie eine Integration in der Adobe Developer Console](#create-adobe-i-o-integration) und laden Sie den generierten öffentlichen Schlüssel hoch.

1. [Konfigurieren Sie Ihre Bereitstellung](#configure-smart-content-service) mithilfe des API-Schlüssels und anderer Anmeldedaten aus der Adobe Developer Console.

1. [Testen Sie die Konfiguration](#validate-the-configuration).

1. Optionally, [enable auto-tagging on asset upload](#enable-smart-tagging-in-the-update-asset-workflow-optional).

### Konfiguration des Smart Content Service erstellen, um ein öffentliches Zertifikat zu erhalten {#obtain-public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in der Adobe Developer Console.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]** auf.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Dienst-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld &quot;Experience Manager-Smart-Content-Dienst&quot;zur Bereitstellung der Content-Dienst-URL](assets/aem_scs.png)


   *Abbildung: Dialogfeld &quot;Smart Content Service&quot;zum Bereitstellen der URL des Inhaltsdienstes*

   >[!NOTE]
   >
   >The URL provided as [!UICONTROL Service URL] is not accessible via browser and generates a 404 error. Die Konfiguration funktioniert mit demselben Wert des [!UICONTROL Service-URL-Parameters] . For the overall service status and maintenance schedule, see [https://status.adobe.com](https://status.adobe.com).

1. Click **[!UICONTROL Download Public Certificate for OAuth Integration]**, and download the public certificate file `AEM-SmartTags.crt`.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/smart-tags-download-public-cert.png)


   *Abbildung: Einstellungen für den intelligenten Tag-Dienst*

#### Reconfigure when a certificate expires {#certrenew}

Nach Ablauf eines Zertifikats wird es nicht mehr als vertrauenswürdig eingestuft. Sie können ein abgelaufenes Zertifikat nicht verlängern. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus.

1. Melden Sie sich bei Ihrer [!DNL Experience Manager]-Implementierung als Administrator an. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.

1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag für Ähnlichkeitssuche in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)


   *Abbildung: Löschen des vorhandenen Eintrags `similaritysearch` in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.*

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zu den vorhandenen Smart Content Services auf der Seite **[!UICONTROL Integrationen]**. Laden Sie das neue Zertifikat hoch. For more information, see the instructions in [Create Adobe Developer Console integration](#create-adobe-i-o-integration).

### Adobe Developer Console-Integration erstellen {#create-adobe-i-o-integration}

Um Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in Adobe Developer Console, um den [!UICONTROL API-Schlüssel] (der im Feld [!UICONTROL CLIENT ID] der Adobe Developer Console-Integration generiert wurde), die [!UICONTROL TECHNISCHE ACCOUNT-ID], die [!UICONTROL Organisations-ID]und [!UICONTROL CLIENT SECRET]  [!DNL Experience Manager]für die Einstellungen des Smart-Tagging-Dienstes zu erhalten.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Organisationsrolle „Systemadministrator“ ist.

1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie auf der Seite **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL Öffentlichen Schlüssel hochladen]** aus. Stellen Sie die von [!DNL Experience Manager] heruntergeladenen Zertifikatdatei bereit. Die Meldung [!UICONTROL Öffentliche(r) Schlüssel erfolgreich hochgeladen] wird angezeigt. Klicken Sie auf **[!UICONTROL Weiter]**.

   Die Seite [!UICONTROL Neue Dienstkonto (JWT)-Anmeldedaten erstellen] zeigt den öffentlichen Schlusselle für das Dienstkonto an, das Sie gerade konfiguriert haben.

1. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie auf der Seite **[!UICONTROL Produktprofile auswählen]** die Option **[!UICONTROL Smart Content Services]** aus. Klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite geöffnet, um diese Werte zu kopieren und in den Einstellungen [!UICONTROL des Smart-Tagging-Dienstes] Assets der Cloud-Konfiguration hinzuzufügen, um Smarttags zu konfigurieren. [!DNL Experience Manager]

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)


   *Abbildung: Integrationsdetails in der Adobe Developer Console*

### Konfigurieren des Smart Content Service {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der [!UICONTROL Felder &quot;TECHNISCHE KONTO-ID]&quot;, &quot; [!UICONTROL Organisations-ID]&quot;, &quot; [!UICONTROL CLIENT-SECRET]&quot;und &quot; [!UICONTROL CLIENT-ID] &quot;aus der Adobe Developer Console-Integration. Creating a Smart Tags cloud configuration allows authentication of API requests from the [!DNL Experience Manager] deployment.

1. In [!DNL Experience Manager], navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** to open the [!UICONTROL Cloud Services] console.

1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.

1. Kopieren Sie für die Felder [!UICONTROL API-Schlüssel], [!UICONTROL Technische Konto-ID], [!UICONTROL Organisations-ID]und [!UICONTROL geheimer Clientschlüssel]die folgenden Werte, die in der [Adobe Developer Console-Integration](#create-adobe-i-o-integration)generiert wurden, und verwenden Sie sie.

   | [!UICONTROL Diensteinstellungen für Smart-Tagging in Assets] | [!DNL Adobe Developer Console] Integrationsfelder |
   |--- |--- |
   | [!UICONTROL API-Schlüssel] | [!UICONTROL CLIENT-ID] |
   | [!UICONTROL ID des technischen Kontos] | [!UICONTROL TECHNISCHE KONTO-ID] |
   | [!UICONTROL Unternehmens-ID] | [!UICONTROL Organisations-ID] |
   | [!UICONTROL Client-Geheimnis] | [!UICONTROL CLIENT SECRET] |

### Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie eine JMX MBean verwenden, um die Konfiguration zu validieren. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie auf Ihren [!DNL Experience Manager] Server unter `https://[aem_server]:[port]`.

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** to open the OSGi console. Click **[!UICONTROL Main] > [!UICONTROL JMX]**.

1. Klicken Sie auf `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Klicken Sie auf `validateConfigs()`. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

Die Überprüfungsergebnisse werden im gleichen Dialogfeld angezeigt.

### Enable smart tagging in the [!UICONTROL DAM Update Asset] workflow (Optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. In [!DNL Experience Manager], go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** das Workflow-Modell **[!UICONTROL DAM Update Asset]** aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Smart Tag-Asset]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Abbildung: Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“.*

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren und Schritt zum Hinzufügen von Smarttags](assets/smart-tag-step-properties-workflow1.png)


   *Abbildung: DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren und Schritt zum Hinzufügen von Smarttags*

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren, um einen Schritt zum intelligenten Tag hinzuzufügen und Handler-Modus auszuwählen](assets/smart-tag-step-properties-workflow2.png)


   *Abbildung: DAM-Arbeitsablauf zum Aktualisieren von Assets konfigurieren, um einen Schritt zum intelligenten Tag hinzuzufügen und Handler-Modus auszuwählen*

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Markierung ignorieren]** aus.

   ![Konfigurieren Sie den Arbeitsablauf für DAM-Aktualisierung für Assets, um einen Schritt für intelligente Tags hinzuzufügen, und wählen Sie &quot;Smart-Tag-Flag ignorieren&quot;](assets/smart-tag-step-properties-workflow3.png)


   *Abbildung: Konfigurieren Sie den Arbeitsablauf für DAM-Aktualisierung für Assets, um einen Schritt für intelligente Tags hinzuzufügen, und wählen Sie &quot;Smart-Tag-Flag ignorieren&quot;*

1. Klicken Sie auf **[!UICONTROL OK]**, um den Prozessschritt zu schließen, und speichern Sie dann den Workflow.

## Intelligente Inhaltserstellung {#training-the-smart-content-service}

Damit der Smart Content Service die Taxonomie Ihres Unternehmens erkennen kann, sollten Sie den Dienst auf einen Asset-Satz ausführen, der bereits für Ihr Unternehmen relevante Tags enthält. Um Ihre Markenbilder effektiv mit Tags zu versehen, erfordert der Smart Content Service, dass die Schulungsbilder bestimmten Richtlinien entsprechen. Nach dem Training kann der Dienst dieselbe Taxonomie auf einen ähnlichen Satz von Assets anwenden.

Sie können den Dienst mehrfach trainieren, um die Fähigkeit, relevante Tags anzuwenden, zu verbessern. Führen Sie nach jedem Trainingszyklus einen Tagging-Workflow aus und überprüfen Sie, ob Ihre Assets mit den richtigen Tags versehen wurden.

Sie können den Smart Content Service regelmäßig oder je nach Anforderung trainieren.

>[!NOTE]
>
>Der Trainings-Workflow wird nur für Ordner ausgeführt.

### Richtlinien für das Training {#guidelines-for-training}

Für optimale Ergebnisse sollten Bilder im Trainingssatz folgende Richtlinien einhalten:

**Menge und Größe:** Mindestens 30 Bilder pro Tag. Mindestens 500 Pixel auf der längeren Seite.

**Kohärenz**: Bilder für ein Tag sollten visuell ähnlich sein.

So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainings-Zwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Es geht darum, einige, aber recht unterschiedliche Beispiele zu liefern, damit der Experience Manager lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein.

Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainings-Bilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Dienst ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Service kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt).

Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Beispiel: Fügen Sie im Falle von Tags wie `raincoat` und `model-side-view` beide Tags zum entsprechenden Asset hinzu, bevor Sie dieses für Trainingszwecke verwenden.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Die Fähigkeit des Smart Content Service, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab. Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Service für die einzelnen Tags zu trainieren.

### Regelmäßiges Trainieren {#periodic-training}

Sie können festlegen, dass der Smart Content Service regelmäßig mit den Assets und zugewiesenen Tags in einem Ordner trainiert wird. Open the [!UICONTROL Properties] page of your asset folder, select **[!UICONTROL Enable Smart Tags]** under the **[!UICONTROL Details]** tab, and save the changes.

![enable_smart_tags](assets/enable_smart_tags.png)

Once this option is selected for a folder, [!DNL Experience Manager] runs a training workflow automatically to train the Smart Content Service on the folder assets and their tags. Standardmäßig wird der Trainings-Workflow jede Woche samstags um 00:30 Uhr ausgeführt.

### Training bei Bedarf {#on-demand-training}

Sie können den Smart Content Service über die Workflow-Konsole trainieren, wann immer es erforderlich ist.

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL Smart Tags Training]** workflow and then click **[!UICONTROL Start Workflow]** from the toolbar.
1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** nach dem Payload-Ordner, der die mit Tags versehenen Assets für das Trainieren des Diensts enthält.
1. Geben Sie einen Titel für den Workflow ein und fügen Sie einen Kommentar hinzu. Then, click **[!UICONTROL Run]**. Die Assets und Tags werden für das Training übermittelt.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Nachdem die Assets in einem Ordner für die Schulung verarbeitet wurden, werden in den nachfolgenden Schulungszyklen nur die geänderten Assets verarbeitet.

### Schulungsberichte zur Ansicht {#viewing-training-reports}

Um sicherzustellen, dass der Smart Content Service auf Ihre Tags im Asset-Trainingssatz trainiert ist, überprüfen Sie den Bericht zum Trainings-Workflow über die Berichte-Konsole.

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Klicken Sie auf der Seite **[!UICONTROL Asset-Berichte]** auf **[!UICONTROL Erstellen]**.
1. Wählen Sie den Bericht **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. Um den Bericht anzuzeigen, klicken Sie in der Symbolleiste auf **[!UICONTROL Ansicht]**.
1. Prüfen Sie die Details des Berichts.

   Der Bericht zeigt den Trainings-Status der von Ihnen trainierten Tags an. Grün gibt in der Spalte **[!UICONTROL Trainingsstatus]** an, dass der Smart Content Service für das Tag trainiert wird. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren.

   Wenn Ihre Tags nicht im Bericht angezeigt werden, führen Sie den Trainings-Workflow für diese Tags erneut aus.

1. Um den Bericht herunterzuladen, wählen Sie ihn aus der Liste aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**. Der Bericht wird als Microsoft Excel-Tabellenkalkulation heruntergeladen.

## Beschränkungen {#limitations}

* Verbesserte Smart-Tags basieren auf Lernmodellen von Bildern und deren Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version des Smart Content Service gibt es folgende Einschränkungen:

   * Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: T-Shirts mit schmalem oder normalem Schnitt.
   * Tags können nicht anhand von winzigen Mustern/Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
   * Tagging is supported in the locales that [!DNL Experience Manager] is supported in. Eine Liste der Sprachen finden Sie in den [Versionshinweisen für Smart Content Services](https://docs.adobe.com/content/help/de-DE/experience-manager-64/release-notes/smart-content-service-release-notes.html).

* To search for assets with smart tags (regular or enhanced), use the [!DNL Assets] Omnisearch (full-text search). Es gibt kein separates Suchprädikat für Smart-Tags.

>[!MORELIKETHIS]
>
>* [Übersicht und Schulung von Smart-Tags](enhanced-smart-tags.md)
>* [Videoschulung zum Konfigurieren von Smart-Tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

