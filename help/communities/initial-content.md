---
title: Anfänglicher Sandbox-Inhalt
seo-title: Anfänglicher Sandbox-Inhalt
description: Inhalt erstellen
seo-description: Inhalt erstellen
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
translation-type: tm+mt
source-git-commit: 65e2b98cfd980f17302b4751127e25827decec22
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 6%

---


# Anfänglicher Sandbox-Inhalt {#initial-sandbox-content}

In diesem Abschnitt erstellen Sie die folgenden Seiten, die alle die [Seitenvorlage](initial-app.md#createthepagetemplate)verwenden:

* SCF Sandbox Site, die zur englischen Version der Hauptseite umleitet.

   * SCF Sandbox - Die Hauptseite für die englische Version der Site.

   * SCF Play - Untergeordnetes Element der Hauptseite, auf der abgespielt werden soll.

Obwohl dieses Lernprogramm keine [Sprachkopien](../../help/sites-administering/tc-prep.md)enthält, wurde es so konzipiert, dass die Stammeseite die Erkennung der bevorzugten Sprache für den Benutzer über die HTML-Kopfzeile implementieren und zur entsprechenden Hauptseite für die Sprache umleiten kann. Die Regel besteht darin, den aus zwei Buchstaben bestehenden Ländercode für den Knotennamen der Seite zu verwenden, z. B. &quot;en&quot;für Englisch, &quot;fr&quot;für Französisch usw.

## Erste Seiten erstellen {#create-first-pages}

Da es nun eine [Seitenvorlage](initial-app.md#createthepagetemplate)gibt, können wir die Stammseite der Website im Verzeichnis /content einrichten.

1. Die Standard-Benutzeroberfläche bietet derzeit Entwürfe zum Erstellen von Sites. Da dieses Lernprogramm eine einfache Site erstellt, ist die klassische Benutzeroberfläche nützlich.

   Um zur klassischen Benutzeroberfläche zu wechseln, wählen Sie &quot;Globale Navigation&quot;und halten Sie den Mauszeiger über die rechte Seite des Projektsymbols. Wählen Sie das Symbol *Zu klassischer Benutzeroberfläche* wechseln aus, das angezeigt wird:

   ![classic-ui](assets/classic-ui.png)

   Die Möglichkeit, zur klassischen Benutzeroberfläche zu wechseln, muss von einem Administrator [aktiviert werden](../../help/sites-administering/enable-classic-ui.md).

1. Wählen Sie auf der [klassischen Begrüßungsseite](http://localhost:4502/welcome.html)der Benutzeroberfläche die Option **[!UICONTROL Websites]**.

   ![classic-ui-website](assets/classic-ui-website.png)

   Alternativ können Sie die klassische Benutzeroberfläche für Websites direkt aufrufen, indem Sie zu [/siteadmin navigieren.](http://localhost:4502/siteadmin)

1. Wählen Sie im Explorer-Bereich **[!UICONTROL Websites]** und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**.

   In the **[!UICONTROL Create Page]** dialog, enter the following:

   * Titel: `SCF Sandbox Site`
   * Name: `an-scf-sandbox`
   * Wählen Sie **[!UICONTROL eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**

   ![classic-ui-create-page](assets/classic-ui-create-page.png)

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus `/Websites/SCF Sandbox Site`und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**:

   * Titel: `SCF Sandbox`
   * Name: `en`
   * Wählen Sie **[!UICONTROL eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus `/Websites/SCF Sandbox Site/SCF Sandbox`und klicken Sie auf **[!UICONTROL Neu]** > **[!UICONTROL Neue Seite]**

   * Titel: `SCF Play`
   * Name: `play`
   * Wählen Sie **[!UICONTROL eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**

1. So wird die Website jetzt in der Websites-Konsole angezeigt. Beachten Sie, dass untergeordnete Seiten des im Explorer-Bereich ausgewählten Elements im rechten Bereich angezeigt werden, wo sie verwaltet werden können.

   ![classic-ui-website-page](assets/classic-ui-website-page.png)

   Dies ist die Repository-Ansicht, die mit dem Website-Tool und der Vorlage erstellt wurde:

   ![classic-ui-repository-Ansicht](assets/classic-ui-repository-view.png)

## Hinzufügen des Entwurfspfads {#add-the-design-path}

Wenn ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` sie mithilfe des Abschnitts &quot;Entwürfe&quot;der Konsole &quot;Werkzeuge&quot;erstellt wurde, wird die Eigenschaft

* `cq:template="/libs/wcm/core/templates/designpage"`

definiert wurde, was die optionale Möglichkeit bietet, in einem Skript auf Designelemente zu verweisen, `currentDesign.getPath()`. Beispiel

* `% String favIcon = currentDesign.getPath() + "/favicon.ico"; %`


   * Name: `cq:designPath`
   * Typ: `String`
   * Wert: `/etc/designs/an-scf-sandbox`

* Klicken Sie auf das Grün `[+] Add`

Der Befund sollte wie folgt aussehen:

![classic-ui-repository-path](assets/classic-ui-repository-path.png)

* Klicken Sie auf **[!UICONTROL Alle speichern]**

Bei Problemen beim Speichern der Konfiguration müssen Sie sich erneut anmelden und konfigurieren.

>[!NOTE]
>
>Die Verwendung von `cq:designPath` ist optional und steht in keinem Zusammenhang mit der [Verwendung von clientlibs](develop-app.md#includeclientlibsintemplate), die im Wesentlichen erforderlich sind, da die SCF-Komponenten [clientlibs](client-customize.md#clientlibs-for-scf) zur Verwaltung ihrer JS und CSS verwenden.


