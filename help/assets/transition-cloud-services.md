---
title: Übersetzungsdienst auf Ordner anwenden
description: Übersetzungsdienst auf Ordner anwenden
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Apply translation cloud services to folders {#applying-translation-cloud-services-to-folders}

Mit Adobe Experience Manager (AEM) können Sie von cloudbasierten Übersetzungsdiensten von Ihrem bevorzugten Übersetzungsanbieter Gebrauch machen, um sicherzustellen, dass Ihre Assets basierend auf Ihren Anforderungen übersetzt werden.

Sie können den Übersetzungs-Cloud-Service direkt auf Ihren Asset-Ordner anwenden, sodass die Assets in den Übersetzungs-Workflows verwendet werden können.

## Übersetzungsdienste anwenden {#applying-the-translation-services}

Durch die direkte Anwendung der Übersetzungs-Cloud-Services auf Ihren Assets-Folder entfällt die Notwendigkeit, Übersetzungsdienste zu konfigurieren, wenn Sie Übersetzungs-Workflows erstellen oder aktualisieren.

1. Wählen Sie in der Benutzeroberfläche &quot;Assets&quot;den Ordner aus, auf den Sie Übersetzungsdienste anwenden möchten.
1. Klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**, um die Seite **[!UICONTROL Ordnereigenschaften]** anzuzeigen.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Cloud-Services]**.
1. Wählen Sie in der Liste &quot;Cloud-Dienstkonfigurationen&quot;den gewünschten Übersetzungsanbieter aus. Wenn Sie beispielsweise Übersetzungsdienste von Microsoft nutzen möchten, wählen Sie **[!UICONTROL Microsoft Translator]** aus.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Wählen Sie den Connector für den Übersetzungsanbieter aus.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Speichern]** und klicken Sie anschließend auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Der Übersetzungsdienst wird auf den Ordner angewendet.

## Benutzerdefinierten Übersetzungs-Connector anwenden {#applying-custom-translation-connector}

Wenn Sie einen benutzerdefinierten Connector für die Übersetzungs-Services anwenden möchten, die in Übersetzungs-Workflows verwendet werden sollen. Um einen benutzerdefinierten Connector anzuwenden, installieren Sie den Connector zunächst über Package Manager. Konfigurieren Sie den Connector anschließend über die Konsole „Cloud-Services“. Wenn Sie den Connector konfiguriert haben, ist er in der Connector-Liste in der Registerkarte „Cloud-Services“ verfügbar. Die Beschreibung hierzu finden Sie unter [Anwenden der Übersetzungsdienste](transition-cloud-services.md#applying-the-translation-services). Wenn Sie den benutzerdefinierten Connector anwenden und Übersetzungs-Workflows ausführen, werden die Connector-Details in der Kachel **[!UICONTROL Zusammenfassung der Übersetzung]** des Übersetzungsprojekts unter den Überschriften **[!UICONTROL Anbieter]** und **[!UICONTROL Methode]** angezeigt.

1. Installieren Sie den Connector von Package Manager.
1. Klicken oder tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools > Bereitstellung > Cloud-Services]**.
1. Locate the connector you installed under **[!UICONTROL Third Party Services]** in the **[!UICONTROL Cloud Services]** page.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Klicken/tippen Sie auf den Link **[!UICONTROL Jetzt konfigurieren]**, um das Dialogfeld **[!UICONTROL Konfiguration erstellen]** zu öffnen.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Geben Sie einen Titel und einen Namen für den Connector ein und klicken/tippen Sie dann auf **[!UICONTROL Erstellen]**. The custom connector is available in the list of connectors in the **[!UICONTROL Cloud Services]** tab described in step 5 of [Applying the translation services](#applying-the-translation-services).
1. Führen Sie einen beliebigen unter [Erstellen von Übersetzungsprojekten](translation-projects.md) beschriebenen Übersetzungs-Workflow aus, wenn Sie den benutzerdefinierten Connector angewendet haben. Verify the details of the connector in the **[!UICONTROL Translation Summary]** tile of the translation project in the **[!UICONTROL Projects]** console.

   ![chlimage_1-220](assets/chlimage_1-220.png)
