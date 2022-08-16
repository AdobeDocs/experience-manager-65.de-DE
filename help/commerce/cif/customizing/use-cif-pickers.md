---
title: Verwenden der CIF-Produkt- und Kategorieauswahl
description: Erfahren Sie, wie Sie mit der CIF-Produkt- und Kategorieauswahl in Ihren Commerce-Komponenten Autoren und Marketing-Experten unterstützen können, effizient mit Commerce-Produkten und -Katalogdaten zu arbeiten.
sub-product: Commerce
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 1e7c3748-92b5-45f1-8dd9-f1816e3e34aa
source-git-commit: 2fadfa65242b208a750b0d5392fdd2c41e9ff20e
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---

# Adobe Experience Manager Content and Commerce Authoring-Auswahl {#cif-pickers}

Adobe Experience Manager Content and Commerce Authoring bietet eine Reihe von Authoring-Tools, mit denen AEM-Autoren und Marketing-Experten effizient mit Commerce-Produktdaten und -Katalogen arbeiten können. Die Produktauswahl und die Kategorieauswahl sind Teil des CIF-Add-ons und werden von den CIF-Kernkomponenten verwendet. Bei Projekten können diese Auswahlen in jedem Komponentendialogfeld verwendet werden, um Produkte oder Kategorien auszuwählen.

## Produktauswahl {#product-picker}

Um die Produktauswahl in einer Projektkomponente zu verwenden, müssen Entwickler `commerce/gui/components/common/cifproductfield` zu einem Komponentendialogfeld hinzufügen. Verwenden Sie beispielsweise Folgendes für cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

Das Produktfeld ermöglicht die Navigation zu dem Produkt, das Anwender über die verschiedenen Ansichten auswählen möchten. Standardmäßig gibt das Produktfeld die Kennung des Produkts zurück, kann jedoch mithilfe des Attributs `selectionId` konfiguriert werden.

Das Produktauswahlfeld unterstützt die folgenden optionalen Eigenschaften:

- „selectionId“ („id“, „uid“, „sku“, „slug“, „combinedSlug“, „combinedSku“) – ermöglicht die Auswahl des Produktattributs, das von der Auswahl zurückgegeben werden soll (Standard = „id“). Bei Verwendung von „sku“ wird die SKU des ausgewählten Produkts zurückgegeben, wenn „combinedSku“ verwendet wird. Zudem wird eine Zeichenfolge wie „base#variant“ mit den SKUs des Basisprodukts und der ausgewählten Variante oder eine einzelne SKU zurückgegeben, wenn ein Basisprodukt ausgewählt ist.
- „filter“ („folderOrProduct“, „folderOrProductOrVariant“) – filtert die Inhalte, die von der Auswahl während der Navigation in der Produktstruktur gerendert werden sollen. „folderOrProduct“ – rendert Ordner und Produkte. „folderOrProductOrVariant“ – rendert Ordner, Produkte und Produktvarianten. Wenn Produkte oder Produktvarianten gerendert werden, können sie auch in der Auswahl ausgewählt werden. (Standard = „folderOrProduct“)
- „multiple“ („true“, „false“) – zum Aktivieren der Auswahl eines oder mehrerer Produkte (Standard = „false“).
- „emptyText“ – zum Konfigurieren des leeren Textwerts des Auswahlfelds.

Darüber hinaus werden auch standardmäßige Dialogfeldfeldeigenschaften wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

>[!CAUTION]
>
>Für die Komponente `cifproductfield` ist die Client-Bibliothek `cif.shell.picker` erforderlich. Um einem Dialogfeld eine Client-Bibliothek hinzuzufügen, können Sie die Eigenschaft „extraClientlibs“ verwenden.
>[!CAUTION]
>
>Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Es wird dringend empfohlen, `sku` oder `slug` als Produktkennung zu verwenden. `id` wird weiterhin nur für Projekte unterstützt, die CIF-Kernkomponenten Version 1.x verwenden.

Ein umfassendes praktisches Beispiel für `cifproductfield` finden Sie im Projekt [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml). Siehe auch [Anpassen von Dialogen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=de#customizing-dialogs) in der Dokumentation zu AEM-Kernkomponenten.

## Kategorieauswahl {#category-picker}

Die Kategorieauswahl kann auch in einem Komponentendialogfeld auf ähnliche Weise wie die Produktauswahl verwendet werden.

Das folgende Snippet kann in einer cq:dialog-Konfiguration verwendet werden:

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Das Kategorieauswahlfeld unterstützt die folgenden optionalen Eigenschaften:

- selectionId(id, uid, slug, idAndUrlPath _(veraltet)_, uidAndUrlPath _(veraltet)_) – ermöglicht die Auswahl des Kategorieattributs, das von der Auswahl zurückgegeben werden soll (Standard = id).
- „multiple“ („true“, „false“) – zum Aktivieren der Auswahl einer oder mehrerer Kategorien (Standard = „false“).

Darüber hinaus werden auch standardmäßige Dialogfeldfeldeigenschaften wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

>[!CAUTION]
>
>Wie für die Komponente `cifproductfield` ist für die Komponente `cifcategoryfield` ebenfalls die Client-Bibliothek `cif.shell.picker` erforderlich. Um einem Dialogfeld eine Client-Bibliothek hinzuzufügen, können Sie die Eigenschaft `extraClientlibs` verwenden. Siehe [Anpassen von Dialogen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) in der Dokumentation zu AEM-Kernkomponenten.
>[!CAUTION]
>
>Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Es wird dringend empfohlen, `uid` oder `urlPath` als Kategoriekennung zu verwenden. `id` und `idAndUrlPath` werden weiterhin nur für Projekte unterstützt, die CIF-Kernkomponenten Version 1.x verwenden.

Ein umfassendes praktisches Beispiel für `cifcategoryfield` finden Sie im Projekt [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml).
