---
title: Aktivieren des Hotlink-Schutzes in Dynamic Media
description: Informationen zur Aktivierung des Hot Link-Schutzes in Dynamic Media.
uuid: 5f93bc27-5edd-4143-8701-87896c52f0af
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: a70aa448-0f58-4ed2-9381-afcc76fa827f
role: User, Admin
exl-id: 698e8bdb-9b31-49ab-8560-26b05109bb23
feature: Configuration
source-git-commit: 65af6e33ae3897519491952f4d3a6832700f77b2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 47%

---

# Aktivieren des Hotlink-Schutzes in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Von Hotlinking spricht man, wenn eine Drittanbieter-Website HTML-Code verwendet, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Hotlink *protection* ist eine Methode, um zu verhindern, dass andere Websites direkt auf Bilder, CSS oder JavaScript auf Ihren Webseiten verweisen. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Der Experience Manager-](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) Kundensupport kann einen Referrer-Filter auf CDN-Ebene (Content Delivery Network) konfigurieren, sodass Dynamic Media-Inhalte nur für Websites bereitgestellt werden, die sich auf Ihrer Liste der zulässigen Websites für die Domäne befinden.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. Um den Hotlink-Schutz zu aktivieren, muss ein Administrator ein Adobe-Support-Ticket erstellen, um die Konfigurationsänderung an Ihr Dynamic Media-Konto anzufordern. Mit der Aktivierung des Hotlink-Schutzes sind keine zusätzlichen Kosten verbunden.
