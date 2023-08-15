---
title: Ad-hoc-Abfragen beim Prozess-Reporting
seo-title: Ad-hoc Queries in Process Reporting
description: Erstellen von benutzerdefinierten Abfragen für die Suche nach Prozess- und Aufgabendetails in Process Reporting von AEM Forms auf JEE
seo-description: Create custom queries to search for AEM Forms on JEE  process and task details in Process Reporting
uuid: db0c5c28-b213-4582-a6ed-df127e570a4e
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b0a544e2-2ce4-48e2-a721-82f481d36004
docset: aem65
exl-id: a096eea0-b2fb-4d86-b729-ca47611135b2
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 98%

---

# Ad-hoc-Abfragen beim Prozess-Reporting{#ad-hoc-queries-in-process-reporting}

## Ad-hoc-Abfragen in Process Reporting {#ad-hoc-queries-in-process-reporting-1}

Mit Ad-hoc-Abfragen in Process Reporting können Sie benutzerdefinierte Abfragen erstellen, mit denen Sie nach Prozess- und Aufgabendetails der in Ihrer AEM Forms-Umgebung definierten AEM Forms-Prozessinstanzen suchen können.

Ad-hoc-Abfragen können auch mithilfe von Prozess- und Aufgabeneigenschaftsfiltern definiert werden. Diese Filter können dann gespeichert und zur späteren Ausführung der Berichte verwendet werden.

[**Prozesssuche**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-search-p): Suchen nach Prozessinstanzen mit einem benutzerdefinierten Suchfilter basierend auf Prozessattributen.

[**Prozessdetails**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-details-p): Anzeigen von Details zu einer Prozessinstanz durch Angabe der Prozess-ID.

**Aufgabensuche**: Suchen nach Aufgabeninstanzen mit einem benutzerdefinierten Suchfilter anhand von Aufgabenattributen.

**Aufgabendetails**: Anzeigen von Details zu einer Aufgabeninstanz durch Angabe der Aufgaben-ID.

### Prozesse und Aufgaben {#processes-and-tasks}

Die Schritte zum Erstellen von Filtern und Ausführen von Abfragen für Prozessdetails sind dieselben wie für Aufgaben.

Das bedeutet, dass sich die Benutzeroberflächen für die Prozesssuche und Aufgabensuche nur in den Feldern unterscheiden, nach denen Sie suchen können, und in den Feldern, die in den Suchergebnissen zurückgegeben werden. Dies liegt einfach daran, dass zwar viele der Felder identisch sind, bestimmte Felder jedoch für Prozesse spezifisch sind und andere für Aufgaben.

In diesem Artikel werden die Beschreibungen der Abschnitte Prozess-/Aufgabensuche und Prozess-/Aufgabendetails detailliert. An den geeigneten Stellen werden alle spezifischen Unterschiede speziell ausgewiesen.

## Prozess-/Aufgabensuche {#process-task-search}

Sie verwenden die Prozess-/Aufgabensuche, um Filter zum Abfragen von Prozess-/Aufgabeninstanzen zu definieren.

### So erstellen Sie eine Prozess-/Aufgabensuchabfrage {#to-create-a-process-task-search-query}

1. Um die gespeicherten Prozess-/Aufgabensuchabfragen anzuzeigen oder eine Abfrage zu erstellen, klicken Sie auf **Ad-hoc-Abfragen** und anschließend auf **Prozess-/Aufgabensuche**.

   ![search_nodes](assets/search_nodes.png)

   Das Bedienfeld **Meine Filter** wird rechts neben der Baumansicht angezeigt.

   Im Bedienfeld **Meine Filter** können Sie neue Ad-hoc-Abfragen erstellen und auf zuvor gespeicherte Abfragen klicken, um sie auszuführen.

   ![my_filters_panel](assets/my_filters_panel.png)

1. Um eine vorhandene Abfrage auszuführen, klicken Sie einfach auf die Abfrage im Bedienfeld **Meine Filter**.
1. Um eine Abfrage zu erstellen, klicken Sie auf **Hinzufügen** (+).

   Das Bedienfeld **Filter erstellen** wird angezeigt.

   ![create_filter_panel](assets/create_filter_panel.png)

   Eine Abfrage besteht aus einem oder mehreren Abfragefiltern. Um einen Filter zu erstellen, fügen Sie eine Filterzeile zur Abfrage hinzu. Standardmäßig wird zu der Abfrage nur eine Filterzeile hinzugefügt.

   **So definieren Sie Filter**

   1. Wählen Sie ein Feld aus.

      ![filter_field](assets/filter_field.png)

      >[!NOTE]
      >
      >Die Feldliste enthält die Felder, die für den AEM Forms-Prozess/die Aufgabe spezifisch sind.

   1. Wählen Sie eine Bedingung aus.

      ![filter_condition](assets/filter_condition.png)

      >[!NOTE]
      >
      >Die aufgeführten Bedingungen hängen von dem Attribut ab, das zum Filtern ausgewählt wurde.

   1. Geben Sie einen Wert ein.

      ![filter_value](assets/filter_value.png)

   1. Um einen weiteren Filter zur Abfrage hinzuzufügen, klicken Sie auf **Hinzufügen (+)** rechts neben der Filterzeile.

      Um einen Filter aus der Abfrage zu entfernen, klicken Sie auf **Löschen (-)** rechts neben der Filterzeile.

      ![filter_add_del](assets/filter_add_del.png)

Nachdem Sie eine Abfrage erstellt haben, haben Sie die folgenden Optionen oben rechts im Bedienfeld **Filter erstellen**:

* **Abbrechen**: Verwerfen der Änderungen und Zurückkehren zum Bedienfeld **Meine Filter**.
* **Ausführen**: Ausführen der aktuellen Abfrage, um die Ergebnisse anzuzeigen bzw. zu überprüfen. In diesem Fall brauchen Sie die Abfrage nicht zu speichern, bevor Sie sie ausführen. Sie können die Ergebnisse überprüfen, bei Bedarf Änderungen vornehmen und dann die Abfrage speichern, wenn Sie mit der Ausgabe zufrieden sind.
* **Speichern**: Speichern des Filters. Der Filter kann dann über das Bedienfeld **Meine Filter** angezeigt und ausgeführt werden.

### Optionen im Bedienfeld „Meine Filter“ {#options-in-my-filters-panel}

Verwenden Sie die Optionen im Bedienfeld **Meine Filter** zum **Hinzufügen** ![lc_pr_add_filter](assets/lc_pr_add_filter.png), **Bearbeiten** ![lc_pr_edit_filter](assets/lc_pr_delete_filter.png), oder **Löschen** ![lc_pr_delete_filter](assets/lc_pr_edit_filter.png) einer Ad-hoc-Abfrage.

![my_filters_options](assets/my_filters_options.png)

### So führen Sie eine Suchabfrage aus {#to-execute-a-search-query}

1. Um eine Abfrage auszuführen, klicken Sie auf den Filter im Bedienfeld **Meine Filter**, oder klicken Sie auf die Schaltfläche **Ausführen**, wenn Sie gerade einen Filter erstellen oder bearbeiten.
1. Die Ergebnisse der Abfrage werden im Bedienfeld **Bericht** des Fensters **Process Reporting** angezeigt.

   ![process_search_result](assets/process_search_result.png)

   Sie können die Suchergebnisse mithilfe des Bedienfelds zur Paginierung, das am unteren Rand des Berichts angezeigt wird, paginieren.

   ![process_result_pgn](assets/process_result_pgn.png)

   Wählen Sie in der Dropdown-Liste **Anzeige** die Anzahl der Ergebnisse, die pro Seite angezeigt werden sollen.

   Geben Sie in das Textfeld **Seite** eine Seitennummer ein, um direkt zu dieser Seite zu gelangen.

1. Die folgenden Felder werden in einem Prozesssuchergebnis angezeigt:

   * **Prozess-ID**: Die ID des Prozesses. Das Feld ist mit einem Hyperlink versehen. Wenn Sie in diesem Feld auf eine Prozess-ID klicken, werden Sie zum Bedienfeld **[!UICONTROL Prozessdetails]** für den Prozess weitergeleitet.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellungszeit**: Datum und Uhrzeit des Starts der Prozessinstanz
   * **Abschlusszeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer vom Start bis zum Abschluss der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig werden die Ergebnisse nach Prozess-ID sortiert. Um die Ergebnisse nach einem anderen Feld zu sortieren, klicken Sie auf den Feldtitel.

   Da die Sortierung ein Umschaltvorgang ist, können Sie durch Anklicken einer Spaltenüberschrift die Ergebnisse in aufsteigender Reihenfolge und durch erneutes Anklicken in absteigender Reihenfolge sortieren.

   Analog dazu werden die folgenden Felder in den Ergebnissen einer Aufgabensuche angezeigt:

   * **Aufgaben-ID**: Die ID der Aufgabe. Das Feld ist mit einem Hyperlink versehen. Wenn Sie auf eine Aufgaben-ID in diesem Feld klicken, werden Sie zum Bedienfeld **[!UICONTROL Aufgabendetails]** für die Aufgabe weitergeleitet.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellungszeit**: Datum und Uhrzeit des Starts der Prozessinstanz
   * **Abschlusszeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer vom Start bis zum Abschluss der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig werden die Ergebnisse nach Aufgaben-ID sortiert. Um die Ergebnisse nach einem anderen Feld zu sortieren, klicken Sie auf den Feldtitel. Die Ergebnisse werden nach derjenigen Spalte sortiert, die durch einen dunklen Pfeil neben der Spaltenüberschrift angezeigt wird.

   Da die Sortierung ein Umschaltvorgang ist, können Sie durch Anklicken einer Spaltenüberschrift die Ergebnisse in aufsteigender Reihenfolge und durch erneutes Anklicken in absteigender Reihenfolge sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   ![task_search_result](assets/task_search_result.png)

1. Klicken Sie auf die Schaltfläche mit den Leisten ![lc_pr_rail_button](assets/lc_pr_rail_button.png) oben links, um das Bedienfeld **Meine Filter** zu reduzieren und den verfügbaren Platz für das Bedienfeld **Bericht** zu erweitern.
1. Verwenden Sie die Optionen in der oberen rechten Ecke des Bedienfelds „Bericht“, um Vorgänge mit dem Abfrageergebnis durchzuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher

   * **In CSV exportieren**: Exportieren der Berichtsdaten in eine kommagetrennte Datei.

   >[!NOTE]
   >
   >Wenn Sie einen Bericht exportieren, wird das gesamte Suchergebnis in eine CSV-Datei exportiert, nicht nur in die aktuelle Seite

## Prozess-/Aufgabendetails {#process-task-details}

Sie verwenden das Bedienfeld **Prozessdetails**, um die Details eines bestimmten Prozesses anzuzeigen.

Analog dazu verwenden Sie das Bedienfeld **Aufgabendetails**, um die Details einer bestimmten Aufgabe anzuzeigen.

### So zeigen Sie Prozess-/Aufgabendetails an {#to-view-process-task-details}

Sie können die Details eines bestimmten AEM Forms-Prozesses oder einer bestimmten Aufgabe auf verschiedene Weisen anzeigen:

* **Aus einem Prozess-/Aufgabensuchergebnis**
* **Durch Eingabe der Prozess-/Aufgaben-ID im Bedienfeld „Prozess-/Aufgabendetails“**

#### Aus einem Prozess-/Aufgabensuchergebnis {#from-a-process-task-search-result}

1. Führen Sie eine Prozess-/Aufgabensuche aus. Weitere Informationen finden Sie unter [So führen Sie eine Prozesssuchabfrage aus](#to-execute-a-search-query).

   Beachten Sie, dass die im Ergebnis zurückgegebenen Prozess-IDs mit Hyperlinks versehen sind.

   ![process_id_list](assets/process_id_list.png)

1. Klicken Sie auf eine Prozess-ID in der Liste, um die Details dieses Prozesses im Bedienfeld **Prozessdetails** anzuzeigen.

   Das Abfrageergebnis der **Prozess-/Aufgabendetails** zeigt Details zu den Aufgaben/Formularen an, die in dem Prozess/der Aufgabe enthalten sind.

   Standardmäßig werden die Ergebnisse nach Aufgaben-/Formular-ID sortiert. Um die Ergebnisse nach einem anderen Feld zu sortieren, klicken Sie auf den Feldtitel. Die Spalte, nach der die Ergebnisse sortiert werden, wird durch einen dunklen Pfeil neben der Spaltenüberschrift angezeigt.

   Da die Sortierung ein Umschaltvorgang ist, können Sie durch Anklicken einer Spaltenüberschrift die Ergebnisse in aufsteigender Reihenfolge und durch erneutes Anklicken in absteigender Reihenfolge sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   **Ergebnisse der Prozessdetails**

   ![process_details](assets/process_details.png)

   **Linkes Bedienfeld**: Zeigt die folgenden Details des ausgewählten Prozesses an:

   * Name des Prozesses
   * Zeitpunkt der Prozesserstellung
   * Zeitpunkt des Prozessabschlusses
   * Prozessdauer
   * Prozessstatus
   * Prozessinitiator

   **Bedienfeld oben rechts**: Zeigt die folgenden Details zu den Aufgaben an, aus denen der ausgewählte Prozess besteht:

   * Aufgaben-ID
   * Aufgabenname
   * Aufgabenbesitzer
   * Zeitpunkt der Aufgabenerstellung
   * Zeitpunkt der Aufgabenaktualisierung
   * Zeitpunkt des Aufgabenabschlusses
   * Aufgabendauer
   * Aufgabenstatus

   **Bedienfeld unten rechts**: Zeigt die folgenden Details zum Prozessverlauf des ausgewählten Prozesses an:

   * Prozessname
   * Prozessinitiator
   * Datum der Prozessaktualisierung
   * Zeitpunkt des Prozessabschlusses
   * Prozessstatus

   **Ergebnisse der Aufgabendetails**

   ![Aufgabendetails](assets/task_details.png)

   **Linkes Bedienfeld**: Zeigt die folgenden Details der ausgewählten Aufgabe an:

   * Aufgabenname
   * ID des Prozesses, zu dem diese Aufgabe gehört
   * Aufgabenbeschreibung
   * Zeitpunkt der Aufgabenerstellung
   * Zeitpunkt des Aufgabenabschlusses
   * Aufgabendauer
   * Aufgabenstatus
   * Ausgewählter Aufgabenweg

   **Bedienfeld oben rechts**: Zeigt die folgenden Details zu den Formularen an, aus denen die ausgewählte Aufgabe besteht:

   * Formular-ID
   * Datum der Formularerstellung
   * Datum der Formularaktualisierung
   * Formularvorlagen-URL

   **Bedienfeld unten rechts**: Zeigt die folgenden Details zum Prozessverlauf der ausgewählten Aufgabe an:

   * Aufgabenzuweisungstyp
   * Aufgabenbesitzer
   * Erstellungsdatum der Aufgabenzuweisung
   * Zeitpunkt der Aufgabenaktualisierung

1. Klicken Sie auf **Zurück zur Prozess-/Aufgabensuche**, um zu dem Suchergebnis zurückzukehren, von dem aus die Prozess-/Aufgabendetails aufgeschlüsselt wurden.

   ![back_to_search](assets/back_to_search.png)

   Wenn die Prozess-/Aufgabendetails jedoch durch Eingabe einer bestimmten Prozess-/Aufgaben-ID gefunden wurden, werden Sie durch Klicken auf „Zurück zur Prozess-/Aufgabensuche“ zurück zu **Prozess-/Aufgabensuche** geleitet, ohne dass Suchergebnisse angezeigt werden.

#### Durch Eingabe der Prozess-/Aufgaben-ID im Bedienfeld „Prozess-/Aufgabendetails“ {#by-entering-the-process-task-id-in-the-process-task-details-panel-br}

1. Navigieren Sie zum Bedienfeld **Prozess-/Aufgabendetails**.

   ![details_nodes](assets/details_nodes.png)

1. Geben Sie im Textfeld „Prozess-/Aufgaben-ID“ die Prozess-/Aufgaben-ID ein.

   ![process_details-1](assets/process_details-1.png)

   Die Felder im Abfrageergebnis **Prozess-/Aufgabendetails** sind Felder, die für einen AEM Forms-Prozess/eine Aufgabe spezifisch sind.

   Für einen Prozess zeigt das Abfrageergebnis die Details der im Prozess enthaltenen Aufgaben an.

   Für eine Aufgabe zeigt das Abfrageergebnis die Details der in der Aufgabe enthaltenen Formulare an.
