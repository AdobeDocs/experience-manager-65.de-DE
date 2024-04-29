---
title: API zum Aufrufen des Formulardatenmodell-Service aus adaptiven Formularen
description: Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Web-Dienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms, Foundation Components
exl-id: cf037174-3153-486f-85b1-c974cd5a1ace
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '533'
ht-degree: 100%

---

# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Übersicht {#overview}

AEM Forms ermöglicht es Formularautorinnen und -autoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem in einem Formulardatenmodell konfigurierte Dienste aus einem adaptiven Formularfeld heraus aufgerufen werden. Um einen Datenmodell-Service aufzurufen, können Sie entweder eine Regel im visuellen Editor anlegen oder ein JavaScript mit der `guidelib.dataIntegrationUtils.executeOperation`-API im Code-Editor des [Regeleditors](/help/forms/using/rule-editor.md) angeben.

In diesem Dokument wird das Schreiben von JavaScript in der `guidelib.dataIntegrationUtils.executeOperation`-API für den Aufruf eines Service beschrieben.

## Verwenden der API {#using-the-api}

Die `guidelib.dataIntegrationUtils.executeOperation`-API ruft einen Service über ein Feld in einem adaptiven Formular auf. Für die API gilt folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

Die Struktur der `guidelib.dataIntegrationUtils.executeOperation`-API gibt Details zum Service-Vorgang an. Die Struktur weist die folgende Syntax auf.

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

Die API-Struktur gibt folgende Informationen zum Service-Vorgang an.

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
   <td>Gibt den Repository-Pfad zum Formulardatenmodell an, einschließlich seines Namens</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Gibt den Namen des auszuführenden Service-Vorgangs an</td>
  </tr>
  <tr>
   <td><code>inputs</code></td>
   <td>Ordnet mindestens ein Formularobjekt den Eingabeargumenten für den Service-Vorgang zu</td>
  </tr>
  <tr>
   <td><code>Outputs</code></td>
   <td>Ordnet mindestens ein Formularobjekt Ausgabewerten aus dem Service-Vorgang zu, um Formularfelder zu befüllen<br /> </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Gibt Werte auf Grundlage der Eingabeargumente für den Service-Vorgang zurück. Dies ist ein optionaler Parameter, der als Rückruffunktion verwendet wird.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Zeigt eine Fehlermeldung an, wenn die Funktion für erfolgreichen Rückruf die Ausgabewerte auf Grundlage der Eingabeargumente nicht anzeigen kann. Dies ist ein optionaler Parameter, der als Rückruffunktion verwendet wird.<br /> </td>
  </tr>
 </tbody>
</table>

## Beispielskript zum Aufrufen eines Service {#sample-script-to-invoke-a-service}

Folgendes Beispielskript verwendet die `guidelib.dataIntegrationUtils.executeOperation`-API, um den `getAccountById`-Service-Vorgang aufzurufen, der im Formulardatenmodell `employeeAccount` konfiguriert ist.

Der Vorgang `getAccountById` nimmt den Wert im Formularfeld `employeeID` als Eingabe für das Argument `empId` und gibt den Mitarbeiternamen, die Kontonummer und den Kontostand für den entsprechenden Mitarbeiter zurück. Die Ausgabewerte werden in den angegebenen Formularfeldern befüllt. Beispielsweise wird der Wert im Argument `name` im Formularelement `fullName` befüllt und der Wert für das Argument `accountNumber` im Formularelement `account`.

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

## Verwenden der API mit Rückruffunktion {#using-the-api-callback}

Sie können den Formulardatenmodell-Service auch mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API mit einer Rückruffunktion aufrufen. Für die API gilt folgende Syntax:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

Die Rückruffunktion kann über die Rückruffunktionen `success` und `failure` verfügen.

### Beispielskript mit Rückruffunktionen für Erfolg und Fehlschlag {#callback-function-success-failure}

Folgendes Beispielskript verwendet die `guidelib.dataIntegrationUtils.executeOperation`-API, um den `GETOrder`-Service-Vorgang aufzurufen, der im Formulardatenmodell `employeeOrder` konfiguriert ist.

Der Vorgang `GETOrder` nimmt den Wert im Formularfeld `Order ID` als Eingabe für das `orderId`-Argument und gibt den Wert für die Bestellmenge in der Rückruffunktion `success` zurück.  Wenn die Rückruffunktion `success` nicht die Bestellmenge zurückgibt, zeigt die Rückruffunktion `failure` die Meldung `Error occured` an.

>[!NOTE]
>
>Wenn Sie die Rückruffunktion `success` verwenden, werden die Ausgabewerte nicht in die angegebenen Formularfelder eingefügt.

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
