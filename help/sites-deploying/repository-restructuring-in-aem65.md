---
title: Repository-Neustrukturierung in AEM 6.5
seo-title: Repository-Neustrukturierung in AEM 6.5
description: Informationen zur Repository-Umstrukturierung in AEM 6.5
seo-description: Informationen zur Repository-Umstrukturierung in AEM 6.5
uuid: bc577c82-3279-4ddd-898c-607864868db0
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 274a7f5a-d509-4ca9-9ae5-30e48f34f171
docset: aem65
redirecttarget: /content/help/en/experience-manager/6-5/help/sites-deploying/repository-restructuring.html
translation-type: tm+mt
source-git-commit: bd0dc09ea230416ad3544d14440b7b74b80ec406

---


# Repository-Neustrukturierung in AEM 6.5 {#repository-restructuring-in-aem}

## Einführung {#introduction}

Vor AEM 6.5 wurde Kundencode in unvorhersehbaren Bereichen der JCR bereitgestellt, die bei Aktualisierungen geändert werden mussten. Aus diesem Grund wurde es bei offiziellen AEM-Versionen (Hauptversionen, Feature Packs, Service Packs oder Hotfixes) üblich, benutzerdefinierten Code, Konfigurationen oder Inhalt zu überschreiben. Darüber hinaus kam es vor, dass durch Kunden vorgenommene Änderungen den AEM-Produktcode oder AEM-Inhalte überschrieben und die Produktfunktion beeinträchtigt haben.

Solche Konflikte konnten nicht immer automatisch aufgelöst werden, das Kennzeichnen verbrauchte sehr viel Verarbeitungszeit und es musste manuell eingegriffen werden, wobei die Lösung nicht immer eindeutig war. Durch klare Abgrenzungshierarchien für AEM-Produktcode und Kundencode können diese Konflikte vermieden werden.

To that end, beginning in AEM 6.5 and to be continued in future releases, content is being restructured out of `/etc` to other folders in the repository, along with guidelines on what content goes  where,  adhering to the following high-level rules:

* AEM product code will always be placed in `/libs`, which must not be overwritten by custom code
* Custom  code should be placed in `/apps`, `/content`, and `/conf`

This article is organized into three sections, representing the type of content that has been moved out of `/etc`:

1. Konfiguration
1. Client-seitige Bibliotheken
1. Sonstiges

Jeder Abschnitt enthält:

* Eine Tabelle mit den neu strukturierten Speicherorten und zusätzlichem Kontext. Die Tabellen werden in naher Zukunft umformatiert, um die Lesbarkeit zu verbessern.
* an extensibility strategy allowing custom code to successfully extend AEM application code residing under `/libs`.

## Abwärtskompatibilität {#backwards-compatibility}

In den meisten Fällen wird die Abwärtskompatibilität zu den alten Standorten nach der Aktualisierung auf AEM 6.5 beibehalten. Dies wird erreicht, indem die alten Standorte durch Produktcode beibehalten und respektiert werden, zusätzlich zu den neuen Standorten, die hinzugefügt werden. In den meisten Fällen wird bedingte Logik verwendet, um zu überprüfen, ob der Legacy-Ordner vorhanden ist, und um Inhalte von dort anstelle des neuen Speicherorts zu lesen.

Kunden wird empfohlen, die alten Speicherorte nach der Aktualisierung auf 6.5 zu entfernen, damit die neuen Speicherorte verwendet werden. Kunden können den Zeitpunkt dieser Änderung nach eigenem Ermessen planen. Die unten stehenden Tabellen enthalten Anweisungen zur Einhaltung der neuen Inhaltsstruktur nach Ort.

>[!NOTE]
>
>Eine aktualisierte Instanz wird neben den neuen Speicherorten auch alte Inhaltsspeicherorte einbeziehen. Bei einer Neuinstallation werden nur die neuen Speicherorte berücksichtigt.

## Anleitung für die Tabellen {#how-to-read-the-tables}

Die Tabellen in den einzelnen Abschnitten enthalten:

* Die AEM-Lösung (Sites, Assets, Forms usw.), für die der Inhalt relevant ist.
* Den alten Speicherort (6.4 und früher).
* Den neuen Speicherort ab 6.5.
* Anleitungen für die Umstellung auf die neue Inhaltsstruktur. So kann es z. B. in den Wochen oder Monaten nach der Aktualisierung auf 6.5 notwendig sein, ein Skript auszuführen oder Dateien manuell zu verschieben.
* Den von AEM verwendeten Ansatz für die Erhaltung der Abwärtskompatibilität mit alten Inhaltsspeicherorten für Kunden, die eine Aktualisierung von einer früheren Version auf AEM 6.5 durchführen.

## Konfiguration{#configuration}

The content locations in this section generally refer to content that resides under a `/settings` folder under `/libs`, `/apps`, or `/conf`.

### Erweiterbarkeitsstrategie {#extensibility-strategy}

In general, but with a few exceptions, content under this section can be extended using Apache Sling&#39;s [   Context Aware   Configuration](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) feature.

Die Context Aware-Konfiguration ermöglicht es, Inhalte in einem Teil des Repositorys mehrmals durch Inhalte in anderen Teilen des Repositorys zu überlagern. Beispielsweise `/libs` können Inhalte in durch Inhalte in überlagert werden, `/apps`die dann durch Inhalte in überlagert werden können `/conf`. Moreover, content in a global folder under `/conf` can be overlayed by a specific &quot;tenant&quot; or &quot;site&quot; (e.g. `/conf/we-retail/settings`).

In der Regel wird die kontextabhängige Konfiguration als Strategie zum Erweitern von Funktionskonfigurationen verwendet, es gibt jedoch Fälle, in denen sie von anderen Inhaltstypen verwendet wird.

Die folgende Tabelle enthält eine zusätzliche Spalte mit dem Namen &quot;Konfigurationstyp&quot;, um zu erklären, in welchem Umfang eine Konfiguration überlagert werden kann. Hier finden Sie weitere Details zu diesen Konfigurationstypen:

**Nicht kontextsensitiv**

* Resources happen to be in context-aware folder structures (like `/libs/settings`) but always referenced via absolute path so context awareness is not in effect.
* Ressourcen können sich überall befinden. For example, Assets DRM Licenses could be at `/content/my-customer/licenses/creative-commons.html`
* Beispiele:

   * Workflow scripts -> `/apps/settings/workflow/scripts/noop.ecma`
   * Assets DRM-Lizenzen -> `/apps/settings/dam/drm/my-license`

**Nur global** 

* Funktion mit ausschließlich globaler Konfiguration
* As a reference point, take the precedence of settings in this example: `/libs/settings` &lt; `/apps/settings` &lt; `/conf/global`

* AEM unterstützt nur eine globale Konfiguration, keine Konfigurationen mit Mandanten.
* AEM beginnt immer mit der Suche nach Konfigurationen auf der Ebene /conf/global

* Beispiele:

   * Workflow-Starter -> `/libs/settings/workflow/launcher`
   * Workflow-Modelle -> `/conf/global/settings/workflow/models`

**Mandantenabhängig**

* For tenant-aware configurations, see this example for the precedence of configuration paths: `/libs/settings` &lt; `/apps/settings` &lt; `/conf/global` &lt; `/conf/we-retail`, where we-retail is the tenant name. Mandantenabhängige Konfigurationen unterstützen außerdem untergeordnete Mandanten. 

* AEM unterstützt mandantenabhängige Konfigurationen. It respects `cq:conf` property on hierarchy
* Beispiele:

   * Bearbeitbare Vorlagen -> `/conf/we-retail/settings/wcm/templates`
   * Cloud-Konfigurationen -> `/conf/we-retail/settings/cloudsettings`

<table>
 <tbody>
  <tr>
   <td><strong>Lösung</strong></td>
   <td><strong>Vorherige Position</strong><br /> </td>
   <td><strong>Neuer Speicherort </strong></td>
   <td><strong>Kontextsensitiver Konfigurationstyp</strong><br /> </td>
   <td><strong>Abwärtskompatibilitätsansatz </strong></td>
   <td><strong>Anforderungen für die Ausrichtung am aktuellsten Modell </strong></td>
  </tr>
  <tr>
   <td>AEM Sites/AEM Forms</td>
   <td><p><code>/etc/cloudservices/typekit</code></p> <p><code>/etc/cloudservices/recaptcha</code></p> <p><code>/etc/cloudservices/echosign</code></p> </td>
   <td><p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/typekit</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/recaptcha</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/echosign</code></p> </td>
   <td>Mandantenabhängig</td>
   <td><p>Alte Cloudservices.</p> <p>Bei einer Aktualisierung erhalten geblieben. Code zum Auflisten und Lesen ist in AEM weiterhin als Fallback vorhanden.</p> </td>
   <td>Das Dienstprogramm für die Lazy-Content-Migration kann über die Migrationsbenutzeroberfläche von Forms ausgelöst werden, um eine automatische Umwandlung in den neuen Pfad durchzuführen.<br />  </td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/cloudservices/fdm</code></td>
   <td><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/fdm</code></td>
   <td>Mandantenabhängig</td>
   <td><p>Alte Cloudservices.</p> <p>In einem aktualisierten Setup erhalten geblieben. Code zum Auflisten und Lesen ist in AEM weiterhin als Fallback vorhanden.</p> </td>
   <td>Das Dienstprogramm für die Lazy-Content-Migration kann über die Migrationsbenutzeroberfläche von Forms ausgelöst werden, um eine automatische Umwandlung in den neuen Pfad durchzuführen.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/adhocassetshare</code></td>
   <td><code>/libs/settings/dam/adhocassetshare</code></td>
   <td>Mandantenabhängig</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td>Project level customizations need to be cut and pasted into the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td>
   <td><code>/libs/settings/dam/workflow</code></td>
   <td>Mandantenabhängig</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td>Project level customizations need to be cut and pasted into the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/drm/licenses/</code></td>
   <td><code>/libs/settings/dam/drm</code></td>
   <td>Nicht kontextsensitiv</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td>Project level customizations need to be cut and pasted into the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/indesign/scripts</code></td>
   <td><code>/libs/settings/dam/indesign</code></td>
   <td>Mandantenabhängig</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td><p>Project level customizations need to be cut and pasted under the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</p> <p>Beim Ausführen eines Workflows mit Asset-Verarbeitung können weiterhin Verweise auf den alten Speicherort in /etc in der Media Extraction Process-Konfiguration vorhanden sein. Neben dem Verschieben der Skripte aus /etc in die entsprechenden Pfade unter /apps und /conf müssen angepasste Media Extraction Process-Argumente angepasst werden, indem absolute in relative Pfade geändert werden.</p> <p>Weitere Informationen finden Sie auf <a href="https://helpx.adobe.com/experience-manager/6-2/help/assets/indesign.html">dieser Seite</a>.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/video</code></td>
   <td><code>/libs/settings/dam/video</code></td>
   <td>Mandantenabhängig</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td>Project level customizations need to be cut and pasted into the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/notification/email/default</code></td>
   <td><code>/libs/settings/dam/notification</code></td>
   <td>Mandantenabhängig</td>
   <td>Veraltete Inhaltsstrukturen erhalten eine höhere Priorität als neue OOTB-Strukturen.</td>
   <td>Project level customizations need to be cut and pasted into the equivalent <code>/apps</code> or <code>/conf</code> paths as applicable.</td>
  </tr>
  <tr>
   <td>AEM Sites/AEM Assets</td>
   <td><code>/etc/designs</code> </td>
   <td><code>/libs/settings/wcm/designs</code></td>
   <td>Nicht kontextsensitiv</td>
   <td><p>Verarbeitende Dienste berücksichtigen den alten Speicherort.</p> <p>Konfigurationen vom alten Speicherort werden berücksichtigt.</p> </td>
   <td><br /> Move custom content from <code>/etc/design</code> to <code>/apps/settings/wcm/design</code> for alignment with the new repository structure. In Zukunft können Sie Ihre Sites dahingehend aktualisieren, dass diese bearbeitbare Vorlagen verwenden, die den Designmodus und somit diesen Inhalt überflüssig machen.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/scaffolding</code></td>
   <td><p><code>/libs/settings/wcm/template-types/scaffolding/scaffolding</code></p> <p><code>/apps/settings/wcm/template-types/scaffolding/scaffolding</code></p> </td>
   <td>Nicht kontextsensitiv</td>
   <td>The components in the old location under <code>/etc/scaffolding</code> will continue to function, but have been deprecated.</td>
   <td>Adobe empfiehlt die Verwendung der neuen Gerüstkomponenten am neuen Speicherort.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/blueprints</code></td>
   <td><p>/libs/msm für standardmäßige Screens- und Commerce-Musterkonfigurationen</p> <p> </p> </td>
   <td>Nicht kontextsensitiv</td>
   <td><p>Verarbeitende Dienste berücksichtigen den alten Speicherort.</p> <p>Konfigurationen vom alten Speicherort werden berücksichtigt.</p> </td>
   <td>Die Konfigurationen müssen an die neuen Speicherorte kopiert werden.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/mobile</code></td>
   <td><code>/libs/settings/mobile</code></td>
   <td>Mandantenabhängig</td>
   <td>Die Funktion nutzt den Configuration Manager und unterstützt den alten Speicherort weiterhin als Fallback.</td>
   <td>
    <ol>
     <li>Die Konfigurationen von <code>/etc</code> zu <code>/conf/&lt;tenant&gt;/settings/mobile</code></li>
     <li>Aktualisieren Sie dann den Verweis im Inhalt wie folgt:</li>
    </ol> <p><code>/content/&lt;tenant&gt;/jcr:content/cq:deviceGroups{String[]}=mobile/groups/responsive</code></p> </td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/msm/rolloutConfigs</code></td>
   <td><code>/libs/msm/wcm/rolloutconfigs</code></td>
   <td>Nicht zutreffend</td>
   <td><p>Verarbeitende Dienste berücksichtigen den alten Speicherort.</p> <p>Wenn am alten Speicherort Konfigurationen gefunden werden, werden diese verwendet.</p> </td>
   <td>To align with the new model, configurations need to be created in the new locations, and the old ones under <code>/etc</code> must be deleted.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/segmentation/contexthub</code></td>
   <td><code>/conf/we-retail/settings/wcm/segments</code></td>
   <td>Mandantenabhängig</td>
   <td><p>Segmente vom alten Speicherort:</p>
    <ul>
     <li>Verbleiben schreibgeschützt in der Zielgruppenkonsole.</li>
     <li>Werden weiterhin auf der Seite geladen (wenn der angegebene Pfad unter <strong>Seiteneigenschaften &gt; Personalisierung &gt; Segmentpfad</strong> ausgewählt wird).</li>
     <li>Kann für Content-Targeting verwendet werden.</li>
    </ul> </td>
   <td>Sie können das <a href="/help/sites-deploying/upgrading-code-and-customizations.md#migrateconfigurations">Tool für die Segmentmigration</a> verwenden, um zum neuen Speicherort zu migrieren.</td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/social/config/languageOpts</code></td>
   <td><code>/libs/social/translation/languageOpts</code></td>
   <td>Nicht zutreffend</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/community/templates</code></td>
   <td><code>/libs/settings/community/templates</code></td>
   <td> </td>
   <td><p>Der Code berücksichtigt den Speicherort der alten Vorlage. Existing templates will continue to be referred and read/write from <code>/etc</code>.</p> <p><br /> Wenn ein Kunde bereits benutzerdefinierte E-Mail-Vorlagen unter einem anderen Pfad verwendet, den er als <strong>Stammverzeichnis für Vorlagen</strong> in der <strong>Konfiguration für das Beantworten von E-Mails in AEM Communities</strong> konfiguriert hat, sollten keine Änderungen vorgenommen werden.</p> </td>
   <td><p>A <a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration" target="_blank">migration utility</a> can align to the latest AEM Communities templates model.</p> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/community/badging</code></td>
   <td><p><strong>Badge-Regeln:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-Bilder: </strong></p> <p>The out of the box images in the old location at <code>/etc/community/badging/images</code> are moved to <code>/libs/community/badging/images </code> </p> <p> </p> <p>Custom images are moved to <code>/content/community/badging/images</code>.</p> <p> </p> </td>
   <td>Mandantenabhängig</td>
   <td><p>Der Code berücksichtigt die alten Badging-Pfade.</p> <p><br /> Er prüft zuerst, ob ältere Pfade<br /> vorhanden sind. Wenn keine Pfade vorhanden sind, werden die neuen Pfade verwendet.</p> </td>
   <td><p>Für die Anpassung an das aktuelle Modell ist eine manuelle Migration erforderlich. Führen Sie hierzu die folgenden Schritte aus:</p>
    <ol>
     <li>Erstellen Sie unter <strong>Tools</strong> mit dem Konfigurationsbrowser einen Behälter für den Site-Kontext.</li>
     <li>Wechseln Sie zum Stammordner der Site.</li>
     <li>Legen Sie für die Eigenschaft <code>cq:conf</code> den Behälterpfad fest, unter dem Sie alle Konfigurationen speichern möchten. Dieselbe Einstellung kann über den <strong>Assistenten für die Seitenbearbeitung als Eingabe für die Cloud-Konfiguration</strong> festgelegt und gespeichert werden.</li>
     <li>Move the relevant badging rules and scoring rules from <code>etc/community/*</code> to the site context bucket created in the previous step</li>
     <li>Passen Sie die Eigenschaften <code>badgingRules</code> und <code>scoringRules</code> an das Site-Stammverzeichnis an, um relative Verweise auf den neuen Speicherort der Regeln zu erhalten. As an example, if <code>cq:conf</code> is set to <code>/conf/we-retail</code>, the value for <code>badgingRules</code> will be <code>community/badging/rules</code> if rules are now moved to this new bucket</li>
     <li>Passen Sie auf die gleiche Weise die Verweise auf Scoring-Regeln in einem Badging-Regel-Knoten an, um einen relativen Pfad zu erhalten.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><p><code>/etc/cloudservices/facebookconnect</code></p> <p><code>/etc/cloudservices/twitterconnect</code></p> <p><code>/etc/cloudservices/pinterestconnect</code></p> </td>
   <td><p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> </td>
   <td>Mandantenabhängig</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/community/scoring</code></td>
   <td><code>/libs/settings/community/scoring</code></td>
   <td> </td>
   <td><p>Der Code berücksichtigt die alten Badging-Pfade.</p> <p><br /> Er prüft zuerst, ob ältere Pfade<br /> vorhanden sind. Wenn keine Pfade vorhanden sind, werden die neuen Pfade verwendet.</p> </td>
   <td><p>Für die Anpassung an das aktuelle Modell sind manuelle Migrationsschritte erforderlich.</p> <p>Diese Schritte stimmen mit den oben für die Badging-Regeln beschriebenen Schritten überein.</p> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/community/notifications</code></td>
   <td><code>/libs/settings/community/notifications</code></td>
   <td>Nicht kontextsensitiv</td>
   <td><p>Diese Konfigurationen sind nicht abwärtskompatibel. In der Spalte mit den Anforderungen für die Anpassung an das aktuelle Modell finden Sie die für die Migration zu den neuen Speicherorten erforderlichen Schritte.<br />  </p> <br /> </td>
   <td><p>Für die Anpassung an das aktuelle Modell ist eine manuelle Migration erforderlich. You can use the Granite Configuration Manager to move the configurations to the new path under <code>/apps/settings</code>.</p> <p>Therefore, you need to set the <code>mergeList</code> property to true on the <code>/libs/settings/community/subscriptions</code> node and then add an <code>nt:unstructured</code> child node.<br /> </p> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/community/subscriptions</code></td>
   <td><code>/libs/settings/community/subscriptions</code></td>
   <td>Nicht kontextsensitiv</td>
   <td>Diese Konfigurationen sind nicht abwärtskompatibel. In der Spalte mit den Anforderungen für die Anpassung an das aktuelle Modell finden Sie die für die Migration zu den neuen Speicherorten erforderlichen Schritte.</td>
   <td><p>Für die Anpassung an das aktuelle Modell ist eine manuelle Migration erforderlich. You can use the Granite Configuration Manager to move the configurations to the new path under <code>/apps/settings</code>.</p> <p>Therefore, you need to set the <code>mergeList</code> property to true on the <code>/libs/settings/community/subscriptions</code> node and then add an <code>nt:unstructured</code> child node.</p> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/socialconfig/srpc/defaultconfiguration</code></td>
   <td><code>/conf/global/settings/community/srpc/defaultconfiguration</code></td>
   <td>global</td>
   <td>Diese Konfigurationen sind abwärtskompatibel. Wenn alte Pfade gefunden werden, werden diese verwendet. Andernfalls haben die neuen Pfade Vorrang.</td>
   <td><p>Die Aufgabe für die Lazy-Content-Migration ist als <code>CQ64CommunitiesConfigsCleanupTask</code> verfügbar.</p> <p>Weitere Informationen finden Sie in der <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Dokumentation zur verzögerten Migration</a>.</p> </td>
  </tr>
  <tr>
   <td>AEM Communities</td>
   <td><code>/etc/watchwords</code></td>
   <td><code>/libs/community/watchwords</code></td>
   <td>Nicht zutreffend</td>
   <td>Diese Konfigurationen sind abwärtskompatibel. Wenn alte Pfade gefunden werden, werden diese verwendet. Andernfalls haben die neuen Pfade Vorrang.</td>
   <td><p>Die Aufgabe für die Lazy-Content-Migration ist als <code>CQ64CommunitiesConfigsCleanupTask</code> verfügbar.</p> <p>Watchwords will have to be manually moved from <code>/etc/watchwords</code> to <code>/conf/global/settings/community/watchwords</code>.</p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/models</code></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code> </p> <p><code>/var/workflow/models</code></p> </td>
   <td>global</td>
   <td><p>Legacy location is used if present and no configuration exists in <code>/libs</code> or <code>/conf</code>.</p> <p>When editing OOTB workflow models, context-aware overlays must be created under <code>/conf</code> to allow them to be modifiable.</p> <p>Package export needs to include the model in <code>/libs</code> or <code>/conf</code> and the runtime model in <code>/var/workflow/models.</code></p> </td>
   <td><p>Newly created models will be created in the <code>/conf/global/settings</code> location.</p> <p>Any edits in <code>/etc</code> or <code>/libs</code> require you to explicitly create an override in <code>/conf/global/settings</code> before editing can be done. The Edit button has to be selected, and it will cause the override in <code>/conf</code> to be created and editing allowed.</p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/launcher</code></td>
   <td><p><code>/libs/settings/workflow/launcher</code></p> <p><code>/conf/global/settings/workflow/launcher</code></p> </td>
   <td>global</td>
   <td>Legacy location is used if present and no configuration<br /> exists in <code>/libs</code> or <code>/conf</code> locations. Auf diese Weise bleiben benutzerdefinierte Starter erhalten.</td>
   <td><p>Newly created or edited launcher configurations are located in the <code>/conf</code> location.</p> <p>All launchers should be moved from the legacy <code>/etc</code> location to<code> /conf/global/settings/workflow/launcher.</code></p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/models</code></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code></p> </td>
   <td>global</td>
   <td>Legacy location is used if present and no configuration<br /> exists in <code>/libs</code> or <code>/conf</code> locations. Auf diese Weise bleiben benutzerdefinierte Workflow-Modelle erhalten.</td>
   <td><p>All workflow models should be moved from the legacy <code>/etc</code> location to <code>/conf/global/settings/workflow/models</code>.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/notification</code></td>
   <td><p><code>/libs/settings/workflow/notification</code></p> <p><code>/conf/global/settings/workflow/notification</code></p> </td>
   <td>Nicht kontextsensitiv</td>
   <td><p>Aus Gründen der Abwärtskompatibilität wird der alte Speicherort verwendet, sofern er vorhanden ist.</p> <p>Previously, out of the box templates had to be overridden by editing them in <code>/etc</code>. Now, override should be stored in <code>/conf/global</code>.</p> </td>
   <td>Weitere Informationen finden Sie in der Workflow-Dokumentation.<br />  </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/cloudservices/translation</code></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/translationcfg</code></p> <p> </p> </td>
   <td>Mandantenabhängig</td>
   <td>Alte Cloudservices. Werden in einem aktualisierten Setup beibehalten. Code zum Auflisten und Lesen ist im Produkt weiterhin als Fallback vorhanden.</td>
   <td><p>In order to move cloud configurations to <code>/conf</code>, you can either:</p>
    <ul>
     <li>Erstellen Sie Konfigurationen über die neue Touch-optimierte Benutzeroberfläche<br /> oder<br />  </li>
     <li>Copy the configurations from <code>/etc/cloudservices/translation</code> to their respective new location(s)</li>
    </ul> <p>Once this is done, the configurations need to be associated with Sites via <strong>Sites &gt; Properties</strong> in the user interface.</p> <p><em>Hinweis: Damit dies funktioniert, müssen Übersetzungs-Connectors mit AEM 6.5 kompatibel sein. </em></p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/cloudservices/msft-translation</code></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/msft-translation</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/msft-translation</code></p> </td>
   <td>Mandantenabhängig</td>
   <td>Alte Cloudservices. Werden in einem aktualisierten Setup beibehalten. Code zum Auflisten und Lesen ist im Produkt weiterhin als Fallback vorhanden.</td>
   <td><p>In order to move cloud configurations to <code>/conf</code>, you can either:</p>
    <ul>
     <li>Erstellen Sie Konfigurationen über die neue Touch-optimierte Benutzeroberfläche oder<br /> </li>
     <li>Copy older configurations from <code>/etc/cloudservices/translation</code> to their respective new location(s)</li>
    </ul> <p>Once this is done, the configurations need to be associated with Sites via <strong>Sites &gt; Properties</strong> in the user interface.</p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/cloudsettings</code></td>
   <td><p><code>/libs/settings/cloudsettings</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudsettings</code></p> </td>
   <td>Mandantenabhängig</td>
   <td><p>Existing entries under <code>/etc</code> remain in place on upgrading the instance.</p> <p>Wenn Sie nach der Aktualisierung auf die Benutzeroberfläche mit den Cloud-Einstellungen zugreifen, werden die vorhandenen Cloud-Einstellungen in die neue Repository-Struktur kopiert. Der vorhandene Inhalt bleibt dabei erhalten, um die Abwärtskompatibilität sicherzustellen.</p> </td>
   <td><p>Die Inhaltsmodelle sind identisch, es wird nur der Speicherort geändert und an kontextsensitive Konfigurationen angepasst.</p> <p>Die Aufgabe für die <a href="/help/sites-deploying/lazy-content-migration.md">verzögerte Migration</a> für diese Cloud-Einstellungen führt die folgenden Aktionen durch:</p>
    <ul>
     <li>Vorhandene Cloud-Einstellungen kopieren in <code>/etc/cloudsettings</code> <code>/conf/global/settings/cloudsettings</code></li>
     <li>Alle untergeordneten Elemente entfernen <code>/etc/cloudsettings</code></li>
    </ul> <p>Es gibt jedoch Schritte, die nach der Aktualisierung und vor der verzögerten Migration manuell ausgeführt werden müssen:</p>
    <ul>
     <li>All references pointing to <code>/etc/cloudsettings/*</code> need to be updated to point to <code>/conf/global</code></li>
    </ul> <p>Einschränkung:</p>
    <ul>
     <li>The <code>/etc/cloudsettings</code> container needs to be preserved</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/cloudservices/dmscene7</code></td>
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td>
   <td>Nur global</td>
   <td><p>Die Cloud-Konfiguration für das Setup „Dynamic Media - Scene“ (Ausführungsmodus <code>dynamicmedia_scene7</code>7) bleibt am ursprünglichen Speicherort. Der Prozess wird unverändert ausgeführt. Falls Sie den Wert für die Cloud-Konfiguration anpassen müssen, gibt es hierzu zwei Möglichkeiten:</p>
    <ol>
     <li>Aktualisieren einer vorhandenen Konfiguration über die alte Benutzeroberfläche für die Cloud-Konfiguration.</li>
     <li>Erstellen einer neuen Cloud-Konfiguration über die neue Touch-optimierte Benutzeroberfläche. Diese hat gegenüber der alten Vorrang.</li>
    </ol> </td>
   <td><p>Zur Anpassung an das aktuelle Modell muss das unter folgendem Link verfügbare Skript ausgeführt werden:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/presets/viewer</code></td>
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td>
   <td>Nur global</td>
   <td><p>The OOTB viewer presets will only be available in the new location, while the custom viewer preset will still be under <code>/etc</code> until a modification is incurred.</p> <p>Nach einer Änderung werden sie über die Lazy-Migration am neuen Speicherort gespeichert. Wenn der Bildserver eine Einbettungsanforderung erhält, sucht er sowohl unter dem alten als auch unter dem neuen Pfad. Es ist daher nicht erforderlich, den Einbettungscode oder die URLs zu ändern.</p> </td>
   <td><p>Die Voreinstellungen für die Standardanzeige sind nur am neuen Speicherort verfügbar. Für die benutzerdefinierten Voreinstellungen für die Anzeige müssen Sie das Migrationsskript unter folgendem Link ausführen:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p>Similar to the backward compatibility case, you don't have to adjust the copyURL/embed code to point to <code>/conf</code>. The existing request to <code>/etc</code> will be re-routed under the hood to the correct content from <code>/conf</code>.</p> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/imageserver/macros</code></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
   <td>Nur global</td>
   <td>The macro under <code>/etc</code> is still valid. If modify it, the modified node will be moved to the new location under <code>/conf</code> via a Lazy Migration task.</td>
   <td><p>Das Migrationsskript muss über den folgenden Link ausgeführt werden:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/video/dynamicmedia/Adaptive Video Encoding</code></td>
   <td><code>/libs/settings/dam/dm/presets/video/jcr:content/Adaptive Video Encoding</code></td>
   <td>Nicht zutreffend</td>
   <td><p>Das Standardvideoprofil wird entfernt, ohne dass die Eigenschaft des Asset-Ordners mit einer Verknüpfung mit dem Profil aktualisiert wird.</p> <p>Im Codierungsprozess ist eine Übersetzung des alten in den neuen Speicherort integriert. Der alte Pfad wird in den neuen Profilpfad umgewandelt.</p> </td>
   <td>Keine Änderungen erforderlich</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
   <td>Nur global</td>
   <td><p>Das benutzerdefinierte Videoprofil bleibt so lange unverändert an seinem Speicherort, bis es bearbeitet wird.</p> <p>Nach einer Bearbeitung wird es über die Lazy-Migration an den neuen Speicherort verschoben. Dies ist ähnlich wie die standardmäßige Videovoreinstellung bei der Codierungssuche. Der Codierungsprozess besitzt eine integrierte Pfadübersetzung, die zuerst am alten Speicherort und anschließend am neuen Speicherort nach dem Videoprofil sucht.</p> </td>
   <td><p>Für die Anpassung an das aktuelle Modell können Sie das folgende Migrationsskript ausführen:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
   <td>Nur global</td>
   <td><p>Diese Cloud-Konfiguration für ein hybrides Setup für dynamische Medien (Ausführungsmodus <code>dynamicmedia</code>) verbleibt am selben Speicherort. Der Prozess funktioniert wie bisher. Falls Sie den Konfigurationswert anpassen müssen, ist dies auf zwei Wegen möglich.</p>
    <ol>
     <li>Aktualisieren einer vorhandenen Konfiguration über die alte Benutzeroberfläche für die Cloud-Konfiguration.</li>
     <li>Erstellen einer neuen Cloud-Konfiguration über die neue Touch-optimierte Benutzeroberfläche. Diese hat gegenüber der alten Vorrang.</li>
    </ol> </td>
   <td><p>Sie müssen das Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt. Sie finden das Skript unter folgendem Link:<br />  </p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/cloudservices/youtube</code></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
   <td>Nur global</td>
   <td><p>Die Cloud-Konfiguration für das DM-Youtube-Setup verbleibt am selben Speicherort. Der Prozess funktioniert wie bisher. Falls Sie den Cloud-Konfigurationswert anpassen müssen, ist dies auf zwei Wegen möglich.</p>
    <ol>
     <li>Aktualisieren einer vorhandenen Konfiguration über die alte Benutzeroberfläche für die Cloud-Konfiguration.</li>
     <li>Erstellen einer neuen Cloud-Konfiguration über die neue Touch-optimierte Benutzeroberfläche. Diese hat gegenüber der alten Vorrang.</li>
    </ol> </td>
   <td><p>Sie können ein Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt. Sie finden das Skript unter folgendem Link:<br />  </p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p> </p> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/presets/analytics</code></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
   <td>Nur global</td>
   <td>Keine Aktion erforderlich.</td>
   <td><p>Sie können ein Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt. Sie finden das Skript unter folgendem Link:<br />  </p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><p><code>/etc/notification/email/default/com.day.cq.replication</code></p> <p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td>
   <td><code>/libs/settings/notification-templates</code></td>
   <td>Nur global</td>
   <td>The templates in <code>/etc/notification/email/default/</code> are given precedence over the ones in <code>/libs/settings/notification-templates</code>.</td>
   <td>In order to align to the latest model, you can create new templates under <code>/apps/settings/notification-templates</code> and perform new modifications there.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><p><code>/etc/msm/rolloutconfigs/launch</code></p> <p><code>/etc/msm/rolloutconfigs/pushonmodifyshallow</code></p> </td>
   <td><p><code>/libs/msm/launches/rolloutconfigs/launch</code></p> <p><code>/libs/msm/launches/rolloutconfigs/pushonmodifyshallow</code></p> </td>
   <td>Nicht zutreffend</td>
   <td><p>Verarbeitende Dienste berücksichtigen den alten Speicherort.</p> <p>Wenn am alten Speicherort Konfigurationen gefunden werden, werden diese verwendet.</p> </td>
   <td>To align with the new model, configurations need to be created in the new locations, and the old ones under <code>/etc</code> must be deleted.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/translation/supportedLanguages</code></td>
   <td><p><code>/libs/settings/translation/supportedLanguages</code></p> <p><code>/apps/settings/translation/supportedLanguages</code></p> </td>
   <td>Nicht kontextsensitiv</td>
   <td>Voraussetzung ist, dass angepasste Sprachen zur Liste hinzugefügt werden.<br />  </td>
   <td>Überlagern und aktualisieren Sie die neue Liste mit zusätzlichen Sprachen (sofern vorhanden). Alternatively, copying the old list to <code>/apps</code> location would also work.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/models/translation/translation_rules.xml</code></td>
   <td><p><code>/libs/settings/translation/rules/translation_rules.xml</code></p> <p><code>/apps/settings/translation/rules/translation_rules.xml</code></p> <p><code>/conf/global/settings/translation/rules/translation_rules.xml</code></p> </td>
   <td>Nur global</td>
   <td>Werden in einem aktualisierten Setup beibehalten. Code zum Auflisten und Lesen ist weiterhin im Produkt vorhanden.</td>
   <td>To persist the changes, copy the XML file from <code>/etc</code> to <code>/libs</code> or <code>/conf</code>. Alternatively,<strong> </strong>remove file from <code>/etc</code>.</td>
  </tr>
 </tbody>
</table>

## Client-seitige Bibliotheken {#client-side-libraries}

[Clientseitige Bibliotheken](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/clientlibs.html) sind JavaScript- und CSS-Code, der im Browser verarbeitet wird.

### Erweiterbarkeitsstrategie {#extensibility-strategy-1}

AEM bietet ein erweiterbares Framework, um mehrere JavaScript-Dateien anzufügen. Any file with the same &quot;categories&quot; property will be appended, allowing custom code to extend AEM code that resides under `/libs`.

<table>
 <tbody>
  <tr>
   <td><strong>Lösung</strong></td>
   <td><strong>Vorherige Position</strong><br /> </td>
   <td><strong>Neuer Speicherort </strong></td>
   <td><strong>Abwärtskompatibilitätsansatz </strong></td>
   <td><strong>Anforderungen für die Ausrichtung am aktuellsten Modell </strong></td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/fp</code></td>
   <td><code>/libs/fd/fp/components</code></td>
   <td><p>Alte Client-Bibliothek, die auf einer Instanz weiterbesteht, die durch ein direktes Upgrade aktualisiert wurde.</p> <p>New clientlibs have the same category names along with the "<strong><code>replaces</code></strong>" property to avoid merging of old and new clientlibs.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/rte</code></td>
   <td><code>/libs/fd/rte</code></td>
   <td><p>Alte clientlibs, die auf einer Instanz beibehalten werden, die über eine ersetzende Aktualisierung aktualisiert wurde.</p> <p>New clientlibs have the same category names along with the "<strong><code>replaces</code></strong>" property to avoid merging of old and new clientlibs.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/af</code></td>
   <td><code>/libs/fd/af/authoring/clientlibs</code></td>
   <td>Alte Client-Bibliotheken. Bestehen auf einer Instanz weiter, die durch ein direktes Upgrade aktualisiert wurde. New clientlibs have the same category names along with the "<strong><code>replaces</code></strong>" property to avoid merging of old and new clientlibs.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/themes/themeLibrary</code></td>
   <td>Nicht mehr im Standardpaket von AEM 6.5 enthalten.</td>
   <td><p>Standarddesigns in adaptiven Formularen.</p> <p>Werden in einem aktualisierten Setup beibehalten.</p> </td>
   <td>Dies ist teilweise vom Benutzer generierter Inhalt. Wird mit dem Namen <code>aem-forms-reference-themes</code> als Referenzinhaltspaket bereitgestellt.</td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/expeditor</code></td>
   <td><code>/libs/fd/expeditor/clientlibs</code></td>
   <td>Alte Client-Bibliotheken. Bestehen auf einer Instanz weiter, die durch ein direktes Upgrade aktualisiert wurde. New clientlibs have the same category names along with the "<strong><code>replaces</code></strong>" property to avoid merging of old and new clientlibs.</td>
   <td>Keine Aktion erforderlich.<p> </p> </td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/clientlibs/fd/fmaddon</code></td>
   <td><code>/libs/fd/fmaddon</code></td>
   <td>Alte Analytics- und Target-Client-Bibliotheken die nicht für die direkte Verarbeitung vorgesehen sind. </td>
   <td>Werden nach der Aktualisierung mit einem Cleanup-Filter bereinigt.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td>
   <td><code>/libs/dam/clientlibs</code></td>
   <td>Alte Client-Bibliotheken haben unterschiedliche Client-Kategorienamen.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td> </td>
   <td><code>/etc/clientlibs/ckeditor</code></td>
   <td><code>/libs/clientlibs/ckeditor</code></td>
   <td>Dies sind alte Client-Bibliotheken. Sie werden in einem aktualisierten Setup beibehalten. New clientlibs have the same category names along with the "<code>replaces</code>" property to avoid the merging of old and new clientlibs.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/foundation/sitecatalyst</code></td>
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td>
   <td><p>Dies sind alte Client-Bibliotheken. Werden in einem aktualisierten Setup beibehalten.</p> <p>Neue Client-Bibliotheken haben dieselben Kategorienamen.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/foundation/personalization</code></td>
   <td><code>/libs/cq/personalization/clientlibs/personalization</code></td>
   <td><p>Dies sind alte Client-Bibliotheken. Werden in einem aktualisierten Setup beibehalten.</p> <p>Neue Client-Bibliotheken haben dieselben Kategorienamen.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/foundation/searchpromote</code></td>
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td>
   <td><p>Dies sind alte Client-Bibliotheken. Werden in einem aktualisierten Setup beibehalten.</p> <p>Neue Client-Bibliotheken haben dieselben Kategorienamen.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/foundation/target</code></td>
   <td><code>/libs/cq/target/clientlibs/target</code></td>
   <td><p>Dies sind alte Client-Bibliotheken. Werden in einem aktualisierten Setup beibehalten.</p> <p>Neue Client-Bibliotheken haben dieselben Kategorienamen.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/address</code></td>
   <td><code>/libs/cq/address/clientlibs</code></td>
   <td>Neue Client-Bibliotheken haben dieselben Kategorienamen.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/wcm/foundation</code></td>
   <td><code>/libs/wcm/foundation/clientlibs</code></td>
   <td>Alte Client-Bibliotheken. Werden in einem aktualisierten Setup beibehalten. Neue Client-Bibliotheken haben dieselben Kategorienamen zusammen mit der Eigenschaft <strong>ersetzt</strong>, um ein Vermischen alter und neuer Client-Bibliotheken zu vermeiden.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Sites</td>
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td>
   <td><p><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></p> </td>
   <td><p>Bei einem direkten Upgrade verbleibt die veraltete Datei (/etc/clientlibs/wcm/…_) und kann nicht automatisch entfernt werden, damit Verweise auf die alte /etc/clientlibs/wcm/foundation/grid/grid_base.less weiterhin funktionieren.</p> <p><em>Beachten Sie, dass es sich hierbei um einen Sonderfall handelt, in dem diese LESS-Datei über LESS @import-Anweisungen über einen absoluten Pfad referenziert wird und NICHT über die clientlib-Kategorie.</em></p> <p>Wenn der LESS-Verweis des Kunden auf grid_base.less auf eine nicht vorhandene Datei zeigt, schlägt der Modus für das bearbeitbare Vorlagenlayout fehl und daran vorgenommenen Anpassungen sind nicht vorhanden (d. h. alle Komponenten erscheinen in voller Breite auf der Seite).</p> </td>
   <td>Aktualisieren Sie alle Verweise im benutzerdefinierten Code (d. h. in allen LESS-Dateien, die auf die verschobene Datei grid_base.less verweisen) so, dass sie auf den neuen Speicherort zeigen, und entfernen Sie den alten Speicherort.</td>
  </tr>
 </tbody>
</table>

Dies sind weitere Neustrukturierungen, die in den vorherigen Abschnitten nicht behandelt wurden.

### Erweiterbarkeitsstrategie {#extensibility-strategy-2}

In den Tabellenzeilen werden alle unterstützten Erweiterbarkeitsmodelle angegeben. In diesem Abschnitt enthaltener Inhalt wird in der Regel nicht erweitert.

## Sonstiges {#miscellaneous}

<table>
 <tbody>
  <tr>
   <td><strong>Lösung</strong></td>
   <td><strong>Vorherige Position</strong><br /> </td>
   <td><strong>Neuer Speicherort </strong></td>
   <td><strong>Abwärtskompatibilitätsansatz </strong></td>
   <td><strong>Anforderungen für die Ausrichtung am aktuellsten Modell </strong></td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/designs/fd/fp</code></td>
   <td><code>/libs/fd/fp</code></td>
   <td><p>Alte OOTB-Vorlagen des AEM Forms Portal. Diese Vorlagen verbleiben nach einer Aktualisierung in /etc.</p> <p>In the template listing, the word<em> "deprecated</em>" will be added to the template title to differentiate them with the newer templates.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Forms</td>
   <td><code>/etc/aep</code></td>
   <td><code>/var/fd/content/annotations</code></td>
   <td>Alte Correspondence Management-Kommentardatei. Nicht für die direkte Verarbeitung vorgesehen. Wird nach der Aktualisierung mit einem Cleanup-Filter bereinigt.</td>
   <td>Der alte Speicherort wird nach der Aktualisierung mit einem Cleanup-Filter bereinigt.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/tags</code></td>
   <td><code>/content/cq:tags</code></td>
   <td>Die Tag-Manager-API unterstützt sowohl den alten als auch den neuen Speicherort. Wenn die OSGi-Komponente JcrTagManagerFactory gestartet wird, erkennt sie, ob sie auf einer aktualisierten Instanz oder einer alten Instanz läuft, und verwendet den entsprechenden Speicherort.<br />  </td>
   <td><p>Für eine korrekte Anpassung an das neue Modell:</p>
    <ol>
     <li>Ersetzen Sie die Verweise auf das alte Modell (<code>/etc/tags</code>) durch das neue (<code>/content/cq:tags</code>), indem Sie die Variable <code>tagID.</code></li>
     <li>Melden Sie sich bei CRXDE Lite an.</li>
     <li>Verschieben Sie die Tags von <code>/etc/tags</code> nach <code>/content/cq:tags</code></li>
     <li>OSGi-Komponente neu starten <code class="code">com.day.cq.tagging.impl.JcrTagManagerFactoryImpl.
        </code></li>
    </ol> <p> </p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/instances</code></td>
   <td><code>/var/workflow/instances</code></td>
   <td>Alter Speicherort, der bei der Verarbeitung von<br /> laufenden Workflows verwendet wird. Neue Workflows verwenden den neuen Speicherort in <code>/var.</code></td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/scripts</code></td>
   <td><p><code>/libs/workflow/scripts</code></p> <p><code>/apps/workflow/scripts</code></p> </td>
   <td><p>Existing Workflow Model Steps that reference workflow scripts in the legacy location at <code>/etc/workflow/scripts</code> will continue to point to these scripts after the upgrade, and execute properly.</p> <p>Beachten Sie, dass die AEM-Benutzeroberfläche für die Bearbeitung der Workflow-Schritte (Verarbeiten, Aufteilen usw.) no longer lists scripts under <code>/etc/workflow/scripts</code> in the drop-down used select to workflow scripts.</p> </td>
   <td><p>Workflows, die diese Skripte nutzen, funktionieren weiterhin wie erwartet, solange der zugehörige Workflow-Verarbeitungsschritt nicht in AEM bearbeitet wurde.</p> <p>Für eine vollständige Abwärtskompatibilität, die auch bestehen bleibt, wenn Schritte bearbeitet werden, muss der Kunde nach der Aktualisierung manuell eingreifen:</p>
    <ul>
     <li>The scripts must be moved from <code>/etc/workflow/scripts</code> to <code>/apps/workflow/scripts.</code></li>
     <li>Any<strong> </strong>references to <code>/etc/workflow/scripts</code> in workflow model steps must be updated to reference the new <code>/apps/workflow/scripts</code> location.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/replication/treeactivation</code></td>
   <td><code>/libs/replication/treeactivation</code></td>
   <td>Die Seite mit dem Dienstprogramm ClassicUI bleibt bei der Aktualisierung erhalten.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Assets</td>
   <td><code>/etc/dam/jobs</code></td>
   <td><code>/var/dam/jobs</code></td>
   <td><p>Temporärer Speicherort für ZIP-Dateien, die für das Aufrufen der Downloadaktion von AEM Assets generiert werden.</p> <p>Hier ist keine Aktualisierung erforderlich, da die Dateien am neuen Speicherort erstellt werden, sobald der Client das Herunterladen des Assets anfordert.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/products</code></td>
   <td><code>/var/commerce/products</code></td>
   <td><p>Der alte Inhalt verbleibt an seinem Speicherort und kann nach der Aktualisierung verwendet werden.</p> <p>Für die Migration an den neuen Speicherort ist eine Lazy-Migration verfügbar.</p> </td>
   <td><p>Die Migration erfolgt über eine Lazy Migration-Aufgabe: <code>CQ64CommerceMigrationTask.</code></p> <p>Diese führt folgende Schritte aus:</p>
    <ul>
     <li>Anpassung der Verweise auf den alten Speicherort an den neuen Speicherort.</li>
     <li>Verschieben des Inhalts vom alten Speicherort an den neuen Speicherort</li>
     <li><p>Entfernen des alten Speicherorts, um die Verwendung des neuen Speicherorts im gesamten System zu aktivieren.</p> </li>
    </ul> <p>Die von der Aufgabe betroffenen Speicherorte:</p>
    <ul>
     <li>/etc/commerce/products</li>
     <li>/etc/commerce/collections<br /> </li>
     <li>/etc/commerce/orders<br /> </li>
     <li>/etc/commerce/payment-methods<br /> </li>
     <li>/etc/commerce/shipping-methods<br /> </li>
    </ul> <p>Für größere Kataloge empfiehlt es sich, die Aufgabe für die Commerce-Migration einzeln auszuführen, indem die folgende Java-Systemeigenschaft an AEM übergeben wird:</p>
    <ul>
     <li>Eigenschaftsname: <code>com.adobe.upgrade.forcemigration</code></li>
     <li>Eigenschaftswert: <code>com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></li>
    </ul> <p>Nach der Migration muss AEM neu gestartet werden.</p> </td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/orders</code></td>
   <td><code>/var/commerce/orders</code></td>
   <td><p>Der alte Inhalt verbleibt an seinem Speicherort und kann nach der Aktualisierung verwendet werden.</p> <p>Für die Migration an den neuen Speicherort ist eine Lazy-Migration verfügbar.</p> </td>
   <td>See the description above for <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/collections</code></td>
   <td><code>/var/commerce/collections</code></td>
   <td><p>Der alte Inhalt verbleibt an seinem Speicherort und kann nach der Aktualisierung verwendet werden.</p> <p>Für die Migration an den neuen Speicherort ist eine Lazy-Migration verfügbar.</p> </td>
   <td>See the description above for <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/classifications</code></td>
   <td><code>/var/commerce/classifications</code></td>
   <td>Keine Aktion erforderlich.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/shipping-methods</code></td>
   <td><code>/var/commerce/shipping-methods</code></td>
   <td><p>Der alte Inhalt verbleibt an seinem Speicherort und kann nach der Aktualisierung verwendet werden.</p> <p>Für die Migration an den neuen Speicherort ist eine Lazy-Migration verfügbar.</p> </td>
   <td>See the description above for <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/payment-methods</code></td>
   <td><code>/var/commerce/payment-methods</code></td>
   <td><p>Der alte Inhalt verbleibt an seinem Speicherort und kann nach der Aktualisierung verwendet werden.</p> <p>Für die Migration an den neuen Speicherort ist eine Lazy-Migration verfügbar.</p> </td>
   <td>See the description above for <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/taskmanagement</code></td>
   <td><code>/var/taskmanagement</code></td>
   <td><p>Neue Aufgaben werden unter <code>/var/taskmanagement</code></p> <p>Am alten Speicherort vorhandene Aufgaben werden weiterhin im AEM-Posteingang angezeigt.</p> </td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/packages</code></td>
   <td><code>/var/workflow/packages</code></td>
   <td><p>Mit AEM Package Manager erstellte AEM-Pakete werden weiterhin in <code>/etc/workflow/packages.</code></p> <p>Andere Pakete, die über AEM Sites und Workflows erstellt wurden, werden weiterhin in<code>/var/workflow/packages.</code></p> <p>Packages found in both <code>/etc/workflow/packages</code> and <code>/var/workflow/packages</code> can still be edited via AEM's Package Manager. </p> </td>
   <td><p>Keine Aktion erforderlich.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/workflow/instances</code></td>
   <td><code>/var/workflow/instances</code></td>
   <td>New workflow instances will be created under <code>/var</code> automatically.</td>
   <td>Keine Aktion erforderlich.</td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/commerce/searchpromote</code></td>
   <td><code>/var/cq/searchpromote</code></td>
   <td><p>Neuer Speicherort für Search&amp;Promote-Feedinhalt.</p> <p>Die alte URL funktioniert weiterhin und die Anforderung wird durch einen ServletFilter an den neuen Speicherort weitergeleitet.</p> </td>
   <td>Keine Aktion erforderlich.<br /><br /> </td>
  </tr>
  <tr>
   <td>Alle</td>
   <td><code>/etc/dtm-hook</code></td>
   <td><code>/var/cq/dtm/web-hook</code></td>
   <td><p>Neuer Speicherort für DTM Web-Hooks.</p> <p>Die alte URL funktioniert weiterhin und die Anforderung wird durch einen ServletFilter an den neuen Speicherort weitergeleitet.</p> </td>
   <td>Keine Aktion erforderlich.<br /> <br /> </td>
  </tr>
 </tbody>
</table>

