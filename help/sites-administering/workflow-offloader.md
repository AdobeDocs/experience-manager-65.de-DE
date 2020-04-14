---
title: Offloader für Assets-Workflows
seo-title: Offloader für Assets-Workflows
description: Informieren Sie sich über den Offloader für Assets-Workflows.
seo-description: Informieren Sie sich über den Offloader für Assets-Workflows.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Offloader für Assets-Workflows{#assets-workflow-offloader}

Mit dem Offloader für Assets-Workflows können Sie es ermöglichen, dass mehrere Instanzen von Adobe Experience Manager (AEM) Assets die Verarbeitungslast auf der primären (führenden) Instanz reduzieren. Die Verarbeitungslast wird unter der führenden Instanz und den verschiedenen Offloader-Instanzen (Arbeiterinstanzen), die Sie hinzufügen, aufgeteilt. Die Verteilung der Verarbeitungslast von Assets erhöht die Effizienz und Geschwindigkeit, mit der Assets in AEM Assets verarbeitet werden. Darüber hinaus unterstützt dieser Ansatz die Zuteilung von dedizierten Ressourcen, um Assets eines bestimmten MIME-Typs zu verarbeiten. Beispielsweise können Sie festlegen, dass ein bestimmter Knoten in Ihrer Topologie ausschließlich InDesign-Assets verarbeitet.

## Konfigurieren der Offloader-Topologie {#configure-offloader-topology}

Verwenden Sie Configuration Manager, um die URL für die Füllzeicheninstanz und die Hostnamen von offloader-Instanzen für Verbindungsanforderungen in der Füllzeicheninstanz hinzuzufügen.

1. Tap/click the AEM logo, and choose **Tools** > **Operations** > **Web Console** to open Configuration Manager.
1. From the Web Console, select **Sling** >  **Topology Management**.

   ![chlimage_1-44](assets/chlimage_1-44a.png)

1. In the Topology Management page, tap/click the **Configure Discovery.Oak Service** link.

   ![chlimage_1-45](assets/chlimage_1-45a.png)

1. In the Discovery Service Configuration page, specify the connector URL for the leader instance in the **Topology Connector URLs** field.

   ![chlimage_1-46](assets/chlimage_1-46a.png)

1. In the **Topology Connector Whitelist** field, specify IP address or host names of offloader instances that are allowed to connect with the leader instance. Tippen/Klicken Sie auf **Speichern**.

   ![chlimage_1-47](assets/chlimage_1-47a.png)

1. Um die Offloader-Instanzen anzuzeigen, die mit der führenden Instanz verbunden sind, gehen Sie zu **Tools** > **Bereitstellung** > **Topologie** und tippen oder klicken Sie auf die Cluster-Ansicht.

## Deaktivieren des Abladens {#disable-offloading}

1. Tap/click the AEM logo, and choose **Tools** > **Deployment** > **Offloading**. The **Offloading Browser** page displays topics and the server instances that can consume the topics.

   ![chlimage_1-48](assets/chlimage_1-48a.png)

1. Disable the *com/adobe/granite/workflow/offloading* topic on the leader instances with which users interact to upload or change AEM assets.

   ![chlimage_1-49](assets/chlimage_1-49a.png)

## Konfigurieren von Workflow-Startern auf der führenden Instanz {#configure-workflow-launchers-on-the-leader-instance}

Configure workflow launchers to use the [!UICONTROL DAM Update Asset Offloading] workflow on the leader instance instead of the **Dam Update Asset** workflow.

1. Tap/click the AEM logo, and choose, **Tools** > **Workflow** > **Launchers** to open the **Workflow Launchers** console.

   ![chlimage_1-50](assets/chlimage_1-50a.png)

1. Locate the two Launcher configurations with event type **Node Created** and **Node Modified** respectively, which run the **DAM Update Asset** workflow.
1. For each configuration, select the checkbox before it and tap/click the **View Properties** icon from the toolbar to display the **Launcher Properties** dialog.

   ![chlimage_1-51](assets/chlimage_1-51a.png)

1. From the **Workflow** list, choose [!UICONTROL DAM Update Asset Offloading] and tap/click **Save**.

   ![chlimage_1-52](assets/chlimage_1-52a.png)

1. Tap/click the AEM logo, and choose, **Tools** > **Workflow** > **Models** to open the **Workflow Models** page.
1. Select the [!UICONTROL DAM Update Asset Offloading] workflow, and tap/click **Edit** from the toolbar to display its details.

   ![chlimage_1-53](assets/chlimage_1-53a.png)

1. Display the context menu for the **DAM Workflow Offloading** step, and choose **Edit**. Überprüfen Sie den Eintrag im Feld **Auftragsthema** auf der Registerkarte **Generische Argumente** des Konfigurationsdialogfelds.

   ![chlimage_1-54](assets/chlimage_1-54a.png)

## Deaktivieren der Workflow-Starter auf den Offloader-Instanzen {#disable-the-workflow-launchers-on-the-offloader-instances}

Disable the workflow launchers that run the **DAM Update Asset** workflow on the leader instance.

1. Tap/click the AEM logo, and choose, **Tools** > **Workflow** > **Launchers** to open the **Workflow Launchers** console.

   ![chlimage_1-55](assets/chlimage_1-55a.png)

1. Locate the two Launcher configurations with event type **Node Created** and **Node Modified** respectively, which run the **DAM Update Asset** workflow.
1. For each configuration, select the checkbox before it and tap/click the **View Properties** icon from the toolbar to display the **Launcher Properties** dialog.

   ![chlimage_1-56](assets/chlimage_1-56a.png)

1. In the **Activate** section, drag the slider to disable the workflow launcher and tap/click **Save** to disable it.

   ![chlimage_1-57](assets/chlimage_1-57a.png)

1. Laden Sie alle Assets vom Typ image in die Füllzeicheninstanz hoch. Überprüfen Sie, welche Miniaturansichten für das Asset von der abgeladenen Instanz generiert und zurückportiert wurden.

