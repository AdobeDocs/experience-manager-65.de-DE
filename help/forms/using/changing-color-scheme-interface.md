---
title: Ändern des Farbschemas der Benutzeroberfläche
description: So ändern Sie das selektiv das Farbschema der Benutzeroberfläche von AEM Forms Workspace.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: e0a261a2-518b-4984-a5b5-24f0b9222e24
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 100%

---

# Ändern des Farbschemas der Benutzeroberfläche {#changing-the-color-scheme-of-the-interface}

Sie können das Farbschema von Bereichen der Benutzeroberfläche von AEM Forms Workspace Ihren Anforderungen entsprechend ändern. Im Folgenden finden Sie einige Beispiele für repräsentative Anpassungen des Farbschemas. Zusätzlich zu den in diesem Artikel besprochenen Schritten finden Sie mehr unter [Generische Schritte für die Anpassung des AEM Forms-Arbeitsbereichs](/help/forms/using/generic-steps-html-workspace-customization.md).

## Navigationsleiste oben {#top-navigation-bar}

### Verwenden eines Hintergrundbilds {#using-background-image}

So aktualisieren Sie die Navigationsleiste am oberen Rand von AEM Forms Workspace

1. Erstellen Sie ein Hintergrundbild, um die Farbe zu aktualisieren. Geben Sie der Datei den Namen „newBackground.jpg“.
1. Laden Sie die Datei des Hintergrundbilds mithilfe eines WebDAV-Clients in den Ordner „/apps/ws/images“ hoch.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [WebDAV-Zugriff](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=de).

1. Verweisen Sie auf das neue Hintergrundbild in „/apps/ws/css/newStyle.css“, indem Sie den folgenden Stil hinzufügen.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Verwenden der Farbeigenschaft in CSS {#using-color-property-in-css}

1. Fügen Sie in „newStyle.css“ unter „/apps/ws/css“ den folgenden Stil hinzu:

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Kategoriekomponente {#category-component}

Die Kategoriekomponente zeigt die verschiedenen Kategorien Ihrer Aufgaben im linken Bereich an. Um die Farbe zu ändern, definieren Sie die Hintergrundfarbe im `.category`-Element der CSS-Datei.

## Task-Komponente {#task-component}

Aufgaben werden im mittleren Fenster, der TaskList-Komponente, angezeigt. Um die Farbe zu ändern, ändern Sie den Stil, der mit .task-Auswahl im Stylesheet verknüpft ist.
