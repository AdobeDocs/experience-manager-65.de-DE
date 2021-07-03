---
title: Veröffentlichen von Dynamic Media-Assets
description: Veröffentlichen von Dynamic Media-Assets
uuid: b1bee905-86cf-4284-8d4e-067e11557899
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 99d7025f-d022-4213-83c0-815a4712c573
role: User, Admin
exl-id: 750627fc-2a29-43ff-867e-55cb2e371043
feature: Veröffentlichung
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 58%

---

# Veröffentlichen von Dynamic Media-Assets {#publishing-dynamic-media-assets}

Sie veröffentlichen Ihre Dynamic Media-Assets, indem Sie die bereits hochgeladenen Assets auswählen und auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** tippen. Nachdem Ihre Dynamic Media-Assets veröffentlicht wurden, können Sie sie über eine URL auf einer Web-Seite einschließen oder den Code auf der Seite einbetten.

Sie können hochgeladene Assets auch sofort veröffentlichen, ohne dass der Benutzer eingreifen muss. Siehe [Konfigurieren von Dynamic Media - Scene7-Modus](config-dms7.md).
Alternativ können Sie Assets selektiv in Dynamic Media oder Adobe Experience Manager veröffentlichen, sich gegenseitig ausschließen, indem Sie **[!UICONTROL Selektive Veröffentlichung]** auf Ordnerebene verwenden. Siehe [Arbeiten mit selektiver Veröffentlichung in Dynamic Media](/help/assets/selective-publishing.md).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Wenn ein Asset bereits veröffentlicht ist, verwenden Sie Experience Manager, um das Asset in einen anderen Ordner zu verschieben und von seinem neuen Speicherort aus erneut zu veröffentlichen. Die ursprüngliche Position des veröffentlichten Assets sowie das neu veröffentlichte Asset sind weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für Experience Manager nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, die Veröffentlichung von Assets zunächst rückgängig zu machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets sofort nach der Kodierung veröffentlichen möchten, stellen Sie sicher, dass die Kodierung abgeschlossen ist. Während Videos kodiert werden, informiert das System Sie darüber, dass ein Videoverarbeitungs-Workflow ausgeführt wird. Wenn die Videokodierung abgeschlossen ist, können Sie eine Vorschau der Videoausgabedarstellungen anzeigen. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe auch [Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite](embed-code.md) .

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn die Assets nicht veröffentlicht werden, funktioniert das Kopieren und Einfügen der URL in einen Webbrowser nicht.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.

>



Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](manage-assets.md).

## Bereitstellung von Dynamic Media-Assets über HTTP/2   {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie unter [HTTP/2-Bereitstellung von häufig gestellten Fragen zu Inhalten](/help/sites-administering/scene7-http2faq.md).
