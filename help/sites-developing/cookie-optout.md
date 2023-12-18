---
title: Konfigurieren der Verwendung von Cookies
description: AEM bietet einen Dienst, mit dem Sie die Verwendung von Cookies auf Ihren Web-Seiten konfigurieren und steuern können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 42e8d804-6b6a-432e-a651-940b9f45db4e
source-git-commit: 4e2ee7da5424ac6677eaa2392de7803e7543d13c
workflow-type: ht
source-wordcount: '550'
ht-degree: 100%

---

# Konfigurieren der Verwendung von Cookies{#configuring-cookie-usage}

AEM bietet einen Dienst, mit dem Sie die Verwendung von Cookies auf Ihren Web-Seiten konfigurieren und steuern können:

* Ein konfigurierbarer Server-seitiger Dienst verwaltet eine Liste von Cookies, die verwendet werden können.
* Eine JavaScript-API ermöglicht es Ihrem JavaScript-Code, zu überprüfen, ob ein Cookie verwendet werden kann.

Verwenden Sie diese Funktion, um sicherzustellen, dass Ihre Seiten der Einverständniserklärung Ihrer Benutzenden zur Verwendung von Cookies entsprechen.

## Konfigurieren zulässiger Cookies {#configuring-allowed-cookies}

Konfigurieren Sie den Opt-out-Service von Adobe Granite, um festzulegen, wie Cookies auf Ihren Web-Seiten verwendet werden. In der folgenden Tabelle werden die Eigenschaften beschrieben, die Sie konfigurieren können.

Zum Konfigurieren des Dienstes können Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) verwenden oder [eine OSGi-Konfiguration zum Repository hinzufügen](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). In der folgenden Tabelle werden die Eigenschaften beschrieben, die für beide Methoden erforderlich sind. Für eine OSGi-Konfiguration lautet die PID des Dienstes `com.adobe.granite.optout`.

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname | Beschreibung |
|---|---|---|
| Opt-out-Cookies | optout.cookies | Die Namen von Cookies, die, wenn sie auf den Geräten von Benutzenden vorhanden sind, anzeigen, dass die Benutzenden der Verwendung von Cookies nicht zugestimmt haben. |
| HTTP-Header für Opt-out | optout.headers | Die Namen der HTTP-Header, die, wenn vorhanden, anzeigen, dass die bzw. der Benutzende der Verwendung von Cookies nicht zugestimmt hat. |
| Cookies auf der Zulassungsliste | optout.whitelist.cookies | Eine Liste von Cookies, die für die Funktionalität der Website unerlässlich sind und ohne Zustimmung des Benutzers verwendet werden können. |

## Überprüfen der Verwendung von Cookies {#validating-cookie-usage}

Verwenden Sie Client-seitiges JavaScript, um den Adobe Granite Opt-Out-Service aufzurufen und zu überprüfen, ob Sie Cookies verwenden können. Verwenden Sie das Granite.OptOutUtil-JavaScript-Objekt, um die folgenden Aufgaben auszuführen:

* Abrufen einer Liste von Cookie-Namen, die darauf hinweisen, dass Benutzende nicht damit einverstanden sind, Cookies zur Nachverfolgung zu verwenden
* Abrufen einer Liste von Cookies, die verwendet werden können
* Erkennen, ob der Webbrowser ein Cookie enthält, das darauf hinweist, dass Benutzende nicht mit der Verwendung von Cookies zur Nachverfolgung einverstanden sind
* Erkennen, ob ein bestimmtes Cookie verwendet werden kann

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

## Das Granite.OptOutUtil-JavaScript-Objekt {#the-granite-optoututil-javascript-object}

„Granite.OptOutUtil“ ermöglicht es Ihnen, festzulegen, ob die Verwendung von Cookies zulässig ist.

### Funktion „getCookieNames()“ {#getcookienames-function}

Die Namen der Cookies, die, falls vorhanden, darauf hinweisen, dass Benutzende der Verwendung von Cookies nicht zugestimmt haben.

**Parameter**

Ohne.

**Rückgabe**

Ein Array von Cookie-Namen.

#### Funktion „getWhitelistCookieNames()“ {#getwhitelistcookienames-function}

Die Namen der Cookies, die unabhängig von der Zustimmung durch Benutzende verwendet werden können.

**Parameter**

Ohne.

**Rückgabe**

Ein Array von Cookie-Namen.

#### Funktion „isOptedOut()“ {#isoptedout-function}

Lässt erkennen, ob der Browser der bzw. des Benutzenden Cookies enthält, die darauf hinweisen, dass keine Zustimmung zur Verwendung von Cookies erteilt wurde.

**Parameter**

Ohne.

**Rückgabe**

Einen booleschen Wert, der `true` lautet, wenn ein Cookie gefunden wird, das darauf hinweist, dass keine Zustimmung erteilt wurde, und `false` lautet, wenn kein Cookie darauf hinweist, dass keine Zustimmung erteilt wurde.

### Funktion „maySetCookie(cookieName)“ {#maysetcookie-cookiename-function}

Lässt erkennen, ob ein bestimmtes Cookie im Browser von Benutzenden verwendet werden kann. Diese Funktion entspricht der Verwendung der Funktion `isOptedOut`, wobei ermittelt wird, ob das angegebene Cookie in der Liste enthalten ist, die die Funktion `getWhitelistCookieNames` zurückgibt.

**Parameter**

* cookieName: String. Der Name des Cookies.

**Rückgabe**

Einen booleschen Wert, der `true` lautet, wenn `cookieName` verwendet werden kann, oder `false` lautet, wenn `cookieName` nicht verwendet werden kann.
