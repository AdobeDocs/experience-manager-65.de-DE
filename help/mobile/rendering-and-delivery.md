---
title: Rendering und Versand
seo-title: Rendering und Versand
description: Rendering und Versand
seo-description: 'null'
uuid: 1253b6a5-6bf3-42b1-be3a-efa23b6ddb51
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 672d5b1e-6b2f-4afe-ab04-c398e5ef45d5
exl-id: f0c543ae-33ed-40bb-9eb7-0dc3bdea69e0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 11%

---

# Rendering and Delivery{#rendering-and-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM Inhalt kann einfach über [Sling Default Servlets](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) gerendert werden, um [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) und andere Formate zu rendern.

Diese vordefinierten Renderer führen normalerweise das Repository durch und geben Inhalt unverändert zurück.

AEM unterstützt über Sling auch die Entwicklung und Bereitstellung benutzerdefinierter Sling-Renderer, um die volle Kontrolle über das gerenderte Schema und den gerenderten Inhalt zu übernehmen.

Content Services Default Renderer füllen die Lücke zwischen vordefinierten Sling Defaults und benutzerdefinierter Entwicklung, um die Anpassung und Kontrolle vieler Aspekte des gerenderten Inhalts ohne Entwicklung zu ermöglichen.

Das folgende Diagramm zeigt die Darstellung von Inhaltsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## Anfordern von JSON {#requesting-json}

Verwenden Sie **&lt;RESOURCE.caas[.&lt;export-config>.][&lt;export-config>.** jsonto JSON anfordern.]

<table>
 <tbody>
  <tr>
   <td>RESSOURCE</td>
   <td>eine Entitätsressource unter /content/entils<br /> oder <br /> einer Inhaltsressource unter /content</td>
  </tr>
  <tr>
   <td>EXPORT-CONFIG</td>
   <td><p><strong>OPTIONAL</strong><br /> </p> <p>eine Exportkonfiguration, die unter /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> <br /> gefunden wird. Wenn diese Option weggelassen wird, wird die standardmäßige Exportkonfiguration angewendet </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong></strong><br /> <br /> OPTIONALdepth-Rekursion für das Rendering von untergeordneten Elementen, wie beim Sling-Rendering verwendet</td>
  </tr>
 </tbody>
</table>

## Erstellen von Exportkonfigurationen {#creating-export-configs}

Exportkonfigurationen können erstellt werden, um das JSON-Rendering anzupassen.

Sie können einen Konfigurationsknoten unter */apps/mobileapps/caas/exportConfigs.* erstellen.

| Knotenname | Name der Konfiguration (für Rendering-Selektor) |
|---|---|
| jcr:primaryType | nt:unstructured |

Die folgende Tabelle zeigt die Eigenschaften von Exportkonfigurationen:

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Standard (if, not set)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>sling:resourceType</td>
   <td>Ausschließen von Details für Knoten mit dem angegebenen sling:resourceType vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>sling:resourceType</td>
   <td>Include-Details nur für Knoten mit dem angegebenen sling:resourceType vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>Eigenschaftspräfixe</td>
   <td>Ausschließen von Eigenschaften, die mit angegebenen Präfixen beginnen, aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>Eigenschaftsnamen</td>
   <td>Ausschluss spezifizierter Eigenschaften aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>Eigenschaftsnamen</td>
   <td><p>Wenn excludePropertyPrefixes set<br /> dies angegebene Eigenschaften enthält, obwohl das Präfix mit dem Präfix ausgeschlossen wird,</p> <p>else (Eigenschaften ausschließen ignoriert) schließen nur diese Eigenschaften ein</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>untergeordnete Namen</td>
   <td>Ausschluss bestimmter untergeordneter Elemente aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td>Zeichenfolge[]<br /> <br /> </td>
   <td>nichts ausschließen</td>
   <td>untergeordnete Namen</td>
   <td>nur angegebene untergeordnete Elemente aus dem JSON-Export einschließen, andere ausschließen</td>
  </tr>
  <tr>
   <td>renameProperties</td>
   <td>Zeichenfolge[]<br /> <br /> </td>
   <td>nichts umbenennen</td>
   <td>&lt;actual_property_name&gt;,&lt;replacement_property_name&gt;</td>
   <td>Umbenennen von Eigenschaften mithilfe von Ersetzungen</td>
  </tr>
 </tbody>
</table>

### Export von Ressourcentypen überschreibt {#resource-type-export-overrides}

Erstellen Sie einen Konfigurationsknoten unter */apps/mobileapps/caas/exportConfigs.*

| name | resourceTypeOverrides |
|---|---|
| jcr:primaryType | nt:unstructured |

Die folgende Tabelle zeigt die Eigenschaften:

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Standard (if, not set)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>&lt;selector_to_inc&gt;</td>
   <td>Zeichenfolge[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Für die folgenden Sling-Ressourcentypen sollten Sie nicht den standardmäßigen CaaS-JSON-Export zurückgeben.<br /> Geben Sie einen Customer JSON-Export zurück, indem Sie die Ressource als <br /> &lt;resource&gt; rendern.&lt;selector_to_inc&gt;.json </td>
  </tr>
 </tbody>
</table>

### Vorhandene Content Services-Exportkonfigurationen {#existing-content-services-export-configs}

Content Services umfasst zwei Exportkonfigurationen:

* default (keine Konfiguration angegeben)
* Seite (zum Rendern von Site-Seiten)

#### Standard-Exportkonfiguration {#default-export-configuration}

Die standardmäßige Exportkonfiguration für Content Services wird angewendet, wenn im angeforderten URI eine Konfiguration angegeben ist.

&lt;resource>.caas[.&lt;depth-int>].json

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Wert</strong></td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>jcr:,sling:,cq:,oak:,pge-</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>jcr:text,text<br /> jcr:title,title<br /> jcr:description,description<br /> jcr:lastModified,lastModified<br /> cq:tags,tags<br /> cq:lastModified,lastModified</td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>Sling JSON-Überschreibungen</td>
   <td>foundation/components/image<br /> wcm/foundation/components/image<br /> mobileapps/caas/components/data/contentReference<br /> mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Seitenexportkonfiguration {#page-export-configuration}

Diese Konfiguration erweitert die Standardeinstellung, um die Gruppierung von untergeordneten Elementen unter einem untergeordneten Knoten einzuschließen.

&lt;site_page>.caas.page[.&lt;depth-int>].json

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen in Content Services finden Sie in den folgenden Ressourcen:

* [Entwicklung von Modellen](/help/mobile/administer-mobile-apps.md)
* [Authoring - Content Services](/help/mobile/develop-content-as-a-service.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)
