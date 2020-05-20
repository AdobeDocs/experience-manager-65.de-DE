---
title: Verwalten Sie Metadaten vieler Assets und Sammlungen in Adobe Enterprise Manager.
description: Bearbeiten Sie die Metadaten vieler Assets und Sammlungen gleichzeitig, um häufig vorkommende Metadatenänderungen schnell zu übertragen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 62%

---


# Verwalten von Assets und Sammlungen {#managing-multiple-assets-and-collections}

Mit Adobe Enterprise Manager Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, um häufig vorkommende Änderungen an Metadaten schnell und stapelweise an Assets weitergeben zu können. Sie können die Metadaten für mehrere Sammlungen zusammen bearbeiten.

Verwenden Sie die Seite „Eigenschaften“, um Metadatenänderungen für mehrere Assets oder Sammlungen durchzuführen:

* Metadateneigenschaften in einen gemeinsamen Wert ändern
* Tags hinzufügen oder ändern

Verwenden Sie den Schema-Editor, um die Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen, anzupassen.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](search-assets.md#metadataupdates).

## Edit metadata properties of multiple assets {#editing-metadata-properties-of-multiple-assets}

1. Navigieren Sie auf der Assets-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. From the toolbar, click the **[!UICONTROL Properties]** icon to open the properties page for the selected assets.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Anders ausgedrückt, zeigt die Seite &quot;Eigenschaften&quot;nur Metadatenfelder an, die auf den Eigenschaftsseiten aller einzelnen Assets häufig vorkommen.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um den Metadateneditor für ein bestimmtes Asset anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Eigenschaftenseite können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl aufheben. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Asset-Liste das Kontrollkästchen neben **[!UICONTROL Titel]**, um zwischen der Auswahl von Assets und dem Deaktivieren der Liste umzuschalten.


1. To select a different metadata schema for the assets, click the **[!UICONTROL Settings]** icon from the toolbar, and select the desired schema.
1. Speichern Sie die Änderungen.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Klicken Sie auf **[!UICONTROL Übermitteln]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configlimit}

Um eine DOS-ähnliche Situation zu vermeiden, beschränkt Enterprise Manager die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. Enterprise Manager erzeugt die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.

>[!MORELIKETHIS]
>
>* [Bearbeiten von Metadateneigenschaften von mehreren Sammlungen](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

