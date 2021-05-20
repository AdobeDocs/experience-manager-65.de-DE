---
title: Leistung des Anwendungsservers verbessern
seo-title: Leistung des Anwendungsservers verbessern
description: In diesem Dokument werden die optionalen Einstellungen beschrieben, die Sie zum Verbessern der Leistung des AEM Forms-Anwendungsservers konfigurieren können.
seo-description: In diesem Dokument werden die optionalen Einstellungen beschrieben, die Sie zum Verbessern der Leistung des AEM Forms-Anwendungsservers konfigurieren können.
uuid: 88d2f96a-3b59-410d-8160-20581d27acad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fad65765-d56d-4a9f-82d5-bcceb1758953
exl-id: 6e2f3d4c-2ead-45b3-98e7-32cacc7e2985
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 95%

---

# Leistung des Anwendungsservers verbessern{#enhancing-application-server-performance}

In diesem Abschnitt werden die optionalen Einstellungen beschrieben, die Sie zum Verbessern der Leistung des AEM Forms-Anwendungsservers konfigurieren können.

## Datenquellen für Anwendungsserver konfigurieren {#configuring-application-server-data-sources}

AEM Forms verwendet das AEM Forms-Repository als Datenquelle. Das AEM Forms-Repository speichert Anwendungselemente und zur Laufzeit können Dienste bei der Ausführung automatisierter Geschäftsprozesses Elemente aus dem Repository abrufen.

Auf diese Datenquellen wird u. U. sehr häufig zugegriffen. Dies hängt davon ab, wie viele AEM Forms-Module ausgeführt werden und wie viele Benutzer gleichzeitig auf die Anwendung zugreifen. Der Zugriff auf die Datenquellen kann durch Verbindungspools optimiert werden. Durch *Verbindungspools* entfällt der Verarbeitungsaufwand für das Herstellen neuer Datenbankverbindungen, sobald eine Anwendung oder ein Serverobjekt Zugriff auf die Datenbank benötigt.  Verbindungspools werden in der Regel bei webbasierten Anwendungen und Unternehmensanwendungen verwendet und meist (aber nicht ausschließlich) von einem Anwendungsserver verarbeitet.

Sie müssen Ihre Parameter für den Verbindungspool ordnungsgemäß konfigurieren, damit immer Verbindungen zur Verfügung stehen, da ansonsten die Anwendungsleistung beeinträchtigt werden kann.

Um die Einstellungen für den Verbindungspool richtig zu konfigurieren, muss der Anwendungsserveradministrator den Verbindungspool zu Spitzenbelastungszeiten während des Tages unbedingt überwachen. Die Überwachung stellt sicher, dass jederzeit genügend Verbindungen für Anwendungen und Benutzer zur Verfügung stehen. Die meisten Anwendungsserver bieten entsprechende Überwachungswerkzeuge.

Sie können eine Vielzahl verschiedener Statistiken für jede JDBC-Datenquelleninstanz in Ihrer Domäne mithilfe von WebLogic Server Administration Console überwachen. Einzelheiten finden Sie in der WebLogic-Dokumentation.

Wenn der Administrator des Anwendungsservers die richtigen Einstellungen für den Verbindungspool ermittelt hat, sollten diese Angaben auch dem Datenbankadministrator mitgeteilt werden. Der Datenbankadministrator benötigt diese Informationen, da die Anzahl der Datenbankverbindungen gleich der Anzahl der Verbindungen im Verbindungspool für die Datenquelle ist. Führen Sie anschließend die nachfolgend beschriebenen Schritte zum Konfigurieren der Einstellungen für den Verbindungspool für Ihren Anwendungsserver und ihren Datenquellentyp durch.

### Einstellungen für den Verbindungspool für WebLogic für Oracle und MySQL konfigurieren  {#configure-connection-pool-settings-for-weblogic-for-oracle-and-mysql}

1. Klicken Sie unter „Domain Structure“ auf Services > JDBC > Data Sources und anschließend im rechten Bereich auf IDP_DS.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte „Configuration“ > „Connection Pool“ und geben Sie Werte in die folgenden Felder ein:

   * Initial Capacity
   * Maximum Capacity
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf Save und dann auf Activate Changes.
1. Starten Sie WebLogic Managed Server neu.

### Einstellungen für den Verbindungspool für WebLogic für SQLServer konfigurieren  {#configure-connection-pool-settings-for-weblogic-for-sqlserver}

1. Klicken Sie unter „Change Center“ auf Lock &amp; Edit.
1. Klicken Sie unter „Domain Structure“ auf „Services“ > „JDBC“ > „Data Sources“ und klicken Sie dann im rechten Bereich auf „EDC_DS“.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte „Configuration“ > „Connection Pool“ und geben Sie Werte in die folgenden Felder ein:

   * Anfangskapazität
   * Maximale Kapazität
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf Save und dann auf Activate Changes.
1. Starten Sie WebLogic Managed Server neu.

### Einstellungen für den Verbindungspool für WebSphere für DB2 konfigurieren  {#configure-connection-pool-settings-for-websphere-for-db2}

1. Klicken Sie in der Navigationsstruktur auf Resources > JDBC > JDBC Providers. Klicken Sie im rechten Bereich auf die von Ihnen erstellte Datenquelle – entweder DB2 Universal JDBC Driver Provider oder LiveCycle – db2 – IDP_DS.
1. Klicken Sie unter „Additional Properties“ auf „Data sources“ und klicken Sie dann auf „IDP_DS“.
1. Klicken Sie im nächsten Bildschirm unter „Additional Properties“ auf „Connection Pool Properties“ und geben Sie einen Wert in das Feld „Maximum Connections“ und in das Feld „Minimum Connections“ ein.
1. Klicken Sie auf „OK“ oder „Apply“ und klicken Sie dann auf „Save directly to Master Configuration“.

### Einstellungen für den Verbindungspool für WebSphere für Oracle konfigurieren  {#configure-connection-pool-settings-for-websphere-for-oracle}

1. Klicken Sie in der Navigationsstruktur auf Resources > JDBC > JDBC Providers. Klicken Sie im rechten Bereich auf die von Ihnen erstellte Oracle JDBC Driver-Datenquelle.
1. Klicken Sie unter „Additional Properties“ auf „Data sources“ und klicken Sie dann auf „IDP_DS“.
1. Klicken Sie im nächsten Bildschirm unter „Additional Properties“ auf „Connection Pool Properties“ und geben Sie einen Wert in das Feld „Maximum Connections“ und in das Feld „Minimum Connections“ ein.
1. Klicken Sie auf „OK“ oder „Apply“ und klicken Sie dann auf „Save directly to Master Configuration“.

### Einstellungen für den Verbindungspool für WebSphere für SQLServer konfigurieren  {#configure-connection-pool-settings-for-websphere-for-sqlserver}

1. Klicken Sie in der Navigationsstruktur auf „Resources“ > „JDBC“ > „JDBC Providers“ und anschließend im rechten Bereich auf die erstellte Datenquelle „User-Defined JDBC Driver“.
1. Klicken Sie unter „Additional Properties“ auf „Data sources“ und klicken Sie dann auf „IDP_DS“.
1. Klicken Sie im nächsten Bildschirm unter „Additional Properties“ auf „Connection Pool Properties“ und geben Sie einen Wert in das Feld „Maximum Connections“ und in das Feld „Minimum Connections“ ein:
1. Klicken Sie auf „OK“ oder „Apply“ und klicken Sie dann auf „Save directly to Master Configuration“.

## Optimieren von Inline-Dokumenten und Auswirkungen auf den JVM-Speicher  {#optimizing-inline-documents-and-impact-on-jvm-memory}

Wenn Sie in der Regel relativ kleine Dokumente verarbeiten, können Sie die Leistung in Bezug auf die Übertragungsgeschwindigkeit von Dokumenten und den Speicherplatz optimieren. Implementieren Sie zu diesem Zweck die nachfolgenden AEM Forms-Produktkonfigurationen:

* Erhöhen Sie die standardmäßige Maximalgröße für Inline-Dokumente für AEM Forms, sodass diese über der Größe der meisten Dokumente liegt.
* Wenn Sie größere Dateien verarbeiten, legen Sie Speicherordner fest, die sich in einem Hochgeschwindigkeits-Festplattensystem oder auf einem RAM-Datenträger befinden.

Die Inline-Maximalgröße und die Speicherordner (AEM Forms-Speicherordner für temporäre Dateien und Ordner des globalen Dokumentenspeichers) werden in Administration Console konfiguriert.

### Dokumentgröße und Inline-Maximalgröße  {#document-size-and-maximum-inline-size}

Wenn die Größe eines Dokuments, das von AEM Forms zur Verarbeitung gesendet wird, kleiner gleich der standardmäßigen Maximalgröße für Inline-Dokumente ist, wird es als Inline-Dokument auf dem Server gespeichert und als Adobe-Dokumentobjekt serialisiert. Die Inline-Speicherung von Dokumenten kann die Leistung erheblich steigern. Wenn Sie jedoch den Arbeitsablauf für Formulare verwenden, wird der Inhalt möglicherweise zur einfacheren Verfolgung auch in der Datenbank gespeichert. Eine Erhöhung der Inline-Maximalgröße kann sich also auf die Datenbankgröße auswirken.

Dokumente, welche die Inline-Maximalgröße überschreiten, werden im lokalen Dateisystem gespeichert. Das Adobe-Dokumentobjekt, das von und zum Server übertragen wird, ist dann lediglich ein Verweis auf diese Datei.

Wenn der Dokumentinhalt kleiner als die Inline-Maximalgröße ist, wird er in der Datenbank (d. h. als Teil des Serialisierungsaufkommens des Dokuments) gespeichert. Eine Erhöhung der Inline-Maximalgröße kann sich also auf die Datenbankgröße auswirken.

**Die Inline-Maximalgröße ändern**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie einen Wert in das Feld „Standardmäßige Maximalgröße für Inline-Dokumente“ ein.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft &quot;Max. Inline-Größe des Dokuments&quot;muss für die AEM Forms on JEE-Umgebung identisch sein und für AEM Forms im OSGi-Bundle, das die AEM Forms on JEE-Umgebung enthält. Diese Schritte sind nur aktualisierte Werte für die AEM Forms on JEE-Umgebung und nicht für AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung.

1. Starten Sie den Anwendungsserver mit folgenden Systemeigenschaft neu:

   com.adobe.idp.defaultDocumentMaxInlineSize=`[value specified in Step 2]`

   >[!NOTE]
   >
   >Die oben angegebene Sytemeigenschaft überschreibt das Eigenschaftset für die max. Inline-Größe des Dokuments für die AEM Forms on JEE-Umgebung und das AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung.

>[!NOTE]
>
>Der Standardwert für die Inline-Maximalgröße beträgt 65.536 Bytes.

### Maximale JVM-Heap-Größe  {#jvm-maximum-heap-size}

Wenn die Inline-Maximalgröße erhöht wird, ist mehr Speicher zum Ablegen der serialisierten Dokumente erforderlich. Daher muss in der Regel auch die JVM-Einstellung „Maximale Heap-Größe“ erhöht werden.

Bei einem stark ausgelasteten System, das eine Vielzahl von Dokumenten verarbeitet, kann der JVM-Heap-Speicher schnell erschöpft sein. Um Fehler wegen ungenügenden Speicherplatzes zu verhindern, muss die maximale JVM-Heap-Größe um einen Wert erhöht werden, der dem Produkt aus der Größe der Inline-Dokumente und der Anzahl der Dokumente entspricht, die in der Regel zu einem bestimmten Zeitpunkt ausgeführt werden.

Erhöhung der maximalen JVM-Heap-Größe = (Größe der Inline-Dokumente) x (durchschnittliche Anzahl verarbeiteter Dokumente).

**Maximale JVM-Heap-Größe berechnen**

In diesem Beispiel wurden die maximale JVM-Heap-Größe ursprünglich auf 512 MB und die Inline-Maximalgröße auf 64 KB festgelegt. Der Server muss für die gleichzeitige Ausführung von 10 Aufträgen konfiguriert werden, wobei jeder Auftrag 9 Eingabedateien und 1 Ergebnisdatei umfasst (d. h. 10 Dateien pro Auftrag und 100 gleichzeitig verarbeitete Dateien). Die Größe aller Dateien liegt unter 512 KB.

Damit alle Dateien als Inline-Dateien gespeichert werden können, muss die Inline-Maximalgröße auf mindestens 512 KB festgelegt werden.

Die erforderliche Erhöhung der maximalen JVM-Heap-Größe wird mit der folgenden Gleichung berechnet:

(512 KB) x (100) = 51200 KB oder 50 MB

Die maximale JVM-Heap-Größe muss daher um 50 MB erhöht werden, sodass sie insgesamt 562 MB beträgt.

**Heap-Fragmentierung berücksichtigen**

Wenn die Größe von Inline-Dokumenten auf einen hohen Wert festgelegt wird, erhöht sich dadurch das Fehlerrisiko wegen ungenügenden Speicherplatzes bei Systemen, die für die Heap-Fragmentierung anfällig sind. Zur Inline-Speicherung eines Dokuments muss im JVM-Heap-Speicher ein genügend großer zusammenhängender Speicherblock zur Verfügung stehen. Einige Betriebssysteme, JVMs und Löschprogrammalgorithmen (so genannte „Garbage Collectors“) sind für Fragmentierungen des Heap-Speichers anfällig. Die Fragmentierung reduziert die Größe des zusammenhängenden Heap-Speichers, sodass Fehler wegen ungenügenden Speicherplatzes auch dann auftreten können, wenn der insgesamt verfügbare freie Heap-Speicher eigentlich ausreichend ist.

Dies kann beispielsweise der Fall sein, wenn sich der JVM-Heap nach der Ausführung anderer Vorgänge auf dem Anwendungsserver in einem fragmentierten Zustand befindet und der Garbage Collector den Heap nicht genügend komprimieren kann, um große, zusammenhängende Speicherblöcke zu bilden. Fehler wegen ungenügenden Speicherplatzes können auch dann noch auftreten, wenn die maximale JVM-Heap-Größe an die erhöhte Inline-Maximalgröße angepasst wurde.

Um die Heap-Fragmentierung zu berücksichtigen, darf die Inline-Dokumentgröße auf nicht mehr als 0,1 % der gesamten Heap-Größe eingestellt werden. Mit einer maximalen JVM-Heap-Größe von 512 MB kann beispielsweise eine Inline-Maximalgröße von 512 MB x 0,001 = 0,512 MB oder 512 KB unterstützt werden.

## Optimierungen für den WebSphere Application Server  {#websphere-application-server-enhancements}

In diesem Abschnitt werden Einstellungen beschrieben, die spezifisch für eine WebSphere Application Server-Umgebung gelten.

### JVM zugewiesenen maximalen Arbeitsspeicher erhöhen  {#increasing-the-maximum-memory-allocated-to-the-jvm}

Wenn Sie Configuration Manager ausführen oder versuchen, Enterprise JavaBeans-(EJB-)Bereitstellungscode über das Befehlszeilen-Dienstprogramm *ejbdeploy* zu erstellen und ein Fehler wegen ungenügenden Arbeitsspeichers auftritt, erhöhen Sie die Größe des Speichers, welcher der JVM zugewiesen ist.

1. Bearbeiten Sie das Skript ejbdeploy im Ordner *[appserver root]*/deploytool/itp/ :

   * (Windows) `ejbdeploy.bat`
   * (Linux und UNIX) `ejbdeploy.sh`

1. Suchen Sie den Parameter `-Xmx256M` und ändern Sie ihn in einen höheren Wert, z. B. `-Xmx1024M`.
1. Speichern Sie die Datei.
1. Führen Sie den Befehl `ejbdeploy` aus oder führen Sie mit dem Configuration Manager eine erneute Bereitstellung aus.

## Windows Server 2003-Leistung mit LDAP verbessern {#improving-windows-server-2003-performance-with-ldap}

In diesem Abschnitt werden Einstellungen beschrieben, die spezifisch für eine Microsoft Windows Server 2003-Betriebssystemumgebung gelten.

Durch die Verwendung von Verbindungspools bei der Suchverbindung kann die Anzahl der benötigten Anschlüsse um bis zu 50 % verringert werden. Der Grund dafür ist, dass diese Verbindung immer dieselben Berechtigungen für eine bestimmte Domäne verwendet und darüber hinaus der Kontext und die entsprechenden Objekte ausdrücklich geschlossen werden.

### Windows Server für die Verwendung von Verbindungspools konfigurieren  {#configure-your-windows-server-for-connection-pooling}

1. Klicken Sie auf „Start“ > „Ausführen“, um den Registrierungs-Editor zu starten. Geben Sie dann in das Feld „Öffnen“ den Befehl `regedit` ein und klicken Sie auf „OK“.
1. Navigieren Sie zum Registrierungsschlüssel `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters` .
1. Suchen Sie im rechten Bereich des Registrierungs-Editors den Wertnamen „TcpTimedWaitDelay“. Falls der Name fehlt, wählen Sie in der Menüleiste den Befehl „Bearbeiten“ > „Neu“ > „DWORD-Wert“ aus, um den Namen hinzuzufügen.
1. Geben Sie in das Feld „Name“`TcpTimedWaitDelay`

   >[!NOTE]
   >
   >Wenn kein blinkender Cursor und `New Value #` im Feld angezeigt werden, klicken Sie mit der rechten Maustaste in das rechte Bedienfeld, wählen Sie &quot;Umbenennen&quot;und geben Sie im Feld &quot;Name&quot;`TcpTimedWaitDelay`*.* ein.

1. Wiederholen Sie Schritt 4 für die Wertnamen „MaxUserPort“, „MaxHashTableSize“ und „MaxFreeTcbs“.
1. Doppelklicken Sie im rechten Bereich, um den Wert „TcpTimedWaitDelay“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `30`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxUserPort“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65534`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxHashTableSize“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65536`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxFreeTcbs“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `16000`.

>[!NOTE]
>
>Wenn Sie mit dem Registrierungs-Editor oder einer anderen Methode fehlerhafte Änderungen an der Registrierung vornehmen, kann dies schwerwiegende Folgen haben. Im Extremfall müssen Sie eventuell das Betriebssystem neu installieren. Alle Änderungen an der Registrierung erfolgen auf eigenes Risiko.
