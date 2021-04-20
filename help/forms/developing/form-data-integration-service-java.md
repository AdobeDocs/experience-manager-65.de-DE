---
title: JavaAPI Quick Beginn (SOAP) des Formulardatenintegrationsdienstes
seo-title: JavaAPI Quick Beginn (SOAP) des Formulardatenintegrationsdienstes
description: Verwenden Sie den Forms Data Integration-Dienst, um Daten in ein PDF-Formular zu importieren und Daten aus einem PDF-Formular mithilfe der Java-API zu exportieren.
seo-description: Verwenden Sie den Forms Data Integration-Dienst, um Daten in ein PDF-Formular zu importieren und Daten aus einem PDF-Formular mithilfe der Java-API zu exportieren.
uuid: bde8e83d-56d3-4331-a025-82b327c219b7
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 91b738ec-aa00-4f05-bf42-2574ced8d993
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Formulardatenintegrationsdienst Java API Quick Beginn (SOAP) {#form-data-integration-service-javaapi-quick-start-soap}

Die folgenden Quick-Beginn sind für den Formulardatenintegrationsdienst verfügbar.

[Quick Beginn (SOAP-Modus): Formulardaten mit der Java-API importieren](form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Quick Beginn (SOAP-Modus): Exportieren von Formulardaten mit der Java-API](form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms API ausgeführt werden, und der Verbindungsmodus sollte auf SOAP eingestellt sein.

>[!NOTE]
>
>Quick Beginn unter Programmieren mit AEM Formularen basieren auf dem Forms-Server, der auf JBoss Application Server und dem Microsoft Windows-Betriebssystem bereitgestellt wird. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungsserver verwenden, stellen Sie sicher, dass Sie gültige Verbindungseigenschaften angeben. Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Quick Beginn (SOAP-Modus): Formulardaten mit der Java-API {#quick-start-soap-mode-importing-form-data-using-the-java-api} importieren

Im folgenden Java-Codebeispiel werden Daten in ein PDF-Formular importiert. Die Daten befinden sich in einer XML-Datei mit dem Namen *Loan_data.xml* und das PDF-Formular wird als PDF-Datei mit dem Namen *ResultLoanForm.pdf* gespeichert. (Siehe [Formulardaten importieren](/help/forms/developing/importing-exporting-data.md#importing-form-data).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-formdataintegration-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is located in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is located in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are located in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote forms server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 import java.io.File;
 import java.io.FileInputStream;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.formdataintegration.client.*;
 
 public class ImportDataSOAP {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
              //Create a ServiceClientFactory object
              ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a FormDataIntegrationClient object
             FormDataIntegrationClient dataClient = new FormDataIntegrationClient(myFactory);
 
             //Import XDP XML data into an XFA PDF document
             //Reference an XFA PDF form
             FileInputStream inputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inputPDF = new Document(inputStream);
 
             FileInputStream dataInput = new FileInputStream("C:\\Adobe\Loan_data.xml");
             Document inputDataFile = new Document(dataInput);
 
             //Import data into the form
             Document resultPDF = dataClient.importData(inputPDF,inputDataFile);
 
             //Save the PDF file
             File resultFile = new File("C:\\Adobe\ResultLoanForm.pdf");
             resultPDF.copyToFile(resultFile);
 
         }catch (Exception e) {
              e.printStackTrace();
         }
       }
     }
 
```

## Quick Beginn (SOAP-Modus): Exportieren von Formulardaten mit der Java-API {#quick-start-soap-mode-exporting-form-data-using-the-java-api}

Im folgenden Java-Codebeispiel werden Daten aus einem PDF-Formular exportiert. Die Formulardaten werden als XML-Datei mit dem Namen *Loan_data.xml* gespeichert. (Siehe [Exportieren von Formulardaten](/help/forms/developing/importing-exporting-data.md#exporting-form-data).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-formdataintegration-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is located in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is located in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are located in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote forms server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 import java.io.File;
 import java.io.FileInputStream;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.formdataintegration.client.*;
 
 public class ExportDataSOAP {
 
     public static void main(String[] args) {
 
     try{
         //Set connection properties required to invoke AEM Forms using SOAP mode
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
          //Create a ServiceClientFactory object
          ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
          //Create a FormDataIntegrationClient object
          FormDataIntegrationClient dataClient = new FormDataIntegrationClient(myFactory);
 
          //Reference a PDF form from which to export data
          FileInputStream fileInputStream2 = new FileInputStream("C:\\Adobe\LoanForm.pdf");
          Document inputPDF = new Document(fileInputStream2);
 
          //Export data from the form
          Document resultPDF = dataClient.exportData(inputPDF);
 
          //Save the exported form data as an XML file
          File resultFile = new File("C:\\Adobe\Loan_data.xml");
          resultPDF.copyToFile(resultFile);
 
     }catch (Exception e) {
              e.printStackTrace();
         }
     }
 }
```

