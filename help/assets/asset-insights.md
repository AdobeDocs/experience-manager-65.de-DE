---
title: Assets Insights
description: Erfahren Sie, wie Sie mit der Funktion „Assets Insights“ Benutzerbewertungen und Nutzungsstatistiken von Bildern nachverfolgen können, die auf Drittanbieter-Websites, in Marketing-Kampagnen und den Kreativlösungen von Adobe verwendet werden.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 0130ac40-a72b-4caf-a10f-3c7d76eaa1e6
hide: true
source-git-commit: 3d5e9ad8ee19756b05e5a77a3f748bc647fcf734
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 89%

---

# Assets Insights {#asset-insights}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/assets-insights.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Mit der Funktion „Assets Insights“ können Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern nachverfolgen, die auf Drittanbieter-Websites, in Marketing-Kampagnen und den Kreativlösungen von Adobe verwendet werden. Sie hilft, Erkenntnisse über ihre Leistung und Beliebtheit abzuleiten.

[!DNL Assets] Insights hält Details zu Benutzeraktivitäten wie Anzahl der Bildbewertungen, Klickraten und Impressionen (Häufigkeit des Ladens eines Bildes auf einer Website) fest. Basierend auf diesen Statistiken werden Bildern Bewertungen zugewiesen. Sie können Bewertungs- und Leistungsstatistiken nutzen, um beliebte Bilder für Kataloge, Marketing-Kampagnen usw. auszuwählen. Sie können außerdem Richtlinien zu Archivierungen und Lizenzerneuerungen anhand dieser Statistiken formulieren.

Damit [!DNL Assets] Insights Nutzungsstatistiken für Bilder von einer Website festhalten kann, müssen Sie den Einbettungs-Code für das Bild in den Website-Code einfügen.

Damit Assets Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion für den Abruf von Berichtsdaten aus Adobe Analytics. Weitere Details finden Sie unter [Asset Insights konfigurieren](/help/assets/configure-asset-insights.md). Um diese Funktion in einer On-Premise-Installation zu verwenden, ist der separate Kauf einer [!DNL Adobe Analytics] -Lizenz erforderlich. Kundinnen und Kunden mit [!DNL Managed Services] erhalten die [!DNL Analytics]-Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

## Anzeigen von Statistiken für Bilder {#viewing-statistics-for-an-image}

Sie können die Asset Insights-Bewertungen über die Metadatenseite anzeigen.

1. [!DNL Assets]Wählen Sie in der-Benutzeroberfläche das Bild aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Klicken Sie auf der Seite Eigenschaften auf die **[!UICONTROL Insights]** Registerkarte.
1. Überprüfen Sie die Nutzungsdetails für das Asset auf der Registerkarte **[!UICONTROL Insights]**. Der Abschnitt **[!UICONTROL Bewertung]** beschreibt die gesamte Asset-Nutzung und die Leistungsbewertungen eines Assets.

   Die Nutzungsbewertung beschreibt, wie oft ein Asset in verschiedenen Lösungen verwendet wird.

   Die **[!UICONTROL Impressionen]** score ist die Anzahl der Ladevorgänge des Assets auf der Website. Die unter **[!UICONTROL Klicks]** ist die Anzahl der Klicks auf das Asset.

1. Im Abschnitt **[!UICONTROL Nutzungsstatistiken]** können Sie ermitteln, in welchen Elementen das Asset enthalten war und in welchen Kreativlösungen es vor Kurzem verwendet wurde. Je höher die Nutzung ist, desto größer ist die Wahrscheinlichkeit, dass das Asset bei Benutzern beliebt ist. Nutzungsdaten werden unter den folgenden Überschriften angezeigt:

   * **Asset**: Wie oft war das Asset Teil einer Sammlung oder eines zusammengesetzten Assets
   * **Web und Mobile**: Wie oft wurde das Asset in Websites und Apps verwendet
   * **Social**: Wie oft wurde das Asset in Lösungen wie Adobe Social und Adobe Campaign verwendet
   * **E-Mail**: Wie oft wurde das Asset in E-Mail-Kampagnen verwendet

   ![Nutzungsstatistiken](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Da die Assets Insights-Funktion die Lösungsdaten aus Adobe Analytics normalerweise in bestimmten Abständen abruft, werden im Abschnitt „Lösungen“ möglicherweise nicht die neuesten Daten angezeigt. Der Zeitraum, für den die Daten angezeigt werden, hängt vom Zeitplan des Abholvorgangs ab, mit dem Asset Insights ausgeführt wird, um Daten aus Analytics abzurufen.

1. Um Leistungsstatistiken für das Asset für einen bestimmten Zeitraum grafisch anzuzeigen, wählen Sie den gewünschten Zeitraum im Abschnitt **[!UICONTROL Leistungsstatistiken]** aus. Details wie Klicks und Impressions werden als Trend-Linien eines Diagramms angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Im Gegensatz zu den Daten im Abschnitt „Lösungen“ zeigt der Abschnitt „Leistungsstatistiken“ die neuesten Daten an.

1. Um den Einbettungs-Code für das Asset zu erhalten, das Sie in die Websites einbeziehen, um Leistungsdaten zu erhalten, klicken Sie unter dem Asset-Miniaturbild auf **[!UICONTROL Einbettungs-Code abrufen]**. Weitere Informationen dazu, wie Sie Ihren Einbettungs-Code in Web-Seiten von Drittanbietern einschließen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten](/help/assets/use-page-tracker.md).

   ![chlimage_1-98](assets/chlimage_1-303.png)

## Anzeigen von zusammengefassten Statistiken für Bilder {#viewing-aggregate-statistics-for-images}

Mit der **[!UICONTROL Insights-Ansicht]** können Sie Bewertungen aller Assets in einem Ordner gleichzeitig anzeigen.

1. Gehen Sie in der [!DNL Assets]-Benutzeroberfläche zum Ordner, in dem die Assets enthalten sind, für die Sie Statistiken anzeigen möchten.
1. Klicken Sie in der Symbolleiste auf „Layout“ und wählen Sie **[!UICONTROL Insights-Ansicht]** aus.
1. Auf der Seite werden Nutzungsbewertungen für die Assets angezeigt. Vergleichen Sie die Bewertungen der verschiedenen Assets und ziehen Sie Ihre Erkenntnisse daraus.

## Planen von Hintergrundaufträgen {#scheduling-background-job}

Assets Insights ruft Nutzungsdaten für Assets regelmäßig aus den Adobe Analytics-Report Suites ab. Standardmäßig führt Assets Insights alle 24 Stunden um 2 Uhr einen Hintergrundauftrag aus, um Daten abzurufen. Sie können jedoch die Häufigkeit und die Zeit ändern, indem Sie den Dienst **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** von der Web-Konsole aus konfigurieren.

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie anschließend zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie die Service-Konfiguration **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-99](assets/chlimage_1-304.png)

1. Geben Sie die gewünschte Planungsfrequenz und die Startzeit für den Auftrag im Ausdruck für die Eigenschaftsplanung an. Speichern Sie die Änderungen.
