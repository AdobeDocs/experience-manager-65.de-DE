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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Content Services{#content-services}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Die Content Services-Funktion wird nur zu Vorschauzwecken dokumentiert.
>
>Es kann mit der Veröffentlichung von 6.3 GA Service Pack 1 geändert werden.

AEM Mobile Content Services ist eine einfache Funktion zum Anfordern von Inhalten, die von AEM verwaltet werden. Dadurch erhalten alle App-Entwickler eine leistungsstarke Möglichkeit, Inhalte abzurufen, ohne über umfassende Kenntnisse des Inhalts-Repository (JCR) und des Web-Frameworks (Sling) von AEM verfügen zu müssen. Dadurch können die anfordernden Anwendungen vom Inhalts-Repository entkoppelt werden.

Content Services stellt mehrere neue AEM-Konstrukte vor, mit denen Entwickler auf AEM-verwaltete Inhalte zugreifen können, ohne die Repository-Struktur dieses Inhalts zu kennen.

Diese Konstrukte sind erforderlich, um Flexibilität zu gewährleisten und eine künftige Erweiterung zu ermöglichen, indem eine Abstraktionsebene zwischen den von AEM verwalteten Inhalten und den mobilen Apps, die den Inhalt konsumieren, bereitgestellt wird. Dadurch kann AEM Content Services als Abstraktionsebene zwischen den Inhaltsanforderungen der nativen Anwendung und dem AEM-Inhalts-Repository verwendet werden.

Content Services kann die Inhalte als Assets, verpacktes HTML (HTML/CSS/JS) oder als kanalunabhängige Inhalte bereitstellen.

>[!CAUTION]
>
>**Voraussetzungen:**
>
>Bevor Sie mit Content Services beginnen, müssen Sie das Flag &quot;Content Services&quot;aktivieren. Um die Erstellung und Verwaltung von Modellen in Ihrer App zu aktivieren, müssen Sie Datenmodelle im Konfigurationsbrowser aktivieren.
>
>Weitere Informationen finden Sie unter **[Verwalten von Content Services](/help/mobile/developing-content-services.md)**.

![chlimage_1-143](assets/chlimage_1-143.png)

Nachdem Sie das Flag &quot;Content Services&quot;und die Datenmodelle in Configuration Browser aktiviert haben, sehen Sie sich die folgenden Ressourcen an, um mit AEM Mobile Content Services zu beginnen, und lernen Sie die Content Services-Konzepte kennen, wie z. B. Modellverwaltung, Entitätsverwaltung und anschließende Inhaltsbereitstellung/-wiedergabe für AEM Mobile Content Services.

* Modelle im Repository
* Wiedergabe und Bereitstellung

