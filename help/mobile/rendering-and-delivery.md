---
title: Rendering und Versand
description: Erfahren Sie, wie Sie Adobe Experience Manager-Inhalte mithilfe von Sling-Standard-Servlets rendern können, um JSON und andere Formate zu rendern.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: f0c543ae-33ed-40bb-9eb7-0dc3bdea69e0
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 6%

---

# Rendering und Versand{#rendering-and-delivery}

{{ue-over-mobile}}

Adobe Experience Manager (AEM)-Inhalte können einfach über „Sling [&quot;-Standard-Servlets gerendert werden](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) um [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) und andere Formate zu rendern.

Diese vordefinierten Renderings führen normalerweise das Repository durch und geben die Inhalte unverändert zurück.

AEM unterstützt mithilfe von Sling auch die Entwicklung und Bereitstellung benutzerdefinierter Sling-Renderer, um die volle Kontrolle über das gerenderte Schema und die gerenderten Inhalte zu übernehmen.

Content Services Default Renderer füllen die Lücke zwischen standardmäßigen Sling-Standardwerten und benutzerdefinierter Entwicklung und ermöglichen die Anpassung und Kontrolle vieler Aspekte des gerenderten Inhalts ohne Entwicklung.

Das folgende Diagramm zeigt das Rendering von Content Services.

![chlimage_1-15](assets/chlimage_1-15.png)

## JSON wird angefordert {#requesting-json}

Verwenden Sie **&lt;RESOURCE.caas`[.<EXPORT-CONFIG][.&lt;DEPTH-INT&gt;]`.json** um JSON anzufordern.

<table>
 <tbody>
  <tr>
   <td>RESSOURCE</td>
   <td>Eine Entitätsressource unter /content/entities<br /> oder eine Inhaltsressource unter /content <br /></td>
  </tr>
  <tr>
   <td>EXPORT-CONFIG</td>
   <td><p><strong>OPTIONAL</strong><br /> </p> <p>eine Exportkonfiguration unter /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> <br /> Wenn nicht angegeben, wird die standardmäßige Exportkonfiguration angewendet </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPTIONAL</strong><br /> <br /> Tiefenrekursion für das Rendering von untergeordneten Elementen, wie es beim Sling-Rendering verwendet wird</td>
  </tr>
 </tbody>
</table>

## Erstellen von Exportkonfigurationen {#creating-export-configs}

Exportkonfigurationen können erstellt werden, um das JSON-Rendering anzupassen.

Sie können unter */apps/mobileapps/caas/exportConfigs einen Konfigurationsknoten erstellen.*

| Knotenname | Name der Konfiguration (für den Rendering-Selektor) |
|---|---|
| jcr:primaryType | nt:unstructured |

In der folgenden Tabelle sind die Eigenschaften der Exportkonfigurationen aufgeführt:

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Standard (wenn nicht festgelegt)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>Alles einschließen</td>
   <td>sling:resourceType</td>
   <td>Ausschließen von Details für Knoten mit dem angegebenen sling:resourceType aus dem JSON-Export</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>Zeichenfolge[]</td>
   <td>Nichts ausschließen</td>
   <td>sling:resourceType</td>
   <td>Schließen Sie Details nur für Knoten mit dem angegebenen sling:resourceType aus dem JSON-Export ein</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>Zeichenfolge[]</td>
   <td>Nichts ausschließen</td>
   <td>Eigenschaftspräfixe</td>
   <td>Ausschließen von Eigenschaften, die mit angegebenen Präfixen beginnen, vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>Nichts ausschließen</td>
   <td>Eigenschaftsnamen</td>
   <td>Ausschließen der angegebenen Eigenschaften vom JSON-Export</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>Zeichenfolge[]</td>
   <td>Alles einschließen</td>
   <td>Eigenschaftsnamen</td>
   <td><p>Wenn excludePropertyPrefixes festgelegt ist<br /> werden angegebene Eigenschaften einbezogen, obwohl das Präfix ausgeschlossen ist,</p> <p>Sonst (Eigenschaften ausschließen ignoriert): Schließt nur diese Eigenschaften ein</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>Zeichenfolge[]</td>
   <td>Alles einschließen</td>
   <td>Untergeordnete Namen</td>
   <td>Ausschließen angegebener untergeordneter Elemente vom JSON-Export</td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td>String[]<br /> <br /> </td>
   <td>Nichts ausschließen</td>
   <td>Untergeordnete Namen</td>
   <td>Nur angegebene untergeordnete Elemente vom JSON-Export einbeziehen, andere ausschließen</td>
  </tr>
  <tr>
   <td>Eigenschaften umbenennen</td>
   <td>String[]<br /> <br /> </td>
   <td>Nichts umbenennen</td>
   <td>&lt;ACTUAL_PROPERTY_NAME&gt;,&lt;REPLACEMENT_PROPERTY_NAME&gt;</td>
   <td>Umbenennen von Eigenschaften mithilfe von Ersetzungen</td>
  </tr>
 </tbody>
</table>

### Überschreibungen des Ressourcentypexports {#resource-type-export-overrides}

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
   <td><strong>Standard (wenn nicht festgelegt)</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>&lt;SELECTOR_TO_INC&gt;</td>
   <td>Zeichenfolge[] </td>
   <td>–</td>
   <td>sling:resourceType</td>
   <td>Für die folgenden Sling-Ressourcentypen geben Sie nicht den standardmäßigen Cas-JSON-Export zurück.<br /> Geben Sie einen Kunden-JSON-Export zurück, indem Sie die Ressource als <br /> &lt;RESOURCE&gt; rendern.&lt;SELECTOR_TO_INC&gt;.json </td>
  </tr>
 </tbody>
</table>

### Vorhandene Content Services-Exportkonfigurationen {#existing-content-services-export-configs}

Content Services umfassen zwei Exportkonfigurationen:

* Standard (keine Konfiguration festgelegt)
* Seite (zum Rendern von Seiten der Site)

#### Standardexportkonfiguration {#default-export-configuration}

Die standardmäßige Content Services-Exportkonfiguration wird angewendet, wenn im angeforderten URI eine Konfiguration angegeben ist.

&lt;RESOURCE>.[.&lt;DEPTH-INT>].json

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
   <td>jcr:,sling:,cq:,oak:,page-</td>
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
   <td>Foundation/components/image<br /> wcm/foundation/components/image<br /> mobileapps/caas/components/data/contentReference<br /> mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Konfiguration des Seitenexports {#page-export-configuration}

Mit dieser Konfiguration wird der Standard erweitert, sodass untergeordnete Elemente unter einem untergeordneten Knoten gruppiert werden.

&lt;SITE_PAGE>.caas.page[.&lt;DEPTH-INT>].json

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen in Content Services finden Sie in den folgenden Ressourcen:

* [Entwickeln von Modellen](/help/mobile/administer-mobile-apps.md)
* [Authoring von Content Services](/help/mobile/develop-content-as-a-service.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)
