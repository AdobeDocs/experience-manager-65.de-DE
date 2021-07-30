---
title: Designanpassung
seo-title: Designanpassung
description: Anpassen des Themas an Ihre AEM Forms-App.
seo-description: Anpassen des Themas an Ihre AEM Forms-App.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: 9b8c5933-b783-48f9-b463-15a01e06ee98
source-git-commit: 6bc228866aca785ec768daefb73970fc24568ef0
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 58%

---

# Designanpassung {#theme-customization}

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben bzw. Startpunkten ändern. Folgendes Beispiel enthält hierzu Anweisungen:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Farbverlauf Hintergrundfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * Öffnen Sie für iOS `Capture.xcodeproj` in Xcode.
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * Öffnen Sie für Windows `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * Navigieren Sie in Xcode zum Ordner **Capture > www > wsmobile > js > runtime > templates** .
   * Navigieren Sie in Eclipse zum Ordner **assets > www > wsmobile > js > runtime > templates** .
   * Navigieren Sie in Visual Studio zum Ordner **MWSWindows > www > wsmobile > js > runtime > templates** .

1. Öffnen Sie die Datei `template.html` zur Bearbeitung.
1. Suchen Sie die folgende Zeichenfolge:

   ```jsp
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Ersetzen Sie sie durch `<%`.

1. Suchen Sie den folgenden Code in der Datei `template.html`:

   ```jsp
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Geben Sie die folgende Zeile ein und speichern Sie die Datei.

   ```jsp
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigieren Sie zum Ordner „css“.

   * Navigieren Sie in Xcode zu **Capture > www > wsmobile > css**.
   * Navigieren Sie in Eclipse zu **assets > www > wsmobile > css**.
   * Navigieren Sie in Visual Studio zu **MWSWindows > www > wsmobile > css**.

1. Öffnen Sie die Datei `_style.css` zur Bearbeitung.
1. Ändern Sie für das Hintergrundbild `#323232` in `#fff`.
1. Speichern Sie die Änderungen und schließen Sie die Datei `_style.css`.
1. Öffnen Sie die AEM Forms-App.

   Die AEM Forms-App zeigt jetzt Anweisungen anstelle einer Beschreibung an.
