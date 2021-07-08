---
title: Benutzerdefinierte HTTP-Header
description: Benutzerdefinierte HTTP-Header konfigurieren
source-git-commit: 7d174be35cb99d802e4aeff6f4d955b1b92cab74
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 1%

---


# Benutzerdefinierte HTTP-Header {#custom-http-headers}

## Übersicht {#overview}

Um mehr Kontrolle über ihr Backend zu erhalten, können Autoren benutzerdefinierte HTTP-Header konfigurieren, die an die Commerce-Engine gesendet werden, zusammen mit den bereits von CIF gesendeten Headern. Häufige Anwendungsfälle sind Multi-Store-Setups, in denen Sie HTTP-Header verwenden können, um die Antwort des Commerce-Backend zu steuern.

>[!NOTE]
>
>Entwickler können benutzerdefinierte HTTP-Header immer mithilfe der GraphQL-Client-Konfiguration konfigurieren.


## Konfiguration {#configuration}

Um die benutzerdefinierten HTTP-Header zu konfigurieren, müssen sie zuerst definiert werden. Die benutzerdefinierten HTTP-Header müssen zuerst definiert werden, indem sie mithilfe einer OSGi-Konfiguration zur Dienstkonfiguration `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` hinzugefügt werden.

Sie können die Werte der HTTP-Header auf der Seite &quot;Cloud Service Configuration&quot;für Ihr Projekt konfigurieren:

1. Navigieren Sie zur Konfigurationsseite des Cloud Service unter Tools > Cloud Services > CIF-Konfiguration .
1. Öffnen Sie eine vorhandene Konfiguration oder erstellen Sie eine neue.
1. Gehen Sie zur Registerkarte &quot;Erweitert&quot;und suchen Sie das Multifeld &quot;Benutzerdefinierte HTTP-Header&quot;. Sie können die zuvor definierten Header auswählen und ihnen Werte zuweisen.

Die Komponenten, die die obige Cloud Service-Konfiguration verwenden, senden diese HTTP-Header mit jeder GraphQL-Anfrage.

## Einschränkungen {#restrictions}

Der Dienst ermöglicht zwar die Definition von Kopfzeilennamen, einschließlich der standardmäßigen, aber sie stehen nicht zur Konfiguration zur Verfügung. Mit anderen Worten, Sie können die standardmäßigen HTTP-Header nicht mit dieser Funktion überschreiben. Eine Liste mit eingeschränkten Kopfzeilennamen finden Sie [hier](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers). Darüber hinaus gibt es zwei weitere Header, die nicht verwendet werden können:

* &quot;Store&quot;- wird von CIF verwendet, um den Magento Store zu identifizieren.
* &quot;Vorschau-Version&quot;- wird von CIF zum Abrufen von Staging-Produkten verwendet
