---
title: Ungültigmachen des CDN-Cache über dynamische Medien
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.6/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 9e67e252348f471c052f6c3e88aea61d7a309241
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 16%

---


# Ungültigmachen des CDN-Cache über dynamische Medien {#invalidating-cdn-cache-for-dm-assets}

Dynamic Media-Assets werden vom CDN (Content Versand Network) zwischengespeichert, um einen schnellen Versand zu Ihren Kunden zu ermöglichen. Wenn Sie jedoch Aktualisierungen an diesen Assets vornehmen, möchten Sie möglicherweise, dass diese Änderungen sofort auf Ihrer Website wirksam werden. Durch das Löschen oder Ungültigmachen des CDN-Cache können Sie schnell die von dynamischen Medien bereitgestellten Assets aktualisieren. Anstatt darauf zu warten, dass der Cache mit einem TTL-Wert (Time To Live) abläuft (Standard ist 10 Stunden), können Sie eine Anforderung von Dynamischen Medien senden, damit der Cache sofort abläuft.

>[!IMPORTANT]
>
>Diese Schritte gelten nur für den Modus &quot;Dynamische Medien - Scene7&quot;in AEM 6.5, Service Pack 6 oder höher. <!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

See also [Caching overview in Dynamic Media](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den im CDN zwischengespeicherten Inhalt für dynamische Medienelemente ungültig:**

1. Tippen Sie in AEM 6.5.6 oder höher auf **[!UICONTROL Werkzeuge > Assets > CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Legen Sie auf der Seite &quot;CDN-Ungültigmachung&quot;die gewünschten Optionen fest:

   | Option | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** | Wenn Sie diese Option aktivieren, können Sie ein oder mehrere dynamische Medien-Assets auswählen, unabhängig vom MIME-Typ und den zugehörigen Bildvorgaben für die Cache-Ungültigmachung.<br>Sie können zwar einen oder mehrere Ordner mit Assets auswählen, diese Vorgehensweise wird jedoch von Adobe nicht empfohlen. Stattdessen sollten Sie einzelne Asset-Dateien auswählen.<br>Bearbeitet bis zum nächsten Schritt. |
   | **[!UICONTROL Auf Vorlage basierende Ungültigmachung]** | Wenn Sie diese Option aktivieren, können Sie die Assets für dynamische Medien und die zuvor erstellte Vorlage für das Ungültigmachen auswählen. Verwenden Sie diese Option mit |
   | **[!UICONTROL Assets hinzufügen]** | Blah |
   | **[!UICONTROL URL hinzufügen]** | Manually add full URL paths to Dynamic Media assets whose cache you want to invalidate. |

1. 
1. Tippen Sie auf **[!UICONTROL Weiter.]**
1. 
