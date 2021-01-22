---
title: Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic
description: Wenn Sie Ihre zwischengespeicherten Inhalte im CDN (Content Versand Network) für ungültig erklären, können Sie Assets, die von Dynamic Media Classic bereitgestellt werden, schnell aktualisieren, anstatt darauf zu warten, dass der Cache abläuft.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: f786b35e77c6b862f7fc6e45d3d0af56a51e3e95
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 81%

---


# Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN zwecks schneller Bereitstellung im Cache gespeichert. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch möglicherweise sofort wirksam werden. Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Cache warten.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für Dynamic Media in AEM 6.5, Service Pack 5 (AEM 6.5.5) oder früher.<br>Wenn Sie Dynamic Media in AEM 6.5, Service Pack 6 (AEM 6.5.6) oder höher verwenden, befolgen Sie die Schritte unter  [Ungültigmachen des CDN-Cache über Dynamic Media.](/help/assets/invalidate-cdn-cache-dynamic-media.md)

Siehe auch [Überblick über Caching in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den CDN-Cache über Dynamic Media Classic ungültig:**

1. Öffnen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) und melden Sie sich dann bei Ihrem Konto an.

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Tippen Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen.]**
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage ausschließlich `<ID>` enthält, füllt Dynamic Media die URL `https://<server>/is/image` auf. Dabei steht `<server>` für den Veröffentlichungs-Server-Namen, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> für die Assets, die ungültig gemacht werden sollen.

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Schließen.]**
1. Wählen Sie in der Benutzeroberfläche von Dynamic Media Classic ein oder mehrere Assets aus und klicken Sie dann auf **[!UICONTROL Datei > Ungültiges CDN.]** Daraufhin wird eine Liste der URL(s) angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde. Dabei werden die Server-URL-Einträge unter „Veröffentlichungsservername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, wird die folgende URL in der Benutzeroberfläche zur Invalidierung des CDN-Cache generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klicken Sie im URL-Listenfeld auf **[!UICONTROL Weiter]**, um den Cache für jede einzelne URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen; es ist nicht erforderlich, die Vorlage für CDN-Invalidierung vorab festzulegen

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist.

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei > Ungültiges CDN]** geklickt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL referenziert.]** Daher können Sie eine **[!UICONTROL Vorlage für CDN-Invalidierung]** definieren, die auf alle auf Ihrer Website referenzierten URL-Bildvorgaben (wie Produktdetails, Suchergebnisse usw.) verweist. Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, erstellt Dynamic Media mithilfe einer Vorlage für CDN-Invalidierung automatisch die URLs, die für das Content Delivery Network (CDN) ungültig gemacht werden sollen. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei > Ungültiges CDN]** aufrufen.

