---
title: Anfänglicher Sandbox-Inhalt
description: Erfahren Sie, wie Sie mit der Seitenvorlage in der Sandbox eine Hauptseite für eine englische Version einer Website und eine untergeordnete Seite der Hauptseite erstellen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 068a0fff-ca48-4847-ba3f-d78416c97f6d
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 3%

---

# Anfänglicher Sandbox-Inhalt {#initial-sandbox-content}

In diesem Abschnitt erstellen Sie die folgenden Seiten, die alle die [Seitenvorlage“ ](initial-app.md#createthepagetemplate):

* SCF Sandbox-Site, die zur englischen Version der Hauptseite weiterleitet.

   * SCF Sandbox - Die Hauptseite für die englische Version der Website.

   * SCF Play - Untergeordnetes Element der Hauptseite, auf der gespielt werden soll.

Dieses Tutorial geht nicht auf [Sprachkopien“ ](../../help/sites-administering/tc-prep.md). Stattdessen wurde er so konzipiert, dass die Stammseite die Erkennung der bevorzugten Sprache für den Benutzer über den HTML-Header implementieren und zur entsprechenden Hauptseite für die Sprache umleiten kann. Die Konvention besagt, dass der aus zwei Buchstaben bestehende Länder-Code für den Knotennamen der Seite verwendet wird, z. B. „en“ für Englisch und „fr“ für Französisch.

## Erste Seiten erstellen {#create-first-pages}

Da es jetzt eine [Seitenvorlage“ ](initial-app.md#createthepagetemplate), können Sie die Stammseite der Website im Verzeichnis /content einrichten.

1. Die Standard-Benutzeroberfläche bietet derzeit Blueprints zum Erstellen von Sites. Da dieses Tutorial eine einfache Site erstellt, ist die klassische Benutzeroberfläche nützlich.

   Um zur klassischen Benutzeroberfläche zu wechseln, wählen Sie die globale Navigation aus und bewegen Sie den Mauszeiger über die rechte Seite des Symbols Projekte . Wählen Sie das *Zu klassischer Benutzeroberfläche wechseln* aus, das angezeigt wird:

   ![classic-ui](assets/classic-ui.png)

   Die Möglichkeit, zur klassischen Benutzeroberfläche zu wechseln, muss [von einem Administrator aktiviert](../../help/sites-administering/enable-classic-ui.md).

1. Wählen Sie auf der [Startseite der klassischen Benutzeroberfläche](http://localhost:4502/welcome.html) die Option **[!UICONTROL Websites]** aus.

   ![classic-ui-website](assets/classic-ui-website.png)

   Alternativ können Sie direkt auf die klassische Benutzeroberfläche für Websites zugreifen, indem Sie zu [/siteadmin navigieren.](http://localhost:4502/siteadmin)

1. Wählen Sie im Explorer-Fenster **[!UICONTROL Websites]** und wählen Sie dann in der Symbolleiste **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Geben **[!UICONTROL im Dialogfeld]** Seite erstellen“ Folgendes ein:

   * Titel: `SCF Sandbox Site`
   * Name: `an-scf-sandbox`
   * Wählen Sie **[!UICONTROL Eine SCF-Sandbox-Wiedergabevorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![classic-ui-create-page](assets/classic-ui-create-page.png)

1. Wählen Sie im Explorer-Fenster die von Ihnen erstellte Seite aus, `/Websites/SCF Sandbox Site` Sie und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**:

   * Titel: `SCF Sandbox`
   * Name: `en`
   * Wählen Sie **[!UICONTROL Eine SCF-Sandbox-Wiedergabevorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Wählen Sie im Explorer-Fenster die von Ihnen erstellte Seite aus, `/Websites/SCF Sandbox Site/SCF Sandbox` Sie und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**

   * Titel: `SCF Play`
   * Name: `play`
   * Wählen Sie **[!UICONTROL Eine SCF-Sandbox-Wiedergabevorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

1. So wird die Website jetzt in der Websites-Konsole angezeigt. Beachten Sie, dass untergeordnete Seiten des im Explorer-Fenster ausgewählten Elements im rechten Bereich angezeigt werden, in dem sie verwaltet werden können.

   ![classic-ui-website-page](assets/classic-ui-website-page.png)

   Dies ist die Repository-Ansicht dessen, was mit dem Website-Tool und der Vorlage erstellt wurde:

   ![classic-ui-repository-view](assets/classic-ui-repository-view.png)

## Hinzufügen des Designpfads {#add-the-design-path}

Als ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` mit dem Abschnitt „Designs“ der Tools-Konsole erstellt wurde, gilt für die Eigenschaft &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

wurde definiert, was die optionale Möglichkeit bietet, in einem Skript mithilfe von `currentDesign.getPath()` auf Design-Assets zu verweisen. Zum Beispiel

* `% String favIcon = currentDesign.getPath() + "/favicon.ico"; %`


   * Name: `cq:designPath`
   * Typ: `String`
   * Wert: `/etc/designs/an-scf-sandbox`

* Klicken Sie auf die grüne `[+] Add`

Das Repository sollte wie folgt aussehen:

![classic-ui-repository-path](assets/classic-ui-repository-path.png)

* Klicken Sie **[!UICONTROL Alle speichern]**

Wenn beim Speichern der Konfiguration Probleme auftreten, melden Sie sich erneut an und konfigurieren Sie erneut.

>[!NOTE]
>
>Die Verwendung von `cq:designPath` ist optional und steht in keinem Zusammenhang mit der [Verwendung von clientlibs](develop-app.md#includeclientlibsintemplate), die erforderlich sind, da die SCF-Komponenten [clientlibs](client-customize.md#clientlibs-for-scf) zur Verwaltung ihrer JS und CSS verwenden.
