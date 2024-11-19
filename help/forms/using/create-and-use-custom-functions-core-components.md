---
title: Erstellen und Hinzufügen von benutzerdefinierten Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, sodass Benutzende eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Im Regeleditor können Sie eine benutzerdefinierte Funktion hinzufügen, eine benutzerdefinierte Funktion verwenden, eine benutzerdefinierte Funktion erstellen oder eine benutzerdefinierte Funktion verwenden.
content-type: reference
feature: Adaptive Forms, Core Components
role: Admin, User, Developer
exl-id: 00073e3a-f1b5-4c42-9fea-4a14b8a22c81
source-git-commit: 7f1283898cbeebdedb7bdea6f0a8d9db567617ee
workflow-type: ht
source-wordcount: '3385'
ht-degree: 100%

---

# Benutzerdefinierte Funktionen in Kernkomponenten für adaptive Formulare

In diesem Artikel wird das Erstellen benutzerdefinierter Funktionen mit der neuesten Kernkomponente für adaptive Formulare beschrieben, die die aktuellsten Funktionen aufweist, z. B.:

* Caching-Funktion für benutzerdefinierte Funktionen
* Globale Unterstützung von Objekt- und Feldobjekten für benutzerdefinierte Funktionen
* Unterstützung für moderne JavaScript-Funktionen wie Let- und Pfeil-Funktionen (ES10-Unterstützung)

Stellen Sie sicher, dass die [neueste Formularversion](https://github.com/adobe/aem-core-forms-components/tree/release/650) in Ihrer AEM Forms-Kernkomponentenumgebung festgelegt ist, damit Sie die neuesten Features in benutzerdefinierten Funktionen verwenden können. </span>


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | Dieser Artikel |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/create-and-use-custom-functions) |

## Einführung

AEM Forms 6.5 umfasst JavaScript-Funktionen, mit denen Sie mithilfe des Regeleditors komplexe Geschäftsregeln definieren können. AEM Forms bietet verschiedene vordefinierte Funktionen, für die jedoch in vielen Fällen benutzerdefinierte Funktionen definiert werden müssen, damit sie in mehreren Formularen verwendet werden können. Diese benutzerdefinierten Funktionen erweitern die Möglichkeiten von Formularen, indem sie die Be- und Verarbeitung von eingegebenen Daten ermöglichen, wenn spezifische Anforderungen erfüllt werden sollen. Darüber hinaus ermöglichen sie dynamische Veränderungen des Formularverhaltens basierend auf den vordefinierten Kriterien.

### Vorteile benutzerdefinierter Funktionen {#uses-of-custom-function}

Vorteile der Verwendung benutzerdefinierter Funktionen in Kernkomponenten für adaptive Formulare sind:


* **Datenverwaltung**: Benutzerdefinierte Funktionen helfen beim Verwalten und Verarbeiten der Daten, die in die Formularfelder eingegeben wurden.
* **Datenverarbeitung**: Benutzerdefinierte Funktionen helfen bei der Verarbeitung der in die Formularfelder eingegebenen Daten.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen Ihnen benutzerdefinierte Überprüfungen von Formulareingaben und das Anzeigen bestimmter Fehlermeldungen.
* **Dynamisches Verhalten**: Mit benutzerdefinierten Funktionen können Sie das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies ist hilfreich beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen entsprechend externer Ereignisse.

Benutzerdefinierte Funktionen sind im Wesentlichen Client-Bibliotheken, die in der JavaScript-Datei hinzugefügt werden. Nachdem Sie eine benutzerdefinierte Funktion erstellt haben, steht sie im Regeleditor zur Auswahl durch Benutzende in einem adaptiven Formular zur Verfügung. Die benutzerdefinierten Funktionen sind im Regeleditor anhand der JavaScript-Anmerkungen zu erkennen.

### Unterstützte JavaScript-Anmerkungen für benutzerdefinierte Funktionen {#js-annotations}

**JavaScript-Anmerkungen bieten Metadaten für JavaScript-Code**. Dies schließt Kommentare ein, die mit bestimmten Symbolen beginnen, z. B. `/**` und `@`. Die Anmerkungen enthalten wichtige Informationen zu Funktionen, Variablen und anderen Elementen im Code. Adaptive Formulare unterstützen die folgenden JavaScript-Anmerkungen für benutzerdefinierte Funktionen:

#### Name

Der **Name** wird verwendet, um die benutzerdefinierte Funktion im Regeleditor eines adaptiven Formulars zu erkennen. Die folgenden Syntaxen werden verwendet, um eine benutzerdefinierte Funktion zu benennen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`

>[!NOTE]
>`[functionName]` ist der Name der Funktion. Leerzeichen sind nicht zulässig.
>`<Function Name>` ist der Anzeigename der Funktion im Regeleditor von adaptiven Formularen.
>Wenn der Anzeigename der Funktion mit dem Namen der Funktion selbst übereinstimmt, können Sie in der Syntax `[functionName]` weglassen.

#### Parameter

Der **Parameter** ist eine Liste von Argumenten, die von benutzerdefinierten Funktionen verwendet werden. Eine Funktion kann mehrere Parameter unterstützen. Die folgenden Syntaxen werden verwendet, um einen Parameter in einer benutzerdefinierten Funktion zu definieren:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`

  `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * string[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt ein an eine benutzerdefinierte Funktion übergebenes Formularobjekt dar, anstatt dessen Wert direkt weiterzugeben.
   * scope: Stellt das globals-Objekt dar, das schreibgeschützte Variablen wie Formularinstanzen, Zielfeldinstanzen und Methoden zum Ausführen von Formularänderungen innerhalb der benutzerdefinierten Funktionen enthält. Es wird als letzter Parameter in den JavaScript-Anmerkungen deklariert und ist für den Regeleditor eines adaptiven Formulars nicht sichtbar. Der Parameter „scope“ greift auf das Objekt des Formulars oder der Komponente zu, um die für die Formularverarbeitung erforderliche Regel oder das Ereignis auszulösen. Um weitere Informationen zum globals-Objekt und dessen Verwendung zu erhalten, [klicken Sie hier](/help/forms/using/create-and-use-custom-functions-core-components.md#field-and-global-scope-objects-in-custom-functions-support-field-and-global-objects).

Beim Parametertyp **wird nicht zwischen Groß- und Kleinschreibung unterschieden** und Leerzeichen sind im Parameternamen nicht zulässig.

`<Parameter Description>` enthält Details zum Zweck des Parameters. Dies kann aus mehreren Wörtern bestehen.

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
  `{type}` gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:
* string: Stellt einen einzelnen Zeichenfolgenwert dar.
* number: Stellt einen einzelnen numerischen Wert dar.
* boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
* string[]: Stellt ein Array von Zeichenfolgenwerten dar.
* number[]: Stellt ein Array von numerischen Werten dar.
* boolean[]: Stellt ein Array von booleschen Werten dar.
* date: Stellt einen einzelnen Datumswert dar.
* date[]: Stellt ein Array von Datumswerten dar.
* array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
* object: Stellt das Formularobjekt anstatt direkt den Wert dar.

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

Wenn Benutzende zu einer benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird sie im Regeleditor anhand ihres Funktionsnamens aufgelistet. Es wird jedoch empfohlen, JavaScript-Anmerkungen einzubeziehen, um die Lesbarkeit der benutzerdefinierten Funktionen zu verbessern.


### Pfeilfunktion mit obligatorischen JavaScript-Anmerkungen oder -Kommentaren

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

Wenn Benutzende der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Funktionsausdruck mit obligatorischen JavaScript-Anmerkungen oder -Kommentaren

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

Wenn Benutzende der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Voraussetzungen zum Erstellen einer benutzerdefinierten Funktion.

Bevor Sie mit dem Hinzufügen einer benutzerdefinierten Funktion zu Ihrem adaptiven Formular beginnen, stellen Sie sicher, dass Sie die folgende Software auf Ihrem Computer installiert haben:

* **Nur-Text-Editor (IDE)**: Zwar kann jeder einfache Nur-Text-Editor verwendet werden, aber eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code bietet erweiterte Funktionen für eine einfachere Bearbeitung.

* **Git:**: Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie nicht über das Programm verfügen, laden Sie es von https://git-scm.com herunter.


## Erstellen einer benutzerdefinierten Funktion {#create-custom-function}

Die Schritte zum Erstellen benutzerdefinierter Funktionen sind die Folgenden:
1. [Erstellen einer Client-seitigen Bibliothek mit dem AEM-Projektarchetyp und Hinzufügen einer benutzerdefinierten Funktion](#create-client-library-archetype)
ODER
   [Erstellen benutzerdefinierter Funktionen über CRXDE](#create-add-custom-function)
1. [Hinzufügen einer Client-Bibliothek zu einem adaptiven Formular](#add-client-library)
1. [Verwenden einer benutzerdefinierten Funktion in einem adaptiven Formular](#use-custom-functions)


### Erstellen einer Client-Bibliothek mit dem AEM-Projektarchetyp{#create-client-library-archetype}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie [unter Verwendung des AEM-Projektarchetyps](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/using#getting-started) eine Client-Bibliothek zu dem erstellten Projekt hinzufügen.
Wenn Sie über ein vorhandenes Projekt verfügen <!--and have already the project structure as shown in the image below,-->, können Sie Ihrem lokalen Projekt direkt [benutzerdefinierte Funktionen](#create-add-custom-function) hinzufügen.

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->

Nachdem Sie ein Archetypprojekt erstellt oder ein vorhandenes Projekt verwendet haben, erstellen Sie eine Client-Bibliothek. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

**Hinzufügen eines Client-Bibliotheksordners**

Gehen Sie wie folgt vor, um einen neuen Client-Bibliotheksordner zu Ihrem [AEM-Projektverzeichnis] hinzuzufügen:

1. Öffnen Sie das [AEM-Projektverzeichnis] in einem Editor.

   ![Ordnerstruktur der benutzerdefinierten Funktion](assets/custom-library-folder-structure.png)

1. Suchen Sie `ui.apps`.
1. Fügen Sie einen neuen Ordner hinzu. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Navigieren Sie zum Ordner `/experience-league/` und fügen Sie einen `ClientLibraryFolder` hinzu. Erstellen Sie beispielsweise einen Client-Bibliotheksordner mit dem Namen `customclientlibs`.

   Der Speicherort ist: `[AEM project directory]/ui.apps/src/main/content/jcr_root/apps/`.

**Hinzufügen von Dateien und Ordnern zum Client-Bibliotheksordner**

Fügen Sie dem hinzugefügten Client-Bibliotheksordner Folgendes hinzu:

* Datei `.content.xml`
* Datei `js.txt`
* Ordner `js`

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Fügen Sie in `.content.xml` die folgenden Code-Zeilen hinzu:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Sie können für die Eigenschaften `client library folder` und `categories` beliebige Namen auswählen.

1. Fügen Sie in `js.txt` die folgenden Code-Zeilen hinzu:

   ```javascript
         #base=js
       function.js
   ```

1. Fügen Sie im Ordner `js` die JavaScript-Datei, die die benutzerdefinierten Funktionen enthält, als `function.js` hinzu:

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

![Ordnerstruktur der benutzerdefinierten Funktionen](assets/custom-function-added-files.png)

**Schließen Sie den neuen Ordner in filter.xml ein**:

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   `<filter root="/apps/experience-league" />`
1. Speichern Sie die Datei.

   ![Benutzerdefinierte Funktion Filter XML](assets/custom-function-filterxml.png)

1. Erstellen Sie den neu erstellten Client-Bibliotheksordner in Ihrer AEM-Umgebung, indem Sie die Schritte im Abschnitt [Anleitung zum Erstellen](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype#how-to-build) befolgen.

## Erstellen und Bereitstellen benutzerdefinierter Funktionen über CRXDE{#create-add-custom-function}

Wenn Sie die aktuellsten Versionen von AEM Forms- und des Forms-Add-ons verwenden, können Sie über CRXDE eine benutzerdefinierte Funktion erstellen, um die neuesten Aktualisierungen von benutzerdefinierten Funktionen zu verwenden. Führen Sie dazu die folgenden Schritte aus:

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
1. Erstellen Sie eine JavaScript-Datei mit dem Namen `functions.js` unter dem Ordner `js`
1. Erstellen Sie eine Datei mit dem Namen `js.txt` unter dem Ordner `clientlibs`.
1. Speichern Sie Ihre Änderungen.
Die erstellte Ordnerstruktur sieht wie folgt aus:

   ![Erstellte Ordnerstruktur der Client-Bibliothek](/help/forms/using/assets/clientlibrary_folderstructure.png)
1. Doppelklicken Sie auf die Datei `functions.js`, um den Editor zu öffnen. Die Datei enthält den Code für die benutzerdefinierte Funktion.
Fügen wir der JavaScript-Datei den folgenden Code hinzu, um das Alter basierend auf dem Geburtsdatum (JJJJ-MM-TT) zu berechnen.

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

Sie können auf den folgenden Ordner [Benutzerdefinierte Funktion](/help/forms/using/assets/customfunction.zip) verweisen. Laden Sie diesen Ordner herunter und installieren Sie ihn in Ihrer AEM-Instanz.

Jetzt können Sie die benutzerdefinierte Funktion in Ihrem adaptiven Formular verwenden, indem Sie die Client-Bibliothek hinzufügen.

## Hinzufügen einer Client-Bibliothek in einem adaptiven Formular{#add-client-library}

Nachdem Sie Ihre Client-Bibliothek in Ihrer AEM Forms-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zu einem adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie dann **[!UICONTROL Bearbeiten]** aus.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol „Guide-Container-Eigenschaften“. Das Dialogfeld „Container für adaptive Formulare“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Einfach]** und wählen Sie den Namen der **[!UICONTROL Client-Bibliothekskategorie]** aus der Dropdown-Liste aus (in diesem Fall `customfunctionscategory`).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Jetzt können Sie eine Regel erstellen, um benutzerdefinierte Funktionen im Regeleditor zu verwenden:

![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/calculateage-customfunction.png)

Im Folgenden erfahren Sie, wie Sie einen benutzerdefinierten Fehler-Handler mit dem [Aufrufdienst des Regeleditors in AEM Forms 6.5](/help/forms/using/rule-editor-core-components.md#invoke-form-data-model-service-invoke) konfigurieren und verwenden.

## Verwenden von benutzerdefinierten Funktionen in einem adaptiven Formular. {#use-custom-functions}

In einem adaptiven Formular können Sie [benutzerdefinierte Funktionen im Regeleditor](/help/forms/using/rule-editor-core-components.md) verwenden.
Fügen Sie der JavaScript-Datei (`Function.js`) den folgenden Code hinzu, um das Alter basierend auf dem Geburtsdatum (JJJJ-MM-TT) zu berechnen. Erstellen Sie eine benutzerdefinierte Funktion als `calculateAge()`, die das Geburtsdatum als Eingabe annimmt und das Alter zurückgibt:

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

Wenn Benutzende im obigen Beispiel das Geburtsdatum im Format JJJJ-MM-TT eingeben, wird die benutzerdefinierte Funktion `calculateAge` aufgerufen und das Alter zurückgegeben.

![Benutzerdefinierte Funktion „Alter berechnen“ im Regeleditor](/help/forms/using/assets/custom-function-calculate-age.png)

Sehen wir uns das Formular in der Vorschau an, um zu sehen, wie die benutzerdefinierten Funktionen über den Regeleditor implementiert werden:

![Benutzerdefinierte Funktion „Alter berechnen“ in der Formularvorschau des Regeleditors](/help/forms/using/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Sie können auf den folgenden Ordner [Benutzerdefinierte Funktionen](/help/forms/using/assets/customfunctions.zip) verweisen. Laden Sie diesen Ordner herunter und installieren Sie ihn mithilfe von [Package Manager](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager) in Ihrer AEM-Instanz.

### Unterstützung für asynchrone Funktionen in benutzerdefinierten Funktionen {#support-of-async-functions}

Asynchrone benutzerdefinierte Funktionen werden nicht in der Liste des Regeleditors angezeigt. Es ist jedoch möglich, asynchrone Funktionen innerhalb benutzerdefinierter Funktionen aufzurufen, die mit synchronen Funktionsausdrücken erstellt wurden.

![Synchrone und asynchrone benutzerdefinierte Funktionen](/help/forms/using/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> Der Vorteil des Aufrufens asynchroner Funktionen in benutzerdefinierten Funktionen besteht darin, dass asynchrone Funktionen die gleichzeitige Ausführung mehrerer Aufgaben ermöglichen, wobei das Ergebnis jeder Funktion in den benutzerdefinierten Funktionen verwendet wird.

Sehen Sie sich den folgenden Code an, um zu erfahren, wie Sie asynchrone Funktionen mit benutzerdefinierten Funktionen aufrufen können:

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

Im obigen Beispiel ist die Funktion „asyncFunction“ eine `asynchronous function`. Sie führt einen asynchronen Vorgang durch, indem eine `GET`-Anfrage an `https://petstore.swagger.io/v2/store/inventory` gesendet wird. Sie wartet mit `await` auf die Antwort, analysiert den Antworttext mithilfe der `response.json()` als JSON und gibt dann die Daten zurück. Die Funktion `callAsyncFunction` ist eine synchrone benutzerdefinierte Funktion, die die Funktion `asyncFunction` aufruft und die Antwortdaten in der Konsole anzeigt. Obwohl die Funktion `callAsyncFunction` synchron ist, ruft sie die asynchrone Funktion „asyncFunction“ auf und verarbeitet ihr Ergebnis mit den Anweisungen `then` und `catch`.

Um ihre Funktionsweise zu sehen, fügen wir eine Schaltfläche hinzu und erstellen eine Regel für die Schaltfläche, die die asynchrone Funktion bei einem Klick auf eine Schaltfläche aufruft.

![Erstellen einer Regel für eine asynchrone Funktion](/help/forms/using/assets/rule-for-async-funct.png)

In der Abbildung unten finden Sie das Konsolenfenster, um zu zeigen, dass beim Klicken auf die Schaltfläche `Fetch` die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, die wiederum die asynchrone Funktion `asyncFunction` aufruft. Inspizieren Sie das Konsolenfenster, um die Antwort anzusehen, wenn Sie auf die Schaltfläche klicken:

![Konsolenfenster](/help/forms/using/assets/async-custom-funct-console.png)

Im Folgenden werden die Merkmale von benutzerdefinierten Funktionen vorgestellt.

## Verschiedene Merkmale von benutzerdefinierten Funktionen

Sie können benutzerdefinierte Funktionen verwenden, um personalisierte Merkmale zu Funktionen hinzuzufügen. Diese Funktionen unterstützen verschiedene Fähigkeiten, wie z. B. das Arbeiten mit bestimmten Feldern, das Verwenden globaler Felder oder das Zwischenspeichern. Diese Flexibilität ermöglicht es Ihnen, Formulare entsprechend den Anforderungen Ihres Unternehmens anzupassen.

### Objekte mit dem Gültigkeitsbereich „Feld“ und „Global“ in benutzerdefinierten Funktionen {#support-field-and-global-objects}

Feldobjekte beziehen sich auf die einzelnen Komponenten oder Elemente in einem Formular, z. B. Textfelder und Kontrollkästchen. Das Globals-Objekt enthält schreibgeschützte Variablen wie Formularinstanz, Zielfeldinstanz und Methoden zum Durchführen von Formularänderungen in benutzerdefinierten Funktionen.

>[!NOTE]
>
> Der `param {scope} globals` muss der letzte Parameter sein und wird nicht im Regeleditor eines adaptiven Formulars angezeigt.

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

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen für verschiedene Anwendungsfälle Feld- und global-Objekte mithilfe eines `Contact Us`-Formulars verwenden.

![Kontaktformular ](/help/forms/using/assets/contact-us-form.png)

#### **Anwendungsfall**: Anzeigen eines Bedienfelds mithilfe der `SetProperty`-Regel

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um das Formularfeld auf `Required` festzulegen.

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
> * Sie können die Feldeigenschaften mit den verfügbaren Eigenschaften in `[form-path]/jcr:content/guideContainer.model.json` konfigurieren.
> * Änderungen am Formular, die mit der Methode `setProperty` des Globals-Objekts vorgenommen werden, sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird das Bedienfeld `personaldetails` durch Klicken auf die Schaltfläche überprüft. Wenn im Bedienfeld keine Fehler erkannt werden, wird ein weiteres Bedienfeld, das Bedienfeld `feedback`, beim Klicken auf die Schaltfläche angezeigt.

Erstellen wir eine Regel für die Schaltfläche `Next`, die das Bedienfeld `personaldetails` validiert und das Bedienfeld `feedback` sichtbar macht, wenn Benutzende auf die Schaltfläche `Next` klicken.

![Eigenschaft festlegen](/help/forms/using/assets/custom-function-set-property.png)

In der folgenden Abbildung sehen Sie, wie das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Next` validiert wird. Falls alle Felder innerhalb der `personaldetails` validiert werden, wird das Bedienfeld `feedback` angezeigt.

![Festlegen der Vorschau für das Eigenschaftsformular ](/help/forms/using/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern des Bedienfelds `personaldetails` vorhanden sind, werden sie beim Klicken auf die Schaltfläche `Next` auf Feldebene angezeigt und das Bedienfeld `feedback` bleibt unsichtbar.

![Festlegen der Vorschau für das Eigenschaftsformular ](/help/forms/using/assets/set-property-panel.png)

#### **Anwendungsfall**: Das Feld validieren.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um das Feld zu validieren.

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
> Wenn in der Funktion `validate()` kein Argument übergeben wird, wird das Formular validiert.

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf das Feld `contact` angewendet. Benutzende müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern beginnt. Wenn Benutzende eine Telefonnummer eingeben, die nicht mit `10` beginnt oder nicht genau `8` Ziffern enthält, wird beim Klicken auf die Schaltfläche eine Validierungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die Schaltfläche `Next` zu erstellen, die das Feld `contact` beim Klicken auf die Schaltfläche validiert.

![Überprüfungsmuster](/help/forms/using/assets/custom-function-validate.png)

Beziehen Sie sich auf die folgende Abbildung, die zeigt, dass eine Fehlermeldung auf Feldebene angezeigt wird, wenn Benutzende eine Telefonnummer eingeben, die nicht mit `10` beginnt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/custom-function-validate-error-message.png)

Wenn Benutzende eine gültige Telefonnummer eingeben und alle Felder im Bedienfeld `personaldetails` validiert worden sind, wird das Bedienfeld `feedback` auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/using/assets/validate-form-preview-form.png)

#### **Anwendungsfall**: Zurücksetzen eines Bedienfelds

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um das Bedienfeld zurückzusetzen.

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
> Wenn in der Funktion `reset()` kein Argument übergeben wird, wird das Formular validiert.

In diesem Beispiel wird das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Clear` zurückgesetzt. Als Nächstes erstellen Sie eine Regel für die Schaltfläche `Clear`, die das Bedienfeld bei einem Klick auf die Schaltfläche zurücksetzt.

![Schaltfläche „Löschen“](/help/forms/using/assets/custom-function-reset-field.png)

In der folgenden Abbildung sehen Sie, dass der Bereich `personaldetails` zurückgesetzt wird, wenn jemand auf die Schaltfläche `clear` klickt:

![Formular zurücksetzen](assets/custom-function-reset-form.png)

#### **Anwendungsfall**: Eine benutzerdefinierte Nachricht auf Feldebene anzeigen und das Feld als ungültig markieren

Mit der Funktion `markFieldAsInvalid()` können Sie ein Feld als ungültig definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festlegen. Der Wert `fieldIdentifier` kann `fieldId`, `field qualifiedName` oder `field dataRef` lauten. Der Wert des Objekts namens `option` kann `{useId: true}`, `{useQualifiedName: true}` oder `{useDataRef: true}` lauten.
Die Syntaxen, die zum Markieren des Felds als ungültig und zum Festlegen der benutzerdefinierten Nachricht verwendet werden, sind:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren, fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben.

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

In diesem Beispiel wird eine benutzerdefinierte Meldung auf Feldebene angezeigt, wenn Benutzende weniger als 15 Zeichen in das Textfeld „Kommentare“ eingeben.

Der nächste Schritt besteht darin, eine Regel für das Feld `comments` zu erstellen:

![Feld als ungültig markieren](/help/forms/using/assets/custom-function-invalid-field.png)

Sehen Sie sich das Beispiel unten an, in dem dargestellt wird, wie die Eingabe von negativem Feedback in das Feld `comments` die Anzeige einer benutzerdefinierten Nachricht auf Feldebene auslöst:

![Feld als ungültige Formularvorschau markieren](/help/forms/using/assets/custom-function-invalidfield-form.png)

Wenn jemand mehr als 15 Zeichen in das Textfeld „Kommentare“ eingibt, wird das Feld validiert und das Formular wird gesendet:

![Feld als gültige Formularvorschau markieren](/help/forms/using/assets/custom-function-validfield-form.png)


#### **Anwendungsfall**: Übermittlung geänderter Daten an den Server

Diese Codezeile
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument gibt an, ob das Formular vor der Übermittlung validiert werden soll. Es ist `optional` und standardmäßig auf `true` festgelegt.
* Das dritte Argument ist der `contentType` der Übermittlung, der ebenfalls optional ist und den Standardwert `multipart/form-data` hat. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded` sein.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um die bearbeiteten Daten an den Server zu senden:

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

Wenn jemand in diesem Beispiel das Textfeld `comments` leer lässt, wird beim Senden des Formulars an den Server `NA` gesendet.

Erstellen Sie nun eine Regel für die Schaltfläche `Submit`, mit der Daten gesendet werden:

![Daten senden](/help/forms/using/assets/custom-function-submit-data.png)

In der Abbildung unten finden Sie das `console window`, das zeigt, dass der Wert als `NA` an den Server gesendet wird, wenn jemand das Textfeld `comments` leer lässt:

![Daten im Konsolenfenster senden](/help/forms/using/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Daten im Konsolenfenster überprüfen](/help/forms/using/assets/custom-function-submit-data-console-data.png)

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

Adaptive Formulare nutzen Caching für benutzerdefinierte Funktionen, um die Antwortzeit beim Abrufen der Liste der benutzerdefinierten Funktionen im Regeleditor zu verbessern. In der Datei `error.log` wird eine Meldung `Fetched following custom functions list from cache` angezeigt.

![benutzerdefinierte Funktion mit Cache-Unterstützung](/help/forms/using/assets/custom-function-cache-error.png)

Wenn die benutzerdefinierten Funktionen geändert werden, wird das Caching invalidiert, und es wird analysiert.

## Fehlerbehebung {#troubleshooting}

* Die Benutzenden müssen sicherstellen, dass die [Kernkomponente und die Spezifikationsversion von auf die neueste Version festgelegt sind](https://github.com/adobe/aem-core-forms-components/tree/release/650). Für bestehende AEM-Projekte und -Formulare sind jedoch zusätzliche Schritte erforderlich:

   * Für das AEM Projekt sollten Benutzende alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` ersetzen und das Projekt bereitstellen.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht richtig funktionieren, müssen Benutzende die Regel `submitForm` mithilfe des Regeleditors anhand der Schaltfläche **Senden** öffnen und speichern. Diese Aktion ersetzt im Formular die vorhandene Regel `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()`.


* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Um die Liste der benutzerdefinierten Funktionen zu überprüfen, können Sie für den Fehler zur Datei `error.log` navigieren. Im Fall eines Fehlers wird die Liste der benutzerdefinierten Funktionen leer angezeigt:

  ![Fehlerprotokolldatei](/help/forms/using/assets/custom-function-list-error-file.png)

  Wenn kein Fehler auftritt, wird die benutzerdefinierte Funktion abgerufen und in der Datei `error.log` angezeigt. In der Datei `error.log` wird eine Meldung mit dem Wert `Fetched following custom functions list` angezeigt:

  ![Fehlerprotokolldatei mit ordnungsgemäßer benutzerdefinierter Funktion](/help/forms/using/assets/custom-function-list-fetched-in-error.png)

## Überlegungen

* Der `parameter type` und der `return type` unterstützen `None` nicht.

* Folgende Funktionen werden in der Liste der benutzerdefinierten Funktionen nicht unterstützt:
   * Generator-Funktionen
   * Async/Await-Funktionen
   * Methodendefinitionen
   * Klassenmethoden
   * Standardparameter
   * Rest-Parameter:
