---
title: Content Services
description: Erfahren Sie, wie Sie mit AEM Mobile Content Services von AEM verwaltete Inhalte anfordern können.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 955ffb1c-4fa9-43bb-8e5b-2df7f2d17951
solution: Experience Manager
feature: Mobile
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 2%
---
# Content Services{#content-services}

{{ue-over-mobile}}

>[!CAUTION]
>
>Die Content Services-Funktion wird nur zu Vorschauzwecken dokumentiert.
>
>Sie kann sich mit Version 6.3 Service Pack 1 ändern.

AEM Mobile Content Services ist eine schlanke Funktion zum Anfordern von Inhalten, die von AEM verwaltet werden. Dadurch erhalten alle App-Entwickler eine leistungsstarke Möglichkeit, Inhalte abzurufen, ohne über fundierte Kenntnisse des Content-Repositorys (JCR) und des Web-Frameworks (Sling) von AEM verfügen zu müssen. Dadurch können die anfordernden Programme vom Content-Repository entkoppelt werden.

Content Services führt mehrere neue AEM-Konstrukte ein, die es Entwickelnden ermöglichen, ohne Kenntnis der Repository-Struktur dieser Inhalte auf von AEM verwaltete Inhalte zuzugreifen.

Diese Konstrukte sind erforderlich, um die Flexibilität aufrechtzuerhalten und eine zukünftige Erweiterung zu ermöglichen, indem eine Abstraktionsebene zwischen den von AEM verwalteten Inhalten und den mobilen Apps bereitgestellt wird, die die Inhalte nutzen. Dadurch können AEM Content Services als Abstraktionsebene zwischen den Inhaltsanforderungen des nativen Programms und dem AEM Content-Repository fungieren.

Content Services können die Inhalte als Assets, als gebündelte HTML (HTML/CSS/JS) oder als kanalunabhängige Inhalte bereitstellen.

>[!CAUTION]
>
>**Voraussetzungen:**
>
>Bevor Sie mit Content Services beginnen, stellen Sie sicher, dass Sie das Content Services-Flag aktivieren. Um die Erstellung und Verwaltung von Modellen in Ihrer App zu ermöglichen, aktivieren Sie Datenmodelle im Konfigurations-Browser.
>
>Weitere Informationen finden **[in der Dokumentation](/help/mobile/developing-content-services.md)** Verwalten von Content Services[&#x200B; und &#x200B;](/help/sites-administering/configurations.md)Konfigurations-Browser“.

![chlimage_1-143](assets/chlimage_1-143.png)

Nachdem Sie das Content Services-Flag festgelegt und Datenmodelle im Konfigurations-Browser aktiviert haben, finden Sie weitere Informationen zu den folgenden Ressourcen, um mit AEM Mobile Content Services zu beginnen. Machen Sie sich mit Content Services-Konzepten vertraut, z. B. Modell-Management und Entitätsverwaltung, gefolgt von der Bereitstellung/Wiedergabe von Inhalten für AEM Mobile Content Services.

* Modelle im Repository
* Rendering und Versand
