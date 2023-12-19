---
title: APIs zum Zugriff auf Briefinstanzen
description: Entdecken Sie APIs und verwenden Sie sie, um programmgesteuert auf Briefinstanzen in der AEM Forms-Umgebung zuzugreifen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: 9d43d9d4-5487-416c-b641-e807227ac056
source-git-commit: 000c22028259eb05a61625d43526a2e8314a1d60
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 85%

---

# APIs zum Zugriff auf Briefinstanzen {#apis-to-access-letter-instances}

## Übersicht {#overview}

Durch Verwenden der Correspondence Management-Benutzeroberfläche „Korrespondenzen erstellen“ können Sie Entwürfe laufender Briefinstanzen speichern. Außerdem sind gesendete Briefinstanzen vorhanden.

Correspondence Management bietet APIs, über die Sie eine Listenschnittstelle erstellen können, um mit gesendeten Briefinstanzen oder Entwürfen zu arbeiten. Die APIs listen und öffnen gesendete und Entwurfsbriefinstanzen eines Agenten, damit der Agent weiterhin am Entwurf oder an der gesendeten Briefinstanz arbeiten kann.

## Abrufen von Briefinstanzen {#fetching-letter-instances}

Correspondence Management stellt APIs zum Abrufen von Briefinstanzen über den LetterInstanceService-Dienst bereit.

| Methode | Beschreibung |
|--- |--- |
| getAllLetterInstances | Ruft Briefinstanzen anhand des Eingabeabfrageparameters ab. Um alle Briefinstanzen aufzurufen, übergeben Sie den Abfrageparameter als null. |
| getLetterInstance | Ruft die angegebene Briefinstanz basierend auf der Briefinstanz-ID auf. |
| letterInstanceExists | Prüft anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist. |

>[!NOTE]
>
>„LetterInstanceService“ ist ein OSGi-Dienst und seine Instanz kann wie folgt abgerufen werden:
über@Reference in der Java™-Klasse oder sling.getService(LetterInstanceService. Class) in JSP.

### Verwendung von getAllLetterInstances {#using-nbsp-getallletterinstances}

Die folgende API findet die Briefinstanzen basierend auf dem Abfrageobjekt (Gesendet und Entwurf). Wenn das Abfrageobjekt null ist, werden alle Briefinstanzen zurückgegeben. Diese API gibt eine Liste von [LetterInstanceVO](https://helpx.adobe.com/de/aem-forms/6-2/javadocs/com/adobe/icc/dbforms/obj/LetterInstanceVO.html)-Objekten zurück, die zum Extrahieren von zusätzlichen Informationen aus der Briefinstanz verwendet werden können.

**Syntax**: `List getAllLetterInstances(Query query) throws ICCException;`

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>query</td>
   <td>Der Parameter „query“ wird zum Suchen/Filtern der Briefinstanz verwendet. Hier unterstützt „query“ nur Attribute/Eigenschaften der obersten Ebene des Objekts. „query“ besteht aus Anweisungen und „attributeName“ im Anweisungsobjekt sollte dem Namen der Eigenschaft im Briefinstanzobjekt entsprechen.<br /> </td>
  </tr>
 </tbody>
</table>

#### Beispiel 1: Abrufen aller Briefinstanzen vom Typ GESENDET {#example-fetch-all-the-letter-instances-of-type-submitted}

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
| letterInstanceName | Der Name der Briefinstanz, bei der Sie überprüfen möchten, ob sie vorhanden ist. |

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceName = "sampleLetterInstance";
Boolean result = letterInstanceService.letterInstanceExists(letterInstanceName );
```

## Öffnen von Briefinstanzen {#opening-letter-instances}

Die Briefinstanz kann vom Typ „Gesendet“ oder „Entwurf“ sein. Beim Öffnen der beiden Briefinstanztypen zeigen sich unterschiedliche Verhaltensweisen:

* Wenn eine Instanz für gesendete Briefe vorhanden ist, wird eine PDF geöffnet, die die Briefinstanz darstellt. Die Briefinstanz vom Typ „Gesendet“, die auf dem Server vorhanden ist, enthält auch die dataXML und verarbeitete XDP, die verwendet werden können, um Anwendungsfälle wie das Erstellen einer PDF/A durchzuführen und weiter anzupassen.
* Wenn eine Briefinstanz vom Typ Entwurf vorhanden ist, wird die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;in den exakten vorherigen Status wie zum Zeitpunkt der Erstellung des Entwurfs neu geladen

### Öffnen der Briefinstanz „Entwurf“  {#opening-draft-letter-instance-nbsp}

Die CCR-Benutzeroberfläche unterstützt den Parameter cmLetterInstanceId , der zum Neuladen des Briefs verwendet werden kann.

`https://[hostName]:[portNo]/[contextPath]//aem/forms/createcorrespondence.html?random=[randomNo]&cmLetterInstanceId=[letterInstanceId]`

>[!NOTE]
>
Sie müssen beim Neuladen einer Korrespondenz weder cmLetterId noch cmLetterName/State/Version angeben, da die gesendeten Daten bereits alle Details zu dieser Korrespondenz enthalten. „RandomNo“ wird verwendet, um Probleme mit dem Browsercache zu vermeiden. Sie können einen Zeitstempel als Zufallszahl verwenden.

### Öffnen der Briefinstanz „Gesendet“ {#opening-submitted-letter-instance}

Ein gesendetes PDF-Dokument kann mit der Briefinstanz-ID direkt geöffnet werden:

`https://[hostName]:[portNo]/[contextPath]/[letterInstanceId]`
