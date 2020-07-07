---
title: Konfigurieren von Layout-Container und Layout-Modus
seo-title: Konfigurieren von Layout-Container und Layout-Modus
description: Erfahren Sie, wie Sie Layout Container und Layoutmodus konfigurieren.
seo-description: Erfahren Sie, wie Sie Layout Container und Layoutmodus konfigurieren.
uuid: 952b7c86-76ab-4699-8530-8638e46bb50f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 10940000-808a-48ae-8e46-61eccef71eab
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 84%

---


# Konfigurieren von Layout-Container und Layout-Modus{#configuring-layout-container-and-layout-mode}

[Responsive Layout](/help/sites-authoring/responsive-layout.md) ist ein Mechanismus zum Realisieren von [reaktionsfähigem Webdesign](https://en.wikipedia.org/wiki/Responsive_web_design). Damit lassen sich Webseiten erstellen, deren Layout und Abmessungen von dem Gerät des Benutzers abhängen.

>[!NOTE]
>
>Dieser Ansatz ist vergleichbar mit den Mechanismen für [mobile Websites](/help/sites-developing/mobile-web.md), die adaptives Webdesign nutzen (in erster Linie für die klassische Benutzeroberfläche).

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente **](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

   Diese Komponente liefert ein Rasterabsatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Sie können sie als Standard-ParSys für Ihre Seite nutzen und/oder sie anderen Autoren im Komponenten-Browser zur Verfügung stellen.

   * The default **Layout Container** component is defined under:

      /libs/wcm/foundation/components/responsivegrid

   * Sie können Layout-Container wie folgt definieren:

      * als Komponente, die Benutzer zu einer Seite hinzufügen können
      * als Standard-ParSys für die Seite
      * Beide.

         Sie können den Layout-Container als Standard für die Seite festlegen und es den Benutzern gleichzeitig erlauben, weitere Layout-Container darin hinzuzufügen, z. B. für die Spaltensteuerung.

* **[Layoutmodus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**Sobald der Container des Layouts auf der Seite positioniert ist, können Sie den **Layoutmodus**verwenden, um den Inhalt im interaktiven Raster zu positionieren.
[**Emulator **](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)Hiermit können Sie responsive Websites erstellen und bearbeiten, deren Layout durch eine interaktive Größenanpassung der Komponenten an die Größe des Geräts oder Fensters angepasst wird. Der Benutzer kann sich mit dem Emulator ansehen wie der Inhalt für bestimmte Geräte gerendert wird.**

* [!CAUTION]**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)

>Auch wenn die **Layout-Container**-Komponente in der klassischen Benutzeroberfläche verfügbar ist, steht der vollständige Funktionsumfang nur in der Touch-optimierten Benutzeroberfläche zur Verfügung.
>
>Dieser responsive Rastermechanismus bietet folgende Möglichkeiten:****

Haltepunkte (die eine Gerätegruppierung anzeigen), um unterschiedliches Verhalten der Inhalte basierend auf dem Geräte-Layout zu definieren

* Ausblenden von Komponenten basierend auf der Gerätegruppe (definieren Sie, an welchem Haltepunkt eine Komponente ausgeblendet werden soll)
* Horizontale Ausrichtung am Raster (platzieren Sie Komponenten im Raster, passen Sie die Größe an, definieren Sie, wann ein Reduzieren/Umfließen daneben oder drüber/darunter stattfinden soll).
* Realisieren einer Spaltensteuerung.
* [!NOTE]

>Bei einer vorab konfigurierten Installation wurde das responsive Layout für die [We.Retail-Referenzwebsite](/help/sites-developing/we-retail.md) konfiguriert. Sie müssen [die Layout-Container-Komponente für andere Seiten nach wie vor aktivieren](#enable-the-layout-container-component-for-page).
>
>Konfigurieren des responsiven Emulators {#configuring-the-responsive-emulator}](/help/sites-developing/we-retail.md)[](#enable-the-layout-container-component-for-page)

## Mit diesen Aufgaben können Sie den responsiven **Emulator** auf Ihrer Website anzeigen.

Registrieren der Seitenkomponenten für die Emulation {#register-your-page-components-for-emulation}**

### Um die Emulator-Unterstützung für Ihre Seiten zu aktivieren, müssen Sie die Seitenkomponenten registrieren. Weitere Informationen finden Sie unter [Registrieren von Seitenkomponenten für die Simulation](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

Festlegen der Gerätegruppen {#specify-the-device-groups}](/help/sites-developing/responsive.md#registering-page-components-for-simulation)

### Informationen dazu, wie Sie die Gerätegruppen festlegen, die in der Geräteliste des Emulators angezeigt werden, finden Sie unter [Festlegen der Gerätegruppen](/help/sites-developing/responsive.md#specifying-the-device-groups).

Verknüpfen der Website mit den festgelegten Gerätegruppen {#link-your-site-to-the-specified-device-groups}](/help/sites-developing/responsive.md#specifying-the-device-groups)

### Um den Emulator einzubinden, müssen Sie die Website mit den Gerätegruppen verknüpfen. See [Adding the Devices List](/help/sites-developing/responsive.md#adding-the-devices-list) (for both the classic and touch-optimized UI).

Aktivieren des Layout-Modus für die Website {#activate-layout-mode-for-your-site}](/help/sites-developing/responsive.md#adding-the-devices-list)

## These procedures are used to enable the **Layout** mode on your site.

Konfigurieren der Haltepunkte {#configure-the-breakpoints}**

### [Haltepunkte](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

[werden bei responsiven Designs genutzt](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)

* können folgendermaßen definiert werden:
* auf der Seitenvorlage, von der die Einstellungen auf alle Seiten kopiert werden, die mit dieser Vorlage erstellt wurden

   * auf dem Seitenknoten, von dem die Einstellungen von allen untergeordneten Seiten geerbt werden
   * definieren einen Titel und eine Breite:

* Der Titel beschreibt die allgemeine Gerätegruppierung, bei Bedarf mit Ausrichtung; z. B. phone, tablet, tabletlandscape.

   * Die Breite definiert die Höchstbreite in Pixel für diese allgemeine Gerätegruppierung. Wenn beispielsweise der Haltepunkt „phone“ eine Breite von 768 hat, ist das die Höchstbreite des Layouts, das für ein Smartphone genutzt wird.
   * sind als Markierung oben auf dem Seiten-Editor sichtbar, wenn Sie den Emulator nutzen

* werden von der übergeordneten Knotenhierarchie geerbt und können beliebig überschrieben werden
* Es gibt einen standardmäßigen (vorab konfigurierten) Haltepunkt, der alles über dem letzten *konfigurierten* Haltepunkt abdeckt.
* Haltepunkte können Sie mit CRXDE Lite oder XML definieren.**

[!NOTE]

>[!NOTE]Wenn Sie ein neues Projekt einrichten:
>
>müssen Sie Haltepunkte zu den Vorlagen hinzufügen.
>
>* Wenn Sie ein vorhandenes Projekt (mit vorhandenen Inhalten) migrieren, müssen Sie:
>
>
Haltepunkte zu den Vorlagen hinzufügen
>
>* dieselben Haltepunkte zu vorhandenen Seiten hinzufügen
>* Da die Vererbung in Betrieb ist, können Sie diese auf die Stamm-Seite Ihres Inhalts beschränken.

>
>  
Konfigurieren von Haltepunkten mit CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

#### Wenn Sie CRXDE Lite (o. ä.) verwenden, navigieren Sie wahlweise zu einer der folgenden Optionen:{#configuring-breakpoints-using-crxde-lite}

1. der Vorlagendefinition

   * The `jcr:content` node of your page.
   * Under `jcr:content` create the node:

1. Name: `cq:responsive`

   * Typ: `nt:unstructured`
   * Erstellen Sie darunter den Knoten:`nt:unstructured`

1. Name: `breakpoints`

   * Typ: `nt:unstructured`
   * Unter dem Haltepunktknoten können Sie eine beliebige Anzahl an Haltepunkten erstellen. Jede Definition ist ein einziger Knoten mit den folgenden Eigenschaften:`nt:unstructured`

1. Name: `<descriptive name>`

   * Typ: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breite: `Decimal` * `<value of breakpoint>`*
   * Konfigurieren von Haltepunkten mit XML {#configuring-breakpoints-using-xml}`<value of breakpoint>`

#### Breakpoints are located inside the `<jcr:content>` section of the `.context.html` under the appropriate template (or content) folder.

Eine Beispieldefinition`<jcr:content>``.context.html`

Hinzufügen eines responsiven Informationsanbieters {#add-a-responsive-information-provider}

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### [!NOTE]

>[!NOTE]Dies ist nur erforderlich, wenn die Seitenkomponente nicht auf der Foundation-Seitenkomponente basiert.
>
>Kopieren Sie die folgende `cq:infoProviders`-Knotenstruktur in die übergeordnete Seitenkomponente:

`/libs/foundation/components/page/cq:infoProviders/responsive`

Aktivieren der Größenänderung von Komponenten für die Seite {#enable-component-resizing-for-the-page}

## These procedures are required so you can resize components in the **Layout** mode.

Festlegen des Layout-Containers als Haupt-ParSys {#set-layout-container-as-main-parsys}**

### Um einen Layout-Container als Haupt-ParSys einer Seite festzulegen, müssen Sie das ParSys wie folgt definieren:{#set-layout-container-as-main-parsys}

`wcm/foundation/components/responsivegrid`

`wcm/foundation/components/responsivegrid`Wahlweise in der:

Seitenkomponente

* Seitenvorlage (für die zukünftige Verwendung)
* Die folgenden beiden Beispiele veranschaulichen die Definition:

**HTL:**

* **JSP:**

   ```xml
   <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
   ```

* Einschließen von responsivem CSS {#include-the-responsive-css}**

   ```
   <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
   ```

### CSS für Haltepunkte mit LESS {#css-for-breakpoints-using-less}

#### AEM nutzt LESS, um Teile des erforderlichen CSS zu erstellen. Sie müssen für Ihre Projekte eingeschlossen sein.{#css-for-breakpoints-using-less}

Sie müssen auch eine [Client-Bibliothek[#$tu99] erstellen, um zusätzliche Konfigurationen und Funktionsaufrufe bereitzustellen. Der folgende LESS-Ausschnitt ist ein Beispiel für den Code, den Sie mindestens zu Ihrem Projekt hinzufügen müssen:



```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

Überlegungen zum Stil {#styling-considerations}

#### Die Größe von Komponenten in einem responsiven Container (und ihren entsprechenden HTML-DOM-Elementen) wird gemäß der Größe des responsiven Rasters geändert. Daher empfehlen wir in diesen Fällen, Definitionen von (enthaltenen) DOM-Elementen mit fester Breite zu vermeiden (oder zu aktualisieren).{#styling-considerations}

Beispiel:

Vorher:

* `width=100px`

   * `width=100px`Nachher:

* `max-width=100px`

   * Größenänderung und adaptive Bild-Compliance {#resizing-and-adaptive-image-compliance}

#### Jede Änderung der Größe einer Komponente innerhalb des Rasters löst mindestens einen der folgende Listener aus:{#resizing-and-adaptive-image-compliance}

`beforeedit`

* `beforechildedit`
* `afteredit`
* `afterchildedit`

* To properly resize and update the content of an adaptive image included in a responsive grid, you need to add an `afterEdit` set to `REFRESH_PAGE` listener into the `EditConfig` file of every contained component.

Beispiel:`afterEdit``REFRESH_PAGE``EditConfig`

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`Der adaptive Bildmechanismus wird über ein Skript bereitgestellt, das die Auswahl des korrekten Bildes für die aktuelle Fenstergröße steuert. Es wird aktiviert, wenn das DOM bereit ist oder ein dediziertes Ereignis empfangen wird. Zurzeit muss die Seite aktualisiert werden, um das Ergebnis der Benutzeraktion korrekt widerzuspiegeln.

[!CAUTION]

>[!CAUTION]Benutzerdefinierte Stylesheet-clientlibs müssen als Teil der Kopfzeile geladen werden, damit sie sowohl beim Autor als auch bei der Veröffentlichung ordnungsgemäß funktionieren.
>
>Aktivieren der Layout-Container-Komponente für die Seite {#enable-the-layout-container-component-for-page}

## Mit den folgenden Aufgaben können Autoren Instanzen der **Layout-Container**-Komponente auf die Seite verschieben.

Aktivieren der Layout-Container-Komponente für die Seitenbearbeitung {#enable-the-layout-container-component-for-page-editing}**

### Um es Autoren zu erlauben, weitere responsive Raster zu den Inhaltsseiten hinzuzufügen, müssen Sie die Layout-Container-Komponente für Ihre Seite hinzufügen. Möglich ist dies über folgende Optionen:{#enable-the-layout-container-component-for-page-editing}

**Autorenumgebung**

* Aktivieren Sie im [Design-Modus](/help/sites-authoring/default-components-designmode.md) die **Layout-Container**-Komponente für eine Seite.

   **Komponentendefinition******

* Nutzen Sie beim Definieren der Komponente `allowedComponent` oder ein Static Include.**

   Konfigurieren des Rasters des Layout-Containers {#configure-the-grid-of-the-layout-container}

### Sie können die Anzahl an Spalten konfigurieren, die für jede spezifische Instanz des Layout-Containers verfügbar sind:{#configure-the-grid-of-the-layout-container}

**Autorenumgebung**

1. **Sie können die Anzahl an Spalten konfigurieren, die für jede spezifische Instanz des Layout-Containers verfügbar sind.**

   Öffnen Sie dazu im [Design-Modus](/help/sites-authoring/default-components-designmode.md) das Design-Dialogfeld für den betroffenen Container. Hier können Sie festlegen, wie viele Spalten für die Positionierung und Größeneinstellung vorhanden sein sollen. Standard: 12.

   **XML**

1. **Die Definitionen für das responsive Raster werden in folgender Datei festgelegt:**

   `etc/design/<*your-project-name*>/.content.xml`

   `etc/design/<*your-project-name*>/.content.xml`Sie können die folgenden Parameter festlegen:

   Anzahl an verfügbaren Spalten:

   * `columns="{String}8"`

      * `columns="{String}8"`Komponenten, die zur aktuellen Komponente hinzugefügt werden können:
   * `components="[/libs/wcm/foundation/components/responsivegrid, ...`

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`


