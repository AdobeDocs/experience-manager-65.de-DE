---
title: Konfigurieren Sie Assets Insights für Analysen.
description: Konfigurieren Sie Assets Insights in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Developer, Admin
feature: Asset Insights,Asset Reports
exl-id: 67be0ae6-5939-40fe-bf8a-b8a2c2f68f15
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: a4e1c1f5-18fc-592e-bfc7-453ce6ae0030
    internal-label: Asset Insights
  - id: ac365bec-0634-4744-9473-c42f47320593
    internal-label: Asset management and governance
subfeature_v2:
  - id: c29e3a96-cd2b-4e21-b382-a8279aa04553
    internal-label: Asset reports
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 98%
---
# Konfigurieren von Asset Insights {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] ruft Nutzungsdaten zu digitalen Assets, die von Websites Dritter verwendet werden, von [!DNL Adobe Analytics] ab. Um Asset Insights zu aktivieren und diese Daten abzurufen und Statistiken zu erzeugen, konfigurieren Sie zuerst die Funktion zur Integration mit [!DNL Adobe Analytics]. Um diese Funktion in einer On-Premise-Installation zu verwenden, kaufen Sie die [!DNL Adobe Analytics]-Lizenz separat. Kundinnen und Kunden mit [!DNL Managed Services] erhalten die [!DNL Analytics]-Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldedaten an, z. B. den Namen Ihres Unternehmens, den Benutzernamen und gemeinsamen geheimen Schlüssel.

   ![Konfigurieren von Adobe Analytics für Asset Insights in Experience Manager &#x200B;](assets/insights_config2.png)

   *Abbildung: Konfigurieren von [!DNL Adobe Analytics] für Asset Insights in [!DNL Experience Manager].*

1. Klicken Sie auf **[!UICONTROL Authentifizieren]**.
1. Nachdem [!DNL Experience Manager] Ihre Anmeldedaten authentifiziert hat, wählen Sie aus der Liste **[!UICONTROL Report Suite]** eine Report Suite aus, aus der Asset Insights Daten abrufen soll. [!DNL Adobe Analytics] Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nach der Einrichtung der Report Suite durch [!DNL Experience Manager] klicken Sie auf **[!UICONTROL Fertig]**.

## Seitenverfolgung {#page-tracker}

Nachdem Sie Ihr [!DNL Adobe Analytics]-Konto konfiguriert haben, wird der Seitenverfolgungs-Code für Sie erzeugt. Um Asset Insights zur Verfolgung von [!DNL Experience Manager]-Assets in Websites von Drittanbietern zu aktivieren, schließen Sie den Seitenverfolgungs-Code in den Website-Code ein. Verwenden Sie das Dienstprogramm zur [!UICONTROL Seitenverfolgung] in [!DNL Experience Manager Assets], um den Seitenverfolgungs-Code zu erzeugen. Weitere Informationen dazu, wie Sie Ihren Seitenverfolgungs-Code in Web-Seiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten](/help/assets/use-page-tracker.md).

1. Klicken Sie in [!DNL Experience Manager] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um den Seitenverfolgungs-Code herunterzuladen.
