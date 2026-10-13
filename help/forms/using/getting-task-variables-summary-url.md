---
title: Abrufen von Aufgabenvariablen in einer Zusammenfassungs-URL
description: Erfahren Sie, wie Sie die Informationen zu einer Aufgabe wiederverwenden und eine Zusammenfassungs-URL für die Zusammenfassung oder Beschreibung einer Aufgabe generieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b5e27b54-d141-48dd-a4ed-dd0a691319a5
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 95%
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

      Fügen Sie außerdem einen **sling:resourceType**-Schlüssel mit dem Wert **Employees/PtoApplication** in der Zuordnung hinzu.

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
