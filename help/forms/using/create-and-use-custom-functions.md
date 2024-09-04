---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
feature: Adaptive Forms, Foundation Components
role: Admin, User, Developer
source-git-commit: f63dcd7edca640cee47c8f615d1675ef5052953c
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 50%

---

# Benutzerdefinierte Funktionen in Adaptive Forms

## Einführung

AEM Forms 6.5 bietet nun die Möglichkeit, JavaScript-Funktionen zu definieren, mit denen komplexe Geschäftsregeln mithilfe des Regeleditors definiert werden können. AEM Forms bietet eine Reihe solcher benutzerdefinierter Funktionen standardmäßig, aber Sie müssen Ihre eigenen benutzerdefinierten Funktionen definieren und sie in mehreren Formularen verwenden.

Die benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Bearbeitung und Verarbeitung der eingegebenen Daten erleichtern, um bestimmten Anforderungen gerecht zu werden. Sie ermöglichen auch eine dynamische Änderung des Formularverhaltens basierend auf vordefinierten Kriterien.
In Adaptive Forms können Sie benutzerdefinierte Funktionen im [Regeleditor eines adaptiven Formulars](/help/forms/using/rule-editor.md) verwenden, um spezifische Validierungsregeln für Formularfelder zu erstellen.
Im Folgenden wird die Verwendung einer benutzerdefinierten Funktion beschrieben, in der Benutzer die E-Mail-Adresse eingeben und sichergestellt werden soll, dass die eingegebene E-Mail-Adresse ein bestimmtes Format aufweist (sie enthält ein &quot;@&quot;-Symbol und einen Domänennamen). Erstellen Sie eine benutzerdefinierte Funktion als &quot;ValidateEmail&quot;, die die E-Mail-Adresse als Eingabe verwendet und &quot;true&quot; zurückgibt, wenn sie gültig ist, andernfalls &quot;false&quot;.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

Im obigen Beispiel wird, wenn der Benutzer versucht, das Formular zu senden, die benutzerdefinierte Funktion &quot;ValidateEmail&quot;aufgerufen, um zu überprüfen, ob die eingegebene E-Mail-Adresse gültig ist.

## Verwendung benutzerdefinierter Funktionen {#uses-of-custom-function}

Die Verwendung benutzerdefinierter Funktionen in Adaptive Forms bietet folgende Vorteile:

* **Datenbearbeitung**: Benutzerdefinierte Funktionen bearbeiten und verarbeiten in die Formularfelder eingegebene Daten.
* **Validierung der Daten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen für Formulareingaben durchzuführen und bestimmte Fehlermeldungen anzugeben.
* **Dynamisches Verhalten**: Mit benutzerdefinierten Funktionen können Sie das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies hilft beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen basierend auf externen Ereignissen.

## Unterstützte JS-Anmerkungen

Stellen Sie sicher, dass die benutzerdefinierte Funktion, die Sie schreiben, mit dem oben stehenden `jsdoc` versehen ist, falls Sie eine benutzerdefinierte Konfiguration und Beschreibung benötigen. Es gibt mehrere Möglichkeiten, eine Funktion in `JavaScript,` zu deklarieren, und Kommentare ermöglichen es Ihnen, die Funktionen zu verfolgen. Weitere Informationen finden Sie unter [usejsdoc.org](https://jsdoc.app/).

Unterstützte `jsdoc`-Tags:

* **Private** (Privat)
Syntax: `@private`  
Eine Private-Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* **Name**
Syntax: `@name funcName <Function Name>`
Alternativ dazu ist es möglich`,``@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>` zu verwenden.
  `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).
  `<Function Name>` ist der Anzeigename der Funktion.

* **Member** (Mitglied)
Syntax: `@memberof namespace`
Bindet einen Namespace an die Funktion.

* **Parameter**
Syntax: `@param {type} name <Parameter Description>`
Alternativ dazu ist es möglich, `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>` zu verwenden.
Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens).
  `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   1. String (Zeichenfolge)
   2. Number (Zahl)
   3. Boolean (Boolesch)
   4. Scope (Umfang)

  Der Umfang wird für die Verweise auf Felder eines adaptiven Formulars verwendet. Wenn ein Formular verzögertes Laden (Lazy Loading) verwendet, können Sie `scope` verwenden, um auf dessen Felder zuzugreifen. Sie können auf Felder zugreifen, wenn die Felder geladen wurden oder wenn die Felder als „global“ gekennzeichnet sind.

  Alle anderen Parametertypen fallen in eine der oben genannten Kategorien. Keine Angabe wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei den Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameter `name` unzulässig. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Return Type** (Rückgabetyp)
Syntax: `@return {type}`
Alternativ ist es möglich, `@returns {type}` zu verwenden.
Fügt Informationen über die Funktion hinzu (z. B. ihren Zweck).
Die Zeichenfolge „{type}“ gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)

  Alle anderen Rückgabetypen fallen in eine der oben genannten Kategorien. Keine Angabe wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

* **This** (Dieses)
Syntax: `@this currentComponent`

  Verwenden Sie @this, um auf die Komponente des adaptiven Formulars zu verweisen, in der die Regel geschrieben wird.

  Das folgende Beispiel basiert auf dem Feldwert. In dem folgenden Beispiel blendet die Regel ein Feld im Formular aus. Der `this`-Teil von `this.value` bezieht sich auf die zugrunde liegende Komponente des adaptiven Formulars, für die die Regel geschrieben wird.

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
  >Kommentare vor benutzerdefinierten Funktionen werden für die Zusammenfassung verwendet. Die Zusammenfassung kann sich über mehrere Zeilen bis zum nächsten Tag erstrecken. Beschränken Sie ihre Länge auf eine einzelne Zeile, um eine kurze Beschreibung im Regel-Builder zu erhalten.

## Unterstützte Typen von Funktionsdeklarationen {#function-declaration-supported-types}

**Funktionsanweisung**

```javascript
function area(len) {
    return len*len;
}
```

Diese Funktion wird ohne `jsdoc`-Kommentare eingefügt.

**Funktionsausdruck**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Funktionsausdruck und -anweisung**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Funktionsdeklaration als Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Einschränkung: Über die benutzerdefinierte Funktion wird nur die erste Funktionsdeklaration aus der Variablenliste ausgewählt, falls zusammen vorhanden. Der Funktionsausdruck kann für jede deklarierte Funktion verwendet werden.

**Funktionsdeklaration als Objekt**

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

## Benutzerdefinierte Funktion erstellen {#create-custom-function}

Um eine benutzerdefinierte Funktion zu erstellen, führen Sie die folgenden Schritte aus:

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
Fügen wir der JavaScript-Datei den folgenden Code hinzu, um das Alter basierend auf dem Geburtsdatum (JJJ-MM-TT) zu berechnen.

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

## Clientbibliothek in einem adaptiven Formular hinzufügen{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek in Ihrer Forms CS-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zum adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol Eigenschaften des Guide-Containers. Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Einfach]** und wählen Sie den Namen der Kategorie **[!UICONTROL Client-Bibliothek]** aus der Dropdownliste aus (wählen Sie in diesem Fall `customfunctionscategory` aus).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klicken Sie auf **[!UICONTROL Fertig]** .

Jetzt können Sie eine Regel erstellen, um benutzerdefinierte Funktionen im Regeleditor zu verwenden:

![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/using//assets/calculateage-customfunction.png)

Jetzt sollten wir verstehen, wie Sie eine benutzerdefinierte Funktion mithilfe des Aufrufdienstes des [Regel-Editors in AEM Forms](/help//forms/using/rule-editor.md) konfigurieren und verwenden.
