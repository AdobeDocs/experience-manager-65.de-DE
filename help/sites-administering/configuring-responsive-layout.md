---
title: Konfigurieren von Layout-Container und Layout-Modus
seo-title: Konfigurieren von Layout-Container und Layout-Modus
description: Erfahren Sie, wie Sie Layout-Container und Layout-Modus konfigurieren.
seo-description: Erfahren Sie, wie Sie Layout-Container und Layout-Modus konfigurieren.
uuid: 952b7c86-76ab-4699-8530-8638e46bb50f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 10940000-808a-48ae-8e46-61eccef71eab
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
exl-id: 61152b2d-4c0b-4cfd-9669-cf03d32cb7c7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 84%

---

# Konfigurieren von Layout-Container und Layout-Modus{#configuring-layout-container-and-layout-mode}

[Responsives ](/help/sites-authoring/responsive-layout.md) Layout ist ein Mechanismus zur Realisierung von  [responsivem Webdesign](https://en.wikipedia.org/wiki/Responsive_web_design). Damit lassen sich Webseiten erstellen, deren Layout und Abmessungen von dem Gerät des Benutzers abhängen.

>[!NOTE]
>
>Dieser Ansatz ist vergleichbar mit den Mechanismen für [mobile Websites](/help/sites-developing/mobile-web.md), die adaptives Webdesign nutzen (in erster Linie für die klassische Benutzeroberfläche).

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

   Diese Komponente liefert ein Rasterabsatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Sie können sie als Standard-ParSys für Ihre Seite nutzen und/oder sie anderen Autoren im Komponenten-Browser zur Verfügung stellen.

   * Die Standardkomponente **Layout-Container** wird definiert unter:

      /libs/wcm/foundation/components/responsivegrid

   * Sie können Layout-Container wie folgt definieren:

      * als Komponente, die Benutzer zu einer Seite hinzufügen können
      * als Standard-ParSys für die Seite
      * Beide.

         Sie können den Layout-Container als Standard für die Seite festlegen und es den Benutzern gleichzeitig erlauben, weitere Layout-Container darin hinzuzufügen, z. B. für die Spaltensteuerung.

* **[Layout-](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
ModusSobald der Layout-Container auf der Seite positioniert ist, können Sie die 
**** Layout-Modus zum Positionieren von Inhalt im responsiven Raster.

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Hiermit können Sie responsive Websites erstellen und bearbeiten, deren Layout durch eine interaktive Größenanpassung der Komponenten an die Größe des Geräts oder Fensters angepasst wird. Der Benutzer kann sich mit dem Emulator ansehen wie der Inhalt für bestimmte Geräte gerendert wird.

>[!CAUTION]
>
>Auch wenn die **Layout-Container**-Komponente in der klassischen Benutzeroberfläche verfügbar ist, steht der vollständige Funktionsumfang nur in der Touch-optimierten Benutzeroberfläche zur Verfügung.

Dieser responsive Rastermechanismus bietet folgende Möglichkeiten:

* Haltepunkte (die eine Gerätegruppierung anzeigen), um unterschiedliches Verhalten der Inhalte basierend auf dem Geräte-Layout zu definieren
* Ausblenden von Komponenten basierend auf der Gerätegruppe (definieren Sie, an welchem Haltepunkt eine Komponente ausgeblendet werden soll)
* Horizontale Ausrichtung am Raster (platzieren Sie Komponenten im Raster, passen Sie die Größe an, definieren Sie, wann ein Reduzieren/Umfließen daneben oder drüber/darunter stattfinden soll).
* Realisieren einer Spaltensteuerung.

>[!NOTE]
>
>Bei einer vorab konfigurierten Installation wurde das responsive Layout für die [We.Retail-Referenzwebsite](/help/sites-developing/we-retail.md) konfiguriert. Sie müssen [die Layout-Container-Komponente für andere Seiten nach wie vor aktivieren](#enable-the-layout-container-component-for-page).

## Konfigurieren des responsiven Emulators {#configuring-the-responsive-emulator}

Mit diesen Aufgaben können Sie den responsiven **Emulator** auf Ihrer Website anzeigen.

### Registrieren der Seitenkomponenten für die Emulation {#register-your-page-components-for-emulation}

Um die Emulator-Unterstützung für Ihre Seiten zu aktivieren, müssen Sie die Seitenkomponenten registrieren. Weitere Informationen finden Sie unter [Registrieren von Seitenkomponenten für die Simulation](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Festlegen der Gerätegruppen  {#specify-the-device-groups}

Informationen dazu, wie Sie die Gerätegruppen festlegen, die in der Geräteliste des Emulators angezeigt werden, finden Sie unter [Festlegen der Gerätegruppen](/help/sites-developing/responsive.md#specifying-the-device-groups).

### Verknüpfen der Website mit den festgelegten Gerätegruppen  {#link-your-site-to-the-specified-device-groups}

Um den Emulator einzubinden, müssen Sie die Website mit den Gerätegruppen verknüpfen. Siehe [Hinzufügen der Geräteliste](/help/sites-developing/responsive.md#adding-the-devices-list) (für die klassische und die Touch-optimierte Benutzeroberfläche).

## Aktivieren des Layout-Modus für die Website {#activate-layout-mode-for-your-site}

Diese Verfahren werden verwendet, um den Modus **Layout** auf Ihrer Site zu aktivieren.

### Konfigurieren der Haltepunkte {#configure-the-breakpoints}

[Haltepunkte](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* werden bei responsiven Designs genutzt
* können folgendermaßen definiert werden:

   * auf der Seitenvorlage, von der die Einstellungen auf alle Seiten kopiert werden, die mit dieser Vorlage erstellt wurden
   * auf dem Seitenknoten, von dem die Einstellungen von allen untergeordneten Seiten geerbt werden

* definieren einen Titel und eine Breite:

   * Der Titel beschreibt die allgemeine Gerätegruppierung, bei Bedarf mit Ausrichtung; z. B. phone, tablet, tabletlandscape.
   * Die Breite definiert die Höchstbreite in Pixel für diese allgemeine Gerätegruppierung. Wenn beispielsweise der Haltepunkt „phone“ eine Breite von 768 hat, ist das die Höchstbreite des Layouts, das für ein Smartphone genutzt wird.

* sind als Markierung oben auf dem Seiten-Editor sichtbar, wenn Sie den Emulator nutzen
* werden von der übergeordneten Knotenhierarchie geerbt und können beliebig überschrieben werden
* Es gibt einen standardmäßigen (vorab konfigurierten) Haltepunkt, der alles über dem letzten *konfigurierten* Haltepunkt abdeckt.

Haltepunkte können Sie mit CRXDE Lite oder XML definieren.

>[!NOTE]
>
>Wenn Sie ein neues Projekt einrichten:
>
>* müssen Sie Haltepunkte zu den Vorlagen hinzufügen.
>
>
Wenn Sie ein vorhandenes Projekt (mit vorhandenen Inhalten) migrieren, müssen Sie:
>
>* Haltepunkte zu den Vorlagen hinzufügen
>* dieselben Haltepunkte zu vorhandenen Seiten hinzufügen

>
>  
Da die Vererbung ausgeführt wird, können Sie dies auf die Stammseite Ihres Inhalts beschränken.

#### Konfigurieren von Haltepunkten mit CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Wenn Sie CRXDE Lite (o. ä.) verwenden, navigieren Sie wahlweise zu einer der folgenden Optionen:

   * der Vorlagendefinition
   * Der Knoten `jcr:content` Ihrer Seite.

1. Erstellen Sie unter `jcr:content` den Knoten:

   * Name: `cq:responsive`
   * Typ: `nt:unstructured`

1. Erstellen Sie darunter den Knoten:

   * Name: `breakpoints`
   * Typ: `nt:unstructured`

1. Unter dem Haltepunktknoten können Sie eine beliebige Anzahl an Haltepunkten erstellen. Jede Definition ist ein einziger Knoten mit den folgenden Eigenschaften:

   * Name: `<descriptive name>`
   * Typ: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breite: `Decimal` * `<value of breakpoint>`*

#### Konfigurieren von Haltepunkten mit XML {#configuring-breakpoints-using-xml}

Haltepunkte befinden sich im Abschnitt `<jcr:content>` des Ordners `.context.html` unter der entsprechenden Vorlage (oder dem entsprechenden Inhaltsordner).

Eine Beispieldefinition

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Hinzufügen eines responsiven Informationsanbieters  {#add-a-responsive-information-provider}

>[!NOTE]
>
>Dies ist nur erforderlich, wenn die Seitenkomponente nicht auf der Foundation-Seitenkomponente basiert.

Kopieren Sie die folgende `cq:infoProviders`-Knotenstruktur in die übergeordnete Seitenkomponente:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Aktivieren der Größenänderung von Komponenten für die Seite {#enable-component-resizing-for-the-page}

Diese Verfahren sind erforderlich, damit Sie die Größe von Komponenten im Modus **Layout** ändern können.

### Festlegen des Layout-Containers als Haupt-ParSys {#set-layout-container-as-main-parsys}

Um einen Layout-Container als Haupt-ParSys einer Seite festzulegen, müssen Sie das ParSys wie folgt definieren:

`wcm/foundation/components/responsivegrid`

Wahlweise in der:

* Seitenkomponente
* Seitenvorlage (für die zukünftige Verwendung)

Die folgenden beiden Beispiele veranschaulichen die Definition:

* **HTL:**

   ```xml
   <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
   ```

* **JSP:**

   ```
   <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
   ```

### Einschließen von responsivem CSS {#include-the-responsive-css}

#### CSS für Haltepunkte mit LESS {#css-for-breakpoints-using-less}

AEM nutzt LESS, um Teile des erforderlichen CSS zu erstellen. Sie müssen für Ihre Projekte eingeschlossen sein.

Sie müssen auch eine [Client-Bibliothek](https://docs.adobe.com/content/docs/en/aem/6-0/develop/the-basics/clientlibs.html) erstellen, um zusätzliche Konfigurationen und Funktionsaufrufe bereitzustellen. Der folgende LESS-Ausschnitt ist ein Beispiel für den Code, den Sie mindestens zu Ihrem Projekt hinzufügen müssen:

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

Die Basisrasterdefinition finden Sie unter:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Überlegungen zum Stil {#styling-considerations}

Die Größe von Komponenten in einem responsiven Container (und ihren entsprechenden HTML-DOM-Elementen) wird gemäß der Größe des responsiven Rasters geändert. Daher empfehlen wir in diesen Fällen, Definitionen von (enthaltenen) DOM-Elementen mit fester Breite zu vermeiden (oder zu aktualisieren).

Beispiel:

* Vorher:

   * `width=100px`

* Nachher:

   * `max-width=100px`

#### Größenänderung und adaptive Bild-Compliance {#resizing-and-adaptive-image-compliance}

Jede Änderung der Größe einer Komponente innerhalb des Rasters löst mindestens einen der folgende Listener aus:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Um die Größe eines adaptiven Bildes in einem responsiven Raster korrekt zu ändern und zu aktualisieren, müssen Sie einen `afterEdit`-Listener hinzufügen, der auf `REFRESH_PAGE` gesetzt ist, und ihn in die `EditConfig`-Datei jeder enthaltenen Komponente einfügen.

Beispiel:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Der adaptive Bildmechanismus wird über ein Skript bereitgestellt, das die Auswahl des korrekten Bildes für die aktuelle Fenstergröße steuert. Es wird aktiviert, wenn das DOM bereit ist oder ein dediziertes Ereignis empfangen wird. Zurzeit muss die Seite aktualisiert werden, um das Ergebnis der Benutzeraktion korrekt widerzuspiegeln.

>[!CAUTION]
>
>Benutzerdefinierte Stylesheet-Client-Bibliotheken müssen als Teil der Kopfzeile geladen werden, damit sie sowohl auf der Autoren- als auch auf der Veröffentlichungsinstanz ordnungsgemäß funktionieren.

## Aktivieren der Layout-Container-Komponente für die Seite {#enable-the-layout-container-component-for-page}

Mit den folgenden Aufgaben können Autoren Instanzen der **Layout-Container**-Komponente auf die Seite verschieben.

### Aktivieren der Layout-Container-Komponente für die Seitenbearbeitung  {#enable-the-layout-container-component-for-page-editing}

Um es Autoren zu erlauben, weitere responsive Raster zu den Inhaltsseiten hinzuzufügen, müssen Sie die Layout-Container-Komponente für Ihre Seite hinzufügen. Möglich ist dies über folgende Optionen:

* **Autorenumgebung**

   Aktivieren Sie im [Design-Modus](/help/sites-authoring/default-components-designmode.md) die **Layout-Container**-Komponente für eine Seite.

* **Komponentendefinition**

   Nutzen Sie beim Definieren der Komponente `allowedComponent` oder ein Static Include.

### Konfigurieren des Rasters des Layout-Containers {#configure-the-grid-of-the-layout-container}

Sie können die Anzahl an Spalten konfigurieren, die für jede spezifische Instanz des Layout-Containers verfügbar sind:

1. **Autorenumgebung**

   Sie können die Anzahl an Spalten konfigurieren, die für jede spezifische Instanz des Layout-Containers verfügbar sind.

   Öffnen Sie dazu im [Design-Modus](/help/sites-authoring/default-components-designmode.md) das Design-Dialogfeld für den betroffenen Container. Hier können Sie festlegen, wie viele Spalten für die Positionierung und Größeneinstellung vorhanden sein sollen. Standard: 12.

1. **XML**

   Die Definitionen für das responsive Raster werden in folgender Datei festgelegt:

   `etc/design/<*your-project-name*>/.content.xml`

   Sie können die folgenden Parameter festlegen:

   * Anzahl an verfügbaren Spalten:

      * `columns="{String}8"`
   * Komponenten, die zur aktuellen Komponente hinzugefügt werden können:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`
