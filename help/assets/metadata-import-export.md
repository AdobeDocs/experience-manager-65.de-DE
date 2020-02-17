---
title: Importieren und Exportieren von Asset-Metadaten in Massen
description: Importieren und Exportieren von Asset-Metadaten in Massen
contentOwner: AG
translation-type: tm+mt
source-git-commit: 07c1a4102539ba4678c55dee3a4882101e39864f

---


# Importieren und Exportieren von Asset-Metadaten in Massen {#import-and-export-asset-metadata-in-bulk}

Mit AEM Assets können Sie Asset-Metadaten mithilfe einer CSV-Datei in Massen importieren. Sie können für die kürzlich hochgeladenen Assets oder die vorhandenen Assets eine Massenaktualisierung durchführen, indem Sie eine CSV-Datei importieren. Außerdem können Sie Asset-Metadaten von Drittanbietersystemen mithilfe des CSV-Formats in Batches aufnehmen.

## Metadaten importieren {#import-metadata}

Der Metadatenimport ist asynchron und beeinträchtigt nicht die Systemleistung. Die gleichzeitige Aktualisierung der Metadaten für mehrere Assets kann aufgrund der XMP-Writeback-Aktivität ressourcenintensiv sein, wenn das Flag für die Arbeitsabläufe gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

>[!NOTE]
>
>Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.

1. Navigieren Sie zur Benutzeroberfläche „Assets“ und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie aus dem Menü **[!UICONTROL Metadaten]** aus.
1. In the **[!UICONTROL Metadata Import]** page, tap/click **[!UICONTROL Select File]**. Wählen Sie die CSV-Datei mit den Metadaten aus.
1. Geben Sie die folgenden Parameter an:

   | Metadaten-Importparameter | Beschreibung |
   |:---|:---|
   | [!UICONTROL Batch-Größe] | Anzahl der Assets in einem Batch, für die Metadaten importiert werden sollen. Der Standardwert ist 50. Der Wert darf maximal 100 betragen. |
   | [!UICONTROL Feldtrennzeichen] | Default value is `,` (a comma). Sie können jedoch ein beliebiges anderes Zeichen eingeben. |
   | [!UICONTROL Mehrfachtrennzeichen] | Trennzeichen für Metadatenwerte. Der Standardwert ist `|`. |
   | [!UICONTROL Workflows starten] | Lautet standardmäßig „False“. When set to `true` and default Launcher settings are in effect for the DAM Metadata WriteBack Workflow (that writes metadata to the binary XMP data). Die Aktivierung von Start-Arbeitsabläufen verlangsamt das System. |
   | [!UICONTROL Asset-Pfad-Spaltenname] | Definiert den Namen der Spalte in der CSV-Datei, die die Assets enthält. |

1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Importieren]**. Nachdem die Metadaten importiert wurden, wird eine Benachrichtigung an Ihren Benachrichtigungs-Posteingang gesendet. Navigieren Sie zur Asset-Eigenschaftsseite und überprüfen Sie, ob die Metadatenwerte richtig in die entsprechenden Assets importiert wurden.

## Metadaten exportieren {#export-metadata}

Sie können Metadaten für mehrere Assets in ein CSV-Format exportieren. Die Metadaten werden asynchron exportiert, sodass der Export die Systemleistung nicht beeinträchtigt. To export metadata, AEM traverses through the properties of the asset node `jcr:content/metadata` and its child nodes and exports the metadata properties in a CSV file.

Einige Anwendungsfälle für den Massenexport von Metadaten:

* Importieren Sie die Metadaten in ein Drittanbietersystem, wenn Sie Assets migrieren.
* Geben Sie Asset-Metadaten für ein breiteres Projektteam frei.
* Testen oder prüfen Sie die Metadaten auf Ihre Konformität.
* Externalisieren Sie die Metadaten für eine separate Lokalisierung.

1. Wählen Sie einen Asset-Ordner aus, der Assets enthält, für die Sie Metadaten exportieren möchten. Wählen Sie in der Symbolleiste **[!UICONTROL Metadaten exportieren]** aus.
1. Geben Sie im Dialogfeld „Metadatenexport“ einen Namen für die CSV-Datei an. Um Metadaten von Assets in Unterordnern zu exportieren, wählen Sie **[!UICONTROL Assets in Unterordnern einschließen]**.

   ![Benutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in eine](assets/export_metadata_page.png "folderBenutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in einem Ordner")

1. Wählen Sie die gewünschten Optionen aus. Geben Sie einen Dateinamen und ggf. ein Datum an.

1. Geben Sie im Feld **[!UICONTROL Zu exportierende Eigenschaften]** an, ob Sie alle oder nur bestimmte Eigenschaften exportieren wollen. Wenn Sie für den Export „Selektive Eigenschaften“ auswählen, fügen Sie die gewünschten Eigenschaften hinzu.

1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Exportieren]**. Sie erhalten eine Meldung, die bestätigt, dass die Metadaten exportiert wurden. Schließen Sie die Meldung.
1. Öffnen Sie die Posteingangsbenachrichtigung für den Exportauftrag. Wählen Sie den Auftrag aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Öffnen]**. Um die CSV-Datei mit den Metadaten herunterzuladen, tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL CSV-Download]**. Klicken Sie auf **[!UICONTROL Schließen]**.

   ![Dialogfeld zum Herunterladen der CSV-Datei mit Metadaten, die in großen Mengen exportiert wurden](assets/csv_download.png)
   *Abbildung: Dialogfeld zum Herunterladen der CSV-Datei, die Metadaten enthält, die als Massendatei exportiert wurden*

>[!MORELIKETHIS]
>
>* [Metadaten-Import und -Export in AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html)

