---
title: Konfigurieren Sie Assets Insights für Analysen.
description: Konfigurieren von Asset Insights in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Architect, Admin
feature: Asset Insights,Asset Reports
exl-id: 67be0ae6-5939-40fe-bf8a-b8a2c2f68f15
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 44%

---

# Konfigurieren von Asset Insights {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] ruft Nutzungsdaten zu digitalen Assets, die von Websites Dritter verwendet werden, von [!DNL Adobe Analytics] ab. Um Asset Insights zu aktivieren und diese Daten abzurufen und Statistiken zu erzeugen, konfigurieren Sie zuerst die Funktion zur Integration mit [!DNL Adobe Analytics]. Um diese Funktion in einer On-Premise-Installation zu verwenden, kaufen Sie [!DNL Adobe Analytics] -Lizenz getrennt. Kunden mit [!DNL Managed Services] receive [!DNL Analytics] Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldedaten an, z. B. den Namen Ihres Unternehmens, den Benutzernamen und gemeinsamen geheimen Schlüssel.

   ![Konfigurieren von Adobe Analytics für Asset Insights in Experience Manager](assets/insights_config2.png)

   *Abbildung: Konfigurieren [!DNL Adobe Analytics] für Asset Insights in [!DNL Experience Manager].*

1. Klicken Sie auf **[!UICONTROL Authentifizieren]**.
1. Nachher [!DNL Experience Manager] authentifiziert Ihre Anmeldedaten über die **[!UICONTROL Report Suite]** Liste, wählen Sie eine [!DNL Adobe Analytics] Report Suite, aus der Assets Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nach der Einrichtung der Report Suite durch [!DNL Experience Manager] klicken Sie auf **[!UICONTROL Fertig]**.

## Seitenverfolgung {#page-tracker}

Nachdem Sie die [!DNL Adobe Analytics] -Konto, wird der Seitenverfolgungs-Code für Sie generiert. So aktivieren Sie die Verfolgung durch Assets Insights [!DNL Experience Manager] -Assets, die auf Websites von Drittanbietern verwendet werden, enthalten den Seiten-Tracker-Code im Website-Code. Verwenden Sie die [!UICONTROL Seitenverfolgung] Dienstprogramm in [!DNL Experience Manager Assets] , um den Seiten-Tracker-Code zu generieren. Weitere Informationen dazu, wie Sie Ihren Seitenverfolgungs-Code in Webseiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden des Seitentrackers und des Einbettungscodes in Webseiten](/help/assets/use-page-tracker.md).

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um den Seitenverfolgungs-Code herunterzuladen.
