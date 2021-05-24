---
title: Aktivieren eines JSON-Exports für eine Komponente
seo-title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
seo-description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
uuid: d7cc3347-2adb-4ea5-94a4-a847a2e66d28
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: 448ad337-d4bb-4603-a27b-77da93feadbd
exl-id: 6d127e14-767e-46ad-aaeb-0ce9dd14d553
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 98%

---

# Aktivieren eines JSON-Exports für eine Komponente{#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Überblick {#overview}

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem Framework des [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (der sich wiederum auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) stützt).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn JSON exportiert werden soll. Deshalb müssen Sie diese beiden Schritte befolgen, um einen JSON-Export für eine beliebige Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente   {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>Ein Beispiel für die Verwendung von Sling-Modellen finden Sie im Artikel [Entwickeln von Sling Model Exportern in AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/sling-model-exporter-tutorial-develop.html).

Die Implementierungsklasse des Sling-Modells muss wie folgt kommentiert werden:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dadurch wird sichergestellt, dass Ihre Komponente mit dem `.model`-Selektor und der `.json`-Erweiterung eigenständig exportiert werden kann.

Außerdem kann die Sling-Modell-Klasse dadurch in der `ComponentExporter`-Oberfläche übernommen werden.

>[!NOTE]
>
>Jackson-Anmerkungen werden in der Regel nicht auf der Ebene der Sling-Modell-Klasse festgelegt, sondern auf der Ebene der Modell-Oberfläche. Damit wird sichergestellt, dass der JSON-Export als Teil der Komponenten-API gewertet wird.

>[!NOTE]
>
>Die Klassen `ExporterConstants` und `ComponentExporter` stammen aus dem `com.adobe.cq.export.json`-Paket.

### Verwenden mehrerer Selektoren {#multiple-selectors}

Obwohl dies kein Standardanwendungsfall ist, können zusätzlich zum `model`-Selektor mehrere Selektoren konfiguriert werden.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss der `model`-Selektor jedoch der erste Selektor und `.json` die Erweiterung sein.

## Kommentieren der Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Damit sie im JSON Exporter-Framework beachtet wird, sollte die `ComponentExporter`-Oberfläche (oder `ContainerExporter` bei Container-Komponenten) in der Modelloberfläche implementiert werden.

Für die entsprechende Sling-Modell-Oberfläche (`MyComponent`) wird in diesem Fall über [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) definiert, wie sie exportiert (serialisiert) werden soll.

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden serialisiert, die die gängigen Benennungskonventionen für Abfragemethoden einhalten. Ihre JSON-Eigenschaftsnamen werden dabei naturgemäß von den Namen der Abfragemethode abgeleitet. Um dies zu vermeiden bzw. zu überschreiben, benennen Sie die JSON-Eigenschaft mit `@JsonIgnore` oder `@JsonProperty` um.

## Beispiel {#example}

Die Kernkomponenten unterstützen den JSON-Export seit der Version [1.1.0 der Kernkomponenten](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/introduction.html). Sie können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-core-wcm-components auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip) herunter

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* Das [Thema „Inhaltsfragmente“·im Assets-Benutzerhandbuch](https://helpx.adobe.com/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-Exporter für Content Services ](/help/sites-developing/json-exporter.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) und die [Inhaltsfragmentkomponente](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)
