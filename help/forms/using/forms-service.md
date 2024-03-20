---
title: Formularservice
description: In diesem Artikel werden der Forms-Dienst und die formularbezogenen Aufgaben beschrieben, die Sie mit dem Forms-Dienst ausführen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 6580fe6f-3cdb-45ec-8ba3-51dc60d1965e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 50%

---

# Formularservice {#forms-service}

## Übersicht {#overview}

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen zur Datenerfassung erstellen, mit denen typischerweise in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Der Forms-Dienst rendert als PDF Dokumente für jeden Formularentwurf, den Sie entwickeln.

Der Forms-Dienst ermöglicht Unternehmen auch die Erweiterung ihrer intelligenten Datenerfassungsprozesse durch die Bereitstellung elektronischer Formulare als Adobe-PDF. Sie können den Dienst auch verwenden, um Daten in bzw. aus vorhandenen PDF forms zu importieren und zu exportieren.

Der Forms-Dienst bietet folgende Funktionen:

* Rendern Sie PDF forms basierend auf Vorlage und XML-Daten.
* Aktivieren Sie die Formulardatenintegration, um Daten in PDF forms zu importieren und aus ihnen zu extrahieren.
* Wiedergabe von Formularen basierend auf Fragmenten.

## Erstellen von PDF forms  {#creating-pdf-forms-nbsp}

Verwenden Sie den Formulardienst, um PDF forms für die Datenerfassung zu erstellen. Als Grundlage verwenden Sie dazu in der Regel eine AEM Forms Designer-Vorlage. Mit dem Javadoc-Vorgang `renderPDFForm` des Forms-Dienstes konvertieren Sie diese Vorlage in ein PDF-Formular.

Als ersten Parameter des Vorgangs `renderPDFForm` geben Sie den Namen der Vorlagendatei ein (z. B. `ExpenseClaim.xdp`). Die Vorlagendatei kann in einem lokalen Dateisystem, in einem CRX-Repository oder auf einem HTTP- oder FTP-Server gespeichert sein. Den Speicherort der Vorlagendatei können Sie über den Inhaltsstamm im Parameter `PDFFormRenderOptions` des Vorgangs `renderPDFForm` festlegen. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit dem Parameter `PDFFormRenderOptions` angeben können.

Der Vorgang `renderPDFForm` akzeptiert auch XML-Daten. Die XML-Daten werden bei der Erstellung eines PDF-Formulars mit der Vorlage zusammengeführt, sodass das generierte PDF-Formular die angegebenen Daten enthält. Der zweite Parameter des Vorgangs `renderPDFForm` akzeptiert ein Dokument- bzw. Javadoc-Objekt, das die gewünschten XML-Daten enthält.

## Extrahieren von Daten aus PDF-Formularen  {#extracting-data-from-pdf-forms-nbsp}

Zum Extrahieren von XML-Daten aus einem PDF-Formular verwenden Sie den Javadoc-Vorgang `exportData` des Forms-Dienstes. Dieser Vorgang akzeptiert ein Dokument als ersten Parameter. Sie können die Daten entweder als XDP-Dokument oder als XML-Datei exportieren. Wenn Sie die Daten als XML-Datei exportieren, entfernen die exportierten Daten den XDP-Umschlag und geben eine einfache XML-Datei zurück. Sie können diese Anordnung mit dem zweiten Parameter festlegen.

## Importieren von Daten in PDF forms {#importing-data-into-pdf-forms}

Mit dem Forms-Dienst können Sie ein mit AEM Forms Designer oder `renderPDFForm` erstelltes PDF-Formular auch mit XML-Daten zusammenführen. Der Javadoc-Vorgang `importData` des Forms-Dienstes akzeptiert als Parameter das PDF-Formular sowie die XML-Daten und gibt ein PDF-Formular mit den XML-Daten zurück.

## Wiedergabe von Formularen basierend auf Fragmenten {#rendering-forms-based-on-fragments}

Der Forms-Dienst kann Formulare auch basierend auf Fragmenten wiedergeben, die mit AEM Forms Designer erstellt wurden. Ein Fragment ist ein wiederverwendbarer Teil eines Formulars. Es wird als separate XDP-Datei gespeichert, die in mehrere Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Die Verwendung von Fragmenten vereinfacht und beschleunigt die Erstellung und Pflege einer großen Anzahl von Formularen. Fügen Sie beim Erstellen eines Formulars einen Verweis auf das erforderliche Fragment ein, damit das Fragment im Formular erscheint. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist.

Die Verwendung von Fragmenten hat folgende Vorteile:

* **Inhaltswiederverwendung**: Sie können Inhalte in mehreren Formularentwürfen wiederverwenden. Um Teile desselben Inhalts schnell in mehreren Formularen wiederzuverwenden, erstellen Sie ein Fragment. Das Kopieren oder Neuerstellen des Inhalts dauert länger. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Globale Änderungen an mehreren Formularen können nur einmal in einer Datei vorgenommen werden. Sie können den Inhalt, die Skriptobjekte, die Datenbindungen, das Layout oder die Stile eines Fragments ändern. Alle XDP-Formulare, die auf das Fragment verweisen, spiegeln die Änderungen wider.
* **Gemeinsame Formularerstellung**: Sie können die Erstellung von Formularen für mehrere Ressourcen freigeben. Formularentwickler, die mit Scripting oder anderen erweiterten Funktionen von AEM Forms Designer vertraut sind, können Fragmente, die Scripting und dynamische Eigenschaften nutzen, entwickeln und mit anderen teilen. Formularentwickler können die Fragmente zum Entwerfen von Formularen verwenden. Darüber hinaus können sie die Fragmente verwenden, um sicherzustellen, dass alle Teile eines Formulars über mehrere Formulare hinweg ein einheitliches Erscheinungsbild und eine einheitliche Funktionalität aufweisen.
