---
title: Überwachen von Serverressourcen mit der JMX-Konsole
seo-title: Überwachen von Serverressourcen mit der JMX-Konsole
description: Erfahren Sie, wie Sie mit der JMX-Konsole Serverressourcen überwachen.
seo-description: Erfahren Sie, wie Sie mit der JMX-Konsole Serverressourcen überwachen.
uuid: 0a28aafe-61b2-472b-8f8f-2cd6540cbfee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 873ce073-0055-4e1b-b3c6-ae7967700894
docset: aem65
translation-type: tm+mt
source-git-commit: 97c93a95cd7fe63b306d80fe127388a209b727c7
workflow-type: tm+mt
source-wordcount: '4974'
ht-degree: 70%

---


# Überwachen von Serverressourcen mit der JMX-Konsole{#monitoring-server-resources-using-the-jmx-console}

Mit der JMX-Konsole können Sie Dienste auf dem CRX-Server überwachen und verwalten. Die folgenden Abschnitte fassen die Attribute und Vorgänge zusammen, die über das JMX-Framework bereitgestellt werden.

Weitere Informationen zur Nutzung der Konsolensteuerung finden Sie unter [Verwenden der JMX-Konsole](#using-the-jmx-console). Hintergrundinformationen zu JMX finden Sie auf der Seite [Java Management Extensions (JMX) Technology](https://www.oracle.com/technetwork/java/javase/tech/javamanagement-140525.html) auf der Oracle-Website.

Weitere Informationen zur Erstellung von MBeans für die Verwaltung Ihrer Dienste über die JMX-Konsole finden Sie unter [Integrieren von Diensten mit der JMX-Konsole](/help/sites-developing/jmx-integration.md).

## Workflow-Wartung {#workflow-maintenance}

Vorgänge zum Verwalten von ausgeführten, abgeschlossenen, statischen und fehlgeschlagenen Workflow-Instanzen.

* Domäne: com.adobe.granite.workflow
* Typ: Wartung

>[!NOTE]
>
>In der [Workflow-Konsole](/help/sites-administering/workflows-administering.md) finden Sie zusätzliche Workflow-Verwaltungstools und Beschreibungen von möglichen Status der Workflow-Instanzen.

### Betrieb {#operations}

**** listRunningWorkflowsPerModelListet die Anzahl der Workflow-Instanzen auf, die für jedes Workflow-Modell ausgeführt werden.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit Count- und ModelId-Spalten.

**** listCompletedWorkflowsPerModelListet die Anzahl der abgeschlossenen Workflow-Instanzen für jedes Workflow-Modell auf.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit Count- und ModelId-Spalten.

**** returnWorkflowQueueInfoListet Informationen zu verarbeiteten Workflow-Elementen auf, die zur Verarbeitung in die Warteschlange gestellt wurden.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den folgenden Spalten:

   * Aufträge
   * Queue Name
   * Active Jobs
   * Average Processing Time
   * Average Waiting Time
   * Cancelled Jobs
   * Failed Jobs
   * Finished Jobs
   * Processed Jobs
   * Queued Jobs

**** returnWorkflowJobTopicInfoListet Verarbeitungsinformationen für Workflow-Aufträge nach Thema auf.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den folgenden Spalten:

   * Topic Name
   * Durchschnittliche Verarbeitungszeit
   * Durchschnittliche Wartezeit
   * Abgebrochene Aufträge
   * Fehlgeschlagene Aufträge
   * Fertiggestellte Aufträge
   * Verarbeitete Aufträge

**returnFailureWorkflowCount** Zeigt die Anzahl der Workflow-Instanzen an, die fehlgeschlagen sind. Sie können ein Workflow-Modell für die Abfrage angeben oder Informationen für alle Workflow-Modelle abrufen.

* Argumente:

   * model: Die ID des Modells für die Abfrage. Um die Anzahl an fehlgeschlagenen Workflow-Instanzen für alle Workflow-Modelle anzuzeigen, legen Sie keinen Wert fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an fehlgeschlagenen Workflow-Instanzen.

**returnFailureWorkflowCountPerModelZeigt die Anzahl der Workflow-Instanzen an, die für jedes Workflow-Modell fehlgeschlagen sind.** 

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit Count- und ModelId-Spalten.

**Workflow-Instanzen** beenden, die fehlgeschlagen sind. Sie können alle fehlgeschlagenen Instanzen beenden oder nur die fehlgeschlagenen Instanzen für ein bestimmtes Modell. Optional können Sie die Instanzen neu starten, nachdem sie beendet wurden. Sie können den Vorgang auch testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Restart the instance: (optional) Legen Sie den Wert `true` fest, um die Instanzen neu zu starten, nachdem sie beendet wurden. Beim Standardwert `false` werden beendete Workflow-Instanzen nicht neu gestartet.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.
   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die fehlgeschlagenen Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: Tabellendaten zu den beendeten Instanzen mit den folgenden Spalten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**** retryFailureWorkItemsVersuche, fehlgeschlagene Arbeitselementschritte auszuführen. Sie können alle fehlgeschlagenen Arbeitselemente erneut ausführen lassen oder nur die fehlgeschlagenen Arbeitselemente für ein bestimmtes Workflow-Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.
   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die fehlgeschlagenen Arbeitselemente aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: Tabellendaten zu den fehlgeschlagenen Arbeitselementen, die erneut ausgeführt werden sollen, mit den folgenden Spalten:

   * Initiator
   * InstanceId
   * modelId
   * Nutzlast
   * StartComment
   * WorkflowTitle

**** PurgeActiveEntfernt aktive Workflow-Instanzen eines bestimmten Alters. Sie können aktive Instanzen für alle Modelle bereinigen oder nur die Instanzen für ein bestimmtes Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Number of days since workflow started: das Alter der zu bereinigenden Workflow-Instanzen in Tagen.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: Tabellendaten zu den aktiven Workflow-Instanzen, die bereinigt werden, mit den folgenden Spalten:

   * Initiator
   * InstanceId
   * modelId
   * Nutzlast
   * StartComment
   * WorkflowTitle

**** countStaleWorkflowsGibt die Anzahl der nicht mehr unterstützten Workflow-Instanzen zurück. Sie können die Anzahl an veralteten Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an veralteten Workflow-Instanzen.

**Workflow-Instanzen** neu startenStaleWorkflowsStartet statische Workflow-Instanzen neu. Sie können alle veralteten Instanzen neu starten oder nur die veralteten Instanzen für ein bestimmtes Modell. Sie können den Vorgang auch testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die veralteten Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: eine Liste der Workflow-Instanzen, die neu gestartet werden.

**fetchModelListListet** alle Workflow-Modelle auf.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten, die die Workflow-Modelle identifizieren, mit den ModelId- und ModelName-Spalten.

**** countRunningWorkflowsGibt die Anzahl der ausgeführten Workflow-Instanzen zurück. Sie können die Anzahl an laufenden Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Modell: (Optional) Die ID des Modells, für das die Anzahl der ausgeführten Instanzen zurückgegeben wird. Um die Anzahl an laufenden Instanzen für alle Workflow-Modelle zurückzugeben, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an laufenden Workflow-Instanzen.

**** countCompletedWorkflowsGibt die Anzahl der abgeschlossenen Workflow-Instanzen zurück. Sie können die Anzahl an abgeschlossenen Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Modell: (Optional) Die ID des Modells, für das die Anzahl der abgeschlossenen Instanzen zurückgegeben wird. Um die Anzahl an abgeschlossenen Instanzen für alle Workflow-Modelle zurückzugeben, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an abgeschlossenen Workflow-Instanzen.

**** purgeCompletedEntfernt Datensätze zu abgeschlossenen Workflows eines bestimmten Alters aus dem Repository. Wenn Sie häufig Workflows verwenden, verringern Sie mit diesem Vorgang regelmäßig die Größe des Repositorys. Sie können abgeschlossene Instanzen für alle Modelle bereinigen oder nur die Instanzen für ein bestimmtes Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Number of days since workflow has been completed: die Anzahl an Tagen, seit denen sich die Workflow-Instanzen im abgeschlossenen Status befinden.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: Tabellendaten zu den abgeschlossenen Workflow-Instanzen, die bereinigt werden, mit den folgenden Spalten:

   * Initiator
   * InstanceId
   * modelId
   * Nutzlast
   * StartComment
   * WorkflowTitle

## Repository {#repository}

Informationen zum CRX-Repository

* Domäne: com.adobe.granite
* Typ: Repository

### Attribute {#attributes}

**** NameDer Name der JCR-Repository-Implementierung. Schreibgeschützt.

**** VersionDie Version der Repository-Implementierung. Schreibgeschützt.

**** HomeDirDer Ordner, in dem sich das Repository befindet. Der standardmäßige Speicherort ist &lt;QuickStart_Jar_Location>/crx-quickstart/repository. Schreibgeschützt.

**** CustomerNameDer Name des Kunden, dem die Softwarelizenz erteilt wird. Schreibgeschützt.

**** LicenseKeyDer eindeutige Lizenzschlüssel für diese Installation des Repositorys. Schreibgeschützt.

**** AvailableDiskSpaceDer für diese Instanz des Repositorys verfügbare Speicherplatz in MB. Schreibgeschützt.

**** MaximumNumberOfOpenFilesDie Anzahl der Dateien, die gleichzeitig geöffnet werden können. Schreibgeschützt.

**** SessionTrackerDer Wert der Systemvariable crx.debug.session. &quot;true&quot;bedeutet eine Debug-Sitzung. false bedeutet eine normale Sitzung. Lese- und Schreibzugriff.

**** DeskriptorenEine Gruppe von Schlüssel/Wert-Paaren, die Repository-Eigenschaften darstellen. Alle Eigenschaften sind schreibgeschützt.

<table>
 <tbody>
  <tr>
   <th>Schlüssel</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>option.node.and.property.with.same.name.supported</td>
   <td>Gibt an, ob ein Knoten und eine Eigenschaft des Knotens denselben Namen haben dürfen. Dabei bedeutet „true“, dass derselbe Name zulässig ist, und „false“, dass derselbe Name nicht zulässig ist. </td>
  </tr>
  <tr>
   <td>identifier.stability</td>
   <td>Gibt die Stabilität von nicht-referenzierbaren Knoten-IDs an. Die folgenden Werte sind möglich:
    <ul>
     <li>identifier.stability.indefinite.duration: Die IDs ändern sich nicht.</li>
     <li>identifier.stability.method.duration: Die IDs können sich zwischen Methodenaufrufen ändern.</li>
     <li>identifier.stability.save.duration: Die IDs ändern sich innerhalb eines Speicher-/Aktualisierungszyklus nicht.</li>
     <li>identifier.stability.session.duration: Die IDs ändern sich während einer Sitzung nicht.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>query.xpath.pos.index</td>
   <td>Gibt an, ob die JCR 1.0 XPath-Abfragesprache unterstützt wird. Dabei bedeutet „true“, dass sie unterstützt wird, und „false“, dass sie nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>crx.repository.systemid</td>
   <td>Die System-ID, wie sie in der Datei system.id festgelegt ist</td>
  </tr>
  <tr>
   <td>option.query.sql.supported</td>
   <td>Gibt an, ob die JCR 1.0 XPath-Abfragesprache unterstützt wird. Dabei bedeutet „true“, dass sie unterstützt wird, und „false“, dass sie nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>jcr.repository.version</td>
   <td>Die Version der Repository-Implementierung</td>
  </tr>
  <tr>
   <td>option.update.primary.node.type.supported</td>
   <td>Gibt an, ob der primäre Knotentyp eines Knotens geändert werden kann. Dabei bedeutet „true“, dass Sie den primären Knotentyp ändern können, und „false“, dass die Änderung nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.node.type.management.supported</td>
   <td>Gibt an, ob die Knotentyp-Verwaltung unterstützt wird. Dabei bedeutet „true“, dass sie unterstützt wird, und „false“, dass sie nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>node.type.management.overrides.supported</td>
   <td>Gibt an, ob Sie die vererbte Eigenschaft oder die Definition des untergeordneten Knotens eines Knotentyps überschreiben können. Dabei bedeutet „true“, dass eine Überschreibung möglich ist, und „false“, dass die Überschreibung nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.observation.supported</td>
   <td>Der Wert „true“ bedeutet, dass die asynchrone Überwachung von Repository-Änderungen unterstützt wird. Bei unterstützter asynchroner Überwachung können Anwendungen Benachrichtigungen zu jeder Änderung sofort erhalten und darauf reagieren.</td>
  </tr>
  <tr>
   <td>query.jcrscore</td>
   <td><p>"true"bedeutet, dass die pseudo-Eigenschaft "jcr:score"in XPath- und SQL-Abfragen verfügbar ist, die die Funktion jcrfn:contains (in XPath) oder CONTAINS (in SQL) enthalten, um eine Volltextsuche durchzuführen.</p> </td>
  </tr>
  <tr>
   <td>option.simple.versioning.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die einfache Versionierung unterstützt. Bei der einfachen Versionierung bewahrt das Repository eine sequenzielle Serie an Versionen eines Knotens auf.</td>
  </tr>
  <tr>
   <td>option.workspace.management.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Erstellen und Löschen von Workspaces mit APIs unterstützt.</td>
  </tr>
  <tr>
   <td>option.update.mixin.node.types.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Hinzufügen und Entfernen von Mixin-Knotentypen eines vorhandenen Knotens unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.primary.item.name.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository zulässt, dass Knotendefinitionen ein primäres Element als untergeordnetes Element enthalten. Über die API kann auf das primäre Element zugegriffen werden, ohne den Namen des Elements zu kennen.</td>
  </tr>
  <tr>
   <td>level.2.supported</td>
   <td>Der Wert „true“ bedeutet, dass sowohl LEVEL_1_SUPPORTED als auch OPTION_XML_IMPORT_SUPPORTED wahr sind.</td>
  </tr>
  <tr>
   <td>write.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository über die API Schreibzugriff bietet. Der Wert „false“ bedeutet, dass nur schreibgeschützter Zugriff möglich ist.</td>
  </tr>
  <tr>
   <td>node.type.management.update.in.use.supported</td>
   <td>Der Wert „true“ bedeutet, dass Sie die Knotendefinitionen ändern können, die von vorhandenen Knoten genutzt werden.</td>
  </tr>
  <tr>
   <td>jcr.specification.version</td>
   <td>Die Version der JCR-Spezifikation, die das Repository implementiert</td>
  </tr>
  <tr>
   <td>option.journaled.observation.supported</td>
   <td>Der Wert „true“ bedeutet, dass Anwendungen die Journaling-Überwachung des Repositorys vornehmen dürfen. Bei der Journaling-Überwachung können Änderungsbenachrichtigungen für einen bestimmten Zeitraum abgerufen werden. </td>
  </tr>
  <tr>
   <td>query.languages</td>
   <td>Die vom Repository unterstützten Abfragesprachen. Kein Wert bedeutet, dass keine Abfragen unterstützt werden.</td>
  </tr>
  <tr>
   <td>option.xml.export.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Exportieren von Knoten als XML-Code unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.multiple.binary.properties.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Registrieren von Knotentypen unterstützt, die mehrere binäre Eigenschaften aufweisen. Der Wert „false“ bedeutet, dass eine einzige binäre Eigenschaft für einen Knotentyp unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.access.control.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die Zugangssteuerung unterstützt, mit der Sie die Benutzerrechte für den Zugriff auf den Knoten einrichten und festlegen können.</td>
  </tr>
  <tr>
   <td>option.baselines.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository sowohl Konfigurationen als auch Baselines unterstützt.</td>
  </tr>
  <tr>
   <td>option.shareable.nodes.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Erstellen von gemeinsam nutzbaren Knoten unterstützt.</td>
  </tr>
  <tr>
   <td>crx.cluster.id</td>
   <td>Die ID des Repository-Clusters</td>
  </tr>
  <tr>
   <td>query.stored.queries.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository gespeicherte Abfragen unterstützt.</td>
  </tr>
  <tr>
   <td>query.full.text.search.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die Volltextsuche unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.inheritance</td>
   <td><p>Gibt den Grad der Unterstützung von Knotentypen-Vererbung durch das Repository an. Die folgenden Werte sind möglich:</p> <p>node.type.management.inheritance.minimal: Es können nur die primären Knotentypen registriert werden, die nur nt:base als Supertyp aufweisen. Die Registrierung von Mixin-Knotentypen ist auf die ohne Supertyp beschränkt.</p> <p>node.type.management.inreferance.single: Die Registrierung primärer Node-Typen ist auf solche mit einem Supertyp beschränkt. Die Registrierung von Mixin-Knotentypen ist auf die mit höchstens einem Supertyp beschränkt.</p> <p><br /> node.type.management.inreferance.multiple: Primär-Node-Typen können mit einem oder mehreren Supertypen registriert werden. Es können Mixin-Knotentypen mit null oder mehr Supertypen registriert werden.</p> </td>
  </tr>
  <tr>
   <td>crx.cluster.preferredMaster</td>
   <td>Der Wert „true“ bedeutet, dass dieser Cluster-Knoten der bevorzugte Master des Clusters ist.</td>
  </tr>
  <tr>
   <td>option.transactions.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Transaktionen unterstützt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor.url</td>
   <td>Die URL des Repository-Anbieters</td>
  </tr>
  <tr>
   <td>node.type.management.value.constraints.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Wertebeschränkungen für Knoteneigenschaften unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.property.types</td>
   <td>ein Array von javax.jcr.PropertyType-Konstanten, die die Eigenschaftstypen darstellen, die ein registrierter Knotentyp angeben kann. Ein Array der Länge null gibt an, dass registrierte Knotentypen keine Eigenschaftsdefinitionen festlegen können. Eigenschaftstypen sind STRING, URI, BOOLEAN, LONG, DUBLETTE, DECIMAL, BINARY, DATE, NAME, PFAD, WETTBEWERBSREFERENZ, REFERENZ und UNDEFINED (sofern unterstützt)</td>
  </tr>
  <tr>
   <td>node.type.management.orderable.child.nodes.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die Beibehaltung der Reihenfolge der untergeordneten Knoten unterstützt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor</td>
   <td>Der Name des Repository-Anbieters</td>
  </tr>
  <tr>
   <td>query.joins</td>
   <td><p>Der Grad an Unterstützung von Joins bei Abfragen. Die folgenden Werte sind möglich:</p>
    <ul>
     <li>query.joins.none: Keine Unterstützung von Joins. Abfragen können einen Selektor verwenden.</li>
     <li>query.joins.inner: Unterstützung von Inner Joins.</li>
     <li>query.joins.inner.outer: Unterstützung von Inner Joins und Outer Joins.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>org.apache.jackrabbit.spi.commons.AdditionalEventInfo</td>
   <td> </td>
  </tr>
  <tr>
   <td>query.xpath.doc.order</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die XPath 1.0-Abfragesprache unterstützt.</td>
  </tr>
  <tr>
   <td>query.jcrpath</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.xml.import.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Importieren von XML-Code als Inhalt unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.same.name.siblings.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Geschwisterknoten (Knoten mit demselben übergeordneten Element) mit demselben Namen unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.residual.definitions.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Namenseigenschaften mit Restdefinitionen unterstützt. Wenn dies unterstützt wird, kann das Namensattribut einer Elementdefinition ein Asterisk (*) sein.</td>
  </tr>
  <tr>
   <td>node.type.management.autocreated.definitions.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die automatische Erstellung von untergeordneten Elementen (Knoten oder Eigenschaften) eines Knotens bei der Knotenerstellung unterstützt.</td>
  </tr>
  <tr>
   <td>crx.cluster.master</td>
   <td>Der Wert „true“ bedeutet, dass dieser Repository-Knoten der Master-Knoten des Clusters ist.</td>
  </tr>
  <tr>
   <td>level.1.supported</td>
   <td>Der Wert „true“ bedeutet, dass option.xml.export.support wahr ist und query.languages die Länge null aufweist.</td>
  </tr>
  <tr>
   <td>option.unfiled.content.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository nicht geordnete Inhalte unterstützt. Nicht erfasste Knoten gehören nicht zur Hierarchie des Repositorys.</td>
  </tr>
  <tr>
   <td>jcr.specification.name</td>
   <td>Der Name der JCR-Spezifikation, die das Repository implementiert</td>
  </tr>
  <tr>
   <td>option.versioning.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die volle Versionierung unterstützt. </td>
  </tr>
  <tr>
   <td>jcr.repository.name</td>
   <td>Der Name des Repositorys</td>
  </tr>
  <tr>
   <td>option.locking.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository das Sperren von Knoten unterstützt. Mit der Sperrung kann ein Benutzer temporär verhindern, dass ein anderer Benutzer Änderungen vornimmt.</td>
  </tr>
  <tr>
   <td>jcr.repository.version.display</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.activities.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Aktivitäten unterstützt. Aktivitäten sind eine Reihe von Änderungen, die in einem Arbeitsbereich vorgenommen werden und in einen anderen Arbeitsbereich zusammengeführt werden.</td>
  </tr>
  <tr>
   <td>node.type.management.multivalued.properties.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository Knoteneigenschaften mit null oder mehr Werten unterstützt.</td>
  </tr>
  <tr>
   <td>option.retention.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die Nutzung von externen Anwendungen für das Aufbewahrungsmanagement unterstützt, um Aufbewahrungsrichtlinien für Inhalte anzuwenden, und das Halten und Freigeben unterstützt.</td>
  </tr>
  <tr>
   <td>option.lifecycle.supported</td>
   <td>Der Wert „true“ bedeutet, dass das Repository die Lebenszyklusverwaltung unterstützt.</td>
  </tr>
 </tbody>
</table>

**** WorkspaceNamesDie Namen der Arbeitsflächen im Repository. Schreibgeschützt.

**** DataStoreGarbageCollectionDelayDie Zeit in Millisekunden, in der die Garbage Collection nach dem Scannen aller zehnten Nodes schläft. Lese- und Schreibzugriff.

**** BackupDelayDie Zeit in Millisekunden, die der Sicherungsvorgang zwischen den einzelnen Sicherungsschritten vergeht. Lese- und Schreibzugriff.

**** BackupInProgressDer Wert true gibt an, dass ein Sicherungsprozess ausgeführt wird. Schreibgeschützt.

**** BackupProgressFür die aktuelle Sicherung ist der Prozentsatz aller gesicherten Dateien. Schreibgeschützt.

**** CurrentBackupTargetFür die aktuelle Sicherung wird die ZIP-Datei, in der Sicherungsdateien gespeichert werden, verwendet. Wenn gerade kein Backup durchgeführt wird, wird kein Wert angezeigt. Schreibgeschützt.

**** BackupWarSuccessful Der Wert true gibt an, dass während der aktuellen Sicherung keine Fehler aufgetreten sind oder keine Sicherung ausgeführt wird. Der Wert „false“ bedeutet, dass beim aktuellen Backup ein Fehler aufgetreten ist. Schreibgeschützt.

**** BackupResultDer Status der aktuellen Sicherung. Die folgenden Werte sind möglich:

* Backup in progress: Gerade wird ein Backup ausgeführt.
* Backup canceled: Das Backup wurde abgebrochen.
* Backup finished with error: Beim Backup ist ein Fehler aufgetreten. Die Fehlermeldung enthält Angaben zur Ursache.
* Backup completed: Das Backup war erfolgreich.
* No backup executed so far: Es wird gerade kein Backup ausgeführt.

Schreibgeschützt.

**** TarOptimizationRunningSinceDer Zeitpunkt, zu dem der aktuelle TAR-Dateioptimierungsprozess begann. Schreibgeschützt.

**** TarOptimizationDelayDie Zeit in Millisekunden, die der TAR-Optimierungsprozess zwischen den einzelnen Schritten des Prozesses schläft. Lese- und Schreibzugriff.

**** ClusterPropertiesEine Gruppe von Schlüssel-Wert-Paaren, die Clustereigenschaften und -werte darstellen. Jede Zeile der Tabelle steht für eine Cluster-Eigenschaft. Schreibgeschützt.

**** ClusterNodesDie Mitglieder des Repository-Clusters.

**** ClusterIdDie Kennung dieses Repository-Clusters. Schreibgeschützt.

**** ClusterMasterIdDer Bezeichner des Übergeordnet-Knotens dieses Repository-Clusters. Schreibgeschützt.

**** ClusterNodeIdDie Kennung dieses Knotens im Repository-Cluster. Schreibgeschützt.

### Betrieb {#operations-1}

**** createWorkspaceErstellt eine Arbeitsfläche in diesem Repository.

* Argumente:

   * name: ein Zeichenfolgenwert, der den Namen des neuen Workspaces darstellt.

* Zurückgegebener Wert: keiner

**** runDataStoreGarbageCollectionFührt die Garbage Collection auf den Repository-Knoten aus.

* Argumente:

   * löschen: Ein boolescher Wert, der angibt, ob nicht verwendete Repository-Elemente gelöscht werden sollen. Der Wert „true“ bedeutet, dass nicht genutzte Knoten und Eigenschaften gelöscht werden. Der Wert „false“ bedeutet, dass alle Knoten gescannt, aber nicht gelöscht werden.

* Zurückgegebener Wert: keiner

**** stopDataStoreGarbageCollectionStellt eine laufende Datspeicher-Garbage-Sammlung ein.

* Argumente: keine
* Zurückgegebener Wert: Darstellung des aktuellen Status in einer Zeichenfolge

**** startBackupSichert Repository-Daten in einer ZIP-Datei.

* Argumente:

   * `target`: (Optional) Ein  `String` Wert, der den Namen der ZIP-Datei oder des Ordners darstellt, in dem die Repository-Daten archiviert werden sollen. Um eine ZIP-Datei zu verwenden, fügen Sie die ZIP-Dateinamen-Erweiterung ein. Um ein Verzeichnis zu verwenden, fügen Sie keine Dateinamen-Erweiterung ein.

      Um ein inkrementelles Backup durchzuführen, geben Sie das Verzeichnis an, das zuletzt für das Backup genutzt wurde.

      Sie können einen absoluten oder einen relativen Pfad festlegen. Relative Pfade sind relativ zum übergeordneten Element des CRX-Schnellstartverzeichnisses.

      Wenn Sie keinen Wert angeben, wird der Standardwert von `backup-currentdate.zip` verwendet, wobei `currentdate` im Format `yyyyMMdd-HHmm` vorliegt.

* Zurückgegebener Wert: keiner

**** cancelBackupStoppt den aktuellen Sicherungsvorgang und löscht das temporäre Archiv, das der für die Archivierung der Daten erstellte Prozess erstellt hat.

* Argumente: keine
* Zurückgegebener Wert: keiner

**Änderungen** an den Repository-Daten werden von blockRepositoryWritesBlocks übernommen. Alle Backup-Listener des Repositorys werden über die Blockierung informiert.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** unblockRepositoryWritesEntfernt den Block aus dem Repository. Alle Backup-Listener des Repositorys werden über die Aufhebung der Blockierung informiert.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** startTarOptimizationStartet den TAR-Dateioptimierungsprozess mit dem Standardwert für tarOptimizationDelay.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** stopTarOptimizationStoppt die TAR-Dateioptimierung.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** tarIndexMergeFührt die obersten Indexdateien aller TAR-Sets zusammen. Die höchsten Indexdateien sind Dateien mit unterschiedlichen Hauptversionen. Beispielsweise werden die folgenden Dateien in die Datei &quot;index_3_1.tar&quot;zusammengeführt: index_1_1.tar, index_2_0.tar, index_3_0.tar. Die zusammengeführten Dateien werden gelöscht (im vorherigen Beispiel werden &quot;index_1_1.tar&quot;, &quot;index_2_0.tar&quot;und &quot;index_3_0.tar&quot;gelöscht).

* Argumente:

   * `background`: Ein boolescher Wert, der angibt, ob der Vorgang im Hintergrund ausgeführt werden soll, damit die Web-Konsole währenddessen verwendet werden kann. Der Wert „true“ bedeutet, dass der Vorgang im Hintergrund ausgeführt wird.

* Zurückgegebener Wert: keiner

**Dieser Repository-Knoten** wird als Übergeordnet-Knoten des Clusters festgelegt. Wenn er nicht bereits Master ist, hält dieser Befehl den Listener der aktuellen Master-Instanz an und startet einen Master-Listener auf dem aktuellen Knoten. Dieser Knoten wird dann als Übergeordnet-Knoten festgelegt und neu gestartet, sodass alle anderen Knoten im Cluster (d. h. die vom Übergeordnet gesteuerten Knoten) eine Verbindung zu dieser Instanz herstellen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** joinClusterFügt dieses Repository einem Cluster als Knoten hinzu, der vom Cluster Übergeordnet gesteuert wird. Sie müssen für die Authentifizierung einen Benutzernamen und ein Kennwort eingeben. Die Verbindung nutzt die grundlegende Authentifizierung. Die Sicherheitsanmeldedaten werden mit Base64 verschlüsselt, bevor sie an den Server übermittelt werden.

* Argumente:

   * `master`: Ein Zeichenfolgenwert, der für die IP-Adresse oder den Computernamen des Computers steht, auf dem der Master-Repository-Knoten ausgeführt wird. 
   * `username`: Der Benutzername, der für die Authentifizierung beim Cluster genutzt werden soll.
   * `password`: Das Kennwort, dass für die Authentifizierung genutzt werden soll.

* Zurückgegebener Wert: keiner

**** traversalCheckTraverses und behebt optional Inkonsistenzen in einer Unterstruktur, die an einem bestimmten Knoten beginnt. Ausführliche Informationen hierzu finden Sie in der Dokumentation zu Persistenzmanagern.

**** complianceCheckChecks und optional Korrekturen der Konsistenz im Datenspeicher. Ausführliche Informationen hierzu finden Sie in der Dokumentation zum Datenspeicher.

## Repository-Statistiken (TimeSeries) {#repository-statistics-timeseries}

Der Wert des TimeSeries-Feldes für jeden Statistiktyp, den `org.apache.jackrabbit.api.stats.RepositoryStatistics` definiert.

* Domain: `com.adobe.granite`
* Typ: `TimeSeries`
* Name: Einer der folgenden Werte aus der Enum-Klasse:`org.apache.jackrabbit.api.stats.RepositoryStatistics.Type`

   * BUNDLE_CACHE_ACCESS_COUNTER
   * BUNDLE_CACHE_MISS_AVERAGE
   * BUNDLE_CACHE_MISS_COUNTER
   * BUNDLE_CACHE_MISS_DURATION
   * BUNDLE_CACHE_SIZE_COUNTER
   * BUNDLE_COUNTER
   * BUNDLE_READ_COUNTER
   * BUNDLE_WRITE_AVERAGE
   * BUNDLE_WRITE_COUNTER
   * BUNDLE_WRITE_DURATION
   * BUNDLE_WS_SIZE_COUNTER
   * QUERY_AVERAGE
   * QUERY_COUNT
   * QUERY_DURATION
   * SESSION_COUNT
   * SESSION_LOGIN_COUNTER
   * SESSION_READ_AVERAGE
   * SESSION_READ_COUNTER
   * SESSION_READ_DURATION
   * SESSION_WRITE_AVERAGE
   * SESSION_WRITE_COUNTER
   * SESSION_WRITE_DURATION

### Attribute {#attributes-1}

Die folgenden Attribute werden für jeden Statistiktyp bereitgestellt, der gemeldet wird:

* ValuePerSecond: Der gemessene Wert pro Sekunde während der letzten Minute. Schreibgeschützt.
* ValuePerMinute: Der gemessene Wert pro Minute während der letzten Stunde. Schreibgeschützt.
* ValuePerHour: Der gemessene Wert pro Stunde in der letzten Woche. Schreibgeschützt.
* ValuePerWeek: Der gemessene Wert pro Woche in den letzten drei Jahren. Schreibgeschützt.

## Repository-Abfragestatistiken {#repository-query-stats}

Statistische Informationen zu Repository-Abfragen.

* Domäne: com.adobe.granite
* Typ: QueryStat

### Attribute {#attributes-2}

**** SlowQueriesInformationen zu den Repository-Abfragen, die am längsten abgeschlossen wurden. Schreibgeschützt.

**** SlowQueriesQueueSizeDie maximale Anzahl von Abfragen, die in die SlowQueries-Liste einbezogen werden sollen. Lese- und Schreibzugriff.

**** PopularQueriesInformationen zu den Repository-Abfragen, die am häufigsten aufgetreten sind. Schreibgeschützt.

**** PopularQueriesQueueSizeDie maximale Anzahl von Abfragen in der Liste PopularQueries. Lese- und Schreibzugriff.

### Betrieb {#operations-2}

**** clearSlowQueriesQueueEntfernt alle Abfragen aus der SlowQueries-Liste.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** clearPopularQueriesQueueEntfernt alle Abfragen aus der PopularQueries-Liste.

* Argumente: keine
* Zurückgegebener Wert: keiner

## Replikationsagenten {#replication-agents}

Überwachen Sie die Dienste für jeden Replikationsagenten. Wenn Sie einen Replikationsagenten erstellen, wird der Dienst automatisch in der JMX-Konsole angezeigt.

* **Domäne:** com.adobe.granite.Replication
* **Typ:** Agent
* **Name:** kein Wert
* **Eigenschaften:** {id=&quot;*Name*&quot;}, wobei  ** Name der Wert der Eigenschaft agent Name ist.

### Attribute {#attributes-3}

**** IdEin Zeichenfolgenwert, der den Bezeichner der Replizierungsagentenkonfiguration darstellt. Mehrere Agenten können dieselbe Konfiguration nutzen. Schreibgeschützt.

**** ValidEin boolescher Wert, der angibt, ob der Agent korrekt konfiguriert ist:

* `true`: Gültige Konfiguration.
* `false` : Die Konfiguration enthält Fehler.

Schreibgeschützt.

**** AktiviertEin boolescher Wert, der angibt, ob der Agent aktiviert ist:

* `true`: Aktiviert.
* `false`: Disabled.

**** QueueBlockedEin boolescher Wert, der angibt, ob die Warteschlange vorhanden ist und blockiert ist:

* `true`: Blockiert. Ein automatischer erneuter Versuch steht aus.
* `false`: nicht blockiert oder nicht vorhanden

Schreibgeschützt.

**** QueuePausedEin boolescher Wert, der angibt, ob die Auftragswarteschlange angehalten wurde:

* `true`: Angehalten (ausgesetzt)
* `false`: nicht angehalten oder nicht vorhanden.

Lese- und Schreibzugriff.

**** QueueNumEntriesEin int-Wert, der die Anzahl der Aufträge in der Agenturwarteschlange angibt. Schreibgeschützt.

**** QueueStatusTimeEin Datumswert, der die Zeit auf dem Server angibt, zu der die angezeigten Statuswerte abgerufen wurden. Der Wert entspricht dem Zeitpunkt, zu dem die Seite geladen wurde. Schreibgeschützt.

**** QueueNextRetryTimeFür blockierte Warteschlangen, ein Datumswert, der angibt, wann der nächste automatische Versuch stattfindet. Wenn keine Zeit angegeben ist, ist die Warteschlange nicht blockiert. Schreibgeschützt.

**** QueueProcessingSinceEin Datumswert, der angibt, wann die Verarbeitung für den aktuellen Auftrag begonnen hat. Wenn keine Zeit angegeben ist, ist die Warteschlange entweder blockiert oder inaktiv. Schreibgeschützt.

**** QueueLastProcessTimeEin Datumswert, der angibt, wann der vorherige Auftrag abgeschlossen wurde. Schreibgeschützt.

### Betrieb {#operations-3}

**** queueForceRetryBei blockierten Warteschlangen wird der Befehl zum Wiederholen an die Warteschlange gesendet.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** queueClearEntfernt alle Aufträge aus der Warteschlange.

* Argumente: keine
* Zurückgegebener Wert: keiner

## Sling Engine {#sling-engine}

Stellt Statistiken zu HTTP-Abfragen bereit, damit Sie die Leistung des SlingRequestProcessor-Dienstes überwachen können.

* Domäne: org.apache.sling
* Typ: Engine
* Eigenschaften: {service=RequestProcessor}

### Attribute {#attributes-4}

**** RequestsCountDie Anzahl der Anfragen, die seit dem letzten Zurücksetzen der Statistiken aufgetreten sind.

**** MinRequestDurationMsecDie kürzeste Zeit (in Millisekunden), die seit dem letzten Zurücksetzen der Statistiken zur Verarbeitung einer Anforderung erforderlich war.

**** MaxRequestDurationMsecDie längste Zeit (in Millisekunden), die seit dem letzten Zurücksetzen der Statistiken zur Verarbeitung einer Anforderung erforderlich war.

**** StandardDeversionDurationMsecDie Standardabweichung der Zeitdauer, die für die Verarbeitung von Anforderungen erforderlich war. Diese Standardabweichung wird basierend auf allen Abfragen seit dem letzten Zurücksetzen der Statistiken ermittelt.

**** MeanRequestDurationMsecDer mittlere Zeitraum, der für die Verarbeitung einer Anforderung erforderlich war. Dieser Durchschnitt wird basierend auf allen Abfragen seit dem letzten Zurücksetzen der Statistiken ermittelt.

### Betrieb {#operations-4}

**** resetStatisticsLegt alle Statistiken auf null fest. Setzen Sie die Statistiken zurück, wenn Sie die Abfragen-Verarbeitungsleistung innerhalb eines bestimmten Zeitrahmens analysieren müssen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**** idDie Zeichenfolgendarstellung der Paket-ID.

**** installedEin boolescher Wert, der angibt, ob das Paket installiert ist:

* `true`: Installiert.
* `false`: Nicht installiert.

**** installedByDie ID des Benutzers, der das Paket zuletzt installiert hat.

**** installedDateDas Datum, an dem das Paket zuletzt installiert wurde.

**** sizeEin langer Wert, der die Größe des Pakets in Byte enthält.


## Quickstart-Starter {#quickstart-launcher}

Informationen zum Startvorgang und zum Quickstart-Starter.

* Domäne: com.adobe.granite.quickstart
* Typ: Starter

### Betrieb {#operations-5}

**log**

Zeigt eine Meldung im QuickStart-Fenster an.

Argumente:

* p1: Ein `String`-Wert, der die anzuzeigende Meldung enthält.
* Zurückgegebener Wert: keiner

**startupFinished**

Ruft die startupFinished-Methode des Server-Starters auf. Die Methode versucht, die Willkommensseite in einem Webbrowser zu öffnen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**startupProgress**

Legt den Abschlusswert des Server-Startvorgangs fest. Die Statusleiste im QuickStart-Fenster zeigt den Abschlusswert an.

* Argumente:
   * p1: Ein Gleitkommawert, der als Bruch angibt, wie groß der bereits abgeschlossene Anteil des Startvorgangs ist. Der Wert sollte zwischen null und eins liegen. Beispielsweise steht „0,3“ für „30 % abgeschlossen“.
* Zurückgegebener Wert: keiner

## Dienste von Drittanbietern  {#third-party-services}

Einige Drittanbieter-Serverressourcen installieren MBeans, die Attribute und Vorgänge an die JMX-Konsole übermitteln. In der folgenden Tabelle sind die Drittanbieter-Ressourcen und Links zu weiteren Informationen aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Domain</th>
   <th>Typ</th>
   <th>MBean-Klasse</th>
  </tr>
  <tr>
   <td>JMImplementation</td>
   <td>MBeanServerDelegate</td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/MBeanServerDelegate.html">javax.management.MBeanServerDelegate</a></td>
  </tr>
  <tr>
   <td>com.sun.management</td>
   <td>HotSpotDiagnostic</td>
   <td><a href="https://docs.oracle.com/javase/8/docs/jre/api/management/extension/com/sun/management/HotSpotDiagnosticMXBean.html">com.sun.management.HotSpotDiagnosticMXBean</a></td>
  </tr>
  <tr>
   <td>java.lang</td>
   <td>
    <ul>
     <li>ClassLoading</li>
     <li>Compilation</li>
     <li>GarbageCollector</li>
     <li>Arbeitsspeicher</li>
     <li>MemoryManager</li>
     <li>MemoryPool</li>
     <li>OperatingSystem</li>
     <li>Runtime</li>
     <li>Threading</li>
    </ul> </td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/package-summary.html">javax.</a> managementpackage</td>
  </tr>
  <tr>
   <td>java.util.logging</td>
   <td> </td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/logging/LoggingMXBean.html">java.util.logging.LoggingMXBean</a></td>
  </tr>
  <tr>
   <td>osgi.core</td>
   <td>
    <ul>
     <li>bundleState</li>
     <li>Framework</li>
     <li>packageState</li>
     <li>serviceState</li>
    </ul> </td>
   <td><a href="https://osgi.org/specification/osgi.enterprise/7.0.0/service.jmx.html#d0e42567">org.osgi.jmx.</a> frameworkpackage</td>
  </tr>
 </tbody>
</table>

## Verwenden der JMX-Konsole {#using-the-jmx-console}

Die JMX-Konsole zeigt Informationen zu mehreren Diensten an, die auf dem Server ausgeführt werden:

* Attribute: Diensteigenschaften wie Konfigurationen oder Laufzeitdaten. Attribute können schreibgeschützt oder mit Lese- und Schreibzugriff versehen sein.
* Vorgänge: Befehle, die Sie bei dem Dienst aufrufen können.

MBeans, die mit einem OSGi-Dienst bereitgestellt werden, übermitteln Dienstattribute und Vorgänge an die Konsole. Das MBean legt fest, welche Attribute und Vorgänge übermittelt werden und ob sie schreibgeschützt oder mit Lese- und Schreibzugriff versehen sind.

Die Hauptseite der JMX-Konsole enthält eine Tabelle der Dienste. Jede Zeile in der Tabelle steht für einen Dienst, der von einem MBean übermittelt wird.

1. Öffnen Sie die Web-Konsole und klicken Sie auf die JMX-Registerkarte ([http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
2. Klicken Sie auf einen Zellenwert für einen Dienst, um die Attribute und Vorgänge für diesen Dienst anzuzeigen.
3. Um einen Attributwert zu ändern, klicken Sie auf den Wert, geben Sie den Wert im angezeigten Dialogfeld ein und klicken Sie auf „Speichern“.
4. Um einen Dienstvorgang aufzurufen, klicken Sie auf den Vorgangsnamen, geben Sie die Argumentwerte im angezeigten Dialogfeld ein und klicken Sie auf „Aufrufen“.

## Verwenden externer JMX-Anwendungen zur Überwachung  {#using-external-jmx-applications-for-monitoring}

Bei CRX können externe Anwendungen über [Java Management Extensions (JMX)](https://docs.oracle.com/javase/6/docs/technotes/guides/management/overview.html) mit Managed Beans (MBeans) interagieren. Mit allgemeinen Konsolen wie [JConsole](https://java.sun.com/developer/technicalArticles/J2SE/jconsole.html) oder domänenspezifischen Überwachungsanwendungen können Sie CRX-Konfigurationen und -Eigenschaften abrufen und festlegen sowie die Leistung und Ressourcenauslastung überwachen.

### Herstellen einer Verbindung zu CRX mit JConsole  {#using-jconsole-to-connect-to-crx}

Um mit JConsole eine Verbindung zu CRX herzustellen, gehen Sie wie folgt vor:

1. Öffnen Sie ein Terminal-Fenster.
1. Geben Sie den folgenden Befehl ein:

   `jconsole`

JConsole wird gestartet und das JConsole-Fenster wird angezeigt.

### Verbinden mit einem lokalen CRX-Prozess {#connecting-to-a-local-crx-process}

JConsole zeigt eine Liste der lokalen Java Virtual Machine-Prozesse an. Die Liste enthält zwei Quickstart-Prozesse. Wählen Sie den „CHILD“-Quickstart-Prozess aus der Liste der lokalen Prozesse aus. (Das ist in der Regel der Prozess mit der höheren PID.)

![screen_shot_2012-03-26at114557am](assets/screen_shot_2012-03-26at114557am.png)

### Verbinden mit einem externen CRX-Prozess {#connecting-to-a-remote-crx-process}

Um eine Verbindung zu einem externen CRX-Prozess herzustellen, muss auf der JVM, die den externen CRX-Prozess hostet, die Annahme von externen JMX-Verbindungen aktiviert sein.

Um externe JMX-Verbindungen zu aktivieren, müssen Sie beim Starten der JVM die folgende Systemeigenschaft festlegen:

`com.sun.management.jmxremote.port=portNum`

In der o. g. Eigenschaft steht `portNum` für die Nummer des Ports, für den JMX-RMI-Verbindungen aktiviert werden sollen. Stellen Sie sicher, dass Sie eine nicht verwendete Portnummer angeben. Durch das Festlegen dieser Eigenschaft wird nicht nur ein RMI-Connector für den lokalen Zugriff veröffentlicht, sondern auch ein zusätzlicher RMI-Connector in einer privaten, schreibgeschützten Registrierung am angegebenen Port. Dabei wird ein bekannter Name verwendet, und zwar „jmxrmi“.

Wenn Sie die Remote-Überwachung für den JMX-Agenten aktivieren, wird zur Kennwortauthentifizierung die Kennwortdatei genutzt, die mit der folgenden Systemeigenschaft beim Starten der Java VM festgelegt werden muss:

`com.sun.management.jmxremote.password.file=pwFilePath`

Detaillierte Anweisungen zum Einrichten einer Kennwortdatei finden Sie in der [relevanten JMX-Dokumentation](https://docs.oracle.com/javase/6/docs/technotes/guides/management/agent.html).

Beispiel:

```shell
$ java
  -Dcom.sun.management.jmxremote.password.file=pwFilePath
  -Dcom.sun.management.jmxremote.port=8463
  -jar ./cq-quickstart.jar
```

### Verwenden der von CRX bereitgestellten MBeans {#using-the-mbeans-provided-by-crx}

Nach dem Herstellen der Verbindung zum Quickstart-Prozess bietet JConsole eine Reihe allgemeiner Überwachungstools für die JVM, auf der CRX ausgeführt wird.

![screen_shot_2012-03-26at115056am](assets/screen_shot_2012-03-26at115056am.png)

Um auf die internen Überwachungs- und Konfigurationsoptionen von CRX zuzugreifen, wählen Sie auf der Registerkarte „MBeans“ aus dem hierarchischen Inhaltsbaum auf der linken Seite die Attribute oder Vorgänge aus, für die Sie sich interessieren, z. B. für den Abschnitt „com.adobe.granite/Repository/Operations“.

Innerhalb dieses Abschnitts wählen Sie das gewünschte Attribut oder den gewünschten Vorgang im linken Bildschirmbereich aus.

![screen_shot_2012-03-26at115728am](assets/screen_shot_2012-03-26at115728am.png)

