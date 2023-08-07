---
title: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 087bc811-e8f8-4db5-b066-627a9b082f57
hide: true
source-git-commit: 6f01f5725ed2b0533756830c1a5e55b7464708f6
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Installieren des [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-install.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Ein Benutzer mit Adminzugriff in [!DNL Adobe Experience Manager] installiert den erweiterten Connector. Überprüfen Sie vor der Installation die Plattformunterstützung und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe erfordert die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt die Versionen 1.7.4 und höher des erweiterten Connectors. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Um die Version des erweiterten Connectors zu überprüfen, gehen Sie zu der Gruppe `digital.hoodoo`, die im linken Fensterbereich des [Package Managers](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) verfügbar ist.
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie im [Prüfungshandbuch](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

Gehen Sie wie folgt vor, um den Connector zu installieren:

1. Laden Sie den Connector von [[!DNL Software Distribution] link](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip) herunter.
1. [Konfigurieren der Firewall](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html?lang=de).
1. Erlauben Sie auf dem Dispatcher die HTTP-Header `authorization`, `username` und `apikey`. Lassen Sie `GET`-, `POST`- und `PUT`-Anfragen an `/bin/workfront-tools` zu.
1. Stellen Sie sicher, dass die folgenden Pfade nicht im [!DNL Experience Manager]-Repository vorhanden sind:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Installieren Sie das Paket mit dem [!UICONTROL Package Manager]. Informationen zum Installieren von Paketen finden Sie unter [Dokumentation zum Package Manager](/help/sites-administering/package-manager.md).
1. Erstellen Sie `wf-workfront-users` in den [!DNL Experience Manager]-Benutzergruppen und weisen Sie `/content/dam` die Berechtigung `jcr:all` zu.

Ein `workfront-tools`-Systembenutzer wird automatisch erstellt und die erforderlichen Berechtigungen werden automatisch verwaltet. Alle Benutzer von [!DNL Workfront], die den Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

## Konfigurieren der Verbindung zwischen [!DNL Experience Manager] und [!DNL Workfront] {#configure-connection}

Um eine Verbindung mit Workfront zu erstellen, führen Sie die folgenden Schritte aus:

1. Wählen Sie in [!DNL Experience Manager] die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]**.

1. Wählen Sie `workfront-tools` im linken Bedienfeld aus und wählen Sie **[!UICONTROL Erstellen]** oben rechts auf der Seite.

1. Tragen Sie im Dialogfeld **[!UICONTROL Workfront-Verbindung]** die erforderlichen Details für Ihre [!DNL Workfront]-Bereitstellung ein und wählen Sie die Option **[!UICONTROL Mit Workfront verbinden]**. Sobald die Verbindung erfolgreich hergestellt wurde, wird die benutzerdefinierte Dokumentenintegration von [!DNL Workfront] automatisch in der [!DNL Workfront]-Umgebung erstellt.

   ![Verbinden Sie [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Um die Verbindung zu überprüfen, greifen Sie in [!DNL Workfront] darauf zu und stellen Sie sicher, dass der API-Schlüssel derselbe ist und dass die Verbindung **[!UICONTROL aktiviert]** ist. Wählen Sie dazu **[!UICONTROL Einrichtung]** > **[!UICONTROL Dokumente]** > **[!UICONTROL Benutzerdefinierte Integrationen]** in [!DNL Workfront] aus.

## Aktualisieren [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

Mit Experience Manager Assets können Sie den [!DNL Workfront for Experience Manager enhanced connector] von einer früheren Version auf die neueste Version aktualisieren.

So aktualisieren Sie den [!DNL Workfront for Experience Manager enhanced connector] auf die neueste Version:

1. Laden Sie die neueste Version des erweiterten Connectors von [[!DNL Software Distribution] link](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip) herunter.
1. Installieren Sie das Paket mit dem [!UICONTROL Package Manager]. Informationen zum Installieren von Paketen finden Sie unter [Dokumentation zum Package Manager](/help/sites-administering/package-manager.md).
