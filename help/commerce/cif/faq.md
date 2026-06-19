---
title: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
description: Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework
exl-id: d541607f-c4c9-4dd5-aadf-64d4cb5f9f2a
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 80%

---

# Häufig gestellte Fragen zur Integration von AEM mit Commerce mithilfe des Commerce Integration Framework

## &#x200B;1. Wird CIF GraphQL nur für Commerce verwendet oder ist es für die Abfrage von Inhalten verfügbar, die im JCR von AEM erstellt wurden?

Adobe hat die GraphQL-APIs von Adobe Commerce&#39; als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Adobe Commerce&#39; und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL-API ist beim Zugriff auf Inhaltsfragmente unabhängig von der GraphQL-API von AEM.

## &#x200B;2. Können Produkt-Assets (Bilder) von AEM über den Adobe Commerce-Administrator gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es gibt keine offizielle Integration von AEM Assets mit Adobe Commerce. Auf dem [Marketplace](https://marketplace.magento.com/partner/bounteous_ecomm) ist ein Partner-Connector verfügbar.

Als Problemumgehung können Sie auch Produkt-Assets (Bilder) in AEM Assets speichern. Sie müssen die Asset-URLs jedoch manuell in Adobe Commerce speichern. Dynamic Media ist jetzt Teil von AEM Assets und funktioniert unverändert.

## &#x200B;3. Ist es wichtig, wo die Commerce-Lösung bereitgestellt wird? (Lokal oder in der Cloud)

Nein, es spielt keine Rolle, wo Ihre Lösung für den Handel bereitgestellt wird. CIF und die AEM-Storefront funktionieren unabhängig vom Implementierungsmodell. Wenn die Lösung jedoch mit der empfohlenen E2E-Referenzarchitektur implementiert wird, können E2E-Tests mit Leistungs-KPIs durchgeführt werden, die ein typisches Unternehmens-Kundenprofil darstellen. Dieser Prozess stellt zusätzliche Informationen bereit, die als Benchmark verwendet werden können.

## &#x200B;4. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## &#x200B;5. Wenn Sie Produktdaten in Ihrer Commerce-Lösung aktualisieren, erfolgt dies dann in Echtzeit an AEM? Oder erfolgt dies per Batch-Prozess?

Das CIF-Add-on, das mit AEM verwendet wird, ermöglicht auf Anforderung den Datenfluss von der Lösung für den Handel zu AEM. Daher handelt es sich bei diesem Workflow nicht um einen Push-Vorgang in Echtzeit oder einen Batch-Prozess, wenn eine Aktualisierung in Ihrer Lösung für den Handel erfolgt.

## &#x200B;6. Welche Kataloggröße unterstützt AEM mit CIF?

Die unterstützte Kataloggröße hängt von einigen zusätzlichen Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und -seiten? Wie viele gleichzeitige Anfragen erwarten Sie während der Spitzenzeiten? Wie skalierbar sind die APIs Ihrer Lösungen für den Handel?

## &#x200B;7. Wie fügt sich PIM in dieses Framework ein?

PIM-Daten werden AEM und den Clients über GraphQL-Anfragen zur Verfügung gestellt. Wir empfehlen, PIM in die E-Commerce-Engine (von Adobe Commerce oder anderen Anbietern) zu integrieren, sodass die PIM-Daten dann von der E-Commerce-Engine abgerufen werden können.

## &#x200B;8. Speichern Sie auch Preise und andere Daten über Dispatcher im Cache? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, ist eine Cache-Invalidierung erforderlich.

## &#x200B;9. Wie funktioniert die Cache-Invalidierung für AEM Dispatcher mit AEM und Commerce?

Es wird von Adobe empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die im Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten wird empfohlen, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html?lang=de).

## &#x200B;10. Gibt es eine Empfehlung für die einheitliche Suche nach AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## &#x200B;11. Wie funktioniert die Suche mit AEM und Commerce unter Verwendung von CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anfrage mit dem Suchbegriff an die Lösung für den Handel, die dann eine Produktliste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Verwenden Sie den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## &#x200B;12. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden bereits in PIM oder in Adobe Commerce übersetzt. Die Integration von AEM mit Adobe Commerce unterstützt die Verbindung zu mehreren Adobe Commerce-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Adobe Commerce-Store-Ansicht verknüpft.

## &#x200B;13. Gibt es eine Möglichkeit, die Produktdaten durch Geschäftstexte zu erweitern? Wenn ja, wo passiert dies? In AEM oder in der Lösung für den Handel?

Adobe empfiehlt, Marketing-bezogene Daten und Inhalte in AEM zu verwalten. Versehen Sie Produktdaten aus Ihrer Lösung für den Handel mit zusätzlichen Attributen, indem Sie Inhaltsfragmente verwenden, oder erstellen Sie Experience Fragments für unstrukturierte Inhalte und verknüpfen Sie diese mit Ihren Produkten.

## &#x200B;14. Wie stellt ein Unternehmen PCI-Compliance sicher, wenn AEM für die gesamte Präsentationsebene verwendet wird?

Adobe empfiehlt die Verwendung abstrakter Zahlungsmethoden. Dadurch kommuniziert der Browser-Client direkt mit dem Zahlungs-Gateway-Anbieter, sodass weder Adobe noch die Lösung für den Handel Informationen über den Karteninhaber enthält oder weitergibt. Dieser Ansatz erfordert nur PCI-Compliance der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf eine umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Adobe Commerce finden Sie unter [PCI-Compliance](https://business.adobe.com/de/products/magento/pci-compliance.html).

## &#x200B;15. Wenn ich AEM und Adobe Commerce Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-kompatibel?

Ja, der Selbstbewertungsfragebogen D und die Konformitätsbescheinigung sind auf Anfrage erhältlich.

## &#x200B;16. Wie kann ich eine E/A Runtime-Testlizenz anfordern?

Weitere Informationen zum Anfordern einer Testlizenz für I/O Runtime finden Sie unter [Zugriff erhalten](https://developer.adobe.com/runtime/docs/guides/overview/getting_access/).
