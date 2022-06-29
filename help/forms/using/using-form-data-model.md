---
title: Verwenden eines Formulardatenmodells
seo-title: Use form data model
description: Erfahren Sie, wie Sie mit dem Formulardatenmodell adaptive Formulare und interaktive Kommunikation erstellen und damit arbeiten können.
seo-description: Learn how to use form data model to create and work with adaptive forms and interactive communications.
uuid: 9d8d8f43-9a50-4905-a6ef-a5ea3b9c11f7
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
discoiquuid: 87f5f9f5-2d03-4565-830e-eacc3757e542
docset: aem65
feature: Form Data Model
exl-id: 9a73a643-7ad4-49aa-a971-08d52679158d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1252'
ht-degree: 100%

---

# Verwenden eines Formulardatenmodells{#use-form-data-model}

![](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Back-End-Datenquellen verwenden, um ein Formulardatenmodell zu erstellen, das Sie als Schema in verschiedenen adaptiven Formularen und interaktiven Kommunikationsworkflows verwenden können. Dafür ist das Konfigurieren von Datenquellen und Erstellen von Formulardatenmodellen, basierend auf Datenmodellobjekten sowie Diensten, die in den Datenquellen verfügbar sind, erforderlich. Weitere Informationen finden Sie in den folgenden Themen:

* [Datenintegration für AEM Forms](../../forms/using/data-integration.md)
* [Konfigurieren von Datenquellen](../../forms/using/configure-data-sources.md)
* [Erstellen des Formulardatenmodells](../../forms/using/create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](../../forms/using/work-with-form-data-model.md)

Ein Formulardatenmodell ist eine Erweiterung des JSON-Schemas, die Sie wie folgt verwenden können:

* [Adaptive Formulare und Fragmente erstellen](#create-af)
* [Interaktive Kommunikation und Bausteine wie Text, Liste und Bedingungsfragmente erstellen](#create-ic)
* [Vorschau für interaktive Kommunikation mit Beispieldaten](#preview-ic)
* [Adaptive Formulare und interaktive Kommunikation ausfüllen](#prefill)
* [Gesendete adaptive Formulardaten zurück in Datenquellen schreiben](#write-af)
* [Dienste über Regeln für adaptive Formulare aufrufen](#invoke-services)

## Adaptive Formulare und Fragmente erstellen {#create-af}

Sie können [adaptive Formulare](../../forms/using/creating-adaptive-form.md) und [adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md) anhand des Formulardatenmodells erstellen. Gehen Sie wie folgt vor, um ein Formulardatenmodell beim Erstellen eines adaptiven Formulars oder eines adaptiven Formularfragments zu verwenden:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Auswählen aus]**.

   ![Create-af-1-1](assets/create-af-1-1.png)

1. Tippen Sie auf **[!UICONTROL Formulardatenmodell auswählen]**, um es zu erweitern. Alle verfügbaren Formulardatenmodelle werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![Create-af-2-1](assets/create-af-2-1.png)

1. (**Nur adaptive Formularfragmente**) Sie können ein adaptives Formularfragment nur auf Basis eines einzelnen Datenmodellobjekts in einem Formulardatenmodell erstellen. Erweitern Sie die Dropdownliste **[!UICONTROL Definitionen für Formulardatenmodell]**. Hier sind sämtliche Datenmodellobjekte im angegebenen Formulardatenmodell aufgelistet. Wählen Sie ein Datenmodellobjekt aus der Liste aus.

   ![create-af-3](assets/create-af-3.png)

Sobald das auf einem Formulardatenmodell basierende adaptive Formular oder Formularfragment erstellt ist, werden Formulardatenobjekte auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des Inhaltsbrowsers im Editor für adaptive Formulare angezeigt.

>[!NOTE]
>
>Für adaptive Formularfragmente werden nur das beim Verfassen gewählte Datenmodellobjekt und die mit diesem verknüpften Datenmodellobjekte auf der Registerkarte „Datenmodellobjekte“ angezeigt.

![data-model-object-tab](assets/data-model-objects-tab.png)

Indem Sie Datenmodellobjekte in das adaptive Formular oder Fragment ziehen und dort ablegen, können Sie Formularfelder hinzufügen. Für die hinzugefügten Formularfelder bleiben die Metadateneigenschaften und die Bindung der Datenmodellobjekteigenschaften erhalten. Die Bindung stellt sicher, dass die Feldwerte in den entsprechenden Datenquellen bei der Formularübermittlung aktualisiert und bei der Ausgabe des Formulars vorausgefüllt werden.

## Interaktive Kommunikation erstellen {#create-ic}

Sie können eine interaktive Kommunikation basierend auf einem Formulardatenmodell erstellen, mit dem Sie die interaktive Kommunikation mit Daten aus konfigurierten Datenquellen vorab füllen können. Darüber hinaus können die Bausteine &#x200B;&#x200B;einer interaktiven Kommunikation, wie etwa Text-, Listen- und Bedingungsdokumentfragmente, auf einem Formulardatenmodell basieren.

Sie können ein Formulardatenmodell beim Erstellen einer interaktiven Kommunikation oder eines Dokumentfragments auswählen. Das folgende Bild zeigt die Registerkarte „Allgemein“ des Dialogfelds „Interaktive Kommunikation erstellen“.

![create-ic](assets/create-ic.png)

Registerkarte „Allgemein“ des Dialogfelds „Interaktive Kommunikation erstellen“

Weitere Informationen finden Sie unter:

[Interaktive Kommunikation erstellen](../../forms/using/create-interactive-communication.md)

[Text in interaktiven Kommunikationen](/help/forms/using/texts-interactive-communications.md)

[Bedingungen in interaktiven Kommunikationen](/help/forms/using/conditions-interactive-communications.md)

[Fragmente aufführen](/help/forms/using/lists.md)

## Vorschau mit Beispieldaten {#preview-ic}

Mit dem Formulardatenmodelleditor können Sie Beispieldaten für Datenmodellobjekte im Formulardatenmodell generieren und bearbeiten. Sie können diese Daten verwenden, um interaktive Kommunikation und adaptive Formulare in der Vorschau anzuzeigen und zu testen. Sie müssen die Beispieldaten vor der Vorschau generieren, wie beschrieben unter [Arbeiten mit einem Formulardatenmodell](../../forms/using/work-with-form-data-model.md#sample).

So zeigen Sie eine interaktive Kommunikation mit Stichprobendatenmodelldaten an:

1. Navigieren Sie auf dem AEM-Server zu **[!UICONTROL Formulare > Formulare und Dokumente]**.
1. Wählen Sie eine interaktive Kommunikation und tippen Sie auf **[!UICONTROL Vorschau]** in der Symbolleiste, um **[!UICONTROL Webkanal]**, **[!UICONTROL Druckkanal]** oder **[!UICONTROL Beide Kanäle]** auszuwählen und eine Vorschau der interaktiven Kommunikation anzuzeigen.
1. Stellen Sie im Vorschau-Dialogfeld [*Kanal*] sicher, dass **[!UICONTROL Testdaten des Formulardatenmodells]** ausgewählt ist, und tippen Sie auf **[!UICONTROL Vorschau]**.

Die interaktive Kommunikation öffnet sich mit vorbefüllten Beispieldaten.

![web-preview](assets/web-preview.png)

Um ein adaptives Formular mit Beispieldaten in der Vorschau anzuzeigen, öffnen Sie das adaptive Formular im Autorenmodus und tippen Sie auf **[!UICONTROL Vorschau]**.

## Vorbefüllen mit dem Formulardatenmodelldienst {#prefill}

AEM Forms bietet einen standardmäßigen Vorbefüllungs-Dienst für Formulardatenmodelle, den Sie für adaptive Formulare und interaktive Kommunikation auf Basis eines Formulardatenmodells aktivieren können. Der Vorbefüllungs-Dienst fragt Datenquellen nach Datenmodellobjekte im adaptiven Formular und in der interaktiven Kommunikation ab und befüllt dementsprechend Daten, während das Formular oder die Kommunikation gerendert wird.

Um den Vorbefüllungs-Dienst für ein adaptives Formular zu aktivieren, öffnen Sie die Eigenschaften des Containers für ein adaptives Formular und wählen Sie **[!UICONTROL Vorbefüllungs-Dienst für Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Vorbefüllungs-Dienst]** im Accordion „Standard“. Speichern Sie anschließend die Eigenschaften.

![prefill-service](assets/prefill-service.png)

Um den Vorbefüllungs-Dienst für Formulardatenmodelle in einer interaktiven Kommunikation zu konfigurieren, können Sie im Dropdown-Liste für den Vorbefüllungs-Dienst den Vorbefüllungs-Dienst für Formulardatenmodelle während der Erstellung auswählen, oder später, indem Sie die Eigenschaften ändern.

![edit-ic-props](assets/edit-ic-props.png)

Dialogfeld „Eigenschaften bearbeiten“ für eine interaktive Kommunikation

## Gesendete adaptive Formulardaten in Datenquellen schreiben {#write-af}

Sie können ein auf einem Formulardatenmodell basierendes Formular so konfigurieren, dass die vom Benutzer im Formular übermittelten Daten für ein Datenmodellobjekt bei der Übermittlung in dessen Datenquellen geschrieben werden. Zu diesem Zweck steht in AEM Forms die [Übermittlungsaktion für Formulardatenmodelle](../../forms/using/configuring-submit-actions.md) zur Verfügung. Standardmäßig ist sie nur für adaptive Formulare verfügbar, die auf einem Formulardatenmodell basieren. Durch diese Aktion werden übermittelte Daten für ein Datenmodellobjekt in dessen Datenquelle geschrieben.

Um die Übermittlungsaktion für Formulardatenmodelle zu konfigurieren, öffnen Sie die Adaptive Form-Container-Eigenschaften und wählen Sie **[!UICONTROL Übermitteln mit dem Formulardatenmodell]** aus dem Dropdown-Menü „Übermittlungsaktion“ unter dem Akkordeon „Übermittlung“. Suchen Sie dann das gewünschte Datenmodellobjekt in der Dropdownliste **[!UICONTROL Name des zu übermittelnden Modellobjekts]** und wählen Sie es aus. Speichern Sie die Eigenschaften.

Bei Übermitteln des Formulars werden die Daten für das konfigurierte Datenmodellobjekt in die entsprechende Datenquelle geschrieben.

![data-submission](assets/data-submission.png)

Mithilfe der Objekteigenschaft „Binärdatenmodell“ können Sie auch Formularanhänge an eine Datenquelle senden. Gehen Sie wie folgt vor, um Anhänge an eine JDBC-Datenquelle zu senden:

1. Fügen Sie dem Formulardatenmodell ein Datenmodellobjekt hinzu, das eine binäre Eigenschaft enthält.
1. Ziehen Sie im adaptiven Formular die Komponente **[!UICONTROL Dateianhang]** aus dem Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Tippen Sie auf die hinzugefügte Komponente, um sie auszuwählen, und tippen Sie dann auf ![settings_icon](assets/settings_icon.png), um den Eigenschaftenbrowser für die Komponente zu öffnen.
1. Tippen Sie im Feld „Bindungsverweis“ auf ![foldersearch_18](assets/foldersearch_18.png), navigieren Sie zur binären Eigenschaft, die Sie im Formulardatenmodell hinzugefügt haben, und wählen Sie sie aus. Konfigurieren Sie weitere Eigenschaften entsprechend.

   Tippen Sie auf ![check-button](assets/check-button.png), um die Eigenschaften zu speichern. Damit ist das Anhangsfeld an die binäre Eigenschaft des Formulardatenmodells gebunden.

1. Aktivieren Sie im Abschnitt „Übermittlung“ der Eigenschaften des Containers für das adaptive Formular die Option **[!UICONTROL Formularanhänge einreichen]**. Dadurch wird der Anhang im Feld der binären Eigenschaft bei der Sendung des Formulars an die Datenquelle gesendet.

## Dienste in adaptiven Formularen mithilfe von Regeln aufrufen {#invoke-services}

In einem auf einem Formulardatenmodell basierenden adaptiven Formular können Sie [Regeln erstellen](../../forms/using/rule-editor.md), um die im Formulardatenmodell konfigurierten Dienste aufzurufen. Für die Operation **[!UICONTROL Dienste aufrufen]** werden alle verfügbaren Dienste im Formulardatenmodell aufgelistet und Sie können die Eingabe- und Ausgabefelder für den Dienst wählen. Sie können außerdem mit dem Regeltyp **Wert festlegen** einen Formulardatenmodelldienst aufrufen und die vom Dienst zurückgegebene Ausgabe als Wert eines Feldes einstellen.

Beispielsweise ruft folgende Regel einen Get-Service auf, für den die Mitarbeiter-ID als Eingabe angegeben werden muss und der die entsprechenden Werte in den Feldern für die Angehörigen-ID, den Nachnamen, den Vornamen und das Geschlecht zurückgibt.

![invoke-service](assets/invoke-service.png)

Darüber hinaus können Sie mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API ein JavaScript im Codeeditor für den Regeleditor schreiben. Informationen zur API finden Sie unter [API zum Aufrufen des Formulardatenmodelldienstes](/help/forms/using/invoke-form-data-model-services.md).
