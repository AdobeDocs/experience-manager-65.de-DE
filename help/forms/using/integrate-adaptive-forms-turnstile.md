---
title: Verwenden von Turnstile in einem adaptiven Formular von AEM 6.5?
description: Mit dem Turnstile-Service können Sie die Formularsicherheit verbessern. Schrittweise Anleitung enthalten.
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: bed93ce3-89db-477a-8316-7598275e4bca
source-git-commit: 94a9f4087e36bfe5701ad9aafd4e8446ca643ddf
workflow-type: ht
source-wordcount: '851'
ht-degree: 100%

---

# Verbinden Ihrer AEM Forms-Umgebung mit Turnstile {#connect-your-forms-environment-with-turnstile-service}

<!--
<span class="preview">This feature is based on Feature Toggle id `FT_FORMS-12407`. To enable the feature, follow the steps given in the [Enable Feature Toggle](/help/forms/using/enable-feature-toggle.md) article. </span>
-->

<span class="preview">Diese Funktion ist standardmäßig nicht aktiviert. Sie können von Ihrer offiziellen Adresse aus an aem-forms-ea@adobe.com schreiben, um Zugriff auf die Funktion zu beantragen.</span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms 6.5 unterstützt die folgenden CAPTCHA-Lösungen:

* [Turnstile Captcha](/help/forms/using/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)


<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Integrieren der AEM Forms-Umgebung mit Turnstile Captcha

Turnstile Captcha von Cloudflare bietet eine Sicherheitsmaßnahme zum Schutz von Formularen vor automatisierten Bots, bösartigen Angriffen, Spams und unerwünschtem automatisierten Traffic. Bei der Formularübermittlung wird ein Kontrollkästchen angezeigt, mit dem überprüft wird, ob es sich um menschliche Benutzende handelt, bevor das Formular übermittelt werden kann.

>[!VIDEO](https://video.tv.adobe.com/v/3440940/)

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um Turnstile für AEM Forms zu konfigurieren, müssen Sie den [Site-Schlüssel von Turnstile sowie den geheimen Schlüssel](https://developers.cloudflare.com/turnstile/get-started/) von der Turnstile-Website abrufen.

### Konfigurieren von Turnstile {#steps-to-configure-hcaptcha}

So integrieren Sie AEM Forms mit dem Turnstile-Service:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM Forms mit externen Diensten verbunden wird. So erstellen Sie einen Konfigurations-Container:
   1. Öffnen Sie Ihre AEM Forms-Umgebung.
   1. Navigieren Sie zu **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurations-Browser können Sie einen vorhandenen Ordner auswählen oder einen neuen Ordner erstellen:
      * So erstellen Sie einen **neuen Ordner** und aktivieren die Cloud-Konfigurationen:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und einen Titel an und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen **vorhandenen Ordner**:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern.

1. So konfigurieren Sie Ihre Cloud-Services:
   1. Navigieren Sie in Ihrer AEM-Autorinstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud-Services]** und klicken Sie auf **[!UICONTROL Turnstile]**.
      ![Turnstile in Cloud-Services](assets/turnstile-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der wie im vorherigen Abschnitt beschrieben erstellt oder aktualisiert wurde. Klicken Sie auf **[!UICONTROL Erstellen]**.
      ![Konfiguration von Turnstile](assets/config-hcaptcha.png)
   1. Geben Sie den **[!UICONTROL Widget-Typ]** als verwaltet, nicht interaktiv oder unsichtbar an.
   1. Geben Sie weitere Details an wie **[!UICONTROL Titel]** und **[!UICONTROL Name]**.
   1. Geben Sie den **[!UICONTROL Site-Schlüssel]** und den **[!UICONTROL geheimen Schlüssel]** für den Turnstile-Dienst an, [die Sie beide gemäß der obigen Voraussetzung abgerufen haben](#prerequisite).
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren des Cloud-Services für die Verbindung Ihrer AEM Forms-Umgebung mit Turnstile](assets/config-turntstile.png)

   >[!NOTE]
   > Benutzende brauchen die Client-seitige JavaScript-Validierungs-URL und die Server-seitige Validierungs-URL nicht zu ändern, da sie bereits für die Turnstile-Validierung vorausgefüllt sind.

   Sobald der Turnstile-Captcha-Dienst konfiguriert ist, kann er in adaptiven Formularen verwendet werden.

## Verwenden von Turnstile in einem adaptiven Formular {#using-turnstile-aem-6.5}

1. Öffnen Sie Ihre AEM Forms-Umgebung.
1. Navigieren Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**. Wählen Sie unter **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Turnstile verbindet.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen Konfigurations-Container für den CAPTCHA-Service haben, erfahren Sie im Abschnitt [Konfigurieren von Turnstile](#configure-turnstile-steps-to-configure-hcaptcha), wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**, um Ihr adaptives Formular im Editor zu öffnen.
1. Ziehen Sie die **[!UICONTROL Captcha]**-Komponente im Komponenten-Browser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die **[!UICONTROL CAPTCHA]**-Komponente aus und klicken Sie auf das Symbol ![Eigenschaften](assets/configure-icon.svg). Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden Eigenschaften an:

   <!--![Turnstile v2](assets/turnstile-settings-v2.png)-->
   ![Cloudfare Turnstile v1](assets/turnstile-setting-v1.png)

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor durch ihren eindeutigen Titel leicht identifizieren.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine für Turnstile konfigurierte Cloud-Konfiguration aus.
   * **[!UICONTROL Validierungsmeldung]:** Geben Sie eine Validierungsmeldung zur Validierung von Captcha bei der Formularübermittlung oder bei einer Benutzeraktion ein.
   * **[!UICONTROL Captcha-Service]:** Wählen Sie den CAPTCHA-Service für Ihre Formularübermittlung aus. Hier wählen Sie Turnstile®.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine für Turnstile® konfigurierte Cloud-Konfiguration aus.
     >[!NOTE]
     >Es kann sein, dass Sie für ähnliche Zwecke über mehrere Cloud-Konfigurationen in Ihrer Umgebung verfügen. Wählen Sie den Service daher sorgfältig aus. Wenn kein Service aufgeführt ist, lesen Sie [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service), um zu erfahren, wie Sie einen Cloud-Service erstellen, der Ihre AEM Forms-Umgebung mit dem Turnstile-Service verbindet.

   * **[!UICONTROL Fehlermeldung]:** Geben Sie die Fehlermeldung an, die den Benutzenden angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **Captcha-Größe:** Sie können die Anzeigegröße des hCaptcha®-Challenge-Dialogfelds auswählen. Verwenden Sie die Option **[!UICONTROL Compact]**, um ein kleines hCaptcha®-Challenge-Dialogfeld anzuzeigen, und die Option **[!UICONTROL Normal]** für ein relativ großes Dialogfeld.

1. Wählen Sie **[!UICONTROL Fertig]** aus.


Jetzt sind nur legitime Formulare zur Übermittlung zulässig, bei denen die Person, die das Formular ausfüllt, die vom Turnstile-Service ausgehende Herausforderung erfolgreich löst.

![Turnstile-Challenge](assets/turnstile-challenge.png)


## Häufig gestellte Fragen

* **F: Kann ich mehr als eine Captcha-Komponente in einem adaptiven Formular verwenden?**
* **Antwort:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird davon abgeraten, eine Captcha-Komponente in einem Fragment oder einem Bereich zu verwenden, das bzw. der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

* [Verwenden von CAPTCHA in adaptiven Formularen](/help/forms/using/captcha-adaptive-forms.md)
* [Verwenden von hCaptcha in adaptiven Formularen](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)
