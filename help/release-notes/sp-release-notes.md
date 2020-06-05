---
title: Versionshinweise zum AEM 6.5 Service Pack
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Service Pack 5.
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 46f28926af6cbf3999a4c81cb1f1297b09c07f9f
workflow-type: tm+mt
source-wordcount: '4486'
ht-degree: 12%

---


# Versionshinweise zu Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager 6.5** |
|---|---|
| Version | 6.5.5.0 |
| Typ | Service Pack-Version |
| Datum       | 04. Juni 2020 |
| Download-URL | [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/AEM-6.5.5.0-Service-Pack), [Softwareverteilung ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) |

## Inhalt von Adobe Experience Manager 6.5.5.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.5.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Verbesserungen sowie Leistung, Stabilität und Sicherheitsverbesserungen umfasst. Dieses Update wurde seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht. Es kann über Adobe Experience Manager (AEM) 6.5 installiert werden.

Zu den wichtigsten Funktionen und Verbesserungen, die in AEM 6.5.5.0 eingeführt wurden, zählen:

* Anpassen der Spaltennamen, die in AEM Inbox angezeigt werden.

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

* Die Sortierfunktion sortierbarer Kopfzeilen (in Ansicht der Liste, Ansicht der [!UICONTROL Zeitschiene] und Seite Veröffentlichung [!UICONTROL verwalten] ) wird jetzt von Bildschirmlesehilfen angekündigt und die Sortiersteuerung auf Spaltenköpfen kann über die Tastatur aufgerufen werden (NPR-32979).

* Die anklickbaren Elemente (z. B. Kommentarkarten, Versionsupdates, Kombinationsfelder und Chevron-Symbole von Menüs) können jetzt über die Tastatur fokussiert und bearbeitet werden (NPR-33514).

* Funktionen (oder Aktionszweck) von Insight-Symbolen (für die Verwendung, Impressionen und Klicks) in der [!UICONTROL Insight-Ansicht] werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33513).

* Schreibgeschützte Formularfelder (z. B. deaktivierte Felder auf der Registerkarte [!UICONTROL &quot;] Einfach&quot;von Asset- [!UICONTROL Eigenschaften]) können jetzt über die Tastatur fokussiert werden (NPR-33493, CQ-4273031).

* Bezeichnungen in verschiedenen Eingabefeldern sind nun dauerhafte Bezeichnungen (also barrierefrei) und nicht nur Platzhalterbeschriftungen, die bei der Texteingabe verschwanden (NPR-33475).

* Verschiedene Überschriftenebenen (z. B. Seitentitel und Abschnittsüberschriften) werden nun als Überschriften mit unterschiedlichen Ebenen als Bildschirmlesehilfen-Benutzer wahrgenommen (NPR-33471).

* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen (auf der Seite mit Kopf- und Zoomoptionen für Assets, Ordnernavigation), können jetzt über eine Tastatur aufgerufen werden (NPR-33468, CQ-4271412).

* Die [!UICONTROL Optionen]-, [!UICONTROL Scope]- und [!UICONTROL Workflows] -Fortschrittsindikatoren auf der Seite &quot;Veröffentlichung  verwalten&quot;werden jetzt von Bildschirmlesehilfen als Fortschrittsindikatoren anstelle von Registerkarten korrekt gelesen (NPR-33416).

* Die Farbe der Bewertungssymbole für Sterne (z. B. im [!UICONTROL Rating] -Bereich der Registerkarte &quot; [!UICONTROL Erweitert] &quot;in den Asset- [!UICONTROL Eigenschaften] oder in der Karten-Ansicht) wird geändert, damit der entsprechende Kontrast für Benutzer mit eingeschränkter Sichtbarkeit und ohne Farbwahrnehmung sichtbar ist (NPR-33414).

* Nach oben zeigender Pfeil neben dem Feld [!UICONTROL Kommentar] auf der Seite mit den Asset-Details können Sie jetzt mit den Tastaturbefehlen (NPR-33397) aufrufen.

* Die erweiterten und reduzierten Zustände des Dialogfelds [!UICONTROL Tags] über Asset- [!UICONTROL Eigenschaften] und linke Schienennavigation (in der Assets-Benutzeroberfläche) werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33396).

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

* Beim Verschieben von Assets aus einem Ordner in einen anderen im [!DNL Adobe Experience Manager] Modus &quot;Dynamic Media Scene7&quot;wird der Asset-Name in Kleinbuchstaben geändert (NPR-32995).

* Ein durchsuchtes Asset kann nicht gelöscht werden, nachdem es aus den Suchergebnissen zu seinen Eigenschaften navigiert und dann zu den Suchergebnissen zurückgekehrt ist, um es zu löschen (NPR-32998).

* [!UICONTROL Die nächste] Option bleibt bei der Auswahl des Zielordners in der Benutzeroberfläche &quot;Assets [!UICONTROL verschieben] &quot;deaktiviert (NPR-33356).

* [!UICONTROL Die nächste] Option ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33275).

* Berechtigungen zum Ein- und Auschecken sind für Benutzer mit Berechtigung zum Löschen auf Adobe Asset Link (AAL) deaktiviert, auch wenn ihnen andere Berechtigungen wie Lesen, Erstellen oder Ändern zugewiesen werden dürfen (NPR-33272).

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
* Durch das Hinzufügen eines Erlebnisfragmentordners zu einem vorhandenen Übersetzungsprojekt wird ein neues Projekt erstellt (NPR-32843).
* In den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32628) wird ein `NullPointerException` Fehler angezeigt.

### WCM {#wcm-6550}

* Seiten-Editor - Der [!DNL Sites] Seiten-Editor erlaubt es Benutzern, die nur über die Tastatur verfügen, nicht, zum Hauptinhalt zu springen, anstatt den Tabulatorfokus durch alle verfügbaren Optionen in der Kopfzeile zu verschieben (CQ-4293883).
* Seiten-Editor - Bedienfelder, die Gut-Komponente verwenden und gespeicherte Daten enthalten, werden aufgrund von Aktualisierungen in [!DNL Chrome] und [!DNL Firefox] Versionen nicht angezeigt (CQ-4292995).
* MSM - Das Löschen einer Komponente von der Seite löscht die Komponente nicht aus der veröffentlichten Version der Seite (CQ-4292360).

### Brand Portal {#assets-brand-portal-6550}

* Wenn Sie ein veröffentlichtes Metadaten-Schema aus [!DNL Brand Portal] den Ergebnissen entfernen, wird ein Fehler ausgegeben (CQ-4292063).
* Wenn ein Administrator [!DNL Experience Manager Assets] 6.5.4 über die Adobe Developer Console mit dem Markenportal konfiguriert, kann der [!DNL Brand Portal] Benutzer das Asset des Beitragsordners nicht von [!DNL Brand Portal] bis veröffentlichen [!DNL Experience Manager]. (NPR-33046).
* Duplikat-Replikation der übergeordneten Ordner, die Konflikte verursachen (NPR-33001).

### Communities {#communities-6550}

* Karten können nicht in der Moderationskonsole mit der Schnellbearbeitungs-Menüoption (NPR-33117) gelöscht werden.
* Beim Zugriff auf die [!UICONTROL Aktivität Stream] -Seite (NPR-33146) tritt ein Fehler auf.
* In der Autoreninstanz gelöschte Gruppen werden nicht aus allen Veröffentlichungsinstanzen entfernt (NPR-33199).
* Autoren werden nach der Erstellung einer neuen Gruppe nicht in den Abschnitt [!UICONTROL Community Group] unter [!DNL Internet Explorer] 11 (NPR-33205) umgeleitet.
* Der Zugriff auf eine Nachricht in AEM Inbox ändert den Status der Nachricht in Lesen (NPR-32764) nicht.
* Durch Bearbeiten einer [!DNL Communities] Gruppe und Ändern der Miniaturansicht wird das Gruppenminiaturbild nicht aktualisiert (NPR-32599).
* Ein Benutzer kann keine E-Mail an einen anderen Benutzer in einer Community senden (NPR-32598).
* Ein gesendeter Blog wird erst angezeigt, wenn der Benutzer die Seite aktualisiert (NPR-32391).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von User Generated Content (UGC) wird eine falsche ID der Quellseite gespeichert (CQ-4279355, CQ-4289703).

### Workflow {#workflow-6550}

* Die [!UICONTROL Option &quot;Zeitschiene] &quot;in der linken Leiste dauert länger als erwartet (NPR-32851).
* Nach dem Neustart einer AEM-Instanz enthält die E-Mail für die Review-Aufgabe für eine Sammlung einen falschen Payload-Link (NPR-32774).

### Forms {#forms-6550}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

* Correspondence Management: Die Reihenfolge der Vermögenswerte in einem Zielgruppen-Bereich wird nach der Einreichung eines Schreibens (NPR-33359, NPR-33153) geändert.
* Adaptive Formulare: Wenn ein Benutzer ein adaptives Formular bearbeitet, funktioniert die Option [!UICONTROL Beginn-Workflow] im Menü &quot; [!UICONTROL Seiteninformationen] &quot;nicht (NPR-33004).
* Adaptive Formulare: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-32997).
* Adaptive Formulare: Das Ändern des Bedienfeldlayouts in einem adaptiven Formular führt zu einem Fehler (CQ-4293880).
* Adaptive Formulare: Eine neue Zeile zu einer Zeichenfolge in einem Wörterbuch für adaptive Formulare fügt dem Wörterbuch Zeichen hinzu (NPR-33266). `&#xa;`
* Barrierefreiheit adaptiver Formulare: Wenn ein Benutzer ein adaptives Formular als HTML-Formular Vorschau, kann das [!UICONTROL Scribble-Signatur] -Feld den Tabstopp nicht beibehalten (NPR-33159).
* Barrierefreiheit adaptiver Formulare: Die Fehlermeldungen, die beim Senden eines adaptiven Formulars angezeigt werden, sind nicht mit einem `aria-describedBy` Attribut verknüpft (NPR-33071).
* Barrierefreiheit adaptiver Formulare: Felder, die in einem adaptiven Formular als Pflichtfelder markiert sind, haben im ARIA-Schema (NPR-33070) nicht das obligatorische Attribut &quot;True&quot;.
* PDFG-Dienst: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33238).
* PDFG-Dienst: `CreatePDF` Vorgang kann eine PDF-Datei nicht in das PDF OCR-Format konvertieren (NPR-32994).
* PDFG-Dienst: Die PDF-Konvertierung schlägt bei der 200. Instanz eines [!DNL OpenOffice] Dokuments fehl (NPR-32766).
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33169) abläuft.
* Designer: Bildschirmlesehilfen führen die Tab-Reihenfolge basierend auf der geografischen Standardreihenfolge statt der benutzerdefinierten Tab-Reihenfolge aus, die in der XDP-Datei (NPR-32160) definiert ist.
* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32778) ausgeblendet.

## Install 6.5.5.0 {#install}

**Einrichtungsvoraussetzungen**

* AEM 6.5.5.0 requires AEM 6.5. Check [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* Der Download des Service Packs ist in Adobe Package Share verfügbar, auf das Sie direkt über die AEM 6.5-Instanz zugreifen können.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.5.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer AEM-Instanz.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Dennoch wird dies empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.5.5.0-Paket zu entfernen oder zu deinstallieren.

### Installieren des Service Packs {#install-service-pack}

Führen Sie folgende Schritte aus, um das Service Pack in einer vorhandenen AEM 6.5-Instanz zu installieren:

1. Klicken Sie auf den Link [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/AEM-6.5.5.0-Service-Pack) oder [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) , um das Paket herunterzuladen.

1. Öffnen Sie [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und klicken Sie auf Paket **hochladen** , um das Paket hochzuladen.

1. Wählen Sie den Paketnamen und klicken Sie auf **Installieren**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.5.5.0 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

**Automatische Installation**

Es gibt zwei Möglichkeiten, AEM 6.5.5.0 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in einen `../crx-quickstart/install ` Ordner, während der Server online verfügbar ist. Das Paket wird automatisch installiert.

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

* Wenn Sie [!DNL Experience Manager] 6.5.5.0 mit [!DNL Java] 11 installieren, starten Sie den Server nach der Installation des Service Packs neu. Wenn Sie das Service Pack mit [!DNL Java] 8 installieren, ist kein Neustart erforderlich.

* Wenn ein Ordner in der Hierarchie umbenannt wird [!DNL Experience Manager Assets] und der verschachtelte Ordner, der ein Asset enthält, in veröffentlicht wird, wird [!DNL Brand Portal]der Titel des Ordners erst dann aktualisiert, [!DNL Brand Portal] wenn der Stammordner erneut veröffentlicht wird.

* Bei der Installation von AEM 6.5.5.0 verursacht die Aktualisierung von [!DNL Chrome] Version 83 ein Problem beim Erstellen von Paketen. Verwenden Sie andere verfügbare Browser, z. B. [!DNL Internet Explorer] und [!DNL Firefox]andere Installationsoptionen für AEM-Standardpakete, um das Problem zu beheben. Das Problem wird nach der Installation von AEM 6.5.5.0 behoben.

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
* [Wenden Sie sich an den Support](https://docs.adobe.com/content/help/en/customer-one/using/home.html). Weitere Informationen zum Zugriff auf das Support-Portal finden Sie unter [Zugriff auf das Support-Portal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORELIKETHIS]
>
>* [Versionshinweise zu AEM 6.5](/help/release-notes/release-notes.md)
>* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
>* [Dokumentation zu AEM 6.5](https://helpx.adobe.com/de/support/experience-manager/6-5.html)
>* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

