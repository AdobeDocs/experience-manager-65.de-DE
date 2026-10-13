---
title: Anzeigen zusätzlicher Daten in der Aufgabenliste
description: Gehen Sie wie folgt vor, um durch Anpassen der Anzeige der Aufgabenliste von LiveCycle AEM Forms Workspace weitere Informationen außer den standardmäßig angezeigten Informationen darzustellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: f8b84f13-02d3-4787-95e1-25fd684e6d3b
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
source-wordcount: '288'
ht-degree: 100%
---
# Anzeigen zusätzlicher Daten in der Aufgabenliste{#displaying-additional-data-in-todo-list}

Standardmäßig zeigt die Aufgabenliste von AEM Forms Workspace den Anzeigenamen und die Beschreibung von Aufgaben an. Sie können jedoch andere Informationen wie Erstellungsdatum und Termin hinzufügen. Sie können auch Symbole hinzufügen und den Stil der Anzeige ändern.

![Abbildung der Registerkarte „Aufgaben“ von HTML Workspace mit der Standardkonfiguration](assets/html-todo-list.png)

Dieser Artikel führt die einzelnen Schritte auf, um Anzeigeinformationen für jede Aufgabe in der Aufgabenliste hinzuzufügen.

## Was kann hinzugefügt werden {#what-can-be-added}

Sie können die verfügbaren Informationen der Datei in `task.json` hinzufügen, die vom Server gesendet wurde. Die Informationen können als normaler Text hinzugefügt werden, oder Sie können Stile verwenden, um die Informationen zu formatieren.

Weitere Informationen über die JSON-Objektbeschreibung finden Sie in [diesem](/help/forms/using/html-workspace-json-object-description.md) Artikel.

## Anzeigen von Informationen über eine Aufgabe {#displaying-information-on-a-task}

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md).
1. Um zusätzliche Information für eine Aufgabe anzuzeigen, müssen die entsprechenden Schlüssel-Wert-Paare innerhalb des Aufgabenblocks von `translation.json` hinzugefügt werden.

   Ändern Sie zum Beispiel `/apps/ws/locales/en-US/translation.json` für Englisch:

   ```json
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Fügen Sie entsprechende Schlüssel-Wert-Paare für alle unterstützten Sprachen hinzu.

1. Fügen Sie beispielsweise Informationen im Aufgabenblock hinzu:

   ```json
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## Definieren von CSS für die neue Eigenschaft {#defining-css-for-the-new-property}

1. Sie können einen Stil auf die einer Aufgabe hinzugefügten Informationen (Eigenschaft) anwenden. Dazu müssen Sie Stilinformationen für die neue Eigenschaft hinzufügen, die `/apps/ws/css/newStyle.css` hinzugefügt wurde.

   Fügen Sie beispielsweise Folgendes hinzu:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Hinzufügen eines Eintrags in der HTML-Vorlage {#adding-entry-in-the-html-template}

Schließlich müssen Sie für jede Eigenschaft, die Sie der Aufgabe hinzufügen möchten, einen Eintrag ins Entwicklerpaket aufnehmen. Informationen zum Erstellen eines Eintrags finden Sie unter „Erstellen von AEM Forms Workspace-Code“.

1. Kopieren `task.html`:

   * von: `/libs/ws/js/runtime/templates/`
   * in: `/apps/ws/js/runtime/templates/`

1. Fügen Sie `/apps/ws/js/runtime/templates/task.html` die neuen Informationen hinzu.

   Fügen Sie beispielsweise Folgendes unter `div class="taskProperties"` hinzu:

   ```jsp
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
