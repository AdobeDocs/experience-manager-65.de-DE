---
title: Verwenden der Batch-API zum Generieren mehrerer interaktiver Kommunikationen
description: Verwenden der Batch-API zum Generieren mehrerer interaktiver Kommunikationen
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communication
feature: Interactive Communication
exl-id: f65d8eb9-4d2c-4a6e-825f-45bcfaa7ca75
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 066528bd9c2d7db9705a9d47ed6ea91a584129cb
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 100%

---

# Generieren mehrerer interaktiver Kommunikationen mithilfe der Batch-API {#use-batch-api-to-generate-multiple-ic}

Sie können die Batch-API verwenden, um mehrere interaktive Kommunikationen aus einer Vorlage zu erstellen. Die Vorlage ist eine interaktive Kommunikation ohne Daten. Die Batch-API kombiniert Daten mit einer Vorlage, um eine interaktive Kommunikation zu erzeugen. Die API ist bei der Massenproduktion interaktiver Kommunikationen nützlich. Zum Beispiel Telefonrechnungen, Kreditkartenauszüge für mehrere Kunden.

Die Batch-API akzeptiert Datensätze (Daten) im JSON-Format und aus einem Formulardatenmodell. Die Anzahl der erzeugten interaktiven Kommunikationen entspricht den Datensätzen, die in der JSON-Eingabedatei im konfigurierten Formulardatenmodell angegeben sind. Sie können die API verwenden, um sowohl Druck- als auch Web-Ausgaben zu erstellen. Die PRINT-Option erzeugt ein PDF-Dokument, und die WEB-Option erzeugt Daten im JSON-Format für jeden einzelnen Datensatz.

## Verwenden der Batch-API {#using-the-batch-api}

Sie können die Batch-API mit überwachten Ordnern oder als eigenständige REST-API verwenden. Sie konfigurieren eine Vorlage, einen Ausgabetyp (HTML, PRINT oder beides), ein Gebietsschema, einen Service zur Vorbefüllungs und einen Namen für die generierte interaktive Kommunikation, um die Batch-API zu verwenden.

Sie kombinieren einen Datensatz mit einer Vorlage für interaktive Kommunikation, um eine interaktive Kommunikation zu erzeugen. Batch-APIs können Datensätze (Daten für interaktive Kommunikationsvorlagen) direkt aus einer JSON-Datei oder aus einer externen Datenquelle lesen, auf die über das Formulardatenmodell zugegriffen wird. Sie können jeden Datensatz in einer separaten JSON-Datei speichern oder ein JSON-Array erstellen, um alle Datensätze in einer Datei zu speichern.

**Ein einzelner Datensatz in einer JSON-Datei**

```json
{
   "employee": {
       "name": "Sara",
       "id": 3,
       "mobileNo": 9871996463,
       "age": 37
   }
}
```

**Mehrere Datensätze in einer JSON-Datei**

```json
[{
   "employee": {
       "name": "John",
       "id": 1,
       "mobileNo": 9871996461,
       "age": 39
   }
},{
   "employee": {
       "name": "Jacob",
       "id": 2,
       "mobileNo": 9871996462,
       "age": 38
   }
},{
   "employee": {
       "name": "Sara",
       "id": 3,
       "mobileNo": 9871996463,
       "age": 37
   }
}]
```

### Verwenden der Batch-API mit überwachten Ordnern {#using-the-batch-api-watched-folders}

Um die Arbeit mit der API zu erleichtern, bietet AEM Forms einen Service für überwachte Ordner, der schon für die Verwendung der Batch-API vorkonfiguriert ist. Sie können über die Benutzeroberfläche von AEM Forms auf den Service zugreifen, um mehrere interaktive Kommunikationen zu generieren. Sie können auch benutzerdefinierte Services entsprechend Ihren Anforderungen erstellen. Sie können die unten aufgeführten Methoden verwenden, um die Batch-API mit dem überwachten Ordner zu verwenden:

* Geben Sie Eingabedaten (Datensätze) im JSON-Dateiformat an, um eine interaktive Kommunikation zu erstellen.
* Verwenden Sie Eingabedaten (Datensätze), die in einer externen Datenquelle gespeichert sind und über ein Formulardatenmodell aufgerufen werden, um eine interaktive Kommunikation zu erstellen.

#### Angeben von Datensätzen der Eingabedaten im JSON-Dateiformat, um eine interaktive Kommunikation zu erstellen {#specify-input-data-in-JSON-file-format}

Sie kombinieren einen Datensatz mit einer Vorlage für interaktive Kommunikation, um eine interaktive Kommunikation zu erzeugen. Sie können für jeden Datensatz eine separate JSON-Datei erstellen oder ein JSON-Array erstellen, um alle Datensätze in einer Datei zu speichern:

So erstellen Sie eine interaktive Kommunikation aus Datensätzen, die in einer JSON-Datei gespeichert sind:

1. Erstellen Sie einen [überwachten Ordner](/help/forms/using/creating-configure-watched-folder.md) und konfigurieren Sie ihn für die Verwendung der Batch-API:
   1. Melden Sie sich bei der AEM Forms-Autoreninstanz an.
   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Formulare]** > **[!UICONTROL Überwachten Ordner konfigurieren]**. Wählen Sie **[!UICONTROL Neu]** aus.
   1. Geben Sie die den **[!UICONTROL Namen]** und den physischen **[!UICONTROL Pfad]** des Ordners an. Beispiel: `c:\batchprocessing`.
   1. Wählen Sie die Option **[!UICONTROL Service]** im Feld **[!UICONTROL Datei verarbeiten mit]**.
   1. Wählen Sie den Service **[!UICONTROL com.adobe.fd.ccm.multichannel.batch.impl.service.InteractiveCommunicationBatchServiceImpl]** im Feld **[!UICONTROL Service-Name]**.
   1. Geben Sie ein **[!UICONTROL Ausgabedateimuster]** an. Beispiel: Das %F/ [Muster](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-watched-folder-endpoints.html?lang=de#about-file-patterns) gibt an, dass der überwachte Ordner Eingabedateien in einem Unterordner des Ordners „Watched Folder\input“ finden kann.
1. So konfigurieren Sie die erweiterten Parameter:
   1. Öffnen Sie die Registerkarte **[!UICONTROL Erweitert]** und fügen Sie die folgenden benutzerdefinierten Eigenschaften hinzu:

      | Eigenschaft | Typ | Beschreibung |
      |--- |--- |--- |
      | templatePath | Zeichenfolge | Geben Sie den Pfad der zu verwendenden interaktiven Kommunikationsvorlage an. Beispiel: `/content/dam/formsanddocuments/testsample/mediumic`. Dies ist eine obligatorische Eigenschaft. |
      | recordPath | Zeichenfolge | Der Wert des Felds recordPath hilft beim Festlegen des Namens einer interaktiven Kommunikation. Sie können den Pfad eines Datensatzfelds als Wert des Felds recordPath festlegen. Wenn Sie beispielsweise /employee/Id angeben, wird der Wert des ID-Felds zum Namen für die entsprechende interaktive Kommunikation. Der Standardwert ist eine [zufällige UUID](https://docs.oracle.com/javase/7/docs/api/java/util/UUID.html#randomUUID()). |
      | usePrefillService | Boolesch | Legen Sie den Wert auf „False“ fest. Sie können den Parameter usePrefillService verwenden, um die interaktive Kommunikation mit Daten vorzufüllen, die aus dem Vorbefüllungs-Service abgerufen wurden, der für die entsprechende interaktive Kommunikation konfiguriert ist. Wenn usePrefillService auf „true“ gesetzt ist, werden JSON-Eingabedaten (für jeden Datensatz) als FDM-Argumente behandelt. Der Standardwert lautet false. |
      | batchType | Zeichenfolge | Setzen Sie den Wert auf PRINT, WEB oder WEB_AND_PRINT. Der Standardwert ist WEB_AND_PRINT. |
      | locale | Zeichenfolge | Geben Sie das Gebietsschema für die Ausgabe der interaktiven Kommunikation an. Der vordefinierte Service verwendet nicht die Gebietsschema-Option, Sie können jedoch einen benutzerdefinierten Service erstellen, um lokalisierte interaktive Kommunikationen zu generieren. Der Standardwert ist en_US |

   1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Verwenden Sie den erstellten überwachten Ordner, um interaktive Kommunikation zu generieren:
   1. Öffnen Sie den überwachten Ordner. Navigieren Sie zum Eingabeordner. 
   1. Erstellen Sie einen Ordner im Eingabeordner und legen Sie die JSON-Datei im neu erstellten Ordner ab.
   1. Warten Sie, bis der überwachte Ordner die Datei verarbeitet hat. Wenn die Verarbeitung beginnt, werden die Eingabedatei und der Unterordner, die die Datei enthält, in den Staging-Ordner verschoben.
   1. Öffnen Sie den Ausgabeordner, um die Ausgabe anzuzeigen:
      * Wenn Sie in der Konfiguration des überwachten Ordners die PRINT-Option angeben, wird eine PDF-Ausgabe für die interaktive Kommunikation generiert.
      * Wenn Sie in der Konfiguration des überwachten Ordners die WEB-Option angeben, wird eine JSON-Datei pro Datensatz generiert. Sie können die JSON-Datei zum [Vorausfüllen einer Web-Vorlage](#web-template) verwenden.
      * Wenn Sie sowohl die PRINT- als auch die WEB-Option angeben, werden sowohl PDF-Dokumente als auch eine JSON-Datei pro Datensatz generiert.

#### Verwenden Sie Eingabedaten, die in einer externen Datenquelle gespeichert sind und über das Formulardatenmodell aufgerufen werden, um eine interaktive Kommunikation zu erstellen. {#use-fdm-as-data-source}

Sie kombinieren in einer externen Datenquelle gespeicherte Daten (Datensätze) mit einer interaktiven Kommunikationsvorlage, um eine interaktive Kommunikation zu erzeugen. Wenn Sie eine interaktive Kommunikation erstellen, verbinden Sie sie über ein Formulardatenmodell (FDM) mit einer externen Datenquelle, um auf Daten zuzugreifen. Sie können den Batch-Prozess-Service für überwachte Ordner konfigurieren, um Daten mit demselben Formulardatenmodell aus einer externen Datenquelle abzurufen. So [Erstellen Sie eine interaktive Kommunikation aus Datensätzen, die in einer externen Datenquelle gespeichert sind](/help/forms/using/work-with-form-data-model.md):

1. So konfigurieren Sie das Formulardatenmodell der Vorlage:
   1. Öffnen Sie das Formulardatenmodell, das mit der Vorlage für interaktive Kommunikation verknüpft ist.
   1. Wählen Sie Ihr MODELLOBJEKT DER OBERSTEN EBENE aus und wählen Sie „Eigenschaften bearbeiten“ aus.
   1. Wählen Sie Ihren Service zum Abrufen aus dem Feld „Lese-Service“ im Bereich „Eigenschaften bearbeiten“ aus.
   1. Wählen Sie das Stiftsymbol für das Argument des Lese-Service aus, um das Argument an ein Anfrageattribut zu binden, und geben Sie den Bindungswert an. Er bindet das Dienstargument an das angegebene Bindungsattribut oder den angegebenen Literalwert, der an den Dienst als Argument übergeben wird, um mit dem angegebenen Wert verknüpfte Details aus der Datenquelle abzurufen.

      In diesem Beispiel nimmt das ID-Argument den Wert des ID-Attributs des Benutzerprofils an und übergibt ihn als Argument an den Lesedienst. Dieser liest Werte aus zugeordneten Eigenschaften aus dem Datenmodellobjekt „employee“ für die angegebene ID und gibt sie zurück. Wenn Sie beispielsweise im ID-Feld im Formular den Wert „00250“ festlegen, liest der Lesedienst die Informationen zu der Person mit der Mitarbeiter-ID „00250“.

      ![Konfigurieren des Anfrageattributs](assets/request-attribute.png)

   1. Speichern Sie die Eigenschaften und das Formulardatenmodell.
1. So konfigurieren Sie den Wert für das Anfrageattribut:
   1. Erstellen Sie eine JSON-Datei in Ihrem Dateisystem und öffnen Sie sie zur Bearbeitung.
   1. Erstellen Sie ein JSON-Array und geben Sie das primäre Attribut an, um Daten aus dem Formulardatenmodell abzurufen. Beispielsweise fordert die folgende JSON-Datei FDM auf, Daten von Datensätzen mit einer ID von 27126 oder 27127 zu senden:

      ```json
          [
              {
                  "id": 27126
              },
              {
                  "id": 27127
              }
          ]
      ```

   1. Speichern und schließen Sie die Datei.

1. Erstellen Sie einen [überwachten Ordner](/help/forms/using/creating-configure-watched-folder.md) und konfigurieren Sie ihn für die Verwendung des Batch-API-Services:
   1. Melden Sie sich bei der AEM Forms-Autoreninstanz an.
   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Formulare]** > **[!UICONTROL Überwachten Ordner konfigurieren]**. Wählen Sie **[!UICONTROL Neu]** aus.
   1. Geben Sie die den **[!UICONTROL Namen]** und den physischen **[!UICONTROL Pfad]** des Ordners an. Beispiel: `c:\batchprocessing`.
   1. Wählen Sie die Option **[!UICONTROL Service]** im Feld **[!UICONTROL Datei verarbeiten mit]**.
   1. Wählen Sie den Service **[!UICONTROL com.adobe.fd.ccm.multichannel.batch.impl.service.InteractiveCommunicationBatchServiceImpl]** im Feld **[!UICONTROL Service-Name]**.
   1. Geben Sie ein **[!UICONTROL Ausgabedateimuster]** an. Beispiel: Das %F/ [Muster](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-watched-folder-endpoints.html?lang=de#about-file-patterns) gibt an, dass der überwachte Ordner Eingabedateien in einem Unterordner des Ordners „Watched Folder\input“ finden kann.
1. So konfigurieren Sie die erweiterten Parameter:
   1. Öffnen Sie die Registerkarte **[!UICONTROL Erweitert]** und fügen Sie die folgenden benutzerdefinierten Eigenschaften hinzu:

      | Eigenschaft | Typ | Beschreibung |
      |--- |--- |--- |
      | templatePath | Zeichenfolge | Geben Sie den Pfad der zu verwendenden interaktiven Kommunikationsvorlage an. Beispiel: /content/dam/formsanddocuments/testsample/mediumic. Dies ist eine obligatorische Eigenschaft. |
      | recordPath | Zeichenfolge | Der Wert des Felds recordPath hilft beim Festlegen des Namens einer interaktiven Kommunikation. Sie können den Pfad eines Datensatzfelds als Wert des Felds recordPath festlegen. Wenn Sie beispielsweise /employee/Id angeben, wird der Wert des ID-Felds zum Namen für die entsprechende interaktive Kommunikation. Der Standardwert ist eine [zufällige UUID](https://docs.oracle.com/javase/7/docs/api/java/util/UUID.html#randomUUID()). |  |
      | usePrefillService | Boolesch | Legen Sie den Wert auf „True“ fest. Der Standardwert lautet „false“. Wenn der Wert auf „true“ gesetzt ist, liest die Batch-API Daten aus dem konfigurierten Formulardatenmodell und füllt sie in die interaktive Kommunikation. Wenn usePrefillService auf „true“ gesetzt ist, werden JSON-Eingabedaten (für jeden Datensatz) als FDM-Argumente behandelt. |
      | batchType | Zeichenfolge | Setzen Sie den Wert auf PRINT, WEB oder WEB_AND_PRINT. Der Standardwert ist WEB_AND_PRINT. |
      | locale | Zeichenfolge | Geben Sie das Gebietsschema für die Ausgabe der interaktiven Kommunikation an. Der vordefinierte Service verwendet nicht die Gebietsschema-Option, Sie können jedoch einen benutzerdefinierten Service erstellen, um lokalisierte interaktive Kommunikationen zu generieren. Der Standardwert ist en_US. |

   1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Verwenden Sie den erstellten überwachten Ordner, um interaktive Kommunikation zu generieren:
   1. Öffnen Sie den überwachten Ordner. Navigieren Sie zum Eingabeordner. 
   1. Erstellen Sie einen Ordner im Eingabeordner. Platzieren Sie die in Schritt 2 erstellte JSON-Datei im neu erstellten Ordner.
   1. Warten Sie, bis der überwachte Ordner die Datei verarbeitet hat. Wenn die Verarbeitung beginnt, werden die Eingabedatei und der Unterordner, die die Datei enthält, in den Staging-Ordner verschoben.
   1. Öffnen Sie den Ausgabeordner, um die Ausgabe anzuzeigen:
      * Wenn Sie in der Konfiguration des überwachten Ordners die PRINT-Option angeben, wird eine PDF-Ausgabe für die interaktive Kommunikation generiert.
      * Wenn Sie in der Konfiguration des überwachten Ordners die WEB-Option angeben, wird eine JSON-Datei pro Datensatz generiert. Sie können die JSON-Datei zum [Vorausfüllen einer Web-Vorlage](#web-template) verwenden.
      * Wenn Sie sowohl die PRINT- als auch die WEB-Option angeben, werden sowohl PDF-Dokumente als auch eine JSON-Datei pro Datensatz generiert.

## Rufen Sie die Batch-API mithilfe von REST-Anfragen auf.

Sie können [die Batch-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javadocs/index.html) durch REST-Anfragen (Representational State Transfer) aufrufen. Damit können Sie anderen Benutzenden einen REST-Endpunkt bereitstellen, um auf die API zuzugreifen und Ihre eigenen Methoden zur Verarbeitung, Speicherung und Anpassung der interaktiven Kommunikation zu konfigurieren. Sie können Ihr eigenes benutzerdefiniertes Java™-Servlet entwickeln, um die API auf Ihrer AEM-Instanz bereitzustellen.

Stellen Sie vor der Bereitstellung des Java™-Servlets sicher, dass Sie über eine interaktive Kommunikation und entsprechende Datendateien verfügen. Führen Sie die folgenden Schritte aus, um das Java™-Servlet zu erstellen und bereitzustellen:

1. Melden Sie sich bei Ihrer AEM-Instanz an und erstellen Sie eine interaktive Kommunikation. Um die interaktive Kommunikation zu verwenden, die im folgenden Beispielcode erwähnt wird, [hier klicken](assets/SimpleMediumIC.zip).
1. [Erstellen Sie ein AEM-Projekt und stellen Sie es mit Apache Maven auf Ihrer AEM-Instanz bereit](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/aem-project-archetype.html?lang=de).
1. Fügen Sie [AEM Forms Client SDK Version 6.0.12 oder später](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) in der Abhängigkeitsliste der POM-Datei Ihres AEM-Projekts hinzu. Beispiel:

   ```xml
       <dependency>
           <groupId>com.adobe.aemfd</groupId>
           <artifactId>aemfd-client-sdk</artifactId>
           <version>6.0.122</version>
       </dependency>
   ```

1. Öffnen Sie das Java™-Projekt und erstellen Sie eine .java-Datei, z. B. „CCMBatchServlet.java“. Fügen Sie der Datei den folgenden Code hinzu:

   ```java
           package com.adobe.fd.ccm.multichannel.batch.integration;
   
           import java.io.File;
           import java.io.FileInputStream;
           import java.io.FileOutputStream;
           import java.io.IOException;
           import java.io.InputStream;
           import java.io.PrintWriter;
           import java.util.List;
           import javax.servlet.Servlet;
           import org.apache.commons.io.IOUtils;
           import org.apache.sling.api.SlingHttpServletRequest;
           import org.apache.sling.api.SlingHttpServletResponse;
           import org.apache.sling.api.servlets.SlingAllMethodsServlet;
           import org.json.JSONArray;
           import org.json.JSONObject;
           import org.osgi.service.component.annotations.Component;
           import org.osgi.service.component.annotations.Reference;
   
           import com.adobe.fd.ccm.multichannel.batch.api.builder.BatchConfigBuilder;
           import com.adobe.fd.ccm.multichannel.batch.api.factory.BatchComponentBuilderFactory;
           import com.adobe.fd.ccm.multichannel.batch.api.model.BatchConfig;
           import com.adobe.fd.ccm.multichannel.batch.api.model.BatchInput;
           import com.adobe.fd.ccm.multichannel.batch.api.model.BatchResult;
           import com.adobe.fd.ccm.multichannel.batch.api.model.BatchType;
           import com.adobe.fd.ccm.multichannel.batch.api.model.RecordResult;
           import com.adobe.fd.ccm.multichannel.batch.api.model.RenditionResult;
           import com.adobe.fd.ccm.multichannel.batch.api.service.BatchGeneratorService;
           import com.adobe.fd.ccm.multichannel.batch.util.BatchConstants;
           import java.util.Date;
   
   
           @Component(service=Servlet.class,
           property={
                   "sling.servlet.methods=GET",
                   "sling.servlet.paths="+ "/bin/batchServlet"
           })
           public class CCMBatchServlet extends SlingAllMethodsServlet {
   
               @Reference
               private BatchGeneratorService batchGeneratorService;
               @Reference
               private BatchComponentBuilderFactory batchBuilderFactory;
               public void doGet(SlingHttpServletRequest req, SlingHttpServletResponse resp) {
                   try {
                       executeBatch(req,resp);
                   } catch (Exception e) {
                       e.printStackTrace();
                   }
               }
               private void executeBatch(SlingHttpServletRequest req, SlingHttpServletResponse resp) throws Exception {
                   int count = 0;
                   JSONArray inputJSONArray = new JSONArray();
                   String filePath = req.getParameter("filePath");
                   InputStream is = new FileInputStream(filePath);
                   String data = IOUtils.toString(is);
                   try {
                       // If input file is json object, then create json object and add in json array, if not then try for json array
                       JSONObject inputJSON = new JSONObject(data);
                       inputJSONArray.put(inputJSON);
                   } catch (Exception e) {
                       try {
                           // If input file is json array, then iterate and add all objects into inputJsonArray otherwise throw exception
                           JSONArray inputArray = new JSONArray(data);
                           for(int i=0;i<inputArray.length();i++) {
                               inputJSONArray.put(inputArray.getJSONObject(i));
                           }
                       } catch (Exception ex) {
                           throw new Exception("Invalid JSON Data. File name : " + filePath, ex);
                       }
                   }
                   BatchInput batchInput = batchBuilderFactory.getBatchInputBuilder().setData(inputJSONArray).setTemplatePath("/content/dam/formsanddocuments/[path of the interactive communcation]").build();
                   BatchConfig batchConfig = batchBuilderFactory.getBatchConfigBuilder().setBatchType(BatchType.WEB_AND_PRINT).build();
                   BatchResult batchResult = batchGeneratorService.generateBatch(batchInput, batchConfig);
                   List<RecordResult> recordList = batchResult.getRecordResults();
                   JSONObject result = new JSONObject();
                   for (RecordResult recordResult : recordList) {
                       String recordId = recordResult.getRecordID();
                       for (RenditionResult renditionResult : recordResult.getRenditionResults()) {
                           if (renditionResult.isRecordPassed()) {
                               InputStream output = renditionResult.getDocumentStream().getInputStream();
                               result.put(recordId +"_"+renditionResult.getContentType(), output);
   
                               Date date= new Date();
                               long time = date.getTime();
   
                               // Print output
                               if(getFileExtension(renditionResult.getContentType()).equalsIgnoreCase(".json")) {
                                   File file = new File(time + getFileExtension(renditionResult.getContentType()));
                                   copyInputStreamToFile(output, file);
                               } else
                               {
                                   File file = new File(time + getFileExtension(renditionResult.getContentType()));
                                   copyInputStreamToFile(output, file);
                               }
                           }
                       }
                   }
                   PrintWriter writer = resp.getWriter();
                   JSONObject resultObj = new JSONObject();
                   resultObj.put("result", result);
                   writer.write(resultObj.toString());
               }
   
   
               private static void copyInputStreamToFile(InputStream inputStream, File file)
                       throws IOException {
   
                       try (FileOutputStream outputStream = new FileOutputStream(file)) {
   
                           int read;
                           byte[] bytes = new byte[1024];
   
                           while ((read = inputStream.read(bytes)) != -1) {
                               outputStream.write(bytes, 0, read);
                           }
   
                       }
   
                   }
   
   
               private String getFileExtension(String contentType) {
                   if (contentType.endsWith(BatchConstants.JSON)) {
                       return ".json";
                   } else return ".pdf";
               }
   
   
           }
   ```

1. Ersetzen Sie im obigen Code den Vorlagenpfad (setTemplatePath) durch den Pfad Ihrer Vorlage und legen Sie den Wert der setBatchType-API fest:
   * Wenn Sie die PRINT-Option PDF angeben, wird eine Ausgabe für die interaktive Kommunikation generiert.
   * Wenn Sie die WEB-Option angeben, wird eine JSON-Datei pro Eintrag generiert. Sie können die JSON-Datei zum [Vorausfüllen einer Web-Vorlage](#web-template) verwenden.
   * Wenn Sie sowohl die PRINT- als auch die WEB-Option angeben, werden sowohl PDF-Dokumente als auch eine JSON-Datei pro Datensatz generiert.

1. [Verwenden Sie Maven, um den aktualisierten Code für Ihre AEM-Instanz bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/aem-project-archetype.html?lang=de).
1. Rufen Sie zum Generieren der interaktiven Kommunikationen die Batch-API auf.  Die Batch-API druckt und gibt einen Stream von PDF- und JSON-Dateien abhängig von der Anzahl der Datensätze zurück. Sie können die JSON-Datei zum [Vorausfüllen einer Web-Vorlage](#web-template) verwenden. Wenn Sie den oben genannten Code verwenden, wird die API unter `http://localhost:4502/bin/batchServlet` bereitgestellt. Der Code druckt und gibt einen Stream von PDF- und JSON-Dateien zurück.

### Vorausfüllen einer Web-Vorlage {#web-template}

Wenn Sie den batchType so einstellen, dass der Web-Kanal gerendert wird, generiert die API eine JSON-Datei für jeden Datensatz. Sie können die folgende Syntax verwenden, um die JSON-Datei mit dem entsprechenden Web-Kanal zusammenzuführen und eine interaktive Kommunikation zu generieren:

**Syntax**
`http://host:port/<template-path>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=<guide-merged-json-path>`

**Beispiel**
Wenn sich Ihre JSON-Datei unter `C:\batch\mergedJsonPath.json` befindet und Sie die folgende interaktive Kommunikationsvorlage verwenden: `http://host:port/content/dam/formsanddocuments/testsample/mediumic/jcr:content?channel=web`

Anschließend zeigt die folgende URL auf dem Veröffentlichungsknoten den Web-Kanal der interaktiven Kommunikation an
`http://host:port/<path-to-ic>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=file:///C:/batch/mergedJsonData.json`

Sie speichern nicht nur die Daten im Dateisystem, sondern auch JSON-Dateien im CRX-Repository, Dateisystem oder Webserver oder können über den OSGi-Vorbefüllungs-Service auf Daten zugreifen. Syntax zum Zusammenführen von Daten mithilfe verschiedener Protokolle:

* **CRX-Protokoll**
  `http://host:port/<path-to-ic>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=crx:///tmp/fd/af/mergedJsonData.json`

* **Dateiprotokoll**
  `http://host:port/<path-to-ic>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=file:///C:/Users/af/mergedJsonData.json`

* **Vorbefüllungs-Service-Protokoll**
  `http://host:port/<path-to-ic>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=service://[SERVICE_NAME]/[IDENTIFIER]`

  SERVICE_NAME verweist auf den Namen des OSGI-Vorbefüllungs-Service. Lesen Sie Erstellen und Ausführen eines Vorbefüllungs-Service.

  IDENTIFIER bezieht sich auf alle Metadaten, die vom OSGI-Vorbefüllungs-Service erforderlich sind, um die Daten zum Vorbefüllen aufzurufen. Eine Kennung für die angemeldete Benutzerin bzw. den angemeldeten Benutzer ist ein Beispiel für Metadaten, die verwendet werden können.

* **HTTP-Protokoll**
  `http://host:port/<path-to-ic>/jcr:content?channel=web&mode=preview&guideMergedJsonPath=http://localhost:8000/somesamplexmlfile.xml`

>[!NOTE]
>
>Standardmäßig ist nur das CRX-Protokoll aktiviert. Informationen zum Aktivieren anderer unterstützter Protokolle finden Sie unter [Konfigurieren des Vorbefüllungs-Services mit Configuration Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/adaptive-forms-advanced-authoring/prepopulate-adaptive-form-fields.html?lang=de).
