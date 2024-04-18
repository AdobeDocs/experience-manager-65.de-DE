---
title: Die RemotePage-Komponente
description: Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente zur Bearbeitung von Remote-React-SPAs in AEM.
exl-id: 3f015997-0d42-4241-a890-0f16a19c5e34
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 86%

---

# Die RemotePage-Komponente {#remote-page-component}

Wenn Sie entscheiden, welchen Grad der Integration Sie zwischen Ihrer externen SPA und AEM haben möchten, wird oft klar, dass Sie die SPA in AEM anzeigen und bearbeiten können müssen. Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente genau für diesen Zweck.

## Übersicht {#overview}

Die RemotePage-Komponente ruft alle erforderlichen Assets aus dem generierten `asset-manifest.json` des Programms ab und verwendet diese zum Rendern der SPA in AEM.

* Mit RemotePage können Sie die Skripte und Stylesheets einer SPA im Hauptteil einer AEM-Seitenkomponente einfügen.
* Mit den Virtual Frontend-Komponenten können Sie Bereiche im AEM SPA Editor als bearbeitbar markieren.
* Gemeinsam stellen sie sicher, dass eine SPA, die auf einer anderen Domain gehostet wird, in AEM bearbeitet werden kann.

Weitere Informationen zu bearbeitbaren externen SPAs in AEM finden Sie im Artikel zum [Bearbeiten einer externen SPA in AEM](spa-edit-external.md).

## Voraussetzungen {#requirements}

* CORS in der Entwicklung aktivieren
* Remote-URL in den Seiteneigenschaften konfigurieren
* SPA in AEM rendern
* Die Web-Anwendung muss ein Bundler-Asset-Manifest wie eines der folgenden verwenden und eine asset-manifest.json-Datei im Domain-Stamm bereitstellen, die in einer entrypoints-Eigenschaft alle zu ladenden CSS- und JS-Dateien auflistet:
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest

  ![Einstiegspunkte](assets/asset-manifest-entrypoints.png)

* Die Anwendung muss in einem `<div id="root"></div>`-Element unter dem Body-Element initialisiert werden können. Wenn für die Instanziierung der App ein anderes Markup erwartet wird, muss dies in den HTL-Skripten der Proxy-Komponente mit dem Wert `sling:resourceSuperType="spa-project-core/components/remotepage` entsprechend angepasst werden.

## Beschränkungen {#limitations}

* Die RemotePage-Komponente erwartet, dass die Implementierung ein Asset-Manifest wie das [hier gefundene bereitstellt.](https://github.com/shellscape/webpack-manifest-plugin) Die RemotePage-Komponente wurde jedoch nur für die Verwendung mit dem React-Framework getestet (und Next.js über die Komponente &quot;remote-page-next&quot;) und unterstützt daher nicht das Remote-Laden von Anwendungen aus anderen Frameworks wie Angular.
* Internes CSS, das in der Stamm-HTML-Datei der Anwendung definiert ist, sowie Inline-CSS im Stamm-DOM-Knoten sind beim Remote-Rendering in AEM nicht verfügbar.

## Technische Details {#technical-details}

Wie der Rest des AEM-SPA-Projekts ist auch die RemotePage-Komponente eine Open Source-Komponente. Die vollständigen technischen Details der RemotePage-Komponente [finden Sie im GitHub-Repository.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
