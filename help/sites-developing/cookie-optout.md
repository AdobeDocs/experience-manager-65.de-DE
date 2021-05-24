---
title: Konfigurieren der Verwendung von Cookies
seo-title: Konfigurieren der Verwendung von Cookies
description: AEM bietet einen Dienst, mit dem Sie die Verwendung von Cookies auf Ihren Webseiten konfigurieren und steuern können.
seo-description: AEM bietet einen Dienst, mit dem Sie die Verwendung von Cookies auf Ihren Webseiten konfigurieren und steuern können.
uuid: 10d95176-0a56-41f1-9d36-01dbdac757d4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 5773ec1a-f15b-462d-8f9f-54ee1d7ead44
exl-id: 42e8d804-6b6a-432e-a651-940b9f45db4e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 81%

---

# Konfigurieren der Verwendung von Cookies{#configuring-cookie-usage}

AEM bietet einen Dienst, mit dem Sie konfigurieren und steuern können, wie Cookies mit Ihren Webseiten verwendet werden:

* Ein konfigurierbarer serverseitiger Dienst verwaltet eine Liste von Cookies, die verwendet werden können.
* Eine JavaScript-API ermöglicht es Ihrem JavaScript-Code zu überprüfen, ob ein Cookie verwendet werden kann.

Verwenden Sie diese Funktion, um sicherzustellen, dass Ihre Seiten der Einverständniserklärung Ihrer Benutzer zur Verwendung von Cookies entsprechen.

## Konfigurieren zulässiger Cookies  {#configuring-allowed-cookies}

Konfigurieren Sie den Opt-out-Service von Adobe Granite, um festzulegen, wie Cookies auf Ihren Webseiten verwendet werden. In der folgenden Tabelle werden die Eigenschaften beschrieben, die Sie konfigurieren können.

Zum Konfigurieren des Dienstes können Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) verwenden oder [eine OSGi-Konfiguration zum Repository hinzufügen](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). In der folgenden Tabelle werden die Eigenschaften beschrieben, die für beide Methoden erforderlich sind. Für eine OSGi-Konfiguration lautet die PID des Dienstes `com.adobe.granite.optout`.

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname | Beschreibung |
|---|---|---|
| Opt-out-Cookies | optout.cookies | Die Namen von Cookies, die angeben, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat, sofern sie auf dem Gerät des Benutzers vorhanden sind. |
| HTTP-Header für Opt-out | optout.headers | Die Namen von HTTP-Headern, die angeben, wenn vorhanden, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat. |
| Cookies auf der White-List | optout.whitelist.cookies | Eine Liste von Cookies, die für die Funktionsweise der Website unerlässlich sind und ohne Zustimmung des Benutzers verwendet werden können. |

## Überprüfen der Verwendung von Cookies {#validating-cookie-usage}

Verwenden Sie clientseitiges JavaScript, um den Adobe Granite Opt-Out Service aufzurufen und zu überprüfen, ob Sie Cookies verwenden können. Verwenden Sie das Granite.OptOutUtil-JavaScript-Objekt, um die folgenden Aufgaben auszuführen:

* Abrufen einer Liste von Cookie-Namen, die darauf hinweisen, dass der Benutzer nicht damit einverstanden ist, Cookies zur Nachverfolgung zu verwenden
* Abrufen einer Liste von Cookies, die verwendet werden können
* Bestimmen, ob der Webbrowser ein Cookie enthält, das darauf hinweist, dass der Benutzer nicht mit der Verwendung von Cookies zur Nachverfolgung einverstanden ist
* Bestimmen, ob ein bestimmtes Cookie verwendet werden kann

Der [Client-Bibliotheksordner](/help/sites-developing/clientlibs.md#referencing-client-side-libraries) „granite.utils“ enthält das Granite.OptOutUtil-Objekt. Fügen Sie den folgenden Code zu Ihrer JSP-Datei für den Seitenkopf hinzu, um einen Link zur JavaScript-Bibliothek einzufügen:

`<ui:includeClientLib categories="granite.utils" />`

Die folgende JavaScript-Funktion bestimmt beispielsweise, ob das Cookie „COOKIE_NAME“ vor dem Schreiben in das Cookie verwendet werden darf:

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

## Das Granite.OptOutUtil-JavaScript-Objekt  {#the-granite-optoututil-javascript-object}

„Granite.OptOutUtil“ ermöglicht es Ihnen festzulegen, ob die Verwendung von Cookies zulässig ist.

### Funktion „getCookieNames()“  {#getcookienames-function}

Gibt die Namen der Cookies zurück, die, falls vorhanden, darauf hinweisen, dass der Benutzer der Verwendung von Cookies nicht zugestimmt hat.

**Parameter**

Kein.

**Rückgabe**

Eine Reihe von Cookie-Namen

#### Funktion „getWhitelistCookieNames()“  {#getwhitelistcookienames-function}

Gibt die Namen von Cookies zurück, die unabhängig von der Zustimmung des Benutzers verwendet werden können.

**Parameter**

Kein.

**Rückgabe**

Eine Reihe von Cookie-Namen

#### Funktion „isOptedOut()“  {#isoptedout-function}

Bestimmt, ob der Browser des Benutzers Cookies enthält, die darauf hinweisen, dass keine Zustimmung zur Verwendung von Cookies erteilt wurde.

**Parameter**

Kein.

**Rückgabe**

Einen booleschen Wert, der `true` lautet, wenn ein Cookie gefunden wird, das darauf hinweist, dass keine Zustimmung erteilt wurde, und `false` lautet, wenn kein Cookie darauf hinweist, dass keine Zustimmung erteilt wurde.

### Funktion „maySetCookie(cookieName)“{#maysetcookie-cookiename-function}

Bestimmt, ob ein bestimmtes Cookie im Browser des Benutzers verwendet werden kann. Diese Funktion entspricht der Verwendung der Funktion `isOptedOut`, wobei zusätzlich ermittelt wird, ob das angegebene Cookie in der Liste enthalten ist, die die Funktion `getWhitelistCookieNames` zurückgibt.

**Parameter**

* cookieName: String. Der Name des Cookies.

**Rückgabe**

Der boolesche Wert `true`, wenn `cookieName` verwendet werden kann, oder der Wert `false` , wenn `cookieName` nicht verwendet werden kann.
