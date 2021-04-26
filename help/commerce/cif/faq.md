---
title: AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen
description: AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen
exl-id: 0a946d98-22c7-445d-984a-9e09c306ce45,aece1190-9530-4060-9b08-022da7068987
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 47%

---

# AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen

## 1. Wird CIF GraphQL nur für den Handel verwendet oder ist dies für die Abfrage von Inhalten verfügbar, die mit AEM JCR erstellt wurden?

Adobe hat die GraphQL-APIs von Magento als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Magento und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL API ist unabhängig von AEM GraphQL API für den Zugriff auf Inhaltsfragmente.

## 2. Können Produkt-Assets (Images) über den Adobe Commerce-Administrator (Magento) gespeichert und über AEM referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es gibt keine offizielle AEM Assets-Magento-Integration. Auf dem [marketplace](https://marketplace.magento.com/bounteous-dam.html) ist ein Partneranschluss verfügbar.

Alternativ können Sie als Problemumgehung Produkt-Assets (Bilder) in AEM Assets speichern, aber Sie müssen die Asset-URLs manuell in Magento speichern. Dynamic Media ist jetzt Teil von AEM Assets. Die Funktionalität der Lösung bleibt unverändert bestehen.

## 3. Ist es wichtig, wo die Commerce-Lösung bereitgestellt wird? (Lokal oder in der Cloud)

Nein, es spielt keine Rolle, wo Ihre Commerce-Lösung bereitgestellt wird. CIF und der AEM Store funktionieren unabhängig vom Bereitstellungsmodell. Wenn die Lösung jedoch mit der empfohlenen E2E-Referenzarchitektur bereitgestellt wird, können E2E-Tests mit Performance-KPIs ausgeführt werden, die ein typisches Enterprise-Profil darstellen. Dadurch werden zusätzliche Informationen bereitgestellt, die als Benchmark verwendet werden können.

## 4. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. Es werden keine Produkt- oder Katalogdaten in AEM importiert und gespeichert.

## 5. Wenn Sie Produktdaten in Ihrer Commerce-Lösung aktualisieren, ist das ein Echtzeit-AEM? Oder erfolgt dies per Batch-Prozess?

Das mit AEM verwendete CIF-Add-on ermöglicht den Datenfluss von der Commerce-Lösung zu AEM On-Demand. Daher handelt es sich bei diesem Vorgang nicht um einen Push- oder Batch-Vorgang in Echtzeit, wenn Ihre Commerce-Lösung aktualisiert wird.

## 6. Welche Kataloggröße AEM mit CIF-Unterstützung?

Dies hängt von einigen zusätzlichen Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und Seiten? Wie viele gleichzeitige Anforderungen erwarten Sie während der Stoßzeiten? Wie skalierbar sind die APIs Ihrer Commerce-Lösungen?

## 7. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden über GraphQL-Anfragen für AEM und Clients bereitgestellt. Unsere Empfehlung ist, PIM in die Commerce-Engine (Magento oder andere) zu integrieren, damit PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 8. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, muss der Cache invalidiert werden.

## 9. Wie funktioniert die Cache-Ungültigmachung für AEM Dispatcher mit AEM und Commerce?

Es wird empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die in AEM Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten empfiehlt es sich, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/kb/optimizing-the-dispatcher-cache.html).

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist in der Regel sehr kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 11. Wie funktioniert die Suche mit AEM und dem Handel mit CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anforderung mit dem Suchbegriff an die Commerce-Lösung, die dann eine Liste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Wir verwenden den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## 12. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden in der Regel bereits im PIM-System oder in Magento übersetzt. Die Integration von AEM und Magento unterstützt die Verbindung zu mehreren Magento-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Magento-Store-Ansicht verknüpft.

## 13. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wo kann dies geschehen? In AEM oder in der Commerce-Lösung?

Wir empfehlen, Marketing-bezogene Daten und Inhalte in AEM zu verwalten. Dekorieren Sie Produktdaten aus Ihrer Commerce-Lösung mit zusätzlichen Attributen mithilfe von Inhaltsfragmenten oder erstellen und verknüpfen Sie Erlebnisfragmente für nicht strukturierte Inhalte mit Ihren Produkten.

## 14. Wie lässt sich PCI-Compliance sicherstellen, wenn AEM für die gesamte Präsentationschicht verwendet wird?

Es wird empfohlen, abstrakte Zahlungsmethoden zu verwenden. Dadurch wird der Browser-Client direkt mit dem Payment Gateway Provider kommuniziert, sodass weder die Adobe noch die Commerce-Lösungen Karteninhaberdaten speichern oder weitergeben. Dieser Ansatz erfordert nur die PCI-Kompatibilität der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Kompatibilität mit Magento finden Sie unter <https://magento.com/pci-compliance>

## 15. Wenn ich AEM und Magento Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-konform?

Ja, Selbstbewertungsfragebogen D und Konformitätsbescheinigung sind auf Anfrage erhältlich.

## 16. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://adobeio.typeform.com/to/obqgRm) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.
