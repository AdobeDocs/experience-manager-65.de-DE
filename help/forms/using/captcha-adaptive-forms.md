---
title: Verwenden von CAPTCHA in adaptiven Formularen
description: Erfahren Sie, wie Sie AEM CAPTCHA oder Google reCAPTCHA-Service in adaptiven Formularen konfigurieren.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 9b4219b8-d5eb-4099-b205-d98d84e0c249
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1832'
ht-degree: 100%

---

# Verwenden von CAPTCHA in adaptiven Formularen{#using-captcha-in-adaptive-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/captcha-adaptive-forms.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms unterstützt CAPTCHA in adaptiven Formularen. Sie können den reCAPTCHA-Service von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>* AEM Forms unterstützt reCAPTCHA v2 und Enterprise. Es werden keine anderen Versionen unterstützt.
>* Im Offline-Modus wird CAPTCHA in adaptiven Formularen in der AEM Forms-App nicht unterstützt.

## Konfigurieren des reCAPTCHA-Services von Google für adaptive Formulare {#google-reCAPTCHA}

AEM Forms-Benutzende können den reCAPTCHA-Service von Google verwenden, um CAPTCHA in adaptive Formulare zu implementieren. Er bietet erweiterte CAPTCHA-Funktionen zum Schutz Ihrer Site. Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/). Der reCAPTCHA-Service einschließlich reCAPTCHA v2 und reCAPTCHA Enterprise ist in AEM Forms integriert. Je nach Ihren Anforderungen können Sie den reCAPTCHA-Service konfigurieren, um Folgendes zu aktivieren:

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)

![reCAPTCHA](/help/forms/using/assets/recaptcha_new.png)

### Konfigurieren von reCAPTCHA Enterprise  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Erstellen Sie ein [reCAPTCHA Enterprise-Projekt](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin), mit aktivierter [reCAPTCHA Enterprise-API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. [Rufen](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) Sie die Projekt-ID ab.
1. Erstellen Sie einen [API-Schlüssel](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) und einen [Site-Schlüssel für Websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Erstellen Sie einen Konfigurations-Container für Cloud-Dienste.

   1. Wählen Sie **[!UICONTROL „Tools“ > „Allgemein“ > „Konfigurationsbrowser“]**. Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.
      1. Wählen Sie im Konfigurations-Browser den Ordner **[!UICONTROL Global]** und klicken Sie auf **[!UICONTROL Eigenschaften]**.
      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
      1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   1. Wählen Sie im Konfigurations-Browser **[!UICONTROL Erstellen]** aus.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus, um den für Cloud-Service-Konfigurationen aktivierten Ordner zu erstellen.
1. Konfigurieren Sie den Cloud Service für reCAPTCHA Enterprise.

   1. Gehen Sie in der Experience Manager-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud-Services]**.
   1. Wählen Sie **[!UICONTROL reCAPTCHA]** aus. Die Konfigurationsseite öffnet sich. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und dann **[!UICONTROL Erstellen]** aus.
   1. Wählen Sie die Version „reCAPTCHA Enterprise“ und geben Sie den Namen, die Projekt-ID, den Site-Schlüssel und den API-Schlüssel (erhalten in Schritt 2 und 3) für den reCAPTCHA Enterprise-Dienst an.
   1. Wählen Sie den Schlüsseltyp aus. Der Schlüsseltyp sollte mit dem im Google Cloud-Projekt konfigurierten Site-Schlüssel übereinstimmen, z. B. **Checkbox site key** oder **Score-based site key**.
   1. Geben Sie einen Schwellenwert im Bereich von 0 bis 1 an. ([Klicken Sie hier, um mehr über den Wert zu erfahren](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores).) Werte, die größer oder gleich den Schwellenwerten sind, kennzeichnen menschliche Interaktionen, die ansonsten als Bot-Interaktion betrachtet werden.

      > Hinweis:
      >
      > * Formularautorinnen und -autoren können eine Punktzahl im Bereich angeben, der für die unterbrechungsfreie Formularübermittlung geeignet ist.

   1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.

   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ den Namen, die Projekt-ID, den Site-Schlüssel und den API-Schlüssel an (erhalten in den Schritten 2 und 3), wählen Sie den Schlüsseltyp aus und geben Sie den Schwellenwert ein. Wählen Sie **[!UICONTROL Einstellungen speichern]** und dann **[!UICONTROL OK]** aus, um die Konfiguration abzuschließen.

Sobald der reCAPTCHA Enterprise-Dienst aktiviert ist, kann er in adaptiven Formularen verwendet werden. Siehe [Verwenden von CAPTCHA in adaptiven Formularen](#using-reCAPTCHA).

![ReCaptcha Enterprise](/help/forms/using/assets/recaptcha1-enterprise.png)


### Konfigurieren von Google reCAPTCHA v2 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Rufen Sie ein [reCAPTCHA-API-Schlüsselpaar](https://www.google.com/recaptcha/admin) von Google ab. Er enthält einen **Site-Schlüssel** und einen **geheimen Schlüssel**.
1. Erstellen Sie einen Konfigurations-Container für Cloud-Dienste.
   1. Wählen Sie **[!UICONTROL „Tools“ > „Allgemein“ > „Konfigurationsbrowser“]**. Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

      1. Wählen Sie im Konfigurations-Browser den Ordner **[!UICONTROL Global]** und klicken Sie auf **[!UICONTROL Eigenschaften]**.

      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
      1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   1. Wählen Sie im Konfigurations-Browser **[!UICONTROL Erstellen]** aus.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus, um den für Cloud-Service-Konfigurationen aktivierten Ordner zu erstellen.

1. Konfigurieren Sie den Cloud Service für reCAPTCHA v2.

   1. Navigieren Sie in der AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **Cloud-Services**.
   1. Wählen Sie **[!UICONTROL reCAPTCHA]** aus. Die Konfigurationsseite öffnet sich. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und dann **[!UICONTROL Erstellen]** aus.
   1. Wählen Sie die Version „reCAPTCHA v2“ aus, geben Sie den Namen, den Site-Schlüssel und den geheimen Schlüssel für den reCAPTCHA-Service an (aus Schritt 1) und wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.
   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ die Site- und Geheimschlüssel an, die Sie in Schritt 1 erhalten haben. Wählen Sie **[!UICONTROL Einstellungen speichern]** und dann **OK** aus, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Service konfiguriert ist, kann er in adaptiven Formularen verwendet werden. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-captcha).

![reCAPTCHA v2](/help/forms/using/assets/recaptcha-v2.png)


## Verwenden von reCAPTCHA in adaptiven Formularen {#using-reCAPTCHA}

So verwenden Sie reCAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurations-Container den reCAPTCHA-Cloud Service enthält. Sie können auch adaptive Formulareigenschaften bearbeiten, um den Konfigurationscontainer zu ändern, der dem Formular zugeordnet ist.

1. Ziehen Sie die **CAPTCHA**-Komponente im Komponenten-Browser in das adaptive Formular und legen Sie sie dort ab.

   >[!NOTE]
   >
   >Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird nicht empfohlen, CAPTCHA in einem Fragment oder in einem Bedienfeld zu verwenden, das für das verzögerte Laden konfiguriert wurde.

   >[!NOTE]
   >
   >Captcha ist zeitabhängig und läuft in etwa einer Minute ab. Daher wird empfohlen, die Captcha-Komponente unmittelbar vor der Sendeschaltfläche im adaptiven Formular zu platzieren.

1. Wählen Sie die hinzugefügte Captcha-Komponente und dann ![cmppr](assets/cmppr.png) aus, um die zugehörigen Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **CAPTCHA**. Wählen Sie **Titel ausblenden**, wenn der Titel nicht angezeigt werden soll.
1. Wählen Sie aus der Dropdown-Liste **Captcha-Service** die Option **reCAPTCHA**, um den reCAPTCHA-Service zu aktivieren, wenn Sie ihn wie unter [reCAPTCHA-Service von Google](#google-reCAPTCHA) beschrieben konfiguriert haben.
1. Wählen Sie eine Konfiguration aus der Dropdown-Liste „Einstellungen“. 
1. **Wenn die ausgewählte Konfiguration die Version reCAPTCHA Enterprise aufweist**:
   1. Sie können die reCAPTCHA-Cloud-Konfiguration auswählen, wobei der **Schlüsseltyp** als **Kontrollkästchen** ausgewählt ist. Beim Schlüsseltyp „Kontrollkästchen“ wird die angepasste Fehlermeldung als Inline-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt. Sie können zwischen den Größen **[!UICONTROL Normal]** und **[!UICONTROL Kompakt]** wählen.
   1. Sie können die reCAPTCHA-Cloud-Konfiguration auswählen, wobei der **Schlüsseltyp** als **punktebasiert** ausgewählt ist. Beim bewerteten Schlüsseltyp wird die angepasste Fehlermeldung als Popup-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt.
   1. Wenn Sie einen **[!UICONTROL Bindungsverweis]** auswählen, sind die übermittelten Daten gebundene Daten, ansonsten handelt es sich um ungebundene Daten. Im Folgenden finden Sie XML-Beispiele für ungebundene Daten und gebundene Daten (mit Bindungsverweis als SSN), wenn ein Formular gesendet wird.

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


   **Wenn die ausgewählte Konfiguration die Version „reCAPTCHA v2“ aufweist**:
   1. Wählen Sie als Größe für das reCAPTCHA-Widget entweder **[!UICONTROL Normal]** oder **[!UICONTROL Kompakt]** aus. Sie können auch die Option **[!UICONTROL Unsichtbar]** auswählen, um die CAPTCHA-Abfrage nur bei einer verdächtigen Aktivität anzuzeigen. Das unten abgebildete Abzeichen **mit reCAPTCHA geschützt** wird auf den geschützten Formularen angezeigt.

      ![Durch Google geschützt mit reCAPTCHA-Badge](/help/forms/using/assets/google-recaptcha-v2.png)


   Der reCAPTCHA-Dienst wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen.

1. Speichern Sie die Eigenschaften.

>[!NOTE]
> 
> Wählen Sie nicht **[!UICONTROL Standard]** aus der Dropdown-Liste „CAPTCHA-Service“ aus, da der standardmäßige AEM-CAPTCHA-Service nicht mehr unterstützt wird.

### Ein- oder Ausblenden der CAPTCHA-Komponente auf Grundlage von Regeln {#show-hide-captcha}

Sie können die CAPTCHA-Komponente auf Grundlage von Regeln, die Sie auf eine Komponente in einem adaptiven Formular anwenden, ein- oder ausblenden. Wählen Sie erst die Komponente, dann ![Regeln bearbeiten](assets/edit-rules-icon.svg) und schließlich **[!UICONTROL Erstellen]** aus, um eine Regel zu erstellen. Weitere Informationen zum Erstellen von Regeln finden Sie im [Regeleditor](rule-editor.md).

Beispielsweise darf die CAPTCHA-Komponente nur dann in einem adaptiven Formular angezeigt werden, wenn das Feld „Währungswert“ im Formular einen Wert von mehr als 25000 aufweist.

Wählen Sie im Formular das Feld **[!UICONTROL Währungswert]** aus und erstellen Sie folgende Regeln:

![Regeln zum Ein- oder Ausblenden](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> * Wenn Sie eine reCAPTCHA v2-Konfiguration mit der Größe als **[!UICONTROL Unsichtbar]** oder den reCAPTCHA Enterprise punktebasierten Schlüsseln auswählen, dann ist die Option zum Anzeigen/Verbergen nicht anwendbar.

### CAPTCHA validieren {#validate-captcha}

Sie können CAPTCHA in einem adaptiven Formular entweder beim Übermitteln des Formulars validieren oder angeben, dass die CAPTCHA-Validierung auf Benutzeraktionen und -bedingungen basiert.

#### CAPTCHA bei Formularübermittlung validieren {#validation-form-submission}

So validieren Sie ein CAPTCHA beim Übermitteln eines adaptiven Formulars automatisch:

1. Wählen Sie die CAPTCHA-Komponente und dann ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA bei Formularübermittlung validieren]**.
1. Wählen Sie ![Fertig](assets/save_icon.svg) aus, um die Komponenteneigenschaften zu speichern.

#### Validieren von CAPTCHA mit Benutzeraktionen und -bedingungen {#validate-captcha-user-action}

So walidieren Sie ein CAPTCHA basierend auf Bedingungen und Benutzeraktionen:

1. Wählen Sie die CAPTCHA-Komponente und dann ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL CAPTCHA validieren]** die Option **[!UICONTROL CAPTCHA mit Benutzeraktion validieren]**.
1. Wählen Sie ![Fertig](assets/save_icon.svg) aus, um die Komponenteneigenschaften zu speichern.

   >[!NOTE]
   >
   >
   > Wenn Sie eine reCAPTCHA v2-Konfiguration mit der Größe als **[!UICONTROL Unsichtbar]** oder den reCAPTCHA Enterprise punktebasierten Schlüsseln auswählen, dann ist „Valid Captcha“ auf eine Benutzeraktion nicht anwendbar.

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
1. Wählen Sie **[!UICONTROL Übermitteln]** aus. CAPTCHA wird auf Grundlage der Bedingungen validiert, die in der `ValidateCAPTCHA`-API der benutzerdefinierten Übermittlungsaktion definiert sind.

**Option 2: Verwenden Sie die [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA vor dem Übermitteln des Formulars bei einer Benutzeraktion zu validieren.**

Sie können die `ValidateCAPTCHA`-API auch aufrufen, indem Sie Regeln auf eine Komponente in einem adaptiven Formular anwenden.

Sie fügen beispielsweise die Schaltfläche **[!UICONTROL CAPTCHA validieren]** in einem adaptiven Formular hinzu und erstellen eine Regel, um beim Klick auf eine Schaltfläche einen Service aufzurufen.

Folgende Abbildung zeigt, wie Sie beim Klick auf die Schaltfläche **[!UICONTROL CAPTCHA validieren]** einen Service aufrufen können:

![CAPTCHA validieren](assets/captcha-validation1.gif)

Sie können das benutzerdefinierte Servlet, das die `ValidateCAPTCHA`-API enthält, mit dem Regeleditor aufrufen und die Schaltfläche zum Übermitteln des adaptiven Formulars basierend auf dem Validierungsergebnis aktivieren oder deaktivieren.

Ebenso können Sie mithilfe des Regeleditors eine benutzerdefinierte Methode zur Validierung von CAPTCHA in ein adaptives Formular aufnehmen.

<!--
### Add custom CAPTCHA services {#add-custom-captcha-service}

[!DNL Experience Manager Forms] provides reCAPTCHA as the CAPTCHA service. However, you can add a custom service to display in the **[!UICONTROL CAPTCHA Service]** drop-down list.  

The following is a sample implementation of the interface to add additional CAPTCHA service to your Adaptive Form:

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

`captchaPropertyNodePath` Refers to the resource path of the CAPTCHA component in the Sling repository. Use this property to include details specific to the CAPTCHA component. For example, `captchaPropertyNodePath` includes information for the reCAPTCHA cloud configuration configured on the CAPTCHA component. The cloud configuration information provides **[!UICONTROL Site Key]** and **[!UICONTROL Secret Key]** settings for implementing the reCAPTCHA service.

`userResponseToken` Refers to the `g_reCAPTCHA_response` that gets generated after solving a CAPTCHA in a form. -->
