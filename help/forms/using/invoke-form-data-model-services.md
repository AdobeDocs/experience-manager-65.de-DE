---
title: API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen
seo-title: API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen
description: Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Webdienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden.
seo-description: Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Webdienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 35%

---


# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Übersicht {#overview}

AEM Forms ermöglicht es Formularautoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem sie Dienste, die in einem Formulardatenmodell konfiguriert sind, aus einem adaptiven Formularfeld heraus aufrufen. To invoke a data model service, you can either create a rule in the visual editor or specify a JavaScript using the `guidelib.dataIntegrationUtils.executeOperation` API in the code editor of the [rule editor](/help/forms/using/rule-editor.md).

In diesem Dokument wird das Schreiben von JavaScript im API`guidelib.dataIntegrationUtils.executeOperation` für den Aufruf eines Dienst beschrieben.

## Verwenden der API {#using-the-api}

The `guidelib.dataIntegrationUtils.executeOperation` API invokes a service from within an adaptive form field. Für die API gilt die folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

The structure of the `guidelib.dataIntegrationUtils.executeOperation` API specifies details about the service operation. Die Struktur weist die folgende Syntax auf.

```javascript
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

Die API-Struktur gibt die folgenden Informationen zum Webdienst-Vorgang an.

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>operationInfo</code></td>
   <td>Struktur zur Angabe von Formulardatenmodellkennung, Operationstitel und Operationsname</td>
  </tr>
  <tr>
   <td><code>formDataModelId</code></td>
   <td>Gibt den Repository-Pfad zum Formulardatenmodell einschließlich seines Namens an</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Gibt den Namen des auszuführenden Dienstvorgangs an</td>
  </tr>
  <tr>
   <td><code>inputs</code></td>
   <td>Ordnet ein oder mehrere Formularobjekte den Eingabeargumenten für den Dienstvorgang zu</td>
  </tr>
  <tr>
   <td><code>Outputs</code></td>
   <td>Maps one or more form objects to output values from the service operation to populate form fields<br /> </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Gibt Werte basierend auf den Eingabeargumenten für den Dienstvorgang zurück. Es handelt sich um einen optionalen Parameter, der als Rückruffunktion verwendet wird.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Zeigt eine Fehlermeldung an, wenn die Rückruffunktion success die Ausgabenwerte basierend auf den Eingabeargumenten nicht anzeigen kann. Es handelt sich um einen optionalen Parameter, der als Rückruffunktion verwendet wird.<br /> </td>
  </tr>
 </tbody>
</table>

## Beispielskript zum Erstellen eines Dienstes {#sample-script-to-invoke-a-service}

The following sample script uses the `guidelib.dataIntegrationUtils.executeOperation` API to invoke the `getAccountById` service operation configured in the `employeeAccount` form data model.

The `getAccountById` operation takes the value in the `employeeID` form field as input for the `empId` argument and returns employee name, account number, and account balance for the corresponding employee. Die Ausgabewerte werden in den angegebenen Formularfeldern befüllt. For example, the value in `name` argument is populated in the `fullName` form element and value for `accountNumber` argument in `account` form element.

```javascript
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

## Verwenden der API mit der Rückruffunktion {#using-the-api-callback}

Sie können den Formulardatenmodelldienst auch über die `guidelib.dataIntegrationUtils.executeOperation` API mit einer Rückruffunktion aufrufen. Für die API gilt die folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

Die Rückruffunktion kann über Rückruffunktionen `success` und `failure` Rückruffunktionen verfügen.

### Beispielskript mit Rückruffunktionen bei Erfolg und Fehler {#callback-function-success-failure}

The following sample script uses the `guidelib.dataIntegrationUtils.executeOperation` API to invoke the `GETOrder` service operation configured in the `employeeOrder` form data model.

Der `GETOrder` Vorgang nimmt den Wert im `Order ID` Formularfeld als Eingabe für das `orderId` Argument und gibt den Wert für die Bestellmenge in der `success` Rückruffunktion zurück.  Wenn die `success` Rückruffunktion nicht die Bestellmenge zurückgibt, zeigt die `failure` Rückruffunktion die `Error occured` Meldung an.

>[!NOTE]
>
> Wenn Sie die `success` Rückruffunktion verwenden, werden die Ausgabewerte nicht in die angegebenen Formularfelder eingefügt.

```javascript
var operationInfo = {
    "formDataModelId": "/content/dam/formsanddocuments-fdm/employeeOrder",
    "operationTitle": "GETOrder",
    "operationName": "GETOrder"
};
var inputs = {
    "orderId" : Order ID
};
var outputs = {};
var success = function (wsdlOutput, textStatus, jqXHR) {
order_quantity.value = JSON.parse(wsdlOutput).quantity;
 };
var failure = function(){
alert('Error occured');
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, success, failure);
```
