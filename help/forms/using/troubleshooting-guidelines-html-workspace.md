---
title: Fehlerbehebung bei Richtlinien für einen AEM Forms-Arbeitsbereich
description: Aktivieren Sie Protokolle und verwenden Sie Debugger im Browser, um eine Fehlerbehebung in AEM Forms Workspace durchzuführen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: a054b60a-5e89-4c98-87bc-35669988d160
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 100%

---

# Fehlerbehebung bei Richtlinien für einen AEM Forms-Arbeitsbereich {#troubleshooting-guidelines-for-aem-forms-workspace}

Dieser Artikel erläutert, wie Sie AEM Forms Workspace debuggen, indem Sie die Protokollierung aktivieren und den Debugger in einem Browser verwenden. Außerdem werden einige häufig auftretende Probleme bei der Verwendung von AEM Forms Workspace und deren Umgehungslösungen erläutert.

## AEM Forms Workspace-Paket kann nicht installiert werden {#unable-to-install-aem-forms-workspace-package}

Öffnen Sie nach der Installation des Patches den AEM Forms Workspace. Falls ein Fehler vom Typ „Keine Resource gefunden“ auftritt, öffnen Sie CRX Package Manager und installieren Sie das Paket `adobe-lc-workspace-pkg-<version>.zip` erneut.

Wenn während der Installation des Pakets der Fehler `javax.jcr.nodetype.ConstraintViolationException: OakConstraint0025: Authorizable property rep:authorizableId may not be removed` auftritt, führen Sie folgende Schritte aus:

1. Melden Sie sich bei CRXDE Lite an. Die Standard-URL ist `https://[localhost]:'port'/lc/crx/de/index.jsp`
1. Löschen Sie den folgenden Knoten:

   `/home/groups/P/PERM_WORKSPACE_USER`

1. Navigieren Sie zu Package Manager. Die Standardeinstellung ist `https://[localhost]:'port'/lc/crx/packmgr/index.jsp.`
1. Suchen Sie das Paket `adobe-lc-workspace-pkg-[version].zip` und installieren Sie es.
1. Starten Sie den Anwendungs-Server neu.

>[!NOTE]
>
> Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## AEM Forms Workspace-Protokollierung {#aem-forms-workspace-nbsp-logging}

Sie können Protokolle auf verschiedenen Ebenen generieren, um eine optimale Fehlerbehebung zu ermöglichen. In einer komplexen Anwendung hilft beispielsweise die Protokollierung auf Komponentenebene beim Debugging und der Fehlerbehebung bei bestimmten Komponenten.

In AEM Forms Workspace:

* Um die Protokollinformationen zu einer bestimmten Komponentendatei zu erhalten, hängen Sie `/log/<ComponentFile>/<LogLevel>` an die URL an und drücken Sie `Enter`. Alle Protokollinformationen für die Komponentendatei auf der angegebenen Protokollebene werden in der Konsole ausgegeben.

* Um Protokollinformationen zu allen Komponentendateien zu erhalten, hängen Sie `/log/all/trace` an die URL an und drücken Sie `Enter`.

* Protokollformat: `<Component file> <Date>:<Time>: <Log Level> : <Log Message>`

>[!NOTE]
>
>Standardmäßig ist die Protokollebene aller Komponenten auf INFO festgelegt.

* Die von Benutzern bzw. Benutzerinnen festgelegte Protokollebene wird nur für diese Browser-Sitzung beibehalten. Wenn Benutzer bzw. Benutzerinnen die Seite aktualisieren, wird die Protokollebene für alle Komponenten auf ihren ursprünglichen Wert festgelegt.

### Liste der Komponentendateien in AEM Forms Workspace {#list-of-component-files-in-nbsp-aem-forms-workspace}

<table>
 <tbody>
  <tr>
   <td><p>allcategoryModel</p> </td>
   <td><p>processinstanceModel</p> </td>
   <td><p>tasklistModel</p> </td>
  </tr>
  <tr>
   <td><p>appnavigationModel</p> </td>
   <td><p>processInstanceView</p> </td>
   <td><p>tasklistView</p> </td>
  </tr>
  <tr>
   <td><p>appnavigationView</p> </td>
   <td><p>processnamelistModel</p> </td>
   <td><p>taskModel</p> </td>
  </tr>
  <tr>
   <td><p>categorylistModel</p> </td>
   <td><p>processnamelistView</p> </td>
   <td><p>taskView</p> </td>
  </tr>
  <tr>
   <td><p>categorylistView</p> </td>
   <td><p>processnameModel</p> </td>
   <td><p>teamqueuesView</p> </td>
  </tr>
  <tr>
   <td><p>categoryModel</p> </td>
   <td><p>processnameView</p> </td>
   <td><p>todoView</p> </td>
  </tr>
  <tr>
   <td><p>categoryView</p> </td>
   <td><p>searchtemplatedetailsView</p> </td>
   <td><p>trackingView</p> </td>
  </tr>
  <tr>
   <td><p>favoritecategoryModel</p> </td>
   <td><p>sharequeueModel</p> </td>
   <td><p>uisettingsModel</p> </td>
  </tr>
  <tr>
   <td><p>filterlistView</p> </td>
   <td><p>sharequeueView</p> </td>
   <td><p>uisettingsView</p> </td>
  </tr>
  <tr>
   <td><p>filterView</p> </td>
   <td><p>startpointlistModel</p> </td>
   <td><p>userinfoModel</p> </td>
  </tr>
  <tr>
   <td><p>outofofficeModel</p> </td>
   <td><p>startpointlistView</p> </td>
   <td><p>userinfoView</p> </td>
  </tr>
  <tr>
   <td><p>outofofficeView</p> </td>
   <td><p>startpointModel</p> </td>
   <td><p>usersearchModel</p> </td>
  </tr>
  <tr>
   <td><p>preferencesView</p> </td>
   <td><p>startpointView</p> </td>
   <td><p>usersearchView</p> </td>
  </tr>
  <tr>
   <td><p>processinstancehistoryView</p> </td>
   <td><p>startProcessView</p> </td>
   <td><p>wserrorModel</p> </td>
  </tr>
  <tr>
   <td><p>processinstancelistModel</p> </td>
   <td><p>startprocessView</p> </td>
   <td><p>wserrorView</p> </td>
  </tr>
  <tr>
   <td><p>processinstancelistView</p> </td>
   <td><p>taskdetailsView</p> </td>
   <td><p>wsmessageView</p> </td>
  </tr>
 </tbody>
</table>

### Verfügbare Protokollebenen in AEM Forms Workspace {#log-levels-available-in-nbsp-aem-forms-workspace}

* FATAL
* ERROR
* WARN
* INFO
* DEBUG
* TRACE
* AUS

## Debugging-Informationen für Browser {#debugging-information-for-browsers}

Das Debugging von Skripten und Stilen ist in verschiedenen Browsern möglich.

* **Debugging in IE**: Informationen zum Debugging von AEM Forms Workspace in IE finden Sie unter: [https://learn.microsoft.com/de-de/office/dev/add-ins/testing/debug-add-ins-using-f12-tools-ie](https://learn.microsoft.com/de-de/office/dev/add-ins/testing/debug-add-ins-using-f12-tools-ie).

* **Debugging in Chrome**: Um den Debugger in Chrome zu öffnen, verwenden Sie den Tastaturbefehl Strg+Umschalt+I. Weitere Informationen finden Sie unter: [https://developer.chrome.com/docs/extensions/mv3/tut_debugging/](https://developer.chrome.com/docs/extensions/mv3/tut_debugging/).

* **Debugging in Firefox**: Zum Debugging von Skripten und Stilen in Firefox stehen mehrere Add-ons zur Verfügung. Zum Beispiel ist Firebug ein solches Debugging-Programm ([https://getfirebug.com](https://getfirebug.com)).

## Häufig gestellte Fragen {#faqs}

1. PDF-Formular wird in Google Chrome nicht gerendert oder übermittelt.

   1. Installieren Sie das Adobe® Reader®-Plug-in.
   1. Öffnen Sie in Chrome chrome://plugins, um verfügbare Plug-ins anzuzeigen.
   1. Deaktivieren Sie das Chrome PDF Viewer-Plug-in und aktivieren Sie das Adobe Reader-Plug-in.

1. SWF-Formular oder Guide wird in Google Chrome nicht gerendert.

   1. Öffnen Sie in Chrome chrome://plugins, um verfügbare Plug-ins anzuzeigen.
   1. Sehen Sie sich die Details zum Adobe Flash® Player-Plug-in an.
   1. Deaktivieren Sie PepperFlash unter dem Adobe Flash Player-Plug-in.

1. Ich habe AEM Forms Workspace angepasst, kann die Änderungen jedoch nicht sehen.

   Löschen Sie den Cache des Browsers und rufen Sie dann AEM Forms Workspace auf.

1. Was müssen Benutzer bzw. Benutzerinnen tun, damit das Formular beim Öffnen auf dem Desktop in HTML gerendert werden kann?

   Wählen Sie bei Verwendung von Workbench im Schritt „Aufgabe zuweisen“ die Optionsschaltfläche „HTML“ für das Standardprofil aus.

1. Der Anhang wird beim Klicken nicht angezeigt.

   Um Anlagen anzuzeigen, aktivieren Sie Popups in Ihrem Browser.

1. Eine Benutzerin bzw. ein Benutzer ist bei einer Formularanwendung angemeldet. Wenn die Benutzerin bzw. der Benutzer versucht, sich bei Workspace anzumelden, kann es möglicherweise nicht geladen werden, wenn die Person keine Workspace-Berechtigungen hat.

   Melden Sie sich von der anderen Formularanwendung ab und melden Sie sich dann bei Workspace an.

1. Bei HTML-Formularen, die Prozesseigenschaften im Design verwenden, wird bei der Wiedergabe in AEM Forms Workspace die Schaltfläche „Senden“ innerhalb des Formulars angezeigt.

   Wenn Sie beim Entwerfen von Formularen Prozesseigenschaften verwenden, wird im Formular eine Schaltfläche „Senden“ hinzugefügt. Wenn die Schaltfläche „Senden“ in AEM Forms Workspace als PDF gerendert wird, ist sie für den Endbenutzer bzw. die Endbenutzerin nicht sichtbar. Beim Rendern als HTML-Formular in AEM Forms Workspace ist die Schaltfläche „Senden“ jedoch für den Endbenutzer bzw. die Endbenutzerin sichtbar. Durch Klicken auf diese „Senden“ Schaltfläche im Formular wird keine Aktion ausgelöst. Durch Klicken auf die Schaltfläche „Senden“ unten in AEM Forms Workspace, außerhalb des Formulars, wird die Aufgabe abgeschlossen.
