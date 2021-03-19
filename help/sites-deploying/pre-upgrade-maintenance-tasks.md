---
title: Wartungsaufgaben vor einer Aktualisierung
seo-title: Wartungsaufgaben vor einer Aktualisierung
description: Erfahren Sie mehr über die Aufgaben im Vorfeld der AEM-Aktualisierung.
seo-description: Erfahren Sie mehr über die Aufgaben im Vorfeld der AEM-Aktualisierung.
uuid: 5da1cfc7-8a10-47b1-aafb-2cd112e3f818
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 291c91e5-65ff-473d-ac11-3da480239e76
docset: aem65
feature: Aktualisieren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2159'
ht-degree: 79%

---


# Wartungsaufgaben vor einer Aktualisierung{#pre-upgrade-maintenance-tasks}

Bevor Sie mit der Aktualisierung beginnen, ist es wichtig, die folgenden Wartungsaufgaben durchzuführen, damit das System bereit ist und zurückgesetzt werden kann, falls Probleme auftreten:

* [Überprüfung auf ausreichenden Festplattenspeicher](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Vollständige Sicherung von AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Sicherung von Änderungen unter /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Erstellen der quickstart.properties-Datei](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Konfigurieren von Workflow- und Auditprotokoll-Löschung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installieren, Konfigurieren und Ausführen der Aufgaben vor der Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Deaktivieren von benutzerdefinierten Anmeldemodulen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Entfernen von Updates aus dem /install-Verzeichnis](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Beenden aller Cold-Standby-Instanzen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Deaktivieren von benutzerdefinierten geplanten Aufträgen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs) 
* [Durchführen der Offline-Revisionsbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup) 
* [Durchführen der Datenspeicherbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection) 
* [Aktualisieren Sie bei Bedarf das Schema Database.](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Benutzer löschen, die die Aktualisierung behindern könnten](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)

* [Rotieren von Protokolldateien](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files) 

## Überprüfung auf ausreichenden Festplattenspeicher {#ensure-sufficient-disk-space}

Wenn Sie die Aktualisierung durchführen, ist zusätzlich zur Aktualisierung von Inhalt und Code auch eine Migration des Repositorys erforderlich. Bei der Migration wird eine Kopie des Repositorys im Segment-TAR-Format erstellt. Daher benötigen Sie ausreichend Festplattenspeicher, um eine zweite (möglicherweise größere) Version des Repositorys zu speichern.

## Vollständige Sicherung von AEM  {#fully-back-up-aem}

Bevor Sie mit der Aktualisierung beginnen, sollten Sie eine vollständige Sicherungskopie von AEM erstellen. Erstellen Sie Sicherungskopien des Repositorys, der Anwendungsinstallation, des Datenspeichers und der Mongo-Instanzen, falls zutreffend. Weitere Informationen zum Sichern und Wiederherstellen einer AEM-Instanz finden Sie unter[ Sicherung und Wiederherstellung](/help/sites-administering/backup-and-restore.md).

## Sicherung von Änderungen unter /etc  {#backup-changes-etc}

Der Aktualisierungsprozess bietet eine gute Funktion zum Verwalten und Zusammenführen vorhandener Inhalte und Konfigurationen unter den Pfaden `/apps` und `/libs` im Repository. Für Änderungen am `/etc`-Pfad, einschließlich Context Hub-Konfigurationen, ist es häufig erforderlich, diese Änderungen nach der Aktualisierung erneut anzuwenden. Während die Aktualisierung eine Sicherungskopie aller Änderungen erstellt, die unter `/var` nicht zusammengeführt werden können, empfehlen wir, diese Änderungen manuell zu sichern, bevor die Aktualisierung beginnt.

## Erstellen der quickstart.properties-Datei {#generate-quickstart-properties}

Wenn Sie AEM von einer JAR-Datei aus starten, wird eine `quickstart.properties`-Datei unter `crx-quickstart/conf` erstellt. Falls AEM bisher nur mit dem Startskript gestartet wurde, ist diese Datei nicht vorhanden und die Aktualisierung schlägt fehl. Überprüfen Sie daher, dass diese Datei vorhanden ist, und starten Sie AEM andernfalls von der JAR-Datei aus neu.

## Konfigurieren von Workflow- und Auditprotokoll-Löschung  {#configure-wf-audit-purging}

Für die Aufgaben `WorkflowPurgeTask` und `com.day.cq.audit.impl.AuditLogMaintenanceTask` sind separate OSGi-Konfigurationen erforderlich, sonst werden diese nicht ausgeführt. Falls diese Aufgaben beim Ausführen von Aufgaben vor der Aktualisierung fehlschlagen, sind die Ursache dafür wahrscheinlich fehlende Konfigurationen. Daher müssen Sie die OSGi-Konfigurationen für diese Aufgaben hinzufügen oder diese Aufgaben vollständig aus der Liste der Optimierungsaufgaben vor der Aktualisierung löschen, falls Sie diese nicht ausführen möchten. Dokumentation zum Konfigurieren von Workflow-Löschaufgaben finden Sie unter [Verwalten von Workflow-Instanzen](/help/sites-administering/workflows-administering.md). Informationen zur Konfiguration von Wartungsaufgaben für Auditprotokolle finden Sie unter [Wartung von Auditprotokollen in AEM 6](/help/sites-administering/operations-audit-log.md).

Informationen zum Workflow und zum Löschen von Auditprotokollen in CQ 5.6 und AEM 6.0 finden Sie unter [Löschen von Workflow- und Auditknoten](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).

## Installieren, Konfigurieren und Ausführen der Aufgaben vor der Aktualisierung  {#install-configure-run-pre-upgrade-tasks}

Da AEM ein hohes Maß an Anpassung erlaubt, gibt es in der Regel keine einheitliche Vorgehensweise für die Durchführung von Aktualisierungen. Es ist deshalb schwierig, ein standardisiertes Verfahren für Aktualisierungen zu entwickeln.

In vorherigen Versionen war es zudem problematisch, gestoppte oder fehlgeschlagene AEM-Aktualisierungen wieder sicher fortzusetzen. Dies führte zu Situationen, in denen die Aktualisierung komplett neu gestartet werden musste oder defekte Aktualisierungen durchgeführt wurden, ohne dass Warnungen ausgelöst wurden.

Um diese Probleme zu beheben, hat Adobe einige Verbesserungen am Aktualisierungsprozess vorgenommen, sodass dieser jetzt ausfallsicherer und benutzerfreundlicher ist. Wartungsaufgaben vor einer Aktualisierung, die bisher manuell durchgeführt werden mussten, wurden optimiert und automatisiert. Darüber hinaus wurden Berichte hinzugefügt, die nach der Aktualisierung erstellt werden, sodass der Vorgang umfassend überprüft werden kann und Probleme einfach identifizierbar sind.

Die Wartungsaufgaben vor einer Aktualisierung sind derzeit auf verschiedene Benutzeroberflächen verteilt und werden teilweise oder vollständig manuell durchgeführt. Durch die in AEM 6.3 eingeführte Optimierungsfunktionen für die Wartungsaufgaben im Vorfeld der Aktualisierung können diese Aufgaben einheitlich ausgelöst und ihre Ergebnisse bei Bedarf überprüft werden.

Sämtliche Aufgaben, die zum Optimierungsschritt vor der Aktualisierung gehören, sind mit allen Versionen (ab Version 6.0) kompatibel.

### Einrichtung  {#how-to-set-it-up}

In AEM 6.3 und höher ist die Optimierung der Wartungsaufgaben vor einer Aktualisierung Teil der quickstart-Datei. Bei einer Aktualisierung von älteren AEM 6-Versionen ist sie über separate Pakete verfügbar, die Sie von Package Manager herunterladen können.

Sie finden die Pakete hier:

* [Bei der Aktualisierung von AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60) 

* [Bei der Aktualisierung von AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61) 

* [Bei der Aktualisierung von AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62) 

### Verwendung {#how-to-use-it}

Die OSGi-Komponente `PreUpgradeTasksMBean` ist mit einer Liste von Wartungsaufgaben vor der Aktualisierung vorkonfiguriert, die gleichzeitig ausgeführt werden können. Sie können die Aufgaben mit den nachfolgenden Schritten konfigurieren:

1. Gehen Sie zur Web-Konsole, indem Sie *https://serveraddress:serverport/system/console/configMgr*

1. Suchen Sie nach **preupgradetasks** und klicken Sie auf die erste übereinstimmende Komponente. Der vollständige Name der Komponenten lautet `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`.

1. Ändern Sie die Liste der auszuführenden Wartungsaufgaben wie unten gezeigt:

   ![1487758925984](assets/1487758925984.png)

Die Aufgabenliste unterscheidet sich je nach dem verwendeten Ausführungsmodus zum Starten der Instanz. Nachfolgend finden Sie eine Beschreibung der Ausführungsmodi für die einzelnen Wartungsaufgaben.

<table>
 <tbody>
  <tr>
   <td><strong>Aufgabe</strong></td>
   <td><strong>Ausführungsmodus</strong></td>
   <td><strong>Hinweise</strong></td>
  </tr>
  <tr>
   <td><code>TarIndexMergeTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>DataStoreGarbageCollectionTask</code></td>
   <td>crx2</td>
   <td>Mark und Sweep werden ausgeführt. Lassen Sie bei freigegebenen Datenspeichern diesen Schritt aus und gehen Sie<br /> manuell vor oder bereiten Sie die Instanzen vor der Ausführung richtig vor.</td>
  </tr>
  <tr>
   <td><code>ConsistencyCheckTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>WorkflowPurgeTask</code></td>
   <td>crx2/crx3</td>
   <td>Vor der Ausführung muss die Adobe Granite Workflow-Bereinigung in OSGi konfiguriert werden.</td>
  </tr>
  <tr>
   <td><code>GenerateBundlesListFileTask</code></td>
   <td>crx2/crx3</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>RevisionCleanupTask</code></td>
   <td>crx3</td>
   <td>Für TarMK-Instanzen auf AEM 6.0 bis 6.2 führen Sie stattdessen die Offline-Revisionsbereinigung durch.</td>
  </tr>
  <tr>
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td>
   <td>crx3</td>
   <td>Vor der Ausführung muss der Auditprotokoll-Bereinigungsplaner in OSGi konfiguriert werden.</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Die Aufgabe `DataStoreGarbageCollectionTask` ruft einen Vorgang zur Datenspeicherbereinigung mit der Mark- und Sweep-Phase auf, falls sie verwendet wird. Bei Bereitstellungen mit einem freigegebenen Datenspeicher muss dieser entweder neu konfiguriert oder die Instanz ordnungsgemäß vorbereitet werden, um das Löschen von Elementen, auf die andere Instanzen verweisen, zu vermeiden. Hierzu muss die Mark-Phase möglicherweise auf allen Instanzen manuell ausgeführt werden, bevor diese Aufgabe vor einer Aktualisierung ausgelöst wird.

### Standardkonfiguration der Konsistenzprüfungen vor einer Aktualisierung  {#default-configuration-of-the-pre-upgrade-health-checks}

Die OSGi-Komponente `PreUpgradeTasksMBeanImpl` umfasst eine vorkonfigurierte Liste von Tags für Konsistenzprüfungen vor einer Aktualisierung, die ausgeführt werden sollen, wenn die Methode `runAllPreUpgradeHealthChecks` aufgerufen wird:

* **system** – Das von den Wartungs-Konsistenzprüfungen von Granite verwendete Tag.

* **pre-upgrade** – Ein benutzerdefiniertes Tag, das Sie allen Konsistenzprüfungen hinzufügen können, deren Ausführung vor einer Aktualisierung festgelegt werden können.

Die Liste kann bearbeitet werden. Mit den Plus- **(+)** und Minus-Schaltflächen **(-)** neben den Tags können Sie weitere benutzerdefinierte Tags hinzufügen oder die Standard-Tags entfernen.

**MBean-Methoden** 

Der Zugriff auf die Funktion für verwaltete Beans ist über die [JMX-Konsole](/help/sites-administering/jmx-console.md) möglich.

Sie können wie folgt auf die MBeans zugreifen:

1. Wechseln Sie zur JMX-Konsole unter *https://serveraddress:serverport/system/console/jmx*
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
   <td>Zeigt die Namensliste der verfügbaren Wartungsaufgaben vor der Aktualisierung an.</td>
  </tr>
  <tr>
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td>
   <td>INFO</td>
   <td>Zeigt die Namensliste Liste der Konsistenzprüfungen vor der Aktualisierung an.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeTasks()</code></td>
   <td>AKTION</td>
   <td>Führt alle in der Liste genannten Wartungsaufgaben vor der Aktualisierung aus.</td>
  </tr>
  <tr>
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td>
   <td>AKTION</td>
   <td>Führt die Wartungsaufgabe vor der Aktualisierung mit dem als Parameter angegebenen Namen aus.</td>
  </tr>
  <tr>
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Überprüft, ob die <code>runAllPreUpgradeTasksmaintenance</code>-Aufgabe derzeit ausgeführt wird.</td>
  </tr>
  <tr>
   <td><code>getAnyPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Überprüft, ob gerade Wartungsaufgaben vor der Aktualisierung ausgeführt werden und<br /> gibt ein Array mit den Namen der gerade ausgeführten Aufgaben aus.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td>
   <td>AKTION</td>
   <td>Gibt die genaue Ausführungszeit der Wartungsaufgaben vor der Aktualisierung mit dem Namen als Parameter an.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td>
   <td>AKTION</td>
   <td>Gibt den letzten Ausführungsstatus der Wartungsaufgabe vor der Aktualisierung mit dem Namen als Parameter an.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td>
   <td>AKTION</td>
   <td><p>Führt alle Gesundheitsüberprüfungen vor der Aktualisierung aus und speichert ihren Status in einer Datei mit dem Namen <code>preUpgradeHCStatus.properties</code>, die sich im sling-Homepad befindet. Wenn der Parameter <code>shutDownOnSuccess</code> auf <code>true</code> eingestellt ist, wird die AEM Instanz heruntergefahren, jedoch nur, wenn alle Statusprüfungen vor der Aktualisierung den Status OK haben.</p> <p>Die Eigenschaftendatei wird als Vorbedingung für zukünftige Aktualisierungen verwendet<br /> und der Aktualisierungsvorgang wird angehalten, wenn die Konsistenzprüfungen vor einer Aktualisierung<br /> fehlgeschlagen sind. Wenn Sie das Ergebnis der Konsistenzprüfungen <br />vor einer Aktualisierung ignorieren und die Aktualisierung trotzdem starten möchten, können Sie die Datei löschen.</p> </td>
  </tr>
  <tr>
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td>
   <td>AKTION</td>
   <td>Listet alle importierten Pakete auf, die nach der<br /> Aktualisierung auf eine bestimmte AEM-Version nicht mehr kompatibel sind. Die AEM-Zielversion muss<br /> als Parameter angegeben werden.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die MBean-Methoden können über folgende Komponenten aufgerufen werden:
>
>* Die JMX-Konsole
>* Eine beliebige externe Anwendung, die eine Verbindung mit JMX herstellt
>* cURL

>



## Deaktivieren von benutzerdefinierten Anmeldemodulen  {#disable-custom-login-modules}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine Aktualisierung von einer AEM 5-Version durchführen. Für Aktualisierungen älterer AEM 6-Versionen kann der Schritt übersprungen werden.

Die Art und Weise, wie `LoginModules` für die Authentifizierung auf der Repository-Ebene konfiguriert werden, hat sich in Apache Oak entscheidend geändert.

In AEM-Versionen mit CRX2 wurde die Konfiguration in der Datei `repository.xml` platziert. Ab AEM 6 erfolgt sie über die Web-Konsole im Dienst „Apache Felix JAAS Configuration Factory“.

Daher müssen die vorhandenen Konfigurationen deaktiviert und für Apache Oak nach der Aktualisierung erneut erstellt werden.

Zum Deaktivieren der in der JAAS-Konfiguration von `repository.xml` definierten benutzerdefinierten Module müssen Sie die Konfiguration so ändern, dass das standardmäßige `LoginModule` verwendet wird, wie dies in diesem Beispiel der Fall ist:

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
>Entfernen Sie Pakete aus dem Verzeichnis „crx-quickstart/install“ erst, NACHDEM Sie die AEM-Instanz heruntergefahren haben. Dies ist einer der letzten Schritte vor dem Start des Aktualisierungsverfahrens.

Entfernen Sie alle Service Packs, Feature Packs oder Hotfixes, die im lokalen Dateisystem im Verzeichnis `crx-quickstart/install` bereitgestellt sind. Dadurch wird die unbeabsichtigte Installation alter Hotfixes und Service Packs auf der neuen AEM-Version nach der Aktualisierung verhindert.

## Beenden aller Cold-Standby-Instanzen  {#stop-tarmk-coldstandby-instance}

Falls Sie TarMK Cold Standby verwenden, stoppen Sie alle Cold-Standby-Instanzen, falls erforderlich. Dies stellt sicher, dass das System problemlos in den Online-Modus wechseln kann, falls bei der Aktualisierung Probleme aufgetreten sind. Nach der erfolgreichen Aktualisierung müssen die Cold-Standby-Instanzen auf Basis der aktualisierten primären Instanzen neu erstellt werden.

## Deaktivieren von benutzerdefinierten geplanten Aufträgen  {#disable-custom-scheduled-jobs}

Deaktivieren Sie in OSGi geplante Aufträge, die im Anwendungscode enthalten sind.

## Durchführen der Offline-Revisionsbereinigung  {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Dieser Schritt ist nur für TarMK-Installationen erforderlich.

Falls Sie TarMK verwenden, sollten Sie vor der Aktualisierung eine Offline-Revisionsbereinigung durchführen. Dadurch werden die Repository-Migration und die nachfolgenden Aktualisierungsaufgaben viel schneller ausgeführt. Dies wiederum unterstützt die erfolgreiche Online-Revisionsbereinigung nach der Aktualisierung. Weitere Informationen zum Durchführen einer Offline-Revisionsbereinigung finden Sie unter [Durchführen einer Offline-Revisionsbereinigung](/help/sites-deploying/storage-elements-in-aem-6.md#performing-offline-revision-cleanup).

## Durchführen der Datenspeicherbereinigung  {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Dieser Schritt ist nur für Instanzen erforderlich, die crx3 ausführen.

Nach der Revisionsbereinigung auf CRX3-Instanzen sollten Sie die Datenspeicherbereinigung ausführen, um nicht referenzierte BLOB-Objekte aus dem Datenspeicher zu löschen. Eine Anleitung finden Sie in der Dokumentation zur [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md).

## Aktualisieren Sie bei Bedarf das Database Schema.{#upgrade-the-database-schema-if-needed}

Normalerweise übernimmt der zugrunde liegende Apache Oak-Stapel, der AEM für Persistenz verwendet, bei Bedarf die Aktualisierung des Schemas.

Es kann jedoch vorkommen, dass das Schema nicht automatisch aktualisiert werden kann. Dies sind meist Umgebung mit hoher Sicherheit, bei denen die Datenbank unter einem Benutzer mit sehr begrenzten Berechtigungen ausgeführt wird. In diesem Fall wird AEM weiterhin das alte Schema verwenden.

Um dies zu verhindern, müssen Sie das Schema wie folgt aktualisieren:

1. Fahren Sie die AEM Instanz herunter, die aktualisiert werden muss.
1. Aktualisieren Sie das Schema der Datenbank. Bitte lesen Sie die Dokumentation für Ihren Datenbanktyp, um zu sehen, welche Werkzeuge Sie dazu benötigen.

   Weitere Informationen dazu, wie Oak mit Schema-Upgrades umgeht, finden Sie auf dieser Seite auf der Apache-Website](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).[

1. Fahren Sie mit der AEM fort.

## Löschen Sie Benutzer, die die Aktualisierung {#delete-users-that-might-hinder-the-upgrade} behindern könnten.

>[!NOTE]
>
>Diese Aufgabe zur Wartung vor der Aktualisierung ist nur erforderlich, wenn:
>
>* Sie aktualisieren von AEM älteren Versionen als AEM 6.3
>* Während der Aktualisierung werden die folgenden Fehler angezeigt.

>



Es gibt Ausnahmefälle, in denen Dienstbenutzer in älteren AEM Versionen falsch getaggt werden können.

In diesem Fall schlägt die Aktualisierung fehl mit einer Meldung wie der folgenden:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Um dieses Problem zu umgehen, gehen Sie wie folgt vor:

1. Die Instanz vom Produktions-Traffic trennen
1. Erstellen Sie eine Sicherung der Benutzer, die das Problem verursachen. Sie können dies über Package Manager tun. Weitere Informationen finden Sie unter [So arbeiten Sie mit Paketen.](/help/sites-administering/package-manager.md)
1. Löschen Sie die Benutzer, die das Problem verursachen. Nachfolgend finden Sie eine Liste von Benutzern, die unter diese Kategorie fallen könnten:

   1. `dynamic-media-replication`
   1. `communities-ugc-writer`
   1. `communities-utility-reader`
   1. `communities-user-admin`
   1. `oauthservice`
   1. `sling-scripting`

## Rotieren von Protokolldateien {#rotate-log-files}

Bevor Sie mit der Aktualisierung beginnen, empfiehlt es sich, die aktuellen Protokolldateien zu archivieren. Dadurch können Sie Protokolldateien vor und nach der Aktualisierung einfacher überwachen und scannen, um auftretende Probleme zu identifizieren.
