---
title: Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen
seo-title: Record a transaction for custom implementations
description: Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden
seo-description: Use the TransactionRecorder API to record actions which are not accounted as transactions automatically
uuid: a22b1a0b-7553-4a17-8fb4-a3bee97b4a98
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 0d961630-573b-4c8e-902f-996f1d1265b6
exl-id: a1d97b15-14a6-4c3d-bdd3-6366f7acdfc8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen {#record-a-transaction-for-custom-implementations}

Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden

Anstatt die mit AEM Forms bereitgestellten Übermittlungsmethoden zu verwenden, können Sie auch einen benutzerdefinierten Code verwenden, um ein PDF-Formular zu übermitteln, um die Vorschau-URL der Benutzeroberfläche für Agenten an Endbenutzer zu senden, um eine interaktive Kommunikation in der Vorschau anzuzeigen, oder um ein Formular mithilfe benutzerdefinierter Methoden zu übermitteln. Alle oben genannten Aktionen und benutzerdefinierten Implementierungen von AEM Forms-APIs werden nicht als Transaktionen gezählt. AEM Forms stellt eine API namens [TransactionRecorder](https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html) bereit, um Aktionen wie etwa Transaktionen aufzuzeichnen.

Um eine Transaktion aufzuzeichnen, schreiben Sie das [Standard-Sling-Servlet](https://helpx.adobe.com/de/experience-manager/using/custom-sling-servlets.html) und rufen das Servlet von einem Client aus auf, um eine Transaktion aufzuzeichnen. Sie können das Servlet mithilfe von AJAX oder einer anderen Standardmethode aufrufen.

## Beispiel für Server-seitigen Code {#sample-server-sided-code}

Sie können den folgenden Beispiel-Code verwenden, um die TransactionRecorder-API von einer Java-Klasse aus mithilfe eines benutzerdefinierten OSGi-Bundles auszuführen.

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

* [Übersicht über Transaktionsberichte](/help/forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Abrechenbare APIs für Transaktionsberichte](/help/forms/using/transaction-reports-billable-apis.md)
