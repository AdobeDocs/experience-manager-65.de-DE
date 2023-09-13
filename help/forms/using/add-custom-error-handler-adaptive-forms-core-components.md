---
title: Fügen Sie einen benutzerdefinierten Fehler-Handler im adaptiven Forms hinzu, der auf Kernkomponenten für AEM adaptive Forms basiert
seo-title: Error Handlers in Adaptive Forms for AEM Adaptive Forms core components
description: AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für ein Formular mit dem REST-Endpunkt, der zum Aufrufen eines externen Dienstes konfiguriert wurde. Sie können einen standardmäßigen Fehler-Handler und einen benutzerdefinierten Fehler-Handler in einem AEM adaptiven Formular hinzufügen.
seo-description: Error handler function and Rule Editor in Adaptive Forms core components helps you to effectively manage and customize error handling. You can add a default error handler as well as custom error handler in an AEM Adaptive Form.
keywords: Fügen Sie einen benutzerdefinierten Fehler-Handler hinzu, fügen Sie einen Standard-Fehler-Handler hinzu, fügen Sie einen Fehler-Handler zum Formular hinzu, verwenden Sie den invoke-Dienst des Regeleditors, um einen benutzerdefinierten Fehler-Handler hinzuzufügen, konfigurieren Sie den Regeleditor, um einen benutzerdefinierten Fehler-Handler hinzuzufügen, fügen Sie mithilfe des Regeleditors einen benutzerdefinierten Fehler-Handler hinzu.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms
source-git-commit: 6d6e74c61b2ecb13e7cc352d5278c40d2677d44d
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 7%

---


# Fehlerhandler in Adaptive Forms (Kernkomponenten) {#error-handlers-in-adaptive-form}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/add-custom-error-handler-adaptive-forms-core-components.html) |
| AEM 6.5 | Dieser Artikel |

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Es bietet außerdem Funktionen zum Anpassen von Fehler-Handler-Funktionen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist. Handler sind Client-seitige Funktionen, die basierend auf der Server-Antwort ausgeführt werden. Wenn ein externer Dienst mithilfe von APIs aufgerufen wird, werden die Daten zur Validierung an den Server übertragen, der eine Antwort mit Informationen zum Erfolgs- oder Fehlerereignis für die Übermittlung an den Client zurückgibt. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen. Ein Fehler-Handler hilft bei der Verwaltung und Anzeige von Fehlern oder Validierungsproblemen.

![Workflow für Fehler-Handler, um zu verstehen, wie Sie benutzerdefinierten Fehler-Handler in Formularen hinzufügen](/help/forms/using/assets/error-handler-workflow.png)

Das adaptive Formular validiert die Eingaben, die Sie in Feldern bereitstellen, basierend auf voreingestellten Validierungskriterien und überprüft auf verschiedene Fehler, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert wurde. Sie können die Validierungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Web-Services als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Validierungskriterien erfüllen und die Werte an die Datenquelle gesendet werden, zeigt das adaptive Formular eine Fehlermeldung mit einem Fehler-Handler an. Ähnlich wie bei diesem Ansatz integrieren Adaptive Forms mit benutzerdefinierten Fehler-Handlern, um Datenvalidierungen durchzuführen. Wenn die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene im adaptiven Formular angezeigt. Dies tritt auf, wenn die vom Server zurückgegebene Validierungsfehlermeldung im standardmäßigen Nachrichtenformat vorliegt.


## Verwendung von Fehler-Handlern {#uses-of-error-handler}

Fehlerhandler werden für verschiedene Zwecke verwendet. Einige der Verwendungen von Fehler-Handler-Funktionen sind unten aufgeführt:

* **Validierung durchführen**: Die Fehlerbehandlung beginnt mit der Validierung von Benutzereingaben anhand vordefinierter Regeln oder Kriterien. Wenn Benutzer ein adaptives Formular ausfüllen, validiert der Fehler-Handler die Eingabe, um sicherzustellen, dass sie das erforderliche Format, die Länge oder andere Einschränkungen erfüllt.

* **Echtzeit-Feedback geben**: Wenn ein Fehler erkannt wird, zeigt der Fehler-Handler dem Benutzer sofortiges Feedback an, z. B. Inline-Fehlermeldungen unter den entsprechenden Formularfeldern. Dieses Feedback hilft Benutzern, Fehler zu identifizieren und zu korrigieren, ohne das Formular senden und auf eine Antwort warten zu müssen.


* **Fehlermeldungen anzeigen**: Wenn bei einer Übermittlung des adaptiven Formulars ein Überprüfungsfehler auftritt, zeigt der Fehler-Handler eine entsprechende Fehlermeldung an. Die Fehlermeldungen sollten klar, kurz und deutlich die spezifischen Felder sein, die beachtet werden müssen.

* **markiert das fehlerhafte Feld**: Um die Aufmerksamkeit des Benutzers auf bestimmte falsche Felder zu lenken, hebt der Fehler-Handler die entsprechenden Felder hervor oder unterscheidet sie visuell. Dies geschieht durch Ändern der Hintergrundfarbe, Hinzufügen eines Symbols oder Rahmens oder eines anderen visuellen Hinweises, der Benutzern beim schnellen Auffinden und Beheben der Fehler hilft.


## Fehler-/Fehlerreaktionsformat {#failure-response-format}

Ein adaptives Formular zeigt die Fehler auf Feldebene an, wenn die Fehlermeldungen zur Servervalidierung im folgenden Standardformat vorliegen.
Der folgende Code veranschaulicht die vorhandene Fehlerreaktionsstruktur:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


Dabei gilt:

* `errorCausedBy` beschreibt den Grund für das Fehlschlagen.
* `errors` Geben Sie den qualifizierten Feldnamen der Felder an, die die Validierungskriterien nicht erfüllt haben, sowie die Validierungsfehlermeldung.
* `originCode` -Feld von AEM hinzugefügt wurde und den vom externen Dienst zurückgegebenen HTTP-Status-Code enthält.
* `originMessage` -Feld von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen rohen Fehlerdaten enthält.

Mit den Verbesserungen der Funktionen und nachfolgenden Aktualisierungen der Versionen von AEM Forms hat sich die vorhandene Fehlerreaktionsstruktur auf Grundlage von RFC7807 in ein neues Format geändert, das abwärtskompatibel mit der vorhandenen Fehlerreaktionsstruktur ist:

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<qualified fieldname of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code>, (optional - in case of SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - in case of SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * Stellen Sie sicher, dass die Struktur der Fehlerantwort Folgendes enthält: **fieldName** oder **dataRef**.
> * Stellen Sie sicher, dass **ContentType** -Kopfzeile ist **application/problem+json**.

Dabei gilt:
* `type (required)` gibt den Fehlertyp an. Es kann sich um einen der folgenden Werte handeln:
   * `SERVER_SIDE_VALIDATION` weist auf einen Fehler aufgrund der serverseitigen Validierung hin.
   * `FORM_SUBMISSION` weist auf einen Fehler während der Formularübermittlung hin
   * `SERVICE_INVOCATION` weist auf einen Fehler während eines Drittanbieter-Dienstaufrufs hin.
   * `FAILURE` zeigt einen allgemeinen Fehler an.
   * `VALIDATION_ERROR` weist auf einen Fehler aufgrund eines Validierungsfehlers hin.

* `title (optional)` gibt einen Titel oder eine kurze Beschreibung des Fehlschlagens ein.
* `detail (optional)` enthält bei Bedarf weitere Details zum Fehler.
* `instance (optional)` stellt eine Instanz oder einen Bezeichner dar, die bzw. der mit dem Fehler verknüpft ist, und hilft beim Tracking oder Identifizieren des spezifischen Vorkommens des Fehlers.
* `validationErrors (required)` enthält Informationen zu Validierungsfehlern. Er enthält die folgenden Felder:
   * `fieldname` erwähnt den qualifizierten Feldnamen der Felder, die die Validierungskriterien nicht erfüllt haben.
   * `dataRef` stellt den JSON-Pfad oder XPath der Felder dar, bei denen die Überprüfung fehlgeschlagen ist.
   * `details` enthalten die Validierungsfehlermeldung mit dem fehlerhaften Feld.
* `originCode (optional)` von AEM hinzugefügtes Feld enthält den vom externen Dienst zurückgegebenen HTTP-Status-Code
* `originMessage (optional)` -Feld von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen rohen Fehlerdaten enthält.

### Beispiel für ein Antwortformat für Fehler {#sample-error-response-format}

Einige der Optionen zur Anzeige der Fehlerantworten sind:

+++  Basiert auf der Feldname-Eigenschaft des adaptiven Formulars


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "$form.PetId",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```


+++


+++ Basiert auf der dataRef-Eigenschaft des adaptiven Formulars

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "$.Pet.id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

+++

## Voraussetzungen {#prerequisites}

Vor der Verwendung des Fehler-Handlers in einem adaptiven Forms:

* [Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung](enable-adaptive-forms-core-components.md).
* Grundlegendes Wissen zu [Erstellen einer benutzerdefinierten Funktion](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/custom-functions-aem-forms.html?lang=en#:~:text=AEM%20Forms%206.5%20introduced%20the,use%20them%20across%20multiple%20forms.).
* Installieren Sie die neueste Version von [Apache Maven](https://maven.apache.org/download.cgi).

## Hinzufügen eines Fehler-Handlers mit dem Regeleditor {#add-error-handler-using-rule-editor}

Verwenden der [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) -Aktion verwenden, definieren Sie die Validierungskriterien auf Grundlage der Datenquelle, die Sie mit dem adaptiven Formular verwenden. Wenn Sie RESTful-Webdienste als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren. Durch die Verwendung der Funktionen für Fehler-Handler und des Regeleditors in Adaptive Forms können Sie die Fehlerbehandlung effektiv verwalten und anpassen. Sie definieren die Bedingungen mithilfe des Regeleditors und konfigurieren die gewünschten Aktionen, die ausgeführt werden sollen, wenn die Regel ausgelöst wird. Adaptives Formular validiert die Eingaben, die Sie in Felder eingeben, basierend auf vordefinierten Validierungskriterien. Falls die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene in einem adaptiven Formular angezeigt.

>[!NOTE]
>
> * Um Fehler-Handler mit der Aktion &quot;Aufrufdienst&quot;des Regeleditors zu verwenden, konfigurieren Sie Adaptive Forms mit einem Formulardatenmodell.
> * Es wird ein standardmäßiger Fehler-Handler bereitgestellt, mit dem Fehlermeldungen in Feldern angezeigt werden, wenn die Fehlerantwort im Standardschema enthalten ist. Sie können auch den Standard-Fehler-Handler über die benutzerdefinierte Fehler-Handler-Funktion aufrufen.

Mit dem Regeleditor können Sie:

* [Standard-Fehler-Handler-Funktion hinzufügen](#add-default-errror-handler)
* [Hinzufügen einer benutzerdefinierten Fehler-Handler-Funktion](#add-custom-errror-handler)


### Standard-Fehler-Handler-Funktion hinzufügen {#add-default-errror-handler}

Ein standardmäßiger Fehler-Handler wird unterstützt, um Fehlermeldungen in Feldern anzuzeigen, wenn die Fehlerantwort im Standardschema oder bei serverseitigem Validierungsfehler liegt.
Informationen zur Verwendung eines Standard-Fehler-Handlers mit der [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) -Aktion verwenden, nehmen Sie ein Beispiel für ein einfaches adaptives Formular mit zwei Feldern. **Haustier-ID** und **Heimtiername** und verwenden Sie den Standard-Fehler-Handler unter **Haustier-ID** -Feld zur Überprüfung auf verschiedene Fehler, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist, z. B. `200 - OK`,`404 - Not Found`, `400 - Bad Request`. Führen Sie die folgenden Schritte aus, um mithilfe der Aktion &quot;Aufrufdienst&quot;des Regeleditors einen standardmäßigen Fehler-Handler hinzuzufügen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus, wählen Sie eine Formularkomponente aus und tippen Sie auf **[!UICONTROL Regeleditor]** , um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Definieren Sie eine Bedingung im Abschnitt **Wann** der Regel. Beispiel: **Wann[Name des Felds &quot;Haustier-ID&quot;]** geändert. Wählen Sie die Option aus. **Status auswählen** Dropdown-Liste.
1. Im Abschnitt **Dann** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **Aktion auswählen.**
1. Wählen Sie eine **Post-Service** und die entsprechenden Datenbindungen aus der **Eingabe** Abschnitt. Beispiel: Zu validieren **Haustier-ID**, wählen Sie eine **Post-Service** as **GET /pet/{petId}** und wählen **Haustier-ID** im **Eingabe** Abschnitt.
1. Wählen Sie die Datenbindungen aus der **Ausgabe** Abschnitt. Auswählen **Heimtiername** im **Ausgabe** Abschnitt.
1. Auswählen **[!UICONTROL Standard-Fehler-Handler]** aus dem **Fehler-Handler** Abschnitt.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Standard-Fehler-Handler für Feldüberprüfungen in einem Formular hinzufügen](/help/forms/using/assets/default-error-handler.png)

Aus dieser Regel ergeben sich die Werte, für die Sie **Haustier-ID** überprüft die Validierung für **Heimtiername** Verwendung des externen Dienstes, der vom REST-Endpunkt aufgerufen wurde. Wenn die auf der Datenquelle basierenden Validierungskriterien fehlschlagen, werden die Fehlermeldungen auf Feldebene angezeigt.

![Anzeigen der Standardfehlermeldung beim Hinzufügen eines Standard-Fehler-Handlers in einem Formular zur Verarbeitung von Fehlerantworten](/help/forms/using/assets/default-error-message.png)

### Hinzufügen einer benutzerdefinierten Fehler-Handler-Funktion {#add-custom-errror-handler}

Sie können eine benutzerdefinierte Fehler-Handler-Funktion hinzufügen, um einige der folgenden Aktionen auszuführen:

* Verarbeiten Sie Fehlerantworten, die nicht standardmäßige oder standardmäßige Fehlerantworten verwenden. Es ist wichtig zu beachten, dass diese nicht standardmäßigen Fehlerantworten nicht mit dem [Standardschema von Fehlerantworten](#failure-response-format).
* Analytics-Ereignisse an beliebige Analytics-Plattformen senden. Beispiel: Adobe Analytics.
* modales Dialogfeld mit Fehlermeldungen anzeigen.

Zusätzlich zu den genannten Aktionen können die benutzerdefinierten Fehler-Handler verwendet werden, um benutzerdefinierte Funktionen auszuführen, die bestimmten Benutzeranforderungen entsprechen.

Der benutzerdefinierte Fehler-Handler ist eine Funktion (Client-Bibliothek), die auf von einem externen Dienst zurückgegebene Fehler reagiert und Endbenutzern eine benutzerdefinierte Antwort bereitstellt. Jede Client-Bibliothek mit Anmerkungen `@errorHandler` wird als benutzerdefinierte Fehler-Handler-Funktion betrachtet. Diese Anmerkung hilft bei der Identifizierung der Fehler-Handler-Funktion, die in der `.js` -Datei.

Informationen zum Erstellen und Verwenden eines benutzerdefinierten Fehler-Handlers mit dem [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) -Aktion verwenden. Nehmen wir ein Beispiel für ein adaptives Formular mit zwei Feldern. **Haustier-ID** und **Heimtiername** und verwenden Sie einen benutzerdefinierten Fehler-Handler am **Haustier-ID** -Feld zur Überprüfung auf verschiedene Fehler, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist, z. B. `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

So fügen Sie einen benutzerdefinierten Fehler-Handler in einem adaptiven Formular hinzu und verwenden ihn:

1. [Benutzerdefinierten Fehler-Handler erstellen](#create-custom-error-message)
1. [Verwenden des Regeleditors zum Konfigurieren des benutzerdefinierten Fehler-Handlers](#use-custom-error-handler)

#### 1. Erstellen Sie einen benutzerdefinierten Fehler-Handler {#create-custom-error-message}

Um eine benutzerdefinierte Fehlerfunktion zu erstellen, führen Sie die folgenden Schritte aus:

1. Anmelden `http://server:port/crx/de/index.jsp#`.
1. Erstellen Sie einen Ordner unter dem `/apps` Ordner. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Speichern Sie Ihre Änderungen.
1. Navigieren Sie zum erstellten Ordner und erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` as `clientlibs`.
1. Navigieren Sie zum neu erstellten `clientlibs` und fügen Sie den `allowProxy` und `categories` properties:

   ![Eigenschaften von benutzerdefinierten Bibliotheksknoten](/help/forms/using/assets/customlibrary-properties.png)

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen anstelle von `customfunctionsdemo`.

1. Speichern Sie Ihre Änderungen.

1. Erstellen Sie einen Ordner mit dem Namen `js` unter `clientlibs` Ordner.
1. Erstellen Sie eine JavaScript-Datei mit dem Namen `functions.js` unter `js` Ordner
1. Erstellen Sie eine Datei mit dem Namen `js.txt` unter `clientlibs` Ordner.
1. Speichern Sie Ihre Änderungen.
Die erstellte Ordnerstruktur sieht wie folgt aus:

   ![Ordnerstruktur der erstellten Client-Bibliothek](/help/forms/using/assets/customclientlibrary_folderstructure.png)
1. Doppelklicken Sie auf die `functions.js` -Datei, um den Editor zu öffnen. Die Datei enthält den Code für den benutzerdefinierten Fehler-Handler.
Fügen wir den folgenden Code zur JavaScript-Datei hinzu, um die Antwort und die vom REST-Dienstendpunkt empfangenen Kopfzeilen in der Browserkonsole anzuzeigen.

   ```javascript
       /** 
       Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers, globals)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           alert("CustomErrorHandler - Please enter valid PetId.")
           globals.invoke('defaultErrorHandler',response, headers)
           console.log("Custom Error Handler processing end...");
       }
   ```

   Um den Standard-Fehler-Handler von Ihrem benutzerdefinierten Fehler-Handler aufzurufen, wird die folgende Zeile des Beispielcodes verwendet:
   `globals.invoke('defaultErrorHandler',response, headers) `

1. Speichern `function.js`.
1. Navigieren Sie zu `js.txt` und fügen Sie den folgenden Code hinzu:

   ```javascript
       #base=js
       functions.js
   ```

1. Speichern Sie die Datei `js.txt`.

Jetzt erfahren Sie, wie Sie einen benutzerdefinierten Fehler-Handler mit dem Invoke-Dienst des Regeleditors in AEM Forms konfigurieren und verwenden.

#### 2. Verwenden Sie den Regeleditor, um den benutzerdefinierten Fehler-Handler zu konfigurieren {#use-custom-error-handler}

Bevor Sie den benutzerdefinierten Fehler-Handler in ein adaptives Formular implementieren, stellen Sie sicher, dass der Name der Client-Bibliothek im **[!UICONTROL Client-Bibliothekskategorie]** entspricht dem Namen, der in der Kategorieoption der `.content.xml` -Datei.

![Hinzufügen des Namens der Client-Bibliothek in der Konfiguration des Containers für adaptive Formulare](/help/forms/using/assets/client-library-category-name-core-component.png)

In diesem Fall wird der Name der Client-Bibliothek als `customfunctionsdemo` im `.content.xml` -Datei.

So verwenden Sie einen benutzerdefinierten Fehler-Handler mit dem **[!UICONTROL Aufrufdienst des Regeleditors]** Aktion:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus, wählen Sie eine Formularkomponente aus und tippen Sie auf **[!UICONTROL Regeleditor]** , um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Definieren Sie eine Bedingung im Abschnitt **Wann** der Regel. Beispiel: Wenn **[Name des Felds &quot;Haustier-ID&quot;]** geändert wird, wählen Sie **geändert wird** aus dem **Status auswählen** Dropdown-Liste.
1. Im Abschnitt **Dann** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **Aktion auswählen.**
1. Wählen Sie eine **Post-Service** und die entsprechenden Datenbindungen aus der **Eingabe** Abschnitt. Beispiel: Zu validieren **Haustier-ID**, wählen Sie eine **Post-Service** as **GET /pet/{petId}** und wählen **Haustier-ID** im **Eingabe** Abschnitt.
1. Wählen Sie die Datenbindungen aus der **Ausgabe** Abschnitt. Wählen Sie beispielsweise **Heimtiername** im **Ausgabe** Abschnitt.
1. Auswählen **[!UICONTROL Benutzerdefinierter Fehler-Handler]** aus dem **[!UICONTROL Fehler-Handler]** Abschnitt.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Fügen Sie einen benutzerdefinierten Fehler-Handler in ein Formular ein, um Fehlerantworten zu verarbeiten](/help/forms/using/assets/custom-error-handler.png)

Aus dieser Regel ergeben sich die Werte, für die Sie **Haustier-ID** überprüft die Validierung für **Heimtiername** Verwendung des externen Dienstes, der vom REST-Endpunkt aufgerufen wurde. Wenn die auf der Datenquelle basierenden Validierungskriterien fehlschlagen, werden die Fehlermeldungen auf Feldebene angezeigt.

![Fügen Sie einen benutzerdefinierten Fehler-Handler in ein Formular ein, um Fehlerantworten zu verarbeiten.](/help/forms/using/assets/custom-error-handler-message-core-component.png)

Öffnen Sie die Browser-Konsole und überprüfen Sie die Antwort und die Kopfzeile, die vom REST-Dienstendpunkt empfangen wurden, auf die Überprüfungsfehlermeldung.

Die benutzerdefinierte Fehler-Handler-Funktion ist für die Ausführung zusätzlicher Aktionen verantwortlich, z. B. für die Anzeige eines modalen Dialogfelds oder das Senden eines Analytics-Ereignisses basierend auf der Fehlerantwort. Eine benutzerdefinierte Fehler-Handler-Funktion bietet die Flexibilität, die Fehlerbehandlung an die spezifischen Benutzeranforderungen anzupassen.

## Siehe auch {#see-also}

* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Erstellen von Stilen oder Designs für Ihre Formulare](/help/forms/using/create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)