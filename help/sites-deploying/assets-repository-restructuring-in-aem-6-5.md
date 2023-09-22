---
title: Assets-Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in Adobe Experience Manager (AEM) 6.5 für Assets zu migrieren.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 28ddd23c-5907-4356-af56-ebc7589a2b5d
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 49%

---

# Assets-Repository-Neustrukturierung in AEM 6.5 {#assets-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) -Seite verwenden, sollten Kunden, die auf Adobe Experience Manager (AEM) 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM Assets-Lösung auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Upgrades auf AEM 6.5, während andere auf eine zukünftige Aktualisierung verschoben werden können.

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
   <td><p>Wenn ein benutzerdefinierter Code von diesem Speicherort abhängt (d. h., der Code verlässt sich explizit auf diesen Pfad), muss der Code aktualisiert werden, um den neuen Speicherort vor der Aktualisierung zu verwenden. Idealerweise werden Java™-APIs verwendet, wenn verfügbar, um Abhängigkeiten von einem bestimmten Pfad im JCR zu reduzieren.</p> <p>Temporärer Speicherort für eine ZIP-Datei, die der Client herunterladen kann. Eine Aktualisierung ist nicht notwendig, wenn der Client das Herunterladen des Assets anfordert. Es wird eine Datei am neuen Speicherort generiert.</p> </td>
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
     <li>Die E-Mail-Vorlage <code>/libs/settings/dam/notification</code> sollte von <strong><code>/etc/notification/email/default</code></strong> nach <strong><code>/apps/settings/notification/email/default</code></strong> kopiert werden.
      <ol>
       <li>Da sich das Ziel in<strong> <code>/apps</code></strong>, sollte diese Änderung in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner <strong><code>/etc/dam/notification/email/default</code></strong>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc/notification/email/default</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 4-Installation unter <strong><code>/libs/settings/notification/email/default</code></strong> vorhanden ist.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Klassische Designs zur Asset-Freigabe {#classic-asset-share-designs}

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
   <td><p>Führen Sie für alle Designs, die in SCM verwaltet werden und zur Laufzeit nicht über Design-Dialogfelder in geschrieben werden, die folgenden Aktionen aus, um sie an das aktuelle Modell anzupassen:</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort unter <code>/apps</code>.</li>
     <li>Konvertieren Sie alle CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code>.</li>
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort im <code>cq:designPath</code> -Eigenschaft über <strong>AEM &gt; DAM-Admin &gt; Asset-Freigabe-Seite &gt; Seiteneigenschaften &gt; Erweiterte Registerkarte &gt; Designfeld</strong>.</li>
     <li>Um die neue Kategorie Client-Bibliothek zu verwenden, aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen. Dazu muss der Seiten-Implementierungscode aktualisiert werden.</li>
     <li>Aktualisieren Sie die Dispatcher-Regeln, damit Sie die Bereitstellung von Client-Bibliotheken über die Variable <code>/etc.clientlibs/</code> Proxy-Servlet.</li>
    </ol> <p>Verschieben Sie bei Designs, die nicht in SCM verwaltet werden und die zur Laufzeit über Design-Dialogfelder geändert werden, keine bearbeitbaren Designs aus <code>/etc</code>.</p> </td>
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
   <td><p>Wenn die E-Mail-Vorlagen (<strong>downloadasset</strong> oder <strong>transientworkflowcompleted</strong>) wurden geändert und befolgen Sie dann das folgende Verfahren, um sich an die neue Struktur anzupassen:</p>
    <ol>
     <li>Die aktualisierte E-Mail-Vorlage sollte aus <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> nach <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong> kopiert werden
      <ol>
       <li>Da sich das Ziel in<strong> <code>/apps</code></strong>, sollte diese Änderung in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner <code>/etc/dam/workflow/notification/email/downloadasset </code>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 6,4-Installation unter <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> vorhanden ist.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>while <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> wird technisch für die Suche unterstützt (hat Vorrang vor /apps über die übliche Sling-CAConfig-Suche, aber danach <code>/etc</code>) die Vorlage platziert werden kann in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Dies wird jedoch nicht empfohlen, da es keine Laufzeitbenutzeroberfläche gibt, um die Bearbeitung der E-Mail-Vorlage zu erleichtern.</td>
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
     <li>Die aktualisierte E-Mail-Vorlage sollte aus <strong><code>/etc/dam/adhocassetshare</code></strong> nach <strong><code>/apps/settings/dam/adhocassetshare</code></strong> kopiert werden
      <ol>
       <li>Da sich das Ziel in<strong><code>/apps</code></strong>, sollte diese Änderung in SCM beibehalten werden.</li>
      </ol> </li>
     <li>Entfernen Sie den Ordner <strong><code>/etc/dam/adhocassetshare</code></strong>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br />
      <ol>
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 6,4-Installation unter <strong><code>/libs/settings/dam/adhocassetshare</code></strong> vorhanden ist.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>while <code>/conf/global/settings/dam/adhocassetshare</code> wird für die Suche technisch unterstützt (sie hat Vorrang vor <code>/apps</code> über die übliche Sling-CAConfig-Suche, aber nach <code>/etc</code>), kann die Vorlage in <code>/conf/global/settings/dam/adhocassetshare</code>. Dies wird allerdings nicht empfohlen, da es keine Laufzeit-Benutzeroberfläche für die Bearbeitung der E-Mail-Vorlage gibt.</td>
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
   <td><p>So nehmen Sie eine Anpassung an eine neue Repository-Struktur vor:</p>
    <ol>
     <li>Kopieren Sie alle benutzerdefinierten oder geänderten Skripte aus <strong><code>/etc/dam/indesign/scripts</code></strong> nach <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br />.
      <ol>
       <li>Nur neue oder geänderte Skripte kopieren, da von AEM bereitgestellte nicht geänderte Skripte über verfügbar sind <strong><code>/libs/settings</code></strong> AEM 6.5</li>
      </ol> </li>
     <li>Suchen Sie alle Workflow-Modelle, die den Medienextraktionsprozess-WF-Schritt verwenden.
      <ol>
       <li>Aktualisieren Sie für jede Instanz des Workflow-Schrittes die Pfade in config, sodass sie auf die entsprechenden Skripte unter <strong> <code>/apps/settings/dam/indesign/scripts</code></strong> oder <strong><code>/libs/settings/dam/indesign/scripts</code></strong> verweisen.</li>
      </ol> </li>
     <li>Entfernen Sie <strong> <code>/etc/dam/indesign/scripts</code></strong> vollständig.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Es ist empfehlenswert, benutzerdefinierte Skripte unter <code>/apps</code> zu speichern, dem vorgesehenen Speicherort für Code.</td>
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
   <td><p>Anpassungen auf Projektebene müssen ausgeschnitten und unter äquivalentem eingefügt werden <code>/apps</code> oder <code>/conf</code> Pfade.</p> <p>So nehmen Sie eine Anpassung an die Repository-Struktur von AEM 6.4 vor:</p>
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

### Konfigurationen von Viewer-Vorgaben {#viewer-preset-configurations}

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
   <td><p>Für die vordefinierte Viewer-Vorgabe ist sie nur am neuen Speicherort verfügbar.</p> <p>Für die benutzerdefinierte Viewer-Vorgabe:</p>
    <ul>
     <li>Führen Sie ein Migrationsskript aus, damit Sie den Knoten von <code>/etc</code> nach <code>/conf</code>. Das Skript befindet sich unter <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>oder Sie können die Konfiguration bearbeiten und sie werden automatisch am neuen Speicherort gespeichert.</li>
    </ul> <p>Sie müssen ihren copyURL/embed-Code nicht so anpassen, dass er auf <code>/conf</code>. Die vorhandene Anforderung an <code>/etc</code> auf den richtigen Inhalt von umgeleitet wird <code>/conf</code>.</p> </td>
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
   <td><p>Passen Sie alle Verweise so an, dass sie auf die neuen Ressourcen unter <code>/libs</code> verweisen, indem Sie das Präfix <code>/etc.clientlibs/</code> zum Zulassen als Proxy-Präfix verwenden.</p> <p>Entfernen Sie abschließend die Ordner für die migrierten Client-Bibliotheken aus dem Verzeichnis <code>/etc/clientlibs/foundation/</code></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>
