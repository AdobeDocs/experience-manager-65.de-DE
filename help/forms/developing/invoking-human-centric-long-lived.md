---
title: An Menschen orientierte langlebige Prozesse aufrufen
seo-title: Invoking Human-Centric Long-Lived Processes
description: Rufen Sie in Workbench erstellte, am Menschen orientierte langlebige Prozesse programmgesteuert mit Hilfe eines webbasierten Java-Client-Programms, das die Invocation-API verwendet, eines ASP.NET-Programms, das Webservices verwendet, und eines mit Flex erstellten Client-Programms, das Remoting verwendet, auf.
seo-description: Programmatically invoke human-centric long-lived processes created in Workbench using a Java web-based client application that uses the Invocation API, an ASP.NET application that uses web services, and a client application built with Flex that uses Remoting.
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
role: Developer
exl-id: c9ebad8b-b631-492d-99a3-094e892b2ddb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '3699'
ht-degree: 100%

---

# An Menschen orientierte langlebige Prozesse aufrufen {#invoking-human-centric-long-lived-processes}

Sie können in Workbench erstellte, am Menschen orientierte langlebige Prozesse programmgesteuert unter Verwendung der folgenden Client-Programme aufrufen:

* Ein webbasiertes Java-Client-Programm, das die Invocation-API verwendet. (Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)
* Ein ASP.NET-Programm, das Webservices verwendet. (Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mit Webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Eine mit Flex erstellte Client-Anwendung, die Remoting verwendet. (Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM-Formulare nicht mehr unterstützt)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Der langlebige Prozess, der aufgerufen wird, heißt *FirstAppSolution/PreLoanProcess*. Sie können diesen Prozess erstellen, indem Sie der Anleitung unter [Erstellen des ersten AEM Forms-Programms](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63) folgen.

Ein am Menschen orientierter Prozess umfasst eine Aufgabe, auf die ein Benutzer mithilfe von Workspace reagieren kann. Beispielsweise können Sie mit Workbench einen Prozess erstellen, mit dem der Manager einer Bank einen Kreditantrag genehmigen oder ablehnen kann. Die folgende Abbildung zeigt den Prozess *FirstAppSolution/PreLoanProcess*.

Der *FirstAppSolution/PreLoanProcess*-Prozess akzeptiert einen Eingabeparameter namens *formData* vom Datentyp XML. Die XML-Daten werden mit einem Formularentwurf zusammengeführt, der *PreLoanForm.xdp* heißt. Die folgende Abbildung zeigt ein Formular, das eine Aufgabe darstellt, die einem Benutzer zugewiesen wurde, um einen Kreditantrag zu genehmigen oder abzulehnen. Der Benutzer verwendet Workspace, um den Antrag zu genehmigen oder abzulehnen. Der Workspace-Benutzer kann den Kreditantrag genehmigen, indem er auf die in der folgenden Abbildung dargestellte Schaltfläche „Genehmigen“ klickt. Ebenso kann der Benutzer die Kreditanfrage ablehnen, indem er auf die Schaltfläche „Ablehnen“ klickt.

Ein langlebiger Prozess wird asynchron aufgerufen und kann aufgrund der folgenden Faktoren nicht synchron aufgerufen werden:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Zur Beendigung eines Prozesses ist eine externe Eingabe erforderlich. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Büro ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

Wenn ein langlebiger Prozess aufgerufen wird, erstellt AEM Forms beim Erstellen eines Datensatzes einen Wert für die Aufrufkennung. Der Datensatz verfolgt den Status des langlebigen Prozesses und wird in der AEM Forms-Datenbank gespeichert. Mithilfe des Werts für die Aufrufkennung können Sie den Status des langlebigen Prozesses verfolgen. Darüber hinaus können Sie den Wert für die Prozessaufruf-ID verwenden, um Process Manager-Vorgänge auszuführen, z. B. das Beenden einer laufenden Prozessinstanz.

>[!NOTE]
>
>AEM Forms erstellt beim Aufrufen eines kurzlebigen Prozesses weder einen Aufrufkennungswert noch einen Datensatz.

Der `FirstAppSolution/PreLoanProcess`-Prozess wird aufgerufen, wenn ein Antragsteller einen Antrag sendet, der in Form von XML-Daten dargestellt wird. Der Name der Eingabeprozessvariablen lautet `formData` und ihr Datentyp XML ist. Für die Zwecke dieser Diskussion nehmen wir an, dass die folgenden XML-Daten als Eingabe für den `FirstAppSolution/PreLoanProcess`-Prozess verwendet werden.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <LoanApp>
 <Name>Sam White</Name>
 <LoanAmount>250000</LoanAmount>
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail>
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
 </LoanApp>
```

Die an einen Prozess übergebenen XML-Daten müssen den Feldern in dem Formular entsprechen, das im Prozess verwendet wird. Andernfalls werden keine Daten im Formular angezeigt. Alle Programme, die den `FirstAppSolution/PreLoanProcess`-Prozess aufrufen, müssen diese XML-Datenquelle übergeben. Die in *Aufrufen von am Menschen orientierten langlebigen Prozessen* erstellten Programme erstellen die XML-Datenquelle dynamisch aus den Werten, die ein Benutzer in einen Webclient eingegeben hat.

Mithilfe eines Client-Programms können Sie dem *FirstAppSolution/PreLoanProcess*-Prozess die erforderlichen XML-Daten senden. Ein langlebiger Prozess gibt einen Aufruf-ID-Wert als Rückgabewert zurück. Die folgende Abbildung zeigt Client-Programme, die den langlebigen Prozess „*FirstAppSolution/PreLoanProcess“ aufrufen. Die Client-Programme senden XML-Daten und erhalten einen Zeichenfolgenwert zurück, der den Wert der Aufrufkennung darstellt.

**Siehe auch**

[Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Erstellen einer ASP.NET-Webanwendung, die einen langlebigen, am Menschen orientierten Prozess aufruft](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Erstellung eines Client-Programms mit Flex, das einen an Menschen orientierten, langlebigen Prozess aufruft](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

Sie können ein webbasiertes Programm erstellen, das ein Java-Servlet verwendet, um den `FirstAppSolution/PreLoanProcess`-Prozess aufzurufen. Um diesen Prozess über ein Java-Servlet aufzurufen, verwenden Sie die Invocation-API im Java-Servlet. (Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mit der Java API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

Die folgende Abbildung zeigt ein webbasiertes Client-Programm, das Werte für Name, Telefon (oder E-Mail) und Betrag veröffentlicht. Diese Werte werden an das Java-Servlet gesendet, wenn der Benutzer auf die Schaltfläche „Programm übermitteln“ klickt.

Das Java-Servlet führt die folgenden Aufgaben aus:

* Abrufen der Werte, die von der HTML-Seite an das Java-Servlet gesendet werden.
* Dynamisches Erstellen einer XML-Datenquelle, die an den *FirstAppSolution/PreLoanProcess*-Prozess übergeben wird. Die Werte für Name, Telefon (oder E-Mail) und Betrag werden in der XML-Datenquelle angegeben.
* Aufrufen des *FirstAppSolution/PreLoanProcess*-Prozesses mithilfe der AEM Forms Invocation-API.
* Zurückgeben des Werts der Aufrufkennung an den Client-Webbrowser.

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein webbasiertes Java-Programm zu erstellen, das den `FirstAppSolution/PreLoanProcess` -Prozess aufruft, führen Sie die folgenden Schritte aus:

1. [Erstellen Sie ein Web-Projekt](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Erstellen Sie die Java-Programmlogik für das Servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [Erstellen der Web-Seite für die Webanwendung](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Verpacken Sie die Webanwendung in eine WAR-Datei.](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Stellen Sie die WAR-Datei auf dem J2EE-Anwendungsserver bereit, der als Host für AEM Forms dient](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms).
1. [Testen Sie die Webanwendung](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Einige dieser Schritte hängen von dem J2EE-Programm ab, auf dem AEM Forms bereitgestellt wird. Die Methode zum Bereitstellen einer WAR-Datei hängt beispielsweise von dem verwendeten J2EE-Programm-Server ab. Es wird davon ausgegangen, dass AEM Forms auf JBoss® bereitgestellt wird.

### Erstellen eines Web-Projekts {#create-a-web-project}

Der erste Schritt zum Erstellen einer Webanwendung besteht darin, ein Web-Projekt zu erstellen. Die Java-IDE, auf der dieses Dokument basiert, ist Eclipse 3.3. Erstellen Sie mithilfe der Eclipse-IDE ein Web-Projekt und fügen Sie die erforderlichen JAR-Dateien zu Ihrem Projekt hinzu. Fügen Sie Ihrem Projekt eine HTML-Seite mit dem Namen *index.html* und ein Java-Servlet hinzu.

Die folgende Liste gibt die JAR-Dateien an, die Sie in Ihr Web-Projekt einbinden müssen:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>Die Datei „J2EE.jar“ definiert die Datentypen, die von einem Java-Servlet verwendet werden. Sie können diese JAR-Datei von dem J2EE-Anwendungs-Server abrufen, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Web-Projekts**

1. Starten Sie Eclipse und klicken Sie auf **Datei** > **Neues Projekt**.
1. Wählen Sie im Dialogfeld **Neues Projekt** die Optionen **Web** > **Dynamisches Webprojekt**.
1. Geben Sie `InvokePreLoanProcess` als Namen Ihres Projekts ein und klicken Sie dann auf **Fertig stellen**.

**Hinzufügen erforderlicher JAR-Dateien zu Ihrem Projekt**

1. Klicken Sie im Fenster „Projekt-Explorer“ mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Eigenschaften** aus.
1. Klicken Sie auf **Java-Build-Pfad** und anschließend auf die Registerkarte **Bibliotheken**.
1. Klicken Sie auf **Externe JARs hinzufügen** und navigieren Sie zu den einzubindenden JAR-Dateien.

**Hinzufügen eines Java-Servlets zu Ihrem Projekt**

1. Klicken Sie im Fenster „Projekt Explorer“ mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Neu** > **Sonstiges**.
1. Erweitern Sie den Ordner **Web**, wählen Sie **Servlet** aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie im Dialogfeld „Servlet erstellen“ als Namen des Servlets `SubmitXML` ein und klicken Sie dann auf **Fertig stellen**.

**Hinzufügen einer HTML-Seite zu einem Projekt**

1. Klicken Sie im Fenster „Projekt Explorer“ mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Neu** > **Sonstiges**.
1. Erweitern Sie den Ordner **Web**, wählen Sie **HTML** aus und klicken Sie auf **Weiter**.
1. Geben Sie im Dialogfeld „Neue HTML“ als Dateinamen `index.html` ein und klicken Sie dann auf **Fertig stellen**.

>[!NOTE]
>
>Informationen zum Erstellen von HTML-Inhalten, die das Java-Servlet SubmitXML aufrufen, finden Sie unter [Erstellen der Webseite für die Webanwendung](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application).

### Erstellen der Java-Programmlogik für das Servlet {#create-java-application-logic-for-the-servlet}

Erstellen Sie eine Java-Programmlogik, die den `FirstAppSolution/PreLoanProcess`-Prozess aus dem Java-Servlet heraus aufruft. Der folgende Code zeigt die Syntax des Java-Servlets `SubmitXML`:

```java
     public class SubmitXML extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
         doPost(req,resp);
 
         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
             //Add code here to invoke the FirstAppSolution/PreLoanProcess process
             }
```

Normalerweise würden Sie keinen Client-Code in der Methode `doGet` oder `doPost` innerhalb eines Java-Servlets platzieren. Eine bessere Programmierpraxis besteht darin, diesen Code in einer separaten Klasse zu platzieren. Instanziieren Sie dann die Klasse aus der `doPost`-Methode (oder `doGet`-Methode) heraus und rufen Sie die entsprechenden Methoden auf. Codebeispiele werden jedoch aus Gründen der Übersichtlichkeit des Codes auf ein Minimum beschränkt und in der `doPost`-Methode aufgeführt.

Um den `FirstAppSolution/PreLoanProcess`-Prozess mithilfe der Aufruf-API aufzurufen, führen Sie die folgenden Aufgaben aus:

1. Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Rufen Sie die Werte für den Namen, die Telefonnummer und den Betrag ab, die von der HTML-Seite gesendet werden. Verwenden Sie diese Werte, um dynamisch eine XML-Datenquelle zu erstellen, die an die `FirstAppSolution/PreLoanProcess`-Prozess gesendet wird. Zum Erstellen der XML-Datenquelle können Sie `org.w3c.dom`-Klassen verwenden (diese Programmlogik wird im folgenden Codebeispiel gezeigt).
1. Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Erstellen Sie ein `ServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Mit einem `ServiceClient` -Objekt können Sie einen Dienstvorgang aufrufen. Es erledigt Aufgaben wie das Auffinden, Versenden und Weiterleiten von Aufrufanforderungen.
1. Erstellen Sie ein Objekt `java.util.HashMap`, indem Sie den Konstruktor verwenden.
1. Rufen Sie die Methode `java.util.HashMap` des `put`-Objekts für jeden Eingabeparameter auf, der an den langlebigen Prozess übergeben erden soll. Stellen Sie sicher, dass Sie den Namen der Eingabeparameter des Prozesses angeben. Da der `FirstAppSolution/PreLoanProcess`-Prozess einen Eingabeparameter vom Typ `XML` (`formData` genannt) erfordert, brauchen Sie nur die `put`-Methode aufzurufen.

   ```java
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
    
    //Create a Map object to store the parameter value
    Map params = new HashMap();
    params.put("formData", inXML);
   ```

1. Erstellen Sie ein `InvocationRequest`-Objekt, indem Sie die Methode `createInvocationRequest` des `ServiceClientFactory`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein string-Wert, der den Namen des langlebigen aufzurufenden Prozesses angibt. Um den Prozess `FirstAppSolution/PreLoanProcess` aufzurufen, geben Sie `FirstAppSolution/PreLoanProcess` an.
   * Ein string-Wert, der den Prozessvorgangsnamen darstellt. Der Name des langlebigen Prozessvorgangs lautet `invoke`.
   * Das `java.util.HashMap`-Objekt, das die Parameterwerte enthält, die für den Dienstvorgang erforderlich sind.
   * Ein boolescher Wert, der `false` angibt, sodass eine asynchrone Anfrage erstellt wird (dieser Wert kann zum Aufrufen eines langlebigen Prozesses verwendet werden).

   >[!NOTE]
   >
   >*Ein kurzlebiger Prozess kann aufgerufen werden, indem der Wert „true“ als vierter Parameter der createInvocationRequest-Methode übergeben wird. Wenn Sie den Wert „true“ übergeben, wird eine synchrone Anfrage erstellt.*

1. Senden Sie die Aufrufanforderung an AEM Forms, indem Sie die `invoke`-Methode des `ServiceClient`-Objekts aufrufen und das `InvocationRequest`-Objekt übergeben. Die `invoke`-Methode gibt ein `InvocationReponse`-Objekt zurück.
1. Ein langlebiger Prozess gibt einen Zeichenfolgenwert zurück, der einen Aufrufkennungswert darstellt. Rufen Sie diesen Wert ab, indem Sie die `getInvocationId`-Methode des `InvocationReponse`-Objekts aufrufen.

   ```java
    //Send the invocation request to the long-lived process and
    //get back an invocation response object
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
    String invocationId = lcResponse.getInvocationId();
   ```

1. Schreiben Sie den Aufrufkennungswert in den Client-Webbrowser. Zum Schreiben dieses Werts in den Webbrowser des Clients können Sie eine `java.io.PrintWriter`-Instanz verwenden.

### Schnellstart: Aufrufen eines langlebigen Prozesses mithilfe der Aufruf-API {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

Das folgende Java-Code-Beispiel stellt das Java-Servlet dar, das den `FirstAppSolution/PreLoanProcess`-Prozess aufruft.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-livecycle-client.jar
     * 2. adobe-usermanager-client.jar
     *
     * (Because this  quick start is implemented as a Java servlet, it is
     * not necessary to include J2EE specific JAR files - the Java project
     * that contains this quick start is exported as a WAR file which
     * is deployed to the J2EE application server)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * For complete details about the location of these JAR files,
     * see "Including AEM Forms library files" in Programming with AEM forms
     * */
 import java.io.ByteArrayOutputStream;
 import java.io.File;
 import java.io.IOException;
 import java.io.PrintWriter;
 
 import javax.servlet.ServletException;
 import javax.servlet.http.HttpServletRequest;
 import javax.servlet.http.HttpServletResponse;
 import java.util.*;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import javax.xml.parsers.DocumentBuilder;
 import javax.xml.parsers.DocumentBuilderFactory;
 import javax.xml.transform.Transformer;
 import javax.xml.transform.TransformerFactory;
 import javax.xml.transform.dom.DOMSource;
 import javax.xml.transform.stream.StreamResult;
 
 import com.adobe.idp.dsc.InvocationRequest;
 import com.adobe.idp.dsc.InvocationResponse;
 import com.adobe.idp.dsc.clientsdk.ServiceClient;
 import org.w3c.dom.Element;
 
     public class SubmitXML extends javax.servlet.http.HttpServlet implements javax.servlet.Servlet {
       static final long serialVersionUID = 1L;
 
        public SubmitXML() {
         super();
     }
 
 
     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
         // TODO Auto-generated method stub
         doPost(request,response);
     }
 
     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a ServiceClient object
             ServiceClient myServiceClient = myFactory.getServiceClient();
 
             //Get the values that are passed from the Loan HTML page
             String name = (String)request.getParameter("name");
             String phone = (String)request.getParameter("phone");
             String amount = (String)request.getParameter("amount");
 
             //Create XML to pass to the FirstAppSolution/PreLoanProcess process
             org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
 
             //Create a Map object to store the XML input parameter value
             Map params = new HashMap();
             params.put("formData", inXML);
 
             //Create an InvocationRequest object
             InvocationRequest lcRequest =  myFactory.createInvocationRequest(
                 "FirstAppSolution/PreLoanProcess", //Specify the long-lived process name
                     "invoke",           //Specify the operation name
                     params,               //Specify input values
                     false);               //Create an asynchronous request
 
             //Send the invocation request to the long-lived process and
             //get back an invocation response object
             InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
             String invocationId = lcResponse.getInvocationId();
 
             //Create a PrintWriter instance
             PrintWriter pp = response.getWriter();
 
             //Write the invocation identifier value back to the client web browser
             pp.println("The job status identifier value is: " +invocationId);
 
         }catch (Exception e) {
              System.out.println("The following exception occurred: "+e.getMessage());
       }
     }
 
 
      //Create XML data to pass to the long-lived process
      private static org.w3c.dom.Document GetDataSource(String name, String phone, String amount)
      {
             org.w3c.dom.Document document = null;
 
             try
             {
                 //Create DocumentBuilderFactory and DocumentBuilder objects
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
                 DocumentBuilder builder = factory.newDocumentBuilder();
 
                 //Create a new Document object
                 document = builder.newDocument();
 
                 //Create MortgageApp - the root element in the XML
                 Element root = (Element)document.createElement("LoanApp");
                 document.appendChild(root);
 
                 //Create an XML element for Name
                 Element nameElement = (Element)document.createElement("Name");
                 nameElement.appendChild(document.createTextNode(name));
                 root.appendChild(nameElement);
 
                 //Create an XML element for Phone
                 Element phoneElement = (Element)document.createElement("PhoneOrEmail");
                 phoneElement.appendChild(document.createTextNode(phone));
                 root.appendChild(phoneElement);
 
                 //Create an XML element for amount
                 Element loanElement = (Element)document.createElement("LoanAmount");
                 loanElement.appendChild(document.createTextNode(amount));
                 root.appendChild(loanElement);
 
                 //Create an XML element for ApprovalStatus
                 Element approveElement = (Element)document.createElement("ApprovalStatus");
                 approveElement.appendChild(document.createTextNode("PENDING APPROVAL"));
                 root.appendChild(approveElement);
 
               }
          catch (Exception e) {
                   System.out.println("The following exception occurred: "+e.getMessage());
                }
         return document;
          }
         }
```

### Erstellen der Web-Seite für die Webanwendung {#create-the-web-page-for-the-web-application}

Die Web-Seite *index.html* bietet einen Einstiegspunkt zu dem Java-Servlet, das den `FirstAppSolution/PreLoanProcess`-Prozess aufruft. Diese Web-Seite ist ein einfaches HTML-Formular, das ein HTML-Formular und eine Schaltfläche „Senden“ enthält. Wenn der Benutzer auf die Schaltfläche „Senden“ klickt, werden die Formulardaten an das `SubmitXML`-Java-Servlet abgeschickt.

Das Java-Servlet erfasst die von der HTML-Seite veröffentlichten Daten mithilfe des folgenden Java-Codes:

```java
 //Get the values that are passed from the Loan HTML page
 String name = request.getParameter("name");
 String phone = request.getParameter("phone");
 String amount = request.getParameter("amount");
```

Der folgende HTML-Code stellt die Datei index.html dar, die beim Einrichten der Entwicklungsumgebung erstellt wurde. (Siehe [Erstellen eines Webprojekts](invoking-human-centric-long-lived.md#create-a-web-project).)

```xml
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "https://www.w3.org/TR/html4/loose.dtd">
 <html>
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
 <title>Insert title here</title>
 </head>
 <body>
 <table>
     <TBODY>
         <TR>
             <td><img src="financeCorpLogo.jpg" width="172" height="62"></TD>
             <td><FONT size="+2"><strong>Java Loan Application Page</strong></FONT></TD>
             <td> </TD>
             <td> </TD>
         </TR>
 
     </TBODY>
 </TABLE>
     <FORM action="https://hiro-xp:8080/PreLoanProcess/SubmitXML" method="post">
        <table>
          <TBODY>
                <TR>
                      <td><LABEL for="name">Name: </LABEL></TD>
                  <td><INPUT type="text" name="name"></TD>
                  <td><input type="submit" value="Submit Application"></TD>
                  </TR>
            <TR>
                  <td> <LABEL for="phone">Phone/Email: </LABEL></TD>
              <td><INPUT type="text" name="phone"></TD>
                  <td></TD>
              </TR>
 
            <TR>
                  <td><LABEL for="amount">Amount: </LABEL></TD>
              <td><INPUT type="text" name="amount"></TD>
                 <td></TD>
             </TR>
          </TBODY>
 </TABLE>
       </FORM>
 </body>
 </html>
```

### Packen der Webanwendung in eine WAR-Datei {#package-the-web-application-to-a-war-file}

Um das Java-Servlet bereitzustellen, das den `FirstAppSolution/PreLoanProcess`-Prozess aufruft, packen Sie Ihre Webanwendung in eine WAR-Datei. Stellen Sie sicher, dass externe JAR-Dateien, von denen die Geschäftslogik der Komponente abhängig ist, wie z. B. adobe-livecycle-client.jar und adobe-usermanager-client.jar, ebenfalls in der WAR-Datei enthalten sind.

Die folgende Abbildung zeigt den Inhalt des Eclipse-Projekts, das in eine WAR-Datei gepackt ist.

>[!NOTE]
>
>In der vorstehenden Abbildung kann die JPG-Datei durch eine beliebige JPG-Bilddatei ersetzt werden.

**So packen Sie eine Webanwendung in eine WAR-Datei:**

1. Im **Projekt-Explorer**-Fenster klicken Sie mit der rechten Maustaste auf das `InvokePreLoanProcess`-Projekt und wählen **Export** > **WAR-Datei** aus.
1. In das Textfeld **Webmodul** schreiben Sie `InvokePreLoanProcess` für den Namen des Java-Projekts.
1. In das Textfeld **Ziel** schreiben Sie **`PreLoanProcess.war`** für denDateinamen, anschließend geben Sie den Speicherort für Ihre WAR-Datei an und klicken auf „Beenden“.

### Bereitstellen der WAR-Datei für den J2EE-Anwendungsserver, der als Host für AEM Forms dient {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Stellen Sie die WAR-Datei dem J2EE-Anwendungsserver bereit, auf dem AEM Forms bereitgestellt ist. Um die WAR-Datei auf dem J2EE-Anwendungsserver bereitzustellen, kopieren Sie die WAR-Datei aus dem Exportpfad nach `[AEM Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy`.

>[!NOTE]
>
>Wenn AEM Forms nicht auf JBoss bereitgestellt wird, müssen Sie die WAR-Datei in Übereinstimmung mit dem J2EE-Programm-Server bereitstellen, der als Host für AEM Forms dient.

### Testen des Web-Programms {#test-your-web-application}

Nach der Bereitstellung der Webanwendung können Sie sie mithilfe eines Webbrowsers testen. Wenn Sie denselben Computer verwenden, auf dem AEM Forms gehostet wird, können Sie folgende URL angeben:

* http://localhost:8080/PreLoanProcess/index.html

   Geben Sie Werte in die HTML-Formularfelder ein und klicken Sie auf die Schaltfläche „Antrag einreichen“. Wenn Probleme auftreten, lesen Sie die Protokolldatei des J2EE-Anwendungsservers.

>[!NOTE]
>
>Um zu bestätigen, dass das Java-Programm den Prozess aufgerufen hat, starten Sie Workspace und akzeptieren Sie das Darlehen.

## Erstellen einer ASP.NET-Webanwendung, die einen langlebigen, am Menschen orientierten Prozess aufruft {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

Sie können ein ASP.NET-Programm erstellen, das den Prozess `FirstAppSolution/PreLoanProcess` aufruft. Um diesen Prozess von einem ASP.NET-Programm aus aufzurufen, verwenden Sie Web-Services. (Siehe [Aufrufen von AEM Forms mithilfe von Web-Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)).

Die folgende Abbildung zeigt ein ASP.NET-Client-Programm, das Daten von einem Endbenutzer abruft. Die Daten werden in einer XML-Datenquelle abgelegt und an den `FirstAppSolution/PreLoanProcess`-Prozess gesendet, wenn der Benutzer auf die Schaltfläche „Antrag einreichen“ klickt.

Beachten Sie, dass nach dem Aufrufen des Prozesses ein Wert für die Aufrufkennung angezeigt wird. Ein Wert für die Aufrufkennung wird als Teil eines Datensatzes erstellt, der den Status des langlebigen Prozesses verfolgt.

Das ASP.NET-Programm führt die folgenden Aufgaben aus:

* Es ruft die Werte ab, die der Benutzer auf der Web-Seite eingegeben hat.
* Dynamisches Erstellen einer XML-Datenquelle, die an den Prozess „FirstAppSolution/PreLoanProcess“ übergeben wird. Die drei Werte werden in der XML-Datenquelle angegeben.
* Ruft den Prozess „FirstAppSolution/PreLoanProcess“ mithilfe der Web-Services auf.
* Gibt den Wert der Aufrufkennung und den Status des langlebigen Vorgangs an den Client-Webbrowser zurück.

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein ASP.NET-Programm zu erstellen, das in der Lage ist, den Prozess FirstAppSolution/PreLoanProcess aufzurufen, führen Sie die folgenden Schritte aus:

1. [Erstellen eines ASP.NET-Web-Programms](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Erstellen einer ASP-Seite, die den FirstAppSolution/PreLoanProcess aufruft](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess).
1. [Ausführen des ASP.NET-Programms](invoking-human-centric-long-lived.md#run-the-asp-net-application).

### Erstellen eines ASP.NET-Web-Programms {#create-an-asp-net-web-application}

Erstellen Sie ein Microsoft .NET C# ASP.NET-Web-Programm. Die folgende Abbildung zeigt den Inhalt des ASP.NET-Projekts mit dem Namen *InvokePreLoanProcess*.

Beachten Sie, dass es unter den Service-Verweisen zwei Elemente gibt. Das erste Element heißt „JobManager“. Diese Referenz ermöglicht es dem ASP.NET-Programm, den Job Manager-Service aufzurufen. Dieser Service gibt Informationen zum Status eines langlebigen Prozesses zurück. Wenn der Prozess beispielsweise gerade ausgeführt wird, gibt dieser Service einen numerischen Wert zurück, der angibt, dass der Prozess gerade ausgeführt wird. Die zweite Referenz heißt *PreLoanProcess*. Dieser Service-Verweis stellt den Verweis zum Prozess „FirstAppSolution/PreLoanProcess“ dar. Nachdem Sie einen Service-Verweis erstellt haben, sind mit dem AEM Forms-Service verknüpfte Datentypen für die Verwendung in Ihrem .NET-Projekt verfügbar.

**So erstellen Sie ein ASP.NET-Projekt:**

1. Starten Sie Microsoft Visual Studio 2008.
1. Wählen Sie im Menü **Datei** die Option **Neu**, **Website**.
1. Wählen Sie in der Liste **Vorlagen** die Option **ASP.NET-Website**.
1. Wählen Sie im Feld **Speicherort** einen Speicherort für Ihr Projekt aus. Nennen Sie Ihr Projekt *InvokePreLoanProcess*.
1. Wählen Sie im Feld **Sprache** Visual C#
1. Klicken Sie auf OK.

**Hinzufügen von Service-Verweisen:**

1. Wählen Sie im Menü „Projekt“ die Option **Service-Verweis hinzufügen**.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den Job Manager-Service an.

   ```java
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Geben Sie in das Feld „Namespace“ `JobManager` ein.
1. Klicken Sie auf **Los** und dann auf **OK**.
1. Wählen Sie im Menü **Projekt** die Option **Service-Verweis hinzufügen**.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den Prozess „FirstAppSolution/PreLoanProcess“ an.

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Geben Sie im Feld „Namespace“ `PreLoanProcess` ein.
1. Klicken Sie auf **Los** und dann auf **OK**.

>[!NOTE]
>
>Ersetzen Sie `hiro-xp` durch die IP-Adresse des J2EE-Programm-Servers, der als Host für AEM Forms dient. Die Option `lc_version` stellt sicher, dass AEM Forms-Funktionen wie MTOM verfügbar sind. Ohne Angabe der Option `lc_version` können Sie AEM Forms nicht mit MTOM aufrufen. (Siehe [Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)).

### Erstellen einer ASP-Seite, die den FirstAppSolution/PreLoanProcess aufruft {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

Fügen Sie innerhalb des ASP.NET-Projekts ein Web-Formular (eine ASPX-Datei) hinzu, das für die Anzeige einer HTML-Seite für den Antragsteller des Darlehens verantwortlich ist. Das Web-Formular basiert auf einer Klasse, die von `System.Web.UI.Page` abgeleitet ist. Die C#-Anwendungslogik, die `FirstAppSolution/PreLoanProcess` aufruft, befindet sich in der Methode `Button1_Click` (diese Schaltfläche stellt die Schaltfläche „Antrag einreichen“ dar).

Die folgende Abbildung zeigt das ASP.NET-Programm

In der folgenden Tabelle sind die Steuerelemente aufgeführt, die Teil dieses ASP.NET-Programms sind.

<table>
 <thead>
  <tr>
   <th><p>Name des Steuerelements</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>TextBoxName</p></td>
   <td><p>Gibt den Vor- und Nachnamen des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>TextBoxPhone</p></td>
   <td><p>Gibt die Telefonnummer oder E-Mail-Adresse des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>TextBoxAmount</p></td>
   <td><p>Gibt den Darlehensbetrag an.</p></td>
  </tr>
  <tr>
   <td><p>Button1</p></td>
   <td><p>Stellt die Schaltfläche „Antrag einreichen“ dar.</p></td>
  </tr>
  <tr>
   <td><p>LabelJobID</p></td>
   <td><p>Ein Steuerelement zur Kennzeichnung, das den Wert der Aufrufkennung angibt.</p></td>
  </tr>
  <tr>
   <td><p>LabelStatus</p></td>
   <td><p>Ein Steuerelement zur Kennzeichnung, das den Wert des Auftragsstatus angibt. Dieser Wert wird durch Aufrufen des Job Manager-Services abgerufen. </p></td>
  </tr>
 </tbody>
</table>

Die Anwendungslogik, die Teil des ASP.NET-Programms ist, muss dynamisch eine XML-Datenquelle erstellen, die an den Prozess `FirstAppSolution/PreLoanProcess` übergeben wird. Die Werte, die der Antragsteller auf der HTML-Seite eingegeben hat, müssen in der XML-Datenquelle angegeben werden. Diese Datenwerte werden beim Anzeigen des Formulars in Workspace mit dem Formular zusammengeführt. Die Klassen, die sich im Namespace `System.Xml` befinden, werden zum Erstellen der XML-Datenquelle verwendet.

Beim Aufrufen eines Prozesses, der XML-Daten aus einem ASP.NET-Programm erfordert, steht Ihnen ein XML-Datentyp zur Verfügung. Das heißt, Sie können keine `System.Xml.XmlDocument`-Instanz an den Prozess übergeben. Der vollständig qualifizierte Name dieser XML-Instanz, die an den Prozess übergeben wird, lautet `InvokePreLoanProcess.PreLoanProcess.XML`. Konvertieren Sie die `System.Xml.XmlDocument`-Instanz zu `InvokePreLoanProcess.PreLoanProcess.XML`. Sie können diese Aufgabe mithilfe des folgenden Codes ausführen.

```java
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process
 XmlDocument myXML = CreateXML(userName, phone, amount);
 
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance
 StringWriter sw = new StringWriter();
 XmlTextWriter xw = new XmlTextWriter(sw);
 myXML.WriteTo(xw);
 
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML();
 inXML.document = sw.ToString();
```

Um eine ASP-Seite zu erstellen, die den Prozess `FirstAppSolution/PreLoanProcess` aufruft, führen Sie die folgenden Aufgaben in der Methode `Button1_Click` aus:

1. Erstellen Sie ein `FirstAppSolution_PreLoanProcessClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
1. Erstellen Sie ein `FirstAppSolution_PreLoanProcessClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL und den Typ der Codierung angibt:

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Stellen Sie jedoch sicher, dass Sie `?blob=mtom` angeben.

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp`* durch die IP-Adresse des J2EE-Programm-Servers, der als Host für AEM Forms dient. *

1. Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Datenelements `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
1. Setzen Sie das Datenelement `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
1. Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

   * Weisen Sie dem Datenelement `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
   * Weisen Sie dem Datenelement `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
   * Weisen Sie dem Datenelement `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Datenelement `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   Das folgende Code-Beispiel zeigt diese Aufgaben.

   ```as3
    //Enable BASIC HTTP authentication
    BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding;
    b.MessageEncoding = WSMessageEncoding.Mtom;
    mortgageClient.ClientCredentials.UserName.UserName = "administrator";
    mortgageClient.ClientCredentials.UserName.Password = "password";
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
    b.MaxReceivedMessageSize = 2000000;
    b.MaxBufferSize = 2000000;
    b.ReaderQuotas.MaxArrayLength = 2000000;
   ```

1. Rufen Sie die Werte für Name, Telefon und Betrag ab, die der Benutzer auf der Web-Seite eingegeben hat. Verwenden Sie diese Werte, um dynamisch eine XML-Datenquelle zu erstellen, die an den `FirstAppSolution/PreLoanProcess`-Prozess gesendet wird. Erstellen Sie ein `System.Xml.XmlDocument`, das die XML-Datenquelle darstellt, die an den Prozess übergeben werden soll (diese Programmlogik wird im folgenden Code-Beispiel gezeigt).
1. Konvertieren Sie die `System.Xml.XmlDocument`-Instanz in `InvokePreLoanProcess.PreLoanProcess.XML` (diese Programmlogik wird im folgenden Code-Beispiel gezeigt).
1. Rufen Sie den `FirstAppSolution/PreLoanProcess`-Prozess auf, indem Sie die `invoke_Async`-Methode des `FirstAppSolution_PreLoanProcessClient`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Aufrufkennung des langlebigen Prozesses darstellt.
1. Erstellen Sie einen `JobManagerClient`, indem Sie dessen Konstruktor verwenden. (Stellen Sie sicher, dass Sie einen Service-Verweis auf den Job Manager-Service festgelegt haben.)
1. Wiederholen Sie die Schritte 1 bis 5. Geben Sie die folgende URL für Schritt 2 an: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Erstellen Sie ein Objekt `JobId`, indem Sie den Konstruktor verwenden.
1. Legen Sie das `id`-Datenelement des `JobId`-Objekts mit dem Rückgabewert der `invoke_Async`-Methode des `FirstAppSolution_PreLoanProcessClient`-Objekts fest.
1. Weisen Sie `value` mit „true“ zum `persistent`-Datenelement des `JobId`-Objekts zu.
1. Erstellen Sie ein `JobStatus`-Objekt, indem Sie die `getStatus`-Methode des `JobManagerService`-Objekts aufrufen und das `JobId`-Objekt übergeben.
1. Rufen Sie den Statuswert ab, indem Sie den Wert des `statusCode`-Datenelements des `JobStatus`-Objekts abrufen.
1. Weisen Sie den Wert der Aufrufkennung zum `LabelJobID.Text`-Feld zu.
1. Weisen Sie den Statuswert zum `LabelStatus.Text`-Feld zu.

### Schnellstart: Aufrufen eines langlebigen Prozesses mithilfe der Webservice-API {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

Das folgende C#-Code-Beispiel ruft den `FirstAppSolution/PreLoanProcess`-Prozess auf.

```csharp
 ???/**
     * Ensure that you create a .NET project that uses
     * MS Visual Studio 2008 and version 3.5 of the .NET
     * framework. This is required to invoke a
     * AEM Forms service using MTOM.
 
 
 using System;
 using System.Collections;
 using System.Configuration;
 using System.Data;
 using System.Linq;
 using System.Web;
 using System.ServiceModel;
 using System.Web.Security;
 using System.Web.UI;
 using System.Web.UI.HtmlControls;
 using System.Web.UI.WebControls;
 using System.Web.UI.WebControls.WebParts;
 using System.Xml.Linq;
 using System.Xml;
 using System.IO;
 
 //A reference to FirstAppSolution/PreLoanProcess
 using InvokePreLoanProcess.PreLoanProcess;
 
 //A reference to JobManager service
 using InvokePreLoanProcess.JobManager;
 
 
 namespace InvokePreLoanProcess
 {
        public partial class _Default : System.Web.UI.Page
        {
            //This method is called when the Submit Application button is
            //Clicked
            protected void Button1_Click(object sender, EventArgs e)
            {
                //Create a FirstAppSolution_PreLoanProcessClient object
                FirstAppSolution_PreLoanProcessClient mortgageClient = new FirstAppSolution_PreLoanProcessClient();
                mortgageClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom");
 
                //Enable BASIC HTTP authentication
                BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding;
                b.MessageEncoding = WSMessageEncoding.Mtom;
                mortgageClient.ClientCredentials.UserName.UserName = "administrator";
                mortgageClient.ClientCredentials.UserName.Password = "password";
                b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                b.MaxReceivedMessageSize = 2000000;
                b.MaxBufferSize = 2000000;
                b.ReaderQuotas.MaxArrayLength = 2000000;
 
                //Retrieve values that user entered into the web page
                String userName = TextBoxName.Text;
                String phone = TextBoxPhone.Text;
                String amount = TextBoxAmount.Text;
 
                //Create the XML to pass to the FirstAppSolution/PreLoanProcess process
                XmlDocument myXML = CreateXML(userName, phone, amount);
 
                StringWriter sw = new StringWriter();
                XmlTextWriter xw = new XmlTextWriter(sw);
                myXML.WriteTo(xw);
 
                InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML();
                inXML.document = sw.ToString();
 
                //INvoke the FirstAppSolution/PreLoanProcess process
                String invocationID =  mortgageClient.invoke_Async(inXML);
 
                //Create a JobManagerClient object to obtain the status of the long-lived operation
                JobManagerClient jobManager = new JobManagerClient();
                jobManager.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/JobManager?blob=mtom");
 
                //Enable BASIC HTTP authentication
                BasicHttpBinding b1 = (BasicHttpBinding)jobManager.Endpoint.Binding;
                b1.MessageEncoding = WSMessageEncoding.Mtom;
                jobManager.ClientCredentials.UserName.UserName = "administrator";
                jobManager.ClientCredentials.UserName.Password = "password";
                b1.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                b1.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                b1.MaxReceivedMessageSize = 2000000;
                b1.MaxBufferSize = 2000000;
                b1.ReaderQuotas.MaxArrayLength = 2000000;
 
 
                //Create a JobID object that represents the status of the
                //long-lived operation
                JobId jobId = new JobId();
                jobId.id = invocationID;
                jobId.persistent = true;
                JobStatus jobStatus = jobManager.getStatus(jobId);
                System.Int16 val2 = jobStatus.statusCode;
                LabelJobID.Text = "The job status identifier value is " + invocationID;
                LabelStatus.Text = "The status of the long-lived operation is " + getJobDescription(val2);
 
            }
 
            private static XmlDocument CreateXML(String name, String phone, String amount)
            {
                //This method dynamically creates a DDX document
                //to pass to the FirstAppSolution/PreLoanProcess process
                XmlDocument xmlDoc = new XmlDocument();
 
                //Create the root element and append it to the XML DOM
                System.Xml.XmlElement root = xmlDoc.CreateElement("LoanApp");
                xmlDoc.AppendChild(root);
 
                //Create the Name element
                XmlElement nameElement = xmlDoc.CreateElement("Name");
                nameElement.AppendChild(xmlDoc.CreateTextNode(name));
                root.AppendChild(nameElement);
 
                //Create the LoanAmount element
                XmlElement LoanAmount = xmlDoc.CreateElement("LoanAmount");
                LoanAmount.AppendChild(xmlDoc.CreateTextNode(amount));
                root.AppendChild(LoanAmount);
 
                //Create the PhoneOrEmail element
                XmlElement PhoneOrEmail = xmlDoc.CreateElement("PhoneOrEmail");
                PhoneOrEmail.AppendChild(xmlDoc.CreateTextNode(phone));
                root.AppendChild(PhoneOrEmail);
 
                //Create the ApprovalStatus element
                XmlElement ApprovalStatus = xmlDoc.CreateElement("ApprovalStatus");
                ApprovalStatus.AppendChild(xmlDoc.CreateTextNode("PENDING APPROVAL"));
                root.AppendChild(ApprovalStatus);
 
                //Return the XmlElement instance
                return xmlDoc;
            }
 
 
            //Returns the String value of the Job Manager status code
            private String getJobDescription(int val)
            {
                switch(val)
                {
                    case 0:
                        return "JOB_STATUS_UNKNOWN";
 
                    case 1:
                        return "JOB_STATUS_QUEUED";
 
                    case 2:
                        return "JOB_STATUS_RUNNING";
 
                    case 3:
                        return "JOB_STATUS_COMPLETED";
 
                    case 4:
                        return "JOB_STATUS_FAILED";
 
                     case 5:
                        return "JOB_STATUS_COMPLETED";
 
                    case 6:
                        return "JOB_STATUS_SUSPENDED";
 
                    case 7:
                        return "JOB_STATUS_COMPLETE_REQUESTED";
 
                    case 8:
                        return "JOB_STATUS_TERMINATE_REQUESTED";
 
                     case 9:
                        return "JOB_STATUS_SUSPEND_REQUESTED";
 
                       case 10:
                        return "JOB_STATUS_RESUME_REQUESTED";
                }
 
                return "";
            }
       }
 }
 
```

>[!NOTE]
>
>Die Werte in der benutzerdefinierten getJobDescription-Methode entsprechen den vom Job Manager-Service zurückgegebenen Werten.

### Ausführen des ASP.NET-Programms {#run-the-asp-net-application}

Nachdem Sie das ASP.NET-Programm kompiliert und bereitgestellt haben, können Sie es mithilfe eines Webbrowsers ausführen. Wenn der Name des ASP.NET-Projekts *InvokePreLoanProcess* lautet, geben Sie die folgende URL in einem Webbrowser an:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

Dabei ist „localhost“ der Name des Webservers, der das ASP.NET-Projekt hostet, und 1629 ist die Port-Nummer. Wenn Sie das ASP.NET-Programm kompilieren und erstellen, stellt Microsoft Visual Studio es automatisch bereit.

>[!NOTE]
>
>Um zu bestätigen, dass das ASP.NET-Programm den Prozess aufgerufen hat, starten Sie Workspace und akzeptieren Sie das Darlehen.

## Erstellung eines Client-Programms mit Flex, das einen an Menschen orientierten, langlebigen Prozess aufruft {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

Sie können ein mit Flex erstelltes Client-Programm erstellen, um den *FirstAppSolution/PreLoanProcess*-Prozess aufzurufen. Dieses Programm verwendet Remoting, um den *FirstAppSolution/PreLoanProcess*-Prozess aufzurufen. (Siehe [Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Die folgende Abbildung zeigt ein Client-Programm, das mit Flex erstellt wurde und Daten von einem Endbenutzer erfasst. Die Daten werden in eine XML-Datenquelle eingefügt und an den Prozess gesendet.

Beachten Sie, dass nach dem Aufrufen des Prozesses ein Wert für die Aufrufkennung angezeigt wird. Ein Wert für die Aufrufkennung wird als Teil eines Datensatzes erstellt, der den Status des langlebigen Prozesses verfolgt.

Das mit Flex erstellte Client-Programm führt die folgenden Aufgaben aus:

* Es ruft die Werte ab, die der Benutzer auf der Web-Seite eingegeben hat.
* Es erstellt dynamisch eine XML-Datenquelle, die an den *FirstAppSolution/PreLoanProcess*-Prozess übergeben wird. Die drei Werte werden in der XML-Datenquelle angegeben.
* Es ruft den *FirstAppSolution/PreLoanProcess*-Prozess mithilfe von Remoting auf.
* Es gibt den Wert der Aufrufkennung des langlebigen Prozesses zurück.

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um ein mit Flex erstelltes Client-Programm zu erstellen, das den FirstAppSolution/PreLoanProcess-Prozess aufrufen kann, führen Sie die folgenden Schritte aus:

1. Starten Sie ein neues Flex-Projekt.
1. Schließen Sie die Datei „adobe-remoting-provider.swc“ in den Klassenpfad Ihres Projekts ein. (Siehe [Einschließen der AEM Forms-Flex-Bibliotheksdatei](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Erstellen Sie eine `mx:RemoteObject`-Instanz mit ActionScript oder MXML. (Siehe [Erstellen einer mx:RemoteObject-Instanz](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Richten Sie eine `ChannelSet`-Instanz ein, um mit AEM Forms zu kommunizieren, und verknüpfen Sie sie mit der `mx:RemoteObject`-Instanz. (Siehe [Erstellen eines Kanals in AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Rufen Sie die `login`-Methode von „ChannelSet“ oder die `setCredentials`-Methode des Service auf, um den Wert und das Kennwort der Benutzerkennug anzugeben. (Siehe [Verwenden von Single Sign-on](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Erstellen Sie die XML-Datenquelle, die an den `FirstAppSolution/PreLoanProcess`-Prozess übergeben werden soll, indem Sie eine XML-Instanz erstellen. (Diese Anwendungslogik wird im folgenden Code-Beispiel gezeigt.)
1. Erstellen Sie ein Objekt des Typs „Object“ mithilfe des zugehörigen Konstruktors. Weisen Sie dem Objekt die XML zu, indem Sie den Namen des Eingabeparameters des Prozesses angeben, wie im folgenden Code gezeigt:

   ```csharp
    //Get the XML data to pass to the AEM Forms process
    var xml:XML = createXML();
    var params:Object = new Object();
    params["formData"]=xml;
   ```

1. Rufen Sie den Prozess `FirstAppSolution/PreLoanProcess` auf, indem Sie die Methode `invoke_Async` der `mx:RemoteObject`-Instanz aufrufen. Übergeben Sie das `Object`, das den Eingabeparameter enthält. (Weitere Informationen finden Sie unter [Übergeben von Eingabewerten](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Rufen Sie den Aufrufkennungswert ab, der von einem langlebigen Prozess zurückgegeben wird, wie im folgenden Code gezeigt:

   ```csharp
    // Handles async call that invokes the long-lived process
    private function resultHandler(event:ResultEvent):void
    {
    ji = event.result as JobId;
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
    }
   ```

### Aufrufen eines langlebigen Prozesses mithilfe von Remoting {#invoking-a-long-lived-process-using-remoting}

Im folgenden Flex-Code-Beispiel wird der Prozess `FirstAppSolution/PreLoanProcess` aufgerufen.

```java
 <?xml version="1.0" encoding="utf-8"?>
 
 <mx:Application  xmlns="*" backgroundColor="#FFFFFF"
      creationComplete="initializeChannelSet();">
 
 <mx:Script>
          <![CDATA[
 
             import mx.controls.Alert;
             import mx.rpc.events.FaultEvent;
             import mx.rpc.events.ResultEvent;
             import flash.net.navigateToURL;
             import mx.messaging.ChannelSet;
             import mx.messaging.channels.AMFChannel;
             import mx.collections.ArrayCollection;
             import mx.rpc.livecycle.JobId;
             import mx.rpc.livecycle.JobStatus;
             import mx.rpc.livecycle.DocumentReference;
             import mx.formatters.NumberFormatter;
 
             // Holds the job ID returned by LC.JobManager
             private var ji:JobId;
 
             private function initializeChannelSet():void
              {
              var cs:ChannelSet= new ChannelSet();
         cs.addChannel(new AMFChannel("remoting-amf", "https://hiro-xp:8080/remoting/messagebroker/amf"));
         LC_MortgageApp.setCredentials("tblue", "password");
         LC_MortgageApp.channelSet = cs;
              }
 
            private function submitApplication():void
             {
             //Get the XML data to pass to the AEM Forms process
             var xml:XML = createXML();
             var params:Object = new Object();
             params["formData"]=xml;
             LC_MortgageApp.invoke_Async(params);
             }
 
             // Handles async call that invokes the long-lived process
             private function resultHandler(event:ResultEvent):void
             {
                ji = event.result as JobId;
                jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
             }
 
             private function createXML():XML
             {
                //Calculate the Mortgage value to place in the XML data
                var propertyPrice:String = txtAmount.text ;
                var name:String = txtName.text ;
                var phone:String = txtPhone.text ;;
 
                var model:XML =
 
                  <LoanApp>
                           <Name>{name}</Name>
                           <LoanAmount>{propertyPrice}</LoanAmount>
                           <PhoneOrEmail>{phone}</PhoneOrEmail>
                           <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
                  </LoanApp>
 
              return model;
             }
 
 
          ]]>
       </mx:Script>
 
       <!-- Declare the RemoteObject and set its destination to the mortgage-app remoting endpoint defined in AEM Forms. -->
       <mx:RemoteObject id="LC_MortgageApp" destination="FirstAppSolution/PreLoanProcess" result="resultHandler(event);">
          <mx:method name="invoke_Async" result="resultHandler(event)"/>
      </mx:RemoteObject>
 
 
     <mx:Grid x="229" y="186">
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Image>
                     <mx:source>file:///D|/LiveCycle_9/FirstApp/financeCorpLogo.jpg</mx:source>
                 </mx:Image>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Flex Loan Application Page" fontSize="20"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Name:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtName"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Button label="Submit Application" click="submitApplication()"/>
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Phone/Email:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtPhone"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Amount:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtAmount"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Label" id="jobStatusDisplay" enabled="true" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
     </mx:Grid>
 
 </mx:Application>
 
```
