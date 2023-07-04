---
title: Ändern des Organisationslogos für das Branding
seo-title: Changing the organization logo for branding
description: Um AEM Forms Workspace mit Markenzeichen zu versehen, stellen Sie das Logo Ihres Unternehmens bereit, indem Sie das Standardlogo anpassen.
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 49572f2a-f3ec-4ee6-98b8-2563de1cf96c
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Ändern des Organisationslogos für das Branding {#changing-the-organization-logo-for-branding}

Das Unternehmenslogo wird in der linken oberen Ecke des AEM Forms Workspace-Fensters angezeigt. Um das Logo zu aktualisieren, befolgen Sie die [Allgemeine Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) und dann die folgenden Schritte.

1. Erstellen Sie ein Logo und benennen Sie die Datei als `NewWorkspace.png` Platzieren Sie die Bilddatei mit einem WebDAV-Client im Ordner „/apps/ws/images“.

   >[!NOTE]
   >
   >Die empfohlene Größe des Logobilds beträgt 218 px × 20 px.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).

1. Erstellen Sie einen Verweis auf das neue Logo im Stylesheet bei „/apps/ws/css/newStyle.css“, indem Sie folgenden Stil hinzufügen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
