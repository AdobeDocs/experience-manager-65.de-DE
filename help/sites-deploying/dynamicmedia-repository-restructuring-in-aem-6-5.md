---
title: Umstrukturierung des dynamischen Medienspeichers in AEM 6.5
seo-title: Umstrukturierung des dynamischen Medienspeichers in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.5 für Dynamic Media zu migrieren.
seo-description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.5 für Dynamic Media zu migrieren.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
translation-type: tm+mt
source-git-commit: d20ddba254c965e1b0c0fc84a482b7e89d4df5cb

---


# Dynamic Media repository restructuring in AEM 6.5 {#dynamic-media-repository-restructuring-in-aem}

As described on the parent [Repository Restructuring in AEM 6.5](/help/sites-deploying/repository-restructuring.md) page, customers upgrading to AEM 6.5 should use this page to assess the work effort associated with repository changes impacting the Dynamic Media Solution. Einige Änderungen erfordern Arbeitsaufwand während des Aktualisierungsprozesses von AEM 6.5, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Vor der zukünftigen Aktualisierung**

* [Benutzerdefinierte Konfigurationen für die adaptive Video-Kodierung](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#custom-adaptive-video-encoding-configurations)
* [Cloud-Konfiguration für Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#dynamic-media-dms-cloud-configuration)
* [Cloud-Service-Konfiguration für Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube-Cloud-Service-Konfiguration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#youtubecloudserviceconfiguration)
* [Verschiedenes](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#misc)

## Vor der zukünftigen Aktualisierung {#prior-to-upgrade}

### Custom Adaptive Video encoding configurations  {#custom-adaptive-video-encoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das folgende Migrationsskript ausführen, um zum neuen Speicherort zu migrieren:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der AEM-Benutzeroberfläche bearbeiten, und die Änderungen werden am neuen Speicherort gespeichert.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media (DMS7) Cloud configuration {#dynamic-media-dms-cloud-configuration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
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
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Dynamic Media (DM Hybrid) Cloud Service configuration {#cloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können das untenstehende Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media - YouTube Cloud Service configuration  {#youtubecloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>1. Rückgängigmachen der Veröffentlichung aller Videos von YouTube<br /> 2. Create the YouTube Configuration using the new TouchUI (from <code>/conf</code>) including copying all the Channels from the old location<br /> 3. Veröffentlichen Sie alle Videos neu auf YouTube.</p> <p>Dieser Workflow führt zu neuen YouTube-URLs. Wenn Sie die Veröffentlichung nicht vor der Erstellung einer neuen YouTube-Konfiguration mit der Touch-optimierten Benutzeroberfläche aufheben, werden unter „Eigenschaften“ mehrere YouTube-URLs aufgelistet, da die neu erstellten Kanäle bei Gelegenheit erneut veröffentlicht werden. Dies bedeutet, dass Sie unbrauchbar gewordene URLs haben, die unter „Eigenschaften“ aufgelistet sind.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
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
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der AEM-Benutzeroberfläche bearbeiten, und die Änderungen werden am neuen Speicherort gespeichert.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
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
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

