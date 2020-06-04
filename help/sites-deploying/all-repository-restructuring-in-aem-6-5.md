---
title: Repository-Neustrukturierung für alle Lösungen in AEM 6.5
seo-title: Repository-Neustrukturierung für alle Lösungen in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen zur Migration zur neuen Repository-Struktur in AEM 6.5 vornehmen, die für alle Bereiche von AEM gelten.
seo-description: Erfahren Sie, wie Sie die erforderlichen Änderungen zur Migration zur neuen Repository-Struktur in AEM 6.5 vornehmen, die für alle Bereiche von AEM gelten.
uuid: a4bb64e5-387b-4084-9258-54e68db12f3b
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 80bd707f-c02d-4616-9b45-90f6c726abea
translation-type: tm+mt
source-git-commit: 6396660b642fd78ac7f311fa416efe0e0d52a9e3
workflow-type: tm+mt
source-wordcount: '2721'
ht-degree: 79%

---


# Repository-Neustrukturierung für alle Lösungen in AEM 6.5 {#common-repository-restructuring-in-aem}

As described on the parent [Repository Restructuring in AEM 6.5](/help/sites-deploying/repository-restructuring.md) page, customers upgrading to AEM 6.5 should use this page to assess the work effort associated with repository changes potentially impacting all solutions. Einige Änderungen erfordern Arbeitsaufwand während des Aktualisierungsprozesses von AEM 6.5, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [ContextHub-Konfigurationen](#contexthub-6.5)
* [Workflow-Instanzen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-instances)
* [Workflow-Modelle](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-models)
* [Workflow-Starter](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-launchers)
* [Workflow-Skripte](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-scripts)

**Vor der zukünftigen Aktualisierung**

* [ContextHub-Konfigurationen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#contexthub-configurations)
* [Klassische Designs für Cloud-Services](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-cloud-services-designs)
* [Klassische Dashboard-Designs](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-dashboards-designs)
* [Klassische Bericht-Designs](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-reports-designs)
* [Standard-Designs](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#default-designs)
* [Adobe DTM-JavaScript-Endpunkt](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#adobe-dtm-javascript-endpoint)
* [Adobe DTM-Web-Hook-Endpunkt](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#adobe-dtm-web-hook-endpoint)
* [Aufgaben des Posteingangs](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#inbox-tasks)
* [Blueprint-Konfigurationen für den Multi-Site-Manager](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#multi-site-manager-blueprint-configurations)
* [Dashboard-Gadget-Konfigurationen für AEM-Projekte](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#aem-projects-dashboard-gadget-configurations)
* [E-Mail-Vorlage für die Replikationsbenachrichtigung](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#replication-notification-e-mail-template)
* [Tags](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags)
* [Cloud-basierte Übersetzungsdienste](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-cloud-services)
* [Übersetzungssprachen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-languages)
* [Übersetzungsregeln](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-rules)
* [Übersetzungs-Widget der Client-Bibliothek](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-widget-client-library)
* [Web-Konsole für Strukturaktivierung](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tree-activation-web-console)
* [Connector-Cloud-Services für Übersetzungsanbieter](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#vendor-translation-connector-cloud-services)
* [E-Mail-Vorlagen für die Workflow-Benachrichtigung](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-notification-email-templates)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### ContextHub-Konfigurationen {#contexthub-6.5}

Ab AEM 6.4 gibt es keine ContextHub-Standardkonfiguration mehr. Therefore on the root level of the site a `cq:contextHubPathproperty` should be set to indicate which configuration should be used.

1. Navigieren Sie zum Stammverzeichnis der Site. 
1. Öffnen Sie die Seiteneigenschaften der Stammseite und wählen Sie die Registerkarte Personalisierung aus. 
1. Geben Sie im Feld ContextHub-Pfad Ihren Pfad zur ContextHub-Konfiguration ein.

Additionally on the ContextHub configuration, the `sling:resourceType` needs to be updated to be relative and not absolute.

1. Open the properties of ContextHub configuration node in CRX DE Lite, e.g. `/apps/settings/cloudsettings/legacy/contexthub`
1. Ändern `sling:resourceType` von `/libs/granite/contexthub/cloudsettings/components/baseconfiguration` zu `granite/contexthub/cloudsettings/components/baseconfiguration`

Der `sling:resourceType`-Pfad der ContextHub-Konfiguration muss relativ sein. 

### Workflow-Modelle {#workflow-models}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/models</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code></p> <p><code>/var/workflow/models</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder geänderten Workflow-Modelle müssen nach /conf/global/workflow/models migriert werden.</p>
    <ol>
     <li>Stellen Sie die geänderten Workflow-Modelle in einer lokalen AEM 6.4-Entwicklungsinstanz bereit, sodass sie im vorherigen Speicherort vorhanden sind.</li>
     <li>Bearbeiten Sie das Workflow-Modell unter Verwendung des Editors für AEM Workflow-Modelle unter „AEM &gt; Tools &gt; Workflow &gt; Modelle“.</li>
     <li>Migration von modifizierten, von AEM bereitgestellten Workflow-Modellen
      <ol>
       <li>Öffnen Sie den Editor für Workflow-Modelle, ändern Sie die Browser-URL und ersetzen Sie das Pfadsegment /libs/settings/workflow/models durch /etc/workflow/models.
        <ul>
         <li>For example, change: <em>http://localhost:4502/editor.html<strong>/libs/settings/workflow/models</strong>/dam/update_asset.html</em> to <em>http://localhost:4502/editor.html<strong>/etc/workflow/models</strong>/dam/update_asset.html</em></li>
        </ul> </li>
      </ol> </li>
     <li>Aktivieren Sie den Bearbeitungsmodus im Editor für Workflow-Modelle, wodurch die Definition des Workflow-Modells nach /conf/global/workflow/models kopiert wird.</li>
     <li>Tippen Sie auf die Synchronisierungsschaltfläche, um die Änderungen am Laufzeit-Workflow-Modell unter /var/workflow/models zu synchronisieren.</li>
     <li>Exportieren Sie sowohl das Workflow-Modell (/conf/global/workflow/models/&lt;Workflow-Modell&gt;) als auch das Laufzeit-Workflow-Modell (/var/workflow/models/&lt;Workflow-Modell&gt;) und integrieren Sie beide in das AEM-Projekt.
      <ol>
       <li>Zum Beispiel, exportieren Sie:
        <ul>
         <li><code>/config/settings/workflow/models/dam/my_workflow_model</code> und </li>
         <li><code>/var/workflow/models/dam/my_workflow_model</code></li>
        </ul> </li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung des Workflow-Modells geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/models</code></li>
     <li><code>/libs/settings/workflow/models</code></li>
     <li><code>/etc/workflow/models</code></li>
    </ol> <p>Daher müssen alle Anpassungen zu den von AEM bereitgestellten Workflow-Modellen, die am vorherigen Speicherort bestehen bleiben, nach /conf/global/settings/workflow/models verschoben werden, wenn sie beibehalten werden sollen. Andernfalls werden sie durch die von AEM bereitgestellte Definition des Workflow-Modells in /libs/settings/workflow/models ersetzt.</p> </td>
  </tr>
 </tbody>
</table>

### Workflow-Instanzen {#workflow-instances}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/instances</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/var/workflow/instances</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für die Anpassung an den neuen Speicherort ist keine Aktion erforderlich.</p> <p>Bisherige Workflow-Instanzen können weiterhin am vorherigen Speicherort erhalten bleiben und neue Workflow-Instanzen werden am neuen Speicherort erstellt.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Bei allen expliziten Pfadverweisen im <code>
     custom
    </code> Code auf den vorherigen Speicherort sollte auch der neue Speicherort berücksichtigt werden. Dies ist zu empfehlen, denn dieser Code wurde für die Verwendung in Verbindung mit AEM-Workflow-APIs überarbeitet.</td>
  </tr>
 </tbody>
</table>

### Workflow-Starter {#workflow-launchers}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/launcher/config</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/workflow/launcher/config</code></p> <p><code>/conf/global/settings/workflow/launcher/config</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any new or modified Workflow Launchers must be migrated to <code>/conf/global/workflow/launcher/config</code>.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder geänderten Workflow-Starter Konfigurationen vom bisherigen Speicherort an den neuen Speicherort (<code>/conf/global</code>).</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung des Workflow-Starters geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/launcher</code></li>
     <li><code>/libs/settings/workflow/launcher</code></li>
     <li><code>/etc/workflow/launcher</code></li>
    </ol> <p>Thus, any customizations of AEM-provided Workflow Launcher persisted in the Previous location must be moved to the New Location (<code>/conf/global/settings/workflow/launcher</code> if they are to be retained, otherwise they will be superseded by the AEM-provided Workflow Launcher definition in <code>/libs/settings/workflow/launcher</code>.</p> </td>
  </tr>
 </tbody>
</table>

### Workflow-Skripte {#workflow-scripts}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/scripts</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/workflow/scripts</code></p> <p><code>/apps/workflow/scripts</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder geänderten Workflow-Skripte müssen an den neuen Speicherort migriert werden und referenzierte Workflow-Modelle müssen migriert werden, sodass sie den neuen Speicherort enthalten.</p>
    <ol>
     <li>Kopieren Sie jedes neue oder modifizierte Workflow-Skript vom vorherigen Speicherort zum neuen Speicherort.<br />
      <ul>
       <li><code>/apps/workflow/scripts</code> sollten in SCM beibehalten werden.</li>
      </ul> </li>
     <li>Aktualisieren Sie alle Verweise auf die Workflow-Skripte in den Workflow-Modellen am vorherigen Speicherort, sodass sie auf die neuen Speicherorte verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>AEM 6.4 SP1, when it is released, makes it so this restructuring can be deferred until 6.5
     <code>
      upgrade
     </code>.</p> <p>Wenn Sie auf AEM 6.4 aktualisieren möchten, bevor AEM 6.4 SP1 veröffentlicht wurde, sollte diese Neustrukturierung als Teil der Aktualisierung ausgeführt werden. Ohne das Bearbeiten und Abspeichern von Workflow-Schritten werden die Referenz-Skripte vom vorherigen Speicherort vollständig aus den Workflow-Schritten entfernt und nur die Workflow-Schritte vom neuen Speicherort sind in der Dropdown-Liste „Skriptauswahl“ verfügbar.</p> </td>
  </tr>
 </tbody>
</table>

## Vor der zukünftigen Aktualisierung {#prior-to-upgrade}

### ContextHub-Konfigurationen {#contexthub-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudsettings</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/cloudsettings</code></p> <p><code>/conf/global/settings/cloudsettings</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudsettings</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder modifizierten ContextHub Konfigurationen müssen an den neuen Speicherort migriert werden und die referenzierenden AEM Sites-Seiten müssen so aktualisiert werden, dass sie den neuen Speicherort enthalten.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten ContextHub-Konfigurationen vom vorherigen Speicherort zum neuen Speicherort.</li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM-Inhaltshierarchien.
      <ol>
       <li>Die Seitenhierarchien von AEM Sites über <strong>AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Erweitert &gt; Cloud-Konfiguration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten ContextHub-Konfigurationen von den oben aufgeführten AEM-Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Designs für Cloud-Services {#classic-cloud-services-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/cloudservices</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/cloudservices</code></p> <p><code>/apps/settings/wcm/designs/cloudservices</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Update references to the Previous Location in the <span class="code">
       <code>
        cq
       </code>:
       <code>
        designPath
       </code></span> property.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen .</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Dashboard-Designs {#classic-dashboards-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/dashboards</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/dashboards</code></p> <p><code>/apps/settings/wcm/designs/dashboards</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Update references to the Previous Location in the
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> property.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen .</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Bericht-Designs {#classic-reports-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/reports</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/reports</code></p> <p><code>/apps/settings/wcm/designs/reports</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Update references to the Previous Location in the
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> property.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen .</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Standard-Designs {#default-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/default</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/default</code></p> <p><code>/apps/settings/wcm/designs/default</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Update references to the Previous Location in the
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> property.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen .</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Adobe DTM-JavaScript-Endpunkt {#adobe-dtm-javascript-endpoint}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/clientlibs/dtm</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/var/cq/dtm/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Es ist keine Aktion erforderlich.</p> <p>Der vorherige öffentliche Speicherort fungiert als Proxy-Endpunkt für den privaten neuen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Adobe DTM-Web-Hook-Endpunkt {#adobe-dtm-web-hook-endpoint}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/dtm-hook</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/var/cq/dtm/web-hook</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Es ist keine Aktion erforderlich.</p> <p>Der vorherige öffentliche Speicherort fungiert als Proxy-Endpunkt für den privaten neuen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Aufgaben des Posteingangs {#inbox-tasks}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/taskmanagement</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/var/taskmanagement</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Verwenden Sie die <strong>Wartungsaufgabe zum Bereinigen des Posteingangs</strong>, um alte Aufgaben vom vorherigen Speicherort zu entfernen.</td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Für die Migration von Aufgaben an den neuen Speicherort sind keine Maßnahmen erforderlich.</p>
    <ul>
     <li>Aufgaben, die am vorherigen Speicherort vorhanden sind, sind weiterhin verfügbar und funktionieren.</li>
     <li>Neue Aufgaben werden im neuen Speicherort erstellt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Blueprint-Konfigurationen für den Multi-Site-Manager {#multi-site-manager-blueprint-configurations}

<table>
 <tbody>
  <tr>
   <td><strong><em></em>Vorheriger Speicherort</strong></td>
   <td><code>/etc/blueprints</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/msm</code></p> <p><code>/apps/msm</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>
    <ol>
     <li>Copy custom configurations from <code>/etc/blueprints</code> to <code>/apps/msm</code>.</li>
     <li>Remove <code>/etc/blueprints</code>.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Dashboard-Gadget-Konfigurationen für AEM-Projekte {#aem-projects-dashboard-gadget-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/projects/dashboard/gadgets</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/cq/core/content/projects/dashboard/gadgets</code></p> <p><code>/apps/cq/core/content/projects/dashboard/gadgets</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any new or modified AEM Projects Dashboard Gadget Configurations must be migrated to the new location (<code>/apps</code>).</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Dashboard-Gadget-Konfigurationen für AEM-Projekte vom vorherigen an den neuen Speicherort (<code>/apps</code>).
      <ol>
       <li>Do not copy unmodified AEM Projects Dashboard Gadget Configurations as these now exist in the new location (<code>/libs</code>).</li>
      </ol> </li>
     <li>Aktualisieren Sie alle AEM-Projektvorlagen, die auf den vorherigen Speicherort verweisen, sodass sie auf den neuen Speicherort verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Wenn das AEM 6.4-Kompatibilitätspaket verwendet wird, muss die Anpassung des Repositorys zum Zeitpunkt der Entfernung des Kompatibilitätspaket durchgeführt werden.</td>
  </tr>
 </tbody>
</table>

### E-Mail-Vorlage für die Replikationsbenachrichtigung {#replication-notification-e-mail-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/notification/email/default/com.day.cq.replication</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/notification-templates/com.day.cq.replication</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.replication</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any new or modified Replication Notification E-mail Templates must be migrated to the new location (<code>/apps</code>)</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten E-Mail-Vorlagen für die Replikationsbenachrichtigung vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten E-Mail-Vorlagen für die Replikationsbenachrichtigung vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die einzigen neuen unterstützten E-Mail-Vorlagen für die Replikationsbenachrichtigung sind solche, die neue Lokalisationen unterstützen.</p> <p>Die Auflösung für die E-Mail-Vorlage für die Replikationsbenachrichtigung geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/notification/email/default/com.day.cq.replication</code></li>
     <li><code class="code">/apps/settings/notification-templates/com.day.cq.replication
        </code></li>
     <li><code>/libs/settings/notification-templates/com.day.cq.replication</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Tags {#tags}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/tags</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/content/cq:tags</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>All Tags must be migrated to <code>/content/cq:tags</code>.</p>
    <ol>
     <li>Kopieren Sie alle Tags vom vorherigen Speicherort an den neuen Speicherort.</li>
     <li>Entfernen Sie alle Tags aus dem vorherigen Speicherort.</li>
     <li>Via the AEM Web Console, restart the Day Communique 5 Tagging OSGi bundle at <em>https://serveraddress:serverport/system/console/bundles/com.day.cq.cq-tagging</em> for AEM to recognize the New Location contains content and should be used.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Beim Neustart des Day Communique Tagging OSGi-Bundles wird der neue Speicherort nur als Tag-Stammverzeichnis registriert, wenn der vorherige Speicherort leer ist.</p> <p>Verweise auf den vorherigen Speicherort bleiben nach der Migration an den neuen Speicherort weiterhin für alle Funktionen erhalten, die die TagManager-API von AEM für die Tag-Auflösung unterstützen.</p> <p>Jeder benutzerspezifische Code, der explizit auf den Pfad verweist, <code>/etc/tags</code> muss zusammen mit dieser Migration auf <span class="code">/content/ <code>
       cq
      </code><code>
       :tags
      </code></span>oder vorzugsweise umgeschrieben werden, um die TagManager Java-API zu nutzen.</p> </td>
  </tr>
 </tbody>
</table>

### Cloud-basierte Übersetzungsdienste {#translation-cloud-services}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/translation</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/apps/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/global/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/translationcfg</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any new Translation Cloud Services must be migrated to the new location (<code>/apps</code>, <code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>).</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im bisherigen Speicherort an den neuen Speicherort.
      <ul>
       <li>Erstellen Sie manuell neue Konfigurationen der Cloud-basierten Übersetzungsdienste über die AEM-Benutzeroberfläche unter <strong>Tools &gt; Cloud-Dienste &gt; Übersetzungs-Cloud-Services</strong>.<br /> ODER </li>
       <li>Copy any new Translation Cloud Services configurations from the Previous Location to the New Location (<code>/apps</code>, <code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM-Inhaltshierarchien.
      <ol>
       <li>Die Seitenhierarchien von AEM Sites über <strong>AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Erweitert &gt; Cloud-Konfiguration</strong>.</li>
       <li>Hierarchien von AEM-Experience-Fragments über <strong>AEM-Experience-Fragments &gt; Experience Fragments &gt; Eigenschaften &gt; Cloud-Services &gt; Cloud-Konfiguration</strong>.</li>
       <li>Ordnerhierarchien von AEM-Experience-Fragments über <strong>AEM-Experience-Fragments &gt; Ordner &gt; Eigenschaften &gt; Cloud-Services &gt; Cloud-Konfiguration</strong>.<br /> </li>
       <li>AEM Assets folder hierarchies via <strong>AEM Assets &gt; Folder &gt; Folder Properties &gt; Cloud Services Tab &gt; Configuration</strong>.</li>
       <li>AEM Projects via <strong>AEM Projects &gt; Project &gt; Project Properties &gt; Advanced Tab &gt; Cloud Configuration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten alten Cloud-basierten Übersetzungsdienste von den oben genannten AEM-Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung der Cloud-basierten Übersetzungsdienste geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/conf/global/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/apps/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/libs/settings/cloudconfigs/translations/translationcfg</code></li>
    </ol> <p>Migrierte Cloud-basierte Übersetzungsdienste müssen mit AEM 6.4 kompatibel sein.</p> </td>
  </tr>
 </tbody>
</table>

### Übersetzungssprachen {#translation-languages}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/translation/supportedLanguages</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/translation/supportedLanguages</code></p> <p><code>/apps/settings/translation/supportedLanguages</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder modifizierten Definitionen für Übersetzungssprachen erfordern eine Migration der Definitionen für Übersetzungssprachen an den neuen Speicherort (<code>/apps</code>).</p>
    <ol>
     <li>If any additions or modifications have been made to the Translation Language definitions, then copy all Translation Language definitions from the previous location to the new location (<code>/apps</code>).</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung des Pfads für Übersetzungssprachen geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/translation/supportedLanguages</code></li>
     <li><code>/apps/settings/translation/supportedLanguage</code></li>
     <li><code>/libs/settings/translation/supportedLanguages</code></li>
    </ol> <p>Diese Lösung unterstützt kein Zusammenführen von Überlagerungen, der aufgelöste Pfad muss also alle unterstützten Sprachen enthalten und übernimmt nicht unterstützte Sprachen von übergeordneten Auflösungen.</p> </td>
  </tr>
 </tbody>
</table>

### Übersetzungsregeln {#translation-rules}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/models/translation/translation_rules.xml</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/translation/rules/translation_rules.xml</code></p> <p><code>/apps/settings/translation/rules/translation_rules.xml</code></p> <p><code>/conf/global/settings/translation/rules/translation_rules.xml</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>A modified Translation Rules XML file must be migrated to the new location (<code>/apps</code>, or <code>/conf/global</code>).</p> <p>1. Kopieren Sie die modifizierte XML-Datei für Übersetzungsregeln vom bisherigen Speicherort an den neuen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die XML-Auflösung der Replikation der Übersetzungsregeln geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/global/settings/translation/rules/translation_rules.xml</code></li>
     <li><code class="code">/apps/settings/translation/rules/translation_rules.xml
        </code></li>
     <li><code class="code">/etc/workflow/models/translation/translation_rules.xml
        </code></li>
     <li><code>/libs/settings/translation/rules/translation_rules.xml</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Übersetzungs-Widget der Client-Bibliothek {#translation-widget-client-library}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/translation/translationwidget</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/translation/translationwidget</code></p> <p><code>/apps/settings/wcm/designs/translation/translationwidget</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Update references to the Previous Location in the
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> property.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen .</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Web-Konsole für Strukturaktivierung {#tree-activation-web-console}

| **Vorheriger Speicherort** | `/etc/replication/treeactivation` |
|---|---|
| **Neuer Speicherort** | `/libs/replication/treeactivation` |
| **Leitfaden für die Neustrukturierung** | Es ist keine Aktion erforderlich. |
| **Hinweise** | Die Web-Konsole für die Strukturaktivierung ist jetzt über **Tools > Bereitstellung > Replikation > Tree aktivieren** verfügbar. |

### Connector-Cloud-Services für Übersetzungsanbieter {#vendor-translation-connector-cloud-services}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/&lt;vendor&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/&lt;vendor&gt;</code></p> <p><code class="code">/apps/settings/cloudconfigs/translation/&lt;vendor&gt;
       </code></p> <p><code class="code">/conf/global/settings/cloudconfigs/translation/&lt;vendor&gt;
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/&lt;vendor&gt;</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any new Vendor Translation Connector Cloud Services must be migrated to the new location (<code>/apps</code>, <code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>).</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im bisherigen Speicherort an den neuen Speicherort.
      <ul>
       <li>Erstellen Sie manuell neue Konfigurationen der Connector-Cloud-Services für Übersetzungsanbieter über die AEM-Benutzeroberfläche unter <strong>Tools &gt; Cloud-Dienste &gt; Übersetzungs-Cloud-Services</strong>.<br /> ODER </li>
       <li>Copy any new Vendor Translation Connector Cloud Services configurations from previous location to the new location (<code>/apps</code>, <code>/conf/global </code>or <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM-Inhaltshierarchien.
      <ol>
       <li>Die Seitenhierarchien von AEM Sites über <strong>AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Erweitert &gt; Cloud-Konfiguration</strong>.</li>
       <li>Hierarchien von AEM-Experience-Fragments über <strong>AEM-Experience-Fragments &gt; Experience Fragments &gt; Eigenschaften &gt; Cloud-Services &gt; Cloud-Konfiguration</strong>.</li>
       <li>Ordnerhierarchien von AEM-Experience-Fragments über <strong>AEM-Experience-Fragments &gt; Ordner &gt; Eigenschaften &gt; Cloud-Services &gt; Cloud-Konfiguration</strong>.</li>
       <li>AEM Assets folder hierarchies via <strong>AEM Assets &gt; Folder &gt; Folder Properties &gt; Cloud Services Tab &gt; Configuration</strong>.</li>
       <li>AEM Projects via <strong>AEM Projects &gt; Project &gt; Project Properties &gt; Advanced Tab &gt; Cloud Configuration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten alten Cloud-basierten Übersetzungsdienste von den oben genannten AEM-Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung der Cloud-basierten Übersetzungsdienste geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/conf/global/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/apps/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/libs/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### E-Mail-Vorlagen für die Workflow-Benachrichtigung {#workflow-notification-email-templates}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/notification</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/workflow/notification</code></p> <p><code>/conf/global/settings/workflow/notification</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Any modified Workflow Notification Email Templates must be migrated to the New Location (<code>/conf/global</code>).</p>
    <ol>
     <li>Kopieren Sie alle modifizierten E-Mail-Vorlagen für die Workflow-Benachrichtigung vom bisherigen Speicherort an den neuen Speicherort.</li>
     <li>Entfernen Sie migrierte E-Mail-Vorlagen für die Workflow-Benachrichtigung vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Die Auflösung für die E-Mail-Vorlage für die Workflow-Benachrichtigung geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/workflow/notification</code></li>
     <li><code>/conf/global/settings/workflow/notification</code></li>
     <li><code>/libs/settings/workflow/notification</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Workflow-Pakete {#workflow-packages}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/workflow/packages</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/var/workflow/packages</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Bestehende Workflow-Pakete sollten vom vorherigen Speicherort an den neuen Speicherort migriert werden.</p>
    <ol>
     <li>Entfernen Sie alle Workflow-Pakete vom vorherigen Speicherort, die durch andere Inhalte nicht referenziert werden und auch sonst nicht benötigt werden.</li>
     <li>Verschieben Sie alle Workflow-Pakete an den vorherigen Speicherort, die nicht durch andere Inhalte referenziert werden, aber am neuen Speicherort benötigt werden.</li>
     <li>Belassen Sie alle Workflow-Pakete, auf die andere Inhalte verweisen, am vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td><p>Workflow-Pakete, die über die Miscadmin-Konsole in der klassischen Benutzeroberfläche erstellt wurden, verbleiben am vorherigen Speicherort, während alle anderen am neuen Speicherort gespeichert werden.</p> <p>Die Workflow-Pakete, die entweder am vorherigen oder am neuen Speicherort gespeichert sind, können über die Miscadmin-Konsole in der klassischen Benutzeroberfläche verwaltet werden.</p> </td>
  </tr>
 </tbody>
</table>

