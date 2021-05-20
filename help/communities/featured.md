---
title: Funktionen für spezielle Inhalte
seo-title: Funktionen für spezielle Inhalte
description: Mit der Funktion für spezielle Inhalte können angemeldete Site-Besucher Inhalte hervorheben
seo-description: Mit der Funktion für spezielle Inhalte können angemeldete Site-Besucher Inhalte hervorheben
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
exl-id: 76b76e0e-531b-4f80-be70-68532ef81a7f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 8%

---

# Funktion für spezielle Inhalte {#featured-content-feature}

## Einführung {#introduction}

Die Funktion für spezielle Inhalte bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung, in dem Inhalte hervorgehoben werden können für:

* [Blogs](blog-feature.md)
* [Kalender](calendar.md)
* [Foren](forum.md)
* [Ideen](ideation-feature.md)
* [Frage und Antwort](working-with-qna.md)

Sobald Inhalte als vorgestellt gekennzeichnet sind, werden sie in dieser Komponente aufgelistet, die auf bestimmten Landingpages oder in Bereichen platziert werden kann, die die Aufmerksamkeit der Community-Mitglieder leicht erfassen.

Die Funktion zum Feature von Inhalten kann pro Komponente erlaubt oder deaktiviert sein.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen spezieller Inhalte zu einer Community-Site.
* Konfigurationseinstellungen für die Komponente `Featured Content` .

## Hinzufügen von speziellen Inhalten zu einer Seite {#adding-featured-content-to-a-page}

Um eine Komponente `Featured Content` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Featured Content`

und ziehen Sie sie an die gewünschte Stelle auf der Seite, auf der der gewünschte Inhalt erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-featured.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Featured Content` so angezeigt:

![featuredcontent](assets/featuredcontent.png)

## Konfiguration von speziellen Inhalten {#configuring-featured-content}

Wählen Sie die platzierte Komponente `Featured Content` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![featuredcontent1](assets/featuredcontent1.png)

### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Inhalt an, der verwendet werden soll:

* **[!UICONTROL Anzeigename]**

   Der Titel für die Liste der vorgestellten Inhalte. Beispiel: `Featured Questions` oder `Featured Ideas`. Der Standardwert ist `Featured Content` , wenn leer gelassen.

* **[!UICONTROL Position des präsentierten Inhalts]**

   *(Erforderlich)* Navigieren Sie zu der Seite, die den Inhalt enthält, der möglicherweise eine Funktion aufweist. (Die Komponenten dieser Seite müssen so konfiguriert sein, dass &quot;Spezifischer Inhalt zulassen&quot;konfiguriert wird.) Beispiel: `/content/sites/engage/en/forum`.

* **[!UICONTROL Anzeigelimit]**

   Die maximale Anzahl der anzuzeigenden speziellen Inhalte. Der Standardwert ist 5.

## Site-Besuchererlebnis {#site-visitor-experience}

Die Fähigkeit, Inhalte als speziellen Inhalt zu kennzeichnen, erfordert Moderatorberechtigungen.

Wenn ein Moderator veröffentlichte Inhalte anzeigt, hat er Zugriff auf die kontextbezogenen Moderationsflags, die die neue `Feature`-Markierung enthalten.

![site-visitor-experience](assets/site-visitor-experience.png)

Sobald das Modeartions-Flag als Funktion gekennzeichnet ist, wird es zu `Unfeature`.

Die Seite, die die Komponente `Featured Content` enthält, enthält jetzt diesen Beitrag.

![site-visitor-experience1](assets/site-visitor-experience1.png)

`Read More` ist ein Link zum eigentlichen Beitrag.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Empfohlene Inhalte](essentials-featured.md) für Entwickler.

Informationen zum Kennzeichnen von Inhalten mit den Funktionen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).
