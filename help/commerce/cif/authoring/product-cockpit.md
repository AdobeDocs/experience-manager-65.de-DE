---
title: Produkt-Cockpit
description: Arbeiten mit dem Produkt-Cockpit
source-git-commit: f3e286c7b5404812655f3b257de17be7bfde7487
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Produkt-Cockpit {#product-cockpit}

## Übersicht {#overview}

Das Produkt-Cockpit bietet einen einheitlichen Überblick über verknüpfte Produktkataloge und zugehörige Inhalte. Alle zugehörigen Inhalte verfügen über Links, über die Sie schnell vom Cockpit aus darauf zugreifen können.

Staging-Produktdaten beinhalten zukünftig jede Mutation wie neue Kategorien, Produkte oder aktualisierte Eigenschaften.

>[!NOTE]
>
>Der Begriff &quot;Produktkatalog&quot;ist mit Commerce Store-, Store-Ansicht- und ähnlichen Ausdrücken austauschbar.

## Konfiguration {#configuration}

Produktkataloge müssen in AEM konfiguriert werden. Siehe [Konfigurieren von Speichern und Katalogen](/help/commerce/cif/getting-started.md#catalog) für weitere Informationen.

Die Aktivierung von Stage-Katalogfunktionen erfordert Authentifizierung. Siehe [Erste Schritte](/help/commerce/cif/getting-started.md) für weitere Informationen.

>[!NOTE]
>
>Staging-Katalogfunktionen sind nur bei Adobe Commerce- und Drittanbieter-Connectoren verfügbar, die Token-basierte Authentifizierung unterstützen.

## Öffnen des Produkt-Cockpits {#opening-product-cockpit}

Der einfachste Weg, auf das Produkt-Cockpit zuzugreifen, ist über das &#39;Commerce&#39;-Menü in AEM Hauptmenü. Es ist auch möglich, Omnisearch (Suche nach Commerce) oder das Öffnen von `https://<yourAEMInstance>/commerce.html`.

![Menü AEM](/help/commerce/cif/assets/aem-menu.png)

## Durchsuchen von Produktkatalogen {#browsing-product-catalogs}

Das Produkt-Cockpit ist hierarchisch nach der Produktkatalogstruktur organisiert. Die erste Ebene zeigt die Katalogstammebene aller konfigurierten Produktkataloge einschließlich Metadaten des Commerce-Backend.

![Konfigurierte Kataloge](/help/commerce/cif/assets/catalog-overview.png)

Durch Klicken auf eine Kategorie werden die untergeordneten Elemente der angeklickten Kategorie geladen.

![Kategorienunterkinder](/help/commerce/cif/assets/catalog-category-children.png)

Wenn Sie auf ein Produkt klicken, werden Produktvarianten geladen, sofern verfügbar.

![Produktvarianten](/help/commerce/cif/assets/catalog-product-variation.png)

>[!NOTE]
>
>Produktkatalogdaten in AEM sind Daten, die in Echtzeit über den konfigurierten Commerce-Endpunkt abgerufen werden. In AEM werden keine Produktkatalogdaten gespeichert.

## Suchen von Produktkatalogen {#searching-product-catalog}

Eine Volltextsuche über den vollständigen Produktkatalog finden Sie auf der Registerkarte mit dem linken Filter , um Produkte schnell zu finden.

![Suchen](/help/commerce/cif/assets/search-cockpit.png)

## Staging-Produktkatalog durchsuchen {#staged-product-catalogs}

Standardmäßig zeigt das Produkt-Cockpit Live-Produktkatalogdaten an. Mithilfe des &quot;STAGED CATALOG&quot;-Tabs auf der linken Filterseite wird der Produktkatalog für jedes ausgewählte Datum geladen.

![gestaffelter Katalog](/help/commerce/cif/assets/staged-cockpit.png)

## Eigenschaften des Produktkatalogs {#catalog-properties}

Durch Klicken auf das Eigenschaftensymbol eines Produkts oder einer Kategorie wird die Eigenschaftenansicht des ausgewählten Objekts geöffnet. Die offenen Eigenschaften einer Produktvariante entsprechen dem Öffnen der Hauptprodukteigenschaften.

### Commerce-Registerkarten {#tabs}

Die Registerkarten Allgemein und Variante zeigen vordefinierte Commerce-Eigenschaften, die aus dem Commerce-Backend stammen. Diese Daten (einschl. -Varianten) sind schreibgeschützte Daten in AEM, da das Aufzeichnungssystem das Commerce-Backend ist. Der Tab Variante wird nur für Produkte mit Varianten angezeigt und enthält eine Liste aller Varianten.

![Katalogeigenschaften](/help/commerce/cif/assets/catalog-properties.png)

### AEM Inhaltsregisterkarten {#content-tabs}

Diese Registerkarten, gruppiert nach AEM Inhaltstypen (Erlebnisfragmente, Inhaltsfragmente, zugehörige Assets), zeigen AEM Inhalt an, der mit dem Commerce-Objekt verknüpft ist. Mit der Aktion &quot;Details anzeigen&quot;wird eine neue Browser-Registerkarte mit dem ausgewählten Inhalt geöffnet.

![Inhaltseigenschaften](/help/commerce/cif/assets/content-properties.png)
