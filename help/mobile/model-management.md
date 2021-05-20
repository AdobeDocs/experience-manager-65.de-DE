---
title: Modellübersicht
seo-title: Modellübersicht
description: Modellübersicht
seo-description: 'null'
uuid: e09dac52-9515-43f7-9d3b-6637e2283d59
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: c8281f98-9811-42f7-9a31-f82dd0f09319
exl-id: 50785534-5784-4354-b123-5e640b7c0242
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 3%

---

# Modellübersicht{#models-overview}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Modellverwaltung umfasst die Erstellung und Verwaltung von Modellen zum Zweck der Zuordnung zu Datenobjekten. Jedes Modell enthält alle Eigenschaften und Felddefinitionen, die zur Erleichterung der Erstellung und Darstellung von Objekten erforderlich sind.

Die Modellverwaltung umfasst die Erstellung von **Modellen**, **Entitäten** und **Leerzeichen**. Das folgende Diagramm zeigt die Beziehung zwischen AEM Content und den Modellen.

![chlimage_1-81](assets/chlimage_1-81.png)

## Das Inhaltsmodell {#the-content-model}

Ein Modell beschreibt den Inhaltstyp und gibt an, welche Informationen für die native Anwendung verfügbar sein werden. Es ist eine Beschreibung dessen, was ein Inhaltselement ausmacht. Ein Inhaltsmodell ist die Regel zum Erstellen eines Inhaltselements. Das Inhaltsmodell umfasst, welche Daten verfügbar sind, welche Assets verwendet werden können, die Beziehung zwischen Assets und Daten, die Beziehung zu anderen Inhaltsmodellen und die verfügbaren Metadaten.

Modelle dienen auch dazu, vorhandene AEM in Objekte umzuwandeln, die von nativen Apps einfach verwendet werden können.

Content Services bietet einige vordefinierte Modelle für gängige Objekte wie Assets, Asset-Sammlungen, HTML-Seiten, App-Konfigurationen und kanalunabhängige Seiten. Diese können so konfiguriert werden, dass sie spezifischen Kundenanforderungen gerecht werden, ohne dass AEM Entwicklungsaufwand erforderlich ist.

Der Benutzer kann seine eigenen Modelle erstellen. Dies ermöglicht die Erstellung neuer Inhaltstypen, die noch nicht von AEM verwaltet werden. Die Modellerstellung erfolgt über eine Benutzeroberfläche mit vorhandenen Primitive-Typen.

Das folgende Diagramm zeigt das Inhaltsmodell für AEM Mobile-Apps und wie Entitäten, Ordner und Leerzeichen einer App zugewiesen werden.

![chlimage_1-82](assets/chlimage_1-82.png)

### Die Modelle {#the-models}

Modelle werden verwendet, um zu bestimmen, wie Entitäten erstellt werden. Sie definieren, was in einer Entität verfügbar ist und wie diese Daten aus AEM Inhalt generiert werden. Bevor Sie mit der Arbeit mit Leerzeichen, Ordnern und Entitäten beginnen, sollten Sie mit dem Erstellen und Verwalten von Modellen vertraut sein.

>[!NOTE]
>
>Ein Modell existiert außerhalb einer App, da mehrere Apps es verwenden können.


Siehe **[Modelle](/help/mobile/administer-mobile-apps.md)** zum Erstellen und Verwalten von Modellen im Dashboard und Repository.

### Entitäten im Inhaltsmodell {#entities-in-content-model}

Eine Entität ist eine Instanz eines Inhaltsmodells. Eine Entität wird über die Content Services-API der Client-seitigen Bibliothek bereitgestellt und bietet einer nativen App die Möglichkeit, kanalunabhängig auf Inhalte zuzugreifen.

Bei vorhandenem AEM wird eine Entität mithilfe eines Modells und der AEM Inhaltsquelle generiert. Beispielsweise ist eine Seitenentität ein kanalunabhängiges und layout-unabhängiges Objekt, das von einer AEM Seite und dem Seitenmodell generiert wird.

Änderungen am referenzierten Inhalt einer Entität führen zu einer Änderung an der Entität. Wenn beispielsweise *cq:page* aktualisiert wird, werden auch alle Entitäten aktualisiert, die auf dieser Seite basieren.

Informationen zum Erstellen benutzerdefinierter Entitäten aus Modellen finden Sie unter **[Arbeiten mit Entitäten](/help/mobile/spaces-and-entities.md)** .

>[!NOTE]
>
>Wenn das Modell keinem vorhandenen AEM-Inhalt entspricht, z. B. wenn der Kunde ein neues Modell erstellt hat, gibt es eine Benutzeroberfläche, über die ein Kunde eine neue Entität erstellen kann.


### Leerzeichen im Inhaltsmodell {#spaces-in-content-model}

Ein Leerzeichen dient zum Organisieren von Entitäten für einfachen Zugriff. Ein Leerzeichen kann einen oder mehrere Entitätstypen enthalten und Unterordner enthalten.

Auf der AEM Seite ist ein Leerzeichen eine bequeme Möglichkeit, verwandte Entitäten zu verwalten. Es kann auch verwendet werden, um Autorisierungsberechtigungen zuzuweisen. Die Autorisierung kann an einem Leerzeichen vorgenommen werden, das dann die Entitäten schützt, die sich in diesem Bereich befinden.

*Beispiel*:

Ein Benutzer verfügt über drei allgemeine Klassifizierungen von Entitäten. Eine dient nur der internen Verwendung, eine andere ist für die öffentliche Verwendung zugelassen und die dritte für gängige Entitäten, die von vielen Apps verwendet werden. Um die Verwaltung zu vereinfachen, erstellt der Benutzer drei Leerzeichen: *internal*, *public* (mit sowohl englischem als auch französischem Inhalt) und *common* für die Verwaltung der entsprechenden Entitäten wie unten erwähnt:

* /content/entity/internal
* /content/entity/public/en
* /content/entity/public/fr
* /content/entity/common

Der Bereich wird mit einem Dienstendpunkt versehen, damit die native Client-Bibliothek eine Liste der Inhalte eines Platzes anfordern kann. Diese &quot;Auflistung&quot;wird als JSON-Objekt zurückgegeben.

Informationen zum Erstellen und Veröffentlichen von Platzierungen finden Sie unter **[Platzierungen und Entitäten](/help/mobile/spaces-and-entities.md)** .

>[!NOTE]
>
>Ein Leerzeichen kann von vielen Apps verwendet werden und eine App kann viele Leerzeichen verwenden.

### Ordner im Inhaltsmodell {#folders-in-content-model}

Ordner ermöglichen es Benutzern, Entitäten nach Bedarf zu organisieren und erleichtern eine feinere ACL-Steuerung. Leerzeichen können Ordner enthalten, die die weitere Organisation des Inhalts und der Assets des Raums erleichtern. Ein Benutzer kann eine eigene Hierarchie unter einem Leerzeichen erstellen.

Informationen zum Erstellen und Verwalten von Ordnern in einem Bereich finden Sie unter **[Arbeiten mit Ordnern in einem Leerzeichen](/help/mobile/spaces-and-entities.md)**.
