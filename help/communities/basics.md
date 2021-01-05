---
title: Grundlagen zu Communities-Komponenten
seo-title: Grundlagen zu Communities-Komponenten
description: Funktionen von Communities AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
seo-description: Funktionen von Communities AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 61%

---


# Grundlagen zu Communities-Komponenten {#communities-components-basics}

## Überblick {#overview}

Im Autorenabschnitt der Dokumentation finden Sie Informationen zum Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus sowie eine Beschreibung der Komponentenkonfigurationen.

Komponenten können mithilfe einer AEM Instanz und des interaktiven [Community Components guide](components-guide.md)-Handbuchs untersucht werden.

## Auf Communities-Komponenten zugreifen {#accessing-communities-components}

Wenn Sie Seiteninhalte verfassen und die zugrunde liegende Vorlage Änderungen am Design der Seite zulässt, können Komponenten aktiviert werden, die im Komponenten-Browser noch nicht als Teil des Seitendesigns verfügbar sind.

Die verfügbaren Communities-Komponenten sind [hier](author-communities.md#available-communities-components) aufgeführt.

>[!NOTE]
>
>Ansicht der [Quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md) für allgemeine Authoring-Informationen.
>
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [Basisbehandlung](../../help/sites-authoring/basic-handling.md).

### Designmodus aktivieren {#entering-design-mode}

Wenn keine Komponente **Communities** im Komponenten-Browser (Sidekick) gefunden wird, müssen Sie `Design Mode` eingeben, um weitere Communities-Komponenten hinzuzufügen. Möglicherweise müssen Sie zudem [erforderliche Client-seitige Bibliotheken](#required-clientlibs) (clientlibs) hinzufügen.

Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](../../help/sites-authoring/default-components-designmode.md).

Im Folgenden finden Sie Bilder zur Auswahl einiger Communities-Komponenten und zur Anzeige im Komponenten-Browser:

![component-design](assets/component-design.png)

Die ausgewählten Komponenten werden jetzt im Komponenten-Browser angezeigt:

![component-design1](assets/component-design1.png)

## Erforderliche Clientlibs {#required-clientlibs}

[Client-seitige Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) werden für die ordnungsgemäße Ausführung (JavaScript) und Formatierung (CSS) der Komponenten benötigt.

Wird eine Communities-Komponente einer Seite hinzugefügt und führt dies zur Ausgabe einer Fehlermeldung sowie einem unerwarteten Layoutergebnis, sollte zunächst überprüft werden, ob die für die Communities-Komponente erforderlichen clientlibs hinzugefügt wurden. Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

### Beispiel: Ursprünglich platzierte Reviews ohne Client-Bibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... Und mit Client-Bibliotheken {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tagging {#tagging}

Viele Communities-Funktionen lassen sich so konfigurieren, dass Mitglieder veröffentlichte (gepostete) Inhalte in der Veröffentlichungsumgebung taggen können.

Ist das Tagging von Inhalten freigeschaltet, werden die für Mitglieder in der Veröffentlichungsumgebung verfügbaren Namespaces möglicherweise durch die Konfiguration der Community-Site beschränkt. Informationen hierzu finden Sie in der [Community-Sites-Konsole](sites-console.md#tagging).

Funktionen, die Tags ermöglichen: [Blog](blog-feature.md), [Kalender](calendar.md), [Dateibibliothek](file-library.md), [Forum](forum.md)

Funktionen, die Tags verwenden: [Katalog](catalog.md), [Suche](search.md), [Social Tag-Cloud](tagcloud.md)

Informationen zum Verfassen:

* [Verwenden von Tags](../../help/sites-authoring/tags.md)

Verwaltungsinformationen:

* Erstellen von Tag-Namensräumen (taxonomy): [Verwalten von Tags](../../help/sites-administering/tags.md)
* Community-Site-Konfiguration: siehe [TAGGING](sites-console.md#tagging)
* [Tagging benutzergenerierter Inhalte](../../help/sites-authoring/tags.md)
* [Tagging von Aktivierungsressourcen](tag-resources.md)

Entwicklerinformationen:

* [AEM-Tagging-Framework](../../help/sites-developing/framework.md)
* [Tagging-Grundlagen](tag.md)

