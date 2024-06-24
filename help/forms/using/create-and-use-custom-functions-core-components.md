---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Fügen Sie eine benutzerdefinierte Funktion hinzu, verwenden Sie eine benutzerdefinierte Funktion, erstellen Sie eine benutzerdefinierte Funktion, verwenden Sie eine benutzerdefinierte Funktion im Regeleditor.
content-type: reference
feature: Adaptive Forms, Core Components
roles: Admin, Developer
exl-id: 00073e3a-f1b5-4c42-9fea-4a14b8a22c81
source-git-commit: 6c902ca08b7689e428facdc4150f443dad089bff
workflow-type: tm+mt
source-wordcount: '3385'
ht-degree: 5%

---

# Benutzerdefinierte Funktionen in adaptiven Forms-Kernkomponenten

In diesem Artikel wird das Erstellen benutzerdefinierter Funktionen mit der neuesten Kernkomponente für adaptive Formulare beschrieben, die die neuesten Funktionen aufweist, z. B.:

* Caching-Funktion für benutzerdefinierte Funktionen
* Globale Unterstützung von Objekt- und Feldobjekten für benutzerdefinierte Funktionen
* Unterstützung für moderne JavaScript-Funktionen wie let- und pfeile Funktionen (ES10-Unterstützung)

Stellen Sie sicher, dass [aktuelle Formularversion](https://github.com/adobe/aem-core-forms-components/tree/release/650) in Ihrer AEM Forms-Kernkomponentenumgebung verwenden, um die neuesten Funktionen in benutzerdefinierten Funktionen zu verwenden. </span>


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | Dieser Artikel |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/create-and-use-custom-functions) |

## Einführung

AEM Forms 6.5 enthält JavaScript-Funktionen, mit denen Sie mithilfe des Regeleditors komplexe Geschäftsregeln definieren können. AEM Forms bietet eine Vielzahl vordefinierter Funktionen, für die jedoch in vielen Fällen benutzerdefinierte Funktionen definiert werden müssen, damit sie in mehreren Formularen verwendet werden können. Diese benutzerdefinierten Funktionen verbessern die Funktionen von Formularen, indem sie die Bearbeitung und Verarbeitung der eingegebenen Daten ermöglichen, um bestimmten Anforderungen gerecht zu werden. Darüber hinaus ermöglichen sie eine dynamische Änderung des Formularverhaltens basierend auf den vordefinierten Kriterien.

### Verwendung benutzerdefinierter Funktionen {#uses-of-custom-function}

Vorteile der Verwendung benutzerdefinierter Funktionen in adaptiven Forms-Kernkomponenten sind:


* **Daten verwalten**: Benutzerdefinierte Funktionen verwalten und verarbeiten die in die Formularfelder eingegebenen Daten.
* **Datenverarbeitung**: Benutzerdefinierte Funktionen helfen bei der Verarbeitung der in die Formularfelder eingegebenen Daten.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen von Formulareingaben durchzuführen und bestimmte Fehlermeldungen bereitzustellen.
* **Dynamisches Verhalten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen zu steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies hilft beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen basierend auf externen Ereignissen.

Benutzerdefinierte Funktionen sind im Wesentlichen Client-Bibliotheken, die in der JavaScript-Datei hinzugefügt werden. Nachdem Sie eine benutzerdefinierte Funktion erstellt haben, steht sie im Regeleditor zur Auswahl durch den Benutzer in einem adaptiven Formular zur Verfügung. Die benutzerdefinierten Funktionen werden durch die JavaScript-Anmerkungen im Regeleditor identifiziert.

### Unterstützte JavaScript-Anmerkungen für benutzerdefinierte Funktionen {#js-annotations}

**JavaScript-Anmerkungen bieten Metadaten für JavaScript-Code**. Es enthält Kommentare, die mit bestimmten Symbolen beginnen, z. B. `/**` und `@`. Die Anmerkungen enthalten wichtige Informationen zu Funktionen, Variablen und anderen Elementen im Code. Das adaptive Formular unterstützt die folgenden JavaScript-Anmerkungen für benutzerdefinierte Funktionen:

#### Name

Die **Name** wird verwendet, um die benutzerdefinierte Funktion im Regeleditor eines adaptiven Formulars zu identifizieren. Die folgenden Syntaxen werden verwendet, um eine benutzerdefinierte Funktion zu benennen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`

>[!NOTE]
>`[functionName]` ist der Name der Funktion. Leerzeichen sind nicht zulässig.
>`<Function Name>` ist der Anzeigename der Funktion im Regeleditor von Adaptive Forms.
>Wenn der Name der Funktion mit dem Namen der Funktion selbst übereinstimmt, können Sie `[functionName]` aus der Syntax.

#### Parameter

Die **Parameter** ist eine Liste von Argumenten, die von benutzerdefinierten Funktionen verwendet werden. Eine Funktion kann mehrere Parameter unterstützen. Die folgenden Syntaxen werden verwendet, um einen Parameter in einer benutzerdefinierten Funktion zu definieren:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`

  `{type}` stellt den Parametertyp dar. Zulässige Parametertypen sind:

   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * Zeichenfolge[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt ein an eine benutzerdefinierte Funktion übergebenes Formularobjekt dar, anstatt dessen Wert direkt weiterzugeben.
   * scope: Stellt das global -Objekt dar, das schreibgeschützte Variablen wie Formularinstanzen, Zielfeldinstanzen und Methoden zum Ausführen von Formularänderungen innerhalb der benutzerdefinierten Funktionen enthält. Sie wird als letzter Parameter in den JavaScript-Anmerkungen deklariert und ist für den Regeleditor eines adaptiven Formulars nicht sichtbar. Der Parameter scope greift auf das Objekt des Formulars oder der Komponente zu, um die für die Formularverarbeitung erforderliche Regel oder das Ereignis Trigger. Weitere Informationen zum Globals-Objekt und dessen Verwendung finden Sie unter [Klicken Sie hier](/help/forms/using/create-and-use-custom-functions-core-components.md#field-and-global-scope-objects-in-custom-functions-support-field-and-global-objects)

Der Parametertyp lautet **nicht zwischen Groß- und Kleinschreibung unterscheiden** und Leerzeichen sind im Parameternamen nicht zulässig.

`<Parameter Description>` enthält Details zum Zweck des Parameters. Es kann mehrere Wörter enthalten.

<!--

**Optional Parameters**
By default, all parameters are mandatory. You can define a parameter as optional by either adding `=` after the parameter type or enclosing the parameter name in `[]`. Parameters defined as optional in JavaScript annotations are displayed as optional in the rule editor.
To define a variable as an optional parameter, you can use the any of the following syntaxes:
  
* `@param {type=} Input1`

In the above line of code, `Input1` is an optional parameter without any default value. To declare optional parameter with default value:

`@param {string=<value>} input1`
        
`input1` as an optional parameter with the default value set to `value`. 

* `@param {type} [Input1]`

In the above line of code, `Input1` is an optional parameter without any default value. To declare optional parameter with default value:

`@param {array} [input1=<value>]`

    `input1` is an optional parameter of array type with the default value set to `value`. 
    Ensure that the parameter type is enclosed in curly brackets {} and the parameter name is enclosed in square brackets []. 

Consider the following code snippet, where input2 is defined as an optional parameter:

```javascript

        /**
         * optional parameter function
         * @name OptionalParameterFunction
         * @param {string} input1 
         * @param {string=} input2 
         * @return {string}
        */
        function OptionalParameterFunction(input1, input2) {
        let result = "Result: ";
        result += input1;
        if (input2 !== null) {
            result += " " + input2;
        }
        return result;
        }
```

The following illustration displays using the `OptionalParameterFunction` csutom function in the rule editor:

![Optional or required parameters ](/help/forms/using/assets/optional-default-params.png)

You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

![incomplete rule warning](/help/forms/using/assets/incomplete-rule.png)

When user leaves the optional parameter empty, then the "Undefined" value is passed to the custom function for the optional parameter.

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

-->

#### Rückgabetyp

Der Rückgabetyp gibt den Typ des Werts an, den die benutzerdefinierte Funktion nach der Ausführung zurückgibt. Die folgenden Syntaxen werden verwendet, um einen Rückgabetyp in einer benutzerdefinierten Funktion zu definieren:

* `@return {type}`
* `@returns {type}`
  `{type}` stellt den Rückgabetyp der Funktion dar. Zulässige Rückgabetypen sind:
* string: Stellt einen einzelnen Zeichenfolgenwert dar.
* number: Stellt einen einzelnen numerischen Wert dar.
* boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
* Zeichenfolge[]: Stellt ein Array von Zeichenfolgenwerten dar.
* number[]: Stellt ein Array numerischer Werte dar.
* boolean[]: Stellt ein Array boolescher Werte dar.
* date: Stellt einen einzelnen Datumswert dar.
* date[]: Stellt ein Array von Datumswerten dar.
* array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
* object: Stellt direkt das Formularobjekt anstelle des Werts dar.

Beim Rückgabetyp wird nicht zwischen Groß- und Kleinschreibung unterschieden.

#### Privat

Die als privat deklarierte benutzerdefinierte Funktion wird nicht in der Liste der benutzerdefinierten Funktionen im Regeleditor eines adaptiven Formulars angezeigt. Standardmäßig sind benutzerdefinierte Funktionen öffentlich. Die Syntax zum Deklarieren der benutzerdefinierten Funktion als privat lautet `@private`.

<!--
#### Member

  Syntax: `@memberof namespace`
  Attaches a namespace to the function.
-->

<!--

#### This

   Syntax: `@this currentComponent`

   Use @this to refer to the Adaptive Form component on which the rule is written. 
  
   The following example is based on the field value. In the following example, the rule hides a field in the form. The `this` portion of `this.value` refers to underlying Adaptive Form component, on which the rule is written.

   ```
      /**
      * @function myTestFunction
      * @this currentComponent
      * @param {scope} scope in which code inside function will be executed.
      */
      myTestFunction = function (scope) {
         if(this.value == "O"){
               scope.age.visible = true;
         } else {
            scope.age.visible = false;
         }
      }

   ```

    >[!NOTE]
    >
    >Comments before custom function are used for summary. Summary can extend to multiple lines until a tag is encountered. Limit the size to a single for a concise description in the rule builder.

-->

<!--

## Function declaration supported types {#function-declaration-supported-types}

**Function Statement**

```javascript
function area(len) {
    return len*len;
}
```

This function is included without `jsdoc` comments.

**Function Expression**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Function Expression and Statement**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Function Declaration as Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Limitation: custom function picks only the first function declaration from the variable list, if together. You can use function expression for every function declared.

**Function Declaration as Object**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```
-->

## Richtlinien beim Erstellen benutzerdefinierter Funktionen {#considerations}

Um die benutzerdefinierten Funktionen im Regeleditor aufzulisten, können Sie eines der folgenden Formate verwenden:

### Funktionsanweisung mit oder ohne jsdoc-Kommentare

Sie können eine benutzerdefinierte Funktion mit oder ohne jsdoc-Kommentare erstellen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```

Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird sie im Regeleditor anhand ihres Funktionsnamens aufgelistet. Es wird jedoch empfohlen, JavaScript-Anmerkungen einzufügen, um die Lesbarkeit der benutzerdefinierten Funktionen zu verbessern.


### Pfeilfunktion mit obligatorischen JavaScript-Anmerkungen oder Kommentaren

Sie können eine benutzerdefinierte Funktion mit einer Pfeilfunktionssyntax erstellen:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Funktionsausdruck mit obligatorischen JavaScript-Anmerkungen oder Kommentaren

Um benutzerdefinierte Funktionen im Regeleditor eines adaptiven Formulars aufzulisten, erstellen Sie benutzerdefinierte Funktionen im folgenden Format:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Voraussetzungen für die Erstellung einer benutzerdefinierten Funktion

Bevor Sie mit dem Hinzufügen einer benutzerdefinierten Funktion zu Ihrem adaptiven Forms beginnen, stellen Sie sicher, dass Sie die folgende Software auf Ihrem Computer installiert haben:

* **Klartext-Editor (IDE)**: Obwohl jeder Nur-Text-Editor funktionieren kann, bietet eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code erweiterte Funktionen zur einfacheren Bearbeitung.

* **Git:** Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie es nicht installiert haben, laden Sie es von https://git-scm.com herunter.


## Erstellen einer benutzerdefinierten Funktion {#create-custom-function}

Schritte zum Erstellen benutzerdefinierter Funktionen:
1. [Erstellen Sie eine Client-seitige Bibliothek mithilfe des AEM Projektarchetyps und fügen Sie eine benutzerdefinierte Funktion hinzu.](#create-client-library-archetype)
ODER
   [Erstellen benutzerdefinierter Funktionen über CRXDE](#create-add-custom-function)
1. [Clientbibliothek zu einem adaptiven Formular hinzufügen](#add-client-library)
1. [Verwenden der benutzerdefinierten Funktion in einem adaptiven Formular](#use-custom-functions)


### Erstellen einer Client-Bibliothek mithilfe des AEM Projektarchetyps{#create-client-library-archetype}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie dem erstellten Projekt eine Client-Bibliothek hinzufügen [Verwenden des AEM Projektarchetyps](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using#getting-started).
Wenn Sie ein vorhandenes Projekt haben <!--and have already the project structure as shown in the image below,--> Sie können [benutzerdefinierte Funktionen](#create-add-custom-function) zu Ihrem lokalen Projekt hinzufügen.

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->

Nachdem Sie ein Archetypprojekt erstellt oder ein vorhandenes Projekt verwendet haben, erstellen Sie eine Client-Bibliothek. So erstellen Sie eine Client-Bibliothek:

**Client-Bibliotheksordner hinzufügen**

So fügen Sie einen neuen Client-Bibliotheksordner zu Ihrem [AEM Projektverzeichnis]führen Sie die folgenden Schritte aus:

1. Öffnen Sie die [AEM Projektverzeichnis] in einem Editor.

   ![Ordnerstruktur für benutzerdefinierte Funktionen](assets/custom-library-folder-structure.png)

1. Suchen `ui.apps`.
1. Fügen Sie neuen Ordner hinzu. Fügen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Navigieren Sie zu `/experience-league/` und fügen Sie einen `ClientLibraryFolder`. Erstellen Sie beispielsweise einen Client-Bibliotheksordner mit dem Namen `customclientlibs`.

   Speicherort ist: `[AEM project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Hinzufügen von Dateien und Ordnern zum Ordner &quot;Client-Bibliothek&quot;**

Fügen Sie dem hinzugefügten Client-Bibliotheksordner Folgendes hinzu:

* Datei `.content.xml`
* Datei `js.txt`
* `js` Ordner

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Im `.content.xml` die folgenden Codezeilen hinzufügen:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen für `client library folder` und `categories` -Eigenschaft.

1. Im `js.txt` die folgenden Codezeilen hinzufügen:

   ```javascript
         #base=js
       function.js
   ```

1. Im `js` Ordner, fügen Sie die JavaScript-Datei als `function.js` , das die benutzerdefinierten Funktionen enthält:

   ```javascript
   /**
       * Calculates Age
       * @name calculateAge
       * @param {object} field
       * @return {string} 
   */
   
   function calculateAge(field) {
   var dob = new Date(field);
   var now = new Date();
   
   var age = now.getFullYear() - dob.getFullYear();
   var monthDiff = now.getMonth() - dob.getMonth();
   
   if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
   age--;
   }
   
   return age;
   }
   ```

1. Speichern Sie die Dateien.

![Ordnerstruktur für benutzerdefinierte Funktionen](assets/custom-function-added-files.png)

**Den neuen Ordner in filter.xml einschließen**:

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   `<filter root="/apps/experience-league" />`
1. Speichern Sie die Datei.

   ![Benutzerdefinierte Funktionsfilter XML](assets/custom-function-filterxml.png)

1. Erstellen Sie den neu erstellten Client-Bibliotheksordner in Ihrer AEM-Umgebung, indem Sie die Schritte unter [Abschnitt &quot;Erstellen&quot;](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype#how-to-build).

## Erstellen und Bereitstellen benutzerdefinierter Funktionen über CRXDE{#create-add-custom-function}

Wenn Sie das neueste AEM Forms- und Forms-Add-on verwenden, können Sie über CRXDE eine benutzerdefinierte Funktion erstellen, um die neuesten Aktualisierungen benutzerdefinierter Funktionen zu verwenden. Führen Sie dazu die folgenden Schritte aus:

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->


1. Melden Sie sich bei `http://server:port/crx/de/index.jsp#` an.
1. Erstellen Sie einen Ordner unter dem Ordner `/apps`. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Speichern Sie Ihre Änderungen.
1. Navigieren Sie zum erstellten Ordner und erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` als `clientlibs`.
1. Navigieren Sie zum neu erstellten Ordner `clientlibs` und fügen Sie die Eigenschaften `allowProxy` und `categories` hinzu:

   ![Eigenschaften von benutzerdefinierten Bibliotheksknoten](/help/forms/using/assets/customlibrary-catproperties.png)

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen anstelle von `customfunctionsdemo` verwenden.

1. Speichern Sie Ihre Änderungen.

1. Erstellen Sie einen Ordner mit dem Namen `js` unter dem Ordner `clientlibs`.
1. Erstellen Sie eine JavaScript-Datei mit dem Namen `functions.js` unter `js` Ordner.
1. Erstellen Sie eine Datei mit dem Namen `js.txt` unter dem Ordner `clientlibs`.
1. Speichern Sie Ihre Änderungen.
Die erstellte Ordnerstruktur sieht wie folgt aus:

   ![Erstellte Ordnerstruktur der Client-Bibliothek](/help/forms/using/assets/clientlibrary_folderstructure.png)
1. Doppelklicken Sie auf die Datei `functions.js`, um den Editor zu öffnen. Die Datei enthält den Code für die benutzerdefinierte Funktion.
Fügen wir den folgenden Code zur JavaScript-Datei hinzu, um das Alter basierend auf dem Geburtsdatum (JJJJ-MM-TT) zu berechnen.

   ```javascript
       /**
            * Calculates Age
            * @name calculateAge 
            * @return {string} 
       */
   
       function calculateAge(dateOfBirthString) {
       var dob = new Date(dateOfBirthString);
       var now = new Date();
   
       var age = now.getFullYear() - dob.getFullYear();
       var monthDiff = now.getMonth() - dob.getMonth();
   
       if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
       age--;
       }
   
       return age;
       }
   ```

1. Speichern `function.js`.
1. Navigieren Sie zu `js.txt` und fügen Sie den folgenden Code hinzu:

   ```javascript
       #base=js
       functions.js
   ```

1. Speichern Sie die Datei `js.txt`.

Sie können auf Folgendes verweisen: [benutzerdefinierte Funktion](/help/forms/using/assets/customfunction.zip) Ordner. Laden Sie diesen Ordner herunter und installieren Sie ihn auf Ihrer AEM.

Jetzt können Sie die benutzerdefinierte Funktion in Ihrem adaptiven Formular verwenden, indem Sie die Client-Bibliothek hinzufügen.

## Clientbibliothek in einem adaptiven Formular hinzufügen{#add-client-library}

Nachdem Sie Ihre Client-Bibliothek in Ihrer AEM Forms-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zum adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol Eigenschaften des Guide-Containers. Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Allgemein]** und wählen Sie den Namen der **[!UICONTROL Client-Bibliothekskategorie]** aus der Dropdown-Liste aus (in diesem Fall wählen Sie `customfunctionscategory`).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Jetzt können Sie eine Regel erstellen, um benutzerdefinierte Funktionen im Regeleditor zu verwenden:

![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/calculateage-customfunction.png)

Jetzt sollten wir verstehen, wie eine benutzerdefinierte Funktion mithilfe der [Aufrufdienst des Regeleditors in AEM Forms 6.5](/help/forms/using/rule-editor-core-components.md#invoke-form-data-model-service-invoke)

## Verwenden der benutzerdefinierten Funktion in einem adaptiven Formular {#use-custom-functions}

In einem adaptiven Formular können Sie [Benutzerdefinierte Funktionen im Regeleditor](/help/forms/using/rule-editor-core-components.md).
Fügen Sie der JavaScript-Datei (`Function.js` ), um das Alter basierend auf dem Geburtsdatum (JJJ-MM-TT) zu berechnen. Erstellen Sie eine benutzerdefinierte Funktion als `calculateAge()` , das das Geburtsdatum als Eingabe annimmt und das Alter zurückgibt:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

Wenn der Benutzer im obigen Beispiel das Geburtsdatum im Format (JJJJ-MM-TT) eingibt, wird die benutzerdefinierte Funktion `calculateAge` aufgerufen wird und das Alter zurückgibt.

![Benutzerdefinierte Funktion &quot;Alter berechnen&quot;im Regeleditor](/help/forms/using/assets/custom-function-calculate-age.png)

Sehen wir uns das Formular in der Vorschau an, um zu sehen, wie die benutzerdefinierten Funktionen über den Regeleditor implementiert werden:

![Benutzerdefinierte Funktion &quot;Alter berechnen&quot;in der Formularvorschau des Regeleditors](/help/forms/using/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Sie können auf Folgendes verweisen: [benutzerdefinierte Funktionen](/help/forms/using/assets/customfunctions.zip) Ordner. Laden Sie diesen Ordner herunter und installieren Sie ihn in Ihrer AEM mithilfe der [Package Manager](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager).

### Unterstützung für asynchrone Funktionen in benutzerdefinierten Funktionen {#support-of-async-functions}

Asynchrone benutzerdefinierte Funktionen werden nicht in der Liste des Regeleditors angezeigt. Es ist jedoch möglich, asynchrone Funktionen innerhalb benutzerdefinierter Funktionen aufzurufen, die mit synchronen Funktionsausdrücken erstellt wurden.

![Benutzerdefinierte Funktion &quot;Synchronisieren und asynchron&quot;](/help/forms/using/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> Der Vorteil des Aufrufs asynchroner Funktionen in benutzerdefinierten Funktionen besteht darin, dass asynchrone Funktionen die gleichzeitige Ausführung mehrerer Aufgaben ermöglichen, wobei das Ergebnis jeder Funktion in den benutzerdefinierten Funktionen verwendet wird.

Im folgenden Code erfahren Sie, wie Sie asynchrone Funktionen mit benutzerdefinierten Funktionen aufrufen können:

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

Im obigen Beispiel ist die asyncFunction-Funktion ein `asynchronous function`. Er führt einen asynchronen Vorgang durch, indem er eine `GET` Anfrage an `https://petstore.swagger.io/v2/store/inventory`. Es wartet auf die Antwort mit `await`, analysiert den Antworttext mit der `response.json()`und gibt dann die Daten zurück. Die `callAsyncFunction` -Funktion ist eine synchrone benutzerdefinierte Funktion, die die `asyncFunction` und zeigt die Antwortdaten in der Konsole an. Obwohl die Variable `callAsyncFunction` -Funktion synchron ist, ruft sie die asynchrone asyncFunction-Funktion auf und verarbeitet ihr Ergebnis mit `then` und `catch` -Anweisungen.

Um seine Funktionsweise zu sehen, fügen wir eine Schaltfläche hinzu und erstellen eine Regel für die Schaltfläche, die die asynchrone Funktion bei einem Klick auf eine Schaltfläche aufruft.

![Erstellen einer Regel für die asynchrone Funktion](/help/forms/using/assets/rule-for-async-funct.png)

In der Abbildung unten sehen Sie das Konsolenfenster, um zu veranschaulichen, dass der Benutzer beim Klicken auf die `Fetch` Schaltfläche, die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, was wiederum eine asynchrone Funktion aufruft `asyncFunction`. Inspect Sie das Konsolenfenster, um die Antwort anzuzeigen, wenn Sie auf die Schaltfläche klicken:

![Konsolenfenster](/help/forms/using/assets/async-custom-funct-console.png)

Im Folgenden werden die Funktionen von benutzerdefinierten Funktionen vorgestellt.

## Verschiedene Funktionen für benutzerdefinierte Funktionen

Sie können benutzerdefinierte Funktionen verwenden, um Formularen personalisierte Funktionen hinzuzufügen. Diese Funktionen unterstützen verschiedene Funktionen, wie z. B. das Arbeiten mit bestimmten Feldern, das Verwenden globaler Felder oder das Zwischenspeichern. Diese Flexibilität ermöglicht es Ihnen, Formulare entsprechend den Anforderungen Ihres Unternehmens anzupassen.

### Felder und globale Perimeter in benutzerdefinierten Funktionen {#support-field-and-global-objects}

Feldobjekte beziehen sich auf die einzelnen Komponenten oder Elemente in einem Formular, z. B. Textfelder und Kontrollkästchen. Das Globals -Objekt enthält schreibgeschützte Variablen wie Formularinstanz, Zielfeldinstanz und Methoden zum Durchführen von Formularänderungen in benutzerdefinierten Funktionen.

>[!NOTE]
>
> Die `param {scope} globals` muss der letzte Parameter sein und wird nicht im Regeleditor eines adaptiven Formulars angezeigt.

<!-- Let us look at the following code snippet:

```JavaScript
   
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

Erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` Formulare mit unterschiedlichen Anwendungsfällen verwenden.

![Kontaktformular](/help/forms/using/assets/contact-us-form.png)

#### **Anwendungsfall**: Zeigen Sie ein Bedienfeld mit dem `SetProperty` Regel

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) Abschnitt, um das Formularfeld als `Required`.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> * Sie können die Feldeigenschaften mit den verfügbaren Eigenschaften konfigurieren, die sich unter `[form-path]/jcr:content/guideContainer.model.json`.
> * Änderungen am Formular, die mithilfe des `setProperty` -Methode des Globals-Objekts sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird die `personaldetails` angezeigt, wenn auf die Schaltfläche geklickt wird. Wenn im Bedienfeld keine Fehler erkannt werden, wird in einem anderen Bedienfeld die `feedback` -Bedienfeld angezeigt, wird beim Klicken auf die Schaltfläche sichtbar.

Erstellen wir eine Regel für die `Next` -Schaltfläche, mit der die `personaldetails` und erstellt die `feedback`  Bereich, der angezeigt wird, wenn der Benutzer auf die `Next` Schaltfläche.

![Eigenschaft festlegen](/help/forms/using/assets/custom-function-set-property.png)

In der folgenden Abbildung erfahren Sie, wo die Variable `personaldetails` beim Klicken auf `Next` Schaltfläche. Für alle Felder im `personaldetails` validiert werden, wird die `feedback` -Bedienfeld wird angezeigt.

![Festlegen der Eigenschaftenformularvorschau](/help/forms/using/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern der Variablen `personaldetails` angezeigt werden, werden sie beim Klicken auf die `Next` und der `feedback` bleibt unsichtbar.

![Festlegen der Eigenschaftenformularvorschau](/help/forms/using/assets/set-property-panel.png)

#### **Anwendungsfall**: Validieren Sie das Feld.

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um das Feld zu validieren.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> Wenn kein -Argument übergeben wird, wird die `validate()` -Funktion, validiert sie das Formular.

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf die `contact` -Feld. Benutzer müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern. Wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` oder enthält mehr oder weniger als `8` Ziffern angeben, wird beim Klicken auf die Schaltfläche eine Validierungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die `Next` -Schaltfläche, die die `contact` auf der Schaltfläche klicken.

![Überprüfungsmuster](/help/forms/using/assets/custom-function-validate.png)

Beachten Sie die folgende Abbildung, um zu zeigen, dass wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10`wird auf Feldebene eine Fehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/custom-function-validate-error-message.png)

Wenn der Benutzer eine gültige Telefonnummer und alle Felder in der `personaldetails` validiert werden, wird die `feedback` wird auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/validate-form-preview-form.png)

#### **Anwendungsfall**: Zurücksetzen eines Bedienfelds

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) -Abschnitt, um das Bedienfeld zurückzusetzen.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> Wenn kein -Argument übergeben wird, wird die `reset()` -Funktion, validiert sie das Formular.

In diesem Beispiel wird die `personaldetails` beim Klicken auf `Clear` Schaltfläche. Der nächste Schritt besteht darin, eine Regel für die `Clear` -Schaltfläche, mit der das Bedienfeld auf die Schaltfläche zurückgesetzt wird.

![Schaltfläche Löschen](/help/forms/using/assets/custom-function-reset-field.png)

Die folgende Abbildung zeigt, dass der Benutzer durch Klicken auf die `clear` -Schaltfläche, `personaldetails` Bedienfeld zurückgesetzt:

![Formular zurücksetzen](assets/custom-function-reset-form.png)

#### **Anwendungsfall**: So zeigen Sie benutzerdefinierte Nachrichten auf Feldebene an und kennzeichnen das Feld als ungültig

Sie können die `markFieldAsInvalid()` -Funktion, um ein Feld als ungültig zu definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festzulegen. Die `fieldIdentifier` Wert kann `fieldId`oder `field qualifiedName`oder `field dataRef`. Der Wert des Objekts mit dem Namen `option` kann `{useId: true}`, `{useQualifiedName: true}`oder `{useDataRef: true}`.
Die Syntaxen, die zum Markieren des Felds als ungültig und zum Festlegen der benutzerdefinierten Nachricht verwendet werden, sind:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

In diesem Beispiel wird eine benutzerdefinierte Meldung auf Feldebene angezeigt, wenn der Benutzer weniger als 15 Zeichen in das Textfeld &quot;Kommentare&quot;eingibt.

Der nächste Schritt besteht darin, eine Regel für die `comments` -Feld:

![Feld als ungültig markieren](/help/forms/using/assets/custom-function-invalid-field.png)

Sehen Sie sich die unten stehende Demonstration an, um anzuzeigen, dass negative Rückmeldungen im `comments` -Feld wird die Anzeige einer benutzerdefinierten Nachricht auf Feldebene Trigger:

![Feld als ungültiges Vorschauformular markieren](/help/forms/using/assets/custom-function-invalidfield-form.png)

Wenn der Benutzer mehr als 15 Zeichen in das Textfeld &quot;Kommentare&quot;eingibt, wird das Feld validiert und das Formular wird gesendet:

![Feld als gültiges Vorschauformular markieren](/help/forms/using/assets/custom-function-validfield-form.png)


#### **Anwendungsfall**: Sendet geänderte Daten an den Server

Die folgende Codezeile:
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument stellt dar, ob das Formular vor der Übermittlung validiert werden soll. Es ist `optional` und legen Sie `true` Standardmäßig.
* Das dritte Argument ist die `contentType` der Übermittlung, die ebenfalls optional ist, wobei der Standardwert als `multipart/form-data`. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded`.

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um die bearbeiteten Daten auf dem Server zu senden:

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */
    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

Wenn der Benutzer in diesem Beispiel die `comments` Textfeld leer, das `NA` wird beim Senden des Formulars an den Server gesendet.

Erstellen Sie nun eine Regel für die `Submit` -Schaltfläche zum Senden von Daten:

![Daten senden](/help/forms/using/assets/custom-function-submit-data.png)

Siehe Abbildung der `console window` unten, um zu zeigen, dass wenn der Benutzer die `comments` Textfeld leer, dann der Wert als `NA` wird auf dem Server gesendet:

![Daten im Konsolenfenster senden](/help/forms/using/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Inspect-Daten im Konsolenfenster](/help/forms/using/assets/custom-function-submit-data-console-data.png)

<!--

#### **Use Case**: Display form submission and failure messages for custom submit action 

Add the following line of code as explained in the [create-custom-function ](#create-custom-function) section, to customize the submission or failure message for form submissions and display the form submission messages in a modal box:

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

In this example, when the user uses the `customSubmitSuccessHandler` and `customSubmitErrorHandler` custom functions, the success and failure messages are displayed in a modal. The JavaScript function `showModal(type, message)` is used to dynamically create and display a modal dialog box on a screen.

Now, create a rule for successful form submission:

![Form submission success](/help/forms/using/assets/form-submission-success.png)

Refer to the illustration below to demonstrate that when the form is submitted successfully, the success message is displayed in a modal:

![Form submission success message](/help/forms/using/assets/form-submission-success-message.png )
 
Similarly, let us create a rule for failed form submissions:

![Form submission fail](/help/forms/using/assets/form-submission-fail.png)

Refer to the illustration below to demonstrate that when the form submission fails, the error message is displayed in a modal:

![Form submission fail message](/help/forms/using/assets/form-submission-fail-message.png )

To display form submission success and failure in a default manner, the `Default submit Form Success Handler` and `Default submit Form Error Handler` functions are available out of the box.

In case, the custom submit action fails to perform as expected in existing AEM projects or forms, refer to the [troubleshooting](#troubleshooting) section.

-->

## Caching-Unterstützung für benutzerdefinierte Funktionen

Adaptive Forms implementiert Caching für benutzerdefinierte Funktionen, um die Reaktionszeit beim Abrufen der benutzerdefinierten Funktionsliste im Regeleditor zu verkürzen. Eine Nachricht als `Fetched following custom functions list from cache` im `error.log` -Datei.

![benutzerdefinierte Funktion mit Cache-Unterstützung](/help/forms/using/assets/custom-function-cache-error.png)

Wenn die benutzerdefinierten Funktionen geändert werden, wird die Zwischenspeicherung invalidiert und analysiert.

## Fehlerbehebung {#troubleshooting}

* Der Benutzer muss sicherstellen, dass die [Kernkomponente und Spezifikationsversion auf die neueste Version eingestellt](https://github.com/adobe/aem-core-forms-components/tree/release/650). Für bestehende AEM-Projekte und Formulare sind jedoch zusätzliche Schritte erforderlich:

   * Für das AEM Projekt sollte der Benutzer alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` mit `submitForm()` und stellen Sie das Projekt bereit.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht ordnungsgemäß funktionieren, muss der Benutzer die `submitForm` -Regel auf **Einsenden** -Schaltfläche mit dem Regeleditor. Diese Aktion ersetzt die vorhandene Regel aus `submitForm('custom:submitSuccess', 'custom:submitError')` mit `submitForm()` im Formular.


* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Um die Liste der benutzerdefinierten Funktionen zu überprüfen, können Sie zum `error.log` -Datei für den Fehler. Im Fall eines Fehlers wird die Liste der benutzerdefinierten Funktionen leer angezeigt:

  ![Fehlerprotokolldatei](/help/forms/using/assets/custom-function-list-error-file.png)

  Wenn kein Fehler auftritt, wird die benutzerdefinierte Funktion abgerufen und im `error.log` -Datei. Eine Nachricht als `Fetched following custom functions list` im `error.log` Datei:

  ![Fehlerprotokolldatei mit entsprechender benutzerdefinierter Funktion](/help/forms/using/assets/custom-function-list-fetched-in-error.png)

## Überlegungen

* Die `parameter type` und `return type` nicht unterstützen `None`.

* Folgende Funktionen werden in der benutzerdefinierten Funktionsliste nicht unterstützt:
   * Generator-Funktionen
   * Async/Await-Funktionen
   * Methodendefinitionen
   * Klassenmethoden
   * Standardparameter
   * REST-Parameter
