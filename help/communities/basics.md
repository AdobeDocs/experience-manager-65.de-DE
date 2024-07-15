---
title: Grundlagen zu Communities-Komponenten
description: Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: eb5ce76a-bf28-4540-bc2d-3b5ecb8286f2
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 1%

---

# Grundlagen zu Communities-Komponenten {#communities-components-basics}

## Überblick {#overview}

Im Abschnitt &quot;Authoring&quot;der Dokumentation wird beschrieben, wie Sie im Bearbeitungsmodus für Autoren Communities-Funktionen zu AEM Sites hinzufügen und Komponentenkonfigurationen beschreiben.

Komponenten können mithilfe einer AEM-Instanz und des interaktiven Leitfadens [Community-Komponenten](components-guide.md) untersucht werden.

## Zugreifen auf Communities-Komponenten {#accessing-communities-components}

Wenn beim Erstellen von Seiteninhalten die zugrunde liegende Vorlage Änderungen am Design der Seite zulässt, ist es möglich, Komponenten zu aktivieren, die im Komponenten-Browser nicht bereits als Teil des Site-Designs verfügbar sind.

Die verfügbaren Communities-Komponenten werden [hier](author-communities.md#available-communities-components) aufgelistet.

>[!NOTE]
>
>Allgemeine Informationen zum Authoring finden Sie in der [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zur [grundlegenden Handhabung](../../help/sites-authoring/basic-handling.md).

### Aufrufen des Designmodus {#entering-design-mode}

Wenn keine **Communities** -Komponente im Komponenten-Browser (Sidekick) gefunden wird, müssen Sie `Design Mode` eingeben, um andere Communities-Komponenten hinzuzufügen. [Erforderliche clientseitige Bibliotheken](#required-clientlibs) (clientlibs) müssen möglicherweise ebenfalls hinzugefügt werden.

Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](../../help/sites-authoring/default-components-designmode.md).

Im Folgenden finden Sie Bilder zur Auswahl einiger Communities-Komponenten und deren Anzeige im Komponenten-Browser:

![component-design](assets/component-design.png)

Die ausgewählten Komponenten sind jetzt im Komponenten-Browser verfügbar:

![component-design1](assets/component-design1.png)

## Erforderliche Clientlibs {#required-clientlibs}

[Client-seitige Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn Sie einer Seite eine Communities-Komponente hinzufügen und das Ergebnis ein Fehler oder ein unerwartetes Erscheinungsbild ist, sollten Sie zunächst die erforderlichen Clientlibs für die Communities-Komponente hinzufügen. Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

### Beispiel: Ursprünglich platzierte Bewertungen ohne Client-Bibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... Und mit Client-Bibliotheken {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tagging {#tagging}

Viele Communities-Funktionen können so konfiguriert werden, dass Mitglieder Inhalte taggen können, die in der Veröffentlichungsumgebung eingegeben (veröffentlicht) wurden.

Wenn Tagging zulässig ist, kann die Konfiguration der Community-Site so festgelegt sein, dass die Namespaces, die Mitgliedern in der Veröffentlichungsumgebung angezeigt werden, beschränkt werden. Siehe [Community-Sites-Konsole](sites-console.md#tagging).

Funktionen, die Tagging ermöglichen: [blog](blog-feature.md), [calendar](calendar.md), [file library](file-library.md), [forum](forum.md)

Funktionen, die Tags verwenden: [search](search.md), [social tag cloud](tagcloud.md)

Für Informationen zur Bearbeitung:

* [Verwenden von Tags](../../help/sites-authoring/tags.md)

Für Verwaltungsinformationen:

* Erstellen von Tag-Namespaces (Taxonomie): [Verwalten von Tags](../../help/sites-administering/tags.md)
* Community-Site-Konfiguration: siehe [TAGGING](sites-console.md#tagging)
* [Tagging benutzergenerierter Inhalte](../../help/sites-authoring/tags.md)

Für Entwicklerinformationen:

* [AEM-Tagging-Framework](../../help/sites-developing/framework.md)
* [Tagging-Grundlagen](tag.md)
