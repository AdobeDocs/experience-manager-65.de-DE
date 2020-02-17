---
title: Verwalten mehrerer Assets und Sammlungen
description: Erfahren Sie, wie Sie die Metadaten mehrerer Assets und Sammlungen simultan bearbeiten können, um schnell häufige Metadaten-Änderungen zu übertragen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Verwalten von Assets und Sammlungen {#managing-multiple-assets-and-collections}

Mit Adobe Enterprise Manager (AEM) Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Sie können die Metadaten für mehrere Sammlungen zusammen bearbeiten.

Verwenden Sie die Seite „Eigenschaften“, um Metadatenänderungen für mehrere Assets oder Sammlungen durchzuführen:

* Metadateneigenschaften in einen gemeinsamen Wert ändern
* Tags hinzufügen oder ändern

Verwenden Sie den Schemaeditor, um die Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen, anzupassen.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](search-assets.md#metadataupdates).

## Edit metadata properties of multiple assets {#editing-metadata-properties-of-multiple-assets}

1. Navigieren Sie auf der Assets-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Tippen oder klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]**, um die Eigenschaftenseite für die ausgewählten Assets zu öffnen.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Anders ausgedrückt, zeigt die Seite &quot;Eigenschaften&quot;nur Metadatenfelder an, die auf allen Eigenschaftsseiten der einzelnen Assets verwendet werden.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um den Metadateneditor für ein bestimmtes Asset anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Eigenschaftenseite können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl aufheben. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* At the top of assets list, select the check box near **[!UICONTROL Title]** to toggle between selecting the assets and clearing the list.


1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, tippen oder klicken Sie auf das Symbol **[!UICONTROL Einstellungen]** in der Symbolleiste und wählen Sie das gewünschte Schema aus.
1. Speichern Sie die Änderungen.
1. To append the new metadata with the existing metadata in fields that contain multiple values, select **[!UICONTROL Append mode]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den Feldern. Tap/click **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Edit metadata properties of multiple collections {#editing-metadata-properties-of-multiple-collections}

1. Wählen Sie in der Konsole „Sammlungen“ die Sammlungen aus, die Sie bearbeiten möchten.
1. From the toolbar, tap/click **[!UICONTROL Properties]** to open the properties page for the selected collections.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Sammlungen auf den verschiedenen Registerkarten.

   >[!NOTE]
   >
   >Die Metadaten, die Sie für die ausgewählten Sammlungen hinzufügen, überschreiben die vorherigen Metadaten für diese Sammlungen, außer für Tags. Any tags you add in the **[!UICONTROL Tags]** field, are appended to the existing list of tags in the metadata.

1. Heben Sie die Auswahl der anderen Sammlungen in der Sammlungsliste auf, um die Metadateneigenschaften für eine bestimmte Sammlung anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für die bestimmte Sammlung gefüllt.

   >[!NOTE]
   >
   >* Auf der Sammlungseigenschaftenseite können Sie Sammlungen aus der Liste der Sammlungen entfernen, indem Sie die Auswahl aufheben. In der Sammlungsliste sind alle Sammlungen standardmäßig ausgewählt. Die Metadaten für Sammlungen, die Sie entfernen, werden nicht aktualisiert.
   >* At the top of the list, select the check box near **[!UICONTROL Title]** to toggle between selecting the collections and clearing the list.


1. Speichern Sie die Änderungen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configlimit}

Um DOS-ähnliche Situationen zu vermeiden, beschränkt AEM die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. AEM generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, greifen Sie auf die Web-Konsole (**[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**) zu und ändern Sie den Wert für **[!UICONTROL maximale POST-Parameter]** unter **[!UICONTROL Apache Sling Request Parameter Handling]** der OSGi-Konfiguration.
