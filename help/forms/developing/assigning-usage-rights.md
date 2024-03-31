---
title: Zuweisen von Verwendungsrechten
description: Verwenden Sie die Java Client-API und die Webservice-API der Acrobat Reader DC-Erweiterungen, um Verwendungsrechte auf PDF-Dokumente anzuwenden oder sie daraus zu entfernen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 6af148eb-427a-4b54-9c5f-8750736882d8
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3897'
ht-degree: 100%

---

# Zuweisen von Verwendungsrechten {#assigning-usage-rights}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Informationen zum Service „Acrobat Reader DC-Erweiterungen“ {#about-the-acrobat-reader-dc-extensions-service}

Der Service „Acrobat Reader DC-Erweiterungen“ ermöglicht Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweitern der Funktionalität von Adobe Reader. Der Service „Acrobat Reader DC-Erweiterungen“ unterstützt alle PDF-Dokumente bis einschließlich PDF 1.7 vollständig. Er funktioniert mit Adobe Reader 7.0 und höher. Der Service fügt einem PDF-Dokument Verwendungsrechte hinzu und aktiviert dadurch Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird. Externe Benutzer benötigen keine zusätzliche Software oder Plug-Ins für das Verwenden der berechtigungsaktivierten Dokumente.

Sie können diese Aufgaben mithilfe des Services „Acrobat Reader DC-Erweiterungen“ ausführen:

* Anwenden von Verwendungsrechten auf PDF-Dokumente. Weitere Informationen finden Sie unter [Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Entfernen von Verwendungsrechten aus PDF-Dokumenten. Weitere Informationen finden Sie unter [Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Abrufen von Anmeldeinformationen. Weitere Informationen finden Sie unter [Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Weitere Informationen zum Service „Acrobat Reader DC-Erweiterungen“ finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Anwenden von Verwendungsrechten auf PDF-Dokumente {#applying-usage-rights-to-pdf-documents}

Mit der Java-Client-API der Acrobat Reader DC-Erweiterungen und dem entsprechenden Webservice können Sie Verwendungsrechte auf PDF-Dokumente anwenden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzende, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

>[!NOTE]
>
>Beim Anwenden von Verwendungsrechten auf PDF-Dokumente mithilfe der Methode `applyUsageRights`, die Teil der Java-API ist, können Sie den Parameter `isModeFinal` des `ReaderExtensionsOptionSpec`-Objekts auf `false` setzen. Dadurch wird der Zähler für verarbeitete Formulare nicht aktualisiert, was die Leistung verbessert. Wenn Sie nicht an der Aktualisierung des Zählers für verarbeitete Formulare interessiert sind, wird empfohlen, den Parameter `isModeFinal` auf `false` zu setzen.

>[!NOTE]
>
>Weitere Informationen zum Service „Acrobat Reader DC-Erweiterungen“ finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um Verwendungsrechte auf ein PDF-Dokument anzuwenden, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.
1. Rufen Sie ein PDF-Dokument ab.
1. Geben Sie die anzuwendenden Verwendungsrechte an.
1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.
1. Speichern Sie das berechtigungsaktivierte PDF-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Client-Objekts für Acrobat Reader DC-Erweiterungen**

Um einen Vorgang für den Service „Acrobat Reader DC-Erweiterungen“ programmgesteuert durchführen zu können, müssen Sie ein Client-Objekt für den Service „Acrobat Reader DC-Erweiterungen“ erstellen. Wenn Sie die Java-API für Acrobat Reader DC-Erweiterungen verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Webservice-API für Acrobat Reader DC-Erweiterungen verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**Abrufen eines PDF-Dokuments**

Rufen Sie ein PDF-Dokument ab, um Verwendungsrechte anzuwenden. Berechtigungsaktivierte PDF-Dokumente enthalten ein Wörterbuch zu Verwendungsrechten. Wenn Adobe Reader ein Dokument öffnet, das ein solches Wörterbuch enthält, werden nur diejenigen Verwendungsrechte aktiviert, die im Wörterbuch für dieses Dokument angegeben sind. Wenn das Dokument kein Wörterbuch für Verwendungsrechte enthält, erstellt der Service „Acrobat Reader DC-Erweiterungen“ eines. Wenn es bereits ein Wörterbuch enthält, überschreibt der Service „Acrobat Reader DC-Erweiterungen“ vorhandene Verwendungsrechte mit den von Ihnen angegebenen. Das Wörterbuch gibt an, welche Verwendungsrechte aktiviert sind. Wenn ein Benutzer das Dokument in Adobe Reader öffnet, sind nur die im Wörterbuch angegebenen Verwendungsrechte zulässig.

**Angeben der anzuwendenden Verwendungsrechte**

Die Verwendungsrechte, die Sie festlegen können, werden durch eine von Adobe Systems Incorporated erworbene Berechtigung bestimmt. Diese Berechtigungen bieten normalerweise die Berechtigung zum Festlegen einer Gruppe verwandter Verwendungsrechte, z. B. für interaktive Formulare. Jede Berechtigung bietet das Recht, eine bestimmte Anzahl von berechtigungsaktivierten PDF-Dokumenten zu erstellen. Eine Testberechtigung gibt die Möglichkeit, eine unbegrenzte Anzahl von Entwürfen von Dokumenten zu erstellen.

>[!NOTE]
>
>Wenn Sie versuchen, ein Verwendungsrecht zuzuweisen, das im Rahmen Ihrer Berechtigung nicht zulässig ist, wird eine Ausnahme ausgelöst.

**Anwenden von Verwendungsrechten auf das PDF-Dokument**

Um Verwendungsrechte auf ein PDF-Dokument anzuwenden, verweisen Sie auf den Alias der Berechtigung, die Sie zum Anwenden von Verwendungsrechten verwenden (eine solche Berechtigung wird normalerweise während der Installation von AEM Forms installiert). Außerdem müssen Sie das PDF-Dokument angeben, auf das die Verwendungsrechte angewendet werden. Informationen zum Konfigurieren einer Berechtigung finden Sie im Handbuch zum Installieren und Bereitstellen für Ihren Programm-Server.

**Speichern des berechtigungsaktivierten PDF-Dokuments**

Nachdem der Service „Acrobat Reader DC-Erweiterungen“ Verwendungsrechte auf ein PDF-Dokument angewendet hat, können Sie das berechtigungsaktivierte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Anwenden von Verwendungsrechten mithilfe der Java-API](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Anwenden von Verwendungsrechten mithilfe der Webservice-API](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitung zur API des Services „Acrobat Reader DC-Erweiterungen“](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Anwenden von Verwendungsrechten mithilfe der Java-API {#apply-usage-rights-using-the-java-api}

So wenden Sie mithilfe der API für Acrobat Reader DC-Erweiterungen (Java) Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-reader-extensions-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument repräsentiert, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das die Verwendungsrechte darstellt, mithilfe seines Konstruktors.
   * Rufen Sie für jedes anzuwendende Verwendungsrecht eine entsprechende Methode auf, die zum `UsageRights`-Objekt gehört. Um beispielsweise das Verwendungsrecht `enableFormFillIn` hinzuzufügen, rufen Sie die Methode `enableFormFillIn` des `UsageRights`-Objekts auf und übergeben `true`. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Service „Acrobat Reader DC-Erweiterungen“ erforderlich sind. Beim Aufrufen dieses Konstruktors müssen Sie die folgenden Werte angeben:

      * Das `UsageRights`-Objekt, das die Verwendungsrechte enthält, die auf das Dokument angewendet werden sollen.
      * Ein Zeichenfolgenwert, der eine Meldung angibt, die ein Benutzer zu sehen bekommt, wenn das berechtigungsaktivierte PDF-Dokument in Adobe Reader 7.x geöffnet wird. Diese Meldung wird in Adobe Reader 8.0 nicht angezeigt.

   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die Methode `applyUsageRights` des `ReaderExtensionsServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, auf das die Verwendungsrechte angewendet werden.
      * Ein Zeichenfolgenwert, der den Alias der Berechtigung angibt, dank derer Sie Verwendungsrechte anwenden können.
      * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)

   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die Methode `applyUsageRights` gibt ein `com.adobe.idp.Document`-Objekt zurück, das das berechtigungsaktivierte PDF-Dokument enthält.

1. Speichern Sie das berechtigungsaktivierte PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `applyUsageRights` zurückgegeben wurde).

**Siehe auch**

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Kurzanleitung (SOAP-Modus): Anwenden von Verwendungsrechten mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Anwenden von Verwendungsrechten mithilfe der Webservice-API {#apply-usage-rights-using-the-web-service-api}

So wenden Sie mithilfe der API für Acrobat Reader DC-Erweiterungen (Webservice) Verwendungsrechte auf ein PDF-Dokument an:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL zu dem AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts im `ReaderExtensionsServiceClient.Endpoint.Binding`-Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das Verwendungsrechte angewendet werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie ein `UsageRights`-Objekt, das Verwendungsrechte darstellt, indem Sie seinen Konstruktor verwenden.
   * Weisen Sie für jedes anzuwendende Verwendungsrecht den Wert `true` dem entsprechenden Datenelement zu, das zum `UsageRights`-Objekt gehört. Um beispielsweise das `enableFormFillIn`-Verwendungsrecht hinzuzufügen, weisen Sie dem Datenelement `enableFormFillIn` des `UsageRights`-Objekts `true` zu. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Service „Acrobat Reader DC-Erweiterungen“ erforderlich sind.
   * Weisen Sie das `UsageRights`-Objekt dem Datenelement `usageRights` des `ReaderExtensionsOptionSpec`-Objekts zu.
   * Weisen Sie dem Datenelement `message` des `ReaderExtensionsOptionSpec`-Objekts einen Zeichenfolgenwert zu, der die Meldung angibt, die ein Benutzer zu sehen bekommt, wenn das berechtigungsaktivierte PDF-Dokument in Adobe Reader geöffnet wird.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die Methode `applyUsageRights` des `ReaderExtensionsServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

      * Das `BLOB`-Objekt, das das PDF-Dokument enthält, auf das die Verwendungsrechte angewendet werden.
      * Ein Zeichenfolgenwert, der den Alias der Berechtigung angibt, dank derer Sie Verwendungsrechte anwenden können.
      * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null` übergeben.)

   * Das `ReaderExtensionsOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die Methode `applyUsageRights` gibt ein `BLOB`-Objekt zurück, das das berechtigungsaktivierte PDF-Dokument enthält.

1. Speichern Sie das berechtigungsaktivierte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des berechtigungsaktivierten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `applyUsageRights` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Datenelements des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen von Verwendungsrechten aus PDF-Dokumenten {#removing-usage-rights-from-pdf-documents}

Sie können Verwendungsrechte aus einem berechtigungsaktivierten Dokument entfernen. Das Entfernen von Verwendungsrechten aus einem PDF-Dokument mit aktivieren Rechten ist auch erforderlich, um andere AEM Forms-Vorgänge damit durchführen zu können. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie demnach Vorgänge auf ein berechtigungsaktiviertes Dokument anwenden möchten, müssen Sie die Verwendungsrechte vom PDF-Dokument entfernen, die anderen Vorgänge anwenden (z. B. das Dokument digital signieren) und anschließend die Verwendungsrechte für das Dokument wieder aktivieren.

>[!NOTE]
>
>Weitere Informationen zum Service „Acrobat Reader DC-Erweiterungen“ finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um Verwendungsrechte aus einem berechtigungsaktivierten PDF-Dokument zu entfernen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Entfernen der Verwendungsrechte aus dem PDF-Dokument.
1. Speichern Sie das PDF-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Client-Objekts für Acrobat Reader DC-Erweiterungen**

Bevor Sie einen Service-Vorgang für Acrobat Reader DC-Erweiterungen programmgesteuert ausführen können, müssen Sie ein Service-Client-Objekt für Acrobat Reader DC-Erweiterungen erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Webservice-API für Acrobat Reader DC-Erweiterungen verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**Abrufen eines berechtigungsaktivierten PDF-Dokuments**

Rufen Sie ein PDF-Dokument mit aktivierten Rechten ab, um Verwendungsrechte zu entfernen.

**Entfernen von Verwendungsrechten aus dem PDF-Dokument**

Wenn Sie ein PDF-Dokument mit aktivierten Verwendungsrechten öffnen, können Sie diese entfernen. Nachdem Sie die Verwendungsrechte entfernt haben, verfügt das PDF-Dokument über keine zusätzlichen Funktionen, wenn es mit Adobe Reader geöffnet wird.

**Das PDF-Dokument speichern**

Sie können das PDF-Dokument, das keine Verwendungsrechte mehr enthält, als PDF-Datei speichern. Sobald das PDF-Dokument als PDF-Datei gespeichert wurde, kann es mit Adobe Reader oder Acrobat geöffnet werden.

**Siehe auch**

[Verwendungsrechte anhand der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Verwendungsrechte anhand der Web-Service-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitung zur API des Services „Acrobat Reader DC-Erweiterungen“](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Anwenden von Verwendungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Verwendungsrechte anhand der Java-API entfernen {#remove-usage-rights-using-the-java-api}

Entfernen der Verwendungsrechte aus einem PDF-Dokument mit aktivierten Verwendungsrechten anhand der API (Java) der Acrobat Reader DC Erweiterungen:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-reader-extensions-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Rechten darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen der Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie die Verwendungsrechte aus dem PDF-Dokument, indem Sie die `removeUsageRights`-Methode des `ReaderExtensionsServiceClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile`-Methode des `Document`-Objekts auf, um die Inhalte des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das von der `removeUsageRights`-Methode zurückgegebene `Document`-Objekt verwenden).

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Schnellstart (SOAP-Modus): Entfernen von Verwendungsrechten aus einem PDF-Dokument anhand der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verwendungsrechte anhand der Web-Service-API entfernen {#remove-usage-rights-using-the-web-service-api}

Entfernen der Verwendungsrechte aus einem PDF-Dokument mit aktivierten Rechten anhand der API der Acrobat Reader DC-Erweiterungen (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL zu dem AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts im `ReaderExtensionsServiceClient.Endpoint.Binding`-Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, aus dem die Verwendungsrechte entfernt werden sollen.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie diese der `MTOM`-Eigenschaft des Objekts zuweisen.

1. Entfernen der Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie die Verwendungsrechte aus dem PDF-Dokument, indem Sie die `removeUsageRights`-Methode des `ReaderExtensionsServiceClient`-Objekts aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie dessen Konstruktor aufrufen und eine Zeichenfolge übergeben, die den Speicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des von der Methode `removeUsageRights` zurückgegebenen `BLOB`-Objekts enthält. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Datenelements des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie dessen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Berechtigungsinformationen {#retrieving-credential-information}

Sie können Informationen zu den Berechtigungsdaten abrufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument mit aktivierten Benutzerrechten verwendet wurden. Durch das Abrufen von Informationen zu einer Berechtigung können Sie Informationen wie das Datum, nach dem das Zertifikat nicht mehr gültig ist, erhalten.

>[!NOTE]
>
>Weitere Informationen zum Service für Acrobat Reader DC-Erweiterungen finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um Informationen zu den Berechtigungen abzurufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument verwendet wurden, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Rufen Sie Informationen über die Berechtigung ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Client-Objekts für Acrobat Reader DC-Erweiterungen**

Bevor Sie einen Service-Vorgang für Acrobat Reader DC-Erweiterungen programmgesteuert ausführen können, müssen Sie ein Service-Client-Objekt für Acrobat Reader DC-Erweiterungen erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt. Wenn Sie die Webservice-API für Acrobat Reader DC-Erweiterungen verwenden, erstellen Sie ein `ReaderExtensionsServiceService`-Objekt.

**Abrufen eines berechtigungsaktivierten PDF-Dokuments**

Rufen Sie ein PDF-Dokument mit aktivierten Rechten ab, um Informationen über die Berechtigung zu erhalten. Sie können auch Informationen zu einer Berechtigung abrufen, indem Sie deren Alias angeben. Wenn Sie jedoch Informationen zu einer Berechtigung abrufen möchten, die zum Anwenden von Verwendungsrechten auf ein bestimmtes PDF-Dokument mit aktivierten Rechten verwendet wurde, müssen Sie das Dokument abrufen.

**Abrufen von Informationen zur Berechtigung**

Nachdem Sie ein PDF-Dokument mit aktivierten Verwendungsrechten abgerufen haben, können Sie Informationen zu der Berechtigung erhalten, mit der die Verwendungsrechte angewendet wurden. Sie können die folgenden Informationen über die Berechtigung abrufen:

* Die Nachricht, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Benutzerrechten geöffnet wird.
* Das Datum, nach dem die Berechtigung nicht mehr gültig ist.
* Das Datum, vor dem die Berechtigung nicht gültig ist.
* Die Verwendungsrechte, die für dieses PDF-Dokument mit aktivierten Benutzerrechten festgelegt wurden.
* Die Häufigkeit, mit der die Berechtigung verwendet wurde.

**Siehe auch**

[Verwendungsrechte anhand der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Verwendungsrechte anhand der Web-Service-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitung zur API des Services „Acrobat Reader DC-Erweiterungen“](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Abrufen von Berechtigungen mithilfe der Java-API {#retrieve-credential-information-using-the-java-api}

Abrufen von Berechtigungen mithilfe der API für Acrobat Reader DC-Erweiterungen (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-reader-extensions-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mit aktivierten Verwendungsrechten darstellt, indem Sie den Konstruktor des Objekts verwenden und eine Zeichenfolge übergeben, die den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen der Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu der Berechtigung ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet wird, indem Sie die Methode `getDocumentUsageRights` des `ReaderExtensionsServiceClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument enthält. Diese Methode gibt ein `GetUsageRightsResult`-Objekt mit Informationen zur Berechtigung zurück.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie die Methode `getNotAfter` des `GetUsageRightsResult`-Objekts aufrufen. Diese Methode gibt ein `java.util.Date`-Objekt zurück, das das Ablaufdatum der Berechtigung darstellt.
   * Rufen Sie die Nachricht ab, die in Adobe Reader beim Öffnen des PDF-Dokuments mit aktivierten Verwendungsberechtigungen angezeigt wird, indem Sie die Methode `getMessage` des `GetUsageRightsResult`-Objekts aufrufen. Diese Methode gibt eine Zeichenfolge zurück, die die Nachricht darstellt.

**Siehe auch**

[Abrufen von Berechtigungsinformationen](assigning-usage-rights.md#retrieving-credential-information)

[Schnellstart (SOAP-Modus): Abrufen von Informationen zu Berechtigungen mithilfe der Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Informationen zu Berechtigungen mithilfe der Web-Service-API {#retrieve-credential-information-using-the-web-service-api}

Abrufen von Informationen zu Berechtigungen mithilfe der API für Acrobat Reader DC-Erweiterungen (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC-Erweiterungen.

   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt mithilfe seines Standardkonstruktors.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `ReaderExtensionsServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL zu dem AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Stellen Sie sicher, dass Sie `?blob=mtom` angeben.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts im `ReaderExtensionsServiceClient.Endpoint.Binding`-Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments mit aktivierten Berechtigungen verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments mit aktivierten Berechtigungen und den Ausführungsmodus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie diese der `MTOM`-Eigenschaft des Objekts zuweisen.

1. Entfernen der Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu den Anmeldedaten für das Anwenden von Verwendungsrechten auf das PDF-Dokument ab, indem Sie die `getDocumentUsageRights`-Methode des `ReaderExtensionsServiceClient`-Objekts aufrufen und ihr das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt ein `GetUsageRightsResult`-Objekt mit den Anmeldeinformationen zurück.
   * Rufen Sie das Datum ab, nach dem die Anmeldedaten nicht mehr gültig sind, indem Sie den Wert des Datenelements `notAfter` des `GetUsageRightsResult`-Objekts abrufen. Der Datentyp dieses Datenelements lautet `System.DateTime`.
   * Rufen Sie die Meldung ab, die angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen in Adobe Reader geöffnet wird, indem Sie den Wert des Datenelement `message` des `GetUsageRightsResult`-Objekts abrufen. Der Datentyp dieses Datenelements ist eine Zeichenfolge.
   * Ermitteln Sie, wie oft die Anmeldedaten verwendet werden, indem Sie den Wert des Datenelements `useCount` des `GetUsageRightsResult`-Objekts abrufen. Der Datentyp dieses Datenelements ist eine Ganzzahl.

**Siehe auch**

[Abrufen von Berechtigungsinformationen](assigning-usage-rights.md#retrieving-credential-information)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
