---
title: Konfigurieren der AEM Assets-Integration mit Experience Cloud
description: Erfahren Sie, wie Sie die AEM Assets-Integration mit Experience Cloud konfigurieren können.
contentOwner: AG
feature: Asset Management
role: User, Architect, Admin
exl-id: d167cf97-6829-45a7-ba46-2239d530b060
source-git-commit: b2faf81983216bef9151548d90ae86f1c26a9f91
workflow-type: ht
source-wordcount: '987'
ht-degree: 100%

---

# Konfigurieren der AEM Assets-Integration mit Experience Cloud {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

Wenn Sie Adobe Experience Cloud-Kunde sind, können Sie Ihre Assets innerhalb von Adobe Experience Manager Assets mit Adobe Creative Cloud synchronisieren und umgekehrt. Sie können Ihre Assets auch mit Experience Cloud synchronisieren und umgekehrt. Sie können diese Synchronisierung durch [!DNL Adobe I/O] einrichten. Der Name [!DNL Adobe Marketing Cloud] wurde in [!DNL Adobe Experience Cloud] geändert.

Der Workflow zur Einrichtung dieser Integration ist:

1. Erstellen Sie über ein öffentliches Gateway eine Authentifizierung in [!DNL Adobe I/O] und rufen Sie eine Anwendungs-ID ab.
1. Erstellen Sie mithilfe der Anwendungs-ID ein Profil auf Ihrer AEM Assets-Instanz.
1. Verwenden Sie diese Konfiguration, um Ihre Assets zu synchronisieren.

Am Backend authentifiziert der AEM-Server Ihr Profil gegenüber dem Gateway und synchronisiert dann die Daten zwischen Assets und Experience Cloud.

>[!NOTE]
>
>Diese Funktion ist in [!DNL Assets] ausgemustert. Ersatzmöglichkeiten finden Sie unter [Best Practices für die Integration von AEM und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). [Bei Fragen wenden Sie sich an den Kunden-Support von Adobe](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-48.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Erstellen eines Programms {#create-an-application}

1. Greifen Sie auf die Adobe Developer Gateway-Schnittstelle zu, indem Sie sich unter [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/) einloggen.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um eine Anwendungs-ID zu erstellen.

1. Navigieren Sie vom linken Fensterbereich aus zu **[!UICONTROL Entwickler-Tools]** > **[!UICONTROL Anwendungen]**, um eine Liste der Anwendungen anzuzeigen.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]** ![aem_assets_addcircle_icon](assets/aem_assets_addcircle_icon.png), um eine Anwendung zu erstellen.
1. Wählen Sie aus der Liste **[!UICONTROL Client-Anmeldeinformationen]** die Option **[!UICONTROL Dienstkonto (JWT-Assertion)]** aus. Dies ist ein Server-zu-Server-Kommunikationsdienst für die Serverauthentifizierung.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Geben Sie einen Namen für die Anwendung und eine optionale Beschreibung an.
1. Wählen Sie aus der Liste **[!UICONTROL Organisation]** die Organisation aus, für die Sie die Assets synchronisieren möchten.
1. Wählen Sie aus der Liste **[!UICONTROL Umfang]** die Optionen **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** und **[!UICONTROL cc-share]** aus.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Eine Meldung informiert Sie darüber, dass die Anwendung erstellt wurde.

   ![Benachrichtigung über die erfolgreiche Erstellung der Anwendung, die AEM Assets mit Creative Cloud integrieren soll](assets/chlimage_1-50.png)

1. Kopieren Sie die **[!UICONTROL Anwendungs-ID]**, die für die neue Anwendung generiert wird.

   >[!CAUTION]
   >
   >Achten Sie darauf, dass Sie nicht versehentlich das **[!UICONTROL Anwendungsgeheimnis]** anstelle der **[!UICONTROL Anwendungs-ID]** kopieren.

## Hinzufügen einer neuen Konfiguration zu Experience Cloud {#add-a-new-configuration}

1. Klicken Sie auf das AEM-Logo in der Benutzeroberfläche in Ihrer lokalen AEM Assets-Instanz und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Legacy-Cloud-Services]**.

1. Suchen Sie den Dienst **[!UICONTROL Adobe Experience Cloud]**. Wenn keine Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Jetzt konfigurieren]**. Wenn Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Konfigurationen anzeigen]** und anschließend auf `+`, um eine neue Konfiguration hinzuzufügen.

   >[!NOTE]
   >
   >Verwenden Sie ein Adobe ID-Konto mit Administratorrechten für die entsprechende Organisation.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die neue Konfiguration an und klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Benennen neuer Konfigurationen für die Integration mit AEM Assets und Creative Cloud](assets/aem-ec-integration-config1.png)

1. Geben Sie im Feld **[!UICONTROL Mandanten-URL]** die URL für AEM Assets ein. Wenn die URL in der Vergangenheit als `https://<tenant_id>.marketing.adobe.com` definiert war, ändern Sie sie in `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Navigieren Sie zu **Tools > Cloud Services > Legacy-Cloud Services**. Klicken Sie unter Adobe Experience Cloud auf **Konfigurationen anzeigen**.
   1. Wählen Sie die zu bearbeitende vorhandene Konfiguration aus. Bearbeiten Sie die Konfiguration und ersetzen Sie `marketing.adobe.com` durch `experiencecloud.adobe.com`.
   1. Speichern Sie die Konfiguration. Testen Sie die Mac-Sync-Replikationsagenten.

1. Fügen Sie im Feld **[!UICONTROL Client-ID]** die Anwendungs-ID ein, die Sie am Ende des Vorgangs zum [Erstellen einer Anwendung](#create-an-application) kopiert haben.

   ![Angeben der erforderlichen Anwendungs-ID-Werte für die Integration von AEM Assets und Creative Cloud](assets/cloudservices_tenant_info.png)

1. Wählen Sie unter **[!UICONTROL Synchronisierung]** die Option **[!UICONTROL Aktiviert]** aus, um die Synchronisierung zu aktivieren, und klicken Sie auf **[!UICONTROL OK]**. Wenn Sie **Deaktiviert** auswählen, erfolgt die Synchronisierung in eine einzige Richtung.

1. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**, um den für Ihre Instanz generierten öffentlichen Schlüssel anzuzeigen. Klicken Sie alternativ dazu auf **[!UICONTROL Öffentlichen Schlüssel für OAuth Gateway herunterladen]**, um die Datei mit dem öffentlichen Schlüssel herunterzuladen. Öffnen Sie dann die Datei, um den öffentlichen Schlüssel anzuzeigen.

## Aktivieren der Synchronisierung {#enable-synchronization}

1. Zeigen Sie den öffentlichen Schlüssel mit einer der folgenden Methoden an, die im letzten Schritt des Verfahrens [Hinzufügen einer neuen Konfiguration zu Experience Cloud](#add-a-new-configuration) erwähnt werden. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**.

1. Kopieren Sie den öffentlichen Schlüssel und fügen Sie ihn im Feld **[!UICONTROL Öffentlicher Schlüssel]** der Konfigurationsoberfläche der Anwendung ein, die Sie unter [Erstellen einer Anwendung](#create-an-application) erstellt haben.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**. Sie können nun Ihre Assets mit der AEM Assets-Instanz synchronisieren.

## Testen der Synchronisierung {#test-the-synchronization}

1. Klicken Sie auf das AEM-Logo in der Benutzeroberfläche in Ihrer lokalen AEM Assets-Instanz und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**, um die für die Synchronisierung erstellten Replikationsprofile zu suchen.
1. Klicken Sie auf der Seite **[!UICONTROL Replikation]** auf **[!UICONTROL Agenten auf Autor]**.
1. Klicken Sie in der Liste der Profile auf das Standardreplikationsprofil zu Ihrer Organisation, um es zu öffnen.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Verbindung testen]**.

   ![Testen der Verbindung und Festlegen des Standardreplikationsprofils zu Ihrer Organisation](assets/chlimage_1-54.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

## Hinzufügen von Benutzern zu Experience Cloud {#add-users-to-experience-cloud}

1. Melden Sie sich mithilfe der Anmeldedaten des Admins bei Experience Cloud an.
1. Gehen Sie über die Leiste zu **[!UICONTROL Administration]** und klicken Sie dann auf **[!UICONTROL Enterprise Dashboard starten]**.
1. Klicken Sie in der Leiste auf **[!UICONTROL Benutzer]**, um die Seite **[!UICONTROL Benutzerverwaltung]** zu öffnen.
1. Klicken Sie in der Symbolleiste auf **Hinzufügen** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Fügen Sie einen oder mehr Benutzer hinzu, denen Sie die Möglichkeit zur Freigabe von Assets für Creative Cloud bereitstellen möchten.

<!-- TBD: Check.
   >[!NOTE]
   >
   >Only the users that you add to Experience Cloud can share assets from AEM Assets to Creative Cloud.

-->

## Austauschen von Assets zwischen AEM Assets und Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Melden Sie sich bei AEM Assets an.
1. Erstellen Sie in der Assets-Konsole einen Ordner und laden Sie einige Assets dort hoch. Erstellen Sie zum Beispiel einen Ordner **mc-demo** und laden Sie ein Asset dort hoch.
1. Wählen Sie den Ordner aus und klicken Sie dann auf **Freigeben.** ![assets_share](assets/do-not-localize/assets_share.png).
1. Wählen Sie im Menü **[!UICONTROL Adobe Experience Cloud]** aus und klicken Sie dann auf **[!UICONTROL Freigeben]**. Eine Meldung benachrichtigt Sie, dass der Ordner für Experience Cloud freigegeben wird.

   >[!NOTE]
   >
   >Die Freigabe eines Asset-Ordners vom Typ `sling:OrderedFolder` wird im Rahmen der Freigabe in Adobe Experience Cloud nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in AEM Assets freigeben möchten, wählen Sie nicht die Option **[!UICONTROL Geordnet]** aus.

1. Aktualisieren Sie die AEM Assets-Benutzeroberfläche. Der von Ihnen in der Assets-Konsole Ihrer lokalen AEM Assets-Instanz erstellte Ordner wird in die Benutzeroberfläche von Experience Cloud kopiert. Das Asset, das Sie in den Ordner in AEM Assets hochladen, wird in der Kopie des Ordners in Experience Cloud angezeigt, nachdem es vom AEM-Server verarbeitet wird.
1. Sie können in der replizierten Kopie des Ordners in Experience Cloud auch ein Asset hochladen. Nach der Verarbeitung wird das Asset im freigegebenen Ordner in AEM Assets angezeigt.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.

## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

>[!CAUTION]
>
>The AEM to Creative Cloud Folder Sharing feature is deprecated. Customers are strongly advised to use newer capabilities, like [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) or [AEM desktop app](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Learn more in [AEM and Creative Cloud Integration Best Practices](/help/assets/aem-cc-integration-best-practices.md).

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/do-not-localize/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Best Practices für die Integration von Assets und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)

