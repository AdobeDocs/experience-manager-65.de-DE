---
title: Gestenanpassung
description: Erfahren Sie, wie Sie die Gesten in der AEM Forms-App anpassen. Sie können die Gesten anpassen, um eine individuelle Methode der Interaktion mit der Anwendung bereitzustellen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 6debb1a7-7889-4fdd-87c7-ecb87cc0b1f5
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 100%

---

# Gestenanpassung {#gesture-customization}

Sie können die Gesten der AEM Forms-App anpassen, um eine individuelle Methode der Interaktion mit der App bereitzustellen. Beispielsweise können Sie neue Gesten zum Öffnen oder Schließen einer Aufgabe bzw. eines Startpunkts hinzufügen.

## So passen Sie Gesten in der AEM Forms-App an {#to-customize-gestures-in-aem-forms-app}

In der AEM Forms-App wird durch das Wischen nach links eine neue Aufgabe bzw. ein neuer Startpunkt geöffnet, während beim Wischen nach rechts nichts passiert. Das folgende Beispiel zeigt Schritte zum Öffnen einer neuen Aufgabe oder eines neuen Startpunkts mittels Wischen nach rechts in der AEM Forms-App.

1. Öffnen Sie Ihr Projekt.

   * In iOS öffnen Sie `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * In Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ansichtsordner und öffnen Sie die Datei `task.js` zur Bearbeitung.

   * In Xcode navigieren Sie zum Ordner **Capture > www > wsmobile > js > runtime > views**.
   * In Eclipse navigieren Sie zum Ordner **assets > www > wsmobile > js > runtime > views**.
   * In Visual Studio navigieren Sie zum Ordner **MWSWindows > www > wsmobile > js > runtime > views**.

   >[!NOTE]
   >
   >Die Datei „task.js“ enthält die Backbone-Ansicht, die mit allen Aufgaben oder Startpunkten in der Aufgaben- oder Startpunktliste verknüpft ist.

1. Suchen Sie in der Datei `task.js` nach der Ereigniseigenschaft der Ansicht.

   Die Ereigniseigenschaft ist eine Zuordnung mit jedem Eintrag im folgenden Format:

   `"EventName Selector": "Function"`

   Wenn Sie ein JavaScript-Ereignis mit dem Namen `EventName` auf einem durch `Selector` angegebenen HTML-Element auslösen, wird die `Function` aufgerufen.

1. Suchen

   * &quot;select .taskContentArea&quot; : &quot;onTaskClick&quot;,

     &quot;select .taskOpenArea&quot; : &quot;onTaskClick&quot;,

     &quot;select .task-content&quot; : &quot;onTaskClick&quot;,

     &quot;select .last_empty_div&quot; : &quot;onTaskClick&quot;,

   und ersetzen Sie diese durch

   * „swipe .taskContentArea“ : „onTaskClick“,

     „swipe .taskOpenArea“ : „onTaskClick“,

     „swipe .task-content“ : „onTaskClick“,

     „swipe .last_empty_div“ : „onTaskClick“,

1. Speichern und schließen Sie die Datei `task.js`.
1. Erstellen Sie die AEM Forms-App und führen Sie sie aus. Jetzt können Sie eine Aufgabe mit einem Wischen nach links und rechts öffnen.

Auf ähnliche Weise können Sie Änderungen in anderen Ansichten für verschiedene Kombinationen von Gesten, HTML-Elementen und Funktionen vornehmen.
