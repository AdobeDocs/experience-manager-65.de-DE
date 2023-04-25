---
title: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
description: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
exl-id: d541607f-c4c9-4dd5-aadf-64d4cb5f9f2a
source-git-commit: c96f83b84ed1473aee0ddcca08a0e585ec088aa1
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 67%

---

# Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework

## 1. Wird CIF GraphQL nur für Commerce verwendet oder ist es für die Abfrage von Inhalten verfügbar, die in AEM JCR erstellt wurden?

Adobe hat die GraphQL-APIs von Adobe Commerce&#39; als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Adobe Commerce&#39; und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL-API ist beim Zugriff auf Inhaltsfragmente unabhängig von der GraphQL-API von AEM.

## 2. Können Produkt-Assets (Bilder) von AEM über die Adobe Commerce-Administration gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es gibt keine offizielle AEM Assets-Adobe Commerce-Integration. Auf dem [Marketplace](https://marketplace.magento.com/partner/bounteous_ecomm) ist ein Partner-Connector verfügbar.

Alternativ können Sie als Workaround Produkt-Assets (Bilder) in AEM Assets speichern, aber Sie müssen die Asset-URLs manuell in Adobe Commerce speichern. Dynamic Media ist Teil von AEM Assets und funktioniert auf dieselbe Weise.

## 3. Ist es wichtig, wo die Commerce-Lösung implementiert wird? (Lokal oder in der Cloud)

Nein, es spielt keine Rolle, wo Ihre Commerce-Lösung implementiert wird. CIF und die AEM Storefront funktionieren unabhängig vom Bereitstellungsmodell. Wenn die Lösung jedoch mit der empfohlenen E2E-Referenzarchitektur implementiert wird, können E2E-Tests mit Leistungs-KPIs durchgeführt werden, die ein typisches Unternehmens-Kundenprofil darstellen. Dieser Prozess bietet zusätzliche Informationen, die als Benchmark verwendet werden können.

## 4. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## 5. Wenn man Produktdaten in seiner E-Commerce-Lösung aktualisiert, wird die Aktualisierung dann in Echtzeit an AEM gepusht? Oder erfolgt dies per Batch-Prozess?

Das CIF-Add-on, das mit AEM verwendet wird, ermöglicht auf Anforderung den Datenfluss von der E-Commerce Lösung zu AEM. Daher handelt es sich bei diesem Workflow nicht um einen Push- oder Batch-Prozess in Echtzeit, wenn Ihre Commerce-Lösung aktualisiert wird.

## 6. Welche Kataloggröße unterstützt AEM mit CIF?

Die Unterstützung der Kataloggröße hängt von einigen zusätzlichen Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und -seiten? Wie viele gleichzeitige Anfragen erwarten Sie während der Spitzenzeiten? Wie skalierbar sind die APIs Ihrer Commerce-Lösungen?

## 7. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden über GraphQL-Anfragen AEM und Clients bereitgestellt. Adobe empfiehlt, PIM in die Commerce-Engine (Adobe Commerce oder andere) zu integrieren, damit PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 8. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, ist eine Cache-Invalidierung erforderlich.

## 9. Wie funktioniert die Cache-Invalidierung für AEM Dispatcher mit AEM und Commerce?

Adobe empfiehlt die Einrichtung einer TTL-basierten Cache-Invalidierung für Seiten, die im Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Lagerinformationen empfiehlt Adobe, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html?lang=en)

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 11. Wie funktioniert die Suche bei AEM und Commerce mithilfe von CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anfrage mit dem Suchbegriff an die Lösung für den Handel, die dann eine Produktliste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Verwenden Sie den Schlüssel SLUG/url , um einen Verweis auf die Produktdetailseite zu erstellen.

## 12. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden bereits in PIM oder in Adobe Commerce übersetzt. Die Integration von AEM mit Adobe Commerce unterstützt die Verbindung zu mehreren Adobe Commerce-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Adobe Commerce-Store-Ansicht verknüpft.

## 13. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wenn ja, wo ist sie tätig? In AEM oder in der Commerce-Lösung?

Adobe empfiehlt die Verwaltung von Daten und Inhalten, die mit Marketing in AEM zusammenhängen. Versehen Sie Produktdaten aus Ihrer Commerce-Lösung mit zusätzlichen Attributen, indem Sie Inhaltsfragmente verwenden, oder erstellen Sie Experience Fragments für unstrukturierte Inhalte und verknüpfen Sie diese mit Ihren Produkten.

## 14. Wie gewährleistet ein Unternehmen PCI-Compliance bei der Verwendung von AEM für die gesamte Präsentationsschicht?

Adobe empfiehlt die Verwendung abstrakter Zahlungsmethoden. Dadurch kommuniziert der Browser-Client direkt mit dem Payment Gateway Provider, sodass die Adobe weder das Datum des Karteninhabers noch die Commerce-Lösungen enthält oder weitergibt. Dieser Ansatz erfordert nur PCI-Compliance der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf eine umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Adobe Commerce finden Sie unter [PCI-Compliance](https://business.adobe.com/de/products/magento/pci-compliance.html)

## 15. Wenn ich AEM- und Adobe Commerce-Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-kompatibel?

Ja, der Selbstbewertungsfragebogen D und die Konformitätsbescheinigung sind auf Anfrage erhältlich.

## 16. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://adobeio.typeform.com/to/obqgRm) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.
