---
title: Anpassen von Registerkarten für eine Aufgabe
seo-title: Anpassen von Registerkarten für eine Aufgabe
description: Gehen Sie wie folgt vor, um die Namen der Registerkarten für Ihre Aufgaben in LiveCycle AEM Forms Workspace anzupassen.
seo-description: Gehen Sie wie folgt vor, um die Namen der Registerkarten für Ihre Aufgaben in LiveCycle AEM Forms Workspace anzupassen.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 51%

---


# Anpassen von Registerkarten für eine Aufgabe {#customizing-tabs-for-a-task}

Sie können Registerkartennamen für die Komponente `Start Process` in der Ansicht `Start Process` und `Task Details` in der Ansicht `ToDo` anpassen.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Ändern Sie den Wert von `tabname`in der Datei `translation.json`.

   Ändern Sie beispielsweise `/apps/ws/locales/en-US/translation.json` für Englisch in Folgendes.

   * Verwenden Sie für Aufgaben, die im Beginn ausgelöst werden, das folgende Codefragment aus dem Block `"startprocess" : {}`.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Verwenden Sie für Aufgaben in Aufgaben den folgenden Codeausschnitt aus dem Block `"todo" : {}`.

   ```json
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Fügen Sie das entsprechende Schlüssel-Wert-Paar für alle unterstützten Sprachen hinzu.
