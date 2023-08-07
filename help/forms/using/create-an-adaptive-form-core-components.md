---
title: Erstellen eines adaptiven Formulars
seo-title: Learn how to create a Core Components based Adaptive Form on AEM 6.5 Forms.
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
seo-description: Learn how to create an Adaptive Form using [!DNL Experience Manager Forms]. Adaptive Forms are responsive HTML5 forms that streamline information gathering and processing. Dig deeper on how to create an Adaptive Form based on a Form Data Model and XML or JSON schema.
Keywords: create adaptive form core component, create core component based adaptive form, creare adaptive form
products: SG_EXPERIENCEMANAGER/6.5/FORMS
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
source-git-commit: 3bc61e56d2fcd9f32c37a7ea04b0ffc6728bfc56
workflow-type: tm+mt
source-wordcount: '1725'
ht-degree: 32%

---


# Erstellen von Kernkomponenten-basierten adaptiven Forms {#creating-an-adaptive-form-core-components}


<span class="preview"> Adobe empfiehlt die Verwendung von Kernkomponenten zu [Adaptive Forms zu einer AEM Sites-Seite hinzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) oder [eigenständige adaptive Forms erstellen](/help/forms/using/create-an-adaptive-form-core-components.md). </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

**Gilt für:** ✅ Kernkomponenten des adaptiven Formulars ❎ [Adaptive Form Foundation-Komponenten](/help/forms/using/create-adaptive-form.md).

Adaptive Formulare bieten Ihnen die Möglichkeit, interaktive, responsive und dynamische adaptive Formulare zu erstellen. AEM Forms bietet eine benutzerfreundliche Benutzeroberfläche für Unternehmen, mit der Sie schnell Adaptive Forms erstellen können. Die Benutzeroberfläche bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Adobe empfiehlt die Nutzung dieser modernen und erweiterbaren Komponenten zur Entwicklung von adaptiven Formularen.

* [Foundation-Komponenten adaptiver Formulare](creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie Formulare erstellen, empfiehlt Adobe die Verwendung von  [Adaptive Forms-Kernkomponenten](/help/forms/using/create-adaptive-form.md) , um eine adaptive Forms zu erstellen.

## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Aktivieren der adaptiven Forms-Kernkomponenten für Ihre Umgebung**: AEM Projektarchetyp Version 41 oder höher ist erforderlich, um [Kernkomponenten für Ihre Umgebung aktivieren](/help/forms/using/enable-adaptive-forms-core-components.md). Wenn Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die **Adaptive Forms (Kernkomponente)** Vorlage und Arbeitsflächendesign werden Ihrer Umgebung hinzugefügt.

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll.

  >[!NOTE]
  >
  > Wenn Sie über keine Vorlage für **adaptive Formulare (Kernkomponente)** in Ihrer Umgebung verfügen, [aktivieren Sie die Kernkomponenten für adaptive Formulare für Ihre Umgebung](/help/forms/using/enable-adaptive-forms-core-components.md). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die Vorlage für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt.

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Die `Canvas` -Design wird standardmäßig hinzugefügt, wenn Sie Kernkomponenten für Ihre Umgebung aktivieren. Sie können auch [Standarddesigns herunterladen und anpassen](create-or-customize-themes-for-adaptive-forms-core-components.md).

* **Berechtigungen**: Fügen Sie Ihre Benutzerinnen und Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der [!DNL forms-users]-Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste formularspezifischer Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form}

1. Bei Ihrer lokalen [AEM Autoreninstanz](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=en#author-and-publish-installs).

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, tippen Sie in der oberen linken Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Tippen **[!UICONTROL Erstellen]**  > **[!UICONTROL Adaptive Forms erstellen]**.

1. Wählen Sie eine Vorlage für adaptive Forms-Kernkomponenten aus und klicken Sie auf **[!UICONTROL Nächste]**.

1. Die **[!UICONTROL Eigenschaften hinzufügen]** angezeigt. Geben Sie die Werte für die folgenden Eigenschaftenfelder an. Die Felder „Titel“ und „Name“ sind obligatorisch.

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden.
   * **[!UICONTROL Beschreibung:]** Gibt detaillierte Informationen zum Formular an.
   * **[!UICONTROL Design-Client-Bibliothek]:** Gibt das Design für ein adaptives Formular an. Standardmäßig wird die Variable `adaptiveform.theme.canvas3` Design ausgewählt ist. Sie können auch ein anderes Design als das **[!UICONTROL Design-Client-Bibliothek]** Dropdown-Menü.
   * **[!UICONTROL Konfigurations-Container:]**  Definiert einen Speicherort, an dem Konfigurationsdateien für Adaptive Forms gespeichert werden. Diese Konfigurationsdateien enthalten Einstellungen und Eigenschaften, die sich auf das Verhalten und Erscheinungsbild von Adaptive Forms beziehen.
   * **[!UICONTROL Tags:]** Gibt Tags an, die eine eindeutige Identifizierung des adaptiven Formulars ermöglichen. Tags erleichtern die Suche nach dem Formular. Um die Tags zu erstellen, geben Sie neue Tag-Namen in das Feld **[!UICONTROL Tags]** ein.
1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt, und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.


1. Tippen **[!UICONTROL Bearbeiten]** , um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet und zeigt die in der Vorlage verfügbaren Inhalte an. Außerdem wird die Seitenleiste angezeigt, um das neu erstellte Formular anzupassen.


## Verwenden der Kernkomponenten des adaptiven Forms zum Erstellen Ihres Formulars

Nachdem Sie das Formular zur Bearbeitung geöffnet haben, können Sie verfügbare Adaptive Forms-Kernkomponenten verwenden, um Ihrem Formular Formularfelder hinzuzufügen. Sie können per Drag &amp; Drop oder mit dem + [Komponente einfügen] -Option, um diese Komponenten einem Formular hinzuzufügen. Weitere Informationen AEM die Dokumentation zu Kernkomponenten [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#components). Sie können auch [https://aemcomponents.dev/](https://aemcomponents.dev/) besuchen, um die verfügbaren Kernkomponenten in Aktion zu sehen.

## Konfigurieren der Sendeaktion für ein adaptives Formular {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Sie wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche Senden klickt. Adaptive Formulare enthalten einige vordefinierte Übermittlungsaktionen. Sie können auch eine standardmäßige Übermittlungsaktion erweitern, um eine eigene benutzerdefinierte Übermittlungsaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.

1. Klicken Sie auf  **[!UICONTROL Einsendung]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen und eine Sendeaktion zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

1. Auswählen und Konfigurieren eines **[!UICONTROL Übermittlungsaktion]**, basierend auf Ihren Anforderungen. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/using/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leiten Sie den Benutzer auf eine Seite um oder zeigen Sie bei der Formularübermittlung eine Dankesnachricht an

Beim Senden eines Formulars können Sie den Benutzer zu einer anderen Webseite oder Nachricht umleiten. So leiten Sie den Benutzer um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Einsendung]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Zu URL umleiten]** und eine AEM Sites-Seite durchsuchen und auswählen oder die URL einer externen Seite angeben.

   * Um eine benutzerdefinierte Nachricht oder Dankesnachricht zu konfigurieren, wählen Sie für die Option &quot;Senden&quot;die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie eine Nachricht im **[!UICONTROL Nachrichteninhalt]** ankreuzen. Dies ist ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Schema oder Formulardatenmodell für ein adaptives Formular konfigurieren {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie basierend auf der Anforderung Ihr Formular mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen eines JSON-Schemas und Hochladen in Ihre Umgebung](/help/forms/using/adaptive-form-json-schema-form-model.md)
* [Formulardatenmodell erstellen](/help/forms/using/create-form-data-models.md)

### JSON-Schema oder Formulardatenmodell für Ihr Formular konfigurieren

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Datenmodell]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um ein JSON-Schema oder Formulardatenmodell zu konfigurieren.](/help/forms/using/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Wählen und konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell basierend auf Ihren Anforderungen:

   * Wenn Sie die **[!UICONTROL Formularmodell]** verwenden, verwenden Sie die **[!UICONTROL Formulardatenmodell auswählen]** -Option, um ein vorkonfiguriertes Formulardatenmodell auszuwählen.
   * Wenn Sie die **[!UICONTROL Schema]** verwenden, verwenden Sie die **[!UICONTROL Schema]** -Option, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!NOTE]
>
> Sie können das JSON-Schema oder das Formulardatenmodell für ein adaptives Formular mithilfe der Eigenschaften des Guide-Containers bearbeiten.

## Konfigurieren eines Vorbefüllungs-Dienstes  {#configure-prefill-service-for-form}

Sie können den Vorbefüllungs-Dienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungs-Dienstes](/help/forms/using/prepopulate-adaptive-form-fields.md)
* [Vorfülldienst für Formulardatenmodell verwenden](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle, um Felder eines adaptiven Formulars im Voraus auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungs-Dienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungs-Dienst im Voraus auszufüllen. Der Vorbefüllungs-Dienst für Formulardatenmodelle verwendet die [Dienst für konfiguriertes Formulardatenmodell abrufen](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) , um Daten abzurufen. So verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle für ein adaptives Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Klicken Sie auf die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-container-prefill-service.png)
1. Formulardatenmodell auswählen. Öffnen Sie die **[!UICONTROL Allgemein]** Registerkarte. Wählen Sie im Vorbefüllungs-Dienst die Option **[!UICONTROL Vorfüllservice für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es das Vorfüllen des Formulardatenmodells verwendet. Sie können jetzt die [Regeleditor](rule-editor.md) , um Regeln zum Vorausfüllen von Formularfeldern zu erstellen.

<!--
## Edit Form Model properties of an Adaptive Form {#edit-form-model}

1. Select the Adaptive Form and tap ![Page information](/help/forms/using/assets/configure-icon.svg) > **[!UICONTROL Open Properties]**. The Form Properties page opens. 

1. Go to the **[!UICONTROL Form Model]** tab and choose a form model. If the Adaptive Form is without a form model, you have the freedom to choose either a JSON schema or a form data model. On the other hand, if the Adaptive Form is already based on a form model, you have the option to switch to another form model of the same type. For instance, if the form is using a JSON schema, you can easily switch to another JSON schema, and similarly if the form is using a Form Data Model, you can switch to another Form Data Model. 

1. Tap **[!UICONTROL Save]** to save the properties.
-->

## Wie geht es weiter

* [Verwenden Sie den Regeleditor, um dem Formular dynamisches Verhalten hinzuzufügen](rule-editor.md)
* [Erstellen oder Anpassen von Designs für auf Kernkomponenten basierende adaptive Forms](create-or-customize-themes-for-adaptive-forms-core-components.md)
* Erstellen einer Vorlage für auf Kernkomponenten basierende adaptive Forms

## Siehe auch

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](create-an-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)

