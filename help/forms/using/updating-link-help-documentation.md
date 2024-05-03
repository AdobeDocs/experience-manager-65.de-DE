---
title: Aktualisieren des Links zur Dokumentation
description: Erfahren Sie, wie Sie das Ziel des Workspace-Hilfe-Links in AEM Forms Workspace aktualisieren, sodass es auf Ihren benutzerdefinierten Link zur Dokumentation verweist.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: ca637bea-05c1-4920-9283-e782f07607de
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---

# Aktualisieren des Links zur Dokumentation {#updating-the-link-to-the-documentation}

Sie können auf den standardmäßigen Hilfeinhalt für AEM Forms Workspace zugreifen, indem Sie **Hilfe > Workspace-Hilfe** auswählen. Dies verweist auf die Online-Dokumentation auf der Adobe-Website. Sie können den Verweis jedoch so aktualisieren, dass er auf eine andere URL verweist.

Betrachten Sie die folgenden Anwendungsfälle, in denen es angebracht wäre, die standardmäßige Hilfe-URL zu ändern:

* Zur Bereitstellung lokalisierter Hilfeinhalte in einer Sprache Ihrer Wahl.
* Zur Bereitstellung angepasster Hilfeinhalte für Ihre Angepassungen von Workspace.

Um die URL der Onlinedokumentation zu aktualisieren, führen Sie die Schritte unter [Generische Schritte zur Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md) und dann die folgenden Schritte aus.

1. Kopieren Sie die `userinfo.html`-Datei aus `/libs/ws/js/runtime/templates` nach `/apps/ws/js/runtime/templates`.
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
   1. Suchen und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/userinfo.html` mit `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
