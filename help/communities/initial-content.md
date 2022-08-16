---
title: Anfänglicher Sandbox-Inhalt
seo-title: Initial Sandbox Content
description: Inhalt erstellen
seo-description: Create content
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
exl-id: 068a0fff-ca48-4847-ba3f-d78416c97f6d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 5%

---

# Anfänglicher Sandbox-Inhalt {#initial-sandbox-content}

In diesem Abschnitt erstellen Sie die folgenden Seiten, die alle die [Seitenvorlage](initial-app.md#createthepagetemplate):

* SCF-Sandbox-Site, die zur englischen Version der Hauptseite umleitet.

   * SCF Sandbox - Die Hauptseite für die englische Version der Site.

   * SCF Play - Untergeordnetes Element der Hauptseite, auf der abgespielt werden soll.

Auch wenn dieses Tutorial sich nicht mit [Sprachkopien](../../help/sites-administering/tc-prep.md), so entworfen, dass die Stammseite die Erkennung der bevorzugten Sprache für den Benutzer über die HTML-Kopfzeile implementieren und zur entsprechenden Hauptseite für die weiterleiten kann. Die Konvention besteht darin, den aus zwei Buchstaben bestehenden Ländercode für den Knotennamen der Seite zu verwenden, z. B. &quot;en&quot;für Englisch, &quot;fr&quot;für Französisch usw.

## Erste Seiten erstellen {#create-first-pages}

Jetzt gibt es eine [Seitenvorlage](initial-app.md#createthepagetemplate), können wir die Stammseite der Website im Verzeichnis /content einrichten.

1. Die Standard-Benutzeroberfläche bietet derzeit Blueprints zum Erstellen von Sites. Da in diesem Tutorial eine einfache Site erstellt wird, ist die klassische Benutzeroberfläche nützlich.

   Um zur klassischen Benutzeroberfläche zu wechseln, wählen Sie die globale Navigation aus und bewegen Sie den Mauszeiger über die rechte Seite des Projektsymbols. Wählen Sie die *Zur klassischen Benutzeroberfläche wechseln* -Symbol, das angezeigt wird:

   ![classic-ui](assets/classic-ui.png)

   Die Möglichkeit, zur klassischen Benutzeroberfläche zu wechseln, muss [von einem Administrator aktiviert](../../help/sites-administering/enable-classic-ui.md).

1. Aus dem [Startseite der klassischen Benutzeroberfläche](http://localhost:4502/welcome.html)auswählen **[!UICONTROL Websites]**.

   ![classic-ui-website](assets/classic-ui-website.png)

   Sie können auch direkt auf die klassische Benutzeroberfläche für Websites zugreifen, indem Sie zu [/siteadmin.](http://localhost:4502/siteadmin)

1. Wählen Sie im Explorer-Bereich **[!UICONTROL Websites]** und wählen Sie dann in der Symbolleiste **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   Im **[!UICONTROL Seite erstellen]** Geben Sie Folgendes ein:

   * Titel: `SCF Sandbox Site`
   * Name: `an-scf-sandbox`
   * Auswählen **[!UICONTROL Eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![classic-ui-create-page](assets/classic-ui-create-page.png)

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus. `/Websites/SCF Sandbox Site`und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**:

   * Titel: `SCF Sandbox`
   * Name: `en`
   * Auswählen **[!UICONTROL Eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus. `/Websites/SCF Sandbox Site/SCF Sandbox`und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**

   * Titel: `SCF Play`
   * Name: `play`
   * Auswählen **[!UICONTROL Eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**.

1. So wird die Website jetzt in der Websites-Konsole angezeigt. Beachten Sie, dass untergeordnete Seiten des im Explorer-Bereich ausgewählten Elements im rechten Bereich angezeigt werden, wo sie verwaltet werden können.

   ![classic-ui-website-page](assets/classic-ui-website-page.png)

   Dies ist die Repository-Ansicht, die mit dem Website-Tool und der Vorlage erstellt wurde:

   ![classic-ui-repository-view](assets/classic-ui-repository-view.png)

## Hinzufügen des Designpfads {#add-the-design-path}

Wann ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` wurde mit dem Abschnitt &quot;Designs&quot;der Tools-Konsole erstellt, die Eigenschaft &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

definiert wurde, was die optionale Möglichkeit bietet, Design-Assets in einem Skript mit `currentDesign.getPath()`. Beispiel

* `% String favIcon = currentDesign.getPath() + "/favicon.ico"; %`


   * Name: `cq:designPath`
   * Typ: `String`
   * Wert: `/etc/designs/an-scf-sandbox`

* Klicken Sie auf Grün `[+] Add`

Das Repository sollte wie folgt aussehen:

![classic-ui-repository-path](assets/classic-ui-repository-path.png)

* Klicken Sie auf **[!UICONTROL Alle speichern]**

Falls Probleme beim Speichern der Konfiguration auftreten, melden Sie sich erneut an und konfigurieren Sie sie erneut.

>[!NOTE]
>
>Die Verwendung von `cq:designPath` ist optional und nicht mit dem [Verwendung von clientlibs](develop-app.md#includeclientlibsintemplate), die im Wesentlichen erforderlich sind, da die SCF-Komponenten [clientlibs](client-customize.md#clientlibs-for-scf) um ihre JS und CSS zu verwalten.
