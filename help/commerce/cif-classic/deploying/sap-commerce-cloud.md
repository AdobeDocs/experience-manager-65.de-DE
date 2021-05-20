---
title: SAP Commerce Cloud
seo-title: SAP-Commerce Cloud
description: Hier erfahren Sie, wie Sie eCommerce mit SAP Commerce Cloud bereitstellen können.
seo-description: Hier erfahren Sie, wie Sie eCommerce mit SAP Commerce Cloud bereitstellen können.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 85%

---

# SAP-Commerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>Diese Seite enthält Links zur hybris-Website. Für bestimmte Seiten benötigen Sie ein Konto, mit dem Sie sich anmelden können.

## Bereitstellen von eCommerce mit SAP-Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>Zur Veranschaulichung der folgenden Bereitstellung wird dieser Demonstrationskatalog verwendet:
>
>`Geometrixx Outdoors Site English (US)`

Durch die Implementierung der [erforderlichen eCommerce-Pakete](#packages-needed-for-ecommerce-with-hybris) wird der volle Funktionsumfang des eCommerce-Frameworks zusammen mit einer Referenzimplementierung der eCommerce-Funktionen bereitgestellt, die im Rahmen einer Demandware Commerce-Implementierung (einschließlich Demo-Katalog) verfügbar sind.

Dies ist unter der englischen (US-) Niederlassung ( `/content/geometrixx-outdoors/en_US`) der Geometrixx Outdoors-Website verfügbar:

* [Produktinformationen](#productinformationwithcolorvariants) (mit Farbvarianten sofern zutreffend) 

* [Übersicht über den Warenkorbinhalt ](#shoppingcartcontentoverview)
* [Kundenregistrierung](#customersignup) und [Kundenanmeldung](#customersignin) 

* [Zugriff auf die hybris-Verwaltungskonsole ](#accesstothehybrismanagementconsole)

### Technische Anforderungen – hybris-Server {#technical-requirements-hybris-server}

Die hybris-Erweiterung des eCommerce Integration Framework wurde aktualisiert, um Hybris 5 (standardmäßig) zu unterstützen und gleichzeitig die Abwärtskompatibilität mit [Hybris 4](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#developing-for-hybris) zu gewährleisten.

>[!NOTE]
>
>* Unterstützt die Versionen 18.11 und höher.
>* Sie benötigen Java 7 für den [hybris 5 Server](https://www.hybris.com/en/architecture-technology).
>* Das hybris-Add-on, der [Telco Accelerator](https://www.hybris.com/en/products/telecommunication), wird nicht von der AEM-Erweiterung unterstützt.

>



### Benötigte Pakete für eCommerce mit hybris {#packages-needed-for-ecommerce-with-hybris}

Zur Installation der eCommerce-Funktionalität benötigen Sie:

* Ihr hybris-Server
* AEM eCommerce-Framework:

   * Dies ist Teil einer standardmäßigen AEM-Installation. 

* AEM Geometrixx-all-Paket:

   * `cq-geometrixx-all-pkg`

* AEM hybris-Inhaltspakete:

   * `cq-hybris-content-6.3.2`
   * hybris-spezifische API-Implementierung
   * `cq-geometrixx-hybris-content-6.3.2`
   * eine Referenzimplementierung zur Veranschaulichung der Verwendung von hybris ( `geometrixx-outdoors/en_US`)

### Installation von eCommerce mit hybris {#installation-of-ecommerce-with-hybris}

Um eine vollständige Konfiguration (mithilfe des Demonstrationskatalogs Geometrixx Outdoors) zu installieren, gehen Sie folgendermaßen vor:

1. [Installieren Sie AEM](/help/sites-deploying/deploy.md).
1. Installieren Sie das Paket Geometrixx-all

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installieren Sie die Demonstrations-Inhaltspakete mithilfe des [Paketmanagers](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Laden Sie den hybris-Server herunter und richten Sie ihn ein](#download-and-build-your-hybris-server).
1. Erstellen Sie Ihren Katalog in Ihrer eCommerce-Engine:

   1. [Richten Sie den Geometrixx Outdoor Store ein](#setup-the-geometrixx-outdoors-store).

1. [Erstellen](/help/sites-authoring/qg-page-authoring.md) Sie etwaige zusätzliche Seiten, die Sie in AEM benötigen.

>[!CAUTION]
>
>Die Verwendung des hybris-Servers erfordert eine separate hybris-Lizenz.

>[!NOTE]
>
>Für Entwickler ist auch eine [API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) zum Herunterladen verfügbar. 

### hybris-Server herunterladen und einrichten {#download-and-build-your-hybris-server}

Mit den folgenden Schritten können Sie den hybris-Server herunterladen und einrichten. Dadurch werden auch die Erstkonfigurationen erstellt, die für die Verbindungen zwischen hybris und CQ erforderlich sind. Die Erweiterung kann danach mit den Standardeinstellungen verwendet werden.

>[!CAUTION]
>
>Hybris-Versionen vor 5.5.1 werden nicht unterstützt.

>[!NOTE]
>
>Dazu muss [Groovy](https://groovy-lang.org/) auf Ihrem System installiert sein.

1. Laden Sie die **hybris Commerce Suite** von der hybris-Download-Website herunter.

   >[!CAUTION]
   >
   >Dazu benötigen Sie ein hybris-Konto.

1. Dekomprimieren Sie die Distributionsdatei am entsprechenden Speicherort (&lt;hybris-root-directory>).
1. Geben Sie in der Befehlszeile Folgendes ein:

   ```shell
   cd <hybris-root-directory>/bin/platform
   . ./setantenv.sh
   ant clean all
   cd ../..
   ```

   >[!NOTE]
   >
   >Während der Ausführung:
   >
   >`ant clean all`
   >
   >Drücken Sie bei Bedarf `Return`.

1. Laden Sie die folgenden Dateien in den Stammordner Ihrer extrahierten hybris-Distribution herunter,

   ```
       <hybris-root-directory>
   ```


[Datei laden](/help/sites-deploying/assets/setup.groovy)

   >[!NOTE]
   >
   >Verwenden Sie für hybris 5.6.0 und höher folgende setup.groovy.

   5.6.0 und höher

[Datei laden](/help/sites-deploying/assets/setup-1.groovy)

1. Geben Sie in der Befehlszeile Folgendes ein, um:

   * die Konfiguration des hybris-Servers zu aktualisieren (gemäß der Anforderung der Erweiterung); 
   * den hybris-Server mit der geänderten Konfiguration einzurichten; 
   * den Server zu starten.

   ```shell
   groovy setup.groovy
   cd bin/platform
   ant clean all
   sh hybrisserver.sh
   ```

   >[!NOTE]
   >
   >Abhängig von Ihrem System können diese Schritte einige Minuten dauern.

1. Navigieren Sie im Browser zu **hybris Administration Console** unter:

   [http://localhost:9002](http://localhost:9002)

1. Klicken Sie auf **Initialize** und bestätigen Sie dann die Initialisierung (da dadurch vorhandene Daten gelöscht werden).

   Der Fortschritt ist in der Konsole zu sehen und nach Fertigstellung wird `FINISHED` angezeigt.

   >[!NOTE]
   >
   >Abhängig von Ihrem System kann dies einige Minuten dauern.

### Einrichten des Geometrixx Outdoors Store  {#setup-the-geometrixx-outdoors-store}

Mit diesem Verfahren wird das Demonstrationsgeschäft Geometrixx Online hochgeladen und konfiguriert.

1. Starten Sie Ihre hybris-Instanz. Geben Sie in der Befehlszeile Folgendes ein:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. Navigieren Sie im Browser zur **hybris-Verwaltungskonsole** unter:

   [https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Verwenden Sie diese Anmeldedaten:
   * Benutzername: admin
   * password: nimda

1. Erweitern Sie in der Seitenleistennavigation **System** und **Tools**. Wählen Sie dann **Import** aus, um das Fenster **Wizard: CSV Import** zu öffnen.
1. Wählen Sie auf der Registerkarte **Configuration** die Option **Upload** für die folgende **Importdatei**:

[Datei laden](/help/sites-deploying/assets/geometrixx-outdoors-export.csv)

1. Definieren Sie die **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Öffnen Sie die Registerkarte **Resources**.
1. **Laden** Sie die folgende **Media-Zip**-Datei hoch:

[Datei laden](/help/sites-deploying/assets/geometrixx-outdoors-images.zip)

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Result** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Wählen Sie in der Sidebar **System**, dann **Tools** und schließlich **Import**. 

1. **Laden** Sie die folgende **Importdatei** hoch:

[Datei laden](/help/sites-deploying/assets/base-store.csv)

   Verwenden Sie für hybris 5.7 folgende Datei:

[Datei laden](/help/sites-deploying/assets/base-store-5_7.csv)

1. Definieren Sie die **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Result** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Im Produkt-Cockpit können Sie sich jetzt die importierten Kataloge und Produkte ansehen:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
