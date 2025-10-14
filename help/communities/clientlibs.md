---
title: Clientlibs für Communities-Komponenten
description: Erfahren Sie, wie Sie einer Seite Client-seitige Bibliotheken (Clientlibs) hinzufügen, damit Sie Nutzungsdetails erfassen und Debugging-Tools für Communities-Komponenten verwenden können.
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

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie einer Seite für Communities-Komponenten Client-seitige Bibliotheken (clientlibs) hinzufügen.

Grundlegende Informationen finden Sie in den folgenden Themen:

* [Verwendung Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md) mit Nutzungsdetails und Debugging-Tools
* [Clientlibs für SCF](/help/communities/client-customize.md#clientlibs), das nützliche Informationen beim Anpassen von SCF-Komponenten bereitstellt


## Warum Client-Bibliotheken erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für das ordnungsgemäße Funktionieren (JavaScript) und Formatieren (CSS) einer Komponente erforderlich.

Wenn für eine Funktion [Community-Funktion](/help/communities/functions.md) vorhanden ist, sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen Clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, kann [Hinzufügen einer Communitys-Komponente zu einer Seite](/help/communities/author-communities.md) zu JavaScript-Fehlern und einem unerwarteten Erscheinungsbild führen.

### Beispiel : platzierte Reviews ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![platziert-reviews](assets/placed-reviews.png)

### Beispiel : Platzierte Rezensionen mit Clientlibs {#example-placed-reviews-with-clientlibs}

![views-clientlibs](assets/reviews-clientlibs.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus bietet die Navigation auf einer AEM[Instanz zum -Komponentenhandbuch &#x200B;](/help/communities/components-guide.md) Zugriff auf eine Liste der clientlib-Kategorien, die für eine Komponente erforderlich sind.

Beispielsweise werden oben auf der Seite [Überprüfungen](https://localhost:4502/content/community-components/en/reviews.html) die erforderlichen Client-Bibliotheken aufgeführt.

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-views](assets/clientlibs-reviews.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie einer Seite eine Communities -Komponente hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Mit [CRXDE|Lite](#using-crxde-lite) können Sie eine vorhandene clientlibs-Liste für eine Community-Site-Seite ändern.

So fügen Sie mithilfe von [CRXDE Lite eine Client-Bibliothek für eine Community-Site &#x200B;](/help/sites-developing/developing-with-crxde-lite.md):

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Suchen Sie den `clientlibslist` Knoten für die Seite, auf der Sie die Komponente hinzufügen möchten:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit `clientlibslist` ausgewählten Knoten:

   * Suchen Sie die Zeichenfolge[] Eigenschaft `scg:requiredClientLibs`.
   * Wählen Sie die `Value` aus, damit Sie auf das Dialogfeld Zeichenfolgen-Array zugreifen können.

      * Scrollen Sie bei Bedarf nach unten.
      * Wählen Sie + aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen Sie diesen Vorgang, um weitere Client-Bibliotheken hinzuzufügen.

         * Wählen Sie **OK** aus.

   * Klicken Sie auf **Alle speichern**.

>[!NOTE]
>
>Wenn die Site keine Community-Site ist, muss das Vorhandensein oder der Speicherort der für die Site verwendeten Client-Bibliotheken erkannt werden.

Wenn Sie das [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) verwenden, `site-name` &quot;*&quot;*, würde die clientliblist wie folgt aussehen, wenn Sie die Reviews-Komponente hinzufügen:

![review-component](assets/review-component.png)
