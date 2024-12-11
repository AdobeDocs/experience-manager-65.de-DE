---
title: Wie wird Turnstile in einem AEM adaptiven Formular 6.5 verwendet?
description: Verbessern Sie die Formularsicherheit mit dem Turnstile-Dienst mühelos. Schrittweise Anleitung enthalten!
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: bed93ce3-89db-477a-8316-7598275e4bca
source-git-commit: 94a9f4087e36bfe5701ad9aafd4e8446ca643ddf
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 21%

---

# AEM Forms-Umgebung mit Turnstile verbinden {#connect-your-forms-environment-with-turnstile-service}

<!--
<span class="preview">This feature is based on Feature Toggle id `FT_FORMS-12407`. To enable the feature, follow the steps given in the [Enable Feature Toggle](/help/forms/using/enable-feature-toggle.md) article. </span>
-->

<span class="preview">Diese Funktion ist standardmäßig nicht aktiviert. Sie können von Ihrer offiziellen Adresse an aem-forms-ea@adobe.com schreiben, um Zugriff auf die Funktion anzufordern.</span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms 6.5 unterstützt die folgenden CAPTCHA-Lösungen:

* [Turnstile Captcha](/help/forms/using/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)


<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Integrieren der AEM Forms-Umgebung mit dem Turnstile Captcha

Das Turnstile Captcha von Cloudflare ist eine Sicherheitsmaßnahme, um Formulare und Sites vor automatisierten Bots, bösartigen Angriffen, Spam und unerwünschtem automatisierten Traffic zu schützen. Bei der Formularübermittlung wird ein Kontrollkästchen angezeigt, mit dem überprüft wird, ob es sich um menschliche Benutzende handelt, bevor das Formular übermittelt werden kann.

>[!VIDEO](https://video.tv.adobe.com/v/3440940/)

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um die Turnstile für AEM Forms zu konfigurieren, müssen Sie den [Turnstile-SiteKey und den geheimen Schlüssel](https://developers.cloudflare.com/turnstile/get-started/) von der Turnstile-Website abrufen.

### Turnstile konfigurieren {#steps-to-configure-hcaptcha}

Führen Sie die folgenden Schritte aus, um AEM Forms in den Turnstile-Dienst zu integrieren:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, die zum Verbinden von AEM Forms mit externen Diensten verwendet werden. So erstellen Sie einen Konfigurations-Container:
   1. Öffnen Sie Ihre AEM Forms-Umgebung.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurationsbrowser wählen Sie einen vorhandenen Ordner aus oder erstellen einen neuen Ordner:
      * So erstellen Sie einen **neuen Ordner** und aktivieren die Cloud-Konfigurationen:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Namen und einen Titel ein und aktivieren Sie die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * Aktivieren der Cloud-Konfiguration für einen **vorhandenen Ordner**:
         1. Wählen Sie im Konfigurationsbrowser den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Klicken Sie auf **[!UICONTROL Speichern und schließen]** , um die Konfiguration zu speichern.

1. Konfigurieren Sie Ihre Cloud Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und klicken Sie auf **[!UICONTROL Turnstile]**.
      ![Turnstile in Cloud Services](assets/turnstile-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Klicken Sie auf **[!UICONTROL Erstellen]**.
      ![Konfigurations-Turnstile](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Widget-Typ]** als verwaltet, nicht interaktiv oder unsichtbar an.
   1. Geben Sie weitere Details wie **[!UICONTROL Titel]**, **[!UICONTROL Name]** an.
   1. Geben Sie den **[!UICONTROL Site-Schlüssel]** und den **[!UICONTROL geheimen Schlüssel]** für den Turnstile-Dienst [ an, der unter Voraussetzung ](#prerequisite) abgerufen wurde.
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit der Turnstile](assets/config-turntstile.png)

   >[!NOTE]
   > Benutzer müssen die clientseitige JavaScript-Validierungs-URL und die serverseitige Validierungs-URL nicht ändern, da sie bereits für die Turnstile-Validierung vorausgefüllt sind.

   Sobald der Turnstile Captcha-Dienst konfiguriert ist, ist er für die Verwendung in Ihrem adaptiven Formular verfügbar.

## Verwenden der Turnstile in einem adaptiven Formular {#using-turnstile-aem-6.5}

1. Öffnen Sie Ihre AEM Forms-Umgebung.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**. Wählen Sie in **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Turnstile verbindet.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen Konfigurations-Container zum Konfigurieren des Captcha-Dienstes haben, erfahren Sie im Abschnitt [Konfigurieren der Turnstile](#configure-turnstile-steps-to-configure-hcaptcha) , wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]** , um das adaptive Formular im Editor zu öffnen.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die Komponente **[!UICONTROL Captcha]** aus und klicken Sie auf das Symbol für die Eigenschaften ![Eigenschaften-Symbol](assets/configure-icon.svg) . Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden Eigenschaften an:

   <!--![Turnstile v2](assets/turnstile-settings-v2.png)-->
   ![Turnstile der Cloudfare-Version 1](assets/turnstile-setting-v1.png)

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor einfach mit ihrem eindeutigen Titel identifizieren.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine Cloud-Konfiguration für die Turnstile aus.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für die Validierung von Captcha bei Formularübermittlung oder Benutzeraktion bereit.
   * **[!UICONTROL Captcha-Dienst]:** Wählen Sie den CAPTCHA-Dienst für Ihre Formularübermittlung aus, hier wählen Sie Turnstile®.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie Ihre Cloud-Konfiguration für Turnstile® aus.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgelistet ist, finden Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service) Informationen zum Erstellen eines Cloud Service, der Ihre AEM Forms-Umgebung mit dem Turnstile-Dienst verbindet.

   * **[!UICONTROL Fehlermeldung]:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **Captcha-Größe:** Sie können die Anzeigegröße des Chaptcha®-Challenger-Dialogfelds auswählen. Verwenden Sie die Option **[!UICONTROL Kompakt]** , um eine kleine Größe anzuzeigen, und die Option **[!UICONTROL Normal]**, um ein relativ großes Chaptcha®-Anforderungsdialogfeld anzuzeigen.

1. Wählen Sie **[!UICONTROL Fertig]**.


Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Benutzer die vom Turnstile-Dienst ausgehende Herausforderung erfolgreich löscht.

![Turnstile-Herausforderung](assets/turnstile-challenge.png)


## Häufig gestellte Fragen

* **Q: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **s:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

* [Verwenden von CAPTCHA in adaptiven Formularen](/help/forms/using/captcha-adaptive-forms.md)
* [Verwenden von hCaptcha in adaptiven Formularen](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)
