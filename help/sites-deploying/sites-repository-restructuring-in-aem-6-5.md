---
title: Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um in AEM 6.5 für Sites zur neuen Repository-Struktur zu migrieren.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: b4531792-06dd-4545-9dbb-57224be20dc7
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 70%

---

# Repository-Neustrukturierung in AEM 6.5 {#sites-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollte Kundschaft, die auf AEM 6.5 aktualisiert, diese Seite nutzen, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen abzuschätzen, die sich auf AEM Sites auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Upgrades auf AEM 6.5, während andere auf eine zukünftige Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [ContextHub-Segmente](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#contexthub-segments)

**Vor einem künftigen Upgrade**

* [Adobe Analytics-Client-Bibliotheken](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-analytics-client-libraries)
* [Vom klassischen Microsoft Word zu Web-Seiten-Designs](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#classic-microsoft-word-to-web-page-designs)
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
   <td><p><code>/apps/settings/wcm/segments</code><br /> </p> <p><code>/conf/settings/settings/wcm/segments</code><br /> </p> <p><code>/conf/&lt;tenant&gt;/settings/wcm/segments</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Wenn neue oder geänderte ContextHub-Segmente in der Quell-Code-Verwaltung bearbeitet werden, anstatt in AEM bearbeitet zu werden, müssen sie an den neuen Speicherort migriert werden:</p>
    <ol>
     <li>Kopieren Sie alle neuen oder geänderten ContextHub-Segmente vom vorherigen Speicherort an den neuen Speicherort (/<code>apps</code>, <code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>).</li>
     <li>Aktualisieren Sie die Verweise auf ContextHub-Segmente am vorherigen Speicherort auf die migrierten ContextHub-Segmente an den neuen Speicherorten (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li>
    </ol> <p>Die folgende Abfrage mit QueryBuilder findet alle Verweise auf ContextHub-Segmente in den vorherigen Speicherorten.<br /> <br /> <code class="code">path=/content
       property=cq:segments
       property.operation=like
       property.value=/etc/segmentation/contexthub/%</code><br /> <br /> Dies kann über die <a href="/help/sites-developing/querybuilder-api.md" target="_blank">Benutzeroberfläche von QueryBuilder Debugger AEM</a> geschehen. Beachten Sie, dass es sich um eine traversierende Abfrage handelt, führen Sie sie also nicht gegen die Produktion aus und stellen Sie sicher, dass die Traversalgrenzen bei Bedarf angepasst werden.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>ContextHub-Segmente, die am vorherigen Speicherort erhalten bleiben, werden unter <strong>AEM &gt; Personalisierung &gt; Zielgruppen</strong> als schreibgeschützt angezeigt.</p> <p>Wenn ContextHub-Segmente in AEM bearbeitbar sein sollen, müssen sie an den neuen Speicherort (<code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>) migriert werden. Alle neuen ContentHub-Segmente, die in AEM erstellt werden, bleiben am neuen Speicherort (<code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>) erhalten.</p> <p>Die Seiteneigenschaften von AEM Sites erlauben lediglich die Auswahl des vorherigen Speicherorts (<code>/etc</code>) oder eines einzelnen neuen Speicherorts (<code>/apps</code>, <code>/conf/global</code> oder <code>/conf/&lt;tenant&gt;</code>), daher müssen ContextHub-Segmente entsprechend migriert werden.</p> <p>Nicht verwendete ContextHub-Segmente aus AEM Referenz-Sites können entfernt und nicht an den neuen Speicherort migriert werden:</p>
    <ul>
     <li>/etc/segmentation/geometrixx/</li>
     <li>/etc/segmentation/geometrixx-outdoors</li>
    </ul> <p>Hinweis: Wenn ClientContext verwendet wird, wird empfohlen, in ContextHub zu konvertieren.</p> </td>
  </tr>
 </tbody>
</table>

## Vor einem künftigen Upgrade {#prior-to-upgrade}

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
   <td><p>Jede benutzerdefinierte Verwendung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen:</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek nach Pfad am vorherigen Speicherort sollten aktualisiert werden, um <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzrahmen für AEM Client-Bibliothek</a>.</li>
     <li>Wenn AEM Referenzierungsframework für Client-Bibliotheken nicht verwendet werden kann, kann über AEM Client Library Proxy-Servlet auf den absoluten Pfad der Client-Bibliotheken verwiesen werden.
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

### Vom klassischen Microsoft Word zu Web-Seiten-Designs {#classic-microsoft-word-to-web-page-designs}

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
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort in der Eigenschaft cq:designPath .</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet <code>/etc.clientlibs/</code> zuzulassen.</li>
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

### Konfigurationen für den Emulator von Mobilgeräten {#mobile-device-emulator-configurations}

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
     <li>Aktualisieren Sie für alle AEM Sites-Seiten, die von diesen Konfigurationen für den Mobilgeräte-Emulator abhängen, den Knoten <span class="code">
       <code>
        jcr
       </code>
       <code>
        :content
       </code></span> der Seite: <br /> <span class="code">[cq:Page]/jcr:content@cq:
       <code>
        deviceGroups
       </code> = String[ mobile/groups/responsive ]</span></li>
     <li>Aktualisieren Sie die bearbeitbaren Vorlagen für alle bearbeitbaren Vorlagen, die von diesen Konfigurationen für den Mobilgeräte-Emulator abhängen, indem Sie <span class="code">
       <code>
        cq
       </code>:
       <code>
        deviceGroups
       </code></span> auf den neuen Speicherort verweisen.</li>
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
   <td><p><code>/apps/msm</code> (Kunden-Blueprint-Konfigurationen)</p> <p><code>/libs/msm</code> (Gebrauchsfertige Blueprint-Konfigurationen für Screens, Commerce)</p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen oder geänderten Blueprint-Konfigurationen für den Multi-Site-Manager müssen an den neuen Speicherort (<code>/apps</code>) migriert werden.</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten Blueprint-Konfigurationen für den Multi-Site-Manager vom vorherigen an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten Blueprint-Konfigurationen für den Multi-Site-Manager vom vorherigen Speicherort.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Alle von AEM bereitgestellten Blueprint-Konfigurationen für den Multi-Site-Manager sind am neuen Speicherort unter <code>/libs</code> verfügbar.</p> <p>Der Inhalt verweist nicht auf die blauen Konfigurationen für den Multi-Site-Manager. Daher gibt es keine Inhaltsverweise, die angepasst werden müssen.</p> </td>
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
     <li>Aktualisieren Sie alle Verweise auf AEM-Seiten auf Rollout-Konfigurationen für den Multi-Site-Manager am vorherigen Speicherort, um auf ihre Gegenstücke an den neuen Speicherorten zu verweisen (<code>/libs</code> oder <code>/apps</code>).</li>
    </ol> <p>Entfernen Sie alle migrierten Rollout-Konfigurationen für den Multi-Site-Manager vom vorherigen Speicherort.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Wenn migrierte Rollout-Konfigurationen für den Multi-Site-Manager nicht vom vorherigen Speicherort entfernt werden, werden AEM Autoren doppelte Rollout-Optionen angezeigt.</td>
  </tr>
 </tbody>
</table>

### E-Mail-Vorlage für die Benachrichtigung über Seitenereignisse {#page-event-notification-e-mail-template}

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
   <td><p>Die einzigen unterstützten neuen E-Mail-Vorlagen für Seitenereignis-Benachrichtigungen sind die Unterstützung neuer Gebietsschemata.</p> <p>Die Auflösung der E-Mail-Vorlage für Seitenereignisse erfolgt in der folgenden Reihenfolge:</p>
    <ol>
     <li><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></li>
     <li><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
     <li><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td><p>Alle neuen oder geänderten E-Mail-Vorlagen für die Seitenereignis-Benachrichtigung müssen an den neuen Speicherort unter <code>/apps</code> migriert werden:</p>
    <ol>
     <li>Kopieren Sie alle neuen oder modifizierten E-Mail-Vorlagen für die Seitenereignis-Benachrichtigung vom vorherigen Speicherort an den neuen Speicherort (<code>/apps</code>).</li>
     <li>Entfernen Sie alle migrierten E-Mail-Vorlagen für Seitenereignisbenachrichtigungen vom vorherigen Speicherort.</li>
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
   <td>Strukturvorlagen, die im vorherigen Speicherort erstellt wurden, verwenden das alte Strukturvorlagen-Framework und können nicht in den neuen Speicherort migriert werden. Um eine Anpassung an den neuen Speicherort zu ermöglichen, muss jede ältere Strukturvorlage mithilfe des unterstützten Strukturvorlagen-Frameworks neu entwickelt werden.</td>
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
   <td><p>Alle Verweise auf den vorherigen Speicherort in benutzerdefinierten LESS-Dateien müssen aktualisiert werden, um sie vom neuen Speicherort zu importieren.</p>
    <ul>
     <li>Aktualisieren Sie alle referenzierenden benutzerdefinierten LESS-Dateien, die grid_base.less im vorherigen Speicherort referenzieren, um auf den neuen Speicherort zu verweisen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Verweis auf eine nicht vorhandene <code>grid_base.less</code> Datei führt dazu, dass der Layout-Modus des Seiten- und Vorlageneditors nicht funktioniert und verursacht eine Unterbrechung des Seiten-Layouts.</td>
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
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort in der Eigenschaft <code>cq:designPath</code> über <strong>AEM &gt; Sites &gt; Seiten für benutzerdefinierte Site &gt; Seiteneigenschaften &gt; Erweitert &gt; Design</strong>.</li>
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden (dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes).</li>
     <li>Aktualisieren Sie AEM Dispatcher-Regeln, um die Unterstützung für Client-Bibliotheken über das Proxy-Servlet <code>/etc.clientlibs/</code> zuzulassen.</li>
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
   <td><p>Jede benutzerdefinierte Verwendung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen.</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek nach Pfad am vorherigen Speicherort sollten aktualisiert werden, um <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzrahmen für AEM Client-Bibliothek</a>.</li>
     <li>Wenn AEM Referenzierungsframework für Client-Bibliotheken nicht verwendet werden kann, kann der absolute Pfad der Client-Bibliotheken über AEM Client Library Proxy-Servlet referenziert werden:</li>
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
   <td><p>Die Bearbeitung dieser Client-Bibliotheken wurde zu keinem Zeitpunkt unterstützt.</p> <p>Um die Kategorien der Client-Bibliothek abzurufen, rufen Sie jeden Knoten cq:ClientLIbraryFolder über CRXDELite auf und überprüfen Sie die Eigenschaft "categories":</p>
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
   <td><p>Jede benutzerdefinierte Verwendung dieser Client-Bibliotheken sollte nach Kategorie und nicht nach Pfad auf die Client-Bibliothek verweisen.</p>
    <ol>
     <li>Alle Verweise auf die Client-Bibliothek nach Pfad am vorherigen Speicherort sollten aktualisiert werden, um <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">Referenzrahmen für AEM Client-Bibliothek</a>.</li>
     <li>Wenn AEM Referenzierungsframework für Client-Bibliotheken nicht verwendet werden kann, kann über AEM Client Library Proxy-Servlet auf den absoluten Pfad der Client-Bibliotheken verwiesen werden.</li>
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
