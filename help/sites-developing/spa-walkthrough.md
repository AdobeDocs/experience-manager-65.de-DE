---
title: Einführung in SPAs und exemplarische Anleitung
description: In diesem Artikel werden die Konzepte einer SPA vorgestellt und die Nutzung einer einfachen SPA zur Inhaltserstellung erläutert. Außerdem wird gezeigt, wie eine SPA mit dem zugrunde liegenden AEM-SPA-Editor in Beziehung steht.
topic-tags: spa
content-type: reference
exl-id: 95990112-2afc-420a-a7c7-9613f40d4c4a
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1967'
ht-degree: 94%

---


# Einführung in SPAs und exemplarische Anleitung {#spa-introduction-and-walkthrough}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA Frameworks erstellen können und Autoren möchten Inhalte in AEM für eine Site, die mit solchen Frameworks erstellt wurde, nahtlos bearbeiten.

Der SPA-Editor bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird die Verwendung einer einfachen SPA zur Inhaltserstellung erläutert und gezeigt, wie sie mit dem zugrunde liegenden AEM-SPA-Editor in Beziehung steht.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Einführung {#introduction}

### Ziel des Artikels {#article-objective}

In diesem Artikel werden die grundlegenden Konzepte von SPAs vorgestellt, bevor der Leser eine exemplarische Anleitung zum SPA-Editor erhält, indem ein einfaches SPA-Programm zum Demonstrieren der grundlegenden Inhaltsbearbeitung verwendet wird. Dann folgen Details zum Aufbau der Seite und zu der Frage, wie die SPA mit dem AEM-SPA-Editor in Beziehung steht und interagiert.

Ziel der vorliegenden Einführung und exemplarischen Anleitung ist es, einem AEM-Entwickler zu demonstrieren, warum SPAs relevant sind, wie sie grundsätzlich funktionieren, wie SPAs vom AEM-SPA-Editor gehandhabt werden und wie sie sich von einem standardmäßigen AEM-Programm unterscheiden.

## Voraussetzungen {#requirements}

Die exemplarische Anleitung basiert auf AEM-Standardfunktionen und der beispielhaften WKND SPA Project-App. Um dieser schrittweisen Anleitung zu folgen, müssen Sie über Folgendes verfügen.

* [AEM Version 6.5.4 oder neuer](/help/release-notes/release-notes.md)
   * Sie müssen über Administratorrechte für das System verfügen.
* [Die Beispiel-Anwendung des WKND SPA-Projekts ist auf GitHub verfügbar](https://github.com/adobe/aem-guides-wknd-spa)
   * Laden Sie die [neueste Version der React-Anwendung herunter.](https://github.com/adobe/aem-guides-wknd-spa/releases) Sie wird ähnlich benannt wie `wknd-spa-react.all.classic-X.Y.Z-SNAPSHOT.zip`.
   * Laden Sie die [neuesten Beispielbilder](https://github.com/adobe/aem-guides-wknd-spa/releases) für die Anwendung herunter. Sie wird ähnlich benannt wie `wknd-spa-sample-images-X.Y.Z.zip`.
   * [Verwenden Sie den Package Manager](/help/sites-administering/package-manager.md), um die Pakete zu installieren, wie Sie es mit jedem anderen Paket in AEM tun würden.
   * Für die Zwecke dieser schrittweisen Anleitung muss die Anwendung nicht mit Maven installiert werden.

>[!CAUTION]
>
>Dieses Dokument verwendet die [WKND Spa Project-Anwendung](https://github.com/adobe/aem-guides-wknd-spa) nur zu Demonstrationszwecken. Sie sollte nicht für Projektaufgaben verwendet werden.
>
>Jedes AEM-Projekt sollte den [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) nutzen, der SPA-Projekte mit React oder Angular unterstützt und das SPA-SDK nutzt.

### Was ist eine SPA? {#what-is-a-spa}

Eine Einzelseitenanwendung (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

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

1. Bearbeiten Sie die WKND-SPA-Projekt-App in AEM.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

   ![Schritt 1](assets/spa-walkthrough-step-1.png)

1. Wählen Sie eine Überschriftkomponente aus und beachten Sie, dass wie bei jeder anderen Komponente eine Symbolleiste angezeigt wird. Wählen Sie **Bearbeiten** aus.

   ![Schritt 2](assets/spa-walkthrough-step-2.png)

1. Bearbeiten Sie den Inhalt in AEM wie gewohnt und beachten Sie, dass die Änderungen beibehalten werden.

   ![Schritt 3](assets/spa-walkthrough-step-3.png)

   >[!NOTE]
   >
   >Weitere Informationen zum integrierten Texteditor und SPAs finden Sie unter [SPA-Editor – Übersicht](spa-overview.md#requirements-limitations) für.

1. Verwenden Sie den Assets-Browser, um ein neues Bild in eine Bildkomponente zu ziehen.

   ![Schritt 4](assets/spa-walkthrough-step-4.png)

1. Die Änderung wird beibehalten.

   ![Schritt 5](assets/spa-walkthrough-step-5.png)

Weitere Authoring-Werkzeuge wie das Ziehen und Ablegen zusätzlicher Komponenten auf der Seite, das Neuanordnen von Komponenten und das Ändern des Layouts werden wie in jeder Nicht-SPA-Anwendung unterstützt.

>[!NOTE]
>
>Der SPA-Editor ändert das DOM des Programms nicht. Die SPA selbst ist für das DOM verantwortlich.
>
>Um zu erfahren, wie das funktioniert, fahren Sie mit dem nächsten Abschnitt des Artikels [SPAs und der AEM-SPA-Editor](#spa-apps-and-the-aem-spa-editor) fort.

## SPAs und der AEM-SPA-Editor {#spa-apps-and-the-aem-spa-editor}

Wenn Sie wissen, wie sich eine SPA beim Endbenutzer verhält, und dann die SPA-Seite prüfen, können Sie besser verstehen, wie eine SAP-Anwendung mit dem SPA-Editor in AEM zusammenarbeitet.

### Verwenden einer SPA-Anwendung {#using-an-spa-application}

1. Laden Sie die WKND-SPA-Projekt-Anwendung entweder auf den Veröffentlichungs-Server oder mithilfe der Option **Als veröffentlicht anzeigen** im Menü **Seiteninformationen** des Seiteneditors.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Schritt 1](assets/spa-walkthrough-step-1-1.png)

   Beachten Sie die Seitenstruktur, einschließlich der Navigation zu untergeordneten Seiten, Wetter-Widget und Artikeln.

1. Navigieren Sie mithilfe des Menüs zu einer untergeordneten Seite und beachten Sie, dass die Seite sofort geladen wird, ohne dass eine Aktualisierung erforderlich ist.

   ![Schritt 2](assets/spa-walkthrough-step-1-2.png)

1. Öffnen Sie die integrierten Entwickler-Tools Ihres Browsers und überwachen Sie beim Navigieren durch die untergeordneten Seiten die Netzwerkaktivität.

   ![Schritt 3](assets/spa-walkthrough-step-1-3.png)

   Wenn Sie in der App von Seite zu Seite wechseln, ist der Traffic sehr gering. Die Seite wird nicht neu geladen; lediglich die neuen Bilder werden angefordert.

   Die SPA verwaltet Inhalt und Routing komplett auf der Client-Seite.

Wenn die Seite beim Navigieren durch die untergeordneten Seiten nicht neu geladen wird: Wie wird sie dann geladen?

Der nächste Abschnitt, [Laden einer SPA-Anwendung](#loading-an-spa-application), geht näher auf die Mechanismen des Ladens der SPA ein und beschreibt, wie Inhalte synchron und asynchron geladen werden können.

### Laden eines SPA-Programms {#loading-an-spa-application}

1. Laden Sie, falls noch nicht geschehen, die WKND-SPA-Projekt-Anwendung entweder auf den Veröffentlichungs-Server oder unter Verwendung der Option **Als veröffentlicht anzeigen** im Menü **Seiteninformationen** des Seiten-Editors.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Schritt 1](assets/spa-walkthrough-step-1-1.png)

1. Verwenden Sie das integrierte Tool Ihres Browsers, um die Quelle der Seiten anzuzeigen.
1. Beachten Sie, dass der Inhalt der Quelle sehr begrenzt ist.

   * Die Seite enthält im Hauptteil keine Inhalte. Sie besteht hauptsächlich aus Stylesheets und einem Aufruf an verschiedene Skripte wie `clientlib-react.min.js`.
   * Diese Skripte sind die Hauptelemente des Programms und für das Rendern sämtlicher Inhalte verantwortlich.

1. Nutzen Sie die integrierten Tools Ihres Browsers, um die Seite zu überprüfen. Sehen Sie sich den Inhalt des vollständig geladenen DOM an.

   ![Schritt 4](assets/spa-walkthrough-step-1-4.png)

1. Wechseln Sie zur Registerkarte **Netzwerk** der Entwickler-Tools und laden Sie die Seite neu.

   Beachten Sie beim Ignorieren von Bildanforderungen, dass die primären Ressourcen, die für die Seite geladen werden, die Seite selbst, CSS, das React-JavaScript, seine Abhängigkeiten sowie JSON-Daten für die Seite sind.

   ![Schritt 5](assets/spa-walkthrough-step-1-5.png)

1. Laden Sie `react.model.json` in einer neuen Registerkarte.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![Schritt 6](assets/spa-walkthrough-step-1-6.png)

   Der AEM-SPA-Editor nutzt [AEM Content Services](/help/assets/content-fragments/content-fragments.md), um den gesamten Inhalt der Seite als JSON-Modell bereitzustellen.

   Durch Implementierung spezifischer Schnittstellen stellen Sling-Modelle die für die SPA notwendigen Daten bereit. Die Bereitstellung der JSON-Daten wird nach unten an die jeweilige Komponente delegiert (von Seite zu Absatz zu Komponente usw.).

   Jede Komponente entscheidet, was sie verfügbar macht und wie sie gerendert wird (Server-seitig mit HTL oder Client-seitig mit React). In diesem Artikel geht es um das Client-seitige Rendering mit React.

1. Das Modell kann Seiten auch zusammen gruppieren, damit sie synchron geladen werden. Dadurch verringert sich die Zahl der erforderlichen Seitenneuladungen.

   Im Beispiel des WKND-SPA-Projekt-Programms werden die Seiten `home`, `page-1`, `page-2` und `page-3` synchron geladen, da Besucher in der Regel alle diese Seiten besuchen.

   Dieses Verhalten ist nicht obligatorisch und kann vollständig definiert werden.

   ![Schritt 7](assets/spa-walkthrough-step-1-7.png)

1. Um diesen Unterschied im Verhalten zu sehen, laden Sie die Seite neu und deaktivieren Sie die Netzwerkaktivität der Entwickler-Tools. Navigieren Sie im Seitenmenü zu `page-1` und vergewissern Sie sich, dass die einzige Netzwerkaktivität eine Anfrage nach dem Bild von `page-1` ist. `page-1` selbst muss nicht geladen werden.

   ![Schritt 8](assets/spa-walkthrough-step-1-8.png)

### Interaktion mit dem SPA-Editor {#interaction-with-the-spa-editor}

Mithilfe des exemplarischen WKND-SPA-Projekt-Programms wird deutlich, wie sich die App verhält und beim Veröffentlichen geladen wird. Dabei kommen Inhalts-Services für die JSON-Inhaltsbereitstellung sowie das asynchrone Laden von Ressourcen zum Einsatz.

Darüber hinaus ist die Inhaltserstellung mit einem SPA-Editor für den Inhaltsautor in AEM nahtlos.

Im folgenden Abschnitt werden wir uns den Vertrag ansehen, der es dem SPA-Editor erlaubt, Komponenten innerhalb der SPA mit AEM-Komponenten zu verbinden und so für ein nahtloses Bearbeitungserlebnis zu sorgen.

1. Laden Sie das WKND-SPA-Projekt-Programm im Editor und wechseln Sie in den **Vorschau**-Modus.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. Überprüfen Sie mithilfe der integrierten Entwickler-Tools Ihres Browsers den Inhalt der Seite. Wählen Sie mit dem Auswahl-Tool eine bearbeitbare Komponente auf der Seite aus und zeigen Sie die Elementdetails an.

   Beachten Sie, dass die Komponente über ein neues Datenattribut verfügt (`data-cq-data-path`).

   ![Schritt 2](assets/spa-walkthrough-step-2-2.png)

   Beispiel

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

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
