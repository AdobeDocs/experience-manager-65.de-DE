---
title: Best Practices zur Überwachung der Bereitstellung von  [!DNL Assets]
description: Best Practices zur Überwachung der Umgebung und Leistung der Implementierung von [!DNL Adobe Experience Manager] nach der Bereitstellung.
contentOwner: AG
role: Admin, Architect
feature: Asset Management
exl-id: a9e1bd6b-c768-4faa-99a3-7110693998dc
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 45%

---

# Best Practices zur Überwachung der [!DNL Adobe Experience Manager Assets]-Bereitstellung {#assets-monitoring-best-practices}

Aus Sicht von [!DNL Experience Manager Assets] sollte die Überwachung das Beobachten und das Erstellen von Berichten für die folgenden Prozesse und Technologien umfassen:

* SystemCPU
* Systemspeicherauslastung
* IO- und IO-Wartezeit der Systemdiskette
* Systemnetzwerk-IO
* JMX MBeans für Heap-Nutzung und asynchrone Prozesse wie Workflows
* Integritätsprüfungen der OSGi-Konsole

Normalerweise kann die Überwachung in [!DNL Experience Manager Assets] auf zwei Arten durchgeführt werden: Live-Überwachung und Langzeitüberwachung.

## Live-Überwachung {#live-monitoring}

Sie sollten während der Leistungstestphase Ihrer Entwicklung oder in Situationen mit hoher Auslastung eine Live-Überwachung durchführen, um die Leistungsmerkmale Ihrer Umgebung zu verstehen. Normalerweise sollte die Live-Überwachung mit einer Suite von Tools durchgeführt werden. Hier einige Empfehlungen:

* [Visual VM](https://visualvm.github.io/): Mit Visual VM können Sie ausführliche Java-VM-Informationen anzeigen, z. B. CPU-Auslastung oder Java-Speicherauslastung. Außerdem können Sie Stichproben von Code nehmen und auswerten, der auf einer Bereitstellung ausgeführt wird.
* [Oben](https://man7.org/linux/man-pages/man1/top.1.html): Oben ist ein Linux-Befehl, der ein Dashboard öffnet, das Nutzungsstatistiken anzeigt, einschließlich CPU-, Speicher- und I/O-Nutzung. Er bietet einen allgemeinen Überblick darüber, was auf einer Instanz geschieht.
* [oberste](https://hisham.hm/htop/): Htop ist ein interaktiver Prozess-Viewer. Zusätzlich zu den von Top bereitgestellten Funktionen bietet es eine detaillierte CPU- und Speicherbelegung. „Htop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install htop` oder `apt-get install htop` installiert werden.

* Iotop: „Iotop“ ist ein ausführliches Dashboard für die I/O-Auslastung von Datenträgern. Darin werden anhand von Balken und Anzeigen die Prozesse, für die Datenträger-I/O-Vorgänge genutzt werden, sowie die verwendete Menge dargestellt. „Iotop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install iotop` oder `apt-get install iotop` installiert werden.

* [iftop](https://www.ex-parrot.com/pdw/iftop/): Wenn Sie detaillierte Informationen zur Ethernet-/Netzwerknutzung anzeigen. Iftop zeigt die Statistiken der einzelnen Kommunikationskanäle über die Entitäten an, die das Ethernet verwenden, und die Menge der von ihnen verwendeten Bandbreite. „Iftop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install iftop` oder `apt-get install iftop` installiert werden.

* Java Flight Recorder (JFR): Ein kommerzielles Tool von Oracle, das Sie in Umgebungen, die nicht für die Produktion bestimmt sind, kostenlos nutzen können. Ausführliche Informationen finden Sie unter [Verwenden von Java Flight Recorder zum Diagnostizieren von CQ-Laufzeitproblemen](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager]-Datei `error.log`: Sie können die [!DNL Experience Manager]-Datei `error.log` nach Details zu Fehlern durchsuchen, die im System protokolliert wurden. Verwenden Sie den Befehl `tail -F quickstart/logs/error.log`, um Fehler zu identifizieren, die untersucht werden müssen.
* [Workflow-Konsole](/help/sites-administering/workflows.md): Nutzen Sie die Workflow-Konsole, um Workflows zu überwachen, die Verzögerungen aufweisen oder hängen.

Normalerweise verwenden Sie diese Tools zusammen, um sich einen umfassenden Überblick über die Leistung Ihrer [!DNL Experience Manager]-Bereitstellung zu verschaffen.

>[!NOTE]
>
>Diese Tools sind Standardwerkzeuge und werden nicht direkt von Adobe unterstützt. Sie benötigen keine zusätzlichen Lizenzen.

![chlimage_1-33](assets/chlimage_1-143.png)

*Abbildung: Live-Überwachung mit dem Visual VM-Tool.*

![chlimage_1-32](assets/chlimage_1-142.png)

## Langzeitüberwachung {#long-term-monitoring}

Bei der Langzeitüberwachung einer [!DNL Experience Manager]-Bereitstellung werden die gleichen Komponenten, die live überwacht werden, auch über einen längeren Zeitraum überwacht. Sie umfasst auch die Definition von Warnhinweisen, die speziell für Ihre Umgebung gelten.

### Protokollaggregation und Reporting {#log-aggregation-and-reporting}

Es gibt verschiedene Tools zum Aggregieren von Protokollen, z. B. Splunk(TM) und Elastic Search, Logstash und Kabana (ELK). Zum Auswerten der Betriebszeit Ihrer [!DNL Experience Manager]-Bereitstellung ist es wichtig, dass Sie mit den jeweiligen Protokollereignissen Ihres Systems vertraut sind und basierend darauf Warnungen erstellen. Wenn Sie Ihre Entwicklungs- und Betriebsabläufe gut kennen, können Sie den Prozess der Protokollaggregation besser optimieren, um kritische Warnungen zu generieren.

### Umgebungsüberwachung {#environment-monitoring}

Die Umgebungsüberwachung umfasst die Überwachung folgender Elemente:

* Netzwerkdurchsatz
* Datenträger-E
* Arbeitsspeicher
* CPU-Auslastung
* JMX MBeans
* Externe Websites

Sie benötigen externe Tools wie NewRelic(TM) und AppDynamics(TM), um jedes Element zu überwachen. Mithilfe dieser Tools können Sie systemspezifische Warnhinweise definieren, z. B. hohe Systemauslastung, Workflow-Sicherung, Fehler bei der Konsistenzprüfung oder nicht authentifizierten Zugriff auf Ihre Website. Adobe empfiehlt keine speziellen Tools. Suchen Sie nach dem Tool, das für Sie funktioniert, und verwenden Sie es, um die diskutierten Elemente zu überwachen.

#### Interne Anwendungsüberwachung {#internal-application-monitoring}

Die interne Anwendungsüberwachung umfasst das Überwachen der Anwendungskomponenten, aus denen der [!DNL Experience Manager]-Stapel besteht, z. B. JVM, das Inhalts-Repository und die Überwachung mit benutzerdefiniertem Anwendungs-Code, der auf der Plattform erstellt wird. Im Allgemeinen wird sie über JMX MBeans durchgeführt, die direkt von vielen beliebten Überwachungslösungen wie SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) und anderen überwacht werden können. Für Systeme, die keine direkte Verbindung zu JMX unterstützen, können Sie Shell-Skripte schreiben, um die JMX-Daten zu extrahieren und für diese Systeme in einem Format verfügbar zu machen, das sie nativ verstehen.

Der Remotezugriff auf die JMX MBeans ist standardmäßig nicht aktiviert. Weitere Informationen zur Überwachung per JMX finden Sie unter [Überwachung und Verwaltung per JMX-Technologie](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

In vielen Fällen ist eine Grundlinie erforderlich, um eine Statistik effektiv zu überwachen. Um eine Grundlinie zu erstellen, beobachten Sie das System unter normalen Arbeitsbedingungen für einen vorab festgelegten Zeitraum und identifizieren Sie dann die normale Metrik.

**JVM-Überwachung**

Wie alle Java-basierten Anwendungsstapel ist auch [!DNL Experience Manager] von den Ressourcen abhängig, die über die zugrunde liegende Java Virtual Machine bereitgestellt werden. Sie können den Status vieler dieser Ressourcen über Platform MXBeans überwachen, die von JVM verfügbar gemacht werden. Weitere Informationen zu MXBeans finden Sie unter [Verwenden von Platform MBean Server und Platform MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Hier sind einige Baseline-Parameter angegeben, die Sie für JVM überwachen können:

Arbeitsspeicher

* `MBean: lava.lang:type=Memory`
* URL: `/system/console/jmx/java.lang:type=Memory`
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Heap- oder Nicht-Heap-Speicherauslastung 75 % des entsprechenden maximalen Speichers überschreitet.
* Alarmdefinition: Entweder der Systemspeicher reicht nicht aus oder der Code enthält einen Speicherleck. Analysieren Sie einen Thread-Dump, um zu einer Definition zu gelangen.

>[!NOTE]
>
>Die von diesem Bean-Element gelieferten Informationen werden in Byte ausgedrückt.

Threads

* MBean: `java.lang:type=Threading`
* URL: `/system/console/jmx/java.lang:type=Threading`
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Anzahl der Threads größer ist als 150 % der Baseline.
* Alarmdefinition: Entweder gibt es einen aktiven Runaway-Prozess oder ein ineffizienter Vorgang verbraucht eine große Menge an Ressourcen. Analysieren Sie einen Thread-Dump, um zu einer Definition zu gelangen.

**Überwachen von[!DNL Experience Manager]**

[!DNL Experience Manager] stellt über JMX auch einen Satz mit Statistiken und Vorgängen bereit. Diese Daten können dazu beitragen, die Systemintegrität zu bewerten und potenzielle Probleme zu identifizieren, bevor sie für Benutzende eine Beeinträchtigung darstellen. Weitere Informationen finden Sie in der [Dokumentation](/help/sites-administering/jmx-console.md) zu [!DNL Experience Manager] JMX MBeans.

Hier sind einige Baseline-Parameter angegeben, die Sie für [!DNL Experience Manager] überwachen können:

Replikationsagenten

* MBean: `com.adobe.granite.replication:type=agent,id="<AGENT_NAME>"`
* URL: `/system/console/jmx/com.adobe.granite.replication:type=agent,id="<AGENT_NAME>"`
* Instanzen: Eine Autoren- und alle Veröffentlichungsinstanzen (für Flush-Agenten)
* Alarmschwellenwert: Wenn der Wert von `QueueBlocked` `true` lautet oder der Wert von `QueueNumEntries` größer als 150 % der Baseline ist.

* Alarmdefinition: Vorhandensein einer blockierten Warteschlange im System, die angibt, dass das Replikationsziel ausfällt oder nicht erreichbar ist. Häufig führen Netzwerk- oder Infrastrukturprobleme dazu, dass übermäßige Einträge in die Warteschlange gestellt werden, was die Systemleistung beeinträchtigen kann.

>[!NOTE]
>
>Ersetzen Sie für die MBean- und URL-Parameter `<AGENT_NAME>` durch den Namen des Replikationsagenten, den Sie überwachen möchten.

Sitzungszähler

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn geöffnete Sitzungen die Grundlinie um mehr als 50 % überschreiten.
* Alarmdefinition: Sitzungen können durch einen Code geöffnet und nie geschlossen werden. Dies kann im Laufe der Zeit langsam passieren und schließlich zu Speicherlecks im System führen. Während die Anzahl der Sitzungen in einem System schwanken sollte, sollten sie nicht kontinuierlich steigen.

Konsistenzprüfungen

Konsistenzprüfungen, die im [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md#health-reports) über entsprechende JMX MBeans zur Überwachung verfügen. Sie können jedoch benutzerdefinierte Konsistenzprüfungen schreiben, um zusätzliche Systemstatistiken verfügbar zu machen.

Im Folgenden finden Sie einige vordefinierte Konsistenzprüfungen, die zur Überwachung hilfreich sind:

* Systemprüfungen
   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Weitere Informationen zur Ursache des Problems finden Sie im Protokollattribut.

* Replikations-Warteschlange

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Überprüfen Sie das Protokollattribut auf weitere Informationen zur Warteschlange, die das Problem verursacht hat.

* Antwortleistung

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * Instanzen: Alle Server
   * Alarmdauer: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Überprüfen Sie das Protokollattribut auf weitere Informationen zur Warteschlange, die das Problem verursacht hat.

* Abfrageleistung

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus,type=HealthCheck`
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Eine oder mehrere Abfragen, die langsam im System ausgeführt werden. Weitere Informationen zu den Abfragen, die das Problem verursacht haben, finden Sie im Protokollattribut .

* Aktive Bundles

   * MBean: `org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Vorhandensein von inaktiven oder nicht aufgelösten OSGi-Bundles im System. Weitere Informationen zu den Bundles, die das Problem verursacht haben, finden Sie im Protokollattribut .

* Fehlerprotokoll

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Die Protokolldateien enthalten Fehler. Weitere Informationen zur Ursache des Problems finden Sie im Protokollattribut.

## Häufige Probleme und Lösungen  {#common-issues-and-resolutions}

Wenn während des Überwachungsprozesses Probleme auftreten, können Sie die folgenden Problembehandlungsschritte ausführen, um häufig auftretende Probleme mit einer [!DNL Experience Manager]-Bereitstellung zu lösen:

* Führen Sie die Tar-Komprimierung häufig durch, falls Sie TarMK nutzen. Weitere Informationen finden Sie unter [Verwalten des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* Überprüfen Sie die `OutOfMemoryError`-Protokolle. Weitere Informationen finden Sie unter [Analysieren von Speicherproblemen](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17482.html?lang=de).

* Überprüfen Sie die Protokolle auf Verweise auf unindizierte Abfragen, Baumdurchläufe oder Indexdurchläufe. Diese weisen auf nicht indizierte Abfragen oder unzureichend indizierte Abfragen hin. Best Practices zur Optimierung der Abfrage- und Indizierungsleistung finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Überprüfen Sie mithilfe der Workflow-Konsole, ob Ihre Workflows erwartungsgemäß funktionieren. Schließen Sie nach Möglichkeit mehrere Workflows in einen einzigen Workflow zusammen.
* Suchen Sie über die Live-Überwachung nach weiteren Engpässen oder einem hohen Verbrauch bestimmter Ressourcen.
* Untersuchen Sie die Ausgangspunkte des Client-Netzwerks und die Eingangspunkte des [!DNL Experience Manager]-Bereitstellungsnetzwerks, einschließlich Dispatcher. Häufig handelt es sich um Engpässe. Weitere Informationen finden Sie unter [Überlegungen zum Assets-Netzwerk](/help/assets/assets-network-considerations.md).
* Vergrößern Sie den [!DNL Experience Manager]-Server. Unter Umständen verfügen Sie über eine [!DNL Experience Manager]-Bereitstellung mit unzureichender Größe. Der Adobe Kunden-Support kann Sie dabei unterstützen, festzustellen, ob Ihr Server ggf. zu klein ausgelegt ist.
* Untersuchen Sie die Dateien `access.log` und `error.log` auf Einträge, die zu Fehlerzeitpunkten erstellt wurden. Suchen Sie nach Mustern, die möglicherweise auf benutzerdefinierte Code-Anomalien hinweisen. Fügen Sie sie zur Liste der Ereignisse hinzu, die Sie überwachen.
