---
title: Anpassen der Auflistung von Prozessinstanzen
description: Erfahren Sie, wie Sie die Eigenschaften anpassen, die in der Prozessinstanz in AEM Forms Workspace angezeigt werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b27ffe92-8491-43a0-bf42-613eb39a606e
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
source-wordcount: '294'
ht-degree: 100%
---
# Anpassen der Auflistung von Prozessinstanzen {#customizing-the-listing-of-process-instances}

Die Prozessinstanzliste wird auf der Registerkarte „Tracking“ von AEM Forms Workspace angezeigt.

In der Prozessinstanzliste zeigt AEM Forms Workspace für jede Prozessinstanz einige Eigenschaften dieser Instanz. Die folgenden Eigenschaften sind für jede Prozessinstanz verfügbar. Diese Eigenschaften werden als Attribute im Prozessinstanz-Komponentenmodell gespeichert und sind in dessen Ansicht und Vorlage verfügbar.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>description</td>
   <td>Beschreibung der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>Name der Initiatorin bzw. des Initiators der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>ID der Initiatorin bzw. des Initiators der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>processCompleteTime</td>
   <td>Zeitstempel zum Zeitpunkt, zu dem der Prozess abgeschlossen wurde.</td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>ID der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>processInstanceStatus</td>
   <td>0 = Initiiert<br /> 1 = Wird ausgeführt<br /> 2 = Abgeschlossen<br /> 3 = Wird abgeschlossen<br />4 = Beendet<br /> 5 = Wird beendet<br /> 6 = Ausgesetzt<br /> 7 = Wird ausgesetzt<br /> 8 = Aussetzen wird aufgehoben</td>
  </tr>
  <tr>
   <td>processName</td>
   <td>Name des Prozesses.</td>
  </tr>
  <tr>
   <td>processStartTime</td>
   <td>Zeitstempel zum Zeitpunkt, als der Prozess gestartet wurde.</td>
  </tr>
  <tr>
   <td>processVariables</td>
   <td>Array von Objekten aus Prozessvariablen. Jedes Objekt einer Prozessvariable enthält <strong>name</strong> (den Namen der Prozessvariable), <strong>value</strong> (den Wert der Prozessvariable) und <strong>type</strong> (den Typ der Prozessvariable).</td>
  </tr>
 </tbody>
</table>

**Beispiel:**

Um die Eigenschaft `description` der Prozessinstanz auf der Prozessinstanzkarte anzuzeigen, führen Sie die folgenden Schritte aus.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Gehen Sie folgendermaßen vor:

   1. Kopieren Sie /libs/ws/js/runtime/templates/processinstance.html nach /apps/ws/js/runtime/templates/, wenn es nicht existiert. Klicken Sie auf **Alle speichern**.
   1. Fügen Sie die Prozessbeschreibung div mit class = „processDescription“ in processinstance.html hinzu.

   ```jsp
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.
   1. Suchen und Ersetzen `text!/lc/libs/ws/js/runtime/templates/processinstance.html`mit `text!/lc/`**apps**/ws/js/runtime/templates/processinstance.html

1. Die oben genannten Änderungen erfordern möglicherweise ein Update der CSS-Datei, indem Sie wie folgt einen Eintrag im Stylesheet /apps/ws/css/newStyle.css hinzufügen:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement and user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
