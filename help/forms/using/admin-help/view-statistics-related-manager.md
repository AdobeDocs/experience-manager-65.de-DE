---
title: Anzeigen von Statistiken mit Bezug auf Work Manager
seo-title: View statistics related to Work Manager
description: Auf der Registerkarte "Work Manager"werden Statistiken angezeigt, die sich auf Work Manager-Elemente beziehen. Erfahren Sie, wie Sie die Arbeitselemente anzeigen und filtern können.
seo-description: The Work Manager tab displays statistics that relate to Work Manager items. Learn how you can view and filter the work items.
uuid: c3a575c7-773d-477a-bc75-6cbcf8b836b8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8e1b2f7c-2609-474b-a1b2-fa820df74ae3
exl-id: ce8f7257-bb9a-428d-b816-27b1d1632ee1
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 34%

---

# Anzeigen von Statistiken mit Bezug auf Work Manager {#view-statistics-related-to-work-manager}

Auf der Registerkarte &quot;Work Manager&quot;werden Statistiken angezeigt, die sich auf Work Manager-Elemente beziehen. Diese Arbeitselemente weisen je nach Prozessort unterschiedliche Status auf. (Siehe [Status (nur für die Kategorien &quot;Standard&quot;, &quot;Workflow&quot;oder &quot;Ereignisse&quot;)](view-statistics-related-manager.md#status-for-default-workflow-or-events-categories-only). Sie können die Informationen so filtern, dass nur eine Teilmenge der Elemente angezeigt wird, indem Sie die verschiedenen verfügbaren Optionen verwenden (z. B. Status oder Kategorie). Sie können die resultierenden Arbeits- oder Auftragselemente (in auf- oder absteigender Reihenfolge) sortieren, indem Sie auf eine der Spaltenüberschriften klicken. Außerdem können Sie die Arbeitselemente mithilfe der Vorgangswerkzeuge verwalten, die über der Liste der Arbeitselemente angezeigt werden.

## Arbeitselemente filtern {#filter-the-work-items}

1. Klicken Sie auf die Registerkarte Work Manager .
1. Wählen Sie die Kriterien für einen oder mehrere der unten beschriebenen Filter aus und klicken Sie auf Los .

### Kategorie {#category}

**Standard:** Alle Arbeitselemente, denen der Client beim Übermitteln keine Kategorie zugewiesen hat. Work Manager verwaltet diese Elemente, daher gehören die Status zu Work Manager.

**Job Manager:** Alle Aufträge, die zu Job Manager gehören. Job Manager verwaltet eigene Aufträge und hat eigene Auftragsstatus. Siehe die spezifischen Auftragsstatus, die nachfolgend beschrieben werden.

**Workflow:** Alle Arbeitselemente, die zur Workflow-Ausführung gehören. Workflow verwaltet keine eigenen Arbeitselemente, sondern verlässt sich auf Work Manager. Daher gehören die Status zu Work Manager.

**Ereignisse:** Alle Arbeitselemente, die zur Ereignisverwaltung gehören. Die Ereignisverwaltung verwaltet keine eigenen Arbeitselemente, sondern verlässt sich auf Work Manager. Daher gehören die Status zu Work Manager.

### Status (nur für die Kategorien &quot;Standard&quot;, &quot;Workflow&quot;oder &quot;Ereignisse&quot;) {#status-for-default-workflow-or-events-categories-only}

**Alle anzeigen:** Zeigt alle aktuellen Arbeitselemente an.

**Geplant:** Zeigt alle Arbeitselemente an, die vom Anwendungsserver ausgeführt werden können, jedoch noch nicht gestartet wurden.

**Angehalten:** Zeigt alle geplanten Arbeitselemente an, die von der Client-Anwendung angehalten wurden. Diese Elemente können ausgeführt oder gelöscht werden. (Siehe Arbeitselemente oder Aufträge verwalten.)

**In Arbeit:** Zeigt alle Arbeitselemente an, die der Work Manager des Anwendungsservers ausgewählt hat und die entweder abgeschlossen werden oder fehlschlagen. Sie können für diese Arbeitselemente keine Vorgänge verwenden.

**Fertig:** Zeigt alle Arbeitselemente an, die erfolgreich ausgeführt wurden. Permanente Arbeitselemente verbleiben in diesem Status, und nicht permanente Elemente werden beim Beenden von Rückrufen an die Rückruf-Handler gelöscht. Sie können diese Elemente mithilfe des Vorgangs &quot;Delete Items&quot;löschen. (Siehe Arbeitselemente oder Aufträge verwalten.)

**Fehlgeschlagen:** Zeigt alle Arbeitselemente an, die aufgrund eines Fehlers nicht erfolgreich beendet wurden. Diese Arbeitselemente können mehrmals durch Verwenden des Vorgangs „Elemente wiederholen“ wiederholt werden. (Siehe Arbeitselemente oder Aufträge verwalten.) Über den Link Fehler in der Spalte Status können Sie auf Details zum Fehler zugreifen.

**Unbekannt:** Zeigt alle Arbeitselemente an, deren Status unbekannt ist.

### Status (nur für Job Manager-Kategorie) {#status-for-job-manager-category-only}

**Abgeschlossen** Zeigt alle Aufträge an, die erfolgreich ausgeführt wurden. Permanente Arbeitselemente verbleiben in diesem Status und nicht permanente Elemente werden beim Beenden von Rückrufen an die Rückruf-Handler gelöscht.

**Abschließen angefordert:** Zeigt Aufträge an, für die eine vollständige Anforderung ausgeführt wurde.

**Fehler angefordert:** Zeigt Aufträge an, für die eine Fehleranforderung ausgeführt wurde.

**Fehlgeschlagen:** Zeigt Aufträge an, die aufgrund eines Fehlers nicht erfolgreich beendet wurden. Über den Link Fehler in der Spalte Status können Sie auf Details zum Fehler zugreifen.

**Beenden angefordert:** Zeigt Aufträge an, für die eine Anforderung zum Beenden ausgeführt wurde.

**Beendet:** Zeigt Aufträge an, die beendet wurden, ohne abgeschlossen worden zu sein.

**Aussetzen angefordert:** Zeigt Aufträge an, für die eine Anforderung zum Aussetzen ausgeführt wurde.

**Ausgesetz:** Zeigt Aufträge an, die ausgesetzt wurden.

**Wartet auf Wiederaufnahme** Zeigt Aufträge an, für die eine Anforderung zur Wiederaufnahme gestellt wurde.

**In die Warteschlange gestellt** Zeigt Aufträge an, die sich in der Warteschlange befinden.

**Betrieb:** Zeigt Aufträge an, die gerade ausgeführt werden.

### Servername {#server-name}

Wählen Sie nur für Clusterserver den Namen des Knotens aus, um die Arbeitselemente oder Auftragselemente anzuzeigen, die nur auf diesem Server erstellt wurden. Wenn Alle anzeigen ausgewählt ist, werden alle Arbeitselemente für alle Knoten in einem Cluster angezeigt.

### Zeit erstellen {#create-time}

Wählen Sie eine Option in diesem Filter aus, um nur die Arbeitselemente anzuzeigen, die innerhalb des von Ihnen ausgewählten Zeitrahmens erstellt wurden. Wenn Sie beispielsweise &quot;1 Tag&quot;auswählen, werden alle Arbeitselemente angezeigt, die innerhalb von 24 Stunden vor der im Filter &quot;Vor&quot;festgelegten Zeit erstellt wurden.

### Vor {#prior-to}

Legt das Datum und die Uhrzeit fest, die der Filter Zeit erstellen als Enddatum verwendet. Behalten Sie die Option Aktuelles Datum und Uhrzeit verwenden bei, um vom aktuellen Datum und der aktuellen Uhrzeit zurückzufiltern, oder deaktivieren Sie die Option und geben Sie die entsprechenden Werte ein. Klicken Sie entweder auf die Kalendersymbole oder auf die Uhrsymbole, um Werte mithilfe dieser Tools auszuwählen.

Wenn Sie beispielsweise Zeit = 1 Tag erstellen und Vor = Aktuelles Datum und Zeit verwenden auswählen, werden alle Arbeitselemente zurückgegeben, die in den letzten 24 Stunden erstellt wurden.

>[!NOTE]
>
>Bei Oracle-Datenbankbereitstellungen funktionieren Datumsbereichsfilter (d. h. die Einstellungen &quot;Zeit erstellen&quot;und &quot;Vor&quot;) nicht ordnungsgemäß. Verwenden Sie einen anderen Filter, um Arbeitselemente abzurufen.

## Über die Benutzeroberfläche der Registerkarte &quot;Work Manager&quot; {#about-the-work-manager-tab-interface}

Wenn Sie eine Work Manager-Abfrage ausführen oder einen Vorgang an einem Arbeitselement oder Auftrag durchführen, wird eine Meldung über der Liste angezeigt. Diese Nachricht enthält Feedback zu der von Ihnen initiierten Aktion und in einigen Fällen einen Link &quot;Weitere Informationen&quot;, um Details anzugeben. Wenn beispielsweise der von Ihnen initiierte Vorgang fehlgeschlagen ist, gibt die Nachricht so viel an und stellt einen Link bereit, über den Details zum Fehler abgerufen werden.

Wenn Sie auf &quot;Weitere Informationen&quot;klicken, wird im Dialogfeld &quot;Vorgangsdetails&quot;eine Liste der Arbeitselemente oder Aufträge angezeigt, die während des Vorgangs ausgewählt wurden. Sie können auf jedes Listenelement klicken, um die Fehlerdetails unten im Dialogfeld anzuzeigen.

### Arbeitselemente oder Aufträge verwalten {#manage-the-work-items-or-jobs}

1. Verwenden Sie die unten beschriebenen Vorgangstools, um die Arbeitselemente oder Aufträge in der Liste zu verwalten.

   >[!NOTE]
   >
   >Vorgänge sind je nach Status des Elements verfügbar.

   **Elemente löschen:** Löscht das ausgewählte Arbeitselement oder den ausgewählten Auftrag.

   **Elemente anhalten:** Hält die ausgewählten Arbeitselemente oder Aufträge an.

   **Elemente fortsetzen:** Setzt die ausgewählten angehaltenen Arbeitselemente oder Aufträge fort.

   **Elemente wiederholen:** Versucht, die ausgewählten Arbeitselemente oder Aufträge von ihrem aktuellen Zustand an erneut auszuführen.

   Sie können überprüfen, ob ein Vorgang erfolgreich war, indem Sie über der Liste auf Weitere Informationen klicken. Ein Dialogfeld mit den ausgewählten Arbeitselementen oder Aufträgen und ihren Status wird angezeigt.

## Zusätzliche Informationen zum Status von Arbeitselementen {#additional-information-about-work-item-statuses}

Eine typische Statustransition für ein Arbeitselement ist &quot;Neu&quot;> &quot;Geplant&quot;> &quot;In Bearbeitung&quot;> &quot;Abgeschlossen&quot;oder &quot;Fehler&quot;.

Der Status Angehalten unterbricht diesen normalen Fluss. Entweder die Client-Anwendung oder der Systemadministrator kann diese Unterbrechung auslösen (z. B. zur Wartung oder Aktualisierung). Sie können diese Aktion rückgängig machen, indem Sie den Vorgang &quot;Fortsetzen&quot;verwenden, um das Arbeitselement wieder in den Status &quot;Geplant&quot;zu verschieben.

Ein Arbeitselement mit dem Status &quot;Geplant&quot;wird zur Ausführung in die Warteschlange gestellt, die noch nicht begonnen hat. Diese Elemente können angehalten oder gelöscht werden oder werden in den Status &quot;Wird ausgeführt&quot;verschoben, wenn Work Manager sie aus der Warteschlange nimmt. Laufende Arbeitselemente können nicht geändert werden. Sie werden entweder abgeschlossen oder schlagen fehl.

Der Status Fehlgeschlagen tritt aufgrund einer Fehlerbedingung auf, die während der Ausführung des Arbeitselements auftritt. Wenn Sie vermuten, dass Fehler situationsbedingt sind (aufgrund des Kontexts zum Zeitpunkt der Ausführung), können Sie die Ausführung wiederholen und das Arbeitselement wieder in die Warteschlange stellen. Nur eine begrenzte Anzahl weiterer Versuche ist zulässig.
