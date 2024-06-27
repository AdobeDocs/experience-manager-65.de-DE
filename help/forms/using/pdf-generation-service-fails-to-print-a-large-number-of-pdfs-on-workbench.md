---
title: Beim Drucken einer großen Anzahl von PDFs mit Workbench schlägt die PDF-Generierung fehl
description: Wenn eine Kundin oder ein Kunde eine große Anzahl von PDF über Dienste generiert, die über Workbench implementiert wurden, schlägt der Druckdienst fehl.
exl-id: f3746b8e-4c38-447a-b5bf-d11fc77556f7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '775'
ht-degree: 100%

---

# Beim Drucken einer großen Anzahl von PDFs über Workbench schlägt die PDF-Generierung fehl {#PDF-generation-fails-to-print-a-large-number-of-PDFs-via-WorkBench}

## Problem {#issue}

Wenn eine Kundin oder ein Kunde eine große Anzahl von PDF über Dienste generiert, die über Workbench implementiert wurden, schlägt der Dienst fehl, weil nicht genügend Arbeitsspeicher vorhanden ist. Es wird der folgende Fehler angezeigt:

`ALC-OUT-002-013: XMLFormFactory, PAexecute failure: "0: Out of Memory"`

<!-- Attached is a simplified template (BollatoRiservatiLandscape_table_simple.xdp) that simulates the problem.
Using the Designer, if we associate the template "BollatoRiservatiLandscape_table_semplice.xdp" with the XML file "BollatoRiservati.xml" during the generation of the pdf, the process comes to occupy 1.6 Gb of RAM. On the server side, with the complete template, the pdf generation process breaks down, occupying 2 GB of RAM.-->

Dies liegt daran, dass die maximale Anzahl von Seiten in einer Druckanfrage unter Windows auf ca. 1000 Seiten begrenzt ist. Wenn eine Druckausgabe generiert wird, müssen die Vorlage und die Daten in den Speicher geladen werden und das resultierende Layout wird im Speicher aufgebaut. Es gibt also eine Größenbeschränkung für die abschließende Ausgabe. Bei dem Prozess, der die Druckausgabe generiert, handelt es sich um eine 32-Bit-Aufgabe, d. h., dass sie unter Windows auf 2 GB RAM <!--and 4 GB on UNIX--> begrenzt ist.

## Gilt für {#applies-to}

Die Lösung gilt für AEM Forms <!--JEE Server and AEM Forms on OSGi Server--> für x86_win32 XMLFM.

## Lösung {#solution}

Der wichtigste Faktor, der sich auf die Speicherauslastung auswirkt, ist die Datenmenge in einem Formular. In einem Formularentwurf gibt es jedoch auch andere Faktoren, die die Speicherauslastung in geringerem Umfang beeinflussen. Wenn Sie sich dieser Faktoren bewusst sind, können Sie ein Formular für eine größere Druckausgabe entwickeln. Im folgenden Abschnitt werden in priorisierter Reihenfolge Faktoren aufgeführt, die den Speicherbedarf beeinflussen:

### Einflussfaktor {#impact-factor}

**Hoch**

1. **Auswahl-Teilformularsatz**: Bei einem Auswahl-Teilformularsatz handelt es sich um eine Abwandlung des Teilformularsatzobjekts, mit dem Sie die Anzeige bestimmter Teilformulare im Satz mithilfe von bedingten Anweisungen anpassen können.
1. **Verwendung von statischem Text anstelle von Beschriftungen**: Fast jedes Feld umfasst eine Beschriftung. Benutzende sollten diese anstelle von zusätzlichem statischem Text als Beschriftung verwenden.
1. Verwenden Sie nach Möglichkeit **RTF (Rich Text Format)**.

**Durchschnittlich**

Die folgenden zusätzlichen Faktoren sollten bei der Gestaltung von Formularvorlagen berücksichtigt werden, um die Speicherauslastung zu optimieren:

1. Vermeiden Sie die Verwendung von statischem Text zur Beschriftung eines Felds. Verwenden Sie stattdessen Beschriftungen im Textfeld.
2. Verwenden Sie nicht zu viele Rechtecke, Linien, Objekte und Tabellen.
3. Vermeiden Sie nach Möglichkeit die Verwendung von Rich-Text- und Auswahl-Teilformularen.
4. Vermeiden Sie eine übermäßige Verwendung von (verschachtelten) Teilformularen.

### Datengrößenbegrenzung {#data-size-limitations}

Wir sind durch den maximalen Prozessspeicher eingeschränkt, wobei der vom Prozess belegte Speicher nicht nur von der Größe der Datendatei alleine abhängt. Vielmehr ist dieser Aspekt sehr eng mit dem Formularentwurf und in gewissem Maße mit der tatsächlichen Datenmenge verknüpft, die im Formular zusammengeführt wird.

Wenn das Formular viele kleine Knoten mit kleinen Datenmengen enthält, verbraucht der Prozess mehr Speicher (und stößt schneller an seine Speichergrenzen) als ein Formular mit weniger Knoten mit (sogar) großen Datenmengen.

Weitere Informationen finden Sie im [Anhang unten](#appendix). Die Testergebnisse basieren dabei auf Druckformularen (PDF ohne Tags). Bei getaggten PDF-Dateien steigen die des Speicheranforderungen des Prozesses. Dies hängt auch von der Anzahl der Felder im Formular ab. Der Speicherbedarf für den Prozess würde gegenüber PDFs ohne Tags etwas mehr als das 1,5-Fache betragen.

### Interaktive Formulare {#interactive-forms}

Interaktive Formulare verbrauchen mehr Speicher als Druckformulare, da interaktive Felder erneut gerendert werden. In den durchgeführten Tests mit statischen interaktiven Formulare stieg der Speicherbedarf im Vergleich zu Druckformularen um etwa das 1,5-Fache.

### Bildformate {#image-formats}

Adobe empfiehlt kein bestimmtes Bildformat. Eine kleinere Bildgröße wäre jedoch gut, z. B. indem Sie das Format PNG (Portable Network Graphics) verwenden. Es ist auch nicht ratsam, Bilder mit hohen Auflösungen zu verwenden, die Hunderte Megabyte groß sein können. Außerdem sollten keine komprimierte Bilder verwendet werden, da diese nach der Dekomprimierung mehrere Hundert Megabyte an Daten umfassen können.

### Anhang {#appendix}

**Tabellenbeispiele**

Nachstehend finden Sie verschiedene Tabellen, die die Anzahl der gerenderten Seiten im Vergleich zur Datengröße für einfache Tabellen und komplexe Tabellen zeigen.

1. Eine Tabelle mit einer einzigen Spalte, bei der 5000 PDF-Seiten generiert werden, die Datendatei 24 MB groß ist und 30.000 Datensätze vorhanden sind:

   ![Tabelle mit einer Spalte](/help/forms/using/assets/table_single_column.png)

1. Eine Tabelle mit vielen kleinen Spalten, bei der 800 PDF-Seiten generiert werden, die Datendatei 4,6 MB groß ist und 20.000 Datensätze vorhanden sind:
   ![Tabelle mit vielen kleinen Spalten](/help/forms/using/assets/table_many_small_columns.png)

1. Eine Tabelle mit vielen kleinen Spalten, aber einer größeren Datendatei, da größere xmlTag-Namen verwendet werden.
Hier ist alles gleich wie zuvor; der XML-Tag-Name ist aber größer (sodass die Datendateigröße ohne Erhöhung der tatsächlichen effektiven Daten zunimmt) und das Endergebnis (obere Obergrenze) ist nahezu identisch. Die Datendateigröße ist allerdings von 4,6 MB auf 44,6 MB angewachsen. Hier werden 800 PDF-Seiten generiert, die Datendateigröße beträgt 44,6 MB und es sind 20.000 Datensätze vorhanden.

   ![Tabelle mit größerem XML-Tag-Namen](/help/forms/using/assets/table_bigger_xml_tagname.png)

Es ist daher schwierig, eine allgemeine Obergrenze für die Datendateigröße festzulegen. Jedes Formular ist einzigartig. Daher unterscheidet sich auch der Speicherbedarf von Formular zu Formular.
