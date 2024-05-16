---
title: Dokumentdetails für den Renderer
description: Grundlegende Informationen darüber, wie Renderer in AEM Forms Workspace die verschiedenen unterstützten Formular- und Dateitypen wiedergeben.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 946f0f6d-86af-41c1-98ef-98c8f5566e95
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '666'
ht-degree: 100%

---

# Dokumentdetails für den Renderer {#document-details-for-renderer}

## Einführung {#introduction}

In AEM Forms Workspace werden mehrere Formulartypen nahtlos unterstützt. Dazu gehören:

* PDF-Formulare (XDP/Acroform/reduzierte PDF-Dateien)
* Neue HTML-Formulare
* Bilder
* Drittanbieteranwendungen (zum Beispiel Correspondence Management)

In diesem Dokument wird die Verwendung dieser Renderer aus der Perspektive der semantischen Anpassung bzw. der Komponentenwiederverwendung erläutert, sodass Kundenanforderungen erfüllt werden können, ohne eine Ausgabedarstellung zu beeinträchtigen. Obwohl der Arbeitsbereich von AEM Forms beliebige Änderungen der Benutzeroberfläche oder der Bedeutung zulässt, wird empfohlen, die Rendering-Logik von verschiedenen Formulartypen nicht zu ändern. Andernfalls können die Ergebnisse unvorhersehbar sein. Dieses Dokument dient zur Anleitung und zum Verständnis für das Rendering desselben Formulars mit den gleichen Workspace-Komponenten auf verschiedenen Portalen, nicht zum Ändern der Renderlogik selbst.

## PDF-Formulare {#pdf-forms}

PDF-Formulare werden von `PdfTaskForm View` gerendert.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird vom FormsAugmenter-Service ein `FormBridge`-JavaScript™ hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offline-Schalten des Formulars.

In AEM Forms Workspace kommuniziert die Ansicht „PDFTaskForm“ über einen HTML-Zwischen-Code, der unter `/lc/libs/ws/libs/ws/pdf.html` gespeichert ist, mit dem `FormBridge`-JavaScript. Der Fluss verläuft wie folgt:

**PDFTaskForm-Ansicht – pdf.html**

Kommunikation über `window.postMessage`/`window.attachEvent('message')`

Diese Methode ist das Standardverfahren zur Kommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener von zuvor geöffneten PDF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html – `FormBridge`-JavaScript innerhalb der gerenderten PDF-Datei**

Kommunikation über `pdfObject.postMessage`/`pdfObject.messageHandler`

Diese Methode ist das Standardverfahren zur Kommunikation mit einem PDF-JavaScript aus HTML. Die PdfTaskForm-Ansicht behandelt auch eine reduzierte PDF-Datei und rendert sie als einfache Datei.

>[!NOTE]
>
>Es wird davon abgeraten, die Datei pdf.html oder den Inhalt der PdfTaskForm-Ansicht zu bearbeiten.

## Neue HTML-Formulare {#new-html-forms}

Neue HTML-Formulare werden durch die NewHTMLTaskForm-Ansicht gerendert.

Wenn ein XDP-Formular mit dem in CRX bereitgestellten Mobile-Formularpaket als HTML gerendert wird, wird dem Formular auch zusätzliches `FormBridge`-JavaScript hinzugefügt, das verschiedene Methoden für das Speichern und Senden von Formulardaten verfügbar macht.

Dieses JavaScript unterscheidet sich von dem, auf das oben unter „PDF-Formulare“ verwiesen wird, erfüllt jedoch einen ähnlichen Zweck.

>[!NOTE]
>
>Adobe rät von der Bearbeitung des Inhalts der NewHTMLTaskForm-Ansicht ab.

## Flex-Formulare und Guides {#flex-forms-and-guides}

Flex-Formulare werden durch die Ansicht SwfTaskForm gerendert, Guides durch die Ansicht HtmlTaskForm.

In AEM Forms Workspace kommunizieren diese Ansichten mit dem tatsächlichen SWF, aus dem das Flex®-Formular bzw. der Guide besteht, über einen Zwischen-SWF-Code, der in `/lc/libs/ws/libs/ws/WSNextAdapter.swf` gespeichert ist.

Die Kommunikation erfolgt mithilfe von `swfObject.postMessage`/`window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt. `WsNextAdapter.swf` wird zum Ausführen verschiedener Formularaktionen wie Speichern oder Senden verwendet.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (zum Beispiel Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Drittanbieteranwendungen werden mithilfe der ExtAppTaskForm-Ansicht gerendert.

**Kommunikation zwischen Drittanbieterprogrammen und dem Arbeitsbereich von AEM Forms**

Der Arbeitsbereich von AEM Forms ruft von `window.global.postMessage([Message],[Payload])` ab.

[Nachricht] kann eine in `runtimeMap` als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` angegebene Zeichenfolge sein. Drittanbieterprogramme müssen diese Schnittstelle verwenden, um AEM Forms Workspace bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der Arbeitsbereich von AEM Forms wissen muss, wann die Aufgabe gesendet wird, damit das Aufgabefenster bereinigt werden kann.

**Kommunikation zwischen dem Arbeitsbereich von AEM Forms und Drittanbieterprogrammen**

Wenn die direkten Aktionsschaltflächen des Arbeitsbereichs von AEM Forms sichtbar sind, wird `window.[External-App-Name].getMessage([Action])` aufgerufen, wobei `[Action]` aus `routeActionMap` gelesen wird. Das Drittanbieterprogramm muss von dieser Schnittstelle abrufen und dann den Arbeitsbereich von AEM Forms über die API `postMessage ()` benachrichtigen.

Beispielsweise kann ein Flex-Programm `ExternalInterface.addCallback('getMessage', listener)` definieren, um diese Kommunikation zu unterstützen. Wenn im Drittanbieterprogramm das Senden von Formularen über eigene Schaltflächen behandelt wird, sollten Sie `hideDirectActions = true() in the runtimeMap` angeben, und Sie können diesen Listener überspringen. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen in Correspondence Management finden Sie unter [Integrieren von Correspondence Management im AEM Forms Workspace](/help/forms/using/integrating-correspondence-management-html-workspace.md).
