---
title: Einrichten und Zuweisen von Aktivierungsressourcen
seo-title: Einrichten und Zuweisen von Aktivierungsressourcen
description: hinzufügen
seo-description: hinzufügen
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 7%

---


# Aktivierungsressourcen {#create-and-assign-enablement-resources} erstellen und zuweisen

## hinzufügen einer Aktivierungsressource {#add-an-enablement-resource}

So fügen Sie der neuen Community-Site eine Aktivierungsressource hinzu:

* Melden Sie sich als Systemadministrator bei der Autoreninstanz an:
   * Beispiel: [http://localhost:4502/](http://localhost:4503/)
* Wählen Sie in der globalen Navigation **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]**

   ![resources](assets/resources.png)

   ![enable-resource](assets/enablement-resource.png)
* Wählen Sie die Community-Site aus, der die Aktivierungsressourcen hinzugefügt werden:
   * Wählen Sie **[!UICONTROL Aktivierungsübung]**.
* Wählen Sie im Menü **[!UICONTROL Erstellen]**.
* Wählen Sie **[!UICONTROL Ressource]**.

![create-resource](assets/create-enablement-resource.png)

### Grundlegende Informationen {#basic-info}

Füllen Sie die grundlegenden Informationen für die Ressource aus:

* **[!UICONTROL Site-Name]**

   Auf den Namen der ausgewählten Community-Site setzen: Übungen zur Aktivierung

* **[!UICONTROL Ressourcenname&amp;ast;]**

   Skiunterricht 1

* **[!UICONTROL Tags]**

   Übung: Sport/Skifahren

* **[!UICONTROL Im Katalog anzeigen]**

   Stellen Sie sie auf **Ein** ein.

* **[!UICONTROL Beschreibung]**

   Schneeschlitten für Anfänger.

* **[!UICONTROL Bild hinzufügen]**

   hinzufügen Sie ein Bild, das die Ressource für das Mitglied in der Ansicht &quot;Zuweisungen&quot;darstellt.

   ![basic-info](assets/basic-info.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Inhalt hinzufügen {#add-content}

Es wird zwar so angezeigt, als ob mehrere Ressourcen ausgewählt wären, es ist jedoch nur eine zulässig.

Wählen Sie `'+' icon` in der oberen rechten Ecke aus, um mit der Auswahl der Ressource zu beginnen, indem Sie die Quelle angeben.

![add-content](assets/add-content.png)

![upload-resource](assets/upload-resource.png)

Eine Ressource hochladen. Bei einer Videoressource können Sie entweder ein benutzerdefiniertes Beginn hochladen, das vor der Videowiedergabe angezeigt wird, oder eine Miniaturansicht aus dem Video generieren lassen (dies kann einige Minuten dauern - es ist nicht erforderlich zu warten).

![upload-video](assets/upload-video.png)

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Einstellungen {#settings}

* **[!UICONTROL Einstellungen für Social Media]**

   Lassen Sie die Standardeinstellungen so, dass die Kommentierung und Bewertung der Aktivierungsressourcen durch die Lernenden möglich ist.

* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum gewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.

* **[!UICONTROL Ressourcen-Autor]**

   *(Optional)* Lassen Sie das Feld leer.

* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus  `Quinn Harper`.

* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* Lassen Sie das Feld leer.

   **Hinweis**: Wenn Benutzer oder Gruppen nicht sichtbar sind, überprüfen Sie, ob sie der  `Community Enable Members` Gruppe hinzugefügt und in der Veröffentlichungsinstanz  ** gespeichert wurden.

   ![enable-settings](assets/enablement-settings.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Zuweisungen {#assignments}

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Lassen Sie die Einstellung deaktiviert, da diese Aktivierungsressource einem Lernpfad hinzugefügt wird. Wenn ein Lernender der einzelnen Aktivierungsressource sowie einem Lernpfad mit der Aktivierungsressource zugewiesen ist, wird der Lernende der Aktivierungsressource zweimal zugewiesen.

   ![add-assignments](assets/add-assignments.png)

* Wählen Sie **[!UICONTROL Erstellen]**

   ![create-resource](assets/create-resource.png)

Die erfolgreiche Erstellung der Ressource kehrt bei Auswahl der neu erstellten Ressource zur Ressourcenkonsole zurück. Über diese Konsole können Sie andere Einstellungen veröffentlichen, hinzufügen und ändern.

Um eine neue Version der Ressource für die Aktivierung hochzuladen, wird empfohlen, eine neue Ressource zu erstellen und dann die Anmeldung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version einzutragen.

### Ressource {#publish-the-resource} veröffentlichen

Bevor die Lernenden die zugewiesenen Ressourcen sehen können, müssen sie veröffentlicht werden:

* Wählen Sie das Symbol Welt `Publish`

Die Aktivierung wird mit einer Erfolgsmeldung bestätigt:

![publish-resource](assets/publish-resource.png)

## hinzufügen einer zweiten Aktivierungsressource {#add-a-second-enablement-resource}

Wiederholen Sie die oben stehenden Schritte, um eine zweite zugehörige Aktivierungsressource zu erstellen und zu veröffentlichen, aus der ein Lernpfad erstellt wird.

![add-resource](assets/add-resource.png)

**Die zweite Ressource** veröffentlichen.

Kehren Sie zur Liste der Ressourcen des Tutorials zur Aktivierung zurück.

*Hinweis: Wenn beide Ressourcen nicht sichtbar sind, aktualisieren Sie die Seite.*

![refresh-resource](assets/refresh-resource.png)

## hinzufügen eines Lernpfads {#add-a-learning-path}

Ein Lernpfad ist eine logische Gruppierung von Ressourcen zur Aktivierung, die einen Kurs bilden.

* Wählen Sie in der Ressourcenkonsole `+ Create`
* Wählen Sie **[!UICONTROL Lernpfad]**

![add-learning-path](assets/add-learning-path.png)

hinzufügen Sie die **[!UICONTROL Basisinformationen]**:

* **[!UICONTROL Lernpfad-Name]**

   Skiunterricht

* **[!UICONTROL Tags]**

   Übung: Skifahren

* **[!UICONTROL Im Katalog anzeigen]**

   Nicht aktivieren

* **[!UICONTROL Hochladen eines Bildes]**

   Zum Darstellen des Lernpfads in der Ressourcenkonsole.

   ![learn-path-basic](assets/learningpath-basic.png)

* Wählen Sie **[!UICONTROL Weiter]** aus.

Überspringen Sie das nächste Bedienfeld, da es keine erforderlichen Lernpfade zum Hinzufügen gibt.

* Wählen Sie **[!UICONTROL Weiter]** aus

Im Bereich Hinzufügen Ressourcen:

* Wählen Sie `+ Add Resources` aus, um die 2 Skilesenressourcen auszuwählen, die dem Lernpfad hinzugefügt werden sollen.

   Hinweis: Nur **published**-Ressourcen können ausgewählt werden.

>[!NOTE]
>
>Sie können die verfügbaren Ressourcen nur auf derselben Ebene wie der Lernpfad auswählen. Beispielsweise stehen für einen Lernpfad, der in einer Gruppe erstellt wird, nur Ressourcen auf Gruppenebene zur Verfügung; für einen Lernpfad, der auf einer Community-Site erstellt wurde, stehen die Ressourcen auf dieser Site zum Hinzufügen zum Lernpfad zur Verfügung.

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

   ![Lernpfad](assets/learningpath-add.png)

   ![create-learn-path](assets/create-learningpath.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

   ![learn-path-settings](assets/learningpath-settings.png)

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Verwenden Sie das Pulldown-Menü, um die Gruppe `Community Ski Class` auszuwählen, zu der die Mitglieder `Riley Taylor` und `Sidney Croft.` gehören sollten

* **[!UICONTROL Lernpfad Kontakt&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus  `Quinn Harper`.

* Wählen Sie **[!UICONTROL Erstellen]**.

   ![learn-path-info](assets/learningpath-info.png)

Bei erfolgreicher Erstellung des Lernpfads wird die Ressourcenkonsole mit dem neu erstellten Lernpfad ausgewählt. Über diese Konsole können Sie andere Einstellungen veröffentlichen, hinzufügen und ändern.

**Veröffentlichen** Sie den Lernpfad.

