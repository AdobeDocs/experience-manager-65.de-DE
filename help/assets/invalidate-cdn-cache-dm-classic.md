---
title: Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic
description: Durch die Invalidierung Ihres im CDN (Content Delivery Network) zwischengespeicherten Inhalts können Sie von Dynamic Media Classic bereitgestellte Assets schnell aktualisieren, anstatt darauf zu warten, dass der Cache abläuft.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: CDN Cache,Dynamic Media Classic
role: Business Practitioner, Administrator
exl-id: 7020343a-b556-4091-9717-93fcc55e623b
source-git-commit: c9aec973faf4caef741961d92a6f258646aeddb7
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 49%

---

# Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zur schnellen Bereitstellung zwischengespeichert. Wenn Sie jedoch ein Asset aktualisieren, sollen diese Änderungen sofort wirksam werden. Durch die Invalidierung Ihres im CDN-Cache zwischengespeicherten Inhalts können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren, anstatt darauf zu warten, dass der Cache abläuft.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN verwenden, das im Lieferumfang von Adobe Experience Manager Dynamic Media enthalten ist. Mit dieser Funktion werden keine anderen benutzerdefinierten CDNs unterstützt.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für Dynamic Media in AEM 6.5, Service Pack 5 (AEM 6.5.5) oder früher.<br>Wenn Sie Dynamic Media in AEM 6.5, Service Pack 6 (AEM 6.5.6) oder höher verwenden, führen Sie die Schritte unter  [Invalidierung des CDN-Cache über Dynamic Media aus.](/help/assets/invalidate-cdn-cache-dynamic-media.md)

Siehe auch [Überblick über Caching in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den CDN-Cache über Dynamic Media Classic ungültig:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) und melden Sie sich bei Ihrem Konto an.

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen.]**
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage nur `<ID>` enthält, füllt Dynamic Media `https://<server>/is/image` auf, wobei `<server>` der Veröffentlichungsservername ist, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> die Assets ist, die ungültig gemacht werden sollen.

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Schließen.]**
1. Wählen Sie in der Benutzeroberfläche von Dynamic Media Classic ein oder mehrere Assets aus und klicken Sie dann auf **[!UICONTROL Datei > Ungültiges CDN.]** Es wird eine Liste mit einer oder mehreren URLs angezeigt, die aus der von Ihnen erstellten Vorlage und den von Ihnen ausgewählten Assets generiert wurden. Dabei werden die Server-URL-Einträge unter „Veröffentlichungs-Servername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie auf **[!UICONTROL Datei > Ungültiges CDN]** tippen, wird die folgende generierte URL in der Benutzeroberfläche für CDN-Invalidierung generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Tippen Sie im URL-Listenfeld auf **[!UICONTROL Weiter]** , um den Cache für jede bestimmte URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie sie in das URL-Listenfeld eingeben oder einfügen. Sie müssen die Vorlage für CDN-Invalidierung nicht vorab festlegen.

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist.

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei > Ungültiges CDN]** tippen, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL referenziert.]** Daher können Sie eine  **[!UICONTROL Vorlage für CDN-Invalidierung definieren, die auf jede URL-Bildvorgabe verweist, auf die auf Ihrer Website verwiesen wird (z. B. Produktdetails und Suchergebnisse).]** Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, erstellt Dynamic Media mithilfe einer Vorlage für CDN-Invalidierung automatisch die URLs, die für das Content Delivery Network (CDN) ungültig gemacht werden sollen. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei > Ungültiges CDN]** aufrufen.
