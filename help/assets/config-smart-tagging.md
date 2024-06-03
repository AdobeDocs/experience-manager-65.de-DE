---
title: Konfigurieren des Asset-Tagging mit dem Smart Content Service
description: Erfahren Sie, wie Sie in  [!DNL Adobe Experience Manager] Smart-Tagging und optimierte Smart-Tags mit dem Smart Content Service konfigurieren.
contentOwner: AG
role: Admin
feature: Tagging,Smart Tags
exl-id: 9f68804f-ba15-4f83-ab1b-c249424b1396
solution: Experience Manager, Experience Manager Assets
source-git-commit: 5aff321eb52c97e076c225b67c35e9c6d3371154
workflow-type: ht
source-wordcount: '2415'
ht-degree: 100%

---

# Vorbereiten von [!DNL Assets] für Smart-Tagging {#configure-asset-tagging-using-the-smart-content-service}

Bevor Sie mit dem Tagging Ihrer Assets per Smart Content Services beginnen können, integrieren Sie [!DNL Experience Manager Assets] in die Adobe Developer Console, um den Smart-Service von [!DNL Adobe Sensei] zu nutzen. Trainieren Sie nach der Konfiguration den Service mit einigen Bildern und einem Tag.

>[!NOTE]
>
>* Smart Content Services ist nicht mehr für neue Kunden von [!DNL Experience Manager Assets] On-Premise verfügbar. Bestehende On-Premise-Kunden, die diese Funktion bereits aktiviert haben, können Smart Content Services weiterhin nutzen.
>* Smart Content Services ist für bestehende Kunden von [!DNL Experience Manager Assets] Managed Services verfügbar, für die diese Funktion bereits aktiviert ist.
>* Neue Kunden von [!DNL Experience Manager Assets] Managed Services können die in diesem Artikel beschriebenen Anweisungen zum Einrichten von Smart Content Services befolgen.

Bevor Sie den Smart Content Service verwenden, führen Sie Folgendes aus:

* [Integrieren Sie ihn mit der Adobe Developer Console](#integrate-adobe-io).
* [Trainieren Sie den Smart Content Service](#training-the-smart-content-service).

* Installieren Sie die neueste Version des [[!DNL Experience Manager] Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

## Integrieren mit der Adobe Developer Console {#integrate-adobe-io}

Bei der Integration mit der Adobe Developer Console authentifiziert der [!DNL Experience Manager]-Server Ihre Service-Anmeldedaten beim Adobe Developer Console-Gateway, bevor er Ihre Anfrage an den Smart Content Service weiterleitet. Zur Integration benötigen Sie ein Adobe ID-Konto mit Administratorrechten für die für Ihr Unternehmen erworbene und aktivierte Smart Content Service-Lizenz.

Gehen Sie wie folgt vor, um den Smart Content Service zu konfigurieren:

1. Um einen öffentlichen Schlüssel zu erzeugen, [erstellen Sie in [!DNL Experience Manager] eine Smart Content Service](#obtain-public-certificate)-Konfiguration. [Erlangen Sie ein öffentliches Zertifikat](#obtain-public-certificate) für die OAuth-Integration.

1. [Erstellen Sie eine Integration in der Adobe Developer Console](#create-adobe-i-o-integration) und laden Sie den generierten öffentlichen Schlüssel hoch.

1. [Konfigurieren Sie die Bereitstellung](#configure-smart-content-service) mithilfe des API-Schlüssels und der anderen Anmeldedaten aus der Adobe Developer Console.

1. [Testen Sie die Konfiguration](#validate-the-configuration).

1. Optional können Sie [das automatische Tagging beim Hochladen eines Assets aktivieren](#enable-smart-tagging-in-the-update-asset-workflow-optional).

### Abrufen eines öffentlichen Zertifikats durch Erstellen der Konfiguration des Smart Content Service {#obtain-public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in der Adobe Developer Console.

1. Greifen Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Ältere Cloud Services]** zu.

1. Klicken Sie auf der Seite „Cloud Services“ unter **[!UICONTROL Assets Smart Tags]** auf **[!UICONTROL Jetzt konfigurieren]**.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Service-URL]**: `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`

   Beispiel: `https://smartcontent.adobe.io/apac`. Sie können `na`, `emea` oder `apac` als die Regionen angeben, in denen Ihre Experience Manager-Autoreninstanz gehostet wird.

   >[!NOTE]
   >
   >Wenn der Experience Manager Managed Service vor dem 1. September 2022 bereitgestellt wurde, verwenden Sie die folgende Service-URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld von Experience Manager Smart Content Service zum Bereitstellen der Content Service-URL](assets/aem_scs.png)


   *Abbildung: Dialogfeld von Content Service zum Bereitstellen der Content Service-URL*

   >[!NOTE]
   >
   >Die als [!UICONTROL Service-URL] angegebene URL ist über den Browser nicht erreichbar und erzeugt einen 404-Fehler. Die Konfiguration funktioniert problemlos mit demselben Wert für den [!UICONTROL Service-URL]-Parameter. Informationen zum Gesamtstatus und Wartungszeitplan für den Service finden Sie unter [https://status.adobe.com](https://status.adobe.com).

1. Klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]** und laden Sie die öffentliche Zertifikatdatei `AEM-SmartTags.crt` herunter.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/smart-tags-download-public-cert.png)


   *Abbildung: Einstellungen für den Smart-Tagging-Service.*

#### Erneutes Konfigurieren, wenn ein Zertifikat abläuft {#certrenew}

Wenn ein Zertifikat abläuft, ist es nicht mehr vertrauenswürdig. Sie können ein abgelaufenes Zertifikat nicht verlängern. Um ein Zertifikat hinzuzufügen, führen Sie diese Schritte aus.

1. Melden Sie sich bei Ihrer [!DNL Experience Manager]-Bereitstellung als Administrator an. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.

1. Löschen Sie den vorhandenen Keystore **[!UICONTROL Similaritysearch]** mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag der Ähnlichkeitssuche in KeyStore, um ein Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)


   *Abbildung: Löschen des vorhandenen `similaritysearch`-Eintrags in Keystore, um ein Sicherheitszertifikat hinzuzufügen.*

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.

1. Gehen Sie zu [https://console.adobe.io](https://console.adobe.io) und dann zu den vorhandenen Smart Content Services auf der Seite **[!UICONTROL Integrationen]**. Laden Sie das neue Zertifikat hoch. Weitere Informationen finden Sie in den Anweisungen unter [Erstellen einer Integration in der Adobe Developer Console](#create-adobe-i-o-integration).

### Erstellen einer Integration in der Adobe Developer Console {#create-adobe-i-o-integration}

Um die Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in der Adobe Developer Console, um den [!UICONTROL API-Schlüssel] (der im Feld [!UICONTROL CLIENT-ID] der Adobe Developer Console-Integration generiert wird), die [!UICONTROL ID DES TECHNISCHEN KONTOS], die [!UICONTROL ORGANISATIONS-ID] und das [!UICONTROL CLIENT-GEHEIMNIS] für die [!UICONTROL Smart Tagging Service-Einstellungen für Assets] der Cloud-Konfiguration in [!DNL Experience Manager].

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Organisationsrolle „Systemadministrator“ ist.

1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie auf der Seite **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL Öffentlichen Schlüssel hochladen]** aus. Stellen Sie die von [!DNL Experience Manager] heruntergeladenen Zertifikatdatei bereit. Die Meldung [!UICONTROL Öffentliche(r) Schlüssel erfolgreich hochgeladen] wird angezeigt. Klicken Sie auf **[!UICONTROL Weiter]**.

   Die Seite [!UICONTROL Neue Dienstkonto (JWT)-Anmeldedaten erstellen] zeigt den öffentlichen Schlüssel für das Dienstkonto an.

1. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie auf der Seite **[!UICONTROL Produktprofile auswählen]** die Option **[!UICONTROL Smart Content Services]** aus. Klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite geöffnet, um diese Werte zu kopieren und in den [!UICONTROL Einstellungen des Smart Tagging Service für Assets] in der Cloud-Konfiguration in [!DNL Experience Manager] zuzufügen, um Smart Tags zu konfigurieren.

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)


   *Abbildung: Integrationsdetails in der Adobe Developer Console*

### Konfigurieren des Smart Content Service {#configure-smart-content-service}

>[!CAUTION]
>
>Zuvor mit JWT-Anmeldedaten erstellte Konfigurationen werden in der Adobe Developer Console jetzt nicht mehr unterstützt. Nach dem 3. Juni 2024 können Sie keine neuen JWT-Anmeldedaten mehr erstellen. Solche Konfigurationen können nicht mehr erstellt oder aktualisiert werden, können aber zu OAuth-Konfigurationen migriert werden.
> Siehe [Einrichten von IMS-Integrationen für AEM](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)
>Siehe [Schritte zum Konfigurieren von OAuth für On-Premise-Benutzende](#config-oauth-onprem)
> Siehe [Fehlerbehebung für Smart-Tags hinsichtlich OAuth-Anmeldedaten](#config-smart-tagging.md)

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder [!UICONTROL ID DES TECHNISCHEN KONTOS], [!UICONTROL ORGANISATIONS-ID], [!UICONTROL CLIENT-GEHEIMNIS] und [!UICONTROL CLIENT-ID] aus der Adobe Developer Console-Integration. Das Erstellen einer Smart-Tags-Cloud-Konfiguration ermöglicht die Authentifizierung von API-Anfragen aus der [!DNL Experience Manager]-Bereitstellung.

1. Gehen Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Ältere Cloud-Services]**, um die [!UICONTROL Cloud Services]-Konsole zu öffnen.

1. Öffnen Sie unter **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite „Diensteinstellungen“ auf **[!UICONTROL Bearbeiten]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.

1. Für die Felder [!UICONTROL API-Schlüssel], [!UICONTROL ID des Technischen Kontos], [!UICONTROL Organisations-ID] und [!UICONTROL Client-Geheimnis], kopieren und verwenden Sie die folgenden Werte, die in [Integration der Adobe Developer Console](#create-adobe-i-o-integration) generiert wurden.

   | [!UICONTROL Diensteinstellungen für Smart-Tagging in Assets] | [!DNL Adobe Developer Console] Integrationsfelder |
   |--- |--- |
   | [!UICONTROL API-Schlüssel] | [!UICONTROL CLIENT-ID] |
   | [!UICONTROL ID des technischen Kontos] | [!UICONTROL  ID DES TECHNISCHEN KONTOS] |
   | [!UICONTROL Organisations-ID] | [!UICONTROL ORGANISATIONS-ID] |
   | [!UICONTROL Client-Geheimnis] | [!UICONTROL CLIENT-GEHEIMNIS] |

### Konfigurieren von OAuth für On-Premise-Benutzende {#config-oauth-onprem}

#### Voraussetzungen {#prereqs-config-oauth-onprem}

Ein Autorisierungsumfang ist eine OAuth-Zeichenfolge, die die folgenden Voraussetzungen enthält:

* Erstellen Sie in der [Developer Console](https://developer.adobe.com/console/user/servicesandapis) eine neue OAuth-Integration mit `ClientID`, `ClientSecretID` und `OrgID`.
* Fügen Sie unter dem Pfad `/apps/system/config in crx/de` die folgenden Dateien hinzu:
   * `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

#### Konfigurieren von OAuth für On-Premise-Benutzende {#steps-config-oauth-onprem}

1. Fügen Sie in `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config` die folgenden Eigenschaften hinzu oder aktualisieren Sie sie:

   * `auth.token.provider.authorization.grants="client_credentials"`
   * `auth.token.provider.orgId="<OrgID>"`
   * `auth.token.provider.default.claims=("\"iss\"\ :\ \"<OrgID>\"")`
   * `auth.token.provider.scope="read_pc.dma_smart_content,\ openid,\ AdobeID,\ additional_info.projectedProductContext"`
     `auth.token.validator.type="adobe-ims-similaritysearch"`
   * Aktualisieren Sie die `auth.token.provider.client.id` mit der Client-ID der neuen OAuth-Konfiguration.
   * Ändern Sie die Angabe für `auth.access.token.request` in `"https://ims-na1.adobelogin.com/ims/token/v3"`.
2. Benennen Sie die Datei in `com.adobe.granite.auth.oauth.accesstoken.provider-<randomnumber>.config` um.
3. Führen Sie in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config` die folgenden Schritte aus:
   * Aktualisieren Sie die Eigenschaft „auth.ims.client.secret“ mit dem Client-Geheimnis aus der neuen OAuth-Integration.
   * Benennen Sie die Datei in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl-<randomnumber>.config` um.
4. Speichern Sie alle Änderungen in der Entwicklungskonsole des Content-Repositorys, z. B. CRXDE.
5. Navigieren Sie zu `/system/console/configMgr` und ändern Sie die OSGi-Konfiguration von `.<randomnumber>` in `-<randomnumber>`.
6. Löschen Sie die alte Konfiguration für `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr`.
7. Starten Sie die Konsole neu.

### Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie unter `https://[aem_server]:[port]` auf Ihren [!DNL Experience Manager]-Server zu.

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**, um die OSGi-Konsole zu öffnen. Klicken Sie auf **[!UICONTROL Main] > [!UICONTROL JMX]**.

1. Klicken Sie auf `com.day.cq.dam.similaritysearch.internal.impl`. Die Seite **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** wird geöffnet

1. Klicken Sie auf `validateConfigs()`. Klicken Sie im Dialogfeld **[!UICONTROL Konfigurationen prüfen]** auf **[!UICONTROL Aufrufen]**.

Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

### Aktivieren der Smart-Tagging-Funktion im Workflow [!UICONTROL DAM Update Asset] (optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Gehen Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** das Workflow-Modell **[!UICONTROL DAM Update Asset]** aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Asset intelligent taggen]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Abbildung: Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „[!UICONTROL DAM-Update-Asset]“.*

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![Konfigurieren des Workflows „DAM-Update-Asset“ und Hinzufügen des Schritts „;Smart-Tag“](assets/smart-tag-step-properties-workflow1.png)


   *Abbildung: Konfigurieren des Workflows „DAM-Update-Asset“ und Hinzufügen des Schritts „Smart-Tag“*

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![Konfigurieren des Workflows „DAM Update Asset“, um den Schritt „Smart-Tag“ hinzuzufügen und den erweiterten Handler-Modus auszuwählen](assets/smart-tag-step-properties-workflow2.png)


   *Abbildung: Konfigurieren des Workflows „DAM Update Asset“, um den Schritt „Smart-Tag“ hinzuzufügen und den erweiterten Handler-Modus auszuwählen*

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Markierung ignorieren]** aus.

   ![Konfigurieren des Workflows „DAM Update Asset“, um den Schritt „Smart-Tag“ hinzuzufügen und „Smart-Tag-Markierung ignorieren“ auszuwählen](assets/smart-tag-step-properties-workflow3.png)


   *Abbildung: Konfigurieren des Workflows „DAM Update Asset“, um den Schritt „Smart-Tag“ hinzuzufügen und „Smart-Tag-Markierung ignorieren“ auszuwählen*

1. Klicken Sie auf **[!UICONTROL OK]**, um den Prozessschritt zu schließen, und speichern Sie dann den Workflow.

## Trainieren des Smart Content Service {#training-the-smart-content-service}

Damit der Smart Content Service die Taxonomie Ihres Unternehmens erkennen kann, sollten Sie den Dienst auf einen Asset-Satz ausführen, der bereits für Ihr Unternehmen relevante Tags enthält. Damit Sie Ihre Markenbilder effektiv mit Tags versehen können, müssen die zum Trainieren des Smart Content Service verwendeten Bilder bestimmten Richtlinien entsprechen. Nach dem Training kann der Dienst dieselbe Taxonomie auf einen ähnlichen Satz von Assets anwenden.

Sie können den Dienst mehrmals trainieren, um die Fähigkeit zu verbessern, relevante Tags anzuwenden. Führen Sie nach jedem Trainings-Zyklus einen Tagging-Workflow aus und überprüfen Sie, ob Ihre Assets mit den richtigen Tags versehen sind.

Sie können den Smart Content Service regelmäßig oder bei Bedarf trainieren.

>[!NOTE]
>
>Der Trainings-Workflow wird nur für Ordner ausgeführt.

### Richtlinien für das Training {#guidelines-for-training}

Für optimale Ergebnisse sollten Bilder im Trainingssatz folgende Richtlinien einhalten:

**Menge und Größe:** Mindestens 30 Bilder pro Tag. Mindestens 500 Pixel auf der längeren Seite.

**Kohärenz**: Bilder, die für ein bestimmtes Tag verwendet werden, sind optisch ähnlich.

So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainings-Zwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass Experience Manager lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein.

Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainings-Bilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Service ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Service kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt).

Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Beispiel: Fügen Sie im Falle von Tags wie `raincoat` und `model-side-view` beide Tags zum entsprechenden Asset hinzu, bevor Sie dieses für Trainingszwecke verwenden.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Die Fähigkeit des Smart Content Service, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab. Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Service für die einzelnen Tags zu trainieren.

### Regelmäßiges Training {#periodic-training}

Sie können festlegen, dass der Smart Content Service regelmäßig mit den Assets und zugewiesenen Tags in einem Ordner trainiert wird. Öffnen Sie die Seite [!UICONTROL Eigenschaften] Ihres Asset-Ordners, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** in der Registerkarte **[!UICONTROL Details]** aus und speichern Sie die Änderungen.

![enable_smart_tags](assets/enable_smart_tags.png)

Wenn Sie diese Option für einen Ordner auswählt haben, führt [!DNL Experience Manager] automatisch einen Trainings-Workflow aus, um den Smart Content Service mit den Assets im Ordner und deren Tags zu trainieren. Standardmäßig wird der Trainings-Workflow jede Woche samstags um 00:30 Uhr ausgeführt.

### Training bei Bedarf {#on-demand-training}

Sie können den Smart Content Service bei Bedarf über die Workflow-Konsole trainieren.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.
1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** nach dem Payload-Ordner, der die mit Tags versehenen Assets für das Trainieren des Services enthält.
1. Geben Sie einen Titel für den Workflow an und fügen Sie einen Kommentar hinzu. Klicken Sie dann auf **[!UICONTROL Ausführen]**. Die Assets und Tags werden für das Training übermittelt.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Wenn die Assets in einem Ordner für das Training verarbeitet wurden, werden für zukünftige Trainingszyklen nur die modifizierten Assets verarbeitet.

### Anzeigen von Trainings-Berichten {#viewing-training-reports}

Um sicherzustellen, dass der Smart Content Service auf Ihre Tags im Asset-Trainingssatz trainiert ist, überprüfen Sie den Bericht zum Trainings-Workflow über die Berichte-Konsole.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.
1. Klicken Sie auf der Seite **[!UICONTROL Asset-Berichte]** auf **[!UICONTROL Erstellen]**.
1. Wählen Sie den Bericht **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. Um den Bericht anzuzeigen, klicken Sie in der Symbolleiste auf **[!UICONTROL Ansicht]**.
1. Prüfen Sie die Details des Berichts.

   Der Bericht zeigt den Trainings-Status der von Ihnen trainierten Tags an. Grün gibt in der Spalte **[!UICONTROL Trainingsstatus]** an, dass der Smart Content Service für das Tag trainiert wird. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren.

   Wenn Ihre Tags nicht in diesem Bericht angezeigt werden, führen Sie den Trainings-Workflow für diese Tags erneut aus.

1. Um den Bericht herunterzuladen, wählen Sie ihn aus der Liste aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**. Der Bericht kann als Microsoft Excel-Tabellenkalkulation heruntergeladen werden.

## Beschränkungen {#limitations}

* Optimiertes Smart-Tagging basiert auf Lernmodellen von Bildern und den zugehörigen Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version des Smart Content Service bestehen folgende Einschränkungen:

   * Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: T-Shirts mit schmalem oder normalem Schnitt.
   * Tags können nicht anhand von winzigen Mustern oder Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
   * Tagging wird in den Gebietsschemata unterstützt, in denen [!DNL Experience Manager] unterstützt wird.

* Verwenden Sie [!DNL Assets]-OmniSearch (Volltextsuche), um nach Assets mit Smart-Tags (normal oder erweitert) zu suchen. Es gibt kein separates Suchprädikat für Smart-Tags.

>[!MORELIKETHIS]
>
>* [Überblick über Smart Tags und deren Training](enhanced-smart-tags.md)
>* [Fehlerbehebung für Smart-Tags hinsichtlich OAuth-Anmeldedaten](config-oauth.md)
>* [Video-Tutorial zu Smart-Tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=de)
