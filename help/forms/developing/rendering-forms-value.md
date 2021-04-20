---
title: Rendern von Forms nach Wert
seo-title: Rendern von Forms nach Wert
description: Verwenden Sie die Forms API (Java), um ein Formular mit der Java API und der Web Service API wertmäßig zu rendern.
seo-description: Verwenden Sie die Forms API (Java), um ein Formular mit der Java API und der Web Service API wertmäßig zu rendern.
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1863'
ht-degree: 3%

---


# Rendern von Forms mit dem Wert {#rendering-forms-by-value}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

In der Regel wird ein in Designer erstellter Formularentwurf durch Verweis auf den Forms-Dienst weitergeleitet. Formularentwürfe können sehr umfangreich sein. Daher ist es effizienter, sie als Referenz weiterzugeben, um Formularentwurfssytes nicht nach Wert zu ordnen. Der Forms-Dienst kann den Formularentwurf auch zwischenspeichern, sodass er den Formularentwurf beim Zwischenspeichern nicht ständig lesen muss.

Wenn ein Formularentwurf ein UUID-Attribut enthält, wird er zwischengespeichert. Der UUID-Wert ist für alle Formularentwürfe eindeutig und dient zur eindeutigen Identifizierung eines Formulars. Beim Rendern eines Formulars als Wert sollte das Formular nur zwischengespeichert werden, wenn es wiederholt verwendet wird. Wenn das Formular jedoch nicht wiederholt verwendet wird und eindeutig sein muss, können Sie die Zwischenspeicherung des Formulars mithilfe von Zwischenspeicherungsoptionen vermeiden, die mit der AEM Forms API festgelegt werden.

Der Forms-Dienst kann auch die Position verknüpfter Inhalte im Formularentwurf auflösen. Verknüpfte Bilder, auf die im Formularentwurf verwiesen wird, sind beispielsweise relative URLs. Verknüpfte Inhalte werden immer als relativ zum Speicherort des Formularentwurfs betrachtet. Das Auflösen von verknüpften Inhalten ist daher eine Frage der Bestimmung der Position, indem der relative Pfad zum absoluten Speicherort des Formularentwurfs angewendet wird.

Anstatt einen Formularentwurf als Referenz zu übergeben, können Sie einen Formularentwurf als Wert übergeben. Die Weitergabe eines Formularentwurfs durch Wert ist effizient, wenn ein Formularentwurf dynamisch erstellt wird. das heißt, wenn eine Clientanwendung die XML generiert, die einen Formularentwurf während der Laufzeit erstellt. In diesem Fall wird ein Formularentwurf nicht in einem physischen Repository gespeichert, da er im Arbeitsspeicher gespeichert wird. Wenn Sie einen Formularentwurf zur Laufzeit dynamisch erstellen und ihn wertmäßig übergeben, können Sie das Formular zwischenspeichern und die Leistung des Forms-Dienstes verbessern.

**Einschränkungen bei der Übergabe eines Formulars nach Wert**

Die folgenden Einschränkungen gelten, wenn ein Formularentwurf nach Wert übergeben wird:

* Im Formularentwurf dürfen keine relativen verknüpften Inhalte enthalten sein. Alle Bilder und Fragmente müssen in den Formularentwurf eingebettet oder auf den unbedingt verwiesen werden.
* Serverseitige Berechnungen können nach der Wiedergabe des Formulars nicht mehr durchgeführt werden. Wenn das Formular zurück an den Forms-Dienst gesendet wird, werden die Daten extrahiert und ohne serverseitige Berechnungen zurückgegeben.
* Da HTML nur verknüpfte Bilder zur Laufzeit verwenden kann, ist es nicht möglich, HTML mit eingebetteten Bildern zu generieren. Der Forms-Dienst unterstützt eingebettete Bilder mit HTML, indem die Bilder von einem referenzierten Formularentwurf abgerufen werden. Da ein von Werten übergebener Formularentwurf keinen referenzierten Speicherort hat, können eingebettete Bilder nicht extrahiert werden, wenn die HTML-Seite angezeigt wird. Daher müssen Bildverweise absolute Pfade sein, die in HTML wiedergegeben werden sollen.

>[!NOTE]
>
>Obwohl Sie verschiedene Formulartypen nach Wert wiedergeben können (z. B. HTML-Formulare oder Formulare mit Verwendungsrechten), wird in diesem Abschnitt die Wiedergabe interaktiver PDF forms behandelt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein Formular als Wert:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Referenzieren Sie den Formularentwurf.
1. Formular wertmäßig wiedergeben
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie Daten programmgesteuert in eine PDF-Formular-Client-API importieren können, müssen Sie einen Data Integration-Dienstclient erstellen. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Referenzieren des Formularentwurfs**

Beim Rendern eines Formulars nach Wert müssen Sie ein `com.adobe.idp.Document`-Objekt erstellen, das den wiederzugebenden Formularentwurf enthält. Sie können auf eine vorhandene XDP-Datei verweisen oder einen Formularentwurf zur Laufzeit dynamisch erstellen und ein `com.adobe.idp.Document` mit diesen Daten füllen.

>[!NOTE]
>
>Dieser Abschnitt und der zugehörige Quick Beginn verweisen auf eine vorhandene XDP-Datei.

**Formular als Wert wiedergeben**

Um ein Formular als Wert wiederzugeben, übergeben Sie eine `com.adobe.idp.Document`-Instanz, die den Formularentwurf enthält, an den Parameter `inDataDoc` der Rendermethode (kann eine der Rendermethoden des `FormsServiceClient`-Objekts sein, z. B. `renderPDFForm`, `(Deprecated) renderHTMLForm` usw.). Dieser Parameterwert ist normalerweise für Daten reserviert, die mit dem Formular zusammengeführt werden. Übergeben Sie entsprechend einen leeren Zeichenfolgenwert an den Parameter `formQuery`. Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

>[!NOTE]
>
>Wenn Sie Daten im Formular anzeigen möchten, müssen die Daten im Element `xfa:datasets` angegeben werden. Informationen zur XFA-Architektur finden Sie unter [https://partners.adobe.com/public/developer/xml/index_arch.html](https://partners.adobe.com/public/developer/xml/index_arch.html).

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular wertmäßig wiedergibt, gibt er einen Formulardatenstream zurück, den Sie an den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Formular mit der Java-API wertmäßig wiedergeben](#render-a-form-by-value-using-the-java-api)

[Formular mit der Webdienst-API wertmäßig wiedergeben](#render-a-form-by-value-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Weiterleiten von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formular mit der Java-API {#render-a-form-by-value-using-the-java-api} wertmäßig wiedergeben

Rendern Sie ein Formular wertmäßig mit der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das den Formularentwurf darstellt, der mithilfe des Konstruktors wiedergegeben werden soll, und übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Formular als Wert wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und weisen Sie die Größe des Objekts `InputStream` zu. Rufen Sie die `available`-Methode des Objekts auf, um die Größe des `InputStream`-Objekts abzurufen.`InputStream`
   * Füllen Sie das Bytearray mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms nach Wert](/help/forms/developing/rendering-forms.md)

[Quick Beginn (SOAP-Modus): Rendern nach Wert mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formular mit der Webdienst-API {#render-a-form-by-value-using-the-web-service-api} wertmäßig wiedergeben

Wiedergabe eines Formulars nach Wert mit der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem Kennwort verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `java.io.FileInputStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Größe des `java.io.FileInputStream`-Objekts mit der `available`-Methode abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `java.io.FileInputStream`-Methode des Objekts `read` aufrufen und das Bytearray übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie die `setBinaryData`-Methode aufrufen und das Bytearray übergeben.

1. Formular als Wert wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `BLOB`-Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Auf diese Weise wird das gerenderte PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms nach Wert](#rendering-forms-by-value)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
