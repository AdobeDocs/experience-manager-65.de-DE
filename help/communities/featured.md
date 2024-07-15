---
title: Funktionen für spezielle Inhalte
description: Mit der Funktion für spezielle Inhalte können angemeldete Site-Besucher Inhalte hervorheben
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

# Funktionen für spezielle Inhalte {#featured-content-feature}

## Einführung {#introduction}

Die Funktion für spezielle Inhalte bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung, in dem Inhalte hervorgehoben werden können für:

* [Blogs](blog-feature.md)
* [Kalender](calendar.md)
* [Foren](forum.md)
* [Ideen](ideation-feature.md)
* [Fragen und Antworten](working-with-qna.md)

Sobald Inhalte als vorgestellt gekennzeichnet sind, werden sie in dieser Komponente aufgelistet, die in bestimmten Landingpages oder Bereichen platziert werden kann, die die Aufmerksamkeit der Community-Mitglieder leicht erfassen.

Die Funktion zum Feature von Inhalten kann pro Komponente erlaubt oder untersagt sein.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen spezieller Inhalte zu einer Community-Site.
* Konfigurationseinstellungen für die Komponente `Featured Content` .

## Hinzufügen von speziellen Inhalten zu einer Seite {#adding-featured-content-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Featured Content` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Featured Content`

Ziehen Sie ihn an die gewünschte Stelle auf einer Seite, auf der der spezielle Inhalt erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-featured.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Featured Content` wie folgt angezeigt:

![featuredcontent](assets/featuredcontent.png)

## Konfiguration von speziellen Inhalten {#configuring-featured-content}

Wählen Sie die platzierte Komponente `Featured Content` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![featuredcontent1](assets/featuredcontent1.png)

### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Inhalt an, der für die Funktion verwendet werden soll:

* **[!UICONTROL Anzeigename]**

  Der Titel für die Liste der vorgestellten Inhalte. Beispiel: `Featured Questions` oder `Featured Ideas`. Der Standardwert ist &quot;`Featured Content`&quot;, wenn leer gelassen.

* **[!UICONTROL Position des speziellen Inhalts]**

  *(Erforderlich)* Navigieren Sie zu der Seite, die den Inhalt enthält, der möglicherweise angezeigt wird. (Die Komponenten dieser Seite müssen so konfiguriert sein, dass &quot;Vorgestellter Inhalt zulassen&quot;konfiguriert wird.) Zum Beispiel: `/content/sites/engage/en/forum`.

* **[!UICONTROL Anzeigelimit]**

  Die maximale Anzahl der anzuzeigenden speziellen Inhalte. Der Standardwert lautet 5.

## Site-Besuchererlebnis {#site-visitor-experience}

Die Fähigkeit, Inhalte als speziellen Inhalt zu kennzeichnen, erfordert Moderatorberechtigungen.

Wenn ein Moderator veröffentlichte Inhalte anzeigt, hat er Zugriff auf die kontextbezogenen Moderationsflags, die das neue `Feature` -Flag enthalten.

![site-visitor-experience](assets/site-visitor-experience.png)

Nachdem es als Funktion gekennzeichnet wurde, wird das Moderationsflag zu `Unfeature`.

Die Seite mit der Komponente `Featured Content` enthält jetzt diesen Beitrag.

![site-visitor-experience1](assets/site-visitor-experience1.png)

Die `Read More` verlinkt zum eigentlichen Beitrag.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Vorgestellte Inhalte](essentials-featured.md) .

Informationen zum Kennzeichnen von Inhalten mit den Funktionen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).
