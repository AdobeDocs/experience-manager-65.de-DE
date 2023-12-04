---
title: Einrichten einer Kampagne
description: Für das Einrichten einer neuen Kampagne ist es erforderlich, eine Marke für Ihre Kampagnen zu erstellen, eine Kampagne für Erlebnisse zu erstellen und schließlich die Eigenschaften für Ihre neue Kampagne zu definieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 1b607a52-f065-4e35-8215-d54df7c8403d
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '2194'
ht-degree: 34%

---

# Einrichten einer Kampagne{#setting-up-your-campaign}

Das Einrichten einer neuen Kampagne umfasst die folgenden (allgemeinen) Schritte:

1. [Marke erstellen](#creating-a-new-brand) , um Ihre Kampagnen zu speichern.
1. Bei Bedarf können Sie [Eigenschaften für Ihre neue Marke definieren](#defining-the-properties-for-your-new-brand).
1. [Kampagne erstellen](#creating-a-new-campaign) zum Speichern von Erlebnissen, z. B. Teaser-Seiten oder einen Newsletter.
1. Bei Bedarf können Sie [Eigenschaften für Ihre neue Kampagne definieren](#defining-the-properties-for-your-new-campaign).

Je nach Erlebnistyp müssen Sie dann [Erlebnis erstellen](#creating-a-new-experience). Die Details des Erlebnisses und die Aktionen, die auf seine Erstellung folgen, hängen vom Erlebnistyp ab, den Sie erstellen möchten:

* Beim Erstellen eines Teasers:

   1. [Teaser-Erlebnis erstellen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingateaserexperience).
   1. [Inhalt zu Ihrem Teaser hinzufügen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttoyourteaser).
   1. [Touchpoint für Ihren Teaser erstellen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatouchpointforyourteaser) (Fügen Sie Ihren Teaser zu einer Inhaltsseite hinzu).

* Wenn Sie einen Newsletter erstellen:

   1. [Erstellen eines Newsletter-Erlebnisses](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatinganewsletterexperience).
   1. [Fügen Sie dem Newsletter Inhalt hinzu.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttonewsletters)
   1. [Personalisieren Sie den Newsletter.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#personalizingnewsletters)
   1. [Erstellen einer attraktiven Landingpage für Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupanewsletterlandingpage).
   1. [Newsletter senden](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#sendingnewsletters) Abonnenten oder Leads.

* Beim Erstellen eines Adobe Target-Angebots (ehemals Test&amp;Target):

   1. [Erstellen eines Adobe Target-Angebots](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatesttargetofferexperience).
   1. [Integrieren mit Adobe Target](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#integratewithadobetesttarget)

>[!NOTE]
>
>Siehe [Segmentierung](/help/sites-administering/campaign-segmentation.md) für detaillierte Anweisungen zur Definition Ihrer Segmente.

## Erstellen einer neuen Marke {#creating-a-new-brand}

1. Öffnen Sie die **MCM** und wählen **Kampagnen** im linken Bereich.

1. Auswählen **Neu...** , um **Titel** und **Name** und der Vorlage für Ihre neue Marke:

   ![chlimage_1-17](assets/chlimage_1-17.png)

1. Klicken Sie auf **Erstellen**. Ihre neue Marke wird im MCM angezeigt (mit einem Standardsymbol).

### Definieren der Eigenschaften für Ihre neue Marke {#defining-the-properties-for-your-new-brand}

1. Von **Kampagnen** Wählen Sie im linken Bereich das Symbol Ihrer neuen Marke im rechten Bereich aus und klicken Sie auf **Eigenschaften...**

   Sie können eine **Titel**, **Beschreibung** und ein Bild, das als Symbol verwendet werden soll.

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Klicken Sie zum Speichern auf **OK**.

### Erstellen einer neuen Kampagne {#creating-a-new-campaign}

1. Von **Kampagnen** wählen Sie Ihre neue Marke im linken Bereich aus oder doppelklicken Sie auf das Symbol im rechten Bereich.

   Die Übersicht wird angezeigt (bei einer neuen Marke leer).

1. Klicks **Neu...** und geben Sie die **Titel**, **Name** und der Vorlage, die für Ihre neue Kampagne verwendet werden soll.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Klicken Sie auf **Erstellen**. Ihre neue Kampagne wird im MCM angezeigt.

### Definieren der Eigenschaften für Ihre neue Kampagne {#defining-the-properties-for-your-new-campaign}

Konfigurieren Sie Kampagneneigenschaften, die das Verhalten steuern:

* **Priorität:** Die Priorität dieser Kampagne im Vergleich zu anderen Kampagnen. Sind mehrere Kampagnen gleichzeitig aktiv, wird das Besuchererlebnis über diejenige Kampagne mit der höchsten Priorität gesteuert.
* **Ein- und Ausschaltzeit:** Diese Eigenschaften steuern den Zeitraum, in dem die Kampagne das Besuchererlebnis steuert. Die Eigenschaft &quot;Einschaltzeit&quot;steuert den Zeitpunkt, zu dem die Kampagne beginnt, das Erlebnis zu steuern. Die Eigenschaft &quot;Ausschaltzeit&quot;steuert, wann die Kampagnen die Steuerung des Erlebnisses beenden.
* **Bild:** Das Bild, das die Kampagne in AEM darstellt.
* **Cloud Service:** Die Kampagnenkonfigurationen für Cloud Service. (Siehe [Integration mit Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md).

* **Adobe Target:** Eigenschaften zum Konfigurieren von Kampagnen, die in Adobe Target integriert sind. (Siehe [Integration mit Adobe Target](/help/sites-administering/target.md).

1. Von **Kampagnen** auswählen. Aktivieren Sie im rechten Bereich Ihre Kampagne und klicken Sie auf **Eigenschaften**.

   Sie können verschiedene Eigenschaften eingeben, darunter **Titel**, **Beschreibung** und sämtliche gewünschten **Cloud-Services**.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Klicken Sie zum Speichern auf **OK**.

### Erstellen eines neuen Erlebnisses {#creating-a-new-experience}

Die Vorgehensweise zum Erstellen eines Erlebnisses hängt vom Erlebnistyp ab:

* [Erstellen eines Teasers](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingateaser)
* [Erstellen eines Newsletters](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatinganewsletter)
* [Erstellen eines Adobe Target-Angebots](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatesttargetoffer)

>[!NOTE]
>
>Wie bei früheren Versionen ist es weiterhin möglich, das Erlebnis als Seite im **Websites** -Konsole (und alle in früheren Versionen erstellten Seiten werden weiterhin vollständig unterstützt).
>
>Es wird jetzt empfohlen, den MCM zum Erstellen von Erlebnissen zu verwenden.

### Konfigurieren des neuen Erlebnisses {#configuring-your-new-experience}

Nachdem Sie das grundlegende Skelett für Ihr Erlebnis erstellt haben, müssen Sie je nach Erlebnistyp die folgenden Aktionen fortsetzen:

* [Teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers):

   * [Verknüpfen Sie die Teaser-Seite mit Besuchersegmenten.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#applyingasegmenttoyourteaser)
   * [Touchpoint für Ihren Teaser erstellen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatouchpointforyourteaser) (Fügen Sie Ihren Teaser zu einer Inhaltsseite hinzu).

* [Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters):

   * [Fügen Sie dem Newsletter Inhalt hinzu.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttonewsletters)
   * [Personalisieren Sie den Newsletter.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#personalizingnewsletters)
   * [Newsletter senden](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#sendingnewsletters) Abonnenten oder Leads.
   * [Erstellen einer attraktiven Landingpage für Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupanewsletterlandingpage).

* [Adobe Target-Angebot](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#testtargetoffers):

   * [Integrieren mit Adobe Target](/help/sites-administering/target.md)

### Hinzufügen eines neuen Touchpoints {#adding-a-new-touchpoint}

Wenn Sie über vorhandene Erlebnisse verfügen, können Sie einen Touchpoint direkt aus der Kalenderansicht von MCM hinzufügen:

1. Wählen Sie die Kalenderansicht für Ihre Kampagne aus.

1. Klicken Sie auf **Touchpoint hinzufügen...**, um das Dialogfeld zu öffnen. Geben Sie das Erlebnis an, das Sie hinzufügen möchten:

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Klicken Sie zum Speichern auf **OK**.

## Arbeiten mit Leads {#working-with-leads}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Lead-Verwaltung) weiter auszubauen.
>Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

In AEM MCM können Sie Leads ordnen und hinzufügen, indem Sie sie manuell eingeben oder indem Sie eine kommagetrennte Liste importieren, z. B. eine Mailing-Liste. Sie können Leads auch über Newsletter-Anmeldungen oder Community-Anmeldungen generieren. (Wenn diese Option konfiguriert ist, kann ein Workflow zum Ausfüllen von Leads Trigger werden.)

Leads werden im Allgemeinen kategorisiert und in eine Liste eingefügt, sodass Sie später Aktionen für die gesamte Liste durchführen können, z. B. eine benutzerdefinierte E-Mail an eine bestimmte Liste senden.

Über das Dashboard haben Sie Zugriff auf alle Leads, indem Sie im linken Bereich auf **Leads** klicken. Sie können auch über die **Listen** -Bereich.

![screen_shot_2012-02-21at114748am](assets/screen_shot_2012-02-21at114748am.png)

>[!NOTE]
>
>Um die Avatare von Benutzern hinzuzufügen oder zu ändern, öffnen Sie die Clickstream-Cloud (Strg+Alt+c), laden Sie das Profil und klicken Sie auf **Bearbeiten**.

### Erstellen neuer Leads {#creating-new-leads}

Denken Sie daran, die Leads nach dem Erstellen zu [aktivieren](#activating-or-deactivating-leads), damit Sie deren Aktivitäten auf der Veröffentlichungsinstanz verfolgen und das Benutzererlebnis personalisieren können.

So erstellen Sie einen Lead manuell:

1. Navigieren Sie in AEM zum MCM. Klicken Sie im Dashboard auf **Leads**.
1. Klicken Sie auf **Neu**. Die **Neu erstellen** öffnet sich.

   ![screen_shot_2012-02-21at115008am](assets/screen_shot_2012-02-21at115008am.png)

1. Geben Sie die Informationen in die Felder ein. Klicken Sie auf **Adresse** Registerkarte.

   ![screen_shot_2012-02-21at115045am](assets/screen_shot_2012-02-21at115045am.png)

1. Geben Sie die Adressinformationen ein. Klicken Sie auf **Speichern**, um den Lead zu speichern. Wenn Sie zusätzliche Leads hinzufügen müssen, klicken Sie auf **Speichern und neu**.

   Der neue Lead wird im Bereich „Leads“ angezeigt. Wenn Sie auf den Eintrag klicken, werden alle eingegebenen Informationen im rechten Bereich angezeigt. Nachdem Sie einen Lead erstellt haben, können Sie ihn einer Liste hinzufügen.

   ![screen_shot_2012-02-21at120307pm](assets/screen_shot_2012-02-21at120307pm.png)

### Aktivieren oder Deaktivieren von Leads {#activating-or-deactivating-leads}

Durch Aktivieren des Leads können Sie dessen Aktivitäten auf der Veröffentlichungsinstanz verfolgen und das Benutzererlebnis personalisieren. Wenn Sie ihre Aktivität nicht mehr verfolgen möchten, können Sie sie deaktivieren.

So aktivieren oder deaktivieren Sie Leads:

1. Navigieren Sie in AEM zu MCM und klicken Sie auf **Leads**.

1. Wählen Sie die Leads aus, die Sie aktivieren oder deaktivieren möchten, und klicken Sie auf **Aktivieren** oder **Deaktivieren**.

   ![screen_shot_2012-02-21at120620pm](assets/screen_shot_2012-02-21at120620pm.png)

   Wie bei AEM-Seiten wird der Veröffentlichungsstatus in der Spalte **Veröffentlicht** angezeigt.

   ![screen_shot_2012-02-21at122901pm](assets/screen_shot_2012-02-21at122901pm.png)

### Importieren neuer Leads {#importing-new-leads}

Wenn Sie neue Leads importieren, können Sie sie automatisch zu einer vorhandenen Liste hinzufügen oder eine Liste erstellen, um diese Leads einzuschließen.

So importieren Sie Leads aus einer kommagetrennten Liste:

1. Navigieren Sie in AEM zu MCM und klicken Sie auf **Leads**.

   >[!NOTE]
   >
   >Alternativ können Sie Leads importieren, indem Sie einen der folgenden Schritte ausführen:
   >
   >* Klicken Sie im Dashboard auf **Leads importieren** im **Listen** Bereich
   >* Klicks **Listen** und im **Instrumente** Menü auswählen **Leads importieren**.

1. Im **Instrumente** Menü auswählen **Import** **Leads**.

1. Geben Sie die Informationen wie unter Beispieldaten beschrieben ein. Die folgenden Felder können importiert werden: email,familyName,givenName,gender,aboutMe,city,country,phoneNumber,postalCode,region,streetAddress

   >[!NOTE]
   >
   >Die erste Zeile in der CSV-Liste sind vordefinierte Beschriftungen, die genau wie im Beispiel geschrieben werden müssen:
   >
   >
   >`email,givenName,familyName` – wenn Sie z. B. `givenname` schreiben, erkennt das System dies nicht.
   >
   >

   ![screen_shot_2012-02-21at123055pm](assets/screen_shot_2012-02-21at123055pm.png)

1. Klicken Sie auf **Weiter**. Hier können Sie eine Vorschau der Leads anzeigen, um sicherzustellen, dass die Angaben richtig sind.

   ![screen_shot_2012-02-21at123104pm](assets/screen_shot_2012-02-21at123104pm.png)

1. Klicken Sie auf **Weiter**. Wählen Sie die Liste aus, der die Leads angehören sollen. Wenn sie keiner Liste zugewiesen werden sollen, löschen Sie die Informationen aus dem Feld. Standardmäßig erstellt AEM einen Listennamen, der das Datum und die Uhrzeit enthält. Wählen Sie **Importieren**.

   ![screen_shot_2012-02-21at123123pm](assets/screen_shot_2012-02-21at123123pm.png)

   Der neue Lead wird im Bereich „Leads“ angezeigt. Wenn Sie auf den Eintrag klicken, werden alle eingegebenen Informationen im rechten Bereich angezeigt. Nachdem Sie einen Lead erstellt haben, können Sie ihn einer Liste hinzufügen.

### Hinzufügen von Leads zu Listen {#adding-leads-to-lists}

So fügen Sie Leads zu bereits vorhandenen Listen hinzu:

1. Klicken Sie im MCM auf **Leads** um alle verfügbaren Leads anzuzeigen.

1. Wählen Sie die Leads aus, die Sie einer Liste hinzufügen möchten, indem Sie das Kontrollkästchen neben dem Lead aktivieren. Sie können beliebig viele Leads hinzufügen.

   ![screen_shot_2012-02-21at123835pm](assets/screen_shot_2012-02-21at123835pm.png)

1. Wählen Sie aus dem Menü **Tools** die Option **Zu Liste hinzufügen...** aus. Das Fenster **Zu Liste hinzufügen** wird geöffnet.

   ![screen_shot_2012-02-21at124019pm](assets/screen_shot_2012-02-21at124019pm.png)

1. Wählen Sie die Liste aus, der Sie die Leads hinzufügen möchten, und klicken Sie auf **OK**. Die Leads werden den entsprechenden Listen hinzugefügt.

### Anzeigen von Lead-Informationen {#viewing-lead-information}

Um Lead-Informationen anzuzeigen, klicken Sie im MCM auf das Kontrollkästchen neben dem Lead und ein rechtes Fenster wird geöffnet, in dem alle Lead-Informationen einschließlich der Listenzugehörigkeit angezeigt werden.

![screen_shot_2012-02-21at124228pm](assets/screen_shot_2012-02-21at124228pm.png)

### Ändern vorhandener Leads {#modifying-existing-leads}

So ändern Sie vorhandene Lead-Informationen:

1. Klicken Sie im MCM auf **Leads**. Aktivieren Sie in der Liste der Leads das Kontrollkästchen neben dem Lead, den Sie bearbeiten möchten. Alle Lead-Informationen werden im rechten Bereich angezeigt.

   ![screen_shot_2012-02-21at124514pm](assets/screen_shot_2012-02-21at124514pm.png)

   >[!NOTE]
   >
   >Sie können nur jeweils einen Lead bearbeiten. Wenn Sie Leads ändern müssen, die Teil derselben Liste sind, können Sie stattdessen die Liste ändern.

1. Klicken Sie auf **Bearbeiten**. Die **Lead bearbeiten** öffnet sich.

   ![screen_shot_2012-02-21at124609pm](assets/screen_shot_2012-02-21at124609pm.png)

1. Nehmen Sie die gewünschten Änderungen vor und klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

   >[!NOTE]
   >
   >Gehen Sie zum Benutzerprofil, um den Lead-Avatar zu ändern. Sie können das Profil in der Clickstream-Cloud laden, indem Sie Strg+ALT+C drücken und auf **Laden** und wählen Sie dann das Profil aus.

### Löschen vorhandener Leads {#deleting-existing-leads}

Wählen Sie zum Löschen von bestehenden Leads im MCM das Kontrollkästchen neben dem Lead aus und klicken Sie auf **Löschen**. Der Lead wird aus der Lead-Liste und allen zugehörigen Listen entfernt.

>[!NOTE]
>
>Vor dem Löschen fragt AEM noch einmal nach, ob Sie den bestehenden Lead wirklich löschen möchten. Nach dem Löschen kann er nicht mehr abgerufen werden.

## Arbeiten mit Listen {#working-with-lists}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Listenverwaltung) weiter auszubauen.
>Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

Mithilfe von Listen können Sie Ihre Leads in Gruppen organisieren. Mit Listen können Sie Marketing-Kampagnen gezielt für eine bestimmte Personengruppe erstellen, z. B. können Sie einen speziellen Newsletter an eine bestimmte Liste senden. Auf die Listen können Sie im MCM über das Dashboard oder durch Klicken auf **Listen** zugreifen. Beide geben den Namen der Liste und die Anzahl der Mitglieder an.

![screen_shot_2012-02-21at125021pm](assets/screen_shot_2012-02-21at125021pm.png)

Wenn Sie auf **Listen** können Sie auch anzeigen, ob die Liste Mitglied einer anderen Liste ist, und eine Beschreibung anzeigen.

![screen_shot_2012-02-21at124828pm](assets/screen_shot_2012-02-21at124828pm.png)

### Erstellen neuer Listen {#creating-new-lists}

1. Klicken Sie im MCM-Dashboard auf **Neue Liste ...** oder **Listen** klicken **Neu** ... Das Fenster Liste erstellen wird geöffnet.

   ![screen_shot_2012-02-21at125147pm](assets/screen_shot_2012-02-21at125147pm.png)

1. Geben Sie einen Namen (erforderliche Angabe) und falls gewünscht eine Beschreibung ein und klicken Sie auf **Speichern**. Die Liste wird im **Listen** -Bereich.

   ![screen_shot_2012-02-21at125320pm](assets/screen_shot_2012-02-21at125320pm.png)

### Vorhandene Listen ändern {#modifying-existing-lists}

1. Klicken Sie im MCM auf **Listen**.

1. Aktivieren Sie in der Liste das Kontrollkästchen neben der Liste, die Sie bearbeiten möchten, und klicken Sie auf **Bearbeiten**. Die **Liste bearbeiten** öffnet sich.

   ![screen_shot_2012-02-21at125452pm](assets/screen_shot_2012-02-21at125452pm.png)

   >[!NOTE]
   >
   >Sie können jeweils nur eine Liste bearbeiten.

1. Nehmen Sie die gewünschten Änderungen vor und klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

### Löschen vorhandener Listen {#deleting-existing-lists}

Wählen Sie zum Löschen von bestehenden Listen im MCM das Kontrollkästchen neben der Liste aus und klicken Sie auf **Löschen**. Die Liste wird gelöscht. Leads, die mit der Liste verknüpft waren, werden nicht entfernt - nur die Zuordnung zur Liste wird gelöscht.

>[!NOTE]
>
>Vor dem Löschen fragt AEM noch einmal nach, ob Sie die bestehende Liste wirklich löschen möchten. Nach dem Löschen kann er nicht mehr abgerufen werden.

### Zusammenführen von Listen {#merging-lists}

Sie können eine bestehende Liste mit einer anderen zusammenführen. Dabei wird die Liste, die Sie zusammenführen, Mitglied der anderen Liste. Sie existiert weiterhin als separate Entität und sollte nicht gelöscht werden.

Sie können Listen zusammenführen, wenn Sie dieselbe Konferenz an zwei verschiedenen Orten haben und sie zu einer Teilnehmerliste aller Konferenzen zusammenführen möchten.

So führen Sie bestehende Listen zusammen:

1. Klicken Sie im MCM auf **Listen**.

1. Wählen Sie die Liste aus, mit der Sie eine andere Liste zusammenführen möchten, indem Sie das Kontrollkästchen daneben aktivieren.

1. Im **Instrumente** Menü auswählen **Zusammenführungsliste**.

   >[!NOTE]
   >
   >Sie können jeweils nur eine Liste zusammenführen.

1. Im **Zusammenführungsliste** , wählen Sie die Liste aus, mit der Sie zusammenführen möchten, und klicken Sie auf **OK**.

   ![screen_shot_2012-02-21at10259pm](assets/screen_shot_2012-02-21at10259pm.png)

   Die zusammengeführte Liste sollte ein zusätzliches Mitglied anzeigen. Um zu sehen, dass Ihre Liste zusammengeführt wurde, wählen Sie die zusammengeführte Liste aus und **Instrumente** Menü auswählen **Leads anzeigen**.

1. Wiederholen Sie diesen Schritt, bis Sie alle gewünschten Listen zusammengeführt haben.

   ![screen_shot_2012-02-21at10538pm](assets/screen_shot_2012-02-21at10538pm.png)

>[!NOTE]
>
>Das Entfernen einer zusammengeführten Liste aus der Mitgliedschaft entspricht dem Entfernen von Leads aus einer Liste. Öffnen Sie die **Listen** wählen Sie die Liste aus, die die zusammengeführte Liste enthält, und entfernen Sie die Mitgliedschaft, indem Sie auf den roten Kreis neben der Liste klicken.

### Anzeigen von Leads in Listen {#viewing-leads-in-lists}

Sie können jederzeit anzeigen, welche Leads zu einer bestimmten Liste gehören, indem Sie Mitglieder durchsuchen oder suchen.

So zeigen Sie Leads in Listen an:

1. Klicken Sie im MCM auf **Listen**.

1. Aktivieren Sie das Kontrollkästchen neben der Liste, für die Sie Mitglieder anzeigen möchten.

1. Wählen Sie im Menü **Tools** die Option **Leads anzeigen** aus. AEM zeigt die Leads an, die Mitglieder dieser Liste sind. Sie können die Liste durchsuchen oder nach Mitgliedern suchen.

   >[!NOTE]
   >
   >Außerdem können Sie Leads aus einer Liste löschen, indem Sie sie auswählen und auf **Mitgliedschaft entfernen**.

   ![screen_shot_2012-02-21at10828pm](assets/screen_shot_2012-02-21at10828pm.png)

1. Klicken Sie auf **Schließen**, um zu MCM zurückzukehren.
