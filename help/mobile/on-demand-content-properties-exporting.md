---
title: Verwenden von Inhaltseigenschaften zum Exportieren von Inhalten
seo-title: Verwenden von Inhaltseigenschaften zum Exportieren von Inhalten
description: Auf der folgenden Seite finden Sie App-Eigenschaften und -Knoten.
seo-description: Auf der folgenden Seite finden Sie App-Eigenschaften und -Knoten.
uuid: 73f1832f-e457-47d0-a0e1-80af90897d31
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a3006835-b1d2-47d6-959a-cdb692e34e1e
exl-id: db1c33c9-8539-436d-b4d0-3d5e6fd688ed
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 10%

---

# Verwenden von Inhaltseigenschaften zum Exportieren von Inhalt{#using-content-properties-to-export-content}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Apps werden in AEM als *cq:Pages* dargestellt.

Sie verwenden dieselben allgemeinen Eigenschaften, die in jedem *cq:Page* vorhanden sind, zusätzlich zu anderen, die unten angezeigt werden und die unterstützende Eigenschaften der Integration darstellen.

## App-Eigenschaften {#app-properties}

Die folgende Tabelle zeigt **App-Eigenschaften und -Knoten**.

<table>
 <tbody>
  <tr>
   <td><strong>PropertyName</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>DPS-Cloud-Konfiguration</td>
   <td>Zeichenfolge:Pfad</td>
   <td><p>Pfad zu einem konfigurierten mobilen On-Demand-Cloud Service. Wird für AEM Mobile- zu Mobile-On-Demand-Aktionen verwendet (API-Aufruf)</p> <p>Diese Zuordnung wird über die Kachel Verbindung verwalten konfiguriert, wenn ein Autor einen On-Demand-Cloud Service für Mobilgeräte auswählt, mit dem die App verknüpft werden soll.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>Zeichenfolge:Pfad</td>
   <td><p>Pfad zu den Exportkonfigurationen der App. Die Exportkonfiguration ist ein Ordner mit zwei untergeordneten ContentSync-Exportkonfigurationsvorlagen.</p> <p><i>dps-article</i>: Exportkonfiguration für ContentSync zum Exportieren von Artikelinhalten</p> <p><i>dps-HTMLResources</i>: Exportkonfiguration für ContentSync zum Exportieren von freigegebenen Ressourcen für Apps/Artikel</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>Zeichenfolge</td>
   <td><p>ID/URI des mobilen On-Demand-Projekts, mit dem diese App verknüpft/verbunden ist.</p> <p>Diese Verknüpfung wird über die Kachel Verbindung verwalten konfiguriert, wenn ein Autor das Projekt aus einer Liste der verfügbaren Projekte für den zugehörigen Mobile On-Demand-Cloud Service auswählt.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>Zeichenfolge</td>
   <td>App-Titel.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>Zeichenfolge</td>
   <td>Inhaltstyp.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>Datum</td>
   <td>Datum des letzten Uploads freigegebener Ressourcen von AEM in AEM Mobile.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploadedBy</td>
   <td>Zeichenfolge: userid</td>
   <td>ID des Benutzers, der die letzte Anforderung freigegebener Ressourcen von AEM auf AEM Mobile hochgeladen hat.</td>
  </tr>
  <tr>
   <td>page-dashboard-config</td>
   <td>Zeichenfolge:Pfad</td>
   <td>Pfad zu einer Dashboard-Konfiguration. Der Pfad kann bei Bedarf zu einer benutzerdefinierten Dashboard-Konfiguration umgeleitet werden.</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>Zeichenfolge:Pfad</td>
   <td><p>Pfad zu einer cq:Component , die <i>mobileapps/core/components/instance ist oder erweitert.</i></p> <p>Dadurch erhalten Sie die Präsenz und das Rendering im Apps-Katalog.</p> </td>
  </tr>
 </tbody>
</table>

Sie können ***Inhaltseigenschaften*** verwenden, um Inhalte zu erstellen. Siehe die folgenden Ressourcen zum Erstellen und Exportieren von Artikeln und freigegebenen Ressourcen:

* [Inhaltseigenschaften](/help/mobile/content-properties.md)
* [Erstellen der Konfiguration von Artikelexporten](/help/mobile/creating-article-export-configuration.md)
* [Erstellen der Exportkonfiguration für freigegebene Ressourcen](/help/mobile/creating-shared-resources-export-configuration.md)
