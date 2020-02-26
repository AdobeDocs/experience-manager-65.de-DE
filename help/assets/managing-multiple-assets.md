---
title: Verwalten mehrerer Assets und Sammlungen
description: Erfahren Sie, wie Sie die Metadaten mehrerer Assets und Sammlungen simultan bearbeiten können, um schnell häufige Metadaten-Änderungen zu übertragen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9af0ee0ff9d1089b6cf09c52f7f606cce6775d72

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
1. Um die neuen Metadaten mit den vorhandenen Metadaten für Felder anzuhängen, die mehrere Werte enthalten, wählen Sie **[!UICONTROL Beifügemodus]** aus. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Tippen/Klicken Sie auf **[!UICONTROL Senden]**.

   >[!CAUTION]
   >
   >Bei Feldern mit nur einem einzigen Wert werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Beifügemodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configlimit}

Um DOS-ähnliche Situationen zu vermeiden, beschränkt AEM die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. AEM generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, greifen Sie auf die Web Console zu (**[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web Console]**) und ändern Sie den Wert der **[!UICONTROL Max. POST-Parameter]** in der OSGi-Konfiguration für das **[!UICONTROL Parameter-Handling von Apache Sling-Anfragen]**.

>[!MORELIKETHIS]
>
>* [Metadateneigenschaften mehrerer Sammlungen bearbeiten](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

