---
title: Ändern des Farbschemas der Benutzeroberfläche
seo-title: Ändern des Farbschemas der Benutzeroberfläche
description: Sie können das Farbschema der Benutzeroberfläche von AEM Forms Workspace selektiv ändern.
seo-description: Sie können das Farbschema der Benutzeroberfläche von AEM Forms Workspace selektiv ändern.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: e0a261a2-518b-4984-a5b5-24f0b9222e24
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 76%

---

# Ändern des Farbschemas der Benutzeroberfläche {#changing-the-color-scheme-of-the-interface}

Sie können das Farbschema von Bereichen der Benutzeroberfläche von AEM Forms Workspace Ihren Anforderungen entsprechend ändern. Im Folgenden sehen Sie einige Beispiele für repräsentative Anpassungen des Farbschemas. Zusätzlich zu den Schritten, die in diesem Artikel beschrieben werden, finden Sie unter [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).

## Navigationsleiste oben {#top-navigation-bar}

### Verwenden eines Hintergrundbilds {#using-background-image}

Aktualisieren der Navigationsleiste oben in AEM Forms Workspace.

1. Erstellen Sie ein Hintergrundbild, um die Farbe zu aktualisieren. Benennen Sie die Datei als newBackground.jpg.
1. Laden Sie die Hintergrundbild-Datei mit einem WebDAV-Client in den Ordner „/apps/ws/images“ hoch.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Verweisen Sie in /apps/ws/css/newStyle.css auf das neue Hintergrundbild, indem Sie folgenden Stil hinzufügen.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Verwenden der Farbeigenschaft in CSS   {#using-color-property-in-css}

1. Fügen Sie in newStyle.css unter „/apps/ws/css“ den folgenden Stil hinzu.

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Category-Komponente {#category-component}

In der Category-Komponente werden die verschiedenen Kategorien Ihrer Aufgaben im linken Fenster angezeigt. Um die Farbe zu ändern, definieren Sie die Hintergrundfarbe im Element `.category` der CSS-Datei.

## Task-Komponente {#task-component}

Aufgaben werden im mittleren Fenster, der TaskList-Komponente, angezeigt. Um die Farbe zu ändern, ändern Sie den Stil, der mit .task-Auswahl im Stylesheet verknüpft ist.
