---
title: API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen
seo-title: API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen
description: Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Webdienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden.
seo-description: Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Webdienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Formulare
exl-id: cf037174-3153-486f-85b1-c974cd5a1ace
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 35%

---

# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Überblick {#overview}

AEM Forms ermöglicht es Formularautoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem sie Dienste, die in einem Formulardatenmodell konfiguriert sind, aus einem adaptiven Formularfeld heraus aufrufen. Um einen Datenmodelldienst aufzurufen, können Sie entweder eine Regel im Visual Editor erstellen oder mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API im Code-Editor des [Regel-Editors](/help/forms/using/rule-editor.md) ein JavaScript angeben.

In diesem Dokument wird das Schreiben von JavaScript im API`guidelib.dataIntegrationUtils.executeOperation` für den Aufruf eines Dienst beschrieben.

## Verwenden der API {#using-the-api}

Die `guidelib.dataIntegrationUtils.executeOperation`-API ruft einen Dienst aus einem Feld in einem adaptiven Formular auf. Für die API gilt die folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

Die Struktur der API `guidelib.dataIntegrationUtils.executeOperation` gibt Details zum Dienstvorgang an. Die Struktur weist die folgende Syntax auf.

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
   <td>Ordnet ein oder mehrere Formularobjekte Ausgabewerten aus dem Dienstvorgang zu, um Formularfelder auszufüllen<br /> </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Gibt Werte basierend auf den Eingabeargumenten für den Dienstvorgang zurück. Dies ist ein optionaler Parameter, der als Callback-Funktion verwendet wird.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Zeigt eine Fehlermeldung an, wenn die success -Rückruffunktion die Ausgabewerte basierend auf den Eingabeargumenten nicht anzeigen kann. Dies ist ein optionaler Parameter, der als Callback-Funktion verwendet wird.<br /> </td>
  </tr>
 </tbody>
</table>

## Beispielskript zum Erstellen eines Dienstes {#sample-script-to-invoke-a-service}

Das folgende Beispielskript verwendet die `guidelib.dataIntegrationUtils.executeOperation`-API, um den im Formulardatenmodell `employeeAccount` konfigurierten Dienstvorgang `getAccountById` aufzurufen.

Der Vorgang `getAccountById` nimmt den Wert im Formularfeld `employeeID` als Eingabe für das `empId`-Argument und gibt den Mitarbeiternamen, die Kontonummer und den Kontostand für den entsprechenden Mitarbeiter zurück. Die Ausgabewerte werden in den angegebenen Formularfeldern befüllt. Beispielsweise wird der Wert im Argument `name` im Formularelement `fullName` und der Wert für das Argument `accountNumber` im Formularelement `account` eingetragen.

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

## Verwenden der API mit der Callback-Funktion {#using-the-api-callback}

Sie können den Formulardatenmodelldienst auch mit der `guidelib.dataIntegrationUtils.executeOperation`-API mit einer Rückruffunktion aufrufen. Für die API gilt die folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

Die Callback-Funktion kann über die Callback-Funktionen `success` und `failure` verfügen.

### Beispielskript mit Callback-Funktionen für Erfolg und Fehler {#callback-function-success-failure}

Das folgende Beispielskript verwendet die `guidelib.dataIntegrationUtils.executeOperation`-API, um den im Formulardatenmodell `employeeOrder` konfigurierten Dienstvorgang `GETOrder` aufzurufen.

Der Vorgang `GETOrder` nimmt den Wert im Formularfeld `Order ID` als Eingabe für das `orderId`-Argument und gibt den Wert der Bestellmenge in der Callback-Funktion `success` zurück.  Wenn die Rückruffunktion `success` die Auftragsmenge nicht zurückgibt, zeigt die Rückruffunktion `failure` die Meldung `Error occured` an.

>[!NOTE]
>
> Wenn Sie die Callback-Funktion `success` verwenden, werden die Ausgabewerte nicht in die angegebenen Formularfelder eingefügt.

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
