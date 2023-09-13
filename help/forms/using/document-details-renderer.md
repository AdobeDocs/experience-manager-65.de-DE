---
title: Dokumentdetails für den Renderer
description: Grundlegende Informationen dazu, wie die Wiedergabe in AEM Forms Workspace funktioniert, um die verschiedenen unterstützten Formular- und Dateitypen wiederzugeben.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 946f0f6d-86af-41c1-98ef-98c8f5566e95
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 44%

---

# Dokumentdetails für den Renderer {#document-details-for-renderer}

## Einführung {#introduction}

Im AEM Forms-Arbeitsbereich werden mehrere Formulartypen nahtlos unterstützt. Dazu gehören:

* PDF forms (XDP/Acroform/Flache PDF)
* Neue HTML forms
* Bilder
* Drittanbieteranwendungen (z. B. Correspondence Management)

In diesem Dokument wird die Arbeit dieser Renderer aus der Perspektive der semantischen Anpassung/Komponentenwiederverwendung erläutert, sodass die Kundenanforderungen erfüllt werden, ohne dass die Ausgabedarstellung unterbrochen wird. Obwohl der Arbeitsbereich von AEM Forms beliebige Änderungen der Benutzeroberfläche oder der Bedeutung zulässt, wird empfohlen, die Rendering-Logik von verschiedenen Formulartypen nicht zu ändern. Andernfalls können die Ergebnisse unvorhersehbar sein. Dieses Dokument dient als Anleitung bzw. als Anleitung für das Rendern desselben Formulars unter Verwendung derselben Workspace-Komponenten in verschiedenen Portalen und nicht zum Ändern der Renderlogik selbst.

## PDF forms {#pdf-forms}

PDF-Formulare werden von `PdfTaskForm View` gerendert.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird vom FormsAugmenter-Service ein `FormBridge`-JavaScript™ hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offline-Schalten des Formulars.

In AEM Forms Workspace kommuniziert die Ansicht PDFTaskForm mit dem `FormBridge`JavaScript über eine zwischengeschaltete HTML unter `/lc/libs/ws/libs/ws/pdf.html`. Der Fluss ist:

**PDFTaskForm-Ansicht - pdf.html**

Kommunikation über `window.postMessage`/`window.attachEvent('message')`

Diese Methode ist die Standardkommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener aus zuvor geöffneten PDF forms werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Bereinigung wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html - `FormBridge`JavaScript innerhalb der gerenderten PDF**

Kommunikation über `pdfObject.postMessage`/`pdfObject.messageHandler`

Diese Methode ist das Standardverfahren zur Kommunikation mit einem PDF-JavaScript aus HTML. Die PdfTaskForm-Ansicht kümmert sich auch um eine flache PDF und rendert sie einfach.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt von pdf.html / der PdfTaskForm-Ansicht zu bearbeiten.

## Neue HTML Forms {#new-html-forms}

Neue HTML-Formulare werden von der NewHTMLTaskForm-Ansicht wiedergegeben.

Wenn ein XDP-Formular mit dem in CRX bereitgestellten Mobile-Formularpaket als HTML gerendert wird, wird dem Formular auch zusätzliches `FormBridge`-JavaScript hinzugefügt, das verschiedene Methoden für das Speichern und Senden von Formulardaten verfügbar macht.

Dieses JavaScript unterscheidet sich von dem, auf das oben in PDF forms verwiesen wird, erfüllt jedoch einen ähnlichen Zweck.

>[!NOTE]
>
>Adobe rät von der Bearbeitung des Inhalts der Ansicht NewHTMLTaskForm ab.

## Flex Forms und Handbücher {#flex-forms-and-guides}

Flex Forms wird von SwfTaskForm gerendert und Guides werden von HtmlTaskForm-Ansichten gerendert.

In AEM Forms Workspace kommunizieren diese Ansichten mit dem tatsächlichen SWF, aus dem das Formular/Handbuch besteht, und verwenden dazu eine zwischengeschaltete SWF unter `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

Die Kommunikation erfolgt mithilfe von `swfObject.postMessage`/`window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Die Logik berücksichtigt auch den Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht. Die `WsNextAdapter.swf` wird verwendet, um verschiedene Formularaktionen wie Speichern oder Senden auszuführen.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (z. B. Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Anwendungen von Drittanbietern werden mithilfe der Ansicht ExtAppTaskForm gerendert.

**Kommunikation zwischen Drittanbieterprogrammen und dem Arbeitsbereich von AEM Forms**

Der Arbeitsbereich von AEM Forms ruft von `window.global.postMessage([Message],[Payload])` ab.

[Nachricht] kann eine in `runtimeMap` als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` angegebene Zeichenfolge sein. Anwendungen von Drittanbietern müssen diese Schnittstelle verwenden, um den AEM Forms Workspace bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der Arbeitsbereich von AEM Forms wissen muss, wann die Aufgabe gesendet wird, damit das Aufgabefenster bereinigt werden kann.

**Kommunikation zwischen dem Arbeitsbereich von AEM Forms und Drittanbieterprogrammen**

Wenn die direkten Aktionsschaltflächen des Arbeitsbereichs von AEM Forms sichtbar sind, wird `window.[External-App-Name].getMessage([Action])` aufgerufen, wobei `[Action]` aus `routeActionMap` gelesen wird. Das Drittanbieterprogramm muss von dieser Schnittstelle abrufen und dann den Arbeitsbereich von AEM Forms über die API `postMessage ()` benachrichtigen.

Beispielsweise kann ein Flex-Programm `ExternalInterface.addCallback('getMessage', listener)` definieren, um diese Kommunikation zu unterstützen. Wenn im Drittanbieterprogramm das Senden von Formularen über eigene Schaltflächen behandelt wird, sollten Sie `hideDirectActions = true() in the runtimeMap` angeben, und Sie können diesen Listener überspringen. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen in Correspondence Management finden Sie unter [Integrieren von Correspondence Management in den AEM Forms-Arbeitsbereich](/help/forms/using/integrating-correspondence-management-html-workspace.md).
