---
title: Produkt-Feed
seo-title: Produkt-Feed
description: Hier erfahren Sie mehr zum AEM-Produkt-Feed.
seo-description: Hier erfahren Sie mehr zum AEM-Produkt-Feed.
uuid: 99eb9bdc-2717-45d4-9203-6394b7d7ddc6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 1f920892-c52e-42ca-900c-2c7ab3c503b3
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# Produkt-Feed {#product-feed}

AEM integrates with [Search&amp;Promote](https://www.adobe.com/solutions/testing-targeting/searchandpromote.html) and allows you to:

* Verwenden der eCommerce-API, unabhängig von der zugrunde liegenden Repository-Struktur und Commerce-Plattform
* Nutzen der Index-Connector-Funktion von Search&amp;Promote zur Bereitstellung eines Produkt-Feeds im XML-Format
* Nutzen der Fernsteuerungsfunktion von Search&amp;Promote zur bedarfsabhängigen bzw. planmäßigen Durchführung von Anfragen des Produkt-Feeds
* Erstellen von Feeds für verschiedene Search&amp;Promote-Konten, konfiguriert als Cloud Service-Konfigurationen

You need to have a valid account and to [configure the connection to Search&amp;Promote](/help/sites-administering/search-and-promote.md#configuring-the-connection-to-search-promote). You also have to verify that you are using the correct [data center](/help/sites-administering/search-and-promote.md#configuring-the-data-center) and make sure that the **Remote server URI **is configured.

## Einrichten des Produkt-Feeds {#set-up-the-product-feed}

Zuallererst müssen Sie einen Website-Stamm und ein ID-Attribut eingeben. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zur Search&amp;Promote-Konfiguration.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Konfiguration für Index-Connector-Feed]**.
1. Enter the **[!UICONTROL Web site root]** and **[!UICONTROL Identifier attribute]**.

   >[!NOTE]
   >
   >The **[!UICONTROL Web site root]** is the root of your eCommerce website, for example `/content/geometrixx-outdoors/en`.
   >
   >The **[!UICONTROL Identifier attribute]** is a JCR property that uniquely identifies the product: `identifier`.

1. Klicken Sie auf **[!UICONTROL OK]**.

Dann müssen Sie auch zwei Konfigurationen in der Web-Konsole bearbeiten, bevor Sie Produkt-Feeds generieren können.

### Konfigurieren der Day CQ-Search&amp;Promote-Produktcrawler-Implementierung für Geometrixx {#configuring-the-day-cq-search-promote-products-crawler-implementation-for-geometrixx}

1. Gehen Sie zu [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klicken Sie auf **[!UICONTROL Day CQ-Search&amp;Promote-Produktcrawler-Implementierung für Geometrixx]**.
1. Geben Sie die Search&amp;Promote-Kontonummer an, mit der dieser Crawler verknüpft ist. Sie wird verwendet, um die Cloud Service-Konfiguration nachzuschlagen, die von diesem Crawler verwendet wird.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

### Konfigurieren des Day CQ-Search&amp;Promote-Produkt-Feed-Generators für Geometrixx {#configuring-the-day-cq-search-promote-products-feed-generator-for-geometrixx}

1. Gehen Sie zu [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klicken Sie auf **[!UICONTROL Day CQ-Search&amp;Promote-Produkt-Feed-Generator für Geometrixx]**.
1. Geben Sie die Search&amp;Promote-Kontonummer an, mit der dieser Generator verknüpft ist. Sie wird verwendet, um die Cloud Service-Konfiguration nachzuschlagen, die von diesem Generator verwendet wird.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Planen des Produkt-Feeds {#schedule-the-product-feed}

Zur Aktivierung der geplanten Feed-Erstellung müssen Sie dafür einen Planer konfigurieren.
Ein Planer wird als untergeordnete Konfiguration Ihrer eigenen Search&amp;Promote-Cloud Service-Konfiguration konfiguriert.

1. Navigieren Sie zur Search&amp;Promote-Konfiguration.
1. Klicken Sie neben **[!UICONTROL Planerkonfiguration]** auf das **[!UICONTROL +]**.
1. Enter a **[!UICONTROL Title]** that is recognizable to page authors, and a unique **[!UICONTROL Name]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein Dialogfeld wird geöffnet.

   ![chlimage_1-108](assets/chlimage_1-108a.png)

1. Enter the **[!UICONTROL Remote Control Password]**. Hierbei handelt es sich um das Kennwort, das Sie in Ihrem Search&amp;Promote-Konto konfiguriert haben.

   >[!NOTE]
   >
   >Es ist aber nicht das Kennwort Ihres Search&amp;Promote-Kontos. You can find and change this password by logging into your Search&amp;Promote account and going to **[!UICONTROL Index]** and then to **[!UICONTROL Remote control]**.

1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Zeitplan aktivieren]**.
1. Wählen Sie einen **[!UICONTROL Zeitplan]** aus. Hierbei handelt es sich um den eigentlichen Zeitplan für die Feed-Generierung.
1. Sie können die **[!UICONTROL Bedarfsorientierte Indizierung]** aktivieren. Diese Funktion wird verwendet, um den Search&amp;Promote-Index manuell aufzurufen. If **[!UICONTROL Request full products feed]** is checked, Search&amp;Promote will request a full products feed. Andernfalls wird ein mehrstufiger Produkt-Feed aufgefordert.

   >[!NOTE]
   >
   >Die bedarfsgesteuerte Indizierungsfunktion nutzt die Fernsteuerungsfunktion von Search&amp;Promote. Wenn eine Remote-Indizierung aufgerufen wird, beginnt die Indizierung nicht sofort. Stattdessen wird mithilfe der Fernsteuerungsfunktion zuerst eine Indizierungsanforderung an Search&amp;Promote gesendet.

1. Klicken Sie auf **[!UICONTROL OK]**.

Now that you configured everything, you can see an XML page containing all the products under the configured web site root: [http://localhost:4502/etc/commerce/searchpromote/feed/full](http://localhost:4502/etc/commerce/searchpromote/feed/full).
