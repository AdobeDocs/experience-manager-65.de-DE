---
title: Anwenderdefinierte HTTP-Kopfzeilen
description: Erfahren Sie, wie Sie benutzerdefinierte HTTP-Kopfzeilen in Adobe Experience Manager Commerce konfigurieren.
exl-id: 834aadac-c3be-4e7a-a3cb-349608810b40
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# Anwenderdefinierte HTTP-Kopfzeilen {#custom-http-headers}

## Überblick {#overview}

Um mehr Kontrolle über ihr Backend zu erhalten, können Autoren anwenderdefinierte HTTP-Kopfzeilen konfigurieren, die zusammen mit den bereits von CIF gesendeten Kopfzeilen an die Commerce-Engine gesendet werden. Häufige Anwendungsfälle sind Multi-Store-Setups, in denen Sie HTTP-Kopfzeilen verwenden können, um die Antwort des Commerce-Backends zu steuern.

>[!NOTE]
>
>Entwickler können anwenderdefinierte HTTP-Kopfzeilen jederzeit mithilfe der GraphQL-Client-Konfiguration konfigurieren.
>

## Konfiguration {#configuration}

Um die benutzerdefinierten HTTP-Kopfzeilen zu konfigurieren, müssen Sie sie zuerst definieren. Die anwenderdefinierten HTTP-Kopfzeilen müssen zuerst definiert werden, indem sie mithilfe einer OSGi-Konfiguration zur Service-Konfiguration `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` hinzugefügt werden.

Sie können die Werte der HTTP-Kopfzeilen auf der Seite „Cloud Service-Konfiguration“ für Ihr Projekt konfigurieren:

1. Navigieren Sie unter „Tools“ > „Cloud-Services“ > „CIF-Konfiguration“ zur Seite „Cloud-Service-Konfiguration“.
1. Öffnen Sie eine vorhandene Konfiguration oder erstellen Sie eine neue.
1. Wechseln Sie zur Registerkarte „Erweitert“ und suchen Sie das Multi-Feld „Anwenderdefinierte HTTP-Kopfzeilen“. Sie können die zuvor definierten Kopfzeilen auswählen und ihnen Werte zuweisen.

Die Komponenten, die die obige Cloud-Service-Konfiguration verwenden, senden diese HTTP-Kopfzeilen mit jeder GraphQL-Anfrage.

## Einschränkungen {#restrictions}

Der Service ermöglicht zwar die Definition von Kopfzeilennamen, einschließlich der standardmäßigen Namen, aber sie stehen nicht zur Konfiguration zur Verfügung. Mit anderen Worten: Sie können mit dieser Funktion nicht die standardmäßigen HTTP-Kopfzeilen überschreiben. Eine Liste mit eingeschränkten Kopfzeilennamen finden Sie auf der MDN Web Docs-Website unter [HTTP-Header](https://developer.mozilla.org/de-DE/docs/Web/HTTP/Headers). Darüber hinaus gibt es zwei weitere Kopfzeilen, die nicht verwendet werden können:

* „Store“ – wird von CIF verwendet, um den Adobe Commerce-Store zu identifizieren.
* „Preview-Version“ – wird von CIF zum Abrufen von Staging-Produkten verwendet.
