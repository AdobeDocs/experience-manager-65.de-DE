---
title: AEM Assets-Integration mit Experience Cloud und Creative Cloud konfigurieren
seo-title: Konfigurieren der AEM Assets-Integration mit Marketing Cloud und Creative Cloud
description: Erfahren Sie, wie Sie die AEM Assets-Integration mit Experience Cloud und Creative Cloud konfigurieren können.
seo-description: Erfahren Sie, wie Sie die AEM Assets-Integration mit Experience Cloud und Creative Cloud konfigurieren können.
uuid: ec36ea0e-607f-4c73-89df-e095067fccd4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 82a8e807-a2df-4fe3-a68c-2dabc9328eca
docset: aem65
translation-type: tm+mt
source-git-commit: 0560eb8e3c127964920827609a9982acf07b515f
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 67%

---


# AEM Assets-Integration mit Experience Cloud und Creative Cloud konfigurieren {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

Wenn Sie Adobe Experience Cloud-Kunde sind, können Sie Ihre Assets innerhalb von Adobe Experience Manager Assets mit Adobe Creative Cloud synchronisieren und umgekehrt. Sie können Ihre Assets auch mit Experience Cloud synchronisieren und umgekehrt. Sie können diese Synchronisierung über [!DNL Adobe I/O] einrichten.

Der Workflow zur Einrichtung dieser Integration ist:

1. Erstellen Sie eine Authentifizierung in [!DNL Adobe I/O] mithilfe eines öffentlichen Gateways und erhalten Sie eine Anwendungs-ID.
1. Erstellen Sie mit der Anwendungs-ID ein Profil auf Ihrer AEM Assets-Instanz.
1. Verwenden Sie diese Konfiguration zum Synchronisieren Ihrer Assets in AEM Assets mit Creative Cloud.

Am Backend authentifiziert der AEM-Server Ihr Profil gegenüber dem Gateway und synchronisiert dann die Daten zwischen AEM Assets und Experience Cloud.

>[!CAUTION]
>
>Die Funktion der Ordnerfreigabe von AEM zu Creative Cloud wird in AEM Assets nicht unterstützt. Weitere Informationen und Ersetzungen finden Sie unter [Best Practices zur AEM- und Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md).

![Datenfluss, wenn AEM Assets und Creative Cloud integriert werden](assets/chlimage_1-48.png)

Datenfluss, wenn AEM Assets und Creative Cloud integriert werden

>[!NOTE]
>
>Das Freigeben von Assets zwischen Adobe Experience Cloud und Adobe Creative Cloud erfordert Administratorrechte für die AEM-Instanz.

>[!CAUTION]
>
>Adobe Marketing Cloud wurde als Adobe Experience Cloud umbenannt. Die folgenden Verfahren erwähnen noch Marketing Cloud, um die aktuelle Oberfläche widerzuspiegeln. Diese Erwähnungen werden zu einem späteren Zeitpunkt geändert.

## Erstellen einer Anwendung {#create-an-application}

1. Greifen Sie auf die Adobe Developer Gateway-Schnittstelle zu, indem Sie sich unter [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/) einloggen.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um eine Anwendungs-ID zu erstellen.

1. Navigieren Sie im linken Bereich zu **[!UICONTROL Entwicklerwerkzeuge]** > **[!UICONTROL Anwendungen]**, um eine Liste von Anwendungen Ansicht.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]** ![aem_assets_addcircle_icon](assets/aem_assets_addcircle_icon.png), um eine Anwendung zu erstellen.
1. Wählen Sie aus der Liste **[!UICONTROL Client-Anmeldeinformationen]** die Option **[!UICONTROL Dienstkonto (JWT-Assertion)]** aus. Dies ist ein Server-zu-Server-Kommunikationsdienst für die Serverauthentifizierung.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Geben Sie einen Namen für die Anwendung und eine optionale Beschreibung an.
1. Wählen Sie aus der Liste **[!UICONTROL Organisation]** die Organisation aus, für die Sie die Assets synchronisieren möchten.
1. Wählen Sie in der Liste **[!UICONTROL Scope]** **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** und **[!UICONTROL cc-share]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Eine Meldung informiert Sie darüber, dass die Anwendung erstellt wurde.

   ![Benachrichtigung über die erfolgreiche Erstellung der Anwendung, die AEM Assets mit Adobe CC integrieren soll](assets/chlimage_1-50.png)

1. Kopieren Sie die **[!UICONTROL Anwendungs-ID]**, die für die neue Anwendung generiert wird.

   >[!CAUTION]
   >
   >Achten Sie darauf, dass Sie nicht versehentlich das **[!UICONTROL Anwendungsgeheimnis]** anstelle der **[!UICONTROL Anwendungs-ID]** kopieren.

## Hinzufügen einer neuen Konfiguration zu Marketing Cloud {#add-a-new-configuration-to-marketing-cloud}

1. Klicken Sie auf das AEM-Logo in der Benutzeroberfläche in Ihrer lokalen AEM Assets-Instanz und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Legacy-Cloud-Services]**.

1. Suchen Sie den Dienst **[!UICONTROL Adobe Marketing Cloud]**. Wenn keine Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Jetzt konfigurieren]**. Wenn Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Konfigurationen anzeigen]** und klicken Sie auf `+`, um eine neue Konfiguration hinzuzufügen.

   >[!NOTE]
   >
   >Verwenden Sie ein Adobe ID-Konto mit Administratorrechten für die entsprechende Organisation.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die neue Konfiguration an und klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Benennen neuer Konfigurationen für die Integration mit AEM Assets und CC](assets/chlimage_1-51.png)

1. Geben Sie im Feld **[!UICONTROL Mandanten-URL]** die URL für AEM Assets ein.

   >[!CAUTION]
   >
   >Wenn Sie die Tenant-URL als `https://<tenant_id>.marketing.adobe.com` umbenannt haben, müssen Sie sie in `https://<tenant_id>.experiencecloud.adobe.com.` ändern, um dies zu tun, führen Sie die folgenden Schritte aus:
   >
   >1. Navigieren Sie zu **Werkzeuge > Cloud Services > Legacy-Cloud Services**.
   1. Unter „Adobe Marketing Cloud“ klicken Sie auf **Konfigurationen anzeigen**.
   1. Wählen Sie die Konfiguration, die während der Einrichtung der AEM-MAC-CC-Synchronisation erstellt wurde.
   1. Bearbeiten Sie die Cloudservice-Konfiguration und ersetzen Sie **marketing.adobe.com** im Feld &quot;Tenant-URL&quot;durch **experiencecloud.adobe.com**.
   1. Speichern Sie die Konfiguration.
   1. Testen Sie die Mac-Sync-Replikationsagenten.


1. Fügen Sie im Dialogfeld **[!UICONTROL Client-ID]** die Anwendungs-ID ein, die Sie am Ende des Vorgangs zum [Erstellen einer Anwendung](/help/sites-administering/configure-assets-cc-integration.md#create-an-application) kopiert haben.

   ![Angeben der erforderlichen Anwendungs-ID-Werte für die Integration von AEM Assets und Creative Cloud](assets/cloudservices_tenant_info.png)

1. Wählen Sie unter **[!UICONTROL Synchronisierung]** die Option **[!UICONTROL Aktiviert]** aus, um die Synchronisierung zu aktivieren, und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   Wenn Sie **Deaktiviert** auswählen, erfolgt die Synchronisierung in eine einzige Richtung.

1. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**, um den für Ihre Instanz generierten öffentlichen Schlüssel anzuzeigen. Alternativ können Sie auf **[!UICONTROL Öffentlichen Schlüssel für OAuth Gateway herunterladen]** klicken, um die Datei mit dem öffentlichen Schlüssel herunterzuladen. Öffnen Sie dann die Datei, um den öffentlichen Schlüssel anzuzeigen.

## Aktivieren der Synchronisierung  {#enable-synchronization}

1. Zeigen Sie den öffentlichen Schlüssel mit einer der folgenden Methoden an, die im letzten Schritt des Verfahrens [Hinzufügen eine neue Konfiguration auf Marketing Cloud](/help/sites-administering/configure-assets-cc-integration.md#add-a-new-configuration-to-marketing-cloud) erwähnt werden. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Kopieren Sie den öffentlichen Schlüssel und fügen Sie ihn in das Feld **[!UICONTROL Öffentlicher Schlüssel]** der Konfigurationsoberfläche der Anwendung ein, die Sie unter [Anwendung erstellen](/help/sites-administering/configure-assets-cc-integration.md#create-an-application) erstellt haben.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**. Synchronisieren Sie Ihre Assets jetzt mit der AEM Assets-Instanz.

## Testen der Synchronisierung {#test-the-synchronization}

1. Klicken Sie in der Benutzeroberfläche Ihrer lokalen AEM Assets-Instanz auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** **[!UICONTROL Bereitstellung]**> **[!UICONTROL Replikation]**, um die für die Synchronisierung erstellten Replizierungs-Profil zu finden.
1. Klicken Sie auf der Seite **[!UICONTROL Replication]** auf **[!UICONTROL Agenten unter author]**.
1. Klicken Sie in der Liste der Profile auf das Standardreplikationsprofil zu Ihrer Organisation, um es zu öffnen.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Verbindung testen]**.

   ![Testen der Verbindung und Festlegen des Standardreplikationsprofils zu Ihrer Organisation](assets/chlimage_1-54.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

## Benutzer zu Marketing Cloud hinzufügen {#add-users-to-marketing-cloud}

1. Melden Sie sich mithilfe der Anmeldeinformationen des Administrators bei Marketing Cloud an.
1. Wechseln Sie in den Leisten zu **[!UICONTROL Administration]** und klicken Sie dann auf **[!UICONTROL Enterprise Dashboard starten]**.
1. Klicken Sie in der Leiste auf **[!UICONTROL Benutzer]**, um die Seite **[!UICONTROL Benutzerverwaltung]** zu öffnen.
1. Klicken Sie in der Symbolleiste auf/tippen Sie auf **Hinzufügen** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Fügen Sie einen oder mehr Benutzer hinzu, denen Sie die Möglichkeit zur Freigabe von Assets für Creative Cloud bereitstellen möchten.

   >[!NOTE]
   Nur die Benutzer, die Sie zu Marketing Cloud hinzufügen, können Assets von AEM Assets für Creative Cloud freigeben.

## Austauschen von Assets zwischen AEM Assets und Marketing Cloud  {#exchange-assets-between-aem-assets-and-marketing-cloud}

1. Melden Sie sich bei AEM Assets an.
1. Erstellen Sie in der Assets-Konsole einen Ordner und laden Sie einige Assets dort hoch. Erstellen Sie zum Beispiel einen Ordner **mc-demo** und laden Sie ein Asset dort hoch.
1. Wählen Sie den Ordner aus und klicken Sie auf **Freigeben** ![assets_share](assets/assets_share.png).
1. Wählen Sie im Menü **[!UICONTROL Adobe Marketing Cloud]** aus und klicken Sie dann auf **[!UICONTROL Freigeben]**. Eine Meldung benachrichtigt Sie, dass der Ordner für Marketing Cloud freigegeben wird.

   ![chlimage_1-55](assets/chlimage_1-55.png)

   >[!NOTE]
   Die Freigabe eines Asset-Ordners vom Typ `sling:OrderedFolder` wird im Rahmen der Freigabe in Adobe Marketing Cloud nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in AEM Assets freigeben möchten, wählen Sie nicht die Option **[!UICONTROL Geordnet]** aus.

1. Aktualisieren Sie die AEM Assets-Benutzeroberfläche. Der Ordner, den Sie in der Asset-Konsole Ihrer lokalen AEM Assets-Instanz erstellt haben, wird in die Marketing Cloud-Benutzeroberfläche kopiert. Das Asset, das Sie in den Ordner in AEM Assets hochladen, wird in der Ordnerkopie in Marketing Cloud angezeigt, nachdem es vom AEM verarbeitet wurde.
1. Sie können in der replizierten Kopie des Ordners in Marketing Cloud auch ein Asset hochladen. Nach der Verarbeitung wird das Asset im freigegebenen Ordner in AEM Assets angezeigt.

## Austauschen von Assets zwischen AEM Assets und Creative Cloud  {#exchange-assets-between-aem-assets-and-creative-cloud}

>[!CAUTION]
Die Ordnerfreigabe von AEM in Creative Cloud wird nicht mehr unterstützt. Kunden wird dringend empfohlen, neuere Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [AEM Desktop-App](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html) zu verwenden. Weitere Informationen finden Sie unter [Best Practices für die Integration von AEM und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Mit AEM Assets können Sie Ordner mit Assets für Benutzer von Adobe Creative Cloud freigeben.

1. Wählen Sie in der Assets-Konsole den für Creative Cloud freizugebenden Ordner aus.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Freigeben]** ![assets_share](assets/assets_share.png).
1. Wählen Sie in der Liste die Option **[!UICONTROL Adobe Creative Cloud]**.

   >[!NOTE]
   Die Optionen sind für Benutzer mit Leseberechtigungen für das Stammverzeichnis verfügbar. Die Benutzer müssen die erforderlichen Berechtigungen verfügen, um auf die Informationen zum Replikationsagenten von Marketing Cloud zuzugreifen.

1. Fügen Sie auf der Seite **[!UICONTROL Freigeben von Creative Clouden]** den Benutzer hinzu, für den der Ordner freigegeben werden soll, und wählen Sie eine Rolle für den Benutzer aus. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]**.

1. Melden Sie sich mit den Anmeldeinformationen des Benutzers, für den Sie den Ordner freigegeben haben, bei Creative Cloud an. Der freigegebene Ordner ist in Creative Cloud verfügbar.

Die Synchronisierung zwischen AEM Assets und Marketing Cloud ist so gestaltet, dass die Benutzercomputerinstanz, von der das Asset hochgeladen wird, das Recht zur Änderung des Assets behält. Nur diese Änderungen werden in der anderen Instanz eingefügt. 

Wenn zum Beispiel ein Asset von einer AEM Assets-Instanz (vor Ort) hochgeladen wird, werden die von dieser Instanz vorgenommenen Änderungen am Asset in der Marketing Cloud-Instanz aufgefüllt. Die von der Marketing Cloud-Instanz zu demselben Asset vorgenommenen Änderungen werden jedoch nicht an die AEM-Instanz weitergegeben und umgekehrt, wenn ein Asset aus Marketing Cloud hochgeladen wird.

>[!MORELIKETHIS]
* [Best Practices für die Integration von AEM und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)
* [Best Practices für die Ordnerfreigabe aus AEM in Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

