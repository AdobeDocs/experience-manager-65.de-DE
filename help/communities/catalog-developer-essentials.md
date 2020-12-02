---
title: Kataloggrundlagen
seo-title: Kataloggrundlagen
description: Katalogübersicht
seo-description: Katalogübersicht
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
translation-type: tm+mt
source-git-commit: 41de9fff615b5b2f77d835740dfb1d33aa81e59b
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 4%

---


# Kataloggrundlagen {#catalog-essentials}

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Katalogfunktion von Community-Sites, die die Aktivierung ermöglichen.

Mit der Katalogfunktion können Community-Mitglieder, wenn sie in einer Community-Site enthalten sind, die in einem Katalog aufgelisteten Ressourcen zur Aktivierung durchsuchen und auswählen.

Die [ `enablement catalog`-Komponente](catalog.md) ermöglicht es Community-Mitgliedern, auf einen Katalog von [Aktivierungsressourcen](resources.md) zuzugreifen. Die Verwendung von AEM-Tags ist ein wichtiger Bestandteil der Verwaltung des Erscheinungsbilds der Aktivierungsressourcen in einem Katalog.

Siehe [Tagging-Aktivierungsressourcen](tag-resources.md).

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/enable/components/hbs/catalog</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.enable.hbs.breadcrumbs<br /> cq.social.enable.hbs.catalog<br /> cq.social.enable.hbs.resource<br /> cq.social.enable.hbs.learn.path</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/enablement/components/hbs/catalog/catalog.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/enablement/components/hbs/catalog/clientlibs/catalog.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="catalog.md">Katalogfunktion</a></td>
  </tr>
 </tbody>
</table>

## Grundlagen für serverseitige {#essentials-for-server-side}

### Katalogfunktion {#catalog-function}

Eine Community-Site-Struktur, die die Katalogfunktion [enthält, enthält eine konfigurierte `enablement catalog`-Komponente.](functions.md#catalog-function)

### Pre-Filters {#pre-filters}

Wenn einer Community-Site eine Katalogfunktion hinzugefügt wurde, können die Aktivierungsressourcen und Lernpfade, die im Katalog angezeigt werden, durch Angabe eines Vorfilters eingeschränkt werden. Dies geschieht durch Festlegen von Eigenschaften für die Instanz der Katalogressource für die Site.

Verwenden Sie das Beispiel des [Aktivierungslehrgangs](getting-started-enablement.md):

* Autor
* Verwenden von [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md)

   * Beispiel: [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* Navigieren Sie zur Katalogressource auf der Katalogseite

   * Beispiel: `/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`

* hinzufügen eines untergeordneten Filter-Knotens

   * Wählen Sie den Knoten `catalog`aus
   * Wählen Sie **[!UICONTROL Knoten erstellen]**

      * Name: `filters`
      * Typ: `nt:unstructured`
      * Wählen Sie **[!UICONTROL Alle speichern]**

* hinzufügen `se_resource-tags`-Eigenschaft auf den Knoten `filters`

   * Wählen Sie den Knoten `filters`
   * hinzufügen einer Multi-Eigenschaft

      * Name: `se_resource-tags`
      * Typ: String
      * Wert: *&lt;enter a [TagID](#pre-filter-tagids)*
         * Wählen Sie **[!UICONTROL Multi]**
         * Wählen Sie **[!UICONTROL Hinzufügen]**

            * Wählen Sie im Popup-Dialogfeld `+` aus, um weitere TagIDs vor dem Filter hinzuzufügen.

* Veröffentlichen Sie die Community-Site erneut.

![configure-catalog](assets/configure-catalog.png)

#### TagIDs vor dem Filtern {#pre-filter-tagids}

Der Vorfilter [TagIDs](../../help/sites-developing/framework.md#tagid) muss exakt mit den Tags übereinstimmen, die auf die Aktivierungsressourcen angewendet wurden. Diese sind im Ordner `resources` für die Site als Werte der Eigenschaft `se_resource-tags` sichtbar.

![configure-Filters](assets/configure-catalog1.png)

### Referenz-APIs {#reference-apis}

* [Aktivierungs-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/api/package-summary.html)

* [Berichte-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/reporting/api/package-summary.html)

* [Berichte Analytics-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/reporting/analytics/api/package-summary.html)

