---
title: Die RemotePage-Komponente
description: Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente zur Bearbeitung von Remote-React-SPAs in AEM.
exl-id: 3f015997-0d42-4241-a890-0f16a19c5e34
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: a9f7d31e-bbe1-4475-966a-5f213546fcd9
    internal-label: SPA Editor
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 96%
---

# Die RemotePage-Komponente {#remote-page-component}

Wenn Sie entscheiden, welchen Grad der Integration Sie zwischen Ihrer externen SPA und AEM haben möchten, wird oft klar, dass Sie die SPA in AEM anzeigen und bearbeiten können müssen. Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente genau für diesen Zweck.

{{ue-over-spa}}

## Überblick {#overview}

Die RemotePage-Komponente ruft alle erforderlichen Assets aus dem generierten `asset-manifest.json` des Programms ab und verwendet diese zum Rendern der SPA in AEM.

* Mit RemotePage können Sie die Skripte und Stylesheets einer SPA im Hauptteil einer AEM-Seitenkomponente einfügen.
* Mit Virtual Frontend-Komponenten können Abschnitte im AEM-SPA-Editor als bearbeitbar markiert werden.
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

## Einschränkungen {#limitations}

* Die RemotePage-Komponente erwartet, dass die Implementierung ein Asset-Manifest wie das hier [ bereitstellt](https://github.com/shellscape/webpack-manifest-plugin) Die RemotePage-Komponente wurde jedoch nur für die Zusammenarbeit mit dem React-Framework (und Next.js über die Komponente „remote-page-next“) getestet und unterstützt daher nicht das Fernladen von Anwendungen aus anderen Frameworks, wie z. B. Angular.
* Internes CSS, das in der Stamm-HTML-Datei der Anwendung definiert ist, sowie Inline-CSS im Stamm-DOM-Knoten sind beim Remote-Rendering in AEM nicht verfügbar.

## Technische Details {#technical-details}

Wie der Rest des AEM-SPA-Projekts ist auch die RemotePage-Komponente eine Open Source-Komponente. Die vollständigen technischen Details der RemotePage-Komponente [finden Sie im GitHub-Repository.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
