---
title: Modelle - Übersicht
description: Erfahren Sie, wie Sie die Modellverwaltung verwenden, die die Erstellung und Verwaltung von Modellen für die Verknüpfung mit möglichen Datenobjekten umfasst.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 50785534-5784-4354-b123-5e640b7c0242
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Modelle - Übersicht{#models-overview}

{{ue-over-mobile}}

Die Modellverwaltung umfasst die Erstellung und Verwaltung von Modellen für die Verknüpfung mit eventuellen Datenobjekten. Jedes Modell enthält alle Eigenschaften und Felddefinitionen, die für die Erleichterung der Erstellung und des Renderings von Objekten erforderlich sind.

Die Modellverwaltung umfasst die Erstellung von **&#x200B;**, **Entitäten** und **&#x200B;**. Die folgende Abbildung zeigt die Beziehung zwischen dem AEM-Inhalt und den Modellen.

![chlimage_1-81](assets/chlimage_1-81.png)

## Das Inhaltsmodell {#the-content-model}

Ein Modell beschreibt den Inhaltstyp und gibt an, welche Informationen dem nativen Programm zur Verfügung stehen. Es ist eine Beschreibung dessen, woraus ein Teil des Inhalts besteht. Ein Inhaltsmodell ist die Regel, mit der ein Inhaltselement erstellt wird. Das Inhaltsmodell umfasst, welche Daten verfügbar sind, welche Assets verwendet werden können, die Beziehung zwischen Assets und Daten, die Beziehung zu anderen Inhaltsmodellen und die verfügbaren Metadaten.

Modelle dienen auch als Möglichkeit, vorhandene AEM-Inhalte in Objekte umzuwandeln, die von nativen Mobile Apps einfach verwendet werden können.

Content Services bietet einige vordefinierte Modelle für gängige Objekte wie Assets, Asset-Sammlungen, HTML-Seiten, App-Konfigurationen und kanalunabhängige Seiten. Diese sind so konfigurierbar, dass sie spezifischen Kundenanforderungen gerecht werden, ohne dass ein AEM-Entwicklungsaufwand erforderlich ist.

Benutzer können ihre eigenen Modelle erstellen. Dies ermöglicht die Erstellung neuer Inhaltstypen, die noch nicht von AEM verwaltet werden. Die Modellerstellung erfolgt über eine Benutzeroberfläche mit vorhandenen primitiven Typen.

Das folgende Diagramm veranschaulicht das Inhaltsmodell für AEM Mobile-Apps und wie einer App Entitäten, Ordner und Platzierungen zugewiesen werden.

![chlimage_1-82](assets/chlimage_1-82.png)

### Die Modelle {#the-models}

Modelle werden verwendet, um zu bestimmen, wie Entitäten erstellt werden. Sie definieren, was in einer Entität verfügbar ist und wie diese Daten aus AEM-Inhalten generiert werden. Bevor Sie mit Räumen, Ordnern und Entitäten arbeiten, sollten Sie mit dem Erstellen und Verwalten von Modellen vertraut sein.

>[!NOTE]
>
>Ein Modell ist außerhalb einer App vorhanden, da mehr als eine App es verwenden kann.
>

Informationen zum Erstellen und Verwalten von Modellen im Dashboard und Repository finden Sie unter **[Modelle](/help/mobile/administer-mobile-apps.md)**.

### Entitäten im Inhaltsmodell {#entities-in-content-model}

Eine Entität ist eine Instanz eines Inhaltsmodells. Eine Entität wird über die Content Services-API für die Client-seitige Bibliothek verfügbar gemacht und bietet einer nativen App eine Möglichkeit, kanalunabhängig auf Inhalte zuzugreifen.

Wenn bereits AEM-Inhalte vorhanden sind, wird eine Entität mithilfe eines Modells und der AEM-Inhaltsquelle generiert. Beispielsweise ist eine Seitenentität ein kanal- und layoutunabhängiges Objekt, das aus einer AEM-Seite und dem Seitenmodell generiert wird.

Änderungen am referenzierten Inhalt einer Entität führen zu einer Änderung der Entität. Wenn beispielsweise eine *cq:page* aktualisiert wird, werden auch alle Entitäten aktualisiert, die auf dieser Seite basieren.

Informationen zum Erstellen benutzerdefinierter Entitäten aus Modellen finden Sie unter **[Arbeiten mit Entitäten](/help/mobile/spaces-and-entities.md)**.

>[!NOTE]
>
>Wenn das Modell keinem vorhandenen AEM-Inhalt entspricht, z. B. wenn der Kunde ein Modell erstellt hat, gibt es eine Benutzeroberfläche, über die der Kunde eine Entität erstellen kann.
>

### Leerzeichen im Inhaltsmodell {#spaces-in-content-model}

Ein Bereich wird verwendet, um Entitäten für einfachen Zugriff zu organisieren. Eine Platzierung kann einen oder mehrere Entitätstypen und Unterordner enthalten.

Auf der AEM-Seite ist eine Platzierung eine praktische Möglichkeit, um verwandte Entitäten zu verwalten. Es kann auch verwendet werden, um Autorisierungsberechtigungen zuzuweisen. Die Autorisierung kann für eine Platzierung erfolgen, die die Entitäten schützt, die sich in dieser Platzierung befinden.

*Beispiel*:

Ein Benutzer verfügt über drei allgemeine Klassifizierungen von Entitäten. Eine ist nur für den internen Gebrauch, eine andere ist für den öffentlichen Gebrauch zugelassen und noch eine dritte ist für gängige Entitäten, die von vielen Apps verwendet werden. Um die Verwaltung zu vereinfachen, erstellt der Benutzer drei Bereiche: *intern*, *öffentlich* (mit englischem und französischem Inhalt) und *häufig* für die Verwaltung der entsprechenden Entitäten, wie unten erwähnt:

* /content/entities/internal
* /content/entities/public/en
* /content/entities/public/fr
* /content/entities/common

Ein Service-Endpunkt wird für die Platzierung bereitgestellt, damit die native Client-Bibliothek eine Liste der Inhalte einer Platzierung anfordern kann. Diese „Auflistung“ wird als JSON-Objekt zurückgegeben.

Siehe **[Bereiche und Entitäten](/help/mobile/spaces-and-entities.md)** zum Erstellen und Veröffentlichen von Bereichen.

>[!NOTE]
>
>Eine Platzierung kann von vielen Apps genutzt werden und eine App kann viele Platzierungen nutzen.

### Ordner im Inhaltsmodell {#folders-in-content-model}

Mit Ordnern können Benutzer Entitäten nach Bedarf organisieren. Dies erleichtert eine feinere ACL-Steuerung. Leerzeichen können Ordner enthalten, um den Inhalt und die Assets des Bereichs weiter zu organisieren. Ein Benutzer kann unter einem Bereich seine eigene Hierarchie erstellen.

Informationen zum Erstellen und Verwalten von Ordnern in einem Bereich finden Sie unter **[Arbeiten mit Ordnern in einem Bereich](/help/mobile/spaces-and-entities.md)**.
