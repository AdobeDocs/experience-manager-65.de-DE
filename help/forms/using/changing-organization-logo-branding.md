---
title: Ändern des Organisationslogos für das Branding
description: Um AEM Forms Workspace mit Markenzeichen zu versehen, stellen Sie das Logo Ihres Unternehmens bereit, indem Sie das Standardlogo anpassen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 49572f2a-f3ec-4ee6-98b8-2563de1cf96c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '119'
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
   >Weitere Informationen finden Sie unter [WebDAV-Zugriff](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=de).

   [WebDAV-Zugriff](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=de)

1. Erstellen Sie einen Verweis auf das neue Logo im Stylesheet bei „/apps/ws/css/newStyle.css“, indem Sie folgenden Stil hinzufügen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
