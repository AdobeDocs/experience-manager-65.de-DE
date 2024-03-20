---
title: Arbeiten mit AEM Forms Workspace
description: Erste Schritte mit AEM Forms Workspace mit diesem kurzen Überblick über die Prozess-Workflows.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 0bedcbd9-2cf8-47da-9440-c773982e550c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 27%

---

# Arbeiten mit AEM Forms Workspace{#working-with-aem-forms-workspace}

## Einführung {#introduction}

AEM Forms Workspace ist Teil von AEM Forms. Workspace erleichtert die Wiedergabe von HTML-Formularen zusätzlich zu PDF-Formularen. Jetzt können Sie Geschäftsprozesse über mobile Schnittstellen und Webanwendungen durchführen.

AEM Forms Workspace lässt sich außerdem sehr genau und gezielt mithilfe von Standard-HTML- und JavaScript-Entwicklungsmethoden anpassen. Es handelt sich dabei um eine komponentenbasierte Software, die einfach in Ihre anderen Webanwendungen integriert werden kann.

Weitere Informationen finden Sie unter [Einführung in AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md).

## Erste Schritte {#getting-familiar}

Um sich mit dem End-to-End-Prozess zum Erstellen einer Formularanwendung zur Automatisierung eines Geschäftsprozesses vertraut zu machen, führen Sie die Anleitung aus. Nachdem Sie die Anleitung ausgeführt haben, können Sie eine Anwendung mit Workbench, Designer und AEM Forms Workspace erstellen, verwalten und testen. Weitere Informationen zur Implementierung finden Sie unter [Erstellen der ersten AEM Forms-Anwendung](https://help.adobe.com/de_DE/livecycle/11.0/CreateFirstApp/index.html).

## Funktionsübersicht {#functional-overview}

Sie können AEM Forms Workspace verwenden, um die folgenden Aufgaben auszuführen:

**Starten eines Geschäftsprozesses:** Verwenden Sie AEM Forms Workspace-Kategorien für Ihre Prozesse, wie sie von Ihrem Unternehmen entworfen und eingerichtet wurden. Sie können häufig verwendete Kategorien bevorzugen, um schnell auf die Kategorien zugreifen zu können. Wenn Sie einen Prozess starten, füllen Sie normalerweise ein Formular aus, um einen Geschäftsprozess zu starten, den der Arbeitsablauf für Formulare steuert. Weitere Informationen finden Sie unter [Starten von Prozessen](/help/forms/using/starting-processes.md).

**Anzeigen und Ausführen von Aufgaben:** Wenn Sie Ihre Aufgabenlisten anzeigen, sehen Sie möglicherweise Aufgaben aus einem Geschäftsprozess, die Ihnen oder Gruppen, denen Sie angehören, zugewiesen sind oder die freigegebene Aufgaben anderer Benutzer sind. Sie können die Aufgaben nach Bedarf öffnen, bearbeiten und abschließen. Normalerweise umfasst das Abschließen einer Aufgabe die Bereitstellung von Informationen, das Genehmigen eines Formulars oder das Zurückweisen eines Formulars. Weitere Informationen finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md).

**Aufgaben verfolgen**: Um Ihre Aufgaben zu verfolgen, verwenden Sie die Registerkarte Verfolgung im AEM Forms-Arbeitsbereich. Sie können nach aktiven oder abgeschlossenen Prozessen suchen, die Sie gestartet haben oder an denen Sie beteiligt waren. Sie können die Aufgaben, Zuweisungen und Formulare anzeigen, die Teil des Prozesses waren. Sie können auch neue Prozesse mit Formulardaten aus einem zuvor initiierten Prozess starten. Weitere Informationen finden Sie unter [Verfolgen von Prozessen](/help/forms/using/tracking-processes.md).

## Neues Angebot von AEM Forms Workspace {#new-offering-of-aem-forms-workspace}

**Unterstützung der Massengenehmigung von Aufgaben**:

Sie können mehrere Aufgaben desselben Typs genehmigen. Wenn Sie eine Aufgabe zur Genehmigung auswählen, bleiben nur Aufgaben desselben Prozesses mit denselben Aufgabennamen und denselben Routenoptionen aktiviert. Informationen zur Implementierung finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md).

## Migrieren von Flex Workspace zu AEM Forms Workspace {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wird für AEM Forms-Kunden nicht unterstützt. Alle Kunden, die Flex Workspace verwenden, sollten zu AEM Forms Workspace wechseln.

In AEM Forms Workspace wurden die standardmäßigen Wiedergabe- und Sendedienste im standardmäßigen Aktionsprofil, die mit XDP-Formularen verknüpft sind, geändert und neue Dienste wurden eingeführt. Weitere Informationen finden Sie unter [Neuer Wiedergabe- und Sendedienst](/help/forms/using/new-render-submit-service.md). Um Ihre vorhandenen Prozesse, die mit XDP-Formularen funktionieren, zu migrieren, um diese Dienste zu verwenden, können Sie folgende Schritte ausführen: [diese Schritte](new-render-submit-service.md).

**Zuordnen von Flex Workspace-Anpassungen zu AEM Forms Workspace**

Die verschiedenen Arten der Anpassung in beiden Arbeitsbereichen werden wie folgt zugeordnet.

<table>
 <tbody>
  <tr>
   <td><strong>Art der Anpassung </strong></td>
   <td><strong>Betroffene Anpassungen umfasst </strong></td>
   <td><strong>Entsprechendes Anpassungsszenario in AEM Forms Workspace</strong></td>
  </tr>
  <tr>
   <td>Anpassung der Lokalisierung</td>
   <td>
    <ol>
     <li>Ändern des Gebietsschemas von Workspace</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Änderung des Gebietsschemas für den AEM Forms-Arbeitsbereich</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Designanpassung</td>
   <td>
    <ol>
     <li>Ersetzen von Bildern</li>
     <li>Ändern von Farben</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-organization-logo-branding.md">Änderung des Unternehmenslogos</a> </li>
     <li><a href="/help/forms/using/changing-color-scheme-interface.md">Änderung des Farbschemas</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Layout-Anpassung</td>
   <td>
    <ol>
     <li>Vereinfachung der Workspace-Benutzeroberfläche<br /> </li>
     <li>Erstellen eines neuen Anmeldebildschirms</li>
     <li>Erstellen eines benutzerdefinierten Approval-Containers</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/description-reusable-components.md">Arbeiten mit wiederverwendbaren Komponenten</a></li>
     <li><a href="/help/forms/using/creating-new-login-screen.md">Erstellen eines Anmeldebildschirms</a></li>
     <li>Approval-Container wird nicht mehr unterstützt.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

Zu den Funktionen von Flex Workspace, die in AEM Forms Workspace nicht verfügbar sind, gehören: Nachrichten und Benachrichtigungen, Begrüßungsseite, Genehmigungs-Container und Optionen zum Verwalten von Spaltenüberschriften. Eine vollständige Liste finden Sie unter [In AEM Forms Workspace nicht verfügbare Funktionen von Flex Workspace](/help/forms/using/features-flex-workspace-available-html.md).

## Entwickeln mit AEM Forms Workspace {#developing-with-aem-forms-workspace}

### Architektur {#architecture}

AEM Forms Workspace ist eine auf HTML und JavaScript™ basierende Webanwendung, die auf CRX™ gehostet wird. Wenn die Workspace-URL in einem Browser geöffnet wird, wird auf eine CRX™-Ressource zugegriffen und die Anwendung wird als HTML-Seite im Browser wiedergegeben. Die JavaScript-Bibliotheken und der benutzerdefinierte JavaScript-Code verwalten das interne und externe Verhalten der Anwendung, z. B. die Benutzeroberfläche, die Benutzerinteraktion und die Kommunikation mit dem AEM Forms-Server. Weitere Informationen finden Sie unter AEM Forms Workspace . [Architektur](/help/forms/using/html-workspace-architecture.md).

### Anpassung von AEM Forms Workspace {#aem-forms-workspace-customization}

AEM Forms Workspace unterstützt viele Anpassungen, mit denen das Layout, die Darstellung, die Funktionalität und andere Aspekte der Benutzeroberfläche aktualisiert werden können. Die Anpassungen umfassen die Aktualisierung einer oder mehrerer der folgenden Elemente:

* Erscheinungsbild der Benutzeroberfläche
* Funktionalität mithilfe semantischer Anpassungen
* Wiederverwenden von HTML-Komponenten in anderen Webanwendungen

Die [Anpassung](introduction-customizing-html-workspace.md#types-of-customizations) In diesem Artikel werden die Arten solcher Anpassungen erläutert.

### Einrichten der Entwicklungsumgebung {#set-up-the-developer-environment}

AEM Forms Workspace-Lieferziele umfassen ein CRX-Paket, das auf CRX bereitgestellt wird, einem SDK-Archiv, das den vollständigen Quellcode, JavaScript-Bibliotheken von Drittanbietern und Build-Skripte von AEM Forms Workspace enthält. Verwenden Sie diese, um die Entwicklungsumgebung für die oben genannten Anpassungen einzurichten. Weitere Informationen finden Sie unter [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code).

Sie können einen Großteil der Benutzeroberfläche und Kernfunktionen anpassen, z. B. Schriftarten, Farbschema, Logo, Anmeldebildschirm, Fehlerdialogfelder, Integration mit Drittanbieteranwendungen und Wiederverwendung von Komponenten in Drittanbieteranwendungen. Sie können auch die auf der Seite &quot;Aufgabenzusammenfassung&quot;angezeigten Inhalte erweitern, Bilder für Aufgabenrouten-Aktionen anzeigen und sogar die Hintergrundmodelle und Ansichten ändern, die die AEM Forms Workspace-Anwendung erstellen.

### HTML-Rendering von XDP Forms {#html-rendering-of-xdp-forms}

Für einen neuen Prozess wird ein XDP-Formular standardmäßig auf einem Desktop im PDF-Format und auf einem Tablet im HTML-Format wiedergegeben. Es ist möglich, ein XDP-Formular immer im HTML-Format wiederzugeben. Weitere Informationen finden Sie unter [Neue Wiedergabe- und Sendedienste](/help/forms/using/new-render-submit-service.md).

Die [Mobile Forms](https://helpx.adobe.com/de/livecycle/help/mobile-forms/introduction.html)-Funktion, die [Profile](https://helpx.adobe.com/de/livecycle/help/mobile-forms/creating-profile.html) nutzt, ermöglicht die HTML-Ausgabedarstellung von XDP-Formularen. „Render New HTML Form (neu)“ nutzt standardmäßig das Profil `default.html`, das Sie ändern können. Sie können auch benutzerdefinierte Änderungen hinzufügen, die vor dem Rendern eines XDP-Formulars im HTML-Format vorgenommen werden.

## AEM Forms Workspace-App {#aem-forms-workspace-app}

Um auf einem Mobilgerät an Ihren Geschäftsprozessen zu arbeiten, können Sie die AEM Forms Workspace-App von AEM Forms verwenden. Weitere Informationen finden Sie unter [Übersicht über die AEM Forms Workspace-App](https://helpx.adobe.com/de/livecycle/help/mobile-workspace/mobile-workspace-overview.html).
