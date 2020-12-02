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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---


# Einrichten der Website-Struktur {#setup-website-structure}

Die folgenden Anweisungen beschreiben zum Einrichten Ihrer Website die Ordner, die an den folgenden Orten erstellt werden sollen:

* `/apps/an-scf-sandbox`

   Hier befinden sich benutzerdefinierte Anwendungen und Vorlagen.

* `/etc/designs/an-scf-sandbox`

   Hier befinden sich herunterladbare Designelemente.

* `/content/an-scf-sandbox`

   Hier befinden sich die herunterladbaren Webseiten.

Der Code in diesem Lernprogramm hängt davon ab, dass der Name des Hauptordners für die Anwendung, den Entwurf und den Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website wählen, ersetzen Sie `an-scf-sandbox` immer durch den Namen, den Sie gewählt haben.

>[!NOTE]
>
>Info zu Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbaren Inhalten bilden.
>* Knotennamen können Leerzeichen enthalten, bei Verwendung in einem URI muss das Leerzeichen jedoch entweder als &quot;%20&quot;oder &quot;+&quot;kodiert werden.
>* Knotennamen können Bindestriche und Unterstriche enthalten, müssen jedoch kodiert werden, wenn sie als Paketname in einer Java-Datei referenziert werden. Sowohl Bindestriche als auch Unterstriche werden mit einem Unterstrich gefolgt von ihrem Unicode-Wert versehen:

   >
   >   
   * Bindestrich wird &#39;_002d&#39;
   >   * Unterstrich wird &#39;_005f&#39;


## Einrichten des Anwendungsverzeichnisses (/apps) {#setup-the-application-directory-apps}

Der Ordner &quot;/apps&quot;im Repository enthält den Code mit implementiert das Verhalten und die Wiedergabe der Seiten, die vom Ordner &quot;/content&quot;bereitgestellt werden.

Der Ordner &quot;/apps&quot;ist geschützt und nicht öffentlich zugänglich, ebenso wie die Ordner &quot;/content&quot;und &quot;/etc/designs&quot;.

1. Erstellen Sie den Ordner `/apps/an-scf-sandbox`.

   Verwenden von **[!UICONTROL CRXDE Lite]** im Explorer-Bereich

   1. Wählen Sie den Ordner `/apps` aus.
   1. Klicken Sie mit der rechten Maustaste auf **[!UICONTROL Erstellen]**... oder ziehen Sie **[!UICONTROL Erstellen...]**-Menü.
   1. Wählen Sie **[!UICONTROL Ordner erstellen...]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** `an-scf-sandbox` ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL Komponenten]**.

   1. Wählen Sie den Ordner `/apps/an-scf-sandbox` aus.
   1. Klicken Sie auf **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** **[!UICONTROL Komponenten]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL templates]**.

   1. Wählen Sie den Ordner `/apps/an-scf-sandbox` aus.
   1. Klicken Sie auf **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** **[!UICONTROL Vorlagen]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Wählen Sie `/apps/an-scf-sandbox` erneut aus.
   1. Wählen Sie **[!UICONTROL Alle speichern]**.

   Speichern Sie wie bei jedem Bearbeitungsprozess häufig. Wenn bei der Dateneingabe Probleme auftreten, kann dies entweder daran liegen, dass Ihr Anmeldevorgang abgelaufen ist oder Sie vorherige Änderungen speichern müssen.

1. Die Struktur im Explorer-Bereich der CRXDE Lite sollte nun etwa wie folgt aussehen:

   ![crxde-template](assets/crxde-template.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner &quot;/etc/designs&quot;enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Um das Designer-Tool in der klassischen Benutzeroberfläche zu verwenden, navigieren Sie zu [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite verwenden, um einen Knoten des Typs `cq:Page` zu erstellen, werden Zugriffskontrolle und Replikation nicht auf Standardeinstellungen für eine Seite eingestellt.

1. Wählen Sie im Explorer-Bereich den Ordner **[!UICONTROL Entwürfe]** und klicken Sie dann auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Geben Sie Folgendes ein:

   * Titel: **[!UICONTROL Eine SCF-Sandbox]**
   * Name: **[!UICONTROL an-scf-sandbox]**
   * Wählen Sie **[!UICONTROL Designseitenvorlage]**

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![design-template](assets/design-template.png)

1. Aktualisieren Sie den Explorer-Bereich, wenn der Ordner &quot;An SCF Sandbox&quot;nicht angezeigt wird.

1. Kehren Sie zur CRXDE Lite zurück (http:// localhost:4502/crx/de) und erweitern Sie &quot;/etc/designs&quot;, um den Knoten &quot;an-scf-sandbox&quot; anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarte Eigenschaften, die Registerkarte Zugriffskontrolle und die Registerkarte Replikation Ansicht haben, um zu sehen, was mit der Designseitenvorlage definiert wurde.

   ![crxde-configure-template](assets/crxde-configure-template.png)

## Content Directory (/content) {#setup-the-content-directory-content} einrichten

Der Ordner &quot;/content&quot;im entsprechenden Ordner befindet sich dort, wo sich der Inhalt der Website befindet. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

*Nachdem* die  [Seitenvorlage als Teil der ursprünglichen Anwendung ](initial-app.md#createthepagetemplate) erstellt wurde, kann der ursprüngliche Seiteninhalt auf der Grundlage der Vorlage erstellt werden....  [**δ**](initial-app.md)
