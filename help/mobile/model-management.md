---
title: Modellübersicht
seo-title: Modellübersicht
description: 'null'
seo-description: 'null'
uuid: e09dac52-9515-43f7-9d3b-6637e2283d59
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: c8281f98-9811-42f7-9a31-f82dd0f09319
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Modellübersicht{#models-overview}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Modellverwaltung umfasst die Erstellung und Verwaltung von Modellen zum Zweck der Verknüpfung mit Datenobjekten. Jedes Modell enthält alle Eigenschaften und Felddefinitionen, die zur Erleichterung der Erstellung und Wiedergabe von Objekten erforderlich sind.

Die Modellverwaltung umfasst die Erstellung von **Modellen**, **Entitäten** und **Räumen**. Das folgende Diagramm zeigt die Beziehung zwischen dem AEM-Inhalt und den Modellen.

![chlimage_1-81](assets/chlimage_1-81.png)

## Das Inhaltsmodell {#the-content-model}

Ein Modell beschreibt den Inhaltstyp und gibt an, welche Informationen der nativen Anwendung zur Verfügung stehen. Es ist eine Beschreibung dessen, was ein Stück Inhalt ausmacht. Ein Inhaltsmodell ist die Regeln zum Erstellen eines Inhaltselements. Das Inhaltsmodell beinhaltet, welche Daten verfügbar sind, welche Assets verwendet werden können, die Beziehung zwischen Assets und Daten, die Beziehung zu anderen Inhaltsmodellen und die verfügbaren Metadaten.

Modelle dienen auch dazu, vorhandene AEM-Inhalte in Objekte umzuwandeln, die von nativen mobilen Apps einfach verwendet werden können.

Content Services bietet einige vordefinierte Modelle für allgemeine Objekte wie Assets, Asset-Sammlungen, HTML-Seiten, App-Konfigurationen und kanalunabhängige Seiten. Diese können so konfiguriert werden, dass sie bestimmten Kundenanforderungen entsprechen, ohne dass eine AEM-Entwicklung erforderlich ist.

Der Benutzer kann seine eigenen Modelle erstellen. Dies ermöglicht die Erstellung neuer Inhaltstypen, die noch nicht von AEM verwaltet werden. Die Modellerstellung erfolgt über eine Benutzeroberfläche mit vorhandenen Primitive-Typen.

Das folgende Diagramm zeigt das Inhaltsmodell für AEM Mobile-Apps und die Zuweisung von Entitäten, Ordnern und Leerzeichen zu einer App.

![chlimage_1-82](assets/chlimage_1-82.png)

### Die Modelle {#the-models}

Modelle werden verwendet, um zu bestimmen, wie Entitäten erstellt werden. Sie definieren, was in einer Entität verfügbar ist und wie diese Daten aus AEM-Inhalten generiert werden. Bevor Sie mit der Arbeit mit Bereichen, Ordnern und Entitäten beginnen, sollten Sie mit dem Erstellen und Verwalten von Modellen vertraut sein.

>[!NOTE]
>
>Ein Modell existiert außerhalb einer App, da mehrere Apps es verwenden können.


Siehe **[Modelle](/help/mobile/administer-mobile-apps.md)**zum Erstellen und Verwalten von Modellen im Dashboard und Repository.

### Entitäten im Inhaltsmodell {#entities-in-content-model}

Eine Entität ist eine Instanz eines Inhaltsmodells. Eine Entität wird über die Content Services-API der clientseitigen Bibliothek bereitgestellt und bietet einer nativen App die Möglichkeit, auf Inhalte kanalunabhängig zuzugreifen.

Bei vorhandenen AEM-Inhalten wird eine Entität mit einem Modell und der AEM-Inhaltsquelle generiert. Eine Seitenentität ist beispielsweise ein kanalunabhängiges und layoutunabhängiges Objekt, das von einer AEM-Seite und dem Seitenmodell generiert wird.

Änderungen am referenzierten Inhalt einer Entität führen zu einer Änderung der Entität. Wenn beispielsweise eine *cq:page* aktualisiert wird, werden auch alle Entitäten, die auf dieser Seite basieren, aktualisiert.

Siehe **[Arbeiten mit Entitäten](/help/mobile/spaces-and-entities.md)**, um benutzerdefinierte Entitäten aus Modellen zu erstellen.

>[!NOTE]
>
>Wenn das Modell nicht mit einem vorhandenen AEM-Inhalt übereinstimmt, z. B. wenn der Kunde ein neues Modell erstellt hat, gibt es eine Benutzeroberfläche, damit ein Kunde eine neue Entität erstellen kann.


### Leerzeichen im Inhaltsmodell {#spaces-in-content-model}

Ein Leerzeichen wird verwendet, um Entitäten für einfachen Zugriff zu organisieren. Ein Leerzeichen kann einen oder mehrere Entitätstypen enthalten und kann Unterordner enthalten.

Auf der AEM-Seite ist ein Leerzeichen eine bequeme Möglichkeit, damit verbundene Entitäten zu verwalten. Sie kann auch verwendet werden, um Autorisierungsberechtigungen zuzuweisen. Die Autorisierung kann an einem Ort vorgenommen werden, der dann die Entitäten schützt, die sich in diesem Raum befinden.

*Beispiel*:

Ein Benutzer verfügt über drei allgemeine Klassifizierungen von Entitäten. Eine ist nur für den internen Gebrauch bestimmt, eine andere für den öffentlichen Gebrauch und eine dritte für allgemeine Entitäten, die von vielen Apps verwendet werden. Um eine einfache Verwaltung zu ermöglichen, erstellt der Benutzer drei Räume: *interne*, *öffentliche* (mit englischen und französischen Inhalten) und *gemeinsame* Räume für die Verwaltung der entsprechenden Entitäten, wie unten erwähnt:

* /content/instances/internal
* /content/entity/public/de
* /content/entity/public/fr
* /content/instances/common

Dem Bereich wird ein Dienstendpunkt bereitgestellt, damit die native Client-Bibliothek eine Liste der Inhalte eines Bereichs anfordern kann. Diese &quot;Auflistung&quot;wird als JSON-Objekt zurückgegeben.

Siehe **[Bereiche und Entitäten](/help/mobile/spaces-and-entities.md)**zum Erstellen und Veröffentlichen von Bereichen.

>[!NOTE]
>
>Ein Leerzeichen kann von vielen Apps verwendet werden und eine App kann viele Leerzeichen verwenden.

### Ordner im Inhaltsmodell {#folders-in-content-model}

Ordner ermöglichen es Benutzern, Entitäten nach Bedarf zu organisieren und erleichtern eine bessere ACL-Steuerung. Leerzeichen können Ordner enthalten, um den Inhalt und die Assets des Raums weiter zu organisieren. Ein Benutzer kann eine eigene Hierarchie unter einem Leerzeichen erstellen.

Siehe **[Arbeiten mit Ordnern in einem Bereich](/help/mobile/spaces-and-entities.md)**, um Ordner in einem Bereich zu erstellen und zu verwalten.
