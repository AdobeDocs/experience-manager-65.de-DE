---
title: "Schulung: Formulardatenmodell erstellen "
description: Erfahren Sie, wie Sie MySQL als Datenquelle konfigurieren, Formulardatenmodell (FDM) erstellen, konfigurieren und für AEM Forms testen können.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
docset: aem65
exl-id: 40bc5af6-9023-437e-95b0-f85d3df7d8aa
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 73%

---

# Schulung: Formulardatenmodell erstellen {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Dieses Tutorial ist ein Teil der Serie [Erstellen Ihres ersten adaptives Formulars](../../forms/using/create-your-first-adaptive-form.md). Adobe empfiehlt, dass Sie der Reihe in chronologischer Abfolge folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

## Über das Tutorial {#about-the-tutorial}

AEM [!DNL Forms] Mit dem Datenintegrationsmodul können Sie ein Formulardatenmodell aus unterschiedlichen Backend-Datenquellen erstellen, z. B. AEM Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Sie können Datenmodellobjekte und -dienste in einem Formulardatenmodell konfigurieren und einem adaptiven Formular zuordnen. Adaptive Formularfelder sind an Datenmodellobjekt-Eigenschaften gebunden. Mit den Diensten können Sie das adaptive Formular vorab befüllen und gesendete Formulardaten zurück an das Datenmodellobjekt schreiben.

Weitere Informationen zum Formulardatenmodell und zur Formulardatenintegration finden Sie unter [Datenintegration für AEM Forms](../../forms/using/data-integration.md).

Dieses Tutorial führt Sie durch die Schritte zum Vorbereiten, Erstellen, Konfigurieren und Verknüpfen eines Formulardatenmodells mit einem adaptiven Formular. Am Ende dieses Tutorials können Sie Folgendes:

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

Sie können verschiedene Arten von Datenquellen konfigurieren, um ein Formulardatenmodell zu erstellen. Für dieses Tutorial konfigurieren Sie die MySQL-Datenbank, die Sie konfiguriert und mit Beispieldaten gefüllt haben. Informationen zu anderen unterstützten Datenquellen und deren Konfiguration finden Sie unter [AEM Forms-Datenintegration](../../forms/using/data-integration.md).

Gehen Sie folgendermaßen vor, um Ihre [!DNL MySQL]-Datenbank zu konfigurieren:

1. Installieren Sie den JDBC-Treiber für die [!DNL MySQL]-Datenbank als OSGi-Bundle:

   1. Laden Sie das [!DNL MySQL] JDBC-Treiber-OSGi-Bundle von `http://www.java2s.com/ref/jar/download-orgosgiservicejdbc100jar-file.html` herunter. <!-- This URL is an insecure link but using https is not possible -->
   1. Melden Sie sich bei der AEM [!DNL Forms]-Autoreninstanz als Administrator an und wechseln Sie zu den AEM-Web-Konsole-Bundles. Die Standard-URL lautet [http://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Wählen Sie **[!UICONTROL Installieren/Aktualisieren]**. Ein Dialogfeld [!UICONTROL Pakete hochladen/installieren] wird angezeigt.

   1. Auswählen **[!UICONTROL Datei auswählen]** , um die [!DNL MySQL] OSGi-Paket des JDBC-Treibers. Auswählen **[!UICONTROL Paket starten]** und **[!UICONTROL Aktualisieren von Paketen]** und wählen Sie **[!UICONTROL Installieren oder Aktualisieren]**. Stellen Sie sicher, dass der JDBC-Treiber der [!DNL Oracle Corporation's] für [!DNL MySQL] aktiv ist. Der Treiber wird installiert.

1. Konfigurieren Sie die [!DNL MySQL]-Datenbank als Datenquelle:

   1. Wechseln Sie zu AEM-Web-Konsole unter [http://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Connection Pooled DataSource**. Wählen Sie diese Option aus, um die Konfiguration im Bearbeitungsmodus zu öffnen.
   1. Geben Sie im Konfigurationsdialog die folgenden Details an:

      * **Datenquellenname:** Sie können einen beliebigen Namen angeben. beispielsweise **WeRetailMySQL**.
      * **Name der DataSource-Diensteigenschaft**: Geben Sie den Namen der Diensteigenschaft an, die den DataSource-Namen enthält. Er wird beim Registrieren der Datenquelleninstanz als OSGi-Dienst angegeben. Zum Beispiel: **datasource.name**.
      * **JDBC-Treiberklasse**: Geben Sie den Java-Klassennamen™ des JDBC-Treibers an. Geben Sie für die [!DNL MySQL]-Datenbank **com.mysql.jdbc.Driver** an.
      * **JDBC-Verbindungs-URI**: Geben Sie die Verbindungs-URL der Datenbank an. Für [!DNL MySQL] Datenbank, die auf Port 3306 und Schema ausgeführt wird `weretail`lautet die URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`

      >[!NOTE]
      >
      > Wenn sich die [!DNL MySQL]-Datenbank hinter einer Firewall befindet, ist der Datenbank-Host-Name kein öffentliches DNS. Die IP-Adresse der Datenbank muss in der *Datei /etc/hosts* des AEM Host Computers hinzugefügt werden.

      * **Benutzername:** Benutzername der Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Kennwort:** Kennwort für die Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.

      >[!NOTE]
      >
      >AEM Forms unterstützt keine NT-Authentifizierung für [!DNL MySQL]. Rufen Sie AEM Webkonsole auf unter [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr) und suchen Sie nach &quot;Apache Sling Connection Pooled Data Source&quot;. Legen Sie für die Eigenschaft &quot;JDBC connection URI&quot;den Wert von &quot;integratedSecurity&quot;auf False fest und verwenden Sie den erstellten Benutzernamen und das Kennwort für die Verbindung mit [!DNL MySQL] Datenbank.

      * **Test on Borrow**: Aktivieren Sie die Option **[!UICONTROL Test on Borrow]**.
      * **Test on Return:** Aktivieren Sie die Option **[!UICONTROL Test on Return.]**
      * **Validierungsabfrage:** Geben Sie eine SQL SELECT-Abfrage an, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Zum Beispiel **select &#42; from customerdetails**.
      * **Transaktions-Isolierung**: Setzen Sie den Wert auf **READ_COMMITTED**.

        Belassen Sie die Standardwerte](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) bei den anderen Eigenschaften und [wählen Sie Speichern ]**aus**[!UICONTROL .

        Eine Konfiguration ähnlich der folgenden wird erstellt.

        ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Schritt 2: Erstellen eines Formulardatenmodells {#create-fdm}

AEM [!DNL Forms] bietet eine intuitive Benutzeroberfläche zum [Erstellen eines Formulardatenmodells](data-integration.md) aus konfigurierten Datenquellen. Sie können mehrere Datenquellen in einem Formulardatenmodell verwenden. Für diesen Anwendungsfall können Sie die konfigurierte [!DNL MySQL] Datenquelle.

Gehen Sie folgendermaßen vor, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare]** > **[!UICONTROL Datenintegration]**.
1. Auswählen **[!UICONTROL Erstellen]** > **[!UICONTROL Formulardatenmodell]**.
1. Geben Sie im Dialogfeld „Formulardatenmodell erstellen“ einen **Namen** für das Formulardatenmodell ein. Zum Beispiel **customer-shipping-billing-details**. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Im Bildschirm „Datenquelle auswählen“ werden alle konfigurierten Datenquellen angezeigt. Wählen Sie **WeRetailMySQL-Datenquelle** und dann Erstellen ]**aus**[!UICONTROL .

   ![data-source-selection](assets/data-source-selection.png)

Das Formulardatenmodell **customer-shipping-billing-details** wird erstellt.

## Schritt 3: Konfigurieren des Formulardatenmodells {#config-fdm}

Das Konfigurieren des Formulardatenmodells umfasst Folgendes:

* Hinzufügen von Datenmodellobjekten und Diensten
* Konfigurieren von Lese- und Schreibdiensten für Datenmodellobjekte

Gehen Sie wie folgt vor, um das Formulardatenmodell zu konfigurieren:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare]** > **[!UICONTROL Datenintegrationen]**. Die Standard-URL lautet [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Das Formulardatenmodell **customer-shipping-billing-details**, dass Sie zuvor erstellt haben, ist hier aufgeführt. Öffnen Sie es im Bearbeitungsmodus.

   Die ausgewählte Datenquelle **WeRetailMySQL** wird im Formulardatenmodell konfiguriert.

   ![default-fdm](assets/default-fdm.png)

1. Erweitern Sie den WeRailMySQL-Datenquellenbaum. Wählen Sie die folgenden Datenmodellobjekte und Dienste aus **weretail** > **customerdetails** -Schema, damit Sie ein Datenmodell erstellen können:

   * **Datenmodellobjekte**:

      * id
      * name
      * shippingAddress
      * Ort
      * state
      * Postleitzahl

   * **Dienste:**

      * Abrufen
      * Aktualisieren

   Auswählen **Auswahl hinzufügen** , um ausgewählte Datenmodellobjekte und Dienste zum Formulardatenmodell hinzuzufügen.

   ![WeRetail-Schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >Die Standard-Services zum Abrufen, Aktualisieren und Einfügen von JDBC-Datenquellen werden standardmäßig mit dem Formulardatenmodell bereitgestellt.

1. Konfigurieren Sie die Lese- und Schreibdienste für das Datenmodellobjekt.

   1. Wählen Sie das **Datenmodellobjekt &quot;customerdetails** &quot; und danach &quot; **[!UICONTROL Bearbeiten Eigenschaften]**&quot;.
   1. Wählen Sie aus dem Dropdown-Menü „Lesedienst“ **[!UICONTROL get.]** Das Argument **id**, das der Primärschlüssel im Datenmodellobjekt des „customerdetails“ ist, wird automatisch hinzugefügt. Auswählen ![aem_6_3_edit](assets/aem_6_3_edit.png) und konfigurieren Sie das -Argument wie folgt.

      ![read-default](assets/read-default.png)

   1. Wählen Sie auf ähnliche Weise **[!UICONTROL Aktualisieren]** als Schreibdienst. Das Objekt **customerdetails** wird automatisch als Argument hinzugefügt. Das Argument wird wie folgt konfiguriert.

      ![write-default](assets/write-default.png)

      Fügen Sie das Argument **id** hinzu und konfigurieren Sie es wie folgt.

      ![id-arg](assets/id-arg.png)

   1. Auswählen **[!UICONTROL Fertig]** , um die Eigenschaften des Datenmodellobjekts zu speichern. Wählen Sie **[!UICONTROL dann Speichern aus, um]** das Formulardatenmodell zu speichern.

      Die Dienste **[!UICONTROL get]** und **[!UICONTROL update]** werden als Standarddienste für das Datenmodellobjekt hinzugefügt.

      ![data-model-object](assets/data-model-object.png)

1. Wechseln Sie zur Registerkarte **[!UICONTROL Dienste]** und konfigurieren Sie die Dienste **[!UICONTROL get]** und **[!UICONTROL update]**.

   1. Wählen Sie die **[!UICONTROL get]** Dienst und wählen Sie **[!UICONTROL Eigenschaften bearbeiten]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.
   1. Geben Sie im Dialogfeld „Eigenschaften bearbeiten“ Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Zum Beispiel: Versandadresse abrufen.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die eine detaillierte Funktionsweise des Dienstes enthält. Beispiel:

        Dieser Dienst ruft die Lieferadresse und andere Kundendetails aus dem [!DNL MySQL] Datenbank

      * **Ausgabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

        customerdetail schema

      * **Array zurückgeben**: Deaktivieren Sie die Option **Array zurückgeben**.
      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID** aus.

      Auswählen **[!UICONTROL Fertig]**. Der Dienst zum Abrufen von Kundendaten aus der MySQL-Datenbank ist konfiguriert.

      ![shiiping-address-retrieve](assets/shiiping-address-retrieval.png)

   1. Wählen Sie die **[!UICONTROL update]** Dienst und wählen Sie **[!UICONTROL Eigenschaften bearbeiten]**. Das Dialogfeld „Eigenschaften“ wird geöffnet.

   1. Geben Sie im Dialogfeld [!UICONTROL Eigenschaften bearbeiten] Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Versandadresse aktualisieren.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die eine detaillierte Funktionsweise des Dienstes enthält. Beispiel:

        Dieser Service aktualisiert die Lieferadresse und die zugehörigen Felder in der MySQL-Datenbank

      * **Eingabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

        customerdetail schema

      * **Ausgabetyp**: Wählen Sie **BOOLEAN**.

      * **Argumente**: Wählen Sie den Argumentnamen **ID** und **customerdetails**.

      Auswählen **[!UICONTROL Fertig]**. Der Service **[!UICONTROL update]** zur Aktualisierung der Kundendaten in der [!DNL MySQL]-Datenbank ist konfiguriert.

      ![shiiping-address-update](assets/shiiping-address-update.png)

Das Datenmodellobjekt und die Dienste im Formulardatenmodell sind konfiguriert. Sie können das Formulardatenmodell jetzt testen.

## Schritt 4: Testen des Formulardatenmodells {#test-fdm}

Sie können das Datenmodellobjekt und die Services testen, um zu überprüfen, ob das Formulardatenmodell ordnungsgemäß konfiguriert ist.

Führen Sie folgende Schritte aus, um den Test durchzuführen:

1. Navigieren Sie zu **[!UICONTROL Modell]** auswählen, wählen Sie die **customerdetails** Datenmodellobjekt auswählen **[!UICONTROL Testmodell-Objekt]**.
1. Wählen Sie im Fenster [!UICONTROL Modell/Dienst testen] **[!UICONTROL Modellobjekt lesen]** aus der Dropdown-Liste **[!UICONTROL Modell/Dienst auswählen]** auswählen.
1. Im **customerdetails** einen Wert für **id** -Argument, das in der konfigurierten [!DNL MySQL] Datenbank und wählen Sie **[!UICONTROL Test]**.

   Die Kundendetails, die der angegebenen ID zugeordnet sind, werden abgerufen und im Abschnitt **[!UICONTROL Ausgabe]** angezeigt, wie unten gezeigt.

   ![test-read-model](assets/test-read-model.png)

1. Auf ähnliche Weise können Sie das Schreib-Modellobjekt und die Dienste testen.

   Im folgenden Beispiel ändert der Aktualisierungsdienst erfolgreich die Adressdetails für die ID 7102715 in der Datenbank.

   ![test-write-model](assets/test-write-model.png)

   Wenn Sie den Lesemodell-Dienst jetzt erneut für die ID 7107215 testen, ruft er die aktualisierten Kundendetails ab und zeigt sie an, wie unten dargestellt.

   ![read-updated](assets/read-updated.png)
