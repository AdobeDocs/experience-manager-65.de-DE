---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6,5
description: '[!DNL Adobe Experience Manager]Informationen zu  6.5 mit Versionshinweisen, Angaben zu neuen Funktionen und zur Installation sowie ausführlichen Änderungslisten.'
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 1ca3032063a148293f67c69a941b83b6aa5d48f1
workflow-type: tm+mt
source-wordcount: '3884'
ht-degree: 5%

---

# [!DNL Adobe Experience Manager] 6.5 Neueste Service Pack - Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.11.0 |
| Typ | Service Pack-Version |
| Datum | 25. November 2021 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.11.zip) |

## Was ist enthalten in [!DNL Adobe Experience Manager] 6,5,11,0 {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.11.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf installiert. [!DNL Adobe Experience Manager] 6.5.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.11.0 sind:

* Mehrfeld-Unterstützung für mehrzeiligen Text-Datentyp hinzugefügt.

* Verbesserung, um Benutzer über den asynchronen Auftrag zu informieren, der derzeit im Hintergrund ausgeführt wird, um zu verhindern, dass sie mehrere asynchrone Vorgänge auf demselben Pfad auslösen.

* Die automatische Generierung von Sitemap für SEO-Zwecke ist mit dem [SEO-Indexpaket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip). Es unterstützt Sitemaps, alternative URLs, Roboter-Meta-Tags und mehr in der [!DNL Core Components].

* Zur Verbesserung des Anwendererlebnisses wird nun die Anzahl der in einem Ordner vorhandenen Assets angezeigt. Für mehr als 1.000 Assets in einem Ordner zeigt [!DNL Assets] „1000+“ an.

   ![Anzahl der Assets in einem Ordner](/help/assets/assets/browse-folder-number-of-assets.png)

* Unterstützung von Geschäftsprofilen für Adobe Asset Link.

* Sie können jetzt [!DNL Dynamic Media] , um allgemeine Einstellungen zu konfigurieren, anstatt die [!DNL Dynamic Media Classic] Desktop-Applikation. Siehe [Allgemeine Dynamic Media-Einstellungen konfigurieren](/help/assets/dm-general-settings.md).

   ![Allgemeine DM-Einstellungen](/help/assets/assets-dm/dm-general-settings.png)

* Sie können jetzt [!DNL Dynamic Media] um die Veröffentlichungseinstellungen zu konfigurieren, anstatt die [!DNL Dynamic Media Classic] Desktop-Applikation. Siehe [Konfigurieren der Veröffentlichungseinstellungen von Dynamic Media](/help/assets/dm-publish-settings.md).

   ![DM-Veröffentlichungseinstellungen](/help/assets/assets-dm/dm-publish-setup.png)

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.9 aktualisiert.

Im Folgenden finden Sie die Liste der Fehlerbehebungen in [!DNL Experience Manager] Version 6.5.11.0.

### [!DNL Sites] {#sites-65110}

>[!WARNING]
>
>Eine neue Version dieses Pakets wird derzeit entwickelt. Der Link wird veröffentlicht, sobald er verfügbar ist.

Um auf die Bereitstellung von Headless-Inhalten mit Inhaltsfragmenten mit GraphQL zuzugreifen und die erweiterten Funktionen für Inhaltsfragmentmodelle und Editor zu verwenden, installieren Sie das Indexdefinitionspaket und indizieren Sie die folgenden asynchronen AEM Indexdefinitionen neu:

* `/oak:index/assetPrefixNodename`

* `/oak:index/fragments`

* `/oak:index/graphqlConfig`

Die folgenden Probleme wurden in [!DNL Sites]:

* Vorlage zum Erstellen eines Inhaltsfragments ist beim Erstellen eines Inhaltsfragments nicht sichtbar (SITES-3365).

* Reguläre Ausdrücke und [!UICONTROL Eindeutig] Feldoptionen funktionieren nicht in [!UICONTROL appsUrl] -Modell im Inhaltsfragment-Editor (SITES-1823).

* Konfigurationen werden hinzugefügt in `/apps/system` Knoten anstatt `/libs` bei der Installation des vorherigen Service Packs (SITES-3203).

* Funktionen, die Inhaltsfragmente verwenden, funktionieren bei der Installation des vorherigen Service Packs nicht wie gewohnt (SITES-3151).

* Die Sortierung funktioniert nicht in [!UICONTROL Inhaltsfragmentmodelle] Konsole (SITES-2722).

* GraphiQL lädt keine Modelle (Schemas) und tritt bei Endpunkt-JSON (SITES-2428) auf einen Fehler.

* Die Auflistungsfeldtypen, die zu einem [!UICONTROL Inhaltsfragmentmodell] nicht sichtbar in [!UICONTROL Inhaltsfragmentmodell-Editor] (SITES-2391).

* Der Datentyp Tags unterstützt bestimmte Datentypen nicht (SITES-2390).

* [!UICONTROL Inhaltsfragment-Rest-API] exportiert veraltete Tag-Werte (SITES-2386).

* Der Pfeil im Breadcrumb ist im Inhaltsfragmente-Editor nicht richtig ausgerichtet (SITES-2341).

* Die Referenzsuche für Inhaltsfragmente ist bei großen Datensätzen langsam (SITES-2147).

* [!UICONTROL CopyUrl] Option ist in nicht geeignet [!UICONTROL Inhaltsfragmente-Editor] (SITES-2007).

* Es wird keine Warnung angezeigt, wenn ein Inhaltsfragment zusammen mit einem zugehörigen Modell veröffentlicht wird und das Modell Bremsänderungen einführt (SITES-1988).

* Die URL-Bearbeitung des Inhaltsfragmentmodells unterscheidet sich für verschiedene Anwendungsfälle der Bearbeitung von Inhaltsfragmentmodellen (SITES-1980).

* Beim Erstellen von zwei Inhaltsfragmenten mit demselben Titel mithilfe der Inline-Funktion [!UICONTROL Neues Inhaltsfragment] -Aktion verwenden, gibt der Assistent denselben Fragmentpfad zurück (SITES-1978).

* Die automatische Vervollständigung funktioniert nicht in [!UICONTROL Inhaltsfragmentmodell] Suchfacette (SITES-1976).

* Wenn ein Inhaltsfragment eine große Hierarchie verschachtelter Fragmente enthält, wird die [!UICONTROL Inhaltsfragment-Editor] reagiert beim Laden des Seitenbereichs nicht mehr (SITES-1974).

* Die globale Suche im Fragmentauswahlpfad funktioniert nicht (SITES-1973).

* Verweise werden beim Verschieben eines Inhaltsfragments aktualisiert (SITES-1897).

* Die Option zum Erstellen einer Seite fehlt in der Karten- und Spaltenansicht (NPR-37549).

* Beim Neuanordnen von Komponenten auf einer Launch-Seite behält das Weiterleiten von Launch die Neuanordnung von Komponenten nicht bei (NPR-37539).

* Die Option zur Auswahl aller Elemente in einer Liste funktioniert nicht auf der Rollout-Seite (NPR-37443).

* Die geplante Aktivierung mehrerer Seiten führt zum Öffnen einer neuen JCR-Sitzung für `wcm-workflow-service` Benutzer (NPR-37417).

* Der Vorgang zum Verschieben von Ordnern in der Sites-Konsole schlägt mit der Fehlermeldung &quot;Startinformationen für ausgewählte Elemente konnten nicht abgerufen werden&quot;fehl. (NPR-37340)

* Beim Generieren einer Miniaturansicht für Blueprint und Rollout in Live Copies ist die Vererbung für Registerkarten nach der Miniaturansicht in Live Copies fehlerhaft (NPR-37190).

* Das Filterprädikat zur Anzeige von Live Copy zeigt nicht alle Live Copies an (NPR-37126).

* Das Replikationsereignis gibt nicht die Liste aller übergeordneten und untergeordneten Seiten zurück, die zum Löschen markiert wurden, wenn der Replikationsereignis-Handler auf dem Autor aufgerufen wird (NPR-37123).

* Beim Speichern einer Eigenschaft mit mehreren Werten mit dem Bulk Editor wird die durch Kommas getrennte Zeichenfolge als erstes Element des Arrays gespeichert (NPR-37089).

* Die Größenanpassung des Komponentenlayouts funktioniert nicht im Layout für Mobilgeräte (NPR-37086).

* Ein neuer Knoten wird beim Speichern von Seiteneigenschaften fälschlicherweise auf Live Copy-Ebene erstellt, nachdem Rollout-Konfigurationen hinzugefügt wurden (NPR-37084).

* Benutzer können keine Live Copies erstellen oder mit Seiteneigenschaften für neue Übergeordnete Seiten ein Rollout durchführen (SITES-3442).

* Tags zeigen Tag-Namen anstelle des Titels an und die Option zum Schließen entfernt die Tags nicht vollständig, da die Tag-Eigenschaft falsch funktioniert, wenn die Vererbung auf Eigenschaftsebene abgebrochen wird (NPR-36831).

* Die Option, die Auswahl aller Elemente aufzuheben, funktioniert nicht und die Kopfzeile überschneidet sich mit der ersten Zeile in der Tabelle, der Seite, die eine Liste von Live Copies anzeigt (NPR-37070).

* In einem benutzerdefinierten Dialogfeld, das in einem Workflow verwendet wird, schlägt der Experience Manager bei der Überprüfung des Dialogfelds mit einem Fehler in der Browserkonsole fehl (GRANITE-35049).

Die folgenden Verbesserungen der Barrierefreiheit sind verfügbar in [!DNL Adobe Experience Manager Sites]:

* Die Rolle der [!UICONTROL Site-Referenzen] und [!UICONTROL Sprachkopien] Optionen (SITES-1791).

* Die Reihenfolge des Browsermodus-Fokus wird jetzt sequenziell auf verschiedene Optionen in der Benutzeroberfläche verschoben (SITES-1791).

* Bildschirmlesehilfen kommentieren jetzt, ob das ausgewählte Baumstrukturelement den ausgewählten Status aufweist, und teilen dem Benutzer außerdem mit, dass der Aktionsbereich angezeigt wird (SITES-2109).

* Bildschirmlesehilfen geben jetzt an, dass bei der Auswahl von Filtern oder der Suche nach einer Seite eine Ladeanzeige vorhanden ist (SITES-1790).

* Bildschirmlesehilfen kommentieren jetzt, wenn die [!UICONTROL Filter] -Option gibt in der linken Leiste kein Suchergebnis zurück (SITES-1599).

* Beim Navigieren im Durchsuchen-Modus kommentieren Bildschirmlesehilfen die Rolle der Inhaltsseite und den ausgewählten Status einer Seite, wenn die Eingabetaste gedrückt wird (SITES-1579).

* Bildschirmlesehilfen kommentieren jetzt, wenn [!UICONTROL Hinweis] ausgewählt ist (SITES-1573).

* Formularfelder haben jetzt neben den Platzhaltern visuelle Beschriftungen, sodass die Benutzer der Bildschirmlesehilfe bei der Eingabe der Feldwerte entsprechend geleitet werden (SITES-1258).

### [!DNL Assets] {#assets-65110}

Die folgenden Verbesserungen der Barrierefreiheit sind verfügbar in [!DNL Assets]:

* In der Kartenansicht im [!DNL Assets] Repository bei Verwendung von `Tab` zum Verschieben des Fokus auf das erste Element, das Schnellaktionen im Fokus öffnet, gibt die Bildschirmlesehilfe den Namen des fokussierten Elements an.
* In [!DNL Dynamic Media] [!UICONTROL Viewer-Vorgabeneditor]Wenn Shadow Color und Border Color nicht vorhanden sind, werden die Eingaben mit der Eigenschaft disabled deaktiviert. Tastaturbenutzer können die Eingabe nicht fokussieren, und Bildschirmlesehilfen geben den Status für das Steuerelement nicht als deaktiviert an.
* In [!DNL Dynamic Media], um ein neues Videokodierungsprofil zu erstellen, muss die [!UICONTROL Smart Crop Ratio] für die Barrierefreiheit gekennzeichnet ist, sodass Bildschirmlesehilfen sie entsprechend ankündigen.

* Sie können jetzt auf die Steuerelemente für die Referenzliste in [!DNL Experience Manager Assets] über eine Tastatur.

Die folgenden Probleme wurden in [!DNL Assets]:

* Wenn ein Benutzer der Gruppe &quot;Mitarbeiter&quot;zum DAM-Asset-Repository navigiert, ist ein außergewöhnliches `POST` -Anfrage zum Erstellen einer Sammlung ausgelöst. Diese `POST` Anfrage schlägt fehl und spiegelt einen Fehler in den Protokollen wider (NPR-37171).

* Beim Erstellen einer Live Copy des Blueprints mit einer verschachtelten Ordnerstruktur werden die geänderten Eigenschaften des Quellordners nicht im Live Copy-Ordner aktualisiert (NPR-37449).

* Beim Auswählen mehrerer Assets und Ändern der Metadatenfeldwerte werden die Werte beim Speichern der Assets nicht beibehalten. Außerdem werden die Metadatenänderungen nicht angewendet (NPR-37341).

* Wenn Sie mehrere Assets auswählen und die Eigenschaften ändern, werden die benutzerdefinierten Eigenschaften (Dropdown-Listen) durch die Standardwerte überschrieben (NPR-36437).

* Für die Broschüren-, Flyer- und InDesign-Vorlagen wird eine falsche PDF-Darstellung generiert. (NPR-36433)

* Speichern einer [!DNL Adobe Target] Aktivität mit [!DNL Experience Manager] Der Targeting-Modus schlägt im Falle eines [!DNL Adobe Analytics] Berichtsmetrik wird referenziert (NPR-37167).

* Wenn ein Benutzer mit E-Mail-Adresse mit dem Domänennamen mit gemischten Groß-/Kleinschreibung ein Asset auscheckt, ist das Asset in den ausgecheckten Assets des Benutzers nicht sichtbar in [!DNL Asset Link] (CQ-4329266).

<!-- Add 
* [!DNL Adobe Asset Link] is not able to access the digital assets even when the [!DNL Creative Cloud] and [!DNL Experience Management] entitlements are provided by two different organizations. -->

* Beim Hinzufügen eines Videos mit benutzerdefinierten Metadaten, die beim Hochladen auf eine Seite generiert werden, wird ein Fehler bezüglich eines unbekannten Namespace angezeigt, auch wenn der Namespace registriert ist (CQ-4331471).

* In [!DNL Assets], wenn [!DNL Launcher] deaktiviert ist, funktioniert das Metadaten-Writeback nicht, wenn es manuell ausgelöst wird. (CQ-4329082)

### [!DNL Dynamic Media] {#dynamic-media-65110}

Die folgenden Fehlerbehebungen sind in verfügbar: [!DNL Dynamic Media]:

* Asset wird in nicht aktualisiert [!DNL Dynamic Media] beim Wiederherstellen der Asset-Version in [!DNL Experience Manager] (NPR-37421).

* ECatalogs werden nicht auf dem Veröffentlichen von PDF-Dateien veröffentlicht (CQ-4329886).

* 3D-Assets werden nicht geladen, wenn die veröffentlichte Seite geöffnet wird, falls die Komponente eine vordefinierte Vorgabe verwendet (CQ-4329205).

* Probleme bei der PDF-Asset-Verarbeitung bei großen Repositorys (CQ-4328711).

* PDF-Verarbeitungsfehler wird nicht auf [!DNL Experience Manager] im Falle eines Versagens [!DNL Scene7] (CQ-4331145).

* Benutzer können die Standard-Metadateneigenschaften für ein .MOV-Asset nicht sehen. (CQ-4332546)

* .MXF-Videodateien können nicht in hochgeladen werden [!DNL Dynamic Media] using [!DNL Experience Manager] (CQ-4329709).

* Upload-Probleme beim Einrichten des benutzerdefinierten Unternehmens-Stammverzeichnisses (CQ-4332800).

* In [!DNL Experience Manager] Setups, die benutzerdefinierten Starter mit `ActivationModel` Während des Workflows stürzt der Experience Manager aufgrund von Speicherproblemen beim Hochladen von PDF-Dateien ab. (CQ-4330512).

* Leistungsprobleme in `DamEventRecorder` (CQ-4334072).

* Wenn ein Shop-fähiger Video-Hyperlink (verknüpfte URL) Sonderzeichen enthält, wird die Ziel-URL vom Viewer kodiert und führt zu einer falschen Produktseite (CQ-4331639).

* Auf einer Videoprofilseite werden die Symbolleistenoptionen nicht mehr angezeigt, wenn der Benutzer beim Laden der Seite ein Videoprofil auswählt (CQ-4308521).

* Fehler bei der DM-Asset-Verarbeitung aufgrund gleichzeitiger JCR-Schreibvorgänge (CQ-4333489).

* Der Zugriff auf die Seite &quot;Videoprofile&quot;schlägt fehl, wenn im Videoprofil-Stammordner des Benutzers benutzerdefinierte Zugriffsrichtlinien für den Stammknoten der Videoprofile definiert sind (CQ-4332941).

* In einem vergrößerbaren Bild fallen die Tastaturbefehle (&#39;+&#39;, &#39;-&#39;) oder Esc-Tasten den Fokus der Bildschirmlesehilfen auf. (CQ-4290719)

* Wenn ein Benutzer auf die Tastenkombination &quot;F&quot;im Formularmodus klickt, ordnet die Bildschirmlesehilfe die Beschriftung der [!UICONTROL Einbettungsgröße] Menüschaltfläche verfügbar in [!UICONTROL Einbetten abrufen] Code-Dialogfeld (CQ-4290929).

* Bei Verwendung der Tastaturnavigation zum Öffnen des Popup-Fensters für E-Mail-Links sind die in der Benutzeroberfläche angezeigten Fehlervorschläge für die Felder &quot;An&quot;und &quot;Von&quot;nicht beschreibend. (CQ-4290930)

* Beim Navigieren zum Dialogfeld &quot;E-Mail-Link&quot;liest die Bildschirmlesehilfe die Beschriftungsinformationen für die neu hinzugefügten Bearbeitungsfelder nicht mit dem Abwärtspfeil und dem Tastaturbefehl für den Formularmodus (&#39;F&#39;) (CQ-4290934).

* Beim Navigieren zum Dialogfeld &quot;E-Mail-Link&quot;spiegelt die Bildschirmlesehilfe das visuelle Sternchen (*)-Symbol für die Pflichtfelder &quot;Bis&quot;und &quot;Von&quot;nicht wider (CQ-4290935).

* Die Benutzer können das Wahrzeichen und die Region nicht mithilfe der Tastaturbefehle (&#39;D&#39;, &#39;R&#39;) identifizieren (CQ-4312118).

<!-- Anuj to check if this section is required or not. We have an enh. in CIF area that is mentioned. It is added above and not part of this bug fix section.
-->

### Commerce {#commerce-65110}

* Bei Verwendung von [!UICONTROL Später veröffentlichen] -Option, spiegelt die Benutzeroberfläche den Status nicht als [!UICONTROL Veröffentlichung ausstehend] (CQ-4334229).

* Beim Rückgängigmachen der Veröffentlichung eines Ordners wird die Veröffentlichung der Produkte dieses Ordners nicht vollständig rückgängig gemacht. Die Produkte werden aus dem Herausgeber entfernt, sind aber noch in der Autoreninstanz vorhanden (CQ-4332731).

### Plattform {#platform-65110}

* Wenn ein Benutzer auf das Symbol &quot;Neu anordnen&quot;für eine Multifield-Option klickt, wird die Bildlaufleiste in der Benutzeroberfläche ausgeblendet (CQ-4331100).

* Wenn ein Benutzer nach der Aktualisierung die Komponente für den Login-Container am Arbeitsplatz öffnet, ist die Kopfzeile des Dialogfelds nicht auf der Benutzeroberfläche sichtbar (CQ-4316173).

### Integrationen {#integrations-65110}

* Speichern einer [!DNL Adobe Target] Aktivität mit [!DNL Experience Manager] Der Targeting-Modus schlägt im Falle eines [!DNL Adobe Analytics] Berichtsmetrik wird referenziert (NPR-37167).

### Projekte {#projects-65110}

* Bei der Aktualisierung von [!DNL Experience Manager] 6.5.8.0 auf Version 6.5.9.0, überschreibt die Installation die Eigenschaften auf `/content/dam/projects`. Setzt das zugewiesene Metadatenschema und die Eigenschaften des Ordners auf den Standardwert zurück (NPR-37124).

### Benutzeroberfläche {#user-interface-65110}

* Das Ordnersymbol, das das Modell darstellt, ist falsch (NPR-37176).

* Wenn ein Benutzer mithilfe des Pfadfeld-Browsers eine Suche durchführt oder durchsucht, werden falsche Knoten angezeigt (NPR-37175).

* In der Veröffentlichungsinstanz werden die eingehenden Anfragen mehrere Minuten blockiert (NPR-37169).

* Beim Hinzufügen einer multifield -Eigenschaft in einem Dialogfeld für einen benutzerdefinierten Workflow kann das Dialogfeld nicht fortgesetzt werden und der Benutzer kann das Dialogfeld nicht schließen (NPR-37075).

### Übersetzungsprojekte {#translation-65110}

* Die automatische Promotion des Übersetzungsstarts schlägt mit einer Ausnahme fehl (NPR-37528).

* Durch die Übersetzung des Experience Fragment werden die Verweise für die Sprachkopie der URL nicht aktualisiert (NPR-37522).

* Wenn ein Experience Fragment in einem Pfad erstellt wird, der nicht mit dem Pfad der Sprach-Stamm-Struktur übereinstimmt, spiegelt das Hinzufügen dieser Seite zu einem Übersetzungsprojekt eine leere Fehlermeldung wider (NPR-37425).

* Wenn eine Seite (Englisch), die Experience Fragments enthält, geändert und zur Übersetzung gesendet wird, werden die bereits übersetzten Experience Fragments durch englische Inhalte überschrieben (NPR-37283).

* Der Filter für Übersetzungsanbieter funktioniert nicht ordnungsgemäß (NPR-37186).

* Experience Fragment- und Accordion-Komponenten werden nicht nativ für den Site-Beispielinhalt übersetzt (NPR-37170).

* Nach der Aktualisierung auf [!DNL Experience Manager] 6.5.9.0 wird durch Hinzufügen einer Seite zum Übersetzungsprojekt eine leere Fehlermeldung angezeigt (NPR-37105).

* Beim Hinzufügen von Seiten innerhalb des Launches sind die Übersetzungsseiten mit ähnlichen Namen nicht im Projekt enthalten (NPR-37082).

* Beim Exportieren eines Formularwörterbuchs als .xliff-Datei mithilfe der Übersetzerschnittstelle ist die Feldreihenfolge der exportierten Datei falsch (NPR-37048).

* Beim Rollout einer übergeordneten Seite aus einem Übersetzungsprojekt werden die sprachspezifischen untergeordneten Seiten gelöscht (NPR-36998).

* Beim Erstellen eines Übersetzungsprojekts führt die zyklische Referenzierung der Seiten zu einem Start, was zu einem Trigger führt (CQ-4332982).

* Der Link zum Experience Fragment im übersetzten Experience Fragment und auf der Seite enthält die Launch-Referenz (NPR-37649).

### Sling {#sling-65110}

* Beim Hochladen eines neuen Pakets wird der Speicheralias in der MapEntries-Karte entfernt (NPR-37067).

### Workflow {#workflow-65110}

* `Deactivate` -Methode in `InboxOmniSearchHandler` zeigt eine Null-Zeiger-Ausnahme an (NPR-37533).

### [!DNL Communities] {#communities-65110}

* Der Benutzer kann der Seite keinen Kommentar hinzufügen, die `Post` Operation schlägt mit Fehlercode 500 fehl (NPR-37156).

* Bei der Bereitstellung der Anwendung wird ein Segment, das keine Ausnahme gefunden hat, aufgrund der langwierigen Sitzung von SyncManager beobachtet (NPR-37351).

* Der Benutzer kann die Thread-Antworten nicht in dem Forumsdiskussionsbeitrag sehen (NPR-37083).




<!--
Need to verify with Engineering, the status is currently showing as Resolved
-->


<!--
### [!DNL Brand Portal] {#brandportal-65110}

*

-->

### [!DNL Forms] {#forms-65110}


>[!NOTE]
>
>* [!DNL Experience Manager Forms] veröffentlicht die Add-on-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.


**Adaptive Formulare**

* Barrierefreiheit - Wenn Sie die `Wizard` Layout für ein Bedienfeld in einem adaptiven Formular verwenden, verfügen die Navigationsschaltflächen nicht über Aria-Beschriftungen und Rollen (NPR-37613).

* Überprüfungen eines Datumsfelds in einem adaptiven Formular funktionieren nicht erwartungsgemäß (NPR-37556).

* Wenn der Beschriftungstext für die Kontrollkästchen- und Optionsfeld-Komponenten lang ist, passt der Text nicht richtig. (NPR-37294)

* Wenn Sie Stiländerungen auf die Dankesnachricht der AEM Forms-Container-Komponente anwenden, werden die Änderungen nicht im adaptiven Quellformular repliziert (NPR-37284).

* Unterschiede im Wert der `Switch` -Komponente auf der Benutzeroberfläche und im Backend (NPR-37268).

* Wenn Sie die Tastaturbefehle zum `Submit` und drücken Sie die `Enter` -Schlüssel können Sie das adaptive Formular mehrmals senden (CQ-4333993).

* Der Vorgang &quot;Remove&quot;für die Komponente &quot;File Attachment&quot;funktioniert nicht wie erwartet (NPR-37376).

* Wenn eine Beschriftung für ein Feld 1000 Zeichen in einem adaptiven Formular überschreitet, das in verschiedene Sprachen übersetzt wird, kann das Wörterbuch die Übersetzung der Beschriftung nicht abrufen (CQ-4329290).

**Document Services**

* Bei Verwendung des Assembler-Dienstes wird ein Fehler angezeigt (NPR-37606):

   ```TXT
     500 Internal Server Error
   ```

* Wenn die Dokumentanlagen an den Assembler-Dienst übergeben werden, wird die folgende Ausnahme angezeigt (NPR-37582):

   ```TXT
     com.adobe.livecycle.assembler.client.ProcessingException: ⁪: Failed to execute the DDX
   ```

* Fehlende schließende Klammern aus Daten nach der Konvertierung eines PDF-Dokuments in ein PDF-A/1B-PDF-Dokument (NPR-37608).

**HTML5-Formulare**

* Wenn Sie AEM 6.5.10.0 installieren, funktioniert die HTML-Vorschau für ein XDP-Formular nicht (NPR-37503, CQ-4331926).

* Überlappende Textprobleme bei der Migration der PDF forms auf HTML 5-Formulare in verschiedenen Sprachen (NPR-37173).

**Briefe**

* Wenn Sie einen Brief senden und ihn in der HTML-Ansicht erneut öffnen, bleibt die Position der Textdokumentfragmente nicht gleich (NPR-37307).

**Formular-Workflow**

* Im Fall eines eingebetteten Container-Workflows erhalten Sie mehrere E-Mails zum Abschluss des Workflows, selbst wenn Sie die `Notify on Complete of Container Workflow` (NPR-37280).

**Foundation JEE**

* Nach der Installation von AEM 6.5 Forms Service Pack 9 sind die CRX-Repository-URLs nicht mehr verfügbar (NPR-37592).

**Behobene Probleme in AEM Forms 6.5.11.1**

>[!NOTE]
>
>Wenn Sie noch kein Upgrade auf AEM 6.5.11.0 Forms durchgeführt haben, installieren Sie das Add-On-Paket für AEM Forms 6.5.11.1 direkt. Wenn Sie AEM 6.5.11.0 Forms installiert haben, empfiehlt Adobe, auf AEM 6.5.11.1 Forms zu aktualisieren.

* Übermittlungsaktionen, E-Mail senden und Workflow aufrufen funktionieren nach der Installation des Add-On-Pakets Forms 6.5.11.0 nicht mehr.
* Der Vorgang CreatePDF stoppt die Konvertierung von Microsoft Word-Dokumenten in PDF-Dokumente, nachdem das Add-On-Paket für Forms 6.5.11.0 installiert wurde.
* (Nur JEE) Kritische Sicherheitslücken (CVE-2021-44228 und CVE-2021-45046), die für Apache Log4j2 gemeldet wurden.
* (Nur JEE) Assembler DSC in Patch 6.5.11.0 enthält falsche Metainfo-ähnliche Spezifikations-Version und Impl-Version.


Informationen zu Sicherheitsupdates finden Sie unter [[!DNL Experience Manager] Seite mit Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.11.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.11.0 ist Experience Manager 6.5 erforderlich. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen.
* Der Service Pack-Download ist auf Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.11.0 mithilfe des Package Managers auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, die [!DNL Adobe Experience Manager] 6.5.11.0-Paket.

### Service Pack installieren {#install-service-pack}

So installieren Sie das Service Pack auf einem [!DNL Adobe Experience Manager] 6.5-Instanz ausführen:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager] -Instanz.

1. Laden Sie das Service Pack herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.11.zip).

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. Normalerweise tritt dieses Problem in [!DNL Safari] -Browser, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, automatisch zu installieren [!DNL Experience Manager] 6.5.11.0 auf einer funktionierenden Instanz:

A. Platzieren Sie das Paket in `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwendung `cmd=install&recursive=true` damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.11.0 unterstützt nicht die Installation von Bootstraps.

**Installation überprüfen**

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge an `Adobe Experience Manager (6.5.11.0)` under [!UICONTROL Installierte Produkte].

1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für die Verwendung mit dieser Version zertifiziert sind, finden Sie in der [technische Anforderungen](/help/sites-deploying/technical-requirements.md).

<!-- 

### Install Adobe Experience Manager Forms add-on package {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Skip if you are not using Experience Manager Forms. Fixes in Experience Manager Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

1. Ensure that you have installed the Adobe Experience Manager Service Pack.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>Experience Manager 6.5.10.0 includes a new version of [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). If you are using an older version of AEM Forms Compatibility Package and updating to Experience Manager 6.5.10.0, install the latest version of the package post installation of Forms Add-On Package.

### Install Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Skip if you are not using AEM Forms on JEE. Fixes in Adobe Experience Manager Forms on JEE are delivered through a separate installer.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes](jee-patch-installer-65.md).

>[!NOTE]
>
>After installing the cumulative installer for Experience Manager Forms on JEE, install the latest Forms add-on package, delete the Forms add-on package from the `crx-repository\install` folder, and restart the server.

-->

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.11.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.11/).

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.11</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstatt im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar`. Es gibt also keine `classifier`, mit `apis` als Wert für die `dependency` -Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die als veraltet gekennzeichnet sind mit [!DNL Experience Manager] 6.5.7.0. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Die **[!UICONTROL AEM Cloud Services-Opt-in]** Der Bildschirm wird nicht mehr unterstützt, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration wurde in Experience Manager 6.5 aktualisiert. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O] und unterstützt die wachsende Rolle von Adobe Launch als Instrument [!DNL Experience Manager] Seiten für Analysen und Personalisierung verwenden, ist der Opt-in-Assistent funktionell irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O] Integrationen über die entsprechenden [!DNL Experience Manager] Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Wenn Sie AEM 6.5 Service Pack 11 installieren und versuchen, die Status-ZIP-Datei herunterzuladen, lädt Experience Manager eine beschädigte Datei herunter. Herunterladen und installieren [AEM Sites SEO Index Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip) auf Ihrer AEM Instanz vor dem Herunterladen der ZIP-Datei, um das Problem zu beheben.

* As [!DNL Microsoft Windows Server 2019] unterstützt nicht [!DNL MySQL 5.7] und [!DNL JBoss EAP 7.1], [!DNL Microsoft Windows Server 2019] unterstützt keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie ein Upgrade [!DNL Experience Manager] -Instanz von 6.5 bis 6.5.10.0, können Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5, die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] und veröffentlichen Sie einen verschachtelten Ordner in [!DNL Brand Portal]. Der Titel des Ordners wird jedoch nicht aktualisiert in [!DNL Brand Portal] bis die Veröffentlichung des Stammordners erfolgt ist.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

* Beim Versuch, Inhaltsfragmente oder Sites/Seiten zu verschieben/zu löschen/zu veröffentlichen, tritt ein Problem auf, wenn Inhaltsfragmentverweise abgerufen werden, da die Hintergrundabfrage fehlschlägt. d. h. die Funktionalität funktioniert nicht.
Um den korrekten Vorgang sicherzustellen, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten hinzufügen `/oak:index/damAssetLucene` (Eine Neuindizierung ist nicht erforderlich) :

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die in [!DNL Experience Manager] 6.5.11.0:

* [Liste der in Experience Manager 6.5.11.0 enthaltenen OSGi-Bundles](assets/65110_bundles.txt)

* [Liste der in Experience Manager 6.5.11.0 enthaltenen Inhaltspakete](assets/65110_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Siehe [Kontaktaufnahme mit dem Adobe-Support](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

## Wichtige seit [!DNL Adobe Experience Manager] 6.5 SP10{#key-releases-since-last-sp}

Zwischen dem 26. August 2021 und dem 25. November 2021 veröffentlichte Adobe zusätzlich zu den Service Packs Folgendes:

* [!DNL Adobe Experience Manager] as a Cloud Service [2021.9.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/2021/release-notes-2021-9-0.html) und [2021.10.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

* [[!DNL Experience Manager] Desktop-Programm 2.1 (2.1.3.4)](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=de).

* [Experience Manager Screens: Feature Pack 202109](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202109.html?lang=de)


>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

