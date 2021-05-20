---
title: Gestenanpassung
seo-title: Gestenanpassung
description: Anpassen der Gesten in Ihrer AEM Forms-App
seo-description: Anpassen der Gesten in Ihrer AEM Forms-App
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 6debb1a7-7889-4fdd-87c7-ecb87cc0b1f5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 46%

---

# Gestenanpassung {#gesture-customization}

Sie können die Gesten der AEM Forms-App anpassen, um eine unterschiedliche Methode zur Interaktion mit der App bereitzustellen. Beispielsweise können Sie neue Gesten zum Öffnen oder Schließen einer Aufgabe bzw. eines Startpunkts hinzufügen.

## So passen Sie Gesten in der AEM Forms-App an {#to-customize-gestures-in-aem-forms-app}

In der AEM Forms-App wird durch das Wischen nach links eine neue Aufgabe bzw. ein neuer Startpunkt geöffnet, während beim Wischen nach rechts nichts passiert. Im folgenden Beispiel werden Schritte zum Öffnen einer neuen Aufgabe oder eines neuen Startpunkts zum Ausführen der Wischgesten nach rechts in der AEM Forms-App beschrieben.

1. Öffnen Sie Ihr Projekt.

   * Öffnen Sie für iOS `Capture.xcodeproj` in Xcode.
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * Öffnen Sie für Windows `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner &quot;views&quot;und öffnen Sie die Datei `task.js` zur Bearbeitung.

   * Navigieren Sie in Xcode zum Ordner **Capture > www > wsmobile > js > runtime > views** .
   * Navigieren Sie in Eclipse zum Ordner **assets > www > wsmobile > js > runtime > views** .
   * Navigieren Sie in Visual Studio zum Ordner **MWSWindows > www > wsmobile > js > runtime > views** .

   >[!NOTE]
   >
   >Die Datei „task.js“ enthält die Backbone-Ansicht, die mit allen Aufgaben oder Startpunkten in der Aufgaben- oder Startpunktliste verknüpft ist.

1. Suchen Sie in der Datei `task.js` nach der Ereigniseigenschaft der Ansicht.

   Die Ereigniseigenschaft ist eine Zuordnung mit jedem Eintrag im folgenden Format:

   `"EventName Selector": "Function"`

   Wenn Sie ein JavaScript-Ereignis mit dem Namen `EventName`für ein von `Selector` angegebenes HTML-Element Trigger haben, wird `Function`aufgerufen.

1. Suchen

   * &quot;Tippen Sie auf .taskContentArea&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .taskOpenArea&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .task-content&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .last_empty_div : &quot;onTaskClick&quot;,
   und ersetzen Sie diese durch

   * &quot;swipe .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .task-content&quot;: &quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot;: &quot;onTaskClick&quot;,


1. Speichern und schließen Sie die Datei `task.js`.
1. Erstellen Sie die AEM Forms-App und führen Sie sie aus. Jetzt können Sie eine Aufgabe mit einem Wischen nach links und rechts öffnen.

Auf ähnliche Weise können Sie Änderungen in anderen Ansichten für verschiedene Kombinationen von Gesten, HTML-Elementen und Funktionen vornehmen.
