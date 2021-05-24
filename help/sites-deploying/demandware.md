---
title: Salesforce Commerce Cloud
seo-title: Salesforce Commerce Cloud/Demandware
description: Hier erfahren Sie, wie Sie eCommerce mit Salesforce Commerce Cloud/Demandware bereitstellen können.
seo-description: Hier erfahren Sie, wie Sie eCommerce mit Salesforce Commerce Cloud/Demandware bereitstellen können.
uuid: c0270632-bdd2-4dba-bbbe-312757ea20f4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 52cc3162-b638-410d-854a-383399e2effb
docset: aem65
pagetitle: Deploying eCommerce with Demandware
redirecttarget: https //github.com/adobe/commerce-salesforce
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 66%

---


# Salesforce Commerce Cloud{#salesforce-commerce-cloud}

Durch die Bereitstellung der erforderlichen eCommerce-Pakete erhalten Sie alle Funktionen des eCommerce-Frameworks sowie eine Referenzimplementierung der eCommerce-Funktionalität, die mit einer Salesforce-Commerce Cloud-/Demandware-Implementierung (einschließlich eines Demonstrationskatalogs) bereitgestellt wird.

## Für eCommerce mit Salesforce Commerce Cloud benötigte Pakete {#packages-needed-for-ecommerce-with-salesforce-commerce-cloud}

Zur Installation der eCommerce-Funktionalität benötigen Sie:

* AEM eCommerce-Framework:

   * Dies ist Teil einer standardmäßigen AEM-Installation. 

* AEM Demandware Commerce-Inhaltspaket

   * cq-6.4.0-featurepack-10262

>[!NOTE]
>
>Diese Integration unterstützt Salesforce Commerce Cloud- bzw. Demandware-Instanzen, die für die Verwendung der OCAPI-Version 17.6 oder höher konfiguriert wurden.

### Installation von eCommerce mit Salesforce Commerce Cloud {#installation-of-ecommerce-with-salesforce-commerce-cloud}

Um AEM mit einer Demandware Commerce-Integrationskonfiguration (mithilfe des Demonstrationskatalogs Geometrixx Outdoors) zu installieren, gehen Sie folgendermaßen vor:

1. [Installieren Sie AEM](/help/sites-deploying/deploy.md).
1. Installieren Sie das Inhaltspaket mit dem [Package Manager](/help/sites-administering/package-manager.md):
1. [Erstellen](/help/sites-authoring/page-authoring.md) Sie etwaige zusätzliche Seiten, die Sie in AEM benötigen.

>[!NOTE]
>
>Um die Pakete herunterzuladen, navigieren Sie zu [Package Share](/help/sites-administering/package-manager.md#package-share).

Die Serververbindung zwischen AEM und der Demandware-Sandbox muss konfiguriert werden. Die meisten Konfigurationen sind bereits so vorkonfiguriert, dass sie mit dem bereitgestellten SiteGenisis-Demoinhaltspaket unter Verwendung von Standardpfaden, Bibliotheken usw. funktionieren. Wenn der Connector mit anderen Websites und Bibliotheken verwendet wird, müssen Sie diese Konfiguration aktualisieren.

1. Navigieren Sie zu [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Klicken Sie auf **Demandware Client**.
1. Geben Sie die **IP-Adresse für den Instanzenendpunkt oder den Hostnamen** ein.

   ![chlimage_1-5](assets/chlimage_1-5.png)

1. Klicken Sie auf **Speichern**.
1. Klicken Sie auf **Demandware TransportHandler Plugin for WebDAV**.
1. Geben Sie den **WebDAV-Benutzer** und das entsprechende **Passwort** ein.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Klicken Sie auf **Speichern**.

#### Replikation {#replication}

Die Replikation sollte nach der Paketinstallation aktiviert sein. Sie können dies hier überprüfen: [https://localhost:4502/etc/replication/agents.author/demandware.html](https://localhost:4502/etc/replication/agents.author/demandware.html)

>[!NOTE]
>
>Der Replikationsagent wird standardmäßig auf Informationsprotokollebene konfiguriert. Wenn Sie weitere Informationen wünschen, können Sie die Protokollebene auf „debug“ ändern.

#### OAuth {#oauth}

Der OAuth-Client ist so konfiguriert, dass er mit einer Demandware-Sandbox-Instanz funktioniert. Für Testzwecke sind keine Änderungen erforderlich.

Für Staging- und Produktionssysteme müssen die OAuth-Clients mit der entsprechenden Client-ID und einem Passwort konfiguriert werden.

1. Navigieren Sie zu [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Klicken Sie auf **Demandware Access Token Provider**.

   ![chlimage_1-7](assets/chlimage_1-7.png)

1. Ändern Sie die Werte nach Bedarf und klicken Sie auf **Speichern**.

### Salesforce Commerce Cloud-Sandbox  {#salesforce-commerce-cloud-sandbox}

Die Demandware-Sandbox muss so konfiguriert werden, dass die neue Vorlagen-Engine „Velocity“ ausgeführt werden kann.

>[!NOTE]
>
>Der folgende Assistent ist nicht Teil des AEM Demandware Connectors. Er wird im Rahmen des Demo-Inhaltspakets bereitgestellt, um die rasche Einrichtung der SiteGenesis-Demoseiten zu ermöglichen.

1. Navigieren Sie zu [https://localhost:4502/etc/demandware/init.html](https://localhost:4502/etc/demandware/init.html).
1. Klicken Sie auf **Edit**.
1. Überprüfen Sie die Werte und klicken Sie auf **OK**.
1. Klicken Sie auf **Initialize**.
1. Gehen Sie zum Ordner WebDAV und suchen Sie nach veröffentlichten Vorlagendateien, z. B. unter `adobe01-tech-prtnr-na01-dw.demandware.net/on/demandware.servlet/webdav/Sites/Dynamic/SiteGenesis`.

   >[!NOTE]
   >
   >Die Erweiterung lautet `.vs`.

1. Suchen Sie auch nach exportierten JS- und CSS-Dateien, z. B. unter `adobe01-tech-prtnr-na01-dw.demandware.net/on/demandware.servlet/webdav/Sites/Libraries/SiteGenesisSharedLibrary`.

