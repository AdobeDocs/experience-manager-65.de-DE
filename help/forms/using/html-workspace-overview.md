---
title: Arbeiten mit AEM Forms Workspace
seo-title: Arbeiten mit AEM Forms Workspace
description: Dieser kurze Überblick über die Prozessabläufe beschreibt erste Schritte mit AEM Forms Workspace.
seo-description: Dieser kurze Überblick über die Prozessabläufe beschreibt erste Schritte mit AEM Forms Workspace.
uuid: 36381e7b-1533-459c-80de-92e806a49cd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 866cd9cb-6661-4b0f-a3af-e39453e6e51b
docset: aem65
exl-id: 0bedcbd9-2cf8-47da-9440-c773982e550c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 87%

---

# Arbeiten mit AEM Forms Workspace{#working-with-aem-forms-workspace}

## Einführung {#introduction}

AEM Forms Workspace ist Bestandteil von AEM Forms. Workspace erleichtert die Wiedergabe von HTML-Formularen zusätzlich zu PDF-Formularen. Jetzt können Sie Geschäftsprozesse über mobile Schnittstellen und Webanwendungen durchführen.

AEM Forms Workspace lässt sich außerdem sehr genau und gezielt mithilfe von Standard-HTML- und JavaScript-Entwicklungsmethoden anpassen. Es ist eine komponentenbasierte Software, die problemlos in andere Webanwendungen integriert werden kann.

Weitere Informationen finden Sie unter [Einführung in AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md).

## Erste Schritte {#getting-familiar}

Um sich mit dem kompletten Ablauf zum Erstellen einer Formularanwendung vertraut zu machen, mit der ein Geschäftsprozess automatisiert wird, befolgen Sie die schrittweisen Anleitung. Nachdem Sie die Anleitung ausgeführt haben, können Sie Anwendungen mithilfe von Workbench, Designer und AEM Forms Workspace erstellen, verwalten und testen. Nähere Informationen zur Implementierung finden Sie unter [Erstellen der ersten AEM Forms-Anwendung](https://help.adobe.com/en_US/livecycle/11.0/CreateFirstApp/index.html).

## Funktionsübersicht  {#functional-overview}

Mit AEM Forms Workspace können Sie die folgenden Aufgaben durchführen:

**Geschäftsprozess starten:** AEM Forms Workspace kategorisiert Ihre Prozesse, wie sie von Ihrem Unternehmen entwickelt und eingerichtet wurden. Sie können häufig verwendete Kategorien als Favoriten definieren, um schneller auf die zugreifen zu können. Beim Starten eines Prozesses füllen Sie normalerweise ein Formular aus, um einen von Forms gesteuerten Geschäftsprozess zu starten. Weitere Informationen finden Sie unter [Starten von Prozessen](/help/forms/using/starting-processes.md).

**Anzeigen von Aufgaben und Ausführen von Aufgaben:** Wenn Sie Ihre Aufgabenlisten anzeigen, sehen Sie Aufgaben aus einem Geschäftsprozess, die Ihnen oder Gruppen zugewiesen sind, denen Sie angehören, oder die freigegebenen Aufgaben anderer Benutzer sind. Sie können die Aufgaben wie benötigt öffnen, bearbeiten und abschließen. Um eine Aufgabe abzuschließen, müssen Sie normalerweise Informationen angeben, ein Formular genehmigen oder es ablehnen. Weitere Informationen hierzu finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md).

**Verfolgen von Aufgaben**: Um Ihre Aufgaben zu verfolgen, verwenden Sie die Registerkarte „Verfolgung“ von AEM Forms Workspace. Sie können nach aktiven oder abgeschlossenen Prozessen suchen, die von Ihnen gestartet wurden oder an denen Sie teilgenommen haben. Sie können die Aufgaben, Zuweisungen und Formulare anzeigen, die Teil des Prozesses waren. Zudem können Sie neue Prozesse mit Formulardaten aus einem zuvor gestarteten Prozess starten. Weitere Informationen finden Sie unter finden Sie unter [Verfolgen von Prozessen](/help/forms/using/tracking-processes.md).

## Neues Angebot von AEM Forms Workspace  {#new-offering-of-aem-forms-workspace}

**Unterstützung für Massengenehmigung von Aufgaben**:

Sie können mehrere Aufgaben desselben Typs genehmigen. Nachdem Sie eine Aufgabe zur Genehmigung ausgewählt haben, bleiben nur die Aufgaben mit demselben Prozess, mit denselben Aufgabennamen und denselben Routenoptionen aktiviert. Implementierungsdetails finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md) .

## Migrieren von Flex Workspace zu AEM Forms Workspace {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wird für AEM Forms-Kunden nicht unterstützt. Alle Kunden, die Flex Workspace verwenden, sollten zu AEM Forms Workspace wechseln.

In AEM Forms Workspace wurden die mit XDP-Formularen verknüpften standardmäßigen Wiedergabe- und Sendedienste im standardmäßigen Aktionsprofil geändert und neue Dienste wurden eingeführt. Weitere Informationen finden Sie unter [Neue Wiedergabe- und Sendedienste](/help/forms/using/new-render-submit-service.md). Um Ihre vorhandenen Prozesse, die XDP-Formulare nutzen, zu migrieren, sodass Sie diese Dienste nutzen können, führen Sie [diese Schritte](new-render-submit-service.md) aus.

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
   <td>Lokalisierungsanpassung</td>
   <td>
    <ol>
     <li>Änderung des Gebietsschemas für den Arbeitsbereich</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Änderung des Gebietsschemas für den Arbeitsbereich</a></li>
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
   <td>Layoutanpassung</td>
   <td>
    <ol>
     <li>Vereinfachung der Workspace-Benutzeroberfläche<br /> </li>
     <li>Erstellen eines neuen Anmeldebildschirms</li>
     <li>Festlegen eines benutzerdefinierten Approval-Containers</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/description-reusable-components.md">Arbeiten mit wiederverwendbaren Komponenten</a></li>
     <li><a href="/help/forms/using/creating-new-login-screen.md">Erstellen eines neuen Anmeldebildschirms</a></li>
     <li>Approval-Container wird nicht mehr unterstützt.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

Zu den Funktionen von Flex Workspace, die nicht in AEM Forms Workspace verfügbar sind, gehören: Nachrichten und Benachrichtigungen, Begrüßungsseite, Approval-Container sowie die Option zur Verwaltung von Spaltenüberschriften. Eine vollständige Liste finden Sie unter [In AEM Forms Workspace nicht verfügbare Funktionen von Flex Workspace](/help/forms/using/features-flex-workspace-available-html.md).

## Entwickeln mit AEM Forms Workspace  {#developing-with-aem-forms-workspace}

### Architektur {#architecture}

AEM Forms Workspace ist eine auf HTML und JavaScript™ basierende Webanwendung, die auf CRX™ gehostet wird. Wenn die Workspace-URL in einem Browser geöffnet wird, wird auf eine CRX™-Ressource zugegriffen und die Anwendung wird als HTML-Seite im Browser wiedergegeben. Die JavaScript-Bibliotheken und der benutzerdefinierte JavaScript-Code verwalten das interne und externe Verhalten der Anwendung, z. B. die Benutzeroberfläche, die Interaktion und die Kommunikation mit AEM Forms-Server. Weitere Informationen finden Sie unter AEM Forms Workspace-[Architektur](/help/forms/using/html-workspace-architecture.md).

### Anpassung von AEM Forms Workspace  {#aem-forms-workspace-customization}

AEM Forms Workspace unterstützt viele Anpassungen, mit denen das Layout, die Darstellung, die Funktionalität und andere Aspekte der Benutzeroberfläche aktualisiert werden können. Bei den Anpassungen wird mindestens eins der folgenden Faktoren aktualisiert:

* Aussehen der Benutzeroberfläche
* Funktionen mithilfe der semantischen Anpassungen
* Wiederverwenden von HTML-Komponenten in anderen Webanwendungen

Der Artikel zu [Anpassungen](introduction-customizing-html-workspace.md#types-of-customizations) beschreibt die Arten solcher Anpassungen.

### Einrichten der Entwicklungsumgebung  {#set-up-the-developer-environment}

AEM Forms Workspace wird bereitgestellt mit einem auf CRX implementierten CRX -Paket, einem SDK-Archiv mit dem vollständigen Quellcode, JavaScript-Bibliotheken anderer Anbieter sowie Build-Skripten von AEM Forms Workspace. Verwenden Sie diese zum Einrichten der Entwicklungsumgebung, um die oben genannten Anpassungen durchführen zu können. Weitere Informationen finden Sie unter [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code).

Sie können einen Großteil der Benutzeroberfläche sowie Hauptfunktionen wie Schriftarten, Farbschema, Logo, Anmeldebildschirm, Fehlerdialoge, Integration mit Anwendungen anderer Anbieter und Wiederverwendung von Komponenten in Anwendungen anderer Anbieter anpassen. Sie können darüber hinaus den Inhalt der Seite „Aufgabenzusammenfassung“ verbessern, Abbildungen zu Aktionen für Aufgabenrouten anzeigen und sogar die systemnahen Backbone-Modelle und Ansichten bearbeiten, die die AEM Forms Workspace-Anwendung erstellen.

### HTML-Wiedergabe von XDP-Formularen {#html-rendering-of-xdp-forms}

Für neue Prozesse werden XDP-Formulare standardmäßig auf dem Desktop im PDF- und auf Tablets im HTML-Format wiedergegeben. Es ist möglich, XDP-Formulare immer im HTML-Format wiederzugeben. Weitere Informationen finden Sie unter [Neue Wiedergabe- und Sendedienste](/help/forms/using/new-render-submit-service.md).

[Mobile ](https://helpx.adobe.com/livecycle/help/mobile-forms/introduction.html) Forms-Funktion, die mit  [Profilen](https://helpx.adobe.com/livecycle/help/mobile-forms/creating-profile.html) arbeitet, ermöglicht die HTML-Ausgabe von XDP-Formularen. „Render New HTML Form (neu)“ nutzt standardmäßig das Profil `default.html`, das Sie ändern können. Sie können darüber hinaus benutzerdefinierte Änderungen hinzufügen, die erfolgen, bevor das XDP-Formular im HTML-Format wiedergegeben wird.

## AEM Forms-Workspace-Applikation  {#aem-forms-workspace-app}

Um auf einem Mobilgerät an Ihren Geschäftsprozessen zu arbeiten, können Sie die für AEM Forms angebotene AEM Forms-Workspace-Applikation verwenden. Weitere Informationen finden Sie unter [Übersicht über AEM Forms Workspace-Applikation](https://helpx.adobe.com/livecycle/help/mobile-workspace/mobile-workspace-overview.html).
