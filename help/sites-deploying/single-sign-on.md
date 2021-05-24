---
title: Single Sign-On
seo-title: Single Sign-On
description: Erfahren Sie, wie Sie Single Sign-On (SSO) für eine AEM-Instanz konfigurieren.
seo-description: Erfahren Sie, wie Sie Single Sign-On (SSO) für eine AEM-Instanz konfigurieren.
uuid: b8dcb28e-4604-4da5-b8dd-4e1e2cbdda18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring, Security
content-type: reference
discoiquuid: 86e8dc12-608d-4aff-ba7a-5524f6b4eb0d
feature: Konfiguration
exl-id: 7d2e4620-c3a5-4f5a-9eb6-42a706479d41
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 83%

---

# Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (der so genannte vertrauenswürdige Authentifikator) führt die Authentifizierung durch und liefert die Zugangsdaten an Experience Manager. Experience Manager überprüft diese und erzwingt die Zugriffsberechtigungen für den Benutzer (d. h. legt fest, auf welche Ressourcen der Benutzer zugreifen darf). 

Der Handler-Dienst der SSO-Authentifizierung (`com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verarbeitet die von der vertrauenswürdigen Authentifizierung bereitgestellten Authentifizierungsergebnisse. Der SSO-Authentifizierungs-Handler sucht nach einer SSID (SSO-Kennung) als Wert eines speziellen Attributs an folgenden Speicherorten in dieser Reihenfolge:

1. Anforderungskopfzeilen
1. Cookies
1. Anforderungsparameter

Wenn ein Wert gefunden wird, ist die Suche beendet und dieser Wert wird verwendet.

Konfigurieren Sie die folgenden beiden Dienste, um den Namen des Attributs zu identifizieren, in dem die SSID gespeichert ist:

* Das Anmeldemodul
* Den SSO-Authentifizierungsdienst

Sie müssen denselben Attributnamen für beide Dienste angeben. Das Attribut ist im `SimpleCredentials` enthalten, das `Repository.login` bereitgestellt wird. Der Wert des Attributs ist unwichtig und wird ignoriert. Nur das Vorhandensein ist wichtig und wird überprüft.

## Konfigurieren von SSO  {#configuring-sso}

Um SSO für eine AEM-Instanz zu konfigurieren, müssen Sie den [SSO-Authentifizierungs-Handler](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler) konfigurieren:

1. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Services. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

   Legen Sie beispielsweise für NTLM Folgendes fest:

   * **Pfad:** nach Bedarf; Beispiel:  `/`
   * **Kopfzeilennamen**:  `LOGON_USER`
   * **ID-Format**:  `^<DOMAIN>\\(.+)$`

      Dabei wird `<*DOMAIN*>` durch Ihren eigenen Domänennamen ersetzt.
   Für CoSign:

   * **Pfad:** nach Bedarf; Beispiel:  `/`
   * **Kopfzeilennamen**: remote_user
   * **ID-Format:** AsIs

   Für SiteMinder:

   * **Pfad:** nach Bedarf; Beispiel:  `/`
   * **Kopfzeilennamen:** SM_USER
   * **ID-Format:** AsIs



1. Bestätigen Sie, dass Single Sign-On wie erforderlich funktioniert, einschließlich Autorisierung. 

>[!CAUTION]
>
>Stellen Sie sicher, dass Benutzer nicht direkt auf AEM zugreifen können, falls SSO konfiguriert ist.
>
>Wenn der Benutzerzugriff ausschließlich über einen Webserver erfolgt, auf dem der Agent des SSO-Systems ausgeführt wird, ist sichergestellt, dass Benutzer nicht direkt Kopfzeilen, Cookies oder Parameter senden können, die von AEM als vertrauenswürdig eingestuft werden, da der Agent derartige von externen Standorten gesendete Daten filtert.
>
>Alle Benutzer, die direkt auf die AEM-Instanz zugreifen können (d. h. nicht über den Webserver) können als beliebige Benutzer agieren, indem sie Kopfzeilen, Cookies oder Parameter senden, falls ihnen die Namen bekannt sind.
>
>Stellen Sie auch sicher, dass Sie nur die Kopfzeilen, Kopien und Parameternamen von Anforderungen konfigurieren, die für das SSO-Setup erforderlich sind.


>[!NOTE]
>
>Single Sign-On wird oft zusammen mit [LDAP](/help/sites-administering/ldap-config.md) verwendet.

>[!NOTE]
>
>Falls Sie auch den [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) mit dem Microsoft Internet Information Server (IIS) verwenden, ist eine zusätzliche Konfiguration erforderlich:
>
>* `disp_iis.ini`
>* IIS

>
>
Legen Sie in `disp_iis.ini` Folgendes fest:
>(Weitere Informationen finden Sie unter [Installieren des Dispatchers mit dem Microsoft Internet Information Server](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html#microsoft-internet-information-server) .)
>
>* `servervariables=1` (leitet IIS-Servervariablen als Anforderungskopfzeilen an die Remote-Instanz weiter)
>* `replaceauthorization=1` (ersetzt alle Kopfzeilen mit dem Namen „Authorization“ mit Ausnahme von „Basic“ durch die Entsprechung von „Basic“)

>
>
In IIS:
>
>* Deaktivieren Sie die Option **Anonymer Zugriff**.
   >
   >
* Aktivieren Sie die Option **Integrierte Windows-Authentifizierung**.

>



Mithilfe der **Authentifizierungs**-Option in der Felix-Konsole können Sie sehen, welcher Authentifizierungs-Handler auf welchen Abschnitt in der Inhaltsstruktur angewendet wird, z. B.:

`http://localhost:4502/system/console/slingauth`

Der Handler, der zum größten Teil mit dem Pfad übereinstimmt, wird zuerst abgefragt. Wenn Sie beispielsweise Handler-A für den Pfad `/` und Handler-B für den Pfad `/content` konfigurieren, fragt eine Anfrage an `/content/mypage.html` zuerst Handler-B ab.

![screen_shot_2012-02-15at21006pm](assets/screen_shot_2012-02-15at21006pm.png)

### Beispiel {#example}

Für eine Cookie-Anforderung (unter Verwendung der URL `http://localhost:4502/libs/wcm/content/siteadmin.html`):

```xml
GET /libs/cq/core/content/welcome.html HTTP/1.1
Host: localhost:4502
Cookie: TestCookie=admin
```

mit folgender Konfiguration:

* **Pfad**: `/`

* **Kopfzeilennamen**:  `TestHeader`

* **Cookie-Namen**:  `TestCookie`

* **Parameternamen**:  `TestParameter`

* **ID-Format**:  `AsIs`

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

Oder Sie können den folgenden curl-Befehl verwenden, um die Kopfzeile `TestHeader` an `admin:` zu senden
`curl -D - -H "TestHeader: admin" http://localhost:4502/libs/cq/core/content/welcome.html`

>[!NOTE]
>
>Bei Verwendung des Anforderungsparameters in einem Browser sehen Sie nur einen Teil des HTML-Codes ohne CSS. Dies liegt daran, dass alle Anforderungen aus dem HTML-Code ohne den Anforderungsparameter erfolgen.

## Entfernen des AEM-Abmelde-Links  {#removing-aem-sign-out-links}

Bei Verwendung von SSO werden An- und Abmeldung extern gehandhabt, sodass die AEM-Abmelde-Links nicht mehr gültig sind und entfernt werden sollten.

Sie können den Abmelde-Link auf dem Begrüßungsbildschirm mit folgenden Schritten entfernen.

1. Überlagern Sie `/libs/cq/core/components/welcome/welcome.jsp` in `/apps/cq/core/components/welcome/welcome.jsp`
1. Entfernen Sie folgenden Teil aus der JSP-Datei:

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Um den Abmelde-Link oben rechts aus dem persönlichen Menü des Benutzers zu entfernen, folgen Sie diesen Schritten:

1. Überlagern Sie `/libs/cq/ui/widgets/source/widgets/UserInfo.js` in `/apps/cq/ui/widgets/source/widgets/UserInfo.js`

1. Entfernen Sie den folgenden Teil aus der Datei:

   ```
   menu.addMenuItem({
       "text":CQ.I18n.getMessage("Sign out"),
       "cls": "cq-userinfo-logout",
       "handler": this.logout
   });
   menu.addSeparator();
   ```
