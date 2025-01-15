---
title: Exportieren von Inhalten mit Inhaltseigenschaften
description: Auf der folgenden Seite werden die Eigenschaften und Knoten der Mobile App angezeigt.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: db1c33c9-8539-436d-b4d0-3d5e6fd688ed
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 3%

---

# Exportieren von Inhalten mit Inhaltseigenschaften{#using-content-properties-to-export-content}

{{ue-over-mobile}}

Apps werden in AEM als *cq:Pages* dargestellt.

Sie verwenden dieselben gemeinsamen Eigenschaften wie in jeder *cq:Page* zusätzlich zu anderen, die unten gezeigt werden und Eigenschaften darstellen, die die Integration unterstützen.

## App-Eigenschaften {#app-properties}

Die folgende Tabelle zeigt &quot;**und Knoten**.

<table>
 <tbody>
  <tr>
   <td><strong>PropertyName</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>DPS-Cloud-Konfiguration</td>
   <td>string:path</td>
   <td><p>Pfad zu einem konfigurierten Mobile-On-Demand-Cloud Service. Wird für AEM Mobile-zu-Mobile-On-Demand-Aktionen (API-Aufruf) verwendet</p> <p>Diese Zuordnung wird über die Kachel Verbindung verwalten konfiguriert, wenn ein Autor einen Mobile-On-Demand-Cloud Service auswählt, mit dem die App verknüpft werden soll.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>string:path</td>
   <td><p>Pfad zu den Exportkonfigurationen der App. Die Exportkonfiguration ist ein Ordner mit zwei untergeordneten ContentSync-Exportkonfigurationsvorlagen.</p> <p><i>dps-article</i>: ContentSync-Exportkonfiguration zum Exportieren des Artikelinhalts</p> <p><i>dps-HTMLResources</i>: ContentSync-Exportkonfiguration zum Exportieren der vom Programm/Artikel freigegebenen Ressourcen</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>Zeichenfolge</td>
   <td><p>ID/URI des mobilen On-Demand-Projekts, mit dem diese App verknüpft/gebunden ist.</p> <p>Diese Zuordnung wird über die Kachel Verbindung verwalten konfiguriert, wenn ein Autor das Projekt aus einer Liste der verfügbaren Projekte für den zugehörigen Mobile On-Demand-Cloud Service auswählt.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>Zeichenfolge</td>
   <td>App-Titel.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>Zeichenfolge</td>
   <td>Content-Typ.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>Datum</td>
   <td>Datum des letzten Uploads freigegebener Ressourcen von AEM in AEM Mobile.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploadedBy</td>
   <td>string:userId</td>
   <td>ID des Benutzers, der den letzten Upload der Anforderung freigegebener Ressourcen von AEM an AEM Mobile durchgeführt hat.</td>
  </tr>
  <tr>
   <td>page-dashboard-config</td>
   <td>string:path</td>
   <td>Pfad zu einer Dashboard-Konfiguration. Der Pfad kann bei Bedarf zu einer benutzerdefinierten Dashboard-Konfiguration umgeleitet werden.</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>string:path</td>
   <td><p>Pfad zu einer cq:Component, die (mobileApps/core/components/instance<i> erweitert oder aktualisiert wird</i></p> <p>Dadurch wird das Vorhandensein und Rendering im Anwendungskatalog bereitgestellt.</p> </td>
  </tr>
 </tbody>
</table>

Sie können ***Inhaltseigenschaften*** verwenden, um Inhalte zu erstellen. In den folgenden Ressourcen finden Sie Informationen zum Erstellen und Exportieren von Artikeln und freigegebenen Ressourcen:

* [Inhaltseigenschaften](/help/mobile/content-properties.md)
* [Erstellen der Konfiguration für den Artikelexport](/help/mobile/creating-article-export-configuration.md)
* [Erstellen der Exportkonfiguration für freigegebene Ressourcen](/help/mobile/creating-shared-resources-export-configuration.md)
