---
title: Responsives Layout
seo-title: Responsives Layout
description: AEM bietet Ihnen die Möglichkeit, Ihre Seiten mit einem responsiven Layout zu gestalten.
seo-description: AEM bietet Ihnen die Möglichkeit, Ihre Seiten mit einem responsiven Layout zu gestalten.
uuid: 4db45d78-9fca-4251-b504-ae3481fd9a8b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 668d1a8a-c757-4c9f-833f-e5dada4d0384
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Responsives Layout{#responsive-layout}

AEM ermöglicht das Erstellen eines responsiven Layouts für Ihre Seiten mithilfe der Komponente **Layout-Container**.

Dieses liefert ein Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Dieses Raster kann das Layout abhängig von der Größe des Geräts/Fensters und des Formats neu anordnen. The component is used in conjunction with the [**Layout **mode](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode), which allows you to create and edit your responsive layout dependent on device.

Der Layout-Container:

* Bietet horizontales Ausrichten am Raster zusammen mit der Möglichkeit Komponenten im Raster nebeneinander zu platzieren und zu definieren wann ein Reduzieren/Umfließen stattfinden soll.
* Verwendet vordefinierte Breakpoints (z. B. für Smartphones, Tablets usw.), sodass Sie das erforderliche Verhalten des Inhalts für ähnliche Geräte/Ausrichtungen definieren können.

   * Sie können z. B. die Größe der Komponente anpassen oder festlegen, ob die Komponente auf bestimmten Geräten sichtbar ist.

* Kann für die Spaltensteuerung verschachtelt werden.

Der Benutzer kann sich mit dem Emulator ansehen, wie der Inhalt für bestimmte Geräte gerendert wird.

>[!CAUTION]
>
>Auch wenn die Layout-Container-Komponente in der klassischen Benutzeroberfläche verfügbar ist, steht der vollständige Funktionsumfang nur in der Touch-optimierten Benutzeroberfläche zur Verfügung.

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Komponente &quot;Layout-Container **](#adding-a-layout-container-and-its-content-edit-mode)&quot;

   This component is available in the [component browser](/help/sites-authoring/author-environment-tools.md#components-browser) and provides a grid-paragraph system to allow you to add and position components within a responsive grid. Dieses kann auf Ihrer Seite auch als Standardabsatzsystem festgelegt werden.

* [**Layout-Modus **](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)

   Once the layout container is positioned on your page you can use the **Layout** mode to position content within the responsive grid.

* [**Emulator **](#selecting-a-device-to-emulate)Hiermit können Sie responsive Websites erstellen und bearbeiten, deren Layout durch eine interaktive Größenanpassung der Komponenten an die Größe des Geräts oder Fensters angepasst wird. Der Benutzer kann sich dann mit dem Emulator ansehen, wie der Inhalt für bestimmte Geräte gerendert wird.

Dieser responsive Rastermechanismus bietet folgende Möglichkeiten:

* Verwendung von Breakpoints zur Definition verschiedener Inhaltslayouts basierend auf der Gerätebreite (nach Gerätetyp und -ausrichtung).
* Verwendung derselben Breakpoints und Inhaltslayouts, um sicherzustellen, dass Ihr Inhalt an die Größe des Browserfensters auf dem Desktop angepasst wird.
* Mit der horizontalen Ausrichtung am Raster können Sie Komponenten im Raster platzieren, die Größe anpassen und definieren, wann ein Reduzieren/Umfließen daneben oder drüber/darunter erfolgen soll.
* Ausblenden von Komponenten für bestimmte Gerätelayouts.
* Realisieren einer Spaltensteuerung.

Je nach Projekt kann der Layout-Container als Standard-Absatzsystem für Ihre Seiten oder als Komponente verwendet werden, die über den Komponenten-Browser (oder beide) zu Ihrer Seite hinzugefügt werden kann.

>[!NOTE]
>
>Adobe provides [GitHub documentation](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) of the responsive layout as a reference that can be given to front-end developers allowing them to use the AEM grid outside of AEM, for example when creating static HTML mock-ups for a future AEM site.

>[!NOTE]
>
>Die Verwendung des obigen Mechanismus wird durch die Konfiguration der Vorlage aktiviert. See [Configuring Responsive Layout](/help/sites-administering/configuring-responsive-layout.md) for further information.

## Layout-Definitionen, Geräteemulation und Breakpoints {#layout-definitions-device-emulation-and-breakpoints}

Wenn Sie den Inhalt Ihrer Website erstellen, möchten Sie sicherstellen, dass Ihr Inhalt auf dem für die Anzeige verwendeten Gerät angemessen angezeigt wird.

AEM ermöglicht die Definition von Layouts, die von der Breite des Geräts abhängig sind:

* Mit dem Emulator können Sie diese Layouts auf verschiedenen Geräten emulieren. In addition to the device type, the orientation, selected by the **Rotate device** option, can impact the breakpoint selected as the width changes.
* Breakpoints sind Punkte, die die Layout-Definitionen trennen.

   * Sie definieren die maximale Breite (in Pixel) der Geräte, die ein bestimmtes Layout verwenden.
   * Breakpoints gelten in der Regel für eine Auswahl an Geräten und hängen von der Breite der Displays ab.
   * Ein Breakpoint reicht nach links bis zum nächsten Breakpoint.
   * Sie können den Breakpoint nicht spezifisch auswählen - durch die Auswahl eines Geräts und einer Ausrichtung wird der entsprechende Breakpoint automatisch ausgewählt.

Das Gerät **Desktop**, das keine bestimmte Breite aufweist und sich auf den Standard-Breakpoint bezieht (d. h. auf alles über dem letzten konfigurierten Breakpoint).

>[!NOTE]
>
>Es wäre möglich, Breakpoints für jedes einzelne Gerät zu definieren. Dies würde jedoch den Aufwand für die Layout-Definition und die Wartung deutlich erhöhen.

Wenn Sie mit dem Emulator ein bestimmtes zu emulierendes Gerät und die Layout-Definition auswählen, wird auch der zugehörige Breakpoint hervorgehoben. Alle von Ihnen durchgeführten Änderungen am Layout wirken sich auch auf andere Geräte aus, für die derselbe Breakpoint gilt – also auf alle links vom aktiven Breakpoint bis zum nächsten Breakpoint platzierten Geräte.

Wenn Sie z. B. das Gerät **iPhone 6 Plus** für die Emulation und das Layout auswählen (das mit einer Breite von 540 Pixel definiert ist), wird auch der Breakpoint **Telefon** (768 Pixel) aktiviert. Alle Änderungen am Layout, die Sie für das **iPhone 6** durchführen, gelten auch für die anderen Geräte unter dem Breakpoint **Telefon**, wie das **iPhone 5** (mit 320 Pixel definiert).

![screen_shot_2018-03-23at084058](assets/screen_shot_2018-03-23at084058.png)

## Selecting a Device to Emulate {#selecting-a-device-to-emulate}

1. Öffnen Sie die gewünschte Seite für die Bearbeitung. Beispiel:

   `http://localhost:4502/editor.html/content/we-retail/us/en/experience.html`

1. Wählen Sie auf der oberen Symbolleiste das Symbol **Emulator** aus:

   ![](do-not-localize/screen_shot_2018-03-23at084256.png)

1. Die Emulator-Symbolleiste wird geöffnet.

   ![screen_shot_2018-03-23at084551](assets/screen_shot_2018-03-23at084551.png)

   In der Emulator-Symbolleiste werden zusätzliche Layout-Optionen angezeigt:

   * **Gerät drehen** – Ermöglicht es Ihnen, die vertikale Ausrichtung (Hochformat) eines Geräts in eine horizontale Ausrichtung (Querformat) zu ändern und umgekehrt.
   ![](do-not-localize/screen_shot_2018-03-23at084612.png) ![](do-not-localize/screen_shot_2018-03-23at084637.png)

   * **Gerät auswählen** – Ermöglicht es Ihnen, ein bestimmtes Gerät anzugeben, das aus einer Liste emuliert werden soll (Einzelheiten dazu werden im nächsten Schritt beschrieben).
   ![](do-not-localize/screen_shot_2018-03-23at084743.png)

1. Um ein bestimmtes Gerät für das Emulieren auszuwählen, können Sie wie folgt vorgehen:

   * Wählen Sie über das Symbol „Gerät auswählen“ eine Option aus der Dropdown-Liste aus.
   * Tippen/klicken Sie auf der Emulator-Symbolleiste auf das Gerätezeichen.
   ![screen_shot_2018-03-23at084818](assets/screen_shot_2018-03-23at084818.png)

1. Nachdem Sie ein bestimmtes Gerät ausgewählt haben, sind folgende Möglichkeiten verfügbar:

   * See the active marker for the selected device, such as **iPad.**
   * See the active marker for the appropriate [breakpoint](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints) such as **Tablet.**
   ![screen_shot_2018-03-23at084932](assets/screen_shot_2018-03-23at084932.png)

   * Die gepunktete blaue Linie stellt den *Falz* für das ausgewählte Gerät dar (in diesem Fall ein **iPhone 6**).
   ![screen_shot_2018-03-23at084947](assets/screen_shot_2018-03-23at084947.png)

   * Dabei handelt es sich um eine Art Seitenumbruch für den Inhalt (nicht zu verwechseln mit den [Breakpoints](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints)). Dies wird zur Vereinfachung angezeigt, um zu veranschaulichen, welchen Teil des Inhalts der Benutzer vor dem Bildlauf auf dem Gerät sehen wird.
   * Die Linie für den Falz wird nicht angezeigt, wenn die Höhe des zu emulierenden Geräts die Bildschirmgröße überschreitet.
   * Der Falz wird aus Komfortgründen für Autoren, aber nicht auf der veröffentlichten Seite angezeigt.



## Adding a Layout Container and its Content (Edit mode) {#adding-a-layout-container-and-its-content-edit-mode}

Ein **Layout-Container** ist ein Absatzsystem mit folgenden Eigenschaften:

* Enthält andere Komponenten.
* Definiert das Layout.
* Reagiert auf Änderungen.

>[!NOTE]
>
>Falls er noch nicht verfügbar ist, muss der **Layout-Container** explizit [für ein Absatzsystem/eine Seite aktiviert werden](/help/sites-administering/configuring-responsive-layout.md) (z. B. über den [**Designmodus **](/help/sites-authoring/default-components-designmode.md)).

1. Der **Layout-Container**[ ist als Standardkomponente im Komponenten-Browser verfügbar](/help/sites-authoring/author-environment-tools.md#components-browser). Von hier können Sie ihn an die gewünschte Position auf der Seite ziehen. Danach wird der Platzhalter **Komponenten hierher ziehen** angezeigt.
1. Anschließend können Sie Komponenten zum Layout-Container hinzufügen. Diese Komponenten enthalten dann den eigentlichen Inhalt:

   ![screen_shot_2018-03-23at085500](assets/screen_shot_2018-03-23at085500.png)

## Auswählen und Bearbeiten eines Layout-Containers (Bearbeitungsmodus) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Einen Layout-Container können Sie wie andere Komponenten im **Bearbeitungsmodus** auswählen und anschließend bearbeiten (ausschneiden, kopieren, löschen):

>[!CAUTION]
>
>Da ein Layout-Container ein Absatzsystem ist, werden beim Löschen der Komponente sowohl das Layout-Raster als auch sämtliche im Container vorhandenen Komponenten und deren Inhalte gelöscht.

1. Wenn Sie den Mauszeiger über den Rasterplatzhalter halten oder darauf tippen, wird das Aktionsmenü angezeigt.

   ![screen_shot_2018-03-23at085357](assets/screen_shot_2018-03-23at085357.png)

   You need to select the **Parent** option.

   ![](do-not-localize/screen_shot_2018-03-23at085417.png)

1. Wenn die Layout-Komponente verschachtelt ist, wird durch Auswählen der Option **Übergeordnetes Element** eine Dropdown-Liste geöffnet, über die Sie den verschachtelten Layout-Container oder seine übergeordneten Elemente auswählen können.

   Wenn Sie den Mauszeiger im Dropdown-Menü über die Container-Namen halten, wird ihre Gliederung auf der Seite angezeigt.

   * Der am wenigsten verschachtelte Layout-Container ist schwarz dargestellt.
   * Der nächste Layout-Container ist dunkelgrau dargestellt.
   * Alle folgenden Container sind in jeweils helleren Grautönen dargestellt.
   ![screen_shot_2018-03-23at085636](assets/screen_shot_2018-03-23at085636.png)

1. Dadurch wird das gesamte Raster mit den Inhalten markiert. The action toolbar will be shown, from where you can select an action such as **Delete.**

   ![screen_shot_2018-03-23at085724](assets/screen_shot_2018-03-23at085724.png)

## Definieren von Layouts (Layout-Modus) {#defining-layouts-layout-mode}

>[!NOTE]
>
>Sie können für jeden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) (der durch den emulierten Gerätetyp und die Ausrichtung bestimmt wird) ein eigenes Layout definieren.

To configure the layout of a responsive grid implemented with the Layout Container you need to use the **Layout** mode.

Der **Layout**-Modus kann auf zwei Arten aktiviert werden.

* By using the [mode menu in the toolbar](/help/sites-authoring/author-environment-tools.md#page-modes) and choosing **Layout** mode

   * Select the **Layout** mode just as you would switch to **Edit** mode or **Targeting** mode.
   * **Der Layoutmodus** bleibt erhalten und Sie verlassen den **Layoutmodus** erst, wenn Sie über die Modusauswahl einen anderen Modus auswählen.

* Beim [Bearbeiten einer einzelnen Komponente](/help/sites-authoring/editing-content.md#edit-component-layout)

   * Durch Verwenden der Option **Layout** im Schnellaktionsmenü der Komponente können Sie in den **Layout**-Modus wechseln.
   * Der **Layout**-Modus wird zunächst automatisch beibehalten, während Sie die Komponente bearbeiten. Sobald Sie den Fokus auf eine andere Komponente richten, kehren Sie in den **Bearbeitungsmodus** zurück.

Im Layout-Modus können Sie verschiedene Aktionen für ein Raster durchführen:

* Passen Sie die Größe der Inhaltskomponenten mithilfe der blauen Punkte an. Die Größenanpassung wird immer am Raster ausgerichtet. Während der Größenanpassung wird im Hintergrund das Raster sichtbar, das die Ausrichtung erleichtert:

   ![screen_shot_2018-03-23at090140](assets/screen_shot_2018-03-23at090140.png)

   >[!NOTE]
   >
   >Wenn Sie die Größe von Komponenten wie **Bildern** ändern, bleiben die Proportionen und Seitenverhältnisse erhalten.

* Wenn Sie auf eine Inhaltskomponente klicken/tippen, bietet Ihnen die Symbolleiste folgende Möglichkeiten:

   * **Übergeordnet**

      Ermöglicht die Auswahl der gesamten Layout-Container-Komponente zum Durchführen von Aktionen.

   * **Gleitkommawert in neue Zeile**

      Die Komponente wird je nach dem im Raster verfügbaren Platz in eine neue Zeile verschoben.

   * **Komponente ausblenden**

      Die Komponente wird unsichtbar gemacht (sie kann über die Symbolleiste des Layout-Containers wiederhergestellt werden).
   ![screen_shot_2018-03-23at090246](assets/screen_shot_2018-03-23at090246.png)

* In **Layout** mode you can tap/click on the **Drag components here** to select the entire component. Dadurch wird die Symbolleiste für diesen Modus angezeigt.

   Die Symbolleiste weist je nach Status der Layout-Komponente und zugehörigen Komponenten verschiedene Optionen auf. Beispiel:

   * **Übergeordnet** - Wählen Sie die übergeordnete Komponente aus.
   ![](do-not-localize/screen_shot_2018-03-23at090823.png)

   * **Ausgeblendete Komponenten** anzeigen: Alle oder einzelne Komponenten anzeigen. Die Zahl gibt an, wie viele ausgeblendete Komponenten es derzeit gibt. Der Zähler zeigt an, wie viele Komponenten ausgeblendet sind.
   ![](do-not-localize/screen_shot_2018-03-23at091007.png)

   * **Haltepunktlayout** wiederherstellen - Zurückkehren zum Standardlayout. Das bedeutet, dass kein benutzerdefiniertes Layout festgelegt wird.
   ![](do-not-localize/screen_shot_2018-03-23at091013.png)

   * **In neue Zeile** schwenken - Komponente nach oben verschieben, wenn Abstände dies zulassen.
   ![screen_shot_2018-03-23at090829](assets/screen_shot_2018-03-23at090829.png)

   * **Komponente** ausblenden: Blenden Sie die aktuelle Komponente aus.
   ![](do-not-localize/screen_shot_2018-03-23at090834.png)

   >[!NOTE]
   >
   >Im obigen Beispiel sind die Aktionen zum Verschieben und Ausblenden verfügbar, weil dieser Layout-Container in einem übergeordneten Layout-Container verschachtelt ist.

   * **Komponenten einblenden** – Ermöglicht das Auswählen der übergeordneten Komponenten, um die Aktionssymbolleiste mit der Option **Verborgene Komponenten einblenden** anzuzeigen. In diesem Beispiel gibt es zwei ausgeblendete Komponenten. 
   ![screen_shot_2018-03-23at091200](assets/screen_shot_2018-03-23at091200.png)

   Bei Auswahl der Option **Verborgene Komponenten einblenden** werden die jeweils ausgeblendeten Komponenten in Blau an ihren ursprünglichen Positionen angezeigt.

   ![screen_shot_2018-03-23at091224](assets/screen_shot_2018-03-23at091224.png)

   Bei Auswahl der Option **Alle wiederherstellen** werden alle verborgenen Komponenten eingeblendet.

