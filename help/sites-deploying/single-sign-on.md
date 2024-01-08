---
title: Single Sign-On
description: Erfahren Sie, wie Sie Single Sign-On (SSO) für eine Instanz von Adobe Experience Manager (AEM) konfigurieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring, Security
content-type: reference
feature: Configuring
exl-id: 7d2e4620-c3a5-4f5a-9eb6-42a706479d41
source-git-commit: 3bcdbfc17efe1f4c6069fd97fd6a16ec41d0579e
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 40%

---

# Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authenticator bezeichnet) führt die Authentifizierung durch und stellt Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft die Zugriffsberechtigungen und setzt diese für die Benutzerin oder den Benutzer durch (legt also fest, auf welche Ressourcen die Benutzerin oder der Benutzer zugreifen darf).

Der Handler-Dienst der SSO-Authentifizierung (`com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verarbeitet die von der vertrauenswürdigen Authentifizierung bereitgestellten Authentifizierungsergebnisse. Der SSO-Authentifizierungs-Handler sucht nach einer SSO-Kennung (SSO Identifier, SSID) als Wert eines speziellen Attributs an den folgenden Stellen in dieser Reihenfolge:

1. Anforderungsheader
1. Cookies
1. Anfrageparameter

Wenn ein Wert gefunden wird, ist die Suche abgeschlossen und dieser Wert wird verwendet.

Konfigurieren Sie die folgenden beiden Dienste, um den Namen des Attributs zu erkennen, in dem die SSID gespeichert wird:

* Das Anmeldemodul.
* Der SSO-Authentifizierungsdienst.

Geben Sie für beide Dienste denselben Attributnamen an. Das Attribut ist in den `SimpleCredentials` enthalten, die beim `Repository.login` angegeben werden. Der Wert des Attributs ist irrelevant und wird ignoriert, das bloße Vorhandensein ist wichtig und verifiziert.

## Konfigurieren von SSO {#configuring-sso}

Um SSO für eine AEM-Instanz zu konfigurieren, konfigurieren Sie die [SSO-Authentifizierungs-Handler](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler):

1. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

   Beispiel: für NTLM-Satz:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: `LOGON_USER`
   * **ID-Format**: `^<DOMAIN>\\(.+)$`

     Wo `<*DOMAIN*>` durch den Namen Ihrer eigenen Domäne ersetzt.

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
>Stellen Sie sicher, dass Benutzer nicht direkt auf AEM zugreifen können, wenn SSO konfiguriert ist.
>
>Durch die Anforderung, dass Benutzer einen Webserver durchlaufen müssen, auf dem der Agent Ihres SSO-Systems ausgeführt wird, wird sichergestellt, dass kein Benutzer direkt einen Header, ein Cookie oder einen Parameter sendet, der dazu führt, dass der Benutzer von AEM als vertrauenswürdig eingestuft wird, da der Agent diese Informationen filtert, wenn sie von außen gesendet werden.
>
>Jeder Benutzer, der direkt auf Ihre AEM-Instanz zugreifen kann, ohne den Webserver zu durchlaufen, kann wie jeder Benutzer agieren, indem er die Kopfzeile, das Cookie oder den Parameter sendet, sofern die Namen bekannt sind.
>
>Stellen Sie außerdem sicher, dass Sie bei Headern, Cookies und Anforderungsparametern nur den konfigurieren, der für Ihre SSO-Einrichtung erforderlich ist.
>

>[!NOTE]
>
>Single Sign-On wird häufig mit [LDAP](/help/sites-administering/ldap-config.md).

>[!NOTE]
>
>Wenn Sie auch die [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) Mit dem Microsoft® Internet Information Server (IIS) ist eine zusätzliche Konfiguration erforderlich in:
>
* `disp_iis.ini`
* IIS
>
In `disp_iis.ini` festgelegt ist (siehe [Installieren des Dispatchers mit dem Microsoft® Internet Information Server](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install.html#microsoft-internet-information-server) für alle Einzelheiten)
>
* `servervariables=1` (leitet IIS-Server-Variablen als Anforderungskopfzeilen an die Remote-Instanz weiter)
* `replaceauthorization=1` (ersetzt alle Kopfzeilen mit dem Namen „Authorization“ mit Ausnahme von „Basic“ durch die Entsprechung von „Basic“)
>
In IIS:
>
* Deaktivieren Sie die Option **Anonymer Zugriff**.
>
* enable **Integrierte Windows-Authentifizierung**
>

Mithilfe der **Authenticator** -Option der Felix-Konsole, z. B.:

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
Wenn Sie den Anforderungsparameter in einem Browser verwenden, sehen Sie nur einige der HTML - ohne CSS. Dies liegt daran, dass alle Anfragen von der HTML ohne den Anforderungsparameter durchgeführt werden.

## Entfernen AEM Abmelde-Links {#removing-aem-sign-out-links}

Bei Verwendung von SSO werden Anmelden und Abmelden extern verarbeitet, sodass AEM eigenen Abmelde-Links nicht mehr anwendbar sind und entfernt werden sollten.

Der Abmelde-Link auf dem Willkommensbildschirm kann mithilfe der folgenden Schritte entfernt werden.

1. Überlagern Sie `/libs/cq/core/components/welcome/welcome.jsp` über `/apps/cq/core/components/welcome/welcome.jsp`.
1. Entfernen Sie folgenden Teil aus der JSP-Datei:

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Gehen Sie wie folgt vor, um den Abmelde-Link zu entfernen, der oben rechts im persönlichen Menü des Benutzers verfügbar ist:

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
