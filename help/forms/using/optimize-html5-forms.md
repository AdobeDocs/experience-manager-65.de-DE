---
title: Optimieren von HTML5-Formularen
description: Sie können die Ausgabegröße der HTML5-Formulare optimieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
feature: Mobile Forms
exl-id: 14309ebd-8d00-4ca5-b4ab-44d80d97d066
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 29%

---

# Optimieren von HTML5-Formularen {#optimizing-html-forms}

HTML5 forms rendert Formulare im HTML5-Format. Die resultierende Ausgabe kann abhängig von Faktoren wie der Formulargröße und den Bildern im Formular groß sein. Um die Datenübertragung zu optimieren, wird empfohlen, die HTML-Antwort mit dem Webserver zu komprimieren, von dem aus die Anforderung bereitgestellt wird. Dieser Ansatz reduziert die Antwortgröße, den Netzwerk-Traffic und die zum Streamen von Daten zwischen dem Server und den Clientgeräten erforderliche Zeit.

In diesem Artikel werden die Schritte beschrieben, die zum Aktivieren der Komprimierung für den 32-Bit-Apache-Webserver 2.0 mit JBoss erforderlich sind.

>[!NOTE]
>
>Die folgenden Anweisungen gelten für keine anderen Server als Apache Web Server 2.0 32 Bit.

Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem:

* Für Windows laden Sie den Apache-Webserver von der Apache HTTP Server Project-Site herunter.
* Für Solaris 64 Bit laden Sie den Apache-Webserver von der Sunfreeware for Solaris-Website herunter.
* Für Linux ist der Apache-Webserver auf einem Linux-System vorinstalliert.

Apache kann mit JBoss über HTTP oder das AJP-Protokoll kommunizieren.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei *APACHE_HOME/conf/httpd.conf*.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Für Linux ist der Standardordner APACHE_HOME /etc/httpd/.

1. Konfigurieren Sie den Proxy auf Port 8080 von JBoss.

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
   * Bearbeiten Sie die Konfiguration für den Apache Sling Referrer Filter .
   * Fügen Sie unter &quot;Hosts zulassen&quot;den Eintrag für den Proxyserver hinzu.

1. Aktivieren Sie die Komprimierung.

   Fügen Sie in die Konfigurationsdatei *APACHE_HOME/conf/httpd.conf* folgende Konfiguration ein.

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
