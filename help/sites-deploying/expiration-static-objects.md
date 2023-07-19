---
title: Ablauf statischer Objekte
seo-title: Expiration of Static Objects
description: Erfahren Sie, wie Sie AEM so konfigurieren, dass statische Objekte (für einen angemessenen Zeitraum) nicht ablaufen.
seo-description: Learn how to configure AEM so that static objects do not expire (for a reasonable period of time).
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: Configuring
exl-id: bfd5441c-19cc-4fa8-b597-b1221465f75d
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 35%

---

# Ablauf statischer Objekte{#expiration-of-static-objects}

Statische Objekte (z. B. Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass sie (für einen angemessenen Zeitraum) nicht ablaufen und so unnötigen Traffic reduzieren.

Dies hat folgende Auswirkungen:

* Lädt Anforderungen aus der Serverinfrastruktur ab.
* Erhöht die Leistung beim Laden von Seiten, da der Browser Objekte im Browser-Cache zwischenspeichert.

Abläufe sind im HTTP-Standard in Bezug auf den „Ablauf“ von Dateien spezifiziert (siehe etwa Kapitel 14.21 des Dokuments [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt), „Hypertext Transfer Protocol – HTTP 1.1“). Dieser Standard greift auf den Header zurück, um Clients das Speichern von Objekten im Cache zu erlauben, bis die Objekte als alt eingestuft werden; diese Objekte werden für den angegebenen Zeitraum im Cache gespeichert, ohne dass der Ursprungsserver einer Statusprüfung unterzogen wird.

>[!NOTE]
>
>Diese Konfiguration ist vollständig losgelöst vom Dispatcher (und kann nicht für diesen verwendet werden).
>
>Der Dispatcher dient dem Caching der Daten vor AEM.

Alle Dateien, die nicht dynamisch sind und sich im Laufe der Zeit nicht ändern, können und sollten zwischengespeichert werden. Die Konfiguration für den Apache HTTPD-Server könnte abhängig von der Umgebung wie eine der folgenden aussehen:

>[!CAUTION]
>
>Achten Sie bei der Definition des Zeitraums, in dem ein Objekt als aktuell gilt. Da gibt es *keine Überprüfung bis zum Ablauf des angegebenen Zeitraums*, kann der Client schließlich alte Inhalte aus dem Cache präsentieren.

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

   Je nachdem, wie oft Ihre Site aktualisiert wird, können Sie auch das Zwischenspeichern von HTML-Seiten in Erwägung ziehen. Ein angemessener Zeitraum wäre 1 Stunde:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Gehen Sie nach der Konfiguration der statischen Objekte die Datei `request.log` durch, während Sie Seiten mit solchen Objekten auswählen, um zu bestätigen, dass keine (unnötigen) Anforderungen für statische Objekte erfolgen.
