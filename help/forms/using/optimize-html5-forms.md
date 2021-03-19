---
title: Optimieren von HTML5-Formularen
seo-title: Optimieren von HTML5-Formularen
description: Sie können die Ausgabegröße von HTML5-Formularen optimieren.
seo-description: Sie können die Ausgabegröße von HTML5-Formularen optimieren.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 89%

---


# Optimieren von HTML5-Formularen {#optimizing-html-forms}

HTML5 forms gibt Formulare im HTML5-Format aus. Die Ausgabe hängt möglicherweise stark von Faktoren wie der Formulargröße und den Bildern im Formular ab. Die empfohlene Vorgehensweise zum Optimieren der Datenübertragung ist eine Komprimierung der HTML-Antwort auf dem Webserver, von dem die Anforderung stammt. Auf diese Weise können die Antwortgröße, der Netzwerkverkehr und die für das Streaming der Daten zwischen dem Server und den Clientgeräten erforderliche Zeit erheblich verringert werden.

In diesem Artikel werden die Schritte beschrieben, die erforderlich sind, um die Komprimierung für den 32-Bit-Apache-Webserver 2.0 mit JBoss zu aktivieren.

>[!NOTE]
>
>Die folgenden Anweisungen gelten nicht für andere Server als Apache Web Server 2.0 32 Bit.

Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem:

* (Windows) Laden Sie den Apache-Webserver von der Apache HTTP Server Project-Site herunter.
* (Solaris 64-Bit) Laden Sie den Apache-Webserver von der Sunfreeware for Solaris-Website herunter.
* (Linux) Auf Linux-Systemen ist der Apache-Webserver vorinstalliert.

Apache kann mit JBoss mithilfe des HTTP- oder AJP-Protokolls kommunizieren.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei *APACHE_HOME/conf/httpd.conf*.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Unter Linux ist das Standardverzeichnis für APACHE_HOME /etc/httpd/.

1. Konfigurieren des Proxys auf Port 8080 von JBoss.

   Fügen Sie in die Datei *APACHE_HOME/conf/httpd.conf* folgende Konfiguration ein.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Wenn Sie einen Proxy verwenden, sind die folgenden Konfigurationsänderungen erforderlich:
   >
   >* Zugriff: *https://&lt;server>:&lt;port>/system/console/configMgr*
   * Bearbeiten Sie die Konfiguration für Apache Sling Referrer Filter
   * Fügen Sie unter „Hosts zulassen“ den Eintrag für den Proxyserver hinzuf.


1. Aktivieren Sie die Komprimierung.

   Fügen Sie in die Datei *APACHE_HOME/conf/httpd.conf* folgende Konfiguration ein.

   ```xml
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Um auf den AEM-Server zuzugreifen, verwenden Sie https://[Apache_server]:80.
