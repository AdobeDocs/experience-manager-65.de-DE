---
title: Erstellen von Web-Programmen, die Formulare wiedergeben
seo-title: Creating Web Applications thatRenders Forms
description: Erstellen Sie ein Web-basiertes Programm, das Java-Servlets verwendet, um den Forms-Service aufzurufen und Formulare wiederzugeben. Das Java-Servlet dient als Bindeglied zwischen dem Forms-Service, der ein Formular zurückgibt, und einem Client-Webbrowser.
seo-description: Create a web-based application that uses Java servlets to invoke the Forms service and render forms. The Java servlet serves as the link between the Forms service that returns a form and a client web browser.
uuid: 00de10c5-79bd-4d8a-ae18-32f1fd2623bf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: f29b089e-8902-4744-81c5-15ee41ba8069
role: Developer
exl-id: 85e00003-8c8b-463a-b728-66af174be295
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '1872'
ht-degree: 99%

---

# Erstellen von Web-Programmen, die Formulare wiedergeben {#creating-web-applications-thatrenders-forms}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Erstellen von Web-Programmen, die Formulare wiedergeben {#creating-web-applications-that-renders-forms}

Sie können ein Web-basiertes Programm erstellen, das Java-Servlets verwendet, um den Forms-Service aufzurufen und Formulare wiederzugeben. Ein Vorteil der Verwendung eines Java™-Servlets besteht darin, dass Sie den Rückgabewert des Prozesses in einen Client-Webbrowser schreiben können. Das heißt, ein Java-Servlet kann als Bindeglied zwischen dem Forms-Service, der ein Formular zurückgibt, und einem Client-Webbrowser verwendet werden.

>[!NOTE]
>
>In diesem Abschnitt wird beschrieben, wie Sie ein Web-basiertes Programm erstellen, das ein Java-Servlet verwendet, das den Forms-Service aufruft und auf Fragmenten basierende Formulare wiedergibt. (Siehe [Wiedergeben von Formularen, die auf Fragmenten basieren](/help/forms/developing/rendering-forms-based-fragments.md).)

Mithilfe eines Java-Servlets können Sie ein Formular in einen Client-Webbrowser schreiben, damit ein Kunde Daten anzeigen und in das Formular eingeben kann. Nach dem Ausfüllen des Formulars mit Daten klickt der Web-Benutzer auf eine Senden-Schaltfläche im Formular, um Informationen zurück an das Java-Servlet zu senden, wo die Daten abgerufen und verarbeitet werden können. Beispielsweise können die Daten an einen anderen Prozess gesendet werden.

In diesem Abschnitt wird beschrieben, wie Sie ein Web-basiertes Programm erstellen können, mit dem der Benutzer entweder amerikanische oder kanadische Formulardaten auswählen kann, wie in der folgenden Abbildung dargestellt.

![cw_cw_fragmentwebclient](assets/cw_cw_fragmentwebclient.png)

Das Formular, das wiedergegeben wird, ist ein Formular, das auf Fragmenten basiert. Das heißt, wenn der Benutzer amerikanische Daten auswählt, verwendet das zurückgegebene Formular Fragmente, die auf amerikanischen Daten basieren. Beispielsweise enthält die Fußzeile des Formulars eine amerikanische Adresse, wie in der folgenden Abbildung dargestellt.

![cw_cw_fragementformfooter](assets/cw_cw_fragementformfooter.png)

Wenn der Benutzer kanadische Daten auswählt, enthält das zurückgegebene Formular eine kanadische Adresse, wie in der folgenden Abbildung dargestellt.

![cw_cw_fragementformfootercnd](assets/cw_cw_fragementformfootercnd.png)

>[!NOTE]
>
>Weitere Informationen zum Erstellen von Formularentwürfen, die auf Fragmenten basieren, finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

**Beispieldateien**

In diesem Abschnitt werden Beispieldateien verwendet, die sich am folgenden Speicherort befinden können:

&lt;*Installationsordner von Forms Designer*>/Samples/Forms/Purchase Order/Form Fragments

wobei &lt;*Installationsordner*> der Installationspfad ist. Für die Zwecke des Client-Programms wurde die Datei „Purchase Order Dynamic.xdp“ von diesem Installationsort kopiert und in einem Forms-Programm namens *Applications/FormsApplication* bereitgestellt. Die Datei „Purchase Order Dynamic“ wird in einem Ordner mit dem Namen „FormsFolder“ abgelegt. Ebenso werden die Fragmente in dem Ordner „Fragments“ platziert, wie in der folgenden Abbildung dargestellt.

![cw_cw_fragmentsrepository](assets/cw_cw_fragmentsrepository.png)

Um auf den Formularentwurf „Purchase Order Dynamic.xdp“ zuzugreifen, geben Sie `Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp` als Formularnamen (den ersten Parameter, der an die Methode `renderPDFForm` übergeben wird) und `repository:///` als Wert für den Stamm-URI des Inhalts an.

Die vom Web-Programm verwendeten XML-Datendateien wurden vom Ordner „Data“ nach `C:\Adobe` verschoben (das Dateisystem, das zum J2EE-Programm-Server gehört, der AEM Forms hostet). Die Dateinamen sind „Bestellung *Canada.xml*“ und „Bestellung *US.xml*“.

>[!NOTE]
>
>Weitere Informationen zum Erstellen eines Forms-Programms mit Workbench finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein Web-basiertes Programm zu erstellen, das Formulare wiedergibt, die auf Fragmenten basieren:

1. Erstellen Sie ein neues Web-Projekt.
1. Erstellen Sie die Java-Anwendungslogik, die das Java-Servlet darstellt.
1. Erstellen Sie die Web-Seite für das Web-Programm.
1. Verpacken Sie das Web-Programm in eine WAR-Datei.
1. Stellen Sie die WAR-Datei auf dem J2EE-Programm-Server bereit.
1. Testen Sie Ihr Web-Programm.

>[!NOTE]
>
>Einige dieser Schritte hängen von dem J2EE-Programm ab, auf dem AEM Forms bereitgestellt wird. Die Methode zum Bereitstellen einer WAR-Datei hängt beispielsweise von dem verwendeten J2EE-Programm-Server ab. In diesem Abschnitt wird davon ausgegangen, dass AEM Forms auf JBoss® bereitgestellt wird.

### Erstellen eines Web-Projekts {#creating-a-web-project}

Der erste Schritt zum Erstellen eines Web-Programms mit einem Java-Servlet, das den Forms-Service aufrufen kann, besteht darin, ein neues Web-Projekt zu erstellen. Die Java-IDE, auf der dieses Dokument basiert, ist Eclipse 3.3. Erstellen Sie mithilfe der Eclipse-IDE ein Web-Projekt und fügen Sie die erforderlichen JAR-Dateien zu Ihrem Projekt hinzu. Fügen Sie schließlich eine HTML-Seite mit dem Namen *index.html* und ein Java-Servlet zu Ihrem Projekt hinzu.

In der folgenden Liste sind die JAR-Dateien aufgeführt, die Sie zu Ihrem Web-Projekt hinzufügen müssen:

* adobe-forms-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**So erstellen Sie ein Web-Projekt:**

1. Starten Sie Eclipse und klicken Sie auf **Datei** > **Neues Projekt**.
1. Wählen Sie im Dialogfeld **Neues Projekt** die Optionen **Web** > **Dynamisches Webprojekt**.
1. Geben Sie `FragmentsWebApplication` für den Namen Ihres Projekts ein, und klicken Sie dann auf **Beenden**.

**So fügen Sie erforderliche JAR-Dateien zu Ihrem Projekt hinzu:**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `FragmentsWebApplication` und wählen Sie **Eigenschaften**.
1. Klicken Sie auf **Java-Build-Pfad** und anschließend auf die Registerkarte **Bibliotheken**.
1. Klicken Sie auf die Schaltfläche **Externe JARs hinzufügen** und navigieren Sie zu den einzuschließenden JAR-Dateien.

**So fügen Sie ein Java-Servlet zu Ihrem Projekt hinzu:**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `FragmentsWebApplication` und wählen Sie **Neu** > **Sonstige**.
1. Erweitern Sie den Ordner **Web**, wählen Sie **Servlet** aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie im Dialogfeld „Servlet erstellen“ `RenderFormFragment` für den Namen des Servlets ein und klicken Sie dann auf **Beenden**.

**So fügen Sie eine HTML-Seite zu Ihrem Projekt hinzu:**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `FragmentsWebApplication` und wählen Sie **Neu** > **Sonstige**.
1. Erweitern Sie den Ordner **Web**, wählen Sie **HTML** und klicken Sie auf **Weiter**.
1. Geben Sie im Dialogfeld „Neue HTML“ `index.html` für den Dateinamen ein und klicken Sie auf **Beenden**.

>[!NOTE]
>
>Weitere Informationen zum Erstellen der HTML-Seite, die das Java-Servlet `RenderFormFragment` aufruft, finden Sie unter [Erstellen der Web-Seite](/help/forms/developing/rendering-forms.md#creating-the-web-page).

### Erstellen der Java-Anwendungslogik für das Servlet {#creating-java-application-logic-for-the-servlet}

Sie erstellen eine Java-Anwendungslogik, die den Forms-Service vom Java-Servlet aus aufruft. Der folgende Code zeigt die Syntax des Java-Servlets `RenderFormFragment`:

```java
     public class RenderFormFragment extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
         doPost(req,resp);
 
         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
             //Add code here to invoke the Forms service
             }
```

Normalerweise würden Sie keinen Client-Code innerhalb der Methode `doGet` oder `doPost` eines Java-Servlets platzieren. Eine bessere Programmierpraxis ist es, diesen Code in einer separaten Klasse zu platzieren, die Klasse innerhalb der Methode `doPost` (oder `doGet`) zu instanziieren und die entsprechenden Methoden aufzurufen. Aus Gründen der Kürze des Codes werden die Code-Beispiele in diesem Abschnitt jedoch auf ein Minimum beschränkt und die Code-Beispiele in der Methode `doPost` platziert.

Führen Sie die folgenden Aufgaben aus, um ein auf Fragmenten basierendes Formular mithilfe der Forms-Service-API wiederzugeben:

1. Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Rufen Sie den Wert der Optionsschaltfläche ab, der vom HTML-Formular gesendet wird, und geben Sie an, ob amerikanische oder kanadische Daten verwendet werden sollen. Wenn es um amerikanische Daten geht, erstellen Sie ein `com.adobe.idp.Document`, das die Daten in der Datei *Purchase Order US.xml* speichert. Wenn es sich um kanadische Daten handelt, erstellen Sie entsprechend ein `com.adobe.idp.Document`, das Daten in der Datei *Purchase Order Canada.xml* speichert.
1. Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
1. Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
1. Rufen Sie die Methode `setApplicationWebRoot` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Web-Stamm des Programms darstellt.
1. Rufen Sie die `setContentRootURI`-Methode des `URLSpec`-Objekts auf und übergeben Sie ihr einen Zeichenfolgenwert, der den Inhaltsstamm-URI angibt. Stellen Sie sicher, dass sich der Formularentwurf und die Fragmente im URI des Inhaltsstamms befinden. Andernfalls löst der Forms-Service eine Ausnahme aus. Um auf das AEM Forms-Repository zu verweisen, geben Sie `repository://` an.
1. Rufen Sie die Methode `setTargetURL` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Wert der Ziel-URL angibt, an die die Formulardaten gesendet werden. Wenn Sie die Ziel-URL im Formularentwurf definieren, können Sie auch eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular zur Durchführung von Berechnungen gesendet wird.
1. Rufen Sie die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf und übergeben Sie ihr folgende Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs angibt, einschließlich der Dateinamenerweiterung.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen (erstellt in Schritt 2).
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Weitere Informationen finden Sie unter [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die der Forms-Service benötigt, um ein Formular basierend auf Fragmenten rendern zu können.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Erstellen Sie ein `com.adobe.idp.Document`-Objekt durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts.
1. Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
1. Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
1. Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
1. Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `getInputStream`-Methode des `com.adobe.idp.Document`-Objekts aufrufen.
1. Erstellen Sie ein Byte-Array, das mit dem Formulardatenstrom gefüllt wird, indem Sie die `read`-Methode des `InputStream`-Objekts aufrufen und ihr das Byte-Array als Argument übergeben.
1. Rufen Sie die `write`-Methode des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array der `write`-Methode.

Das folgende Code-Beispiel stellt das Java-Servlet dar, das den Forms-Service aufruft und ein Formular basierend auf Fragmenten rendert.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-forms-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     *
     * (Because Forms quick starts are implemented as Java servlets, it is
     * not necessary to include J2EE specific JAR files - the Java project
     * that contains this quick start is exported as a WAR file which
     * is deployed to the J2EE application server)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs
     *
     * For complete details about the location of these JAR files,
     * see "Including AEM Forms library files" in Programming with AEM forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.io.IOException;
 import java.io.PrintWriter;
 
 import javax.servlet.Servlet;
 import javax.servlet.ServletException;
 import javax.servlet.ServletOutputStream;
 import javax.servlet.http.HttpServlet;
 import javax.servlet.http.HttpServletRequest;
 import javax.servlet.http.HttpServletResponse;
 import com.adobe.livecycle.formsservice.client.*;
 import java.util.*;
 import java.io.InputStream;
 import java.net.URL;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class RenderFormFragment extends HttpServlet implements Servlet {
 
     public void doGet(HttpServletRequest req, HttpServletResponse resp)
         throws ServletException, IOException {
             doPost(req,resp);
 
     }
     public void doPost(HttpServletRequest req, HttpServletResponse resp)
     throws ServletException, IOException {
 
 
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Get the value of selected radio button
             String radioValue = req.getParameter("radio");
 
             //Create an Document object to store form data
             Document oInputData = null;
 
             //The value of the radio button determines the form data to use
             //which determines which fragments used in the form
             if (radioValue.compareTo("AMERICAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml");
                 oInputData = new Document(myData);
             }
             else if (radioValue.compareTo("CANADIAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml");
                 oInputData = new Document(myData);
             }
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a FormsServiceClient object
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);
 
             //Set the parameter values for the renderPDFForm method
             String formName = "Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp";
 
             //Cache the PDF form
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec();
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true));
 
             //Specify URI values that are required to render a form
             //design based on fragments
             URLSpec uriValues = new URLSpec();
             uriValues.setApplicationWebRoot("https://'[server]:[port]'/RenderFormFragment");
             uriValues.setContentRootURI("repository:///");
             uriValues.setTargetURL("https://'[server]:[port]'/FormsServiceClientApp/HandleData");
 
             //Invoke the renderPDFForm method and write the
             //results to a client web browser
             FormsResult formOut = formsClient.renderPDFForm(
                         formName,               //formQuery
                         oInputData,             //inDataDoc
                         pdfFormRenderSpec,      //PDFFormRenderSpec
                         uriValues,                //urlSpec
                         null                    //attachments
                         );
 
             //Create a Document object that stores form data
             Document myData = formOut.getOutputContent();
 
             //Get the content type of the response and
             //set the HttpServletResponse object’s content type
             String contentType = myData.getContentType();
             resp.setContentType(contentType);
 
             //Create a ServletOutputStream object
             ServletOutputStream oOutput = resp.getOutputStream();
 
             //Create an InputStream object
             InputStream inputStream = myData.getInputStream();
 
             //Write the data stream to the web browser
             byte[] data = new byte[4096];
             int bytesRead = 0;
             while ((bytesRead = inputStream.read(data)) > 0)
             {
                 oOutput.write(data, 0, bytesRead);
             }
 
         }catch (Exception e) {
              System.out.println("The following exception occurred: "+e.getMessage());
       }
     }
 }
```

### Erstellen der Webseite {#creating-the-web-page}

Die Webseite „index.html“ bietet einen Einstiegspunkt für das Java-Servlet und ruft den Forms-Service auf. Bei dieser Webseite handelt es sich um ein einfaches HTML-Formular mit zwei Optionsfeldern und einer Schaltfläche „submit“. Der Name der Optionsfelder lautet „radio“. Wenn der Benutzer auf die Schaltfläche „Senden“ klickt, werden die Formulardaten an das Java-Servlet `RenderFormFragment` gesendet.

Das Java-Servlet erfasst die von der HTML-Seite veröffentlichten Daten mithilfe des folgenden Java-Codes:

```java
             Document oInputData = null;
 
             //Get the value of selected radio button
             String radioValue = req.getParameter("radio");
 
             //The value of the radio button determines the form data to use
             //which determines which fragments used in the form
             if (radioValue.compareTo("AMERICAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml");
                 oInputData = new Document(myData);
             }
             else if (radioValue.compareTo("CANADIAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml");
                 oInputData = new Document(myData);
             }
```

Der folgende HTML-Code befindet sich in der Datei „index.html“, die beim Einrichten der Entwicklungsumgebung erstellt wurde. (Weitere Informationen finden Sie unter [Erstellen eines Webprojekts](/help/forms/developing/rendering-forms.md#creating-a-web-project).)

```xml
 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
 <html xmlns="https://www.w3.org/1999/xhtml">
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
 <title>Untitled Document</title>
 </head>
 
 <body>
 <form name="myform" action="https://'[server]:[port]'/FragmentsWebApplication/RenderFormFragment" method="post">
      <table>
      <tr>
        <th>Forms Fragment Web Client</th>
      </tr>
      <tr>
        <td>
          <label>
          <input type="radio" name="radio" id="radio_Data" value="CANADIAN" />
          Canadian data<br />
          </label>
          <p>
            <label>
            <input type="radio" name="radio" id="radio_Data" value="AMERICAN" checked/>
            American data</label>
          </p>
        </td>
      </tr>
      <tr>
      <td>
        <label>
          <input type="submit" name="button_Submit" id="button_Submit" value="Submit" />
            </label>
            </td>
         </tr>
        </table>
      </form>
 </body>
 </html>
```

### Verpacken der Webanwendung {#packaging-the-web-application}

Um das Java-Servlet bereitzustellen, das den Forms-Service aufruft, packen Sie Ihre Webanwendung in eine WAR-Datei. Stellen Sie sicher, dass externe JAR-Dateien, von denen die Geschäftslogik der Komponente abhängig ist, wie „adobe-livecycle-client.jar“ und „adobe-forms-client.jar“, ebenfalls in der WAR-Datei enthalten sind.

**So packen Sie eine Webanwendung in eine WAR-Datei:**

1. Klicken Sie im Fenster **Projekt-Explorer** mit der rechten Maustaste auf das Projekt `FragmentsWebApplication` und wählen Sie **Export** > **WAR-Datei**.
1. Geben Sie in das Textfeld **Webmodul** als Namen des Java-Projekts `FragmentsWebApplication` ein.
1. Geben Sie in das Textfeld **Ziel** die Zeichenfolge **`FragmentsWebApplication.war`** als Dateinamen ein, geben Sie den Speicherort für Ihre WAR-Datei an und klicken Sie auf „Fertig stellen“.

### Bereitstellen der WAR-Datei auf dem J2EE-Anwendungsserver {#deploying-the-war-file-to-the-j2ee-application-server}

Sie können die WAR-Datei auf dem J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt worden ist, bereitstellen. Nachdem die WAR-Datei bereitgestellt wurde, können Sie über einen Webbrowser auf die HTML-Webseite zugreifen.

**So stellen Sie die WAR-Datei auf dem J2EE-Anwendungsserver bereit:**

* Kopieren Sie die WAR-Datei aus dem Exportpfad nach `[Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\all\deploy`.

### Testen der Webanwendung {#testing-your-web-application}

Nach der Bereitstellung der Webanwendung können Sie sie mithilfe eines Webbrowsers testen. Wenn Sie denselben Computer verwenden, auf dem AEM Forms gehostet wird, können Sie folgende URL angeben:

* http://localhost:8080/FragmentsWebApplication/index.html

  Wählen Sie ein Optionsfeld aus und klicken Sie auf die Schaltfläche „Submit“. Ein Formular, das auf Fragmenten basiert, wird im Webbrowser angezeigt. Wenn Probleme auftreten, lesen Sie die Protokolldatei des J2EE-Anwendungsservers.
