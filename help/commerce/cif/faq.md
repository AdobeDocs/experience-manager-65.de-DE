---
title: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
description: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
exl-id: 0a946d98-22c7-445d-984a-9e09c306ce45
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 75%

---

# Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework

## 1. Wird CIF GraphQL nur für Commerce verwendet oder kann die Sprache auch für die Abfrage von Inhalten verwendet werden, die im JCR von AEM erstellt wurden?

Adobe hat die GraphQL-APIs von Adobe Commerce als offizielle Commerce-API für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Adobe Commerce und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL-API ist beim Zugriff auf Inhaltsfragmente unabhängig von der GraphQL-API von AEM.

## 2. Können Produkt-Assets (Bilder) von AEM über Adobe Commerce Admin gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es ist keine offizielle AEM Assets - Adobe Commerce -Integration verfügbar. Auf dem [Marketplace](https://marketplace.magento.com/bounteous-dam.html) ist ein Partner-Connector verfügbar.

Alternativ können Sie als Workaround Produkt-Assets (Bilder) in AEM Assets speichern, aber Sie müssen die Asset-URLs manuell in Adobe Commerce speichern. Dynamic Media ist jetzt Teil von AEM Assets. Die Funktionalität der Lösung bleibt unverändert bestehen.

## 3. Ist es wichtig, wo die Commerce-Lösung implementiert wird? (Lokal oder in der Cloud)

Nein, es spielt keine Rolle, wo Ihre Commerce-Lösung implementiert wird. CIF und die AEM-Storefront funktionieren unabhängig vom Implementierungsmodell. Wenn die Lösung jedoch mit der empfohlenen E2E-Referenzarchitektur implementiert wird, können E2E-Tests mit Leistungs-KPIs durchgeführt werden, die ein typisches Unternehmens-Kundenprofil darstellen. Dadurch werden zusätzliche Informationen bereitgestellt, die als Benchmark verwendet werden können.

## 4. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## 5. Wenn man Produktdaten in seiner E-Commerce-Lösung aktualisiert, wird die Aktualisierung dann in Echtzeit an AEM gepusht? Oder erfolgt dies per Batch-Prozess?

Das CIF-Add-on, das mit AEM verwendet wird, ermöglicht auf Anforderung den Datenfluss von der E-Commerce Lösung zu AEM. Daher handelt es sich bei diesem Vorgang nicht um einen Push-Vorgang in Echtzeit oder einen Batch-Prozess, wenn eine Aktualisierung in Ihrer E-Commerce Lösung erfolgt.

## 6. Welche Kataloggröße unterstützt AEM mit CIF?

Dies hängt von einigen weiteren Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und -seiten? Wie viele gleichzeitige Anfragen erwarten Sie während der Spitzenzeiten? Wie skalierbar sind die APIs Ihrer Commerce-Lösungen?

## 7. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden über GraphQL-Anfragen für AEM und Clients bereitgestellt. Wir empfehlen, PIM in die Commerce-Engine (Adobe Commerce oder andere) zu integrieren, damit PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 8. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, muss der Cache invalidiert werden.

## 9. Wie funktioniert die Cache-Invalidierung für AEM Dispatcher mit AEM und Commerce?

Es wird empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die in AEM Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten empfiehlt es sich, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/kb/optimizing-the-dispatcher-cache.html).

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist in der Regel sehr kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 11. Wie funktioniert die Suche bei AEM und Commerce mithilfe von CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anfrage mit dem Suchbegriff an die Commerce-Lösung, die dann eine Produktliste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Wir verwenden den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## 12. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden in der Regel bereits in PIM oder in Adobe Commerce übersetzt. Die AEM-Adobe Commerce-Integration unterstützt die Verbindung zu mehreren Adobe Commerce Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM Site mit einer Adobe Commerce Store-Ansicht verknüpft.

## 13. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wo kann dies geschehen? In AEM oder in der Commerce-Lösung?

Es wird empfohlen, Marketing-bezogene Daten und Inhalte in AEM zu verwalten. Dekorieren Sie Produktdaten aus Ihrer Commerce-Lösung mit zusätzlichen Attributen mithilfe von Inhaltsfragmenten oder erstellen und verknüpfen Sie Experience Fragments für unstrukturierte Inhalte mit Ihren Produkten.

## 14. Wie lässt sich PCI-Compliance sicherstellen, wenn AEM für die gesamte Präsentationschicht verwendet wird?

Es wird empfohlen, abstrakte Zahlungsmethoden zu verwenden. Dadurch kommuniziert der Browser-Client direkt mit dem Payment Gateway Provider, sodass weder Adobe noch die Commerce-Lösungen Daten von Karteninhabern speichern oder weitergeben. Dieser Ansatz erfordert nur PCI-Compliance der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Adobe Commerce finden Sie unter [PCI-Compliance](https://business.adobe.com/products/magento/pci-compliance.html)

## 15. Wenn ich AEM und Adobe Commerce-Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-kompatibel?

Ja, der Selbstbewertungsfragebogen D und die Konformitätsbescheinigung sind auf Anfrage erhältlich.

## 16. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://adobeio.typeform.com/to/obqgRm) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.
