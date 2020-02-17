---
title: Konfigurieren der Integration von AEM Assets mit Brand Portal
seo-title: Konfigurieren der Integration von AEM Assets mit Brand Portal
description: Erfahren Sie, wie AEM Assets mit Brand Portal integriert wird, um Assets und Sammlungen in Brand Portal zu veröffentlichen.
seo-description: Erfahren Sie, wie AEM Assets mit Brand Portal integriert wird, um Assets und Sammlungen in Brand Portal zu veröffentlichen.
uuid: b95c046e-9988-444c-b50e-ff5ec8cafe14
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: dca5a2ac-1fc8-4251-b073-730fd6f49b1c
docset: aem65
translation-type: tm+mt
source-git-commit: 9c73abc3291f2847c705cb649d2993fb186b0993

---


# Konfigurieren der Integration von AEM Assets mit Brand Portal {#configure-aem-assets-integration-with-brand-portal}

Wenn Sie Adobe Experience Manager (AEM) Asset Brand Portal-Kunde sind, können Sie AEM Assets in das Markenportal integrieren, um die Veröffentlichung von Assets im Markenportal zu aktivieren. Sie können diese Integration über die Adobe.io-Benutzeroberfläche einrichten.

Erstellen Sie zunächst im öffentlichen Gateway von Marketing Cloud eine Anwendung mit einem Authentifizierungsmechanismus. Als Nächstes erstellen Sie mithilfe der aus dem Gateway abgerufenen Anwendungs-ID ein Profil in Ihrer AEM Assets-Instanz.

Verwenden Sie diese Konfiguration, um Assets aus AEM Assets in Brand Portal zu veröffentlichen. Am Backend authentifiziert der AEM-Server Ihr Profil beim Gateway und integriert dann AEM Assets mit Brand Portal.

>[!NOTE]
>
>The User Interface for configuring oAuth integrations is hosted in [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/), which was earlier hosted in [https://marketing.adobe.com/developer/](https://marketing.adobe.com/developer/).

## Erstellen von JWT-Anwendungen {#create-jwt-application}

1. Login to [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/) with your Adobe ID. **Die Seite &quot;JWT-Anwendungen** &quot;wird geöffnet.

   >[!NOTE]
   >
   >Sie können eine Anwendungs-ID nur erstellen, wenn Sie der Systemadministrator Ihrer Organisation sind. Mandant ist der technische Name für Ihr Unternehmen, der bei Adobe Marketing Cloud registriert ist.

1. Select **[!UICONTROL Add Application]** to create an application.
1. Geben Sie einen Namen für die Anwendung und eine optionale Beschreibung an.
1. Wählen Sie aus der Liste **[!UICONTROL Organisation]** die Organisation aus, für die Sie die Assets synchronisieren möchten.
1. From the **[!UICONTROL Scope]** list, select **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]**, and **[!UICONTROL cc-share]**.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.  Daraufhin wird eine JWT-Dienstanwendung erstellt. Sie können die Anwendung bearbeiten und speichern.
1. Kopieren Sie die Anwendungs-ID, die für die neue Anwendung erstellt wird.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie nicht versehentlich die geheime Frage für die Anwendung statt der Anwendungs-ID kopieren.

## Erstellen neuer Cloud-Konfigurationen {#create-a-new-cloud-configuration}

1. From the **[!UICONTROL Navigation]** page of your local AEM Assets instance, click **[!UICONTROL Tools]** icon on the left.

1. Navigate to **[!UICONTROL Cloud Services]>[!UICONTROL Legacy Cloud Services]**.

   ![AEM-Tools](assets/aem-tools.png)

1. In **[!UICONTROL Cloud Services]**, locate the **[!UICONTROL Assets Brand Portal]** service under **[!UICONTROL Adobe Experience Cloud]**.

   ![Adobe Experience Cloud Services](assets/experience-cloud-services.png)

1. Click **[!UICONTROL Configure now]** link below the service to display the **[!UICONTROL Create Configuration]** dialog.
1. In **[!UICONTROL Create Configuration]** dialog, specify a title and name for the new configuration and click **[!UICONTROL Create]**.

   ![bp-config](assets/bp-config.png)

1. In the **[!UICONTROL AEM Assets Brand Portal Replication]** dialog, specify the URL of your organization in the **[!UICONTROL Tenant URL]** field.
1. Fügen Sie im Feld **[!UICONTROL Client-ID]** die Anwendungs-ID ein, die Sie am Ende des Vorgangs [Anwendung erstellen](/help/assets/brand-portal-configuring-integration.md#create-jwt-application) kopiert haben. Wählen Sie **[!UICONTROL OK]** aus.

   ![public-folder-publish](assets/public-folder-publish.png)

1. To make the assets (published from AEM) publicly available to general users of Brand Portal, enable the **[!UICONTROL Public Folder Publish]** check box .

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Veröffentlichung eines öffentlichen Ordners]** ist ab AEM-Version 6.3.2.1 verfügbar.

1. Klicken Sie auf der Seite **[!UICONTROL Brand Portal-Konfiguration]** auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**, um den öffentlichen Schlüssel anzuzeigen, der für Ihre Instanz erzeugt wurde.

   ![display-public-key](assets/display-public-key.png)

   Alternatively, click **[!UICONTROL Download Public Key for OAuth Gateway]** to download the file containing the public key. Öffnen Sie dann die Datei, um den öffentlichen Schlüssel anzuzeigen.

## Aktivieren der Integration {#enable-integration}

1. Display the public key using one of the following methods mentioned in the last step of the procedure [Add a new configuration to Marketing Cloud](/help/assets/brand-portal-configuring-integration.md#create-a-new-cloud-configuration).

   * Click **[!UICONTROL Display Public Key]** button to display the key.
   * Öffnen Sie die heruntergeladene Datei, die den Schlüssel enthält.

1. Open the Marketing Cloud Developer Connection interface and click on the application you created in [Create an application](/help/assets/brand-portal-configuring-integration.md#create-jwt-application).
1. Fügen Sie den öffentlichen Schlüssel in das Feld **[!UICONTROL Öffentlicher Schlüssel]** der Konfigurationsbenutzeroberfläche ein.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Eine Meldung bestätigt, dass die Anwendung aktualisiert wurde.

## Testen der Integration {#test-the-integration}

1. From the **[!UICONTROL Navigation]** page of your local AEM Assets instance, click **[!UICONTROL Tools]** icon on the left.

1. Navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**.

   ![deployment](assets/deploymentreplication.png)

1. In the **[!UICONTROL Replication]** page, click **[!UICONTROL Agents on author]**.

   ![agents_on_author](assets/agents_on_author.png)

1. Um die Verbindung zwischen AEM Author und Brand Portal zu überprüfen, öffnen Sie einen der vier Replikationsagenten und klicken Sie auf **[!UICONTROL Verbindung testen]**.

   >[!NOTE]
   >
   >Die Replizierungsagenten arbeiten parallel und teilen die Auftragsverteilung gleichmäßig, wodurch die Veröffentlichungsgeschwindigkeit um das Vierfache der Originalgeschwindigkeit steigt. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.

   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation einiger Assets fehlschlägt.

   ![aem_assets_parallelpublishing](assets/aem_assets_parallelpublishing.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

   ![Replication_succeeded](assets/replication_succeeded.png)

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen im Brand Portal veröffentlichen. Weitere Details finden Sie unter:

* [Veröffentlichen von Assets und Ordnern in Brand Portal](/help/assets/brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen in Brand Portal](/help/assets/brand-portal-publish-collection.md)

## Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen im Brand Portal veröffentlichen. Gehen Sie wie folgt vor, um Assets in Brand Portal zu veröffentlichen:

>[!NOTE]
>
>Adobe empfiehlt eine gestaffelte Veröffentlichung, vorzugsweise außerhalb der Spitzenzeiten, sodass die AEM-Autoreninstanz keine übermäßigen Ressourcen belegt.

1. Wählen Sie in der Assets-Konsole die Assets/Ordner aus, die Sie veröffentlichen möchten, und klicken Sie in der Symbolleiste auf die Option &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;.

   Alternativ können Sie auch die Assets auswählen, die Sie in Brand Portal veröffentlichen möchten.

   ![publish2bp-2](assets/publish2bp.png)

1. Um die Assets im Markenportal zu veröffentlichen, stehen zwei Optionen zur Verfügung:
   * [Assets sofort veröffentlichen](#publish-to-bp-now)
   * [Assets später veröffentlichen](#publish-to-bp-now)

### Assets jetzt veröffentlichen {#publish-to-bp-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* From the toolbar, select **[!UICONTROL Quick Publish]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* From the toolbar, select **[!UICONTROL Manage Publication]**.

   1. Then from the **[!UICONTROL Action]** select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**. Klicken Sie auf **[!UICONTROL Weiter]**.

   2. Within **[!UICONTROL Scope]**, confirm your selection and click **[!UICONTROL Publish to Brand Portal]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Oberfläche des Markenportals an, um die veröffentlichten Assets anzuzeigen.

### Assets später veröffentlichen {#publish-to-bp-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Once you have selected assets/ folders to publish, select **[!UICONTROL Manage Publication]** from the tool bar at the top.

1. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

   ![publishlatbp-1](assets/publishlaterbp-1.png)

1. Select an **[!UICONTROL Activation date]** and specify time. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Select an **Activation date** and specify time. Klicken Sie auf **Weiter**.

1. Specify a **[!UICONTROL Workflow title]** in **[!UICONTROL Workflows]**. Click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

Melden Sie sich jetzt beim Markenportal an, um zu sehen, ob die veröffentlichten Assets auf der Benutzeroberfläche des Markenportals verfügbar sind.

![bp_landing_page](assets/bp_landing_page.png)
