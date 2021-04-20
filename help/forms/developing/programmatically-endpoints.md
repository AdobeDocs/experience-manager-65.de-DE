---
title: Programmgesteuertes Verwalten von Endpunkten
seo-title: Programmgesteuertes Verwalten von Endpunkten
description: Verwenden Sie den Endpunktregistrierungsdienst, um EJB-Endpunkte hinzuzufügen, SOAP-Endpunkte hinzuzufügen, Endpunkte für überwachte Ordner hinzuzufügen, E-Mail-Endpunkte hinzuzufügen, Remoting-Endpunkte hinzuzufügen, Aufgabe Manager-Endpunkte hinzuzufügen, Endpunkte zu ändern, Endpunkte zu entfernen und Endpunktschnittstelleninformationen abzurufen.
seo-description: Verwenden Sie den Endpunktregistrierungsdienst, um EJB-Endpunkte hinzuzufügen, SOAP-Endpunkte hinzuzufügen, Endpunkte für überwachte Ordner hinzuzufügen, E-Mail-Endpunkte hinzuzufügen, Remoting-Endpunkte hinzuzufügen, Aufgabe Manager-Endpunkte hinzuzufügen, Endpunkte zu ändern, Endpunkte zu entfernen und Endpunktschnittstelleninformationen abzurufen.
uuid: 5dc50946-3323-4c5d-a43b-31c1c980bd04
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 076889a7-9c9f-4b6f-a45b-67a9b3923c36
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '10864'
ht-degree: 6%

---


# Programmgesteuertes Verwalten von Endpunkten {#programmatically-managing-endpoints}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Info zum Endpunkt-Registrierungsdienst**

Der Endpoint-Registrierungsdienst bietet die Möglichkeit, Endpunkte programmgesteuert zu verwalten. Sie können beispielsweise die folgenden Typen von Endpunkten zu einem Dienst hinzufügen:

* EJB
* SOAP
* Überwachter Ordner
* E-Mail
* (Für AEM Formulare nicht mehr unterstützt) Remoting
* Aufgabe Manager

>[!NOTE]
>
>SOAP-, EJB- und (für AEM Forms on JEE nicht mehr unterstützt) Remoting-Endpunkte werden automatisch für jeden aktivierten Dienst erstellt. Die SOAP- und EJB-Endpunkte ermöglichen SOAP und EJB für alle Dienstvorgänge.

Ein Remoting-Endpunkt ermöglicht es Flex-Clients, Vorgänge für den AEM Forms-Dienst aufzurufen, dem der Endpunkt hinzugefügt wird. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt, und Flex-Clients können RemoteObjects erstellen, die auf dieses Ziel verweisen, um Vorgänge für den betreffenden Dienst aufzurufen.

Die Endpunkte &quot;E-Mail&quot;, &quot;Aufgabe-Manager&quot;und &quot;Überwachter Ordner&quot;stellen nur einen bestimmten Dienstvorgang bereit. Das Hinzufügen dieser Endpunkte erfordert einen zweiten Konfigurationsschritt, um eine Methode zum Aufrufen auszuwählen, Konfigurationsparameter festzulegen und Zuordnungen von Eingabe- und Ausgabeparametern festzulegen.

Sie können TaskManager-Endpunkte in Gruppen mit dem Namen *Kategorien* organisieren. Diese Kategorien werden dann Workspace über TaskManager angezeigt, wobei die TaskManager-Endpunkte den Endpunkten während der Kategorisierung angezeigt werden. Innerhalb von Workspace sehen Endbenutzer diese Kategorien im Navigationsbereich. Die Endpunkte in den einzelnen Kategorien werden als Prozesskarten auf der Seite &quot;Beginn-Prozesse&quot;in Workspace angezeigt.

Sie können diese Aufgaben mithilfe des Endpunktregistrierungsdiensts ausführen:

* hinzufügen EJB-Endpunkte. (Siehe [Hinzufügen von EJB-Endpunkten](programmatically-endpoints.md#adding-ejb-endpoints).)
* hinzufügen SOAP-Endpunkte. (Siehe [Hinzufügen von SOAP-Endpunkten](programmatically-endpoints.md#adding-soap-endpoints).)
* hinzufügen Endpunkte für überwachte Ordner (siehe [Hinzufügen von Endpunkten für überwachte Ordner](programmatically-endpoints.md#adding-watched-folder-endpoints).)
* hinzufügen E-Mail-Endpunkte. (Siehe [Hinzufügen von E-Mail-Endpunkten](programmatically-endpoints.md#adding-email-endpoints).)
* hinzufügen Remoting-Endpunkte. (Siehe [Remoting-Endpunkte](programmatically-endpoints.md#adding-remoting-endpoints) hinzufügen.)
* hinzufügen TaskManager-Endpunkte (siehe [Hinzufügen von TaskManager-Endpunkten](programmatically-endpoints.md#adding-taskmanager-endpoints).)
* Endpunkte ändern (Siehe [Endpunkte ändern](programmatically-endpoints.md#modifying-endpoints).)
* Entfernen Sie Endpunkte (siehe [Entfernen von Endpunkten](programmatically-endpoints.md#removing-endpoints).)
* Abrufen von Endpunktschnittstellenverbindungsinformationen (siehe [Abrufen von Endpunktschnittstelleninformationen](programmatically-endpoints.md#retrieving-endpoint-connector-information).)

## Hinzufügen von EJB-Endpunkten {#adding-ejb-endpoints}

Sie können einem Dienst programmgesteuert einen EJB-Endpunkt hinzufügen, indem Sie die AEM Forms Java API verwenden. Indem Sie einem Dienst einen EJB-Endpunkt hinzufügen, aktivieren Sie eine Clientanwendung, um den Dienst mithilfe des EJB-Modus aufzurufen. Das heißt, beim Festlegen der Verbindungseigenschaften, die zum Aufrufen von AEM Forms erforderlich sind, können Sie den EJB-Modus auswählen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Mit Webdiensten können Sie keinen EJB-Endpunkt hinzufügen.

>[!NOTE]
>
>Normalerweise wird einem Dienst standardmäßig ein EJB-Endpunkt hinzugefügt. Ein EJB-Endpunkt kann jedoch einem programmgesteuert bereitgestellten Prozess hinzugefügt werden oder wenn ein EJB-Endpunkt entfernt wurde und erneut hinzugefügt werden muss.

### Zusammenfassung der Schritte {#summary-of-steps}

So fügen Sie einem Dienst einen EJB-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistry Client`-Objekt.
1. Legen Sie EJB-Endpunktattribute fest.
1. Erstellen Sie einen EJB-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Bevor Sie einen EJB-Endpunkt programmgesteuert hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**EJB-Endpunktattribute festlegen**

Um einen EJB-Endpunkt für einen Dienst zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen EJB-Endpunkt zu erstellen, geben Sie `EJB` an.
* **Beschreibung**: Gibt die Endpunktbeschreibung an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Dienstkennung**: Gibt den Dienst an, zu dem der Endpunkt gehört.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines EJB-Endpunkts ein Platzhalterzeichen ( `*`) an. Wenn Sie jedoch einen bestimmten Vorgang angeben möchten, anstatt alle Dienstvorgänge aufzurufen, geben Sie den Namen des Vorgangs an, anstatt das Platzhalterzeichen ( `*`) zu verwenden.

**Erstellen eines EJB-Endpunkts**

Nachdem Sie EJB-Endpunktattribute festgelegt haben, können Sie einen EJB-Endpunkt für einen Dienst erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Nachdem Sie den Endpunkt aktiviert haben, kann er zum Aufrufen des Dienstes verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console Ansicht haben.

**Siehe auch**

[Hinzufügen eines EJB-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#adding-an-ejb-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines EJB-Endpunkts mit der Java-API {#adding-an-ejb-endpoint-using-the-java-api}

hinzufügen eines EJB-Endpunkts mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein. (

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie EJB-Endpunktattribute fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `EJB` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie den Vorgang an, der durch Aufrufen der `CreateEndpointInfo`-Objektmethode `setOperationName` aufgerufen wird, und übergeben Sie einen Zeichenfolgenwert, der den Vorgangsnamen angibt. Geben Sie für SOAP- und EJB-Endpunkte ein Platzhalterzeichen ( `*`) an, das alle Vorgänge umfasst.

1. Erstellen Sie einen EJB-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen EJB-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die enable-Methode des Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.`EndpointRegistryClient`

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines EJB-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Hinzufügen von SOAP-Endpunkten {#adding-soap-endpoints}

Sie können einem Dienst programmgesteuert einen SOAP-Endpunkt hinzufügen, indem Sie die AEM Forms Java API verwenden. Durch Hinzufügen eines SOAP-Endpunkts aktivieren Sie eine Clientanwendung, um den Dienst im SOAP-Modus aufzurufen. Das heißt, beim Festlegen der Verbindungseigenschaften, die zum Aufrufen von AEM Forms erforderlich sind, können Sie den SOAP-Modus auswählen.

>[!NOTE]
>
>Mit Webdiensten können Sie keinen SOAP-Endpunkt hinzufügen.

>[!NOTE]
>
>Normalerweise wird einem Dienst standardmäßig ein SOAP-Endpunkt hinzugefügt. Ein SOAP-Endpunkt kann jedoch einem programmgesteuert bereitgestellten Prozess hinzugefügt werden oder wenn ein SOAP-Endpunkt entfernt wurde und erneut hinzugefügt werden muss.

### Zusammenfassung der Schritte {#summary_of_steps-1}

So fügen Sie einem Dienst einen SOAP-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Legen Sie SOAP-Endpunktattribute fest.
1. Erstellen Sie einen SOAP-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Diese JAR-Dateien sind erforderlich, um einen SOAP-Endpunkt zu erstellen. Sie benötigen jedoch zusätzliche JAR-Dateien, wenn Sie den SOAP-Endpunkt zum Aufrufen des Dienstes verwenden. Weitere Informationen zu AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Um einem Dienst programmgesteuert einen SOAP-Endpunkt hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**SOAP-Endpunktattribute festlegen**

Um einem Dienst einen SOAP-Endpunkt hinzuzufügen, geben Sie die folgenden Werte an:

* **Connector-ID-Wert**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen SOAP-Endpunkt zu erstellen, geben Sie `SOAP` an.
* **Beschreibung**: Gibt die Endpunktbeschreibung an.
* **Name**: Gibt den Endpunktnamen an.
* **Dienst-ID-Wert**: Gibt den Dienst an, zu dem der Endpunkt gehört.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines SOAP-Endpunkts ein Platzhalterzeichen ( `*`) an. Wenn Sie jedoch einen bestimmten Vorgang angeben möchten, anstatt alle Dienstvorgänge aufzurufen, geben Sie den Namen des Vorgangs an, anstatt das Platzhalterzeichen ( `*`) zu verwenden.

**SOAP-Endpunkt erstellen**

Nachdem Sie SOAP-Endpunktattribute festgelegt haben, können Sie einen SOAP-Endpunkt erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Dienstes verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console für die Ansicht anzeigen.

**Siehe auch**

[hinzufügen eines SOAP-Endpunkts mit der Java-API](programmatically-endpoints.md#add-a-soap-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen eines SOAP-Endpunkts mit der Java-API {#add-a-soap-endpoint-using-the-java-api}

hinzufügen eines SOAP-Endpunkts zu einem Dienst mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie SOAP-Endpunktattribute fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `SOAP` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOperationName` aufrufen und einen Zeichenfolgenwert übergeben, der den Vorgangsnamen angibt. Geben Sie für SOAP- und EJB-Endpunkte ein Platzhalterzeichen ( `*`) an, das alle Vorgänge umfasst.

1. Erstellen Sie einen SOAP-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen SOAP-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die enable-Methode des Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.`EndpointRegistryClient`

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines SOAP-Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Endpunkte für überwachte Ordner {#adding-watched-folder-endpoints} hinzufügen

Sie können einem Dienst programmgesteuert einen Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzufügen, indem Sie die AEM Forms Java API verwenden. Durch Hinzufügen eines Endpunkts für den überwachten Ordner können Sie Benutzern das Platzieren einer Datei (z. B. einer PDF-Datei) in einem Ordner ermöglichen. Wenn die Datei im Ordner abgelegt wird, wird der konfigurierte Dienst aufgerufen und verarbeitet die Datei. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei in einem angegebenen Ausgabeordner gespeichert. Ein überwachter Ordner ist so konfiguriert, dass er in einem bestimmten Zeitintervall oder mit einem Cron-Zeitplan gescannt wird, z. B. jeden Montag, Mittwoch und Freitag um 12 Uhr.

Um einem Dienst programmgesteuert einen Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzuzufügen, beachten Sie den folgenden Prozess mit kurzer Lebensdauer mit dem Namen *EncryptDocument*. (Siehe [Die AEM Forms-Prozesse](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).)

![aw_aw_encryptdocumentprocess](assets/aw_aw_encryptdocumentprocess.png)

Bei diesem Vorgang wird ein unbesichertes PDF-Dokument als Eingabewert akzeptiert und anschließend das unbesicherte PDF-Dokument an den Vorgang `EncryptPDFUsingPassword` des Encryption-Dienstes weitergegeben. Das PDF-Dokument wird mit einem Kennwort verschlüsselt, und das kennwortverschlüsselte PDF-Dokument ist der Ausgabewert dieses Vorgangs. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) ist `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (kennwortverschlüsseltes PDF-Dokument) ist `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

>[!NOTE]
>
>Mit Webdiensten können Sie keinen Endpunkt für den überwachten Ordner hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-2}

So fügen Sie einem Dienst einen Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Legen Sie Endpunktattribute für überwachte Ordner fest.
1. Geben Sie Konfigurationswerte an.
1. Definieren Sie Eingabeparameterwerte.
1. Definieren Sie einen Ausgabeparameterwert.
1. Erstellen Sie einen Endpunkt des Typs &quot;Überwachter Ordner&quot;.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Um programmgesteuert einen Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Endpunktattribute für überwachten Ordner festlegen**

Geben Sie die folgenden Werte an, um einen Endpunkt des Typs &quot;Überwachter Ordner&quot;für einen Dienst zu erstellen:

* **Connector-ID**: Gibt den Typ des erstellten Endpunkts an. Um einen Endpunkt des Typs &quot;Überwachter Ordner&quot;zu erstellen, geben Sie `WatchedFolder` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Dienstkennung**: Gibt den Dienst an, zu dem der Endpunkt gehört. Um beispielsweise dem in diesem Abschnitt eingeführten Prozess einen Endpunkt für den überwachten Ordner hinzuzufügen (ein Prozess wird zu einem Dienst, wenn er mithilfe von Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Beim Erstellen eines Endpunkts für einen überwachten Ordner für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs in der Regel `invoke`.

**Konfigurationswerte angeben**

Sie müssen Konfigurationswerte für einen Endpunkt des Typs &quot;Überwachter Ordner&quot;angeben, wenn Sie einem Dienst programmgesteuert einen Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzufügen. Diese Konfigurationswerte werden von einem Administrator festgelegt, wenn mithilfe von Administration Console ein Endpunkt des Typs &quot;Überwachter Ordner&quot;hinzugefügt wird.

Die folgende Liste gibt Konfigurationswerte an, die festgelegt werden, wenn einem Dienst programmgesteuert ein Endpunkt des Typs &quot;überwachter Ordner&quot;hinzugefügt wird:

* **url**: Gibt den Speicherort des überwachten Ordners an. In einer geclusterten Umgebung muss dieser Wert auf einen freigegebenen Netzwerkordner verweisen, auf den von jedem Computer im Cluster zugegriffen werden kann.
* **asynchron**: Identifiziert den Aufruftyp als asynchron oder synchron. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert lautet true. Asynchron wird empfohlen.
* **cronExpression**: Wird von Quarz verwendet, um die Abfrage des Eingabeordners zu planen. Weitere Informationen zum Konfigurieren des Cron-Ausdrucks finden Sie unter [https://quartz.sourceforge.net/javadoc/org/quartz/CronTrigger.html](https://quartz.sourceforge.net/javadoc/org/quartz/CronTrigger.html).
* **purgeDuration**: Dies ist ein obligatorisches Attribut. Dateien und Ordner im Ergebnisordner werden bereinigt, wenn sie älter als dieser Wert sind. Dieser Wert wird in Tagen gemessen. Dieses Attribut ist nützlich, um sicherzustellen, dass der Ergebnisordner nicht voll ist. Ein Wert von „-1“ Tage bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.
* **repeatInterval**: Das Intervall (in Sekunden), in dem der überwachte Ordner auf Eingabe überprüft wird. Sofern die Einschränkungen nicht aktiviert sind, sollte dieser Wert länger als die Verarbeitungszeit für einen durchschnittlichen Auftrag sein. Andernfalls kann das System überlastet werden. Der Standardwert ist 5. 
* **repeatCount**: Die Häufigkeit, mit der ein überwachter Ordner den Ordner oder Ordner überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.
* **throttleOn**: Begrenzt die Anzahl der Aufträge für überwachte Ordner, die jederzeit verarbeitet werden können. Die maximale Anzahl von Aufträgen wird durch den Wert batchSize bestimmt.
* **userName**: Der Benutzername, der beim Aufrufen eines Zielgruppe-Dienstes aus dem überwachten Ordner verwendet wird. Dieser Wert ist erforderlich. Der Standardwert ist „SuperAdmin“.
* **domainName**: Die Domäne des Benutzers. Dieser Wert ist erforderlich. Der Standardwert ist „DefaultDom“.
* **batchSize**: Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Verwenden Sie diesen Wert, um eine Überlastung des Systems zu vermeiden. Das gleichzeitige Scannen zu vieler Dateien kann zu einem Absturz führen. Der Standardwert ist 2. 
* **waitTime**: Die Zeit in Millisekunden, die nach der Erstellung gewartet wird, bevor ein Ordner oder eine Datei überprüft wird. Wenn die Wartezeit beispielsweise 36.000.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei nach Ablauf von 59 oder mehr Minuten aufgenommen. Dieses Attribut ist nützlich, um sicherzustellen, dass eine Datei oder ein Ordner vollständig in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und der Download der Datei zehn Minuten dauert, setzen Sie die Wartezeit auf 10&amp;ast;60&amp;ast;1000 Millisekunden. Diese Einstellung verhindert, dass der überwachte Ordner die Datei überprüft, wenn sie zehn Minuten lang nicht gewartet hat. Der Standardwert ist 0.
* **excludeFilePattern**: Das Muster, mit dem ein überwachter Ordner ermittelt, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Dateien oder Ordner mit diesem Muster werden nicht zur Verarbeitung überprüft. Diese Einstellung ist nützlich, wenn die Eingabe ein Ordner ist, der mehrere Dateien enthält. Der Inhalt des Ordners kann in einen Ordner kopiert werden, der einen Namen hat, der vom überwachten Ordner aufgenommen wird. Dieser Schritt verhindert, dass der überwachte Ordner einen Ordner zur Verarbeitung aufnimmt, bevor der Ordner vollständig in den Eingabeordner kopiert wird. Wenn beispielsweise der Wert excludeFilePattern `data*` ist, werden alle Dateien und Ordner, die `data*` entsprechen, nicht aufgenommen. Dazu gehören Dateien und Ordner mit den Namen `data1`, `data2` usw. Zusätzlich kann das Muster durch Platzhaltermuster ergänzt werden, um Dateimuster anzugeben. Der überwachte Ausdruck ändert den regulären Ordner, um Platzhaltermuster wie `*.*` und `*.pdf` zu unterstützen. Diese Platzhaltermuster werden von normalen Ausdrücken nicht unterstützt.
* **includeFilePattern**: Das Muster, mit dem der überwachte Ordner ermittelt, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn dieser Wert beispielsweise `*` ist, werden alle Dateien und Ordner abgerufen, die `input*` entsprechen. Dazu gehören Dateien und Ordner mit den Namen `input1`, `input2` usw. Der Standardwert ist `*`. Dieser Wert gibt alle Dateien und Ordner an. Zusätzlich kann das Muster durch Platzhaltermuster ergänzt werden, um Dateimuster anzugeben. Der überwachte Ausdruck ändert den regulären Ordner, um Platzhaltermuster wie `*.*` und `*.pdf` zu unterstützen. Diese Platzhaltermuster werden von normalen Ausdrücken nicht unterstützt. Dieser Wert ist ein obligatorischer Wert.
* **resultFolderName**: Der Ordner, in dem die gespeicherten Ergebnisse gespeichert werden. Dieser Speicherort kann ein absoluter oder ein relativer Ordnerpfad sein. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Der Standardwert ist `result/%Y/%M/%D/`. Dies ist der Ergebnisordner im überwachten Ordner.
* **preserveFolderName**: Der Speicherort, an dem Dateien nach erfolgreichem Scannen und Aufnehmen gespeichert werden. Dieser Speicherort kann ein absoluter, relativer oder Null-Ordnerpfad sein. Der Standardwert ist `preserve/%Y/%M/%D/`.
* **failureFolderName**: Der Ordner, in dem Fehlerdateien gespeichert werden. Dieser Speicherort ist stets relativ zum überwachten Ordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Der Standardwert ist `failure/%Y/%M/%D/`.
* **preserveOnFailure**: Behält Eingabedateien bei, wenn der Vorgang für einen Dienst nicht ausgeführt werden konnte. Der Standardwert lautet true.
* **overwriteDuplicateFilename**: Bei der Einstellung &quot;true&quot;werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf &quot;false&quot;werden Dateien und Ordner mit dem Suffix &quot;Numerischer Index&quot;als Name verwendet. Der Standardwert lautet false.

**Definieren von Eingabeparameterwerten**

Beim Erstellen eines Endpunkts für überwachte Ordner müssen Sie Eingabeparameterwerte definieren. Das heißt, Sie müssen die Eingabewerte beschreiben, die an den Vorgang übergeben werden, der vom überwachten Ordner aufgerufen wird. Betrachten Sie zum Beispiel den in diesem Thema eingeführten Prozess. Es hat einen Eingabewert mit dem Namen `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Wenn Sie einen Endpunkt für den überwachten Ordner für diesen Prozess erstellen (nachdem ein Prozess aktiviert wurde, wird er zu einem Dienst), müssen Sie den Wert des Eingabeparameters definieren.

Geben Sie die folgenden Werte an, um Eingabeparameterwerte zu definieren, die für einen Endpunkt des Typs &quot;Überwachter Ordner&quot;erforderlich sind:

**Name** des Eingabeparameters: Der Name des Eingabeparameters. Der Name eines Eingabewerts wird in Workbench für einen Prozess angegeben. Wenn der Eingabewert zu einem Dienstvorgang gehört (einem Dienst, der nicht in Workbench erstellt wurde), wird der Eingabename in der Datei component.xml angegeben. Beispielsweise lautet der Name des Eingabeparameters für den in diesem Abschnitt eingeführten Prozess `InDoc`.

**Zuordnungstyp**: Dient zum Konfigurieren der zum Aufrufen des Dienstvorgangs erforderlichen Eingabewerte. Es gibt zwei Arten von Zuordnungstypen:

* `Literal`: Der Endpunkt des Typs &quot;Überwachter Ordner&quot;verwendet den in das Feld eingegebenen Wert, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, long, int und Boolean verwendet, wird die Zeichenfolge in den richtigen Typ konvertiert und der Dienst aufgerufen.
* `Variable`: Der eingegebene Wert ist ein Dateimuster, das vom überwachten Ordner zum Auswählen der Eingabe verwendet wird. Wenn Sie beispielsweise Variable für den Zuordnungstyp auswählen und das Eingabedateien eine PDF-Dokument sein muss, können Sie `*.pdf`als Zuordnungswert angeben.

**Zuordnungswert**: Gibt den Wert des Zuordnungstyps an. Wenn Sie beispielsweise den Zuordnungstyp `Variable` auswählen, können Sie `*.pdf` als Dateimuster angeben.

**Datentyp**: Gibt den Datentyp der eingegebenen Werte an. Der Datentyp des Eingabewerts des in diesem Abschnitt eingeführten Prozesses ist beispielsweise `com.adobe.idp.Document`.

**Definieren eines Ausgabeparameterwerts**

Beim Erstellen eines Endpunkts für einen überwachten Ordner müssen Sie einen Ausgabeparameterwert definieren. Das heißt, Sie müssen den Ausgabewert beschreiben, der von dem Dienst zurückgegeben wird, der vom Endpunkt des Typs &quot;Überwachter Ordner&quot;aufgerufen wird. Betrachten Sie zum Beispiel den in diesem Thema eingeführten Prozess. Es hat einen Ausgabewert mit dem Namen `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`. Wenn Sie einen Endpunkt für den überwachten Ordner für diesen Prozess erstellen (nachdem ein Prozess aktiviert wurde, wird er zu einem Dienst), müssen Sie den Wert des Ausgabeparameters definieren.

Um einen für einen Endpunkt des Typs &quot;Überwachter Ordner&quot;erforderlichen Ausgabeparameterwert zu definieren, geben Sie die folgenden Werte an:

**Name** des Ausgabeparameters: Der Name des Ausgabeparameters. Der Name eines Prozessausgabewerts wird in Workbench angegeben. Wenn der Ausgabewert zu einem Dienstvorgang gehört (einem Dienst, der nicht in Workbench erstellt wurde), wird der Ausgabename in der Datei component.xml angegeben. Beispielsweise lautet der Name des Ausgabeparameters für den in diesem Abschnitt eingeführten Prozess `SecuredDoc`.

**Zuordnungstyp**: Dient zum Konfigurieren der Ausgabe des Dienstes und Vorgangs. Die folgenden Optionen sind verfügbar:

* Wenn der Dienst ein einzelnes Objekt (ein einzelnes Dokument) zurückgibt, ist das Muster `%F.pdf` und das Quellziel ist sourcefilename.pdf. Beispielsweise gibt der in diesem Abschnitt eingeführte Prozess ein einzelnes Dokument zurück. Daher kann der Zuordnungstyp als `%F.pdf` definiert werden ( `%F` bedeutet, dass Sie den angegebenen Dateinamen verwenden). Das Muster `%E` gibt die Erweiterung des Eingabe-Dokuments an.
* Wenn der Dienst eine Liste zurückgibt, lautet das Muster `Result\%F\` und das Quellziel lautet Result\sourcefilename\source1 (output 1) und Result\sourcefilename\source2 (output 2).
* Wenn der Dienst eine Zuordnung zurückgibt, ist das Muster `Result\%F\` und das Quellziel ist Result\sourcefilename\file1 and Result\sourcefilename\file2. Wenn die Map über mehr als ein Objekt verfügt, ist das Muster `Result\%F.pdf` und das Quellziel lautet Result\sourcefilename1.pdf (Ausgabe 1), Result\sourcefilenam2.pdf (Ausgabe 2) usw.

**Datentyp**: Gibt den Datentyp des Rückgabewerts an. Der Datentyp des Rückgabewerts des in diesem Abschnitt eingeführten Prozesses ist beispielsweise `com.adobe.idp.Document`.

**Endpunkt des Typs &quot;Überwachter Ordner&quot;erstellen**

Nachdem Sie die Attribute und Konfigurationswerte des Endpunkts festgelegt und Werte für Eingabe- und Ausgabeparameter definiert haben, müssen Sie den Endpunkt des Typs &quot;Überwachter Ordner&quot;erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen Endpunkt des Typs &quot;Überwachter Ordner&quot;erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Dienstes verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console Ansicht haben.

**Siehe auch**

[hinzufügen eines Endpunkts für einen überwachten Ordner mit der Java-API](programmatically-endpoints.md#add-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen eines Endpunkts des Typs &quot;Überwachter Ordner&quot;mit der Java-API {#add-a-watched-folder-endpoint-using-the-java-api}

hinzufügen eines Endpunkts für den überwachten Ordner mithilfe der AEM Forms Java API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie Endpunktattribute für überwachte Ordner fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `WatchedFolder` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOperationName` aufrufen und einen Zeichenfolgenwert übergeben, der den Vorgangsnamen angibt. Beim Erstellen eines Endpunkts für einen überwachten Ordner für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, wird normalerweise der Name des Vorgangs aufgerufen.

1. Geben Sie Konfigurationswerte an.

   Für jeden Konfigurationswert, der für den Endpunkt des Typs &quot;Überwachter Ordner&quot;festgelegt wird, müssen Sie die `CreateEndpointInfo`-Methode des Objekts aufrufen. `setConfigParameterAsText` Um beispielsweise den Konfigurationswert `url` festzulegen, rufen Sie die `CreateEndpointInfo`-Methode des Objekts `setConfigParameterAsText` auf und übergeben Sie die folgenden Zeichenfolgenwerte:

   * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Geben Sie beim Festlegen des Konfigurationswerts `url` `url` an.
   * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Geben Sie beim Festlegen des Konfigurationswerts `url` den Speicherort des überwachten Ordners an.

   >[!NOTE]
   >
   >Informationen zu allen für den EncryptDocument-Dienst festgelegten Konfigurationswerten finden Sie im Java-Codebeispiel unter [QuickStart: Hinzufügen eines Endpunkts für den überwachten Ordner mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api).

1. Definieren Sie Eingabeparameterwerte.

   Definieren Sie einen Eingabeparameterwert, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setInputParameterMapping` aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Eingabeparameters angibt. Beispielsweise lautet der Name des Eingabeparameters für den EncryptDocument-Dienst `InDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Eingabeparameters angibt. Der Datentyp des Eingabeparameters `InDoc` lautet beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `variable` angeben.
   * Ein Zeichenfolgenwert, der den Wert des Zuordnungstyps angibt. Sie können beispielsweise &amp;ast;.pdf als Dateimuster angeben.

   >[!NOTE]
   >
   >Rufen Sie die `setInputParameterMapping`-Methode für jeden zu definierenden Eingabeparameterwert auf. Da der EncryptDocument-Prozess nur einen Eingabeparameter hat, müssen Sie diese Methode einmal aufrufen.

1. Definieren Sie einen Ausgabeparameterwert.

   Definieren Sie einen Ausgabeparameterwert, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOutputParameterMapping` aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Ausgabeparameters angibt. Beispielsweise lautet der Name des Ausgabeparameters für den EncryptDocument-Dienst `SecuredDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Ausgabeparameters angibt. Der Datentyp des Ausgabeparameters `SecuredDoc` lautet beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `%F.pdf` angeben.

1. Erstellen Sie einen Endpunkt des Typs &quot;Überwachter Ordner&quot;.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den Endpunkt des Typs &quot;Überwachter Ordner&quot;darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `enable` aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines Endpunkts für einen überwachten Ordner mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konfigurationswerte für überwachte Ordner Konstante Datei {#watched-folder-configuration-values-constant-file}

Der [QuickStart: Beim Hinzufügen eines Endpunkts für den überwachten Ordner mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api) wird eine Konstantendatei verwendet, die Teil Ihres Java-Projekts sein muss, um den schnellen Beginn zu kompilieren. Diese Konstantendatei stellt Konfigurationswerte dar, die beim Hinzufügen eines Endpunkts für den überwachten Ordner festgelegt werden müssen. Der folgende Java-Code stellt die Konstantendatei dar.

```java
 /**
     * This class contains constants that can be used when setting Watched Folder
     * configuration values
     */

 public final class WatchedFolderEndpointConfigConstants {

         public static final String PROPERTY_FILEPROVIDER_URL = "url";
         public static final String PROPERTY_PROPERTY_ASYNCHRONOUS = "asynchronous";
         public static final String PROPERTY_CRON_EXPRESSION = "cronExpression";
         public static final String PROPERTY_PURGE_DURATION = "purgeDuration";
         public static final String PROPERTY_REPEAT_INTERVAL = "repeatInterval";
         public static final String PROPERTY_REPEAT_COUNT = "repeatCount";
         public static final String PROPERTY_THROTTLE = "throttleOn";
         public static final String PROPERTY_USERNAMER = "userName";
         public static final String PROPERTY_DOMAINNAME = "domainName";
         public static final String PROPERTY_FILEPROVIDER_BATCH_SIZE = "batchSize";
         public static final String PROPERTY_FILEPROVIDER_WAIT_TIME = "waitTime";
         public static final String PROPERTY_EXCLUDE_FILE_PATTERN = "excludeFilePattern";
         public static final String PROPERTY_INCLUDE_FILE_PATTERN = "excludeFilePattern";
         public static final String PROPERTY_FILEPROVIDER_RESULT_FOLDER_NAME =  "resultFolderName";
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_FOLDER_NAME = "preserveFolderName";
         public static final String PROPERTY_FILEPROVIDER_FAILURE_FOLDER_NAME = "failureFolderName";
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_ON_FAILURE = "preserveOnFailure";
         public static final String PROPERTY_FILEPROVIDER_OVERWRITE_DUPLICATE_FILENAME = "overwriteDuplicateFilename";
        }
```

## Hinzufügen von E-Mail-Endpunkten {#adding-email-endpoints}

Sie können einem Dienst programmgesteuert einen E-Mail-Endpunkt hinzufügen, indem Sie die AEM Forms Java API verwenden. Durch Hinzufügen eines E-Mail-Endpunkts können Sie Benutzern das Senden einer E-Mail mit einer oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto ermöglichen. Anschließend wird der Konfigurationsdienst aufgerufen und die Dateien werden verarbeitet. Nachdem der Dienst den angegebenen Vorgang ausgeführt hat, wird eine E-Mail-Nachricht mit den geänderten Dateien als Dateianlagen an den Absender gesendet.

Um einem Dienst programmgesteuert einen E-Mail-Endpunkt hinzuzufügen, beachten Sie den folgenden Prozess mit kurzer Lebensdauer mit dem Namen *MyApplication\EncryptDocument*. Informationen zu Prozessen mit kurzer Lebensdauer finden Sie unter [Die AEM Forms-Prozesse](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).

![ae_ae_encryptdocumentprocess](assets/ae_ae_encryptdocumentprocess.png)

Bei diesem Vorgang wird ein unbesichertes PDF-Dokument als Eingabewert akzeptiert und anschließend das unbesicherte PDF-Dokument an den Vorgang `EncryptPDFUsingPassword` des Encryption-Dienstes weitergegeben. Dieser Vorgang verschlüsselt das PDF-Dokument mit einem Kennwort und gibt das kennwortverschlüsselte PDF-Dokument als Ausgabenwert zurück. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) ist `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (kennwortverschlüsseltes PDF-Dokument) ist `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

>[!NOTE]
>
>Mit Webdiensten können Sie keinen E-Mail-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-3}

So fügen Sie einem Dienst einen E-Mail-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Festlegen von E-Mail-Endpunktattributen.
1. Geben Sie Konfigurationswerte an.
1. Definieren Sie Eingabeparameterwerte.
1. Definieren Sie einen Ausgabeparameterwert.
1. Erstellen Sie den E-Mail-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Bevor Sie programmgesteuert einen E-Mail-Endpunkt hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**E-Mail-Endpunktattribute festlegen**

Um einen E-Mail-Endpunkt für einen Dienst zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID-Wert**: Gibt den Typ des erstellten Endpunkts an. Um einen E-Mail-Endpunkt zu erstellen, geben Sie `Email` an.
* **Beschreibung**: Gibt eine Beschreibung für den Endpunkt an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Dienst-ID-Wert**: Gibt den Dienst an, zu dem der Endpunkt gehört. Um beispielsweise dem in diesem Abschnitt eingeführten Prozess einen E-Mail-Endpunkt hinzuzufügen (ein Prozess wird zu einem Dienst, wenn er mithilfe von Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Beim Erstellen eines E-Mail-Endpunkts für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs in der Regel `invoke`.

**Konfigurationswerte angeben**

Beim programmgesteuerten Hinzufügen eines E-Mail-Endpunkts zu einem Dienst müssen Sie Konfigurationswerte für einen E-Mail-Endpunkt angeben. Diese Konfigurationswerte werden von einem Administrator angegeben, wenn ein E-Mail-Endpunkt über Administration Console hinzugefügt wird.

>[!NOTE]
>
>Das überwachte E-Mail-Konto ist ein besonderes Konto, das nur für den E-Mail-Endpunkt verwendet wird. Dieses Konto ist kein normales E-Mail-Konto des Benutzers. Das E-Mail-Konto eines normalen Benutzers darf nicht als das Konto konfiguriert werden, das der E-Mail-Anbieter verwendet, da der E-Mail-Anbieter E-Mail-Nachrichten aus dem Posteingang löscht, nachdem die Nachrichten abgeschlossen wurden.

Die folgenden Konfigurationswerte werden festgelegt, wenn einem Dienst programmgesteuert ein E-Mail-Endpunkt hinzugefügt wird:

* **cronExpression**: Ein Cron-Ausdruck, wenn die E-Mail mithilfe eines Cron-Ausdrucks geplant werden muss.
* **repeatCount**: Gibt an, wie oft der E-Mail-Endpunkt den Ordner oder das Verzeichnis überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.
* **repeatInterval**: Die Abtastrate in Sekunden, die der Empfänger zum Prüfen auf eingehende E-Mails verwendet. Der Standardwert ist 10. 
* **startDelay**: Die Wartezeit bis zum Scannen nach den Beginn der Planung. Die Standardzeit ist 0.
* **batchSize**: Die Anzahl der E-Mail-Nachrichten, die der Empfänger pro Überprüfung verarbeitet, um eine optimale Leistung zu erzielen. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert ist 2. 
* **userName**: Der Benutzername, der beim Aufrufen eines Zielgruppe-Dienstes aus E-Mail verwendet wird. Der Standardwert ist `SuperAdmin`.
* **domainName**: Ein obligatorischer Konfigurationswert. Der Standardwert ist `DefaultDom`.
* **domainPattern**: Gibt die Domänenmuster für eingehende E-Mails an, die vom Anbieter akzeptiert werden. Wenn beispielsweise `adobe.com` verwendet wird, werden nur E-Mails von adobe.com verarbeitet, E-Mails von anderen Domänen ignoriert.
* **filePattern**: Gibt die Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Dateinamenerweiterungen (&amp;ast;.dat, &amp;ast;.xml), Dateien mit bestimmten Namen (Daten) und Dateien mit zusammengesetzten Ausdrücken im Namen und in der Erweiterung (&amp;ast;.[d][aA]&#39;port&#39;). Der Standardwert ist `*`.
* **empfängerSuccessfulJob**: Eine E-Mail-Adresse, an die Benachrichtigungen über erfolgreiche Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über erfolgreiche Aufträge immer an den Absender gesendet. Wenn Sie `sender` eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen an, die jeweils durch ein Komma getrennt werden. Um diese Option zu deaktivieren, lassen Sie diesen Wert leer. In einigen Fällen möchten Sie möglicherweise einen Trigger durchführen und keine E-Mail-Benachrichtigung zum Ergebnis wünschen. Der Standardwert ist `sender`.
* **empfängerFailedJob**: Eine E-Mail-Adresse, an die Benachrichtigungen über fehlgeschlagene Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über fehlgeschlagene Aufträge immer an den Absender gesendet. Wenn Sie `sender` eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen an, die jeweils durch ein Komma getrennt werden. Um diese Option zu deaktivieren, lassen Sie diesen Wert leer. Der Standardwert ist `sender`.
* **inboxHost**: Der Hostname oder die IP-Adresse des Posteingangs, die vom E-Mail-Anbieter überprüft werden soll.
* **inboxPort**: Der Anschluss, den der E-Mail-Server verwendet. Der Standardwert ist für POP3 „110“ und für IMAP „143“. Ist SSL aktiviert, ist der Standardwert für POP3 „995“ und für IMAP „993“.
* **inboxProtocol**: Das E-Mail-Protokoll für den E-Mail-Endpunkt, der zum Überprüfen des Posteingangs verwendet wird. Die Optionen sind `IMAP` oder `POP3`. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.
* **inboxTimeOut**: Zeitüberschreitung in Sekunden, bis der E-Mail-Anbieter auf Posteingangsantworten wartet. Der Standardwert ist 60. 
* **inboxUser**: Der Benutzername, der zum Anmelden beim E-Mail-Konto erforderlich ist. Je nach E-Mail-Server und Konfiguration kann dies nur der Benutzernamenteil der E-Mail-Adresse oder die vollständige E-Mail-Adresse sein.
* **inboxPassword**: Das Kennwort für den Posteingangsbenutzer.
* **inboxSSLEnabled**: Legen Sie diesen Wert fest, um den E-Mail-Anbieter zu zwingen, SSL zu verwenden, wenn Benachrichtigungen über Ergebnisse oder Fehler gesendet werden. Stellen Sie sicher, dass der IMAP- oder POP3-Host SSL unterstützt.
* **smtpHost**: Der Hostname des E-Mail-Servers, an den der E-Mail-Anbieter Ergebnisse und Fehlermeldungen sendet.
* **smtpPort**: Der Standardwert für den SMTP-Anschluss ist 25.
* **smtpUser**: Das Benutzerkonto, das vom E-Mail-Anbieter verwendet werden soll, wenn E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern gesendet werden.
* **smtpPassword**: Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.
* **charSet**: Der vom E-Mail-Anbieter verwendete Zeichensatz. Der Standardwert ist `UTF-8`.
* **smtpSSLEnabled**: Legen Sie diesen Wert fest, um den E-Mail-Anbieter zu zwingen, SSL zu verwenden, wenn Benachrichtigungen über Ergebnisse oder Fehler gesendet werden. Stellen Sie sicher, dass der SMTP-Host SSL unterstützt.
* **failedJobFolder**: Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, wenn der SMTP-Mail-Server nicht betriebsbereit ist.
* **asynchron**: Wenn &quot;synchron&quot;festgelegt ist, werden alle Eingabedateien verarbeitet und eine einzige Antwort zurückgegeben. Bei Festlegung auf &quot;asynchron&quot;wird für jedes verarbeitete Eingabedatum eine Antwort gesendet. Beispielsweise wird ein E-Mail-Endpunkt für den in diesem Thema eingestellten Prozess erstellt und eine E-Mail-Nachricht an den Posteingang des Endpunkts gesendet, die mehrere ungesicherte PDF-Dokumente enthält. Wenn alle PDF-Dokumente mit einem Kennwort verschlüsselt sind und der Endpunkt als synchron konfiguriert ist, wird eine einzige E-Mail-Antwort mit allen geschützten PDF-Dokumenten gesendet. Wenn der Endpunkt als asynchron konfiguriert ist, wird für jedes geschützte PDF-Dokument eine separate E-Mail-Antwort gesendet. Jede E-Mail-Nachricht enthält ein einzelnes PDF-Dokument als Anlage. Der Standardwert ist „asynchron“.

**Definieren von Eingabeparameterwerten**

Beim Erstellen eines E-Mail-Endpunkts müssen Sie Eingabeparameterwerte definieren. Das heißt, Sie müssen die Eingabewerte beschreiben, die an den Vorgang übergeben werden, der vom E-Mail-Endpunkt aufgerufen wird. Betrachten Sie zum Beispiel den in diesem Thema eingeführten Prozess. Es hat einen Eingabewert mit dem Namen `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Wenn Sie einen E-Mail-Endpunkt für diesen Prozess erstellen (nachdem ein Prozess aktiviert wurde, wird er zu einem Dienst), müssen Sie den Eingabeparameterwert definieren.

Geben Sie die folgenden Werte an, um die für einen E-Mail-Endpunkt erforderlichen Eingabeparameterwerte zu definieren:

**Name** des Eingabeparameters: Der Name des Eingabeparameters. Der Name eines Eingabewerts wird in Workbench für einen Prozess angegeben. Wenn der Eingabewert zu einem Dienstvorgang gehört (einem Forms-Dienst, der nicht in Workbench erstellt wurde), wird der Eingabename in der Datei component.xml angegeben. Beispielsweise lautet der Name des Eingabeparameters für den in diesem Abschnitt eingeführten Prozess `InDoc`.

**Zuordnungstyp**: Dient zum Konfigurieren der zum Aufrufen des Dienstvorgangs erforderlichen Eingabewerte. Es gibt zwei Arten von Zuordnungstypen:

* `Literal`: Der E-Mail-Endpunkt verwendet den in das Feld eingegebenen Wert, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, Long, Int oder Boolean verwendet, wird die Zeichenfolge in einen ordnungsgemäßen Typ konvertiert und der Dienst aufgerufen.
* `Variable`: Der eingegebene Wert ist ein Dateimuster, das vom E-Mail-Endpunkt zum Auswählen der Eingabe verwendet wird. Wenn Sie beispielsweise Variable für den Zuordnungstyp auswählen und das Eingabedateien eine PDF-Dokument sein muss, können Sie `*.pdf` als Zuordnungswert angeben.

**Zuordnungswert**: Gibt den Wert des Zuordnungstyps an. Wenn Sie beispielsweise einen Variablenzuordnungstyp auswählen, können Sie `*.pdf` als Dateimuster angeben.

**Datentyp**: Gibt den Datentyp der Eingabewerte an. Der Datentyp des Eingabewerts des in diesem Abschnitt eingeführten Prozesses ist beispielsweise com.adobe.idp.Dokument.

**Definieren eines Ausgabeparameterwerts**

Beim Erstellen eines E-Mail-Endpunkts müssen Sie einen Ausgabeparameterwert definieren. Das heißt, Sie müssen den Ausgabewert beschreiben, der von dem Dienst zurückgegeben wird, der vom E-Mail-Endpunkt aufgerufen wird. Betrachten Sie zum Beispiel den in diesem Thema eingeführten Prozess. Es hat einen Ausgabewert mit dem Namen `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`. Wenn Sie einen E-Mail-Endpunkt für diesen Prozess erstellen (nachdem ein Prozess aktiviert wurde, wird er zu einem Dienst), müssen Sie den Wert des Ausgabeparameters definieren.

Um einen für einen E-Mail-Endpunkt erforderlichen Ausgabeparameterwert zu definieren, geben Sie die folgenden Werte an:

**Name** des Ausgabeparameters: Der Name des Ausgabeparameters. Der Name eines Prozessausgabewerts wird in Workbench angegeben. Wenn der Ausgabewert zu einem Dienstvorgang gehört (einem Dienst, der nicht in Workbench erstellt wurde), wird der Ausgabename in der Datei component.xml angegeben. Beispielsweise lautet der Name des Ausgabeparameters für den in diesem Abschnitt eingeführten Prozess `SecuredDoc`.

**Zuordnungstyp**: Dient zum Konfigurieren der Ausgabe des Dienstes und Vorgangs. Die folgenden Optionen sind verfügbar:

* Wenn der Dienst ein einzelnes Objekt (ein einzelnes Dokument) zurückgibt, ist das Muster `%F.pdf` und das Quellziel ist sourcefilename.pdf. Beispielsweise gibt der in diesem Abschnitt eingeführte Prozess ein einzelnes Dokument zurück. Daher kann der Zuordnungstyp als `%F.pdf` definiert werden ( `%F` bedeutet, dass Sie den angegebenen Dateinamen verwenden). Das Muster `%E` gibt die Erweiterung des Eingabe-Dokuments an.
* Wenn der Dienst eine Liste zurückgibt, lautet das Muster `Result\%F\` und das Quellziel lautet Result\sourcefilename\source1 (output 1) und Result\sourcefilename\source2 (output 2).
* Wenn der Dienst eine Zuordnung zurückgibt, ist das Muster `Result\%F\` und das Quellziel ist Result\sourcefilename\file1 and Result\sourcefilename\file2. Wenn die Map über mehr als ein Objekt verfügt, ist das Muster `Result\%F.pdf` und das Quellziel lautet Result\sourcefilename1.pdf (Ausgabe 1), Result\sourcefilenam2.pdf (Ausgabe 2) usw.

**Datentyp**: Gibt den Datentyp des Rückgabewerts an. Der Datentyp des Rückgabewerts des in diesem Abschnitt eingeführten Prozesses ist beispielsweise `com.adobe.idp.Document`.

**E-Mail-Endpunkt erstellen**

Nachdem Sie die E-Mail-Endpunktattribute und Konfigurationswerte festgelegt und Eingabe- und Ausgabeparameterwerte definiert haben, müssen Sie den E-Mail-Endpunkt erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen E-Mail-Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Dienstes verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console Ansicht haben.

**Siehe auch**

[hinzufügen eines E-Mail-Endpunkts mit der Java-API](programmatically-endpoints.md#add-an-email-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen eines E-Mail-Endpunkts mit der Java-API {#add-an-email-endpoint-using-the-java-api}

hinzufügen eines E-Mail-Endpunkts mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von E-Mail-Endpunktattributen.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `Email` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOperationName` aufrufen und einen Zeichenfolgenwert übergeben, der den Vorgangsnamen angibt. Beim Erstellen eines E-Mail-Endpunkts für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, wird normalerweise der Name des Vorgangs aufgerufen.

1. Geben Sie Konfigurationswerte an.

   Damit jeder Konfigurationswert für den E-Mail-Endpunkt festgelegt wird, müssen Sie die `setConfigParameterAsText`-Methode des Objekts aufrufen. `CreateEndpointInfo` Um beispielsweise den Konfigurationswert `smtpHost` festzulegen, rufen Sie die `CreateEndpointInfo`-Methode des Objekts `setConfigParameterAsText` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Geben Sie beim Festlegen des Konfigurationswerts `smtpHost` `smtpHost` an.
   * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Geben Sie beim Festlegen des Konfigurationswerts `smtpHost` einen Zeichenfolgenwert an, der den Namen des SMTP-Servers angibt.

   >[!NOTE]
   >
   >Um alle in diesem Abschnitt eingeführten Konfigurationswerte für den EncryptDocument-Dienst anzuzeigen, finden Sie im Java-Codebeispiel unter [QuickStart: Hinzufügen eines E-Mail-Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api).

1. Definieren Sie Eingabeparameterwerte.

   Definieren Sie einen Eingabeparameterwert, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setInputParameterMapping` aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Eingabeparameters angibt. Beispielsweise lautet der Name des Eingabeparameters für den EncryptDocument-Dienst `InDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Eingabeparameters angibt. Der Datentyp des Eingabeparameters `InDoc` lautet beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `variable` angeben.
   * Ein Zeichenfolgenwert, der den Wert des Zuordnungstyps angibt. Sie können beispielsweise &amp;ast;.pdf als Dateimuster angeben.

   >[!NOTE]
   >
   >Rufen Sie die `setInputParameterMapping`-Methode für jeden zu definierenden Eingabeparameterwert auf. Da der EncryptDocument-Prozess nur einen Eingabeparameter hat, müssen Sie diese Methode einmal aufrufen.

1. Definieren Sie einen Ausgabeparameterwert.

   Definieren Sie einen Ausgabeparameterwert, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOutputParameterMapping` aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Ausgabeparameters angibt. Beispielsweise lautet der Name des Ausgabeparameters für den EncryptDocument-Dienst `SecuredDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Ausgabeparameters angibt. Der Datentyp des Ausgabeparameters `SecuredDoc` lautet beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `%F.pdf` angeben.

1. Erstellen Sie den E-Mail-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den E-Mail-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `enable` aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines Endpunkts für einen überwachten Ordner mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Email-Konfigurationswerte Konstante Datei {#email-configuration-values-constant-file}

Der [QuickStart: Beim Hinzufügen eines E-Mail-Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api) wird eine Konstantendatei verwendet, die Teil Ihres Java-Projekts sein muss, um den schnellen Beginn zu kompilieren. Diese Konstantendatei stellt Konfigurationswerte dar, die beim Hinzufügen eines E-Mail-Endpunkts festgelegt werden müssen. Der folgende Java-Code stellt die Konstantendatei dar.

```java
 /**
     * This class contains constants that can be used when setting email endpoint
     * configuration values
     */
 public class EmailEndpointConfigConstants {

     public static final String PROPERTY_EMAILPROVIDER_CRON_EXPRESSION = "cronExpression";
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_COUNT = "repeatCount";
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_INTERVAL = "repeatInterval";
     public static final String PROPERTY_EMAILPROVIDER_START_DELAY = "startDelay";
     public static final String PROPERTY_EMAILPROVIDER_BATCH_SIZE = "batchSize";
     public static final String PROPERTY_EMAILPROVIDER_USERNAME = "userName";
     public static final String PROPERTY_EMAILPROVIDER_DOMAINNAME = "domainName";
     public static final String PROPERTY_EMAILPROVIDER_DOMAINPATTERN = "domainPattern";
     public static final String PROPERTY_EMAILPROVIDER_FILEPATTERN = "filePattern";
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_SUCCESSFUL_JOB = "recipientSuccessfulJob";
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_FAILED_JOB = "recipientFailedJob";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_HOST = "inboxHost";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PORT = "inboxPort";
     public static final String PROPERTY_EMAILPROVIDER_PROTOCOL = "inboxProtocol";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_TIMEOUT = "inboxTimeOut";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_USER = "inboxUser";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PASSWORD = "inboxPassword";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_SSL = "inboxSSLEnabled";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_HOST = "smtpHost";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PORT = "smtpPort";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_USER = "smtpUser";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PASSWORD = "smtpPassword";
     public static final String PROPERTY_EMAILPROVIDER_CHARSET = "charSet";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_SSL = "smtpSSLEnabled";
     public static final String PROPERTY_EMAILPROVIDER_FAILED_FOLDER = "failedJobFolder";
     public static final String PROPERTY_EMAILPROVIDER_ASYNCHRONOUS = "asynchronous";
 }
```

## Remoting-Endpunkte {#adding-remoting-endpoints} hinzufügen

>[!NOTE]
>
>LiveCycle Remoting-APIs für AEM Forms on JEE nicht mehr unterstützt.

Sie können einem Dienst programmgesteuert einen Remoting-Endpunkt hinzufügen, indem Sie die AEM Forms Java API verwenden. Durch Hinzufügen eines Remoting-Endpunkts aktivieren Sie eine Flex-Anwendung, um den Dienst mithilfe von Remoting aufzurufen. (Siehe [Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Zum programmgesteuerten Hinzufügen eines Remoting-Endpunkts zu einem Dienst sollten Sie den folgenden Prozess mit kurzer Lebensdauer mit dem Namen *EncryptDocument* in Erwägung ziehen.

![ar_ar_encryptdocumentprocess](assets/ar_ar_encryptdocumentprocess.png)

Bei diesem Vorgang wird ein unbesichertes PDF-Dokument als Eingabewert akzeptiert und anschließend das unbesicherte PDF-Dokument an den Vorgang `EncryptPDFUsingPassword` des Encryption-Dienstes weitergegeben. Das PDF-Dokument wird mit einem Kennwort verschlüsselt, und das kennwortverschlüsselte PDF-Dokument ist der Ausgabewert dieses Vorgangs. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) ist `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (kennwortverschlüsseltes PDF-Dokument) ist `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

Um zu zeigen, wie ein Remoting-Endpunkt zu einem Dienst hinzugefügt wird, wird in diesem Abschnitt ein Remoting-Endpunkt zu einem Dienst namens EncryptDocument hinzugefügt.

>[!NOTE]
>
>Mit Webdiensten können Sie keinen Remoting-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entfernen Sie einen Endpunkt aus einem Dienst:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Festlegen von Remoting-Endpunktattributen.
1. Erstellen Sie einen Remoting-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Um einen Remoting-Endpunkt programmgesteuert hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Remoting-Endpunktattribute festlegen**

Um einen Remoting-Endpunkt für einen Dienst zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID-Wert**: Gibt den Typ des erstellten Endpunkts an. Um einen Remoting-Endpunkt zu erstellen, geben Sie `Remoting` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Dienst-ID-Wert**: Gibt den Dienst an, zu dem der Endpunkt gehört. Um beispielsweise dem in diesem Abschnitt eingeführten Prozess einen Remoting-Endpunkt hinzuzufügen (ein Prozess wird zu einem Dienst, wenn er in Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines Remoting-Endpunkts ein Platzhalterzeichen (&amp;ast;) ein.

**Remoting-Endpunkt erstellen**

Nachdem Sie Remoting-Endpunktattribute festgelegt haben, können Sie einen Remoting-Endpunkt für einen Dienst erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn ein Remoting-Endpunkt aktiviert ist, aktiviert er einen Flex-Client, um den Dienst aufzurufen.

**Siehe auch**

[hinzufügen eines Remoting-Endpunkts mit der Java-API](programmatically-endpoints.md#add-a-remoting-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen eines Remoting-Endpunkts mit der Java-API {#add-a-remoting-endpoint-using-the-java-api}

hinzufügen eines Remoting-Endpunkts mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von Remoting-Endpunktattributen.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `Remoting` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie den Vorgang an, der von der `CreateEndpointInfo`-Methode des Objekts `setOperationName` aufgerufen wird, und übergeben Sie einen Zeichenfolgenwert, der den Vorgangsnamen angibt. Geben Sie für einen Remoting-Endpunkt ein Platzhalterzeichen (&amp;ast;) an.

1. Erstellen Sie einen Remoting-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen Remoting-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `enable` aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines Remoting-Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Hinzufügen von TaskManager-Endpunkten {#adding-taskmanager-endpoints}

Sie können einem Dienst programmgesteuert einen TaskManager-Endpunkt hinzufügen, indem Sie die AEM Forms Java API verwenden. Indem Sie einem Dienst einen TaskManager-Endpunkt hinzufügen, aktivieren Sie einen Workspace-Benutzer, um den Dienst aufzurufen. Das heißt, ein in Workspace arbeitender Benutzer kann einen Prozess aufrufen, der über einen entsprechenden TaskManager-Endpunkt verfügt.

>[!NOTE]
>
>Mit Webdiensten können Sie keinen TaskManager-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-5}

So fügen Sie einem Dienst einen TaskManager-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Erstellen Sie eine Kategorie für den Endpunkt.
1. Legen Sie TaskManager-Endpunktattribute fest.
1. Erstellen Sie einen TaskManager-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Bevor Sie einen TaskManager-Endpunkt programmgesteuert hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Kategorie für den Endpunkt erstellen**

Kategorien werden verwendet, um Dienste in Workspace zu organisieren. Das heißt, ein Workspace-Benutzer kann einen Dienst mit einem TaskManager-Endpunkt aufrufen, indem er eine Kategorie in Workspace auswählt. Beim Erstellen eines TaskManager-Endpunkts können Sie entweder auf eine vorhandene Kategorie verweisen oder programmgesteuert eine neue Kategorie erstellen.

>[!NOTE]
>
>In diesem Abschnitt wird eine neue Kategorie erstellt, um einem Dienst einen TaskManager-Endpunkt hinzuzufügen.

**TaskManager-Endpunktattribute festlegen**

Um einen TaskManager-Endpunkt für einen Dienst zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID**: Gibt den Typ des erstellten Endpunkts an. Um einen TaskManager-Endpunkt zu erstellen, geben Sie `TaskManagerConnector` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Dienstkennung**: Gibt den Dienst an, zu dem der Endpunkt gehört.
* **Kategorie**: Gibt einen Kategorien-ID-Wert an, der mit dem TaskManager-Endpunkt verknüpft ist.
* **Vorgangsname**: Beim Erstellen eines TaskManager-Endpunkts für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs normalerweise  `invoke`.

**TaskManager-Endpunkt erstellen**

Nachdem Sie die TaskManager-Endpunktattribute festgelegt haben, können Sie einen TaskManager-Endpunkt für einen Dienst erstellen.

**Endpunkt aktivieren**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Dienstes in Workspace verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console Ansicht haben.

**Siehe auch**

[hinzufügen eines TaskManager-Endpunkts mit der Java-API](programmatically-endpoints.md#add-a-taskmanager-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen eines TaskManager-Endpunkts mit der Java-API {#add-a-taskmanager-endpoint-using-the-java-api}

hinzufügen eines TaskManager-Endpunkts mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Erstellen Sie eine Kategorie für den Endpunkt.

   * Erstellen Sie ein `CreateEndpointCategoryInfo`-Objekt, indem Sie den Konstruktor verwenden und die folgenden Werte übergeben:

      * Ein Zeichenfolgenwert, der den ID-Wert der Kategorie angibt
      * Ein Zeichenfolgenwert, der die Beschreibung der Kategorie angibt
   * Erstellen Sie die Kategorie, indem Sie die `EndpointRegistryClient`-Objektmethode `createEndpointCategory` aufrufen und das `CreateEndpointCategoryInfo`-Objekt übergeben. Diese Methode gibt ein `EndpointCategory`-Objekt zurück, das die neue Kategorie darstellt.


1. Legen Sie TaskManager-Endpunktattribute fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Connector-ID-Wert an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setConnectorId` aufrufen und den Zeichenfolgenwert `TaskManagerConnector` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setDescription` aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setName` aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Dienst an, zu dem der Endpunkt gehört, indem Sie die `setServiceId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Dienstnamen angibt.`CreateEndpointInfo`
   * Geben Sie die Kategorie an, zu der der Endpunkt gehört, indem Sie die `setCategoryId`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Kategorien-ID-Wert angibt. `CreateEndpointInfo` Sie können die `EndpointCategory`-Objektmethode `getId` aufrufen, um den Bezeichnerwert dieser Kategorie abzurufen.
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die `CreateEndpointInfo`-Methode des Objekts `setOperationName` aufrufen und einen Zeichenfolgenwert übergeben, der den Vorgangsnamen angibt. Beim Erstellen eines `TaskManager`-Endpunkts für einen Dienst, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs in der Regel `invoke`.

1. Erstellen Sie einen TaskManager-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `createEndpoint` aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen TaskManager-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `enable` aufrufen und das `Endpoint`-Objekt übergeben, das von der `createEndpoint`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Hinzufügen eines TaskManager-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Endpunkte ändern {#modifying-endpoints}

Sie können einen vorhandenen Endpunkt programmgesteuert mithilfe der AEM Forms Java API ändern. Durch Ändern eines Endpunkts können Sie das Verhalten des Endpunkts ändern. Betrachten Sie beispielsweise einen Endpunkt des Typs &quot;Überwachter Ordner&quot;, der einen Ordner angibt, der als überwachter Ordner verwendet wird. Sie können Konfigurationswerte, die zum Endpunkt des Typs &quot;Überwachter Ordner&quot;gehören, programmgesteuert ändern, sodass ein anderer Ordner als überwachter Ordner funktioniert. Weitere Informationen zu Konfigurationswerten, die zu einem Endpunkt des Typs &quot;Überwachter Ordner&quot;gehören, finden Sie unter [Hinzufügen von Endpunkten für überwachte Ordner](programmatically-endpoints.md#adding-watched-folder-endpoints).

Um zu zeigen, wie ein Endpunkt geändert wird, ändert dieser Abschnitt einen Endpunkt des Typs &quot;Überwachter Ordner&quot;, indem der Ordner geändert wird, der sich wie der überwachte Ordner verhält.

>[!NOTE]
>
>Sie können einen Endpunkt nicht mithilfe von Webdiensten ändern.

### Zusammenfassung der Schritte {#summary_of_steps-6}

So ändern Sie einen Endpunkt:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Rufen Sie den Endpunkt ab.
1. Geben Sie neue Konfigurationswerte an.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Um einen Endpunkt programmgesteuert zu ändern, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Abrufen des zu ändernden Endpunkts**

Bevor Sie einen Endpunkt ändern können, müssen Sie ihn abrufen. Um einen Endpunkt abzurufen, müssen Sie eine Verbindung als Benutzer herstellen, der auf einen Endpunkt zugreifen kann. Es wird empfohlen, eine Verbindung als Administrator herzustellen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Sie können einen Endpunkt abrufen, indem Sie eine Liste von Endpunkten abrufen. Anschließend können Sie die Liste durchlaufen und nach dem zu entfernenden Endpunkt suchen. Sie können beispielsweise einen Endpunkt suchen, indem Sie den Dienst festlegen, der dem Endpunkt und dem Endpunkttyp entspricht. Wenn Sie den Endpunkt suchen, können Sie ihn ändern.

**Geben Sie neue Konfigurationswerte an**

Geben Sie beim Ändern eines Endpunkts neue Konfigurationswerte an. Um beispielsweise einen Endpunkt des Typs &quot;Überwachter Ordner&quot;zu ändern, setzen Sie alle Konfigurationswerte des Endpunkts &quot;Überwachter Ordner&quot;zurück, nicht nur die, die Sie ändern möchten. Weitere Informationen zu Konfigurationswerten, die zu einem Endpunkt des Typs &quot;Überwachter Ordner&quot;gehören, finden Sie unter [Hinzufügen von Endpunkten für überwachte Ordner](programmatically-endpoints.md#adding-watched-folder-endpoints).

>[!NOTE]
>
>Weitere Informationen zu Konfigurationswerten, die zu einem E-Mail-Endpunkt gehören, finden Sie unter [Hinzufügen von E-Mail-Endpunkten](programmatically-endpoints.md#adding-email-endpoints).

>[!NOTE]
>
>Sie können den Dienst, der vom Endpunkt aufgerufen wird, nicht ändern. Wenn Sie versuchen, den Dienst zu ändern, wird eine Ausnahme ausgelöst. Um den einem bestimmten Endpunkt zugeordneten Dienst zu ändern, entfernen Sie den Endpunkt und erstellen Sie einen neuen. (Siehe [Entfernen von Endpunkten](programmatically-endpoints.md#removing-endpoints).)

**Siehe auch**

[Ändern eines Endpunkts mit der Java-API](programmatically-endpoints.md#modifying-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ändern eines Endpunkts mit der Java-API {#modifying-an-endpoint-using-the-java-api}

Ändern Sie einen Endpunkt mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den zu ändernden Endpunkt ab.

   * Rufen Sie eine Liste aller Endpunkte ab, auf die der aktuelle Benutzer (in den Verbindungseigenschaften angegeben) zugreifen kann, indem Sie die `getEndpoints`-Objektmethode aufrufen und ein `PagingFilter`-Objekt übergeben, das als Filter fungiert. `EndpointRegistryClient` Sie können einen `(PagingFilter)null`-Wert übergeben, um alle Endpunkte zurückzugeben. Diese Methode gibt ein `java.util.List`-Objekt zurück, wobei jedes Element ein `Endpoint`-Objekt ist. Weitere Informationen zu einem `PagingFilter`-Objekt finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Durchlaufen Sie das `java.util.List`-Objekt, um zu ermitteln, ob es Endpunkte enthält. Wenn Endpunkte vorhanden sind, ist jedes Element eine `EndPoint`-Instanz.
   * Stellen Sie den Dienst fest, der einem Endpunkt entspricht, indem Sie die `EndPoint`-Methode des Objekts `getServiceId` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Dienstnamen angibt.
   * Bestimmen Sie den Typ des Endpunkts, indem Sie die `EndPoint`-Methode des Objekts `getConnectorId` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Typ des Endpunkts angibt. Wenn der Endpunkt beispielsweise ein Endpunkt des Typs &quot;Überwachter Ordner&quot;ist, gibt diese Methode `WatchedFolder` zurück.

1. Geben Sie neue Konfigurationswerte an.

   * Erstellen Sie ein `ModifyEndpointInfo`-Objekt, indem Sie den Konstruktor aufrufen.
   * Rufen Sie für jeden festzulegenden Konfigurationswert die `ModifyEndpointInfo`-Methode des Objekts `setConfigParameterAsText` auf. Um beispielsweise den URL-Konfigurationswert festzulegen, rufen Sie die `ModifyEndpointInfo`-Methode des Objekts `setConfigParameterAsText` auf und übergeben Sie die folgenden Werte:

      * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Um beispielsweise den Konfigurationswert `url` festzulegen, geben Sie `url` an.
      * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Um einen Wert für den Konfigurationswert `url` zu definieren, geben Sie den Speicherort des überwachten Ordners an.
   * Rufen Sie die `modifyEndpoint`-Methode des Objekts auf und übergeben Sie das `ModifyEndpointInfo`-Objekt.`EndpointRegistryClient`


**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Ändern eines Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Entfernen von Endpunkten {#removing-endpoints}

Sie können einen Endpunkt programmgesteuert aus einem Dienst entfernen, indem Sie die AEM Forms Java API verwenden. Nachdem Sie einen Endpunkt entfernt haben, kann der Dienst nicht mit der vom Endpunkt aktivierten Aufrufmethode aufgerufen werden. Wenn Sie beispielsweise einen SOAP-Endpunkt aus einem Dienst entfernen, können Sie den Dienst nicht im SOAP-Modus aufrufen.

Um zu demonstrieren, wie ein Endpunkt aus einem Dienst entfernt wird, entfernt dieser Abschnitt einen EJB-Endpunkt aus einem Dienst mit dem Namen *EncryptDocument*.

>[!NOTE]
>
>Ein Endpunkt kann nicht mithilfe von Webdiensten entfernt werden.

### Zusammenfassung der Schritte {#summary_of_steps-7}

So entfernen Sie einen Endpunkt aus einem Dienst:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Rufen Sie den Endpunkt ab.
1. Entfernen Sie den Endpunkt.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**EndpointRegistry Client-Objekt erstellen**

Um einen Endpunkt programmgesteuert zu entfernen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Den zu entfernenden Endpunkt abrufen**

Bevor Sie einen Endpunkt entfernen können, müssen Sie ihn abrufen. Um einen Endpunkt abzurufen, müssen Sie eine Verbindung als Benutzer herstellen, der auf einen Endpunkt zugreifen kann. Es wird empfohlen, eine Verbindung als Administrator herzustellen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Sie können einen Endpunkt abrufen, indem Sie eine Liste von Endpunkten abrufen. Anschließend können Sie die Liste durchlaufen und nach dem zu entfernenden Endpunkt suchen. Sie können beispielsweise einen Endpunkt suchen, indem Sie den Dienst festlegen, der dem Endpunkt und dem Endpunkttyp entspricht. Wenn Sie den Endpunkt suchen, können Sie ihn entfernen.

**Endpunkt entfernen**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Dienstes verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in Administration Console Ansicht haben.

**Siehe auch**

[Entfernen eines Endpunkts mit der Java-API](programmatically-endpoints.md#removing-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen eines Endpunkts mit der Java-API {#removing-an-endpoint-using-the-java-api}

Entfernen Sie einen Endpunkt mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den zu entfernenden Endpunkt ab.

   * Rufen Sie eine Liste aller Endpunkte ab, auf die der aktuelle Benutzer (in den Verbindungseigenschaften angegeben) zugreifen kann, indem Sie die `getEndpoints`-Objektmethode aufrufen und ein `PagingFilter`-Objekt übergeben, das als Filter fungiert. `EndpointRegistryClient` Sie können `(PagingFilter)null` übergeben, um alle Endpunkte zurückzugeben. Diese Methode gibt ein `java.util.List`-Objekt zurück, wobei jedes Element ein `Endpoint`-Objekt ist.
   * Durchlaufen Sie das `java.util.List`-Objekt, um zu ermitteln, ob es Endpunkte enthält. Wenn Endpunkte vorhanden sind, ist jedes Element eine `EndPoint`-Instanz.
   * Stellen Sie den Dienst fest, der einem Endpunkt entspricht, indem Sie die `EndPoint`-Methode des Objekts `getServiceId` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Dienstnamen angibt.
   * Bestimmen Sie den Typ des Endpunkts, indem Sie die `EndPoint`-Methode des Objekts `getConnectorId` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Typ des Endpunkts angibt. Wenn der Endpunkt beispielsweise ein EJB-Endpunkt ist, gibt diese Methode `EJB` zurück.

1. Entfernen Sie den Endpunkt.

   Entfernen Sie den Endpunkt, indem Sie die `EndpointRegistryClient`-Methode des Objekts `remove` aufrufen und das `EndPoint`-Objekt übergeben, das den zu entfernenden Endpunkt darstellt.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Entfernen eines Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Abrufen von Endpunkt-Connector-Informationen {#retrieving-endpoint-connector-information}

Mit der AEM Forms API können Sie programmgesteuert Informationen zu Endpunktschnittstellen abrufen. Ein Connector ermöglicht es einem Endpunkt, einen Dienst mit verschiedenen Aufrufmethoden aufzurufen. Ein Connector für überwachte Ordner ermöglicht es beispielsweise einem Endpunkt, einen Dienst mit überwachten Ordnern aufzurufen. Durch programmgesteuertes Abrufen von Informationen zu Endpunktschnittstellen können Sie Konfigurationswerte abrufen, die mit einem Connector verknüpft sind, z. B. welche Konfigurationswerte erforderlich sind und welche optional sind.

In diesem Abschnitt wird veranschaulicht, wie Informationen zu Endpunktschnittstellen abgerufen werden, und es werden Informationen zu einem Connector für überwachte Ordner abgerufen. (Siehe [Hinzufügen von Endpunkten für überwachte Ordner](programmatically-endpoints.md#adding-watched-folder-endpoints).)

>[!NOTE]
>
>Mit Webdiensten können Sie keine Informationen zu Endpunkten abrufen.

>[!NOTE]
>
>Dieses Thema verwendet die API `ConnectorRegistryClient`, um Informationen zu Endpunktschnittstellen abzurufen. (Siehe [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

### Zusammenfassung der Schritte {#summary_of_steps-8}

So rufen Sie Endpunktschnittstelleninformationen ab:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `ConnectorRegistryClient`-Objekt.
1. Geben Sie den Connector-Typ an.
1. Rufen Sie Konfigurationswerte ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, ersetzen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**ConnectorRegistry-Client-Objekt erstellen**

Um Endpunktschnittstelleninformationen programmgesteuert abzurufen, erstellen Sie ein `ConnectorRegistryClient`-Objekt.

**Angeben des Connector-Typs**

Geben Sie den Connector-Typ an, von dem Informationen abgerufen werden sollen. Die folgenden Arten von Connectors sind vorhanden:

* **EJB**: Aktiviert eine Clientanwendung, um einen Dienst im EJB-Modus aufzurufen.
* **SOAP**: Aktiviert eine Clientanwendung, um einen Dienst im SOAP-Modus aufzurufen.
* **Überwachter Ordner**: Aktiviert überwachte Ordner zum Aufrufen eines Dienstes.
* **E-Mail**: Aktiviert E-Mail-Nachrichten zum Aufrufen eines Dienstes.
* **Remoting**: Aktiviert eine Flex-Clientanwendung zum Aufrufen eines Dienstes.
* **TaskManagerConnector**: Ermöglicht einem Workspace-Benutzer, einen Dienst aus Workspace aufzurufen.

**Konfigurationswerte abrufen**

Nachdem Sie den Connector-Typ angegeben haben, können Sie Informationen zum Connector abrufen, z. B. den unterstützten Konfigurationswert. Beispielsweise können Sie für jeden Connector festlegen, welche Konfigurationswerte erforderlich und welche optional sind.

**Siehe auch**

[Abrufen von Endpunktschnittstellenverbindungsinformationen mit der Java-API](programmatically-endpoints.md#retrieve-endpoint-connector-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Endpunktschnittstellenverbindungsinformationen mit der Java-API {#retrieve-endpoint-connector-information-using-the-java-api}

Rufen Sie Endpunktschnittstellenverbindungsinformationen mithilfe der Java-API ab:

1. Schließen Sie Projektdateien ein. .

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-livecycle-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein ConnectorRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConnectorRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Geben Sie den Connector-Typ an.

   Geben Sie den Connector-Typ an, indem Sie die `ConnectorRegistryClient`-Methode des Objekts `getEndpointDefinition` aufrufen und einen Zeichenfolgenwert übergeben, der den Connector-Typ angibt. Um beispielsweise den Connector-Typ für den überwachten Ordner anzugeben, übergeben Sie den Zeichenfolgenwert `WatchedFolder`. Diese Methode gibt ein `Endpoint`-Objekt zurück, das dem Connector-Typ entspricht.

1. Rufen Sie Konfigurationswerte ab.

   * Rufen Sie Konfigurationswerte ab, die mit diesem Endpunkt verknüpft sind, indem Sie die `getConfigParameters`-Methode des Objekts aufrufen. `Endpoint` Diese Methode gibt ein Array von `ConfigParameter`-Objekten zurück.
   * Rufen Sie Informationen zu jedem Konfigurationswert ab, indem Sie die einzelnen Elemente im Array abrufen. Jedes Element ist ein `ConfigParameter`-Objekt. Sie können beispielsweise bestimmen, ob der Konfigurationswert erforderlich oder optional ist, indem Sie die `isRequired`-Methode des Objekts aufrufen. `ConfigParameter` Wenn der Konfigurationswert erforderlich ist, gibt diese Methode `true` zurück.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Abrufen von Endpunktschnittstellenverbindungsinformationen mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
