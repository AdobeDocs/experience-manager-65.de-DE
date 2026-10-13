---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: bc0cfb0e-3f70-4377-8831-326a7cae73bd
hide: true
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 100%
---
# Versehen von digitalen Assets mit Wasserzeichen {#watermarking}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/watermark-assets.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

[!DNL Adobe Experience Manager Assets] ermöglicht das Hinzufügen eines digitalen Wasserzeichens zu Assets, mit dem Benutzende die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Schritt „Wasserzeichen“ im Workflow [!UICONTROL DAM-Update-Asset] hinzu.

1. Öffnen Sie die [!DNL Experience Manager]-Benutzeroberfläche und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]** aus dem seitlichen Bedienfeld in den Workflow [!UICONTROL DAM-Update-Asset].

   ![Fügen Sie den Schritt [!UICONTROL Wasserzeichen hinzufügen] durch Ziehen zum Workflow [!UICONTROL DAM-Update-Asset] ](assets/add_watermark_step_aem_assets.png) hinzu.

   *Abbildung: Ziehen Sie den Schritt [!UICONTROL Wasserzeichen hinzufügen] und fügen Sie ihn zum Workflow [!UICONTROL DAM-Update-Asset] hinzu.*

   >[!NOTE]
   >
   >Ordnen Sie den Schritt [!UICONTROL Wasserzeichen hinzufügen] an beliebiger Stelle vor dem Schritt [!UICONTROL Miniaturansichten verarbeiten] ein.

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]** zum Anzeigen der Eigenschaften.
1. Geben Sie auf der Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an, einschließlich Text, Schriftart, Größe, Farbe, Position, Ausrichtung usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Abbildung: Stellen Sie die Argumente im Schritt „Wasserzeichen hinzufügen“ in [!DNL Assets] bereit.*

1. Speichern Sie den Workflow **[!UICONTROL DAM-Update-Asset]** mit dem Schritt „Wasserzeichen“.
1. Laden Sie über die [!DNL Assets]-Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit den Werten für Schriftgrad und Farbe an der in den obigen Schritten konfigurierten Position angezeigt.

Wenn Sie PDF-Dokumente programmgesteuert oder mit dynamischen Informationen mit Wasserzeichen versehen möchten, sollten Sie [Experience Manager Document Services](/help/forms/using/overview-aem-document-services.md) nutzen.

## Tipps und Einschränkungen {#tips-limitations}

* Es werden nur textbasierte Wasserzeichen unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie beim Erstellen des Prozesses [!UICONTROL Wasserzeichen hinzufügen] Bilder hochladen können.
* Nur PNG- und JPEG-Dateien können mit Wasserzeichen versehen werden. Andere Asset-Formate werden nicht mit Wasserzeichen versehen.
