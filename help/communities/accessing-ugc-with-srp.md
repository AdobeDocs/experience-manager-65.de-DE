---
title: Zugriff auf UGC mit SRP
seo-title: Zugriff auf UGC mit SRP
description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht im AEM-Node Store (JCR) gespeichert
seo-description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht im AEM-Node Store (JCR) gespeichert
uuid: 30549f93-e370-4b8b-a35a-69e05884227e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 72d4022c-43ba-49e0-b94c-f2beabaef64d
docset: aem65
translation-type: tm+mt
source-git-commit: 974d58efa560b90234d5121a11bdb445c7bf94cf

---


# Zugriff auf UGC mit SRP {#accessing-ugc-with-srp}

## Informationen zu SRP {#about-srp}

Alle Komponenten und Funktionen von AEM Communities basieren auf dem [Social-Komponenten-Framework (SCF)](/help/communities/scf.md), das die SocialResourceProvider-API aufruft, um auf alle benutzergenerierten Inhalte zuzugreifen.

Bevor eine Community-Site erstellt wird, muss der [Datenspeicherung Resource Provider (SRP)](/help/communities/working-with-srp.md) so konfiguriert sein, dass eine Implementierung ausgewählt wird, die mit der zugrunde liegenden [Topologie](/help/communities/topologies.md)übereinstimmt. Die SRP-Implementierungen basieren auf drei Optionen für die Datenspeicherung:

1. [ASRP](/help/communities/asrp.md) - On-Demand-Datenspeicherung von Adobe
1. [MSRP](/help/communities/msrp.md) - MongoDB
1. [JSRP](/help/communities/jsrp.md) - JCR

## UGC-Datenspeicherung {#about-ugc-storage}

Wichtig ist, dass Sie über die Datenspeicherung von UGC wissen, wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die eigentliche UGC nicht im AEM- [Node Store](/help/sites-deploying/data-store-config.md) (JCR) gespeichert.

Es gibt zwar Knoten in JCR, die den UGC zur Bereitstellung nützlicher Metadaten schatten, diese Knoten sind jedoch nicht mit dem tatsächlichen UGC zu verwechseln.

Siehe Übersicht über den [Datenspeicherung Resource Provider.](/help/communities/srp.md)

## Best Practice {#best-practice}

Bei der Entwicklung benutzerdefinierter Komponenten sollten Entwickler darauf achten, dass sie unabhängig von der aktuell gewählten Topologie kodieren, um in Zukunft flexibel zu einer neuen Topologie zu wechseln.

### Angenommen, JCR ist nicht verfügbar {#assume-jcr-not-available}

JCR-spezifische Methoden sollten vermieden werden.

Zu verwendende Methoden:

* Sling API (Sling Resource)

   * geht nicht davon aus, dass JCR-Knoten vorhanden sind

* OSGi-Ereignis

   * setzen Sie nicht voraus, dass JCR-Ereignis vorhanden sind

* [SocialResourceUtilities](/help/communities/socialutils.md#socialresourceutilities-package)
* [SCFUtilities](/help/communities/socialutils.md#scfutilities-package)

Methoden zur Vermeidung:

* Knoten-API
* JCR-Ereignisse
* Workflow-Starter (die JCR-Ereignis verwenden)

### Suchsammlungen verwenden {#use-search-collections}

Verschiedene SRPs können unterschiedliche Sprachen für die native Abfrage haben. Es wird empfohlen, Methoden aus dem [Paket com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) zu verwenden, um die entsprechende Abfrage auszuführen.

For more information, see [Search Essentials](/help/communities/search-implementation.md).

## Ressourcen {#resources}

* [Community Content Datenspeicherung](/help/communities/working-with-srp.md) - Diskussion der verfügbaren SRP-Optionen für einen UGC Common Store
* [Übersicht über](/help/communities/srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](/help/communities/srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Essentials](/help/communities/search-implementation.md) suchen - wesentliche Informationen für die Suche nach UGC
* [SocialUtils Refactoring](/help/communities/socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

