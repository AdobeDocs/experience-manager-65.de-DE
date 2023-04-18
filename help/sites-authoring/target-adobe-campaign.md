---
title: Targeting Ihrer Adobe Campaign
description: Sie können zielgerichtete Erlebnisse für Adobe Campaign erstellen, nachdem Sie die Segmentierung eingerichtet haben.
uuid: 8fcc9210-d8c5-44e3-8aa8-6c6db810c98e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f1cb5e98-ccd1-4b2c-acca-2b3cc1b7ac5f
exl-id: fc6fccba-41c5-4c13-aac0-b4ef67767abe
source-git-commit: f4b6eb2ded17ec641f23a1fc3b977ce77169c8a1
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 45%

---

# Zielgruppenbestimmung für Adobe Campaign{#targeting-your-adobe-campaign}

Um Ihren Adobe Campaign-Newsletter als Ziel festzulegen, müssen Sie zunächst die Segmentierung einrichten, die nur in der klassischen Benutzeroberfläche verfügbar ist (für Client Context). Danach können Sie zielgerichtete Erlebnisse für Adobe Campaign erstellen. Beide werden in diesem Abschnitt beschrieben.

## Einrichten der Segmentierung in AEM {#setting-up-segmentation-in-aem}

Um die Segmentierung einzurichten, müssen Sie die Segmente über die klassische Benutzeroberfläche einrichten. Die verbleibenden Schritte können in der Standardbenutzeroberfläche ausgeführt werden.

Im Rahmen des Einrichtens der Segmentierung werden Segmente erstellt sowie eine Marke, Kampagne und Erlebnisse erstellt.

>[!NOTE]
>
>Die Segment-ID muss einer ID in Adobe Campaign zugewiesen werden.

### Erstellen von Segmenten {#creating-segments}

So erstellen Sie Segmente:

1. Öffnen Sie die [Segmentierungskonsole](http://localhost:4502/miscadmin#/etc/segmentation) unter **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Erstellen Sie eine neue Seite, geben Sie einen Namen ein (beispielsweise **AC-Segmente**) und wählen Sie die Vorlage **Segment (Adobe Campaign)** aus.
1. Wählen Sie die erstellte Seite in der Baumansicht auf der linken Seite aus.
1. Erstellen Sie ein Segment, z. B. für männliche Benutzer, indem Sie eine neue Seite unter dem von Ihnen erstellten Segment namens Männlich erstellen und wählen Sie die **Segment (Adobe Campaign)** Vorlage.
1. Öffnen Sie die erstellte Segmentseite und ziehen Sie eine **Segment-ID** aus dem Sidekick auf die Seite.
1. Doppelklicken Sie auf das Merkmal, geben Sie die zugewiesene ID des männlichen Segments in Adobe Campaign ein (beispielsweise **MÄNNLICH**) und klicken Sie auf **OK**. Die folgende Meldung sollte angezeigt werden: *`targetData.segmentCode == "MALE"`*
1. Wiederholen Sie die Schritte für ein anderes Segment, z. B. ein Segment, das auf weibliche Benutzer ausgerichtet ist.

### Erstellen einer Marke {#creating-a-brand}

So erstellen Sie eine Marke:

1. Navigieren Sie unter **Sites** zum Ordner **Kampagnen** (beispielsweise We.Retail).
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für die Seite an (beispielsweise We.Retail-Marke) und wählen Sie die Vorlage **Marke** aus.

### Erstellen einer Kampagne {#creating-a-campaign}

So erstellen Sie eine Kampagne:

1. Öffnen Sie die **Marke** Seite, die Sie gerade erstellt haben.
1. Klicken **Seite erstellen** und geben Sie einen Titel für Ihre Seite ein, z. B. We.Retail Campaign, und wählen Sie die **Kampagne** Vorlage und klicken Sie auf **Erstellen**.

### Erstellen von Erlebnissen {#creating-experiences}

So erstellen Sie Erlebnisse für Segmente:

1. Öffnen Sie die Seite **Kampagne**, die Sie soeben erstellt haben.
1. Erstellen Sie Erlebnisse für Ihre Segmente, indem Sie auf **Seite erstellen** klicken, und geben Sie einen Titel für Ihre Seite ein, z. B. „Männlich“, wenn Sie ein Erlebnis für das Segment „Männlich“ erstellen, und wählen Sie dann die Vorlage **Erlebnis** aus.
1. Öffnen Sie die erstellte Erlebnisseite.
1. Klicken Sie auf **Bearbeiten** und unterhalb der Segmente auf **Element hinzufügen**.
1. Geben Sie den Pfad zum männlichen Segment ein (beispielsweise **/etc/segmentation/ac-segments/male**) und klicken Sie auf **OK**. Es wird folgende Meldung angezeigt: *Erlebnis ist ausgerichtet auf: Männlich*.
1. Wiederholen Sie die vorherigen Schritte, um ein Erlebnis für alle Segmente zu erstellen, z. B. für die weibliche Zielgruppe.

## Erstellen eines Newsletters mit zielgerichteten Inhalten {#creating-a-newsletter-with-targeted-content}

Nachdem Sie Segmente, eine Marke, eine Kampagne und ein Erlebnis erstellt haben, können Sie einen Newsletter mit zielgerichteten Inhalten erstellen. Nachdem Sie das Erlebnis erstellt haben, verknüpfen Sie Erlebnisse mit Ihren Segmenten.

>[!NOTE]
>
>[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

So erstellen Sie einen Newsletter mit zielgerichtetem Inhalt:

1. Erstellen Sie einen Newsletter mit zielgerichtetem Inhalt: Klicken oder tippen Sie unterhalb der E-Mail-Kampagnen von Geometrixx Outdoors auf **Erstellen** > **Seite** und wählen eine der Adobe Campaign-E-Mail-Vorlagen aus.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Fügen Sie dem Newsletter eine Text- und Personalisierungs-Komponente hinzu.
1. Fügen Sie der Text- und Personalisierungs-Komponente Text hinzu, beispielsweise: „Dies ist der Standardtext.“
1. Klicken Sie auf den Pfeil neben **Bearbeiten** und wählen Sie **Targeting** aus.
1. Wählen Sie Ihre Marke aus dem Dropdown-Menü Marke aus und wählen Sie Ihre Kampagne aus. (Dies ist die Marke und Kampagne, die Sie zuvor erstellt haben).
1. Klicken Sie auf **Targeting starten**. Die Segmente werden nun im Zielgruppenbereich angezeigt. Sollte ein Besucher nicht in eines der festgelegten Segmente passen, wird er zum Standarderlebnis weitergeleitet.

   >[!NOTE]
   >
   >Standardmäßig werden die in AEM enthaltenen E-Mail-Beispiele als Targeting-Engine für Adobe Campaign verwendet. Bei benutzerdefinierten Newslettern müssen Sie möglicherweise Adobe Campaign als Targeting-Engine auswählen. Tippen oder klicken Sie beim Targeting in der Symbolleiste auf +, geben Sie einen Titel für die neue Aktivität ein und wählen Sie **Adobe Campaign** als Targeting-Engine.

1. Klicken **Standard** und dann die Komponente Text und Personalisierung , die Sie hinzugefügt haben, und das Bullseye mit einem Pfeil darin sehen. Klicken Sie auf das Symbol, um diese Komponente als Ziel festzulegen.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Navigieren Sie zu einem anderen Segment („Männlich“), klicken Sie auf **Angebot hinzufügen** und klicken Sie auf das Pluszeichen (+). Bearbeiten Sie anschließend das Angebot.
1. Navigieren Sie zu einem anderen Segment (Weiblich) und klicken Sie auf **Angebot hinzufügen** und das Pluszeichen +. Bearbeiten Sie dann dieses Angebot.
1. Klicken Sie auf **Weiter**, um die Zuordnung anzuzeigen, und klicken Sie dann auf **Weiter**, um die Einstellungen anzuzeigen, die nicht für Adobe Campaign gelten, und klicken Sie auf **Speichern**.

   AEM generiert automatisch den richtigen Targeting-Code für Adobe Campaign, wenn der Inhalt in einem Versand innerhalb von Adobe Campaign verwendet wird

1. Erstellen Sie in Adobe Campaign Ihren Versand - wählen Sie **E-Mail-Versand mit AEM Inhalt** und wählen Sie gegebenenfalls das lokale AEM-Konto aus und bestätigen Sie Ihre Änderungen.

   In der HTML-Ansicht sind die verschiedenen Erlebnisse der Targeting-Komponenten im Adobe Campaign-Targeting-Code eingeschlossen.

   ![chlimage_1-190](assets/chlimage_1-190.png)

   >[!NOTE]
   >
   >Sollten Sie die Segmente auch in Adobe Campaign eingerichtet haben, werden Ihnen beim Klick auf **Vorschau** die Erlebnisse der unterschiedlichen Segmente angezeigt.
