---
title: Verwandte Assets
description: Erfahren Sie, wie Sie Assets mit bestimmten gemeinsamen Attributen verknüpfen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: d15273e9308926ca4745fc1045e2da9fe8ed91d4

---


# Related assets {#related-assets}

Mit Adobe Experience Manager (AEM)-Assets können Sie Assets mithilfe der entsprechenden Asset-Funktion manuell auf Grundlage der Anforderungen Ihres Unternehmens verknüpfen. Beispielsweise können Sie einem Asset oder einem Bild/Video eine Lizenzdatei zu einem ähnlichen Thema zuordnen. Sie können Assets zuordnen, die bestimmte gängige Attribute teilen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, der INDD-Quelldatei zuordnen.

Mit dieser Funktion haben Sie die Flexibilität, eine PDF- oder JPG-Datei mit niedriger Auflösung für Händler oder Agenturen freizugeben und die hochauflösende INDD-Datei nur auf Anfrage verfügbar zu machen.

>[!NOTE] Nur Benutzer mit Bearbeitungsberechtigungen für Assets können die Assets verknüpfen und die Verknüpfung aufheben.
>

## Relate assets {#relating-assets}

1. From the AEM interface, open the **[!UICONTROL Properties]** page for an asset that you want to relate.

   ![Öffnen der Seite &quot;Eigenschaften&quot;eines Assets, um das Asset zu verknüpfen](assets/asset-properties-relate-assets.png)

   *Abbildung: Seite mit Asset-Eigenschaften zum Verknüpfen von Assets*

   Wählen Sie alternativ das gewünschte Asset in der Liste aus.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Sie können das Asset auch aus einer Sammlung auswählen.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Um dem ausgewählten Asset ein anderes Asset zuzuordnen, klicken/tippen Sie in der Symbolleiste auf das Symbol für **[!UICONTROL Zuordnen]**.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei des Elements zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste aus.
   * To relate a derived file, select **[!UICONTROL Derived]** from the list.
   * Um eine Zweiwege-Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL Andere]** aus der Liste aus.
   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Navigieren Sie im Bildschirm **[!UICONTROL Assets auswählen]** zum Speicherort des Elements, das Sie zuordnen möchten, und wählen Sie es aus.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken/tippen Sie auf das Symbol **[!UICONTROL Bestätigen]**.
1. Click/tap **[!UICONTROL OK]** to close the dialog. Je nach Auswahl der Beziehung in Schritt 3 wird das zugeordnete Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Zugehörig]** aufgeführt. Beispiel: Wenn das zugeordnete Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. To un-relate an asset, click/tap **[!UICONTROL Unrelate]** from the toolbar.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Select the asset(s) you want to un-relate from the **[!UICONTROL Remove Relations]** dialog, and the click/tap **[!UICONTROL Unrelate]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klicken/tippen Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Die Assets, für die Sie Verbindungen entfernt haben, werden aus der Liste der zugeordneten Assets im Abschnitt **[!UICONTROL Zugehörig]** gelöscht.

## Übersetzen von zugehörigen Assets {#translating-related-assets}

Für die Übersetzungs-Workflows ist die Erstellung von Quellbeziehungen/abgeleiteten Beziehungen zwischen Assets mit der Funktion „Zugehörige Assets“ nützlich. Wenn Sie für ein abgeleitetes Asset einen Übersetzungs-Workflow ausführen, ruft AEM Assets automatisch beliebige Assets ab, die von der Quelldatei referenziert werden, und nimmt sie in die Übersetzung auf. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit dem Quell-Asset und den abgeleiteten Assets übersetzt. Beispiel: In einem Szenario enthält die Kopie in englischer Sprache ein abgeleitetes Asset und die entsprechende Quelldatei wie gezeigt.

![chlimage_1-281](assets/chlimage_1-281.png)

Wenn die Quelldatei mit einem anderen Asset verknüpft ist, ruft Experience Manager Assets das referenzierte Asset ab und nimmt es zur Übersetzung auf.

![Seite &quot;Asset-Eigenschaften&quot;zeigt die Quelldatei des zugehörigen Assets an, die zur Übersetzung verwendet werden soll](assets/asset-properties-source-asset.png)

*Abbildung: Quellenasset der zugehörigen Assets, die zur Übersetzung verwendet werden sollen*

1. Übersetzen Sie die Assets im Quellordner für eine Zielsprache, indem Sie die Schritte unter [Neues Übersetzungsprojekt erstellen](translation-projects.md#create-a-new-translation-project) befolgen. Übersetzen Sie in diesem Fall zum Beispiel Ihre Assets ins Französische.

1. From the [!UICONTROL Projects] page, open the translation folder.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Klicken/tippen Sie auf die Projektkachel, um die Seite mit den Details zu öffnen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klicken/tippen Sie auf die Auslassungszeichen unter der Karte „Übersetzungsauftrag“, um den Übersetzungsstatus anzuzeigen.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Wählen Sie das Asset aus und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL In Assets einblenden]**, um den Übersetzungsstatus für das Asset anzuzeigen.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Um sicherzustellen, dass die der Quelle zugeordneten Assets übersetzt wurden, klicken/tippen Sie auf das Quellelement.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Select the asset that is related to the source, and then click/tap **[!UICONTROL Reveal in Assets]**. Das übersetzte zugehörige Asset wird angezeigt.

   ![chlimage_1-288](assets/chlimage_1-288.png)
