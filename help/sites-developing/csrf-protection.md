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
source-git-commit: 8d7c5b4962ea0dbd80cf78faa31238b2252f4a5c
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%

---

# Das CSRF Protection Framework {#the-csrf-protection-framework}

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
>Wenn Sie den Manifest-Cache mit Ihrer Web-Anwendung verwenden, stellen Sie sicher, dass Sie „*****“ zum Manifest hinzufügen, damit das Token die CSRF-Token-Erzeugungsanforderung nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
