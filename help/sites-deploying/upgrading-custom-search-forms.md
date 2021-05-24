---
title: Aktualisieren von benutzerdefinierten Suchformularen
seo-title: Aktualisieren von benutzerdefinierten Suchformularen
description: In diesem Artikel werden die Anpassungen erläutert, die nach einer Aktualisierung erfolgen müssen, damit benutzerdefinierte Suchformulare ordnungsgemäß funktionieren.
seo-description: In diesem Artikel werden die Anpassungen erläutert, die nach einer Aktualisierung erfolgen müssen, damit benutzerdefinierte Suchformulare ordnungsgemäß funktionieren.
uuid: 35b8fbb9-5951-4e1c-bf04-4471a55b9cb0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: a08cee9c-e981-4483-8bdc-e6353977f854
feature: Aktualisieren
exl-id: 797bbdf9-917a-4537-a5f9-bf2682db968b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 62%

---

# Aktualisieren von benutzerdefinierten Suchformularen{#upgrading-custom-search-forms}

Der in AEM 6.2 verwendete Speicherort von benutzerdefinierten Suchformularen im Repository wurde geändert. Nach der Aktualisierung werden diese von ihrem Speicherort in 6.1 unter:

* /apps/cq/gui/content/facets

an diesen neuen Speicherort verschoben:

* /conf/global/settings/cq/search/facets

Daher müssen nach einer Aktualisierung manuelle Anpassungen vorgenommen werden, damit die Formulare weiterhin funktionieren.

Dies gilt für neue Suchformulare und Standardformulare, die benutzerdefiniert wurden.

Weitere Informationen finden Sie in der Dokumentation zu [Suchfacetten](/help/assets/search-facets.md).

## Ändern der Eigenschaft „resourceType“{#changing-the-resourcetype-property}

Sofern nicht anders angegeben, muss für die meisten Anpassungen nach einer Aktualisierung die Eigenschaft `sling:resourceType` für die konfigurierten benutzerdefinierten Suchformulare geändert werden. Dieser Schritt ist notwendig, damit die Eigenschaft auf den richtigen Speicherort des Rendering-Skripts verweist.

Sie können die Eigenschaft ändern, indem Sie folgende Schritte ausführen:

1. Öffnen Sie die CRXDE Lite, indem Sie zu `https://server:port/crx/de/index.jsp` navigieren.
1. Navigieren Sie zum Speicherort des Knotens, der angepasst werden muss, wie in der Liste mit [benutzerdefinierten Suchformularen](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) unten angegeben.
1. Klicken Sie auf den Knoten. Klicken Sie im rechten Eigenschaftenfenster auf die Eigenschaft **sling:resourceType** und ändern Sie diese.
1. Speichern Sie dann die Änderungen und klicken Sie auf die Schaltfläche **Alle speichern**.

## Liste der benutzerdefinierten Suchformulare  {#list-of-custom-search-forms}

Nachstehend finden Sie eine Liste aller benutzerdefinierten Suchformulare und der Änderungen, die nach der Aktualisierung erforderlich sind. Sie beziehen sich auf die Namen in `/conf/global/settings/cq/search/facets/sites/items`.

### Volltexteigenschaft mit Knotenname &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1</td>
   <td>fulltext</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

In AEM 6.1 war die standardmäßige Volltexteigenschaft Teil des Suchformulars. In Version 6.2 wurde das Volltext-Feld durch OmniSearch ersetzt. Diese Eigenschaft wird programmgesteuert übersprungen und kann entfernt werden.

**Aktion:** Entfernen Sie den Knoten vollständig.

### Andere Volltexteigenschaften {#other-fulltext-predicates}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Pfadbrowser-Eigenschaften {#path-browser-predicates}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>path</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/pathpredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/pathpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Tags-Eigenschaften {#tags-predicates}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>tags</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/tagspredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/tagspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft **resourceType** an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Seitenstatus-Eigenschaft {#page-status-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>pagestatuspredicate</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/pagestatuspredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

Der Seitenstatus wurde durch zwei Options-Eigenschaftsprädikate ersetzt, jeweils eins für den Veröffentlichungs- und eins für den LiveCopy-Status.

**Aktionen:**

* Entfernen Sie den Knoten `pagestatuspredicate` .
* Knoten kopieren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * in `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Knoten kopieren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * in `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Stellen Sie sicher, dass Sie die Eigenschaft `listOrder` für den Knoten `analyticspredicate` auf &quot;**8**&quot;festlegen. Dies ist erforderlich, um Konflikte zu vermeiden.

### Datumsbereich-Eigenschaften  {#date-range-predicates}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>daterangepredicate</td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.1</td>
   <td>cq/gui/components/common/admin/customsearch/searchpredicates/daterangepredicate</td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/daterangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Ausgeblendeter Filter {#hidden-filter}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>type</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>granite/ui/components/foundation/form/hidden</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>granite/ui/components/foundation/form/hidden</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Keine Anpassungen erforderlich.

### Analytics-Eigenschaft {#analytics-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>analyticspredicate</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Eigenschaft für Bereich {#range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

>[!NOTE]
>
>Hinweis: Anders als in 6.1 wird mit der Eigenschaft „Bereich“ kein Tag mehr in der Suchleiste angezeigt.

### Options-Eigenschaftsprädikat  {#options-property-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Reglerbereichseigenschaft {#slider-range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Komponenteneigenschaft {#components-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Verfassereigenschaft {#author-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Vorlageneigenschaft {#templates-predicate}

<table>
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /><br /> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td>
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td>
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

## Asset-Admin-Suchschiene {#assets-admin-search-rail}

Die folgenden Knoten beziehen sich auf die Namen in `/conf/global/settings/dam/search/facets/assets/items`

### Volltexteigenschaft mit Knotenname &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext-1}

| Knoten im Standard-Suchformular in 6.1 | fulltext |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/fulltextpredicate |
| Ressourcentyp in 6.2 | Nicht zutreffend |

In 6.1 war die standardmäßige Volltexteigenschaft Teil des Suchformulars. In Version 6.2 wurde das Volltext-Feld durch OmniSearch ersetzt. Diese Eigenschaft wird programmgesteuert übersprungen und kann entfernt werden.

**Aktion:** Entfernen Sie den oben genannten Knoten.

### Pfadbrowser-Eigenschaften  {#path-browser-predicates-1}

| Knoten im Standard-Suchformular in 6.1 | pathbrowser |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/pathbrowserpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/pathbrowserpredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Eigenschaften des MIME-Typs {#mime-type-predicates}

| Knoten im Standard-Suchformular in 6.1 | mimetype |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen 6.2-Position hinzu).

### Dateigrößen-Eigenschaften {#file-size-predicates}

| Knoten im Standard-Suchformular in 6.1 | Dateigröße |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/filesizepredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` wie beim oben für 6.2 angegebenen Pfad an.

### Eigenschaften für letzte Änderung des Assets {#asset-last-modified-predicates}

| Knoten im Standard-Suchformular in 6.1 | assetlastmodifiedpredicate |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |

Aktion: Passen Sie die Eigenschaft resourceType an (fügen Sie &quot;/coral&quot;wie in der oben angegebenen 6.2-Position hinzu).

### Veröffentlichungseigenschaft {#publish-predicate}

| Knoten im Standard-Suchformular in 6.1 | publish |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/publishpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/publishpredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie &quot;**/coral**&quot;wie in der oben angegebenen Position 6.2 hinzu).

* Fügen Sie eine `optionPaths` (vom Typ String)-Eigenschaft mit dem Wert hinzu: `/libs/dam/options/predicates/publish`

* Fügen Sie die Eigenschaft `singleSelect` mit dem booleschen Wert `true` hinzu.

### Statuseigenschaften {#status-predicates}

| Knoten im Standard-Suchformular in 6.1 | status |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).

### Eigenschaften für Gültigkeitsdauer {#expiry-status-predicates}

| Knoten im Standard-Suchformular in 6.1 | expirystatus |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/expiredassetpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/expiredassetpredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).

### Eigenschaften für Metadaten-Gültigkeit {#metadata-validity-predicates}

| Knoten im Standard-Suchformular in 6.1 | Metadatavalidität |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).

### Bewertungseigenschaften {#rating-predicates}

| Knoten im Standard-Suchformular in 6.1 | Bewertung |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/ratingpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).

### Ausrichtungseigenschaft {#orientation-predicate}

| Knoten im Standard-Suchformular in 6.1 | Ausrichtung |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Ressourcentyp in 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie &quot;**/coral**&quot;wie in der oben angegebenen Position 6.2 hinzu).

* Fügen Sie eine Eigenschaft `fieldLabel` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `emptyText` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `rootPath` mit dem gleichen Wert wie für die Eigenschaft `optionPaths` auf demselben Knoten hinzu.

### Stileigenschaft {#style-predicate}

| Knoten im Standard-Suchformular in 6.1 | Stil |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Ressourcentyp in 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie &quot;**/coral**&quot;wie in der oben angegebenen Position 6.2 hinzu).

* Fügen Sie eine Eigenschaft `fieldLabel` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `emptyText` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `rootPath` mit dem gleichen Wert wie für die Eigenschaft `optionPaths` auf demselben Knoten hinzu.

### Videoformat-Eigenschaften {#video-format-predicates}

| Knoten im Standard-Suchformular in 6.1 | videoFormat |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).

### Eigenschaft für Haupt-Asset {#mainasset-predicate}

| Knoten im Standard-Suchformular in 6.1 | mainasset |
|---|---|
| Ressourcentyp in 6.1 | granite/ui/components/foundation/form/hidden |
| Ressourcentyp in 6.2 | granite/ui/components/coral/foundation/form/hidden |

**Aktion:** Passen Sie die  `resourceType` Eigenschaft an (fügen Sie &quot;**/coral**&quot;wie an der oben angegebenen Position in 6.2 hinzu).
