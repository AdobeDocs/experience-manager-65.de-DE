---
title: Leistungsoptimierung für AEM Forms-Server
description: Damit AEM Forms optimal funktioniert, können Sie die Cacheeinstellungen und JVM-Parameter anpassen. Außerdem kann die Verwendung eines Webservers die Leistung der AEM Forms-Bereitstellung verbessern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: 22926757-9cdb-4f8a-9bd9-16ddbc3f954a
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 26%

---

# Leistungsoptimierung des AEM Forms-Servers{#performance-tuning-of-aem-forms-server}

In diesem Artikel werden Strategien und Best Practices besprochen, die Sie implementieren können, um Engpässe zu reduzieren und die Leistung Ihrer AEM Forms-Implementierung zu optimieren.

## Cacheeinstellungen {#cache-settings}

Sie können die Cachestrategie für AEM Forms mithilfe der **Mobile Forms-Konfigurationen** -Komponente in der AEM Web-Konfigurationskonsole unter:

* (AEM Forms on OSGi) `https://'[server]:[port]'/system/console/configMgr`
* (AEM Forms unter JEE) `https://'[server]:[port]'/lc/system/console/configMgr`

Die verfügbaren Optionen für die Zwischenspeicherung sind:

* **Keines**: Erzwingt, dass kein Artefakt zwischengespeichert wird. Dies verlangsamt in der Praxis die Leistung und erfordert aufgrund des Fehlens von Cache eine hohe Speicherverfügbarkeit.
* **Konservativ**: Dient zum Zwischenspeichern nur der Zwischenartefakte, die vor dem Rendern des Formulars generiert werden, z. B. einer Vorlage, die Inline-Fragmente und Bilder enthält.
* **Aggressiv**: Erzwingt das Zwischenspeichern von fast allem, was zwischengespeichert werden kann, einschließlich gerenderter HTML-Inhalte neben allen Artefakten aus der Cachestufe &quot;Konservativ&quot;. Dies führt zur besten Leistung, verbraucht aber auch mehr Speicher zum Speichern zwischengespeicherter Artefakte. Aggressive Cachestrategie bedeutet, dass Sie beim Rendern eines Formulars eine konstante Zeitleistung erhalten, da der gerenderte Inhalt zwischengespeichert wird.

Die standardmäßigen Cacheeinstellungen für AEM Forms erweisen sich für eine optimale Leistung möglicherweise als unzureichend. Daher wird die Verwendung der folgenden Einstellungen empfohlen:

* **Cache-Strategie**: Aggressiv
* **Cachegröße** (in Bezug auf Anzahl von Formularen): Bei Bedarf
* **Max Objektgröße**: Bei Bedarf

![Mobile Forms-Konfigurationen](assets/snap.png)

>[!NOTE]
>
>Wenn Sie AEM Dispatcher verwenden, um adaptive Formulare zwischenzuspeichern, werden auch adaptive Formulare zwischengespeichert, die Formulare mit vorausgefüllten Daten enthalten. Wenn solche Formulare aus dem AEM Dispatcher-Cache bereitgestellt werden, kann dies dazu führen, dass vorausgefüllte oder veraltete Daten für die Benutzer bereitgestellt werden. Verwenden Sie AEM Dispatcher also, um adaptive Formulare zwischenzuspeichern, die keine vorausgefüllten Daten verwenden. Außerdem werden zwischengespeicherte Fragmente nicht durch einen Dispatcher-Cache automatisch invalidiert. Verwenden Sie sie also nicht zum Zwischenspeichern von Formularfragmenten. Verwenden Sie für solche Formulare und Fragmente [Adaptiver Formularcache](../../forms/using/configure-adaptive-forms-cache.md).

## JVM-Parameter  {#jvm-parameters}

Für eine optimale Leistung wird die Verwendung der folgenden JVM empfohlen `init` Argumente zum Konfigurieren der `Java heap` und `PermGen`.

```shell
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Die empfohlenen Einstellungen gelten für Windows 2008 R2 8 Core und Oracle HotSpot 1.7 (64-bit) JDK und sollten gemäß Ihrer Systemkonfiguration angepasst werden.

## Webserver verwenden {#using-a-web-server}

Adaptive Formulare und HTML5-Formulare werden im HTML5-Format wiedergegeben. Die resultierende Ausgabe kann abhängig von Faktoren wie der Formulargröße und den Bildern im Formular groß sein. Um die Datenübertragung zu optimieren, wird empfohlen, die HTML-Antwort mit dem Webserver zu komprimieren, von dem aus die Anforderung bereitgestellt wird. Dieser Ansatz reduziert die Antwortgröße, den Netzwerk-Traffic und die zum Streamen von Daten zwischen Server- und Client-Computern erforderliche Zeit.

Führen Sie beispielsweise die folgenden Schritte aus, um die Komprimierung auf Apache Web Server 2.0 32-Bit mit JBoss® zu aktivieren:

>[!NOTE]
>
>Die folgenden Anweisungen gelten für keine anderen Server als Apache Web Server 2.0 32 Bit.  Informationen über spezielle Schritte für andere Server finden Sie in der entsprechenden Produktdokumentation.

Die folgenden Schritte zeigen die erforderlichen Änderungen, um die Komprimierung mit Apache Web Server zu ermöglichen

**Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem.**

* Windows: Laden Sie den Apache-Webserver von der Apache HTTP Server Project-Site herunter.
* Solaris™ 64-Bit: Laden Sie den Apache-Webserver von der Sunfreeware for Solaris™-Website herunter.
* Linux®: Der Apache-Webserver ist auf einem Linux®-System vorinstalliert.

Apache kann mit CRX über das HTTP-Protokoll kommunizieren. Die Konfigurationen dienen der Optimierung mithilfe von HTTP.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei `APACHE_HOME/conf/httpd.conf`.

   ```shell
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Für Linux® ist die Standardeinstellung `APACHE_HOME` is `/etc/httpd/`.

1. Konfigurieren Sie das Proxys auf Port 4502 von crx.
Fügen Sie in die `APACHE_HOME/conf/httpd.conf`-Konfigurationsdatei folgende Konfiguration ein.

   ```shell
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Aktivieren Sie die Komprimierung. Fügen Sie in die `APACHE_HOME/conf/httpd.conf`-Konfigurationsdatei folgende Konfiguration ein.

   **Für HTML5-Formulare**

   ```xml
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don't compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Für adaptive Formulare**

   ```xml
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don't compress
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

## Verwenden eines Antivirenprogramms auf dem Server, auf dem AEM Forms ausgeführt wird {#using-an-antivirus-on-server-running-aem-forms}

Auf Servern, auf denen eine Antivirensoftware ausgeführt wird, kann die Leistung beeinträchtigt werden. Eine ständig aktualisierte Antivirensoftware (On-Access Scan) scannt alle Dateien eines Systems. Dies kann den Server verlangsamen und die Leistung des AEM Forms beeinträchtigen.

Um die Leistung zu verbessern, können Sie die Antivirus-Software anweisen, die folgenden AEM Forms-Dateien und -Ordner von der (On-Access-)Prüfung auszuschließen:

* AEM Installationsverzeichnis. Wenn das vollständige Verzeichnis nicht ausgeschlossen werden kann, schließen Sie Folgendes aus:

   * [AEM-Installationsverzeichnis]\crx-repository\temp
   * [AEM-Installationsverzeichnis]\crx-repository\repository
   * [AEM-Installationsverzeichnis]\crx-repository\launchpad

* Temporärer Ordner des Anwendungsservers. Der Standardspeicherort lautet:

   * (JBoss®) [AEM Installationsverzeichnis]\jboss\standalone\tmp
   * (WebLogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (WebSphere®) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Nur AEM Forms on JEE)** Ordner des globalen Dokumentenspeichers (GDS). Der Standardspeicherort lautet:

   * (JBoss®) [Anwendungsserver-Stammordner]/server/&#39;server&#39;/svcnative/DocumentStorage
   * (WebLogic) [Anwendungs-Server-Domain]/&#39;Server&#39;/adobe/LiveCycleServer/DocumentStorage
   * (WebSphere®) [Anwendungsserver-Stammordner]/installedApps/adobe/&#39;server&#39;/DocumentStorage

* **(Nur AEM Forms on JEE)** AEM Forms-Serverprotokolle und temporärer Ordner. Der Standardspeicherort lautet:

   * Serverprotokolle: [AEM Forms-Installationsverzeichnis]\Adobe\AEM forms\[app-server]\server\all\logs
   * Temporäres Verzeichnis: [AEM Forms-Installationsverzeichnis]\temp

>[!NOTE]
>
* Wenn Sie einen anderen Speicherort für den Ordner des globalen Dokumentenspeichers und den temporären Ordner verwenden, öffnen Sie AdminUI`https://'[server]:[port]'/adminui`, navigieren Sie zu **Startseite > Einstellungen > Core-System > Core-Konfigurationen**, um den verwendeten Speicherort zu bestätigen.
>
* Wenn der AEM Forms-Server auch nach dem Ausschließen der vorgeschlagenen Verzeichnisse langsam funktioniert, schließen Sie auch die ausführbare Java™-Datei (java.exe) aus.
>
