---
title: Verfassen von Commerce-Erlebnissen
description: Commerce-Erlebnisse verwenden
source-git-commit: f3e286c7b5404812655f3b257de17be7bfde7487
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---

# Verfassen von Commerce-Erlebnissen {#authoring-commerce-experiences}

## Übersicht {#overview}

Das CIF-Add-on erweitert AEM Authoring mit Commerce-spezifischen Funktionen. Dadurch können Autoren Commerce-bezogene Erlebnisse effizient erstellen und verwalten, indem sie auf Produktdaten und Inhalte zugreifen können, ohne den Kontext verlassen zu müssen.

## Picker {#pickers}

Produkt- und Kategorieauswahlen sind Dialogfelder der modalen Benutzeroberfläche, mit denen AEM Autoren bei Bedarf Produkte oder Kategorien finden und auswählen können. Kernkomponenten, Inhaltsverknüpfung und Produktvorlagen sind die typischen Bereiche mit Konfigurationen, für die Produktkatalogdaten erforderlich sind. Picker unterstützen verschiedene Konfigurationsoptionen, z. B. Mehrfachauswahl, Variantenauswahl und Vorab-Auswahl von Werten.

### Produktauswahl {#product-picker}

Diese Auswahl bietet die Möglichkeit, durch die Katalogstruktur oder die Volltextsuche zu navigieren, um das Produkt zu finden. Produkte mit Variante bieten in der Spalte &quot;Typ&quot;ein Ordnersymbol. Durch Klicken auf das Ordnersymbol werden die Varianten des ausgewählten Produkts geöffnet.

![Produktauswahl](/help/commerce/cif/assets/authoring/product-picker.png)

Wenn Sie auf die übergeordnete Kategorie klicken, kehrt der Autor zur Produktebene zurück.

![Produktauswahl](/help/commerce/cif/assets/authoring/product-picker-variation.png)

**Beispiel für Produkt-Teaser**

![Teaser-Komponente ohne Auswahl](/help/commerce/cif/assets/authoring/teaser_component_without_selection.png)

Das Konfigurationsdialogfeld dieser Komponente erfordert ein Produkt. CIF verwendet die SKU als Produktkennung. Autoren können entweder die SKU manuell eingeben oder auf das Ordnersymbol klicken, um die Produktauswahl zu öffnen. Nach dem Auswählen und Schließen der Auswahl zeigt das Komponentendialogfeld den Namen des ausgewählten Produkts an

![Teaser-Komponente mit Auswahl](/help/commerce/cif/assets/authoring/teaser_component_with_selection.png)

### Kategorieauswahl {#category-picker}

Mit diesem Picker können Sie die Katalogstruktur durchsuchen, um die Kategorie zu finden.

![Kategorieauswahl](/help/commerce/cif/assets/authoring/category-picker.png)

**Beispiel-Kategoriekarussell**

![Karussellkomponente ohne Auswahl](/help/commerce/cif/assets/authoring/carousel_component_without_selection.png)

Das Konfigurationsdialogfeld dieser Komponente erfordert 1 : n Kategorien. CIF verwendet die UID/ID als Kategoriekennung. Autoren können entweder die UID manuell eingeben oder auf das Ordnersymbol klicken, um die Kategorieauswahl zu öffnen. Nach dem Auswählen und Schließen der Auswahl zeigt das Komponentendialogfeld den Namen der ausgewählten Kategorie an.

![Karussellkomponente mit Auswahl](/help/commerce/cif/assets/authoring/carousel_component_with_selection.png)

## Universal Editor {#universal-editor}

Der universelle Editor wird um Funktionen erweitert, mit denen Sie auf die Echtzeit-Produktdaten und zugehörigen Produktinhalte zugreifen können.

### Zugriff auf Produktdaten {#access-product-data}

Die Registerkarte &quot;Assets&quot;im seitlichen Bedienfeld des Editors bietet Zugriff auf Produktdaten, indem der Typ &quot;Produkte&quot;ausgewählt wird. Die Daten werden live vom konfigurierten Commerce-Endpunkt abgerufen. Der Filter ist eine Volltextsuche am Commerce-Endpunkt, um nach bestimmten Produkten zu suchen.

![Seitenbereich für Produktdaten](/help/commerce/cif/assets/authoring/products-side-panel.png)

Analog zu Assets können Produkte auf einer Seite hinzugefügt werden (wodurch standardmäßig eine Produkt-Teaser-Komponente erstellt wird) oder Komponenten (derzeit werden Produkteaser und Produktkarussell unterstützt).

### Hinzufügen von Links in Textfeldern mithilfe des RTE {#rte}

CIF-Produktkatalogseiten sind virtuelle Seiten, die dynamisch gerendert werden. Daher ist das Einbetten von Hyperlinks wie für reguläre AEM nicht möglich. CIF fügt eine neue Aktion &quot;Commerce Links&quot;zum RTE (Rich-Text-Editor) hinzu. Diese Aktion funktioniert genau wie die normale Aktion &quot;Hyperlink&quot;, ermöglicht es Autoren jedoch, entweder ein Produkt oder eine Kategorie mithilfe der Auswahl auszuwählen.

![RTE](/help/commerce/cif/assets/authoring/RTE.png)

    >[!NOTE]
    >
    > Wenn sowohl Kategorie als auch Produkt ausgewählt werden, wird das Produkt ausgewählt.

Dadurch wird ein Platzhalterlink erstellt, der beim Rendern der Seite durch einen echten Link ersetzt wird.

### Zugreifen auf zugehörige Produktinhalte {#associated-content}

Wenn der universelle Editor 1:n-Produkte auf einer Seite erkennt, wird im Seitenbereich automatisch die Registerkarte &quot;Zugehörige Commerce-Inhalte&quot;angezeigt. Auf dieser Registerkarte können Autoren schnell auf AEM Inhalt zugreifen, der mit dem Produkt getaggt wurde (siehe [Anreicherung von Produktdaten mit zugehörigen AEM](./enrich-product-associated-content.md) für weitere Informationen). Auf dieser Registerkarte finden Sie Dropdown-Listen, mit denen nach Inhaltstyp und bestimmten Produkten gefiltert werden kann, wenn sich mehrere Produkte auf der Seite befinden. Die Verwendung des Inhalts funktioniert genauso wie die Verwendung von Inhalten auf der Registerkarte &quot;Assets&quot;.

![Seitenbereich für Produktdaten](/help/commerce/cif/assets/authoring/associated-commerce-content-tab.png)

### Vorschau von gestaffelten Produktdaten {#staged-data}

Der Timewarp-Modus im Editor ermöglicht es Autoren, ein AEM Erlebnis mit gestaffelten Produktkatalogdaten basierend auf dem Timewarp-Datum in der Vorschau anzuzeigen und zu durchsuchen.

![Timewarp](/help/commerce/cif/assets/authoring/timewarp.png)

Komponenten zeigen einen visuellen Indikator an, wenn das verwendete Datum gestaffelt ist.

![Staging-Anzeige](/help/commerce/cif/assets/authoring/staged-indicator.png)

## Omnisearch {#omnisearch}

Die Verwendung von Omnisearch ist eine einfache Möglichkeit für Anwender, AEM Inhalte und Produktkatalogdaten mithilfe der Volltextsuche zu finden. Omnisearch führt die Volltextsuche in AEM und im Commerce-Backend durch, um Produktkatalogobjekte im Commerce-Backend und AEM Inhalt zu finden. AEM Ergebnisse umfassen auch Inhalte, die mit Produkt-/Kategoriedaten getaggt wurden.

![Omnisearch](/help/commerce/cif/assets/authoring/omnisearch.png)

Das Ergebnis wird nach Typ gruppiert.

    >[!NOTE]
    >
    > Volltextsuche in Omnisearch unterstützt keine zugehörigen Inhaltsfragmente. Verwenden Sie SKU oder UID, um verknüpfte Inhaltsfragmente zu finden.
