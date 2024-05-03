---
title: Bereinigen von Datensätzen aus der Job Manager-Datenbank
description: Große Prozessdaten können zu niedrigerer AEM Forms-Leistung führen. Es ist empfehlenswert, Prozessdaten zu bereinigen, wenn die Einträge nicht mehr benötigt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 5279f6c3-5954-472c-9ea0-18e8a7ec860e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 100%

---

# Bereinigen von Datensätzen aus der Job Manager-Datenbank {#purge-records-from-the-job-manager-database}

Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur unnötigen Belegung von Speicherplatz führt.  Es ist empfehlenswert, Prozessdaten zu bereinigen, wenn die Einträge nicht mehr benötigt werden. 

Sie können die Administrationskonsole verwenden, um eine einmalige Bereinigung von veralteten Einträgen auszuführen oder regelmäßige automatische Bereinigungen zu planen.  Weitere Methoden zum Bereinigen veralteter Einträge werden unter [Bereinigen von Prozessdaten](/help/forms/using/admin-help/purging-process-data.md#purging-process-data) erläutert.

**Zugreifen auf die Seite „Zeitplaner für die Auftragsbereinigung“**

1. Klicken Sie in der Administrationskonsole in der rechten oberen Ecke der Seite auf „Health Monitor“.
1. Klicken Sie auf die Registerkarte „Zeitplaner für die Auftragsbereinigung“.

Weitere Informationen zu aktuell geplanten Bereinigungen werden im Informationsfeld des Zeitplaners für die Auftragsbereinigung angezeigt.

>[!NOTE]
>
>Durch Klicken auf die Option „Zeitplaner anhalten“ werden alle für die Zukunft geplanten Bereinigungen gestoppt. Bereinigungsaufträge, die gerade ausgeführt werden, werden jedoch nicht beendet.

**Planen einer einmaligen Bereinigung**

1. Wählen Sie „Nur einmal“ aus.
1. Geben Sie im Bereich „Abgeschlossene Aufzeichnungen bereinigen“ die Anzahl der Tage oder Wochen an, nach denen ein Eintrag als veraltet gelten soll und bereinigt werden kann.

   >[!NOTE]
   >
   >Einträge, die im Zusammenhang mit nicht ausgeführten Prozessen erstellt wurden, werden nicht bereinigt, auch wenn sie älter als der angegebene Zeitraum sind.

1. Geben Sie an, wann die Bereinigung ausgeführt werden soll.  Aktivieren Sie das Kontrollkästchen „Aktuelles Datum und Zeit verwenden“ oder deaktivieren Sie es und klicken Sie auf die Kalender- bzw. Uhrsymbole, um das Datum und die Uhrzeit anzugeben, wann die Bereinigung ausgeführt werden soll.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Uhrzeit angeben, die in der Vergangenheit liegen, wird die Bereinigung sofort ausgeführt, sobald Sie auf „Zeitplaner starten“ klicken.

1. Klicken Sie auf „Zeitplaner starten“.  Alle vorherigen geplanten Einstellungen des Zeitplaners werden durch die neuen Einstellungen ersetzt.

**Konfigurieren eines automatischen Bereinigungszeitplans**

1. Wählen Sie die Option „Wiederholen alle“ aus und geben Sie die Anzahl der Tage oder Wochen an, die zwischen den Bereinigungsvorgängen liegen sollen.
1. Geben Sie im Bereich „Abgeschlossene Aufzeichnungen bereinigen“ die Anzahl der Tage oder Wochen an, nach denen ein Eintrag als veraltet gelten soll und bereinigt werden kann. Sie können den Wert nicht auf `0` einstellen.

   >[!NOTE]
   >
   >Einträge, die im Zusammenhang mit nicht ausgeführten Prozessen erstellt wurden, werden nicht bereinigt, auch wenn sie älter als der angegebene Zeitraum sind.

1. Geben Sie an, wann die Bereinigungen beginnen sollen.  Aktivieren Sie das Kontrollkästchen „Aktuelles Datum und Zeit verwenden“ oder deaktivieren Sie es und klicken Sie auf die Kalender- bzw. Uhrsymbole, um das Datum und die Uhrzeit anzugeben, wann die Bereinigung ausgeführt werden soll.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Startzeit angeben, die in der Vergangenheit liegen, berechnet AEM Formulare das logische nächste Startdatum basierend auf dem angegebenen Datum. Wenn Sie beispielsweise planen, dass die Auftragsbereinigung ab dem 7. April wöchentlich ausgeführt werden soll und heute der 9. April ist, wird die erste Bereinigung am 14. April ausgeführt.

1. Klicken Sie auf „Zeitplaner starten“.  Alle vorherigen geplanten Einstellungen des Zeitplaners werden durch die neuen Einstellungen ersetzt.
