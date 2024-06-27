---
title: Empfohlene Vorgehensweisen für HTML5-Formulare
description: Stimmen Sie Ihre XFA-basierten HTML5-Formulare für optimale Leistung ab.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
content-type: reference
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 62ff6306-9989-43b0-abaf-b0a811f0a6a4
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1402'
ht-degree: 100%

---

# Empfohlene Vorgehensweisen für HTML5-Formulare{#best-practices-for-html-forms}

## Übersicht {#overview}

AEM Forms bietet eine Komponente mit dem Namen „HTML5-Formulare“. Auf diese Weise können Sie vorhandene XFA-basierte PDF-Formulare (XDP-Dateien) im HTML5-Format rendern. Dieses Dokument enthält Richtlinien und Empfehlungen, um die Ladezeit zu verkürzen und die Leistung von HTML5-Formularen auf Mobilgeräten zu verbessern.

Die meisten Mobilgeräte sind bezüglich Verarbeitungsleistung und Arbeitsspeicher begrenzt. Dies trägt dazu bei, dass die Standby-Zeit von Mobilgeräten verbessert wird. Die auf einem Mobilgerät ausgeführten Webbrowser haben Zugriff auf beschränkte Ressourcen (begrenzter Arbeitsspeicher und begrenzte Verarbeitungsfähigkeiten). Sobald das Limit erreicht ist, wird das Browser-Verhalten langsam. Dieses Dokument enthält Empfehlungen, um die Größe eines HTML5-Formulars zu kontrollieren. Ein kleineres Formular bringt den Arbeitsspeicher und die Verarbeitungsleistung eines Geräts nicht an ihre Grenzen und läuft mühelos.

Obwohl die Empfehlungen, die in diesem Artikel diskutiert werden, auf HTML5-Formulare abzielen, gelten diese aber auch für XFA-basierte PDF-Formulare. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung von HTML5-Formularen bei. Es ist eine sorgfältige Planung erforderlich, um effiziente und produktive Formulare zu entwickeln. Erste Schritte:

## Knoten sind die Währung der HTML5-Formulare, also nutzen Sie diese sinnvoll. {#nodes-are-currency-of-html-forms-spend-them-wisely}

Im Allgemeinen hat ein XFA-Formular mehrere Elemente.  Beispiel: Tabelle, Text und Bilder.  Jedes Element hat mehrere Eigenschaften, um das Verhalten und das Erscheinungsbild des Elements zu steuern. Wenn ein XFA-Formular im HTML5-Format gerendert wird, werden alle XFA-Elemente und die entsprechenden Eigenschaften in Modell- oder HTML DOM-Knoten konvertiert. Diese Knoten erhöhen die Größe und Komplexität eines DOM. Sie machen das HTML5-Formular für das Rendern langsamer.

Es ist einfacher für Browser, ein schlankeres DOM wiederzugeben. Sie können die folgenden Optimierungen auf einem XFA-Formular durchführen, um die Anzahl der Knoten zu reduzieren. Sie sollten daher eine schlanke DOM-Struktur erstellen:

* Mit der Titel-Eigenschaft können Sie einem Feld eine Bezeichnung hinzuzufügen. Verwenden Sie kein separates Textelement, um eine Bezeichnung hinzuzufügen. Es trägt dazu bei, zusätzliche Gewichtung loszuwerden, was zur Leistungssteigerung führt. Es werden außerdem Layout-Probleme vermieden.
* Halten Sie die Anzahl von Zeichen-Textelementen in einem Formular auf einem absoluten Minimum.  Zeichenelemente sind hilfreich beim Verbessern der Lesbarkeit und des Erscheinungsbilds, haben aber keine Möglichkeit, Informationen zu speichern. Es wird empfohlen, mehrere Zeichen-Textelemente in ein einzelnes Zeichen-Textelement zusammenzuführen. Nutzen Sie alle Möglichkeiten, um ein Formular schlanker zu machen.

## Lite-Formulare funktionieren besser und komprimieren die Ressourcen {#lite-forms-perform-better-keep-the-resources-compressed}

Ein HTML5-Formular kann mehrere externe Ressourcen enthalten, z. B. Bilder, JavaScript- und CSS-Dateien. Jedes Mal, wenn ein Browser ein Formular anfordert, werden die externen Ressourcen über das Netzwerk übertragen. Die benötigte Zeit für die Übertragung über das Netzwerk ist direkt zur Größe der Dateien proportional.

Deshalb ist die Reduzierung der Größe der externen Ressourcen und die Verwendung von nur absolut erforderlichen Ressourcen die bevorzugte Methode zur Verbesserung der Leistung der Formulare. Sie können die folgenden Optimierungen an einem XFA-Formular durchführen, um die Größe von externen Ressourcen eines Formulars zu verringern:

* Verwenden Sie [komprimierte Bilder](/help/assets/best-practices-for-optimizing-the-quality-of-your-images.md). Dies reduziert die Netzwerkaktivität und den erforderlichen Arbeitsspeicher für das Rendern eines Formulars. Deshalb verringert sich die Formularladezeit erheblich.
* Verwenden Sie die minify-Option im AEM Configuration Manager (Day CQ HTML Library Manager), um JavaScript- und CSS-Dateien zu komprimieren. Weitere Informationen finden Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).
* Aktivieren Sie die Web-Komprimierung. Die Größe der Anfragen und Antworten von einem Formular werden reduziert. Weitere Informationen finden Sie unter [Leistungsoptimierung für AEM-Formular-Server](https://helpx.adobe.com/de/aem-forms/6-3/performance-tuning-aem-forms.html).

## Das Interesse wachhalten – nur erforderliche Felder zeigen  {#keep-the-interest-alive-show-only-required-fields}

Ein HTML5-Formular kann Hunderte von Seiten umfassen. Ein Formular mit vielen Feldern wird im Browser langsam geladen. Sie können die folgenden Optimierungen in einem XFA-Formular durchführen, um Formulare mit vielen Feldern und Seiten zu optimieren:

* Überlegen Sie, große Formulare ggf. in mehrere Formulare aufzuteilen. Sie können auch einen Formularsatz verwenden, um alle kleineren Formulare zusammen zu gruppieren und sie als eine Einheit zu präsentieren. Ein Formularsatz lädt nur die erforderlichen Formulare. Darüber hinaus können Sie in einem Formularsatz gemeinsame Felder in verschiedenen Formularen so konfigurieren, dass sie Datenbindungen gemeinsam nutzen. Mit den richtigen Datenbindungen müssen Benutzer allgemeine Informationen nur einmal ausfüllen. Diese werden dann in den nachfolgenden Formularen automatisch ausgefüllt. Weitere Informationen zu Formularsätzen finden Sie unter [Formularsatz in AEM Forms](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html).
* Erwägen Sie, das Formular in Abschnitte aufzuteilen und jeden Abschnitt auf eine andere Seite zu verschieben. HTML5-Formulare laden jede Seite dynamisch, wenn das Scrollen einer Seite angefordert wird. Nur gescrollte Seiten (die angezeigte Seite und ihre vorherigen Seiten) werden im Arbeitsspeicher gespeichert. Die übrigen Seiten werden nach Bedarf geladen. Indem Sie also Abschnitte erstellen und diese auf eigene Seiten verschieben, reduziert sich die zum Laden eines Formulars erforderliche Zeit. Sie können zudem die erste Seite des Formulars als Landingpage verwenden. Dies ist mit dem Inhaltsverzeichnis eines Buchs vergleichbar. Eine Landingpage des Formulars enthält nur Links zu den anderen Abschnitten des Formulars. Dadurch wird die Ladezeit der ersten Formularseite erheblich verkürzt und das Anwendererlebnis verbessert.
* Lassen Sie bedingte Abschnitte standardmäßig ausgeblendet. Machen Sie diese Abschnitte nur sichtbar, wenn eine bestimmte Bedingung erfüllt ist. Auf diese Weise können Sie die DOM-Größe auf ein Minimum beschränken. Sie können zur Navigation auch Registerkarten verwenden, um nur jeweils einen Abschnitt anzuzeigen.

## Weniger ist mehr – die Anzahl der Seiten reduzieren {#less-is-more-reduce-the-number-of-pages}

HTML5-Formulare können datengesteuerte Felder (Tabellen und Teilformulare) enthalten. Diese Felder erhöhen die Größe des Formulars zur Laufzeit. Eine datengesteuerte Tabelle in einem HTML5-Formular kann beispielsweise Tausende von Zeilen umfassen. Solche Tabellen können das Layout und die Leistung beeinträchtigen. Die unten vorgeschlagenen Optimierungen können Ihnen dabei helfen, die Ladezeit von HTML5-Formularen mit datengesteuerten Feldern zu reduzieren:

* Nutzen Sie XFA-Scripting, um eine ausgelagerte Navigation zu ermöglichen und datengesteuerte Felder (Tabellen und Teilformulare) anzuzeigen. Bei der ausgelagerten Navigation werden nur bestimmte Daten auf einer Seite angezeigt. Dadurch wird der Vorgang des Zeichnens im Browser auf die jeweils angezeigten Felder beschränkt und die Navigation in einem Formular erleichtert. Außerdem sind die Benutzer auf Mobilgeräten nur an einer Untergruppe von Daten interessiert. Damit wird größere Benutzerfreundlichkeit geboten und die Zeit zum Laden der benötigten Daten wird verkürzt. Das Ergebnis sind zwei Lösungen. Beachten Sie auch, dass ausgelagerte Navigation nicht vorkonfiguriert verfügbar ist. Sie können XFA-Scripting verwenden, um eine ausgelagerte Navigation zu entwickeln.

* Überlegen Sie, ggf. mehrere schreibgeschützte Spalten in einer Spalte zusammenzuführen. Dadurch wird der für die Anzeige des Formulars erforderliche Arbeitsspeicher reduziert. Außerdem sollten Sie vermeiden, die Spalten anzuzeigen, für die keine Benutzereingabe erforderlich ist.
* Überlegen Sie, ggf. das datengesteuerte Formular in einen [Formularsatz](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html) aufzuteilen, wenn die obigen Vorschläge zu keinen deutlichen Verbesserungen führen. Wenn beispielsweise eine Tabelle mehr als 1000 Zeilen aufweist, verschieben Sie jeweils 100 Zeilen in ein anderes Formular. Das würde die Ladezeit und die Leistung der Formulare verbessern. Beachten Sie auch, dass ein Formularsatz eine konsolidierte Übermittlungs-XML für alle Formulare erzeugt. Um Daten für jedes Formular zu unterscheiden, verwenden Sie verschiedene Datenstämme. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html).

## Zweierpotenz für ein Datensatzdokument (DoR) {#power-of-two-for-document-of-record-dor}

Ein XFA-Formular kann viele Abschnitte enthalten, die nur für Datensatzdokumente (Documents of Record, DoR) vorgesehen sind. Um die Anzahl der Knoten zu reduzieren und die Leistung eines solchen Formulars zu verbessern, können Sie verschiedene Kopien des Formulars beibehalten – eine Kopie zum Ausfüllen des Formulars und eine weitere zum Erzeugen des Datensatzdokuments auf dem Server. Zeigen Sie in der Kopie zum Ausfüllen des XFA-Formulars die Felder an, die nur zum Erfassen von Daten erforderlich sind. Behalten Sie Felder, die nur in der gedruckten Ausgabe des Formulars erforderlich sind, im XFA zum Generieren des Datensatzdokuments bei. Bevor Sie sich für den vorgeschlagenen Ansatz entscheiden, sollten Sie die Leistungssteigerung und den höheren Wartungsaufwand in Ihre Überlegungen einfließen lassen.

## Weiterführende Informationen  {#recommended-reads}

Mit Adobe Experience Manager(AEM)-Formularen können Sie komplexe Transaktionen in einfache, beeindruckende digitale Erlebnisse transformieren. Zur Entwicklung effizienter und produktiver Formulare bedarf es jedoch gemeinsamer Anstrengungen. Zusätzlich zu HTML5-Formularen finden Sie hier einige Informationen zu bewährten Verfahren für AEM:

* [Bewährte Verfahren für das Bereitstellen und Warten von AEM](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren zum Erstellen von Inhalten](/help/sites-authoring/best-practices.md)
* [Best Practices für die Verwaltung von AEM](/help/sites-administering/administer-best-practices.md)
* [Bewährte Verfahren zur Entwicklung von Lösungen](/help/sites-developing/best-practices.md)
* [Best Practices für die Arbeit mit adaptiven Formularen](/help/forms/using/adaptive-forms-best-practices.md)
* [AEM Forms-Server bettet Schriftarten nicht in ein dynamisches PDF-Formular ein](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-server-does-not-embed-fonts-to-dynamic-pdf-form.html)

## Schnellnachweiskarte {#quick-reference-card}

Sie können die folgende Karte ausdrucken (wenn Sie auf die Karte klicken, können Sie eine Version mit hoher Auflösung herunterladen) und auf Ihrem Schreibtisch als Schnellreferenz bereithalten: 
[![Schnellreferenzkarte mit bewährten Verfahren für HTML5-Formulare](do-not-localize/best-practices_reference_card.png)](assets/html5_forms_best_practices_reference_card.pdf)
