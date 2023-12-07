---
title: Überwachen von AEM Forms-Bereitstellungen
description: Sie können Formularbereitstellungen von AEM sowohl auf Systemebene als auch auf interner Ebene überwachen. Erfahren Sie mehr über das Überwachen von AEM Forms-Bereitstellungen für dieses Dokument.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 931e8095-5c7c-4c1f-b95b-75ac2827d4f3
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 100%

---

# Überwachen von AEM Forms-Bereitstellungen {#monitoring-aem-forms-deployments}

Sie können Formularbereitstellungen von AEM sowohl auf Systemebene als auch auf interner Ebene überwachen. Sie können spezialisierte Verwaltungstools wie HP OpenView, IBM® Tivoli und CA UniCenter sowie einen JMX-Monitor eines Drittanbieters namens *JConsole* verwenden, um speziell Java™-Aktivitäten zu überwachen. Die Implementierung einer Überwachungsstrategie verbessert die Verfügbarkeit, Zuverlässigkeit und Leistung Ihrer AEM Formularbereitstellungen.

<!-- For more information about monitoring AEM forms deployments, see [A technical guide for monitoring AEM forms deployments](https://www.adobe.com/devnet/livecycle/pdfs/lc_monitoring_wp_ue.pdf). This URL is 404. No suitable replacement URL was found after a search. Do not make this link live if it is dead! -->

## Überwachung mithilfe von MBeans {#monitoring-using-mbeans}

AEM Forms bietet zwei registrierte MBeans, die Navigations- und Statistikinformationen bereitstellen. Die folgenden MBeans sind die einzigen, die für die Integration und Inspektion unterstützt werden:

* **ServiceStatistic:** Diese MBean stellt Informationen über den Dienstnamen und die Version bereit.
* **OperationStatistic:** Diese MBean stellt die Statistik für jeden Dienst des AEM Forms-Servers bereit. In dieser MBean können Administrierende Informationen zu einem bestimmten Dienst abrufen, z. B. Aufrufzeit und Fehleranzahl.

### ServiceStatisticMbean öffentliche Schnittstellen {#servicestatisticmbean-public-interfaces}

Auf diese öffentlichen Schnittstellen von „ServiceStatistic MBean“ kann zu Testzwecken zugegriffen werden:

```java
 public String getServiceId();
 public int getMajorVersion();
 public int getMinorVersion();
```

### OperationStatisticMbean öffentliche Schnittstellen {#operationstatisticmbean-public-interfaces}

Auf diese öffentlichen Schnittstellen von „OperationStatistic MBean“ kann zu Testzwecken zugegriffen werden:

```java
 // InvocationCount: The number of times the method is invoked.
 public long getInvocationCount();
 // InvocationStartTime: The time at which the method started to execute.
 public long getInvocationStartTime();
 // InvocationEndTime: The time at which the method finished execution.
 public long getInvocationEndTime();
 // InvocationTime: The time taken for the execution of the method.
 public long getInvocationTime();
 // LastSamplingDateTime: Convert InvocationStartTime to a formatted string
 public String getLastSamplingDateTime();
 // MaxInvocationTime: The maximum time taken for the execution of the method.
 public long getMaxInvocationTime();
 // MinInvocationTime: The minimum time taken for the execution of the method.
 public long getMinInvocationTime();
 // AverageInvocationTime: the averege execution time taken for the execution of the method.
 public double getAverageInvocationTime();
 // ExceptionCount: The number of times the method has thrown an Exception.
 public long getExceptionCount();
 // ExceptionMessage: The message of the last exception occurred.
 public String getExeptionMessage();
 public void setExceptionMessage(String errorMessage);
```

### MBean Struktur- &amp; Vorgangsstatistiken {#mbean-tree-operation-statistics}

Mithilfe der JMX-Konsole (JConsole) werden Statistiken von „OperationStatistic MBean“ bereitgestellt. Diese Statistiken sind Attribute von MBean und können unter der folgenden Hierarchiestruktur navigiert werden:

**MBean-Struktur**

**Adobe-Domain-Name:** Hängt vom Anwendungsserver ab. Wenn der Anwendungsserver die Domain nicht definiert, lautet die Standard-Domain „adobe.com“.

**ServiceType:** AdobeService ist der Name, der zum Auflisten aller Services verwendet wird.

**AdobeServiceName:** Service-Name oder Service-ID.

**Version:** Version des Service.

**Vorgangsstatistiken**

**Aufrufzeit:** Die Dauer für die Ausführung der Methode. Dieser Aufruf beinhaltet nicht die Zeit, in der die Anfrage serialisiert, vom Client zum Server übertragen und deserialisiert wird.

**Anzahl der Aufrufe:** Die Häufigkeit, mit der der Service aufgerufen wird.

**Durchschnittliche Aufrufzeit:** Durchschnittliche Zeit aller Aufrufe, die seit dem Start des Servers ausgeführt wurden.

**Maximale Aufrufzeit:** Die Dauer des längsten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Minimale Aufrufzeit:** Die Dauer des kürzesten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Anzahl der Ausnahmen:** Anzahl der Aufrufe, bei denen Fehler aufgetreten sind.

**Ausnahmemeldung:** Die Fehlermeldung über die letzte aufgetretene Ausnahme.

**Letztes Sampling: Datum, Zeit:** Das Datum des letzten Aufrufs.

**Zeiteinheit:** Der Standardwert ist Millisekunde.

Um die JMX-Überwachung zu aktivieren, benötigen die Anwendungs-Server in der Regel einige Konfigurationen. Weitere Informationen finden Sie in der Dokumentation zum Anwendungs-Server.

### Beispiele zum Einrichten eines offenen JMX-Zugriffs {#examples-of-how-to-set-up-open-jmx-access}

**JBoss® 4.0.3/4.2.0 – JVM-Start konfigurieren**

Um MBeans von JConsole anzuzeigen, konfigurieren Sie die JVM-Startparameter des JBoss-Anwendungsservers. Stellen Sie sicher, dass JBoss von der Datei „run.bat/sh“ gestartet wird.

1. Bearbeiten Sie die Datei „run.bat/sh“, die sich unter „InstallJBoss/bin“ befindet.
1. Suchen Sie die Zeile „JAVA_OPTS“ und fügen Sie Folgendes hinzu:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

**WebLogic 9.2/10 – JVM-Start konfigurieren**

1. Bearbeiten Sie die Datei „startWebLogic.bat“, die sich unter „`[WebLogic home]/user_projects/domains/Adobe_Live_Cycle/bin`“ befindet.
1. Suchen Sie die Zeile „JAVA_OPTS“ und fügen Sie Folgendes hinzu:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebLogic neu.

>[!NOTE]
>
>Für WebLogic können Sie über Remote oder IIOP auf das MBean zugreifen.

**Remote-Zugriff auf MBean**

1. Starten Sie JConsole, um eine neue Verbindung herzustellen, und klicken Sie auf die Registerkarte „Remote“.
1. Geben Sie den Host-Namen und Port ein (9088, die Nummer, die Sie bei den Startoptionen von JVM angeben).

**WebSphere® 6.1 – JVM-Start konfigurieren**

1. Fügen Sie in Admin Console („Application server“ > „server1“ > „Process Definition“ > „JVM“) die folgende Zeile in das Feld „Generic JVM Argument“ ein:

   ```shell
    -Djavax.management.builder.initial= -Dcom.sun.management.jmxremote
   ```

1. Fügen Sie die folgenden drei Zeilen in der Datei „/opt/IBM/WebSphere/AppServer/java/jre/lib/management/management.properties“ (oder „&lt;Your Websphere JRE>/ lib/management/management.properties“) hinzu oder heben Sie für sie den Kommentar auf:

   ```shell
    com.sun.management.jmxremote.port=9999 //any port you like, but make sure you use this port when you connect
    com.sun.management.jmxremote.authenticate=false
    com.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebSphere neu.
