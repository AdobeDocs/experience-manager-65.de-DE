---
title: Installieren [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 087bc811-e8f8-4db5-b066-627a9b082f57
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 49%

---

# Installieren des [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-install.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-connector-install.html?lang=en) |

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager]  installiert den erweiterten Connector. Überprüfen Sie vor der Installation die Plattformunterstützung und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe fordert, dass die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services] durchgeführt wird. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt erweiterte Connector-Versionen 1.7.4 und höher. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Navigieren Sie zur erweiterten Connector-Version, um sie zu überprüfen. `digital.hoodoo` im linken Bereich in [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de).
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie unter [Prüfungsleitfaden](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


Gehen Sie wie folgt vor, um den Connector zu installieren:

1. Herunterladen des Connectors von [[!DNL Software Distribution] link](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. [Konfigurieren der Firewall](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html?lang=de).
1. Lassen Sie im Dispatcher HTTP-Kopfzeilen zu, die `authorization`, `username` und `apikey` heißen. Lassen Sie `GET`-, `POST`- und `PUT`-Anfragen an `/bin/workfront-tools` zu.
1. Stellen Sie sicher, dass die folgenden Pfade nicht im [!DNL Experience Manager]-Repository vorhanden sind:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Installieren Sie das Paket mit [!UICONTROL Package Manager]. Informationen zum Installieren von Paketen finden Sie unter [Package Manager-Dokumentation](/help/sites-administering/package-manager.md).
1. Erstellen `wf-workfront-users` in [!DNL Experience Manager] Benutzergruppe und Berechtigung zuweisen `jcr:all` nach `/content/dam`.

Ein `workfront-tools`-Systembenutzer wird automatisch erstellt und die erforderlichen Berechtigungen werden automatisch verwaltet. Alle Benutzer von [!DNL Workfront] die den Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

## Konfigurieren Sie die Verbindung zwischen [!DNL Experience Manager] und [!DNL Workfront] {#configure-connection}

Gehen Sie wie folgt vor, um eine Verbindung mit Workfront herzustellen:

1. Wählen Sie in [!DNL Experience Manager] die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]**.

1. Wählen Sie `workfront-tools` im linken Bedienfeld aus und wählen Sie **[!UICONTROL Erstellen]** oben rechts auf der Seite.

1. Tragen Sie im Dialogfeld **[!UICONTROL Workfront-Verbindung]** die erforderlichen Details für Ihre [!DNL Workfront]-Bereitstellung ein und wählen Sie die Option **[!UICONTROL Mit Workfront verbinden]**. Sobald die Verbindung erfolgreich hergestellt wurde, wird die benutzerdefinierte Dokumentenintegration von [!DNL Workfront] automatisch in der [!DNL Workfront]-Umgebung erstellt.

   ![Verbinden Sie [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Um die Verbindung zu überprüfen, greifen Sie darauf zu unter [!DNL Workfront] und überprüfen Sie, ob der API-Schlüssel identisch ist und ob die Verbindung **[!UICONTROL Aktiviert]**. Wählen Sie dazu **[!UICONTROL Einrichtung]** > **[!UICONTROL Dokumente]** > **[!UICONTROL Benutzerdefinierte Integrationen]** in [!DNL Workfront].

## Aktualisieren [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

Mit Experience Manager Assets können Sie die [!DNL Workfront for Experience Manager enhanced connector] von einer vorherigen Version zur neuesten Version.

So aktualisieren Sie die [!DNL Workfront for Experience Manager enhanced connector] auf die neueste Version:

1. Laden Sie die neueste Version des erweiterten Connectors von herunter. [[!DNL Software Distribution] link](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. Installieren Sie das Paket mit [!UICONTROL Package Manager]. Informationen zum Installieren von Paketen finden Sie unter [Package Manager-Dokumentation](/help/sites-administering/package-manager.md).
