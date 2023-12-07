---
title: Bereinigen von Datensätzen aus der Job Manager-Datenbank
description: Große Prozessdaten können zu niedrigerer AEM Forms-Leistung führen. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn Datensätze nicht mehr benötigt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 5279f6c3-5954-472c-9ea0-18e8a7ec860e
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 6%

---

# Bereinigen von Datensätzen aus der Job Manager-Datenbank {#purge-records-from-the-job-manager-database}

Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn Datensätze nicht mehr benötigt werden.

Sie können Administration Console verwenden, um eine einmalige Bereinigung veralteter Datensätze durchzuführen oder regelmäßige automatische Bereinigungen zu planen. Weitere Methoden zum Bereinigen veralteter Datensätze finden Sie unter [Prozessdaten bereinigen](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**Auf die Seite &quot;Zeitplaner für die Auftragsbereinigung&quot;zugreifen**

1. Klicken Sie in Administration Console oben rechts auf der Seite auf Health Monitor .
1. Klicken Sie auf die Registerkarte Zeitplaner für die Auftragsbereinigung .

Informationen zu derzeit geplanten Bereinigungen werden im Feld Informationen zur Zeitplanung für die Auftragsbereinigung angezeigt.

>[!NOTE]
>
>Durch Klicken auf Planung stoppen werden alle in der Zukunft geplanten Bereinigungen beendet. Bereinigungsaufträge, die bereits ausgeführt werden, werden jedoch nicht beendet.

**Eine einmalige Bereinigung planen**

1. Wählen Sie Nur einmal aus.
1. Geben Sie im Bereich &quot;Filter für abgeschlossene Datensätze bereinigen&quot;die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gilt und zur Bereinigung bereit ist.

   >[!NOTE]
   >
   >Datensätze, die sich auf nicht abgeschlossene Prozesse beziehen, werden nicht bereinigt, auch wenn sie älter als das angegebene Alter sind.

1. Geben Sie an, wann die Bereinigung ausgeführt werden soll. Aktivieren Sie das Kontrollkästchen Aktuelles Datum und Uhrzeit verwenden oder deaktivieren Sie das Kontrollkästchen und klicken Sie auf die Kalender- und Uhrensymbole, um Datum und Uhrzeit der Bereinigung anzugeben.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Startzeit angeben, die in der Vergangenheit liegen, erfolgt die Bereinigung sofort, wenn Sie auf Planung starten klicken.

1. Klicken Sie auf Planung starten . Alle zuvor geplanten Planungseinstellungen werden durch die neuen Einstellungen ersetzt.

**Automatische Bereinigungsplanung konfigurieren**

1. Wählen Sie &quot;Wiederholen alle&quot;und geben Sie die Anzahl der Tage oder Wochen zwischen den Bereinigungen an.
1. Geben Sie im Bereich &quot;Filter für abgeschlossene Datensätze bereinigen&quot;die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gilt und zur Bereinigung bereit ist. Sie können den Wert nicht auf `0` einstellen.

   >[!NOTE]
   >
   >Datensätze, die sich auf nicht abgeschlossene Prozesse beziehen, werden nicht bereinigt, auch wenn sie älter als das angegebene Alter sind.

1. Geben Sie an, wann die Bereinigung beginnen soll. Aktivieren Sie das Kontrollkästchen Aktuelles Datum und Uhrzeit verwenden oder deaktivieren Sie das Kontrollkästchen und klicken Sie auf die Kalender- und Uhrensymbole, um Datum und Uhrzeit der Bereinigung anzugeben.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Startzeit angeben, die in der Vergangenheit liegen, berechnet AEM Formulare das logische nächste Startdatum basierend auf dem angegebenen Datum. Wenn Sie beispielsweise planen, dass die Auftragsbereinigung ab dem 7. April wöchentlich durchgeführt wird und jetzt der 9. April ist, wird die erste Bereinigung am 14. April durchgeführt.

1. Klicken Sie auf Planung starten . Alle zuvor geplanten Planungseinstellungen werden durch die neuen Einstellungen ersetzt.
