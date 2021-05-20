---
title: Einrichten der Website-Struktur
seo-title: Einrichten der Website-Struktur
description: Einrichten von Ordnern
seo-description: Einrichten von Ordnern
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
exl-id: 1f60a0d4-a272-45e8-9742-4b706be8502e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---

# Einrichten der Website-Struktur {#setup-website-structure}

Die folgenden Anweisungen beschreiben die Ordner, die an den folgenden Orten erstellt werden sollen, um Ihre Website einzurichten:

* `/apps/an-scf-sandbox`

   Hier befinden sich benutzerdefinierte Anwendungen und Vorlagen.

* `/etc/designs/an-scf-sandbox`

   Hier befinden sich herunterladbare Design-Elemente.

* `/content/an-scf-sandbox`

   Hier befinden sich die herunterladbaren Webseiten.

Der Code in diesem Tutorial setzt voraus, dass der Hauptordnername für Anwendung, Design und Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website wählen, ersetzen Sie `an-scf-sandbox` immer durch den von Ihnen ausgewählten Namen.

>[!NOTE]
>
>Über Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbaren Inhalten bilden.
>* Knotennamen können Leerzeichen enthalten. Bei Verwendung in einem URI muss das Leerzeichen jedoch entweder als &quot;%20&quot;oder &quot;+&quot;kodiert werden.
>* Knotennamen können Bindestriche und Unterstriche enthalten, müssen jedoch kodiert werden, wenn sie in einer Java-Datei als Paketname referenziert werden. Sowohl Bindestriche als auch Unterstriche sind mit einem Unterstrich gefolgt von ihrem Unicode-Wert maskiert:

   >
   >   
   * Bindestrich wird zu &quot;_002d&quot;
   >   * Unterstrich wird zu &#39;_005f&#39;


## Einrichten des Anwendungsverzeichnisses (/apps) {#setup-the-application-directory-apps}

Das Verzeichnis /apps im Repository enthält den Code mit implementiert das Verhalten und Rendering der Seiten, die aus dem Verzeichnis /content bereitgestellt werden.

Der Ordner /apps ist geschützt und nicht öffentlich zugänglich wie die Ordner /content und /etc/designs.

1. Erstellen Sie den Ordner `/apps/an-scf-sandbox` .

   Verwenden von **[!UICONTROL CRXDE Lite]** im Explorer-Bereich

   1. Wählen Sie den Ordner `/apps` aus.
   1. Klicken Sie mit der rechten Maustaste auf **[!UICONTROL Erstellen]**... oder ziehen Sie die **[!UICONTROL Erstellen...]** Menü.
   1. Wählen Sie **[!UICONTROL Ordner erstellen...]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** `an-scf-sandbox` ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL components]** .

   1. Wählen Sie den Ordner `/apps/an-scf-sandbox` aus.
   1. Klicken Sie auf **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** **[!UICONTROL Komponenten]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen Sie den Unterordner **[!UICONTROL templates]** .

   1. Wählen Sie den Ordner `/apps/an-scf-sandbox` aus.
   1. Klicken Sie auf **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** **[!UICONTROL Vorlagen]** ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Wählen Sie `/apps/an-scf-sandbox` erneut aus.
   1. Wählen Sie **[!UICONTROL Alle speichern]** aus.

   Speichern Sie wie bei jedem Bearbeitungsprozess häufig. Wenn Probleme bei der Dateneingabe auftreten, kann dies entweder daran liegen, dass Ihre Anmeldung abgelaufen ist, oder Sie müssen frühere Bearbeitungen speichern.

1. Die Struktur im Explorer-Bereich der CRXDE Lite sollte jetzt etwa so aussehen:

   ![crxde-template](assets/crxde-template.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner /etc/designs enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Um das Designer-Tool in der klassischen Benutzeroberfläche zu verwenden, navigieren Sie zu [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite zum Erstellen eines Knotens vom Typ `cq:Page` verwenden, werden die Einstellungen für die Zugriffssteuerung und Replikation nicht auf die Standardeinstellungen für eine Seite festgelegt.

1. Wählen Sie im Explorer-Bereich den Ordner **[!UICONTROL Designs]** aus und klicken Sie dann auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Geben Sie Folgendes ein:

   * Titel: **[!UICONTROL Eine SCF-Sandbox]**
   * Name: **[!UICONTROL an-scf-sandbox]**
   * Wählen Sie **[!UICONTROL Design Page Template]**

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![design-template](assets/design-template.png)

1. Aktualisieren Sie den Explorer-Bereich, wenn der Ordner &quot;An SCF Sandbox&quot;nicht angezeigt wird.

1. Kehren Sie zur CRXDE Lite zurück (http:// localhost:4502/crx/de) und erweitern Sie /etc/designs, um den Knoten &quot;an-scf-sandbox&quot;anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarte Eigenschaften , die Registerkarte Zugriffssteuerung und die Registerkarte Replikation anzeigen, um zu sehen, was mithilfe der Vorlage Design-Seite definiert wurde.

   ![crxde-configure-template](assets/crxde-configure-template.png)

## Einrichten des Inhaltsverzeichnisses (/content) {#setup-the-content-directory-content}

Das Verzeichnis /content im Repository befindet sich dort, wo sich der Website-Inhalt befindet. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

** Nachdem die  [Seitenvorlagen als Teil der ursprünglichen Anwendung erstellt ](initial-app.md#createthepagetemplate) wurden, kann der anfängliche Seiteninhalt anhand der Vorlage erstellt werden....  [**.**](initial-app.md)
