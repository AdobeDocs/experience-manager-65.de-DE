---
title: Kampagnen-Management
description: Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen. Es bietet Ihnen die Möglichkeit, Marketing-Kampagnen für Internet, E-Mail und Mobile Services zu erstellen und so Benutzerinteraktionen auszulösen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: d1741525-a475-4a76-bd16-55318023495e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 100%

---


# Kampagnen-Management{#campaign-management}

Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucherinnen und Besucher zu schaffen.

Es bietet Ihnen die Möglichkeit, Marketing-Kampagnen für Internet, E-Mail und Mobile Services zu erstellen und so Benutzerinteraktionen auszulösen.  Sie können Inhalte erstellen, Besuchende in Segmente einteilen, zielgerichtete Inhalte an bestimmte Benutzerprofile weiterleiten und Kampagnen über mehrere Kanäle verwalten.

Dieses Dokument beschreibt die verschiedenen Elemente, aus denen Kampagnen bestehen.  Weitere Informationen finden Sie in folgenden Dokumenten:

* [Teaser und Strategien](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [E-Mail-Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Landing-Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Target-Angebote](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Arbeiten mit dem Marketing Campaign Manager](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Grundlegendes zur Segmentierung](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Einrichten einer Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

Das Kampagnen-Management umfasst verschiedene Elemente:

* **Marken**
In Adobe Experience Manager (AEM) bilden Marken die höchste Ebene und stellen eine Sammlung von **Kampagnen** dar.

* **Kampagnen**
Eine Kampagne ist eine Sammlung einzelner **Erlebnisse**.

* **Erlebnisse**
Die zielgerichteten Inhalte bilden verschiedene Erlebnisse, die Besucherinnen und Besuchern an **Touchpoints** präsentiert werden. Es gibt verschiedene Erlebnistypen:

   * **Teaser**
     [Teaser-Seiten/-Absätze](#teasers) dienen dazu, bestimmte **Besuchersegmente** zu Inhalten zu leiten, die auf ihre Interessen ausgerichtet sind.

     Teaser-Seiten bieten folgende Möglichkeiten:

      * Präsentieren einer Optionspalette, aus der Besucherinnen und Besucher wählen können
      * Anzeigen von nur einem Teaser-Absatz, der auf dem spezifischen Besuchersegment basiert.  Beispielsweise kann der angezeigte Teaser-Absatz vom Alter der Besucherin bzw. des Besuchers abhängen.

     Bei einer Teaser-Seite handelt es sich in der Regel um eine temporäre Aktion, die für einen bestimmten Zeitraum gültig ist, bis sie durch die nächste Teaser-Seite ersetzt wird.

   * **Newsletter**

     [E-Mail-Nachrichten](#emailmarketing) werden verwendet, um Benutzer einzubinden und sie zum Besuchen der Website anzuregen. Im Allgemeinen haben sie die Form eines Newsletters, der an die **Leads** gesendet wird (die in **Listen** unterteilt sind). **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen. Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

   * **Adobe Target**

     Dies ermöglicht die Integration mit Adobe Target (ehemals Test&amp;Target), das Personen mit Marketing-Expertise für die Konversion ein Website-Optimierungs-Tool mit den erforderlichen Funktionen bietet, um Online-Inhalte und -Angebote für Kundinnen und Kunden relevanter zu machen und so höhere Konversionswerte zu erzielen. Adobe Target bietet eine intuitive Benutzeroberfläche für das Entwerfen und Ausführen von Tests, das Erstellen von Zielgruppensegmenten sowie das Targeting von Inhalten – und das alles in einer einzigen Anwendung.

* **Touchpoints**

  Dies sind die Kontaktpunkte zwischen dem Besucher und Ihrer Kampagne. Die Touchpoints sind mit den von Ihnen erstellten Erlebnissen verbunden.

  Bei einem Teaser ist dies z. B. die Inhaltsseite, auf der sich der Teaser-Absatz befindet, bei einem Newsletter ist es die Mailing-Liste.

* **Leads**

  Die Informationen, die Sie über Ihre Besucher und die Kontaktaufnahme mit ihnen gesammelt haben, bildet die Grundlage für Ihre Leads. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **Listen**

  Leads werden in Listen gruppiert, damit Sie kollektive Aktionen auf sie anwenden können. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen.](/help/sites-administering/campaign.md)

* **Segmente**

  Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Die Analyse nach Faktoren wie Aktivität auf der Website, registrierte Profilinformationen und Aktivität auf anderen Websites hilft Ihnen, Segmente zu definieren. Inhalte können dann entsprechend den jeweiligen Segmenten auf die Anforderungen und Interessen der Besucherinnen und Besucher ausgerichtet werden.

* **MCM**

  Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie auf alle Funktionen zugreifen können, die Sie zum Erstellen und Steuern Ihrer Kampagnen, Marken, Erlebnisse, Touchpoints, Leads, Listen, Segmente und Berichte benötigen.

  Sie können von verschiedenen (als **Kampagnen** gekennzeichneten) Stellen oder z. B. über folgende URL darauf zugreifen:

  `http://localhost:4502/libs/mcm/content/admin.html`
