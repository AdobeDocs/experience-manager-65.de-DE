---
title: Wiedergabe von Formularen nach Wert
seo-title: Wiedergabe von Formularen nach Wert
description: 'null'
seo-description: 'null'
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Wiedergabe von Formularen nach Wert {#rendering-forms-by-value}

In der Regel wird ein in Designer erstellter Formularentwurf durch Verweis auf den Forms-Dienst weitergeleitet. Formularentwürfe können sehr umfangreich sein. Daher ist es effizienter, sie als Referenz weiterzugeben, um Formularentwurfssytes nicht nach Wert zu ordnen. Der Forms-Dienst kann den Formularentwurf auch zwischenspeichern, sodass er den Formularentwurf beim Zwischenspeichern nicht kontinuierlich lesen muss.

Wenn ein Formularentwurf ein UUID-Attribut enthält, wird er zwischengespeichert. Der UUID-Wert ist für alle Formularentwürfe eindeutig und dient zur eindeutigen Identifizierung eines Formulars. Beim Rendern eines Formulars als Wert sollte das Formular nur zwischengespeichert werden, wenn es wiederholt verwendet wird. Wenn das Formular jedoch nicht wiederholt verwendet wird und eindeutig sein muss, können Sie die Zwischenspeicherung des Formulars mithilfe der Zwischenspeicherungsoptionen vermeiden, die mit der AEM Forms-API festgelegt werden.

Der Forms-Dienst kann auch die Position verknüpfter Inhalte im Formularentwurf auflösen. Verknüpfte Bilder, auf die im Formularentwurf verwiesen wird, sind beispielsweise relative URLs. Verknüpfte Inhalte werden immer als relativ zum Speicherort des Formularentwurfs betrachtet. Das Auflösen von verknüpften Inhalten ist daher eine Frage der Bestimmung der Position, indem der relative Pfad zum absoluten Speicherort des Formularentwurfs angewendet wird.

Anstatt einen Formularentwurf als Referenz zu übergeben, können Sie ihn als Wert übergeben. Die Weitergabe eines Formularentwurfs durch Wert ist effizient, wenn ein Formularentwurf dynamisch erstellt wird. das heißt, wenn eine Clientanwendung die XML generiert, die einen Formularentwurf während der Laufzeit erstellt. In diesem Fall wird ein Formularentwurf nicht in einem physischen Repository gespeichert, da er im Arbeitsspeicher gespeichert wird. Wenn Sie einen Formularentwurf zur Laufzeit dynamisch erstellen und als Wert übergeben, können Sie das Formular zwischenspeichern und die Leistung des Forms-Dienstes verbessern.

**Einschränkungen bei der Übergabe eines Formulars nach Wert**

Die folgenden Einschränkungen gelten, wenn ein Formularentwurf nach Wert übergeben wird:

* Im Formularentwurf dürfen keine relativen verknüpften Inhalte enthalten sein. Alle Bilder und Fragmente müssen in den Formularentwurf eingebettet oder auf den unbedingt verwiesen werden.
* Serverseitige Berechnungen können nach der Wiedergabe des Formulars nicht mehr durchgeführt werden. Wenn das Formular zurück an den Forms-Dienst gesendet wird, werden die Daten extrahiert und ohne serverseitige Berechnungen zurückgegeben.
* Da HTML nur verknüpfte Bilder zur Laufzeit verwenden kann, ist es nicht möglich, HTML mit eingebetteten Bildern zu generieren. Der Forms-Dienst unterstützt eingebettete Bilder mit HTML, indem die Bilder von einem referenzierten Formularentwurf abgerufen werden. Da ein von Werten übergebener Formularentwurf keinen referenzierten Speicherort hat, können eingebettete Bilder nicht extrahiert werden, wenn die HTML-Seite angezeigt wird. Daher müssen Bildverweise absolute Pfade sein, die in HTML wiedergegeben werden sollen.

>[!NOTE]
>
>Obwohl Sie verschiedene Formulartypen nach Wert wiedergeben können (z. B. HTML-Formulare oder Formulare mit Verwendungsrechten), wird in diesem Abschnitt die Wiedergabe interaktiver PDF-Formulare behandelt.

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein Formular als Wert:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Referenzieren Sie den Formularentwurf.
1. Formular wertmäßig wiedergeben
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie Daten programmgesteuert in eine PDF-Formular-Client-API importieren können, müssen Sie einen Data Integration-Dienstclient erstellen. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Referenzieren des Formularentwurfs**

Beim Rendern eines Formulars nach Wert müssen Sie ein `com.adobe.idp.Document` Objekt erstellen, das den zu rendernden Formularentwurf enthält. Sie können auf eine vorhandene XDP-Datei verweisen oder einen Formularentwurf zur Laufzeit dynamisch erstellen und eine `com.adobe.idp.Document` mit diesen Daten füllen.

>[!NOTE]
>
>Dieser Abschnitt und der zugehörige Schnellstart verweisen auf eine vorhandene XDP-Datei.

**Formular als Wert wiedergeben**

Um ein Formular als Wert wiederzugeben, übergeben Sie eine `com.adobe.idp.Document` Instanz mit dem Formularentwurf an den `inDataDoc` -Parameter der Rendermethode (kann eine beliebige der Rendermethoden des `FormsServiceClient` Objekts sein, z. B. `renderPDFForm`, `(Deprecated) renderHTMLForm`usw.). Dieser Parameterwert ist normalerweise für Daten reserviert, die mit dem Formular zusammengeführt werden. Übergeben Sie entsprechend einen leeren Zeichenfolgenwert an den `formQuery` Parameter. Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

>[!NOTE]
>
>Wenn Sie Daten im Formular anzeigen möchten, müssen die Daten im `xfa:datasets` Element angegeben werden. Informationen zur XFA-Architektur finden Sie unter [https://partners.adobe.com/public/developer/xml/index_arch.html](https://partners.adobe.com/public/developer/xml/index_arch.html).

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular nach Wert wiedergibt, gibt er einen Formulardatenstream zurück, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Formular mit der Java-API wertmäßig wiedergeben](#render-a-form-by-value-using-the-java-api)

[Formular mit der Webdienst-API wertmäßig wiedergeben](#render-a-form-by-value-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formular mit der Java-API wertmäßig wiedergeben {#render-a-form-by-value-using-the-java-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das den zu rendernden Formularentwurf darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Formular als Wert wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `com.adobe.idp.Document` Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderPDFForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und weisen Sie die Größe des `InputStream` Objekts zu. Rufen Sie die `InputStream` Methode des `available` Objekts auf, um die Größe des `InputStream` Objekts abzurufen.
   * Füllen Sie das Byte-Array mit dem Formulardatenstream, indem Sie die `InputStream` `read`Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von Formularen nach Wert](/help/forms/develop/rendering-forms-rendering-forms-forms-value-rendering-forms.md#rendering-forms-by-value)

[Kurzanleitung (SOAP-Modus): Rendern nach Wert mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formular mit der Webdienst-API wertmäßig wiedergeben {#render-a-form-by-value-using-the-web-service-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern eines mit einem Kennwort verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein Bytearray, das den Inhalt des `java.io.FileInputStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Größe des `java.io.FileInputStream` Objekts mithilfe der `available` Methode abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `java.io.FileInputStream` Objektmethode aufrufen und das Bytearray `read` übergeben.
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `setBinaryData` Methode aufrufen und das Bytearray übergeben.

1. Formular als Wert wiedergeben

   Rufen Sie die `FormsService` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `BLOB` Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode gefüllt wird. Auf diese Weise wird das gerenderte PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `renderPDFForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von Formularen nach Wert](#rendering-forms-by-value)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
