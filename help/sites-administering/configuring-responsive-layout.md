---
title: Konfigurieren von Layout-Container und Layout-Modus
seo-title: Configuring Layout Container and Layout Mode
description: Erfahren Sie, wie Sie Layout-Container und den Layout-Modus konfigurieren.
seo-description: Learn how to configure Layout Container and Layout Mode.
uuid: 952b7c86-76ab-4699-8530-8638e46bb50f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 10940000-808a-48ae-8e46-61eccef71eab
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
exl-id: 61152b2d-4c0b-4cfd-9669-cf03d32cb7c7
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 37%

---

# Konfigurieren von Layout-Container und Layout-Modus{#configuring-layout-container-and-layout-mode}

Ein [responsives Layout](/help/sites-authoring/responsive-layout.md) ist eine Methode, um ein [responsives Webdesign](https://de.wikipedia.org/wiki/Responsive_Webdesign) zu realisieren. Damit lassen sich Web-Seiten erstellen, deren Layout und Abmessungen von dem Gerät des Benutzers abhängen.

>[!NOTE]
>
>Dieser Ansatz ist vergleichbar mit den Mechanismen für [mobile Websites](/help/sites-developing/mobile-web.md), die adaptives Webdesign nutzen (in erster Linie für die klassische Benutzeroberfläche).

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

   Diese Komponente liefert ein Rasterabsatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Sie können sie als Standard-ParSys für Ihre Seite nutzen und/oder sie anderen Autoren im Komponenten-Browser zur Verfügung stellen.

   * Die standardmäßige **Layout-Container**-Komponente ist definiert unter:

      /libs/wcm/foundation/components/responsivegrid

   * Sie können Layout-Container definieren:

      * Als Komponente, die der Benutzer einer Seite hinzufügen kann.
      * Als Standard-ParSys für die Seite.
      * Beide.

         Sie können den Layout-Container als Standard für die Seite festlegen und es den Benutzern gleichzeitig erlauben, weitere Layout-Container darin hinzuzufügen, z. B. für die Spaltensteuerung.

* **[Layout-Modus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
Sobald der Layout-Container auf Ihrer Seite positioniert ist, können Sie den 
**Layout**-Modus verwenden, um Inhalte im responsiven Raster zu positionieren.

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Auf diese Weise können Sie responsive Websites erstellen und bearbeiten, die das Layout durch interaktive Größenanpassung der Komponenten an die Geräte-/Fenstergröße anpassen. Der Benutzer kann dann sehen, wie der Inhalt mit dem Emulator wiedergegeben wird.

>[!CAUTION]
>
>Obwohl die Variable **Layout-Container** -Komponente in der klassischen Benutzeroberfläche verfügbar ist, ist die vollständige Funktionalität nur in der Touch-optimierten Benutzeroberfläche verfügbar.

Mit diesen responsiven Rastermechanismen können Sie:

* Verwenden Sie Haltepunkte (die die Gerätegruppierung angeben), um je nach Gerätelayout ein unterschiedliches Inhaltsverhalten zu definieren.
* Ausblenden von Komponenten basierend auf Gerätegruppen (definieren Sie, an welchem Haltepunkt eine Komponente ausgeblendet wird).
* Verwenden Sie die horizontale Ausrichtung am Raster (platzieren Sie Komponenten in das Raster, passen Sie die Größe an, definieren Sie, wann sie nebeneinander oder darüber/darunter reduziert/umfließen sollen).
* Realisieren einer Spaltensteuerung.

>[!NOTE]
>
>Bei einer vorab konfigurierten Installation wurde das responsive Layout für die [We.Retail-Referenzwebsite](/help/sites-developing/we-retail.md) konfiguriert. Sie müssen [die Layout-Container-Komponente für andere Seiten nach wie vor aktivieren](#enable-the-layout-container-component-for-page).

## Konfigurieren des responsiven Emulators {#configuring-the-responsive-emulator}

Mit diesen Aufgaben können Sie den responsiven **Emulator** auf Ihrer Website anzeigen.

### Registrieren Ihrer Seitenkomponenten für die Emulation {#register-your-page-components-for-emulation}

Damit der Emulator Ihre Seiten unterstützen kann, müssen Sie die Seitenkomponenten registrieren. Siehe [Registrieren von Seitenkomponenten für die Simulation](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Gerätegruppen angeben {#specify-the-device-groups}

Informationen zum Festlegen der Gerätegruppen, die in der Liste &quot;Geräte&quot;des Emulators angezeigt werden, finden Sie unter [Festlegen der Gerätegruppen](/help/sites-developing/responsive.md#specifying-the-device-groups).

### Verknüpfen Ihrer Site mit den angegebenen Gerätegruppen {#link-your-site-to-the-specified-device-groups}

Um den Emulator einzuschließen, verknüpfen Sie Ihre Site mit den Gerätegruppen. Siehe [Hinzufügen der Geräteliste](/help/sites-developing/responsive.md#adding-the-devices-list) (für die klassische und die Touch-optimierte Benutzeroberfläche).

## Aktivieren des Layout-Modus für die Website {#activate-layout-mode-for-your-site}

Mit diesen Vorgängen wird der **Layout-Modus** auf Ihrer Website aktiviert.

### Konfigurieren der Haltepunkte {#configure-the-breakpoints}

[Haltepunkte](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* werden im responsiven Design verwendet.
* Kann definiert werden:

   * Auf der Seitenvorlage, von der aus die Einstellungen auf alle Seiten kopiert werden, die mit dieser Vorlage erstellt wurden.
   * Auf dem Seitenknoten, von dem aus die Einstellungen von untergeordneten Seiten übernommen werden.

* Definieren Sie einen Titel und eine Breite:

   * Der Titel beschreibt die generische Gerätegruppierung, gegebenenfalls mit Ausrichtung. z. B. Telefon, Tablet, Tabletlandscape.
   * Die Breite definiert die maximale Breite in Pixel für diese generische Gerätegruppierung. Wenn das Breakpoint-Telefon beispielsweise eine Breite von 768 hat, dann die maximale Breite des Layouts, das für ein Telefongerät verwendet wird.

* Sind als Markierungen am oberen Rand des Seiteneditors sichtbar, wenn Sie den Emulator verwenden.
* werden von der Hierarchie des übergeordneten Knotens übernommen und können beliebig überschrieben werden.
* Es gibt einen standardmäßigen (nativen) Breakpoint, der alles über dem letzten *konfiguriert* Haltepunkt.

Haltepunkte können Sie mit CRXDE Lite oder XML definieren.

>[!NOTE]
>
>Wenn Sie ein neues Projekt einrichten:
>
>* Fügen Sie Haltepunkte zu den Vorlagen hinzu.
>
>Wenn Sie ein vorhandenes Projekt (mit vorhandenem Inhalt) migrieren, müssen Sie:
>
>* Haltepunkte zu Vorlagen hinzufügen
>* dieselben Haltepunkte zu vorhandenen Seiten hinzufügen
>
>  Da die Vererbung im Einsatz ist, können Sie dies auf die Stammseite Ihrer Inhalte beschränken.

#### Konfigurieren von Haltepunkten mithilfe von CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Navigieren Sie mit der CRXDE Lite (oder einer entsprechenden Vorlage) zu einer der folgenden Optionen:

   * Ihre Vorlagendefinition.
   * dem Knoten `jcr:content` Ihrer Seite

1. Erstellen Sie unter `jcr:content` den Knoten:

   * Name: `cq:responsive`
   * Typ: `nt:unstructured`

1. Erstellen Sie darunter den Knoten:

   * Name: `breakpoints`
   * Typ: `nt:unstructured`

1. Unter dem Breakpoints-Knoten können Sie eine beliebige Anzahl von Haltepunkten erstellen. Jede Definition ist ein einzelner Knoten mit den folgenden Eigenschaften:

   * Name: `<descriptive name>`
   * Typ: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breite: `Decimal` * `<value of breakpoint>`*

#### Konfigurieren von Haltepunkten mit XML {#configuring-breakpoints-using-xml}

Haltepunkte befinden sich im Abschnitt `<jcr:content>` der Datei `.context.html` im entsprechenden Vorlagenorder (bzw. Inhaltsordner).

Eine Beispieldefinition:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Responsive Informationsanbieter hinzufügen {#add-a-responsive-information-provider}

>[!NOTE]
>
>Dies ist nur erforderlich, wenn die Seitenkomponente nicht auf der Foundation-Seitenkomponente basiert.

Kopieren Sie die folgende `cq:infoProviders`-Knotenstruktur in die übergeordnete Seitenkomponente:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Aktivieren der Größenänderung von Komponenten für die Seite {#enable-component-resizing-for-the-page}

Sie müssen diese Vorgänge durchführen, um die Größe von Komponenten im **Layout-Modus** zu ändern.

### Layout-Container als Haupt-Parsys festlegen {#set-layout-container-as-main-parsys}

Um festzulegen, dass die Haupt-ParSys Ihrer Seite ein Layout-Container sein sollen, definieren Sie die ParSys wie folgt:

`wcm/foundation/components/responsivegrid`

In beiden Fällen:

* Seitenkomponente
* Seitenvorlage (zur zukünftigen Verwendung)

Die folgenden beiden Beispiele veranschaulichen die Definition:

* **HTL:**

   ```xml
   <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
   ```

* **JSP:**

   ```
   <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
   ```

### Responsive CSS einschließen {#include-the-responsive-css}

#### CSS für Haltepunkte mit LESS {#css-for-breakpoints-using-less}

AEM verwendet LESS, um Teile des erforderlichen CSS zu generieren. Diese müssen für Ihre Projekte einbezogen werden.

Sie müssen auch eine [Client-Bibliothek](https://experienceleague.adobe.com/docs/?lang=de) , um zusätzliche Konfigurations- und Funktionsaufrufe bereitzustellen. Der folgende LESS-Extrakt ist ein Beispiel für das Minimum, das Sie zum Projekt hinzufügen müssen:

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

#### Überlegungen zur Formatierung {#styling-considerations}

Die Größe von Komponenten, die in einem responsiven Container gespeichert sind, wird (zusammen mit den entsprechenden HTML-DOM-Elementen) entsprechend der Größe des responsiven Rasters geändert. Daher wird unter diesen Umständen empfohlen, Definitionen von DOM-Elementen mit fester Breite (enthalten) zu vermeiden (oder zu aktualisieren).

Beispiel:

* Vorher:

   * `width=100px`

* Nachher:

   * `max-width=100px`

#### Größenanpassung und Adaptive Bildkompatibilität {#resizing-and-adaptive-image-compliance}

Bei jeder Größenänderung einer Komponente im Raster werden die folgenden Listener entsprechend Trigger:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Um die Größe eines adaptiven Bildes in einem responsiven Raster ordnungsgemäß zu ändern und die Inhalte des Bildes zu aktualisieren, müssen Sie den Listener `afterEdit`, dessen Wert auf `REFRESH_PAGE` festgelegt ist, zur `EditConfig`-Datei aller enthaltenen Komponenten hinzufügen.

Beispiel:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Der Mechanismus für adaptive Bilder wird über ein Skript zur Verfügung gestellt, das die Auswahl des richtigen Bildes für die aktuelle Fenstergröße steuert. Sie wird aktiviert, nachdem das DOM bereit ist oder wenn ein dediziertes Ereignis empfangen wird. Derzeit muss die Seite aktualisiert werden, um das Ergebnis der Benutzeraktion korrekt widerzuspiegeln.

>[!CAUTION]
>
>Benutzerdefinierte Stylesheet-ClientLibs müssen als Teil der Kopfzeile geladen werden, damit sie in der Autoren und der Veröffentlichungsumgebung ordnungsgemäß funktionieren.

## Aktivieren der Layout-Container-Komponente für Seite {#enable-the-layout-container-component-for-page}

Mit diesen Aufgaben können Autoren Instanzen der **Layout-Container** auf der Seite.

### Aktivieren der Layout-Container-Komponente für die Seitenbearbeitung {#enable-the-layout-container-component-for-page-editing}

Damit Autoren weitere responsive Raster zu den Inhaltsseiten hinzufügen können, müssen Sie die Layout-Container-Komponente für Ihre Seite aktivieren. Möglich ist dies über folgende Optionen:

* **Autorenumgebung**

   Verwendung [Designmodus](/help/sites-authoring/default-components-designmode.md) , um die **Ebenencontainer** -Komponente für eine Seite.

* **Komponentendefinition**

   Nutzen Sie beim Definieren der Komponente `allowedComponent` oder ein Static Include.

### Konfigurieren des Rasters des Layout-Containers {#configure-the-grid-of-the-layout-container}

Sie können die Anzahl der Spalten konfigurieren, die für jede bestimmte Instanz des Layout-Containers verfügbar sind:

1. **Autorenumgebung**

   Sie können die Anzahl der Spalten konfigurieren, die für jede bestimmte Instanz des Layout-Containers verfügbar sind.

   Verwenden Sie dazu [Designmodus](/help/sites-authoring/default-components-designmode.md)und öffnen Sie dann das Dialogfeld &quot;Design&quot;für den erforderlichen Container. Hier können Sie festlegen, wie viele Spalten für die Positionierung und Größenanpassung verfügbar sein sollen. Der Standardwert lautet 12.

1. **XML**

   Definitionen für das responsive Raster finden Sie unter:

   `etc/design/<*your-project-name*>/.content.xml`

   Die folgenden Parameter können definiert werden:

   * Anzahl der verfügbaren Spalten:

      * `columns="{String}8"`
   * Komponenten, die zur aktuellen Komponente hinzugefügt werden können:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`
