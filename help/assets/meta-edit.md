---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Learn about asset metadata in [!DNL Adobe Experience Manager Assets] an various ways by which you can edit asset metadata.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 4748eed3ce484e8446b641ccbc7b5d76cb66f428
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 22%

---


# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten{#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder neue Metadateneigenschaften zu einem vorhandenen Feld hinzufügen, z. B. wenn ein Metadatenfeld leer ist.

Organisationen benötigen kontrollierte und zuverlässige Metadaten-Vokabeln. Daher ist es [!DNL Experience Manager Assets] nicht möglich, bei Bedarf neue Metadateneigenschaften hinzuzufügen. Entwickler und nicht Autoren können neue Metadatenfelder für Assets hinzufügen. Siehe [Erstellen der Metadateneigenschaft für Assets](meta-edit.md#editing-metadata-schema).

## Edit metadata for an asset {#editing-metadata-for-an-asset}

Gehen Sie wie folgt vor, um Metadaten zu bearbeiten:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der [!DNL Assets] Benutzeroberfläche das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Ansichten-Eigenschaften]** .
   * Wählen Sie die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus der Miniaturansicht des Assets aus.
   * Klicken Sie auf der Seite &quot;Asset&quot;in der Symbolleiste auf das Symbol für die **[!UICONTROL Ansicht Eigenschaften]** ![Assets](assets/do-not-localize/info-circle-icon.png) .

   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Die Metadaten werden extrahiert, wenn das Asset hochgeladen (aufgenommen) wird [!DNL Experience Manager].

   ![Eigenschaften eines Assets auswählen, um die Metadaten Ansicht](assets/asset-metadata.png)

   *Abbildung: Bearbeiten oder Hinzufügen von Metadaten auf der Seite[!UICONTROL &quot;Asset-Eigenschaften&quot;].*

1. Make edits to the metadata under the various tabs, as required, and when completed, click **[!UICONTROL Save]** from the toolbar to save your changes. Click **[!UICONTROL Close]** to return to the [!DNL Assets] web interface.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen. 

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Der Metadaten-Schreibback-Arbeitsablauf fügt die Metadaten zur ursprünglichen Binärdatei hinzu. Changes made to the existing properties (such as `dc:title`) are overwritten and new properties (including custom properties like `cq:tags`) are added with the schema.

XMP write-back is supported and enabled for the platforms and file formats described in [technical requirements.](/help/sites-deploying/technical-requirements.md)

## Edit metadata schema {#editing-metadata-schema}

Weitere Informationen finden Sie unter [Bearbeiten von Metadaten-Schema-Formularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerspezifischen Namensraums in [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

You can add your own namespaces within [!DNL Experience Manager]. Just as there are predefined namespaces such as `cq`, `jcr`, and `sling`, you can have a namespace for your repository metadata and XML processing.

1. Greifen Sie auf die Knotentyp-Verwaltungsseite zu `https://[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Klicken Sie auf **[!UICONTROL Namensraum]** oben auf der Seite, um auf die Seite &quot;Namensraum-Administration&quot;zuzugreifen.
1. Klicken Sie zum Hinzufügen eines Namensraums unten auf der Seite auf **[!UICONTROL Neu]** .
1. Geben Sie einen benutzerdefinierten Namensraum in der XML-Namensraum-Konvention an. Geben Sie die ID in Form eines URI und eines zugehörigen Präfix für die ID an. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!MORELIKETHIS]
>
>* [Informationen zu Metadaten und deren Bedarf in Assets](metadata.md)
>* [XMP-Metadaten](xmp.md)
>* [Metadaten-Schemareferenz](meta-ref.md)

