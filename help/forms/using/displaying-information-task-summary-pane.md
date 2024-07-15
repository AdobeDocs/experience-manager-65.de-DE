---
title: Anzeigen von Informationen in der Aufgabenzusammenfassung
description: In AEM Forms Workspace kann ein Bedienfeld zur Aufgabenzusammenfassung konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige Web-Seite anzuzeigen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 0b3087fe-a3fb-4eac-ad4b-c123526e8195
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Anzeigen von Informationen in der Aufgabenzusammenfassung {#displaying-information-in-the-task-summary-pane}

Wenn Sie eine Aufgabe in AEM Forms Workspace öffnen, kann eine Zusammenfassung der Aufgabe in einem entsprechenden Fenster angezeigt werden. Diese zusätzlichen und relevanten Informationen für eine Aufgabe bieten den Endbenutzenden von AEM Forms Workspace einen Mehrwert.

Mit AEM Forms Workspace können Sie eine Web-Seite auswählen, die in der Aufgabenzusammenfassung angezeigt werden soll. Es kann ein Vorgang erstellt werden, um eine Aufgabenzusammenfassung mithilfe von Workbench anzuzeigen.

1. Erstellen Sie einen Prozess „Aufgabe zuweisen“ in Workbench. Weitere Informationen zum Vorgang „Aufgabe zuweisen“ finden Sie im Dienstreferenzthema in der [Workbench-Hilfe](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Wenn eine TaskSummary-URL vorhanden ist, wird standardmäßig die Ansicht „Aufgabenzusammenfassung“ statt der Formularansicht geöffnet. In diesem Fall wird das Formular auch dann nicht im maximierten Modus geöffnet, wenn die Benutzerin bzw. der Benutzer unter „Aufgabe zuweisen“ die Option „Formular im maximierten Modus öffnen“ aktiviert.

1. Konfigurieren Sie das URL-Feld für die Aufgabenzusammenfassung. Sie können einen Literalwert, eine Vorlage, eine Variable oder einen XPath-Ausdruck angeben.
1. Nachfolgend finden Sie ein Beispiel für die Anzeige von Informationen auf der Aufgabenzusammenfassungsseite.

   * Melden Sie sich bei der CRXDE Lite-Umgebung unter `https://'[server]:[port]'/lc/crx/de` an.
   * `Create a node`**SampleSummary** ` under `/content` with type `nt:unstructured`. In the properties of this node, add `sling:resourceType` of type String and value `SampleSummary`. In the Access Control List of this node, add an entry for `PERM_WORKSPACE_USER` allowing `jcr:read` privileges.`
   * `Create a folder`**SampleSummary** unter `/apps`. Fügen Sie in der Zugriffssteuerungsliste von `/apps/SampleSummary` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, wobei die Berechtigungen `jcr:readprivileges` zugelassen werden.
   * `Create a file `html.esp` at `/apps/SampleSummary`. For example, add the following lines in `html.esp`.`

   ```html
   <html>
       <body>
           <h1>Sample Summary</h1>
           <br/>
           <p>Hello Sir!
               <br/>
               This is sample summary page for this task.
           </p>
       </body>
   </html>
   ```

   * Legen Sie im Schritt „Aufgabe zuweisen“ den Wert der Aufgabenzusammenfassungs-URL auf `/lc/content/SampleSummary.html` fest.
   * Wenn die Aufgabe, die mit diesem Schritt „Aufgabe zuweisen“ verknüpft ist, in AEM Forms Workspace geöffnet wird, wird `html.esp` in `/apps/SampleSummary` in der Aufgabenzusammenfassung gerendert.
