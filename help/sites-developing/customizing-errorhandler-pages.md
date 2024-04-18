---
title: Anpassen der vom Fehler-Handler angezeigten Seiten
description: Adobe Experience Manager verfügt über einen Standard-Fehler-Handler zur Verarbeitung von HTTP-Fehlern.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: d6745baa-44da-45dd-b5d5-a9b218e7e8cf
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 100%

---

# Anpassen der vom Fehler-Handler angezeigten Seiten{#customizing-pages-shown-by-the-error-handler}

Adobe Experience Manager (AEM) enthält einen Standard-Fehler-Handler für die Verarbeitung von HTTP-Fehlern. Beispielsweise wird Folgendes gezeigt:

![chlimage_1-67](assets/chlimage_1-67a.png)

Das System stellt Skripte (unter `/libs/sling/servlet/errorhandler`) bereit, um auf Fehler-Codes zu reagieren. Standardmäßig sind folgende Skripte mit einer Standard-CQ-Instanz verfügbar:

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM basiert auf Apache Sling. Siehe [Umgang mit Fehlern](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html) mit detaillierten Informationen zur Sling-Fehlerbehandlung.

>[!NOTE]
>
>In einer Autoreninstanz ist [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler schreibt daraufhin den vollständigen Stacktrace in die Antwort.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter *immer* deaktiviert (selbst wenn er als aktiviert konfiguriert ist).

## Anpassen der vom Fehler-Handler angezeigten Seiten {#how-to-customize-pages-shown-by-the-error-handler}

Sie können Ihre eigenen Skripte erstellen, um die Seiten anzupassen, die der Fehler-Handler anzeigt, wenn ein Fehler auftritt. Die angepassten Seiten werden unter `/apps` erstellt und überlagern die Standardseiten (die unter `/libs` zu finden sind).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verwenden von Überlagerungen](/help/sites-developing/overlays.md).

1. Kopieren Sie im Repository die Standardskripte:

   * von `/libs/sling/servlet/errorhandler/`
   * nach `/apps/sling/servlet/errorhandler/`

   Da der Zielpfad standardmäßig nicht vorhanden ist, müssen Sie ihn erstellen, wenn Sie diesen Vorgang zum ersten Mal durchführen.

1. Navigieren Sie zu `/apps/sling/servlet/errorhandler` und führen Sie einen der folgenden Schritte aus:

   * das entsprechende vorhandene Skript bearbeiten, um die benötigten Informationen anzugeben.
   * ein neues Skript für den erforderlichen Code erstellen und bearbeiten.

1. Speichern Sie die Änderungen und testen Sie sie.

>[!CAUTION]
>
>Die Handler 404.jsp und 403.jsp sind speziell für die CQ5-Authentifizierung entwickelt. Insbesondere ermöglichen sie eine Systemanmeldung, wenn diese Fehler auftreten.
>
>Daher sollten Sie diese beiden Handler nur mit größter Vorsicht ersetzen.

### Anpassung der Reaktion auf HTTP 500-Fehler {#customizing-the-response-to-http-errors}

HTTP 500-Fehler werden von Server-seitigen Ausnahmefehlern verursacht.

* **[500 Interner Serverfehler](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)** Der Server hat einen unerwarteten Zustand entdeckt und kann daher die Anfrage nicht erfüllen.

Wenn die Bearbeitung einer Anfrage zu einem Ausnahmefehler führt, führt das Apache Sling-Framework (auf dem AEM basiert) folgende Schritte durch:

* Protokollierung des Ausnahmefehlers
* Rückgabe:

   * der HTTP-Antwort-Code 500
   * der Stacktrace des Ausnahmefehlers

  im Hauptteil der Antwort.

Indem Sie [die Seiten anpassen, die der Fehler-Handler zeigt](#how-to-customize-pages-shown-by-the-error-handler), können Sie ein `500.jsp`-Skript erstellen. Es wird jedoch nur verwendet, wenn `HttpServletResponse.sendError(500)` explizit ausgeführt wird, d. h. von einem Abfangalgorithmus für Ausnahmen.

Andernfalls wird der Antwort-Code auf „500“ gesetzt, aber das `500.jsp`-Skript wird nicht ausgeführt.

Um 500-Fehler zu verarbeiten, muss der Dateiname des Fehler-Handler-Skripts identisch mit der Ausnahmeklasse (oder der übergeordneten Klasse) sein. Um alle derartigen Ausnahmen zu bearbeiten, können Sie ein `/apps/sling/servlet/errorhandler/Throwable.js`- oder `/apps/sling/servlet/errorhandler/Exception.jsp`-Skript erstellen.

>[!CAUTION]
>
>In einer Autoreninstanz ist [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler schreibt daraufhin den vollständigen Stacktrace in die Antwort.
>
>Für eine individuelle Fehlerverarbeitung sind Antworten mit Code 500 erforderlich. Der [CQ WCM Debug-Filter muss also deaktiviert sein](/help/sites-deploying/osgi-configuration-settings.md). Dadurch wird sichergestellt, dass der Antwort-Code 500 zurückgegeben wird, was wiederum den richtigen Sling-Fehler-Handler auslöst.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter *immer* deaktiviert (selbst wenn er als aktiviert konfiguriert ist).
