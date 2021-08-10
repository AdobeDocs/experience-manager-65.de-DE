---
title: Videoausgabeformate
description: Videoausgabeformate
uuid: a02f9ec1-30d9-4cbb-8746-8391ac614f0a
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: 1601b473-7227-4a56-bb7c-289de2987e4b
exl-id: a644558e-5be9-4ba2-b560-fc300497fbdf
source-git-commit: 77687a0674b939460bd34011ee1b94bd4db50ba4
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 45%

---

# Videoausgabeformate {#video-renditions}

Adobe Experience Manager Assets generiert Videoausgabeformate für Video-Assets verschiedener Formate wie OGG, FLV usw.

Experience Manager Assets unterstützt statische und dynamische Ausgabeformate (DM-kodierte Ausgabeformate) für Medien-Assets.

Statische Ausgabeformate werden nativ mit FFMPEG (im Systempfad installiert und verfügbar) generiert und im Inhalts-Repository gespeichert.

Die DM-kodierten Ausgabeformate werden im Proxyserver gespeichert und zur Laufzeit bereitgestellt.

Experience Manager Assets bietet Client-seitige Wiedergabefunktion für diese Ausgabedarstellungen.

Um die Ausgabeformate eines bestimmten Video-Assets anzuzeigen, öffnen Sie die Asset-Seite und wählen Sie das Symbol Globale Navigation aus. Wählen Sie dann **[!UICONTROL Ausgabeformate]** aus der Liste aus.

![chlimage_1-478](assets/chlimage_1-478.png)

Die Liste der Videoausgabeformate wird im Bedienfeld **[!UICONTROL Ausgabeformate]** angezeigt.

![chlimage_1-479](assets/chlimage_1-479.png)

Konfigurieren Sie den Proxyserver für DM-kodierte Ausgabeformate, indem Sie [Cloud-Dienste für Dynamic Media konfigurieren](config-dynamic.md).

Generieren Sie Videoausgabeformate mit gewünschten Parametern, [indem Sie ein entsprechendes Videoprofil erstellen](video-profiles.md).

Nachdem Sie den Proxyserver konfiguriert und Videoprofile erstellt haben, können Sie diese Videovorlage in ein Verarbeitungsprofil aufnehmen und dieses Verarbeitungsprofil auf einen Ordner anwenden.

>[!NOTE]
>
>Die Audiowiedergabe funktioniert nicht für OGG- und WAV-Dateien in Microsoft® Internet Explorer 11. Auf der Asset-Detailseite wird für Assets mit der Erweiterung OGG oder WAV ein Fehler `Invalid Source` angezeigt.
>
>Auf MS® Edge und iPad werden OGG-Dateien nicht abgespielt und es wird ein nicht unterstützter Formatfehler ausgegeben.
