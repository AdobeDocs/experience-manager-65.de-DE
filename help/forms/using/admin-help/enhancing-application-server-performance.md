---
title: Verbessern der Leistung des Anwendungs-Servers
description: In diesem Dokument werden optionale Einstellungen beschrieben, die Sie konfigurieren können, um die Leistung des AEM forms-Anwendungsservers zu verbessern.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6e2f3d4c-2ead-45b3-98e7-32cacc7e2985
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 15%

---

# Leistung des Anwendungsservers verbessern{#enhancing-application-server-performance}

In diesem Abschnitt werden optionale Einstellungen beschrieben, die Sie konfigurieren können, um die Leistung des AEM forms-Anwendungsservers zu verbessern.

## Anwendungsserver-Datenquellen konfigurieren {#configuring-application-server-data-sources}

AEM Formulare verwenden das AEM Formular-Repository als Datenquelle. Das AEM Forms-Repository speichert Anwendungs-Assets und zur Laufzeit können Dienste Assets aus dem Repository abrufen, um einen automatisierten Geschäftsprozess abzuschließen.

Der Zugriff auf die Datenquelle kann je nach der Anzahl der AEM Formularmodule, die Sie ausführen, und der Anzahl der gleichzeitigen Benutzer, die auf die Anwendung zugreifen, erheblich sein. Der Datenquellenzugriff kann mithilfe von Verbindungspools optimiert werden. Durch *Verbindungspools* entfällt der Verarbeitungsaufwand für das Herstellen neuer Datenbankverbindungen, sobald eine Anwendung oder ein Serverobjekt Zugriff auf die Datenbank benötigt. Verbindungspools werden in der Regel in webbasierten Anwendungen und Unternehmensanwendungen verwendet und werden normalerweise von einem Anwendungsserver verarbeitet, jedoch nicht ausschließlich.

Es ist wichtig, die Parameter Ihres Verbindungspools ordnungsgemäß zu konfigurieren, damit Ihnen nie die Verbindungen fehlen, was zu einer Verschlechterung der Anwendungsleistung führen kann.

Um die Einstellungen für den Verbindungspool ordnungsgemäß zu konfigurieren, ist es wichtig, dass der Administrator des Anwendungsservers den Verbindungspool während der Spitzenzeiten des Tages überwacht. Die Überwachung stellt sicher, dass für Anwendungen und Benutzer jederzeit ausreichende Verbindungen verfügbar sind. Die meisten Anwendungsserver umfassen Überwachungstools.

Sie können eine Vielzahl verschiedener Statistiken für jede JDBC-Datenquelleninstanz in Ihrer Domain mithilfe von WebLogic Server Administration Console überwachen. Weitere Informationen finden Sie in der WebLogic-Dokumentation .

Wenn der Administrator des Anwendungsservers die richtigen Einstellungen für den Verbindungspool ermittelt, muss diese Person diese Informationen dem Datenbankadministrator mitteilen. Der Datenbankadministrator benötigt diese Informationen, da die Anzahl der Datenbankverbindungen der Anzahl der Verbindungen im Verbindungspool für die Datenquelle entspricht. Führen Sie dann die Schritte aus, um die Einstellungen für den Verbindungspool für Ihren Anwendungsserver und den Datenquellentyp wie unten beschrieben zu konfigurieren.

### Einstellungen für den Verbindungspool für WebLogic für Oracle und MySQL konfigurieren {#configure-connection-pool-settings-for-weblogic-for-oracle-and-mysql}

1. Klicken Sie unter &quot;Domain Structure&quot;auf Services > JDBC > Data Sources und anschließend im rechten Bereich auf IDP_DS.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte Configuration > Connection Pool und geben Sie in die folgenden Felder einen Wert ein:

   * Anfangskapazität
   * Maximale Kapazität
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie den verwalteten WebLogic-Server neu.

### Einstellungen für den Verbindungspool für WebLogic für SQLServer konfigurieren {#configure-connection-pool-settings-for-weblogic-for-sqlserver}

1. Klicken Sie im Change Center auf „Sperren und bearbeiten“
1. Klicken Sie unter &quot;Domain Structure&quot;auf Services > JDBC > Data Sources und anschließend im rechten Bereich auf EDC_DS.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte Configuration > Connection Pool und geben Sie in die folgenden Felder einen Wert ein:

   * Anfangskapazität
   * Maximale Kapazität
   * Capacity Increment
   * Statement Cache Size

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie den verwalteten WebLogic-Server neu.

### Einstellungen für den Verbindungspool für WebSphere für DB2 konfigurieren {#configure-connection-pool-settings-for-websphere-for-db2}

1. Klicken Sie in der Navigationsstruktur auf Resources > JDBC > JDBC Providers. Klicken Sie im rechten Bereich auf die erstellte Datenquelle, entweder DB2 Universal JDBC Driver Provider oder LiveCycle - db2 - IDP_DS.
1. Klicken Sie unter &quot;Additional Properties&quot;auf Data Sources und wählen Sie dann IDP_DS aus.
1. Klicken Sie im nächsten Bildschirm unter &quot;Additional Properties&quot;auf Connection Pool Properties und geben Sie einen Wert in das Feld Maximum Connections (Maximale Verbindungen) und das Feld Minimum Connections (Mindestverbindungen) ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to Master Configuration.

### Einstellungen für den Verbindungspool für WebSphere für Oracle konfigurieren {#configure-connection-pool-settings-for-websphere-for-oracle}

1. Klicken Sie in der Navigationsstruktur auf Resources > JDBC > JDBC Providers. Klicken Sie im rechten Bereich auf die erstellte Oracle JDBC Driver-Datenquelle.
1. Klicken Sie unter &quot;Additional Properties&quot;auf Data Sources und wählen Sie dann IDP_DS aus.
1. Klicken Sie im nächsten Bildschirm unter &quot;Additional Properties&quot;auf Connection Pool Properties und geben Sie einen Wert in das Feld Maximum Connections (Maximale Verbindungen) und das Feld Minimum Connections (Mindestverbindungen) ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to Master Configuration.

### Einstellungen für den Verbindungspool für WebSphere für SqlServer konfigurieren {#configure-connection-pool-settings-for-websphere-for-sqlserver}

1. Klicken Sie in der Navigationsstruktur auf Resources > JDBC > JDBC Providers und anschließend im rechten Bereich auf die von Ihnen erstellte Datenquelle User-Defined JDBC Driver .
1. Klicken Sie unter &quot;Additional Properties&quot;auf Data Sources und wählen Sie dann IDP_DS aus.
1. Klicken Sie im nächsten Bildschirm unter &quot;Additional Properties&quot;auf Connection Pool Properties und geben Sie einen Wert in das Feld Maximum Connections und das Feld Minimum Connections ein:
1. Klicken Sie auf OK oder Apply und dann auf Save directly to Master Configuration.

## Optimieren von Inline-Dokumenten und Auswirkungen auf den JVM-Speicher {#optimizing-inline-documents-and-impact-on-jvm-memory}

Wenn Sie in der Regel relativ kleine Dokumente verarbeiten, können Sie die mit der Geschwindigkeit der Dokumentübertragung und dem Speicherplatz verbundene Leistung verbessern. Implementieren Sie dazu die folgenden Produktkonfigurationen für AEM Formulare:

* Erhöhen Sie die standardmäßige Maximalgröße für Inline-Dokumente für AEM Formulare, sodass sie die Größe der meisten Dokumente übersteigt.
* Geben Sie für die Verarbeitung größerer Dateien Speicherordner an, die sich auf einem Hochgeschwindigkeits-Festplattensystem oder einem RAM-Datenträger befinden.

Die Inline-Maximalgröße und die Speicherordner (der temporäre Dateiordner für AEM Formulare und der Ordner des globalen Dokumentenspeichers) werden in Administration Console konfiguriert.

### Dokumentgröße und Inline-Maximalgröße {#document-size-and-maximum-inline-size}

Wenn ein Dokument, das von AEM Formularen zur Verarbeitung gesendet wird, kleiner oder gleich der standardmäßigen Maximalgröße für Inline-Dokumente ist, wird das Dokument inline auf dem Server gespeichert und als Adobe Document-Objekt serialisiert. Das Inline-Speichern von Dokumenten kann erhebliche Leistungsvorteile haben. Wenn Sie jedoch den Arbeitsablauf für Formulare verwenden, kann der Inhalt auch zu Tracking-Zwecken in der Datenbank gespeichert werden. Eine Erhöhung der Inline-Maximalgröße kann sich daher auf die Datenbankgröße auswirken.

Ein Dokument, das die Inline-Maximalgröße überschreitet, wird im lokalen Dateisystem gespeichert. Das Adobe Document -Objekt, das auf und vom Server übertragen wird, ist nur ein Zeiger auf diese Datei.

Wenn der Dokumentinhalt eingebettet wird (d. h. kleiner als die Inline-Maximalgröße ist), wird der Inhalt in der Datenbank als Teil der Serialisierungs-Payload des Dokuments gespeichert. Eine Erhöhung der Inline-Maximalgröße kann sich daher auf die Datenbankgröße auswirken.

**Inline-Maximalgröße ändern**

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie in das Feld &quot;Standardmäßige Maximalgröße für Inline-Dokumente&quot;einen Wert ein und klicken Sie auf &quot;OK&quot;.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft „Maximalgröße für Inline-Dokumente“ muss für die Umgebung von AEM Forms auf JEE und die Umgebung von AEM Forms auf JEE, die das Bundle AEM Forms unter OSGi enthält, identisch sein. Mit diesen Schritten wurde der Wert nur für die AEM Forms on JEE-Umgebung und nicht für AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung aktualisiert.

1. Starten Sie den Anwendungsserver mit der folgenden Systemeigenschaft neu:

   com.adobe.idp.defaultDocumentMaxInlineSize=`[value specified in Step 2]`

   >[!NOTE]
   >
   >Die oben genannte Systemeigenschaft überschreibt den Wert der Eigenschaft &quot;Max Inline Size&quot;des Dokuments, die für die AEM Forms on JEE-Umgebung und AEM Forms on OSGi-Bundle in der AEM Forms on JEE-Umgebung festgelegt ist.

>[!NOTE]
>
>Die standardmäßige Inline-Maximalgröße beträgt 65536 Byte.

### Maximale JVM-Heap-Größe {#jvm-maximum-heap-size}

Eine Erhöhung der Inline-Maximalgröße erfordert mehr Speicher zum Speichern der serialisierten Dokumente. Daher ist im Allgemeinen auch eine Erhöhung der maximalen JVM-Heap-Größe erforderlich.

Ein stark geladenes System, das viele Dokumente verarbeitet, kann den JVM-Heap-Speicher schnell überlasten. Um einen OutOfMemoryError zu vermeiden, erhöhen Sie die maximale JVM-Heap-Größe um einen Wert, der der Größe der Inline-Dokumente entspricht, multipliziert mit der Anzahl der Dokumente, die normalerweise zu einem bestimmten Zeitpunkt ausgeführt werden.

Maximale JVM-Heap-Größe erhöhen = (Größe von Inline-Dokumenten) x (durchschnittliche Anzahl verarbeiteter Dokumente).

**Maximale JVM-Heap-Größe berechnen**

In diesem Beispiel ist der aktuelle maximale JVM-Heap auf 512 MB und die Inline-Maximalgröße auf 64 KB eingestellt. Der Server muss für das Szenario konfiguriert werden, in dem 10 Aufträge gleichzeitig ausgeführt werden und jeder Auftrag 9 Eingabedateien und 1 Ergebnisdatei enthält (insgesamt 10 Dateien pro Auftrag und 100 gleichzeitig verarbeitete Dateien). Alle Dateien sind kleiner als 512 KB.

Um alle Dateien inline zu speichern, legen Sie die Inline-Maximalgröße auf mindestens 512 KB fest.

Die erforderliche Erhöhung der maximalen JVM-Heap-Größe wird mit der folgenden Gleichung berechnet:

(512 KB) x (100) = 51200 KB oder 50 MB

Die maximale JVM-Heap-Größe muss um 50 MB für insgesamt 562 MB erhöht werden.

**Heap-Fragmentierung berücksichtigen**

Wenn Sie die Größe von Inline-Dokumenten auf große Werte einstellen, erhöht sich das Risiko eines OutOfMemoryError auf Systemen, die anfällig für Heap-Fragmentierung sind. Um ein Dokument inline zu speichern, muss der JVM-Heap-Speicher über ausreichend zusammenhängenden Speicherplatz verfügen. Einige Betriebssysteme, JVMs und Speicherbereinigungsalgorithmen sind anfällig für Heap-Fragmentierung. Die Fragmentierung verringert den Umfang des zusammenhängenden Heap-Speicherplatzes und kann zu einem OutOfMemoryError führen, selbst wenn ausreichend freier Speicherplatz vorhanden ist.

Beispielsweise haben frühere Vorgänge auf dem Anwendungsserver den JVM-Heap in einem fragmentierten Zustand hinterlassen, und der Garbage Collector kann den Heap nicht ausreichend komprimieren, um große Blöcke freien Speicherplatz zurückzugewinnen. Ein OutOfMemoryError kann auftreten, auch wenn die maximale JVM-Heap-Größe an die Erhöhung der Inline-Maximalgröße angepasst wurde.

Um die Heap-Fragmentierung zu berücksichtigen, darf die Inline-Dokumentgröße nicht höher als 0,1 % der gesamten Heap-Größe sein. Beispielsweise kann eine maximale JVM-Heap-Größe von 512 MB eine Inline-Maximalgröße von 512 MB x 0,001 = 0,512 MB oder 512 KB unterstützen.

## Verbesserungen für WebSphere Application Server {#websphere-application-server-enhancements}

In diesem Abschnitt werden Einstellungen beschrieben, die für eine WebSphere Application Server-Umgebung spezifisch sind.

### Erhöhen des der JVM zugewiesenen maximalen Arbeitsspeichers {#increasing-the-maximum-memory-allocated-to-the-jvm}

Wenn Sie Configuration Manager ausführen oder versuchen, Enterprise JavaBeans (EJB)-Bereitstellungscode mithilfe des Befehlszeilen-Dienstprogramms zu generieren *ejbdeploy* und ein Fehler wegen ungenügenden Speicherplatzes auftritt, erhöhen Sie die der JVM zugewiesene Speichermenge.

1. Bearbeiten Sie im Ordner „*[Programm-Server-Stammordner]*/deploytool/itp/“ das Skript „ejbdeploy“:

   * (Windows) `ejbdeploy.bat`
   * (Linux und UNIX) `ejbdeploy.sh`

1. Suchen Sie den Parameter `-Xmx256M` und erhöhen Sie dessen Wert, z. B. auf `-Xmx1024M`.
1. Speichern Sie die Datei.
1. Führen Sie den Befehl `ejbdeploy` aus oder führen Sie mit dem Configuration Manager eine erneute Bereitstellung aus.

## Verbessern der Leistung von Windows Server 2003 mit LDAP {#improving-windows-server-2003-performance-with-ldap}

In diesem Abschnitt werden Einstellungen beschrieben, die für eine Microsoft Windows Server 2003-Betriebssystemumgebung spezifisch sind.

Durch die Verwendung von Verbindungspools für die Suchverbindung kann die Anzahl der benötigten Ports um bis zu 50 % reduziert werden. Der Grund dafür ist, dass diese Verbindung immer dieselben Berechtigungen für eine bestimmte Domain verwendet und darüber hinaus der Kontext und die entsprechenden Objekte ausdrücklich geschlossen werden.

### Windows Server für Verbindungspools konfigurieren {#configure-your-windows-server-for-connection-pooling}

1. Klicken Sie auf „Start“ > „Ausführen“, um den Registrierungs-Editor zu starten. Geben Sie dann in das Feld „Öffnen“ den Befehl `regedit` ein und klicken Sie auf „OK“.
1. Wechseln Sie zum Registrierungsschlüssel `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`
1. Suchen Sie im rechten Bereich des Registrierungs-Editors den Wertnamen TcpTimedWaitDelay . Wenn der Name nicht angezeigt wird, wählen Sie in der Menüleiste Bearbeiten > Neu > DWORD-Wert aus, um den Namen hinzuzufügen.
1. Geben Sie in das Feld „Name“`TcpTimedWaitDelay`

   >[!NOTE]
   >
   >Wenn in dem Feld weder ein blinkender Cursor noch der Text `New Value #` angezeigt wird, klicken Sie mit der rechten Maustaste in den rechten Bereich, wählen Sie „Umbenennen“ und geben Sie im Feld „Name“ `TcpTimedWaitDelay`*ein.*

1. Wiederholen Sie Schritt 4 für die Wertnamen MaxUserPort, MaxHashTableSize und MaxFreeTcbs.
1. Doppelklicken Sie im rechten Bereich auf , um den Wert TcpTimedWaitDelay festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `30`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxUserPort“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65534`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxHashTableSize“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `65536`.
1. Doppelklicken Sie im rechten Bereich, um den Wert „MaxFreeTcbs“ festzulegen. Wählen Sie unter „Basis“ die Option „Dezimal“ und geben Sie in das Feld „Wert“ den Wert `16000`.

>[!NOTE]
>
>Wenn Sie die Registrierung mit dem Registrierungs-Editor oder einer anderen Methode falsch ändern, können schwerwiegende Probleme auftreten. Diese Probleme erfordern möglicherweise, dass Sie Ihr Betriebssystem neu installieren. Ändern Sie die Registrierung auf eigene Gefahr.
