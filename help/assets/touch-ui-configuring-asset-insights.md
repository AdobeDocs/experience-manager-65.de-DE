---
title: Konfigurieren von Asset Insights
description: Konfigurieren Sie Asset Insights in AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 44daaa61f7328e79fd4e11a503b0eef3ff9ffb56

---


# Konfigurieren von Asset Insights {#configure-asset-insights}

Adobe Experience Manager (AEM) Assets ruft Nutzungsdaten rund um AEM-Assets von Websites von Drittanbietern aus Adobe Analytics ab. Um Asset Insights zu aktivieren und diese Daten abzurufen und Statistiken zu erzeugen, konfigurieren Sie zuerst die Funktion zur Integration mit Adobe Analytics.

>[!NOTE]
>
>Einblicke werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in AEM auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insight-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldedaten an, z. B. den Namen Ihres Unternehmens, den Benutzernamen und gemeinsamen geheimen Schlüssel.

   ![Konfigurieren von Adobe Analytics für Asset Insights in AEM](assets/insights_config2.png)

   *Abbildung: Adobe Analytics für Assets Insights in AEM konfigurieren*

1. Tippen/Klicken Sie auf **[!UICONTROL Authentifizieren]**.
1. Nachdem AEM Ihre Anmeldedaten authentifiziert hat, wählen Sie aus der Liste **[!UICONTROL Report Suite]** eine Adobe Analytics Report Suite aus, aus der Asset Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nach der Report Suite-Einrichtung durch AEM klicken/tippen Sie auf **[!UICONTROL Fertig]**.

## Page tracker {#page-tracker}

Nachdem Sie Ihr Adobe Analytics-Konto konfiguriert haben, wird der Seiten-Tracker-Code für Sie generiert. Um Asset Insights zur Verfolgung von AEM-Assets in Websites von Drittanbietern zu aktivieren, beziehen Sie den Seitenverfolgungscode in den Website-Code ein. Verwenden Sie das Seitenverfolgungs-Dienstprogramm in AEM Assets, um den Seitenverfolgungscode zu erzeugen. For more information on how to include your Page Tracker code in third-party web pages, see [Use page tracker and embed code in web pages](/help/assets/touch-ui-using-page-tracker.md).

1. Klicken Sie in AEM auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klicken Sie auf der Seite **[!UICONTROL Navigation]** auf die Karte **[!UICONTROL Insights Page Tracker]**.
1. Click **[!UICONTROL Download]** to download the page tracker code.
