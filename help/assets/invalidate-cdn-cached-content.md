---
title: 'Ungültigmachen von Inhalten im CDN-Cache '
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Ungültigmachen von Inhalten im CDN-Cache  {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden von CDN zwecks schneller Bereitstellung im Cache gespeichert. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch möglicherweise sofort wirksam werden. Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.

Siehe auch Übersicht über den [Cache in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie Inhalte im CDN-Cache ungültig:** 

1. Melden Sie sich bei Ihrem Dynamic Media Classic (Scene7)-Konto an: 

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1.  Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.
1. On the Application General Settings page, under the Servers group heading, locate the **[!UICONTROL CDN Invalidation Template]** text box.

1. Geben Sie die Vorlage an, die zum Ungültigmachen des CDN (Content Delivery Network)-Caches verwendet wird.

   For example, suppose you enter an image URL (including image presets or modifiers) referencing `<ID>`, instead of a specific image ID as in the following example:

   `https://server.com/is/image/Company/<ID>?$product$`

   If the Template just contains `<ID>`, then Dynamic Media fills in `https://<server>/is/image` where `<server>` is the Publish Server Name that is defined in General Settings and &lt;ID> is the asset(s) selected to be invalidated.

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Schließen]**. 
1. Wählen Sie in der Dynamic Media Classic (Scene7)-Benutzeroberfläche mindestens ein Asset aus und klicken Sie auf **[!UICONTROL Datei > Ungültiges CDN]**.  Daraufhin wird eine Liste der URL(s) angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde.  Dabei werden die Server-URL-Einträge unter „Veröffentlichungsservername“ in den allgemeinen Programmeinstellungen verwendet. 

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten CDN-Ungültigmachen-Vorlage ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt.  Wenn Sie dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, wird die folgende URL in der Benutzeroberfläche zum Ungültigmachen des CDN-Caches generiert: 

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klicken Sie im URL-Listenfeld auf **[!UICONTROL Weiter]**, um den Cache für jede einzelne URL zu löschen.  Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen; es ist nicht erforderlich, die CDN-Ungültigmachen-Vorlage vorab festzulegen  

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist. 

   If you selected multiple assets, then clicked **[!UICONTROL File > Invalidate CDN]**, each asset is referenced in the saved **[!UICONTROL Template URL]**. Therefore, you can define a **[!UICONTROL CDN Invalidate Template]** referencing each URL image preset that is referenced on your website (such as product detail, search results, and so forth). Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, erstellt Dynamic Media mithilfe einer CDN-Ungültigmachen-Vorlage automatisch die URLs, die für Content Delivery Network (CDN) ungültig gemacht werden sollen.  If there is nothing in the **[!UICONTROL CDN Invalidate Template]** text box, then you get a blank URL list. Die Speicherung im CDN-Cache erfolgt nicht Asset-basiert, sondern URL-basiert.  Daher müssen Sie über alle URLs auf Ihrer Website informiert sein.  After you determine those URLs, you can add them to the **[!UICONTROL Invalidate CDN Template]** text box earlier in the steps. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen. 
   >
   >Another option is to add complete URLs to the **[!UICONTROL Invalidate CDN]** list. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei > Ungültiges CDN]** aufrufen. 

