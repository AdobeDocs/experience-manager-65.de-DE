---
title: Assets Insights
description: Erfahren Sie, wie Sie mit der Funktion "Asset Insights"Benutzerbewertungen und Nutzungsstatistiken von Bildern verfolgen können, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen der Adobe verwendet werden.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 0130ac40-a72b-4caf-a10f-3c7d76eaa1e6
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 64%

---

# Assets Insights {#asset-insights}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klicken Sie hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/assets-insights.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Klicken Sie hier](https://experienceleague.adobe.com/docs/experience-manager-64/assets/managing/touch-ui-configuring-asset-insights.html?lang=en) |

Mit der Funktion Assets Insights können Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern verfolgen, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen der Adobe verwendet werden. Sie hilft, Erkenntnisse über ihre Leistung und Beliebtheit abzuleiten.

[!DNL Assets] Insights hält Details zu Benutzeraktivitäten wie Anzahl der Bildbewertungen, Klickraten und Impressionen (Häufigkeit des Ladens eines Bildes auf einer Website) fest. Basierend auf diesen Statistiken werden Bildern Bewertungen zugewiesen. Sie können Bewertungs- und Leistungsstatistiken nutzen, um beliebte Bilder für Kataloge, Marketing-Kampagnen usw. auszuwählen. Sie können außerdem Richtlinien zu Archivierungen und Lizenzerneuerungen anhand dieser Statistiken formulieren.

Für [!DNL Assets] Einblicke zur Erfassung von Nutzungsstatistiken für Bilder von einer Website müssen Sie den Einbettungscode für das Bild in den Website-Code aufnehmen.

Damit Assets Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion, um Berichtsdaten aus Adobe Analytics abzurufen. Weitere Details finden Sie unter [Asset Insights konfigurieren](/help/assets/configure-asset-insights.md). Um diese Funktion in einer On-Premise-Installation zu verwenden, kaufen Sie [!DNL Adobe Analytics] -Lizenz getrennt. Kunden mit [!DNL Managed Services] receive [!DNL Analytics] Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

## Anzeigen von Statistiken für Bilder {#viewing-statistics-for-an-image}

Sie können die Asset Insights-Bewertungen über die Metadatenseite anzeigen.

1. Aus dem [!DNL Assets] Benutzeroberfläche, wählen Sie das Bild aus und klicken Sie auf **[!UICONTROL Eigenschaften]** aus der Symbolleiste.
1. Klicken Sie auf der Seite „Eigenschaften“ auf die Registerkarte **[!UICONTROL Statistiken]**.
1. Überprüfen Sie die Nutzungsdetails für das Asset auf der Registerkarte **[!UICONTROL Insights]**. Der Abschnitt **[!UICONTROL Bewertung]** beschreibt die gesamte Asset-Nutzung und die Leistungsbewertungen eines Assets.

   Die Nutzungsbewertung beschreibt, wie oft ein Asset in verschiedenen Lösungen verwendet wird.

   Die Bewertung **[!UICONTROL Impressionen]** beschreibt, wie oft das Asset auf der Website geladen wurde. Die unter **[!UICONTROL Klicks]** angezeigte Zahl beschreibt, wie oft Benutzer auf das Asset geklickt haben.

1. Im Abschnitt **[!UICONTROL Nutzungsstatistiken]** können Sie ermitteln, in welchen Elementen das Asset enthalten war und in welchen Kreativlösungen es vor Kurzem verwendet wurde. Je höher die Nutzung, desto größer ist die Wahrscheinlichkeit, dass das Asset bei Benutzern beliebt ist. Nutzungsdaten werden unter den folgenden Überschriften angezeigt:

   * **Asset**: Wie oft war das Asset Teil einer Sammlung oder eines zusammengesetzten Assets
   * **Web und Mobile**: Wie oft wurde das Asset in Websites und Apps verwendet
   * **Social**: Wie oft wurde das Asset in Lösungen wie Adobe Social und Adobe Campaign verwendet
   * **E-Mail**: Wie oft wurde das Asset in E-Mail-Kampagnen verwendet

   ![Nutzungsstatistiken](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Da die Funktion &quot;Assets Insights&quot;normalerweise die Lösungsdaten regelmäßig aus Adobe Analytics abruft, werden im Abschnitt &quot;Lösungen&quot;möglicherweise nicht die neuesten Daten angezeigt. Der Zeitraum, für den die Daten angezeigt werden, hängt vom Zeitplan des Abholvorgangs ab, mit dem Asset Insights ausgeführt wird, um Daten aus Analytics abzurufen.

1. Um Leistungsstatistiken für das Asset für einen bestimmten Zeitraum grafisch anzuzeigen, wählen Sie den gewünschten Zeitraum im Abschnitt **[!UICONTROL Leistungsstatistiken]** aus. Details wie Klicks und Impressions werden als Trend-Linien eines Diagramms angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Im Gegensatz zu den Daten im Abschnitt „Lösungen“ zeigt der Abschnitt „Leistungsstatistiken“ die neuesten Daten an.

1. Um den Einbettungs-Code für das Asset zu erhalten, das Sie in die Websites einbeziehen, um Leistungsdaten zu erhalten, klicken Sie unter dem Asset-Miniaturbild auf **[!UICONTROL Einbettungs-Code abrufen]**. Weitere Informationen zum Einbettungscode in Webseiten von Drittanbietern finden Sie unter [Verwenden von Seitenverfolgung und Einbettungscode in Webseiten](/help/assets/use-page-tracker.md).

   ![chlimage_1-98](assets/chlimage_1-303.png)

## Anzeigen von zusammengefassten Statistiken für Bilder {#viewing-aggregate-statistics-for-images}

Mit der **[!UICONTROL Insights-Ansicht]** können Sie Bewertungen aller Assets in einem Ordner gleichzeitig anzeigen.

1. Im [!DNL Assets] Navigieren Sie in der -Benutzeroberfläche zu dem Ordner mit den Assets, für die Sie Einblicke anzeigen möchten.
1. Klicken Sie in der Symbolleiste auf Layout und wählen Sie dann **[!UICONTROL Insights-Ansicht]**.
1. Die Seite zeigt die Nutzungsbewertungen für die Assets an. Vergleichen Sie die Bewertungen der verschiedenen Assets und ziehen Sie Ihre Erkenntnisse daraus.

## Planen von Hintergrundaufträgen {#scheduling-background-job}

Assets Insights ruft regelmäßig Nutzungsdaten für Assets aus Adobe Analytics Report Suites ab. Standardmäßig führt Assets Insights alle 24 Stunden um 2 Uhr einen Hintergrundauftrag aus, um die Daten abzurufen. Sie können jedoch die Häufigkeit und die Zeit ändern, indem Sie den Dienst **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** von der Web-Konsole aus konfigurieren.

1. Klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie die Service-Konfiguration **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-99](assets/chlimage_1-304.png)

1. Geben Sie die gewünschte Terminplaner-Häufigkeit und Startzeit für den Auftrag im Eigenschaftsplanerausdruck ein. Speichern Sie die Änderungen.
