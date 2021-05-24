---
title: Asynchrone Aufträge
description: Adobe Experience Manager optimiert die Leistung durch asynchrone Ausführung einiger ressourcenintensiver Aufgaben.
exl-id: 4af1bcfe-9f2e-44a4-8666-881f2dccc3bc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 98%

---

# Asynchrone Vorgänge {#asynchronous-operations}

Um negative Auswirkungen auf die Leistung einzuschränken, werden bestimmte lang laufende und ressourcenintensive Vorgänge in Adobe Experience Manager asynchron verarbeitet. Die asynchrone Verarbeitung umfasst den Aufbau einer Warteschlange mit mehreren Aufträgen und schließlich deren serielle Ausführung gemäß der Verfügbarkeit von Systemressourcen.

Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets
* Verschieben vieler Assets oder Assets mit vielen Verweisen
* Exportieren/Importieren von Asset-Metadaten in großen Mengen
* Abrufen von Assets, die über dem festgelegten Schwellenwert liegen, aus einer Remote-AEM-Bereitstellung
* Verschieben von Seiten
* Ausrollen von Live Copies

Sie können den Status asynchroner Aufträge über das Dashboard **[!UICONTROL Status asynchroner Aufträge]** unter **Globale Navigation** > **Tools** > **Vorgänge** > **Aufträge** anzeigen.

>[!NOTE]
>
>Standardmäßig werden asynchrone Aufträge parallel ausgeführt. Wenn die Anzahl der CPU-Kerne *`n`* ist, können standardmäßig *`n/2`* Aufträge parallel ausgeführt werden. Um benutzerdefinierte Einstellungen für die Auftragswarteschlange zu verwenden, ändern Sie die **[!UICONTROL Standardwarteschlangenkonfiguration für asynchrone Vorgänge]** und die **Konfiguration für Seitenverschiebung und Rollout von asynchronen Vorgängen** in der Web-Konsole.
>
>Weitere Informationen finden Sie unter [Warteschlangenkonfigurationen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Überwachen des Status asynchroner Vorgänge {#monitor-the-status-of-asynchronous-operations}

Wenn AEM einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung in Ihrem [Posteingang](/help/sites-authoring/inbox.md) und per E-Mail (falls aktiviert).

Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Status asynchroner Aufträge]**.

1. Klicken Sie in der Benutzeroberfläche von Experience Manager auf **[!UICONTROL Vorgänge]** > **[!UICONTROL Aufträge]**.

1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Status von asynchronen Aufträgen]**.

   ![Status und Details asynchroner Vorgänge](assets/async-operation-status.png)

   Den Fortschritt einzelner Vorgänge finden Sie als Wert in der Spalte **[!UICONTROL Status]**. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet

   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen

   * **[!UICONTROL Fehlschlag]** oder **[!UICONTROL Fehler]**: Der Vorgang konnte nicht bearbeitet werden.

   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant

1. Um einen aktiven Vorgang abzubrechen, wählen Sie ihn in der Liste aus und tippen/klicken Sie auf das Symbol **[!UICONTROL Stopp]** in der Symbolleiste.

   ![Stoppsymbol](assets/async-stop-icon.png)

1. Um zusätzliche Details anzuzeigen, beispielsweise eine Beschreibung und Protokolle, wählen Sie den Vorgang aus und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Öffnen]**.

   ![Öffnen-Symbol](assets/async-open-icon.png)

   Die Detailseite für den Auftrag wird angezeigt.

   ![Auftragsdetails](assets/async-job-details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. Um die Details als CSV-Datei herunterzuladen, tippen/klicken Sie auf **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Sie können einen Auftrag nicht löschen, wenn er **Aktiv** ist oder sich **In der Warteschlange** befindet.

## Bereinigen von abgeschlossenen Aufträgen {#purging-completed-jobs}

AEM führt jeden Tag um 01:00 Uhr einen Bereinigungsauftrag aus, um abgeschlossene asynchrone Aufträge zu löschen, die älter als einen Tag sind.

Sie können den Zeitplan für den Bereinigungsauftrag bearbeiten. Außerdem können Sie anpassen, wie lange die Details zu abgeschlossenen Aufträgen gespeichert werden sollen, bevor sie gelöscht werden. Darüber hinaus können Sie die maximale Anzahl abgeschlossener Aufträge konfigurieren, deren Details zu einem beliebigen Zeitpunkt gespeichert werden.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie den Auftrag **[!UICONTROL Adobe Granite – Geplante Bereinigung asynchroner Aufträge]**.
1. Geben Sie Folgendes an:
   * Den Schwellenwert der Tage, nach denen abgeschlossene Aufträge gelöscht werden.
   * Die maximale Anzahl von Aufträgen, für die Details im Verlauf beibehalten werden.
   * Der Cron-Ausdruck für den Zeitpunkt, an dem die Bereinigung laufen soll.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufträge](assets/async-purge-job.png)

1. Speichern Sie die Änderungen.

## Konfigurieren der asynchronen Verarbeitung {#configuring-asynchronous-processing}

Sie können die Schwellenwerte für Assets, Seiten oder Verweise konfigurieren, damit AEM einen bestimmten Vorgang asynchron verarbeitet, und E-Mail-Benachrichtigungen für den Zeitpunkt der erfolgten Auftragsverarbeitung ein- oder ausschalten.

### Konfigurieren von asynchronen Vorgängen zum Löschen von Assets {#configuring-synchronous-delete-operations}

Wenn die Anzahl der Assets oder der zu löschenden Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron ausgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die **[!UICONTROL Konfiguration der Standardwarteschlange für asynchrone Vorgänge.]**
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets]** den Schwellenwert für die Anzahl von Assets/Ordnern für die asynchrone Verarbeitung von Löschvorgängen an.

   ![Schwellenwert zum Löschen von Assets](assets/async-delete-threshold.png)

1. Aktivieren Sie die Option **E-Mail-Benachrichtigung aktivieren**, um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. Z. B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Konfigurieren von asynchronen Vorgängen zum Verschieben von Assets {#configuring-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Anlagen/Ordner oder Referenzen den Schwellenwert übersteigt, wird der Verschiebevorgang asynchron ausgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die **[!UICONTROL Konfiguration der Verarbeitung asynchroner Verschiebeaufträge]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets/Verweise]** den Schwellenwert für Assets/Ordner oder Verweise für die asynchrone Verarbeitung von Verschiebevorgängen fest.

   ![Schwellenwert für das Verschieben von Assets](assets/async-move-threshold.png)

1. Aktivieren Sie die Option **E-Mail-Benachrichtigung aktivieren**, um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. Z. B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Konfigurieren von asynchronen Seitenverschiebungsvorgängen {#configuring-asynchronous-page-move-operations}

Wenn die Anzahl der Verweise auf die zu verschiebende(n) Seite(n) den Schwellenwert überschreitet, wird der Verschiebungsvorgang asynchron durchgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die **[!UICONTROL Konfiguration der Verarbeitung asynchroner Seitenverschiebeaufträge]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Verweise]** den Schwellenwert für Verweise für asynchrone Verarbeitungen von Seitenverschiebevorgängen fest.

   ![Schwellenwert für Seitenverschiebungen](assets/async-page-move.png)

1. Aktivieren Sie die Option **E-Mail-Benachrichtigung aktivieren**, um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. Z. B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Konfigurieren asynchroner MSM-Vorgänge {#configuring-asynchronous-msm-operations}

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die **[!UICONTROL Konfiguration der Verarbeitung asynchroner Seitenverschiebeaufträge]**.
1. Aktivieren Sie die Option **E-Mail-Benachrichtigung aktivieren**, um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. Z. B. Erfolg, fehlgeschlagen.

   ![Konfigurieren eines MSM](assets/async-msm.png)

1. Speichern Sie die Änderungen.

>[!MORELIKETHIS]
>
>* [Erstellen und Organisieren von Seiten](/help/sites-authoring/managing-pages.md)
* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [E-Mail in Experience Manager konfigurieren](/help/sites-administering/notification.md).
* [Importieren von Asset-Metadaten](/help/assets/metadata.md#import-metadata).
* [Exportieren von Asset-Metadaten](/help/assets/metadata.md#export-metadata).
* [Verwenden Sie verbundene Assets, um DAM-Assets aus Remote-Implementierungen freizugeben](/help/assets/use-assets-across-connected-assets-instances.md).

