---
title: Wiedergabe und Bereitstellung
seo-title: Wiedergabe und Bereitstellung
description: 'null'
seo-description: 'null'
uuid: 1253b6a5-6bf3-42b1-be3a-efa23b6ddb51
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 672d5b1e-6b2f-4afe-ab04-c398e5ef45d5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Wiedergabe und Bereitstellung{#rendering-and-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM-Inhalte können problemlos über [Sling Default Servlets](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) gerendert werden, um [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) und andere Formate wiederzugeben.

Diese sofort einsetzbaren Renderer führen normalerweise das Repository aus und geben Inhalt wie bisher zurück.

AEM unterstützt über Sling auch die Entwicklung und Bereitstellung von benutzerdefinierten Sling-Renderern, um das gerenderte Schema und den gerenderten Inhalt vollständig zu steuern.

Content Services-Standard-Renderer füllen die Lücke zwischen den standardmäßigen Sling-Standardeinstellungen und der benutzerdefinierten Entwicklung, sodass viele Aspekte des gerenderten Inhalts ohne Entwicklung angepasst und gesteuert werden können.

Das folgende Diagramm zeigt die Wiedergabe von Inhaltsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## Anfordern von JSON {#requesting-json}

Verwenden Sie **&lt;RESOURCE.caas[.&lt;EXPORT-CONFIG][.&lt;EXPORT-CONFIG].json** zum Anfordern von JSON.

<table>
 <tbody>
  <tr>
   <td>RESSOURCE</td>
   <td>eine Entitätsressource unter /content/entity<br /> oder <br /> eine Inhaltsressource unter /content</td>
  </tr>
  <tr>
   <td>EXPORT-CONFIG</td>
   <td><p><strong>OPTIONAL</strong><br /> </p> <p>eine Exportkonfiguration gefunden unter /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> Wenn die standardmäßige Exportkonfiguration <br /> weggelassen wird, wird angewendet </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPTIONALE</strong><br /> <br /> Tiefenrekursion für das Rendering von Kindern, wie beim Sling-Rendering verwendet</td>
  </tr>
 </tbody>
</table>

## Erstellen von Exportkonfigurationen {#creating-export-configs}

Exportkonfigurationen können erstellt werden, um das JSON-Rendering anzupassen.

Sie können einen Konfigurationsknoten unter */apps/mobileapps/caas/exportConfigs erstellen.*

| Knotenname | Name der Konfiguration (für die Renderauswahl) |
|---|---|
| jcr:primaryType | nt:unstructured |

Die folgende Tabelle zeigt die Eigenschaften von Exportkonfigurationen:

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Standard (falls nicht festgelegt)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>sling:resourceType</td>
   <td>Ausschließen von Details für Knoten mit angegebenem sling:resourceType vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>sling:resourceType</td>
   <td>umfassen nur Details für Knoten mit angegebenem sling:resourceType vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>Präfixe für Eigenschaften</td>
   <td>Ausschließen von Eigenschaften, die mit bestimmten Präfixen beginnen, aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>nichts ausschließen</td>
   <td>Eigenschaftsnamen</td>
   <td>Ausschließen spezifizierter Eigenschaften aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>Eigenschaftsnamen</td>
   <td><p>Wenn excludePropertyPrefixes festgelegt<br /> sind, enthält dies die angegebenen Eigenschaften, obwohl das Präfix ausgeschlossen wurde,</p> <p>else (Eigenschaften ausschließen ignoriert) schließen Sie nur diese Eigenschaften ein</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>Zeichenfolge[]</td>
   <td>alles einschließen</td>
   <td>untergeordnete Namen</td>
   <td>Ausschließen spezifizierter untergeordneter Elemente aus dem JSON-Export</td>
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
   <td>&lt;IST_property_name&gt;,&lt;ERROPTEINSTELLUNGSINSTANZ&gt;</td>
   <td>Eigenschaften mit Ersetzungen umbenennen</td>
  </tr>
 </tbody>
</table>

### Außerkraftsetzungen beim Exportieren von Ressourcentypen {#resource-type-export-overrides}

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
   <td><strong>Standard (falls nicht festgelegt)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>&lt;SELECTOR_TO_INC&gt;</td>
   <td>Zeichenfolge[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Bei den folgenden Sling-Ressourcentypen sollten Sie den standardmäßigen CaaS-JSON-Export nicht zurückgeben.<br /><br /> Geben Sie einen Kunden-JSON-Export zurück, indem Sie die Ressource als &lt;RESOURCE&gt;.&lt;SELECTOR_TO_INC&gt;.json </td>
  </tr>
 </tbody>
</table>

### Vorhandene Content Services-Exportkonfigurationen {#existing-content-services-export-configs}

Content Services umfasst zwei Exportkonfigurationen:

* default (keine Konfiguration angegeben)
* page (zum Rendern von Site-Seiten)

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
   <td>Sling JSON Overrides</td>
   <td>foundation/components/image<br /> wcm/foundation/components/image<br /> mobileapps/caas/components/data/contentReferenz<br /> zu mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Seitenexport-Konfiguration {#page-export-configuration}

Diese Konfiguration erweitert den Standard um die Einbeziehung von untergeordneten Elementen unter einem untergeordneten Knoten.

&lt;SITE_PAGE>.caas.page[.&lt;DEPTH-INT>].json

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen in Content Services finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Entwicklung von Modellen](/help/mobile/models-in-repository.md)
* [Authoring von Content Services](/help/mobile/develop-content-as-a-service.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)

