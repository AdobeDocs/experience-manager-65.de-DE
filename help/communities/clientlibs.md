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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 2%
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

Wenn Sie von einer AEM-Instanz aus zum [Community-Komponentenhandbuch“ navigieren](/help/communities/components-guide.md) erhalten Sie außerdem Zugriff auf eine Liste mit Client-Bibliothekskategorien, die für eine Komponente erforderlich sind.

Beispielsweise werden oben auf der Seite [Überprüfungen](https://localhost:4502/content/community-components/en/reviews.html) die erforderlichen Client-Bibliotheken aufgeführt.

* CQ.CKEditor
* CQ.social.hbs.reviews

![clientlibs-views](assets/clientlibs-reviews.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie einer Seite eine Communities -Komponente hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Mit [CRXDE|Lite](#using-crxde-lite) können Sie eine vorhandene clientlibs-Liste für eine Community-Site-Seite ändern.

So fügen Sie mithilfe von [CRXDE Lite eine Client-Bibliothek für eine Community-Site ](/help/sites-developing/developing-with-crxde-lite.md):

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
