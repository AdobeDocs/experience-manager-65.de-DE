---
title: Verwenden von CAPTCHA in adaptiven Formularen
seo-title: Verwenden von CAPTCHA in adaptiven Formularen
description: Erfahren Sie, wie Sie AEM CAPTCHA oder Google reCAPTCHA in adaptiven Formularen konfigurieren.
seo-description: Erfahren Sie, wie Sie AEM CAPTCHA oder Google reCAPTCHA in adaptiven Formularen konfigurieren.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 7a3f54d90769708344e6751756b2a12ac6c962d7
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 43%

---


# Verwenden von CAPTCHA in adaptiven Formularen{#using-captcha-in-adaptive-forms}

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ - „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das in Online-Transaktionen eingesetzt wird, um zwischen Personen oder Bots und automatisierten Programmen zu unterscheiden. Es bewertet die Benutzerantwort, um zu ermitteln, ob ein Mensch oder ein Bot mit der Website interagiert. Es verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, und macht Online-Transaktionen sicherer, weil Bots so keinen Spam veröffentlichen oder andere bösartige Zwecke verfolgen können.

AEM Forms unterstützt CAPTCHA in adaptiven Formularen. Sie können den reCAPTCHA-Dienst von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>* AEM Forms unterstützt nur reCaptcha v2. Es werden keine anderen Versionen unterstützt.
>* Im Offline-Modus wird CAPTCHA in adaptiven Formularen in der AEM Forms-App nicht unterstützt.

>



## ReCAPTCHA-Dienst von Google konfigurieren {#google-recaptcha}

Formularautoren können den reCAPTCHA-Dienst von Google verwenden, um CAPTCHA in adaptive Formulare zu implementieren. Er bietet erweiterte CAPTCHA-Fähigkeiten, um Ihre Website zu schützen. Weitere Informationen dazu, wie reCAPTCHA funktioniert, finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![Recaptcha](assets/recaptcha_new.png)

Implementieren des reCAPTCHA-Diensts in AEM Forms:

1. Rufen Sie ein [reCAPTCHA-API-Schlüsselpaar](https://www.google.com/recaptcha/admin) von Google ab. Er enthält einen Site-Schlüssel und einen geheimen Schlüssel.
1. Erstellen Sie einen Konfigurationscontainer für Cloud-Dienste.

   1. Gehen Sie zu **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud-Dienstkonfigurationen zu erstellen und zu konfigurieren.

      1. Wählen Sie im Konfigurationsbrowser  den Ordner **[!UICONTROL global]** und tippen Sie auf **[!UICONTROL Eigenschaften]**.

      1. Aktivieren Sie im Dialogfeld Konfigurationseigenschaften die Option **[!UICONTROL Cloud-Konfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.
   1. Tippen Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld Konfiguration erstellen einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den Ordner zu erstellen, der für Cloud-Dienstkonfigurationen aktiviert ist.


1. Konfigurieren Sie den Cloud-Dienst für reCAPTCHA.

   1. Wechseln Sie in Ihrer AEM Autoreninstanz zu ![tools-1](assets/tools-1.png) > **Cloud Services**.
   1. Tippen Sie auf **[!UICONTROL reCAPTCHA]**. Die Konfigurationsseite wird geöffnet. Wählen Sie den im vorherigen Schritt erstellten Konfigurationscontainer und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Geben Sie den Namen, den Site-Schlüssel und den geheimen Schlüssel für den reCAPTCHA-Dienst an und tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Dienstkonfiguration zu erstellen.
   1. Wählen Sie im Dialogfeld „Komponente bearbeiten“ und geben Sie die Website sowie den Site- und geheimen Schlüssel an, den Sie in Schritt 1 erhalten haben. Tippen Sie auf **Einstellungen speichern** und dann auf **OK**, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Dienst konfiguriert ist, kann er in adaptiven Formularen verwendet werden. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-captcha).

## Verwenden von CAPTCHA in adaptiven Formularen  {#using-captcha}

Verwenden von CAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurationscontainer den Cloud-Dienst reCAPTCHA enthält. Sie können auch adaptive Formulareigenschaften bearbeiten, um den Konfigurationscontainer zu ändern, der dem Formular zugeordnet ist.

1. Ziehen Sie im Komponenten-Browser per Drag&amp;Drop die **Captcha-Komponente** in das adaptive Formular.

   >[!NOTE]
   >
   >Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird nicht empfohlen, CAPTCHA in einem Fragment oder in einem Bedienfeld zu verwenden, für das verzögertes Laden konfiguriert wurde.

   >[!NOTE]
   >
   >Captcha ist zeitabhängig und läuft in etwa einer Minute ab. Daher wird empfohlen, die Captcha-Komponente unmittelbar vor der Sendeschaltfläche im adaptiven Formular zu platzieren.

1. Wählen Sie die hinzugefügte Captcha-Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png), um ihre Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **Captcha**. Wählen Sie **Titel ausblenden**, wenn der Titel nicht angezeigt werden soll.
1. Wählen Sie in der Dropdownliste **Captcha-Dienst** **reCaptcha** aus, um den reCAPTCHA-Dienst zu aktivieren, wenn Sie ihn wie unter [ReCAPTCHA-Dienst von Google](#google-recaptcha) beschrieben konfiguriert haben. Wählen Sie eine Konfiguration aus der Dropdown-Liste „Einstellungen“. Wählen Sie außerdem als Größe **Normal** oder **Kompakt** für das reCAPTCHA-Widget aus.

   >[!NOTE]
   >
   >Wählen Sie nicht die Option **[!UICONTROL Standard]** aus der Dropdownliste „Captcha-Dienst“ aus, da der AEM-CAPTCHA-Standarddienst nicht mehr unterstützt wird.

1. Speichern Sie die Eigenschaften.

Der reCAPTCHA-Dienst wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen.

### CAPTCHA-Komponente basierend auf Regeln ein- oder ausblenden{#show-hide-captcha}

Sie können die CAPTCHA-Komponente auf Grundlage von Regeln, die Sie auf eine Komponente in einem adaptiven Formular anwenden, ein- oder ausblenden. Tippen Sie auf die Komponente, wählen Sie ![Regeln bearbeiten](assets/edit-rules-icon.svg) und tippen Sie auf **[!UICONTROL Erstellen]**, um eine Regel zu erstellen. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Regel-Editor](rule-editor.md).

Beispielsweise darf die CAPTCHA-Komponente nur dann in einem adaptiven Formular angezeigt werden, wenn das Feld &quot;Währungswert&quot;im Formular einen Wert von mehr als 25000 aufweist.

Tippen Sie im Formular auf das Feld **[!UICONTROL Währungswert]** und erstellen Sie die folgenden Regeln:

![Regeln ein- oder ausblenden](assets/rules-show-hide-captcha.png)

### CAPTCHA überprüfen {#validate-captcha}

Sie können CAPTCHA in einem adaptiven Formular validieren, wenn Sie das Formular senden oder die CAPTCHA-Überprüfung auf Benutzeraktionen und -bedingungen basieren.

#### CAPTCHA bei Formularübermittlung überprüfen {#validation-form-submission}

So validieren Sie ein CAPTCHA beim Senden eines adaptiven Formulars automatisch

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg), um die Komponenteneigenschaften Ansicht.
1. Wählen Sie im Abschnitt **[!UICONTROL CAPTCHA überprüfen]** **[!UICONTROL CAPTCHA bei Formularübermittlung überprüfen]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

#### CAPTCHA bei Benutzeraktionen und -bedingungen {#validate-captcha-user-action} validieren

So validieren Sie ein CAPTCHA basierend auf Bedingungen und Benutzeraktionen:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg), um die Komponenteneigenschaften Ansicht.
1. Wählen Sie im Abschnitt **[!UICONTROL CAPTCHA überprüfen]** **[!UICONTROL CAPTCHA für eine Benutzeraktion]** überprüfen.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

[!DNL Experience Manager Forms] stellt  `ValidateCAPTCHA` API zur Validierung von CAPTCHA unter Verwendung vordefinierter Bedingungen bereit. Sie können die API mit einer benutzerdefinierten Übermittlungsaktion oder durch Definieren von Regeln für Komponenten in einem adaptiven Formular aufrufen.

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

Das Beispiel zeigt an, dass die API das CAPTCHA im Formular nur dann validiert, wenn die Anzahl der Stellen im numerischen Feld, die der Benutzer beim Ausfüllen des Formulars angegeben hat, größer als 5 ist.`ValidateCAPTCHA`

**Option 1: Verwenden Sie die  [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA mithilfe einer benutzerdefinierten Übermittlungsaktion zu validieren**

Führen Sie die folgenden Schritte aus, um die `ValidateCAPTCHA`-API zur Validierung von CAPTCHA mit einer benutzerdefinierten Übermittlungsaktion zu verwenden:

1. hinzufügen Sie das Skript mit der API `ValidateCAPTCHA` in eine benutzerdefinierte Übermittlungsaktion. Weitere Informationen zu benutzerdefinierten Übermittlungsaktionen finden Sie unter [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptives Forms](custom-submit-action-form.md).
1. Wählen Sie den Namen der benutzerdefinierten Übermittlungsaktion aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** in den **[!UICONTROL Übermittlungseigenschaften]** eines adaptiven Formulars.
1. Tippen Sie auf **[!UICONTROL Senden]**. Das CAPTCHA wird basierend auf den Bedingungen validiert, die in der API `ValidateCAPTCHA` der benutzerdefinierten Übermittlungsaktion definiert sind.

**Option 2: Verwenden Sie die  [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA vor dem Senden des Formulars bei einer Benutzeraktion zu validieren**

Sie können die API auch aufrufen, indem Sie Regeln für eine Komponente in einem adaptiven Formular anwenden.`ValidateCAPTCHA`

Sie fügen beispielsweise die Schaltfläche **[!UICONTROL CAPTCHA überprüfen]** in einem adaptiven Formular hinzu und erstellen eine Regel, um einen Dienst beim Klicken auf eine Schaltfläche aufzurufen.

Die folgende Abbildung zeigt, wie Sie einen Dienst beim Klicken auf eine Schaltfläche **[!UICONTROL CAPTCHA überprüfen]** aufrufen können:

![CAPTCHA überprüfen](assets/captcha-validation1.gif)

Sie können das benutzerdefinierte Servlet mit der API `ValidateCAPTCHA` mithilfe des Regeleditors aufrufen und die Senden-Schaltfläche des adaptiven Formulars basierend auf dem Überprüfungsergebnis aktivieren oder deaktivieren.

Ebenso können Sie mithilfe des Regeleditors eine benutzerdefinierte Methode zur Validierung von CAPTCHA in ein adaptives Formular einschließen.

### hinzufügen benutzerdefinierten CAPTCHA-Dienste {#add-custom-captcha-service}

[!DNL Experience Manager Forms] stellt reCAPTCHA als CAPTCHA-Dienst bereit. Sie können jedoch einen benutzerdefinierten Dienst hinzufügen, der in der Dropdown-Liste **[!UICONTROL CAPTCHA-Dienst]** angezeigt wird.

Im Folgenden finden Sie eine Beispielimplementierung der Oberfläche zum Hinzufügen eines zusätzlichen CAPTCHA-Dienstes zu Ihrem adaptiven Formular:

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

`captchaPropertyNodePath` verweist auf den Ressourcenpfad der CAPTCHA-Komponente im Sling-Repository. Verwenden Sie diese Eigenschaft, um spezifische Details zur CAPTCHA-Komponente einzuschließen. Beispielsweise enthält `captchaPropertyNodePath` Informationen zur reCAPTCHA-Cloud-Konfiguration, die für die CAPTCHA-Komponente konfiguriert ist. Die Cloud-Konfigurationsinformationen enthalten die Einstellungen **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL Geheimschlüssel]** für die Implementierung des reCAPTCHA-Dienstes.

`userResponseToken` bezieht sich auf die  `g_recaptcha_response` Daten, die nach dem Lösen eines CAPTCHA in einem Formular generiert werden.
