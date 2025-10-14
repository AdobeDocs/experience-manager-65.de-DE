---
title: Funktion für vorgestellte Inhalte
description: Mit der Funktion „Vorgestellte Inhalte“ können angemeldete Site-Besucher Inhalte markieren
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 76b76e0e-531b-4f80-be70-68532ef81a7f
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 5%

---

# Funktion für vorgestellte Inhalte {#featured-content-feature}

## Einführung {#introduction}

Die Funktion für vorgestellte Inhalte bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung, in dem Inhalte für folgende Zwecke hervorgehoben werden:

* [Blogs](blog-feature.md)
* [Kalender](calendar.md)
* [Foren](forum.md)
* [Ideen](ideation-feature.md)
* [Fragen und Antworten](working-with-qna.md)

Sobald Inhalte als „Gezeigt“ gekennzeichnet sind, werden sie in dieser Komponente aufgelistet, die auf bestimmten Landingpages oder in Bereichen platziert werden kann, die leicht die Aufmerksamkeit von Community-Mitgliedern erregen.

Die Funktion zum Anzeigen von Inhalten kann pro Komponente zulässig oder unzulässig sein.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen von vorgestellten Inhalten zu einer Community-Site.
* Konfigurationseinstellungen für die `Featured Content`.

## Hinzufügen von vorgestellten Inhalten zu einer Seite {#adding-featured-content-to-a-page}

Um einer Seite im Autorenmodus eine `Featured Content` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Featured Content`

und ziehen Sie sie auf eine Seite, auf der der angezeigte Inhalt angezeigt werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](essentials-featured.md#essentials-for-client-side) enthalten sind, wird die `Featured Content` Komponente wie folgt angezeigt:

![featuresContent](assets/featuredcontent.png)

## Konfigurieren von vorgestellten Inhalten {#configuring-featured-content}

Wählen Sie die platzierte `Featured Content` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

![featureContent1](assets/featuredcontent1.png)

### Registerkarte „Einstellungen“ {#settings-tab}

Identifizieren Sie auf **[!UICONTROL Registerkarte]** Einstellungen“ den zu verwendenden Inhalt:

* **[!UICONTROL Anzeigename]**

  Der Titel für die Liste der vorgestellten Inhalte. Beispiel: `Featured Questions` oder `Featured Ideas`. Die Standardeinstellung ist `Featured Content`, wenn sie leer gelassen wird.

* **[!UICONTROL Speicherort des angezeigten Inhalts]**

  *(Erforderlich)* Navigieren Sie zur Seite mit den Inhalten, die angezeigt werden können (Komponenten dieser Seite müssen so konfiguriert sein, dass sie vorgestellte Inhalte zulassen). Zum Beispiel: `/content/sites/engage/en/forum`.

* **[!UICONTROL Anzeigegrenze]**

  Die maximale Anzahl der anzuzeigenden angezeigten Inhalte. Der Standardwert lautet 5.

## Site-Besuchererlebnis {#site-visitor-experience}

Die Möglichkeit, Inhalte als vorgestellte Inhalte zu kennzeichnen, erfordert Moderatorrechte.

Wenn ein Moderator gepostete Inhalte anzeigt, hat er Zugriff auf die kontextbezogenen Moderationsflags, die das neue `Feature`-Flag enthalten.

![site-visitor-experience](assets/site-visitor-experience.png)

Nachdem es als Funktion gekennzeichnet wurde, wird das Moderations-Flag `Unfeature`.

Die Seite, die die `Featured Content`-Komponente enthält, enthält jetzt diesen Beitrag.

![site-visitor-experience1](assets/site-visitor-experience1.png)

Der `Read More` verweist auf den tatsächlichen Beitrag.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Vorgestellte Inhalte](essentials-featured.md) für Entwickler.

Informationen zum Kennzeichnen von Inhalten als vorgestellt finden [&#x200B; unter „Moderieren benutzergenerierter Inhalte](moderate-ugc.md).
