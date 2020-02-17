---
title: eCommerce
seo-title: eCommerce
description: Mit AEM eCommerce können Marketingexperten personalisierte Marken-Einkaufserlebnisse über Web-, Mobile- und Social-Touchpoints bereitstellen.
seo-description: Mit AEM eCommerce können Marketingexperten personalisierte Marken-Einkaufserlebnisse über Web-, Mobile- und Social-Touchpoints bereitstellen.
uuid: 75818c60-1cf1-4a91-94ce-d722563b661c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: e972ee05-f0cb-40ca-9ae2-34395791c709
docset: aem65
translation-type: tm+mt
source-git-commit: 46610888fd61900c52b197e73a8a5850dc9c4c35

---


# eCommerce{#ecommerce}

* [Konzepte](/help/sites-administering/concepts.md)
* [Verwaltung (generisch)](/help/sites-administering/generic.md)

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
     <li>Monolithische Integration, voreingestellte Zuordnung (Vorlage)</li>
     <li>JCR-Repository</li>
    </ul> </td>
   <td>
    <ul>
     <li>Magento</li>
     <li>Java &amp; Javascript</li>
     <li>Keine Commerce-Daten im JCR-Repository gespeichert</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Front-End</p> </td>
   <td><p>Server-seitig wiedergegebene AEM-Seiten</p> </td>
   <td>Gemischte Seitenanwendung (hybrides Rendering)</td>
  </tr>
  <tr>
   <td><p>Produktkatalog</p> </td>
   <td>
    <ul>
     <li>Produktimporteur, Editor, Zwischenspeicherung in AEM</li>
     <li>Standardkataloge mit AEM- oder Proxy-Seiten</li>
    </ul> </td>
   <td>
    <ul>
     <li>Kein Produktimport</li>
     <li>Allgemeine Vorlagen</li>
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
     <li>Zwischenspeicherung im Dispatcher oder im CDN</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standardisiertes Datenmodell</td>
   <td>Nein</td>
   <td>Ja, Magento GraphQL-Schema</td>
  </tr>
  <tr>
   <td>Verfügbarkeit</td>
   <td><p>Ja. SAP Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 (standardmäßig) zu unterstützen und Kompatibilität mit Hybris 4 zu gewährleisten)</p> <p>Salesforce Commerce Cloud (Open-Source-Connector zur Unterstützung von AEM 6.4)</p> </td>
   <td>Ja, über Open Source von GitHub. Magento Commerce (unterstützt Magento 2.3.2 (standardmäßig) und ist mit Magento 2.3.1 kompatibel).</td>
  </tr>
  <tr>
   <td>Wann ist sie einzusetzen?</td>
   <td>Eingeschränkte Anwendungsfälle: z. B. wenn kleine, statische Kataloge importiert werden müssen</td>
   <td>Bevorzugte Lösung in den meisten Anwendungsfällen</td>
  </tr>
 </tbody>
</table>

Zusammen mit der Produktdatenverwaltung (PIM) verarbeitet eCommerce die Aktivitäten auf einer Website mit Schwerpunkt auf dem Verkauf von Produkten über einen Online-Shop:

* Erstellung, Lebensdauer und Veralterung eines Produkts
* Preisverwaltung
* Transaktionsverwaltung
* Verwaltung von kompletten Katalogen
* Live- und zentralisierte Speicherdatensätze
* Webschnittstellen

Mit AEM eCommerce können Marketingexperten personalisierte Marken-Einkaufserlebnisse über Web-, Mobile- und Social-Touchpoints bereitstellen. In der Authoring-Umgebung von AEM können Sie die Seiten und Komponenten an den Kontext des Zielbesuchers und Ihre Merchandising-Strategien anpassen, zum Beispiel:

* Produktseiten
* Warenkorbkomponenten
* Kassenkomponenten

Die Implementierung ermöglicht den Echtzeitzugriff auf Produktdaten. Damit lässt sich Folgendes durchsetzen:

* Integrität der Produktdaten
* Preise
* Lagerbestand
* Variationen im Status eines Warenkorbs

>[!NOTE]
>
>Um das Integrationsframework mit externen eCommerce-Anbietern zu nutzen, müssen Sie zunächst die benötigten Pakete installieren. For more information, see [Deploying eCommerce](/help/sites-deploying/ecommerce.md).
>
>For information about extending eCommerce capabilities, see [Developing eCommerce](/help/sites-developing/ecommerce.md).

## Zentrale Funktionen {#main-features}

AEM eCommerce bietet Folgendes:

* A number of **out-of-the-box AEM components** to illustrate what can be achieved for your project:

   * Produktanzeige
   * Warenkorb
   * Kasse
   * Kürzlich angezeigte Produkte
   * Gutscheine
   * und mehr
   ![](assets/chlimage_1-130.png)

   >[!NOTE]
   >
   >Mit dem Integrationsframework von AEM können Sie unabhängig von Ihrer eCommerce-Engine zusätzliche AEM-Komponenten für eCommerce-Funktionen entwickeln.

* **Suche** – entweder:

   * die AEM-Suche
   * die Suche des eCommerce-Systems
   * die Suche eines Drittanbieters (z. B. Search&amp;Promote)
   * oder eine Kombination aus diesen Suchmöglichkeiten
   ![](assets/chlimage_1-131.png)

* Uses the AEM ability to **present your content on multiple channels**, be that full browser window or mobile device. So stehen die Inhalte in dem Format bereit, das Ihre Besucher benötigen.

   ![](assets/chlimage_1-132.png)

* Funktion zur **Entwicklung Ihrer eigenen Integrationsimplementierung basierend auf dem[AEM eCommerce-Framework](#the-framework)**.

   Die beiden aktuell verfügbaren Implementierungen setzen auf derselben Basis auf und nutzen die allgemeine API (das Framework). Bei der Implementierung einer neuen Integration müssen Sie nur die Funktionen implementieren, die für Ihre Implementierung erforderlich sind. Frontendkomponenten können von jeder neuen Implementierung genutzt werden, da sie Schnittstellen verwenden (und somit unabhängig von der Implementierung sind).

* Möglichkeit zur Entwicklung von **erlebnisgesteuertem Handel basierend auf den Daten und Aktivitäten der Käufer**. Damit können Sie zahlreiche Szenarien umsetzen:

   * Beispielsweise können Sie einen Nachlass auf die Versandkosten anbieten, wenn der Gesamtbetrag der Bestellung einen bestimmten Wert überschreitet.
   * Oder Sie bieten saisonale Angebote an, die Profildaten (wie den Ort) nutzen. Diese könnten dann bei Bedarf abhängig von anderen Faktoren hervorgehoben werden.
   Im folgenden Beispiel wird ein Teaser angezeigt, da die Artikel im Warenkorb einen Wert von unter 75 USD aufweisen:

   ![](assets/chlimage_1-133.png)

   Wenn die Artikel im Warenkorb den Wert von 75 USD überschreiten, erfolgt eine Änderung:

   ![](assets/chlimage_1-134.png)

* Weitere Funktionen, darunter:

   * Artikel im Warenkorb werden sitzungsübergreifend gespeichert.
   * Vollständiger Bestellverlauf
   * Eilkatalogaktualisierung

## Das Framework {#the-framework}

Im Abschnitt [Konzepte](/help/sites-administering/concepts.md) finden Sie detailliertere Informationen zum Framework. Nachfolgend erhalten Sie einen groben Überblick über das Framework:

### Eigenschaften des Frameworks {#what}

* Das Integrationsframework stellt die API, mehrere Komponenten zur Veranschaulichung der Funktionalität und einige Erweiterungen für Beispiele für Anbindungsmethoden bereit.
* Das Framework stellt die grundlegende Struktur bereit, die für eine Projektimplementierung erforderlich ist.
* Das Framework ist erweiterbar.
* Das Framework stellt keine vorkonfigurierte, sofort verwendbare Website bereit. Ein gewisses Maß an Entwicklungsarbeit ist immer erforderlich, um das Framework an Ihre Vorgaben anzupassen.

### Why? {#why}

* Bereitstellung der grundlegenden Mechanismen, die zur schnellen Realisierung einer benutzerspezifischen eCommerce-Site erforderlich sind.
* Flexibilität, die für die Entwicklung einer echten eCommerce-Website nötig ist
* Veranschaulichung bewährter Verfahren