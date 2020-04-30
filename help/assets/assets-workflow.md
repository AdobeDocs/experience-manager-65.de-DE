---
title: Verarbeiten Sie Assets, um Geschäftsprozesse durchzuführen, Prüfungen durchzuführen, Compliance zu erzielen und die Grundanforderungen zu erfüllen.
description: Asset-Verarbeitung zum Konvertieren von Formaten, Erstellen von Darstellungen, Verwalten von Assets, Überprüfen von Assets und Ausführen von Workflows.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Digitale Assets verarbeiten {#process-assets}

[!DNL Adobe Experience Manager Assets] ermöglicht Ihnen, Ihre digitalen Assets auf vielfältige Weise zu bearbeiten, um eine robuste Asset-Verarbeitung zu ermöglichen. Sie können die standardmäßigen oder angepassten Verarbeitungsmethoden verwenden, um den Abschluss von End-to-End-Geschäftsprozessen, Prüfungen und Kompatibilität, Erkennung und Verteilung sowie die grundlegende Zuverlässigkeit Ihrer digitalen Assets sicherzustellen. Sie können die Asset-Management-Aufgaben ausführen und dabei die erforderliche Skalierung und Anpassung durchführen.

## Verstehen Sie Workflows {#understand-workflows}

Zur Verarbeitung von Assets [!DNL Experience Manager] werden Workflows verwendet. Workflows helfen bei der Automatisierung der Geschäftslogik oder der Aktivitäten. Granuläre Schritte zum Ausführen bestimmter Aufgaben werden standardmäßig bereitgestellt, und Entwickler können eigene benutzerdefinierte Schritte erstellen. Diese Schritte können in einer logischen Reihenfolge kombiniert werden, um Workflows zu erstellen. Ein Workflow kann beispielsweise Wasserzeichen auf hochgeladene Bilder anwenden, die auf bestimmten Kriterien basieren, wie dem hochgeladenen Ordner, der Bildauflösung usw. Ein weiteres Beispiel ist ein Workflow, der für Wasserzeichen konfiguriert ist und gleichzeitig Metadaten hinzufügt, Darstellungen erstellt, intelligente Tags hinzugefügt und in einem Datenspeicher veröffentlicht wird.

## Workflows verfügbar unter [!DNL Experience Manager]{#default-workflows}

Standardmäßig werden alle hochgeladenen Assets mit dem [!UICONTROL DAM Update Asset] -Arbeitsablauf verarbeitet. Der Arbeitsablauf wird für jedes hochgeladene Asset ausgeführt und führt grundlegende Aufgaben zur Asset-Verwaltung durch, wie z. B. Generierung von Ausgabeformaten, Schreibback von Metadaten, Extraktion von Seiten, Extraktion von Medien und Transkodierung.

Informationen zu den verschiedenen Workflow-Modellen, die standardmäßig verfügbar sind, finden Sie unter **[!UICONTROL Werkzeuge > Workflow > Modelle]** in [!DNL Experience Manager].

![Einige der standardmäßigen Arbeitsabläufe](assets/aem-default-workflows.png)

*Abbildung: Einige der standardmäßigen Workflows in[!DNL Experience Manager].*

## Apply workflows to process assets {#applying-workflows-to-assets}

Das Anwenden von Workflows auf digitale Assets entspricht dem Vorgehen bei den Seiten einer Website. For a complete guide on how to create and use workflows, see [start workflows](/help/sites-authoring/workflows-participating.md).

Nutzen Sie Workflows in digitalen Assets, um das Asset zu aktivieren oder Wasserzeichen zu erstellen. Viele Workflows für Assets werden automatisch aktiviert. Beispielsweise wird der Workflow, mit dem nach der Bearbeitung eines Bildes automatisch ein Ausgabeformat erstellt wird, automatisch aktiviert.

>[!NOTE]
>
>If a workflow available in Classic UI is not available in Touch enabled UI, like [!UICONTROL Request to Activate] and [!UICONTROL Request to Deactivate], see [make workflow models](/help/sites-developing/workflows-models.md#classic2touchui).

## Apply a workflow to an asset {#apply-a-workflow-to-an-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->
Gehen Sie wie folgt vor, um einen Workflow auf ein Asset anzuwenden:

1. Navigieren Sie zum Speicherort des Assets, für das Sie einen Workflow erstellen möchten, und klicken Sie auf das Asset, um die Asset-Seite zu öffnen. Wählen Sie im Menü die Option **[!UICONTROL Zeitschiene]** aus, um die Zeitschiene anzuzeigen.

   ![timeline-1](assets/timeline.png)

1. Click **[!UICONTROL Actions]** at the bottom to open the list of actions available for the asset.

1. Click **[!UICONTROL Start Workflow]** from the list.

1. Wählen Sie im Dialogfeld **[!UICONTROL Workflow starten]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-254](assets/chlimage_1-50.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der verwendet werden kann, um auf die Instanz des Workflows zu verweisen.

   ![chlimage_1-255](assets/chlimage_1-51.png)

1. Click **[!UICONTROL Start]** and then click **[!UICONTROL Proceed]**. Jeder Schritt des Workflows wird in der Timeline als ein Ereignis angezeigt.

   ![chlimage_1-256](assets/chlimage_1-52.png)

## Anwenden eines Workflows auf mehrere Assets {#applying-a-workflow-to-multiple-assets}

1. Navigieren Sie in der Assets-Konsole zum Verzeichnis der Assets, für die Sie einen Workflow starten möchten, und wählen Sie die Assets aus. Wählen Sie im Menü die Option **[!UICONTROL Zeitschiene]** aus, um die Zeitschiene anzuzeigen.

   ![screen_shot_2019-03-06at123325pm](assets/chlimage_1-136.png)

1. Klicken Sie unten auf **[!UICONTROL Aktionen]** .

   ![chlimage_1-30](assets/chlimage_1-137.png)

1. Klicken Sie auf **[!UICONTROL Workflow starten]**. Wählen Sie im Dialogfeld **[!UICONTROL Workflow starten]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-31](assets/chlimage_1-138.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der für den Verweis auf die Workflow-Instanz verwendet werden kann.
1. Klicken Sie auf **[!UICONTROL Starten]** und anschließend im Dialogfeld auf **[!UICONTROL Bestätigen]**. Der Workflow wird für alle Assets ausgeführt, die Sie ausgewählt haben.

## Anwenden eines Workflows auf mehrere Ordner {#applying-a-workflow-to-multiple-folders}

Die Vorgehensweise zum Anwenden eines Workflows auf mehrere Ordner ähnelt der Vorgehensweise beim Anwenden eines Workflows auf mehrere Assets. Select the folders in the [!DNL Assets] interface, and perform steps 2-7 of the procedure [apply a workflow to multiple assets](/help/assets/assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Apply a workflow to a collection {#applying-a-workflow-to-a-collection}

Siehe [Anwenden eines Workflows auf eine Sammlung](/help/assets/managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Automatisches Beginn eines Workflows zur bedingten Verarbeitung von Assets {#auto-execute-workflow-on-some-assets}

Administratoren können Arbeitsabläufe so konfigurieren, dass Assets auf der Grundlage vordefinierter Bedingungen automatisch ausgeführt und verarbeitet werden. Diese Funktion ist beispielsweise nützlich für Benutzer und Marketingfachleute, um einen benutzerdefinierten Workflow für bestimmte Ordner zu erstellen. Angenommen, alle Assets aus dem Foto einer Agentur können mit einem Wasserzeichen versehen oder alle von einem freiberuflichen Anbieter hochgeladenen Assets können verarbeitet werden, um bestimmte Darstellungen zu erstellen.

Für ein Workflow-Modell können Benutzer einen Workflow-Starter erstellen, der es ausführt. Ein Workflow-Starter überwacht Änderungen im Inhalts-Repository und führt den Workflow aus, wenn die vordefinierten Bedingungen erfüllt sind. Administratoren können Marketingexperten Zugriff gewähren, um die Workflows zu erstellen und den Starter zu konfigurieren. Benutzer können den standardmäßigen Arbeitsablauf [!UICONTROL DAM Update Asset] ändern, um die zusätzlichen Schritte hinzuzufügen, die zur Verarbeitung bestimmter Assets erforderlich sind. Der Workflow wird für alle neu hochgeladenen Assets ausgeführt. Verwenden Sie einen der folgenden Ansätze, um die Ausführung der zusätzlichen Schritte für bestimmte Assets zu beschränken:

* Erstellen Sie eine Kopie des [!UICONTROL DAM Update Asset] -Workflows und ändern Sie ihn, um ihn in einer bestimmten Ordnerhierarchie auszuführen. Dieser Ansatz ist für einige Ordner nützlich.
* Die zusätzlichen Verarbeitungsschritte können mit einer [ODER-Teilung](/help/sites-developing/workflows-step-ref.md#or-split) hinzugefügt werden, die je nach Bedarf für so viele Ordner gilt.

>[!MORELIKETHIS]
>
>* [Workflows](/help/sites-authoring/workflows.md)
>* [Erstellen von Workflow-Modellen und Erweitern der Workflow-Funktionalität](/help/sites-developing/workflows.md)
>* [Methoden zum Ausführen Workflows](/help/sites-administering/workflows-starting.md)
>* [Best Practices für Arbeitsabläufe](/help/sites-developing/workflows-best-practices.md)
>* [Community-Artikel zum Ändern von Assets mithilfe des Workflows](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)

