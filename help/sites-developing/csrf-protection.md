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
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 72%

---

# Das CSRF Protection Framework{#the-csrf-protection-framework}

Neben dem Apache Sling Referrer Filter bietet Adobe zudem ein neues CSRF Protection Framework zum Schutz vor dieser Art von Angriffen.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Tokens werden erzeugt, wenn das Formular an den Client gesendet wird, und validiert, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Für anonyme Benutzer gibt es in den Veröffentlichungsinstanzen keine Token.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die sich auf die Abhängigkeit `granite.jquery` stützt, profitiert automatisch vom CSRF Protection Framework. Wenn dies für eine Ihrer Komponenten nicht der Fall ist, müssen Sie eine Abhängigkeit von `granite.csrf.standalone` deklarieren, bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

Um die Token zu nutzen, müssen Sie die `/etc/keys/hmac` -Binärdatei für alle Instanzen in Ihrer Implementierung replizieren. Eine bequeme Möglichkeit, den HMAC-Schlüssel in alle Instanzen zu kopieren, besteht darin, ein Paket zu erstellen, das den Schlüssel enthält, und ihn über Package Manager auf alle Instanzen zu installieren.

>[!NOTE]
>
>Achten Sie darauf, auch die notwendigen [Dispatcher-Konfigurationsänderungen](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) vorzunehmen, um das CSRF Protection Framework zu verwenden.

>[!NOTE]
>
>Wenn Sie den Manifestcache mit Ihrer Webanwendung verwenden, stellen Sie sicher, dass Sie &quot;**&amp;ast;**&quot;zum Manifest hinzufügen, um sicherzustellen, dass das Token den Aufruf zur Erstellung von CSRF-Token nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
