---
title: Arbeiten mit AEM Forms Workspace
description: Dieser kurze Überblick über die Prozess-Workflows beschreibt die ersten, Schritte mit AEM Forms Workspace.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 0bedcbd9-2cf8-47da-9440-c773982e550c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1019'
ht-degree: 100%

---

# Arbeiten mit AEM Forms Workspace{#working-with-aem-forms-workspace}

## Einführung {#introduction}

AEM Forms Workspace ist Bestandteil von AEM Forms. Workspace erleichtert die Wiedergabe von HTML-Formularen zusätzlich zu PDF-Formularen. Sie können jetzt Geschäftsprozesse über mobile Schnittstellen und Web-Anwendungen durchführen.

AEM Forms Workspace lässt sich außerdem sehr genau und gezielt mithilfe von Standard-HTML- und JavaScript-Entwicklungsmethoden anpassen. Es ist eine komponentenbasierte Software, die problemlos in andere Web-Anwendungen integriert werden kann.

Weitere Informationen finden Sie unter [Einführung in AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md).

## Erste Schritte {#getting-familiar}

Um sich mit dem kompletten Ablauf zum Erstellen einer Formularanwendung vertraut zu machen, mit der ein Geschäftsprozess automatisiert wird, befolgen Sie die schrittweise Anleitung. Nachdem Sie die Anleitung durchgegangen sind, können Sie Anwendungen mithilfe von Workbench, Designer und AEM Forms Workspace erstellen, verwalten und testen. Details zur Implementierung finden Sie unter [Erstellen Ihrer ersten AEM Forms-Anwendung](https://help.adobe.com/de_DE/livecycle/11.0/CreateFirstApp/index.html).

## Funktionsüberblick {#functional-overview}

Mit AEM Forms Workspace können Sie die folgenden Aufgaben durchführen:

**Starten eines Geschäftsprozesses:** Verwenden Sie AEM Forms Workspace-Kategorien für Ihre Prozesse, wie sie von Ihrem Unternehmen entworfen und eingerichtet wurden. Sie können häufig verwendete Kategorien als Favoriten definieren, um schneller auf die Kategorien zugreifen zu können. Beim Starten eines Prozesses füllen Sie normalerweise ein Formular aus, um einen von Forms Workflow gesteuerten Geschäftsprozess zu starten. Weitere Informationen finden Sie unter [Starten von Prozessen](/help/forms/using/starting-processes.md).

**Anzeigen und Ausführen von Aufgaben:** Wenn Sie Ihre Aufgabenlisten anzeigen, sehen Sie möglicherweise Aufgaben aus einem Geschäftsprozess, die Ihnen oder Gruppen, denen Sie angehören, zugewiesen sind oder die freigegebene Aufgaben anderer Benutzer sind. Sie können die Aufgaben wie benötigt öffnen, bearbeiten und abschließen. Um eine Aufgabe abzuschließen, müssen Sie normalerweise Informationen angeben, ein Formular genehmigen oder es ablehnen. Weitere Informationen hierzu finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md).

**Verfolgen von Aufgaben**: Um Ihre Aufgaben zu verfolgen, verwenden Sie die Registerkarte „Tracking“ von AEM Forms Workspace. Sie können nach aktiven oder abgeschlossenen Prozessen suchen, die von Ihnen gestartet wurden oder an denen Sie teilgenommen haben. Sie können die Aufgaben, Zuweisungen und Formulare anzeigen, die Teil des Prozesses waren. Zudem können Sie neue Prozesse mithilfe von Formulardaten aus einem zuvor initiierten Prozess starten. Weitere Informationen finden Sie unter [Tracking von Prozessen](/help/forms/using/tracking-processes.md).

## Neues Angebot von AEM Forms Workspace {#new-offering-of-aem-forms-workspace}

**Unterstützung für Massengenehmigung von Aufgaben**:

Sie können mehrere Aufgaben desselben Typs genehmigen. Wenn Sie eine Aufgabe zur Genehmigung auswählen, bleiben nur Aufgaben desselben Prozesses mit denselben Aufgabennamen und denselben Routenoptionen aktiviert. Informationen zur Implementierung finden Sie unter [Arbeiten mit Aufgabenlisten](/help/forms/using/todo-lists.md).

## Migrieren von Flex Workspace zu AEM Forms Workspace {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wird für AEM Forms-Kundinnen und -Kunden nicht unterstützt. Alle Kundinnen und Kunden, die Flex Workspace verwenden, sollten zu AEM Forms Workspace wechseln.

In AEM Forms Workspace wurden die mit XDP-Formularen verknüpften standardmäßigen Wiedergabe- und Sendedienste im standardmäßigen Aktionsprofil geändert und neue Dienste wurden eingeführt. Weitere Details finden Sie unter [Neuer Wiedergabe- und Sendedienst](/help/forms/using/new-render-submit-service.md). Um Ihre vorhandenen Prozesse, die XDP-Formulare nutzen, zu migrieren, sodass Sie diese Dienste nutzen können, führen Sie [diese Schritte](new-render-submit-service.md) aus.

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
     <li>Ändern des Gebietsschemas für den Workspace</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Änderung des Gebietsschemas für den AEM Forms-Arbeitsbereich</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Anpassung des Designs</td>
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
   <td>Anpassung des Layouts</td>
   <td>
    <ol>
     <li>Vereinfachen der Workspace-Benutzeroberfläche<br /> </li>
     <li>Erstellen eines neuen Anmeldebildschirms</li>
     <li>Festlegen eines benutzerdefinierten Genehmigungs-Containers</li>
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

Zu den Funktionen von Flex Workspace, die nicht in AEM Forms Workspace verfügbar sind, gehören: Nachrichten und Benachrichtigungen, Begrüßungsseite, Genehmigungs-Container sowie die Option zur Verwaltung von Spaltenüberschriften. Eine vollständige Liste finden Sie unter [In AEM Forms Workspace nicht verfügbare Funktionen von Flex Workspace](/help/forms/using/features-flex-workspace-available-html.md).

## Entwickeln mit AEM Forms Workspace {#developing-with-aem-forms-workspace}

### Architektur {#architecture}

AEM Forms Workspace ist eine auf HTML und JavaScript™ basierende Web-Anwendung, die auf CRX™ gehostet wird. Wenn die Workspace-URL in einem Browser geöffnet wird, wird auf eine CRX™-Ressource zugegriffen und die Anwendung wird als HTML-Seite im Browser wiedergegeben. Die JavaScript-Bibliotheken und der benutzerdefinierte JavaScript-Code verwalten das interne und externe Verhalten der Anwendung, z. B. die Benutzeroberfläche, die Benutzerinteraktion und die Kommunikation mit dem AEM Forms-Server. Weitere Details finden Sie unter [AEM Forms Workspace-Architektur](/help/forms/using/html-workspace-architecture.md).

### Anpassen von AEM Forms Workspace {#aem-forms-workspace-customization}

AEM Forms Workspace unterstützt viele Anpassungen, mit denen das Layout, die Darstellung, die Funktionalität und andere Aspekte der Benutzeroberfläche aktualisiert werden können. Bei den Anpassungen wird mindestens einer der folgenden Faktoren aktualisiert:

* Aussehen der Benutzeroberfläche
* Funktionen mithilfe der semantischen Anpassungen
* Wiederverwenden von HTML-Komponenten in anderen Web-Anwendungen

Der Artikel zu [Anpassungen](introduction-customizing-html-workspace.md#types-of-customizations) beschreibt die Arten solcher Anpassungen.

### Einrichten der Entwicklungsumgebung {#set-up-the-developer-environment}

AEM Forms Workspace wird mit einem auf CRX implementierten CRX -Paket, einem SDK-Archiv mit dem vollständigen Quell-Code, JavaScript-Bibliotheken anderer Anbieter sowie Build-Skripten von AEM Forms Workspace bereitgestellt. Verwenden Sie diese zum Einrichten der Entwicklungsumgebung, um die oben genannten Anpassungen durchführen zu können. Weitere Informationen finden Sie unter [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code).

Sie können einen Großteil der Benutzeroberfläche sowie Hauptfunktionen wie Schriftarten, Farbschema, Logo, Anmeldebildschirm, Fehlerdialogfelder, Integration mit Anwendungen anderer Anbieter und Wiederverwendung von Komponenten in Anwendungen anderer Anbieter anpassen. Sie können darüber hinaus den Inhalt der Seite „Aufgabenzusammenfassung“ verbessern, Abbildungen zu Aktionen für Aufgabenrouten anzeigen und sogar die systemnahen Backbone-Modelle und Ansichten bearbeiten, die die AEM Forms Workspace-Anwendung erstellen.

### HTML-Rendern von XDP-Formularen {#html-rendering-of-xdp-forms}

Für neue Prozesse werden XDP-Formulare standardmäßig auf dem Desktop im PDF- und auf Tablets im HTML-Format wiedergegeben. Es ist möglich, ein XDP-Formular immer im HTML-Format zu rendern. Weitere Informationen finden Sie unter [Neue Render- und Sendedienste](/help/forms/using/new-render-submit-service.md).

Die [Mobile Forms](https://helpx.adobe.com/de/livecycle/help/mobile-forms/introduction.html)-Funktion, die [Profile](https://helpx.adobe.com/de/livecycle/help/mobile-forms/creating-profile.html) nutzt, ermöglicht die HTML-Ausgabedarstellung von XDP-Formularen. „Render New HTML Form (neu)“ nutzt standardmäßig das Profil `default.html`, das Sie ändern können. Sie können darüber hinaus benutzerdefinierte Änderungen hinzufügen, die erfolgen, bevor das XDP-Formular im HTML-Format gerendert wird.

## AEM Forms Workspace-App {#aem-forms-workspace-app}

Um auf einem Mobilgerät an Ihren Geschäftsprozessen zu arbeiten, können Sie die für AEM Forms angebotene AEM Forms-Workspace-App verwenden. Weitere Informationen finden Sie unter [Überblick über die AEM Forms Workspace-App](https://helpx.adobe.com/de/livecycle/help/mobile-workspace/mobile-workspace-overview.html).
