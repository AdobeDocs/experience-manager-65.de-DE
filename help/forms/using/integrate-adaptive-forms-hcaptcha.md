---
title: Wie wird Captcha&reg; in einem AEM 6.5 Forms verwendet?
description: Mit dem hCaptcha®-Dienst können Sie die Formularsicherheit optimieren. Schrittweise Anleitung enthalten!
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 6aa7a0a5-bd45-4628-abd0-312a9e6cf6fe
source-git-commit: 94a9f4087e36bfe5701ad9aafd4e8446ca643ddf
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 27%

---

# Verbinden Ihrer AEM Forms-Umgebung mit Captcha® {#connect-your-forms-environment-with-hcaptcha-service}

<!--
<span class="preview">This feature is based on Feature Toggle id `FT_FORMS-12407`. To enable the feature, follow the steps given in the [Enable Feature Toggle](/help/forms/using/enable-feature-toggle.md) article. </span>
-->

<span class="preview">Diese Funktion ist standardmäßig nicht aktiviert. Sie können von Ihrer offiziellen Adresse an aem-forms-ea@adobe.com schreiben, um Zugriff auf die Funktion anzufordern.</span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

Zusätzlich zu hCaptcha® unterstützt AEM Forms 6.5 die folgenden CAPTCHA-Lösungen:

* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [Cloudflare Turnstile](/help/forms/using/integrate-adaptive-forms-turnstile.md)

## Integrieren der AEM Forms-Umgebung mit Captcha®

Der hCaptcha®-Dienst schützt Ihre Formulare vor Bots, Spam und automatisiertem Missbrauch. Er führt einen Kontrollkästchen-Widget-Test durch und ermittelt anhand der Benutzerantwort, ob ein Mensch oder ein Bot mit dem Formular interagiert. Dabei wird verhindert, dass Benutzende fortfahren, wenn der Test fehlschlägt. Dies erhöht die Sicherheit von Online-Transaktionen, indem Bots keinen Spam senden oder andere bösartige Aktivitäten durchführen können.

AEM 6.5 Adaptive Forms unterstützt Captcha&amp;reg. Sie können es verwenden, um eine Herausforderung für ein Kontrollkästchen-Widget bei der Formularübermittlung darzustellen.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->


### Voraussetzungen für die Integration der AEM Forms-Umgebung in Captcha® {#prerequisite}

Um Captcha® mit AEM Forms zu konfigurieren, müssen Sie den Site-Schlüssel [hCaptcha® und den geheimen Schlüssel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) von der hCaptcha®-Website abrufen.

### Captcha® konfigurieren {#steps-to-configure-hcaptcha}

Führen Sie die folgenden Schritte aus, um AEM Forms mit dem Captcha®-Dienst zu integrieren:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms-Umgebung, der Cloud-Konfigurationen enthält, mit denen AEM mit externen Diensten verbunden werden. So erstellen Sie einen Konfigurations-Container:
   1. Öffnen Sie Ihre AEM Forms-Umgebung.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurationsbrowser können Sie einen vorhandenen Ordner auswählen oder einen neuen Ordner erstellen:
      * So erstellen Sie einen neuen Ordner und aktivieren die Cloud-Konfigurationen:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Namen und einen Titel ein und aktivieren Sie die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * Aktivieren der Cloud-Konfiguration für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie dann **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Speichern und schließen]** , um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren Sie Ihre Cloud Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und klicken Sie auf **[!UICONTROL Captcha®]**.
      ![hCaptcha® in ui](assets/hcaptcha-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfiguration von Captcha®](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Titel]**, <!--**[!UICONTROL Name]**--> an **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL geheimer Schlüssel]** für den Captcha®-Dienst [erhalten in Voraussetzung](#prerequisite).
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit Captcha®](assets/create-hcaptcha-config.png)

   >[!NOTE]
   > Benutzer müssen die [clientseitige JavaScript-Validierungs-URL](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) und die [serverseitige Validierungs-URL](https://docs.hcaptcha.com/#verify-the-user-response-server-side) nicht ändern, da sie bereits für die Captcha®-Validierung vorausgefüllt sind.

   Sobald der hCAPTCHA-Dienst konfiguriert ist, steht er zur Verwendung in Ihrem adaptiven Formular zur Verfügung.

## Verwenden von Captcha® in einem adaptiven Formular {#using-hCaptcha-in-aem-6.5}

1. Öffnen Sie Ihre AEM Forms-Umgebung.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie im **[!UICONTROL Konfigurations-Container]** den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Captcha verbindet.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen Konfigurations-Container für Captcha haben, erfahren Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#configure-hcaptcha-steps-to-configure-hcaptcha) , wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/using/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]** , um das Formular im Editor zu öffnen.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die Komponente **[!UICONTROL Captcha]** aus und klicken Sie auf das Symbol &quot;Eigenschaften&quot;![Eigenschaften&quot;](assets/configure-icon.svg), um das Dialogfeld &quot;Eigenschaften&quot;zu öffnen. Geben Sie die folgenden Eigenschaften an:

   ![hCaptcha® v1](assets/config-hcaptcha-v1-img.png)

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für Ihre Captcha-Validierung bei der Formularübermittlung oder bei einer Benutzeraktion bereit.
   * **[!UICONTROL Captcha-Dienst]:** Wählen Sie den CAPTCHA-Dienst für die Formularübermittlung aus, hier wählen Sie Captcha® aus.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie Ihre für Captcha® konfigurierte Cloud-Konfiguration aus.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgeführt ist, finden Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#connect-your-forms-environment-with-hcaptcha-service) Informationen zum Erstellen eines Cloud Service, der Ihre AEM Forms-Umgebung mit dem Captcha®-Dienst verbindet.

   * **[!UICONTROL Fehlermeldung]:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **[!UICONTROL Captcha-Größe]:** Sie können die Anzeigegröße des Chaptcha®-Challenge-Dialogfelds auswählen. Verwenden Sie die Option **[!UICONTROL Kompakt]** , um eine kleine Größe anzuzeigen, und die Option **[!UICONTROL Normal]**, um ein relativ großes Chaptcha®-Anforderungsdialogfeld anzuzeigen, oder **[!UICONTROL Unsichtbar]**, um hCaptcha® zu validieren, ohne das Kontrollkästchen-Widget auf der Benutzeroberfläche explizit darzustellen.

1. Wählen Sie **[!UICONTROL Fertig]**.


Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Formularbenutzer die vom Captcha®-Dienst ausgehende Herausforderung erfolgreich löscht.

**hCaptcha® ist eine eingetragene Marke von Intuition Machines, Inc.**


## Häufig gestellte Fragen

* **Q: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **s:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

* [Verwenden von CAPTCHA in adaptiven Formularen](/help/forms/using/captcha-adaptive-forms.md)
* [Verwenden von Turnstile Captcha in adaptiven Formularen](/help/forms/using/integrate-adaptive-forms-turnstile.md)
