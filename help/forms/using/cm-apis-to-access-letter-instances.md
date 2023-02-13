---
title: APIs zum Zugriff auf Briefinstanzen
seo-title: APIs to access letter instances
description: Erfahren Sie mehr zur Verwendung von APIs, um auf Briefinstanzen zuzugreifen.
seo-description: Learn how to use APIs to access letter instances.
uuid: e7fb7798-f49d-458f-87f5-22df5f3e7d10
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 9c27f976-972a-4250-b56d-b84a7d72f8c8
feature: Correspondence Management
exl-id: 9d43d9d4-5487-416c-b641-e807227ac056
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '578'
ht-degree: 100%

---

# APIs zum Zugriff auf Briefinstanzen {#apis-to-access-letter-instances}

## Übersicht {#overview}

Durch Verwenden der Benutzeroberfläche „Korrespondenz erstellen“ von Correspondence Management können Sie Entwürfe von Briefinstanzen unter Fortschritt speichern und es gibt gesendete Briefinstanzen.

Correspondence Management bietet APIs, mit denen Sie die Listenschnittstelle erstellen können, um mit gesendeten Briefinstanzen oder Entwürfen zu arbeiten. Die APIs listen und öffnen gesendete und Entwurfsbriefinstanzen eines Agenten, damit der Agent weiterhin am Entwurf oder an der gesendeten Briefinstanz arbeiten kann.

## Abrufen von Briefinstanzen {#fetching-letter-instances}

Correspondence Management stellt APIs bereit, um  Briefinstanzen mithilfe von LetterInstanceService abzurufen.

| Methode | Beschreibung |
|--- |--- |
| getAllLetterInstances | Ruft Briefinstanzen anhand des Eingabeabfrageparameters ab. Um alle Briefinstanzen aufzurufen, geben Sie die Abfrageparameter als null weiter. |
| getLetterInstance | Ruft die angegebene Briefinstanz basierend auf der Briefinstanz-ID auf. |
| letterInstanceExists | Prüft anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist. |

>[!NOTE]
>
>LetterInstanceService ist ein OSGI-Service, dessen Instanz mit Hilfe von @Reference in Java abgerufen werden kann
>Klasse oder sling.getService(LetterInstanceService. Class) in JSP.

### Verwendung von getAllLetterInstances {#using-nbsp-getallletterinstances}

Die folgende API findet die Briefinstanzen basierend auf dem Abfrageobjekt (Gesendet und Entwurf). Wenn das Abfrageobjekt null ist, werden alle Briefinstanzen zurückgegeben. Diese API gibt eine Liste von [LetterInstanceVO](https://helpx.adobe.com/de/aem-forms/6-2/javadocs/com/adobe/icc/dbforms/obj/LetterInstanceVO.html)-Objekten zurück, die zum Extrahieren zusätzlicher Informationen der Briefinstanz verwendet werden können

**Syntax**: `List getAllLetterInstances(Query query) throws ICCException;`

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Abfrage</td>
   <td>Der Abfrageparameter wird verwendet, um die Briefinstanz zu finden/filtern. Hier unterstützt die Abfrage nur Attribute/Eigenschaften des Objekts auf höchster Ebene. „Abfrage“ besteht aus Anweisungen und dem „attributeName“ im Anweisungsobjekt und sollte mit dem Namen der Eigenschaft im Briefinstanzobjekt verwendet werden.<br />  </td>
  </tr>
 </tbody>
</table>

#### Beispiel 1: Rufen Sie alle Briefinstanzen des Typs GESENDET ab {#example-fetch-all-the-letter-instances-of-type-submitted}

Der folgende Code gibt die Liste der gesendeten Briefinstanzen zurück. Um nur Entwürfe zu erhalten, ändern Sie `LetterInstanceType.COMPLETE.name()` in `LetterInstanceType.DRAFT.name().`

```java
@Reference
LetterInstanceService letterInstanceService;
Query query = new Query();

List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();

Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

#### Beispiel 2: Rufen Sie alle Briefinstanzen, die von einem Benutzer gesendet wurden auf; der Briefinstanztyp ist ENTWURF {#example-nbsp-fetch-all-the-letter-instances-submitted-by-a-user-and-letter-instance-type-is-draft}

Der folgende Code hat mehrfache Aussagen in der gleichen Abfrage zum Filtern der Ergebnisse, basierend auf unterschiedlichen Kriterien wie von einem Benutzer gesendete Briefinstanz (Attribut gesendet von) und Typ von letterInstanceType ist ENTWURF.

```java
@Reference
LetterInstanceService letterInstanceService;

String submittedBy = "tglodman";
Query query = new Query();

List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();

Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);

Statement statementForSubmittedBy = new Statement();
statementForSubmittedBy .setAttributeName("submittedby");
statementForSubmittedBy .setOperator(Operator.EQUALS);
statementForSubmittedBy .setAttributeValue(submittedBy);
query.addStatement(statementForSubmittedBy );
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

### Verwenden von getLetterInstance {#using-nbsp-getletterinstance}

Rufen Sie die Briefinstanz auf, die von der angegebenen Briefinstanz-ID identifiziert wird. Es wird „null“ zurückgegeben, wenn die Instanz-ID nicht übereinstimmt.

**Syntax**: `public LetterInstanceVO getLetterInstance(String letterInstanceId) throws ICCException;`

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceId = "/content/apps/cm/letterInstances/1001/sampleLetterInstance";
LetterInstanceVO letterInstance = letterInstanceService.getLetterInstance(letterInstanceId );
```

### Überprüfen, ob Briefinstanz vorhanden ist {#verifying-if-letterinstance-exist}

Prüfen Sie anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist

**Syntax**: `public Boolean letterInstanceExists(String letterInstanceName) throws ICCException;`

| **Parameter** | **Beschreibung** |
|---|---|
| letterInstanceName | Der Name der Briefinstanz, die Sie überprüfen möchten, ob sie vorhanden ist |

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceName = "sampleLetterInstance";
Boolean result = letterInstanceService.letterInstanceExists(letterInstanceName );
```

## Öffnen von Briefinstanzen {#opening-letter-instances}

Briefinstanz kann vom Typ „Gesendet“ oder „Entwurf“ sein. Wenn die beiden Briefinstanztypen geöffnet werden, werden unterschiedliche Verhalten gezeigt:

* Bei der Briefinstanz „Gesendet“ wird ein PDF-Dokument geöffnet, das die Briefinstanz darstellt. Briefinstanz „Gesendet“, die auf dem Server vorhanden ist, enthält auch die dataXML und verarbeitete XDP, die verwendet werden können, um Anwendungsfälle wie das Erstellen einer PDF/A weiter anzupassen.
* Im Falle der Briefinstanz „Entwurf“ wird die Benutzeroberfläche „Korrespondenz erstellen“ in den genauen Status wie zuvor neu geladen, als sie als Entwurf erstellt wurde

### Öffnen der Briefinstanz „Entwurf“  {#opening-draft-letter-instance-nbsp}

CCR Benutzeroberfläche  unterstützt den Parameter cmLetterInstanceId, der zum Neuladen des Briefs verwendet werden kann.

`https://[hostName]:[portNo]/[contextPath]//aem/forms/createcorrespondence.html?random=[randomNo]&cmLetterInstanceId=[letterInstanceId]`

>[!NOTE]
>
>Sie müssen beim Neuladen einer Korrespondenz weder cmLetterId noch cmLetterName/State/Version angeben, da die gesendeten Daten bereits alle Details zu dieser Korrespondenz enthalten. RandomNo wird verwendet, um Probleme mit dem Browser-Cache zu vermeiden. Sie können Zeitstempel als zufällige Zahl verwenden.

### Öffnen einer gesendeten Briefinstanz {#opening-submitted-letter-instance}

Gesendetes PDF-Dokument kann mit der Briefinstanz-ID direkt geöffnet werden:

`https://[hostName]:[portNo]/[contextPath]/[letterInstanceId]`
