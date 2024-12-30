---
title: Zugriff auf benutzergenerierten Inhalt mit SRP
description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird der eigentliche UGC nicht im Knotenspeicher (JCR) von AEM gespeichert
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

# Zugriff auf benutzergenerierten Inhalt mit SRP {#accessing-ugc-with-srp}

## Über SRP {#about-srp}

Alle AEM Communities-Komponenten und -Funktionen basieren auf dem [Social Component Framework (SCF)](/help/communities/scf.md) das die SocialResourceProvider-API aufruft, um auf alle benutzergenerierten Inhalte zuzugreifen.

Bevor eine Community-Site erstellt wird, muss [Speicherressourcenanbieter (SRP)) ](/help/communities/working-with-srp.md) werden, um eine Implementierung auszuwählen, die der zugrunde liegenden [Topologie) ](/help/communities/topologies.md). Die SRP-Implementierungen basieren auf drei Speicheroptionen :

1. [ASRP](/help/communities/asrp.md) - Adobe-On-Demand-Speicher
1. [MSRP](/help/communities/msrp.md) - MongoDB
1. [JSRP](/help/communities/jsrp.md) - JCR

## Über UGC-Speicher {#about-ugc-storage}

Was Sie über die Speicherung von UGC wissen sollten, ist Folgendes: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird der eigentliche UGC nicht im [Knotenspeicher](/help/sites-deploying/data-store-config.md) (JCR) von AEM gespeichert.

Es kann zwar Knoten im JCR geben, die den UGC zur Bereitstellung nützlicher Metadaten überschatten, diese Knoten sind jedoch nicht mit dem tatsächlichen UGC zu verwechseln.

Siehe [Speicherressourcenanbieter - Übersicht.](/help/communities/srp.md)

## Best Practice {#best-practice}

Bei der Entwicklung benutzerdefinierter Komponenten sollten Entwickler darauf achten, unabhängig von der aktuell ausgewählten Topologie zu codieren, um so die Flexibilität zu behalten, in Zukunft zu einer neuen Topologie zu wechseln.

### Annahme: JCR nicht verfügbar {#assume-jcr-not-available}

JCR-spezifische Methoden sollten vermieden werden.

Zu verwendende Methoden :

* Sling-API (Sling-Ressource)

   * Gehen Sie nicht davon aus, dass JCR-Knoten vorhanden sind

* OSGi-Ereignisse

   * Gehen Sie nicht davon aus, dass JCR-Ereignisse vorhanden sind

* [socialResourceUtilities](/help/communities/socialutils.md#socialresourceutilities-package)
* [SCFUtilities](/help/communities/socialutils.md#scfutilities-package)

Zu vermeidende Methoden :

* Knoten-API
* JCR-Ereignisse
* Workflow-Starter (die JCR-Ereignisse verwenden)

### Verwenden der Sammlungssuche {#use-search-collections}

Verschiedene SRPs können unterschiedliche native Abfragesprachen aufweisen. Verwenden Sie Methoden aus dem Paket [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) , um die entsprechende Abfragesprache auszuführen.

Weitere Informationen finden Sie unter [Grundlagen suchen](/help/communities/search-implementation.md).

## Ressourcen {#resources}

* [Community-Inhaltsspeicher](/help/communities/working-with-srp.md) - Erläutert die verfügbaren SRP-Optionen für einen gemeinsamen Speicher für benutzergenerierten Inhalt
* [Übersicht über den Speicherressourcenanbieter](/help/communities/srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](/help/communities/srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele
* [Search Essentials](/help/communities/search-implementation.md) - Wichtige Informationen zum Suchen von benutzergenerierten Inhalten
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden
