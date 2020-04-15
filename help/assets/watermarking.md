---
title: Hinzufügen von Wasserzeichen zu digitalen Assets.
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Digitale Assets mit Wasserzeichen versehen {#watermarking}

Mit Adobe Experience Manager (AEM) Assets können Sie Assets ein digitales Wasserzeichen hinzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. AEM Assets unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

To be able to apply watermark on assets, add the watermarking step in the [!UICONTROL DAM Update Asset] workflow.

1. Rufen Sie die AEM-Benutzeroberfläche auf und navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL DAM Update Asset]** workflow and click **[!UICONTROL Edit]**.

1. From the side panel, drag the **[!UICONTROL Add Watermark]** step to the [!UICONTROL DAM Update Asset] workflow.

   ![Ziehen Sie den [!UICONTROL Hinzufügen Wasserzeichenschritt] und fügen Sie dem [!UICONTROL DAM-Update-Asset] -Arbeitsablauf](assets/add_watermark_step_aem_assets.png)2 hinzu
   *Abbildung: Ziehen Sie den[!UICONTROL HinzufügenWasserzeichenschritt]und fügen Sie dem Arbeitsablauf für das[!UICONTROL DAM-Update-Asset]hinzu*

   >[!NOTE]
   >
   >Place the [!UICONTROL Add Watermark] step anywhere before the [!UICONTROL Process Thumbnail] step.

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Tippen oder klicken Sie auf das Symbol „Fertig“, um die Änderungen zu bestätigen.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in Assets](assets/arguments_add_watermark_aem_assets.png)

   *Abbildung: Geben Sie die Argumente im Schritt zum Hinzufügen von Wasserzeichen in Assets an*

1. Save the **[!UICONTROL DAM Update Asset]** workflow with the watermark step.
1. Laden Sie über die Assets-Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit den Werten für Schriftgröße, Farbe usw. an der in den obigen Schritten konfigurierten Position angezeigt.
