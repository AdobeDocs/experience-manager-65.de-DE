---
title: Verwendung des Proxyservertools
seo-title: Verwendung des Proxyservertools
description: Ein Proxyserver fungiert als zwischengeschalteter Server, der Anfragen zwischen einem Client und einem Server weiterreicht.
seo-description: Ein Proxyserver fungiert als zwischengeschalteter Server, der Anfragen zwischen einem Client und einem Server weiterreicht.
uuid: 30f4f46d-839e-4d23-a511-12f29b3cc8aa
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: dfbc1d2f-80c1-4564-a01c-a5028b7257d7
exl-id: 7222a0c3-cdb9-4c73-9d53-26f00792e439
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 91%

---

# Verwendung des Proxyservertools{#how-to-use-the-proxy-server-tool}

Ein Proxyserver fungiert als zwischengeschalteter Server, der Anfragen zwischen einem Client und einem Server weiterreicht. Der Proxyserver speichert alle Interaktionen zwischen Client und Server und erstellt ein Protokoll der gesamten TCP-Kommunikation. So können Sie sämtliche Aktivitäten genau überwachen und müssen nicht auf den Hauptserver zugreifen.

Den Proxyserver in Ihrer AEM-Installation finden Sie hier:

`crx-quickstart/opt/helpers/proxy-2.1.jar`

Sie können den Proxyserver verwenden, um alle Interaktionen zwischen Client und Server zu überwachen, unabhängig vom zugrunde liegenden Kommunikationsprotokoll. So können Sie beispielsweise die folgenden Protokolle überwachen:

* HTTP für Webseiten
* HTTPS für sichere Webseiten
* SMTP für E-Mail-Nachrichten
* LDAP für die Benutzerverwaltung

Sie können den Proxyserver zum Beispiel zwischen zwei Anwendungen schalten, die über ein TCP/IP-Netzwerk kommunizieren, etwa einem Webbrowser und AEM. So können Sie genau überprüfen, was passiert, wenn Sie eine CQ-Seite anfordern.

## Starten des Proxyservertools {#starting-the-proxy-server-tool}

Starten Sie den Server über eine Befehlszeile:

`java -jar proxy-2.1.jar <host> <remoteport> <localport> [options]`

**Parameter**

`<host>`

Hierbei handelt es sich um die Hostadresse der CRX-Instanz, zu der Sie eine Verbindung aufbauen möchten. Wenn sich die Instanz auf Ihrem lokalen Computer befindet, lautet sie `localhost`.

`<remoteport>`

Hierbei handelt es sich um den Port der CRX-Zielinstanz. Der Standardport für eine neue AEM-Installation lautet zum Beispiel **`4502`** und der Standardport für eine neue AEM-Erstellungsinstanz `4502`.

`<localport>`

Dies ist der Port auf Ihrem lokalen Computer, zu dem Sie eine Verbindung aufbauen, um über den Proxy auf die CRX-Instanz zuzugreifen.

**Optionen**

`-q` (leiser Modus)

Die Ausgabe wird nicht in das Konsolenfenster geschrieben. Verwenden Sie die Option, wenn Sie die Verbindung entlasten möchten oder wenn Sie die Ausgabe in einer Datei protokollieren (siehe Option „-logfile“).

`-b`(binärer Modus)

Aktivieren Sie den binären Modus, wenn Sie nach bestimmten Bytekombinationen im Datenverkehr suchen. Die Ausgabe enthält anschließend die Hexadezimal- und Zeichenausgabe.

`-t` (Zeitstempelprotokolleinträge)

Fügt jedem Eintrag im Protokoll einen Zeitstempel hinzu. Der Zeitstempel wird in Sekunden angegeben, weshalb er möglicherweise nicht zur Prüfung einzelner Anfragen geeignet ist. Verwenden Sie die Option, um Ereignisse ausfindig zu machen, die zu einem bestimmten Zeitpunkt erfolgt sind, wenn Sie den Proxyserver über einen längeren Zeitraum nutzen.

`-logfile <filename>`(Schreiben in Protokolldatei)

Schreibt die Interaktionen zwischen Client und Server in eine Protokolldatei. Dieser Parameter kann auch im stillen Modus genutzt werden.

**`-i <numIndentions>`**(Einzug hinzufügen)

Die einzelnen Verbindungen werden für eine bessere Lesbarkeit eingezogen. Der Standardwert beträgt 16 Ebenen. Diese Funktion wurde mit `proxy.jar version 1.16` eingeführt.

### Protokollformat {#log-format}

Die von proxy-2.1.jar erstellten Protokolleinträge haben das folgende Format:

`[timestamp (optional)] [Client|Server]-[ConnectionNumber]-[BytePosition] ->[Character Stream]`

So kann eine Webseitenanforderung zum Beispiel wie folgt aussehen:

`C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]`

* „C“ gibt an, dass dieser Eintrag vom Client stammt (es handelt sich dabei um die Anforderung einer Webseite).
* „0“ ist die Verbindungsnummer (der Verbindungszähler startet bei 0).
* # 00000 ist der Versatz im Bytestream. Hierbei handelt es sich um den ersten Eintrag, weshalb der Versatz bei 0 ist.
* `[GET <?>]` ist der Inhalt der Anfrage, im Beispiel einer der HTTP-Header (URL).

Wenn eine Verbindung geschlossen wird, werden die folgenden Informationen protokolliert:

```
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Hier werden die Anzahl der Bytes, die zwischen dem Client (`C`) und dem Server (`S`) bei der 6. Verbindung übertragen wurden, und die durchschnittliche Geschwindigkeit angegeben.

**Beispiel für eine Protokollausgabe**

Stellen Sie sich als Beispiel eine Seite vor, die bei einer Anforderung den folgenden Code ausgibt:

### Beispiel {#example}

Stellen Sie sich als Beispiel ein sehr einfaches HTML-Dokument vor, das sich im Repository unter

`/content/test.html`

befindet, zusammen mit einer Bilddatei unter

`/content/test.jpg`

Der Inhalt von `test.html` lautet:

```xml
<html>
<head>
    <title>Test</title>
</head>
<body>
    Test<br>
    <img src="test.jpg">
</body>
</html>
```

Wenn die AEM-Instanz auf `localhost:4502` ausgeführt wird, starten wir den Proxy wie folgt:

`java -jar proxy.jar localhost 4502 4444 -logfile test.log`

Die CQ-/CRX-Instanz kann jetzt über den Proxy unter `localhost:4444` aufgerufen werden und die gesamte Kommunikation über diesen Port wird unter `test.log` protokolliert.

Wenn Sie sich nun die Ausgabe des Proxys ansehen, können Sie die Interaktion zwischen dem Browser und der AEM-Instanz beobachten.

Beim Start erfolgt die folgende Ausgabe über den Proxy:

```xml
starting proxy for localhost:4502 on port 4444
using logfile: <some-dir>/crx-quickstart/opt/helpers/test.log
```

Wenn Sie anschließend einen Browser öffnen und auf die Testseite unter

`http://localhost:4444/content/test.html`

und wir sehen, dass der Browser eine `GET` -Anfrage für die Seite stellt:

```shell
C-0-#000000 -> [GET /content/test.html HTTP/1.1 ]
C-0-#000033 -> [Host: localhost:4444 ]
C-0-#000055 -> [Connection: keep-alive ]
C-0-#000079 -> [User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_4) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11 ]
C-0-#000212 -> [Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 ]
C-0-#000285 -> [Accept-Encoding: gzip,deflate,sdch ]
C-0-#000321 -> [Accept-Language: en-US,en;q=0.8 ]
C-0-#000354 -> [Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3 ]
C-0-#000402 -> [Cookie: login-token=179ba6bd-e0a7-4909-a965-e11c7f2bc2fc%3a618bd8a8-fbaf-43c5-827d-c84c62248c5e_22ee860cc9036fee%3acrx.default%3b21148fb0-eb6c]
C-0-#000543 -> [-43c9-a2b9-c8d40618d8ae%3ad87a3d1a-5e9a-4d5a-bab1-0ee60ad6d8df_d0e4ddce0fcd84b6%3acrx.default%3b5cb95227-ea51-47bf-850b-68ad1dfd7297%3af3bbb6]
C-0-#000684 -> [59-7913-4285-8857-832c087bafd5_c484727d3b3665ad%3acrx.default; ys-cq-siteadmin-tree=o%3Awidth%3Dn%253A240%5EselectedPath%3Ds%253A/content ]
C-0-#000824 -> [ ]
```

Die AEM-Instanz antwortet mit den Inhalten der Datei `test.html`:

```shell
S-0-#000000 -> [HTTP/1.1 200 OK ]
S-0-#000017 -> [Connection: Keep-Alive ]
S-0-#000041 -> [Server: Day-Servlet-Engine/4.1.24  ]
S-0-#000077 -> [Content-Type: text/html;charset=utf-8 ]
S-0-#000116 -> [Content-Length: 104 ]
S-0-#000137 -> [Date: Mon, 16 Jul 2012 11:23:38 GMT ]
S-0-#000174 -> [Last-Modified: Mon, 16 Jul 2012 11:19:27 GMT ]
S-0-#000220 -> [ ]
S-0-#000222 -> [<html>]
S-0-#000229 -> [<head>]
S-0-#000236 -> [    <title>Test</title>]
S-0-#000260 -> [</head> ]
S-0-#000269 -> [<body>]
S-0-#000276 -> [ Test<br>]
S-0-#000286 -> [    <img src="test.jpg">]
S-0-#000311 -> [</body>]
S-0-#000319 -> [</html>]
```

### Anwendungsfälle für das Proxyservertool {#uses-of-the-proxy-server}

In den folgenden Szenarien werden einige Einsatzzwecke für die Proxyserver demonstriert:

**Überprüfen von Cookies und ihren Werten**

Der folgende beispielhafte Protokolleintrag enthält alle Cookies, die vom Client bei der sechsten Verbindung seit Proxystart gesendet wurden, und ihre Werte:

`C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]`

**Überprüfen von Kopfzeilen und ihren Werten**

Der folgende beispielhafte Protokolleintrag zeigt, dass der Server eine „Keep-Alive“-Verbindung herstellen kann und die „Content-Length“-Kopfzeile richtig festgelegt wurde:

```
S-7-#000017 -> [Connection: Keep-Alive ]
 ...
 S-7-#000107 -> [Content-Length: 124 ]
```

**Überprüfen der Funktionsfähigkeit von Keep-Alive**

Keep-Alive ist eine Funktion von HTTP, die es einem Client ermöglicht, eine TCP-Verbindung zum Server wiederzuverwenden, um mehrere Anforderungen zu tätigen (für Seitencode, Bilder, Stylesheets usw.). Ohne Keep-Alive muss der Client für jede Anforderung eine neue Verbindung aufbauen.

So überprüfen Sie, ob Keep-Alive funktioniert:

* Starten Sie den Proxyserver.
* Fordern Sie eine Seite an.
* Falls Keep-Alive funktioniert, sollte der Verbindungszähler immer nur auf einen Wert zwischen 5–10 Verbindungen ansteigen.
* Sollte Keep-Alive nicht funktionieren, erhöht sich dieser Wert sehr schnell.

**Finden verlorener Anforderungen**

Sollten Anforderungen in einer komplexen Serverumgebung, zum Beispiel einer mit Firewall und Dispatcher, verloren gehen, können Sie den Proxyserver verwenden, um herauszufinden, wo die Anforderung verloren ging. In Fällen mit Firewall:

* Starten Sie einen Proxy vor der Firewall.
* Starten Sie einen weiteren Proxy hinter der Firewall.
* Verwenden Sie die Proxys, um herauszufinden, wie weit die Anforderungen kommen.

**Hängende Anforderungen**

Gehen Sie wie folgt vor, wenn gelegentlich hängende Anforderungen auftreten:

* Starten Sie den Proxy.
* Warten Sie oder schreiben Sie das Zugriffsprotokoll in eine Datei, in der jeder Eintrag einen Zeitstempel aufweist.
* Wenn hängende Anforderungen auftreten, können Sie sehen, wie viele Verbindungen offen waren und welche Anforderung dafür verantwortlich ist.
