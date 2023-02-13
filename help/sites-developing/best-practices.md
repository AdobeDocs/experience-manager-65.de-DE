---
title: Best Practices
seo-title: Best Practices
description: Die Entwicklungs- und Beratungs-Teams von Adobe haben einen umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt
seo-description: Adobe Engineering and Consulting teams have developed a comprehensive set of best practices for AEM developers
uuid: f962c31f-8140-482f-b189-16376e23bfed
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 99678c1a-81f3-4fb3-bf73-98f0691c3fb6
exl-id: 0a478e80-c1b2-46c1-a6be-794d78b85d69
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: ht
source-wordcount: '463'
ht-degree: 100%

---

# Best Practices{#best-practices}

## Best Practices für Entwickler – Erste Schritte {#best-practices-for-developers-getting-started}

Die Entwicklungs- und Beratungs-Teams von Adobe haben einen umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt. Sie werden von den Entwicklern von Adobe eingehalten, wenn sie zentrale AEM-Produktaktualisierungen und Code für Kundenimplementierungen entwickeln.

Bevor Sie mit Ihrem AEM-Entwicklungsprojekt beginnen, machen Sie sich zunächst mit diesen Best Practices vertraut:

* [Entwicklungspraktiken](/help/sites-developing/development-practices.md)
* [Inhaltsarchitektur](/help/sites-developing/content-architecture.md)
* [Software-Architektur](/help/sites-developing/software-architecture.md)
* [Tipps zum Programmieren](/help/sites-developing/coding-tips.md)
* [Fallstricke beim Programmieren](/help/sites-developing/code-pitfalls.md)
* [JCR-Interaktion](/help/sites-developing/jcr-integration.md)
* [OSGi-Bundles](/help/sites-developing/osgi-bundles.md)
* [Best Practices für die Java-API](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=de)

### Weitere Informationen zu Best Practices {#additional-best-practices-information}

Für die folgenden Bereiche steht jeweils eine Dokumentation der Best Practices bei der Entwicklung zur Verfügung:

* [Sites](#sites)
* [Communities](/help/sites-developing/best-practices.md#communities)
* [Tools/HTL](/help/sites-developing/best-practices.md#tooling-htl)

Spezielle Dokumente werden in den folgenden Tabellen beschrieben und verknüpft.

Best Practices für die Verwaltung, Bereitstellung und Pflege oder Inhaltserstellung finden Sie unter folgenden Themen:

* [Best Practices für die Verwaltung ](/help/sites-administering/administer-best-practices.md)
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)
* [Best Practices für die Bereitstellung ](/help/sites-deploying/best-practices.md)

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

[AEM Communities](/help/communities/overview.md) vereinfacht die Erstellung und Verwaltung von On-Premise-Communities.

Einige Best Practices für Communities sind hier beschrieben:

|  |  |  |
|---|---|---|
| Best Practices für die Arbeit mit benutzergenerierten Inhalten | [Kodierungsrichtlinien ](/help/communities/code-guide.md) | Richtlinien für die Entwicklung von flexiblem, portablem Code für das [Social Component Framework](/help/communities/scf.md) (SCF). |
| Beispielverwendung von Community-Komponenten | [Handbuch der Community-Komponenten](/help/communities/components-guide.md) | Ein interaktives Entwicklungswerkzeug. |

## Tooling/HTL {#tooling-htl}

HTML Template Language (HTL) ist ein neues HTML-Vorlagensystem, das mit AEM 6.0 eingeführt wurde. Es ersetzt JSP und ESP als bevorzugtes Vorlagensystem von AEM.

|  |  |  |
|---|---|---|
| HTL-Übersicht | [HTL-Überblick und -Syntax](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) | In diesem Dokument wird beschrieben, was HTL ist und wie der Umstieg auf HTL gelingt. Es enthält Beispiele eines Projekts, Syntax, Ausdrücke und Aussagen. |
| Verwenden von APIs in Java | [HTL-Java-Anwendungs-API](https://helpx.adobe.com/de/experience-manager/htl/using/use-api.html) | Mit der HTL-Java-Anwendungs-API kann eine HTL-Datei auf Hilfsmethoden in einer benutzerdefinierten Java-Klasse zugreifen. |

>[!NOTE]
>
>Das mehrteilige Tutorial kann im Hinblick auf Best Practices für die Einrichtung eines neuen AEM-Projekts hilfreich sein. Es bietet umfassende Informationen zu den Kernkomponenten, bearbeitbaren Vorlagen, Client-Bibliotheken und zur Komponentenentwicklung:
>[Erste Schritte mit AEM Sites - WKND-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)
