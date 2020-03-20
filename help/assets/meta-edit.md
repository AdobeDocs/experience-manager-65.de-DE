---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in AEM Assets und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 91818198032de0580fe04d09fdd567dc470c021d

---


# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Element, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder neue Metadateneigenschaften vorhandenen Feldern hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Firmen gesteuerte und zuverlässige Metadaten-Vokabeln benötigen, ist das AEM Assets-Hinzufügen neuer Metadateneigenschaften nicht möglich. Autoren können keine neuen Metadatenfelder für Assets hinzufügen, Entwickler hingegen schon. See [Create new metadata property for assets](meta-edit.md#editing-metadata-schema).

## Edit metadata for an asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * From the Assets UI, select the asset and click/tap the **[!UICONTROL View Properties]** icon from the toolbar.
   * From the asset thumbnail, select the **[!UICONTROL View Properties]** quick action.
   * From the asset page, click/tap the **[!UICONTROL View Properties]** icon from the toolbar.
      ![chlimage_1-168](assets/chlimage_1-168.png)
      *Abbildung: Eigenschaftensymbol*
   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Diese Metadaten wurden beim Hochladen (Erfassen) in AEM Assets automatisch extrahiert.

   ![Asset-Eigenschaften für Ansicht-Metadaten auswählen](assets/asset-metadata.png)


   *Abbildung: Bearbeiten oder Hinzufügen von Metadaten auf der Seite &quot;Asset-Eigenschaften&quot;*

1. Nehmen Sie die gewünschten Änderungen an den Metadaten unter den verschiedenen Registerkarten vor und tippen/klicken Sie nach Abschluss der Bearbeitung in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Tippen/Klicken Sie auf **[!UICONTROL Schließen]**, um zur Assets-Weboberfläche zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen. 

Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies erfolgt über den AEM-Metadaten-Schreib-Workflow. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

XMP write-back is supported and enabled for the platforms and file formats described in [technical requirements.](/help/sites-deploying/technical-requirements.md)

## Edit metadata schema {#editing-metadata-schema}

For details on how to edit metadata schema, see [Edit metadata schema forms](metadata-schemas.md#edit-metadata-schema-forms).

## Register a custom namespace within AEM {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in AEM hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Go to the node type administration page `https:[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Click or tap **[!UICONTROL Namespaces]** at the top of the page. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt. 

1. To add a namespace, click or tap **[!UICONTROL New]** at the bottom.
1. Specify a custom namespace in the XML namespace convention (Specify the id in the form of a URI and an associated prefix for the id), and click or tap **[!UICONTROL Save]**.
