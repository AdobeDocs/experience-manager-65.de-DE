---
title: Authoring – Umgebung und Tools in AEM
description: Die Authoring-Umgebung von AEM bietet verschiedene Mechanismen für das Organisieren und Bearbeiten von Inhalten.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 3b3c118b-ca35-484b-a62e-7bec98953123
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2246'
ht-degree: 100%

---

# Bearbeiten: Umgebung und Tools{#authoring-the-environment-and-tools}

Die Autorenumgebung von AEM bietet verschiedene Mechanismen für das Organisieren und Bearbeiten von Inhalten. Die verfügbaren Tools können über verschiedene Konsolen und Seiteneditoren aufgerufen werden.

## Verwalten Ihrer Site {#managing-your-site}

Die **Sites**-Konsole bietet Ihnen die Möglichkeit, auf Ihrer Website zu navigieren und diese zu verwalten. Hierfür stehen neben der Kopfzeilen- und Symbolleiste auch Aktionssymbole (für die jeweils ausgewählte Ressource) sowie Breadcrumbs und ggf. sekundäre Leisten (z. B. Timeline und Verweise) zur Verfügung.

Zum Beispiel in der Spaltenansicht:

![ateat-01](assets/ateat-01.png)

## Bearbeiten des Seiteninhalts {#editing-page-content}

Sie können eine Seite mit dem Seiteneditor bearbeiten. Zum Beispiel:

`https://localhost:4502/editor.html/content/we-retail/us/en/equipment.html`

![ateat-02](assets/ateat-02.png)

>[!NOTE]
>
>Wenn Sie eine Seite zum ersten Mal zur Bearbeitung öffnen, werden Sie in einer Bildschirmpräsentation durch die Funktionen geführt.
>
>Sie können diese Tour überspringen und jederzeit wiederholen, indem Sie sie im Menü **Seiteninformationen** auswählen.

## Aufrufen der Hilfe   {#accessing-help}

Wenn Sie eine Seite bearbeiten, können Sie folgendermaßen auf die **Hilfe** zugreifen:

* über den Selektor [**Seiteninformationen**](/help/sites-authoring/editing-page-properties.md#page-properties); dieser zeigt die Einführungsfolien an (wie beim erstmaligen Zugriff auf den Editor).
* über das [Konfigurationsdialogfeld](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) bei bestimmten Komponenten (mithilfe des Symbols „?“ in der Symbolleiste des Dialogfelds), das die kontextsensitive Hilfe anzeigt.

In den Konsolen stehen weitere [Hilferessourcen zur Verfügung](/help/sites-authoring/basic-handling.md#accessing-help).

## Komponenten-Browser {#components-browser}

Der Komponenten-Browser enthält alle Komponenten, die zur Verwendung auf der aktuellen Seite verfügbar sind. Sie können diese an die gewünschte Position ziehen und dann bearbeiten, um Inhalte hinzuzufügen.

Der Komponenten-Browser befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) und der [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree)). Um das seitliche Bedienfeld zu öffnen bzw. zu schließen, verwenden Sie das Symbol links oben in der Symbolleiste:

![ateat-03](assets/ateat-03.png)

Wenn Sie das seitliche Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie hier ggf. die Registerkarte **Komponenten**. Wenn es geöffnet ist, können Sie alle für Ihre Seite verfügbaren Komponenten durchsuchen.

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite weniger als 1024 Pixel beträgt. Dies kann auch bei einem kleinen Desktop-Fenster der Fall sein.

* **Mobilgerät (z. B. iPad)**

  Der Komponenten-Browser deckt die gesamte Seite ab, die bearbeitet wird.

  Um der Seite eine Komponente hinzuzufügen, berühren und halten Sie die gewünschte Komponente und verschieben Sie sie nach rechts. Der Komponenten-Browser wird geschlossen und die Seite wird erneut angezeigt. Sie können die Komponente jetzt dort platzieren.

  ![ateat-04](assets/ateat-04.png)

* **Desktop-Gerät**

  Der Komponenten-Browser wird auf der linken Seite des Fensters geöffnet.

  Um der Seite eine Komponente hinzuzufügen, klicken Sie auf die gewünschte Komponente und ziehen Sie sie an die gewünschte Position.

  ![ateat-05](assets/ateat-05.png)

  Komponenten werden wie folgt dargestellt:

   * Komponentenname
   * Komponentengruppe (in grau)
   * Symbol oder Abkürzung

      * Die Symbole für die Standardkomponenten sind monochrom dargestellt.
      * Für die Abkürzungen werden immer die ersten zwei Buchstaben des Komponentennamens verwendet.

  Die obere Symbolleiste des **Komponenten**-Browsers bietet folgende Möglichkeiten:

   * Komponenten nach Namen filtern
   * Mittels Dropdown-Auswahl die Anzeige auf eine bestimmte Gruppe begrenzen

  Wenn Sie auf das Informationssymbol neben der Komponente im **Komponenten**-Browser klicken, finden Sie eine detailliertere Beschreibung der Komponente (falls verfügbar). Beispiel für den **Layout-Container**:

  ![ateat-06](assets/ateat-06.png)

  Weitere Informationen zu den verfügbaren Komponenten finden Sie unter [Komponenten-Konsole](/help/sites-authoring/default-components-console.md).

## Asset-Browser {#assets-browser}

Der Asset-Browser enthält alle [Assets](/help/assets/assets.md), die auf Ihrer aktuellen Seite direkt verwendet werden können.

Der Asset-Browser befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) und der [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree)). Um das seitliche Bedienfeld zu öffnen bzw. zu schließen, verwenden Sie das Symbol links oben in der Symbolleiste:

![ateat-03-1](assets/ateat-03-1.png)

Wenn Sie das seitliche Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie ggf. die Registerkarte **Assets**.

![ateat-07](assets/ateat-07.png)

Wenn der Asset-Browser geöffnet ist, können Sie alle für die Seite verfügbaren Assets durchsuchen. Bei Bedarf können Sie die Liste durch Scrollen unendlich erweitern.

![ateat-08](assets/ateat-08.png)

Um ein Asset zu der Seite hinzuzufügen, wählen Sie es aus und ziehen Sie es an die gewünschte Position. Dabei kann es sich um Folgendes handeln:

* Eine vorhandene Komponente des entsprechenden Typs.

   * Sie können beispielsweise ein Asset des Typs „Bild“ auf eine Bildkomponente ziehen.

* Ein [Platzhalter](/help/sites-authoring/editing-content.md#component-placeholder) im Absatzsystem zum Erstellen einer Komponente des entsprechenden Typs.

   * Sie können beispielsweise ein Asset des Typs „Bild“ in das Absatzsystem ziehen, um eine Bildkomponente zu erstellen.

>[!NOTE]
>
>Dies ist für spezielle Assets und Komponententypen verfügbar. Weitere Einzelheiten finden Sie unter [Einfügen einer Komponente mit dem Asset-Browser](/help/sites-authoring/editing-content.md#inserting-a-component-using-the-assets-browser).

In der Symbolleiste des Asset-Browsers können Sie Assets nach folgenden Kriterien filtern:

* Name
* Pfad
* Asset-Typ, z. B. Bilder, Manuskripte, Dokumente, Videos, Seiten, Absätze oder Produkte
* Asset-Merkmale, z. B. Ausrichtung (Hochformat, Querformat, quadratisch) und Stil (farbig, monochrom, Graustufen)

   * Nur für bestimmte Asset-Typen verfügbar

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite geringer als 1024 Pixel ist, d. h. auch bei einem kleinen Desktop-Fenster.

* **Mobilgerät, z. B. iPad**

  Der Asset-Browser deckt die gesamte bearbeitete Seite ab.

  Um der Seite ein Asset hinzuzufügen, berühren und halten Sie das gewünschte Asset und verschieben Sie es nach rechts. Der Asset-Browser wird geschlossen und die Seite wird erneut angezeigt. Jetzt können Sie das Asset der gewünschten Komponente hinzufügen.

  ![ateat-09](assets/ateat-09.png)

* **Desktop-Gerät**

  Der Asset-Browser wird auf der linken Seite des Fensters geöffnet.

  Um ein Asset zu Ihrer Seite hinzuzufügen, klicken Sie auf das gewünschte Asset und ziehen Sie es auf die benötigte Komponente oder Stelle.

  ![ateat-10](assets/ateat-10.png)

Wenn Sie schnell eine Änderung an einem Asset vornehmen möchten, können Sie den [Asset-Editor](/help/assets/manage-assets.md) auch direkt über den Asset-Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen.

![Assets-Browser-Desktop-Gerät](do-not-localize/screen_shot_2018-03-22at142448.png)

## Inhaltsstruktur {#content-tree}

Die **Inhaltsstruktur** bietet einen Überblick über alle auf der Seite verwendeten Komponenten in einer hierarchischen Darstellung, sodass Sie direkt feststellen können, wie die Seite aufgebaut ist.

Die Inhaltsstruktur befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem Asset-Browser). Um das seitliche Bedienfeld zu öffnen bzw. zu schließen, verwenden Sie das Symbol links oben in der Symbolleiste:

![Inhaltsstruktur](do-not-localize/screen_shot_2018-03-22at142042.png)

Wenn Sie das seitliche Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie ggf. die Registerkarte **Inhaltsstruktur** aus. Mit dieser Strukturansicht Ihrer Seite oder Vorlage können Sie leicht nachvollziehen, wie die darauf verwendeten Komponenten hierarchisch strukturiert sind. Auf einer komplexer gestalteten Seite können Sie so zudem einfacher zwischen Komponenten auf der Seite wechseln.

![ateat-11](assets/ateat-11.png)

Da eine Seite häufig zahlreiche Komponenten desselben Typs enthält, wird in der Komponentenstruktur (Inhalt) neben dem Namen des Komponententyps (schwarz dargestellt) zusätzlich eine Beschreibung angezeigt (grau dargestellt). Der Text für diese Beschreibung wird aus den allgemeinen Eigenschaften der Komponente (z. B. Titel oder Text) entnommen.

Die Komponententypen werden in der Benutzersprache angezeigt, während der Text der Komponentenbeschreibung aus der Seitensprache stammt.

Durch Klicken auf den Pfeil neben einer Komponente wird die entsprechende Ebene ein- bzw. ausgeblendet.

![screen_shot_2018-03-22at142559](assets/screen_shot_2018-03-22at142559.png)

>[!NOTE]
>
>Beim Bearbeiten einer Seite auf einem Mobilgerät ist die Inhaltsstruktur nicht verfügbar (wenn die Browser-Breite weniger als 1.024 Pixel beträgt).

Durch Klicken auf die Komponente wird diese im Seiten-Editor markiert. Die verfügbaren Aktionen hängen vom Status der Seite ab:

* Zum Beispiel bei einer einfachen Seite:

  `https://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html`

  ![ateat-12](assets/ateat-12.png)

  Wenn die Komponente, auf die Sie in der Struktur klicken, bearbeitbar ist, erscheint ein Schraubenschlüssel-Symbol rechts neben dem Namen. Durch Klicken auf dieses Symbol wird das Dialogfeld „Bearbeiten“ für die Komponente geöffnet.

  ![Schraubenschlüsselsymbol – Bearbeiten](do-not-localize/screen_shot_2018-03-22at142725.png)

* Oder bei einer Seite, die Teil einer [Live Copy](/help/sites-administering/msm.md) ist, wobei Komponenten von einer anderen Seite übernommen werden, zum Beispiel

  `https://localhost:4502/editor.html/content/we-retail/us/en/equipment.html`

  ![ateat-13](assets/ateat-13.png)

## Fragmente: Browser für zugehörige Inhalte {#fragments-associated-content-browser}

Wenn Ihre Seite Inhaltsfragmente enthält, haben Sie auch Zugriff auf den [Browser für zugehörige Inhalte](/help/sites-authoring/content-fragments.md#using-associated-content).

## Verweise {#references}

**Verweise** zeigen Verbindungen zur ausgewählten Seite an:

* Blueprints
* Launches
* Live Copies
* Sprachkopien
* Eingehende Links
* Verwendung der Referenzkomponente: geliehener und verliehener Inhalt
* Verweise auf Produktseiten (auf der Konsole „E-Commerce - Produkte“)

Öffnen Sie die gewünschte Konsole, navigieren Sie zur gewünschten Ressource und öffnen Sie **Verweise** wie folgt:

![screen_shot_2018-03-22at153653](assets/screen_shot_2018-03-22at153653.png)

[Wählen Sie die gewünschte Ressource](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) zeigt eine Liste von Verweistypen, die für diese Ressource relevant sind:

![ateat-22](assets/ateat-22.png)

Wählen Sie den gewünschten Verweistyp, um weitere Informationen anzuzeigen. In bestimmten Situationen sind weitere Aktionen verfügbar, wenn Sie einen bestimmten Verweis auswählen, z. B.:

* **Eingehende Links** enthält eine Liste der Seiten, die auf die Seite verweisen, und bietet direkten Zugriff zum **Bearbeiten** einer dieser Seiten, wenn Sie einen bestimmten Link auswählen. 

   * Es können nur statische Links angezeigt werden, nicht dynamisch generierte Links, z. B. aus der Listenkomponente.

* Instanzen von geliehenen und verliehenen Inhalten, die die **Referenz**-Komponente verwenden. Sie können von hier aus zur referenzierten Seite navigieren.

* [Verweise auf Produktseiten](/help/commerce/cif-classic/administering/generic.md#showing-product-references) (verfügbar in der Konsole „E-Commerce - Produkte“)
* [Launches](/help/sites-authoring/launches.md) bietet Zugriff auf zugehörige Launches.
* [Live Copys](/help/sites-administering/msm.md) zeigt die Pfade aller Live Copys an, die auf der gewählten Ressource basieren.
* [Blueprint](/help/sites-administering/msm-best-practices.md) bietet Details und verschiedene Aktionen.
* [Sprachkopien](/help/sites-administering/tc-manage.md#creating-translation-projects-using-the-references-panel) bietet Details und verschiedene Aktionen.

Sie können beispielsweise einen beschädigten Verweis innerhalb einer Verweiskomponente reparieren:

![ateat-14](assets/ateat-14.png)

## Ereignisse: Timeline {#events-timeline}

Bei bestimmten Ressourcen (z. B. Seiten aus der **Sites**-Konsole oder Assets aus der **Asset**-Konsole) kann die [Timeline dazu verwendet werden, die zuletzt durchgeführten Aktivitäten für ausgewählte Elemente anzuzeigen](/help/sites-authoring/basic-handling.md#timeline).

Öffnen Sie die gewünschte Konsole, navigieren Sie zur gewünschten Ressource und öffnen Sie die **Timeline** wie folgt:

![ateat-15](assets/ateat-15.png)

[Wählen Sie die gewünschte Ressource ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)und danach entweder **Alle anzeigen** oder **Aktivitäten** aus, um die mit den ausgewählten Ressourcen zuletzt ausgeführten Aktionen aufzulisten:

![ateat-16](assets/ateat-16.png)

## Seiteninformationen {#page-information}

Mit der Schaltfläche „Seiteninformationen“ (Equalizer-Symbol) öffnen Sie ein Menü, das auch Details zur letzten Bearbeitung und zur letzten Aktivierung enthält. Abhängig von den Eigenschaften der Seite (und der Website, zu der sie gehört) sind u. U. weitere Optionen verfügbar:

![ateat-17](assets/ateat-17.png)

* [Eigenschaften öffnen](/help/sites-authoring/editing-page-properties.md)
* [Seiten-Rollout](/help/sites-administering/msm.md#msm-from-the-ui)
* [Workflow starten](/help/sites-authoring/workflows-applying.md#starting-a-workflow-from-the-page-editor)
* [Sperren einer Seite](/help/sites-authoring/editing-content.md#locking-a-page)
* [Seite veröffentlichen](/help/sites-authoring/publishing-pages.md#main-pars-title-10)
* [Veröffentlichen einer Seite aufheben](/help/sites-authoring/publishing-pages.md#main-pars-title-5)
* [Vorlage bearbeiten](/help/sites-authoring/templates.md), wenn die Seite auf einer [bearbeitbaren Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates) basiert.

* [Als veröffentlicht anzeigen](/help/sites-authoring/editing-content.md#view-as-published)
* „In Admin anzeigen“ öffnet die Seite in der [Sites-Konsole](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)
* [Hilfe](/help/sites-authoring/basic-handling.md#accessing-help)

Zum Beispiel hat **Seiteninformation** gegebenenfalls auch die Optionen:

* [Launch bewerben](/help/sites-authoring/launches-promoting.md), wenn die Seite ein Launch ist
* [In klassischer Benutzeroberfläche öffnen](/help/sites-authoring/select-ui.md#switching-to-classic-ui-when-editing-a-page), wenn diese Option [von einer bzw. einem Admin aktiviert](/help/sites-administering/enable-classic-ui-editor.md) wurde

Darüber hinaus können über die **Seiteninformationen** ggf. auch Analysen und Empfehlungen aufgerufen werden.

## Seitenmodi {#page-modes}

Für die Bearbeitung von Seiten stehen verschiedene Modi zur Verfügung, über die jeweils unterschiedliche Aktionen durchgeführt werden können:

* [Bearbeiten](/help/sites-authoring/editing-content.md): Verwenden Sie diesen Modus zum Bearbeiten des Seiteninhalts.
* [Layout](/help/sites-authoring/responsive-layout.md): Ermöglicht es Ihnen, Ihr responsives Layout gerätespezifisch zu erstellen und zu bearbeiten (wenn die Seite auf einem Layout-Container basiert).

* [Strukturvorlage](/help/sites-authoring/scaffolding.md): Hilft Ihnen bei der Erstellung einer großen Anzahl von Seiten, die unterschiedliche Inhalte, aber eine einheitliche Struktur aufweisen sollen.
* [Entwicklung](/help/sites-developing/developer-mode.md): Ermöglicht die Durchführung verschiedener Aktionen (erfordert Berechtigungen). Dazu gehört die Überprüfung der technischen Details einer Seite und ihrer Komponenten.

* [Design](/help/sites-authoring/default-components-designmode.md): Ermöglicht es Ihnen, Komponenten für die Verwendung auf einer Seite zu aktivieren bzw. zu deaktivieren und das Design der Komponente zu konfigurieren (wenn die Seite auf einer [statischen Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates) basiert).

* [Zielsetzung:](/help/sites-authoring/content-targeting-touch.md) Steigerung der Inhaltsrelevanz durch Zielsetzung und Messung über alle Kanäle hinweg.
* [Activity Map:](/help/sites-authoring/page-analytics-using.md#analyticsvisiblefromthepageeditor) Zeigt Analytics-Daten für die Seite an.

* [Timewarp](/help/sites-authoring/working-with-page-versions.md#timewarp): Ermöglicht es, eine Seite in dem Zustand anzuzeigen, den sie zu einem bestimmten früheren Zeitpunkt aufgewiesen hat.
* [Live Copy-Status:](/help/sites-authoring/editing-content.md#live-copy-status): Für einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen oder nicht übernommen wurden.
* [Vorschau](/help/sites-authoring/editing-content.md#previewing-pages): Dient zur Anzeige der Darstellung der Seite in der Veröffentlichungsumgebung oder zur Navigation anhand der Links im Inhalt.

* [Anmerken](/help/sites-authoring/annotations.md): In diesem Modus können Sie Anmerkungen auf der Seite hinzufügen oder anzeigen.

Sie können darauf über die Symbole oben rechts zugreifen. Das Symbol ändert sich entsprechend dem derzeit verwendeten Modus:

![ateat-18](assets/ateat-18.png)

>[!NOTE]
>
>* Je nach den Merkmalen der Seite sind einige Modi ggf. nicht verfügbar.
>* Für den Zugriff auf einige Modi sind die entsprechenden Berechtigungen erforderlich.
>* Aus Platzgründen steht der Entwicklungsmodus auf Mobilgeräten nicht zur Verfügung.
>* Mit einem [Tastaturbefehl](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) (`Ctrl-Shift-M`) können Sie zwischen der **Vorschau** und dem aktuell ausgewählten Modus (**Bearbeiten**, **Layout** usw.) hin- und herwechseln.
>

## Pfadauswahl {#path-selection}

Oft muss bei der Bearbeitung einer Seite eine andere Ressource ausgewählt werden (z. B. zum Definieren eines Links zu einer anderen Seite/Ressource oder zum Auswählen eines Bilds). Zur Vereinfachung der Pfadauswahl werden Eingaben in den [Pfad-Feldern](/help/sites-authoring/author-environment-tools.md#path-fields) automatisch ausgefüllt. Ergänzend dazu stehen zudem leistungsstarke Auswahlfunktionen im [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) zur Verfügung.

### Pfadfelder {#path-fields}

Im vorliegenden Beispiel wird zur Verdeutlichung die Bildkomponente verwendet. Weitere Informationen zur Verwendung und Bearbeitung von Komponenten finden Sie unter [Komponenten für die Seitenbearbeitung](/help/sites-authoring/default-components.md).

Die Pfadfelder bieten jetzt auch automatisches Ausfüllen und Vorausschau auf Eingaben, um die Suche nach Ressourcen zu vereinfachen.

Durch Klicken auf die Schaltfläche **Auswahl-Dialogfeld öffnen** auf dem Pfadfeld wird das Dialogfeld [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) geöffnet, in dem Optionen für eine präzisere Auswahl zur Verfügung stehen.

![Auswahl-Dialogfeld öffnen](do-not-localize/screen_shot_2018-03-22at154427.png)

Alternativ können Sie etwas in das Pfadfeld eingeben und AEM schlägt Ihrer Eingabe entsprechend passende Pfade vor.

![ateat-19](assets/ateat-19.png)

### Pfad-Browser {#path-browser}

Der Pfad-Browser ist wie die [Spaltenansicht](/help/sites-authoring/basic-handling.md#column-view) der Sites-Konsole aufgebaut und ermöglicht eine präzisere Auswahl der Ressourcen.

![screen_shot_2018-03-22at154521](assets/screen_shot_2018-03-22at154521.png)

* Wenn eine Ressource ausgewählt wird, wird die Schaltfläche **Auswählen** oben rechts im Dialogfeld aktiviert. Klicken Sie, um die Auswahl zu bestätigen, oder wählen Sie zum Aufheben der Auswahl die Option **Abbrechen** aus.
* Wenn der Kontext die Auswahl mehrerer Ressourcen zulässt, wird bei Auswahl einer Ressource auch die Schaltfläche **Auswählen** aktiviert, aber auch die Anzahl der ausgewählten Ressourcen wird oben rechts im Fenster angezeigt. Klicken Sie auf das **X** neben der Zahl, um die Auswahl für alle aufzuheben.
* Wenn Sie durch den Baum navigieren, wird Ihre Position in den Breadcrumbs am oberen Rand des Dialogfelds angezeigt. Mithilfe der Breadcrumbs können Sie innerhalb der Ressourcenhierarchie schnell von einem Punkt zu einem anderen wechseln.
* Sie können auch jederzeit das Suchfeld oben im Dialogfeld verwenden. Klicken Sie im Suchfeld auf **X**, wenn Sie die Suche löschen möchten.
* Sie können Ihre Suche auch eingrenzen, indem Sie die Filteroptionen einblenden und die Ergebnisse nach Pfad filtern.

  ![ateat-21](assets/ateat-21.png)

## Tastaturbefehle {#keyboard-shortcuts}

Für die Bedienung stehen verschiedene [Tastaturbefehle](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) zur Verfügung.
