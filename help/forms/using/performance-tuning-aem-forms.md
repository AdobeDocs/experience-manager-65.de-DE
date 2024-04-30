---
title: Leistungsoptimierung für AEM Forms-Server
description: Damit AEM Forms optimal funktioniert, können Sie die Cache-Einstellungen und JVM-Parameter anpassen. Durch das Verwenden eines Webservers lässt sich auch die Leistung der AEM Forms-Bereitstellung verbessern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: 22926757-9cdb-4f8a-9bd9-16ddbc3f954a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '902'
ht-degree: 100%

---

# Leistungsoptimierung für AEM Forms-Server{#performance-tuning-of-aem-forms-server}

In diesem Artikel werden Strategien und Best Practices beschrieben, die Sie implementieren können, um Engpässe zu reduzieren und die Leistung Ihrer AEM Forms-Bereitzustellung zu optimieren.

## Cache-Einstellungen {#cache-settings}

Sie können die Cache-Strategie für AEM Forms mithilfe der Komponente **Mobile Forms-Konfigurationen** in AEM Web Configuration Console konfigurieren und steuern:

* (AEM Forms on OSGi) `https://'[server]:[port]'/system/console/configMgr`
* (AEM Forms unter JEE) `https://'[server]:[port]'/lc/system/console/configMgr`

Für das Caching sind folgende Optionen verfügbar:

* **Keine**: Verhindert das Caching von Artefakten. Auf diese Weise wird tatsächlich die Leistung beeinträchtigt. Aufgrund des nicht vorhandenen Caches ist zudem eine hohe Speicherverfügbarkeit erforderlich.
* **Konservativ**: Schreibt vor, dass nur die Zwischenartefakte zwischengespeichert werden, die vor dem Rendern des Formulars generiert werden, z. B. Vorlagen mit Inline-Fragmenten und Bildern.
* **Aggressie**: Setzt durch, dass fast alle Caching-fähigen Elemente zwischengespeichert werden, einschließlich gerenderter HTML-Inhalte neben allen Artefakten der Cache-Ebene „Konservativ“. Dies ergibt die beste Leistung, verbraucht aber mehr Platz für die Speicherung der zwischengespeicherten Artefakte. Eine aggressive Caching-Strategie bedeutet, dass Sie beim Rendern eines Formulars eine konstante Zeitleistung erhalten, da der gerenderte Inhalt zwischengespeichert wird.

Die standardmäßigen Cacheeinstellungen für AEM Forms erweisen sich für eine optimale Leistung möglicherweise als unzureichend. Daher wird die Verwendung der folgenden Einstellungen empfohlen:

* **Cache-Strategie**: Aggressiv
* **Cachegröße** (in Bezug auf Anzahl von Formularen): Bei Bedarf
* **Max Objektgröße**: Bei Bedarf

![Mobile Forms-Konfigurationen](assets/snap.png)

>[!NOTE]
>
>Wenn Sie AEM Dispatcher zum Caching adaptiver Formulare verwenden, werden dabei auch adaptive Formulare im Cache gespeichert, die Formulare mit vorausgefüllten Daten enthalten. Werden solche Formulare aus dem AEM Dispatcher-Cache bereitgestellt, erhalten die Benutzenden eventuell vorausgefüllte oder veraltete Daten. Verwenden Sie AEM Dispatcher daher zum Zwischenspeichern von Formularen, die keine vorausgefüllten Daten enthalten. Darüber hinaus werden im Dispatcher-Cache gespeicherte Fragmente nicht automatisch invalidiert. Verwenden Sie diesen daher nicht zum Zwischenspeichern von Formularfragmenten. Nutzen Sie für solche Formulare und Fragmente den [Cache für adaptive Formulare](../../forms/using/configure-adaptive-forms-cache.md).

## JVM-Parameter  {#jvm-parameters}

Für eine optimale Leistung werden folgende `init`-JVM-Argumente empfohlen, um `Java heap` und `PermGen` zu konfigurieren.

```shell
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Die empfohlenen Einstellungen gelten für Windows 2008 R2 8 Core und Oracle HotSpot 1.7 (64-bit) JDK und sollten gemäß Ihrer Systemkonfiguration angepasst werden.

## Verwenden eines Webservers {#using-a-web-server}

Adaptive Formulare und HTML5-Formulare werden im HTML5-Format gerendert. Die Ausgabe kann stark von Faktoren wie der Formulargröße und den Bildern im Formular abhängen. Die empfohlene Vorgehensweise zum Optimieren der Datenübertragung besteht darin, die HTML-Antwort unter Verwendung des Webservers zu komprimieren, über den die Anfrage gestellt wird. Auf diese Weise können die Antwortgröße, der Netzwerk-Traffic und der für das Streaming der Daten zwischen Server und Clients erforderliche Zeitaufwand erheblich verringert werden.

Führen Sie beispielsweise die folgenden Schritte durch, um die Komprimierung auf Apache Web Server 2.0 32-Bit mit JBoss® zu ermöglichen:

>[!NOTE]
>
>Die folgenden Anweisungen gelten für keine anderen Server als Apache Web Server 2.0 32 Bit.  Informationen über spezielle Schritte für andere Server finden Sie in der entsprechenden Produktdokumentation.

Die folgenden Schritte zeigen die Änderungen, die für eine Komprimierung mit Apache Web Server erforderlich sind.

**Installieren Sie die Apache Web Server-Software für Ihr Betriebssystem.**

* Windows: Laden Sie Apache Web Server von der Apache HTTP Server Project-Site herunter.
* Solaris™ 64-Bit: Laden Sie Apache Web Server von der Sunfreeware-Website für Solaris™ herunter.
* Linux®: Auf Linux-Systemen ist Apache Web Server vorinstalliert.

Apache kann mit CRX über das HTTP-Protokoll kommunizieren. Die Konfigurationen dienen der Optimierung mithilfe von HTTP.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei `APACHE_HOME/conf/httpd.conf`.

   ```shell
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Für Linux® lautet der Standard für `APACHE_HOME` `/etc/httpd/`.

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
           #Do not compress
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
           #Do not compress
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

## Verwenden von Antiviren-Software auf Servern mit AEM Forms {#using-an-antivirus-on-server-running-aem-forms}

Server, auf denen Antiviren-Software ausgeführt wird, können langsam sein. Antiviren-Software mit permanenter (On-Access-)Überprüfung überprüft sämtliche Dateien auf dem System. Dadurch kann der Server langsamer werden, mit entsprechenden Auswirkungen auf AEM Forms.

Um die Leistung zu verbessern, können Sie die Antiviren-Software anweisen, die folgenden AEM Forms-Dateien und -Ordner von der permanenten (On-Access-)Überprüfung auszuschließen:

* AEM-Installationsverzeichnis. Wenn es nicht möglich ist, das gesamte Verzeichnis auszuschließen, schließen Sie die folgenden Ordner aus:

   * [AEM-Installationsverzeichnis]\crx-repository\temp
   * [AEM-Installationsverzeichnis]\crx-repository\repository
   * [AEM-Installationsverzeichnis]\crx-repository\launchpad

* Temporärverzeichnis des Anwendungs-Servers. Der Standardspeicherort lautet:

   * (JBoss®) [AEM-Installationsverzeichnis]\jboss\standalone\tmp
   * (WebLogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (WebSphere®) \Programme\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(nur AEM Forms on JEE)** Verzeichnis des globalen Dokumentenspeichers (GDS). Der Standardspeicherort lautet:

   * (JBoss®) [Anwendungs-Server-Stammordner]/server/&#39;Server&#39;/svcnative/DocumentStorage
   * (WebLogic) [Anwendungs-Server-Domain]/&#39;Server&#39;/adobe/LiveCycleServer/DocumentStorage
   * (WebSphere®) [Anwendungs-Server-Stammordner]/installedApps/adobe/&#39;Server&#39;/DocumentStorage

* **(nur AEM Forms on JEE)** AEM Forms-Server-Protokolle und -Temporärverzeichnis. Der Standardspeicherort lautet:

   * Serverprotokolle: [AEM Forms-Installationsverzeichnis]\Adobe\AEM forms\[app-server]\server\all\logs
   * Temporäres Verzeichnis: [AEM Forms-Installationsverzeichnis]\temp

>[!NOTE]
>
>* Wenn Sie einen anderen Speicherort für den Ordner des globalen Dokumentenspeichers und den temporären Ordner verwenden, öffnen Sie AdminUI`https://'[server]:[port]'/adminui`, navigieren Sie zu **Startseite > Einstellungen > Core-System > Core-Konfigurationen**, um den verwendeten Speicherort zu bestätigen.
>
>* Wenn der AEM Forms-Server auch nach dem Ausschließen der vorgeschlagenen Verzeichnisse langsam ist, schließen Sie die ausführbare Java™-Datei (java.exe) ebenfalls aus.
>
