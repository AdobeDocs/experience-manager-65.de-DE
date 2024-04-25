---
title: Einrichten der Website-Struktur
description: Erfahren Sie, wie Sie Ihre Website-Struktur einschließlich der zu erstellenden Ordner einrichten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 1f60a0d4-a272-45e8-9742-4b706be8502e
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '555'
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

Der Code in diesem Tutorial basiert darauf, dass der Hauptordnername für Anwendung, Design und Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website wählen, ersetzen Sie immer `an-scf-sandbox` mit dem Namen, den Sie gewählt haben.

>[!NOTE]
>
>Über Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbaren Inhalten bilden.
>* Knotennamen können Leerzeichen enthalten. Bei Verwendung in einem URI muss das Leerzeichen jedoch entweder als &quot;%20&quot;oder &quot;+&quot;kodiert werden.
>* Knotennamen können Bindestriche und Unterstriche enthalten, müssen jedoch kodiert werden, wenn sie in einer Java™-Datei als Paketname referenziert werden. Sowohl Bindestriche als auch Unterstriche sind mit einem Unterstrich gefolgt von ihrem Unicode-Wert maskiert:
>
>   * Bindestrich wird zu &quot;_002d&quot;
>   * Unterstrich wird zu &#39;_005f&#39;

## Einrichten des Anwendungsverzeichnisses (/apps) {#setup-the-application-directory-apps}

Das Verzeichnis /apps im Repository enthält den Code mit implementiert das Verhalten und Rendering der Seiten, die aus dem Verzeichnis /content bereitgestellt werden.

Der Ordner /apps ist geschützt und nicht öffentlich zugänglich wie die Ordner /content und /etc/designs.

1. Erstellen `/apps/an-scf-sandbox` Ordner.

   Verwenden **[!UICONTROL CRXDE Lite]** im Explorer-Bereich

   1. Wählen Sie die `/apps` Ordner.
   1. Rechtsklick **[!UICONTROL Erstellen]**... oder ziehen Sie die **[!UICONTROL Erstellen...]** Menü.
   1. Auswählen **[!UICONTROL Ordner erstellen...]**.
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter `an-scf-sandbox`.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen **[!UICONTROL Komponenten]** Unterordner.

   1. Wählen Sie die `/apps/an-scf-sandbox` Ordner.
   1. Klicks **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter **[!UICONTROL Komponenten]**.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen **[!UICONTROL templates]** Unterordner.

   1. Wählen Sie die `/apps/an-scf-sandbox` Ordner.
   1. Klicks **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter **[!UICONTROL templates]**.
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Neu auswählen `/apps/an-scf-sandbox`.
   1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   Wie bei allen Bearbeitungsprozessen sollten Sie häufig speichern. Wenn Probleme bei der Dateneingabe auftreten, kann dies entweder daran liegen, dass Ihre Anmeldung abgelaufen ist, oder Sie müssen frühere Bearbeitungen speichern.

1. Die Struktur im Explorer-Bereich von CRXDE Lite sollte jetzt etwa so aussehen:

   ![crxde-template](assets/crxde-template.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner /etc/designs enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Navigieren Sie zur Verwendung des Designer-Tools in der klassischen Benutzeroberfläche zu [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite verwenden, um einen Knoten vom Typ `cq:Page`festgelegt ist, würden die Zugriffssteuerung und Replikation nicht auf Standardeinstellungen für eine Seite festgelegt.

1. Wählen Sie im Explorer-Bereich die **[!UICONTROL Designs]** Ordner und klicken Sie dann auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Geben Sie ein:

   * Titel: **[!UICONTROL Eine SCF-Sandbox]**
   * Name: **[!UICONTROL an-scf-sandbox]**
   * Auswählen **[!UICONTROL Design Page Template]**

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![design-template](assets/design-template.png)

1. Aktualisieren Sie den Explorer-Bereich, wenn der Ordner &quot;An SCF Sandbox&quot;nicht angezeigt wird.

1. Kehren Sie zu CRXDE Lite zurück (http:// localhost:4502/crx/de) und erweitern Sie /etc/designs, um den Knoten &quot;an-scf-sandbox&quot;anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarte Eigenschaften, die Registerkarte Zugriffssteuerung und die Registerkarte Replikation anzeigen, um zu sehen, was mit der Vorlage Design-Seite definiert wurde.

   ![crxde-configure-template](assets/crxde-configure-template.png)

## Content Directory (/content) einrichten {#setup-the-content-directory-content}

Das Verzeichnis /content im Repository befindet sich dort, wo sich der Website-Inhalt befindet. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

*Nachher* die [Seitenvorlage](initial-app.md#createthepagetemplate) als Teil der ursprünglichen Anwendung erstellt wurde, kann der anfängliche Seiteninhalt basierend auf der Vorlage erstellt werden... [**imetrisch**](initial-app.md)
