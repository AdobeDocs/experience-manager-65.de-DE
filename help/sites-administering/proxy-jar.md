---
title: Proxy-Server-Tool (proxy.jar)
description: Erfahren Sie mehr über das Proxy-Server-Tool (proxy.jar) in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: 3df50303-5cdd-4df0-abec-80831d2ccef7
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 96%

---

# Proxy-Server-Tool (proxy.jar){#proxy-server-tool-proxy-jar}

Der Proxy-Server fungiert als Zwischen-Server, der Anforderungen zwischen einem Client und einem Server weiterleitet. Der Proxy-Server verfolgt alle Interaktionen zwischen Client und Server und gibt ein Protokoll der gesamten TCP-Kommunikation aus. Auf diese Weise können Sie die Vorgänge genau überwachen, ohne auf den Haupt-Server zugreifen zu müssen.

Sie finden den Proxy-Server im entsprechenden Installationsordner:

* &lt;cq_install_path>/opt/helpers/proxy.jar
* &lt;crx_install_path>/opt/helpers/proxy.jar

Sie können den Proxy-Server verwenden, um alle Interaktionen zwischen Client und Server unabhängig vom zugrunde liegenden Kommunikationsprotokoll zu überwachen. Sie können beispielsweise folgende Protokolle überwachen:

* HTTP für Web-Seiten
* HTTPS für sichere Web-Seiten
* SMTP für E-Mail-Nachrichten
* LDAP für die Benutzerverwaltung

Sie können den Proxy-Server zum Beispiel zwischen zwei Anwendungen schalten, die über ein TCP/IP-Netzwerk kommunizieren, etwa einem Webbrowser und AEM. So können Sie genau überprüfen, was passiert, wenn Sie eine CQ-Seite abrufen.

## Starten des Proxy-Server-Tools {#starting-the-proxy-server-tool}

Das Tool befindet sich im Ordner /opt/helpers Ihrer AEM-Installation. Geben Sie Folgendes ein, um es zu starten:

```xml
java -jar proxy.jar <host> <remoteport> <localport> [options]
```

### Optionen {#options}

* **q (leiser Modus)** Die Anforderungen werden nicht im Konsolenfenster angezeigt. Verwenden Sie dies, wenn Sie die Verbindung nicht verlangsamen oder die Ausgabe in einer Datei protokollieren möchten (siehe Option -logfile).
* **b (binärer Modus)** Aktivieren Sie den binären Modus, wenn Sie nach bestimmten Byte-Kombinationen im Traffic suchen. Die Ausgabe enthält die hexadezimale und die Zeichenausgabe.
* **t (Zeitstempelprotokolleinträge)** Fügt zu jeder Protokollausgabe einen Zeitstempel hinzu. Der Zeitstempel wird in Sekunden angegeben, sodass er möglicherweise nicht zur Überprüfung einzelner Anforderungen geeignet ist. Verwenden Sie ihn, um Ereignisse zu suchen, die zu einem bestimmten Zeitpunkt aufgetreten sind, wenn Sie den Proxy-Server über einen längeren Zeitraum verwenden.
* **logfile &lt;filename> (In Protokolldatei schreiben):** Verwenden Sie diese Option, um die Konversation zwischen Client und Server in eine Protokolldatei zu schreiben. Dieser Parameter funktioniert auch im stillen Modus.
* **i &lt;numIndentions> (Einzug hinzufügen)** Jede aktive Verbindung wird zwecks besserer Lesbarkeit eingerückt. Der Standardwert beträgt 16 Stufen. (Neu in proxy.jar Version 1.16).

## Verwendungsmöglichkeiten des Proxy-Server-Tools {#uses-of-the-proxy-server-tool}

In den folgenden Szenarien werden ein paar Einsatzzwecke demonstriert, für die das Proxyserver-Tool eingesetzt werden können:

**Überprüfen auf Cookies und ihre Werte**

Das folgende Beispiel eines Protokolleintrags zeigt alle Cookies und deren Werte, die vom Client bei der sechsten seit dem Proxy-Start geöffneten Verbindung gesendet wurden:

```xml
C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]
```

**Überprüfen auf Header und ihre Werte** Das folgende Beispiel eines Protokolleintrags zeigt, dass der Server eine Keep-Alive-Verbindung herstellen kann und der Inhaltslängen-Header ordnungsgemäß festgelegt wurde:

```xml
S-7-#000017 -> [Connection: Keep-Alive ]
...
S-7-#000107 -> [Content-Length: 124 ]
```

**Überprüfen der Funktionsfähigkeit von Keep-Alive**

**Keep-Alive** bedeutet, dass ein Client die Verbindung zum Server wiederverwendet, um mehrere Dateien (Seiten-Code, Bilder, Stylesheets usw.) zu übertragen. Ohne Keep-Alive muss der Client für jede Anfrage eine neue Verbindung aufbauen.

So überprüfen Sie, ob Keep-Alive funktioniert:

1. Starten Sie den Proxy-Server.
1. Fragen Sie eine Seite an.

* Wenn Keep-Alive funktioniert, sollte der Verbindungszähler nie über 5 bis 10 Verbindungen hinausgehen.
* Wenn Keep-Alive nicht funktioniert, steigt der Verbindungszähler schnell.

**Finden verlorener Anfragen**

Wenn Sie Anforderungen in einer komplexen Servereinstellung verlieren, z. B. mit einer Firewall und einem Dispatcher, können Sie den Proxy-Server verwenden, um herauszufinden, wo die Anforderung verloren ging. Wenn eine Firewall vorhanden ist:

1. Starten Sie einen Proxy vor der Firewall.
1. Starten Sie einen weiteren Proxy hinter der Firewall.
1. Verwenden Sie die Proxys, um herauszufinden, wie weit die Anfragen kommen.

**Hängende Anfragen**

Gehen Sie wie folgt vor, wenn gelegentlich hängende Anfragen auftreten:

1. Starten Sie proxy.jar.
1. Warten Sie oder schreiben Sie das Zugriffsprotokoll in eine Datei, in der jeder Eintrag einen Zeitstempel aufweist.
1. Wenn die Anfrage zu hängen beginnt, können Sie sehen, wie viele Verbindungen offen waren und welche Anfrage dafür verantwortlich ist.

## Das Format von Protokollmeldungen {#the-format-of-log-messages}

Die von proxy.jar erstellten Protokolleinträge haben das folgende Format:

```xml
[timestamp (optional)] [<b>C</b>lient|<b>S</b>erver]-[ConnectionNumber]-[BytePosition] ->[Character Stream]
```

So kann eine Web-Seitenanfrage zum Beispiel wie folgt aussehen:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]
```

* „C“ gibt an, dass dieser Eintrag vom Client stammt (es handelt sich dabei um die Anfrage einer Web-Seite).
* „0“ ist die Verbindungsnummer (der Verbindungszähler startet bei 0).
* #00000 ist der Versatz im Bytestream. Hierbei handelt es sich um den ersten Eintrag, weshalb der Versatz bei 0 ist.
* [GET &lt;?>] ist der Inhalt der Anfrage, im Beispiel eine der HTTP-Kopfzeilen (URL).

Wenn eine Verbindung geschlossen wird, werden die folgenden Informationen protokolliert:

```xml
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Hier werden die Anzahl der Bytes, die zwischen dem Client und dem Server bei der 6. Verbindung übertragen wurden, und die durchschnittliche Geschwindigkeit angegeben.

## Beispiel für eine Protokollausgabe {#an-example-of-log-output}

Sehen Sie sich diese einfache Vorlage an, die bei Anforderung folgenden Code erzeugt:

```xml
<html>
  <head>
    <title>Welcome</title>
  </head>
  <body>
    Welcome to Playground<br>
    <img src="/logo.gif">
  </body>
</html>
```

Wenn AEM auf „localhost:4303“ ausgeführt wird, starten Sie den Proxy-Server wie folgt:

```xml
java -jar proxy.jar localhost 4303 4444 -logfile test.log
```

Sie können ohne den Proxy-Server auf den Server zugreifen (`localhost:4303`). Wenn Sie jedoch über `localhost:4444` auf ihn zugreifen, protokolliert der Proxy-Server die Kommunikation. Öffnen Sie einen Browser und rufen Sie eine Seite auf, die mit der vorherigen Vorlage erstellt wurde.  Sehen Sie sich anschließend die Protokolldatei an.

>[!NOTE]
>
>Bis zur Version 1.14 von proxy.jar werden die Protokolleinträge einer Verbindung nicht synchronisiert, was bedeutet, dass die Protokolleinträge einer Client-/Server-Verbindung nicht zwangsläufig in der sequenziellen Reihenfolge angegeben sind.  Bei neueren Versionen (ab 1.14) des Proxy-Servers tritt dieses Problem nicht auf.

Beim Starten werden die folgenden Informationen in das Protokoll geschrieben:

```xml
starting proxy for localhost:4303 on port 4444
using logfile: C:\CQUnify355default\opt\helpers\test.log
```

Die folgenden Kopfzeilenfelder werden beim Start der ersten Verbindung (0) aufgeführt, bei der die HTML-Hauptseite angefordert wird:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102936796533 HTTP/1.1 ]
C-0-#000053 -> [Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-powerpoint, application/vnd.ms-excel, application/msword, appl]
C-0-#000194 -> [ication/x-shockwave-flash, */* ]
C-0-#000227 -> [Accept-Language: de-ch ]
C-0-#000251 -> [Accept-Encoding: gzip, deflate ]
C-0-#000283 -> [User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0) ]
C-0-#000347 -> [Host: localhost:4444 ]
```

Der Client fordert eine Keep-Alive-Verbindung an, damit der Server mehrere Dateien über dieselbe Verbindung senden kann:

```xml
C-0-#000369 -> [Connection: Keep-Alive ]
```

Der Proxy-Server ist ein geeignetes Tool, um zu überprüfen, ob Cookies richtig gesetzt werden oder nicht. Hier sehen Sie Folgendes:

* den von AEM generierten cq3session-Cookie
* den von CFC generierten „show mode switch“-Cookie
* Ein Cookie mit dem Namen JSESSIONID. Dieses wird automatisch von JSP erstellt, wenn Sie die Verwendung dieses Cookies nicht ausdrücklich über &lt;%@ page session=&quot;false&quot; %> deaktiviert haben:

```xml
C-0-#000393 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-0-#000514 -> [ ]
S-0-#000000 -> [HTTP/1.0 200 OK ]
```

Der Server schließt die Verbindung 0 nach der Anfrage.  Eine Keep-Alive-Verbindung ist nicht möglich, da die Anfrage ein Fragezeichen enthält.  Dies bedeutet, dass der Server keine Cache-gespeicherte Version zurückgeben und deshalb an diesem Punkt auch nicht die Länge des Inhalts bestimmen kann. Dies ist jedoch für eine Keep-Alive-Verbindung erforderlich.

```xml
S-0-#000017 -> [Connection: Close ]
S-0-#000036 -> [Server: Communique Servlet Engine/3.5.5 ]
S-0-#000077 -> [Content-Type: text/html;charset=iso-8859-1 ]
S-0-#000121 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-0-#000158 -> [Set-Cookie: JSESSIONID=4161a56b-f193-d8-88a5-e09c5ff7ef2a;Path=/author ]
S-0-#000232 -> [ ]
```

Hier beginnt der Server, den HTML-Code über die Verbindung 0 zu senden:

```xml
S-0-#000234 -> [<html> ]
S-0-#000242 -> [.<head> ]
S-0-#000251 -> [..<title>Welcome</title> ]
S-0-#000277 -> [.</head> ]
S-0-#000287 -> [.<body> ]
S-0-#000296 -> [..Welcome to Playground<br> ]
S-0-#000325 -> [..<img src="/author/logo.gif"> ]
S-0-#000357 -> [.</body> ]
S-0-#000367 -> [</html>]
```

Die Verbindung 0 wird unmittelbar nach der Bereitstellung der HTML-Datei geschlossen:

```xml
C-0-Finished: 516 bytes (0.0 kb/s)
S-0-Finished: 374 bytes (0.0 kb/s)
```

Nun wird die Ausgabe für die Verbindung 1 gestartet, wobei das im HTML-Code enthaltene Bild heruntergeladen wird:

```xml
C-1-#000000 -> [GET /author/logo.gif HTTP/1.1 ]
C-1-#000031 -> [Accept: */* ]
C-1-#000044 -> [Referer: http://localhost:4444/author/prox.html?CFC_cK=1102936796533 ]
C-1-#000114 -> [Accept-Language: de-ch ]
C-1-#000138 -> [Accept-Encoding: gzip, deflate ]
C-1-#000170 -> [User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0) ]
C-1-#000234 -> [Host: localhost:4444 ]
```

Der Client fordert erneut eine Keep-Alive-Verbindung an:

```xml
C-1-#000256 -> [Connection: Keep-Alive ]
C-1-#000280 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-1-#000401 -> [ ]
S-1-#000000 -> [HTTP/1.0 200 OK ]
```

Für die Verbindung 1 kann der Server eine Keep-Alive-Verbindung bereitstellen, da das Bild statisch und somit die Länge des Inhalts bekannt ist.

```xml
S-1-#000017 -> [Connection: Keep-Alive ]
S-1-#000041 -> [Server: Communique Servlet Engine/3.5.5 ]
S-1-#000082 -> [Content-Type: image/gif ]
```

Der Server gibt die Länge des Inhalts des Bilds über die Verbindung 1 zurück:

```xml
S-1-#000107 -> [Content-Length: 124 ]
S-1-#000128 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-1-#000165 -> [ ]
```

Nun, da die Länge des Inhalts festgelegt ist, sendet der Server die Bilddaten über die Verbindung 1:

```xml
S-1-#000167 -> [GIF87a..........................,.......
...I....0.A..8......YDA.W...1..`i.`..6...Z...$@.F..)`..f..A.....iu.........$..;]
```

Nachdem die maximale Wartezeit für das Keep-Alive erreicht wurde, wird auch die Verbindung 1 geschlossen:

```xml
S-1-Finished: 291 bytes (0.0 kb/s)
C-1-Finished: 403 bytes (0.0 kb/s)
```

Das obige Beispiel ist verhältnismäßig einfach, da die beiden Verbindungen nacheinander aufgebaut werden:

* Zuerst gibt der Server den HTML-Code zurück;
* dann fordert der Browser das Bild an und öffnet eine neue Verbindung.

In der Praxis generiert eine Seite möglicherweise viele parallele Anforderungen für Bilder, Stylesheets und JavaScript-Dateien. Dies bedeutet, dass die Protokolle sich überlappende Einträge von parallel geöffneten Verbindungen enthalten.  In diesem Fall empfiehlt Adobe der Lesbarkeit halber, die Option „-i“ zu verwenden.
