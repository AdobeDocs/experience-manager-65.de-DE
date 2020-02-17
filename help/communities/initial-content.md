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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Anfänglicher Sandbox-Inhalt {#initial-sandbox-content}

In diesem Abschnitt erstellen Sie die folgenden Seiten, die alle die [Seitenvorlage](initial-app.md#createthepagetemplate)verwenden:

* SCF Sandbox-Site, die zur englischen Version der Hauptseite umleitet

   * SCF Sandbox - Die Hauptseite für die englische Version der Site

      * SCF Play - Untergeordnetes Element der Hauptseite, auf der die Wiedergabe durchgeführt werden soll

Obwohl dieses Lernprogramm keine [Sprachkopien](../../help/sites-administering/tc-prep.md)enthält, wurde es so konzipiert, dass die Stammeseite die Erkennung der bevorzugten Sprache für den Benutzer über die HTML-Kopfzeile implementieren und zur entsprechenden Hauptseite für die Sprache umleiten kann. Die Regel besteht darin, den aus zwei Buchstaben bestehenden Ländercode für den Knotennamen der Seite zu verwenden, z. B. &quot;en&quot;für Englisch, &quot;fr&quot;für Französisch usw.

## Erste Seiten erstellen {#create-first-pages}

Da es nun eine [Seitenvorlage](initial-app.md#createthepagetemplate)gibt, können wir die Stammseite der Website im Verzeichnis /content einrichten.

1. Die Standard-Benutzeroberfläche bietet derzeit Entwürfe zum Erstellen von Sites. Da dieses Lernprogramm eine einfache Site erstellt, ist die klassische Benutzeroberfläche nützlich.

   Um zur klassischen Benutzeroberfläche zu wechseln, wählen Sie &quot;Globale Navigation&quot;und halten Sie den Mauszeiger über die rechte Seite des Projektsymbols. Wählen Sie das Symbol *Zu klassischer Benutzeroberfläche* wechseln aus, das angezeigt wird:

   ![chlimage_1-36](assets/chlimage_1-36.png)

   Die Möglichkeit, zur klassischen Benutzeroberfläche zu wechseln, muss von einem Administrator [aktiviert werden](../../help/sites-administering/enable-classic-ui.md).

1. Wählen Sie auf der [klassischen Begrüßungsseite](http://localhost:4502/welcome.html)der Benutzeroberfläche die Option **[!UICONTROL Websites]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Alternativ können Sie die klassische Benutzeroberfläche für Websites direkt aufrufen, indem Sie zu [/siteadmin navigieren.](http://localhost:4502/siteadmin)

1. Wählen Sie im Explorer-Bereich **[!UICONTROL Websites]** und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Neu > Neue Seite]**.

   In the **[!UICONTROL Create Page]** dialog, enter the following:

   * Titel: `SCF Sandbox Site`
   * Name: `an-scf-sandbox`
   * Wählen Sie **[!UICONTROL eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**
   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus `/Websites/SCF Sandbox Site`und klicken Sie auf **[!UICONTROL Neu > Neue Seite]**:

   * Titel: `SCF Sandbox`
   * Name: `en`
   * Wählen Sie **eine SCF-Sandbox-Abspielvorlage **
   * Klicken Sie auf **Erstellen **

1. Wählen Sie im Explorer-Bereich die soeben erstellte Seite aus `/Websites/SCF Sandbox Site/SCF Sandbox`und klicken Sie auf **[!UICONTROL Neu > Neue Seite]**

   * Titel: `SCF Play`
   * Name: `play`
   * Wählen Sie **[!UICONTROL eine SCF-Sandbox-Abspielvorlage]**
   * Klicken Sie auf **[!UICONTROL Erstellen]**

1. So wird die Website jetzt in der Websites-Konsole angezeigt. Beachten Sie, dass untergeordnete Seiten des im Explorer-Bereich ausgewählten Elements im rechten Bereich angezeigt werden, wo sie verwaltet werden können.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Dies ist die Repository-Ansicht, die mit dem Website-Tool und der Vorlage erstellt wurde:

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Entwurfspfad hinzufügen {#add-the-design-path}

Wenn ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` sie mithilfe des Abschnitts &quot;Entwürfe&quot;der Konsole &quot;Werkzeuge&quot;erstellt wurde, wird die Eigenschaft

* `cq:template="/libs/wcm/core/templates/designpage"`

definiert wurde, was die optionale Möglichkeit bietet, in einem Skript auf Designelemente zu verweisen, `currentDesign.getPath()`. Beispiel

* &lt;% String favIcon = currentDesign.getPath() + &quot;/favicon.ico&quot;; %>


   * Name: `cq:designPath`
   * Typ: `String`
   * Wert: `/etc/designs/an-scf-sandbox`

* Klicken Sie auf das Grün `[+] Add`

Der Befund sollte wie folgt aussehen:

![chlimage_1-41](assets/chlimage_1-41.png)

* Klicken Sie auf **[!UICONTROL Alle speichern]**

[ Probleme beim Sparen? Melden Sie sich erneut an! ]

>[!NOTE]
>
>Die Verwendung von cq:designPath ist optional und steht in keinem Zusammenhang mit der [Verwendung von clientlibs](develop-app.md#includeclientlibsintemplate), die im Wesentlichen erforderlich sind, da die SCF-Komponenten [clientlibs](client-customize.md#clientlibs-for-scf) zur Verwaltung ihrer JS und CSS verwenden.

