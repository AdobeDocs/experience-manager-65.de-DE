---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: bc0cfb0e-3f70-4377-8831-326a7cae73bd
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 31%

---

# Digitale Assets mit Wasserzeichen versehen {#watermarking}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/watermark-assets.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/watermarking.html?lang=en) |

[!DNL Adobe Experience Manager Assets] ermöglicht das Hinzufügen eines digitalen Wasserzeichens zu Assets, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Schritt &quot;Wasserzeichen&quot;im [!UICONTROL DAM-Update-Asset] Arbeitsablauf.

1. Zugriff auf [!DNL Experience Manager] Benutzeroberfläche und navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Aus dem **[!UICONTROL Workflow-Modelle]** Seite, wählen Sie die **[!UICONTROL DAM-Update-Asset]** Workflow und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie aus dem seitlichen Bedienfeld die **[!UICONTROL Wasserzeichen hinzufügen]** Schritt zum [!UICONTROL DAM-Update-Asset] Arbeitsablauf.

   ![Ziehen Sie die [!UICONTROL Wasserzeichen hinzufügen] und fügen Sie zum [!UICONTROL DAM-Update-Asset] Workflow](assets/add_watermark_step_aem_assets.png)

   *Abbildung: Ziehen Sie die [!UICONTROL Wasserzeichen hinzufügen] und fügen Sie zum [!UICONTROL DAM-Update-Asset] Arbeitsablauf.*

   >[!NOTE]
   >
   >Platzieren Sie die [!UICONTROL Wasserzeichen hinzufügen] Schritt an einer beliebigen Stelle vor [!UICONTROL Prozessminiatur] Schritt.

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Abbildung: Geben Sie die Argumente im Schritt &quot;Wasserzeichen hinzufügen&quot;in [!DNL Assets].*

1. Speichern Sie die **[!UICONTROL DAM-Update-Asset]** Arbeitsablauf mit dem Wasserzeichenschritt.
1. Aus dem [!DNL Assets] -Benutzeroberfläche ein Beispiel-Asset hochladen. Das Wasserzeichen wird mit den Werten für Schriftgröße, Farbe usw. an der in den obigen Schritten konfigurierten Position angezeigt.

Wenn Sie Dokumente mit Wasserzeichen-PDF programmgesteuert oder mit dynamischen Informationen versehen möchten, sollten Sie die Verwendung von [Experience Manager Document Services](/help/forms/using/overview-aem-document-services.md) anbieten.

## Tipps und Einschränkungen {#tips-limitations}

* Es werden nur textbasierte Wasserzeichen unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie beim Erstellen der [!UICONTROL Wasserzeichenprozess hinzufügen].
* Nur PNG- und JPEG-Dateien werden als Wasserzeichen unterstützt. Andere Asset-Formate sind nicht mit Wasserzeichen versehen.
