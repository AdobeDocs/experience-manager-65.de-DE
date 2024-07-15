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
ht-degree: 100%

---

# Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authenticator bezeichnet) führt die Authentifizierung durch und stellt Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft die Zugriffsberechtigungen und setzt diese für die Benutzerin oder den Benutzer durch (legt also fest, auf welche Ressourcen die Benutzerin oder der Benutzer zugreifen darf).

Der Handler-Dienst der SSO-Authentifizierung (`com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verarbeitet die von der vertrauenswürdigen Authentifizierung bereitgestellten Authentifizierungsergebnisse. Der SSO-Authentifizierungs-Handler sucht nach einer SSO-Kennung (SSID) als Wert eines speziellen Attributs an folgenden Stellen und in dieser Reihenfolge:

1. Anfrage-Headern
1. Cookies
1. Anforderungsparametern

Wenn ein Wert gefunden wird, ist die Suche beendet und dieser Wert wird verwendet.

Konfigurieren Sie die folgenden beiden Dienste, um den Namen des Attributs zu identifizieren, in dem die SSID gespeichert ist:

* Anmeldemodul.
* SSO-Authentifizierungsdienst.

Geben Sie denselben Attributnamen für beide Dienste an. Das Attribut ist in den `SimpleCredentials` enthalten, die beim `Repository.login` angegeben werden. Der Wert des Attributs ist unwichtig und wird ignoriert. Er muss einfach nur vorhanden sein, und genau dies wird überprüft.

## Konfigurieren von SSO {#configuring-sso}

Um SSO für eine AEM-Instanz zu konfigurieren, konfigurieren Sie den [SSO-Authentifizierungs-Handler](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler):

1. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

   Legen Sie beispielsweise für NTLM Folgendes fest:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: `LOGON_USER`
   * **ID-Format**: `^<DOMAIN>\\(.+)$`

     `<*DOMAIN*>` steht dabei für den Namen Ihrer eigenen Domain.

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
>Stellen Sie sicher, dass Benutzende nicht direkt auf AEM zugreifen können, falls SSO konfiguriert ist.
>
>Wenn der Benutzerzugriff ausschließlich über einen Webserver erfolgt, auf dem der Agent Ihres SSO-Systems ausgeführt wird, ist sichergestellt, dass Benutzende nicht direkt Header, Cookies oder Parameter senden können, die dazu führen, dass Benutzende von AEM als vertrauenswürdig eingestuft werden, da der Agent derartige von externen Standorten gesendete Daten filtert.
>
>Alle Benutzenden, die direkt auf die AEM-Instanz zugreifen können (d. h. nicht über den Webserver) können als beliebige Benutzende agieren, indem sie Header, Cookies oder Parameter senden, sofern die Namen bekannt sind.
>
>Stellen Sie auch sicher, dass Sie nur die Header-, Cookies- und Anfrageparameternamen konfigurieren, die für das SSO-Setup erforderlich sind.
>

>[!NOTE]
>
>Single Sign-On wird häufig zusammen mit [LDAP](/help/sites-administering/ldap-config.md) verwendet.

>[!NOTE]
>
>Falls Sie auch den [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) mit Microsoft® Internet Information Server (IIS) verwenden, ist eine zusätzliche Konfiguration erforderlich:
>
>* `disp_iis.ini`
>* IIS
>
>Legen Sie in `disp_iis.ini` Folgendes fest:
>(Einzelheiten finden Sie unter [Installieren des Dispatchers mit Microsoft® Internet Information Server](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install.html?lang=de#microsoft-internet-information-server))
>
>* `servervariables=1` (leitet IIS-Server-Variablen als Anforderungskopfzeilen an die Remote-Instanz weiter)
>* `replaceauthorization=1` (ersetzt alle Kopfzeilen mit dem Namen „Authorization“ mit Ausnahme von „Basic“ durch die Entsprechung von „Basic“)
>
>In IIS:
>
>* Deaktivieren Sie die Option **Anonymer Zugriff**.
>
>* Aktivieren Sie die Option **Integrierte Windows-Authentifizierung**
>

Mithilfe der **Authentifizierungsoption** in der Felix-Konsole können Sie sehen, welcher Authentifizierungs-Handler auf welchen Abschnitt in der Inhaltsstruktur angewendet wird, z. B.:

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
>Bei Verwendung des Anfrageparameters in einem Browser sehen Sie nur einen Teil des HTML-Codes ohne CSS. Dies liegt daran, dass alle Anfragen aus dem HTML-Code ohne den Anfrageparameter erfolgen.

## Entfernen von AEM-Abmelde-Links {#removing-aem-sign-out-links}

Bei Verwendung von SSO werden An- und Abmeldung extern gehandhabt, sodass AEM-Abmelde-Links nicht mehr gültig sind und entfernt werden sollten.

Sie können den Abmelde-Link auf dem Begrüßungsbildschirm mit folgenden Schritten entfernen:

1. Überlagern Sie `/libs/cq/core/components/welcome/welcome.jsp` über `/apps/cq/core/components/welcome/welcome.jsp`.
1. Entfernen Sie folgenden Teil aus der JSP-Datei:

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Gehen Sie wie folgt vor, um den Abmelde-Link oben rechts im persönlichen Menü der Benutzerin oder des Benutzers zu entfernen:

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
