---
title: Content Services
description: Erfahren Sie, wie Sie mit AEM Mobile Content Services Inhalte anfordern können, die von AEM verwaltet werden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 955ffb1c-4fa9-43bb-8e5b-2df7f2d17951
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 8%

---

# Content Services{#content-services}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Die Funktion Content Services wird nur zu Vorschauzwecken dokumentiert.
>
>Es kann mit der Veröffentlichung von 6.3 Service Pack 1 geändert werden.

AEM Mobile Content Services ist eine einfache Funktion zum Anfordern von Inhalten, die von AEM verwaltet werden. Dadurch erhalten alle App-Entwickler eine leistungsstarke Möglichkeit, Inhalte abzurufen, ohne über fundierte Kenntnisse des Content-Repository (JCR) und des Web-Frameworks (Sling) AEM zu verfügen. Dadurch können die anfragenden Anwendungen vom Inhalts-Repository entkoppelt werden.

Content Services führt mehrere neue AEM-Konstrukte ein, mit denen Entwickler auf AEM verwalteten Inhalt zugreifen können, ohne die Repository-Struktur dieses Inhalts zu kennen.

Diese Konstrukte sind erforderlich, um Flexibilität zu gewährleisten und eine künftige Erweiterung zu ermöglichen, indem eine Abstraktionsebene zwischen den AEM verwalteten Inhalten und den Apps bereitgestellt wird, die den Inhalt verbrauchen. Dadurch kann AEM Content Services als Abstraktionsebene zwischen den Inhaltsanforderungen der nativen Anwendung und dem AEM Content Repository funktionieren.

Content Services kann die Inhalte als Assets, verpackte HTML (HTML/CSS/JS) oder als kanalunabhängige Inhalte bereitstellen.

>[!CAUTION]
>
>**Voraussetzungen:**
>
>Bevor Sie mit Content Services beginnen, müssen Sie das Flag Content Services aktivieren. Um die Erstellung und Verwaltung von Modellen in Ihrer App zu aktivieren, aktivieren Sie Datenmodelle im Konfigurationsbrowser.
>
>Weitere Informationen finden Sie unter **[Verwalten von Content Services](/help/mobile/developing-content-services.md)** und in der Dokumentation zum [Konfigurations-Browser](/help/sites-administering/configurations.md) .

![chlimage_1-143](assets/chlimage_1-143.png)

Nachdem Sie das Flag &quot;Content Services&quot;festgelegt und Datenmodelle im Konfigurationsbrowser aktiviert haben, finden Sie in den unten stehenden Ressourcen eine Anleitung zu AEM Mobile Content Services. Machen Sie sich mit Content Services-Konzepten wie Modellverwaltung, Entitätsverwaltung, gefolgt von Inhaltsbereitstellung/-rendering für AEM Mobile Content Services vertraut.

* Modelle im Repository
* Rendering und Versand
