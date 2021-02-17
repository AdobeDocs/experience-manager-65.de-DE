---
title: Verwendungsrechte zuweisen
seo-title: Verwendungsrechte zuweisen
description: Verwenden Sie die Acrobat Reader DC Extensions Java Client API und die Web Service API, um Verwendungsrechte für PDF-Dokumente anzuwenden und zu entfernen.
seo-description: Verwenden Sie die Acrobat Reader DC Extensions Java Client API und die Web Service API, um Verwendungsrechte für PDF-Dokumente anzuwenden und zu entfernen.
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '3937'
ht-degree: 6%

---


# Verwendungsrechte zuweisen {#assigning-usage-rights}

## Info zum Acrobat Reader DC Extensions-Dienst {#about-the-acrobat-reader-dc-extensions-service}

Der Acrobat Reader DC Extensions-Dienst ermöglicht Ihrem Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader. Der Acrobat Reader DC Extensions-Dienst unterstützt alle PDF-Dokumente bis einschließlich PDF 1.7 vollständig. Es funktioniert mit Adobe Reader 7.0 und höher. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Reader geöffnet wird. Drittanbieterbenutzer benötigen keine zusätzliche Software oder Plug-Ins, um mit den Dokumenten mit aktivierten Benutzerrechten arbeiten zu können.

Sie können diese Aufgaben mit dem Acrobat Reader DC Extensions-Dienst ausführen:

* Verwendungsrechte auf PDF-Dokumente anwenden Weitere Informationen finden Sie unter [Verwendungsrechte auf PDF-Dokumente anwenden](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Entfernen Sie Verwendungsrechte aus PDF-Dokumenten. Weitere Informationen finden Sie unter [Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Berechtigungsdetails abrufen. Weitere Informationen finden Sie unter [Abrufen von Berechtigungsinformationen](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Verwendungsrechte auf PDF-Dokumente anwenden {#applying-usage-rights-to-pdf-documents}

Sie können Verwendungsrechte auf PDF-Dokumente mit der Acrobat Reader DC Extensions Java Client-API und dem Webdienst anwenden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzer, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

>[!NOTE]
>
>Beim Anwenden von Verwendungsrechten auf PDF-Dokumente mit der Methode `applyUsageRights`, die Teil der Java-API ist, können Sie den Parameter `isModeFinal` des Objekts `ReaderExtensionsOptionSpec` auf `false` setzen. Dadurch wird der Zähler für verarbeitete Formulare nicht aktualisiert und die Leistung verbessert. Wenn Sie den Zähler für verarbeitete Formulare nicht aktualisieren möchten, sollten Sie den Parameter `isModeFinal` auf `false` setzen.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So wenden Sie Verwendungsrechte auf ein PDF-Dokument an:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.
1. PDF-Dokument abrufen
1. Geben Sie die anzuwendenden Verwendungsrechte an.
1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.
1. Speichern Sie das PDF-Dokument mit aktivierten Verwendungsrechten.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Acrobat Reader DC Extensions-Client-Objekt erstellen**

Um einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert durchzuführen, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Acrobat Reader DC Extensions Java API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**PDF-Dokument abrufen**

Sie müssen ein PDF-Dokument abrufen, um Verwendungsrechte anzuwenden. Für Rechte aktivierte PDF-Dokumente enthalten ein Wörterbuch mit Verwendungsrechten. Wenn Adobe Reader ein Dokument öffnet, das ein solches Wörterbuch enthält, aktiviert es nur die im Wörterbuch angegebenen Verwendungsrechte für dieses Dokument. Wenn das Dokument kein Wörterbuch mit Verwendungsrechten enthält, erstellt der Acrobat Reader DC Extensions-Dienst eines. Wenn der Acrobat Reader DC Extensions-Dienst bereits ein Wörterbuch enthält, überschreibt er vorhandene Verwendungsrechte mit den von Ihnen angegebenen. Das Wörterbuch gibt an, welche Verwendungsrechte aktiviert sind. Wenn ein Benutzer das Dokument in Adobe Reader öffnet, sind nur die im Wörterbuch angegebenen Verwendungsrechte zulässig.

**Verwendungsrechte festlegen**

Die Verwendungsrechte, die Sie festlegen können, werden durch eine Berechtigung festgelegt, die Sie bei Adobe Systems Incorporated erwerben. Berechtigungen bieten in der Regel die Berechtigung zum Festlegen einer Gruppe verwandter Verwendungsrechte, z. B. für interaktive Formulare. Jede Berechtigung bietet das Recht, eine bestimmte Anzahl von PDF-Dokumenten mit aktivierten Benutzerrechten zu erstellen. Eine Testberechtigung berechtigt zur Erstellung einer unbegrenzten Anzahl von Dokumenten.

>[!NOTE]
>
>Wenn Sie versuchen, ein Verwendungsrecht zuzuweisen, das in Ihrer Berechtigung nicht zulässig ist, verursachen Sie eine Ausnahme.

**Verwendungsrechte auf das PDF-Dokument anwenden**

Um Verwendungsrechte auf ein PDF-Dokument anzuwenden, verweisen Sie auf den Alias der Berechtigung, mit der Sie Verwendungsrechte anwenden (eine Berechtigung wird normalerweise während der Installation von AEM Forms installiert). Außerdem müssen Sie das PDF-Dokument angeben, auf das Verwendungsrechte angewendet werden. Weitere Informationen zum Konfigurieren einer Berechtigung finden Sie im Handbuch zum Installieren und Bereitstellen für Ihren Anwendungsserver.

**Speichern des PDF-Dokuments mit aktivierten Verwendungsrechten**

Nachdem der Acrobat Reader DC Extensions-Dienst Verwendungsrechte auf ein PDF-Dokument angewendet hat, können Sie das PDF-Dokument mit aktivierten Verwendungsrechten als PDF-Datei speichern.

**Siehe auch**

[Verwendungsrechte mithilfe der Java-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Verwendungsrechte mithilfe der Webdienst-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Verwendungsrechte mit der Java-API {#apply-usage-rights-using-the-java-api} anwenden

Anwenden von Verwendungsrechten auf ein PDF-Dokument mithilfe der Acrobat Reader DC Extensions API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-reader-extensions-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das mithilfe des Konstruktors Verwendungsrechte darstellt.
   * Rufen Sie für jedes Verwendungsrecht eine entsprechende Methode auf, die zum `UsageRights`-Objekt gehört. Um beispielsweise das Verwendungsrecht `enableFormFillIn` hinzuzufügen, rufen Sie die `UsageRights`-Methode des Objekts `enableFormFillIn` auf und übergeben Sie `true`. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die vom Acrobat Reader DC Extensions-Dienst benötigt werden. Beim Aufrufen dieses Konstruktors müssen Sie die folgenden Werte angeben:

      * Das `UsageRights`-Objekt mit den auf das Dokument anzuwendenden Verwendungsrechten.
      * Ein Zeichenfolgenwert, der eine Meldung angibt, die einem Benutzer angezeigt wird, wenn das PDF-Dokument mit aktivierten Benutzerrechten in Adobe Reader 7.x geöffnet wird. Diese Meldung wird in Adobe Reader 8.0 nicht angezeigt.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `ReaderExtensionsServiceClient`-Objektmethode `applyUsageRights` aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, auf das Verwendungsrechte angewendet werden.
      * Ein Zeichenfolgenwert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)
   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das PDF-Dokument mit aktivierten Rechten enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Verwendungsrechten.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `applyUsageRights`-Methode zurückgegeben wurde).`com.adobe.idp.Document`

**Siehe auch**

[Verwendungsrechte auf PDF-Dokumente anwenden](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Quick Beginn (SOAP-Modus):Verwendungsrechte mithilfe der Java-API anwenden](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verwendungsrechte mithilfe der Webdienst-API {#apply-usage-rights-using-the-web-service-api} anwenden

Anwenden von Verwendungsrechten auf ein PDF-Dokument mithilfe der Acrobat Reader DC Extensions API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das Verwendungsrechte angewendet werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das mithilfe des Konstruktors Verwendungsrechte darstellt.
   * Weisen Sie für jedes Verwendungsrecht den Wert `true` dem entsprechenden Datenmember zu, der zum `UsageRights`-Objekt gehört. Um beispielsweise das Verwendungsrecht `enableFormFillIn` hinzuzufügen, weisen Sie `true` dem `UsageRights`-Datenmember des Objekts `enableFormFillIn` zu. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die vom Acrobat Reader DC Extensions-Dienst benötigt werden.
   * Weisen Sie das `UsageRights`-Objekt dem `ReaderExtensionsOptionSpec`-Datenelement des Objekts `usageRights` zu.
   * Weisen Sie dem Datenmember des Objekts `message` einen Zeichenfolgenwert zu, der die Meldung angibt, die ein Benutzer beim Öffnen des PDF-Dokuments mit aktivierten Benutzerrechten in Adobe Reader sieht.`ReaderExtensionsOptionSpec`
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `ReaderExtensionsServiceClient`-Objektmethode `applyUsageRights` aufrufen und die folgenden Werte übergeben:

      * Das `BLOB`-Objekt, das das PDF-Dokument enthält, auf das Verwendungsrechte angewendet werden.
      * Ein Zeichenfolgenwert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)
   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights`-Methode gibt ein `BLOB`-Objekt zurück, das das PDF-Dokument mit aktivierten Rechten enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Verwendungsrechten.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments mit aktivierten Benutzerrechten darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `applyUsageRights`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Verwendungsrechte auf PDF-Dokumente anwenden](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen von Verwendungsrechten aus PDF-Dokumenten {#removing-usage-rights-from-pdf-documents}

Sie können Verwendungsrechte aus einem Dokument mit aktivierten Benutzerrechten entfernen. Das Entfernen von Verwendungsrechten aus einem PDF-Dokument mit aktivierten Verwendungsrechten ist auch erforderlich, um andere AEM Forms-Vorgänge darauf auszuführen. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie daher Vorgänge für ein Dokument mit aktivierten Benutzerrechten ausführen möchten, müssen Sie Verwendungsrechte aus dem PDF-Dokument entfernen, andere Vorgänge wie das digitale Signieren des Dokuments ausführen und anschließend erneut Verwendungsrechte auf das Dokument anwenden.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So entfernen Sie Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Acrobat Reader DC Extensions-Client-Objekt erstellen**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Verwendungsrechten**

Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab, um Verwendungsrechte zu entfernen.

**Verwendungsrechte aus dem PDF-Dokument entfernen**

Nachdem Sie ein PDF-Dokument mit aktivierten Verwendungsrechten abgerufen haben, können Sie Verwendungsrechte entfernen. Nachdem Sie Verwendungsrechte entfernt haben, verfügt das PDF-Dokument bei der Anzeige in Adobe Reader über keine zusätzlichen Funktionen.

**PDF-Dokument speichern**

Sie können das PDF-Dokument, das keine Verwendungsrechte mehr enthält, als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann das PDF-Dokument in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Entfernen von Verwendungsrechten mit der Java-API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Verwendungsrechten mit der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Verwendungsrechte auf PDF-Dokumente anwenden](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Entfernen Sie Verwendungsrechte mit der Java-API {#remove-usage-rights-using-the-java-api}.

Entfernen Sie mithilfe der Acrobat Reader DC Extensions-API (Java) Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-reader-extensions-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF-Dokument abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Verwendungsrechten darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `ReaderExtensionsServiceClient`-Objektmethode `removeUsageRights` aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Benutzerrechten enthält. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .PDF ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `removeUsageRights`-Methode zurückgegeben wurde).`Document`

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Quick Beginn (SOAP-Modus): Entfernen von Verwendungsrechten aus einem PDF-Dokument mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen Sie Verwendungsrechte mithilfe der Webdienst-API {#remove-usage-rights-using-the-web-service-api}.

Entfernen Sie Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten mithilfe der Acrobat Reader DC Extensions API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, für das Verwendungsrechte entfernt wurden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `ReaderExtensionsServiceClient`-Objektmethode `removeUsageRights` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument mit aktivierten Benutzerrechten enthält. Diese Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `removeUsageRights`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Berechtigungsinformationen {#retrieving-credential-information}

Sie können Informationen über die Berechtigung abrufen, mit der Verwendungsrechte auf ein PDF-Dokument mit aktivierten Verwendungsrechten angewendet wurden. Durch Abrufen von Informationen zu einer Berechtigung können Sie Informationen abrufen, z. B. das Datum, nach dem das Zertifikat nicht mehr gültig ist.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

So rufen Sie Informationen über die Berechtigung ab, mit der Verwendungsrechte auf ein PDF-Dokument angewendet wurden:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Rufen Sie Informationen zur Berechtigung ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Acrobat Reader DC Extensions-Client-Objekt erstellen**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Verwendungsrechten**

Sie müssen ein PDF-Dokument mit aktivierten Benutzerrechten abrufen, um Informationen zur Berechtigung abrufen zu können. Sie können auch Informationen zu einer Berechtigung abrufen, indem Sie deren Alias angeben. Wenn Sie jedoch Informationen zu einer Berechtigung abrufen möchten, die zum Anwenden von Verwendungsrechten auf ein bestimmtes PDF-Dokument mit aktivierten Benutzerrechten verwendet wurde, müssen Sie das Dokument abrufen.

**Informationen zur Berechtigung abrufen**

Nachdem Sie ein PDF-Dokument mit aktivierten Verwendungsrechten abgerufen haben, können Sie Informationen zu den Berechtigungen abrufen, mit denen Verwendungsrechte darauf angewendet wurden. Sie können die folgenden Informationen zur Berechtigung abrufen:

* Die Meldung, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Benutzerrechten geöffnet wird.
* Das Datum, nach dem die Berechtigung nicht mehr gültig ist.
* Das Datum, vor dem die Berechtigung ungültig ist.
* Die Verwendungsrechte, die für dieses PDF-Dokument mit aktivierten Verwendungsrechten festgelegt wurden.
* Die Häufigkeit, mit der die Berechtigung verwendet wurde.

**Siehe auch**

[Entfernen von Verwendungsrechten mit der Java-API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Verwendungsrechten mit der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Abrufen von Anmeldeinformationen mit der Java-API {#retrieve-credential-information-using-the-java-api}

Abrufen von Anmeldeinformationen mithilfe der Acrobat Reader DC Extensions-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-reader-extensions-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF-Dokument abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Verwendungsrechten darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt, für das Rechte aktiviert sind.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen über die Berechtigung ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet wird, indem Sie die `getDocumentUsageRights`-Methode des Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Verwendungsrechten enthält. `ReaderExtensionsServiceClient` Diese Methode gibt ein `GetUsageRightsResult`-Objekt zurück, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie die `getNotAfter`-Methode des Objekts aufrufen. `GetUsageRightsResult` Diese Methode gibt ein `java.util.Date`-Objekt zurück, das das Datum darstellt, nach dem die Berechtigung nicht mehr gültig ist.
   * Rufen Sie die Meldung ab, die in Adobe Reader beim Öffnen des PDF-Dokuments mit aktivierten Benutzerrechten angezeigt wird, indem Sie die `GetUsageRightsResult`-Objektmethode `getMessage` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Meldung darstellt.

**Siehe auch**

[Abrufen von Berechtigungsinformationen](assigning-usage-rights.md#retrieving-credential-information)

[Quick Beginn (SOAP-Modus): Abrufen von Anmeldeinformationen mit der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Anmeldeinformationen mithilfe der Webdienst-API {#retrieve-credential-information-using-the-web-service-api}

Abrufen von Anmeldeinformationen mit der Acrobat Reader DC Extensions-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Acrobat Reader DC Extensions-Client-Objekt.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `ReaderExtensionsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments mit aktivierten Benutzerrechten verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments mit aktivierten Rechten und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen über die Berechtigung ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet wird, indem Sie die `getDocumentUsageRights`-Methode des Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Verwendungsrechten enthält. `ReaderExtensionsServiceClient` Diese Methode gibt ein `GetUsageRightsResult`-Objekt zurück, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie den Wert des `GetUsageRightsResult`-Datenelements des Objekts `notAfter` abrufen. Der Datentyp dieses Datenelements ist `System.DateTime`.
   * Rufen Sie die Meldung ab, die beim Öffnen des PDF-Dokuments mit aktivierten Benutzerrechten in Adobe Reader angezeigt wird, indem Sie den Wert des `GetUsageRightsResult`-Datenelements des Objekts `message` abrufen. Der Datentyp dieses Datenelements ist eine Zeichenfolge.
   * Rufen Sie ab, wie oft die Berechtigung verwendet wird, indem Sie den Wert des `GetUsageRightsResult`-Datenelements des Objekts `useCount` abrufen. Der Datentyp dieses Datenelements ist eine Ganzzahl.

**Siehe auch**

[Abrufen von Berechtigungsinformationen](assigning-usage-rights.md#retrieving-credential-information)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
