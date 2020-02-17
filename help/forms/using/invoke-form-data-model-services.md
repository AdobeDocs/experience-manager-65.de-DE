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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Überblick {#overview}

AEM Forms ermöglicht es Formularautoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem sie Dienste, die in einem Formulardatenmodell konfiguriert sind, aus einem adaptiven Formularfeld heraus aufrufen. To invoke a data model service, you can either create a rule in the visual editor or specify a JavaScript using the `guidelib.dataIntegrationUtils.executeOperation` API in the code editor of the [rule editor](/help/forms/using/rule-editor.md).

In diesem Dokument wird das Schreiben von JavaScript im API`guidelib.dataIntegrationUtils.executeOperation` für den Aufruf eines Dienst beschrieben.

## Verwenden der API {#using-the-api}

The `guidelib.dataIntegrationUtils.executeOperation` API invokes a service from within an adaptive form field. Für die API gilt die folgende Syntax:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

Für die API sind die folgenden Parameter erforderlich.

| Parameter | Beschreibung |
|---|---|
| `operationInfo` | Struktur zur Angabe von Formulardatenmodellkennung, Operationstitel und Operationsname |
| `inputs` | Struktur zum Festlegen von Formularobjekten, deren Werte für den Dienstvorgang eingegeben werden |
| `outputs` | Struktur zur Angabe von Formularobjekten, die mit den vom Dienstvorgang zurückgegebenen Werten gefüllt werden |

The structure of the `guidelib.dataIntegrationUtils.executeOperation` API specifies details about the service operation. Die Struktur weist die folgende Syntax auf.

```
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
   <td><code>forDataModelId</code></td>
   <td>Geben Sie den Repository-Pfad zum Formulardatenmodell an, einschließlich Name</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Geben Sie den Namen des Dienstvorgangs an, um</td>
  </tr>
  <tr>
   <td><code>input</code></td>
   <td>Ordnen Sie ein oder mehrere Formularobjekte den Eingabeargumenten für den Dienstvorgang zu.</td>
  </tr>
  <tr>
   <td>Ausgabe</td>
   <td>Ordnen Sie ein oder mehrere Formularobjekte Ausgabewerte aus dem Dienstvorgang zu, um Formularfelder zu füllen.<br />  </td>
  </tr>
 </tbody>
</table>

## Beispielskript zum Erstellen eines Dienstes {#sample-script-to-invoke-a-service}

The following sample script uses the `guidelib.dataIntegrationUtils.executeOperation` API to invoke the `getAccountById` service operation configured in the `employeeAccount` form data model.

The `getAccountById` operation takes the value in the `employeeID` form field as input for the `empId` argument and returns employee name, account number, and account balance for the corresponding employee. Die Ausgabewerte werden in den angegebenen Formularfeldern befüllt. For example, the value in `name` argument is populated in the `fullName` form element and value for `accountNumber` argument in `account` form element.

```
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

