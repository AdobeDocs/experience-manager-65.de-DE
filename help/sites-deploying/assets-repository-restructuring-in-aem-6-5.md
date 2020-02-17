---
title: Assets-Repository-Neustrukturierung in AEM 6.5
seo-title: Assets-Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.5 für Assets zu migrieren.
seo-description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.5 für Assets zu migrieren.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
translation-type: tm+mt
source-git-commit: d20ddba254c965e1b0c0fc84a482b7e89d4df5cb

---


# Assets-Repository-Neustrukturierung in AEM 6.5 {#assets-repository-restructuring-in-aem}

As described on the parent [Repository Restructuring in AEM 6.5](/help/sites-deploying/repository-restructuring.md) page, customers upgrading to AEM 6.5 should use this page to assess the work effort associated with repository changes impacting the AEM Assets Solution. Einige Änderungen erfordern Arbeitsaufwand während des Aktualisierungsprozesses von AEM 6.5, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [Verschiedenes](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc)

**Vor der zukünftigen Aktualisierung**

* [Vorlage für E-Mail-Benachrichtigung für Asset-/Sammlungsereignis](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#asset-collection-event-e-mail-notification-template)
* [Klassische Asset-Freigabe-Designs](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#classic-asset-share-designs)
* [Vorlage für E-Mail-Benachrichtigung zum Asset-Download](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#download-asset-e-mail-notification-template)
* [Beispiel-DRM-Lizenzen](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#example-drm-licenses)
* [Vorlage für E-Mail-Benachrichtigung zu Link-Freigabe](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#link-share-e-mail-notification-template)
* [InDesign-Workflow-Skripts](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#indesign-workflow-scripts)
* [Konfigurationen für die Videotranskodierung](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#video-transcoding-configurations)
* [Verschiedenes](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc2)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### Verschiedenes {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td>/etc/dam/jobs</td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td>/var/dam/jobs</td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn ein benutzerdefinierter Code von diesem Speicherort abhängig ist (d. h. der Code stützt sich explizit auf diesen Pfad), muss der Code aktualisiert werden, um den neuen Speicherort vor dem Aktualisieren zu nutzen. Im Idealfall werden die Java-APIs verwendet, um Abhängigkeiten von einem bestimmten Pfad im JCR zu reduzieren.</p> <p>Temporärer Speicherort, um die ZIP-Datei für das Herunterladen des Clients zu speichern. Eine Aktualisierung ist nicht notwendig, wenn der Client das Herunterladen des Assets anfordert. Am neuen Speicherort wird eine Datei erstellt.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

## Vor der zukünftigen Aktualisierung {#prior-to-upgrade}

### Vorlage für E-Mail-Benachrichtigung für Asset-/Sammlungsereignis {#asset-collection-event-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/notification/email/default</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn die E-Mail-Vorlagen vom Kunden geändert wurden, führen Sie die folgenden Schritte aus, um sie an die neue Repository-Struktur anzupassen:</p>
    <ol>
     <li>Die <code>/libs/settings/dam/notification</code> E-Mail-Vorlage sollte von <strong><code>/etc/notification/email/default</code></strong> in <strong><code>/apps/settings/notification/email/default</code></strong>
      <ol>
       <li>Because the destination is in<strong> <code>/apps</code></strong> this change should be persisted in SCM.</li>
      </ol> </li>
     <li>Remove the folder: <strong><code>/etc/dam/notification/email/default</code></strong> after the e-mail templates within it have been moved.<br />
      <ol>
       <li>If no updates were made to the e-mail template under<strong> <code>/etc/notification/email/default</code></strong>, the folder can be removed as the original e-mail template exists under <strong><code>/libs/settings/notification/email/default</code></strong> as part of AEM 4 install.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Klassische Asset-Freigabe-Designs {#classic-asset-share-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/assetshare</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Entwürfe, die in SCM verwaltet werden und in die nicht während der Laufzeit von Design-Dialogfeldern geschrieben wird, führen Sie die folgenden Schritte aus, um das neueste Modell anzupassen:</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort unter <code>/apps</code>.</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort in der Eigenschaft <code>cq:designPath</code> über <strong>AEM &gt; Sites &gt; Seiten für benutzerdefinierte Site &gt; Seiteneigenschaften &gt; Erweitert &gt; Design</strong>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, um die neue Kategorie „Client-Bibliothek“ zu verwenden. Dies erfordert die Aktualisierung des Implementierungscodes der Seite.</li>
     <li>Update the Dispatcher rules to allow serving of Client Libraries via the <code>/etc.clientlibs/</code> proxy servlet.</li>
    </ol> <p>Für alle Designs, die nicht in SCM verwaltet werden und die zur Laufzeit über Design-Dialoge geändert werden, verschieben Sie keine bearbeitbaren Designs aus <code>/etc</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Vorlage für E-Mail-Benachrichtigung zum Asset-Download {#download-asset-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn die E-Mail-Vorlagen (<strong>downloadasset</strong> oder<strong> transientworkflowcompleted</strong>) geändert wurden, befolgen Sie die nachstehenden Schritte, um sie an die neue Struktur anzupassen:</p>
    <ol>
     <li>The updated e-mail template should be copied from <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> to <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong>
      <ol>
       <li>Because the destination is in<strong> <code>/apps</code></strong> this change should be persisted in SCM.</li>
      </ol> </li>
     <li>Remove the folder: <code>/etc/dam/workflow/notification/email/downloadasset </code>after the e-mail templates within it have been moved.<br />
      <ol>
       <li>If no updates were made to the e-mail template under<strong> <code>/etc</code></strong>, the folder can be removed as the orginal e-mail template exists under <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> as part of AEM 6.4 install.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>While <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> is technically supported for look-up (takes precedence before /apps via usual Sling CAConfig lookup, but after <code>/etc</code>) the template could be placed in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Dies wird allerdings nicht empfohlen, da es keine Laufzeit-Benutzeroberfläche gibt, die die Bearbeitung der E-Mail-Vorlage erleichtert.</td>
  </tr>
 </tbody>
</table>

### Beispiel-DRM-Lizenzen {#example-drm-licenses}

| **Vorheriger Speicherort** | `/etc/dam/drm/licenses/` |
|---|---|
| **Neuer Speicherort** | `/libs/settings/dam/drm` |
| **Leitfaden für die Neustrukturierung** | Nicht zutreffend |
| **Hinweise** | Nicht zutreffend |

### Vorlage für E-Mail-Benachrichtigung zu Link-Freigabe {#link-share-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/adhocassetshare</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn die E-Mail-Vorlage vom Kunden geändert wurde, sollte sie anschließend an die neue Repository-Struktur angepasst werden:</p>
    <ol>
     <li>The updated e-mail template should be copied from <strong><code>/etc/dam/adhocassetshare</code></strong> to <strong><code>/apps/settings/dam/adhocassetshare</code></strong>
      <ol>
       <li>Because the destination is in<strong> <code>/apps</code></strong> this change should be persisted in SCM.</li>
      </ol> </li>
     <li>Remove the folder: <strong><code>/etc/dam/adhocassetshare</code></strong> after the e-mail templates within it have been moved.<br />
      <ol>
       <li>If no updates were made to the e-mail template under<strong> <code>/etc</code></strong>, the folder can be removed as the original e-mail template exists under <strong><code>/libs/settings/dam/adhocassetshare</code></strong> as part of AEM 6.4 install.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>While <code>/conf/global/settings/dam/adhocassetshare</code> is technically supported for look-up (it takes precedence before <code>/apps</code> via usual Sling CAConfig lookup, but after <code>/etc</code>), the template can be placed in <code>/conf/global/settings/dam/adhocassetshare</code>. Dies wird jedoch nicht empfohlen, da es keine Benutzeroberfläche zur Laufzeit gibt, die die Bearbeitung der E-Mail-Vorlage erleichtern könnte</td>
  </tr>
 </tbody>
</table>

### InDesign-Workflow-Skripts {#indesign-workflow-scripts}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/indesign/scripts</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>So nehmen Sie eine Anpassung an eine neue Repository-Sturktur vor:</p>
    <ol>
     <li>Alle benutzerdefinierten oder geänderten Skripten kopieren von <strong><code>/etc/dam/indesign/scripts</code></strong><strong><code>/apps/settings/dam/indesign/scripts</code></strong><br />
      <ol>
       <li>Only copy new or modified scripts as unmodified scripts provided by AEM will be available via <strong><code>/libs/settings</code></strong> in AEM 6.5</li>
      </ol> </li>
     <li>Suchen Sie alle Workflow-Modelle, die den Medienextraktionsprozess-WF-Schritt verwenden und
      <ol>
       <li>For each instance of the Workflow Step, update the paths in config to point explicitly at the proper scripts under<strong> <code>/apps/settings/dam/indesign/scripts</code></strong> or <strong><code>/libs/settings/dam/indesign/scripts</code></strong> as appropriate.</li>
      </ol> </li>
     <li>Entfernen<strong> Sie <code>/etc/dam/indesign/scripts</code></strong> vollständig.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>It is recommended customized scripts be stored under <code>/apps</code>, since that is the location where code should be stored.</td>
  </tr>
 </tbody>
</table>

### Konfigurationen für die Videotranskodierung {#video-transcoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/video</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Project level customizations need to be cut and pasted under equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</p> <p>So nehmen Sie eine Anpassung an die Repository-Sturktur von AEM 6.4 vor:</p>
    <ol>
     <li>Alle geänderten Videokonfigurationen kopieren von <code>/etc/dam/video</code> in <code>/apps/settings/dam/video</code></li>
     <li>Remove <code>/etc/dam/video</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Konfigurationen der Viewer-Voreinstellungen {#viewer-preset-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dam/presets/viewer</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Die Voreinstellungen für die Standardanzeige sind nur am neuen Speicherort verfügbar.</p> <p>Für die benutzerdefinierte Viewer-Vorgabe:</p>
    <ul>
     <li>you will have to run a migration script to move the node from <code>/etc</code> to <code>/conf</code>. The script is located at <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>oder Sie können die Konfiguration bearbeiten und sie wird automatisch am neuen Speicherort gespeichert.</li>
    </ul> <p>Note that you do not have to adjust their copyURL/embed code to point to <code>/conf</code>. The existing request to <code>/etc</code> will be re-routed to the correct content from <code>/conf</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Verschiedenes {#misc2}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/dam/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Adjust any references to point to the new resources under <code>/libs</code> using the <code>/etc.clientlibs/</code> allow proxy prefix.</p> <p>Bereinigen Sie schließlich die Ordner für die migrierten clientlibs aus <code>/etc/clientlibs/foundation/</code></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

