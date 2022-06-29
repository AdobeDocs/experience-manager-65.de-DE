---
title: Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server
seo-title: Integrating AEM forms workspace with Microsoft Office SharePoint Server
description: 'Sie können AEM Forms Workspace in Microsoft Office SharePoint Server integrieren. '
seo-description: You can integrate AEM forms workspace with Microsoft Office SharePoint Server.
uuid: 69d51bdf-729f-4eea-8fae-1e2b8aacaae6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 8990b422-f4f6-4080-871a-33cdf7ca6455
docset: aem65
exl-id: d080932f-d5fb-482d-9329-62da5df10362
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '542'
ht-degree: 100%

---

# Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server{#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Voraussetzungen**

**Vorausgesetztes Wissen** 
Bevor Sie AEM Forms Workspace zu SharePoint Server hinzufügen können, benötigen Sie Zugriff auf SharePoint Server mit den entsprechenden Berechtigungen. Außerdem müssen Sie die URL für den Zugriff auf Workspace kennen. In den folgenden Schritten wird davon ausgegangen, dass Sie mit SharePoint Server vertraut sind. Weitere Informationen zu Webparts in SharePoint Server Webparte finden Sie unter „Webparts in Windows SharePoint-Diensten“.

**Benutzerebene** Erste Schritte

Sie können AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server (z. B. Microsoft Office SharePoint Server 2007) verwenden. Benutzer können auf AEM Forms Workspace zugreifen, indem sie mithilfe eines Webbrowsers eine Verbindung zu Ihrem SharePoint Server herstellen und so eine einheitliche Plattform erhalten. In diesem Artikel lernen Sie die grundlegenden Schritte, um AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server anzuzeigen. Sie können die Schritte ausführen, die in diesem Artikel beschrieben werden, um eine einheitliche Plattform zu bieten, damit Benutzer, die eine Verbindung mit dem SharePoint Server herstellen, auf AEM Forms Workspace vom gleichen Port aus zugreifen können.

>[!NOTE]
>
>Die Schritte, die in diesem Artikel aufgeführt sind, gelten für Microsoft SharePoint Server 2007. Sie können auch HTML Workspace mit anderen unterstützten Versionen von Microsoft SharePoint konfigurieren.

## Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Gehen Sie zur Integration von AEM Forms Workspace in einen Webpart wie folgt vor:

1. Navigieren Sie in einem Webbrowser zur SharePoint-Website, wie etwa `https://[myMOSSserver]:44299/default.aspx`, wobei `[myMOSSserver]` für den Namen oder die IP-Adresse von Sharepoint Server steht.

   >[!NOTE]
   >
   >44299 ist die Standardportnummer für den SharePoint Server. Die Portnummer hängt von Ihrer Installation des SharePoint Server ab.

1. Klicken Sie in der rechten oberen Ecke der Webseite auf **Site-Aktionen** und wählen Sie **Seite bearbeiten**.
1. Klicken Sie auf die Schaltfläche **Webpart hinzufügen.**
1. Wählen Sie im Webseitendialogfeld „Webparts hinzufügen“ unter „Sonstiges“ **Seiten-Viewer-Webpart** hinzu und klicken Sie dann auf **Hinzufügen**.
1. Im Feld „Seiten-Viewer-Webpart“ klicken Sie auf **Bearbeiten** und wählen Sie **Freigegebenen Webpart ändern**.

   >[!NOTE]
   >
   >Das Feld „Seiten-Viewer-Webpart“ wird unter der Schaltfläche **Webpart hinzufügen** angezeigt, auf die Sie in Schritt 3 geklickt haben, wie in der folgenden Abbildung gezeigt (Abbildung 1):

   ![Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   Abbildung 1. – Das Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server.

1. Führen Sie auf der Seite „Seiten-Viewer“ folgende Aufgaben durch:

   1. Geben Sie im Dialogfeld „Link“ die URL von AEM Forms Workspace ein, wie etwa `https://[AEM_forms_Server]:8080/lc/ws`, wobei `[AEM_forms_Server]` die IP-Adresse oder den Namen des AEM Forms-Servers darstellt.
   1. Klicken Sie auf **Erscheinungsbild** und ändern Sie die Höhe, die Breite und den Titel, damit Sie die gesamte Workspace-Benutzeroberfläche sehen können. Beispielsweise können Sie die Breite und Höhe auf 15 cm bzw. 28 cm festlegen.
   1. Klicken Sie auf **Link testen**. Ein neues Webbrowserfenster mit Workspace wird angezeigt.
   1. (Optional) Klicken Sie auf **Layout** und ändern Sie das Layout von Workspace im Webpart.
   1. (Optional) Klicken Sie auf **Erweitert** und ändern Sie andere Einstellungen wie die Beschreibung und ob Workspace im Webpart minimiert werden oder geschlossen werden kann.

      Klicken Sie auf **Übernehmen**.

1. Klicken Sie auf **Bearbeitungsmodus beenden** und vergewissern Sie sich, dass Sie auf Workspace zugreifen können.

Nachdem Sie die oben beschriebenen Schritte durchgeführt haben, sieht Ihre SharePoint-Site ähnlich wie in der folgenden Abbildung gezeigt aus (Abbildung 2):

![AEM Forms Workspace in Microsoft Office SharePoint Server integriert](assets/aem-forms-workspace.jpg)

Abbildung 2 – AEM Forms Workspace in Microsoft Office SharePoint Server integriert
