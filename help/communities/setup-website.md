---
title: Website-Struktur einrichten
seo-title: Website-Struktur einrichten
description: Einrichten von Ordnern
seo-description: Einrichten von Ordnern
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
translation-type: tm+mt
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---


# Website-Struktur einrichten {#setup-website-structure}

Die folgenden Anweisungen beschreiben zum Einrichten Ihrer Website die Ordner, die an den folgenden Orten erstellt werden sollen:

* `/apps/an-scf-sandbox`

   Hier befinden sich benutzerdefinierte Anwendungen und Vorlagen.

* `/etc/designs/an-scf-sandbox`

   This is where downloadable design elements reside.

* `/content/an-scf-sandbox`

   Hier befinden sich die herunterladbaren Webseiten.

The code in this tutorial will rely on the main folder name being the same for the application, design, and content. If you choose some other name for your website, then always replace `an-scf-sandbox` with the name you have chosen.

>[!NOTE]
>
>About names:
>
>* The names seen in CRXDE are node names which form the path to addressable content.
>* Node names may contain spaces, but when used in an URI, the space must be encoded either as &#39;%20&#39; or &#39;+&#39;.
>* Node names may contain hyphens and underscores, but they must be encoded when referenced as a package name within a Java file. Both hyphens and underscores are escaped with underscore followed by their unicode value:

   >
   >   
   * Bindestrich wird &#39;_002d&#39;
   >   * underscore becomes &#39;_005f&#39;


## Set up the Application Directory (/apps) {#setup-the-application-directory-apps}

The /apps directory in the repository contains the code with implements the behavior and rendering of the pages served from the /content directory.

The /apps directory is protected and not publicly accessible as are the /content and /etc/designs directories.

1. Create `/apps/an-scf-sandbox` folder.

   Using **[!UICONTROL CRXDE Lite]**, in the explorer pane

   1. Select the `/apps` folder.
   1. Right-click **[!UICONTROL Create]**... or pull down the **[!UICONTROL Create...]** menu.
   1. Wählen Sie Ordner **[!UICONTROL erstellen...]**.
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot;ein `an-scf-sandbox`.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL Komponenten]** .

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner aus.
   1. Click **[!UICONTROL Create > Create Folder]**.
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot;die **[!UICONTROL Komponenten]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie **[!UICONTROL den Unterordner &quot;templates]** &quot;.

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner aus.
   1. Click **[!UICONTROL Create > Create Folder]**.
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot; **[!UICONTROL Vorlagen]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Wählen Sie erneut `/apps/an-scf-sandbox`.
   1. Select **[!UICONTROL Save All]**.

   Speichern Sie wie bei jedem Bearbeitungsprozess häufig. Wenn bei der Dateneingabe Probleme auftreten, kann dies entweder daran liegen, dass Ihr Anmeldevorgang abgelaufen ist oder Sie vorherige Änderungen speichern müssen.

1. Die Struktur im Explorer-Bereich der CRXDE Lite sollte nun etwa wie folgt aussehen:

   ![crxde-template](assets/crxde-template.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner &quot;/etc/designs&quot;enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Um das Designer-Tool in der klassischen Benutzeroberfläche zu verwenden, navigieren Sie zu [https://&lt;server>:/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite verwenden, um einen Knoten des Typs zu erstellen, `cq:Page`werden Zugriffskontrolle und Replikation nicht auf Standardeinstellungen für eine Seite festgelegt.

1. In the explorer pane, select the **[!UICONTROL Designs]** folder and then click **[!UICONTROL New]** > **[!UICONTROL New Page]**.

   Geben Sie Folgendes ein:

   * Title: **[!UICONTROL An SCF Sandbox]**
   * Name: **[!UICONTROL an-scf-sandbox]**
   * Vorlage **[!UICONTROL der Entwurfsseite auswählen]**

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![design-template](assets/design-template.png)

1. Refresh the explorer pane if &quot;An SCF Sandbox&quot; folder does not appear.

1. Return to CRXDE Lite (http:// localhost:4502/crx/de) and expand /etc/designs to see the node named &quot;an-scf-sandbox&quot;.

   In the right, lower pane of CRXDE, you can view the Properties tab, Access Control tab and Replication tab to see what was defined using the Design Page Template.

   ![crxde-configure-template](assets/crxde-configure-template.png)

## Set up the Content Directory (/content) {#setup-the-content-directory-content}

The /content directory in the respository is where the website content resides. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

*After* the [page template](initial-app.md#createthepagetemplate) is created as part of the initial application, the initial page content can be created based on the template.... [**⇒**](initial-app.md)
