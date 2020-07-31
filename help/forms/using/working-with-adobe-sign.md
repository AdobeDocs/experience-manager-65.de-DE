---
title: Verwenden von Adobe Sign in einem adaptiven Formular
seo-title: Verwenden von Adobe Sign in einem adaptiven Formular
description: Indem Sie Workflows mit e-Signatur (Adobe Sign) für ein adaptives Formular aktivieren, können Sie Signatur-Workflows automatisieren, Prozesse mit einer oder mehreren Signaturen vereinfachen und Formulare elektronisch von Mobilgeräten aus signieren.
seo-description: Indem Sie Workflows mit e-Signatur (Adobe Sign) für ein adaptives Formular aktivieren, können Sie Signatur-Workflows automatisieren, Prozesse mit einer oder mehreren Signaturen vereinfachen und Formulare elektronisch von Mobilgeräten aus signieren.
uuid: cc3012ed-c318-4529-9adc-61aa5b5761a0
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: f79828d8-2230-4477-8ffa-eeb6a0413acd
docset: aem65
translation-type: tm+mt
source-git-commit: 70052a5a8cba16dd2d73179e6e1d617347d716bc
workflow-type: tm+mt
source-wordcount: '3679'
ht-degree: 64%

---


# Verwenden von Adobe Sign in einem adaptiven Formular{#using-adobe-sign-in-an-adaptive-form}

Adobe Sign ermöglicht Workflows mit e-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Szenario mit Adobe Sign und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Beispielsweise sind für einen Hypotheken- und oder Kreditkartenantrag rechtskräftige Signaturen von allen Kreditnehmern und Mitantragstellern erforderlich. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren. Einige weitere Anwendungsbeispiele für Adobe Sign sind:

* Geschäftsabschlüsse von jedem Gerät aus mit vollautomatischen Prozessen für Vorschlag, Angebot und Vertrag.
* Schnelleres Abschließen von Prozessen im Personalwesen und Zugang zu digitalen Abläufen für Ihre Mitarbeiter.
* Kürzere Vertragszyklen und schnelleres Onboarding Ihrer Lieferanten.
* Erstellen digitaler Workflows zur Automatisierung häufig verwendeter Prozesse.

Die Integration von Adobe Sign in AEM Forms unterstützt die folgenden Funktionen:

* Workflows für Signaturen eines einzelnen oder mehrerer Benutzer
* Workflows mit sequenzieller und simultaner Signatur
* Abläufe für Signaturen innerhalb und außerhalb des Formulars
* Signieren von Formularen als anonymer oder angemeldeter Benutzer
* Dynamische Signaturvorgänge (Integration mit AEM Forms-Workflow)
* Authentifizierung über eine Wissensdatenbank, ein Telefon und soziale Profile

## Voraussetzungen {#prerequisites}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie Adobe Sign in einem adaptiven Formular verwenden:

* Vergewissern Sie sich, dass der AEM Forms-Cloud-Service für die Verwendung von Adobe Sign konfiguriert ist. Weitere Informationen finden Sie unter [Integrieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).
* Halten Sie die Liste der Unterzeichner bereit. Sie benötigen mindestens eine E-Mail-Adresse für jeden Unterzeichner.

## Adobe Sign für adaptive Formulare konfigurieren {#configure-adobe-sign-for-an-adaptive-form}

Führen Sie die folgenden Schritte durch, um Adobe Sign für adaptive Formulare zu konfigurieren:

1. [Eigenschaften von adaptiven Formularen für Adoben bearbeiten](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-Felder zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign für adaptives Formular aktivieren](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Cloud-Service von Adobe Sign für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Senden-Aktion für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![Details zum Unterzeichner](assets/signer_details_new.png)

### Adaptive Formulareigenschaften für Adobe Sign bearbeiten {#enableadobesign}

Konfigurieren Sie die Eigenschaften adaptiver Formulare für Adobe Sign für ein vorhandenes oder ein neues adaptives Formular.

[Erstellen eines adaptiven Formulars für Adobe Sign](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) beschreibt die Schritte zum Erstellen eines grundlegenden adaptiven Formulars. Weitere Optionen, die beim Erstellen eines adaptiven Formulars verfügbar sind, finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md) .

#### Erstellen eines adaptiven Formulars für Adobe Sign {#create-an-adaptive-form-for-adobe-sign}

Führen Sie die folgenden Schritte aus, um ein signaturfähiges adaptives Formular zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Adaptives Formular]**. Eine Liste von Vorlagen wird angezeigt. Select the template and tap **[!UICONTROL Next]**.
1. In the **[!UICONTROL Basic]** tab:

   1. Geben Sie den **Namen** und den **Titel** für das adaptive Formular an.

   1. Wählen Sie den [Configuration Container](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von Adobe Sign mit AEM Forms erstellt wurde.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen aus:

   * Wählen Sie die Option &quot;Formularvorlage **[!UICONTROL zuordnen&quot;als Dokument der Datensatzvorlage]** und wählen Sie ein Dokument der Datensatzvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden nur die Dokumente, die zum Unterschreiben gesendet werden, angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   * Wählen Sie die Option &quot;Dokument aus Datensatz **[!UICONTROL generieren&quot;]** . Wenn Sie ein adaptives Formular mit aktivierter Option &quot;Dokument aus Datensatz&quot;verwenden, zeigt das zum Unterschreiben gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Erstellen.]** Es wird ein adaptives Formular mit aktiviertem Zeichen erstellt, das zum Hinzufügen von Adobe Sign-Feldern verwendet werden kann.

#### Bearbeiten eines adaptiven Formulars für Adobe Sign {#editafsign}

Führen Sie die folgenden Schritte aus, um Adobe Sign in einem vorhandenen adaptiven Formular zu verwenden:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.
1. Select the adaptive form and tap **[!UICONTROL Properties]**.
1. Wählen Sie auf der Registerkarte &quot; **[!UICONTROL Einfach]** &quot;den [Konfigurationsordner](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von Adobe Sign mit AEM Forms erstellt wurde.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodus]** eine der folgenden Optionen aus:

   * Wählen Sie die Option &quot;Formularvorlage **[!UICONTROL zuordnen&quot;als Dokument der Datensatzvorlage]** und wählen Sie ein Dokument der Datensatzvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden nur die Dokumente, die zum Unterschreiben gesendet werden, angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   * Wählen Sie die Option &quot;Dokument aus Datensatz **[!UICONTROL generieren&quot;]** . Wenn Sie ein adaptives Formular mit aktivierter Option &quot;Dokument aus Datensatz&quot;verwenden, zeigt das zum Unterschreiben gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Speichern und Schließen]**. Das adaptive Formular ist für Adobe Sign aktiviert.

### Adobe Sign-Felder zu adaptivem Formular hinzufügen {#addadobesignfieldstoanadaptiveform}

Adobe Sign verfügt über verschiedene Felder, die in einem adaptiven Formular platziert werden können. In diese Felder können verschiedene Datentypen wie Signaturen, Initialen, Firma oder Titel eingegeben. Sie helfen dabei, beim Unterschreiben zusätzliche Informationen zusammen mit den Signaturen zu erfassen. Sie können die Adobe Sign Block-Komponente verwenden, um Adobe Sign-Felder an verschiedenen Stellen in einem adaptiven Formular zu platzieren.

Gehen Sie wie folgt vor, um einem adaptiven Formular Felder hinzuzufügen und eine Reihe von Optionen für diese Felder anzupassen:

1. Ziehen Sie die Komponente **Adobe Sign Block** aus dem Komponentenbrowser in das adaptive Formular. Die Adobe Sign Block-Komponente enthält alle unterstützten Adobe Sign-Felder. By default, it adds a **Signature** field to the adaptive form.

   ![Signaturblock](assets/sign_block_new.png)

   Standardmäßig ist der Adobe Sign Block im veröffentlichten adaptiven Formular nicht sichtbar. Er wird nur in den Signaturdokumenten angezeigt. Sie können die Sichtbarkeit von Adobe Sign Block in den Eigenschaften der Adobe Sign Block-Komponente ändern.

   >[!NOTE]
   >
   >    * Für die Verwendung von Adobe Sign in einem adaptiven Formular ist Adobe Sign Block nicht zwingend erforderlich. Wenn Sie den Adobe Sign-Block nicht verwenden und keine Felder für die Unterzeichner hinzufügen, wird das Standardunterschriftsfeld unten in den unterschreibenden Dokumenten angezeigt.
   >    * Verwenden Sie den Adobe Sign-Block nur für adaptive Formulare, die automatisch ein Datensatzdokument generieren. Wenn Sie das Datensatzdokument mithilfe einer benutzerdefinierten XDP-Datei generieren oder ein formularvorlagenbasiertes adaptives Formular verwenden, wird Adobe Sign nicht benötigt.


1. Select the **Adobe Sign Block** component and tap the **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) icon. Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Wählen Sie Adobe Sign-Felder aus und fügen Sie sie hinzu. **B.** Erweitern des Adobe Sign-Blocks auf Ansicht im Vollbildmodus

1. Tippen Sie auf das Symbol **Adobe Sign Field** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) . Optionen zum Auswählen und Hinzufügen von Adobe Sign-Feldern werden angezeigt.

   Expand the **Type** drop-down field to select a Adobe Sign field and tap the Done ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) icon to add the selected field to Adobe Sign block. Die Dropdown-Liste **Typ** enthält die Feldtypen Signatur, Signiererinformationen und Daten. Die Integration von Adobe Sign in AEM Forms unterstützt nur die in der Dropdown-Liste „Typ“ angegebenen Felder. Ausführliche Informationen zu Adobe Sign-Feldern finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   Es ist obligatorisch, einen eindeutigen Namen für ein Feld anzugeben. Sie können auch die Option „Erforderlich“ aktivieren, um ein Feld als Pflichtfeld zu markieren. Für manche Adobe Sign-Felder stehen außer den Optionen **Name** und **Erforderlich** weitere Optionen verfügbar. Dies kann z. B. Maske oder mehrzeilig sein. Geben Sie außerdem eindeutige Namen für die einzelnen Adobe Sign-Felder an, unabhängig davon, ob diese Felder sich im selben oder in verschiedenen Adobe Sign-Blöcken befinden.

   Wenn Sie in der Dropdown-Liste &quot; **Digitale Signatur** &quot;auswählen, können Sie dem adaptiven Formular digitale Signaturen zuweisen:

   * Online mit Cloud-Signaturen zur Unterzeichnung mit einer [digitalen ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) , die von einem Trust-Dienstleister gehostet wird.
   * Lokal durch Herunterladen des Dokuments mit Adobe Acrobat oder Reader mit einer Chipkarte, einem USB-Token oder einer dateibasierten digitalen ID.

### Adobe Sign für adaptives Formular aktivieren {#enableadobsignforanadaptiveform}

Adobe Sign ist standardmäßig nicht für adaptive Formulare aktiviert. Gehen Sie wie folgt vor, um es zu aktivieren:

1. In the Content browser, tap **Form Container**, and tap the **Configure** ![configure](assets/configure.png) icon. Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.

### Cloud-Service von Adobe Sign und Signaturreihenfolge wählen {#selectadobesigncloudserviceforanadaptiveform}

Sie können mehrere Adobe Sign-Dienste für eine Instanz von AEM Forms konfigurieren. Es empfiehlt sich, für jede Funktion (Personalwesen, Finanzen usw.) eine eigene Gruppe von Diensten zu verwenden. Dies erleichtert die Verfolgung und Berichterstellung für signierte Dokumente. So könnte beispielsweise eine Bank mehrere Abteilungen umfassen. In diesem Fall können Sie für jede Abteilung eine eigene Konfiguration einrichten, damit die Dokumente leichter zu verfolgen sind.

Ein Dokument kann auch mehrere Unterzeichner haben. Beispielsweise können bei einem Kreditkartenantrag mehrere Antragsteller vorhanden sein. Die Bank benötigt die Unterschriften aller Antragsteller, bevor sie mit der Bearbeitung beginnt. Bei Szenarien mit mehreren Unterzeichnern können Sie wählen, ob diese das Dokument nacheinander oder simultan unterschreiben sollen.

Führen Sie die folgenden Schritte aus, um einen Cloud-Service und die Reihenfolge für die Unterzeichnung zu wählen:

![cloud-service](assets/cloud-service.png)

1. In the Content browser, tap **Form Container**, and tap the **Configure** ![configure](assets/configure.png) icon. Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.
1. Wählen Sie einen Cloud-Dienst aus der bereits konfigurierten Liste der Adobe Sign Cloud-Services aus.

   Wenn die Liste der **Cloud-Services von Adobe Sign** leer ist, befolgen Sie die Anweisungen zum [Konfigurieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md), um den Dienst zu konfigurieren.

1. Wählen Sie die Signaturreihenfolge im Dialogfeld **Benutzer können signieren**. Adobe Sign-Unterzeichner können ein adaptives Formular **sequenziell**, d. h. nacheinander, oder **simultan** in beliebiger Reihenfolge unterschreiben.

   Bei sequenzieller Reihenfolge erhält jeder Unterzeichner das Formular einzeln. Nachdem ein Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter.

   Bei simultaner Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.

1. [Hinzufügen Sie Unterzeichner zu einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) und tippen Sie auf das Symbol Fertig [aem_6_3_forms_save](assets/aem_6_3_forms_save.png) , um die Änderungen zu speichern.


### Unterzeichner zu adaptivem Formular hinzufügen {#addsignerstoanadaptiveform}

Sie können für ein adaptives Formular nur einen oder mehrere Unterzeichner festlegen. Wenn Sie einen Unterzeichner hinzufügen, können Sie außerdem Authentifizierungsdetails für den Unterzeichner konfigurieren. Sie können auch wählen, ob die Person, die das Formular ausfüllt, zugleich der Unterzeichner sein muss. Führen Sie die folgenden Schritte durch, um einen Unterzeichner hinzuzufügen und seine Details anzugeben:

1. In the Content browser, tap **Form Container**, and tap the **Configure** ![configure](assets/configure.png) icon. Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.
1. Tippen Sie auf **Unterscheibende Person hinzufügen** unter **Signiererkonfiguration**. Es wird ein Unterzeichner zum adaptiven Formular hinzugefügt. Sie können dem adaptiven Formular mehreren Adobe Sign-Unterzeichner hinzufügen.
1. ![phone-details](assets/phone-details.png)

   Click the **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) icon to specify the following information about the signer:

   * **Titel:** Geben Sie einen Titel an, um einen Unterzeichner eindeutig zu identifizieren.

   * **Sind der Unterzeichner und die Person, die das Formular ausfüllt, identisch?:** Wählen Sie **Ja**, wenn Formularbenutzer und erster Unterzeichner dieselbe Person sind. Wenn für die Option **Nein** eingestellt ist, können Sie die Komponente für den Signaturschritt nicht im adaptiven Formular verwenden. Wenn die Komponente für „Unterschriftsschritt“ im Formular enthalten ist, wird automatisch „Ja“ für das Feld festgelegt.

   * **E-Mail-Adresse der unterzeichnenden Person:** Geben Sie die E-Mail-Adresse des Unterzeichners an. Der Unterzeichner erhält die zu unterschreibenden Dokumente/das Formular unter der angegebenen E-Mail-Adresse. Sie können eine E-Mail-Adresse verwenden, die in einem Formularfeld im AEM-Benutzerprofil des angemeldeten Benutzers angegeben ist, oder manuell eine E-Mail-Adresse eingeben. Dieser Schritt ist obligatorisch. Vergewissern Sie sich, dass die E-Mail-Adresse des ersten Unterzeichners oder des einzigen Unterzeichners (bei einem einzigen Unterzeichner) nicht mit dem Adobe Sign-Konto, das zum Konfigurieren der AEM cloud services verwendet wird, identisch ist.

   * **Authentifizierungsmethode für unterzeichnende Person:** Geben Sie die Methode zum Authentifizieren eines Benutzers an, bevor Sie ein Formular zum Signieren öffnen. Sie können die Authentifizierung per Telefon, Wissensdatenbank und Profil in sozialem Netzwerk wählen.
   >[!NOTE]
   >
   >    * Bei der Authentifizierung über soziale Netzwerke steht standardmäßig eine Option zum Authentifizieren über Facebook, Google und LinkedIn zur Verfügung. Wenden Sie sich an den Adobe Sign-Support, wenn Sie weitere Anbieter von Authentifizierung über soziale Netzwerke aktivieren möchten.


   * **Auszufüllende oder zu unterzeichnende Adobe Sign Felder:** Wählen Sie die Adobe Sign-Felder für den Unterzeichner. Ein adaptives Formular kann mehrere Adobe Sign-Felder umfassen. Sie können bestimmte Felder für einen bestimmten Unterzeichner aktivieren. Das Feld zeigt alle verfügbaren Adobe Sign-Blöcke an. Wenn Sie einen Block auswählen, werden alle Felder des Blocks ausgewählt. Über das X-Symbol können Sie die Auswahl eines Feldes aufheben.

   ![signer-details](assets/signer-details.png)

   Die Abbildung oben zeigt zwei Adobe Sign-Blöcke als Beispiel: Personal-Information und Office-details

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) . Der Unterzeichner wird hinzugefügt und konfiguriert.

### Senden-Aktion für adaptives Formular wählen {#selectsubmitactionforanadaptiveform}

Nachdem Sie dem adaptiven Formular Adobe Sign-Felder hinzugefügt, Adobe Sign über den Formular-Container aktiviert, den Cloud-Service von Adobe Sign gewählt und Adobe Sign-Unterzeichner hinzugefügt haben, wählen Sie die geeignete Übermittlungsaktion für das adaptive Formular. Ausführliche Informationen zu Übermittlungsaktionen für adaptive Formulare finden Sie unter [Konfigurieren der Übermittlungsaktion](../../forms/using/configuring-submit-actions.md).

Ein für Adobe Sign aktiviertes adaptives Formular wird darüber hinaus erst übermittelt, nachdem alle Unterzeichner es signiert haben. Teilweise signierte Formulare finden Sie im Abschnitt „Ausstehende Signatur“ im Forms-Portal. Der Adobe Sign Configuration Service fragt den Adobe Sign-Server in [regelmäßige Abständen](../../forms/using/adobe-sign-integration-adaptive-forms.md) ab, um den Status der Signaturen zu überprüfen. Wenn alle Unterzeichner das Formular signiert haben, wird der Dienst für die Übermittlungsaktion gestartet und das Formular übermittelt. Wenn Sie eine benutzerdefinierte Übermittlungsaktion verwenden und Adobe Sign im Formular verwendet wird, aktualisieren Sie Ihre benutzerdefinierte Übermittlungsaktion, sodass der Dienst für die Übermittlungsaktion verwendet wird.

>[!NOTE]
>
>Die Daten des adaptiven Formulars werden vorübergehend im Forms-Portal gespeichert. Wir empfehlen, [benutzerdefinierten Speicher für das Forms-Portal](/help/forms/using/configuring-draft-submission-storage.md) zu verwenden. Dadurch wird sichergestellt, dass keine persönlichen Daten (PII) auf AEM-Servern gespeichert werden.

Damit ist der Ablauf zur Formularunterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen. Im veröffentlichten Formular werden die Felder des Adobe Sign-Blocks angezeigt, wenn ein Unterzeichner das Formular per E-Mail zum Unterschreiben erhält. Diese Erfahrung wird auch als Signieren außerhalb des Formulars bezeichnet. Sie können auch einen Ablauf zum Signieren innerhalb des Formulars für den ersten Unterzeichner konfigurieren. Eine detaillierte Anleitung finden Sie unter [Formularinternen Signaturvorgang erstellen](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Cloud-Signaturen für ein adaptives Formular konfigurieren {#configure-cloud-signatures-for-an-adaptive-form}

Cloud-basierte digitale Signaturen oder Remote-Signaturen sind eine neue Generation digitaler Signaturen, die über Desktop, Mobilgeräte und das Web funktioniert — und die höchste Kompatibilitätsstufe und die höchste Sicherheit für die Signiererauthentifizierung erfüllen. Sie können ein adaptives Formular mit Cloud-basierten digitalen Signaturen signieren.

Nachdem Sie die Eigenschaften des adaptiven Formulars für das Signieren [der Adobe](../../forms/using/working-with-adobe-sign.md#enableadobesign)bearbeitet haben, führen Sie die folgenden Schritte aus, um einem adaptiven Formular ein Cloud-Signaturfeld hinzuzufügen:

1. Ziehen Sie die Komponente **Adobe Sign Block** aus dem Komponentenbrowser in das adaptive Formular. Die Adobe Sign Block-Komponente enthält alle unterstützten Adobe Sign-Felder. By default, it adds a **Signature** field to the adaptive form.

   ![Signaturblock](assets/sign-block-new.png)

1. Select the **Adobe Sign Block** component and tap the **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) icon. Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Wählen Sie Adobe Sign-Felder aus und fügen Sie sie hinzu. **B.** Erweitern des Adobe Sign-Blocks auf Ansicht im Vollbildmodus

1. Tippen Sie auf das Symbol **Adobe Sign Field** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) . Optionen zum Auswählen und Hinzufügen von Adobe Sign-Feldern werden angezeigt.

   Expand the **Type** drop-down field to select **Digital Signature** and tap the Done icon to add the selected field to Adobe Sign block.

   ![Digitale Signaturen](assets/digital_signatures_new.png)

   Es ist obligatorisch, einen eindeutigen Namen für ein Feld anzugeben.

   Anwenden digitaler Signaturen auf das adaptive Formular mit:

   * Cloud-Signaturen: Signieren Sie mit einer [digitalen ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) , die von einem Trust-Dienstleister gehostet wird.
   * Adobe Acrobat oder Reader: Laden Sie das Dokument mit Adobe Acrobat oder Reader herunter und öffnen Sie es, um sich mit einer Chipkarte, einem USB-Token oder einer dateibasierten digitalen ID zu signieren.

   Nachdem Sie das Cloud-Signaturfeld zum adaptiven Formular hinzugefügt haben, führen Sie die folgenden Schritte aus, um den Konfigurationsprozess abzuschließen:

   * [Adobe Sign für adaptives Formular aktivieren](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Cloud-Service von Adobe Sign für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Senden-Aktion für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)


## Formularinternen Signaturvorgang erstellen {#create-in-form-signing-experience}

Ein Benutzer kann ein adaptives Formular beim Ausfüllen auch signieren. Diese Erfahrung wird auch formularinternes Signieren bezeichnet. Dieser Ablauf steht nur für den ersten Unterzeichner in einer Umgebung mit mehreren Unterzeichnern zur Verfügung. Gehen Sie Führen Sie die folgenden Schritte aus, um einen Ablauf für formularinternes Signieren für ein adaptives Formular zu erstellen:

1. [Fügen Sie die Komponente für Signaturschritt hinzu und konfigurieren Sie sie](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. [Fügen Sie die Komponente für Übersichtsschritt hinzu](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component).

![Formularsignaturerlebnis](assets/in_form_signing_experience_new.png)

### Komponente für Signaturschritt hinzufügen und konfigurieren {#add-and-configure-the-signature-step-component}

Mit der Komponente für Signaturschritt können Sie einen Bereich für die elektronische Unterschrift unter dem ausgefüllten Formular bereitstellen. Bei der Ausgabe des Abschnitts mit der Komponente für Signaturschritt wird eine signierbare PDF-Version des ausgefüllten Formulars angezeigt. Die Signaturschritt-Komponente nimmt die volle für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Signaturschritt-Komponente enthält.

Führen Sie die folgenden Schritte aus, um die Signaturschritt-Komponente zu konfigurieren:

1. Ziehen Sie die Komponente **Unterschriftsschritt** aus dem Komponentenbrowser in das Formular.
1. Select the newly added Signature step component and tap the **Configure** ![configure](assets/configure.png) icon. Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Signaturschritts an. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.

   * **Titel:** Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht:** Geben Sie die Nachricht an, die angezeigt werden soll, während die Signatur-PDF geladen wird. Die Adobe Sign-Dienste benötigen einige Zeit, um Signatur-PDF vorzubereiten und zu laden.
   * **Signaturdienst:** Wählen Sie die Option **Adobe Sign** aus.

   * **Frühere E-Sign-Komponente verwenden:** Wenn Sie das entsprechende adaptive Formular in [AEM Forms Workspace](../../forms/using/introduction-html-workspace.md) oder die AEM Forms-App verwenden oder das zugrunde liegende adaptive Formular eine ältere E-Sign-Komponente enthält, wählen Sie die Option **Legacy-E-Sign-Komponente verwenden**.

   * **Konfiguration**: Wählen Sie eine Konfiguration (Adobe Sign Cloud Service). Diese Dropdown-Liste ist nur verfügbar, wenn die Option **Frühere E-Sign Komponente verwenden** aktiviert ist.

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) , um die Änderungen zu speichern.

   ![Unterschriftsschritt](assets/signature_step_new.png)

   >[!NOTE]
   >
   > * Wenn Sie die Komponente **[!UICONTROL Unterschriftsschritt]** in das Formular ziehen und dort ablegen, wird für die Option **[!UICONTROL Wird das Formular von derselben Person ausgefüllt und unterzeichnet?]** automatisch **Ja** festgelegt. Dies ist für die Funktionsfähigkeit des Formulars erforderlich.
      >
      > 
   * Verwenden Sie die Komponente Zusammenfassungsschritt nach der Komponente Unterschriftsschritt, um ein optimales Erlebnis zu erhalten. Der Schritt &quot;Zusammenfassung&quot;sendet das Formular automatisch und sofort, nachdem Sie die Unterzeichnung eines Formulars in der Komponente &quot;Unterschriftsschritt&quot;abgeschlossen haben. Wenn Sie den Übersichtsschritt nicht verwenden, wird eine automatische Übermittlung erst nach dem mit dem [Adobe Sign-Konfigurationsdienst](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status)festgelegten Intervall ausgelöst.
   > * Einige bewährte Verfahren sind:
   > * Das Bedienfeld für adaptive Formulare, das den Unterschriftsschritt enthält, befindet sich immer im letzten oder zweiten Bereich eines adaptiven Formulars. Es kann nur dann der zweite letzte Bereich sein, wenn das letzte Bedienfeld den Übersichtsschritt enthält.
   > * Das Bedienfeld, das die Komponente &quot;Signature&quot;oder &quot;Summary&quot;enthält, kann keine andere Komponente enthalten.
   > * Bei adaptiven Formularen mit Unterschriftsschritt kann keine Senden-Schaltfläche verwendet werden. Die Übermittlung erfolgt über einen Hintergrunddienst oder den Übersichtsschritt.
   > * Entwerfen Sie das Formular, damit Benutzer nicht von einem Bereich mit dem Schritt &quot;Unterschrift&quot;oder &quot;Zusammenfassung&quot;zurück navigieren können.



### Komponente für Danksagungsseite oder Zusammenfassungsschritt konfigurieren {#configure-the-thank-you-page-or-summary-step-component}

Die Komponente **Zusammenfassungsschritt** übermittelt automatisch das Formular, füllt die Informationen auf der angepassten Zusammenfassungsseite aus und zeigt die Zusammenfassung des übermittelten Formulars an. Sie ruft darüber hinaus die erforderlichen Informationen in der Rückgabezuordnung ab. Die Komponente &quot;Zusammenfassungsschritt&quot;nimmt die volle Breite ein, die für das Formular verfügbar ist. Es wird empfohlen, keine andere Komponente im Abschnitt mit der Komponente Zusammenfassungsschritt zu verwenden.

Damit ist der Ablauf zur formularinternen Unterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen.

## Häufig gestellte Fragen {#frequently-asked-questions}

**A:** Nein. Die Verwendung von adaptiven Formularen, in die für die Unterzeichnung ein für Adobe Sign aktiviertes adaptives Formular eingebettet ist, wird in AEM Forms nicht unterstützt.

**A:** Adaptive Formulare, die die erweiterte Vorlage nutzen, sind für die Verwendung von Adobe Sign konfiguriert. Um den Fehler zu beheben, erstellen  Sie eine Adobe Sign Cloud-Konfiguration, wählen Sie sie aus und konfigurieren Sie einen Adobe Sign-Unterzeichner für das adaptive Formular.

**A:** Ja, Sie können Text-Tags in einer Textkomponente verwenden, um Adobe Sign-Felder einem adaptiven Formular mit [Datensatzdokument](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) hinzuzufügen (nur Option für automatisch generiertes Datensatzdokument). Informationen zu den Verfahren und Regeln zum Erstellen eines Text-Tags finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/de/sign/help/text-tags.html). Beachten Sie außerdem, dass adaptive Formulare Text-Tags nur begrenzt unterstützen. Sie können die Text-Tags verwenden, um nur die von [Adobe Sign Block](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) unterstützten Felder zu erstellen.

**Antwort:** Sie können beide Komponenten gleichzeitig in einem Formular verwenden. Beachten Sie die folgenden Empfehlungen für die Verwendung dieser Komponenten:

**Adobe Sign Block:** Mit dem Adobe Sign-Block können Sie Adobe Sign-Felder an beliebigen Stellen im adaptiven Formular hinzufügen. Dies ermöglicht es auch, den Unterzeichnern bestimmte Felder zuzuweisen. Bei der Vorschau oder Veröffentlichung eines adaptiven Formulars ist Adobe Sign Block standardmäßig nicht sichtbar. Diese Blöcke werden nur in den Signaturdokumenten angezeigt. Im Signaturdokument sind nur die einem Unterzeichner zugewiesenen Felder aktiviert. Der Adobe Sign-Block für den ersten und die folgenden Unterzeichner verwendet werden.

**Signaturschrittkomponente:** Sie können die Signaturschrittkomponente verwenden, um eine formularinterne Signaturfunktion zu erstellen. Damit kann nur der erste Unterzeichner unterschreiben, während das Formular ausgefüllt wird. Bei der Ausgabe des Abschnitts mit der Signaturschritt-Komponente wird eine signierbare PDF-Version des Formulars angezeigt. In der Regel ist dies der letzte oder der vorletzte Abschnitt, auf den die Übersichtskomponente eines Formulars folgt.

## Fehlerbehebung {#troubleshoot}

### Adobe Sign-Abkommen versagt {#adobe-sign-agreement-failures}

**Problem** Wenn der Adobe Sign-Dienst für ein adaptives Formular konfiguriert ist, kann vom Dienst keine Adobe Sign-Vereinbarung für das zugrunde liegende adaptive Formular erstellt werden.

**Auflösung**

* Überprüfen Sie die [Konfiguration des Adobe Sign Cloud-Dienstes](../../forms/using/adobe-sign-integration-adaptive-forms.md) , der im adaptiven Formular verwendet wird.
* Stellen Sie sicher, dass die API-Anwendung auf dem Adobe Sign-Server, die zum Konfigurieren des Adobe Sign Cloud-Dienstes verwendet wird, über die erforderlichen Berechtigungen verfügt.
* Wenn Sie mehrere Adobe Sign Cloud-Dienste verwenden, weisen Sie die **[!UICONTROL Auth-URL]** aller Dienste auf denselben **[!UICONTROL Adobe Sign-Store]** hin.

* Verwenden Sie separate E-Mail-Adressen, um das Adobe Sign-Konto und den ersten Unterzeichner und einen einzelnen Unterzeichner zu konfigurieren. Die E-Mail-Adresse des ersten Unterzeichners oder des einzigen Unterzeichners (im Falle eines einzelnen Unterzeichners) kann nicht mit dem Adobe Sign-Konto identisch sein, das zur Konfiguration der AEM cloud services verwendet wird.

## Related Articles {#related-articles}

* [Integrieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)

* [Verwenden von Adobe Sign mit AEM Forms (Video)
   ](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
