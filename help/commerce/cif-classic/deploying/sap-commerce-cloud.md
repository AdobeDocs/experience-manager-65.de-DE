---
title: Bereitstellen von eCommerce mit SAP Commerce Cloud
description: Erfahren Sie, wie Sie Adobe Experience Manager eCommerce mit SAP Commerce Cloud bereitstellen.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: ecbd0097-c407-4581-bab2-4729a71df4a3
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 66%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>Diese Seite enthält Links zur Hybris-Website. Für bestimmte Seiten benötigen Sie ein Konto, um sich anzumelden.

## Bereitstellen von eCommerce mit SAP Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>Zur Veranschaulichung der folgenden Bereitstellung wird dieser Demo-Katalog verwendet:
>
>`Geometrixx Outdoors Site English (US)`

Bereitstellen des [erforderliche eCommerce-Pakete](#packages-needed-for-ecommerce-with-hybris) bietet die vollständige Funktionalität des eCommerce-Frameworks sowie eine Referenzimplementierung der eCommerce-Funktionalität, die mit einer hybris-Implementierung bereitgestellt wird (einschließlich eines Demonstrationskatalogs).

Dies ist in der englischen (US) Version (`/content/geometrixx-outdoors/en_US`) der Geometrixx Outdoors-Website erhältlich:

* [Produktinformationen](#productinformationwithcolorvariants) (mit Farbvarianten sofern zutreffend)

* [Übersicht über den Warenkorbinhalt ](#shoppingcartcontentoverview)
* [Kundenregistrierung](#customersignup) und [Kundenanmeldung](#customersignin) 

* [Zugriff auf die Hybris-Verwaltungskonsole](#accesstothehybrismanagementconsole)

### Technische Anforderungen – Hybris-Server {#technical-requirements-hybris-server}

Die Hybris-Erweiterung des eCommerce-Integrations-Frameworks wurde aktualisiert und unterstützt jetzt Hybris 5 (standardmäßig), während die Rückwärtskompatibilität mit [Hybris 4](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#developing-for-hybris) ebenfalls gewährleistet ist.

>[!NOTE]
>
>* Unterstützt die Versionen 18.11 und höher.
>* Sie benötigen Java™ 7, um die [hybris 5-Server.](https://www.sap.com/products/crm.html)
* Das Hybris-Add-on [Telco Accelerator](https://www.sap.com/products/crm.html) wird von der AEM-Erweiterung nicht unterstützt.
>

### Für eCommerce mit Hybris benötigte Pakete {#packages-needed-for-ecommerce-with-hybris}

Zur Installation der eCommerce-Funktion benötigen Sie:

* Ihren Hybris-Server
* AEM eCommerce-Framework:

   * Dies ist Teil einer Standardinstallation von AEM

* AEM Geometrixx-all-Paket:

   * `cq-geometrixx-all-pkg`

* AEM Hybris-Inhaltspakete:

   * `cq-hybris-content-6.3.2`
   * Hybris-spezifische API-Implementierung
   * `cq-geometrixx-hybris-content-6.3.2`
   * Eine Referenzimplementierung zur Veranschaulichung der Funktionsweise von Hybris (`geometrixx-outdoors/en_US`)

### Installation von eCommerce mit Hybris {#installation-of-ecommerce-with-hybris}

Um eine vollständige Konfiguration zu installieren (mithilfe des Demonstrationskatalogs, Geometrixx Outdoors), gehen Sie folgendermaßen vor:

1. [Installieren Sie AEM](/help/sites-deploying/deploy.md).
1. Installieren Sie das Geometrixx-all-Paket.

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installieren Sie die Demonstrations-Inhaltspakete mithilfe des [Package Manager](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Laden Sie Ihren Hybris-Server herunter und erstellen Sie ihn](#download-and-build-your-hybris-server).
1. Erstellen Sie Ihren Katalog in Ihrer eCommerce-Engine:

   1. [Einrichten des Geometrixx Outdoor Store](#setup-the-geometrixx-outdoors-store).

1. [Erstellen](/help/sites-authoring/qg-page-authoring.md) Sie alle zusätzlichen Seiten, die Sie in AEM benötigen.

>[!CAUTION]
>
Die Verwendung des Hybris-Servers erfordert eine separate Hybris-Lizenz.

>[!NOTE]
>
Für Entwickler [API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) kann auch heruntergeladen werden.

### Herunterladen und Erstellen Ihres Hybris-Servers {#download-and-build-your-hybris-server}

Die Schritte in diesem Verfahren laden den hybris-Server herunter und erstellen ihn. Außerdem werden die anfänglichen Konfigurationen vorgenommen, die für die Verbindungen zwischen hybris und cq erforderlich sind. Die Erweiterung kann dann mit den Standardeinstellungen verwendet werden.

>[!CAUTION]
>
Hybris-Versionen vor 5.5.1 werden nicht unterstützt.

>[!NOTE]
>
Um dies abzuschließen, benötigen Sie [Groovy](https://groovy-lang.org/) auf Ihrem System installiert.

1. Laden Sie die **Hybris Commerce Suite**-Distribution von der Hybris-Download-Website herunter.

   >[!CAUTION]
   >
   Sie benötigen ein Konto (von hybris), um darauf zugreifen zu können.

1. Entpacken Sie die Distributionsdatei am erforderlichen Speicherort (&lt;hybris-root-directory>).
1. Führen Sie an der Befehlszeile Folgendes aus:

   ```shell
   cd <hybris-root-directory>/bin/platform
   . ./setantenv.sh
   ant clean all
   cd ../..
   ```

   >[!NOTE]
   >
   Beim Ausführen:
   >
   `ant clean all`
   >
   Drücken Sie bei Bedarf `Return`.

1. Laden Sie die folgenden Dateien in den Stammordner Ihrer dekomprimierten Hybris-Distributionsdatei herunter:

   ```
       <hybris-root-directory>
   ```


[Datei abrufen](/help/sites-deploying/assets/setup.groovy)

   >[!NOTE]
   >
   Verwenden Sie für hybris 5.6.0 und höher die folgende setup.groovy.

   5.6.0 und höher

[Datei abrufen](/help/sites-deploying/assets/setup-1.groovy)

1. Geben Sie in der Befehlszeile Folgendes ein, um:

   * die Konfiguration des Hybris-Servers zu aktualisieren (gemäß der Anforderung der Erweiterung); 
   * den Hybris-Server mit der geänderten Konfiguration einzurichten; 
   * den Server zu starten.

   ```shell
   groovy setup.groovy
   cd bin/platform
   ant clean all
   sh hybrisserver.sh
   ```

   >[!NOTE]
   >
   Je nach System kann es mehrere Minuten dauern, bis einige dieser Schritte abgeschlossen sind.

1. Navigieren Sie in Ihrem Browser zu **Hybris Administration Console** unter:

   [http://localhost:9002](http://localhost:9002)

1. Klicks **Initialisieren** und bestätigen Sie dann die Initialisierungsaktion (da vorhandene Daten gelöscht werden).

   Der Fortschritt wird in der Konsole mit `FINISHED` Angabe der Fertigstellung.

   >[!NOTE]
   >
   Abhängig von Ihrem System kann dies mehrere Minuten dauern.

### Einrichten des Geometrixx Outdoors-Stores {#setup-the-geometrixx-outdoors-store}

Mit diesem Verfahren wird der Demonstrationsspeicher Geometrixx Online hochgeladen und konfiguriert.

1. Starten Sie Ihre Hybris-Instanz. Führen Sie an der Befehlszeile Folgendes aus:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. Navigieren Sie in Ihrem Browser zur **Hybris-Verwaltungskonsole** unter:

   [https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Verwenden Sie diese Anmeldedaten:
   * Benutzername: admin
   * Kennwort: nimda

1. Erweitern Sie in der Sidebar-Navigation **System** und **Tools**. Wählen Sie anschließend **Importieren** aus, um das Fenster **Assistent: CSV-Import** zu öffnen.
1. Verwenden Sie auf der Registerkarte **Konfiguration** die Option **Hochladen**, um die folgende **Importdatei** hochzuladen:

[Datei abrufen](/help/sites-deploying/assets/geometrixx-outdoors-export.csv)

1. Definieren Sie **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Öffnen Sie die Registerkarte **Ressourcen**.
1. Verwenden Sie die Option **Hochladen** zum Hochladen der folgenden **Medien-ZIP-Datei**:

[Datei abrufen](/help/sites-deploying/assets/geometrixx-outdoors-images.zip)

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Die **Ergebnis** zeigt alle Protokolleinträge an.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Wählen Sie in der Sidebar **System**, dann **Tools** und schließlich **Import** aus.

1. **Laden** Sie die folgende **Importdatei** hoch:

[Datei abrufen](/help/sites-deploying/assets/base-store.csv)

   Verwenden Sie für hybris 5.7 Folgendes:

[Datei abrufen](/help/sites-deploying/assets/base-store-5_7.csv)

1. Definieren Sie **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Die **Ergebnis** zeigt alle Protokolleinträge an.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Im Produkt-Cockpit können Sie sich jetzt die importierten Kataloge und Produkte ansehen:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
