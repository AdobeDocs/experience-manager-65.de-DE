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
feature: Adaptive Forms, Adobe Sign
exl-id: a8decba9-229d-40a2-992a-3cc8ebefdd6d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3863'
ht-degree: 38%

---

# Verwenden von [!DNL Adobe Sign] in einem adaptiven Formular{#using-adobe-sign-in-an-adaptive-form}

[!DNL Adobe Sign] aktiviert Workflows für die elektronische Signatur für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Szenario mit [!DNL Adobe Sign] und adaptiven Formularen füllt ein Benutzer ein adaptives Formular aus, um einen Dienst zu beantragen. Beispielsweise sind für einen Hypotheken- und oder Kreditkartenantrag rechtskräftige Signaturen von allen Kreditnehmern und Mitantragstellern erforderlich. Um Workflows für elektronische Signaturen für ähnliche Szenarien zu aktivieren, können Sie [!DNL Adobe Sign] in AEM [!DNL Forms] integrieren. Ein paar weitere Beispiele sind [!DNL Adobe Sign], um:

* Geschäftsabschlüsse von jedem Gerät aus mit vollautomatischen Prozessen für Vorschlag, Angebot und Vertrag.
* Schnelleres Abschließen von Prozessen im Personalwesen und Zugang zu digitalen Abläufen für Ihre Mitarbeiter.
* Kürzere Vertragszyklen und schnelleres Onboarding Ihrer Lieferanten.
* Erstellen digitaler Workflows zur Automatisierung häufig verwendeter Prozesse.

[!DNL Adobe Sign] Integration mit AEM  [!DNL Forms] unterstützt:

* Workflows für Signaturen eines einzelnen oder mehrerer Benutzer
* Workflows mit sequenzieller und simultaner Signatur
* Abläufe für Signaturen innerhalb und außerhalb des Formulars
* Signieren von Formularen als anonymer oder angemeldeter Benutzer
* Dynamische Signierungsprozesse (Integration mit AEM [!DNL Forms]-Workflow)
* Authentifizierung über eine Wissensdatenbank, ein Telefon und soziale Profile

Lernen Sie die [Best Practices für die Verwendung von Adobe Sign mit adaptiven Formularen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) kennen, um bessere Signiererlebnisse zu erstellen.

## Voraussetzungen {#prerequisites}

Vor der Verwendung von [!DNL Adobe Sign] in einem adaptiven Formular:

* Stellen Sie sicher, AEM der Cloud-Service [!DNL Forms] für die Verwendung von [!DNL Adobe Sign] konfiguriert ist. Weitere Informationen finden Sie unter [Integrieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).
* Halten Sie die Liste der Unterzeichner bereit. Sie benötigen mindestens eine E-Mail-Adresse für jeden Unterzeichner.

## [!DNL Adobe Sign] für ein adaptives Formular {#configure-adobe-sign-for-an-adaptive-form} konfigurieren

Führen Sie die folgenden Schritte aus, um [!DNL Adobe Sign] für ein adaptives Formular zu konfigurieren:

1. [Bearbeiten von Eigenschaften des adaptiven Formulars für Adobe-Sign](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-Felder zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign für adaptives Formular aktivieren](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Cloud-Service von Adobe Sign für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Senden-Aktion für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![Signiererdetails](assets/signer_details_new.png)

### Bearbeiten der Eigenschaften des adaptiven Formulars für [!DNL Adobe Sign] {#enableadobesign}

Konfigurieren Sie die Eigenschaften des adaptiven Formulars für [!DNL Adobe Sign] für ein vorhandenes oder ein neues adaptives Formular.

[Erstellen eines adaptiven Formulars für Adobe ](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) Signature beschreibt die Schritte zum Erstellen eines einfachen adaptiven Formulars. Weitere Optionen, die beim Erstellen eines adaptiven Formulars verfügbar sind, finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md) .

#### Erstellen eines adaptiven Formulars für [!DNL Adobe Sign] {#create-an-adaptive-form-for-adobe-sign}

Führen Sie die folgenden Schritte aus, um ein signierfähiges adaptives Formular zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Adaptives Formular]**. Eine Liste mit Vorlagen wird angezeigt. Wählen Sie die Vorlage aus und tippen Sie auf **[!UICONTROL Weiter]**.
1. Auf der Registerkarte **[!UICONTROL Basic]** :

   1. Geben Sie **[!UICONTROL Name]** und **[!UICONTROL Titel]** für das adaptive Formular an.

   1. Wählen Sie den [Konfigurationscontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von [!DNL Adobe Sign] mit AEM [!DNL Forms] erstellt wurde.

      >[!NOTE]
      >
      >Die Dropdownliste **[!UICONTROL Adobe Sign Cloud Service]** enthält die Cloud-Services, die im Konfigurationscontainer konfiguriert sind, den Sie in diesem Feld auswählen. Die Dropdown-Liste **[!UICONTROL Adobe Sign Cloud Service]** ist im Abschnitt **[!UICONTROL Elektronische Signatur]** der Eigenschaften des adaptiven Formulars verfügbar, wenn Sie die Option **[!UICONTROL Adobe Sign]** aktivieren auswählen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen aus:

   * Wählen Sie die Option **[!UICONTROL Formularvorlage als Datensatzdokumentvorlage zuordnen]** und wählen Sie eine Datensatzdokumentvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden in den zum Signieren gesendeten Dokumenten nur die Felder angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   * Wählen Sie die Option **[!UICONTROL Generate Document of Record]** aus. Wenn Sie ein adaptives Formular verwenden, für das die Option &quot;Datensatzdokument&quot;aktiviert ist, zeigt das zum Signieren gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Erstellen.]** Es wird ein adaptives Formular erstellt, das für die Anmeldung aktiviert ist und das zum Hinzufügen von  [!DNL Adobe Sign] Feldern verwendet werden kann.

#### Bearbeiten eines adaptiven Formulars für [!DNL Adobe Sign] {#editafsign}

Führen Sie die folgenden Schritte aus, um [!DNL Adobe Sign] in einem vorhandenen adaptiven Formular zu verwenden:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]**.
1. Wählen Sie das adaptive Formular aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Basic]** den [Konfigurationscontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von [!DNL Adobe Sign] mit AEM [!DNL Forms] erstellt wurde.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen aus:

   * Wählen Sie die Option **[!UICONTROL Formularvorlage als Datensatzdokumentvorlage zuordnen]** und wählen Sie eine Datensatzdokumentvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden in den zum Signieren gesendeten Dokumenten nur die Felder angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   * Wählen Sie die Option **[!UICONTROL Generate Document of Record]** aus. Wenn Sie ein adaptives Formular verwenden, für das die Option &quot;Datensatzdokument&quot;aktiviert ist, zeigt das zum Signieren gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Speichern und Schließen]**. Das adaptive Formular ist für [!DNL Adobe Sign] aktiviert.

### Adobe Sign-Felder zu adaptivem Formular hinzufügen {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign] verfügt über verschiedene Felder, die in einem adaptiven Formular platziert werden können. In diese Felder können verschiedene Datentypen wie Signaturen, Initialen, Firma oder Titel eingegeben. Sie helfen dabei, beim Unterschreiben zusätzliche Informationen zusammen mit den Signaturen zu erfassen. Sie können die Komponente [!DNL Adobe Sign] Block verwenden, um [!DNL Adobe Sign]-Felder an verschiedenen Stellen in einem adaptiven Formular zu platzieren.

Gehen Sie wie folgt vor, um einem adaptiven Formular Felder hinzuzufügen und eine Reihe von Optionen für diese Felder anzupassen:

1. Ziehen Sie die Komponente **[!UICONTROL Adobe Sign Block]** aus dem Komponentenbrowser in das adaptive Formular. Die Komponente [!DNL Adobe Sign] Block verfügt über alle unterstützten Felder [!DNL Adobe Sign] . Standardmäßig wird das Feld **Signature** zum adaptiven Formular hinzugefügt.

   ![Signaturblock](assets/sign_block_new.png)

   Standardmäßig ist der Block [!DNL Adobe Sign] im veröffentlichten adaptiven Formular nicht sichtbar. Er wird nur in den Signaturdokumenten angezeigt. Sie können die Sichtbarkeit von [!DNL Adobe Sign] Block in den Eigenschaften der Block-Komponente [!DNL Adobe Sign] ändern.

   >[!NOTE]
   >
   >    * Die Verwendung des Blocks [!DNL Adobe Sign] ist nicht erforderlich, um [!DNL Adobe Sign] in einem adaptiven Formular zu verwenden. Wenn Sie den Block [!DNL Adobe Sign] nicht verwenden und Felder für die Unterzeichner hinzufügen, wird das Standard-Unterschriftsfeld unten in den Unterschriftsdokumenten angezeigt.
   >    * Verwenden Sie den Block [!DNL Adobe Sign] nur für adaptive Formulare, die automatisch Datensatzdokument generieren. Wenn Sie eine benutzerdefinierte XDP zum Generieren des Datensatzdokuments oder eines auf einer Formularvorlage basierenden adaptiven Formulars verwenden, wird der Block [!DNL Adobe Sign] nicht unterstützt.


1. Wählen Sie die Komponente **[!UICONTROL Adobe Sign Block]** aus und tippen Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png). Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Wählen Sie  [!DNL Adobe Sign] Felder aus und fügen Sie sie hinzu. **B.** Erweitern Sie den  [!DNL Adobe Sign] Block in die Vollbildansicht.

1. Tippen Sie auf das Symbol **[!UICONTROL Adobe Sign] Field** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png). Es werden Optionen zum Auswählen und Hinzufügen von [!DNL Adobe Sign]-Feldern angezeigt.

   Erweitern Sie das Dropdown-Feld **[!UICONTROL Typ]** , um ein [!DNL Adobe Sign]-Feld auszuwählen, und tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) , um das ausgewählte Feld zum Block [!DNL Adobe Sign] hinzuzufügen. Die Dropdown-Liste **[!UICONTROL Typ]** enthält die Feldtypen Signatur, Signiererinformationen und Daten. [!DNL Adobe Sign] Integration mit AEM  [!DNL Forms] Supportfeldern, die nur im   Dropdown-Feld Typedrop-down aufgeführt sind. Ausführliche Informationen zu [!DNL Adobe Sign]-Feldern finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   Es ist erforderlich, einen eindeutigen Namen für ein Feld anzugeben. Sie können auch die Option „Erforderlich“ aktivieren, um ein Feld als Pflichtfeld zu markieren. Zusätzlich zur Option **[!UICONTROL Name]** und **[!UICONTROL Erforderlich]** verfügen einige [!DNL Adobe Sign]-Felder über weitere Optionen. Dies kann z. B. Maske oder mehrzeilig sein. Geben Sie außerdem für jedes [!DNL Adobe Sign]-Feld einen eindeutigen Namen an, unabhängig davon, ob sich die Felder in denselben oder unterschiedlichen [!DNL Adobe Sign]-Blöcken befinden.

   Wenn Sie **[!UICONTROL Digital Signature]** aus der Dropdownliste auswählen, können Sie digitale Signaturen auf das adaptive Formular anwenden:

   * Online mit Cloud-Signaturen zur Signierung mit einer [digitalen ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html), die von einem Trust Service Provider gehostet wird.
   * Lokal durch Herunterladen des Dokuments mit Adobe Acrobat oder Reader mithilfe einer Smart-Karte, eines USB-Tokens oder einer dateibasierten digitalen ID.

### [!DNL Adobe Sign] für ein adaptives Formular aktivieren {#enableadobsignforanadaptiveform}

Standardmäßig ist [!DNL Adobe Sign] nicht für ein adaptives Formular aktiviert. Gehen Sie wie folgt vor, um es zu aktivieren:

1. Tippen Sie im Inhaltsbrowser auf **[!UICONTROL Formular-Container]** und tippen Sie auf das Symbol **[!UICONTROL Konfigurieren]** ![Konfigurieren](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **[!UICONTROL Elektronische Signatur]** und wählen Sie die Option **[!UICONTROL Adobe Sign aktivieren]**. Sie aktiviert [!DNL Adobe Sign] für ein adaptives Formular.

### Wählen Sie den Cloud Service [!DNL Adobe Sign] und die Unterschriftsreihenfolge aus. {#selectadobesigncloudserviceforanadaptiveform}

Sie können mehrere [!DNL Adobe Sign]-Dienste für eine Instanz von AEM [!DNL Forms] konfigurieren. Es wird empfohlen, für jede Funktion (Humanressourcen, Finanzen usw.) einen separaten Satz an Diensten zu verwenden. Das Tracking und Reporting signierter Dokumente wird vereinfacht. Eine Bank verfügt beispielsweise über mehrere Abteilungen. In diesem Fall können Sie für jede Abteilung eine eigene Konfiguration einrichten, damit die Dokumente leichter zu verfolgen sind.

Ein Dokument kann auch mehrere Unterzeichner haben. Beispielsweise kann ein Kreditkartenantrag mehrere Antragsteller umfassen. Die Bank benötigt die Unterschriften aller Antragsteller, bevor sie mit der Bearbeitung beginnt. Bei Szenarien mit mehreren Unterzeichnern können Sie wählen, ob diese das Dokument nacheinander oder simultan unterschreiben sollen.

Führen Sie die folgenden Schritte aus, um einen Cloud-Service und die Reihenfolge für die Unterzeichnung zu wählen:

![Cloud-Service](assets/cloud-service.png)

1. Tippen Sie im Inhaltsbrowser auf **[!UICONTROL Formular-Container]** und tippen Sie auf das Symbol **[!UICONTROL Konfigurieren]** ![Konfigurieren](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **[!UICONTROL Elektronische Signatur]** und wählen Sie die Option **[!UICONTROL Adobe Sign aktivieren]**. Sie aktiviert [!DNL Adobe Sign] für ein adaptives Formular.
1. Wählen Sie einen Cloud-Dienst aus der bereits konfigurierten Liste der Cloud Services [!DNL Adobe Sign] aus.

   Wenn die Liste **[!UICONTROL Adobe Sign Cloud Service]** leer ist, befolgen Sie den Artikel [Adobe Sign mit AEM Forms konfigurieren](../../forms/using/adobe-sign-integration-adaptive-forms.md) , um den Dienst zu konfigurieren.

   In der Dropdown-Liste werden die Cloud-Services aufgelistet, die im Ordner `global` unter Tools > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** vorhanden sind. Darüber hinaus werden in der Dropdown-Liste auch die Cloud-Dienste aufgelistet, die in dem Ordner vorhanden sind, den Sie beim Erstellen eines adaptiven Formulars im Feld **[!UICONTROL Konfigurations-Container]** auswählen.

1. Wählen Sie die Signaturreihenfolge im Dialogfeld **[!UICONTROL Benutzer können signieren]**. [!DNL Adobe Sign] -Sänger können ein adaptives Formular in beliebiger Reihenfolge  **[!UICONTROL sequenziell]**  - nacheinander oder  **[!UICONTROL gleichzeitig]**  - signieren.

   Bei sequenzieller Reihenfolge erhält jeder Unterzeichner das Formular einzeln. Nachdem ein Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter.

   Bei simultaner Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.

1. [Fügen Sie einem adaptiven ](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) Formular Unterzeichner hinzu und tippen Sie auf das Symbol Fertig  ![aem_6_3_forms_](assets/aem_6_3_forms_save.png) saveicon , um die Änderungen zu speichern.


### Unterzeichner zu adaptivem Formular hinzufügen {#addsignerstoanadaptiveform}

Sie können für ein adaptives Formular nur einen oder mehrere Unterzeichner festlegen. Wenn Sie einen Unterzeichner hinzufügen, können Sie außerdem Authentifizierungsdetails für den Unterzeichner konfigurieren. Sie können auch wählen, ob die Person, die das Formular ausfüllt, zugleich der Unterzeichner sein muss. Führen Sie die folgenden Schritte durch, um einen Unterzeichner hinzuzufügen und seine Details anzugeben:

1. Tippen Sie im Inhaltsbrowser auf **[!UICONTROL Formular-Container]** und tippen Sie auf das Symbol **[!UICONTROL Konfigurieren]** ![Konfigurieren](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **[!UICONTROL Elektronische Signatur]** und wählen Sie die Option **[!UICONTROL Adobe Sign aktivieren]**. Sie aktiviert [!DNL Adobe Sign] für ein adaptives Formular.
1. Tippen Sie auf **[!UICONTROL Unterscheibende Person hinzufügen]** unter **[!UICONTROL Signiererkonfiguration]**. Dadurch wird dem adaptiven Formular ein Unterzeichner hinzugefügt. Sie können mehrere [!DNL Adobe Sign] Unterzeichner zu einem adaptiven Formular hinzufügen.
   ![phone-details](assets/phone-details.png)

1. Klicken Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png) , um die folgenden Informationen zum Unterzeichner anzugeben:

   * **[!UICONTROL Titel]:**  Geben Sie einen Titel an, um einen Unterzeichner eindeutig zu identifizieren.

   * **[!UICONTROL Sind der Unterzeichner und die Person, die das Formular ausfüllt, identisch?]** Wählen Sie  **Ja**, wenn der Formularbenutzer und der erste Unterzeichner dieselbe Person sind. Wenn für die Option **Nein** eingestellt ist, können Sie die Komponente für den Signaturschritt nicht im adaptiven Formular verwenden. Wenn das Formular eine Signaturschritt-Komponente enthält, wird für das Feld automatisch &quot;Ja&quot;festgelegt.

   * **[!UICONTROL Unterzeichner-E-Mail-Adresse]:**  Geben Sie die E-Mail-Adresse des Unterzeichners an. Der Unterzeichner erhält die zu unterschreibenden Dokumente/das Formular unter der angegebenen E-Mail-Adresse. Sie können eine E-Mail-Adresse verwenden, die in einem Formularfeld im AEM-Benutzerprofil des angemeldeten Benutzers angegeben ist, oder manuell eine E-Mail-Adresse eingeben. Dieser Schritt ist obligatorisch. Stellen Sie sicher, dass die E-Mail-Adresse des ersten Unterzeichners oder des einzigen Unterzeichners (im Fall eines einzelnen Unterzeichners) nicht mit dem [!DNL Adobe Sign]-Konto übereinstimmt, das zum Konfigurieren von AEM-Cloud-Services verwendet wurde.

   * **[!UICONTROL Authentifizierungsmethode für Unterzeichner]:**  Geben Sie die Methode an, um einen Benutzer zu authentifizieren, bevor Sie ein Formular zum Signieren öffnen. Sie können die Authentifizierung per Telefon, Wissensdatenbank und Profil in sozialem Netzwerk wählen.
   >[!NOTE]
   >
   >    * Bei der Authentifizierung über soziale Netzwerke steht standardmäßig eine Option zum Authentifizieren über Facebook, Google und LinkedIn zur Verfügung. Sie können sich an den [!DNL Adobe Sign]-Support wenden, um andere Anbieter sozialer Authentifizierung zu aktivieren.


   * **[!DNL Adobe Sign]Felder zum Ausfüllen oder Signieren:** Wählen Sie  [!DNL Adobe Sign] Felder für den Unterzeichner aus. Ein adaptives Formular kann mehrere [!DNL Adobe Sign] -Felder haben. Sie können bestimmte Felder für einen bestimmten Unterzeichner aktivieren. Das Feld zeigt alle verfügbaren [!DNL Adobe Sign] Blöcke an. Wenn Sie einen Block auswählen, werden alle Felder des Blocks ausgewählt. Über das X-Symbol können Sie die Auswahl eines Feldes aufheben.

   ![signer-details](assets/signer-details.png)

   Das obige Bild enthält zwei Beispiele für [!DNL Adobe Sign] Blöcke: Persönliche Informationen und Bürodetails

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) . Der Unterzeichner wird hinzugefügt und konfiguriert.

### Senden-Aktion für adaptives Formular wählen {#selectsubmitactionforanadaptiveform}

Nachdem Sie die Felder [!DNL Adobe Sign] in ein adaptives Formular eingefügt haben, aktivieren Sie [!DNL Adobe Sign] aus dem Formularcontainer, wählen Sie [!DNL Adobe Sign] Cloud Service und fügen Sie [!DNL Adobe Sign] Unterzeichner hinzu und wählen Sie eine geeignete Übermittlungsaktion für das adaptive Formular aus. Ausführliche Informationen zu Übermittlungsaktionen für adaptive Formulare finden Sie unter [Konfigurieren der Übermittlungsaktion](../../forms/using/configuring-submit-actions.md).

Außerdem wird ein [!DNL Adobe Sign] aktiviertes adaptives Formular erst gesendet, nachdem alle Unterzeichner das Formular signiert haben. Teilweise signierte Formulare finden Sie im Abschnitt „Ausstehende Signatur“ im Forms-Portal. [!DNL Adobe Sign] Configuration Service speichert den Abruf- [!DNL Adobe Sign] Server in  [regelmäßigen ](../../forms/using/adobe-sign-integration-adaptive-forms.md) Intervalle, um den Status von Signaturen zu überprüfen. Wenn alle Unterzeichner das Formular signiert haben, wird der Dienst für die Übermittlungsaktion gestartet und das Formular übermittelt. Wenn Sie eine benutzerdefinierte Übermittlungsaktion verwenden und das Formular [!DNL Adobe Sign] verwendet, aktualisieren Sie Ihre benutzerdefinierte Übermittlungsaktion, um den Übermittlungsaktion-Dienst zu verwenden.

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the adaptive form is stored temporarily on Forms Portal. It is recommended to use [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

Damit ist der Ablauf zur Formularunterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen. Im veröffentlichten Formular werden die Felder [!DNL Adobe Sign] Baustein angezeigt, wenn ein Unterzeichner das Formular zur Unterzeichnung per E-Mail erhält. Diese Erfahrung wird auch als Signieren außerhalb des Formulars bezeichnet. Sie können auch einen Ablauf zum Signieren innerhalb des Formulars für den ersten Unterzeichner konfigurieren. Eine detaillierte Anleitung finden Sie unter [Formularinternen Signaturvorgang erstellen](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Konfigurieren von Cloud-Signaturen für ein adaptives Formular {#configure-cloud-signatures-for-an-adaptive-form}

Cloud-basierte digitale Signaturen oder Remote-Signaturen sind eine neue Generation digitaler Signaturen, die auf dem Desktop, auf Mobilgeräten und im Internet funktionieren und die höchste Kompatibilität und Sicherheit für die Signiererauthentifizierung bieten. Sie können ein adaptives Formular mit Cloud-basierten digitalen Signaturen signieren.

Nachdem Sie [die Eigenschaften des adaptiven Formulars für das Adobe-Zeichen](../../forms/using/working-with-adobe-sign.md#enableadobesign) bearbeitet haben, führen Sie die folgenden Schritte aus, um einem adaptiven Formular ein Cloud-Signaturfeld hinzuzufügen:

1. Ziehen Sie die Komponente **[!UICONTROL Adobe Sign Block]** aus dem Komponentenbrowser in das adaptive Formular. Die Komponente [!UICONTROL Adobe Sign Block] enthält alle unterstützten Felder [!DNL Adobe Sign]. Standardmäßig wird das Feld **[!UICONTROL Signature]** zum adaptiven Formular hinzugefügt.

   ![Signaturblock](assets/sign-block-new.png)

1. Wählen Sie die Komponente **[!UICONTROL Adobe Sign Block]** aus und tippen Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png). Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Wählen Sie  [!DNL Adobe Sign] Felder aus und fügen Sie sie hinzu. **B.** Erweitern Sie den  [!DNL Adobe Sign] Block in die Vollbildansicht.

1. Tippen Sie auf das Symbol **[!UICONTROL Adobe Sign-Feld]** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) . Es werden Optionen zum Auswählen und Hinzufügen von [!DNL Adobe Sign]-Feldern angezeigt.

   Erweitern Sie das Dropdown-Feld **[!UICONTROL Typ]**, wählen Sie **[!UICONTROL Digitale Signatur]** aus und tippen Sie auf das Symbol **Fertig**, um das ausgewählte Feld zum Block [!DNL Adobe Sign] hinzuzufügen.

   ![Digitale Signaturen](assets/digital_signatures_new.png)

   Es ist erforderlich, einen eindeutigen Namen für ein Feld anzugeben.

   Anwenden digitaler Signaturen auf das adaptive Formular mithilfe von:

   * Cloud-Signaturen: Signieren Sie mit einer [digitalen ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html), die von einem Trust Service Provider gehostet wird.
   * Adobe Acrobat oder Reader: Laden Sie das Dokument herunter und öffnen Sie es mit Adobe Acrobat oder Reader, um es mit einer Smartcard, einem USB-Token oder einer dateibasierten digitalen ID zu signieren.

   Nachdem Sie das Cloud-Signaturfeld zum adaptiven Formular hinzugefügt haben, führen Sie die folgenden Schritte aus, um den Konfigurationsprozess abzuschließen:

   * [Adobe Sign für adaptives Formular aktivieren](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Cloud-Service von Adobe Sign für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Senden-Aktion für adaptives Formular wählen](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)


## Formularinternen Signaturvorgang erstellen {#create-in-form-signing-experience}

Ein Benutzer kann ein adaptives Formular beim Ausfüllen auch signieren. Diese Erfahrung wird auch formularinternes Signieren bezeichnet. Dieser Ablauf steht nur für den ersten Unterzeichner in einer Umgebung mit mehreren Unterzeichnern zur Verfügung. Gehen Sie Führen Sie die folgenden Schritte aus, um einen Ablauf für formularinternes Signieren für ein adaptives Formular zu erstellen:

1. [Fügen Sie die Komponente für Signaturschritt hinzu und konfigurieren Sie sie](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. [Fügen Sie die Komponente für Übersichtsschritt hinzu](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component).

![Formularinternes Signing-Erlebnis](assets/in_form_signing_experience_new.png)

### Komponente für Signaturschritt hinzufügen und konfigurieren {#add-and-configure-the-signature-step-component}

Mit der Komponente für Signaturschritt können Sie einen Bereich für die elektronische Unterschrift unter dem ausgefüllten Formular bereitstellen. Bei der Ausgabe des Abschnitts mit der Komponente für Signaturschritt wird eine signierbare PDF-Version des ausgefüllten Formulars angezeigt. Die Signaturschritt-Komponente nimmt die volle für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Signaturschritt-Komponente enthält.

Führen Sie die folgenden Schritte aus, um die Signaturschritt-Komponente zu konfigurieren:

1. Ziehen Sie die Komponente **[!UICONTROL Unterschriftsschritt]** aus dem Komponentenbrowser in das Formular.
1. Wählen Sie die neu hinzugefügte Signaturschritt-Komponente aus und tippen Sie auf das Symbol **Konfigurieren** ![Konfigurieren](assets/configure.png) . Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Signaturschritts an. Konfigurieren Sie die folgenden Eigenschaften:

   * **[!UICONTROL Name]**: Geben Sie den Namen der Komponente an.

   * **[!UICONTROL Titel]:**  Geben Sie den eindeutigen Titel der Komponente an.
   * **[!UICONTROL Vorlagennachricht]:**  Geben Sie die Nachricht an, die während des Ladens der Signatur-PDF angezeigt werden soll. [!DNL Adobe Sign] -Dienste benötigen einige Zeit, um Signatur-PDF vorzubereiten und zu laden.
   * **[!UICONTROL Signaturdienst]:** Wählen Sie die  **[!DNL Adobe Sign]** Option aus.

   * **[!UICONTROL Frühere E-Sign-Komponente verwenden:]** Wenn Sie das entsprechende adaptive Formular in [AEM Workspace](../../forms/using/introduction-html-workspace.md)[!DNL Forms] oder die AEM Forms-App verwenden oder das zugrunde liegende adaptive Formular eine ältere E-Sign-Komponente enthält, wählen Sie die Option **Legacy-E-Sign-Komponente verwenden**.

   * **[!UICONTROL Konfiguration]**: Wählen Sie eine Konfiguration ([!DNL Adobe Sign] Cloud Service) aus. Diese Dropdown-Liste ist nur verfügbar, wenn die Option **Frühere E-Sign Komponente verwenden** aktiviert ist.

   * **[!UICONTROL CSS-Klasse]**: Geben Sie die CSS-Klasse für die Komponente an.

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) , um die Änderungen zu speichern.

   ![Signaturschritt](assets/signature_step_new.png)

   >[!NOTE]
   >
   > * Wenn Sie die Komponente **[!UICONTROL Unterschriftsschritt]** in das Formular ziehen und dort ablegen, wird für die Option **[!UICONTROL Wird das Formular von derselben Person ausgefüllt und unterzeichnet?]** automatisch **Ja** festgelegt. Dies ist für die Funktionsfähigkeit des Formulars erforderlich.
      >
      > 
   * Verwenden Sie die Komponente Zusammenfassungsschritt nach der Signaturschritt , um ein optimales Erlebnis zu erzielen. Der Schritt &quot;Zusammenfassung&quot;sendet das Formular automatisch und sofort, nachdem Sie die Unterzeichnung eines Formulars in der Signaturschritt-Komponente abgeschlossen haben. Wenn Sie den Übersichtsschritt nicht verwenden, wird eine automatische Übermittlung erst nach dem mithilfe von [Adobe Sign Configuration Service](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status) festgelegten Intervall ausgelöst.
      > Einige Best Practices sind:
   > * Der Bereich des adaptiven Formulars, der den Schritt &quot;Signatur&quot;enthält, befindet sich immer im letzten oder zweiten letzten Bereich eines adaptiven Formulars. Es kann nur dann ein zweites letztes Bedienfeld sein, wenn das letzte Bedienfeld den Schritt Zusammenfassung enthält.
   > * Das Bedienfeld, das die Komponente für die Schritte &quot;Signatur&quot;oder &quot;Zusammenfassung&quot;enthält, darf keine andere Komponente enthalten.
   > * Adaptive Formulare, die Signaturschritt enthalten, können nicht über die Senden-Schaltfläche verfügen.
   > * Die Übermittlung für die adaptiven Formulare, die den Schritt &quot;Signatur&quot;enthalten, erfolgt über einen Hintergrunddienst oder den Schritt &quot;Zusammenfassung&quot;. Wenn es einen konfigurierten Unterzeichner gibt, der auch das Formular ausfüllt, besteht der Vorteil der Handhabung der Übermittlung des adaptiven Formulars mithilfe des Übersichtsschritts darin, dass sofort bewertet wird, ob der Unterzeichner das Formular signiert hat, und die Übermittlungsaktion aufgerufen wird. Ein Hintergrunddienst benötigt mehr Zeit, um zu überprüfen, ob alle konfigurierten Unterzeichner das Formular signiert haben, und verzögert die Übermittlung des adaptiven Formulars.
   > * Entwerfen Sie das Formular so, dass ein Benutzer nicht von einem Bedienfeld, das den Schritt &quot;Signatur&quot;oder &quot;Zusammenfassung&quot;enthält, zurück navigieren kann.



### Komponente für Danksagungsseite oder Zusammenfassungsschritt konfigurieren {#configure-the-thank-you-page-or-summary-step-component}

Die Komponente **Zusammenfassungsschritt** übermittelt automatisch das Formular, füllt die Informationen auf der angepassten Zusammenfassungsseite aus und zeigt die Zusammenfassung des übermittelten Formulars an. Sie ruft darüber hinaus die erforderlichen Informationen in der Rückgabezuordnung ab. Die Komponente &quot;Zusammenfassungsschritt&quot;nimmt die volle für das Formular verfügbare Breite ein. Es wird empfohlen, keine andere Komponente im Abschnitt zu haben, der die Komponente &quot;Zusammenfassungsschritt&quot;enthält.

Damit ist der Ablauf zur formularinternen Unterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen.

## Häufig gestellte Fragen {#frequently-asked-questions}

**F:** Sie können ein adaptives Formular in ein anderes adaptives Formular einbetten. Kann das eingebettete adaptive Formular [!DNL Adobe Sign] aktiviert sein?
**A:**[!DNL Forms] Nein. Die Verwendung von adaptiven Formularen, in die für die Unterzeichnung ein für aktiviertes adaptives Formular eingebettet ist, wird in AEM nicht unterstützt.[!DNL Adobe Sign]

**F:** Wenn ich ein adaptives Formular mithilfe der erweiterten Vorlage erstellen und es zur Bearbeitung öffnen möchte, wird die Fehlermeldung &quot;Elektronische Signatur oder Unterzeichner sind nicht richtig konfiguriert&quot; angezeigt. angezeigt. Wie behebe ich den Fehler?
**Antwort:** Adaptive Formulare, die mit der erweiterten Vorlage erstellt wurden, sind für die Verwendung konfiguriert  [!DNL Adobe Sign]. Um den Fehler zu beheben, erstellen und wählen Sie eine [!DNL Adobe Sign]-Cloud-Konfiguration und konfigurieren Sie einen [!DNL Adobe Sign]-Unterzeichner für das adaptive Formular.

**F:** Kann ich  [!DNL Adobe Sign] Text-Tags in einer statischen Textkomponente eines adaptiven Formulars verwenden?
**Antwort:** Ja, Sie können Text-Tags in einer Textkomponente verwenden, um  [!DNL Adobe Sign] Felder zu einem adaptiven Formular hinzuzufügen, das für das  [Datensatzdokument](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)  aktiviert ist (nur Option für automatisch generiertes Datensatzdokument). Informationen zu den Verfahren und Regeln zum Erstellen eines Text-Tags finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/sign/using/text-tag.html_de). Beachten Sie außerdem, dass adaptive Formulare Text-Tags nur begrenzt unterstützen. Sie können die Text-Tags verwenden, um nur die von [Adobe Sign Block](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) unterstützten Felder zu erstellen.

**F:** AEM  [!DNL Forms] stellt die Komponenten  [!UICONTROL Adobe Sign-] Blockade und Signaturschritt bereit. Können beide zusammen in einem adaptiven Formular verwendet werden?
**Antwort:** Sie können beide Komponenten gleichzeitig in einem Formular verwenden. Beachten Sie die folgenden Empfehlungen für die Verwendung dieser Komponenten:

**Adobe Sign-Block:** Sie können die  [!UICONTROL Adobe Sign-] Blockierung verwenden, um  [!UICONTROL Adobe-] Signaturfelder an einer beliebigen Stelle im adaptiven Formular hinzuzufügen. Dies ermöglicht es auch, den Unterzeichnern bestimmte Felder zuzuweisen. Wenn ein adaptives Formular in der Vorschau angezeigt oder veröffentlicht wird, ist [!UICONTROL Adobe Sign] Block standardmäßig nicht sichtbar. Diese Blöcke werden nur in den Signaturdokumenten angezeigt. Im Signaturdokument sind nur die einem Unterzeichner zugewiesenen Felder aktiviert. [!UICONTROL Der Adobe Sign-Block für den ersten und die folgenden Unterzeichner verwendet werden.]

**Signaturschrittkomponente:** Sie können die Signaturschrittkomponente verwenden, um eine formularinterne Signaturfunktion zu erstellen. Damit kann nur der erste Unterzeichner unterschreiben, während das Formular ausgefüllt wird. Bei der Ausgabe des Abschnitts mit der Signaturschritt-Komponente wird eine signierbare PDF-Version des Formulars angezeigt. In der Regel ist dies der letzte oder der vorletzte Abschnitt, auf den die Übersichtskomponente eines Formulars folgt.

## Fehlerbehebung {#troubleshoot}

### [!DNL Adobe Sign] Fehlgeschlagene Vereinbarungen  {#adobe-sign-agreement-failures}

****
ProblemWenn der  [!DNL Adobe Sign] Dienst für ein adaptives Formular konfiguriert ist, kann der Dienst keine  [!DNL Adobe Sign] Vereinbarung für das zugrunde liegende adaptive Formular erstellen.

**Auflösung**

* Überprüfen Sie die [Konfiguration des Adobe Sign-Cloud-Service](../../forms/using/adobe-sign-integration-adaptive-forms.md), der im adaptiven Formular verwendet wird.
* Stellen Sie sicher, dass die API-Anwendung auf dem [!DNL Adobe Sign]-Server, der zum Konfigurieren von [!DNL Adobe Sign] Cloud Service verwendet wird, über die erforderlichen Berechtigungen verfügt.
* Wenn Sie mehrere [!DNL Adobe Sign] Cloud-Dienste verwenden, verweisen Sie die **[!UICONTROL oAuth-URL]** aller Dienste auf denselben **[!UICONTROL Adobe Sign-Shard]**.

* Verwenden Sie separate E-Mail-Adressen, um das [!DNL Adobe Sign]-Konto sowie den ersten Unterzeichner und den einzelnen Unterzeichner zu konfigurieren. Die E-Mail-Adresse des ersten Unterzeichners oder des einzigen Unterzeichners (im Fall des einzelnen Unterzeichners) kann nicht mit dem [!DNL Adobe Sign]-Konto identisch sein, das zum Konfigurieren von AEM-Cloud-Services verwendet wird.

### AEM [!DNL Forms]-Workflow, der für ein [!DNL Adobe Sign] aktiviertes adaptives Formular konfiguriert ist, startet {#adobe-sign-aem-form-workflow-failures} nicht

****
ProblemWenn für ein adaptives Formular konfiguriert  [!DNL Adobe Sign] ist, startet der mit der Option  [!DNL Forms] Workflow aufrufen konfigurierte Workflow nicht.

**Auflösung**

* Wenn Sie [!DNL Adobe Sign] ohne den Unterschriftsschritt verwenden oder das Formular Unterschriften mehrerer Personen erfordert, wartet der Server AEM [!DNL Forms] darauf, dass der Planer bestätigt, dass alle Personen das Formular unterzeichnet haben. Der Planer sendet das adaptive Formular erst, nachdem die gesamte Person die Unterzeichnung abgeschlossen hat und der Workflow erst nach einer erfolgreichen Übermittlung des adaptiven Formulars beginnt. Sie können das Intervall von [scheduler](adobe-sign-integration-adaptive-forms.md) verkürzen, um den Status der Formularsignatur in kurzen Abständen zu überprüfen und die Formularübermittlung zu beschleunigen.


## Verwandte Artikel {#related-articles}

* [Integrieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [Best Practices für die Verwendung von Adobe Sign mit adaptiven Formularen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
