---
title: Verwenden des Layout-Modus zum Ändern der Größe von Komponenten für adaptive Formulare
description: Definieren Sie die Position von Komponenten mithilfe des responsiven Rasters, das im Layout-Modus verfügbar ist
feature: Adaptive Forms, Foundation Components
exl-id: 5cf76cb1-c92c-4aed-9945-37494fef2d29
source-git-commit: d85fc98d9a31bc4014aef4311ba0f838c7ef619a
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 80%

---

# Verwenden des Layout-Modus zum Ändern der Größe von Komponenten {#use-layout-mode-to-resize-components}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/resize-using-layout-mode.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


Mit der Authoring-Oberfläche für adaptive Formulare können Sie mithilfe des Layout-Modus die Größe von Komponenten ändern. Indem Sie blaue Punkte per Drag-und-Drop in Spalten ziehen, können Sie den Start- und Endpunkt zur Positionierung der Komponenten definieren. Die blauen Punkte werden nach dem Tippen auf die Komponente im responsiven Raster angezeigt. Das responsive Raster besteht aus 12 gleichen Spalten. Die weiße und blaue Farbschattierung in alternativen Spalten setzt die Spalten voneinander ab.

Sie können den Layout-Modus verwenden, um die Größe von Komponenten für alle Gerätetypen wie Desktopcomputer, Tablet, Smartphone und andere kleinere Geräte zu ändern. Das Tablet leitet die Layout-Konfiguration automatisch von der Desktopversion ab und die kleineren Geräte leiten die Layout-Konfiguration vom Smartphone ab. Sie können die automatisch abgeleiteten Konfigurationen jedoch überschreiben, um für jeden Gerätetyp eine andere Konfiguration zu definieren.

## Zugriff auf Layout-Modus {#access-layout-mode}

Wählen Sie **Layout** aus der Dropdownliste, die oben in der Authoring-Oberfläche für adaptive Formulare neben der Option **Vorschau** angezeigt wird. Das Formular wird im Layout-Modus angezeigt.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
1. Erstellen Sie eine [adaptives Formular](../../forms/using/creating-adaptive-form.md) oder öffnen Sie eine bestehende.
1. Wählen Sie **Layout** aus der Dropdownliste, die oben neben der Option **Vorschau** angezeigt wird. Das Formular wird im Layout-Modus angezeigt.

   ![Layout-Modus](assets/layout_mode_ic_new.png)

## Anpassen der Größe von Komponenten {#resize-components}

1. Wählen Sie im Layout -Modus die Komponente aus, deren Größe geändert werden soll. Die blauen Punkte werden am Beginn und am Ende des responsiven Rasters angezeigt.
1. Ziehen Sie die blauen Punkte mit der Maus, um die Position der Komponente im responsiven Raster zu definieren.

   ![Ändern der Größe mit dem Layout-Modus](assets/layout_mode_resize_new_updated1.png)

   Die Symbolleiste, die nach dem Tippen auf Komponenten angezeigt wird, besteht aus folgenden Optionen:

   * **[!UICONTROL Übergeordnet]**: Wählen Sie das übergeordnete Element einer Komponente aus.
   * **[!UICONTROL Breakpoint-Layout wiederherstellen]**: Machen Sie alle Änderungen der Größe rückgängig und wenden Sie das Standard-Layout auf die Komponente an.
   * **[!UICONTROL In neue Zeile gleiten lassen]**: Versetzt die Komponente in die nächste Zeile, wenn sich mehrere Komponenten in derselben Zeile befinden.

   Sie können die Option **[!UICONTROL Breakpoint-Layout wiederherstellen]** (![Revert Breakpoint](assets/reverttopreviouslypublishedversion.png)) auch auf Bedienfeldebene verwenden, um alle Änderungen der Größe rückgängig zu machen.

   >[!NOTE]
   >
   >Sie können die Größe von Tabellenspalten, Symbolleisten, Symbolleistenschaltflächen und Zielbereichskomponenten mit dem Layout-Modus nicht ändern. Verwenden Sie den Stilmodus, um die Größe dieser Komponenten zu ändern.

### Beispiel {#example}

**Ziel**: Eine Tabellenkomponente und eine Bildkomponente sollen eingefügt und parallel in einem adaptiven Formular positioniert werden.

1. Fügen Sie die Tabellen- und Bildkomponenten mit dem Modus Bearbeiten in das adaptive Formular ein. Die Bildkomponente wird nach der Tabellenkomponente angezeigt.
1. Wechseln Sie in den Layout -Modus und wählen Sie die Komponente Tabelle aus. Die blauen Punkte zur Größenanpassung der Komponente werden in den Spalten 1 und 12 angezeigt.
1. Ziehen Sie per Drag-und-Drop den blauen Punkt von Spalte 12 in Spalte 6 des responsiven Rasters.

   ![Definieren des Endpunkts der Tabelle](assets/layout_mode_end_point_table_new.png)

1. Wählen Sie analog dazu die Bildkomponente und ziehen Sie per Drag-und-Drop den blauen Punkt von Spalte 1 in Spalte 7 des responsiven Rasters. Die Tabellen- und Bildkomponenten werden parallel zueinander angezeigt.

   ![Tabelle und Bild parallel im Layout-Modus](assets/table_image_parallel_new.png)

   Sie können die Bildkomponente auswählen und die **In neue Zeile verschieben** -Option in der Symbolleiste verfügbar, um die Bildkomponente in die nächste Zeile zu verschieben.

## Ändern der Größe von Bereichen {#resize-panels-layout-mode}

Führen Sie folgende Schritte aus, wenn Sie die Größe des gesamten Bereichs statt der Größe einzelner Komponenten ändern möchten:

1. Wählen Sie eine der Komponenten im Bereich aus, deren Größe Sie ändern möchten, und wählen Sie ![Übergeordnetes Element auswählen](assets/select_parent_icon.svg)und wählen Sie die erste Option in der Dropdown-Liste aus, wenn das Bedienfeld direkt über der Komponente liegt.

   Die blauen Punkte werden am Beginn und am Ende des responsiven Rasters angezeigt.

1. Ziehen Sie die blauen Punkte mit der Maus, um die Position des Bereichs im responsiven Raster zu definieren.
Sie können die Schritte 1 und 2 wiederholen und mit ![Übergeordnetes Element auswählen](assets/float_to_new_line_icon.svg) den Bereich mit der Größenanpassung zur nächsten Zeile verschieben.

## Definieren eines mehrspaltigen Layouts für einen Bereich

Führen Sie folgende Schritte aus, um die Anzahl der Spalten für einen Bereich zu definieren:

1. In **[!UICONTROL Bearbeiten]** Modus, wählen Sie das Bedienfeld aus, wählen Sie ![Konfigurieren](assets/configure_icon.png)und wählen Sie **[!UICONTROL Responsiv - alles auf der Seite ohne Navigation]** Option aus der **[!UICONTROL Bedienfeldlayout]** Dropdown-Liste.

1. Auswählen ![Speichern](assets/save_icon.svg) , um die Eigenschaften zu speichern.

1. Im **[!UICONTROL Layout]** -Modus eine der Komponenten im Bedienfeld auswählen, wählen Sie ![Übergeordnetes Element auswählen](assets/select_parent_icon.svg)und wählen Sie das Bedienfeld aus.

1. Auswählen ![mehrspaltig](assets/multi-column.svg) und wählen Sie die Anzahl der Spalten aus der Dropdown-Liste aus. Die Anzahl der Spalten kann zwischen 1 und 12 liegen. Der Bereich wird in ein mehrspaltiges Layout unterteilt.

![mehrere Spalten im Layout-Modus](assets/multi-column-layout.png)

## Aktivieren des neuen responsiven Rasters für alte responsive Layouts {#enableresponsivegrid}

Aktivieren Sie das neue responsive Raster für AEM Forms, die Sie mit Forms 6.4 oder einer älteren Version erstellen, um die Größe von Komponenten zu ändern.

>[!NOTE]
>
>Beim Wechsel zum neuen responsiven Raster werden die Layout-Eigenschaften verworfen, die bereits für im Formular verwendete Komponenten definiert wurden.

Führen Sie folgende Schritte aus, um das neue responsive Raster zu aktivieren:

1. Wählen Sie **Layout** aus der Dropdownliste, die oben neben der Option **Vorschau** angezeigt wird. Eine Bestätigung zur Aktivierung des Layout-Modus wird angezeigt.
1. Auswählen **Ja** um die **Layout** -Modus für das Formular.

### Einbetten eines alten Fragments in ein adaptives Formular mit neuem responsivem Layout {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Mit dem neuen responsiven Layout für adaptive Formulare können Sie ein adaptives Formularfragment mit dem alten responsiven Layout zum Formular hinzufügen. Das neue Layout verwirft jedoch die Layout-Eigenschaften, die bereits für im Fragment verwendete Komponenten definiert wurden. Sie können zum Layout-Modus wechseln, um die Layout-Eigenschaften für die im Fragment verwendeten Komponenten zu definieren.

### Einbetten eines Fragments mit neuem responsivem Layout in ein altes adaptives Formular {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Wenn Sie ein Fragment mit dem neuen responsiven Layout in ein adaptives Formular mit altem responsivem Layout einbetten, fordert das System Sie dazu auf, den Layout-Modus für das Formular zu aktivieren und das Fragment erneut einzubetten.

Um den Layout -Modus zu aktivieren, wählen Sie **Layout** aus der Dropdownliste, die oben neben dem **Vorschau** auswählen **Ja** zur Bestätigung. Wählen Sie den Modus **Bearbeiten**, um das Fragment erneut einzubetten.

## Deaktivieren des Layout-Modus für Formulare mit altem responsivem Layout {#disable-layout-mode-for-forms-with-old-responsive-layout}

Sie können den Layout-Modus für Formulare mit altem responsivem Layout deaktivieren, indem Sie die Eigenschaften der im Formular verwendeten Vorlage bearbeiten.

Gehen Sie wie folgt vor, um den Layout-Modus zu deaktivieren:

1. Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Vorlagen]** und öffnen Sie die Vorlage, die im Formular im Modus **[!UICONTROL Bearbeiten]** verwendet wird.
1. Wählen Sie den Dokumentcontainer im linken Bereich aus und wählen Sie **[!UICONTROL Richtlinie.]**

   ![Deaktivieren des Layout-Modus](assets/policy_disable_layout_mode.png)

1. Wählen Sie die **[!UICONTROL Layout-Einstellungen]** Registerkarte und wählen Sie **[!UICONTROL Layout-Modus deaktivieren]**.
1. Auswählen ![Änderungen speichern](assets/save_icon.png) , um die Vorlageneigenschaften zu speichern.
