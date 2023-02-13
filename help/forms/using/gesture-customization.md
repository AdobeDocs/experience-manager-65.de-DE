---
title: Gestenanpassung
seo-title: Gesture customization
description: Anpassen der Gesten in Ihrer AEM Forms-App
seo-description: Customize the gestures on your AEM Forms app
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 6debb1a7-7889-4fdd-87c7-ecb87cc0b1f5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '296'
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

   Wenn Sie ein Javascript-Ereignis mit dem Namen `EventName` für ein von `Selector` festgelegtes HTML-Element auslösen, wird `Function` aufgerufen.

1. Suchen

   * „tap .taskContentArea“ : „onTaskClick“,

      „tap .taskOpenArea“ : „onTaskClick“,

      „tap .task-content“ : „onTaskClick“,

      „tap .last_empty_div“ : „onTaskClick“,
   und ersetzen Sie diese durch

   * „swipe .taskContentArea“ : „onTaskClick“,

      „swipe .taskOpenArea“ : „onTaskClick“,

      „swipe .task-content“ : „onTaskClick“,

      „swipe .last_empty_div“ : „onTaskClick“,


1. Speichern und schließen Sie die Datei `task.js`.
1. Erstellen Sie die AEM Forms-App und führen Sie sie aus. Jetzt können Sie eine Aufgabe mit einem Wischen nach links und rechts öffnen.

Auf ähnliche Weise können Sie Änderungen in anderen Ansichten für verschiedene Kombinationen von Gesten, HTML-Elementen und Funktionen vornehmen.
