---
title: Zielgruppenbestimmung für Adobe Campaign
description: Sie können zielgerichtete Erlebnisse für Adobe Campaign erstellen, nachdem Sie die Segmentierung eingerichtet haben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: fc6fccba-41c5-4c13-aac0-b4ef67767abe
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization,Integration
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
    internal-label: Personalization
  - id: 243139ec-8e41-5296-a287-31343ab1bc0f
    internal-label: Integration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 100%
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
1. Erstellen Sie eine Seite, geben Sie einen Titel ein (zum Beispiel **AC-Segmente**) und wählen Sie die Vorlage **Segment (Adobe Campaign)**
1. Wählen Sie die erstellte Seite in der Strukturansicht auf der linken Seite aus.
1. Erstellen Sie ein Segment, mit dem beispielsweise männliche Benutzer angesprochen werden, indem Sie eine Seite unter dem Segment erstellen, die Sie „männlich“ nennen, und die Vorlage **Segment (Adobe Campaign)** wählen.
1. Öffnen Sie die erstellte Segmentseite und ziehen Sie per Drag-and-Drop eine **Segment-ID** aus dem Sidekick auf die Seite.
1. Doppelklicken Sie auf das Merkmal, geben Sie die zugewiesene ID des männlichen Segments in Adobe Campaign ein (beispielsweise **MÄNNLICH**) und klicken Sie auf **OK**. Die folgende Meldung sollte angezeigt werden: *`targetData.segmentCode == "MALE"`*
1. Wiederholen Sie diese Schritte für ein weiteres Segment, beispielsweise eines, mit dem Benutzerinnen angesprochen werden.

### Erstellen einer Marke {#creating-a-brand}

So erstellen Sie eine Marke:

1. Navigieren Sie auf **Sites** zum Ordner **Kampagnen** (zum Beispiel in We.Retail).
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für die Seite ein (zum Beispiel „We.Retail-Marke“) und wählen Sie die Vorlage **Marke**.

### Erstellen einer Kampagne {#creating-a-campaign}

So erstellen Sie eine Kampagne:

1. Öffnen Sie die Seite **Marke**, die Sie erstellt haben.
1. Klicken Sie auf **Seite erstellen**, geben Sie einen Titel für Ihre Seite an (beispielsweise „We.Retail-Kampagne“), wählen Sie die Vorlage **Kampagne** aus und klicken Sie auf **Erstellen**.

### Erstellen von Erlebnissen {#creating-experiences}

So erstellen Sie Erlebnisse für Segmente:

1. Öffnen Sie die Seite **Kampagne**, die Sie erstellt haben.
1. Erstellen Sie Erlebnisse für Ihre Segmente, indem Sie auf **Seite erstellen** klicken, und geben Sie einen Titel für Ihre Seite ein, z. B. „Männlich“, wenn Sie ein Erlebnis für das Segment „Männlich“ erstellen, und wählen Sie dann die Vorlage **Erlebnis** aus.
1. Öffnen Sie die erstellte Erlebnisseite.
1. Klicken Sie auf **Bearbeiten** und unterhalb der Segmente auf **Element hinzufügen**.
1. Geben Sie den Pfad zum Segment „männlich“ ein, zum Beispiel **/etc/segmentation/ac-segments/male**, und klicken Sie auf **OK**. Es sollte die folgende Meldung angezeigt werden: *Erlebnis ist ausgerichtet auf: Männlich*.
1. Wiederholen Sie die vorherigen Schritte, um ein Erlebnis für alle Segmente zu erstellen, zum Beispiel eine weibliche Zielgruppe.
