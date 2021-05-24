---
title: Proxyserver-Tool (proxy.jar)
seo-title: Proxyserver-Tool (proxy.jar)
description: Erfahren Sie mehr über das Proxyserver-Tool in AEM.
seo-description: Erfahren Sie mehr über das Proxyserver-Tool in AEM.
uuid: 2fc1df24-8d5a-4be7-83fa-238ae65591b0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: ca98dc3c-7056-4cdc-b4d3-23e471da5730
docset: aem65
exl-id: 3df50303-5cdd-4df0-abec-80831d2ccef7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 97%

---

# Proxyserver-Tool (proxy.jar){#proxy-server-tool-proxy-jar}

Ein Proxyserver fungiert als zwischengeschalteter Server, der Anfragen zwischen einem Client und einem Server weiterreicht. Der Proxyserver speichert alle Interaktionen zwischen Client und Server und erstellt ein Protokoll der gesamten TCP-Kommunikation. So können Sie sämtliche Aktivitäten genau überwachen und müssen nicht auf den Hauptserver zugreifen.

Sie finden den Proxyserver im entsprechenden Installationsordner:

* &lt;CQ_Installationspfad>/opt/helpers/proxy.jar
* &lt;CRX_Installationspfad>/opt/helpers/proxy.jar

Sie können den Proxyserver verwenden, um alle Interaktionen zwischen Client und Server zu überwachen, unabhängig vom zugrunde liegenden Kommunikationsprotokoll. So können Sie beispielsweise die folgenden Protokolle überwachen:

* HTTP für Webseiten
* HTTPS für sichere Webseiten
* SMTP für E-Mail-Nachrichten
* LDAP für die Benutzerverwaltung

Sie können den Proxyserver zum Beispiel zwischen zwei Anwendungen schalten, die über ein TCP/IP-Netzwerk kommunizieren, etwa einem Webbrowser und AEM. So können Sie genau überprüfen, was passiert, wenn Sie eine AEM-Seite anfordern.

## Starten des Proxyservertools  {#starting-the-proxy-server-tool}

Das Tool befindet sich im Ordner /opt/helpers Ihrer AEM Installation. Geben Sie Folgendes ein, um es zu starten:

```xml
java -jar proxy.jar <host> <remoteport> <localport> [options]
```

### Optionen {#options}

* **q (Stiller Modus):** Die Anfragen werden nicht in das Konsolenfenster geschrieben. Verwenden Sie die Option, wenn Sie die Verbindung entlasten möchten oder wenn Sie die Ausgabe in einer Datei protokollieren (siehe Option „-logfile“).
* **b (Binärer Modus):** Aktivieren Sie den binären Modus, wenn Sie nach bestimmten Bytekombinationen im Datenverkehr suchen. Die Ausgabe enthält anschließend die Hexadezimal- und Zeichenausgabe.
* **t (Zeitstempel-Protokolleinträge):** Verwenden Sie diese Option, um einen Zeitstempel an jede Protokollausgabe anzuhängen. Der Zeitstempel wird in Sekunden angegeben, weshalb er möglicherweise nicht zur Prüfung einzelner Anfragen geeignet ist. Verwenden Sie die Option, um Ereignisse ausfindig zu machen, die zu einem bestimmten Zeitpunkt erfolgt sind, wenn Sie den Proxyserver über einen längeren Zeitraum nutzen.
* **logfile &lt;Dateiname> (In Protokolldatei schreiben):** Verwenden Sie diese Option, um die Konversation zwischen Client und Server in eine Protokolldatei zu schreiben. Dieser Parameter kann auch im stillen Modus genutzt werden.
* **i &lt;numIndentions> (Einzug hinzufügen)**: Verwenden Sie diese Option, um jede aktive Verbindung der Lesbarkeit halber einzurücken. Der Standardwert beträgt 16 Ebenen. (Neu in der proxy.jar-Version 1.16).

## Einsatzzwecke für das Proxyserver-Tool  {#uses-of-the-proxy-server-tool}

In den folgenden Szenarien werden ein paar Einsatzzwecke demonstriert, für die das Proxyserver-Tool eingesetzt werden können:

**Überprüfen von Cookies und ihren Werten**

Der folgende beispielhafte Protokolleintrag enthält alle Cookies, die vom Client bei der sechsten Verbindung seit Proxystart gesendet wurden, und ihre Werte:

```xml
C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]
```

**Überprüfen von Kopfzeilen und ihren Werten** Der folgende beispielhafte Protokolleintrag zeigt, dass der Server eine „Keep-Alive“-Verbindung herstellen kann und die „Content-Length“-Kopfzeile richtig festgelegt wurde:

```xml
S-7-#000017 -> [Connection: Keep-Alive ]
...
S-7-#000107 -> [Content-Length: 124 ]
```

**Überprüfen der Funktionsfähigkeit von Keep-Alive**

**Keep-Alive** bedeutet, dass ein Client die Verbindung zum Server wiederverwendet, um mehrere Dateien zu transportieren (den Seiten-Code, Bilder, Stylesheets usw.). Ohne Keep-Alive muss der Client für jede Anforderung eine neue Verbindung aufbauen.

So überprüfen Sie, ob Keep-Alive funktioniert:

1. Starten Sie den Proxyserver.
1. Fordern Sie eine Seite an.

* Falls Keep-Alive funktioniert, sollte der Verbindungszähler immer nur auf einen Wert zwischen 5–10 Verbindungen ansteigen.
* Sollte Keep-Alive nicht funktionieren, erhöht sich dieser Wert sehr schnell.

**Finden verlorener Anforderungen**

Sollten Anforderungen in einer komplexen Serverumgebung, zum Beispiel einer mit Firewall und Dispatcher, verloren gehen, können Sie den Proxyserver verwenden, um herauszufinden, wo die Anforderung verloren ging. In Fällen mit Firewall:

1. Starten Sie einen Proxy vor der Firewall.
1. Starten Sie einen weiteren Proxy hinter der Firewall.
1. Verwenden Sie die Proxys, um herauszufinden, wie weit die Anforderungen kommen.

**Hängende Anforderungen**

Gehen Sie wie folgt vor, wenn gelegentlich hängende Anforderungen auftreten:

1. Starten Sie proxy.jar.
1. Warten Sie oder schreiben Sie das Zugriffsprotokoll in eine Datei, in der jeder Eintrag einen Zeitstempel aufweist.
1. Wenn hängende Anforderungen auftreten, können Sie sehen, wie viele Verbindungen offen waren und welche Anforderung dafür verantwortlich ist.

## Das Format von Protokollmeldungen  {#the-format-of-log-messages}

Die von proxy.jar erstellten Protokolleinträge haben das folgende Format:

```xml
[timestamp (optional)] [<b>C</b>lient|<b>S</b>erver]-[ConnectionNumber]-[BytePosition] ->[Character Stream]
```

So kann eine Webseitenanforderung zum Beispiel wie folgt aussehen:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]
```

* „C“ gibt an, dass dieser Eintrag vom Client stammt (es handelt sich dabei um die Anforderung einer Webseite).
* „0“ ist die Verbindungsnummer (der Verbindungszähler startet bei 0).
* # 00000 ist der Versatz im Bytestream. Hierbei handelt es sich um den ersten Eintrag, weshalb der Versatz bei 0 ist.
* [GET  &lt;?>] ist der Inhalt der Anfrage, im Beispiel einer der HTTP-Header (URL).

Wenn eine Verbindung geschlossen wird, werden die folgenden Informationen protokolliert:

```xml
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Hier werden die Anzahl der Bytes, die zwischen dem Client und dem Server bei der 6. Verbindung übertragen wurden, und die durchschnittliche Geschwindigkeit angegeben.

## Beispiel für eine Protokollausgabe  {#an-example-of-log-output}

Lassen Sie uns eine einfache Vorlage durchgehen, die bei Anforderung folgenden Code erzeugt:

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

Wenn AEM auf dem „localhost:4303“ ausgeführt wird, starten Sie den Server wie folgt:

```xml
java -jar proxy.jar localhost 4303 4444 -logfile test.log
```

Sie können ohne den Proxyserver auf den Server zugreifen (`localhost:4303`), wenn Sie jedoch über `localhost:4444` auf ihn zugreifen, protokolliert der Proxyserver die Kommunikation. Öffnen Sie einen Browser und rufen Sie eine Seite auf, die mit der vorherigen Vorlage erstellt wurde. Betrachten Sie anschließend die Protokolldatei.

>[!NOTE]
>
>Bis zur proxy.jar-Version 1.14 werden die Protokolleinträge einer Verbindung nicht synchronisiert, was bedeutet, dass die Protokolleinträge einer Client-/Server-Verbindung nicht zwangsläufig in der sequenziellen Reihenfolge angegeben sind. Bei neueren Versionen (ab 1.14) des Proxyservers tritt dieses Problem nicht auf.

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

Der Proxyserver ist ein geeignetes Tool, um zu überprüfen, ob Cookies richtig eingestellt sind oder nicht. Nachfolgend können wir Folgendes sehen:

* Den von AEM generierten cq3sessions-Cookie
* Den von CFC generierten ShowMode-Switch-Cookie
* Ein Cookie mit dem Namen JSESSIONID; dieser wird automatisch von JSP erstellt, wenn Sie die Verwendung dieses Cookies nicht ausdrücklich über &lt;%@ page session=&quot;false&quot; %> deaktiviert haben:

```xml
C-0-#000393 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-0-#000514 -> [ ]
S-0-#000000 -> [HTTP/1.0 200 OK ]
```

Der Server schließt die Verbindung 0 nach der Anforderung. Eine Keep-Alive-Verbindung ist nicht möglich, da die Anforderung ein Fragezeichen enthält. Dies bedeutet, dass der Server keine Cache-gespeicherte Version zurückgeben und deshalb an diesem Punkt auch nicht die Länge des Inhalts bestimmen kann. Dies ist jedoch für eine Keep-Alive-Verbindung erforderlich.

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

Nun da die Länge des Inhalts festgelegt ist, sendet der Server die Bilddaten über die Verbindung 1:

```xml
S-1-#000167 -> [GIF87a..........................,.......
...I....0.A..8......YDA.W...1..`i.`..6...Z...$@.F..)`..f..A.....iu.........$..;]
```

Nach Erreichen des Keep-Alive-Timeouts wird die Verbindung 1 ebenfalls geschlossen:

```xml
S-1-Finished: 291 bytes (0.0 kb/s)
C-1-Finished: 403 bytes (0.0 kb/s)
```

Das obige Beispiel ist verhältnismäßig einfach, da die beiden Verbindungen nacheinander aufgebaut werden:

* Zuerst gibt der Server den HTML-Code zurück;
* dann fordert der Browser das Bild an und öffnet eine neue Verbindung.

In der Praxis generiert eine Seite möglicherweise viele parallele Anforderungen für Bilder, Stylesheets, JavaScript-Dateien usw. Dies bedeutet, dass die Protokolle sich überlappende Einträge von parallel geöffneten Verbindungen haben. In diesem Fall empfehlen wir der Lesbarkeit halber, die Option „-i“ zu verwenden.
