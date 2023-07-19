---
title: Arbeiten mit dem Marketing Campaign Manager
seo-title: Working with the Marketing Campaign Manager
description: Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie Multi-Channel-Kampagnen verwalten können. Mit dieser Software zur Marketing-Automatisierung können Sie alle Ihre Marken, Kampagnen und Erlebnisse gemeinsam mit den zugehörigen Segmenten, Listen, Leads und Berichten verwalten.
seo-description: The Marketing Campaign Manager (MCM) is a console that helps you manage multi-channel campaigns. With this marketing automation software you can manage all your brands, campaigns and experiences together with the related segments, lists, leads, and reports.
uuid: 63b817e4-34b9-42b8-845b-e0b7d9af3a96
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 11ff8bb3-39eb-4f77-b3dc-720262fa7f3f
docset: aem65
exl-id: 0e13112b-d9df-4ba6-bd73-431c87890b79
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 54%

---

# Arbeiten mit dem Marketing Campaign Manager{#working-with-the-marketing-campaign-manager}

Der Marketing Campaign Manager (MCM) in AEM ist eine Konsole, mit der Sie Multi-Channel-Kampagnen verwalten können. Mit dieser Software zur Marketing-Automatisierung können Sie alle Ihre Marken, Kampagnen und Erlebnisse gemeinsam mit den zugehörigen Segmenten, Listen, Leads und Berichten verwalten.

Der Zugriff auf MCM erfolgt über verschiedene Stellen in AEM. beispielsweise den Begrüßungsbildschirm, über das Kampagnensymbol oder mit der URL:

`https://<hostname>:<port>/libs/mcm/content/admin.html`

Beispiel:

`https://localhost:4502/libs/mcm/content/admin.html`

![screen_shot_2012-02-21at114636am](assets/screen_shot_2012-02-21at114636am.png)

Aus MCM können Sie auf folgende Komponenten zugreifen:

* **[Dashboard](#dashboard)**
Dieses ist in vier Bereiche unterteilt:

   * [Listen](#lists)
Dieser Bereich enthält die Listen, die Sie bereits erstellt haben, sowie die Anzahl der Leads in den jeweiligen Listen. Aus diesem Bereich können Sie direkt neue Listen erstellen oder Leads importieren, um eine neue Liste zu erstellen.
Wenn Sie eine bestimmte Liste auswählen, gelangen Sie in den Bereich [Listen](#lists), der Details zu Ihrer Liste enthält.

   * [Segmente](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#anoverviewofsegmentation)
Dieser Bereich enthält die Segmente, die Sie definiert haben. Mit Segmenten können Sie eine Gruppe von Besuchern charakterisieren, die bestimmte Eigenschaften teilen.
Wenn Sie ein bestimmtes Segment auswählen, wird die Segment-Definitionsseite geöffnet.

   * [Berichte](/help/sites-administering/reporting.md)
In AEM stehen verschiedene Berichte zur Verfügung, mit denen Sie den Status Ihrer Instanz analysieren und überwachen können. In diesem MCM-Bereich werden die Berichte angezeigt.
Wenn Sie einen Bericht auswählen, wird die Berichtseite geöffnet.

   * [Kampagnen](#campaigns)
In diesem Fenster werden Ihre Kampagnenerlebnisse wie [Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) und [Teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) aufgeführt.

* **[Leads](#leads)**
Hier können Sie Ihre Leads verwalten. Sie können Leads erstellen oder importieren, bestimmte Details für einzelne Leads bearbeiten oder löschen, wenn sie nicht mehr benötigt werden. Außerdem können Sie Leads in verschiedene Gruppen, sogenannte Listen, einteilen. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.
Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **[Listen](#lists)**
Hier können Sie Ihre (Lead-)Listen verwalten.**Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.
Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

* **[Kampagnen](#campaigns)**
Hier können Sie Ihre Marken, Kampagnen und Erlebnisse verwalten.

## Dashboard {#dashboard}

Das Dashboard enthält vier Bereiche, die Ihnen eine Übersicht über Ihre (Lead-)Listen, Segmente, Berichte und Kampagnen bieten. Hier finden Sie auch Zugriff auf grundlegende Funktionen für diese.

![mcm_dashboard](assets/mcm_dashboard.png)

### Leads {#leads}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Lead-Verwaltung) weiter auszubauen.
>Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

Im MCM von AEM können Sie Leads organisieren und hinzufügen, indem Sie sie manuell eingeben oder indem Sie eine kommagetrennte Liste importieren, z. B. eine Mailing-Liste. Sie können Leads auch anhand von Newsletter- oder Community-Anmeldungen generieren. (Wenn dies konfiguriert wurde, kann nach einer Anmeldung ein Workflow ausgelöst werden, aus dem Leads hervorgehen.) Leads werden in der Regel kategorisiert und in eine Liste eingefügt, sodass Sie später Aktionen für die gesamte Liste durchführen können. Senden einer benutzerdefinierten E-Mail an eine bestimmte Liste.

Im linken Bereich unter **Leads** können Sie Ihre Leads erstellen, importieren, bearbeiten und löschen und anschließend nach Bedarf aktivieren oder deaktivieren. Sie können einen Lead zu einer Liste hinzufügen oder sehen, zu welchen Listen er bereits gehört.

>[!NOTE]
>
>Genauere Informationen zu bestimmten Aufgaben finden Sie unter [Arbeiten mit Leads](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithleads).

![screen_shot_2012-02-21at114748am-1](assets/screen_shot_2012-02-21at114748am-1.png)

### Listen {#lists}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Listenverwaltung) weiter auszubauen.
>Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

Mithilfe von Listen können Sie Ihre Leads in Gruppen organisieren. Mit Listen können Sie Ihre Marketing-Kampagnen auf eine ausgewählte Personengruppe ausrichten. Sie können beispielsweise einen zielgerichteten Newsletter an eine Liste senden.

Unter **Listen** können Sie Ihre Listen verwalten, indem Sie Listen erstellen, importieren, bearbeiten, zusammenführen und löschen und dann nach Bedarf aktivieren oder deaktivieren. Sie können auch die Leads in dieser Liste anzeigen, sehen, ob die Liste Mitglied einer anderen Liste ist, oder die Beschreibung anzeigen.

>[!NOTE]
>
>Genauere Informationen zu bestimmten Aufgaben finden Sie unter [Arbeiten mit Listen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists).

![screen_shot_2012-02-21at124828pm-1](assets/screen_shot_2012-02-21at124828pm-1.png)

### Kampagnen {#campaigns}

>[!NOTE]
>
>Unter [Teaser und Strategien](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists), [Einrichten einer Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupyourcampaign) und [Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) finden Sie genauere Informationen zu bestimmten Aufgaben.

Klicken Sie in MCM auf **Kampagnen**, um auf die bestehenden Kampagnen zuzugreifen.

![screen_shot_2012-02-21at11106pm](assets/screen_shot_2012-02-21at11106pm.png)

* **Linker Bereich**:
Hier finden Sie eine vollständige Aufzählung aller Marken und Kampagnen.
Mit einem einzigen Klick auf eine Marke können Sie Folgendes tun:

   * Erweitern Sie die Liste, um alle zugehörigen Kampagnen im linken Bereich anzuzeigen. Diese Liste zeigt auch die Anzahl der Erlebnisse an, die für jede Kampagne vorhanden sind.
   * Öffnen Sie die Markenübersicht im rechten Bereich.

* **Rechter Bereich**:
Hier werden für jede Marke Symbole angezeigt (historische Kampagnen werden nicht aufgeführt).
Sie können auf diese doppelklicken, um die Markenübersicht zu öffnen.

#### Markenübersicht {#brand-overview}

![mcm_brandoverview](assets/mcm_brandoverview.png)

Hier können Sie folgende Aktionen durchführen:

* Sehen Sie sich die Anzahl der Kampagnen und Erlebnisse an (Zahl wird im linken Bereich angezeigt), die für diese Marke vorhanden sind.
* Erstellen Sie eine **Neu...** Kampagne für diese Marke.

* Ändern des angezeigten Zeitbereichs; select **Woche**, **Monat** oder **Quartal** verwenden, um bestimmte Zeiträume auszuwählen oder zu **Heute**.

* Wählen Sie eine Kampagne (im rechten Bereich) aus, um:

   * Bearbeiten Sie die **Eigenschaften...**
   * **Löschen** die Kampagne.

* Öffnen Sie die Kampagnenübersicht (doppelklicken Sie im rechten Bereich auf eine Kampagne oder klicken Sie einfach im linken Bereich auf eine Kampagne).

#### Kampagnenübersicht {#campaign-overview}

Für die einzelnen Kampagnen stehen zwei Ansichten zur Verfügung:

1. **Kalenderansicht**

   Verwenden Sie das Symbol:

   ![Kalenderansicht](do-not-localize/mcm_iconcalendarview.png)

   Hier finden Sie eine Liste aller Touchpoints (grau) mit einem horizontalen Zeitrahmen der Erlebnisse (grün), die mit diesem Touchpoint verbunden sind:

   ![mcm_banner_calendarview](assets/mcm_banner_calendarview.png)

   Hier können Sie folgende Aktionen durchführen:

   * Ändern Sie den angezeigten Zeitraum mithilfe der Pfeile oder kehren Sie zu **Heute**.

   * Verwendung **Touchpoint hinzufügen...** , um einen neuen Touchpoint für ein vorhandenes Erlebnis hinzuzufügen.

   * Klicken Sie auf einen Teaser (im rechten Bereich), um die **Einschaltzeit** und **Ausschaltzeit**.

1. **Listenansicht**

   Verwenden Sie das Symbol:

   ![Listenansicht](do-not-localize/mcm_icon_listview.png)

   Hier werden alle Erlebnisse (z. B. Teaser und Newsletter) für die ausgewählte Kampagne aufgelistet:

   ![mcm_banner_listview](assets/mcm_banner_listview.png)

   Hier können Sie folgende Aktionen durchführen:

   * Erstellen eines **neuen** Erlebnisses, z. B. Adobe Target-Angebote, Teaser und Newsletter.
   * **Bearbeiten** die Details einer bestimmten Teaser-Seite oder eines bestimmten Newsletters (es kann auch ein Doppelklick verwendet werden).
   * Definieren Sie die **Eigenschaften...** für eine bestimmte Teaser-Seite oder einen bestimmten Newsletter.
   * **Simulieren** des Aussehens eines Erlebnisses (Teaser-Seite oder Newsletter).
Wenn die simulierte Seite geöffnet ist, können Sie den Sidekick öffnen, um in den Bearbeitungsmodus für diese Seite zu wechseln.

   * **Analysieren...** die für eine Seite generierten Impressionen.

   * **Löschen** Elemente, wenn sie nicht mehr benötigt werden.
   * **Suchen** nach Text (das Feld „Titel“ des Erlebnisses wird durchsucht).
   * Verwendung **Erweitert** Suchen, um Filter auf die Suche anzuwenden.

### Simulieren Ihrer Campaign-Erlebnisse {#simulating-your-campaign-experiences}

Klicken Sie im MCM auf **Kampagnen**. Vergewissern Sie sich, dass die Listenansicht aktiv ist, wählen Sie dann die gewünschte Kampagnenerfahrung und klicken Sie auf **Simulieren**. Der Touchpoint (Teaser- oder Newsletter-Seite) wird geöffnet, um das von Ihnen ausgewählte Erlebnis anzuzeigen, wie es dem Besucher angezeigt wird.

![mcm_simateexperience](assets/mcm_simulateexperience.png)

Von hier aus können Sie auch den Sidekick öffnen (klicken Sie auf den kleinen Pfeil nach unten), um in den Bearbeitungsmodus zu wechseln, um die Seite zu aktualisieren.

### Analysieren Ihrer Kampagnenerlebnisse {#analyzing-your-campaign-experiences}

Klicken Sie im MCM auf **Kampagnen**. Vergewissern Sie sich, dass die Listenansicht aktiv ist, wählen Sie dann die gewünschte Kampagnenerfahrung und klicken Sie auf **Analysieren...**. Ein Diagramm der Seitenimpressionen im Zeitverlauf wird angezeigt.

![mcm_campaignanalyze](assets/mcm_campaignanalyze.png)
