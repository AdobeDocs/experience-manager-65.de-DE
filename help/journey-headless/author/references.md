---
title: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten
description: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten für Inhalte, andere Fragmente und andere Assets (Medien). Einführung der Notwendigkeit und der Mechanik verschachtelter Fragmente für Headless CMS Authoring.
index: true
hide: false
hidefromtoc: false
source-git-commit: 9661061a98c31fbb74bd0716dbedc7abef298f44
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 10%

---

# Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten {#author-headless-references}

## Die Geschichte so weit {#story-so-far}

Am Anfang des [AEM Headless Content Author-Journey](overview.md) die [Einführung](introduction.md) die grundlegenden Konzepte und Terminologie für das Headless-Authoring behandelt.

Sie haben die Grundlagen der Headless-CMS-Bearbeitung kennengelernt, mit einer Einführung in das Authoring mit AEMaaCS und insbesondere das Authoring von Inhaltsfragmenten.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie Verweise verwenden können, um eigene Inhalte für Ihr AEM Headless-Projekt zu erstellen.

## Ziel {#objective}

* **Zielgruppe**: Fortgeschrittene
* **Ziel**: Einführung der Verwendung von Referenzen für Headless CMS Authoring. Welche Arten von Verweisen sind verfügbar und zu welchen Zwecken dienen sie?

   * Inhaltsreferenzen
   * Asset-/Medienreferenzen
   * Fragmentreferenzen
   * Ad-hoc-Verweise aus einem Textblock

## Verweise {#what-are-references}

Referenzen sind lediglich ein Mechanismus zum Verbinden Ihrer Ressourcen, sei es mit anderen Inhalten, Assets (wie in Bildern) oder anderen Fragmenten. Obwohl sehr ähnlich, gibt es einige Unterschiede.

Einige Verweise verfügen über dedizierte Datentypen (z. B. Inhaltsverweise und Fragmentverweise), während andere einfach als Verweis in einem Textblock hinzugefügt werden (Asset-Verweise und Ad-hoc-Verweise).

![Inhaltsfragmente - Verweise](/help/journey-headless/author/assets/headless-journey-author-references-01.png)

## Inhaltsreferenzen {#content-references}

Inhaltsreferenzen tun genau das - sie ermöglichen es Ihnen, auf beliebige andere Inhalte zu verweisen. Dadurch wird ein Browser geöffnet, in dem Sie das Inhaltselement auswählen können.

## Asset-/Medienreferenzen {#assets-media-references}

Assets (z. B. Bilder oder Medien) können in einem Textblock mithilfe der **Asset einfügen** -Option. Dadurch wird ein Browser geöffnet, in dem Sie das Asset auswählen können.

![Inhaltsfragmente - Asset einfügen](/help/journey-headless/author/assets/headless-journey-author-references-02.png)

## Fragmentreferenzen {#fragment-references}

Fragmentverweise tun genau das - sie ermöglichen es Ihnen, auf ein anderes Fragment zu verweisen. Warum dies bedeutsam ist, bedarf es etwas mehr Erklärungen.

Sie können beispielsweise die folgenden Inhaltsfragmentmodelle definieren:

* Stadt
* Unternehmen
* Person
* Auszeichnungen

Es scheint ziemlich einfach, aber natürlich hat ein Unternehmen sowohl einen CEO als auch Mitarbeiter....und dies sind alle Personen, die jeweils als Person definiert sind.

Und eine Person kann einen Preis bekommen (oder vielleicht zwei).

* My Company - Company
   * CEO - Person
   * Arbeitnehmer(innen) - Person
      * Persönliche Auszeichnungen - Auszeichnung

Und das ist nur für Anfänger. Je nach Komplexität kann ein Preis unternehmensspezifisch sein oder eine Firma könnte ihre Hauptverwaltung in einer bestimmten Stadt haben.

Die Repräsentation dieser Beziehungen kann mit Fragmentverweisen erreicht werden, da diese sowohl von Ihnen (dem Autor) als auch von den Headless-Anwendungen verstanden werden.

Als Autor sind Sie nicht für die Definition dieser Beziehungen verantwortlich (das wird vom Inhaltsarchitekten beim Erstellen des Inhaltsfragmentmodells vorgenommen), Sie müssen jedoch wissen, wie Sie die Verweise erkennen und bearbeiten können.

### Erstellen verschachtelter Fragmente {#author-nested-fragment}

Die Erstellung von Fragmentverweisen ist relativ einfach (obwohl das Feld normalerweise nicht als **Fragmentverweis**). Sie können die Referenz entweder direkt eingeben oder (wahrscheinlicher) das Ordnersymbol auswählen, um einen Browser zu öffnen, in dem Sie navigieren und das gewünschte Fragment auswählen können.

![Inhaltsfragmente - Verweise](/help/journey-headless/author/assets/headless-journey-author-references-03.png)

Die Definition der Steuerelemente für das Inhaltsfragmentmodell:

* ob Sie mehrere Verweise hinzufügen können
* die Modelltypen der Inhaltsfragmente, die Sie auswählen können; Das Inhaltsfragmentmodell definiert die Fragmentmodelle, die für die Referenz zulässig sind, sodass AEM nur Fragmente basierend auf diesen Modellen präsentiert.

### Navigieren in verschachtelten Fragmenten {#navigate-nested-fragment}

Verwenden der **Strukturbaum** im Inhaltsfragment-Editor können Sie durch die Fragmente navigieren, auf die von Ihrem Fragment verwiesen wird, und dann durch alle darin enthaltenen Verweise. Wenn Sie eine Referenz auswählen, wird dieses Fragment zur Bearbeitung geöffnet.

>[!NOTE]
>
>Mithilfe der Breadcrumbs im Hauptbedienfeld können Sie zurück zu Ihrem Ausgangspunkt gelangen.

![Strukturbaum der Inhaltsfragmente](/help/assets/content-fragments/assets/cfm-structuretree-02.png)

## Ad-hoc-Verweise {#adhoc-references}

Ad-hoc-Verweise können als einfacher Link innerhalb eines Textblocks hinzugefügt werden:

![Inhaltsfragmente - Ad-hoc-Verweise](/help/journey-headless/author/assets/headless-journey-author-references-04.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie sich mit Verweisen und Strukturen in Inhaltsfragmenten vertraut gemacht haben, müssen Sie als Nächstes [Erfahren Sie mehr über Metadaten und Tagging](metadata-tagging.md). In diesem Abschnitt wird erläutert, wie Sie Metadaten und Tags für Ihre Inhaltsfragmente definieren können.

## Zusätzliche Ressourcen {#additional-resources}

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)

      * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Erstellen eines Inhaltsfragments](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [Varianten - Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Inhaltsfragmentmodelle - Datentypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Inhaltsfragmentmodelle - Eigenschaften](/help/assets/content-fragments/content-fragments-models.md#properties)


* Anleitungen für den Einstieg
   * [Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [Journey AEM Headless Content Architect](/help/journey-headless/architect/overview.md)

* [AEM Headless Translation Journey](/help/journey-headless/translation/overview.md)
