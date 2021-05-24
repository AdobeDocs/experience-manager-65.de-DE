---
title: Entwicklung und Seitenvergleich
seo-title: Entwicklung und Seitenvergleich
description: Entwicklung und Seitenvergleich
seo-description: 'null'
uuid: 06f27bc2-f42a-4176-ab94-255e721c6933
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6612f89d-c518-4e5a-8df1-6487cc330a9a
docset: aem65
exl-id: b07134b2-074a-4d52-8d0c-7e7abe51fc3a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 92%

---

# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-developing/pagediff.md#operation-details) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Berechtigungen {#permissions}

Zuvor musste in der klassischen Benutzeroberfläche bei der Entwicklung besonders berücksichtigt werden, um die AEM zu vereinfachen (z. B. die Verwendung der Tag-Bibliothek `cq:text` oder die benutzerdefinierte Integration des `DiffService`-OSGi-Dienstes in Komponenten). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie clientseitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch einige Einschränkungen, die der Entwickler beachten muss.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichs-Service ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.
