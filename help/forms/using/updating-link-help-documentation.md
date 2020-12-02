---
title: Aktualisieren des Links zur Dokumentation
seo-title: Aktualisieren des Links zur Dokumentation
description: Gehen Sie wie folgt vor, um durch Aktualisieren des Link-Ziels für Workspace-Hilfe in AEM Forms auf Ihren benutzerdefinierten Link zur Dokumentation zu verweisen.
seo-description: Gehen Sie wie folgt vor, um durch Aktualisieren des Link-Ziels für Workspace-Hilfe in AEM Forms auf Ihren benutzerdefinierten Link zur Dokumentation zu verweisen.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 94%

---


# Aktualisieren des Links zur Dokumentation {#updating-the-link-to-the-documentation}

Sie können auf den Standardhilfeinhalt für HTML Workspace zugreifen, indem Sie **Hilfe > Workspace-Hilfe** auswählen. Dies verweist auf die Onlinedokumentation auf der Website von Adobe. Sie können den Verweis jedoch in jede andere URL ändern.

Berücksichtigen Sie die folgenden Anwendungsfälle, wenn Sie die Standardhilfe-URL ändern:

* Für lokalisierte Hilfe in einer Sprache Ihrer Wahl.
* Zur Bereitstellung angepasster Hilfeinhalte für Ihre Angepassungen von Workspace.

Um die URL der Onlinedokumentation zu aktualisieren, führen Sie die Schritte unter [Generische Schritte zur Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md) und dann die folgenden Schritte aus.

1. Kopieren Sie die Datei `userinfo.html` von `/libs/ws/js/runtime/templates` nach `/apps/ws/js/runtime/templates`.
1. Änderung:

   ```html
   <ul class="helpmenu">
     <li>
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

   in

   ```html
   <ul class="helpmenu">
     <li>
       <a href="<!--place new help url here-->" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.
   1. Suchen und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/userinfo.html` durch `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
