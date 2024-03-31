---
title: Videoausgabeformate
description: Erstellen Sie mit Adobe Experience Manager Assets Videoausgabedarstellungen für Video-Assets verschiedener Formate einschließlich OGG, FLV usw.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
exl-id: a644558e-5be9-4ba2-b560-fc300497fbdf
solution: Experience Manager, Experience Manager Assets
feature: Video
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 100%

---

# Videoausgabeformate {#video-renditions}

Adobe Experience Manager Assets erstellt Videoausgabeformate für Video-Assets verschiedener Formate, einschließlich OGG, FLV usw.

Experience Manager Assets unterstützt statische und dynamische Ausgabeformate (DM-kodierte Ausgabeformate) für Medien-Assets.

Statische Ausgabeformate werden nativ mit FFMPEG (im Systempfad installiert und verfügbar) generiert und im Inhalts-Repository gespeichert.

Die DM-kodierten Ausgabeformate werden im Proxyserver gespeichert und zur Laufzeit bereitgestellt.

Experience Manager Assets bietet Wiedergabeunterstützung für diese Ausgabeformate auf der Client-Seite.

Um die Ausgabeformate eines bestimmten Video-Assets anzuzeigen, öffnen Sie die entsprechende Asset-Seite und klicken oder wählen Sie das GlobalNav-Symbol. Wählen Sie dann **[!UICONTROL Ausgabeformate]** aus der Liste aus.

![chlimage_1-478](assets/chlimage_1-478.png)

Die Liste mit Videoausgabeformate wird im Bereich **[!UICONTROL Wiedergaben]** angezeigt.

![chlimage_1-479](assets/chlimage_1-479.png)

Konfigurieren Sie den Proxyserver für DM-kodierte Ausgabeformate, indem Sie [Cloud-Dienste für Dynamic Media konfigurieren](config-dynamic.md).

Generieren Sie Videoausgabeformate mit gewünschten Parametern: [Erstellen eines passenden Videoprofils](video-profiles.md).

Nachdem Sie den Proxyserver konfiguriert und Videoprofile erstellt haben, können Sie diese Videovorlage in ein Verarbeitungsprofil aufnehmen und dieses Verarbeitungsprofil auf einen Ordner anwenden.

>[!NOTE]
>
>Die Audiowiedergabe funktioniert nicht für OGG- und WAV-Dateien in Microsoft® Internet Explorer 11. Auf der Seite mit den Asset-Details wird für Assets mit der Erweiterung OGG oder WAV der Fehler `Invalid Source` angezeigt.
>
>In MS® Edge und auf dem iPad werden die OGG-Dateien nicht abgespielt und lösen den Fehler „Format nicht unterstützt“ aus.
