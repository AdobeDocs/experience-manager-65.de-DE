---
title: AEM Headless-Entwickler-Tour
description: AEM Headless-CMS-Dokumentation. Beginnen Sie hier Ihre geführte Tour durch die leistungsstarken und flexiblen Headless-Funktionen von AEM und ihre Möglichkeiten und erfahren Sie, wie Sie diese in Ihrem ersten Entwicklungsprojekt nutzen können.
exl-id: f24fb308-daa7-426f-ba45-37a236b5a500
source-git-commit: 9c517590c2b78eed7c52e33e0a106237a2af3bb7
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 97%

---

# AEM Headless-Entwickler-Tour {#aem-headless-developer-journey}

Beginnen Sie hier Ihre geführte Tour durch die leistungsstarken und flexiblen Headless-Funktionen von AEM und ihre Möglichkeiten und erfahren Sie, wie Sie diese in Ihrem ersten Headless-Entwicklungsprojekt nutzen können. Auf dieser Tour erhalten Sie die gesamte AEM Headless-Dokumentation, die Sie zur Entwicklung Ihres ersten Headless-Programms benötigen.

## Einführung {#introduction}

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von digitalen Erlebnissen.

Dieser Leitfaden führt Sie durch die meisten Themen in AEM zur Headless-Implementierung, sodass Sie nach Abschluss:

* Umfassendes Verständnis davon, was die Headless-Bereitstellung von Inhalten ist und welche Vorteile sie bietet
* Kenntnisse der Headless-Funktionen von AEM und wie sie zusammenarbeiten, um Headless-Erlebnisse bereitzustellen
* Fähigkeit, die ersten Schritte zur Implementierung Ihres ersten AEM Headless-Projekts auszuführen

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/home.md) verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen durch eine Erzählung, die dem nicht mit AEM vertrauten Leser hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Headless-Geschäftsfälle mit AEM zu lösen, sollten Sie mit den [AEM Headless-Touren](/help/journey-headless/home.md) beginnen.

>[!TIP]
>
>Wenn Sie es vorziehen, durch **praktisches Tun zu lernen** und technisch versiert sind, besuchen Sie die AEM Headless-Tutorials, die nach API und Framework gegliedert sind und im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments zur Verfügung stehen.

## Zielgruppe {#audience}

Diese Tour ist speziell für die Rolle des Entwicklers ausgelegt und legt die Anforderungen und Schritte sowie den Ansatz von AEM Headless-Projekten aus Entwicklersicht dar. Sie definiert weitere Rollen, mit denen Entwickler interagieren müssen, um zum Gelingen von Projekten beizutragen. Zugeschnitten ist die Tour jedoch auf Entwickler.

Im Folgenden finden Sie die Rollen, die in dieser Tour interagieren.

| Persona | Beschreibung | Rolle in dieser Tour |
|---|---|---|
| Entwickler (Zielgruppe) | Hat Erfahrung mit der Entwicklung von Headless-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen | Zielgruppe dieser Tour |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die „headless“ bereitgestellt werden. | Inhaltsautoren erstellen Inhalte, die der Entwickler „headless“ bereitstellt. |
| Administrator | Verwaltet die grundlegende Einrichtung und Konfiguration von AEM | Der Entwickler arbeitet mit dem Administrator zusammen, um für die Entwicklung erforderliche Konfigurationsänderungen vorzunehmen. |
| Inhaltsarchitekt | Analysiert die Anforderungen an die Daten, die „headless“ bereitgetellt werden müssen, und definiert die Struktur für diese Daten. | Die Entwickler arbeiten mit dem Inhaltsarchitekten zusammen, um die Struktur der Daten und die Anforderungen für die Headless-Bereitstellung der Daten zu verstehen. |

Die Informationen in dieser Tour können natürlich auch für andere Rollen nützlich sein, aber einige Informationen sind für bestimmte Rollen nicht relevant. Freuen Sie sich auf [neue Touren, mit denen wir künftig auf weitere Rollen eingehen.](/help/journey-documentation/home.md#journeys)

## Die Headless-Entwickler-Tour {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen Grundkenntnisse über Headless-Funktionen in AEM und bieten Links zu detaillierten technischen Dokumentationen.

Sie können direkt zu einem bestimmten Teil der Tour gehen. Beachten Sie jedoch, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Daher empfiehlt Adobe, dass Sie, wenn Sie neu bei AEM sind, am Anfang beginnen und sequenziell fortfahren.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Entwickler-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über die CMS-Headless-Entwicklung](learn-about.md) | Hier erfahren Sie mehr über Headless-Technologie und wann sie verwendet werden kann. |
| 2 | [Erste Schritte mit AEM Headless](getting-started.md) | Hier erfahren Sie mehr über die Voraussetzungen für AEM Headless. |
| 3 | [Gestalten Ihres ersten Erlebnisses mit AEM Headless ](path-to-first-experience.md) | Richten Sie Ihre Entwicklungsumgebung ein und erfahren Sie, wie Sie ein einfaches Programm mit AEM Headless integrieren. |
| 4 | [Erfahren Sie, wie Sie Ihre Inhalte modellieren](model-your-content.md) | Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren. Setzen Sie dann diese Struktur für Adobe Experience Manager (AEM) mithilfe von Inhaltsfragmentmodellen und Inhaltsfragmenten um, um sie kanalübergreifend wiederzuverwenden. |
| 5 | [Zugreifen auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) | Hier erfahren Sie, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können. |
| 6 | [So aktualisieren Sie Ihre Inhalte über AEM Assets-APIs:](update-your-content.md) | Hier erfahren Sie, wie Sie mit einer REST-API Ihre Inhaltsfragmente aktualisieren können. |
| 7 | [So fügen Sie alles zusammen – Ihr Programm und Ihre Inhalte in AEM Headless](put-it-all-together.md) | Erfahren Sie, wie Sie mit dem AEM Headless-SDK Ihr AEM-Projekt für den Go-live vorbereiten können. |
| 8 | [Live-Schalten Ihres Headless-Programms](go-live.md) | Hier erfahren Sie, wie Sie Ihr Programm live bereitstellen, indem Sie Ihren lokalen Code in Git in das Git-Repository von Cloud Manager für die CI/CD-Pipeline verschieben. |
| 9 | [Optional – Erstellen von Single Page Applications (SPA) mit AEM](create-spa.md) | Sobald Sie sich mit den AEM Headless-Funktionen vertraut gemacht haben, sollten Sie sich damit befassen, wie Sie eine Headful- und Headless-Bereitstellung kombinieren und in Erfahrung bringen, wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können. |

## Wie geht es weiter {#what-is-next}

Jetzt sind Sie bereit, mit Ihrer Adobe Headless-Tour zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Erfahren Sie mehr über die CMS-Headless-Entwicklung](learn-about.md) zu lesen.

### Wählen Sie Ihren eigenen Weg {#choose-your-path}

Adobe möchte jedoch, dass Sie Erfolg haben, wenn Sie mit Ihrem AEM Headless-Projekt beginnen, unabhängig von Ihrem Lernstil. Erwägen Sie daher bitte die beiden folgenden Optionen.

* Wenn Sie darüber hinaus **mehr über Headless-Konzepte und -Technologien von AEM** erfahren möchten, sollten Sie Ihre AEM Headless-Tour wie empfohlen fortsetzen, indem Sie sich das Dokument [Modellieren Ihres Inhalts](model-your-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre Content-Struktur in AEM modellieren.
* Wenn Sie **praktische Erfahrungen** vorziehen, empfehlen wir Ihnen das praxisnahe Tutorial [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de). Dort können Sie sich direkt mit der AEM Headless-Entwicklung vertraut machen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Dokumentations-Touren zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem es eine Erzählung bereitstellt, die Sie durch komplexe, miteinander verknüpfte Prozesse und Funktionen führt. Eine Tour veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

Diese Touren sind so konzipiert, dass sie für sich allein stehen können. Einige davon können jedoch miteinander verbunden werden. In diesen zusätzlichen Touren finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) – Wenn Sie es vorziehen, durch praktisches Arbeiten zu lernen und technisch versiert sind, können Sie unsere nach API und Framework geordneten praktischen Tutorials nutzen, in denen die Erstellung und Verwendung von Programmen auf der Grundlage von AEM Headless behandelt wird.
* [AEM Headless Übersetzungs-Tour](/help/journey-headless/translation/overview.md) – Diese Dokumentations-Tour vermittelt Ihnen ein umfassendes Verständnis der Headless-Technologie sowie davon, wie AEM Headless Inhalte bereitstellt und wie Sie sie übersetzen können.
* [Headless-Autoren-Tour](/help/journey-headless/author/overview.md) – Diese angeleitete Tour bietet Ihnen eine Einführung zu den leistungsstarken und flexiblen Headless-Funktionen von AEM und deren Möglichkeiten. Sie veranschaulicht, wie Sie bei Ihrem ersten Headless-Projekt Inhalte modellieren können.
* [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) – Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager und erfahren Sie, wie Sie Inhalte für Ihr Projekt modellieren können.
* [Technische Dokumentation zu AEM](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM und Headless-Technologien verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.

   * Ein [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)

* Die [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
