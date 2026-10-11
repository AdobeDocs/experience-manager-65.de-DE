---
title: AEM Headless-Übersetzungs-Tour
description: Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer Headless-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM.
exl-id: 1a9d4c88-b676-4168-a9ef-7d218b39129f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Developer, User, Leader
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 100%
---
# AEM Headless-Übersetzungs-Tour {#aem-headless-translation-journey}

Beginnen Sie hier mit einer geführten Tour durch die Übersetzung Ihrer Headless-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM.

## Einführung {#introduction}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihre Zielgruppe überall und unabhängig von Kanal, Region oder Gebietsschema bereitzustellen.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Mithilfe der leistungsstarken Übersetzungs-Tools in AEM können diese wiederverwendbaren Fragmente einfach übersetzt und für Ihre Zielgruppe bereitgestellt werden, wo immer sie sich befindet.

Dieser Leitfaden führt Sie durch die wichtigsten Themen der Headless-Übersetzung. Nach dem Abschluss der Lektüre sollten Sie:

* einen Überblick darüber haben, was die Bereitstellung von Headless-Inhalten ist.
* ein grundlegendes Verständnis der Headless-Funktionen von AEM haben.
* die Übersetzungsfunktionen von AEM verstehen und wissen, wie sie sich auf Headless-Inhalte beziehen.
* In der Lage sein, Ihre eigenen Headless-Inhalte zu übersetzen.

Ziel ist es, Ihnen ein breites Verständnis der Headless-Technologie zu vermitteln, davon, wie AEM Headless-Inhalte bereitstellt, und wie Sie diese übersetzen können. Wenn Sie mit keinem dieser Themen vertraut sind, ist dies Ihr idealer Ausgangspunkt.

Wenn Sie bereits mit AEM, Headless und Übersetzung vertraut sind, verfügen Sie vielleicht schon über das Grundwissen aus dieser Tour. Ziehen Sie auch unsere technische Dokumentation zu Rate, die im [Abschnitt Zusätzliche Ressourcen unten verlinkt ist.](#additional-resources)

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/home.md) verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen durch eine Erzählung, die dem nicht mit AEM vertrauten Leser hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Headless-Geschäftsfälle mit AEM zu lösen, sollten Sie mit den [AEM Headless-Touren](/help/journey-headless/overview.md) beginnen.

## Zielgruppe {#audience}

Diese Tour richtet sich an die Perona des Übersetzungsspezialisten, oft auch als Übersetzungsprojektmanager oder TPM (Translation Project Manager) bezeichnet. In dieser Tour werden die Anforderungen, Schritte und Ansätze zur Übersetzung von Headless-Inhalten in AEM beschrieben. In der Tour können zusätzliche Personas definiert werden, mit denen der Übersetzungsspezialist interagieren muss, aber der Blickwinkel für die Tour ist der des Übersetzungsspezialisten.

Bei dieser Tour wird davon ausgegangen, dass der Leser Erfahrung mit der Übersetzung von Inhalten in einem großen CMS-System hat, aber keine Kenntnisse über Headless-Technologie oder AEM hat.

Im Folgenden finden Sie die Personas, die in dieser Tour interagieren.

| Persona | Beschreibung | Rolle in der Tour |
|---|---|---|
| Übersetzungsspezialist | Definiert, welche Inhalte übersetzt werden sollen, und verwaltet diese Workflows | Zielgruppe dieser Tour |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die „headless“ bereitgestellt werden | Inhaltsautoren erstellen Inhalte, die der Übersetzungsspezialist übersetzen muss. |
| Administrator | Verwaltet die grundlegende Einrichtung und Konfiguration von AEM | Der Übersetzungsspezialist arbeitet mit dem Administrator zusammen, um die für die Übersetzung erforderlichen Konfigurationsänderungen vorzunehmen, z. B. die Installation eines Übersetzungs-Connectors. |
| Inhaltsarchitekt | Analysiert die Anforderungen an die Daten, die „headless“ bereitgestellt werden müssen, und definiert die Struktur für diese Daten. | Übersetzungsfachleute arbeiten mit der Inhaltsarchitektin bzw. dem Inhaltsarchitekten zusammen, um die Organisation des Content zu definieren, damit er leicht übersetzt werden kann. |

Die Informationen in dieser Journey können auch für andere Rollen nützlich sein, aber einige Informationen sind für bestimmte Rollen nicht relevant. Freuen Sie sich auf [neue Touren, mit denen wir künftig auf weitere Rollen eingehen.](/help/journey-documentation/home.md#journeys)

## Die Tour zur Headless-Übersetzung {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen Grundkenntnisse über das Übersetzen von Headless-Inhalten in AEM und enthalten Links zu detaillierten technischen Dokumentationen.

Sie können direkt zu einem bestimmten Teil der Tour gehen. Beachten Sie jedoch, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Wenn für Sie Headless-Übersetzungen in AEM also neu sind, empfehlen wir Ihnen, am Anfang zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Übersetzungs-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über Headless-Inhalte und wie Sie sie in AEM übersetzen können.](learn-about.md) | Lernen Sie die Headless-Konzepte, ihre Zuordnung zu AEM und die Theorie der Übersetzung in AEM kennen. |
| 2 | [Erste Schritte mit der Headless-Übersetzung in AEM](getting-started.md) | Erfahren Sie, wie Sie Ihre Headless-Inhalte organisieren und wie die Übersetzungs-Tools von AEM funktionieren. |
| 3 | [Konfigurieren der Übersetzungsintegration](configure-connector.md) | Erfahren Sie, wie Sie AEM mit einem Übersetzungs-Service verbinden. |
| 4 | [Konfigurieren von Übersetzungsregeln](translation-rules.md) | Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren. |
| 5 | [Übersetzen von Inhalten](translate-content.md) | Verwenden Sie die Übersetzungsintegration und -regeln, um Ihre Headless-Inhalte zu übersetzen. |
| 6 | [Veröffentlichen übersetzter Inhalte](publish-content.md) | Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzung aktualisieren können, wenn sich die zugrunde liegenden Inhalte ändern. |

## So geht es weiter {#what-is-next}

Jetzt können Sie mit Ihrer Adobe Headless-Übersetzungs-Tour beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Erfahren Sie mehr über Headless-Inhalte und wie man sie in AEM übersetzt](learn-about.md) zu lesen.

## Zusätzliche Ressourcen {#additional-resources}

Dokumentations-Touren zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem es eine Erzählung bereitstellt, die Sie durch komplexe, miteinander verknüpfte Prozesse und Funktionen führt. Eine Tour veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

Journeys sind dazu gedacht, eigenständig zu sein. Einige Journeys können jedoch miteinander verbunden werden. In diesen zusätzlichen Touren finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* [Headless-Autoren-Tour](/help/journey-headless/author/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie bei Ihrem ersten Headless-Projekt Inhalte modellieren können.
* [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) – Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager und erfahren Sie, wie Sie Inhalte für Ihr Projekt modellieren können.
* [AEM Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) – Beginnen Sie hier Ihre geführte Tour durch die leistungsstarken und flexiblen Headless-Funktionen von AEM und ihre Möglichkeiten und erfahren Sie, wie Sie diese in Ihrem ersten Entwicklungsprojekt nutzen können.
* [Technische Dokumentation zu AEM](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM und Headless-Technologien verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.
  * Eine [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)
* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – Wenn Sie es vorziehen, durch praktisches Arbeiten zu lernen, und technisch versiert sind, können Sie unsere nach API und Framework geordneten praktischen Tutorials nutzen, in denen die Erstellung und Verwendung von Programmen auf der Grundlage von AEM Headless behandelt wird.
* Das [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
