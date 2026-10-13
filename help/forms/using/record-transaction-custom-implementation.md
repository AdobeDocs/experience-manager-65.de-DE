---
title: Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen
description: Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
feature: Transaction Reports
exl-id: b0c4f72a-e65f-453a-af66-5d9f98a9d6df
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: bcb3e79d-a57e-59a4-ad50-e03803c9f153
    internal-label: Transaction Reports
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 94%
---
# Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen für AEM Forms auf OSGi {#record-a-transaction-for-custom-implementations}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/using-communications/record-transaction-custom-implementation) |
| AEM 6.5 | Dieser Artikel |

Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden

Sie können einen benutzerdefinierten Code verwenden, um ein PDF-Formular abzusenden oder um die URL der Agenten-Benutzeroberflächen-Vorschau an Endbenutzer bzw. Endbenutzerinnen zu senden, um eine interaktive Kommunikation in der Vorschau anzuzeigen. Oder Sie senden ein Formular mit benutzerdefinierten Methoden ab, anstatt die mit AEM Forms bereitgestellten Übermittlungsmethoden zu verwenden. Alle oben genannten Aktionen und benutzerdefinierten Implementierungen von AEM Forms-APIs werden nicht als Transaktionen gezählt. AEM Forms stellt eine API namens [TransactionRecorder](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html) bereit, um Aktionen wie etwa Transaktionen aufzuzeichnen.

Um eine Transaktion aufzuzeichnen, schreiben Sie das [Standard-Sling-Servlet](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/store-and-retrieve-af-with-2fa/create-servlet.html?lang=de) und rufen das Servlet von einem Client aus auf, um eine Transaktion aufzuzeichnen. Sie können das Servlet mithilfe von AJAX oder einer anderen Standardmethode aufrufen.

## Beispiel für Server-seitigen Code {#sample-server-sided-code}

Sie können den folgenden Beispiel-Code verwenden, um die TransactionRecorder-API von einer Java™-Klasse aus mithilfe eines benutzerdefinierten OSGi-Pakets auszuführen.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;

doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## Beispiel für Client-seitigen Code {#sample-client-side-code}

Sie können den folgenden Beispiel-Code verwenden, um das Servlet aufzurufen, das die `TransactionRecorder`-API hat.

```javascript
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1,
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## Ähnliche Artikel {#related-articles}

* [Überblick über Transaktionsberichte für AEM Forms on OSGi](/help/forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten für AEM Forms on OSGi](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Abrechenbare APIs für Transaktionsberichte für AEM Forms on OSGi](/help/forms/using/transaction-reports-billable-apis.md)
