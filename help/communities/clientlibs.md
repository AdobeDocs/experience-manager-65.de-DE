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

* [Verwenden Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md) , das Nutzungsdetails und Debugging-Tools bereitstellt
* [Clientlibs für SCF](/help/communities/client-customize.md#clientlibs) , die nützliche Informationen beim Anpassen von SCF-Komponenten bietet


## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn eine [Community-Funktion](/help/communities/functions.md) für eine Funktion sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, [Hinzufügen einer Communities-Komponente zu einer Seite](/help/communities/author-communities.md) kann zu JavaScript-Fehlern und einem unerwarteten Erscheinungsbild führen.

### Beispiel : platzierte Prüfungen ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![platzierten Reviews](assets/placed-reviews.png)

### Beispiel : Placed Reviews with clientlibs {#example-placed-reviews-with-clientlibs}

![review-clientlibs](assets/reviews-clientlibs.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus navigieren Sie von einer AEM-Instanz zum [Handbuch zu Community-Komponenten](/help/communities/components-guide.md) bietet Zugriff auf eine Liste von clientlib-Kategorien, die für eine Komponente erforderlich sind.

Beispiel: oben im [Überprüfungsseite](https://localhost:4502/content/community-components/en/reviews.html) die aufgelisteten erforderlichen clientlibs

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-views](assets/clientlibs-reviews.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwendung [CRXDE|Lite](#using-crxde-lite) , um eine vorhandene Clientlibsliste für eine Community-Site-Seite zu ändern.

So fügen Sie eine clientlib für eine Community-Site hinzu mithilfe von [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Suchen Sie die `clientlibslist` -Knoten für die Seite, auf der Sie die Komponente hinzufügen möchten:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit `clientlibslist` ausgewählter Knoten:

   * Suchen Sie den String .[] property `scg:requiredClientLibs`.
   * Auswahl der `Value` , damit Sie auf das Dialogfeld String-Array zugreifen können.

      * Scrollen Sie bei Bedarf nach unten.
      * Wählen Sie + aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen Sie dies, um weitere Client-Bibliotheken hinzuzufügen.

         * Wählen Sie **OK** aus.

   * Klicken Sie auf **Alle speichern**.

>[!NOTE]
>
>Wenn es sich bei der Site nicht um eine Community-Site handelt, muss das Vorhandensein oder der Speicherort der Client-Bibliotheken ermittelt werden, die für die Site verwendet werden.

Verwenden der [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) Beispiel, wobei `site-name` is *interagieren* festgelegt ist, wird die clientliblist so angezeigt, wenn die Reviews-Komponente hinzugefügt wird:

![review-component](assets/review-component.png)
