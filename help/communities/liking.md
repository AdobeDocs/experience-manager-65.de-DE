---
title: Verwenden von „Gefällt mir“
description: Erfahren Sie, wie Sie die Komponente „Verknüpfung“ hinzufügen und konfigurieren, damit Benutzer eine Meinung zu einem bestimmten Inhalt äußern können, z. B. zu einem Kommentar.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
solution: Experience Manager
feature: Communities
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%
---
# Verwenden von „Gefällt mir“ {#using-liking}

Die `Liking`-Komponente ist ein nützliches Tool, mit dem Benutzende ihre Meinung zu einem bestimmten Inhalt äußern können, z. B. zu einem Kommentar innerhalb eines Forums. Bei der Komponente `Liking` wählen Mitglieder das Herz-Symbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen einer Verknüpfung zu einer Seite {#adding-liking-to-a-page}

Um einer Seite im Autorenmodus eine `Liking` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Liking`

Und ziehen Sie es auf einer Seite, z. B. eine Position relativ zur Funktion, die Benutzern gefällt.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](essentials-liking.md#essentials-for-client-side) enthalten sind, wird die `Liking` Komponente wie folgt angezeigt.

![liking-component](assets/liking-component.png)

## Konfiguration der Verknüpfung {#configuring-liking}

Wählen Sie die platzierte `Liking` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** geben Sie die Eigenschaften an, die zum Aufzeichnen von Likes verwendet werden sollen.

![configure-liking](assets/configure-liking.png)

* **[!UICONTROL Positive Response Label]**

  (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

  (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Tally-Name]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Mitglieder können jederzeit ihr „Gefällt mir“ ändern.

### Anonym {#anonymous}

Anonyme Verknüpfungen werden nicht unterstützt. Besuchende der Website müssen sich registrieren (Mitglied werden) und sich anmelden, um an „Gefällt mir“ teilzunehmen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Liking Essentials](essentials-liking.md) für Entwickler.
