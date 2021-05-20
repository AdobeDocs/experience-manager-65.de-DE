---
title: Fehlerbehebung bei Richtlinien für AEM Forms Workspace
seo-title: Fehlerbehebung bei Richtlinien für AEM Forms Workspace
description: Aktivieren Sie Protokolle und verwenden Sie Debugger im Browser, um AEM Forms Workspace-Fehler zu beheben.
seo-description: Aktivieren Sie Protokolle und verwenden Sie Debugger im Browser, um AEM Forms Workspace-Fehler zu beheben.
uuid: 07b8c8ed-f1ff-4be5-8005-251ff7b2ac85
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 5dae9ed9-77a3-44f5-a94d-ca5c355c8730
exl-id: a054b60a-5e89-4c98-87bc-35669988d160
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 81%

---

# Fehlerbehebung bei Richtlinien für AEM Forms Workspace {#troubleshooting-guidelines-for-aem-forms-workspace}

Dieser Artikel erläutert, wie Sie AEM Forms Workspace debuggen, indem Sie die Protokollierung aktivieren und den Debugger in einem Browser verwenden. Darüber hinaus werden einige allgemeine Fragen, die bei der Verwendung von AEM Forms Workspace auftreten können, und ihre Umgehungslösungen behandelt.

## AEM Forms Workspace-Paket kann nicht installiert werden  {#unable-to-install-aem-forms-workspace-package}

Nach der Installation des Patches öffnen Sie die AEM Forms Workspace-App. Wenn der Fehler &quot;Keine Ressource gefunden&quot;auftritt, öffnen Sie den CRX Package Manager und installieren Sie das Paket `adobe-lc-workspace-pkg-<version>.zip` erneut.

Wenn beim Installieren des Pakets ein Fehler `javax.jcr.nodetype.ConstraintViolationException: OakConstraint0025: Authorizable property rep:authorizableId may not be removed` auftritt, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei CRX DE Lite an. Die Standard-URL lautet `https://[localhost]:'port'/lc/crx/de/index.jsp` .
1. Löschen Sie den folgenden Knoten:

   `/home/groups/P/PERM_WORKSPACE_USER`

1. Navigieren Sie zu Package Manager. Die Standardeinstellung ist `https://[localhost]:'port'/lc/crx/packmgr/index.jsp.`
1. Suchen und installieren Sie das Paket `adobe-lc-workspace-pkg-[version].zip` .
1. Starten Sie den Anwendungsserver neu.

## Protokollierung für AEM Forms Workspace  {#aem-forms-workspace-nbsp-logging}

Sie können Protokolle auf verschiedenen Ebenen generieren, um eine optimale Fehlerbehebung zu ermöglichen. Beispielsweise hilft in einer komplexen Anwendung die Protokollierung auf der Komponentenebene beim Debugging und der Fehlerbehebung bestimmter Komponenten.

In AEM Forms Workspace:

* Um die Protokollinformationen zu einer bestimmten Komponentendatei zu erhalten, hängen Sie `/log/<ComponentFile>/<LogLevel>` an die URL an und drücken Sie die Taste `Enter`. Alle Protokollinformationen für die Komponentendatei auf der angegebenen Protokollebene werden in der Konsole ausgegeben.

* Um Protokollinformationen zu allen Komponentendateien zu erhalten, hängen Sie `/log/all/trace` an die URL an und drücken Sie `Enter`.

* Protokollformat: `<Component file> <Date>:<Time>: <Log Level> : <Log Message>`

>[!NOTE]
>
>Standardmäßig wird die Protokollebene aller Komponenten auf INFO festgelegt.

* Die vom Benutzer festgelegte Protokollebene gilt nur für diese Browsersitzung. Wenn der Benutzer die Seite aktualisiert, wird die Protokollebene auf den anfänglichen Wert für alle Komponenten festgelegt.

### Liste von Komponentendateien in AEM Forms Workspace  {#list-of-component-files-in-nbsp-aem-forms-workspace}

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

### In AEM Forms Workspace verfügbare Protokollebenen  {#log-levels-available-in-nbsp-aem-forms-workspace}

* FATAL
* ERROR
* WARN
* INFO
* DEBUG
* TRACE
* AUS

## Debugging-Information für Browser {#debugging-information-for-browsers}

Skripten und Stile können in verschiedenen Browsern debuggt werden.

* **Debugging in IE**: Informationen zum Debugging von AEM Forms Workspace in IE finden Sie unter:  [https://msdn.microsoft.com/en-us/library/hh772704(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/hh772704(v=vs.85).aspx).

* **Debugging in Chrome**: Um den Debugger in Chrome zu öffnen, verwenden Sie den Tastaturbefehl: Strg+Umschalt+I. Weitere Informationen finden Sie unter:  [https://developer.chrome.com/extensions/tut_debugging.html](https://developer.chrome.com/extensions/tut_debugging.html).

* **Debugging in Firefox**: Zum Debugging von Skripten und Stilen in Firefox stehen mehrere Add-ons zur Verfügung. Firebug ist beispielsweise eines dieser Debugging-Hilfsprogramme ([https://getfirebug.com](https://getfirebug.com)).

## Häufig gestellte Fragen {#faqs}

1. PDF-Formular wird in Google Chrome nicht wiedergegeben oder gesendet.

   1. Installieren Sie das Adobe® Reader®-Plug-In.
   1. Öffnen Sie in Chrome chrome://plugins, um verfügbare Plug-Ins anzuzeigen.
   1. Deaktivieren Sie das Chrome-Plug-In PDF Viewer und aktivieren Sie das Adobe Reader-Plug-In.

1. SWF-Formular oder Guide wird in Google-Chrome nicht angezeigt.

   1. Öffnen Sie in Chrome chrome://plugins, um verfügbare Plug-Ins anzuzeigen.
   1. Suchen Sie nach Informationen für das Adobe Flash® Player-Plug-In.
   1. Deaktivieren Sie PepperFlash unter dem Adobe Flash Player-Plug-In.

1. Ich habe AEM Forms Workspace angepasst, aber ich kann die Änderungen nicht sehen.

   Löschen Sie den Cache des Browsers und greifen Sie dann auf AEM Forms Workspace zu.

1. Was muss der Benutzer tun, damit das Formular in HTML wiedergegeben wird, wenn es auf dem Desktop geöffnet wird?

   Wählen Sie bei der Verwendung von Workbench im Schritt zum Zuweisen der Aufgabe das HTML-Optionsfeld für das Standardprofil aus.

1. Anlage wird nicht angezeigt, wenn darauf geklickt wird.

   Um Anlagen anzuzeigen, aktivieren Sie Popups im Browser.

1. Ein Benutzer ist bei einer Forms-Anwendung angemeldet. Wenn der Benutzer versucht, sich bei Workspace anzumelden, wird es möglicherweise nicht geladen, wenn der Benutzer über keine Workspace-Berechtigungen verfügt.

   Melden Sie sich von der anderen Forms-Anwendung ab und melden Sie sich dann bei Workspace an.

1. Bei HTML-Formularen, die Prozesseigenschaften im Design verwenden, wird bei der Wiedergabe in AEM Forms Workspace die Schaltfläche &quot;Senden“ innerhalb des Formulars angezeigt.

   Wenn Sie ein Formular mit Prozesseigenschaften entwerfen, wird die Schaltfläche „Senden“ innerhalb des Formulars eingefügt. Bei der Wiedergabe als PDF in AEM Forms Workspace ist die Schaltfläche „Senden“ für den Endbenutzer nicht sichtbar. Wird in AEM Forms Workspace jedoch als HTML-Formular wiedergegeben, ist die Schaltfläche „Senden“ für den Endbenutzer sichtbar. Durch Klicken auf die Schaltfläche „Senden“ im Formular wird keine Aktion ausgelöst. Durch Klicken auf die Schaltfläche „Senden“ unten im AEM Forms Workspace, außerhalb des Formulars, wird die Aufgabe abgeschlossen.
