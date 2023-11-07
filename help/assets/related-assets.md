---
title: Verknüpfte Assets
description: Erfahren Sie, wie Sie digitale Assets mit gemeinsamen Attributen verknüpfen. Erstellen Sie außerdem von der Quelle abgeleitete Beziehungen zwischen digitalen Assets.
contentOwner: AG
role: User
feature: Collaboration,Asset Management
exl-id: ddb69727-74a0-4a4d-a14e-7d3bb5ceea2a
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 77%

---

# Verknüpfte Assets {#related-assets}

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets manuell entsprechend den Anforderungen Ihres Unternehmens verknüpfen. Verwenden Sie hierfür die Funktion „Verknüpfte Assets“. Beispielsweise können Sie einem Asset oder einem Bild/Video mit einer Lizenzdatei zu einem ähnlichen Thema verknüpfen. Sie können Assets verknüpfen, die bestimmte Attribute gemeinsam haben. Sie können die Funktion auch verwenden, um Quell-/abgeleitete Beziehungen zwischen Assets zu erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, mit der INDD-Quelldatei verknüpfen.

Mit dieser Funktion können Sie eine PDF- oder JPG-Datei mit niedriger Auflösung für Anbieter oder Agenturen freigeben und die hochauflösende INDD-Datei nur auf Anfrage verfügbar machen.

>[!NOTE]
>
>Nur Benutzer mit Bearbeitungsberechtigungen für Assets können die Assets verknüpfen und die Verknüpfung aufheben.

## Verknüpfen von Assets {#relating-assets}

1. Öffnen Sie in der [!DNL Experience Manager]-Benutzeroberfläche von die Seite **[!UICONTROL Eigenschaften]** für ein Asset, das Sie verknüpfen möchten.

   ![Öffnen der Seite „Eigenschaften“ eines Assets, um das Asset zu verknüpfen](assets/asset-properties-relate-assets.png)

   *Abbildung: [!DNL Assets] Seite [!UICONTROL Eigenschaften], um Assets zu verknüpfen.*

   Wählen Sie alternativ das gewünschte Asset in der Listenansicht aus.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Sie können das Asset auch aus einer Sammlung auswählen.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Um das ausgewählte Asset mit einem anderen Asset zu verknüpfen, klicken Sie in der Symbolleiste auf **[!UICONTROL Verknüpfen]** ![Assets verknüpfen](assets/do-not-localize/link-relate.png).
1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei für das Asset zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste.
   * Um eine abgeleitete Datei zuzuordnen, wählen Sie **[!UICONTROL Abgeleitet]** aus der Liste aus.
   * Um eine bidirektionale Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL sonstige]** aus der Liste.

1. Aus dem **[!UICONTROL Asset auswählen]** navigieren Sie zum Speicherort des Assets, das Sie zuordnen möchten, und wählen Sie es aus.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.
1. Klicken Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Je nach Auswahl der Beziehung in Schritt 3 wird das verknüpfte Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Verknüpft]** aufgeführt. Beispiel: Wenn das verknüpfte Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Um die Verknüpfung eines Assets aufzuheben, klicken Sie in der Symbolleiste auf **[!UICONTROL Verknüpfung aufheben]** ![Verknüpfung von Assets aufheben](assets/do-not-localize/link-unrelate-icon.png).

1. Wählen Sie die Assets aus, für die Sie die Verknüpfung zum **[!UICONTROL Relationen entfernen]** und klicken Sie **[!UICONTROL Nicht zuordnen]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klicken Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Die Assets, für die Sie Verknüpfungen entfernt haben, werden aus der Liste der verknüpften Assets im Abschnitt **[!UICONTROL Verknüpft]** gelöscht.

## Übersetzen verknüpfter Assets {#translating-related-assets}

Für die Übersetzungs-Workflows ist die Erstellung von Quellbeziehungen / abgeleiteten Beziehungen zwischen Assets mit der Funktion „Verknüpfte Assets“ nützlich. Wenn Sie für ein abgeleitetes Asset einen Übersetzungs-Workflow ausführen, ruft [!DNL Experience Manager Assets] automatisch beliebige Assets ab, die von der Quelldatei referenziert werden, und nimmt sie in die Übersetzung auf. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit der Quelle und den abgeleiteten Assets übersetzt. Angenommen, Ihre englischsprachige Kopie enthält ein abgeleitetes Asset und dessen Quelldatei wie gezeigt.

![chlimage_1-281](assets/chlimage_1-281.png)

Ist die Quelldatei mit einem anderen Asset verknüpft, ruft [!DNL Experience Manager Assets] das referenzierte Asset ab und nimmt es in die Übersetzung auf.

![Asset-Eigenschaftenseite, die die Quelldatei des verknüpften Assets anzeigt, das zur Übersetzung hinzugefügt werden soll](assets/asset-properties-source-asset.png)

*Abbildung: Quell-Asset der verknüpften Assets, die zur Übersetzung hinzugefügt werden sollen.*

1. Übersetzen Sie die Assets im Quellordner in eine Zielsprache, indem Sie die Schritte unter [Erstellen eines Übersetzungsprojekts](translation-projects.md#create-a-new-translation-project). Übersetzen Sie in diesem Fall beispielsweise Ihre Assets auf Französisch.

1. Öffnen Sie auf der Seite [!UICONTROL Projekte] den Übersetzungsordner.

1. Klicken Sie auf die Projektkachel, um die Seite mit den Details zu öffnen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klicke Sie auf die Auslassungszeichen unter der Karte „Übersetzungsauftrag“, um den Übersetzungsstatus anzuzeigen.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL In Assets einblenden]**, um den Übersetzungsstatus für das Asset anzuzeigen.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Um sicherzustellen, dass die mit der Quelle verknüpften Assets übersetzt wurden, klicken Sie auf das Quellen-Asset.

1. Wählen Sie das mit der Quelle verknüpfte Asset aus und klicken Sie auf **[!UICONTROL In Assets einblenden]**. Das übersetzte zugehörige Asset wird angezeigt.
