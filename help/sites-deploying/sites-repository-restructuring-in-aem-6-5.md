---
title: Repository-Neustrukturierung in AEM 6.5
seo-title: Sites Repository Restructuring in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um die neue Repository-Struktur in AEM 6.5 für Sites zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.5 for Sites.
uuid: 6dc5f8bd-1680-40af-9b8f-26c1f4bc3304
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 3eccb2d5-c325-43a6-9c03-5f93f7e30712
feature: Upgrading
exl-id: b4531792-06dd-4545-9dbb-57224be20dc7
source-git-commit: 58594be73372e128ba999a8290615fbcb447084e
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 74%

---

# Repository-Neustrukturierung in AEM 6.5 {#sites-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) -Seite verwenden, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM Sites-Lösung auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.5 Arbeitsaufwand, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [ContextHub-Segmente](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#contexthub-segments)

**Vor der künftigen Aktualisierung**

* [Adobe Analytics-Client-Bibliotheken](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-analytics-client-libraries)
* [Vom klassischen Microsoft Word zu Webseiten-Designs](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#classic-microsoft-word-to-web-page-designs)
* [Konfigurationen für den Mobilgeräte-Emulator](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#mobile-device-emulator-configurations)
* [Blueprint-Konfigurationen für den Multi-Site-Manager](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#multi-site-manager-blueprint-configurations)
* [Rollout-Konfigurationen für den Multi-Site-Manager](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#multi-site-manager-rollout-configurations)
* [E-Mail-Vorlage für Seitenereignis-Benachrichtigung](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#page-event-notification-e-mail-template)
* [Seiten-Strukturvorlage](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#page-scaffolding)
* [Responsives Raster (LESS)](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#responsive-grid-less)
* [Designs für statische Vorlagen](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#static-template-designs)

<!-- Search&Promote is end-of-life September 1, 2022 * [Adobe Search and Promote Integration Client Libraries](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-search-and-promote-integration-client-libraries) -->
* [Client-Bibliotheken für die Integration mit Adobe Target](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-target-integration-client-libraries)
* [WCM Foundation-Client-Bibliotheken](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#wcm-foundation-client-libraries)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### ContextHub-Segmente {#contexthub-segments}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/segmentation/contexthub</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/apps/settings/wcm/segments</code> </p> <p><code>/conf/settings/settings/wcm/segments</code> </p> <p><code>/conf/&lt;tenant&gt;/settings/wcm/segments</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn alle neuen oder modifizierten ContextHub-Segmente für die Bearbeitung in der Versionsverwaltung und nicht in AEM vorgesehen sind, müssen Sie an den neuen Speicherort migriert werden:</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten ContextHub-Segmente vom vorherigen Speicherort an den entsprechenden neuen Speicherort (/<code>apps</code>, <code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>)</li>
     <li>Aktualisieren Sie Verweise auf ContextHub-Segmente am vorherigen Speicherort auf die migrierten ContextHub-Segmente an den neuen Speicherorten (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li>
    </ol> <p>Die folgende Abfrage mit QueryBuilder findet alle Verweise auf ContextHub-Segmente in den vorherigen Speicherorten.<br /> <br /> <code class="code">path=/content
       property=cq:segments
       property.operation=like
       property.value=/etc/segmentation/contexthub/%</code><br /> <br /> Dies kann über <a href="/help/sites-developing/querybuilder-api.md" target="_blank">Benutzeroberfläche von QueryBuilder Debugger AEM</a>. Beachten Sie, dass es sich hierbei um eine durchgehende Abfrage handelt. Führen Sie sie daher nicht gegen die Produktion aus und stellen Sie sicher, dass die Traversal-Beschränkungen nach Bedarf angepasst werden.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>ContextHub-Segmente, die am vorherigen Speicherort erhalten bleiben, werden unter <strong>AEM &gt; Personalisierung &gt; Zielgruppen</strong> als schreibgeschützt angezeigt.</p> <p>Wenn ContextHub-Segmente in AEM bearbeitbar sein sollen, müssen sie an den neuen Speicherort (<code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>). Alle neuen Segmente von ContentHub, die in AEM erstellt wurden, bleiben am neuen Speicherort (<code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>).</p> <p>Die Seiteneigenschaften von AEM Sites erlauben nur den vorherigen Speicherort (<code>/etc</code>) oder einem einzelnen neuen Speicherort (<code>/apps</code>, <code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>) ausgewählt werden, sodass ContextHub-Segmente entsprechend migriert werden müssen.</p> <p>Alle ungenutzten ContextHub-Segmente von AEM-Referenz-Sites können entfernt werden und müssen und nicht an den neuen Speicherort migriert werden:</p>
    <ul>
     <li>/etc/segmentation/geometrixx/</li>
     <li>/etc/segmentation/geometrixx-outdoors</li>
    </ul> <p>Hinweis: Wenn ClientContext verwendet wird, wird empfohlen, in ContextHub zu konvertieren.</p> </td>
  </tr>
 </tbody>
</table>

## Vor der künftigen Aktualisierung {#prior-to-upgrade}

### Adobe Analytics-Client-Bibliotheken {#adobe-analytics-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/clientlibs/foundation/sitecatalyst</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Jede benutzerdefinierte Nutzung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen:</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek anhand des Pfads im vorherigen Speicherort sollten entsprechend dem <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzierungssystem für Client-Bibliotheken von AEM</a> aktualisiert werden.</li>
     <li>Wenn das Referenzierungssystem für Client-Bibliotheken von AEM nicht verwendet werden kann, kann der absolute Pfad der Client-Bibliotheken über das Proxy-Servlet für Client-Bibliotheken von AEM referenziert werden.
      <ul>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/appmeasurement.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/plugins.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/tracking.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/util.js</code></li>
      </ul> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Bearbeitung dieser Client-Bibliotheken wurde zu keinem Zeitpunkt unterstützt.</p> <p>Um die Kategorien der Client-Bibliothek zu erhalten, rufen Sie jeden Knoten <code>cq:ClientLIbraryFolder</code> über CRXDELite auf und prüfen Sie die Kategorie-Eigenschaft.</p>
    <ul>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/appmeasurement</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/plugins</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/tracking</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/util</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Vom klassischen Microsoft Word zu Webseiten-Designs {#classic-microsoft-word-to-web-page-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/wordDesign</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/wordDesign</code></p> <p><code>/apps/settings/wcm/designs/wordDesign</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie Verweise auf den vorherigen Speicherort in der Eigenschaft cq:designPath.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren AEM Dispatcher-Regeln, um die Bereitstellung von Client-Bibliotheken über die <code>/etc.clientlibs/</code> Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden:</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen für den Mobilgeräte-Emulator {#mobile-device-emulator-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/mobile</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/mobile</code></p> <p><code>/apps/settings/mobile</code></p> <p><code>/conf/global/settings/mobile</code></p> <p><code>/conf/&lt;tenant&gt;/settings/mobile</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Alle neuen Konfigurationen für den Mobilgeräte-Emulator müssen an den neuen Speicherort migriert werden.
    <ol>
     <li>Kopieren Sie alle neuen Konfigurationen für den Mobilgeräte-Emulator vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li>
     <li>Aktualisieren Sie für alle AEM Sites-Seiten, die von diesen Konfigurationen für den Mobilgeräte-Emulator abhängen, die Seite <span class="code">
       <code>
        jcr
       </code>
       <code>
        :content
       </code></span> node: <br /> <span class="code">[cq:Page]/jcr:content@cq:
       <code>
        deviceGroups
       </code> = String[ mobile/groups/responsive ]</span></li>
     <li>Aktualisieren Sie für alle bearbeitbaren Vorlagen, die von diesen Konfigurationen für den Mobilgeräte-Emulator abhängen, die bearbeitbaren Vorlagen, indem Sie auf die <span class="code">
       <code>
        cq
       </code>:
       <code>
        deviceGroups
       </code></span> zum neuen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Auflösung der Konfigurationen für den Mobilgeräte-Emulator geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/mobile</code></li>
     <li><code>/conf/global/settings/mobile</code></li>
     <li><code>/apps/settings/mobile</code></li>
     <li><code>/libs/settings/mobile</code></li>
     <li><code>/etc/mobile</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Blueprint-Konfigurationen für den Multi-Site-Manager {#multi-site-manager-blueprint-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/blueprints</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/apps/msm</code> (Kunden-Blueprint-Konfigurationen)</p> <p><code>/libs/msm</code> (Standardmäßige Blueprint-Konfigurationen für Screens, Commerce)</p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder modifizierten Blueprint-Konfigurationen für den Multi-Site-Manager müssen an den neuen Speicherort (<code>/apps</code>).</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Blueprint-Konfigurationen für den Multi-Site-Manager vom vorherigen an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten Blueprint-Konfigurationen für den Multi-Site-Manager vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Alle AEM bereitgestellten Blueprint-Konfigurationen für den Multi-Site-Manager sind am neuen Speicherort unter <code>/libs</code>.</p> <p>Inhalt verweist nicht auf die Blueprint-Konfigurationen für den Multi-Site-Manager, daher müssen keine Inhaltsverweise angepasst werden.</p> </td>
  </tr>
 </tbody>
</table>

### Rollout-Konfigurationen für den Multi-Site-Manager {#multi-site-manager-rollout-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/msm/rolloutConfigs</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/msm/wcm/rolloutconfigs</code></p> <p><code>/apps/msm/wcm/rolloutconfigs</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder modifizierten Rollout-Konfigurationen für den Multi-Site-Manager müssen an den neuen Speicherort migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Rollout-Konfigurationen für den Multi-Site-Manager vom vorherigen an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Aktualisieren Sie alle Verweise auf AEM Seiten auf Rollout-Konfigurationen für den Multi-Site-Manager am vorherigen Speicherort, um auf ihre Gegenstücke an den neuen Speicherorten zu verweisen (<code>/libs</code> oder <code>/apps</code>).</li>
    </ol> <p>Entfernen Sie alle migrierten Rollout-Konfigurationen für den Multi-Site-Manager vom vorherigen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Wenn migrierte Rollout-Konfigurationen für den Multi-Site-Manager nicht aus dem vorherigen Speicherort entfernt werden, werden den AEM-Autoren doppelte Rollout-Optionen angezeigt.</td>
  </tr>
 </tbody>
</table>

### E-Mail-Vorlage für Seitenereignis-Benachrichtigung {#page-event-notification-e-mail-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Die einzigen neuen unterstützten E-Mail-Vorlagen für die Seitenereignis-Benachrichtigung sind solche, die neue Lokalisationen unterstützen.</p> <p>Die Auflösung für die E-Mail-Vorlage für die Seitenereignis-Benachrichtigung geschieht in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></li>
     <li><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
     <li><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Alle neuen oder modifizierten E-Mail-Vorlagen für Seitenereignis-Benachrichtigungen müssen an den neuen Speicherort unter migriert werden <code>/apps</code>:</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten E-Mail-Vorlagen für die Seitenereignis-Benachrichtigung vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten E-Mail-Vorlagen für die Seitenereignis-Benachrichtigung vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Seiten-Strukturvorlage {#page-scaffolding}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/scaffolding</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><span class="code">/libs/settings/
      <code>
       wcm
      </code>/template-types/scaffolding/scaffolding</span></p> <p><span class="code">/apps/settings/
      <code>
       wcm
      </code>/template-types/scaffolding/scaffolding</span></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Stukturvorlagen, die im vorherigen Speicherort erstellt wurden, verwenden das alte Strukturvorlagen-Framework und können nicht in den neuen Speicherort migriert werden. Zur Anpassung an den neuen Speicherort muss jede alte Strukturvorlage mithilfe des unterstützen Strukturvorlagen-Frameworks neu entwickelt werden.</td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Responsives Raster (LESS) {#responsive-grid-less}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle Verweise auf den vorherigen Speicherort in benutzerdefinierten LESS-Dateien müssen aktualisiert werden, damit ein Import vom neuen Speicherort erfolgt.</p>
    <ul>
     <li>Aktualisieren Sie alle referenzierenden benutzerdefinierten LESS-Dateien, die auf grid_base.less im vorherigen Speicherort verweisen, sodass sie auf den neuen Speicherort zu verweisen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Verweis auf eine nicht vorhandene <code>grid_base.less</code> Datei führt dazu, dass der Layoutmodus des Seiten- und Vorlageneditors nicht funktioniert und verursacht eine Unterbrechung des Seitenlayouts.</td>
  </tr>
 </tbody>
</table>

### Designs für statische Vorlagen {#static-template-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/&lt;custom-site&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/apps/settings/wcm/designs/&lt;custom-site&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Für alle Designs, die in SCM verwaltet werden und in die nicht zur Laufzeit über Design-Dialogfelder geschrieben wird.</p>
    <ol>
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li>
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort in der Eigenschaft <code>cq:designPath</code> über <strong>AEM &gt;  Sites &gt; Seiten für benutzerdefinierte Site &gt; Seiteneigenschaften &gt; Erweitert &gt; Design</strong>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungscodes).</li>
     <li>Aktualisieren AEM Dispatcher-Regeln, um die Bereitstellung von Client-Bibliotheken über die <code>/etc.clientlibs/</code> Proxy-Servlet.</li>
    </ol> <p>Für alle Designs, die NICHT in SCM verwaltet werden und die über Design-Dialogfelder zur Laufzeit angepasst werden:</p>
    <ul>
     <li>Entfernen Sie keine bearbeitbaren Designs aus <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Der empfohlene Ansatz besteht darin, AEM Sites und -Seiten mit bearbeitbaren Vorlagen zu erstellen, die Strukturinhalte und Richtlinien anstelle von Designs verwenden.</td>
  </tr>
 </tbody>
</table>

<!-- Search&Promote is end of life as of September 1, 2022 ### Adobe Search and Promote Integration Client Libraries {#adobe-search-and-promote-integration-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Previous location</strong></td>
   <td><p><code>/etc/clientlibs/foundation/searchpromote</code></p> </td>
  </tr>
  <tr>
   <td><strong>New location(s)</strong></td>
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td>
  </tr>
  <tr>
   <td><strong>Restructuring guidance</strong></td>
   <td><p>Any custom use of these Client Libraries should reference the Client Library by category, and not by path.</p>
    <ol>
     <li>Any references to the Client Library by path at the Previous Location should be updated to use <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM's Client Library referencing framework</a>.</li>
     <li>If AEM's Client Library referencing framework cannot be used, the absolute path of the Client Libraries can be referenced via AEM's Client Library Proxy servlet:</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/cq/searchpromote/clientlibs/searchpromotei.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Notes</strong></td>
   <td><p>Editing of these Client Libraries was never supported.</p> <p>To obtain the Client Library categories, visit each cq:ClientLIbraryFolder node via CRXDELite and inspect the categories property:</p>
    <ul>
     <li><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table> -->

### Client-Bibliotheken für die Integration mit Adobe Target {#adobe-target-integration-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/clientlibs/foundation/target</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/cq/testandtarget/clientlibs/testandtarget</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Jede benutzerdefinierte Nutzung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen:</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek anhand des Pfads im vorherigen Speicherort sollten entsprechend dem <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzierungssystem für Client-Bibliotheken von AEM</a> aktualisiert werden.</li>
     <li>Wenn das Referenzierungssystem für Client-Bibliotheken von AEM nicht verwendet werden kann, kann der absolute Pfad der Client-Bibliotheken über das Proxy-Servlet für Client-Bibliotheken von AEM referenziert werden.</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/testandtarget.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs-integration.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/init.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/mbox.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/parameters.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/util.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Bearbeitung dieser Client-Bibliotheken wurde zu keinem Zeitpunkt unterstützt.</p> <p>Um die Kategorien der Client-Bibliothek zu erhalten, rufen Sie jeden Knoten cq:ClientLIbraryFolder über CRXDELite auf und prüfen Sie die Kategorie-Eigenschaft.</p>
    <ul>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/testandtarget</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs-integration</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/init</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/mbox</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/parameters</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/util</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### WCM Foundation-Client-Bibliotheken {#wcm-foundation-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/clientlibs/wcm/foundation</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/wcm/foundation/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Jede benutzerdefinierte Nutzung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen:</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek anhand des Pfads im vorherigen Speicherort sollten entsprechend dem <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzierungssystem für Client-Bibliotheken von AEM</a> aktualisiert werden.</li>
     <li>Wenn das Referenzierungssystem für Client-Bibliotheken von AEM nicht verwendet werden kann, kann der absolute Pfad der Client-Bibliotheken über das Proxy-Servlet für Client-Bibliotheken von AEM referenziert werden.</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/accessibility.css</code></li>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.css</code></li>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Die Bearbeitung dieser Client-Bibliotheken wurde zu keinem Zeitpunkt unterstützt.</p> <p>Um die Kategorien der Client-Bibliothek zu erhalten, rufen Sie jeden Knoten <code>cq:ClientLIbraryFolder</code> über CRXDELite auf und prüfen Sie die Kategorie-Eigenschaft.</p>
    <ul>
     <li><code>/libs/wcm/foundation/clientlibs/accessibility</code></li>
     <li><code>/libs/wcm/foundation/clientlibs/main</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>
