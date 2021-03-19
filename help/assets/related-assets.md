---
title: Zugehörige Assets
description: Erfahren Sie, wie digitale Assets, die einige allgemeine Attribute gemeinsam haben, miteinander verknüpft werden. Erstellen Sie auch Quell-abgeleitete Beziehungen zwischen digitalen Assets.
contentOwner: AG
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 47%

---


# Zugehörige Assets {#related-assets}

[!DNL Adobe Experience Manager Assets] ermöglicht die manuelle Verknüpfung von Assets auf Grundlage der Anforderungen Ihres Unternehmens mithilfe der entsprechenden Asset-Funktion. Beispielsweise können Sie einem Asset oder einem Bild/Video eine Lizenzdatei zu einem ähnlichen Thema zuordnen. Sie können Assets zuordnen, die bestimmte gängige Attribute teilen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, der INDD-Quelldatei zuordnen.

Mit dieser Funktion haben Sie die Flexibilität, eine PDF- oder JPG-Datei mit niedriger Auflösung für Händler oder Agenturen freizugeben und die hochauflösende INDD-Datei nur auf Anfrage verfügbar zu machen.

>[!NOTE]
>
>Nur Benutzer mit Bearbeitungsberechtigungen für Assets können die Assets verknüpfen und die Verknüpfung aufheben.

## Zuordnen von Assets {#relating-assets}

1. Öffnen Sie in der Oberfläche [!DNL Experience Manager] die Seite **[!UICONTROL Eigenschaften]** für ein Asset, das Sie verknüpfen möchten.

   ![Öffnen der Seite &quot;Eigenschaften&quot;eines Assets, um das Asset zu verknüpfen](assets/asset-properties-relate-assets.png)

   *Abbildung:  [!DNL Assets] [!UICONTROL Eigenschaften ] zu verknüpfen.*

   Wählen Sie alternativ das gewünschte Asset in der Liste aus.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Sie können das Asset auch aus einer Sammlung auswählen.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Um ein anderes Asset mit dem ausgewählten Asset zu verknüpfen, klicken Sie in der Symbolleiste auf **[!UICONTROL Relate]** ![Verknüpfen von Assets](assets/do-not-localize/link-relate.png).
1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei des Elements zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste aus.
   * Um eine abgeleitete Datei zuzuordnen, wählen Sie **[!UICONTROL Abgeleitet]** aus der Liste aus.
   * Um eine Zweiwege-Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL Andere]** aus der Liste aus.

1. Navigieren Sie im Bildschirm **[!UICONTROL Assets auswählen]** zum Speicherort des Elements, das Sie zuordnen möchten, und wählen Sie es aus.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.
1. Klicken Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Je nach Auswahl der Beziehung in Schritt 3 wird das zugeordnete Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Zugehörig]** aufgeführt. Beispiel: Wenn das zugeordnete Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Um die Verknüpfung eines Assets aufzuheben, klicken Sie in der Symbolleiste auf **[!UICONTROL Aufheben der Verknüpfung]** ![Aufheben der Verknüpfung von Assets](assets/do-not-localize/link-unrelate-icon.png).

1. Wählen Sie im Dialogfeld **[!UICONTROL Beziehungen entfernen]** die Elemente aus, für die Sie die Verknüpfung aufheben möchten, und klicken Sie auf **[!UICONTROL Aufheben der Verknüpfung]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klicken Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Die Assets, für die Sie Verbindungen entfernt haben, werden aus der Liste der zugeordneten Assets im Abschnitt **[!UICONTROL Zugehörig]** gelöscht.

## Übersetzen zugehöriger Assets {#translating-related-assets}

Das Erstellen von Quell-/abgeleiteten Beziehungen zwischen Assets mithilfe der entsprechenden Asset-Funktion ist auch bei der Workflows hilfreich. Wenn Sie einen Übersetzungs-Workflow für ein abgeleitetes Asset ausführen, ruft [!DNL Experience Manager Assets] automatisch jedes Asset ab, auf das die Quelldatei verweist, und fügt es zur Übersetzung ein. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit dem Quell-Asset und den abgeleiteten Assets übersetzt. Beispiel: In einem Szenario enthält die Kopie in englischer Sprache ein abgeleitetes Asset und die entsprechende Quelldatei wie gezeigt.

![chlimage_1-281](assets/chlimage_1-281.png)

Wenn die Quelldatei mit einem anderen Asset verknüpft ist, ruft [!DNL Experience Manager Assets] das referenzierte Asset ab und fügt es zur Übersetzung ein.

![Seite &quot;Asset-Eigenschaften&quot;zeigt die Quelldatei des zugehörigen Assets an, die zur Übersetzung verwendet werden soll](assets/asset-properties-source-asset.png)

*Abbildung: Quell-Asset der zugehörigen Assets, die für die Übersetzung verwendet werden sollen.*

1. Übersetzen Sie die Assets im Quellordner für eine Zielsprache, indem Sie die Schritte unter [Neues Übersetzungsprojekt erstellen](translation-projects.md#create-a-new-translation-project) befolgen. Übersetzen Sie in diesem Fall zum Beispiel Ihre Assets ins Französische.

1. Öffnen Sie auf der Seite [!UICONTROL Projekte] den Übersetzungsordner.

1. Klicken Sie auf die Projektkachel, um die Detailseite zu öffnen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klicken Sie auf die Auslassungspunkte unter der Karte Übersetzungsauftrag, um den Übersetzungsstatus Ansicht.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Wählen Sie das Asset aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL In Assets anzeigen]**, um den Übersetzungsstatus für das Asset Ansicht.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Klicken Sie auf das Quellelement, um zu überprüfen, ob die mit der Quelle verknüpften Assets übersetzt wurden.

1. Wählen Sie das Asset aus, das mit der Quelle in Beziehung steht, und klicken Sie dann auf **[!UICONTROL In Assets anzeigen]**. Das übersetzte zugehörige Asset wird angezeigt.
