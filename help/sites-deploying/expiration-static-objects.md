---
title: Ablauf statischer Objekte
description: Erfahren Sie, wie Sie Adobe Experience Manager so konfigurieren, dass statische Objekte (für einen angemessenen Zeitraum) nicht ablaufen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: bfd5441c-19cc-4fa8-b597-b1221465f75d
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 30%

---

# Ablauf statischer Objekte{#expiration-of-static-objects}

Statische Objekte (z. B. Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass diese Objekte (über einen angemessenen Zeitraum) nicht ablaufen, damit unnötiger Traffic reduziert wird.

Dies hat folgende Auswirkungen:

* Lädt Anforderungen aus der Serverinfrastruktur ab.
* Erhöht die Leistung beim Laden von Seiten, da der Browser Objekte im Browser-Cache zwischenspeichert.

Die Ablaufdaten werden durch den HTTP-Standard in Bezug auf den &quot;Ablauf&quot;von Dateien angegeben (siehe beispielsweise Kapitel 14.21 von [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot; Hypertext Transfer Protocol - HTTP 1.1&quot;). Dieser Standard greift auf den Header zurück, um Clients das Speichern von Objekten im Cache zu erlauben, bis die Objekte als alt eingestuft werden; diese Objekte werden für den angegebenen Zeitraum im Cache gespeichert, ohne dass der Ursprungsserver einer Statusprüfung unterzogen wird.

>[!NOTE]
>
>Diese Konfiguration unterscheidet sich vom Dispatcher (und funktioniert nicht für diesen).
>
>Der Dispatcher dient dazu, Daten vor Adobe Experience Manager (AEM) zwischenzuspeichern.

Alle Dateien, die nicht dynamisch sind und sich im Laufe der Zeit nicht ändern, können und sollten zwischengespeichert werden. Die Konfiguration für den Apache HTTPD-Server könnte abhängig von der Umgebung wie eine der folgenden aussehen:

>[!CAUTION]
>
>Seien Sie vorsichtig, wenn Sie den Zeitraum definieren, in dem ein Objekt als aktuell betrachtet wird. Da gibt es *keine Überprüfung bis zum Ablauf des angegebenen Zeitraums*, kann der Client schließlich alte Inhalte aus dem Cache präsentieren.

1. **Für eine Autoreninstanz:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Dadurch kann der Zwischenspeicher (z. B. der Browsercache) CSS-, JavaScript-, PNG- und GIF-Dateien bis zu einem Monat speichern, bis sie ablaufen. Dies bedeutet, dass sie nicht von AEM oder dem Webserver angefordert werden müssen, sondern im Browsercache verbleiben können.

   Andere Bereiche der Site sollten nicht in einer Autoreninstanz zwischengespeichert werden, da sie jederzeit geändert werden können.

1. **Für eine Veröffentlichungsinstanz:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   Dadurch kann der Zwischenspeicher (z. B. der Browsercache) CSS-, JavaScript-, PNG- und GIF-Dateien für bis zu einen Tag in Client-Caches speichern. Obwohl dieses Beispiel globale Einstellungen für alle Elemente unter `/content` und `/etc/designs` veranschaulicht, sollten Sie hier genauer vorgehen.

   Je nachdem, wie oft Ihre Site aktualisiert wird, können Sie auch das Zwischenspeichern von HTML-Seiten in Erwägung ziehen. Ein angemessener Zeitraum wäre eine Stunde:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Gehen Sie nach der Konfiguration der statischen Objekte die Datei `request.log` durch, während Sie Seiten mit solchen Objekten auswählen, um zu bestätigen, dass keine (unnötigen) Anforderungen für statische Objekte erfolgen.
