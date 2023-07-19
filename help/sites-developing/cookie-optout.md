---
title: Konfigurieren der Verwendung von Cookies
seo-title: Configuring Cookie Usage
description: AEM bietet einen Dienst, mit dem Sie konfigurieren und steuern können, wie Cookies mit Ihren Webseiten verwendet werden
seo-description: AEM provides a service that enables you to configure and control how cookies are used with your web pages
uuid: 10d95176-0a56-41f1-9d36-01dbdac757d4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 5773ec1a-f15b-462d-8f9f-54ee1d7ead44
exl-id: 42e8d804-6b6a-432e-a651-940b9f45db4e
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 40%

---

# Konfigurieren der Verwendung von Cookies{#configuring-cookie-usage}

AEM bietet einen Dienst, mit dem Sie konfigurieren und steuern können, wie Cookies mit Ihren Webseiten verwendet werden:

* Ein konfigurierbarer Server-seitiger Dienst verwaltet eine Liste von Cookies, die verwendet werden können.
* Mit einer JavaScript-API kann Ihr JavaScript-Code überprüfen, ob ein Cookie verwendet werden kann.

Verwenden Sie diese Funktion, um sicherzustellen, dass Ihre Seiten die Zustimmung Ihrer Benutzer zur Cookie-Nutzung einhalten.

## Konfigurieren zulässiger Cookies {#configuring-allowed-cookies}

Konfigurieren Sie den Opt-out-Dienst der Adobe Granite , um festzulegen, wie Cookies auf Ihren Webseiten verwendet werden. In der folgenden Tabelle werden die Eigenschaften beschrieben, die Sie konfigurieren können.

Zum Konfigurieren des Dienstes können Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) verwenden oder [eine OSGi-Konfiguration zum Repository hinzufügen](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). In der folgenden Tabelle werden die Eigenschaften beschrieben, die für beide Methoden erforderlich sind. Für eine OSGi-Konfiguration lautet die PID des Dienstes `com.adobe.granite.optout`.

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname | Beschreibung |
|---|---|---|
| Opt-out-Cookies | optout.cookies | Die Namen von Cookies, die, wenn sie auf dem Gerät des Benutzers vorhanden sind, anzeigen, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat. |
| HTTP-Header für Opt-out | optout.headers | Die Namen der HTTP-Header, die, wenn vorhanden, anzeigen, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat. |
| Cookies auf der Zulassungsliste | optout.whitelist.cookies | Eine Liste von Cookies, die für die Funktionalität der Website unerlässlich sind und ohne Zustimmung des Benutzers verwendet werden können. |

## Validieren der Cookie-Nutzung {#validating-cookie-usage}

Verwenden Sie Client-seitiges JavaScript, um den Adobe Granite Opt-Out Service aufzurufen und zu überprüfen, ob Sie Cookies verwenden können. Verwenden Sie das JavaScript-Objekt Granite.OptOutUtil , um eine der folgenden Aufgaben auszuführen:

* Rufen Sie eine Liste mit Cookie-Namen ab, die darauf hinweisen, dass der Benutzer der Verwendung von Cookies zu Tracking-Zwecken nicht zustimmt.
* Rufen Sie eine Liste von Cookies ab, die verwendet werden können.
* Bestimmen Sie, ob der Webbrowser ein Cookie enthält, das anzeigt, dass der Benutzer der Verwendung von Cookies zum Tracking nicht zustimmt.
* Bestimmen Sie, ob ein bestimmtes Cookie verwendet werden kann.

Die granite.utils [Client-Bibliotheksordner](/help/sites-developing/clientlibs.md#referencing-client-side-libraries) stellt das Objekt Granite.OptOutUtil bereit. Fügen Sie Ihrem Seitenkopf-JSP den folgenden Code hinzu, um einen Link zur JavaScript-Bibliothek einzuschließen:

`<ui:includeClientLib categories="granite.utils" />`

Beispielsweise bestimmt die folgende JavaScript-Funktion, ob das Cookie COOKIE_NAME vor dem Schreiben in verwendet werden darf:

```
function writeCookie(value){
   if (!Granite.OptOutUtil.maySetCookie("COOKIE_NAME"))
      return;
   if (value) {
      value = encodeURIComponent(value);
      document.cookie = "COOKIE_NAME=" + value;
   }
}
```

## Das Granite.OptOutUtil-JavaScript-Objekt {#the-granite-optoututil-javascript-object}

Mit Granite.OptOutUtil können Sie bestimmen, ob die Verwendung von Cookies zulässig ist.

### Funktion &quot;getCookieNames()&quot; {#getcookienames-function}

Gibt die Namen der Cookies zurück, die, sofern vorhanden, darauf hinweisen, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat.

**Parameter**

Ohne.

**Rückgabe**

Ein Array von Cookie-Namen.

#### Funktion &quot;getWhitelistCookieNames()&quot; {#getwhitelistcookienames-function}

Gibt die Namen der Cookies zurück, die unabhängig von der Zustimmung des Benutzers verwendet werden können.

**Parameter**

Ohne.

**Rückgabe**

Ein Array von Cookie-Namen.

#### isOptedOut()-Funktion {#isoptedout-function}

Bestimmt, ob der Browser des Benutzers Cookies enthält, die darauf hinweisen, dass die Verwendung von Cookies nicht genehmigt wurde.

**Parameter**

Ohne.

**Rückgabe**

Einen booleschen Wert, der `true` lautet, wenn ein Cookie gefunden wird, das darauf hinweist, dass keine Zustimmung erteilt wurde, und `false` lautet, wenn kein Cookie darauf hinweist, dass keine Zustimmung erteilt wurde.

### Funktion &quot;maySetCookie(cookieName)&quot; {#maysetcookie-cookiename-function}

Bestimmt, ob ein bestimmtes Cookie im Browser des Benutzers verwendet werden kann. Diese Funktion entspricht der Verwendung der Funktion `isOptedOut`, wobei zusätzlich ermittelt wird, ob das angegebene Cookie in der Liste enthalten ist, die die Funktion `getWhitelistCookieNames` zurückgibt.

**Parameter**

* cookieName: Zeichenfolge. Der Name des Cookies.

**Rückgabe**

Einen booleschen Wert, der `true` lautet, wenn `cookieName` verwendet werden kann, oder `false` lautet, wenn `cookieName` nicht verwendet werden kann.
