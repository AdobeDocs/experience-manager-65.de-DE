---
title: Best Practices
seo-title: Best Practices
description: Die Entwicklungs- und Beratungsteams von Adobe haben einen umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt
seo-description: Die Entwicklungs- und Beratungsteams von Adobe haben einen umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt
uuid: f962c31f-8140-482f-b189-16376e23bfed
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 99678c1a-81f3-4fb3-bf73-98f0691c3fb6
translation-type: tm+mt
source-git-commit: e562939f1c64d8345b4c2a28e4b882200d9e4c07
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 80%

---


# Best Practices{#best-practices}

## Best Practices für Entwickler – Erste Schritte {#best-practices-for-developers-getting-started}

Die Entwicklungs- und Beratungsteams von Adobe haben einen umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt. Sie werden von den Entwicklern von Adobe eingehalten, wenn sie zentrale AEM-Produktaktualisierungen und Code für Kundenimplementierungen entwickeln.

Bevor Sie mit Ihrem AEM-Entwicklungsprojekt beginnen, machen Sie sich zunächst mit diesen Best Practices vertraut:

* [Entwicklungspraktiken](/help/sites-developing/development-practices.md)
* [Inhaltsarchitektur](/help/sites-developing/content-architecture.md)
* [Software-Architektur](/help/sites-developing/software-architecture.md)
* [Tipps zum Programmieren](/help/sites-developing/coding-tips.md)
* [Fallstricke beim Programmieren](/help/sites-developing/code-pitfalls.md)
* [JCR-Interaktion](/help/sites-developing/jcr-integration.md)
* [OSGi-Bundles](/help/sites-developing/osgi-bundles.md)
* [Best Practices für Java-API](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Weitere Informationen zu Best Practices {#additional-best-practices-information}

Für die folgenden Bereiche steht jeweils eine Dokumentation der Best Practices bei der Entwicklung zur Verfügung:

* [Sites](#sites)
* [Communities](/help/sites-developing/best-practices.md#communities)
* [Tools/HTL](/help/sites-developing/best-practices.md#tooling-htl)

Spezielle Dokumente werden in den folgenden Tabellen beschrieben und verknüpft.

Best Practices für die Verwaltung, Bereitstellung und Pflege oder Inhaltserstellung finden Sie unter folgenden Themen:

* [Best Practices für die Verwaltung](/help/sites-administering/administer-best-practices.md) 
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)
* [Best Practices für die Bereitstellung](/help/sites-deploying/best-practices.md) 

## Sites {#sites}

Zur Verwaltung und Bearbeitung Ihrer Website-Inhalte wurden einige Best Practices wie folgt beschrieben:

<table>
 <tbody>
  <tr>
   <td>Teile der Theorie, die der standardmäßigen Touch-optimierten Benutzeroberfläche zugrunde liegt</td>
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Touch-optimierte Benutzeroberfläche: Konzepte</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Touch-optimierte Benutzeroberfläche: Struktur</a></p> </td>
   <td>Diese Dokumente bieten einen Überblick über die Konzepte und die Struktur der Touch-optimierten Benutzeroberfläche.</td>
  </tr>
  <tr>
   <td>Touch-optimierte Benutzeroberfläche: Anpassen von Konsolen </td>
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">Anpassen der Konsolen der Touch-optimierten Benutzeroberfläche</a></td>
   <td>Dieses Dokument beschreibt die beste Methode, um die Konsolen für die Touch-optimierte Benutzeroberfläche zu erweitern.</td>
  </tr>
  <tr>
   <td>Touch-optimierte Benutzeroberfläche: Anpassen der Seiteninhaltserstellung</td>
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">Anpassen der Seiteninhaltserstellung bei der Touch-optimierten Benutzeroberfläche</a></td>
   <td>Beschreibt, wie Sie die Seiteninhaltserstellung für die Touch-optimierte Benutzeroberfläche erweitern.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td><a href="/help/sites-developing/workflows-best-practices.md">Entwickeln und Erweitern von Workflows</a></td>
   <td><p>Mit Workflows können Sie Adobe Experience Manager (AEM)-Aktivitäten automatisieren und einen größeren Umfang der Verarbeitung repräsentieren, die in einer AEM-Umgebung stattfindet. Daher empfiehlt es sich, die Workflow-Implementierungen sorgfältig zu planen.</p> </td>
  </tr>
 </tbody>
</table>

## Communities {#communities}

[AEM ](/help/communities/overview.md) Community vereinfacht die Gründung und Verwaltung von lokalen Gemeinschaften.

Einige Best Practices für Communities sind hier beschrieben:

|  |  |  |
|---|---|---|
| Best Practices für die Arbeit mit benutzerdefinierten Inhalten (UGC) | [Kodierungsrichtlinien ](/help/communities/code-guide.md) | Richtlinien für die Entwicklung von flexiblem, portablen Code für das [Framework für soziale Komponenten](/help/communities/scf.md) (SCF). |
| Beispielverwendung von Communities-Komponenten | [Handbuch der Community-Komponenten](/help/communities/components-guide.md) | Ein interaktives Entwicklungstool. |

## Tools/HTL {#tooling-htl}

HTML Template Language (HTL) ist ein neues HTML-Vorlagensystem, das mit AEM 6.0 eingeführt wurde. Es ersetzt JSP und ESP als bevorzugtes Vorlagensystem von AEM.

|  |  |  |
|---|---|---|
| HTL-Überblick | [HTL-Überblick und -Syntax](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html) | In diesem Dokument wird beschrieben, was HTL ist und wie der Umstieg auf HTL gelingt. Es enthält Beispiele eines Projekts, Syntax, Ausdrücke und Aussagen. |
| Verwenden von APIs in Java | [HTL-Java-Anwendungs-API](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) | Mit der Java-Anwendungs-API von HTL kann eine HTL-Datei auf Hilfsmethoden in einer benutzerdefinierten Java-Klasse zugreifen. |

>[!NOTE]
>
>Für die Best Practice zum Einrichten eines neuen AEM-Projekts, in dem die Kernkomponenten, bearbeitbare Vorlagen, Client-Bibliotheken und Komponentenentwicklung ausführlich beschrieben werden, könnte es von Interesse sein, ein mehrteiliges Lernprogramm zu folgen:
>[Erste Schritte mit AEM Sites - WKND-Tutorial](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)

