---
title: eCommerce-Integrations-Framework
description: AEM eCommerce hilft Marketing-Fachleuten bei der Bereitstellung von markenspezifischen, personalisierten Einkaufserlebnissen über Web-, mobile und soziale Touchpoints hinweg.
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: d995f0d6-9e48-4228-ac82-f33a0b25b9d3
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 96%

---

# eCommerce{#ecommerce}

* [Konzepte](/help/commerce/cif-classic/administering/concepts.md)
* [Verwaltung (generisch)](/help/commerce/cif-classic/administering/generic.md)

Adobe bietet zwei Versionen des Commerce-Integrations-Frameworks:

<table>
 <tbody>
  <tr>
   <th><p> </p> </th>
   <th><p>CIF On-Premise</p> </th>
   <th><p>CIF Cloud</p> </th>
  </tr>
  <tr>
   <td><p>Unterstützte AEM-Versionen</p> </td>
   <td><p>AEM On-Premise oder AMS 6.x</p> </td>
   <td>AEM AMS 6.4 und 6.5</td>
  </tr>
  <tr>
   <td><p>Back-End</p> </td>
   <td>
    <ul>
     <li>AEM, Java</li>
     <li>Monolithische Integration, Pre-Build-Zuordnung (Vorlage)</li>
     <li>JCR-Repository</li>
    </ul> </td>
   <td>
    <ul>
     <li>Adobe Commerce</li>
     <li>Java und JavaScript</li>
     <li>Keine Commerce-Daten im JCR-Repository gespeichert</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Frontend</p> </td>
   <td><p>In AEM Server-seitig gerenderte Seiten</p> </td>
   <td>Gemischte Seitenanwendung (Hybrid-Rendering)</td>
  </tr>
  <tr>
   <td><p>Produktkatalog</p> </td>
   <td>
    <ul>
     <li>Produktimport-Tool, Editor, Caching in AEM</li>
     <li>Standardkataloge mit AEM- oder Proxy-Seiten</li>
    </ul> </td>
   <td>
    <ul>
     <li>Kein Produktimport</li>
     <li>Generische Vorlagen</li>
     <li>On-Demand-Daten über Connector</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Skalierbarkeit</p> </td>
   <td>
    <ul>
     <li>Unterstützt bis zu mehrere Millionen Produkte (je nach Anwendungsfall)</li>
     <li>Zwischenspeicherung im Dispatcher</li>
    </ul> </td>
   <td>
    <ul>
     <li>Keine Volumenbegrenzung</li>
     <li>Zwischenspeicherung im Dispatcher oder CDN</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standardisiertes Datenmodell</td>
   <td>Nein</td>
   <td>Ja, das Adobe Commerce GraphQL-Schema</td>
  </tr>
  <tr>
   <td>Verfügbarkeit</td>
   <td><p>Ja. SAP Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 (standardmäßig) zu unterstützen und die Kompatibilität mit Hybris 4 zu gewährleisten)</p> <p>Salesforce Commerce Cloud (Connector Open-Source-Unterstützung für AEM 6.4)</p> </td>
   <td>Ja, über Open Source über GitHub. Adobe Commerce (unterstützt 2.3.2 (standardmäßig) und ist mit 2.3.1 kompatibel).</td>
  </tr>
  <tr>
   <td>Wann ist sie einzusetzen?</td>
   <td>Eingeschränkte Anwendungsfälle: Zum Beispiel für Szenarien, in denen kleine, statische Kataloge importiert werden müssen.</td>
   <td>Bevorzugte Lösung in den meisten Anwendungsfällen</td>
  </tr>
 </tbody>
</table>

eCommerce übernimmt zusammen mit dem Produktdatenmanagement (PIM) die Aktivitäten einer Website, die sich auf den Verkauf von Produkten über einen Online-Store konzentriert:

* Erstellung, Lebensdauer und Veralterung eines Produkts
* Preisverwaltung
* Transaktionsmanagement
* Verwaltung von kompletten Katalogen
* Live- und zentralisierte Speicherdatensätze
* Web-Schnittstellen

AEM eCommerce hilft Marketing-Fachleuten bei der Bereitstellung von markenspezifischen, personalisierten Einkaufserlebnissen über Web-, mobile und soziale Touchpoints hinweg. In der Authoring-Umgebung von AEM können Sie die Seiten und Komponenten an den Kontext der Zielbesucherinnen und -besucher und Ihre Merchandising-Strategien anpassen, zum Beispiel:

* Produktseiten
* Warenkorbkomponenten
* Checkout-Komponenten

Die Implementierung ermöglicht den Echtzeitzugriff auf Produktinformationen. Dies kann verwendet werden, um Folgendes zu erzwingen:

* Integrität der Produktinformationen
* Preise
* Lagerbestand
* Variationen im Status eines Warenkorbs

>[!NOTE]
>
>Um das Integrationsframework mit externen eCommerce-Anbietern zu nutzen, müssen Sie zunächst die benötigten Pakete installieren. Weitere Informationen finden Sie unter [Bereitstellen von eCommerce](/help/commerce/cif-classic/deploying/ecommerce.md).
>
>Weitere Informationen zu erweiterten eCommerce-Funktionen finden Sie unter [Entwicklung von eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).

## Hauptfunktionen {#main-features}

AEM eCommerce bietet:

* Eine Reihe von **AEM-Komponenten, die vorkonfiguriert sind** und zeigen, was bei Ihrem Projekt möglich ist:

   * Produktanzeige
   * Warenkorb
   * Checkout
   * Kürzlich angesehene Produkte
   * Gutscheine
   * und mehr

  ![Beispiel für Geometrixx-Komponenten](/help/sites-administering/assets/chlimage_1-130.png)

  >[!NOTE]
  >
  >Mit dem Integrationsframework von AEM können Sie unabhängig von Ihrer E-Commerce-Engine zusätzliche AEM-Komponenten für E-Commerce-Funktionen entwickeln.

* **Suche** – mit entweder:

   * der AEM-Suche
   * der Suche des eCommerce-Systems
   * eine Suche von Drittanbietern
   * oder eine Kombination aus diesen Suchmöglichkeiten

  ![Suchbeispiel](/help/sites-administering/assets/chlimage_1-131.png)

* Nutzt die AEM-Funktion zur **Darstellung Ihrer Inhalte auf mehreren Kanälen**, ob im Browserfenster oder auf einem Mobilgerät. So stehen die Inhalte in dem Format bereit, das Ihre Besucher benötigen.

  ![Beispiel einer mobilen Ansicht](/help/sites-administering/assets/chlimage_1-132.png)

* Funktion zur **Entwicklung Ihrer eigenen Integrationsimplementierung basierend auf dem [AEM eCommerce-Framework](#the-framework)**.

  Die beiden derzeit verfügbaren Implementierungen basieren auf derselben Basis – zusätzlich zur allgemeinen API (dem Framework). Die Implementierung einer neuen Integration umfasst nur die Implementierung der Funktionen, die für Ihre Integration erforderlich sind. Frontendkomponenten können von jeder neuen Implementierung genutzt werden, da sie Schnittstellen verwenden (und somit unabhängig von der Implementierung sind).

* Die Möglichkeit der Entwicklung eines **erlebnisgesteuerten Handels, der auf Kundendaten und Aktivitäten basiert**. Auf diese Weise können Sie viele Szenarien umsetzen:

   * Beispielsweise können Sie einen Nachlass auf die Versandkosten anbieten, wenn der Gesamtbetrag der Bestellung einen bestimmten Wert überschreitet.
   * Eine andere Möglichkeit besteht darin, saisonale Angebote anzubieten, die auf Profildaten (z. B. dem Standort) basieren. Diese können dann bei Bedarf hervorgehoben werden, auch hier abhängig von anderen Faktoren.

  Im folgenden Beispiel wird ein Teaser angezeigt, da der Inhalt des Warenkorbs weniger als 75 USD beträgt:

  ![Warenkorb mit Client Context](/help/sites-administering/assets/chlimage_1-133.png)

  Dies kann geändert werden, wenn der Inhalt des Warenkorbs 75 USD überschreitet:

  ![Warenkorb mit Client Context nach Änderung](/help/sites-administering/assets/chlimage_1-134.png)

* Und andere Funktionen wie:

   * Inhalte des Warenkorbs werden sitzungsübergreifend beibehalten
   * Vollständiger Bestellverlauf
   * Express-Katalogaktualisierung

## Das Framework {#the-framework}

Im Abschnitt [Konzepte](/help/commerce/cif-classic/administering/concepts.md) wird das Framework detaillierter behandelt, doch im Folgenden sehen Sie eine allgemeine und schnelle Übersicht des Frameworks:

### Was? {#what}

* Das Integrations-Framework stellt die API, eine Reihe von Komponenten zur Veranschaulichung der Funktionalität und mehrere Erweiterungen bereit, um Beispiele für Verbindungsmethoden bereitzustellen.
* Das Framework stellt die für eine Projektimplementierung benötigte grundlegende Struktur bereit.
* Das Framework ist erweiterbar.
* Das Framework stellt keine vorkonfigurierte, sofort verwendbare Website bereit. Ein gewisses Maß an Entwicklungsarbeit ist immer erforderlich, um das Framework an Ihre Vorgaben anzupassen.

### Vorteile {#why}

* Bereitstellung der grundlegenden Mechanismen, um schnell eine benutzerdefinierte eCommerce-Website zu erstellen
* Tp bietet die Flexibilität, die für die Entwicklung einer echten eCommerce-Website erforderlich ist.
* Veranschaulichen Sie Best Practices.
