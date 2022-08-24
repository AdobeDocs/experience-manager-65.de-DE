---
title: Verwenden einer Abstimmung
seo-title: Using Voting
description: Hinzufügen der Komponente "Abstimmung"zu einer Seite
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: aa90bf1b-6053-4949-b061-232d72b80682
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 25%

---

# Verwenden einer Abstimmung {#using-voting}

Die `Voting` -Komponente ist ein nützliches Tool, mit dem Community-Mitglieder einen bestimmten Inhalt bewerten können, z. B. eine Antwort innerhalb einer QnA-Komponente. Mit dem `Voting` -Komponente, wählen die Mitglieder Pfeile nach oben oder unten aus, um ihre Meinung zu äußern.

## Hinzufügen einer Abstimmung zu einer Seite {#adding-voting-to-a-page}

So fügen Sie eine `Voting` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Voting` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an eine Position relativ zur Funktion, über die Benutzer abstimmen können.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-voting.md#essentials-for-client-side) eingeschlossen sind, wird die `Voting` wird angezeigt.

![stimmberechtigte Komponente](assets/voting-component.png)

## Konfigurieren einer Abstimmung {#configuring-voting}

Wählen Sie die platzierte `Voting` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte die Eigenschaften für die Aufzeichnung von Abstimmungen angeben.

![Abstimmungsbezeichnung](assets/voting-label.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

   (*Erforderlich*) Der interne Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

   (*Erforderlich*) Der interne Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**

   (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Mitglieder dürfen nur einmal abstimmen, können ihre Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Eine anonyme Abstimmung wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um selbst abstimmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Abstimmungsgrundlagen](essentials-voting.md) für Entwickler.
