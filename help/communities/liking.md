---
title: Verwenden von "Gefällt mir"
seo-title: Verwenden von "Gefällt mir"
description: Hinzufügen und Konfigurieren der Komponente "Gefällt mir"
seo-description: Hinzufügen und Konfigurieren der Komponente "Gefällt mir"
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 6%

---

# Verwenden von &quot;Gefällt mir&quot;-Klicks {#using-liking}

Die Komponente `Liking` ist ein nützliches Tool, mit dem Benutzer eine Meinung zu einem bestimmten Inhaltselement, z. B. zu einem Kommentar in einem Forum, äußern können. Mit der Komponente `Liking` wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von &quot;Link&quot;zu einer Seite {#adding-liking-to-a-page}

Um eine Komponente `Liking` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Liking`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die den Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-liking.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Liking` so angezeigt.

![liking-component](assets/liking-component.png)

## Konfigurieren von Link {#configuring-liking}

Wählen Sie die platzierte Komponente `Liking` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** die Eigenschaften an, die zum Aufzeichnen von &quot;Gefällt mir&quot;-Klicks verwendet werden.

![configure-liking](assets/configure-liking.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**

   (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können ihre Art jederzeit ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Gefällt mir-Grundlagen](essentials-liking.md) für Entwickler.
