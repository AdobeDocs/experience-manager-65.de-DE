---
title: Verwenden von "Gefällt mir"
description: Erfahren Sie, wie Sie die Komponente "Link"hinzufügen und konfigurieren, damit Benutzer eine Meinung zu einem bestimmten Inhaltselement, z. B. zu einem Kommentar, äußern können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
source-git-commit: b8887b4a6f757352e9dbfdf074c10e9ccd6dbd4f
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---

# Verwenden von &quot;Gefällt mir&quot; {#using-liking}

Die `Liking` -Komponente ist ein nützliches Tool, mit dem Benutzer zu einem bestimmten Inhalt Stellung nehmen können, z. B. zu einem Kommentar in einem Forum. Mit dem `Liking` -Komponente verwenden, wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von Links zu Seiten {#adding-liking-to-a-page}

So fügen Sie eine `Liking` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Liking`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position in Bezug auf die Funktion, die den Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](essentials-liking.md#essentials-for-client-side) eingeschlossen sind, wird die `Liking` -Komponente angezeigt.

![liking-component](assets/liking-component.png)

## Konfigurieren der Verknüpfung {#configuring-liking}

Auswählen der platzierten `Liking` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte die Eigenschaften angeben, die zum Aufzeichnen von &quot;Gefällt mir&quot;verwendet werden.

![configure-liking](assets/configure-liking.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

  (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

  (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können jederzeit ihren Geschmack ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Gefällt mir-Grundlagen](essentials-liking.md) -Seite für Entwickler.
