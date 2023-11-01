---
title: Repository-Neustrukturierung für alle Lösungen in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um in AEM 6.5 zur neuen Repository-Struktur zu migrieren, die für alle Bereiche von AEM gelten.
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
exl-id: 2d852d9d-9be3-487a-966a-4902bd7df7f9
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '2689'
ht-degree: 63%

---

# Repository-Neustrukturierung für alle Lösungen in AEM 6.5 {#common-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kundinnen und Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen einzuschätzen, die sich auf alle Lösungen auswirken könnten. Einige Änderungen erfordern einen Arbeitsaufwand während des Upgrades auf AEM 6.5, während andere auf eine zukünftige Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [ContextHub-Konfigurationen](#contexthub-6.5)
* [Workflow-Instanzen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-instances)
* [Workflow-Modelle](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-models)
* [Workflow-Starter](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-launchers)
* [Workflow-Skripte](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-scripts)

**Vor einem künftigen Upgrade**

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
* [Übersetzungs-Cloud-Services](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-cloud-services)
* [Übersetzungssprachen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-languages)
* [Übersetzungsregeln](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-rules)
* [Übersetzungs-Widget der Client-Bibliothek](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-widget-client-library)
* [Web-Konsole für Strukturaktivierung](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tree-activation-web-console)
* [Connector-Cloud-Services für Übersetzungsanbieter](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#vendor-translation-connector-cloud-services)
* [E-Mail-Vorlagen für die Workflow-Benachrichtigung](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-notification-email-templates)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### ContextHub-Konfigurationen {#contexthub-6.5}

Ab AEM 6.4 gibt es keine ContextHub-Standardkonfiguration mehr. Daher muss auf der Stammverzeichnisebene der Site `cq:contextHubPathproperty` festgelegt werden, um anzugeben, welche Konfiguration verwendet werden soll.

1. Navigieren Sie zum Stammverzeichnis der Site. 
1. Öffnen Sie die Seiteneigenschaften der Stammseite und wählen Sie die Registerkarte Personalisierung aus. 
1. Geben Sie im Feld ContextHub-Pfad Ihren Pfad zur ContextHub-Konfiguration ein.

Außerdem muss in der ContextHub-Konfiguration in `sling:resourceType` der absolute Pfad in einen relativen Pfad geändert werden.

1. Öffnen Sie die Eigenschaften des ContextHub-Konfigurationsknotens in CRX DE Lite, z. B. `/apps/settings/cloudsettings/legacy/contexthub`
1. Ändern Sie `sling:resourceType` von `/libs/granite/contexthub/cloudsettings/components/baseconfiguration` in `granite/contexthub/cloudsettings/components/baseconfiguration`.

Der `sling:resourceType`-Pfad der ContextHub-Konfiguration muss relativ sein. 

### Workflow-Modelle {#workflow-models}

<table style="table-layout:auto">
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
     <li>Stellen Sie die geänderten Workflow-Modelle in einer lokalen AEM 6.5-Entwicklungsinstanz bereit, sodass sie im vorherigen Speicherort vorhanden sind.</li>
     <li>Bearbeiten Sie das Workflow-Modell mit AEM Workflow-Modell-Editor unter AEM &gt; Tools &gt; Workflow &gt; Modelle.</li>
     <li>Beim Migrieren von modifizierten, AEM bereitgestellten Workflow-Modellen
      <ol>
       <li>Wenn der Workflow-Modell-Editor geöffnet ist, ändern Sie die Adresse des Browsers und ersetzen Sie das Pfadsegment /libs/settings/workflow/models durch /etc/workflow/models.
        <ul>
         <li>Ändern Sie beispielsweise: <em>http://localhost:4502/editor.html<strong>/libs/settings/workflow/models</strong>/dam/update_asset.html</em> in <em>http://localhost:4502/editor.html<strong>/etc/workflow/models</strong>/dam/update_asset.html</em></li>
        </ul> </li>
      </ol> </li>
     <li>Aktivieren Sie den Bearbeitungsmodus im Workflow-Modell-Editor, der die Definition des Workflow-Modells nach /conf/global/workflow/models kopiert.</li>
     <li>Tippen Sie auf die Schaltfläche Synchronisieren , um die Änderungen mit dem Runtime Workflow-Modell unter /var/workflow/models zu synchronisieren.</li>
     <li>Exportieren Sie beide Workflow-Modelle (/conf/global/workflow/models/&lt;workflow-model&gt;) und das Laufzeitarbeitsablaufmodell (/var/workflow/models/&lt;workflow-model&gt;) und in das AEM Projekt integrieren.
      <ol>
       <li>Beispiel: export:
        <ul>
         <li><code>/conf/global/settings/workflow/models/dam/my_workflow_model</code><br /> und </li>
         <li><code>/var/workflow/models/dam/my_workflow_model</code></li>
        </ul> </li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Auflösung des Workflow-Modells geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/models</code></li>
     <li><code>/libs/settings/workflow/models</code></li>
     <li><code>/etc/workflow/models</code></li>
    </ol> <p>Daher müssen alle Anpassungen AEM bereitgestellten Workflow-Modelle, die am vorherigen Speicherort beibehalten werden, nach /conf/global/settings/workflow/models verschoben werden, wenn sie beibehalten werden sollen. Andernfalls werden sie durch die AEM bereitgestellte Workflow-Modelldefinition in /libs/settings/workflow/models ersetzt.</p> </td>
  </tr>
 </tbody>
</table>

### Workflow-Instanzen {#workflow-instances}

<table style="table-layout:auto">
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
   <td><p>Es ist keine Aktion erforderlich, um den neuen Speicherort anzupassen.</p> <p>Historische Workflow-Instanzen können sicher im vorherigen Speicherort verbleiben und neue Workflow-Instanzen werden am neuen Speicherort erstellt.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Alle expliziten Pfadverweise in
    <code>
     custom
    </code>-Code zum vorherigen Speicherort sollten auch den neuen Speicherort berücksichtigen. Es wird empfohlen, diesen Code zu überarbeiten, um die AEM Workflow-APIs zu verwenden.</td>
  </tr>
 </tbody>
</table>

### Workflow-Starter {#workflow-launchers}

<table style="table-layout:auto">
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
   <td><p>Jeder neue oder modifizierte Workflow-Starter muss nach <code>/conf/global/workflow/launcher/config</code> migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder geänderten Workflow-Starter Konfigurationen vom bisherigen Speicherort an den neuen Speicherort (<code>/conf/global</code>).</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Auflösung des Workflow-Starters geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/launcher</code></li>
     <li><code>/libs/settings/workflow/launcher</code></li>
     <li><code>/etc/workflow/launcher</code></li>
    </ol> <p>Daher müssen alle Anpassungen zu von AEM bereitgestellten Workflow-Startern, die am vorherigen Speicherort bestehen bleiben, an den neuen Speicherort (<code>/conf/global/settings/workflow/launcher</code>) verschoben werden, wenn sie beibehalten werden sollen. Andernfalls werden sie durch die von AEM bereitgestellte Definition des Workflow-Starters in <code>/libs/settings/workflow/launcher</code> ersetzt.</p> </td>
  </tr>
 </tbody>
</table>

### Workflow-Skripte {#workflow-scripts}

<table style="table-layout:auto">
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
   <td><p>Alle neuen oder modifizierten Workflow-Skripte müssen an den neuen Speicherort migriert werden und die referenzierenden Workflow-Modelle müssen entsprechend dem neuen Speicherort aktualisiert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Workflow-Skripte vom vorherigen Speicherort an den neuen Speicherort.<br />
      <ul>
       <li><code>/apps/workflow/scripts</code> sollte in SCM gepflegt werden.</li>
      </ul> </li>
     <li>Aktualisieren Sie alle Verweise auf die Workflow-Skripte in den Workflow-Modellen am vorherigen Speicherort, sodass sie auf die neuen Speicherorte verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Nach der Veröffentlichung von AEM 6.4 SP1 ist es möglich, die Restrukturierung bis Version 6.5 zu verschieben 
     <code>
      upgrade
     </code>.</p> <p>Wenn Sie auf AEM 6.4 aktualisieren möchten, bevor AEM 6.4 SP1 veröffentlicht wurde, sollte diese Neustrukturierung als Teil der Aktualisierung ausgeführt werden. Andernfalls wird beim Bearbeiten und Speichern von Workflow-Schritten, die auf Skripte am vorherigen Speicherort verweisen, der Workflow-Skript-Verweis vollständig aus dem Workflow-Schritt entfernt. In der Dropdown-Liste für die Skriptauswahl sind nur Workflow-Skripte an neuen Speicherorten verfügbar.</p> </td>
  </tr>
 </tbody>
</table>

## Vor einem künftigen Upgrade {#prior-to-upgrade}

### ContextHub-Konfigurationen {#contexthub-configurations}

<table style="table-layout:auto">
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
   <td><p>Alle neuen oder modifizierten ContextHub-Konfigurationen müssen an den neuen Speicherort migriert werden und die referenzierenden AEM Sites-Seiten müssen entsprechend dem neuen Speicherort aktualisiert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten ContextHub-Konfigurationen vom vorherigen Speicherort an den neuen Speicherort.</li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM Inhaltshierarchien.
      <ol>
       <li><strong>AEM Sites-Seitenhierarchien über AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Erweiterte Registerkarte &gt; Cloud-Konfiguration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten älteren ContextHub-Konfigurationen von den oben AEM Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Designs für Cloud-Services {#classic-cloud-services-designs}

<table style="table-layout:auto">
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
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft <span class="code">
       <code>
        cq
       </code>:
       <code>
        designPath
       </code></span>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen. Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Dashboard-Designs {#classic-dashboards-designs}

<table style="table-layout:auto">
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
     <li>Kopieren Sie die Designs vom vorherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft
      <code>
       cq
      </code>:
      <code>
       designPath
      </code>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen. Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Klassische Bericht-Designs {#classic-reports-designs}

<table style="table-layout:auto">
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
     <li>Kopieren Sie die Designs vom vorherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft
      <code>
       cq
      </code>:
      <code>
       designPath
      </code>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen. Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Standard-Designs {#default-designs}

<table style="table-layout:auto">
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
     <li>Kopieren Sie die Designs vom vorherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft
      <code>
       cq
      </code>:
      <code>
       designPath
      </code>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen. Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Adobe DTM-JavaScript-Endpunkt {#adobe-dtm-javascript-endpoint}

<table style="table-layout:auto">
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
   <td><p>Keine Aktion erforderlich.</p> <p>Der vorherige öffentliche Speicherort dient als Proxy-Endpunkt für den neuen privaten Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Adobe DTM-Web-Hook-Endpunkt {#adobe-dtm-web-hook-endpoint}

<table style="table-layout:auto">
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
   <td><p>Keine Aktion erforderlich.</p> <p>Der vorherige öffentliche Speicherort dient als Proxy-Endpunkt für den neuen privaten Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Aufgaben des Posteingangs {#inbox-tasks}

<table style="table-layout:auto">
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
   <td><strong>Anmerkungen</strong></td>
   <td><p>Zum Migrieren von Aufgaben an den neuen Speicherort ist keine Aktion erforderlich.</p>
    <ul>
     <li>Aufgaben, die am vorherigen Speicherort vorhanden sind, sind weiterhin verfügbar und funktionieren.</li>
     <li>Neue Aufgaben werden am neuen Speicherort erstellt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Blueprint-Konfigurationen für den Multi-Site-Manager {#multi-site-manager-blueprint-configurations}

<table style="table-layout:auto">
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
     <li>Kopieren Sie benutzerdefinierte Konfigurationen von <code>/etc/blueprints</code> nach <code>/apps/msm</code>.</li>
     <li>Remove <code>/etc/blueprints</code>.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Dashboard-Gadget-Konfigurationen für AEM-Projekte {#aem-projects-dashboard-gadget-configurations}

<table style="table-layout:auto">
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
   <td><p>Alle neuen oder modifizierten Dashboard-Gadget-Konfigurationen für AEM-Projekte müssen an den neuen Speicherort (<code>/apps</code>) migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Dashboard-Gadget-Konfigurationen für AEM-Projekte vom vorherigen an den neuen Speicherort (<code>/apps</code>).
      <ol>
       <li>Kopieren Sie keine unmodifizierten Dashboard-Gadget-Konfigurationen für AEM-Projekte, da diese bereits am neuen Speicherort (<code>/libs</code>) existieren.</li>
      </ol> </li>
     <li>Aktualisieren Sie alle AEM-Projektvorlagen, die auf den vorherigen Speicherort verweisen, sodass sie auf den neuen Speicherort verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Wenn das Kompatibilitätspaket AEM 6.4 angewendet wird, müssen die Aktivitäten zur Repository-Ausrichtung zum Zeitpunkt der Entfernung des Kompatibilitätspakets durchgeführt werden.</td>
  </tr>
 </tbody>
</table>

### E-Mail-Vorlage für die Replikationsbenachrichtigung {#replication-notification-e-mail-template}

<table style="table-layout:auto">
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
   <td><p>Alle neuen oder modifizierten E-Mail-Vorlagen für die Replikationsbenachrichtigung müssen an den neuen Speicherort (<code>/apps</code>) migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten E-Mail-Vorlagen für die Replikationsbenachrichtigung vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten E-Mail-Vorlagen für die Replikationsbenachrichtigung vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die einzigen unterstützten neuen E-Mail-Vorlagen für Replikationsbenachrichtigungen sind die Unterstützung neuer Gebietsschemata.</p> <p>Die Auflösung der E-Mail-Vorlage für Replikationsbenachrichtigungen erfolgt in der folgenden Reihenfolge:</p>
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

<table style="table-layout:auto">
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
   <td><p>Alle Tags müssen nach <code>/content/cq:tags</code> migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle Tags vom vorherigen Speicherort an den neuen Speicherort.</li>
     <li>Entfernen Sie alle Tags vom vorherigen Speicherort.</li>
     <li>Über die AEM-Web-Konsole erfolgt der Neustart des Day Communique 5 Tagging OSGi-Bundles unter <em>https://serveradresse:serverport/system/console/bundles/com.day.cq.cq-tagging</em>, damit AEM erkennt, dass der neue Speicherort Inhalt enthält und verwendet werden sollte.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Wenn Sie das OSGi-Bundle Day Communique Tagging neu starten, wird der neue Speicherort nur als Tag-Stamm registriert, wenn der vorherige Speicherort leer ist.</p> <p>Verweise auf den vorherigen Speicherort funktionieren auch nach der Migration zum neuen Speicherort für alle Funktionen, die die TagManager-API für die Tag-Auflösung nutzen, weiterhin.</p> <p>Jeder benutzerspezifische Code, der explizit auf den Pfad <code>/etc/tags</code> verweist, muss aktualisiert werden auf <span class="code">/content/
      <code>
       cq
      </code>
      <code>
       :tags
      </code></span>, oder vorzugsweise umgeschrieben, um die TagManager Java-API gemeinsam mit dieser Migration zu nutzen.</p> </td>
  </tr>
 </tbody>
</table>

### Übersetzungs-Cloud-Services {#translation-cloud-services}

<table style="table-layout:auto">
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
   <td><p>Alle neuen Cloud-basierten Übersetzungsdienste müssen an den neuen Speicherort (<code>/conf/global</code>,<code>/apps</code> oder <code>/conf/&lt;tenant&gt;</code>) migriert werden.</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen am vorherigen Speicherort zum neuen Speicherort.
      <ul>
       <li>Erstellen Sie manuell neue Konfigurationen für Übersetzungs-Cloud Service über die AEM Authoring-Benutzeroberfläche unter <strong>Tools &gt; Cloud Service &gt; Übersetzungs-Cloud Service</strong>.<br /> ODER </li>
       <li>Kopieren Sie alle neuen Konfigurationen für Cloud-basierte Übersetzungsdienste vom vorherigen Speicherort an den neuen Speicherort (<code>/conf/global</code>,<code>/apps</code> oder <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM Inhaltshierarchien.
      <ol>
       <li>AEM Sites-Seitenhierarchien über <strong>AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Registerkarte "Erweitert"&gt; Cloud-Konfiguration</strong>.</li>
       <li>AEM von Experience Fragment-Hierarchien über <strong>AEM Experience Fragments &gt; Experience Fragment &gt; Eigenschaften &gt; Registerkarte Cloud Service &gt; Cloud-Konfiguration</strong>.</li>
       <li>AEM Ordnerhierarchien von Experience Fragment über <strong>AEM Experience Fragments &gt; Ordner &gt; Eigenschaften &gt; Registerkarte "Cloud Service"&gt; Cloud-Konfiguration</strong>.<br /> </li>
       <li>Ordnerhierarchien von AEM Assets über <strong>AEM Assets &gt; Ordner &gt; Ordnereigenschaften &gt; Cloud-Services &gt; Konfiguration</strong>.</li>
       <li>AEM-Projekte über <strong>AEM-Projekte &gt; Projekt &gt; Projekteigenschaften &gt; Erweitert &gt; Cloud-Konfiguration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten alten Cloud-basierten Übersetzungsdienste von den oben genannten AEM-Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Auflösung der Cloud-basierten Übersetzungsdienste geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/conf/global/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/apps/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/libs/settings/cloudconfigs/translations/translationcfg</code></li>
    </ol> <p>Migrierte Übersetzungs-Cloud Service müssen mit AEM 6.4 kompatibel sein.</p> </td>
  </tr>
 </tbody>
</table>

### Übersetzungssprachen {#translation-languages}

<table style="table-layout:auto">
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
     <li>Falls Ergänzungen oder Modifikationen an den Definitionen für Übersetzungssprachen vorgenommen wurden, sollten Sie alle Definitionen für Übersetzungssprachen vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>) kopieren.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Auflösung des Pfads für Übersetzungssprachen geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/translation/supportedLanguages</code></li>
     <li><code>/apps/settings/translation/supportedLanguage</code></li>
     <li><code>/libs/settings/translation/supportedLanguages</code></li>
    </ol> <p>Diese Auflösung unterstützt keine Zusammenführungsüberlagerung. Das bedeutet, dass der aufgelöste Pfad alle unterstützten Sprachen enthalten muss und unterstützte Sprachen nicht von den Auflösungen mit höherer Reihenfolge übernimmt.</p> </td>
  </tr>
 </tbody>
</table>

### Übersetzungsregeln {#translation-rules}

<table style="table-layout:auto">
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
   <td><p>Eine modifizierte XML-Datei für Übersetzungsregeln muss an den neuen Speicherort (<code>/apps</code> oder <code>/conf/global</code>) migriert werden.</p> <p>1. Kopieren Sie die modifizierte XML-Datei für Übersetzungsregeln vom bisherigen Speicherort an den neuen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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

<table style="table-layout:auto">
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
     <li>Kopieren Sie die Designs vom vorherigen Speicherort an den neuen Speicherort (/apps).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft
      <code>
       cq
      </code>:
      <code>
       designPath
      </code>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet /etc.clientlibs/... zuzulassen. Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden.</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>

### Web-Konsole für Strukturaktivierung {#tree-activation-web-console}

| **Vorheriger Speicherort** | `/etc/replication/treeactivation` |
|---|---|
| **Neuer Speicherort** | `/libs/replication/treeactivation` |
| **Leitfaden für die Neustrukturierung** | Keine Aktion erforderlich. |
| **Anmerkungen** | Die Web-Konsole für die Strukturaktivierung ist jetzt über verfügbar. **Tools > Bereitstellung > Replikation > Tree aktivieren**. |

{style="table-layout:auto"}

### Connector-Cloud-Services für Übersetzungsanbieter {#vendor-translation-connector-cloud-services}

<table style="table-layout:auto">
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
   <td><p>Alle neuen Connector-Cloud-Services für Übersetzungsanbieter müssen an den neuen Speicherort (<code>/conf/global</code>,<code>/apps</code> oder <code>/conf/&lt;tenant&gt;</code>) migriert werden.</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im vorherigen Speicherort zum neuen Speicherort.
      <ul>
       <li>Erstellen Sie manuell die neuen Konfigurationen des Connector-Cloud Service für Übersetzungsanbieter über die <strong>AEM Authoring-Benutzeroberfläche unter Tools &gt; Cloud Service &gt; Übersetzungs-Cloud Service</strong>.<br /> ODER </li>
       <li>Kopieren Sie alle neuen Konfigurationen für Connector-Cloud-Services für Übersetzungsanbieter vom vorherigen Speicherort an den neuen Speicherort (<code>/conf/global </code>, <code>/apps</code> oder <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Verknüpfen Sie die entsprechenden AEM-Konfigurationen mit den AEM Inhaltshierarchien.
      <ol>
       <li>AEM Sites-Seitenhierarchien über <strong>AEM Sites &gt; Seite &gt; Seiteneigenschaften &gt; Registerkarte "Erweitert"&gt; Cloud-Konfiguration</strong>.</li>
       <li>AEM von Experience Fragment-Hierarchien über <strong>AEM Experience Fragments &gt; Experience Fragment &gt; Eigenschaften &gt; Registerkarte Cloud Service &gt; Cloud-Konfiguration</strong>.</li>
       <li>AEM Ordnerhierarchien von Experience Fragment über <strong>AEM Experience Fragments &gt; Ordner &gt; Eigenschaften &gt; Registerkarte "Cloud Service"&gt; Cloud-Konfiguration</strong>.</li>
       <li>Ordnerhierarchien von AEM Assets über <strong>AEM Assets &gt; Ordner &gt; Ordnereigenschaften &gt; Cloud-Services &gt; Konfiguration</strong>.</li>
       <li>AEM-Projekte über <strong>AEM-Projekte &gt; Projekt &gt; Projekteigenschaften &gt; Erweitert &gt; Cloud-Konfiguration</strong>.</li>
      </ol> </li>
     <li>Trennen Sie alle migrierten alten Cloud-basierten Übersetzungsdienste von den oben genannten AEM-Inhaltshierarchien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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

<table style="table-layout:auto">
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
   <td><p>Alle modifizierten E-Mail-Vorlagen für Workflow-Benachrichtigungen müssen an den neuen Speicherort (<code>/conf/global</code>) migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle geänderten E-Mail-Vorlagen für Workflow-Benachrichtigungen vom vorherigen Speicherort an den neuen Speicherort.</li>
     <li>Entfernen Sie migrierte E-Mail-Vorlagen für Workflow-Benachrichtigungen vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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

<table style="table-layout:auto">
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
   <td><p>Vorhandene Workflow-Pakete am vorherigen Speicherort sollten an den neuen Speicherort migriert werden.</p>
    <ol>
     <li>Entfernen Sie alle Workflow-Pakete am vorherigen Speicherort, die nicht durch andere Inhalte referenziert werden und ansonsten nicht erforderlich sind.</li>
     <li>Verschieben Sie alle Workflow-Pakete an den vorherigen Speicherort, die nicht durch andere Inhalte referenziert, aber anderweitig am neuen Speicherort erforderlich sind.</li>
     <li>Belassen Sie alle Workflow-Pakete, die durch andere Inhalte referenziert werden, am vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Workflow-Pakete, die über die Miscadmin Console der klassischen Benutzeroberfläche erstellt wurden, bleiben am vorherigen Speicherort erhalten, während alle anderen am neuen Speicherort beibehalten werden.</p> <p>Workflow-Pakete, die entweder in den vorherigen oder niedrigeren Speicherorten gespeichert sind, können über die Miscadmin Console der klassischen Benutzeroberfläche verwaltet werden.</p> </td>
  </tr>
 </tbody>
</table>
