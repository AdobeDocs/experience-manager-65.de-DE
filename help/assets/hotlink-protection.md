---
title: Aktivieren des Hotlink-Schutzes in Dynamic Media
description: Informationen zum Aktivieren des Hotlink-Schutzes in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
role: User, Admin
exl-id: 698e8bdb-9b31-49ab-8560-26b05109bb23
feature: Configuration
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: da0dfbce-df02-4f8b-b32d-a4e3b1d05085
    internal-label: Configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 100%
---
# Hotlink-Schutz in Dynamic Media aktivieren {#activating-hotlink-protection-in-dynamic-media}

Von Hotlinking spricht man, wenn eine Drittanbieter-Website HTML-Code verwendet, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Der Hotlink-*Schutz* ist eine Methode, um zu verhindern, dass andere Websites direkte Links auf Bilder, CSS oder JavaScript auf Ihren Webseiten erstellen. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Der Experience Manager-Kunden-Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager&support-tab=home&lang=de#support) kann einen Filter für Verweise auf CDN-Ebene (Content Delivery Network) konfigurieren, sodass Dynamic Media-Inhalte nur für Websites übermittelt werden, die auf der Liste der zulässigen Websites für die Domain stehen.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. Zum Aktivieren des Hotlink-Schutzes muss eine bzw. ein Admin ein Support-Ticket für den Adobe-Kunden-Support erstellen, um die Konfigurationsänderung an Ihrem Dynamic Media-Konto anzufordern. Mit der Aktivierung des Hotlink-Schutzes sind keine zusätzlichen Kosten verbunden.
