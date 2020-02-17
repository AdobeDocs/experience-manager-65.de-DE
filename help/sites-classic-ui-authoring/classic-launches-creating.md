---
title: Erstellen von Launches
seo-title: Erstellen von Launches
description: Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Webseiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben.
seo-description: Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Webseiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben.
uuid: e67608a9-e6c9-42f3-bd1d-63a5fa87ae18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 48826f03-6731-49c5-a6c5-6e2fb718f912
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Erstellen von Launches{#creating-launches}

Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Webseiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben:

* The title appears in the **Sidekick**, from where authors can access them to work on them.
* Die untergeordneten Seiten der Quellseiten werden standardmäßig in den Launch eingeschlossen. Sie können bei Bedarf nur die Quellseite verwenden.
* Standardmäßig aktualisiert [Live Copy](/help/sites-administering/msm.md) automatisch die Launch-Seiten, wenn sich die Quellseiten ändern. Zur Vermeidung automatischer Änderungen können Sie festlegen, dass eine statische Kopie erstellt wird.

Optional können Sie das **Launch-Datum** (und die Uhrzeit) für die Bewerbung und Aktivierung der Launch-Seiten angeben. However the **Launch Date** only operates in combination with the **Production Ready** flag (see [Editing a Launch Configuration](/help/sites-classic-ui-authoring/classic-launches-editing.md#editing-a-launch-configuration)); for the actions to actually occur automatically, both must be set.

## Erstellen eines Launches {#creating-a-launch}

Der folgende Prozess erzeugt einen Launch.

1. Öffnen Sie die Verwaltungsseite für die Website ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)).
1. Klicken Sie auf **Neu…** gefolgt von **Neuer Launch…**.
1. Geben Sie im Dialogfeld **Launch erstellen** Werte für die folgenden Eigenschaften an:

   * **Launch-Titel**: Der Name des Launches. Der Name sollte für Autoren einen Sinn ergeben.
   * **Quellseite**: Der Pfad zu der Seite, für die der Launch erstellt werden soll. Standardmäßig sind alle untergeordneten Seiten eingeschlossen.
   * **Unterseiten ausschließen**: Wählen Sie diese Option aus, um den Launch nur für die Quellseite und nicht für die untergeordneten Seiten zu erstellen. Standardmäßig ist diese Option nicht aktiviert. 
   * **** Synchronisieren: Wählen Sie diese Option, um den Inhalt von Launch-Seiten automatisch zu aktualisieren, wenn die Quellseiten sich ändern. Dies wird erzielt, indem der Launch zu einer [Live Copy](/help/sites-administering/msm.md) gemacht wird.
   * **Launch-Datum**: Das Datum und die Uhrzeit für die Aktivierung der Launch-Kopie (abhängig von der Kennzeichnung **Produktionsbereit**. Siehe [Launches: Reihenfolge von Ereignissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).
   ![chlimage_1-99](assets/chlimage_1-99a.png)

1. Klicken Sie auf **Erstellen**.

## Löschen von Launches {#deleting-a-launch}

Sie können einen Launch auch löschen.

1. Wählen Sie den erforderlichen Launch in der [Launch-Konsole](/help/sites-classic-ui-authoring/classic-launches.md) aus.
1. Klicken Sie auf **Löschen**. Der Vorgang muss bestätigt werden:

   ![chlimage_1-100](assets/chlimage_1-100a.png)

   >[!CAUTION]
   >
   >Beim Löschen von verschachtelten Launches sollten Sie zuerst die niedrigeren Ebenen löschen.

