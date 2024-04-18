---
title: Reporting
description: Erfahren Sie, wie Sie mit Reporting in Adobe Experience Manager arbeiten (AEM).
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: 2a0bf59d-8829-4142-9cb4-dcef90f53ae9
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2782'
ht-degree: 98%

---

# Reporting {#reporting}

Um Ihnen bei der Überwachung und Analyse des Status Ihrer Instanz zu helfen, stellt Adobe Experience Manager (AEM) eine Auswahl von Standardberichten bereit, die für Ihre individuellen Anforderungen konfiguriert werden können:

* [Komponentenbericht](#component-report)
* [Speichernutzung](#disk-usage)
* [Konsistenzprüfung](#health-check)
* [Seitenaktivitätsbericht](#page-activity-report)
* [Bericht für nutzergenerierte Inhalte](#user-generated-content-report)
* [Benutzerbericht](#user-report)
* [Bericht der Workflow-Instanz](#workflow-instance-report)
* [Workflow-Bericht](#workflow-report)

>[!NOTE]
>
>Diese Berichte sind nur in der klassischen Benutzeroberfläche verfügbar. Informationen zur Systemüberwachung und zum Reporting in der modernen Benutzeroberfläche finden Sie unter [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

Über die Konsole **Tools** kann auf alle Berichte zugegriffen werden. Wählen Sie im linken Bereich die Option **Berichte** aus und doppelklicken Sie dann im rechten Bereich auf den erforderlichen Bericht, um ihn zur Anzeige und/oder Konfiguration zu öffnen.

Neue Instanzen eines Berichts können auch über die Konsole **Tools** erstellt werden. Wählen Sie im linken Bereich die Option **Berichte** und dann in der Symbolleiste die Option **Neu** aus. Legen Sie einen **Titel** und **Namen** fest, wählen Sie den benötigten Berichtstyp aus und klicken Sie dann auf **Erstellen**. Ihre neue Berichtsinstanz wird in der Liste angezeigt. Doppelklicken Sie zum Öffnen darauf und ziehen Sie dann eine Komponente aus dem Sidekick, um die erste Spalte zu erstellen und mit der Berichtsdefinition zu beginnen.

>[!NOTE]
>
>Zusätzlich zu den vorkonfigurierten AEM-Standardberichten können Sie auch [Ihre eigenen (neuen) Berichte entwickeln](/help/sites-developing/dev-reports.md).

## Die Grundlagen der Berichtsanpassung {#the-basics-of-report-customization}

Es stehen verschiedene Berichtsformate zur Verfügung. Die folgenden Berichte nutzen alle Spalten, die wie in den folgenden Abschnitten beschrieben angepasst werden können:

* [Komponentenbericht](#component-report)
* [Seitenaktivitätsbericht](#page-activity-report)
* [Bericht für nutzergenerierte Inhalte](#user-generated-content-report)
* [Benutzerbericht](#user-report)
* [Bericht der Workflow-Instanz](#workflow-instance-report)

>[!NOTE]
>
>Die folgenden Berichte verfügen alle über ihr eigenes Format und ihre eigene Anpassung:
>
>
>* Die [Konsistenzprüfung](#health-check) nutzt Auswahlfelder, um die Daten anzugeben, zu denen Sie einen Bericht erstellen möchten.
>* Der [Festplattenauslastungsbericht](#disk-usage) verwendet Verknüpfungen für einen Drilldown durch die Repository-Struktur.
>* Der [Workflow-Bericht](/help/sites-administering/reporting.md#workflow-report) bietet einen Überblick über die Workflows, die in Ihrer Instanz ausgeführt werden.
>
>Die folgenden Verfahren zur Spaltenkonfiguration sind also nicht geeignet. Weitere Informationen finden Sie in den Beschreibungen der einzelnen Berichte.

### Auswählen und Positionieren der Datenspalten {#selecting-and-positioning-the-data-columns}

Spalten können in allen standardmäßigen und benutzerdefinierten Berichten hinzugefügt oder neu positioniert bzw. daraus entfernt werden.

Auf der Registerkarte **Komponenten** im Sidekick (verfügbar auf der Berichtsseite) sind alle Kategorien von Daten aufgeführt, die als Spalten ausgewählt werden können.

So ändern Sie die Datenauswahl:

* Ziehen Sie zum Hinzufügen einer Spalte die erforderliche Komponente aus dem Sidekick und legen Sie sie an der gewünschten Position ab.

   * Ein grünes Häkchen steht für eine gültige Position und durch zwei Pfeile wird genau gezeigt, wo die Platzierung erfolgt.
   * Ein rotes Kreuzsymbol steht für eine ungültige Position.

* Um eine Spalte zu verschieben, klicken Sie auf die Überschrift, halten Sie sie gedrückt und ziehen Sie sie an die neue Position.
* Um eine Spalte zu entfernen, klicken Sie auf den Spaltentitel, halten Sie ihn gedrückt und ziehen Sie ihn in den Kopfzeilenbereich des Berichts. (Ein rotes Minuszeichen weist darauf hin, dass die Position ungültig ist.) Lassen Sie die Maustaste los. Daraufhin werden Sie über das Dialogfeld „Komponenten löschen“ aufgefordert, die Löschung der Spalte zu bestätigen.

### Spalten-Dropdown-Menü {#column-drop-down-menu}

Jede Spalte im Bericht verfügt über ein Dropdown-Menü. Es wird angezeigt, wenn der Mauszeiger über die Zelle mit dem Spaltentitel bewegt wird.

Ganz rechts neben der Zelle mit dem Titel wird eine Pfeilspitze angezeigt (nicht mit der Pfeilspitze direkt rechts neben dem Titeltext zu verwechseln, die den [aktuellen Sortiermechanismus](#sorting-the-data) anzeigt).

![reportcolumnsort](assets/reportcolumnsort.png)

Die im Menü verfügbaren Optionen hängen von der (während der Projektentwicklung vorgenommenen) Konfiguration der Spalte ab. Alle ungültigen Optionen sind abgeblendet (ausgegraut).

### Sortieren der Daten {#sorting-the-data}

Die Daten können durch folgende Möglichkeiten nach einer bestimmten Spalte sortiert werden:

* Durch Klicken auf die jeweilige Spaltenüberschrift wechselt die Sortierung von aufsteigend zu absteigend, was durch eine Pfeilspitze direkt neben dem Titeltext angezeigt wird.
* Verwenden Sie das [Dropdown-Menü der Spalte](#column-drop-down-menu), um zwischen **Aufsteigend sortieren** und **Absteigend sortieren** auszuwählen. Dies wird wiederum durch eine Pfeilspitze direkt neben dem Titeltext angezeigt.

### Gruppen und das aktuelle Datendiagramm {#groups-and-the-current-data-chart}

In den entsprechenden Spalten können Sie im [Dropdown-Menü der Spalte](#column-drop-down-menu) die Option **Nach Spalte gruppieren** auswählen. Hierdurch werden die Daten nach jedem einzelnen Wert innerhalb dieser Spalte gruppiert. Sie können mehrere Spalten auswählen, die gruppiert werden sollen. Die Option ist abgeblendet (ausgegraut), wenn die Daten in der Spalte nicht geeignet sind. Das heißt, jeder Eintrag ist verschieden und einzigartig, sodass keine Gruppen gebildet werden können. Ein Beispiel hierfür ist die Spalte „Benutzer-ID“ des Benutzerberichts.

Nach der Gruppierung mindestens einer Spalte wird auf Grundlage dieser Gruppierung ein Tortendiagramm der **aktuellen Daten** generiert. Wenn mehrere Spalten gruppiert werden, wird dies ebenfalls im Diagramm angegeben.

![reportuser](assets/reportuser.png)

Wenn Sie Ihren Mauszeiger über das Tortendiagramm bewegen, wird der aggregierte Wert für das entsprechende Segment angezeigt. Hierbei wird das aktuell für die Spalte definierte Aggregat verwendet, z. B. Anzahl, Minimum oder Durchschnitt.

### Filter und Aggregate {#filters-and-aggregates}

In den entsprechenden Spalten können Sie außerdem **Filtereinstellungen** und/oder **Aggregate** über das [Dropdown-Menü der Spalte](#column-drop-down-menu) konfigurieren.

#### Filter {#filters}

Mithilfe der Filtereinstellungen können Sie die Kriterien für anzuzeigende Einträge festlegen. Folgende Operatoren stehen zur Verfügung:

* `contains`
* `equals`

![reportfilter](assets/reportfilter.png)

Sie können wie folgt einen Filter festlegen:

1. Wählen Sie den gewünschten Operator aus der Dropdown-Liste aus.
1. Geben Sie den Text ein, nach dem gefiltert werden soll.
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

Ein Diagramm zu den Änderungen an Ihren Daten im Laufe der Zeit kann unter **Frühere Daten** angezeigt werden. Dieses wird von in regelmäßigen Intervallen aufgenommenen Momentaufnahmen abgeleitet.

Die Daten werden:

* von der ersten sortierten Spalte erfasst, sofern verfügbar, bzw. andernfalls von der ersten (nicht gruppierten) Spalte
* nach der entsprechenden Spalte sortiert

Der Bericht kann wie folgt generiert werden:

1. Legen Sie die Option **Gruppierung** für die erforderliche Spalte fest.
1. **Bearbeiten** Sie die Konfiguration so, dass Sie stündliche oder tägliche Momentaufnahmen definieren können.
1. **Beenden…** Sie die Definition, um die Sammlung von Momentaufnahmen zu starten.

   Die roten/grünen Reglerschaltflächen oben links zeigen an, wenn Momentaufnahmen erfasst werden.

Das daraus resultierende Diagramm wird unten rechts angezeigt:

![reporttrends](assets/reporttrends.png)

Wenn die Datenerfassung begonnen hat, können Sie Folgendes auswählen:

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

* Verwenden Sie erneut **Beenden…**, um die Sammlung neu zu initialisieren.

  Durch **Beenden** wird die Berichtsstruktur (d. h. die dem Bericht zugewiesenen Spalten und welche gruppiert, sortiert, gefiltert sind usw.) „eingefroren“ und mit der Erstellung der Momentaufnahmen begonnen.

* Öffnen Sie das Dialogfeld **Bearbeiten**, um **Keine Datenmomentaufnahmen** auszuwählen und die Sammlung zu beenden, bis diese erforderlich ist.

  Durch **Bearbeiten** wird lediglich das Anfertigen von Momentaufnahmen ein- oder ausgeschaltet. Wenn das Anfertigen von Momentaufnahmen erneut eingeschaltet wird, wird der Status des Berichts bei dessen letzter Fertigstellung zum Anfertigen weiterer Momentaufnahmen verwendet.

>[!NOTE]
>
>Die Momentaufnahmen werden unter `/var/reports/...` gespeichert, wo der übrige Pfad den Pfad des jeweiligen Berichts sowie die bei der Fertigstellung des Berichts erstellte ID wiedergibt.
>
>
>Alte Momentaufnahmen können manuell gelöscht werden, wenn Sie sicher sind, dass Sie diese Instanzen nicht mehr benötigen.

>[!NOTE]
>
>Die vorkonfigurierten Berichte sind nicht leistungsintensiv, es wird jedoch dennoch empfohlen, in einer Produktionsumgebung tägliche Momentaufnahmen zu verwenden. Führen Sie diese täglichen Momentaufnahmen nach Möglichkeit zu einer Tageszeit aus, zu der auf Ihrer Website nicht viel Aktivität vorhanden ist. Dies kann mit dem `Daily snapshots (repconf.hourofday)` Parameter für **Day CQ-Berichtkonfiguration**. Siehe [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für weitere Informationen zur Konfiguration.

#### Anzeigelimits {#display-limits}

Das Erscheinungsbild des Berichts zu historischen Daten kann sich aufgrund von festlegbaren Beschränkungen auch geringfügig ändern – je nach der Anzahl der Ergebnisse zum ausgewählten Zeitraum.

Jede horizontale Zeile wird als Reihe bezeichnet (und entspricht einem Eintrag in der Diagrammlegende) und jede vertikale Spalte von Punkten stellt die zusammengefassten Momentaufnahmen dar.

![chlimage_1-44](assets/chlimage_1-44.png)

Damit das Diagramm über längere Zeiträume hinweg „sauber“ bleibt, können Beschränkungen festgelegt werden. Für die Standardberichte lauten diese wie folgt:

* horizontale Reihe – Standardwert und Systemmaximum ist `9`

* vertikale zusammengefasste Momentaufnahmen – Standardwert ist `35` (pro horizontaler Reihe)

Wenn also die (entsprechenden) Beschränkungen überschritten werden:

* werden die Punkte nicht angezeigt
* zeigt die Legende zu den historischen Daten ggf. eine andere Anzahl an Einträgen an als das aktuelle Datendiagramm

![chlimage_1-45](assets/chlimage_1-45.png)

In benutzerspezifischen Berichten kann auch der Wert **Insgesamt** für die ganze Reihe angezeigt werden. Dies wird als eine Reihe angezeigt (horizontale Linie und Eintrag in der Legende).

>[!NOTE]
>
>Für benutzerspezifische Berichte können die Beschränkungen anders festgelegt werden.

### Bearbeiten (Bericht) {#edit-report}

Über die Schaltfläche **Bearbeiten** wird das Dialogfeld **Bericht bearbeiten** geöffnet.

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

     Die Berichtsdaten werden bei jeder Aktualisierung der Berichtsdefinition aktualisiert.

   * **Daten manuell aktualisieren**

     Diese Option kann verwendet werden, um bei einer großen Datenmenge durch automatische Aktualisierungsvorgänge verursachte Verzögerungen zu verhindern.

     Diese Auswahl zeigt an, dass die Berichtsdaten manuell aktualisiert werden müssen, wenn sich ein beliebiger Aspekt der Berichtskonfiguration verändert hat. Außerdem bedeutet dies, dass die Berichtstabelle bei jeder Änderung eines Konfigurationsaspekts ausgeblendet wird.

     Wenn diese Option ausgewählt ist, wird die Schaltfläche **[Daten laden](#load-data)** (neben **Bearbeiten** im Bericht) angezeigt. Mit **Daten laden** werden die Daten geladen und die angezeigten Berichtsdaten werden aktualisiert.

* **Momentaufnahmen**
Sie können festlegen, wie oft Momentaufnahmen angefertigt werden sollen: täglich, stündlich oder gar nicht.

### Daten laden {#load-data}

Die Schaltfläche **Daten laden** wird nur angezeigt, wenn **Daten manuell aktualisieren** unter **[Bearbeiten](#edit-report)** ausgewählt wurde.

![chlimage_1-46](assets/chlimage_1-46.png)

Durch Klicken auf **Daten laden** werden die Daten neu geladen und der angezeigte Bericht aktualisiert.

Die Auswahl von „Daten manuell aktualisieren“ bedeutet Folgendes:

1. Wenn Sie die Berichtskonfiguration ändern, wird die Tabelle der Berichtsdaten ausgeblendet.

   Wenn Sie beispielsweise den Sortiermechanismus einer Spalte ändern, werden die Daten nicht angezeigt.

1. Wenn die Berichtsdaten erneut angezeigt werden sollen, müssen Sie zum erneuten Laden der Daten auf **Daten laden** klicken.

### Fertigstellen (Bericht) {#finish-report}

Wenn Sie den Bericht **fertigstellen**, geschieht Folgendes:

* Die Berichtsdefinition *ab diesem Zeitpunkt* wird zum Erstellen der Momentaufnahmen verwendet. Danach können Sie die Arbeit an einer Berichtsdefinition fortsetzen, da diese von den Momentaufnahmen getrennt ist.
* Alle vorhandenen Momentaufnahmen werden entfernt.
* Es werden neue Momentaufnahmen für [frühere Daten](#historic-data) erfasst.

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

* Welche Komponenten werden wo verwendet?

  Dies ist beispielsweise bei Tests nützlich.

* Wie Instanzen einer bestimmten Komponente verteilt sind

  Dies kann interessant sein, wenn bei bestimmten Seiten (d. h. „umfangreichen Seiten“) Leistungsprobleme auftreten.

* Welche Teile der Site weisen häufige/weniger häufige Veränderungen auf?
* Wie verändert sich Seiteninhalt sich im Laufe der Zeit?

Alle Komponenten werden einbezogen, die standardmäßig zum Produkt gehörenden und die projektspezifischen. Mithilfe des Dialogfelds **Bearbeiten** kann der Benutzer auch einen **Stammpfad** festlegen, der den Startpunkt des Berichts definiert. Alle Komponenten unter diesem Stammpfad werden für den Bericht berücksichtigt.

![reportcomponent](assets/reportcomponent.png) ![reportcompentall](assets/reportcompentall.png)

### Speichernutzung {#disk-usage}

Der Festplattenauslastungsbericht zeigt Informationen zu den innerhalb Ihres Repositorys gespeicherten Daten an.

Der Bericht beginnt im Stamm ( / ) des Repositorys. Durch Klicken auf eine bestimmte Verzweigung können Sie innerhalb des Repositorys einen Drilldown durchführen (der aktuelle Pfad wird im Berichtstitel wiedergegeben).

![reportdiskusage](assets/reportdiskusage.png)

### Konsistenzprüfung {#health-check}

Dieser Bericht analysiert das aktuelle Anforderungsprotokoll

`<cq-installation-dir>/crx-quickstart/logs/request.log`

So können Sie die aufwendigsten Anfragen innerhalb eines bestimmten Zeitraums identifizieren.

Zum Generieren des Berichts können Sie Folgendes festlegen:

* **Zeitraum (Stunden)**

  Die zu analysierende Anzahl von (vergangenen) Stunden.

  Standard: `24`

* **max. Ergebnisse**

  Maximale Anzahl an Ausgabezeilen.

  Standard: `50`

* **max. Anforderungen**

  Maximale Anzahl an zu analysierenden Anfragen.

  Standard: `-1` (alle)

* **E-Mail-Adresse**

  Senden Sie die Ergebnisse an eine E-Mail-Adresse.

  Optional; Standard: leer

* **Täglich ausführen um (hh:mm)**

  Geben Sie eine Uhrzeit an, zu der der Bericht automatisch täglich ausgeführt werden soll.

  Optional; Standard: leer

![reporthhealth](assets/reporthealth.png)

### Seitenaktivitätsbericht {#page-activity-report}

Im Seitenaktivitätsbericht werden die Seiten und die auf ihnen vorgenommenen Aktionen aufgeführt.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) zu:

* Seite
* Zeit
* Typ
* Benutzer

Bedeutet, dass Sie Folgendes überwachen können:

* Die neuesten Änderungen.
* Autorinnen und Autoren, die auf bestimmten Seiten arbeiten.
* Seiten, die in letzter Zeit nicht geändert wurden, sodass möglicherweise Handlungsbedarf besteht.
* Seiten, die am häufigsten/am seltensten geändert werden.
* Die am meisten/am wenigsten aktiven Benutzenden.

Der Seitenaktivitätsbericht übernimmt alle Informationen aus dem Administratorprotokoll. Standardmäßig wird der Stammpfad im Administratorprotokoll unter `/var/audit/com.day.cq.wcm.core.page` konfiguriert.

![reportpageactivity](assets/reportpageactivity.png)

### Bericht für nutzergenerierte Inhalte {#user-generated-content-report}

Dieser Bericht liefert Informationen über nutzergenerierte Inhalte, seien es Kommentare, Bewertungen oder Foren.

[Informationsspalten](#selecting-and-positioning-the-data-columns) zu:

* Datum
* IP-Adresse
* Seite
* Referrer
* Typ
* Benutzerkennung

Ermöglicht Ihnen Folgendes:

* Sehen, welche Seiten die meisten Kommentare erhalten.
* Einen Überblick über alle Kommentare gewinnen, die bestimmte Besucher der Website hinterlassen, und ob die Themen miteinander zusammenhängen
* Beurteilen, ob neue Inhalte Kommentare zur Folge haben, indem überwacht wird, wann Kommentare auf einer Seite vorgenommen werden

![reportusercontent](assets/reportusercontent.png)

### Benutzerbericht {#user-report}

Dieser Bericht bietet Informationen zu allen Benutzern, die sich mit einem Konto und/oder Profil registriert haben. Dies umfasst sowohl Autoren innerhalb Ihrer Organisation als auch externe Besucher.

[Informationsspalten](#selecting-and-positioning-the-data-columns) (sofern verfügbar) zu:

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

* Die demografische Verteilung Ihrer Benutzenden anzeigen zu lassen
* Berichte zu benutzerdefinierten Feldern, die Sie den Profilen hinzugefügt haben.

![reportusercanned](assets/reportusercanned.png)

#### Generische Spalte {#generic-column}

Die **generische Spalte** ist im Benutzerbericht verfügbar, sodass Sie auf benutzerdefinierte Informationen zugreifen können, normalerweise aus den [Benutzerprofilen](/help/sites-administering/identity-management.md#profiles-and-user-accounts); zum Beispiel [Favoritenfarbe, wie unter „Hinzufügen von Feldern zur Profildefinition“ beschrieben](/help/sites-administering/identity-management.md#adding-fields-to-the-profile-definition).

Das Dialogfeld „Generische Spalte“ wird geöffnet, wenn Sie eine der folgenden Aktionen ausführen:

* Die Komponente „Generisch“ vom Sidekick in den Bericht ziehen
* Die Spalteneigenschaften zu einer vorhandenen generischen Spalte auswählen

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

Auf der Registerkarte **Erweitert** können Sie außerdem die verfügbaren Zusammenfassungen und Filter festlegen:

![reportusrgenericcolmextented](assets/reportusrgenericcolmextented.png)

### Bericht der Workflow-Instanz {#workflow-instance-report}

Dies bietet Ihnen einen knappen Überblick und stellt Ihnen Informationen zu den einzelnen Instanzen der Workflows bereit – sowohl zu den laufenden als auch zu den abgeschlossenen.

[Spalten mit Informationen](#selecting-and-positioning-the-data-columns) zu:

* Abgeschlossen
* Dauer
* Initiator
* Modell
* Payload
* Gestartet
* Status

Dies bedeutet, dass Sie Folgendes tun können:

* Überwachen der durchschnittlichen Dauer von Workflows. Wenn dies regelmäßig passiert, können Probleme innerhalb des Workflows hervorgehoben werden.

![reportworkflowintance](assets/reportworkflowintance.png)

### Workflow-Bericht {#workflow-report}

Dieser Bericht stellt wichtige Statistiken zu den auf Ihrer Instanz ausgeführten Workflows bereit.

![reportworkflow](assets/reportworkflow.png)

## Verwenden von Berichten in einer Veröffentlichungsumgebung {#using-reports-in-a-publish-environment}

Sobald Sie die Berichte entsprechend Ihren spezifischen Anforderungen konfiguriert haben, können Sie sie für die Übertragung der Konfiguration in die Publishing-Umgebung aktivieren.

>[!CAUTION]
>
>Wenn Sie **historische Daten** für die Veröffentlichungsumgebung wünschen, dann **beenden** Sie den Bericht in der Autorenumgebung, bevor Sie die Seite aktivieren.

Der entsprechende Bericht ist dann verfügbar unter

`/etc/reports`

Der Bericht für nutzergenerierte Inhalte ist beispielsweise hier zu finden:

`http://localhost:4503/etc/reports/ugcreport.html`

In dem Bericht sind Daten enthalten, die aus der Veröffentlichungsumgebung erfasst wurden.

Da in der Veröffentlichungsumgebung keine Berichtskonfiguration zulässig ist, sind die Schaltflächen **Bearbeiten** und **Beenden** nicht verfügbar. Sie können allerdings den **Zeitraum** und das **Intervall** für die Berichte zu **früheren Daten** auswählen, wenn Momentaufnahmen erfasst werden.

![reportsucgpublish](assets/reportsucgpublish.png)

>[!CAUTION]
>
>Der Zugriff auf diese Berichte kann ein Sicherheitsproblem darstellen. Daher empfiehlt Adobe die Konfiguration des Dispatchers, sodass `/etc/reports` für externe Besucherinnen und Besucher nicht verfügbar ist. Weitere Informationen finden Sie unter [Sicherheitscheckliste](security-checklist.md).

## Für die Ausführung von Berichten erforderliche Berechtigungen {#permissions-needed-for-running-reports}

Die benötigten Berechtigungen hängen von der Aktion ab:

* Berichtsdaten werden mit den Berechtigungen der bzw. des aktuellen Benutzenden erfasst.
* Verlaufsdaten werden mit den Berechtigungen der Person erfasst, die den Bericht abgeschlossen hat.

In einer standardmäßigen AEM-Installation sind die folgenden Berechtigungen für die Berichte voreingestellt:

* **Benutzerbericht**

  `user administrators`: Lesen und Schreiben

* **Seitenaktivitätsbericht**

  `contributors`: Lesen und Schreiben

* **Komponentenbericht**

  `contributors`: Lesen und Schreiben

* **Bericht für nutzergenerierte Inhalte**

  `contributors`: Lesen und Schreiben

* **Bericht der Workflow-Instanz**

  `workflow-users`: Lesen und Schreiben

Alle Mitglieder der Gruppe `administrators` verfügen über die Rechte zum Erstellen von Berichten.
