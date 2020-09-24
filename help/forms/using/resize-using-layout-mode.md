---
title: Verwenden des Layoutmodus zum Ändern der Größe von Komponenten
seo-title: Verwenden des Layoutmodus zum Ändern der Größe von Komponenten
description: 'Definieren der Position von Komponenten mithilfe des im Layoutmodus verfügbaren interaktiven Rasters '
seo-description: 'Definieren der Position von Komponenten mithilfe des im Layoutmodus verfügbaren interaktiven Rasters '
uuid: 6b077ebe-caea-4ae3-b17a-be2dca94eeb3
contentOwner: anujkapo
topic-tags: interactive-communications, author
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9e9aaf36-bb86-4954-83cc-fa6b3e80ae4b
docset: aem65
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 2%

---


# Verwenden des Layoutmodus zum Ändern der Größe von Komponenten{#use-layout-mode-to-resize-components}

Die Authoring-Benutzeroberfläche für adaptive Formulare und interaktive Kommunikation im Web Kanal ermöglicht es Ihnen, die Größe von Komponenten mithilfe des Layoutmodus zu ändern. Ziehen Sie blaue Punkte in Spalten, um den Beginn und den Endpunkt für die Positionierung der Komponenten zu definieren. Die blauen Punkte werden angezeigt, nachdem auf die Komponente im interaktiven Raster getippt wurde. Das reaktionsfähige Raster besteht aus 12 gleichen Spalten. Die weiße und blaue Farbschattierung in alternativen Spalten unterscheidet eine Spalte von der anderen.

Sie können den Layoutmodus verwenden, um die Größe von Komponenten für alle Gerätetypen wie Desktop, Tablet, Smartphone und andere kleinere Geräte zu ändern. Das Tablet leitet die Layoutkonfiguration automatisch von der Desktop-Version ab und die kleineren Geräte leiten die Layoutkonfiguration vom Smartphone ab. Sie können die automatisch abgeleiteten Konfigurationen jedoch überschreiben, um für jeden Gerätetyp eine andere Konfiguration zu definieren.

Wenn Sie den Web-Kanal mit [Print Kanal für eine interaktive Kommunikation Übergeordnet](../../forms/using/create-interactive-communication.md) erstellen, umfassen die für die Größenanpassung verfügbaren Komponenten auch die Teilformulare und Felder, die in Web Kanal mithilfe von Print Kanal automatisch generiert werden. Der Web-Kanal behält das Layout für die Kanal &quot;Drucken&quot;im Layoutmodus bei.

## Layout-Modus aufrufen {#access-layout-mode}

Wählen Sie **Layout** aus der Dropdown-Liste, die oben auf der Authoring-Oberfläche für adaptive Formulare und interaktive Kommunikation neben der Option &quot; **Vorschau** &quot;angezeigt wird. Das Formular wird im Layoutmodus angezeigt.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
1. [Erstellen Sie ein neues](../../forms/using/create-interactive-communication.md) oder öffnen Sie ein vorhandenes adaptives Formular oder eine interaktive Kommunikation.
1. Wählen Sie **Layout** aus der Dropdown-Liste, die oben neben der Option &quot; **Vorschau** &quot;angezeigt wird. Das Formular wird im Layoutmodus angezeigt.

   ![Layout-Modus für interaktive Kommunikation](assets/layout_mode_ic_new.png)

## Größe von Komponenten anpassen {#resize-components}

1. Tippen Sie im Layoutmodus auf die zu ändernde Komponente. Die blauen Punkte werden am Beginn und am Ende des reaktionsfähigen Rasters angezeigt.
1. Ziehen Sie die blauen Punkte per Drag &amp; Drop, um die Position der Komponente im interaktiven Raster zu definieren.

   ![Größe mithilfe des Layoutmodus ändern](assets/layout_mode_resize_new_updated.png)

   Die Symbolleiste, die nach dem Tippen auf Komponenten angezeigt wird, besteht aus den folgenden Optionen:

   * **Übergeordnet:** Wählen Sie das übergeordnete Element einer Komponente aus.
   * **In neue Zeile schwenken:** Versetzen Sie die Komponente in die nächste Zeile, wenn sich mehrere Komponenten in derselben Zeile befinden.

   Mit der Option &quot;Haltepunkt **[!UICONTROL zurücksetzen&quot;können Sie alle Änderungen an der Größe rückgängig machen und Standardlayout auf das Bedienfeld anwenden, das die Größe der Komponenten enthält, indem Sie die Option &quot;Haltepunkt]** zurücksetzen&quot; ![(&quot;Haltepunkt](assets/reverttopreviouslypublishedversion.png)zurücksetzen&quot;) verwenden. Tippen Sie auf das übergeordnete Element der Größenanpassung, um die Option Ansicht.

   >[!NOTE]
   >
   >Die Größe von Tabellenspalten, Symbolleisten-, Symbolleisten- und Zielgruppen-Bereichskomponenten kann im Layoutmodus nicht geändert werden. Verwenden Sie den Stilmodus, um die Größe dieser Komponenten zu ändern.

### Beispiel {#example}

**Zielsetzung:** Sie möchten eine Tabellenkomponente und eine Bildkomponente einfügen und sie in einer interaktiven Kommunikation parallel zueinander positionieren.

1. Fügen Sie die Tabellen- und Bildkomponenten im Bearbeitungsmodus im Web-Kanal ein. Die Image-Komponente wird nach der Tabellenkomponente angezeigt.
1. Wechseln Sie zum Layoutmodus und tippen Sie auf die Komponente &quot;Tabelle&quot;. Die blauen Punkte zur Größenanpassung der Komponente werden in den Spalten 1 und 12 angezeigt.
1. Ziehen Sie den blauen Punkt in Spalte 12 in Spalte 6 des interaktiven Rasters.

   ![Definieren des Endpunkts der Tabelle](assets/layout_mode_end_point_table_new.png)

1. Wählen Sie auf ähnliche Weise die Image-Komponente aus und ziehen Sie den blauen Punkt in Spalte 1 in Spalte 7 des interaktiven Rasters. Die Tabellen- und Bildkomponenten werden parallel zueinander angezeigt.

   ![Tabelle und Bild parallel im Layoutmodus](assets/table_image_parallel_new.png)

   Sie können die Bildkomponente auswählen und auf die Option &quot; **Auf neue Zeile** verschieben&quot;tippen, die in der Symbolleiste verfügbar ist, um die Bildkomponente zur nächsten Zeile zu verschieben.

## Größe von Bedienfeldern ändern {#resize-panels-layout-mode}

Führen Sie die folgenden Schritte aus, wenn Sie die Größe des gesamten Bedienfelds anstelle einzelner Komponenten ändern möchten:

1. Tippen Sie auf eine der Komponenten im Bedienfeld, deren Größe Sie ändern möchten, wählen Sie &quot;Übergeordnet ![auswählen](assets/select_parent_icon.svg)&quot;und wählen Sie die erste Option in der Dropdown-Liste aus, wenn das Bedienfeld direkt über der Komponente liegt.

   Die blauen Punkte werden am Beginn und am Ende des reaktionsfähigen Rasters angezeigt.

1. Ziehen Sie die blauen Punkte per Drag &amp; Drop, um die Position des Bereichs im interaktiven Raster zu definieren.
Sie können die Schritte 1 und 2 wiederholen und &quot;Übergeordnetes Element ![auswählen](assets/float_to_new_line_icon.svg) &quot;auswählen, um den Bereich mit der Größenanpassung zur nächsten Zeile zu verschieben.

## Definieren des Layouts für mehrere Spalten für ein Bedienfeld

Führen Sie die folgenden Schritte aus, um die Anzahl der Spalten für ein Bedienfeld zu definieren:

1. Tippen Sie im **[!UICONTROL Bearbeitungsmodus]** auf das Bedienfeld, wählen Sie &quot; ![Konfigurieren](assets/configure_icon.png)&quot;und wählen Sie &quot; **[!UICONTROL Interaktiv - alles auf der Seite ohne Navigationsoption]** &quot;aus der Dropdown-Liste &quot; **[!UICONTROL Bedienfeldlayout]** &quot;.

1. Tippen Sie auf ![Speichern](assets/save_icon.svg), um die Eigenschaften zu speichern.

1. Tippen Sie im **[!UICONTROL Layoutmodus]** auf eine der Komponenten im Bedienfeld, wählen Sie &quot;Übergeordnetes Element ![auswählen](assets/select_parent_icon.svg)&quot;und dann den Bereich aus.

1. Tippen Sie auf ![mehrspaltig](assets/multi-column.svg) und wählen Sie die Spaltenanzahl aus der Dropdown-Liste aus. Die Anzahl der Spalten kann zwischen 1 und 12 liegen. Das Bedienfeld wird in ein mehrspaltiges Layout unterteilt.

![mehrere Spalten im Layoutmodus](assets/multi-column-layout.png)

## Aktivieren des neuen interaktiven Rasters für alte reaktionsfähige Layouts {#enableresponsivegrid}

Aktivieren Sie das neue interaktive Raster für Formulare, die Sie mit AEM Forms 6.4 oder einer niedrigeren Version erstellen, um die Größe von Komponenten zu ändern.

>[!NOTE]
>
>Beim Wechsel zum neuen interaktiven Raster werden die Layouteigenschaften verworfen, die bereits für im Formular verwendete Komponenten definiert wurden.

Führen Sie die folgenden Schritte aus, um das neue interaktive Raster zu aktivieren:

1. Wählen Sie **Layout** aus der Dropdown-Liste, die oben neben der Option &quot; **Vorschau** &quot;angezeigt wird. Eine Bestätigung zur Aktivierung des Layoutmodus wird angezeigt.
1. Tippen Sie auf **Ja** , um den **Layoutmodus** für das Formular zu aktivieren.

### Einbetten eines alten Fragments in ein adaptives Formular mit einem neuen reaktionsfähigen Layout {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Mit dem neuen reaktionsfähigen Layout für adaptive Formulare können Sie ein adaptives Formularfragment mit dem alten reaktionsfähigen Layout zum Formular hinzufügen. Das neue Layout verwirft jedoch die Layouteigenschaften, die bereits für im Fragment verwendete Komponenten definiert wurden. Sie können zum Modus &quot;Layout&quot;wechseln, um die Layouteigenschaften für die im Fragment verwendeten Komponenten zu definieren.

### Einbetten eines Fragments mit einem neuen reaktionsfähigen Layout in ein altes adaptives Formular {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Wenn Sie ein Fragment mit dem neuen reaktionsfähigen Layout in ein adaptives Formular mit einem alten reaktionsfähigen Layout einbetten, fordert Sie das System auf, den Layoutmodus für das Formular zu aktivieren und das Fragment erneut einzubetten.

Um den Layoutmodus zu aktivieren, wählen Sie in der Dropdown-Liste, die oben neben der Option &quot; **Vorschau** &quot;angezeigt wird, die Option &quot; **Layout** &quot;aus und tippen Sie zur Bestätigung auf **Ja** . Wählen Sie **Bearbeitungsmodus** , um das Fragment erneut einzubetten.

## Layout-Modus für Formulare mit altem reaktionsfähigem Layout deaktivieren {#disable-layout-mode-for-forms-with-old-responsive-layout}

Sie können den Layoutmodus für Formulare mit einem alten reaktionsfähigen Layout deaktivieren, indem Sie die Eigenschaften der im Formular verwendeten Vorlage bearbeiten.

Führen Sie die folgenden Schritte aus, um den Layoutmodus zu deaktivieren:

1. Wählen Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Vorlagen]** und öffnen Sie die Vorlage, die im Formular im **[!UICONTROL Bearbeitungsmodus]** verwendet wird.
1. Wählen Sie im linken Bereich den Container Dokument aus und tippen Sie auf **[!UICONTROL Richtlinie.]**

   ![Layout deaktivieren, Modus](assets/policy_disable_layout_mode.png)

1. Tippen Sie auf die Registerkarte **[!UICONTROL Layouteinstellungen]** und wählen Sie Layout-Modus **[!UICONTROL deaktivieren]**.
1. Tap ![Save changes](assets/save_icon.png) to save the template properties.

