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
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 82%

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
