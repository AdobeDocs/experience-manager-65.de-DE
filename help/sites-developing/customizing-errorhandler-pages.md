---
title: Anpassen der vom Fehler-Handler angezeigten Seiten
description: Adobe Experience Manager verfügt über einen Standard-Fehler-Handler zur Verarbeitung von HTTP-Fehlern.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: d6745baa-44da-45dd-b5d5-a9b218e7e8cf
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 39%

---

# Anpassen der vom Fehler-Handler angezeigten Seiten{#customizing-pages-shown-by-the-error-handler}

Adobe Experience Manager (AEM) verfügt über einen standardmäßigen Fehler-Handler für die Verarbeitung von HTTP-Fehlern, z. B. durch Anzeige von:

![chlimage_1-67](assets/chlimage_1-67a.png)

Das System stellt Skripte (unter `/libs/sling/servlet/errorhandler`) bereit, um auf Fehler-Codes zu reagieren. Standardmäßig sind folgende Skripte mit einer Standard-CQ-Instanz verfügbar:

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM basiert auf Apache Sling. Siehe [Umgang mit Fehlern](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html) für detaillierte Informationen zur Sling-Fehlerbehandlung.

>[!NOTE]
>
>Auf einer Autoreninstanz muss die [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) ist standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler antwortet, indem er den vollständigen Stacktrace in die Antwort schreibt.
>
>Auf einer Veröffentlichungsinstanz lautet der CQ WCM Debug Filter *always* deaktiviert (auch wenn als aktiviert konfiguriert).

## Anpassen der vom Fehler-Handler angezeigten Seiten {#how-to-customize-pages-shown-by-the-error-handler}

Sie können Ihre eigenen Skripte erstellen, um die Seiten anzupassen, die der Fehler-Handler anzeigt, wenn ein Fehler auftritt. Ihre angepassten Seiten werden unter `/apps` und überlagern die Standardseiten (die unter `/libs`).

>[!NOTE]
>
>Siehe [Verwenden von Überlagerungen](/help/sites-developing/overlays.md) für weitere Details.

1. Kopieren Sie im Repository die Standardskripte:

   * von `/libs/sling/servlet/errorhandler/`
   * nach `/apps/sling/servlet/errorhandler/`

   Da der Zielpfad nicht standardmäßig vorhanden ist, müssen Sie ihn erstellen, wenn Sie dies zum ersten Mal durchführen.

1. Navigieren Sie zu `/apps/sling/servlet/errorhandler` und führen Sie einen der folgenden Schritte aus:

   * Bearbeiten Sie das entsprechende vorhandene Skript, damit Sie die erforderlichen Informationen bereitstellen können.
   * ein neues Skript für den erforderlichen Code erstellen und bearbeiten.

1. Speichern Sie die Änderungen und testen Sie sie.

>[!CAUTION]
>
>Die Handler &quot;404.jsp&quot;und &quot;403.jsp&quot;wurden für die CQ5-Authentifizierung entwickelt, um insbesondere eine Systemanmeldung zu ermöglichen, wenn diese Fehler auftreten.
>
>Daher sollten diese beiden Handler mit großer Sorgfalt ersetzt werden.

### Anpassung der Reaktion auf HTTP 500-Fehler {#customizing-the-response-to-http-errors}

HTTP 500-Fehler werden durch serverseitige Ausnahmen verursacht.

* **[500 Interner Serverfehler](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)** Der Server hat einen unerwarteten Zustand entdeckt und kann daher die Anfrage nicht erfüllen.

Wenn die Bearbeitung einer Anfrage zu einem Ausnahmefehler führt, führt das Apache Sling-Framework (auf dem AEM basiert) folgende Schritte durch:

* protokolliert die Ausnahme
* gibt zurück:

   * der HTTP-Antwort-Code 500
   * Ausnahmestapelverfolgung

  im Hauptteil der Antwort.

Indem Sie [die Seiten anpassen, die der Fehler-Handler zeigt](#how-to-customize-pages-shown-by-the-error-handler), können Sie ein `500.jsp`-Skript erstellen. Sie wird jedoch nur verwendet, wenn `HttpServletResponse.sendError(500)` explizit ausgeführt wird, d. h. von einem Ausnahmefänger.

Andernfalls wird der Antwort-Code auf „500“ gesetzt, aber das `500.jsp`-Skript wird nicht ausgeführt.

Um 500-Fehler zu verarbeiten, muss der Dateiname des Fehler-Handler-Skripts identisch mit der Ausnahmeklasse (oder der übergeordneten Klasse) sein. Um alle diese Ausnahmen zu handhaben, können Sie ein Skript erstellen `/apps/sling/servlet/errorhandler/Throwable.js`p oder `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!CAUTION]
>
>Auf einer Autoreninstanz muss die [CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) ist standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler antwortet, indem er den vollständigen Stacktrace in die Antwort schreibt.
>
>Für einen benutzerdefinierten Fehler-Handler sind Antworten mit Code 500 erforderlich, sodass die Variable [CQ WCM Debug Filter muss deaktiviert sein](/help/sites-deploying/osgi-configuration-settings.md). Dadurch wird sichergestellt, dass der Antwort-Code 500 zurückgegeben wird, was wiederum den richtigen Sling-Fehler-Handler auslöst.
>
>Auf einer Veröffentlichungsinstanz lautet der CQ WCM Debug Filter *always* deaktiviert (auch wenn als aktiviert konfiguriert).
