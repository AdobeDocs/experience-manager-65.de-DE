---
title: Modellübersicht
description: Erfahren Sie, wie Sie die Modellverwaltung verwenden, die die Erstellung und Verwaltung von Modellen für die Zuordnung zu eventuell vorhandenen Datenobjekten umfasst.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 50785534-5784-4354-b123-5e640b7c0242
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 3%

---

# Modellübersicht{#models-overview}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Modellverwaltung umfasst die Erstellung und Verwaltung von Modellen für die Zuordnung zu eventuell vorhandenen Datenobjekten. Jedes Modell enthält alle Eigenschaften und Felddefinitionen, die zur Erleichterung der Erstellung und Darstellung von Objekten erforderlich sind.

Die Modellverwaltung umfasst die Erstellung von **models**, **entitäten** und **Leerzeichen**. Das folgende Diagramm zeigt die Beziehung zwischen AEM Content und den Modellen.

![chlimage_1-81](assets/chlimage_1-81.png)

## Das Inhaltsmodell {#the-content-model}

Ein Modell beschreibt den Inhaltstyp und gibt an, welche Informationen für die native Anwendung verfügbar sind. Es ist eine Beschreibung dessen, was ein Inhaltselement ausmacht. Ein Inhaltsmodell ist die Regel zum Erstellen eines Inhaltselements. Das Inhaltsmodell umfasst die verfügbaren Daten, die verwendbaren Assets, die Beziehung zwischen Assets und Daten, die Beziehung zu anderen Inhaltsmodellen und die verfügbaren Metadaten.

Modelle dienen auch dazu, vorhandene AEM in Objekte umzuwandeln, die von nativen Apps einfach verwendet werden können.

Content Services bietet einige vordefinierte Modelle für gängige Objekte wie Assets, Asset-Sammlungen, HTML-Seiten, App-Konfigurationen und kanalunabhängige Seiten. Diese können so konfiguriert werden, dass sie spezifischen Kundenanforderungen gerecht werden, ohne dass AEM Entwicklungsaufwand erforderlich ist.

Benutzer können eigene Modelle erstellen. Dies ermöglicht die Erstellung neuer Inhaltstypen, die noch nicht von AEM verwaltet werden. Die Modellerstellung erfolgt über eine Benutzeroberfläche mit vorhandenen Primitive-Typen.

Das folgende Diagramm zeigt das Inhaltsmodell für AEM Mobile-Apps und wie Entitäten, Ordner und Leerzeichen einer App zugewiesen werden.

![chlimage_1-82](assets/chlimage_1-82.png)

### Die Modelle {#the-models}

Modelle werden verwendet, um zu bestimmen, wie Entitäten erstellt werden. Sie definieren, was in einer Entität verfügbar ist und wie diese Daten aus AEM Inhalt generiert werden. Bevor Sie mit der Arbeit mit Leerzeichen, Ordnern und Entitäten beginnen, sollten Sie mit dem Erstellen und Verwalten von Modellen vertraut sein.

>[!NOTE]
>
>Ein Modell existiert außerhalb einer App, da mehrere Apps es verwenden können.
>

Informationen zum Erstellen und Verwalten von Modellen im Dashboard und Repository finden Sie unter **[Modelle](/help/mobile/administer-mobile-apps.md)**.

### Entitäten im Inhaltsmodell {#entities-in-content-model}

Eine Entität ist eine Instanz eines Inhaltsmodells. Eine Entität wird über die Content Services-API der Client-seitigen Bibliothek bereitgestellt und bietet einer nativen App die Möglichkeit, kanalunabhängig auf Inhalte zuzugreifen.

Wenn bereits AEM Inhalt vorhanden ist, wird eine Entität mithilfe eines Modells und der AEM Inhaltsquelle generiert. Beispielsweise ist eine Seitenentität ein kanalunabhängiges und layout-unabhängiges Objekt, das von einer AEM Seite und dem Seitenmodell generiert wird.

Änderungen am referenzierten Inhalt einer Entität führen zu einer Änderung der Entität. Wenn beispielsweise eine *cq:page* aktualisiert wird, werden auch alle Entitäten aktualisiert, die auf dieser Seite basieren.

Informationen zum Erstellen benutzerdefinierter Entitäten aus Modellen finden Sie unter **[Arbeiten mit Entitäten](/help/mobile/spaces-and-entities.md)**.

>[!NOTE]
>
>Wenn das Modell nicht einem vorhandenen AEM-Inhalt entspricht, z. B. wenn der Kunde ein Modell erstellt hat, gibt es eine Benutzeroberfläche, über die ein Kunde eine Entität erstellen kann.
>

### Leerzeichen im Inhaltsmodell {#spaces-in-content-model}

Ein Leerzeichen dient zum Organisieren von Entitäten für einfachen Zugriff. Ein Leerzeichen kann einen oder mehrere Entitätstypen enthalten und Unterordner enthalten.

Auf der AEM Seite ist ein Leerzeichen eine bequeme Möglichkeit, verwandte Entitäten zu verwalten. Es kann auch verwendet werden, um Autorisierungsberechtigungen zuzuweisen. Die Autorisierung kann an einem Leerzeichen vorgenommen werden, das die in diesem Bereich befindlichen Entitäten schützt.

*Beispiel*:

Ein Benutzer verfügt über drei allgemeine Klassifizierungen von Entitäten. Eine dient nur der internen Verwendung, eine andere ist für die öffentliche Verwendung zugelassen und die dritte für gängige Entitäten, die von vielen Apps verwendet werden. Um die Verwaltung zu vereinfachen, erstellt der Benutzer drei Leerzeichen: *internal*, *public* (mit englischem und französischem Inhalt) und *common* zur Verwaltung der entsprechenden Entitäten, wie unten erwähnt:

* /content/entity/internal
* /content/entity/public/en
* /content/entity/public/fr
* /content/entity/common

Dem Bereich wird ein Dienstendpunkt bereitgestellt, damit die native Client-Bibliothek eine Liste der Inhalte eines Platzes anfordern kann. Diese &quot;Auflistung&quot;wird als JSON-Objekt zurückgegeben.

Informationen zum Erstellen und Veröffentlichen von Platzierungen finden Sie unter **[Platzierungen und Entitäten](/help/mobile/spaces-and-entities.md)** .

>[!NOTE]
>
>Ein Leerzeichen kann von vielen Apps verwendet werden und eine App kann viele Leerzeichen verwenden.

### Ordner im Inhaltsmodell {#folders-in-content-model}

Ordner ermöglichen es Benutzern, Entitäten nach Bedarf zu organisieren und erleichtern eine feinere ACL-Steuerung. Leerzeichen können Ordner enthalten, die die weitere Organisation des Inhalts und der Assets des Raums erleichtern. Ein Benutzer kann eine eigene Hierarchie unter einem Leerzeichen erstellen.

Informationen zum Erstellen und Verwalten von Ordnern in einem Bereich finden Sie unter **[Arbeiten mit Ordnern in einem Leerzeichen](/help/mobile/spaces-and-entities.md)**.
