---
title: Wie erstellt man adaptive Formulare mit dem JSON-Schema?
description: Erfahren Sie, wie Sie adaptive Formulare mit dem JSON-Schema als Formularmodell erstellen. Sie können bestehende JSON-Schemata verwenden, um adaptive Formulare zu erstellen. Vertiefen Sie Ihre Kenntnisse anhand eines Beispiels für ein JSON-Schema, konfigurieren Sie Felder in der JSON-Schema-Definition vor, beschränken Sie den zulässigen Wertebereich für eine Komponente eines adaptiven Formulars und machen Sie sich mit nicht unterstützten Konstrukten vertraut.
feature: Adaptive Forms
role: User, Developer
level: Beginner, Intermediate
exl-id: 1b402aef-a319-4d32-8ada-cadc86f5c872
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 51%

---

# Erstellen adaptiver Formulare mithilfe des JSON-Schemas {#creating-adaptive-forms-using-json-schema}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


## Voraussetzungen {#prerequisites}

Für das Erstellen eines adaptiven Formulars mit einem JSON-Schema als Formularmodell sind grundlegende Kenntnisse zu JSON-Schemata erforderlich. Es wird empfohlen, den folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](creating-adaptive-form.md)
* [JSON-Schema](https://json-schema.org/)

## Verwenden eines JSON-Schemas als Formularmodell  {#using-a-json-schema-as-form-model}

[!DNL Adobe Experience Manager Forms] unterstützt die Erstellung eines adaptiven Formulars mit einem vorhandenen JSON-Schema als Formularmodell. Dieses JSON-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Das JSON-Schema, das Sie verwenden, sollte mit den [Spezifikationen der Version 4](https://json-schema.org/draft-04/schema) konform sein.

Die wichtigsten Funktionen bei Verwendung eines JSON-Schemas sind wie folgt:

* Die Struktur der JSON-Datei wird im Authoring-Modus für ein adaptives Formular auf der Registerkarte Inhaltssuche als Baumstruktur angezeigt. Sie können Elemente aus der JSON-Hierarchie in das adaptive Formular ziehen und hinzufügen.
* Sie können das Formular mit JSON im Voraus ausfüllen, das mit dem zugehörigen Schema konform ist.
* Bei der Übermittlung werden die vom Benutzer eingegebenen Daten als JSON gesendet, das dem zugehörigen Schema entspricht.

Ein JSON-Schema besteht aus einfachen und komplexen Elementtypen. Die Elemente weisen Attribute auf, die dem Element Regeln hinzufügen. Wenn diese Elemente und Attribute in ein adaptives Formular gezogen werden, werden sie automatisch der entsprechenden Komponente des adaptiven Formulars zugeordnet.

Diese Zuordnung von JSON-Elementen zu adaptiven Formularkomponenten lautet wie folgt:

```json
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
```

<table>
 <tbody>
  <tr>
   <th><strong>JSON-Element, -Eigenschaften oder -Attribute</strong></th>
   <th><strong>Komponente des adaptiven Formulars</strong></th>
  </tr>
  <tr>
   <td><p>Zeichenfolgen-Eigenschaften mit enum- und enumNames-Beschränkung.</p> <p>Syntax,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td>
   <td><p>Dropdown-Komponente:</p>
    <ul>
     <li>Die in enumNames aufgeführten Werte werden in der Dropbox angezeigt.</li>
     <li>Die in der Aufzählung aufgeführten Werte werden zur Berechnung verwendet.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Zeichenfolgeneigenschaft mit Formateinschränkung. Beispielsweise E-Mail und Datum.</p> <p>Syntax,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>Die E-Mail-Komponente wird zugeordnet, wenn der Typ Zeichenfolge und das Format E-Mail ist.</li>
     <li>Textbox-Komponente mit Validierung wird zugeordnet, wenn der Typ Zeichenfolge ist und das Format der Hostname ist.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>}</code></p> </td>
   <td><br /> <br /> Textfeld<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>number-Eigenschaft<br /> </td>
   <td>Numerisches Feld mit Untertyp auf Gleitkommazahl eingestellt<br /> </td>
  </tr>
  <tr>
   <td>Ganzzahl-Eigenschaft<br /> </td>
   <td>Numerisches Feld mit Untertyp "integer"<br /> </td>
  </tr>
  <tr>
   <td>Boolesche Eigenschaft<br /> </td>
   <td>Schalter<br /> </td>
  </tr>
  <tr>
   <td>Objekteigenschaft<br /> </td>
   <td>Bedienfeld<br /> </td>
  </tr>
  <tr>
   <td>Array-Eigenschaft</td>
   <td>Wiederholbares Bedienfeld mit Mindest- und Höchstwert gleich "minItems"bzw. "maxItems". Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.<br /> </td>
  </tr>
 </tbody>
</table>

### Allgemeine Schema-Eigenschaften {#common-schema-properties}

Das adaptive Formular verwendet die im JSON-Schema verfügbaren Informationen, um jedes generierte Feld zuzuordnen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Die Eigenschaft `title` dient als Bezeichnung für die Komponenten des adaptiven Formulars.
* Die Eigenschaft `description` ist als lange Beschreibung für eine Komponente eines adaptiven Formulars festgelegt.
* Die Eigenschaft `default` dient als Ausgangswert für ein Feld in einem adaptiven Formular.
* Die `maxLength`-Eigenschaft wird dem `maxlength`-Attribut einer Textfeldkomponente zugewiesen.
* Die Eigenschaften `minimum`, `maximum`, `exclusiveMinimum` und `exclusiveMaximum` werden für Komponenten vom Typ „numerisches Feld“ verwendet.
* Um Bereiche für eine `DatePicker component`-Komponente zu unterstützen, werden die zusätzlichen JSON-Schemaeigenschaften `minDate` und `maxDate` bereitgestellt.
* Mithilfe der Eigenschaften `minItems` und `maxItems` wird die Anzahl der Elemente/Felder eingeschränkt, die einer Bedienfeldkomponente hinzugefügt oder daraus entfernt werden können.
* Die Eigenschaft `readOnly` legt das `readonly`-Attribut einer Komponente eines adaptiven Formulars fest.
* Die Eigenschaft `required` kennzeichnet ein adaptives Formularfeld als obligatorisch, während im Falle eines Bedienfelds (wo der Typ „object“ ist) die endgültigen übermittelten JSON-Daten Felder mit leerem Wert entsprechend diesem Objekt enthalten.
* Die Eigenschaft `pattern` ist als Validierungsmuster (regulärer Ausdruck) im adaptiven Formular festgelegt.
* Die Erweiterung der JSON-Schema-Datei „.schema.json“ muss beibehalten werden. Beispiel: &lt;filename>.schema.json.

## Beispiel für ein JSON-Schema {#sample-json-schema}

Im Folgenden finden Sie ein Beispiel für ein JSON-Schema.

```json
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Wiederverwendbare Schemadefinitionen {#reusable-schema-definitions}

Definitionsschlüssel kennzeichnen wiederverwendbare Schemas. Die wiederverwendbaren Schemadefinitionen werden verwendet, um Fragmente zu erstellen. Sie ähnelt der Identifizierung komplexer Typen in XSD. Ein JSON-Beispielschema mit Definitionen wird unten angezeigt:

```json
{
  "$schema": "https://json-schema.org/draft-04/schema#",

  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },

  "type": "object",

  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

Im obigen Beispiel wird ein Kundendatensatz definiert, in dem jeder Kunde über eine Versand- und eine Rechnungsadresse verfügt. Die Struktur beider Adressen ist identisch - Adressen haben eine Straße, eine Stadt und einen Bundesstaat - daher ist es empfehlenswert, die Adressen nicht zu duplizieren. Außerdem wird das Hinzufügen und Löschen von Feldern für künftige Änderungen vereinfacht.

## Vorkonfigurieren von Feldern in JSON-Schemadefinitionen {#pre-configuring-fields-in-json-schema-definition}

Mit der Eigenschaft **aem:afProperties** können Sie ein JSON-Schemafeld so vorkonfigurieren, dass es einer benutzerdefinierten Komponente des adaptiven Formulars zugeordnet wird. Ein Beispiel wird unten angezeigt:

```json
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Konfigurieren von Skripten oder Ausdrücken für Formularobjekte  {#configure-scripts-or-expressions-for-form-objects}

JavaScript ist die Ausdruckssprache für adaptive Formulare. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Sie können Formularobjekte vorkonfigurieren, um in einem Formularereignis [einen Ausdruck auszuwerten](adaptive-form-expressions.md).

Verwenden Sie die Eigenschaft aem:afproperties, um Ausdrücke für adaptive Formulare oder Skripte für Komponenten von adaptiven Formularen vorzukonfigurieren. Wenn beispielsweise das Initialisierungsereignis ausgelöst wird, setzt der folgende Code den Wert des Telefonfelds und druckt einen Wert in das Protokoll:

```json
"telephone": {
  "type": "string",
  "pattern": "/\\d{10}/",
  "aem:affKeyword": ["phone", "telephone","mobile phone", "work phone", "home phone", "telephone number", "telephone no", "phone number"],
  "description": "Telephone Number",
  "aem:afProperties" : {
    "sling:resourceType" : "fd/af/components/guidetelephone",
    "guideNodeClass" : "guideTelephone",
    "events": {
      "Initialize" : "this.value = \"1234567890\"; console.log(\"ef:gh\") "
    }
  }
}
```

Sie sollten Mitglied der [forms-power-user-Gruppe](forms-groups-privileges-tasks.md) sein, um Skripte oder Ausdrücke für Formularobjekte zu konfigurieren. In der folgenden Tabelle sind alle Skriptereignisse aufgeführt, die für eine adaptive Formularkomponente unterstützt werden.

<table>
 <tbody>
  <tr>
   <th><strong></strong>Komponente \ Ereignis</th>
   <th>initialize <br /> </th>
   <td>Calculate</td>
   <td>Sichtbarkeit</td>
   <td>Validieren</td>
   <td>Aktiviert</td>
   <td>Wertfestschreibung</td>
   <td>Klicken Sie auf </td>
   <td>Optionen</td>
  </tr>
  <tr>
   <td>Textfeld</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerisches Feld</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerische Schritte</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Optionsschaltfläche</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Telefonnummer</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Schalter</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
  </tr>
  <tr>
   <td>Kontrollkästchen</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Dropdown</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Bildauswahl</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Feld zur Datumseingabe</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumsauswahl</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>E-Mail</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Dateianhang</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Bild</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Draw</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Bedienfeld</td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="Symbol "Ja"" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Einige Beispiele für die Verwendung von Ereignissen in einer JSON sind das Ausblenden eines Felds beim Initialisierungsereignis und das Konfigurieren des Werts eines anderen Felds beim Ereignis zum Bestätigen von Werten. Detaillierte Informationen zum Erstellen von Ausdrücken für die Skriptereignisse finden Sie unter [Ausdrücke in adaptiven Formularen](adaptive-form-expressions.md).

Hier finden Sie den JSON-Beispiel-Code für die zuvor erwähnten Beispiele.

### Ausblenden eines Felds beim Initialisierungsereignis {#hiding-a-field-on-initialize-event}

```json
"name": {
    "type": "string",
    "aem:afProperties": {
        "events" : {
            "Initialize" : "this.visible = false;"
        }
    }
}
```

#### Konfigurieren des Wertes eines anderen Feldes bei einem Ereignis zum Bestätigen von Werten {#configure-value-of-another-field-on-value-commit-event}

```json
"Income": {
    "type": "object",
    "properties": {
        "monthly": {
            "type": "number",
            "aem:afProperties": {
                "events" : {
                    "Value Commit" : "IncomeYearly.value = this.value * 12;"
                }
            }
        },
        "yearly": {
            "type": "number",
            "aem:afProperties": {
                "name": "IncomeYearly"
            }
        }
    }
}
```

## Einschränken der gültigen Werte für eine Komponente eines adaptiven Formulars {#limit-acceptable-values-for-an-adaptive-form-component}

Sie können die folgenden Einschränkungen zu JSON-Schemaelementen hinzufügen, um die Werte zu beschränken, die für eine Komponente eines adaptiven Formulars gültig sind:

<table>
 <tbody>
  <tr>
   <td><p><strong> Schemaeigenschaft</strong></p> </td>
   <td><p><strong>Datentyp</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
   <td><p><strong>Komponente</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Obergrenze für numerische Werte und Daten an. Standardmäßig ist der Maximalwert enthalten.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte<br /> </li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Untergrenze für numerische Werte und Daten an. Standardmäßig ist der Mindestwert enthalten.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>Boolesch</p> </td>
   <td><p>Wenn "true", muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner als der numerische Wert oder das Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> <p>Bei "false"muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>Boolesch</p> </td>
   <td><p>Wenn "true", muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer sein als der numerische Wert oder das Datum, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> <p>Bei "false"muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Mindestanzahl von Zeichen an, die in einer Komponente zulässig sind. Die minimale Länge muss größer oder gleich null sein.</p> </td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die maximal zulässige Anzahl von Zeichen in einer Komponente an. Die maximale Länge muss größer oder gleich null sein.</td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Reihenfolge der Zeichen an. Eine Komponente akzeptiert die Zeichen, wenn die Zeichen dem angegebenen Muster entsprechen.</p> <p>Die pattern-Eigenschaft wird dem Überprüfungsmuster der entsprechenden adaptiven Formularkomponente zugeordnet.</p> </td>
   <td>
    <ul>
     <li>Alle adaptiven Formulare, die einem XSD-Schema zugeordnet sind </li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxItems</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die maximale Anzahl von Elementen in einem Array an. Die maximale Anzahl von Elementen muss größer oder gleich null sein.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>minItems</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die Mindestanzahl von Elementen in einem Array an. Die Mindestanzahl von Elementen muss größer oder gleich null sein.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Nicht unterstützte Konstrukte  {#non-supported-constructs}

Adaptive Formulare bieten keine Unterstützung für die folgenden JSON-Schemakonstrukte:

* Null-Typ
* Unionstypen, z. B. und
* OneOf, AnyOf, AllOf und NOT
* Nur homogene Arrays werden unterstützt. Die Elementbegrenzung muss also ein Objekt und kein Array sein.

## Häufig gestellte Fragen {#frequently-asked-questions}

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das vollständige Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie finde ich ein bestimmtes Element?**

Sie haben zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden

**Welche Erweiterung sollte die JSON-Schema-Datei aufweisen?**

Für eine JSON-Schema-Datei muss immer die Erweiterung .schema.json verwendet werden. Beispiel: &lt;filename>.schema.json.
