---
title: Same-Site-Cookie-Unterstützung für AEM 6.5
description: Same-Site-Cookie-Unterstützung für AEM 6.5
topic-tags: security
exl-id: e1616385-0855-4f70-b787-b01701929bbc
source-git-commit: f7a4907ca6ce8ecaff9ef1fdf99ec0951ff497e0
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---

# Same-Site-Cookie-Unterstützung für AEM 6.5 {#same-site-cookie-support-for-aem-65}

Seit Version 80 ist in Chrome und Safari ein neues Modell für die Sicherheit von Cookies enthalten. Dieser Modus führt über die Einstellung `SameSite` Sicherheitskontrollen für Cookies auf Drittanbieter-Sites ein. Weitere Informationen finden Sie in diesem [Artikel](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM-Instanzen oder -Services nicht funktioniert. Dies liegt daran, dass die Domains oder URL-Strukturen dieser Services möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie das `SameSite`-Cookie-Attribut für das Anmelde-Token auf `None` festlegen.

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
