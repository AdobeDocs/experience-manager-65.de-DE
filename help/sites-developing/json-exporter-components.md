---
title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
exl-id: 6d127e14-767e-46ad-aaeb-0ce9dd14d553
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 78%

---

# Aktivieren eines JSON-Exports für eine Komponente{#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Übersicht {#overview}

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem Framework des [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (der sich wiederum auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) stützt).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn JSON exportiert werden soll. Führen Sie daher diese beiden Schritte aus, um den JSON-Export für jede Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>Ein Beispiel für die Verwendung von Sling-Modellen finden Sie unter [Entwickeln von Sling Model Exportern in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html?lang=de).

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
>Jackson-Anmerkungen werden nicht auf der Ebene der Sling-Modell-Klasse, sondern auf der Ebene der Modell-Oberfläche angegeben. Damit wird sichergestellt, dass der JSON-Export als Teil der Komponenten-API gewertet wird.

>[!NOTE]
>
>Die Klassen `ExporterConstants` und `ComponentExporter` stammen aus dem `com.adobe.cq.export.json`-Paket.

### Verwenden mehrerer Selektoren {#multiple-selectors}

Obwohl dies kein Standardnutzungsszenario ist, können zusätzlich zum `model`-Selektor mehrere Selektoren konfiguriert werden.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss der `model`-Selektor jedoch der erste Selektor und `.json` die Erweiterung sein.

## Kommentieren der Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Um vom JSON Exporter-Framework berücksichtigt zu werden, sollte die Modellschnittstelle die `ComponentExporter` -Schnittstelle (oder `ContainerExporter`, wenn eine Container-Komponente vorhanden ist).

Für die entsprechende Sling-Modell-Oberfläche (`MyComponent`) wird in diesem Fall über [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) definiert, wie sie exportiert (serialisiert) werden soll.

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden, die die übliche Benennungskonvention für Getter einhalten, serialisiert und leiten ihre JSON-Eigenschaftsnamen von den Getter-Namen aus. Um dies zu vermeiden bzw. zu überschreiben, benennen Sie die JSON-Eigenschaft mit `@JsonIgnore` oder `@JsonProperty` um.

## Beispiel {#example}

Die Kernkomponenten haben seit der Veröffentlichung den JSON-Export unterstützt [1.1.0 der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und kann als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-core-wcm-components auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip) herunter

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter folgenden Themen:

* Das [Thema „Inhaltsfragmente“ im Assets-Benutzerhandbuch](https://helpx.adobe.com/de/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-Exporter für Content Services](/help/sites-developing/json-exporter.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und die [Inhaltsfragmentkomponente](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html)
