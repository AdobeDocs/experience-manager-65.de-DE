---
title: Best Practices für die Bereitstellung
seo-title: Best Practices für die Bereitstellung
description: Best Practices für die Bereitstellung und Wartung
seo-description: Best Practices für die Bereitstellung und Wartung
uuid: 4546ed2c-43d5-40f3-874f-567b324e78c2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 4b5c0677-c630-4fae-867e-4f4583ac8507
exl-id: 4cbc0a30-d5f6-40ff-b7f6-8d64762e1970
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 60%

---

# Best Practices für die Bereitstellung{#deploying-best-practices}

In den Best Practices für die Bereitstellung wird beschrieben, wie AEM am effizientesten und wirkungsvollsten bereitgestellt und gewartet wird. Diese laufend erweiterte Liste von Themen enthält eine Vielzahl von AEM-Bereichen.

Für die folgenden Bereiche ist Dokumentation zu Best Practices und Empfehlungen für die Bereitstellung und Wartung verfügbar:

* [OAK](#oak)
* [Communities](#communities)
* [Benutzeroberfläche](#ui)
* [Leistung](#performance)

Informationen zu Best Practices zur Verwaltung, Entwicklung oder Inhaltserstellung finden Sie in den folgenden Abschnitten:

* [Best Practices für die Verwaltung ](/help/sites-administering/administer-best-practices.md)
* [Best Practices für die Entwicklung](/help/sites-developing/best-practices.md)
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)

Die folgenden Tabellen enthalten auch Beschreibungen und Links zu speziellen Dokumenten.

## OAK {#oak}

[Oak](/help/sites-deploying/platform.md) ist ein leistungsstarkes skalierbares, hierarchisches Inhaltsrepository und bildet die Basis von AEM.

<table>
 <tbody>
  <tr>
   <td><p>Skalierbarkeit, Leistung und Notfallwiederherstellung</p> </td>
   <td><a href="/help/sites-deploying/performance.md">Leistung und Skalierbarkeit</a></td>
   <td>Enthält ein Whitepaper über die technischen Funktionen für Agilität, hohe Leistung und Klangkatastrophen</td>
  </tr>
  <tr>
   <td>Empfohlene OAK-Implementierungen</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Empfohlene Bereitstellungen</a></td>
   <td>Beschreibt Bereitstellungsszenarien</td>
  </tr>
  <tr>
   <td>Mongo-Topologie</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Best Practices für die Mongo-Topologie</a></td>
   <td>Beschreibt die Mongo-Topologie - wann welche Topologie verwendet werden soll.</td>
  </tr>
  <tr>
   <td>Datenspeicheroptionen</td>
   <td><a href="/help/sites-deploying/data-store-config.md">Konfigurieren von Knoten und Datenspeichern</a></td>
   <td>In diesem Dokument werden Best Practices zum Speichern von Binärdaten und Inhaltsknoten erläutert. Enthält Informationen zum Speicherdienst Amazon S3.</td>
  </tr>
  <tr>
   <td>Suchen in OAK</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Best Practices für Abfragen und Indizierung</a><br /> </td>
   <td>Beschreibt Best Practices für die Indizierung von Inhalten.</td>
  </tr>
 </tbody>
</table>

## Communities {#communities}

AEM Communities vereinfacht die Erstellung und Verwaltung von On-Premise-Communities. Best Practices für AEM Communities werden hier beschrieben:

[Community-Inhaltsspeicher](/help/communities/working-with-srp.md)  - Behandelt die neue Funktion des gemeinsamen Speichers für benutzergenerierte Inhalte (UGC) und Überlegungen zur Auswahl der zugrunde liegenden  [Topologie](/help/communities/topologies.md).

[Empfohlene Bereitstellungen für Communities](/help/sites-deploying/recommended-deploys.md#considerations-for-aem-communities)  - Beschreibt die empfohlenen Bereitstellungen für Communities. |

## Benutzeroberfläche {#ui}

Best Practices für die Benutzeroberfläche werden hier beschrieben: 

[Empfehlungen für Kunden zur Benutzeroberfläche](/help/sites-deploying/ui-recommendations.md)

AEM verfügt derzeit über zwei Benutzeroberflächen: klassische und Touch-optimierte Benutzeroberfläche in derselben Version. Daher müssen sich Kunden während der Projektimplementierung für die Nutzung der einen oder anderen entscheiden. Dieses Dokument soll bei der Suche nach der richtigen Wahl helfen.

## Leistung {#performance}

Best Practices über die Leistung sind hier aufgeführt:

<table>
 <tbody>
  <tr>
   <td>Best Practices zur Qualitätssicherung</td>
   <td><a href="/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance">Best Practices zur Qualitätssicherung</a></td>
   <td>Ein standardisierter Überblick über die Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in Ihrer <em>publish</em>-Umgebung. Dies ist vor allem für QA-Beauftragte, Projektleiter und Systemadministratoren von Interesse.</td>
  </tr>
  <tr>
   <td>Verwenden des Dispatchers mit einem CDN </td>
   <td><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Verwenden des Dispatchers mit einem CDN </a></td>
   <td>Ein CDN (Content Delivery Network) wie Akamai Edge Delivery oder Amazon Cloud Front stellt Inhalte von einem Speicherort in der Nähe des Endbenutzers bereit.</td>
  </tr>
  <tr>
   <td>Leistungsoptimierung</td>
   <td><a href="/help/sites-deploying/configuring-performance.md">Leistungsoptimierung</a></td>
   <td>Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anforderungen durch Besucher zu reagieren.</td>
  </tr>
  <tr>
   <td>Leistungstests</td>
   <td><a href="/help/sites-deploying/best-practices-for-performance-testing.md">Best Practices für Leistungstests</a></td>
   <td>Beschreibt Best Practices für die Durchführung von Leistungstests bei der AEM-Bereitstellung<br />  </td>
  </tr>
 </tbody>
</table>
