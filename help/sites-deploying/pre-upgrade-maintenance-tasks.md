---
title: Wartungsaufgaben vor einem Upgrade
seo-title: Pre-Upgrade Maintenance Tasks
description: Erfahren Sie mehr über die Aufgaben im Vorfeld des AEM-Upgrades
seo-description: Learn about the pre-upgrade tasks in AEM.
uuid: 5da1cfc7-8a10-47b1-aafb-2cd112e3f818
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 291c91e5-65ff-473d-ac11-3da480239e76
docset: aem65
feature: Upgrading
exl-id: 37d4aee4-15eb-41ab-ad71-dfbd5c7910f8
source-git-commit: 2981f11565db957fac323f81014af83cab2c0a12
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 42%

---

# Wartungsaufgaben vor einem Upgrade{#pre-upgrade-maintenance-tasks}

Bevor Sie mit dem Upgrade beginnen, ist es wichtig, die folgenden Wartungsaufgaben durchzuführen, damit das System bereit ist und zurückgesetzt werden kann, falls Probleme auftreten:

* [Überprüfung auf ausreichenden Festplattenspeicher](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Vollständige Sicherung von AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Sicherung von Änderungen unter /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Erstellen der quickstart.properties-Datei](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Konfigurieren von Workflow- und Auditprotokoll-Löschung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installieren, Konfigurieren und Ausführen der Aufgaben vor dem Upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Deaktivieren von benutzerdefinierten Anmeldemodulen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Entfernen von Updates aus dem /install-Verzeichnis](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Beenden aller Cold-Standby-Instanzen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Deaktivieren von benutzerdefinierten geplanten Aufträgen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Durchführen der Offline-Revisionsbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Durchführen der Datenspeicherbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Upgrade des Datenbankschemas bei Bedarf](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Löschen von Benutzern, die das Upgrade behindern könnten](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)

* [Rotieren von Protokolldateien](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Überprüfung auf ausreichenden Festplattenspeicher {#ensure-sufficient-disk-space}

Beim Ausführen der Aktualisierung muss zusätzlich zu den Aktivitäten für die Inhalts- und Code-Aktualisierung eine Repository-Migration durchgeführt werden. Die Migration erstellt eine Kopie des Repositorys im neuen Segment-TAR-Format. Daher benötigen Sie genügend Speicherplatz, um eine zweite, möglicherweise größere Version Ihres Repositorys beizubehalten.

## Vollständige Sicherung von AEM {#fully-back-up-aem}

Bevor Sie mit dem Upgrade beginnen, sollten Sie eine vollständige Sicherungskopie von AEM erstellen. Stellen Sie sicher, dass Sie Ihr Repository, Ihre Anwendungsinstallation, Ihren Datenspeicher und gegebenenfalls Ihre Mongo-Instanzen sichern. Weitere Informationen zum Sichern und Wiederherstellen einer AEM-Instanz finden Sie unter [Sicherung und Wiederherstellung](/help/sites-administering/backup-and-restore.md).

## Sicherung von Änderungen unter /etc {#backup-changes-etc}

Ein Upgrade ist ein guter Anlass, um vorhandene Inhalte und Konfigurationen unter den Pfaden `/apps` und `/libs` im Repository zu pflegen und zusammenzuführen. Für Änderungen, die an der `/etc` Pfad, einschließlich ContextHub-Konfigurationen, häufig müssen diese Änderungen nach der Aktualisierung erneut angewendet werden. Während das Upgrade eine Sicherungskopie aller Änderungen vornimmt, die nicht zusammengeführt werden können unter `/var`empfiehlt Adobe, diese Änderungen manuell zu sichern, bevor Sie mit der Aktualisierung beginnen.

## Erstellen der quickstart.properties-Datei {#generate-quickstart-properties}

Wenn Sie AEM aus der JAR-Datei starten, wird eine `quickstart.properties` -Datei wird generiert unter `crx-quickstart/conf`. Wenn AEM bisher nur mit dem Startskript gestartet wurde, ist diese Datei nicht vorhanden und die Aktualisierung schlägt fehl. Überprüfen Sie, ob diese Datei vorhanden ist, und starten Sie AEM aus der JAR-Datei neu, falls sie nicht vorhanden ist.

## Konfigurieren von Workflow- und Auditprotokoll-Löschung {#configure-wf-audit-purging}

Die `WorkflowPurgeTask` und `com.day.cq.audit.impl.AuditLogMaintenanceTask` -Aufgaben erfordern separate OSGi-Konfigurationen und können ohne diese nicht ausgeführt werden. Falls diese Aufgaben beim Ausführen von Aufgaben vor dem Upgrade fehlschlagen, sind die Ursache dafür wahrscheinlich fehlende Konfigurationen. Daher müssen Sie die OSGi-Konfigurationen für diese Aufgaben hinzufügen oder diese Aufgaben vollständig aus der Liste der Optimierungsaufgaben vor dem Upgrade löschen, falls Sie diese nicht ausführen möchten. Die Dokumentation zum Konfigurieren von Workflow-Bereinigungsaufgaben finden Sie unter [Verwalten von Workflow-Instanzen](/help/sites-administering/workflows-administering.md) Die Konfiguration der Wartungsaufgaben im Auditprotokoll finden Sie unter [Auditprotokollwartung in AEM 6](/help/sites-administering/operations-audit-log.md).

Informationen zu Workflow- und Auditprotokolllöschungen in CQ 5.6 sowie zur Bereinigung von Auditprotokollen in AEM 6.0 finden Sie unter [Workflow- und Auditknoten bereinigen](https://helpx.adobe.com/de/experience-manager/kb/howtopurgewf.html).

## Installieren, Konfigurieren und Ausführen der Aufgaben vor dem Upgrade {#install-configure-run-pre-upgrade-tasks}

Da AEM ein hohes Maß an Anpassung erlaubt, gibt es in der Regel keine einheitliche Vorgehensweise für die Durchführung von Upgrades. Dadurch wird die Schaffung eines standardisierten Verfahrens für Upgrades zu einem schwierigen Prozess.

In früheren Versionen war es auch schwierig, Aktualisierungen AEM, die angehalten wurden oder die nicht sicher fortgesetzt werden konnten. Dieses Problem führte zu Situationen, in denen ein Neustart des vollständigen Aktualisierungsverfahrens erforderlich war oder fehlerhafte Aktualisierungen durchgeführt wurden, ohne Warnungen auszulösen.

Um diese Probleme zu beheben, hat die Adobe dem Aktualisierungsprozess mehrere Verbesserungen hinzugefügt, sodass er robuster und benutzerfreundlicher wird. Wartungsaufgaben vor einem Upgrade, die bisher manuell durchgeführt werden mussten, wurden optimiert und automatisiert. Darüber hinaus wurden Berichte hinzugefügt, die nach dem Upgrade erstellt werden, sodass der Vorgang umfassend überprüft werden kann und Probleme einfach identifizierbar sind.

Wartungsaufgaben vor der Aktualisierung sind derzeit auf verschiedene Schnittstellen verteilt, die teilweise oder vollständig manuell durchgeführt werden. Durch die in AEM 6.3 eingeführte Optimierungsfunktionen für die Wartungsaufgaben im Vorfeld des Upgrades können diese Aufgaben einheitlich ausgelöst und ihre Ergebnisse bei Bedarf überprüft werden.

Sämtliche Aufgaben, die zum Optimierungsschritt vor dem Upgrade gehören, sind mit allen Versionen (ab Version 6.0) kompatibel.

### Einrichtung {#how-to-set-it-up}

In AEM 6.3 und höher ist die Optimierung der Wartungsaufgaben vor einem Upgrade Teil der quickstart-Datei.

<!-- URLs below are all 404s. This content should probably be removed because it is entirely obsolete.

If you are upgrading from an older version of AEM 6, they are made available through separate packages that you can download from the Package Manager.

You can find the packages at these locations:

* [For upgrading from AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [For upgrading from AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [For upgrading from AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62) -->

### Verwendung {#how-to-use-it}

Die OSGi-Komponente `PreUpgradeTasksMBean` ist mit einer Liste von Wartungsaufgaben vor dem Upgrade vorkonfiguriert, die gleichzeitig ausgeführt werden können. Sie können die Aufgaben mit den nachfolgenden Schritten konfigurieren:

1. Navigieren Sie zur Web-Konsole unter *https://Server-Adresse:Serverport/system/console/configMgr*.

1. Suchen Sie nach &quot;**preupgradetasks**&quot;, klicken Sie dann auf die erste übereinstimmende Komponente. Der vollständige Name der Komponenten lautet `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`.

1. Ändern Sie die Liste der auszuführenden Wartungsaufgaben wie folgt:

   ![1487758925984](assets/1487758925984.png)

Die Aufgabenliste unterscheidet sich je nach dem verwendeten Ausführungsmodus zum Starten der Instanz. Nachfolgend finden Sie eine Beschreibung des Ausführungsmodus, für den jede Wartungsaufgabe entwickelt wurde.

<table>
 <tbody>
  <tr>
   <td><strong>Aufgabe</strong></td>
   <td><strong>Ausführungsmodus</strong></td>
   <td><strong>Anmerkungen</strong></td>
  </tr>
  <tr>
   <td><code>TarIndexMergeTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>DataStoreGarbageCollectionTask</code></td>
   <td>crx2</td>
   <td>Läuft markieren und kehren. Entfernen Sie bei freigegebenen Datenspeichern diesen Schritt und führen Sie<br /> -Instanzen manuell oder ordnungsgemäß vorbereiten, bevor sie ausgeführt werden.</td>
  </tr>
  <tr>
   <td><code>ConsistencyCheckTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>WorkflowPurgeTask</code></td>
   <td>crx2/crx3</td>
   <td>Vor der Ausführung muss die Adobe Granite Workflow Purge Configuration OSGi konfiguriert werden.</td>
  </tr>
  <tr>
   <td><code>GenerateBundlesListFileTask</code></td>
   <td>crx2/crx3</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>RevisionCleanupTask</code></td>
   <td>crx3</td>
   <td>Führen Sie bei TarMK-Instanzen unter AEM 6.0 bis 6.2 stattdessen die Offline-Revisionsbereinigung manuell aus.</td>
  </tr>
  <tr>
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td>
   <td>crx3</td>
   <td>Vor der Ausführung muss die OSGi-Konfiguration für die Auditprotokolllöschung konfiguriert werden.</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Die `DataStoreGarbageCollectionTask` ruft einen Vorgang vom Typ Datastore Garbage Collection mit der Mark- und Sweep-Phase auf, falls verwendet. Stellen Sie bei Bereitstellungen, die einen freigegebenen Datenspeicher verwenden, sicher, dass Sie ihn ordnungsgemäß neu konfigurieren oder die Instanz vorbereiten, um das Löschen von Elementen zu vermeiden, auf die von einer anderen Instanz verwiesen wird. Dieser Prozess erfordert möglicherweise, die Markierungsphase manuell auf allen Instanzen auszuführen, bevor diese Aufgabe vor der Aktualisierung ausgelöst wird.

### Standardkonfiguration der Konsistenzprüfungen vor einem Upgrade {#default-configuration-of-the-pre-upgrade-health-checks}

Die OSGi-Komponente `PreUpgradeTasksMBeanImpl` umfasst eine vorkonfigurierte Liste von Tags für Konsistenzprüfungen vor einem Upgrade, die ausgeführt werden sollen, wenn die Methode `runAllPreUpgradeHealthChecks` aufgerufen wird:

* **System** - das Tag, das von den Wartungs-Konsistenzprüfungen für Granite verwendet wird

* **vor der Aktualisierung** - ein benutzerdefiniertes Tag, das zu allen Konsistenzprüfungen hinzugefügt werden kann, die Sie vor einer Aktualisierung ausführen können

Die Liste kann bearbeitet werden. Sie können das Pluszeichen **(+)** und minus **(-)** -Schaltflächen neben den Tags, um weitere benutzerdefinierte Tags hinzuzufügen oder die standardmäßigen Tags zu entfernen.

**MBean-Methoden**

Auf die Funktion für verwaltete Beans kann über die [JMX-Konsole](/help/sites-administering/jmx-console.md).

Sie können wie folgt auf die MBeans zugreifen:

1. Wechseln Sie zur JMX-Konsole unter *https://Server-Adresse:Serverport/system/console/jmx*.
1. Suchen Sie nach **PreUpgradeTasks** und klicken Sie auf das Ergebnis.

1. Wählen Sie im Bereich **Operations** eine Methode und im daraufhin angezeigten Fenster **Invoke** aus.

Nachfolgend finden Sie eine Liste aller verfügbaren Methoden, die von `PreUpgradeTasksMBeanImpl` bereitgestellt werden:

<table>
 <tbody>
  <tr>
   <td><strong>Name der Methode</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><code>getAvailablePreUpgradeTasksNames()</code></td>
   <td>INFO</td>
   <td>Zeigt die Namensliste der verfügbaren Wartungsaufgaben vor dem Upgrade an.</td>
  </tr>
  <tr>
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td>
   <td>INFO</td>
   <td>Zeigt die Namensliste Liste der Konsistenzprüfungen vor dem Upgrade an.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeTasks()</code></td>
   <td>ACTION</td>
   <td>Führt alle in der Liste genannten Wartungsaufgaben vor dem Upgrade aus.</td>
  </tr>
  <tr>
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td>
   <td>ACTION</td>
   <td>Führt die Wartungsaufgabe vor dem Upgrade mit dem als Parameter angegebenen Namen aus.</td>
  </tr>
  <tr>
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Prüft, ob die <code>runAllPreUpgradeTasksmaintenance</code> Aufgabe wird ausgeführt.</td>
  </tr>
  <tr>
   <td><code>getAnyPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Prüft, ob Wartungsaufgaben vor der Aktualisierung ausgeführt werden und<br /> gibt ein Array zurück, das die Namen der derzeit ausgeführten Aufgaben enthält.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td>
   <td>ACTION</td>
   <td>Gibt die genaue Ausführungszeit der Wartungsaufgaben vor dem Upgrade mit dem Namen als Parameter an.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td>
   <td>ACTION</td>
   <td>Gibt den letzten Ausführungsstatus der Wartungsaufgabe vor dem Upgrade mit dem Namen als Parameter an.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td>
   <td>ACTION</td>
   <td><p>Führt alle Konsistenzprüfungen vor der Aktualisierung aus und speichert ihren Status in einer Datei mit dem Namen <code>preUpgradeHCStatus.properties</code> , der sich im Sling-Startpfad befindet. Wenn die Variable <code>shutDownOnSuccess</code> -Parameter auf <code>true</code>, wird die AEM-Instanz heruntergefahren, jedoch nur, wenn alle Konsistenzprüfungen vor der Aktualisierung den Status OK aufweisen.</p> <p>Die Eigenschaftendatei wird als Voraussetzung für zukünftige Aktualisierungen verwendet<br /> und der Aktualisierungsprozess angehalten wird, wenn die Konsistenzprüfung vor der Aktualisierung durchgeführt wird<br /> Ausführung fehlgeschlagen. Wenn Sie das Ergebnis der Konsistenzprüfungen <br />vor einem Upgrade ignorieren und das Upgrade trotzdem starten möchten, können Sie die Datei löschen.</p> </td>
  </tr>
  <tr>
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td>
   <td>ACTION</td>
   <td>Listet alle importierten Packages auf, die nicht mehr zufrieden sind, wenn<br /> Aktualisierung auf die angegebene AEM. Die Zielversion AEM muss<br /> als Parameter angegeben.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die MBean-Methoden können wie folgt aufgerufen werden:
>
>* Die JMX-Konsole
>* Jede externe Anwendung, die eine Verbindung zu JMX herstellt
>* cURL
>


## Deaktivieren von benutzerdefinierten Anmeldemodulen {#disable-custom-login-modules}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie ein Upgrade von einer AEM 5-Version durchführen. Für Upgrades älterer AEM 6-Versionen kann der Schritt übersprungen werden.

Die Art und Weise, wie `LoginModules` für die Authentifizierung auf der Repository-Ebene konfiguriert werden, hat sich in Apache Oak entscheidend geändert.

In AEM-Versionen mit CRX2 wurde die Konfiguration in der Datei `repository.xml` platziert. Ab AEM 6 erfolgt sie über die Web-Konsole im Dienst „Apache Felix JAAS Configuration Factory“.

Daher müssen die vorhandenen Konfigurationen deaktiviert und für Apache Oak nach dem Upgrade erneut erstellt werden.

So deaktivieren Sie die benutzerdefinierten Module, die in der JAAS-Konfiguration von `repository.xml`, müssen Sie die Konfiguration so bearbeiten, dass die Standardkonfiguration `LoginModule`, wie im folgenden Beispiel:

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Authentifizierung mit dem externen Anmeldemodul](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>Ein Beispiel der `LoginModule`-Konfiguration in AEM 6 finden Sie im Abschnitt [Konfigurieren von LDAP mit AEM 6](/help/sites-administering/ldap-config.md).

## Entfernen von Updates aus dem /install-Verzeichnis {#remove-updates-install-directory}

>[!NOTE]
>
>Entfernen Sie nur Pakete aus dem Verzeichnis crx-quickstart/install , nachdem Sie die AEM-Instanz heruntergefahren haben. Dieser Schritt ist einer der letzten Schritte vor dem Beginn des Aktualisierungsverfahrens.

Entfernen Sie alle Service Packs, Feature Packs oder Hotfixes, die über das `crx-quickstart/install` im lokalen Dateisystem. Dadurch wird verhindert, dass alte Hotfixes und Service Packs nach Abschluss der Aktualisierung versehentlich zusätzlich zur neuen AEM installiert werden.

## Beenden aller Cold-Standby-Instanzen {#stop-tarmk-coldstandby-instance}

Wenn Sie TarMK Cold Standby verwenden, beenden Sie alle Cold-Standby-Instanzen. Dies garantiert eine effiziente Möglichkeit, bei Problemen im Upgrade wieder online zu gehen. Nach erfolgreichem Abschluss des Upgrades müssen die Cold-Standby-Instanzen von den aktualisierten primären Instanzen neu erstellt werden.

## Deaktivieren von benutzerdefinierten geplanten Aufträgen {#disable-custom-scheduled-jobs}

Deaktivieren Sie alle geplanten OSGi-Aufträge, die im Anwendungscode enthalten sind.

## Durchführen der Offline-Revisionsbereinigung {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Dieser Schritt ist nur für TarMK-Installationen erforderlich.

Bei Verwendung von TarMK sollten Sie die Offline-Revisionsbereinigung vor der Aktualisierung ausführen. Auf diese Weise werden der Schritt zur Repository-Migration und die nachfolgenden Aktualisierungsaufgaben viel schneller ausgeführt und es wird sichergestellt, dass die Online-Revisionsbereinigung nach Abschluss der Aktualisierung erfolgreich ausgeführt werden kann. Informationen zum Ausführen der Offline-Revisionsbereinigung finden Sie unter [Durchführen der Offline-Revisionsbereinigung](/help/sites-deploying/storage-elements-in-aem-6.md#performing-offline-revision-cleanup).

## Durchführen der Datenspeicherbereinigung {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Dieser Schritt ist nur für Instanzen erforderlich, die crx3 ausführen

Nachdem Sie die Revisionsbereinigung auf CRX3-Instanzen ausgeführt haben, sollten Sie die Datenspeicherbereinigung ausführen, um alle nicht referenzierten Blobs im Datenspeicher zu entfernen. Anweisungen finden Sie in der Dokumentation unter [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md).

## Upgrade des Datenbankschemas bei Bedarf {#upgrade-the-database-schema-if-needed}

Normalerweise übernimmt der zugrunde liegende Apache Oak-Stapel, der AEM für die Persistenz verwendet, bei Bedarf die Aktualisierung des Datenbankschemas.

Es kann jedoch vorkommen, dass das Schema nicht automatisch aktualisiert werden kann. Bei solchen Fällen handelt es sich größtenteils um Sicherheitsumgebungen, in denen die Datenbank unter einem Benutzer mit eingeschränkten Berechtigungen ausgeführt wird. Wenn eine solche Situation eintritt, verwendet AEM weiterhin das alte Schema.

Um zu verhindern, dass ein solches Szenario eintritt, aktualisieren Sie das Schema wie folgt:

1. Beenden Sie die AEM Instanz, die aktualisiert werden muss.
1. Führen Sie ein Upgrade für das Datenbankschema durch. Lesen Sie die Dokumentation für Ihren Datenbanktyp , um zu sehen, welche Tools zum Erzielen des Ergebnisses erforderlich sind.

   Weitere Informationen dazu, wie Oak mit Schema-Upgrades umgeht, finden Sie auf [dieser Seite der Apache-Website](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. Fahren Sie mit dem Upgrade von AEM fort.

## Löschen von Benutzern, die das Upgrade behindern könnten {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>Diese Wartungsaufgabe vor dem Upgrade ist nur erforderlich, wenn:
>
>* Sie führen ein Upgrade von AEM-Versionen durch, die älter als AEM 6.3 sind
>* Während des Upgrades werden alle unten aufgeführten Fehler angezeigt.
>


Es gibt Ausnahmefälle, in denen Dienstbenutzer in einer älteren AEM-Version landen, die fälschlicherweise als normale Benutzer getaggt wurde.

Wenn eine solche Situation eintritt, schlägt das Upgrade mit einer Meldung wie der folgenden fehl:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Um dieses Problem zu umgehen, gehen Sie folgendermaßen vor:

1. Trennen der Instanz vom Produktions-Traffic
1. Erstellen Sie eine Sicherungskopie von einem oder mehreren Benutzern, die das Problem verursachen. Sie können diese Aufgabe über Package Manager durchführen. Weitere Informationen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).
1. Löschen Sie einen oder mehrere Benutzer, die das Problem verursachen. Nachfolgend finden Sie eine Liste der Benutzer, die unter diese Kategorie fallen können:

   1. `dynamic-media-replication`
   1. `communities-ugc-writer`
   1. `communities-utility-reader`
   1. `communities-user-admin`
   1. `oauthservice`
   1. `sling-scripting`

## Rotieren von Protokolldateien {#rotate-log-files}

Adobe empfiehlt, die aktuellen Protokolldateien zu archivieren, bevor Sie mit der Aktualisierung beginnen. Auf diese Weise können Sie Ihre Protokolldateien während und nach der Aktualisierung einfacher überwachen und scannen, um eventuelle Probleme zu erkennen und zu beheben.
