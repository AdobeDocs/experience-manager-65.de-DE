---
title: '"Schulung: Formulardatenmodell erstellen "'
seo-title: Formulardatenmodell erstellen - Schulung
description: Formulardatenmodell erstellen
seo-description: Formulardatenmodell erstellen
uuid: b9d2bb1b-90f0-44f4-b1e3-0603cdf5f5b8
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 12e6c325-ace0-4a57-8ed4-6f7ceee23099
docset: aem65
translation-type: tm+mt
source-git-commit: 78768e6eab65f452421d8809384500c6eab6b97f
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 66%

---


# Schulung: Formulardatenmodell erstellen {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](../../forms/using/create-your-first-adaptive-form.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

## Über die Schulung {#about-the-tutorial}

AEM [!DNL Forms] data integration module allows you to create a form data model from disparate backend data sources such as AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. Sie können Datenmodellobjekte und -Dienste in einem Formulardatenmodell konfigurieren und einem adaptiven Formular zuordnen. Adaptive Formularfelder sind an Datenmodellobjekteigenschaften gebunden. Mit den Diensten können Sie das adaptive Formular vorab befüllen und gesendete Formulardaten zurück an das Datenmodellobjekt schreiben.

Weitere Informationen zum Formulardatenmodell und zur Formulardatenintegration finden Sie unter [Datenintegration für AEM Forms](../../forms/using/data-integration.md).

Diese Schulung führt Sie durch die Schritte zum Vorbereiten, Erstellen, Konfigurieren und Zuordnen eines Formulardatenmodells mit einem adaptiven Formular. Am Ende dieser Schulung können Sie Folgendes:

* [Konfigurieren der MySQL-Datenbank als Datenquelle](#config-database)
* [Erstellen eines Formulardatenmodells mit der MySQL-Datenbank](#create-fdm)
* [Konfigurieren eines Formulardatenmodells](#config-fdm)
* [Testen eines Formulardatenmodells](#test-fdm)

Das Formulardatenmodell sieht etwa wie folgt aus:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Configured data sources **B.** Data source schemas **C.** Available services **D.** Data model objects **E.** Configured services

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* [!DNL MySQL] Datenbank mit Musterdaten, wie im Abschnitt &quot;Voraussetzungen&quot;unter [Erstellen des ersten adaptiven Formulars beschrieben.](../../forms/using/create-your-first-adaptive-form.md)
* OSGi bundle for [!DNL MySQL] JDBC driver as explained in [Bundling the JDBC Database Driver](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* Adaptive form as explained in the first tutorial [Create an adaptive form](/help/forms/using/create-adaptive-form.md)

## Schritt 1: Konfigurieren der MySQL-Datenbank als Datenquelle {#config-database}

Sie können verschiedene Arten von Datenquellen konfigurieren, um ein Formulardatenmodell zu erstellen. Für diese Schulung werden wir die MySQL-Datenbank, die Sie konfiguriert und mit Beispieldaten befüllt haben, konfigurieren. Informationen zu anderen unterstützten Datenquellen und deren Konfiguration finden Sie unter [AEM Forms-Datenintegration](../../forms/using/data-integration.md).

Do the following to configure your [!DNL MySQL] database:

1. Install JDBC driver for [!DNL MySQL] database as an OSGi bundle:

   1. Log in to AEM [!DNL Forms] Author Instance as an administrator and go to AEM web console bundles. The default URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Tap **[!UICONTROL Install/Update]**. Ein Dialogfeld [!UICONTROL Pakete hochladen/installieren] wird angezeigt.

   1. Tap **[!UICONTROL Choose File]** to browse and select the [!DNL MySQL] JDBC driver OSGi bundle. Select **[!UICONTROL Start Bundle]** and **[!UICONTROL Refresh Packages]**, and tap **[!UICONTROL Install or Update]**. Ensure that the [!DNL Oracle Corporation's] JDBC Driver for [!DNL MySQL] is active. Der Treiber wird installiert.

1. Configure [!DNL MySQL] database as a data source:

   1. Go to AEM web console at [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Connection Pooled DataSource**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
   1. Geben Sie im Konfigurationsdialog die folgenden Details an:

      * **Datenquellenname:** Sie können einen beliebigen Namen angeben, beispielsweise **WeRetailMySQL**.
      * **Name der DataSource-Diensteigenschaft**: Geben Sie den Namen der Diensteigenschaft an, die den DataSource-Namen enthält. Er wird beim Registrieren der Datenquelleninstanz als OSGi-Dienst angegeben. Zum Beispiel: **datasource.name**.
      * **JDBC-Treiberklasse**: Geben Sie den Java-Klassennamen des JDBC-Treibers an. For [!DNL MySQL] database, specify **com.mysql.jdbc.Driver**.
      * **JDBC-Verbindungs-URI**: Geben Sie die Verbindungs-URL der Datenbank an. Für [!DNL MySQL] Datenbanken, die auf Port 3306 ausgeführt werden, und für Schema, das über Ethernet verfügt, lautet die URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Benutzername:** Benutzername der Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Kennwort:** Kennwort für die Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Test auf Borge:** Aktivieren Sie die Option **[!UICONTROL Test on Borrow]** .
      * **Test on Return:** Aktivieren Sie die Option **[!UICONTROL Test on Return.]**
      * **Validation Query:** Geben Sie eine SQL SELECT-Abfrage ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Beispiel: **Wählen Sie * aus Kundendaten**.
      * **Transaktions-Isolierung**: Setzen Sie den Wert auf **READ_COMMITTED**.

         Leave other properties with default [values](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) and tap **[!UICONTROL Save]**.

         Eine Konfiguration ähnlich der folgenden wird erstellt.

         ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Schritt 2: Erstellen eines Formulardatenmodells {#create-fdm}

AEM [!DNL Forms] provides an intuitive user interface to [create a form data model](data-integration.md) from configured data sources. Sie können mehrere Datenquellen in einem Formulardatenmodell verwenden. For our use case, we will use the configured [!DNL MySQL] data source.

Gehen Sie folgendermaßen vor, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare]** > **[!UICONTROL Datenintegration]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Formulardatenmodell]**.
1. Geben Sie im Dialogfeld „Formulardatenmodell erstellen“ einen **Namen** für das Formulardatenmodell ein. Zum Beispiel **customer-shipping-billing-details**. Tippen Sie auf **[!UICONTROL Weiter]**.
1. Im Bildschirm „Datenquelle auswählen“ werden alle konfigurierten Datenquellen angezeigt. Select **WeRetailMySQL** data source and tap **[!UICONTROL Create]**.

   ![data-source-selection](assets/data-source-selection.png)

The **customer-shipping-billing-details** form data model is created.

## Schritt 3: Konfigurieren eines Formulardatenmodells {#config-fdm}

Zum Konfigurieren eines Formulardatenmodells gehört Folgendes:

* Hinzufügen von Datenmodellobjekten und Diensten
* Konfigurieren von Lese- und Schreibdiensten für Datenmodellobjekte

Gehen Sie folgendermaßen vor, um das Formulardatenmodell zu konfigurieren:

1. On AEM author instance, navigate to **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**. The default URL is [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. The **customer-shipping-billing-details** form data model you created earlier is listed here. Öffnen Sie es im Bearbeitungsmodus.

   Die ausgewählte Datenquelle **WeRetailMySQL** wird im Formulardatenmodell konfiguriert.

   ![default-fdm](assets/default-fdm.png)

1. Erweitern Sie den WeRailMySQL-Datenquellenbaum. Select the following data model objects and services from **weretail** > **customerdetails** schema to form data model:

   * **Datenmodellobjekte**:

      * id
      * name
      * shippingAddress
      * city
      * state
      * zipcode
   * **Dienste:**

      * get
      * Aktualisieren

   Tippen Sie auf **Ausgewählte hinzufügen**, um dem Formulardatenmodell ausgewählte Datenmodellobjekte und Dienste hinzuzufügen.

   ![WeRetail Schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >Die standardmäßigen get-, update- und insert-Dienste für JDBC-Datenquellen werden standardmäßig mit dem Formulardatenmodell bereitgestellt.

1. Konfigurieren Sie Lese- und Schreibdienste für Datenmodellobjekte.

   1. Wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**.
   1. Wählen Sie aus dem Dropdown-Menü „Lesedienst“ **[!UICONTROL get.]** Das Argument **id**, das der Primärschlüssel im Datenmodellobjekt des „customerdetails“ ist, wird automatisch hinzugefügt. Tap ![aem_6_3_edit](assets/aem_6_3_edit.png) and configure the argument as follows.

      ![read-default](assets/read-default.png)

   1. Wählen Sie ebenfalls **[!UICONTROL update]** als Schreibdienst. Das Objekt **customerdetails** wird automatisch als Argument hinzugefügt. Das Argument ist wie folgt konfiguriert.

      ![write-default](assets/write-default.png)

      Fügen Sie das Argument **id** hinzu und konfigurieren Sie es wie folgt.

      ![id-arg](assets/id-arg.png)

   1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Eigenschaften des Datenmodellobjekts zu speichern. Then, tap **[!UICONTROL Save]** to save the form data model.

      Die Dienste **[!UICONTROL get]** und **[!UICONTROL update]** werden als Standarddienste für das Datenmodellobjekt hinzugefügt.

      ![data-model-object](assets/data-model-object.png)

1. Wechseln Sie zur Registerkarte **[!UICONTROL Dienste]** und konfigurieren Sie die Dienste **[!UICONTROL get]** und **[!UICONTROL update]**.

   1. Select the **[!UICONTROL get]** service and tap **[!UICONTROL Edit Properties]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.
   1. Geben Sie im Dialogfeld „Eigenschaften bearbeiten“ Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse abrufen.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         This service retrieves shipping address and other customer details from [!DNL MySQL] database

      * **Ausgabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail Schema

      * **Array zurückgeben**: Deaktivieren Sie die Option **Array zurückgeben**.
      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID**.

      Tippen Sie auf **[!UICONTROL Fertig]**. Der Dienst zum Abrufen von Kundendaten aus der MySQL-Datenbank ist konfiguriert.

      ![shiiping-address-retrieve](assets/shiiping-address-retrieval.png)

   1. Select the **[!UICONTROL update]** service and tap **[!UICONTROL Edit Properties]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.

   1. Specify the following in the [!UICONTROL Edit Properties] dialog:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse aktualisieren.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         This service updates shipping address and related fields in MySQL database

      * **Eingabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail Schema

      * **Ausgabetyp**: Wählen Sie **BOOLEAN**.

      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID** und **customerdetails**.
      Tippen Sie auf **[!UICONTROL Fertig]**. The **[!UICONTROL update]** service to update customer details in the [!DNL MySQL] database is configured.

      ![shiiping-address-update](assets/shiiping-address-update.png)



Das Datenmodellobjekt und die Dienste im Formulardatenmodell sind konfiguriert. Sie können nun das Formulardatenmodell testen.

## Schritt 4: Testen eines Formulardatenmodells {#test-fdm}

Sie können das Datenmodellobjekt und die Datendienste testen, um sicherzustellen, dass das Formulardatenmodell ordnungsgemäß konfiguriert ist.

Führen Sie folgende Schritte aus, um den Test durchzuführen:

1. Wechseln Sie auf die Registerkarte **[!UICONTROL Modell]**, wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **[!UICONTROL Modellobjekt testen]**.
1. Wählen Sie im Fenster [!UICONTROL Modell/Dienst testen] **[!UICONTROL Modellobjekt lesen]** aus der Dropdown-Liste **[!UICONTROL Modell/Dienst auswählen]** auswählen.
1. In the **customerdetails** section, specify a value for the **id** argument that exists in the configured [!DNL MySQL] database and tap **[!UICONTROL Test]**.

   Die Kundendetails, die der angegebenen ID zugeordnet sind, werden abgerufen und im Abschnitt **[!UICONTROL Ausgabe]** angezeigt, wie unten gezeigt.

   ![test-read-model](assets/test-read-model.png)

1. In ähnlicher Weise können Sie das Schreibmodellobjekt und die Dienste testen.

   Im folgenden Beispiel aktualisiert der Aktualisierungsdienst die Adressdetails für die ID 7102715 in der Datenbank erfolgreich.

   ![test-write-model](assets/test-write-model.png)

   Wenn Sie nun den Lesemodelldienst für die ID 7107215 erneut testen, werden die aktualisierten Kundendetails abgerufen und angezeigt (siehe unten).

   ![read-updated](assets/read-updated.png)
