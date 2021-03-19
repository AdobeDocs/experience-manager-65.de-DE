---
title: Aktivierungsressourcen-Konsole
seo-title: Aktivierungsressourcen-Konsole
description: In der Ressourcenkonsole erstellen, verwalten und weisen Aktivierungsmanager Ressourcen Mitgliedern einer Community-Site für eine Aktivierung zu.
seo-description: In der Ressourcenkonsole erstellen, verwalten und weisen Aktivierungsmanager Ressourcen Mitgliedern einer Community-Site für eine Aktivierung zu.
uuid: 52445b39-c339-4b39-8004-eb36de99bced
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1ef15e76-fe7c-4ced-a20d-c0a9385e3ee4
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2980'
ht-degree: 6%

---


# Aktivierungsressourcen-Konsole {#enablement-resources-console}

Für AEM Communities ist die Ressourcenkonsole der Ort, an dem [Aktivierungsmanager](users.md) Ressourcen erstellen, verwalten und Mitgliedern einer Community-Site für die Aktivierung zuweisen.

## Voraussetzungen {#requirements}

Vor dem Hinzufügen von Aktivierungsressourcen für eine Community-Site müssen die AEM ordnungsgemäß konfiguriert sein, einschließlich:

* SCORM
* FFmpeg

Weitere Informationen finden Sie unter [Konfigurieren der Aktivierung](enablement.md).

>[!CAUTION]
>
>Wenn SCORM nach der Erstellung einer Community-Site installiert wird, müssen alle vor der Installation von SCORM vorhandenen Aktivierungsressourcen neu erstellt werden.

>[!NOTE]
>
>Mit der Veröffentlichung von [AEM 6.3](deploy-communities.md#latestfeaturepack) und den entsprechenden Communities Feature Packs [AEM 6.2 FP3](deploy-communities.md#latestfeaturepack) und [AEM 6.1 FP7](https://docs.adobe.com/content/docs/en/aem/6-1/deploy/communities.html#Latest Feature Pack) ist für die Aktivierung keine [MySQL-Datenbank](mysql.md) mehr erforderlich.

## Terminologie {#terminology}

### Ressource {#resource}

Ressourcen sind unverzichtbar für eine [Aktivierungs-Community](overview.md#enablement-community). Sie sind die Materialien, die den Mitgliedern zugewiesen werden, damit sie ihre Fähigkeiten verbessern können.

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

Wenn eine Community-Site erstellt wird, wird der Name, der der Site für die URL gegeben wird, bei der Erstellung der [Site-spezifischen Benutzergruppen](users.md) verwendet, die mit verschiedenen Berechtigungen für verschiedene Rollen konfiguriert wurden. All diese automatisch erstellten Gruppen haben das Präfix `Community <site-name>`.

Eine dieser Benutzergruppen ist die Gruppe `Community <site-name> Members`, die registrierte Benutzer in der Umgebung zum Veröffentlichen als Community-Mitglieder identifiziert. Ein Beispiel finden Sie im Tutorial [Erste Schritte mit AEM Communities für Aktivierung](getting-started-enablement.md).

Für [Implementierungsgemeinschaften](overview.md#egagementcommunity) ist es sinnvoll, Site-Besuchern zu erlauben, sich selbst zu registrieren oder Social-Login zu verwenden. Zu diesem Zeitpunkt werden sie automatisch der Mitgliedergruppe hinzugefügt.

Für [Aktivierungsgemeinschaften](overview.md#enablement-community) wird empfohlen, die Site privat zu gestalten. Danach muss ein Administrator Benutzer zur Mitgliedergruppe hinzufügen.

## Zugriff auf die Aktivierungsressourcen einer Community-Site {#accessing-a-community-site-s-enablement-resources}

### Navigieren Sie zu Communities Ressourcen {#navigate-to-communities-resources}

In der Umgebung &quot;author&quot;zur Konsole &quot;Resources&quot;

* Aus globaler Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]**

   ![enable-sites](assets/enablement-sites.png)

### Community-Site {#select-a-community-site} auswählen

Die Communities-Ressourcen-Konsole zeigt alle Community-Sites an.

Aktivierungsressourcen werden für eine bestimmte Community-Site erstellt, nachdem die Site in der Ressourcenkonsole ausgewählt wurde.

Sobald eine bestimmte Community-Site ausgewählt ist, können alle vorhandenen Ressourcen und Lernpfade verwaltet und geändert werden. Es können neue Ressourcen für die Aktivierung und Lernpfade erstellt werden.

![community-resources](assets/community-resources.png)

#### Suche {#search-features}

![search](assets/searchsite.png)

Wählen Sie das Symbol zum Umschalten zwischen den Seitenbedienfeldern aus, um nach einer Aktivierungsressource oder einem Lernpfad zu suchen. Wenn diese Option aktiviert ist, wird auf der linken Seite der Konsole ein Suchfeld geöffnet und ein Textfeld zur Eingabe von Suchbegriffen bereitgestellt.

![search-result](assets/search-result.png)

#### Auswahlmodus {#selection-mode}

Um mehrere Aktivierungsressourcen auszuwählen, wählen Sie die erste aus, indem Sie den Mauszeiger über die Karte halten und das Häkchensymbol auswählen. Wenn Sie eine andere Karte ausgewählt haben, wird sie der Auswahlgruppe hinzugefügt. Wenn Sie ein zweites Mal auswählen, wird die Karte deaktiviert.

![selection-mode](assets/selection-mode.png)

## Eine Ressource {#create-a-resource} erstellen

![create-resource](assets/create-resource1.png)

So fügen Sie der Community-Site eine neue Aktivierungsressource hinzu

* Wählen Sie das Symbol `Create`.
* Wählen Sie im angezeigten Untermenü **[!UICONTROL Ressource]** aus.

Dadurch wird ein schrittweiser Prozess gestartet mit:

* Beschreibung der Ressource (Name, Kartenbild und Text).
* Auswählen des Ressourceninhalts.
* Auswählen eines Deckblattbilds für die Ressource.
* Identifizieren von Ressourcenkontakten.
* Zuweisen von Ressourcen zu Mitgliedern.

Ist die Ressource Teil eines Kurses, eines Lernpfads, sollten Mitglieder nur dem Lernpfad zugewiesen werden. Zuweisungen können hinzugefügt werden, nachdem die Aktivierungsressource erstellt wurde.

### 1 Grundlegende Informationen {#basic-info}

![resource-basicinfo](assets/resource-basicinfo.png)

* **[!UICONTROL Bild hinzufügen]**

   (*Optional*) Ein Bild, das auf der Karte für die Aktivierungsressource auf der Seite &quot;Zuweisungen&quot;des Mitglieds sowie in der Ressourcenkonsole angezeigt wird. Das Bild wird aus dem lokalen Dateisystem des Servers ausgewählt. Wenn kein Bild bereitgestellt wird, wird eine Miniaturansicht für die hochgeladene Ressource generiert.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht einfach 480 x 480 Pixel. Aufgrund des reaktionsfähigen Designs der Karten mit verschiedenen Browser-Abmessungen kann die Anzeigegröße von 220 x 165 Pixel bis 400 x 165 Pixel betragen.

* **[!UICONTROL Site-Name]**

   (*readonly*) Die Community-Site, der die Ressource hinzugefügt wird.

* **[!UICONTROL Ressourcenname]**

   (*Erforderlich*) Der Anzeigename für die Ressource. Aus dem Anzeigenamen wird ein gültiger Knotenname erstellt.

* **[!UICONTROL Tags]**

   (*Optional*) Es können ein oder mehrere Tags ausgewählt werden, die die Aktivierungsressource mit einem oder mehreren Katalogen verbinden. Siehe [Tagging-Aktivierungsressourcen](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   Wenn diese Option deaktiviert ist, wird die Aktivierungsressource in keinem Katalog angezeigt. Wenn diese Option aktiviert ist, wird die Aktivierungsressource in allen Katalogen angezeigt, es sei denn, [vorgefiltert](catalog-developer-essentials.md#pre-filters) oder die Member-Filter aus der Benutzeroberfläche. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Die Beschreibung, die für die Aktivierungsressource angezeigt werden soll.

* **[!UICONTROL Kleines Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein Miniaturbild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. in einem Katalog.

* **[!UICONTROL Großes Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein großes Bild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. auf der Hauptseite einer Ressource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein Inhaltsfragment, auf das in der Umgebung &quot;Veröffentlichen&quot;verwiesen werden kann, das jedoch standardmäßig nicht verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus

### 2 Hinzufügen Inhalt {#add-content}

![resource-addcontent](assets/resource-addcontent.png)

Es wird zwar so angezeigt, als ob mehrere Aktivierungsressourcen ausgewählt wären, es ist jedoch nur eine zulässig.

Wählen Sie `'+' icon` in der oberen rechten Ecke aus, um mit der Auswahl der Ressource durch Identifizieren der Quelle zu beginnen.

![upload-resource](assets/upload-resource1.png)

* **[!UICONTROL Upload aus lokalen Dateien]**

   Beim Hochladen aus dem lokalen Dateisystem wird der native Dateibrowser verwendet, um eine Datei auszuwählen und hochzuladen. Unterstützte Dateitypen sind SCORM.zip (HTML5 oder SWF), MP4-Video-, SWF-, PDF- und Bildtypen (JPG, PNG, GIF, BMP). Der Dateiname wird zum Namen des Assets, der der Asset-Bibliothek hinzugefügt wird.

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

   * **[!UICONTROL Standort]**

      Die Lage eines physischen Standorts, z. B. eines Klassenzimmers.

#### Beispiel für eine hinzugefügte Videoressource {#example-of-an-added-video-resource}

![add-video](assets/add-video.png)

* **[!UICONTROL Ressourcen-Titelbild]**

   Das Deckblattbild ist ein Bild, das angezeigt wird, wenn die Aktivierungsressource zum ersten Mal angezeigt wird. Das Deckblattbild wird beispielsweise angezeigt, wenn eine Videoressource noch nicht abgespielt wird. Wenn kein benutzerdefiniertes Bild hochgeladen wird, wird ein Standardbild angezeigt. Bei Videoressourcen ist es möglicherweise möglich, eine Miniaturansicht von [zu erstellen, allerdings nur beim Hochladen und nicht, wenn das Video als URL referenziert wird. ](enablement.md#ffmpeg) Für Standortressourcen kann das Bild verwendet werden, um zusätzliche Informationen bereitzustellen.

   Die empfohlene Größe für das Deckblattbild ist 640 x 360 Pixel.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### 3 Einstellungen {#settings}

![resource-settings](assets/resource-settings.png)

>[!NOTE]
>
>Lernende sollten nicht direkt in Aktivierungsressourcen eingeschrieben werden, auf die von einem Lernpfad aus verwiesen werden soll. Lernende müssen nur in den Lernpfad eingeschrieben werden.
>
>Wenn ein Mitglied sowohl in einer Ressource als auch in einem Lernpfad angemeldet ist, der auf diese Ressource verweist, zeigen ihre Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.

* **[!UICONTROL Einstellungen für Social Media]**

   Diese Einstellungen steuern, ob Lernende Eingaben in Bezug auf die Aktivierungsressource bereitstellen können. Die [Moderationseinstellungen](sites-console.md#moderation) sind die der übergeordneten Community-Site.

   * **[!UICONTROL Kommentieren zulassen]**

      Wenn diese Option aktiviert ist, können Mitglieder die Ressource kommentieren. Diese Option ist standardmäßig aktiviert.

   * **[!UICONTROL Bewertungen zulassen]**

      Wenn diese Option aktiviert ist, können Mitglieder die Ressource bewerten. Diese Option ist standardmäßig aktiviert.

   * **[!UICONTROL Anonymen Zugriff erlauben]**

      Wenn diese Option aktiviert ist, dürfen anonyme Site-Besucher die Ressource in einem Katalog Ansicht haben, wenn die Community-Site auch den anonymen Zugriff zulässt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum gewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.

* **[!UICONTROL Ressourcen-Autor]**

   *(Optional)* Der Autor der Aktivierungsressource. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder der Gruppe [Mitglieder](#members-group) sind.

* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Erforderlich)* Eine Person, die das Mitglied bezüglich der Aktivierungsressource kontaktieren kann. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder der Gruppe [Mitglieder](#members-group) sind.

* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* Eine Person, die mit der Aktivierungsressource in Verbindung steht. Verwenden Sie das Pulldown-Menü, um Benutzer auszuwählen, die Mitglieder der Gruppe [Mitglieder](#members-group) sind.

### 4 Zuweisungen {#assignments}

![Ressourcenzuweisungen](assets/resource-assignments.png)

* **[!UICONTROL Bevollmächtigte hinzufügen]**

   Verwenden Sie das Pulldown-Menü, um aus [Mitgliedern](#members-group) - Die Benutzer und Benutzergruppen (in Fettdruck aufgelistet) auszuwählen, die als Lernende eingeschrieben werden sollen. Wenn sich Mitglieder bei der Community-Site anmelden, werden die Aktivierungsressourcen (und Lernpfade), in die sie eingeschrieben sind, auf ihrer [Assignments](functions.md#assignments-function)-Seite angezeigt.

* Wählen Sie **[!UICONTROL Erstellen]**.

   ![resourceinfo](assets/resourceinfo.png)

Bei erfolgreicher Erstellung der Ressourcen für die Aktivierung wird die Ressourcenkonsole mit der neu erstellten Ressource erneut ausgewählt. In dieser Konsole ist es möglich, die Ressource [zu verwalten.](#managing-a-resource)

## Lernpfad {#create-a-learning-path} erstellen

![add-learning-path](assets/add-learning-path.png)

So fügen Sie der Community-Site einen neuen Lernpfad hinzu

* Wählen Sie das Symbol `Create`
* Wählen Sie im angezeigten Untermenü **[!UICONTROL Lernpfad]** aus.

Dadurch wird ein schrittweiser Prozess gestartet mit:

* Identifizieren des Lernpfads.
* Bereitstellung eines Kartenbilds zur Darstellung des Lernpfads für die Lernenden.
* Referenzieren der in den Lernpfad einzubeziehenden Ressourcen für die Aktivierung.
* Optional die Reihenfolge der Ressourcen.
* Optional Identifizieren von voraussichtlichen Lernpfaden.
* Identifizieren eines Lernpfadkontakts.
* Mitglieder werden eingeschrieben.

Für die in einem Lernpfad enthaltenen Aktivierungsressourcen sollten die Zuweisungen nur für den Lernpfad und nicht für die einzelnen Ressourcen vorgenommen werden.

### Grundlegende Informationen {#basic-info-1}

![learn-path-basic](assets/learningpath-basic1.png)

* **[!UICONTROL Bild hinzufügen]**

   (*Optional*) Ein Bild, das auf der Karte für den Lernpfad auf der Seite Zuweisungen des Mitglieds sowie in der Ressourcenkonsole angezeigt wird. Das Bild wird aus dem lokalen Dateisystem des Servers ausgewählt. Wenn kein Bild bereitgestellt wird, wird eine Miniaturansicht für die hochgeladene Ressource generiert.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht mehr einfach 480 x 480 Pixel. Aufgrund des reaktionsfähigen Designs der Karten mit verschiedenen Browser-Abmessungen kann die Anzeigegröße von 220 x 165 Pixel bis 400 x 165 Pixel betragen.

* **[!UICONTROL Site-Name]**

   (*Readonly*) Die Community-Site, der die Ressource hinzugefügt wird.

* **[!UICONTROL Lernpfad-Name]**

   (*Erforderlich*) Der Anzeigename für den Lernpfad. Aus dem Anzeigenamen wird ein gültiger Knotenname erstellt.

* **[!UICONTROL Tags]**

   (*Optional*) Es können ein oder mehrere Tags ausgewählt werden, die den Lernpfad mit einem oder mehreren Katalogen verbinden. Siehe [Tagging-Aktivierungsressourcen](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   Wenn diese Option deaktiviert ist, wird der Lernpfad in keinem Katalog angezeigt. Wenn diese Option aktiviert ist, wird der Lernpfad in allen Katalogen angezeigt, es sei denn, [vorgefiltert](catalog-developer-essentials.md#pre-filters) oder die Member-Filter aus der Benutzeroberfläche. Durch die Anzeige des Lernpfads in einem Katalog erhalten Sie indirekt Zugriff auf alle darin enthaltenen Ressourcen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Die Beschreibung, die für die Aktivierungsressource angezeigt werden soll.

* **[!UICONTROL Kleines Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein Miniaturbild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. in einem Katalog.

* **[!UICONTROL Großes Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein großes Bild, das die Ressource in der Umgebung &quot;Veröffentlichen&quot;darstellt, z. B. auf der Hauptseite einer Ressource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*Optional*) Aus AEM Assets ausgewählt. Ein Inhaltsfragment, auf das in der Umgebung &quot;Veröffentlichen&quot;verwiesen werden kann, das jedoch standardmäßig nicht verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Voraussetzungen hinzufügen {#add-prerequisites}

![Lernpfad-Voraussetzungen](assets/learningpath-prerequisites.png)

* **[!UICONTROL Erforderliche Lernpfade]**

   (*Optional*) Wenn andere veröffentlichte Lernpfade ausgewählt sind, müssen sie abgeschlossen sein, bevor ein Lernender diesen Lernpfad auswählen kann.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Ressourcen hinzufügen {#add-resources}

![learn-path-addresource](assets/learningpath-addresource.png)

* **[!UICONTROL Reihenfolge im Lernpfad erzwingen]**

   (*Optional*) Wenn diese Option auf &quot;Ein&quot;gesetzt ist, ist die Reihenfolge, in der die Aktivierungsressourcen hinzugefügt werden, die Reihenfolge, in der die Lernenden den Lernpfad durchlaufen müssen. Die Standardeinstellung ist deaktiviert.

* **[!UICONTROL Ressourcen]**

   Eine oder mehrere Ressourcen, die unter den *published*-Aktivierungsressourcen ausgewählt wurden, die für die aktuelle Community-Site erstellt wurden.

>[!NOTE]
>
>Sie können die verfügbaren Ressourcen nur auf derselben Ebene wie der Lernpfad auswählen. Beispielsweise stehen für einen Lernpfad, der in einer Gruppe erstellt wird, nur Ressourcen auf Gruppenebene zur Verfügung; für einen Lernpfad, der auf einer Community-Site erstellt wurde, stehen die Ressourcen auf dieser Site zum Hinzufügen zum Lernpfad zur Verfügung.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Einstellungen {#settings-1}

![learn-path-settings1](assets/learningpath-settings1.png)

* **[!UICONTROL Einschreibungen hinzufügen]**

   Verwenden Sie das Pulldown-Menü, um aus den (fettgedruckten) Mitgliedern und Mitgliedsgruppen auszuwählen, die Mitglieder der [Mitgliedergruppe](#members-group) der Community-Site sind. Es ist nicht erforderlich, Zuweisungen beim ersten Erstellen des Lernpfads hinzuzufügen. Die Eigenschaften des Lernpfads können geändert werden, um Lernende zu einem späteren Zeitpunkt hinzuzufügen.

* **[!UICONTROL Lernpfad Kontakt&amp;ast;]**

   *(Erforderlich)* Eine Person, die das Mitglied bezüglich des Lernpfads kontaktieren kann. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder der [Mitgliedergruppe](#members-group) der Community-Site sind.

* Wählen Sie **[!UICONTROL Erstellen]**

>[!NOTE]
>
>In den Aktivierungsressourcen, auf die vom Lernpfad verwiesen wird, sollten nicht dieselben Bevollmächtigten (Lernende) Liste werden, sofern vorhanden.
>
>Wenn ein Mitglied sowohl in einer Aktivierungsressource als auch in einem Lernpfad, der auf diese Ressource verweist, eingeschrieben ist, zeigen ihre Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.

## Verwalten einer Ressource {#managing-a-resource}

So verwalten Sie eine einzelne Aktivierungsressource

* Wählen Sie in der Konsole **[!UICONTROL Ressourcen]** die Community-Site aus, die die Ressource enthält.
* Wählen Sie die Ressource aus.

Für die ausgewählte Aktivierungsressource können Sie:

* Eigenschaften von Ansichten (Standard)
* Eigenschaften bearbeiten
* Löschen
* Veröffentlichen
* Veröffentlichung rückgängig machen

Um eine neue Version der Ressource für die Aktivierung hochzuladen, wird empfohlen, eine neue Ressource zu erstellen und dann die Anmeldung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version einzutragen.

### Ressource bearbeiten {#edit-resource}

![edit-resource](assets/edit-resource.png)

Durch Auswahl des Stiftsymbols werden die zum Erstellen einer Aktivierungsressource angezeigten Schritte verfügbar gemacht, sodass alle bereitgestellten Informationen geändert werden können.

Wenn die einzige Änderung darin besteht, Zuweisungen im Schritt Einstellungen zu ändern, werden die Änderungen beim Speichern veröffentlicht. Wenn andere Änderungen vorgenommen werden, muss die Ressource nach dem Speichern explizit veröffentlicht werden.

### Ressource löschen {#delete-resource}

![delete-resource](assets/delete-resource.png)

Durch Auswahl des Papierkorbsymbols wird nach der Bestätigung `Deleted` als Aktivierungsressource ausgewählt.

### Veröffentlichen   {#publish}

![publish-resource](assets/publish-resource1.png)

Bevor die Lernenden eine zugewiesene Aktivierungsressource sehen können, müssen sie veröffentlicht werden:

* Wählen Sie das Symbol Welt auf `Publish`.
* Wählen Sie im Popup-Dialogfeld **[!UICONTROL Veröffentlichen]** erneut.
* Wählen Sie **[!UICONTROL Schließen]**.

Obwohl im Dialogfeld angegeben wird, dass die Aktion in die Warteschlange gestellt ist, wird sie oft sofort veröffentlicht.

### Veröffentlichung rückgängig machen {#unpublish}

![unpublish](assets/unpublish.png)

Wenn Sie vorübergehend verhindern möchten, dass die Aktivierungsressourcen für Mitglieder in der Umgebung &quot;Veröffentlichen&quot;zugänglich sind, ohne sie zu löschen, verwenden Sie das Symbol &quot;Welt&quot;für `Unpublish`.

### Bericht {#report}

![resource-reports](assets/resource-reports.png)

Das Berichtssymbol ermöglicht den Zugriff auf die Berichte, die generiert werden, wenn die Lernenden mit ihren zugewiesenen Aktivierungsressourcen in der Umgebung &quot;Veröffentlichen&quot;interagieren. Der Bericht hängt vom Typ der Ressource ab.

Für alle Lernpfade ist es möglich, einen Bericht auf der Grundlage von Ressourcen oder Lernenden ( `User Report`) Ansicht.

![learn-path-info](assets/learningpath-info1.png)

Dieser Bericht ist speziell für die aktuelle Aktivierungsressource oder den Lernpfad gedacht. Die angegebene Tiefe des Berichte hängt davon ab, ob [Adobe Analytics](analytics.md) für die Community-Site lizenziert und aktiviert ist. Die Berichte [Zeitschiene](#timeline), [Viewer-Interaktion](#viewer-engagement) und [Interaktion nach Gerät](#engagement-by-device) werden basierend auf dem [Abfrageintervall](analytics.md#report-importer) aus Adobe Analytics importiert.

Für alle Aktivierungsressourcen gibt es Berichte zu [Status des zugewiesenen Benutzers](#assignee-status) und zu [Bewertungen](#ratings) sowie zu einer [Tabelle &quot;Berichtszusammenfassung](#report-summary)&quot;.

![resource-report](assets/resource-report1.png)

#### Zeitleiste {#timeline}

Der Bericht zur Analytics-Timeline zeigt an, wann Ereignis im Zeitverlauf für diese Aktivierungsressource auftreten:

* **Ansichten**

   Eine Ansicht ist, wenn ein Lernender die Seite mit den Ressourcendetails besucht.

* **Wiedergaben**

   Eine Wiedergabe erfolgt, wenn alLearn mit der Ressource interagiert, z. B. beim Abspielen eines Videos oder Öffnen einer PDF-Datei.

* **Bewertungen**

   Eine Bewertung ist, wenn ein Lernender einer Ressource eine Sternbewertung zuweist.

* **Kommentare**

   Ein Kommentar ist, wenn alLerner einen Kommentar hinzufügt.

Die vertikale Achse ist die Anzahl der Ereignis.

Die horizontale Achse ist die Kalenderzeit.

[Adobe Analytics erforderlich](sites-console.md#analytics).

#### Betrachterinteraktion {#viewer-engagement}

Der Bericht &quot;Interaktion mit dem Analytics-Viewer&quot;zeigt für Videoressourcen die Anzahl der Lernenden an, die die Ressource angesehen haben, und, falls sie nicht bis zum Ende wiedergegeben wurde, an welchem Punkt die Wiedergabe gestoppt wurde.

Die vertikale Achse ist die Anzahl der Lernenden, die diese Ressource angesehen haben.

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

Sie können die Anzeige der Tabelle anpassen, indem Sie Spalten mit der Auswahl `Show / hide columns` auswählen.

#### Bericht als CSV herunterladen {#download-report-as-csv}

Die Tabelle &quot;Berichtzusammenfassung&quot;kann im CSV-Format mit einer Schaltfläche oben in der Konsole heruntergeladen werden.

* Für eine Aktivierungsressource: `Download Resource Report as CSV`-Schaltfläche.
* Für einen Lernpfad: `Download Learning Path Report as CSV`-Schaltfläche.

Die vollständige Berichtszusammenfassung wird unabhängig von den zur Anzeige ausgewählten Spalten heruntergeladen.
