---
title: Ordnermetadatenschema
description: Erfahren Sie, wie Sie Metadatenschema für Asset-Ordner in AEM Assets erstellen
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
uuid: bf8d066c-0f23-4d18-9ce9-860fa505dea2
discoiquuid: 23009e50-a026-4823-8e4c-7a313a11b38c
docset: aem65
translation-type: tm+mt
source-git-commit: 62cc3282f8d8bc77f072de1d027484bd93efa38a

---


# Folder metadata schema {#folder-metadata-schema}

Mit Adobe Experience Manager (AEM) Assets können Sie Metadatenschemata für Asset-Ordner erstellen, die das Layout und die Metadaten definieren, die auf den Seiten mit Ordnereigenschaften angezeigt werden.

## Hinzufügen von Ordner-Metadatenschema-Formularen {#add-a-folder-metadata-schema-form}

Verwenden Sie den Editor für Metadatenschema-Formulare, um Metadatenschemata für Ordner zu erstellen und zu bearbeiten.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. In the Folder Metadata Schema Forms page, tap/click **[!UICONTROL Create]**.
1. Geben Sie einen Namen für das Formular an und tippen/klicken Sie auf **[!UICONTROL Erstellen]**. Das neue Schemaformular wird auf der Seite „Schemaformulare“ aufgeführt.

## Bearbeiten von Ordner-Metadatenschema-Formularen {#edit-folder-metadata-schema-forms}

Sie können neu erstellte oder bestehende Metadatenschema-Formulare bearbeiten. Hierzu zählen folgende Elemente:

* Registerkarten
* Formularelemente innerhalb von Registerkarten

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen.

1. In the Schema Forms page, select the form you created, and then tap/click the **[!UICONTROL Edit]** icon from the toolbar.
1. In the Folder Metadata Schema Editor page, tap `+` to add a tab to the form. Um die Registerkarte umzubenennen, tippen/klicken Sie auf den Standardnamen und geben Sie unter **[!UICONTROL Einstellungen]** den neuen Namen an.

   ![custom_tab](assets/custom_tab.png)

   Um weitere Registerkarten hinzuzufügen, tippen Sie auf `+`. Tippen Sie auf `X` eine Registerkarte, um sie zu löschen.

1. In the active tab, add one or more components from the **[!UICONTROL Build Form]** tab.

   ![adding_components](assets/adding_components.png)

   Wenn Sie mehrere Registerkarten erstellen, tippen/klicken Sie auf eine Registerkarte, um Komponenten hinzuzufügen.

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

   Löschen Sie ggf. eine Komponente über die Registerkarte **[!UICONTROL Einstellungen]**.

   ![configure_properties](assets/configure_properties.png)

1. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

### Komponenten zum Erstellen von Formularen {#components-to-build-forms}

The **[!UICONTROL Build Form]** tab lists form items that you use in your folder metadata schema form. The **[!UICONTROL Settings]** tab displays the attributes for each item that you select in the **[!UICONTROL Build Form]** tab. Here is a list the form items available in the **[!UICONTROL Build Form]** tab:

| Komponentenname | Beschreibung |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzelzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdownliste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |

### Bearbeiten von Formularelementen {#editing-form-items}

To edit the properties of form items, tap/click the component and edit all or a subset of the following properties in the **[!UICONTROL Settings]** tab.

**[!UICONTROL Feldbeschriftung]**: Der Name der Metadateneigenschaft, die auf der Eigenschaftenseite für den Ordner angezeigt wird.

**[!UICONTROL Zu Eigenschaft zuordnen]**: Diese Eigenschaft gibt den relativen Pfad des Ordnerknotens im CRX-Repository an, wo das Element gespeichert ist. Sie beginnt mit „**./**“. Dies zeigt an, dass sich der Pfad unter dem Knoten des Ordners befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert auf dem Metadaten-Knoten des Ordners als Eigenschaft `dc:title`.

* `./jcr:created`: Zeigt die Eigenschaft „JCR“ im Knoten des Ordners an. Wenn Sie diese Eigenschaften in CRXDE konfigurieren, empfiehlt Adobe, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls tritt der Fehler &#39; `Asset(s) failed to modify`&#39; auf, wenn Sie die Eigenschaften des Assets speichern.

Um zu gewährleisten, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, fügen Sie dem Eigenschaftenpfad keine Leerzeichen hinzu.

**[!UICONTROL JSON-Pfad]**: Verwenden Sie ihn, um den Pfad der JSON-Datei anzugeben, in der Sie Schlüssel-Wert-Paare für Optionen angeben.

**[!UICONTROL Platzhalter]**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.

**[!UICONTROL Wahlen]**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**[!UICONTROL Beschreibung]**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**[!UICONTROL Klasse]**: Objektklasse, der die Eigenschaft zugeordnet ist.

## Löschen von Ordner-Metadatenschema-Formularen {#delete-folder-metadata-schema-forms}

Sie können Metadaten-Schemaformulare aus Ordnern auf der Seite &quot;Schemaformulare für Metadaten-Ordner&quot;löschen. Um ein Formular zu löschen, wählen Sie es aus und tippen/klicken Sie in der Symbolleiste auf das Löschsymbol.

![delete_form](assets/delete_form.png)

## Zuordnen eines Ordner-Metadatenschemas {#assign-a-folder-metadata-schema}

Sie können einem Ordner entweder auf der Seite &quot;Metadaten-Schemaformulare für Ordner-Metadaten&quot;oder beim Erstellen eines Ordners ein Schema zuweisen.

Wenn Sie ein Metadatenschema für einen Ordner konfigurieren, wird der Pfad in der Eigenschaft `folderMetadataSchema` des Ordnerknotens unter */jcr:content* gespeichert.

### Zuweisen eines Schemas über die Seite „Ordner-Metadatenschema“ {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Wählen Sie auf der Seite &quot;Metadaten-Schemaformulare&quot;das Schemaformular aus, das Sie auf einen Ordner anwenden möchten.
1. From the toolbar, tap/click **[!UICONTROL Apply to Folder(s)]**.

1. Select the folder on which to apply the schema and then click/tap **[!UICONTROL Apply]**. Wenn bereits ein Metadatenschema auf den Ordner angewendet wurde, wird eine Warnung dazu angezeigt, dass das bestehende Schema überschrieben wird. Tap/click **[!UICONTROL Overwrite]**.
1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.

   ![folder_properties](assets/folder_properties.png)

   To view the folder metadata fields, tap/click the **[!UICONTROL Folder Metadata]** tab.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Zuweisen eines Schemas bei der Ordnererstellung {#assign-a-schema-when-creating-a-folder}

Sie können Ordner-Metadatenschemata auch beim Erstellen eines Ordners zuweisen. Wenn bereits mindestens ein Ordner-Metadatenschema im System vorhanden ist, wird eine zusätzliche Liste im Dialogfeld **[!UICONTROL Ordner erstellen]** angezeigt. Sie können das gewünschte Schema auswählen. Standardmäßig ist kein Schema ausgewählt.

1. Tippen/klicken Sie in der Symbolleiste der AEM Assets-Benutzeroberfläche auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel und einen Namen für den Ordner an.
1. Wählen Sie in der Liste „Ordner-Metadatenschema“ das gewünschte Schema aus. Tippen/klicken Sie anschließend auf **[!UICONTROL Erstellen]**.

   ![select_schema](assets/select_schema.png)

1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.
1. To view the folder metadata fields, tap/click the **[!UICONTROL Folder Metadata]** tab.

## Verwenden des Ordner-Metadatenschemas {#use-the-folder-metadata-schema}

Öffnen Sie die Eigenschaften für einen Ordner, der mit einem Ordner-Metadatenschema konfiguriert wurde. A **[!UICONTROL Folder Metadata]** tab is displayed in the folder properties page. Um das Ordner-Metadatenschema-Formular anzuzeigen, wählen Sie diese Registerkarte aus.

Geben Sie Metadatenwerte in die verschiedenen Felder ein und tippen/klicken Sie auf **[!UICONTROL Speichern]**, um die Werte zu speichern. Die angegebenen Werte werden im Ordnerknoten im CRX-Repository gespeichert.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

