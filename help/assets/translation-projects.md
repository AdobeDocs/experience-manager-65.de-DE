---
title: Erstellen von Übersetzungsprojekten
description: Erfahren Sie, wie Sie in  [!DNL Adobe Experience Manager] Übersetzungsprojekte erstellen können.
contentOwner: AG
role: Architect, Admin
feature: Translation
exl-id: 8990feca-cfda-4974-915e-27aa9d8f2ee1
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 96%

---

# Erstellen von Übersetzungsprojekten {#creating-translation-projects}

Lösen Sie zum Erstellen einer Sprachkopie einen der folgenden Sprachkopie-Workflows aus, die in der Leiste „Verweise“ der Benutzeroberfläche von [!DNL Experience Manager] verfügbar sind.

* **Erstellen und Übersetzen**: Bei diesem Workflow werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Darüber hinaus wird je nach den von Ihnen gewählten Optionen ein Übersetzungsprojekt für die Assets in der Projektkonsole erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald das Übersetzungsprojekt erstellt wurde.

* **Sprachlopien aktualisieren**: Diesen Workflow führen Sie aus, um eine weitere Gruppe von Assets zu übersetzen und in eine Sprachkopie für ein bestimmtes Gebietsschema aufzunehmen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält.

>[!PREREQUISITES]
>
>* Benutzer, die Übersetzungsprojekte erstellen, sind Mitglieder der Gruppe `projects-administrators`.
>* Der Übersetzungsdienstleister unterstützt die Übersetzung von Binärdateien.

## Workflow für das Erstellen und Übersetzen {#create-and-translate-workflow}

Den Workflow für das Erstellen und Übersetzen verwenden Sie, um erstmals Sprachkopien für eine bestimmte Sprache zu erstellen. Der Workflow bietet die folgenden Optionen:

* Nur Struktur erstellen.
* Erstellen eines neuen Übersetzungsprojekts.
* Hinzufügen zu einem vorhandenen Übersetzungsprojekt.

### Nur Struktur erstellen {#create-structure-only}

Verwenden Sie die Option **[!UICONTROL Nur Struktur erstellen]**, um eine Zielordnerhierarchie im Zielsprachenstamm zu erstellen und die Hierarchie des Quellordners im Ausgangssprachenstamm widerzuspiegeln. In diesem Fall werden Quellelemente in den Zielordner kopiert. Es wird jedoch kein Übersetzungsprojekt generiert.

1. Wählen Sie in der Benutzeroberfläche von [!DNL Assets] den Ordner, für den Sie eine Struktur im Zielsprachenstamm erstellen möchten.

1. Öffnen Sie den Fensterbereich **[!UICONTROL Verweise]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![Sprachkopien](assets/translation-language-copies.png)

1. Klicken Sie auf **[!UICONTROL Erstellen und Übersetzen]**. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache, für die Sie eine Ordnerstruktur erstellen möchten.

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Nur Struktur erstellen]**.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Die neue Struktur für die Zielsprache wird unter **[!UICONTROL Sprachkopien]** aufgeführt.

   ![Sprachkopien](assets/lang-copy2.png)

1. Klicken Sie auf die Struktur aus der Liste und dann auf **[!UICONTROL In Assets einblenden]**, um zur Ordnerstruktur in der Zielsprache zu navigieren.

   ![Einblenden von Assets](assets/reveal-in-assets.png)

### Erstellen eines neuen Übersetzungsprojekts {#create-a-new-translation-project}

Wenn Sie diese Option verwenden, werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Je nach den von Ihnen gewählten Optionen wird ein Übersetzungsprojekt für die Assets in der Projektkonsole erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald das Übersetzungsprojekt erstellt wurde.

1. Wählen Sie in der Benutzeroberfläche von [!DNL Assets] den Ordner, für den Sie eine Sprachkopie erstellen möchten.
1. Wechseln Sie zum Fensterbereich **[!UICONTROL Verweise]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. Klicken Sie unten auf **[!UICONTROL Erstellen und Übersetzen]**.

1. Aus dem **[!UICONTROL Zielsprachen]** wählen Sie die Sprachen aus, für die Sie eine Ordnerstruktur erstellen möchten.

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Namen für das Projekt ein.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. [!DNL Assets] aus dem Quellordner werden in die Zielordner für die Gebietsschemata kopiert, die Sie in Schritt 4 gewählt haben.

   ![Sprachkopien](assets/lang-copy2.png)

1. Um zum Ordner zu navigieren, wählen Sie die Sprachkopie und klicken Sie auf **[!UICONTROL In Assets einblenden]**.

   ![Einblenden von Assets](assets/reveal-in-assets.png)

1. Gehen Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektkonsole kopiert.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Klicken Sie auf das Projekt, um die Seite mit den Details zu öffnen.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Gehen Sie zur Benutzeroberfläche von [!DNL Assets] und öffnen Sie die Seite mit den [!UICONTROL Eigenschaften] für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

   ![Anzeigen der übersetzten Metadaten auf der Seite „Asset-Eigenschaften“](assets/translated-metadata-asset-properties.png)

   *Abbildung: Übersetzte Metadaten auf der Seite „Asset-Eigenschaften“.*

   >[!NOTE]
   >
   >Diese Funktion ist sowohl für Assets als auch für Ordner verfügbar. Wenn ein Asset anstelle eines Ordners gewählt wurde, wird die gesamte Hierarchie der Ordner bis zum Sprachstamm kopiert, um eine Sprachkopie für das Asset zu erstellen.

### Hinzufügen zu einem vorhandenen Übersetzungsprojekt {#add-to-existing-translation-project}

Wenn Sie diese Option verwenden, wird der Übersetzungs-Workflow für Assets ausgeführt, die Sie dem Quellordner hinzufügen, nachdem Sie einen vorherigen Übersetzungs-Workflow ausgeführt haben. Nur die neu hinzugefügten Assets werden in den Zielordner kopiert, der zuvor übersetzte Assets enthält. In diesem Fall wird kein neues Übersetzungsprojekt erstellt.

1. Navigieren Sie in der Benutzeroberfläche von [!DNL Assets] zu dem Ordner, der nicht übersetzte Assets enthält.
1. Wählen Sie ein Asset, das Sie übersetzen möchten, und wechseln Sie zum Bereich **[!UICONTROL Verweise]**. Im Abschnitt **[!UICONTROL Sprachkopien]** wird die Anzahl der Übersetzungskopien angezeigt, die momentan verfügbar sind.
1. Klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**. Eine Liste der verfügbaren Übersetzungskopien wird angezeigt.
1. Klicken Sie unten auf **[!UICONTROL Erstellen und Übersetzen]**.

1. Aus dem **[!UICONTROL Zielsprachen]** wählen Sie die Sprachen aus, für die Sie eine Ordnerstruktur erstellen möchten.

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]**, um den Übersetzungs-Workflow für den Ordner auszuführen.

   >[!NOTE]
   >
   >Wenn Sie die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** wählen, wird Ihr Übersetzungsprojekt nur dann zu einem bereits vorhandenen Projekt hinzugefügt, wenn Ihre Projekteinstellungen genau mit den Einstellungen des bereits vorhandenen Projekts übereinstimmen. Andernfalls wird ein neues Projekt erstellt.

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Die zu übersetzenden Assets werden dem Zielordner hinzugefügt. Der aktualisierte Ordner wird unter **[!UICONTROL Sprachkopien]** aufgeführt.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Gehen Sie zur Projektkonsole und öffnen Sie das vorhandene Übersetzungsprojekt, dem Sie Assets hinzugefügt haben.
1. Klicken Sie auf das Übersetzungsprojekt, um die Seite mit den Projektdetails anzuzeigen.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Klicken Sie unten auf der Kachel **Übersetzungsauftrag** auf das Auslassungszeichen, um die Assets im Übersetzungs-Workflow anzuzeigen. In der Übersetzungsauftragsliste werden auch Einträge für Asset-Metadaten und -Tags aufgeführt. Diese Einträge geben an, dass die Metadaten und Tags für die Assets ebenfalls übersetzt werden.

   >[!NOTE]
   >
   >Wenn Sie den Eintrag für Tags oder Metadaten löschen, werden keine Tags oder Metadaten für die Assets übersetzt.

   >[!NOTE]
   >
   >Wenn das Asset, das Sie zum Übersetzungsauftrag hinzufügen, Teil-Assets enthält, wählen Sie die Teil-Assets und entfernen Sie sie, damit die Übersetzung fehlerfrei fortgesetzt werden kann.

1. Um die Übersetzung der Assets zu starten, klicken Sie auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf den Pfeil und wählen Sie aus der Liste die Option **[!UICONTROL Start]**.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   Weitere Informationen finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Nach Abschluss des Übersetzungsvorgangs ändert sich der Status in „Bereit für Überprüfung“. Gehen Sie zur Benutzeroberfläche von [!DNL Assets] und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

## Aktualisieren von Sprachkopien {#update-language-copies}

Führen Sie diesen Workflow aus, um eine weitere Gruppe von Assets zu übersetzen und in eine Sprachkopie für ein bestimmtes Gebietsschema aufzunehmen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält. Je nach Auswahl der Optionen wird ein Übersetzungsprojekt erstellt oder ein vorhandenes Übersetzungsprojekt für die neuen Assets aktualisiert. Der Workflow zum Aktualisieren der Sprachkopien umfasst die folgenden Optionen:

* Erstellen eines neuen Übersetzungsprojekts
* Hinzufügen zu einem vorhandenen Übersetzungsprojekt

### Erstellen eines neuen Übersetzungsprojekts {#create-a-new-translation-project-1}

Wenn Sie diese Option verwenden, wird ein Übersetzungsprojekt für die Gruppe von Assets erstellt, für die Sie eine Sprachkopie aktualisieren möchten.

1. Wählen Sie in der Benutzeroberfläche von [!DNL Assets] den Quellordner, dem Sie ein Asset hinzugefügt haben.
1. Öffnen Sie den Fensterbereich **[!UICONTROL Verweise]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Liste der Sprachkopien anzuzeigen.
1. Aktivieren Sie das Kontrollkästchen vor **[!UICONTROL Sprachkopien]** und wählen Sie dann den Zielordner aus, der dem entsprechenden Gebietsschema entspricht.

   ![Sprachkopie auswählen](assets/lang-copy1.png)

1. Klicken Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Namen für das Projekt ein.

1. Klicken Sie auf **[!UICONTROL Starten]**.
1. Gehen Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektkonsole kopiert.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Klicken Sie auf das Projekt, um die Seite mit den Details zu öffnen.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Um die Übersetzung der Assets zu starten, klicken Sie auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf den Pfeil und wählen Sie aus der Liste die Option **[!UICONTROL Start]**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Gehen Sie zur Benutzeroberfläche von [!DNL Assets] und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

### Hinzufügen zu einem vorhandenen Übersetzungsprojekt {#add-to-existing-translation-project-1}

Wenn Sie diese Option verwenden, wird die Gruppe der Assets zu einem vorhandenen Übersetzungsprojekt hinzugefügt, um die Sprachkopien für das von Ihnen gewählte Gebietsschema zu aktualisieren.

1. Wählen Sie in der Benutzeroberfläche von [!DNL Assets] den Quellordner, dem Sie einen Asset-Ordner hinzugefügt haben.
1. Öffnen Sie den Fensterbereich **[!UICONTROL Verweise]** und klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Liste der Sprachkopien anzuzeigen.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Sprachkopien]**, um alle Sprachkopien auszuwählen. Heben Sie die Auswahl anderer Kopien auf. Nur die Sprachkopien, die den gewünschten Gebietsschemata entsprechen, sollten ausgewählt bleiben.

   ![Sprachkopie auswählen](assets/lang-copy1.png)

1. Klicken Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]**.

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

1. Klicken Sie auf **[!UICONTROL Starten]**.
1. Führen Sie Schritt 9 bis 14 des Verfahrens [Zu vorhandenem Übersetzungsprojekt hinzufügen](translation-projects.md#add-to-existing-translation-project) aus, um den Vorgang abzuschließen.

## Erstellen temporärer Sprachkopien {#creating-temporary-language-copies}

Wenn Sie einen Übersetzungs-Workflow ausführen, um eine Sprachkopie mit bearbeiteten Versionen der ursprünglichen Assets zu aktualisieren, wird die vorhandene Sprachkopie beibehalten, bis Sie die übersetzten Assets genehmigen. [!DNL Adobe Experience Manager Assets] speichert die neu übersetzten Assets an einem temporären Speicherort und aktualisiert die vorhandene Sprachkopie, nachdem Sie die Assets explizit genehmigt haben. Wenn Sie die Assets ablehnen, bleibt die Sprachkopie unverändert.

1. Klicken Sie auf den Quellstammordner unter **[!UICONTROL Sprachkopien]**, für den Sie bereits eine Sprachkopie erstellt haben, und klicken Sie anschließend auf **[!UICONTROL In Assets einblenden]**, um den Ordner in [!DNL Experience Manager Assets] zu öffnen.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Wählen Sie in der Benutzeroberfläche von [!DNL Assets] ein bereits übersetztes Asset und tippenklicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.
1. Bearbeiten Sie das Asset und speichern Sie die Änderungen.
1. Führen Sie Schritt 2 bis 14 des Verfahrens [Zu vorhandenem Übersetzungsprojekt hinzufügen](#add-to-existing-translation-project) aus, um die Sprachkopie zu aktualisieren.
1. Klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen. Der Liste der Assets auf der Seite **[!UICONTROL Übersetzungsauftrag]** können Sie den temporären Speicherort der übersetzten Version des Assets entnehmen.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL Titel]**.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Übersetzung annehmen]** ![Übersetzung annehmen](assets/do-not-localize/thumb-up.png) und dann im Dialogfeld auf **[!UICONTROL Annehmen]**, um das übersetzte Asset im Zielordner mit der übersetzten Version des bearbeiteten Assets zu überschreiben.

   >[!NOTE]
   >
   >Damit der Übersetzungs-Workflow die Ziel-Assets aktualisieren kann, akzeptieren Sie sowohl das Asset als auch die Metadaten.

   Klicken Sie auf **[!UICONTROL Übersetzung ablehnen]** ![Übersetzung ablehnen](assets/do-not-localize/thumb-down.png), um die ursprünglich übersetzte Version des Assets im Zielgebietsschema-Stamm beizubehalten und die bearbeitete Version abzulehnen.

1. Um die übersetzten Metadaten anzuzeigen, gehen Sie zur [!DNL Assets]-Konsole und öffnen Sie die Seite [!UICONTROL Eigenschaften] für jedes der übersetzten Assets.

## Tipps und Einschränkungen {#tips-limitations}

* Wenn Sie einen Übersetzungs-Workflow für komplexe Assets wie PDF- und [!DNL Adobe InDesign]-Dateien starten, werden ihre Teil-Assets oder Ausgabeformate (sofern vorhanden) nicht zur Übersetzung übermittelt.
* Wenn Sie maschinelle Übersetzung verwenden, werden die Asset-Binärdateien nicht übersetzt.
