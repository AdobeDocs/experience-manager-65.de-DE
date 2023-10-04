---
title: Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard
seo-title: Working with Adobe Campaign 6.1 and Adobe Campaign Standard
description: Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten.
seo-description: You can create email content in AEM and process it in Adobe Campaign emails.
uuid: 439df7fb-590b-45b8-9768-565b022a808b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 61b2bd47-dcef-4107-87b1-6bf7bfd3043b
exl-id: a4717cb8-b70c-4150-b816-35e9b871e792
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 50%

---

# Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard{#working-with-adobe-campaign-and-adobe-campaign-standard}

Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie in AEM mithilfe einer für Adobe Campaign spezifischen Vorlage einen neuen Newsletter.
1. Auswählen [einen Adobe Campaign-Dienst](#selectingtheadobecampaigncloudservice) vor der Bearbeitung des Inhalts, um auf alle Funktionen zuzugreifen.
1. Bearbeiten Sie den Inhalt.
1. Überprüfen Sie den Inhalt.

Inhalte können dann mit einem Versand in Adobe Campaign synchronisiert werden. Detaillierte Anweisungen finden Sie in diesem Dokument.

>[!NOTE]
>
>Bevor Sie diese Funktion verwenden können, müssen Sie AEM so konfigurieren, dass entweder [Adobe Campaign](/help/sites-administering/campaignonpremise.md) oder [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md).

## Senden von E-Mail-Inhalten über Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nachdem Sie AEM und Adobe Campaign konfiguriert haben, können Sie E-Mail-Versandinhalte direkt in AEM erstellen und sie dann in Adobe Campaign verarbeiten.

Wenn Sie Adobe Campaign-Inhalte in AEM erstellen, müssen Sie sich mit einem Adobe Campaign-Service verbinden, damit für die Bearbeitung der Inhalte sämtliche Funktionen bereitstehen.

Es gibt zwei mögliche Fälle:

* Inhalte können mit einem Versand aus Adobe Campaign synchronisiert werden. Auf diese Weise können Sie AEM Inhalt in einem Versand verwenden.
* (Nur Adobe Campaign vor Ort) Der Inhalt kann direkt an Adobe Campaign gesendet werden, wodurch automatisch ein neuer E-Mail-Versand erstellt wird. Dieser Modus weist Einschränkungen auf.

Detaillierte Anweisungen finden Sie in diesem Dokument.

### Erstellen neuer E-Mail-Inhalte {#creating-new-email-content}

>[!NOTE]
>
>Stellen Sie sicher, dass E-Mail-Vorlagen unter **/content/campaigns** hinzugefügt werden, sodass sie sich verwenden lassen.
>

1. Wählen Sie in AEM den Ordner **Websites** aus und durchsuchen Sie den Explorer nach dem Speicherort, an dem Ihre E-Mail-Kampagnen verwaltet werden. Im folgenden Beispiel ist der entsprechende Knoten **Websites** > **Kampagnen** > **Geometrixx Outdoors** > **E-Mail-Kampagnen**.

   >[!NOTE]
   >
   >[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md#weretail). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

   ![chlimage_1-172](assets/chlimage_1-172.png)

1. Wählen Sie **Neu** > **Neue Seite** aus, um neue E-Mail-Inhalte zu erstellen.
1. Wählen Sie eine der für Adobe Campaign verfügbaren Vorlagen aus und füllen Sie dann die allgemeinen Eigenschaften der Seite aus. Standardmäßig sind drei Vorlagen verfügbar:

   * **Adobe Campaign-E-Mail (AC 6.1)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign 6.1 übermittelt wird.
   * **Adobe Campaign-E-Mail (ACS)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign Standard weitergeleitet wird.

   ![chlimage_1-173](assets/chlimage_1-173.png)

1. Klicken Sie auf **Erstellen**, um die E-Mail oder den Newsletter zu erstellen.

### Auswählen des Adobe Campaign-Cloud-Service und der Vorlage {#selecting-the-adobe-campaign-cloud-service-and-template}

Zur Integration mit Adobe Campaign müssen Sie der Seite einen Adobe Campaign-Cloud-Service hinzufügen. Auf diese Weise erhalten Sie Zugriff auf Personalisierung und andere Adobe Campaign-Informationen.

Darüber hinaus müssen Sie möglicherweise auch die Adobe Campaign-Vorlage auswählen, den Betreff ändern und Textinhalte für die Benutzer hinzufügen, die die E-Mail nicht auf HTML anzeigen.

1. Wählen Sie im Sidekick die Registerkarte **Seite** und anschließend **Seiteneigenschaften** aus.
1. Wählen Sie auf der Registerkarte **Cloud-Services** im Popup-Fenster **Service hinzufügen** aus, um den Adobe Campaign-Service hinzuzufügen, und klicken Sie auf **OK**.

   ![chlimage_1-174](assets/chlimage_1-174.png)

1. Wählen Sie aus einer Dropdown-Liste die Konfiguration aus, die Ihrer Adobe Campaign-Konfiguration entspricht, und bestätigen Sie Ihre Auswahl durch einen Klick auf **OK**.

   >[!NOTE]
   >
   >Tippen/klicken Sie unbedingt auf **OK** oder **Anwenden** nach dem Hinzufügen des Cloud-Dienstes. Dadurch wird die **Adobe Campaign** -Tab korrekt ausgeführt werden.

1. Möchten Sie anstatt der Standardvorlage **E-Mail** eine bestimmte Bereitstellungsvorlage für E-Mails (aus Adobe Campaign) verwenden, wählen Sie erneut **Seiteneigenschaften** aus. Geben Sie auf der Registerkarte **Adobe Campaign** den internen Namen der E-Mail-Bereitstellungsvorlage in der entsprechenden Adobe Campaign-Instanz ein.

   In Adobe Campaign Standard lautet die Vorlage . **Versand mit AEM Inhalt**. In Adobe Campaign 6.1 lautet die Vorlage . **E-Mail-Versand mit AEM Inhalt**.

   Wenn Sie eine Vorlage auswählen, aktiviert AEM automatisch die Komponenten von **Adobe Campaign-Newsletter**.

### E-Mail-Inhalt bearbeiten {#editing-email-content}

Sie können E-Mail-Inhalte in der klassischen oder der Touch-optimierten Benutzeroberfläche bearbeiten.

1. Geben Sie den Betreff und die Textversion der E-Mail ein, indem Sie **Seiteneigenschaften** > **E-Mail** in der Toolbox auswählen.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Bearbeiten Sie den E-Mail-Inhalt, indem Sie die gewünschten Elemente aus den im Sidekick verfügbaren Elementen hinzufügen. Ziehen Sie sie dazu per Drag-and-Drop in den Arbeitsbereich. Doppelklicken Sie dann auf das Element, das Sie bearbeiten möchten.

   Sie können beispielsweise Text mit Personalisierungsfeldern hinzufügen.

   ![chlimage_1-176](assets/chlimage_1-176.png)

   Eine Beschreibung der für Adobe Campaign-Newsletter/-E-Mails verfügbaren Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Personalisierung einfügen {#inserting-personalization}

Beim Bearbeiten des Inhalts können Sie Folgendes einfügen:

* Adobe Campaign-Kontextfelder. Hierbei handelt es sich um Felder, die Sie in Ihren Text einfügen können und die sich entsprechend den Empfängerdaten anpassen (z. B. Vorname, Nachname oder Daten der Zieldimension).
* Adobe Campaign-Personalisierungsblöcke. Hierbei handelt es sich um Blöcke mit vorkonfiguriertem Inhalt, die sich nicht auf die Daten des Empfängers beziehen (beispielsweise Logo der Marke oder Link zu einer Mirrorseite).

Siehe [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) für eine vollständige Beschreibung der Kampagnenkomponenten.

>[!NOTE]
>
>* Nur die Felder der Adobe Campaign **Profile** Zielgruppendimension wird berücksichtigt.
>* Wenn Sie Eigenschaften von **Sites** anzeigen, haben Sie keinen Zugriff auf die Adobe Campaign-Kontextfelder. Sie können bei deren Bearbeitung direkt aus E-Mails darauf zugreifen.
>

1. Fügen Sie eine neue Komponente aus **Newsletter** > **Text und Personalisierung (Kampagne)** ein.
1. Öffnen Sie die Komponente, indem Sie darauf doppelklicken. Die **Bearbeiten** verfügt über eine Funktion, mit der Sie Personalisierungselemente einfügen können.

   >[!NOTE]
   >
   >Die verfügbaren Kontextfelder entsprechen dem **Profile** Zielgruppendimension in Adobe Campaign.
   >
   >Weitere Informationen finden Sie unter [Verknüpfen von AEM-Seiten mit Adobe Campaign-E-Mails](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#linkinganaempagetoanadobecampaignemail).

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Wählen Sie **ClientContext** im Sidekick aus, um die Personalisierungsfelder unter Verwendung der Daten in den Rollenprofilen zu testen.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Es wird ein Fenster angezeigt, in dem Sie die gewünschte Person auswählen können. Die Personalisierungsfelder werden automatisch durch Daten aus dem ausgewählten Profil ersetzt.

   ![chlimage_1-180](assets/chlimage_1-180.png)

### Newsletter-Vorschau {#previewing-a-newsletter}

Sie können eine Vorschau des Newsletters sowie eine Vorschau der Personalisierung anzeigen.

1. Öffnen Sie den Newsletter, dessen Vorschau angezeigt werden soll, und klicken Sie auf Vorschau (Lupe), um den Sidekick zu verkleinern.
1. Klicken Sie auf eines der E-Mail-Client-Symbole, um herauszufinden, wie der Newsletter von verschiedenen Clients angezeigt wird.

   ![chlimage_1-181](assets/chlimage_1-181.png)

1. Erweitern Sie den Sidekick, um die Bearbeitung erneut zu starten.

### Inhalt in AEM validieren {#approving-content-in-aem}

Nach Abschluss des Inhalts können Sie den Genehmigungsprozess starten. Rufen Sie in der Toolbox die Registerkarte **Workflow** auf und wählen Sie den Workflow **Für Adobe Campaign genehmigen** aus.

Dieser vordefinierte Workflow besteht aus zwei Schritten: Änderung, Validierung oder Revision, dann Ablehnung. Dieser Workflow kann jedoch erweitert und an einen komplexeren Prozess angepasst werden.

![chlimage_1-182](assets/chlimage_1-182.png)

Um den Inhalt für Adobe Campaign zu genehmigen, wenden Sie den Workflow an, indem Sie im Sidekick **Workflow** auswählen. Wählen Sie dann **Für Adobe Campaign genehmigen** aus und klicken Sie auf **Workflow starten**. Führen Sie die vorgegebenen Schritte aus und genehmigen Sie den Inhalt. Sie können Inhalte auch ablehnen, indem Sie im letzten Schritt des Workflows statt **Genehmigen** die Option **Ablehnen** auswählen.

![chlimage_1-183](assets/chlimage_1-183.png)

Nachdem der Inhalt genehmigt wurde, wird er als in Adobe Campaign genehmigt angezeigt. Die E-Mail kann dann gesendet werden.

In Adobe Campaign Standard:

![chlimage_1-184](assets/chlimage_1-184.png)

In Adobe Campaign 6.1:

![chlimage_1-185](assets/chlimage_1-185.png)

>[!NOTE]
>
>Nicht genehmigte Inhalte können mit einem Versand in Adobe Campaign synchronisiert werden, der Versand kann jedoch nicht ausgeführt werden. Über Campaign-Sendungen können nur genehmigte Inhalte gesendet werden.

## Verknüpfung von AEM mit Adobe Campaign Standard und Adobe Campaign 6.1 {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verknüpfen von AEM mit Adobe Campaign Standard und Adobe Campaign 6.1](/help/sites-authoring/campaign.md#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic) unter [Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard](/help/sites-authoring/campaign.md) in der Standarddokumentation für die Bearbeitung.
