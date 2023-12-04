---
title: Authoring von Commerce-Erlebnissen
description: Das CIF-Add-on erweitert das Adobe Experience Manager-Authoring mit Commerce-spezifischen Funktionen.
exl-id: 2db51bd7-8fc7-4ae8-8d6f-e5035fbe954d
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 89%

---

# Authoring von Commerce-Erlebnissen {#authoring-commerce-experiences}

## Übersicht {#overview}

Das CIF-Add-on erweitert die Bearbeitung in AEM mit Commerce-spezifischen Funktionen. Dadurch können Autoren Commerce-bezogene Erlebnisse effizient erstellen und verwalten, indem sie auf Produktdaten und Inhalte zugreifen können, ohne den Kontext verlassen zu müssen.

## Auswahloptionen {#pickers}

Produkt- und Kategorieauswahloptionen sind Dialogfelder der modalen Benutzeroberfläche, mit denen AEM-Autoren bei Bedarf Produkte oder Kategorien finden und auswählen können. Kernkomponenten, Inhaltsverknüpfung und Produktvorlagen sind die typischen Bereiche mit Konfigurationen, für die Produktkatalogdaten erforderlich sind. Auswahloptionen unterstützen verschiedene Konfigurationsoptionen, z. B. Mehrfachauswahl, Variantenauswahl und Vorabauswahl von Werten.

### Produktauswahl {#product-picker}

Diese Auswahl kann das Durchsuchen der Katalogstruktur oder die Volltextsuche anbieten, um das Produkt zu finden. Produkte mit Variante bieten in der Spalte „Typ“ ein Ordnersymbol. Durch Klicken auf das Ordnersymbol werden die Varianten des ausgewählten Produkts geöffnet.

![Produktauswahl](/help/commerce/cif/assets/authoring/product-picker.png)

Durch Klicken auf die übergeordnete Kategorie kehrt der Autor zur Produktebene zurück.

![Produktauswahl](/help/commerce/cif/assets/authoring/product-picker-variation.png)

**Beispiel für Produkt-Teaser**

![Teaser-Komponente ohne Auswahl](/help/commerce/cif/assets/authoring/teaser_component_without_selection.png)

Das Konfigurationsdialogfeld dieser Komponente erfordert ein Produkt. CIF verwendet die SKU als Produktkennung. Autoren können entweder die SKU manuell eingeben oder auf das Ordnersymbol klicken, um die Produktauswahl zu öffnen. Nach dem Auswählen und Schließen der Auswahl zeigt das Komponentendialogfeld den Namen des ausgewählten Produkts an.

![Teaser-Komponente mit Auswahl](/help/commerce/cif/assets/authoring/teaser_component_with_selection.png)

### Kategorieauswahl {#category-picker}

Diese Auswahl kann das Durchsuchen der Katalogstruktur anbieten, um die Kategorie zu finden.

![Kategorieauswahl](/help/commerce/cif/assets/authoring/category-picker.png)

**Beispiel für Kategoriekarussell**

![Karussellkomponente ohne Auswahl](/help/commerce/cif/assets/authoring/carousel_component_without_selection.png)

Das Konfigurationsdialogfeld dieser Komponente erfordert 1:n Kategorien. CIF verwendet die UID/ID als Kategoriekennung. Autoren können entweder die UID manuell eingeben oder auf das Ordnersymbol klicken, um die Kategorieauswahl zu öffnen. Nach dem Auswählen und Schließen der Auswahl zeigt das Komponentendialogfeld den Namen der ausgewählten Kategorie an.

![Karussellkomponente mit Auswahl](/help/commerce/cif/assets/authoring/carousel_component_with_selection.png)

## Universeller Editor {#universal-editor}

Der universelle Editor wird um Funktionen erweitert, mit denen Sie auf die Echtzeit-Produktdaten und zugehörigen Produktinhalte zugreifen können.

### Zugreifen auf Produktdaten {#access-product-data}

Die Registerkarte „Elemente“ im Seitenbereich des Editors bietet Zugriff auf Produktdaten, indem der Typ „Produkte“ ausgewählt wird. Die Daten werden live vom konfigurierten Commerce-Endpunkt abgerufen. Der Filter ist eine Volltextsuche auf dem Commerce-Endpunkt, um nach bestimmten Produkten zu suchen.

![Seitenbereich für Produktdaten](/help/commerce/cif/assets/authoring/products-side-panel.png)

Analog zu Elementen können Produkte (wodurch standardmäßig eine Produkt-Teaser-Komponente erstellt wird) oder Komponenten (derzeit werden Produkt-Teaser und Produktkarussell unterstützt) auf einer Seite hinzugefügt werden.

### Hinzufügen von Links in Textfeldern mithilfe von RTE {#rte}

CIF-Produktkatalogseiten sind virtuelle Seiten, die dynamisch gerendert werden. Daher ist das Einbetten von Hyperlinks wie bei regulären AEM-Seiten nicht möglich. CIF fügt eine neue Aktion für Commerce-Links zum RTE (Rich-Text-Editor) hinzu. Diese Aktion funktioniert genau wie die normale Aktion „Hyperlink“, ermöglicht es Autoren jedoch, entweder ein Produkt oder eine Kategorie mithilfe der Auswahl auszuwählen.

![RTE](/help/commerce/cif/assets/authoring/RTE.png)

    >[!NOTE]
    >
    >Wenn sowohl Kategorie als auch Produkt ausgewählt werden, wird das Produkt verwendet.

Dadurch wird ein Platzhalter-Link erstellt, der beim Rendern der Seite durch einen echten Link ersetzt wird.

### Zugreifen auf zugehörige Produktinhalte {#associated-content}

Wenn der universelle Editor 1:n Produkte auf einer Seite erkennt, wird im Seitenbereich automatisch die Registerkarte „Zugehörige Commerce-Inhalte“ angezeigt. Auf dieser Registerkarte können Autoren schnell auf AEM-Inhalt zugreifen, der mit dem Produkt getaggt wurde (weitere Informationen finden Sie unter [Anreichern von Produktdaten mit zugehörigem AEM-Inhalt](./enrich-product-associated-content.md)). Auf dieser Registerkarte finden Sie Dropdown-Listen, mit denen nach Inhaltstyp und bestimmten Produkten gefiltert werden kann, wenn sich mehrere Produkte auf der Seite befinden. Die Verwendung des Inhalts funktioniert wie die Verwendung von Inhalt auf der Registerkarte „Elemente“.

![Seitenbereich für Produktdaten](/help/commerce/cif/assets/authoring/associated-commerce-content-tab.png)

### Vorschau von gestaffelten Produktdaten {#staged-data}

Der Timewarp-Modus im Editor ermöglicht es Autoren, ein AEM-Erlebnis mit gestaffelten Produktkatalogdaten basierend auf dem Timewarp-Datum in der Vorschau anzuzeigen und zu durchsuchen.

![Timewarp](/help/commerce/cif/assets/authoring/timewarp.png)

Komponenten zeigen einen visuellen Indikator an, wenn das verwendete Datum gestaffelt ist.

![Indikator für „Gestaffelt“](/help/commerce/cif/assets/authoring/staged-indicator.png)

## Omnisearch {#omnisearch}

Die Verwendung von Omnisearch ist eine einfache Möglichkeit für Anwender, AEM-Inhalt und Produktkatalogdaten mithilfe der Volltextsuche zu finden. Omnisearch führt die Volltextsuche in AEM und im Commerce-Backend durch, um Produktkatalogobjekte im Commerce-Backend und AEM-Inhalt zu finden. AEM Ergebnisse umfassen auch Inhalte, die mit Produkt-/Kategoriedaten getaggt wurden.

![Omnisearch](/help/commerce/cif/assets/authoring/omnisearch.png)

Das Ergebnis wird nach Typ gruppiert.

    >[!NOTE]
    >
    >Volltextsuche in Omnisearch unterstützt keine verknüpften Inhaltsfragmente. Verwenden Sie SKU oder UID, um verknüpfte Inhaltsfragmente zu finden.
