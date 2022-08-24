---
title: Kataloggrundlagen
seo-title: Catalog Essentials
description: Katalogübersicht
seo-description: Catalog overview
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
exl-id: 4ca76b50-d56d-4f4d-be92-bf8929c5d754
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 6%

---

# Kataloggrundlagen {#catalog-essentials}

Auf dieser Seite finden Sie die wichtigsten Informationen zum Arbeiten mit der Katalogfunktion von Community-Seiten für die Aktivierung.

Mit der Katalogfunktion können Community-Mitglieder, die in einer Community-Site enthalten sind, die in einem Katalog aufgelisteten Aktivierungsressourcen durchsuchen und auswählen.

Die [ `enablement catalog` component](catalog.md) ermöglicht es Community-Mitgliedern, auf einen Katalog von [Aktivierungsressourcen](resources.md). Die Verwendung AEM Tags ist ein wichtiger Bestandteil der Verwaltung des Erscheinungsbilds von Aktivierungsressourcen in einem Katalog.

Siehe [Tagging von Aktivierungsressourcen](tag-resources.md).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/enable/components/hbs/catalog</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.catalog<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learning.path</td>
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

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

### Katalogfunktion {#catalog-function}

Eine Community-Site-Struktur mit [Katalogfunktion](functions.md#catalog-function)enthält eine konfigurierte `enablement catalog` -Komponente.

### Vorfilter {#pre-filters}

Wenn einer Community-Site eine Katalogfunktion hinzugefügt wurde, können Sie die Aktivierungsressourcen und Lernpfade, die im Katalog angezeigt werden, einschränken, indem Sie einen Vorfilter angeben. Dies geschieht durch Festlegen von Eigenschaften in der Instanz der Katalogressource für die Site.

Verwenden des Beispiels der [Tutorial zur Aktivierung](getting-started-enablement.md):

* Beim Autor
* Verwenden [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md)

   * z. B. [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* Navigieren Sie zur Katalogressource auf der Katalogseite.

   * Beispiel: `/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`

* Knoten für untergeordnete Filter hinzufügen

   * Wählen Sie die `catalog`Knoten
   * Auswählen **[!UICONTROL Knoten erstellen]**

      * Name: `filters`
      * Typ: `nt:unstructured`
      * Wählen Sie **[!UICONTROL Alle speichern]** aus

* Hinzufügen `se_resource-tags` -Eigenschaft auf `filters` Knoten

   * Wählen Sie die `filters` Knoten
   * Hinzufügen einer Eigenschaft &quot;Multi&quot;

      * Name: `se_resource-tags`
      * Typ: String
      * Wert: *&lt;enter a=&quot;&quot; span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />TagID](#pre-filter-tagids)>*[
         * Auswählen **[!UICONTROL Multi]**
         * Klicken Sie auf **[!UICONTROL Hinzufügen]**

            * Wählen Sie im Popup-Dialogfeld `+` um zusätzliche Tag-IDs vor dem Filter hinzuzufügen

* Veröffentlichen Sie die Community-Site erneut.

![configure-catalog](assets/configure-catalog.png)

#### Tag-IDs vor dem Filter {#pre-filter-tagids}

Der Vorfilter [TagIDs](../../help/sites-developing/framework.md#tagid) muss genau mit den Tags übereinstimmen, die auf die Aktivierungsressourcen angewendet werden. Diese sind im `resources` Ordner für die Site als Werte der Eigenschaft `se_resource-tags`.

![configure-filters](assets/configure-catalog1.png)

### Referenz-APIs {#reference-apis}

* [Aktivierungs-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [Reporting-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Reporting-Analytics-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/model/api/package-summary.html)
