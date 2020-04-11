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
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Gestenanpassung {#gesture-customization}

Sie können die Gesten der AEM Forms-App anpassen, um eine unterschiedliche Methode zur Interaktion mit der App bereitzustellen. Beispielsweise können Sie neue Gesten zum Öffnen oder Schließen einer Aufgabe bzw. eines Startpunkts hinzufügen.

## So passen Sie Gesten in der AEM Forms-App an {#to-customize-gestures-in-aem-forms-app}

In der AEM Forms-App wird durch das Wischen nach links eine neue Aufgabe bzw. ein neuer Startpunkt geöffnet, während beim Wischen nach rechts nichts passiert. Im folgenden Beispiel wird beschrieben, wie Sie eine neue Aufgabe oder einen neuen Startpunkt öffnen, wenn Sie die Gesten zum Wischen nach rechts in der AEM Forms-App ausführen.

1. Öffnen Sie Ihr Projekt.

   * For iOS, open `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * For Windows, open `MWSWindows.sln` in Visual Studio.

1. Navigate to the views folder and open the `task.js` file for editing.

   * In Xcode, navigate to the **Capture > www > wsmobile > js > runtime > views** folder.
   * In Eclipse, navigate to the **assets > www > wsmobile > js > runtime > views** folder.
   * In Visual Studio, navigate to the **MWSWindows > www > wsmobile > js > runtime > views** folder.
   >[!NOTE]
   >
   >Die Datei „task.js“ enthält die Backbone-Ansicht, die mit allen Aufgaben oder Startpunkten in der Aufgaben- oder Startpunktliste verknüpft ist.

1. Suchen Sie in der Datei `task.js` nach der Ereigniseigenschaft der Ansicht.

   Die Eigenschaft &quot;Ereignisses&quot;ist eine Zuordnung mit jedem Eintrag im Format:

   `"EventName Selector": "Function"`

   When you trigger a Javascript event named `EventName`on an HTML element specified by `Selector`, the `Function`is called.

1. Suchen

   * &quot;tap .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;tap .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;tap .Aufgabe-content&quot;: &quot;onTaskClick&quot;,

      &quot;tap .last_empty_div&quot; : &quot;onTaskClick&quot;,
   und ersetzen Sie diese durch

   * &quot;swipe .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .Aufgabe-content&quot;: &quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot; : &quot;onTaskClick&quot;,


1. Save and close the `task.js` file.
1. Erstellen Sie die AEM Forms-App und führen Sie sie aus. Jetzt können Sie eine Aufgabe mit einem Wischen nach links und rechts öffnen.

Auf ähnliche Weise können Sie Änderungen in anderen Ansichten für verschiedene Kombinationen von Gesten, HTML-Elementen und Funktionen vornehmen.
