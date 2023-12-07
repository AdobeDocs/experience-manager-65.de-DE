---
title: Empfohlene Vorgehensweisen für HTML5-Formulare
description: Stimmen Sie Ihre XFA-basierten HTML5-Formulare für optimale Leistung ab.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
content-type: reference
docset: aem65
feature: Mobile Forms
exl-id: 62ff6306-9989-43b0-abaf-b0a811f0a6a4
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 22%

---

# Empfohlene Vorgehensweisen für HTML5-Formulare{#best-practices-for-html-forms}

## Übersicht {#overview}

AEM Forms verfügt über eine Komponente mit dem Namen HTML5 forms. Dadurch können Sie vorhandene XFA-basierte PDF forms (XDP-Dateien) im HTML5-Format rendern. Dieses Dokument enthält Richtlinien und Empfehlungen zur Verkürzung der Ladezeit und zur Leistungsverbesserung von HTML5-Formularen auf Mobilgeräten.

Die meisten Mobilgeräte verfügen über eine begrenzte Verarbeitungsleistung und Speicherkapazität. Dies trägt zur Verbesserung der Standby-Zeit für Mobilgeräte bei. Die Webbrowser, die auf einem Mobilgerät ausgeführt werden, haben Zugriff auf begrenzte Ressourcen (begrenzter Speicher und Verarbeitungskapazitäten). Sobald das Limit erreicht ist, wird das Browserverhalten langsam. Dieses Dokument enthält Empfehlungen, wie Sie die Größe eines HTML5-Formulars kontrollieren können. Ein kleineres Formular verstößt nicht gegen die Beschränkungen der Speicher- und Verarbeitungsleistung eines Geräts und bietet ein reibungsloses Erlebnis.

Obwohl die Empfehlungen, die in diesem Artikel diskutiert werden, auf HTML5-Formulare abzielen, gelten diese aber auch für XFA-basierte PDF-Formulare. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung von HTML5-Formularen bei. Es ist eine sorgfältige Planung erforderlich, um effiziente und produktive Formulare zu entwickeln. Fangen wir an:

## Knoten sind Währung von HTML5-Formularen, verwenden Sie sie sinnvoll {#nodes-are-currency-of-html-forms-spend-them-wisely}

Im Allgemeinen enthält ein XFA-Formular mehrere Elemente. Beispiel: Tabelle, Textfeld und Bilder. Jedes Element verfügt über mehrere Eigenschaften, um das Verhalten und Erscheinungsbild des Elements zu steuern. Wenn ein XFA-Formular im HTML5-Format wiedergegeben wird, werden alle XFA-Elemente und die entsprechenden Eigenschaften in Modell- oder HTML-DOM-Knoten konvertiert. Diese Knoten erhöhen die Größe und Komplexität eines DOM. Langsame Wiedergabe des HTML5-Formulars.

Es ist für die Browser einfacher, ein schlankeres DOM zu rendern. Sie können also die folgenden Optimierungen an einem XFA-Formular durchführen, um die Anzahl der Knoten zu reduzieren. Generieren Sie daher eine schlanke DOM-Struktur:

* Verwenden Sie die Beschriftungseigenschaft, um einem Feld eine Beschriftung hinzuzufügen. Verwenden Sie kein separates Textelement, um eine Beschriftung hinzuzufügen. Dies trägt dazu bei, zusätzliche Gewichtungen abzubauen, was zu Leistungssteigerungen führt. Es werden außerdem Layout-Probleme vermieden.
* Halten Sie die Anzahl der Textelemente auf einem Formular auf ein Minimum beschränkt. Zeichenelemente sind hilfreich bei der Verbesserung der Lesbarkeit und des Erscheinungsbilds, verfügen jedoch nicht über Speicherfunktionen für Informationen. Es wird empfohlen, mehrere Textelemente vom Typ Zeichnen in einem Textelement vom Typ Zeichnen zusammenzuführen. Lassen Sie keinen Stein unverarbeitet, um ein Formular schlanker zu machen.

## Lite-Formulare funktionieren besser, komprimieren Sie die Ressourcen. {#lite-forms-perform-better-keep-the-resources-compressed}

Ein HTML5-Formular kann mehrere externe Ressourcen wie Bild-, JavaScript- und CSS-Dateien enthalten. Jedes Mal, wenn ein Browser ein Formular anfordert, werden die externen Ressourcen über das Netzwerk gesendet. Die für die Übertragung über das Netzwerk benötigte Zeit ist direkt proportional zur Größe der Dateien.

Daher ist die Reduzierung der Größe der externen Ressourcen und die Verwendung von nur absolut erforderlichen Ressourcen die bevorzugte Methode zur Verbesserung der Leistung der Formulare. Sie können die folgenden Optimierungen an einem XFA-Formular durchführen, um die Größe externer Ressourcen eines Formulars zu reduzieren:

* Verwendung [komprimierte Bilder](/help/assets/best-practices-for-optimizing-the-quality-of-your-images.md). Dadurch werden die Netzwerkaktivität und der für die Wiedergabe eines Formulars erforderliche Arbeitsspeicher reduziert. Daher nimmt die Formularladezeit erheblich ab.
* Verwenden Sie die Minimierungsoption in AEM Configuration Manager (Day CQ HTML Library Manager), um JavaScript- und CSS-Dateien zu komprimieren. Weitere Informationen finden Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).
* Aktivieren Sie die Webkomprimierung. Dadurch wird die Größe der Anforderungen und Antworten reduziert, die von einem Formular stammen. Weitere Informationen finden Sie unter [Leistungsoptimierung des AEM Forms-Servers](https://helpx.adobe.com/de/aem-forms/6-3/performance-tuning-aem-forms.html).

## Halten Sie das Interesse am Leben, zeigen Sie nur erforderliche Felder an  {#keep-the-interest-alive-show-only-required-fields}

Ein HTML5-Formular kann Hunderte von Seiten umfassen. Ein Formular mit einer großen Anzahl von Feldern wird langsam im Browser geladen. Sie können die folgenden Optimierungen an einem XFA-Formular durchführen, um die Formulare mit einer großen Anzahl von Feldern und Seiten zu optimieren:

* Bewerten Sie die Aufteilung großer Formulare in mehrere Formulare. Sie können auch einen Formularsatz verwenden, um alle kleineren Formulare zu gruppieren und als eine Einheit darzustellen. Ein Formularsatz lädt nur erforderliche Formulare. Darüber hinaus können Sie in einem Formularsatz allgemeine Felder in verschiedenen Formularen konfigurieren, um Datenbindungen freizugeben. Mit den richtigen Datenbindungen müssen Benutzer allgemeine Informationen nur einmal ausfüllen. Diese werden dann in den nachfolgenden Formularen automatisch ausgefüllt. Weitere Informationen zu Formularsätzen finden Sie unter [Formularsatz in AEM Formularen](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html).
* Ziehen Sie die Aufteilung von Abschnitten in Betracht und verschieben Sie die einzelnen Abschnitte auf eine andere Seite. HTML5-Formulare laden jede Seite dynamisch bei der Bildlaufanforderung für die Seite. Nur gescrollte Seiten (die angezeigte Seite und die Seiten davor) werden im Speicher gespeichert. Die restlichen Seiten werden bei Bedarf geladen. Indem Sie also einen Abschnitt auf einer eigenen Seite aufteilen und verschieben, wird die zum Laden eines Formulars erforderliche Zeit reduziert. Sie können auch die erste Seite des Formulars als Landingpage verwenden. Sie ähnelt dem Inhaltsverzeichnis eines Buches. Eine Landingpage des Formulars enthält nur Links zu den anderen Abschnitten des Formulars. Dadurch wird die Ladezeit der ersten Formularseite erheblich verkürzt und das Benutzererlebnis verbessert.
* Halten Sie bedingte Abschnitte standardmäßig ausgeblendet. Machen Sie diese Abschnitte nur sichtbar, wenn eine bestimmte Bedingung erfüllt ist. Dies hilft, die DOM-Größe auf ein Minimum zu beschränken. Sie können auch mit Registerkartennavigation nur einen Abschnitt gleichzeitig anzeigen.

## Weniger ist mehr, reduzieren Sie die Anzahl der Seiten {#less-is-more-reduce-the-number-of-pages}

HTML5-Formulare können datengesteuerte Felder (Tabellen und Unterformulare) enthalten. Diese Felder erweitern die Größe des Formulars zur Laufzeit. Eine datengesteuerte Tabelle in einem HTML5-Formular kann beispielsweise Tausende von Zeilen umfassen. Solche Tabellen können zu einer Beeinträchtigung des Layouts und der Leistung führen. Die unten vorgeschlagenen Optimierungen können Ihnen dabei helfen, die Ladezeit von HTML5-Formularen mit datengesteuerten Feldern zu reduzieren:

* Verwenden Sie XFA-Skripterstellung, um die Seitennavigation zu erreichen und datengesteuerte Felder (Tabellen und Unterformulare) anzuzeigen. In der Seitennavigation werden nur bestimmte Daten auf einer Seite angezeigt. Dadurch wird der Vorgang des Zeichnens im Browser auf die jeweils angezeigten Felder beschränkt und die Navigation in einem Formular erleichtert. Außerdem sind die Benutzer auf Mobilgeräten nur an einer Untergruppe von Daten interessiert. Damit wird größere Benutzerfreundlichkeit geboten und die Zeit zum Laden der benötigten Daten wird verkürzt. Das Ergebnis sind zwei Lösungen. Beachten Sie auch, dass ausgelagerte Navigation nicht vorkonfiguriert verfügbar ist. Sie können XFA-Skripterstellung verwenden, um die Seitennavigation zu entwickeln.

* Bewerten Sie die Zusammenführung mehrerer schreibgeschützter Spalten in einer Spalte. Dadurch wird der für die Anzeige des Formulars erforderliche Arbeitsspeicher reduziert. Außerdem sollten Sie vermeiden, die Spalten anzuzeigen, für die keine Benutzereingaben erforderlich sind.
* Bewerten Sie die Aufteilung des datengesteuerten Formulars in eine [Formularsatz](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html), wenn die obigen Vorschläge nicht viele Verbesserungen bringen. Wenn eine Tabelle beispielsweise mehr als 1000 Zeilen enthält, verschieben Sie alle 100 Zeilen in ein anderes Formular. Das würde die Ladezeit und die Leistung der Formulare verbessern. Beachten Sie auch, dass ein Formularsatz eine konsolidierte Übermittlungs-XML für alle Formulare erzeugt. Um Daten für jedes Formular zu unterscheiden, verwenden Sie verschiedene Datenstämme. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html).

## Zweierleistung für Datensatzdokument (DOR) {#power-of-two-for-document-of-record-dor}

Ein XFA-Formular kann eine große Anzahl von Abschnitten enthalten, die nur für das Datensatzdokument (DOR) vorgesehen sind. Um die Anzahl der Knoten zu reduzieren und die Leistung eines solchen Formulars zu verbessern, können Sie verschiedene Kopien des Formulars beibehalten – eine Kopie zum Ausfüllen des Formulars und eine weitere zum Erzeugen des Datensatzdokuments auf dem Server. In der Kopie zum Ausfüllen des XFA-Formulars zeigen Felder, die nur zum Erfassen von Daten erforderlich sind. Behalten Sie im Generieren des Datensatzdokuments XFA-Felder bei, die nur in der gedruckten Ausgabe des Formulars erforderlich sind. Bevor Sie den vorgeschlagenen Ansatz wählen, bewerten Sie den Leistungsgewinn und den Wartungsaufwand.

## Empfohlene Lesevorgänge  {#recommended-reads}

Mit Adobe Experience Manager(AEM)-Formularen können Sie komplexe Transaktionen in einfache, beeindruckende digitale Erlebnisse umwandeln. Es bedarf jedoch gemeinsamer Anstrengungen zur Entwicklung effizienter und produktiver Formen. Neben HTML5 Forms finden Sie hier einige empfohlene Informationen zu allgemeinen AEM Best Practices:

* [Bewährte Verfahren für das Bereitstellen und Warten von AEM](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren zum Erstellen von Inhalten](/help/sites-authoring/best-practices.md)
* [Best Practices für die Verwaltung von AEM](/help/sites-administering/administer-best-practices.md)
* [Bewährte Verfahren zur Entwicklung von Lösungen](/help/sites-developing/best-practices.md)
* [Best Practices für die Arbeit mit adaptiven Formularen](/help/forms/using/adaptive-forms-best-practices.md)
* [AEM Forms-Server bettet Schriftarten nicht in ein dynamisches PDF-Formular ein](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-server-does-not-embed-fonts-to-dynamic-pdf-form.html)

## Schnellnachweiskarte {#quick-reference-card}

Sie können folgende Karte drucken (klicken Sie auf eine Karte, um eine hochauflösende Version herunterzuladen) und auf Ihrem Schreibtisch behalten, um eine kurze Referenz zu erhalten:
[![HTML5 Forms Best Practices - Schnellverweiskarte](do-not-localize/best-practices_reference_card.png)](assets/html5_forms_best_practices_reference_card.pdf)
