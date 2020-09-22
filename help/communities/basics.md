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
source-git-commit: c77a353d43a3a6f33dffecf0b4e7672ed3e2dd3f
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 61%

---


# Grundlagen zu Communities-Komponenten {#communities-components-basics}

## Überblick {#overview}

Im Autorenabschnitt der Dokumentation finden Sie Informationen zum Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus sowie eine Beschreibung der Komponentenkonfigurationen.

Components may be explored using an AEM instance and the interactive [Community Components guide](components-guide.md).

## Auf Communities-Komponenten zugreifen {#accessing-communities-components}

Wenn Sie Seiteninhalte verfassen und die zugrunde liegende Vorlage Änderungen am Design der Seite zulässt, können Komponenten aktiviert werden, die im Komponenten-Browser noch nicht als Teil des Seitendesigns verfügbar sind.

Die verfügbaren Communities-Komponenten sind [hier](author-communities.md#available-communities-components) aufgeführt.

>[!NOTE]
>
>For general authoring information, view the [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).
>
>If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md).


### Designmodus aktivieren {#entering-design-mode}

If a **Communities** component is not found in the components browser (sidekick), it will be necessary to enter `Design Mode` to add other Communities components. Möglicherweise müssen Sie zudem [erforderliche Client-seitige Bibliotheken](#required-clientlibs) (clientlibs) hinzufügen.

For details, see [Configuring Components in Design Mode](../../help/sites-authoring/default-components-designmode.md).

Im Folgenden finden Sie Bilder zur Auswahl einiger Communities-Komponenten und zur Anzeige im Komponenten-Browser:

![component-design](assets/component-design.png)

Die ausgewählten Komponenten werden jetzt im Komponenten-Browser angezeigt:

![component-design1](assets/component-design1.png)

## Erforderliche Clientlibs {#required-clientlibs}

[Client-seitige Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) werden für die ordnungsgemäße Ausführung (JavaScript) und Formatierung (CSS) der Komponenten benötigt.

Wird eine Communities-Komponente einer Seite hinzugefügt und führt dies zur Ausgabe einer Fehlermeldung sowie einem unerwarteten Layoutergebnis, sollte zunächst überprüft werden, ob die für die Communities-Komponente erforderlichen clientlibs hinzugefügt wurden. Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

### Example: Initially placed reviews without client libraries... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... And with client libraries {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tagging {#tagging}

Viele Communities-Funktionen lassen sich so konfigurieren, dass Mitglieder veröffentlichte (gepostete) Inhalte in der Veröffentlichungsumgebung taggen können.

Ist das Tagging von Inhalten freigeschaltet, werden die für Mitglieder in der Veröffentlichungsumgebung verfügbaren Namespaces möglicherweise durch die Konfiguration der Community-Site beschränkt. Informationen hierzu finden Sie in der [Community-Sites-Konsole](sites-console.md#tagging).

Features which allow tagging: [blog](blog-feature.md), [calendar](calendar.md), [file library](file-library.md), [forum](forum.md)

Features which use tags: [catalog](catalog.md), [search](search.md), [social tag cloud](tagcloud.md)

Informationen zum Verfassen:

* [Verwenden von Tags](../../help/sites-authoring/tags.md)

Verwaltungsinformationen:

* Creating tag namespaces (taxonomy): [Administering Tags](../../help/sites-administering/tags.md)
* Community Site configuration: see [TAGGING](sites-console.md#tagging)
* [Tagging benutzergenerierter Inhalte](../../help/sites-authoring/tags.md)
* [Tagging von Aktivierungsressourcen](tag-resources.md)

Entwicklerinformationen:

* [AEM-Tagging-Framework](../../help/sites-developing/framework.md)
* [Tagging-Grundlagen](tag.md)

