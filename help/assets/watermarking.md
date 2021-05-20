---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Asset-Verwaltung
exl-id: bc0cfb0e-3f70-4377-8831-326a7cae73bd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 31%

---

# Digitale Assets mit Wasserzeichen versehen {#watermarking}

[!DNL Adobe Experience Manager Assets] ermöglicht das Hinzufügen eines digitalen Wasserzeichens zu Assets, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Schritt &quot;Wasserzeichen&quot;im Workflow [!UICONTROL DAM-Update-Asset] hinzu.

1. Rufen Sie die [!DNL Experience Manager]-Benutzeroberfläche auf und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie den Schritt **[!UICONTROL Wasserzeichen]** aus dem seitlichen Bedienfeld in den Workflow [!UICONTROL DAM-Update-Asset] .

   ![Ziehen Sie den Schritt  [!UICONTROL Wasserzeichen ] hinzufügen und fügen Sie ihn zum Workflow  [!UICONTROL DAM-Update-] Asset hinzu.](assets/add_watermark_step_aem_assets.png)

   *Abbildung: Ziehen Sie den Schritt  [!UICONTROL Wasserzeichen ] hinzufügen und fügen Sie ihn zum Workflow  [!UICONTROL DAM-Update-] Asset hinzu.*

   >[!NOTE]
   >
   >Platzieren Sie den Schritt [!UICONTROL Wasserzeichen] an einer beliebigen Stelle vor dem Schritt [!UICONTROL Prozessminiatur] .

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Abbildung: Geben Sie die Argumente im Schritt &quot;Wasserzeichen hinzufügen&quot;in  [!DNL Assets]an.*

1. Speichern Sie den Workflow **[!UICONTROL DAM-Update-Asset]** mit dem Wasserzeichenschritt.
1. Laden Sie in der Benutzeroberfläche [!DNL Assets] ein Beispiel-Asset hoch. Das Wasserzeichen wird mit den Werten für Schriftgröße, Farbe usw. an der in den obigen Schritten konfigurierten Position angezeigt.

Wenn Sie PDF-Dokumente programmatisch oder mit dynamischen Informationen mit Wasserzeichen versehen möchten, sollten Sie das Angebot [Experience Manager Document Services](/help/forms/using/overview-aem-document-services.md) in Erwägung ziehen.

## Tipps und Einschränkungen {#tips-limitations}

* Es werden nur textbasierte Wasserzeichen unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie Bilder beim Erstellen des [!UICONTROL Wasserzeichenprozesses hinzufügen] hochladen können.
* Nur PNG- und JPEG-Dateien werden als Wasserzeichen unterstützt. Andere Asset-Formate sind nicht mit Wasserzeichen versehen.
