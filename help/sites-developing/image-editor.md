---
title: Bild-Editor
seo-title: Bild-Editor
description: Der Bild-Editor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um die Bearbeitung von Bildern durch Inhaltsersteller zu erleichtern.
seo-description: Der Bild-Editor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um die Bearbeitung von Bildern durch Inhaltsersteller zu erleichtern.
uuid: de6ac71b-380a-4b67-b697-ac34a79a9cc4
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: f6347492-cf48-4835-b8fd-ce9a75a09abe
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Bild-Editor{#image-editor}

Der Bild-Editor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um die Bearbeitung von Bildern durch Inhaltsersteller zu erleichtern.

>[!CAUTION]
>
>Um die in diesem Artikel beschriebenen Funktionen des Bildeditors verwenden zu können, muss das [Feature Pack 24267](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) installiert sein.

## Relative Einheiten für Imagemap {#relative-units-for-image-map}

Der Bildeditor behält Imagemap-Bereiche sowohl als absolute als auch als relative Einheiten bei. Relative Einheiten sind nützlich, wenn sie als Datenattribute zur dynamischen Größenanpassung einer Imagemap (relativ zur Bildgröße) clientseitig in einer interaktiven Bildkomponente bereitgestellt werden.

### imageMap-Eigenschaft {#imagemap-property}

Die Imagemap-Koordinaten werden vom Bildeditor als `imageMap` Eigenschaft an der JCR-Datei beibehalten. Es hat das folgende Format.

Die Eigenschaft speichert Zuordnungsbereiche wie folgt:

`[area1][area2][...]`

Flächenformat:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Beispiel:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Unterstützung für SVG-Bilder {#support-for-svg-images}

Scalable Vector Graphics (SVG) werden vom Bildeditor unterstützt.

* Das Drag-and-Drop eines SVG-Assets aus DAM und das Hochladen eines SVG-Datei-Uploads aus einem lokalen Dateisystem werden beide unterstützt.

## Aktivieren von Plugins nach MIME-Typ {#enabling-plugins-by-mime-type}

In bestimmten Situationen müssen Authoring-Aktionen für bestimmte MIME-Typen eingeschränkt werden, da die serverseitige Verarbeitung nicht unterstützt wird. Das Bearbeiten von SVG-Bildern ist beispielsweise nicht zulässig.

Plugins im Bildeditor können selektiv vom MIME-Typ aktiviert werden, indem Sie eine `supportedMimeTypes` Eigenschaft auf dem Konfigurationsknoten des jeweiligen Plugins festlegen.

### Beispiel {#example}

Nehmen wir beispielsweise an, die Möglichkeit zum Beschneiden sollte nur für GIF-, JPEG-, PNG-, WEBP- und TIFF-Bilder erlaubt sein.

Die `supportedMimeTypes` Eigenschaft muss dann als Zeichenfolge der zulässigen MIME-Typen auf dem Konfigurationsknoten des Plugins auf dem `cq:editConfig` Knoten der Bildkomponente festgelegt werden.

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

