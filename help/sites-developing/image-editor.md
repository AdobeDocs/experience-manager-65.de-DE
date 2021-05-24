---
title: Bildeditor
seo-title: Bildeditor
description: Der Bildeditor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um eine Bearbeitung von Bildern durch Inhaltsautoren zu erlauben.
seo-description: Der Bildeditor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um eine Bearbeitung von Bildern durch Inhaltsautoren zu erlauben.
uuid: de6ac71b-380a-4b67-b697-ac34a79a9cc4
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: f6347492-cf48-4835-b8fd-ce9a75a09abe
exl-id: af6cf1e0-8901-4621-9f72-e791cb8d68ae
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 94%

---

# Bildeditor{#image-editor}

Der Bildeditor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um eine Bearbeitung von Bildern durch Inhaltsautoren zu erlauben.

>[!CAUTION]
>
>Um die in diesem Artikel beschriebenen Funktionen des Bildeditors verwenden zu können, muss [Feature Pack 24267](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) installiert sein.

## Relative Einheiten für Imagemap {#relative-units-for-image-map}

Der Bildeditor persistiert Imagemap-Bereiche sowohl als absolute als auch als relative Einheiten. Relative Einheiten sind nützlich, wenn sie in einer interaktiven Bildkomponente Client-seitig als Datenattribute zur dynamischen Größenanpassung einer Imagemap (relativ zur Bildgröße) bereitgestellt werden.

### imageMap-Eigenschaft {#imagemap-property}

Die Imagemap-Koordinaten werden vom Bildeditor als `imageMap`-Eigenschaft im JCR persistiert. Die Eigenschaft weist das folgende Format auf.

Sie speichert Zuordnungsbereiche wie folgt:

`[area1][area2][...]`

Bereichsformat:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Beispiel:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Unterstützung für SVG-Bilder {#support-for-svg-images}

Skalierbare Vektorgrafiken (SVG) werden vom Bildeditor unterstützt.

* Das Drag-and-Drop eines SVG-Assets aus DAM und das Hochladen eines SVG-Datei-Uploads aus einem lokalen Dateisystem werden beide unterstützt.

## Aktivieren von Plug-ins nach MIME-Typ {#enabling-plugins-by-mime-type}

In bestimmten Fällen müssen Erstellungsaktionen für bestimmte MIME-Typen eingeschränkt werden, da die Server-seitige Verarbeitung nicht unterstützt wird. Das Bearbeiten von SVG-Bildern ist beispielsweise nicht zulässig.

Plug-ins im Bildeditor können selektiv nach MIME-Typ aktiviert werden, indem Sie im Konfigurationsknoten des jeweiligen Plug-ins eine `supportedMimeTypes`-Eigenschaft festlegen.

### Beispiel {#example}

Nehmen wir beispielsweise an, die Möglichkeit zum Zuschneiden sollte nur bei GIF-, JPEG-, PNG-, WEBP- und TIFF-Bildern erlaubt sein.

Die `supportedMimeTypes`-Eigenschaft muss dann als Zeichenfolge der zulässigen MIME-Typen im Konfigurationsknoten des Plug-ins im `cq:editConfig`-Knoten der Bildkomponente festgelegt werden.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
