---
title: Versionshinweise zum AEM 6.5 Service Pack
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Service Pack 5.
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: d51577195e969ff8af31be49159ff575e3654cc9
workflow-type: tm+mt
source-wordcount: '4476'
ht-degree: 12%

---


# Adobe Experience Manager 6.5 Service Pack Release Notes {#aem-service-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager 6.5** |
|---|---|
| Version | 6.5.5.0 |
| Typ | Service Pack-Version |
| Datum       | 04. Juni 2020 |
| Download-URL | [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/AEM-6.5.5.0-Service-Pack), [Softwareverteilung ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) |

## What&#39;s included in Adobe Experience Manager 6.5.5.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.5.0 is an important update that includes new features, key customer requested enhancements and performance, stability, security improvements, released since the general availability of 6.5 release in **April 2019**. Es kann über Adobe Experience Manager (AEM) 6.5 installiert werden.

Zu den wichtigsten Funktionen und Verbesserungen, die in AEM 6.5.5.0 eingeführt wurden, zählen:

* Customizing the column names that display in AEM Inbox.

* Verbesserung der Barrierefreiheit in verschiedenen Bereichen des AEM Web Content-Management (WCM), z. B. in den Bereichen Seiteneditor, Kernkomponenten, RTE und Admin-Benutzeroberfläche.

* Speichern einer interaktiven Kommunikation als Entwurf.

* Unterstützung [!DNL Oracle WebLogic 12] für AEM Forms on JEE.

* Die Handhabung von Ausnahmen wurde jetzt im Fluss der Benutzeroberfläche [!DNL Adobe Experience Manager] &quot;Assets&quot;verbessert.

* Eine neue Methode `getRemoteAssetPublishURL` wird der `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi` Oberfläche hinzugefügt, um die Veröffentlichungs-URL für dynamische Medien in Scene7 abzurufen.

* [Barrierefreiheitsverbesserungen](#assets-6550-changes) in [!DNL Adobe Experience Manager] Assets in Übereinstimmung mit den Web Content Accessibility Guidelines (WCAG).

* Die Paketfreigabe-Integration mit Adobe Experience Manager wurde entfernt.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.3 aktualisiert.

Eine vollständige Liste der Funktionen, wichtigen Highlights und wichtigen Funktionen, die mit AEM 6.5 Service Pack 5 eingeführt wurden, finden Sie unter [Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 5](new-features-latest-service-pack.md) .

Im Folgenden finden Sie die Liste der Fehlerbehebungen in Version [!DNL Experience Manager] 6.5.5.0.

### Sites {#sites-6550}

* AEM-Sites bietet eine Option zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung einer Seite über ihren Alias. Die Option funktioniert nicht (NPR-33415).
* Wenn ein Layout-Container aus einer Vorlage mit mehreren Vorlagen gelöscht wird, wird die Vorlage nicht korrekt dargestellt (NPR-33347).
* Wenn eine AEM-Siteseite zu einem großen Inhaltsset mit mehreren Live-Kopien gehört, schlägt die Vorschau des Seitenversionsverlaufs fehl (NPR-33311).
* Wenn Sie den Befehl &quot;Verschieben&quot;verwenden, um eine AEM-Siteseite umzubenennen, wird der Seitentitel nicht aktualisiert (NPR-33264).
* Wenn Sie Seiten durch die Ansicht verschieben, werden die Spalten ausgeblendet (NPR-33216).
* Wenn der Name einer lokalen Komponente in einer Sprachkopie identisch mit dem Namen einer Komponente im Entwurf ist und die Komponente aus dem Entwurf herausgegeben wird, wird der Name der lokalen Komponente nicht mit dem Begriff _msm_move (NPR-33208) versehen.
* Das Seitenumleitungs-Servlet hängt .html an eine AEM-Sites-URL an, wobei ResourceType nicht cq:Page (NPR-33176) lautet.
* Wenn Sie eine Unterstruktur einfügen, gibt es keine Option zu entscheiden, ob die entsprechenden Unterseiten eingefügt werden sollen oder nicht (NPR-33149).
* Die Anzahl der Ergebnisse in Live-Verwendungen einer Komponente ist auf die Zahl 49 beschränkt (NPR-33058).
* Wenn Sie ein Inhaltsfragment auf einem Schema basieren und es einen obligatorischen Textbereich oder ein Pfadfeld enthält, kann das Inhaltsfragment nicht gespeichert werden (NPR-33007).
* Wenn Sie eine benutzerdefinierte Komponente mithilfe der vordefinierten Erlebnisfragmentkomponente erstellen und sie auf den AEM-Siteseiten verwenden, zeigt AEM keine Verweise (Nutzung) für die benutzerdefinierte Komponente (NPR-32852) an.
* Wenn Sie einen Ordner mit einer großen Anzahl von Verweisen umbenennen, werden viele Verweise auf den Ordner nicht aktualisiert (NPR-32765).
* Wenn Sie die Quellbearbeitungsoption aktivieren, steht sie für Inline-Vollbildoptionen zur Verfügung, bleibt aber für das Bearbeiten des Dialogfelds und der Vollbildoptionen des Rich-Text-Editors (NPR-32763) nicht mehr verfügbar.
* Wenn Sie über ein Multifeld verfügen und es ein erforderliches Feld (wie ein Dropdown-Feld oder ein Pfadfeld) in den Seiteneigenschaften eines Blueprints enthält, werden die Seiteneigenschaften der Live-Kopie nicht gespeichert, wenn eine Seite, die ein solches Multifeld enthält, mit Rollout beendet wird. (NPR-32751)
* Bildschirmlesehilfen können die Überschriftenstruktur nicht zum Navigieren auf einer Seite verwenden. Darüber hinaus enthält die Registerkarte Komponenten die falsche Beschriftung (NPR-32648).
* Beim Paginieren werden nicht alle Elemente (NPR-32605) in der Erlebnisfragmentauswahl geladen.
* Autorenberechtigungen zum Lesen, Ändern, Erstellen und Löschen von Live-Kopien werden widerrufen. Jeder Autor musste explizit Lese- und Änderungsberechtigungen zum Verschieben von Seiten in einem Blueprint (NPR-32550) bereitstellen.
* Inhaltsersteller können Launch für eine Seite, die mit Adobe Analytics (NPR-32548) integriert ist, nicht erstellen.
* Wenn ein Benutzer die Vererbung mit der Synchronisierung fortsetzt, wird die Live-Kopie der übergeordneten Seite nicht mit dem Entwurf synchronisiert und zeigt einen falschen Status an (NPR-32500).
* Das Laden der AEM-Sites-Editor-Seite dauert mehr als 15 Sekunden (NPR-32413).
* In bestimmten Feldern wird die Option Vererbung abbrechen nicht angezeigt (NPR-32362).
* Wenn Sie einen Pfad für eine Erlebnisfragment-Komponente auswählen und das Kontrollkästchen &quot;Auswahldialogfeld öffnen&quot;aktivieren, werden Sie nicht zum ausgewählten Pfad im Pfadbrowser (NPR-32308) navigiert.
* Wenn Sie von AEM 6.2 auf AEM 6.5 aktualisieren, wird die Komponente Parsys der statischen Vorlagen nicht korrekt angezeigt. Die Höhe der Parsys-Komponente wird auf 0 gesetzt und die darin enthaltenen Komponenten sind nicht sichtbar. (NPR-33663).
* Wenn ein Benutzer einen Layout-Container kopiert und auf derselben Seite eingefügt hat, werden Komponenten in einem Layout-Container nicht angezeigt (NPR-33648).
* Dispatcher Health Check zeigt eine `Invalid cookie header` Warnmeldung in den Protokolldateien an (NPR-33629).

### Assets {#assets-6550-changes}

**Verbesserungen der Barrierefreiheit in Experience Manager Assets**

* Es ist jetzt möglich, den Tastaturfokus auf die Liste [!UICONTROL Kommentare] und die Option zum [!UICONTROL Erstellen] von Versionskommentaren unter Neue Version  erstellen im [!UICONTROL Timeline] -Bedienfeld von Assets (NPR-33424) zu lenken.

* Es ist jetzt möglich, die [!UICONTROL Ansicht Einstellungen] für Assets zu erreichen und die Einstellungen im Dialogfeld [!UICONTROL Ansicht Einstellungen] mithilfe der Tastenkombinationen (NPR-33420) zu ändern.

* Das Dropdown-Feld &quot;Liste&quot;des Kombinationsfeldes (in verschiedenen Feldern auf verschiedenen Seiten) zeigt nun Einträge als Liste von Optionen an, die von Bildschirmlesehilfen angekündigt werden können (NPR-33516).

* The sort functionality of sortable headers (in list view, [!UICONTROL Timeline] view, and [!UICONTROL Manage Publication] page) are now announced by screen readers and sorting controls on column headers are accessible using keyboard (NPR-32979).

* The clickable elements (such as comment cards, version updates, combo boxes, and chevron icons of menus) are now focusable and actionable using keyboard (NPR-33514).

* Functionality (or purpose of action) of insights icons (for usage, impressions, and clicks) on [!UICONTROL Insights View] are now correctly announced by screen readers (NPR-33513).

* Schreibgeschützte Formularfelder (z. B. deaktivierte Felder auf der Registerkarte [!UICONTROL &quot;] Einfach&quot;von Asset- [!UICONTROL Eigenschaften]) können jetzt über die Tastatur fokussiert werden (NPR-33493, CQ-4273031).

* Labels in various input fields are now permanent labels (thus accessible) and not just placeholder labels, which disappeared when text was entered (NPR-33475).

* Different heading levels (such as page titles and section headings) are now perceived as headings with different levels to screen reader users (NPR-33471).

* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen (auf der Seite mit Kopf- und Zoomoptionen für Assets, Ordnernavigation), können jetzt über eine Tastatur aufgerufen werden (NPR-33468, CQ-4271412).

* Die [!UICONTROL Optionen]-, [!UICONTROL Scope]- und [!UICONTROL Workflows] -Fortschrittsindikatoren auf der Seite &quot;Veröffentlichung  verwalten&quot;werden jetzt von Bildschirmlesehilfen als Fortschrittsindikatoren anstelle von Registerkarten korrekt gelesen (NPR-33416).

* The color of star rating icons (such as in [!UICONTROL Rating] section of [!UICONTROL Advanced] tab in asset [!UICONTROL Properties] or in card view) is changed for appropriate contrast to be visible to users with limited vision and without perception of color (NPR-33414).

* Nach oben zeigender Pfeil neben dem Feld [!UICONTROL Kommentar] auf der Seite mit den Asset-Details können Sie jetzt mit den Tastaturbefehlen (NPR-33397) aufrufen.

* The expanded and collapsed states of [!UICONTROL Tags] dialog on asset [!UICONTROL Properties] and left rail navigation (on assets user interface) are now correctly announced by screen readers (NPR-33396).

* Die Titel aller durchsuchten Seiten auf [!DNL Adobe Experience Manager] Assets sind jetzt eindeutig (NPR-33343).

* Beim Navigieren in der Baumstruktur werden verschiedene Elemente des Baumdiagrammsteuerelements jetzt korrekt von Bildschirmlesehilfen (NPR-33304) angekündigt.

* Die verschiedenen Versionen der Assets in der [!UICONTROL Timeline] -Ansicht auf der Seite mit den Asset-Details können jetzt mit Tastaturbefehlen (NPR-33283) aufgerufen werden.

* Die Namen von Suchvorschlägen, die im Kombinationsfeld von Omniture enthalten sind, werden jetzt von Bildschirmlesehilfen bei Verwendung der Suchfunktion (NPR-33280) angekündigt.

* Klickbare Elemente und [!UICONTROL Gehe zu Link] in der [!UICONTROL Bezugsleiste] werden jetzt von Bildschirmlesehilfen als anklickbare Elemente (NPR-33278) angekündigt.

* Informationen zur Tabellenstruktur (wie z.B. Zeile 1, Zelle 1, Tabelle) des Dialogfelds [!UICONTROL Link] freigeben werden von Bildschirmlesehilfen nicht mehr angekündigt, wenn der Dialog geöffnet wird (NPR-33268).

* Der Zweck verschiedener Kombinationsfeldelemente (z. B. Pfadfeld und Option zum Öffnen des Auswahldialogfelds auf der Registerkarte Grundeinstellungen der Asset-Eigenschaften) wird nun von Bildschirmlesehilfen korrekt angekündigt (NPR-33235).

* Die Informationen, die die Zeilen in der Tabelle &quot;Ansicht&quot;auswählen können, werden jetzt Bildschirmlesehilfen-Benutzern mitgeteilt, wenn der Tastaturfokus auf sie gelegt wird. Diese Information wird angekündigt, wenn der Mauszeiger auf die Zeilen bewegt wird (NPR-33234).

* Die Optionen (mit [!UICONTROL x]) zum Entfernen der einzelnen markierten Tags unter dem Feld &quot; [!UICONTROL Tags] &quot;auf der Registerkarte &quot; [!UICONTROL Einfach] &quot;der [!UICONTROL Eigenschaften] stehen jetzt Sprachausgabeprogrammen zur Verfügung (NPR-33206).

* Die Kalenderdatumsauswahl kann jetzt mithilfe der Tastatur nach Bildschirmlesehilfen-Benutzern und sichtbaren Keyboard-Benutzern fokussiert werden (NPR-33200).

* Der Umschalter zum Wechseln zwischen der Ansicht der Liste und der Ansicht der Karte stellt nun ihre Funktion (zum Anpassen von Ansichten) an Bildschirmlesehilfen (NPR-33069) korrekt dar.

* Das Menü in der linken Leiste ist jetzt verfügbar. Funktionalität und Zweck der Erweiterung des Menüs werden von Bildschirmlesehilfen entsprechend angekündigt (NPR-33068).

* Liste-Box und viele andere Benutzeroberflächenelemente sind jetzt für Benutzer ohne Sichtkontakt mit Bildschirmlesehilfen verfügbar. Die folgenden Informationen werden von Bildschirmlesehilfen (NPR-33040) angekündigt:

   * ob die Benutzereingabe für ein Element vor dem Senden des Formulars erforderlich ist.
   * ob ein Element nicht bearbeitbar ist.
   * ob ein Widget ausgewählt ist oder nicht.

* Die Option zum Öffnen der Filter-Seitenleiste kann jetzt über die Tastatur aufgerufen werden (NPR-32842, CQ-4273018).

* Die Kontrollkästchen-Steuerung in der Spaltenüberschrift der Ansicht der Liste ist jetzt verfügbar und die Verwendung der Steuerung wird von Bildschirmlesehilfen angekündigt (NPR-32722, NPR-33005).

* Die Felder für Stunden (HH) und Minuten (mm) in der Datumsauswahl im Kalender sind jetzt dauerhafte Beschriftungen anstelle von Platzhalterbeschriftungen und verschwinden nicht, wenn der Benutzer Text in diese Felder eingibt (NPR-32720).

* Der Linktext der Benachrichtigungen (die nach dem Klicken auf das Glockensymbol angezeigt werden) wird jetzt für Bildschirmlesehilfen-Benutzer bekannt gegeben, die mit der Tabulatortaste auf jeden Link zugreifen (NPR-32645).

* [!UICONTROL Die Optionen]&quot;Auswählen&quot;, &quot; [!UICONTROL Herunterladen]&quot;, &quot; [!UICONTROL Eigenschaften]&quot;und &quot; [!UICONTROL Weitere Aktionen] &quot;auf Asset-Karten in der [!UICONTROL Insight-Ansicht] sind jetzt über die Tastatur verfügbar (NPR-32609).

* Visuell ausgeblendete Inhalte (z. B. Inhalte der Kopfzeilenmenüleiste in Suchergebnissen) werden von Bildschirmlesehilfen beim Zugriff über die Tastatur nicht mehr angekündigt (NPR-32606).

* Zweck der Beschriftungen für Kontrollen, die in der Kalenderdatumsauswahl in die nächsten und vorherigen Monate verschoben werden sollen, werden jetzt von Bildschirmlesehilfen (NPR-32604) angekündigt.

* Sternbewertungs-Symbole können jetzt mithilfe von Tastenkombinationen fokussiert und bearbeitet werden (NPR-32513).

* Die Funktion zur Steuerung der Videolautstärke ist jetzt über Registerkarten (zum Fokus auf Lautstärkeregler) und Pfeiltasten (zum Einstellen der Lautstärke) auf der Tastatur verfügbar (NPR-32065).

* Der Zweck der Eingabefelder mit Untergrenze ([!UICONTROL Von]) und Obergrenze ([!UICONTROL Bis]) des Dateigrößenfilters wird nun nicht-seighted Screen Reader Users (NPR-32064) bekannt gegeben.

* Das Menü &quot; [!UICONTROL Sprachen] &quot;im Formular &quot; [!UICONTROL Erstellen und Übersetzen] &quot;steht jetzt Bildschirmlesehilfen im Durchsuchenmodus zur Verfügung (CQ-4293906).

* Das [!UICONTROL Referenzen] -Bedienfeld ist jetzt mit folgenden Erweiterungen verfügbar (NPR-33261, CQ-4293798):

   * Im Durchsuchen-Modus wird der Bildschirmlesehilfen-Fokus nicht mehr auf ausgeblendete mehrzeilige Bearbeitungsfelder unter [!UICONTROL Site-Referenzen], [!UICONTROL Asset-Referenzen], [!UICONTROL Kopien]und [!UICONTROL Formularverweise] verschoben.

   * Bildschirmlesehilfen geben jetzt die Rolle der Elemente [!UICONTROL Site-Referenzen] und [!UICONTROL Sprachkopien] an.

   * Der Fokus von Bildschirmlesehilfen im Durchsuchen-Modus wechselt in einer aussagekräftigen Sequenz zu verschiedenen Elementen.

* [!UICONTROL Die Metadaten-Schema-Editor] -Seite und die zugehörigen Elemente sind jetzt über die Tastatur verfügbar und können mit Bildschirmlesehilfen verwendet werden (CQ-4290962, CQ-4272953).

* Der Zweck des [!UICONTROL x] -Symbols bei der Option zum Entfernen der aktuell ausgewählten Tags wird zusammen mit der Anzahl der ausgewählten Tags (CQ-4273017) angekündigt.

* Dekorative Symbole und Bilder werden jetzt von Bildschirmlesehilfen ignoriert, um Verwirrung für nicht sichtbare Benutzer mit einer Bildschirmlesehilfe zu vermeiden (CQ-4272944).

**Behobene Probleme in Experience Manager-Assets**

[!DNL Adobe Experience Manager] 6.5.5.0 Assets bieten Korrekturen an folgenden Problemen:

* [!UICONTROL Die Option &quot;Beginn] &quot;im Dialogfeld &quot;Arbeitsablauf  erstellen&quot;für Assets in einer Sammlung ist deaktiviert, sodass Workflow nicht ausgelöst wird (NPR-32471).

* Wenn Sie in Metadaten-Schemas die Dropdownoption &quot;Kaskadieren&quot;verwenden und eine Dropdown-Option mit einem Apostroph (aus der untergeordneten Dropdown-Liste) auswählen und speichern, wird die ausgewählte Apostroph-Option nach dem erneuten Öffnen der Asset- [!UICONTROL Eigenschaften] ausgeblendet (NPR-32649).

* [!UICONTROL Asset Insights Sync Job] stoppt und schlägt fehl, wenn ungültige Einträge (auf der Seite von Analytics) auftreten, anstatt zum nächsten Eintrag (NPR-32674) zu wechseln.

* Gyroscope ist nicht funktionsfähig, da Bewegungssensoren standardmäßig in mobilen Browsern im Panorama-Viewer deaktiviert sind (CQ-4272937).

* [!UICONTROL Der Assistent zur Konfiguration] von verbundenen Assets funktioniert mit dem Fehler 404 nicht, wenn 6.5.3 unter 6.5.1 (NPR-32730) installiert wird.

* Während des XMP-Schreibvorgangs ändern alle benutzerdefinierten Metadateneigenschaften des Namensraums das benutzerdefinierte Präfix des Namensraums in &quot;ns2&quot;anstelle des konfigurierten Namensraums (NPR-32748).

* Verzögertes Laden wird nicht ausgelöst und es werden nur 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32750).

* `NullPointerException` wird aufgrund fehlender Node-Voreinstellungen im neu erstellten Profil (SAML/SSO) beobachtet. Dieser Fehler verhindert, dass neu angemeldete Benutzer die [!DNL Adobe Experience Manager Stock] Integration verwenden (NPR-32777).

* In Protokollen zum Öffnen einer intelligenten Sammlung mit mehr als 10.000 Assets (NPR-32980) werden seitenübergreifende Warnungen angezeigt.

* Asset names are changed to lowercase when moving assets from one folder to another in [!DNL Adobe Experience Manager] working on Dynamic Media Scene7 runmode (NPR-32995).

* A searched asset cannot be deleted after navigating to its properties from the search results and then going back to search results to delete it (NPR-32998).

* [!UICONTROL Next] option remains disabled on selecting destination folder in [!UICONTROL Move Assets] interface (NPR-33356).

* [!UICONTROL Next] option is not enabled on selecting parent node (where single child folder is visible) and then selecting child folder (NPR-33275).

* Check in and check out permissions are disabled on Adobe Asset Link (AAL) for users with delete permission, even if other permissions such as read, create, or modify are allowed to them (NPR-33272).

* Im Dialogfeld zum Herunterladen von Assets (NPR-33167) sind keine Smart-Zuschneiden-Darstellungen verfügbar.

* Ausnahmen sind in Protokollen beim Öffnen der Rail-Darstellungen für eine PDF-Datei unter einem Profil mit intelligenten Zuschnitten (CQ-4294201) zu beobachten.

* Bildvorgaben werden nicht veröffentlicht, wenn der Synchronisierungsmodus [!UICONTROL für] dynamische Medien in AEM mit dem Scene7-Laufzeitmodus für dynamische Medien standardmäßig deaktiviert ist (CQ-4294200).

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert, und die Workflow-Instanz zeigt angehaltene Instanzen des DAM-Aktualisierungsassets (CQ-4293916).

* Das Erstellen einer Konfiguration für dynamische Medien in AEM funktioniert, auf der Benutzeroberfläche geschieht jedoch nichts bei der Auswahl von Speichern (CQ-4292442).

* Die Vorschau von f4v-Video-Assets funktioniert bei der progressiven Wiedergabe auf Safari/Mac nicht (CQ-4289844).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit Punkt- `.` Zeichen im Namen befindet (CQ-4289337).

* Die Miniaturansicht ist beschädigt, und das Videoverarbeitungsbanner wird nicht angezeigt, wenn ein Video kopiert wird (CQ-4284125).

* Beim Dimensional Viewer werden in Firefox bei einigen Modellen mit leeren Ansichten fälschlicherweise leere Miniaturansichten angezeigt (CQ-4283447).

* Die in Version 6.5.5.0 behobenen Leistungsprobleme lauten (CQ-4279206):

   * Es dauert zu lange, bis große Binärdateien auf die Server der dynamischen Medienverarbeitung hochgeladen werden.

   * Die Zeit für die Erstellung von Miniaturbildern in AEM wird aufgrund der Architektur von Scene7 für dynamische Medien verlängert.

* Migrationsprobleme mit dynamischen Medien in Scene7 schlagen bei Kunden mit einer großen Anzahl von Assets fehl (CQ-4279206).

* Das Layout des 360-Grad-Viewers für Video ist beschädigt, wenn es verwendet `setVideo` wird, und das Video wechselt bei der Verwendung nach unten `video= modifier` (CQ-4263201).

* Während der Installation des AEM SDL-Pakets (NPR-33175) wird eine Fehlermeldung angezeigt.

### Plattform {#platform-6550}

* Der [!DNL Sling] Filter wird nicht aufgerufen, wenn der `sling:match` Karteneintrag unter `/etc/maps` (NPR-33362) erstellt wird.
* AEM stürzt aufgrund eines Segmentierungsfehlers ab [!DNL Apache Lucene] (NPR-32988).
* [!DNL Jackson] Kernpaket fehlt in der AEM Uber-JAR-Datei (NPR-32848).
* CRXDE Lite lädt keine Inhalte für Benutzer ohne READ-Berechtigung für die `jcr:primaryType` Eigenschaft eines Knotens (NPR-32611).
* [!DNL Granite] Die Planung der Maintenance-Aufgabe wird während der AEM-Bereitstellung zu oft neu initialisiert (CQ-4294627).
* Wenn eine SQL-Abfrage länger ausgeführt wird (z. B. 7 Stunden), reagiert AEM nicht mehr (NPR-33044).

### Benutzeroberfläche {#ui-6550}

* Die Auswahl des Optionsfeldes bleibt in einem Multifeld (NPR-33309) nicht erhalten.
* Lazy Loading Limit funktioniert nicht für die Liste Ansicht (NPR-33124).
* Die Seite mit den Omniture Suchergebnissen zeigt keine Meldung an, wenn keine Übereinstimmungen vorliegen (NPR-32974).
* Der Omniture-Filter gibt alle Übereinstimmungen unter dem `/content` Knoten zurück, wobei der ausgewählte Speicherort ignoriert wird (NPR-32849).

### Integrationen {#integrations-6550}

* Der interne Cache wird gelöscht, wenn eine Seite mit einer Adobe-Zielgruppe-Komponente veröffentlicht wird (NPR-33162).
* Die Integration mit Adobe Zielgruppe funktioniert nicht mit [!DNL Windows Internet Explorer] 11 (NPR-33111).
* Beim Konfigurieren von Adobe Zielgruppe werden die Felder [!UICONTROL Firma] und [!UICONTROL Report Suite] nicht angezeigt, wenn Sie eine Berichte-Quelle auswählen (NPR-32502).
* Beim Exportieren von Erlebnisfragmenten mit Adobe I/O werden Metadaten wie Source Product nicht in Adobe Zielgruppe (NPR-32159) exportiert.
* Autorisierte IMS-Benutzer in einer lokalen AEM-Administratorgruppe können keine IMS-Konfigurationen erstellen oder ändern (NPR-33045).
* Auf der Seite &quot;Adobe Launch-Konfigurationen&quot;werden nicht alle Datensätze angezeigt (NPR-33011).
* Benutzer in der Gruppe &quot;Inhaltsersteller&quot;können die Eigenschaften einer Adobe-Zielgruppe aufgrund eines JavaScript-Fehlers (NPR-32996) nicht bearbeiten.

### Übersetzungsprojekte {#translation-6550}

* Übersetzte Tags werden nicht aus Übersetzungsdiensten von Drittanbietern (NPR-33154) in AEM importiert.
* Auf der Seite &quot;Übersetzungskonfiguration&quot;wird ein falscher Übersetzungsanbieter angezeigt als der für die Übersetzung verwendete (NPR-32971).
* Adding an experience fragment folder to an existing translation project creates a new project (NPR-32843).
* A `NullPointerException` error is seen in the logs on running a translation job (NPR-32628).

### WCM {#wcm-6550}

* Page Editor - The [!DNL Sites] Page Editor does not allow the keyboard-only users to skip to the main content instead of shifting tab focus through all options available in the header (CQ-4293883).
* Page Editor  - Panels that use Well component and include saved data do not display due to updates in [!DNL Chrome] and [!DNL Firefox] versions (CQ-4292995).
* MSM - Deleting a component from the page does not delete the component from the published version of the page (CQ-4292360).

### Brand Portal {#assets-brand-portal-6550}

* Removing a published metadata schema from [!DNL Brand Portal] results in an error (CQ-4292063).
* If an administrator configures [!DNL Experience Manager Assets] 6.5.4 with Brand Portal via Adobe Developer Console, the [!DNL Brand Portal] user is not able to publish a contribution folder&#39;s asset from [!DNL Brand Portal] to [!DNL Experience Manager]. (NPR-33046).
* Duplicate replication of the parent folders causing conflicts (NPR-33001).

### Communities {#communities-6550}

* Cannot delete a card in moderation console using the quick edit menu option (NPR-33117).
* An error occurs on accessing the [!UICONTROL Activity Stream] page (NPR-33146).
* Groups deleted on author instance are not removed from all publish instances (NPR-33199).
* Authors, after creating a new group, are not redirected to the [!UICONTROL Community Group] section on [!DNL Internet Explorer] 11 (NPR-33205).
* Accessing a message in AEM Inbox does not change the status of the message to Read (NPR-32764).
* Editing a [!DNL Communities] group and changing the thumbnail image does not update the group thumbnail image (NPR-32599).
* A user is not able to send an email to another user in a community (NPR-32598).
* A submitted blog does not display until the user refreshes the page (NPR-32391).
* While creating a version of notifications and subscriptions of User Generated Content (UGC), an incorrect ID of the source page is stored (CQ-4279355, CQ-4289703).

### Workflow {#workflow-6550}

* The [!UICONTROL Timeline] option in the left rail takes more time to load than expected (NPR-32851).
* After restarting an AEM instance, the email for the review task for a collection includes an incorrect payload link (NPR-32774).

### Forms {#forms-6550}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

* Correspondence Management: The order of assets in a target area shuffles after submitting a letter (NPR-33359, NPR-33153).
* Adaptive Forms: When a user edits an adaptive form, the [!UICONTROL Start Workflow] option available in the [!UICONTROL Page Information] menu does not work (NPR-33004).
* Adaptive Forms: The user is not able to save an adaptive form with more than one attachment (NPR-32997).
* Adaptive Forms: Changing the panel layout in an adaptive form results in an error (CQ-4293880).
* Adaptive Forms: A new line to a string in an adaptive forms dictionary adds `&#xa;` characters to the dictionary (NPR-33266).
* Barrierefreiheit adaptiver Formulare: Wenn ein Benutzer ein adaptives Formular als HTML-Formular Vorschau, kann das [!UICONTROL Scribble-Signatur] -Feld den Tabstopp nicht beibehalten (NPR-33159).
* Adaptive Forms accessibility: The error messages that display on submitting an adaptive form do not link to an `aria-describedBy` attribute (NPR-33071).
* Barrierefreiheit adaptiver Formulare: Felder, die in einem adaptiven Formular als Pflichtfelder markiert sind, haben im ARIA-Schema (NPR-33070) nicht das obligatorische Attribut &quot;True&quot;.
* PDFG Service: When a user converts a text file to a PDF, Japanese characters do not render correctly (NPR-33238).
* PDFG-Dienst: `CreatePDF` Vorgang kann eine PDF-Datei nicht in das PDF OCR-Format konvertieren (NPR-32994).
* PDFG Service: PDF conversion fails for the 200th instance of an [!DNL OpenOffice] document (NPR-32766).
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33169) abläuft.
* Designer: Screen readers execute the tabbing order based on the default geographic order instead of the custom tabbing order defined in the XDP file (NPR-32160).
* Designer: If the tagging option is enabled, the subform border disappears in the generated PDF output (NPR-32778).

## Install 6.5.5.0 {#install}

**Einrichtungsvoraussetzungen**

* AEM 6.5.5.0 requires AEM 6.5. Check [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* Der Download des Service Packs ist in Adobe Package Share verfügbar, auf das Sie direkt über die AEM 6.5-Instanz zugreifen können.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.5.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Before installing, take a snapshot or a fresh backup of your AEM instance.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Dennoch wird dies empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.5.5.0-Paket zu entfernen oder zu deinstallieren.

### Installieren des Service Packs {#install-service-pack}

Führen Sie folgende Schritte aus, um das Service Pack in einer vorhandenen AEM 6.5-Instanz zu installieren:

1. Click the [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/AEM-6.5.5.0-Service-Pack) or [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) link to download the package.

1. Öffnen Sie [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und klicken Sie auf Paket **hochladen** , um das Paket hochzuladen.

1. Select the package name and click **Install**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.5.5.0 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

**Automatische Installation**

Es gibt zwei Möglichkeiten, AEM 6.5.5.0 automatisch in einer laufenden Instanz zu installieren:

A. Place the package into `../crx-quickstart/install ` folder while the server is available online. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - make sure that you use `cmd=install&recursive=true` - so the nested packages  are  installed.

>[!NOTE]
>
>AEM 6.5.5.0 unterstützt keine Bootstrap-Installation.

**Bestätigen der Installation**

1. Auf der Seite &quot;Produktinformationen&quot;(/system/console/productinfo) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager, Version 6.5.5.0` unter &quot;Installierte Produkte&quot;angezeigt.

1. All  OSGi  bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: /system/console/bundles).
1. The OSGI bundle `org.apache.jackrabbit.oak-core` is on version 1.10.6 or higher (Use Web Console: `/system/console/bundles`).

In order to see what platforms are certified to run with this release, please refer to the [Technical Requirements](/help/sites-deploying/technical-requirements.md).

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

1. Stellen Sie sicher, dass Sie das AEM Service Pack installiert haben.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

### Install AEM Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Korrekturen in AEM Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

For information about installing the cumulative installer for AEM Forms on JEE and post-deployment configuration, see the [release notes for patch 0014](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-5/jee-patch-0014.html).

### UberJar {#uber-jar}

The UberJar for AEM 6.5.5.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.5/).

To use UberJar in a Maven project, refer to the article, [How to use UberJar](/help/sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

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
| Integrationen | The **[!UICONTROL AEM Cloud Services Opt-In]** screen has been deprecated. Die AEM- und Zielgruppe-Integration wurde in AEM 6.5 aktualisiert, um die Zielgruppe Standard-API zu unterstützen, die die Authentifizierung über Adobe IMS und I/O verwendet, und die wachsende Rolle von Adobe Launch bei der Instrumentierung von AEM-Seiten für Analyse und Personalisierung hat dazu beigetragen, dass der Assistent für die Teilnahme an einer Teilnahme an der App funktional irrelevant geworden ist. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und Adobe I/O-Integrationen über entsprechende AEM-Cloud-Services |

## Bekannte Probleme {#known-issues}

* If you are installing [!DNL Experience Manager] 6.5.5.0 with [!DNL Java] 11, restart the server after installing the Service Pack. Wenn Sie das Service Pack mit [!DNL Java] 8 installieren, ist kein Neustart erforderlich.

* Wenn ein Ordner in der Hierarchie umbenannt wird [!DNL Experience Manager Assets] und der verschachtelte Ordner, der ein Asset enthält, in veröffentlicht wird, wird [!DNL Brand Portal]der Titel des Ordners erst dann aktualisiert, [!DNL Brand Portal] wenn der Stammordner erneut veröffentlicht wird.

* Die Aktualisierung von [!DNL chrome] Version 83 verursacht ein Problem beim Erstellen von Paketen. Verwenden Sie andere verfügbare Browser, z. B. [!DNL Internet Explorer] und [!DNL Firefox]andere Installationsoptionen für AEM-Standardpakete, um das Problem zu beheben.

* Es kann keine E-Mail mit dem AEM-Standard-E-Mail-Sender an den Remote-SMTP-Server gesendet werden, da nur die Kommunikation mit TLS v1.2 möglich ist. Entfernen Sie das Bundle `javax.mail:mail:1.5.0-b01` aus `system/console` und aktualisieren Sie die Bundles, um das Problem zu beheben.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Wenn der Konfigurationsassistent für [!UICONTROL verbundene Assets nach der Installation die Fehlermeldung 404 zurückgibt, müssen Sie die Pakete] und `cq-remotedam-client-ui-content` `cq-remotedam-client-ui-components` Pakete manuell mit dem Package Manager neu installieren.

* Die folgenden Fehler- und Warnmeldungen können während der Installation von AEM 6.5.x.x angezeigt werden:
   * „Wenn die Target-Integration mit der Target Standard-API (IMS-Authentifizierung) in AEM konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregat-Funktionen wie SUM, MAX und MIN verwendet werden. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.

## OSGi bundles and content packages included {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Inhaltspakete in AEM 6.5.5.0:

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
>* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
>* [Dokumentation zu AEM 6.5](https://helpx.adobe.com/de/support/experience-manager/6-5.html)
>* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

