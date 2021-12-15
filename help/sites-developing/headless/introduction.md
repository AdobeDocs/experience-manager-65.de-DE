---
title: 'Headless-Entwicklung für AEM 6.5 Sites '
description: Erfahren Sie, wie AEM leistungsstarken Headless-Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API von 6.5 zusammenarbeiten, damit Sie Ihre Erlebnisse zentral verwalten und kanalübergreifend bereitstellen können.
source-git-commit: 2f400d209148278f0695f7b9523b58bba6845cfb
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 64%

---


# Headless-Entwicklung für AEM 6.5 Sites {#headless-development}

Erfahren Sie, wie AEM leistungsstarken Headless-Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API von 6.5 zusammenarbeiten, damit Sie Ihre Erlebnisse zentral verwalten und kanalübergreifend bereitstellen können.

## Übersicht {#overview}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihr Zielgruppe überall und unabhängig vom Kanal bereitzustellen.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack- und Hybrid-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

![AEM-Implementierungsmodelle](assets/aem-implementation-models.png)

## Vergleich von Headful und Headless {#headful-headless}

Dieses Dokument konzentriert sich auf das vollständige Headless-Implementierungsmodell von AEM. In AEM muss die Entscheidung zwischen Headful und Headless aber keine Entweder-Oder-Entscheidung sein. Headless-Funktionen können verwendet werden, um Content zu verwalten und für verschiedene Endpunkte bereitzustellen sowie um Inhaltserstellern gleichzeitig die Bearbeitung von Single Page Applications zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Headful und Headless in AEM](/help/sites-developing/headful-headless.md).

## AEM 6.5 und Headless {#aem-headless}

AEM 6.5 ist ein flexibles Tool für die Headless-Implementierung, das drei leistungsstarke Dienste anbietet:

1. Inhaltsmodelle
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Diese werden von Informationsarchitekten im Inhaltsfragmentmodell-Editor in AEM definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Inhaltsfragmente
   * Inhaltsfragmente sind Instanziierungen von Inhaltsmodellen.
   * Diese werden von Inhaltsautoren mit dem Inhaltsfragment-Editor in AEM erstellt.
   * Sie werden in AEM Assets gespeichert und in der Administrator-Benutzeroberfläche von Assets verwaltet.
1. Inhalts-API für die Bereitstellung
   * Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   * Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   * Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Kernkomponenten für Inhaltsfragmente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de) möglich.

## Erste Schritte mit AEM Headless {#first-steps}

Es stehen eine Reihe von Ressourcen zur Verfügung, mit denen Sie mit AEM Headless-Funktionen beginnen können. Sie sind für verschiedene Anwendungsfälle vorgesehen, bieten jedoch alle einen umfassenden Überblick über AEM Headless-Funktionen.

| Ressource | Beschreibung | Typ | Zielgruppe | Schätzung Zeit |
|---|---|---|---|---|
| [Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) | **Für Anwender, die neu AEM und Headless sind** Technologien, beginnen Sie hier für eine umfassende Einführung in AEM und seine Headless-Features von der Theorie des Headless-Lebens bis hin zu Ihrem ersten Headless-Projekt. | -Anleitung | Entwickler **neu für AEM und Headless** | 1 Stunde |
| [Erste Schritte mit Headless](/help/sites-developing/headless/getting-started/introduction.md) | **Für erfahrene AEM** die eine kurze Zusammenfassung der wichtigsten AEM Headless-Funktionen benötigen, sehen Sie sich diese Schnellstartübersicht an. | Schnellstart | Entwickler, Administratoren **mit AEM Erlebnis** | 20 Minuten |
| [Praktisches Tutorial für die ersten Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de) | **Wenn Sie einen praxisnahen Ansatz bevorzugen und mit AEM vertraut sind**, taucht dieses Tutorial direkt in die Erstellung eines einfachen Headless-Projekts ein. | Tutorial | Entwickler | 2 Stunden |
