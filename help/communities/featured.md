---
title: Funktionen für spezielle Inhalte
seo-title: Funktionen für spezielle Inhalte
description: Mit der Funktion für spezielle Inhalte können Besucher, die sich angemeldet haben, Inhalte hervorheben
seo-description: Mit der Funktion für spezielle Inhalte können Besucher, die sich angemeldet haben, Inhalte hervorheben
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
translation-type: tm+mt
source-git-commit: a8b1ad0fcd2ca9c7fe3117dd8bd161da82d13e8a
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 8%

---


# Funktion für spezielle Inhalte {#featured-content-feature}

## Einführung {#introduction}

Die Funktion für speziellen Inhalt bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Umgebung zum Veröffentlichen, in dem Sie Inhalte hervorheben können für:

* [Blogs](blog-feature.md)
* [Kalender](calendar.md)
* [Foren](forum.md)
* [Ideen](ideation-feature.md)
* [Frage und Antwort](working-with-qna.md)

Sobald der Inhalt als &quot;hervorgehoben&quot;gekennzeichnet ist, wird er in dieser Komponente aufgelistet, die in bestimmten Landingpages oder Bereichen platziert werden kann, die die Aufmerksamkeit der Community-Mitglieder leicht erfassen.

Die Funktion zum Feature von Inhalten kann pro Komponente zugelassen oder deaktiviert werden.

Dieser Abschnitt der Dokumentation beschreibt:

* Hinzufügen von speziellen Inhalten zu einer Community-Site.
* Konfigurationseinstellungen für die Komponente `Featured Content`.

## Hinzufügen von speziellen Inhalten zu einer Seite {#adding-featured-content-to-a-page}

Um einer Seite im Autorenmodus eine `Featured Content`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach

* `Communities / Featured Content`

und ziehen Sie es auf eine Seite, auf der der spezielle Inhalt angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-featured.md#essentials-for-client-side) einbezogen werden, wird die `Featured Content`-Komponente wie folgt angezeigt:

![featuredcontent](assets/featuredcontent.png)

## Konfigurieren von speziellen Inhalten {#configuring-featured-content}

Wählen Sie die platzierte Komponente `Featured Content` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![featuredcontent1](assets/featuredcontent1.png)

### Registerkarte „Settings“{#settings-tab}

Identifizieren Sie unter der Registerkarte **[!UICONTROL Einstellungen]** den Inhalt, der funktionsfähig sein soll:

* **[!UICONTROL Anzeigename]**

   Der Titel für die Liste von speziellen Inhalten. Beispiel: `Featured Questions` oder `Featured Ideas`. Die Standardeinstellung ist `Featured Content`, wenn leer gelassen.

* **[!UICONTROL Position des präsentierten Inhalts]**

   *(Erforderlich)* Navigieren Sie zu der Seite, die den Inhalt enthält, der möglicherweise Funktion ist (Komponenten dieser Seite müssen so konfiguriert sein, dass spezielle Inhalte zulässig sind). Beispiel: `/content/sites/engage/en/forum`.

* **[!UICONTROL Anzeigelimit]**

   Die maximale Anzahl der anzuzeigenden speziellen Inhalte. Der Standardwert ist 5.

## Site-Besuchererlebnis {#site-visitor-experience}

Die Möglichkeit, Inhalte als speziellen Inhalt zu kennzeichnen, erfordert Moderatorenrechte.

Wenn ein Moderator gepostete Inhalte Ansicht, hat er Zugriff auf die kontextbezogenen Moderations-Flags, die das neue `Feature`-Flag enthalten.

![site-Besucher-experience](assets/site-visitor-experience.png)

Wenn das Modeartions-Flag als Funktion markiert wurde, wird es zu `Unfeature`.

Die Seite, die die Komponente `Featured Content` enthält, enthält jetzt diesen Beitrag.

![site-Besucher-experience1](assets/site-visitor-experience1.png)

`Read More` ist ein Link zum eigentlichen Beitrag.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Vorgestellte Inhalte](essentials-featured.md) für Entwickler.

Informationen zum Anzeigen von Inhalten mit den entsprechenden Funktionen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).
