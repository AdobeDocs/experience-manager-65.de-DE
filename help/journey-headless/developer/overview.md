---
title: AEM Headless-Entwickler-Tour
description: AEM Headless-CMS-Dokumentation. Dieser Leitfaden bietet Ihnen eine Einführung zu den effektiven und flexiblen Headless-Features von AEM und deren Funktionen und erläutert, wie Sie sie bei Ihrem ersten Entwicklungsprojekt nutzen können.
source-git-commit: 919cef01470dd930884e97b15f2d40a38872c0d0
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 53%

---

# AEM Headless-Entwickler-Tour {#aem-headless-developer-journey}

Diese angeleitete Tour bietet Ihnen eine Einführung zu den effektiven und flexiblen Headless-Features von AEM und deren Funktionen. Sie veranschaulicht, wie Sie sie bei Ihrem ersten Headless-Entwicklungsprojekt nutzen können. Diese Journey bietet Ihnen alle AEM Headless-Dokumentation, die Sie zur Entwicklung Ihrer ersten Headless-Anwendung benötigen.

## Einführung {#introduction}

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von digitalen Erlebnissen.

Dieser Leitfaden führt Sie durch die Headless-Implementierungsthemen in AEM, sodass Sie nach Abschluss Folgendes tun:

* Umfassendes Verständnis davon, was die Headless-Bereitstellung von Inhalten ist und welche Vorteile sie bietet
* Kenntnisse der Headless-Funktionen von AEM und wie sie zusammenarbeiten, um Headless-Erlebnisse bereitzustellen
* Fähigkeit, die ersten Schritte zur Implementierung Ihres ersten AEM Headless-Projekts auszuführen

## Journey AEM Dokumentation {#documentation-journeys}

[Eine Journey der Dokumentation](/help/journey-documentation/home.md) verbindet viele verschiedene und vielleicht komplizierte Themen und Funktionen, indem eine Erzählung bereitgestellt wird, die dem Leser hilft, der neu zu AEM sein kann, ein Geschäftsproblem von Anfang bis Ende zu verstehen und zu lösen, während er von Anfang bis Ende nur ein minimales vorheriges Thema oder AEM Wissen angeht.

Die Journey der Dokumentation basieren auf Best-Practice-Prinzipien, die durch aktuelle Forschungsarbeiten der Adobe, bewährte Implementierungserfahrungen von Adobe-Beratern und Rückmeldungen von Kundenprojekten informiert werden.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Headless-Geschäftsfälle mit AEM zu lösen, [AEM Headless-Journey](/help/journey-headless/home.md) sind, wo sie beginnen sollen.

>[!TIP]
>
> Wenn Sie **Lernen durch** und technisch geneigt sind, besuchen Sie die AEM Headless-Tutorials, die nach API und Framework organisiert sind und in der [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) am Ende dieses Dokuments.

## Zielgruppe {#audience}

Diese Tour ist für die Entwickler-Persona konzipiert. Sie legt die Anforderungen, Schritte und den Ansatz eines AEM Headless-Projekts aus Entwicklersicht dar. Die Journey definiert zusätzliche Personas, mit denen der Entwickler für ein erfolgreiches Projekt interagieren muss, aber die Sicht auf die Journey ist die des Entwicklers.

Im Folgenden finden Sie die Rollen, die in dieser Journey interagieren.

| Rolle | Beschreibung | Rolle in dieser Journey |
|---|---|---|
| Entwickler (Zielgruppe) | Hat Erfahrung bei der Entwicklung von Headless-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen | Zielgruppe dieser Journey |
| Inhaltsautor | Erstellt und verwaltet Headless-Inhalte | Inhaltsautoren erstellen Inhalte, die der Entwickler per Headless-Implementierung bereitstellt. |
| Administrator | Verwalten der grundlegenden Einrichtung und Konfiguration von AEM | Der Entwickler arbeitet mit dem Administrator zusammen, um für die Entwicklung erforderliche Konfigurationsänderungen vorzunehmen. |
| Inhaltsarchitektur | Analysiert die Anforderungen an die Daten, die Headless-Implementierung erfolgen muss, und definiert die Struktur für diese Daten | Entwickler arbeiten mit dem Inhaltsarchitekten zusammen, um die Struktur der Daten und die Anforderungen für die Bereitstellung Headless zu verstehen. |

Informationen in dieser Journey können natürlich für alle Personen nützlich sein, aber einige Informationen können für bestimmte Rollen überflüssig sein. Bleiben Sie dran für [bevorstehende Journey, in denen zusätzliche Rollen behandelt werden.](/help/journey-documentation/home.md#journeys)

## Die Headless-Entwickler-Tour {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen Grundkenntnisse über Headless-Funktionen in AEM und bieten Links zu detaillierten technischen Dokumentationen.

Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Einsteigern empfiehlt sich daher, von vorn zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung |
|---|---|---|
| 0 | AEM Headless-Entwickler-Tour | Dieses Dokument |
| 1 | [Erfahren Sie mehr über die CMS-Headless-Entwicklung](learn-about.md) | Hier erfahren Sie mehr über Headless-Technologie und wann sie verwendet werden kann. |
| 2 | [Erste Schritte mit AEM Headless](getting-started.md) | Hier erfahren Sie mehr über die Voraussetzungen für AEM Headless. |
| 3 | [Gestalten Ihres ersten Erlebnisses mit AEM Headless ](path-to-first-experience.md) | Richten Sie Ihre Entwicklungsumgebung ein und erfahren Sie, wie Sie ein einfaches Programm mit AEM Headless integrieren. |
| 4 | [Erfahren Sie, wie Sie Ihre Inhalte modellieren](model-your-content.md) | Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren. Setzen Sie dann diese Struktur für Adobe Experience Manager (AEM) mithilfe von Inhaltsfragmentmodellen und Inhaltsfragmenten um, um sie kanalübergreifend wiederzuverwenden. |
| 5 | [Zugreifen auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) | Hier erfahren Sie, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können. |
| 6 | [Aktualisieren Ihres Inhalts über AEM Assets-APIs](update-your-content.md) | Hier erfahren Sie, wie Sie mit einer REST-API Ihre Inhaltsfragmente aktualisieren können. |
| 7 | [So fügen Sie alles zusammen – Ihr Programm und Ihre Inhalte in AEM Headless](put-it-all-together.md) | Erfahren Sie, wie Sie mit dem AEM Headless-SDK Ihr AEM-Projekt für den Go-live vorbereiten können. |
| 8 | [Live-Schalten Ihres Headless-Programms](go-live.md) | Hier erfahren Sie, wie Sie Ihr Programm live schalten, indem Sie Ihren lokalen Code in Git in das Git-Repository von Cloud Manager für die CI/CD-Pipeline verschieben. |
| 9 | [Optional – Erstellen von Single Page Applications (SPA) mit AEM](create-spa.md) | Sobald Sie sich mit den AEM Headless-Funktionen vertraut gemacht haben, sollten Sie sich damit befassen, wie Sie eine Headful- und Headless-Bereitstellung kombinieren und in Erfahrung bringen, wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können. |

## Wie geht es weiter {#what-is-next}

Jetzt sind Sie bereit, mit Ihrer Adobe Headless-Tour zu beginnen. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Erfahren Sie mehr über die CMS-Headless-Entwicklung](learn-about.md) zu lesen.

### Wählen Sie Ihren eigenen Weg {#choose-your-path}

Adobe möchte jedoch, dass Sie Erfolg haben, wenn Sie mit Ihrem AEM Headless-Projekt beginnen, unabhängig von Ihrem Lernstil. Erwägen Sie daher bitte die beiden folgenden Optionen.

* Wenn Sie darüber hinaus **mehr über Headless-Konzepte und -Technologien von AEM** erfahren möchten, sollten Sie Ihre AEM Headless-Tour wie empfohlen fortsetzen, indem Sie sich das Dokument [Modellieren Ihres Inhalts](model-your-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre Content-Struktur in AEM modellieren.
* Wenn Sie **praktische Erfahrungen** vorziehen, empfehlen wir Ihnen das praxisnahe Tutorial [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de). Dort können Sie sich direkt mit der AEM Headless-Entwicklung vertraut machen, indem Sie ein einfaches Projekt implementieren, um AEM Headless-Inhalte bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Die Journey der Dokumentation zeigen Ihnen, wie AEM ein Geschäftsproblem löst, indem sie eine Erzählung bereitstellen, die Sie durch komplexe, miteinander verknüpfte Prozesse und Funktionen führt. Eine Journey veranschaulicht, wie mehrere Funktionen zusammenarbeiten, um eine einzige Geschäftsanforderung zu erfüllen.

Journey sind so konzipiert, dass sie auf sich allein gestellt stehen. Einige davon können jedoch miteinander verbunden werden. Weitere Informationen dazu, wie AEM leistungsstarken Funktionen zusammenarbeiten, finden Sie in diesen zusätzlichen Journey .

* [AEM Headless-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de) - Wenn Sie lieber lernen möchten, indem Sie tun und technisch geneigt sind, nehmen Sie unsere praxisorientierten Tutorials organisiert von API und Framework, die die Erstellung und Verwendung von Anwendungen, die auf AEM Headless aufbauen.
* [AEM Headless Translation Journey](/help/journey-headless/translation/overview.md) - Diese Journey-Dokumentation vermittelt Ihnen ein umfassendes Verständnis der Headless-Technologie, wie AEM Headless Content bereitstellen und wie Sie ihn übersetzen können.
* [Headless-Authoring-Journey](/help/journey-headless/author/overview.md) - Beginnen Sie hier für eine geführte Journey durch die leistungsstarken und flexiblen Headless-Features von AEM, deren Funktionen und wie Sie Ihre Inhalte in Ihrem ersten Headless-Projekt modellieren können.
* [Headless Architect-Journey](/help/journey-headless/architect/overview.md) - Beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen, Headless-Funktionen von Adobe Experience Manager und wie Sie Inhalte für Ihr Projekt modellieren können.
* [AEM technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de) - Wenn Sie bereits über ein festes Verständnis von AEM und Headless-Technologien verfügen, können Sie unsere ausführlichen technischen Dokumente direkt konsultieren.
