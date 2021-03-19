---
title: Ablauf statischer Objekte
seo-title: Ablauf statischer Objekte
description: Erfahren Sie, wie Sie AEM konfigurieren können, damit statische Objekte (über einen angemessenen Zeitraum) nicht ablaufen.
seo-description: Erfahren Sie, wie Sie AEM konfigurieren können, damit statische Objekte (über einen angemessenen Zeitraum) nicht ablaufen.
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: Konfiguration
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 95%

---


# Ablauf statischer Objekte{#expiration-of-static-objects}

Statische Objekte (wie Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass diese Objekte (über einen angemessenen Zeitraum) nicht ablaufen, damit unnötiger Traffic reduziert wird. 

Dies wirkt sich wie folgt aus:

* Anforderungen werden von der Serverinfrastruktur abgeladen.
* Die Leistung beim Laden von Seiten wird erhöht, da der Browser Objekte im Browsercache zwischenspeichert.

Abläufe sind im HTTP-Standard in Bezug auf den „Ablauf“ von Dateien spezifiziert (siehe etwa Kapitel 14.21 des Dokuments [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt), „Hypertext Transfer Protocol – HTTP 1.1“). Dieser Standard greift auf den Header zurück, um Clients das Speichern von Objekten im Cache zu erlauben, bis die Objekte als alt eingestuft werden; diese Objekte werden für den angegebenen Zeitraum im Cache gespeichert, ohne dass der Ursprungsserver einer Statusprüfung unterzogen wird.

>[!NOTE]
>
>Diese Konfiguration ist vollständig losgelöst vom Dispatcher (und kann nicht für diesen verwendet werden).
>
>Der Dispatcher dient dem Caching der Daten vor AEM.

Alle Dateien, die nicht dynamisch sind und im Laufe der Zeit nicht geändert werden, können und sollten im Cache gespeichert werden. Die Konfiguration für den Apache-HTTPD-Server kann je nach Umgebung wie eine der folgenden Möglichkeiten aussehen:

>[!CAUTION]
>
>Sie müssen vorsichtig sein, wenn Sie den Zeitraum definieren, in dem ein Objekt als aktuell gilt. Da *keine Prüfung bis zum Ablauf des angegebenen Zeitraums erfolgt*, ist es möglich, dass der Client alten Inhalt aus dem Cache präsentiert.

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

   Hierdurch wird ermöglicht, dass der temporäre Cache (etwa der Browsercache) CSS-, JavaScript-, PNG- und GIF-Dateien maximal einen Monat lang, bis zu ihrem Ablauf, speichert. Sie müssen also nicht von AEM oder vom Webserver angefordert werden, sondern können im Browsercache verbleiben.

   Andere Abschnitte der Website sollten nicht in einer Autoreninstanz im Cache gespeichert werden, da sich diese jederzeit ändern können.

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

   Hierdurch wird ermöglicht, dass der temporäre Cache (etwa der Browsercache) CSS-, JavaScript-, PNG- und GIF-Dateien einen Tag lang in Clientcaches speichert. Obwohl dieses Beispiel die globalen Einstellungen für alles unterhalb von `/content` und `/etc/designs` veranschaulicht, sollten Sie sie granularer gestalten.

   Abhängig vom Aktualisierungsintervall der Website käme für Sie ggf. auch das Caching von HTML-Seiten in Frage. Ein angemessener Zeitraum wäre etwa 1 Stunde:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Gehen Sie nach der Konfiguration der statischen Objekte die Datei `request.log` durch, während Sie Seiten mit solchen Objekten auswählen, um zu bestätigen, dass keine (unnötigen) Anforderungen für statische Objekte erfolgen.
