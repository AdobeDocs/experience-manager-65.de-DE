---
title: Ad-hoc-Abfragen in Process Berichte
seo-title: Ad-hoc-Abfragen in Process Berichte
description: Erstellen Sie benutzerdefinierte Abfragen, um nach AEM Forms on JEE-Prozess- und Aufgabe-Details im Process Berichte zu suchen
seo-description: Erstellen Sie benutzerdefinierte Abfragen, um nach AEM Forms on JEE-Prozess- und Aufgabe-Details im Process Berichte zu suchen
uuid: db0c5c28-b213-4582-a6ed-df127e570a4e
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b0a544e2-2ce4-48e2-a721-82f481d36004
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 0%

---


# Ad-hoc-Abfragen im Process Berichte{#ad-hoc-queries-in-process-reporting}

## Ad-hoc-Abfragen im Process Berichte {#ad-hoc-queries-in-process-reporting-1}

Mit Ad-hoc-Abfragen in Process Berichte können Sie benutzerdefinierte Abfragen erstellen, mit denen Sie nach Prozess- und Aufgaben-Details der in Ihrer AEM Forms-Umgebung definierten AEM Forms-Prozessinstanzen suchen können.

Ad-hoc-Abfragen können auch mit Filtern für Prozess- und Aufgabe-Eigenschaften definiert werden. Diese Filter können dann gespeichert und verwendet werden, um die Berichte später auszuführen.

[**Prozesssuche**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-search-p): Suchen Sie nach Prozessinstanzen mit einem benutzerdefinierten Suchfilter, der auf Prozessattributen basiert.

[**Prozessdetails**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-details-p): Details zur Ansicht einer Prozessinstanz durch Angabe der Prozess-ID.

**Aufgaben-Suche**: Suchen Sie nach Instanzen der Aufgabe mit einem benutzerdefinierten Suchfilter, der auf Aufgaben-Attributen basiert.

**Aufgabe Details**: Details zur Ansicht einer Aufgabe durch Angabe der Aufgaben-ID.

### Vorgänge und Aufgaben {#processes-and-tasks}

Die Schritte zum Erstellen von Filtern und zum Ausführen von Abfragen für Prozessdetails sind dieselben wie bei Aufgaben.

Das bedeutet, dass die Benutzeroberflächen für die Prozesssuche und -suche sich nur in den Aufgaben unterscheiden, nach denen Sie suchen können, und in den Suchergebnissen zurückgegebenen Feldern. Dies liegt einfach daran, dass zwar viele Felder identisch sind, bestimmte Felder aber für bestimmte Prozesse spezifisch sind und bestimmte Felder für Aufgaben spezifisch sind.

In diesem Artikel werden die Beschreibungen der Abschnitte &quot;Prozesssuche/Aufgabe&quot;und &quot;Prozess-/Aufgabe-Details&quot;erläutert. An geeigneten Orten werden alle spezifischen Unterschiede gesondert ausgewiesen.

## Prozess-/Aufgaben-Suche {#process-task-search}

Mit der Aufgabe-/Prozesssuche können Sie Filter für die Abfrage von Prozess-/Aufgabe-Instanzen definieren.

### So erstellen Sie eine Abfrage für die Prozesssuche/Aufgabe {#to-create-a-process-task-search-query}

1. Um die gespeicherten Abfragen für die Aufgabe-/Prozesssuche Ansicht oder eine Abfrage zu erstellen, klicken Sie auf **Adhoc-Abfragen** und dann auf **Aufgaben-/Prozesssuche**.

   ![search_nodes](assets/search_nodes.png)

   Das Bedienfeld **Meine Filter** wird rechts neben der Ansicht angezeigt.

   Im Bedienfeld **Meine Filter** können Sie neue Ad-hoc-Abfragen erstellen und auf klicken, um zuvor gespeicherte Abfragen auszuführen.

   ![my_Filters_panel](assets/my_filters_panel.png)

1. Um eine bestehende Abfrage auszuführen, klicken Sie einfach auf die Abfrage im Bereich **Meine Filter**.
1. Um eine Abfrage zu erstellen, klicken Sie auf **Hinzufügen** (+).

   Das Bedienfeld **Filter erstellen** wird angezeigt.

   ![create_filter_panel](assets/create_filter_panel.png)

   Eine Abfrage besteht aus einem oder mehreren Filtern der Abfrage. Um einen Filter zu erstellen, fügen Sie der Abfrage eine Filterzeile hinzu. Standardmäßig wird der Abfrage eine Filterzeile hinzugefügt.

   **So definieren Sie einen Filter**

   1. Wählen Sie ein Feld aus.

      ![filter_field](assets/filter_field.png)

      >[!NOTE]
      >
      >Die Liste &quot;field&quot;enthält die Felder, die für den AEM Forms-Prozess/die-Aufgabe spezifisch sind.

   1. Wählen Sie eine Bedingung aus.

      ![filter_bedingung](assets/filter_condition.png)

      >[!NOTE]
      >
      >Die aufgelisteten Bedingungen hängen vom Attribut ab, das zum Filtern ausgewählt wurde.

   1. Geben Sie einen Wert ein.

      ![filter_value](assets/filter_value.png)

   1. Um der Abfrage einen weiteren Filter hinzuzufügen, klicken Sie auf **Hinzufügen (+)** rechts neben der Filterzeile.

      Um einen Filter aus der Abfrage zu entfernen, klicken Sie auf **Löschen (-)** rechts neben der Filterzeile.

      ![filter_add_del](assets/filter_add_del.png)

Nachdem Sie eine Abfrage erstellt haben, verwenden Sie die Optionen oben rechts im Bedienfeld **Filter erstellen**, um:

* **Abbrechen**: Abbrechen Sie die Änderungen und gehen Sie zurück zum  **Mein** Filterfeld.
* **Ausführen**: Führen Sie die aktuelle Abfrage aus, um die Ergebnisse zu sehen und / oder zu überprüfen. In diesem Fall müssen Sie die Abfrage nicht speichern, bevor Sie die Abfrage ausführen. Sie können die Ergebnisse überprüfen, bei Bedarf Änderungen vornehmen und die Abfrage dann speichern, wenn Sie mit der Ausgabe zufrieden sind.
* **Speichern**: Speichern Sie den Filter. Der Filter kann dann über das Bedienfeld **Meine Filter** angezeigt und ausgeführt werden.

### Optionen im Bereich &quot;Meine Filter&quot;{#options-in-my-filters-panel}

Verwenden Sie die Optionen im Bereich **Meine Filter** in **Hinzufügen** ![lc_pr_add_filter](assets/lc_pr_add_filter.png), **Bearbeiten** ![lc_pr_delete_filter](assets/lc_pr_delete_filter.png) oder **Löschen** ![lc_pr_edit_filter](assets/lc_pr_edit_filter.png)eine Ad-hoc-Abfrage.

![my_Filters_options](assets/my_filters_options.png)

### So führen Sie eine Search-Abfrage {#to-execute-a-search-query} aus

1. Um eine Abfrage auszuführen, klicken Sie im Bereich **Meine Filter** auf den Filter oder klicken Sie auf die Schaltfläche **Ausführen**, wenn Sie einen Filter erstellen oder bearbeiten.
1. Die Ergebnisse der Abfrage werden im Bereich **Bericht** des Fensters **Berichte verarbeiten** angezeigt.

   ![process_search_result](assets/process_search_result.png)

   Sie können die Suchergebnisse mithilfe des Seitenumbruchbedienfelds am unteren Rand des Berichts paginieren.

   ![process_result_pgn](assets/process_result_pgn.png)

   Wählen Sie in der Dropdown-Liste **Anzeige** die Anzahl der pro Seite anzuzeigenden Ergebnisse aus.

   Geben Sie im Textfeld **Seite** eine Seitenzahl ein, um direkt zu dieser Seite zu wechseln.

1. Die folgenden Felder werden in einem Prozesssuchergebnis angezeigt:

   * **Prozess-ID**: Die ID des Prozesses. Das Feld ist mit Hyperlinks verknüpft. Wenn Sie in diesem Feld auf eine Prozess-ID klicken, werden Sie zum Bereich **[!UICONTROL Prozessdetails]** für den Prozess weitergeleitet.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellungszeit**: Datum und Uhrzeit des Starts der Prozessinstanz
   * **Abgeschlossene Zeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer vom Beginn bis zum Abschluss der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig wird das Ergebnis nach Prozess-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Spaltenüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut, um es absteigend zu sortieren.

   Gleichermaßen werden die folgenden Felder in einem Suchergebnis der Aufgabe angezeigt:

   * **Aufgaben-ID**: Die ID der Aufgabe. Das Feld ist mit Hyperlinks verknüpft. Wenn Sie in diesem Feld auf eine Aufgaben-ID klicken, werden Sie zum Bereich **[!UICONTROL Aufgaben-Details]** für die Aufgabe weitergeleitet.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellungszeit**: Datum und Uhrzeit des Starts der Prozessinstanz
   * **Abgeschlossene Zeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer vom Beginn bis zum Abschluss der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig wird das Ergebnis nach Aufgaben-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel. Das Ergebnis wird nach der Spalte sortiert, die durch einen dunklen Pfeil neben der Spaltenüberschrift gekennzeichnet ist.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Feldüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut darauf, um es absteigend zu sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   ![Aufgabe_Suche_Ergebnis](assets/task_search_result.png)

1. Klicken Sie oben links auf die Schaltfläche ![lc_pr_rail_button](assets/lc_pr_rail_button.png), um den Bereich **Meine Filter** zu reduzieren und den für das Bedienfeld **Bericht** verfügbaren Platz zu erweitern.
1. Verwenden Sie die Optionen in der oberen rechten Ecke des Bereichs **Bericht **zum Durchführen von Vorgängen am Ergebnis der Abfrage.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten in der Datenspeicherung

   * **In CSV** exportieren: Exportieren Sie die Berichtsdaten in eine kommagetrennte Datei.
   >[!NOTE]
   >
   >Wenn Sie einen Bericht exportieren, wird das gesamte Suchergebnis in eine CSV-Datei exportiert und nicht nur in die aktuelle Seite

## Prozess-/Aufgaben-Details {#process-task-details}

Mit dem Bedienfeld **Prozessdetails** können Sie die Details eines bestimmten Vorgangs Ansicht werden.

Gleichermaßen verwenden Sie das Bedienfeld **Aufgabe Details**, um die Details einer bestimmten Aufgabe Ansicht.

### So führen Sie Ansichten für Prozess-/Aufgaben-Details {#to-view-process-task-details} aus

Sie können die Details eines bestimmten AEM Forms-Prozesses/einer bestimmten-Aufgabe Ansicht ausführen:

* **Von einem Prozess-/Aufgaben-Suchergebnis**
* **Durch Eingabe der Prozess-/Aufgaben-ID in das Bedienfeld &quot;Prozess-/Aufgaben-Details&quot;**

#### Aus einem Prozess-/Aufgaben-Suchergebnis {#from-a-process-task-search-result}

1. Führen Sie eine Prozess-/Aufgaben-Suche aus. Weitere Informationen finden Sie unter [So führen Sie eine Process Search-Abfrage](#to-execute-a-search-query) aus.

   Beachten Sie, dass die im Ergebnis zurückgegebenen Prozess-IDs Hyperlinks sind.

   ![process_id_Liste](assets/process_id_list.png)

1. Klicken Sie auf eine Prozess-ID in der Liste, um die Details zu diesem Vorgang im Bereich **Prozessdetails** Ansicht.

   Die Abfrage **Prozess-/Aufgabe-Details** zeigt Details zu den Aufgaben/Formularen an, die im Prozess/in der Aufgabe enthalten sind.

   Standardmäßig wird das Ergebnis nach Aufgaben-/Formular-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel. Die Spalte, nach der das Ergebnis sortiert wird, wird durch einen dunklen Pfeil neben der Spaltenüberschrift angezeigt.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Feldüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut darauf, um es absteigend zu sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   **Prozessdetails-Ergebnis**

   ![process_details](assets/process_details.png)

   **Linke Leiste:** Zeigt die folgenden Details des ausgewählten Prozesses an:

   * Name des Prozesses
   * Zeitpunkt der Prozesserstellung
   * Abschlussdatum des Prozesses
   * Prozessdauer
   * Prozessstatus
   * Prozessinitiator

   **Rechts oben:** Zeigt die folgenden Details der Aufgaben an, aus denen der ausgewählte Prozess besteht:

   * Aufgaben-ID
   * Name der Aufgabe
   * Eigentümer der Aufgabe
   * Zeitpunkt der Erstellung der Aufgabe
   * Aktualisierungsdatum der Aufgabe
   * Abschlussdatum der Aufgabe
   * Dauer der Aufgabe
   * Status der Aufgabe

   **Unterrechts:** Zeigt die folgenden Details des Prozessverlaufs des ausgewählten Prozesses an:

   * Prozessname
   * Prozessinitiator
   * Aktualisierungsdatum
   * Abschlussdatum des Prozesses
   * Prozessstatus

   **Ergebnis der Aufgabe**

   ![Aufgabendetails](assets/task_details.png)

   **Linke Leiste:** Zeigt die folgenden Details zur ausgewählten Aufgabe an:

   * Aufgabenname
   * ID des Prozesses, zu dem diese Aufgabe gehört
   * Beschreibung der Aufgabe
   * Zeitpunkt der Erstellung der Aufgabe
   * Abschlussdatum der Aufgabe
   * Dauer der Aufgabe
   * Status der Aufgabe
   * Gewählte Aufgabe

   **Rechts oben:** Zeigt die folgenden Details der Formulare an, aus denen die ausgewählte Aufgabe besteht:

   * Foprm-ID
   * Zeitpunkt der Formularerstellung
   * Datum der Formularaktualisierung
   * URL der Formularvorlage

   **Unterrechts:** Zeigt die folgenden Details zum Prozessverlauf der ausgewählten Aufgabe an:

   * Zuordnungstyp für Aufgaben
   * Eigentümer der Aufgabe
   * Erstellungsdatum der Aufgabe
   * Aktualisierungsdatum der Aufgabe






1. Klicken Sie auf **Zurück zu Prozess-/Aufgabe-Suche**, um zu dem Suchergebnis zurückzukehren, aus dem die Prozess-/Aufgabe-Details heruntergeführt wurden.

   ![back_to_search](assets/back_to_search.png)

   Wenn Sie jedoch die Prozess-/Aufgaben-Details durch Eingabe einer bestimmten Prozess-/Aufgaben-ID gefunden haben, führen Sie durch Klicken auf Zurück zur Prozess-/Aufgabe-Suche zurück zu **Aufgabe-Suche**, ohne Suchergebnisse anzuzeigen.

#### Durch Eingabe der Prozess-/Aufgaben-ID im Bereich &quot;Prozess-/Aufgaben-Details&quot; {#by-entering-the-process-task-id-in-the-process-task-details-panel-br}

1. Wechseln Sie zum Bereich **Prozess-/Aufgabe-Details**.

   ![details_nodes](assets/details_nodes.png)

1. Geben Sie in das Textfeld &quot;Prozess-/Aufgaben-ID&quot;die Prozess-/Aufgaben-ID ein.

   ![process_details-1](assets/process_details-1.png)

   Die Felder in der Abfrage **Prozess-/Aufgabe-Details** sind für einen AEM Forms-Prozess/eine-Aufgabe spezifische Felder.

   Bei einem Prozess zeigt das Ergebnis der Abfrage die Details der Aufgaben an, die im Prozess enthalten sind.

   Bei einer Aufgabe zeigt das Ergebnis der Abfrage die Details der Formulare in der Aufgabe an.
