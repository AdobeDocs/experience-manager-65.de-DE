---
title: Testen von Inhaltsfragmenten in We.Retail
seo-title: Testen von Inhaltsfragmenten in We.Retail
description: 'null'
seo-description: 'null'
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
translation-type: tm+mt
source-git-commit: dca52c05c413fc96bf7fab012a3be52f6769c2e0

---


# Testen von Inhaltsfragmenten in We.Retail{#trying-out-content-fragments-in-we-retail}

Inhaltsfragmente ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen. **We.Retail** (wie in einer vordefinierten AEM-Instanz verfügbar) stellt das Fragment **Arctic Surfing in Lofoten** als Grundmuster bereit. Dies verdeutlicht:

* Adobe Experience Manager (AEM)-Inhaltsfragmente werden [als seitenunabhängige Assets erstellt und verwaltet](/help/assets/content-fragments.md). Sie ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen.

   * See [Where to Find Content Fragment assets in We.Retail](#where-to-find-content-fragments-in-we-retail)

* Sie können [diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten](/help/sites-authoring/content-fragments.md) verwenden.

   * See [Where Content Fragments are Used in We.Retail](#where-content-fragments-are-used-in-we-retail)

Die vollständige Dokumentation zum Erstellen, Verwalten, Nutzen und Entwickeln von Inhaltsfragmenten:

* See [Further Information](#further-information)

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-authoring/experience-fragments.md)**sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte, vor allem Text und zugehörige Bilder. Dabei handelt es sich um reinen Inhalt ohne Design und Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Webseiten dar.
>
>
Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.

## Suche nach Inhaltsfragment-Assets in We.Retail {#where-to-find-content-fragments-in-we-retail}

There are several sample content fragments in We.Retail; navigate via **Assets**, **Files**, **We.Retail**, **English**, **Experiences**.

Diese enthalten **Arktisches Surfen in Lofoten**, ein Fragment zusammen mit dazu gehörenden visuellen Assets:

* Navigate via **Assets**, **Files**, **We.Retail**, **English**, **Experiences**, **Artic Surfing in Lofoten**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten) 

![cf-44](assets/cf-44.png)

Sie können das Fragment **Arktisches Surfen in Lofoten** auswählen und bearbeiten:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Hier können Sie Ihr Fragment anhand der Registerkarten (linkes Bedienfeld) [bearbeiten und verwalten](/help/assets/content-fragments.md):

<!--![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png) ASSET does not exist-->

* **[Variationen](/help/assets/content-fragments-variations.md)**einschließlich[Markdown](/help/assets/content-fragments-markdown.md)
* **[Zugehörige Inhalte](/help/assets/content-fragments-assoc-content.md)**
* **[Metadaten](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Verwendung von Inhaltsfragmenten in We.Retail {#where-content-fragments-are-used-in-we-retail}

Unter folgendem Link finden Sie mehrere Beispiele zum Veranschaulichen der [Seitenerstellung mit einem Inhaltsfragment](/help/sites-authoring/content-fragments.md):

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

For example, the **Arctic Surfing in Lofoten** content fragment is referenced in the Sites page:

* Navigate via **Sites**, **We.Retail**, **Language Masters**, **English**, **Experience**. Öffnen Sie dann **Arktisches Surfen in Lofoten** zur Bearbeitung:

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [Arbeiten mit Inhaltsfragmenten ](/help/assets/content-fragments.md)

   * Hier erfahren Sie, wie Sie Ihre Inhaltsfragment-Assets erstellen, bearbeiten und verwalten.

* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)

   * Verwenden Sie Ihr Inhaltsfragment beim Erstellen einer Seite.

* [Entwickeln von AEM-Komponenten für Inhaltsfragmente](/help/sites-developing/components-content-fragments.md)

   * Ein Überblick über die Komponenten für Inhaltsfragmente.

* [Entwickeln und Erweitern von Inhaltsfragmenten](/help/sites-developing/customizing-content-fragments.md)

   * Informationen, mit deren Hilfe Sie Inhaltsfragmente entwickeln und erweitern können.

