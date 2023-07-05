---
title: Kampagnen-Management
seo-title: Campaign Management
description: Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen. Damit können Sie Ihre Marketing-Kampagnen über Web-, E-Mail- und Mobile-Services hinweg koordinieren und so Ihre Besucher binden.
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: d1741525-a475-4a76-bd16-55318023495e
source-git-commit: 1ba34f95cf3ce3f136482075802d2e4372f28917
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 42%

---


# Kampagnen-Management{#campaign-management}

Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen.

Damit können Sie Ihre Marketing-Kampagnen über Web-, E-Mail- und Mobile-Services hinweg koordinieren und so Ihre Besucher binden. Sie können Inhalte erstellen, Besucher segmentieren, zielgerichtete Inhalte für bestimmte Benutzerprofile pushen und bewerben und Kampagnen über mehrere Kanäle hinweg verwalten.

In diesem Dokument werden die verschiedenen Elemente der Kampagnen beschrieben. Weitere Informationen finden Sie in den folgenden Dokumenten:

* [Teaser und Strategien](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [E-Mail-Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Landing-Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Target-Angebote](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Arbeiten mit dem Marketing Campaign Manager](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Grundlegendes zur Segmentierung](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Einrichten einer Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

Die Kampagnenverwaltung besteht aus verschiedenen Elementen:

* **Marken**
In AEM bilden Marken die oberste Ebene und bilden eine Sammlung von **Kampagnen**.

* **Kampagnen**
Eine Kampagne ist eine Kollektion einzelner **Erlebnisse**.

* **Erlebnisse**
Der fokussierte Inhalt bildet die verschiedenen Erlebnisse, die dem Besucher unter **Touchpoints**. Es stehen verschiedene Erlebnistypen zur Verfügung:

   * **Teasers**
     [Teaser-Seiten/-Absätze](#teasers) dienen dazu, bestimmte **Besuchersegmente** zu Inhalten zu leiten, die auf ihre Interessen ausgerichtet sind.

     Teaser-Seiten können:

      * eine Reihe von Optionen zur Auswahl für den Besucher anbieten
      * nur einen Teaser-Absatz anzeigen, der auf dem spezifischen Besuchersegment basiert; Beispielsweise kann der angezeigte Teaser-Absatz vom Alter des Besuchers abhängen.

     Normalerweise ist eine Teaser-Seite eine temporäre Aktion, die für einen bestimmten Zeitraum anhält, bis sie durch die nächste Teaser-Seite ersetzt wird.

   * **Newsletter**

     [E-Mail-Nachrichten](#emailmarketing) werden verwendet, um Benutzer einzubinden und sie zum Besuchen der Website anzuregen. Im Allgemeinen haben sie die Form eines Newsletters, der an die **Leads** gesendet wird (die im Allgemeinen in **Listen** unterteilt sind). **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen. Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

   * **Adobe Target**

     Dies ermöglicht die Integration in Adobe Target (ehemals Test&amp;Target), das Marketing-Experten ein Tool zur Konversionswebsite-Optimierung mit den erforderlichen Funktionen bietet, um ihre Online-Inhalte und -Angebote für ihre Kunden relevanter zu machen und so eine höhere Konversionsrate zu erzielen. Adobe Target bietet eine intuitive Benutzeroberfläche für die Konzeption und Ausführung von Tests, die Erstellung von Zielgruppensegmenten und das Targeting von Inhalten in einer einzigen Anwendung.

* **Touchpoints**

  Dies sind die Kontaktpunkte zwischen dem Besucher und Ihrer Kampagne. Die Touchpoints sind mit den von Ihnen erstellten Erlebnissen verknüpft.

  Bei Teasern ist es beispielsweise die Inhaltsseite, auf der sich der Teaser-Absatz befindet, bei einem Newsletter ist es die Mailingliste.

* **Leads**

  Die Informationen, die Sie über Ihre Besucher und die Kontaktaufnahme mit ihnen gesammelt haben, bildet die Grundlage für Ihre Leads. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **Listen**

  Leads werden im Allgemeinen in Listen gruppiert, damit Sie kollektive Aktionen auf sie anwenden können. Hinweis: **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **Segmente**

  Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Durch die Analyse nach Faktoren wie Aktivität auf der Website, registrierte Profilinformationen sowie Aktivität auf anderen Websites können Sie Segmente definieren. Inhalte können dann entsprechend den jeweiligen Segmenten speziell auf die Anforderungen und Interessen des Besuchers abgestimmt werden.

* **MCM**

  Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie auf alle Funktionen zugreifen können, die Sie zum Erstellen und Steuern Ihrer Kampagnen, Marken, Erlebnisse, Touchpoints, Leads, Listen, Segmente und Berichte benötigen.

  Der Zugriff erfolgt über verschiedene Orte (mit der Bezeichnung **Kampagnen**) oder mit der URL:

  `http://localhost:4502/libs/mcm/content/admin.html`
