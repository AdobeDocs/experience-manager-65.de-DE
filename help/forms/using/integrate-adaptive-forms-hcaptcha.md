---
title: Wie wird hCAPTCHA&reg; in einer AEM 6.5-Forms verwendet?
description: Mit dem hCaptcha®-Dienst können Sie die Formularsicherheit optimieren. Schrittweise Anleitung enthalten!
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 6aa7a0a5-bd45-4628-abd0-312a9e6cf6fe
source-git-commit: 94a9f4087e36bfe5701ad9aafd4e8446ca643ddf
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 27%

---

# Verbinden Ihrer AEM Forms-Umgebung mit hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<!--
<span class="preview">This feature is based on Feature Toggle id `FT_FORMS-12407`. To enable the feature, follow the steps given in the [Enable Feature Toggle](/help/forms/using/enable-feature-toggle.md) article. </span>
-->

<span class="preview">Diese Funktion ist standardmäßig nicht aktiviert. Sie können an Ihre offizielle Adresse aem-forms-ea@adobe.com schreiben, um Zugriff auf die Funktion zu beantragen.</span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

Zusätzlich zu hCAPTCHA® unterstützt AEM Forms 6.5 die folgenden CAPTCHA-Lösungen:

* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [Cloudflare Turnstile](/help/forms/using/integrate-adaptive-forms-turnstile.md)

## Integrieren der AEM Forms-Umgebung mit hCaptcha®

Der hCaptcha®-Dienst schützt Ihre Formulare vor Bots, Spam und automatisiertem Missbrauch. Er führt einen Kontrollkästchen-Widget-Test durch und ermittelt anhand der Benutzerantwort, ob ein Mensch oder ein Bot mit dem Formular interagiert. Dabei wird verhindert, dass Benutzende fortfahren, wenn der Test fehlschlägt. Dies erhöht die Sicherheit von Online-Transaktionen, indem Bots keinen Spam senden oder andere bösartige Aktivitäten durchführen können.

AEM 6.5 Adaptive Forms unterstützt hCAPTCHA&amp;reg. Sie können damit beim Übermitteln eines Formulars eine Herausforderung für ein Kontrollkästchen-Widget darstellen.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->


### Voraussetzungen für die Integration der AEM Forms-Umgebung mit hCaptcha® {#prerequisite}

Um hCAPTCHA® mit AEM Forms zu konfigurieren, müssen Sie den [hCAPTCHA®-Site- und Geheimschlüssel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) von der hCAPTCHA®-Website abrufen.

### Konfigurieren von hCAPTCHA® {#steps-to-configure-hcaptcha}

Um AEM Forms mit dem hCAPTCHA®-Service zu integrieren, führen Sie die folgenden Schritte aus:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms-Umgebung, der Cloud-Konfigurationen enthält, mit denen die AEM mit externen Services verbunden wird. So erstellen Sie einen Konfigurations-Container:
   1. Öffnen Sie Ihre AEM Forms-Umgebung.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurations-Browser können Sie einen vorhandenen Ordner auswählen oder einen neuen Ordner erstellen:
      * So erstellen Sie einen neuen Ordner und aktivieren die Cloud-Konfigurationen:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und einen Titel an und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Cloud-Konfiguration für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie dann **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie **[!UICONTROL Speichern und schließen]** um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren Sie Ihre Cloud Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und klicken Sie auf **[!UICONTROL hCaptcha®]**.

      ![hCaptcha® in der Benutzeroberfläche](assets/hcaptcha-in-ui.png)
   1. Wählen Sie einen erstellten oder aktualisierten Konfigurations-Container aus, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfiguration hCAPTCHA®](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Titel]**, <!--**[!UICONTROL Name]**--> an **[!UICONTROL Site-]** und **[!UICONTROL Secret Key]** für den hCAPTCHA®-Service [abgerufen in PREREQUISITE](#prerequisite).
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren Sie den Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit hCaptcha®](assets/create-hcaptcha-config.png)

   >[!NOTE]
   > Benutzende müssen die Client[seitige JavaScript-Validierungs-URL ](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) die [Server-seitige Validierungs-URL](https://docs.hcaptcha.com/#verify-the-user-response-server-side) nicht ändern, da sie bereits für die hCAPTCHA®-Validierung vorausgefüllt sind.

   Sobald der CAPTCHA-Service konfiguriert ist, kann er in Ihrem adaptiven Formular verwendet werden.

## Verwenden von hCAPTCHA® in einem adaptiven Formular {#using-hCaptcha-in-aem-6.5}

1. Öffnen Sie Ihre AEM Forms-Umgebung.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie im **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit hCAPTCHA verbindet.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen Konfigurations-Container für hCAPTCHA haben, erfahren Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit hCAPTCHA®](#configure-hcaptcha-steps-to-configure-hcaptcha), wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/using/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie **[!UICONTROL Bearbeiten]**, um das Formular im Editor zu öffnen.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die **[!UICONTROL CAPTCHA]**-Komponente aus und klicken Sie auf Eigenschaften ![Symbol „Eigenschaften](assets/configure-icon.svg), um das Dialogfeld „Eigenschaften“ zu öffnen. Geben Sie die folgenden Eigenschaften an:

   ![hCaptcha® v1](assets/config-hcaptcha-v1-img.png)

   * **[!UICONTROL Titel]:** Geben Sie den Titel für die CAPTCHA-Komponente an.
   * **[!UICONTROL Validierungsmeldung]:** Geben Sie eine Validierungsmeldung für Ihre CAPTCHA-Validierung bei der Formularübermittlung oder bei einer Benutzeraktion ein.
   * **[!UICONTROL CAPTCHA-]:** Wählen Sie den CAPTCHA-Dienst für die Formularübermittlung aus. Hier wählen Sie hCAPTCHA®.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie Ihre für hCAPTCHA konfigurierte Cloud-Konfiguration ®.

     >[!NOTE]
     >Sie können in Ihrer Umgebung mehrere Cloud-Konfigurationen für einen ähnlichen Zweck verwenden. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Service aufgeführt ist, erfahren Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit hCAPTCHA®](#connect-your-forms-environment-with-hcaptcha-service), wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem hCAPTCHA®-Service verbindet.

   * **[!UICONTROL Fehlermeldung]:** Geben Sie die Fehlermeldung an, die Benutzern angezeigt werden soll, wenn die CAPTCHA-Übermittlung fehlschlägt.
   * **[!UICONTROL CAPTCHA-Größe]:** Sie können die Anzeigegröße des Dialogfelds für die hCAPTCHA®-Abfrage auswählen. Verwenden Sie die **[!UICONTROL Compact]**-Option, um ein kleines Format anzuzeigen, und **[!UICONTROL Normal]**, um ein relativ großes hCAPTCHA®-Dialogfeld für Herausforderungen anzuzeigen, oder **[!UICONTROL Unsichtbar]**, um hCAPTCHA® zu validieren, ohne das Kontrollkästchen-Widget auf der Benutzeroberfläche explizit zu rendern.

1. Wählen Sie **[!UICONTROL Fertig]**.


Jetzt sind nur noch legitime Formulare für die Formularübermittlung zulässig, bei denen der Formularausfüller die vom hCAPTCHA®-Service ausgehende Herausforderung erfolgreich löscht.

**hCaptcha® ist eine eingetragene Marke von Intuition Machines, Inc.**


## Häufig gestellte Fragen

* **F: Kann ich mehr als eine CAPTCHA-Komponente in einem adaptiven Formular verwenden?**
* **A:** Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird nicht empfohlen, eine CAPTCHA-Komponente in einem Fragment oder einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

* [Verwenden von CAPTCHA in adaptiven Formularen](/help/forms/using/captcha-adaptive-forms.md)
* [Verwenden von Turnstile Captcha in adaptiven Formularen](/help/forms/using/integrate-adaptive-forms-turnstile.md)
