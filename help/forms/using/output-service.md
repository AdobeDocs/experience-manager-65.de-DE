---
title: Ausgabe-Service
seo-title: Output Service
description: Dieser Artikel erläutert den Output-Dienst, eine Komponente der AEM Document Services.
seo-description: Describes Output Service, which is part of AEM Document Services
uuid: edddef59-b43c-486f-8734-3f97961ecf4d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 51ab91ff-c0c0-4165-ae02-f306e45eea03
docset: aem65
exl-id: 1b62e1c1-428d-4c0f-98a8-486f319fa581
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 100%

---

# Ausgabe-Service{#output-service}

## Übersicht {#overview}

Der OSGi-Dienst Output ist eine Komponente der AEM Document Services. Der Ausgabedienst unterstützt verschiedene Ausgabeformate und Ausgabedesignfunktionen von AEM Forms Designer. Mit dem Output-Dienst können Sie XFA-Vorlagen und XML-Daten in verschiedene Druckformate konvertieren.

Dabei können Sie mit dem Output-Service Programme mit folgenden Funktionen erstellen:

* Erzeugen fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
* Generieren von Ausgabeformularen in verschiedenen Formaten einschließlich nicht interaktiver PDF-, PostScript-, PCL- und ZPL-Druckdatenströme
* Generieren von druckbaren PDFs aus XFA-Formular-PDFs
* Generieren von PDF-, PostScript-, PCL- und ZPL-Dokumenten in großen Mengen durch Zusammenführen mehrerer Datensätze mit den bereitgestellten Vorlagen

>[!NOTE]
>
>Ausgabedienst ist eine 32-Bit-Anwendung. Unter Microsoft Windows darf eine 32-Bit-Anwendung maximal 2 GB Arbeitsspeicher verwenden. Das Limit gilt auch für den Ausgabedienst.

## Erstellen nicht interaktiver Formulardokumente {#creating-non-interactive-form-documents}

![usingOutput_modified](assets/usingoutput_modified.png)

Normalerweise erstellen Sie Vorlagen mit AEM Forms Designer. Mit den APIs `generatePDFOutput` und `generatePrintedOutput` des Output-Dienstes können Sie diese Vorlagen direkt in verschiedene Formate wie PDF, PostScript, ZPL und PCL konvertieren.

Mit `generatePDFOutput` generieren Sie PDF-Dokumente, während `generatePrintedOutput` Dokumente in den Formaten PostScript, ZPL und PCL generiert. Der erste Parameter beider Vorgänge akzeptiert entweder den Namen der Vorlagendatei (z. B. `ExpenseClaim.xdp`) oder ein Dokumentobjekt, das die Vorlage enthält. Wenn Sie den Namen der Vorlagendatei angeben, vergessen Sie nicht, auch den Inhaltsstamm als Pfad zum Vorlagenordner anzugeben. Sie können den Inhaltsstamm entweder mit dem Parameter `PDFOutputOptions` oder dem Parameter `PrintedOutputOptions` angeben. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit diesen Parametern angeben können.

Der zweite Parameter akzeptiert ein XML-Dokument, das bei der Generierung des Ausgabedokuments mit der Vorlage zusammengeführt wird.

Der Vorgang `generatePDFOutput` kann als Eingabe auch ein XFA-basiertes PDF-Formular akzeptieren und als Ausgabe eine nicht interaktive Version des PDF-Formulars zurückgeben.

## Generieren nicht interaktiver Formulardokumente {#generating-non-interactive-form-documents}

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Datensätze mit XML-Daten.

In diesem Fall können Sie mit den Vorgängen `generatePDFOutputBatch` und `generatePrintedOutputBatch` des Output-Dienstes für jeden Datensatz ein Druckdokument erstellen.

Sie können die Datensätze auch zu einem Dokument zusammenfassen. Beide Vorgänge akzeptieren vier Parameter.

Der erste Parameter ist eine Zuordnung mit einer Zufallszeichenfolge als Schlüssel und dem Namen der Vorlagendatei als Wert.

Der zweite Parameter ist ebenfalls eine Zuordnung, deren Wert ein Dokumentobjekt für die XML-Daten ist. Der Schlüssel ist derselbe wie beim ersten Parameter.

Der dritte Parameter für `generatePDFOutputBatch` oder `generatePrintedOutputBatch` ist vom Typ `PDFOutputOptions` bzw. `PrintedOutputOptions`.

Die Parametertypen sind die gleichen wie die Typen der Parameter für die Vorgänge `generatePDFOutput` und `generatePrintedOutput` und haben die gleiche Auswirkung.

Der vierte Parameter ist vom Typ `BatchOptions`, mit dem Sie angeben, ob für jeden Datensatz eine eigene Datei erzeugt werden kann. Der Standardwert dieses Parameters ist „false“.

Sowohl `generatePrintedOutputBatch` als auch `generatePDFOutputBatch` geben einen Wert vom Typ `BatchResult` zurück. Der Wert enthält eine Liste der generierten Dokumente. Außerdem enthält er ein Metadatendokument im XML-Format mit Informationen zu jedem generierten Dokument.
