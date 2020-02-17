---
title: Entwicklung und Seitenvergleich
seo-title: Entwicklung und Seitenvergleich
description: 'null'
seo-description: 'null'
uuid: 06f27bc2-f42a-4176-ab94-255e721c6933
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6612f89d-c518-4e5a-8df1-6487cc330a9a
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Vorgangsdetails {#operation-details}

Beim Vergleich von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Unterschied zu erleichtern. Dies ist erforderlich, damit der Inhalt [für einen Vergleich](/help/sites-developing/pagediff.md#operation-details)nebeneinander gerendert werden kann.

Dieser Erholungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert kein Eingreifen. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Struktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Eine Bereinigungsaufgabe wird automatisch ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Berechtigungen {#permissions}

Previously, in Classic UI, special development consideration had to be made to facilitate AEM diffing (such as using `cq:text` tag lib, or custom integrating the `DiffService` OSGi service into components). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie clientseitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch einige Einschränkungen, die der Entwickler beachten muss.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich clientseitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der clientseitige Vergleichsdienst ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Einzelseiten-Webanwendungen
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.
