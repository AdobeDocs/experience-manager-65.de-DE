---
title: APIs zum Zugriff auf Briefinstanzen
description: Erfahren Sie, wie Sie mit APIs auf Briefinstanzen zugreifen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: 9d43d9d4-5487-416c-b641-e807227ac056
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 41%

---

# APIs zum Zugriff auf Briefinstanzen {#apis-to-access-letter-instances}

## Übersicht {#overview}

Mithilfe der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;von Correspondence Management können Sie Entwürfe von Briefinstanzen unter &quot;Fortschritt&quot;speichern und es gibt gesendete Briefinstanzen.

Correspondence Management bietet APIs, mit denen Sie die Listenschnittstelle für die Arbeit mit gesendeten Briefinstanzen oder Entwürfen erstellen können. Die APIs listen und öffnen gesendete und Entwurfsbriefinstanzen eines Agenten, damit der Agent weiterhin am Entwurf oder an der gesendeten Briefinstanz arbeiten kann.

## Abrufen von Briefinstanzen {#fetching-letter-instances}

Correspondence Management stellt APIs bereit, um  Briefinstanzen mithilfe von LetterInstanceService abzurufen.

| Methode | Beschreibung |
|--- |--- |
| getAllLetterInstances | Ruft Briefinstanzen anhand des Eingabeabfrageparameters ab. Um alle Briefinstanzen abzurufen, übergeben Sie den Abfrageparameter als null. |
| getLetterInstance | Ruft die angegebene Briefinstanz basierend auf der Briefinstanz-ID ab. |
| letterInstanceExists | Überprüft anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist. |

>[!NOTE]
>
>LetterInstanceService ist ein OSGI-Dienst und seine Instanz kann mithilfe von @Reference in Java™ Class oder sling.getService(LetterInstanceService abgerufen werden. Class) in JSP.

### Verwendung von getAllLetterInstances {#using-nbsp-getallletterinstances}

Die folgende API findet die Briefinstanzen basierend auf dem Abfrageobjekt (Gesendet und Entwurf). Wenn das Abfrageobjekt null ist, werden alle Briefinstanzen zurückgegeben. Diese API gibt eine Liste von [LetterInstanceVO](https://helpx.adobe.com/de/aem-forms/6-2/javadocs/com/adobe/icc/dbforms/obj/LetterInstanceVO.html) -Objekte, die zum Extrahieren zusätzlicher Informationen der Briefinstanz verwendet werden können.

**Syntax**: `List getAllLetterInstances(Query query) throws ICCException;`

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Abfrage</td>
   <td>Der Abfrageparameter wird zum Suchen/Filtern der Briefinstanz verwendet. Hier unterstützt die Abfrage nur Attribute/Eigenschaften der obersten Ebene des Objekts. Abfrage besteht aus Anweisungen und der im Statement-Objekt verwendete "attributeName"sollte der Name der Eigenschaft im Briefinstanzobjekt sein.<br /> </td>
  </tr>
 </tbody>
</table>

#### Beispiel 1: Rufen Sie alle Briefinstanzen des Typs &quot;SUBMITTED&quot;ab {#example-fetch-all-the-letter-instances-of-type-submitted}

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
| letterInstanceName | Name der Briefinstanz, deren Existenz Sie überprüfen möchten. |

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceName = "sampleLetterInstance";
Boolean result = letterInstanceService.letterInstanceExists(letterInstanceName );
```

## Öffnen von Briefinstanzen {#opening-letter-instances}

Die Briefinstanz kann vom Typ &quot;Gesendet&quot;oder &quot;Entwurf&quot;sein. Das Öffnen beider Briefinstanztypen zeigt unterschiedliche Verhaltensweisen:

* Im Falle einer Briefinstanz &quot;Gesendet&quot; wird eine PDF geöffnet, die die Briefinstanz darstellt. Die gesendete Briefinstanz, die auf dem Server persistiert wird, enthält auch die dataXML und verarbeitete XDP, die verwendet werden können, um einen Anwendungsfall wie das Erstellen einer PDF/A auszuführen und weiter anzupassen.
* Im Falle einer Briefinstanz &quot;Entwurf&quot;wird die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;in den exakten vorherigen Status wie zum Zeitpunkt der Erstellung des Entwurfs neu geladen

### Öffnen der Briefinstanz „Entwurf“  {#opening-draft-letter-instance-nbsp}

CCR Benutzeroberfläche  unterstützt den Parameter cmLetterInstanceId , der zum Neuladen des Briefs verwendet werden kann.

`https://[hostName]:[portNo]/[contextPath]//aem/forms/createcorrespondence.html?random=[randomNo]&cmLetterInstanceId=[letterInstanceId]`

>[!NOTE]
>
Sie müssen beim Neuladen einer Korrespondenz weder cmLetterId noch cmLetterName/State/Version angeben, da die gesendeten Daten bereits alle Details zu dieser Korrespondenz enthalten. RandomNo wird verwendet, um Browsercache-Probleme zu vermeiden. Sie können einen Zeitstempel als zufällige Nummer verwenden.

### Öffnen der gesendeten Briefinstanz {#opening-submitted-letter-instance}

Gesendete PDF kann direkt mit der Briefinstanz-ID geöffnet werden:

`https://[hostName]:[portNo]/[contextPath]/[letterInstanceId]`
