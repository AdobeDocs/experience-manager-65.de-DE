---
title: Verwenden einer Abstimmung
seo-title: Verwenden einer Abstimmung
description: Hinzufügen der Komponente "Abstimmung"zu einer Seite
seo-description: Hinzufügen der Komponente "Abstimmung"zu einer Seite
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 25%

---


# Verwenden einer Abstimmung {#using-voting}

Die Komponente `Voting` ist ein nützliches Tool, mit dem Community-Mitglieder einen bestimmten Inhalt bewerten können, z. B. eine Antwort innerhalb einer QnA-Komponente. Bei der Komponente `Voting` wählen die Mitglieder Pfeilschaltflächen nach oben oder unten aus, um ihre Meinung anzugeben.

## Hinzufügen einer Abstimmung zu einer Seite {#adding-voting-to-a-page}

Um einer Seite im Autorenmodus eine `Voting`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach `Communities / Voting` und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zur Funktion, über die Benutzer abstimmen können.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-voting.md#essentials-for-client-side) einbezogen werden, wird die `Voting`-Komponente so angezeigt.

![stimmberechtigte Komponente](assets/voting-component.png)

## Konfigurieren einer Abstimmung {#configuring-voting}

Wählen Sie die platzierte Komponente `Voting` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Bezeichnungen]** die Eigenschaften für die Aufzeichnung von Abstimmungen an.

![wahlbeschriftung](assets/voting-label.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

   (*Erforderlich*) Der interne Eigenschaftenname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

   (*Erforderlich*) Der interne Eigenschaftenname für eine negative Antwort.

* **[!UICONTROL Zählername]**

   (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer stimmberechtigten Komponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Mitglieder dürfen nur einmal abstimmen, können ihre Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Eine anonyme Abstimmung wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um selbst abstimmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Essentials](essentials-voting.md) für Entwickler.
