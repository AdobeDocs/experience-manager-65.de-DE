---
title: PDF-Generierung kann mit WorkBench nicht viele PDF drucken
description: Wenn ein Kunde eine große Anzahl von PDF über Services generiert, die über WorkBench implementiert wurden, schlägt der Druckdienst fehl.
exl-id: f3746b8e-4c38-447a-b5bf-d11fc77556f7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# PDF-Generierung kann nicht viele PDF über WorkBench drucken {#PDF-generation-fails-to-print-a-large-number-of-PDFs-via-WorkBench}

## Problem {#issue}

Wenn ein Kunde eine große Anzahl von PDF über Services generiert, die über WorkBench implementiert wurden. Der Dienst schlägt fehl, weil nicht genügend Arbeitsspeicher vorhanden ist. Der Fehler wird wie folgt angezeigt:

`ALC-OUT-002-013: XMLFormFactory, PAexecute failure: "0: Out of Memory"`

<!-- Attached is a simplified template (BollatoRiservatiLandscape_table_simple.xdp) that simulates the problem.
Using the Designer, if we associate the template "BollatoRiservatiLandscape_table_semplice.xdp" with the XML file "BollatoRiservati.xml" during the generation of the pdf, the process comes to occupy 1.6 Gb of RAM. On the server side, with the complete template, the pdf generation process breaks down, occupying 2 GB of RAM.-->

Dies liegt daran, dass die maximale Anzahl von Seiten in einer Druckanforderung unter Windows auf ca. 1000 Seiten begrenzt ist. Wenn eine Druckausgabe generiert wird, müssen die Vorlage und die Daten in den Speicher geladen werden und das resultierende Layout wird im Speicher aufgebaut. Dies bedeutet, dass die Größe der endgültigen Ausgabe begrenzt ist. Der Prozess, der die Druckausgabe generiert, ist eine 32-Bit-Aufgabe, was bedeutet, dass sie unter Windows auf 2 GB RAM begrenzt ist <!--and 4 GB on UNIX-->.

## Gilt für {#applies-to}

Die Lösung gilt für AEM Forms <!--JEE Server and AEM Forms on OSGi Server--> für x86_win32 XMLFM.

## Lösung {#solution}

Der größte Faktor, der sich auf die Speichernutzung auswirkt, ist die Datenmenge in einem Formular. In einem Formularentwurf gibt es jedoch andere Faktoren, die die Speichernutzung in geringerem Umfang beeinflussen. Wenn Sie diese Faktoren kennen, können Sie ein Formular für eine größere Druckausgabe entwerfen. Im folgenden Abschnitt werden in priorisierter Reihenfolge Faktoren aufgeführt, die den Speicherbedarf beeinflussen:

### Wirkungsfaktor {#impact-factor}

**Hoch**

1. **Auswahl-Teilformulare** - Ein Auswahl-Teilformularsatz ist eine Variante des Teilformularsatz-Objekts, mit dem Sie die Anzeige bestimmter Teilformulare aus dem Satz mithilfe von bedingten Anweisungen anpassen können.
1. **Statischen Text anstelle von Beschriftungen verwenden** - Fast jedes Feld bietet eine Beschriftung in , sollte der Benutzer diese anstelle eines zusätzlichen statischen Textes als Beschriftung verwenden.
1. Verwendung **RTF (Rich Text Format)** soweit möglich.

**Durchschnittlich**

Zusätzliche Faktoren, die bei der Erstellung von Formularvorlagen zu berücksichtigen sind, um die Speichernutzung zu verbessern:

1. Vermeiden Sie die Verwendung von statischem Text zur Beschriftung eines Felds. Verwenden Sie stattdessen Beschriftungen im Textfeld.
2. Verwenden Sie keine Rechtecke, Linien, Objekte und Tabellen.
3. Vermeiden Sie nach Möglichkeit die Verwendung von RichText- und Auswahl-Teilformularen.
4. Vermeiden Sie die übermäßige Verwendung von Teilformularen und verschachtelten Teilformularen.

### Datengrößenbegrenzung {#data-size-limitations}

Da wir durch den maximalen Prozessspeicher eingeschränkt sind und der vom Prozess belegte Speicher nicht nur von der Größe der Datendatei abhängt. Sie ist sehr eng mit dem Formularentwurf und in gewissem Umfang mit der tatsächlichen Datenmenge verknüpft, die im Formular zusammengeführt wird.

Wenn das Formular viele kleine Knoten mit kleinen Daten enthält, verbraucht der Prozess mehr Speicher (und verlässt daher schneller den Speicher) als ein Formular mit weniger Knoten (auch) mit großen Daten.

Lesen Sie die [Anlage unten](#appendix) für weitere Informationen, bei denen die Testergebnisse auf dem Druckformular basieren (PDF ohne Tags). Die Verwendung von getaggten PDF-Prozessspeicheranforderungen erhöht sich. Es hängt auch von der Anzahl der Felder im Formular ab. Ungefähr die Speicheranforderung für den Prozess würde etwas mehr als das 1,5-fache des PDF ohne Tags betragen.

### Interaktive Forms {#interactive-forms}

Interaktive Formulare verbrauchen mehr Speicher als Forms drucken, da interaktive Felder erneut wiedergegeben werden. In den durchgeführten Tests stieg der Speicherverbrauch im Vergleich zu Druckformularen um etwa 1,5, wobei es sich um statische interaktive Formulare handelte.

### Bildformate {#image-formats}

Adobe empfiehlt kein bestimmtes Bildformat. Es wäre jedoch schön, eine kleinere Bildgröße zu haben, z. B. PNG (Portable Network Graphics). Es ist auch nicht ratsam, Bilder mit hohen Auflösungen zu verwenden, deren Größe mehrere Hundert Megabyte variiert. Außerdem ist es nicht ratsam, komprimierte Bilder zu verwenden, deren Größe bei der Dekomprimierung auf mehrere Hundert Megabyte an Daten erweitert.

### Anhang {#appendix}

**Tabellenbeispiele**

Unten finden Sie verschiedene Varianten für Tabellen, die die Rendering-Anzahl der Seiten im Vergleich zur Datengröße für einfache Tabellen und komplexe Tabellen anzeigen.

1. Eine Tabelle mit einer einzigen Spalte, in der 5000 PDF-Seiten, die Datendateigröße 24 MB und 30 KB-Datensätze generiert werden.

   ![table_single_column](/help/forms/using/assets/table_single_column.png)

1. Eine Tabelle mit vielen kleinen Spalten, in der 800 Seiten PDF erstellt werden, die Datendateigröße beträgt 4,6 MB und 20 KB.
   ![table_many_small_columns](/help/forms/using/assets/table_many_small_columns.png)

1. Eine Tabelle mit vielen kleinen Spalten, aber einer größeren Datendatei, da größere xmlTag-Namen verwendet werden.
Hier ist alles gleich wie zuvor, aber XML-Tag-Namen wurden groß gemacht (sodass die Datendateigröße ohne Erhöhung der tatsächlichen effektiven Daten zunimmt), ist das Endergebnis (obere Grenze) fast gleich. Die Datendateigröße ist zwar von 4,6 MB auf 44,6 MB gestiegen. Hier werden 800 Seiten PDF generiert, die Datendateigröße beträgt 44,6 MB und 20 KB.

   ![table_greater_xml_tagname](/help/forms/using/assets/table_bigger_xml_tagname.png)

Es ist daher schwierig, eine allgemeine Obergrenze für die Datendateigröße festzulegen. Jedes Formular ist eindeutig, und daher würde sich der Speicherverbrauch von Formular zu Formular unterscheiden.
