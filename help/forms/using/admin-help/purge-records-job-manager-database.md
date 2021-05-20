---
title: Job Manager-Datenbank um Aufzeichnungen bereinigen
seo-title: Job Manager-Datenbank um Aufzeichnungen bereinigen
description: Große Prozessdaten können zu niedrigerer AEM-Forms-Leistung führen. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn die Aufzeichnungen nicht mehr gebraucht werden.
seo-description: Große Prozessdaten können zu niedrigerer AEM-Forms-Leistung führen. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn die Aufzeichnungen nicht mehr gebraucht werden.
uuid: cf214498-36e9-4dcc-b4d4-e7c46f80dbab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 69a406f2-4fa8-40bb-b671-7b0f5b6a2c4c
exl-id: 5279f6c3-5954-472c-9ea0-18e8a7ec860e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 100%

---

# Job Manager-Datenbank um Aufzeichnungen bereinigen {#purge-records-from-the-job-manager-database}

Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur Belegung von unnötigem Speicherplatz führt. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn die Aufzeichnungen nicht mehr gebraucht werden.

Sie können Administration Console verwenden, um eine einmalige Bereinigung von veralteten Datensätzen auszuführen oder regelmäßige automatische Bereinigungen zu planen. Weitere Methoden zum Bereinigen veralteter Aufzeichnungen werden unter [Prozessdaten bereinigen](/help/forms/using/admin-help/purging-process-data.md#purging-process-data) erläutert.

**Auf die Seite „Zeitplaner für die Auftragsbereinigung“ zugreifen**

1. Klicken Sie in Administration Console in der rechten oberen Ecke der Seite auf „Health Monitor“.
1. Klicken Sie auf die Registerkarte „Zeitplaner für die Auftragsbereinigung“.

Weitere Informationen zu aktuell geplanten Bereinigungen werden im Informationsfeld des Zeitplaners für die Auftragsbereinigung angezeigt.

>[!NOTE]
>
>Durch Klicken auf die Option „Zeitplaner anhalten“ werden alle für die Zukunft geplanten Bereinigungen beendet. Bereinigungsaufträge, die gerade ausgeführt werden, werden jedoch nicht beendet.

**Eine einmalige Bereinigung planen**

1. Wählen Sie „Nur einmal“ aus.
1. Geben Sie im Bereich „Abgeschlossene Aufzeichnungen bereinigen“ die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gelten soll und bereinigt werden kann.

   >[!NOTE]
   >
   >Aufzeichnungen, die im Zusammenhang mit nicht ausgeführten Prozessen erstellt wurden, werden nicht bereinigt, auch wenn sie älter als der angegebene Zeitraum sind.

1. Geben Sie an, wann die Bereinigung ausgeführt werden soll. Aktivieren Sie das Kontrollkästchen „Aktuelles Datum und Zeit verwenden“ oder deaktivieren Sie es und klicken Sie auf die Kalender- oder Uhrsymbole, um das Datum und die Uhrzeit anzugeben, wann die Bereinigung ausgeführt werden soll.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Uhrzeit angeben, die in der Vergangenheit liegen, wird die Bereinigung sofort ausgeführt, sobald Sie auf „Zeitplaner starten“ klicken.

1. Klicken Sie auf „Zeitplaner starten“. Alle vorherigen geplanten Einstellungen des Zeitplaners werden durch die neuen Einstellungen ersetzt.

**Einen automatischen Bereinigungszeitplan konfigurieren**

1. Wählen Sie die Option „Wiederholen alle“ aus und geben Sie die Anzahl der Tage oder Wochen an, die zwischen den Bereinigungsvorgängen liegen sollen.
1. Geben Sie im Bereich „Abgeschlossene Aufzeichnungen bereinigen“ die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gelten soll und bereinigt werden kann. Sie können den Wert nicht auf `0`   einstellen.

   >[!NOTE]
   >
   >Aufzeichnungen, die im Zusammenhang mit nicht ausgeführten Prozessen erstellt wurden, werden nicht bereinigt, auch wenn sie älter als der angegebene Zeitraum sind.

1. Geben Sie an, wann die Bereinigung beginnen soll. Aktivieren Sie das Kontrollkästchen „Aktuelles Datum und Zeit verwenden“ oder deaktivieren Sie es und klicken Sie auf die Kalender- oder Uhrsymbole, um das Datum und die Uhrzeit anzugeben, wann die Bereinigung ausgeführt werden soll.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum festlegen, das in der Vergangenheit liegt, wird anhand des angegebenen Datums von AEM Forms das nächste logische Startdatum errechnet. Wenn Sie beispielsweise planen, dass die Auftragsbereinigung ab dem 7. April wöchentlich ausgeführt werden soll und heute der 9. April ist, wird die erste Bereinigung am 14. April ausgeführt.

1. Klicken Sie auf „Zeitplaner starten“. Alle vorherigen geplanten Einstellungen des Zeitplaners werden durch die neuen Einstellungen ersetzt.
