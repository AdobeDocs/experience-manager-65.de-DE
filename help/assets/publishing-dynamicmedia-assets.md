---
title: Veröffentlichen von Dynamic Media-Assets
description: Erfahren Sie, wie Sie Dynamic Media-Assets wie Videos und Bilder veröffentlichen, einschließlich der HTTP/2-Bereitstellung solcher Assets.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
exl-id: 750627fc-2a29-43ff-867e-55cb2e371043
feature: Publishing
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: f59890ff-de81-47d5-9ef8-7ab2dd10c6c3
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: f901afa4-5613-4581-add5-219fa5f03fb5
    internal-label: Publishing
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%
---
# Veröffentlichen von Dynamic Media-Assets {#publishing-dynamic-media-assets}

Sie veröffentlichen Ihre Dynamic Media-Assets, indem Sie die bereits hochgeladenen Assets auswählen und auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** tippen. Nach dem Veröffentlichen Ihrer Dynamic Media-Assets können diese über eine URL oder einen Code in eine Web-Seite eingebettet werden.

Sie können hochgeladene Assets auch umgehend und ohne Anwenderinteraktion veröffentlichen. Siehe [Konfigurieren von Dynamic Media – Scene7-Modus](config-dms7.md).
Sie können Assets für Dynamic Media oder Adobe Experience Manager auch selektiv veröffentlichen (sich gegenseitig ausschließend), indem Sie auf der Ordnerebene die Option **[!UICONTROL Selektive Veröffentlichung]** verwenden. Siehe [Arbeiten mit selektiver Veröffentlichung in Dynamic Media](/help/assets/selective-publishing.md).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Angenommen, ein Asset wurde bereits veröffentlicht. Dann verschieben Sie es mit Adobe Experience Manager in einen anderen Ordner und veröffentlichen Sie es von seinem neuen Speicherort erneut. Die ursprüngliche Position des veröffentlichten Assets sowie das neu veröffentlichte Asset sind weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für Experience Manager nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, die Veröffentlichung von Assets zunächst rückgängig zu machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets sofort nach der Kodierung veröffentlichen möchten, achten Sie darauf, dass die Kodierung abgeschlossen ist. Wenn Videos kodiert werden, erhalten Sie eine Systemmeldung, dass ein Videoverarbeitungs-Workflow aktiv ist. Wenn die Videokodierung abgeschlossen ist, können Sie eine Vorschau der Videoausgabedarstellungen anzeigen. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit Ihrer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe auch [Einbetten des Dynamic Media- oder Bild-Viewers auf einer Web-Seite](embed-code.md).

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn Assets nicht veröffentlicht sind, können Sie die URL nicht kopieren und in einen Webbrowser einfügen.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.
>

Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](manage-assets.md).

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein Einbettungs-Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Das veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Diese Bereitstellungsmethode verbessert die Kommunikationsweise von Browsern und Servern, sodass eine bessere Antwort- und Ladezeit aller Assets mit dynamischen Medien möglich ist.

Weitere Informationen finden Sie unter [Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)](/help/sites-administering/scene7-http2faq.md).
