---
title: Rendern von Forms nach Wert
seo-title: Rendern von Forms nach Wert
description: Verwenden Sie die Forms-API (Java), um ein Formular mit Werten mithilfe der Java-API und der Web Service-API zu rendern.
seo-description: Verwenden Sie die Forms-API (Java), um ein Formular mit Werten mithilfe der Java-API und der Web Service-API zu rendern.
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
role: Developer
exl-id: a3a6a06d-ec90-4147-a5f0-e776a086ee12
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1862'
ht-degree: 3%

---

# Rendern von Forms nach Wert {#rendering-forms-by-value}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

In der Regel wird ein in Designer erstellter Formularentwurf durch Verweis auf den Forms-Dienst übergeben. Formularentwürfe können groß sein und daher ist es effizienter, sie anhand von Verweisen zu übergeben, um zu vermeiden, dass Formularentwurfssbyte nach Wert sortiert werden müssen. Der Forms-Dienst kann den Formularentwurf auch zwischenzuspeichern, sodass er den Formularentwurf beim Zwischenspeichern nicht kontinuierlich lesen muss.

Wenn ein Formularentwurf ein UUID-Attribut enthält, wird er zwischengespeichert. Der UUID-Wert ist für alle Formularentwürfe eindeutig und dient zur eindeutigen Identifizierung eines Formulars. Beim Wiedergeben eines Formulars nach Wert sollte das Formular nur zwischengespeichert werden, wenn es wiederholt verwendet wird. Wenn das Formular jedoch nicht wiederholt verwendet wird und eindeutig sein muss, können Sie das Zwischenspeichern des Formulars mithilfe von Zwischenspeicherungsoptionen vermeiden, die mithilfe der AEM Forms-API festgelegt werden.

Der Forms-Dienst kann auch den Speicherort verknüpfter Inhalte im Formularentwurf auflösen. Beispielsweise sind verknüpfte Bilder, auf die im Formularentwurf verwiesen wird, relative URLs. Verknüpfte Inhalte werden immer als relativ zum Speicherort des Formularentwurfs betrachtet. Daher muss der Speicherort des verknüpften Inhalts durch Anwenden des relativen Pfads auf den absoluten Speicherort des Formularentwurfs bestimmt werden.

Anstatt einen Formularentwurf als Referenz zu übergeben, können Sie einen Formularentwurf als Wert übergeben. Die Übergabe eines Formularentwurfs anhand eines Werts ist effizient, wenn ein Formularentwurf dynamisch erstellt wird. das heißt, wenn eine Client-Anwendung die XML generiert, die während der Laufzeit einen Formularentwurf erstellt. In diesem Fall wird ein Formularentwurf nicht in einem physischen Repository gespeichert, da er im Speicher gespeichert ist. Wenn Sie einen Formularentwurf zur Laufzeit dynamisch erstellen und nach Wert übergeben, können Sie das Formular zwischenspeichern und die Leistung des Forms-Dienstes verbessern.

**Einschränkungen für die Übergabe eines Formulars nach Wert**

Die folgenden Einschränkungen gelten, wenn ein Formularentwurf vom Wert übergeben wird:

* Relativer verknüpfter Inhalt kann nicht im Formularentwurf enthalten sein. Alle Bilder und Fragmente müssen in den Formularentwurf eingebettet oder auf den unbedingt verwiesen werden.
* Serverseitige Berechnungen können nach der Wiedergabe des Formulars nicht mehr ausgeführt werden. Wenn das Formular an den Forms-Dienst zurückgesendet wird, werden die Daten extrahiert und ohne serverseitige Berechnungen zurückgegeben.
* Da HTML nur verknüpfte Bilder zur Laufzeit verwenden kann, ist es nicht möglich, HTML mit eingebetteten Bildern zu generieren. Dies liegt daran, dass der Forms-Dienst eingebettete Bilder mit HTML unterstützt, indem er die Bilder von einem referenzierten Formularentwurf abruft. Da ein Formularentwurf, der vom Wert übergeben wird, keinen referenzierten Speicherort hat, können eingebettete Bilder nicht extrahiert werden, wenn die HTML-Seite angezeigt wird. Daher müssen Bildverweise absolute Pfade sein, die in HTML gerendert werden sollen.

>[!NOTE]
>
>Sie können zwar unterschiedliche Formulartypen nach Wert rendern (z. B. HTML-Formulare oder Formulare mit Verwendungsrechten), in diesem Abschnitt wird jedoch die Wiedergabe interaktiver PDF forms beschrieben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular nach Wert wiederzugeben, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Referenzieren Sie den Formularentwurf.
1. Wiedergabe eines Formulars nach Wert.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie Daten programmgesteuert in eine Client-API für PDF-Formulare importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Referenzieren des Formularentwurfs**

Beim Rendern eines Formulars nach Wert müssen Sie ein `com.adobe.idp.Document`-Objekt erstellen, das den wiederzugebenden Formularentwurf enthält. Sie können auf eine vorhandene XDP-Datei verweisen oder einen Formularentwurf zur Laufzeit dynamisch erstellen und `com.adobe.idp.Document` mit diesen Daten ausfüllen.

>[!NOTE]
>
>Dieser Abschnitt und der entsprechende Schnellstart verweisen auf eine vorhandene XDP-Datei.

**Formular nach Wert rendern**

Um ein Formular nach Wert wiederzugeben, übergeben Sie eine `com.adobe.idp.Document`-Instanz, die den Formularentwurf enthält, an den Parameter `inDataDoc` der Rendermethode (kann eine der Rendermethoden des Objekts `FormsServiceClient` sein, z. B. `renderPDFForm`, `(Deprecated) renderHTMLForm` usw.). Dieser Parameterwert ist normalerweise für Daten reserviert, die mit dem Formular zusammengeführt werden. Übergeben Sie auf ähnliche Weise einen leeren Zeichenfolgenwert an den Parameter `formQuery` . Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

>[!NOTE]
>
>Wenn Sie Daten im Formular anzeigen möchten, müssen diese im Element `xfa:datasets` angegeben werden. Informationen zur XFA-Architektur finden Sie unter [https://partners.adobe.com/public/developer/xml/index_arch.html](https://partners.adobe.com/public/developer/xml/index_arch.html).

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular anhand des Werts wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars nach Wert mithilfe der Java-API](#render-a-form-by-value-using-the-java-api)

[Wiedergabe eines Formulars nach Wert mithilfe der Webdienst-API](#render-a-form-by-value-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines Formulars nach Wert mithilfe der Java-API {#render-a-form-by-value-using-the-java-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das den Formularentwurf darstellt, der durch Verwendung des zugehörigen Konstruktors wiedergegeben werden soll, und übergeben Sie einen string -Wert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Formular nach Wert rendern

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `com.adobe.idp.Document` -Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe des `InputStream` -Objekts zu. Rufen Sie die `available` -Methode des Objekts `InputStream` auf, um die Größe des `InputStream` -Objekts zu erhalten.
   * Füllen Sie das Byte-Array mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von Forms nach Wert](/help/forms/developing/rendering-forms.md)

[Schnellstart (SOAP-Modus): Rendern nach Wert mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines Formulars nach Wert mithilfe der Webdienst-API {#render-a-form-by-value-using-the-web-service-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen string -Wert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem Kennwort verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `java.io.FileInputStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Größe des `java.io.FileInputStream`-Objekts mit der `available`-Methode abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `read` -Methode des Objekts `java.io.FileInputStream` aufrufen und das Byte-Array übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `setBinaryData`-Methode aufrufen und das Byte-Array übergeben.

1. Formular nach Wert rendern

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `BLOB` -Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `BLOB` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `BLOB` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von Forms nach Wert](#rendering-forms-by-value)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
