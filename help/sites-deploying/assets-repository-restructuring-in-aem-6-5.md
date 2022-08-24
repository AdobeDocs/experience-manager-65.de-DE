---
title: Assets-Repository-Neustrukturierung in AEM 6.5
seo-title: Assets Repository Restructuring in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.5 für Assets zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.5 for Assets.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
feature: Upgrading
exl-id: 28ddd23c-5907-4356-af56-ebc7589a2b5d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 52%

---

# Assets-Repository-Neustrukturierung in AEM 6.5 {#assets-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) -Seite verwenden, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM Assets-Lösung auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.5 Arbeitsaufwand, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [Verschiedenes](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc)

**Vor der künftigen Aktualisierung**

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
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

## Vor der künftigen Aktualisierung {#prior-to-upgrade}

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
     <li>Die <code>/libs/settings/dam/notification</code> E-Mail-Vorlage sollte kopiert werden von <strong><code>/etc/notification/email/default</code></strong> nach <strong><code>/apps/settings/notification/email/default</code></strong>
      <ol>
       <li>Da sich das Ziel in<strong> <code>/apps</code></strong> Diese Änderung sollte in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner: <strong><code>/etc/dam/notification/email/default</code></strong> nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen an der E-Mail-Vorlage unter<strong> <code>/etc/notification/email/default</code></strong>, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage unter <strong><code>/libs/settings/notification/email/default</code></strong> als Teil AEM 4-Installation.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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
     <li>Aktualisieren Sie die Dispatcher-Regeln, um die Bereitstellung von Client-Bibliotheken über die <code>/etc.clientlibs/</code> Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die nicht in SCM verwaltet werden und die zur Laufzeit über Design-Dialoge geändert werden, verschieben Sie keine bearbeitbaren Designs aus <code>/etc</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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
     <li>Die aktualisierte E-Mail-Vorlage sollte kopiert werden von <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> nach <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong>
      <ol>
       <li>Da sich das Ziel in<strong> <code>/apps</code></strong> Diese Änderung sollte in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner: <code>/etc/dam/workflow/notification/email/downloadasset </code>nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen an der E-Mail-Vorlage unter<strong> <code>/etc</code></strong>, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage unter <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> als Teil der AEM 6.4 Installation.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>while <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> wird technisch für die Suche unterstützt (hat Vorrang vor /apps über die übliche Sling-CAConfig-Suche, aber danach <code>/etc</code>) die Vorlage in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Dies wird allerdings nicht empfohlen, da es keine Laufzeit-Benutzeroberfläche gibt, die die Bearbeitung der E-Mail-Vorlage erleichtert.</td>
  </tr>
 </tbody>
</table>

### Beispiel-DRM-Lizenzen {#example-drm-licenses}

| **Vorheriger Speicherort** | `/etc/dam/drm/licenses/` |
|---|---|
| **Neuer Speicherort** | `/libs/settings/dam/drm` |
| **Leitfaden für die Neustrukturierung** | Nicht zutreffend |
| **Anmerkungen** | Nicht zutreffend |

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
     <li>Die aktualisierte E-Mail-Vorlage sollte kopiert werden von <strong><code>/etc/dam/adhocassetshare</code></strong> nach <strong><code>/apps/settings/dam/adhocassetshare</code></strong>
      <ol>
       <li>Da sich das Ziel in<strong> <code>/apps</code></strong> Diese Änderung sollte in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner: <strong><code>/etc/dam/adhocassetshare</code></strong> nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen an der E-Mail-Vorlage unter<strong> <code>/etc</code></strong>, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage unter <strong><code>/libs/settings/dam/adhocassetshare</code></strong> als Teil der AEM 6.4 Installation.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>while <code>/conf/global/settings/dam/adhocassetshare</code> wird für die Suche technisch unterstützt (sie hat Vorrang vor <code>/apps</code> über die übliche Sling-CAConfig-Suche, aber danach <code>/etc</code>), kann die Vorlage in <code>/conf/global/settings/dam/adhocassetshare</code>. Dies wird jedoch nicht empfohlen, da es keine Laufzeitbenutzeroberfläche gibt, um die Bearbeitung der E-Mail-Vorlage zu erleichtern</td>
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
     <li>Kopieren Sie alle benutzerdefinierten oder geänderten Skripte aus <strong><code>/etc/dam/indesign/scripts</code></strong> nach <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br />
      <ol>
       <li>Kopieren Sie nur neue oder geänderte Skripte, da von AEM bereitgestellte unveränderte Skripte über verfügbar sind. <strong><code>/libs/settings</code></strong> AEM 6.5</li>
      </ol> </li>
     <li>Suchen Sie alle Workflow-Modelle, die den Medienextraktionsprozess-WF-Schritt verwenden und
      <ol>
       <li>Aktualisieren Sie für jede Instanz des Workflow-Schritts die Pfade in config, damit sie explizit auf die richtigen Skripte unter<strong> <code>/apps/settings/dam/indesign/scripts</code></strong> oder <strong><code>/libs/settings/dam/indesign/scripts</code></strong> gegebenenfalls.</li>
      </ol> </li>
     <li>Entfernen<strong> <code>/etc/dam/indesign/scripts</code></strong> zurück.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Es wird empfohlen, benutzerdefinierte Skripte unter <code>/apps</code>, da dies der Speicherort ist, an dem Code gespeichert werden soll.</td>
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
   <td><p>Anpassungen auf Projektebene müssen geschnitten und unter äquivalent eingefügt werden <code>/apps</code> oder <code>/conf</code> Pfade.</p> <p>So nehmen Sie eine Anpassung an die Repository-Sturktur von AEM 6.4 vor:</p>
    <ol>
     <li>Kopieren Sie alle geänderten Videokonfigurationen aus <code>/etc/dam/video</code> nach <code>/apps/settings/dam/video</code></li>
     <li>Remove <code>/etc/dam/video</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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
     <li>Sie müssen ein Migrationsskript ausführen, um den Knoten von <code>/etc</code> nach <code>/conf</code>. Das Skript befindet sich unter <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>oder Sie können die Konfiguration bearbeiten und sie wird automatisch am neuen Speicherort gespeichert.</li>
    </ul> <p>Beachten Sie, dass Sie ihren copyURL-/embed-Code nicht so anpassen müssen, dass er auf <code>/conf</code>. Die vorhandene Anforderung an <code>/etc</code> wird in den richtigen Inhalt von <code>/conf</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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
   <td><p>Passen Sie alle Verweise an, um auf die neuen Ressourcen unter zu verweisen. <code>/libs</code> mithilfe der <code>/etc.clientlibs/</code> Proxy-Präfix zulassen.</p> <p>Entfernen Sie abschließend die Ordner für die migrierten Client-Bibliotheken aus <code>/etc/clientlibs/foundation/</code></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>
