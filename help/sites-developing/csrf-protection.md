---
title: Das CSRF Protection Framework
description: Das Framework verwendet Token, um sicherzustellen, dass die Client-Anfrage legitim ist
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 88%
---
# Das CSRF Protection Framework{#the-csrf-protection-framework}

Neben dem Apache Sling Referrer Filter bietet Adobe zudem ein neues CSRF Protection Framework zum Schutz vor dieser Art von Angriffen.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Token werden erzeugt, wenn das Formular an den Client gesendet wird, und validiert, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Für anonyme Benutzer gibt es in den Veröffentlichungsinstanzen keine Token.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die sich auf die Abhängigkeit `granite.jquery` stützt, profitiert automatisch vom CSRF Protection Framework. Wenn dies für eine Ihrer Komponenten nicht der Fall ist, müssen Sie eine Abhängigkeit von `granite.csrf.standalone` deklarieren, bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

Um die Token nutzen zu können, müssen Sie die HMAC-Binärdatei auf alle Instanzen in Ihrer Bereitstellung replizieren. Siehe [Replizieren des HMAC-Schlüssels](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) für weitere Details.

>[!NOTE]
>
>Achten Sie darauf, auch die notwendigen Dispatcher-Konfigurationsänderungen vorzunehmen, um das CSRF Protection Framework zu verwenden:
>
>* [Konfigurieren von Adobe Experience Manager Dispatcher zum Verhindern von CSRF-Angriffen](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/configuring/configuring-dispatcher-to-prevent-csrf)
>* [Dispatcher-Überblick](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher)

>[!NOTE]
>
>Wenn Sie den Manifest-Cache mit Ihrer Web-Anwendung verwenden, stellen Sie sicher, dass Sie &quot;**&ast;**&quot; zum Manifest hinzufügen, damit das Token die CSRF-Token-Erzeugungsanforderung nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
