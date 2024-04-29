---
title: Verwenden von Diagrammen in einem adaptiven Formular.
description: Verwenden Sie Diagramme in einem adaptiven Formular, um Ihr Formular informativer zu gestalten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Adaptive Forms, Foundation Components
exl-id: 973d5ddb-cbcc-454d-859f-144442828a1a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2005'
ht-degree: 100%

---

# Diagramme in adaptiven Formularen {#af-charts}

![Hero_Image](assets/charts_hero_image.jpg)

Ein Diagramm oder Graph ist eine visuelle Darstellung von Daten. So können Sie große Mengen an Informationen übersichtlich darstellen und komplexe Daten besser visualisieren, auswerten und analysieren.
Das AEM Forms-Add-on-Paket bietet eine vorkonfigurierte Diagrammkomponente. Sie können diese in Ihren adaptiven Formularen und Dokumenten für die visuelle Darstellung zweidimensionaler Daten in **wiederholbaren Bedienfeldern** und **Tabellen** verwenden. Mit der Diagrammkomponente können Sie folgende Arten von Diagrammen hinzufügen und konfigurieren:

1. Tortendiagramm
1. Säulendiagramm
1. Donut
1. Balken
1. Line
1. Linie und Punkt
1. Punkt
1. Flächendiagramm

Die Diagrammkomponente unterstützt und bietet integrierte statistische Funktionen (Summe, Mittelwert, Maximum, Minimum, Modus, Median, Bereich und Häufigkeit), um Werte in einem Diagramm zu berechnen und darzustellen. Zusätzlich zu den Standardfunktionen können Sie Ihre eigenen benutzerdefinierten Funktionen entwickeln und für die Verwendung in Diagrammen freigeben.

Als Nächstes sehen wir uns an, wie die Diagrammkomponente hinzugefügt und konfiguriert wird.

## Hinzufügen eines Diagramms {#add-chart}

Die Diagrammkomponente steht in der AEM-Seitenleiste standardmäßig zur Verfügung. Sie können die Diagrammkomponente im Bearbeitungsmodus von der AEM-Seitenleiste auf das adaptive Dokument oder Formular ziehen und dort ablegen. Wenn Sie die Komponente ablegen, erstellt sie einen Platzhalter für ein Diagramm.

## Konfigurieren eines Diagramms {#configure-chart}

>[!NOTE]
> 
> Bevor Sie das Diagramm konfigurieren, sorgen Sie dafür, dass das Bedienfeld oder die Tabellenzeile, für die Sie das Diagramm konfigurieren, auf wiederholbar eingestellt ist. Sie können die minimalen und maximalen Werte für wiederholbare Bedienfelder oder Tabellenzeilen im Dialogfeld „Komponente bearbeiten“ auf der Registerkarte „Wiederholungseinstellungen“ angeben.

Um das Diagramm zu konfigurieren, klicken Sie auf die Diagrammkomponente und dann auf ![Einstellungen](cmppr1.png). Daraufhin wird das Dialogfeld „Diagramm bearbeiten“ geöffnet. Es enthält etwa die Registerkarten „Titel und Text“, „Konfiguration“, „Erweiterte Optionen“ und „Formatieren“, mit denen Sie das Diagramm konfigurieren können.

### Allgemein {#basic}

Auf der Registerkarte „Allgemein“ können Sie die folgenden Eigenschaften konfigurieren:

![Diagrammeigenschaften](assets/chart-properties.png)

* **Elementname**: Eine Kennung für das Diagrammelement in der JCR-Inhaltsstruktur. Sie ist zwar im Diagramm nicht sichtbar, jedoch nützlich, wenn von anderen Komponenten, Skripten und SOM-Ausdrücken auf das Element verwiesen wird.
* **Diagrammtyp**: Gibt den Diagrammtyp an, den Sie erstellen möchten. Es kann ein Kreisdiagramm, Ringdiagramm, Balkendiagramm, Säulendiagramm, Liniendiagramm, Linien- und Punktdiagramm, Punktdiagramm oder Flächendiagramm als Typ festgelegt werden. In diesem Beispiel ist als Diagrammtyp das Säulendiagramm angegeben.
* **Sich wiederholender Zeilenname/Bedienfeldname für Datenquelle**: Gibt den Elementnamen der Tabellenzeile oder des wiederholbaren Bedienfelds an, aus dem die Daten bezogen werden. In diesem Beispiel ist „statementDetails“ der Elementname der wiederholbaren Zeile in der Tabelle mit den Anweisungsdetails.
* **X-Achse > Titel**: Gibt den Titel für die X-Achse an. In diesem Beispiel lautet der Titel für die X-Achse „Kategorie“.
* **X-Achse > Feld**: Gibt den Elementnamen des auf der X-Achse abzubildenden Felds (oder der Zelle in einer Tabelle) an. Im Beispiel werden Kategorien auf der X-Achse konfiguriert. Der Elementname für die Tabellenzelle in der Spalte der Beispieltabelle ist „Kategorie“.
* **X-Achse > Funktion verwenden**: Gibt die statistische Funktion an, die für die Berechnung der Werte auf der X-Achse zu verwenden ist. Im Beispiel ist die ausgewählte Option „Ohne“. Weitere Informationen zu den Funktionen finden Sie unter „Verwenden von Funktionen im Diagramm“.
* **Y-Achse > Titel**: Gibt den Titel für die Y-Achse an. In diesem Beispiel ist der Name für die Y-Achse „Spesenkonto“.
* **Y-Achse > Feld**: Gibt den Elementnamen des auf der Y-Achse abzubildenden Felds (oder der Zelle in einer Tabelle) an. Im Beispiel konfigurieren Sie den Betrag auf der y-Achse.  Der Elementname für die Zelle in der Betrag-Spalte der Beispieltabelle ist „Betrag“.
* **Y-Achse > Funktion verwenden**: Gibt die statistische Funktion an, die für die Berechnung der Werte auf der y-Achse zu verwenden ist.  In diesem Beispiel wird der Betrag aus jeder Kategorie zusammengerechnet und der berechnete Wert wird auf der y-Achse abgebildet.  Wählen Sie also die Option „Summe“ aus der Dropdown-Liste „Funktion verwenden“.  Weitere Informationen zu den Funktionen finden Sie unter „Verwenden von Funktionen im Diagramm“.
* **Legendenposition:** Legt die Position der Legende in Bezug auf das Diagramm fest. Die verfügbaren Optionen sind rechts, links, oben und unten.
* **Legende anzeigen**: Zeigt eine Legende für das Diagramm an, wenn aktiviert.
* **QuickInfo**: Gibt das Format an, in dem die QuickInfo beim Bewegen der Maus über einen Datenpunkt in der Grafik angezeigt wird. Der Standardwert ist **\${x}(\${y})**. Je nach Diagrammtyp werden die Variablen **\${x}** und **\${y}** dynamisch durch die entsprechenden Werte für die x-Achse und y-Achse ersetzt und in der QuickInfo angezeigt, wenn Sie den Mauszeiger über einen Punkt, ein Segment oder einen Balken im Diagramm bewegen. Wie im folgenden Beispiel wird die QuickInfo als **Einzelhandel(5870)** angezeigt, wenn Sie den Mauszeiger in die Spalte Einzelhandelsgeschäfte halten. Wenn Sie die QuickInfo deaktivieren möchten, lassen Sie das Feld „Quickinfo“ leer. Diese Option ist nicht auf Linien- und Bereichsdiagramme anwendbar.
* **Spezifische Diagrammkonfigurationen**: Neben den allgemeinen Konfigurationen sind die folgenden spezifischen Diagrammkonfigurationen verfügbar:
* **Innerer Radius**: Für Ringdiagramme verfügbar, um den Radius (in Pixeln) für den inneren Kreis des Diagramms anzugeben.
* **Linienfarbe**: Verfügbar für Linien-, Linien- und Punkt- sowie Bereichsdiagramme, um den hexadezimalen Farbwert für die Linie im Diagramm anzugeben.
* **Punktfarbe**: Verfügbar für Punkt- und Liniendiagramme sowie Punktdiagramme, um den hexadezimalen Farbwert für den Punkt im Diagramm anzugeben.
* **Bereichsfarbe**: Verfügbar für Bereichsdiagramme, um den hexadezimalen Farbwert für den Bereich unter der Linie im Diagramm anzugeben.
* **CSS-Klasse**: Geben Sie den Namen einer CSS-Klasse im CSS-Klassen-Feld an, um benutzerdefinierte Stile im Diagramm anzuwenden.

### Konfiguration {#configuration}

In der Registerkarte „Grundeinstellungen“ definieren Sie die Art des Diagramms, Quellbedienfelds bzw. der Tabellenzeile, die Daten, die Werte, die auf der x-Achse und y-Achse des Diagramms angezeigt werden können, und je nachdem auch die statistische Funktion, um die Werte für die grafische Darstellung auf dem Diagramm zu berechnen.

Im Folgenden werden wir im Einzelnen auf die Informationen eingehen, die zu dieser Registerkarte gehören und als Beispiel eine wiederholbare Tabelle in einem Kreditkartenauszug geben.  Nehmen wir an, dass Sie ein Diagramm erstellen möchten, um die Gesamtkosten in den verschiedenen Kategorien im detaillierten Bereich eines Kreditkartenauszugs wie unten dargestellt anzuzeigen und zu erkennen.

Dazu müssen Sie Kategorien auf der x-Achse und der y-Achse ebenso wie die Gesamtausgaben in jeder Kategorie grafisch darstellen.

![Details zur Anweisung](assets/statement-details.png)

Der Kreditkartenauszug, der in diesem Beispiel verwendet wird, ist ein adaptives Formulardokument und der detaillierte Bereich eine Tabelle, die im Authoring-Modus wie folgt aussieht.

![Authoring von Details zur Anweisung](assets/statement-details-authoring.png)

Gehen wir einmal davon aus, dass die folgenden Anforderungen und die Bedingungen für das Generieren des Diagramms von Bedeutung sind:

* Das Diagramm zeigt die Gesamtkosten in jeder Kategorie in der Tabelle mit den Einzelheiten des Auszugs an.
* Der Diagrammtyp ist Säule, es kann aber auch ein anderer Diagrammtyp ausgewählt werden.
* Die Tabellenzeile in der Tabelle mit den Einzelheiten des Auszugs ist wiederholbar. Sie können dies im Feld „Wiederholungseinstellungen“ der Tabellenzeileneigenschaften konfigurieren.
* Der Elementname für die Zeile lautet „statementDetails“.  Sie können ihn in den Tabellenzeileneigenschaften konfigurieren.
* Der Elementname für die Zelle in der Spalte „Kategorie“ ist „Kategorie“.  Sie können dies inline angeben.  Wählen Sie die Zelle aus und tippen Sie auf die Schaltfläche „Bearbeiten“.
* Der Elementname für die Zelle in der Spalte „Betrag“ lautet „Betrag“.  Die Tabellenzelle in der Spalte „Betrag“ ist außerdem ein numerisches Feld.
* Mit der angegebenen Konfiguration wird das Säulendiagramm im Beispiel wie folgt angezeigt.  Jede Farbe stellt eine Kategorie dar und einzelne Zeileneinträge oder Werte für eine Kategorie werden im Diagramm addiert.

  ![Diagramm](assets/chart.png)

Die Legende und QuickInfo werden wie folgt angezeigt.

![QuickInfo zur Diagrammlegende](assets/chart-legend-tooltip.png)

### Stile {#styling}

Im Stilmodus können Sie die Breite des Diagramms als Prozentsatz der Gesamtbreite im Formular oder Dokument und die Höhe in Pixeln festlegen.  Außerdem haben Sie die Möglichkeit, Text, Hintergrund, Ränder, Effekte und CSS-Überschreibungen anzubringen.

Um in der Seitensymbolleiste auf den Stilmodus umzuschalten, **tippen Sie auf >> Stile**.

![Verfügbare Diagrammeigenschaften für Formatierung](assets/chart-styling.png)

## Verwenden von Funktionen im Diagrammen {#use-functions}

Sie können ein Diagramm so konfigurieren, dass es mithilfe statistischer Funktionen Werte aus den Quelldaten für die Darstellung im Diagramm berechnet. Die Diagrammkomponente verfügt bereits über einige integrierte Funktionen, allerdings können Sie auch eigene Funktionen erstellen und für die Verwendung in der Diagrammkonfiguration freigeben.

>[!NOTE]
>
> Sie können Funktionen verwenden, um Werte für die x-Achse oder y-Achse in einem Diagramm zu berechnen.

### Standardfunktionen {#default-functions}

Die folgenden Funktionen sind standardmäßig in der Diagrammkomponente verfügbar:

* **Mittelwert (Durchschnitt)** Gibt den Durchschnitt der Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Summe** Gibt die Summe aller Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Maximum** Gibt das Maximum der Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Häufigkeit** Gibt die Anzahl der Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Bereich** Gibt die Differenz zwischen dem Maximum und dem Minimum der Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Median** Gibt den Wert zurück, der höhere und niedrigere Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse in der Mitte trennt.
* **Minimum** Gibt das Minimum der Werte auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück.
* **Modus** Gibt den Wert mit den meisten Vorkommnissen auf der x-Achse oder y-Achse für einen bestimmten Wert auf der jeweils anderen Achse zurück

### Benutzerdefinierte Funktionen {#custom-functions}

Neben der Verwendung der Standardfunktionen in Diagrammen können Sie [benutzerdefinierte Funktionen](/help/forms/using/rule-editor.md#custom-functions-in-rule-editor-custom-functions) in JavaScript schreiben und in der Liste der Funktionen in der Diagrammkomponente verfügbar machen.

Eine Funktion akzeptiert ein Array oder Werte sowie einen Kategorienamen als Eingaben und gibt einen Wert zurück. Beispiel:

```
Multiply(valueArray, category) {
    var val = 1;
    _.each(valueArray, function(value) {
        val = val * value;
    });
    return val;
}
```

Nachdem Sie eine benutzerdefinierte Funktion geschrieben haben, führen Sie die folgenden Schritte aus, um sie für die Verwendung in der Diagrammkonfiguration verfügbar zu machen:

1. Fügen Sie die benutzerdefinierte Funktion in der Client-Bibliothek hinzu, die dem adaptiven Formular oder dem Dokument zugeordnet ist.
1. Erstellen Sie in CRXDe-Lite einen „nt:unstructured“-Knoten mit den folgenden Eigenschaften im Anwendungsordner:
   * Legen Sie „guideComponentType“ auf „fd/af/reducer“ fest. (mandatory)
   * Dem Wert muss ein vollständig qualifizierter Name der benutzerdefinierten JavaScript-Funktion zugewiesen werden.  (mandatory)
   * Weisen Sie „jcr:description“ einen aussagekräftigen Namen zu.  Er erscheint in der Dropdown-Liste **Funktion verwenden**. Beispiel:**Multiplizieren**. 
   * Weisen Sie „qtip“ eine kurze Beschreibung der Funktion zu.  Sie wird als QuickInfo angezeigt, wenn der Mauszeiger über den Funktionsnamen in der Dropdown-Liste „Funktion verwenden“ bewegt wird.
   * Klicken Sie auf **Alles Speichern**, um die Konfiguration zu speichern.
   * Die Funktion ist jetzt für die Verwendung im Diagramm verfügbar.

![Benutzerdefinierte Funktion](assets/custom-function.png)


## Automatische Aktualisierung des Diagramms {#auto-refresh-chart}

Ein Diagramm wird automatisch aktualisiert, wenn die Benutzerin oder der Benutzer einen der folgenden Schritte ausführt:
* Hinzufügen oder Entfernen einer Instanz des Bedienfelds der Datenquelle oder Tabellenzeile.
* Ändern jedes auf der x-Achse oder y-Achse der Datenquelle oder Tabellenzeile grafisch dargestellten Wertes.
* Ändern des Diagrammtyps.

## Verwenden des Diagrammtyps in adaptiven Formularregeln {#chart-in-rules}

Die „chartType“-Eigenschaft gibt den Typ des Diagramms an.  Die möglichen Werte sind Kreisdiagramm, Tortendiagramm, Balken, Linie, Linie und Punkt, Punkt und Bereich.  Es handelt sich um eine skriptfähige Eigenschaft. Das bedeutet, dass Sie sie in [adaptiven Formularregeln](/help/forms/using/rule-editor.md) zur Anpassung von Diagrammkonfigurationen verwenden können. Sehen wir uns dazu ein Beispiel an.

Sagen wir, dass Sie ein Säulendiagramm konfiguriert haben.  Sie möchten Benutzenden allerdings auch die Möglichkeit bieten, einen anderen Diagrammtyp aus einer Dropdown-Liste auszuwählen und die Kurve neu zu zeichnen.  Dies können Sie mithilfe der Eigenschaft „chartType“ in einer Regel wie folgt erzielen:

1. Ziehen Sie aus der AEM-Seitenleiste eine Dropdown-Listen-Komponente auf das adaptive Formular.
1. Wählen Sie die Komponente aus und tippen Sie auf ![Einstellungen](cmppr1.png). 
1. Geben Sie einen Namen für die Dropdown-Liste ein.  Wählen Sie beispielsweise „Diagrammtyp“ aus.
1. Fügen Sie im Abschnitt „Elemente“ unterstützte Diagrammtypen hinzu, um die Dropdown-Liste zu füllen. Klicken Sie auf **Fertig**.
   ![Auswählen der Diagramm-Dropdown-Liste](chart-drop-down.png)

1. Wählen Sie die Dropdown-Komponente aus und klicken Sie auf ![Gesamter Text](rule_editor_icon.png). Erstellen Sie im Regeleditor eine Regel im visuellen Regeleditor, wie unten dargestellt.
   ![Festlegen von Diagrammregeln](assets/chart-rules.png)

   In diesem Beispiel lautet der Elementname der Diagrammkomponente **myChart**.

   Alternativ können Sie die folgenden Regeln im Code-Editor erstellen.

   ![Diagrammregeln](assets/chart-code-rule.png)

   Weitere Informationen zum Erstellen von Regeln finden Sie unter [Regeleditor](/help/forms/using/rule-editor.md)

1. Klicken Sie auf „Fertig“, um die Regel zu speichern.

Jetzt können Sie einen Diagrammtyp aus der Dropdown-Liste auswählen. Wenn Sie dann auf „Aktualisieren“ klicken, wird das Diagramm neu gezeichnet.
