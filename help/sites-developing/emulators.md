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
exl-id: 009b7e2c-ac37-4acc-a656-0a34d3853dfd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 66%

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

## Emulatoren-Eigenschaften  {#emulators-characteristics}

Emulatoren haben folgende Eigenschaften:

* Sie basieren auf ExtJS.
* Sie werden auf dem Seiten-DOM ausgeführt.
* Die Darstellung erfolgt mithilfe von CSS.
* Sie unterstützten Plug-ins (z. B. für die Drehung auf mobilen Geräten).
* Sie sind nur im author-Modus aktiviert.
* Die Basiskomponente befindet sich unter `/libs/wcm/emulator/components/base`.

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
* sind über das JSON-Servlet verfügbar unter:

   http://localhost:4502/bin/wcm/mobile/emulators.json

Wenn sich die Seitenkomponente auf die mobile Seitenkomponente ( `/libs/wcm/mobile/components/page`) stützt, wird die Emulatorfunktion automatisch über den folgenden Mechanismus in die Seite integriert:

* Die mobile Seitenkomponente `head.jsp` beinhaltet die der Gerätegruppe zugeordnete Initialisierungskomponente des Emulators (nur im author-Modus) und Rendering-CSS durch:

   `deviceGroup.drawHead(pageContext);`

* Die Methode `DeviceGroup.drawHead(pageContext)` enthält die Init-Komponente des Emulators, d. h. ruft die `init.html.jsp` der Emulator-Komponente auf. Wenn die Emulatorkomponente nicht über eine eigene `init.html.jsp` verfügt und sich auf den mobilen Basis-Emulator ( `wcm/mobile/components/emulators/base)`) stützt, wird das Init-Skript des mobilen Basis-Emulators ( `/libs/wcm/mobile/components/emulators/base/init.html.jsp`) aufgerufen.

* Das Init-Skript des mobilen Basis-Emulators definiert über JavaScript:

   * Die Konfiguration für alle Emulatoren, die für die Seite definiert sind (emulatorConfigs)
   * Der Emulator-Manager, der die Funktionalität des Emulators in die Seite integriert durch:

      `emulatorMgr.launch(config)`;

      Der Emulator-Manager wird folgendermaßen definiert:

      `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Erstellen eines benutzerdefinierten mobilen Emulators {#creating-a-custom-mobile-emulator}

Gehen Sie zum Erstellen eines benutzerdefinierten mobilen Emulators wie folgt vor:

1. Erstellen Sie unter `/apps/myapp/components/emulators` die Komponente `myemulator` (Knotentyp: `cq:Component`).

1. Legen Sie die Eigenschaft `sling:resourceSuperType` auf `/libs/wcm/mobile/components/emulators/base` fest.

1. Definieren Sie eine CSS-Client-Bibliothek mit der Kategorie `cq.wcm.mobile.emulator` für das Emulator-Erscheinungsbild: name = `css`, node type = `cq:ClientLibrary`

   Als Beispiel können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/iPhone/css` verweisen.

1. Definieren Sie bei Bedarf eine JS-Client-Bibliothek, um beispielsweise ein bestimmtes Plug-in zu definieren: name = js, node type = cq:ClientLibrary

   Als Beispiel können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/base/js` verweisen.

1. Wenn der Emulator bestimmte durch Plug-ins definierte Funktionen unterstützt (z. B. Touch-Scrollen), erstellen Sie einen Konfigurationsknoten unter dem Emulator: name = `cq:emulatorConfig`, node type = `nt:unstructured` und fügen Sie die Eigenschaft hinzu, die das Plug-in definiert:

   * Name = `canRotate`, Typ = `Boolean`, Wert = `true`: , um die Rotationsfunktion einzuschließen.

   * Name = `touchScrolling`, Typ = `Boolean`, Wert = `true`: , um die Funktion zum Touch-Scrollen einzuschließen.
   Sie können weitere Funktionen hinzufügen, indem Sie eigene Plug-ins definieren.
