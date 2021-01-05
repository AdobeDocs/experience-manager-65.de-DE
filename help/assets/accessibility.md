---
title: Barrierefreiheit in  [!DNL Experience Manager Assets]
description: Erkennen Sie, wie Barrierefreiheitsfunktionen in [!DNL Adobe Experience Manager] 6.5 [!DNL Assets] Benutzern mit Behinderungen helfen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e056d25cf16d79e8eadc80b9cb17b60b2ba8d7e1
workflow-type: tm+mt
source-wordcount: '1919'
ht-degree: 49%

---


<!--
Possible topics to cover in this article are below.

* Compile a list of enhancements done in the last ~1 year.
* Showcase a few prominent use cases (search?) in a screencast.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.
* List all UIs that are keyboard navigable.
* Unified list of the product tasks supported, such as, search assets, download assets, add or editing metadata, use DM Viewers, etc.
* Do we need to add support matrix of user tasks with browser and screen reader combinations. Everything may not work in all browsers and/or using all screen readers.
* Any exceptions that users should be aware of. It may help to call out (it may be done in ACR) what tasks are NOT supported.
* CTAs – what's next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Link to a11y-specific online methods to report issues, seek support, or request enhancements, if any. Asked the a11y team on Slack.
-->

# Barrierefreiheitsfunktionen in [!DNL Adobe Experience Manager Assets] {#accessibility-in-aem-assets}

[!DNL Adobe Experience Manager] Ersteller und Herausgeber von Inhalten können beeindruckende Erlebnisse im Web bereitstellen. Adobe bemüht sich, die Schöpfer mit Behinderungen einzubeziehen, indem die Zugänglichkeit von [!DNL Experience Manager] verbessert wird. Die Software wird kontinuierlich erweitert, um den Anforderungen aller Benutzertypen gerecht zu werden und die weltweiten Standards einzuhalten, zu denen Personen mit Sehbehinderungen, Hörgeschäften, Mobilitäten oder anderen Beeinträchtigungen gehören.

[!DNL Experience Manager] veröffentlicht Konformitätsinformationen, die die Standards, die es einhält, beschreiben, die Barrierefreiheitsmerkmale des Produkts skizzieren und den Grad der Konformität beschreiben. Die Berichte zur Barrierefreiheitskonformität helfen [!DNL Experience Manager] Benutzern, den Grad der Einhaltung verschiedener Standards zu verstehen. Die Erweiterungen in [!DNL Assets] ermöglichen es allen Benutzern, die Schnittstellen einfach über Tastatur, Bildschirmlesehilfen, Vergrößerungen und andere Hilfstechnologien zu verwenden.

[!DNL Experience Manager] bietet variierende Unterstützung für die folgenden Standards:

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Überarbeiteter Abschnitt 508 des Rehabilitationsgesetzes](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) von W3C](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Informationen zum Lesen eines Berichts mit Details zur Kompatibilitätsstufe finden Sie auf der Seite [Barrierefreiheitskonformitätsbericht](https://www.adobe.com/accessibility/compliance.html) (ACR).

Informationen zum Zugriff auf [!DNL Dynamic Media] finden Sie unter [Barrierefreiheit in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).

## Hilfstechnologien {#at-support}

Benutzer mit Behinderungen sind häufig auf Hardware und Software angewiesen, um auf Webinhalte zuzugreifen und Softwareprodukte zu verwenden. Diese Werkzeuge werden als Hilfstechnologien bezeichnet. [!DNL Experience Manager Assets] kann mit folgenden Arten von Hilfstechnologien (AT) arbeiten, wenn die Kernfunktionen der Software verwendet werden:

* Bildschirmlesehilfen und Vergrößerungssoftware.
* Spracherkennungssoftware.
* Verwendung der Tastatur – Navigation und Tastaturbefehle.
* Hilfs-Hardware, einschließlich Switch-Steuerungen, aktualisierbarer Braille-Displays und anderer Computer-Eingabegeräte.
* Tools zum Vergrößern der Benutzeroberfläche.

## [!DNL Experience Manager Assets]-Anwendungsfälle, die möglich sind {#accessible-assets-use-cases}

In [!DNL Experience Manager] decken die Funktionen für Barrierefreiheit zwei wichtige Anforderungen von [!DNL Experience Manager]-Benutzern und ihren Kunden ab.

* Für Entwickler und Ersteller von Inhalten gibt es Funktionen zum Erstellen und Veröffentlichen von barrierefreien Inhalten, die wiederum von ihren Kunden und Website-Besuchern genutzt werden. Menschen mit Behinderungen nutzen die Inhalte mithilfe von Hilfstechnologien. Weitere Informationen finden Sie unter [Richtlinien für Barrierefreiheit im Web](/help/managing/web-accessibility.md).
* [!DNL Experience Manager] ermöglicht es Benutzern und Administratoren mit Behinderungen außerdem, auf die Benutzeroberfläche und Steuerelemente zuzugreifen, um Inhalte zu erstellen und zu verwalten. Menschen mit Behinderungen können mithilfe von Hilfstechnologien die [!DNL Assets]-Funktion navigieren, nutzen und verwalten.

Die Kernfunktionen in [!DNL Assets] sind leichter zugänglich als zuvor und werden regelmäßig aktualisiert, um die Erfüllung globaler Standards zu verbessern. Die CRUD-Vorgänge in [!DNL Assets] verfügen über einen gewissen Grad an Barrierefreiheit. DAM-Workflows wie das Hinzufügen, Verwalten, Suchen und Verteilen von Assets sind durch Tastaturbefehle, Sprachausgaben, Farbkontrast usw. barrierefrei.

## Unterstützung für die Verwendung der Tastatur {#keyboard-use}

Viele Elemente der Benutzeroberfläche, die mit einem Zeiger angeklickt oder bearbeitet werden können, können auch mit der Tastatur genutzt werden. Mithilfe einer Tastatur können Benutzer auf Elemente der Benutzeroberfläche fokussieren und eine gewünschte Aktion ausführen. Benutzer können direkt Tastaturbefehle verwenden, um einen Befehl oder eine Aktion auszulösen, ohne sich auf UI-Elemente konzentrieren zu müssen. Beispielsweise können Benutzer die Zeitleiste eines Assets auf der linken Seite der Benutzeroberfläche öffnen, indem sie mithilfe einer Tastatur zum Steuerelement der Benutzeroberfläche navigieren, `Return` auswählen und `Alt + 2`-Tastaturbefehl auswählen.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Tastaturbefehle in [!DNL Assets] {#keyboard-shortcuts}

Die folgenden Aktionen in [!DNL Assets] funktionieren mit den aufgelisteten Tastaturbefehlen. Die meisten Tastaturbefehle, die für [!DNL Experience Manager]-Konsolen gelten, gelten auch für [!DNL Assets]. Siehe [Tastaturbefehle für Konsolen](/help/sites-authoring/keyboard-shortcuts.md#keyboard-shortcuts). Erfahren Sie, wie Sie [die Tastaturbefehle aktivieren oder deaktivieren](/help/sites-authoring/keyboard-shortcuts.md#deactivating-keyboard-shortcuts).

| Benutzeroberfläche oder Szenario | Tastaturbefehl | Aktion |
|---|---|---|
| Spalten-Ansicht in der [!DNL Assets]-Benutzeroberfläche | Nach-oben- und Nach-unten-Taste | Navigieren Sie zu Dateien und Ordnern in derselben Hierarchie. |
| Spalten-Ansicht in der [!DNL Assets]-Benutzeroberfläche | Nach-links- und Nach-rechts-Taste | Navigieren Sie zu Dateien und Ordnern über oder unter dem aktuellen Ordner. |
| Durchsuchen von Ordnern in [!DNL Assets] | `/` | Rufen Sie die Suche auf, indem Sie das Omnisearch-Feld öffnen. |
| [!DNL Assets] Konsole | ` | Seitenleisten umschalten |
| [!DNL Assets] Konsole | `Alt + 1` | Öffnen Sie die Inhaltsstruktur. |
| [!DNL Assets] Konsole | `Alt + 2` | Öffnen Sie die linke Leiste [!UICONTROL Navigation]. |
| [!DNL Assets] Konsole | `Alt + 3` | Zeigen Sie die [!UICONTROL Zeitleiste] eines ausgewählten Assets an. |
| [!DNL Assets] Konsole | `Alt + 4` | Öffnen Sie Live Copy-Verweise des ausgewählten Assets. |
| [!DNL Assets] Konsole | `Alt + 5` | Suchen und Suchen von Beginn im ausgewählten Ordner. |
| Asset oder Ordner ist ausgewählt | Rücktaste | Löschen Sie das ausgewählte Asset oder den ausgewählten Ordner. |
| Asset oder Ordner ist ausgewählt | `p` | Öffnen Sie die Eigenschaftenseite des ausgewählten Assets. |
| Asset oder Ordner ist ausgewählt | `e` | Bearbeiten Sie das ausgewählte Asset. |
| Asset oder Ordner ist ausgewählt | `m` | Verschieben Sie das ausgewählte Asset. |
| Asset oder Ordner ist ausgewählt | `Ctrl + c` | Kopieren Sie das ausgewählte Asset. |
| Asset oder Ordner ist ausgewählt | `Esc` | Deaktivieren Sie die Auswahl. |
| Das Dialogfeld wird geöffnet und befindet sich im Fokus. | `Esc` | Schließen Sie das Dialogfeld. |
| Innerhalb eines Ordners in DAM | `Ctrl + v` | Fügen Sie das kopierte Asset ein. |
| [!DNL Assets] Konsole | `Ctrl + A` | Wählen Sie alle Assets aus. |
| Asset-Eigenschaftenseiten | `Ctrl + S` | Speichern Sie die Änderungen. |
| [!DNL Assets] Konsole | `?` | Zeigen Sie eine Liste der Tastaturbefehle an. |

## Anmelden bei und Navigieren in der [!DNL Assets]-Benutzeroberfläche {#login}

Benutzer können die Tastatur verwenden, um zum Anmeldefeld zu navigieren und es auszufüllen und sich anzumelden. Die Fehlermeldungen aufgrund falscher Kombinationen aus Benutzername und Kennwort auf der Anmeldeseite werden von Bildschirmlesehilfen jedes Mal, wenn der Fehler auftritt, angekündigt.

Nach der Anmeldung können DAM-Benutzer mithilfe der Tastatur in der [!DNL Assets]-Benutzeroberfläche navigieren. Die Elemente der Benutzeroberfläche, wie die linke Leiste, die Menüs, das Profil, die Suchleiste, die Dateien und Ordner sowie die Administrations- und Konfigurationseinstellungen, können über die Tastatur navigiert werden. Die Navigationsreihenfolge der Tastatur verläuft von links nach rechts und von oben nach unten. Beim Navigieren mit einer Tastatur wird eine Option, die im Fokus aktiviert werden kann, mit einem besseren Farbkontrast hervorgehoben und von einer Bildschirmlesehilfe kommentiert. Gegebenenfalls wird der Status der fokussierten Optionen im Menü - z. B. erweitert, reduziert und gemischt - von einer Bildschirmlesehilfe angekündigt. Darüber hinaus gibt die Bildschirmlesehilfe den Zweck der Option an, mit der eine Aktion durchgeführt werden kann, anstatt beispielsweise das Erscheinungsbild oder die Platzierung der Benutzeroberfläche.

Wenn ein Benutzer die Profil- oder Hilfe-Option aus dem Menü erweitert, gibt die Bildschirmlesehilfe die entsprechende Option oder den entsprechenden Status an. Wenn ein Benutzer die Benutzerprofiloption erweitert, können die verfügbaren Optionen über eine Tastatur ausgewählt werden. Ein Administrator kann beispielsweise einen anderen Benutzer imitieren. Wenn ein Benutzer über die Option [!UICONTROL Hilfe] nach einer Zeichenfolge sucht, gibt ein Erzähler &quot;Suchhilfe&quot;an, dass eine Suche ausgeführt wird.

<!-- TBD: Removing for now. Add a more informative video later. Host it on tv.adobe

![Keyboard navigation of top options in [!DNL Experience Manager] user interface](assets/keyboard-navigation-in-aem.gif)

*Figure: Navigating through the options at the top of [!DNL Experience Manager] user interface using `Tab` key.*
-->

## Durchsuchen von Assets und Ansicht der zugehörigen Informationen {#browse}

In der [!DNL Assets]-Benutzeroberfläche können Benutzer die Tastatur verwenden, um die Liste vorhandener digitaler Assets im DAM-Repository zu durchsuchen, ein Asset als Vorschau anzuzeigen oder herunterzuladen, die erzeugten Ausgabedarstellungen anzuzeigen, Ansichten zu wechseln, die Chronik und den Versionsverlauf anzuzeigen, Kommentare und Verweise anzuzeigen sowie Metadaten anzuzeigen und zu verwalten.

<!-- TBD: Not sure about the following list items mean:

In [!DNL Experience Manager] header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog wasn't accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Beim Durchsuchen des Asset-Repositorys wird Barrierefreiheit durch folgende Funktionen erleichtert:

* Die Sprachausgabe trägt Textalternativen vor, die den Zweck oder die Funktionalität von Symbolen anstelle ihrer Namen darstellen.
* Benutzer können die interaktiven Optionen der Benutzeroberfläche in der Referenzliste der Assets mithilfe von Tastenkombinationen aufrufen und fokussieren.
* Die Elemente in den einzelnen Zeilen der Listenansicht werden von Sprachausgaben als Elemente derselben Zeile vorgetragen.
* Wenn Sie mit der `Tab`-Taste navigieren, kann der Fokus zur Schließoption in der Vorschau wechseln.
* Wenn Sie zum Durchsuchen die Tastatur verwenden, weisen die hervorgehobenen ausführbaren Optionen der Benutzeroberfläche einen auffälligeren visuellen Fokus mit erhöhtem Kontrast auf. Dadurch wird der fokussierte Bereich für den Benutzer leichter erkennbar.
* Bei Verwendung der `Esc`-Taste zum Entfernen der Schnellzugriffssymbole aus der Miniaturansicht wird der Tastaturfokus nicht vom zuletzt fokussierten Element entfernt.
* Wenn ein Asset ausgewählt ist, wird durch Auswahl des Tastaturbefehls `Alt + 4` die Liste [!UICONTROL References] in der linken Leiste geöffnet. Mit der `Tab`-Taste können Benutzer durch die Nicht-Null-Referenzeinträge navigieren. Wenn Sie nur die Nicht-Null-Referenzeinträge durchsuchen, sparen Sie auch Arbeitsaufwand und Tastenanschläge.
* Kommentare zu einem Asset sind in der Asset-Zeitleiste verfügbar. Es ist verfügbar, wenn über eine Tastatur oder einen Tastaturbefehl auf die linke Leiste zugegriffen wird.
* [!UICONTROL Die ] Einstellungen für Ansichten  [!DNL Experience Manager] sind über eine Tastatur verfügbar. Die Benutzer können mithilfe der Pfeiltasten durch die verfügbaren Kartengrößen navigieren und durch die Pfeiltasten navigieren, um durch andere Elemente in der Ansicht &quot;Einstellungen für Ansichten&quot;zu navigieren und andere Elemente festzulegen.

<!-- TBD: Gradually, as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?
-->

## Verwalten digitaler Assets {#manage-assets}

Viele Asset-Management-Aufgaben wie CRUD-Vorgänge, das Herunterladen eines Assets und das Hinzufügen von Metadaten stehen in unterschiedlichem Umfang zur Verfügung. [!DNL Assets] ermöglicht Ihnen die Ausführung der Aufgaben mithilfe verschiedener Hilfstechnologien, z. B. einer Bildschirmlesehilfe und einer Tastatur.

Sehen Sie sich ein Video an, um zu erfahren, wie Sie mit der Tastatur das [Repository durchsuchen und ein Asset herunterladen](https://youtu.be/K3dgqMRQJys) können.

Bei Metadatenvorgängen, die in der Regel von Rollen wie Marketing-Experten und Administratoren ausgeführt werden, verbessern folgende Funktionen die Barrierefreiheit:

* Die Option [!UICONTROL Speichern und schließen][!UICONTROL  auf der Seite „Asset-Eigenschaften“ kann jetzt über die Tastatur aufgerufen werden.]
* Bildschirmlesehilfen geben die Optionen zum Löschen der ausgewählten Tags auf der Registerkarte [!UICONTROL Einfach] des Assets [!UICONTROL Eigenschaften] an.
* Benutzer können das Popup-Dialogfeld &quot;Datepicker&quot;mit einer Tastatur verwenden. Das Element der Benutzeroberfläche &quot;Datepicker&quot;dient zum Festlegen von Ein- und Ausschaltzeiten und zum Auswählen des Datums.
* Die Funktion zum Ziehen mit der Tastatur funktioniert in [!UICONTROL Metadaten-Schema-Editor] im Durchsuchen-Modus der Bildschirmlesehilfe korrekt.
* Ein Benutzer kann den Fokus mithilfe der Tastatur in das Feld Hinzufügen Benutzer oder Gruppe unter [!UICONTROL Geschlossene Benutzergruppe] auf der Registerkarte [!UICONTROL Berechtigungen] des Ordners [!UICONTROL Eigenschaften] verschieben.

## Suchen nach digitalen Assets {#search-assets}

Eine schnelle und nahtlose Suche nach Assets sorgt für eine höhere Inhaltsgeschwindigkeit. Anwendungsfälle mit hoher Inhaltsgeschwindigkeit sind Teil der Kernfunktionalität von [!DNL Assets]. Um eine Suche über die Omnisearch-Suchleiste zu starten, können Benutzer die Tastaturbefehle `/` oder `Tab` zusammen mit Sprachausgaben verwenden, um die Suchoption rasch zu finden. Die Bildschirmlesehilfe beschreibt den Namen der Option als &quot;Suchschaltfläche&quot;, wenn der Fokus auf der Suchoption ![search option](assets/do-not-localize/search_icon.png) liegt. Benutzer können `Return` auswählen, um das Feld &quot;Omniture Search&quot;zu öffnen. Die Sprachausgabe sagt nicht nur das in das Suchfeld eingegebene Keyword, sondern auch die von [!DNL Experience Manager Assets] angebotenen Vorschläge an. Benutzer können eine Kombination aus Pfeiltasten, `Return` und `Tab` nutzen, um auf die verschiedenen Optionen zuzugreifen und eine Suche auszulösen.

Die Suchfunktion ist über folgende Funktionen verfügbar:

* Der Seitentitel, so er einer Sprachausgabe zur Verfügung steht, hilft dabei, die Seite als Asset-Suchseite zu identifizieren.
* Benutzer suchen im Feld Omniture nach Assets. Benutzer können sie entweder mit der Tastaturnavigation oder dem Tastaturbefehl `/` öffnen.
* Beginn können den Suchbegriff eingeben und dann die Auto-Vorschläge mit den Pfeiltasten auswählen. Markierte Vorschläge können mit der `Return`-Taste ausgewählt werden und Assets werden nach der ausgewählten Empfehlung gesucht.
* Bildschirmlesehilfen können die Kontrollkästchen mit gemischtem Status identifizieren und ankündigen (bei denen, wenn Sie nicht alle verschachtelten Kontrollkästchen auswählen, die ersten Ebenen nicht ausgewählt sind und durchgestrichen werden), wenn die Suchergebnisse gefiltert werden, im Bedienfeld &quot;Filter&quot;angezeigt werden.
* Der Benutzerfokus wechselt zu den Suchoptionen, sobald das Omnisearch-Suchfeld geschlossen wird.

Beim Filtern der Suchergebnisse:

* Die Suchergebnisseite hat einen informativen Titel, der Benutzern ein besseres Verständnis der Sprachausgaben vermittelt.
* Eine Sprachausgabe sagt die Optionen im Suchfilter als erweiterbare Akkordeons an.
* Prädikate mit Optionen für gemischte Status werden von Bildschirmlesehilfen angekündigt.

## Freigeben von Assets {#share-assets}

<!-- TBD: Anything about accessibility in DA, BP? AAL team confirmed that there's no content for AAL a11y on helpx.
-->

Beim Freigeben von Assets verbessern folgende Funktionen die Barrierefreiheit:

* Benutzer können den Fokus mithilfe der Tastatur in den Feldern „Suchen“ und „E-Mail-Adresse hinzufügen“ im Dialogfeld „Link-Freigabe“ verschieben.

* Wenn Sie im Dialogfeld für die Link-Freigabe im Durchsuchen-Modus navigieren,

   * Die Tabelleninformationen sollten beim Laden des Dialogfelds nicht erwähnt werden.
   * kann die Sprachausgabe zu allen aufgelisteten Vorschlägen navigieren.
   * liest die Sprachausgabe die für die Felder „E-Mail-Adresse hinzufügen“ und „Suchen“ angezeigten Vorschläge vor.

## Barrierefreie Dokumentation {#accessible-docs}

[!DNL Experience Manager] bietet zugängliche Dokumentation für Menschen mit Behinderungen. Die folgenden Hilfen helfen Ihnen, derzeit verfügbare Inhalte barrierefrei zu machen, während Adobe die Vorlage und den Inhalt weiter verbessert:

* Sprachausgaben können den Text vorlesen.
* Bilder und Illustrationen weisen alternativen Text auf.
* Tastaturnavigation ist möglich.
* Kontrastverhältnisse tragen dazu bei, bestimmte Teile der Dokumentations-Website hervorzuheben.

## Feedback {#a11y-feedback}

Verwenden Sie die folgenden Methoden, um Feedback zu geben, Fragen zu stellen und Produktverbesserungen in Bezug auf die Barrierefreiheit anzufordern:

* Füllen Sie das Formular unter [www.adobe.com/accessibility/feedback.html](https://www.adobe.com/accessibility/feedback.html) aus.
* Senden Sie uns eine E-Mail an access@adobe.com.

>[!MORELIKETHIS]
>
>* [Barrierefreiheitsfunktionen in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).
>* [Versionshinweise zu den Verbesserungen, die in jeder Service Pack-Version](/help/release-notes/new-features-latest-service-pack.md) vorgenommen wurden.
>* [[!DNL Adobe Experience Manager] Barrierefreiheit](/help/managing/web-accessibility.md).
>* [Konformitätsberichte (ACR) und VPAT-Auflistung für Adoben](https://www.adobe.com/accessibility/compliance.html).

