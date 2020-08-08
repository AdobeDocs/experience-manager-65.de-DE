---
title: Adobe Experience Manager 6.5 Service Pack Release Notes
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Service Pack 5.
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: ca965d8495c0460b2b6bc5e08d8818b91f9fcdee
workflow-type: tm+mt
source-wordcount: '4531'
ht-degree: 7%

---


# Adobe Experience Manager 6.5 Service Pack Release Notes {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | Adobe Experience Manager 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.5.0 |
| Typ | Service Pack-Version |
| Datum           | June 04, 2020 |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) |

## What&#39;s included in Adobe Experience Manager 6.5.5.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.5.0 is an important update that includes new features, key customer requested enhancements, and performance, stability, and security improvements, that are released since the general availability of 6.5 release in **April 2019**. It can be installed on top of Adobe Experience Manager 6.5.

Zu den wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5.5.0 eingeführt wurden, zählen:

* Customize the column names that display in Adobe Experience Manager Inbox.

* Improved accessibility in various areas in Experience Manager Web Content Management (WCM) such as Page Editor, Core Components, RTE, and Admin user interface.

* Save an [!DNL Interactive Communication] as a draft.

* Unterstützung für [!DNL Oracle WebLogic 12] Experience Manager Forms on JEE.

* Verbesserte Ausnahmebehandlung im [!DNL Adobe Experience Manager Assets] Benutzeroberflächenfluss.

* Um die Veröffentlichungs-URL für das Dynamic Media Scene7 abzurufen, `getRemoteAssetPublishURL` wird der `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi` Benutzeroberfläche eine neue Methode hinzugefügt.

* [Barrierefreiheitsverbesserungen](#assets-6550) in Übereinstimmung mit [!DNL Adobe Experience Manager Assets] den Web Content Accessibility Guidelines (WCAG).

* Removed Package Share integration from within Adobe Experience Manager.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.3 aktualisiert.

For complete list of features, key highlights, key features introduced in Experience Manager 6.5 service pack 5, see [What&#39;s new in Adobe Experience Manager 6.5 Service Pack 5](new-features-latest-service-pack.md) .

Im Folgenden finden Sie die Liste der Fehlerbehebungen in Version [!DNL Experience Manager] 6.5.5.0.

### [!DNL Sites] {#sites-6550}

* Experience Manager Sites provides an option to publish or unpublish a page from its alias. The option does not work (NPR-33415).
* Wenn ein Layout-Container aus einer Vorlage mit mehreren Vorlagen gelöscht wird, wird die Vorlage nicht korrekt dargestellt (NPR-33347).
* Wenn eine Experience Manager-Siteseite Teil eines großen Inhaltssatzes mit mehreren Live-Kopien ist, kann die Vorschau des Seitenversionsverlaufs nicht geladen werden (NPR-33311).
* Wenn Sie den Befehl &quot;Verschieben&quot;verwenden, um eine Experience Manager-Siteseite umzubenennen, wird der Seitentitel nicht aktualisiert (NPR-33264).
* Wenn Sie Seiten durch die Ansicht verschieben, werden die Spalten ausgeblendet (NPR-33216).
* Wenn der Name einer lokalen Komponente in einer Sprachkopie identisch mit dem Namen einer Komponente im Entwurf ist und die Komponente aus dem Entwurf herausgegeben wird, `_msm_moved` wird dem Namen der lokalen Komponente kein Begriff hinzugefügt (NPR-33208).
* Das Seitenumleitungs-Servlet hängt .html an eine Experience Manager-Sites-URL an, bei der ResourceType nicht angegeben ist `cq:Page` (NPR-33176).
* When you paste a subtree, there is no option to decide if corresponding subpages are to be pasted or not (NPR-33149).
* The number of results in live usages of a component is limited to number 49 (NPR-33058).
* When you base a Content Fragment on a schema and it contains a mandatory text area or a path field, the Content Fragment fails to save (NPR-33007).
* Wenn Sie eine benutzerdefinierte Komponente mit der Standardkomponente &quot;Erlebnisfragment&quot;erstellen und sie auf den Seiten &quot;Experience Manager-Sites&quot;verwenden, zeigt Experience Manager keine Verweise (Verwendungszwecke) für die benutzerdefinierte Komponente (NPR-32852) an.
* Wenn Sie einen Ordner mit einer großen Anzahl von Verweisen umbenennen, werden viele Verweise auf den Ordner nicht aktualisiert (NPR-32765).
* Wenn Sie die Quellbearbeitungsoption aktivieren, steht sie für Inline-Vollbildoptionen zur Verfügung, bleibt aber für das Bearbeiten des Dialogfelds und der Vollbildoptionen des Rich-Text-Editors (NPR-32763) nicht mehr verfügbar.
* Wenn Sie über ein Mehrfeld verfügen und es ein erforderliches Feld (wie ein Dropdown-Feld oder ein Pfadfeld) in den Seiteneigenschaften eines Blueprints enthält, werden die Seiteneigenschaften der Live-Kopie nicht gespeichert (NPR-32751), wenn eine Seite, die ein solches Multifeld enthält, verkleinert wird.
* Bildschirmlesehilfen können die Überschriftenstruktur nicht zum Navigieren auf einer Seite verwenden. Darüber hinaus enthält die Registerkarte Komponenten die falsche Beschriftung (NPR-32648).
* Beim Paginieren werden nicht alle Elemente (NPR-32605) in der Erlebnisfragmentauswahl geladen.
* Autorenberechtigungen zum Lesen, Ändern, Erstellen und Löschen von Live-Kopien werden widerrufen. Jeder Autor musste explizit Lese- und Änderungsberechtigungen zum Verschieben von Seiten in einem Blueprint (NPR-32550) bereitstellen.
* Autoren von Inhalten können &quot;Launch&quot;nicht für eine Seite erstellen, die mit Adobe Analytics integriert ist (NPR-32548).
* Wenn ein Benutzer die Vererbung mit der Synchronisierung fortsetzt, wird die Live-Kopie der übergeordneten Seite nicht mit dem Entwurf synchronisiert und zeigt einen falschen Status an (NPR-32500).
* Das Laden der Editor-Seite für Experience Manager-Sites dauert mehr als 15 Sekunden (NPR-32413).
* In bestimmten Feldern wird die Option Vererbung abbrechen nicht angezeigt (NPR-32362).
* Wenn Sie einen Pfad für eine Erlebnisfragment-Komponente auswählen und das Kontrollkästchen &quot;Auswahldialogfeld öffnen&quot;aktivieren, werden Sie nicht zum ausgewählten Pfad im Pfadbrowser (NPR-32308) navigiert.
* Wenn Sie von Experience Manager 6.2 auf Experience Manager 6.5 aktualisieren, wird die Komponente Parsys der statischen Vorlagen nicht korrekt angezeigt. Die Höhe der Komponente Parsys ist auf 0 eingestellt und die darin enthaltenen Komponenten sind nicht sichtbar (NPR-33663).
* Wenn ein Benutzer einen Layout-Container kopiert und auf derselben Seite eingefügt hat, werden Komponenten in einem Layout-Container nicht angezeigt (NPR-33648).
* Dispatcher Health Check zeigt eine `Invalid cookie header` Warnmeldung in den Protokolldateien an (NPR-33629).
* XSS in PreferencesServlet (NPR-33438) reflektiert.
* Anonyme Benutzer können auf die Funktionen von CRX DE Lite zugreifen (GRANITE-27790).

### [!DNL Assets] {#assets-6550}

**Barrierefreiheitsverbesserungen in Experience Manager Assets**

* Es ist jetzt möglich, den Tastaturfokus auf die Liste [!UICONTROL Kommentare] und die Option zum [!UICONTROL Erstellen] von Versionskommentaren unter Neue Version  erstellen im [!UICONTROL Timeline] -Bedienfeld von Assets (NPR-33424) zu lenken.

* Es ist jetzt möglich, die [!UICONTROL Ansicht Einstellungen] für Assets zu erreichen und die Einstellungen im Dialogfeld [!UICONTROL Ansicht Einstellungen] mithilfe der Tastenkombinationen (NPR-33420) zu ändern.

* The list box popup of combo box (in various fields on different pages) now shows entries as a list of options that can be announced by screen readers (NPR-33516).

* Die Sortierfunktion sortierbarer Kopfzeilen (in Ansicht der Liste, Ansicht der [!UICONTROL Zeitschiene] und Seite Veröffentlichung [!UICONTROL verwalten] ) wird jetzt von Bildschirmlesehilfen angekündigt und die Sortiersteuerung auf Spaltenköpfen kann über die Tastatur aufgerufen werden (NPR-32979).

* Die anklickbaren Elemente wie Kommentarkarten, Versionsaktualisierungen, Kombinationsfelder und Chevron-Symbole von Menüs können jetzt mithilfe einer Tastatur (NPR-33514) fokussiert und damit interagiert werden.

* Funktionen (oder Aktionszweck) von Insight-Symbolen (für die Verwendung, Impressionen und Klicks) in der [!UICONTROL Insight-Ansicht] werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33513).

* Read-only form fields (for example disabled fields on [!UICONTROL Basic tab] of asset [!UICONTROL Properties]) are now focusable using keyboard (NPR-33493, CQ-4273031).

* Bezeichnungen in verschiedenen Eingabefeldern sind nun dauerhafte Bezeichnungen (also barrierefrei) und nicht nur Platzhalterbeschriftungen, die bei der Texteingabe verschwanden (NPR-33475).

* Verschiedene Überschriftenebenen (z. B. Seitentitel und Abschnittsüberschriften) werden nun als Überschriften mit unterschiedlichen Ebenen als Bildschirmlesehilfen-Benutzer wahrgenommen (NPR-33471).

* Interactive user interface elements, such as links and options (on header and zoom options of assets page, folder navigation), are now accessible using a keyboard (NPR-33468, CQ-4271412).

* Die [!UICONTROL Optionen]-, [!UICONTROL Scope]- und [!UICONTROL Workflows] -Fortschrittsindikatoren auf der Seite &quot;Veröffentlichung  verwalten&quot;werden jetzt von Bildschirmlesehilfen als Fortschrittsindikatoren anstelle von Registerkarten korrekt gelesen (NPR-33416).

* Die Farbe der Bewertungssymbole für Sterne (z. B. im [!UICONTROL Rating] -Bereich der Registerkarte &quot; [!UICONTROL Erweitert] &quot;in den Asset- [!UICONTROL Eigenschaften] oder in der Karten-Ansicht) wird geändert, damit der entsprechende Kontrast für Benutzer mit eingeschränkter Sichtbarkeit und ohne Farbwahrnehmung sichtbar ist (NPR-33414).

* Nach oben zeigender Pfeil neben dem Feld [!UICONTROL Kommentar] auf der Seite mit den Asset-Details können Sie jetzt mit den Tastaturbefehlen (NPR-33397) aufrufen.

* Die erweiterten und reduzierten Zustände des Dialogfelds [!UICONTROL Tags] über Asset- [!UICONTROL Eigenschaften] und linke Schienennavigation (in der Assets-Benutzeroberfläche) werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33396).

* Titles of all the browsed pages on [!DNL Adobe Experience Manager] Assets are now unique (NPR-33343).

* Beim Navigieren in der Baumstruktur werden jetzt verschiedene Elemente der Baumstruktur-Ansicht-Steuerung von Bildschirmlesehilfen korrekt angekündigt (NPR-33304).

* Different versions of assets in [!UICONTROL Timeline] view on assets details page are now accessible using keyboard keys (NPR-33283).

* Names of search suggestions appearing in Omnisearch combo box are now announced by screen readers when using search functionality (NPR-33280).

* Clickable elements and [!UICONTROL Go to link] in [!UICONTROL References rail] are now announced by screen readers as clickable elements (NPR-33278).

* Table structure information (such as row 1, cell 1, table) of [!UICONTROL Share Link] dialog is no more announced by screen readers, when the dialog opens (NPR-33268).

* The purpose of various combo box elements (such as Path field and option to open Selection dialog in Basic tab of asset Properties) are now correctly announced by screen readers (NPR-33235).

* Information that the rows in list view table are selectable is now communicated to screen reader users when keyboard focus is on them. Wenn ein Zeiger mit der Maus auf die Zeilen zeigt, geben die Bildschirmlesehilfen die Informationen an (NPR-33234).

* Options (having [!UICONTROL x]) to remove each of the selected tags below the [!UICONTROL Tags] field in [!UICONTROL Basic] tab of [!UICONTROL Properties] are now accessible to screen readers (NPR-33206).

* Calendar date picker is now focusable and actionable using keyboard by screen reader users and sighted keyboard users (NPR-33200).

* The toggle to switch between list view and card view now correctly exposes its functionality (of adjusting views) to screen reader (NPR-33069).

* Menu in the left rail is now accessible. Funktionalität und Zweck der Erweiterung des Menüs werden von Bildschirmlesehilfen entsprechend angekündigt (NPR-33068).

* Liste-Box und viele andere Benutzeroberflächenelemente sind jetzt für Benutzer ohne Sichtkontakt mit Bildschirmlesehilfen verfügbar. Die folgenden Informationen werden von Bildschirmlesehilfen (NPR-33040) angekündigt:

   * ob die Benutzereingabe für ein Element vor dem Senden des Formulars erforderlich ist.
   * ob ein Element nicht bearbeitbar ist.
   * whether a widget is selected or not.

* Die Option zum Öffnen der Filter-Seitenleiste kann jetzt über die Tastatur aufgerufen werden (NPR-32842, CQ-4273018).

* Check box control in column header of list view is now accessible and purpose of using the control is announced by screen readers (NPR-32722, NPR-33005).

* Die Felder für Stunden (HH) und Minuten (mm) in der Datumsauswahl im Kalender sind jetzt dauerhafte Beschriftungen anstelle von Platzhalterbeschriftungen und verschwinden nicht, wenn der Benutzer Text in diese Felder eingibt (NPR-32720).

* The links text of notifications (that appear after clicking the bell icon) is now announced to screen reader users, who use tab to access each link (NPR-32645).

* [!UICONTROL Select], [!UICONTROL Download], [!UICONTROL Properties], and [!UICONTROL More Actions] options on asset cards in [!UICONTROL Insights View] are now accessible using keyboard (NPR-32609).

* Visuell ausgeblendete Inhalte (z. B. Inhalte der Kopfzeilenmenüleiste in Suchergebnissen) werden von Bildschirmlesehilfen beim Zugriff über die Tastatur nicht mehr angekündigt (NPR-32606).

* Zweck der Beschriftungen für Kontrollen, die in der Kalenderdatumsauswahl in die nächsten und vorherigen Monate verschoben werden sollen, werden jetzt von Bildschirmlesehilfen (NPR-32604) angekündigt.

* Sternbewertungs-Symbole können jetzt mithilfe von Tastenkombinationen fokussiert und bearbeitet werden (NPR-32513).

* Functionality to control video volume is now accessible through tab (to focus on volume slider) and arrow keys (to adjust volume) on keyboard (NPR-32065).

* Der Zweck der Eingabefelder mit Untergrenze ([!UICONTROL Von]) und Obergrenze ([!UICONTROL Bis]) des Dateigrößenfilters wird nun nicht-seighted Screen Reader Users (NPR-32064) bekannt gegeben.

* Das Menü &quot; [!UICONTROL Sprachen] &quot;im Formular &quot; [!UICONTROL Erstellen und Übersetzen] &quot;steht jetzt Bildschirmlesehilfen im Durchsuchenmodus zur Verfügung (CQ-4293906).

* The [!UICONTROL References] panel is now accessible with following enhancements (NPR-33261, CQ-4293798):

   * In browse mode, screen reader focus no longer moves to hidden multiline edit fields under [!UICONTROL Site References], [!UICONTROL Asset References], [!UICONTROL Copies], and [!UICONTROL Form References] sections.

   * Bildschirmlesehilfen geben jetzt die Rolle der Elemente [!UICONTROL Site-Referenzen] und [!UICONTROL Sprachkopien] an.

   * Der Fokus von Bildschirmlesehilfen im Durchsuchen-Modus wechselt in einer aussagekräftigen Sequenz zu verschiedenen Elementen.

* [!UICONTROL Die Metadaten-Schema-Editor] -Seite und die zugehörigen Elemente sind jetzt über die Tastatur verfügbar und können mit Bildschirmlesehilfen verwendet werden (CQ-4290962, CQ-4272953).

* Der Zweck des `X` Symbols zum Entfernen der ausgewählten Tags wird jetzt von Bildschirmlesehilfen zusammen mit der Anzahl der ausgewählten Tags (CQ-4273017) angekündigt.

* Um Verwirrung bei Benutzern ohne Sehbehinderung mit Bildschirmlesehilfen zu vermeiden, werden dekorative Symbole und Bilder jetzt von Bildschirmlesehilfen ignoriert (CQ-4272944).

**In Experience Manager Assets behobene Probleme**

[!DNL Adobe Experience Manager] 6.5.5.0 Assets bieten Korrekturen an folgenden Problemen:

* [!UICONTROL Die Option &quot;Beginn] &quot;im Dialogfeld &quot;Arbeitsablauf  erstellen&quot;für Assets in einer Sammlung ist deaktiviert, sodass Workflow nicht ausgelöst wird (NPR-32471).

* Wenn Sie in Metadaten-Schemas ein Kaskadenpopup verwenden, wird beim Auswählen und Speichern einer Dropdown-Option mit einem Apostroph (aus der untergeordneten Dropdown-Liste) die ausgewählte Apostroph-Option nach dem erneuten Öffnen der Asset- [!UICONTROL Eigenschaften] (NPR-32649) ausgeblendet.

* [!UICONTROL Asset Insights Sync Job] stoppt und schlägt fehl, wenn ungültige Einträge (auf der Seite von Analytics) auftreten, anstatt zum nächsten Eintrag (NPR-32674) zu wechseln.

* Gyroscope ist nicht funktionsfähig, da Bewegungssensoren standardmäßig in mobilen Browsern im Panorama-Viewer deaktiviert sind (CQ-4272937).

* [!UICONTROL Der Assistent zur Konfiguration] von verbundenen Assets funktioniert mit dem Fehler 404 nicht, wenn 6.5.3 unter 6.5.1 (NPR-32730) installiert wird.

* Während des XMP Schreibvorgangs ändern alle benutzerdefinierten Metadateneigenschaften des Namensraums das benutzerdefinierte Präfix des Namensraums in &quot;ns2&quot;anstelle des konfigurierten Namensraums (NPR-32748).

* Verzögertes Laden wird nicht ausgelöst und es werden nur 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32750).

* `NullPointerException` wird aufgrund fehlender Node-Voreinstellungen im neu erstellten Profil (SAML/SSO) beobachtet. Dieser Fehler verhindert, dass neu angemeldete Benutzer die [!DNL Adobe Experience Manager Stock] Integration verwenden (NPR-32777).

* In Protokollen zum Öffnen einer intelligenten Sammlung mit mehr als 10.000 Assets (NPR-32980) werden seitenübergreifende Warnungen angezeigt.

* Asset-Namen werden in Kleinbuchstaben geändert, wenn Assets von einem Ordner in einen anderen verschoben werden, während sie im Scene7-Laufmodus für dynamische Medien [!DNL Adobe Experience Manager] arbeiten (NPR-32995).

* Ein durchsuchtes Asset kann nicht gelöscht werden, nachdem es aus den Suchergebnissen zu seinen Eigenschaften navigiert und dann zu den Suchergebnissen zurückgekehrt ist, um es zu löschen (NPR-32998).

* [!UICONTROL Die nächste] Option bleibt bei der Auswahl des Zielordners in der Benutzeroberfläche &quot;Assets [!UICONTROL verschieben] &quot;deaktiviert (NPR-33356).

* [!UICONTROL Die nächste] Option ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33275).

* Berechtigungen zum Ein- und Auschecken sind auf Adobe Asset Link (AAL) für Benutzer mit Berechtigung zum Löschen deaktiviert, auch wenn andere Berechtigungen wie Lesen, Erstellen oder Ändern gewährt werden (NPR-33272).

* Im Dialogfeld zum Herunterladen von Assets (NPR-33167) sind keine Smart-Zuschneiden-Darstellungen verfügbar.

* Ausnahmen sind in Protokollen beim Öffnen der Rail-Darstellungen für eine PDF-Datei unter einem Profil mit intelligenten Zuschnitten (CQ-4294201) zu beobachten.

* Bildvorgaben werden nicht veröffentlicht, wenn der Synchronisierungsmodus [!UICONTROL für] dynamische Medien standardmäßig auf dem Experience Manager mit dem Scene7-Modus für dynamische Medien deaktiviert ist (CQ-4294200).

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert, und die Workflow-Instanz zeigt angehaltene Instanzen des DAM-Aktualisierungsassets (CQ-4293916).

* Das Erstellen einer Konfiguration für dynamische Medien auf Experience Manager funktioniert, auf der Benutzeroberfläche geschieht jedoch nichts bei der Auswahl von Speichern (CQ-4292442).

* Die Vorschau von F4V-Video-Assets funktioniert bei der progressiven Wiedergabe auf Safari/Mac nicht (CQ-4289844).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit Punkt- `.` Zeichen im Namen befindet (CQ-4289337).

* Die Miniaturansicht ist beschädigt, und das Videoverarbeitungsbanner wird nicht angezeigt, wenn ein Video kopiert wird (CQ-4284125).

* Beim Dimensional Viewer werden in Firefox bei einigen Modellen mit leeren Ansichten fälschlicherweise leere Miniaturansichten angezeigt (CQ-4283447).

* Die in Version 6.5.5.0 behobenen Leistungsprobleme lauten (CQ-4279206):

   * Es dauert zu lange, bis große Binärdateien auf die Server der dynamischen Medienverarbeitung hochgeladen werden.

   * Die Zeit zum Generieren von Miniaturbildern auf dem Experience Manager nimmt aufgrund der Scene7-Architektur von Dynamic Media zu.

* Probleme mit der Migration von Dynamic Media Scene7 schlagen bei Kunden mit einer großen Anzahl von Assets fehl (CQ-4279206).

* Layout of video 360 viewer is broken if `setVideo` is used, and video shifts down on using `video= modifier` (CQ-4263201).

* An error message displays while installing the Experience Manager SDL package (NPR-33175).

* SSRF vulnerability in Experience Manager (NPR-33435).

### Plattform {#platform-6550}

* The [!DNL Sling] filter is not called if the `sling:match` map entry is created under `/etc/maps` (NPR-33362).
* Experience Manager crashes due to segmentation fault with [!DNL Apache Lucene] (NPR-32988).
* [!DNL Jackson] Kernpaket fehlt in der Datei &quot;Experience Manager uberjar&quot;(NPR-32848).
* CRXDE Lite does not load content for users without read permission on the `jcr:primaryType` property for a node (NPR-32611).
* [!DNL Granite] maintenance task scheduler re-initializes too often during Experience Manager deployments (CQ-4294627).
* When an SQL query execute for a long time, for example 7 hours, Experience Manager stops responding (NPR-33044).

### Benutzeroberfläche {#ui-6550}

* Radio button selection does not persist in a multifield (NPR-33309).
* Lazy loading limit does not work for the list view (NPR-33124).
* Omnisearch results page does not display a message if there are no matches (NPR-32974).
* Der Omniture-Filter gibt alle Übereinstimmungen unter dem `/content` Knoten zurück, wobei der ausgewählte Speicherort ignoriert wird (NPR-32849).

### Integrationen {#integrations-6550}

* Internal cache is cleared when a page with an Adobe Target component is published (NPR-33162).
* Die Integration mit Adobe Target funktioniert nicht mit [!DNL Windows Internet Explorer] 11 (NPR-33111).
* When configuring Adobe Target, the [!UICONTROL Company] and [!UICONTROL Report Suite] fields do not appear on selecting a reporting source (NPR-32502).
* When exporting [!DNL Experience Fragments] using Adobe I/O, metadata like Source Product is not exported into Adobe Target (NPR-32159).
* Authorized IMS users in local Experience Manager admin group cannot create or modify IMS configurations (NPR-33045).
* Adobe Startkonfigurationsseite zeigt nicht alle Datensätze an (NPR-33011).
* Benutzer in der Gruppe &quot;Inhaltsersteller&quot;können Eigenschaften einer Adobe Target-Komponente aufgrund eines JavaScript-Fehlers (NPR-32996) nicht bearbeiten.
* Site-übergreifende Skripterstellung für JSON (NPR-32744).

### Übersetzungsprojekte {#translation-6550}

* Übersetzte Tags werden nicht aus Übersetzungsdiensten von Drittanbietern (NPR-33154) in Experience Manager importiert.
* Auf der Seite &quot;Übersetzungskonfiguration&quot;wird ein falscher Übersetzungsanbieter angezeigt als der für die Übersetzung verwendete (NPR-32971).
* Durch das Hinzufügen eines Erlebnisfragmentordners zu einem vorhandenen Übersetzungsprojekt wird ein neues Projekt erstellt (NPR-32843).
* In den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32628) wird ein `NullPointerException` Fehler angezeigt.

### WCM {#wcm-6550}

* Page Editor - The [!DNL Sites] Page Editor does not allow the keyboard-only users to skip to the main content instead of shifting tab focus through all options available in the header (CQ-4293883).
* Page Editor - Panels that use Well component and include saved data do not display due to updates in [!DNL Chrome] and [!DNL Firefox] versions (CQ-4292995).
* MSM - Deleting a component from the page does not delete the component from the published version of the page (CQ-4292360).

### [!DNL Brand Portal] {#assets-brand-portal-6550}

* Removing a published metadata schema from [!DNL Brand Portal] results in an error (CQ-4292063).
* If an administrator configures [!DNL Experience Manager Assets] 6.5.4 with Brand Portal via Adobe Developer Console, the [!DNL Brand Portal] user is not able to publish a contribution folder&#39;s asset from [!DNL Brand Portal] to [!DNL Experience Manager] (NPR-33046).
* Duplikat-Replikation der übergeordneten Ordner, die Konflikte verursachen (NPR-33001).

### [!DNL Communities] {#communities-6550}

* Cannot delete a card in moderation console using the quick edit menu option (NPR-33117).
* An error occurs on accessing the [!UICONTROL Activity Stream] page (NPR-33146).
* Groups deleted on author instance are not removed from all publish instances (NPR-33199).
* Authors, after creating a new group, are not redirected to the [!UICONTROL Community Group] section on [!DNL Internet Explorer] 11 (NPR-33205).
* Accessing a message in Experience Manager Inbox does not change the status of the message to Read (NPR-32764).
* Editing a [!DNL Communities] group and changing the thumbnail image does not update the group thumbnail image (NPR-32599).
* Ein Benutzer kann keine E-Mail an einen anderen Benutzer in einer Community senden (NPR-32598).
* A submitted blog does not display until the user refreshes the page (NPR-32391).
* While creating a version of notifications and subscriptions of User Generated Content (UGC), an incorrect ID of the source page is stored (CQ-4279355, CQ-4289703).
* Cross-site scripting issue (NPR-33203).

### Workflow {#workflow-6550}

* The [!UICONTROL Timeline] option in the left rail takes more time to load than expected (NPR-32851).
* After restarting an Experience Manager instance, the email for the review task for a collection includes an incorrect payload link (NPR-32774).

### [!DNL Forms] {#forms-6550}

>[!NOTE]
>
>Experience Manager Service Pack enthält keine Korrekturen für [!DNL Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

* Correspondence Management: Die Reihenfolge der Vermögenswerte in einem Zielgruppen-Bereich wird nach der Einreichung eines Schreibens (NPR-33359, NPR-33153) geändert.
* Adaptives Forms: Wenn ein Benutzer ein adaptives Formular bearbeitet, funktioniert die Option [!UICONTROL Beginn-Workflow] im Menü &quot; [!UICONTROL Seiteninformationen] &quot;nicht (NPR-33004).
* Adaptives Forms: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-32997).
* Adaptive Forms: Changing the panel layout in an adaptive form results in an error (CQ-4293880).
* Adaptive Forms: A new line to a string in an adaptive forms dictionary adds `&#xa;` characters to the dictionary (NPR-33266).
* Adaptive Forms accessibility: When a user previews an adaptive form as an HTML form, the [!UICONTROL Scribble Signature] field is not able to retain tab focus (NPR-33159).
* Adaptive Forms accessibility: The error messages that display on submitting an adaptive form do not link to an `aria-describedBy` attribute (NPR-33071).
* Adaptive Forms accessibility: Fields marked mandatory in an adaptive form do not have the mandatory attribute set to True in the ARIA accessibility schema (NPR-33070).
* PDFG-Dienst: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33238).
* PDFG Service: `CreatePDF` operation fails to convert a PDF file to PDF OCR format (NPR-32994).
* PDFG Service: PDF conversion fails for the 200th instance of an [!DNL OpenOffice] document (NPR-32766).
* BackendIntegration: Form data model requests fail as the refresh token expires due to incorrect inactive state (NPR-33169).
* Designer: Screen readers execute the tabbing order based on the default geographic order instead of the custom tabbing order defined in the XDP file (NPR-32160).
* Designer: If the tagging option is enabled, the subform border disappears in the generated PDF output (NPR-32778).
* Stored XSS with the GuideSOMProviderServlet (NPR-32700).

## Install 6.5.5.0 {#install}

**Einrichtungsvoraussetzungen**

* AEM 6.5.5.0 requires AEM 6.5. See [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* The service pack download is available on Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.5.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Before installing, take a snapshot or a fresh backup of your AEM instance.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Dennoch wird dies empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe does not recommend removing or uninstalling the Adobe Experience Manager 6.5.5.0 package.

### Installieren des Service Packs {#install-service-pack}

Führen Sie die folgenden Schritte aus, um das Service Pack auf einer vorhandenen Adobe Experience Manager 6.5-Instanz zu installieren:

1. Download the service pack from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip).

1. Open Package Manager and click **[!UICONTROL Upload Package]** to upload the package. To know how to use it, see [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html).

1. Select the package and click **[!UICONTROL Install]**.

>[!NOTE]
>
>Dialog on Package Manager UI sometimes exits during the installation of the service pack. Adobe empfiehlt, dass Sie auf die Stabilisierung der Fehlerprotokolle warten, bevor Sie auf die Bereitstellung zugreifen. Wait for the specific logs related to the uninstall of the updater bundle before being assured that the installations is successful. Typically, this happens on [!DNL Safari] but can intermittently happen on any browser.

**Automatische Installation**

There are two ways to automatically install Adobe Experience Manager 6.5.5.0 on a working instance:

A. Place the package into `../crx-quickstart/install` folder when the server is available online. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html). Use `cmd=install&recursive=true` so that the nested packages are installed.

>[!NOTE]
>
>Adobe Experience Manager 6.5.5.0 does not support Bootstrap installation.

**Bestätigen der Installation**

1. The product information page (`/system/console/productinfo`) displays the updated version string `Adobe Experience Manager (6.5.5.0)` under [!UICONTROL Installed Products].

1. All OSGi bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: `/system/console/bundles`).

1. The OSGI bundle `org.apache.jackrabbit.oak-core` is version 1.22.3 or higher (Use Web Console: `/system/console/bundles`).

To know the platforms certified to work with this release, see the [technical requirements](/help/sites-deploying/technical-requirements.md).

### Install Adobe Experience Manager Forms add-on package {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms werden über ein separates Add-On-Paket bereitgestellt.

1. Ensure that you have installed the Adobe Experience Manager Service Pack.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

### Install Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fixes in Adobe Experience Manager Forms on JEE are delivered through a separate installer.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes for patch 0014](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-5/jee-patch-0014.html).

### UberJar {#uber-jar}

The UberJar for Experience Manager 6.5.5.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.5/).

To use UberJar in a Maven project, see [how to use UberJar](/help/sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.5</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Veraltete Funktionen {#removed-deprecated-features}

In diesem Abschnitt werden Funktionen Liste, die mit AEM 6.5.5.0 als veraltet gekennzeichnet wurden. Funktionen, die in einer zukünftigen Version entfernt werden sollen, werden zuerst auf &quot;Veraltet&quot;eingestellt, wobei eine alternative Option verwendet werden muss.

Kunden wird empfohlen, zu überprüfen, ob sie die Funktion oder Funktionalität in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm &quot; **[!UICONTROL AEM Cloud-Services-Teilnahme]** &quot;wird nicht mehr unterstützt. Mit der in AEM 6.5 aktualisierten AEM- und Zielgruppe-Integration zur Unterstützung der Target Standard-API, die die Authentifizierung über Adobe IMS und I/O verwendet, und der wachsenden Rolle des Adobe Launch bei der Instrumentierung AEM Seiten für Analyse und Personalisierung ist der Opt-In-Assistent funktional irrelevant geworden. | Konfigurieren Sie Systemverbindungen, Adobe-IMS-Authentifizierung und Adobe-I/O-Integrationen über die jeweiligen AEM-Cloud-Dienste. |
| Connectoren | Die Adobe JCR Connector for Microsoft SharePoint 2010 und Microsoft SharePoint 2013 wird für AEM 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* If you are installing [!DNL Experience Manager] 6.5.5.0 with [!DNL Java] 11, restart the server after installing the Service Pack. No restart is required if you are installing the Service Pack with [!DNL Java] 8.

* If a folder in the hierarchy is renamed in [!DNL Experience Manager Assets] and the nested folder containing an asset is published to [!DNL Brand Portal], the title of the folder is not updated in [!DNL Brand Portal] until the root folder is published again.

* While installing AEM 6.5.5.0, update of [!DNL Chrome] version 83 is causing an issue in building packages. Verwenden Sie andere verfügbare Browser, z. B. [!DNL Internet Explorer] und [!DNL Firefox]andere Standardinstallationsoptionen AEM Pakets, um das Problem zu beheben. Das Problem wird nach der Installation von AEM 6.5.5.0 behoben.

* Unable to send an email to the remote SMTP server using the AEM default mail sender, as it only allows communication using TLS v1.2. Remove bundle `javax.mail:mail:1.5.0-b01` from `system/console` and refresh the bundles to resolve the issue.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Wenn der Konfigurationsassistent für [!UICONTROL verbundene Assets nach der Installation die Fehlermeldung 404 zurückgibt, müssen Sie die Pakete] und `cq-remotedam-client-ui-content` `cq-remotedam-client-ui-components` Pakete manuell mit dem Package Manager neu installieren.

* The following errors and warning messages may display during installation of AEM 6.5.x.x:
   * „Wenn die Target-Integration mit der Target Standard-API (IMS-Authentifizierung) in AEM konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Adaptive Form server-side validation fails when aggregate functions such as SUM, MAX, and MIN are used. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in a Dynamic Media interactive image is not visible when previewing the asset through Shoppable Banner viewer.

## OSGi bundles and content packages included {#osgi-bundles-and-content-packages-included}

The following text documents list the OSGi bundles and Content Packages included in AEM 6.5.5.0:

* [Liste der in AEM 6.5.5.0 enthaltenen OSGi-Bundles](assets/6550_bundles.txt)

* [Liste der in AEM 6.5.5.0 enthaltenen Inhaltspakete](assets/6550_packages.txt)

## Restricted sites {#restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Contact customer support](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
For more information on accessing the support portal, see [Accessing the support portal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORELIKETHIS]
>
>* [Versionshinweise zu AEM 6.5](/help/release-notes/release-notes.md)
>* [AEM-Produktseite](https://www.adobe.com/de/marketing/experience-manager.html)
>* [Dokumentation zu AEM 6.5](https://helpx.adobe.com/de/support/experience-manager/6-5.html)
>* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

