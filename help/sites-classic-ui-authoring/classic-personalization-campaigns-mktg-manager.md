---
title: Arbeiten mit dem Marketing Campaign Manager
description: Der Marketing Campaign Manager (MCM) ist eine Konsole, mit der Sie Multi-Channel-Kampagnen verwalten können. Mit dieser Software zur Marketing-Automatisierung können Sie alle Ihre Marken, Kampagnen und Erlebnisse zusammen mit den zugehörigen Segmenten, Listen, Leads und Berichten verwalten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 0e13112b-d9df-4ba6-bd73-431c87890b79
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 87%

---

# Arbeiten mit dem Marketing Campaign Manager{#working-with-the-marketing-campaign-manager}

Der Marketing Campaign Manager (MCM) in AEM ist eine Konsole, mit der Sie Multi-Channel-Kampagnen verwalten können. Mit dieser Software zur Marketing-Automatisierung können Sie alle Ihre Marken, Kampagnen und Erlebnisse zusammen mit den zugehörigen Segmenten, Listen, Leads und Berichten verwalten.

Der Zugriff auf MCM erfolgt über verschiedene Stellen in AEM, beispielsweise der Begrüßungsbildschirm, das Kampagnensymbol oder die URL:

`https://<hostname>:<port>/libs/mcm/content/admin.html`

Beispiel:

`https://localhost:4502/libs/mcm/content/admin.html`

![screen_shot_2012-02-21at114636am](assets/screen_shot_2012-02-21at114636am.png)

Aus MCM können Sie auf folgende Komponenten zugreifen:

* **[Dashboard](#dashboard)**
Dieses ist in vier Bereiche unterteilt:

   * [Listen](#lists)
Dieser Bereich enthält die Listen, die Sie bereits erstellt haben, sowie die Anzahl der Leads in den jeweiligen Listen. In diesem Bereich können Sie eine Liste direkt erstellen oder Leads importieren, um eine Liste zu erstellen.
Wenn Sie eine bestimmte Liste auswählen, gelangen Sie in den Bereich [Listen](#lists), der Details zu Ihrer Liste enthält.

   * [Segmente](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#anoverviewofsegmentation)
Dieser Bereich enthält die Segmente, die Sie definiert haben. Mit Segmenten können Sie eine Gruppe von Besuchern charakterisieren, die bestimmte Eigenschaften teilen.
Wenn Sie ein bestimmtes Segment auswählen, wird die Seite zur Segmentdefinition geöffnet.

   * [Berichte](/help/sites-administering/reporting.md)
In AEM stehen verschiedene Berichte zur Verfügung, mit denen Sie den Status Ihrer Instanz analysieren und überwachen können. In diesem MCM-Bereich werden die Berichte angezeigt.
Wenn Sie einen Bericht auswählen, wird die Berichtseite geöffnet.

   * [Kampagnen](#campaigns)
In diesem Fenster werden Ihre Kampagnenerlebnisse wie [Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) und [Teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) aufgeführt.

* **[Leads](#leads)**
Hier können Sie Ihre Leads verwalten. Sie können Leads erstellen oder importieren, bestimmte Details für einzelne Leads bearbeiten oder löschen, wenn sie nicht mehr benötigt werden. Außerdem können Sie Leads in verschiedene Gruppen, sogenannte Listen, einteilen. **Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.
Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

* **[Listen](#lists)**
Hier können Sie Ihre (Lead-)Listen verwalten.**Hinweis:** Adobe plant nicht, diese Funktion weiter auszubauen.
Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

* **[Kampagnen](#campaigns)**
Hier können Sie Ihre Marken, Kampagnen und Erlebnisse verwalten.

## Dashboard {#dashboard}

Das Dashboard enthält vier Bereiche, die Ihnen eine Übersicht über Ihre (Lead-)Listen, Segmente, Berichte und Kampagnen bieten. Hier haben Sie auch Zugriff auf deren grundlegende Funktionen.

![mcm_dashboard](assets/mcm_dashboard.png)

### Leads {#leads}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Lead-Verwaltung) weiter auszubauen.
>Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

Im MCM von AEM können Sie Leads organisieren und hinzufügen, indem Sie sie manuell eingeben oder indem Sie eine kommagetrennte Liste importieren, z. B. eine Mailing-Liste. Sie können Leads auch anhand von Newsletter- oder Community-Anmeldungen generieren. (Wenn dies konfiguriert wurde, kann nach einer Anmeldung ein Workflow ausgelöst werden, aus dem Leads hervorgehen.) Leads werden in der Regel kategorisiert und in eine Liste eingefügt, sodass Sie später Aktionen für die gesamte Liste durchführen können, beispielsweise Senden einer benutzerdefinierten E-Mail an eine bestimmte Liste.

Im linken Bereich unter **Leads** können Sie Ihre Leads erstellen, importieren, bearbeiten und löschen und anschließend nach Bedarf aktivieren oder deaktivieren. Sie können einen Lead zu einer Liste hinzufügen oder sehen, zu welchen Listen er bereits gehört.

>[!NOTE]
>
>Genauere Informationen zu bestimmten Aufgaben finden Sie unter [Arbeiten mit Leads](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithleads).

![screen_shot_2012-02-21at114748am-1](assets/screen_shot_2012-02-21at114748am-1.png)

### Listen {#lists}

>[!NOTE]
>
>Adobe plant nicht, diese Funktion (Listenverwaltung) weiter auszubauen.
>Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

Mithilfe von Listen können Sie Ihre Leads in Gruppen organisieren. Mit Listen können Sie Marketing-Kampagnen gezielt für eine bestimmte Personengruppe erstellen, z. B. können Sie einen zielgruppengerechten Newsletter an eine Liste senden.

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
Wenn Sie auf eine Marke klicken, wird die Liste um alle zugehörigen Kampagnen im linken Bereich erweitert. Diese Liste zeigt auch die Anzahl der Erlebnisse, die für jede Kampagne vorhanden sind. Außerdem wird die Markenübersicht im rechten Bereich geöffnet.

* **Rechter Bereich**:
Hier werden für jede Marke Symbole angezeigt (historische Kampagnen werden nicht aufgeführt).
Sie können auf diese Elemente doppelklicken, um die Markenübersicht zu öffnen.

#### Markenübersicht {#brand-overview}

![mcm_brandoverview](assets/mcm_brandoverview.png)

Hier können Sie folgende Aktionen durchführen:

* Anzeigen der Anzahl von Kampagnen und Erlebnissen (Zahl wird im linken Bereich angezeigt), die für diese Marke vorhanden sind.
* Erstellen einer **neuen** Kampagne für diese Marke.

* Ändern des angezeigten Zeitbereichs. Wählen Sie **Woche**, **Monat** oder **Quartal**, verwenden Sie die Pfeile, um bestimmte Zeitabschnitte auszuwählen, oder kehren Sie zu **Heute** zurück.

* Auswählen einer Kampagne (im rechten Bereich), um folgende Aktionen auszuführen:

   * Bearbeiten der **Eigenschaften**.
   * **Löschen** der Kampagne.

* Öffnen der Kampagnenübersicht (doppelklicken Sie im rechten Bereich auf eine Kampagne oder klicken Sie im linken Bereich einmal).

#### Kampagnenübersicht {#campaign-overview}

Für die einzelnen Kampagnen stehen zwei Ansichten zur Verfügung:

1. **Kalenderansicht**

   Verwenden Sie das Symbol:

   ![Kalenderansicht](do-not-localize/mcm_iconcalendarview.png)

   Hier finden Sie eine Liste aller Touchpoints (grau) mit einem horizontalen Zeitrahmen der Erlebnisse (grün), die mit diesem Touchpoint verbunden sind:

   ![mcm_banner_calendarview](assets/mcm_banner_calendarview.png)

   Hier können Sie folgende Aktionen durchführen:

   * Ändern des angezeigten Zeitbereichs mit den Pfeilen bzw. zu **Heute** zurückkehren.

   * Verwenden von **Touchpoint hinzufügen**, um einem vorhandenen Erlebnis einen neuen Touchpoint hinzuzufügen.

   * Klicken auf einen Teaser (im rechten Bereich), um die **Einschaltzeit** und die **Ausschaltzeit** einzurichten.

1. **Listenansicht**

   Verwenden Sie das Symbol:

   ![Listenansicht](do-not-localize/mcm_icon_listview.png)

   Hier werden alle Erlebnisse (z. B. Teaser und Newsletter) für die ausgewählte Kampagne aufgelistet:

   ![mcm_banner_listview](assets/mcm_banner_listview.png)

   Hier können Sie folgende Aktionen durchführen:

   * Erstellen eines **neuen** Erlebnisses, z. B. Adobe Target-Angebote, Teaser und Newsletter.
   * **Bearbeiten** der Details einer bestimmten Teaser-Seite oder eines bestimmten Newsletters (auch per Doppelklick möglich).
   * Definieren der **Eigenschaften** für eine bestimmte Teaser-Seite oder einen bestimmten Newsletter.
   * **Simulieren** des Aussehens eines Erlebnisses (Teaser-Seite oder Newsletter).
Wenn die simulierte Seite geöffnet ist, können Sie den Sidekick öffnen, um in den Bearbeitungsmodus für diese Seite zu wechseln.

   * **Analysieren** der für eine Seite erzeugten Impressionen.

   * **Löschen** von Elementen, die nicht mehr benötigt werden.
   * **Suchen** nach Text (das Feld „Titel“ des Erlebnisses wird durchsucht).
   * Verwenden der **erweiterten** Suche, um Filter auf die Suche anzuwenden.

### Simulieren Ihrer Kampagnenerlebnisse {#simulating-your-campaign-experiences}

Klicken Sie im MCM auf **Kampagnen**. Vergewissern Sie sich, dass die Listenansicht aktiv ist, wählen Sie dann die gewünschte Kampagnenerfahrung und klicken Sie auf **Simulieren**. Der Touchpoint (Teaser- oder Newsletter-Seite) wird geöffnet, um das von Ihnen ausgewählte Erlebnis anzuzeigen, wie es den Besuchenden angezeigt wird.

![mcm_simateexperience](assets/mcm_simulateexperience.png)

Von hier aus können Sie auch den Sidekick öffnen (klicken Sie auf den kleinen Pfeil nach unten), um in den Bearbeitungsmodus zu wechseln, um die Seite zu aktualisieren.

### Analysieren Ihrer Kampagnenerlebnisse {#analyzing-your-campaign-experiences}

Klicken Sie im MCM auf **Kampagnen**. Vergewissern Sie sich, dass die Listenansicht aktiv ist, wählen Sie dann die gewünschte Kampagnenerfahrung und klicken Sie auf **Analysieren...**. Ein Diagramm der Seitenimpressionen im Zeitverlauf wird angezeigt.

![mcm_campaignanalyze](assets/mcm_campaignanalyze.png)
