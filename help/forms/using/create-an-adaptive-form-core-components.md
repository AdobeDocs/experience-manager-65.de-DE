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
exl-id: ee596672-b0b5-42e9-a139-72f90287bf3b
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1794'
ht-degree: 50%

---

# Erstellen Sie adaptive Formulare auf Grundlage der Kernkomponenten {#creating-an-adaptive-form-core-components}


<span class="preview"> Adobe empfiehlt die Verwendung von Kernkomponenten für [Adaptive Forms zu einer AEM Sites-Seite hinzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) oder [eigenständige adaptive Forms erstellen](/help/forms/using/create-an-adaptive-form-core-components.md). </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

**Gilt für:** ✅ Kernkomponenten des adaptiven Formulars ❎ [Adaptive Form Foundation-Komponenten](/help/forms/using/create-adaptive-form.md).

Mit Adaptive Forms können Sie Formulare erstellen, die ansprechend, reaktionsfähig, dynamisch und anpassungsfähig sind. AEM Forms bietet eine benutzerfreundliche Benutzeroberfläche für Unternehmen, mit der Sie schnell Adaptive Forms erstellen können. Die Benutzeroberfläche bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Adobe empfiehlt die Verwendung dieser modernen und erweiterbaren Komponenten zur Entwicklung von Adaptive Forms.

* [Foundation-Komponenten adaptiver Formulare](creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie Formulare erstellen, empfiehlt Adobe,  [Adaptive Forms-Kernkomponenten](/help/forms/using/create-adaptive-form.md) , um eine adaptive Forms zu erstellen.

## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Aktivieren der adaptiven Forms-Kernkomponenten für Ihre Umgebung**: AEM Projektarchetyp Version 41 oder höher ist erforderlich, um [Kernkomponenten für Ihre Umgebung aktivieren](/help/forms/using/enable-adaptive-forms-core-components.md). Wenn Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die **Adaptive Forms (Kernkomponente)** Vorlage und Arbeitsflächendesign werden Ihrer Umgebung hinzugefügt.

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Sie können auch [Beispielvorlagen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) in Ihre Umgebung. Auf diese Weise können Sie Formulare schnell erstellen.

  >[!NOTE]
  >
  > Wenn Sie über keine Vorlage für **adaptive Formulare (Kernkomponente)** in Ihrer Umgebung verfügen, [aktivieren Sie die Kernkomponenten für adaptive Formulare für Ihre Umgebung](/help/forms/using/enable-adaptive-forms-core-components.md). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die Vorlage für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt.

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Die `Canvas` -Design wird standardmäßig hinzugefügt, wenn Sie Kernkomponenten für Ihre Umgebung aktivieren. Sie können  [Standarddesigns herunterladen und anpassen](create-or-customize-themes-for-adaptive-forms-core-components.md). Für **vorkonfiguriert** Bereitstellungsthemen [Beispieldesigns](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) in Ihre Umgebung. Diese helfen Ihnen dabei, mit der Formatierung Ihrer Formulare zu beginnen und eine Basisstruktur bereitzustellen, mit der Sie ein Design gemäß Ihren Geschäftsanforderungen erstellen oder anpassen können.

* **Berechtigungen**: Fügen Sie Ihre Benutzerinnen und Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der [!DNL forms-users]-Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste formularspezifischer Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

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

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Übermittlungsaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.

1. Klicken Sie auf  **[!UICONTROL Einsendung]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen und eine Sendeaktion zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

1. Auswählen und Konfigurieren eines **[!UICONTROL Übermittlungsaktion]**, basierend auf Ihren Anforderungen. Detaillierte Informationen zu Sendeaktionen finden Sie unter [Sendeaktion für adaptive Formulare](/help/forms/using/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leiten Sie bei der Formularübermittlung die Benutzenden auf eine Seite um oder zeigen Sie eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Zu URL umleiten]** und eine AEM Sites-Seite durchsuchen und auswählen oder die URL einer externen Seite angeben.

   * Um eine benutzerdefinierte Nachricht oder Dankesnachricht zu konfigurieren, wählen Sie für die Option &quot;Senden&quot;die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie eine Nachricht im **[!UICONTROL Nachrichteninhalt]** ankreuzen. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Schema oder Formulardatenmodell für ein adaptives Formular konfigurieren {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie basierend auf der Anforderung Ihr Formular mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](/help/forms/using/adaptive-form-json-schema-form-model.md)
* [Erstellen Sie ein Formulardatenmodell](/help/forms/using/create-form-data-models.md)

### JSON-Schema oder Formulardatenmodell für Ihr Formular konfigurieren

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Datenmodell]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um ein JSON-Schema oder Formulardatenmodell zu konfigurieren.](/help/forms/using/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen:

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!NOTE]
>
> Sie können das JSON-Schema oder das Formulardatenmodell für ein adaptives Formular mithilfe der Eigenschaften des Guide-Containers bearbeiten.

## Konfigurieren eines Vorbefüllungs-Dienstes  {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars automatisch mit vorhandenen Daten auszufüllen. Wenn eine Benutzerin oder ein Benutzer ein Formular öffnet, sind die Werte für diese Felder schon vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](/help/forms/using/prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle, um Felder eines adaptiven Formulars im Voraus auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungs-Dienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungs-Dienst im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie für ein adaptives Formular den Vorbefüllungsdienst für Formulardatenmodelle:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptives Formular zu öffnen, um eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-container-prefill-service.png)
1. Wählen Sie ein Formulardatenmodell aus. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Vorbefüllungsdienst für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es die Vorbefüllung für Formulardatenmodelle verwendet. Sie können nun den [Regeleditor](rule-editor.md) verwenden, um Regeln zu erstellen, nach denen Felder des Formulars vorausgefüllt werden.

<!--
## Edit Form Model properties of an Adaptive Form {#edit-form-model}

1. Select the Adaptive Form and tap ![Page information](/help/forms/using/assets/configure-icon.svg) > **[!UICONTROL Open Properties]**. The Form Properties page opens. 

1. Go to the **[!UICONTROL Form Model]** tab and choose a form model. If the Adaptive Form is without a form model, you have the freedom to choose either a JSON schema or a form data model. On the other hand, if the Adaptive Form is already based on a form model, you have the option to switch to another form model of the same type. For instance, if the form is using a JSON schema, you can easily switch to another JSON schema, and similarly if the form is using a Form Data Model, you can switch to another Form Data Model. 

1. Tap **[!UICONTROL Save]** to save the properties.
-->

## Wie geht es weiter

* [Verwenden Sie den Regeleditor, um dem Formular dynamisches Verhalten hinzuzufügen](rule-editor.md)
* [Erstellen oder Anpassen von Designs für auf Kernkomponenten basierende adaptive Forms](create-or-customize-themes-for-adaptive-forms-core-components.md)


## Siehe auch

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](create-an-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Vorlagen für Musterdesigns und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
