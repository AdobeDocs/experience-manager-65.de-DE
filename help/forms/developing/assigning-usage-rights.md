---
title: Verwendungsrechte zuweisen
seo-title: Verwendungsrechte zuweisen
description: Verwenden Sie die Java Client-API und die Web Service-API der Acrobat Reader DC Extensions, um Verwendungsrechte auf PDF-Dokumente anzuwenden und daraus zu entfernen.
seo-description: Verwenden Sie die Java Client-API und die Web Service-API der Acrobat Reader DC Extensions, um Verwendungsrechte auf PDF-Dokumente anzuwenden und daraus zu entfernen.
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
role: Developer
exl-id: 6af148eb-427a-4b54-9c5f-8750736882d8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3951'
ht-degree: 6%

---

# Zuweisen von Nutzungsrechten {#assigning-usage-rights}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Über den Acrobat Reader DC Extensions-Dienst {#about-the-acrobat-reader-dc-extensions-service}

Der Acrobat Reader DC Extensions-Dienst ermöglicht Ihrem Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader. Der Acrobat Reader DC Extensions-Dienst unterstützt alle PDF-Dokumente bis einschließlich PDF 1.7 vollständig. Er funktioniert mit Adobe Reader 7.0 und höher. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Reader geöffnet wird. Drittanbieterbenutzer benötigen keine zusätzliche Software oder Plug-ins, um mit den Dokumenten mit aktivierten Berechtigungen arbeiten zu können.

Sie können diese Aufgaben mithilfe des Acrobat Reader DC Extensions-Dienstes ausführen:

* Verwendungsrechte auf PDF-Dokumente anwenden Weitere Informationen finden Sie unter [Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Entfernen Sie Verwendungsrechte aus PDF-Dokumenten. Weitere Informationen finden Sie unter [Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Abrufen von Anmeldeinformationen. Weitere Informationen finden Sie unter [Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Anwenden von Verwendungsrechten auf PDF-Dokumente {#applying-usage-rights-to-pdf-documents}

Sie können mithilfe der Java Client-API und des Webdiensts der Acrobat Reader DC Extensions Verwendungsrechte auf PDF-Dokumente anwenden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzer, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

>[!NOTE]
>
>Beim Anwenden von Verwendungsrechten auf PDF-Dokumente mithilfe der `applyUsageRights`-Methode, die Teil der Java-API ist, können Sie den Parameter `isModeFinal` des Objekts `ReaderExtensionsOptionSpec` auf `false` setzen. Dadurch wird der Zähler für verarbeitete Formulare nicht aktualisiert und die Leistung verbessert. Wenn Sie sich nicht darum kümmern, den Zähler für verarbeitete Formulare zu aktualisieren, sollten Sie den Parameter `isModeFinal` auf `false` setzen.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So wenden Sie Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument ab.
1. Geben Sie die anzuwendenden Verwendungsrechte an.
1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.
1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Um programmgesteuert einen Acrobat Reader DC Extensions-Dienstvorgang durchzuführen, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Acrobat Reader DC Extensions-Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments**

Sie müssen ein PDF-Dokument abrufen, um Verwendungsrechte anwenden zu können. Berechtigungsaktivierte PDF-Dokumente enthalten ein Wörterbuch zu Verwendungsrechten. Wenn Adobe Reader ein Dokument öffnet, das ein solches Wörterbuch enthält, werden nur die im Wörterbuch für dieses Dokument angegebenen Verwendungsrechte aktiviert. Wenn das Dokument kein Wörterbuch für Verwendungsrechte enthält, erstellt der Acrobat Reader DC Extensions-Dienst eines. Wenn er bereits ein Wörterbuch enthält, überschreibt der Acrobat Reader DC Extensions-Dienst vorhandene Verwendungsrechte mit den von Ihnen angegebenen. Das Wörterbuch gibt an, welche Verwendungsrechte aktiviert sind. Wenn ein Benutzer das Dokument in Adobe Reader öffnet, sind nur die im Wörterbuch angegebenen Verwendungsrechte zulässig.

**Verwendungsrechte festlegen**

Die Verwendungsrechte, die Sie festlegen können, werden durch eine von Adobe Systems Incorporated erworbene Berechtigung bestimmt. Berechtigungen bieten normalerweise die Berechtigung zum Festlegen einer Gruppe verwandter Verwendungsrechte, z. B. für interaktive Formulare. Jede Berechtigung bietet das Recht, eine bestimmte Anzahl von PDF-Dokumenten mit aktivierten Berechtigungen zu erstellen. Eine Testberechtigung gibt die Möglichkeit, eine unbegrenzte Anzahl von Entwürfen von Dokumenten zu erstellen.

>[!NOTE]
>
>Wenn Sie versuchen, ein Nutzungsrecht zuzuweisen, das von Ihrer Berechtigung nicht zulässig ist, verursachen Sie eine Ausnahme.

**Verwendungsrechte auf das PDF-Dokument anwenden**

Um Verwendungsrechte auf ein PDF-Dokument anzuwenden, verweisen Sie auf den Alias der Berechtigung, die Sie zum Anwenden von Verwendungsrechten verwenden (eine Berechtigung wird normalerweise während der Installation von AEM Forms installiert). Außerdem müssen Sie das PDF-Dokument angeben, auf das die Verwendungsrechte angewendet werden. Informationen zum Konfigurieren einer Berechtigung finden Sie im Handbuch zum Installieren und Bereitstellen für Ihren Anwendungsserver.

**Das PDF-Dokument mit aktivierten Berechtigungen speichern**

Nachdem der Acrobat Reader DC Extensions-Dienst Verwendungsrechte auf ein PDF-Dokument angewendet hat, können Sie das PDF-Dokument mit aktivierten Berechtigungen als PDF-Datei speichern.

**Siehe auch**

[Verwendungsrechte mithilfe der Java-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Nutzungsrechte mithilfe der Web-Service-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Verwendungsrechte mithilfe der Java-API {#apply-usage-rights-using-the-java-api} anwenden

Wenden Sie mithilfe der Acrobat Reader DC Extensions-API (Java) Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das mithilfe seines Konstruktors Verwendungsrechte darstellt.
   * Rufen Sie für jedes Verwendungsrecht eine entsprechende Methode auf, die zum `UsageRights` -Objekt gehört. Um beispielsweise das Nutzungsrecht `enableFormFillIn` hinzuzufügen, rufen Sie die Methode `enableFormFillIn` des Objekts `UsageRights` auf und übergeben Sie `true`. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Acrobat Reader DC Extensions-Dienst erforderlich sind. Beim Aufrufen dieses Konstruktors müssen Sie die folgenden Werte angeben:

      * Das `UsageRights`-Objekt, das die Verwendungsrechte enthält, die auf das Dokument angewendet werden sollen.
      * Ein string -Wert, der eine Meldung angibt, die einem Benutzer angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen in Adobe Reader 7.x geöffnet wird. Diese Meldung wird in Adobe Reader 8.0 nicht angezeigt.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `applyUsageRights` -Methode des Objekts `ReaderExtensionsServiceClient` aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, auf das Verwendungsrechte angewendet werden.
      * Ein string -Wert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein string -Wert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)
   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das PDF-Dokument mit aktivierten Berechtigungen enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `applyUsageRights` -Methode zurückgegeben wurde).

**Siehe auch**

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Schnellstart (SOAP-Modus): Anwenden von Nutzungsrechten mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Nutzungsrechte mithilfe der Webdienst-API {#apply-usage-rights-using-the-web-service-api} anwenden

Wenden Sie mithilfe der Acrobat Reader DC Extensions-API (Webdienst) Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das Verwendungsrechte angewendet werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das mithilfe seines Konstruktors Verwendungsrechte darstellt.
   * Weisen Sie für jede Verwendungsberechtigung den Wert `true` dem entsprechenden Datenelement zu, das zum `UsageRights`-Objekt gehört. Um beispielsweise das Nutzungsrecht `enableFormFillIn` hinzuzufügen, weisen Sie `true` dem `UsageRights` -Datenelement des `enableFormFillIn` -Objekts zu. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Acrobat Reader DC Extensions-Dienst erforderlich sind.
   * Weisen Sie das `UsageRights`-Objekt dem `ReaderExtensionsOptionSpec`-Datenelement des `usageRights`-Objekts zu.
   * Weisen Sie dem `message`-Datenelement des Objekts `ReaderExtensionsOptionSpec` einen string -Wert zu, der die Meldung angibt, die ein Benutzer beim Öffnen des PDF-Dokuments mit aktivierten Berechtigungen in Adobe Reader sieht.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `applyUsageRights` -Methode des Objekts `ReaderExtensionsServiceClient` aufrufen und die folgenden Werte übergeben:

      * Das `BLOB`-Objekt, das das PDF-Dokument enthält, auf das Verwendungsrechte angewendet werden.
      * Ein string -Wert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein string -Wert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)
   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights`-Methode gibt ein `BLOB`-Objekt zurück, das das PDF-Dokument mit aktivierten Berechtigungen enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments mit aktivierten Berechtigungen darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `applyUsageRights` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen von Verwendungsrechten aus PDF-Dokumenten {#removing-usage-rights-from-pdf-documents}

Sie können Verwendungsrechte aus einem Dokument mit aktivierten Benutzerrechten entfernen. Das Entfernen von Verwendungsrechten aus einem PDF-Dokument mit aktivierten Verwendungsrechten ist auch erforderlich, um andere AEM Forms-Vorgänge darauf auszuführen. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie daher Vorgänge für ein Dokument mit aktivierten Benutzerrechten durchführen möchten, müssen Sie Verwendungsrechte aus dem PDF-Dokument entfernen, die anderen Vorgänge ausführen, z. B. das Dokument digital signieren, und dann erneut Verwendungsrechte auf das Dokument anwenden.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So entfernen Sie Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument mit aktivierten Berechtigungen ab.
1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Verwendungsrechten**

Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab, um Verwendungsrechte zu entfernen.

**Verwendungsrechte aus dem PDF-Dokument entfernen**

Nachdem Sie ein PDF-Dokument mit aktivierten Verwendungsrechten abgerufen haben, können Sie Verwendungsrechte entfernen. Nachdem Sie Verwendungsrechte entfernt haben, verfügt das PDF-Dokument beim Anzeigen in Adobe Reader über keine zusätzlichen Funktionen.

**PDF-Dokument speichern**

Sie können das PDF-Dokument, das keine Verwendungsrechte mehr enthält, als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann das PDF-Dokument in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Nutzungsrechte mit der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Nutzungsrechten mithilfe der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Entfernen Sie Verwendungsrechte mithilfe der Java-API {#remove-usage-rights-using-the-java-api}.

Entfernen Sie mithilfe der Acrobat Reader DC Extensions-API (Java) Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   Erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Verwendungsrechten darstellt, indem Sie dessen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `removeUsageRights`-Methode des Objekts `ReaderExtensionsServiceClient` aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung .PDF ist.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `removeUsageRights` -Methode zurückgegeben wurde).

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Schnellstart (SOAP-Modus): Entfernen von Verwendungsrechten aus einem PDF-Dokument mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen Sie Verwendungsrechte mithilfe der Webdienst-API {#remove-usage-rights-using-the-web-service-api}.

Entfernen Sie mithilfe der Acrobat Reader DC Extensions-API (Webdienst) Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments mit aktivierten Berechtigungen verwendet, aus dem Verwendungsrechte entfernt werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `removeUsageRights`-Methode des Objekts `ReaderExtensionsServiceClient` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `BLOB` -Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Speicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `removeUsageRights` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Anmeldeinformationen {#retrieving-credential-information}

Sie können Informationen zu den Anmeldedaten abrufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument mit aktivierten Verwendungsrechten verwendet wurden. Durch Abrufen von Informationen zu einer Berechtigung können Sie Informationen wie das Datum abrufen, nach dem das Zertifikat nicht mehr gültig ist.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um Informationen zu den Anmeldedaten abzurufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument verwendet wurden, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument mit aktivierten Berechtigungen ab.
1. Rufen Sie Informationen über die Berechtigung ab.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Verwendungsrechten**

Sie müssen ein PDF-Dokument mit aktivierten Berechtigungen abrufen, um Informationen über die Berechtigung abzurufen. Sie können auch Informationen zu einer Berechtigung abrufen, indem Sie ihren Alias angeben. Wenn Sie jedoch Informationen zu einer Berechtigung abrufen möchten, die zum Anwenden von Verwendungsrechten auf ein bestimmtes PDF-Dokument mit aktivierten Verwendungsrechten verwendet wurde, müssen Sie das Dokument abrufen.

**Informationen zur Berechtigung abrufen**

Nachdem Sie ein PDF-Dokument mit aktivierten Verwendungsrechten abgerufen haben, können Sie Informationen zu den Berechtigungen abrufen, mit denen Verwendungsrechte angewendet wurden. Sie können die folgenden Informationen über die Berechtigung abrufen:

* Die Meldung, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen geöffnet wird.
* Das Datum, nach dem die Berechtigung nicht mehr gültig ist.
* Das Datum, vor dem die Berechtigung nicht gültig ist.
* Die Verwendungsrechte, die für dieses PDF-Dokument mit aktivierten Benutzerrechten festgelegt wurden.
* Die Häufigkeit, mit der die Berechtigung verwendet wurde.

**Siehe auch**

[Nutzungsrechte mit der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Nutzungsrechten mithilfe der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Abrufen von Anmeldeinformationen mithilfe der Java-API {#retrieve-credential-information-using-the-java-api}

Abrufen von Anmeldeinformationen mithilfe der Acrobat Reader DC Extensions-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   Erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Verwendungsrechten darstellt, indem Sie dessen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments mit aktivierten Berechtigungen angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu den Berechtigungen ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet werden, indem Sie die `getDocumentUsageRights` -Methode des `ReaderExtensionsServiceClient` -Objekts aufrufen und das `com.adobe.idp.Document` -Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `GetUsageRightsResult` -Objekt zurück, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie die `getNotAfter` -Methode des Objekts `GetUsageRightsResult` aufrufen. Diese Methode gibt ein `java.util.Date` -Objekt zurück, das das Datum darstellt, nach dem die Berechtigung nicht mehr gültig ist.
   * Rufen Sie die Meldung ab, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Benutzerrechten geöffnet wird, indem Sie die `getMessage` -Methode des Objekts `GetUsageRightsResult` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Nachricht darstellt.

**Siehe auch**

[Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information)

[Schnellstart (SOAP-Modus): Abrufen von Anmeldeinformationen mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Anmeldeinformationen mithilfe der Webdienst-API {#retrieve-credential-information-using-the-web-service-api}

Abrufen von Anmeldeinformationen mithilfe der Acrobat Reader DC Extensions-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie ein `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments mit aktivierten Verwendungsrechten verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments mit aktivierten Rechten und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu den Berechtigungen ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet werden, indem Sie die `getDocumentUsageRights` -Methode des `ReaderExtensionsServiceClient` -Objekts aufrufen und das `com.adobe.idp.Document` -Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `GetUsageRightsResult` -Objekt zurück, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie den Wert des `GetUsageRightsResult` -Datenelements des Objekts `notAfter` abrufen. Der Datentyp dieses Datenelements ist `System.DateTime`.
   * Rufen Sie die Meldung ab, die beim Öffnen des PDF-Dokuments mit aktivierten Benutzerrechten in Adobe Reader angezeigt wird, indem Sie den Wert des `GetUsageRightsResult` -Datenelements des Objekts `message` abrufen. Der Datentyp dieses Datenelements ist eine Zeichenfolge.
   * Rufen Sie die Häufigkeit ab, mit der die Berechtigung verwendet wird, indem Sie den Wert des `GetUsageRightsResult` -Datenelements des Objekts `useCount` abrufen. Der Datentyp dieses Datenelements ist eine Ganzzahl.

**Siehe auch**

[Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
