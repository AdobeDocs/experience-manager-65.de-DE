---
title: Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard
description: Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: a4717cb8-b70c-4150-b816-35e9b871e792
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 100%

---

# Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard{#working-with-adobe-campaign-and-adobe-campaign-standard}

Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie in AEM mithilfe einer spezifischen Vorlage für Adobe Campaign einen neuen Newsletter.
1. Wählen Sie [einen Adobe Campaign-Service](#selectingtheadobecampaigncloudservice) aus, bevor Sie die Inhalte bearbeiten, um Zugriff auf alle Funktionen zu erhalten.
1. Bearbeiten Sie den Inhalt.
1. Überprüfen Sie den Inhalt.

Der Inhalt kann anschließend mit einer Bereitstellung in Adobe Campaign synchronisiert werden. Detaillierte Anweisungen finden Sie in diesem Dokument.

>[!NOTE]
>
>Bevor Sie diese Funktion verwenden können, müssen Sie AEM so konfigurieren, dass es sich entweder mit [Adobe Campaign](/help/sites-administering/campaignonpremise.md) oder [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) integrieren lässt.

## Senden von E-Mail-Inhalten über Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nachdem Sie AEM und Adobe Campaign konfiguriert haben, können Sie E-Mail-Versandinhalte direkt in AEM erstellen und sie dann in Adobe Campaign verarbeiten.

Wenn Sie Adobe Campaign-Inhalte in AEM erstellen, müssen Sie sich mit einem Adobe Campaign-Service verbinden, damit für die Bearbeitung der Inhalte sämtliche Funktionen bereitstehen.

Es gibt zwei mögliche Fälle:

* Inhalte können mit einem Versand aus Adobe Campaign synchronisiert werden. So können Sie AEM-Inhalte in einem Versand verwenden.
* (nur Adobe Campaign On Premise) Inhalte können direkt an Adobe Campaign gesendet werden, wodurch automatisch eine neue E-Mail-Bereitstellung generiert wird. Dieser Modus weist Einschränkungen auf.

Detaillierte Anweisungen finden Sie in diesem Dokument.

### Erstellen neuer E-Mail-Inhalte {#creating-new-email-content}

>[!NOTE]
>
>Stellen Sie sicher, dass E-Mail-Vorlagen unter **/content/campaigns** hinzugefügt werden, sodass sie sich verwenden lassen.
>

1. Wählen Sie in AEM den Ordner **Websites** aus und durchsuchen Sie den Explorer nach dem Speicherort, an dem Ihre E-Mail-Kampagnen verwaltet werden. Im folgenden Beispiel ist der entsprechende Knoten **Websites** > **Kampagnen** > **Geometrixx Outdoors** > **E-Mail-Kampagnen**.

   >[!NOTE]
   >
   >[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md#weretail). Laden Sie Geometrixx-Beispielinhalt aus Package Share herunter.

   ![chlimage_1-172](assets/chlimage_1-172.png)

1. Wählen Sie **Neu** > **Neue Seite** aus, um neue E-Mail-Inhalte zu erstellen.
1. Wählen Sie eine der verfügbaren Adobe Campaign-spezifischen Vorlagen und füllen Sie dann die allgemeinen Eigenschaften der Seite aus.  Standardmäßig sind drei Vorlagen verfügbar:

   * **Adobe Campaign-E-Mail (AC 6.1)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign 6.1 übermittelt wird.
   * **Adobe Campaign-E-Mail (ACS)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign Standard weitergeleitet wird.

   ![chlimage_1-173](assets/chlimage_1-173.png)

1. Klicken Sie auf **Erstellen**, um die E-Mail oder den Newsletter zu erstellen.

### Auswählen des Adobe Campaign-Cloud-Service und der Vorlage {#selecting-the-adobe-campaign-cloud-service-and-template}

Zur Integration mit Adobe Campaign müssen Sie der Seite einen Adobe Campaign-Cloud-Service hinzufügen. Auf diese Weise erhalten Sie Zugriff auf Personalisierung und andere Adobe Campaign-Informationen.

Darüber hinaus müssen Sie möglicherweise auch die Adobe Campaign-Vorlage auswählen, den Betreff ändern und Textinhalte für die Benutzerinnen bzw. Benutzer hinzufügen, die die E-Mail nicht in HTML anzeigen.

1. Wählen Sie im Sidekick die Registerkarte **Seite** und anschließend **Seiteneigenschaften** aus.
1. Wählen Sie auf der Registerkarte **Cloud-Services** im Popup-Fenster **Service hinzufügen** aus, um den Adobe Campaign-Service hinzuzufügen, und klicken Sie auf **OK**.

   ![chlimage_1-174](assets/chlimage_1-174.png)

1. Wählen Sie aus einer Dropdown-Liste die Konfiguration aus, die Ihrer Adobe Campaign-Konfiguration entspricht, und bestätigen Sie Ihre Auswahl durch einen Klick auf **OK**.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie nach dem Hinzufügen des Cloud-Service auf **OK** oder **Anwenden** klicken. Nur so funktioniert die Registerkarte **Adobe Campaign** ordnungsgemäß.

1. Möchten Sie anstatt der Standardvorlage **E-Mail** eine bestimmte Bereitstellungsvorlage für E-Mails (aus Adobe Campaign) verwenden, wählen Sie erneut **Seiteneigenschaften** aus. Geben Sie auf der Registerkarte **Adobe Campaign** den internen Namen der E-Mail-Bereitstellungsvorlage in der entsprechenden Adobe Campaign-Instanz ein.

   In Adobe Campaign Standard ist dies die Vorlage **Bereitstellung mit AEM-Inhalt**. In Adobe Campaign 6.1 ist dies die Vorlage **E-Mail-Bereitstellung mit AEM-Inhalt**.

   Wenn Sie eine Vorlage auswählen, aktiviert AEM automatisch die Komponenten von **Adobe Campaign-Newsletter**.

### Bearbeiten von E-Mail-Inhalten {#editing-email-content}

Sie können E-Mail-Inhalte entweder in der klassischen Benutzeroberfläche oder in der Touch-optimierten Benutzeroberfläche bearbeiten.

1. Geben Sie den Betreff und die Textversion der E-Mail ein, indem Sie **Seiteneigenschaften** > **E-Mail** in der Toolbox auswählen.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Bearbeiten Sie die E-Mail-Inhalte, indem Sie die gewünschten Elemente durch die im Sidekick verfügbaren Optionen hinzufügen.  Hierzu ziehen Sie die Komponenten einfach per Drag-and-Drop in die E-Mail.  Doppelklicken Sie dann auf das Element, das Sie bearbeiten möchten.

   Sie können beispielsweise Text hinzufügen, der Personalisierungsfelder enthält.

   ![chlimage_1-176](assets/chlimage_1-176.png)

   Eine Beschreibung der für Adobe Campaign-Newsletter/-E-Mails verfügbaren Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Einfügen von Personalisierungen {#inserting-personalization}

Beim Bearbeiten Ihrer Inhalte können Sie Folgendes einfügen:

* Adobe Campaign-Kontextfelder. Hierbei handelt es sich um Felder, die Sie in Ihren Text einfügen können und die sich automatisch je nach Daten der Empfängerinnen bzw. Empfänger ändern (beispielsweise Vor- und Nachname oder andere Daten der Zieldimension).
* Adobe Campaign-Personalisierungsblöcke. Hierbei handelt es sich um Blöcke mit vorkonfiguriertem Inhalt, die sich nicht auf die Daten der Empfängerinnen und Empfänger beziehen (beispielsweise ein Markenlogo oder ein Link zu einer Mirrorseite).

Eine ausführliche Beschreibung der Campaign-Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

>[!NOTE]
>
>* Nur die Felder der Adobe Campaign-Zielgruppendimension **Profile** werden berücksichtigt.
>* Wenn Sie Eigenschaften von **Sites** anzeigen, haben Sie keinen Zugriff auf die Adobe Campaign-Kontextfelder. Sie können bei deren Bearbeitung direkt aus E-Mails darauf zugreifen.
>

1. Fügen Sie eine neue Komponente aus **Newsletter** > **Text und Personalisierung (Kampagne)** ein.
1. Öffnen Sie die Komponente, indem Sie darauf doppelklicken.  Das Fenster **Bearbeiten** verfügt über eine Funktion, mit der Sie die Personalisierungselemente einfügen können.

   >[!NOTE]
   >
   >Die verfügbaren Kontextfelder entsprechen der Zielgruppendimension **Profile** in Adobe Campaign.
   >
   >Weitere Informationen finden Sie unter [Verknüpfen von AEM-Seiten mit Adobe Campaign-E-Mails](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#linkinganaempagetoanadobecampaignemail).

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Wählen Sie **ClientContext** im Sidekick aus, um die Personalisierungsfelder unter Verwendung der Daten in den Rollenprofilen zu testen.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Es öffnet sich ein Fenster, in dem das gewünschte Profil ausgewählt werden kann.  Die Personalisierungsfelder werden automatisch durch Daten aus dem ausgewählten Profil ersetzt.

   ![chlimage_1-180](assets/chlimage_1-180.png)

### Newsletter-Vorschau {#previewing-a-newsletter}

Sie können das Aussehen des Newsletters und die Personalisierung in der Vorschau anzeigen.

1. Öffnen Sie den Newsletter, dessen Vorschau angezeigt werden soll, und klicken Sie auf Vorschau (Lupe), um den Sidekick zu verkleinern.
1. Klicken Sie auf eines der E-Mail-Client-Symbole, um herauszufinden, wie der Newsletter von verschiedenen Clients angezeigt wird.

   ![chlimage_1-181](assets/chlimage_1-181.png)

1. Erweitern Sie den Sidekick, um die E-Mail erneut zu bearbeiten.

### Genehmigen von Inhalten in AEM {#approving-content-in-aem}

Nach der Bearbeitung der Inhalte kann mit deren Genehmigung begonnen werden. Rufen Sie in der Toolbox die Registerkarte **Workflow** auf und wählen Sie den Workflow **Für Adobe Campaign genehmigen** aus.

Dieser Standard-Workflow besteht aus zwei Schritten: Prüfung und Genehmigung oder Prüfung und Ablehnung. Dieser Workflow kann jedoch erweitert und komplexer gestaltet werden.

![chlimage_1-182](assets/chlimage_1-182.png)

Um den Inhalt für Adobe Campaign zu genehmigen, wenden Sie den Workflow an, indem Sie im Sidekick **Workflow** auswählen. Wählen Sie dann **Für Adobe Campaign genehmigen** aus und klicken Sie auf **Workflow starten**. Führen Sie die vorgegebenen Schritte aus und genehmigen Sie den Inhalt. Sie können Inhalte auch ablehnen, indem Sie im letzten Schritt des Workflows statt **Genehmigen** die Option **Ablehnen** auswählen.

![chlimage_1-183](assets/chlimage_1-183.png)

Nachdem der Inhalt genehmigt wurde, wird er in Adobe Campaign als genehmigt angezeigt. Die E-Mail kann dann gesendet werden.

Adobe Campaign Standard:

![chlimage_1-184](assets/chlimage_1-184.png)

In Adobe Campaign 6.1:

![chlimage_1-185](assets/chlimage_1-185.png)

>[!NOTE]
>
>Es ist zwar möglich, nicht genehmigte Inhalte mit einem Versand in Adobe Campaign zu synchronisieren, es ist jedoch nicht möglich, einen solchen Versand durchzuführen. Ein Versand mit Campaign lässt sich nur mit genehmigten Inhalten versenden.

## Verknüpfen von AEM mit Adobe Campaign Standard und Adobe Campaign 6.1 {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verknüpfen von AEM mit Adobe Campaign Standard und Adobe Campaign 6.1](/help/sites-authoring/campaign.md#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic) unter [Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard](/help/sites-authoring/campaign.md) in der Standarddokumentation für die Bearbeitung.
