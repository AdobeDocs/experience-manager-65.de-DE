---
title: Produkt-Cockpit
description: Arbeiten mit dem Produkt-Cockpit
exl-id: 05ef2604-1d52-4397-a696-0b64717cc3cc
source-git-commit: b00ed4ed146b89aece9af1d267c890a360a236e9
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 72%

---

# Produkt-Cockpit {#product-cockpit}

## Übersicht {#overview}

Das Produkt-Cockpit bietet einen einheitlichen Überblick über verknüpfte Produktkataloge und zugehörige Inhalte. Alle zugehörigen Inhalte verfügen über Links, über die Sie schnell vom Cockpit aus darauf zugreifen können.

Staging-Produktdaten beinhalten zukünftig jede Mutation wie neue Kategorien, Produkte oder aktualisierte Eigenschaften.

>[!NOTE]
>
>Der Begriff „Produktkatalog“ ist gleichbedeutend mit „Handels-Shop“, „Store-Ansicht“ und ähnlichen Ausdrücken.

## Konfiguration {#configuration}

Produktkataloge müssen in AEM konfiguriert werden. Siehe [Konfigurieren von Shops und Katalogen](/help/commerce/cif/getting-started.md#catalog) für weitere Informationen.

Das Aktivieren von gestaffelten Katalogfunktionen erfordert eine Authentifizierung. Siehe [Erste Schritte](/help/commerce/cif/getting-started.md) für weitere Informationen.

>[!NOTE]
>
>Staging-Katalogfunktionen sind nur bei Adobe Commerce- und Drittanbieter-Connectoren verfügbar, die Token-basierte Authentifizierung unterstützen.

## Öffnen des Produkt-Cockpits {#opening-product-cockpit}

Der einfachste Weg, um auf das Produkt-Cockpit zuzugreifen, ist über das &#39;Commerce&#39;-Menü in AEM Hauptmenü. Es ist auch möglich, Omnisearch (Suche nach „Commerce“) zu verwenden oder `https://<yourAEMInstance>/commerce.html` zu öffnen.

![AEM-Menü](/help/commerce/cif/assets/aem-menu.png)

## Durchsuchen von Produktkatalogen {#browsing-product-catalogs}

Das Produkt-Cockpit ist hierarchisch nach der Produktkatalogstruktur organisiert. Die erste Ebene zeigt die Katalogstammebene aller konfigurierten Produktkataloge einschließlich Metadaten des Commerce-Backends.

![Konfigurierte Kataloge](/help/commerce/cif/assets/catalog-overview.png)

Durch Klicken auf eine Kategorie werden die untergeordneten Elemente der angeklickten Kategorie geladen.

![Untergeordnete Elemente einer Kategorie](/help/commerce/cif/assets/catalog-category-children.png)

Wenn Sie auf ein Produkt klicken, werden Produktvarianten geladen, sofern verfügbar.

![Produktvarianten](/help/commerce/cif/assets/catalog-product-variation.png)

>[!NOTE]
>
>Produktkatalogdaten in AEM sind Daten, die in Echtzeit über den konfigurierten Commerce-Endpunkt abgerufen werden. In AEM werden keine Produktkatalogdaten gespeichert.

## Durchsuchen von Produktkatalogen {#searching-product-catalog}

Eine Volltextsuche über den gesamten Produktkatalog wird auf der linken Filter-Registerkarte angeboten, um Produkte schnell zu finden.

![Durchsuchen](/help/commerce/cif/assets/search-cockpit.png)

## Durchsuchen des gestaffelten Produktkatalogs {#staged-product-catalogs}

Standardmäßig zeigt das Produkt-Cockpit Live-Produktkatalogdaten an. Mithilfe des &quot;STAGED CATALOG&quot;auf der Registerkarte mit dem linken Filter wird der Produktkatalog für ein beliebiges Datum geladen.

![gestaffelter Katalog](/help/commerce/cif/assets/staged-cockpit.png)

## Eigenschaften des Produktkatalogs {#catalog-properties}

Durch Klicken auf das Eigenschaftensymbol eines Produkts oder einer Kategorie wird die Eigenschaftenansicht des ausgewählten Objekts geöffnet. Offene Eigenschaften einer Produktvariante sind gleich dem Öffnen der Hauptprodukteigenschaften.

### Registerkarten „Commerce“ {#tabs}

Die Registerkarten „Allgemein“ und „Varianten“ zeigen vordefinierte Commerce-Eigenschaften, die aus dem Commerce-Backend stammen. Diese Daten (einschl. Varianten) sind schreibgeschützte Daten in AEM, da das Aufzeichnungssystem das Commerce-Backend ist. Die Registerkarte „Varianten“ wird nur für Produkte mit Varianten angezeigt und enthält eine Liste aller Varianten.

![Katalog-Eigenschaften](/help/commerce/cif/assets/catalog-properties.png)

### AEM-Inhaltsregisterkarten {#content-tabs}

Diese Registerkarten, gruppiert nach AEM Inhaltstypen (Experience Fragments, Inhaltsfragmente, zugehörige Assets), zeigen AEM-Inhalte an, die mit dem Commerce-Objekt verknüpft sind. Durch die Aktion „Details anzeigen“ wird eine neue Browser-Registerkarte mit dem ausgewählten Inhalt geöffnet.

![Inhaltseigenschaften](/help/commerce/cif/assets/content-properties.png)
