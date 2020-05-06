---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Learn about asset metadata in [!DNL Adobe Experience Manager Assets] an various ways by which you can edit asset metadata.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 99ce6e0572797b7bccf755aede93623be6bd5698
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 42%

---


# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten{#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder vorhandenen Feldern neue Metadateneigenschaften hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Because organizations need controlled and reliable metadata vocabularies, [!DNL Experience Manager Assets] does not allow for ad-hoc adding of new metadata properties. Autoren können keine neuen Metadatenfelder für Assets hinzufügen, Entwickler hingegen schon. See [create new metadata property for assets](meta-edit.md#editing-metadata-schema).

## Edit metadata for an asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der [!DNL Assets] Benutzeroberfläche das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Ansichten-Eigenschaften]** .
   * Wählen Sie die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus der Miniaturansicht des Assets aus.
   * From the asset page, click **[!UICONTROL View Properties]** ![chlimage_1-168](assets/chlimage_1-168.png) from the toolbar.
   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Die Metadaten werden extrahiert, wenn das Asset hochgeladen (aufgenommen) wird [!DNL Experience Manager].

   ![Asset-Eigenschaften für Ansicht-Metadaten auswählen](assets/asset-metadata.png)

   *Abbildung: Bearbeiten oder Hinzufügen von Metadaten auf der Seite[!UICONTROL &quot;Asset-Eigenschaften&quot;].*

1. Make edits to the metadata under the various tabs, as required, and when completed, click **[!UICONTROL Save]** from the toolbar to save your changes. Click **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen. 

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. This is done via [!DNL Experience Manager] metadata write-back workflow. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

XMP write-back is supported and enabled for the platforms and file formats described in [technical requirements.](/help/sites-deploying/technical-requirements.md)

## Edit metadata schema {#editing-metadata-schema}

Weitere Informationen finden Sie unter [Bearbeiten von Metadaten-Schema-Formularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerspezifischen Namensraums in [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

You can add your own namespaces within [!DNL Experience Manager]. Just as there are predefined namespaces such as `cq`, `jcr`, and `sling`, you can have a namespace for your repository metadata and XML processing.

1. Go to the node type administration page `https:[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Click **[!UICONTROL Namespaces]** at the top of the page. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt.

1. To add a namespace, click **[!UICONTROL New]** at the bottom.
1. Geben Sie einen benutzerdefinierten Namensraum in der XML-Namensraum-Konvention an. Geben Sie die ID in Form eines URI und eines zugehörigen Präfix für die ID an. Klicken Sie auf **[!UICONTROL Speichern]**.
