---
title: Reporting
description: Erfahren Sie, wie Sie mit Reporting in Adobe Experience Manager arbeiten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: 2a0bf59d-8829-4142-9cb4-dcef90f53ae9
source-git-commit: 6799f1d371734b69c547f3c0c68e1e633aa63229
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Reporting {#reporting}

Um Ihnen bei der Überwachung und Analyse des Status Ihrer Instanz zu helfen, bietet Adobe Experience Manager (AEM) eine Auswahl von Standardberichten, die für Ihre individuellen Anforderungen konfiguriert werden können:

* [Komponentenbericht](#component-report)
* [Speichernutzung](#disk-usage)
* [Konsistenzprüfung](#health-check)
* [Seitenaktivitätsbericht](#page-activity-report)
* [Benutzergenerierter Inhaltsbericht](#user-generated-content-report)
* [Benutzerbericht](#user-report)
* [Bericht der Workflow-Instanz](#workflow-instance-report)
* [Workflow-Bericht](#workflow-report)

>[!NOTE]
>
>Diese Berichte sind nur in der klassischen Benutzeroberfläche verfügbar. Informationen zur Systemüberwachung und zum Reporting in der modernen Benutzeroberfläche finden Sie unter [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

Über die Konsole **Tools** kann auf alle Berichte zugegriffen werden. Auswählen **Berichte** Doppelklicken Sie im linken Bereich auf den gewünschten Bericht im rechten Bereich, damit Sie ihn zur Anzeige, Konfiguration oder beidem öffnen können.

Neue Instanzen eines Berichts können auch über die **Instrumente** Konsole. Auswählen **Berichte** im linken Bereich, dann **Neu...** aus der Symbolleiste. Definieren Sie eine **Titel** und **Name**, wählen Sie den gewünschten Berichtstyp aus und klicken Sie auf **Erstellen**. Ihre neue Berichtsinstanz wird in der Liste angezeigt. Doppelklicken Sie darauf, um den Bericht zu öffnen, und ziehen Sie dann eine Komponente aus dem Sidekick, damit Sie die erste Spalte erstellen und die Berichtsdefinition starten können.

>[!NOTE]
>
>Zusätzlich zu den standardmäßigen AEM Berichten, die standardmäßig verfügbar sind, können Sie [eigene (neue) Berichte erstellen](/help/sites-developing/dev-reports.md).

## Die Grundlagen der Berichtsanpassung {#the-basics-of-report-customization}

Es stehen verschiedene Berichtsformate zur Verfügung. Die folgenden Berichte nutzen alle Spalten, die wie in den folgenden Abschnitten beschrieben angepasst werden können:

* [Komponentenbericht](#component-report)
* [Seitenaktivitätsbericht](#page-activity-report)
* [Benutzergenerierter Inhaltsbericht](#user-generated-content-report)
* [Benutzerbericht](#user-report)
* [Bericht der Workflow-Instanz](#workflow-instance-report)

>[!NOTE]
>
>Die folgenden Berichte verfügen alle über ihr eigenes Format und ihre eigene Anpassung:
>
>
>* Die [Konsistenzprüfung](#health-check) nutzt Auswahlfelder, um die Daten anzugeben, zu denen Sie einen Bericht erstellen möchten.
>* [Festplattenauslastung](#disk-usage) verwendet Links zum Drilldown in der Repository-Struktur.
>* [Workflow](/help/sites-administering/reporting.md#workflow-report) bietet einen Überblick über die Workflows, die auf Ihrer Instanz ausgeführt werden.
>
>Die folgenden Verfahren für die Spaltenkonfiguration sind daher nicht angemessen. Details dazu finden Sie in den Beschreibungen der einzelnen Berichte.

### Auswählen und Positionieren der Datenspalten {#selecting-and-positioning-the-data-columns}

Spalten können zu allen Berichten hinzugefügt, neu positioniert oder aus ihnen entfernt werden, entweder standardmäßig oder individuell.

Die **Komponenten** im Sidekick (auf der Berichtsseite verfügbar) werden alle Datenkategorien aufgelistet, die als Spalten ausgewählt werden können.

So ändern Sie die Datenauswahl:

* Um eine Spalte hinzuzufügen, ziehen Sie die gewünschte Komponente aus dem Sidekick und legen Sie sie an der gewünschten Position ab

   * Ein grünes Häkchen zeigt an, wann die Position gültig ist, und ein Pfeile zeigt genau an, wo sie platziert wird
   * Ein rotes Symbol, das nicht startet, zeigt an, wann die Position ungültig ist

* Um eine Spalte zu verschieben, klicken Sie auf die Kopfzeile, halten Sie die Taste gedrückt und ziehen Sie sie an die neue Position
* Um eine Spalte zu entfernen, klicken Sie auf den Spaltentitel, halten Sie die Maustaste gedrückt und ziehen Sie sie in den Kopfzeilenbereich des Berichts. (Ein rotes Minuszeichen weist darauf hin, dass die Position ungültig ist.) Lassen Sie die Maustaste los und das Dialogfeld &quot;Komponenten löschen&quot;fordert Sie auf zu bestätigen, dass Sie die Spalte wirklich löschen möchten.

### Spalten-Dropdown-Menü {#column-drop-down-menu}

Jede Spalte im Bericht verfügt über ein Dropdown-Menü. Es wird angezeigt, wenn der Mauszeiger über die Zelle mit dem Spaltentitel bewegt wird.

Eine Pfeilspitze wird ganz rechts in der Titelzelle angezeigt (nicht zu verwechseln mit der Pfeilspitze direkt rechts neben dem Titeltext, der die [aktueller Sortiermechanismus](#sorting-the-data)).

![reportcolumnsort](assets/reportcolumnsort.png)

Die im Menü verfügbaren Optionen hängen von der Konfiguration der Spalte ab (wie bei der Projektentwicklung vorgenommen). Alle ungültigen Optionen sind abgeblendet (ausgegraut).

### Sortieren der Daten {#sorting-the-data}

Die Daten können nach einer bestimmten Spalte sortiert werden:

* durch Klicken auf die entsprechende Spaltenüberschrift. Die Sortierung umschaltet sich zwischen auf- und absteigender Sortierung. Die Sortierung wird durch eine Pfeilspitze direkt neben dem Titeltext angezeigt.
* die [Dropdown-Menü der Spalte](#column-drop-down-menu) zur Auswahl von **Aufsteigende Sortierung** oder **Absteigende Sortierung** Auch dies wird durch eine Pfeilspitze direkt neben dem Titeltext angezeigt.

### Gruppen und das aktuelle Datendiagramm {#groups-and-the-current-data-chart}

In den entsprechenden Spalten können Sie **Nach dieser Spalte gruppieren** aus dem [Dropdown-Menü der Spalte](#column-drop-down-menu). Dadurch werden die Daten nach jedem eindeutigen Wert in dieser Spalte gruppiert. Sie können mehrere Spalten auswählen, die gruppiert werden sollen. Die Option ist abgeblendet (grau ausgeblendet), wenn die Daten in der Spalte unangemessen sind. Das heißt, jeder Eintrag ist klar und eindeutig, sodass keine Gruppen gebildet werden können. Beispielsweise die Spalte Benutzer-ID des Benutzerberichts.

Nach der Gruppierung von mindestens einer Spalte wird ein Kreisdiagramm von **Aktuelle Daten** wird basierend auf dieser Gruppierung generiert. Wenn mehrere Spalten gruppiert sind, wird dies im Diagramm angezeigt.

![reportuser](assets/reportuser.png)

Wenn Sie den Cursor über das Kreisdiagramm bewegen, wird der aggregierte Wert für das entsprechende Segment angezeigt. Hierbei wird das aktuell für die Spalte definierte Aggregat verwendet, z. B. Zählung, Minimum, Durchschnitt usw.

### Filter und Aggregate {#filters-and-aggregates}

In den entsprechenden Spalten können Sie auch **Filtereinstellungen** und/oder **Aggregate** aus dem [Dropdown-Menü der Spalte](#column-drop-down-menu).

#### Filter {#filters}

Mit den Filtereinstellungen können Sie die Kriterien für die anzuzeigenden Einträge festlegen. Folgende Operatoren stehen zur Verfügung:

* `contains`
* `equals`

![reportfilter](assets/reportfilter.png)

Sie können wie folgt einen Filter festlegen:

1. Wählen Sie den gewünschten Operator aus der Dropdown-Liste aus.
1. Geben Sie den zu filternden Text ein.
1. Klicken Sie auf **Übernehmen**.

So deaktivieren Sie den Filter:

1. Entfernen Sie den Filtertext.
1. Klicken Sie auf **Übernehmen**.

#### Aggregate {#aggregates}

Sie können auch eine Zusammenfassungsmethode auswählen (diese können je nach ausgewählter Spalte variieren):

![reportaggregate](assets/reportaggregate.png)

### Spalteneigenschaften {#column-properties}

Diese Option ist nur verfügbar, wenn [Generische Spalte](#generic-column) im [Benutzerbericht](#user-report) verwendet wurde.

### Frühere Daten {#historic-data}

Eine Grafik der Änderungen Ihrer Daten im Zeitverlauf finden Sie unter **Historische Daten**. Dies wird aus Momentaufnahmen abgeleitet, die in regelmäßigen Abständen erstellt werden.

Die Daten sind:

* Wird, sofern verfügbar, von der ersten sortierten Spalte erfasst, andernfalls von der ersten (nicht gruppierten) Spalte
* Nach der entsprechenden Spalte gruppiert

Der Bericht kann wie folgt generiert werden:

1. Satz **Gruppierung** in der erforderlichen Spalte.
1. **Bearbeiten** die Konfiguration, damit Sie stündliche oder tägliche Momentaufnahmen definieren können.
1. **Beenden...** die Definition, um die Sammlung von Momentaufnahmen zu starten.

   Die roten/grünen Reglerschaltflächen oben links zeigen an, wenn Momentaufnahmen erfasst werden.

Das daraus resultierende Diagramm wird unten rechts angezeigt:

![reporttrends](assets/reporttrends.png)

Beim Start der Datenerfassung können Sie Folgendes auswählen:

* **Zeitraum**

  Sie können Ab- und Bis-Daten für die angezeigten Berichtsdaten auswählen.

* **Intervall**

  Monat, Woche, Tag oder Stunde können für die Skalierung und Zusammenfassung des Berichts ausgewählt werden.

  Wenn zum Beispiel für Februar 2011 tägliche Momentaufnahmen verfügbar sind:

   * Wenn das Intervall auf `Day` festgelegt ist, wird jede Momentaufnahme als einzelner Wert im Diagramm angezeigt.
   * Wenn das Intervall auf `Month` festgelegt ist, werden alle Momentaufnahmen aus dem Monat Februar in einem einzelnen Wert zusammengefasst (der im Diagramm als einzelner „Punkt“ angezeigt wird).

Wählen Sie Ihre Anforderungen aus und klicken Sie dann auf **Los**, um sie auf den Bericht anzuwenden. Um die Anzeige nach der Anfertigung weiterer Momentaufnahmen zu aktualisieren, klicken Sie erneut auf **Los**.

![chlimage_1-43](assets/chlimage_1-43.png)

Wenn Momentaufnahmen erfasst werden, haben Sie folgende Möglichkeiten:

* Verwendung **Beenden...** erneut, um die Sammlung neu zu initialisieren.

  **Beenden** &quot;friert&quot;die Struktur des Berichts (d. h. die dem Bericht zugewiesenen Spalten, die gruppiert, sortiert, gefiltert usw. sind) ein und beginnt mit Momentaufnahmen.

* Öffnen Sie die **Bearbeiten** Dialogfeld, in dem Sie **Keine Daten-Momentaufnahmen** , um die Sammlung zu beenden, bis sie erforderlich ist.

  Durch **Bearbeiten** wird lediglich das Anfertigen von Momentaufnahmen ein- oder ausgeschaltet. Wenn das Anfertigen von Momentaufnahmen erneut eingeschaltet wird, wird der Status des Berichts bei dessen letzter Fertigstellung zum Anfertigen weiterer Momentaufnahmen verwendet.

>[!NOTE]
>
>Die Momentaufnahmen werden unter `/var/reports/...` gespeichert, wo der übrige Pfad den Pfad des jeweiligen Berichts sowie die bei der Fertigstellung des Berichts erstellte ID wiedergibt.
>
>
>Alte Momentaufnahmen können manuell bereinigt werden, wenn Sie sicher sind, dass Sie diese Instanzen nicht mehr benötigen.

>[!NOTE]
>
>Die vorkonfigurierten Berichte sind nicht leistungsintensiv, es wird jedoch dennoch empfohlen, in einer Produktionsumgebung tägliche Momentaufnahmen zu verwenden. Führen Sie diese täglichen Momentaufnahmen nach Möglichkeit zu einer Tageszeit aus, zu der auf Ihrer Website nicht viel Aktivität vorhanden ist. Dies kann mit dem `Daily snapshots (repconf.hourofday)` Parameter für **Day CQ-Berichtkonfiguration**. Siehe [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für weitere Informationen zur Konfiguration.

#### Anzeigebeschränkungen {#display-limits}

Der Bericht zu historischen Daten kann sich aufgrund von Beschränkungen, die je nach Anzahl der Ergebnisse für den ausgewählten Zeitraum festgelegt werden können, auch geringfügig ändern.

Jede horizontale Zeile wird als Reihe bezeichnet (und entspricht einem Eintrag in der Diagrammlegende) und jede vertikale Spalte von Punkten stellt die zusammengefassten Momentaufnahmen dar.

![chlimage_1-44](assets/chlimage_1-44.png)

Um die Grafik über längere Zeiträume hinweg sauber zu halten, können Einschränkungen festgelegt werden. Für die Standardberichte sind dies:

* horizontale Reihe – Standardwert und Systemmaximum ist `9`

* vertikale zusammengefasste Momentaufnahmen – Standardwert ist `35` (pro horizontaler Reihe)

Wenn also die (entsprechenden) Grenzwerte überschritten werden, gilt Folgendes:

* die Punkte werden nicht angezeigt
* Die Legende für das historische Datendiagramm zeigt möglicherweise eine andere Anzahl von Einträgen als die des aktuellen Datendiagramms.

![chlimage_1-45](assets/chlimage_1-45.png)

In benutzerspezifischen Berichten kann auch der Wert **Insgesamt** für die ganze Reihe angezeigt werden. Dies wird als eine Reihe angezeigt (horizontale Linie und Eintrag in der Legende).

>[!NOTE]
>
>Bei benutzerspezifischen Berichten können die Begrenzungen unterschiedlich festgelegt werden.

### Bearbeiten (Bericht) {#edit-report}

Die **Bearbeiten** -Schaltfläche öffnet die **Bericht bearbeiten** Dialogfeld.

Dies ist ein Speicherort, an dem der Zeitraum für die Erfassung von Momentaufnahmen für [frühere Daten](#historic-data) festgelegt wird. Es können jedoch auch diverse andere Einstellungen festgelegt werden:

![reportedit](assets/reportedit.png)

* **Titel**

  Sie können Ihren eigenen Titel festlegen.

* **Beschreibung**

  Sie können Ihre eigene Beschreibung festlegen.

* **Stammpfad** (*nur für bestimmte Berichte aktiv*)

  Verwenden Sie diese Einstellung, um den Bericht auf einen Abschnitt oder Unterabschnitt des Repositorys zu beschränken.

* **Berichtsverarbeitung**

   * **Daten automatisch aktualisieren**

     Die Berichtsdaten werden jedes Mal aktualisiert, wenn Sie die Berichtsdefinition aktualisieren.

   * **Daten manuell aktualisieren**

     Diese Option kann verwendet werden, um bei einer großen Datenmenge durch automatische Aktualisierungsvorgänge verursachte Verzögerungen zu verhindern.

     Diese Auswahl zeigt an, dass die Berichtsdaten manuell aktualisiert werden müssen, wenn sich ein beliebiger Aspekt der Berichtskonfiguration verändert hat. Das bedeutet auch, dass die Berichtstabelle ausgeblendet wird, wenn Sie einen beliebigen Aspekt der Konfiguration ändern.

     Wenn diese Option ausgewählt ist, wird die **[Daten laden](#load-data)** angezeigt wird (neben **Bearbeiten** zum Bericht). **Daten laden** lädt die Daten und aktualisiert die angezeigten Berichtsdaten.

* **Momentaufnahmen**
Sie können festlegen, wie oft Momentaufnahmen angefertigt werden sollen: täglich, stündlich oder gar nicht.

### Daten laden {#load-data}

Die Schaltfläche **Daten laden** wird nur angezeigt, wenn **Daten manuell aktualisieren** unter **[Bearbeiten](#edit-report)** ausgewählt wurde.

![chlimage_1-46](assets/chlimage_1-46.png)

Klicken **Daten laden** lädt die Daten neu und aktualisiert den angezeigten Bericht.

Die Auswahl von „Daten manuell aktualisieren“ bedeutet Folgendes:

1. Wenn Sie die Berichtskonfiguration ändern, wird die Tabelle der Berichtsdaten ausgeblendet.

   Wenn Sie beispielsweise den Sortiermechanismus für eine Spalte ändern, werden die Daten nicht angezeigt.

1. Wenn die Berichtsdaten erneut angezeigt werden sollen, müssen Sie auf **Daten laden** , um die Daten neu zu laden.

### Beenden (Bericht) {#finish-report}

Wenn Sie **Beenden** Bericht:

* Berichtdefinition *ab diesem Zeitpunkt* wird zum Erstellen der Momentaufnahmen verwendet. Danach können Sie die Arbeit an einer Berichtsdefinition fortsetzen, da diese von den Momentaufnahmen getrennt ist.
* Alle vorhandenen Momentaufnahmen werden entfernt.
* Neue Momentaufnahmen für die [Historische Daten](#historic-data).

Mit diesem Dialogfeld können Sie Ihren eigenen Titel und Ihre eigene Beschreibung für den resultierenden Bericht definieren oder aktualisieren.

![reportfinish](assets/reportfinish.png)

## Berichtstypen {#report-types}

### Komponentenbericht {#component-report}

Der Komponentenbericht stellt Informationen dazu bereit, wie Ihre Website die Komponenten verwendet.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) zu:

* Autor
* Komponentenpfad
* Komponententyp
* Zuletzt geändert
* Seite

Das bedeutet, dass Sie Folgendes sehen können:

* Welche Komponenten werden verwendet und wo sie verwendet werden?

  Dies ist beispielsweise bei Tests nützlich.

* Wie Instanzen einer bestimmten Komponente verteilt sind

  Dies kann interessant sein, wenn auf bestimmten Seiten (d. h. &quot;umfangreichen Seiten&quot;) Leistungsprobleme auftreten.

* Identifizieren Sie Teile der Site mit häufigen/weniger häufigen Änderungen.
* Erfahren Sie, wie sich der Seiteninhalt im Laufe der Zeit entwickelt.

Alle Komponenten sind enthalten, dem Produktstandard und dem Projekt entsprechend. Mithilfe des Dialogfelds **Bearbeiten** kann der Benutzer auch einen **Stammpfad** festlegen, der den Startpunkt des Berichts definiert. Alle Komponenten unter diesem Stammpfad werden für den Bericht berücksichtigt.

![reportcomponent](assets/reportcomponent.png) ![reportcompentall](assets/reportcompentall.png)

### Speichernutzung {#disk-usage}

Der Bericht zur Festplattenauslastung zeigt Informationen zu den in Ihrem Repository gespeicherten Daten an.

Der Bericht beginnt im Stammverzeichnis ( / ) des Repositorys. Durch Klicken auf eine bestimmte Verzweigung können Sie innerhalb des Repositorys einen Drilldown durchführen (der aktuelle Pfad wird im Berichtstitel angezeigt).

![reportdiskusage](assets/reportdiskusage.png)

### Konsistenzprüfung {#health-check}

Dieser Bericht analysiert das aktuelle Anforderungsprotokoll

`<cq-installation-dir>/crx-quickstart/logs/request.log`

Damit können Sie die kostspieligsten Anforderungen innerhalb eines bestimmten Zeitraums identifizieren.

Um den Bericht zu erstellen, können Sie Folgendes angeben:

* **Zeitraum (Stunden)**

  Die Anzahl der zu analysierenden Stunden (Vergangenheit).

  Standard: `24`

* **max. Ergebnisse**

  Maximale Anzahl an Ausgabezeilen.

  Standard: `50`

* **max. Anforderungen**

  Maximale Anzahl der zu analysierenden Anforderungen.

  Standard: `-1` (alle)

* **E-Mail-Adresse**

  Senden Sie die Ergebnisse an eine E-Mail-Adresse.

  Optional; Standard: leer

* **Täglich ausführen um (hh:mm)**

  Geben Sie eine Zeit an, zu der der Bericht automatisch täglich ausgeführt werden soll.

  Optional; Standard: leer

![reporthhealth](assets/reporthealth.png)

### Seitenaktivitätsbericht {#page-activity-report}

Im Seitenaktivitätsbericht werden die Seiten und die auf ihnen vorgenommenen Aktionen aufgeführt.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) zu:

* Seite
* Zeit
* Typ
* Benutzer

Das bedeutet, dass Sie überwachen können:

* Die neuesten Änderungen.
* Autoren, die auf bestimmten Seiten arbeiten.
* Seiten, die in letzter Zeit nicht geändert wurden, sodass möglicherweise Handlungsbedarf besteht.
* Seiten, die am häufigsten/am seltensten geändert werden.
* Die meisten/am wenigsten aktiven Benutzer.

Der Seitenaktivitätsbericht übernimmt alle Informationen aus dem Auditprotokoll. Standardmäßig wird der Stammpfad im Administratorprotokoll unter `/var/audit/com.day.cq.wcm.core.page` konfiguriert.

![reportpageactivity](assets/reportpageactivity.png)

### Benutzergenerierter Inhaltsbericht {#user-generated-content-report}

Dieser Bericht enthält Informationen zu benutzergenerierten Inhalten, z. B. Kommentaren, Bewertungen oder Foren.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) auf:

* Datum
* IP-Adresse
* Seite
* Referrer
* Typ
* Benutzer Kennung

Ermöglicht Ihnen Folgendes:

* Ermitteln Sie, welche Seiten die meisten Kommentare erhalten.
* Einen Überblick über alle Kommentare gewinnen, die bestimmte Besucher der Website hinterlassen, und ob die Themen miteinander zusammenhängen
* Beurteilen, ob neue Inhalte Kommentare zur Folge haben, indem überwacht wird, wann Kommentare auf einer Seite vorgenommen werden

![reportusercontent](assets/reportusercontent.png)

### Benutzerbericht {#user-report}

Dieser Bericht bietet Informationen zu allen Benutzern, die sich mit einem Konto und/oder Profil registriert haben. Dies umfasst sowohl Autoren innerhalb Ihrer Organisation als auch externe Besucher.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) (sofern verfügbar) über:

* Alter
* Land
* Domain
* E-Mail
* Nachname
* Geschlecht
* [Generisch](#generic-column)
* Vorname
* Info
* Interesse
* Sprache
* NTLM-Hashcode
* Benutzer-ID 

Ermöglicht Ihnen Folgendes:

* Sehen Sie die demografische Ausbreitung Ihrer Benutzer.
* Berichte zu benutzerdefinierten Feldern, die Sie den Profilen hinzugefügt haben.

![reportusercanned](assets/reportusercanned.png)

#### Allgemeine Spalte {#generic-column}

Die **Generisch** -Spalte ist im Benutzerbericht verfügbar, sodass Sie auf benutzerdefinierte Informationen zugreifen können, die normalerweise über die [Benutzerprofile](/help/sites-administering/identity-management.md#profiles-and-user-accounts); zum Beispiel [Favoritenfarbe, wie unter Felder zur Profildefinition hinzufügen beschrieben](/help/sites-administering/identity-management.md#adding-fields-to-the-profile-definition).

Das Dialogfeld Generische Spalte wird geöffnet, wenn Sie eine der folgenden Aktionen ausführen:

* Ziehen Sie die Komponente &quot;Generisch&quot;aus dem Sidekick in den Bericht.
* Wählen Sie die Spalteneigenschaften für eine vorhandene generische Spalte aus.

![reportusrgenericcolm](assets/reportusrgenericcolm.png)

Über die Registerkarte **Definitionen** können Sie Folgendes festlegen:

* **Titel**

  Ihr eigener Titel für die generische Spalte.

* **Eigenschaft**

  Der Name der Eigenschaft wie er im Repository gespeichert wird, in der Regel innerhalb des Benutzerprofils.

* **Pfad**

  Diese Eigenschaft wird in der Regel aus `profile` entnommen.

* **Typ**

  Wählen Sie den Feldtyp als `String`, `Number`, `Integer` oder `Date` aus.

* **Standardaggregat**

  Dies legt die standardmäßig verwendete Zusammenfassung fest, wenn die Spalte in einem Bericht mit mindestens einer gruppierten Spalte nicht gruppiert ist. Wählen Sie die gewünschte Zusammenfassung als `Count`, `Minimum`, `Average`, `Maximum` oder `Sum` aus.

  *Anzahl* bedeutet bei einem `String`-Feld zum Beispiel, dass die Anzahl der einzelnen `String`-Werte für die Spalte im zusammengefassten Zustand angezeigt wird.

Im **Erweitert** können Sie auch die verfügbaren Aggregate und Filter definieren:

![reportusrgenericcolmextented](assets/reportusrgenericcolmextented.png)

### Bericht der Workflow-Instanz {#workflow-instance-report}

Auf diese Weise erhalten Sie einen kurzen Überblick über die einzelnen Instanzen von Workflows, die sowohl ausgeführt als auch abgeschlossen werden.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) zu:

* Abgeschlossen
* Dauer
* Initiator
* Modell
* Payload
* Gestartet
* Status

Dies bedeutet, dass Sie Folgendes tun können:

* Überwachen Sie die durchschnittliche Dauer von Workflows. In diesem Fall kann es zu Problemen mit dem Workflow kommen.

![reportworkflowintance](assets/reportworkflowintance.png)

### Workflow-Bericht {#workflow-report}

Dieser Bericht stellt wichtige Statistiken zu den auf Ihrer Instanz ausgeführten Workflows bereit.

![reportworkflow](assets/reportworkflow.png)

## Verwenden von Berichten in einer Veröffentlichungsumgebung {#using-reports-in-a-publish-environment}

Nachdem Sie die Berichte entsprechend Ihren spezifischen Anforderungen konfiguriert haben, können Sie sie aktivieren, um die Konfiguration in die Veröffentlichungsumgebung zu übertragen.

>[!CAUTION]
>
>Wenn Sie möchten **Historische Daten** für die Veröffentlichungsumgebung und **Beenden** den Bericht in der Autorenumgebung vor der Aktivierung der Seite.

Der entsprechende Bericht ist dann unter

`/etc/reports`

Der Bericht Benutzergenerierte Inhalte kann beispielsweise unter folgendem Link eingesehen werden:

`http://localhost:4503/etc/reports/ugcreport.html`

In diesem Bericht werden nun Daten erfasst, die aus der Veröffentlichungsumgebung erfasst wurden.

Da in der Veröffentlichungsumgebung keine Berichtskonfiguration zulässig ist, wird die **Bearbeiten** und **Beenden** -Schaltflächen sind nicht verfügbar. Sie können allerdings den **Zeitraum** und das **Intervall** für die Berichte zu **früheren Daten** auswählen, wenn Momentaufnahmen erfasst werden.

![reportsucgpublish](assets/reportsucgpublish.png)

>[!CAUTION]
>
>Der Zugriff auf diese Berichte kann ein Sicherheitsproblem sein. Daher empfiehlt Adobe, den Dispatcher so zu konfigurieren, dass `/etc/reports` steht externen Besuchern nicht zur Verfügung. Weitere Informationen finden Sie unter [Sicherheitscheckliste](security-checklist.md).

## Für die Ausführung von Berichten erforderliche Berechtigungen {#permissions-needed-for-running-reports}

Die benötigten Berechtigungen hängen von der Aktion ab:

* Berichtsdaten werden mit den Berechtigungen des aktuellen Benutzers erfasst.
* Historische Daten werden mit den Berechtigungen des Benutzers erfasst, der den Bericht abgeschlossen hat.

In einer standardmäßigen AEM-Installation sind die folgenden Berechtigungen für die Berichte voreingestellt:

* **Benutzerbericht**

  `user administrators`: Lesen und Schreiben

* **Seitenaktivitätsbericht**

  `contributors`: Lesen und Schreiben

* **Komponentenbericht**

  `contributors`: Lesen und Schreiben

* **Benutzergenerierter Inhaltsbericht**

  `contributors`: Lesen und Schreiben

* **Bericht der Workflow-Instanz**

  `workflow-users`: Lesen und Schreiben

Alle Mitglieder der `administrators` haben die erforderlichen Berechtigungen zum Erstellen von Berichten.
