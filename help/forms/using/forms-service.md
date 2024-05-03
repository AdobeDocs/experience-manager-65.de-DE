---
title: Formularservice
description: Dieser Artikel erläutert den Forms-Dienst sowie die formularspezifischen Aufgaben, die Sie mit diesem Dienst ausführen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 6580fe6f-3cdb-45ec-8ba3-51dc60d1965e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 100%

---

# Formularservice {#forms-service}

## Übersicht {#overview}

Der Forms-Dienst ermöglicht das Erstellen interaktiver Client-Anwendungen zur Datenerfassung, die typischerweise in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und übermitteln. Mit dem Forms-Dienst kann jeder von Ihnen entwickelte Formularentwurf als PDF-Dokument gerendert werden.

Durch die Bereitstellung elektronischer Formulare als Adobe-PDFs erweitert der Forms-Dienst damit die intelligenten Datenerfassungsprozesse eines Unternehmens. Auch der Import und Export von Daten in bzw. aus vorhandenen PDF-Formularen ist mit diesem Dienst möglich.

Der Forms-Dienst bietet folgende Funktionen:

* Rendern von PDF-Formularen auf Basis einer Vorlage und XML-Daten
* Möglichkeit der Formulardatenintegration für den Import und die Extraktion von Daten in bzw. aus PDF-Formularen
* Wiedergabe von Formularen basierend auf Fragmenten.

## Erstellen von PDF-Formularen  {#creating-pdf-forms-nbsp}

Mit dem Forms-Dienst können Sie PDF-Formulare für die Datenerfassung erstellen. Als Grundlage verwenden Sie dazu in der Regel eine AEM Forms Designer-Vorlage. Mit dem Javadoc-Vorgang `renderPDFForm` des Forms-Dienstes konvertieren Sie diese Vorlage in ein PDF-Formular.

Als ersten Parameter des Vorgangs `renderPDFForm` geben Sie den Namen der Vorlagendatei ein (z. B. `ExpenseClaim.xdp`). Die Vorlagendatei kann in einem lokalen Dateisystem, in einem CRX-Repository oder auf einem HTTP- oder FTP-Server gespeichert sein. Den Speicherort der Vorlagendatei können Sie über den Inhaltsstamm im Parameter `PDFFormRenderOptions` des Vorgangs `renderPDFForm` festlegen. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit dem Parameter `PDFFormRenderOptions` angeben können.

Der Vorgang `renderPDFForm` akzeptiert auch XML-Daten. Die XML-Daten werden bei der Erstellung eines PDF-Formulars mit der Vorlage zusammengeführt, sodass das generierte PDF-Formular die angegebenen Daten enthält. Der zweite Parameter des Vorgangs `renderPDFForm` akzeptiert ein Dokument- bzw. Javadoc-Objekt, das die gewünschten XML-Daten enthält.

## Extrahieren von Daten aus PDF-Formularen  {#extracting-data-from-pdf-forms-nbsp}

Zum Extrahieren von XML-Daten aus einem PDF-Formular verwenden Sie den Javadoc-Vorgang `exportData` des Forms-Dienstes. Als ersten Parameter dieses Vorgangs geben Sie ein Dokument an. Sie können die Daten als XDP-Dokument oder als XML-Datei exportieren. Beim Export der Daten als XML-Datei wird die XDP-Hülle entfernt, sodass nur die reine XML-Datei zurückgegeben wird. Sie können diese Anordnung mit dem zweiten Parameter präzisieren.

## Importieren von Daten in PDF-Formulare {#importing-data-into-pdf-forms}

Mit dem Forms-Dienst können Sie ein mit AEM Forms Designer oder `renderPDFForm` erstelltes PDF-Formular auch mit XML-Daten zusammenführen. Der Javadoc-Vorgang `importData` des Forms-Dienstes akzeptiert als Parameter das PDF-Formular sowie die XML-Daten und gibt ein PDF-Formular mit den XML-Daten zurück.

## Wiedergabe von Formularen basierend auf Fragmenten {#rendering-forms-based-on-fragments}

Der Forms-Dienst kann Formulare auch basierend auf Fragmenten wiedergeben, die mit AEM Forms Designer erstellt wurden. Ein Fragment ist ein wiederverwendbarer Teil eines Formulars. Es wird als separate XDP-Datei gespeichert, die in verschiedene Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Durch die Verwendung von Fragmenten wird die Erstellung und Pflege großer Formularbestände vereinfacht und beschleunigt. Fügen Sie beim Erstellen eines Formulars einen Verweis auf das erforderliche Fragment ein, damit das Fragment im Formular erscheint. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist.

Die Verwendung von Fragmenten hat unter anderem folgende Vorteile:

* **Wiederverwendbarkeit von Inhalten**: Sie können Inhalte in mehreren Formularentwürfen wiederverwenden. Am schnellsten können Sie Teile mit demselben Inhalt in mehreren Formularen wiederverwenden, indem Sie ein entsprechendes Fragment erstellen. Den Inhalt zu kopieren oder neu zu erstellen, dauert in jedem Fall länger. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Sie müssen globale Änderungen für mehrere Formulare nur einmal in einer Datei vornehmen. Sie können die Inhalte, Skriptobjekte, Datenbindungen, Layout-Einstellungen oder Stile in einem Fragment ändern. Diese Änderungen werden daraufhin in allen XDP-Formularen, die auf dieses Fragment verweisen, übernommen.
* **Gemeinsame Entwicklung von Formularen**: Sie können die Formularentwicklung auf mehrere Ressourcen aufteilen. Formularentwickler, die mit Scripting oder anderen erweiterten Funktionen von AEM Forms Designer vertraut sind, können Fragmente, die Scripting und dynamische Eigenschaften nutzen, entwickeln und mit anderen teilen. Entwicklerinnen und Entwickler von Formularen können die Fragmente zum Entwerfen von Formularen verwenden. Darüber hinaus können sie die Fragmente verwenden, um sicherzustellen, dass alle Teile eines Formulars über mehrere Formulare hinweg ein einheitliches Erscheinungsbild und einheitliche Funktionalität aufweisen.
