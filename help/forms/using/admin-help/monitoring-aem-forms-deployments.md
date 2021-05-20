---
title: Überwachung der AEM Forms-Bereitstellung
seo-title: Überwachung der AEM Forms-Bereitstellung
description: Sie können AEM Forms-Bereitstellungen sowohl auf Systemebene als auch auf interner Ebene überwachen. Erfahren Sie mehr über das Überwachen von AEM-Forms-Bereitstellungen für dieses Dokument.
seo-description: Sie können AEM Forms-Bereitstellungen sowohl auf Systemebene als auch auf interner Ebene überwachen. Erfahren Sie mehr über das Überwachen von AEM-Forms-Bereitstellungen für dieses Dokument.
uuid: 032b7a93-3069-4ad5-a8c6-4c160f290669
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b3e7bca0-5aaf-4f28-bddb-fd7e8ed72ee8
exl-id: 931e8095-5c7c-4c1f-b95b-75ac2827d4f3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 76%

---

# Überwachung der AEM Forms-Bereitstellung {#monitoring-aem-forms-deployments}

Sie können AEM Forms-Bereitstellungen sowohl auf Systemebene als auch auf interner Ebene überwachen. Hierzu können Sie spezielle Verwaltungswerkzeuge wie HP OpenView, IBM Tivoli oder CA UniCenter verwenden sowie einen JMX-Monitor eines anderen Anbieters mit dem Namen *JConsole*, der speziell für die Überwachung von Java-Aktivitäten gedacht ist. Die Implementierung einer Überwachungsstrategie verbessert die Verfügbarkeit, Zuverlässigkeit und Leistung Ihrer AEM Forms-Bereitstellungen.

Weitere Informationen zum Überwachen von AEM Forms-Bereitstellungen finden Sie im [technischen Handbuch zur AEM Forms-Bereitstellung](https://www.adobe.com/devnet/livecycle/pdfs/lc_monitoring_wp_ue.pdf).

## Überwachung mithilfe von MBeans {#monitoring-using-mbeans}

AEM Forms stellt zwei registrierte MBeans bereit, die Informationen zur Navigation und statistische Informationen enthalten. Die folgenden MBeans sind die einzigen, die für die Integration und Inspektion unterstützt werden:

* **ServiceStatistic:** Diese MBean stellt Informationen über den Dienstnamen und die Version bereit.
* **OperationStatistic:** Diese MBean stellt die Statistik jedes Formularserverdienstes bereit. Hier können Administratoren Informationen zu bestimmten Diensten erhalten, z. B. Aufrufzeit, Anzahl der Fehler usw.

### Öffentliche ServiceStatisticMbean-Schnittstellen  {#servicestatisticmbean-public-interfaces}

Auf diese öffentlichen ServiceStatisticMBean-Schnittstellen kann zu Testzwecken zugegriffen werden:

```java
 public String getServiceId();
 public int getMajorVersion();
 public int getMinorVersion();
```

### Öffentliche OperationStatisticMbean-Schnittstellen  {#operationstatisticmbean-public-interfaces}

Auf diese öffentlichen OperationStatistic MBean-Schnittstellen kann zu Testzwecken zugegriffen werden:

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

### MBean Struktur- &amp; Vorgangsstatistiken  {#mbean-tree-operation-statistics}

Mit der JMX-Konsole (JConsole) werden Statistiken von OperationStatistic MBean bereitgestellt. Diese Statistiken sind Attribute von MBean und können unter der folgenden Hierarchiestruktur gefunden werden:

**MBean-Struktur**

**Domänenname der Adobe:** Hängt vom Anwendungsserver ab. Wenn der Anwendungsserver die Domäne nicht definiert, lautet die Standarddomäne „adobe.com“.

**ServiceType:** AdobeService ist der Name, der zum Auflisten aller Dienste verwendet wird.

**AdobeServiceName:** Dienstname oder Dienst-ID.

**Version:** Version des Dienstes.

**Vorgangsstatistiken**

**Aufrufzeit:** Zeit, die für die Ausführung der Methode benötigt wird. Dies schließt nicht die Zeit ein, die zum Serialisieren der Anfrage, zum Übertragen der Anfrage vom Client zum Server und zum Deserialisieren erforderlich ist.

**Anzahl der Aufrufe:** Die Häufigkeit, mit der der Dienst aufgerufen wird.

**Durchschnittliche Aufrufzeit:**  Durchschnittliche Zeit aller Aufrufe, die seit dem Start des Servers ausgeführt wurden.

**Max. Aufrufzeit:** Die Dauer des längsten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Min. Aufrufzeit:** Die Dauer des kürzesten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Ausnahmeanzahl:** Anzahl der Aufrufe, die zu Fehlern geführt haben.

**Ausnahmemeldung:** Die Fehlermeldung der letzten aufgetretenen Ausnahme.

**Datum des letzten Samplings:** Das Datum des letzten Aufrufs.

**Zeiteinheit:** Der Standardwert ist Millisekunde.

Zum Aktivieren der JMX-Überwachung müssen Anwendungsserver in der Regel konfiguriert werden. Weitere Informationen dazu erhalten Sie in der Dokumentation für Ihren Anwendungsserver.

### Beispiele zum Einrichten eines offenen JMX-Zugriffs  {#examples-of-how-to-set-up-open-jmx-access}

**JBoss 4.0.3/4.2.0 – JVM-Start konfigurieren**

Zum Anzeigen von MBeans von JConsole müssen Sie die JVM-Startparameter des JBoss-Anwendungsservers konfigurieren. Stellen Sie sicher, dass JBoss von der Datei „run.bat/sh“ gestartet wird.

1. Bearbeiten Sie die Datei „run.bat/sh“, die sich unter „InstallJBoss/bin“ befindet.
1. Suchen Sie die Zeile JAVA_OPTS und fügen Sie Folgendes hinzu:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

**WebLogic 9.2 /10 – JVM-Start konfigurieren**

1. Bearbeiten Sie die Datei &quot;startWebLogic.bat&quot;, die sich unter `[WebLogic home]/user_projects/domains/Adobe_Live_Cycle/bin` befindet.
1. Suchen Sie die Zeile JAVA_OPTS und fügen Sie Folgendes hinzu:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebLogic neu.

>[!NOTE]
>
>Für WebLogic können Sie auf die MBean entweder über Remote oder IIOP zugreifen.

**Remotezugriff auf MBean**

1. Starten Sie JConsole, um eine neue Verbindung herzustellen, und klicken Sie auf die Registerkarte „Remote“.
1. Geben Sie den Hostnamen und Anschluss ein (9088, die Nummer, die Sie bei den Startoptionen von JVM angegeben haben).

**Websphere 6.1 – JVM-Start konfigurieren**

1. Fügen Sie in der Verwaltungskonsole („Application server“ > „server1“ > „Process Definition“ > „JVM“) die folgende Zeile in das Feld „Generic JVM Argument“ ein:

   ```shell
    -Djavax.management.builder.initial= -Dcom.sun.management.jmxremote
   ```

1. Fügen Sie die folgenden drei Zeilen in der Datei „/opt/IBM/WebSphere/AppServer/java/jre/lib/management/management.properties“ (oder &lt;Your Websphere JRE>/ lib/management/management.properties) hinzu oder heben Sie den Kommentar auf:

   ```shell
    com.sun.management.jmxremote.port=9999 //any port you like, but make sure you use this port when you connect
    com.sun.management.jmxremote.authenticate=false
    com.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebSphere neu.
