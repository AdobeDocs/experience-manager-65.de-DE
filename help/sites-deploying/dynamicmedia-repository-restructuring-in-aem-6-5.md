---
title: Dynamic Media-Repository-Umstrukturierung in Adobe Experience Manager 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um in Experience Manager 6.5 für Dynamic Media zur neuen Repository-Struktur zu migrieren.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Aktualisieren
exl-id: 4e736924-74ea-431a-be19-1c4ff022f464
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 33%

---

# Dynamic Media-Repository-Umstrukturierung in Adobe Experience Manager 6.5 {#dynamic-media-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in Adobe Experience Manager 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf Experience Manager 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf Dynamic Media auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von Experience Manager 6.5 Arbeitsaufwand, während andere auf eine zukünftige Aktualisierung verschoben werden können.

**Vor der künftigen Aktualisierung**

* [Benutzerdefinierte Konfigurationen für die adaptive Video-Kodierung](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#custom-adaptive-video-encoding-configurations)
* [Cloud-Konfiguration für Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#dynamic-media-dms-cloud-configuration)
* [Cloud-Service-Konfiguration für Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube-Cloud-Service-Konfiguration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#youtubecloudserviceconfiguration)
* [Verschiedenes](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#misc)

## Vor der künftigen Aktualisierung {#prior-to-upgrade}

### Benutzerdefinierte Konfigurationen für die adaptive Videokodierung  {#custom-adaptive-video-encoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
  </tr>
  <tr>
   <td><strong>Neue Standorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das folgende Migrationsskript ausführen, um zum neuen Speicherort zu migrieren:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der Experience Manager-Benutzeroberfläche bearbeiten und die Änderungen am neuen Speicherort speichern.</p> </td>
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
   <td><strong>Neue Standorte</strong></td>
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann an diesem Speicherort ein Migrationsskript ausführen:<br /> </p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>Starten Sie das Dynamic Media-OSGi-Bundle neu.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Konfiguration des Dynamic Media-Cloud Service (DM Hybrid) {#cloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Neue Standorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das untenstehende Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media - YouTube-Cloud Service-Konfiguration  {#youtubecloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Neue Standorte</strong></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>1. Rückgängigmachen der Veröffentlichung aller Videos von YouTube<br /> 2. Erstellen Sie die YouTube-Konfiguration mithilfe der neuen TouchUI (von <code>/conf</code>), einschließlich des Kopierens aller Kanäle vom alten Speicherort<br /> 3. Veröffentlichen Sie alle Videos neu auf YouTube.</p> <p>Dieser Workflow führt zu neuen YouTube-URLs. Wenn Sie die Veröffentlichung nicht vor der Erstellung einer YouTube-Konfiguration für die TouchUI rückgängig machen, werden unter "Eigenschaften"mehrere YouTube-URLs aufgelistet, da die neu erstellten Kanäle erneut veröffentlicht werden, sofern Sie die Möglichkeit dazu haben. Diese Funktion bedeutet, dass Sie nutzlose URLs haben, die unter Eigenschaften aufgelistet sind.</p> </td>
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
   <td><strong>Neue Standorte</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der Experience Manager-Benutzeroberfläche bearbeiten und die Änderungen am neuen Speicherort speichern.</p> </td>
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
   <td><strong>Neue Standorte</strong></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>
