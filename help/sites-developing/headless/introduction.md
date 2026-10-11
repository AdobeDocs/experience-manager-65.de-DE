---
title: Headless-Entwicklung für AEM 6.5 Sites
description: Erfahren Sie, wie die leistungsstarken Headless-Funktionen von AEM 6.5 wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API zusammenarbeiten, um Ihnen die zentrale Verwaltung Ihrer Erlebnisse und deren kanalübergreifende Bereitstellung zu ermöglichen.
exl-id: b6598bcf-b2ce-403a-87cf-6895fec8a91b
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d429a63e-ade4-4117-b04e-9b996d1c94ef
    internal-label: Integrations
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: a02b73a7-bdfc-4225-bdfd-69f7891ab55e
    internal-label: GraphQL
  - id: d781bc8f-52af-43f6-84d0-b73e59a130d5
    internal-label: Persisted queries
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 100%
---
# Headless-Entwicklung für AEM 6.5 Sites {#headless-development}

Erfahren Sie, wie die leistungsstarken Headless-Funktionen von AEM 6.5 wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API zusammenarbeiten, um Ihnen die zentrale Verwaltung Ihrer Erlebnisse und deren kanalübergreifende Bereitstellung zu ermöglichen.

## Übersicht {#overview}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihre Zielgruppe bereitzustellen – wo auch immer sie sich befindet und unabhängig vom Kanal.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack- und Hybrid-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungskonzept zur Implementierung von Web-Erlebnissen.

![AEM-Implementierungsmodelle](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

## Vergleich von Headful und Headless {#headful-headless}

Dieses Dokument konzentriert sich auf das vollständige Headless-Implementierungsmodell von AEM. In AEM muss die Entscheidung zwischen Headful und Headless aber keine Entweder-oder-Entscheidung sein. Headless-Funktionen können verwendet werden, um Content zu verwalten und für verschiedene Endpunkte bereitzustellen sowie um Inhaltserstellern gleichzeitig die Bearbeitung von Single Page Applications zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Headful und Headless in AEM](/help/sites-developing/headful-headless.md).

## AEM 6.5 und Headless {#aem-headless}

AEM 6.5 ist ein flexibles Tool für das Headless-Implementierungsmodell, das drei leistungsstarke Services bietet:

1. Inhaltsmodelle
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Diese werden von Informationsarchitekten im Inhaltsfragmentmodell-Editor in AEM definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Inhaltsfragmente
   * Inhaltsfragmente sind Instanziierungen von Inhaltsmodellen.
   * Diese werden von Inhaltsautoren mit dem Inhaltsfragment-Editor in AEM erstellt.
   * Sie werden in AEM Assets gespeichert und in der Administrator-Benutzeroberfläche von Assets verwaltet.
1. Content-API für die Bereitstellung
   * Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   * Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   * Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Kernkomponenten für Inhaltsfragmente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de) möglich.

## Erste Schritte mit AEM Headless {#first-steps}

Für die ersten Schritte mit AEM Headless-Funktionen stehen verschiedene Ressourcen zur Verfügung. Sie sind für verschiedene Nutzungsszenarien vorgesehen, bieten jedoch alle einen umfassenden Überblick über AEM Headless-Funktionen.

| Ressource | Beschreibung | Typ | Zielgruppe | Schätzung Zeit |
|---|---|---|---|---|
| [Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) | **Benutzer, die noch nicht mit AEM- und Headless**-Technologien vertraut sind, erhalten hier eine umfassende Einführung in AEM und seine Headless-Funktionen, von der Theorie des Headless-Systems bis zum Go-Live Ihres ersten Headless-Projekts. | -Anleitung | Entwickler, die noch **nicht mit AEM und Headless vertraut** sind | 1 Stunde |
| [Erste Schritte mit Headless](/help/sites-developing/headless/getting-started/introduction.md) | **Erfahrene AEM-Anwender**, die eine kurze Zusammenfassung der wichtigsten AEM-Headless-Funktionen benötigen, sollten sich diesen Schnellstart-Überblick ansehen. | Schnellstart | Entwickler, Administratoren **mit AEM-Erfahrung** | 20 Minuten |
| [Praktisches Tutorial für die ersten Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de) | **Wenn Sie einen praxisnahen Ansatz bevorzugen und mit AEM vertraut sind**: dieses Tutorial steigt direkt in die Erstellung eines einfachen Headless-Projekts ein. | Tutorial | Entwickler | 2 Stunden |
| [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de) | Diese Ressourcensammlung wird für **neue** sowie für **erfahrene** Entwickelnde bereitgestellt. | Ressourcensammlung | Entwickelnde | |
