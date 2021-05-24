---
title: Kampagnen-Management
seo-title: Kampagnen-Management
description: Das Kampagnenmanagement bietet E-Marketing-Experten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen. Es bietet Ihnen die Möglichkeit, Marketing-Kampagnen für Internet, E-Mail und Mobilgeräte zu erstellen und so Benutzerinteraktionen auszulösen.
seo-description: Das Kampagnenmanagement bietet E-Marketing-Experten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen. Es bietet Ihnen die Möglichkeit, Marketing-Kampagnen für Internet, E-Mail und Mobilgeräte zu erstellen und so Benutzerinteraktionen auszulösen.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: d1741525-a475-4a76-bd16-55318023495e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 92%

---

# Kampagnen-Management{#campaign-management}

Das Kampagnenmanagement bietet E-Marketing-Experten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen.

Es bietet Ihnen die Möglichkeit, Marketing-Kampagnen für Internet, E-Mail und Mobilgeräte zu erstellen und so Benutzerinteraktionen auszulösen. Sie können Inhalte erstellen, Besucher in Segmente einteilen, zielgerichtete Inhalte an bestimmte Benutzerprofile weiterleiten und Kampagnen über mehrere Kanäle verwalten.

In diesem Dokument werden die verschiedenen Elemente beschrieben, aus denen Kampagnen bestehen. Weitere Informationen finden Sie in folgenden Dokumenten:

* [Teaser und Strategien](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [E-Mail-Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Landing Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Adobe Target-Angebote](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Arbeiten mit dem Marketing Campaign Manager](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Grundlegendes zur Segmentierung](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Konzeption einer Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

Das Kampagnenmanagement umfasst verschiedene Elemente:

* **Marken**
In AEM bilden Marken die oberste Ebene und bilden eine Sammlung von 
**Kampagnen**.

* ****
KampagnenEine Kampagne ist eine Kollektion einzelner Kampagnen 
**Erlebnisse**.

* ****
ErlebnisseDer fokussierte Inhalt bildet die verschiedenen Erlebnisse, die dem Besucher unter 
**Touchpoints**. Es gibt verschiedene Erlebnistypen:

   * **Teasers**
      [Teaser-Seiten/-Absätze](#teasers) dienen dazu, bestimmte Besucher-**Segmente** zu Inhalten zu leiten, die auf ihre Interessen ausgerichtet sind.

      Teaser-Seiten bieten folgende Möglichkeiten:

      * Präsentieren einer Optionspalette, aus der der Besucher wählen kann
      * Anzeigen nur eines Teaser-Absatzes basierend auf dem jeweiligen Besuchersegment. Der angezeigte Teaser-Absatz kann beispielsweise vom Alter des Besuchers abhängig sein.

      Bei einer Teaser-Seite handelt es sich in der Regel um eine temporäre Aktion, die für eine bestimmte Zeitdauer gültig ist, bis sie durch die nächste Teaser-Seite ersetzt wird.

   * **Newsletter**

      [E-Mail-](#emailmarketing) Kommunikation wird verwendet, um Benutzer dazu anzuregen, Ihre Website zu besuchen. Im Allgemeinen haben sie die Form eines Newsletters, der an die **Leads** gesendet wird (die im Allgemeinen in **Listen** unterteilt sind). **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.  Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

   * **Adobe Target**

       Dies ermöglicht die Integration in Adobe Target (ehemals Test&amp;Target), das Marketing-Experten für die Konversion ein Website-Optimierungs-Tool mit den erforderlichen Möglichkeiten bietet, um Online-Inhalte und -Angebote für Kunden relevanter zu machen und so höhere Konversionswerte zu erzielen. Adobe Target bietet eine intuitive Benutzeroberfläche für das Entwickeln und Ausführen von Tests, das Erstellen von Zielgruppensegmenten sowie das Targeting von Inhalten – und das alles in einer einzigen Anwendung.


* **Touchpoints**

   Dies sind die Kontaktpunkte zwischen dem Besucher und Ihrer Kampagne. Die Touchpoints sind mit den von Ihnen erstellten Erlebnissen verbunden.

   Bei einem Teaser ist dies z. B. die Inhaltsseite, auf der sich der Teaser-Absatz befindet, bei einem Newsletter ist es die Mailing-Liste.

* **Leads**

   Die Informationen, die Sie über Ihre Besucher und die Kontaktaufnahme mit ihnen gesammelt haben, bildet die Grundlage für Ihre Leads. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

    Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **Listen**

   Leads werden im Allgemeinen in Listen gruppiert, damit Sie kollektive Aktionen auf sie anwenden können. Hinweis: **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

    Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **Segmente**

   Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Durch die Analyse nach Faktoren wie Aktivität auf der Website, registrierte Profilinformationen sowie Aktivität auf anderen Websites können Sie Segmente definieren. Inhalte können dann entsprechend den zutreffenden Segmenten speziell auf die Anforderungen und Interessen des Besuchers abgestimmt werden.

* **MCM**

   Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie auf sämtliche Funktionen zugreifen können, die Sie zum Erstellen und Steuern von Kampagnen, Marken, Erlebnissen, Touchpoints, Leads, Listen, Segmenten und Berichten benötigen.

   Sie können von verschiedenen (als **Kampagnen** gekennzeichneten) Positionen oder z. B. über folgende URL darauf zugreifen:

   `http://localhost:4502/libs/mcm/content/admin.html`
