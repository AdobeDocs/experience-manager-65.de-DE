---
title: Funktionen für spezielle Inhalte
description: Mit der Funktion für spezielle Inhalte können angemeldete Site-Besucher Inhalte hervorheben
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 76b76e0e-531b-4f80-be70-68532ef81a7f
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 6%

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
* Konfigurationseinstellungen für `Featured Content` -Komponente.

## Hinzufügen von speziellen Inhalten zu einer Seite {#adding-featured-content-to-a-page}

So fügen Sie eine `Featured Content` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Featured Content`

Ziehen Sie ihn an die gewünschte Stelle auf einer Seite, auf der der spezielle Inhalt erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](essentials-featured.md#essentials-for-client-side) eingeschlossen sind, wird die `Featured Content` -Komponente angezeigt:

![featuredcontent](assets/featuredcontent.png)

## Konfiguration von speziellen Inhalten {#configuring-featured-content}

Auswählen der platzierten `Featured Content` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

![featuredcontent1](assets/featuredcontent1.png)

### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** -Tab, um den Inhalt für die Funktion zu identifizieren:

* **[!UICONTROL Anzeigename]**

  Der Titel für die Liste der vorgestellten Inhalte. Beispiel: `Featured Questions` oder `Featured Ideas`. Der Standardwert ist `Featured Content` , wenn leer gelassen.

* **[!UICONTROL Position des präsentierten Inhalts]**

  *(Erforderlich)* Navigieren Sie zu der Seite, die den Inhalt enthält, der möglicherweise angezeigt wird (die Komponenten dieser Seite müssen so konfiguriert sein, dass &quot;Vorgestellter Inhalt zulassen&quot;konfiguriert werden). Zum Beispiel: `/content/sites/engage/en/forum`.

* **[!UICONTROL Anzeigelimit]**

  Die maximale Anzahl der anzuzeigenden speziellen Inhalte. Der Standardwert lautet 5.

## Site-Besuchererlebnis {#site-visitor-experience}

Die Fähigkeit, Inhalte als speziellen Inhalt zu kennzeichnen, erfordert Moderatorberechtigungen.

Wenn ein Moderator veröffentlichte Inhalte anzeigt, hat er Zugriff auf die kontextbezogenen Moderationsflags, die die neuen `Feature` Markierung.

![site-visitor-experience](assets/site-visitor-experience.png)

Nachdem es als Funktion gekennzeichnet wurde, wird das Moderations-Flag `Unfeature`.

Die Seite, die die `Featured Content` -Komponente, enthält jetzt diesen Beitrag.

![site-visitor-experience1](assets/site-visitor-experience1.png)

Die `Read More` Links zum tatsächlichen Beitrag.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Vorgestellte Inhalte](essentials-featured.md) -Seite für Entwickler.

Informationen zum Kennzeichnen von Inhalten als vorgestellt finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).
