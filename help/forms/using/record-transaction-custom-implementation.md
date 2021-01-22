---
title: Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen
seo-title: Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen
description: Verwenden Sie die TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen bilanziert werden
seo-description: Verwenden Sie die TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen bilanziert werden
uuid: a22b1a0b-7553-4a17-8fb4-a3bee97b4a98
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 0d961630-573b-4c8e-902f-996f1d1265b6
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Eine Transaktion für benutzerdefinierte Implementierungen {#record-a-transaction-for-custom-implementations} aufzeichnen

Verwenden Sie die TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen bilanziert werden

Sie können einen benutzerspezifischen Code verwenden, um ein PDF-Formular zu senden, die URL der Benutzeroberfläche des Agenten an Endbenutzer zu senden, um eine interaktive Vorschau zu erstellen, oder um ein Formular mit benutzerdefinierten Methoden zu senden, anstatt die mit AEM Forms bereitgestellten Übermittlungsmethoden zu verwenden. Alle oben genannten Aktionen und benutzerdefinierten Implementierungen von AEM Forms APIs werden nicht als Transaktionen erfasst. AEM Forms stellt eine API bereit, [TransactionRecorder](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html), um Aktionen wie Transaktionen aufzuzeichnen.

Um eine Transaktion aufzuzeichnen, schreiben Sie das standardmäßige Sling-Servlet](https://helpx.adobe.com/experience-manager/using/custom-sling-servlets.html) und rufen Sie das Servlet von einem Client auf, um eine Transaktion aufzuzeichnen. [ Sie können das Servlet mit AJAX oder einer anderen Standardmethode aufrufen.

## Beispiel für serverseitigen Code {#sample-server-sided-code}

Sie können den folgenden Beispielcode verwenden, um die TransactionRecorder-API von einer JAVA-Klasse aus mit einem benutzerdefinierten OSGi-Bundle auszuführen.

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

## Beispiel für clientseitigen Code {#sample-client-side-code}

Sie können den folgenden Beispielcode verwenden, um das Servlet mit der API `TransactionRecorder`aufzurufen.

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

## Verwandte Artikel {#related-articles}

* [Übersicht über Transaktionsberichte](/help/forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Transaktionsberichte Abrechnungsfähige APIs](/help/forms/using/transaction-reports-billable-apis.md)

