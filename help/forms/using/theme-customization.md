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
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Designanpassung {#theme-customization}

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben bzw. Startpunkten ändern. Folgendes Beispiel enthält hierzu Anweisungen:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Farbverlauf Hintergrundfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * For iOS, open `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * For Windows, open `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * In Xcode, navigate to the **Capture > www > wsmobile > js > runtime > templates** folder.
   * In Eclipse, navigate to the **assets > www > wsmobile > js > runtime > templates** folder.
   * In Visual Studio, navigate to the **MWSWindows > www > wsmobile > js > runtime > templates** folder.

1. Open the `template.html` file for editing.
1. Suchen Sie die folgende Zeichenfolge:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Ersetzen Sie sie durch `<%`.

1. Suchen Sie den folgenden Code in der Datei `template.html`:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Geben Sie die folgende Zeile ein und speichern Sie die Datei.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigieren Sie zum Ordner „css“.

   * In Xcode, navigate to **Capture > www > wsmobile > css**.
   * In Eclipse, navigate to **assets > www > wsmobile > css**.
   * In Visual Studio, navigate to **MWSWindows > www > wsmobile > css**.

1. Open the `_style.css` file for editing.
1. For Background image, change `#323232` to `#fff`.
1. Save the changes and close `_style.css` file.
1. Öffnen Sie die AEM Forms-App.

   Die AEM Forms-App zeigt jetzt Anweisungen anstelle einer Beschreibung an.
