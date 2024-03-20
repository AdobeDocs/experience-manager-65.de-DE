---
title: Design-Anpassung
description: Erfahren Sie, wie Sie das Design der AEM Forms-Anwendung anpassen. Sie können den HTML-Code und die CSS-Datei anpassen, um ein unternehmensspezifisches Erscheinungsbild zu erhalten.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 9b8c5933-b783-48f9-b463-15a01e06ee98
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 73%

---

# Design-Anpassung {#theme-customization}

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben oder Startpunkten ändern. Das folgende Beispiel enthält Anweisungen zum Ändern:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Farbverlauf mit Hintergrundfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * In iOS öffnen Sie `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * In Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * In Xcode navigieren Sie zum Ordner **Capture > www > wsmobile > js > runtime > templates**.
   * In Eclipse navigieren Sie zum Ordner **assets > www > wsmobile > js > runtime > templates**.
   * In Visual Studio navigieren Sie zum Ordner **MWSWindows > www > wsmobile > js > runtime > templates**.

1. Öffnen Sie die Datei „`template.html`“, um sie zu bearbeiten.
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

   * In Xcode navigieren Sie zu **Capture > www > wsmobile > css**.
   * In Eclipse navigieren Sie zu **assets > www > wsmobile > css**.
   * In Visual Studio navigieren Sie zu **MWSWindows > www > wsmobile > css**.

1. Öffnen Sie die Datei „`_style.css`“, um sie zu bearbeiten.
1. Ändern Sie für das Hintergrundbild `#323232` auf `#fff`.
1. Speichern Sie die Änderungen und schließen Sie die Datei `_style.css`.
1. Öffnen Sie die AEM Forms-App.

   Das AEM Forms-Programm zeigt jetzt Anweisungen anstelle von Beschreibungen an.
