---
title: Rendering und Versand
description: Erfahren Sie, wie Sie Adobe Experience Manager-Inhalte mithilfe von Sling Default Servlets rendern, um JSON und andere Formate zu rendern.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: f0c543ae-33ed-40bb-9eb7-0dc3bdea69e0
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 11%

---

# Rendering und Versand{#rendering-and-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Adobe Experience Manager-Inhalte (AEM) können einfach über [Sling-Standardservlets](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) gerendert werden, um [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) und andere Formate zu rendern.

Diese vordefinierten Renderings führen normalerweise das Repository aus und geben Inhalt unverändert zurück.

AEM unterstützt über Sling auch die Entwicklung und Bereitstellung benutzerdefinierter Sling-Renderer, um die volle Kontrolle über das gerenderte Schema und den gerenderten Inhalt zu übernehmen.

Content Services Default Renderer füllen die Lücke zwischen vordefinierten Sling Defaults und benutzerdefinierter Entwicklung, um die Anpassung und Kontrolle vieler Aspekte des gerenderten Inhalts ohne Entwicklung zu ermöglichen.

Das folgende Diagramm zeigt die Darstellung von Inhaltsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## Anfordern von JSON {#requesting-json}

Verwenden Sie **&lt;RESOURCE.caas[.&lt;EXPORT-CONFIG][.&lt;EXPORT-CONFIG].json** , um JSON anzufordern.

<table>
 <tbody>
  <tr>
   <td>RESSOURCE</td>
   <td>eine Entitätsressource unter /content/entitäten<br /> oder <br /> eine Inhaltsressource unter /content</td>
  </tr>
  <tr>
   <td>EXPORT-CONFIG</td>
   <td><p><strong>OPTIONAL</strong><br /> </p> <p>eine Exportkonfiguration, die unter /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> <br /> gefunden wird. Wenn die standardmäßige Exportkonfiguration weggelassen wird, wird sie angewendet </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPTIONAL</strong><br /> <br /> Tiefenrekursion für die Wiedergabe von untergeordneten Elementen, wie sie beim Sling-Rendering verwendet wird</td>
  </tr>
 </tbody>
</table>

## Erstellen von Exportkonfigurationen {#creating-export-configs}

Exportkonfigurationen können erstellt werden, um das JSON-Rendering anzupassen.

Sie können einen Konfigurationsknoten unter */apps/mobileapps/caas/exportConfigs* erstellen.

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
   <td><p>Wenn excludePropertyPrefixes set<br /> festgelegt ist, enthält dies angegebene Eigenschaften, obwohl das Präfix nicht mit dem Präfix übereinstimmt.</p> <p>else (Eigenschaften ausschließen ignoriert) schließen nur diese Eigenschaften ein</p> </td>
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
   <td>String[]<br /> <br /> </td>
   <td>nichts ausschließen</td>
   <td>untergeordnete Namen</td>
   <td>nur angegebene untergeordnete Elemente aus dem JSON-Export einschließen, andere ausschließen</td>
  </tr>
  <tr>
   <td>renameProperties</td>
   <td>String[]<br /> <br /> </td>
   <td>nichts umbenennen</td>
   <td>&lt;Isteigenschaftsname&gt;,&lt;Ersatzeigenschaftsname&gt;</td>
   <td>Umbenennen von Eigenschaften mithilfe von Ersetzungen</td>
  </tr>
 </tbody>
</table>

### Außerkraftsetzungen beim Export von Ressourcentypen {#resource-type-export-overrides}

Erstellen Sie einen Konfigurationsknoten unter */apps/mobileapps/caas/exportConfigs*.

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
   <td>&lt;SELECTOR_TO_INC&gt;</td>
   <td>Zeichenfolge[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Für die folgenden Sling-Ressourcentypen geben Sie nicht den standardmäßigen CAAS-JSON-Export zurück.<br /> Geben Sie einen Kunden-JSON-Export zurück, indem Sie die Ressource als;<br /> &lt;RESOURCE&gt; rendern.&lt;SELECTOR_TO_INC&gt;.json </td>
  </tr>
 </tbody>
</table>

### Vorhandene Content Services-Exportkonfigurationen {#existing-content-services-export-configs}

Content Services umfasst zwei Exportkonfigurationen:

* default (keine Konfiguration angegeben)
* Seite (zum Rendern von Site-Seiten)

#### Standardmäßige Exportkonfiguration {#default-export-configuration}

Die standardmäßige Exportkonfiguration für Content Services wird angewendet, wenn im angeforderten URI eine Konfiguration angegeben ist.

&lt;RESOURCE>.caas[.&lt;DEPTH-INT>].json

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

Diese Konfiguration erweitert die Standardeinstellung, um die Gruppierung von untergeordneten Elementen unter einem untergeordneten Knoten einzubeziehen.

&lt;SITE_PAGE>.caas.page[.&lt;DEPTH-INT>].json

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen in Content Services finden Sie in den folgenden Ressourcen:

* [Entwicklung von Modellen](/help/mobile/administer-mobile-apps.md)
* [Authoring - Content Services](/help/mobile/develop-content-as-a-service.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)
