---
title: APIs zum Arbeiten mit gesendeten Formularen in Forms Portal
description: AEM Forms bietet APIs, mit denen Sie gesendete Formulardaten im Forms Portal abfragen und bearbeiten können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish, developer-reference
feature: Forms Portal
exl-id: a685889e-5d24-471c-926d-dbb096792bc8
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 38%

---

# APIs zum Arbeiten mit gesendeten Formularen in Forms Portal {#apis-to-work-with-submitted-forms-on-forms-portal}

AEM Forms bietet APIs, mit deren Hilfe Sie über das Formularportal gesendete Formulardaten abfragen können. Darüber hinaus können Sie mithilfe der in diesem Dokument beschriebenen APIs Kommentare veröffentlichen oder die Eigenschaften gesendeter Formulare aktualisieren.

>[!NOTE]
>
>Benutzer, die die APIs aufrufen sollen, müssen der Reviewer-Gruppe hinzugefügt werden, wie unter [Zuordnen von Übermittlungsprüfern zu einem Formular](/help/forms/using/adding-reviewers-form.md) beschrieben.

## GET /content/forms/portal/submission.review.json?func=getFormsForSubmissionReview {#get-content-forms-portal-submission-review-json-func-getformsforsubmissionreview-br}

Gibt eine Liste aller zulässigen Formulare zurück.

### URL-Parameter {#url-parameters}

Für diese API sind keine zusätzlichen Parameter erforderlich.

### Antwort {#response}

Das Antwortobjekt enthält ein JSON-Array mit Formularnamen und deren Repository-Pfad. Die Antwort weist die folgende Struktur auf:

```json
[
 {formName: "<form name>",
 formPath: "<path to the form>" },
 {.....},
 ......]
```

### Beispiel {#example}

**URL-Anforderung**

```http
https://[host]:[port]/content/forms/portal/submission.review.json?func=getFormsForSubmissionReview
```

**Antwort**

```json
[{"formPath":"/content/dam/formsanddocuments/forms-review/form2","formName":"form2"},{"formPath":"/content/dam/formsanddocuments/forms-review/form1","formName":"form1"}]
```

## GET /content/forms/portal/submission.review.json?func=getAllSubmissions {#get-content-forms-portal-submission-review-json-func-getallsubmissions}

Gibt Details zu allen gesendeten Formularen zurück. Sie können jedoch URL-Parameter verwenden, um die Ergebnisse zu begrenzen.

### URL-Parameter {#url-parameters-1}

Geben Sie die folgenden Parameter in die Anfrage-URL ein:

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>formPath</code></td>
   <td>Gibt den CRX-Repository-Pfad an, in dem sich das Formular befindet. Wenn Sie den Formularpfad nicht angeben, wird eine leere Antwort zurückgegeben.<br /> </td>
  </tr>
  <tr>
   <td><code>offset</code><br /> (optional)</td>
   <td>Gibt den Startpunkt im Index des Ergebnissatzes an. Der Standardwert lautet <strong>0</strong>.</td>
  </tr>
  <tr>
   <td><code>limit</code><br /> (optional)</td>
   <td>Beschränkt die Anzahl der Ergebnisse. Der Standardwert lautet <strong>30</strong>.</td>
  </tr>
  <tr>
   <td><code>orderby</code> <br /> (optional)</td>
   <td>Gibt die Eigenschaft zum Sortieren der Ergebnisse an. Der Standardwert ist <strong>jcr:lastModified</strong>sortiert die Ergebnisse nach der letzten Änderungszeit.</td>
  </tr>
  <tr>
   <td><code>sort</code> <br /> (optional)</td>
   <td>Gibt die Reihenfolge zum Sortieren der Ergebnisse an. Der Standardwert ist <strong>desc</strong>, der die Ergebnisse in absteigender Reihenfolge sortiert. Indem Sie <code>asc</code> angeben, können Sie die Ergebnisse in iaufsteigender Reihenfolge sortieren.</td>
  </tr>
  <tr>
   <td><code>cutPoints</code> <br /> (optional)</td>
   <td>Gibt eine kommagetrennte Liste von Formulareigenschaften an, die in die Ergebnisse aufgenommen werden sollen. Die Standardeigenschaften sind:<br /> <code>formName</code>, <code>formPath</code>, <code>submitID</code>, <code>formType</code>, <code>jcr:lastModified</code>, <code>owner</code></td>
  </tr>
  <tr>
   <td><code>search</code> <br /> (optional)</td>
   <td>Durchsucht den angegebenen Wert in den Formulareigenschaften und gibt Formulare mit übereinstimmenden Werten zurück. Der Standardwert ist <strong>""</strong>.</td>
  </tr>
 </tbody>
</table>

### Antwort {#response-1}

Das Antwortobjekt enthält ein JSON-Array mit Details zu den angegebenen Formularen. Die Antwort weist die folgende Struktur auf:

```json
{
 total: "<total number of submissions>",
 items: [{ formName: "<name of the form>", formPath: "<path to the form>", owner: "<owner of the form>"},
 ....]}
```

### Beispiel {#example-1}

**URL-Anforderung**

```http
https://[host]:[port]/content/forms/portal/submission.review.json?func=getAllSubmissions&formPath=/content/dam/formsanddocuments/forms-review/form2
```

**Antwort**

```json
{"total":1,"items":[{"formName":"form2","formPath":"/content/dam/formsanddocuments/forms-review/form2","submitID":"1403037413508500","formType":"af","jcr:lastModified":"2015-11-05T17:52:32.243+05:30","owner":"admin"}]}
```

## POST /content/forms/portal/submission.review.json?func=addComment {#post-content-forms-portal-submission-review-json-func-addcomment-br}

Fügt der angegebenen Sendeinstanz einen Kommentar hinzu.

### URL-Parameter {#url-parameters-2}

Geben Sie die folgenden Parameter in die Anfrage-URL ein:

| Parameter | Beschreibung |
|---|---|
| `submitID` | Gibt die zu einer Sendeinstanz gehörige Metadaten-ID an. |
| `Comment` | Gibt den Text für Kommentar an, der der angegebenen Sendeinstanz hinzugefügt werden soll. |

### Antwort {#response-2}

Gibt eine Kommentar-ID zum erfolgreichen Posten eines Kommentars zurück.

### Beispiel {#example-2}

**URL-Anforderung**

```http
https://[host:'port'/content/forms/portal/submission.review.json?func=addComment&submitID=1403037413508500&comment=API+test+comment
```

**Antwort**

```java
1403873422601300
```

## GET /content/forms/portal/submission.review.json?func=getComments   {#get-content-forms-portal-submission-review-json-func-getcomments-nbsp}

Gibt alle für die angegebene Sendeinstanz veröffentlichten Kommentare zurück.

### URL-Parameter {#url-parameters-3}

Geben Sie den folgenden Parameter in der Anforderungs-URL an:

| Parameter | Beschreibung |
|---|---|
| `submitID` | Gibt die Metadaten-ID einer Sendeinstanz an. |

### Antwort {#response-3}

Das Antwortobjekt enthält ein JSON-Array, das alle mit der angegebenen Sende-ID verknüpften Kommentare enthält. Die Antwort weist die folgende Struktur auf:

```json
[{
 owner: "<name of the commenter>",
 comment: "<comment text>",
 time: "<time when the comment was posted>"},
 { }......]
```

### Beispiel {#example-3}

**URL-Anforderung**

```http
https://[host]:'port'/content/forms/portal/submission.review.json?func=getComments&submitID=1403037413508500
```

**Antwort**

```java
[{"owner":"fr1","comment":"API test comment","time":1446726988250}]
```

## POST /content/forms/portal/submission.review.json?func=updateSubmission {#post-content-forms-portal-submission-review-json-func-updatesubmission-br}

Aktualisiert den Wert der angegebenen Eigenschaft der angegebenen gesendeten Formularinstanz.

### URL-Parameter {#url-parameters-4}

Geben Sie die folgenden Parameter in die Anfrage-URL ein:

| Parameter | Beschreibung |
|---|---|
| `submitID` | Gibt die zu einer Sendeinstanz gehörige Metadaten-ID an. |
| `property` | Gibt die zu aktualisierende Formulareigenschaft an. |
| `value` | Gibt den Wert der zu aktualisierenden Formulareigenschaft an. |

### Antwort {#response-4}

Gibt ein JSON-Objekt mit Informationen zur veröffentlichten Aktualisierung zurück.

### Beispiel {#example-4}

**URL-Anforderung**

```http
https://[host]:'port'/content/forms/portal/submission.review.json?func=updateSubmission&submitID=1403037413508500&value=sample_value&property=some_new_prop
```

**Antwort**

```json
{"formName":"form2","owner":"admin","jcr:lastModified":1446727516593,"path":"/content/forms/fp/admin/submit/metadata/1403037413508500.html","submitID":"1403037413508500","status":"submitted"}
```
