---
title: Personalisierung und Content-Targeting
seo-title: Personalisierung und Content-Targeting
description: Erfahren Sie, wie AEM personalisierte Inhalte erstellen kann
seo-description: Erfahren Sie, wie AEM personalisierte Inhalte erstellen kann
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: be34760a-875b-419d-9fa4-2359b314a3b7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 87%

---

# Personalisierung und Content-Targeting {#personalization}

## Personalisierung und Content-Targeting {#personalization-and-content-targeting}

AEM stellt eine Reihe von Werkzeugen zur Bearbeitung von Inhalten für eine bestimmte Zielgruppe und die Darstellung personalisierter Erlebnisse bereit.

## Targeting-Modus   {#targeting-mode}

[Verfassen Sie zielgerichtete Inhalte](/help/sites-authoring/content-targeting-touch.md) im Targeting-Modus von AEM. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketingaktivitäten.

## Aktivitäten  {#activities}

Mit Aktivitäten lassen sich Ihre Marketingprojekte definieren und organisieren. Teil der Aktivitäten sind die gewünschten Zielgruppen sowie der Zeitraum, in dem das Targeting durchgeführt wird.

Beispielsweise enthält der Produktkatalog &quot;We.Retail&quot;Teaser, die die Aufmerksamkeit auf saisonale Produkte lenken. In der Aktivität „Sommersport“ sind die Marketing-Segmente definiert, die während der Sommermonate gezielt angesprochen werden sollen.

Mit Aktivitäten wird zudem auch die [Targeting-Engine](/help/sites-authoring/personalization.md#targeting-engine) bestimmt, die Ihre Seiten verwenden.

Mit der [Aktivitätskonsole](/help/sites-authoring/activitylib.md) können Sie die Aktivitäten Ihrer Marken erstellen und verwalten. Sie können auch Aktivitäten erstellen, während Sie [zielgerichtete Inhalte erstellen](/help/sites-authoring/content-targeting-touch.md).

## Erlebnisse {#experiences}

Legen Sie für jede Aktivität ein oder mehr Erlebnisse fest, in denen die gewünschten Zielgruppen identifiziert sind. Mit AEM verfügen Sie über die Möglichkeit, die Inhalte jedes Erlebnisses gezielt zu steuern.

Zielgruppen basieren auf Marketingsegmenten, die entweder in AEM oder Adobe Target erstellt werden. Öffnet ein Besucher eine Webseite, bestimmt die Seitenlogik die Zielgruppe, in die er fällt, und zeigt die für diese Zielgruppe erstellten Inhalte an.

Mit einer Aktivität können beispielsweise Erlebnisse für zwei verschiedene Zielgruppen festgelegt werden: Frauen über 30 und Frauen unter 30. Auf der Damenseite der Website &quot;We.Retail&quot;werden für jedes Erlebnis unterschiedliche Produkte angezeigt.

Die Erlebnisse der Aktivitäten werden von Ihnen festgelegt. Sie können hierzu die [Aktivitätskonsole](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) oder den [Targeting-Modus](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) verwenden und Aktivitäten Erlebnisse hinzufügen.

## Angebote   {#offers}

Angebote sind Inhalte, die an einem Ort auf einer Seite angezeigt werden, die für ein Erlebnis festgelegt wurde. Verwenden Sie für verschiedene Erlebnisse verschiedene Angebote, um Inhalte optimal auf Ihre Zielgruppen zuzuschneiden.

Beispielsweise kann die Damenseite der Beispiel-Website &quot;We.Retail&quot;Angebote als Teaser-Bild verwenden, das oben auf der Seite angezeigt wird. Für Erlebnisse für Frauen über 30 werden andere Angebote eingesetzt als für Frauen unter 30.

Mit der [Angebotskonsole](/help/sites-authoring/offerlib.md) lassen sich Angebote erstellen, die für mehrere Erlebnisse eingesetzt werden sollen. Erstellen Sie Einmal-Angebote oder fügen Sie Angebote aus einer Angebotsbibliothek hinzu, wenn Sie [zielgerichtete Inhalte erstellen](/help/sites-authoring/content-targeting-touch.md).

## Targeting-Engine    {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik hinter zielgerichteten Inhalten darstellt. [Aktivitäten](/help/sites-authoring/activitylib.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

### AEM {#aem}

AEM verfügt über eine integrierte Targeting-Engine, mit der Seitenanfragen verarbeitet und anzuzeigende Inhalte bestimmt werden. Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden und die Zielgruppen Ihrer Erlebnisse festlegen.

### Adobe Target {#adobe-target}

Mit der Adobe Target-Targeting-Engine werden von Seitenbesuchen gesammelte Informationen in Adobe Target verfolgt.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren und die die Zielgruppen Ihrer Erlebnisse bestimmen.
* Aktivitäten, die mit der Adobe Target-Engine bereitgestellt werden, werden [mit Target synchronisiert](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie [in Adobe Target](/help/sites-administering/opt-in.md) integriert haben.
