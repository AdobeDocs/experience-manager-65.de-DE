---
title: Proxy-Server-Tool (proxy.jar)
seo-title: Proxy Server Tool (proxy.jar)
description: Erfahren Sie mehr über das Proxy-Server-Tool in AEM.
seo-description: Learn about the Proxy Server Tool in AEM.
uuid: 2fc1df24-8d5a-4be7-83fa-238ae65591b0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: ca98dc3c-7056-4cdc-b4d3-23e471da5730
docset: aem65
exl-id: 3df50303-5cdd-4df0-abec-80831d2ccef7
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 22%

---

# Proxy-Server-Tool (proxy.jar){#proxy-server-tool-proxy-jar}

Der Proxyserver fungiert als Zwischenserver, der Anforderungen zwischen einem Client und einem Server weiterleitet. Der Proxy-Server verfolgt alle Interaktionen zwischen Client und Server und gibt ein Protokoll der gesamten TCP-Kommunikation aus. Dadurch können Sie genau überwachen, was passiert, ohne auf den Hauptserver zugreifen zu müssen.

Sie finden den Proxyserver im entsprechenden Installationsordner:

* &lt;cq_install_path>/opt/helpers/proxy.jar
* &lt;crx_install_path>/opt/helpers/proxy.jar

Sie können den Proxy-Server verwenden, um alle Interaktionen zwischen Client und Server unabhängig vom zugrunde liegenden Kommunikationsprotokoll zu überwachen. Sie können beispielsweise die folgenden Protokolle überwachen:

* HTTP für Webseiten
* HTTPS für sichere Webseiten
* SMTP für E-Mail-Nachrichten
* LDAP für die Benutzerverwaltung

Sie können beispielsweise den Proxyserver zwischen zwei Anwendungen positionieren, die über ein TCP/IP-Netzwerk kommunizieren. z. B. einen Webbrowser und AEM. Auf diese Weise können Sie genau überwachen, was passiert, wenn Sie eine AEM Seite anfordern.

## Starten des Proxyserver-Tools {#starting-the-proxy-server-tool}

Das Tool befindet sich im Ordner /opt/helpers Ihrer AEM-Installation. Geben Sie Folgendes ein, um es zu starten:

```xml
java -jar proxy.jar <host> <remoteport> <localport> [options]
```

### Optionen {#options}

* **q (leiser Modus)** Die Anforderungen werden nicht in das Konsolenfenster geschrieben. Verwenden Sie dies, wenn Sie die Verbindung nicht verlangsamen möchten oder die Ausgabe in einer Datei protokollieren (siehe Option -logfile ).
* **b (binärer Modus)** Wenn Sie nach bestimmten Byte-Kombinationen im Traffic suchen, aktivieren Sie den Binärmodus. Die Ausgabe enthält dann die Hexadezimal- und die Zeichenausgabe.
* **t (Zeitstempelprotokolleinträge)** Fügt jeder Protokollausgabe einen Zeitstempel hinzu. Der Zeitstempel wird in Sekunden angegeben, sodass er möglicherweise nicht für die Überprüfung einzelner Anforderungen geeignet ist. Verwenden Sie sie, um Ereignisse zu suchen, die zu einem bestimmten Zeitpunkt aufgetreten sind, wenn Sie den Proxyserver über einen längeren Zeitraum verwenden.
* **logfile &lt;filename> (In Protokolldatei schreiben):** Verwenden Sie diese Option, um die Konversation zwischen Client und Server in eine Protokolldatei zu schreiben. Dieser Parameter funktioniert auch im stillen Modus.
* **i &lt;numindentions> (Einzug hinzufügen)** Jede aktive Verbindung wird für eine bessere Lesbarkeit eingerückt. Der Standardwert ist 16 Ebenen. (Neu in proxy.jar Version 1.16).

## Verwendung des Proxyserver-Tools {#uses-of-the-proxy-server-tool}

In den folgenden Szenarien werden ein paar Einsatzzwecke demonstriert, für die das Proxyserver-Tool eingesetzt werden können:

**Suchen nach Cookies und ihren Werten**

Das folgende Beispiel für einen Protokolleintrag zeigt alle Cookies und deren Werte, die vom Client bei der 6. seit dem Proxy-Start geöffneten Verbindung gesendet wurden:

```xml
C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]
```

**Überprüfen von Kopfzeilen und ihren Werten** Das folgende Beispiel für einen Protokolleintrag zeigt, dass der Server eine Keep-Alive-Verbindung herstellen kann und der Header für die Inhaltslänge ordnungsgemäß festgelegt wurde:

```xml
S-7-#000017 -> [Connection: Keep-Alive ]
...
S-7-#000107 -> [Content-Length: 124 ]
```

**Überprüfen der Funktionsfähigkeit von Keep-Alive**

**Keep-Alive** bedeutet, dass ein Client die Verbindung zum Server wiederverwendet, um mehrere Dateien (Seiten-Code, Bilder, Stylesheets usw.) zu transportieren. Ohne Keep-Alive muss der Client für jede Anfrage eine neue Verbindung aufbauen.

So überprüfen Sie, ob Keep-Alive funktioniert:

1. Starten Sie den Proxyserver.
1. Fragen Sie eine Seite an.

* Wenn Keep-Alive funktioniert, sollte der Verbindungszähler nie über 5 bis 10 Verbindungen hinausgehen.
* Wenn Keep-Alive nicht funktioniert, steigt der Verbindungszähler schnell.

**Finden verlorener Anfragen**

Sollten Anfragen in einer komplexen Serverumgebung, zum Beispiel einer mit Firewall und Dispatcher, verloren gehen, können Sie den Proxyserver verwenden, um herauszufinden, wo die Anfrage verloren ging. Bei einer Firewall:

1. Proxy vor einer Firewall starten
1. Starten Sie einen weiteren Proxy nach einer Firewall.
1. Verwenden Sie die Proxys, um herauszufinden, wie weit die Anfragen kommen.

**Hängende Anfragen**

Gehen Sie wie folgt vor, wenn gelegentlich hängende Anfragen auftreten:

1. Starten Sie proxy.jar.
1. Warten oder schreiben Sie das Zugriffsprotokoll in eine Datei, wobei jeder Eintrag einen Zeitstempel aufweist.
1. Wenn die Anfrage anfängt zu hängen, können Sie sehen, wie viele Verbindungen offen waren und welche Anfrage dafür verantwortlich ist.

## Das Format von Protokollmeldungen {#the-format-of-log-messages}

Die von proxy.jar erstellten Protokolleinträge haben alle das folgende Format:

```xml
[timestamp (optional)] [<b>C</b>lient|<b>S</b>erver]-[ConnectionNumber]-[BytePosition] ->[Character Stream]
```

So kann eine Web-Seitenanfrage zum Beispiel wie folgt aussehen:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]
```

* „C“ gibt an, dass dieser Eintrag vom Client stammt (es handelt sich dabei um die Anfrage einer Web-Seite).
* 0 ist die Verbindungsnummer (der Verbindungszähler beginnt bei 0)
* #00000 ist der Versatz im Bytestream. Hierbei handelt es sich um den ersten Eintrag, weshalb der Versatz bei 0 ist.
* [GET &lt;?>] ist der Inhalt der Anfrage, im Beispiel eine der HTTP-Kopfzeilen (URL).

Wenn eine Verbindung geschlossen wird, werden die folgenden Informationen protokolliert:

```xml
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Zeigt die Anzahl der Bytes an, die zwischen Client und Server bei der 6. Verbindung und mit der durchschnittlichen Geschwindigkeit übergeben wurden.

## Beispiel einer Protokollausgabe {#an-example-of-log-output}

Wir werden eine einfache Vorlage überprüfen, die bei Bedarf folgenden Code erzeugt:

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

Wenn AEM auf localhost:4303 ausgeführt wird, starten Sie den Proxyserver wie folgt:

```xml
java -jar proxy.jar localhost 4303 4444 -logfile test.log
```

Sie können ohne den Proxyserver auf den Server zugreifen (`localhost:4303`), wenn Sie jedoch über `localhost:4444` auf ihn zugreifen, protokolliert der Proxyserver die Kommunikation. Öffnen Sie einen Browser und greifen Sie auf eine mit der obigen Vorlage erstellte Seite zu. Sehen Sie sich danach die Protokolldatei an.

>[!NOTE]
>
>Bis Version 1.14 von proxy.jar werden die Protokolleinträge einer Verbindung nicht synchronisiert, was bedeutet, dass die Protokolleinträge einer Client/Server-Verbindung nicht in der richtigen sequenziellen Reihenfolge benötigt werden. In den neueren Versionen (>=1.14) des Proxyservers tritt dieses Problem nicht auf.

Beim Start werden die folgenden Informationen in das Protokoll geschrieben:

```xml
starting proxy for localhost:4303 on port 4444
using logfile: C:\CQUnify355default\opt\helpers\test.log
```

Die folgenden Kopfzeilenfelder werden am Anfang der ersten Verbindung (0) aufgelistet, die die Hauptseite der HTML anfordert:

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

Der Proxy-Server ist ein gutes Tool, um zu überprüfen, ob Cookies richtig gesetzt sind oder nicht. Hier sehen wir Folgendes:

* von AEM generiertes cq3session -Cookie
* das vom CFC generierte Switch-Cookie für den Anzeigemodus
* ein Cookie mit dem Namen JSESSIONID; wird dies automatisch von JSP erstellt, wenn nicht explizit mit &lt;%@ page session=&quot;false&quot; %> deaktiviert wird:

```xml
C-0-#000393 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-0-#000514 -> [ ]
S-0-#000000 -> [HTTP/1.0 200 OK ]
```

Der Server schließt die Verbindung 0 nach der Anfrage. Keep-Alive ist nicht möglich, da die Anfrage ein Fragezeichen aufweist. Das bedeutet, dass der Server keine zwischengespeicherte Version zurückgeben kann und daher die Inhaltslänge zu diesem Zeitpunkt nicht ermitteln kann, was für eine Keep-Alive-Verbindung erforderlich ist.

```xml
S-0-#000017 -> [Connection: Close ]
S-0-#000036 -> [Server: Communique Servlet Engine/3.5.5 ]
S-0-#000077 -> [Content-Type: text/html;charset=iso-8859-1 ]
S-0-#000121 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-0-#000158 -> [Set-Cookie: JSESSIONID=4161a56b-f193-d8-88a5-e09c5ff7ef2a;Path=/author ]
S-0-#000232 -> [ ]
```

Hier beginnt der Server, den HTML-Code bei Verbindung 0 zu senden:

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

Die Verbindung 0 wird unmittelbar nach dem Bereitstellen der HTML-Datei geschlossen:

```xml
C-0-Finished: 516 bytes (0.0 kb/s)
S-0-Finished: 374 bytes (0.0 kb/s)
```

Jetzt beginnt die Ausgabe für Verbindung 1, die das im HTML-Code enthaltene Bild herunterlädt:

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

Für Verbindung 1 kann der Server Keep-Alive-Funktion bereitstellen, da das Bild statisch ist und daher die Inhaltslänge bekannt ist.

```xml
S-1-#000017 -> [Connection: Keep-Alive ]
S-1-#000041 -> [Server: Communique Servlet Engine/3.5.5 ]
S-1-#000082 -> [Content-Type: image/gif ]
```

Der Server gibt die Inhaltslänge des Bildes für Verbindung 1 zurück:

```xml
S-1-#000107 -> [Content-Length: 124 ]
S-1-#000128 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-1-#000165 -> [ ]
```

Nachdem die Inhaltslänge festgelegt ist, sendet der Server die Bilddaten für Verbindung 1:

```xml
S-1-#000167 -> [GIF87a..........................,.......
...I....0.A..8......YDA.W...1..`i.`..6...Z...$@.F..)`..f..A.....iu.........$..;]
```

Nachdem der Keep-Alive-Timeout erreicht wurde, wird auch die Verbindung 1 geschlossen:

```xml
S-1-Finished: 291 bytes (0.0 kb/s)
C-1-Finished: 403 bytes (0.0 kb/s)
```

Das obige Beispiel ist vergleichsweise einfach, da die beiden Verbindungen nacheinander auftreten:

* zuerst gibt der Server den HTML-Code zurück.
* dann fordert der Browser das Bild an und öffnet eine neue Verbindung.

In der Praxis kann eine Seite viele parallele Anforderungen für Bilder, Stylesheets, JavaScript-Dateien usw. generieren. Dies bedeutet, dass die Protokolle überlappende Einträge von parallelen offenen Verbindungen aufweisen. In diesem Fall wurde die Verwendung von Option -i zur Verbesserung der Lesbarkeit empfohlen.
