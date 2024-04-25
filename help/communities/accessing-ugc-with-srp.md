---
title: Zugreifen auf UGC mit SRP
description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht in AEM Knotenspeicher (JCR) gespeichert
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 1157366f-2cc5-46e4-8ec6-e66fe5d0a0f6
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Zugreifen auf UGC mit SRP {#accessing-ugc-with-srp}

## Über SRP {#about-srp}

Alle AEM Communities-Komponenten und -Funktionen basieren auf dem [Social Component Framework (SCF)](/help/communities/scf.md), der die SocialResourceProvider-API aufruft, um auf alle benutzergenerierten Inhalte zuzugreifen.

Bevor eine Community-Site erstellt wird, muss die [Storage Resource Provider (SRP)](/help/communities/working-with-srp.md) muss so konfiguriert sein, dass eine Implementierung ausgewählt wird, die mit der zugrunde liegenden [Topologie](/help/communities/topologies.md). Die SRP-Implementierungen basieren auf drei Speicheroptionen:

1. [ASRP](/help/communities/asrp.md) - Adobe On-Demand-Speicher
1. [MSRP](/help/communities/msrp.md) - MongoDB
1. [JSRP](/help/communities/jsrp.md) - JCR

## Über UGC-Speicher {#about-ugc-storage}

Wichtig ist, dass Sie über die Speicherung von UGC wissen, wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht in gespeichert AEM [Knotenspeicher](/help/sites-deploying/data-store-config.md) (JCR).

Es kann zwar Knoten in JCR geben, die die UGC daran erinnern, nützliche Metadaten bereitzustellen, diese Knoten sind jedoch nicht mit der tatsächlichen UGC zu verwechseln.

Siehe [Übersicht über den Speicheranbieter.](/help/communities/srp.md)

## Best Practice {#best-practice}

Bei der Entwicklung benutzerdefinierter Komponenten sollten Entwickler darauf achten, unabhängig von der aktuell ausgewählten Topologie zu programmieren, und so flexibel bleiben, um in Zukunft zu einer neuen Topologie zu wechseln.

### Angenommen, JCR ist nicht verfügbar {#assume-jcr-not-available}

JCR-spezifische Methoden sollten vermieden werden.

Zu verwendende Methoden :

* Sling-API (Sling-Ressource)

   * Angenommen, es gibt JCR-Knoten

* OSGi-Ereignisse

   * Angenommen, es gibt JCR-Ereignisse

* [SocialResourceUtilities](/help/communities/socialutils.md#socialresourceutilities-package)
* [SCFUtilities](/help/communities/socialutils.md#scfutilities-package)

Methoden zur Vermeidung von :

* Knoten-API
* JCR-Ereignisse
* Workflow-Starter (die JCR-Ereignisse verwenden)

### Verwenden von Suchkollektionen {#use-search-collections}

Verschiedene SRPs können unterschiedliche native Abfragesprachen haben. Verwenden Sie Methoden aus dem [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) -Paket, um die entsprechende Abfragesprache auszuführen.

Weitere Informationen finden Sie unter [Suchgrundlagen](/help/communities/search-implementation.md).

## Ressourcen {#resources}

* [Community-Inhaltsspeicherung](/help/communities/working-with-srp.md) - beschreibt die verfügbaren SRP-Optionen für einen UGC Common Store
* [Übersicht über den Speicheranbieter](/help/communities/srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](/help/communities/srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Suchgrundlagen](/help/communities/search-implementation.md) - wesentliche Informationen für die Suche nach UGC
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
