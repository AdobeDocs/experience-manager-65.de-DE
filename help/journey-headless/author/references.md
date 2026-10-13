---
title: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten
description: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten für Inhalte, andere Fragmente und andere Assets (Medien). Einführung in die Notwendigkeit und die Mechanik verschachtelter Fragmente für Headless-CMS-Seitenbearbeitung.
exl-id: d54a0a40-a8af-456a-9bf5-219d84540c97
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer, User, Leader
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 96%
---
# Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten {#author-headless-references}

## Die bisherige Entwicklung {#story-so-far}

Zu Beginn der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in der [Einführung](introduction.md) die grundlegenden Konzepte und die Terminologie für das Authoring für Headless behandelt.

Sie haben die Grundlagen der Headless-CMS-Seitenbearbeitung kennengelernt, mit einer Einführung in die Seitenbearbeitung mit AEM as a Cloud Service und insbesondere die Bearbeitung von Inhaltsfragmenten.

Dieser Artikel baut auf diesen auf. Sie erfahren, wie Sie Verweise verwenden können, um eigene Inhalte für Ihr AEM Headless-Projekt zu erstellen.

## Ziel {#objective}

* **Zielgruppe**: Fortgeschrittene
* **Ziel**: Einführung der Verwendung von Verweisen für die Headless-CMS-Seitenbearbeitung. Welche Arten von Verweisen sind verfügbar und zu welchen Zwecken dienen sie?

  * Inhaltsreferenzen
  * Asset-/Medienverweise
  * Fragmentreferenzen
  * Ad-hoc-Verweise aus einem Textblock

## Was sind Verweise {#what-are-references}

Verweise sind lediglich ein Mechanismus zum Verbinden Ihrer Ressourcen, sei es mit anderen Inhalten, Assets (wie in Bildern) oder anderen Fragmenten. Obwohl sie sehr ähnlich sind, gibt es einige Unterschiede.

Einige Verweise verfügen über dedizierte Datentypen (z. B. Inhaltsverweise und Fragmentverweise), während andere einfach als Verweis in einem Textblock hinzugefügt werden (Asset-Verweise und Ad-hoc-Verweise).

![Inhaltsfragmente – Verweise](/help/journey-headless/author/assets/headless-journey-author-references-01.png)

## Inhaltsreferenzen {#content-references}

Inhaltsverweise tun genau das – sie ermöglichen es Ihnen, auf beliebige andere Inhalte zu verweisen. Dadurch wird ein Browser geöffnet, in dem Sie das Inhaltselement auswählen können.

## Asset-/Medienverweise {#assets-media-references}

Mithilfe der Option **Asset einfügen** können Sie innerhalb eines Textblocks auf Assets (z. B. Bilder oder Medien) verweisen. Dadurch wird ein Browser geöffnet, in dem Sie das Asset auswählen können.

![Inhaltsfragmente – Asset einfügen](/help/journey-headless/author/assets/headless-journey-author-references-02.png)

## Fragmentreferenzen {#fragment-references}

Fragmentverweise tun genau das – sie ermöglichen es Ihnen, auf ein anderes Fragment zu verweisen. Warum dies von Bedeutung ist, bedarf einer näheren Erläuterung.

Bei Ihnen sind möglicherweise die folgenden Inhaltsfragmentmodelle definiert:

* Stadt
* Unternehmen
* Person
* Auszeichnungen

Es scheint ziemlich einfach zu sein, aber ein Unternehmen hat sowohl einen CEO als auch Mitarbeiter…. und das sind alles Personen, die jeweils als Person definiert sind.

Und eine Person kann eine Auszeichnung bekommen (oder vielleicht zwei).

* Meine Firma – Firma
  * CEO – Person
  * Mitarbeiter – Person
    * Persönliche Auszeichnungen – Auszeichnung

Und das ist nur für den Einstieg. Je nach Komplexität kann eine Auszeichnung firmenspezifisch sein oder eine Firma könnte ihre Hauptverwaltung in einer bestimmten Stadt haben.

Die Repräsentation dieser Beziehungen kann mit Fragmentverweisen erreicht werden, da diese sowohl von Ihnen (dem Autor) als auch von den Headless-Programmen verstanden werden.

Als Autor sind Sie nicht für die Definition dieser Beziehungen verantwortlich (das wird vom Inhaltsarchitekten beim Erstellen des Inhaltsfragmentmodells vorgenommen), Sie müssen jedoch wissen, wie Sie die Verweise erkennen und bearbeiten können.

### Bearbeiten verschachtelter Fragmente {#author-nested-fragment}

Die Bearbeitung von Fragmentverweisen ist relativ einfach (obwohl das Feld normalerweise nicht als **Fragmentverweis** bezeichnet wird). Sie können den Verweis entweder direkt eingeben oder (wahrscheinlicher) auf das Ordnersymbol klicken, um einen Browser zu öffnen, in dem Sie navigieren und das gewünschte Fragment auswählen können.

![Inhaltsfragmente – Verweise](/help/journey-headless/author/assets/headless-journey-author-references-03.png)

Die Definition des Inhaltsfragmentmodells steuert:

* ob Sie wählen können, mehrere Verweise hinzuzufügen
* die Modelltypen der Inhaltsfragmente, die Sie auswählen können. Das Inhaltsfragmentmodell definiert die Fragmentmodelle, die für den Verweis zulässig sind, sodass AEM nur Fragmente basierend auf diesen Modellen anzeigt.

### Navigieren in verschachtelten Fragmenten {#navigate-nested-fragment}

Wenn Sie die Registerkarte **Baumstruktur** des Inhaltsfragment-Editors verwenden, können Sie durch die Fragmente navigieren, auf die Ihr Fragment verweist, und dann durch alle Verweise, die sie möglicherweise enthalten. Wenn Sie eine Referenz auswählen, wird dieses Fragment zur Bearbeitung geöffnet.

>[!NOTE]
>
>Mithilfe der Breadcrumbs im Hauptbedienfeld können Sie zurück zu Ihrem Ausgangspunkt gelangen.

![Strukturbaum der Inhaltsfragmente](/help/assets/content-fragments/assets/cfm-structuretree-02.png)

## Ad-hoc-Verweise {#adhoc-references}

Ad-hoc-Verweise können als einfacher Link innerhalb eines Textblocks hinzugefügt werden:

![Inhaltsfragmente – Ad-hoc-Verweise](/help/journey-headless/author/assets/headless-journey-author-references-04.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie sich mit Verweisen und Strukturen in Inhaltsfragmenten vertraut gemacht haben, fahren Sie mit dem nächsten Schritt fort: [Erfahren Sie mehr über Metadaten und Tagging](metadata-tagging.md). In diesem Abschnitt wird erläutert, wie Sie Metadaten und Tags für Ihre Inhaltsfragmente definieren können.

## Zusätzliche Ressourcen {#additional-resources}

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

  * [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)

    * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

    * [Erstellen eines Inhaltsfragments](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)

  * [Varianten – Authoring von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md)

  * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

    * [Inhaltsfragmentmodelle – Datentypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

    * [Inhaltsfragmentmodelle – Eigenschaften](/help/assets/content-fragments/content-fragments-models.md#properties)

* Anleitungen für den Einstieg
  * [Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [AEM Headless-Inhaltsarchitekten-Tour](/help/journey-headless/architect/overview.md)

* [AEM Headless-Übersetzungs-Tour](/help/journey-headless/translation/overview.md)
