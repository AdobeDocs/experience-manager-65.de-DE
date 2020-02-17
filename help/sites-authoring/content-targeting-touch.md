---
title: Verfassen zielgerichteter Inhalte im Targeting-Modus
seo-title: Verfassen zielgerichteter Inhalte im Targeting-Modus
description: Im Targeting-Modus und in der Targeting-Komponente stehen verschiedene Werkzeuge zur Verfügung, mit deren Hilfe sich Inhalte für Erlebnisse erstellen lassen
seo-description: Im Targeting-Modus und in der Targeting-Komponente stehen verschiedene Werkzeuge zur Verfügung, mit deren Hilfe sich Inhalte für Erlebnisse erstellen lassen
uuid: cea85c1b-1bc3-4498-9eaa-4ad10dc58ea4
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 9d940744-3b00-4721-829a-96d17bb738e8
docset: aem65
translation-type: tm+mt
source-git-commit: 6853306d217809e05dbef4968c75bfef9d048f1c

---


# Verfassen zielgerichteter Inhalte im Targeting-Modus{#authoring-targeted-content-using-targeting-mode}

Verfassen Sie zielgerichtete Inhalte im Targeting-Modus vom AEM. Im Targeting-Modus und in der Targeting-Komponente stehen verschiedene Werkzeuge zur Verfügung, mit deren Hilfe sich Inhalte für Erlebnisse erstellen lassen:

* Erkennen Sie problemlos zielgerichtete Inhalte auf einer Seite. Zielgerichtete Inhalte werden mit einer gepunkteten Linie umrandet.
* Wählen Sie eine Marke und Aktivität aus, um deren Erlebnisse anzuzeigen.
* Fügen Sie einer Aktivität Erlebnisse hinzu oder entfernen Sie diese.
* Führen Sie A/B-Tests durch und konvertieren Sie die Kampagnen mit den besten Ergebnissen (nur Adobe Target).
* Fügen Sie Erlebnissen Angebote hinzu, indem Sie Angebote erstellen oder Angebote aus einer Bibliothek verwenden.
* Konfigurieren Sie Ziele und überwachen Sie die Leistung.
* Simulieren Sie Benutzererlebnisse.
* Für weitere Anpassungsmöglichkeiten muss zunächst die Target-Komponente konfiguriert werden.

Als Targeting-Engine können Sie entweder AEM oder Adobe Target einsetzen (möchten Sie Adobe Target nutzen, benötigen Sie ein aktives Adobe Target-Konto). Wenn Sie Adobe Target verwenden, müssen Sie zunächst die Integration konfigurieren. See [instructions for integrating with Adobe Target](/help/sites-administering/target.md).

![chlimage_1-8](assets/chlimage_1-8.png)

Die im Target-Modus sichtbaren Aktivitäten und Erlebnisse spiegeln die Optionen der [Aktivitätskonsole](/help/sites-authoring/activitylib.md) wider:

* Änderungen, die Sie im Targeting-Modus an den Aktivitäten und Erlebnissen vornehmen, werden in die Aktivitätskonsole übernommen.
* Änderungen, die in der Aktivitätskonsole vorgenommen werden, werden in den Targeting-Modus übernommen.

>[!NOTE]
>
>Erstellen Sie in Adobe Target eine Kampagne, wird dieser eine Eigenschaft mit der Bezeichnung `thirdPartyId` zugewiesen. Sollten Sie die Kampagne in Adobe Target löschen, wird die Eigenschaft „thirdPartyId“ jedoch nicht gelöscht. Die `thirdPartyId` kann nicht für Kampagnen unterschiedlicher Typen (AB, XT) wiederverwendet werden und lässt sich nicht manuell löschen. Benennen Sie zur Vermeidung dieses Problems jede Kampagne einen eindeutigen Namen; Kampagnennamen können daher nicht in verschiedenen Kampagnentypen wiederverwendet werden.
>
>Sollten Sie den gleichen Namen für verschiedene Kampagnentypen verwenden, wird die bereits bestehende Kampagne überschrieben.
>
>Sollte Ihnen beim Synchronisieren die Fehlermeldung „Anforderung fehlgeschlagen. `thirdPartyId` ist bereits vorhanden“ angezeigt werden, ändern Sie den Kampagnennamen und synchronisieren Sie erneut.

>[!NOTE]
>
>Beim Targeting bleibt die Kombination aus Branding und Aktivität auf Benutzerebene gleich, nicht auf Kanalebene.

## Wechseln in den Modus „Targeting“ {#switching-to-targeting-mode}

Wechseln Sie in den Targeting-Modus, um auf die Werkzeuge für die Erstellung von zielgerichtetem Inhalt zuzugreifen.

So wechseln Sie in den Targeting-Modus:

1. Öffnen Sie die Seite, auf der Sie zielgerichtete Inhalte veröffentlichen möchten.
1. Klicken Sie in der Symbolleiste am oberen Rand der Seite auf das Dropdown-Menü Modus oder tippen Sie darauf, um die verfügbaren Modustypen anzuzeigen.

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Klicken oder tippen Sie auf **Targeting**. Die Targeting-Optionen werden daraufhin oben auf der Seite eingeblendet.

   ![chlimage_1-10](assets/chlimage_1-10.png)

## Hinzufügen von Aktivitäten im Targeting-Modus {#adding-an-activity-using-targeting-mode}

Verwenden Sie den Targeting-Modus, um einer Marke eine Aktivität hinzuzufügen. Eine von Ihnen hinzugefügte Aktivität enthält automatisch das Standarderlebnis. Nach dem Hinzufügen der Aktivität können Sie mit dem Targeting-Verfahren für deren Inhalt beginnen.

Außerdem haben Sie die Möglichkeit, Adobe Target-Aktivitäten mit AEM zu erstellen und zu verwalten, indem Sie die entsprechende Targeting-Engine (AEM oder Adobe Target) und den Aktivitätstyp (Erlebnis-Targeting oder A/B-Test) auswählen.

Darüber hinaus können Sie Ziele und Metriken aller Adobe Target-Aktivitäten sowie Ihre Adobe Target-Zielgruppen verwalten. Zu guter Letzt steht Ihnen auch die Aktivitätsberichterstellung von Adobe Target zur Verfügung, die unter anderem auch die Konvertierung der im A/B-Test am besten abschneidenden Erlebnisse umfasst.

Fügen Sie eine Aktivität hinzu, erscheint diese auch in der [Aktivitätskonsole](/help/sites-authoring/activitylib.md).

So fügen Sie eine Aktivität hinzu:

1. Wählen Sie im Dropdown-Menü **Marke** diejenige Marke aus, für die Sie eine Aktivität erstellen möchten.

   >[!NOTE]
   >
   >Es wird empfohlen, [Marken über die Aktivitätskonsole zu erstellen](/help/sites-authoring/activitylib.md#creating-a-brand-using-the-activities-console).
   >
   >
   >If you create a brand in any other way, make certain that the node `/campaigns/<brand>/master` exists or an error will result when you attempt to create an activity.

1. Klicken oder tippen Sie neben dem Dropdown-Menü **Aktivität** auf das Plus-Zeichen (+).
1. Geben Sie einen Namen für die Aktivität ein.

   >[!NOTE]
   >
   >Wenn Sie eine neue Aktivität erstellen und der Seite oder einer der ihr übergeordneten Seiten eine Adobe Target-Cloud-Konfiguration angehängt ist, wird Adobe Target automatisch von AEM als Targeting-Engine festgelegt.

1. Wählen Sie aus dem Dropdown-Menü **Targeting** die gewünschte Targeting-Engine aus.

   * If you select **ContextHub AEM**, the remaining fields are dimmed and not available. Klicken oder tippen Sie auf **Erstellen**.

   * Wenn Sie **Adobe Target** auswählen, können Sie eine Konfiguration (standardmäßig ist die Konfiguration festgelegt, die Sie bei der [Konfiguration des Kontos](/help/sites-administering/opt-in.md) angelegt haben) und einen Aktivitätstyp auswählen.

   * Sollten Sie mit der Integration von AEM und Adobe Campaign arbeiten und zielgerichtete Inhalte (Newsletter) versenden, wählen Sie **Adobe Campaign** aus. Weitere Informationen finden Sie unter [Integration mit Adobe Campaign](/help/sites-administering/campaign.md).

1. Wählen Sie im Aktivitätsmenü entweder **Erlebnis-Targeting** oder **A/B-Test** aus.

   * Erlebnis-Targeting – Verwalten Sie Adobe Target-Aktivitäten in AEM.
   * A/B-Test – Erstellen und verwalten Sie A/B-Testaktivitäten für Adobe Target in AEM.

## Der Targeting-Prozess: Erstellen, Targeting, Ziele und Einstellungen {#the-targeting-process-create-target-and-goals-settings}

Im Targeting-Modus haben Sie die Möglichkeit, verschiedene Aspekte von Aktivitäten zu konfigurieren. Folgen Sie den unten stehenden drei Schritten, um Targeting-Inhalte für Markenaktivitäten zu erstellen:

1. [Erstellen](#create-authoring-the-experiences): Sie können Erlebnisse hinzufügen oder entfernen und jedem Erlebnis Angebote hinzufügen.
1. [Ziel](#diagramtargetconfiguringtheaudiences): Geben Sie die Zielgruppe an, an die sich die jeweiligen Erlebnisse richten. Sie können bestimmte Zielgruppen ansprechen und mittels A/B-Tests bestimmen, welcher Anteil des Traffics an welches Erlebnis weitergeleitet wird.
1. [Ziele und Einstellungen](#settingsgoalssettingsconfiguringtheactivityandsettinggoals): Planen Sie die Aktivität und legen Sie Prioritäten fest. Außerdem lassen sich auch Ziele für Erfolgsmetriken bestimmen.

Gehen Sie wie folgt vor, um mit dem Inhalts-Targeting einer Aktivität zu beginnen.

>[!NOTE]
>
>Um den Targeting-Prozess zu verwenden, müssen Sie Mitglied der Benutzergruppe Target Activity Authors sein.

So fügen Sie eine Aktivität hinzu:

1. Wählen Sie aus dem Dropdown-Menü **Marke** diejenige Marke aus, die die zu bearbeitende Aktivität enthält.
1. Wählen Sie aus dem Dropdown-Menü **Aktivität** diejenige Aktivität aus, für die zielgerichtete Inhalte verfasst werden sollen.
1. Möchten Sie die Steuerungen einblenden, mit denen Sie durch das Targeting-Verfahren navigieren können, klicken oder tippen Sie auf **Targeting starten**.

   ![chlimage_1-11](assets/chlimage_1-11.png)

   >[!NOTE]
   >
   >Möchten Sie die Aktivität bearbeiten, mit der Sie sich aktuell befassen, klicken oder tippen Sie auf **Zurück**.

## Erstellen: Verfassen der Erlebnisse {#create-authoring-the-experiences}

Im Erstellungsschritt des Inhalts-Targetings werden Erlebnisse geschaffen. Während dieses Schrittes lassen sich Erlebnisse für Aktivitäten erstellen oder löschen sowie Angebote hinzufügen.

### Anzeigen von Erlebnisangeboten im Targeting-Modus {#seeing-experience-offers-in-targeting-mode}

Wählen Sie nach [Beginn des Targeting-Verfahrens](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) ein Erlebnis aus, um die ihm zugeordneten Angebote anzuzeigen. Bei der Auswahl eines Erlebnisses ändern sich die auf der Seite angezeigten Targeting-Komponenten so, dass das Angebot des Erlebnisses angezeigt wird.

>[!CAUTION]
>
>Gehen Sie beim Deaktivieren des Targetings für eine Komponente mit Bedacht vor, wenn für diese bereits in der Autoreninstanz Targeting durchgeführt wurde. Die entsprechende Aktivität wird auch automatisch aus der Veröffentlichungsinstanz gelöscht.

>[!NOTE]
>
>Angebote sind die Inhalte von Targeting-Komponenten.

Erlebnisse werden im Zielgruppenbereich angezeigt. In the following example, experiences include **Default**, **Female**, **Female over 30**, and **Female under 30**. In diesem Beispiel wird das Standardangebot einer Targeting-**Bild**-Komponente dargestellt.

![chlimage_1-12](assets/chlimage_1-12.png)

Bei Auswahl eines anderen Erlebnisses wird in der Bild-Komponente das Angebot des entsprechenden Erlebnisses gezeigt.

![chlimage_1-13](assets/chlimage_1-13.png)

Wurde ein Erlebnis ausgewählt und erhält die Targeting-Komponente kein Angebot für dieses Erlebnis, wird in der Komponente über dem halbtransparenten Standardangebot die Option **Angebot hinzufügen** angezeigt. Wurde für ein Erlebnis kein Angebot erstellt, wird das **Standardangebot** für das Segment angezeigt, das dem Erlebnis zugeordnet wurde.

![chlimage_1-14](assets/chlimage_1-14.png)

Das Standardereignis wird ebenfalls angezeigt, wenn die Besuchereigenschaften nicht mit Erlebnissen zugeordneten Segmenten übereinstimmen. See [Adding Experiences using Targeting Mode](#adding-and-removing-experiences-using-targeting-mode).

### Individuelle Angebote und Bibliotheksangebote {#custom-offers-and-library-offers}

Angebote, die [auf der Seite verfasst](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) und nur für ein einziges Erlebnis verwendet werden, werden als individuelle Angebote bezeichnet. Das folgende Bild wurde über dem Inhalt eines individuellen Angebots platziert:

![chlimage_1-15](assets/chlimage_1-15.png)

Angebote, die [aus einer Angebotsbibliothek hinzugefügt werden](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library), werden mit dem folgenden Bild platziert:

![chlimage_1-16](assets/chlimage_1-16.png)

Individuelle Angebote können in einer Angebotsbibliothek gespeichert werden, falls Sie sich dazu entscheiden, sie erneut zu verwenden. Sie können Bibliotheksangebote andererseits auch in individuelle Angebote umwandeln, wenn Sie den Inhalt eines Erlebnisses bearbeiten. Im Anschluss an die Bearbeitung kann das Angebot dann erneut in der Bibliothek gespeichert werden. 

### Hinzufügen und Entfernen von Erlebnissen im Targeting-Modus {#adding-and-removing-experiences-using-targeting-mode}

Im Erstellungsschritt des [Targeting-Verfahrens](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) können Sie Inhalte hinzufügen und entfernen. Darüber hinaus können Sie ein Erlebnis kopieren und es umbenennen.

#### Hinzufügen von Erlebnissen im Targeting-Modus {#adding-experiences-using-targeting-mode}

So fügen Sie Erlebnisse hinzu:

1. To add an experience, click or tap **+** **Add Experience Targeting** that appears below existing experiences in the **Audiences** pane.
1. Wählen Sie eine Zielgruppe aus. Standardmäßig wird der Name des Erlebnisses übernommen. Falls gewünscht, können Sie jedoch auch einen anderen Namen eingeben. Klicken oder tippen Sie auf **OK**.

#### Erlebnisse im Targeting-Modus entfernen {#removing-experiences-using-targeting-mode}

So löschen Sie Erlebnisse:

1. Klicken Sie auf den Pfeil neben dem Namen des Erlebnisses oder tippen Sie darauf.

   ![chlimage_1-17](assets/chlimage_1-17.png)

1. Klicken Sie auf **Löschen**.

#### Umbenennen von Erlebnissen im Targeting-Modus {#renaming-experiences-using-targeting-mode}

So benennen Sie Erlebnisse im Targeting-Modus um:

1. Klicken Sie auf den Pfeil neben dem Namen des Erlebnisses oder tippen Sie darauf.
1. Click **Rename Experience** and type in the new name.
1. Klicken oder tippen Sie auf eine andere Stelle auf dem Bildschirm, um die Änderungen zu speichern.

#### Bearbeiten von Zielgruppen im Targeting-Modus {#editing-audiences-using-targeting-mode}

So bearbeiten Sie im Targeting-Modus Zielgruppen:

1. Klicken Sie auf den Pfeil neben dem Namen des Erlebnisses oder tippen Sie darauf.
1. Click **Edit Audience** and select a new audience.
1. Klicken Sie auf **OK**.

#### Duplizieren von Erlebnissen im Targeting-Modus {#duplicating-experiences-using-targeting-mode}

So duplizieren Sie Erlebnisse im Targeting-Modus:

1. Klicken Sie auf den Pfeil neben dem Namen des Erlebnisses oder tippen Sie darauf.
1. Klicken Sie auf **Duplizieren** und wählen Sie die Zielgruppe aus.
1. Benennen Sie das Erlebnis, falls gewünscht, um und klicken Sie auf **OK**.

### Erstellen von Angeboten im Targeting-Modus {#creating-offers-using-targeting-mode}

Erstellen Sie mit Komponenten-Targeting Angebote für Ihre Erlebnisse. Mit Targeting-Komponenten lassen sich Inhalte bereitstellen, die als Angebote für Erlebnisse genutzt werden können.

* [Führen Sie Targeting einer bestehenden Komponente durch](/help/sites-authoring/content-targeting-touch.md#creating-a-default-offer-by-targeting-an-existing-component). Der Inhalt dieser Komponente wird dann zum Angebot für das Standarderlebnis.
* [Fügen Sie eine Target-Komponente hinzu](/help/sites-authoring/content-targeting-touch.md#creating-an-offer-by-adding-a-target-component) und versehen Sie diese anschließend mit Inhalt.

Nach dem Targeting der Komponente können für jedes Erlebnis Angebote hinzugefügt werden:

* [Fügen Sie kundenspezifische Angebote hinzu](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer).
* [Fügen Sie Angebote aus einer Bibliothek hinzu](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library).

Für die Arbeit mit Angeboten stehen Ihnen folgende Werkzeuge zur Verfügung:

* [Fügen Sie kundenspezifische Angebote einer Angebotsbibliothek hinzu](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library).
* [Wandeln Sie ein Bibliotheksangebot in ein kundenspezifisches Angebot um](/help/sites-authoring/content-targeting-touch.md#converting-a-library-offer-to-a-custom-library).
* [Öffnen Sie ein Bibliotheksangebot und bearbeiten Sie den Inhalt](/help/sites-authoring/content-targeting-touch.md#editing-a-library-offer).

#### Erstellen von Standardangeboten durch Targeting bestehender Komponenten {#creating-a-default-offer-by-targeting-an-existing-component}

Führen Sie Targeting einer Komponente auf Ihrer Seite durch, um die Komponente als Angebot für das Standarderlebnis der Aktivität einzustellen. Beim Targeting einer Komponente wird diese in eine Target-Komponente eingeschlossen und ihr Inhalt wird zum Inhalt des Standarderlebnisses gemacht.

Beim Targeting einer Komponente kann nur diese Komponente für das Angebot verwendet werden. Die Komponente kann nicht aus dem Angebot entfernt und keine weitere Komponente dem Angebot hinzugefügt werden.

Gehen Sie folgendermaßen vor, wenn Sie mit dem [Targeting begonnen haben](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings).

1. Klicken oder tippen Sie auf die Komponente, deren Targeting Sie durchführen möchten. Es wird die Symbolleiste der Komponente eingeblendet, die der hier gezeigten Leiste ähnelt.

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Klicken oder tippen Sie auf das Target-Symbol.

   ![](do-not-localize/chlimage_1.png)

   Der Komponenteninhalt ist das Angebot für das Standarderlebnis. Beim Festlegen einer Komponente wird der zugehörige Standardknoten für jedes Erlebnis repliziert. Dies ist zum Modifizieren des richtigen Inhaltsknotens beim erlebnisspezifischen Bearbeiten erforderlich. For these non-default experiences, either [add a custom offer](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) or [add a library offer](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library).

#### Erstellen eines Angebots durch Hinzufügen einer Target-Komponente {#creating-an-offer-by-adding-a-target-component}

Fügen Sie eine Target-Komponente hinzu, um ein Angebot für das Standarderlebnis zu erstellen. Bei der Target-Komponente handelt es sich um einen Container für andere Komponenten. Komponenten, die in diesem Container platziert werden, werden zu Targeting-Komponenten. Sollten Sie die Targeting-Komponente verwenden, können Sie ein Angebot durch Hinzufügen mehrerer Komponenten erstellen. Außerdem können Sie für jedes Erlebnis verschiedene Komponenten verwenden, um unterschiedliche Angebote zu erstellen.

See [Configuring Target component options](/help/sites-authoring/content-targeting-touch.md#configuring-target-component-options) for information on customizing this component.

>[!NOTE]
>
>Offers that you create using the [Offers console](/help/sites-authoring/offerlib.md) can also contain several components. Diese Angebote gehören zu einer Angebotsbibliothek und lassen sich für mehrere Erlebnisse einsetzen.

Da es sich bei der Target-Komponente um einen Container handelt, wird diese als Ablagebereich für andere Komponenten dargestellt.

Im Targeting-Modus wird die Target-Komponente mit blauem Rahmen dargestellt und die Ablagezielnachricht kennzeichnet Komponenten mit Targeting.

![chlimage_1-19](assets/chlimage_1-19.png)

Im Bearbeitungsmodus wird die Target-Komponente mit Zielscheibensymbol dargestellt.

![](do-not-localize/chlimage_1-1.png)

Ziehen Sie Komponenten in die Target-Komponente, werden diese zu Targeting-Komponenten.

![chlimage_1-20](assets/chlimage_1-20.png)

Fügen Sie der Target-Komponente eine Komponente hinzu, stellt diese Inhalte für ein bestimmtes Erlebnis bereit. Zur Festlegung des Erlebnisses müssen Sie dieses vor dem Hinzufügen der Komponenten auswählen.

Sie können eine Target-Komponente sowohl im Bearbeitungs- als auch im Targeting-Modus zur Seite hinzufügen. Sie können jedoch nur im Targeting-Modus Komponenten zur Target-Komponente hinzufügen. Die Target-Komponente ist Teil der Personalisierungs-Komponentengruppe.

Möchten Sie Targeting-Inhalte bearbeiten, müssen Sie zunächst auf **Targeting starten** tippen oder klicken.

1. Ziehen Sie die Target-Komponente auf die Seite, auf der das Angebot angezeigt werden soll.
1. Standardmäßig ist keine Orts-ID festgelegt. Klicken oder tippen Sie auf das Zahnrad (Konfiguration), um den Ort festzulegen.

   >[!NOTE]
   >
   >Wenn Sie von Ihrem Administrator festgelegt werden, müssen Sie den Speicherort eventuell explizit festlegen.
   >
   >
   >Administrators can decide whether setting this configuration is required at **https://&lt;host>:&lt;port>/system/console/configMgr/com.day.cq.personalization.impl.servlets.TargetingConfigurationServlet**
   Wenn Benutzer einen Ort eingeben müssen, aktivieren Sie das Kontrollkästchen **Position erzwingen **s.

1. Wählen Sie das Erlebnis aus, für das ein Angebot erstellt werden soll.
1. So erstellen Sie das Angebot:

   * Ziehen Sie für das Standarderlebnis Komponenten in den zielgerichteten Ablagebereich und bearbeiten Sie die Komponenteneigenschaften wie gewohnt, um den Inhalt für das Angebot zu erstellen.
   * Ereignissen, die nicht dem Standardereignis entsprechen, können Sie entweder [individuelle Angebote](#adding-a-custom-offer) oder [Bibliotheksangebote](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) hinzufügen.

#### Hinzufügen individueller Angebote {#adding-a-custom-offer}

Erstellen Sie ein Angebot, indem Sie den Inhalt einer Targeting-Komponente im Targeting-Modus bearbeiten. Wenn Sie ein individuelles Angebot erstellen, wird dieses als Angebot für ein bestimmtes, einzelnes Erlebnis verwendet.

If you decide that the offer can be used for other experiences, you can create a custom offer and [add it to the library](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library). Weitere Informationen zur Verwendung der Angebotskonsole für die Erstellung wiederverwendbarer Angebote finden Sie unter [Hinzufügen von Angeboten zu Angebotsbibliotheken](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library).

1. Wählen Sie das Erlebnis aus, dem das Angebot hinzugefügt werden soll.
1. Möchten Sie das Komponentenmenü einblenden, klicken oder tippen Sie auf die Targeting-Komponente, der das Angebot hinzugefügt wird.

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Klicken oder tippen Sie auf das Plus-Zeichen (+).

   Der Inhalt des Standardangebots wird als Angebot des aktuellen Erlebnisses genutzt.

1. Klicken oder tippen Sie auf das Angebot, um das Angebotsmenü einzublenden, und klicken oder tippen Sie auf die Bearbeitungsschaltfläche.

   ![](do-not-localize/chlimage_1-2.png)

1. Bearbeiten Sie den Inhalt der Komponente.

#### Hinzufügen eines Angebots aus einer Angebotsbibliothek {#adding-an-offer-from-an-offer-library}

Add an offer from the [offer library](/help/sites-authoring/offerlib.md) to an experience. Sie können beliebige Angebote aus der Bibliothek der Marke auswählen, die Sie derzeit bearbeiten.

Dem Standarderlebnis lassen sich keine Bibliotheksangebote hinzufügen.

1. Wählen Sie das Erlebnis aus, dem das Angebot hinzugefügt werden soll.
1. Möchten Sie das Komponentenmenü einblenden, klicken oder tippen Sie auf die Targeting-Komponente, der das Angebot hinzugefügt wird.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Klicken oder tippen Sie auf das Ordnersymbol.

   ![](do-not-localize/chlimage_1-3.png)

1. Wählen Sie das gewünschte Angebot aus der Bibliothek aus und klicken oder tippen Sie auf das entsprechende Häkchen.

   ![chlimage_1-23](assets/chlimage_1-23.png)

   Mit der Angebotswahl können Sie die Angebote durchsuchen oder filtern. Beim Durchsuchen oder Filtern der Angebote können diese zudem sortiert und deren Anzeige angepasst werden. Die oben rechts gezeigte Zahl gibt an, wie viele Angebote in der aktuellen Bibliothek verfügbar sind.

   * Click or tap **Browse** to navigate to another folder. Es öffnet sich ein Navigationsfenster, in dem Sie durch Klicken auf die Pfeile tiefer in die Ordnerstruktur vordringen können. Click or tap **Browse** again to close the navigation pane.
   ![chlimage_1-24](assets/chlimage_1-24.png)

   * Klicken oder tippen Sie auf **Filter**, um die Angebote nach Stichwörtern oder Tags zu filtern. Stichwörter werden manuell eingegeben, während sich Tags aus dem entsprechenden Dropdown-Menü auswählen lassen. Klicken oder tippen Sie erneut auf **Filter**, um das Filterfenster zu schließen.
   ![chlimage_1-25](assets/chlimage_1-25.png)

   * Durch Klicken oder Tippen auf den Pfeil neben **Von neu nach alt** können Sie anpassen, wie die Angebote sortiert werden sollen. Angebote können von neu nach alt oder von alt nach neu sortiert werden.
   ![chlimage_1-26](assets/chlimage_1-26.png)

   Klicken oder tippen Sie auf das Symbol neben **Anzeigen als**, um Angebote als Kacheln oder Liste anzuzeigen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

#### Adding a Custom Offer to a Library {#adding-a-custom-offer-to-a-library}

Fügen Sie ein individuelles Angebot der [Angebotsbibliothek](/help/sites-authoring/offerlib.md) hinzu, wenn Sie es für weitere Erlebnisse einsetzen möchten. Sie können Angebote der Bibliothek derjenigen Marke hinzufügen, deren Targeting Sie gerade bearbeiten.

Weitere Informationen zur Verwendung der Angebotskonsole für die Erstellung wiederverwendbarer Angebote finden Sie unter [Hinzufügen von Angeboten zu Angebotsbibliotheken](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library).

1. Wählen Sie das gewünschte Erlebnis aus, um das individuelle Angebot anzuzeigen.
1. Klicken oder tippen Sie auf das individuelle Angebot, um das Angebotsmenü einzublenden, und klicken oder tippen Sie auf das Symbol **Angebot in Angebotsbibliothek speichern**.

   ![](do-not-localize/chlimage_1-4.png)

1. Geben Sie einen Angebotsnamen ein und wählen Sie die Bibliothek aus, der das Angebot hinzugefügt werden soll. Klicken oder tippen Sie abschließend auf das Häkchen.

#### Umwandeln von Bibliotheksangeboten in individuelle Angebote {#converting-a-library-offer-to-a-custom-library}

Wandeln Sie ein Bibliotheksangebot in ein individuelles Angebot um, um das Angebot des aktuellen Erlebnisses zu ändern, ohne dass sich hierbei die Angebote anderer Erlebnisse ändern.

1. Wählen Sie das Erlebnis aus, um das Bibliotheksangebot anzuzeigen.
1. Klicken oder tippen Sie auf das Bibliotheksangebot, um das Angebotsmenü einzublenden, und klicken oder tippen Sie auf das Symbol „In Inline-Angebot konvertieren“.

   ![](do-not-localize/chlimage_1-5.png)

#### Überarbeiten eines Bibliothekangebots {#editing-a-library-offer}

Öffnen Sie im Targeting-Modus das Bibliotheksangebot eines Erlebnisses, um dieses zu bearbeiten. Die von Ihnen vorgenommenen Änderungen werden von allen Erlebnissen übernommen, die dieses Angebot nutzen.

1. Wählen Sie das Erlebnis aus, um das Bibliotheksangebot anzuzeigen.
1. Wandeln Sie das Bibliotheksangebot in ein lokales/individuelles Angebot um. See [Converting a Library Offer to a Custom Library](#converting-a-library-offer-to-a-custom-library).
1. Bearbeiten Sie den Inhalt des Angebots.

1. Speichern Sie es erneut in der Bibliothek. See [Adding a Custom Offer to a Library](#adding-a-custom-offer-to-a-library).

## Target: Konfigurieren der Zielgruppen {#target-configuring-the-audiences}

Im Target-Schritt des [Targeting-Verfahrens](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) werden Zielgruppen mit den Erlebnissen verknüpft, die Sie während des Erstellungsschritts bearbeitet haben. Auf der Target-Seite sind die Zielgruppen aufgeführt, die durch das Erlebnis angesprochen werden sollen. Sie können die Zielgruppen für jedes Erlebnis festlegen und ändern. Sollten Sie mit Adobe Target arbeiten, können Sie zudem A/B-Tests erstellen, die es Ihnen ermöglichen, einen bestimmten Anteil des Traffics einer Zielgruppe auf ein bestimmtes Erlebnis umzuleiten.

### Wenn Sie AEM-Targeting oder Adobe Target (Erlebnis-Targeting) verwenden... {#if-you-are-using-aem-targeting-or-adobe-target-experience-targeting}

werden Zielgruppen auf der linken Seite des Zuordnungsdiagramms angezeigt, Erlebnisse auf der rechten Seite.

![chlimage_1-28](assets/chlimage_1-28.png)

Legen Sie mithilfe eines Segments eine Zielgruppe fest. Durch die Cloud-Konfiguration auf der Seite wird bestimmt, welche Segmente Ihnen zur Verfügung stehen. Wurde die Seite nicht mit einer Adobe Target-Cloud-Konfiguration verknüpft, stehen für die Definition der Zielgruppen AEM-Segmente zur Verfügung. Wurde die Seite hingegen mit einer Adobe Target-Cloud-Konfiguration verknüpft, werden Target-Segmente verwendet.

Weitere Informationen zu Targeting-Engines finden Sie unter [Targeting-Engine](/help/sites-authoring/personalization.md#targeting-engine).

Eine Zielgruppe darf nicht mehr als einem Erlebnis zugewiesen werden. Wenn ein Erlebnis einer Zielgruppe zugewiesen wird, die mit einem anderen Erlebnis verknüpft ist, erscheint neben dem Erlebnis ein Warnsymbol.

![](do-not-localize/chlimage_1-6.png)

### Verknüpfen von Erlebnissen und Zielgruppen (AEM oder Adobe Target) {#associating-experiences-with-audiences-aem-or-adobe-target}

Gehen Sie wie folgt vor, um in AEM Targeting (oder dem Erlebnis-Targeting von Adobe Target) Erlebnissen entsprechende Zielgruppen zuzuweisen:

1. Klicken oder tippen Sie auf den Pfeil des Dropdown-Menüs neben dem Zielgruppenfeld, das dem Erlebnis zugeordnet ist.
1. (Optional) Click or tap **Edit** and then type a keyword to search for the desired segment.
1. Wählen Sie aus der Zielgruppenliste die gewünschte aus und klicken oder tippen Sie auf **OK**.

### Wenn Sie A/B-Tests (Adobe Target) verwenden… {#if-you-are-using-a-b-testing-adobe-target}

befinden sich – sollten Sie über eine A/B-Testaktivität verfügen – die Zielgruppen links, der Anteil der Besucher, der auf das Erlebnis umgeleitet wird, in der Mitte und die Erlebnisse selbst rechts.

Sie können die Prozentwerte beliebig anpassen, solange sie in der Summe 100 % ergeben. Zielgruppen dürfen in A/B-Tests mehreren Erlebnissen zugewiesen werden.

![chlimage_1-29](assets/chlimage_1-29.png)

### Zielgruppen in A/B-Tests Traffic-Anteilen zuordnen {#associating-audiences-and-traffic-percentages-with-a-b-testing}

1. Klicken oder tippen Sie auf das Dropdown-Feld neben der Zielgruppe, die dem Erlebnis zugeordnet ist.
1. (Optional) Klicken Sie auf **Bearbeiten** und geben Sie ein Stichwort ein, um nach dem gewünschten Segment zu suchen.
1. Klicken oder tippen Sie auf **OK.**
1. Geben Sie die Prozentsätze ein, nach denen der Zielgruppen-Traffic auf die verschiedenen Erlebnisse aufgeteilt werden soll. Ihre Summe muss 100 ergeben.
1. (Optional) Bearbeiten Sie den Erlebnisnamen, indem Sie daneben auf das Dropdown-Menü klicken.

## Ziele und Einstellungen: Konfigurieren der Aktivität und Festlegen von Zielen {#goals-settings-configuring-the-activity-and-setting-goals}

The Goals &amp; Settings step of [the targeting process](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) involves configuring the behavior of the brand activity. Legen Sie hier fest, wann die Aktivität beginnt und endet und über welche Priorität sie verfügt. Des Weiteren können Sie auch Ziele verfolgen. Sie können insbesondere festlegen, welche Metriken mit Ihren Aktivitäten gemessen werden sollen.

Zielmetriken sind nur verfügbar, wenn Sie Adobe Target als Targeting-Engine einsetzen. Sie müssen mindestens eine Zielmetrik definieren. Sollte Adobe Analytics konfiguriert sein und sollten Sie über eine A4T Analytics-Cloud-Konfiguration verfügen, können Sie als Quelle der Berichtserstellung Adobe Target oder Adobe Analytics festlegen.

Zielmetriken werden nur für veröffentlichte Kampagnen gemessen.

Sollten Sie AEM als Targeting-Engine verwenden:

![chlimage_1-30](assets/chlimage_1-30.png)

Sollten Sie Adobe Target als Targeting-Engine verwenden:

![chlimage_1-31](assets/chlimage_1-31.png)

Verwenden Sie Adobe Target als Targeting-Engine und wurde A4T Analytics für das Konto konfiguriert, wird Ihnen ein zusätzliches Dropdown-Menü für die **Berichtsquelle** angezeigt:

![chlimage_1-32](assets/chlimage_1-32.png)

Es sind folgende Erfolgsmetriken verfügbar (nur für die Veröffentlichung einsetzbar):

<table>
 <tbody>
  <tr>
   <td><strong>Konversion</strong></td>
   <td><p>Die Prozentzahl der Besucher, die auf einen beliebigen Teil des getesteten Erlebnisses geklickt haben. Eine Konversion kann entweder einmal pro Besucher oder jedes Mal, wenn ein Besucher eine Umrechnung durchführt, gezählt werden. Die Konversionsmetrik ist auf einen der folgenden Werte eingestellt:</p>
    <ul>
     <li><strong>Ansicht einer Seite</strong> - Sie können festlegen, welche Seite die Zielgruppe angezeigt hat, indem Sie entweder die <strong>URL auswählen</strong> und dann die URL oder mehrere URLs definieren oder indem Sie die <strong>URL enthält</strong> und dann einen Pfad oder einen Suchbegriff hinzufügen.</li>
     <li><strong>Mbox angezeigt</strong> – Sie können festlegen, welche Mbox Ihre Zielgruppe angezeigt haben muss, indem Sie deren Namen eingeben. Durch Klicken auf <strong>Mbox hinzufügen</strong> können Sie mehrere Mboxes bestimmen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Umsatz</strong></td>
   <td><p>Durch den Besuch generierter Umsatz. Sie können aus den folgenden Umsatzmetriken auswählen:</p>
    <ul>
     <li>Umsatz pro Besucher (RPV)</li>
     <li>Durchschnittlicher Bestellwert</li>
     <li>Gesamtverkäufe </li>
     <li>Aufträge</li>
    </ul> <p>Sie können bei all diesen Optionen bestimmen, ob das Anzeigen einer Mbox bedeutet, dass das Ziel erreicht wurde. Es können eine oder mehrere Mboxes festgelegt werden.</p> </td>
  </tr>
  <tr>
   <td><strong>Einsatz</strong></td>
   <td><p>Es können drei Interaktionsarten erfasst werden:</p>
    <ul>
     <li>Seitenansichten</li>
     <li>Individuelle Bewertung</li>
     <li>Besuchszeit pro Site</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Darüber hinaus gibt es erweiterte Einstellungen, in denen Sie festlegen können, wie Erfolgsmetriken gemessen werden. Die Optionen umfassen das Zählen der Metrik pro Anzeige oder pro Besucher sowie die Wahl, ob Benutzer in der Aktivität bleiben können oder entfernt werden.

Verwenden Sie die erweiterten Optionen, um festzulegen, was geschehen soll, **wenn** ein Benutzer die Sollmetrik vorfindet. In der folgenden Tabelle finden Sie die verfügbaren Optionen.

<table>
 <tbody>
  <tr>
   <td><strong>Ein Benutzer findet diese Sollmetrik vor...</strong></td>
   <td><strong>Sie wählen folgende Aktionen aus...</strong></td>
  </tr>
  <tr>
   <td><strong>Anzahl erhöhen und Benutzer in Aktivität belassen</strong></td>
   <td>Geben Sie an, wie die Anzahl erhöht wird:
    <ul>
     <li>Einmal pro Teilnehmer</li>
     <li>Bei jeder Impression außer Seitenaktualisierungen</li>
     <li>Bei jeder Impression</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anzahl erhöhen, Benutzer freigeben und Wiedereintritt erlauben</strong></td>
   <td>Wählen Sie das Erlebnis aus, das dem Besucher angezeigt wird, wenn er die Aktivität erneut aufruft:
    <ul>
     <li>Gleiches Erlebnis</li>
     <li>Zufälliges Erlebnis</li>
     <li>Unsichtbares Erlebnis</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Anzahl erhöhen, Benutzer freigeben und an Wiedereintritt hindern</strong></td>
   <td>Bestimmen Sie, was der Benutzer anstelle des Aktivitätsinhalts sieht:
    <ul>
     <li>Gleiches Erlebnis ohne Verfolgung</li>
     <li>Standardinhalt oder Inhalt einer anderen Aktivität</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Weitere Informationen zu Erfolgsmetriken finden Sie in der [Adobe Target-Dokumentation](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html).

### Konfigurieren von Einstellungen (AEM Targeting) {#configuring-settings-aem-targeting}

So werden die Einstellungen für AEM-Targeting konfiguriert:

1. Verwenden Sie das Dropdown-Menü **Start**, um festzulegen, wann die Aktivität beginnen soll. Wählen Sie einen der folgenden Werte aus:

   * **Ist diese Option aktiviert**, beginnt die Aktivität, sobald die Seite aktiviert wird, auf der sich der Targeting-Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wurde diese Option ausgewählt, klicken oder tippen Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Uhrzeit an, zu der die Aktivität online gehen soll.

1. Verwenden Sie das Dropdown-Menü **Ende**, um festzulegen, wann die Aktivität beendet werden soll. Wählen Sie einen der folgenden Werte aus:

   * **Ist diese Option deaktiviert**, endet die Aktivität, sobald die Seite deaktiviert wird, auf der sich der zielgerichtete Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wurde diese Option ausgewählt, klicken oder tippen Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Uhrzeit an, zu der die Aktivität beendet werden soll.

1. Soll die Aktivität eine Priorität erhalten, wählen Sie mit dem Schieberegler entweder **Niedrig**, **Normal** oder **Hoch** aus.

### Konfigurieren von Zielen und Einstellungen (Adobe Target) {#configuring-goals-settings-adobe-target}

So konfigurieren Sie bei Verwendung von Adobe Target Ziele und Einstellungen:

1. Verwenden Sie das Dropdown-Menü **Start**, um festzulegen, wann die Aktivität beginnen soll. Wählen Sie einen der folgenden Werte aus:

   * **Ist diese Option aktiviert**, beginnt die Aktivität, sobald die Seite aktiviert wird, auf der sich der Targeting-Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wurde diese Option ausgewählt, klicken oder tippen Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Uhrzeit an, zu der die Aktivität online gehen soll.

1. Verwenden Sie das Dropdown-Menü **Ende**, um festzulegen, wann die Aktivität beendet werden soll. Wählen Sie einen der folgenden Werte aus:

   * **Ist diese Option deaktiviert**, endet die Aktivität, sobald die Seite deaktiviert wird, auf der sich der zielgerichtete Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wurde diese Option ausgewählt, klicken oder tippen Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Uhrzeit an, zu der die Aktivität beendet werden soll.

1. Soll die Aktivität eine Priorität erhalten, wählen Sie mit dem Schieberegler entweder **Niedrig**, **Normal** oder **Hoch** aus.
1. Sollten Sie Adobe Anaytics über Ihr Adobe Target-Konto konfiguriert haben, wird Ihnen zusätzlich das Dropdown-Menü **Berichtsquelle** angezeigt. Wählen Sie **Adobe Target** oder **Adobe Analytics** als Quelle aus.

   Sollten Sie sich für **Adobe Analytics** entscheiden, wählen Sie Organisation und Report Suite aus. Sollten Sie **Adobe Target** auswählen, muss keine weitere Auswahl getroffen werden.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Wählen Sie im Bereich **Zielmetrik** unter dem Punkt **Mein Primärziel** die zu verfolgende Erfolgsmetrik – Konversionen, Umsatz, Interaktion – aus und geben Sie an, wie die Metrik gemessen werden soll (oder welche Aktion die Zielgruppe ausführen muss, damit das Ziel als erreicht bewertet wird). Definitionen der Zielmetriken in der oben stehenden Tabelle finden Sie in der [Adobe Target-Dokumentation](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html) unter dem Abschnitt zu Erfolgsmetriken.

   You can rename the goal by clicking the three dots in the upper right corner and selecting **Rename**.

   Möchten Sie die Inhalte aller Felder löschen, klicken Sie auf die drei Punkte oben rechts und wählen Sie **Alle Felder löschen** aus.

   Sämtliche Metriken verfügen zudem über von Ihnen festlegbare erweiterte Einstellungen. Diese finden Sie unter der Option **Erweiterte Einstellungen**. See definition of how success metrics are counted in previous table and see [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html).

   >[!NOTE]
   Sie müssen mindestens eine Zielmetrik definieren.

   ![chlimage_1-34](assets/chlimage_1-34.png)

   >[!NOTE]
   Sollten Daten Ihrer Metrik fehlen, wird die zugehörige Metrik rot umrandet.

1. Klicken Sie auf **Neue Metrik hinzufügen**, um weitere Erfolgsmetriken zu konfigurieren.

   ![chlimage_1-35](assets/chlimage_1-35.png)

   >[!NOTE]
   Sie können andere Ziele entfernen, indem Sie entweder auf die drei Punkte oder auf **Löschen** klicken oder tippen. In AEM muss mindestens eine Zielmetrik definiert werden.

1. If you want more control over how success metrics are counted, click or tap **Advanced Settings** to access those.
1. Klicken Sie auf **Speichern**.

Nach abgeschlossener Konfiguration können Sie die [Leistung der Aktivitäten](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test) anzeigen, die Adobe Target verwenden (Erlebnis-Targeting oder A/B-Tests). Bei A/B-Tests können Sie zusätzlich [die Gewinner konvertieren.](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test)

## Simulieren eines Erlebnisses {#simulating-an-experience}

Sie können Besuchererlebnisse simulieren, um sicherzustellen, dass die Seiteninhalte entsprechend dem Design der zielgerichteten Inhalte dargestellt werden. Beim Simulieren können Sie verschiedene Benutzerprofile laden und die jeweiligen zielgerichteten Inhalte anzeigen.

Die folgenden Kriterien bestimmen den Inhalt, der bei der Simulation des Besuchererlebnisses angezeigt wird:

* Die Daten im Sitzungs-Store des Benutzers (über ContextHub).
* Die [aktivierten Aktivitäten](/help/sites-authoring/activitylib.md).
* Die [Regeln, die die Segmente definieren](/help/sites-administering/campaign-segmentation.md).
* Der Inhalt der Erlebnisse in den Target-Komponenten.
* Die [Konfiguration der Targeting-Engine](/help/sites-authoring/activitylib.md).

Sollte auf der Seite unerwarteter Inhalt angezeigt werden, wenn Sie ein Profil laden, prüfen Sie die Konfiguration aller hier aufgeführter Elemente.

>[!NOTE]
Sollten Sie mit A/B-Tests arbeiten, basieren die Simulationen der Erlebnisse auf dem Traffic-Anteil. Dieser wird durch Adobe Target gesteuert, was für Autoren zu unerwarteten Ergebnissen führen kann. (Die Aktivität „_author“ wird mit bestimmten Eigenschaften synchronisiert, die während der Simulation eine Neubewertung ermöglichen.) Möglicherweise müssen Autoren die Seite aktualisieren, um andere auf Traffic-Einstellungen basierende Erlebnisse anzeigen zu können.

Mit den folgenden Werkzeugen lassen sich Besuchererlebnisse simulieren:

* Simulation der Aktivität im Targeting-Modus: Auf der Seite werden die Angebote angezeigt, die dem aktuell im ContextHub ausgewählten Benutzer zugeordnet sind. Sie können die Angebote bearbeiten, die auf den Benutzer zugeschnitten sind.
* Vorschaumodus: Wählen Sie in ContextHub die Benutzer und Orte aus, die die Kriterien derjenigen Segmente erfüllen, auf denen Ihre Erlebnisse aufbauen. Sollten sich Ihre ContextHub-Auswahlen ändern, ändern sich dementsprechend auch die zielgerichteten Inhalte.

1. To switch to Preview mode, on the toolbar click or tap **Preview**.
1. Klicken Sie in der Symbolleiste auf das ContextHub-Symbol.

   ![](do-not-localize/chlimage_1-7.png)

1. Verwenden Sie ContextHub, um die Kontexteigenschaften zu bearbeiten. Klicken oder tippen Sie beispielsweise auf Personeneigenschaften, um einen anderen Benutzer auszuwählen.

   ![chlimage_1-36](assets/chlimage_1-36.png)

   Die Seite ändert sich entsprechend und gibt nun die Inhalte wieder, die für den aktuellen Kontext erstellt wurden.

1. Möchten Sie Änderungen an den angezeigten Angeboten vornehmen, wechseln Sie in den Targeting-Modus. Bearbeiten Sie die ausgewählte, zuvor simulierte Aktivität und deren Angebote für den Kontext, der im Vorschaumodus konfiguriert wurde.

## Konfigurieren der Target-Komponentenoptionen {#configuring-target-component-options}

Sie können die Komponente „Target“ anpassen, indem Sie auf eine von zwei möglichen Arten auf die Komponentenoptionen zugreifen:

1. Klicken oder tippen Sie nach abgeschlossenem Targeting der Komponente auf die Komponente und dann auf das Einstellungssymbol (Zahnrad).

   ![](do-not-localize/chlimage_1-8.png)

   Sodann zeigt AEM das Fenster mit den Target-Optionen an.

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. Alternativ können Sie auf diese Einstellungen auch im Vollbildmodus zugreifen: Klicken oder tippen Sie im Optionsfenster der Target-Komponente auf das Vollbildsymbol.

   ![](do-not-localize/chlimage_1-9.png)

   AEM zeigt die Target-Komponentenoptionen daraufhin im Vollbildmodus an.

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Konfigurieren Sie die Einstellungen der Target-Komponente, wie in den folgenden Tabellen beschrieben.

<table>
 <tbody>
  <tr>
   <td><strong>Wahl</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Standort</strong></td>
   <td><p>Der Speicherort ist ein String, der den Ortsnamen des Targeting-Inhalts enthält und Angebote mit Orten (oder Orte und Komponenten) auf der Seite verknüpft, auf der diese Angebote platziert werden sollen.</p> <p>Bei diesem Feld handelt es sich um einen allgemeinen Wert.</p> <p>Platzieren Sie ein Angebot in einer Komponente, wird die Orts-ID in der Komponente gespeichert. Bei Ausführung der Seite beurteilt die Engine die Besuchersegmente und bestimmt auf dieser Basis die Erlebnisse der aktiven Kampagnen, die dem Besucher angezeigt werden sollen. Anschließend werden die Orts-IDs auf der Seite geprüft und Angebote mit den entsprechenden IDs gesucht.</p> </td>
  </tr>
  <tr>
   <td><strong>Engine</strong></td>
   <td>Select between <strong>Client side Rules (without tracking), Adobe Target, ContextHub, </strong>and<strong> Adobe Campaign </strong>depending on which engine you would like to use.</td>
  </tr>
 </tbody>
</table>

Wenn Sie Adobe Target als Engine auswählen:

![chlimage_1-39](assets/chlimage_1-39.png)

<table>
 <tbody>
  <tr>
   <td><strong>Wahl</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Präzise Zielgruppenerfassung</strong></td>
   <td><p>Durch Aktivierung der genauen Verfolgung wird der Komponente mitgeteilt, auf verfügbare Client Context- oder Context-Hub-Daten zu warten, bevor eine Anfrage an Adobe Target gesendet wird. Dies kann die Ladezeit verlängern. Beim Verfassen ist stets die präzise Zielgruppenerfassung aktiviert.</p> <p>Wenn Sie das Kontrollkästchen <strong>Präzise Zielgruppenerfassung</strong> aktivieren, führt die Mbox zunächst <code>mboxDefine</code> und anschließend <code>mboxUpdate</code> durch, was bei Verfügbarkeit der Daten zu einer Ajax-Anfrage führt.</p> <p>If you do not select the <strong>Accurate targeting</strong> check box, the mbox performs an <code>mboxCreate</code> resulting in a synchronous request right away (in this case, not all context data may be available yet).</p> <p><strong>Hinweis:</strong> Das Aktivieren und Deaktivieren der präzisen Zielgruppenerfassung einer Komponente wirkt sich nicht auf globale Einstellungen aus. Globale Einstellungen lassen sich jederzeit außer Kraft setzen, indem Sie die präzise Zielgruppenerfassung in der Komponente aktivieren.</p> </td>
  </tr>
  <tr>
   <td><strong>Gelöste Segmente einschließen</strong></td>
   <td><p>Aktivieren Sie dieses Kontrollkästchen, werden alle bestimmten Segmente im Mbox-Aufruf sowie in beliebigen auf der Seite konfigurierten Parametern und im Framework erfasst.</p> <p>Dies funktioniert bei XML-APIs nur, wenn AEM-Segmente synchronisiert werden. Wenn Sie über Segmente in AEM verfügen, die nicht von Adobe Target verwaltet werden (beispielsweise Skriptsegmente), ermöglicht es Ihnen diese Option, das Segment in AEM auszuwählen und Adobe Target darüber zu informieren, dass das Segment aktiv ist.</p> </td>
  </tr>
  <tr>
   <td><strong>Übernommene Kontextparameter</strong></td>
   <td>Listenkontextparameter, die (falls vorhanden) vom Adobe Target-Framework übernommen und mit der ausgewählten Seite verknüpft werden.</td>
  </tr>
  <tr>
   <td><strong>Kontextparameter</strong></td>
   <td>Click or tap <strong>Add field</strong> to configure additional context parameters (same as what is available in Target framework). Kontextparameter, die der Komponente hinzugefügt wurden, gelten <i>nur</i> für die gewählte Komponente, nicht für andere Komponenten, wie dies der Fall wäre, wenn Kontextparameter direkt dem Framework hinzugefügt würden.</td>
  </tr>
  <tr>
   <td><strong>Statische Parameter</strong></td>
   <td>Click or tap <strong>Add field</strong> to configure additional static parameters (same as what is available in Target framework). Static parameters added to the component apply <i>only</i> to the component and not to other component as would be the case if you added static parameters directly to the framework. Statische Parameter stammen nicht aus dem Kontext (Client Context des ContentHub).</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
Wählen Sie eine Komponente aus und ermöglichen Sie deren Targeting, wird die Komponente auch von AEM ersetzt und eine Adobe Target-Komponente eingebettet. (Die Adobe Target-Komponente wird nicht nur dann verwendet, wenn Sie sie manuell auf der Seite einfügen, sondern auch dann, wenn Sie das Targeting einer vorhandenen Komponente durchführen.)

Wenn Sie Client Context (Client-Seite) als Engine auswählen:

![chlimage_1-40](assets/chlimage_1-40.png)

<table>
 <tbody>
  <tr>
   <td><strong>Wahl</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Optionen für Client-Seite – Strategie</strong></td>
   <td><p>Wählen Sie eines der folgenden Elemente aus:</p>
    <ul>
     <li><strong>Erste(r)</strong>: das laut Sortierung der Kampagne an erster Stelle stehende Erlebnis.</li>
     <li><strong>Zufällig</strong>: Es wird ein beliebiges Erlebnis verwendet.</li>
     <li><strong>Clickstream-Ergebnis</strong>: Die Tags und zugehörigen Tag-Treffer, die im Clientkontext verfolgt werden, werden verwendet. Die Trefferraten für Tags, die auf der Teaser-Seite definiert sind, werden verglichen.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Wählen Sie **Adobe Campaign** als Engine aus, wenn Sie AEM mit Adobe Campaign integrieren. Weitere Informationen finden Sie unter [Integration von AEM mit Adobe Campaign](/help/sites-administering/campaign.md).

Wählen Sie **ContextHub** als Engine aus, wenn Sie ContextHub für das Targeting verwenden. Weitere Informationen finden Sie unter [Konfigurieren von ContextHub.](/help/sites-administering/contexthub-config.md)

