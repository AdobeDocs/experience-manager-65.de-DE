---
title: Entwicklung und Seitenvergleich
description: Erfahren Sie, wie Sie die Seitenvergleichsfunktion in Adobe Experience Manager entwickeln und nutzen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: b07134b2-074a-4d52-8d0c-7e7abe51fc3a
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 96%
---
# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Die Inhaltserstellung ist ein iterativer Prozess. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Eine Autorin bzw. ein Autor möchte die aktuelle Seite mit einer früheren Version parallel vergleichen können, mit hervorgehobenen Unterschieden.

Der Seitenvergleich ermöglicht es Benutzenden, die aktuelle Seite mit Launches, früheren Versionen usw. zu vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die jemand vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-developing/pagediff.md#operation-details) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Admins, die das Repository beispielsweise in CRXDE Lite anzeigen, sehen diese nacherstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Berechtigungen {#permissions}

Früher in der klassischen Benutzeroberfläche musste bei der Entwicklung besondere Rücksicht genommen werden, um die AEM-Vergleichsfunktion zu unterstützen (z. B. die Verwendung der Tag-Bibliothek `cq:text` oder eine individuelle Integration des OSGi-Dienstes `DiffService` in Komponenten). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie Client-seitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch mehrere Einschränkungen, die von den Entwickelnden berücksichtigt werden müssen.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

  * `html-added`
  * `html-removed`
  * `cq-component-added`
  * `cq-component-removed`
  * `cq-component-moved`
  * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichs-Service ausgeführt wurde. Dies kann Folgendes betreffen:

  * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
  * Single Page Applications
  * JavaScript-basierte Komponenten, die das DOM bei Benutzerinteraktionen manipulieren.

>[!NOTE]
>
>Der Seitenvergleich funktioniert nur für Komponenten mit gültigen cq:editConfig-Knoten.
