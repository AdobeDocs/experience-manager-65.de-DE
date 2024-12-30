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

Zum Einrichten Ihrer Website werden in den folgenden Anweisungen die Ordner beschrieben, die an den folgenden Speicherorten erstellt werden müssen:

* `/apps/an-scf-sandbox`

  Hier befinden sich benutzerdefinierte Programme und Vorlagen.

* `/etc/designs/an-scf-sandbox`

  Hier befinden sich herunterladbare Design-Elemente.

* `/content/an-scf-sandbox`

  Hier befinden sich die herunterladbaren Web-Seiten.

Der Code in diesem Tutorial beruht darauf, dass der Name des Hauptordners für die Anwendung, das Design und den Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website auswählen, ersetzen Sie `an-scf-sandbox` immer durch den ausgewählten Namen.

>[!NOTE]
>
>Über Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbaren Inhalten bilden.
>* Knotennamen können Leerzeichen enthalten, aber bei Verwendung in einem URI muss der Leerzeichen entweder als &quot;%20“ oder &quot;+&quot; kodiert werden.
>* Knotennamen können Bindestriche und Unterstriche enthalten, sie müssen jedoch kodiert werden, wenn sie als Paketname in einer Java™-Datei referenziert werden. Sowohl Bindestriche als auch Unterstriche werden durch einen Unterstrich gefolgt von ihrem Unicode-Wert maskiert:
>
>   * Bindestrich wird zu &#39;_002d&#39;
>   * Unterstrich wird zu &#39;_005f&#39;

## Einrichten des Anwendungsverzeichnisses (/apps) {#setup-the-application-directory-apps}

Der Ordner &quot;/apps“ im Repository enthält den Code mit , der das Verhalten und Rendering der Seiten implementiert, die vom Ordner &quot;/content“ bereitgestellt werden.

Der Ordner &quot;/apps“ ist geschützt und nicht öffentlich zugänglich. Gleiches gilt für die Ordner &quot;/content“ und &quot;/etc/designs“.

1. Erstellen Sie `/apps/an-scf-sandbox` Ordner.

   Verwenden von **[!UICONTROL CRXDE Lite]** im Explorer-Fenster

   1. Wählen Sie den `/apps` Ordner aus.
   1. Klicken Sie mit **[!UICONTROL rechten Maustaste auf]** Erstellen…“ oder ziehen Sie das Menü **[!UICONTROL Erstellen…]** nach unten.
   1. Wählen Sie **[!UICONTROL Ordner erstellen…]**.
   1. Geben **[!UICONTROL im Dialogfeld „Ordner]**&quot; `an-scf-sandbox` ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen **[!UICONTROL Unterordners]** components“.

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner aus.
   1. Klicken Sie **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im **[!UICONTROL Ordner erstellen]** &quot;**[!UICONTROL &quot;]**.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Erstellen **[!UICONTROL Unterordners]** templates“.

   1. Wählen Sie den `/apps/an-scf-sandbox` Ordner aus.
   1. Klicken Sie **[!UICONTROL Erstellen > Ordner erstellen]**.
   1. Geben Sie im **[!UICONTROL Ordner erstellen]** &quot;**[!UICONTROL &quot;]**.
   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. `/apps/an-scf-sandbox` erneut auswählen.
   1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   Wie bei jedem Bearbeitungsprozess sollten Sie häufig speichern. Wenn bei der Dateneingabe Probleme auftreten, kann dies entweder auf eine Zeitüberschreitung bei der Anmeldung zurückzuführen sein oder Sie müssen frühere Änderungen speichern.

1. Die Struktur im Explorer-Fenster von CRXDE Lite sollte nun ungefähr so aussehen:

   ![CRXDE-template](assets/crxde-template.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner /etc/designs enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Navigieren Sie zur Verwendung des Designer-Tools in der klassischen Benutzeroberfläche zu [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite zum Erstellen eines Knotens vom Typ `cq:Page` verwenden, sind Zugriffssteuerung und Replikation für eine Seite nicht auf die Standardeinstellungen festgelegt.

1. Wählen Sie im Explorer-Fenster den Ordner **[!UICONTROL Designs]** aus und klicken Sie dann auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Geben Sie ein:

   * Titel: **[!UICONTROL Eine SCF-Sandbox]**
   * Name: **[!UICONTROL an-scf-sandbox]**
   * Wählen Sie **[!UICONTROL Design-Seitenvorlage]** aus

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![design-template](assets/design-template.png)

1. Aktualisieren Sie das Explorer-Fenster, wenn kein „SCF Sandbox“-Ordner angezeigt wird.

1. Kehren Sie zu CRXDE Lite (http:// localhost:4502/crx/de) zurück und erweitern Sie &quot;/etc/designs“, um den Knoten „an-scf-sandbox“ anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarte Eigenschaften , die Registerkarte Zugriffssteuerung und die Registerkarte Replikation anzeigen, um zu sehen, was mithilfe der Design-Seitenvorlage definiert wurde.

   ![crxde-configure-template](assets/crxde-configure-template.png)

## Einrichten des Inhaltsverzeichnisses (/content) {#setup-the-content-directory-content}

Der Ordner /content im Repository befindet sich dort, wo sich der Website-Inhalt befindet. Die Pfade unter /content enthalten die Pfade der URL für Browser-Anfragen.

*Nachdem* [Seitenvorlage](initial-app.md#createthepagetemplate) als Teil des ersten Programms erstellt wurde, kann der anfängliche Seiteninhalt basierend auf der Vorlage erstellt werden…. [**⇒**](initial-app.md)
