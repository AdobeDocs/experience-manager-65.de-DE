---
title: Das CSRF Protection Framework
seo-title: The CSRF Protection Framework
description: Das Framework verwendet Token, um sicherzustellen, dass die Client-Anfrage legitim ist
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 54%

---

# Das CSRF Protection Framework {#the-csrf-protection-framework}

Zusätzlich zum Apache Sling Referrer Filter bietet Adobe auch ein neues CSRF Protection Framework zum Schutz vor Angriffen dieser Art.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Token werden generiert, wenn das Formular an den Client gesendet und validiert wird, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Für anonyme Benutzer gibt es in den Veröffentlichungsinstanzen keine Token.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die sich auf die Abhängigkeit `granite.jquery` stützt, profitiert automatisch vom CSRF Protection Framework. Wenn dies für eine Ihrer Komponenten nicht der Fall ist, müssen Sie eine Abhängigkeit von `granite.csrf.standalone` deklarieren, bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

Um die Token zu nutzen, müssen Sie die HMAC-Binärdatei für alle Instanzen in Ihrer Implementierung replizieren. Siehe [Replizieren des HMAC-Schlüssels](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) für weitere Details.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie auch die erforderlichen [Dispatcher-Konfigurationsänderungen](https://helpx.adobe.com/de/experience-manager/dispatcher/user-guide.html) , um das CSRF Protection Framework zu verwenden.

>[!NOTE]
>
>Wenn Sie den Manifestcache mit Ihrer Webanwendung verwenden, stellen Sie sicher, dass Sie &quot;**&amp;ast;**&quot;, um sicherzustellen, dass das Token den CSRF-Token-Generierungsaufruf nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
