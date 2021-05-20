---
title: Aktivieren des Hotlink-Schutzes in Dynamic Media
description: Informationen zur Aktivierung des Hot Link-Schutzes in Dynamic Media.
uuid: 5f93bc27-5edd-4143-8701-87896c52f0af
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: a70aa448-0f58-4ed2-9381-afcc76fa827f
role: Business Practitioner, Administrator
exl-id: 698e8bdb-9b31-49ab-8560-26b05109bb23
feature: Konfiguration
source-git-commit: 9134130f349c6c7a06ad9658a87f78a86b7dbf9c
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 19%

---

# Aktivieren des Hotlink-Schutzes in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Bei der Hotlink-Verknüpfung verwendet eine Drittanbieter-Website HTML-Code, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Hotlink *protection* ist eine Methode, um zu verhindern, dass andere Websites direkt auf Bilder, CSS oder JavaScript auf Ihren Webseiten verweisen. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Der ](https://helpx.adobe.com/de/support.html) Support von Adoben kann einen Referrer-Filter auf CDN-Ebene (Content Delivery Network) konfigurieren, sodass Dynamic Media-Inhalte nur für Websites bereitgestellt werden, die sich auf Ihrer Liste der zulässigen Websites für die Domäne befinden.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN verwenden, das im Lieferumfang von Adobe Experience Manager Dynamic Media enthalten ist. Mit dieser Funktion werden keine anderen benutzerdefinierten CDNs unterstützt. Um den Hotlink-Schutz zu aktivieren, muss ein Administrator ein Adobe-Support-Ticket für die Kundenunterstützung erstellen, um die Konfigurationsänderung für Ihr Dynamic Media-Konto anzufordern. Für die Aktivierung des Schutzes von Hotlinks fallen keine zusätzlichen Kosten an.
