---
title: Grundlagen zu Communities-Komponenten
seo-title: Communities Components Basics
description: Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: eb5ce76a-bf28-4540-bc2d-3b5ecb8286f2
source-git-commit: 4dbbcc41757843d3b2d5a3bbb2656ef587e83d2c
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---

# Grundlagen zu Communities-Komponenten {#communities-components-basics}

## Übersicht {#overview}

Im Abschnitt &quot;Authoring&quot;der Dokumentation werden das Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus für Autoren sowie die Beschreibung von Komponentenkonfigurationen beschrieben.

Komponenten können mithilfe einer AEM-Instanz und der interaktiven [Handbuch zu Community-Komponenten](components-guide.md).

## Zugreifen auf Communities-Komponenten {#accessing-communities-components}

Wenn beim Erstellen von Seiteninhalten die zugrunde liegende Vorlage Änderungen am Design der Seite zulässt, ist es möglich, Komponenten zu aktivieren, die im Komponenten-Browser nicht bereits als Teil des Site-Designs verfügbar sind.

Die verfügbaren Communities-Komponenten werden aufgelistet [here](author-communities.md#available-communities-components).

>[!NOTE]
>
>Allgemeine Informationen zum Authoring finden Sie unter [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md).

### Aktivieren des Designmodus {#entering-design-mode}

Wenn eine **Communities** -Komponente nicht im Komponenten-Browser gefunden werden (Sidekick), muss `Design Mode` , um weitere Communities-Komponenten hinzuzufügen. [Erforderliche clientseitige Bibliotheken](#required-clientlibs) (clientlibs) hinzugefügt werden.

Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](../../help/sites-authoring/default-components-designmode.md).

Im Folgenden finden Sie Bilder zur Auswahl einiger Communities-Komponenten und deren Anzeige im Komponenten-Browser:

![component-design](assets/component-design.png)

Die ausgewählten Komponenten sind jetzt im Komponenten-Browser verfügbar:

![component-design1](assets/component-design1.png)

## Erforderliche Clientlibs {#required-clientlibs}

[Client-seitige Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen und das Ergebnis ein Fehler oder ein unerwartetes Erscheinungsbild ist, sollten Sie als Erstes versuchen, die erforderlichen Clientlibs für die Communities-Komponente hinzuzufügen. Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

### Beispiel: Ursprünglich platzierte Bewertungen ohne Client-Bibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... Und mit Client-Bibliotheken {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tagging {#tagging}

Viele Communities-Funktionen können so konfiguriert werden, dass Mitglieder Inhalte taggen können, die in der Veröffentlichungsumgebung eingegeben (veröffentlicht) wurden.

Wenn Tagging zulässig ist, kann die Konfiguration der Community-Site so eingestellt sein, dass die Namespaces, die Mitgliedern in der Veröffentlichungsumgebung angezeigt werden, beschränkt werden. Siehe [Community-Sites-Konsole](sites-console.md#tagging).

Funktionen, die Tagging ermöglichen: [blog](blog-feature.md), [calendar](calendar.md), [Dateibibliothek](file-library.md), [Forum](forum.md)

Funktionen, die Tags verwenden: [suchen](search.md), [Social Tag Cloud](tagcloud.md)

Für Informationen zur Bearbeitung:

* [Verwenden von Tags](../../help/sites-authoring/tags.md)

Für Verwaltungsinformationen:

* Erstellen von Tag-Namespaces (Taxonomie): [Verwalten von Tags](../../help/sites-administering/tags.md)
* Community-Site-Konfiguration: see [TAGGING](sites-console.md#tagging)
* [Tagging benutzergenerierter Inhalte](../../help/sites-authoring/tags.md)

Entwicklerinformationen:

* [AEM-Tagging-Framework](../../help/sites-developing/framework.md)
* [Tagging-Grundlagen](tag.md)
