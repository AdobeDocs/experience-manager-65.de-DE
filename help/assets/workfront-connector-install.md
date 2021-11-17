---
title: Installieren [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
source-git-commit: 468a8d96153c67232524eea6f180c9ceb364d60a
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Installieren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager] installiert den erweiterten Connector. Überprüfen Sie vor der Installation den Plattformsupport und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe erfordert Bereitstellung und Konfiguration der [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird ohne zertifizierten Partner bereitgestellt und konfiguriert oder [!DNL Adobe Professional Services], wird sie von Adobe nicht unterstützt.
>
>Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager] die diesen Connector redundant macht; In diesem Fall kann es erforderlich sein, dass Kunden von der Verwendung dieses Connectors übergehen.

Gehen Sie wie folgt vor, um den Connector zu installieren:

1. Herunterladen des Connectors von [[!DNL Software Distribution] link](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [Konfigurieren der Firewall](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html).

1. Lassen Sie im Dispatcher HTTP-Header zu, die `authorization`, `username`und `apikey`. Zulassen `GET`, `POST`und `PUT` Anforderungen an `/bin/workfront-tools`.

1. Stellen Sie sicher, dass die folgenden Pfade in [!DNL Experience Manager] repository:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Installieren Sie das Paket mit [!UICONTROL Package Manager]. Informationen zum Installieren von Paketen finden Sie unter [Package Manager-Dokumentation](/help/sites-administering/package-manager.md).

1. Erstellen `wf-workfront-users` in [!DNL Experience Manager] Benutzergruppe und Berechtigung zuweisen `jcr:all` nach `/content/dam`.

Ein Systembenutzer `workfront-tools` automatisch erstellt wird und die erforderlichen Berechtigungen automatisch verwaltet werden. Alle Benutzer von [!DNL Workfront] die den Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

## Konfigurieren Sie die Verbindung zwischen [!DNL Experience Manager] und [!DNL Workfront] {#configure-connection}

Gehen Sie wie folgt vor, um eine Verbindung mit Workfront herzustellen:

1. In [!DNL Experience Manager]auswählen **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]**.

1. Auswählen `workfront-tools` im linken Bereich und wählen Sie **[!UICONTROL Erstellen]** im rechten oberen Bereich der Seite.

1. Im **[!UICONTROL Workfront-Verbindung]** -Dialogfeld die erforderlichen Details für Ihre [!DNL Workfront] Bereitstellung und Auswahl **[!UICONTROL Verbindung zu Workfront herstellen]** -Option. Sobald die Verbindung erfolgreich hergestellt wurde, wird die [!DNL Workfront] Die benutzerdefinierte Dokumentenintegration wird automatisch im [!DNL Workfront] Umgebung.

   ![Verbinden [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Um die Verbindung zu überprüfen, greifen Sie darauf zu unter [!DNL Workfront] und überprüfen Sie, ob der API-Schlüssel identisch ist und ob die Verbindung **[!UICONTROL Aktiviert]**. Wählen Sie dazu **[!UICONTROL Einrichtung]** > **[!UICONTROL Dokumente]** > **[!UICONTROL Benutzerdefinierte Integrationen]** in [!DNL Workfront].
