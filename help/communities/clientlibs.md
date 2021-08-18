---
title: Clientlibs für Communities-Komponenten
seo-title: Clientlibs für Communities-Komponenten
description: Client-seitige Bibliotheken für Communities
seo-description: Client-seitige Bibliotheken für Communities
uuid: d2a9f986-96cf-4ee8-81e6-36a96f45ddcb
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 68ce47c8-a03f-40d6-a7f3-2cc64aee0594
docset: aem65
exl-id: 94415926-a273-4f03-b7b6-57fdac12c741
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---

# Clientlibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzufügen.

Grundlegende Informationen finden Sie unter :

* [Verwendung clientseitiger ](/help/sites-developing/clientlibs.md) Bibliotheken, die Nutzungsdetails sowie Debugging-Tools bereitstellt
* [Clientlibs für ](/help/communities/client-customize.md#clientlibs) SCF, die nützliche Informationen beim Anpassen von SCF-Komponenten bereitstellen


## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn für eine Funktion eine [Community-Funktion](/help/communities/functions.md) vorhanden ist, sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, kann das Hinzufügen einer Communities-Komponente zu einer Seite](/help/communities/author-communities.md) zu JavaScript-Fehlern sowie zu einem unerwarteten Erscheinungsbild führen.[

### Beispiel : Platzierte Prüfungen ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![platzierte Rezensionen](assets/placed-reviews.png)

### Beispiel : Platzierte Prüfungen mit Clientlibs {#example-placed-reviews-with-clientlibs}

![review-clientlibs](assets/reviews-clientlibs.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus bietet das Navigieren von einer AEM-Instanz zum [Community Components Guide](/help/communities/components-guide.md) Zugriff auf eine Liste von clientlib-Kategorien, die für eine Komponente erforderlich sind.

Am Anfang der [Seite &quot;Bewertungen&quot;](https://localhost:4502/content/community-components/en/reviews.html) sind die erforderlichen clientlibs aufgeführt.

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-views](assets/clientlibs-reviews.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwenden Sie [CRXDE|Lite](#using-crxde-lite), um eine vorhandene Clientlibslist für eine Community-Site-Seite zu ändern.

So fügen Sie eine clientlib für eine Community-Site mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) hinzu:

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Suchen Sie den Knoten `clientlibslist` für die Seite, auf der Sie die Komponente hinzufügen möchten:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Wählen Sie den Knoten `clientlibslist` aus:

   * Suchen Sie die Eigenschaft String[] `scg:requiredClientLibs` .
   * Wählen Sie das zugehörige `Value` aus, um auf das Dialogfeld String-Array zuzugreifen.

      * Scrollen Sie bei Bedarf nach unten.
      * Wählen Sie + aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen Sie dies, um weitere Client-Bibliotheken hinzuzufügen.

         * Wählen Sie **OK** aus.
   * Wählen Sie **Alle speichern** aus.


>[!NOTE]
>
>Wenn es sich bei der Site nicht um eine Community-Site handelt, müssen die Existenz oder der Speicherort der Client-Bibliotheken, die für die Site verwendet werden, ermittelt werden.

Unter Verwendung des Beispiels [Erste Schritte mit AEM Communities](/help/communities/getting-started.md), in dem `site-name` *engage* ist, würde die clientliblist so angezeigt, wenn die Überprüfungskomponente hinzugefügt wird:

![review-component](assets/review-component.png)
