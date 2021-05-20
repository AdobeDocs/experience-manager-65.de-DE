---
title: Formularservice
seo-title: Formularservice
description: Dieser Artikel erläutert den Forms-Dienst sowie die formularspezifischen Aufgaben, die Sie mit diesem Dienst ausführen können.
seo-description: Dieser Artikel erläutert den Forms-Dienst sowie die formularspezifischen Aufgaben, die Sie mit diesem Dienst ausführen können.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
exl-id: bd1216e4-2248-484b-a3c1-c209da4ff94f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 84%

---

# Formularservice {#forms-service}

## Überblick {#overview}

Der Forms-Dienst ermöglicht das Erstellen interaktiver Clientanwendungen zur Datenerfassung, die in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und übermitteln. Mit dem Forms-Dienst kann jeder von Ihnen entwickelte Formularentwurf als PDF-Dokument wiedergegeben werden.

Durch die Bereitstellung elektronischer Formulare als Adobe-PDFs erweitert der Forms-Dienst damit die intelligenten Datenerfassungsprozesse eines Unternehmens. Auch der Import bzw. Export von Daten in bzw. aus vorhandenen PDF-Formularen ist mit diesem Dienst möglich.

Der Forms-Dienst bietet folgende Funktionen:

* Wiedergabe von PDF-Formularen auf Basis einer Vorlage und den bereitgestellten XML-Daten
* Möglichkeit der Formulardatenintegration für den Import bzw. die Extraktion von Daten in bzw. aus PDF-Formularen
* Wiedergabe von Formularen basierend auf Fragmenten

## Erstellen von PDF-Formularen  {#creating-pdf-forms-nbsp}

Zur Erstellung von PDF-Formularen für die Datenerfassung verwenden Sie den Forms-Dienst. Als Grundlage verwenden Sie dazu in der Regel eine Adobe AEM Forms Designer-Vorlage. Mit dem Javadoc-Vorgang `renderPDFForm` des Forms-Dienstes konvertieren Sie diese Vorlage in ein PDF-Formular.

Als ersten Parameter des Vorgangs `renderPDFForm` geben Sie den Namen der Vorlagendatei ein (z. B. `ExpenseClaim.xdp`). Sie können die Vorlagendatei in einem lokalen Dateisystem, CRX-Repository oder an einem HTTP- oder FTP-Speicherort speichern. Sie können den Speicherort der Vorlagendatei angeben, indem Sie den Inhaltsstamm im Parameter `PDFFormRenderOptions` des Vorgangs `renderPDFForm` festlegen. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit dem Parameter `PDFFormRenderOptions` angeben können.

Der Vorgang `renderPDFForm` akzeptiert auch XML-Daten. Die XML-Daten werden beim Erstellen eines PDF-Formulars mit der Vorlage zusammengeführt, sodass das erstellte PDF-Formular die angegebenen Daten enthält. Der zweite Parameter des Vorgangs `renderPDFForm` akzeptiert ein Dokument- bzw. Javadoc-Objekt, das die gewünschten XML-Daten enthält.

## Extrahieren von Daten aus PDF-Formularen  {#extracting-data-from-pdf-forms-nbsp}

Zum Extrahieren von XML-Daten aus einem PDF-Formular verwenden Sie den Javadoc-Vorgang `exportData` des Forms-Dienstes. Als ersten Parameter dieses Vorgangs geben Sie ein Dokument an. Sie können die Daten als XDP-Dokument oder als XML-Datei exportieren. Beim Export der Daten als XML-Datei wird die XDP-Hülle entfernt, sodass nur die reine XML-Datei zurückgegeben wird. Das Exportformat (XDP oder XML) geben Sie mit dem zweiten Parameter an.

## Importieren von Daten in PDF-Formulare  {#importing-data-into-pdf-forms}

Mit dem Forms-Dienst können Sie ein mit AEM Forms Designer oder `renderPDFForm` erstelltes PDF-Formular auch mit XML-Daten zusammenführen. Der Javadoc-Vorgang `importData` des Forms-Dienstes akzeptiert als Parameter das PDF-Formular sowie die XML-Daten und gibt ein PDF-Formular mit den XML-Daten zurück.

## Wiedergabe von Formularen basierend auf Fragmenten {#rendering-forms-based-on-fragments}

Der Forms-Dienst kann Formulare auch basierend auf Fragmenten wiedergeben, die mit Adobe AEM Forms Designer erstellt wurden. Ein Fragment ist ein wiederverwendbarer Teil eines Formulars. Es wird als separate XDP-Datei gespeichert, die in verschiedene Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Durch die Verwendung von Fragmenten wird die Erstellung und Pflege großer Formularbestände vereinfacht und beschleunigt. Fügen Sie beim Erstellen eines Formulars einen Verweis auf das erforderliche Fragment ein, damit das Fragment im Formular angezeigt wird. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist.

Die Verwendung von Fragmenten hat unter anderem folgende Vorteile:

* **Wiederverwendbarkeit von Inhalten**: Sie können Inhalte in mehreren Formularentwürfen wiederverwenden. Am schnellsten können Sie Teile mit demselben Inhalt in mehreren Formularen wiederverwenden, indem Sie ein entsprechendes Fragment erstellen. Kopieren oder gar Neuerstellen des Inhalts dauert in jedem Fall länger. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Sie müssen globale Änderungen für mehrere Formulare nur einmal in einer Datei vornehmen. Sie können Inhalt, Skriptobjekte, Datenbindungen, Layout und Stile eines Fragments ändern. Alle XDP-Formulare, die auf dieses Fragment verweisen, spiegeln diese Änderungen wider.
* **Gemeinsame Entwicklung von Formularen**: Sie können die Formularentwicklung auf mehrere Ressourcen aufteilen. Formularentwickler mit Erfahrung in der Skripterstellung oder anderen erweiterten Funktionen von AEM Forms Designer können Fragmente entwickeln und freigeben, die Skripterstellung und dynamische Eigenschaften verwenden. Formularentwickler können diese Fragmente zur Gestaltung ihrer Formulare verwenden. Neben der einfacheren Entwicklung stellen sie dadurch sicher, dass Aussehen und Funktionalität aller Formularteile in allen Formularen einheitlich sind.
