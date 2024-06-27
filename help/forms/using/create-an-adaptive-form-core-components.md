---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind responsive HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells und eines XML- oder JSON-Schemas.
Keywords: create adaptive form core component, create core component based adaptive form, creare adaptive form
products: SG_EXPERIENCEMANAGER/6.5/FORMS
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms,Core Components
solution: Experience Manager, Experience Manager Forms
exl-id: ee596672-b0b5-42e9-a139-72f90287bf3b
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1794'
ht-degree: 100%

---

# Erstellen von adaptiven Formularen auf Grundlage der Kernkomponenten {#creating-an-adaptive-form-core-components}


<span class="preview"> Adobe empfiehlt die Verwendung von Kernkomponenten, um [adaptive Formulare zu einer AEM Sites-Seite hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) oder [eigenständige adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md). </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

Mit adaptiven Formularen können Sie Formulare erstellen, die ansprechend, reaktionsfähig, dynamisch und anpassungsfähig sind. AEM Forms bietet eine benutzerfreundliche Benutzeroberfläche für Unternehmen zur schnellen Erstellung adaptiver Formulare.  Die Benutzeroberfläche bietet eine schnelle Registerkartennavigation, mit der Sie vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen einfach auswählen können, um ein adaptives Formular zu erstellen.

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Adobe empfiehlt die Nutzung dieser modernen und erweiterbaren Komponenten zur Entwicklung von adaptiven Formularen.

* [Foundation-Komponenten adaptiver Formulare](creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Für die Erstellung neuer Formulare empfiehlt Adobe die Verwendung von [Kernkomponenten für adaptive Formulare](/help/forms/using/create-adaptive-form.md), um ein adaptives Formular zu erstellen.

## Voraussetzungen

Zum Erstellen eines adaptiven Formulars benötigen Sie Folgendes:

* **Aktivieren der Kernkomponenten für adaptive Formulare für Ihre Umgebung**: Der AEM-Projektarchetyp Version 41 oder höher ist erforderlich, um [Kernkomponenten für Ihre Umgebung zu aktivieren](/help/forms/using/enable-adaptive-forms-core-components.md). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, werden die Vorlage und das Canvas-Design für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt.

* **Eine adaptive Formularvorlage**: Eine Vorlage liefert eine Grundstruktur und definiert das Erscheinungsbild (Layouts und Stile) eines adaptiven Formulars. Es enthält vorformatierte Komponenten einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. Es bietet außerdem die Optionen zum Definieren eines Designs und einer Übermittlungsaktion. Das Design definiert den Look-and-Feel und die Übermittlungsaktion definiert die Aktion, die bei der Übermittlung eines adaptiven Formulars ausgeführt werden soll. Sie können auch [Beispielvorlagen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de) in Ihre Umgebung implementieren. Diese helfen Ihnen dabei, Formulare schnell zu erstellen.

  >[!NOTE]
  >
  > Wenn Sie über keine Vorlage für **adaptive Formulare (Kernkomponente)** in Ihrer Umgebung verfügen, [aktivieren Sie die Kernkomponenten für adaptive Formulare für Ihre Umgebung](/help/forms/using/enable-adaptive-forms-core-components.md). Sobald Sie die Kernkomponenten für Ihre Umgebung aktivieren, wird die Vorlage für **adaptive Formulare (Kernkomponente)** zu Ihrer Umgebung hinzugefügt.

* **Ein adaptives Formular**: Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider.  Das `Canvas`-Design wird standardmäßig hinzugefügt, wenn Sie Kernkomponenten für Ihre Umgebung aktivieren. Sie können [die Standard-Designs herunterladen und anpassen](create-or-customize-themes-for-adaptive-forms-core-components.md). Sie können [Beispiel-Designs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de) für **vorkonfigurierte** Designs in Ihrer Umgebung implementieren. Diese helfen Ihnen dabei, mit der Formatierung Ihrer Formulare zu beginnen und eine Basisstruktur bereitzustellen, mit der Sie ein Design gemäß Ihren Geschäftsanforderungen erstellen oder anpassen können.

* **Berechtigungen**: Fügen Sie Ihre Benutzerinnen und Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der [!DNL forms-users]-Gruppe sind berechtigt, ein adaptives Formular zu erstellen. Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form}

1. Melden Sie sich bei Ihrer lokalen [AEM-Autoreninstanz](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de#author-and-publish-installs) an.

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Wenn Sie sich angemeldet haben, wählen Sie in der oberen linken Ecke **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

1. Wählen Sie **[!UICONTROL Erstellen]**  > **[!UICONTROL Adaptives Formular erstellen]** aus.

1. Wählen Sie eine Vorlage mit Kernkomponenten für adaptive Formulare aus und klicken Sie auf **[!UICONTROL Weiter]**.

1. Es wird **[!UICONTROL Eigenschaften hinzufügen]** angezeigt. Geben Sie die Werte für die folgenden Eigenschaftenfelder an. Die Felder „Titel“ und „Name“ sind obligatorisch.

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden.
   * **[!UICONTROL Beschreibung:]** Gibt detaillierte Informationen zum Formular an.
   * **[!UICONTROL Design-Client-Bibliothek]:** Gibt das Design für ein adaptives Formular an. Standardmäßig wird das Design `adaptiveform.theme.canvas3` ausgewählt. Sie können auch ein anderes Design im Dropdown-Menü **[!UICONTROL Design-Client-Bibliothek]** auswählen.
   * **[!UICONTROL Konfigurations-Container:]** Definiert einen Speicherort, an dem Konfigurationsdateien für adaptive Formulare gespeichert werden. Diese Konfigurationsdateien enthalten Einstellungen und Eigenschaften, die sich auf das Verhalten und das Erscheinungsbild von adaptiven Formularen beziehen.
   * **[!UICONTROL Tags:]** Gibt Tags an, die eine eindeutige Identifizierung des adaptiven Formulars ermöglichen. Tags erleichtern die Suche nach dem Formular. Um die Tags zu erstellen, geben Sie neue Tag-Namen in das Feld **[!UICONTROL Tags]** ein.
1. Wählen Sie **[!UICONTROL Erstellen]**. Es wird ein adaptives Formular erstellt und ein Dialogfeld zum Öffnen der Formularbearbeitung angezeigt. 


1. Wählen Sie **[!UICONTROL Bearbeiten]** aus, um das neu erstellte Formular auf einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet und zeigt den Inhalt an, der in der Vorlage verfügbar ist. Außerdem wird die Seitenleiste angezeigt, um das neu erstellte Formular anzupassen.


## Verwenden der Kernkomponenten für adaptive Formulare zum Erstellen Ihres Formulars

Nachdem Sie das Formular zur Bearbeitung geöffnet haben, können Sie verfügbare Kernkomponenten für adaptive Formulare verwenden, um Ihrem Formular Formularfelder hinzuzufügen. Sie können Drag-and-Drop oder die Option + [Komponente einfügen] verwenden, um diese Komponenten einem Formular hinzuzufügen. In der Dokumentation zu AEM-Kernkomponenten finden Sie weitere Informationen zu den [Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de#components). Sie können auch [https://aemcomponents.dev/](https://aemcomponents.dev/) besuchen, um die verfügbaren Kernkomponenten in Aktion zu sehen.

## Konfigurieren der Übermittlungsaktion für ein adaptives Formular {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Übermittlungsaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und eine Übermittlungsaktion zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

1. Wählen Sie je nach Ihren Anforderungen eine **[!UICONTROL Übermittlungsaktion]** aus und konfigurieren Sie sie. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/using/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leiten Sie bei der Formularübermittlung die Benutzerin oder den Benutzer auf eine Seite um oder zeigen Sie eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und eine Umleitungsseite oder Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-submit-message.png)

   * Wählen Sie zum Konfigurieren einer Umleitungs-URL für die Senden-Option die Option **[!UICONTROL Zu URL umleiten]** aus, durchsuchen Sie eine AEM Sites-Seite und wählen Sie sie aus oder geben Sie die URL einer externen Seite an.

   * Wählen Sie zum Konfigurieren einer benutzerdefinierten Nachricht oder einer Dankesnachricht für die Senden-Option die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie im Feld **[!UICONTROL Nachrichteninhalt]** eine Nachricht ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Konfigurieren eines Schemas oder Formulardatenmodells für ein adaptives Formular {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie Ihr Formular je nach Anforderung mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](/help/forms/using/adaptive-form-json-schema-form-model.md)
* [Erstellen eines Formulardatenmodells](/help/forms/using/create-form-data-models.md)

### Konfigurieren eines JSON-Schemas oder Formulardatenmodells für das Formular:

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Datenmodell]**.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und ein JSON-Schema oder Formulardatenmodell zu konfigurieren.](/help/forms/using/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen:

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!NOTE]
>
> Sie können das JSON-Schema oder das Formulardatenmodell für ein adaptives Formular mithilfe der Eigenschaften des Guide-Containers bearbeiten.

## Konfigurieren eines Vorbefüllungsdienstes  {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars automatisch mit vorhandenen Daten auszufüllen. Wenn eine Benutzerin oder ein Benutzer ein Formular öffnet, sind die Werte für diese Felder schon vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](/help/forms/using/prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle zum Ausfüllen von Feldern eines adaptiven Formulars im Voraus {#fdm-prefill-service}

Sie können den Vorbefüllungsdienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungsdienst im Voraus auszufüllen.  Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie für ein adaptives Formular den Vorbefüllungsdienst für Formulardatenmodelle:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und eine Umleitungsseite oder eine Dankesnachricht zu konfigurieren.](/help/forms/using/assets/adaptive-forms-container-prefill-service.png)
1. Wählen Sie ein Formulardatenmodell aus. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Vorbefüllungsdienst für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es die Vorbefüllung für Formulardatenmodelle verwendet. Sie können nun den [Regeleditor](rule-editor.md) verwenden, um Regeln zu erstellen, nach denen Felder des Formulars vorausgefüllt werden.

## Wie erfolgt das Umbenennen eines adaptiven AEM-Formulars?{#rename-an-AEM-Adaptive-Form}

Führen Sie zum Umbenennen eines adaptiven Formulars die folgenden Schritte aus:

1. Wählen Sie ein adaptives Formular in Ihrer AEM Forms-Benutzeroberfläche aus.
1. Klicken Sie auf **Eigenschaften** in der oberen Leiste.

   ![Eigenschaften](/help/forms/using/assets/rename-form-properties.png)

1. Ändern Sie den Formularnamen auf der Registerkarte **Titel**, wie in der Abbildung unten dargestellt.
1. Klicken Sie auf **Speichern und schließen**.

   ![Umbenennen eines adaptiven AEM-Formulars](/help/forms/using/assets/rename-form-title.png)


<!--
## Edit Form Model properties of an Adaptive Form {#edit-form-model}

1. Select the Adaptive Form and select ![Page information](/help/forms/using/assets/configure-icon.svg) > **[!UICONTROL Open Properties]**. The Form Properties page opens. 

1. Go to the **[!UICONTROL Form Model]** tab and choose a form model. If the Adaptive Form is without a form model, you have the freedom to choose either a JSON schema or a form data model. On the other hand, if the Adaptive Form is already based on a form model, you have the option to switch to another form model of the same type. For instance, if the form is using a JSON schema, you can easily switch to another JSON schema, and similarly if the form is using a Form Data Model, you can switch to another Form Data Model. 

1. Select **[!UICONTROL Save]** to save the properties.
-->

## Wie geht es weiter

* [Verwenden Sie den Regeleditor, um dem Formular dynamisches Verhalten hinzuzufügen](rule-editor.md)
* [Erstellen oder Anpassen von Designs für auf Kernkomponenten basierende adaptive Formulare](create-or-customize-themes-for-adaptive-forms-core-components.md)


## Siehe auch

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](create-an-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Beispielthemenvorlagen und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de)
