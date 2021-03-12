---
title: Selbe Site-Cookie-Unterstützung für AEM 6.5
description: Selbe Site-Cookie-Unterstützung für AEM 6.5
topic-tags: security
translation-type: tm+mt
source-git-commit: ac2f3d69fd20d7779120a194c698d6f0dd6e6a84
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# Selbe Site-Cookie-Unterstützung für AEM 6.5 {#same-site-cookie-support-for-aem-65}

Seit Version 80 haben Chrome und Safari ein neues Modell für die Sicherheit von Cookies eingeführt. Dieser Modus ist so konzipiert, dass Sicherheitskontrollen zur Verfügbarkeit von Cookies für Drittanbieter-Sites eingeführt werden, indem die Einstellung `SameSite` festgelegt wird. Weitere Informationen finden Sie in diesem [Artikel](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM Instanzen oder Diensten nicht funktioniert. Dies liegt daran, dass die Domänen oder URL-Strukturen dieser Dienste möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie für das Login-Token das Attribut SameSite-Cookie auf `None` setzen.

Gehen Sie dazu wie folgt vor:

1. Gehen Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf
1. Setzen Sie das Attribut **SameSite für das Cookie login-token** auf `None`, wie in der Abbildung unten dargestellt
   ![samesite](assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Sobald diese Einstellung aktualisiert und Benutzer erneut abgemeldet und angemeldet sind, wird für `login-token`-Cookies das `None`-Attribut festgelegt und in Site-übergreifende Anforderungen aufgenommen.
