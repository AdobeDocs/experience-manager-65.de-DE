---
title: Clientlibs für Communities-Komponenten
description: Erfahren Sie, wie Sie einer Seite Client-seitige Bibliotheken (clientlibs) hinzufügen, damit Sie Nutzungsdetails erfassen und Debugging-Tools für Communities-Komponenten verwenden können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 94415926-a273-4f03-b7b6-57fdac12c741
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# Clientlibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzufügen.

Grundlegende Informationen finden Sie unter folgenden Themen:

* [Verwendung clientseitiger Bibliotheken](/help/sites-developing/clientlibs.md) , die Nutzungsdetails und Debugging-Tools bereitstellt
* [Clientlibs für SCF](/help/communities/client-customize.md#clientlibs), die nützliche Informationen beim Anpassen von SCF-Komponenten bereitstellen


## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für das ordnungsgemäße Funktionieren (JavaScript) und Styling (CSS) einer Komponente erforderlich.

Wenn für eine Funktion eine [Community-Funktion](/help/communities/functions.md) vorhanden ist, sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen Clientlibs fehlen, kann das Hinzufügen einer Communities-Komponente zu einer Seite ](/help/communities/author-communities.md) zu JavaScript-Fehlern und unerwarteten Erscheinungsbildern führen.[

### Beispiel : platzierte Prüfungen ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![platzierte Rezensionen](assets/placed-reviews.png)

### Beispiel : Placed Reviews with clientlibs {#example-placed-reviews-with-clientlibs}

![review-clientlibs](assets/reviews-clientlibs.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus bietet das Durchsuchen des [Leitfadens zu Community-Komponenten](/help/communities/components-guide.md) von einer AEM-Instanz aus Zugriff auf eine Liste von clientlib-Kategorien, die für eine Komponente erforderlich sind.

Am oberen Rand der Seite [Bewertungen](https://localhost:4502/content/community-components/en/reviews.html) werden beispielsweise die erforderlichen clientlibs aufgeführt.

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-views](assets/clientlibs-reviews.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwenden Sie [CRXDE|Lite](#using-crxde-lite) , um eine vorhandene Clientlibsliste für eine Community-Site-Seite zu ändern.

So fügen Sie mithilfe von [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) eine clientlib für eine Community-Site hinzu:

* Navigieren Sie zu [https://&lt;Server>:&lt;Port>/crx/de](https://localhost:4502/crx/de).
* Suchen Sie den Knoten `clientlibslist` für die Seite, auf der Sie die Komponente hinzufügen möchten:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit ausgewähltem `clientlibslist` -Knoten:

   * Suchen Sie die Eigenschaft &quot;String[]&quot;`scg:requiredClientLibs`.
   * Wählen Sie den Wert `Value` aus, damit Sie auf das Dialogfeld String-Array zugreifen können.

      * Scrollen Sie bei Bedarf nach unten.
      * Wählen Sie + aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen Sie dies, um weitere Client-Bibliotheken hinzuzufügen.

         * Wählen Sie **OK** aus.

   * Klicken Sie auf **Alle speichern**.

>[!NOTE]
>
>Wenn es sich bei der Site nicht um eine Community-Site handelt, muss das Vorhandensein oder der Speicherort der Client-Bibliotheken ermittelt werden, die für die Site verwendet werden.

Unter Verwendung des Beispiels [Erste Schritte mit AEM Communities](/help/communities/getting-started.md), bei dem `site-name` *engage* ist, würde die clientliblist so angezeigt, wenn die Reviews-Komponente hinzugefügt wird:

![review-component](assets/review-component.png)
