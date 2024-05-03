---
title: Verbessern der Leistung des Anwendungs-Servers
description: In diesem Dokument werden die optionalen Einstellungen beschrieben, die Sie zum Verbessern der Leistung des AEM Forms-Anwendungs-Servers konfigurieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6e2f3d4c-2ead-45b3-98e7-32cacc7e2985
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 100%

---

# Leistung des Anwendungsservers verbessern{#enhancing-application-server-performance}

In diesem Abschnitt werden die optionalen Einstellungen beschrieben, die Sie zum Verbessern der Leistung des AEM Forms-Anwendungs-Servers konfigurieren können.

## Konfigurieren von Datenquellen für Anwendungs-Server {#configuring-application-server-data-sources}

AEM Forms verwendet das AEM Forms-Repository als Datenquelle. Das AEM Forms-Repository speichert Anwendungselemente und zur Laufzeit können Dienste bei der Ausführung automatisierter Geschäftsprozesse Elemente aus dem Repository abrufen.

Auf diese Datenquelle wird u. U. sehr häufig zugegriffen. Dies hängt davon ab, wie viele AEM Forms-Module ausgeführt werden und wie viele Benutzende gleichzeitig auf die Anwendung zugreifen. Der Zugriff auf die Datenquellen kann durch Verbindungs-Pools optimiert werden. Durch *Verbindungspools* entfällt der Verarbeitungsaufwand für das Herstellen neuer Datenbankverbindungen, sobald eine Anwendung oder ein Serverobjekt Zugriff auf die Datenbank benötigt. Verbindungs-Pools werden in der Regel bei Web-basierten Anwendungen und Unternehmensanwendungen verwendet und meist (aber nicht ausschließlich) von einem Anwendungs-Server verarbeitet.

Sie müssen Ihre Parameter für den Verbindungs-Pool ordnungsgemäß konfigurieren, damit immer Verbindungen zur Verfügung stehen, da ansonsten die Anwendungsleistung beeinträchtigt werden kann.

Um die Einstellungen für den Verbindungs-Pool richtig zu konfigurieren, muss die Administratorin oder der Administrator des Anwendungs-Servers den Verbindungs-Pool zu Spitzenbelastungszeiten während des Tages unbedingt überwachen. Durch die Überwachung wird sichergestellt, dass jederzeit genügend Verbindungen für Anwendungen und Benutzende zur Verfügung stehen. Die meisten Anwendungs-Server bieten entsprechende Überwachungs-Tools.

Sie können eine Vielzahl verschiedener Statistiken für jede JDBC-Datenquelleninstanz in Ihrer Domain mithilfe von WebLogic Server Administration Console überwachen. Einzelheiten finden Sie in der WebLogic-Dokumentation.

Wenn die Administratorin oder der Administrator des Anwendungs-Servers die richtigen Einstellungen für den Verbindungs-Pool ermittelt hat, sollten diese Angaben auch der Administratorin oder dem Administrator der Datenbank mitgeteilt werden. Die Administratorin oder der Administrator der Datenbank benötigt diese Informationen, da die Anzahl der Datenbankverbindungen der Anzahl der Verbindungen im Verbindungs-Pool für die Datenquelle entspricht. Führen Sie anschließend die nachfolgend beschriebenen Schritte zum Konfigurieren der Einstellungen für den Verbindungs-Pool für den Anwendungs-Server und Datenquellentyp durch.

### Konfigurieren der Einstellungen für den Verbindungs-Pool für WebLogic für Oracle und MySQL {#configure-connection-pool-settings-for-weblogic-for-oracle-and-mysql}

1. Klicken Sie unter „Domain Structure“ auf „Services“ > „JDBC“ > „Data Sources“ und anschließend im rechten Bereich auf „IDP_DS“.
1. Klicken Sie auf dem nächsten Bildschirm auf die Registerkarte „Configuration“ > „Connection Pool“ und geben Sie Werte in die folgenden Felder ein:

   * Initial Capacity
   * Maximum Capacity
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie WebLogic Managed Server neu.

### Konfigurieren der Einstellungen für den Verbindungs-Pool für WebLogic für SQLServer {#configure-connection-pool-settings-for-weblogic-for-sqlserver}

1. Klicken Sie im Change Center auf „Sperren und bearbeiten“
1. Klicken Sie unter „Domain Structure“ auf „Services“ > „JDBC“ > „Data Sources“ und dann im rechten Bereich auf „EDC_DS“.
1. Klicken Sie auf dem nächsten Bildschirm auf die Registerkarte „Configuration“ > „Connection Pool“ und geben Sie Werte in die folgenden Felder ein:

   * Initial Capacity
   * Maximum Capacity
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie WebLogic Managed Server neu.

### Konfigurieren der Einstellungen für den Verbindungs-Pool für WebSphere für DB2 {#configure-connection-pool-settings-for-websphere-for-db2}

1. Klicken Sie in der Navigationsstruktur auf „Resources“ > „JDBC“ > „JDBC Providers“. Klicken Sie im rechten Bereich auf die von Ihnen erstellte Datenquelle – entweder DB2 Universal JDBC Driver Provider oder LiveCycle – db2 – IDP_DS.
1. Klicken Sie unter „Additional Properties“ auf „Data Sources“ und wählen Sie dann „IDP_DS“.
1. Klicken Sie auf dem nächsten Bildschirm unter „Additional Properties“ auf „Connection Pool Properties“ und geben Sie einen Wert in das Feld „Maximum Connections“ und in das Feld „Minimum Connections“ ein.
1. Klicken Sie auf „OK“ oder „Apply“ und dann auf „Save directly to Master Configuration“.

### Konfigurieren der Einstellungen für den Verbindungs-Pool für WebSphere für Oracle {#configure-connection-pool-settings-for-websphere-for-oracle}

1. Klicken Sie in der Navigationsstruktur auf „Resources“ > „JDBC“ > „JDBC Providers“. Klicken Sie im rechten Bereich auf die von Ihnen erstellte Oracle JDBC Driver-Datenquelle.
1. Klicken Sie unter „Additional Properties“ auf „Data Sources“ und wählen Sie dann „IDP_DS“.
1. Klicken Sie auf dem nächsten Bildschirm unter „Additional Properties“ auf „Connection Pool Properties“ und geben Sie einen Wert in das Feld „Maximum Connections“ und in das Feld „Minimum Connections“ ein.
1. Klicken Sie auf „OK“ oder „Apply“ und dann auf „Save directly to Master Configuration“.

### Konfigurieren der Verbindungs-Pool-Einstellungen für WebSphere für SQL Server {#configure-connection-pool-settings-for-websphere-for-sqlserver}

1. Klicken Sie in der Navigationsstruktur auf „Resources“ (Ressourcen) > „JDBC“ > „JDBC Providers“ (JDBC-Anbieter) und anschließend im rechten Bereich auf die von Ihnen erstellte Datenquelle „User-Defined JDBC Driver“ (Benutzerdefinierter JDBC-Treiber).
1. Klicken Sie unter „Additional Properties“ auf „Data Sources“ und wählen Sie dann „IDP_DS“.
1. Klicken Sie auf dem nächsten Bildschirm unter „Additional Properties“ (Zusätzliche Eigenschaften) auf „Connection Pool Properties“ (Verbindungs-Pool-Eigenschaften) und geben Sie einen Wert in die Felder „Maximum Connections“ (Maximale Verbindungen) und „Minimum Connections“ (Minimale Verbindungen) ein:
1. Klicken Sie auf „OK“ oder „Apply“ und dann auf „Save directly to Master Configuration“.

## Optimieren von Inline-Dokumenten und Auswirkungen auf den JVM-Speicher {#optimizing-inline-documents-and-impact-on-jvm-memory}

Wenn Sie in der Regel relativ kleine Dokumente verarbeiten, können Sie die Leistung in Bezug auf die Übertragungsgeschwindigkeit von Dokumenten und den Speicherplatz optimieren. Implementieren Sie hierzu die folgenden AEM Forms-Produktkonfigurationen:

* Erhöhen Sie die standardmäßige Maximalgröße für Inline-Dokumente für AEM Forms, sodass diese über der Größe der meisten Dokumente liegt.
* Wenn Sie größere Dateien verarbeiten, legen Sie Speicherverzeichnisse fest, die sich auf einem Hochgeschwindigkeits-Festplattensystem oder RAM-Datenträger befinden.

Die Inline-Maximalgröße und die Speicherverzeichnisse (AEM Forms-Speicherverzeichnis für temporäre Dateien und Ordner des globalen Dokumentenspeichers) werden in der Administrationskonsole konfiguriert.

### Dokumentgröße und Inline-Maximalgröße {#document-size-and-maximum-inline-size}

Wenn die Größe eines Dokuments, das von AEM Forms zur Verarbeitung gesendet wird, kleiner gleich der standardmäßigen Maximalgröße für Inline-Dokumente ist, wird es als Inline-Dokument auf dem Server gespeichert und als Adobe-Dokumentobjekt serialisiert. Die Inline-Speicherung von Dokumenten kann die Leistung erheblich steigern. Wenn Sie jedoch Forms Workflow verwenden, wird der Inhalt möglicherweise zur einfacheren Verfolgung auch in der Datenbank gespeichert. Eine Erhöhung der Inline-Maximalgröße kann sich also auf die Datenbankgröße auswirken.

Dokumente, die die Inline-Maximalgröße überschreiten, werden im lokalen Dateisystem gespeichert. Das Adobe-Dokumentobjekt, das vom und zum Server übertragen wird, ist dann lediglich ein Verweis auf diese Datei.

Wenn der Dokumentinhalt kleiner als die Inline-Maximalgröße ist, wird er als Teil der Serialisierungs-Payload des Dokuments in der Datenbank gespeichert. Eine Erhöhung der Inline-Maximalgröße kann sich also auf die Datenbankgröße auswirken.

**Ändern der Inline-Maximalgröße**

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie einen Wert in das Feld „Standardmäßige Maximalgröße für Inline-Dokumente“ ein und klicken Sie auf „OK“.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft „Maximalgröße für Inline-Dokumente“ muss für die Umgebung von AEM Forms auf JEE und die Umgebung von AEM Forms auf JEE, die das Bundle AEM Forms unter OSGi enthält, identisch sein. Diese Schritte sind nur aktualisierte Werte für die AEM Forms on JEE-Umgebung und nicht für das AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung.

1. Starten Sie den Anwendungs-Server mit folgender Systemeigenschaft neu:

   com.adobe.idp.defaultDocumentMaxInlineSize=`[value specified in Step 2]`

   >[!NOTE]
   >
   >Die oben angegebene Systemeigenschaft überschreibt den Eigenschaftensatz „Maximalgröße für Inline-Dokumente“ für die AEM Forms on JEE-Umgebung und das AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung.

>[!NOTE]
>
>Der Standardwert für die Inline-Maximalgröße beträgt 65.536 Byte.

### Maximale JVM-Heap-Größe {#jvm-maximum-heap-size}

Wenn die Inline-Maximalgröße erhöht wird, ist mehr Speicher zum Ablegen der serialisierten Dokumente erforderlich. Daher muss in der Regel auch die JVM-Einstellung „Maximale Heap-Größe“ erhöht werden.

Bei einem stark ausgelasteten System, das eine Vielzahl von Dokumenten verarbeitet, kann der JVM-Heap-Speicher schnell erschöpft sein. Um Fehler wegen ungenügenden Speicherplatzes zu verhindern, muss die maximale JVM-Heap-Größe um einen Wert erhöht werden, der der Größe der Inline-Dokumente multipliziert mit der Anzahl der Dokumente entspricht, die in der Regel zu einem bestimmten Zeitpunkt ausgeführt werden.

Erhöhung der maximalen JVM-Heap-Größe = (Größe der Inline-Dokumente) x (durchschnittliche Anzahl verarbeiteter Dokumente)

**Berechnen der maximalen JVM-Heap-Größe**

In diesem Beispiel wurden die maximale JVM-Heap-Größe ursprünglich auf 512 MB und die Inline-Maximalgröße auf 64 KB festgelegt. Der Server muss für die gleichzeitige Ausführung von 10 Aufträgen konfiguriert werden, wobei jeder Auftrag 9 Eingabedateien und 1 Ergebnisdatei umfasst (d. h. 10 Dateien pro Auftrag und 100 gleichzeitig verarbeitete Dateien). Alle Dateien sind kleiner als 512 KB.

Damit alle Dateien als Inline-Dateien gespeichert werden können, muss die Inline-Maximalgröße auf mindestens 512 KB festgelegt werden.

Die erforderliche Erhöhung der maximalen JVM-Heap-Größe wird mit der folgenden Gleichung berechnet:

(512 KB) x (100) = 51.200 KB bzw. 50 MB

Die maximale JVM-Heap-Größe muss um 50 MB erhöht werden, sodass sie insgesamt 562 MB beträgt.

**Berücksichtigen der Heap-Fragmentierung**

Wenn die Größe von Inline-Dokumenten auf einen hohen Wert festgelegt wird, erhöht sich dadurch das Fehlerrisiko wegen ungenügenden Speicherplatzes bei Systemen, die für Heap-Fragmentierung anfällig sind. Zur Inline-Speicherung eines Dokuments muss im JVM-Heap-Speicher ein genügend großer zusammenhängender Speicherblock zur Verfügung stehen. Einige Betriebssysteme, JVMs und Algorithmen zur Speicherbereinigung („Garbage Collector“) sind für Fragmentierungen des Heap-Speichers anfällig. Die Fragmentierung reduziert die Größe des zusammenhängenden Heap-Speichers, sodass Fehler wegen ungenügenden Speicherplatzes auch dann auftreten können, wenn der insgesamt verfügbare freie Heap-Speicher eigentlich ausreichend ist.

Dies kann beispielsweise der Fall sein, wenn sich der JVM-Heap nach der Ausführung anderer Vorgänge auf dem Anwendungs-Server in einem fragmentierten Zustand befindet und der Garbage Collector den Heap nicht genügend komprimieren kann, sodass sich große, zusammenhängende Speicherblöcke bilden. Fehler wegen ungenügenden Speicherplatzes können auch dann noch auftreten, wenn die maximale JVM-Heap-Größe an die erhöhte Inline-Maximalgröße angepasst wurde.

Um die Heap-Fragmentierung zu berücksichtigen, darf die Inline-Dokumentgröße auf nicht mehr als 0,1 % der gesamten Heap-Größe eingestellt werden.  Mit einer maximalen JVM-Heap-Größe von 512 MB kann beispielsweise eine Inline-Maximalgröße von 512 MB x 0,001 = 0,512 MB oder 512 KB unterstützt werden.

## Optimierungen für WebSphere Application Server {#websphere-application-server-enhancements}

In diesem Abschnitt werden Einstellungen beschrieben, die spezifisch für eine WebSphere Application Server-Umgebung gelten.

### Erhöhen des der JVM zugewiesenen maximalen Arbeitsspeichers {#increasing-the-maximum-memory-allocated-to-the-jvm}

Wenn Sie Configuration Manager ausführen oder versuchen, Enterprise JavaBeans(EJB)-Bereitstellungs-Code mithilfe des Befehlszeilen-Dienstprogramms *ejbdeploy* zu generieren, und ein Fehler wegen ungenügenden Speicherplatzes auftritt, erhöhen Sie die der JVM zugewiesene Speichermenge.

1. Bearbeiten Sie im Ordner „*[Programm-Server-Stammordner]*/deploytool/itp/“ das Skript „ejbdeploy“:

   * (Windows) `ejbdeploy.bat`
   * (Linux und UNIX) `ejbdeploy.sh`

1. Suchen Sie den Parameter `-Xmx256M` und erhöhen Sie dessen Wert, z. B. auf `-Xmx1024M`.
1. Speichern Sie die Datei.
1. Führen Sie den Befehl `ejbdeploy` aus oder führen Sie mit dem Configuration Manager eine erneute Bereitstellung aus.

## Verbessern der Windows Server 2003-Leistung mit LDAP {#improving-windows-server-2003-performance-with-ldap}

In diesem Abschnitt werden Einstellungen beschrieben, die spezifisch für eine Microsoft Windows Server 2003-Betriebssystemumgebung gelten.

Durch die Verwendung von Verbindungs-Pools bei der Suchverbindung kann die Anzahl der benötigten Anschlüsse um bis zu 50 % verringert werden.  Der Grund dafür ist, dass diese Verbindung immer dieselben Berechtigungen für eine bestimmte Domain verwendet und darüber hinaus der Kontext und die entsprechenden Objekte ausdrücklich geschlossen werden.

### Konfigurieren eines Windows-Servers für die Verwendung von Verbindungs-Pools {#configure-your-windows-server-for-connection-pooling}

1. Klicken Sie auf „Start“ > „Ausführen“, um den Registrierungs-Editor zu starten. Geben Sie dann in das Feld „Öffnen“ den Befehl `regedit` ein und klicken Sie auf „OK“.
1. Wechseln Sie zum Registrierungsschlüssel `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`
1. Suchen Sie im rechten Bereich des Registrierungs-Editors den Wertnamen „TcpTimedWaitDelay“.  Falls der Name fehlt, wählen Sie in der Menüleiste „Bearbeiten“ > „Neu“ > „DWORD-Wert“ aus, um den Namen hinzuzufügen.
1. Geben Sie in das Feld „Name“`TcpTimedWaitDelay`

   >[!NOTE]
   >
   >Wenn in dem Feld weder ein blinkender Cursor noch der Text `New Value #` angezeigt wird, klicken Sie mit der rechten Maustaste in den rechten Bereich, wählen Sie „Umbenennen“ und geben Sie im Feld „Name“ `TcpTimedWaitDelay`*ein.*

1. Wiederholen Sie Schritt 4 für die Wertnamen „MaxUserPort“, „MaxHashTableSize“ und „MaxFreeTcbs“.
1. Doppelklicken Sie im rechten Bereich, um den Wert „TcpTimedWaitDelay“ festzulegen.  Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `30`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxUserPort“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65534`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxHashTableSize“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65536`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxFreeTcbs“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `16000`.

>[!NOTE]
>
>Wenn Sie mit dem Registrierungs-Editor oder einer anderen Methode fehlerhafte Änderungen an der Registrierung vornehmen, kann dies schwerwiegende Folgen haben.  Im Extremfall müssen Sie möglicherweise das Betriebssystem neu installieren.  Alle Änderungen an der Registrierung erfolgen auf eigenes Risiko.
