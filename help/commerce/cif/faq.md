---
title: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
description: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
exl-id: d541607f-c4c9-4dd5-aadf-64d4cb5f9f2a
source-git-commit: c96f83b84ed1473aee0ddcca08a0e585ec088aa1
workflow-type: ht
source-wordcount: '960'
ht-degree: 100%

---

# Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework

## 1. Wird CIF GraphQL nur für Commerce verwendet oder kann die Sprache auch für die Abfrage von Inhalten verwendet werden, die im JCR von AEM erstellt wurden?

Adobe hat die GraphQL-APIs von Adobe Commerce&#39; als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Adobe Commerce&#39; und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL-API ist beim Zugriff auf Inhaltsfragmente unabhängig von der GraphQL-API von AEM.

## 2. Können Produkt-Assets (Bilder) von AEM über die Adobe Commerce-Administration gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es gibt keine offizielle Integration von AEM Assets mit Adobe Commerce. Auf dem [Marketplace](https://marketplace.magento.com/partner/bounteous_ecomm) ist ein Partner-Connector verfügbar.

Als Problemumgehung können Sie auch Produkt-Assets (Bilder) in AEM Assets speichern. Sie müssen die Asset-URLs jedoch manuell in Adobe Commerce speichern. Dynamic Media ist jetzt Teil von AEM Assets und funktioniert unverändert.

## 3. Ist es wichtig, wo die Commerce-Lösung bereitgestellt wird? (Lokal oder in der Cloud)

Nein, es spielt keine Rolle, wo Ihre Commerce-Lösung bereitgestellt wird. CIF und die AEM-Storefront funktionieren unabhängig vom Implementierungsmodell. Wenn die Lösung jedoch mit der empfohlenen E2E-Referenzarchitektur implementiert wird, können E2E-Tests mit Leistungs-KPIs durchgeführt werden, die ein typisches Unternehmens-Kundenprofil darstellen. Dieser Prozess stellt zusätzliche Informationen bereit, die als Benchmark verwendet werden können.

## 4. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## 5. Wenn man Produktdaten in seiner E-Commerce-Lösung aktualisiert, wird die Aktualisierung dann in Echtzeit an AEM gepusht? Oder erfolgt dies per Batch-Prozess?

Das CIF-Add-on, das mit AEM verwendet wird, ermöglicht auf Anforderung den Datenfluss von der E-Commerce Lösung zu AEM. Daher handelt es sich bei diesem Workflow nicht um einen Push-Vorgang in Echtzeit oder einen Batch-Prozess, wenn eine Aktualisierung in Ihrer E-Commerce Lösung erfolgt.

## 6. Welche Kataloggröße unterstützt AEM mit CIF?

Die unterstützte Kataloggröße hängt von einigen zusätzlichen Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und -seiten? Wie viele gleichzeitige Anfragen erwarten Sie während der Spitzenzeiten? Wie skalierbar sind die APIs Ihrer Commerce-Lösungen?

## 7. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden AEM und den Clients über GraphQL-Anfragen zur Verfügung gestellt. Wir empfehlen, PIM in die E-Commerce-Engine (von Adobe Commerce oder anderen Anbietern) zu integrieren, sodass die PIM-Daten dann von der E-Commerce-Engine abgerufen werden können.

## 8. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, ist eine Cache-Invalidierung erforderlich.

## 9. Wie funktioniert die Cache-Invalidierung für AEM Dispatcher mit AEM und Commerce?

Es wird von Adobe empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die im Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten wird empfohlen, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html?lang=de).

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 11. Wie funktioniert die Suche bei AEM und Commerce mithilfe von CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anfrage mit dem Suchbegriff an die Lösung für den Handel, die dann eine Produktliste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Verwenden Sie den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## 12. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden bereits in PIM oder in Adobe Commerce übersetzt. Die Integration von AEM mit Adobe Commerce unterstützt die Verbindung zu mehreren Adobe Commerce-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Adobe Commerce-Store-Ansicht verknüpft.

## 13. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wenn ja, wo passiert dies? In AEM oder in der Commerce-Lösung?

Adobe empfiehlt, Marketing-bezogene Daten und Inhalte in AEM zu verwalten. Versehen Sie Produktdaten aus Ihrer Commerce-Lösung mit zusätzlichen Attributen, indem Sie Inhaltsfragmente verwenden, oder erstellen Sie Experience Fragments für unstrukturierte Inhalte und verknüpfen Sie diese mit Ihren Produkten.

## 14. Wie kann man als Unternehmen PCI-Compliance sicherstellen, wenn AEM für die gesamte Präsentationsebene verwendet wird?

Adobe empfiehlt die Verwendung abstrakter Zahlungsmethoden. Dadurch kommuniziert der Browser-Client direkt mit dem Zahlungs-Gateway-Anbieter, sodass weder Adobe noch die E-Commerce-Lösung Informationen über den Karteninhaber enthält oder weitergibt. Dieser Ansatz erfordert nur PCI-Compliance der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf eine umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Adobe Commerce finden Sie unter [PCI-Compliance](https://business.adobe.com/de/products/magento/pci-compliance.html).

## 15. Wenn ich AEM- und Adobe Commerce-Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-kompatibel?

Ja, der Selbstbewertungsfragebogen D und die Konformitätsbescheinigung sind auf Anfrage erhältlich.

## 16. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://adobeio.typeform.com/to/obqgRm) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.
