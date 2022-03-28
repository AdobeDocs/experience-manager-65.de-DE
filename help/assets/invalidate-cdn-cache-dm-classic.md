---
title: Invalidierung des Cache des Content Delivery Network über Dynamic Media Classic
description: Durch die Invalidierung Ihres im CDN (Content Delivery Network) zwischengespeicherten Inhalts können Sie von Dynamic Media Classic bereitgestellte Assets schnell aktualisieren, anstatt darauf zu warten, dass der Cache abläuft.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: CDN Cache,Dynamic Media Classic
role: User, Admin
exl-id: 7020343a-b556-4091-9717-93fcc55e623b
source-git-commit: b61157b0e9afa49ef72150ae0c1703a959d154be
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 71%

---

# Invalidierung des Cache des Content Delivery Network über Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zwischengespeichert, um eine schnelle Bereitstellung zu ermöglichen. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch sofort wirksam werden. Indem Sie die Inhalte im CDN-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Cache warten.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 (Experience Manager 6.5.5) oder früher.<br>Wenn Sie Dynamic Media in Experience Manager 6.5, Service Pack 6 (Experience Manager 6.5.6) oder höher verwenden, führen Sie die Schritte unter [Invalidierung des CDN-Cache über Dynamic Media](/help/assets/invalidate-cdn-cache-dynamic-media.md).

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

**So machen Sie den CDN-Cache über Dynamic Media Classic ungültig:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) und melden Sie sich bei Ihrem Konto an.

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Sie nicht über diese Informationen verfügen, wenden Sie sich an den Support von Adobe.

1. Navigieren Sie oben rechts auf der Seite zu **[!UICONTROL Einrichtung]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage ausschließlich `<ID>` enthält, füllt Dynamic Media die URL `https://<server>/is/image` auf. Dabei steht `<server>` für den Veröffentlichungsservernamen, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> für die Assets, die ungültig gemacht werden sollen.

1. Klicken Sie unten rechts auf der Seite auf **[!UICONTROL Schließen]**.
1. Wählen Sie in der Dynamic Media Classic-Benutzeroberfläche ein oder mehrere Assets aus und navigieren Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]**. Daraufhin wird eine Liste der URLs angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde. Dabei werden die Server-URL-Einträge unter „Veröffentlichungs-Servername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie dann auf **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** klicken, wird die folgende URL in der Benutzeroberfläche zur Invalidierung des CDN generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klicken Sie im URL-Listenfeld auf **[!UICONTROL Weiter]**, um den Cache für jede einzelne URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen. Es ist nicht erforderlich, die Vorlage für die CDN-Invalidierung vorab festzulegen.

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist.

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** geklickt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL]** referenziert. Daher können Sie eine **[!UICONTROL Vorlage für CDN-Invalidierung]** auf jede URL-Bildvorgabe verweisen, auf die auf Ihrer Website verwiesen wird (z. B. Produktdetails und Suchergebnisse). Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen, gehen Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** verwendet Dynamic Media eine Vorlage für CDN-Invalidierung, um automatisch URLs zu erstellen, die vom Content Delivery Network (CDN) ungültig gemacht werden. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei > Ungültiges CDN]** aufrufen.
