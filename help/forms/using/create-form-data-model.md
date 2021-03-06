---
title: '"Schulung: Formulardatenmodell erstellen "'
seo-title: Create Form Data Model Tutorial
description: Erstellen des Formulardatenmodells
seo-description: Create form data model
uuid: b9d2bb1b-90f0-44f4-b1e3-0603cdf5f5b8
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 12e6c325-ace0-4a57-8ed4-6f7ceee23099
docset: aem65
exl-id: 40bc5af6-9023-437e-95b0-f85d3df7d8aa
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1421'
ht-degree: 100%

---

# Schulung: Formulardatenmodell erstellen {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](../../forms/using/create-your-first-adaptive-form.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

## Über die Schulung {#about-the-tutorial}

Mit dem AEM [!DNL Forms]-Datenintegrationsmodul können Sie ein Formulardatenmodell aus verschiedenen Backend-Datenquellen wie AEM-Benutzerprofil, RESTful-Web-Services, SOAP-basierten Web-Services, OData-Services und relationalen Datenbanken erstellen. Sie können Datenmodellobjekte und -Dienste in einem Formulardatenmodell konfigurieren und einem adaptiven Formular zuordnen. Adaptive Formularfelder sind an Datenmodellobjekteigenschaften gebunden. Mit den Diensten können Sie das adaptive Formular vorab befüllen und gesendete Formulardaten zurück an das Datenmodellobjekt schreiben.

Weitere Informationen zum Formulardatenmodell und zur Formulardatenintegration finden Sie unter [Datenintegration für AEM Forms](../../forms/using/data-integration.md).

Diese Schulung führt Sie durch die Schritte zum Vorbereiten, Erstellen, Konfigurieren und Zuordnen eines Formulardatenmodells mit einem adaptiven Formular. Am Ende dieser Schulung können Sie Folgendes:

* [Konfigurieren der MySQL-Datenbank als Datenquelle](#config-database)
* [Erstellen eines Formulardatenmodells mit der MySQL-Datenbank](#create-fdm)
* [Konfigurieren eines Formulardatenmodells](#config-fdm)
* [Testen eines Formulardatenmodells](#test-fdm)

Das Formulardatenmodell sieht etwa wie folgt aus:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Konfigurierte Datenquellen **B.** Datenquellenschemata **C.** Verfügbare Services **D.** Datenmodellobjekte **E.** Konfigurierte Services

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* [!DNL MySQL]-Datenbank mit Beispieldaten, wie im Abschnitt „Voraussetzungen“ von [So erstellen Sie Ihr erstes adaptives Formular](../../forms/using/create-your-first-adaptive-form.md) beschrieben
* OSGi-Paket für [!DNL MySQL]-JDBC-Treiber, wie unter [Bündeln der JDBC-Datenbanktreiber](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver) erläutert
* Adaptives Formular, wie in der ersten Schulung [Erstellen eines adaptives Formulars](/help/forms/using/create-adaptive-form.md) erläutert

## Schritt 1: Konfigurieren der MySQL-Datenbank als Datenquelle {#config-database}

Sie können verschiedene Arten von Datenquellen konfigurieren, um ein Formulardatenmodell zu erstellen. Für diese Schulung werden wir die MySQL-Datenbank, die Sie konfiguriert und mit Beispieldaten befüllt haben, konfigurieren. Informationen zu anderen unterstützten Datenquellen und deren Konfiguration finden Sie unter [AEM Forms-Datenintegration](../../forms/using/data-integration.md).

Gehen Sie folgendermaßen vor, um Ihre [!DNL MySQL]-Datenbank zu konfigurieren:

1. Installieren Sie den JDBC-Treiber für die [!DNL MySQL]-Datenbank als OSGi-Bundle:

   1. Melden Sie sich bei der AEM [!DNL Forms]-Autoreninstanz als Administrator an und wechseln Sie zu den AEM-Web-Konsole-Bundles. Die Standard-URL lautet [http://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Tippen Sie auf **[!UICONTROL Installieren/Aktualisieren]**. Ein Dialogfeld [!UICONTROL Pakete hochladen/installieren] wird angezeigt.

   1. Tippen Sie auf **[!UICONTROL Datei auswählen]**, um das OSGi-Bundle für den [!DNL MySQL]-JDBC-Treiber auszuwählen. Wählen Sie **[!UICONTROL Bundle starten]** und **[!UICONTROL Pakete aktualisieren]**, und tippen Sie auf **[!UICONTROL Installieren oder aktualisieren]**. Stellen Sie sicher, dass der JDBC-Treiber der [!DNL Oracle Corporation's] für [!DNL MySQL] aktiv ist. Der Treiber wird installiert.

1. Konfigurieren Sie die [!DNL MySQL]-Datenbank als Datenquelle:

   1. Wechseln Sie zu AEM-Web-Konsole unter [http://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Connection Pooled DataSource**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
   1. Geben Sie im Konfigurationsdialog die folgenden Details an:

      * **Datenquellenname:** Sie können einen beliebigen Namen angeben, beispielsweise **WeRetailMySQL**.
      * **Name der DataSource-Diensteigenschaft**: Geben Sie den Namen der Diensteigenschaft an, die den DataSource-Namen enthält. Er wird beim Registrieren der Datenquelleninstanz als OSGi-Dienst angegeben. Zum Beispiel: **datasource.name**.
      * **JDBC-Treiberklasse**: Geben Sie den Java-Klassennamen des JDBC-Treibers an. Geben Sie für die [!DNL MySQL]-Datenbank **com.mysql.jdbc.Driver** an.
      * **JDBC-Verbindungs-URI**: Geben Sie die Verbindungs-URL der Datenbank an. Für eine [!DNL MySQL]-Datenbank, die auf Port 3306 und nach dem Schema WeRetail ausgeführt wird, lautet die URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Benutzername:** Benutzername der Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Kennwort:** Kennwort für die Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Test beim Ausleihen:** Aktivieren Sie die Option **[!UICONTROL Test on Borrow]**.
      * **Test on Return:** Aktivieren Sie die Option **[!UICONTROL Test on Return.]**
      * **Validation Query:** Geben Sie eine SQL SELECT-Abfrage ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Beispiel: **Wählen Sie * aus Kundendaten**.
      * **Transaktions-Isolierung**: Setzen Sie den Wert auf **READ_COMMITTED**.

         Belassen Sie für andere Eigenschaften die standardmäßigen [Werte](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) und tippen Sie auf **[!UICONTROL Speichern]**.

         Eine Konfiguration ähnlich der folgenden wird erstellt.

         ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Schritt 2: Erstellen eines Formulardatenmodells {#create-fdm}

AEM [!DNL Forms] bietet eine intuitive Benutzeroberfläche zum [Erstellen eines Formulardatenmodells](data-integration.md) aus konfigurierten Datenquellen. Sie können mehrere Datenquellen in einem Formulardatenmodell verwenden. Für unseren Anwendungsfall verwenden wir die konfigurierte [!DNL MySQL]-Datenquelle.

Gehen Sie folgendermaßen vor, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare]** > **[!UICONTROL Datenintegration]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Formulardatenmodell]**.
1. Geben Sie im Dialogfeld „Formulardatenmodell erstellen“ einen **Namen** für das Formulardatenmodell ein. Zum Beispiel **customer-shipping-billing-details**. Tippen Sie auf **[!UICONTROL Weiter]**.
1. Im Bildschirm „Datenquelle auswählen“ werden alle konfigurierten Datenquellen angezeigt. Wählen Sie **WeRetailMySQL** als Datenquelle und tippen Sie auf **[!UICONTROL Erstellen]**.

   ![data-source-selection](assets/data-source-selection.png)

Das Formulardatenmodell **customer-shipping-billing-details** wird erstellt.

## Schritt 3: Konfigurieren eines Formulardatenmodells {#config-fdm}

Zum Konfigurieren eines Formulardatenmodells gehört Folgendes:

* Hinzufügen von Datenmodellobjekten und Diensten
* Konfigurieren von Lese- und Schreibdiensten für Datenmodellobjekte

Gehen Sie folgendermaßen vor, um das Formulardatenmodell zu konfigurieren:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare]** > **[!UICONTROL Datenintegrationen]**. Die Standard-URL lautet [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Das Formulardatenmodell **customer-shipping-billing-details**, dass Sie zuvor erstellt haben, ist hier aufgeführt. Öffnen Sie es im Bearbeitungsmodus.

   Die ausgewählte Datenquelle **WeRetailMySQL** wird im Formulardatenmodell konfiguriert.

   ![default-fdm](assets/default-fdm.png)

1. Erweitern Sie den WeRailMySQL-Datenquellenbaum. Wählen Sie die folgenden Datenmodellobjekte und -services aus dem Schema **weretail** > **customerdetails** aus, um das Datenmodell zu bilden:

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

   ![WeRetail-Schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >Die Standard-Services zum Abrufen, Aktualisieren und Einfügen von JDBC-Datenquellen werden standardmäßig mit dem Formulardatenmodell bereitgestellt.

1. Konfigurieren Sie Lese- und Schreibdienste für Datenmodellobjekte.

   1. Wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**.
   1. Wählen Sie aus dem Dropdown-Menü „Lesedienst“ **[!UICONTROL get.]** Das Argument **id**, das der Primärschlüssel im Datenmodellobjekt des „customerdetails“ ist, wird automatisch hinzugefügt. Tippen Sie auf ![aem_6_3_edit](assets/aem_6_3_edit.png) und konfigurieren Sie das Argument wie folgt.

      ![read-default](assets/read-default.png)

   1. Wählen Sie ebenfalls **[!UICONTROL update]** als Schreibdienst. Das Objekt **customerdetails** wird automatisch als Argument hinzugefügt. Das Argument ist wie folgt konfiguriert.

      ![write-default](assets/write-default.png)

      Fügen Sie das Argument **id** hinzu und konfigurieren Sie es wie folgt.

      ![id-arg](assets/id-arg.png)

   1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Eigenschaften des Datenmodellobjekts zu speichern. Tippen Sie auf **[!UICONTROL Speichern]**, um das Formulardatenmodell zu speichern.

      Die Dienste **[!UICONTROL get]** und **[!UICONTROL update]** werden als Standarddienste für das Datenmodellobjekt hinzugefügt.

      ![data-model-object](assets/data-model-object.png)

1. Wechseln Sie zur Registerkarte **[!UICONTROL Dienste]** und konfigurieren Sie die Dienste **[!UICONTROL get]** und **[!UICONTROL update]**.

   1. Wählen Sie den Service **[!UICONTROL get]** und tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.
   1. Geben Sie im Dialogfeld „Eigenschaften bearbeiten“ Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse abrufen.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         Dieser Service ruft die Lieferadresse und andere Kundendaten aus der [!DNL MySQL]-Datenbank ab.

      * **Ausgabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail schema

      * **Array zurückgeben**: Deaktivieren Sie die Option **Array zurückgeben**.
      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID**.

      Tippen Sie auf **[!UICONTROL Fertig]**. Der Dienst zum Abrufen von Kundendaten aus der MySQL-Datenbank ist konfiguriert.

      ![shiiping-address-retrieve](assets/shiiping-address-retrieval.png)

   1. Wählen Sie den Service **[!UICONTROL update]** und tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.

   1. Geben Sie im Dialogfeld [!UICONTROL Eigenschaften bearbeiten] Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse aktualisieren.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         Dieser Service aktualisiert die Lieferadresse und die zugehörigen Felder in der MySQL-Datenbank

      * **Eingabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail schema

      * **Ausgabetyp**: Wählen Sie **BOOLEAN**.

      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID** und **customerdetails**.
      Tippen Sie auf **[!UICONTROL Fertig]**. Der Service **[!UICONTROL update]** zur Aktualisierung der Kundendaten in der [!DNL MySQL]-Datenbank ist konfiguriert.

      ![shiiping-address-update](assets/shiiping-address-update.png)



Das Datenmodellobjekt und die Dienste im Formulardatenmodell sind konfiguriert. Sie können nun das Formulardatenmodell testen.

## Schritt 4: Testen eines Formulardatenmodells {#test-fdm}

Sie können das Datenmodellobjekt und die Services testen, um zu überprüfen, ob das Formulardatenmodell ordnungsgemäß konfiguriert ist.

Führen Sie folgende Schritte aus, um den Test durchzuführen:

1. Wechseln Sie auf die Registerkarte **[!UICONTROL Modell]**, wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **[!UICONTROL Modellobjekt testen]**.
1. Wählen Sie im Fenster [!UICONTROL Modell/Dienst testen] **[!UICONTROL Modellobjekt lesen]** aus der Dropdown-Liste **[!UICONTROL Modell/Dienst auswählen]** auswählen.
1. Geben Sie im Abschnitt **customerdetails** einen Wert für das Argument **id** in der konfigurierten MySQL-Datenbank [!DNL MySQL] an und tippen Sie auf **[!UICONTROL Test]**.

   Die Kundendetails, die der angegebenen ID zugeordnet sind, werden abgerufen und im Abschnitt **[!UICONTROL Ausgabe]** angezeigt, wie unten gezeigt.

   ![test-read-model](assets/test-read-model.png)

1. In ähnlicher Weise können Sie das Schreibmodellobjekt und die Dienste testen.

   Im folgenden Beispiel aktualisiert der Aktualisierungsdienst die Adressdetails für die ID 7102715 in der Datenbank erfolgreich.

   ![test-write-model](assets/test-write-model.png)

   Wenn Sie nun den Lesemodelldienst für die ID 7107215 erneut testen, werden die aktualisierten Kundendetails abgerufen und angezeigt (siehe unten).

   ![read-updated](assets/read-updated.png)
