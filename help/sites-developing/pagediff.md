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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 70%

---

# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Die Inhaltserstellung ist ein iterativer Prozess. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Ein Autor möchte die aktuelle Seite mit einer vorherigen Version nebeneinander vergleichen können, wobei die Unterschiede hervorgehoben werden.

Der Seitenvergleich ermöglicht es Benutzenden, die aktuelle Seite mit Launches, früheren Versionen usw. zu vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleich von Seitenversionen wird die vorherige Version, die der Benutzer vergleichen möchte, durch AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-developing/pagediff.md#operation-details) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository beispielsweise im CRXDE Lite anzeigen, sehen diese neu erstellten Versionen jedoch innerhalb der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Berechtigungen {#permissions}

Früher in der klassischen Benutzeroberfläche musste bei der Entwicklung besondere Rücksicht genommen werden, um die AEM-Vergleichsfunktion zu unterstützen (z. B. die Verwendung der Tag-Bibliothek `cq:text` oder eine individuelle Integration des OSGi-Dienstes `DiffService` in Komponenten). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie Client-seitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch einige Einschränkungen, die vom Entwickler berücksichtigt werden müssen.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichs-Service ausgeführt wurde. Dies kann sich auf

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die das DOM bei Benutzerinteraktionen manipulieren.

>[!NOTE]
>
>Der Seitenvergleich funktioniert nur für Komponenten mit gültigen cq:editConfig -Knoten.
