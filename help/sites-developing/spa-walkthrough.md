---
title: Einführung in SPAs und exemplarische Anleitung
seo-title: SPA Introduction and Walkthrough
description: In diesem Artikel werden die Konzepte einer SPA vorgestellt und die Nutzung einer einfachen SPA zur Inhaltserstellung erläutert. Außerdem wird gezeigt, wie eine SPA mit dem zugrunde liegenden AEM-SPA-Editor in Beziehung steht.
seo-description: This article introduces the concepts of a SPA and walks through using a basic SPA application for authoring, showing how it relates to the underlying AEM SPA Editor.
uuid: 4b0a9e53-3892-4d60-8bd3-7ff740d2f137
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 0478afcb-b029-4ce6-b3e6-cee4bb5408ce
docset: aem65
exl-id: 95990112-2afc-420a-a7c7-9613f40d4c4a
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 100%

---

# Einführung in SPAs und exemplarische Anleitung{#spa-introduction-and-walkthrough}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA-Frameworks erstellen und Autoren möchten Inhalte in AEM nahtlos für eine Site bearbeiten, die mit diesen Frameworks erstellt wurde.

Der SPA-Editor bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird die Verwendung einer einfachen SPA zur Inhaltserstellung erläutert und gezeigt, wie sie mit dem zugrunde liegenden AEM-SPA-Editor in Beziehung steht.

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen Client-seitiges Rendering auf Basis eines SPA-Frameworks (z. B. React oder Angular) erforderlich ist.

## Einführung {#introduction}

### Ziel des Artikels {#article-objective}

In diesem Artikel werden die grundlegenden Konzepte von SPAs vorgestellt, bevor der Leser eine exemplarische Anleitung zum SPA-Editor erhält, indem ein einfaches SPA-Programm zum Demonstrieren der grundlegenden Inhaltsbearbeitung verwendet wird. Dann folgen Details zum Aufbau der Seite und zu der Frage, wie die SPA mit dem AEM-SPA-Editor in Beziehung steht und interagiert.

Ziel der vorliegenden Einführung und exemplarischen Anleitung ist es, einem AEM-Entwickler zu demonstrieren, warum SPAs relevant sind, wie sie grundsätzlich funktionieren, wie SPAs vom AEM-SPA-Editor gehandhabt werden und wie sie sich von einem standardmäßigen AEM-Programm unterscheiden.

Die exemplarische Anleitung basiert auf AEM-Standardfunktionen und der Beispiel-App „We.Retail Journal“. Die folgenden Anforderungen müssen erfüllt sein:

* [Version AEM 6.4 mit Service Pack 2 oder höher](/help/release-notes/release-notes.md)
* [Installieren Sie die Beispiel-App „We.Retail Journal“, die hier auf GitHub verfügbar ist.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>[!CAUTION]
>
>In diesem Dokument dient die [We.Retail Journal-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) ausschließlich zu Demonstrationszwecken. Sie sollte nicht für Projektaufgaben verwendet werden.
>
>Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK verwendet.

### Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

So wird der Bedarf nach Seitenaktualisierungen reduziert und dem Benutzer ein Erlebnis präsentiert, das nahtlos und schnell ist und eher wie eine native App funktioniert.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklern, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautoren SPA-Inhalte so einfach bearbeiten können wie andere AEM-Inhalte.

### Warum eine SPA? {#why-a-spa}

Da SPAs schneller, nahtloser und eher wie ein natives Programm sind, sind sie nicht nur für Besucher der Web-Seite, sondern auch für Marketing-Experten und Entwickler attraktiv. Das hängt mit der Art und Weise zusammen, wie SPAs funktionieren.

![screen_shot_2018-08-20at135550](assets/screen_shot_2018-08-20at135550.png)

**Besucher**

* Besucher bevorzugen native Erlebnisse, wenn sie mit Inhalten interagieren.
* Es gibt Daten, die klar zeigen, dass eine Konversion umso wahrscheinlicher ist, je schneller eine Seite ist.

**Marketing-Experten**

* Marketing-Experten wollen umfangreiche, quasi native Erlebnisse bieten, um Besucher dazu zu bringen, sich voll und ganz auf Inhalte einzulassen.
* Durch Personalisierung können diese Erlebnisse noch ansprechender gestaltet werden.

**Entwickler**

* Entwickler wünschen sich eine saubere Trennung zwischen Inhalten und Präsentation.
* Eine saubere Trennung macht das System leichter erweiterbar und erlaubt eine unabhängige Frontend-Entwicklung.

### Wie funktioniert eine SPA? {#how-does-a-spa-work}

Die Grundidee hinter einer SPA besteht darin, dass Aufrufe an und Abhängigkeiten von einem Server verringert werden, um Verzögerungen zu minimieren, die durch Server-Aufrufe verursacht werden. So kommen SPAs der Reaktionsgeschwindigkeit einer nativen Anwendung nahe.

Bei einer herkömmlichen, sequenziellen Web-Seite werden nur die für die aktuelle Seite benötigten Daten geladen. Das bedeutet, dass beim Wechseln des Besuchers zu einer anderen Seite der Server für die zusätzlichen Ressourcen aufgerufen werden muss. Weitere Aufrufe können erforderlich sein, wenn der Besucher mit Elementen auf der Seite interagiert. Diese Mehrfachaufrufe können zu einer Wahrnehmung von Verzögerungen führen, da die Seite die Anfragen des Besuchers erfüllen muss.

![screen_shot_2018-08-20at140449](assets/screen_shot_2018-08-20at140449.png)

Für ein nahtloseres Benutzererlebnis, das dem entspricht, was Besucher von mobilen, nativen Apps erwarten, lädt eine SPA alle erforderlichen Daten für den Besucher beim ersten Laden. Dies mag zunächst ein wenig länger dauern, erfordert dann jedoch keine weiteren Server-Aufrufe mehr.

Durch das Client-seitige Rendern reagieren Seitenelemente schneller; Interaktionen mit der Seite durch den Besucher werden sofort ausgeführt. Alle weiteren erforderlichen Daten werden asynchron aufgerufen, um die Seitengeschwindigkeit zu maximieren.

>[!NOTE]
>
>Technische Details zur Funktionsweise von SPAs in AEM finden Sie im Artikel [Erste Schritte mit SPAs in AEM](/help/sites-developing/spa-getting-started-react.md).
>
>Weitere Informationen zu Design, Architektur und technischem Workflow des SPA-Editors finden Sie im Artikel [SPA-Editor – Überblick](/help/sites-developing/spa-overview.md).

## Inhaltsbearbeitungserlebnis mit SPA {#content-editing-experience-with-spa}

Wenn eine SPA zur Nutzung des AEM-SPA-Editors konfiguriert ist, merkt der Inhaltsautor beim Bearbeiten und Erstellen von Inhalten keinen Unterschied. Es stehen gängige AEM-Funktionen zur Verfügung; am Workflow des Autors sind keine Änderungen erforderlich.

>[!NOTE]
>
>Die exemplarische Anleitung basiert auf AEM-Standardfunktionen und der Beispiel-App „We.Retail Journal“. Die folgenden Anforderungen müssen erfüllt sein:
>
>* [Version AEM 6.4 mit Service Pack 2](/help/release-notes/release-notes.md)
>* [Installieren Sie die Beispiel-App „We.Retail Journal“, die hier auf GitHub verfügbar ist.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)
>


1. Bearbeiten Sie die App „We.Retail Journal“ in AEM.

   `https://localhost:4502/editor.html/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at142533](assets/screen_shot_2018-06-07at142533.png)

1. Wählen Sie eine Überschriftkomponente aus und beachten Sie, dass wie bei jeder anderen Komponente eine Symbolleiste angezeigt wird. Wählen Sie **Bearbeiten** aus.

   ![screen_shot_2018-06-07at142937](assets/screen_shot_2018-06-07at142937.png)

1. Bearbeiten Sie den Inhalt in AEM wie gewohnt und beachten Sie, dass die Änderungen gespeichert werden.

   ![screen_shot_2018-06-07at143419](assets/screen_shot_2018-06-07at143419.png)

   >[!NOTE]
   >Weitere Informationen zum integrierten Texteditor und SPAs finden Sie unter [SPA-Editor – Übersicht](spa-overview.md#requirements-limitations) für .

1. Verwenden Sie den Assets-Browser, um ein neues Bild in eine Bildkomponente zu ziehen.

   ![screen_shot_2018-06-07at143530](assets/screen_shot_2018-06-07at143530.png)

1. Die Änderung wird gespeichert.

   ![screen_shot_2018-06-07at143732](assets/screen_shot_2018-06-07at143732.png)

Weitere Authoring-Werkzeuge wie das Ziehen und Ablegen zusätzlicher Komponenten auf der Seite, das Neuanordnen von Komponenten und das Ändern des Layouts werden wie in jeder Nicht-SPA-Anwendung unterstützt.

>[!NOTE]
>
>Der SPA-Editor ändert das DOM des Programms nicht. Die SPA selbst ist für das DOM verantwortlich.
>
>Um zu erfahren, wie das funktioniert, fahren Sie mit dem nächsten Abschnitt des Artikels [SPAs und der AEM-SPA-Editor](/help/sites-developing/spa-walkthrough.md#spa-apps-and-the-aem-spa-editor) fort.

## SPAs und der AEM-SPA-Editor {#spa-apps-and-the-aem-spa-editor}

Wenn Sie wissen, wie sich eine SPA beim Endbenutzer verhält, und dann die SPA-Seite prüfen, können Sie besser verstehen, wie eine SAP-Anwendung mit dem SPA-Editor in AEM zusammenarbeitet.

### Verwenden einer SPA-Anwendung {#using-an-spa-application}

1. Laden Sie die We.Retail Journal-App entweder auf den Veröffentlichungs-Server oder mithilfe der Option **Als veröffentlicht anzeigen** im Menü **Seiteninformationen** des Seiteneditors.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-08at102650](assets/screen_shot_2018-06-08at102650.png)

   Beachten Sie die Seitenstruktur, einschließlich der Navigation zu untergeordneten Seiten, Wetter-Widget und Artikeln.

1. Navigieren Sie mithilfe des Menüs zu einer untergeordneten Seite und beachten Sie, dass die Seite sofort geladen wird, ohne dass eine Aktualisierung erforderlich ist.

   ![screen_shot_2018-06-08at102815](assets/screen_shot_2018-06-08at102815.png)

1. Öffnen Sie die integrierten Entwickler-Tools Ihres Browsers und überwachen Sie beim Navigieren durch die untergeordneten Seiten die Netzwerkaktivität.

   ![screen_shot_2018-06-08at103922](assets/screen_shot_2018-06-08at103922.png)

   Wenn Sie in der App von Seite zu Seite wechseln, ist der Traffic sehr gering. Die Seite wird nicht neu geladen; lediglich die neuen Bilder werden angefordert.

   Die SPA verwaltet Inhalt und Routing komplett auf der Client-Seite.

Wenn die Seite beim Navigieren durch die untergeordneten Seiten nicht neu geladen wird: Wie wird sie dann geladen?

Im nächsten Abschnitt [Laden einer SPA-Anwendung](/help/sites-developing/spa-walkthrough.md#loading-an-spa-application) werden die Methoden zum Laden der SPA sowie zum synchronen und asynchronen Laden von Inhalten genauer erläutert.

### Laden einer SPA-Anwendung {#loading-an-spa-application}

1. Laden Sie, falls noch nicht geschehen, die We.Retail Journal-App entweder auf den Veröffentlichungs-Server oder unter Verwendung der Option **Als veröffentlicht anzeigen** im Menü **Seiteninformationen** des Seiteneditors.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at144736](assets/screen_shot_2018-06-07at144736.png)

1. Verwenden Sie das integrierte Tool Ihres Browsers, um die Quelle der Seiten anzuzeigen.
1. Beachten Sie, dass der Inhalt der Quelle sehr begrenzt ist.

   ```
   <!DOCTYPE HTML>
   <html lang="en-CH">
       <head>
       <meta charset="UTF-8">
       <title>We.Retail Journal</title>
   
       <meta name="template" content="we-retail-react-template"/>
   
   <link rel="stylesheet" href="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.css" type="text/css">
   
   <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
   
   </head>
       <body class="page basicpage">
   
   <div id="page"></div>
   
   <script type="text/javascript" src="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.js"></script>
   
       </body>
   </html>
   ```

   Die Seite enthält im Hauptteil keine Inhalte. Sie besteht hauptsächlich aus Stylesheets und einem Aufruf des React-Skripts `we-retail-journal-react.js`.

   Dieses React-Skript ist der primäre Treiber dieser Anwendung und für das Rendering des gesamten Inhalts zuständig.

1. Nutzen Sie die integrierten Tools Ihres Browsers, um die Seite zu überprüfen. Sehen Sie sich den Inhalt des vollständig geladenen DOM an.

   ![screen_shot_2018-06-07at151848](assets/screen_shot_2018-06-07at151848.png)

1. Wechseln Sie im Inspektor zur Registerkarte „Netzwerk“ und laden Sie die Seite neu.

   Beachten Sie, dass wenn Bildanfragen ignoriert werden, die primären Ressourcen, die für die Seite geladen werden, die Seite selbst, CSS, das React-JavaScript, seine Abhängigkeiten sowie JSON-Daten für die Seite sind.

   ![screen_shot_2018-06-07at152155](assets/screen_shot_2018-06-07at152155.png)

1. Laden Sie `react.model.json` in einer neuen Registerkarte.

   `/content/we-retail-journal/react.model.json`

   ![screen_shot_2018-06-07at152636](assets/screen_shot_2018-06-07at152636.png)

   Der AEM-SPA-Editor nutzt [AEM Content Services](/help/assets/content-fragments/content-fragments.md), um den gesamten Inhalt der Seite als JSON-Modell bereitzustellen.

   Durch Implementierung spezifischer Schnittstellen stellen Sling-Modelle die für die SPA notwendigen Daten bereit. Die Bereitstellung der JSON-Daten wird nach unten an die jeweilige Komponente delegiert (von Seite zu Absatz zu Komponente usw.).

   Jede Komponente entscheidet, was sie verfügbar macht und wie sie gerendert wird (Server-seitig mit HTL oder Client-seitig mit React). In diesem Artikel geht es um das Client-seitige Rendering mit React.

1. Das Modell kann Seiten auch gruppieren, damit sie synchron geladen werden. Dadurch verringert sich die Zahl der erforderlichen Seitenneuladungen.

   Im Beispiel von „We.Retail Journal“ werden die Seiten `home`, `blog` und `aboutus` synchron geladen, da Besucher in der Regel alle diese Seiten besuchen. Allerdings wird die Seite `weather` asynchron geladen, da es weniger wahrscheinlich ist, dass Besucher sie besuchen.

   Dieses Verhalten ist nicht obligatorisch und kann umfassend definiert werden.

   ![screen_shot_2018-06-07at153945](assets/screen_shot_2018-06-07at153945.png)

1. Um diesen Unterschied im Verhalten zu sehen, laden Sie die Seite neu und löschen Sie die Netzwerkaktivität des Inspektors. Navigieren Sie im Seitenmenü zu den Seiten „blog“ und „about us“. Sie sehen, dass keine Netzwerkaktivität gemeldet wird.

   Navigieren Sie zur Seite „weather“. Sie sehen, dass `weather.model.json` asynchron aufgerufen wird.

   ![screen_shot_2018-06-07at155738](assets/screen_shot_2018-06-07at155738.png)

### Interaktion mit dem SPA-Editor {#interaction-with-the-spa-editor}

Mithilfe der Beispiel-App „We.Retail Journal“ wird deutlich, wie sich die App verhält und beim Veröffentlichen geladen wird. Dabei kommen Inhalts-Services für die JSON-Inhaltsbereitstellung sowie das asynchrone Laden von Ressourcen zum Einsatz.

Darüber hinaus ist die Inhaltserstellung mit einem SPA-Editor für den Inhaltsautor in AEM nahtlos.

Im folgenden Abschnitt werden wir uns den Vertrag ansehen, der es dem SPA-Editor erlaubt, Komponenten innerhalb der SPA mit AEM-Komponenten zu verbinden und so für ein nahtloses Bearbeitungserlebnis zu sorgen.

1. Laden Sie die We.Retail Journal-App im Editor und wechseln Sie in den Modus **Vorschau**.

   `https://localhost:4502/editor.html/content/we-retail-journal/react.html`

1. Überprüfen Sie mithilfe der integrierten Entwickler-Tools Ihres Browsers den Inhalt der Seite. Wählen Sie mit dem Auswahl-Tool eine bearbeitbare Komponente auf der Seite aus und zeigen Sie die Elementdetails an.

   Beachten Sie, dass die Komponente über ein neues Datenattribut verfügt (`data-cq-data-path`).

   ![screen_shot_2018-06-08at095124](assets/screen_shot_2018-06-08at095124.png)

   Beispiel

   `data-cq-data-path="root/responsivegrid/paragraph_1`

   Dieser Pfad ermöglicht ein Abrufen und Verknüpfen des Konfigurationsobjekts mit Bearbeitungskontext der einzelnen Komponenten.

   Dies ist das einzige Markup-Attribut, das erforderlich ist, damit der Editor das Element als bearbeitbare Komponente innerhalb der SPA erkennen kann. Auf Grundlage dieses Attributs bestimmt der SPA-Editor, welche bearbeitbare Konfiguration mit der Komponente verknüpft ist, sodass der richtige Rahmen, die richtige Symbolleiste usw. geladen werden.

   Einige spezifische Klassennamen werden auch für die Kennzeichnung von Platzhaltern und für die Drag-and-Drop-Funktion von Assets hinzugefügt.

   >[!NOTE]
   >
   >Dieses Verhalten unterscheidet sich von Server-seitig gerenderten Seiten in AEM, wo für jede bearbeitbare Komponente ein `cq`-Element eingefügt wird.
   >
   >
   >Durch diesen Ansatz für SPAs müssen benutzerdefinierte Elemente nicht mehr eingefügt werden, da nur ein zusätzliches Datenattribut erforderlich ist. Dadurch wird das Markup-Verfahren für Frontend-Entwickler vereinfacht.

## Nächste Schritte {#next-steps}

Da Sie nun das SPA-Bearbeitungserlebnis in AEM kennen und die Beziehung einer SPA zum SPA-Editor verstehen, können Sie sich genauere Einblicke in die Erstellung einer SPA verschaffen.

* [Erste Schritte mit SPAs in AEM](/help/sites-developing/spa-getting-started-react.md) zeigt, wie eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [SPA-Editor – Überblick](/help/sites-developing/spa-overview.md) vertieft das Kommunikationsmodell zwischen AEM und der SPA.
* [Entwicklung von SPAs für AEM](/help/sites-developing/spa-architecture.md) beschreibt, wie Frontend-Entwickler damit beauftragt werden können, eine SPA für AEM zu entwickeln, und wie SPAs mit der Architektur von AEM interagieren.
