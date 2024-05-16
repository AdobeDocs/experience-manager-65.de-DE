---
title: Anzeigen von Statistiken mit Bezug auf Work Manager
description: Auf der Registerkarte „Work Manager“ werden Statistiken angezeigt, die mit Work Manager-Elementen zusammenhängen.  Erfahren Sie, wie Sie die Arbeitselemente anzeigen und filtern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ce8f7257-bb9a-428d-b816-27b1d1632ee1
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1215'
ht-degree: 100%

---

# Anzeigen von Statistiken mit Bezug auf Work Manager {#view-statistics-related-to-work-manager}

Auf der Registerkarte „Work Manager“ werden Statistiken angezeigt, die mit Work Manager-Elementen zusammenhängen.  Diese Arbeitselemente weisen je nachdem, wo sie sich in ihrem Prozess befinden, unterschiedliche Status auf. (Siehe [Status (nur für Standard-, Workflow- oder Ereigniskategorien)](view-statistics-related-manager.md#status-for-default-workflow-or-events-categories-only).) Sie können die Informationen filtern, um nur eine Teilmenge der Elemente anzuzeigen, indem Sie die verschiedenen zur Verfügung stehenden Optionen verwenden (z. B. Status oder Kategorie). Sie können die entstehenden Arbeits- oder Auftragselemente (in aufsteigender oder absteigender Reihenfolge) sortieren, indem Sie auf einen der Spaltenüberschriften klicken.  Sie können die Arbeitselemente außerdem mithilfe der Vorgangswerkzeuge verwalten, die über der Liste der Arbeitselemente angezeigt werden.

## Filtern von Arbeitselementen {#filter-the-work-items}

1. Klicken Sie auf die Registerkarte „Work Manager“.
1. Wählen Sie die Kriterien für einen oder mehrere der folgenden Filter wie unten beschrieben aus, und klicken Sie dann auf „Los“.

### Kategorie {#category}

**Standard:** Alle Arbeitselemente, denen der Client beim Übermitteln keine Kategorie zugewiesen hat. Work Manager verwaltet diese Elemente, daher gehören die Status zu Work Manager.

**Job Manager:** Alle Aufträge, die zu Job Manager gehören. Job Manager verwaltet seine eigenen Aufträge und verfügt über seine eigenen Auftragsstatus.  Informationen hierzu finden Sie in den spezifischen, unten beschriebenen Auftragsstatus.

**Workflow:** Alle Arbeitselemente, die zur Workflow-Ausführung gehören. Workflow verwaltet keine eigenen Arbeitselemente, sondern verlässt sich auf Work Manager. Daher gehören die Status zu Work Manager.

**Ereignisse:** Alle Arbeitselemente, die zur Ereignisverwaltung gehören. Die Ereignisverwaltung verwaltet keine eigenen Arbeitselemente, sondern verlässt sich auf Work Manager. Daher gehören die Status zu Work Manager.

### Status (nur für Standard-, Workflow- oder Ereigniskategorien) {#status-for-default-workflow-or-events-categories-only}

**Alle anzeigen:** Zeigt alle aktuellen Arbeitselemente an.

**Geplant:** Zeigt alle Arbeitselemente an, die vom Anwendungsserver ausgeführt werden können, jedoch noch nicht gestartet wurden.

**Angehalten:** Zeigt alle geplanten Arbeitselemente an, die von der Client-Anwendung angehalten wurden. Diese Elemente können ausgeführt oder gelöscht werden. (Siehe Arbeitselemente oder Aufträge verwalten.)

**In Arbeit:** Zeigt alle Arbeitselemente an, die der Work Manager des Anwendungsservers ausgewählt hat und die entweder abgeschlossen werden oder fehlschlagen. Sie können für diese Arbeitselemente keine Vorgänge verwenden.

**Fertig:** Zeigt alle Arbeitselemente an, die erfolgreich ausgeführt wurden. Permanente Arbeitselemente verbleiben in diesem Status, und nicht permanente Elemente werden beim Beenden von Rückrufen an die Rückruf-Handler gelöscht. Zum Löschen dieser Elemente verwenden Sie den Vorgang „Elemente löschen“.  (Siehe Arbeitselemente oder Aufträge verwalten.)

**Fehlgeschlagen:** Zeigt alle Arbeitselemente an, die aufgrund eines Fehlers nicht erfolgreich beendet wurden. Diese Arbeitselemente können mehrmals durch Verwenden des Vorgangs „Elemente wiederholen“ wiederholt werden. (Siehe Arbeitselemente oder Aufträge verwalten.) Mithilfe der Fehlerverknüpfung in der Statuszeile können Sie auf Details über den Fehler zugreifen.

**Unbekannt:** Zeigt alle Arbeitselemente an, deren Status unbekannt ist.

### Status (nur für Job Manager-Kategorie) {#status-for-job-manager-category-only}

**Abgeschlossen** Zeigt alle Aufträge an, die erfolgreich ausgeführt wurden. Permanente Arbeitselemente verbleiben in diesem Status und nicht permanente Elemente werden beim Beenden von Rückrufen an die Rückruf-Handler gelöscht.

**Abschließen angefordert:** Zeigt Aufträge an, für die eine vollständige Anforderung ausgeführt wurde.

**Fehler angefordert:** Zeigt Aufträge an, für die eine Fehleranforderung ausgeführt wurde.

**Fehlgeschlagen:** Zeigt Aufträge an, die aufgrund eines Fehlers nicht erfolgreich beendet wurden. Mithilfe der Fehlerverknüpfung in der Statuszeile können Sie auf Details über den Fehler zugreifen.

**Beenden angefordert:** Zeigt Aufträge an, für die eine Anforderung zum Beenden ausgeführt wurde.

**Beendet:** Zeigt Aufträge an, die beendet wurden, ohne abgeschlossen worden zu sein.

**Aussetzen angefordert:** Zeigt Aufträge an, für die eine Anforderung zum Aussetzen ausgeführt wurde.

**Ausgesetz:** Zeigt Aufträge an, die ausgesetzt wurden.

**Wartet auf Wiederaufnahme** Zeigt Aufträge an, für die eine Anforderung zur Wiederaufnahme gestellt wurde.

**In die Warteschlange gestellt** Zeigt Aufträge an, die sich in der Warteschlange befinden.

**Betrieb:** Zeigt Aufträge an, die gerade ausgeführt werden.

### Server-Name {#server-name}

Nur für Cluster-Server: Wählen Sie den Namen des Knotens aus, der die Arbeitselemente oder Auftragselemente anzeigen soll, die nur auf diesem Server erstellt wurden.  Wenn die Option „Alle anzeigen“ ausgewählt ist, werden alle Arbeitselemente für alle Knoten im Cluster angezeigt.

### Erstellungszeit {#create-time}

Wählen Sie in diesem Filter eine Option aus, um nur die Arbeitselemente anzuzeigen, die innerhalb des von Ihnen ausgewählten Zeitrahmens erstellt wurden. Wenn Sie beispielsweise „1 Tag“ auswählen, werden alle Arbeitselemente angezeigt, die innerhalb von 24 Stunden vor der im Filter „Vor“ festgelegten Zeit erstellt wurden.

### Vor {#prior-to}

Legt das Datum und die Zeit fest, die der Filter „Erstellungszeit“ als Enddatum verwendet.  Lassen Sie die Option „Aktuelles Datum/Zeit verwenden“ ausgewählt, um vom aktuellen Datum und Uhrzeit aus nach hinten zu filtern. Sie können die Auswahl für die Option auch aufheben und die entsprechenden Werte eingeben.  Klicken Sie entweder auf die Kalender- oder Uhrsymbole, um Werte mithilfe dieser Tools auszuwählen.

Wenn Sie beispielsweise „Erstellungszeit = 1 Tag“ und „Vor = Aktuelles Datum/Zeit verwenden“ auswählen, werden alle Arbeitselemente zurückgegeben, die innerhalb der letzten 24 Stunden erstellt wurden.

>[!NOTE]
>
>Bei Oracle-Datenbankbereitstellungen funktionieren die Datumsbereichsfilter (d. h. die Einstellungen „Erstellungszeit“ und „Vor“) nicht zuverlässig. Verwenden Sie einen anderen Filter, um die Arbeitselemente abzurufen.

## Informationen zur Oberfläche der Registerkarte „Work Manager“ {#about-the-work-manager-tab-interface}

Wenn Sie eine Work Manager-Abfrage oder einen Vorgang an einem Arbeitselement oder Auftrag ausführen, wird über der Liste eine Meldung angezeigt.  Diese bietet Ihnen eine Rückmeldung über die von Ihnen initiierte Aktion und in einigen Fällen eine Verknüpfung „Mehr Informationen“, die weitere Details zur Verfügung stellt. Wenn beispielsweise der von Ihnen initiierte Vorgang fehlgeschlagen ist, gibt die Meldung Informationen darüber an und stellt eine Verknüpfung zum Abrufen von Details über den Fehler bereit.

Wenn Sie auf „Weitere Informationen“ klicken, zeigt das Dialogfeld „Vorgangsdetails“ eine Liste der Arbeitselemente oder Aufträge an, die während des Vorgangs ausgewählt wurden. Sie können auf jedes Listenelement klicken, um die Fehlerdetails unten im Dialogfeld anzuzeigen.

### Verwalten der Arbeitselemente oder Aufträge {#manage-the-work-items-or-jobs}

1. Verwenden Sie die unten beschriebenen Vorgangs-Tools, um die Arbeitselemente oder Aufträge in der Liste zu verwalten.

   >[!NOTE]
   >
   >Vorgänge sind je nach dem Status des Elements verfügbar.

   **Elemente löschen:** Löscht die ausgewählten Arbeitselemente oder Aufträge.

   **Elemente anhalten:** Hält die ausgewählten Arbeitselemente oder Aufträge an.

   **Elemente fortsetzen:** Setzt die ausgewählten angehaltenen Arbeitselemente oder Aufträge fort.

   **Elemente wiederholen:** Versucht, die ausgewählten Arbeitselemente oder Aufträge von ihrem aktuellen Zustand an erneut auszuführen.

   Sie können überprüfen, ob ein Vorgang erfolgreich war, indem Sie über der Liste auf „Weitere Informationen“ klicken.  Es wird ein Dialogfeld angezeigt, das die ausgewählten Arbeitselemente oder Aufträge sowie ihre Status enthält.

## Weitere Informationen über die Status der Arbeitselemente {#additional-information-about-work-item-statuses}

Ein typischer Statusübergang für ein Arbeitselement ist „Neu“ > „Geplant“ > „Wird ausgeführt“ > „Abgeschlossen“ oder „Fehler“.

Der Status „Angehalten“ unterbricht diesen normalen Fluss.  Diese Unterbrechung kann entweder von der Client-Anwendung oder von Systemadmins initiiert werden (z. B. zu Wartungs- oder Aktualisierungszwecken).  Sie können diese Aktion umkehren, indem Sie mithilfe des Vorgangs „Fortsetzen“ das Arbeitselement zurück in den Status „Geplant“ versetzen.

Ein Arbeitselement im Status „Geplant“ befindet sich in der Warteschlange für eine Ausführung, die noch nicht begonnen hat. Diese Elemente können angehalten oder gelöscht werden, oder sie werden in den Status „Wird ausgeführt“ versetzt, wenn der Work Manager sie aus der Warteschlange nimmt. Arbeitselemente, die ausgeführt werden, können nicht bearbeitet werden.  Sie werden entweder abgeschlossen oder es tritt ein Fehler auf.

Der Status „Fehlgeschlagen“ ist das Ergebnis eines Fehlers, der bei der Ausführung des Arbeitselements aufgetreten ist.  Wenn Sie vermuten, dass die Fehler durch die Umstände bedingt sind (aufgrund des Kontextes zum Zeitpunkt der Ausführung), können Sie versuchen, die Ausführung erneut durchzuführen, indem Sie das Arbeitselement zurück in die Warteschlange versetzen. Es ist nur eine begrenzte Anzahl von Neuversuchen zulässig.
