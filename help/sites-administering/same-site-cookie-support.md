---
title: Same-Site-Cookie-Unterstützung für AEM 6.5
description: Erfahren Sie mehr über Same-Site-Cookie-Unterstützung für AEM 6.5
topic-tags: security
exl-id: e1616385-0855-4f70-b787-b01701929bbc
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c35bc059-fd80-4a01-91a6-e48da3c76758
    internal-label: Security practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%
---
# Same-Site-Cookie-Unterstützung für AEM 6.5 {#same-site-cookie-support-for-aem-65}

Seit Version 80 ist in Chrome und Safari ein neues Modell für die Sicherheit von Cookies enthalten. Dieser Modus führt mittels der Einstellung `SameSite` Sicherheitskontrollen für Cookies auf Drittanbieter-Sites ein. Weitere Informationen finden Sie in [diesem web.dev-Artikel, wo SameSite-Cookies erklärt werden](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM-Instanzen oder -Services nicht funktioniert. Dies liegt daran, dass die Domains oder URL-Strukturen dieser Services möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie das Cookie-Attribut `SameSite` für das Login-Token auf `None` setzen.

>[!CAUTION]
>
>Die Einstellung `SameSite=None` wird nur angewendet, wenn das Protokoll sicher ist (HTTPS).
>
>Wenn das Protokoll nicht sicher (HTTP) ist, wird die Einstellung ignoriert und der Server zeigt diese Warnmeldung:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

Sie können die Einstellung mit den nachfolgenden hinzufügen:

1. Wechseln Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf.
1. Legen Sie das **SameSite-Attribut für das Cookie des Anmelde-Tokens** auf `None` fest, wie in der Abbildung unten dargestellt.
   ![samesite](assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Sobald diese Einstellung aktualisiert wurde und Benutzer sich abgemeldet und erneut angemeldet haben, ist für `login-token`-Cookies das `None`-Attribut festgelegt und sie sind in den Site-übergreifenden Anforderungen enthalten.
