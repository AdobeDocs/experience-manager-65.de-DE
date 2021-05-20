---
title: Verwenden Sie den Layout-Modus, um die Größe von Komponenten für adaptive Formulare zu ändern
description: 'Definieren Sie die Position der Komponenten mithilfe des im Layout -Modus verfügbaren responsiven Rasters. '
feature: Adaptive Formulare
exl-id: 5cf76cb1-c92c-4aed-9945-37494fef2d29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 2%

---

# Verwenden Sie den Layout-Modus, um die Größe von Komponenten {#use-layout-mode-to-resize-components} zu ändern.

Mit der Authoring-Oberfläche für adaptive Formulare können Sie die Größe von Komponenten mithilfe des Layout-Modus ändern. Ziehen Sie blaue Punkte in die Spalten, um die Start- und Endpunkte zum Positionieren von Komponenten zu definieren. Die blauen Punkte werden angezeigt, nachdem auf die Komponente im responsiven Raster getippt wurde. Das responsive Raster besteht aus 12 gleichen Spalten. Die weiße und blaue Farbschattierung in alternativen Spalten unterscheidet eine Spalte von der anderen.

Sie können den Layout -Modus verwenden, um die Größe von Komponenten für alle Gerätetypen wie Desktop, Tablet, Telefon und andere kleinere Geräte zu ändern. Das Tablet leitet die Layoutkonfiguration automatisch von der Desktop-Version ab und die kleineren Geräte leiten die Layoutkonfiguration vom Telefon ab. Sie können jedoch die automatisch abgeleiteten Konfigurationen überschreiben, um für jeden Gerätetyp eine andere Konfiguration zu definieren.

## Zugriff auf Layout-Modus {#access-layout-mode}

Wählen Sie **Layout** aus der Dropdown-Liste, die oben in der Authoring-Benutzeroberfläche für adaptive Formulare neben der Option **Vorschau** angezeigt wird. Das Formular wird im Layout -Modus angezeigt.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
1. Erstellen Sie ein neues oder öffnen Sie ein vorhandenes [adaptives Formular](../../forms/using/creating-adaptive-form.md).
1. Wählen Sie **Layout** aus der Dropdownliste, die oben neben der Option **Vorschau** angezeigt wird. Das Formular wird im Layout -Modus angezeigt.

   ![Layout-Modus](assets/layout_mode_ic_new.png)

## Größe von Komponenten anpassen {#resize-components}

1. Tippen Sie im Layout -Modus auf die Komponente, um die Größe zu ändern. Die blauen Punkte werden am Anfang und Ende des responsiven Rasters angezeigt.
1. Ziehen Sie die blauen Punkte per Drag-and-Drop in das responsive Raster, um die Position der Komponente zu definieren.

   ![Größenanpassung mithilfe des Layout-Modus](assets/layout_mode_resize_new_updated1.png)

   Die Symbolleiste, die nach dem Tippen auf Komponenten angezeigt wird, besteht aus den folgenden Optionen:

   * **[!UICONTROL Übergeordnet]**: Wählen Sie das übergeordnete Element einer Komponente aus.
   * **[!UICONTROL Breakpoint-Layout zurücksetzen]**: Machen Sie alle Größenänderungen rückgängig und wenden Sie das Standardlayout auf die Komponente an.
   * **[!UICONTROL In neue Zeile]** verschieben: Schalten Sie die Komponente in die nächste Zeile um, wenn sich mehrere Komponenten in derselben Zeile befinden.

   Sie können auch die Option **[!UICONTROL Breakpoint-Layout]** zurücksetzen ( ![Breakpoint](assets/reverttopreviouslypublishedversion.png) zurücksetzen) auf Bereichsebene verwenden, um alle Größenänderungen rückgängig zu machen.

   >[!NOTE]
   >
   >Sie können die Größe von Tabellenspalten, Symbolleiste, Symbolleisten-Schaltfläche und Zielbereichskomponenten nicht im Layout -Modus ändern. Verwenden Sie den Stilmodus, um die Größe dieser Komponenten zu ändern.

### Beispiel {#example}

**Zielsetzung:** Sie möchten eine Tabellenkomponente und eine Bildkomponente einfügen und sie in einem adaptiven Formular parallel zueinander positionieren.

1. Fügen Sie die Tabellen- und Bildkomponenten im Bearbeitungsmodus in das adaptive Formular ein. Die Bildkomponente wird nach der Tabellenkomponente angezeigt.
1. Wechseln Sie in den Layout -Modus und tippen Sie auf die Komponente Tabelle . Die blauen Punkte zur Größenanpassung der Komponente werden in den Spalten 1 und 12 angezeigt.
1. Ziehen Sie den blauen Punkt in Spalte 12 in Spalte 6 des responsiven Rasters.

   ![Endpunkt der Tabelle definieren](assets/layout_mode_end_point_table_new.png)

1. Wählen Sie auf ähnliche Weise die Bildkomponente aus und ziehen Sie den blauen Punkt in Spalte 1 in Spalte 7 des responsiven Rasters. Die Tabellen- und Bildkomponenten werden parallel zueinander angezeigt.

   ![Tabelle und Bild im Layout-Modus parallel](assets/table_image_parallel_new.png)

   Sie können die Bildkomponente auswählen und auf die Option **In neue Zeile verschieben** tippen, die in der Symbolleiste verfügbar ist, um die Bildkomponente in die nächste Zeile zu verschieben.

## Größe von Bereichen ändern {#resize-panels-layout-mode}

Führen Sie die folgenden Schritte aus, wenn Sie die Größe des gesamten Bedienfelds anstelle einzelner Komponenten ändern möchten:

1. Tippen Sie auf eine der Komponenten im Bedienfeld, deren Größe Sie ändern möchten, wählen Sie ![Übergeordnetes Element auswählen](assets/select_parent_icon.svg) und wählen Sie die erste Option in der Dropdown-Liste aus, wenn das Bedienfeld das unmittelbare übergeordnete Element der Komponente ist.

   Die blauen Punkte werden am Anfang und Ende des responsiven Rasters angezeigt.

1. Ziehen Sie die blauen Punkte per Drag-and-Drop in das responsive Raster, um die Position des Bedienfelds zu definieren.
Sie können die Schritte 1 und 2 wiederholen und ![Übergeordnetes Element auswählen](assets/float_to_new_line_icon.svg) auswählen, um das Bedienfeld mit der Größenänderung zur nächsten Zeile zu verschieben.

## Mehrspaltiges Layout für einen Bereich definieren

Führen Sie die folgenden Schritte aus, um die Anzahl der Spalten für einen Bereich zu definieren:

1. Tippen Sie im Modus **[!UICONTROL Bearbeiten]** auf das Bedienfeld, wählen Sie ![Konfigurieren](assets/configure_icon.png) und wählen Sie **[!UICONTROL Responsiv - alles auf der Seite ohne Navigation]** aus der Dropdownliste **[!UICONTROL Bedienfeldlayout]** aus.

1. Tippen Sie auf ![Speichern](assets/save_icon.svg), um die Eigenschaften zu speichern.

1. Tippen Sie im Modus **[!UICONTROL Layout]** auf eine der Komponenten im Bereich, wählen Sie ![Übergeordnetes Element](assets/select_parent_icon.svg) aus und wählen Sie das Bedienfeld aus.

1. Tippen Sie auf ![mehrspaltige](assets/multi-column.svg) und wählen Sie die Anzahl der Spalten aus der Dropdownliste aus. Die Anzahl der Spalten kann zwischen 1 und 12 liegen. Das Bedienfeld wird in ein mehrspaltiges Layout unterteilt.

![Mehrspalten im Layout-Modus](assets/multi-column-layout.png)

## Aktivieren des neuen responsiven Rasters für alte responsive Layouts {#enableresponsivegrid}

Aktivieren Sie das neue responsive Raster für Formulare, die Sie mit AEM Forms 6.4 oder einer niedrigeren Version erstellen, um die Größe von Komponenten zu ändern.

>[!NOTE]
>
>Beim Wechseln zum neuen responsiven Raster werden die Layouteigenschaften verworfen, die bereits für im Formular verwendete Komponenten definiert sind.

Führen Sie die folgenden Schritte aus, um das neue responsive Raster zu aktivieren:

1. Wählen Sie **Layout** aus der Dropdownliste, die oben neben der Option **Vorschau** angezeigt wird. Es wird eine Bestätigung angezeigt, um den Layout -Modus zu aktivieren.
1. Tippen Sie auf **Ja**, um den Modus **Layout** für das Formular zu aktivieren.

### Einbetten eines alten Fragments in ein adaptives Formular mit neuem responsiven Layout {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Mit dem neuen responsiven Layout für adaptive Formulare können Sie ein adaptives Formularfragment mit dem alten responsiven Layout zum Formular hinzufügen. Das neue Layout verwirft jedoch die Layout-Eigenschaften, die bereits für die im Fragment verwendeten Komponenten definiert sind. Sie können in den Layout -Modus wechseln, um die Layouteigenschaften für die im Fragment verwendeten Komponenten zu definieren.

### Einbetten eines Fragments mit einem neuen responsiven Layout in ein altes adaptives Formular {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Wenn Sie ein Fragment mit dem neuen responsiven Layout in ein adaptives Formular mit einem alten responsiven Layout einbetten, fordert Sie das System auf, den Layout-Modus für das Formular zu aktivieren und das Fragment erneut einzubetten.

Um den Layout -Modus zu aktivieren, wählen Sie **Layout** aus der Dropdown-Liste, die oben neben der Option **Vorschau** angezeigt wird, und tippen Sie zur Bestätigung auf **Ja**. Wählen Sie den Modus **Bearbeiten** aus, um das Fragment erneut einzubetten.

## Layout-Modus für Formulare mit altem responsiven Layout deaktivieren {#disable-layout-mode-for-forms-with-old-responsive-layout}

Sie können den Layout -Modus für Formulare mit dem alten responsiven Layout deaktivieren, indem Sie Eigenschaften für die im Formular verwendete Vorlage bearbeiten.

Führen Sie die folgenden Schritte aus, um den Layout -Modus zu deaktivieren:

1. Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Vorlagen]** und öffnen Sie die im Formular verwendete Vorlage im Modus **[!UICONTROL Bearbeiten]** .
1. Wählen Sie den Dokumentcontainer im linken Bereich aus und tippen Sie auf **[!UICONTROL Richtlinie.]**

   ![Layout-Modus deaktivieren](assets/policy_disable_layout_mode.png)

1. Tippen Sie auf die Registerkarte **[!UICONTROL Layout-Einstellungen]** und wählen Sie **[!UICONTROL Layout-Modus deaktivieren]** aus.
1. Tippen Sie auf ![Änderungen speichern](assets/save_icon.png), um die Vorlageneigenschaften zu speichern.
