---
title: Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard
seo-title: Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard
description: Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten.
seo-description: Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten.
uuid: 439df7fb-590b-45b8-9768-565b022a808b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 61b2bd47-dcef-4107-87b1-6bf7bfd3043b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Arbeiten mit Adobe Campaign 6.1 und Adobe Campaign Standard{#working-with-adobe-campaign-and-adobe-campaign-standard}

Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie in AEM mithilfe einer für Adobe Campaign spezifischen Vorlage einen neuen Newsletter.
1. Wählen Sie [einen Adobe Campaign-Service](#selectingtheadobecampaigncloudservice) aus, bevor Sie die Inhalte bearbeiten, um Zugriff auf alle Funktionen zu erhalten.
1. Bearbeiten Sie den Inhalt.
1. Überprüfen Sie den Inhalt. 

Der Inhalt kann anschließend mit einer Bereitstellung in Adobe Campaign synchronisiert werden. Eine ausführliche Anleitung finden Sie in diesem Dokument.

>[!NOTE]
>
>Bevor Sie diese Funktion verwenden können, müssen Sie AEM so konfigurieren, dass es sich entweder mit [Adobe Campaign](/help/sites-administering/campaignonpremise.md) oder [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) integrieren lässt.

## Versenden von E-Mail-Inhalten mit Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nach der Konfiguration von AEM und Adobe Campaign können Sie E-Mail-Inhalte direkt in AEM erstellen und sie anschließend in Adobe Campaign verarbeiten.

Wenn Sie Adobe Campaign-Inhalte in AEM erstellen, müssen Sie eine Verknüpfung zu einem Adobe Campaign-Dienst erstellen, bevor Sie den Inhalt bearbeiten können, um auf alle Funktionen zugreifen zu können.

Es gibt zwei mögliche Fälle:

* Der Inhalt kann mit einer Bereitstellung in Adobe Campaign synchronisiert sein. So lassen sich AEM-Inhalte in einer Bereitstellung verwenden.
* (nur Adobe Campaign On Premise) Inhalte können direkt an Adobe Campaign gesendet werden, wodurch automatisch eine neue E-Mail-Bereitstellung generiert wird. Diese Methode hat jedoch Einschränkungen.

Eine ausführliche Anleitung finden Sie in diesem Dokument.

### Erstellen neuer E-Mail-Inhalte {#creating-new-email-content}

>[!NOTE]
>
>When adding email templates, be sure to add them under **/content/campaigns** to make them available.


1. In AEM, select the **Websites** folder then browse your explorer to find where your email campaigns are managed. In the following example, the node concerned is **Websites** > **Campaigns** > **Geometrixx Outdoors** > **Email Campaigns**.

   >[!NOTE]
   >
   >[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md#weretail). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

   ![chlimage_1-172](assets/chlimage_1-172.png)

1. Select **New** > **New Page** to create new email content.
1. Wählen Sie eine der drei spezifischen Adobe Campaign-Vorlagen aus und legen Sie die allgemeinen Eigenschaften der Seite fest. Standardmäßig sind drei Vorlagen verfügbar:

   * **Adobe Campaign-E-Mail (AC 6.1)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign 6.1 übermittelt wird.
   * **Adobe Campaign-E-Mail (ACS)**: Hiermit können Sie einer Vorlage eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign Standard weitergeleitet wird.
   ![chlimage_1-173](assets/chlimage_1-173.png)

1. Click **Create** to create your email or newsletter.

### Auswählen von Adobe Campaign-Cloud-Service und Vorlagen {#selecting-the-adobe-campaign-cloud-service-and-template}

Möchten Sie eine Integration mit Adobe Campaign durchführen, müssen Sie der Seite einen Adobe Campaign-Service hinzufügen. Somit verfügen Sie über Zugriff auf Personalisierung und andere Daten aus Adobe Campaign.

Des Weiteren müssen Sie möglicherweise auch eine Adobe Campaign-Vorlage auswählen und den Betreff ändern und normalen Text für Benutzer einfügen, die die E-Mail nicht im HTML-Format anzeigen.

1. Select the **Page** tab in the sidekick, then select **Page properties.**
1. In the **Cloud services** tab in the pop-up window, select **Add Service** to add the Adobe Campaign service and click **OK**.

   ![chlimage_1-174](assets/chlimage_1-174.png)

1. Wählen Sie aus einer Dropdown-Liste die Konfiguration aus, die Ihrer Adobe Campaign-Konfiguration entspricht, und bestätigen Sie Ihre Auswahl durch einen Klick auf **OK**.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie nach dem Hinzufügen des Cloud-Service auf **OK** oder **Anwenden** tippen oder klicken. Nur so funktioniert die Registerkarte **Adobe Campaign** ordnungsgemäß.

1. If you would like to apply a specific email delivery template (from Adobe Campaign), other than the default **mail** template, select **Page properties** again. In the **Adobe Campaign** tab, enter the email delivery template&#39;s internal name in the related Adobe Campaign instance.

   In Adobe Campaign Standard lautet die Vorlage **Bereitstellung mit AEM-Inhalten**. In Adobe Campaign 6.1 lautet die Vorlage **E-Mail-Bereitstellung mit AEM-Inhalten**.

   When you select the template, AEM automatically enables the **Adobe Campaign Newsletter** components.

### Bearbeiten von E-Mail-Inhalten {#editing-email-content}

E-Mail-Inhalte können entweder in der klassischen oder in der Touch-optimierten Benutzeroberfläche bearbeitet werden.

1. Enter the subject and the text version of the email by selecting **Page properties** > **Email** from the toolbox.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Bearbeiten Sie die E-Mail-Inhalte, indem Sie die gewünschten Elemente durch die im Sidekick verfügbaren Optionen hinzufügen. Hierzu ziehen Sie die Komponenten einfach in die E-Mail. Klicken Sie anschließend doppelt auf das Element, das Sie bearbeiten möchten.

   Sie können beispielsweise Text hinzufügen, der Personalisierungsfelder enthält.

   ![chlimage_1-176](assets/chlimage_1-176.png)

   Eine Beschreibung der für Adobe Campaign-Newsletter/-E-Mails verfügbaren Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Einfügen von Personalisierung {#inserting-personalization}

Beim Bearbeiten Ihres Inhalts können Sie Folgendes einfügen:

* Adobe Campaign-Kontextfelder. Hierbei handelt es sich um Felder, die Sie in Ihren Text einfügen können, und die entsprechend den Daten des Empfängers angepasst werden (z. B. Vorname, Nachname oder Daten der Zieldimension).
* Adobe Campaign-Personalisierungsblöcke. Dies sind Blöcke vordefinierter Inhalte, die nicht mit den Daten des Empfängers in Zusammenhang stehen, wie z. B. ein Markenlogo oder ein Link zu einer Spiegelseite.

Detaillierte Beschreibungen der Komponenten von Adobe Campaign finden Sie unter [Adobe Campaign-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

>[!NOTE]
>
>* Es werden nur die Felder der Adobe Campaign-**Profile** der Targeting-Dimension berücksichtigt.
>* When viewing Properties from **Sites**, you do not have access to the Adobe Campaign context fields. Sie können bei deren Bearbeitung direkt aus E-Mails darauf zugreifen.
>



1. Insert a new **Newsletter** > **Text &amp; Personalization (Campaign)** component.
1. Öffnen Sie die Komponente, indem Sie doppelt darauf klicken. Im Fenster **Bearbeiten** stehen Ihnen Funktionen zur Verfügung, mit deren Hilfe Sie personalisierte Inhalte einfügen können.

   >[!NOTE]
   >
   >Die verfügbaren Kontextfelder entsprechen den **Profilen** der Targeting-Dimension in Adobe Campaign.
   >
   >See [Linking an AEM page to an Adobe Campaign email](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#linkinganaempagetoanadobecampaignemail).

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Select **Client Context** in the sidekick to test the personalization fields using the data in the persona profiles.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Es öffnet sich ein Fenster, in dem das gewünschte Profil ausgewählt werden kann. Personalisierungsfelder werden automatisch mit Daten des ausgewählten Profils bestückt.

   ![chlimage_1-180](assets/chlimage_1-180.png)

### Newslettervorschau {#previewing-a-newsletter}

Sie können sich eine Vorschau des Newsletters und der Personalisierung anzeigen lassen.

1. Öffnen Sie den Newsletter, dessen Vorschau angezeigt werden soll, und klicken Sie auf Vorschau (Lupe), um den Sidekick zu verkleinern.
1. Klicken Sie auf eines der E-Mail-Client-Symbole, um herauszufinden, wie der Newsletter von verschiedenen Clients angezeigt wird.

   ![chlimage_1-181](assets/chlimage_1-181.png)

1. Erweitern Sie den Sidekick, um die E-Mail erneut zu bearbeiten.

### Genehmigen von Inhalten in AEM {#approving-content-in-aem}

Nach der Bearbeitung der Inhalte kann mit deren Genehmigung begonnen werden. Go to the **Workflow** tab of the toolbox and select the **Approve for Adobe Campaign** workflow.

Dieser Standardarbeitsablauf besteht aus zwei Schritten: Prüfung und Genehmigung oder Prüfung und Ablehnung. Der Arbeitsablauf kann jedoch auch ausgeweitet oder an komplexere Prozesse angepasst werden.

![chlimage_1-182](assets/chlimage_1-182.png)

Möchten Sie Inhalte für Adobe Campaign genehmigen, wenden Sie den Arbeitsablauf an, indem Sie **Workflow** im Sidekick auswählen, die Option **Für Adobe Campaign genehmigen** wählen und auf **Workflow starten klicken**. Führen Sie die vorgegebenen Schritte aus und genehmigen Sie den Inhalt. Sie können Inhalte auch ablehnen, indem Sie im letzten Schritt des Arbeitsablaufs statt **Genehmigen** die Option **Ablehnen** wählen.

![chlimage_1-183](assets/chlimage_1-183.png)

Nach der Genehmigung des Inhalts wird dieser in Adobe Campaign als genehmigt gekennzeichnet. Die E-Mail kann nun verschickt werden.

In Adobe Campaign Standard:

![chlimage_1-184](assets/chlimage_1-184.png)

In Adobe Campaign 6.1:

![chlimage_1-185](assets/chlimage_1-185.png)

>[!NOTE]
>
>Nicht genehmigte Inhalte können in Adobe Campaign mit einer Bereitstellung synchronisiert werden, diese Bereitstellung lässt sich jedoch nicht durchführen. Mit Campaign-Bereitstellungen lassen sich nur genehmigte Inhalte versenden.

## Verknüpfen von AEM mit Adobe Campaign Standard und Adobe Campaign 6.1 {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign}

>[!NOTE]
>
>See [Linking AEM with Adobe Campaign Standard and Adobe Campaign 6.1](/help/sites-authoring/campaign.md#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic) under [Working with Adobe Campaign 6.1 and Adobe Campaign Standard](/help/sites-authoring/campaign.md) in the standard authoring docurmentation for details.

