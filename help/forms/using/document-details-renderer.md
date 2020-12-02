---
title: Dokumentdetails für Renderer
seo-title: Dokumentdetails für Renderer
description: Grundlegende Informationen darüber, wie in AEM Forms Workspace die verschiedenen unterstützten Formular- und Dateitypen wiedergegeben werden.
seo-description: Grundlegende Informationen darüber, wie in AEM Forms Workspace die verschiedenen unterstützten Formular- und Dateitypen wiedergegeben werden.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 56%

---


# Dokumentdetails für Renderer {#document-details-for-renderer}

## Einführung {#introduction}

In AEM Forms Workspace werden mehrere Formulartypen nahtlos unterstützt. Dazu gehören:

* PDF-Formulare (XDP/Acroform/Flache PDF-Dateien)
* Neue HTML-Formulare
* Bilder
* Drittanbieteranwendungen (zum Beispiel Correspondence Management)

In diesem Dokument wird die Verwendung dieser Renderer aus der Perspektive der semantischen Anpassung bzw. der Komponentenwiederverwendung erläutert, sodass Kundenanforderungen erfüllt werden, ohne eine Darstellung zu beeinträchtigen. Während AEM Forms Workspace beliebige Änderungen der Benutzeroberfläche/Semantik zulässt, wird empfohlen, die Renderlogik verschiedener Formulartypen nicht zu ändern, da andernfalls die Ergebnisse unvorhersehbar sein können. Dieses Dokument dient zur Anleitung und zum Verständnis für das Rendering desselben Formulars mit den gleichen Workspace-Komponenten auf verschiedenen Portalen, nicht zum Ändern der Renderlogik selbst.

## PDF-Formulare {#pdf-forms}

PDF forms werden von `PdfTaskForm View` gerendert.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird ein `FormBridge` JavaScript™ vom FormsAugmenter-Dienst hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offlineschalten des Formulars.

In AEM Forms Workspace kommuniziert die PDFTaskForm-Ansicht mit dem `FormBridge`javascript über einen Zwischencode im HTML-Format `/lc/libs/ws/libs/ws/pdf.html`. Der Fluss verläuft wie folgt:

**PDFTaskForm-Ansicht – pdf.html**

Kommuniziert mit `window.postMessage` / `window.attachEvent('message')`

Diese Methode ist das Standardverfahren zur Kommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener von zuvor geöffneten PDF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Löschung wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html – `FormBridge`-Javascript innerhalb der gerenderten PDF-Datei**

Kommuniziert mit `pdfObject.postMessage` / `pdfObject.messageHandler`

Diese Methode ist die Standardmethode zur Kommunikation mit einem PDFJavaScript aus einem HTML-Code. Die PdfTaskForm-Ansicht behandelt auch flaches PDF und rendert es einfach.

>[!NOTE]
>
>Es wird nicht empfohlen, die Datei pdf.html oder den Inhalt der PdfTaskForm-Ansicht zu ändern.

## Neue HTML-Formulare  {#new-html-forms}

Neue HTML-Formulare werden durch die NewHTMLTaskForm-Ansicht gerendert.

Wenn ein XDP-Formular mit dem auf CRX bereitgestellten Mobile Forms-Paket als HTML wiedergegeben wird, wird dem Formular auch zusätzliches `FormBridge`JavaScript hinzugefügt, das verschiedene Methoden zum Speichern und Senden von Formulardaten bereitstellt.

Dieses JavaScript unterscheidet sich von dem oben genannten, dient jedoch einem ähnlichen Zweck.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt der NewHTMLTaskForm-Ansicht zu ändern.

## Flex-Formulare und Guides {#flex-forms-and-guides}

Flex-Formulare werden durch die Ansicht SwfTaskForm gerendert, Guides durch die Ansicht HtmlTaskForm.

In AEM Forms Workspace kommunizieren diese Ansichten mit der tatsächlichen SWF, aus der das Flex-Formular/Handbuch besteht, und verwenden eine zwischengeschaltete SWF-Datei, die unter `/lc/libs/ws/libs/ws/WSNextAdapter.swf` vorhanden ist.

Die Kommunikation erfolgt mit `swfObject.postMessage` / `window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt. `WsNextAdapter.swf` wird zum Ausführen verschiedener Formularaktionen wie Speichern oder Senden verwendet.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (zum Beispiel Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Drittanbieteranwendungen werden mithilfe der ExtAppTaskForm-Ansicht gerendert.

**Kommunikation mit Drittanbieteranwendungen im AEM Forms Workspace**

AEM Forms Workspace überwacht `window.global.postMessage([Message],[Payload])`

[Bei ] MessagePage kann es sich um eine Zeichenfolge handeln, die als  `SubmitMessage`|  `CancelMessage`|  `ErrorMessage`|  `actionEnabledMessage`im  `runtimeMap`. Anwendungen von Drittanbietern müssen diese Schnittstelle verwenden, um AEM Forms Workspace bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der AEM Forms Workspace wissen muss, dass die Aufgabe gesendet wird, damit das Fenster &quot;Aufgabe&quot;bereinigt werden kann.

**Kommunikation zwischen AEM Forms Workspace und Drittanbieteranwendungen**

Wenn die Schaltflächen für direkte Aktionen von AEM Forms Workspace sichtbar sind, wird `window.[External-App-Name].getMessage([Action])` aufgerufen, wobei `[Action]` von `routeActionMap` gelesen wird. Die Drittanbieteranwendung muss auf dieser Schnittstelle lauschen und dann AEM Forms Workspace über die API `postMessage ()` benachrichtigen.

Beispielsweise kann eine Flex-Anwendung `ExternalInterface.addCallback('getMessage', listener)` definieren, um diese Kommunikation zu unterstützen. Wenn die Drittanbieteranwendung die Formularübermittlung über eigene Schaltflächen verarbeiten möchte, sollten Sie `hideDirectActions = true() in the runtimeMap` angeben und diesen Listener überspringen. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen in Bezug auf Correspondence Management finden Sie unter [Integrieren von Correspondence Management in AEM Forms Workspace](/help/forms/using/integrating-correspondence-management-html-workspace.md).
