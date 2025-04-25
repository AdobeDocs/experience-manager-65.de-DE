---
title: Verwenden von Drehkreuz in einem adaptiven AEM-Formular 6.5
description: Verbessern Sie die Formularsicherheit mit dem Drehkreuz-Service mühelos. Schrittweise Anleitung enthalten!
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: bed93ce3-89db-477a-8316-7598275e4bca
source-git-commit: 94a9f4087e36bfe5701ad9aafd4e8446ca643ddf
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 21%

---

# Verbinden Ihrer AEM Forms-Umgebung mit Turnstile {#connect-your-forms-environment-with-turnstile-service}

<!--
<span class="preview">This feature is based on Feature Toggle id `FT_FORMS-12407`. To enable the feature, follow the steps given in the [Enable Feature Toggle](/help/forms/using/enable-feature-toggle.md) article. </span>
-->

<span class="preview">Diese Funktion ist standardmäßig nicht aktiviert. Sie können an Ihre offizielle Adresse aem-forms-ea@adobe.com schreiben, um Zugriff auf die Funktion zu beantragen.</span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms 6.5 unterstützt die folgenden CAPTCHA-Lösungen:

* [Turnstile Captcha](/help/forms/using/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)


<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Integrieren der AEM Forms-Umgebung mit Turnstile Captcha

Cloudflare&#39;s Turnstile Captcha ist eine Sicherheitsmaßnahme, die darauf abzielt, Formulare und Websites vor automatischen Bots, bösartigen Angriffen, Spam und unerwünschtem automatisierten Traffic zu schützen. Bei der Formularübermittlung wird ein Kontrollkästchen angezeigt, mit dem überprüft wird, ob es sich um menschliche Benutzende handelt, bevor das Formular übermittelt werden kann.

>[!VIDEO](https://video.tv.adobe.com/v/3440940/)

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um das Drehkreuz für AEM Forms zu konfigurieren, müssen Sie den [Standortschlüssel und geheimen Schlüssel des Drehkreuzes](https://developers.cloudflare.com/turnstile/get-started/) von der Website des Drehkreuzes abrufen.

### Drehkreuz konfigurieren {#steps-to-configure-hcaptcha}

So integrieren Sie AEM Forms mit dem Drehkreuz-Service:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM Forms mit externen Services verbunden wird. So erstellen Sie einen Konfigurations-Container:
   1. Öffnen Sie Ihre AEM Forms-Umgebung.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurations-Browser können Sie einen vorhandenen Ordner auswählen oder einen neuen Ordner erstellen:
      * So erstellen Sie einen **neuen Ordner** und aktivieren die Cloud-Konfigurationen:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und einen Titel an und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Cloud-Konfiguration für einen **Ordner**:
         1. Wählen Sie im Konfigurationsbrowser den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie **[!UICONTROL Speichern und schließen]** um die Konfiguration zu speichern.

1. Konfigurieren Sie Ihre Cloud Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und klicken Sie auf **[!UICONTROL Drehkreuz]**.

      ![Drehkreuz in Cloud Services ](assets/turnstile-in-ui.png)
   1. Wählen Sie einen erstellten oder aktualisierten Konfigurations-Container aus, wie im vorherigen Abschnitt beschrieben. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurations-Drehkreuz](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Widget-Typ]** als verwaltet, nicht interaktiv oder unsichtbar an.
   1. Geben Sie weitere Details an **[!UICONTROL Titel]**, **[!UICONTROL Name]**.
   1. Geben Sie **[!UICONTROL Standortschlüssel]** und **[!UICONTROL Geheimschlüssel]** für den Drehkreuz-Dienst an, [ in der Voraussetzung erhalten ](#prerequisite).
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren Sie den Cloud Service, um Ihre AEM Forms-Umgebung mit Turnstile zu verbinden](assets/config-turntstile.png)

   >[!NOTE]
   > Benutzende müssen die Client-seitige JavaScript-Validierungs-URL und die Server-seitige Validierungs-URL nicht ändern, da sie bereits für die Drehkreuz-Validierung vorausgefüllt sind.

   Sobald der Service „Drehkreuz-CAPTCHA“ konfiguriert ist, kann er in Ihrem adaptiven Formular verwendet werden.

## Verwenden eines Drehkreuzes in einem adaptiven Formular {#using-turnstile-aem-6.5}

1. Öffnen Sie Ihre AEM Forms-Umgebung.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**. Wählen **[!UICONTROL unter]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Turnstile verbindet.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen Konfigurations-Container für den CAPTCHA-Service haben, erfahren Sie im Abschnitt [Konfigurieren eines ](#configure-turnstile-steps-to-configure-hcaptcha)&quot;, wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**, um Ihr adaptives Formular im Editor zu öffnen.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die **[!UICONTROL CAPTCHA]**-Komponente aus und klicken Sie auf das Symbol ![Eigenschaften](assets/configure-icon.svg). Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden Eigenschaften an:

   <!--![Turnstile v2](assets/turnstile-settings-v2.png)-->
   ![Cloudfare Turnstile v1](assets/turnstile-setting-v1.png)

   * **[!UICONTROL Titel]:** Geben Sie den Titel für die CAPTCHA-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor durch ihren eindeutigen Titel leicht identifizieren.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine Cloud-Konfiguration aus, die für Drehkreuz konfiguriert ist.
   * **[!UICONTROL Validierungsmeldung]:** Geben Sie eine Validierungsmeldung zur Validierung von CAPTCHA bei der Formularübermittlung oder bei einer Benutzeraktion ein.
   * **[!UICONTROL CAPTCHA-]:** Wählen Sie den CAPTCHA-Dienst für die Formularübermittlung aus, hier wählen Sie Drehkreuz®.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie Ihre für Turnstile konfigurierte Cloud-Konfiguration ®.

     >[!NOTE]
     >Sie können in Ihrer Umgebung mehrere Cloud-Konfigurationen für einen ähnlichen Zweck verwenden. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Service aufgeführt ist, erfahren Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service), wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem Turnstile-Service verbindet.

   * **[!UICONTROL Fehlermeldung]:** Geben Sie die Fehlermeldung an, die Benutzern angezeigt werden soll, wenn die CAPTCHA-Übermittlung fehlschlägt.
   * **CAPTCHA-Größe** Sie können die Anzeigegröße des Dialogfelds für die hCAPTCHA®-Abfrage auswählen. Verwenden Sie die **[!UICONTROL Compact]**-Option, um ein kleines Format anzuzeigen, und **[!UICONTROL Normal]**, um ein relativ großes hCAPTCHA®-Dialogfeld anzuzeigen.

1. Wählen Sie **[!UICONTROL Fertig]**.


Für die Formularübermittlung sind jetzt nur noch Formulare zulässig, in denen der Formularbenutzer die vom Dienst „Drehkreuz“ ausgehende Herausforderung erfolgreich löscht.

![Turnstile Challenge](assets/turnstile-challenge.png)


## Häufig gestellte Fragen

* **F: Kann ich mehr als eine CAPTCHA-Komponente in einem adaptiven Formular verwenden?**
* **A:** Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird nicht empfohlen, eine CAPTCHA-Komponente in einem Fragment oder einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

* [Verwenden von CAPTCHA in adaptiven Formularen](/help/forms/using/captcha-adaptive-forms.md)
* [Verwenden von hCaptcha in adaptiven Formularen](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)
