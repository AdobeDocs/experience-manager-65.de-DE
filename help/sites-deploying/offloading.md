---
title: Abladen von Aufträgen
seo-title: Abladen von Aufträgen
description: Erfahren Sie, wie Sie AEM-Instanzen in einer Topologie konfigurieren und verwenden, um bestimmte Verarbeitungsaufgaben auszuführen.
seo-description: Erfahren Sie, wie Sie AEM-Instanzen in einer Topologie konfigurieren und verwenden, um bestimmte Verarbeitungsaufgaben auszuführen.
uuid: e971d403-dfd2-471f-b23d-a67e35f1ed88
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 370151df-3b8e-41aa-b586-5c21ecb55ffe
feature: Konfiguration
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2404'
ht-degree: 75%

---


# Abladen von Aufträgen{#offloading-jobs}

## Einführung {#introduction}

Durch das Verteilen werden verarbeitende Aufgaben in einer Topologie auf verschiedene Experience Manager verteilt. Mit der Abladung können Sie bestimmte Experience Manager-Instanzen zur Durchführung bestimmter Verarbeitungsarten verwenden. Mit dieser gezielten Verarbeitung kann die Nutzung der verfügbaren Serverressourcen maximiert werden.

Die Abladung basiert auf den [Discovery](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html)- und JobManager-Funktionen von Apache Sling. Zur Verwendung des Offloading fügen Sie einer Topologie Experience Manager-Cluster hinzu und identifizieren die Auftragsthemen, die vom Cluster verarbeitet werden. Cluster bestehen aus einer oder mehr Experience Manager-Instanzen, sodass eine Instanz als Cluster gilt.

Weitere Informationen zum Hinzufügen von Instanzen zu einer Topologie finden Sie unter [Verwalten von Topologien](/help/sites-deploying/offloading.md#administering-topologies).

### Auftragsverteilung {#job-distribution}

Mit den JobManager- und JobConsumer-Diensten von Apache Sling können Aufträge erstellt werden, die in einer Topologie verarbeitet werden:

* JobManager: Ein Dienst, der Aufträge für bestimmte Themen erstellt.
* JobConsumer: Ein Dienst, der Aufträge für ein oder mehrere Themen ausführt. Es können mehrere JobConsumer-Dienste für dasselbe Thema registriert werden.

Wenn der JobManager-Dienst einen Auftrag erstellt, wählt das Abladungs-Framework einen Experience Manager-Cluster in der Topologie aus, um diesen auszuführen:

* Der Cluster muss eine oder mehr Instanzen umfassen, auf denen ein für das Auftragsthema registrierter JobConsumer-Dienst ausgeführt wird.
* Das Thema muss für mindestens eine Instanz im Cluster aktiviert sein.

Weitere Informationen zur Optimierung der Auftragsverteilung finden Sie unter [Konfigurieren der Themenverarbeitung](/help/sites-deploying/offloading.md#configuring-topic-consumption).

![chlimage_1-109](assets/chlimage_1-109.png)

Wenn das Offloading-Framework einen Cluster auswählt, um einen Auftrag auszuführen, und der Cluster aus mehreren Instanzen besteht, bestimmt die Sling-Verteilung, welche Instanz im Cluster den Auftrag ausführt.

### Auftrags-Payloads {#job-payloads}

Das Abladungs-Framework unterstützt Auftrags-Payloads, die Aufträge mit Ressourcen im Repository verknüpfen. Auftrags-Payloads sind hilfreich, wenn Aufträge für Verarbeitungsressourcen erstellt werden und der Auftrag an einen anderen Computer abgeladen wird.

Bei der Erstellung eines Auftrags befindet sich die Payload nur auf der Instanz, die den Auftrag erstellt. Beim Abladen des Auftrags stellen Replikationsagenten sicher, dass die Payload auf der Instanz erstellt wird, die den Auftrag schließlich verarbeitet. Nach Ausführung des Auftrags sorgt die Rückwärtsreplikation dafür, dass die Payload wieder auf die Instanz zurück kopiert wird, die den Auftrag erstellt hat.

## Verwalten von Topologien {#administering-topologies}

Topologien sind lose verknüpfte Experience Manager-Cluster, die an der Abladung beteiligt sind. Ein Cluster besteht aus einer oder mehreren Experience Manager-Serverinstanzen (eine einzelne Instanz wird als Cluster betrachtet).

Jede Experience Manager-Instanz führt die folgenden abladungsbezogenen Dienste aus:

* Discovery-Dienst: Sendet Anfragen an einen Topologie-Connector, um Mitglied einer Topologie zu werden.
* Topologie-Connector: Empfängt die Mitgliedschaftsanfragen und akzeptiert oder lehnt sie ab.

Der Discovery-Dienst aller Topologiemitglieder verweist auf den Topologie-Connector eines der Mitglieder. Im nachfolgenden Abschnitt wird dieses Mitglied als Stamm-Mitglied bezeichnet.

![chlimage_1-110](assets/chlimage_1-110.png)

Jeder Cluster in der Topologie enthält eine Instanz, die als Leader erkannt wird. Der Cluster-Leader interagiert für die anderen Cluster-Mitglieder mit der Topologie. Wenn der Leader den Cluster verlässt, wird automatisch ein neuer Leader ausgewählt.

### Anzeigen der Topologie  {#viewing-the-topology}

Mit dem Topologie-Browser können Sie den Status der Topologie überprüfen, zu der die Experience Manager-Instanz gehört. Der Topologie-Browser zeigt die Cluster und Instanzen der Topologie.

Für jeden Cluster sehen Sie eine Liste von Clustermitgliedern, die die Reihenfolge angibt, in der die einzelnen Mitglieder dem Cluster beigetreten sind, und welches Mitglied der Leader ist. Die Eigenschaft „Aktuell“ gibt die Instanz an, die Sie derzeit verwalten.

Für jede Instanz des Clusters werden verschiedene topologiebezogene Eigenschaften angezeigt:

* Eine Zulassungsliste von Themen für den Jobkonsumenten der Instanz.
* Die Endpunkte, die für die Verbindung mit der Topologie verfügbar gemacht werden
* Die Auftragsthemen, für die die Instanz für die Abladung registriert ist
* Die von der Instanz verarbeiteten Auftragsthemen

1. Klicken Sie auf der Touch-optimierten Benutzeroberfläche auf die Registerkarte „Tools“. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klicken Sie im Bereich „Granite-Vorgänge“ auf „Browser-Abladung“.
1. Klicken Sie im Navigationsfenster auf „Topologie-Browser“.

   Die zur Topologie gehörenden Cluster werden angezeigt.

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. Klicken Sie auf einen Cluster, um eine Liste der Instanzen im Cluster und deren ID, aktuellen Status und Leader-Status anzuzeigen.
1. Klicken Sie auf eine Instanzen-ID, um detaillierte Eigenschaften anzuzeigen.

Sie können auch die Web-Konsole zum Anzeigen von Topologie-Informationen verwenden. Die Konsole stellt weitere Informationen zu den Topologie-Clustern bereit:

* Welche Instanz die lokale Instanz ist
* Die Topologie-Connector-Dienste, über die die Instanz eine Verbindung zur Topologie herstellt (ausgehend), und die Dienste, die eine Verbindung mit dieser Instanz herstellen (eingehend)
* Ändern Sie den Verlauf für die Eigenschaften der Topologie und Instanz.

Gehen Sie wie folgt vor, um die Seite „Topology Management“ der Web-Konsole zu öffnen:

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf „Main“ > „Topology Management“.

   ![chlimage_1-112](assets/chlimage_1-112.png)

### Konfigurieren der Topologie-Mitgliedschaft {#configuring-topology-membership}

Der ressourcenbasierte Apache Sling-Discovery-Dienst wird auf jeder Instanz ausgeführt und steuert, wie Experience Manager-Instanzen mit einer Topologie interagieren.

Der Discovery-Dienst sendet regelmäßig POST-Anforderungen (Heartbeats) an Topologie-Connector-Dienste, um Verbindungen mit der Topologie herzustellen und aufrechtzuerhalten. Der Topology Connector-Dienst verwaltet eine Zulassungsliste von IP-Adressen oder Hostnamen, die der Topologie beitreten dürfen:

* Um eine Instanz zum Topologie-Mitglied zu machen, geben Sie die URL für den Topologie-Connector-Dienst des Stamm-Mitglieds an.
* Um einer Instanz zu ermöglichen, Topologie-Mitglied zu werden, fügen Sie die Instanz der Zulassungsliste für den Topologie-Connector-Dienst des Stammmitglieds hinzu.

Verwenden Sie die Web-Konsole oder einen „slign:OsgiConfig“-Knoten, um die folgenden Eigenschaften des Dienstes „org.apache.sling.discovery.impt.Config“ zu konfigurieren:

<table>
 <tbody>
  <tr>
   <th>Eigenschaftsname</th>
   <th>OSGi-Name</th>
   <th>Beschreibung</th>
   <th>Standardwert</th>
  </tr>
  <tr>
   <td>Heartbeat-Timeout (Sekunden)</td>
   <td>heartbeatTimeout</td>
   <td>Die Zeit in Sekunden, die auf eine Heartbeat-Antwort gewartet wird, bevor die Targeting-Instanz als nicht verfügbar betrachtet wird. </td>
   <td>20</td>
  </tr>
  <tr>
   <td>Heartbeat-Intervall (Sekunden)</td>
   <td>heartbeatInterval</td>
   <td>Die Zeit in Sekunden zwischen Heartbeats.</td>
   <td>15</td>
  </tr>
  <tr>
   <td>Minimale Ereignis-Verzögerung (Sekunden)</td>
   <td>minEventDelay</td>
   <td><p>Wenn eine Änderung an der Topologie eintritt, die Zeitdauer, um die Änderung des Status von TOPOLOGY_CHANGING zu TOPOLOGY_CHANGED zu verzögern. Jede Änderung, die auftritt, wenn der Status TOPOLOGY_CHANGING lautet, erhöht die Verzögerung um diesen zeitlichen Wert.</p> <p>Diese Verzögerung verhindert, dass Listener von Ereignissen überflutet werden. </p> <p>Soll keine Verzögerung verwendet werden, geben Sie „0“ oder eine negative Zahl an.</p> </td>
   <td>3</td>
  </tr>
  <tr>
   <td>Topologie-Connectoren-URLs</td>
   <td>topologyConnectorUrls</td>
   <td>Die URLs der Topologie-Connector-Dienste zum Senden von Heartbeat-Nachrichten.</td>
   <td>http://localhost:4502/libs/sling/topology/connector</td>
  </tr>
  <tr>
   <td>Topology Connector-Zulassungsliste</td>
   <td>topologyConnectorWhitelist</td>
   <td>Die Liste von IP-Adressen oder Host-Namen, die der lokale Topologie-Connector-Dienst in der Topologie zulässt. </td>
   <td><p>localhost</p> <p>127.0.0.1</p> </td>
  </tr>
  <tr>
   <td>Repository-Beschreibungsname</td>
   <td>leaderElectionRepositoryDescriptor</td>
   <td> </td>
   <td>&lt;kein Wert&gt;</td>
  </tr>
 </tbody>
</table>

Gehen Sie wie folgt vor, um eine CQ-Instanz mit dem Stamm-Mitglied einer Topologie zu verbinden. Die Instanz verweist dann auf die Topologie-Connector-URL des Stamm-Mitglieds der Topologie. Führen Sie diese Schritte für alle Topologiemitglieder durch.

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf „Main“ > „Topology Management“.
1. Klicken Sie auf „Configure Discovery Service“.
1. Fügen Sie ein Element zur Eigenschaft „Topology Connector URLs“ hinzu und geben Sie die URL des Topologie-Connector-Dienstes für das Stamm-Mitglied der Topologie an. Die URL hat das Format https://rootservername:4502/libs/sling/topology/connector.

Führen Sie die folgenden Schritte für das Stamm-Mitglied der Topologie aus. Dadurch werden die Namen der anderen Topologiemitglieder der Zulassungsliste für den Discovery-Dienst hinzugefügt.

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf „Main“ > „Topology Management“.
1. Klicken Sie auf „Configure Discovery Service“.
1. Fügen Sie für jedes Mitglied der Topologie der Eigenschaft Topology Connector-Zulassungsliste ein Element hinzu und geben Sie den Hostnamen oder die IP-Adresse des Topologieelements an.

## Konfigurieren der Themenverarbeitung {#configuring-topic-consumption}

Verwenden Sie die Browser-Abladung, um die Themenverarbeitung für die Experience Manager-Instanzen in der Topologie zu konfigurieren. Sie können die von jeder Instanz verarbeiteten Themen angeben. Beispiel: Um die Topologie so zu konfigurieren, dass nur eine Instanz einen bestimmten Thementyp verarbeitet, deaktivieren Sie das Thema auf allen Instanzen bis auf eine.

Aufträge werden auf Instanzen verteilt, bei denen das zugehörige Thema mithilfe der Round-Robin-Logik aktiviert wurde.

1. Klicken Sie auf der Touch-optimierten Benutzeroberfläche auf die Registerkarte „Tools“. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klicken Sie im Bereich „Granite-Vorgänge“ auf „Browser-Abladung“.
1. Klicken Sie im Navigationsfenster auf „Browser-Abladung“.

   Die Abladungsthemen und die Serverinstanzen, die die Themen verarbeiten können, werden angezeigt.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Um den Verbrauch eines Themas für eine Instanz zu deaktivieren, klicken Sie unter dem Themennamen neben der Instanz auf Deaktivieren.
1. Um die Verarbeitung aller Themen für eine Instanz zu konfigurieren, klicken Sie auf die Instanz-ID unter einem beliebigen Thema.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Klicken Sie auf eine der folgenden Schaltflächen neben einem Thema, um das Verarbeitungsverhalten für die Instanz zu konfigurieren. Klicken Sie dann auf „Speichern“:

   * Aktiviert: Diese Instanz verarbeitet Aufträge für dieses Thema.
   * Deaktiviert: Diese Instanz verarbeitet keine Aufträge für dieses Thema.
   * Exklusiv: Diese Instanz verarbeitet nur Aufträge für dieses Thema.

   **Hinweis:** Wenn Sie die Option „Exklusiv“ für ein Thema auswählen, werden alle anderen Themen automatisch auf „Deaktiviert“ gesetzt.

### Installierte JobConsumer-Dienste  {#installed-job-consumers}

Die Installation von Experience Manager umfasst mehrere implementierte JobConsumer-Dienste. Die Themen, für die diese JobConsumer-Dienste registriert sind, werden in der Browser-Abladung angezeigt. Bei den weiteren angezeigten Themen handelt es sich um von benutzerdefinierten JobConsumer-Diensten registrierte Themen. Die nachfolgende Tabelle beschreibt die Standard-JobConsumer-Dienste.

| Auftragsthema | Dienst-PID | Beschreibung |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | Mit Apache Sling installiert. Verarbeitet Aufträge, die vom OSGi-Event-Admin-Dienst aus Gründen der Abwärtskompatibilität generiert werden. |
| com/day/cq/Replication/job/&amp;ast; | com.day.cq.replication.impl.AgentManagerImpl | Ein Replizierungsagenten, der Auftragsnutzlasten repliziert. |

<!--
| com/adobe/granite/workflow/offloading |com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer |Processes jobs that the DAM Update Asset Offloader workflow generates. |
-->

### Deaktivieren und Aktivieren von Themen für eine Instanz {#disabling-and-enabling-topics-for-an-instance}

Der Dienst „Apache Sling Job Consumer Manager“ stellt Eigenschaften für Themen der Zulassungs- und Blockierungsliste bereit. Konfigurieren Sie diese Eigenschaften, um die Verarbeitung von bestimmten Themen auf einer Experience Manager-Instanz zu aktivieren oder zu deaktivieren.

**Hinweis:** Wenn die Instanz zu einer Topologie gehört, können Sie den Offload-Browser auch auf einem beliebigen Computer in der Topologie verwenden, um Themen zu aktivieren oder zu deaktivieren.

Die Logik, die die Liste der aktivierten Themen erstellt, erlaubt zunächst alle Themen, die sich auf der Zulassungsliste befinden, und entfernt dann Themen, die sich auf der Blockierungsliste befinden. Standardmäßig sind alle Themen aktiviert (der Wert für die Zulassungsliste ist `*`) und keine Themen sind deaktiviert (die Blockierungsliste hat keinen Wert).

Verwenden Sie die Web-Konsole oder einen `sling:OsgiConfig`-Knoten, um die folgenden Eigenschaften zu konfigurieren. Für `sling:OsgiConfig`-Knoten lautet die PID des JobConsumerManager-Dienstes „org.apache.sling.event.impl.jobs.JobConsumerManager“.

| Eigenschaftsname in der Web-Konsole | OSGi-ID | Beschreibung |
|---|---|---|
| Zulassungsliste | job.consumermanager.whitelist | Eine Liste von Themen, die vom lokalen JobManager-Dienst verarbeitet werden. Der Standardwert von &amp;ast; bewirkt, dass alle Themen an den registrierten TopicConsumer-Dienst gesendet werden. |
| Blockierungsliste | job.consumermanager.blacklist | Eine Liste der Themen, die nicht vom JobManager-Dienst verarbeitet werden. |

## Erstellen von Replikationsagenten für die Abladung {#creating-replication-agents-for-offloading}

Das Abladungs-Framework überträgt Ressourcen mittels Replikation zwischen Autoren- und Worker-Instanzen. Das Framework erstellt automatisch Replikationsagenten, wenn Instanzen Mitglied der Topologie werden. Die Agenten werden mit Standardwerten erstellt. Das von den Agenten zur Authentifizierung verwendete Kennwort muss manuell geändert werden.

>[!CAUTION]
>
>Es ist ein bekanntes Problem bei automatisch generierten Replikationsagenten, dass neue Agenten manuell erstellt werden müssen. Befolgen Sie das unter [Probleme bei der Verwendung automatisch generierter Replikationsagenten](/help/sites-deploying/offloading.md#problems-using-the-automatically-generated-replication-agents) beschriebene Verfahren, bevor Sie die Agenten für die Abladung erstellen.

Erstellen Sie die Replikationsagenten, die Auftrags-Payloads zwischen Instanzen für die Abladung übertragen. Die nachfolgende Darstellung zeigt die erforderlichen Agenten für die Abladung von der Autoren- an die Worker-Instanz. Der Autor hat eine Sling-ID von 1 und die Worker-Instanz hat eine Sling-ID von 2:

![chlimage_1-115](assets/chlimage_1-115.png)

Für diese Konfiguration sind die folgenden drei Agenten erforderlich:

1. Ein ausgehender Agent auf der Autoreninstanz, der eine Replikation auf der Worker-Instanz durchführt
1. Ein Rückwärtsagent auf der Autoreninstanz, der aus dem Postausgang auf der Worker-Instanz abruft
1. Einen Postausgang-Agent auf der Worker-Instanz

Dieses Replikationsschema gleicht dem für Autoren- und Veröffentlichungsinstanzen verwendeten. Bei der Abladung sind jedoch alle beteiligten Instanzen Autoreninstanzen.

>[!NOTE]
>
>Das Abladungs-Framework nutzt die Topologie zum Abrufen der IP-Adressen der Abladungsinstanzen. Basierend auf diesen IP-Adressen erstellt das Framework dann automatisch die Replikationsagenten. Wenn sich die IP-Adressen der Ablade-Instanzen später ändern, wird die Änderung nach dem Neustart der Instanz automatisch in der Topologie übernommen. Das Abladungs-Framework aktualisiert jedoch nicht automatisch die Replikationsagenten mit den neuen IP-Adressen. Um dies zu vermeiden, verwenden Sie feste IP-Adressen für alle Instanzen in der Topologie.

### Benennen der Replikationsagenten für die Abladung {#naming-the-replication-agents-for-offloading}

Verwenden Sie ein bestimmtes Format für die Eigenschaft ***Name*** der Replizierungsagenten, damit das Ablade-Framework automatisch den richtigen Agenten für bestimmte Workerinstanzen verwendet.

**Benennung des ausgehenden Agenten auf der Autoreninstanz:**

`offloading_<slingid>`, wobei  `<slingid>` die Sling-ID der Worker-Instanz steht.

Beispiel: `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**Benennung des Rückwärtsagenten auf der Autoreninstanz:**

`offloading_reverse_<slingid>`, wobei  `<slingid>` die Sling-ID der Worker-Instanz steht.

Beispiel: `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**Benennung des Postausgangs auf der Worker-Instanz:**

`offloading_outbox`

### Erstellen des ausgehenden Agenten {#creating-the-outgoing-agent}

1. Erstellen Sie einen **Replikationsagenten** auf der Autoreninstanz. (Siehe die [Dokumentation für Replizierungsagenten](/help/sites-deploying/replication.md)). Geben Sie einen beliebigen **Titel an**. **Name** muss der Benennungsregel entsprechen.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften:

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Default |
   | Transport > Transport-URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transportbenutzer | Replizierungsbenutzer auf Zielgruppe-Instanz |
   | Transport > Transportkennwort | Replizieren des Benutzerkennworts auf der Zielgruppe |
   | Erweitert > HTTP-Methode | POST |
   | Trigger > Standard ignorieren | True |

### Erstellen des Rückwärtsagenten {#creating-the-reverse-agent}

1. Erstellen Sie einen **Agenten für Rückwärtsreplikation** beim Autor. (Siehe die [Dokumentation für Replizierungsagenten](/help/sites-deploying/replication.md).) Geben Sie einen beliebigen **Titel an**. **Name** muss der Benennungsregel entsprechen.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften:

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Standard |
   | Transport > Transport-URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transportbenutzer | Replizierungsbenutzer auf Zielgruppe-Instanz |
   | Transport > Transportkennwort | Replizieren des Benutzerkennworts auf der Zielgruppe |
   | Erweitert > HTTP-Methode | GET |

### Erstellen des Postausgangs-Agenten {#creating-the-outbox-agent}

1. Erstellen Sie einen **Replizierungsagenten** auf der Worker-Instanz. (Siehe die [Dokumentation für Replizierungsagenten](/help/sites-deploying/replication.md).) Geben Sie einen beliebigen **Titel an**. **Name** muss `offloading_outbox` sein.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften.

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Standard |
   | Transport > Transport-URI | repo://var/replication/outbox |
   | Trigger > Standard ignorieren | true |

### Suche nach der Sling-ID {#finding-the-sling-id}

Sie können die Sling-ID einer Experience Manager-Instanz mit einer der beiden folgenden Methoden abrufen:

* Öffnen Sie die Web-Konsole und suchen Sie in den Sling-Einstellungen den Wert der Sling-ID-Eigenschaft ([http://localhost:4502/system/console/status-slingsettings](http://localhost:4502/system/console/status-slingsettings)). Diese Methode ist nützlich, wenn die Instanz noch nicht Teil der Topologie ist.
* Ist sie bereits Teil der Topologie, verwenden Sie den Topologie-Browser.

<!--
## Offloading the Processing of DAM Assets {#offloading-the-processing-of-dam-assets}

Configure the instances of a topology so that specific instances perform the background processing of assets that are added or updated in DAM.

By default, Experience Manager executes the [!UICONTROL DAM Update Asset] workflow when a DAM asset changes or one is added to DAM. Change the default behavior so that Experience Manager instead executes the [!UICONTROL DAM Update Asset Offloader] workflow. This workflow generates a JobManager job that has a topic of `com/adobe/granite/workflow/offloading`. Then, configure the topology so that the job is offloaded to a dedicated worker.

>[!CAUTION]
>
>No workflow should be transient when used with workflow offloading. For example, the [!UICONTROL DAM Update Asset] workflow must not be transient when used for asset offloading. To set/unset the transient flag on a workflow, see [Transient Workflows](/help/assets/performance-tuning-guidelines.md#workflows).

The following procedure assumes the following characteristics for the offloading topology:

* One or more Experience Manager instance are authoring instances that users interact with for adding or updating DAM assets.
* Users to do not directly interact with one or more Experience Manager instances that process the DAM assets. These instances are dedicated to the background processing of DAM assets.

1. On each Experience Manager instance, configure the Discovery Service so that it points to the root Topography Connector. (See [Configuring Topology Membership](#title4).)
1. Configure the root Topography Connector so that the connecting instances are on the allow list.
1. Open Offloading Browser and disable the `com/adobe/granite/workflow/offloading` topic on the instances with which users interact to upload or change DAM assets.

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. On each instance that users interact with to upload or change DAM assets, configure workflow launchers to use the [!UICONTROL DAM Update Asset Offloading] workflow:

    1. Open the Workflow console.
    1. Click the Launcher tab.
    1. Locate the two Launcher configurations that execute the [!UICONTROL DAM Update Asset] workflow. One launcher configuration event type is Node Created, and the other type is Node Modified.
    1. Change both event types so that they execute the [!UICONTROL DAM Update Asset Offloading] workflow. (For information about launcher configurations, see [Starting Workflows When Nodes Change](/help/sites-administering/workflows-starting.md).)

1. On the instances that perform the background processing of DAM assets, disable the workflow launchers that execute the [!UICONTROL DAM Update Asset] workflow.
-->

## Weiterführende Literatur {#further-reading}

Neben den auf dieser Seite bereitgestellten, detaillierten Informationen können Sie auch folgende Abschnitte lesen:

* Weitere Informationen zur Verwendung von Java-APIs zum Erstellen von Aufträgen und zum Erstellen von Auftraggebern finden Sie unter [Erstellen und Verarbeiten von Aufträgen für das Verladen](/help/sites-developing/dev-offloading.md).
