---
title: Leistungsoptimierung für AEM Forms-Server
seo-title: Leistungsoptimierung für AEM Forms-Server
description: Damit AEM Forms optimal funktioniert, können Sie die Cacheeinstellungen und JVM-Parameter anpassen. Durch die Verwendung eines Webservers kann auch die Leistung der AEM Forms-Bereitstellung verbessert werden.
seo-description: Damit AEM Forms optimal funktioniert, können Sie die Cacheeinstellungen und JVM-Parameter anpassen. Durch die Verwendung eines Webservers kann auch die Leistung der AEM Forms-Bereitstellung verbessert werden.
uuid: bf23b62c-7559-4726-8f4e-cc8b1457e501
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 38c0ec46-5686-4656-bfb4-7125ec194673
docset: aem65
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Leistungsoptimierung für AEM Forms-Server{#performance-tuning-of-aem-forms-server}

In diesem Artikel werden Strategien und empfohlene Vorgehensweisen besprochen, die Sie implementieren können, um Engpässe zu reduzieren und die Leistung Ihrer AEM Forms-Bereitzustellung zu optimieren.

## Cacheeinstellungen {#cache-settings}

Sie können die Cachestrategie für AEM Forms mithilfe der Komponente **Mobile Forms Configurations** in AEM Web Configuration Console konfigurieren und steuern:

* (AEM Forms on OSGi) `https://'[server]:[port]'/system/console/configMgr`
* (AEM Forms unter JEE) `https://'[server]:[port]'/lc/system/console/configMgr`

Für die Zwischenspeicherung sind folgende Optionen verfügbar:

* **Keine**: Verhindert die Zwischenspeicherung von Artefakten. Auf diese Weise wird tatsächlich die Leistung beeinträchtigt und aufgrund des nicht vorhandenen Zwischenspeichers höhere Speicherverfügbarkeit erforderlich.
* **Konservativ**: Schreibt vor, dass nur jene Zwischenartefakte zwischengespeichert werden, die vor Wiedergabe des Formulars generiert werden wie Vorlagen mit Inline-Fragmenten und Bildern.
* **Aggressiv**: Setzt durch, dass fast alles zwischengespeichert wird, das zwischengespeichert werden kann, einschließlich des gerenderten HTML-Inhalts neben alle Artefakten aus der Cacheebene „Konservativ“. Dies ergibt die beste Leistung, verbraucht aber jedoch mehr Platz für die Speicherung der zwischengespeicherten Artefakte. Unter aggressiver Cachestrategie bedeutet, dass Sie beim Rendern eines Formulars konstante Zeitleistung erhalten, da der gerenderte Inhalt zwischengespeichert ist.

Die standardmäßigen Cacheeinstellungen für AEM Forms erweisen sich für eine optimale Leistung möglicherweise als unzureichend. Daher wird die Verwendung der folgenden Einstellungen empfohlen:

* **Cachestrategie**: Aggressiv
* **Cachegröße** (in Bezug auf Anzahl von Formularen): Bei Bedarf
* **Max Objektgröße**: Bei Bedarf

![Mobile Forms-Konfigurationen](assets/snap.png)

>[!NOTE]
>
>Wenn Sie AEM Dispatcher zum Zwischenspeichern adaptiver Formulare verwenden, werden dabei auch adaptive Formulare im Cache abgelegt, die Formulare mit vorausgefüllten Daten enthalten. Werden solche Formulare aus dem AEM Dispatcher-Cache bereitgestellt, erhalten die Benutzer eventuell vorausgefüllte oder veraltete Daten. Verwenden Sie AEM Dispatcher daher zum Zwischenspeichern von Formularen, die keine vorausgefüllten Daten enthalten. Darüber hinaus werden im Dispatcher-Cache abgelegte Fragmente nicht automatisch ungültig gemacht. Verwenden Sie dies daher nicht zum Zwischenspeichern von Formularfragmenten. Verwenden Sie für solche Formulare und Fragmente vielmehr den [Adaptive Forms-Cache](../../forms/using/configure-adaptive-forms-cache.md).

## JVM-Parameter   {#jvm-parameters}

For optimal performance, it is recomended to use the following JVM `init` arguments to configure the `Java heap` and `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Die empfohlenen Einstellungen gelten für Windows 2008 R2 8 Core und Oracle HotSpot 1.7 (64-Bit) JDK und sollten gemäß Ihrer Systemkonfiguration hoch- oder herunterskaliert werden.

## Verwenden eines Webservers {#using-a-web-server}

Adaptive Formulare und HTML5-Formulare werden im HTML5-Format wiedergeben. Die Ausgabe hängt möglicherweise stark von Faktoren wie der Formulargröße und den Bildern im Formular ab. Die empfohlene Vorgehensweise zum Optimieren der Datenübertragung ist eine Komprimierung der HTML-Antwort auf dem Webserver, von dem die Anforderung stammt. Auf diese Weise können die Antwortgröße, der Netzwerkverkehr und die für das Streaming der Daten zwischen dem Server und den Clientgeräten erforderliche Zeit erheblich verringert werden.

Führen Sie beispielsweise die folgenden Schritte durch, um die Komprimierung auf Apache Web Server 2.0 32-Bit mit Jboss zu ermöglichen:

>[!NOTE]
>
>Die folgenden Anweisungen gelten nicht für andere Server als den 32-Bit-Apache Web Server 2.0. Informationen über spezielle Schritte für andere Server finden Sie in der entsprechenden Produktdokumentation.

Die folgenden Schritte demonstrieren die Änderungen, die erforderlich sind, um die Komprimierung mit Apache Web Server zu aktivieren

**Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem**

* Windows: Laden Sie den Apache-Webserver von der Apache TTP Server Project-Site herunter.
* Solaris 64-Bit: Laden Sie den Apache-Webserver von der Sunfreeware Solaris-Website herunter.
* Linux: Auf Linux-Systemen ist der Apache-Webserver vorinstalliert.

Apache können über das HTTP-Protokoll mit CRX kommunizieren. Die Konfigurationen zur optimierten Nutzung von HTTP.

1. Uncomment the following module configurations in `APACHE_HOME/conf/httpd.conf` file.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >For Linux, the default `APACHE_HOME` is `/etc/httpd/`.

1. Konfigurieren Sie das Proxys auf Port 4502 von crx.
Add following configuration in `APACHE_HOME/conf/httpd.conf` configuration file.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Aktivieren Sie die Komprimierung. Add following configuration in `APACHE_HOME/conf/httpd.conf` configuration file.

   **Für HTML5-Formulare**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Bei adaptiven Formularen**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Verwenden Sie für den Zugriff auf den CRX-Server `https://'server':80`, wobei `server` für den Namen des Servers steht, auf dem der Apache-Server ausgeführt wird.

## Verwendung eines Antivirenprogramms auf dem Server, auf dem AEM Forms ausgeführt wird {#using-an-antivirus-on-server-running-aem-forms}

Auf den Servern, auf denen eine Antivirensoftware ausgeführt wird, kann es zu Leistungsbeeinträchtigungen kommen. Antivirensoftware, die immer aktiv ist (On-Access-Scan) scannt sämtliche Dateien auf dem System. Der Server kann dadurch langsamer laufen und die Leistung von AEM Forms wird beeinträchtigt.

Um die Leistung zu verbessern, können Sie die Antivirensoftware anweisen, die folgenden AEM Forms-Dateien und -Ordner vom ständigen On-Access-Scan auszuschließen:

* AEM-Installationsverzeichnis. Wenn es nicht möglich ist, das gesamte Verzeichnis auszuschließen, schließen Sie die folgenden Ordner aus:

   * [AEM-Installationsordner]\crx-repository\temp
   * [AEM-Installationsordner]\crx-repository\repository
   * [AEM-Installationsordner]\crx-repository\launchpad

* Temporärer Ordner des Anwendungsservers. Der Standardspeicherort lautet:

   * (Jboss) [AEM installation directory]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Programme\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Nur AEM Forms unter JEE),** Ordner des globalen Dokumentenspeichers (GDS). Der Standardspeicherort lautet:

   * (JBoss) [appserver root]/server/&#39;server&#39;/svcnative/DocumentStorage
   * (WebLogic) [appserverdomain]/&#39;server&#39;/adobe/LiveCycleServer/DocumentStorage
   * (WebSphere) [appserver root]/installedApps/adobe/&#39;server&#39;/DocumentStorage

* **(Nur AEM Forms unter JEE),** AEM Forms-Serverprotokolle und temporäres Verzeichnis. Der Standardspeicherort lautet:

   * Server logs - [AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs
   * Temp directory - [AEM Forms installation directory]\temp

>[!NOTE]
>
>* If you are using a different location for GDS and temporary directory, open AdminUI at `https://'[server]:[port]'/adminui`, navigate to **Home > Settings > Core System Settings > Core Configurations** to confirm the location in use.

* Wenn der AEM Forms-Server selbst nach dem Ausschluss der vorgeschlagenen Ordner langsam arbeitet, schließen Sie auch die ausführbare Java-Datei (java.exe) aus.



