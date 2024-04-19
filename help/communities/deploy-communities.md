---
title: Bereitstellen von Communities
description: Erfahren Sie, wie Sie Communities- und Community-Funktionen in Adobe Experience Manager bereitstellen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: 5b3d572d-e73d-4626-b664-c985949469c9
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1658'
ht-degree: 1%

---

# Bereitstellen von Communities {#deploying-communities}

## Voraussetzungen {#prerequisites}

* [AEM 6.5 Platform](/help/sites-deploying/deploy.md)

* AEM Communities-Lizenz

* Optionale Lizenzen für:

   * [Adobe Analytics für Communities-Funktionen](/help/communities/analytics.md)
   * [MongoDB für MSRP](/help/communities/msrp.md)
   * [Adobe Cloud für ASRP](/help/communities/asrp.md)

## Checkliste für die Installation {#installation-checklist}

**Für [AEM](/help/sites-deploying/deploy.md#what-is-aem)**

* Installieren Sie die neueste Version [AEM 6.5 Updates](#aem64updates)

* Wenn Sie die Standardanschlüsse nicht verwenden (4502, 4503), wird [Konfigurieren von Replikationsagenten](#replication-agents-on-author)
* [Replizieren des Kryptoschlüssels](#replicate-the-crypto-key)
* Wenn die Globalisierung unterstützt wird, [Einrichten der automatisierten Übersetzung](/help/sites-administering/translation.md)
(Beispiel-Setup wird für die Entwicklung bereitgestellt)

**Für [Communities-Funktionen](/help/communities/overview.md)**

* Bei der Bereitstellung eines [Verlagsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [den primären Herausgeber identifizieren](#primary-publisher)

* [Tunneldienst aktivieren](#tunnel-service-on-author)
* [Social-Anmeldung aktivieren](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Konfigurieren von Adobe Analytics](/help/communities/analytics.md)
* Richten Sie eine [Standard-E-Mail-Dienst](/help/communities/email.md)
* Auswahl für [freigegebener UGC-Speicher](/help/communities/working-with-srp.md) (**SRP**)

   * Wenn MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installieren und konfigurieren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr konfigurieren](/help/communities/solr.md)
      * [MSRP auswählen](/help/communities/srp-config.md)

   * Wenn relationale Datenbank SRP [(DSRP)](/help/communities/dsrp.md)

      * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
      * [MySQL für DSRP installieren und konfigurieren](/help/communities/dsrp-mysql.md)
      * [Solr konfigurieren](/help/communities/solr.md)
      * [DSRP auswählen](/help/communities/srp-config.md)

   * Wenn Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * Wenden Sie sich zur Bereitstellung an Ihren Kundenbetreuer
      * [ASRP auswählen](/help/communities/srp-config.md)

   * Wenn JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * Kein freigegebener UGC-Speicher (benutzergenerierter Inhalt) :

         * UGC wird nie repliziert
         * UGC ist nur auf der AEM Instanz oder dem Cluster sichtbar, in dem sie eingegeben wurde

         * Die Standardeinstellung ist JSRP

## Neueste Versionen {#latest-releases}

AEM 6.5 Communities GA umfasst Communities-Pakete. Weitere Informationen zu Updates für AEM 6.5 [Communities](/help/release-notes/release-notes.md#experiencemanagercommunities), siehe [AEM 6.5 - Versionshinweise](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Ab AEM 6.4 werden Aktualisierungen an Communities als Teil von AEM Cumulative Fix Packs und Service Packs bereitgestellt.

Die neuesten Updates für AEM 6.5 finden Sie unter [Adobe Experience Manager 6.4 Cumulative Fix Packs und Service Packs](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates).

### Versionsverlauf {#version-history}

Wie AEM 6.4 und höher sind AEM Communities-Funktionen und Hotfixes Teil von AEM Communities Cumulative Fix Packs und Service Packs. Es gibt daher keine separaten Feature Packs.

### JDBC-Treiber für MySQL {#jdbc-driver-for-mysql}

Eine Communities-Funktion verwendet eine MySQL-Datenbank:

* Für [DSRP](/help/communities/dsrp.md): Speichern von UGC

Der MySQL-Connector muss separat abgerufen und installiert werden.

Die erforderlichen Schritte sind:

1. Laden Sie das ZIP-Archiv herunter von [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Die Version muss >= 5.1.38 sein.

1. Extrahieren Sie mysql-connector-java-&lt;version>-bin.jar (Bundle) aus dem Archiv
1. Verwenden Sie die Web-Konsole, um das Bundle zu installieren und zu starten:

   * Beispiel: https://localhost:4502/system/console/bundles
   * Klicken Sie auf **`Install/Update`**
   * Durchsuchen... , um das aus dem heruntergeladenen ZIP-Archiv extrahierte Bundle auszuwählen.
   * Überprüfen Sie, ob *JDBC-Treiber der oracle Corporation für MySQLcom.mysql.jdbc* aktiv ist, und starten Sie es, falls nicht (oder überprüfen Sie die Protokolle)

1. Wenn Sie nach der Konfiguration von JDBC in einer vorhandenen Bereitstellung installieren, binden Sie JDBC erneut an den neuen Connector, indem Sie die JDBC-Konfiguration von der Web-Konsole aus erneut speichern:
   * Beispiel: https://localhost:4502/system/console/configMgr
   * Suchen `Day Commons JDBC Connections Pool` Konfiguration
   * Zum Öffnen auswählen
   * Klicken Sie auf `Save`

1. Wiederholen Sie die Schritte 3 und 4 für alle Autoren- und Veröffentlichungsinstanzen.

Weitere Informationen zur Installation von Bundles finden Sie auf der [Web-Konsole](/help/sites-deploying/web-console.md) Seite.

#### Beispiel : MySQL Connector-Bundle installiert {#example-installed-mysql-connector-bundle}

![connector-bundle](assets/connector-bundle.png)



### AEM erweiterte MLS {#aem-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) erweiterte mehrsprachige Suche (MLS) unterstützen kann, sind zusätzlich zu einem benutzerdefinierten Schema und einer Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst.

Der erweiterte MLS-Download (auch bekannt als `phasetwo`) ist über das Adobe-Repository verfügbar:

* AEM-SOLR-MLS-phasetwo

  Informationen zum Abrufen des erweiterten MLS-Pakets finden Sie unter [AEM erweiterte MLS](deploy-communities.md#aem-advanced-mls) im Abschnitt &quot;Bereitstellung&quot;der Dokumentation.

   * Version 1.2.40, 6. April 2016
   * AEM-SOLR-MLS-phasetwo-1.2.40.zip herunterladen

Weitere Informationen und Installationsinformationen finden Sie unter [Solr-Konfiguration](/help/communities/solr.md) für SRP.

### Über Links zur Paketfreigabe {#about-links-to-package-share}

**In Adobe AEM Cloud sichtbare Pakete**

Die Links zu Paketen auf dieser Seite erfordern keine laufende Instanz von AEM, da sie zu Package Share auf gehören `adobeaemcloud.com`. Während die Pakete sichtbar sind, wird die `Install` -Schaltfläche ist für die Installation der Pakete auf einer Adobe-gehosteten Site vorgesehen. Wenn Sie eine Installation auf einer lokalen AEM-Instanz durchführen möchten, wählen Sie `Install` führt zu einem Fehler.

**Installieren auf einer lokalen AEM-Instanz**

So installieren Sie die Pakete, die in `adobeaemcloud.com` auf einer lokalen AEM-Instanz muss das Paket zuerst auf eine lokale Festplatte heruntergeladen werden:

* Wählen Sie die **Assets** tab
* Auswählen **Herunterladen auf Festplatte**

Verwenden Sie auf der lokalen AEM-Instanz Package Manager (z. B. [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)), um in das lokale AEM-Package-Repository hochzuladen.

Alternativ können Sie über Package Share über die lokale AEM auf das Paket zugreifen (z. B. [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), die `Download` -Schaltfläche wird in das Package-Repository der lokalen AEM-Instanz heruntergeladen.

Sobald Sie sich im Package-Repository der lokalen AEM-Instanz befinden, installieren Sie das Package mit Package Manager.

Weitere Informationen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md#package-share).

## Empfohlene Bereitstellungen {#recommended-deployments}

In AEM Communities wird UGC mithilfe eines gemeinsamen Stores gespeichert, der häufig als [Storage Resource Provider (SRP)](/help/communities/working-with-srp.md). Die empfohlene Implementierung konzentriert sich auf die Auswahl einer SRP-Option für den gemeinsamen Speicher.

Der gemeinsame Speicher unterstützt die Moderation von und die Analyse von UGC in der Veröffentlichungsumgebung, während die Notwendigkeit für [Replikation](/help/communities/sync.md) von UGC.

* [Community-Inhaltsspeicher](/help/communities/working-with-srp.md) : beschreibt die SRP-Speicheroptionen für AEM Communities

* [Empfohlene Topologien](/help/communities/topologies.md) : beschreibt die je nach Anwendungsfall und SRP-Auswahl zu verwendende Topologie

## Upgrade {#upgrading}

Bei der Aktualisierung von früheren Versionen von AEM auf die AEM 6.5-Plattform ist es wichtig, Folgendes zu lesen: [Upgrade auf AEM 6.5](/help/sites-deploying/upgrade.md).

Lesen Sie neben der Aktualisierung der Plattform auch [Upgrade auf AEM Communities 6.5](/help/communities/upgrade.md) , um mehr über Communities-Änderungen zu erfahren.

## Konfigurationen {#configurations}

### Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der ausgewählten Bereitstellung um eine [Veröffentlichungsfarm](/help/communities/topologies.md#tarmk-publish-farm), muss eine AEM Veröffentlichungsinstanz als **`primary publisher`** für Aktivitäten, die nicht in allen Instanzen auftreten sollten. Zum Beispiel Funktionen, die auf **Benachrichtigungen** oder **Adobe Analytics**.

Standardmäßig wird die Variable `AEM Communities Publisher Configuration` Die OSGi-Konfiguration wird mit der **`Primary Publisher`** -Kontrollkästchen aktiviert, sodass sich alle Veröffentlichungsinstanzen in einer Veröffentlichungsfarm selbst als primär identifizieren.

Daher ist es notwendig, **die Konfiguration auf allen sekundären Veröffentlichungsinstanzen bearbeiten** , um die **`Primary Publisher`** aktivieren.

![primary-publisher](assets/primary-publisher.png)

Für alle anderen (sekundären) Veröffentlichungsinstanzen in einer Veröffentlichungsfarm:

* Anmelden mit Administratorrechten
* Zugriff auf [Web-Konsole](/help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Suchen Sie die `AEM Communities Publisher Configuration`
* Bearbeiten-Symbol auswählen
* Deaktivieren Sie die **Primärer Herausgeber** box
* Wählen Sie **Speichern** aus

### Replikationsagenten auf der Autoreninstanz {#replication-agents-on-author}

Die Replikation wird für Site-Inhalte verwendet, die in der Veröffentlichungsumgebung erstellt werden, z. B. Community-Gruppen, und für die Verwaltung von Mitgliedern und Mitgliedergruppen aus der Autorenumgebung mithilfe der [Tunneldienst](#tunnel-service-on-author).

Stellen Sie für den primären Herausgeber sicher, dass die [Konfiguration des Replikationsagenten](/help/sites-deploying/replication.md) den Veröffentlichungsserver und den autorisierten Benutzer korrekt identifiziert. Der standardmäßig autorisierte Benutzer `admin,` verfügt bereits über die entsprechenden Berechtigungen (ist Mitglied von `Communities Administrators`).

Damit andere Benutzer über die entsprechenden Berechtigungen verfügen, müssen sie als Mitglied der `administrators` Benutzergruppe (auch Mitglied von `Communities Administrators`).

Es gibt zwei Replikationsagenten in der Autorenumgebung, für die die Transportkonfiguration korrekt konfiguriert werden muss.

* Zugriff auf die Replikationskonsole im Autorenmodus

   * Navigieren Sie von der globalen Navigation zu **[!UICONTROL Instrumente]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Replikation]** > **[!UICONTROL Agenten für Autor]**

* Gehen Sie für beide Agenten genauso vor:

   * **Standardagent (publish)**
   * **Agenten für Rückwärtsreplikation (Rückwärts veröffentlichen)**

      1. Wählen Sie den Agenten
      1. Auswählen **edit**
      1. Wählen Sie die **Verkehr** tab
      1. Wenn dies nicht der Anschluss ist `4503`, bearbeiten Sie die **URI** zum Angeben des richtigen Ports

      1. Wenn dies nicht der Benutzer ist `admin`, bearbeiten Sie die **Benutzer** und **Passwort** , um ein Mitglied der `administrators` Benutzergruppe

Die folgenden Abbildungen zeigen die Ergebnisse einer Änderung des Ports von 4503 auf 6103 durch:

#### Standardagent (publish) {#default-agent-publish}

![default-agent-publish](assets/default-agent-publish.png)

#### Agenten für Rückwärtsreplikation (Rückwärts veröffentlichen) {#reverse-replication-agent-publish-reverse}

![reverse replication-agent](assets/reverse-replication-agent.png)

### Tunnel-Dienst auf Autoreninstanz {#tunnel-service-on-author}

Bei Verwendung der Autorenumgebung zu [Erstellen von Sites](/help/communities/sites-console.md), [Ändern von Site-Eigenschaften](/help/communities/sites-console.md#modifying-site-properties) oder [Verwalten von Community-Mitgliedern](/help/communities/members.md), ist es erforderlich, auf Mitglieder (Benutzer) zuzugreifen, die in der Veröffentlichungsumgebung registriert sind, nicht auf Benutzer, die in der Autoreninstanz registriert sind.

Der Tunneldienst stellt diesen Zugriff mithilfe des Replikationsagenten auf der Autoreninstanz bereit.

Aktivieren des Tunneldienstes:

* Melden Sie sich mit Administratorrechten für Ihre Autoreninstanz an.
* Wenn der Herausgeber nicht localhost:4503 ist oder der Transportbenutzer nicht `admin`, dann [Konfigurieren des Replikationsagenten](#replication-agents-on-author)

* Zugriff auf [Web-Konsole](/help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* Suchen Sie die `AEM Communities Publish Tunnel Service`
* Bearbeiten-Symbol auswählen
* Überprüfen Sie die **enable** box
* Wählen Sie **Speichern** aus

  ![Tunneldienst](assets/tunnel-service.png)

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Es gibt zwei Funktionen von AEM Communities, für die alle AEM Serverinstanzen dieselben Verschlüsselungsschlüssel verwenden müssen. Diese [Analytics](/help/communities/analytics.md) und [ASRP](/help/communities/asrp.md).

Ab AEM 6.3 wird das Schlüsselmaterial im Dateisystem und nicht mehr im Repository gespeichert.

Um das Schlüsselmaterial aus der Autoreninstanz in alle anderen Instanzen zu kopieren, müssen Sie Folgendes tun:

* Greifen Sie auf die AEM-Instanz zu, in der sich normalerweise eine Autoreninstanz befindet, die das zu kopierende Schlüsselmaterial enthält

   * Suchen Sie die `com.adobe.granite.crypto.file` Bundle im lokalen Dateisystem, beispielsweise

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Die `bundle.info` -Datei identifiziert das Bundle

   * Navigieren Sie zum Datenordner, beispielsweise

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

      * Kopieren Sie die Dateien hmac und primary .

* Für jede AEM-Instanz

   * Navigieren Sie zum Datenordner, beispielsweise

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

   * Fügen Sie die beiden zuvor kopierten Dateien ein.
   * Es ist erforderlich, [Aktualisieren des Granite Crypto-Bundles](#refresh-the-granite-crypto-bundle) wenn die AEM-Zielinstanz ausgeführt wird

>[!CAUTION]
>
>Wenn bereits eine andere Sicherheitsfunktion konfiguriert wurde, die auf den Verschlüsselungsschlüsseln basiert, kann die Replikation der Verschlüsselungsschlüssel die Konfiguration beschädigen. Hilfe: [Kundenunterstützung kontaktieren](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support).

#### Repository-Replikation {#repository-replication}

Das Schlüsselmaterial, das im Repository gespeichert ist (wie bei AEM 6.2 und früher), kann beibehalten werden. Angeben der Systemeigenschaft `-Dcom.adobe.granite.crypto.file.disable=true` beim ersten Start jeder AEM Instanz (die das anfängliche Repository erstellt).

>[!NOTE]
>
>Stellen Sie sicher, dass [Replikationsagent auf Autoreninstanz](#replication-agents-on-author) korrekt konfiguriert ist.

Mit dem im Repository gespeicherten Schlüsselmaterial wird der Crypto-Schlüssel vom Autor auf andere Instanzen wie folgt repliziert:

Verwenden [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* Klicken Sie auf `/etc/key`
* Öffnen `Replication` tab
* Klicken Sie auf `Replicate`

* [Aktualisieren des Granite Crypto-Bundles](#refresh-the-granite-crypto-bundle)

  ![replicare-repository](assets/replicare-repository.png)

#### Aktualisieren des Granite Crypto-Bundles {#refresh-the-granite-crypto-bundle}

* Rufen Sie in jeder Veröffentlichungsinstanz die [Web-Konsole](/help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://&lt;server>:&lt;port>/system/console/bundles](https://localhost:4503/system/console/bundles)

* Suchen `Adobe Granite Crypto Support` Bundle (com.adobe.granite.crypto)
* Auswählen **Aktualisieren**

  ![granite-crypto](assets/granite-crypto.png)

* Nach einem Moment **Erfolg** sollte angezeigt werden:
  `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Stellen Sie bei Verwendung des Apache HTTP-Servers sicher, dass Sie den richtigen Servernamen für alle relevanten Einträge verwenden.

Achten Sie insbesondere darauf, den richtigen Servernamen zu verwenden, nicht `localhost`in der `RedirectMatch`.

#### Beispiel für httpd.conf {#httpd-conf-sample}

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

Informationen zur Verwendung eines Dispatchers finden Sie unter:

* AEM [Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates) Dokumentation
* [Installieren des Dispatchers](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install)
* [Konfigurieren des Dispatchers für Communities](/help/communities/dispatcher.md)
* [Bekannte Probleme](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwandte Communities - Dokumentation {#related-communities-documentation}

* Besuch [Verwalten von Communities-Sites](/help/communities/administer-landing.md) , um mehr über die Erstellung einer Community-Site, die Konfiguration von Community-Site-Vorlagen, die Moderation von Community-Inhalten, die Verwaltung von Mitgliedern und die Konfiguration von Messaging zu erfahren.

* Besuch [Entwickeln von Communities](/help/communities/communities.md) Hier erfahren Sie mehr über das Social Component Framework (SCF) und das Anpassen von Communities-Komponenten und -Funktionen.

* Besuch [Erstellen von Communities-Komponenten](/help/communities/author-communities.md) Hier erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.
