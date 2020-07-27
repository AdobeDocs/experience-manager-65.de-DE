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
source-git-commit: c74d9e86727f2deda62b8d1eb105b28ef4b6d184
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

PDF forms werden von `PdfTaskForm View`.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird ein `FormBridge` JavaScript™ vom FormsAugmenter-Dienst hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offlineschalten des Formulars.

In AEM Forms workspace, PDFTaskForm view communicates with the `FormBridge`javascript, via an intermediary HTML present at `/lc/libs/ws/libs/ws/pdf.html`. Der Fluss verläuft wie folgt:

**PDFTaskForm-Ansicht – pdf.html**

Kommunikation mit `window.postMessage` / `window.attachEvent('message')`

Diese Methode ist das Standardverfahren zur Kommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener von zuvor geöffneten PDF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Löschung wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html –`FormBridge`-Javascript innerhalb der gerenderten PDF-Datei**

Kommunikation mit `pdfObject.postMessage` / `pdfObject.messageHandler`

Diese Methode ist die Standardmethode zur Kommunikation mit einem PDFJavaScript aus einem HTML-Code. Die PdfTaskForm-Ansicht behandelt auch flaches PDF und rendert es einfach.

>[!NOTE]
>
>Es wird nicht empfohlen, die Datei pdf.html oder den Inhalt der PdfTaskForm-Ansicht zu ändern.

## Neue HTML-Formulare {#new-html-forms}

Neue HTML-Formulare werden durch die NewHTMLTaskForm-Ansicht gerendert.

When an XDP Form is rendered as HTML using the mobile forms package deployed on CRX, it also adds additional `FormBridge`JavaScript to the form, which exposes different methods for saving and submitting form data.

Dieses JavaScript unterscheidet sich von dem oben genannten, dient jedoch einem ähnlichen Zweck.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt der NewHTMLTaskForm-Ansicht zu ändern.

## Flex-Formulare und Guides {#flex-forms-and-guides}

Flex-Formulare werden durch die Ansicht SwfTaskForm gerendert, Guides durch die Ansicht HtmlTaskForm.

In AEM Forms workspace, these views communicate with the actual SWF which makes up the flex form/guide using an intermediary SWF present at `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

The communication happens using `swfObject.postMessage` / `window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt. `WsNextAdapter.swf` wird zum Ausführen verschiedener Formularaktionen wie Speichern oder Senden verwendet.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (zum Beispiel Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Drittanbieteranwendungen werden mithilfe der ExtAppTaskForm-Ansicht gerendert.

**Kommunikation zwischen Drittanbieteranwendungen und AEM Forms Workspace**

AEM Forms workspace listens on `window.global.postMessage([Message],[Payload])`

[Die Meldung] kann eine Zeichenfolge sein, die als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage`im `runtimeMap`. Drittanbieteranwendungen müssen diese Schnittstelle verwenden, um AEM Forms Workspace bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der Arbeitsbereich AEM Forms wissen muss, dass die Aufgabe gesendet wird, damit das Fenster Aufgabe bereinigt werden kann.

**Kommunikation zwischen AEM Forms und Drittanbieteranwendungen**

Wenn die Schaltflächen für die direkte Aktion von AEM Forms Workspace sichtbar sind, wird `window.[External-App-Name].getMessage([Action])`aufgerufen, wobei [ `Action]` vom `routeActionMap`. The third-party application must listen on this interface, and then notify AEM Forms workspace via the `postMessage ()` API.

For example, a Flex application can define `ExternalInterface.addCallback('getMessage', listener)` to support this communication. If the third-party application wants to handle form submission via its own buttons, then you should specify `hideDirectActions = true() in the runtimeMap` and you may skip this listener. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen in Bezug auf Correspondence Management finden Sie unter [Integrieren von Correspondence Management in AEM Forms Workspace](/help/forms/using/integrating-correspondence-management-html-workspace.md).
