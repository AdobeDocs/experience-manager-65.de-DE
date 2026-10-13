---
title: Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server
description: Sie können AEM Forms Workspace in Microsoft Office SharePoint Server integrieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
exl-id: d080932f-d5fb-482d-9329-62da5df10362
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
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
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 93%
---
# Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server{#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Voraussetzungen**

**Vorausgesetztes Wissen**
Bevor Sie AEM Forms Workspace zum SharePoint-Server hinzufügen können, benötigen Sie Zugriff auf SharePoint-Server mit den entsprechenden Berechtigungen. Außerdem müssen Sie die URL für den Zugriff auf Workspace kennen. Bei den folgenden Schritten wird davon ausgegangen, dass Sie mit SharePoint Server vertraut sind. Weitere Informationen zu Webparts in SharePoint Server finden Sie unter „Webparts in Windows SharePoint-Diensten“.

**Benutzerebene**
Anfang

Sie können AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server (z. B. Microsoft Office SharePoint Server 2007) verwenden. Benutzer können auf AEM Forms Workspace zugreifen, indem sie mithilfe eines Webbrowsers eine Verbindung zu Ihrem SharePoint Server herstellen und so eine einheitliche Plattform erhalten. In diesem Artikel lernen Sie die grundlegenden Schritte zum Anzeigen von AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server kennen. Sie können die in diesem Artikel beschriebenen Schritte ausführen, um ein einheitliches Erlebnis zu bieten, sodass Benutzende, die eine Verbindung zu Ihrem SharePoint-Server herstellen, von demselben Port aus auf AEM Forms Workspace zugreifen können.

>[!NOTE]
>
>Die Schritte, die in diesem Artikel aufgeführt sind, gelten für Microsoft SharePoint Server 2007. Sie können auch HTML Workspace mit anderen unterstützten Versionen von Microsoft SharePoint konfigurieren.

## Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Führen Sie die folgenden Schritte aus, um AEM Forms Workspace in einen Webpart zu integrieren:

1. Navigieren Sie in einem Webbrowser zur SharePoint-Website, wie etwa `https://[myMOSSserver]:44299/default.aspx`, wobei `[myMOSSserver]` für den Namen oder die IP-Adresse von Sharepoint Server steht.

   >[!NOTE]
   >
   >44299 ist die Standard-Port-Nummer für den SharePoint-Server. Die Port-Nummer hängt von Ihrer Installation des SharePoint-Servers ab.

1. Klicken Sie oben rechts auf der Web-Seite auf **Site-Aktionen** und wählen Sie **Seite bearbeiten** aus.
1. Klicken Sie auf die Schaltfläche **Webpart hinzufügen.**
1. Wählen Sie im Web-Seiten-Dialogfeld „Webparts hinzufügen“ unter „Verschiedenes“ die Option **Seiten-Viewer-Webpart** aus und klicken Sie anschließend auf **Hinzufügen**.
1. Klicken Sie im Feld „Seiten-Viewer-Webpart“ auf **Bearbeiten** und wählen Sie **Freigegebenen Webpart ändern**.

   >[!NOTE]
   >
   >Das Feld „Seiten-Viewer-Webpart“ wird unter der Schaltfläche **Webpart hinzufügen**, auf die Sie in Schritt 3 geklickt haben, wie in der folgenden Abbildung dargestellt (Abbildung 1):

   ![Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   Abbildung 1. – Das Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server

1. Führen Sie auf der Seite „Seiten-Viewer“ die folgenden Aufgaben aus:

   1. Geben Sie im Dialogfeld „Link“ die URL von AEM Forms Workspace ein, wie etwa `https://[AEM_forms_Server]:8080/lc/ws`, wobei `[AEM_forms_Server]` die IP-Adresse oder den Namen des AEM-Formular-Servers darstellt.
   1. Klicken Sie auf **Erscheinungsbild** und ändern Sie Höhe, Breite und Titel, sodass Sie die gesamte Workspace-Benutzeroberfläche sehen können. Sie können beispielsweise Höhe und Breite auf 15 bzw. 28 cm festlegen.
   1. Klicken Sie auf **Link testen**. Es wird ein neues Webbrowser-Fenster mit Workspace angezeigt.
   1. (Optional) Klicken Sie auf **Layout** und ändern Sie das Layout von Workspace im Webpart.
   1. (Optional) Klicken Sie auf **Erweitert** und ändern Sie andere Einstellungen, z. B. die Beschreibung und ob Workspace im Webpart minimiert oder geschlossen werden kann.

      Klicken Sie auf **Übernehmen**.

1. Klicken Sie auf **Bearbeitungsmodus beenden** und vergewissern Sie sich, dass Sie auf Workspace zugreifen können.

Nachdem Sie die oben genannten Schritte ausgeführt haben, sieht Ihre SharePoint-Site ähnlich wie in der folgenden Abbildung (Abbildung 2) gezeigt aus:

![AEM Forms Workspace in Microsoft Office SharePoint Server integriert](assets/aem-forms-workspace.jpg)

Abbildung 2 – AEM Forms Workspace in Microsoft Office SharePoint Server integriert
