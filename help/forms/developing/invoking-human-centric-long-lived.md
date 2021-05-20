---
title: An Menschen orientierte langlebige Prozesse aufrufen
seo-title: An Menschen orientierte langlebige Prozesse aufrufen
description: Rufen Sie in Workbench erstellte, am Menschen orientierte langlebige Prozesse programmgesteuert auf. Verwenden Sie dazu eine webbasierte Java-Clientanwendung, die die Aufruf-API verwendet, eine ASP.NET-Anwendung, die Webdienste verwendet, und eine mit Flex erstellte Clientanwendung, die Remoting verwendet.
seo-description: Rufen Sie in Workbench erstellte, am Menschen orientierte langlebige Prozesse programmgesteuert auf. Verwenden Sie dazu eine webbasierte Java-Clientanwendung, die die Aufruf-API verwendet, eine ASP.NET-Anwendung, die Webdienste verwendet, und eine mit Flex erstellte Clientanwendung, die Remoting verwendet.
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
role: Developer
exl-id: c9ebad8b-b631-492d-99a3-094e892b2ddb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3739'
ht-degree: 4%

---

# An Menschen orientierte langlebige Prozesse aufrufen {#invoking-human-centric-long-lived-processes}

Sie können in Workbench erstellte, am Menschen orientierte langlebige Prozesse programmgesteuert aufrufen, indem Sie die folgenden Clientanwendungen verwenden:

* Eine webbasierte Java-Clientanwendung, die die Aufruf-API verwendet. (Siehe [AEM Forms mithilfe der Java-API aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)
* Eine ASP.NET-Anwendung, die Webdienste verwendet. (Siehe [AEM Forms mithilfe von Webdiensten aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Eine mit Flex erstellte Clientanwendung, die Remoting verwendet. (Siehe [Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Der langlebige Prozess, der aufgerufen wird, heißt *FirstAppSolution/PreLoanProcess*. Sie können diesen Prozess erstellen, indem Sie dem unter [Erstellen der ersten AEM Forms-Anwendung](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63) angegebenen Tutorial folgen.

Ein am Menschen orientierter Prozess umfasst eine Aufgabe, auf die ein Benutzer mithilfe von Workspace reagieren kann. Beispielsweise können Sie mit Workbench einen Prozess erstellen, mit dem ein Bankmanager einen Kreditantrag genehmigen oder ablehnen kann. Die folgende Abbildung zeigt den Prozess *FirstAppSolution/PreLoanProcess*.

Der Prozess *FirstAppSolution/PreLoanProcess* akzeptiert einen Eingabeparameter namens *formData*, dessen Datentyp XML ist. Die XML-Daten werden mit einem Formularentwurf namens *PreLoanForm.xdp* zusammengeführt. Die folgende Abbildung zeigt ein Formular, das eine Aufgabe darstellt, die einem Benutzer zugewiesen wurde, um einen Kreditantrag zu genehmigen oder abzulehnen. Der Benutzer genehmigt oder verweigert die Anwendung mithilfe von Workspace. Der Workspace-Benutzer kann den Kreditantrag genehmigen, indem er auf die in der folgenden Abbildung dargestellte Schaltfläche Genehmigen klickt. Ebenso kann der Benutzer die Kreditanfrage ablehnen, indem er auf die Schaltfläche &quot;Ablehnen&quot;klickt.

Ein langlebiger Prozess wird asynchron aufgerufen und kann aufgrund der folgenden Faktoren nicht synchron aufgerufen werden:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Ein Prozess benötigt eine externe Eingabe, damit er abgeschlossen werden kann. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Büro ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

Wenn ein langlebiger Prozess aufgerufen wird, erstellt AEM Forms beim Erstellen eines Datensatzes einen Wert für die Kennung des Aufrufs. Der Datensatz zeichnet den Status des langlebigen Prozesses auf und wird in der AEM Forms-Datenbank gespeichert. Mithilfe des Werts für die Kennung des Aufrufs können Sie den Status des langlebigen Prozesses verfolgen. Darüber hinaus können Sie den Wert für die Prozessaufruf-ID verwenden, um Process Manager-Vorgänge auszuführen, z. B. das Beenden einer laufenden Prozessinstanz.

>[!NOTE]
>
>AEM Forms erstellt beim Aufrufen eines kurzlebigen Prozesses keinen Aufrufkennungswert oder einen Datensatz.

Der Prozess `FirstAppSolution/PreLoanProcess` wird aufgerufen, wenn ein Antragsteller eine Anwendung sendet, die als XML-Daten dargestellt wird. Der Name der Eingabeprozessvariablen ist `formData` und der Datentyp ist XML. Angenommen, die folgenden XML-Daten werden als Eingabe für den `FirstAppSolution/PreLoanProcess`-Prozess verwendet.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <LoanApp>
 <Name>Sam White</Name>
 <LoanAmount>250000</LoanAmount>
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail>
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
 </LoanApp>
```

Die an einen Prozess übergebenen XML-Daten müssen mit den Feldern im Formular übereinstimmen, das im Prozess verwendet wird. Andernfalls werden keine Daten im Formular angezeigt. Alle Anwendungen, die den Prozess `FirstAppSolution/PreLoanProcess` aufrufen, müssen diese XML-Datenquelle übergeben. Die Anwendungen, die in *Aufrufen menschenzentrierter langlebiger Prozesse* erstellt wurden, erstellen die XML-Datenquelle dynamisch aus Werten, die ein Benutzer in einen Webclient eingegeben hat.

Mithilfe einer Clientanwendung können Sie die *FirstAppSolution/PreLoanProcess*-Verarbeitung der erforderlichen XML-Daten durchführen. Ein langlebiger Prozess gibt einen Aufruf-ID-Wert als Rückgabewert zurück. Die folgende Abbildung zeigt Clientanwendungen, die den langlebigen Prozess &quot;FirstAppSolution/PreLoanProcess&quot;aufrufen. Die Clientanwendungen senden XML-Daten und rufen einen Zeichenfolgenwert zurück, der den Wert der Aufruffunktion darstellt.

**Siehe auch**

[Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Erstellen einer ASP.NET-Webanwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Erstellen einer Clientanwendung, die mit Flex erstellt wurde und einen langlebigen, an Menschen orientierten Prozess aufruft](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

Sie können eine webbasierte Anwendung erstellen, die ein Java-Servlet verwendet, um den Prozess `FirstAppSolution/PreLoanProcess` aufzurufen. Um diesen Prozess über ein Java-Servlet aufzurufen, verwenden Sie die Aufruf-API im Java-Servlet. (Siehe [AEM Forms mithilfe der Java-API aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

Die folgende Abbildung zeigt eine webbasierte Client-Anwendung, die Werte für Name, Telefon (oder E-Mail) und Betrag veröffentlicht. Diese Werte werden an das Java-Servlet gesendet, wenn der Benutzer auf die Schaltfläche Anwendung übermitteln klickt.

Das Java-Servlet führt die folgenden Aufgaben aus:

* Ruft die Werte ab, die von der HTML-Seite an das Java-Servlet veröffentlicht werden.
* Dynamisches Erstellen einer XML-Datenquelle, die an den Prozess *FirstAppSolution/PreLoanProcess* übergeben wird. Die Werte für Name, Telefon (oder E-Mail) und Betrag werden in der XML-Datenquelle angegeben.
* Ruft den Prozess *FirstAppSolution/PreLoanProcess* mithilfe der AEM Forms Invocation API auf.
* Gibt den Wert der Kennung des Aufrufs an den Client-Webbrowser zurück.

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine webbasierte Java-Anwendung zu erstellen, die den `FirstAppSolution/PreLoanProcess`-Prozess aufruft, führen Sie die folgenden Schritte aus:

1. [Erstellen Sie ein Webprojekt](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Erstellen Sie eine Java-Anwendungslogik für das Servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [Webseite für die Webanwendung erstellen](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Verpacken Sie die Webanwendung in eine WAR-Datei](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Stellen Sie die WAR-Datei auf dem J2EE-Anwendungsserver bereit, der als Host für AEM Forms](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms) dient.
1. [Testen Sie Ihre Webanwendung](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Einige dieser Schritte hängen von der J2EE-Anwendung ab, auf der AEM Forms bereitgestellt wird. Die Methode zum Bereitstellen einer WAR-Datei hängt beispielsweise von dem verwendeten J2EE-Anwendungsserver ab. Es wird davon ausgegangen, dass AEM Forms auf JBoss® bereitgestellt wird.

### Webprojekt {#create-a-web-project} erstellen

Der erste Schritt zum Erstellen einer Webanwendung besteht darin, ein Webprojekt zu erstellen. Die Java-IDE, auf der dieses Dokument basiert, ist Eclipse 3.3. Erstellen Sie mit der Eclipse IDE ein Webprojekt und fügen Sie die erforderlichen JAR-Dateien zu Ihrem Projekt hinzu. Fügen Sie Ihrem Projekt eine HTML-Seite mit dem Namen *index.html* und ein Java-Servlet hinzu.

Die folgende Liste gibt die JAR-Dateien an, die in Ihr Webprojekt aufgenommen werden sollen:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Den Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>Die J2EE.jar-Datei definiert Datentypen, die von einem Java-Servlet verwendet werden. Sie können diese JAR-Datei vom J2EE-Anwendungsserver abrufen, auf dem AEM Forms bereitgestellt wird.

**Webprojekt erstellen**

1. Starten Sie Eclipse und klicken Sie auf **Datei** > **Neues Projekt**.
1. Wählen Sie im Dialogfeld **Neues Projekt** **Web** > **Dynamisches Webprojekt** aus.
1. Geben Sie `InvokePreLoanProcess` für den Namen Ihres Projekts ein und klicken Sie dann auf **Finish**.

**Hinzufügen erforderlicher JAR-Dateien zu Ihrem Projekt**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Eigenschaften** aus.
1. Klicken Sie auf **Java-Build-Pfad** und dann auf die Registerkarte **Bibliotheken** .
1. Klicken Sie auf die Schaltfläche **Externe JARs hinzufügen** und navigieren Sie zu den einzuschließenden JAR-Dateien.

**Hinzufügen eines Java-Servlets zu Ihrem Projekt**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Neu** > **Sonstige** aus.
1. Erweitern Sie den Ordner **Web**, wählen Sie **Servlet** und klicken Sie dann auf **Weiter**.
1. Geben Sie im Dialogfeld &quot;Servlet erstellen&quot;`SubmitXML` für den Namen des Servlets ein und klicken Sie dann auf **Finish**.

**HTML-Seite zu Ihrem Projekt hinzufügen**

1. Klicken Sie im Projekt-Explorer-Fenster mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Neu** > **Sonstige** aus.
1. Erweitern Sie den Ordner **Web**, wählen Sie **HTML** aus und klicken Sie auf **Weiter**.
1. Geben Sie im Dialogfeld &quot;New HTML&quot;den Dateinamen `index.html` ein und klicken Sie dann auf **Finish**.

>[!NOTE]
>
>Informationen zum Erstellen von HTML-Inhalten, die das SubmitXML Java-Servlet aufrufen, finden Sie unter [Erstellen der Webseite für die Webanwendung](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application).

### Erstellen Sie die Java-Anwendungslogik für das Servlet {#create-java-application-logic-for-the-servlet}

Erstellen Sie eine Java-Anwendungslogik, die den `FirstAppSolution/PreLoanProcess`-Prozess aus dem Java-Servlet heraus aufruft. Der folgende Code zeigt die Syntax des Java-Servlets `SubmitXML`:

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

Normalerweise würden Sie keinen Client-Code innerhalb der `doGet`- oder `doPost`-Methode eines Java-Servlets platzieren. Eine bessere Programmierpraxis besteht darin, diesen Code in einer separaten Klasse zu platzieren. Instanziieren Sie dann die Klasse aus der `doPost` -Methode (oder `doGet` -Methode) und rufen Sie die entsprechenden Methoden auf. Codebeispiele werden jedoch für eine kürzere Codeausführung auf ein Minimum beschränkt und in die `doPost` -Methode eingefügt.

Um den Prozess `FirstAppSolution/PreLoanProcess` mithilfe der Aufruf-API aufzurufen, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Client-JAR-Dateien wie adobe-livecycle-client.jar in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Rufen Sie die Werte für Name, Telefon und Betrag ab, die von der HTML-Seite gesendet werden. Verwenden Sie diese Werte, um dynamisch eine XML-Datenquelle zu erstellen, die an den `FirstAppSolution/PreLoanProcess`-Prozess gesendet wird. Sie können `org.w3c.dom`-Klassen verwenden, um die XML-Datenquelle zu erstellen (diese Anwendungslogik ist im folgenden Codebeispiel dargestellt).
1. Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Erstellen Sie ein `ServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Mit einem `ServiceClient` -Objekt können Sie einen Dienstvorgang aufrufen. Es erledigt Aufgaben wie das Auffinden, Versenden und Weiterleiten von Aufrufanforderungen.
1. Erstellen Sie ein Objekt `java.util.HashMap`, indem Sie den Konstruktor verwenden.
1. Rufen Sie die Methode `java.util.HashMap` des `put`-Objekts für jeden Eingabeparameter auf, der an den langlebigen Prozess übergeben erden soll. Stellen Sie sicher, dass Sie den Namen der Eingabeparameter des Prozesses angeben. Da der Prozess `FirstAppSolution/PreLoanProcess` einen Eingabeparameter vom Typ `XML` (namens `formData`) erfordert, müssen Sie die `put`-Methode nur einmal aufrufen.

   ```java
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
    
    //Create a Map object to store the parameter value
    Map params = new HashMap();
    params.put("formData", inXML);
   ```

1. Erstellen Sie ein `InvocationRequest` -Objekt, indem Sie die `createInvocationRequest` -Methode des Objekts `ServiceClientFactory` aufrufen und die folgenden Werte übergeben:

   * Ein string-Wert, der den Namen des langlebigen aufzurufenden Prozesses angibt. Um den Prozess `FirstAppSolution/PreLoanProcess` aufzurufen, geben Sie `FirstAppSolution/PreLoanProcess` an.
   * Ein string-Wert, der den Prozessvorgangsnamen darstellt. Der Name des langlebigen Prozessvorgangs ist `invoke`.
   * Das `java.util.HashMap`-Objekt, das die Parameterwerte enthält, die für den Dienstvorgang erforderlich sind.
   * Ein boolescher Wert, der `false` angibt, der eine asynchrone Anforderung erstellt (dieser Wert gilt für den Aufruf eines langlebigen Prozesses).

   >[!NOTE]
   >
   >*Ein kurzlebiger Prozess kann aufgerufen werden, indem der Wert true als vierter Parameter der Methode createInvocationRequest übergeben wird. Durch Übergabe des Werts true wird eine synchrone Anforderung erstellt.*

1. Senden Sie die Aufrufanforderung an AEM Forms, indem Sie die `invoke` -Methode des Objekts `ServiceClient` aufrufen und das `InvocationRequest` -Objekt übergeben. Die `invoke`-Methode gibt ein `InvocationReponse`-Objekt zurück.
1. Ein langlebiger Prozess gibt einen Zeichenfolgenwert zurück, der einen Aufruf-Identifizierungswert darstellt. Rufen Sie diesen Wert ab, indem Sie die `getInvocationId` -Methode des Objekts `InvocationReponse` aufrufen.

   ```java
    //Send the invocation request to the long-lived process and
    //get back an invocation response object
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
    String invocationId = lcResponse.getInvocationId();
   ```

1. Schreiben Sie den Aufrufkennungswert in den Client-Webbrowser. Sie können eine `java.io.PrintWriter`-Instanz verwenden, um diesen Wert in den Client-Webbrowser zu schreiben.

### Schnellstart: Aufrufen eines langlebigen Prozesses mithilfe der Aufruf-API {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

Das folgende Java-Codebeispiel stellt das Java-Servlet dar, das den Prozess `FirstAppSolution/PreLoanProcess` aufruft.

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

### Erstellen Sie die Webseite für die Webanwendung {#create-the-web-page-for-the-web-application} .

Die Webseite *index.html* bietet einen Einstiegspunkt zum Java-Servlet, das den `FirstAppSolution/PreLoanProcess`-Prozess aufruft. Diese Webseite ist ein einfaches HTML-Formular, das ein HTML-Formular und eine Senden-Schaltfläche enthält. Wenn der Benutzer auf die Senden-Schaltfläche klickt, werden die Formulardaten an das Java-Servlet `SubmitXML` gesendet.

Das Java-Servlet erfasst die Daten, die von der HTML-Seite veröffentlicht werden, mithilfe des folgenden Java-Codes:

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

### Verpacken Sie die Webanwendung in eine WAR-Datei {#package-the-web-application-to-a-war-file}

Um das Java-Servlet bereitzustellen, das den Prozess `FirstAppSolution/PreLoanProcess` aufruft, verpacken Sie Ihre Webanwendung in eine WAR-Datei. Stellen Sie sicher, dass externe JAR-Dateien, von denen die Geschäftslogik der Komponente abhängig ist, wie z. B. adobe-livecycle-client.jar und adobe-usermanager-client.jar, ebenfalls in der WAR-Datei enthalten sind.

Die folgende Abbildung zeigt den Inhalt des Eclipse-Projekts, das in eine WAR-Datei gepackt ist.

>[!NOTE]
>
>In der vorherigen Abbildung kann die JPG-Datei durch eine beliebige JPG-Bilddatei ersetzt werden.

**Verpacken Sie eine Webanwendung in eine WAR-Datei:**

1. Klicken Sie im Fenster **Projekt-Explorer** mit der rechten Maustaste auf das Projekt `InvokePreLoanProcess` und wählen Sie **Export** > **WAR-Datei** aus.
1. Geben Sie im Textfeld **Webmodul** `InvokePreLoanProcess` für den Namen des Java-Projekts ein.
1. Geben Sie im Textfeld **Ziel** `PreLoanProcess.war`**für den Dateinamen** den Speicherort für die WAR-Datei ein und klicken Sie auf &quot;Fertig stellen&quot;.

### Stellen Sie die WAR-Datei auf dem J2EE-Anwendungsserver bereit, der als Host für AEM Forms {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms} dient

Stellen Sie die WAR-Datei auf dem J2EE-Anwendungsserver bereit, auf dem AEM Forms bereitgestellt ist. Um die WAR-Datei auf dem J2EE-Anwendungsserver bereitzustellen, kopieren Sie die WAR-Datei aus dem Exportpfad in `[AEM Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy`.

>[!NOTE]
>
>Wenn AEM Forms nicht auf JBoss bereitgestellt wird, müssen Sie die WAR-Datei in Übereinstimmung mit dem J2EE-Anwendungsserver bereitstellen, der als Host für AEM Forms dient.

### Testen Sie Ihre Webanwendung {#test-your-web-application}

Nach der Bereitstellung der Webanwendung können Sie sie mithilfe eines Webbrowsers testen. Wenn Sie denselben Computer verwenden, auf dem AEM Forms gehostet wird, können Sie die folgende URL angeben:

* http://localhost:8080/PreLoanProcess/index.html

   Geben Sie Werte in die HTML-Formularfelder ein und klicken Sie auf die Schaltfläche Anwendung übermitteln . Wenn Probleme auftreten, lesen Sie die Protokolldatei des J2EE-Anwendungsservers.

>[!NOTE]
>
>Um zu bestätigen, dass die Java-Anwendung den Prozess aufgerufen hat, starten Sie Workspace und akzeptieren Sie das Darlehen.

## Erstellen einer ASP.NET-Webanwendung, die einen am Menschen orientierten langlebigen Prozess aufruft {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

Sie können eine ASP.NET-Anwendung erstellen, die den Prozess `FirstAppSolution/PreLoanProcess` aufruft. Verwenden Sie Webdienste, um diesen Prozess von einer ASP.NET-Anwendung aus aufzurufen. (Siehe [Aufrufen von AEM Forms mithilfe von Web Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

Die folgende Abbildung zeigt eine ASP.NET-Clientanwendung, die Daten von einem Endbenutzer abruft. Die Daten werden in eine XML-Datenquelle eingefügt und an den `FirstAppSolution/PreLoanProcess`-Prozess gesendet, wenn der Benutzer auf die Schaltfläche Anwendung übermitteln klickt.

Beachten Sie, dass nach dem Aufrufen des Prozesses ein Wert für die Kennung des Aufrufs angezeigt wird. Ein Wert für die Kennung des Aufrufs wird als Teil eines Datensatzes erstellt, der den Status des langlebigen Prozesses verfolgt.

Die ASP.NET-Anwendung führt die folgenden Aufgaben aus:

* Ruft die Werte ab, die der Benutzer auf der Webseite eingegeben hat.
* Dynamisches Erstellen einer XML-Datenquelle, die an den Prozess &quot;FirstAppSolution/PreLoanProcess&quot;übergeben wird. Die drei Werte werden in der XML-Datenquelle angegeben.
* Ruft den Prozess &quot;FirstAppSolution/PreLoanProcess&quot;mithilfe der Webdienste auf.
* Gibt den Wert der Aufruf-ID und den Status des langlebigen Vorgangs an den Client-Webbrowser zurück.

### Zusammenfassung der Schritte {#summary_of_steps-1}

So erstellen Sie eine ASP.NET-Anwendung, die den Prozess FirstAppSolution/PreLoanProcess aufrufen kann:

1. [Erstellen Sie eine ASP.NET-Webanwendung](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Erstellen Sie eine ASP-Seite, die FirstAppSolution/PreLoanProcess](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess) aufruft.
1. [Führen Sie die ASP.NET-Anwendung](invoking-human-centric-long-lived.md#run-the-asp-net-application) aus.

### Erstellen einer ASP.NET-Webanwendung {#create-an-asp-net-web-application}

Erstellen Sie eine Microsoft .NET C# ASP.NET-Webanwendung. Die folgende Abbildung zeigt den Inhalt des ASP.NET-Projekts *InvokePreLoanProcess*.

Beachten Sie unter Dienstverweise, dass es zwei Elemente gibt. Das erste Element heißt &quot;JobManager&quot;. Diese Referenz ermöglicht es der ASP.NET-Anwendung, den Job Manager-Dienst aufzurufen. Dieser Dienst gibt Informationen zum Status eines langlebigen Prozesses zurück. Wenn der Prozess beispielsweise gerade ausgeführt wird, gibt dieser Dienst einen numerischen Wert zurück, der angibt, dass der Prozess gerade ausgeführt wird. Die zweite Referenz heißt *PreLoanProcess*. Diese Dienstreferenz stellt die Referenz zum Prozess &quot;FirstAppSolution/PreLoanProcess&quot;dar. Nachdem Sie eine Dienstreferenz erstellt haben, sind mit dem AEM Forms-Dienst verknüpfte Datentypen für die Verwendung in Ihrem .NET-Projekt verfügbar.

**Erstellen eines ASP.NET-Projekts:**

1. Starten Sie Microsoft Visual Studio 2008.
1. Wählen Sie im Menü **Datei** **Neu**, **Website** aus.
1. Wählen Sie in der Liste **Vorlagen** die Option **ASP.NET-Website** aus.
1. Wählen Sie im Feld **Position** einen Speicherort für Ihr Projekt aus. Benennen Sie Ihr Projekt *InvokePreLoanProcess*.
1. Wählen Sie im Feld **Language** die Option Visual C# aus.
1. Klicken Sie auf OK.

**Hinzufügen von Dienstverweisen:**

1. Wählen Sie im Menü Projekt die Option **Dienstreferenz hinzufügen**.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den Job Manager-Dienst an.

   ```java
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Geben Sie in das Feld Namespace den Wert `JobManager` ein.
1. Klicken Sie auf **Gehen Sie zu** und klicken Sie dann auf **OK**.
1. Wählen Sie im Menü **Projekt** **Dienstreferenz hinzufügen** aus.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den Prozess FirstAppSolution/PreLoanProcess an.

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Geben Sie in das Feld Namespace den Wert `PreLoanProcess` ein.
1. Klicken Sie auf **Gehen Sie zu** und klicken Sie dann auf **OK**.

>[!NOTE]
>
>Ersetzen Sie `hiro-xp` durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient. Die Option `lc_version` stellt sicher, dass AEM Forms-Funktionen wie MTOM verfügbar sind. Ohne Angabe der Option `lc_version`können Sie AEM Forms nicht mit MTOM aufrufen. (Siehe [AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) aufrufen.)

### Erstellen Sie eine ASP-Seite, die FirstAppSolution/PreLoanProcess {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess} aufruft.

Fügen Sie innerhalb des ASP.NET-Projekts ein Webformular (eine ASPX-Datei) hinzu, das für die Anzeige einer HTML-Seite für den Kreditantrag zuständig ist. Das Webformular basiert auf einer Klasse, die von `System.Web.UI.Page` abgeleitet wird. Die C#-Anwendungslogik, die `FirstAppSolution/PreLoanProcess` aufruft, befindet sich in der `Button1_Click`-Methode (diese Schaltfläche stellt die Schaltfläche &quot;Anwendung übermitteln&quot;dar).

Die folgende Abbildung zeigt die ASP.NET-Anwendung

In der folgenden Tabelle sind die Steuerelemente aufgeführt, die Teil dieser ASP.NET-Anwendung sind.

<table>
 <thead>
  <tr>
   <th><p>Kontrollname</p></th>
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
   <td><p>Gibt die Telefon- oder E-Mail-Adresse des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>TextBoxAmount</p></td>
   <td><p>Gibt den Darlehensbetrag an.</p></td>
  </tr>
  <tr>
   <td><p>Button1</p></td>
   <td><p>Stellt die Schaltfläche Anwendung übermitteln dar.</p></td>
  </tr>
  <tr>
   <td><p>LabelJobID</p></td>
   <td><p>Ein Label-Steuerelement, das den Wert des Aufruffunktionskennungswerts angibt.</p></td>
  </tr>
  <tr>
   <td><p>LabelStatus</p></td>
   <td><p>Ein Label-Steuerelement, das den Wert des Auftragsstatus angibt. Dieser Wert wird durch Aufrufen des Job Manager-Dienstes abgerufen. </p></td>
  </tr>
 </tbody>
</table>

Die Anwendungslogik, die Teil der ASP.NET-Anwendung ist, muss dynamisch eine XML-Datenquelle erstellen, die an den `FirstAppSolution/PreLoanProcess`-Prozess übergeben wird. Die Werte, die der Antragsteller in die HTML-Seite eingegeben hat, müssen in der XML-Datenquelle angegeben werden. Diese Datenwerte werden beim Anzeigen des Formulars in Workspace mit dem Formular zusammengeführt. Die Klassen im Namespace `System.Xml` werden zum Erstellen der XML-Datenquelle verwendet.

Beim Aufrufen eines Prozesses, der XML-Daten aus einer ASP.NET-Anwendung erfordert, steht Ihnen ein XML-Datentyp zur Verfügung. Das heißt, Sie können eine `System.Xml.XmlDocument`-Instanz nicht an den Prozess übergeben. Der vollständig qualifizierte Name dieser XML-Instanz, die an den Prozess übergeben wird, lautet `InvokePreLoanProcess.PreLoanProcess.XML`. Konvertieren Sie die `System.Xml.XmlDocument`-Instanz in `InvokePreLoanProcess.PreLoanProcess.XML`. Sie können diese Aufgabe mithilfe des folgenden Codes ausführen.

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

1. Erstellen Sie ein `FirstAppSolution_PreLoanProcessClient` -Objekt mithilfe des Standardkonstruktors.
1. Erstellen Sie ein `FirstAppSolution_PreLoanProcessClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst und den Kodierungstyp angibt:

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie jedoch sicher, dass Sie `?blob=mtom` angeben.

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp`* durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient. *

1. Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` -Datenelements abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
1. Setzen Sie das `System.ServiceModel.BasicHttpBinding`-Datenelement des `MessageEncoding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
1. Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

   * Weisen Sie dem Datenelement `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName` den Benutzernamen der AEM Formulare zu.
   * Weisen Sie dem Datenelement `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
   * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` dem Datenelement `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Datenelement `BasicHttpBindingSecurity.Security.Mode` zu.

   Das folgende Codebeispiel zeigt diese Aufgaben.

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

1. Rufen Sie die Werte für Name, Telefon und Betrag ab, die der Benutzer auf der Webseite eingegeben hat. Verwenden Sie diese Werte, um dynamisch eine XML-Datenquelle zu erstellen, die an den `FirstAppSolution/PreLoanProcess`-Prozess gesendet wird. Erstellen Sie einen `System.Xml.XmlDocument` -Wert, der die XML-Datenquelle darstellt, die an den Prozess übergeben werden soll (diese Anwendungslogik wird im folgenden Codebeispiel gezeigt).
1. Konvertieren Sie die `System.Xml.XmlDocument`-Instanz in `InvokePreLoanProcess.PreLoanProcess.XML` (diese Anwendungslogik ist im folgenden Codebeispiel dargestellt).
1. Rufen Sie den Prozess `FirstAppSolution/PreLoanProcess` auf, indem Sie die `invoke_Async` -Methode des Objekts `FirstAppSolution_PreLoanProcessClient` aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Aufruffunktionskennungswert des langlebigen Prozesses darstellt.
1. Erstellen Sie einen `JobManagerClient` mithilfe des is-Konstruktors. (Stellen Sie sicher, dass Sie einen Dienstverweis auf den Job Manager-Dienst festgelegt haben.)
1. Wiederholen Sie die Schritte 1 bis 5. Geben Sie die folgende URL für Schritt 2 an: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Erstellen Sie ein Objekt `JobId`, indem Sie den Konstruktor verwenden.
1. Legen Sie das `JobId` -Datenelement des `id` -Objekts mit dem Rückgabewert der `FirstAppSolution_PreLoanProcessClient` -Methode des `invoke_Async` -Objekts fest.
1. Weisen Sie dem `persistent`-Datenelement des `JobId`-Objekts den Wert `value` &quot;true&quot;zu.
1. Erstellen Sie ein `JobStatus` -Objekt, indem Sie die `JobManagerService` -Methode des Objekts `getStatus` aufrufen und das `JobId` -Objekt übergeben.
1. Rufen Sie den Statuswert ab, indem Sie den Wert des `JobStatus` -Datenelements des Objekts `statusCode` abrufen.
1. Weisen Sie dem Feld `LabelJobID.Text` den Wert für die Aufruffunktion zu.
1. Weisen Sie den Statuswert dem Feld `LabelStatus.Text` zu.

### Schnellstart: Aufrufen eines langlebigen Prozesses mithilfe der Webdienst-API {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

Das folgende C#-Codebeispiel ruft den Prozess `FirstAppSolution/PreLoanProcess`auf.

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
>Die Werte in der benutzerdefinierten Methode getJobDescription entsprechen den vom Job Manager-Dienst zurückgegebenen Werten.

### Ausführen der ASP.NET-Anwendung {#run-the-asp-net-application}

Nachdem Sie die ASP.NET-Anwendung kompiliert und bereitgestellt haben, können Sie sie mithilfe eines Webbrowsers ausführen. Wenn der Name des ASP.NET-Projekts *InvokePreLoanProcess* lautet, geben Sie die folgende URL in einem Webbrowser an:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

wobei localhost der Name des Webservers ist, der das ASP.NET-Projekt hostet, und 1629 die Anschlussnummer. Wenn Sie die ASP.NET-Anwendung kompilieren und erstellen, stellt Microsoft Visual Studio sie automatisch bereit.

>[!NOTE]
>
>Um zu bestätigen, dass die ASP.NET-Anwendung den Prozess aufgerufen hat, starten Sie Workspace und akzeptieren Sie das Darlehen.

## Erstellen einer Clientanwendung, die mit Flex erstellt wurde und einen langlebigen, am Menschen orientierten Prozess {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process} aufruft

Sie können eine mit Flex erstellte Clientanwendung erstellen, um den Prozess *FirstAppSolution/PreLoanProcess* aufzurufen. Diese Anwendung verwendet Remoting, um den Prozess *FirstAppSolution/PreLoanProcess* aufzurufen. (Siehe [Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Die folgende Abbildung zeigt eine Clientanwendung, die mit Flex erstellt wurde und Daten von einem Endbenutzer erfasst. Die Daten werden in eine XML-Datenquelle eingefügt und an den Prozess gesendet.

Beachten Sie, dass nach dem Aufrufen des Prozesses ein Wert für die Kennung des Aufrufs angezeigt wird. Ein Wert für die Kennung des Aufrufs wird als Teil eines Datensatzes erstellt, der den Status des langlebigen Prozesses verfolgt.

Die mit Flex erstellte Clientanwendung führt die folgenden Aufgaben aus:

* Ruft die Werte ab, die der Benutzer auf der Webseite eingegeben hat.
* Dynamisches Erstellen einer XML-Datenquelle, die an den Prozess *FirstAppSolution/PreLoanProcess* übergeben wird. Die drei Werte werden in der XML-Datenquelle angegeben.
* Ruft den Prozess *FirstAppSolution/PreLoanProcess* mithilfe von Remoting auf.
* Gibt den Wert der Kennung des Aufrufs des langlebigen Prozesses zurück.

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um eine mit Flex erstellte Clientanwendung zu erstellen, die den FirstAppSolution/PreLoanProcess -Prozess aufrufen kann, führen Sie die folgenden Schritte aus:

1. Starten Sie ein neues Flex-Projekt.
1. Schließen Sie die Datei &quot;adobe-remoting-provider.swc&quot;in den Klassenpfad Ihres Projekts ein. (Siehe [Einschließen der AEM Forms Flex-Bibliotheksdatei](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Erstellen Sie eine `mx:RemoteObject`-Instanz entweder über ActionScript oder MXML. (Siehe [Erstellen einer mx:RemoteObject-Instanz](/help/forms/developing/invoking-aem-forms-using-remoting.md))
1. Richten Sie eine `ChannelSet`-Instanz ein, um mit AEM Forms zu kommunizieren, und verknüpfen Sie sie mit der `mx:RemoteObject`-Instanz. (Siehe [Erstellen eines Kanals zu AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Rufen Sie die `login`-Methode des ChannelSet oder die `setCredentials`-Methode des Diensts auf, um den Wert der Benutzer-ID und das Kennwort anzugeben. (Siehe [Single Sign-on](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Erstellen Sie die XML-Datenquelle, die an den `FirstAppSolution/PreLoanProcess`-Prozess übergeben wird, indem Sie eine XML-Instanz erstellen. (Diese Anwendungslogik wird im folgenden Codebeispiel gezeigt.)
1. Erstellen Sie ein Objekt des Typs &quot;Object&quot;mithilfe des zugehörigen Konstruktors. Weisen Sie dem Objekt die XML zu, indem Sie den Namen des Eingabeparameters des Prozesses angeben, wie im folgenden Code gezeigt:

   ```csharp
    //Get the XML data to pass to the AEM Forms process
    var xml:XML = createXML();
    var params:Object = new Object();
    params["formData"]=xml;
   ```

1. Rufen Sie den `FirstAppSolution/PreLoanProcess`-Prozess auf, indem Sie die `invoke_Async`-Methode der `mx:RemoteObject`-Instanz aufrufen. Übergeben Sie die `Object`, die den Eingabeparameter enthält. (Siehe [Übergeben von Eingabewerten](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Rufen Sie den Aufruf-Identifizierungswert ab, der von einem langlebigen Prozess zurückgegeben wird, wie im folgenden Code gezeigt:

   ```csharp
    // Handles async call that invokes the long-lived process
    private function resultHandler(event:ResultEvent):void
    {
    ji = event.result as JobId;
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
    }
   ```

### Aufrufen eines langlebigen Prozesses mit Remoting {#invoking-a-long-lived-process-using-remoting}

Das folgende Flex-Codebeispiel ruft den `FirstAppSolution/PreLoanProcess`-Prozess auf.

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
