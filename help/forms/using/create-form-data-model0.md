---
title: '„Tutorial: Erstellen eines Formulardatenmodells in AEM Forms“'
description: Erstellen Sie ein Formulardatenmodell für interaktive Kommunikation
uuid: b56d3dac-be54-4812-b958-38a085686218
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e5413fb3-9d50-4f4f-9db8-7e53cd5145d5
docset: aem65
feature: Interactive Communication
exl-id: c8a6037c-46bd-4058-8314-61cb925ba5a8
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 97%

---

# Schulung: Formulardatenmodell erstellen in AEM Forms{#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, die Serie in chronologischer Reihenfolge zu durchlaufen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, durchzuführen und zu demonstrieren.

## Über das Tutorial {#about-the-tutorial}

Mit dem AEM Forms-Datenintegrationsmodul können Sie ein Formulardatenmodell aus unterschiedlichen Backend-Datenquellen wie AEM Benutzerprofil, RESTful-Webservices, SOAP-basierten Webdiensten, OData-Diensten und relationalen Datenbanken erstellen. Sie können Datenmodellobjekte und -dienste in einem Formulardatenmodell konfigurieren und einem adaptiven Formular zuordnen. Adaptive Formularfelder sind an Datenmodellobjekt-Eigenschaften gebunden. Mit den Diensten können Sie das adaptive Formular vorab befüllen und gesendete Formulardaten zurück an das Datenmodellobjekt schreiben.

Weitere Informationen zum Formulardatenmodell und zur Formulardatenintegration finden Sie unter [Datenintegration für AEM Forms](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/data-integration.html).

Dieses Tutorial führt Sie durch die Schritte zum Vorbereiten, Erstellen, Konfigurieren und Verknüpfen eines Formulardatenmodells mit einer interaktiven Kommunikation. Am Ende dieses Tutorials können Sie Folgendes:

* [Einrichten der Datenbank](../../forms/using/create-form-data-model0.md#step-set-up-the-database)
* [Konfigurieren der MySQL-Datenbank als Datenquelle](../../forms/using/create-form-data-model0.md#step-configure-mysql-database-as-data-source)
* [Erstellen des Formulardatenmodells](../../forms/using/create-form-data-model0.md#step-create-form-data-model)
* [Konfigurieren eines Formulardatenmodells](../../forms/using/create-form-data-model0.md#step-configure-form-data-model)
* [Testen eines Formulardatenmodells](../../forms/using/create-form-data-model0.md#step-test-form-data-model-and-services)

Das Formulardatenmodell sieht etwa wie folgt aus:

![Formulardatenmodell](assets/form_data_model_callouts_new.png)

**A.** Konfigurierte Datenquellen **B.** Datenquellenschemata **C.** Verfügbare Services **D.** Datenmodellobjekte **E.** Konfigurierte Services

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* MySQL-Datenbank mit Beispieldaten wie im Abschnitt [Einrichten der Datenbank](../../forms/using/create-form-data-model0.md#step-set-up-the-database) beschrieben.
* OSGi-Bündel für MySQL JDBC-Treiber wie unter [Bündeln der JDBC-Datenbanktreiber](https://helpx.adobe.com/de/experience-manager/6-3/help/sites-developing/jdbc.html#bundling-the-jdbc-database-driver) erläutert

## Schritt 1: Einrichten der Datenbank {#step-set-up-the-database}

Eine Datenbank ist für die Erstellung einer interaktiven Kommunikation unerlässlich. In diesem Tutorial wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM Forms verwendet. Richten Sie eine Datenbank ein, die Kunden-, Rechnungs- und Anruftabellen enthält.
Die folgende Abbildung zeigt Beispieldaten für die Kundentabelle:

![sample_data_cust](assets/sample_data_cust.png)

Mit der folgenden DDL-Anweisung können Sie die Tabelle **customer** in der Datenbank erstellen.

```sql
CREATE TABLE `customer` (
   `mobilenum` int(11) NOT NULL,
   `name` varchar(45) NOT NULL,
   `address` varchar(45) NOT NULL,
   `alternatemobilenumber` int(11) DEFAULT NULL,
   `relationshipnumber` int(11) DEFAULT NULL,
   `customerplan` varchar(45) DEFAULT NULL,
   PRIMARY KEY (`mobilenum`),
   UNIQUE KEY `mobilenum_UNIQUE` (`mobilenum`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Mit der folgenden DDL-Anweisung können Sie die Tabelle **bills** in der Datenbank erstellen.

```sql
CREATE TABLE `bills` (
   `billplan` varchar(45) NOT NULL,
   `latepayment` decimal(4,2) NOT NULL,
   `monthlycharges` decimal(4,2) NOT NULL,
   `billdate` date NOT NULL,
   `billperiod` varchar(45) NOT NULL,
   `prevbal` decimal(4,2) NOT NULL,
   `callcharges` decimal(4,2) NOT NULL,
   `confcallcharges` decimal(4,2) NOT NULL,
   `smscharges` decimal(4,2) NOT NULL,
   `internetcharges` decimal(4,2) NOT NULL,
   `roamingnational` decimal(4,2) NOT NULL,
   `roamingintnl` decimal(4,2) NOT NULL,
   `vas` decimal(4,2) NOT NULL,
   `discounts` decimal(4,2) NOT NULL,
   `tax` decimal(4,2) NOT NULL,
   PRIMARY KEY (`billplan`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Mit der folgenden DDL-Anweisung können Sie die Tabelle **calls** in der Datenbank erstellen.

```sql
CREATE TABLE `calls` (
   `mobilenum` int(11) DEFAULT NULL,
   `calldate` date DEFAULT NULL,
   `calltime` varchar(45) DEFAULT NULL,
   `callnumber` int(11) DEFAULT NULL,
   `callduration` varchar(45) DEFAULT NULL,
   `callcharges` decimal(4,2) DEFAULT NULL,
   `calltype` varchar(45) DEFAULT NULL
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Die Tabelle **calls** enthält die Anrufdetails wie Anrufdatum, Anrufzeit, Anrufnummer, Anrufdauer und Anrufkosten. Die Tabelle **customer** ist mit der Anruftabelle über das Feld „Mobilfunknummer (mobilenum)“ verknüpft. Für jede in der Tabelle **customer** aufgeführte Mobilfunknummer gibt es mehrere Datensätze in der Tabelle **calls**. Sie können beispielsweise die Anrufdetails für die Mobilfunknummer **1457892541** abrufen, indem Sie sich auf die **Anruftabelle** beziehen.

Die Tabelle **bills** enthält die Rechnungsdetails wie Rechnungsdatum, Rechnungszeitraum, monatliche Gebühren und Gesprächsgebühren. Die Tabelle **customer** ist mit der Tabelle **bills** über das Feld „Rechnungsplan“ verknüpft. Jedem Kunden ist in der Tabelle **customer** ein Plan zugeordnet. Die Tabelle **bills** enthält die Preisangaben für alle vorhandenen Pläne. Sie können beispielsweise die Plandetails für **Sarah** aus der **Kundentabelle** abrufen und diese Details verwenden, um Preisdetails aus der Rec **hnungstabelle** abzurufen.

## Schritt 2: Konfigurieren der MySQL-Datenbank als Datenquelle {#step-configure-mysql-database-as-data-source}

Sie können verschiedene Arten von Datenquellen konfigurieren, um ein Formulardatenmodell zu erstellen. Für dieses Tutorial werden wir die MySQL-Datenbank, die Sie konfiguriert und mit Beispieldaten befüllt haben, konfigurieren. Informationen zu anderen unterstützten Datenquellen und deren Konfiguration finden Sie unter [AEM Forms-Datenintegration](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/data-integration.html).

Gehen Sie folgendermaßen vor, um Ihre MySQL-Datenbank zu konfigurieren:

1. Installieren Sie den JDBC-Treiber für die MySQL-Datenbank als OSGi-Bundle:

   1. Melden Sie sich bei der AEM Forms-Autoreninstanz als Administrator an und wechseln Sie zu den AEM-Webkonsolen-Paketen. Die Standard-URL lautet [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).
   1. Tippen Sie auf **Installieren/Aktualisieren**. Ein Dialogfeld **Pakete hochladen/installieren** wird angezeigt.

   1. Tippen Sie auf **Datei auswählen**, um das OSBi-Paket für den MySQL-JDBC-Treiber auszuwählen. Wählen Sie **Bundle starten** und **Pakete aktualisieren**, und tippen Sie auf **Installieren** oder **Aktualisieren**. Stellen Sie sicher, dass der JDBC-Treiber der Oracle Corporation für MySQL aktiv ist. Der Treiber wird installiert.

1. Konfigurieren der MySQL-Datenbank als Datenquelle:

   1. Wechseln zur AEM-Web-Konsole unter [http://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Connection Pooled DataSource**. Tippen Sie auf die Konfiguration, um sie im Bearbeitungsmodus zu öffnen.
   1. Geben Sie im Konfigurationsdialog die folgenden Details an:

      * **Datenquellenname:** Sie können einen beliebigen Namen angeben. Geben Sie beispielsweise **MySQL** an.

      * **Name der DataSource-Diensteigenschaft**: Geben Sie den Namen der Diensteigenschaft an, die den DataSource-Namen enthält. Er wird beim Registrieren der Datenquelleninstanz als OSGi-Dienst angegeben. Zum Beispiel: **datasource.name**.

      * **JDBC-Treiberklasse**: Geben Sie den Java-Klassennamen des JDBC-Treibers an. Geben Sie für die MySQL-Datenbank **com.mysql.jdbc.Driver** an.

      * **JDBC-Verbindungs-URI**: Geben Sie die Verbindungs-URL der Datenbank an. Für MySQL-Datenbanken, die auf Port 3306 und Schema Teleca ausgeführt werden, lautet die URL `jdbc:mysql://'server':3306/teleca?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`.
      * **Benutzername:** Benutzername der Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Kennwort:** Kennwort für die Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Test on Borrow**: Aktivieren Sie die Option **Test on Borrow**.

      * **Test on Return:** Aktivieren Sie die Option **Test on Return.**

      * **Validierungsabfrage:** Geben Sie eine SQL SELECT-Abfrage an, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Zum Beispiel **select &#42; from customer**.

      * **Transaktions-Isolierung**: Setzen Sie den Wert auf **READ_COMMITTED**.

   Belassen Sie die anderen Eigenschaften auf den [Standardwerten](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) und tippen Sie auf **Speichern**.

   Eine Konfiguration ähnlich der folgenden wird erstellt.

   ![Apache-Konfiguration](assets/apache_configuration_new.png)

## Schritt 3: Erstellen eines Formulardatenmodells {#step-create-form-data-model}

AEM Forms bietet eine intuitive Benutzeroberfläche zum [Erstellen eines Formulardatenmodells](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/data-integration.html#main-pars_header_1524967585) aus konfigurierten Datenquellen. Sie können mehrere Datenquellen in einem Formulardatenmodell verwenden. Für den Anwendungsfall in diesem Tutorial verwenden Sie MySQL als Datenquelle.

Gehen Sie folgendermaßen vor, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **Formulare** > **Datenintegration**.
1. Tippen Sie auf **Erstellen** > **Formulardatenmodell**.
1. Geben Sie im Dialogfeld „Formulardatenmodell erstellen“ einen **Namen** für das Formulardatenmodell ein. Zum Beispiel **FDM_Create_First_IC**. Tippen Sie auf **Weiter**.
1. Im Bildschirm „Datenquelle auswählen“ werden alle konfigurierten Datenquellen angezeigt. Wählen Sie **MySQL** als Datenquelle und tippen Sie auf **Erstellen**.

   ![MySQL-Datenquelle](assets/fdm_mysql_data_source_new.png)

1. Klicken Sie auf **Fertig**. Das Formulardatenmodell **FDM_Create_First_IC** wird erstellt.

## Schritt 4: Konfigurieren eines Formulardatenmodells {#step-configure-form-data-model}

Die Konfiguration des Formulardatenmodells umfasst Folgendes:

* [Hinzufügen von Datenmodellobjekten und Diensten](#add-data-model-objects-and-services)
* [Erstellen von berechneten untergeordneten Eigenschaften für das Datenmodellobjekt](#create-computed-child-properties-for-data-model-object)
* [Hinzufügen von Assoziationen zwischen Datenmodellobjekten](#add-associations-between-data-model-objects)
* [Eigenschaften des Datenmodellobjekts bearbeiten](#edit-data-model-object-properties)
* [Konfigurieren von Diensten für Datenmodellobjekte](#configure-services)

### Hinzufügen von Datenmodellobjekten und Services {#add-data-model-objects-and-services}

1. Navigieren Sie in der AEM-Autoreninstanz zu **Formulare** > **Datenintegrationen**. Die Standard-URL lautet [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Das Formulardatenmodell **FDM_Create_First_IC**, dass Sie zuvor erstellt haben, ist hier aufgeführt. Wählen Sie es aus und tippen Sie auf **Bearbeiten**.

   Die ausgewählte Datenquelle **MySQL** wird im Bereich **Datenquellen** angezeigt.

   ![MySQL-Datenquelle für FDM](assets/mysql_fdm_new.png)

1. Erweitern Sie die Datenquellstruktur **MySQL**. Wählen Sie die folgenden Datenmodellobjekte und -Services aus dem Schema **teleca** aus:

   * **Datenmodellobjekte**:

      * Rechnungen
      * Anrufe
      * Kunde

   * **Dienste:**

      * Abrufen
      * Aktualisieren

   Tippen Sie auf **Ausgewählte hinzufügen**, um dem Formulardatenmodell ausgewählte Datenmodellobjekte und Dienste hinzuzufügen.

   ![Auswählen von Datenmodellobjekt-Services](assets/select_data_model_object_services_new.png)

   Die Rechnungen, Anrufe und Kundendatenmodellobjekte werden im rechten Bereich auf der Registerkarte **Modell** angezeigt. Die Abruf- und Aktualisierungsdienste werden auf der Registerkarte **Dienste** angezeigt.

   ![Datenmodellobjekte](assets/data_model_objects_new.png)

### Erstellen berechneter untergeordneter Eigenschaften für das Datenmodellobjekt {#create-computed-child-properties-for-data-model-object}

Eine berechnete Eigenschaft ist diejenige, deren Wert anhand einer Regel oder eines Ausdrucks berechnet wird. Mithilfe einer Regel können Sie den Wert einer berechneten Eigenschaft auf ein Literal, eine Zahl, das Ergebnis eines mathematischen Ausdrucks oder den Wert einer anderen Eigenschaft im Formulardatenmodell festlegen.

Basierend auf dem Anwendungsfall erstellen Sie die untergeordnete berechnete Eigenschaft **usagecharges** im Datenmodellobjekt **Rechnungen** mit folgendem mathematischem Ausdruck:

* Nutzungsgebühren = Gesprächsgebühren + Gebühren für Telefonkonferenzen + SMS-Gebühren + mobile Internet-Gebühren + Nationale und internationale Roaming-Gebühren + VAS (all diese Eigenschaften existieren im Datenmodellobjekt „Rechnungen“) 
Weitere Informationen über die untergeordnete berechnete Eigenschaft **usagecharges** finden Sie unter [Planen der interaktiven Kommunikation](/help/forms/using/planning-interactive-communications.md).

Führen Sie die folgenden Schritte durch, um untergeordnete berechnete Eigenschaften für das Datenmodellobjekt „Rechnungen“ zu erstellen:

1. Aktivieren Sie das Kontrollkästchen oben in dem Datenmodellobjekt **bills** und tippen Sie auf **Untergeordnete Eigenschaft erstellen**.
1. Im Bereich **Untergeordnete Eigenschaft erstellen**:

   1. Geben Sie als Namen der untergeordneten Eigenschaft **usagecharges** ein.
   1. Aktivieren Sie **Berechnet**.
   1. Wählen Sie **Float** als Typ und tippen Sie auf **Fertig**, um die untergeordnete Eigenschaft zum Datenmodellobjekt **bills** hinzuzufügen.

   ![Untergeordnete Eigenschaft erstellen](assets/create_child_property_new.png)

1. Tippen Sie auf **Regel bearbeiten**, um den Regel-Editor zu öffnen.
1. Tippen Sie auf **Erstellen**. Ein Regelfenster **Wert festlegen** wird geöffnet.
1. Wählen Sie in der Dropdownliste **Mathematischer Ausdruck**.

   ![Regel-Editor für Nutzungsgebühren](assets/usage_charges_rule_editor_new.png)

1. Wählen Sie in dem mathematischen Ausdruck **callcharges** und **confcallcharges** als erstes bzw. zweites Objekt aus. Wählen Sie **plus** als Operator. Tippen Sie innerhalb des mathematischen Ausdrucks auf **Ausdruck erweitern**, um die Objekte **smscharges**, **internetcharges**, **roamingnational**, **roamingintnl** und **vas** hinzuzufügen.

   Die folgende Abbildung zeigt den mathematischen Ausdruck im Regeleditor:

   ![Nutzungskostenregel](assets/usage_charges_rule_all_new.png)

1. Tippen Sie auf **Fertig**. Die Regel wird im Regel-Editor erstellt.
1. Tippen Sie auf **Schließen**, um das Fenster des Regel-Editors zu schließen.

### Hinzufügen von Verknüpfungen zwischen Datenmodellobjekten {#add-associations-between-data-model-objects}

Nachdem die Datenmodellobjekte definiert wurden, können Sie Verknüpfungen zwischen ihnen erstellen. Die Zuordnung kann 1:1 oder 1:n sein. Beispielsweise können einem Mitarbeitenden mehrere abhängige Elemente zugeordnet sein. Dies wird als Eins-zu-Viele-Verknüpfung bezeichnet und in der Form 1:n auf der Linie dargestellt, die die zugeordneten Datenmodellobjekte verbindet. Wenn jedoch eine Verknüpfung einen eindeutigen Mitarbeiternamen für eine gegebene Mitarbeiter-ID zurückgibt, wird dies als Eins-zu-Eins-Verknüpfung bezeichnet.

Wenn Sie verknüpfte Datenmodellobjekte in einer Datenquelle einem Formulardatenmodell hinzufügen, werden ihre Verknüpfungen beibehalten und mit Pfeillinien verbunden angezeigt.

Erstellen Sie basierend auf dem Anwendungsfall die folgenden Verknüpfungen zwischen den Datenmodellobjekten:

| Verknüpfung | Datenmodellobjekte |
|---|---|
| 1:n | customer:calls (mehrere Anrufe können einem Kunden oder einer Kundin in einer monatlichen Rechnung zugeordnet werden) |
| 1:1 | customer:bills (eine Rechnung ist einem Kunden oder einer Kundin für einen bestimmten Monat zugeordnet) |

Führen Sie die folgenden Schritte aus, um Verknüpfungen zwischen Datenmodellobjekten zu erstellen:

1. Aktivieren Sie das Kontrollkästchen oben in einem Datenmodellobjekt **customer**, um dieses auszuwählen, und tippen Sie auf **Verknüpfung hinzufügen**. Der Eigenschaftsbereich **Verknüpfung hinzufügen** wird geöffnet.
1. Im Bereich **Verknüpfung hinzufügen**:

   * Geben Sie einen Titel für die Verknüpfung ein. Dies ist ein optionales Feld.
   * Wählen Sie **1:n** aus der **Typ** Dropdown-Liste.

   * Wählen Sie **Anruf** aus der Dropdown-Liste **Modellobjekt**.

   * Wählen Sie **get** aus der Dropdown-Liste **Service**.

   * Tippen Sie auf **Hinzufügen**, um das Datenmodellobjekt **customer** mit dem Datenmodellobjekt **calls** mithilfe einer Eigenschaft zu verknüpfen. Basierend auf dem Anwendungsfall muss das Datenmodellobjekt „call“ mit der Eigenschaft der Mobilfunknummer im Datenmodellobjekt „customer“ verknüpft sein. Das Dialogfeld **Argument hinzufügen** wird geöffnet.

   ![Verknüpfung hinzufügen](assets/add_association_new.png)

1. Im Dialogfeld **Argument hinzufügen**:

   * Wählen Sie **mobilenum** aus der Dropdown-Liste **Name** aus. Die Mobilfunknummer ist eine allgemeine Eigenschaft, die in Datenmodellobjekten „customer“ und „calls“ verfügbar ist. Infolgedessen wird eine Verbindung zwischen Datenmodellobjekten „customer“ und „calls“ erstellt.
Für jede im Datenmodellobjekt „customer“ verfügbare Mobilfunknummer stehen mehrere „call“-Datensätze in der Anruftabelle zur Verfügung.

   * Geben Sie einen optionalen Titel und eine Beschreibung für das Argument an.
   * Wählen Sie **Kunde** aus der Dropdown-Liste **Bindung an**.

   * Wählen Sie **mobilenum** aus der Dropdown-Liste **Bindungswert** aus.

   * Tippen Sie auf **Hinzufügen**.

   ![Verknüpfung für ein Argument hinzufügen](assets/add_association_argument_new.png)

   Die Eigenschaft „mobilenum“ wird im Abschnitt **Argumente** angezeigt.

   ![Argumentzuordnung hinzufügen](assets/add_argument_association_new.png)

1. Tippen Sie auf **Fertig**, um eine 1:n-Verknüpfung zwischen Datenmodellobjekten „customer“ und „calls“ zu erstellen.

   Nachdem Sie eine Zuordnung zwischen Kunden- und Anrufdatenmodellobjekten erstellt haben, erstellen Sie eine 1:1-Verknüpfung zwischen den Datenmodellobjekten „customer“ und „bills“.

1. Aktivieren Sie das Kontrollkästchen am oberen Rand des Datenmodellobjekts **customer**, um es auszuwählen, und tippen Sie auf **Verknüpfung hinzufügen**. Der Eigenschaftsbereich **Verknüpfung hinzufügen** wird geöffnet.
1. Im Bereich **Verknüpfung hinzufügen**:

   * Geben Sie einen Titel für die Verknüpfung ein. Dies ist ein optionales Feld.
   * Wählen Sie **1:1** aus der Dropdown-Liste **Typ** aus.

   * Wählen Sie **bills** aus der Dropdown-Liste **Modellobjekt** aus.

   * Wählen Sie **get** aus der Dropdown-Liste **Service.** Die Eigenschaft **billplan**, die den Primärschlüssel für die Rechnungstabelle darstellt, ist bereits im Abschnitt **Argumente** verfügbar.
Die Datenmodellobjekte „bills“ und „customer“ werden jeweils mit den Eigenschaften „billplan“ Rechnungen und „customerplan“ (Kunde) verknüpft. Erstellen Sie eine Bindung zwischen diesen Eigenschaften, um die Planungsdetails für jeden in der MySQL-Datenbank verfügbaren Kunden abzurufen.

   * Wählen Sie **Kunde** aus der Dropdown-Liste **Bindung an**.

   * Wählen Sie **Kundenplan** aus der Dropdown-Liste **Bindung an**.

   * Tippen Sie auf **Fertig**, um eine Verbindung zwischen den Eigenschaften „billplan“ und „customerplan“ herzustellen.

   ![Hinzufügen einer Verknüpfung mit der Kundenrechnung](assets/add_association_customer_bills_new.png)

   Das folgende Bild zeigt die Zuordnungen zwischen den Datenmodellobjekten und den Eigenschaften, die zum Erstellen von Zuordnungen zwischen ihnen verwendet werden:

   ![fdm_associations](assets/fdm_associations.gif)

### Bearbeiten der Eigenschaften von Datenmodellobjekten {#edit-data-model-object-properties}

Nachdem Sie Verknüpfungen zwischen dem Kunden- und anderen Datenmodellobjekten erstellt haben, bearbeiten Sie die Kundeneigenschaften, um die Eigenschaft zu definieren, anhand derer die Daten vom Datenmodellobjekt abgerufen werden. Basierend auf dem Anwendungsfall wird die Mobilfunknummer als Eigenschaft zum Abrufen von Daten aus dem Datenmodellobjekt „Kunde“ verwendet.

1. Aktivieren Sie das Kontrollkästchen am oberen Rand des Datenmodellobjekts **customer**, um es auszuwählen, und tippen Sie auf **Eigenschaften bearbeiten**. Der Bereich **Eigenschaften bearbeiten** wird geöffnet.
1. Geben Sie **customer** als **Modellobjekt der obersten Ebene** an.
1. Wählen Sie **Abrufen** aus der Dropdown-Liste **Lesedienst**.
1. Im Abschnitt **Argumente**:

   * Wählen Sie **Anfrage-Attribute** aus der Dropdown-Liste **Bindung an**.

   * Geben Sie **mobilenum** als Bindungswert an.

1. Wählen Sie **Update** aus der **Dropdown-Liste** Schreib-Service.
1. Im Abschnitt **Argumente**:

   * Wählen Sie die Eigenschaft **mobilenum**, wählen Sie **customer** aus der Dropdown-Liste **Bindung an** aus.

   * Wählen Sie **mobilenum** aus der Dropdown-Liste **Bindungswert** aus.

1. Tippen Sie auf **Fertig**, um die Eigenschaften zu speichern.

   ![Konfigurieren von Services](assets/configure_services_customer_new.png)

1. Aktivieren Sie das Kontrollkästchen am oberen Rand des Datenmodellobjekts **calls**, um es auszuwählen, und tippen Sie auf **Eigenschaften bearbeiten**. Der Bereich **Eigenschaften bearbeiten** wird geöffnet.
1. Deaktivieren Sie das **Modellobjekt der obersten Ebene** für das Datenmodellobjekt **calls**.
1. Tippen Sie auf **Fertig**.

   Wiederholen Sie die Schritte 8 bis 10, um die Eigenschaften für das Datenmodellobjekt **Rechnung** zu konfigurieren.

### Konfigurieren von Services {#configure-services}

1. Wechseln Sie zur Registerkarte **Services**.
1. Wählen Sie den Service **get** aus und tippen Sie auf **Eigenschaften bearbeiten**. Der Bereich **Eigenschaften bearbeiten** wird geöffnet.
1. Im Bereich **Eigenschaften bearbeiten**:

   * Geben Sie einen optionalen Titel und eine optionale Beschreibung ein.
   * Wählen Sie **Kunde** aus der Dropdown-Liste **Ausgabemodellobjekt**.

   * Tippen Sie auf **Fertig**, um die Eigenschaften zu speichern.

   ![Eigenschaften bearbeiten](assets/edit_properties_get_details_new.png)

1. Wählen Sie den Service **Aktualisierung** aus und tippen Sie auf **Eigenschaften bearbeiten**. Der Bereich **Eigenschaften bearbeiten** wird geöffnet.
1. Im Bereich **Eigenschaften bearbeiten**:

   * Geben Sie einen optionalen Titel und eine optionale Beschreibung ein.
   * Wählen Sie **customer** aus der Dropdown-Liste **Eingabemodellobjekt** aus.

   * Tippen Sie auf **Fertig**.
   * Tippen Sie auf **Speichern**, um das Formulardatenmodell zu speichern.

   ![Service-Eigenschaften aktualisieren](assets/update_service_properties_new.png)

## Schritt 5: Testen von Formulardatenmodellen und Services  {#step-test-form-data-model-and-services}

Sie können das Datenmodellobjekt und die Services testen, um zu überprüfen, ob das Formulardatenmodell ordnungsgemäß konfiguriert ist.

Führen Sie folgende Schritte aus, um den Test durchzuführen:

1. Wechseln Sie zur Registerkarte **Modell**, wählen Sie das Datenmodellobjekt **customer** und tippen Sie auf **Modellobjekt testen**.
1. Wählen Sie im Fenster **Formulardatenmodellobjekt testen** **Lese-Modellobjekt** aus der Dropdown-Liste **Modell/Service auswählen**.
1. Geben Sie im Abschnitt **Eingabe** einen Wert für die Eigenschaft **mobilenum** ein, die in der konfigurierten MySQL-Datenbank existiert, und tippen Sie auf **Testen**.

   Die Kundendetails, die der angegebenen Eigenschaft „mobilenum“ zugeordnet sind, werden abgerufen und im Ausgabeabschnitt angezeigt, wie unten gezeigt. Schließen Sie das Dialogfeld.

   ![Datenmodell testen](assets/test_data_model_new.png)

1. Wechseln Sie zur Registerkarte **Services**.
1. Wählen Sie den Service **get** aus und tippen Sie auf **Service testen**. 
1. Geben Sie im Abschnitt **Eingabe** einen Wert für die Eigenschaft **mobilenum** ein, die in der konfigurierten MySQL-Datenbank existiert, und tippen Sie auf **Testen**.

   Die Kundendetails, die der angegebenen Eigenschaft „mobilenum“ zugeordnet sind, werden abgerufen und im Ausgabeabschnitt angezeigt, wie unten gezeigt. Schließen Sie das Dialogfeld.

   ![Service testen](assets/test_service_new.png)

### Bearbeiten und speichern von Beispieldaten {#edit-and-save-sample-data}

Mit dem Formulardatenmodell-Editor können Sie Beispieldaten für alle Datenmodellobjekteigenschaften, einschließlich berechneter Eigenschaften, in einem Formulardatenmodell generieren. Es handelt sich um einen Satz zufälliger Werte, die dem für jede Eigenschaft konfigurierten Datentyp entsprechen. Sie können auch Daten bearbeiten und speichern, die auch dann beibehalten werden, wenn Sie die Beispieldaten neu generieren.

Führen Sie die folgenden Schritte aus, um Beispieldaten zu generieren, zu bearbeiten und zu speichern:

1. Tippen Sie auf der Seite des Formulardatenmodells auf **Beispieldaten bearbeiten**. Es werden Beispieldaten im Fenster „Beispieldaten bearbeiten“ generiert und angezeigt.

   ![Beispieldaten bearbeiten](assets/edit_sample_data_new.png)

1. Bearbeiten Sie im Fenster **Beispieldaten bearbeiten** die Daten nach Bedarf und tippen Sie auf **Speichern**. Schließen Sie das Fenster.
