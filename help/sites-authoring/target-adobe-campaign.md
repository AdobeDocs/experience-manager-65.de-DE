---
title: Zielgruppenbestimmung für Adobe Campaign
description: Sie können zielgerichtete Erlebnisse für Adobe Campaign erstellen, nachdem Sie die Segmentierung eingerichtet haben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: fc6fccba-41c5-4c13-aac0-b4ef67767abe
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 76%

---

# Zielgruppenbestimmung für Adobe Campaign{#targeting-your-adobe-campaign}

Um Ihren Adobe Campaign-Newsletter gezielt einzusetzen, müssen Sie zunächst eine Segmentierung einrichten, was nur in der klassischen Benutzeroberfläche verfügbar ist (für den Client-Kontext). Anschließend können Sie zielgerichtete Erlebnisse für Adobe Campaign erstellen. Beides wird in diesem Abschnitt beschrieben.

## Einrichten der Segmentierung in AEM {#setting-up-segmentation-in-aem}

Um die Segmentierung einzurichten, müssen Sie mithilfe der klassischen Benutzeroberfläche Segmente einrichten. Die verbleibenden Schritte können in der Standardbenutzeroberfläche ausgeführt werden.

Im Rahmen des Einrichtens der Segmentierung werden Segmente erstellt sowie eine Marke, Kampagne und Erlebnisse erstellt.

>[!NOTE]
>
>Die Segment-ID muss einer ID in Adobe Campaign zugewiesen werden.

### Erstellen von Segmenten {#creating-segments}

So erstellen Sie Segmente:

1. Öffnen Sie die [Segmentierungskonsole](http://localhost:4502/miscadmin#/etc/segmentation) unter **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Erstellen Sie eine Seite und geben Sie einen Titel ein, beispielsweise **AC-Segmente**- und wählen Sie die **Segment (Adobe Campaign)** Vorlage.
1. Wählen Sie die erstellte Seite in der Strukturansicht auf der linken Seite aus.
1. Erstellen Sie ein Segment beispielsweise für männliche Benutzer, indem Sie eine Seite unter dem von Ihnen erstellten Segment namens Männlich erstellen und wählen Sie die **Segment (Adobe Campaign)** Vorlage.
1. Öffnen Sie die erstellte Segmentseite und ziehen Sie per Drag-and-Drop eine **Segment-ID** aus dem Sidekick auf die Seite.
1. Doppelklicken Sie auf das Merkmal, geben Sie die zugewiesene ID des männlichen Segments in Adobe Campaign ein (beispielsweise **MÄNNLICH**) und klicken Sie auf **OK**. Die folgende Meldung sollte angezeigt werden: *`targetData.segmentCode == "MALE"`*
1. Wiederholen Sie diese Schritte für ein weiteres Segment, beispielsweise eines, mit dem Benutzerinnen angesprochen werden.

### Erstellen einer Marke {#creating-a-brand}

So erstellen Sie eine Marke:

1. In **Sites**, navigieren Sie zum **Kampagnen** -Ordner (z. B. in We.Retail).
1. Klicks **Seite erstellen** und geben Sie einen Titel für die Seite ein, z. B. We.Retail Brand, und wählen Sie die **Marke** Vorlage.

### Erstellen einer Kampagne {#creating-a-campaign}

So erstellen Sie eine Kampagne:

1. Öffnen Sie die **Marke** Seite, die Sie erstellt haben.
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für Ihre Seite an (beispielsweise „We.Retail-Kampagne“), wählen Sie die Vorlage **Kampagne** aus und klicken Sie auf **Erstellen**.

### Erstellen von Erlebnissen {#creating-experiences}

So erstellen Sie Erlebnisse für Segmente:

1. Öffnen Sie die **Kampagne** Seite, die Sie erstellt haben.
1. Erstellen Sie Erlebnisse für Ihre Segmente, indem Sie auf **Seite erstellen** klicken, und geben Sie einen Titel für Ihre Seite ein, z. B. „Männlich“, wenn Sie ein Erlebnis für das Segment „Männlich“ erstellen, und wählen Sie dann die Vorlage **Erlebnis** aus.
1. Öffnen Sie die erstellte Erlebnisseite.
1. Klicken Sie auf **Bearbeiten** und unterhalb der Segmente auf **Element hinzufügen**.
1. Geben Sie den Pfad zum männlichen Segment ein, beispielsweise **/etc/segmentation/ac-segments/male** und klicken **OK**. Es wird folgende Meldung angezeigt: *Erlebnis ist ausgerichtet auf: Männlich*.
1. Wiederholen Sie die vorherigen Schritte, um ein Erlebnis für alle Segmente zu erstellen, z. B. für die weibliche Zielgruppe.

## Erstellen eines Newsletters mit zielgerichteten Inhalten {#creating-a-newsletter-with-targeted-content}

Nachdem Sie Segmente, eine Marke, eine Kampagne und ein Erlebnis erstellt haben, können Sie einen Newsletter mit zielgerichteten Inhalten erstellen. Nachdem Sie das Erlebnis erstellt haben, verknüpfen Sie Erlebnisse mit Ihren Segmenten.

>[!NOTE]
>
>[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md). Laden Sie Beispielinhalt aus Package Share herunter.

So erstellen Sie einen Newsletter mit zielgerichtetem Inhalt:

1. Erstellen Sie einen Newsletter mit zielgerichteten Inhalten: Klicken Sie unter &quot;E-Mail-Kampagnen in Geometrixx Outdoors&quot;auf **Erstellen** > **Seite** und wählen Sie eine der Adobe Campaign Mail-Vorlagen aus.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Fügen Sie dem Newsletter eine Text- und Personalisierungs-Komponente hinzu.
1. Fügen Sie der Text- und Personalisierungs-Komponente Text hinzu, beispielsweise: „Dies ist der Standardtext.“
1. Klicken Sie auf den Pfeil neben **Bearbeiten** und wählen Sie **Targeting** aus.
1. Wählen Sie die entsprechende Marke aus dem Dropdown-Menü aus und klicken Sie auf Ihre Kampagne. (Hierbei handelt es sich um die Marke und Kampagne, die Sie zuvor erstellt haben).
1. Klicken Sie auf **Targeting starten**. Die Segmente werden nun im Zielgruppenbereich angezeigt. Sollte ein Besucher nicht in eines der festgelegten Segmente passen, wird er zum Standarderlebnis weitergeleitet.

   >[!NOTE]
   >
   >Standardmäßig werden die in AEM enthaltenen E-Mail-Beispiele als Zielgruppenbestimmungs-Engine für Adobe Campaign verwendet. Bei benutzerdefinierten Newslettern müssen Sie möglicherweise Adobe Campaign als Zielgruppenbestimmungs-Engine auswählen. Klicken Sie beim Targeting in der Symbolleiste auf +, geben Sie einen Titel für die neue Aktivität ein und wählen Sie **Adobe Campaign** als Targeting-Engine.

1. Klicken Sie auf **Standard** und dann auf die Komponente „Text und Personalisierung“, die Sie hinzugefügt haben, und Sie sehen eine Zielscheibe mit darin steckendem Pfeil. Klicken Sie auf das Symbol, um diese Komponente als Ziel festzulegen.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Navigieren Sie zu einem anderen Segment („Männlich“), klicken Sie auf **Angebot hinzufügen** und klicken Sie auf das Pluszeichen (+). Bearbeiten Sie anschließend das Angebot.
1. Navigieren Sie zu einem anderen Segment („Weiblich“), klicken Sie auf **Angebot hinzufügen** und dann auf das Pluszeichen (+). Bearbeiten Sie anschließend dieses Angebot.
1. Klicken Sie auf **Weiter**, um die Zuordnung anzuzeigen, und klicken Sie dann auf **Weiter**, um die Einstellungen anzuzeigen, die nicht für Adobe Campaign gelten, und klicken Sie auf **Speichern**.

   AEM generiert automatisch den richtigen Zielgruppenbestimmungs-Code für Adobe Campaign, wenn der Inhalt in Adobe Campaign für einen Versand genutzt wird.

1. Erstellen Sie in Adobe Campaign einen Versand: Klicken Sie auf **E-Mail-Versand mit AEM-Inhalten**, wählen Sie das passende lokale AEM-Konto aus und bestätigen Sie die Änderungen.

   In der HTML-Ansicht sind die verschiedenen Erlebnisse zielgerichteter Komponenten im Zielgruppenbestimmungs-Code für Adobe Campaign enthalten.

   ![chlimage_1-190](assets/chlimage_1-190.png)

   >[!NOTE]
   >
   >Wenn Sie die Segmente auch in Adobe Campaign einrichten, klicken Sie auf **Vorschau** zeigt Ihnen die Erlebnisse für jedes Segment an.
