---
title: Bereitstellen von Communities
seo-title: Bereitstellen von Communities
description: Bereitstellung von AEM Communities
seo-description: Bereitstellung von AEM Communities
uuid: 18d9b424-004d-43b2-968a-318e27a93759
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: c8d7355f-5a70-40d1-bf22-62fab8002ea0
docset: aem65
translation-type: tm+mt
source-git-commit: 94bc3550a7e18b9203e7a0d495d195d7b798e012
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 6%

---


# Bereitstellen von Communities{#deploying-communities}

## Voraussetzungen {#prerequisites}

* [AEM 6.5-Plattform](/help/sites-deploying/deploy.md)

* AEM Communities-Lizenz

* Optionale Lizenzen für:

   * [Funktionen von Adobe Analytics für Communities](/help/communities/analytics.md)
   * [MongoDB für MSRP](/help/communities/msrp.md)
   * [Adobe Cloud für ASRP](/help/communities/asrp.md)

## Checkliste für die Installation {#installation-checklist}

**Für die[AEM](/help/sites-deploying/deploy.md#what-is-aem)**

* die neuesten [AEM 6.5 Updates installieren](#aem64updates)

* Wenn Sie nicht die Standardanschlüsse verwenden (4502, 4503), dann [konfigurieren Sie Replizierungsagenten](#replication-agents-on-author)
* [Verschlüsselungsschlüssel replizieren](#replicate-the-crypto-key)
* Wenn Sie die Globalisierung unterstützen, [richten Sie die automatisierte Übersetzung](/help/sites-administering/translation.md)ein (Beispiel-Setup wird für die Entwicklung bereitgestellt)

**Fähigkeit &quot;[Communities&quot;](/help/communities/overview.md)**

* bei der Bereitstellung einer [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm)den primären Herausgeber [identifizieren](#primary-publisher)

* [den Tunneldienst aktivieren](#tunnel-service-on-author)
* [Social-Anmeldung aktivieren](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [adobe analytics konfigurieren](/help/communities/analytics.md)
* einen [Standard-E-Mail-Dienst einrichten](/help/communities/email.md)
* die Wahl für [freigegebene UGC-Datenspeicherung](/help/communities/working-with-srp.md) (**SRP**) zu identifizieren.

   * if MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installieren und konfigurieren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr konfigurieren](/help/communities/solr.md)
      * [MSRP auswählen](/help/communities/srp-config.md)
   * wenn relationale Datenbank SRP [(DSRP)](/help/communities/dsrp.md)

      * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
      * [MySQL für DSRP installieren und konfigurieren](/help/communities/dsrp-mysql.md)
      * [Solr konfigurieren](/help/communities/solr.md)
      * [DSRP auswählen](/help/communities/srp-config.md)
   * if Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * bei der Bereitstellung mit Ihrem Kundenbetreuer zusammenarbeiten
      * [ASRP auswählen](/help/communities/srp-config.md)
   * if JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * kein freigegebener UGC-Store:

         * UGC wird nie repliziert
         * UGC nur sichtbar auf AEM Instanz oder Cluster, in dem sie eingegeben wurde
      * default ist JSRP

   Für die **[Aktivierungsfunktion](/help/communities/overview.md#enablement-community)**

   * [Installieren und Konfigurieren von FFmpeg](/help/communities/ffmpeg.md)
   * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
   * [aem communities SCORM-Engine installieren](#scorm-package)
   * [MySQL für die Aktivierung installieren und konfigurieren](/help/communities/mysql.md)






## Latest Releases {#latest-releases}

AEM 6.5 Communities GA mit Communities package. Informationen zu Updates für AEM 6.5 [Communities](/help/release-notes/release-notes.md#experiencemanagercommunities)finden Sie in den [AEM 6.5 Versionshinweisen](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Ab AEM 6.4 werden Updates an Communities als Teil AEM Cumulative Fix Packs und Service Packs bereitgestellt.

Die neuesten Updates für AEM 6.5 finden Sie unter [Adobe Experience Manager 6.4 Cumulative Fix Packs and Service Packs](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Version History {#version-history}

Wie bei AEM 6.4 und höher sind AEM Communities-Funktionen und Hotfixes Teil der AEM Communities-Pakete für kumulative Fixpacks und Service Packs. Es gibt daher keine separaten Feature Packs.

### JDBC-Treiber für MySQL {#jdbc-driver-for-mysql}

Zwei Communities-Funktionen verwenden eine MySQL-Datenbank:

* für [Aktivierung](/help/communities/enablement.md) : Aufzeichnung von SCORM-Aktivitäten und -Lernenden
* für [DSRP](/help/communities/dsrp.md) : Speichern benutzergenerierter Inhalte (UGC)

Der MySQL-Connector muss separat bezogen und installiert werden.

Die erforderlichen Schritte sind:

1. ZIP-Archiv von [https://dev.mysql.com/downloads/connector/j/ herunterladen](https://dev.mysql.com/downloads/connector/j/)

   * Version muss >= 5.1.38 sein

1. extrahieren Sie mysql-connector-java-&lt;version>-bin.jar (bundle) aus dem Archiv
1. Verwenden Sie die Web-Konsole, um das Bundle zu installieren und Beginn:

   * Beispiel: https://localhost:4502/system/console/bundles
   * auswählen **`Install/Update`**
   * Durchsuchen... zum Auswählen des aus dem heruntergeladenen ZIP-Archiv extrahierten Bundles
   * Überprüfen Sie, ob* der JDBC-Treiber der Oracle Corporation für MySQLcom.mysql.jdbc* aktiv ist, und überprüfen Sie ihn gegebenenfalls (oder überprüfen Sie die Protokolle).

1. Wenn Sie nach der Konfiguration von JDBC in einer vorhandenen Bereitstellung installieren, binden Sie JDBC erneut an den neuen Connector, indem Sie die JDBC-Konfiguration aus der Webkonsole erneut binden:

   * Beispiel: https://localhost:4502/system/console/configMgr
   * Konfiguration suchen `Day Commons JDBC Connections Pool`
   * öffnen
   * auswählen `Save`

1. Wiederholen Sie die Schritte 3 und 4 für alle Autoren- und Veröffentlichungsinstanzen.

Weitere Informationen zum Installieren von Bundles finden Sie auf der Seite [Web-Konsole](/help/sites-deploying/web-console.md#bundles) .

#### Beispiel: Installiertes MySQL Connector-Bundle {#example-installed-mysql-connector-bundle}

![](../assets/chlimage_1-125.png)

### SCORM-Paket {#scorm-package}

Das Shareable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

Die AEM Communities SCORM-Engine ist für die [Aktivierungsfunktion](/help/communities/overview.md#enablement-community) erforderlich. Von AEM 6.5 Communities unterstützte Scorm-Pakete:

* [cq-social-scorm-package, Version 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) , die die [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -Engine enthält.

**So installieren Sie ein SCORM-Paket**

1. Installieren Sie das [cq-social-scorm-package, Version 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) , über die Paketfreigabe
1. Laden Sie `/libs/social/config/scorm/database_scormengine_data.sql` von der cq-Instanz herunter und führen Sie sie auf dem mysql-Server aus, um ein aktualisiertes scormEngineDB-Schema zu erstellen.
1. hinzufügen `/content/communities/scorm/RecordResults` in der Eigenschaft &quot;Ausgeschlossene Pfade&quot;im CSRF-Filter von Herausgebern `https://<hostname>:<port>/system/console/configMgr` aus.

#### SCORM-Protokollierung {#scorm-logging}

Nach der Installation wird die gesamte Aktivität zur Aktivierung ausführlich an die Systemkonsole protokolliert.

Bei Bedarf kann die Protokollebene für das `RusticiSoftware.*` Paket auf WARN eingestellt werden.

Informationen zum Arbeiten mit Protokollen finden Sie unter [Arbeiten mit Audit-Aufzeichnungen und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### AEM Advanced MLS {#aem-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) die erweiterte mehrsprachige Suche (MLS) unterstützen kann, sind zusätzlich zu einer benutzerdefinierten Schema- und Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst.

Der erweiterte MLS-Download (auch &quot;phasetwo&quot;genannt) ist im Repository der Adobe verfügbar:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Version 1.2.40, 6. April 2016
   * download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Weitere Informationen und Installationsinformationen finden Sie unter [Solr-Konfiguration](/help/communities/solr.md) für SRP.

### Über Links zur Paketfreigabe {#about-links-to-package-share}

**In Adobe AEM Cloud sichtbare Pakete**

Die Links zu Paketen auf dieser Seite erfordern keine laufende Instanz von AEM, da sie auf Package Share lauten `adobeaemcloud.com`. Während die Pakete angezeigt werden können, ist die `Install`Schaltfläche zum Installieren der Pakete auf einer Adobe gehosteten Site. Wenn Sie beabsichtigen, eine Installation auf einer lokalen AEM durchzuführen, `Install`führt die Auswahl zu einem Fehler.

**Installation auf einer lokalen AEM-Instanz**

Um die Pakete zu installieren, die in `adobeaemcloud.com` einer lokalen AEM angezeigt werden, muss das Paket zunächst auf eine lokale Festplatte heruntergeladen werden:

* select the **Assets** tab
* select **download to disk**

Verwenden Sie auf der lokalen AEM Package Manager (z. B. [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)), um das Paket-Repository in AEM lokalen Repository hochzuladen.

Alternativ dazu wird beim Zugriff auf das Paket mit Package Share von der lokalen AEM Instanz aus (z. B. [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)) die `Download`Schaltfläche zum Paket-Repository der lokalen AEM-Instanz heruntergeladen.

Sobald Sie sich im Paket-Repository der lokalen AEM-Instanz befinden, installieren Sie das Paket mit Package Manager.

Weitere Informationen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md#package-share).

## Empfohlene Bereitstellungen {#recommended-deployments}

In AEM Communities wird ein gemeinsamer Speicher zum Speichern benutzergenerierter Inhalte (UGC) verwendet und häufig als [Datenspeicherung Resource Provider (SRP)](/help/communities/working-with-srp.md)bezeichnet. Die empfohlene Bereitstellung konzentriert sich auf die Auswahl einer SRP-Option für den gemeinsamen Speicher.

Der gemeinsame Speicher unterstützt die Moderation und Analyse von UGC in der Veröffentlichungs-Umgebung, während gleichzeitig die [Replikation](/help/communities/sync.md) von UGC entfällt.

* [Community Content Store](/help/communities/working-with-srp.md) : beschreibt die Optionen für die SRP-Datenspeicherung für AEM Communities

* [Empfohlene Topologien](/help/communities/topologies.md) : die je nach Anwendungsfall und SRP-Auswahl zu verwendende Topologie

## Aktualisieren {#upgrading}

Bei der Aktualisierung auf die AEM 6.5 Plattform von früheren Versionen von AEM ist es wichtig, [Upgrade auf AEM 6.5](/help/sites-deploying/upgrade.md)zu lesen.

Lesen Sie neben der Aktualisierung der Plattform [Upgrade auf AEM Communities 6.5](/help/communities/upgrade.md) , um mehr über Änderungen in Communities zu erfahren.

## Konfigurationen {#configurations}

### Primär Publisher {#primary-publisher}

Wenn es sich bei der gewählten Bereitstellung um eine [Veröffentlichungsfarm](/help/communities/topologies.md#tarmk-publish-farm)handelt, muss eine AEM Instanz im Veröffentlichungsmodus als die Instanz **`primary publisher`** für Aktivitäten identifiziert werden, die nicht in allen Instanzen auftreten sollten, z. B. Funktionen, die auf **Benachrichtigungen **oder **Adobe Analytics** basieren.

Standardmäßig wird die `AEM Communities Publisher Configuration` OSGi-Konfiguration mit dem Kontrollkästchen **`Primary Publisher`** konfiguriert, sodass alle Instanzen im Veröffentlichungsmodus in einer Veröffentlichungsfarm sich selbst als Primär identifizieren.

Daher müssen Sie die Konfiguration für alle sekundären Veröffentlichungsinstanzen **bearbeiten, um das Kontrollkästchen zu deaktivieren** . **`Primary Publisher`**

![](../assets/chlimage_1-126.png)

Für alle anderen (sekundären) Veröffentlichungsinstanzen in einer Veröffentlichungsfarm:

* Melden Sie sich mit Administratorrechten an.
* access the [web console](/help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* suchen `AEM Communities Publisher Configuration`
* Wählen Sie das Bearbeitungssymbol aus.
* Deaktivieren Sie das Kontrollkästchen **Primär Publisher** .
* Wählen Sie **Save** aus.

### Replizierungsagenten beim Autor {#replication-agents-on-author}

Die Replikation wird für Site-Inhalte verwendet, die in der Veröffentlichungsgruppe erstellt wurden, z. B. Community-Umgebung, sowie für die Verwaltung von Mitgliedern und Mitgliedsgruppen aus der Autorenversion mithilfe des [Tunneldienstes](#tunnel-service-on-author).

Stellen Sie für den primären Herausgeber sicher, dass die [Replication Agent-Konfiguration](/help/sites-deploying/replication.md) den Veröffentlichungsserver und den autorisierten Benutzer richtig identifiziert. Der standardmäßig autorisierte Benutzer hat `admin,` bereits die entsprechenden Berechtigungen (ist Mitglied von `Communities Administrators`).

Damit andere Benutzer über die entsprechenden Berechtigungen verfügen können, müssen sie als Mitglied der `administrators` Benutzergruppe (auch Mitglied von `Communities Administrators`) hinzugefügt werden.

Es gibt zwei Replizierungsagenten in der Authoring-Umgebung, für die die Transportkonfiguration korrekt konfiguriert werden muss.

* Zugriff auf die Replikationskonsole beim Autor

   * von der globalen Navigation aus: **Werkzeuge, Bereitstellung, Replikation, Agenten beim Autor**

* für beide Agenten das gleiche Verfahren befolgen:

   * **Standardagent (veröffentlichen)**
   * **Agenten für Rückwärtsreplikation (Rückwärtsveröffentlichen)**

      1. Agent auswählen
      1. select **edit**
      1. select the **Transport** tab
      1. Wenn kein Anschluss vorhanden `4503`ist, bearbeiten Sie den **URI** , um den richtigen Anschluss anzugeben.

      1. Wenn kein Benutzer `admin`, bearbeiten Sie **Benutzer** und **Kennwort** , um ein Mitglied der `administrators` Benutzergruppe anzugeben.

Die folgenden Abbildungen zeigen die Ergebnisse einer Änderung des Anschlusses von 4503 auf 6103 durch:

#### Standardagent (veröffentlichen) {#default-agent-publish}

![configure-limits](../assets/configure-limits.png)

#### Agenten für Rückwärtsreplikation (Rückwärtsveröffentlichen) {#reverse-replication-agent-publish-reverse}

![](../assets/chlimage_1-128.png)

### Tunneldienst beim Autor {#tunnel-service-on-author}

Wenn Sie mit der Autorenversion Websites [](/help/communities/sites-console.md)erstellen, Site-Eigenschaften [](/help/communities/sites-console.md#modifying-site-properties) ändern oder Community-Mitglieder [](/help/communities/members.md)verwalten, müssen Sie auf in der Umgebung &quot;Veröffentlichen&quot;registrierte Mitglieder (Benutzer) zugreifen, nicht auf Benutzer, die beim Autor registriert sind.

Der Tunneldienst bietet diesen Zugriff mithilfe des Replizierungsagenten beim Autor.

So aktivieren Sie den Tunneldienst:

* on **author**
* Melden Sie sich mit Administratorrechten an.
* Wenn der Herausgeber nicht localhost:4503 ist oder der Transportbenutzer nicht `admin`ist, [konfigurieren Sie den Replizierungsagenten](#replication-agents-on-author)

* Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* suchen `AEM Communities Publish Tunnel Service`
* Wählen Sie das Bearbeitungssymbol aus.
* Kontrollkästchen **Aktivieren **Kontrollkästchen
* Wählen Sie **Save** aus.

![](../assets/chlimage_1-129.png)

### Crypto-Schlüssel replizieren {#replicate-the-crypto-key}

Es gibt zwei Funktionen von AEM Communities, bei denen alle AEM Serverinstanzen dieselben Verschlüsselungsschlüssel verwenden müssen. Dies sind [Analytics](/help/communities/analytics.md) und [ASRP](/help/communities/asrp.md).

Ab AEM 6.3 wird das Schlüsselmaterial im Dateisystem und nicht mehr im Repository gespeichert.

Um das Schlüsselmaterial vom Autor in alle anderen Instanzen zu kopieren, müssen Sie Folgendes tun:

* Zugriff auf die AEM Instanz, normalerweise eine Autoreninstanz, die das zu kopierende Schlüsselmaterial enthält

   * locate the `com.adobe.granite.crypto.file` bundle in the local file system
for example,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * die `bundle.info` Datei identifiziert das Bundle
   * zum Beispiel in den Datenordner navigieren,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Kopieren Sie die Dateien &quot;hmac&quot;und &quot;primary node&quot;



* für jede Zielgruppe AEM Instanz

   * zum Beispiel in den Datenordner navigieren,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Einfügen der beiden zuvor kopierten Dateien
   * Es ist erforderlich, das Granite Crypto-Bundle [zu](#refresh-the-granite-crypto-bundle) aktualisieren, wenn die Zielgruppe AEM Instanz derzeit ausgeführt wird.


>[!CAUTION]
>
>Wenn bereits eine andere Sicherheitsfunktion konfiguriert wurde, die auf den Verschlüsselungsschlüsseln basiert, könnte die Replizierung der Verschlüsselungsschlüssel die Konfiguration beschädigen. Wenden Sie sich zwecks Hilfe [an die Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).

#### Repository-Replikation {#repository-replication}

Die Speicherung des Schlüsselmaterials im Repository kann, wie bei AEM 6.2 und früher, beibehalten werden, indem beim ersten Start jeder AEM Instanz (die das anfängliche Repository erstellt) die folgende Systemeigenschaft angegeben wird:

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es ist wichtig zu überprüfen, ob der [Replizierungsagenten beim Autor](#replication-agents-on-author) richtig konfiguriert ist.

Wenn das Schlüsselmaterial im Repository gespeichert ist, erfolgt die Replizierung des Verschlüsselungsschlüssels vom Autor zu anderen Instanzen wie folgt:

Using [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) :

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* auswählen `/etc/key`
* Register öffnen `Replication`
* auswählen `Replicate`

* [Granite Crypto-Bundle aktualisieren](#refresh-the-granite-crypto-bundle)

![](../assets/chlimage_1-130.png)

#### Granite Crypto-Bundle aktualisieren {#refresh-the-granite-crypto-bundle}

* Rufen Sie in jeder Instanz im Veröffentlichungsmodus die [Webkonsole auf](/help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://&lt;server>:&lt;port>/system/console/bundles](https://localhost:4503/system/console/bundles)

* find `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* auswählen **Aktualisieren**

![](../assets/chlimage_1-131.png)

* Nach einem Augenblick sollte ein **Erfolgsdialog angezeigt werden:
   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Wenn Sie den Apache HTTP-Server verwenden, stellen Sie sicher, dass Sie den richtigen Servernamen für alle relevanten Einträge verwenden.

Achten Sie insbesondere darauf, den richtigen Servernamen zu verwenden, nicht `localhost`in der `RedirectMatch`.

#### httpd.conf-Beispiel {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site :
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Wenn Sie einen Dispatcher verwenden, siehe:

* AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) -Dokumentation
* [Installieren des Dispatchers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Konfigurieren von Dispatcher für Communities](/help/communities/dispatcher.md)
* [Bekannte Probleme](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Unter [Communities-Sites verwalten](/help/communities/administer-landing.md) erfahren Sie mehr darüber, wie Sie Community-Sites erstellen, Community-Site-Vorlagen bearbeiten, Community-Inhalte moderieren, Mitglieder verwalten und Messaging-Systeme konfigurieren können.

* Visit [Developing Communities](/help/communities/communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Unter [Authoring Communities-Komponenten](/help/communities/author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

