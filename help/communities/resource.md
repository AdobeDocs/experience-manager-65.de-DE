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
source-git-commit: e84c9a99ce9ec0447a5fb3e0ca5ba76b41c888cd
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 7%

---


# Einrichten und Zuweisen von Aktivierungsressourcen {#create-and-assign-enablement-resources}

## hinzufügen einer Aktivierungsressource {#add-an-enablement-resource}

So fügen Sie der neuen Community-Site eine Aktivierungsressource hinzu:

* Melden Sie sich als Systemadministrator bei der Autoreninstanz an:
   * For example, [http://localhost:4502/](http://localhost:4503/)
* Wählen Sie in der globalen Navigation **[!UICONTROL Communities]** > **[!UICONTROL Resources]**

   ![resources](assets/resources.png)

   ![enable-resource](assets/enablement-resource.png)
* Wählen Sie die Community-Site aus, der die Aktivierungsressourcen hinzugefügt werden:
   * Wählen Sie &quot; **[!UICONTROL Aktivierungslehrgang&quot;]**.
* From the menu, select **[!UICONTROL Create]**.
* Select **[!UICONTROL Resource]**.

![create-resource](assets/create-enablement-resource.png)

### Grundlegende Informationen {#basic-info}

Fill in the basic information for the Resource:

* **[!UICONTROL Site-Name]**

   Set to the name of the selected community site: Enablement Tutorial

* **[!UICONTROL Resource Name&amp;ast;]**

   Skiunterricht 1

* **[!UICONTROL Tags]**

   Tutorial: Sports / Skiing

* **[!UICONTROL Im Katalog anzeigen]**

   Stellen Sie es auf **Ein** ein.

* **[!UICONTROL Beschreibung]**

   Sliding on snow for beginners.

* **[!UICONTROL Bild hinzufügen]**

   hinzufügen Sie ein Bild, das die Ressource für das Mitglied in der Ansicht &quot;Zuweisungen&quot;darstellt.

   ![basic-info](assets/basic-info.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Inhalt hinzufügen {#add-content}

While it appears as if multiple Resources might be selected, only one is allowed.

Wählen Sie oben rechts `'+' icon`die Ressource aus, um mit der Auswahl der Quelle zu beginnen.

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

   *(Erforderlich)* Wählen Sie im Pulldown-Menü ein Mitglied aus `Quinn Harper`.

* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* Lassen Sie das Feld leer.

   **Hinweis**: Wenn Benutzer oder Gruppen nicht sichtbar sind, überprüfen Sie, ob sie der `Community Enable Members` Gruppe hinzugefügt und in der Veröffentlichungsinstanz *gespeichert* wurden.

   ![enable-settings](assets/enablement-settings.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

### Zuweisungen {#assignments}

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Lassen Sie die Einstellung deaktiviert, da diese Aktivierungsressource einem Lernpfad hinzugefügt wird. Wenn ein Lernender der einzelnen Aktivierungsressource sowie einem Lernpfad mit der Aktivierungsressource zugewiesen ist, wird der Lernende der Aktivierungsressource zweimal zugewiesen.

   ![add-assignments](assets/add-assignments.png)

* Wählen Sie **[!UICONTROL Erstellen]**

   ![create-resource](assets/create-resource.png)

Die erfolgreiche Erstellung der Ressource kehrt bei Auswahl der neu erstellten Ressource zur Ressourcenkonsole zurück. From this console, it is possible to publish, add learners and change other settings.

Um eine neue Version der Ressource für die Aktivierung hochzuladen, wird empfohlen, eine neue Ressource zu erstellen und dann die Anmeldung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version einzutragen.

### Ressource veröffentlichen {#publish-the-resource}

Bevor die Lernenden die zugewiesenen Ressourcen sehen können, müssen sie veröffentlicht werden:

* Select the world `Publish` icon

Activation is confirmed with a success message:

![publish-resource](assets/publish-resource.png)

## Add a Second Enablement Resource {#add-a-second-enablement-resource}

Repeat the steps above to create and publish a second related enablement resource from which a learning path will be created.

![add-resource](assets/add-resource.png)

**Veröffentlichen** Sie die zweite Ressource.

Kehren Sie zur Liste der Ressourcen des Tutorials zur Aktivierung zurück.

*Hinweis: Wenn beide Ressourcen nicht sichtbar sind, aktualisieren Sie die Seite.*

![refresh-resource](assets/refresh-resource.png)

## hinzufügen Lernpfad {#add-a-learning-path}

Ein Lernpfad ist eine logische Gruppierung von Ressourcen zur Aktivierung, die einen Kurs bilden.

* Wählen Sie in der Ressourcenkonsole `+ Create`
* Lernpfad auswählen ****

![add-learning-path](assets/add-learning-path.png)

hinzufügen der **[!UICONTROL Basisinformationen]**:

* **[!UICONTROL Lernpfad-Name]**

   Skiunterricht

* **[!UICONTROL Tags]**

   Übung: Skifahren

* **[!UICONTROL Im Katalog anzeigen]**

   Nicht aktivieren

* **[!UICONTROL Upload an image]**

   Zum Darstellen des Lernpfads in der Ressourcenkonsole.

   ![learn-path-basic](assets/learningpath-basic.png)

* Wählen Sie **[!UICONTROL Weiter]** aus.

Überspringen Sie das nächste Bedienfeld, da es keine erforderlichen Lernpfade zum Hinzufügen gibt.

* Wählen Sie **[!UICONTROL Weiter]** aus

Im Bereich Hinzufügen Ressourcen:

* Wählen Sie `+ Add Resources` die 2 Skilesenressourcen aus, die Sie dem Lernpfad hinzufügen möchten.

   Hinweis: Nur **veröffentlichte** Ressourcen können ausgewählt werden.

>[!NOTE]
>
>You can only select the resources available at the same level as the learning path. For example, for a learning path created in a group only the group level resources are available; for a learning path created in a community site the resources in that site are available for adding to the learning path.


* Klicken Sie auf **[!UICONTROL Übermitteln]**.

   ![learningpath](assets/learningpath-add.png)

   ![create-learningpath](assets/create-learningpath.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

   ![learningpath-settings](assets/learningpath-settings.png)

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Use the pulldown menu to select the `Community Ski Class` group, which should included members `Riley Taylor` and `Sidney Croft.`

* **[!UICONTROL Lernpfad Contact&amp;ast;]**

   *(Erforderlich)* Wählen Sie im Pulldown-Menü ein Mitglied aus `Quinn Harper`.

* Wählen Sie **[!UICONTROL Erstellen]**.

   ![learningpath-info](assets/learningpath-info.png)

Bei erfolgreicher Erstellung des Lernpfads wird die Ressourcenkonsole mit dem neu erstellten Lernpfad ausgewählt. Über diese Konsole können Sie andere Einstellungen veröffentlichen, hinzufügen und ändern.

**Publish** the learning path.

