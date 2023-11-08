---
title: Das CSRF Protection Framework
description: Das Framework verwendet Token, um sicherzustellen, dass die Client-Anfrage legitim ist
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
source-git-commit: 941e5d7574d31622f50e50e717c21cd2eba2e602
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 40%

---

# Das CSRF Protection Framework {#the-csrf-protection-framework}

Zusätzlich zum Apache Sling Referrer Filter bietet Adobe auch ein neues CSRF Protection Framework zum Schutz vor Angriffen dieser Art.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Token werden generiert, wenn das Formular an den Client gesendet und validiert wird, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Für anonyme Benutzer gibt es in den Veröffentlichungsinstanzen keine Token.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die auf der `granite.jquery` Abhängigkeiten können automatisch vom CSRF Protection Framework profitieren. Ist dies nicht der Fall, müssen Sie für eine Ihrer Komponenten eine Abhängigkeit zu deklarieren von `granite.csrf.standalone` bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

Um die Token zu verwenden, müssen Sie die HMAC-Binärdatei auf allen Instanzen in Ihrer Implementierung replizieren. Siehe [Replizieren des HMAC-Schlüssels](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) für weitere Details.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie auch die erforderlichen [Dispatcher-Konfigurationsänderungen](https://helpx.adobe.com/de/experience-manager/dispatcher/user-guide.html) , um das CSRF Protection Framework zu verwenden.

>[!NOTE]
>
>Wenn Sie den Manifestcache mit Ihrer Webanwendung verwenden, stellen Sie sicher, dass Sie &quot;**&amp;ast;**&quot;, um sicherzustellen, dass das Token den CSRF-Token-Generierungsaufruf nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
