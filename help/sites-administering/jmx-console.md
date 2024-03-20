---
title: Überwachen von Server-Ressourcen mit der JMX-Konsole
description: Erfahren Sie, wie Sie Serverressourcen mit der JMX-Konsole überwachen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: eabd8335-6140-4c15-8cff-21608719aa5f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '4830'
ht-degree: 51%

---

# Überwachen von Server-Ressourcen mit der JMX-Konsole{#monitoring-server-resources-using-the-jmx-console}

Mit der JMX-Konsole können Sie Dienste auf dem CRX-Server überwachen und verwalten. In den folgenden Abschnitten werden die Attribute und Vorgänge zusammengefasst, die über das JMX-Framework verfügbar sind.

Weitere Informationen zur Nutzung der Konsolensteuerung finden Sie unter [Verwenden der JMX-Konsole](#using-the-jmx-console). Hintergrundinformationen zu JMX finden Sie auf der Seite zu [Java Management Extensions (JMX)-Technologie](https://www.oracle.com/technetwork/java/javase/tech/javamanagement-140525.html) auf der Website von Oracle.

Informationen zum Erstellen von MBeans für die Verwaltung Ihrer Dienste mithilfe der JMX-Konsole finden Sie unter [Integration von Diensten in die JMX-Konsole](/help/sites-developing/jmx-integration.md).

## Workflow-Wartung {#workflow-maintenance}

Vorgänge für die Verwaltung von laufenden, abgeschlossenen, veralteten und fehlgeschlagenen Workflow-Instanzen.

* Domain: com.adobe.granite.workflow
* Typ: Wartung

>[!NOTE]
>
>Siehe [Workflow-Konsole](/help/sites-administering/workflows-administering.md) für zusätzliche Workflow-Verwaltungstools und Beschreibungen der möglichen Status der Workflow-Instanz.

### Betrieb {#operations}

**listRunningWorkflowsPerModel**: Führt die Anzahl an Workflow-Instanzen auf, die für jedes Workflow-Modell ausgeführt werden.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den Spalten Count und ModelId .

**listCompletedWorkflowsPerModel**: Führt die Anzahl an abgeschlossenen Workflow-Instanzen für jedes Workflow-Modell auf.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den Spalten Count und ModelId .

**returnWorkflowQueueInfo**: Zeigt Informationen zu Workflow-Elementen an, die bearbeitet wurden und sich in der Warteschlange für die Verarbeitung befinden.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den folgenden Spalten:

   * Aufträge
   * Queue Name
   * Jobs aktivieren
   * Durchschnittliche Verarbeitungszeit
   * Durchschnittliche Wartezeit
   * Abgebrochene Aufträge
   * Fehlgeschlagene Aufträge
   * Abgeschlossene Aufträge
   * Verarbeitete Aufträge
   * In Warteschlange gestellte Aufträge

**returnWorkflowJobTopicInfo**: Zeigt Verarbeitungsinformationen für Workflow-Aufträge nach Themen geordnet an.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten mit den folgenden Spalten:

   * Themenname
   * Durchschnittliche Verarbeitungszeit
   * Durchschnittliche Wartezeit
   * Abgebrochene Aufträge
   * Fehlgeschlagene Aufträge
   * Abgeschlossene Aufträge
   * Verarbeitete Aufträge

**returnFailedWorkflowCount**: Führt die Anzahl an fehlgeschlagenen Workflow-Instanzen auf. Sie können ein Workflow-Modell für die Abfrage angeben oder Informationen für alle Workflow-Modelle abrufen.

* Argumente:

   * model: Die ID des Modells, das abgefragt werden soll. Um die Anzahl fehlgeschlagener Workflow-Instanzen für alle Workflow-Modelle anzuzeigen, geben Sie keinen Wert an. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an fehlgeschlagenen Workflow-Instanzen.

**returnFailedWorkflowCountPerModel**: Führt die Anzahl an Workflow-Instanzen auf, die für jedes Workflow-Modell fehlgeschlagen sind.

* Argumente: keine.
* Zurückgegebener Wert: Tabellendaten mit den Spalten Zählung und Modell-ID .

**terminateFailedInstances**: Beendet Workflows, die fehlgeschlagen sind. Sie können alle fehlgeschlagenen Instanzen oder nur die fehlgeschlagenen Instanzen für ein bestimmtes Modell beenden. Optional können Sie die Instanzen nach Beendigung neu starten. Sie können den Vorgang auch testen, um die Ergebnisse anzuzeigen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Restart the instance: (optional) Legen Sie den Wert `true` fest, um die Instanzen neu zu starten, nachdem sie beendet wurden. Beim Standardwert `false` werden beendete Workflow-Instanzen nicht neu gestartet.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.
   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Geben Sie kein Modell an, um den Vorgang auf die fehlgeschlagenen Instanzen aller Workflow-Modelle anzuwenden. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: Tabellendaten zu den beendeten Instanzen, die die folgenden Spalten enthalten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**retryFailedWorkItems**: Versucht, fehlgeschlagene Arbeitselementschritte auszuführen. Sie können alle fehlgeschlagenen Arbeitselemente erneut ausführen lassen oder nur die fehlgeschlagenen Arbeitselemente für ein bestimmtes Workflow-Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.
   * Model: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die fehlgeschlagenen Arbeitselemente aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: Tabellendaten zu den fehlgeschlagenen Arbeitselementen, die wiederholt werden, einschließlich der folgenden Spalten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**PurgeActive**: Entfernt aktive Workflow-Instanzen eines bestimmten Alters. Sie können aktive Instanzen für alle Modelle bereinigen oder nur die Instanzen für ein bestimmtes Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Modell: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Number of days since workflow started: das Alter der zu bereinigenden Workflow-Instanzen in Tagen.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: Tabellendaten zu den aktiven Workflow-Instanzen, die bereinigt werden, einschließlich der folgenden Spalten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**countStaleWorkflows**: Gibt die Anzahl an veralteten Workflow-Instanzen zurück. Sie können die Anzahl der veralteten Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Modell: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an veralteten Workflow-Instanzen.

**restartStaleWorkflows**: Startet veraltete Workflow-Instanzen neu. Sie können alle veralteten Instanzen oder nur die veralteten Instanzen für ein bestimmtes Modell neu starten. Sie können den Vorgang auch testen, um die Ergebnisse anzuzeigen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Modell: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Geben Sie kein Modell an, um den Vorgang auf die veralteten Instanzen aller Workflow-Modelle anzuwenden. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: eine Liste der Workflow-Instanzen, die neu gestartet werden.

**fetchModelList**: Führt alle Workflow-Modelle auf.

* Argumente: keine
* Zurückgegebener Wert: Tabellendaten, die die Workflow-Modelle einschließlich der Spalten ModelId und ModelName identifizieren.

**countRunningWorkflows**: Gibt die Anzahl an laufenden Workflow-Instanzen zurück. Sie können die Anzahl der laufenden Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Model: (optional) die ID des Modells, für das die Anzahl an laufenden Instanzen zurückgegeben wird. Um die Anzahl an laufenden Instanzen für alle Workflow-Modelle zurückzugeben, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an laufenden Workflow-Instanzen.

**countCompletedWorkflows**: Gibt die Anzahl an abgeschlossenen Workflow-Instanzen zurück. Sie können die Anzahl der abgeschlossenen Instanzen für alle Workflow-Modelle oder für ein bestimmtes Modell abrufen.

* Argumente:

   * Model: (optional) die ID des Modells, für das die Anzahl an abgeschlossenen Instanzen zurückgegeben wird. Um die Anzahl an abgeschlossenen Instanzen für alle Workflow-Modelle zurückzugeben, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Zurückgegebener Wert: die Anzahl an abgeschlossenen Workflow-Instanzen.

**purgeCompleted**: Entfernt Datensätze von abgeschlossenen Workflows eines bestimmten Alters aus dem Repository. Wenn Sie häufig Workflows verwenden, verringern Sie mit diesem Vorgang regelmäßig die Größe des Repositorys. Sie können abgeschlossene Instanzen für alle Modelle bereinigen oder nur die Instanzen für ein bestimmtes Modell. Optional können Sie den Vorgang testen, um die Ergebnisse zu sehen, ohne den Vorgang tatsächlich durchzuführen.

* Argumente:

   * Modell: (optional) Die ID des Modells, auf das der Vorgang angewendet wird. Um den Vorgang auf die Workflow-Instanzen aller Workflow-Modelle anzuwenden, legen Sie kein Modell fest. Die ID ist der Pfad zum Modellknoten, z. B.:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Number of days since workflow has been completed: die Anzahl an Tagen, seit denen sich die Workflow-Instanzen im abgeschlossenen Status befinden.
   * Dry Run: (optional) Legen Sie den Wert `true` fest, um die Ergebnisse des Vorgangs zu sehen, ohne den Vorgang tatsächlich durchzuführen. Beim Standardwert `false` wird der Vorgang durchgeführt.

* Zurückgegebener Wert: Tabellendaten zu den abgeschlossenen Workflow-Instanzen, die gelöscht werden, einschließlich der folgenden Spalten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

## Repository {#repository}

Informationen zum CRX-Repository

* Domain: com.adobe.granite
* Typ: Repository

### Attribute {#attributes}

**Name**: Der Name der JCR-Repository-Implementierung. Schreibgeschützt.

**Version**: Die Repository-Implementierungsversion. Schreibgeschützt.

**HomeDir**: Das Verzeichnis, in dem sich das Repository befindet. Der standardmäßige Speicherort ist &lt;QuickStart_Jar_Location>/crx-quickstart/repository. Schreibgeschützt.

**CustomerName**: Der Name der Kundschaft, für die die Softwarelizenz ausgegeben wurde. Schreibgeschützt.

**LicenseKey**: Der eindeutige Lizenzschlüssel für diese Installation des Repositorys. Schreibgeschützt.

**AvailableDiskSpace**: Der Festplatten-Speicherplatz, der für diese Instanz des Repositorys verfügbar ist, in MB. Schreibgeschützt.

**MaximumNumberOfOpenFiles**: Die Anzahl an Dateien, die gleichzeitig geöffnet werden können. Schreibgeschützt.

**SessionTracker**: Der Wert der Systemvariablen „crx.debug.sessions“. Der Wert „true“ steht für eine Debugging-Sitzung. Der Wert „false“ steht für eine normale Sitzung. Lese- und Schreibzugriff.

**Descriptors**: Ein Satz an Schlüsselwertpaaren, die für Repository-Eigenschaften stehen. Alle Eigenschaften sind schreibgeschützt.

<table>
 <tbody>
  <tr>
   <th>Schlüssel</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>option.node.and.property.with.same.name.supported</td>
   <td>Gibt an, ob ein Knoten und eine Eigenschaft des Knotens denselben Namen haben können. Der Wert "true"bedeutet, dass dieselben Namen unterstützt werden, der Wert "false"zeigt an, dass er nicht unterstützt wird. </td>
  </tr>
  <tr>
   <td>identifier.stability</td>
   <td>Gibt die Stabilität von nicht referenzierbaren Knoten-IDs an. Die folgenden Werte sind möglich:
    <ul>
     <li>identifier.stability.indefinite.duration: Die IDs ändern sich nicht.</li>
     <li>identifier.stability.method.duration: Die IDs können sich zwischen Methodenaufrufen ändern.</li>
     <li>identifier.stability.save.duration: Die IDs ändern sich innerhalb eines Speicherzyklus/Aktualisierungszyklus nicht.</li>
     <li>identifier.stability.session.duration: Die IDs ändern sich während einer Sitzung nicht.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>query.xpath.pos.index</td>
   <td>Gibt an, ob die XPath-Abfragesprache JCR 1.0 unterstützt wird. "true"bedeutet "support"und "false"zeigt an, dass keine Unterstützung verfügbar ist.</td>
  </tr>
  <tr>
   <td>crx.repository.systemid</td>
   <td>Die Systemkennung, wie sie in der Datei system.id enthalten ist.</td>
  </tr>
  <tr>
   <td>option.query.sql.supported</td>
   <td>Gibt an, ob die XPath-Abfragesprache JCR 1.0 unterstützt wird. "true"bedeutet "support"und "false"zeigt an, dass keine Unterstützung verfügbar ist.</td>
  </tr>
  <tr>
   <td>jcr.repository.version</td>
   <td>Die Version der Repository-Implementierung.</td>
  </tr>
  <tr>
   <td>option.update.primary.node.type.supported</td>
   <td>Gibt an, ob der primäre Knotentyp eines Knotens geändert werden kann. "true"bedeutet, dass Sie den primären Knotentyp ändern können, und "false"zeigt an, dass die Änderung nicht unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.node.type.management.supported</td>
   <td>Gibt an, ob die Knotentyp-Verwaltung unterstützt wird. Der Wert "true"zeigt an, dass er unterstützt wird, und der Wert "false"zeigt an, dass keine Unterstützung erfolgt.</td>
  </tr>
  <tr>
   <td>node.type.management.overrides.supported</td>
   <td>Gibt an, ob Sie die geerbte Eigenschaft oder die Definition des untergeordneten Knotens eines Knotentyps überschreiben können. "true"bedeutet, dass Überschreibungen unterstützt werden, und "false"bedeutet, dass keine Überschreibungen möglich sind.</td>
  </tr>
  <tr>
   <td>option.observation.supported</td>
   <td>Der Wert "true"bedeutet, dass die asynchrone Beobachtung von Repository-Änderungen unterstützt wird. Die Unterstützung der asynchronen Überwachung ermöglicht es Anwendungen, Benachrichtigungen über jede Änderung zu erhalten und darauf zu reagieren.</td>
  </tr>
  <tr>
   <td>query.jcrscore</td>
   <td><p>Der Wert „true“ bedeutet, dass die Pseudoeigenschaft „jcr:score“ in XPath verfügbar ist und mit SQL-Abfragen, die „jcrfn:contains“ (in XPath) oder „CONTAINS“ (in SQL) enthalten, Volltextsuchen durchgeführt werden können.</p> </td>
  </tr>
  <tr>
   <td>option.simple.versioning.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die einfache Versionierung unterstützt. Bei einfacher Versionierung verwaltet das Repository eine sequenzielle Reihe von Versionen eines Knotens.</td>
  </tr>
  <tr>
   <td>option.workspace.management.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository das Erstellen und Löschen von Arbeitsbereichen mithilfe von APIs unterstützt.</td>
  </tr>
  <tr>
   <td>option.update.mixin.node.types.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository das Hinzufügen und Entfernen von Mixin-Knotentypen eines vorhandenen Knotens unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.primary.item.name.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository es ermöglicht, Knotendefinitionen als untergeordnetes Element zu enthalten. Auf ein Primärelement kann über die API zugegriffen werden, ohne dass der Elementname bekannt ist.</td>
  </tr>
  <tr>
   <td>level.2.supported</td>
   <td>Der Wert "true"bedeutet, dass sowohl LEVEL_1_SUPPORTED als auch OPTION_XML_IMPORT_SUPPORTED "true"sind.</td>
  </tr>
  <tr>
   <td>write.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Schreibzugriff über die API bereitstellt. false bedeutet schreibgeschützten Zugriff.</td>
  </tr>
  <tr>
   <td>node.type.management.update.in.use.supported</td>
   <td>Der Wert "true"bedeutet, dass Sie Knotendefinitionen ändern können, die von vorhandenen Knoten verwendet werden.</td>
  </tr>
  <tr>
   <td>jcr.specification.version</td>
   <td>Die Version der JCR-Spezifikation, die das Repository implementiert.</td>
  </tr>
  <tr>
   <td>option.journaled.observation.supported</td>
   <td>Der Wert "true"bedeutet, dass Anwendungen eine journalisierte Beobachtung des Repositorys durchführen können. eine Reihe von Änderungsbenachrichtigungen für einen bestimmten Zeitraum erhalten. </td>
  </tr>
  <tr>
   <td>query.languages</td>
   <td>Die vom Repository unterstützten Abfragesprachen. Kein Wert bedeutet, dass keine Abfrage unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.xml.export.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository das Exportieren von Knoten als XML-Code unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.multiple.binary.properties.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Registrierung von Knotentypen mit mehreren binären Eigenschaften unterstützt. false zeigt an, dass eine einzelne binäre Eigenschaft für einen Knotentyp unterstützt wird.</td>
  </tr>
  <tr>
   <td>option.access.control.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Zugriffskontrolle zum Festlegen und Ermitteln von Benutzerberechtigungen für den Knotenzugriff unterstützt.</td>
  </tr>
  <tr>
   <td>option.baselines.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository sowohl Konfigurationen als auch Grundlinien unterstützt.</td>
  </tr>
  <tr>
   <td>option.shareable.nodes.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Erstellung von freigebbaren Knoten unterstützt.</td>
  </tr>
  <tr>
   <td>crx.cluster.id</td>
   <td>Die Kennung des Repository-Clusters.</td>
  </tr>
  <tr>
   <td>query.stored.queries.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository gespeicherte Abfragen unterstützt.</td>
  </tr>
  <tr>
   <td>query.full.text.search.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Volltextsuche unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.inheritance</td>
   <td><p>Gibt den Grad der Repository-Unterstützung für die Vererbung vom Knotentyp an. Die folgenden Werte sind möglich:</p> <p>node.type.management.inheritance.minimal: Die Registrierung der primären Knotentypen ist auf diejenigen beschränkt, die nur nt:base als Supertyp haben. Die Registrierung von Mixin-Knotentypen ist auf Typen ohne Supertyp beschränkt.</p> <p>node.type.management.inheritance.single: Es können nur die primären Knotentypen mit einem Supertyp registriert werden. Die Registrierung von Mixin-Knotentypen ist auf die mit höchstens einem Supertyp beschränkt.</p> <p><br /> node.type.management.inheritance.multiple: Es können primäre Knotentypen mit einem Supertyp oder mehreren Supertypen registriert werden. Mixin-Knotentypen können mit null oder mehr Supertypen registriert werden.</p> </td>
  </tr>
  <tr>
   <td>crx.cluster.preferredMaster</td>
   <td>Der Wert "true"bedeutet, dass dieser Clusterknoten der bevorzugte Master des Clusters ist.</td>
  </tr>
  <tr>
   <td>option.transactions.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Transaktionen unterstützt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor.url</td>
   <td>Die URL des Repository-Anbieters.</td>
  </tr>
  <tr>
   <td>node.type.management.value.constraints.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Wertbegrenzungen für Knoteneigenschaften unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.property.types</td>
   <td>Ein Array von javax.jcr.PropertyType-Konstanten, die für die Eigenschaftstypen stehen, die ein registrierter Knotentyp festlegen kann. Ein Array der Länge null gibt an, dass registrierte Knotentypen keine Eigenschaftsdefinitionen festlegen können. Eigenschaftstypen sind: STRING, URI, BOOLEAN, LONG, DOUBLE, DECIMAL, BINARY, DATE, NAME, PATH, WEAKREFERENCE, REFERENCE und UNDEFINED (falls unterstützt)</td>
  </tr>
  <tr>
   <td>node.type.management.orderable.child.nodes.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Beibehaltung der Reihenfolge der untergeordneten Knoten unterstützt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor</td>
   <td>Der Name des Repository-Anbieters.</td>
  </tr>
  <tr>
   <td>query.joins</td>
   <td><p>Der Grad der Unterstützung für Joins in Abfragen. Die folgenden Werte sind möglich:</p>
    <ul>
     <li>query.joins.none: Keine Unterstützung für Joins. Abfragen können einen Selektor verwenden.</li>
     <li>query.joins.inner: Unterstützung für innere Joins.</li>
     <li>query.joins.inner.outer: Unterstützung für innere und äußere Joins.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>org.apache.jackrabbit.spi.commons.AdditionalEventInfo</td>
   <td> </td>
  </tr>
  <tr>
   <td>query.xpath.doc.order</td>
   <td>Der Wert "true"bedeutet, dass das Repository die XPath 1.0-Abfragesprache unterstützt.</td>
  </tr>
  <tr>
   <td>query.jcrpath</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.xml.import.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository den Import von XML-Code als Inhalt unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.same.name.siblings.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository gleichrangige Knoten (Knoten mit demselben übergeordneten Element) mit denselben Namen unterstützt.</td>
  </tr>
  <tr>
   <td>node.type.management.residual.definitions.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Namenseigenschaften mit Restdefinitionen unterstützt. Wenn dies unterstützt wird, kann das Attribut name einer Elementdefinition ein Sternchen ("*") sein.</td>
  </tr>
  <tr>
   <td>node.type.management.autocreated.definitions.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die automatische Erstellung von untergeordneten Elementen (Knoten oder Eigenschaften) eines Knotens unterstützt, wenn der Knoten erstellt wird.</td>
  </tr>
  <tr>
   <td>crx.cluster.master</td>
   <td>Der Wert "true"bedeutet, dass dieser Repository-Knoten der Master-Knoten des Clusters ist.</td>
  </tr>
  <tr>
   <td>level.1.supported</td>
   <td>Der Wert "true"bedeutet, dass option.xml.export.support "true"ist und query.languages die Länge ungleich null hat.</td>
  </tr>
  <tr>
   <td>option.unfiled.content.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository nicht abgelegten Inhalt unterstützt. Nicht abgelegte Knoten sind nicht Teil der Repository-Hierarchie.</td>
  </tr>
  <tr>
   <td>jcr.specification.name</td>
   <td>Der Name der JCR-Spezifikation, die das Repository implementiert.</td>
  </tr>
  <tr>
   <td>option.versioning.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die vollständige Versionierung unterstützt.</td>
  </tr>
  <tr>
   <td>jcr.repository.name</td>
   <td>Der Name des Repository.</td>
  </tr>
  <tr>
   <td>option.locking.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository das Sperren von Knoten unterstützt. Durch das Sperren kann ein Benutzer vorübergehend verhindern, dass andere Benutzer Änderungen vornehmen.</td>
  </tr>
  <tr>
   <td>jcr.repository.version.display</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.activities.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Aktivitäten unterstützt. Aktivitäten sind eine Reihe von Änderungen, die in einem Arbeitsbereich vorgenommen werden und in einem anderen Arbeitsbereich zusammengeführt werden.</td>
  </tr>
  <tr>
   <td>node.type.management.multivalued.properties.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository Knoteneigenschaften unterstützt, die null oder mehr Werte aufweisen können.</td>
  </tr>
  <tr>
   <td>option.retention.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Verwendung externer Anwendungen zur Aufbewahrungsverwaltung unterstützt, um Aufbewahrungsrichtlinien auf Inhalte anzuwenden, und dass es die Aufbewahrung und Veröffentlichung unterstützt.</td>
  </tr>
  <tr>
   <td>option.lifecycle.supported</td>
   <td>Der Wert "true"bedeutet, dass das Repository die Lebenszyklusverwaltung unterstützt.</td>
  </tr>
 </tbody>
</table>

**WorkspaceNames**: Die Namen der Workspaces im Repository. Schreibgeschützt.

**DataStoreGarbageCollectionDelay**: Die Zeitdauer in Millisekunden, wie lange die Speicherbereinigung nach dem Scannen jedes zehnten Knotens ruht. Lese- und Schreibzugriff.

**BackupDelay**: Die Zeitdauer in Millisekunden, wie lange der Backup-Vorgang nach jedem Backup-Schritt ruht. Lese- und Schreibzugriff.

**BackupInProgress**: Der Wert „true“ bedeutet, dass gerade ein Backup-Vorgang ausgeführt wird. Schreibgeschützt.

**BackupProgress**: Der Prozentsatz aller Dateien, die beim aktuellen Backup gesichert wurden. Schreibgeschützt.

**CurrentBackupTarget**: Die ZIP-Datei, in der die Backup-Dateien des aktuellen Backups gespeichert werden. Wenn gerade kein Backup durchgeführt wird, wird kein Wert angezeigt. Schreibgeschützt.

**BackupWasSuccessful**: Der Wert „true“ bedeutet, dass beim aktuellen Backup keine Fehler aufgetreten sind oder dass gerade kein Backup durchgeführt wird. false zeigt an, dass während der aktuellen Sicherung ein Fehler aufgetreten ist. Schreibgeschützt.

**BackupResult**: Der Status des aktuellen Backups. Die folgenden Werte sind möglich:

* Backup in progress: Derzeit wird eine Sicherung ausgeführt.
* Backup abgebrochen: Die Sicherung wurde abgebrochen.
* Backup beendet mit Fehler: Während der Sicherung ist ein Fehler aufgetreten. Die Fehlermeldung enthält Informationen zur Ursache.
* Backup completed: Die Sicherung war erfolgreich.
* Bisher kein Backup ausgeführt: Es wird kein Backup durchgeführt.

Schreibgeschützt.

**TarOptimizationRunningSince**: Die Uhrzeit, zu der der aktuelle Vorgang der Optimierung der TAR-Datei begonnen hat. Schreibgeschützt.

**TarOptimizationDelay**: Die Zeitdauer in Millisekunden, wie lange der Vorgang der Optimierung der TAR-Datei nach jedem Schritt ruht. Lese- und Schreibzugriff.

**ClusterProperties**: Ein Satz an Schlüsselwertpaaren, die für Cluster-Eigenschaften und -Werte stehen. Jede Zeile in der Tabelle stellt eine Cluster-Eigenschaft dar. Schreibgeschützt.

**ClusterNodes**: Die Mitglieder des Repository-Clusters.

**ClusterId**: Die ID dieses Repository-Clusters. Schreibgeschützt.

**ClusterMasterId**: Die ID des Master-Knotens dieses Repository-Clusters. Schreibgeschützt.

**ClusterNodeId**: Die ID dieses Knotens des Repository-Clusters. Schreibgeschützt.

### Betrieb {#operations-1}

**createWorkspace**: Legt einen Workspace in diesem Repository an.

* Argumente:

   * name: Ein String -Wert, der den Namen des neuen Arbeitsbereichs darstellt.

* Zurückgegebener Wert: keiner

**runDataStoreGarbageCollection**: Führt die Speicherbereinigung auf den Repository-Knoten durch.

* Argumente:

   * delete: Ein boolescher Wert, der angibt, ob nicht genutzte Repository-Elemente gelöscht werden sollen. Der Wert true bewirkt das Löschen nicht verwendeter Knoten und Eigenschaften. Der Wert false bewirkt, dass alle Knoten gescannt, aber keine gelöscht werden.

* Zurückgegebener Wert: keiner

**stopDataStoreGarbageCollection**: Hält eine gerade ausgeführte Datenspeicherbereinigung an.

* Argumente: keine
* Zurückgegebener Wert: Zeichenfolgendarstellung des aktuellen Status

**startBackup**: Sichert Repository-Daten in einer ZIP-Datei.

* Argumente:

   * `target`: (optional) Ein `String`-Wert, der für den Namen der ZIP-Datei oder des Verzeichnisses steht, in der bzw. dem die Repository-Daten gespeichert werden sollen. Um eine ZIP-Datei zu verwenden, fügen Sie die ZIP-Dateinamenerweiterung hinzu. Um ein Verzeichnis zu verwenden, fügen Sie keine Dateinamenerweiterung hinzu.

     Um ein inkrementelles Backup durchzuführen, geben Sie das Verzeichnis an, das zuletzt für das Backup genutzt wurde.

     Sie können einen absoluten oder einen relativen Pfad festlegen. Relative Pfade sind relativ zum übergeordneten Element des CRX-Schnellstartverzeichnisses.

     Wenn Sie keinen Wert festlegen, wird der Standardwert `backup-currentdate.zip` genutzt, bei dem der Wert für das aktuelle Datum, `currentdate`, im Format `yyyyMMdd-HHmm` angegeben wird.

* Zurückgegebener Wert: keiner

**cancelBackup**: Hält den aktuellen Backup-Vorgang an und löscht das temporäre Archiv, das der Vorgang für die Archivierung der Daten erstellt hatte.

* Argumente: keine
* Zurückgegebener Wert: keiner

**blockRepositoryWrites**: Blockiert Änderungen an den Repository-Daten. Alle Backup-Listener des Repositorys werden über den Block benachrichtigt.

* Argumente: keine
* Zurückgegebener Wert: keiner

**unblockRepositoryWrites**: Hebt die Blockierung des Repositorys auf. Alle Backup-Listener des Repositorys werden über die Entfernung des Blocks informiert.

* Argumente: keine
* Zurückgegebener Wert: keiner

**startTarOptimization**: Startet den Vorgang zur Optimierung der TAR-Datei mit dem Standardwert für tarOptimizationDelay.

* Argumente: keine
* Zurückgegebener Wert: keiner

**stopTarOptimization**: Hält die Optimierung der TAR-Datei an.

* Argumente: keine
* Zurückgegebener Wert: keiner

**tarIndexMerge**: Führt die höchsten Indexdateien aller TAR-Sets zusammen. Die höchsten Indexdateien sind Dateien mit unterschiedlichen Hauptversionen. Beispielsweise werden die folgenden Dateien in der Datei index_3_1.tar zusammengeführt: index_1_1.tar, index_2_0.tar, index_3_0.tar. Die zusammengeführten Dateien werden gelöscht (im vorherigen Beispiel sind das die Dateien index_1_1.tar, index_2_0.tar und index_3_0.tar).

* Argumente:

   * `background`: Ein boolescher Wert, der angibt, ob der Vorgang im Hintergrund ausgeführt werden soll, damit die Web-Konsole währenddessen verwendet werden kann. Der Wert true führt den Vorgang im Hintergrund aus.

* Zurückgegebener Wert: keiner

**becomeClusterMaster**: Legt diesen Repository-Knoten als Master-Knoten des Clusters fest. Wenn er nicht bereits Master ist, hält dieser Befehl den Listener der aktuellen Master-Instanz an und startet einen Master-Listener auf dem aktuellen Knoten. Dieser Knoten wird dann als Master-Knoten festgelegt und neu gestartet, wodurch alle anderen Knoten im Cluster (d. h. die vom Master gesteuerten Knoten) eine Verbindung zu dieser Instanz herstellen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**joinCluster** Fügt dieses Repository einem Cluster als Knoten hinzu, der vom Cluster-Master gesteuert wird. Geben Sie einen Benutzernamen und ein Kennwort für Authentifizierungszwecke an. Die Verbindung verwendet eine einfache Authentifizierung. Die Sicherheitsberechtigungen sind Base-64-kodiert, bevor sie an den Server gesendet werden.

* Argumente:

   * `master`: Ein Zeichenfolgenwert, der für die IP-Adresse oder den Computernamen des Computers steht, auf dem der Master-Repository-Knoten ausgeführt wird. 
   * `username`: Der Benutzername, der für die Authentifizierung beim Cluster genutzt werden soll.
   * `password`: Das Kennwort, dass für die Authentifizierung genutzt werden soll.

* Zurückgegebener Wert: keiner

**traversalCheck**: Durchläuft und behebt ggf. Inkonsistenzen in einer Unterstruktur, beginnend bei einem bestimmten Knoten. Ausführliche Informationen hierzu finden Sie in der Dokumentation zu Persistenz-Managern.

**consistencyCheck**: Überprüft und behebt ggf. Inkonsistenzen im Datenspeicher. Ausführliche Informationen hierzu finden Sie in der Dokumentation zum Datenspeicher.

## Repository-Statistiken (TimeSeries) {#repository-statistics-timeseries}

Der Wert des TimeSeries-Feldes für jeden Statistiktyp, den `org.apache.jackrabbit.api.stats.RepositoryStatistics` definiert.

* Domain: `com.adobe.granite`
* Typ: `TimeSeries`
* Name: einer der folgenden Werte aus der Enum-Klasse von `org.apache.jackrabbit.api.stats.RepositoryStatistics.Type`:

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

Für jeden berichteten Statistiktyp werden die folgenden Attribute bereitgestellt:

* ValuePerSecond: Der gemessene Wert pro Sekunde über die letzte Minute. Schreibgeschützt.
* ValuePerMinute: Der gemessene Wert pro Minute während der letzten Stunde. Schreibgeschützt.
* ValuePerHour: Der gemessene Wert pro Stunde während der letzten Woche. Schreibgeschützt.
* ValuePerWeek: Der gemessene Wert pro Woche während der letzten drei Jahre. Schreibgeschützt.

## Repository-Abfragestatistiken {#repository-query-stats}

Statistische Informationen zu Repository-Abfragen.

* Domain: com.adobe.granite
* Typ: QueryStat

### Attribute {#attributes-2}

**SlowQueries**: Informationen zu den Repository-Abfragen, deren Abschluss am längsten gedauert hat. Schreibgeschützt.

**SlowQueriesQueueSize**: Die maximale Anzahl an Abfragen, die in der SlowQueries-Liste enthalten sein sollen. Lese- und Schreibzugriff.

**PopularQueries**: Informationen zu den Repository-Abfragen, die am häufigsten durchgeführt wurden. Schreibgeschützt.

**PopularQueriesQueueSize**: Die Höchstzahl an Abfragen in der PopularQueries-Liste. Lese- und Schreibzugriff.

### Betrieb {#operations-2}

**clearSlowQueriesQueue**: Entfernt alle Abfragen aus der SlowQueries-Liste.

* Argumente: keine
* Zurückgegebener Wert: keiner

**clearPopularQueriesQueue**: Entfernt alle Abfragen aus der PopularQueries-Liste.

* Argumente: keine
* Zurückgegebener Wert: keiner

## Replikations-Agenten {#replication-agents}

Überwachen Sie die Dienste für jeden Replikationsagenten. Wenn Sie einen Replikationsagenten erstellen, wird der Dienst automatisch in der JMX-Konsole angezeigt.

* **Domain:** com.adobe.granite.replication
* **Typ:** agent
* **Name:** kein Wert
* **Eigenschaften:** {id=&quot;*Name*&quot;}, wobei *Name* der Wert der Eigenschaft für den Agentennamen ist.

### Attribute {#attributes-3}

**Id**: Ein Zeichenfolgenwert, der für die ID der Konfiguration des Replikationsagenten steht. Mehrere Agenten können dieselbe Konfiguration verwenden. Schreibgeschützt.

**Valid**: Ein boolescher Wert, der angibt, ob der Agent korrekt konfiguriert ist:

* `true`: Gültige Konfiguration.
* `false` : Die Konfiguration enthält Fehler.

Schreibgeschützt.

**Enabled**: Ein boolescher Wert, der angibt, ob der Agent aktiviert ist:

* `true`: Aktiviert.
* `false`: Deaktiviert.

**QueueBlocked**: Ein boolescher Wert, der angibt, ob die Warteschlange vorhanden und blockiert ist:

* `true`: Blockiert. Ein automatischer erneuter Versuch steht aus.
* `false`: nicht blockiert oder nicht vorhanden

Schreibgeschützt.

**QueuePaused**: Ein boolescher Wert, der angibt, ob die Auftragswarteschlange angehalten wurde:

* `true`: angehalten (ausgesetzt)
* `false`: nicht angehalten oder nicht vorhanden.

Lese- und Schreibzugriff.

**QueueNumEntries**: Ein int-Wert, der für die Anzahl an Aufträgen in der Agentenwarteschlange steht. Schreibgeschützt.

**QueueStatusTime**: Ein Date-Wert, der die Zeit auf dem Server angibt, zu der die angezeigten Statuswerte abgerufen wurden. Der Wert entspricht dem Zeitpunkt, zu dem die Seite geladen wurde. Schreibgeschützt.

**QueueNextRetryTime**: Ein Date-Wert, der für blockierte Warteschlangen angibt, wann der nächste automatische erneute Versuch stattfindet. Wenn keine Zeit angezeigt wird, wird die Warteschlange nicht blockiert. Schreibgeschützt.

**QueueProcessingSince**: Ein Date-Wert, der angibt, wann die Verarbeitung für den aktuellen Auftrag begonnen hat. Wenn keine Zeit angezeigt wird, ist die Warteschlange entweder blockiert oder inaktiv. Schreibgeschützt.

**QueueLastProcessTime**: Ein Date-Wert, der angibt, wann der vorhergehende Auftrag abgeschlossen wurde. Schreibgeschützt.

### Betrieb {#operations-3}

**queueForceRetry**: Gibt bei blockierten Warteschlangen den Befehl zum erneuten Versuch an die Warteschlange aus.

* Argumente: keine
* Zurückgegebener Wert: keiner

**queueClear**: Entfernt alle Aufträge aus der Warteschlange.

* Argumente: keine
* Zurückgegebener Wert: keiner

## Sling-Engine {#sling-engine}

Stellt Statistiken zu HTTP-Anforderungen bereit, damit Sie die Leistung des SlingRequestProcessor-Dienstes überwachen können.

* Domain: org.apache.sling
* Typ: Motor
* Eigenschaften: {service=RequestProcessor}

### Attribute {#attributes-4}

**RequestsCount**: Die Anzahl an Abfragen, die seit dem letzten Zurücksetzen der Statistiken erfolgt sind.

**MinRequestDurationMsec**: Die kürzeste Zeitdauer (in Millisekunden), die für die Verarbeitung einer Abfrage seit dem letzten Zurücksetzen der Statistiken erforderlich war.

**MaxRequestDuratioMsec**: Die längste Zeitdauer (in Millisekunden), die für die Verarbeitung einer Abfrage seit dem letzten Zurücksetzen der Statistiken erforderlich war.

**StandardDeviationDurationMsec**: Die Standardabweichung von der Zeitdauer, die für die Verarbeitung von Abfragen erforderlich war. Diese Standardabweichung wird basierend auf allen Abfragen seit dem letzten Zurücksetzen der Statistiken ermittelt.

**MeanRequestDurationMsec**: Die Standardabweichung von der Zeitdauer, die für die Verarbeitung von Abfragen erforderlich war. Dieser Durchschnitt wird basierend auf allen Abfragen seit dem letzten Zurücksetzen der Statistiken ermittelt.

### Betrieb {#operations-4}

**resetStatistics**: Setzt alle Statistiken auf null zurück. Setzen Sie die Statistiken zurück, wenn Sie die Leistung der Anforderungsverarbeitung während eines bestimmten Zeitraums analysieren müssen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**id**: Die Zeichenfolgendarstellung der Paket-ID.

**installed**: Ein boolescher Wert, der angibt, ob das Paket installiert ist:

* `true`: installiert
* `false`: nicht installiert.

**installedBy**: Die ID der Benutzerin oder des Benutzers, die/der das Paket zuletzt installiert hat.

**installedDate**: Das Datum, an dem das Paket zuletzt installiert wurde.

**size**: Ein long-Wert, der die Größe des Pakets in Bytes angibt.


## Schnellstart-Starter {#quickstart-launcher}

Informationen zum Startprozess und zum Schnellstart-Starter.

* Domain: com.adobe.granite.quickstart
* Typ: Starter

### Betrieb {#operations-5}

**log**

Zeigt eine Meldung im QuickStart-Fenster an.

Argumente:

* p1: Ein `String`-Wert, der die anzuzeigende Meldung enthält.
* Zurückgegebener Wert: keiner

**startupFinished**

Ruft die Methode startupFinished des Server-Starters auf. Die -Methode versucht, die Begrüßungsseite in einem Webbrowser zu öffnen.

* Argumente: keine
* Zurückgegebener Wert: keiner

**startupProgress**

Legt den Abschlusswert des Serverstartprozesses fest. Die Fortschrittsleiste im QuickStart-Fenster stellt den Abschlusswert dar.

* Argumente:
   * p1: Ein Gleitkommawert, der angibt, wie viel des Startvorgangs als Bruchteil abgeschlossen ist. Der Wert muss zwischen null und eins liegen. 0,3 beispielsweise bedeutet, dass 30 % abgeschlossen sind.
* Zurückgegebener Wert: keiner.

## Drittanbieterdienste {#third-party-services}

Mehrere Serverressourcen von Drittanbietern installieren MBeans, die Attribute und Vorgänge der JMX-Konsole offenlegen. In der folgenden Tabelle sind die Drittanbieterressourcen aufgeführt und Links zu weiteren Informationen aufgeführt.

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
     <li>Kompilierung</li>
     <li>GarbageCollector</li>
     <li>Arbeitsspeicher</li>
     <li>MemoryManager</li>
     <li>MemoryPool</li>
     <li>OperatingSystem</li>
     <li>Laufzeit</li>
     <li>Threading</li>
    </ul> </td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/package-summary.html">javax.management</a>-Paket</td>
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
   <td><a href="https://osgi.org/specification/osgi.enterprise/7.0.0/service.jmx.html#d0e42567">org.osgi.jmx.framework</a>-Paket</td>
  </tr>
 </tbody>
</table>

## Verwenden der JMX-Konsole {#using-the-jmx-console}

Die JMX-Konsole zeigt Informationen zu mehreren Diensten an, die auf dem Server ausgeführt werden:

* Attribute: Diensteigenschaften wie Konfigurationen oder Laufzeitdaten. Attribute können schreibgeschützt oder schreibgeschützt sein.
* Vorgänge: Befehle, die Sie für den Dienst aufrufen können.

MBeans, die mit einem OSGi-Dienst bereitgestellt werden, übermitteln Dienstattribute und Vorgänge an die Konsole. Das MBean legt fest, welche Attribute und Vorgänge übermittelt werden und ob sie schreibgeschützt oder mit Lese- und Schreibzugriff versehen sind.

Die Hauptseite der JMX-Konsole enthält eine Tabelle der Dienste. Jede Zeile in der Tabelle stellt einen Dienst dar, der von einem MBean bereitgestellt wird.

1. Öffnen Sie die Web-Konsole und klicken Sie auf die Registerkarte JMX . ([http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
2. Klicken Sie auf einen Zellenwert für einen Dienst, um die Attribute und Vorgänge für den Dienst anzuzeigen.
3. Um einen Attributwert zu ändern, klicken Sie auf den Wert, geben Sie den Wert im angezeigten Dialogfeld an und klicken Sie auf Speichern.
4. Um einen Dienstvorgang aufzurufen, klicken Sie auf den Vorgangsnamen, geben Sie im angezeigten Dialogfeld Argumentwerte an und klicken Sie auf &quot;Aufrufen&quot;.

## Verwenden externer JMX-Anwendungen zur Überwachung {#using-external-jmx-applications-for-monitoring}

CRX ermöglicht es externen Anwendungen, mit Managed Beans (MBeans) über [Java Management Extensions (JMX)](https://docs.oracle.com/javase/6/docs/technotes/guides/management/overview.html). Verwenden generischer Konsolen wie [JConsole](https://java.sun.com/developer/technicalArticles/J2SE/jconsole.html) für domänenspezifische Überwachungsanwendungen, ermöglicht das Abrufen und Festlegen von CRX-Konfigurationen und -Eigenschaften sowie die Überwachung der Leistung und Ressourcennutzung.

### Verwenden von JConsole zur Verbindung mit CRX {#using-jconsole-to-connect-to-crx}

Gehen Sie wie folgt vor, um über JConsole eine Verbindung zu CRX herzustellen:

1. Öffnen Sie ein Terminal-Fenster.
1. Geben Sie den folgenden Befehl ein:

   `jconsole`

JConsole wird gestartet und das JConsole-Fenster wird angezeigt.

### Herstellen einer Verbindung zu einem lokalen CRX-Prozess {#connecting-to-a-local-crx-process}

JConsole zeigt eine Liste lokaler Java Virtual Machine-Prozesse an. Die Liste enthält zwei Schnellstartprozesse. Wählen Sie den Schnellstart-Prozess &quot;CHILD&quot;aus der Liste der lokalen Prozesse aus (normalerweise der mit der höheren PID).

![screen_shot_2012-03-26at114557am](assets/screen_shot_2012-03-26at114557am.png)

### Herstellen einer Verbindung zu einem Remote-CRX-Prozess {#connecting-to-a-remote-crx-process}

Um eine Verbindung zu einem Remote-CRX-Prozess herzustellen, muss die JVM, die den Remote-CRX-Prozess hostet, aktiviert sein, damit sie Remote-JMX-Verbindungen akzeptieren kann.

Um externe JMX-Verbindungen zu aktivieren, müssen Sie beim Starten der JVM die folgende Systemeigenschaft festlegen:

`com.sun.management.jmxremote.port=portNum`

In der o. g. Eigenschaft steht `portNum` für die Nummer des Ports, für den JMX-RMI-Verbindungen aktiviert werden sollen. Stellen Sie sicher, dass Sie eine nicht verwendete Anschlussnummer angeben. Durch Festlegen dieser Eigenschaft wird nicht nur ein RMI-Connector für den lokalen Zugriff veröffentlicht, sondern auch ein zusätzlicher RMI-Connector in einer privaten schreibgeschützten Registrierung am angegebenen Port veröffentlicht, wobei der bekannte Name &quot;jmxrmi&quot;verwendet wird.

Wenn Sie den JMX-Agenten für die Remote-Überwachung aktivieren, verwendet er standardmäßig die Kennwortauthentifizierung basierend auf einer Kennwortdatei, die beim Starten der Java VM mit der folgenden Systemeigenschaft angegeben werden muss:

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

Nach dem Herstellen einer Verbindung zum Schnellstartprozess stellt JConsole eine Reihe allgemeiner Überwachungstools für die JVM bereit, in der CRX ausgeführt wird.

![screen_shot_2012-03-26at115056am](assets/screen_shot_2012-03-26at115056am.png)

Um auf die internen Überwachungs- und Konfigurationsoptionen von CRX zuzugreifen, gehen Sie zur Registerkarte MBeans und wählen Sie in der hierarchischen Inhaltsstruktur auf der linken Seite den Bereich Attribute oder Vorgänge aus, den Sie interessieren. Beispielsweise den Abschnitt com.adobe.granite/Repository/Operations .

Wählen Sie in diesem Abschnitt das gewünschte Attribut oder den gewünschten Vorgang im linken Bereich aus.

![screen_shot_2012-03-26at115728am](assets/screen_shot_2012-03-26at115728am.png)
