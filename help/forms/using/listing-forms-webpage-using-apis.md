---
title: Auflisten von Formularen auf einer Webseite mithilfe von APIs
description: Führen Sie in Forms Manager programmgesteuerte Abfragen durch, um eine gefilterte Liste mit Formularen abzurufen und sie auf Ihren Web-Seiten anzuzeigen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
exl-id: cfca6656-d2db-476d-a734-7a1d1e44894e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 100%

---

# Auflisten von Formularen auf einer Webseite mithilfe von APIs {#listing-forms-on-a-web-page-using-apis}

AEM Forms stellt eine REST-basierte Such-API bereit, die Web-Entwicklerinnen und -Entwickler verwenden können, um Abfragen in Formularsätzen durchzuführen und Formularsätze abzurufen, die die Suchkriterien erfüllen.  Sie können APIs zum Durchsuchen von Formularen auf Basis verschiedener Filter verwenden.  Das Antwortobjekt enthält Formularattribute sowie Eigenschaften und Render-Endpunkte der Formulare.

Um Formulare mit der REST API zu suchen, senden Sie an den Server unter `https://'[server]:[port]'/libs/fd/fm/content/manage.json` eine GET-Anfrage mit den unten beschriebenen Abfrageparametern.

## Abfrageparameter {#query-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Attributname<br /> </strong></td>
   <td><strong>Beschreibung<br /> </strong></td>
  </tr>
  <tr>
   <td>func<br /> </td>
   <td><p>Gibt die Funktion zum Aufrufen an.  Legen Sie zur Suche nach Formularen den Wert des <code>func </code>-Attributs auf <code>searchForms</code> fest.</p> <p>Beispiel: <code class="code">
       URLParameterBuilder entityBuilder=new URLParameterBuilder ();
       entityBuilder.add("func", "searchForms");</code></p> <p><strong>Hinweis:</strong> <em>Dieser Parameter ist obligatorisch.</em><br /> </p> </td>
  </tr>
  <tr>
   <td>appPath<br /> </td>
   <td><p>Gibt den Anwendungspfad für die Suche nach Formularen an.  Standardmäßig durchsucht das appPath-Attribut alle Anwendungen, die auf der Ebene des Stammknotens verfügbar sind.<br /> </p> <p>Sie können bei einer einzelnen Suchabfrage mehrere Anwendungspfade angeben.  Trennen Sie mehrere Pfade durch einen senkrechten Strich (|).  </p> </td>
  </tr>
  <tr>
   <td>cutPoints<br /> </td>
   <td><p>Gibt die Eigenschaften an, die mit den Elementen abgerufen werden sollen.  Sie können Sternchen (*) verwenden, um alle Eigenschaften gleichzeitig abzurufen.  Verwenden Sie den senkrechten Strich (|), um mehrere Eigenschaften anzugeben. </p> <p>Beispiel: <code>cutPoints=propertyName1|propertyName2|propertyName3</code></p> <p><strong>Hinweis</strong>: </p>
    <ul>
     <li><em>Eigenschaften wie ID, Pfad und Name werden immer abgerufen. </em></li>
     <li><em>Jedes Asset verfügt über einen anderen Satz an Eigenschaften. Eigenschaften wie formUrl, pdfUrl und guideUrl hängen nicht vom cutpoints-Attribut ab. Diese Eigenschaften sind vom Asset-Typ abhängig und werden entsprechend abgerufen. </em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>relation<br /> </td>
   <td>Gibt die zugehörigen Assets an, die neben den Suchergebnissen abgerufen werden.  Sie können eine der folgenden Optionen auswählen, um zugehörige Assets abzurufen:
    <ul>
     <li><strong>NO_RELATION</strong>: Zugehörige Assets nicht abrufen.</li>
     <li><strong>IMMEDIATE</strong>: Assets abrufen, die direkt mit den Suchergebnissen zusammenhängen.</li>
     <li><strong>ALL</strong>: Direkt und indirekt zugehörige Assets abrufen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>maxSize</td>
   <td>Gibt die maximale Anzahl an Formularen zum Abrufen an.</td>
  </tr>
  <tr>
   <td>offset</td>
   <td>Gibt die Anzahl an Formularen an, die ab dem Start übersprungen werden sollen.</td>
  </tr>
  <tr>
   <td>returnCount</td>
   <td>Gibt an, ob die Suchergebnisse zurückgegeben werden, die den angegebenen Kriterien entsprechen oder nicht. </td>
  </tr>
  <tr>
   <td>statements</td>
   <td><p>Gibt die Liste der Anweisungen an.  Die Abfragen werden in der Liste der Anweisungen ausgeführt, die im JSON-Format angegeben sind. </p> <p>Beispiel:</p> <p><code class="code">JSONArray statementArray=new JSONArray();
       JSONObject statement=new JSONObject();
       statement.put("name", "title");
       statement.put("value", "SimpleSurveyAF");
       statement.put("operator", "EQ"); statementArray.put(statement);</code></p> <p>Im oben genannten Beispiel gilt Folgendes:  </p>
    <ul>
     <li><strong>name</strong>: gibt den Namen der Eigenschaft an, nach der gesucht werden soll.</li>
     <li><strong>value</strong>: gibt den Wert der Eigenschaft an, nach der gesucht werden soll.</li>
     <li><strong>operator</strong>: Gibt den Operator an, der bei der Suche angewendet werden soll. Die folgende Operatoren werden unterstützt:
      <ul>
       <li>EQ (equal to – gleich)  </li>
       <li>NEQ (not equal to – ungleich)</li>
       <li>GT (greater than – größer als)</li>
       <li>LT (less than – kleiner als)</li>
       <li>GTEQ (greater than or equal to – größer oder gleich)</li>
       <li>LTEQ (less than or equal to – kleiner oder gleich)</li>
       <li>CONTAINS (ENTHÄLT – A enthält B, wenn B Teil von A ist)</li>
       <li>FULLTEXT (Volltextsuche)</li>
       <li>STARTSWITH (BEGINNT MIT – A beginnt mit B, wenn B der Anfangsteil von A ist)</li>
       <li>ENDSWITH (ENDET MIT – A endet mit B, wenn B der Endteil von A ist)</li>
       <li>LIKE (WIE – implementiert den LIKE-Operator)</li>
       <li>AND (UND – kombiniert mehrere Anweisungen)</li>
      </ul> <p><strong>Hinweis:</strong> <em>Die Operatoren GT, LT, GTEQ und LTEQ gelten für Eigenschaften vom linearen Typ wie LONG, DOUBLE und DATE.</em></p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>orderings<br /> </td>
   <td><p>Gibt die Kriterien für die Reihenfolge der Suchergebnisse an. Die Kriterien sind im JSON-Format definiert. Sie können die Suchergebnisse nach mehr als einem Feld sortieren. Die Ergebnisse werden in der Reihenfolge sortiert, in der die Felder in der Abfrage angezeigt werden.</p> <p>Beispiel:</p> <p>Um die Abfrageergebnisse nach Titeleigenschaft in aufsteigender Reihenfolge abzurufen, fügen Sie den folgenden Parameter hinzu: </p> <p><code class="code">JSONArray orderingsArray=new JSONArray();
       JSONObject orderings=new JSONObject();
       orderings.put("name", "title");
       orderings.put("criteria", "ASC");
       orderingsArray.put(orderings);
       entityBuilder.add("orderings", orderingsArray.toString());</code></p>
    <ul>
     <li><strong>name</strong>: Gibt den Namen der Eigenschaft an, die zum Sortieren der Suchergebnisse verwendet werden soll.</li>
     <li><strong>criteria</strong>: Gibt die Reihenfolge der Ergebnisse an. Das Sortierattribut akzeptiert die folgenden Werte:
      <ul>
       <li>ASC: Verwenden Sie ASC, um die Ergebnisse in aufsteigender Reihenfolge anzuordnen.<br /> </li>
       <li>DES: Verwenden Sie DES, um die Ergebnisse in absteigender Reihenfolge anzuordnen.</li>
      </ul> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>includeXdp</td>
   <td>Gibt an, ob der binäre Inhalt abgerufen werden soll oder nicht. Das Attribut <code>includeXdp</code> gilt für Assets vom Typ <code>FORM</code>, <code>PDFFORM</code> und <code>PRINTFORM</code>.</td>
  </tr>
  <tr>
   <td>assetType</td>
   <td>Gibt die Asset-Typen an, die von allen veröffentlichten Assets abgerufen werden sollen. Verwenden Sie den senkrechten Strich (|), um mehrere Asset-Typen anzugeben. Die folgenden Asset-Typen sind gültig: FORM, PDFFORM, PRINTFORM, RESOURCE und GUIDE.</td>
  </tr>
 </tbody>
</table>

## Beispielanfrage {#sample-request}

```json
func : searchForms
appPath : /content/dam/formsanddocuments/MyApplication23
cutPoints : title|description|author|status|creationDate|lastModifiedDate|activationDate|expiryDate|tags|allowedRenderFormat|formmodel
relation : NO_RELATION
includeXdp : false
maxSize : 10
offset : 0
returnCount : true
statements: [{"name":"name","value":"*Claim.xdp","operator":"CONTAINS"},
                {"name":"","value":"Expense","operator":"FULLTEXT"},
                {"name":"description","value":"ABCD*","operator":"CONTAINS"},
                {"name":"status","value":"false","operator":"EQ"},
                {"name":"lastModifiedDate","value":"01/09/2013","operator":"GTEQ"},
                {"name":"lastModifiedDate","value":"01/18/2013","operator":"LTEQ"}]
orderings:[{"name" :"lastModifiedDate":"order":"ASC"}]
```

## Beispielantwort {#sample-response}

```json
[
{"resultCount":2},
    {"assetType":"FORM","name":"ExpenseClaim.xdp","id":"509fa2d5-e3c9-407b-b8dc-fa0ba08eb0ce",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDEFGIJK","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"5477a127-8bbf-4cec-8f81-2689e5cb4a15",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/Image.gif","resourceSize":0}],
       "status":false,"creationDate":1358429845623,"lastModifiedDate":1358429846771},
{"assetType":"FORM","name":"ExpenseClaim.xdp","id":"4312239b-b666-4d36-95bc-641b3a39ddd4",
       "path":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDefghijklm","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"118a2e3f-7097-4d8c-85d1-651306de284a",
       "path":"/content/dam/formsanddocuments/MyApplication23/Image.gif","resourceSize":0}],"status":false,
       "creationDate":1358429856690,"lastModifiedDate":1358430109023}
]
```

## Verwandte Artikel

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
