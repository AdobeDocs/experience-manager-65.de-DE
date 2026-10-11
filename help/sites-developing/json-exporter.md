---
title: JSON-Exporter für Content Services
description: Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden. Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
exl-id: 647395c0-f392-427d-a998-e9ddf722b9f9
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 97%
---
# JSON-Exporter für Content Services{#json-exporter-for-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* [Single Page Applications (SPA)](spa-walkthrough.md)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Über Inhaltsfragmente, die strukturierte Inhalte verwenden, können Sie Content Services zur Verfügung stellen, indem Sie die Inhalte mit JSON Exporter auf einer (beliebigen) AEM-Seite im JSON-Datenmodellformat bereitstellen. Diese Methode kann dann von Ihren eigenen Anwendungen genutzt werden.

>[!NOTE]
>
>Die hier beschriebene Funktionalität ist für alle Kernkomponenten seit [Version 1.1.0 der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) verfügbar.

## JSON Exporter mit Inhaltsfragment-Kernkomponenten {#json-exporter-with-content-fragment-core-components}

Mit dem AEM JSON Exporter können Sie den Inhalt einer beliebigen AEM-Seite im JSON-Datenmodellformat bereitstellen. Diese Methode kann dann von Ihren eigenen Anwendungen genutzt werden.

Im Rahmen von AEM erfolgt die Bereitstellung über den Selektor `model` und die Erweiterung `.json`.

`.model.json`

1. Beispielsweise werden durch eine URL wie:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en.model.json
   ```

1. Inhalte bereitgestellt wie:

   ![chlimage_1-192](assets/chlimage_1-192.png)

Alternativ können Sie die Inhalte eines strukturierten Inhaltsfragments bereitstellen, indem Sie dieses spezifisch nachverfolgen.

Verwenden Sie den gesamten Pfad zum Fragment (über `jcr:content`), zum Beispiel mit einem Suffix wie.

`.../jcr:content/root/responsivegrid/contentfragment.model.json`

Ihre Seite kann entweder ein einzelnes Inhaltsfragment oder mehrere Komponenten verschiedener Typen enthalten. Sie können auch Mechanismen wie Listenkomponenten verwenden, um automatisch nach relevanten Inhalten zu suchen.

* Beispielsweise werden durch eine URL wie:

  ```shell
  http://localhost:4502/content/we-retail/language-masters/en/manchester-airport/jcr:content/root/responsivegrid/contentfragment.model.json
  ```

* Inhalte bereitgestellt wie:

  ![chlimage_1-193](assets/chlimage_1-193.png)

  >[!NOTE]
  >
  >Sie können [Ihre eigenen Komponenten anpassen](/help/sites-developing/json-exporter-components.md), um auf diese Daten zuzugreifen und sie zu verwenden.

  >[!NOTE]
  >
  >Obwohl es sich nicht um eine Standardimplementierung handelt, werden [mehrere Selektoren unterstützt,](json-exporter-components.md#multiple-selectors) jedoch muss `model` der erste sein.

### Weiterführende Informationen {#further-information}

Siehe auch:

* Assets-HTTP-API

  * [Assets-HTTP-API](/help/assets/mac-api-assets.md)

* Sling-Modelle:

  * [Sling-Modelle - Zuordnen einer Modellklasse zu einem Ressourcentyp seit 1.3.0](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)

* AEM mit JSON:

  * [Ermitteln von Seiteninformationen im JSON-Format](/help/sites-developing/pageinfo.md)

## Verwandte Dokumentation {#related-documentation}

Weiterführende Ressourcen:

* Das [Thema „Inhaltsfragmente“ im Assets-Benutzerhandbuch](/help/assets/content-fragments/content-fragments.md)

* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)
* [Aktivieren eines JSON-Exports für eine Komponente](/help/sites-developing/json-exporter-components.md)

* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und die [Inhaltsfragmentkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de)
