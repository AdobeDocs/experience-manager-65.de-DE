---
title: Rendern von Formularen basierend auf Werten
description: Verwenden Sie die Forms-API (Java), um ein Formular mithilfe der Java-API und der Web Service-API anhand eines Werts zu rendern.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a3a6a06d-ec90-4147-a5f0-e776a086ee12
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1822'
ht-degree: 100%

---

# Rendern von Formularen basierend auf Werten {#rendering-forms-by-value}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

In der Regel wird ein in Designer erstellter Formularentwurf durch Verweis auf den Forms-Service übergeben. Formularentwürfe können sehr groß sein, weshalb es effizienter ist, sie per Verweis zu übergeben, um zu vermeiden, dass die Bytes des Formularentwurfs nach Werten geordnet werden müssen. Der Forms-Service kann den Formularentwurf auch zwischenspeichern, so dass er ihn, wenn er einmal zwischengespeichert ist, nicht kontinuierlich lesen muss.

Wenn ein Formularentwurf ein UUID-Attribut enthält, wird er zwischengespeichert. Der UUID-Wert ist für alle Formularentwürfe eindeutig und dient zur eindeutigen Identifizierung eines Formulars. Beim Rendern eines Formulars anhand eines Werts sollte das Formular nur zwischengespeichert werden, wenn es wiederholt verwendet wird. Wenn das Formular jedoch nicht wiederholt verwendet wird und eindeutig sein muss, können Sie das Zwischenspeichern des Formulars mithilfe von Zwischenspeicherungsoptionen vermeiden, die mithilfe der AEM Forms-API festgelegt werden können.

Der Forms-Service kann auch den Speicherort verknüpfter Inhalte im Formularentwurf auflösen. Beispielsweise stellen verknüpfte Bilder, auf die im Formularentwurf verwiesen wird, relative URLs dar. Verknüpfte Inhalte werden immer als relativ zum Speicherort des Formularentwurfs betrachtet. Daher muss der Speicherort eines verknüpften Inhalts durch Anwenden des relativen Pfads auf den absoluten Speicherort des Formularentwurfs bestimmt werden.

Anstatt einen Formularentwurf per Verweis zu übergeben, können Sie einen Formularentwurf anhand eines Werts übergeben. Das Übergeben eines Formularentwurfs anhand eines Werts ist effizient, wenn ein Formularentwurf dynamisch erstellt wird. das heißt, wenn ein Client-Programm die XML generiert, die während der Laufzeit einen Formularentwurf erstellt. In diesem Fall wird ein Formularentwurf nicht in einem physischen Repository gespeichert, da er im Speicher gespeichert ist. Wenn Sie einen Formularentwurf zur Laufzeit dynamisch erstellen und anhand eines Werts übergeben, können Sie das Formular zwischenspeichern und die Leistung des Forms-Services verbessern.

**Einschränkungen für die Übergabe eines Formulars anhand eines Werts**

Die folgenden Einschränkungen gelten, wenn ein Formularentwurf anhand eines Werts übergeben wird:

* Es können keine relativen verknüpften Inhalte im Formularentwurf enthalten sein. Alle Bilder und Fragmente müssen in den Formularentwurf eingebettet oder mit absoluten Verweisen versehen werden.
* Nach dem Rendern des Formulars können keine Server-seitigen Berechnungen mehr durchgeführt werden. Wenn das Formular an den Forms-Service zurückgesendet wird, werden die Daten extrahiert und ohne Server-seitige Berechnungen zurückgegeben.
* Da HTML zur Laufzeit nur verknüpfte Bilder verwenden kann, ist es nicht möglich, HTML mit eingebetteten Bildern zu generieren. Dies liegt daran, dass der Forms-Service eingebettete Bilder mit HTML unterstützt, indem er die Bilder von einem referenzierten Formularentwurf abruft. Da ein Formularentwurf, der anhand eines Werts übergeben wird, keinen referenzierten Speicherort hat, können eingebettete Bilder nicht extrahiert werden, wenn die HTML-Seite angezeigt wird. Daher müssen Bildverweise absolute Pfade sein, die in HTML gerendert werden sollen.

>[!NOTE]
>
>Sie können zwar unterschiedliche Formulartypen anhand eines Werts rendern (z. B. HTML-Formulare oder Formulare mit Verwendungsrechten), in diesem Abschnitt wird jedoch speziell das Rendern interaktiver PDF-Formulare beschrieben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular anhand eines Werts wiederzugeben, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Verweisen Sie auf den Formularentwurf.
1. Rendern Sie ein Formular anhand eines Werts.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Objekts für die Forms Client API**

Bevor Sie Daten programmgesteuert in eine PDF-Formular-Client-API importieren können, müssen Sie einen Client für den Data Integration-Service erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Services erforderlich sind.

**Verweisen auf den Formularentwurf**

Wenn Sie ein Formular anhand eines Werts rendern, müssen Sie ein `com.adobe.idp.Document`-Objekt erstellen, das den zu rendernden Formularentwurf enthält. Sie können auf eine vorhandene XDP-Datei verweisen oder einen Formularentwurf zur Laufzeit dynamisch erstellen und ein `com.adobe.idp.Document` mit diesen Daten auffüllen.

>[!NOTE]
>
>Dieser Abschnitt und die entsprechende Kurzanleitung verweisen auf eine vorhandene XDP-Datei.

**Rendern eines Formulars anhand eines Werts**

Um ein Formular anhand von Werten zu rendern, übergeben Sie eine `com.adobe.idp.Document`-Instanz, die den Formularentwurf enthält, an den Parameter `inDataDoc` der Render-Methode (dies kann eine beliebige Render-Methode des `FormsServiceClient`-Objekts sein, z. B. `renderPDFForm`, `(Deprecated) renderHTMLForm` usw.). Dieser Parameterwert ist normalerweise für Daten reserviert, die mit dem Formular zusammengeführt werden. Übergeben Sie einen leeren Zeichenfolgenwert an den Parameter `formQuery`. Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

>[!NOTE]
>
>Wenn Sie Daten innerhalb des Formulars anzeigen möchten, müssen die Daten innerhalb des Elements `xfa:datasets` angegeben werden. Informationen zur XFA-Architektur finden Sie unter [https://www.pdfa.org/norm-refs/XFA-3_3.pdf](https://www.pdfa.org/norm-refs/XFA-3_3.pdf).

**Senden des Formular-Datenstreams an den Client-Webbrowser**

Wenn der Forms-Service ein Formular anhand des Werts rendert, wird ein Formulardaten-Stream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Sobald das Formular in den Client-Webbrowser geschrieben wurde, ist es für den Benutzer sichtbar.

**Siehe auch**

[Rendern eines Formulars anhand eines Werts mithilfe der Java-API](#render-a-form-by-value-using-the-java-api)

[Rendern eines Formulars anhand eines Werts mithilfe der Webservice-API](#render-a-form-by-value-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendern eines Formulars anhand eines Werts mithilfe der Java-API {#render-a-form-by-value-using-the-java-api}

So rendern Sie ein Formular anhand eines Werts mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. 

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das den zu rendernden Formularentwurf darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Rendern eines Formulars anhand eines Werts

   Rufen Sie die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `renderPDFForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein Objekt vom Typ `javax.servlet.ServletOutputStream`, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Objekt vom Typ `java.io.InputStream`, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe des `InputStream`-Objekts zu. Rufen Sie die Methode `available` des `InputStream`-Objekts auf, um die Größe des `InputStream`-Objekts zu erhalten.
   * Füllen Sie das Byte-Array mit dem Formulardatenstrom, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen basierend auf Werten](/help/forms/developing/rendering-forms.md)

[Kurzanleitung (SOAP-Modus): Rendern nach Wert mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendern eines Formulars anhand eines Werts mithilfe der Webservice-API {#render-a-form-by-value-using-the-web-service-api}

So rendern Sie ein Formular anhand des Werts mithilfe der Forms-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Ein Zeichenfolgenwert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu speichern.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `java.io.FileInputStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Größe des `java.io.FileInputStream`-Objekts mithilfe seiner Methode `available` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `read` des `java.io.FileInputStream`-Objekts aufrufen und das Byte-Array übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine Methode `setBinaryData` aufrufen und das Byte-Array übergeben.

1. Rendern eines Formulars anhand eines Werts

   Rufen Sie die Methode `renderPDFForm` des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * Ein `BLOB`-Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` festlegen, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die Methode `renderPDFForm` füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardaten-Stream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein Objekt vom Typ `FormResult`, indem Sie den Wert des Datenelements `value` des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `BLOB`, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein Objekt vom Typ `javax.servlet.ServletOutputStream`, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen basierend auf Werten](#rendering-forms-by-value)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
