---
title: Standardmäßige Prüffehlermeldungen für adaptive Formulare
seo-title: Standardmäßige Prüffehlermeldungen für adaptive Formulare
description: Konvertieren der Prüffehlermeldungen für adaptive Formulare in das Standardformat mithilfe von benutzerdefinierten Fehlerhandlern
seo-description: Konvertieren der Prüffehlermeldungen für adaptive Formulare in das Standardformat mithilfe von benutzerdefinierten Fehlerhandlern
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
translation-type: tm+mt
source-git-commit: 48cd21915017da96015df4e7619611ebf775c5fb

---


# Standardmäßige Prüffehlermeldungen für adaptive Formulare {#standard-validation-error-messages}

Adaptive Formulare validieren die Eingaben, die Sie in Feldern bereitstellen, basierend auf einem voreingestellten Validierungskriterium. Die Validierungskriterien beziehen sich auf die zulässigen Eingabewerte für Felder in einem adaptiven Formular. Sie können die Überprüfungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Webdienste als Datenquelle verwenden, können Sie die Überprüfungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Überprüfungskriterien erfüllen, werden die Werte an die Datenquelle gesendet. Andernfalls wird im adaptiven Formular eine Fehlermeldung angezeigt.

Ähnlich wie bei diesem Ansatz können adaptive Formulare jetzt in benutzerdefinierte Dienste integriert werden, um Datenvalidierungen durchzuführen. Wenn die eingegebenen Werte die Überprüfungskriterien nicht erfüllen und die vom Server zurückgegebene Prüffehlermeldung im Standardmeldungsformat vorliegt, werden die Fehlermeldungen auf Feldebene im Formular angezeigt.

Wenn die Eingabewerte die Überprüfungskriterien nicht erfüllen und die Fehlermeldung zur Servervalidierung nicht im Standardmeldungsformat vorliegt, stellen die adaptiven Formulare einen Mechanismus bereit, mit dem die Prüffehlermeldungen in ein Standardformat umgewandelt werden können, sodass sie auf Feldebene im Formular angezeigt werden. Sie können die Fehlermeldung mit zwei der folgenden Methoden in das Standardformat transformieren:

* Hinzufügen eines benutzerspezifischen Fehlerhandlers bei der Übermittlung eines adaptiven Formulars
* Fügen Sie benutzerdefinierte Handler zum Aufrufen einer Dienstaktion mit dem Regeleditor hinzu

In diesem Artikel werden das Standardformat für die Prüffehlermeldungen und die Anweisungen zur Konvertierung der Fehlermeldungen von einem benutzerdefinierten in das Standardformat beschrieben.

## Standard-Fehlermeldungsformat {#standard-validation-message-format}

Die adaptiven Formulare zeigen die Fehler auf Feldebene an, wenn die Fehlermeldungen zur Servervalidierung im folgenden Standardformat vorliegen:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]

        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```

wobei:

* `errorCausedBy` beschreibt den Fehlergrund
* `errors` Erwähnung des SOM-Ausdrucks der Felder, bei denen die Validierungskriterien zusammen mit der Prüffehlermeldung fehlgeschlagen sind
* `originCode` enthält den vom externen Dienst zurückgegebenen Fehlercode
* `originMessage` enthält die vom externen Dienst zurückgegebenen Rohfehlerdaten

## Konfigurieren der Übermittlung adaptiver Formulare zum Hinzufügen benutzerdefinierter Handler {#configure-adaptive-form-submission}

Wenn die Fehlermeldung zur Serverüberprüfung nicht im Standardformat angezeigt wird, können Sie die asynchrone Übermittlung aktivieren und einen benutzerdefinierten Fehlerhandler für die Übermittlung des adaptiven Formulars hinzufügen, um die Nachricht in ein Standardformat zu konvertieren.

### Konfigurieren der asynchronen Übermittlung adaptiver Formulare {#configure-asynchronous-adaptive-form-submission}

Bevor Sie einen benutzerdefinierten Handler hinzufügen, müssen Sie das adaptive Formular für die asynchrone Übermittlung konfigurieren. Führen Sie die folgenden Schritte aus:

1. In adaptive form authoring mode, select the Form Container object and tap ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Wählen Sie **[!UICONTROL Auf Server]** erneut überprüfen, um die Eingabefeldwerte vor der Übermittlung auf dem Server zu überprüfen.
1. Wählen Sie die Übermittlungsaktion aus:

   * Wählen Sie &quot; **[!UICONTROL Senden mit Formulardatenmodell]** &quot;und wählen Sie das entsprechende Datenmodell, wenn Sie RESTful-Webdienst-basiertes [Formulardatenmodell](work-with-form-data-model.md) als Datenquelle verwenden.
   * Wählen Sie &quot; **[!UICONTROL An REST-Endpunkt]** übermitteln&quot;und geben Sie die **[!UICONTROL Umleitungs-URL/den Pfad]** an, wenn Sie RESTful-Webdienste als Datenquelle verwenden.
   ![Eigenschaften für die Übermittlung adaptiver Formulare](assets/af_submission_properties.png)

1. Tippen Sie auf ![Speichern](assets/save_icon.png), um die Eigenschaften zu speichern.

### Hinzufügen eines benutzerspezifischen Fehlerhandlers bei der Übermittlung eines adaptiven Formulars {#add-custom-error-handler-af-submission}

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Handler sind clientseitige Funktionen, die anhand der Serverantwort ausgeführt werden. Wenn ein Formular übermittelt wird, werden die Daten zur Validierung an den Server gesendet, der eine Antwort mit Informationen über den Erfolg oder das Fehlschlagen der Übermittlung an den Client zurücksendet. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Führen Sie die folgenden Schritte aus, um beim Senden des adaptiven Formulars einen benutzerdefinierten Fehlerhandler hinzuzufügen:

1. Open the adaptive form in authoring mode, select any form object, and tap <!--![Rule Editor](assets/af_edit_rules.png)--> to open the rule editor.
1. Wählen Sie **[!UICONTROL Formular]** in der Struktur „Formularobjekte“ und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Wählen Sie **[!UICONTROL Fehler bei Übermittlung]** aus der Dropdownliste Ereignis.
1. Schreiben Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]** , um die Regel zu speichern.

Im Folgenden finden Sie einen Beispielcode zum Konvertieren einer benutzerdefinierten Fehlerstruktur in die standardmäßige Fehlerstruktur:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

Der `var som_map` Listet den SOM-Ausdruck der adaptiven Formularfelder auf, die Sie in das Standardformat umwandeln möchten. Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und &quot;SOM-Ausdruck **[!UICONTROL anzeigen&quot;wählen]**.

Mithilfe dieses benutzerspezifischen Fehlerhandlers konvertiert das adaptive Formular die in aufgeführten Felder in `var som_map` das Standard-Fehlermeldungsformat. Die Prüffehlermeldungen werden daher auf Feldebene im adaptiven Formular angezeigt.

## Hinzufügen eines benutzerdefinierten Handlers mit der Aktion &quot;Dienst aufrufen&quot;

Führen Sie die folgenden Schritte aus, um einen Fehler-Handler hinzuzufügen, um eine benutzerdefinierte Fehlerstruktur mithilfe der Aktion &quot;Aufrufdienst&quot;des [Regeleditors](rule-editor.md) in die Standardfehlerstruktur zu konvertieren:

1. Open the adaptive form in authoring mode, select any form object, and tap ![Rule Editor](assets/rule_editor_icon.png) to open the rule editor.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Erstellen Sie eine Bedingung im Abschnitt **[!UICONTROL Wenn]** der Regel. Beispiel:[WennName des Felds] geändert wird. Die Option &quot;Auswählen&quot; **[!UICONTROL wird aus der Dropdownliste &quot;Status]** auswählen&quot;geändert **[!UICONTROL , um diese Bedingung zu erreichen]** .
1. In the **[!UICONTROL Then]** section, select **[!UICONTROL Invoke Service]** from the **[!UICONTROL Select Action]** drop-down list.
1. Wählen Sie einen Post-Dienst und die zugehörigen Datenbindungen im Abschnitt **[!UICONTROL Eingabe]** aus. Wenn Sie beispielsweise die Felder **Name**, **ID** und **Status** im adaptiven Formular überprüfen möchten, wählen Sie einen Post-Dienst (Tier) aus und wählen Sie im Abschnitt **[!UICONTROL Eingabe]** den Eintrag &quot;pet.name&quot;, &quot;pet.id&quot;und &quot;pet.status&quot;aus.

Aufgrund dieser Regel werden die Werte, die Sie für die Felder **Name**, **ID** und **Status** eingeben, validiert, sobald das in Schritt 2 definierte Feld geändert wird und Sie die Tabulatortaste aus dem Feld im Formular entfernen.

1. Select **[!UICONTROL Code Editor]** from the mode selection drop-down list.
1. Tippen Sie auf Code **[!UICONTROL bearbeiten]**.
1. Löschen Sie die folgende Zeile aus dem vorhandenen Code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Schreiben Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]** , um die Regel zu speichern.
Fügen Sie beispielsweise am Ende den folgenden Beispielcode hinzu, um eine benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren:

   ```javascript
   var errorHandler = function(jqXHR, data) {
   var som_map = {
       "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
       "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
       "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
   };
   
   
   var errorJson = {};
   errorJson.errors = [];
   
   if (data) {
       if (data.originMessage) {
           var errorData;
           try {
               errorData = JSON.parse(data.originMessage);
           } catch (err) {
               // not in json format
           }
   
           if (errorData) {
               Object.keys(errorData).forEach(function(key) {
                   var som_key = som_map[key];
                   if (som_key) {
                       var error = {};
                       error.somExpression = som_key;
                       error.errorMessage = errorData[key];
                       errorJson.errors.push(error);
                   }
               });
           }
           window.guideBridge.handleServerValidationError(errorJson);
       } else {
           window.guideBridge.handleServerValidationError(data);
       }
     }
   };
   
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Der `var som_map` Listet den SOM-Ausdruck der adaptiven Formularfelder auf, die Sie in das Standardformat umwandeln möchten. Sie können den SOM-Ausdruck eines Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und im Menü &quot; **[!UICONTROL Mehr Optionen]** &quot;(...) die Option &quot;SOM-Ausdruck **** anzeigen&quot;auswählen.

   Stellen Sie sicher, dass Sie die folgende Zeile des Beispielcodes in den benutzerdefinierten Fehlerhandler kopieren:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Die executeOperation-API enthält die `null` und `errorHandler` -Parameter, die auf dem neuen benutzerdefinierten Fehlerhandler basieren.

   Mithilfe dieses benutzerspezifischen Fehlerhandlers konvertiert das adaptive Formular die in aufgeführten Felder in `var som_map` das Standard-Fehlermeldungsformat. Die Prüffehlermeldungen werden daher auf Feldebene im adaptiven Formular angezeigt.