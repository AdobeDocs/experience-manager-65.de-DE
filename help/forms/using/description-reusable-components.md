---
title: Beschreibung wiederverwendbarer Komponenten
seo-title: Beschreibung wiederverwendbarer Komponenten
description: Eine vollständige Liste von wiederverwendbaren Komponenten mit Dateinamen und Abhängigkeiten, die Sie bei der Integration von AEM Forms Workspace-Komponenten in Ihre Webanwendungen unterstützen.
seo-description: Eine vollständige Liste von wiederverwendbaren Komponenten mit Dateinamen und Abhängigkeiten, die Sie bei der Integration von AEM Forms Workspace-Komponenten in Ihre Webanwendungen unterstützen.
uuid: 8e6accc7-0935-4d7b-b838-d23676df5cda
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: d3facd17-ceb0-4799-8cd9-ff9e81e09793
exl-id: b8cb7233-3d9e-41d4-85c5-8e8c2481f89c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 88%

---

# Beschreibung wiederverwendbarer Komponenten {#description-of-reusable-components}

AEM Forms Workspace besteht aus [wiederverwendbaren](/help/forms/using/integrating-html-ws-components-web.md)-Komponenten, die in einer bestimmten [Ordnerstruktur](/help/forms/using/folder-structure.md) in CRX™ organisiert sind. Für jede Komponente sind Modell-, Ansichts- und Vorlagendateien in der Ordnerstruktur angegeben, außerdem sind JavaScript™-Abhängigkeiten von anderen Komponentendateien, Listener-Ereignisse der Komponente und JavaScript-Objekte, die diese Ereignisse in HTML Workspace auslösen. Die vollständige Liste der wiederverwendbaren Komponenten mit den einzelnen Dateinamen und Abhängigkeiten ist im Folgenden aufgeführt.

## TaskList {#tasklist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>tasklist.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td>
    <ul>
     <li><p>UserSearch</p></li>
     <li><p>Aufgabe</p></li>
     <li><p>TeamTask</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>Task-Modell</p></li>
     <li><p>TeamTask-Modell</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>filterSelected – TaskList-Modell</p></li>
     <li><p>remove – TaskList-Modell</p></li>
     <li><p>updateQueue – TaskList-Modell</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Diese Komponente kann unabhängig von AEM Forms Workspace verwendet werden, vorausgesetzt, Sie lösen das Ereignis „filterSelected“ für diese Komponente über Ihre benutzerdefinierte Anwendung aus.

## Aufgabe {#task}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>task.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>task.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>task.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>TaskList-Modell</p></li>
     <li><p>taskactions-Dienstprogramm</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>submitComplete – Task-Modell</p></li>
     <li><p>Reject – Task-Modell</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Workspace ruft die fetchTasks-Funktion des TaskList-Modells auf, um Task-Modelle für diese Komponente zu erstellen.

## FilterList {#filterlist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>filterlist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>filterlist.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>fetched – TaskList-Modell </p></li>
     <li><p>remove – TaskList-Modell </p></li>
     <li><p>updateQueue – TaskList-Modell </p></li>
     <li><p>refreshedQueue – TaskList-Modell </p></li>
     <li><p>filterSelected – TaskList-Modell</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## Filter {#filter}

<table>
 <tbody>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>filter.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>filter.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td>
    <ul>
     <li><p>Feld: queue: {name, qid, isDefault, type}</p> </li>
     <li><p>Feld: query: string</p> </li>
     <li><p>Feld: parentView: FilterList-Ansicht</p> </li>
     <li><p>Feld: parentModel: TaskList-Modell</p> </li>
     <li><p>Feld: utility</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
 </tbody>
</table>

## TeamQueues {#teamqueues}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>teamqueues.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>teamqueues.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>fetched – TaskList-Modell </p></li>
     <li><p>remove – TaskList-Modell </p></li>
     <li><p>updateQueue – TaskList-Modell </p></li>
     <li><p>teamQueuesFetched – TaskList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## TeamFilter {#teamfilter}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>teamfilter.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>teamfilter.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td>
    <ul>
     <li><p>Erweitert: Filteransicht</p> </li>
     <li><p>Feld: queue: {name, qid, isDefault, type}</p> </li>
     <li><p>Feld: query: string</p> </li>
     <li><p>Feld: parentView: FilterList-Ansicht</p> </li>
     <li><p>Feld: parentModel: TaskList-Modell</p> </li>
     <li><p>Feld: utility</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>TeamFilter ruft das Ereignis ab, das angibt, welche Aufgabe aus der TaskList-Komponente ausgewählt wurde. Obwohl diese Komponenten dieselbe Modellklasse haben, gibt es keine andere Abhängigkeit.

## TaskDetails {#taskdetails}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>tasklist.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>taskdetails.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>taskdetails.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>Die meisten Dienstprogrammklassen</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td>
    <ul>
     <li><p>processinstancehistory.html</p> </li>
     <li><p>formrendering-Dienstprogramm</p> </li>
     <li><p>notes-Dienstprogramm</p> </li>
     <li><p>attachments-Dienstprogramm</p> </li>
     <li><p>taskactions-Dienstprogramm</p> </li>
     <li><p>history-Dienstprogramm</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li><p>forwarded – Task-Modell</p> </li>
     <li><p>shared – Task-Modell</p> </li>
     <li><p>consulted – Task-Modell</p> </li>
     <li><p>rejected – Task-Modell</p> </li>
     <li><p>abandoned – Task-Modell</p> </li>
     <li><p>unlocked – Task-Modell</p> </li>
     <li><p>locked – Task-Modell</p> </li>
     <li><p>claimed – Task-Modell</p> </li>
     <li><p>change:taskselected – TaskList-Modell</p> </li>
     <li><p>change:formUrl – Task-Modell</p> </li>
     <li>attachmentURLFetched – Task-Modell</li>
    </ul>
    <ul>
     <li>newAttachment – Task-Modell</li>
     <li><p>taskHistoryFetched – Task-Modell</p> </li>
     <li>prepareForSubmitComplete – Task-Modell</li>
     <li><p>submitComplete – Task-Modell</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## CategoryList {#categorylist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>startprocess.html (im Ordner „route“)</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>Kategorie</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>FavoriteCategoryFactory-Modell</p></li>
     <li><p>AllCategoryFactory-Modell</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>allStartpointsFetched – CategoryList-Modell </p></li>
     <li><p>add – CategoryList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Diese Komponente verwendet Modellklassen einiger anderer Komponenten wie StartPointList, StartPoint und Task. Abgesehen von dieser Abhängigkeit kann CategoryList unabhängig verwendet werden.

## Kategorie {#category}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>category.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>category.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>category.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>CategoryList-Modell</p></li>
     <li><p>StartPointList-Modell</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>changed – CategoryList-Modell </p></li>
     <li><p>childrenFetched – CategoryList-Modell </p></li>
     <li><p>category:selected – CategoryList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## StartPointList {#startpointlist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>startpointlist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>startprocess.html (im Ordner „route“)</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>Category-Modell</p></li>
     <li><p>FavoriteCategoryFactory-Modell</p></li>
     <li><p>AllCategoryFactory-Modell</p></li>
     <li><p>StartPoint-Ansicht</p></li>
     <li><p>StartPointList-Modell</p></li>
     <li><p>StartPoint-Modell</p></li>
     <li><p>Task-Modell</p></li>
     <li><p>Task-Modell</p></li>
     <li><p>TaskList-Modell</p></li>
     <li><p>TeamTask-Modell</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>category:selected – CategoryList-Modell </p></li>
     <li><p>allStartpointsFetched – CategoryList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Komponenten StartPointList und CategoryList weisen dieselbe Modellklasse auf, sodass die erste Komponente von der zweiten abhängig ist. CategoryList greift auf die Informationen darüber zu, für welche Kategorie die Startpunkte angezeigt werden. Um StartPointList unabhängig zu verwenden, simulieren Sie den Ereignisauslöser über CategoryList.

## StartPoint {#startpoint}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>startpoint.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>startpoint.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>startpoint.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>Task-Modell</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td><p>change – StartPoint-Modell </p></td>
  </tr>
 </tbody>
</table>

## StartProcess {#startprocess}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>categorylist.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>startprocess.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>startprocess.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td>
    <ul>
     <li><p>Die meisten Dienstprogrammklassen</p> </li>
     <li><p>UserSearch</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td>
    <ul>
     <li><p>Category-Modell</p> </li>
     <li><p>FavoriteCategoryFactory-Modell</p> </li>
     <li><p>AllCategoryFactory-Modell</p> </li>
     <li><p>formrendering-Dienstprogramm</p> </li>
     <li><p>notes-Dienstprogramm</p> </li>
     <li><p>attachments-Dienstprogramm</p> </li>
     <li><p>taskactions-Dienstprogramm</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li><p>category:selected – CategoryList-Modell</p> </li>
     <li><p>change:invokedTask – StartPointList-Modell</p> </li>
     <li><p>change:formUrl – Task-Modell</p> </li>
     <li><p>startpoint:selected – StartPointList-Modell</p> </li>
     <li><p>forwarded – Task-Modell</p> </li>
     <li><p>abandoned – Task-Modell</p> </li>
     <li><p>unlocked – Task-Modell</p> </li>
     <li><p>locked – Task-Modell</p> </li>
     <li>attachmentURLFetched – Task-Modell</li>
     <li>newAttachment – Task-Modell</li>
     <li>prepareForSubmitComplete – Task-Modell </li>
     <li><p>submitComplete – Task-Modell</p> </li>
     <li><p>allStartpointsFetched – CategoryList-Modell</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Komponenten StartProcess und StartPointList weisen dieselbe Modellklasse auf. Diese Komponente wird relevant, wenn Sie in StartPointList einen Startpunkt auswählen.

## ProcessNameList {#processnamelist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>tracking.html (im Ordner „route“)</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>ProcessName-Modell</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>add – ProcessNameList-Modell </p></li>
     <li><p>fetched:processnames – ProcessNameList-Modell </p></li>
     <li><p>change – ProcessNameList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessNameList ist nicht von anderen Komponenten abhängig. Intern ist sie jedoch von der Modellklasse ProcessInstanceList abhängig, die wiederum von anderen Komponenten abhängig ist. Daher verwendet ProcessNameList viele Modellklassen wie ProcessInstanceList, ProcessInstance, TaskList, TeamTask und Task. Abgesehen von diesen Abhängigkeiten kann ProcessNameList unabhängig verwendet werden.

## ProcessName {#processname}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>processname.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>ProcessName (in processnamelist.js)</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>processname.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>ProcessInstanceList-Modell</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td><p>change – ProcessName-Modell </p></td>
  </tr>
 </tbody>
</table>

## ProcessInstanceList {#processinstancelist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>processinstancelist.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>tracking.html (im Ordner „route“)</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>ProcessName-Modell</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>processname:selected – ProcessNameList-Modell </p></li>
     <li><p>processname:instancesfetched – ProcessNameList-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessInstanceList erwartet ein Ereignis von ProcessNameList, das den Prozessnamen für das Abrufen und Anzeigen von Instanzen angibt. Um ProcessInstanceList unabhängig zu verwenden, simulieren Sie den Ereignisauslöser separat.

## ProcessInstance {#processinstance}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>processinstance.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>ProcessName (in processnamelist.js)</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>processinstance.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>TaskList-Modell</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td><p>change – ProcessInstance-Modell </p></td>
  </tr>
 </tbody>
</table>

## ProcessInstanceHistory {#processinstancehistory}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>processinstancehistory.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>processinstancehistory.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td>
    <ul>
     <li><p>ProcessName-Modell</p></li>
     <li><p>history-Dienstprogramm</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>processname:selected – ProcessNameList-Modell </p></li>
     <li><p>processinstance:selected – ProcessInstanceList-Modell </p></li>
     <li><p>tasksFetched – ProcessInstance-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessInstanceHistory erwartet ein Ereignis von ProcessInstanceList, das angibt, für welche Instanz der Verlauf angezeigt werden soll. Abgesehen von dieser Abhängigkeit kann die Komponente unabhängig verwendet werden.

## OutofOffice {#outofoffice}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>outofoffice.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>outofoffice.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>outofoffice.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>UserSearch</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>UserSearch-Ansicht</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li><p>outOfOfficeSettingsFetched – OutofOffice-Modell</p> </li>
     <li><p>outOfOfficeSettingsSaved – OutofOffice-Modell</p> </li>
     <li><p>processesFetched – OutofOffice-Modell</p> </li>
     <li><p>principalSelected – principalsearch-Ansicht</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>OutofOffice kann unabhängig verwendet werden.

## ShareQueue {#sharequeue}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>sharequeue.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>sharequeue.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>sharequeue.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>UserSearch</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>UserSearch-Ansicht</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li><p>queueAccessGranted – sharequeue-Modell</p> </li>
     <li><p>queueAccessRequested – sharequeue-Modell</p> </li>
     <li><p>grantedUsersFetched – sharequeue-Modell</p> </li>
     <li>accessibleUsersFetched – sharequeue-Modell</li>
     <li><p>queueAccessRevoked – sharequeue-Modell</p> </li>
     <li><p>queueAccessRemoved – sharequeue-Modell</p> </li>
     <li><p>principalSelected – principalsearch-Ansicht</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ShareQueue kann unabhängig verwendet werden.

## UISettings {#uisettings}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>uisettings.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>uisettings.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>uisettings.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td>
    <ul>
     <li><p>preferencesFetched – UISettings-Modell </p></li>
     <li><p>settingUpdated – UISettings-Modell </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>UISettings kann unabhängig verwendet werden.

## AppNavigation {#appnavigation}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>appnavigation.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>appnavigation.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>appnavigation.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>AppNavigation kann unabhängig verwendet werden.

## UserInfo {#userinfo}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>userinfo.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>userinfo.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>userinfo.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li>userImageUrlFetched – UserInfo-Modell</li>
     <li>sessionRenewed – userinfo-Modell  <br /> </li>
     <li>sessionExpired – userinfo-Modell </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>UserInfo kann unabhängig verwendet werden.

## WSError {#wserror}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p></td>
   <td><p>wserror.js</p></td>
  </tr>
  <tr>
   <td><p>Anzeigen</p></td>
   <td><p>wserror.js</p></td>
  </tr>
  <tr>
   <td><p>Vorlage</p></td>
   <td><p>wserror.html</p></td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p></td>
   <td><p>nicht vorhanden</p></td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p></td>
   <td><p>newWsError – WSError-Modell </p></td>
  </tr>
 </tbody>
</table>

## UserSearch {#usersearch}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>usersearch.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>usersearch.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>usersearch.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td>
    <ul>
     <li>principalSearched – principalsearch-Modell</li>
     <li>outOfOfficeInfoFetched – usersearch-Modell</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## SearchTemplate {#searchtemplate}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>searchtemplate.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>searchtemplate (in searchtemplatelist.js) </p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>searchtemplate.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td><p>templateFetched – searchtemplate-Modell</p> </td>
  </tr>
 </tbody>
</table>

## SearchTemplateList {#searchtemplatelist}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>tracking.html (im Ordner „route“)</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td><p>searchtemplate-Modell</p> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td><p>change – searchtemplatelist-Modell</p> </td>
  </tr>
 </tbody>
</table>

## SearchTemplateDetails {#searchtemplatedetails}

<table>
 <tbody>
  <tr>
   <td><p>Modell</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Anzeigen</p> </td>
   <td><p>searchtemplatedetails.js</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>searchtemplatedetails.html</p> </td>
  </tr>
  <tr>
   <td><p>Erfordert Komponenten</p> </td>
   <td><p>nicht vorhanden</p> </td>
  </tr>
  <tr>
   <td><p>JS-Abhängigkeiten</p> </td>
   <td>nicht vorhanden<br /> </td>
  </tr>
  <tr>
   <td><p>Listener-Ereignisse (Ereignisname - Trigger)</p> </td>
   <td><p>searchTemplate:selected - searchtemplate-Modell</p> </td>
  </tr>
 </tbody>
</table>
