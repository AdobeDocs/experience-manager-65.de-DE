---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Asset Management
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 31%

---


# Markieren Sie Ihre digitalen Assets {#watermarking}

[!DNL Adobe Experience Manager Assets] ermöglicht es Ihnen, Assets ein digitales Wasserzeichen hinzuzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Wasserzeichenschritt im Arbeitsablauf [!UICONTROL DAM-Aktualisierung des Assets] hinzu.

1. Rufen Sie die [!DNL Experience Manager]-Benutzeroberfläche auf und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM-Update-Asset]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie im Seitenbedienfeld den Schritt **[!UICONTROL Hinzufügen Wasserzeichen]** in den Arbeitsablauf [!UICONTROL DAM-Update-Asset].

   ![Ziehen Sie den  [!UICONTROL Hinzufügen ] Wassermarkierungsschritt und fügen Sie ihn zum  [!UICONTROL DAM Update ] Asset Workflow hinzu.](assets/add_watermark_step_aem_assets.png)

   *Abbildung: Ziehen Sie den  [!UICONTROL Hinzufügen ] Wassermarkierungsschritt und fügen Sie ihn zum  [!UICONTROL DAM Update ] Asset Workflow hinzu.*

   >[!NOTE]
   >
   >Platzieren Sie den Schritt [!UICONTROL Hinzufügen Wasserzeichen] an einer beliebigen Stelle vor dem Schritt [!UICONTROL Prozessminiatur].

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Abbildung: Geben Sie die Argumente im Schritt Wasserzeichen hinzufügen in  [!DNL Assets]an.*

1. Speichern Sie den Workflow **[!UICONTROL DAM Update Asset]** mit dem Wasserzeichenschritt.
1. Laden Sie in der Benutzeroberfläche [!DNL Assets] ein Beispiel-Asset hoch. Das Wasserzeichen wird mit den Werten für Schriftgröße, Farbe usw. an der in den obigen Schritten konfigurierten Position angezeigt.

Um PDF-Dokumente programmgesteuert oder mit dynamischen Informationen zu versehen, sollten Sie das Angebot [Experience Manager Dokument Services](/help/forms/using/overview-aem-document-services.md) verwenden.

## Tipps und Einschränkungen {#tips-limitations}

* Nur textbasierte Wasserzeichen werden unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie Bilder beim Erstellen des [!UICONTROL Hinzufügen Wasserzeichenprozesses] hochladen können.
* Es werden nur PNG- und JPEG-Dateien als Wasserzeichen unterstützt. Andere Asset-Formate sind nicht mit Wasserzeichen versehen.
