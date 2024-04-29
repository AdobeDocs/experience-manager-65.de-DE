---
title: Rendern interaktiver PDF-Formulare
description: Verwenden Sie den Forms-Service, um interaktive PDF-Formulare an Client-Geräte, in der Regel Webbrowser, zu senden, um Informationen von Benutzern zu sammeln. Sie können den Forms-Service verwenden, um interaktive Formulare mithilfe der Java-API und der Webservice-API zu rendern.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d9f32939-c2c0-4531-b15e-f63941c289e3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2455'
ht-degree: 100%

---

# Rendern interaktiver PDF-Formulare {#rendering-interactive-pdf-forms}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Der Forms-Service rendert interaktive PDF-Formulare an Client-Geräte, normalerweise Webbrowser, um Benutzerinformationen zu erfassen. Nachdem ein interaktives Formular gerendert wurde, kann ein Benutzer Daten in Formularfelder eingeben und auf dem Formular auf eine Senden-Schaltfläche klicken, um Informationen an den Forms-Service zurückzusenden. Damit ein interaktives PDF-Formular angezeigt werden kann, muss Adobe Reader oder Acrobat auf dem Computer installiert sein, auf dem der Client-Webbrowser läuft.

>[!NOTE]
>
>Bevor Sie ein Formular mit dem Forms-Service wiedergeben können, erstellen Sie einen Formularentwurf. In der Regel wird ein Formularentwurf in Designer erstellt und als XDP-Datei gespeichert. Informationen zum Erstellen eines Formularentwurfs finden Sie unter [Forms-Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

**Beispielformular für einen Darlehensantrag**

Anhand eines Beispiels für einen Darlehensantrag wird gezeigt, wie der Forms-Service interaktive Formulare verwendet, um Informationen von Benutzern zu erfassen. Mit diesem Antrag kann ein Benutzer ein Formular mit Daten ausfüllen, die für die Aufnahme eines Darlehens erforderlich sind, und die Daten dann an den Forms-Service übermitteln. Die folgende Abbildung zeigt den logischen Ablauf des Darlehensantrags.

![ri_ri_finsrv_loanapp_v1](assets/ri_ri_finsrv_loanapp_v1.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Das Java-Servlet <code>GetLoanForm</code> wird von einer HTML-Seite aufgerufen. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Das Java-Servlet <code>GetLoanForm</code> verwendet die Client-API des Forms-Services, um das Darlehensformular im Client-Webbrowser zu rendern. (Siehe <a href="#render-an-interactive-pdf-form-using-the-java-api">Rendern eines interaktiven PDF-Formulars mithilfe der Java-API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Nachdem der Benutzer das Darlehensformular ausgefüllt und auf die Senden-Schaltfläche geklickt hat, werden die Daten an das Java-Servlet <code>HandleData</code> übermittelt. (Siehe <i>„Darlehensformular“</i>.)</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Das Java-Servlet <code>HandleData</code> verwendet die Client-API des Forms-Services, um die Formularübermittlung zu verarbeiten und Formulardaten abzurufen. Die Daten werden dann in einer Unternehmensdatenbank gespeichert. (Siehe <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Umgang mit übermittelten Formularen</a>.)</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Ein Bestätigungsformular wird an den Webbrowser zurückgegeben. Daten wie der Vor- und Nachname der Person werden mit dem Formular zusammengeführt, bevor es gerendert wird. (Siehe <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">Vorausfüllen von Formularen mit flexiblen Layouts</a>.)</p></td>
  </tr>
 </tbody>
</table>

**Darlehensformular**

Dieses interaktive Darlehensformular wird vom Java-Servlet `GetLoanForm` des Beispiel-Darlehensantrags gerendert.

![ri_ri_loanform](assets/ri_ri_loanform.png)

**Bestätigungsformular**

Dieses Formular wird vom Java-Servlet `HandleData` des Beispiel-Darlehensantrags gerendert.

![ri_ri_confirm](assets/ri_ri_confirm.png)

Das Java-Servlet `HandleData` füllt dieses Formular vorab mit dem Vor- und Nachnamen der Person sowie dem Betrag aus. Nachdem das Formular vorausgefüllt wurde, wird es an den Client-Webbrowser gesendet. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Java-Servlets**

Der Beispiel-Darlehensantrag ist ein Beispiel für ein Forms Service-Programm, das als Java-Servlet vorhanden ist. Ein Java-Servlet ist ein Java-Programm, das auf einem J2EE-Programm-Server wie WebSphere ausgeführt wird und den Client-API-Code des Forms-Services enthält.

Der folgende Code zeigt die Syntax eines Java-Servlets mit dem Namen GetLoanForm:

```java
     public class GetLoanForm extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {

         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {

             }
```

Normalerweise würden Sie den Client-API-Code des Forms-Services nicht innerhalb der Methode `doGet` oder `doPost` eines Java-Servlets platzieren. Es ist eine bessere Programmierpraxis, diesen Code in einer separaten Klasse zu platzieren, die Klasse innerhalb der Methode `doPost` (oder `doGet`) zu instanziieren und die entsprechenden Methoden aufzurufen. Aus Gründen der Kürze des Codes werden die Code-Beispiele in diesem Abschnitt jedoch auf ein Minimum beschränkt und die Code-Beispiele in der Methode `doPost` untergebracht.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

**Zusammenfassung der Schritte**

Um ein interaktives PDF-Formular zu rendern, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Geben Sie URI-Werte an.
1. Hängen Sie Dateien an das Formular an (optional).
1. Rendern Sie ein interaktives PDF-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie ein Forms-Client-API-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webservice-API verwenden, erstellen Sie ein `FormsService`-Objekt.

**Angeben von URI-Werten**

Sie können URI-Werte angeben, die der Forms-Service zum Rendern eines Formulars benötigt. Ein Formularentwurf, der als Teil eines Forms-Programm gespeichert wird, kann mithilfe des Inhaltsstamm-URI-Werts `repository:///` referenziert werden. Betrachten Sie beispielsweise den folgenden Formularentwurf mit dem Namen *Loan.xdp* innerhalb eines Forms-Programms mit dem Namen *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Um auf diesen Formularentwurf zuzugreifen, geben Sie `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` als Formularnamen (den ersten Parameter, der an die Methode `renderPDFForm` übergeben wird) und `repository:///` als Inhaltsstamm-URI-Wert an.

>[!NOTE]
>
>Informationen zum Erstellen eines Forms-Programms mit Workbench finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

Der Pfad zu einer Ressource in einer Forms-Anwendung lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Die folgenden Werte zeigen einige Beispiele für URI-Werte:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

Beim Rendern eines interaktiven Formulars können Sie URI-Werte definieren, z. B. die Ziel-URL, an die die Formulardaten gesendet werden. Die Ziel-URL kann auf eine der folgenden Arten definiert werden:

* Auf der Senden-Schaltfläche beim Entwerfen des Formularentwurfs in Designer
* Durch Verwendung der Client-API des Forms-Services

Wenn die Ziel-URL im Formularentwurf definiert ist, darf sie nicht mit der Client-API des Forms-Services überschrieben werden. Das heißt, durch Festlegen der Ziel-URL mithilfe der Forms-API wird die angegebene URL im Formularentwurf auf die URL zurückgesetzt, die mithilfe der API angegeben wurde. Wenn Sie das PDF-Formular an die im Formularentwurf angegebene Ziel-URL senden möchten, legen Sie die Ziel-URL programmgesteuert auf eine leere Zeichenfolge fest.

Wenn Sie ein Formular mit einer Senden-Schaltfläche und einer Berechnen-Schaltfläche (mit einem entsprechenden Skript, das auf dem Server ausgeführt wird) haben, können Sie programmgesteuert die URL definieren, an die das Formular gesendet wird, um das Skript auszuführen. Verwenden Sie die Senden-Schaltfläche im Formularentwurf, um die URL anzugeben, an die die Formulardaten gesendet werden. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md).)

>[!NOTE]
>
>Anstatt einen URL-Wert anzugeben, um auf eine XDP-Datei zu verweisen, können Sie auch eine `com.adobe.idp.Document`-Instanz an den Forms-Service übergeben. Die `com.adobe.idp.Document`-Instanz enthält einen Formularentwurf. (Siehe [Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md).)

**Anhängen von Dateien an das Formular**

Sie können Dateien an ein Formular anhängen. Wenn Sie ein PDF-Formular mit Dateianlagen rendern, können Benutzer die Dateianlagen in Acrobat mithilfe des Bereichs „Dateianlagen“ abrufen. Sie können verschiedene Dateitypen an ein Formular anhängen, z. B. eine Textdatei oder eine Binärdatei wie eine JPG-Datei.

>[!NOTE]
>
>Das Anhängen von Dateianlagen an ein Formular ist optional.

**Rendern eines interaktiven PDF-Formulars**

Um ein Formular wiederzugeben, verwenden Sie einen Formularentwurf, der in Designer erstellt und als XDP- oder PDF-Datei gespeichert wurde. Sie können auch ein Formular wiedergeben, das mit Acrobat erstellt und als PDF-Datei gespeichert wurde. Um ein interaktives PDF-Formular zu rendern, rufen Sie die Methode `renderPDFForm2` oder die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf.

Die Methode `renderPDFForm` verwendet ein `URLSpec`-Objekt. Der Inhaltsstamm der XDP-Datei wird mit der Methode `setContentRootURI` des `URLSpec`-Objekts an den Forms-Dienst übergeben. Der Name des Formularentwurfs (`formQuery`) wird als separater Parameterwert übergeben. Die beiden Werte werden zusammengefügt, um den absoluten Verweis auf den Formularentwurf zu erhalten.

Die Methode `renderPDFForm2` akzeptiert eine `com.adobe.idp.Document`-Instanz, die das zu rendernde XDP- oder PDF-Dokument enthält.

>[!NOTE]
>
>Die Laufzeitoption für mit Tags versehene PDF kann nicht festgelegt werden, wenn das Eingabedokument ein PDF-Dokument ist. Wenn es sich bei der Eingabedatei um eine XDP-Datei handelt, kann die mit Tags versehene PDF-Option festgelegt werden.

## Rendern eines interaktiven PDF-Formulars mithilfe der Java-API {#render-an-interactive-pdf-form-using-the-java-api}

So rendern Sie ein interaktives PDF-Formular mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. 

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Angeben der URI-Werte

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte speichert, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `setApplicationWebRoot` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Web-Stamm der Anwendung darstellt.
   * Rufen Sie die Methode `setContentRootURI` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert des Inhaltsstamms angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls löst der Forms-Service eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository:///` an.
   * Rufen Sie die Methode `setTargetURL` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Falls Sie die Ziel-URL im Formularentwurf definieren, können Sie auch eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Anhängen von Dateien an das Formular

   * Erstellen Sie ein `java.util.HashMap`-Objekt, um Dateianhänge zu speichern, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `put` des `java.util.HashMap`-Objekts für jede Datei auf, die an das gerenderte Formular angehängt werden soll. Übergeben Sie die folgenden Werte an diese Methode:

      * Ein Zeichenfolgenwert, der den Namen des Dateianhangs angibt, einschließlich der Dateinamenerweiterung.

   * Ein `com.adobe.idp.Document`-Objekt, das die Dateianlage enthält.

   >[!NOTE]
   >
   >Wiederholen Sie diesen Schritt für jede Datei, die an das Formular angehängt werden soll. Dieser Schritt ist optional, und Sie können `null` übergeben, wenn Sie keine Dateianhänge senden möchten.

1. Wiedergeben eines interaktiven PDF-Formulars

   Rufen Sie die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `renderPDFForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein Objekt vom Typ `javax.servlet.ServletOutputStream`, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Objekt vom Typ `java.io.InputStream`, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstrom, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

## Rendern eines interaktiven PDF-Formulars mithilfe der Webservice-API {#render-an-interactive-pdf-form-using-the-web-service-api}

So rendern Sie ein interaktives PDF-Formular mithilfe der Forms-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Angeben der URI-Werte

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte speichert, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `setApplicationWebRoot` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Web-Stamm der Anwendung darstellt.
   * Rufen Sie die Methode `setContentRootURI` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert des Inhaltsstamms angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls löst der Forms-Service eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository:///` an.
   * Rufen Sie die Methode `setTargetURL` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Falls Sie die Ziel-URL im Formularentwurf definieren, können Sie auch eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Anhängen von Dateien an das Formular

   * Erstellen Sie ein `java.util.HashMap`-Objekt, um Dateianhänge zu speichern, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `put` des `java.util.HashMap`-Objekts für jede Datei auf, die an das gerenderte Formular angehängt werden soll. Übergeben Sie die folgenden Werte an diese Methode:

      * Ein Zeichenfolgenwert, der den Namen des Dateianhangs angibt, einschließlich der Dateinamenerweiterung

   * Ein `BLOB`-Objekt, das den Dateianhang enthält

   >[!NOTE]
   >
   >Wiederholen Sie diesen Schritt für jede Datei, die an das Formular angehängt werden soll.

1. Wiedergeben eines interaktiven PDF-Formulars

   Rufen Sie die Methode `renderPDFForm` des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` festlegen, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthalten wird.

   Die Methode `renderPDFForm` füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardaten-Stream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein Objekt vom Typ `FormResult`, indem Sie den Wert des Datenelements `value` des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `BLOB`, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein Objekt vom Typ `javax.servlet.ServletOutputStream`, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Schreiben des Formulardaten-Streams in den Client-Webbrowser**

Wenn der Forms-Service ein Formular rendert, wird ein Formulardatenstrom zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Sobald das Formular in den Client-Webbrowser geschrieben wurde, ist es für den Benutzer sichtbar.
