---
title: Umstrukturierung des Dynamic-Media-Repositorys in Adobe Experience Manager 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in Experience Manager 6.5 für Dynamic Media zu migrieren.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 4e736924-74ea-431a-be19-1c4ff022f464
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 835ee49e-9248-5578-a60a-15c097807178
    internal-label: Upgrading
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 98%
---
# Umstrukturierung des Dynamic-Media-Repositorys in Adobe Experience Manager 6.5 {#dynamic-media-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Umstrukturierung des Dynamic-Media-Repositorys in Adobe Experience Manager 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf Experience Manager 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen einzuschätzen, die sich auf Dynamic Media auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Upgrades auf Experience Manager 6.5, während andere auf eine zukünftige Aktualisierung verschoben werden können.

**Vor einer zukünftigen Aktualisierung**

* [Benutzerdefinierte Konfigurationen für die adaptive Video-Kodierung](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#custom-adaptive-video-encoding-configurations)
* [Cloud-Konfiguration für Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#dynamic-media-dms-cloud-configuration)
* [Cloud-Service-Konfiguration für Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#cloudserviceconfiguration)
* [Dynamic Media – YouTube-Cloud-Service-Konfiguration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#youtubecloudserviceconfiguration)
* [Verschiedenes](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#misc)

## Vor einer zukünftigen Aktualisierung {#prior-to-upgrade}

### Benutzerdefinierte Konfigurationen für die adaptive Video-Kodierung  {#custom-adaptive-video-encoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das folgende Migrationsskript ausführen, um zum neuen Speicherort zu migrieren:</p> <p><em>https://Server-Adresse:Serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der Experience Manager-Benutzeroberfläche bearbeiten und die Änderungen werden am neuen Speicherort gespeichert.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Cloud-Konfiguration für Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann an diesem Speicherort ein Migrationsskript ausführen:<br /> </p>
    <ul>
     <li><em>https://Server-Adresse:Serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>Starten Sie das Dynamic Media-OSGi-Paket neu.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Cloud-Service-Konfiguration für Dynamic Media (DM Hybrid) {#cloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das untenstehende Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt:</p> <p><em>https://Server-Adresse:Serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media – YouTube-Cloud-Service-Konfiguration  {#youtubecloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>1. Veröffentlichung aller Videos in YouTube <br /> 2. Erstellen Sie die YouTube-Konfiguration mit der neuen Touch-optimierten Benutzeroberfläche (von <code>/conf</code>) und kopieren Sie alle Kanäle vom alten Speicherort.<br /> 3. Veröffentlichen Sie alle Videos erneut auf YouTube.</p> <p>Dieser Workflow resultiert in neuen YouTube-URLs. Wenn Sie die Veröffentlichung nicht vor der Erstellung einer YouTube-Konfiguration mit der Touch-optimierten Benutzeroberfläche aufheben, werden unter „Eigenschaften“ mehrere YouTube-URLs aufgelistet, da die neu erstellten Kanäle erneut veröffentlicht werden, sobald sich die Gelegenheit ergibt. Das bedeutet, dass unter „Eigenschaften“ unbrauchbare URLs aufgelistet sind.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Verschiedenes {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/imageserver/macros</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://Server-Adresse:Serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der Experience Manager-Benutzeroberfläche bearbeiten und die Änderungen werden am neuen Speicherort gespeichert.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/presets/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://Server-Adresse:Serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>
