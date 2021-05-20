---
title: Standardmäßige Validierungsfehlermeldungen für adaptive Formulare
seo-title: Standardmäßige Validierungsfehlermeldungen für adaptive Formulare
description: Konvertieren der Überprüfungsfehlermeldungen für adaptive Formulare in das Standardformat mithilfe von benutzerdefinierten Fehler-Handlern
seo-description: Konvertieren der Überprüfungsfehlermeldungen für adaptive Formulare in das Standardformat mithilfe von benutzerdefinierten Fehler-Handlern
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
feature: Adaptive Formulare
exl-id: 54a76d5c-d19b-4026-b71c-7b9e862874bc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 9%

---

# Standardmäßige Validierungsfehlermeldungen für adaptive Formulare {#standard-validation-error-messages}

Adaptive Formulare validieren die Eingaben, die Sie in Feldern bereitstellen, basierend auf vordefinierten Validierungskriterien. Die Validierungskriterien beziehen sich auf die zulässigen Eingabewerte für Felder in einem adaptiven Formular. Sie können die Validierungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Webdienste als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Validierungskriterien erfüllen, werden die Werte an die Datenquelle gesendet. Andernfalls zeigt das adaptive Formular eine Fehlermeldung an.

Ähnlich wie dieser Ansatz können adaptive Formulare jetzt in benutzerdefinierte Dienste integriert werden, um Datenvalidierungen durchzuführen. Wenn die eingegebenen Werte die Validierungskriterien nicht erfüllen und die vom Server zurückgegebene Validierungsfehlermeldung im standardmäßigen Nachrichtenformat vorliegt, werden die Fehlermeldungen auf Feldebene im Formular angezeigt.

Wenn die Eingabewerte die Validierungskriterien nicht erfüllen und die Fehlermeldung bei der Servervalidierung nicht im standardmäßigen Nachrichtenformat vorliegt, bieten die adaptiven Formulare einen Mechanismus, um die Validierungsfehlermeldungen in ein Standardformat umzuwandeln, sodass sie auf Feldebene im Formular angezeigt werden. Sie können die Fehlermeldung mit einer der beiden folgenden Methoden in das Standardformat umwandeln:

* Hinzufügen eines benutzerdefinierten Fehler-Handlers bei der Übermittlung des adaptiven Formulars
* Fügen Sie mithilfe des Regeleditors einen benutzerdefinierten Handler zur Aktion &quot;Dienst aufrufen&quot;hinzu

In diesem Artikel werden das Standardformat für die Validierungsfehlermeldungen und die Anweisungen zum Konvertieren der Fehlermeldungen von einer benutzerdefinierten in das Standardformat beschrieben.

## Standardmäßige Validierungs-Fehlermeldungsformat {#standard-validation-message-format}

Die adaptiven Formulare zeigen die Fehler auf Feldebene an, wenn die Fehlermeldungen bei der Servervalidierung im folgenden Standardformat vorliegen:

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

* `errorCausedBy` beschreibt den Grund für das Fehlschlagen
* `errors` den SOM-Ausdruck der Felder, die die Validierungskriterien nicht erfüllt haben, zusammen mit der Validierungsfehlermeldung erwähnen
* `originCode` enthält den vom externen Dienst zurückgegebenen Fehlercode
* `originMessage` enthält die vom externen Dienst zurückgegebenen rohen Fehlerdaten

## Konfigurieren Sie die Übermittlung des adaptiven Formulars, um benutzerdefinierte Handler {#configure-adaptive-form-submission} hinzuzufügen.

Wenn die Fehlermeldung zur Servervalidierung nicht im Standardformat angezeigt wird, können Sie die asynchrone Übermittlung aktivieren und einen benutzerdefinierten Fehler-Handler bei der Übermittlung des adaptiven Formulars hinzufügen, um die Nachricht in ein Standardformat zu konvertieren.

### Konfigurieren der asynchronen Übermittlung des adaptiven Formulars {#configure-asynchronous-adaptive-form-submission}

Bevor Sie einen benutzerdefinierten Handler hinzufügen, müssen Sie das adaptive Formular für die asynchrone Übermittlung konfigurieren. Führen Sie die folgenden Schritte aus:

1. Wählen Sie im Authoring-Modus für adaptive Formulare das Objekt &quot;Formularcontainer&quot;aus und tippen Sie auf ![Eigenschaften für adaptive Formulare](assets/configure_icon.png), um seine Eigenschaften zu öffnen.
1. Aktivieren Sie im Abschnitt **[!UICONTROL Submission]** properties die Option **[!UICONTROL Asynchrone Übermittlung verwenden]**.
1. Wählen Sie **[!UICONTROL Auf Server erneut überprüfen]** aus, um die Eingabefeldwerte auf dem Server vor der Übermittlung zu überprüfen.
1. Wählen Sie die Sendeaktion aus:

   * Wählen Sie **[!UICONTROL Senden mit Formulardatenmodell]** und wählen Sie das entsprechende Datenmodell aus, wenn Sie das RESTful-Webdienst-basierte [Formulardatenmodell](work-with-form-data-model.md) als Datenquelle verwenden.
   * Wählen Sie **[!UICONTROL An REST-Endpunkt übermitteln]** und geben Sie die **[!UICONTROL Umleitungs-URL/Pfad]** an, wenn Sie RESTful-Webdienste als Datenquelle verwenden.

   ![Eigenschaften für die Übermittlung adaptiver Formulare](assets/af_submission_properties.png)

1. Tippen Sie auf ![Speichern](assets/save_icon.png), um die Eigenschaften zu speichern.

### Fügen Sie einen benutzerdefinierten Fehler-Handler bei der Übermittlung des adaptiven Formulars {#add-custom-error-handler-af-submission} hinzu.

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Handler sind clientseitige Funktionen, die anhand der Serverantwort ausgeführt werden. Wenn ein Formular übermittelt wird, werden die Daten zur Validierung an den Server gesendet, der eine Antwort mit Informationen über den Erfolg oder das Fehlschlagen der Übermittlung an den Client zurücksendet. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Führen Sie die folgenden Schritte aus, um beim Senden des adaptiven Formulars einen benutzerdefinierten Fehler-Handler hinzuzufügen:

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein beliebiges Formularobjekt aus und tippen Sie auf <!--![Rule Editor](assets/af_edit_rules.png)-->, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Formular]** in der Struktur „Formularobjekte“ und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Wählen Sie **[!UICONTROL Fehler beim Senden]** aus der Dropdown-Liste Ereignis aus.
1. Schreiben Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die standardmäßige Fehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern.

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

Der `var som_map` listet den SOM-Ausdruck der adaptiven Formularfelder auf, die in das Standardformat umgewandelt werden sollen. Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und **[!UICONTROL SOM-Ausdruck anzeigen]** auswählen.

Mit diesem benutzerdefinierten Fehler-Handler konvertiert das adaptive Formular die in `var som_map` aufgelisteten Felder in das standardmäßige Fehlermeldungsformat. Daher werden die Überprüfungsfehlermeldungen auf Feldebene im adaptiven Formular angezeigt.

## Hinzufügen eines benutzerdefinierten Handlers mit der Aktion &quot;Dienst aufrufen&quot;

Führen Sie die folgenden Schritte aus, um einen Fehler-Handler hinzuzufügen, um eine benutzerdefinierte Fehlerstruktur mithilfe der Aktion [Regel-Editor](rule-editor.md) Dienst aufrufen in die Standardfehlerstruktur zu konvertieren:

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein beliebiges Formularobjekt aus und tippen Sie auf ![Regeleditor](assets/rule_editor_icon.png), um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Erstellen Sie eine Bedingung im Abschnitt **[!UICONTROL Wenn]** der Regel. Beispiel: Wenn[Name des Felds] geändert wird. Wählen Sie **[!UICONTROL Wird geändert]** aus der Dropdownliste **[!UICONTROL Status]** auswählen aus, um diese Bedingung zu erfüllen.
1. Im Abschnitt **[!UICONTROL Dann]** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen.]**
1. Wählen Sie einen Post-Dienst und die zugehörigen Datenbindungen aus dem Abschnitt **[!UICONTROL Input]** aus. Beispiel: Wenn Sie die Felder **Name**, **ID** und **Status** im adaptiven Formular validieren möchten, wählen Sie einen Post-Dienst (Begleiter) aus und wählen Sie die Felder &quot;pet.name&quot;, &quot;pet.id&quot;und &quot;pet.status&quot;im Abschnitt **[!UICONTROL Input]** aus.

Als Ergebnis dieser Regel werden die Werte, die Sie für die Felder **Name**, **ID** und **Status** eingeben, validiert, sobald das in Schritt 2 definierte Feld geändert wird und Sie aus dem Feld im Formular die Tabulatortaste verlassen.

1. Wählen Sie **[!UICONTROL Code-Editor]** aus der Dropdown-Liste der Modusauswahl.
1. Tippen Sie auf **[!UICONTROL Code bearbeiten]**.
1. Löschen Sie die folgende Zeile aus dem vorhandenen Code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Schreiben Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die standardmäßige Fehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern.
Fügen Sie beispielsweise den folgenden Beispielcode am Ende hinzu, um eine benutzerdefinierte Fehlerstruktur in die standardmäßige Fehlerstruktur zu konvertieren:

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

   Der `var som_map` listet den SOM-Ausdruck der adaptiven Formularfelder auf, die in das Standardformat umgewandelt werden sollen. Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und **[!UICONTROL SOM-Ausdruck anzeigen]** aus dem Menü **[!UICONTROL Weitere Optionen]** (...) auswählen.

   Stellen Sie sicher, dass Sie die folgende Zeile des Beispielcodes in den benutzerdefinierten Fehler-Handler kopieren:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Die executeOperation-API enthält die Parameter `null` und `errorHandler` , die auf dem neuen benutzerdefinierten Fehler-Handler basieren.

   Mit diesem benutzerdefinierten Fehler-Handler konvertiert das adaptive Formular die in `var som_map` aufgelisteten Felder in das standardmäßige Fehlermeldungsformat. Daher werden die Überprüfungsfehlermeldungen auf Feldebene im adaptiven Formular angezeigt.
