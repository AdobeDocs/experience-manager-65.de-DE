---
title: Erstellen und Zuweisen von Aktivierungsressourcen
seo-title: Erstellen und Zuweisen von Aktivierungsressourcen
description: Aktivierungsressourcen hinzufügen
seo-description: Aktivierungsressourcen hinzufügen
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 78908a9c-a260-44ff-ad1e-baa6d78ae399
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 7%

---

# Erstellen und Zuweisen von Aktivierungsressourcen {#create-and-assign-enablement-resources}

## Hinzufügen einer Aktivierungsressource {#add-an-enablement-resource}

So fügen Sie der neuen Community-Site eine Aktivierungsressource hinzu:

* Melden Sie sich als Systemadministrator auf der Autoreninstanz an:
   * Beispiel: [http://localhost:4502/](http://localhost:4503/)
* Wählen Sie in der globalen Navigation **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]** aus.

   ![resources](assets/resources.png)

   ![enable-resource](assets/enablement-resource.png)
* Wählen Sie die Community-Site aus, zu der Aktivierungsressourcen hinzugefügt werden:
   * Wählen Sie **[!UICONTROL Aktivierungs-Tutorial]** aus.
* Wählen Sie im Menü **[!UICONTROL Erstellen]** aus.
* Wählen Sie **[!UICONTROL Resource]** aus.

![create-resource](assets/create-enablement-resource.png)

### Grundlegende Informationen {#basic-info}

Füllen Sie die grundlegenden Informationen für die Ressource aus:

* **[!UICONTROL Site-Name]**

   Auf den Namen der ausgewählten Community-Site setzen: Tutorial zur Aktivierung

* **[!UICONTROL Resource Name&amp;ast;]**

   Skiunterricht 1

* **[!UICONTROL Tags]**

   Tutorial: Sport/Skifahren

* **[!UICONTROL Im Katalog anzeigen]**

   Setzen Sie es auf **On**.

* **[!UICONTROL Beschreibung]**

   Schneeschlitt für Anfänger.

* **[!UICONTROL Bild hinzufügen]**

   Fügen Sie dem Mitglied in der Ansicht &quot;Assignments&quot;ein Bild hinzu, das die Ressource darstellt.

   ![basic-info](assets/basic-info.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Inhalt hinzufügen {#add-content}

Es wird zwar so angezeigt, als ob mehrere Ressourcen ausgewählt sein könnten, aber nur eine ist zulässig.

Wählen Sie `'+' icon` in der oberen rechten Ecke aus, um mit der Auswahl der Ressource zu beginnen, indem Sie die Quelle identifizieren.

![add-content](assets/add-content.png)

![upload-resource](assets/upload-resource.png)

Eine Ressource hochladen. Wenn eine Videoressource vorhanden ist, laden Sie entweder ein benutzerdefiniertes Bild hoch, das vor der Videowiedergabe angezeigt werden soll, oder lassen Sie zu, dass eine Miniaturansicht aus dem Video generiert wird (es kann einige Minuten dauern - es ist nicht erforderlich zu warten).

![upload-video](assets/upload-video.png)

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Einstellungen {#settings}

* **[!UICONTROL Einstellungen für Social Media]**

   Behalten Sie die Standarderstellung für die Kommentierung und Bewertung von Aktivierungsressourcen durch die Lernenden bei.

* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum ausgewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.

* **[!UICONTROL Ressourcen-Autor]**

   *(Optional)* Lassen Sie das Feld leer.

* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus  `Quinn Harper`.

* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* Lassen Sie das Feld leer.

   **Hinweis**: Wenn Benutzer oder Gruppen nicht sichtbar sind, vergewissern Sie sich, dass sie zur  `Community Enable Members` Gruppe hinzugefügt und in der Veröffentlichungsinstanz  ** gespeichert wurden.

   ![enable-settings](assets/enablement-settings.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Zuweisungen {#assignments}

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Lassen Sie die Einstellung deaktiviert, da diese Aktivierungsressource einem Lernpfad hinzugefügt wird. Wenn ein Lernender der einzelnen Aktivierungsressource sowie einem learningPath mit der Aktivierungsressource zugewiesen wird, wird der Lernende der Aktivierungsressource zweimal zugewiesen.

   ![add-assignments](assets/add-assignments.png)

* Wählen Sie **[!UICONTROL Erstellen]**

   ![create-resource](assets/create-resource.png)

Die erfolgreiche Erstellung der Ressource kehrt zur Ressourcenkonsole zurück, wobei die neu erstellte Ressource ausgewählt ist. In dieser Konsole können Sie Inhalte veröffentlichen, Lernende hinzufügen und andere Einstellungen ändern.

Um eine neue Version der Aktivierungsressource hochzuladen, wird empfohlen, eine neue Ressource zu erstellen, dann die Registrierung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version zu registrieren.

### Ressource {#publish-the-resource} veröffentlichen

Damit die Teilnehmer die zugewiesenen Ressourcen sehen können, müssen sie veröffentlicht werden:

* Wählen Sie das Welt-Symbol `Publish` aus.

Die Aktivierung wird mit einer Erfolgsmeldung bestätigt:

![publish-resource](assets/publish-resource.png)

## Eine zweite Aktivierungsressource {#add-a-second-enablement-resource} hinzufügen

Wiederholen Sie die obigen Schritte, um eine zweite zugehörige Aktivierungsressource zu erstellen und zu veröffentlichen, aus der ein Lernpfad erstellt wird.

![add-resource](assets/add-resource.png)

**** Veröffentlichen Sie die zweite Ressource.

Kehren Sie zur Liste des Tutorials zur Aktivierung der Ressourcen zurück.

*Hinweis: Wenn beide Ressourcen nicht sichtbar sind, aktualisieren Sie die Seite.*

![refresh-resource](assets/refresh-resource.png)

## Lernpfad hinzufügen {#add-a-learning-path}

Ein Lernpfad ist eine logische Gruppierung der Aktivierungsressourcen, die einen Kurs bilden.

* Wählen Sie in der Ressourcenkonsole `+ Create` aus.
* Wählen Sie **[!UICONTROL Lernpfad]**

![add-learning-path](assets/add-learning-path.png)

Fügen Sie die **[!UICONTROL Basic Info]** hinzu:

* **[!UICONTROL Lernpfad-Name]**

   Skiunterricht

* **[!UICONTROL Tags]**

   Tutorial: Skiing

* **[!UICONTROL Im Katalog anzeigen]**

   Nicht aktivieren

* **[!UICONTROL Bild hochladen]**

   Zum Darstellen des Lernpfads in der Ressourcenkonsole.

   ![learningPath-basic](assets/learningpath-basic.png)

* Wählen Sie **[!UICONTROL Weiter]** aus.

Überspringen Sie das nächste Bedienfeld, da es keine erforderlichen Lernpfade zum Hinzufügen gibt.

* Wählen Sie **[!UICONTROL Weiter]** aus

Im Bereich Ressourcen hinzufügen :

* Wählen Sie `+ Add Resources` aus, um die 2 Ressourcen für Ski-Läsionen auszuwählen, die zum Lernpfad hinzugefügt werden sollen.

   Hinweis: Es können nur **veröffentlichte** Ressourcen ausgewählt werden.

>[!NOTE]
>
>Sie können nur die Ressourcen auswählen, die auf derselben Ebene wie der Lernpfad verfügbar sind. Beispielsweise sind für einen in einer Gruppe erstellten Lernpfad nur die Ressourcen auf Gruppenebene verfügbar. für einen Lernpfad, der auf einer Community-Site erstellt wurde, stehen die Ressourcen auf dieser Site zum Hinzufügen zum Lernpfad zur Verfügung.

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

   ![Lernpfad](assets/learningpath-add.png)

   ![create-learning-path](assets/create-learningpath.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

   ![learningPath-settings](assets/learningpath-settings.png)

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Wählen Sie im Pulldown-Menü die Gruppe `Community Ski Class` aus, der die Mitglieder `Riley Taylor` und `Sidney Croft.` angehören sollen

* **[!UICONTROL Lernpfad Kontakt&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus  `Quinn Harper`.

* Wählen Sie **[!UICONTROL Erstellen]**.

   ![learningPath-info](assets/learningpath-info.png)

Bei erfolgreicher Erstellung des Lernpfads wird die Konsole Ressourcen mit dem neu erstellten Lernpfad ausgewählt. In dieser Konsole können Sie Inhalte veröffentlichen, Lernende hinzufügen und andere Einstellungen ändern.

**** Veröffentlichen Sie den Lernpfad.
