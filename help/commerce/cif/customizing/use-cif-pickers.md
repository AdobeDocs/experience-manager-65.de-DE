---
title: Verwendung der CIF-Produkt- und Kategorie-Auswahl
description: Erfahren Sie, wie Sie mit der CIF-Produkt- und Kategorie-Auswahl in Ihren Commerce-Komponenten Autoren und Marketingfachleute bei der effizienten Arbeit mit Commerce-Produkt- und Katalogdaten unterstützen.
sub-product: Commerce
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: Commerce Integration Framework
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---

# AEM Content &amp; Commerce Authoring Picker {#cif-pickers}

AEM Content &amp; Commerce Authoring bietet eine Reihe von Authoring-Werkzeugen, mit denen AEM Autoren und Marketingexperten effizient mit Commerce-Produktdaten und -Katalogen arbeiten können. Die Produktauswahl und die Kategorie-Auswahl sind Teil des CIF-Add-ons und werden von den CIF-Kernkomponenten verwendet. Projekte können diese Picker in jedem Komponentendialog verwenden, um Produkte oder Kategorien auszuwählen.

## Produktauswahl {#product-picker}

Um die Produktauswahl in einer Projektkomponente zu verwenden, muss ein Entwickler einem Komponentendialogfeld `commerce/gui/components/common/cifproductfield` hinzufügen. Verwenden Sie beispielsweise Folgendes für cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

Das Produktfeld ermöglicht die Navigation zu dem Produkt, das ein Benutzer über die verschiedenen Ansichten auswählen möchte. Standardmäßig gibt das Produktfeld die ID des Produkts zurück, kann jedoch mithilfe des Attributs `selectionId` konfiguriert werden.

Das Produktauswahl-Feld unterstützt die folgenden optionalen Eigenschaften:

- selectionId (id, uid, sku, slug, CombinedSlug, CombinedSku) - ermöglicht die Auswahl des Produktattributs, das vom Picker zurückgegeben werden soll (default = id). Bei Verwendung von sku wird der Sku des ausgewählten Produkts zurückgegeben, während Sie CombinedSku verwenden, und es wird eine Zeichenfolge wie base#variation mit dem Skus des Basisprodukts und der ausgewählten Variante oder eine einzelne Sku zurückgegeben, wenn ein Basisprodukt ausgewählt ist.
- filter (folderOrProduct, folderOrProductOrVariante) - Filter der Inhalte, die vom Picker während der Navigation in der Produktstruktur wiedergegeben werden sollen. folderOrProduct - rendert Ordner und Produkte. folderOrProductOrVariante - rendert Ordner, Produkt- und Produktvarianten. Wenn ein Produkt oder eine Produktvariante gerendert wird, kann sie auch in der Auswahl ausgewählt werden. (default = folderOrProduct)
- multiple (true, false) - Aktivieren Sie die Auswahl eines oder mehrerer Produkte (Standard = false)
- emptyText - zum Konfigurieren des leeren Textwerts des Auswahlfelds

Darüber hinaus werden auch standardmäßige Eigenschaften von Diaglog-Feldern wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

Die Komponente `cifproductfield` erfordert die clientlib-Datei &quot;cif.shell.picker&quot;. Um einem Dialogfeld eine clientlib hinzuzufügen, können Sie die Eigenschaft extraClientlibs verwenden.

Ein ausführliches Arbeitsbeispiel für `cifproductfield` finden Sie im Projekt [CIF Core Components](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml). Siehe auch [Anpassen von Dialogen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) in der Dokumentation zu AEM Kernkomponenten.

## Kategorie-Picker {#category-picker}

Der Kategorie-Picker kann auch in einem Komponentendialogfeld ähnlich wie die Produktauswahl verwendet werden.

Das folgende Snippet kann in einer cq:dialog-Konfiguration verwendet werden:

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Das Auswahlfeld für Kategorien unterstützt die folgenden optionalen Eigenschaften:

- selectionId(id, uid, slug, idAndUrlPath, uidAndUrlPath) - ermöglicht die Auswahl des Kategorie-Attributs, das vom Picker zurückgegeben werden soll (Standard = id). idAndUrlPath &amp; uidAndUrlPath sind spezielle Optionen, mit denen die Kategorien id/uid und url_path durch einen | Zeichen wie z.B. 1|Herren/Top.
- multiple (true, false) - Aktivieren der Auswahl einer oder mehrerer Kategorien (Standard = false)

Darüber hinaus werden auch standardmäßige Eigenschaften von Diaglog-Feldern wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

Wie bei der Komponente `cifproductfield` erfordert die Komponente `cifcategoryfield` auch die clientlib-Datei &quot;cif.shell.picker&quot;. Um einem Dialogfeld eine clientlib hinzuzufügen, können Sie die Eigenschaft `extraClientlibs` verwenden. Siehe [Anpassen von Dialogen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) in der Dokumentation zu AEM Kernkomponenten.

Ein ausführliches Arbeitsbeispiel für `cifcategoryfield` finden Sie im Projekt [CIF Core Components](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml).
