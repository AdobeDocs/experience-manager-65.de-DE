---
title: Targeting von Adobe Campaign
seo-title: Targeting von Adobe Campaign
description: Im Rahmen der Einrichtung der Segmentierung werden Segmente erstellt sowie eine Marke, Kampagne und Erlebnisse eingerichtet.
seo-description: Im Rahmen der Einrichtung der Segmentierung werden Segmente erstellt sowie eine Marke, Kampagne und Erlebnisse eingerichtet.
uuid: 520cd006-0aa8-43f3-b754-efb7397bb92f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bbc2aac9-ccf1-40c3-be4f-d59c2d0d8a6c
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Targeting von Adobe Campaign{#targeting-your-adobe-campaign}

Möchten Sie ein Targeting Ihres Adobe Campaign-Newsletters durchführen, müssen Sie zunächst die Segmentierung einrichten, die nur in der klassischen Benutzeroberfläche zur Verfügung steht. Anschließend können Sie zielgerichtete Erlebnisse für Adobe Campaign erstellen.

## Einrichten der Segmentierung in AEM {#setting-up-segmentation-in-aem}

Im Rahmen der Einrichtung der Segmentierung werden Segmente erstellt sowie eine Marke, Kampagne und Erlebnisse eingerichtet. Sie können ein Segment nur über die klassische Benutzeroberfläche erstellen. Sie können Marken, Kampagnen und Erlebnisse in der touchfähigen Benutzeroberfläche erstellen.

>[!NOTE]
>
>Die Segment-ID muss einer ID in Adobe Campaign zugewiesen werden.

### Erstellen von Segmenten {#creating-segments}

So erstellen Sie Segmente:

1. Open the [segmentation console](http://localhost:4502/miscadmin#/etc/segmentation) at **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Create a new page and enter a title - for example, **AC Segments** - and select the **Segment (Adobe Campaign)** template.
1. Wählen Sie in der Baumansicht links die erstellte Seite aus.
1. Erstellen Sie ein Segment, mit dem beispielsweise männliche Benutzer angesprochen werden, indem Sie im soeben erstellten Segment eine Seite mit dem Titel „Männlich“ erstellen und die Vorlage **Segment (Adobe Campaign)** auswählen.
1. Öffnen Sie die erstellte Seite und ziehen Sie eine **Segment-ID** aus dem Sidekick auf die Seite.
1. Double-click the trait, enter the ID representing in this case, the male segment defined in Adobe Campaign - for example, **MALE** - and click **OK**. Die folgende Meldung sollte angezeigt werden: `targetData.segmentCode == "MALE"`
1. Wiederholen Sie diese Schritte für ein weiteres Segment, beispielsweise eines, mit dem weibliche Benutzer angesprochen werden.

### Erstellen neuer Marken {#creating-a-brand}

So erstellen Sie eine Marke:

1. Navigieren Sie unter **Sites** zum Ordner **Kampagnen** (beispielsweise We.Retail).
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für die Seite an (beispielsweise We.Retail-Marke) und wählen Sie die Vorlage **Marke** aus.

### Erstellen einer Kampagne {#creating-a-campaign}

So erstellen Sie eine Kampagne:

1. Öffnen Sie die Seite **Marke**, die Sie soeben erstellt haben.
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für Ihre Seite an (beispielsweise We.Retail-Kampagne), wählen Sie die Vorlage **Kampagne** aus und klicken Sie auf **Erstellen**.

### Erstellen von Erlebnissen {#creating-experiences}

So erstellen Sie Erlebnisse für Segmente:

1. Öffnen Sie die Seite **Kampagne**, die Sie soeben erstellt haben.
1. Create experiences for your segments by clicking **Create Page** and entering a title for your page, for example, Male as you are creating an experience for the Male segment, and select the **Experience** template.
1. Öffnen Sie die erstellte Erlebnisseite.
1. Klicken Sie auf **Bearbeiten** und unterhalb der Segmente auf **Element hinzufügen**.
1. Enter the path to the male segment, for example `/etc/segmentation/ac-segments/male` and click **OK**. The following message should appear: *Experience is targeted at: Male*
1. Wiederholen Sie die vorherigen Schritte, um ein Erlebnis für alle Segmente, beispielsweise ein weibliches, zu erstellen.

## Erstellen eines Newsletters mit zielgerichteten Inhalten {#creating-a-newsletter-with-targeted-content}

Nach der Erstellung von Segmenten, Marke, Kampagne und Erlebnissen können Sie einen Newsletter mit zielgerichtetem Inhalt erstellen. Nach Erstellung des Erlebnisses wird dieses mit Ihren Segmenten verknüpft.

Sie können den Newsletter mit zielgerichteten Inhalten sowohl in der touchfähigen als auch in der klassischen Benutzeroberfläche erstellen. In diesem Dokument wird das Verfahren für die touchfähige Benutzeroberfläche beschrieben.

So erstellen Sie einen Newsletter mit zielgerichtetem Inhalt:

1. Create a newsletter with targeted content: Below Email Campaigns in Geometrixx Outdoors, click or tap **Create** > **Page**, and select one of the Adobe Campaign Mail templates.

   >[!NOTE]
   >
   >[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md#weretail). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

1. Fügen Sie dem Newsletter eine Text- und Personalisierungs-Komponente hinzu.
1. Fügen Sie der Text- und Personalisierungs-Komponente Text hinzu, beispielsweise: „Dies ist der Standardtext.“
1. Click the arrow next to **Edit** and select **Targeting**.
1. Wählen Sie die entsprechende Marke aus dem Dropdown-Menü aus und klicken Sie auf Ihre Kampagne. (Hierbei handelt es sich um die Marke und Kampagne, die Sie zuvor erstellt haben).
1. Klicken Sie auf **Targeting starten**. Die Segmente werden nun im Zielgruppebereich angezeigt. Sollte ein Besucher nicht in eines der festgelegten Segmente passen, wird er zum Standarderlebnis weitergeleitet.

   >[!NOTE]
   >
   >Standardmäßig verwenden die in AEM enthaltenen E-Mail-Muster Adobe Campaign als Targeting-Engine. Bei benutzerdefinierten Newslettern müssen Sie möglicherweise Adobe Campaign als Targeting-Engine auswählen. Tippen oder klicken Sie während des Targetings in der Symbolleiste auf +, geben Sie einen Namen für die neue Aktivität ein und wählen Sie **Adobe Campaign** als Targeting-Engine aus.

1. Klicken Sie auf **Standard** und wählen Sie die Text- und Personalisierungs-Komponente aus, die Sie hinzugefügt haben. Es erscheint eine Zielscheibe mit darin steckendem Pfeil. Klicken Sie auf das Symbol, um das Targeting dieser Komponente zu starten.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Navigieren Sie zu einem anderen Segment („Männlich“), klicken Sie auf **Angebot hinzufügen** und klicken Sie auf das Pluszeichen (+). Bearbeiten Sie anschließend das Angebot.
1. Navigieren Sie zu einem anderen Segment („Weiblich“), klicken Sie auf **Angebot hinzufügen** und klicken Sie auf das Pluszeichen (+). Bearbeiten Sie anschließend dieses Angebot.
1. Click **Next** to see Mapping, then click **Next** to see Settings, which does not apply to Adobe Campaign, and click **Save**.

   AEM generiert automatisch den richtigen Targeting-Code für Adobe Campaign, wenn der Inhalt in Adobe Campaign für eine Bereitstellung genutzt wird.

1. Erstellen Sie in Adobe Campaign eine Bereitstellung: Klicken Sie auf **E-Mail-Bereitstellung mit AEM-Inhalten**, wählen Sie das passende lokale AEM-Konto aus und bestätigen Sie die Änderungen.

   In der HTML-Ansicht befinden sich die verschiedenen Erlebnisse der Targeting-Komponenten, die über Adobe Campaign-Targeting-Code verfügen.

   ![chlimage_1-166](assets/chlimage_1-166.png)

   >[!NOTE]
   >
   >Sollten Sie die Segmente auch in Adobe Campaign eingerichtet haben, werden Ihnen beim Klick auf **Vorschau** die Erlebnisse der unterschiedlichen Segmente angezeigt.

