---
title: Content Services
seo-title: Content Services
description: Content Services
seo-description: null
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
exl-id: 955ffb1c-4fa9-43bb-8e5b-2df7f2d17951
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# Content Services{#content-services}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Die Funktion Content Services wird nur zu Vorschauzwecken dokumentiert.
>
>Es kann mit der Veröffentlichung von 6.3 GA Service Pack 1 geändert werden.

AEM Mobile Content Services ist eine einfache Funktion zum Anfordern von Inhalten, die von AEM verwaltet werden. Dadurch erhalten alle App-Entwickler eine leistungsstarke Möglichkeit, Inhalte abzurufen, ohne über fundierte Kenntnisse im AEM Content Repository (JCR) und im Web-Framework (Sling) verfügen zu müssen. Dadurch können die anfragenden Anwendungen vom Inhalts-Repository entkoppelt werden.

Content Services führt mehrere neue AEM-Konstrukte ein, mit denen Entwickler auf AEM verwalteten Inhalt zugreifen können, ohne die Repository-Struktur dieses Inhalts zu kennen.

Diese Konstrukte sind erforderlich, um Flexibilität zu gewährleisten und eine künftige Erweiterung zu ermöglichen, indem eine Abstraktionsebene zwischen den AEM verwalteten Inhalten und den Apps, die den Inhalt konsumieren, bereitgestellt wird. Dadurch kann AEM Content Services als Abstraktionsebene zwischen den Inhaltsanforderungen der nativen Anwendung und dem AEM Content Repository funktionieren.

Content Services kann die Inhalte als Assets, verpackte HTML (HTML/CSS/JS) oder als kanalunabhängige Inhalte bereitstellen.

>[!CAUTION]
>
>**Voraussetzungen:**
>
>Stellen Sie vor dem Einstieg in Content Services sicher, dass Sie das Flag Content Services aktivieren. Um die Erstellung und Verwaltung von Modellen in Ihrer App zu aktivieren, müssen Sie Datenmodelle im Konfigurationsbrowser aktivieren.
>
>Siehe **[Verwalten von Content Services](/help/mobile/developing-content-services.md)** und [Konfigurationsbrowser](/help/sites-administering/configurations.md) Dokumentation finden Sie weitere Informationen.

![chlimage_1-143](assets/chlimage_1-143.png)

Nachdem Sie das Flag &quot;Content Services&quot;festgelegt und die Datenmodelle im Konfigurationsbrowser aktiviert haben, sehen Sie sich die unten stehenden Ressourcen an, um mit AEM Mobile Content Services zu beginnen. Machen Sie sich mit Content Services-Konzepten wie Modellverwaltung, Entitätsverwaltung, gefolgt von Inhaltsbereitstellung/-rendering für AEM Mobile Content Services vertraut.

* Modelle im Repository
* Rendering und Versand
