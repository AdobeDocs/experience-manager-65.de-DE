---
title: Anpassen der vom Fehler-Handler angezeigten Seiten
seo-title: Anpassen der vom Fehler-Handler angezeigten Seiten
description: AEM enthält einen Standard-Fehler-Handler für die Verarbeitung von HTTP-Fehlern.
seo-description: AEM enthält einen Standard-Fehler-Handler für die Verarbeitung von HTTP-Fehlern.
uuid: aaf940fd-e428-4c7c-af7f-88b1d02c17c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 63c94c82-ed96-4d10-b645-227fa3c09f4b
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 76%

---


# Anpassen der vom Fehler-Handler angezeigten Seiten{#customizing-pages-shown-by-the-error-handler}

AEM enthält einen Standard-Fehlerhandler für die Verarbeitung von HTTP-Fehlern. Beispiel:

![chlimage_1-67](assets/chlimage_1-67a.png)

Systembereitgestellte Skripten existieren (unter `/libs/sling/servlet/errorhandler`), um auf Fehlercodes zu reagieren. Standardmäßig sind bei einer Standard-CQ-Instanz folgende Skripten verfügbar:

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM basiert auf Apache Sling, daher finden Sie unter [https://sling.apache.org/site/errorhandling.html](https://sling.apache.org/site/errorhandling.html) detaillierte Informationen zum Sling Error Handling.

>[!NOTE]
>
>In Autoreninstanzen ist [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwortcode 200. Der standardmäßige Fehler-Handler schreibt als Reaktion die vollständige Stacktrace in die Antwort.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter *immer* deaktiviert (selbst wenn er als aktiviert konfiguriert ist).

## Anpassung der vom Fehler-Handler angezeigten Seiten {#how-to-customize-pages-shown-by-the-error-handler}

Sie können Ihre eigenen Skripte erstellen, um die Seiten anzupassen, die der Fehler-Handler anzeigt, wenn ein Fehler auftritt. Ihre benutzerdefinierten Seiten werden unter `/apps` erstellt und überlagern die Standardseiten (die unter `/libs` stehen).

>[!NOTE]
>
>Unter [Verwendung von Überlagerungen](/help/sites-developing/overlays.md) finden Sie weitere Informationen.

1. Kopieren Sie im Repository das/die Standardskript(e):

   * von `/libs/sling/servlet/errorhandler/`
   * in `/apps/sling/servlet/errorhandler/`

   Da der Zielpfad standardmäßig nicht vorhanden ist, müssen Sie ihn erstellen, wenn Sie diesen Vorgang zum ersten Mal durchführen.

1. Navigieren Sie zu `/apps/sling/servlet/errorhandler`. Hier können Sie entweder:

   * das entsprechende vorhandene Skript bearbeiten, um die benötigten Informationen anzugeben.
   * ein neues Skript für den erforderlichen Code erstellen und bearbeiten.

1. Speichern Sie die Änderungen und testen Sie sie.

>[!CAUTION]
>
>Die Handler 404.jsp und 403.jsp sind speziell für die CQ5-Authentifizierung entwickelt. Insbesondere ermöglichen sie eine Systemanmeldung, wenn diese Fehler auftreten.
>
>Daher sollten Sie diese Handler nur mit größter Vorsicht ersetzen.

### Anpassung der Reaktion auf HTTP 500-Fehler  {#customizing-the-response-to-http-errors}

HTTP 500-Fehler werden von serverseitigen Ausnahmefehlern verursacht.

* **[500 Interner Serverfehler](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)** Der Server hat einen unerwarteten Zustand entdeckt und kann daher die Anfrage nicht erfüllen.

Wenn die Verarbeitung von Anforderungen eine Ausnahme ergibt, wird das Apache Sling-Framework (das auf AEM basiert) wie folgt ausgeführt:

* Protokollierung des Ausnahmefehlers
* Folgendes wird zurückgegeben:

   * der HTTP-Antwortcode 500
   * Der Stacktrace des Ausnahmefehlers

   im Haupttext der Antwort.

Indem Sie [die Seiten anpassen, die der Fehler-Handler zeigt](#how-to-customize-pages-shown-by-the-error-handler), können Sie ein `500.jsp`-Skript erstellen. Sie wird jedoch nur verwendet, wenn `HttpServletResponse.sendError(500)` explizit ausgeführt wird. d. h. von einem Ausnahmenfänger.

Andernfalls wird der Antwortcode auf gesetzt, aber das Skript `500.jsp`500.  wird nicht ausgeführt.

Um 500-Fehler zu verarbeiten, muss der Dateiname des Fehler-Handler-Skripts identisch mit der Ausnahmeklasse (oder der übergeordneten Klasse) sein. Um alle derartigen Ausnahmen zu bearbeiten, können Sie ein Skript `/apps/sling/servlet/errorhandler/Throwable.js`p oder `/apps/sling/servlet/errorhandler/Exception.jsp` erstellen.

>[!CAUTION]
>
>In Autoreninstanzen ist [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwortcode 200. Der standardmäßige Fehler-Handler schreibt als Reaktion die vollständige Stacktrace in die Antwort.
>
>Für eine individuelle Fehlerverarbeitung sind Antworten mit Code 500 erforderlich. Der [CQ WCM Debug-Filter muss also deaktiviert sein](/help/sites-deploying/osgi-configuration-settings.md). Dadurch wird sichergestellt, dass der Antwortcode 500 zurückgegeben wird, was wiederum den richtigen Sling-Fehler-Handler auslöst.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter *immer* deaktiviert (selbst wenn er als aktiviert konfiguriert ist).

