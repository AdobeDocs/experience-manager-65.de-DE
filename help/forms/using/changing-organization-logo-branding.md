---
title: Ändern des Organisationslogos für das Branding
seo-title: Ändern des Organisationslogos für das Branding
description: Um AEM Forms Workspace mit Markenzeichen zu versehen, stellen Sie das Logo Ihres Unternehmens durch Anpassen des Standardlogos bereit.
seo-description: Um AEM Forms Workspace mit Markenzeichen zu versehen, stellen Sie das Logo Ihres Unternehmens durch Anpassen des Standardlogos bereit.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 49572f2a-f3ec-4ee6-98b8-2563de1cf96c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 82%

---

# Ändern des Organisationslogos für das Branding {#changing-the-organization-logo-for-branding}

Das Unternehmenslogo wird in der linken oberen Ecke des AEM Forms Workspace-Fensters angezeigt. Um das Logo zu aktualisieren, führen Sie die [generischen Schritte der AEM Forms Workspace-Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) und dann die folgenden Schritte durch.

1. Erstellen Sie ein Logo und benennen Sie die Datei als `NewWorkspace.png` Platzieren Sie die Bilddatei mit einem WebDAV-Client im Ordner „/apps/ws/images“.

   >[!NOTE]
   >
   >Die empfohlene Größe des Logobilds beträgt 218 px × 20 px.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Erstellen Sie einen Verweis auf das neue Logo im Stylesheet bei „/apps/ws/css/newStyle.css“, indem Sie folgenden Stil hinzufügen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
