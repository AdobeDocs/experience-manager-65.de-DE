---
title: Abrufen von Aufgabenvariablen in einer Zusammenfassungs-URL
description: Erfahren Sie, wie Sie die Informationen zu einer Aufgabe wiederverwenden und eine Zusammenfassungs-URL für die Zusammenfassung oder Beschreibung einer Aufgabe generieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b5e27b54-d141-48dd-a4ed-dd0a691319a5
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '431'
ht-degree: 100%

---

# Abrufen von Aufgabenvariablen in einer Zusammenfassungs-URL {#getting-task-variables-in-summary-url}

Auf der Zusammenfassungsseite werden aufgabenbezogene Informationen angezeigt. Dieser Artikel beschreibt, wie Sie aufgabenbezogene Informationen auf der Zusammenfassungsseite wiederverwenden können.

In dieser Beispielorchestrierung reicht jemand einen Urlaubsantrag ein. Das Antragsformular wird dann zur Genehmigung an die Vorgesetzten weitergeleitet.

1. Erstellen Sie einen Beispiel-HTML-Renderer (html.esp) für resourceType **Employees/PtoApplication**.

   Der Renderer setzt voraus, dass die folgenden Eigenschaften für den Knoten festgelegt wurden:

   * ename
   * empid
   * reason
   * duration

   >[!NOTE]
   >
   >Dieser Renderer stellt die Übersichtsseitenvorlage dar.

   Der folgende Beispielcode für diesen Renderer ist enthalten in:

   `apps/Employees/PtoApplication/html.esp`

   ```html
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. Ändern Sie die Orchestrierung, um die vier Eigenschaften aus den übermittelten Formulardaten zu extrahieren. Anschließend erstellen Sie in CRX einen Knoten vom Typ **Employees/PtoApplication** mit ausgefüllten Eigenschaften.

   1. Erstellen Sie einen Prozess **create PTO summary** und verwenden Sie diesen als Teilprozess vor dem Vorgang **Aufgabe zuweisen** in der Orchestrierung.
   1. Definieren Sie **employeeName**, **employeeID**, **ptoReason**, **totalDays** und **nodeName** als Eingabevariablen in dem neuen Prozess. Diese Variablen werden als gesendete Formulardaten übergeben.

      Definieren Sie auch eine Ausgabevariable **ptoNodePath**, die bei der Festlegung der Zusammenfassungs-URL verwendet wird.

   1. Verwenden Sie im Prozess **create PTO summary** die Komponente **set value**, um die Eingabedetails in einer Zuordnung **nodeProperty** (**nodeProps** ) festzulegen.

      Die Schlüssel in dieser Zuordnung müssen identisch mit den Schlüsseln sein, die in Ihrem HTML-Renderer im vorherigen Schritt definiert wurden.

      Fügen Sie in der Zuordnung außerdem einen Schlüssel **sling:resourceType** mit dem Wert **Employees/PtoApplication** hinzu.

   1. Verwenden Sie den Teilprozess **storeContent** aus dem **ContentRepositoryConnector**-Dienst im Prozess **create PTO summary**. Dieser Teilprozess erstellt einen CRX-Knoten.

      Er akzeptiert drei Eingabevariablen:

      * **Ordnerpfad**: Dies ist der Pfad, in dem der neue CRX-Knoten erstellt wird. Legen Sie den Pfad als **/content** fest.
      * **Knotenname**: Weisen Sie diesem Feld die Eingabevariable „nodeName“ zu. Dies ist eine eindeutige Knotennamen-Zeichenfolge.
      * **Knotentyp**: Definieren Sie den Typ als **nt:unstructured**. Die Ausgabe dieses Prozesses ist „nodePath“. „nodePath“ ist der CRX-Pfad des neu erstellten Knotens. „nodePath“ stellt die endgültige Ausgabe des Prozesses **create PTO summary** dar.

   1. Übergeben Sie die gesendeten Formulardaten (**employeeName**, **employeeID**, **ptoReason** und **totalDays**) als Eingabe für den neuen Prozess **create PTO summary**. Übernehmen Sie die Ausgabe als **ptoSummaryNodePath**.

1. Definieren Sie die Zusammenfassungs-URL als XPath-Ausdruck, der die Server-Details zusammen mit **ptoSummaryNodePath** enthält.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wenn Sie in AEM Forms Workspace eine Aufgabe öffnen, greift die Zusammenfassungs-URL auf den CRX-Knoten zu und der HTML-Renderer zeigt die Zusammenfassung an.

Das Zusammenfassungs-Layout kann bearbeitet werden, ohne den Prozess zu ändern. Der HTML-Renderer zeigt die Zusammenfassung entsprechend an.
