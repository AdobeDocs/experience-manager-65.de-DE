---
title: Abrufen von Aufgabenvariablen in der Zusammenfassungs-URL
description: Gehen Sie wie folgt vor, um die Informationen zu einer Aufgabe wiederzuverwenden und eine Zusammenfassungs-URL zu generieren, um eine Aufgabe zusammenzufassen oder zu beschreiben.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b5e27b54-d141-48dd-a4ed-dd0a691319a5
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 20%

---

# Abrufen von Aufgabenvariablen in der Zusammenfassungs-URL {#getting-task-variables-in-summary-url}

Auf der Zusammenfassungsseite werden aufgabenbezogene Informationen angezeigt. In diesem Artikel wird beschrieben, wie Sie aufgabenbezogene Informationen auf der Zusammenfassungsseite wiederverwenden können.

In dieser Beispielorchestrierung sendet ein Mitarbeiter ein Urlaubsantragsformular. Das Antragsformular wird dann zur Genehmigung an den Vorgesetzten des Mitarbeiters weitergeleitet.

1. Erstellen eines HTML-Renderers (html.esp) für resourceType **Employees/PtoApplication**.

   Der Renderer geht davon aus, dass die folgenden Eigenschaften für den Knoten festgelegt werden:

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

1. Ändern Sie die Orchestrierung, um die vier Eigenschaften aus den gesendeten Formulardaten zu extrahieren. Erstellen Sie anschließend einen Knoten des Typs CRX . **Employees/PtoApplication**, wobei die Eigenschaften ausgefüllt sind.

   1. Erstellen eines Prozesses **PTO-Zusammenfassung erstellen** und verwenden Sie dies als Teilprozess vor dem **Aufgabe zuweisen** -Operation in Ihrer Orchestrierung.
   1. Definieren Sie **employeeName**, **employeeID**, **ptoReason**, **totalDays** und **nodeName** als Eingabevariablen in dem neuen Prozess. Diese Variablen werden als gesendete Formulardaten übergeben.

      Definieren Sie außerdem eine Ausgabevariable. **ptoNodePath** wird beim Festlegen der Zusammenfassungs-URL verwendet.

   1. Verwenden Sie im Prozess **create PTO summary** die Komponente **set value**, um die Eingabedetails in einer Zuordnung **nodeProperty** (**nodeProps** ) festzulegen.

      Die Schlüssel in dieser Zuordnung sollten mit den Schlüsseln übereinstimmen, die im vorherigen Schritt im HTML-Renderer definiert wurden.

      Fügen Sie außerdem eine **sling:resourceType** Schlüssel mit Wert **Employees/PtoApplication** in der Karte.

   1. Teilprozess verwenden **storeContent** aus dem **ContentRepositoryConnector** im **PTO-Zusammenfassung erstellen** -Prozess. Dieser Teilprozess erstellt einen CRX-Knoten.

      Es sind drei Eingabevariablen erforderlich:

      * **Ordnerpfad**: Der Pfad, in dem der neue CRX-Knoten erstellt wird. Legen Sie den Pfad als **/content**.
      * **Knotenname**: Weisen Sie diesem Feld die Eingabevariable nodeName zu. Dies ist eine eindeutige Knotennamen-Zeichenfolge.
      * **Knotentyp**: Definieren Sie den Typ als **nt:unstructured**. Die Ausgabe dieses Prozesses ist nodePath. Der nodePath ist der CRX-Pfad des neu erstellten Knotens. NodePath ist die endgültige Ausgabe der **PTO erstellen** Zusammenfassungsprozess.

   1. Übergeben Sie die gesendeten Formulardaten (**employeeName**, **employeeID**, **ptoReason**, und **totalDays**) als Eingabe für den neuen Prozess **PTO-Zusammenfassung erstellen**. Übernehmen Sie die Ausgabe als **ptoSummaryNodePath**.

1. Definieren Sie die Zusammenfassungs-URL als XPath-Ausdruck, der die Serverdetails zusammen mit **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wenn Sie in AEM Forms Workspace eine Aufgabe öffnen, greift die Zusammenfassungs-URL auf den CRX-Knoten zu und der HTML-Renderer zeigt die Zusammenfassung an.

Das Zusammenfassungslayout kann geändert werden, ohne den Prozess zu ändern. Der HTML-Renderer zeigt die Zusammenfassung entsprechend an.
