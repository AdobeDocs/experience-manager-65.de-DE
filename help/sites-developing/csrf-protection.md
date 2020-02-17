---
title: Das CSRF Protection Framework
seo-title: Das CSRF Protection Framework
description: Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist
seo-description: Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
translation-type: tm+mt
source-git-commit: c83c77c5c313099944dd73c8cbe63d429d84a518

---


# Das CSRF Protection Framework{#the-csrf-protection-framework}

Neben dem Apache Sling Referrer Filter bietet Adobe zudem ein neues CSRF Protection Framework zum Schutz vor dieser Art von Angriffen.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Tokens werden erzeugt, wenn das Formular an den Client gesendet wird, und validiert, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Es gibt keine Token für anonyme Benutzer in den Veröffentlichungsinstanzen.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die sich auf die Abhängigkeit `granite.jquery` stützt, profitiert automatisch vom CSRF Protection Framework. Wenn dies für eine Ihrer Komponenten nicht der Fall ist, müssen Sie eine Abhängigkeit von `granite.csrf.standalone` deklarieren, bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

In order to make use of the tokens, you need to replicate the `/etc/keys/hmac` binary to all of the instances in your deployment. Eine bequeme Möglichkeit, den HMAC-Schlüssel in alle Instanzen zu kopieren, besteht darin, ein Paket zu erstellen, das den Schlüssel enthält, und ihn über Package Manager auf alle Instanzen zu installieren.

>[!NOTE]
>
>Achten Sie darauf, auch die notwendigen [Dispatcher-Konfigurationsänderungen](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) vorzunehmen, um das CSRF Protection Framework zu verwenden.

>[!NOTE]
>
>If you use the manifest cache with your web application, make sure you add &quot;**&amp;ast;**&quot; to the manifest in order to make sure the token does not take the CSRF token generation call offline. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
