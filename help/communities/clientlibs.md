---
title: Clientlibs für Communities-Komponenten
seo-title: Clientlibs für Communities-Komponenten
description: Clientseitige Bibliotheken für Communities
seo-description: Clientseitige Bibliotheken für Communities
uuid: d2a9f986-96cf-4ee8-81e6-36a96f45ddcb
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 68ce47c8-a03f-40d6-a7f3-2cc64aee0594
docset: aem65
translation-type: tm+mt
source-git-commit: 5b8b1544645465d10e7c2018364b6a74f1ad9a8e

---


# Clientlibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzugefügt werden.

Grundlegende Informationen finden Sie unter:

* [Verwenden clientseitiger Bibliotheken](/help/sites-developing/clientlibs.md) , die Nutzungsdetails und Debugging-Tools bereitstellen
* [Clientlibs für SCF](/help/communities/client-customize.md#clientlibs) , die beim Anpassen von SCF-Komponenten nützliche Informationen bereitstellen
* [Blog: AEM-Client-Bibliotheken, erklärt durch Beispiel](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für das ordnungsgemäße Funktionieren (JavaScript) und die Formatierung (CSS) einer Komponente erforderlich.

Wenn für eine Funktion eine [Community-Funktion](/help/communities/functions.md) vorhanden ist, werden alle notwendigen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden sein. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche clientlibs hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, kann das [Hinzufügen einer Communities-Komponente zu einer Seite](/help/communities/author-communities.md) zu Javascript-Fehlern und unerwartetem Erscheinungsbild führen.

### Beispiel: Platzierte Reviews ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-132](assets/chlimage_1-132.png)

### Beispiel: Platzierte Reviews mit Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-133](assets/chlimage_1-133.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die wesentlichen Funktionsinformationen für Entwickler identifizieren die erforderlichen clientlibs.

Darüber hinaus können Sie von einer AEM-Instanz aus im [Community-Komponentenleitfaden](/help/communities/components-guide.md) eine Auflistung der für eine Komponente erforderlichen clientlib-Kategorien aufrufen.

Die erforderlichen clientlibs sind beispielsweise ganz oben auf der Seite [Reviews aufgeführt](https://localhost:4502/content/community-components/en/reviews.html) .

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-134](assets/chlimage_1-134.png)

## Erforderliche Clientlibs hinzufügen {#adding-required-clientlibs}

Wenn Sie einer Seite eine Communities-Komponente hinzufügen möchten, müssen Sie die erforderlichen clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwenden Sie [CRXDE|Lite](#using-crxde-lite) , um eine vorhandene clientlibslist für eine Community-Site-Seite zu ändern.

So fügen Sie eine clientlib für eine Community-Site mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) hinzu:

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* Suchen Sie die `clientlibslist` Node der Seite, auf der Sie die Komponente hinzufügen möchten

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit `clientlibslist` ausgewählter Node

   * Suchen Sie die String[] -Eigenschaft `scg:requiredClientLibs`
   * Wählen Sie `Value` die Option zum Zugriff auf das Dialogfeld &quot;String-Array&quot;

      * Bei Bedarf scrollen
      * Wählen Sie +, um eine neue Client-Bibliothek einzugeben

         * Wiederholen, um weitere Client-Bibliotheken hinzuzufügen
      * Wählen Sie **OK** aus
   * Select **Save All**



>[!NOTE]
>
>Wenn die Site keine Community-Site ist, muss die Existenz oder der Speicherort der Client-Bibliotheken, die für die Site verwendet werden, ermittelt werden.

Mithilfe des Beispiels &quot; [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) &quot;, in dem `site-name` &quot; *Interagieren*&quot;angegeben ist, wird die clientliblist wie folgt angezeigt, wenn die Komponente &quot;Reviews&quot;hinzugefügt wird:

![chlimage_1-135](assets/chlimage_1-135.png)

