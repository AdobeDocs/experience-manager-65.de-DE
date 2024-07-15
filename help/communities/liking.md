---
title: Verwenden von "Gefällt mir"
description: Erfahren Sie, wie Sie die Komponente "Link"hinzufügen und konfigurieren, damit Benutzer eine Meinung zu einem bestimmten Inhaltselement, z. B. zu einem Kommentar, äußern können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# Verwenden von &quot;Gefällt mir&quot; {#using-liking}

Die Komponente `Liking` ist ein nützliches Tool, mit dem Benutzer zu einem bestimmten Inhalt Stellung nehmen können, z. B. zu einem Kommentar in einem Forum. Bei der Komponente `Liking` wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von Links zu Seiten {#adding-liking-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Liking` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Liking`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position in Bezug auf die Funktion, die den Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [ erforderlichen clientseitigen Bibliotheken](essentials-liking.md#essentials-for-client-side) enthalten sind, wird die Komponente `Liking` so angezeigt.

![liking-component](assets/liking-component.png)

## Konfigurieren der Verknüpfung {#configuring-liking}

Wählen Sie die platzierte Komponente `Liking` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** die Eigenschaften an, die zum Aufzeichnen von &quot;Gefällt mir&quot;-Klicks verwendet werden.

![configure-liking](assets/configure-liking.png)

* **[!UICONTROL Bezeichnung der positiven Antwort]**

  (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Bezeichnung der negativen Antwort]**

  (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Tally Name]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können jederzeit ihren Geschmack ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Gefällt mir-Grundlagen](essentials-liking.md) .
