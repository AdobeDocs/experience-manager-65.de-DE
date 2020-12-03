---
title: Berichte zur Verwendung und Freigabe von Assets
description: Berichte zu Ihren Assets in [!DNL Adobe Experience Manager Assets] mit Informationen zur Nutzung, Aktivität und Freigabe Ihrer digitalen Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6016cefa9456d8f142347ff197b61b1614d55ab9
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 43%

---


# Asset-Berichte {#asset-reports}

Mit Asset Berichte können Sie das Dienstprogramm Ihrer [!DNL Adobe Experience Manager Assets]-Bereitstellung bewerten. Mit [!DNL Assets] können Sie verschiedene Berichte für Ihre digitalen Assets erstellen. Die Berichte bieten hilfreiche Informationen über die Nutzung Ihres Systems, über die Art und Weise, wie Benutzer mit Assets interagieren und welche Assets heruntergeladen und freigegeben werden.

Verwenden Sie die Informationen in den Berichten, um wichtige Erfolgsmetriken abzuleiten, um die Akzeptanz von [!DNL Assets] in Ihrem Unternehmen und nach Kunden zu messen.

Das [!DNL Assets]-Berichte-Framework verwendet [!DNL Sling]-Aufträge, um Berichtanforderungen asynchron in einer geordneten Weise zu verarbeiten. Es ist für große Repositorys skalierbar. Die asynchrone Berichtsverarbeitung steigert die Effizienz und Geschwindigkeit der Berichtsgenerierung.

Die Berichtsverwaltungsoberfläche ist intuitiv und umfasst detaillierte Optionen und Steuerelemente für den Zugriff auf archivierte Berichte und das Anzeigen des Ausführungsstatus von Berichten („Erfolg“, „Fehlgeschlagen“ und „In Warteschlange“).

Wenn ein Bericht generiert wird, werden Sie mit einer E-Mail (optional) und einer Benachrichtigung im Posteingang benachrichtigt. Sie können einen Bericht auf der Berichtslistenseite anzeigen, herunterladen oder löschen. Dort werden alle zuvor generierten Berichte angezeigt.

## Voraussetzung {#prerequisite-for-reporting}

Gehen Sie wie folgt vor, um Berichte zu erstellen:

* Aktivieren Sie den Dienst [!UICONTROL Day CQ DAM Ereignis Recorder] unter **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web Console]**.
* Wählen Sie die Aktivitäten oder Ereignis aus, auf denen Sie Berichte haben möchten. Um beispielsweise einen Bericht zu heruntergeladenen Assets zu erstellen, wählen Sie [!UICONTROL Heruntergeladenes Asset (HERUNTERGELADEN)].

![Asset-Berichte in der Web-Konsole aktivieren](assets/reports-config-day-cq-dam-event-recorder.png)

## Erstellen von Berichten {#generate-reports}

[!DNL Experience Manager Assets] erstellt die folgenden Standardberichte für Sie:

* Hochladen
* Download
* Ablauf
* Änderung
* Veröffentlichen
* [!DNL Brand Portal] publish
* Festplattenauslastung
* Dateien
* Link-Freigabe

[!DNL Adobe Experience Manager] Administratoren können diese Berichte ganz einfach für Ihre Implementierung erstellen und anpassen. Um einen Bericht zu erstellen, müssen Administratoren folgende Schritte durchführen:

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.

   ![Tools-Seite zum Navigieren im Assets-Bericht](assets/AssetsReportNavigation.png)

1. Klicken Sie auf der Seite [!UICONTROL Asset-Berichte] in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Bericht erstellen]** den zu erstellenden Bericht aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Berichttyp auswählen](assets/choose_report.png)

   >[!NOTE]
   >
   >Standardmäßig sind Inhaltsfragmente und Linkfreigaben im Bericht &quot;Asset [!UICONTROL Download]&quot;enthalten. Wählen Sie die passende Option aus, um einen Bericht zu Linkfreigaben zu erstellen oder Inhaltsfragmente aus dem Downloadbericht auszuschließen.

   >[!NOTE]
   >
   >Der Bericht [!UICONTROL Download] zeigt nur Details zu den Assets an, die heruntergeladen werden, nachdem sie einzeln ausgewählt wurden oder mit der Schnellaktion heruntergeladen wurden. Es enthält jedoch keine Details zu den Assets, die sich in einem heruntergeladenen Ordner befinden.

1. Konfigurieren Sie die Berichtdetails wie Titel, Beschreibung, Miniaturansicht sowie den Ordnerpfad im CRX-Repository, der den Speicherort des Berichts angibt. Der Ordnerpfad ist standardmäßig `/content/dam`. Sie können auch einen anderen Pfad festlegen.

   ![Seite zum Hinzufügen von Berichtsdetails](assets/report_configuration.png)

   Wählen Sie den Datumsbereich für Ihren Bericht aus.

   Sie können den Bericht wahlweise sofort oder zu einem zukünftigen Zeitpunkt generieren lassen.

   >[!NOTE]
   >
   >Wenn Sie den Bericht zu einem späteren Zeitpunkt planen, stellen Sie sicher, dass Sie das Datum und die Uhrzeit in den Feldern Datum und Uhrzeit angeben. Wenn Sie keinen Wert angeben, behandelt die Berichterstattungs-Engine den Bericht als einen sofort zu erstellenden Bericht.

   Die Konfigurationsfelder unterscheiden sich möglicherweise basierend auf der Art des erstellten Berichts. Beispielsweise bietet der Bericht zur **[!UICONTROL Festplattenauslastung]** Optionen, um bei der Berechnung des von Assets genutzten Festplattenvolumens Asset-Ausgabeformate miteinzubeziehen. Sie können Assets zur Berechnung der Speichernutzung in Unterordnern ein- oder ausschließen.

   >[!NOTE]
   >
   >Der Bericht zur **[!UICONTROL Festplattenauslastung]** umfasst keine Felder für den Datumsbereich, da er nur den aktuellen Speicherbedarf angibt.

   ![Detailseite des Berichts &quot;Festplattennutzung&quot;](assets/disk_usage_configuration.png)

   Wenn Sie den Bericht **[!UICONTROL Dateien]** erstellen, können Sie Unterordner ein-/ausschließen. Bei diesem Bericht können Sie jedoch keine Asset-Ausgabeformate miteinbeziehen.

   ![Detailseite des Dateiberichts](assets/files_report.png)

   Der Bericht **[!UICONTROL Linkfreigabe]** zeigt URLs zu Assets an, die von [!DNL Assets] aus für externe Benutzer freigegeben werden. Er enthält E-Mail-IDs des Benutzers, der die Assets freigegeben hat, E-Mail-IDs von Benutzern, für die die Assets freigegeben wurden, Freigabedatum und Ablaufdatum des Links. Die Spalten können nicht angepasst werden.

   Der Bericht **[!UICONTROL Linkfreigabe]** enthält keine Optionen für Unterordner und Darstellungen, da er lediglich die freigegebenen URLs veröffentlicht, die unter `/var/dam/share` angezeigt werden.

   ![Detailseite des Berichts &quot;Linkfreigabe&quot;](assets/link_share.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Weiter]**.

1. Auf der Seite **[!UICONTROL Spalten konfigurieren]** sind einige Spalten standardmäßig für den Bericht ausgewählt. Sie können weitere Spalten auswählen. Heben Sie die Auswahl einer Spalte auf, wenn sie nicht im Bericht angezeigt werden soll.

   ![Auswählen oder Aufheben der Auswahl von Berichtsspalten](assets/configure_columns.png)

   Um einen benutzerdefinierten Spaltennamen oder Eigenschaftenpfad anzuzeigen, konfigurieren Sie die Eigenschaften für die Asset-Binärdatei unter dem Knoten `jcr:content` in CRX. Alternativ können Sie sie über die Auswahl für den Eigenschaftspfad hinzufügen.

   ![Auswählen oder Aufheben der Auswahl von Berichtsspalten](assets/custom_columns.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**. Eine Meldung benachrichtigt Sie darüber, dass die Berichtserstellung startet.
1. Auf der Seite [!UICONTROL Asset-Berichte] basiert der Berichtgenerierungsstatus auf dem aktuellen Status des Berichtsauftrags, z. B. [!UICONTROL Erfolg], [!UICONTROL Fehlgeschlagen], [!UICONTROL Warteschlange] oder [!UICONTROL Eingeplant]. Derselbe Status wird auch im Benachrichtigungsfeld angezeigt.Klicken Sie zur Ansicht der Berichtsseite auf den Link Bericht. Alternativ können Sie den Bericht auswählen und in der Symbolleiste auf **[!UICONTROL Ansicht]** klicken.

   ![Ein generierter Bericht](assets/report_page.png)

   Klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**, um den Bericht im CSV-Format herunterzuladen.

## Hinzufügen benutzerdefinierter Spalten     {#add-custom-columns}

Sie können folgenden Berichten benutzerdefinierte Spalten hinzufügen, um weitere Daten für Ihre speziellen Anforderungen anzuzeigen:

* Hochladen
* Herunterladen
* Ablauf
* Änderung
* Veröffentlichen
* [!DNL Brand Portal] publish
* Dateien

Gehen Sie wie folgt vor, um benutzerspezifische Spalten zu diesen Berichten hinzuzufügen:

1. Klicken Sie in [!DNL Manager interface] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.
1. Klicken Sie auf der Seite [!UICONTROL Asset-Berichte] in der Symbolleiste auf **[!UICONTROL Erstellen]**.

1. Wählen Sie auf der Seite **[!UICONTROL Bericht erstellen]** den zu erstellenden Bericht aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Konfigurieren Sie Berichtsdetails wie Titel, Beschreibung, Miniaturansicht, Ordnerpfad und Datumsbereich wie gewünscht.

1. Um eine benutzerdefinierte Spalte anzuzeigen, geben Sie den Namen der Spalte unter **[!UICONTROL Benutzerdefinierte Spalten]** an.

   ![Name für benutzerdefinierte Berichtsspalte angeben](assets/custom_columns-1.png)

1. Fügen Sie den Eigenschaftspfad mit der Auswahl für den Eigenschaftspfad im `jcr:content`-Knoten in CRXDE hinzu. Alternativ können Sie den Pfad im Feld „Eigenschaftspfad“ eingeben.

   ![Ordnen Sie den Eigenschaftspfad Pfaden in jcr:content zu](assets/property_picker.png)

   Um weitere benutzerdefinierte Spalten hinzuzufügen, klicken Sie auf **[!UICONTROL Hinzufügen]** und wiederholen Sie die Schritte 5 und 6.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**. Eine Meldung benachrichtigt Sie darüber, dass die Berichtserstellung startet.

## Konfigurieren des Bereinigungsdiensts {#configure-purging-service}

Um nicht mehr benötigte Berichte zu entfernen, konfigurieren Sie den Bereinigungsdienst für DAM-Berichte über die Web-Konsole, um vorhandene Berichte basierend auf Menge und Alter zu bereinigen.

1. Greifen Sie über `https://[aem_server]:[port]/system/console/configMgr` auf die Web-Konsole (Configuration Manager) zu.
1. Öffnen Sie die Konfiguration für den **[!UICONTROL Bereinigungsdienst für DAM-Berichte]**.
1. Geben Sie die Häufigkeit (Zeitintervall) für den Bereinigungsdienst in das Feld `scheduler.expression.name` ein. Sie können auch die Schwellenwerte für das Alter und die Menge der Berichte konfigurieren.
1. Speichern Sie die Änderungen.

## Fehlerbehebung für Informationen, Tipps und Einschränkungen {#best-practices-and-limitations}

* Wenn einige Berichte oder Zahlen in den Berichten nicht oder erwartungsgemäß verfügbar sind, stellen Sie sicher, dass der Dienst [!UICONTROL CQ DAM Ereignis Recorder] aktiviert ist.

* Entfernen Sie die nicht mehr benötigten Berichte. Verwenden Sie die Konfigurationsoptionen im DAM Report Purge-Dienst, um die Kriterien zum Bereinigen von Berichten zu konfigurieren.

* Wenn der Bericht &quot;Festplattennutzung&quot;nicht generiert wird und Sie [!DNL Dynamic Media] verwenden, stellen Sie sicher, dass alle Assets ordnungsgemäß ausgeführt werden. Verarbeiten Sie zum Auflösen die Assets erneut und erstellen Sie dann den Bericht erneut.
