---
title: Bereitstellen von eCommerce mit SAP Commerce Cloud
description: Erfahren Sie, wie Sie Adobe Experience Manager eCommerce mit SAP Commerce Cloud bereitstellen.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: ecbd0097-c407-4581-bab2-4729a71df4a3
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 100%

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

Die Bereitstellung der [notwendigen eCommerce-Pakete](#packages-needed-for-ecommerce-with-hybris) bietet die volle Funktionalität des E-Commerce-Frameworks, zusammen mit einer Referenzimplementierung der E-Commerce-Funktionalität, wie sie in einer Hybris-Implementierung bereitgestellt wird (einschließlich eines Demonstrationskatalogs)

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
>* Sie benötigen Java™ 7, um den [Hybris 5-Server](https://www.sap.com/germany/products/crm.html) auszuführen.
>* Das Hybris-Add-on [Telco Accelerator](https://www.sap.com/germany/products/crm.html) wird von der AEM-Erweiterung nicht unterstützt.
>

### Für eCommerce mit Hybris benötigte Pakete {#packages-needed-for-ecommerce-with-hybris}

Zum Installieren der E-Commerce-Funktionalität benötigen Sie Folgendes:

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

Zur Installation einer vollständigen Konfiguration (unter Verwendung des Demonstrationskatalogs Geometrixx Outdoors) sind folgende grundlegende Schritte erforderlich:

1. [Installieren Sie AEM](/help/sites-deploying/deploy.md).
1. Installieren Sie das Geometrixx-all-Paket.

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installieren Sie die Demonstrations-Inhaltspakete mithilfe von [Package Manager](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Laden Sie Ihren Hybris-Server herunter und erstellen Sie ihn](#download-and-build-your-hybris-server).
1. Erstellen Sie Ihren Katalog in Ihrer eCommerce-Engine:

   1. [Richten Sie den Geometrixx Outdoor-Store ein](#setup-the-geometrixx-outdoors-store).

1. [Erstellen](/help/sites-authoring/qg-page-authoring.md) Sie alle zusätzlichen Seiten, die Sie in AEM benötigen.

>[!CAUTION]
>
>Die Verwendung des Hybris-Servers erfordert eine separate Hybris-Lizenz.

>[!NOTE]
>
>Für Entwickelnde ist auch eine [API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) zum Herunterladen verfügbar.

### Herunterladen und Erstellen Ihres Hybris-Servers {#download-and-build-your-hybris-server}

Mit den Schritten in diesem Verfahren wird der Hybris-Server heruntergeladen und erstellt. Außerdem werden die ersten Konfigurationen vorgenommen, die für die Verbindungen zwischen Hybris und CQ erforderlich sind. Die Erweiterung kann dann mit den Standardeinstellungen verwendet werden.

>[!CAUTION]
>
>Hybris-Versionen vor 5.5.1 werden nicht unterstützt.

>[!NOTE]
>
>Um dies zu vervollständigen, müssen Sie [Groovy](https://groovy-lang.org/) auf Ihrem System installieren.

1. Laden Sie die **Hybris Commerce Suite**-Distribution von der Hybris-Download-Website herunter.

   >[!CAUTION]
   >
   >Sie benötigen ein Konto (von Hybris), um darauf zugreifen zu können.

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
   >Beim Ausführen:
   >
   >`ant clean all`
   >
   >Drücken Sie bei Bedarf `Return`.

1. Laden Sie die folgenden Dateien in den Stammordner Ihrer dekomprimierten Hybris-Distributionsdatei herunter:

   ```
       <hybris-root-directory>
   ```


[Datei abrufen](/help/sites-deploying/assets/setup.groovy)

   >[!NOTE]
   >
   >Verwenden Sie für Hybris 5.6.0 und höher setup.groovy.

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
   >Je nach System kann es mehrere Minuten dauern, bis einige dieser Schritte abgeschlossen sind.

1. Navigieren Sie in Ihrem Browser zu **Hybris Administration Console** unter:

   [http://localhost:9002](http://localhost:9002)

1. Klicken Sie auf **Intialisieren** und bestätigen Sie dann die Initialisierung (da dadurch vorhandene Daten gelöscht werden).

   Der Fortschritt ist in der Konsole zu sehen und nach Fertigstellung wird `FINISHED` angezeigt.

   >[!NOTE]
   >
   >Je nach Ihrem System kann dies mehrere Minuten dauern.

### Einrichten des Geometrixx Outdoors-Store {#setup-the-geometrixx-outdoors-store}

Mit diesem Verfahren wird der Store „Geometrixx Online“ zur Veranschaulichung hochgeladen und konfiguriert.

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

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Ergebnis** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Wählen Sie in der Sidebar **System**, dann **Tools** und schließlich **Import** aus.

1. **Laden** Sie die folgende **Importdatei** hoch:

[Datei abrufen](/help/sites-deploying/assets/base-store.csv)

   Verwenden Sie für Hybris 5.7 Folgendes:

[Datei abrufen](/help/sites-deploying/assets/base-store-5_7.csv)

1. Definieren Sie **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Ergebnis** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Im Produkt-Cockpit können Sie sich jetzt die importierten Kataloge und Produkte ansehen:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
