---
title: Personalisierung und Content-Targeting
description: Erfahren Sie, wie Adobe Experience Manager 6.5 personalisierte Inhalte erstellen kann.
exl-id: be34760a-875b-419d-9fa4-2359b314a3b7
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---

# Personalisierung und Content-Targeting {#personalization}

## Personalisierung und Content-Targeting {#personalization-and-content-targeting}

AEM stellt eine Reihe von Tools zur Bearbeitung von Inhalten für eine bestimmte Zielgruppe und die Darstellung personalisierter Erlebnisse bereit.

## Targeting-Modus {#targeting-mode}

[Verfassen Sie zielgerichtete Inhalte](/help/sites-authoring/content-targeting-touch.md) im Targeting-Modus von AEM. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketing-Aktivitäten.

## Aktivitäten {#activities}

Aktivitäten definieren und organisieren Ihre Marketing-Maßnahmen.  Aktivitäten umfassen die Zielgruppen, die Sie als Ziel angeben, und den Zeitraum, in dem das Targeting angewendet wird.

So enthält der We.Retail-Produktkatalog beispielsweise Teaser, die die Aufmerksamkeit auf Produkte der aktuellen Saison lenken sollen. In der Aktivität „Sommersport“ sind die Marketing-Segmente definiert, die während der Sommermonate gezielt angesprochen werden sollen.

Mit Aktivitäten wird zudem auch die [Targeting-Engine](/help/sites-authoring/personalization.md#targeting-engine) bestimmt, die Ihre Seiten verwenden.

Mit der [Aktivitätskonsole](/help/sites-authoring/activitylib.md) können Sie die Aktivitäten Ihrer Marken erstellen und verwalten. Sie können auch Aktivitäten erstellen, während Sie [zielgerichtete Inhalte erstellen](/help/sites-authoring/content-targeting-touch.md).

## Erlebnisse {#experiences}

Legen Sie für jede Aktivität ein oder mehr Erlebnisse fest, in denen die gewünschten Zielgruppen identifiziert sind. Mit AEM verfügen Sie über die Möglichkeit, die Inhalte jedes Erlebnisses gezielt zu steuern.

Zielgruppen basieren auf Marktsegmenten, die entweder in AEM oder in Adobe Target erstellt werden.  Öffnet ein Besucher eine Web-Seite, bestimmt die Seitenlogik die Zielgruppe, in die er fällt, und zeigt die für diese Zielgruppe erstellten Inhalte an.

Mit einer Aktivität können beispielsweise Erlebnisse für zwei verschiedene Zielgruppen festgelegt werden: Frauen über 30 und Frauen unter 30. Die Damenabteilung der We.Retail-Website zeigt für die beiden Erlebnisse unterschiedliche Inhalte an.

Die Erlebnisse der Aktivitäten werden von Ihnen festgelegt.  Sie können die [Aktivitätskonsole](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) oder den [Targeting-Modus](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) verwenden, um Erlebnisse zu einer Aktivität hinzuzufügen.

## Angebote {#offers}

Bei einem Angebot handelt es sich um Inhalte, die an einer Stelle auf einer Seite für ein Erlebnis angezeigt werden.  Verwenden Sie verschiedene Angebote für verschiedene Erlebnisse, um die Effektivität von Inhalten für Ihre Zielgruppen zu optimieren.

Beispielsweise könnte die Damenabteilung einer We.Retail-Beispiel-Website Angebote als das Teaser-Bild verwenden, das oben auf der Seite eingeblendet wird. Für Erlebnisse für Frauen über 30 werden andere Angebote eingesetzt als für Frauen unter 30.

Mit der [Angebotskonsole](/help/sites-authoring/offerlib.md) können Sie Angebote erstellen, die Sie für mehrere Erlebnisse einsetzen können. Erstellen Sie Einmal-Angebote oder fügen Sie Angebote aus einer Angebotsbibliothek hinzu, wenn Sie [zielgerichtete Inhalte erstellen](/help/sites-authoring/content-targeting-touch.md).

## Targeting-Engine {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik hinter zielgerichteten Inhalten darstellt.  [Aktivitäten](/help/sites-authoring/activitylib.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

### AEM {#aem}

AEM bietet eine integrierte Targeting-Engine, die Seitenanforderungen verarbeitet und den anzuzeigenden Inhalt bestimmt.  Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden, um die Zielgruppen Ihrer Erlebnisse festzulegen.

### Adobe Target {#adobe-target}

Die Targeting-Engine von Adobe Target führt dazu, dass die Informationen, die bei Seitenbesuchen erfasst werden, in Adobe Target verfolgt werden.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren, um die Zielgruppen Ihrer Erlebnisse zu bestimmen.
* Aktivitäten, die die Adobe Target-Engine verwenden, werden [mit Target synchronisiert](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie über eine [Integration mit Adobe Target](/help/sites-administering/opt-in.md) verfügen.
