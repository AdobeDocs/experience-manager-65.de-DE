---
title: Single Sign-On
description: Erfahren Sie, wie Sie Single Sign-On (SSO) für eine Instanz von Adobe Experience Manager (AEM) konfigurieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring, Security
content-type: reference
feature: Security
exl-id: 7d2e4620-c3a5-4f5a-9eb6-42a706479d41
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 40%

---

# Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authenticator bezeichnet) führt die Authentifizierung durch und stellt Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft die Zugriffsberechtigungen und setzt diese für die Benutzerin oder den Benutzer durch (legt also fest, auf welche Ressourcen die Benutzerin oder der Benutzer zugreifen darf).

Der Handler-Dienst der SSO-Authentifizierung (`com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verarbeitet die von der vertrauenswürdigen Authentifizierung bereitgestellten Authentifizierungsergebnisse. Der SSO-Authentifizierungs-Handler sucht nach einer SSO-Kennung (SSID) als Wert eines speziellen Attributs an den folgenden Speicherorten in dieser Reihenfolge:

1. Anfrage-Header
1. Cookies
1. Anfrageparameter

Wenn ein Wert gefunden wird, ist die Suche abgeschlossen und dieser Wert wird verwendet.

Konfigurieren Sie die folgenden beiden Dienste, um den Namen des Attributs zu erkennen, das die SSID speichert:

* Das Anmeldemodul.
* Der SSO-Authentifizierungsdienst.

Geben Sie denselben Attributnamen für beide Services an. Das Attribut ist in den `SimpleCredentials` enthalten, die beim `Repository.login` angegeben werden. Der Wert des Attributs ist irrelevant und wird ignoriert. Das bloße Vorhandensein ist wichtig und wird überprüft.

## SSO konfigurieren {#configuring-sso}

Um SSO für eine AEM-Instanz zu konfigurieren, konfigurieren Sie [SSO Authentication Handler](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler):

1. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

   Beispielsweise für NTLM:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: `LOGON_USER`
   * **ID-Format**: `^<DOMAIN>\\(.+)$`

     Hierbei gilt `<*DOMAIN*>` wird durch den Namen Ihrer eigenen Domain ersetzt.

   Für CoSign:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: remote_user
   * **ID-Format:** AsIs

   Für SiteMinder:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen:** SM_USER
   * **ID-Format:** AsIs

1. Bestätigen Sie, dass Single Sign-on wie erforderlich funktioniert, einschließlich Autorisierung. 

>[!CAUTION]
>
>Stellen Sie sicher, dass Benutzende nicht direkt auf AEM zugreifen können, wenn SSO konfiguriert ist.
>
>Da Benutzer einen Webserver verwenden müssen, auf dem der Agent Ihres SSO-Systems ausgeführt wird, ist sichergestellt, dass kein Benutzer direkt eine Kopfzeile, ein Cookie oder einen Parameter senden kann, die dazu führen, dass der Benutzer von AEM als vertrauenswürdig eingestuft wird, da der Agent solche Informationen filtert, wenn sie von außen gesendet werden.
>
>Jeder Benutzer, der direkt auf Ihre AEM-Instanz zugreifen kann, ohne den Webserver zu verwenden, kann wie jeder andere Benutzer agieren, indem er die Kopfzeile, das Cookie oder den Parameter sendet, wenn die Namen bekannt sind.
>
>Stellen Sie außerdem sicher, dass Sie von Kopfzeilen, Cookies und Anfrageparameternamen nur den konfigurieren, der für Ihre SSO-Einrichtung erforderlich ist.
>

>[!NOTE]
>
>Single Sign-On wird häufig verwendet mit [LDAP](/help/sites-administering/ldap-config.md).

>[!NOTE]
>
>Wenn Sie außerdem die [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) mit dem Microsoft® Internet Information Server (IIS), ist dann eine zusätzliche Konfiguration erforderlich in:
>
>* `disp_iis.ini`
>* IIS
>
>Legen Sie in `disp_iis.ini` Folgendes fest:
>(siehe [Installieren des Dispatchers mit dem Microsoft® Internet Information Server](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install.html#microsoft-internet-information-server) Ausführliche Informationen)
>
>* `servervariables=1` (leitet IIS-Server-Variablen als Anforderungskopfzeilen an die Remote-Instanz weiter)
>* `replaceauthorization=1` (ersetzt alle Kopfzeilen mit dem Namen „Authorization“ mit Ausnahme von „Basic“ durch die Entsprechung von „Basic“)
>
>In IIS:
>
>* Deaktivieren Sie die Option **Anonymer Zugriff**.
>
>* aktivieren **Integrierte Windows-Authentifizierung**
>

Mithilfe der können Sie sehen, welcher Authentifizierungs-Handler auf einen beliebigen Abschnitt der Inhaltsstruktur angewendet wird. **Authenticator** Option der Felix-Konsole; zum Beispiel:

`http://localhost:4502/system/console/slingauth`

Der Handler, der zum größten Teil mit dem Pfad übereinstimmt, wird zuerst abgefragt. Falls Sie z. B. Handler-A für den Pfad `/` und Handler-B für den Pfad `/content` konfigurieren, wird bei einer Anforderung an `/content/mypage.html` zuerst Handler-B abgefragt.

![screen_shot_2012-02-15at21006pm](assets/screen_shot_2012-02-15at21006pm.png)

### Beispiel {#example}

Bei einer Cookie-Anforderung (mit der URL `http://localhost:4502/libs/wcm/content/siteadmin.html`):

```xml
GET /libs/cq/core/content/welcome.html HTTP/1.1
Host: localhost:4502
Cookie: TestCookie=admin
```

mit folgender Konfiguration:

* **Pfad**: `/`

* **Kopfzeilennamen**: `TestHeader`

* **Cookie-Namen**: `TestCookie`

* **Parameternamen**: `TestParameter`

* **ID-Format**: `AsIs`

sieht die Antwort wie folgt aus: 

```xml
HTTP/1.1 200 OK
Connection: Keep-Alive
Server: Day-Servlet-Engine/4.1.24
Content-Type: text/html;charset=utf-8
Date: Thu, 23 Aug 2012 09:58:39 GMT
Transfer-Encoding: chunked

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <title>Welcome to Adobe&reg; CQ5</title>
....
```

Dies funktioniert auch, wenn Sie Folgendes anfordern:
`http://localhost:4502/libs/cq/core/content/welcome.html?TestParameter=admin`

Sie können auch den folgenden curl-Befehl verwenden, um die `TestHeader`-Kopfzeile an `admin:` zu senden:
`curl -D - -H "TestHeader: admin" http://localhost:4502/libs/cq/core/content/welcome.html`

>[!NOTE]
>
>Bei Verwendung des Anforderungsparameters in einem Browser wird nur ein Teil der HTML angezeigt - ohne CSS. Dies liegt daran, dass alle Anfragen von der HTML ohne den Abfrageparameter erfolgen.

## Entfernen von AEM-Abmelde-Links {#removing-aem-sign-out-links}

Bei Verwendung von SSO werden die An- und Abmeldung extern verarbeitet, sodass AEM-eigene Abmelde-Links nicht mehr anwendbar sind und entfernt werden sollten.

Der Abmelde-Link auf dem Willkommensbildschirm kann mithilfe der folgenden Schritte entfernt werden.

1. Überlagern Sie `/libs/cq/core/components/welcome/welcome.jsp` über `/apps/cq/core/components/welcome/welcome.jsp`.
1. Entfernen Sie folgenden Teil aus der JSP-Datei:

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Um den Abmelde-Link zu entfernen, der im persönlichen Menü des Benutzers oben rechts verfügbar ist, führen Sie die folgenden Schritte aus:

1. Überlagern Sie `/libs/cq/ui/widgets/source/widgets/UserInfo.js` über `/apps/cq/ui/widgets/source/widgets/UserInfo.js`.

1. Entfernen Sie den folgenden Teil aus der Datei:

   ```
   menu.addMenuItem({
       "text":CQ.I18n.getMessage("Sign out"),
       "cls": "cq-userinfo-logout",
       "handler": this.logout
   });
   menu.addSeparator();
   ```
