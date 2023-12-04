---
title: SharePoint-Connector
seo-title: SharePoint Connector
description: Day JCR Connector for Microsoft SharePoint 2010 und Microsoft SharePoint 2013, Version 4.0.
seo-description: Learn about the Sharepoint Connector in AEM.
uuid: df650476-4e2a-486f-a007-b5ac437ff99f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 907316d1-3d23-4c46-bccb-bad6fe1bd1bb
docset: aem65
exl-id: 10ea7d2e-6e44-4d5c-a2b2-63c73b18f172
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 56%

---

# SharePoint-Connector{#sharepoint-connector}

Dieser Artikel enthält Details zum Adobe JCR-Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013, Version 4.0.

Der SharePoint-Connector unterstützt die folgenden Basisfunktionen:

* Lesen von Inhalten und Metadaten aus SharePoint.
* Anerkennen von SharePoint-Sicherheitseinstellungen für aufgerufene Inhalte durch Anwendung der nativen SharePoint-Authentifizierung und -Autorisierung
* Inhaltsintegration mit Content Finder
* Verwenden AEM Komponenten wie der externen Ressource zur Anzeige von SharePoint-Bildern und -Videos
* Synchronisieren von SharePoint mit AEM Assets

Alle Funktionen werden mithilfe der nativen SharePoint-Webdienste als Schnittstelle zu SharePoint-Inhalten und -Diensten implementiert.

>[!NOTE]
>
>Der SharePoint-Connector wird auch mit AEM 6.1 Service Pack 2 unterstützt. Die Einbindung virtueller Repositorys wird vom Connector nicht mehr unterstützt, weshalb keine Einbindung möglich ist. Wenn Sie über Java-APIs auf das SharePoint-Repository zugreifen möchten, verwenden Sie in Ihrem Projekt die JCR-Repository-Implementierung des SharePoint-Connectors.
>
>Installation, Konfiguration, Verwaltung und IT-Vorgänge der SharePoint-Server-Instanz und der dazugehörigen IT-Infrastruktur werden in diesem Dokument nicht behandelt. Informationen zu diesen Themen finden Sie in der [SharePoint-Dokumentation](https://www.microsoft.com/sharepoint) des Anbieters. Diese Infrastrukturkomponenten müssen ordnungsgemäß installiert, konfiguriert und betrieben werden, damit der Connector verwendet werden kann.
>

## Erste Schritte {#getting-started}

Gehen Sie wie folgt vor, um mit dem Connector zu beginnen:

* Vergewissern Sie sich, dass bei Ihnen mindestens Java 7 installiert ist.
* Laden Sie die Paketverteilungsdatei für den Connector von Software Distribution herunter.
* Gültige kopieren *license.properties* in den Ordner, der die *cq-quickstart-6.4.0.jar* -Datei.

* Doppelklicken Sie auf die JAR-Datei, um AEM zu starten, oder starten Sie sie über die Befehlszeile.
* Installieren Sie das Connector-Paket aus Package Manager.
* Konfigurieren Sie die Connector-Optionen.

## Installieren des SharePoint-Connectors {#installing-sharepoint-connector}

Der Connector ist ein Inhaltspaket, das die einfache Installation erleichtert. Installieren Sie das Paket über Package Manager und legen Sie anschließend die SharePoint-Server-URL und andere Konfigurationsoptionen fest. Der SharePoint-Inhalt steht im AEM-Repository zur Verfügung.

### Installationsanforderungen {#installation-requirements}

Für den Connector ist Folgendes erforderlich:

* Java Runtime Environment 1.7 oder höher
* Über das Netzwerk verfügbare SharePoint-Webdienste
* SharePoint-Server-URL
* Benutzeranmeldeinformationen und -berechtigungen für CRX- und SharePoint-Repositorys
* [Unterstützte Plattformen](#supported-platforms)

Der SharePoint-Connector steht unter [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673) zum Download bereit.

### Unterstützte Plattformen {#supported-platforms}

Der Connector unterstützt Folgendes:

* AEM:

   * AEM 6.4, 6.3

* Microsoft SharePoint-Versionen:

   * Microsoft Office SharePoint Server (MOSS) 2010
   * Microsoft Office SharePoint Server (MOSS) 2013

* Wenn Sie Unterstützung für benutzerdefinierte Bereitstellungen des Connectors (OEM, besondere Anforderungen, benutzerdefinierte Authentifizierungsmethoden) benötigen, wenden Sie sich an das Adobe-Büro für Ihre Region.

>[!NOTE]
>
>Der Connector unterstützt nur Konfigurationen, die offiziell von Microsoft unterstützt werden. Weitere Informationen finden Sie in den Systemanforderungen für [MOSS 2010](https://technet.microsoft.com/de-de/library/cc262485(office.14).aspx) und [MOSS 2013](https://technet.microsoft.com/en-us/library/cc262485.aspx).

### Standardinstallation {#standard-installation}

Produktfeatures, Beispiele und Hotfixes werden über Software Distribution verteilt. Weitere Informationen finden Sie unter [Dokumentation zu Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de#software-distribution).


#### Integration mit AEM {#integrating-with-aem}

Installieren des Inhaltspakets für den Connector.

1. Öffnen Sie ein Adobe Support-Ticket, um das Connector-Feature Pack anzufordern.
1. Laden Sie das Paket herunter, sobald es verfügbar ist, und öffnen Sie dann Package Manager für Ihre AEM-Instanz.
1. Klicks **Installieren** von der Paketbeschreibungsseite aus.
1. Aus dem **Installationspaket** dialog, klicken Sie **Installieren**.

   **Hinweis:** Vergewissern Sie sich, dass Sie als Admin angemeldet sind.

1. Wenn das Paket installiert ist, klicken Sie auf **Schließen**.

## Konfigurieren des SharePoint-Connectors {#configuring-sharepoint-connector}

Konfigurieren Sie nach der Installation des SharePoint-Connectors die Anwendung und die SharePoint-Ebenen für den Connector.

Legen Sie die SharePoint-Server-URL fest, um die JCR-Kompatibilität Ihres SharePoint-Repositorys sicherzustellen. Sie können zusätzliche Parameter festlegen, um die Verbindung zum SharePoint-Server zu konfigurieren. Konfigurieren Sie außerdem die Authentifizierung mit dem SharePoint-Connector.

### Verbindung mit dem SharePoint-Server konfigurieren {#configuring-the-connection-with-the-sharepoint-server}

Führen Sie die folgenden Schritte aus, um die URL der SharePoint-Server-Instanz sowie erweiterte Optionen festzulegen:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach dem Bundle **Day JCR Connector for Microsoft Sharepoint**.
1. Bearbeiten der Konfigurationswerte.
1. Legen Sie die SharePoint-Server-URL als Wert von **Arbeitsbereiche**.
1. Klicken Sie auf **Speichern**.

![chlimage_1-62](assets/chlimage_1-62.png)

Parameter &quot;Workspaces&quot;und &quot;Default Workspace Name&quot;:

Standardmäßig stellt der Connector einen einzelnen JCR-Arbeitsbereich bereit. Der von diesem Arbeitsbereich angezeigte SharePoint-Server wird über den Konfigurationsparameter &quot;SharePoint Server URL&quot;festgelegt.

Der Connector kann auch für mehrere Workspaces konfiguriert werden. In diesem Fall ist jeder Arbeitsbereich mit der URL des entsprechenden SharePoint-Servers verknüpft, der über den Arbeitsbereich verfügbar gemacht wird. Um einen Arbeitsbereich hinzuzufügen, fügen Sie dem Parameter Arbeitsbereiche eine Arbeitsbereichsdefinition hinzu. Eine Workspace-Definition hat folgendes Format:
`<name>`= `<url>`. `<name>` ist der Name des JCR-Workspace. `<url>` ist die URL der SharePoint-Server-Instanz für diesen Workspace.

Führen Sie in AEM neben den obigen Konfigurationsschritten noch einen weiteren Schritt aus. Zulassungsliste des Bundles **com.day.cq.dam.cq-dam-jcr-connectors**.

Gehen Sie wie folgt vor, um in AEM Bundles der Liste hinzuzufügen:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: http://localhost:4502/system/console/configMgr.
1. Suchen Sie nach dem Dienst „Apache Sling Login Admin Whitelist“.
1. Aktivieren Sie das Kontrollkästchen zur **Umgehung der Whitelist**.
1. Fügen Sie `com.day.cq.dam.cq-dam-jcr-connectors` unter „Whitelist-Bundles (Standard)“ hinzu.
1. Klicken Sie auf „Speichern“.

![chlimage_1-82](assets/chlimage_1-82a.png)

>[!NOTE]
>
>Wenn Sie mehrere Workspaces konfigurieren, geben Sie im Parameter „Name des Standard-Workspace“ den Namen des Standard-Workspace an.

Weitere Informationen zu authentifizierungsbezogenen Parametern finden Sie unter [Authentifizierung](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### Überprüfen der Sharepoint-Einrichtung {#verifying-the-sharepoint-setup}

Nachdem Sie den Connector konfiguriert haben, überprüfen Sie Folgendes:

* Der SharePoint-Server wird ausgeführt und die Webdienste sind für die Connector-Instanz zugänglich.
* SharePoint-Benutzeranmeldeinformationen sind gültig und der Benutzer verfügt über die erforderlichen SharePoint-Berechtigungen
* Der Connector ist ordnungsgemäß installiert und konfiguriert

### Konfigurieren der DAM-Synchronisierung mit dem SharePoint-Server {#configuring-dam-sync-with-the-sharepoint-server}

Um die SharePoint Assets mit AEM zu synchronisieren, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach dem Dienst &quot;Default DAMAssetSynchronization&quot;.
1. Bearbeiten der Konfigurationswerte.
1. Legen Sie den Benutzernamen und das entsprechende Kennwort des Benutzers fest, der Zugriff auf die SharePoint-Site hat.
1. Klicken Sie auf „Speichern“.

Aktivieren Sie den standardmäßig deaktivierten DAM-Synchronisierungsdienst:

1. Navigieren Sie zu den Komponenten der OSGi-Web-Konsole: [http://localhost:4502/system/console/component](http://localhost:4502/system/console/components)
1. Suchen Sie nach &quot;com.day.cq.dam.jcrconnectors.impl.AssetSynchronizationService&quot;.
1. Klicken Sie auf Aktivieren.

Optional können Sie die Synchronisierungsverzögerung zwischen verschiedenen Synchronisierungszyklen konfigurieren:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Suchen Sie nach &quot;DAY CQ DAM JCR Connector Asset Synchronization Service&quot;.
1. Bearbeiten der Konfigurationswerte.
1. Legen Sie den Wert des Synchronisierungszeitraums fest (in Sekunden).
1. Klicken Sie auf „Speichern“.

### Authentifizierung konfigurieren {#configuring-authentication}

SharePoint beinhaltet die klassische und die anspruchsbasierte Authentifizierungsmethode, die jeweils folgende Authentifizierungsarten unterstützen:

* Einfach
* Formularbasiert

Insbesondere sind folgende Authentifizierungstypen verfügbar:

* Classic-Basic
* Classic-Forms-basiert
* Schadensanalyse
* Schadensmeldungen - Forms-basiert

Der JCR-Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013, Version 4.0, von AEM unterstützt eine anspruchsbasierte Authentifizierung (wie von Microsoft empfohlen), die in folgenden Modi ausgeführt wird:

* **Einfache/NTLM-Authentifizierung**: Der Connector versucht zunächst, eine Verbindung mithilfe der einfachen Authentifizierung herzustellen. Wenn nicht verfügbar, wird zur NTLM-basierten Authentifizierung gewechselt.
* **Formularbasierte Authentifizierung:** SharePoint validiert Benutzende auf der Grundlage von Anmeldeinformationen, die sie in ein Anmeldeformular (üblicherweise eine Webseite) eingeben. Das System gibt ein Token für authentifizierte Anfragen aus, das einen Schlüssel zum erneuten Einrichten der Identität für nachfolgende Anfragen enthält.

**Konfigurieren der Forms-basierten Authentifizierung**

Navigieren Sie zu: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

1. Klicken Sie auf OSGI > Konfiguration
1. Suchen Sie nach „Day JCR Connector for Microsoft Sharepoint“
1. Klicken Sie auf „Konfigurationswerte bearbeiten“
1. Legen Sie den Wert von „SharePoint-Verbindungs-Factory“ auf „com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory“ fest.
1. Klicken Sie auf **Speichern**.

**Konfigurieren der Standardauthentifizierung (Windows)**

1. [Deaktivieren Sie die Token-Authentifizierung](#disable-token-authentication).
1. Navigieren Sie zu: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
1. Klicken Sie auf OSGi > Konfiguration.
1. Suchen Sie nach **Day JCR Connector für Microsoft Sharepoint**.
1. Klicken Sie auf `Edit the configuration values`.
1. Legen Sie den Wert für die SharePoint-Verbindungs-Factory auf `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory` fest.
1. Klicken Sie auf **Speichern**.

Nur Benutzer, die sowohl in AEM als auch in SharePoint authentifiziert sind, können über den Connector auf den SharePoint-Inhalt zugreifen.

Sie können auch die Connector-Erweiterung für die Authentifizierung verwenden, um ein benutzerdefiniertes Authentifizierungsmodul zu erstellen, das beispielsweise den Zugriff AEM Benutzer bestimmten SharePoint-Benutzern zuordnet. Erstellen Sie AEM Benutzer, die SharePoint-Benutzern entsprechen (Benutzername und Kennwort sollten übereinstimmen), um SharePoint-Inhalte sehen zu können, die der Connector-Instanz zugeordnet sind.

Erstellen von Benutzenden in AEM

1. Melden Sie sich unter http://localhost:9502/ als Admin an.
1. Klicken Sie auf Tools.
1. Klicken Sie auf Sicherheit.
1. Klicken Sie auf Benutzer.
1. Klicken Sie auf **Benutzer erstellen**.
1. Geben Sie die Benutzer-ID (Benutzername einer Benutzerin oder eines Benutzers mit Zugriff auf SharePoint) an.
1. Geben Sie das entsprechende Passwort an.
1. Klicken Sie auf das grüne Häkchen, um die Benutzerin oder den Benutzer zu erstellen.

So fügen Sie den Benutzer zur Administratorgruppe hinzu:

1. Navigieren Sie zur Gruppenverwaltung.
1. Klicken Sie auf den Knoten „a“.
1. Klicken Sie auf „Administratoren“.
1. Geben Sie die weiter oben erstellte Benutzer-ID in das Textfeld vor der Schaltfläche **Durchsuchen** ein.
1. Klicken Sie auf das grüne Häkchen, um die Benutzerin oder den Benutzer der Administratorgruppe hinzuzufügen.

### Deaktivieren der Token-Authentifizierung {#disable-token-authentication}

1. Laden Sie das Paket `basic auth`. `zip` aus Software Distribution.

1. Schnellstart schließen
1. Öffnen Sie die Datei *\crx-quickstart\repository\repository.xml*.
1. Suchen Sie das Tag `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.`.
1. Fügen Sie das Tag `<param name="disableTokenAuth" value="true"/>` in das in Schritt 4 erwähnte Tag ein.
1. Speichern und schließen Sie die XML-Datei.
1. Starten Sie den Schnellstart neu und melden Sie sich mit Ihren Anmeldeinformationen an.

#### Unterstützen verschiedener Authentifizierungsmethoden der SharePoint Server-Instanz {#supporting-different-authentication-methods-of-the-sharepoint-server}

In der Standardversion unterstützt der Connector die **Windows**-IIS-Standardauthentifizierung sowie die formularbasierte Authentifizierung (Token-basiert). Die [anderen Authentifizierungsmethoden](https://technet.microsoft.com/de-de/library/cc262350.aspx#section2) können über den Erweiterbarkeitsmechanismus unterstützt werden.

Die folgenden Schritte bieten Richtlinien für die Erweiterung der Standardauthentifizierung, um verschiedene Authentifizierungsmethoden der SharePoint Server-Instanz zu unterstützen:

1. Implementieren Sie `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` für die Client-Seite Ihres spezifischen Authentifizierungsprozesses.
1. Installieren Sie die Implementierung `SharepointConnectionFactory` als Fragment-Bundle mit dem Fragment-Host `com.day.crx.spi.crx2sharepoint-bundle`.

   Passen Sie bei Verwendung von Maven die folgende Konfiguration von `maven-bundle-plugin` an die Anforderungen Ihres Projekts an:

   ```xml
              <plugin>
                  <groupId>org.apache.felix</groupId>
                  <artifactId>maven-bundle-plugin</artifactId>
                  <extensions>true</extensions>
                  <configuration>
                      <instructions>
                          <Export-Package />
                          <Private-Package>
                              <!-- your private package here -->
                          </Private-Package>
                          <Fragment-Host>
                              com.day.crx.spi.crx2sharepoint-bundle
                          </Fragment-Host>
                       </instructions>
                  </configuration>
              </plugin>
   ```

1. Registrieren Sie die Implementierung `SharepointConnectionFactory` in der Connector-Konfiguration. Klicken Sie im Konfigurationsfenster des Connectors auf **Erweiterte Optionen**. Geben Sie im Feld **SharePoint-Verbindungs-Factory** den Namen der Implementierung `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory` an.

1. Starten Sie den Connector neu.
