---
title: 'Erstellen von Übersetzungsprojekten '
description: Erfahren Sie, wie Sie Übersetzungsprojekte in AEM erstellen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: d15273e9308926ca4745fc1045e2da9fe8ed91d4

---


# Erstellen von Übersetzungsprojekten{#creating-translation-projects} 

Um eine Sprachkopie zu erstellen, lösen Sie eine der folgenden Sprachkopien aus, die in der Leiste &quot;Referenzen&quot;auf der AEM-Benutzeroberfläche verfügbar Workflows.

* **Erstellen und übersetzen**: In diesem Arbeitsablauf werden die zu übersetzenden Assets in die Sprachstamm der Sprache kopiert, in die Sie übersetzen möchten. Darüber hinaus wird je nach gewählten Optionen ein Übersetzungsprojekt für die Assets in der Projektekonsole erstellt. Je nach Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald es erstellt wurde.

* **Sprachkopien** aktualisieren: Führen Sie diesen Workflow aus, um eine zusätzliche Gruppe von Assets zu übersetzen und sie in eine Sprachkopie für ein bestimmtes Gebietsschema einzuschließen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält.

>[!NOTE]
>
>Asset-Binärdateien werden nur dann übersetzt, wenn der Übersetzungsanbieter die Übersetzung von Binärdaten unterstützt.

>[!NOTE]
>
>Wenn Sie einen Übersetzungs-Workflow für komplexe Assets wie PDF- und InDesign-Dateien starten, werden deren Teilassets oder Darstellungen (sofern vorhanden) nicht zur Übersetzung gesendet.

## Workflow für das Erstellen und Übersetzen {#create-and-translate-workflow}

Sie verwenden den Arbeitsablauf zum Erstellen und Übersetzen, um zum ersten Mal Sprachkopien für eine bestimmte Sprache zu erstellen. Der Workflow bietet die folgenden Optionen:

* Nur Struktur erstellen
* Neues Übersetzungsprojekt erstellen
* Zu vorhandenem Übersetzungsprojekt hinzufügen

### Nur Struktur erstellen {#create-structure-only}

Verwenden Sie die Option **[!UICONTROL Nur Struktur erstellen]**, um eine Zielordnerhierarchie im Zielsprachstamm zu erstellen, die der Hierarchie des Quellordners im Quellsprachstamm entspricht. In diesem Fall werden Quellelemente in den Zielordner kopiert. Es wird jedoch kein Übersetzungsprojekt generiert.

1. Wählen Sie in der Benutzeroberfläche von Assets den Ordner, für den Sie eine Struktur im Zielsprachenstamm erstellen möchten.
1. Öffnen Sie den Bereich **[!UICONTROL Referenzen]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache, für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. Wählen Sie in der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Nur Struktur erstellen]**.

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. Tippen/Klicken Sie auf **[!UICONTROL Erstellen]**. The new structure for the target language is listed under **[!UICONTROL Language Copies]**.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Klicken/tippen Sie auf die Struktur aus der Liste und dann auf **[!UICONTROL In Assets einblenden]**, um zur Ordnerstruktur in der Zielsprache zu navigieren.

   ![chlimage_1-62](assets/chlimage_1-62.png)

### Neues Übersetzungsprojekt erstellen {#create-a-new-translation-project}

Wenn Sie diese Option verwenden, werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Je nach gewählten Optionen wird ein Übersetzungsprojekt für die Assets in der Projektekonsole erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald es erstellt wird.

1. Wählen Sie in der Benutzeroberfläche von Assets den Ordner, für den Sie eine Sprachkopie erstellen möchten.
1. Öffnen Sie den Bereich **[!UICONTROL Referenzen]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.

   ![chlimage_1-64](assets/chlimage_1-64.png)

1. Wählen Sie in der Liste **[!UICONTROL Zielsprachen]** die Sprache(n) aus, für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Titel für das Projekt ein.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Tippen/Klicken Sie auf **[!UICONTROL Erstellen]**. Assets aus dem Quellordner werden in die Zielordner für die Gebietsschemata kopiert, die Sie in Schritt 4 gewählt haben.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Um zum Ordner zu navigieren, wählen Sie die Sprachkopie und klicken Sie auf **[!UICONTROL In Assets einblenden]**.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Navigieren Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektekonsole kopiert.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Klicken/tippen Sie auf das Projekt, um die Seite mit den Details zu öffnen.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigieren Sie zur Benutzeroberfläche „Assets“ und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

   ![Ansicht der übersetzten Metadaten auf der Seite &quot;Asset-Eigenschaften&quot;](assets/translated-metadata-asset-properties.png)

   *Abbildung: Übersetzte Metadaten auf der Seite &quot;Asset-Eigenschaften&quot;*


   >[!NOTE]
   >
   >Diese Funktion ist sowohl für Assets als auch für Ordner verfügbar. Wenn ein Asset anstelle eines Ordners gewählt wurde, wird die gesamte Hierarchie der Ordner bis zum Sprachstamm kopiert, um eine Sprachkopie für das Asset zu erstellen.

### Zu vorhandenem Übersetzungsprojekt hinzufügen {#add-to-existing-translation-project}

Wenn Sie diese Option verwenden, wird der Übersetzungs-Workflow für Assets ausgeführt, die Sie zum Quellordner hinzufügen, nachdem bereits ein Übersetzungs-Workflow ausgeführt wurde. Nur die neu hinzugefügten Assets werden in den Zielordner kopiert, der zuvor übersetzte Assets enthält. In diesem Fall wird kein neues Übersetzungsprojekt erstellt.

1. Navigieren Sie in der Benutzeroberfläche „Assets“ zu dem Ordner, der nicht übersetzte Assets enthält.
1. Wählen Sie ein zu übersetzendes Asset aus und öffnen Sie den **[!UICONTROL Referenzbereich]**. Im Abschnitt **[!UICONTROL Sprachkopien]** wird die Anzahl der derzeit verfügbaren Übersetzungskopien angezeigt.
1. Tippen/Klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**. Eine Liste der verfügbaren Übersetzungskopien wird angezeigt.
1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Wählen Sie in der Liste **[!UICONTROL Zielsprachen]** die Sprache(n) aus, für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Wählen Sie in der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** aus, um den Übersetzungsworkflow im Ordner auszuführen.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Wenn Sie die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** wählen, wird Ihr Übersetzungsprojekt zu einem vorhandenen Projekt hinzugefügt, sofern Ihre Projekteinstellungen genau den Einstellungen des bereits vorhandenen Projekts entsprechen. Anderenfalls wird ein neues Projekt erstellt.

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Tippen/Klicken Sie auf **[!UICONTROL Erstellen]**. Die zu übersetzenden Assets werden dem Zielordner hinzugefügt. Der aktualisierte Ordner wird im Abschnitt **[!UICONTROL Sprachkopien]** aufgeführt.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Navigieren Sie zur Projektkonsole und öffnen Sie das vorhandene Übersetzungsprojekt, dem Sie Assets hinzugefügt haben.
1. Klicken/tippen Sie auf das Übersetzungsprojekt, um die Seite mit den Projektdetails anzuzeigen.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Click/tap the ellipsis at the bottom of the **Translation Job** tile to view the assets in the translation workflow. In der Übersetzungsauftragsliste werden auch Einträge für Asset-Metadaten und -Tags aufgeführt. Diese Einträge geben an, dass die Metadaten und Tags für die Assets ebenfalls übersetzt werden.

   >[!NOTE]
   >
   >Wenn Sie den Eintrag für Tags oder Metadaten löschen, werden keine Tags oder Metadaten für die Assets übersetzt.

   >[!NOTE]
   >
   >Wenn Sie die maschinelle Übersetzung verwenden, werden Asset-Binärdateien nicht übersetzt.

   >[!NOTE]
   >
   >Wenn das Asset, das Sie zum Übersetzungsauftrag hinzufügen, Teil-Assets enthält, wählen Sie die Teil-Assets und entfernen Sie sie, damit die Übersetzung fehlerfrei fortgesetzt werden kann.

1. To start the translation for the assets, click/tap the arrow on the **[!UICONTROL Translation Job]** tile and select **[!UICONTROL Start]** from the list.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

   ![chlimage_1-82](assets/chlimage_1-82.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Nach Abschluss des Übersetzungsvorgangs ändert sich der Status in „Bereit für Überprüfung“. Navigieren Sie zur Benutzeroberfläche „Assets“ und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

## Sprachkopien aktualisieren {#update-language-copies}

Führen Sie diesen Workflow aus, um eine weitere Gruppe von Assets zu übersetzen und in eine Sprachkopie für ein bestimmtes Gebietsschema aufzunehmen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält. Abhängig von den gewählten Optionen wird ein Übersetzungsprojekt erstellt oder ein vorhandenes Übersetzungsprojekt für die neuen Assets aktualisiert. Der Workflow zum Aktualisieren der Sprachkopien umfasst die folgenden Optionen:

* Neues Übersetzungsprojekt erstellen
* Zu vorhandenem Übersetzungsprojekt hinzufügen

### Neues Übersetzungsprojekt erstellen {#create-a-new-translation-project-1}

Wenn Sie diese Option verwenden, wird ein Übersetzungsprojekt für den Satz von Assets erstellt, für die Sie eine Sprachkopie aktualisieren möchten.

1. Wählen Sie in der Benutzeroberfläche „Assets“ den Quellordner, dem Sie einen Asset-Ordner hinzugefügt haben.
1. Öffnen Sie den Bereich **[!UICONTROL Referenzen]** und tippen/klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Liste der Sprachkopien anzuzeigen.
1. Aktivieren Sie das Kontrollkästchen vor **[!UICONTROL Sprachkopien]** und wählen Sie dann den Zielordner aus, der dem entsprechenden Gebietsschema entspricht.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Klicken/tippen Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Titel für das Projekt ein.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Tippen/Klicken Sie auf **[!UICONTROL Launch]**.
1. Navigieren Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektekonsole kopiert.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Klicken/tippen Sie auf das Projekt, um die Seite mit den Details zu öffnen.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Um die Übersetzung der Assets zu starten, klicken Sie auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf den Pfeil und wählen Sie aus der Liste die Option **[!UICONTROL Start]**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigieren Sie zur Benutzeroberfläche „Assets“ und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

### Zu vorhandenem Übersetzungsprojekt hinzufügen {#add-to-existing-translation-project-1}

Wenn Sie diese Option verwenden, wird die Gruppe der Assets zu einem vorhandenen Übersetzungsprojekt hinzugefügt, um die Sprachkopien für das von Ihnen gewählte Gebietsschema zu aktualisieren.

1. Wählen Sie in der Benutzeroberfläche „Assets“ den Quellordner, dem Sie einen Asset-Ordner hinzugefügt haben.
1. Öffnen Sie den **[!UICONTROL Referenzbereich]** und tippen/klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Liste der Sprachkopien anzuzeigen.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Aktivieren Sie das Kontrollkästchen vor **[!UICONTROL Sprachkopien]**. So werden alle Sprachkopien ausgewählt. Heben Sie die Auswahl anderer Kopien auf, mit Ausnahme der Sprachkopie(n), die dem/den Gebietsschema(ta) entspricht/entsprechen, in das/die Sie übersetzen möchten.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Klicken/tippen Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. From the **[!UICONTROL Project]** list, choose **[!UICONTROL Add to existing translation project]**.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Tippen/Klicken Sie auf **[!UICONTROL Launch]**.
1. See steps 9-14 of [Add to existing translation project](translation-projects.md#add-to-existing-translation-project) to complete the rest of the procedure.

## Erstellen von temporären Sprachkopien {#creating-temporary-language-copies}

Wenn Sie einen Übersetzungs-Workflow ausführen, um eine Sprachkopie mit bearbeiteten Versionen der ursprünglichen Assets zu aktualisieren, wird die vorhandene Sprachkopie beibehalten, bis Sie die übersetzten Assets genehmigen. AEM Assets speichert die neu übersetzten Assets an einem temporären Speicherort und aktualisiert die vorhandene Sprachkopie, nachdem Sie die Assets genehmigt haben. Wenn Sie die Assets ablehnen, bleibt die Sprachkopie unverändert.

1. Tippen/Klicken Sie unter **[!UICONTROL Sprachkopien]**, für die Sie bereits eine Sprachkopie erstellt haben, auf den Quellstammordner und dann auf **[!UICONTROL In Assets anzeigen]**, um den Ordner in AEM Assets zu öffnen.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Wählen Sie in der Benutzeroberfläche von Assets ein bereits übersetztes Asset und tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.
1. Bearbeiten Sie das Asset und speichern Sie die Änderungen.
1. Perform steps 2-14 of the [Add to existing translation project](#add-to-existing-translation-project) procedure to update the language copy.
1. Click/tap the ellipsis at the bottom of the **[!UICONTROL Translation Job]** tile. Der Liste der Assets auf der Seite **[!UICONTROL Übersetzungsauftrag]** können Sie den temporären Speicherort der übersetzten Version des Assets entnehmen.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL Titel]**.
1. Tippen/Klicken Sie in der Symbolleiste auf **[!UICONTROL Übersetzung akzeptieren]** und im Dialogfeld anschließend auf **[!UICONTROL Akzeptieren]**, um das ursprüngliche Asset im Zielordner mit der übersetzten Version des bearbeiteten Assets zu überschreiben.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   >[!NOTE]
   >
   >Damit der Übersetzungs-Workflow die Ziel-Assets aktualisieren kann, akzeptieren Sie sowohl das Asset als auch die Metadaten.

   Click/tap **[!UICONTROL Reject Translation]** to retain the originally translated version of the asset in the target locale root and reject the edited version.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Navigieren Sie zur Assets-Konsole und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

For tips on translating metadata for assets efficiently, see [5 Steps for Efficiently Translating Metadata](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).
