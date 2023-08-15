---
title: Kampagnen-Management
description: Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen. Damit können Sie Ihre Marketing-Kampagnen über das Web, die E-Mail und Mobile Services hinweg koordinieren und so Ihre Besucher binden.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: d1741525-a475-4a76-bd16-55318023495e
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 28%

---


# Kampagnen-Management{#campaign-management}

Das Kampagnen-Management bietet E-Marketing-Fachleuten die Möglichkeit, personalisierte Inhalte bereitzustellen und so individuelle Erlebnisse für Besucher zu schaffen.

Damit können Sie Ihre Marketing-Kampagnen über das Web, die E-Mail und Mobile Services hinweg koordinieren und so Ihre Besucher binden. Sie können Inhalte erstellen, Besucher segmentieren, zielgerichtete Inhalte für bestimmte Benutzerprofile pushen und bewerben und Kampagnen über mehrere Kanäle hinweg verwalten.

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
In Adobe Experience Manager (AEM) bilden Marken die oberste Ebene und bilden eine Sammlung von **Kampagnen**.

* **Kampagnen**
Eine Kampagne ist eine Kollektion einzelner **Erlebnisse**.

* **Erlebnisse**
Der fokussierte Inhalt bildet die verschiedenen Erlebnisse, die dem Besucher unter **Touchpoints**. Es stehen verschiedene Erlebnistypen zur Verfügung:

   * **Teasers**
     [Teaser-Seiten/-Absätze](#teasers) dienen dazu, bestimmte **Besuchersegmente** zu Inhalten zu leiten, die auf ihre Interessen ausgerichtet sind.

     Teaser-Seiten können:

      * eine Reihe von Optionen zur Auswahl für den Besucher anbieten
      * nur einen Teaser-Absatz anzeigen, der auf dem spezifischen Besuchersegment basiert. Beispielsweise kann der angezeigte Teaser-Absatz vom Alter des Besuchers abhängen.

     In der Regel ist eine Teaser-Seite eine temporäre Aktion, die für einen bestimmten Zeitraum dauert, bis sie durch die nächste Teaser-Seite ersetzt wird.

   * **Newsletter**

     [E-Mail-Nachrichten](#emailmarketing) werden verwendet, um Benutzer einzubinden und sie zum Besuchen der Website anzuregen. Diese werden normalerweise in Form eines Newsletters versendet, der an Ihre **Leads** (die in **Listen**). **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen. Die Empfehlung [Verwenden Sie Adobe Campaign und die Integration, um AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

     Dies ermöglicht die Integration in Adobe Target (ehemals Test&amp;Target), das Marketing-Experten ein Tool zur Konversionswebsite-Optimierung mit den erforderlichen Funktionen bietet, um ihre Online-Inhalte und -Angebote für ihre Kunden relevanter zu machen und so eine höhere Konversionsrate zu erzielen. Adobe Target bietet eine intuitive Benutzeroberfläche für die Konzeption und Ausführung von Tests, die Erstellung von Zielgruppensegmenten und das Targeting von Inhalten in einer einzigen Anwendung.

* **Touchpoints**

  Dies sind die Kontaktpunkte zwischen dem Besucher und Ihrer Kampagne. Die Touchpoints sind mit den von Ihnen erstellten Erlebnissen verknüpft.

  Bei Teasern ist es beispielsweise die Inhaltsseite, auf der sich der Teaser-Absatz befindet, bei einem Newsletter ist es die Mailingliste.

* **Leads**

  Die Informationen, die Sie über Ihre Besucher und die Kontaktaufnahme mit ihnen gesammelt haben, bildet die Grundlage für Ihre Leads. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Die Empfehlung [Verwenden Sie Adobe Campaign und die Integration, um AEM](/help/sites-administering/campaign.md).

* **Listen**

  Leads werden in Listen gruppiert, sodass Sie kollektive Maßnahmen ergreifen können. Hinweis: **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.

  Die Empfehlung [Verwenden Sie Adobe Campaign und die Integration, um AEM.](/help/sites-administering/campaign.md)

* **Segmente**

  Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Die Analyse nach Faktoren wie Aktivität auf der Website, registrierte Profilinformationen und Aktivität auf anderen Websites hilft Ihnen bei der Definition von Segmenten. Inhalte können dann entsprechend den jeweiligen Segmenten auf die Anforderungen und Interessen des Besuchers ausgerichtet werden.

* **MCM**

  Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie auf alle Funktionen zugreifen können, die Sie zum Erstellen und Steuern Ihrer Kampagnen, Marken, Erlebnisse, Touchpoints, Leads, Listen, Segmente und Berichte benötigen.

  Er kann von verschiedenen Orten aus aufgerufen werden (mit der Bezeichnung **Kampagnen**) oder mit der URL:

  `http://localhost:4502/libs/mcm/content/admin.html`
