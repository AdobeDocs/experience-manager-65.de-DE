---
title: Verwalten von Inhaltsfragmenten
seo-title: Verwalten von Inhaltsfragmenten
description: Inhaltsfragmente werden als Assets gespeichert und daher hauptsächlich über die Assets-Konsole verwaltet.
seo-description: Inhaltsfragmente werden als Assets gespeichert und daher hauptsächlich über die Assets-Konsole verwaltet.
uuid: 675e1a6b-2583-488f-bbb4-210daed3e1b0
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: 21a18d60-f3fe-4048-9949-8416b5cb4596
docset: aem65
translation-type: tm+mt
source-git-commit: 9cab3284e8aab996363da7eaa7c5a175044d9592

---


# Verwalten von Inhaltsfragmenten{#managing-content-fragments}

Inhaltsfragmente werden als **Assets** gespeichert und daher hauptsächlich über die **Assets-Konsole** verwaltet.

>[!NOTE]
>
>Inhaltsfragmente werden dann für erstellte Seiten verwendet. Weitere Informationen finden Sie unter [Seitenerstellung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md).

## Erstellen von Inhaltsfragmenten {#creating-content-fragments}

### Erstellen von Inhaltsmodellen {#creating-a-content-model}

[Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md) können vor dem Erstellen von Inhaltsfragmenten mit strukturiertem Inhalt aktiviert und erstellt werden.

>[!NOTE]
>
>Weitere Informationen zu für einfache Inhaltsfragmente verwendeten Vorlagen finden Sie unter [Entwickeln von Inhaltsfragmenten](/help/sites-developing/customizing-content-fragments.md).

### Erstellen eines Inhaltsfragments {#creating-a-content-fragment}

Die Methode zum Erstellen eines Inhaltsmodells ist (im Grunde genommen) bei einfachen und strukturierten Fragmenten gleich:

1. Navigieren Sie in den Ordner **Assets**, in dem Sie das Fragment erstellen möchten.
1. Wählen Sie **Erstellen** und danach **Inhaltsfragment** aus, um den Assistenten zu öffnen.
1. Im ersten Schritt des Assistenten müssen Sie die Grundlage für das neue Fragment festlegen.

   * Dabei kann es sich um Folgendes handeln:

      * [Vorlage](/help/sites-developing/content-fragment-templates.md) – beispielsweise **Einfaches Fragment**

      * [Modell](/help/assets/content-fragments-models.md) – wird verwendet, um ein Fragment zu erstellen, für das strukturierte Inhalte erforderlich sind; beispielsweise das **Flughafen**-Modell
   * Es werden alle verfügbaren Vorlagen und Modelle angezeigt.
   Wählen Sie **Weiter** aus, wenn Sie Ihre Auswahl getroffen haben.

   ![cfm-6420-15](assets/cfm-6420-15.png)

1. In the **Properties** step specify:

   * **Einfach**

      * **Titel**

         Der Fragmenttitel.

         Obligatorisch.

      * **Beschreibung**

      * **Tags**
   * **Erweitert**

      * **Name**

         Der Name, der für die URL verwendet wird.

         Obligatorisch. Wird automatisch aus dem Titel abgeleitet, kann jedoch aktualisiert werden.


1. Wählen Sie **Erstellen** aus, um den Vorgang abzuschließen, und **öffnen** Sie das Fragment zur Bearbeitung oder wechseln Sie über **Fertig** wieder zur Konsole.

## Aktionen für ein Inhaltsfragment {#actions-for-a-content-fragment}

In der **Assets-Konsole** können Sie eine Reihe von Aktionen für Ihre Inhaltsfragmente vornehmen, die Sie wie folgt erreichen:

* Über die Symbolleiste – nachdem Sie das Fragment ausgewählt haben, sind alle geeigneten Aktionen verfügbar.
* Als [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions) – ein Teil der Aktionen, die für die individuellen Fragmentkarten verfügbar sind.

![cfm-6420-17](assets/cfm-6420-17.png)

Wählen Sie das Fragment aus, um die Symbolleiste mit entsprechenden Aktionen anzuzeigen:

* **Download**

   * Speichern Sie das Fragment als ZIP-Datei. Sie können festlegen, ob die betreffenden Elemente, Varianten und Metadaten enthalten sein sollen.

* **Erstellen**
* **Auschecken**
* **Eigenschaften**

   * Ermöglicht das Anzeigen bzw. Bearbeiten der Metadaten des Fragments.

* **Bearbeiten**

   * Allows you to [open the fragment for editing content](/help/assets/content-fragments-variations.md) together with its elements, variations, associated content and metadata.

* **Tags verwalten**
* **Zu Sammlung**

   * Fügen Sie das Fragment einer Sammlung hinzu.
   * Dies können Sie auch erreichen, wenn Sie [eine Sammlung mit dem Fragment verknüpfen](/help/assets/content-fragments-assoc-content.md#adding-associated-content).

* **Kopieren**/**Einfügen**

* **Verschieben**
* **Quick Publish**
* **Veröffentlichung verwalten**
* **Löschen**

>[!NOTE]
>
>Many of these are [standard actions for Assets](/help/assets/managing-assets-touch-ui.md) and/or the [AEM desktop app](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

## Öffnen des Fragment-Editors {#opening-the-fragment-editor}

So öffnen Sie ein Fragment zur Bearbeitung:

>[!CAUTION]
>
>Um ein Inhaltsfragment zu bearbeiten, benötigen Sie [die entsprechenden Berechtigungen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

1. Navigieren Sie in der Konsole **Assets** zum Speicherort des gewünschten Inhaltsfragments.
1. Öffnen Sie das Fragment zur Bearbeitung. Befolgen Sie dazu einen der folgenden Schritte: 

   * Klicken/tippen Sie auf das Fragment oder den Fragmentlink (abhängig von der Konsolenansicht).
   * Selecting the fragment, then **Edit** from the toolbar.
   Der Fragment-Editor wird geöffnet: 

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Eine Meldung wird angezeigt, wenn auf einer Inhaltsseite bereits auf das Fragment verwiesen wird.
      >
      >
      >

   2. The side panel can be hidden/shown using the **Toggle Side Panel** icon.


1. Navigieren Sie mit den Symbolen im seitlichen Bedienfeld durch die drei Modi:

   * Varianten: [Bearbeiten des Inhalts](#editing-the-content-of-your-fragment) und [Verwalten Ihrer Varianten](#creating-and-managing-variations-within-your-fragment)

   * [Anmerkungen](/help/assets/content-fragments-variations.md#annotating-a-content-fragment)
   * [Zugehörige Inhalte](#associating-content-with-your-fragment)
   * [Metadaten](#viewing-and-editing-the-metadata-properties-of-your-fragment)
   ![cfm-10](assets/cfm-10.png)

1. Wenn Sie Ihre Änderungen vorgenommen haben, verwenden Sie je nach Bedarf entweder **Speichern** oder **Abbrechen**. 

   >[!NOTE]
   >
   >Sowohl die Option **Speichern** als auch **Abbrechen** beendet den Editor – vollständige Informationen über die Auswirkung beider Optionen auf Inhaltsfragmente finden Sie unter [Speichern, Abbrechen und Versionen](#save-cancel-and-versions). 

## Speichern, Abbrechen und Versionen  {#save-cancel-and-versions}

>[!NOTE]
>
>Versionen können [über die Timeline auch erstellt, verglichen und zurückgesetzt werden](/help/assets/content-fragments-managing.md#timeline-for-content-fragments).

Der Editor bietet zwei Optionen: 

* **Speichern**

   Die aktuellen Änderungen werden gespeichert und der Editor wird beendet. 

   >[!CAUTION]
   >
   >Um ein Inhaltsfragment zu bearbeiten, benötigen Sie [die entsprechenden Berechtigungen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

   >[!NOTE]
   >
   >Es ist möglich, im Fragment-Editor zu bleiben und vor Auswahl von **Speichern** eine Reihe von Änderungen vorzunehmen. 

   >[!CAUTION]
   >
   >Die Option **Speichern** speichert nicht nur einfach Ihre Änderungen, sondern aktualisiert auch alle Verweise und stellt sicher, dass der Dispatcher nach Bedarf geleert wird.  Es kann einige Zeit dauern, bis diese Änderungen verarbeitet werden.  Aus diesem Grund kann die Leistung eines umfassenden/komplexen/stark belasteten Systems beeinträchtigt werden. 
   >
   >
   >Beachten Sie das, wenn Sie die Option **Speichern** auswählen und den Fragment-Editor danach schnell erneut aufrufen, um weitere Änderungen vorzunehmen und zu speichern. 

* **Abbrechen**

   Der Editor wird beendet und die letzten Änderungen werden nicht gespeichert. 

Beim Bearbeiten Ihres Inhaltsfragments erstellt AEM automatisch Versionen, damit ältere Inhalte wiederhergestellt werden können, falls Sie Ihre Änderungen über **Abbrechen** verwerfen: 

1. When a content fragment is opened for editing AEM checks for the existence of the cookie-based token that indicates whether an *editing session* exists:

   1. Wird das entsprechende Token gefunden, gilt das Fragment als Teil der vorhandenen Bearbeitungssitzung.
   2. Wenn das Token *nicht* verfügbar ist und der Benutzer mit dem Bearbeiten von Inhalt beginnt, wird eine Version erstellt, und ein Token für diese neue Bearbeitungssitzung wird an den Client gesendet, wo er in einem Cookie gespeichert wird.

2. Während einer *aktiven* Bearbeitungssitzung wird der bearbeitete Inhalt automatisch alle 600 Sekunden gespeichert (Standardeinstellung).

   >[!NOTE]
   >
   >The auto save interval is configurable using the `/conf` mechanism.
   >
   >
   >Den Standardwert finden Sie unter: 
   >
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. If the user selects to **Cancel** the edit, the version created at the start of the editing session is restored and the token is removed to end the editing session.
4. If the user selects to **Save** the edits, the updated elements/variations are persisted and the token is removed to end the editing session.

## Bearbeiten des Inhalts Ihres Fragments {#editing-the-content-of-your-fragment}

Wenn Sie das Fragment geöffnet haben, können Sie die Registerkarte [Varianten](/help/assets/content-fragments-variations.md) verwenden, um Ihren Inhalt zu erstellen.

## Erstellen und Verwalten von Varianten innerhalb Ihres Fragments {#creating-and-managing-variations-within-your-fragment}

Sobald Sie den Master-Inhalt erstellt haben, können Sie [Varianten](/help/assets/content-fragments-variations.md) dieses Inhalts erstellen und verwalten.

## Verknüpfen von Inhalt mit Ihrem Fragment {#associating-content-with-your-fragment}

Sie können auch Inhalt mit einem Fragment [verknüpfen](/help/assets/content-fragments-assoc-content.md). So entsteht eine Verbindung, mit der Assets (d. h. Bilder) für ein Fragment verwendet werden können (falls gewünscht), wenn sie zu einer Inhaltsseite hinzugefügt werden.

## Anzeigen und Bearbeiten von Metadaten (Eigenschaften) des Fragments {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Sie können die Eigenschaften eines Fragments über die Registerkarte [Metadaten](/help/assets/content-fragments-metadata.md) anzeigen und bearbeiten.

## Timeline für Inhaltsfragmente {#timeline-for-content-fragments}

Neben den Standardoptionen enthält die [Timeline](/help/assets/managing-assets-touch-ui.md#timeline) Informationen und Aktionen für Inhaltsfragmente.

* Anzeigen von Informationen zu Versionen, Kommentaren und Anmerkungen
* Aktionen für Versionen

   * **[Auf diese Version zurücksetzen](#reverting-to-a-version)**(ein vorhandenes Fragment und eine bestimmte Version auswählen)

   * **[Mit aktueller Version vergleichen](#comparing-fragment-versions)**(ein vorhandenes Fragment und eine bestimmte Version auswählen)

   * **Beschriftung** und/oder **Kommentar** hinzufügen (ein vorhandenes Fragment und eine bestimmte Version auswählen)

   * **Als Version speichern** (ein vorhandenes Fragment und dann den Pfeil nach oben am unteren Rand der Timeline auswählen)

* Aktionen für Anmerkungen

   * **Löschen**

>[!NOTE]
>
>Kommentare sind:
>
>* Standardfunktionen für alle Assets
>* In der Timeline erstellt worden
>* Mit dem Fragment-Asset verbunden
>
>
Anmerkungen (für Inhaltsfragmente) sind:
>
>* Im Fragment-Editor eingegeben worden
>* Spezifisch für ein ausgewähltes Textsegment innerhalb des Fragments
>



Beispiel:

![cfm-6420-19-2019](assets/cfm-6420-19-2019.png)

## Vergleichen von Fragment-Versionen {#comparing-fragment-versions}

Die Aktion **Mit aktueller Version vergleichen** ist in der [Timeline](/help/assets/content-fragments-managing.md#timeline-for-content-fragments) verfügbar, sobald Sie eine bestimmte Version ausgewählt haben.

Folgendes wird geöffnet:

* die **aktuelle** (neueste) Version (links)

* die ausgewählte Version **v&lt;*x.y*>** (rechts)

Sie werden nebeneinander angezeigt:

* Unterschiede werden hervorgehoben

   * Gelöschter Text: Rot
   * Eingefügter Text: Grün 
   * Ersetzter Text: Blau

* Über das Vollbildsymbol können Sie jede Version separat öffnen. Wechseln Sie dann wieder zur parallelen Ansicht.
* Sie können die jeweilige Version **wiederherstellen**.
* Über **Fertig** kehren Sie zur Konsole zurück.

>[!NOTE]
>
>Sie können den Fragmentinhalt nicht bearbeiten, während Sie Fragmente vergleichen.

![cfm-6420-20](assets/cfm-6420-20.png)

## Wiederherstellen einer früheren Version  {#reverting-to-a-version}

Sie können eine frühere Version wiederherstellen.

* Direkt über die [Timeline](/help/assets/content-fragments-managing.md#timeline-for-content-fragments).

   Wählen Sie die gewünschte Version und dann die Aktion **Auf diese Version zurücksetzen** aus.

* Beim [Vergleichen einer Version mit der aktuellen Version](/help/assets/content-fragments-managing.md#comparing-fragment-versions) können Sie die ausgewählte Version **wiederherstellen**.

## Veröffentlichen und Referenzieren von Fragmenten {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Wenn das Fragment auf einem Modell basiert, sollten Sie sicherstellen, dass das [Modell veröffentlicht wurde](/help/assets/content-fragments-models.md#publishing-a-content-fragment-model).
>
>Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

Inhaltsfragmente müssen veröffentlicht werden, um in der Veröffentlichungsumgebung genutzt werden zu können. Sie können folgendermaßen veröffentlicht werden:

* Nach der Erstellung in der Konsole **Assets**.
* Wenn Sie [eine Seite veröffentlichen, in der das Fragment verwendet wird](/help/sites-authoring/content-fragments.md#publishing), wird das Fragment in den Seitenverweisen aufgeführt. 

>[!CAUTION]
>
>Nachdem ein Fragment veröffentlicht und/oder referenziert wurde, zeigt AEM eine Warnmeldung an, wenn ein Autor das Fragment erneut zur Bearbeitung öffnet. Dies dient als Hinweis darauf, dass am Fragment vorgenommene Änderungen sich auch auf die referenzierte Seite auswirken.

## Löschen von Fragmenten {#deleting-a-fragment}

So löschen Sie ein Fragment:

1. Navigieren Sie in der Konsole **Assets** zum Speicherort des Inhaltsfragments.
2. Wählen Sie das Fragment aus.

   >[!NOTE]
   >
   >Die Aktion **Löschen** ist nicht als Schnellzugriff verfügbar.

3. Wählen Sie **Löschen** in der Symbolleiste aus.
4. Bestätigen Sie die **Löschaktion**.

   >[!CAUTION]
   >
   >If the fragment is already referenced in a page you will then see a warning message and be required to confirm that you want to proceed with a **Force Delete**. Das Fragment wird zusammen mit seiner Inhaltsfragmentkomponente aus allen Inhaltsseiten gelöscht.

