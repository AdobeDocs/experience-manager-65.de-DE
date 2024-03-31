---
title: Erstellen und Organisieren von Seiten mit AEM
description: Erfahren Sie, wie Sie mit Adobe Experience Manager Seiten erstellen und verwalten.
exl-id: 74576e51-4b4e-464e-a0b8-0fae748a505d
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2417'
ht-degree: 100%

---

# Erstellen und Organisieren von Seiten {#creating-and-organizing-pages}

In diesem Abschnitt wird beschrieben, wie Sie mit Adobe Experience Manager (AEM) Seiten erstellen und verwalten können, damit Sie anschließend auf diesen Seiten [Inhalte erstellen](/help/sites-authoring/editing-content.md) können.

>[!NOTE]
>
>Ihr Konto muss über die erforderlichen [Zugriffsrechte](/help/sites-administering/security.md) und [Berechtigungen](/help/sites-administering/security.md#permissions) verfügen, damit Sie Aktionen auf Seiten durchführen können, beispielsweise erstellen, kopieren, verschieben, bearbeiten und löschen.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an Ihre Systemadmins zu wenden.

>[!NOTE]
>
>Es steht eine Reihe von [Tastaturbefehlen](/help/sites-authoring/keyboard-shortcuts.md) in der Website-Konsole zur Verfügung, die eine effizientere Seitenorganisation ermöglichen.

## Organisation Ihrer Website {#organizing-your-website}

Organisieren Sie als Autorin oder Autor Ihre Website innerhalb von AEM. Dazu gehört die Erstellung und Benennung von Inhaltsseiten, sodass Folgendes zutrifft:

* Sie müssen leicht in der Authoring-Umgebung auffindbar sein.
* Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Sie können Ihre Inhalte auch mithilfe von [Ordnern](#creating-a-new-folder) organisieren.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Der Titel wird zusammen mit dem Seiteninhalt angezeigt.

Im Folgenden sehen Sie ein Beispiel von der Website We.Retail, auf der eine Seite mit Cargo-Shorts (`desert-sky-shorts`) aufgerufen wird:

* Authoring-Umgebung
  `https://localhost:4502/editor.html/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

* Publishing-Umgebung
  `https://localhost:4503/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

Je nach Konfiguration Ihrer Instanz kann die Verwendung von `/content` in der Publishing-Umgebung optional sein.

```xml
 /content
 /we-retail
  /us
   /en
    /products
     /equipment
      /hiking
       /desert-sky-shorts
       /hiking-poles
       /...
      /running...
      /surfing...
      /...
     /seasonal...
     /...
    /about-us
    /experience
    /...
   /es...
  /de...
  /fr...
  /...
 /...
```

Diese Struktur kann über die **Sites-Konsole** angezeigt werden. Von dort aus können Sie [durch die Seiten Ihrer Website navigieren](/help/sites-authoring/basic-handling.md#navigating) und Aktionen auf den Seiten durchführen. Sie können auch neue Sites und [neue Seiten](#creating-a-new-page) erstellen.

An jedem Punkt können Sie die Verzwigung nach oben in den Breadcrumbs in der Kopfzeilenleiste sehen:

![caop-01](assets/caop-01.png)

### Seitenbenennungskonventionen {#page-naming-conventions}

Beim Erstellen einer neuen Seite gibt es zwei Schlüsselfelder:

* **[Titel](#title)**:

   * Dieses Feld wird dem Benutzer bei der Bearbeitung im oberen Teil des Seiteninhalts in der Konsole angezeigt.
   * Dieses Feld ist obligatorisch.

* **[Name](#name)**:

   * Mit diesem Wert wird der URI generiert.
   * Benutzereingaben sind für dieses Feld optional. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet. Weitere Informationen finden Sie unter [Seitennamen-Einschränkungen und Best Practices](/help/sites-authoring/managing-pages.md#page-name-restrictions-and-best-practices).

#### Einschränkungen und Best Practices bei der Seitenbenennung {#page-name-restrictions-and-best-practices}

Der **Seitentitel** und der **Seitenname** können separat erstellt werden, sind aber verwandt:

* Beim Erstellen einer Seite ist nur das **Titelfeld** erforderlich. Wenn bei der Erstellung von Seiten kein **Name** angegeben wird, generiert AEM einen Namen aus den ersten 64 Zeichen des Titels (entsprechend der nachfolgenden Validierung). Nur die ersten 64 Zeichen werden verwendet, um gängige Best Practices für kurze Seitennamen zu unterstützen.

* Wenn ein Seitenname manuell vom Autor angegeben wird, gilt die Beschränkung von 64 Zeichen nicht, aber andere technische Einschränkungen gelten unter Umständen für die Länge des Seitennamens.

>[!NOTE]
>
>Beim Definieren eines Seitennamens ist es sinnvoll, den Seitennamen so kurz wie möglich zu halten, aber so ausdruckstark und erinnerungsstark wie möglich, um ihn für den Leser verständlich zu machen. Weitere Informationen zum `title`-Element finden Sie im [W3C-Styleguide](https://www.w3.org/Provider/Style/TITLE.html).
>
>Denken Sie auch daran, dass einige Browser (z. B. ältere Versionen von IE) nur URLs bis zu einer bestimmten Länge akzeptieren, sodass auch technische Gründe für die Verwendung von kurzen Seitennamen bestehen.

Beim Erstellen einer Seite [validiert AEM den Seitennamen entsprechend den von AEM und JCR vorgegebenen Konventionen](/help/sites-developing/naming-conventions.md).

Mindestens zulässig sind die folgenden Zeichen:

* „a“ bis „z“
* „A“ bis „Z“
* „0“ bis „9“
* `_` (Unterstrich)
* `-` (Bindestrich/Minus)

Umfassende Informationen zu allen zulässigen Zeichen finden Sie in den [Benennungskonventionen](/help/sites-developing/naming-conventions.md).

>[!NOTE]
>
>Wenn AEM auf einer [MongoMK-Persistenz-Manager-Bereitstellung](/help/sites-deploying/recommended-deploys.md) ausgeführt wird, sind Seitennamen auf 150 Zeichen beschränkt.

#### Titel {#title}

Wenn Sie für eine neu erstellte Seite nur den **Titel** angeben, leitet AEM den **Namen** für die Seite von dieser Zeichenfolge ab und [validiert den Namen entsprechend den Konventionen](/help/sites-developing/naming-conventions.md) von AEM und JCR. Im Feld **Titel** werden ungültige Zeichen akzeptiert, wobei die ungültigen Zeichen im abgeleiteten Namen jedoch ersetzt werden. Beispiel:

| Titel | Abgeleiteter Name |
|---|---|
| Schön | schoen.html |
| SC%&amp;&#42;ç+ | sc---c-.html |

#### Name {#name}

Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen gemäß den Konventionen von AEM und JCR](/help/sites-developing/naming-conventions.md). Die Eingabe von ungültigen Zeichen im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld mit einer erläuternden Meldung hervorgehoben.

![caop-02](assets/caop-02.png)

>[!NOTE]
>
>Sie sollten es vermeiden, einen Zwei-Buchstaben-Code gemäß ISO-639-1 als Seitennamen zu verwenden, sofern es sich nicht um einen Sprachstamm handelt.
>
>Weitere Informationen finden Sie unter [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md).

### Vorlagen {#templates}

In AEM gibt eine Vorlage einen speziellen Seitentyp an. Eine Vorlage wird als Grundlage für jede neue Seite verwendet, die erstellt wird.

Die Vorlage definiert die Seitenstruktur, u. a. eine Miniaturansicht und andere Eigenschaften. Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden. Vorlagen bestehen aus [Komponenten](#components).

Im Lieferumfang von AEM sind diverse Vorlagen enthalten. Welche Vorlagen verfügbar sind, hängt von der jeweiligen Website ab. Die wichtigsten Felder sind:

* **Titel**
Der Titel, der auf der resultierenden Web-Seite angezeigt wird.

* **Name**
Wird beim Benennen der Seite verwendet.

* **Vorlage**
Eine Liste von Vorlagen, die für das Erstellen neuer Seiten verwendet werden können.

>[!NOTE]
>
>Sofern auf Ihrer Instanz konfiguriert, [können Vorlagenautoren Vorlagen mit dem Vorlageneditor erstellen](/help/sites-authoring/templates.md).

### Komponenten {#components}

Komponenten sind die Elemente, die von AEM bereitgestellt werden, damit Sie bestimmte Inhaltstypen hinzufügen können. AEM ist mit [einsatzbereiten Komponenten](/help/sites-authoring/default-components-console.md) ausgestattet, die umfangreiche Funktionen bieten, wie:

* Text
* Bild
* Bildschirmpräsentation
* Video
* Und vieles mehr

Sobald Sie eine Seite erstellt und geöffnet haben, können Sie [Inhalte mithilfe der Komponenten hinzufügen](/help/sites-authoring/editing-content.md#insertinganewparagraph), die im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#componentbrowser) verfügbar sind.

>[!NOTE]
>
>Die [Komponentenkonsole](/help/sites-authoring/default-components-console.md) bietet einen Überblick über die Komponenten in Ihrer Instanz.

## Verwalten von Seiten {#managing-pages}

### Erstellen einer neuen Seite {#creating-a-new-page}

Falls nicht alle Seiten für Sie erstellt wurden, müssen Sie eine Seite erstellen, bevor Sie mit der Erstellung von Inhalten beginnen können:

1. Öffnen Sie die Sites-Konsole, (z. B. [https://localhost:4502/sites.html/content](https://localhost:4502/sites.html/content).).
1. Navigieren Sie zum Speicherort, an dem Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie **Seite** aus der Liste aus:

   ![caop-03](assets/caop-03.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die Vorlage, die Sie zum Erstellen der neuen Seite verwenden möchten, und klicken/tippen Sie dann auf **Weiter**, um fortzufahren.

   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![caop-04](assets/caop-04.png)

1. Im letzten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Geben Sie auf den drei Registerkarten die [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) ein, die Sie der neuen Seite zuweisen möchten, und klicken bzw. tippen Sie dann auf **Erstellen**, um die Seite zu erstellen.

   * Verwenden Sie die **Rücktaste**, um zur Vorlagenauswahl zurückzukehren.

   Die Schlüsselfelder sind:

   * **Titel**:

      * Dieser wird den Benutzenden angezeigt und ist obligatorisch.

   * **Name**:

      * Mit diesem Wert wird der URI generiert. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet.
      * Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen entsprechend den Konventionen](/help/sites-developing/naming-conventions.md) von AEM und JCR.

      * Die **Eingabe von ungültigen Zeichen** im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld markiert und eine erklärende Meldung angezeigt, die angibt, welche Zeichen entfernt/ersetzt werden müssen.

   >[!NOTE]
   >
   >Siehe [Seitenbenennungskonventionen](#page-naming-conventions)

   Zum Erstellen einer neuen Seite muss zumindest der **Titel** angegeben werden.

   ![caop-05](assets/caop-05.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**):

   ![chlimage_1-118](assets/chlimage_1-118.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite erstellen und dabei einen in diesem Verzeichnis bereits vorhandenen Namen verwenden, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `winter` bereits vorhanden ist, wird eine neue Seite `winter0` genannt.

1. Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

   ![caop-06](assets/caop-06.png)

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden - es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-authoring/launches-creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.

### Öffnen einer Seite zur Bearbeitung {#opening-a-page-for-editing}

Wenn Sie eine Seite erstellt haben bzw. in der Konsole zu einer bereits vorhandenen Seite navigiert sind, können Sie diese zur Bearbeitung öffnen:

1. Öffnen Sie die **Sites-Konsole**.
1. Navigieren Sie zu der Seite, die Sie bearbeiten möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Methoden aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigatingandselectionmode) und Symbolleiste

   Wählen Sie anschließend das Symbol **Bearbeiten** aus:

   ![screen_shot_2018-03-22at105355](assets/screen_shot_2018-03-22at105355.png)

1. Die Seite wird geöffnet und Sie können [die Seite bearbeiten](/help/sites-authoring/editing-content.md#touchoptimizedui).

>[!NOTE]
>
>Das Navigieren zu anderen Seiten ist im Seiteneditor nur im Vorschaumodus möglich, da Links im Bearbeitungsmodus des Seiteneditors nicht aktiv sind.

### Kopieren und Einfügen einer Seite {#copying-and-pasting-a-page}

Sie können eine Seite und alle zugehörigen Unterseiten an einen neuen Speicherort kopieren:

1. Navigieren Sie in der **Sites**-Konsole zu der Seite, die Sie kopieren möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigatingandselectionmode) und Symbolleiste

   Wählen Sie anschließend das Symbol **Seite kopieren** aus:

   ![screen_shot_2018-03-22at105425](assets/screen_shot_2018-03-22at105425.png)

   >[!NOTE]
   >
   >Wenn Sie sich im Auswahlmodus befinden, wird dieser automatisch beendet, sobald die Seite kopiert wird.

1. Navigieren Sie zum Speicherort, an dem Sie die neue Kopie der Seite speichern möchten.
1. Das Symbol **Einfügen** ist mit einem Dropdown-Pfeil direkt rechts verfügbar:

   ![Einfügen](assets/paste-without-children.png)

   Wählen Sie eine der folgenden Möglichkeiten aus:
   * Wählen Sie das Symbol **Einfügen** aus: An dieser Stelle wird eine Kopie der Originalseite und etwaiger untergeordneter Seiten erstellt.
   * Wählen Sie den Dropdown-Pfeil aus, um die Option **Ohne untergeordnete Elemente einfügen** anzuzeigen. An dieser Stelle wird eine Kopie der Originalseite erstellt. Untergeordnete Seiten werden nicht kopiert.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort kopieren, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

### Verschieben oder Umbenennen einer Seite {#moving-or-renaming-a-page}

>[!NOTE]
>
>Das Umbenennen einer Seite unterliegt auch den [Seitenbenennungskonventionen](#page-naming-conventions) beim Angeben des neuen Seitennamens.

>[!NOTE]
>
>Eine Seite kann nur an einen Speicherort verschoben werden, an dem die Vorlage, auf der die Seite basiert, zulässig ist. Weitere Informationen finden Sie unter [Formularverfügbarkeit](/help/sites-developing/templates.md#template-availability).

Die Vorgehensweise beim Verschieben oder Umbenennen einer Seite ist im Großen und Ganzen gleich und beide Aktionen werden von demselben Assistenten unterstützt. Dieser Assistent hilft Ihnen bei den folgenden Aktionen:

* Umbenennen einer Seite, ohne sie zu verschieben.
* Verschieben der Seite, ohne sie umzubenennen.
* Verschieben und gleichzeitiges Umbenennen der Seite.

AEM bietet die Möglichkeit, interne Links zu aktualisieren, die zu einer Seite führen, die umbenannt oder verschoben wird. Dies kann seitenweise erfolgen, um volle Flexibilität zu bieten.

1. Navigieren Sie zu der Seite, die Sie verschieben möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigatingandselectionmode) und Symbolleiste

   Wählen Sie anschließend das Symbol **Verschieben** für die Seite aus:

   ![screen_shot_2018-03-22at105534](assets/screen_shot_2018-03-22at105534.png)

   Dadurch wird der Assistent zum Verschieben von Seiten geöffnet.

1. Im Schritt **Umbenennung** des Assistenten haben Sie folgende Möglichkeiten:

   * Geben Sie den Namen an, den die Seite nach dem Verschieben aufweisen soll, und klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen.

   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![caop-07](assets/caop-07.png)

   Der Seitenname kann unverändert bleiben, wenn Sie die Seite nur verschieben.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

1. Im Schritt **Ziel auswählen** des Assistenten können Sie entweder:

   * Die [Spaltenansicht](/help/sites-authoring/basic-handling.md#column-view) verwenden, um zum neuen Speicherort für die Seite zu navigieren:

      * Wählen Sie das Ziel für die Seite aus, indem Sie auf die Miniatur des Ziels klicken.
      * Klicken Sie auf **Weiter**, um fortzufahren.

   * Auf **Zurück** klicken, um zur Angabe des Seitennamens zurückzukehren.

   >[!NOTE]
   >
   >Standardmäßig wird das übergeordnete Element der Seite, die Sie verschieben/umbenennen, als Ziel ausgewählt.

   ![caop-08](assets/caop-08.png)

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

1. Wenn die Seite verknüpft ist oder darauf verwiesen wird, werden die Details im Schritt **Anpassen/Erneut veröffentlichen** aufgeführt.

   Sie können angeben, welche Verweise ggf. angepasst und neu veröffentlicht werden sollen.

   >[!NOTE]
   >
   >Wenn die Seite weder verknüpft ist noch darauf verwiesen wurde, ist dieser Schritt nicht verfügbar.

   ![caop-09](assets/caop-09.png)

1. Wenn Sie **Verschieben** auswählen, wird der Vorgang abgeschlossen und Ihre Seite verschoben bzw. umbenannt.

>[!NOTE]
>
>Wenn die Seite bereits veröffentlicht wurde, wird das Veröffentlichen durch Verschieben der Seite automatisch rückgängig gemacht. Standardmäßig wird sie nach Abschluss des Verschiebevorgangs erneut veröffentlicht. Dies lässt sich jedoch ändern, indem Sie im Schritt **Anpassen/Erneut veröffentlichen** das Kontrollkästchen **Neu veröffentlichen** deaktivieren.

>[!NOTE]
>
>Wenn es keine Verweise auf die Seite gibt, wird der Schritt **Anpassen/Erneut veröffentlichen** übersprungen.

#### Asynchrone Aktionen {#asynchronous-actions}

Seitenverschiebungsaktionen werden immer asynchron verarbeitet, sodass Sie ungehindert mit der Erstellung in der Benutzeroberfläche fortfahren können.

* Der Benutzer muss definieren, wann der asynchrone Vorgang ausgeführt werden soll.
   * **Jetzt** startet die Ausführung des asynchronen Auftrags sofort.
   * **Später** erlaubt es dem Benutzer zu definieren, wann der asynchrone Auftrag starten wird.

  ![Asynchrone Seitenverschiebung](assets/asynchronous-page-move.png)

Der Status asynchroner Aufträge kann im Dashboard [**Status asynchroner Aufträge**](/help/sites-administering/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) unter **Globale Navigation** > **Tools** > **Vorgänge** > **Aufträge** überprüft werden.

>[!NOTE]
>
>Weitere Informationen zur asynchronen Auftragsverarbeitung und zum Konfigurieren der Grenzwerte für Verschiebungs- und Umbenennungsaktionen für Seiten finden Sie im Dokument [Asynchrone Aufträge](/help/sites-administering/asynchronous-jobs.md) im Administrations-Benutzerhandbuch.

>[!NOTE]
>
>Für die asynchrone Seitenverschiebung ist AEM 6.5.3.0 oder höher erforderlich.

### Löschen einer Seite {#deleting-a-page}

1. Navigieren Sie zu der Seite, die Sie löschen möchten.
1. Wählen Sie mit dem [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) die gewünschte Seite aus, bevor Sie in der Symbolleiste die Option **Löschen** auswählen:

   ![screen_shot_2018-03-22at105622](assets/screen_shot_2018-03-22at105622.png)

   >[!NOTE]
   >
   >Als Sicherheitsmaßnahme ist das Symbol **Löschen** nicht per Schnellzugriff verfügbar.

1. Ein Bestätigungsdialogfeld wird angezeigt.

   * Mit **Abbrechen** können Sie den Vorgang abbrechen
   * Mit **Löschen** bestätigen Sie die Aktion.

      * Wenn die Seite keine Verweise enthält, wird sie gelöscht.
      * Wenn die Seite Referenzen enthält, werden Sie in einem Meldungsfeld darüber informiert, dass **auf eine oder mehrere Seiten verwiesen wird.** Sie können **Löschen erzwingen** oder **Abbrechen** auswählen.

>[!NOTE]
>
>Wenn eine Seite bereits veröffentlicht ist, wird ihre Veröffentlichung vor dem Löschen automatisch rückgängig gemacht.

### Sperren einer Seite {#locking-a-page}

Sie können entweder in einer Konsole oder beim Bearbeiten einer Seite [eine Seite sperren/entsperren](/help/sites-authoring/editing-content.md#locking-a-page). An beiden Stellen werden auch Informationen zu gesperrten Seiten angezeigt.

![screen_shot_2018-03-22at105713](assets/screen_shot_2018-03-22at105713.png) ![screen_shot_2018-03-22at105720](assets/screen_shot_2018-03-22at105720.png)

### Erstellen eines neuen Ordners {#creating-a-new-folder}

Sie können Ordner erstellen, um Ihre Dateien und Seiten zu organisieren.

>[!NOTE]
>
>Ordner unterliegen ebenfalls den [Seitenbenennungskonventionen](#page-naming-conventions), wenn ein neuer Ordnername angegeben wird.

>[!CAUTION]
>
>* Ordner können nur direkt unter **Sites** oder unter anderen Ordnern erstellt werden. Sie können nicht unter einer Seite erstellt werden.
>* Für einen Ordner können folgende Standardaktionen ausgeführt werden: Verschieben, Kopieren, Einfügen, Löschen, Veröffentlichen, Rückgängigmachen der Veröffentlichung und Anzeigen/Bearbeiten von Eigenschaften.
>* Ordner sind in einer Live Copy nicht als Auswahl verfügbar.
>

1. Öffnen Sie die **Sites**-Konsole und navigieren Sie zum gewünschten Speicherort.
1. Um die Optionsliste zu öffnen, wählen Sie **Erstellen** in der Symbolleiste aus.
1. Wählen Sie **Ordner** aus, um das Dialogfeld zu öffnen. Hier können Sie den **Namen** und den **Titel** eingeben:

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Wählen Sie **Erstellen**, um den Ordner zu erstellen.
