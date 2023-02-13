---
title: Programmgesteuertes Verwalten von Endpunkten
seo-title: Programmatically Managing Endpoints
description: Verwenden Sie den Dienst „Endpoint Registry“, um EJB-Endpunkte hinzuzufügen, SOAP-Endpunkte hinzuzufügen, Endpunkte für überwachte Ordner hinzuzufügen, E-Mail-Endpunkte hinzuzufügen, Remoting-Endpunkte hinzuzufügen, Task Manager-Endpunkte hinzuzufügen, Endpunkte zu ändern, Endpunkte zu entfernen und Endpunkt-Connector-Informationen abzurufen.
seo-description: Use the Endpoint Registry service to add EJB endpoints, add SOAP endpoint, add Watched Folder endpoints, add Email endpoints, add  Remoting endpoints, add Task Manager endpoints, modify endpoints, remove endpoints, and retrieve endpoint connector information.
uuid: 5dc50946-3323-4c5d-a43b-31c1c980bd04
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 076889a7-9c9f-4b6f-a45b-67a9b3923c36
role: Developer
exl-id: b94dcca2-136b-4b7d-b5ce-544804575876
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: ht
source-wordcount: '10805'
ht-degree: 100%

---

# Programmgesteuertes Verwalten von Endpunkten {#programmatically-managing-endpoints}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Endpoint Registry-Service**

Der Endpoint Registry-Service bietet die Möglichkeit, Endpunkte programmgesteuert zu verwalten. Sie können beispielsweise die folgenden Typen von Endpunkten zu einem Service hinzufügen:

* EJB
* SOAP
* Überwachter Ordner
* E-Mail
* (Veraltet für AEM Forms) Remoting
* Task Manager

>[!NOTE]
>
>SOAP-, EJB- und (für AEM Forms auf JEE nicht mehr unterstützt) Remoting-Endpunkte werden automatisch für jeden aktivierten Service erstellt. Die SOAP- und EJB-Endpunkte aktivieren SOAP und EJB für alle Service-Vorgänge.

Ein Remoting-Endpunkt ermöglicht es Flex-Clients, Vorgänge für den AEM Forms-Service aufzurufen, zu dem der Endpunkt hinzugefügt wird. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt, und Flex-Clients können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Service aufzurufen.

Die Endpunkte „E-Mail“, „Task Manager“ und „Überwachter Ordner“ stellen nur einen bestimmten Vorgang des Services zur Verfügung. Das Hinzufügen dieser Endpunkte erfordert einen zweiten Konfigurationsschritt, um eine aufzurufende Methode auszuwählen, Konfigurationsparameter festzulegen und Zuordnungen von Eingabe- und Ausgabeparametern anzugeben.

Sie können TaskManager-Endpunkte in Gruppen namens *Kategorien* organisieren. Diese Kategorien werden dann über TaskManager für Workspace verfügbar gemacht, wobei die Endbenutzer die TaskManager-Endpunkte entsprechend ihrer Kategorisierung sehen. Innerhalb von Workspace sehen Endbenutzer diese Kategorien im Navigationsbereich. Die Endpunkte in jeder Kategorie werden als Prozesskarten auf der Seite „Startprozesse“ in Workspace angezeigt.

Sie können diese Aufgaben mithilfe des Endpoint Registry-Services ausführen:

* Fügen Sie EJB-Endpunkte hinzu. (Siehe [Hinzufügen von EJB-Endpunkten](programmatically-endpoints.md#adding-ejb-endpoints).)
* Fügen Sie SOAP-Endpunkte hinzu. (Siehe [Hinzufügen von SOAP-Endpunkten](programmatically-endpoints.md#adding-soap-endpoints).)
* Fügen Sie Endpunkte vom Typ „Überwachter Ordner“ hinzu (siehe [Hinzufügen von Endpunkten des Typs „Überwachter Ordner“](programmatically-endpoints.md#adding-watched-folder-endpoints).)
* Fügen Sie E-Mail-Endpunkte hinzu. (Siehe [Hinzufügen von E-Mail-Endpunkten](programmatically-endpoints.md#adding-email-endpoints).)
* Fügen Sie Remoting-Endpunkte hinzu. (Siehe [Hinzufügen von Remoting-Endpunkten](programmatically-endpoints.md#adding-remoting-endpoints).)
* Fügen Sie TaskManager-Endpunkte hinzu (siehe [Hinzufügen von TaskManager-Endpunkten](programmatically-endpoints.md#adding-taskmanager-endpoints).)
* Ändern Sie Endpunkte (siehe [Ändern von Endpunkten](programmatically-endpoints.md#modifying-endpoints).)
* Entfernen Sie Endpunkte (siehe [Entfernen von Endpunkten](programmatically-endpoints.md#removing-endpoints).)
* Rufen Sie Endpunkt-Connector-Informationen ab (siehe [Abrufen der Endpunkt-Connector-Informationen](programmatically-endpoints.md#retrieving-endpoint-connector-information).)

## Hinzufügen von EJB-Endpunkten {#adding-ejb-endpoints}

Sie können einen EJB-Endpunkt programmgesteuert zu einem Service hinzufügen, indem Sie die AEM Forms-Java-API verwenden. Durch das Hinzufügen eines EJB-Endpunkts zu einem Service ermöglichen Sie es einem Client-Programm, den Service unter Verwendung des EJB-Modus aufzurufen. Das heißt, beim Festlegen von Verbindungseigenschaften, die zum Aufrufen von AEM Forms erforderlich sind, können Sie den EJB-Modus auswählen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Mithilfe von Web-Services können Sie keinen EJB-Endpunkt hinzufügen.

>[!NOTE]
>
>Normalerweise wird ein EJB-Endpunkt standardmäßig zu einem Service hinzugefügt. Ein EJB-Endpunkt kann jedoch zu einem Vorgang hinzugefügt werden, der programmgesteuert bereitgestellt wird, oder wenn ein EJB-Endpunkt entfernt wurde und wieder hinzugefügt werden muss.

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um einen EJB-Endpunkt zu einem Service hinzuzufügen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistry Client`-Objekt.
1. Legen Sie die Attribute des EJB-Endpunkts fest.
1. Erstellen Sie einen EJB-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Bevor Sie einen EJB-Endpunkt programmgesteuert hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Festlegen der Attribute für einen EJB-Endpunkt**

Um einen EJB-Endpunkt für einen Service zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen EJB-Endpunkt zu erstellen, geben Sie `EJB` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name:** Gibt den Namen des Endpunkts an.
* **Service-ID**: Gibt den Service an, zu dem der Endpunkt gehört.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines EJB-Endpunkts ein Platzhalterzeichen (`*`) an. Wenn Sie jedoch einen bestimmten Vorgang angeben möchten, anstatt alle Service-Vorgänge aufzurufen, geben Sie anstelle des Platzhalterzeichens (`*`) den Namen des Vorgangs an.

**Erstellen eines EJB-Endpunkts**

Nachdem Sie die Attribute für den EJB-Endpunkt festgelegt haben, können Sie einen EJB-Endpunkt für einen Service erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Nachdem Sie den Endpunkt aktiviert haben, kann er zum Aufrufen des Services verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Administration-Console anzeigen.

**Siehe auch**

[Hinzufügen eines EJB-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#adding-an-ejb-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines EJB-Endpunkts mithilfe der Java-API {#adding-an-ejb-endpoint-using-the-java-api}

So fügen Sie mithilfe der Java-API einen EJB-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. (

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute des EJB-Endpunkts fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `EJB` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die Methode `setOperationName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Vorgangs angibt. Geben Sie für SOAP- und EJB-Endpunkte ein Platzhalterzeichen (`*`) an, wodurch alle Vorgänge impliziert werden.

1. Erstellen Sie einen EJB-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die Methode `createEndpoint` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt eine `Endpoint`-Objekt zurück, das den neuen EJB-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode „enable“ des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Hinzufügen eines EJB-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Hinzufügen von SOAP-Endpunkten {#adding-soap-endpoints}

Sie können einen SOAP-Endpunkt programmgesteuert zu einem Service hinzufügen, indem Sie die AEM Forms-Java-API verwenden. Durch Hinzufügen eines SOAP-Endpunkts aktivieren Sie ein Client-Programm, um den Service mithilfe des SOAP-Modus aufzurufen. Wenn Sie also Verbindungseigenschaften festlegen, die zum Aufrufen von AEM Forms erforderlich sind, können Sie den SOAP-Modus auswählen.

>[!NOTE]
>
>Mithilfe von Web-Services können Sie keinen SOAP-Endpunkt hinzufügen.

>[!NOTE]
>
>Normalerweise wird ein SOAP-Endpunkt standardmäßig zu einem Service hinzugefügt. Ein SOAP-Endpunkt kann jedoch zu einem Vorgang hinzugefügt werden, der programmgesteuert bereitgestellt wird, oder wenn ein SOAP-Endpunkt entfernt wurde und wieder hinzugefügt werden muss.

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Aufgaben aus, um einen SOAP-Endpunkt zu einem Service hinzuzufügen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Legen Sie die Attribute für den SOAP-Endpunkt fest.
1. Erstellen Sie einen SOAP-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Diese JAR-Dateien sind erforderlich, um einen SOAP-Endpunkt zu erstellen. Sie benötigen jedoch zusätzliche JAR-Dateien, wenn Sie den SOAP-Endpunkt zum Aufrufen des Services verwenden. Weitere Informationen zu AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Um einen SOAP-Endpunkt programmgesteuert zu einem Service hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Festlegen der Attribute für einen SOAP-Endpunkt**

Geben Sie die folgenden Werte an, um einen SOAP-Endpunkt zu einem Service hinzuzufügen:

* **Connector-ID-Wert**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen SOAP-Endpunkt zu erstellen, geben Sie `SOAP` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Service-ID-Wert**: Gibt den Service an, zu dem der Endpunkt gehört.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines SOAP-Endpunkts ein Platzhalterzeichen (`*`) an. Wenn Sie jedoch einen bestimmten Vorgang angeben möchten, anstatt alle Service-Vorgänge aufzurufen, geben Sie anstelle des Platzhalterzeichens (`*`) den Namen des Vorgangs an.

**Erstellen eines SOAP-Endpunkts**

Nachdem Sie die Attribute für den SOAP-Endpunkt festgelegt haben, können Sie einen SOAP-Endpunkt erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Service verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Administration-Console anzeigen.

**Siehe auch**

[Hinzufügen eines SOAP-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#add-a-soap-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines SOAP-Endpunkts mithilfe der Java-API {#add-a-soap-endpoint-using-the-java-api}

So fügen Sie mithilfe der Java-API einen SOAP-Endpunkt zu einem Service hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute für den SOAP-Endpunkt fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `SOAP` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die Methode `setOperationName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Vorgangs angibt. Geben Sie für SOAP- und EJB-Endpunkte ein Platzhalterzeichen (`*`) an, wodurch alle Vorgänge impliziert werden.

1. Erstellen Sie einen SOAP-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die Methode `createEndpoint` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen SOAP-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode „enable“ des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Hinzufügen eines SOAP-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Hinzufügen von Endpunkten für überwachte Ordner {#adding-watched-folder-endpoints}

Sie können einen Endpunkt vom Typ „Überwachter Ordner“ mithilfe der AEM Forms Java-API programmgesteuert einem Service hinzufügen. Durch Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ können Sie es Benutzern ermöglichen, eine PDF-Datei in einem Ordner abzulegen. Wenn die Datei im Ordner abgelegt wird, wird der konfigurierte Service aufgerufen und die Datei bearbeitet. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei in einem angegebenen Ausgabeordner gespeichert. Ein überwachter Ordner ist so konfiguriert, dass er in einem festen Zeitintervall oder nach einem Cron-Zeitplan gescannt wird, z. B. jeden Montag, Mittwoch und Freitag Mittag.

Um einem Service programmgesteuert einen Endpunkt vom Typ „Überwachter Ordner“ hinzuzufügen, beachten Sie den folgenden kurzlebigen Prozess namens *EncryptDocument*. (Weitere Informationen finden Sie unter [Grundlagen zu AEM Forms-Prozessen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).)

![aw_aw_encryptdocumentprocess](assets/aw_aw_encryptdocumentprocess.png)

In diesem Prozess wird ein ungesichertes PDF-Dokument als Eingabewert akzeptiert und das ungesicherte PDF-Dokument dann an den `EncryptPDFUsingPassword`-Vorgang des Encryption-Service übergeben. Das PDF-Dokument wird mit einem Passwort verschlüsselt und das passwortverschlüsselte PDF-Dokument ist der Ausgabewert dieses Vorgangs. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) lautet `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (das passwortverschlüsselte PDF-Dokument) lautet `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

>[!NOTE]
>
>Mit Webservices können Sie keinen Endpunkt vom Typ „Überwachter Ordner“ hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Aufgaben aus, um einem Service einen Endpunkt vom Typ „Überwachter Ordner“ hinzuzufügen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Legen Sie die Attribute des Endpunkts „Überwachter Ordner“ fest.
1. Geben Sie Konfigurationswerte an.
1. Definieren Sie Eingabeparameterwerte.
1. Definieren Sie einen Ausgabeparameterwert.
1. Erstellen Sie einen Endpunkt des Typs „Überwachter Ordner“.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Um einen Endpunkt vom Typ „Überwachter Ordner“ programmgesteuert hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Festlegen von Endpunktattributen für überwachte Ordner**

Geben Sie die folgenden Werte an, um einen Endpunkt vom Typ „Überwachter Ordner“ für einen Service zu erstellen:

* **Connector-ID**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen Endpunkt vom Typ „Überwachter Ordner“ zu erstellen, geben Sie `WatchedFolder` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name:** Gibt den Namen des Formulars an.
* **Dienstkennung**: Gibt den Service an, zu dem der Endpunkt gehört. Um beispielsweise einen Endpunkt vom Typ „Überwachter Ordner“ zu dem in diesem Abschnitt eingeführten Prozess hinzuzufügen (ein Prozess wird zu einem Service, wenn er mithilfe von Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Beim Erstellen eines Endpunkts vom Typ „Überwachten Ordner“ für einen Service, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs normalerweise `invoke`.

**Angeben von Konfigurationswerten**

Sie müssen Konfigurationswerte für einen Endpunkt vom Typ „Überwachter Ordner“ angeben, wenn Sie einem Service programmgesteuert einen Endpunkt vom Typ „Überwachter Ordner“ hinzufügen. Diese Konfigurationswerte werden von einem Administrator festgelegt, wenn ein Endpunkt vom Typ „Überwachter Ordner“ mithilfe von Administration Console hinzugefügt wird.

Die folgende Liste gibt Konfigurationswerte an, die festgelegt werden, wenn einem Service programmgesteuert ein Endpunkt vom Typ „Überwachter Ordner“ hinzugefügt wird:

* **url**: Gibt den Speicherort des überwachten Ordners an. In einer Cluster-Umgebung muss dieser Wert auf einen freigegebenen Netzwerkordner verweisen, auf den alle Computer im Cluster zugreifen können.
* **asynchron**: Gibt den Aufruftyp als „asynchron“ oder „synchron“ an. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert lautet true. Asynchron wird empfohlen.
* **cronExpression**: Wird von Quarz zur zeitlichen Planung des Abrufs des Eingabeordners verwendet.
* **purgeDuration**: Dies ist ein obligatorisches Attribut. Dateien und Ordner im Ergebnisordner werden bereinigt, wenn sie älter als dieser Wert sind. Dieser Wert wird in Tagen gemessen. Dieses Attribut ist nützlich, um sicherzustellen, dass der Ergebnisordner nicht voll wird. Ein Wert von „-1“ Tage bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.
* **repeatInterval**: Das Intervall in Sekunden, in dem der überwachte Ordner auf Eingaben überprüft wird. Sofern die Drosselung nicht aktiviert ist, sollte dieser Wert größer sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Andernfalls kann es zu einer Überlastung des Systems kommen. Der Standardwert ist 5.
* **repeatCount**: Die Häufigkeit, mit der ein überwachter Ordner den Ordner oder das Verzeichnis überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.
* **throttleOn**: Begrenzt die Anzahl der Aufträge für überwachte Ordner, die zu einem bestimmten Zeitpunkt verarbeitet werden können. Die maximale Anzahl von Aufträgen wird durch den Wert von „batchSize“ bestimmt.
* **userName**: Der Benutzername, mit dem ein Ziel-Service aus dem überwachten Ordner aufgerufen wird. Dieser Wert ist erforderlich. Der Standardwert ist „SuperAdmin“.
* **domainName**: Die Domain des Benutzers. Dieser Wert ist erforderlich. Der Standardwert ist „DefaultDom“.
* **batchSize**: Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Mit diesem Wert können Sie eine Überlastung des Systems verhindern, da das gleichzeitige Überprüfen zu vieler Dateien zu einem Absturz führen kann. Der Standardwert ist 2.
* **waitTime**: Die Zeit in Millisekunden, die nach der Erstellung gewartet wird, bevor ein Ordner oder eine Datei überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei erst nach Ablauf von mindestens 59 Minuten abgerufen. Dieses Attribut ist nützlich, um sicherzustellen, dass eine Datei oder ein Ordner vollständig in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei 10 Minuten dauert, legen Sie die Wartezeit auf 10 x 60 x 1000 Millisekunden fest. Diese Einstellung verhindert, dass der überwachte Ordner die Datei überprüft, wenn er nicht erst zehn Minuten lang gewartet hat. Der Standardwert ist 0.
* **excludeFilePattern**: Das Muster, das ein überwachter Ordner verwendet, um zu bestimmen, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Alle Dateien oder Ordner, die dieses Muster haben, werden nicht für die Verarbeitung überprüft. Diese Einstellung ist hilfreich, wenn die Eingabe aus einem Ordner mit mehreren Dateien besteht. Der Inhalt des Ordners kann in einen Ordner mit einem Namen kopiert werden, der vom überwachten Ordner aufgenommen wird. Dieser Schritt verhindert, dass der überwachte Ordner einen Ordner für die Verarbeitung aufnimmt, bevor dieser vollständig in den Eingabeordner kopiert ist. Wenn der Wert für „excludeFilePattern“ beispielsweise `data*` ist, werden alle Dateien und Ordner, die `data*` im Namen enthalten, nicht aufgenommen. Hierzu gehören auch Dateien und Ordner mit den Namen `data1`, `data2` usw. Darüber hinaus kann das Muster durch Platzhaltermuster ergänzt werden, um Dateimuster anzugeben. Der überwachte Ordner ändert den regulären Ausdruck, um Platzhaltermuster wie `*.*` und `*.pdf` zu unterstützen. Diese Platzhaltermuster werden von regulären Ausdrücken nicht unterstützt.
* **includeFilePattern**: Das Muster, das der überwachte Ordner verwendet, um zu bestimmen, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn dieser Wert beispielsweise `*` ist, werden alle Dateien und Ordner aufgenommen, die `input*` im Namen enthalten. Hierzu gehören auch Dateien und Ordner mit den Namen `input1`, `input2` usw. Der Standardwert ist `*`. Dieser Wert zeigt alle Dateien und Ordner an. Darüber hinaus kann das Muster durch Platzhaltermuster ergänzt werden, um Dateimuster anzugeben. Der überwachte Ordner ändert den regulären Ausdruck, um Platzhaltermuster wie `*.*` und `*.pdf` zu unterstützen. Diese Platzhaltermuster werden von regulären Ausdrücken nicht unterstützt. Dieser Wert ist erforderlich.
* **resultFolderName**: Der Ordner, in dem die Ergebnisse gespeichert werden. Dieser Speicherort kann ein absoluter oder ein relativer Ordnerpfad sein. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet, sondern im Fehlerordner gespeichert. Der Standardwert ist `result/%Y/%M/%D/`. Dies ist der Ergebnisordner innerhalb des überwachten Ordners.
* **preserveFolderName**: Der Speicherort, an dem Dateien nach erfolgreicher Überprüfung und Aufnahme gespeichert werden. Der Speicherort kann ein absoluter, relativer oder leerer Ordnerpfad sein. Der Standardwert ist `preserve/%Y/%M/%D/`.
* **failureFolderName**: Der Ordner, in dem Dateien mit Fehlern gespeichert werden. Dieser Speicherort ist stets relativ zum überwachten Ordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Der Standardwert ist `failure/%Y/%M/%D/`.
* **preserveOnFailure**: Bewahrt die Eingabedateien auf, wenn es zu einem Fehler bei der Ausführung des Vorgangs für einen Service kommt. Der Standardwert lautet true.
* **overwriteDuplicateFilename**: Bei Festlegung auf „True“ werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf „False“ werden Dateien und Ordner, die ein numerisches Indexsuffix aufweisen, als Name verwendet. Der Standardwert lautet false.

**Definieren von Eingabeparameterwerten**

Beim Erstellen eines Endpunkts des Typs „Überwachter Ordner“ müssen Sie Eingabeparameterwerte definieren. Das heißt, Sie müssen die Eingabewerte beschreiben, die an den Vorgang übergeben werden, der vom überwachten Ordner aufgerufen wird. Betrachten Sie beispielsweise den in diesem Thema eingeführten Prozess. Es gibt einen Eingabewert mit dem Namen `InDoc` und dem Datentyp `com.adobe.idp.Document`. Beim Erstellen eines Endpunkts des Typs „Überwachter Ordner“ für diesen Prozess (nachdem ein Prozess aktiviert wurde, wird er zu einem Service) müssen Sie den Eingabeparameterwert definieren.

Geben Sie die folgenden Werte an, um die für einen Endpunkt des Typs „Überwachter Ordner“ erforderlichen Eingabeparameterwerte zu definieren:

**Name des Eingabeparameters**: Der Name des Eingabeparameters. Der Name eines Eingabewerts wird in Workbench für einen Prozess angegeben. Wenn der Eingabewert zu einem Service-Vorgang gehört (einem Service, der kein in Workbench erstellter Prozess ist), wird der Eingabename in der .xml-Komponentendatei angegeben. Beispielsweise lautet der Name des Eingabeparameters für den in diesem Abschnitt eingeführten Prozess `InDoc`.

**Zuordnungstyp**: Wird zum Konfigurieren der zum Aufrufen des Service-Vorgangs erforderlichen Eingabewerte verwendet. Es gibt zwei Zuordnungstypen:

* `Literal`: Der Endpunkt „Überwachter Ordner“ verwendet den in das Feld eingegebenen Wert, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, Long, Int oder Boolean verwendet, wird die Zeichenfolge in einen ordnungsgemäßen Typ konvertiert und der Service aufgerufen.
* `Variable`: Der eingegebene Wert ist ein Dateimuster, das vom überwachten Ordner zum Auswählen der Eingabe verwendet wird. Wenn Sie beispielsweise „Variable“ für den Zuordnungstyp auswählen und das Eingabedokument eine PDF-Datei sein muss, können Sie `*.pdf` als Zuordnungswert angeben.

**Zuordnungswert**: Gibt den Wert des Zuordnungstyps an. Wenn Sie beispielsweise einen `Variable`-Zuordnungstyp auswählen, können Sie `*.pdf` als Dateimuster angeben.

**Datentyp**: Gibt den Datentyp der Eingabewerte an. Beispielsweise lautet der Datentyp des Eingabewerts des in diesem Abschnitt eingeführten Prozesses `com.adobe.idp.Document`.

**Definieren eines Ausgabeparameterwertes**

Beim Erstellen eines Endpunkts des Typs „Überwachter Ordner“ müssen Sie einen Ausgabeparameterwert definieren. Das heißt, Sie müssen den Ausgabewert beschreiben, der vom Service zurückgegeben wird, der vom Endpunkt „Überwachter Ordner“ aufgerufen wird. Betrachten Sie beispielsweise den in diesem Thema eingeführten Prozess. Es gibt einen Ausgabewert mit dem Namen `SecuredDoc` und dem Datentyp `com.adobe.idp.Document`. Beim Erstellen eines Endpunkts des Typs „Überwachter Ordner“ für diesen Prozess (nachdem ein Prozess aktiviert wurde, wird er zu einem Service) müssen Sie den Ausgabeparameterwert definieren.

Geben Sie die folgenden Werte an, um einen für einen Endpunkt des Typs „Überwachter Ordner“ erforderlichen Ausgabeparameterwert zu definieren:

**Name des Ausgabeparameters**: Der Name des Ausgabeparameters. Der Name eines Prozessausgabewerts wird in Workbench angegeben. Wenn der Ausgabewert zu einem Service-Vorgang gehört (ein Service, der kein in Workbench erstellter Prozess ist), wird der Ausgabename in der Datei „component.xml“ angegeben. Beispielsweise lautet der Name des Ausgabeparameters für den in diesem Abschnitt eingeführten Prozess `SecuredDoc`.

**Zuordnungstyp**: Wird zum Konfigurieren der Ausgabe des Service und Vorgangs verwendet. Die folgenden Optionen sind verfügbar:

* Wenn der Service ein einzelnes Objekt (ein einzelnes Dokument) zurückgibt, lautet das Muster `%F.pdf`, und das Quellziel ist „sourcefilename.pdf“. Beispielsweise gibt der in diesem Abschnitt eingeführte Prozess ein einzelnes Dokument zurück. Daher kann der Zuordnungstyp wie folgt definiert werden: `%F.pdf` (`%F` bedeutet, dass der angegebene Dateiname verwendet wird). Das Muster `%E` gibt die Erweiterung des Eingabedokuments an.
* Wenn der Service eine Liste zurückgibt, lautet das Muster `Result\%F\`, und das Quellziel ist „Result\sourcefilename\source1“ (Ausgabe 1) und „Result\sourcefilename\source2“ (Ausgabe 2).
* Wenn der Service eine Zuordnung zurückgibt, lautet das Muster `Result\%F\`, und das Quellziel ist „Result\sourcefilename\file1“ und „Result\sourcefilename\file2“. Wenn die Zuordnung mehr als ein Objekt enthält, lautet das Muster `Result\%F.pdf`, und das Quellziel ist „Result\sourcefilename1.pdf“ (Ausgabe 1), „Result\sourcefilenam2.pdf“ (Ausgabe 2) usw.

**Datentyp**: Gibt den Datentyp des Rückgabewerts an. Beispielsweise lautet der Datentyp des Rückgabewerts des in diesem Abschnitt eingeführten Prozesses `com.adobe.idp.Document`.

**Erstellen eines Endpunkts vom Typ „Überwachter Ordner“**

Nachdem Sie die Attribute und Konfigurationswerte des Endpunkts festgelegt und Eingabe- und Ausgabeparameterwerte definiert haben, müssen Sie den Endpunkt „Überwachter Ordner“ erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen Endpunkt vom Typ „Überwachter Ordner“ erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Service verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Verwaltungskonsole anzeigen.

**Siehe auch**

[Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ mithilfe der Java-API](programmatically-endpoints.md#add-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ mithilfe der Java-API {#add-a-watched-folder-endpoint-using-the-java-api}

So fügen Sie mithilfe der AEM Forms-Java-API einen Endpunkt des Typs „Überwachter Ordner“ hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute des Endpunkts „Überwachter Ordner“ fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `WatchedFolder` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die Methode `setOperationName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Vorgangs angibt. Beim Erstellen eines Endpunkts vom Typ „Überwachter Ordner“ für einen Service, der aus einem in Workbench erstellten Prozess stammt, wird normalerweise der Name des Vorgangs aufgerufen.

1. Geben Sie Konfigurationswerte an.

   Für jeden Konfigurationswert, der für den Endpunkt „Überwachter Ordner“ festgelegt werden soll, müssen Sie die Methode `setConfigParameterAsText` des `CreateEndpointInfo`-Objekts aufrufen. Um beispielsweise den `url`-Konfigurationswert festzulegen, rufen Sie die Methode `setConfigParameterAsText` des `CreateEndpointInfo`-Objekts auf und übergeben die folgenden Zeichenfolgenwerte:

   * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Wenn Sie den `url`-Konfigurationswert festlegen, geben Sie `url` an.
   * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Geben Sie beim Festlegen des `url`-Konfigurationswerts den Speicherort des überwachten Ordners an.

   >[!NOTE]
   >
   >Alle für den EncryptDocument-Service festgelegten Konfigurationswerte finden Sie im Java-Code-Beispiel unter [Kurzanleitung: Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api).

1. Definieren Sie Eingabeparameterwerte.

   Definieren Sie einen Eingabeparameterwert, indem Sie die Methode `setInputParameterMapping` des `CreateEndpointInfo`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Eingabeparameters angibt. Beispielsweise lautet der Name des Eingabeparameters für den EncryptDocument-Service `InDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Eingabeparameters angibt. Der Datentyp des Eingabeparameters `InDoc` ist beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `variable` angeben.
   * Ein Zeichenfolgenwert, der den Wert des Zuordnungstyps angibt. Beispielsweise können Sie &amp;ast;.pdf als Dateimuster angeben.

   >[!NOTE]
   >
   >Rufen Sie für jeden zu definierenden Eingabeparameterwert die Methode `setInputParameterMapping` auf. Da der EncryptDocument-Prozess nur einen Eingabeparameter hat, müssen Sie diese Methode einmal aufrufen.

1. Definieren Sie einen Ausgabeparameterwert.

   Definieren Sie einen Ausgabeparameterwert, indem Sie die Methode `setOutputParameterMapping` des `CreateEndpointInfo`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Ausgabeparameters angibt. Beispielsweise lautet der Name des Ausgabeparameters für den EncryptDocument-Service `SecuredDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Ausgabeparameters angibt. Der Datentyp des `SecuredDoc`-Ausgabeparameters ist beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `%F.pdf` angeben.

1. Erstellen Sie einen Endpunkt des Typs „Überwachter Ordner“.

   Erstellen Sie den Endpunkt, indem Sie die Methode `createEndpoint` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den Endpunkt „Überwachter Ordner“ darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode `enable` des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Schnellstart: Hinzufügen eines Endpunkts für überwachte Ordner mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Datei mit Konstanten für die Konfigurationswerte des überwachten Ordners {#watched-folder-configuration-values-constant-file}

Die [Kurzanleitung: Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api) verwendet eine Datei mit Konstanten, die Teil des Java-Projekts sein muss, um die Kurzanleitung zu kompilieren. Diese Konstantendatei enthält Konfigurationswerte, die beim Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ festgelegt werden müssen. Der folgende Java-Code bildet die Konstantendatei.

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

Sie können einen E-Mail-Endpunkt programmgesteuert zu einem Service hinzufügen, indem Sie die AEM Forms-Java-API verwenden. Durch Hinzufügen eines E-Mail-Endpunkts können Benutzer eine E-Mail-Nachricht mit einem oder mehreren Dateianlagen an ein bestimmtes E-Mail-Konto senden. Anschließend wird der Vorgang zum Konfigurieren des Services aufgerufen, und die Dateien werden bearbeitet. Nachdem der Service den angegebenen Vorgang ausgeführt hat, sendet er eine E-Mail-Nachricht mit den geänderten Dateien als Dateianlagen an den Absender.

Um einem Service programmgesteuert einen E-Mail-Endpunkt hinzuzufügen, beachten Sie den folgenden kurzlebigen Prozess mit dem Namen *MyApplication\EncryptDocument*. Informationen zu kurzlebigen Prozessen finden Sie unter [Grundlagen zu AEM Forms-Prozessen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).

![ae_ae_encryptdocumentprocess](assets/ae_ae_encryptdocumentprocess.png)

Dieser Prozess akzeptiert ein ungesichertes PDF-Dokument als Eingabewert und übergibt dann das ungesicherte PDF-Dokument an den `EncryptPDFUsingPassword`-Vorgang des Verschlüsselungs-Service. Dieser Prozess verschlüsselt das PDF-Dokument mit einem Kennwort und gibt das kennwortverschlüsselte PDF-Dokument als Ausgabewert zurück. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) lautet `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (das kennwortverschlüsselte PDF-Dokument) lautet `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

>[!NOTE]
>
>Über Webservices können Sie keinen E-Mail-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Aufgaben aus, um einem Service einen E-Mail-Endpunkt hinzuzufügen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Stellen Sie E-Mail-Endpunktattribute ein.
1. Geben Sie Konfigurationswerte an.
1. Definieren Sie Eingabeparameterwerte.
1. Definieren Sie einen Ausgabeparameterwert.
1. Erstellen Sie den E-Mail-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Bevor Sie einen E-Mail-Endpunkt programmgesteuert hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Festlegen von E-Mail-Endpunktattributen**

Geben Sie die folgenden Werte an, um einen E-Mail-Endpunkt für einen Service zu erstellen:

* **Connector-Kennungswert**: Gibt den Typ des Endpunkts an, der erstellt wird. Um einen E-Mail-Endpunkt zu erstellen, geben Sie `Email` an.
* **Beschreibung**: Gibt eine Beschreibung für den Endpunkt an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Service-Kennungswert**: Gibt den Service an, zu dem der Endpunkt gehört. Um beispielsweise einen E-Mail-Endpunkt zum Prozess hinzuzufügen, der in diesem Abschnitt eingeführt wird (ein Prozess wird zu einem Service, wenn er mithilfe von Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Beim Erstellen eines E-Mail-Endpunkts für einen Service, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs normalerweise `invoke`.

**Angeben von Konfigurationswerten**

Beim programmgesteuerten Hinzufügen eines E-Mail-Endpunkts zu einem Service müssen Sie Konfigurationswerte für einen E-Mail-Endpunkt angeben. Diese Konfigurationswerte werden von einem Administrator festgelegt, wenn ein E-Mail-Endpunkt über Administration Console hinzugefügt wird.

>[!NOTE]
>
>Das überwachte E-Mail-Konto ist ein spezielles Konto, das nur für den E-Mail-Endpunkt verwendet wird. Dieses Konto ist kein E-Mail-Konto eines normalen Benutzers. Das E-Mail-Konto eines normalen Benutzers darf nicht als das Konto konfiguriert werden, das der E-Mail-Anbieter verwendet, da der E-Mail-Anbieter E-Mail-Nachrichten aus dem Posteingang löscht, sobald er mit den Nachrichten fertig ist.

Beim programmgesteuerten Hinzufügen eines E-Mail-Endpunkts zu einem Service werden die folgenden Konfigurationswerte festgelegt:

* **cronExpression**: Ein Cron-Ausdruck, wenn die E-Mail mithilfe eines Cron-Ausdrucks geplant werden muss.
* **repeatCount**: Die Häufigkeit, mit welcher der E-Mail-Endpunkt den Ordner oder das Verzeichnis überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.
* **repeatInterval**: Die Überprüfungsrate in Sekunden, mit welcher der Empfänger auf eingehende E-Mails prüft. Der Standardwert ist 10.
* **startDelay**: Der Zeitraum, der nach dem Starten des Zeitplaners verstreichen muss, damit die Überprüfung ausgeführt wird. Der Standardzeitraum ist 0.
* **batchSize**: Die Anzahl von E-Mail-Nachrichten, die der Empfänger pro Überprüfung zur Optimierung der Leistung verarbeitet. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert ist 2.
* **userName**: Der Benutzername, der beim Aufrufen eines Ziel-Service aus einer E-Mail verwendet wird. Der Standardwert ist `SuperAdmin`.
* **domainName**: Ein obligatorischer Konfigurationswert. Der Standardwert ist `DefaultDom`.
* **domainPattern**: Gibt die Domain-Muster für eingehende E-Mails an, die vom Anbieter akzeptiert werden. Wenn beispielsweise „`adobe.com`“ verwendet wird, werden nur E-Mails aus der Domain „adobe.com“ verarbeitet, während E-Mails aus anderen Domains ignoriert werden.
* **filePattern**: Gibt die Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Dateinamenerweiterungen (&amp;ast;.dat, &amp;ast;.xml), Dateien mit bestimmten Namen („data“) und Dateien mit zusammengesetzten Ausdrücken im Namen und in der Erweiterung (&amp;ast;.[dD][aA]&#39;port&#39;). Der Standardwert ist `*`.
* **recipientSuccessfulJob**: Eine E-Mail-Adresse, an die Benachrichtigungen über erfolgreiche Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über erfolgreiche Aufträge immer an den Absender gesendet. Wenn Sie `sender` eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen an, von denen jeder durch ein Komma getrennt ist. Zum Deaktivieren dieser Option lassen Sie das Feld unausgefüllt. Es kann Fälle geben, in denen Sie einen Prozess auslösen möchten, ohne ein Benachrichtigung per E-Mail zum Ergebnis erhalten zu wollen. Der Standardwert ist `sender`.
* **recipientFailedJob**: Eine E-Mail-Adresse, an die Benachrichtigungen über fehlgeschlagene Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über einen fehlgeschlagenen Auftrag immer an den Absender gesendet. Wenn Sie `sender` eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen an, von denen jeder durch ein Komma getrennt ist. Zum Deaktivieren dieser Option lassen Sie das Feld unausgefüllt. Der Standardwert ist `sender`.
* **inboxHost**: Der Hostname oder die IP-Adresse für den Posteingang, der/die vom E-Mail-Anbieter überprüft werden soll.
* **inboxPort**: Der Port, der vom E-Mail-Server verwendet wird. Der Standardwert ist für POP3 „110“ und für IMAP „143“. Ist SSL aktiviert, ist der Standardwert für POP3 „995“ und für IMAP „993“.
* **inboxProtocol**: Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet werden soll. Die Optionen sind `IMAP` oder `POP3`. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.
* **inboxTimeOut**: Der Zeitraum in Sekunden, den der E-Mail-Anbieter auf Antworten des Posteingangs warten soll. Der Standardwert ist 60.
* **inboxUser**: Der Benutzername, der zum Anmelden beim E-Mail-Konto erforderlich ist. In Abhängigkeit vom E-Mail-Server und der Konfiguration kann dies nur der Teil der E-Mail-Adresse mit dem Benutzernamen oder die vollständige E-Mail-Adresse sein.
* **inboxPassword**: Das Kennwort für den Posteingangsbenutzer.
* **inboxSSLEnabled**: Legen Sie diesen Wert fest, um den E-Mail-Anbieter zu zwingen, beim Senden von Benachrichtigungen zu Ergebnissen oder Fehlern SSL zu verwenden. Stellen Sie sicher, dass der IMAP- oder POP3-Host SSL unterstützt.
* **smtpHost**: Der Host-Name des E-Mail-Servers, an den der E-Mail-Anbieter Ergebnisse und Fehlermeldungen sendet.
* **smtpPort**: Der Standardwert für den SMTP-Port ist 25.
* **smtpUser**: Das Benutzerkonto, das vom E-Mail-Anbieter verwendet werden soll, wenn ausgehende E-Mail-Benachrichtigungen mit Ergebnissen und Fehlermeldungen versendet werden.
* **smtpPassword**: Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.
* **charSet**: Der vom E-Mail-Anbieter verwendete Zeichensatz. Der Standardwert ist `UTF-8`.
* **smtpSSLEnabled**: Legen Sie diesen Wert fest, um den E-Mail-Anbieter zu zwingen, beim Senden von Benachrichtigungen zu Ergebnissen oder Fehlern SSL zu verwenden. Stellen Sie sicher, dass der SMTP-Host SSL unterstützt.
* **failedJobFolder**: Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, falls der SMTP-Mail-Server nicht funktioniert.
* **asynchronous**: Bei Festlegung auf synchron werden alle Eingabedokumente verarbeitet und eine einzige Antwort wird zurückgegeben. Bei Festlegung auf asynchron wird für jedes verarbeitete Eingabedokument eine Antwort gesendet. Beispielsweise wird ein E-Mail-Endpunkt für den in dieses Thema eingeführten Prozess erstellt und eine E-Mail-Nachricht an den Posteingang des Endpunkts gesendet, die mehrere ungesicherte PDF-Dokumente enthält. Wenn alle PDF-Dokumente mit einem Kennwort verschlüsselt sind und der Endpunkt als synchron konfiguriert ist, wird eine einzige Antwort-E-Mail-Nachricht mit allen gesicherten PDF-Dokumenten als Anhängen gesendet. Wenn der Endpunkt als asynchron konfiguriert ist, wird für jedes gesicherte PDF-Dokument eine separate Antwort-E-Mail-Nachricht gesendet. Jede E-Mail-Nachricht enthält ein einzelnes PDF-Dokument als Anlage. Der Standardwert ist „asynchron“.

**Definieren von Eingabeparameterwerten**

Beim Erstellen eines E-Mail-Endpunkts müssen Sie Eingabeparameterwerte definieren. Das heißt, Sie müssen die Eingabewerte beschreiben, die an den Vorgang übergeben werden, der vom E-Mail-Endpunkt aufgerufen wird. Betrachten Sie beispielsweise den in diesem Thema eingeführten Prozess. Er hat einen Eingabewert mit dem Namen `InDoc` und dem Datentyp `com.adobe.idp.Document`. Beim Erstellen eines E-Mail-Endpunkts für diesen Prozess (nachdem ein Prozess aktiviert wurde, wird er zu einem Service) müssen Sie den Eingabeparameterwert definieren.

Geben Sie die folgenden Werte an, um die für einen E-Mail-Endpunkt erforderlichen Eingabeparameterwerte zu definieren:

**Name des Eingabeparameters**: Der Name des Eingabeparameters. Der Name eines Eingabewerts wird in Workbench für einen Prozess angegeben. Wenn der Eingabewert zu einem Service-Vorgang gehört (einem Forms-Service, der kein in Workbench erstellter Prozess ist), wird der Eingabename in der Datei „component.xml“ angegeben. Beispielsweise lautet der Name des Eingabeparameters für den in diesem Abschnitt vorgestellten Prozess `InDoc`.

**Zuordnungstyp**: Wird zum Konfigurieren der zum Aufrufen des Service-Vorgangs erforderlichen Eingabewerte verwendet. Es gibt zwei Arten von Zuordnungstypen:

* `Literal`: Der E-Mail-Endpunkt verwendet den in das Feld eingegebenen Wert, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, Long, Int oder Boolean verwendet, wird die Zeichenfolge in einen ordnungsgemäßen Typ konvertiert und der Dienst aufgerufen.
* `Variable`: Der eingegebene Wert ist ein Dateimuster, das vom E-Mail-Endpunkt zum Auswählen der Eingabe verwendet wird. Wenn Sie beispielsweise als Zuordnungstyp „Variable“ auswählen und das Eingabedokument eine PDF-Datei sein muss, können Sie `*.pdf` als Zuordnungswert angeben.

**Zuordnungswert**: Gibt den Wert des Zuordnungstyps an. Wenn Sie beispielsweise den Zuordnungstyp „Variable“ auswählen, können Sie `*.pdf` als Dateimuster angeben.

**Datentyp**: Gibt den Datentyp der Eingabewerte an. Beispielsweise lautet der Datentyp des Eingabewerts des in diesem Abschnitt vorgestellten Prozesses „com.adobe.idp.Document“.

**Definieren eines Ausgabeparameterwerts**

Beim Erstellen eines E-Mail-Endpunkts müssen Sie einen Ausgabeparameterwert definieren. Das heißt, Sie müssen den Ausgabewert beschreiben, der von dem Service zurückgegeben wird, der vom E-Mail-Endpunkt aufgerufen wird. Betrachten Sie beispielsweise den in diesem Thema eingeführten Prozess. Er hat einen Ausgabewert mit dem Namen `SecuredDoc` und dem Datentyp `com.adobe.idp.Document`. Wenn Sie einen E-Mail-Endpunkt für diesen Prozess (nachdem ein Prozess aktiviert wurde, wird er zu einem Service) erstellen, müssen Sie den Wert des Ausgabeparameters definieren.

Um einen für einen E-Mail-Endpunkt erforderlichen Ausgabeparameterwert zu definieren, geben Sie die folgenden Werte an:

**Name des Ausgabeparameters**: Der Name des Ausgabeparameters. Der Name eines Prozessausgabewerts wird in Workbench angegeben. Wenn der Ausgabewert zu einem Service-Vorgang gehört (ein Service, der kein in Workbench erstellter Prozess ist), wird der Ausgabename in der Datei „component.xml“ angegeben. Beispielsweise lautet der Name des Ausgabeparameters für den in diesem Abschnitt eingeführten Prozess `SecuredDoc`.

**Zuordnungstyp**: Wird zum Konfigurieren der Ausgabe des Service und Vorgangs verwendet. Die folgenden Optionen sind verfügbar:

* Wenn der Service ein einzelnes Objekt (ein einzelnes Dokument) zurückgibt, lautet das Muster `%F.pdf`, und das Quellziel ist „sourcefilename.pdf“. Beispielsweise gibt der in diesem Abschnitt eingeführte Prozess ein einzelnes Dokument zurück. Daher kann der Zuordnungstyp wie folgt definiert werden: `%F.pdf` (`%F` bedeutet, dass der angegebene Dateiname verwendet wird). Das Muster `%E` gibt die Erweiterung des Eingabedokuments an.
* Wenn der Service eine Liste zurückgibt, lautet das Muster `Result\%F\`, und das Quellziel ist „Result\sourcefilename\source1“ (Ausgabe 1) und „Result\sourcefilename\source2“ (Ausgabe 2).
* Wenn der Service eine Zuordnung zurückgibt, lautet das Muster `Result\%F\`, und das Quellziel ist „Result\sourcefilename\file1“ und „Result\sourcefilename\file2“. Wenn die Zuordnung mehr als ein Objekt enthält, lautet das Muster `Result\%F.pdf`, und das Quellziel ist „Result\sourcefilename1.pdf“ (Ausgabe 1), „Result\sourcefilenam2.pdf“ (Ausgabe 2) usw.

**Datentyp**: Gibt den Datentyp des Rückgabewerts an. Beispielsweise lautet der Datentyp des Rückgabewerts des in diesem Abschnitt vorgestellten Prozesses `com.adobe.idp.Document`.

**Erstellen des E-Mail-Endpunkts**

Nachdem Sie die E-Mail-Endpunktattribute und Konfigurationswerte festgelegt sowie Ein- und Ausgabeparameterwerte definiert haben, müssen Sie den E-Mail-Endpunkt erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen E-Mail-Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Service verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Verwaltungskonsole anzeigen.

**Siehe auch**

[Hinzufügen eines E-Mail-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#add-an-email-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines E-Mail-Endpunkts mithilfe der Java-API {#add-an-email-endpoint-using-the-java-api}

Fügen Sie mithilfe der Java-API einen E-Mail-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Stellen Sie E-Mail-Endpunktattribute ein.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `Email` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie den Vorgang an, der aufgerufen werden soll, indem Sie die `setOperationName`-Methode des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Vorgangsnamen angibt. Beim Erstellen eines E-Mail-Endpunkts für einen Service, der aus einem in Workbench erstellten Prozess stammt, wird normalerweise der Name des Vorgangs aufgerufen.

1. Geben Sie Konfigurationswerte an.

   Für jeden Konfigurationswert, der für den E-Mail-Endpunkt eingestellt werden soll, müssen Sie die `setConfigParameterAsText`-Methode des `CreateEndpointInfo`-Objekts aufrufen. Um beispielsweise den `smtpHost`-Konfigurationswert einzustellen, rufen Sie die `setConfigParameterAsText`-Methode des `CreateEndpointInfo`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Wenn Sie den `smtpHost`-Konfigurationswert festlegen, geben Sie `smtpHost` an.
   * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Wenn Sie den `smtpHost`-Konfigurationswert einstellen, geben Sie einen Zeichenfolgenwert an, der den Namen des SMTP-Servers festlegt.

   >[!NOTE]
   >
   >Um alle in diesem Abschnitt eingestellten Konfigurationswerte für den EncryptDocument-Service anzuzeigen, lesen Sie das Java-Codebeispiel unter [Schnellstart: Hinzufügen eines E-Mail-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api).

1. Definieren Sie Eingabeparameterwerte.

   Definieren Sie einen Eingabeparameterwert, indem Sie die Methode `setInputParameterMapping` des `CreateEndpointInfo`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Eingabeparameters angibt. Beispielsweise lautet der Name des Eingabeparameters für den EncryptDocument-Service `InDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Eingabeparameters angibt. Der Datentyp des Eingabeparameters `InDoc` ist beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `variable` angeben.
   * Ein Zeichenfolgenwert, der den Wert des Zuordnungstyps angibt. Beispielsweise können Sie &amp;ast;.pdf als Dateimuster angeben.

   >[!NOTE]
   >
   >Rufen Sie für jeden zu definierenden Eingabeparameterwert die Methode `setInputParameterMapping` auf. Da der EncryptDocument-Prozess nur einen Eingabeparameter hat, müssen Sie diese Methode einmal aufrufen.

1. Definieren Sie einen Ausgabeparameterwert.

   Definieren Sie einen Ausgabeparameterwert, indem Sie die `setOutputParameterMapping`-Methode des `CreateEndpointInfo`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Namen des Ausgabeparameters angibt. Beispielsweise lautet der Name des Ausgabeparameters für den EncryptDocument-Service `SecuredDoc`.
   * Ein Zeichenfolgenwert, der den Datentyp des Ausgabeparameters angibt. Der Datentyp des `SecuredDoc`-Ausgabeparameters ist beispielsweise `com.adobe.idp.Document`.
   * Ein Zeichenfolgenwert, der den Zuordnungstyp angibt. Sie können beispielsweise `%F.pdf` angeben.

1. Erstellen Sie den E-Mail-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die `createEndpoint`-Methode des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den E-Mail-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode `enable` des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Schnellstart: Hinzufügen eines Endpunkts für überwachte Ordner mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konfigurationswerte für E-Mails - Konstante Datei {#email-configuration-values-constant-file}

Unter [Schnellstart: Hinzufügen eines E-Mail-Endpunkts mit der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api) wird eine konstante Datei verwendet, die Teil Ihres Java-Projekts sein muss, um den Schnellstart zu kompilieren. Diese konstante Datei stellt Konfigurationswerte dar, die beim Hinzufügen eines E-Mail-Endpunkts festgelegt werden müssen. Der folgende Java-Code bildet die Konstantendatei.

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

## Hinzufügen von Remoting-Endpunkten {#adding-remoting-endpoints}

>[!NOTE]
>
>LiveCycle Remoting-APIs werden für AEM Forms on JEE nicht mehr unterstützt.

Sie können einen Remoting-Endpunkt mithilfe der AEM Forms-Java-API programmgesteuert zu einem Service hinzufügen. Durch Hinzufügen eines Remoting-Endpunkts aktivieren Sie ein Flex-Programm, um den Service mithilfe von Remoting aufzurufen. (Siehe [Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Um einem Service programmgesteuert einen Remoting-Endpunkt hinzuzufügen, beachten Sie den folgenden kurzlebigen Prozess mit dem Namen *EncryptDocument*.

![ar_ar_encryptdocumentprocess](assets/ar_ar_encryptdocumentprocess.png)

Bei diesem Prozess wird ein ungesichertes PDF-Dokument als Eingabewert akzeptiert und das ungesicherte PDF-Dokument wird dann an den `EncryptPDFUsingPassword`-Vorgang des Verschlüsselungsservice übergeben. Das PDF-Dokument wird mit einem Passwort verschlüsselt und das passwortverschlüsselte PDF-Dokument ist der Ausgabewert dieses Vorgangs. Der Name des Eingabewerts (das ungesicherte PDF-Dokument) lautet `InDoc` und der Datentyp ist `com.adobe.idp.Document`. Der Name des Ausgabewerts (das kennwortverschlüsselte PDF-Dokument) lautet `SecuredDoc` und der Datentyp ist `com.adobe.idp.Document`.

Um zu demonstrieren, wie einem Service ein Remoting-Endpunkt hinzugefügt wird, wird in diesem Abschnitt ein Remoting-Endpunkt zu einem Service namens „EncryptDocument“ hinzugefügt.

>[!NOTE]
>
>Mit Webservices können Sie keinen Remoting-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-4}

Führen Sie die folgenden Aufgaben aus, um einen Endpunkt aus einem Service zu entfernen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Legen Sie die Attribute für einen Remoting-Endpunkt fest.
1. Erstellen Sie einen Remoting-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Um einen Remoting-Endpunkt programmgesteuert hinzuzufügen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Festlegen von Remoting-Endpunktattributen**

Geben Sie die folgenden Werte an, um einen Remoting-Endpunkt für einen Service zu erstellen:

* **Connector-Kennungswert**: Gibt den Typ des Endpunkts an, der erstellt wird. Um einen Remoting-Endpunkt zu erstellen, geben Sie `Remoting` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Service-Kennungswert**: Gibt den Service an, zu dem der Endpunkt gehört. Um beispielsweise einen Remoting-Endpunkt zu dem Prozess hinzuzufügen, der in diesem Abschnitt vorgestellt wird (ein Prozess wird zu einem Service, wenn er in Workbench aktiviert wird), geben Sie `EncryptDocument` an.
* **Vorgangsname**: Gibt den Namen des Vorgangs an, der mithilfe des Endpunkts aufgerufen wird. Geben Sie beim Erstellen eines Remoting-Endpunkts ein Platzhalterzeichen (&amp;ast;) an.

**Erstellen eines Remoting-Endpunkts**

Nachdem Sie die Remoting-Endpunktattribute festgelegt haben, können Sie einen Remoting-Endpunkt für einen Service erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn ein Remoting-Endpunkt aktiviert ist, kann ein Flex-Client damit den Service aufzurufen.

**Siehe auch**

[Hinzufügen eines Remoting-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#add-a-remoting-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines Remoting-Endpunkts mithilfe der Java-API {#add-a-remoting-endpoint-using-the-java-api}

So fügen Sie mithilfe der Java-API einen Remoting-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute für einen Remoting-Endpunkt fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `Remoting` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie den Vorgang an, der durch die Methode `setOperationName` des `CreateEndpointInfo`-Objekts aufgerufen wird, und übergeben Sie einen Zeichenfolgenwert, der den Namen des Vorgangs angibt. Geben Sie für einen Remoting-Endpunkt ein Platzhalterzeichen (*) an.

1. Erstellen Sie einen Remoting-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die Methode `createEndpoint` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen Remoting-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode `enable` des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Hinzufügen eines Remoting-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Hinzufügen von TaskManager-Endpunkten {#adding-taskmanager-endpoints}

Sie können einen TaskManager-Endpunkt programmgesteuert zu einem Service hinzufügen, indem Sie die AEM Forms-Java-API verwenden. Durch Hinzufügen eines TaskManager-Endpunkts zu einem Service ermöglichen Sie einem Workspace-Benutzer, den Service aufzurufen. Das heißt, ein Benutzer, der in Workspace arbeitet, kann einen Prozess aufrufen, der über einen entsprechenden TaskManager-Endpunkt verfügt.

>[!NOTE]
>
>Mit Web-Services können Sie keinen TaskManager-Endpunkt hinzufügen.

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie die folgenden Aufgaben aus, um einen TaskManager-Endpunkt zu einem Service hinzuzufügen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Erstellen Sie eine Kategorie für den Endpunkt.
1. Legen Sie die Attribute des TaskManager-Endpunkts fest.
1. Erstellen Sie einen TaskManager-Endpunkt.
1. Aktivieren Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Bevor Sie einen TaskManager-Endpunkt programmgesteuert hinzufügen können, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Erstellen einer Kategorie für den Endpunkt**

Kategorien werden verwendet, um Services in Workspace zu organisieren. Das heißt, ein Workspace-Benutzer kann einen Service aufrufen, der einen TaskManager-Endpunkt hat, indem er eine Kategorie in Workspace auswählt. Beim Erstellen eines TaskManager-Endpunkts können Sie entweder auf eine vorhandene Kategorie verweisen oder programmgesteuert eine neue Kategorie erstellen.

>[!NOTE]
>
>In diesem Abschnitt wird beim Hinzufügen eines TaskManager-Endpunkts zu einem Service eine neue Kategorie erstellt.

**Festlegen der Attribute für einen TaskManager-Endpunkt**

Um einen TaskManager-Endpunkt für einen Service zu erstellen, geben Sie die folgenden Werte an:

* **Connector-ID**: Gibt den Typ des zu erstellenden Endpunkts an. Um einen TaskManager-Endpunkt zu erstellen, geben Sie `TaskManagerConnector` an.
* **Beschreibung**: Gibt die Beschreibung des Endpunkts an.
* **Name**: Gibt den Namen des Endpunkts an.
* **Service-ID**: Gibt den Service an, zu dem der Endpunkt gehört.
* **Kategorie**: Gibt den ID-Wert einer Kategorie an, die mit dem TaskManager-Endpunkt verbunden ist.
* **Vorgangsname**: Beim Erstellen eines TaskManager-Endpunkts für einen Service, der aus einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs in der Regel `invoke`.

**Erstellen eines TaskManager-Endpunkts**

Nachdem Sie die Attribute eines TaskManager-Endpunkts festgelegt haben, können Sie einen TaskManager-Endpunkt für einen Service erstellen.

**Aktivieren des Endpunkts**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er verwendet werden, um den Service von Workspace aus aufzurufen. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Verwaltungskonsole anzeigen.

**Siehe auch**

[Hinzufügen eines TaskManager-Endpunkts mithilfe der Java-API](programmatically-endpoints.md#add-a-taskmanager-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen eines TaskManager-Endpunkts mithilfe der Java-API {#add-a-taskmanager-endpoint-using-the-java-api}

So fügen Sie mithilfe der Java-API einen TaskManager-Endpunkt hinzu:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Erstellen Sie eine Kategorie für den Endpunkt.

   * Erstellen Sie ein `CreateEndpointCategoryInfo`-Objekt, indem Sie seinen Konstruktor verwenden und die folgenden Werte übergeben:

      * Einen Zeichenfolgenwert, der den ID-Wert der Kategorie angibt
      * Einen Zeichenfolgenwert, der die Beschreibung der Kategorie angibt
   * Erstellen Sie die Kategorie, indem Sie die Methode `createEndpointCategory` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointCategoryInfo`-Objekt übergeben. Diese Methode gibt ein `EndpointCategory`-Objekt zurück, das die neue Kategorie darstellt.


1. Legen Sie die Attribute des TaskManager-Endpunkts fest.

   * Erstellen Sie ein Objekt `CreateEndpointInfo`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Wert der Connector-ID an, indem Sie die Methode `setConnectorId` des `CreateEndpointInfo`-Objekts aufrufen und den Zeichenfolgenwert `TaskManagerConnector` übergeben.
   * Geben Sie die Beschreibung des Endpunkts an, indem Sie die Methode `setDescription` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Endpunkt beschreibt.
   * Geben Sie den Namen des Endpunkts an, indem Sie die Methode `setName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen angibt.
   * Geben Sie den Service an, zu dem der Endpunkt gehört, indem Sie die Methode `setServiceId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Services angibt.
   * Geben Sie die Kategorie an, zu der der Endpunkt gehört, indem Sie die Methode `setCategoryId` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den ID-Wert der Kategorie angibt. Sie können die Methode `getId` des `EndpointCategory`-Objekts aufrufen, um den ID-Wert dieser Kategorie abzurufen.
   * Geben Sie den Vorgang an, der aufgerufen wird, indem Sie die Methode `setOperationName` des `CreateEndpointInfo`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Vorgangs angibt. Wenn Sie einen `TaskManager`-Endpunkt für einen Service erstellen, der von einem in Workbench erstellten Prozess stammt, lautet der Name des Vorgangs in der Regel `invoke`.

1. Erstellen Sie einen TaskManager-Endpunkt.

   Erstellen Sie den Endpunkt, indem Sie die Methode `createEndpoint` des `EndpointRegistryClient`-Objekts aufrufen und das `CreateEndpointInfo`-Objekt übergeben. Diese Methode gibt ein `Endpoint`-Objekt zurück, das den neuen TaskManager-Endpunkt darstellt.

1. Aktivieren Sie den Endpunkt.

   Aktivieren Sie den Endpunkt, indem Sie die Methode `enable` des `EndpointRegistryClient`-Objekts aufrufen und das `Endpoint`-Objekt übergeben, das von der Methode `createEndpoint` zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Hinzufügen eines TaskManager-Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Ändern von Endpunkten {#modifying-endpoints}

Sie können einen vorhandenen Endpunkt mithilfe der AEM Forms-Java-API programmgesteuert ändern. Durch Ändern eines Endpunkts können Sie das Verhalten des Endpunkts ändern. Betrachten Sie beispielsweise einen Endpunkt des Typs „Überwachter Ordner“, der einen Ordner angibt, welcher als überwachter Ordner verwendet wird. Sie können Konfigurationswerte, die zum Endpunkt des Typs „überwachter Ordner“ gehören, programmgesteuert ändern, sodass ein anderer Ordner als der überwachte Ordner funktioniert. Weitere Informationen zu Konfigurationswerten, die zu einem Endpunkt des Typs „Überwachter Ordner“ gehören, finden Sie unter [Hinzufügen von Endpunkten des Typs „Überwachter Ordner“](programmatically-endpoints.md#adding-watched-folder-endpoints).

Um zu demonstrieren, wie Sie einen Endpunkt ändern, wird in diesem Abschnitt ein Endpunkt des Typs „Überwachter Ordner“ verändert, indem geändert wird, welcher Ordner sich wie der überwachte Ordner verhält.

>[!NOTE]
>
>Sie können einen Endpunkt nicht mithilfe von Web-Services ändern.

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie die folgenden Aufgaben aus, um einen Endpunkt zu ändern:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Rufen Sie den Endpunkt ab.
1. Geben Sie neue Konfigurationswerte an.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Um einen Endpunkt programmgesteuert zu ändern, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Abrufen des zu ändernden Endpunkts**

Bevor Sie einen Endpunkt ändern können, müssen Sie ihn abrufen. Um einen Endpunkt abzurufen, müssen Sie eine Verbindung als Benutzer herstellen, der auf einen Endpunkt zugreifen kann. Es wird empfohlen, eine Verbindung als Administrator herzustellen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Sie können einen Endpunkt abrufen, indem Sie eine Liste von Endpunkten abrufen. Anschließend können Sie durch die Liste navigieren und nach dem jeweiligen zu entfernenden Endpunkt suchen. Sie können beispielsweise einen Endpunkt suchen, indem Sie den Service bestimmen, der dem Endpunkt und dem Endpunkttyp entspricht. Wenn Sie den Endpunkt finden, können Sie ihn ändern.

**Angeben neuer Konfigurationswerte**

Geben Sie beim Ändern eines Endpunkts neue Konfigurationswerte an. Um beispielsweise einen Endpunkt des Typs „Überwachter Ordner“ zu ändern, setzen Sie alle Konfigurationswerte des Endpunkts „Überwachter Ordner“ zurück, nicht nur die, die Sie ändern möchten. Weitere Informationen zu Konfigurationswerten, die zu einem Endpunkt des Typs „Überwachter Ordner“ gehören, finden Sie unter [Hinzufügen von Endpunkten des Typs „Überwachter Ordner“](programmatically-endpoints.md#adding-watched-folder-endpoints).

>[!NOTE]
>
>Weitere Informationen zu Konfigurationswerten, die zu einem E-Mail-Endpunkt gehören, finden Sie unter [Hinzufügen von E-Mail-Endpunkten](programmatically-endpoints.md#adding-email-endpoints).

>[!NOTE]
>
>Sie können den Service, der vom Endpunkt aufgerufen wird, nicht ändern. Wenn Sie versuchen, den Service zu ändern, wird eine Ausnahme ausgelöst. Um den mit einem bestimmten Endpunkt verknüpften Service zu ändern, entfernen Sie den Endpunkt und erstellen Sie einen neuen. (Siehe [Entfernen von Endpunkten](programmatically-endpoints.md#removing-endpoints).)

**Siehe auch**

[Ändern eines Endpunkts mithilfe der Java-API](programmatically-endpoints.md#modifying-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ändern eines Endpunkts mithilfe der Java-API {#modifying-an-endpoint-using-the-java-api}

So ändern Sie einen Endpunkt mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den zu ändernden Endpunkt ab.

   * Rufen Sie eine Liste aller Endpunkte ab, auf die der aktuelle Benutzer (angegeben in den Verbindungseigenschaften) zugreifen kann, indem Sie die Methode `getEndpoints` des `EndpointRegistryClient`-Objekts aufrufen und ein `PagingFilter`-Objekt übergeben, das als Filter dient. Sie können einen Wert `(PagingFilter)null` übergeben, damit alle Endpunkte zurückgegeben werden. Diese Methode gibt ein `java.util.List`-Objekt zurück, bei dem jedes Element ein `Endpoint`-Objekt ist. Weitere Informationen zu einem `PagingFilter`-Objekt finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Iterieren Sie durch das `java.util.List`-Objekt, um festzustellen, ob es Endpunkte enthält. Wenn Endpunkte vorhanden sind, ist jedes Element eine `EndPoint`-Instanz.
   * Ermitteln Sie den Service, der einem Endpunkt entspricht, indem Sie die Methode `getServiceId` des `EndPoint`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Namen des Services angibt.
   * Ermitteln Sie den Typ des Endpunkts, indem Sie die Methode `getConnectorId` des `EndPoint`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Typ des Endpunkts angibt. Wenn der Endpunkt beispielsweise ein Endpunkt des Typs „überwachter Ordner“ ist, gibt diese Methode `WatchedFolder` zurück.

1. Geben Sie neue Konfigurationswerte an.

   * Erstellen Sie ein `ModifyEndpointInfo`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Rufen Sie für jeden festzulegenden Konfigurationswert die Methode `setConfigParameterAsText` des `ModifyEndpointInfo`-Objekts auf. Um beispielsweise den URL-Konfigurationswert festzulegen, rufen Sie die Methode `setConfigParameterAsText` des `ModifyEndpointInfo`-Objekts auf und übergeben die folgenden Werte:

      * Ein Zeichenfolgenwert, der den Namen des Konfigurationswerts angibt. Um beispielsweise den `url`-Konfigurationswert festzulegen, geben Sie `url` an.
      * Ein Zeichenfolgenwert, der den Wert des Konfigurationswerts angibt. Um einen Wert für den `url`-Konfigurationswert zu definieren, geben Sie den Speicherort des überwachten Ordners an.
   * Rufen Sie die Methode `modifyEndpoint` des `EndpointRegistryClient`-Objekts auf und übergeben Sie das `ModifyEndpointInfo`-Objekt.


**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Ändern eines Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Entfernen von Endpunkten {#removing-endpoints}

Sie können einen Endpunkt mithilfe der AEM Forms-Java-API programmgesteuert aus einem Service entfernen. Nachdem Sie einen Endpunkt entfernt haben, kann der Service nicht mit der Aufrufmethode aufgerufen werden, die der Endpunkt aktiviert hatte. Wenn Sie beispielsweise einen SOAP-Endpunkt aus einem Service entfernen, können Sie den Service nicht im SOAP-Modus aufrufen.

Um zu demonstrieren, wie Sie einen Endpunkt aus einem Service entfernen, wird in diesem Abschnitt ein EJB-Endpunkt aus einem Service mit dem Namen *EncryptDocument* entfernt.

>[!NOTE]
>
>Mit Web-Services können Sie einen Endpunkt nicht entfernen.

### Zusammenfassung der Schritte {#summary_of_steps-7}

Führen Sie die folgenden Aufgaben aus, um einen Endpunkt aus einem Service zu entfernen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `EndpointRegistryClient`-Objekt.
1. Rufen Sie den Endpunkt ab.
1. Entfernen Sie den Endpunkt.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines EndpointRegistry-Client-Objekts**

Um einen Endpunkt programmgesteuert zu entfernen, müssen Sie ein `EndpointRegistryClient`-Objekt erstellen.

**Abrufen des zu entfernenden Endpunkts**

Bevor Sie einen Endpunkt entfernen können, müssen Sie ihn abrufen. Um einen Endpunkt abzurufen, müssen Sie eine Verbindung als Benutzer herstellen, der auf einen Endpunkt zugreifen kann. Es wird empfohlen, eine Verbindung als Administrator herzustellen. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Sie können einen Endpunkt abrufen, indem Sie eine Liste von Endpunkten abrufen. Anschließend können Sie durch die Liste navigieren und nach dem jeweiligen zu entfernenden Endpunkt suchen. Sie können beispielsweise einen Endpunkt suchen, indem Sie den Service bestimmen, der dem Endpunkt und dem Endpunkttyp entspricht. Wenn Sie den Endpunkt finden, können Sie ihn entfernen.

**Entfernen des Endpunkts**

Nachdem Sie einen neuen Endpunkt erstellt haben, müssen Sie ihn aktivieren. Wenn der Endpunkt aktiviert ist, kann er zum Aufrufen des Service verwendet werden. Nachdem Sie den Endpunkt aktiviert haben, können Sie ihn in der Verwaltungskonsole anzeigen.

**Siehe auch**

[Entfernen eines Endpunkts mithilfe der Java-API](programmatically-endpoints.md#removing-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen eines Endpunkts mithilfe der Java-API {#removing-an-endpoint-using-the-java-api}

So entfernen Sie einen Endpunkt mithilfe der Java-API:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein EndpointRegistry-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EndpointRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den zu entfernenden Endpunkt ab.

   * Rufen Sie eine Liste aller Endpunkte ab, auf die der aktuelle Benutzer (angegeben in den Verbindungseigenschaften) zugreifen kann, indem Sie die Methode `getEndpoints` des `EndpointRegistryClient`-Objekts aufrufen und ein `PagingFilter`-Objekt übergeben, das als Filter dient. Sie können einen `(PagingFilter)null`-Wert übergeben, damit alle Endpunkte zurückgegeben werden. Diese Methode gibt ein `java.util.List`-Objekt zurück, bei dem jedes Element ein `Endpoint`-Objekt ist.
   * Iterieren Sie durch das `java.util.List`-Objekt, um festzustellen, ob es Endpunkte enthält. Wenn Endpunkte vorhanden sind, ist jedes Element eine `EndPoint`-Instanz.
   * Ermitteln Sie den Service, der einem Endpunkt entspricht, indem Sie die Methode `getServiceId` des `EndPoint`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Namen des Services angibt.
   * Ermitteln Sie den Typ des Endpunkts, indem Sie die Methode `getConnectorId` des `EndPoint`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Typ des Endpunkts angibt. Wenn der Endpunkt beispielsweise ein EJB-Endpunkt ist, gibt diese Methode `EJB` zurück.

1. Entfernen Sie den Endpunkt.

   Entfernen Sie den Endpunkt, indem Sie die Methode `remove` des `EndpointRegistryClient`-Objekts aufrufen und das `EndPoint`-Objekt übergeben, das den zu entfernenden Endpunkt darstellt.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Kurzanleitung: Entfernen eines Endpunkts mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Abrufen der Endpoint-Connector-Informationen {#retrieving-endpoint-connector-information}

Sie können mithilfe der AEM Forms-API programmgesteuert Informationen zu Endpunkt-Connectoren abrufen. Ein Connector ermöglicht es einem Endpunkt, einen Service mithilfe verschiedener Aufrufmethoden aufzurufen. Ein Connector für überwachte Ordner ermöglicht es beispielsweise einem Endpunkt, einen Service mithilfe überwachter Ordner aufzurufen. Durch das programmgesteuerte Abrufen von Informationen zu Endpunkt-Connectoren können Sie Konfigurationswerte abrufen, die mit einem Connector verknüpft sind, z. B. welche Konfigurationswerte erforderlich sind und welche optional sind.

Um zu demonstrieren, wie Sie Informationen zu Endpunkt-Connectoren abrufen, werden in diesem Abschnitt Informationen zu einem Connector für überwachte Ordner abgerufen. (Siehe [Hinzufügen von Endpunkten des Typs „Überwachter Ordner“](programmatically-endpoints.md#adding-watched-folder-endpoints).)

>[!NOTE]
>
>Mit Web-Services können Sie keine Informationen zu Endpunkten abrufen.

>[!NOTE]
>
>Dieses Thema verwendet die `ConnectorRegistryClient`-API zum Abrufen von Informationen zu Endpunkt-Connectoren. (Siehe [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

### Zusammenfassung der Schritte {#summary_of_steps-8}

Führen Sie die folgenden Aufgaben aus, um Endpunkt-Connector-Informationen abzurufen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein `ConnectorRegistryClient`-Objekt.
1. Geben Sie den Connector-Typ an.
1. Rufen Sie Konfigurationswerte ab.

**Einbeziehen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Programm-Server bereitgestellt wird, der nicht JBoss ist, ersetzen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien, die spezifisch für den J2EE-Programm-Server sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines ConnectorRegistry-Client-Objekts**

Um Endpunkt-Connector-Informationen programmgesteuert abzurufen, erstellen Sie ein `ConnectorRegistryClient`-Objekt.

**Angeben des Connector-Typs**

Geben Sie den Typ des Connectors an, von dem aus Informationen abgerufen werden sollen. Die folgenden Typen von Connectoren sind vorhanden:

* **EJB**: Ermöglicht es einem Client-Programm, einen Service mithilfe des EJB-Modus aufzurufen.
* **SOAP**: Ermöglicht es einem Client-Programm, einen Service mithilfe des SOAP-Modus aufzurufen.
* **Überwachter Ordner**: Ermöglicht es überwachten Ordnern, einen Service aufzurufen.
* **Email**: Ermöglicht es E-Mail-Nachrichten, einen Service aufzurufen.
* **Remoting**: Ermöglicht es einem Flex-Client-Programm, einen Service aufzurufen.
* **TaskManagerConnector**: Ermöglicht es einem Workspace-Benutzer, einen Service von Workspace aus aufzurufen.

**Abrufen von Konfigurationswerten**

Nachdem Sie den Connector-Typ angegeben haben, können Sie Informationen zum Connector abrufen, z. B. den unterstützten Konfigurationswert. Beispielsweise können Sie für jeden Connector festlegen, welche Konfigurationswerte erforderlich sind und welche optional sind.

**Siehe auch**

[Abrufen von Endpunkt-Connector-Informationen mithilfe der Java-API](programmatically-endpoints.md#retrieve-endpoint-connector-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Endpunkt-Connector-Informationen mithilfe der Java-API {#retrieve-endpoint-connector-information-using-the-java-api}

So rufen Sie Endpunkt-Connector-Informationen mithilfe der Java-API ab:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt vom Typ ConnectorRegistry.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConnectorRegistryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Geben Sie den Connector-Typ an.

   Geben Sie den Connector-Typ an, indem Sie die `getEndpointDefinition`-Methode des `ConnectorRegistryClient`-Objekts verwenden und einen Zeichenfolgenwert übergeben, der den Connector-Typ angibt. Um beispielsweise den Connector-Typ „Überwachter Ordner“ anzugeben, übergeben Sie den Zeichenfolgenwert `WatchedFolder`. Diese Methode gibt ein `Endpoint`-Objekt zurück, das dem Connector-Typ entspricht.

1. Rufen Sie Konfigurationswerte ab.

   * Rufen Sie Konfigurationswerte ab, die mit diesem Endpunkt verknüpft sind, indem Sie die `getConfigParameters`-Methode des `Endpoint`-Objekts aufrufen. Diese Methode gibt ein Array von `ConfigParameter`-Objekten zurück.
   * Rufen Sie Informationen zu den einzelnen Konfigurationswerten ab, indem Sie jedes Element im Array abrufen. Jedes Element ist ein `ConfigParameter`-Objekt. Sie können beispielsweise feststellen, ob der Konfigurationswert erforderlich oder optional ist, indem Sie die `isRequired`-Methode des `ConfigParameter`-Objekts aufrufen. Wenn der Konfigurationswert erforderlich ist, gibt diese Methode `true` zurück.

**Siehe auch**

[Zusammenfassung der Schritte](programmatically-endpoints.md#summary-of-steps)

[Schnellstart: Abrufen von Endpunkt-Connector-Informationen mithilfe der Java-API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
