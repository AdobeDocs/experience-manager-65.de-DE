---
title: Emulatoren
seo-title: Emulatoren
description: AEM ermöglicht es Autoren, eine Seite in einem Emulator anzuzeigen, der die Umgebung simuliert, in der ein Benutzer die Seite aufruft.
seo-description: AEM ermöglicht es Autoren, eine Seite in einem Emulator anzuzeigen, der die Umgebung simuliert, in der ein Benutzer die Seite aufruft.
uuid: ee1496a5-be68-4318-b5ce-b11c41e4485c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: c51fca81-5dfc-4838-9672-acb6de62778b
legacypath: /content/docs/en/aem/6-0/develop/mobile/emulators
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Emulatoren{#emulators}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit Adobe Experience Manager (AEM) können Autoren eine Seite in einem Emulator anzeigen, der die Umgebung simuliert, in der ein Benutzer die Seite aufruft, z. B. auf einem mobilen Gerät oder in einem E-Mail-Client.

Das AEM-Emulator-Framework:

* ermöglicht Content-Authoring in einer simulierten Benutzeroberfläche, z. B. auf einem mobilen Gerät oder in einem E-Mail-Client (zum Erstellen von Newslettern).
* passt den Seiteninhalt entsprechend der simulierten Benutzeroberfläche an.
* ermöglicht das Erstellen benutzerdefinierter Emulatoren.

>[!CAUTION]
>
>Diese Funktion wird nur in der klassischen Benutzeroberfläche unterstützt.

## Emulatoren-Eigenschaften {#emulators-characteristics}

Emulatoren haben folgende Eigenschaften:

* Sie basieren auf ExtJS.
* Sie werden auf dem Seiten-DOM ausgeführt.
* Die Darstellung erfolgt mithilfe von CSS.
* Sie unterstützten Plug-ins (z. B. für die Drehung auf mobilen Geräten).
* Sie sind nur im author-Modus aktiviert.
* Its base component is at `/libs/wcm/emulator/components/base`.

### Konvertieren von Inhalten mit einem Emulator {#how-the-emulator-transforms-the-content}

Der Emulator sorgt dafür, dass die Emulator-DIVs den HTML-Hauptteilinhalt umschließen. Der folgende HTML-Code:

```xml
<body>
<div id="wrapper" class="page mobilecontentpage ">
    <div class="topnav mobiletopnav">
    ...
    </div>
    ...
</div>
</body>
```

wird beispielsweise nach dem Starten des Emulators in folgenden HTML-Code geändert:

```xml
<body>
 <div id="cq-emulator-toolbar">
 ...
 </div>
 <div id="cq-emulator-wrapper">
  <div id="cq-emulator-device">
   <div class=" android vertical" id="cq-emulator">
    ...
    <div class=" android vertical" id="cq-emulator-content">
     ...
     <div id="wrapper" class="page mobilecontentpage">
     ...
     </div>
     ...
    </div>
   </div>
  </div>
 </div>
 ...
</body>
```

Zwei DIV-Tags wurden hinzugefügt:

* das DIV-Tag mit der ID `cq-emulator`, das den gesamten Emulator beinhaltet, und

* das DIV-Tag mit der ID `cq-emulator-content`, das den Viewport-, Bildschirm- oder Inhaltsbereich repräsentiert, in dem sich der Seiteninhalt befindet.

Den neuen DIV-Tags des Emulators werden auch neue CSS-Klassen zugewiesen. Sie stellen den Namen des aktuellen Emulators dar.

Die Plug-ins eines Emulators können die Liste der zugeordneten CSS-Klassen zusätzlich erweitern, wie beim Beispiel des Drehungs-Plug-ins, das je nach aktueller Drehung auf dem Gerät die Klasse „vertical“ oder „horizontal“ einfügen.

So kann die vollständige Darstellung des Emulators durch die Verwendung von CSS-Klassen gesteuert werden, die den IDs und CSS-Klassen der Emulator-DIVs entsprechen.

>[!NOTE]
>
>Es wird empfohlen, dass die Projekt-HTML den Hauptteilinhalt wie im obigen Beispiel in einer einzigen DIV umschließt. Wenn der Hauptteilinhalt mehrere Tags enthält, kann es zu unvorhergesehenen Ergebnissen kommen.

### Mobile Emulatoren {#mobile-emulators}

Die vorhandenen mobilen Emulatoren:

* befinden sich unter /libs/wcm/mobile/components/emulators.
* Sind über das JSON-Servlet verfügbar unter:

   http://localhost:4502/bin/wcm/mobile/emulators.json

When the page component relies on the mobile page component ( `/libs/wcm/mobile/components/page`), the emulator functionality is automatically integrated in the page through the following mechanism:

* Die mobile Seitenkomponente `head.jsp` beinhaltet die der Gerätegruppe zugeordnete Initialisierungskomponente des Emulators (nur im author-Modus) und Rendering-CSS durch:

   `deviceGroup.drawHead(pageContext);`

* The method `DeviceGroup.drawHead(pageContext)` includes the emulator&#39;s init component, i.e. calls the `init.html.jsp` of the emulator component. If the emulator component does not have its own `init.html.jsp` and relies on the mobile base emulator ( `wcm/mobile/components/emulators/base)`, the init script of the mobile base emulator is called ( `/libs/wcm/mobile/components/emulators/base/init.html.jsp`).

* Das init-Skript des mobilen Basis-Emulators definiert JavaScript:

   * Die Konfiguration für alle Emulatoren, die für die Seite definiert sind (emulatorConfigs)
   * Der Emulator-Manager, der die Funktionalität des Emulators in die Seite integriert durch:

      `emulatorMgr.launch(config)`;

      Der Emulator-Manager wird wie folgt definiert:

      `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Erstellen eines benutzerdefinierten mobilen Emulators {#creating-a-custom-mobile-emulator}

Gehen Sie zum Erstellen eines benutzerdefinierten mobilen Emulators wie folgt vor:

1. Erstellen Sie unten `/apps/myapp/components/emulators` die Komponente `myemulator` (Knotentyp: 
     `cq:Component`).

1. Set the `sling:resourceSuperType` property to `/libs/wcm/mobile/components/emulators/base`

1. Definieren Sie eine CSS-Client-Bibliothek mit Kategorie `cq.wcm.mobile.emulator` für das Emulator-Erscheinungsbild: name = `css`, node type = `cq:ClientLibrary`

   Als Beispiel können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/iPhone/css`

1. Definieren Sie bei Bedarf eine JS-Client-Bibliothek, um beispielsweise ein bestimmtes Plugin zu definieren: name = js, node type = cq:ClientLibrary

   Als Beispiel können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/base/js`

1. Wenn der Emulator bestimmte Funktionen unterstützt, die von Plugins definiert werden (z. B. per Touch-Scrolling), erstellen Sie einen Konfigurationsknoten unter dem Emulator: name = `cq:emulatorConfig`, node type = `nt:unstructured` und fügen Sie die Eigenschaft hinzu, die das Plugin definiert:

   * Name = `canRotate`, Typ = `Boolean`, Wert = `true`: , um die Rotationsfunktion einzuschließen.

   * Name = `touchScrolling`, Type = `Boolean`, Value = `true`: to include the touch scrolling functionality.
   Sie können weitere Funktionen hinzufügen, indem Sie eigene Plug-ins definieren.

