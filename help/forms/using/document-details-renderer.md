---
title: Dokumentdetails für Renderer
seo-title: Document details for renderer
description: Grundlegende Informationen darüber, wie in AEM Forms Workspace die verschiedenen unterstützten Formular- und Dateitypen wiedergegeben werden.
seo-description: Conceptual information on how renders work in AEM Forms workspace to render the various supported form and file types.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
exl-id: 946f0f6d-86af-41c1-98ef-98c8f5566e95
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '653'
ht-degree: 100%

---

# Dokumentdetails für Renderer {#document-details-for-renderer}

## Einführung {#introduction}

In AEM Forms Workspace werden mehrere Formulartypen nahtlos unterstützt. Dazu gehören:

* PDF-Formulare (XDP/Acroform/Flache PDF-Dateien)
* Neue HTML-Formulare
* Bilder
* Drittanbieteranwendungen (zum Beispiel Correspondence Management)

In diesem Dokument wird die Verwendung dieser Renderer aus der Perspektive der semantischen Anpassung bzw. der Komponentenwiederverwendung erläutert, sodass Kundenanforderungen erfüllt werden, ohne eine Darstellung zu beeinträchtigen. Obwohl der Arbeitsbereich von AEM Forms beliebige Änderungen der Benutzeroberfläche oder der Bedeutung zulässt, wird empfohlen, die Rendering-Logik von verschiedenen Formulartypen nicht zu ändern. Andernfalls können die Ergebnisse unvorhersehbar sein. Dieses Dokument dient zur Anleitung und zum Verständnis für das Rendering desselben Formulars mit den gleichen Workspace-Komponenten auf verschiedenen Portalen, nicht zum Ändern der Renderlogik selbst.

## PDF-Formulare {#pdf-forms}

PDF-Formulare werden von `PdfTaskForm View` gerendert.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird vom FormsAugmenter-Service ein `FormBridge`-JavaScript™ hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offline-Schalten des Formulars.

Im Arbeitsbereich von AEM Forms kommuniziert die Ansicht „PDFTaskForm“ über einen HTML-Zwischen-Code, der unter `/lc/libs/ws/libs/ws/pdf.html` gespeichert ist, mit dem `FormBridge`-Javascript. Der Fluss verläuft wie folgt:

**PDFTaskForm-Ansicht – pdf.html**

Kommunikation über `window.postMessage`/`window.attachEvent('message')`

Diese Methode ist das Standardverfahren zur Kommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener von zuvor geöffneten PDF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Löschung wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html – `FormBridge`-Javascript innerhalb der gerenderten PDF-Datei**

Kommunikation über `pdfObject.postMessage`/`pdfObject.messageHandler`

Diese Methode ist das Standardverfahren zur Kommunikation mit einem PDF-JavaScript aus HTML. Die PdfTaskForm-Ansicht behandelt auch flaches PDF und rendert es einfach.

>[!NOTE]
>
>Es wird nicht empfohlen, die Datei pdf.html oder den Inhalt der PdfTaskForm-Ansicht zu ändern.

## Neue HTML-Formulare {#new-html-forms}

Neue HTML-Formulare werden durch die NewHTMLTaskForm-Ansicht gerendert.

Wenn ein XDP-Formular mit dem in CRX bereitgestellten Mobile-Formularpaket als HTML gerendert wird, wird dem Formular auch zusätzliches `FormBridge`-JavaScript hinzugefügt, das verschiedene Methoden für das Speichern und Senden von Formulardaten verfügbar macht.

Dieses JavaScript unterscheidet sich von dem, auf das oben unter „PDF-Formulare“ verwiesen wird, erfüllt jedoch einen ähnlichen Zweck.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt der NewHTMLTaskForm-Ansicht zu ändern.

## Flex-Formulare und Guides {#flex-forms-and-guides}

Flex-Formulare werden durch die Ansicht SwfTaskForm gerendert, Guides durch die Ansicht HtmlTaskForm.

Im Arbeitsbereich von AEM Forms kommunizieren diese Ansichten mit dem tatsächlichen SWF, aus dem das Flex-Formular bzw. der Form/Guide besteht, über einen Zwischen-SWF-Code, der in `/lc/libs/ws/libs/ws/WSNextAdapter.swf` gespeichert ist.

Die Kommunikation erfolgt mithilfe von `swfObject.postMessage`/`window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt. `WsNextAdapter.swf` wird zum Ausführen verschiedener Formularaktionen wie Speichern oder Senden verwendet.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (zum Beispiel Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Drittanbieteranwendungen werden mithilfe der ExtAppTaskForm-Ansicht gerendert.

**Kommunikation zwischen Drittanbieterprogrammen und dem Arbeitsbereich von AEM Forms**

Der Arbeitsbereich von AEM Forms ruft von `window.global.postMessage([Message],[Payload])` ab.

[Nachricht] kann eine in `runtimeMap` als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` angegebene Zeichenfolge sein. Drittanbieterprogramme müssen diese Schnittstelle verwenden, um den Arbeitsbereich von AEM Forms bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der Arbeitsbereich von AEM Forms wissen muss, wann die Aufgabe gesendet wird, damit das Aufgabefenster bereinigt werden kann.

**Kommunikation zwischen dem Arbeitsbereich von AEM Forms und Drittanbieterprogrammen**

Wenn die direkten Aktionsschaltflächen des Arbeitsbereichs von AEM Forms sichtbar sind, wird `window.[External-App-Name].getMessage([Action])` aufgerufen, wobei `[Action]` aus `routeActionMap` gelesen wird. Das Drittanbieterprogramm muss von dieser Schnittstelle abrufen und dann den Arbeitsbereich von AEM Forms über die API `postMessage ()` benachrichtigen.

Beispielsweise kann ein Flex-Programm `ExternalInterface.addCallback('getMessage', listener)` definieren, um diese Kommunikation zu unterstützen. Wenn im Drittanbieterprogramm das Senden von Formularen über eigene Schaltflächen behandelt wird, sollten Sie `hideDirectActions = true() in the runtimeMap` angeben, und Sie können diesen Listener überspringen. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen in Bezug auf Correspondence Management finden Sie unter [Integrieren von Correspondence Management in AEM Forms Workspace](/help/forms/using/integrating-correspondence-management-html-workspace.md).
