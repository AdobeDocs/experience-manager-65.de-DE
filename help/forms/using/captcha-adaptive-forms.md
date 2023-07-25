---
title: Verwenden von CAPTCHA in adaptiven Formularen
seo-title: Using CAPTCHA in adaptive forms
description: Erfahren Sie, wie Sie AEM CAPTCHA- oder Google reCAPTCHA-Dienst in adaptiven Formularen konfigurieren.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
feature: Adaptive Forms
exl-id: 9b4219b8-d5eb-4099-b205-d98d84e0c249
source-git-commit: 1ab5165dc87684918b33edabec133702b1f62663
workflow-type: tm+mt
source-wordcount: '1995'
ht-degree: 54%

---

# Verwenden von CAPTCHA in adaptiven Formularen{#using-captcha-in-adaptive-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/captcha-adaptive-forms.html) |
| AEM 6.5 | Dieser Artikel |


<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine Herausforderung dar und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms unterstützt CAPTCHA in adaptiven Formularen. Sie können den reCAPTCHA-Service von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>* AEM Forms unterstützt reCAPTCHA v2 und Enterprise. Es werden keine anderen Versionen unterstützt.
>* CAPTCHA in adaptiven Formularen wird im Offline-Modus in der AEM Forms-App nicht unterstützt.

## Konfigurieren des reCAPTCHA-Dienstes von Google für adaptive Forms {#google-reCAPTCHA}

AEM Forms-Benutzer können den reCAPTCHA-Dienst von Google verwenden, um CAPTCHA in adaptive Formulare zu implementieren. Es bietet erweiterte CAPTCHA-Funktionen zum Schutz Ihrer Site. Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/). Der reCAPTCHA-Dienst einschließlich reCAPTCHA v2 und reCAPTCHA Enterprise ist in AEM Forms integriert. Je nach Ihren Anforderungen können Sie den reCAPTCHA-Dienst konfigurieren, um Folgendes zu aktivieren:

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)

![reCAPTCHA](/help/forms/using/assets/recaptcha_new.png)

### reCAPTCHA Enterprise konfigurieren  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Erstellen Sie eine [reCAPTCHA Enterprise-Projekt](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) aktiviert mit [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. [Erhalten](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) die Projekt-ID.
1. Erstellen Sie eine [API-Schlüssel](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) und [Site-Schlüssel für Websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Erstellen Sie einen Konfigurations-Container für Cloud Services.

   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**. Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloudkonfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.
      1. Wählen Sie im Konfigurationsbrowser den Ordner **[!UICONTROL global]** und tippen Sie auf **[!UICONTROL Eigenschaften]**.
      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   1. Tippen Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloudkonfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.
1. Konfigurieren Sie den Cloud-Dienst für reCAPTCHA Enterprise.

   1. Gehen Sie in der Experience Manager-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Tippen **[!UICONTROL reCAPTCHA]**. Die Seite Konfigurationen wird geöffnet. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Wählen Sie Version als reCAPTCHA Enterprise und geben Sie den Namen an. Projekt-ID, Site-Schlüssel und API-Schlüssel (abgerufen in Schritt 2 und 3) für den reCAPTCHA Enterprise-Dienst.
   1. Wählen Sie den Schlüsseltyp aus. Der Schlüsseltyp sollte mit dem im Google Cloud-Projekt konfigurierten Site-Schlüssel übereinstimmen, z. B. **Checkbox-Site-Schlüssel** oder **Score-basierter Site-Schlüssel**.
   1. Geben Sie einen Schwellenwert zwischen 0 und 1 ([Klicken Sie auf , um mehr über die Punktzahl zu erfahren.](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores)). Werte, die größer oder gleich den Schwellenwerten sind, kennzeichnen menschliche Interaktionen, die ansonsten als Bot-Interaktion betrachtet werden.

      > Hinweis:
      >
      > * Formularautoren können eine Punktzahl im Bereich angeben, der für die unterbrechungsfreie Formularübermittlung geeignet ist.

   1. Tippen **[!UICONTROL Erstellen]** , um die Cloud Service-Konfiguration zu erstellen.

   1. Geben Sie im Dialogfeld &quot;Komponente bearbeiten&quot;den Namen, die Projekt-ID, den Site-Schlüssel und den API-Schlüssel an (erhalten in den Schritten 2 und 3), wählen Sie den Schlüsseltyp aus und geben Sie den Schwellenwert ein. Tippen **[!UICONTROL Einstellungen speichern]** und tippen Sie dann auf **[!UICONTROL OK]** , um die Konfiguration abzuschließen.

Sobald der reCAPTCHA Enterprise-Dienst aktiviert ist, ist er zur Verwendung in adaptiven Formularen verfügbar. Siehe [Verwenden von CAPTCHA in adaptiven Formularen](#using-reCAPTCHA).

![reCAPTCHA Enterprise](/help/forms/using/assets/recaptcha1-enterprise.png)


### Konfigurieren von Google reCAPTCHA v2 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Erhalten [reCAPTCHA API-Schlüsselpaar](https://www.google.com/recaptcha/admin) aus Google. Er enthält **Site-Schlüssel** und **geheimer Schlüssel**.
1. Erstellen Sie einen Konfigurations-Container für Cloud Services.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**. Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloudkonfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

      1. Wählen Sie im Konfigurationsbrowser den Ordner **[!UICONTROL global]** und tippen Sie auf **[!UICONTROL Eigenschaften]**.

      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   1. Tippen Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloudkonfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.

1. Konfigurieren Sie den Cloud-Dienst für reCAPTCHA v2.

   1. Navigieren Sie in der AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **Cloud Services**.
   1. Tippen **[!UICONTROL reCAPTCHA]**. Die Seite Konfigurationen wird geöffnet. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Wählen Sie Version als reCAPTCHA v2 aus, geben Sie den Namen an. Site-Schlüssel und geheimer Schlüssel für reCAPTCHA-Dienst (abgerufen in Schritt 1) und tippen Sie auf **[!UICONTROL Erstellen]** , um die Cloud Service-Konfiguration zu erstellen.
   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ die Site- und Geheimschlüssel an, die Sie in Schritt 1 erhalten haben. Tippen Sie auf **[!UICONTROL Einstellungen speichern]** und anschließend auf **OK**, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Dienst konfiguriert ist, ist er zur Verwendung in adaptiven Formularen verfügbar. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-captcha).

![reCAPTCHA v2](/help/forms/using/assets/recaptcha-v2.png)


## Verwenden von reCAPTCHA in adaptiven Formularen {#using-reCAPTCHA}

Verwenden von reCAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurationscontainer den reCAPTCHA-Cloud-Service enthält. Sie können auch die Eigenschaften des adaptiven Formulars bearbeiten, um den mit dem Formular verknüpften Konfigurationscontainer zu ändern.

1. Ziehen Sie aus dem Komponenten-Browser die **Captcha** auf das adaptive Formular.

   >[!NOTE]
   >
   >Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, CAPTCHA in einem Bereich zu verwenden, der für verzögertes Laden markiert ist, oder in einem Fragment.

   >[!NOTE]
   >
   >Captcha ist zeitkritisch und läuft in etwa einer Minute ab. Daher wird empfohlen, die Captcha-Komponente direkt vor der Senden-Schaltfläche im adaptiven Formular zu platzieren.

1. Wählen Sie die hinzugefügte Captcha-Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png) , um die Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **CAPTCHA**. Wählen Sie **Titel ausblenden**, wenn der Titel nicht angezeigt werden soll.
1. Aus dem **Captcha-Dienst** Dropdown-Liste auswählen **reCAPTCHA** , um den reCAPTCHA-Dienst zu aktivieren, wenn Sie ihn wie in [reCAPTCHA-Dienst von Google](#google-reCAPTCHA).
1. Wählen Sie eine Konfiguration aus der Dropdown-Liste „Einstellungen“. 
1. **Wenn die ausgewählte Konfiguration die Version reCAPTCHA Enterprise aufweist**:
   1. Sie können die reCAPTCHA-Cloud-Konfiguration mit **Schlüsseltyp** as **Kontrollkästchen**. Beim Schlüsseltyp Kontrollkästchen wird die angepasste Fehlermeldung als Inline-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt. Sie können die Größe als **[!UICONTROL Normal]** und **[!UICONTROL Kompakt]**.
   1. Sie können die reCAPTCHA-Cloud-Konfiguration mit **Schlüsseltyp** as **Ergebnisbasiert**. Beim bewerteten Schlüsseltyp wird die angepasste Fehlermeldung als Popup-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt.
   1. Wenn Sie eine **[!UICONTROL Bindungsverweis]** die übermittelten Daten sind gebundene Daten, andernfalls sind sie ungebundene Daten. Im Folgenden finden Sie XML-Beispiele für ungebundene Daten und gebundene Daten (mit Bindungsverweis als SSN), wenn ein Formular gesendet wird.

      ```xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <afData>
          <afUnboundData>
              <data>
                  <captcha16820607953761>
                      <captchaType>reCAPTCHAEnterprise</captchaType>
                      <captchaScore>0.9</captchaScore>
                  </captcha16820607953761>
              </data>
          </afUnboundData>
          <afBoundData>
              <Root
                  xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                  <PersonalDetails>
                      <SSN>371237912</SSN>
                      <FirstName>Sarah </FirstName>
                      <LastName>Smith</LastName>
                  </PersonalDetails>
                  <OtherInfo>
                      <City>California</City>
                      <Address>54 Residency</Address>
                      <State>USA</State>
                      <Zip>123112</Zip>
                  </OtherInfo>
              </Root>
          </afBoundData>
          <afSubmissionInfo>
              <stateOverrides/>
              <signers/>
              <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
              <afSubmissionTime>20230608034928</afSubmissionTime>
          </afSubmissionInfo>
          </afData>
      ```


      ```xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <afData>
          <afUnboundData>
              <data/>
          </afUnboundData>
          <afBoundData>
              <Root
                  xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                  <PersonalDetails>
                      <SSN>
                          <captchaType>reCAPTCHAEnterprise</captchaType>
                          <captchaScore>0.9</captchaScore>
                      </SSN>
                      <FirstName>Sarah</FirstName>
                      <LastName>Smith</LastName>
                  </PersonalDetails>
                  <OtherInfo>
                      <City>California</City>
                      <Address>54 Residency</Address>
                      <State>USA</State>
                      <Zip>123112</Zip>
                  </OtherInfo>
              </Root>
          </afBoundData>
          <afSubmissionInfo>
              <stateOverrides/>
              <signers/>
              <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
              <afSubmissionTime>20230608035111</afSubmissionTime>
          </afSubmissionInfo>
          </afData>
      ```


   **Wenn die ausgewählte Konfiguration die Version reCAPTCHA v2 aufweist**:
   1. Wählen Sie die Größe als **[!UICONTROL Normal]** oder **[!UICONTROL Kompakt]** für das reCAPTCHA-Widget. Sie können auch die Option **[!UICONTROL Unsichtbar]** auswählen, um die CAPTCHA-Abfrage nur im Falle einer verdächtigen Aktivität anzuzeigen. Die **geschützt durch reCAPTCHA** -Zeichen, unten angezeigt, wird auf den geschützten Formularen angezeigt.

      ![Durch Google geschützt mit reCAPTCHA-Badge](/help/forms/using/assets/google-recaptcha-v2.png)


   Der reCAPTCHA-Dienst wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen.

1. Speichern Sie die Eigenschaften.

>[!NOTE]
> 
> Wählen Sie nicht **[!UICONTROL Standard]** aus der Dropdown-Liste „CAPTCHA-Service“ aus, da der standardmäßige AEM-CAPTCHA-Service nicht mehr unterstützt wird.

### Ein- oder Ausblenden der CAPTCHA-Komponente auf Grundlage von Regeln {#show-hide-captcha}

Sie können die CAPTCHA-Komponente auf Grundlage von Regeln, die Sie auf eine Komponente in einem adaptiven Formular anwenden, ein- oder ausblenden. Tippen Sie auf die Komponente, wählen Sie ![Regeln bearbeiten](assets/edit-rules-icon.svg) aus und tippen Sie auf **[!UICONTROL Erstellen]**, um eine Regel zu erstellen. Weitere Informationen zum Erstellen von Regeln finden Sie im [Regeleditor](rule-editor.md).

Beispielsweise darf die CAPTCHA-Komponente nur dann in einem adaptiven Formular angezeigt werden, wenn das Feld „Währungswert“ im Formular einen Wert von mehr als 25000 aufweist.

Tippen Sie im Formular auf das Feld **[!UICONTROL Währungswert]** und erstellen Sie folgende Regeln:

![Regeln zum Ein- oder Ausblenden](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> * Wenn Sie die reCAPTCHA v2-Konfiguration mit der Größe **[!UICONTROL Unsichtbar]** oder auf reCAPTCHA Enterprise-Punktzahlen basieren, ist die Option zum Anzeigen/Verbergen nicht anwendbar.

### CAPTCHA validieren {#validate-captcha}

Sie können CAPTCHA in einem adaptiven Formular entweder beim Übermitteln des Formulars validieren oder angeben, dass die CAPTCHA-Validierung auf Benutzeraktionen und -bedingungen basiert.

#### CAPTCHA bei Formularübermittlung validieren {#validation-form-submission}

So validieren Sie CAPTCHA beim Übermitteln eines adaptiven Formulars automatisch:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA bei Formularübermittlung validieren]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

#### Validieren von CAPTCHA mit Benutzeraktionen und -bedingungen {#validate-captcha-user-action}

Validieren von CAPTCHA basierend auf Bedingungen und Benutzeraktionen:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA mit Benutzeraktion validieren]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

   >[!NOTE]
   >
   >
   > Wenn Sie die reCAPTCHA v2-Konfiguration mit der Größe **[!UICONTROL Unsichtbar]** oder auf reCAPTCHA Enterprise-Schlüsseln basieren, ist das gültige Captcha für eine Benutzeraktion nicht anwendbar.

[!DNL Experience Manager Forms] stellt die `ValidateCAPTCHA`-API zur Validierung von CAPTCHA unter Verwendung vordefinierter Bedingungen bereit. Sie können die API mit einer benutzerdefinierten Übermittlungsaktion oder durch Definieren von Regeln für Komponenten in einem adaptiven Formular aufrufen.

Im Folgenden finden Sie ein Beispiel für eine `ValidateCAPTCHA`-API zur Validierung von CAPTCHA unter Verwendung vordefinierter Bedingungen:

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
        GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

Das Beispiel zeigt an, dass die `ValidateCAPTCHA`-API CAPTCHA im Formular nur dann validiert, wenn die Anzahl der Stellen im numerischen Feld, die der Benutzer beim Ausfüllen des Formulars angegeben hat, größer als 5 ist.

**Option 1: Verwenden Sie die [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA mithilfe einer benutzerdefinierten Übermittlungsaktion zu validieren.**

Führen Sie folgende Schritte aus, um die `ValidateCAPTCHA`-API zur Validierung von CAPTCHA mit einer benutzerdefinierten Übermittlungsaktion zu verwenden:

1. Fügen Sie das Skript, das die `ValidateCAPTCHA`-API enthält, zur benutzerdefinierten Übermittlungsaktion hinzu. Weitere Informationen zu benutzerdefinierten Übermittlungsaktionen finden Sie unter [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Formulare](custom-submit-action-form.md).
1. Wählen Sie den Namen der benutzerdefinierten Übermittlungsaktion aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** in den Eigenschaften für die **[!UICONTROL Übermittlung]** eines adaptiven Formulars.
1. Tippen Sie auf **[!UICONTROL Übermitteln]**. CAPTCHA wird auf Grundlage der Bedingungen validiert, die in der `ValidateCAPTCHA`-API der benutzerdefinierten Übermittlungsaktion definiert sind.

**Option 2: Verwenden Sie die [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA vor dem Übermitteln des Formulars bei einer Benutzeraktion zu validieren.**

Sie können die `ValidateCAPTCHA`-API auch aufrufen, indem Sie Regeln auf eine Komponente in einem adaptiven Formular anwenden.

Sie fügen beispielsweise die Schaltfläche **[!UICONTROL CAPTCHA validieren]** in einem adaptiven Formular hinzu und erstellen eine Regel, um beim Klick auf eine Schaltfläche einen Service aufzurufen.

Folgende Abbildung zeigt, wie Sie beim Klick auf die Schaltfläche **[!UICONTROL CAPTCHA validieren]** einen Service aufrufen können:

![CAPTCHA validieren](assets/captcha-validation1.gif)

Sie können das benutzerdefinierte Servlet, das die `ValidateCAPTCHA`-API enthält, mit dem Regeleditor aufrufen und die Schaltfläche zum Übermitteln des adaptiven Formulars basierend auf dem Validierungsergebnis aktivieren oder deaktivieren.

Ebenso können Sie mithilfe des Regeleditors eine benutzerdefinierte Methode zur Validierung von CAPTCHA in ein adaptives Formular aufnehmen.

### Hinzufügen benutzerdefinierter CAPTCHA-Services {#add-custom-captcha-service}

[!DNL Experience Manager Forms] stellt reCAPTCHA als CAPTCHA-Service bereit. Sie können jedoch einen benutzerdefinierten Service hinzufügen, der in der Dropdown-Liste **[!UICONTROL CAPTCHA-Service]** angezeigt wird.

Im Folgenden finden Sie eine Beispielimplementierung der Oberfläche zum Hinzufügen eines zusätzlichen CAPTCHA-Service zu Ihrem adaptiven Formular:

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` Bezieht sich auf den Ressourcenpfad der CAPTCHA-Komponente im Sling-Repository. Verwenden Sie diese Eigenschaft, um spezifische Details zur CAPTCHA-Komponente aufzunehmen. Beispielsweise enthält `captchaPropertyNodePath` Informationen zur reCAPTCHA-Cloudkonfiguration, die für die CAPTCHA-Komponente eingestellt ist. Die Informationen zur Cloudkonfiguration enthalten die Einstellungen **[!UICONTROL Siteschlüssel]** und **[!UICONTROL Geheimschlüssel]** für die Implementierung des reCAPTCHA-Service.

`userResponseToken` Bezieht sich auf die `g_reCAPTCHA_response` wird nach dem Lösen eines CAPTCHA in einem Formular generiert.
