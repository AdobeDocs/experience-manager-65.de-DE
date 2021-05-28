---
title: Konfigurieren Sie Assets Insights für Analysen.
description: Konfigurieren Sie Assets Insights in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Architect, Administrator
feature: Asset Insights,Asset-Berichte
exl-id: 67be0ae6-5939-40fe-bf8a-b8a2c2f68f15
source-git-commit: 68c36d4e3a14567a4d115ee64a4474bcaf9aa386
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 29%

---

# Konfigurieren von Assets Insights {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] ruft Nutzungsdaten zu digitalen Assets, die von Websites Dritter verwendet werden, von [!DNL Adobe Analytics] ab. Damit Assets Insights diese Daten abrufen und Einblicke generieren kann, konfigurieren Sie zunächst die Funktion zur Integration mit [!DNL Adobe Analytics]. Um diese Funktion in einer On-Premise-Installation zu verwenden, erwerben Sie die Lizenz [!DNL Adobe Analytics] separat. Kunden mit [!DNL Managed Services] erhalten die [!DNL Analytics] -Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldedaten an, z. B. den Namen Ihres Unternehmens, den Benutzernamen und gemeinsamen geheimen Schlüssel.

   ![Konfigurieren von Adobe Analytics für Asset Insights in Experience Manager](assets/insights_config2.png)

   *Abbildung: Konfigurieren Sie  [!DNL Adobe Analytics] für Assets Insights in  [!DNL Experience Manager].*

1. Klicken Sie auf **[!UICONTROL Authenticate]**.
1. Nachdem [!DNL Experience Manager] Ihre Anmeldedaten authentifiziert hat, wählen Sie in der Liste **[!UICONTROL Report Suite]** eine [!DNL Adobe Analytics] Report Suite aus, von der aus Assets Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nachdem [!DNL Experience Manager] Ihre Report Suite eingerichtet hat, klicken Sie auf **[!UICONTROL Fertig]**.

## Seitenverfolgung {#page-tracker}

Nachdem Sie Ihr [!DNL Adobe Analytics]-Konto konfiguriert haben, wird der Seitenverfolgungs-Code für Sie generiert. Damit Assets Insights die [!DNL Experience Manager]-Assets verfolgen kann, die auf Drittanbieter-Websites verwendet werden, fügen Sie den Seiten-Tracker-Code in den Website-Code ein. Verwenden Sie das Dienstprogramm [!UICONTROL Seitenverfolgung] in [!DNL Experience Manager Assets], um den Seitenverfolgungs-Code zu generieren. Weitere Informationen dazu, wie Sie Ihren Seitenverfolgungs-Code in Webseiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungscode in Webseiten](/help/assets/use-page-tracker.md).

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um den Seitenverfolgungs-Code herunterzuladen.
