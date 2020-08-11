---
title: Aktivierungsressourcen-Konsole
seo-title: Aktivierungsressourcen-Konsole
description: The Resources console is where Enablement Managers create, manage, and assign resources to members of an enablement community site
seo-description: The Resources console is where Enablement Managers create, manage, and assign resources to members of an enablement community site
uuid: 52445b39-c339-4b39-8004-eb36de99bced
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1ef15e76-fe7c-4ced-a20d-c0a9385e3ee4
translation-type: tm+mt
source-git-commit: 4e2fa3b0a64ae2e959dad85e3a1bc4a1027a2eef
workflow-type: tm+mt
source-wordcount: '2979'
ht-degree: 6%

---


# Aktivierungsressourcen-Konsole {#enablement-resources-console}

For AEM Communities, the Resources console is where [Enablement Managers](users.md) create, manage and assign resources to members of an enablement community site.

## Voraussetzungen {#requirements}

Before adding enablement resources for a community site, the AEM instances must be properly configured, including:

* SCORM
* FFmpeg

For details, see [Configuring Enablement](enablement.md).

>[!CAUTION]
>
>If SCORM is installed after community site creation, any enablement resources present before SCORM is installed must be recreated.



>[!NOTE]
>
>Mit der Veröffentlichung von [AEM 6.3](deploy-communities.md#latestfeaturepack) und den entsprechenden Communities Feature Packs [AEM 6.2 FP3](deploy-communities.md#latestfeaturepack) und [AEM 6.1 FP7](https://docs.adobe.com/content/docs/en/aem/6-1/deploy/communities.html#Latest Feature Pack) ist für die Aktivierung keine [MySQL-Datenbank](mysql.md)mehr erforderlich.


## Terminologie {#terminology}

### Resource {#resource}

Ressourcen sind unverzichtbar für eine [Aktivierungsgemeinschaft](overview.md#enablement-community). Sie sind die Materialien, die den Mitgliedern zugewiesen werden, damit sie ihre Fähigkeiten verbessern können.

Merkmale einer Ressource:

* Kann vom Typ sein:
   * Bild (JPG, PNG, GIF, BMP)
   * Video (MP4)
   * Flash (SWF)
   * Dokument (PDF)
   * Quiz (SCORM)
* Kann von einem oder mehreren Lernpfaden referenziert werden.

### Lernpfad {#learning-path}

Ein Lernpfad ist ein logischer Satz an Ressourcen für die Aktivierung, die gruppiert werden, um die Zuweisung zu Mitgliedern zu vereinfachen.

### Mitgliedergruppe {#members-group}

Wenn eine Community-Site erstellt wird, wird der Name, der der Site für die URL gegeben wird, bei der Erstellung der [Site-spezifischen Benutzergruppen](users.md) verwendet, die mit unterschiedlichen Berechtigungen für verschiedene Rollen konfiguriert wurden. Diesen automatisch erstellten Gruppen wird das Präfix vorangestellt `Community <site-name>`.

Eine dieser Benutzergruppen ist die `Community <site-name> Members` Gruppe, die in der Umgebung zum Veröffentlichen registrierte Benutzer als Community-Mitglieder identifiziert. Ein Beispiel finden Sie im Tutorial [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md) .

Für [Interaktionsgemeinschaften](overview.md#egagementcommunity)ist es sinnvoll, Site-Besuchern zu erlauben, sich selbst zu registrieren oder die Anmeldung über soziale Netzwerke zu verwenden. Zu diesem Zeitpunkt werden sie automatisch der Mitgliedergruppe hinzugefügt.

Für [Aktivierungsgemeinschaften](overview.md#enablement-community)wird empfohlen, die Site privat zu gestalten. Danach muss ein Administrator Benutzer zur Mitgliedergruppe hinzufügen.

## Zugriff auf die Aktivierungsressourcen einer Community-Site {#accessing-a-community-site-s-enablement-resources}

### Zu Communities-Ressourcen navigieren {#navigate-to-communities-resources}

In der Umgebung &quot;author&quot;zur Konsole &quot;Resources&quot;

* Aus globaler Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]**

   ![enable-sites](assets/enablement-sites.png)

### Community-Site auswählen {#select-a-community-site}

Die Communities-Ressourcen-Konsole zeigt alle Community-Sites an.

Aktivierungsressourcen werden für eine bestimmte Community-Site erstellt, nachdem die Site in der Ressourcenkonsole ausgewählt wurde.

Sobald eine bestimmte Community-Site ausgewählt ist, können alle vorhandenen Ressourcen und Lernpfade verwaltet und geändert werden. Es können neue Ressourcen für die Aktivierung und Lernpfade erstellt werden.

![community-resources](assets/community-resources.png)

#### Suche {#search-features}

![search](assets/searchsite.png)

Wählen Sie das Symbol zum Umschalten zwischen den Seitenbedienfeldern aus, um nach einer Aktivierungsressource oder einem Lernpfad zu suchen. Wenn diese Option aktiviert ist, wird auf der linken Seite der Konsole ein Suchfeld geöffnet und ein Textfeld zur Eingabe von Suchbegriffen bereitgestellt.

![search-result](assets/search-result.png)

#### Selection Mode {#selection-mode}

To select multiple enablement resources, select the first by hovering over the card and selecting the checkmark icon. Once selected, selecting any other card will add it to the selection group. Selecting a second time de-selects the card.

![selection-mode](assets/selection-mode.png)

## Ressource erstellen {#create-a-resource}

![create-resource](assets/create-resource1.png)

So fügen Sie der Community-Site eine neue Aktivierungsressource hinzu

* Select the `Create` icon.
* From the sub-menu which displays, select **[!UICONTROL Resource]**.

Dadurch wird ein schrittweiser Prozess gestartet mit:

* Beschreibung der Ressource (Name, Kartenbild und Text).
* Auswählen des Ressourceninhalts.
* Selecting a cover image for the resource.
* Identifizieren von Ressourcenkontakten.
* Zuweisen von Ressourcen zu Mitgliedern.

Ist die Ressource Teil eines Kurses, eines Lernpfads, sollten Mitglieder nur dem Lernpfad zugewiesen werden. Zuweisungen können hinzugefügt werden, nachdem die Aktivierungsressource erstellt wurde.

### 1 Basic Info {#basic-info}

![resource-basicinfo](assets/resource-basicinfo.png)

* **[!UICONTROL Bild hinzufügen]**

   (*Optional*) An image to display on the card for the enablement resource in the member&#39;s assignments page as well as the Resources console. Das Bild wird aus dem lokalen Dateisystem des Servers ausgewählt. Wenn kein Bild bereitgestellt wird, wird eine Miniaturansicht für die hochgeladene Ressource generiert.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht einfach 480 x 480 Pixel. Due to the responsive design of the cards to various browser dimensions, the display size will vary from 220 X 165 pixels to 400 x 165 pixels.

* **[!UICONTROL Site-Name]**

   (*readonly*) The community site to which the resource is being added.

* **[!UICONTROL Ressourcenname]**

   (*Required*) The display name for the resource. A valid node name is created from the display name.

* **[!UICONTROL Tags]**

   (*Optional*) One or more tags may be chosen which associate the enablement resource with one or more catalogs. See [Tagging Enablement Resources](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   When unchecked, the enablement resource will not appear in any catalog. Wenn diese Option aktiviert ist, wird die Aktivierungsressource in allen Katalogen angezeigt, es sei denn, die [vorgefilterten](catalog-developer-essentials.md#pre-filters) Filter oder die Mitglieder der Benutzeroberfläche werden vorgefiltert. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*Optional*) The description to display for the enablement resource.

* **[!UICONTROL Kleines Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein Miniaturbild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. in einem Katalog.

* **[!UICONTROL Großes Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein großes Bild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. auf der Hauptseite einer Ressource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*Optional*) Selected from AEM Assets. Ein Inhaltsfragment, auf das in der Umgebung &quot;Veröffentlichen&quot;verwiesen werden kann, das jedoch standardmäßig nicht verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus

### 2 Add Content {#add-content}

![resource-addcontent](assets/resource-addcontent.png)

Es wird zwar so angezeigt, als ob mehrere Aktivierungsressourcen ausgewählt wären, es ist jedoch nur eine zulässig.

Wählen Sie oben rechts `'+' icon`die Ressource aus, um mit der Auswahl der Quelle zu beginnen.

![upload-resource](assets/upload-resource1.png)

* **[!UICONTROL Upload aus lokalen Dateien]**

   Uploading from the local file system will use the native file browser to select and upload a file. Unterstützte Dateitypen sind SCORM.zip (HTML5 oder SWF), MP4-Video-, SWF-, PDF- und Bildtypen (JPG, PNG, GIF, BMP). Der Dateiname wird zum Namen des Assets, der der Asset-Bibliothek hinzugefügt wird.

* **[!UICONTROL Asset-Bibliothek durchsuchen]**

   Wählen Sie aus der Asset-Bibliothek. Die Auswahl ist auf diejenigen beschränkt, die auf der Community-Site sichtbar sind.

* **[!UICONTROL Externe URL hinzufügen]**

   Geben Sie einen Link zu Lerninhalten ein.

   Geben Sie in das daraufhin geöffnete Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL URL]**

      Die URL zu einem Asset.

* **[!UICONTROL Adobe Connect-URL hinzufügen]**

   Geben Sie einen Link zu einer Adobe Connect-Sitzung ein.

   Geben Sie in das daraufhin geöffnete Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL URL]**

      Die URL zu einer Adobe Connect-Sitzung.

* **[!UICONTROL Externe Ressource definieren]**

   Geben Sie die Stelle ein, an der das Material vorgestellt werden soll. Die Werte für den Erfolgsstatus und das Ergebnis werden manuell eingegeben (siehe [Berichte](reports.md)). Ein hochgeladenes Deckblattbild kann für zusätzliche Informationen verwendet werden.

   Geben Sie in das daraufhin geöffnete Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL Ort]**

      Die Lage eines physischen Standorts, z. B. eines Klassenzimmers.

#### Beispiel für eine hinzugefügte Videoressource {#example-of-an-added-video-resource}

![add-video](assets/add-video.png)

* **[!UICONTROL Ressourcen-Titelbild]**

   Das Deckblattbild ist ein Bild, das angezeigt wird, wenn die Aktivierungsressource zum ersten Mal angezeigt wird. For example, the cover image is displayed when a video resource is not yet playing. If a custom image is not uploaded, a default image is displayed. For video resources, it may be possible to [generate a thumbnail](enablement.md#ffmpeg), but only when uploaded and not when the video is referenced as an URL. Für Standortressourcen kann das Bild verwendet werden, um zusätzliche Informationen bereitzustellen.

   The recommended size for the cover image is 640 x 360 px.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### 3 Settings {#settings}

![resource-settings](assets/resource-settings.png)

>[!NOTE]
>
>Lernende sollten nicht direkt in Aktivierungsressourcen eingeschrieben werden, auf die von einem Lernpfad aus verwiesen werden soll. Learners need only be enrolled in the learning path.
>
>Wenn ein Mitglied sowohl in einer Ressource als auch in einem Lernpfad angemeldet ist, der auf diese Ressource verweist, zeigen ihre Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.


* **[!UICONTROL Einstellungen für Social Media]**

   Diese Einstellungen steuern, ob Lernende Eingaben in Bezug auf die Aktivierungsressource bereitstellen können. Die [Moderationseinstellungen](sites-console.md#moderation) entsprechen denen der übergeordneten Community-Site.

   * **[!UICONTROL Kommentieren zulassen]**

      Wenn diese Option aktiviert ist, können Mitglieder die Ressource kommentieren. Diese Option ist standardmäßig aktiviert.

   * **[!UICONTROL Bewertungen zulassen]**

      Wenn diese Option aktiviert ist, können Mitglieder die Ressource bewerten. Diese Option ist standardmäßig aktiviert.

   * **[!UICONTROL Anonymen Zugriff erlauben]**

      Wenn diese Option aktiviert ist, dürfen anonyme Site-Besucher die Ressource in einem Katalog Ansicht haben, wenn die Community-Site auch den anonymen Zugriff zulässt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum gewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.

* **[!UICONTROL Ressourcen-Autor]**

   *(Optional)* Der Autor der Aktivierungsressource. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder der [Mitgliedergruppe](#members-group)sind.

* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Erforderlich)* Eine Person, die das Mitglied bezüglich der Aktivierungsressource kontaktieren kann. Use the pulldown menu to select from the users who are members of the [members group](#members-group).

* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* A person the member can contact who has expertise regarding the enablement resource. Use the pulldown menu to select from users who are members of the [members group](#members-group).

### 4 Assignments {#assignments}

![resource-assignments](assets/resource-assignments.png)

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Use the pulldown menu to select from [members](#members-group) - The users and user groups (listed in bold face) - who are to be enrolled as Learners. Wenn sich Mitglieder auf der Community-Site anmelden, werden die Aktivierungsressourcen (und Lernpfade), in die sie eingeschrieben sind, auf ihrer Seite &quot; [Aufgaben](functions.md#assignments-function) &quot;angezeigt.

* Wählen Sie **[!UICONTROL Erstellen]**.

   ![resourceinfo](assets/resourceinfo.png)

Successful creation of the enablement resource returns to the Resources console with the newly created resource selected. From this console, it is possible to [manage the resource](#managing-a-resource).

## Create a Learning Path {#create-a-learning-path}

![add-learning-path](assets/add-learning-path.png)

To add a new learning path to the community site

* Wählen Sie das `Create` Symbol
* Wählen Sie im angezeigten Untermenü die Option **[!UICONTROL Lernpfad]**.

Dadurch wird ein schrittweiser Prozess gestartet mit:

* Identifizieren des Lernpfads.
* Bereitstellung eines Kartenbilds zur Darstellung des Lernpfads für die Lernenden.
* Referenzieren der in den Lernpfad einzubeziehenden Ressourcen für die Aktivierung.
* Optional die Reihenfolge der Ressourcen.
* Optional Identifizieren von voraussichtlichen Lernpfaden.
* Identifizieren eines Lernpfadkontakts.
* Mitglieder werden eingeschrieben.

For enablement resources included in a learning path, the assignments should only be made for the learning path and not for the individual resources.

### Grundlegende Informationen {#basic-info-1}

![learningpath-basic](assets/learningpath-basic1.png)

* **[!UICONTROL Bild hinzufügen]**

   (*Optional*) Ein Bild, das auf der Karte für den Lernpfad auf der Seite &quot;Zuweisungen&quot;des Mitglieds sowie in der Konsole &quot;Ressourcen&quot;angezeigt wird. The image is selected from the server&#39;s local file system. If an image is not provided, a thumbnail will be generated for the uploaded resource.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht mehr einfach 480 x 480 Pixel. Due to the responsive design of the cards to various browser dimensions, the display size will vary from 220 X 165 pixels to 400 x 165 pixels.

* **[!UICONTROL Site-Name]**

   (*schreibgeschützt*) Die Community-Site, der die Ressource hinzugefügt wird.

* **[!UICONTROL Lernpfad-Name]**

   (*Erforderlich*) Der Anzeigename für den Lernpfad. Aus dem Anzeigenamen wird ein gültiger Knotenname erstellt.

* **[!UICONTROL Tags]**

   (*Optional*) One or more tags may be chosen which associate the learning path with one or more catalogs. See [Tagging Enablement Resources](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   When unchecked, the learning path will not appear in any catalog. If checked, the learning path will appear in all catalogs unless [pre-filtered](catalog-developer-essentials.md#pre-filters) or the member filters from the UI. Durch die Anzeige des Lernpfads in einem Katalog erhalten Sie indirekt Zugriff auf alle darin enthaltenen Ressourcen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*Optional*) The description to display for the enablement resource.

* **[!UICONTROL Kleines Asset]**

   (*Optional*) Selected from AEM Assets. A thumbnail image to represent the resource in the publish environment, such as in a catalog.

* **[!UICONTROL Großes Asset]**

   (*Optional*) Selected from AEM Assets. A large image to represent the resource in the publish environment, such as on the main page for a resource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*Optional*) Selected from AEM Assets. Ein Inhaltsfragment, auf das in der Umgebung &quot;Veröffentlichen&quot;verwiesen werden kann, das jedoch standardmäßig nicht verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Voraussetzungen hinzufügen {#add-prerequisites}

![learningpath-prerequisites](assets/learningpath-prerequisites.png)

* **[!UICONTROL Erforderliche Lernpfade]**

   (*Optional*) Wenn andere veröffentlichte Lernpfade ausgewählt werden, müssen sie abgeschlossen sein, bevor ein Lernender diesen Lernpfad auswählen kann.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Ressourcen hinzufügen {#add-resources}

![learningpath-addresource](assets/learningpath-addresource.png)

* **[!UICONTROL Reihenfolge im Lernpfad erzwingen]**

   (*Optional*) If set to On, then the order in which the enablement resources are added is the order in which learners are required to proceed through the learning path. Default is Off.

* **[!UICONTROL Ressourcen]**

   One or more Resources chosen from among the *published* enablement resources created for the current community site.

>[!NOTE]
>
>You can only select the resources available at the same level as the learning path. For example, for a learning path created in a group only the group level resources are available; for a learning path created in a community site the resources in that site are available for adding to the learning path.


* Wählen Sie **[!UICONTROL Weiter]** aus.

### Einstellungen {#settings-1}

![learningpath-settings1](assets/learningpath-settings1.png)

* **[!UICONTROL Einschreibungen hinzufügen]**

   Use the pulldown menu to select from the members and member groups (listed in bold face) who are members of the community site&#39;s [members group](#members-group). Es ist nicht erforderlich, Zuweisungen beim ersten Erstellen des Lernpfads hinzuzufügen. The learning path properties can be modified to add learners at a later time.

* **[!UICONTROL Learning Path Contact&amp;ast;]**

   *(Required)* A person the member can contact regarding the learning path. Use the pulldown menu to select from the users who are members of the community site&#39;s [members group](#members-group).

* Wählen Sie **[!UICONTROL Erstellen]**

>[!NOTE]
>
>Enablement resources referenced from the learning path should not list the same Assignees (learners), if any.
>
>Wenn ein Mitglied sowohl in einer Aktivierungsressource als auch in einem Lernpfad, der auf diese Ressource verweist, eingeschrieben ist, zeigen ihre Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.


## Managing a Resource {#managing-a-resource}

To manage a single enablement resource:

* From the **[!UICONTROL Resources]** console, select the community site which contains the resource.
* Wählen Sie die Ressource aus.

For the selected enablement resource, it is possible to:

* View properties (default)
* Eigenschaften bearbeiten
* Löschen
* Veröffentlichen  
* Veröffentlichung rückgängig machen

To upload a new version of the enablement resource, it is recommended to create a new resource, and then unenroll members from the old version and enroll them in the new version.

### Ressource bearbeiten {#edit-resource}

![edit-resource](assets/edit-resource.png)

By selecting the pencil icon, the steps shown for creating a an enablement resource are made available so that any of the information provided may be modified.

If the only change is to modify assignments on the Settings step, then saving the changes results in the modifications being published. If any other changes are made, the resource must be explicitly published afting saving.

### Ressource löschen {#delete-resource}

![delete-resource](assets/delete-resource.png)

By selecting the trashcan icon, the enablement resource will be `Deleted` after confirmation.

### Veröffentlichen   {#publish}

![publish-resource](assets/publish-resource1.png)

Before learners are able to see an assigned enablement resourse, it must be published:

* Select the world icon to `Publish`.
* In the dialog which pops up, select **[!UICONTROL Publish]** again.
* Select **[!UICONTROL Close]**.

Even though the dialog states the action is queued, it often is published immediately.

### Veröffentlichung rückgängig machen {#unpublish}

![unpublish](assets/unpublish.png)

To temporarily make the enablement resources unaccessible to members in the publish environment without deleting it, use the world icon to `Unpublish` the resource.

### Bericht {#report}

![resource-reports](assets/resource-reports.png)

The Report icon provides access to the reports generated when learners interact with their assigned enablement resources in the publish environment. The report varies depending on the type of resource.

For all learning paths, it is possible to view a report based either on resources or learners ( `User Report`.)

![learningpath-info](assets/learningpath-info1.png)

This Report is specifically for the current enablement resource or learning path. The depth of reporting provided depends on whether or not [Adobe Analytics](analytics.md) is licensed and enabled for the community site. The [Timeline](#timeline), [Viewer Engagement](#viewer-engagement), and [Engagement by Device](#engagement-by-device) reports are imported from Adobe Analytics based on the [polling interval](analytics.md#report-importer).

For all enablement resources, regardless of whether or not Adobe Analytics is enabled, there are reports on [Assignee Status](#assignee-status) and [Ratings](#ratings) as well as a [Report Summary](#report-summary) table.

![resource-report](assets/resource-report1.png)

#### Timeline {#timeline}

The Analytics Timeline report shows when events occur over time for this enablement resource:

* **Ansichten**

   A view is when a learner visits the resource details page.

* **Wiedergaben**

   A play is when alLearner interacts with the resource, such as playing a video or opening a PDF.

* **Bewertungen**

   A rating is when a learner assigns a star rating to a resource.

* **Kommentare**

   A comment is when alLearner adds a comment.

The vertical axis is the number of events.

The horizontal axis is calendar time.

[Adobe Analytics required](sites-console.md#analytics).

#### Betrachterinteraktion {#viewer-engagement}

The Analytics Viewer Engagement report shows, for video resources, the number of learners who have viewed the resource and, if not played to the end, at what point learners stopped playing it.

The vertical axis is the number of learners who have viewed this resource.

Die horizontale Achse ist die Dauer dieser Ressource.

[Marketing Cloud-Organisations-ID erforderlich](sites-console.md#enablement).

#### Interaktion nach Gerät {#engagement-by-device}

Der Bericht &quot;Analytics-Interaktion nach Gerät&quot;beschreibt für Videoressourcen den prozentualen Anteil der Ansichten, die vom Desktop und von Mobilgeräten wiedergegeben wurden.

[Marketing Cloud-Organisations-ID erforderlich](sites-console.md#enablement).

#### Status des Bevollmächtigten {#assignee-status}

Der Bericht zum Status des Empfängers basierend auf der Anzahl der Lernenden beschreibt, wie viele

* **Nicht gestartet**
* **In Bearbeitung**
* **Abgeschlossen**

#### Bewertungen {#ratings}

Der Bewertungsbericht basiert auf der Anzahl der Lernenden, die die Berechtigungsressource bewertet haben. Er zeigt die Anzahl der einzelnen Bewertungssterne sowie eine Zusammenfassung der Gesamtanzahl der Bewertungen und der durchschnittlichen Bewertung an.

#### Berichtszusammenfassung {#report-summary}

Bei einer Aktivierungsressource handelt es sich bei der Berichtszusammenfassung um eine Tabellenliste.

* Jeder Lernende, der mit der Ressource interagiert hat
   * ihr Status
   * ob ihnen die Ressource zugewiesen wurde
      * Anstatt die Ressource in einem Katalog zu finden
      * Anzahl der geposteten Kommentare
      * Angabe des Ratings, falls vorhanden

Bei einem Bericht zu Lernpfaden-Ressourcen ist die Berichtszusammenfassung eine Tabelle mit

* Jede im Lernpfad enthaltene Ressource
   * Veröffentlichungsstatus
   * Anzahl Ansichten
   * Anzahl der Wiedergaben
   * Durchschnittliche Bewertung
   * Format
   * Größe
   * Community-Site-Name

Bei einem Benutzerbericht mit Lernpfad handelt es sich bei der Berichtszusammenfassung um eine Tabellenliste.

* Jeder Lernende, der dem Lernpfad zugewiesen ist:
   * Anzahl der abgeschlossenen Ressourcen.
   * Ihr Status.

Sie können die Anzeige der Tabelle anpassen, indem Sie Spalten mithilfe der `Show / hide columns` Auswahl auswählen.

#### Download Report as CSV {#download-report-as-csv}

Die Tabelle &quot;Berichtzusammenfassung&quot;kann im CSV-Format mit einer Schaltfläche oben in der Konsole heruntergeladen werden.

* For an enablement resource: `Download Resource Report as CSV` button.
* For a learning path: `Download Learning Path Report as CSV` button.

The complete Reports Summary is downloaded regardless of columns chosen for display.
