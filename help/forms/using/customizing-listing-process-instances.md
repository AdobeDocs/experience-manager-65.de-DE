---
title: Anpassen der Auflistung von Prozessinstanzen
description: Gehen Sie wie folgt vor, um die Eigenschaften anzupassen, die in der Prozessinstanz in AEM Forms Workspace angezeigt werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b27ffe92-8491-43a0-bf42-613eb39a606e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 58%

---

# Anpassen der Auflistung von Prozessinstanzen {#customizing-the-listing-of-process-instances}

Die Liste der Prozessinstanzen wird auf der Registerkarte &quot;Verfolgung&quot;von AEM Forms Workspace angezeigt.

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
   <td>Initiator</td>
   <td>Name des Initiators der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>Kennung des Initiators der Prozessinstanz.</td>
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
   <td>0 = Initiiert<br /> 1 = Läuft<br /> 2 = Abgeschlossen<br /> 3 = Abgeschlossen<br /> 4 = Beendet<br /> 5 = Beenden<br /> 6 = Ausgesetzt<br /> 7 = Aussetzen<br /> 8 = Aufhebung der Aussetzung</td>
  </tr>
  <tr>
   <td>processName</td>
   <td>Name des Prozesses.</td>
  </tr>
  <tr>
   <td>processStartTime</td>
   <td>Zeitstempel, zu dem der Prozess gestartet wurde.</td>
  </tr>
  <tr>
   <td>processVariables</td>
   <td>Array von Objekten aus Prozessvariablen. Jedes Prozessvariablenobjekt enthält <strong>name</strong> (Name der Prozessvariablen), <strong>value</strong> (Wert der Prozessvariablen) und<strong> type</strong> (der Typ der Prozessvariablen).</td>
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
