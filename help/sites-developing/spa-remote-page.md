---
title: Die RemotePage-Komponente
description: Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente zur Bearbeitung von Remote-React-SPAs in AEM.
exl-id: 3f015997-0d42-4241-a890-0f16a19c5e34
source-git-commit: a92358d187aa78e05dd9b5a7bd4ae14bf0972f62
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 73%

---

# Die RemotePage-Komponente {#remote-page-component}

Wenn Sie entscheiden, welchen Grad der Integration Sie zwischen Ihrer externen SPA und AEM haben möchten, wird oft klar, dass Sie die SPA in AEM anzeigen und bearbeiten können müssen. Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente genau für diesen Zweck.

## Überblick {#overview}

Die RemotePage-Komponente ruft alle erforderlichen Assets aus dem generierten `asset-manifest.json` des Programms ab und verwendet diese zum Rendern der SPA in AEM.

* Mit RemotePage können Sie die Skripte und Stylesheets einer SPA im Hauptteil einer AEM Seitenkomponente einfügen.
* Mit Virtual Frontend-Komponenten können Abschnitte im AEM-SPA-Editor als bearbeitbar markiert werden.
* Gemeinsam stellen sie sicher, dass eine SPA, die auf einer anderen Domain gehostet wird, in AEM bearbeitet werden kann.

Weitere Informationen zu bearbeitbaren externen SPAs in AEM finden Sie im Artikel zum [Bearbeiten einer externen SPA in AEM](spa-edit-external.md).

## Voraussetzungen {#requirements}

* CORS in der Entwicklung aktivieren
* Remote-URL in den Seiteneigenschaften konfigurieren
* SPA in AEM rendern
* Die Webanwendung muss ein Bundler-Asset-Manifest wie eines der folgenden verwenden und eine Datei &quot;asset-manifest.json&quot;im Domänenstamm bereitstellen, in der in einer Einstiegspunkteigenschaft alle zu ladenden CSS- und JS-Dateien aufgelistet sind:
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest

   ![Einstiegspunkte](assets/asset-manifest-entrypoints.png)

* Die Anwendung muss in der Lage sein, unter dem Body-Element `<div id="root"></div>` zu initialisieren. Wenn für die Instanziierung der App ein anderes Markup erwartet wird, muss dies in den HTL-Skripten der Proxy-Komponente mit dem Wert `sling:resourceSuperType="spa-project-core/components/remotepage` entsprechend angepasst werden.

## Beschränkungen {#limitations}

* Die aktuelle Implementierung der RemotePage-Komponente unterstützt nur Remote React-Programme.
* Internes CSS, das in der Stamm-HTML-Datei des Programms definiert ist, sowie Inline-CSS im Stamm-DOM-Knoten sind beim Remote-Rendering in AEM nicht verfügbar.

## Technische Details {#technical-details}

Wie der Rest des AEM-SPA-Projekts ist die RemotePage-Komponente eine Open Source-Komponente. Die vollständigen technischen Details der RemotePage-Komponente [finden Sie im GitHub-Repository.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
