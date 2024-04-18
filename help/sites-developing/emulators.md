---
title: Emulatoren
description: AEM ermöglicht es Autorinnen und Autoren, eine Seite in einem Emulator anzuzeigen, der die Umgebung simuliert, in der Endbenutzende die Seite aufrufen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
legacypath: /content/docs/en/aem/6-0/develop/mobile/emulators
exl-id: 009b7e2c-ac37-4acc-a656-0a34d3853dfd
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 100%

---

# Emulatoren{#emulators}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit Adobe Experience Manager (AEM) können Autorinnen und Autoren eine Seite in einem Emulator anzeigen, der die Umgebung simuliert, in der Endbenutzende die Seite aufrufen, z. B. auf einem Mobilgerät oder in einem E-Mail-Client.

Das AEM-Emulator-Framework:

* ermöglicht die Inhaltserstellung in einer simulierten Benutzeroberfläche, z. B. auf einem Mobilgerät oder in einem E-Mail-Client (zum Erstellen von Newslettern).
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
* Sie unterstützten Plug-ins (z. B. das Plug-in für die Drehung auf Mobilgeräten).
* Sie sind nur in der Autoreninstanz aktiviert.
* Die Basiskomponente befindet sich unter `/libs/wcm/emulator/components/base`.

### Transformieren von Inhalten mit einem Emulator {#how-the-emulator-transforms-the-content}

Der Emulator sorgt dafür, dass die Emulator-DIVs den Inhalt des HTML-Hauptteils umschließen. Der folgende HTML-Code:

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
>Es wird empfohlen, dass die Projekt-HTML den Inhalt des Hauptteils wie im obigen Beispiel in einer einzigen DIV umschließt. Wenn der Inhalt des Hauptteils mehrere Tags umfasst, kann es zu unvorhersehbaren Ergebnissen kommen.

### Mobile Emulatoren {#mobile-emulators}

Die vorhandenen mobilen Emulatoren:

* befinden sich unter „/libs/wcm/mobile/components/emulators“
* sind über dasJSON-Servlet verfügbar unter:

  http://localhost:4502/bin/wcm/mobile/emulators.json

Wenn die Seitenkomponente auf die mobile Seitenkomponente (`/libs/wcm/mobile/components/page`) angewiesen ist, ist die Emulatorfunktion automatisch durch folgenden Mechanismus in die Seite integriert:

* Die mobile Seitenkomponente `head.jsp` beinhaltet die der Gerätegruppe zugeordnete Initialisierungskomponente des Emulators (nur im author-Modus) und Rendering-CSS durch:

  `deviceGroup.drawHead(pageContext);`

* Die Methode `DeviceGroup.drawHead(pageContext)` enthält die Inititialisierungskomponente des Emulators, d. h., sie ruft die Datei `init.html.jsp` der Emulatorkomponente auf. Falls die Emulatorkomponente nicht über eine eigene `init.html.jsp` verfügt, sondern auf den mobilen Basisemulator (`wcm/mobile/components/emulators/base)`) angewiesen ist, wird das Initialisierungsskript des mobilen Basisemulators (`/libs/wcm/mobile/components/emulators/base/init.html.jsp`) aufgerufen.

* Das Initialisierungsskript des mobilen Basisemulators definiert über JavaScript Folgendes:

   * Die Konfiguration für alle Emulatoren, die für die Seite definiert sind (emulatorConfigs)
   * Der Emulator-Manager, der die Funktionalität des Emulators in die Seite über Folgendes integriert:

     `emulatorMgr.launch(config)`;

     Der Emulator-Manager wird durch Folgenders definiert:

     `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Erstellen eines benutzerdefinierten mobilen Emulators {#creating-a-custom-mobile-emulator}

So erstellen Sie einen benutzerdefinierten mobilen Emulator:

1. Erstellen Sie unterhalb von `/apps/myapp/components/emulators` die Komponente `myemulator` (Knotentyp: `cq:Component`).

1. Legen Sie die `sling:resourceSuperType`-Eigenschaft auf `/libs/wcm/mobile/components/emulators/base` fest.

1. Definieren Sie eine CSS-Client-Bibliothek mit der Kategorie `cq.wcm.mobile.emulator` für das Erscheinungsbild des Emulators: Name = `css`, Knotentyp = `cq:ClientLibrary`.

   Beispielsweise können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/iPhone/css` verweisen.

1. Definieren Sie bei Bedarf eine JS-Client-Bibliothek, um beispielsweise ein bestimmtes Plug-in zu definieren: Name = js, Knotentyp = cq:ClientLibrary.

   Beispielsweise können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/base/js` verweisen.

1. Wenn der Emulator bestimmte, durch Plug-ins definierte Funktionen unterstützt (z. B. Touch-Scrolling), erstellen Sie einen Konfigurationsknoten unterhalb des Emulators: Name = `cq:emulatorConfig`, Knotentyp = `nt:unstructured` und fügen Sie die Eigenschaft hinzu, die das Plug-in definiert:

   * Name = `canRotate`, Typ = `Boolean`, Wert = `true`: um die Rotationsfunktion einzuschließen.

   * Name = `touchScrolling`, Typ = `Boolean`, Wrt = `true`: fum die Funktion „Touch-Scrolling“ einzuschließen.

   Sie können weitere Funktionen hinzufügen, indem Sie eigene Plug-ins definieren.
