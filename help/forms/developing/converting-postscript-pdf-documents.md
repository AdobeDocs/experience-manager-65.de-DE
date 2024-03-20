---
title: Konvertieren von PostScript in PDF-Dokumente
description: Verwenden Sie den Distiller-Dienst, um PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien über ein Netzwerk in kompakte, zuverlässige und sichere PDF-Dateien zu konvertieren. Der Distiller-Dienst konvertiert große Mengen von Druckdokumenten in elektronische Dokumente, z. B. Rechnungen und Aussagen mithilfe der Java-API und der Web Service-API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 744df8b2-0c61-410f-89e9-20b8adddbf45
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 99%

---

# Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Über den Distiller-Dienst {#about-the-distiller-service}

Der Distiller®-Dienst konvertiert PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst dient häufig zum Konvertieren großen Mengen gedruckter Dokumente in elektronische Dokumente, z. B. Rechnungen und Belege. Das Konvertieren von Dokumenten in PDF ermöglicht Unternehmen auch, ihren Kunden eine Papier- und eine elektronische Version eines Dokuments zu senden.

>[!NOTE]
>
>Weitere Informationen über den Distiller-Dienst finden Sie unter [Dienst-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents-inner}

Hier wird beschrieben, wie Sie mit der Distiller Service API (Java- und Webdienst) PostScript- (PS), Encapsulated PostScript- (EPS) und PRN-Dateien programmgesteuert in PDF-Dokumente konvertieren können.

>[!NOTE]
>
>Weitere Informationen über den Distiller-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Um PostScript-Dateien in PDF-Dokumente zu konvertieren, muss eine der folgenden Komponenten auf dem Server installiert sein, auf dem AEM Forms gehostet wird: Acrobat 9 oder das weiterverteilbare Paket von Microsoft Visual C++ 2005.

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um einen der unterstützten Typen in ein PDF-Dokument zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Distiller-Dienstclient.
1. Rufen Sie die zu konvertierende Datei ab.
1. Rufen Sie den PDF-Erstellungsvorgang auf.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Distiller-Dienstclients**

Bevor Sie einen Distiller-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Distiller-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DistillerServiceClient`-Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `DistillerServiceService`-Objekt.

**Zu konvertierende Datei abrufen**

Rufen Sie die Datei ab, die Sie konvertieren möchten. Um beispielsweise eine PS-Datei in ein PDF-Dokument zu konvertieren, müssen Sie die PS-Datei abrufen.

**Aufrufen des PDF-Erstellungsvorgangs**

Nachdem Sie den Service-Client erstellt haben, können Sie den PDF-Erstellungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**Speichern Sie das PDF-Dokument**

Sie können das PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren einer PostScript-Datei in eine PDF mithilfe der Java-API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Konvertieren einer PostScript-Datei in eine PDF mithilfe der Webdienst-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Konvertieren einer PostScript-Datei in eine PDF mithilfe der Java-API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Konvertieren Sie eine PostScript-Datei mithilfe der Distiller Service API (Java) in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Nehmen Sie Client-JAR-Dateien, wie z. B. adobe-distiller-client.jar, in den Klassenpfad Ihres Java-Projekts auf.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DistillerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die zu konvertierende Datei mithilfe ihres Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die Methode `DistillerServiceClient` des Objekts `createPDF` auf und übergeben Sie die folgenden Werte:

   * Das `com.adobe.idp.Document`-Objekt, das die zu konvertierende PS-, EPS- oder PRN-Datei darstellt
   * Ein `java.lang.String`-Objekt, das den Namen der zu konvertierenden Datei enthält
   * Ein `java.lang.String`-Objekt, das den Namen der zu verwendenden Adobe PDF-Einstellungen enthält
   * Ein `java.lang.String`-Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält
   * Ein optionales `com.adobe.idp.Document` Objekt, das Einstellungen enthält, die bei der Erstellung des PDF-Dokuments angewendet werden sollen
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Metadaten enthält, die auf das PDF-Dokument angewendet werden sollen.

   Die `createPDF`-Methode gibt ein `CreatePDFResult`-Objekt zurück, das das neue PDF-Dokument und eine eventuell erzeugte Protokolldatei enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die durch den Konvertierungsauftrag erzeugt werden.

1. Speichern Sie das PDF-Dokument.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `CreatePDFResult`-Objekt`getCreatedDocument`-Methode auf. Dadurch wird ein `com.adobe.idp.Document`-Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` Methode des Objekts `copyToFile` auf, um das PDF-Dokument zu extrahieren.

   Um das Protokolldokument abzurufen, führen Sie die folgenden Schritte aus.

   * Rufen Sie die `CreatePDFResult` Methode des `getLogDocument` Objekts auf. Dadurch wird ein `com.adobe.idp.Document`-Objekt zurückgegeben.
   * Um das Protokolldokument zu entnehmen, rufen Sie die `copyToFile`Methode des `com.adobe.idp.Document`-Objekts auf.

**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

[Quick Start (SOAP-Modus): Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren einer PostScript-Datei in eine PDF mithilfe der Webdienst-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Konvertieren Sie eine PostScript-Datei in ein PDF-Dokument, indem Sie die Distiller Service API (Webservice) verwenden:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, der AEM Forms hostet.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `DistillerServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DistillerServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/DistillerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `DistillerServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DistillerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DistillerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird verwendet, um die Datei zu speichern, die in ein PDF-Dokument konvertiert werden soll.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen String-Wert übergeben, der den Speicherort der Datei und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays belegen.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die Methode `DistillerServiceService` des Objekts `CreatePDF2` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Das `BLOB`-Objekt, das die zu konvertierende PS-Datei darstellt
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Adobe PDF-Einstellungen enthält (z. B. `Standard`)
   * Ein string -Objekt, das die zu verwendenden Sicherheitseinstellungen enthält (z. B. `No Securit`y)
   * Ein optionales `BLOB`-Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `BLOB`-Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen
   * Ein `BLOB`-Ausgabeparameter, der zum Speichern des PDF-Dokuments verwendet wird
   * Ein `BLOB`-Ausgabeparameter, der zum Speichern des Protokolls verwendet wird

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der `CreatePDF2`-Methode zurückgegeben wurde (der Ausgabeparameter). Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
