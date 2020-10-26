---
title: Content Services
seo-title: Content Services
description: 'null'
seo-description: 'null'
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 9%

---


# Content Services{#content-services}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Die Content Services-Funktion wird nur zu Zwecken der Vorschau dokumentiert.
>
>Es kann mit der Veröffentlichung von 6.3 GA Service Pack 1 geändert werden.

AEM Mobile Content Services ist eine einfache Funktion zum Anfordern von Inhalten, die von AEM verwaltet werden. Dadurch erhalten alle App-Entwickler eine leistungsstarke Möglichkeit, Inhalte abzurufen, ohne über umfassende Kenntnisse im Content Repository (JCR) und im Web Framework (Sling) verfügen zu müssen. Dadurch können die anfordernden Anwendungen vom Inhalts-Repository entkoppelt werden.

Content Services bietet verschiedene neue AEM-Konstrukte, die Entwicklern den Zugriff auf AEM verwalteten Inhalt ermöglichen, ohne die Repository-Struktur dieses Inhalts zu kennen.

Diese Konstrukte sind erforderlich, um Flexibilität zu gewährleisten und eine künftige Erweiterung zu ermöglichen, indem eine Abstraktionsebene zwischen den AEM verwalteten Inhalten und den mobilen Apps, die die Inhalte verbrauchen, bereitgestellt wird. Auf diese Weise kann AEM Content Services als Abstraktionsebene zwischen den Inhaltsanforderungen der nativen Anwendung und dem AEM Content Repository arbeiten.

Content Services kann die Inhalte als Assets, verpacktes HTML (HTML/CSS/JS) oder als Kanal-unabhängige Inhalte bereitstellen.

>[!CAUTION]
>
>**Voraussetzungen:**
>
>Bevor Sie mit Content Services beginnen, müssen Sie das Flag &quot;Content Services&quot;aktivieren. Um die Erstellung und Verwaltung von Modellen in Ihrer App zu aktivieren, müssen Sie Datenmodelle im Konfigurationsbrowser aktivieren.
>
>Weitere Informationen finden Sie unter **[Verwalten von Content Services](/help/mobile/developing-content-services.md)** und in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md) .

![chlimage_1-143](assets/chlimage_1-143.png)

Nachdem Sie das Flag &quot;Content Services&quot;und die Datenmodelle in Configuration Browser aktiviert haben, sehen Sie sich die folgenden Ressourcen an, um mit AEM Mobile Content Services zu beginnen. Lernen Sie die Content Services-Konzepte kennen, wie z. B. Modellverwaltung, Entitätsverwaltung, gefolgt von Content Versand/Rendering für AEM Mobile Content Services.

* Modelle im Repository
* Rendern und Versand
