---
title: Aktualisieren des Links zur Dokumentation
description: Erfahren Sie, wie Sie das Ziel des Workspace-Hilfe-Links in AEM Forms Workspace aktualisieren, sodass es auf Ihren benutzerdefinierten Link zur Dokumentation verweist.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: ca637bea-05c1-4920-9283-e782f07607de
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
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
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '142'
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
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63_de" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
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
