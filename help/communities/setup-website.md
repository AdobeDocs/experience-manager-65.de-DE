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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Website-Struktur einrichten {#setup-website-structure}

Die folgenden Anweisungen beschreiben zum Einrichten Ihrer Website die Ordner, die an den folgenden Orten erstellt werden sollen:

* `/apps/an-scf-sandbox`
Hier befinden sich benutzerdefinierte Anwendungen und Vorlagen

* `/etc/designs/an-scf-sandbox`
Hier befinden sich herunterladbare Designelemente

* `/content/an-scf-sandbox`
Hier befinden sich die herunterladbaren Webseiten

Der Code in diesem Lernprogramm hängt davon ab, dass der Name des Hauptordners für Anwendung, Entwurf und Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website wählen, ersetzen Sie immer `an-scf-sandbox` den von Ihnen gewählten Namen.

>[!NOTE]
>
>Info zu Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbarem Inhalt bilden
>* Knotennamen können Leerzeichen enthalten, bei Verwendung in einem URI muss das Leerzeichen jedoch entweder als &#39;%20&#39; oder als &#39;+&#39; kodiert werden
>* Knotennamen können Bindestriche und Unterstriche enthalten, müssen jedoch kodiert werden, wenn sie als Paketname in einer Java-Datei referenziert werden. Sowohl Bindestriche als auch Unterstriche werden mit einem Unterstrich gefolgt von ihrem Unicode-Wert versehen:
   >
   >  
* Bindestrich wird &#39;_002d&#39;
>  * Unterstrich wird &#39;_005f&#39;


## Anwendungsverzeichnis einrichten (/apps) {#setup-the-application-directory-apps}

Der Ordner &quot;/apps&quot;im Repository enthält den Code mit implementiert das Verhalten und die Wiedergabe der Seiten, die vom Ordner &quot;/content&quot;bereitgestellt werden.

Der Ordner &quot;/apps&quot;ist geschützt und nicht öffentlich zugänglich, ebenso wie die Ordner &quot;/content&quot;und &quot;/etc/designs&quot;.

1. Create `/apps/an-scf-sandbox` folder.

   Verwenden von **[!UICONTROL CRXDE Lite]** im Explorer-Bereich

   1. Wählen Sie den `/apps` Ordner
   1. **[!UICONTROL Klicken Sie mit der rechten Maustaste auf]** Erstellen **[!UICONTROL ... oder ziehen Sie die]** Create... Menü
   1. **[!UICONTROL Wählen Sie Ordner]** erstellen... .
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen&quot;]**`an-scf-sandbox`
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL Komponenten]** .

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner
   1. Click **[!UICONTROL Create > Create Folder]**
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot; **[!UICONTROL Komponenten ein]**
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie **den Unterordner &quot;templates **&quot;.

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner
   1. Click **[!UICONTROL Create > Create Folder]**
   1. Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot; **[!UICONTROL Vorlagen ein]**
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Neu auswählen `/apps/an-scf-sandbox`
   1. Select **[!UICONTROL Save All]**
   Speichern Sie wie bei jedem Bearbeitungsprozess häufig. Wenn bei der Dateneingabe Probleme auftreten, kann dies entweder daran liegen, dass Ihr Anmeldevorgang abgelaufen ist oder Sie vorherige Änderungen speichern müssen.

1. Die Struktur im Explorer-Bereich von CRXDE Lite sollte nun etwa wie folgt aussehen:

   ![chlimage_1-44](assets/chlimage_1-44.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner &quot;/etc/designs&quot;enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Um das Designer-Tool in der klassischen Benutzeroberfläche zu verwenden, navigieren Sie zu [https://&lt;server>:/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite verwenden, um einen Knoten des Typs zu erstellen, `cq:Page`werden Zugriffssteuerung und Replikation nicht auf Standardeinstellungen für eine Seite eingestellt.

1. In the explorer pane, select the **[!UICONTROL Designs]** folder and then click **[!UICONTROL New > New Page]**.

   Geben Sie Folgendes ein:

   * Titel: **SCF-Sandbox**
   * Name: **an-scf-sandbox**
   * Vorlage **der Entwurfsseite auswählen**
   Klicken Sie auf **[!UICONTROL Erstellen]**

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Aktualisieren Sie den Explorer-Bereich, wenn der Ordner &quot;An SCF Sandbox&quot;nicht angezeigt wird.

1. Kehren Sie zu CRXDE Lite zurück (http:// localhost:4502/crx/de) und erweitern Sie /etc/designs, um den Knoten &quot;an-scf-sandbox&quot;anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarten Eigenschaften, Zugriffssteuerung und Replizierung anzeigen, um zu sehen, was mit der Designseitenvorlage definiert wurde.

   ![chlimage_1-46](assets/chlimage_1-46.png)

## Content Directory (/content) einrichten {#setup-the-content-directory-content}

Der Ordner &quot;/content&quot;im entsprechenden Ordner befindet sich dort, wo sich der Inhalt der Website befindet. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

*Nachdem* die [Seitenvorlage](initial-app.md#createthepagetemplate) als Teil der ursprünglichen Anwendung erstellt wurde, kann der anfängliche Seiteninhalt basierend auf der Vorlage erstellt werden... . [****](initial-app.md)