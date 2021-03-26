---
title: '[!DNL Adobe Experience Manager] 6.5 Versionshinweise zu früheren Service Packs'
description: Versionshinweise für Service Packs  [!DNL Adobe Experience Manager] 6.5.
contentOwner: AK
translation-type: tm+mt
source-git-commit: ecb32596edecaf47ef54a74c2be8ecf252de466c
workflow-type: tm+mt
source-wordcount: '17912'
ht-degree: 17%

---


# Hotfixes und Feature Packs in den vorherigen Service Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## [!DNL Adobe Experience Manager] 6.5.7.0  {#experience-manager-6570}

[!DNL Adobe Experience Manager] 6.5.7.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Verbesserungen sowie Verbesserungen in den Bereichen Leistung, Stabilität und Sicherheit umfasst. Diese Verbesserungen wurden seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht. Das Service Pack wird auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Erweiterungen von [!DNL Adobe Experience Manager] 6.5.7.0 umfassen:

* Durchführen von Seitenverschiebungen und MSM-Rollouts als asynchrone Vorgänge, um deren Auswirkungen auf die Laufzeitleistung zu reduzieren.

* Die Benutzer können digitale Assets in den Ansichten &quot;Karte&quot;und &quot;Spalte&quot;sortieren.

* [!DNL Assets] und  [!DNL Dynamic Media] bieten mehrere Verbesserungen an der Barrierefreiheit. Die Verbesserungen betreffen die Tastaturnavigation, die Verwendung von Bildschirmlesehilfen und die Verwendung ähnlicher Hilfstechnologien (AT). Siehe [[!DNL Assets] Erweiterungen](#assets-6570) und [[!DNL Dynamic Media] Erweiterungen](#dynamic-media-6570).

* [HTTP-Client-](../../help/forms/using/configure-data-sources.md#fdm-http-client-configuration) Konfiguration des Formulardatenmodells zur Leistungsoptimierung.

* [Verfügbarkeit der Option &quot;Zurücksetzen&quot;für jede ](../../help/forms/using/resize-using-layout-mode.md#resize-components) Komponente im Layoutmodus

* [!DNL Experience Manager] 6.5 Service Pack 7 Forms verbessert die Leistung für:

   * Validieren der Feldwerte auf dem Server, wenn Sie ein adaptives Formular senden.

   * Konvertieren eines PDF-Formulars in ein adaptives Formular mit dem [!DNL Automated Forms Conversion service].

* Unterstützung für [!DNL Microsoft SQL Server] 2019 in [!DNL Experience Manager Forms].

* Unterstützung für SQL Server 2016 &quot;Stets On availability&quot;-Gruppen für hohe Verfügbarkeit von OSGi-Bereitstellungen.[!DNL Microsoft]

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.5 aktualisiert.

Eine vollständige Liste der in [!DNL Experience Manager] 6.5.7.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 7](new-features-latest-service-pack.md).

Im Folgenden finden Sie die Liste der Fehlerbehebungen in der Version 6.5.7.0.[!DNL Experience Manager]

### [!DNL Sites] {#sites-6570}

* Wenn Sie die Option [!UICONTROL Zeitumbruch] für eine Seite öffnen, die Seitenleiste der Zeitleiste öffnen und zur Konsole [!UICONTROL Sites] navigieren, tritt der `Failed to Load`-Fehler auf (NPR-34951).

* Die Option [!UICONTROL Zeitumbruch] zeigt keine Bilder für den ausgewählten Datums- und Zeitbereich an (NPR-34951).

* Wenn ein Filter `getHeader()` von einer Seite mit einem Inhaltsfragment aufruft, tritt der `java.lang.AbstractMethodError`-Fehler auf (NPR-34942).

* Wenn der Pfad einer Seite mehrere Inhaltszeichenfolgen enthält, können Vorschauen nicht gerendert werden, und die Versionsvergleichsfunktion schlägt ebenfalls fehl (NPR-34740).

* Wenn Sie einen numerischen Wert für die label-Eigenschaft `String` einer Komponente festlegen, können Sie die Komponente löschen und den Löschvorgang rückgängig machen. Nachdem Sie den Löschvorgang rückgängig gemacht haben, ändert sich die Eigenschaft label von `String` in `Long` (NPR-34739).

* Beim Hinzufügen eines Erlebnisfragments basierend auf einer Vorlage mit einem gesperrten Layout zu einer Seite (NPR-34632) tritt die folgende Ausnahme auf:

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.mozilla.javascript.EcmaError: TypeError: Cannot call method "getChildren" of null
   ```

* Wenn Sie einen Ordner verschieben, treten Querschnittsprobleme auf, und der folgende Fehler tritt auf (NPR-34554):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript. org.apache.jackrabbit.oak.query.RuntimeNodeTraversalException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped
   ```

* Wenn neue Assets erstellt, veröffentlicht und an einen neuen Speicherort verschoben werden, wird der `Request to complete move operation`-Workflow erstellt und führt zu einem Aborted-Status. Das Hochladen eines neuen Assets und Ausführen eines Vorgangs `move` führt zur Erstellung des `Request to complete move operation`-Workflows im ausstehenden Status (NPR-34543).

* Wenn Sie ein Erlebnisfragment aus der Umgebung [!DNL Experience Manager] 6.5.2 in [!DNL Target] Standard exportieren, schlägt der API-Aufruf fehl, da die Workspace-Eigenschaft für [!DNL Target] Standard (NPR-34557) nicht verfügbar ist.

* Benutzer können keine Seiten über die Option [!UICONTROL Veröffentlichung verwalten] veröffentlichen, da die Option [!UICONTROL Veröffentlichen] verschwindet (NPR-34542).

* Wenn Sie dem Text einige Stile hinzufügen, wird dem Text ein `<div>`-Tag hinzugefügt, und der Stil kann nicht mehr auf den Text angewendet werden (NPR-34531).

* Wenn Sie ein Element in einem Popupmenü auswählen und die erforderlichen Dateien aktualisieren, ist es nicht möglich, Dialogfeldwerte zu speichern, da das andere Menü ein leeres erforderliches Feld enthält (NPR-34529).

* Wenn Sie eine Seite aus einer benutzerdefinierten Vorlage erstellen und sie in die Blueprint-Hierarchie verschieben, werden die Beginn der Seite, die sich auf der Seite befinden, früher aus der Live-Kopierhierarchie gelöscht (NPR-34527).

* Wenn ein Artikelstil auf einen Inhalt angewendet wurde, kann er nicht entfernt werden (NPR-34486).

* Alle Live-Kopien und Kopien eines Erlebnisfragments verweisen auf dieselbe [!DNL Adobe Target] Angebot-ID (NPR-34469).

* Elemente mit Aufzählungszeichen werden zusätzlich zur nummerierten Liste (NPR-34455) angezeigt.

* Die Option &quot;Mit Quelle vergleichen&quot;zeigt nicht den Unterschied zwischen der Quellseite und der bearbeiteten Version einer Seite (NPR-34285).

* Wenn Sie eine Seite löschen, sind die Versionsdetails nicht konfigurierbar (NPR-34159).

* Wenn ein Benutzer die Dialogoption [!UICONTROL Auswahl öffnen] auswählt, wird der Tastaturfokus auf das ausgeblendete Steuerelement auf der Seite verschoben (CQ-4307779, CQ-4293601).

* Wenn Sie einen veröffentlichten Ordner im Autor verschieben, werden die Ordnerpfade in der Veröffentlichungsinstanz nicht entsprechend aktualisiert (CQ-4305144).

* Wenn ein Benutzer die `Enter`-Taste bei der Option [!UICONTROL Alle auswählen] auswählt, wird der Tastaturfokus nicht zur Option [!UICONTROL Steuerelement erstellen] verschoben (CQ-4293599).

* Wenn Sie den Schlüssel `Esc` auswählen, wird der Fokus nicht auf das übergeordnete Steuerelement wiederhergestellt (CQ-4293593, CQ-4293590).

* Verbesserte WCAG-Kompatibilität für [!DNL Sites] UI- und Core-Komponenten (CQ-4293448).

* [!UICONTROL Die ] Zoom- und   Skalierungsfunktionen sind für die  [!DNL Sites Editor] Seite deaktiviert (CQ-4282353).

* Wenn Sie die Option &quot;Nach rechts drehen&quot;verwenden, beendet die Bildschirmlesehilfe die Narratisierung des aktuellen Drehungs- oder Drehstatus (CQ-4282128).

* Die Schaltflächen zum Konfigurieren des Dialogfelds &quot;Fertig&quot;und &quot;Abbrechen&quot;verfügen über mehr als einen Tabstopp (CQ-4274601).

* Das Verschieben von Seiten mit einem ähnlichen Namen auf derselben Ebene ist nicht zulässig (NPR-35041).

* Nach Auswahl der Option Löschen (x) wird der Tastaturfokus nicht in das Feld [!UICONTROL Filter] verschoben (CQ-4293581).

* Wenn Sie auf [!DNL Experience Manager] 6.5.6.0 aktualisieren, ändert sich das Verhalten des geerbten Absatzsystems und funktioniert nicht ordnungsgemäß (NPR-35117).

* Tastaturbenutzer können den Tabulatorfokus nicht in der richtigen Reihenfolge verschieben, nachdem sie den Abschnitt [!UICONTROL Aktion] auf einer [!DNL AEM Sites]-Seite (CQ-4307786) ausgewählt haben.

* Nachdem Sie beim Bearbeiten eines Inhaltsfragments in der Liste &quot;Zielgruppe&quot;der RTE-Symbolleiste eine Option ausgewählt haben, wird das Dialogfeld &quot;Autor des Inhaltsfragments&quot;flackern (CQ-4305532).

* Tastaturbenutzer können die Optionen in der Dropdown-Liste [!UICONTROL Hinzufügen Komponente] nicht mit der Nach-unten-Taste (CQ-4295097) auswählen.

* Der Tabulatorfokus ändert sich nicht in der richtigen Reihenfolge, wenn ein Datum im Menü Kalender auf der Registerkarte [!UICONTROL Assets] einer [!DNL Sites]-Seite (CQ-4293600) ausgewählt wird.

* Der Tabulatorfokus wechselt nicht zu den nächsten oder vorherigen Optionen für Tastaturbenutzer, nachdem die beim Bearbeiten einer Siteseite verfügbaren Link- oder Textoptionen gelöscht wurden (CQ-4293597).

* Benutzer der Tastatur können den Fokus der Registerkarte nicht wieder auf Mehr Optionen im Abschnitt [!UICONTROL Aktionen] verschieben, nachdem sie die verfügbaren Optionen angezeigt und die `Esc`-Taste gedrückt haben (CQ-4293592).

* Wenn Sie die Option [!UICONTROL Drehen] für ein Bild im Modus [!UICONTROL Bearbeiten] aktivieren, wechselt der Registerfokus, anstatt auf &quot;Drehen&quot;zu bleiben, zur Option [!UICONTROL Wiederholen] für die Tastaturbenutzer (CQ-4293587).

* Im Dialogfeld [!UICONTROL Auswahl öffnen], das auf der Registerkarte [!UICONTROL Link und Aktionen] verfügbar ist, wechselt der Registerfokus nach der Option [!UICONTROL Abbrechen] zu ausgeblendeten Elementen auf der Seite (CQ-4293579).

* Wenn Tastaturbenutzer ein Bild bearbeiten, zur Option [!UICONTROL Fertig stellen] navigieren und die Eingabetaste drücken, wird die Fertigstellung nicht angekündigt (CQ-4282351).

* Die im Dialogfeld [!UICONTROL Link und Aktionen] verfügbaren Optionen &quot;Nach oben&quot;und &quot;Nach unten&quot;stehen den Bildschirmlesehilfen- und Tastaturbenutzern nicht zur Verfügung (CQ-4281120).

* Tastaturbenutzer können den Registerfokus nicht wiederherstellen, nachdem sie auf der [!UICONTROL Eigenschaften]-Seite (CQ-4293581, NPR-34653) zur Option Schließen (X) navigiert haben.

### [!DNL Assets] {#assets-6570}

[!DNL Adobe Experience Manager] 6.5.7.0  [!DNL Assets] behebt die folgenden Probleme und bietet die folgenden Erweiterungen.

* Die folgenden Erweiterungen werden für Barrierefreiheit in [!DNL Experience Manager Assets] in dieser Version vorgenommen. Weitere Informationen finden Sie unter [Funktionen für die Barrierefreiheit in [!DNL Assets]](/help/assets/accessibility.md).

   * Beim Navigieren in der Zeitleiste mit einer Tastatur kann die `Esc`-Taste die Option [!UICONTROL Alle anzeigen] ausblenden, ohne den Fokus zu verlieren (CQ-4293598).
   * Beim Navigieren mit der Tastatur-Tabulatortaste behält das Tag-Feld den Fokus (NPR-35109) bei, nachdem das letzte Tag aus den hinzugefügten Tags entfernt wurde.
   * [!DNL Experience Manager] Komponenten enthalten nun entsprechende Informationen für Namen, Rolle und Wert, die von Bildschirmlesehilfen verwendet werden sollen (NPR-34255).
   * Nachdem Sie das Kombinationsfeld &quot;Typ/Größe&quot;, das Kombinationsfeld &quot;Verknüpfen&quot;, das Sprachkombinationsfeld oder das Textfeld zum Bearbeiten gelöscht haben, kehrt der Tastaturfokus zu den nächsten oder vorherigen Elementen der Benutzeroberfläche oder zu einem relevanteren Element der Benutzeroberfläche zurück (CQ-4293585).
   * Wenn Sie den Mauszeiger über Optionen bewegen, werden Tipps wie „Auswählen“ und „Herunterladen“ angezeigt. Benutzer, die eine Bildschirmlupe verwenden, können die Miniaturansichten der Dateien wegen dieser Tipps möglicherweise nicht sehen. Es ist jetzt möglich, den Fokus beizubehalten, nachdem die Option mit der `Escape`-Taste entfernt wurde. (CQ-4293554).
   * Wenn Sie eine Rasterzelle aus dem Raster auf der Seite auswählen, wird der Fokus auf die Aktionsleiste verschoben, die auf dem Bildschirm angezeigt wird (CQ-4282127).
   * Visuelle Benutzer können zwischen normalem Text und einem Link unterscheiden, da visuelle Hinweise (Unterstreichung und Chevron-Symbol) für Links zu allen Lösungen in der [!DNL Experience Manager]-Startseite (CQ-4282072) angezeigt werden.

* Die folgende Benutzererfahrungsverbesserung erfolgt in [!DNL Assets]:

   * Sortieren von Assets in der Karten- und Spalten-Ansicht (NPR-35097) aktivieren.

* Wenn nach der Aktualisierung auf 6.5 eine JSON-Datei mit der Assets HTTP API generiert wird, treten Probleme mit der in der Datei verwendeten Kodierung auf (NPR-35129).

* Benutzer einer Gruppe, denen keine Berechtigung zum Erstellen von Sammlungen erteilt wurde (Option &quot;Sammlung erstellen&quot;ist nicht verfügbar) können weiterhin Sammlungen erstellen, indem sie direkt auf die URL `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/collections/createcollectionwizard.html/content/dam/collections?contentPath=/content/dam/collections` (NPR-35115) zugreifen.

* Wenn die gesuchten Assets nach Namen sortiert werden, wird zwischen Groß- und Kleinschreibung unterschieden. Dadurch werden zwei separate sortierte Listen erstellt, die auf dem Gehäuse basieren, das in den Suchergebnissen geordnet angezeigt wird (NPR-35068).

* Wenn ein Inhaltsfragment im Editor geöffnet wird, werden Warnmeldungen (`Invalid value specified for a metadata property`) in den Fehlerprotokollen (NPR-35012) protokolliert.

* Benutzer ohne Administratorberechtigung können abgelaufene Assets mit der Desktop-App [Experience Manager] bearbeiten. (NPR-34993).

* Wenn dasselbe Asset in die Benutzeroberfläche &quot;Assets&quot;gezogen und eine neue Version erstellt wird, sind die Änderungen in den Metadaten nicht beständig (NPR-34940).

* Beim Bearbeiten von Sammlungen kann ein Benutzer den Titel der Sammlung löschen und die Änderungen erfolgreich speichern (NPR-34889).

* Beim Hochladen eines Duplikat-Bildes wird eine Löschoption angezeigt. Wenn Sie &quot;Löschen&quot;wählen, können die Bilder hochgeladen werden. DAM Update Asset Workflow wird ebenfalls ausgelöst (NPR-34744).

* Bei Verwendung von [!DNL Adobe Asset Link] mit [!DNL Adobe InDesign] enthalten die Suchergebnisse keine Ordner und Sammlungen, sondern nur Assets (NPR-34699, CQ-4303666).

* Wenn Sie den Mauszeiger über die Ansicht der Karte bewegen, wird der Bildlauf durch (automatische) Fokussierung auf die Schnellaktionen durchgeführt, die auf der Karte verfügbar sind (NPR-34514).

* Wenn Sie die Eigenschaften mehrerer Assets stapelweise bearbeiten, wird durch Auswahl der Option [!UICONTROL Speichern] die Ansicht des Masseneditors geschlossen und zur Hauptseite [!DNL Assets] umgeleitet. Dieses Verhalten ist mit dem Verhalten der Option [!UICONTROL Speichern &amp; Schließen] identisch und wird nicht erwartet (NPR-34546).

* Die intelligente Sammlung zeigt nach dem Speichern nicht die richtige Benutzeroberflächeneinstellung an. Die Abfrage wird ordnungsgemäß gespeichert, aber die Oberfläche zeigt immer die zuletzt hinzugefügte Option Predicate (NPR-34539) an.

* Beim Hinzufügen von Assets zu [!DNL Experience Manager] werden die Metadaten ohne Namensraum nicht importiert (NPR-34530).

* Wenn Sie ein Asset in einen Ordner ziehen, um es zu verschieben, zeigt die Benutzeroberfläche auch die Option [!UICONTROL In Leuchtkasten ] ablegen und [!UICONTROL In Sammlung ablegen] an. Auch wenn der Verschiebungsvorgang abgebrochen wird, zeigt die Benutzeroberfläche weiterhin die beiden letztgenannten Optionen an (NPR-34526).

* Das Symbol `%>` wird auf der Seite &quot;Sammlungen&quot;angezeigt (NPR-34499).

* In der Ansicht der Spalte [!DNL Assets] werden Duplikat- und Asset-Namen angezeigt, wenn ein Bildlauf nach oben oder nach unten durchgeführt wird, bevor alle Assets angezeigt werden (NPR-34464).

* Wenn Sie unmittelbar nach dem Erstellen eines öffentlichen Ordners einen privaten Ordner erstellen, verwendet der öffentliche Ordner die Einstellungen für den privaten Ordner (NPR-34415).

* In der Ansicht sind die Karten nicht in alphabetischer Reihenfolge aufgeführt und können nicht alphabetisch sortiert werden (NPR-34234).

* Beim erneuten Öffnen von Kaskadenregeln werden die Optionen auf der Benutzeroberfläche nicht beibehalten (CQ-4301452).

#### [!DNL Dynamic Media] {#dynamic-media-6570}

* Die folgenden Erweiterungen wurden für Barrierefreiheit in [!DNL Dynamic Media] (CQ-4290306) vorgenommen. Weitere Informationen finden Sie unter [Barrierefreiheitsfunktionen in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).

   * Bildschirmlesehilfen (JAWS, Erzähler) beschreiben den Namen, die Rolle und den Status der Menüelemente in der Menüoption &quot;Größe einbetten&quot;(CQ-4290927).
   * Benutzer können mit der `Tab`-Taste (CQ-4290926) im Dialogfeld &quot;E-Mail-Link&quot;navigieren.
   * Der Arbeitsablauf zum Erstellen von Videokodierungs-Profilen ist benutzerfreundlicher, da die Bildschirmlesehilfe verbessert wurde (CQ-4290623, CQ-4290622).
   * Beim Navigieren mit der Taste `Tab` wird der Fokus auf die entsprechenden Elemente der Benutzeroberfläche im Workflow verschoben, um ein interaktives Video zu erstellen (CQ-4290621, CQ-4290620, CQ-4290619).
   * Die Seiten „Veröffentlichen“, „Asset bearbeiten“, „Smartes Zuschneiden bearbeiten“ und „Bildset-Editor“ wurden verbessert, um den Web-Standards zu entsprechen. Hilfstechnologie (AT)-Benutzer können jetzt einfach durch diese Seiten navigieren und Aktionen wie das Zuschneiden von Bildern ausführen (CQ-4290617, CQ-4290616, CQ-4290613, CQ-4290612, CQ-422 90610, CQ-4290614).
   * Die Viewer wurden verbessert, damit Benutzer mit einer Tastatur navigieren können (CQ-4290615).
   * Die Benutzer der Tastatur und der Bildschirmlesehilfe können die Funktion zum Beschneiden verwenden (CQ-4290609).
   * Die Tastaturbenutzer können die Hotspots besser verwalten (CQ-4290604, CQ-4290603).

* Remote-Bildsätze können in [!DNL Experience Manager] nicht bearbeitet werden, wenn Firma und Ordnername identisch sind (NPR-31340).

* Die z-index-Reihenfolge ist nicht korrekt, wenn Sie versuchen, die Ausgabe nach dem Hinzufügen eines Hotspots zu einem [!DNL Dynamic Media]-Bild oder nach der Bearbeitung eines [!DNL Dynamic Media]-Videos oder eines [!DNL Experience Fragment] mit einem Bild (CQ-4307267) Vorschau.

* [!DNL Dynamic Media] Die Synchronisierung schlägt fehl, wenn gemischte Mediensets erneut verarbeitet werden (CQ-4307184).

* Wenn ein Asset in einen Ordner verschoben wird, in dem die automatische Synchronisierung auf [!DNL Dynamic Media] konfiguriert ist, wird das Asset nicht synchronisiert (CQ-4307122).

* [!DNL Dynamic Media] Videos werden auf iOS-Geräten mit den nativen HTML5-Video-Steuerelementen (CQ-4306977, CQ-4306727) nicht wiedergegeben.

* Bilder, auf die SmartCrop angewendet wird, können nicht heruntergeladen werden (CQ-4304558).

* Es ist nicht möglich, Ordner selektiv auf Dynamic Media zu veröffentlichen (CQ-4304526).

* Rückgängigmachen der Veröffentlichung einer Videodatei von [!DNL Experience Manager] machen Sie die Veröffentlichung des adaptiven Videosets nicht aus einer konfigurierten Scene7-Bereitstellung rückgängig (CQ-4304405).

* Das Hinzufügen eines Panorama-Bild-Assets zu einer Panorama-Medienkomponente und das Aktualisieren der Seite führt zu einem `Uncaught ReferenceError: $ is not defined`-Fehler (CQ-4302810).

* Im [!UICONTROL Viewer-Vorgaben-Editor] ist bei der Bearbeitung der Vorgabe [!UICONTROL PanoramicImage/PanoramicImage_VR] in der Komponente `PanoramicView` die Modifikator-Beschriftung `PANORAMICVIEW_AUTOROTATE` nicht verfügbar (CQ-4302443).

* Videobeschriftungen werden nicht angezeigt, wenn das Video nicht das erste in einem MixedMediaSet (CQ-4298161) ist.

* Der HTML5-E-Katalog-Viewer auf iPhones-Mobilgeräten kann die Seiten nicht drehen oder blättern (CQ-4296611).

* Beim Bildlauf von Farbfeldern auf einem Mobilgerät werden die Farbfelder einige Sekunden lang nach rechts und aus dem Sichtbereich blättert, bevor sie wieder in die Ansicht scrollen (CQ-4296439).

* Wenn ein Viewer-Vorgabe-Übergeordnet-Datensatz erstellt wird, werden das CSS und die Grafik nicht veröffentlicht und nur die Viewer-Vorgabe wird veröffentlicht (CQ-4262205).

* Beim Versuch, ein Erlebnisfragment für einen bestimmten Hotspot in der Komponente [!UICONTROL Interaktives Video/Bilder] zu verknüpfen, wird der ausgewählte Pfad zum Erlebnisfragment nicht angezeigt. Stattdessen wird ein leerer Wert aus dem Pfadfeld zurückgegeben (NPR-35146, CQ-4298136).

* Kann kein Erlebnisfragment im IVV-Editor (CQ-4308560) Vorschau werden.

* Wenn Sie einem Bild einen Hotspot hinzufügen und ein Erlebnisfragment auswählen, ist es nicht möglich, die Unterordner und Varianten des Erlebnisfragments (CQ-4307455) auszuwählen.

* Die Nicht-Bild-Assets werden nach dem Hochladen nicht als veröffentlicht angezeigt (CQ-4306415).

#### [!DNL Experience Manager] 3D-Assets  {#three-d-assets-6570}

* `DAM CQ MIME Type` -Dienst wendet falsche MIME-Typen auf 3D-Assets an, was zu einem fehlerhaften Rendering führt (NPR-34731).

### [!DNL Commerce] {#commerce-6570}

* Die Benutzeroberfläche für die Commerce-Produktsammlung Liste nicht mehr als 15 Produkte innerhalb einer Sammlung (NPR-34502).

### Plattform {#platform-6570}

* Eine HTTP-Sitzung über HTTPS ist nicht ungültig (NPR-35083).
* Ein `NullPointerException` wird zurückgegeben, wenn tägliche oder wöchentliche Aufgaben der Wartung über die Benutzeroberfläche gestartet werden (NPR-34953).
* Der W3C-Validator meldet Warnungen für konforme JavaScript-Clientbibliotheksdateien (NPR-34898).
* Die Funktion `AudienceOmniSearchHandler` verwendet einen veralteten Index (NPR-34870).
* Beim Abmelden von Experience Manager werden die Cookies nicht gelöscht (NPR-34743).
* Die Funktion `findByTitle` der API funktioniert nicht, wenn der Tag-Name ein Sonderzeichen enthält (NPR-34357).`TagManager`
* Der Vorgang zum Importieren des Synchronisierungspakets für Benutzer ist fehlgeschlagen (NPR-34399).
* Unterstützung für `ariaLabel`- und `ariaLabelledby`-Eigenschaften zur `Coral.Masonry`-Komponente (GRANITE-29962) hinzugefügt.
* Der Dispatcher-Cache wird für Seiten mit Inhaltsfragmenten nach der Installation der neuesten Core-Komponenten-Pakete (CQ-4306788) nicht aktualisiert.
* Lokalisierte Tag-Namen mit Anführungszeichen (`"`) werden auf der Benutzeroberfläche nicht richtig angezeigt (CQ-4305439).

### Benutzeroberfläche {#ui-6570}

* Das Feld [!UICONTROL Link zu] in den Komponenteneigenschaften enthält automatisch vervollständigte Vorschläge, die nicht mit der angegebenen Zeichenfolge übereinstimmen (NPR-34865).

* AEM zeigt die folgende Fehlermeldung an, wenn Sie ein tägliches Wartungsfenster planen, das zwischen 2 Tagen verteilt wird (NPR-35280):

   ```TXT
   ERROR The start time must precede (be less than) the end time
   ```

### Integrationen {#integrations-6570}

* Die Bearbeitung einer vorhandenen [!DNL Adobe Launch]-Konfiguration ist fehlgeschlagen (NPR-35045).
* Bei Verwendung der IMS-Konfiguration und der [!DNL Adobe Target Standard]-Umgebung (NPR-34555) kann [!DNL Experience Fragments] nicht nach [!DNL Adobe Target] exportiert werden.
* Die Option [!UICONTROL Erstellen] wird auf der Seite [!UICONTROL Audiencen] angezeigt, wenn Sie von einem Ordner zur Seite [!UICONTROL Audiencen] navigieren (NPR-35151).

### Sling {#sling-6570}

* Bei der Standardüberprüfung des Anmeldestatus werden die Anmeldeinformationen eines Benutzers überprüft, der nicht vorhanden ist (NPR-34686).

### Übersetzungsprojekte {#translation-6570}

* Beim Abbrechen eines Übersetzungsprojekts in [!DNL Experience Manager] wird die Anforderung zum Abbrechen nicht an den Übersetzungsanbieter gesendet (NPR-34433).

### [!DNL Communities] {#communities-6570}

* Alle Fälle ungleicher Terminologie im Produkt werden durch anerkannte Entsprechungen ersetzt (NPR-34311).
* [!DNL Google+] wird aus der Liste der Social Sharing-Optionen entfernt (NPR-33877).

### [!DNL Brand Portal] {#brandportal-6570}

* Die Benutzeroberfläche reagiert nicht, wenn die Assets in der Ansicht [!UICONTROL Liste] (NPR-34728) ausgewählt werden.

### [!DNL Forms] {#forms-6570}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für  [!DNL Forms]. Sie werden mithilfe eines separaten [!DNL Forms] Add-On-Pakets bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-on installieren](#install-aem-forms-add-on-package) und [AEM Forms on JEE installieren](#install-aem-forms-jee-installer).

**Adaptive Formulare**

* Adaptive Formulare können nach Anwendung von [!DNL Experience Manager] Service Pack 6 (NPR-35126) nicht mit der klassischen Benutzeroberfläche bearbeitet werden.

* Wenn Sie eine PDF-Datei in ein adaptives Formular konvertieren, können Sie keinen Wert für ein verschachteltes Bedienfeld mit einem Formulardatenmodell im Layout mit Registerkarten festlegen. Darüber hinaus gibt es Probleme beim dynamischen Festlegen eines Werts für Optionsfeldgruppen mit einem statischen Array mithilfe des Code-Editors (NPR-35062).

* Wenn Sie japanische Zeichen in eine Textfeldkomponente in einem adaptiven Formular eingeben, können Sie mehr Zeichen als die maximal zulässige Länge von 35 Zeichen angeben (NPR-35039).

* Das adaptive Formular zeigt unerwünschte Parameter wie `owner` und `status` auf der **[!UICONTROL Danksagungsseite]** an, die nach dem Senden des Formulars angezeigt wird (NPR-34989).

* Das Dialogfeld [!UICONTROL Dateiauswahl] für die Komponente [!UICONTROL Anlage] zeigt die nicht unterstützten Dateitypen sowie die Auswahl an, die während der Übermittlung des adaptiven Formulars zu einem Fehler führt (NPR-34970).

* Wenn Sie ein adaptives Formular auf einer [!DNL Experience Manager Sites]-Seite einfügen, die Text vor dem Formular enthält, wird der Cursor direkt auf das Formular und nicht auf den Text vor dem Formular verschoben (NPR-34947).

* [!UICONTROL Vorschau mit ] DataOption zum Vorausfüllen eines adaptiven Formulars mit einer XML-Datendatei der Version  [!DNL Experience Manager] 6.2 funktioniert nicht ordnungsgemäß (NPR-35087).

* Wenn Sie das Datenwörterbuch für ein adaptives Formular aktualisieren, wird das Formular nicht übersetzt, da das adaptive Formular zwischengespeicherte Werte zurückgibt (NPR-34845).

* Fragmente benötigen mehr Zeit, um in einem adaptiven Formular geladen zu werden, da der Cache ungültig wird (NPR-34567).

* Die Registerkartennavigation funktioniert nicht ordnungsgemäß für Bildschirmlesehilfen in adaptiven Formularen (NPR-34544).

**Korrespondenzverwaltung**

* Werte für XML-Tags mit numerischen Daten, die den Fließtyp enthalten, können nicht als Entwurf gespeichert werden (NPR-35050).

* Wenn Sie die Assets aus ES3 migrieren, enthalten die Assets zwei nicht bearbeitbare Standardbedingungen (NPR-34972).

* Wenn Sie ein Datenwörterbuch in einem Brief bearbeiten, zeigt der Abschnitt [!UICONTROL Geliehener Inhalt] rotierende Rechtecke anstelle nützlicher Informationen an (NPR-34853).

**Interaktive Kommunikation**

* Der Name der Rollout-Konfiguration für interaktive Kommunikation, der nach der Installation des Add-On-Pakets [!DNL Forms] verfügbar ist, Duplikat den standardmäßigen Namen der Rollout-Konfiguration (NPR-34976).

**Dokumentensicherheit**

* Wenn Sie eine neue Dokument-Sicherheitsrichtlinie speichern, zeigt Experience Manager Forms die Fehlermeldung `Relative validity period is required` (NPR-34679) an.

* Dokument Security kann PDF 2.0-Dokument nicht schützen (CQ-4305851).

Informationen zu Sicherheitsaktualisierungen finden Sie unter [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.6.0  {#experience-manager-6560}

Adobe Experience Manager 6.5.6.0 ist ein wichtiges Update, das neue Funktionen, vom Kunden angeforderte wichtige Verbesserungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen umfasst, die seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht werden. Es kann auf Adobe Experience Manager 6.5 installiert werden.

Die wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5.6.0 eingeführt wurden, umfassen:

* Veröffentlichen oder rückgängig machen Sie die Veröffentlichung von Assets mithilfe des Assistenten [!UICONTROL Schnellveröffentlichung] oder [!UICONTROL Veröffentlichung verwalten] selektiv.[!DNL Experience Manager][!DNL Dynamic Media]

* Verwenden Sie die [!DNL Dynamic Media]-Benutzeroberfläche, um zwischengespeicherte Content Versand Network (CDN) ungültig zu machen.

* Das Veröffentlichen der Asset-Beitragsordner vom Markenportal in Experience Manager Assets wird jetzt auch über den Proxyserver unterstützt.

* Die automatisch generierten Gruppen von privaten Ordnern werden jetzt beim Löschen des privaten Ordners in [!DNL Experience Manager Assets] bereinigt.

* Die Beschreibungen der Modifikatoren im Vorgabeneditor für Video [!UICONTROL Viewer] wurden in [!DNL Dynamic Media] aktualisiert.

* Es wird eine neue Einstellung für die Firma bereitgestellt, die den Status von [!DNL Dynamic Media] Connector widerspiegelt.

* Die Standardoptionen für `test` und `aiprocess` werden auf `Thumbnail` von `Rasterize` zuvor in Dynamic Media aktualisiert, um sicherzustellen, dass Benutzer nur Miniaturansichten erstellen und die Extraktion der Extraktion und des Suchbegriffs überspringen müssen.

* [Ausfüllen eines adaptiven Formulars im Voraus auf dem Client](../../help/forms/using/prepopulate-adaptive-form-fields.md#prefill-at-client).

* [Integration des Formulardatenmodells mit RESTful-APIs auf einem Server mit Zweiweg-SSL-Implementierung](../../help/forms/using/configure-data-sources.md).

* [Verbesserte Zwischenspeicherung für übersetzte Seiten](../../help/forms/using/configure-adaptive-forms-cache.md) adaptiver Formulare.

* Unterstützung für [Adobe Sign-Text-Tags in Automated forms conversion Service](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html).

* Unterstützung für [Konvertieren farbiger Formulare in adaptive Formulare](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html) mit [!DNL Automated Forms Conversion service].

* Unterstützung für SMB 2- und SMB 3-Protokolle.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.4 aktualisiert.

Eine vollständige Liste der in Experience Manager 6.5.6.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 6](new-features-latest-service-pack.md).

Im Folgenden finden Sie die Liste der Fehlerbehebungen in der Version 6.5.6.0.[!DNL Experience Manager]

### [!DNL Sites] {#sites-6560}

* Wählen Sie unter [!DNL Sites] oder [!DNL Screens] ein Projekt aus und klicken Sie auf [!UICONTROL Verwaltungsveröffentlichungen]. Benutzer können aufgrund von Benutzeroberflächenfehlern nicht im Assistenten [!UICONTROL Veröffentlichung verwalten] fortfahren. Insbesondere funktioniert die Option [!UICONTROL Publish] nicht (NPR-34099).
* Die Position von iParsys (geerbtes Absatzsystem) wird nicht auf die ursprüngliche Standardposition zurückgesetzt, nachdem die Optionen [!UICONTROL Vererbung abbrechen] oder [!UICONTROL Vererbung deaktivieren] (NPR-34097) deaktiviert wurden.
* Wenn `RolloutConfigManagerFactoryImpl` keine Rollout-Konfiguration laden kann, wird nicht versucht, die fehlenden Konfigurationen zu laden. Es gibt die zwischengespeicherten Konfigurationen (NPR-34092) zurück.
* In der Kernkomponente &quot;Text&quot;wird nach Verwendung der HTML-Quellbearbeitungsoption die Klasse aus dem Tag `em` entfernt (NPR-34081).
* Nach der Aktualisierung von Experience Manager 6.3.3 auf Experience Manager 6.5.3 dauert der Rollout-out-Vorgang viel länger und der Rollout schlägt mit einem Timeout-Fehler (NPR-34049) fehl.
* Das `htmlwriter` kodiert die Attributwerte nicht zurück. Das Markup, das im XF-Markup vorhanden ist, wird mit dekodierten Attributwerten (d. h. `"` anstelle von `&#34`) exportiert. Es verursacht Probleme auf der Seite der Zielgruppe mit Visual Experience Composer, die das exportierte XF (NPR-34048) verwenden.
* Verbessern Sie beim Verschieben von Seiten in [!DNL Experience Manager Sites] die Protokollierung, um den Fehler bei der Erstellung der Version mit Grund zu erfassen (NPR-34014).
* Bei [!DNL Rich Text Editor] wird das Absatz-Tag ebenfalls entfernt (NPR-33976).
* Wenn die Seite `siteadmin` (in der klassischen Benutzeroberfläche) geöffnet oder aktualisiert wird, sind die Optionen im Menü `New` deaktiviert (NPR-33949).

   ![Screenshot zum Problem fehlender Menüs in der klassischen Benutzeroberfläche](assets/33949_missing_menu.png)

* Ein [!DNL Content Fragment] kann nicht als `TemplatedResource` verwendet werden, da es in `ContentFragmentUsePojo` (NPR-33911) fehlschlägt.
* Synchrone und asynchrone Verschiebungen können zu Fehlern führen, die auf gleichzeitige Übertragungen zurückzuführen sind. Seitenverschiebungsvorgänge sind nur auf asynchrones Verschieben beschränkt. Es verhindert das gleichzeitige Verschieben von Seiten (NPR-33875).
* [!UICONTROL Der Vorgang &quot;] Veröffentlichung verwalten&quot;schlägt fehl, um Inhalte aus der Instanz &quot;Autor&quot;in &quot;Publish&quot;zu replizieren, und erzeugt einen JavaScript-Fehler (NPR-33872).
* Wenn mehrere Seiten oder Assets ausgewählt sind, um Versionen zu erstellen, wird die neue Version nur für die zuletzt ausgewählte Seite oder das zuletzt ausgewählte Asset erstellt (NPR-33866).
* Verschieben Sie eine Blueprint-Seite mit Live-Kopien in einen anderen Ordner. Beim Verschieben in den Originalordner schlägt der Verschieben-Vorgang ohne Fehler fehl (NPR-33864).
* Wenn mit der Aktion &quot;Verschieben&quot;eine Webseite in der [!DNL Sites]-Konsole umbenannt wird, werden im letzten Schritt des Assistenten zwei überlappende Dialogfelder angezeigt (NPR-33831).

   ![Screenshot zur Erläuterung des NPR-33831-Themas des sich überschneidenden Dialogs über Verlagerungen](assets/33831_rename_dialog.png)

* Die Eigenschaften `cq:acLinks` und `cq:acUUID` für [!DNL Adobe Campaign] auf der Kopie werden beim Kopieren und Einfügen entfernt (NPR-33794).
* Bei einem Rollout auf einer untergeordneten Seite einer abgetrennten übergeordneten Live-Kopie generiert [!DNL Experience Manager] eine Null-Zeiger-Ausnahme (NPR-33676).
* Die [!DNL RTE]-Komponenten in einem Layout-Container sind nicht sichtbar, wenn der Layout-Container kopiert und erneut auf die Seite eingefügt wird. Die [!DNL RTE]-Komponenten können nicht bearbeitet werden, werden aber bei einer Seitenaktualisierung angezeigt (NPR-33662).
* Wenn Sie die Größe einer Layoutkomponente für verschiedene Haltepunkte (mittel und groß) ändern, verhält sich das Layout nicht wie erwartet (NPR-33608).
* Im Inline-Bearbeitungsmodus unter [!DNL RTE] funktioniert das Ziehen eines Bildes nicht für Textkomponente (NPR-33602).
* Es ist möglich, eine Komponente in einer Blueprint-Seite mit demselben Namen wie der Seitenname zu erstellen. Bei der Rollout wird `_msm_moved` angefügt, um die Komponente umzubenennen. Die Komponente wird an das Ende des [!UICONTROL Absatzsystems] (NPR-33535) verschoben.
* Wenn offTime oder onTime auf vielen Seiten oder Assets eingestellt ist, ist es ressourcenintensiv und verlangsamt das System beim Start und Herunterfahren (NPR-33482).
* Ein Benutzer mit CRUD-Berechtigungen für `/content/experience-fragment` kann einen Ordner nicht löschen (NPR-33436).
* Sie können [!UICONTROL HTML &amp; JSON] als Option für [!UICONTROL Adobe Target Exportformat] in einem übergeordneten Ordner im Abschnitt [!DNL Experience Fragments] auswählen. Die gleichen Eigenschaften werden in der touchfähigen Benutzeroberfläche für die Unterordner dieses übergeordneten Ordners angezeigt. In CRXDE wird jedoch für `cq:adobeTargetExportFormat` nur HTML angezeigt, anstatt `html,json` anzuzeigen (NPR-33423).
* Veröffentlichen oder Rückgängigmachen der Veröffentlichung über ein Seitenalias wird nicht unterstützt. Entfernen Sie die Option, die anscheinend anders zu behaupten scheint (NPR-33415).
* Ein bestimmtes Tag kann in [!DNL Experience Manager] von einem Ort zu einem anderen verschoben werden. Sie kann auch auf verschiedene Seiten vor und nach dem Verschieben angewendet werden. Wenn Sie die Eigenschaften der Seiten bearbeiten, wird das Tag nicht zur Bearbeitung angezeigt, obwohl das Tag dasselbe ist (NPR-33353).
* Eine Seitenvorlage wird nicht richtig dargestellt, wenn ein Layout-Container aus einer Vorlage mit mehreren Layout-Containern gelöscht wird (NPR-33347).
* Versuchen Sie im Vorlageneditor, eine Vorlage zu löschen, die von mehr als 100000 Seiten unter `/content/` verwendet wird. Ein Fehler wird ohne Fehlermeldung angezeigt (NPR-33312).
* Die Umleitung auf die Seite [!DNL Experience Manager] mit Anker funktioniert in der Autoreninstanz nicht, da `PageRedirectServlets` die Abfrage nach einem URL-Fragment oder Anker (NPR-34288) setzt.
* Das Erstellen einer Marke unter `/content/campaign` führt zu einer Struktur, die das Erstellen von Kampagnen nicht zulässt. [!UICONTROL Die Option &quot;] Branding erstellen&quot;lässt die neu erstellte Marke ohne Möglichkeit,  [!UICONTROL Angebot und ] Aktivitäten zu erstellen, da keine   Option &quot;Erstellen&quot;vorhanden ist (NPR-34113).
* Sie können das [!DNL Live Copy] einer Seite aussetzen und die Vererbung wird, wie im Editor-Modus gesehen, unterbrochen. In den Seiteneigenschaften gibt das Symbol für Vererbung fälschlicherweise an, dass die Vererbung vorhanden ist und nicht beschädigt ist (NPR-34017).
* Seiten mit vielen Referenzen können nicht asynchron verschoben werden und manchmal schlägt der Verschieben-Vorgang fehl (CQ-4297969).
* Eine Webseite mit dem Zeichen `/` in der URL reagiert beim Authoring nicht mehr. Wenn beim Authoring eine Komponente hinzugefügt wird, erhöht sich die CPU-Auslastung und der Browser reagiert nicht mehr (CQ-4295749).
* Im Durchsuchen-Modus erwähnt NVDA keinen Wert, der über die Menüoption &quot;Typ/Größe&quot;ausgewählt wurde. Der visuelle Fokus liegt nicht auf dem ausgewählten Element. Benutzer, die auf eine Bildschirmlesehilfe angewiesen sind, können den Durchsuchen-Modus nicht verwenden (CQ-4294993).
* Beim Erstellen einer Webseite können Benutzer die Vorlage [!UICONTROL Inhaltsseite] auswählen. Auf der Registerkarte [!UICONTROL Social Media] wählen Benutzer eine [!UICONTROL Bevorzugte XF-Variante] aus. Um ein Erlebnisfragment im NVDA-Durchsuchenmodus auszuwählen, können Benutzer keine Tastenkombinationen verwenden (CQ-4292669).
* Die Bibliothek mit Handlebars wurde auf die sicherere Version 4.7.3 (NPR-34484) aktualisiert.
* Mehrere Site-übergreifende Skriptinstanzen in [!DNL Experience Manager Sites]-Komponenten (NPR-33925).
* Das Feld &quot;Ordnername&quot;beim Erstellen eines neuen Ordners ist anfällig für eine seitenübergreifende Skripterstellung (GRANITE-30094).
* Die Suchergebnisse auf der Seite [!UICONTROL  Willkommen] und die Pfadende-Vorlage sind anfällig für Cross-Site-Scripting (NPR-33719, NPR-33718).
* Das Erstellen einer binären Eigenschaft auf einem unstrukturierten Knoten führt zu Site-übergreifendem Skripten im Dialogfeld für binäre Eigenschaften (NPR-33717).
* Site-übergreifende Skripterstellung bei Verwendung der Option [!UICONTROL Zugriffskontrolle-Test] auf der CRX DE-Schnittstelle (NPR-33716).
* Benutzereingaben werden beim Senden von Informationen an den Client für verschiedene Komponenten nicht ordnungsgemäß kodiert (NPR-33695).
* Site-übergreifende Skripterstellung in der Kalenderversion für Experience Manager Inbox (NPR-33545).
* Eine URL, die mit `childrenlist.html` endet, zeigt eine HTML-Seite anstelle einer 404-Antwort an. Solche URLs sind anfällig für Cross-Site-Scripting (NPR-33441).


### [!DNL Assets] {#assets-6560}

**Barrierefreiheitsverbesserungen in Experience Manager Assets**

* Mithilfe der Tastenkombinationen können Benutzer jetzt auf die interaktiven Benutzeroberflächenoptionen in der [!UICONTROL References]-Liste der Assets zugreifen und sich darauf konzentrieren (NPR-34115).

* Bildschirmlesehilfen geben nun die beabsichtigte Aktion der Prädikate auf der Suchseite an (NPR-34104).

* Die Suchseite und die Suchergebnisseite haben jetzt informativere Titel für ein besseres Verständnis der Benutzer von Bildschirmlesehilfen (NPR-34093).

* Bildschirmlesehilfen geben jetzt die Optionen zum Löschen der ausgewählten Tags auf der Seite [!UICONTROL Einfach] des Assets [!UICONTROL Eigenschaften] (NPR-33972) an.

* Die Elemente in jeder Zeile in der Ansicht der Liste werden nun als Elemente derselben Zeile von Bildschirmlesehilfen (NPR-33932) angekündigt.

* Der Benutzerfokus beim Navigieren mit der `Tab`-Taste wechselt jetzt zur Schließoption in der Vorschau der Version (NPR-33863).

* Der Benutzerfokus wird nun auf das Suchsymbol verschoben, nachdem Omniture Search geschlossen wurde (NPR-33705).

* Die Optionen der umsetzbaren Benutzeroberfläche haben jetzt einen auffälligeren visuellen Fokus und einen verbesserten Kontrast bei der Navigation mit den Tasten der Tastatur. Die Tastaturbenutzer können die fokussierten Bereiche identifizieren (NPR-33542).

* Die Drag-Funktion mit der Tastatur funktioniert jetzt im [!UICONTROL Metadaten-Schema-Editor] im Durchsuchenmodus der Bildschirmlesehilfe (CQ-4296326).

* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * Die Tabelleninformationen werden nicht kommentiert, sobald das Dialogfeld geladen wurde.

   * Kann zu allen aufgelisteten automatischen Empfehlungen navigieren.

   * Beschreibt die angezeigten automatischen Vorschläge für [!UICONTROL Hinzufügen E-Mail-Adresse/Suche] (CQ-4294232).

* Durch die Verwendung der `Esc`-Taste zum Entfernen der Schnellaktion-Symbole aus der Ansicht der Karten wird der Tastaturfokus nicht mehr aus dem zuletzt fokussierten Element entfernt (CQ-4293554).

* Bei interaktiven Optionen auf der Benutzeroberfläche gibt die Bildschirmlesehilfe jetzt statt der wörtlichen Namen der Symbole ihren Zweck an (CQ-4272943).

* Der Tastaturfokus wird jetzt erfolgreich nach [!UICONTROL Flyout], [!UICONTROL InlineZoom], [!UICONTROL Shoppable_Banner], [!UICONTROL Zoom_dark], [!UICONTROL Zoom_light], [!UICONTROL ZoomVertical_dark_dark a11/> und [!UICONTROL ZoomVertical_light] Optionen beim Navigieren mit der Tabulatortaste in Asset-Details [!UICONTROL Viewer] in [!DNL Dynamic Media] (CQ-4290605).]

* [!UICONTROL Die Option &quot;Speichern und ] Schließen&quot;auf der Asset-  Eigenschaftenseite kann jetzt über die Tastatur aufgerufen werden (NPR-34107).

* Fehlermeldungen aufgrund falscher Kombinationen aus Benutzername und Kennwort auf der Anmeldeseite werden jetzt von Bildschirmlesehilfen bei jedem Auftreten des Fehlers angekündigt (NPR-33722).

* Im Kopfzeilenabschnitt von [!DNL Experience Manager] gibt die Bildschirmlesehilfe jetzt bei der Navigation im Durchsuchen-Modus an,

   * Automatisch bearbeitete Vorschläge in [!UICONTROL Geben Sie ein, um in Omniture zu suchen].

   * Der Status wurde für die Optionen [!UICONTROL Lösungen], [!UICONTROL Hilfe], [!UICONTROL Inbox] und [!UICONTROL Benutzer] erweitert oder reduziert.

   * Die Statusmeldung [!UICONTROL Hilfe suchen], die angezeigt wird, wenn der Benutzer eine Suchzeichenfolge in das Feld [!UICONTROL Hilfe] unter [!UICONTROL Hilfe] eingibt.

   ![Hilfemenü in der Kopfzeile](assets/Help_aem_header.png)

   *Abbildung:  [!UICONTROL Suchen Sie nach ] Helpin   Helpmenu.*

   * Die Fehlermeldung, wenn ein falscher Wert in das Feld [!UICONTROL Identität annehmen als] unter [!UICONTROL Benutzer] eingegeben wird und der Fokus korrekt auf das Textfeld (NPR-33804) verschoben wird.

   ![Benutzermenü in der Kopfzeile](assets/User_aem_header.png)

   *Abbildung:  [!UICONTROL Stellen Sie ] ein Feld im   Benutzermenü in der Kopfzeile dar.*

* Der Benutzer kann jetzt den Fokus mithilfe der Tastatur in folgenden Bereichen ändern:

   * [!UICONTROL Suchen/Hinzufügen Sie im ] Feld &quot;E-Mail-Adressen&quot;im  [!UICONTROL Dialogfeld &quot;] Linkfreigabe&quot;.

   * [!UICONTROL hinzufügen Benutzer oder ] Groupfield unter  [!UICONTROL Geschlossene ] Benutzergruppe in der   Berechtigungstabelle der  [!UICONTROL Ordnereigenschaften] (NPR-34452).

**In Experience Manager Assets behobene Probleme**

[!DNL Adobe Experience Manager] 6.5.6.0  [!DNL Assets] enthält Korrekturen an folgenden Problemen:

* Anmerkungen werden nicht hervorgehoben, wenn sie in der Zeitleiste des Assets ausgewählt werden (CQ-4302422).

* Bei der Vorschau von Marketing-Sicherheiten (wie Broschüre, Flyer und Visitenkarte), die mit der [!DNL Adobe InDesign]-Vorlage erstellt wurden, werden keine Zeilenumbrüche und Absatzbrüche angezeigt (NPR-34268).

* Die Extraktion von Text und damit die Volltextsuche für die hochgeladenen PDF-Dateien funktioniert nicht (NPR-34164). Um dies zu beheben, starten Sie die [!DNL sAdobe Experience Manager]-Bereitstellung nach der Installation von Service Pack 6 neu.

* In der Zeitleiste mehrseitiger Assets werden Anmerkungen angezeigt, die beim Durchsuchen des Assets in der Timeline-Ansicht auf alle Teilassets angewendet werden, anstatt die Anmerkungen anzuzeigen, die spezifisch für die jeweiligen Teilassets sind (NPR-34100).

* Asset-Ordner werden nicht mit der Option [!UICONTROL Veröffentlichung verwalten] veröffentlicht, wenn die Ordner Ressourcen in den Dateiformaten JavaScript, CSS oder JSON enthalten (NPR-34090).

* Wenn Sie die angewendeten Tags oder Filter in Omniture deaktivieren oder entfernen, wird die Abfrage mehrmals ausgeführt, was die Suchzeit verlängert (NPR-34078).

* In der Ansicht der Karte, wenn ein Workflow (für ein Asset in einem Ordner) ausgeführt oder ausstehend ist, wird die Seite neu geladen, bis der Workflow abgeschlossen oder beendet ist. Daher können Autoren nicht an den Assets im Ordner arbeiten, für die sie einen Bildlauf nach unten durchführen müssen (NPR-33986).

* Wenn der Benutzer ein veröffentlichtes Asset an einen neuen Speicherort verschiebt, wird das Asset erneut veröffentlicht, auch wenn die Option [!UICONTROL Neu veröffentlichen] deaktiviert ist. Dies führt dazu, dass sich viele verwaiste Assets in der Veröffentlichungsinstanz befinden. Das Standardverhalten ist jedoch, dass beim Verschieben eines Vorgangs für ein veröffentlichtes Asset die Veröffentlichung automatisch rückgängig gemacht wird. Dieses Asset wird erneut veröffentlicht, wenn der Autor beim Verschieben des Assets die Option [!UICONTROL Neu veröffentlichen] auswählt (NPR-33934).

* Die Seite [!UICONTROL Assets verschieben] für Assets in Sammlungen lädt nicht den gesamten HTML-Inhalt, z. B. [!UICONTROL Anpassen/Neu veröffentlichen]. Daher können die Verwender den Verschiebevorgang nicht abschließen (NPR-33860).

* Wenn Sie ein Asset verschieben und dem Namen und Titel der verschobenen Assets Sonderzeichen hinzufügen, wird am neuen Speicherort des Assets ein zusätzlicher Ordner (mit demselben Namen) erstellt (NPR-33826).

* [!UICONTROL Die ] Downloadschaltfläche für ein Asset wird deaktiviert, wenn   im   Download-Katalog (NPR-33730) die Option &quot;Emailoption&quot;ausgewählt ist.

* Der Fehler &quot;Request-URI too long&quot;wird bei der Ausführung von Massenvorgängen für Assets wie der Bearbeitung von Massenmetadaten (NPR-33723) beobachtet.

* Es wird ein JavaScript-Fehler festgestellt, und Benutzer können die Auswahlmöglichkeiten, die im Feld [!UICONTROL Dropdown] durch [!UICONTROL Hinzufügen durch die JSON-Funktion] im [!UICONTROL Ordner-Metadaten-Schema-Editor] generiert wurden, nicht auswählen oder löschen, wenn die hochgeladene JSON-Datei Leerzeichen oder Sonderzeichen enthält (NPR-333337717122).

* Die statischen Darstellungen von Assets werden nicht aktualisiert, wenn das Asset mit der Option [!UICONTROL Öffnen] in [!DNL desktop app] oder [!DNL Adobe Asset Link] aktualisiert wird und wieder mit [!DNL Adobe Experience Manager] (CQ-4296279) synchronisiert wird.

* In der Ansicht der Spalte werden beim Verschieben eines Assets auch die Assets verschoben, die ausgewählt wurden, bevor für sie die Option [!UICONTROL Filter] verwendet wird. Beachten Sie, dass bei Verwendung der Option [!UICONTROL Filter] die vorherige Auswahl aufgehoben wird (NPR-34018).

* Backslashes werden vor Sonderzeichen in Suchvorschlägen von Assets hinzugefügt, deren Name Sonderzeichen enthält (NPR-33834).

* Beim Erstellen von Regeln für die Dropdown-Liste in [!UICONTROL Ordnermetadaten-Schema-Formular] kann der Benutzer keine Werte aus der Spalte [!UICONTROL Feldauswahl] auswählen (CQ-4297530).

* Die Laufzeitkopie des benutzerdefinierten Workflow-Modells für Assets (erstellt in `/var/workflow/models/dam`) wird gelöscht, wenn Sie [!DNL Experience Manager] 6.5 Service Pack 5 oder eine frühere Version auf [!DNL Experience Manager] 6.5 (NPR-34532) installieren. Um die Laufzeitkopie abzurufen, synchronisieren Sie die Entwurfskopie des Workflow-Modells mit der Laufzeitkopie mit der HTTP-API:
   `<designModelPath>/jcr:content.generate.json`.

**Behobene Probleme in Dynamic Media**

* Wenn der Benutzer die Kodierungseinstellungen in Bearbeitungen definiert, nachdem das Video-Profil erstellt wurde, werden die Einstellungen für die intelligente Beschneidung aus den Video-Profilen entfernt (CQ-4299177).

* Assets flimmern beim Laden der Seite, wenn der Benutzer zwischen den Optionen der Seitenleiste umschaltet (z. B. [!UICONTROL Übersicht], [!UICONTROL Zeitschiene], [!UICONTROL Viewer]) auf der Seite mit den Asset-Details (NPR-34235).

* Folgende Probleme werden bei der Neuverarbeitung von Aufträgen beobachtet:

   * Die Job-ID fehlt im Auftragsbearbeitungsauftrag, der vom Neuverarbeitungsauftrag zurückgegeben wird.

   * Neuverarbeitung des Auftrags für Videoprotokolle nur Dateiname und nicht vollständigen Pfad.

   * Der Neuverarbeitungsauftrag verfügt nicht über die Option, den Asset-Typ als statisch festzulegen.

   * `ExcludeFromAVS` nicht angegeben ist (CQ-4298401).

* Die Funktion &quot;Intelligentes Beschneiden&quot;schlägt fehl, wenn einem Profil mit mehreren Seitenverhältnissen (z. B. 11) (NPR-34082) ein Bild hinzugefügt wird.

* Der Arbeitsablauf für DAM-Update-Assets wird ausgelöst, wenn der Benutzer auf der Registerkarte [!UICONTROL Workflow-Archiv] auf der Seite [!UICONTROL Workflow] unter [!UICONTROL Tools] in der Konfiguration mit Dynamic Media Scene7 (CQ-4299727) nach unten blättert.[!DNL Adobe Experience Manager]

* Symbole auf der Registerkarte [!UICONTROL Verhalten] von [!UICONTROL Viewer-Vorgabeneditor] sind nicht lokalisiert (CQ-4299026).

* In der Hauptansicht wird ein Ansicht mit einem falschen Layout angezeigt, das nicht in den Viewer passt, wenn der Viewer im interaktiven Modus ausgeführt wird (CQ-4298293).

* Änderungen an Bildvorgaben in [!UICONTROL Adobe Experience Manager] werden nicht mit dem Scene7 Publishing System (CQ-4299713) synchronisiert.

### [!DNL Commerce] {#commerce-6560}

* Links zu Assets von Produkten werden beim Verschieben von Assets nicht umgestaltet (NPR-34098).

### Plattform {#platform-6560}

* Protokolle können nicht mit dem Diagnosetool auf einer aktualisierten Experience Manager-Instanz (NPR-34336) heruntergeladen werden.
* Die Aktualisierung schlägt mit einem Fehler aufgrund von Abhängigkeiten zu einer bestimmten Version des `cq-wcm-api`-Gründungspakets (CQ-4300520) fehl.
* Die Standardwerte für die Einstellungen **[!UICONTROL Connect Timeout]** und **[!UICONTROL Socket Timeout]** für die Standardagentenkonfiguration (publish) sind nicht angegeben (NPR-33707).
* Aktualisierungen der Zuordnungskonfiguration unter `/etc/map.publish` beziehen sich nicht auf die Seiten der Site (NPR-34015).
* [API-Referenzdokumentation ](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html) enthält nicht die Dokumentation für das  `com.day.cq.tagging` Paket (CQ-4295864).

### Benutzeroberfläche {#ui-6560}

* Die Oberfläche des Offload-Browsers zeigt nicht alle Auftragsthemen an (NPR-34308).
* Die Oberfläche [Configuration Browser](/help/sites-administering/configurations.md) zeigt nicht alle Konfigurationen an (NPR-33644).
* Wenn Sie bei der Suche nach Identitätswechsel die `Esc`-Taste drücken, wird das Dialogfeld **[!UICONTROL Benutzer]** statt der Liste des Benutzers (NPR-34084) geschlossen.

### Integrationen {#integrations-6560}

* Aktivitäten mit langen Namen werden nicht mit [!DNL Adobe Target] (NPR-34254) synchronisiert.

* Wenn Sie eine Eigenschaft beim Erstellen einer neuen Adobe Startkonfiguration auswählen, wird die folgende Fehlermeldung angezeigt (NPR-33947):

   ```javascript
   GET http://hostname:Port/libs/cq/dtm-reactor/content/configurations/createcloudconfigwizard/jcr:content/body/items/form/items/wizard/items/general/items/fixedcolumns/items/container/items/general/items/property/data.html?query=&start=0&end=25&imsConfigurationId=Adobe%20Launch&companyId=&_charset_=utf-8 400 (Bad Request)
   ```

### Übersetzungsprojekte {#translation-6560}

* Ein Übersetzungsprojekt wird nicht erstellt, wenn das `authorizableID` des Benutzers Sonderzeichen enthält (NPR-33828).

### Sling {#sling-6560}

* Health Check und Musterdetektor haben überlappende Funktionen. Die Gesundheitsprüfung wird daher aus dem Produkt entfernt (NPR-33928).

### WCM {#wcm-6560}

* Foundation-Komponenten: Wenn Sie einer Seite eine Grundbildkomponente hinzufügen und ein Bild referenzieren, funktioniert der Vorgang `Undo` nicht (NPR-34516).

* Der Vorgang &quot;Seitenverschiebung&quot;kann nicht verwendet werden (CQ-4303028).

### [!DNL Communities] {#communities-6560}

* Die Freigabe eines Beitrags in sozialen Medien zeigt eine veraltete Option Google+ (NPR-33877).

* Community-Mitglied kann keine Gruppenvorlage oder andere Einstellungen für Gruppenfunktionen ändern (NPR-33530).

* Hyperlink-Tags auf Bildern werden in einem Forumsbeitrag (NPR-33464) nicht ordnungsgemäß generiert.

* Fehler bei der Zugänglichkeit werden in der Funktion &quot;Community Assignment&quot;(NPR-33442) identifiziert.

* Die vorhandenen Benutzer einer Community-Gruppe, die über die Admin-Konsole hinzugefügt wurde, werden bei jeder Änderung in der Community-Gruppenkonsole (NPR-34315) aus der Liste entfernt.

* Das `TagFilterServlet` leckt potenziell sensible Daten (NPR-33868).

<!--
* Tag filters are vulnerable to sensitive information disclosure (NPR-33868).
-->

### [!DNL Forms] {#forms-6560}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für  [!DNL Forms]. Sie werden mithilfe eines separaten [!DNL Forms] Add-On-Pakets bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-on installieren](#install-aem-forms-add-on-package) und [AEM Forms on JEE installieren](#install-aem-forms-jee-installer).

Nach der Installation des Add-On-Pakets [!DNL Experience Manager Forms] 6.5.6.0:

* Beenden Sie die [!DNL Experience Manager Forms]-Instanz.

* Löschen Sie die JAR-Dateien `bcpkix-1.51`, `bcmail-1.51` und `bcprov-1.51` aus dem Ordner `crx-repository\launchpad\ext`.

* Löschen Sie die Eigenschaft` sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider` aus der Datei `sling.properties`.

* Starten Sie die [!DNL Experience Manager Forms]-Instanz neu.

**Adaptive Formulare**

* Wenn ein adaptives Formularfragment fehlt, kann das adaptive Formular nicht gerendert werden (NPR-34302).

* In der Inhaltsbeschreibung für adaptive Formularfelder wird ein Absatz-HTML-Tag (NPR-34116) angezeigt.

* Wenn Sie die Eigenschaft **[!UICONTROL Auf Server]** erneut überprüfen auswählen, kann das adaptive Formular nicht gesendet werden (NPR-33876).

* Die Übermittlungsaktion **[!UICONTROL An REST-Endpunkt senden]** funktioniert nicht für ein adaptives Formular (CQ-4299044).

* Zugänglichkeit: Wenn Sie versuchen, ein adaptives Formular zu senden, ohne eine Anlage für ein Pflichtfeld hochzuladen, wird der Fokus nicht automatisch auf das Anlagenfeld verschoben (CQ-4298065).

* Wenn Sie einer Tabelle eines adaptiven Formulars Zeilen hinzufügen, zeigen die Optionen **[!UICONTROL Hinzufügen nach oben]** und **[!UICONTROL Hinzufügen nach unten]** keine geeigneten Ergebnisse an (CQ-4297511).

* Das Skript [!UICONTROL Wertaufgabe] wird falsch ausgelöst, was zu Datenverlust in einem adaptiven Formular (CQ-4296874) führt.

* Die Datumsauswahl funktioniert bei lokalisierten adaptiven Formularen nicht ordnungsgemäß (NPR-34333).

* Wenn der Dateiname einen Unterstrich oder ein Leerzeichen enthält, können Sie die Datei nicht an ein adaptives Formular anhängen (CQ-4301001).

* Wenn ein verschachteltes wiederholbares Bedienfeld mehr Vorkommen aufweist als sein übergeordnetes Element, schlagen alle Vorkommen eines solchen verschachtelten wiederholbaren Bedienfelds fehl (NPR-33666).

* Adaptive Formulare verfügen über einige offene Ressourcenauflöser. Dies führt zu Übermittlungsfehlern. Das Problem tritt gelegentlich auf (CQ-4299407).

* Wenn Sie die Feldkonfiguration zum ersten Mal öffnen, wird das Symbol Eigenschaften nicht angezeigt (CQ-4296284).

* Benutzer können beim Senden eines adaptiven Formulars Sendemetadaten wie `afPath`, `afSubmissionTime` und `signers` bearbeiten. Um das Problem zu beheben, werden die Metadatenwerte von den Formulardaten auf der Clientseite entfernt. Benutzer können das `FormSubmitInfo`-Objekt verwenden, um diese Werte vom Server abzurufen (NPR-33654).

* Benutzereingaben werden für [!DNL Forms]-Komponenten nicht ordnungsgemäß kodiert, wenn Informationen an den Client gesendet werden (NPR-33611).

**Arbeitsablauf**

* Wenn ein Workflow-Genehmiger eine Anlage hochlädt, wird die Anlage in `undefined` (NPR-33699) umbenannt.

* [!DNL Experience Manager] Der Vorgang &quot;Workflow-Bereinigung&quot;schlägt fehl und zeigt die folgende Fehlermeldung an (NPR-33575):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* [!DNL Experience Manager Forms] App für  [!DNL Windows] beendet die Antwort nach dem Senden eines Formulars (NPR-34409).

* Wenn Sie AEM Service Pack installieren, wird die Liste **Aufgaben** der Elemente nicht als Links angezeigt. Der Text für die Elemente **Aufgaben** enthält HTML-Tags (NPR-34317).

**Interaktive Kommunikation**

* Wenn Sie ein Textfragment mit verschachtelten wiederholbaren Dokumenten einschließen, kann die Interaktive Kommunikation nicht gespeichert werden (NPR-34095).

**Korrespondenzverwaltung**

* Wenn Sie ein Textfeldfragment ändern, das Datenwörterbuchwerte enthält, reagiert die Agent-Benutzeroberfläche nicht mehr (NPR-33930).

* Das Kopieren von Inhalten aus einem [!DNL Microsoft Word]-Dokument in ein Textfragment in einem Dokument führt zu Formatierungsproblemen (NPR-33536).

**Document Services**

* Wenn Sie eine PDF-Datei mit Output- und Forms-Diensten aus einer XDP-Datei generieren, führt dies zu fehlendem und überlappendem Text (NPR-34237, CQ-4299331).

* Wenn Sie eine HTML-Datei in PDF konvertieren, ist das `MaxReuseCount`-Attribut nicht konfigurierbar (NPR-33470).

* Wenn Sie eine PDF-Datei herunterladen, die interaktive Reader-Erweiterungen enthält, können Sie der PDF-Datei keine Anlagen mit [!DNL Adobe Reader] (NPR-33729) hinzufügen.

**Dokumentensicherheit**

* Der Signaturvorgang mit HSM-basierten Zertifikaten kann nach der Installation von [!DNL Experience Manager] Service Pack (NPR-34310) nicht in einer PDF-Datei ausgeführt werden.

**Designer**

* XForms kann nicht in Designer Version 6.5.x (CQ-4295322) geöffnet werden.

* Wenn Sie Designer öffnen, wird im Begrüßungsbildschirm ein falsches Jahr angezeigt (CQ-4295289).

* Wenn Sie [!DNL Acrobat DC] auf dem Server installieren, ist die Option **[!UICONTROL Formular verteilen]** inaktiv (CQ-4296304).

Informationen zu Sicherheitsaktualisierungen finden Sie unter [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.5.0  {#experience-manager-6550}

Adobe Experience Manager 6.5.5.0 ist ein wichtiges Update, das neue Funktionen, vom Kunden angeforderte wichtige Verbesserungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen umfasst, die seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht werden. Es kann auf Adobe Experience Manager 6.5 installiert werden.

Zu den wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.5.0 eingeführt wurden, gehören:

* Anonymer Zugriff auf CRXDE Lite ist nicht zulässig. Stattdessen werden die Benutzer zum Anmeldebildschirm weitergeleitet. Siehe [Entwickeln mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* Passen Sie die Spaltennamen an, die im Posteingang angezeigt werden.[!DNL Adobe Experience Manager]

* Verbesserte Barrierefreiheit in verschiedenen Bereichen des Experience Manager Web Content-Management (WCM), z. B. im Seiteneditor, in den Hauptkomponenten, in RTE und in der Admin-Benutzeroberfläche.

* Speichern Sie ein [!DNL Interactive Communication] als Entwurf.

* Unterstützung für [!DNL Oracle WebLogic 12] für Experience Manager Forms on JEE.

* Verbesserte Ausnahmebehandlung in [!DNL Adobe Experience Manager Assets] der Benutzeroberfläche.

* Um die Veröffentlichungs-URL für Dynamic Media Scene7 abzurufen, wird der `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi`-Schnittstelle eine neue Methode `getRemoteAssetPublishURL` hinzugefügt.

* [Barrierefreiheitsverbesserungen ](#assets-6550) gemäß  [!DNL Adobe Experience Manager Assets] den Web Content Accessibility Guidelines (WCAG).

* Paketfreigabe-Integration aus Adobe Experience Manager entfernt.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.3 aktualisiert.

Eine vollständige Liste der Funktionen, wichtigen Highlights und Schlüsselfunktionen, die in Experience Manager 6.5 Service Pack 5 eingeführt wurden, finden Sie unter [Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 5](new-features-latest-service-pack.md) .

Im Folgenden finden Sie die Liste der Fehlerbehebungen in der Version 6.5.5.0.[!DNL Experience Manager]

### [!DNL Sites] {#sites-6550}

* Experience Manager-Sites bieten eine Option zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung einer Seite aus ihrem Alias. Die Option funktioniert nicht (NPR-33415).
* Wenn ein Layout-Container aus einer Vorlage mit mehreren Vorlagen gelöscht wird, wird die Vorlage nicht korrekt dargestellt (NPR-33347).
* Wenn eine Experience Manager-Siteseite Teil eines großen Inhaltssatzes mit mehreren Live-Kopien ist, kann die Vorschau des Seitenversionsverlaufs nicht geladen werden (NPR-33311).
* Wenn Sie den Befehl &quot;Verschieben&quot;verwenden, um eine Experience Manager-Siteseite umzubenennen, wird der Seitentitel nicht aktualisiert (NPR-33264).
* Wenn Sie Seiten durch die Ansicht verschieben, werden die Spalten ausgeblendet (NPR-33216).
* Wenn der Name einer lokalen Komponente in einer Sprachkopie identisch mit dem Namen einer Komponente im Entwurf ist und die Komponente aus dem Entwurf herausgegeben wird, wird dem Namen der lokalen Komponente kein Begriff `_msm_moved` hinzugefügt (NPR-33208).
* Das Seitenumleitungs-Servlet hängt .html an eine Experience Manager-Sites-URL an, bei der ResourceType nicht `cq:Page` ist (NPR-33176).
* Wenn Sie eine Unterstruktur einfügen, gibt es keine Option zu entscheiden, ob die entsprechenden Unterseiten eingefügt werden sollen oder nicht (NPR-33149).
* Die Anzahl der Ergebnisse in Live-Verwendungen einer Komponente ist auf die Zahl 49 beschränkt (NPR-33058).
* Wenn Sie ein Inhaltsfragment auf einem Schema basieren und es einen obligatorischen Textbereich oder ein Pfadfeld enthält, kann das Inhaltsfragment nicht gespeichert werden (NPR-33007).
* Wenn Sie eine benutzerdefinierte Komponente mit der Standardkomponente &quot;Erlebnisfragment&quot;erstellen und sie auf den Seiten &quot;Experience Manager-Sites&quot;verwenden, zeigt Experience Manager keine Verweise (Verwendungszwecke) für die benutzerdefinierte Komponente (NPR-32852) an.
* Wenn Sie einen Ordner mit einer großen Anzahl von Verweisen umbenennen, werden viele Verweise auf den Ordner nicht aktualisiert (NPR-32765).
* Wenn Sie die Quellbearbeitungsoption aktivieren, steht sie für Inline-Vollbildoptionen zur Verfügung, bleibt aber für das Bearbeiten des Dialogfelds und der Vollbildoptionen des Rich-Text-Editors (NPR-32763) nicht mehr verfügbar.
* Wenn Sie über ein Mehrfeld verfügen und es ein erforderliches Feld (wie ein Dropdown-Feld oder ein Pfadfeld) in den Seiteneigenschaften eines Blueprints enthält, werden die Seiteneigenschaften der Live-Kopie nicht gespeichert (NPR-32751), wenn eine Seite, die ein solches Multifeld enthält, mit einem Rollout abgeschlossen wird.
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
* Bei der Dispatcher-Statusprüfung wird in den Protokolldateien die Meldung `Invalid cookie header` angezeigt (NPR-33629).
* XSS in PreferencesServlet (NPR-33438) reflektiert.
* Anonyme Benutzer können auf Funktionen der CRXDE Lite zugreifen (GRANITE-27790).

### [!DNL Assets] {#assets-6550}

>[!IMPORTANT]
>
>Windows-Benutzer von [!DNL Experience Manager desktop app] werden empfohlen, ein Upgrade auf [Desktop-App-Version 2.0.3.2](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html#whats-new-added) durchzuführen, um auf das DAM-Repository auf der [!DNL Adobe Experience Manager 6.5.5.0]-Instanz zuzugreifen. Da beim Zugriff auf das DAM-Repository auf der [!DNL Adobe Experience Manager] 6.5.5.0-Instanz Probleme auftreten können, wenn die Desktop-App Version 2.0.2 verwendet wird.

**Barrierefreiheitsverbesserungen in Experience Manager Assets**

* Es ist jetzt möglich, den Tastaturfokus auf die Liste [!UICONTROL Kommentare] und die Option &quot;anklickbar&quot;zu [!UICONTROL Erstellen] Versionskommentare unter [!UICONTROL Neue Version erstellen] in [!UICONTROL Zeitschiene] Bedienfeld mit Assets (NPR-33424) zu legen.

* Es ist nun möglich, die Option [!UICONTROL Ansicht Settings] für Assets zu erreichen und die Einstellungen im [!UICONTROL Ansicht Settings] Dialogfeld mithilfe der Tastenkombinationen (NPR-33420) zu ändern.

* Das Popup-Feld &quot;Liste&quot;des Kombinationsfeldes (in verschiedenen Feldern auf verschiedenen Seiten) zeigt nun Einträge als Liste von Optionen an, die von Bildschirmlesehilfen angekündigt werden können (NPR-33516).

* Die Sortierfunktion sortierbarer Kopfzeilen (in Liste Ansicht, [!UICONTROL Zeitschiene] Ansicht und [!UICONTROL Veröffentlichung verwalten]) werden jetzt von Bildschirmlesehilfen angekündigt und die Sortiersteuerung auf Spaltenköpfe können über die Tastatur aufgerufen werden (NPR-32979).

* Die anklickbaren Elemente wie Kommentarkarten, Versionsaktualisierungen, Kombinationsfelder und Chevron-Symbole von Menüs können jetzt mithilfe einer Tastatur (NPR-33514) fokussiert und damit interagiert werden.

* Funktionalität (oder Zweck der Aktion) von Insight-Symbolen (für die Verwendung, Impressionen und Klicks) auf [!UICONTROL Insights-Ansicht] werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33513).

* Schreibgeschützte Formularfelder (z. B. deaktivierte Felder auf [!UICONTROL Einfache Registerkarte] des Assets [!UICONTROL Eigenschaften]) können jetzt über die Tastatur fokussiert werden (NPR-33493, CQ-4273031).

* Bezeichnungen in verschiedenen Eingabefeldern sind nun dauerhafte Bezeichnungen (also barrierefrei) und nicht nur Platzhalterbeschriftungen, die bei der Texteingabe verschwanden (NPR-33475).

* Verschiedene Überschriftenebenen (z. B. Seitentitel und Abschnittsüberschriften) werden nun als Überschriften mit unterschiedlichen Ebenen als Bildschirmlesehilfen-Benutzer wahrgenommen (NPR-33471).

* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen (auf der Seite mit Kopf- und Zoomoptionen für Assets, Ordnernavigation), können jetzt über eine Tastatur aufgerufen werden (NPR-33468, CQ-4271412).

* Die Fortschrittsindikatoren [!UICONTROL Options], [!UICONTROL Scope] und [!UICONTROL Workflows] auf [!UICONTROL Manage Publication]-Seite werden jetzt korrekt von Bildschirmlesehilfen als Fortschrittsindikatoren anstelle von Registerkarten gelesen (NPR-33416).

* Die Farbe der Bewertungssymbole für Sterne (z. B. im Bereich [!UICONTROL Bewertung] von [!UICONTROL Erweitert] im Asset [!UICONTROL Eigenschaften] oder in der Ansicht der Karte) wird geändert, damit der entsprechende Kontrast für Benutzer mit eingeschränkter Sicht und ohne Farbwahrnehmung sichtbar ist (NPR-33414).

* Nach-oben-Pfeil neben dem Feld [!UICONTROL Kommentar] auf der Seite mit den Asset-Details können Sie jetzt mit den Tastaturschlüsseln (NPR-33397) auf den Link klicken.

* Die erweiterten und reduzierten Zustände des Dialogfelds [!UICONTROL Tags] für Asset [!UICONTROL Eigenschaften] und linke Schienennavigation (auf der Assets-Benutzeroberfläche) werden jetzt von Bildschirmlesehilfen korrekt angekündigt (NPR-33396).

* Titel aller durchsuchten Seiten auf [!DNL Adobe Experience Manager] Assets sind jetzt eindeutig (NPR-33343).

* Beim Navigieren in der Baumstruktur werden jetzt verschiedene Elemente der Baumstruktur-Ansicht-Steuerung von Bildschirmlesehilfen korrekt angekündigt (NPR-33304).

* Verschiedene Versionen von Assets in der [!UICONTROL Zeitschiene] Ansicht auf der Seite mit den Asset-Details können jetzt mit Tastaturbefehlen (NPR-33283) aufgerufen werden.

* Die Namen von Suchvorschlägen, die im Kombinationsfeld von Omniture enthalten sind, werden jetzt von Bildschirmlesehilfen bei Verwendung der Suchfunktion (NPR-33280) angekündigt.

* Klickbare Elemente und [!UICONTROL Gehe zu Link] in [!UICONTROL Bezugsleiste] werden jetzt von Bildschirmlesehilfen als anklickbare Elemente (NPR-33278) angekündigt.

* Informationen zur Tabellenstruktur (z. B. Zeile 1, Zelle 1, Tabelle) des Dialogfelds [!UICONTROL Link freigeben] wird von Bildschirmlesehilfen nicht mehr angekündigt, wenn das Dialogfeld geöffnet wird (NPR-33268).

* Der Zweck verschiedener Kombinationsfeldelemente (z. B. Pfadfeld und Option zum Öffnen des Auswahldialogfelds auf der Registerkarte Grundeinstellungen der Asset-Eigenschaften) wird nun von Bildschirmlesehilfen korrekt angekündigt (NPR-33235).

* Die Informationen, die die Zeilen in der Tabelle &quot;Ansicht&quot;auswählen können, werden jetzt Bildschirmlesehilfen-Benutzern mitgeteilt, wenn der Tastaturfokus auf sie gelegt wird. Wenn ein Zeiger mit der Maus auf die Zeilen zeigt, geben die Bildschirmlesehilfen die Informationen an (NPR-33234).

* Die Optionen (mit [!UICONTROL x]) zum Entfernen der ausgewählten Tags unter dem Feld [!UICONTROL Tags] auf der Registerkarte [!UICONTROL Einfach] von [!UICONTROL Eigenschaften] sind jetzt für Bildschirmlesehilfen verfügbar (NPR-33206).

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

* [!UICONTROL Wählen Sie] die Optionen &quot; [!UICONTROL Herunterladen]&quot;, &quot; [!UICONTROL Eigenschaften]&quot;und &quot; [!UICONTROL Weitere ] Aktionen&quot;für Elementkarten in  [!UICONTROL Insight ] Viewer, auf die jetzt über die Tastatur zugegriffen werden kann (NPR-32609).

* Visuell ausgeblendete Inhalte (z. B. Inhalte der Kopfzeilenmenüleiste in Suchergebnissen) werden von Bildschirmlesehilfen beim Zugriff über die Tastatur nicht mehr angekündigt (NPR-32606).

* Zweck der Beschriftungen für Kontrollen, die in der Kalenderdatumsauswahl in die nächsten und vorherigen Monate verschoben werden sollen, werden jetzt von Bildschirmlesehilfen (NPR-32604) angekündigt.

* Sternbewertungs-Symbole können jetzt mithilfe von Tastenkombinationen fokussiert und bearbeitet werden (NPR-32513).

* Die Funktion zur Steuerung der Videolautstärke ist jetzt über Registerkarten (zum Fokus auf Lautstärkeregler) und Pfeiltasten (zum Einstellen der Lautstärke) auf der Tastatur verfügbar (NPR-32065).

* Der Zweck der Eingabefelder mit Untergrenze ([!UICONTROL Von]) und Obergrenze ([!UICONTROL bis]) des Filters &quot;Dateigröße&quot;wird jetzt nicht gesichteten Bildschirmlesehilfen (NPR-32064) mitgeteilt.

* Das Menü [!UICONTROL Sprachen] in [!UICONTROL Formular Erstellen und übersetzen] ist jetzt für Bildschirmlesehilfen im Durchsuchenmodus verfügbar (CQ-4293906).

* Das Bedienfeld [!UICONTROL Referenzen] ist jetzt mit folgenden Erweiterungen verfügbar (NPR-33261, CQ-4293798):

   * Im Durchsuchen-Modus wird der Bildschirmlesehilfen-Fokus nicht mehr auf ausgeblendete mehrzeilige Bearbeitungsfelder unter den Abschnitten [!UICONTROL Site-Referenzen], [!UICONTROL Asset-Referenzen], [!UICONTROL Kopien] und [!UICONTROL Formularverweise] verschoben.

   * Bildschirmlesehilfen geben jetzt die Rolle der Elemente [!UICONTROL Site-Verweise] und [!UICONTROL Sprachkopien] an.

   * Der Fokus von Bildschirmlesehilfen im Durchsuchen-Modus wechselt in einer aussagekräftigen Sequenz zu verschiedenen Elementen.

* [!UICONTROL Metadata Schema ] Editorpage und seine Elemente sind jetzt über die Tastatur verfügbar und sind für Bildschirmlesehilfen geeignet (CQ-4290962, CQ-4272953).

* Der Zweck des `X`-Symbols zum Entfernen der ausgewählten Tags wird jetzt von Bildschirmlesehilfen zusammen mit der Anzahl der ausgewählten Tags (CQ-4273017) angekündigt.

* Um Verwirrung bei Benutzern ohne Sehbehinderung mit Bildschirmlesehilfen zu vermeiden, werden dekorative Symbole und Bilder jetzt von Bildschirmlesehilfen ignoriert (CQ-4272944).

**In Experience Manager Assets behobene Probleme**

[!DNL Adobe Experience Manager] 6.5.5.0 Assets bieten Korrekturen an folgenden Problemen:

* [!UICONTROL Die ] Option &quot;Workflow   erstellen&quot;für Assets in einer Sammlung ist deaktiviert, wodurch verhindert wird, dass der Workflow ausgelöst wird (NPR-32471).

* Wenn Sie in Metadaten-Schemas ein Kaskadenpopup verwenden und eine Dropdown-Option mit einem Apostroph (aus der untergeordneten Dropdown-Liste) auswählen und speichern, wird die ausgewählte Apostroph-Option nach dem erneuten Öffnen des Assets [!UICONTROL Eigenschaften] (NPR-32649) ausgeblendet.

* [!UICONTROL Asset Insights synchronisiert ] JBulbs und schlägt fehl, wenn ungültige Einträge (auf der Analytics-Seite) auftreten, anstatt zum nächsten Eintrag (NPR-32674) zu wechseln.

* Gyroscope ist nicht funktionsfähig, da Bewegungssensoren standardmäßig in mobilen Browsern im Panorama-Viewer deaktiviert sind (CQ-4272937).

* [!UICONTROL Der ] Konfigurationsassistent für verbundene Assets funktioniert mit dem Fehler 404 nicht, wenn 6.5.3 unter 6.5.1 (NPR-32730) installiert wird.

* Während des XMP Schreibvorgangs ändern alle benutzerdefinierten Metadateneigenschaften des Namensraums das benutzerdefinierte Präfix des Namensraums in &quot;ns2&quot;anstelle des konfigurierten Namensraums (NPR-32748).

* Verzögertes Laden wird nicht ausgelöst und es werden nur 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32750).

* `NullPointerException` wird aufgrund fehlender Node-Voreinstellungen im neu erstellten Profil (SAML/SSO) beobachtet. Dieser Fehler verhindert, dass neu angemeldete Benutzer die [!DNL Adobe Experience Manager Stock] Integration (NPR-32777) verwenden.

* In Protokollen zum Öffnen einer intelligenten Sammlung mit mehr als 10.000 Assets (NPR-32980) werden seitenübergreifende Warnungen angezeigt.

* Asset-Namen werden in Kleinbuchstaben geändert, wenn Assets von einem Ordner in einen anderen verschoben werden, und zwar in [!DNL Adobe Experience Manager], wenn sie im Dynamic Media Scene7 Runmode (NPR-32995) arbeiten.

* Ein durchsuchtes Asset kann nicht gelöscht werden, nachdem es aus den Suchergebnissen zu seinen Eigenschaften navigiert und dann zu den Suchergebnissen zurückgekehrt ist, um es zu löschen (NPR-32998).

* [!UICONTROL Die ] Option &quot;Nextoption&quot;bleibt bei der Auswahl des Zielordners in  [!UICONTROL &quot;] Assets verschieben&quot;deaktiviert (NPR-33356).

* [!UICONTROL Die ] Option &quot;Nextoption&quot;ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33275).

* Berechtigungen zum Ein- und Auschecken sind auf Adobe Asset Link (AAL) für Benutzer mit Berechtigung zum Löschen deaktiviert, auch wenn andere Berechtigungen wie Lesen, Erstellen oder Ändern gewährt werden (NPR-33272).

* Im Dialogfeld zum Herunterladen von Assets (NPR-33167) sind keine Smart-Zuschneiden-Darstellungen verfügbar.

* Ausnahmen sind in Protokollen beim Öffnen der Rail-Darstellungen für eine PDF-Datei unter einem Profil mit intelligenten Zuschnitten (CQ-4294201) zu beobachten.

* Bildvorgaben werden nicht veröffentlicht, wenn [!UICONTROL Dynamic Media-Synchronisierungsmodus] auf Experience Manager mit Dynamic Media Scene7-Ausführungsmodus (CQ-4294200) standardmäßig deaktiviert ist.

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert, und die Workflow-Instanz zeigt angehaltene Instanzen des DAM-Aktualisierungsassets (CQ-4293916).

* Das Erstellen einer Dynamic Media-Konfiguration auf Experience Manager funktioniert, auf der Benutzeroberfläche geschieht jedoch nichts bei der Auswahl von Speichern (CQ-4292442).

* Die Vorschau von F4V-Video-Assets funktioniert bei der progressiven Wiedergabe auf Safari/Mac nicht (CQ-4289844).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit dem Zeichen `.` in seinem Namen befindet (CQ-4289337).

* Die Miniaturansicht ist beschädigt, und das Videoverarbeitungsbanner wird nicht angezeigt, wenn ein Video kopiert wird (CQ-4284125).

* Beim Dimensional Viewer werden in Firefox bei einigen Modellen mit leeren Ansichten fälschlicherweise leere Miniaturansichten angezeigt (CQ-4283447).

* Die in Version 6.5.5.0 behobenen Leistungsprobleme lauten (CQ-4279206):

   * Es dauert zu lange, bis große Binärdateien auf die Dynamic Media-Bildverarbeitungsserver hochgeladen werden.

   * Die Zeit für die Erstellung von Miniaturbildern auf dem Experience Manager nimmt aufgrund der Dynamic Media Scene7-Architektur zu.

* Probleme mit der Dynamic Media Scene7-Migration schlagen bei Kunden mit einer großen Anzahl von Assets fehl (CQ-4279206).

* Das Layout des Video 360-Viewers ist beschädigt, wenn `setVideo` verwendet wird, und das Video wird bei Verwendung von `video= modifier` (CQ-4263201) nach unten verschoben.

* Während der Installation des Experience Manager-SDL-Pakets (NPR-33175) wird eine Fehlermeldung angezeigt.

* Anfälligkeit für SSRF in Experience Manager (NPR-33435).

### Plattform {#platform-6550}

* Der Filter [!DNL Sling] wird nicht aufgerufen, wenn der `sling:match`-Map-Eintrag unter `/etc/maps` (NPR-33362) erstellt wird.
* Experience Manager stürzt aufgrund eines Segmentierungsfehlers mit [!DNL Apache Lucene] (NPR-32988) ab.
* [!DNL Jackson] Kernpaket fehlt in der Datei &quot;Experience Manager uberjar&quot;(NPR-32848).
* CRXDE Lite lädt keine Inhalte für Benutzer ohne Leseberechtigung für die `jcr:primaryType`-Eigenschaft eines Knotens (NPR-32611).
* [!DNL Granite] Die Planung der Maintenance-Aufgabe wird während der Bereitstellung des Experience Managers zu oft neu initialisiert (CQ-4294627).
* Wenn eine SQL-Abfrage lange ausgeführt wird (z. B. 7 Stunden), reagiert Experience Manager nicht mehr (NPR-33044).

### Benutzeroberfläche {#ui-6550}

* Die Auswahl des Optionsfeldes bleibt in einem Multifeld (NPR-33309) nicht erhalten.
* Lazy Loading Limit funktioniert nicht für die Liste Ansicht (NPR-33124).
* Die Seite mit den Omniture Suchergebnissen zeigt keine Meldung an, wenn keine Übereinstimmungen vorliegen (NPR-32974).
* Der Omniture-Filter gibt alle Übereinstimmungen unter dem Knoten `/content` zurück, wobei der ausgewählte Speicherort ignoriert wird (NPR-32849).

### Integrationen {#integrations-6550}

* Der interne Cache wird gelöscht, wenn eine Seite mit einer Adobe Target-Komponente veröffentlicht wird (NPR-33162).
* Die Integration mit Adobe Target funktioniert nicht auf [!DNL Windows Internet Explorer] 11 (NPR-33111).
* Beim Konfigurieren von Adobe Target werden die Felder [!UICONTROL Firma] und [!UICONTROL Report Suite] bei der Auswahl einer Berichte-Quelle (NPR-32502) nicht angezeigt.
* Beim Exportieren von [!DNL Experience Fragments] mit [!DNL Adobe I/O] werden Metadaten wie &quot;Quellprodukt&quot;nicht nach Adobe Target exportiert (NPR-32159).
* Autorisierte IMS-Benutzer in der lokalen Experience Manager-Administratorgruppe können keine IMS-Konfigurationen erstellen oder ändern (NPR-33045).
* Adobe Startkonfigurationsseite zeigt nicht alle Datensätze an (NPR-33011).
* Benutzer in der Gruppe &quot;Inhaltsersteller&quot;können Eigenschaften einer Adobe Target-Komponente aufgrund eines JavaScript-Fehlers (NPR-32996) nicht bearbeiten.
* Site-übergreifende Skripterstellung für JSON (NPR-32744).

### Übersetzungsprojekte {#translation-6550}

* Übersetzte Tags werden nicht aus Übersetzungsdiensten von Drittanbietern (NPR-33154) in Experience Manager importiert.
* Auf der Seite &quot;Übersetzungskonfiguration&quot;wird ein falscher Übersetzungsanbieter angezeigt als der für die Übersetzung verwendete (NPR-32971).
* Durch das Hinzufügen eines Erlebnisfragmentordners zu einem vorhandenen Übersetzungsprojekt wird ein neues Projekt erstellt (NPR-32843).
* Ein `NullPointerException`-Fehler wird in den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32628) angezeigt.

### WCM {#wcm-6550}

* Seiten-Editor - Der [!DNL Sites] Seiten-Editor erlaubt es Benutzern, die nur über die Tastatur verfügen, nicht zum Hauptinhalt zu springen, anstatt den Tabulatorfokus durch alle Optionen zu verschieben, die in der Kopfzeile verfügbar sind (CQ-4293883).
* Seiten-Editor - Bedienfelder, die die Well-Komponente verwenden und gespeicherte Daten enthalten, werden aufgrund von Aktualisierungen in [!DNL Chrome]- und [!DNL Firefox]-Versionen (CQ-4292995) nicht angezeigt.
* MSM - Das Löschen einer Komponente von der Seite löscht die Komponente nicht aus der veröffentlichten Version der Seite (CQ-4292360).

### [!DNL Brand Portal] {#assets-brand-portal-6550}

* Wenn Sie ein veröffentlichtes Metadaten-Schema aus [!DNL Brand Portal] entfernen, wird ein Fehler ausgegeben (CQ-4292063).
* Wenn ein Administrator [!DNL Experience Manager Assets] 6.5.4 über Adobe Developer Console mit dem Markenportal konfiguriert, kann der [!DNL Brand Portal]-Benutzer das Asset des Beitragsordners nicht von [!DNL Brand Portal] bis [!DNL Experience Manager] (NPR-33046) veröffentlichen.
* Duplikat-Replikation der übergeordneten Ordner, die Konflikte verursachen (NPR-33001).

### [!DNL Communities] {#communities-6550}

* Karten können nicht in der Moderationskonsole mit der Schnellbearbeitungs-Menüoption (NPR-33117) gelöscht werden.
* Beim Zugriff auf die Seite [!UICONTROL Aktivität Stream] (NPR-33146) tritt ein Fehler auf.
* In der Autoreninstanz gelöschte Gruppen werden nicht aus allen Veröffentlichungsinstanzen entfernt (NPR-33199).
* Autoren werden nach dem Erstellen einer neuen Gruppe nicht zum Abschnitt [!UICONTROL Community-Gruppe] unter [!DNL Internet Explorer] 11 (NPR-33205) umgeleitet.
* Der Zugriff auf eine Nachricht in Experience Manager Inbox ändert den Status der Nachricht nicht in Lesen (NPR-32764).
* Wenn Sie eine [!DNL Communities]-Gruppe bearbeiten und das Miniaturbild ändern, wird das Gruppenminiaturbild nicht aktualisiert (NPR-32599).
* Ein Benutzer kann keine E-Mail an einen anderen Benutzer in einer Community senden (NPR-32598).
* Ein gesendeter Blog wird erst angezeigt, wenn der Benutzer die Seite aktualisiert (NPR-32391).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von User Generated Content (UGC) wird eine falsche ID der Quellseite gespeichert (CQ-4279355, CQ-4289703).
* Site-übergreifendes Skriptproblem (NPR-33203).

### Workflow {#workflow-6550}

* Die Option [!UICONTROL Zeitschiene] in der linken Leiste dauert länger als erwartet (NPR-32851).
* Nach dem Neustart einer Experience Manager-Instanz enthält die E-Mail für die Review-Aufgabe für eine Sammlung einen falschen Payload-Link (NPR-32774).

### [!DNL Forms] {#forms-6550}

>[!NOTE]
>
>Experience Manager Service Pack enthält keine Fehlerbehebungen für [!DNL Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [Experience Manager-Forms-Add-On installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) und [Experience Manager Forms on JEE installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

* Correspondence Management: Die Reihenfolge der Vermögenswerte in einem Zielgruppen-Bereich wird nach der Einreichung eines Schreibens (NPR-33359, NPR-33153) geändert.
* Adaptives Forms: Wenn ein Benutzer ein adaptives Formular bearbeitet, funktioniert die Option [!UICONTROL Beginn-Workflow] im Menü [!UICONTROL Seiteninformationen] nicht (NPR-33004).
* Adaptives Forms: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-32997).
* Adaptives Forms: Das Ändern des Bedienfeldlayouts in einem adaptiven Formular führt zu einem Fehler (CQ-4293880).
* Adaptives Forms: Eine neue Zeile zu einer Zeichenfolge in einem Wörterbuch für adaptive Formulare fügt dem Wörterbuch `&#xa;`-Zeichen hinzu (NPR-33266).
* Adaptive Forms-Barrierefreiheit: Wenn ein Benutzer ein adaptives Formular als HTML-Formular Vorschau, kann das Feld [!UICONTROL Freihandsignatur] den Tabulatorfokus nicht beibehalten (NPR-33159).
* Adaptive Forms-Barrierefreiheit: Die Fehlermeldungen, die beim Senden eines adaptiven Formulars angezeigt werden, sind nicht mit einem `aria-describedBy`-Attribut (NPR-33071) verknüpft.
* Adaptive Forms-Barrierefreiheit: Felder, die in einem adaptiven Formular als Pflichtfelder markiert sind, haben im ARIA-Schema (NPR-33070) nicht das obligatorische Attribut &quot;True&quot;.
* PDFG-Dienst: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33238).
* PDFG-Dienst: `CreatePDF`-Vorgang kann eine PDF-Datei nicht in das PDF-OCR-Format konvertieren (NPR-32994).
* PDFG-Dienst: Die PDF-Konvertierung schlägt für die 200. Instanz eines [!DNL OpenOffice]-Dokuments (NPR-32766) fehl.
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33169) abläuft.
* Designer: Bildschirmlesehilfen führen die Tab-Reihenfolge basierend auf der geografischen Standardreihenfolge statt der benutzerdefinierten Tab-Reihenfolge aus, die in der XDP-Datei (NPR-32160) definiert ist.
* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32778) ausgeblendet.
* XSS mit GuideSOMProviderServlet (NPR-32700) gespeichert.

## Adobe Experience Manager 6.5.4.0 {#experience-manager-6540}

Adobe Experience Manager 6.5.4.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Erweiterungen sowie Leistung, Stabilität und Sicherheitsverbesserungen umfasst. Dieses Update wurde seit der allgemeinen Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht. **** Es kann auf Adobe Experience Manager 6.5 installiert werden.

Zu den wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5.4.0 eingeführt wurden, zählen:

* Adobe Experience Manager Assets wird jetzt über die [!DNL Adobe I/O]-Konsole mit dem Markenportal konfiguriert.

* Ein neuer Schritt [Druckbare Ausgabe generieren](../forms/using/aem-forms-workflow-step-reference.md) ist jetzt für Adobe Experience Manager Forms Workflows verfügbar.

* [Unterstützung für ](../forms/using/resize-using-layout-mode.md) den Layoutmodus für adaptive Formulare und interaktive Kommunikation in mehreren Spalten.

* Unterstützung für [Rich Text](../forms/using/designing-form-template.md) in HTML5-Formularen.

* [Barrierefreiheitsverbesserungen ](new-features-latest-service-pack.md#accessibility-enhancements) in Experience Manager Assets.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.8 aktualisiert.

* Sie können jetzt ausgewählte Inhaltsunterbauten mit *Dynamic Media - Scene7-Modus* synchronisieren, anstatt mit `content/dam`.

* Die Integration des Formulardatenmodells mit dem SOAP-Webdienst unterstützt jetzt Auswahlgruppen oder Attribute für Elemente.

* SOAP-Eingabe- oder -Ausgabe und komplexe Datenstrukturen unterstützen jetzt die dynamische Gruppenersetzung.

Eine vollständige Liste der in den neuesten Service Packs eingeführten Funktionen und wichtigen Highlights finden Sie unter [Neue Funktionen in Adobe Experience Manager 6.5 Service Packs](new-features-latest-service-pack.md).

### Sites {#sites-fixes}

* Wenn eine URL einer Adobe Experience Manager Sites-Seite einen Doppelpunkt (`:`) oder ein Prozentsymbol (`%`) enthält, reagiert der Browser nicht mehr und die CPU-Auslastung steigt an (NPR-32369, NPR-31918).

* Wenn eine Experience Manager-Siteseite zur Bearbeitung geöffnet und eine Komponente kopiert wird, steht die Einfügeaktion für einige Platzhalter nicht zur Verfügung (NPR-32317).

* Wenn der Assistent zum Verwalten von Veröffentlichungen geöffnet wird, wird ein Erlebnisfragment, das mit einer Kernkomponente verknüpft ist, nicht in den Listen veröffentlichter Verweise (NPR-32233) angezeigt.

* Die Übersicht über Live-Kopien in der Touch-Benutzeroberfläche dauert wesentlich länger als die klassische Benutzeroberfläche (NPR-32149).

* Wenn sich die Server- und die Maschinenzeit in unterschiedlichen Zeitzonen befinden, zeigt die geplante Veröffentlichungszeit die Serverzeit in der Touch-Benutzeroberfläche an, während in der klassischen Benutzeroberfläche die Maschinenzeit angezeigt wird (NPR-32077).

* Experience Manager-Sites können keine Seite mit einem Suffix in der URL (NPR-32072) öffnen.

* Wenn ein Benutzer ein Inhaltsfragment bearbeitet, wird eine gelöschte Variante des Inhaltsfragments wiederhergestellt (NPR-32062).

* Benutzer dürfen ein Inhaltsfragment speichern, ohne in den erforderlichen Feldern Informationen anzugeben (NPR-31988).

* kernel.js und ui.js sind nicht vorab erfüllt oder zwischengespeichert. Dies führt zu zusätzlicher Zeit beim Rendern von Seiten (NPR-31891).

* Wenn PageEventAuditListener aktiviert ist, wird die Länge der Warteschlange zum Übernehmen verlängert. Es wirkt sich auf die Leistung vieler Vorgänge wie Massenveröffentlichung, Navigation, Massenbewegung von Assets aus (NPR-31890).

* Wenn Erlebnisfragmente gezogen werden, wird eine hohe Reaktionszeit beobachtet (NPR-31878).

* Wenn Sie die Option Komponente hierher ziehen im Platzhalter eines interaktiven Rasters auswählen, wird eine GET gesendet und die Anforderung führt zum HTTP-403-Fehler (NPR-31845).

* Wenn Sie den Inhalt innerhalb desselben Ordners verschieben, ist die Option zum Verschieben der Seite deaktiviert (NPR-31840).

* Im Strukturmodus für bearbeitbare Vorlagen zeigt die Liste der zulässigen Komponenten im Layout-Container falsche Ergebnisse an. Im Layout-Container (NPR-31816) werden nur Komponenten mit Design-Dialog angezeigt.

* Wenn eine Seite schreibgeschützte Berechtigungen für einen Benutzer hat, ist die Option &quot;Eigenschaften öffnen&quot;in sites.html, jedoch nicht in editor.html (NPR-31770) sichtbar.

* Wenn ein Benutzer auf die Schaltfläche Erstellen klickt, ist die Seitenoption nicht verfügbar (NPR-31756).

* Die Kampagne in der Adobe-Kampagne mit OOTB (Out-of-the-Box)-Designimportkomponente (NPR-31728) kann nicht synchronisiert werden.

* Wenn Sie versuchen, eine Aufzählungszeichen-Liste in eine nummerierte Liste zu ändern, werden nur die ersten beiden Elemente der Liste geändert (NPR-31636).

* Wenn eine Seite nicht verfasst ist und die untergeordnete Node ausgewählt ist, wird im Auswahldialogfeld weiterhin die ursprüngliche Node angezeigt. Wenn die Seite erstellt wird und der Benutzer auf &quot;Durchsuchen&quot;klickt, wird die Seite zum Stammknoten statt zum erstellten Knoten (NPR-31618) umgeleitet.

* Das Dialogfeld für die Konfiguration der Ansicht funktioniert nicht ordnungsgemäß bei der Funktion für den Arbeitsablauf für die Anpassung des Posteingangs (NPR-32503 und NPR-32492).

* Beim Anzeigen von Workflow-Informationen mit Inbox (CQ-4282168) wird eine Fehlermeldung angezeigt.

### Assets {#assets-6540-enhancements}

* Die Schaltfläche zum Trigger-Workflow auf der Seite zur Asset-Erfassung ist deaktiviert (NPR-32471).

* Ein Ordner ohne Namen wird in SPS (Scene7 Publishing System) erstellt, während ein Asset in Experience Manager mit Dynamic Media Scene7-Konfiguration (NPR-32440) von einem Ordner in einen anderen verschoben wird.

* Die Aktion zum Verschieben aller Assets (mit &quot;Alle auswählen&quot;und dann &quot;Verschieben&quot;) in einen Ordner mit veröffentlichten Assets schlägt fehl (NPR-32366).

* Die Generierung von Ausgabeformaten für Assets mit ${extension} schlägt fehl (NPR-32294).

* Die URLs im Versionsverlauf werden auf der Eigenschaftenseite für Assets unter &quot;Verwiesen auf&quot;angezeigt (NPR-31889).

* Die von DAM heruntergeladene ZIP-Datei kann nicht mit WinZip (NPR-32293) geöffnet werden.

* Ursprüngliche Berechtigungen eines Ordners werden aktualisiert, wenn Ordnereinstellungen geöffnet werden, um den Ordnertitel oder das Miniaturbild zu ändern und dann zu speichern (NPR-32292).

* Das Kalendersymbol für geplante Aktivierungen wird nicht in der Statusspalte (in der Classic UI der DAM-Asset-Auflistung) für Assets angezeigt, deren Aktivierung für ein späteres Datum und eine spätere Uhrzeit geplant ist (NPR-32291).

* Die Erstellung von Snippets mithilfe von Snippet-Vorlagen gibt beim Erstellen von Snippets (NPR-32290) Fehler beim Suchen nach Sammlungen.

* Mehrere Abfragen der Suche werden ausgelöst, wenn mehrere Tags aus dem Suchfilter ausgewählt werden (NPR-32143).

* In der Benutzeroberfläche &quot;Experience Manager Assets&quot;werden abgeschnittene Dateinamen angezeigt, wenn Assets mit mehr als 50 Zeichen im Dateinamen hochgeladen werden (NPR-32054).

* Alle Kontrollkästchen im Filterbedienfeld werden gelöscht, wenn das erste und das zweite Kontrollkästchen geleert werden, wenn in Adobe Stock die Kontrollkästchen der Stufe 2 aktiviert wurden (NPR-31919).

* Die Datei- und Ordnersuche mit Omniture-Facetten bildet eine Ausnahme (NPR-31872).

* Die Feldhervorhebung für die obligatorische Feldauswahl im Metadateneditor wird auch nach Auswahl des erforderlichen Schemas nicht entfernt, wenn die Abhängigkeitsregeln im entsprechenden Metadaten-Formular (NPR-31834) festgelegt sind.

* Vollständige Namen von Tags auf Blattebene (aus der Taghierarchie) werden auf der Seite &quot;Asset-Eigenschaften&quot;nicht angezeigt (NPR-31820).

* Die Verwendung des Befehls &quot;Zurück&quot;auf der Seite &quot;Asset-Eigenschaften&quot;im Safari-Browser gibt einen Fehler zurück (NPR-31753).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Auf der Seite &quot;Assets-Detail&quot;von PDF-Assets werden keine Aktionsschaltflächen angezeigt, mit Ausnahme der Schaltflächen &quot;An Sammlung&quot;und &quot;Hinzufügen Darstellung&quot;in Experience Manager, der im Dynamic Media Scene7-Ausführungsmodus ausgeführt wird (CQ-4286705).

* Die Verarbeitung von Assets durch den Batch-Upload von Scene7 (CQ-4286445) dauert zu lange.

* Die Schaltfläche &quot;Speichern&quot;importiert kein Remote-Set, wenn der Benutzer im Set-Editor im Dynamic Media Client keine Änderungen vorgenommen hat (CQ-4285690).

* Die Miniaturansicht von 3D-Assets ist nicht informativ, wenn ein unterstütztes 3D-Modell in Experience Manager integriert wird (CQ-4283701).

* Der unverarbeitete Status der Viewer-Vorgabe für intelligente Beschneidung wird zweimal neben dem Vorgabennamen auf dem Bannertext angezeigt (CQ-4283517).

* Auf der Detailseite des Assets (CQ-4283309) wird eine falsche Höhe des Containers eines hochgeladenen 3D-Modells, das in der Vorschau im 3D-Viewer angezeigt wird, festgestellt.

* Karussell-Editor in IE 11 im Dynamic Media Hybrid-Modus des Experience Managers (CQ-4255590) nicht geöffnet.

* Der Tastaturfokus wird in der Dropdown-Liste &quot;E-Mail&quot;im Dialogfeld &quot;Herunterladen&quot;in Chrome und Safari-Browsern (NPR-32067) angehalten.

* Das Kontrollkästchen &quot;Alle Inhalte synchronisieren&quot;ist beim Hinzufügen der DM Cloud-Konfiguration auf dem Experience Manager nicht standardmäßig aktiviert (CQ-4288533).

### Foundation-Benutzeroberfläche {#foundation-ui-6540}

* Die Maussteuerung wechselt zum vorherigen Filterfeld, anstatt im vorhandenen Filterfeld zu bleiben, während Assets mit dem Filterbedienfeld (NPR-32538) gesucht werden.

* Plattform-Tagging: Die Suche nach Tags durch Eingabe in die Tag-Felder zeigt Tags außerhalb der Root-Grenzen an und berücksichtigt nicht die `rootPath`-Eigenschaft der Tag-Felder (NPR-31895).

* Plattform-Benutzeroberfläche: Pfadbrowser wird umgebrochen, wenn im Textfeld ein ungültiger Pfad hinzugefügt wird (NPR-31884).

* Die Benachrichtigung wird hinter einem fixierbaren Menü bei der Seitenauswahl (NPR-31628) versteckt.

### Plattform {#platform-sling-6540}

* (HTL) Unterstriche ersetzen Doppelpunkte im Pfadabschnitt der URL (NPR-32231).

### Projekte {#projects-6540}

* Schaltfläche &quot;Erstellen&quot;ist für den Benutzer nicht sichtbar, auch wenn der Benutzer berechtigt ist, ein Projekt im Unterordner zu erstellen (NPR-31832).

### Projektübersetzung {#projects-translation-6540}

* Die Erstellung eines Übersetzungsprojekts bricht die Benutzeroberfläche aus, wenn die Option &quot;Beschneidungsbereiche&quot;in `Apache Sling JSP Script Handler` (NPR-32154) aktiviert ist.

* Fehler in UI- und Null-Punkt-Ausnahme in Fehlerprotokollen werden beobachtet, wenn ein zu übersetzendes Tag einem Übersetzungsprojekt hinzugefügt wird (NPR-31896).

### Integrationen {#integrations-6540}

* Die URL-Erstellung der Startbibliothek basiert nur auf den Werten `path` und `library_name` der Start-API und basiert nicht auf dem Wert `library_path` (NPR-31550).

* Während der Verarbeitung von LiveFyre-bezogenen Elementen wird eine Fehlermeldung angezeigt (FYR-12420).

* ReportSuitesServlet ist anfällig für SSRF (NPR-32156).

### WCM-Vorlagen-Editor {#wcm-template-editor-6540}

* Im Strukturmodus für bearbeitbare Vorlagen zeigt die Liste für zulässige Komponenten im Layout-Container keine Komponente für die Verknüpfungsschaltfläche an (CQ-4282099).

### WCM-Seiten-Editor {#wcm-page-editor-6540}

* Fehler werden bei der Auswahl einer Überlagerung und der anschließenden Auswahl von reaktionsfähigen Raster Ziehen Sie Komponenten hierher (CQ-4283342).

### Kampagnen-Targeting {#campaign-targeting-6540}

* Die Konfiguration der Zielgruppe Cloud schlägt fehl, wenn die Fehlermeldung &quot;get mboxes&quot;fehlgeschlagen ist (CQ-4279880).

### Brand Portal {#assets-brand-portal-6540}

* Markenportalbenutzer können bei einem Upgrade auf [!DNL Adobe I/O] auf Experience Manager 6.5.4 (CQDOC-15655) keine Beitragsordnerelemente für [!DNL Assets] veröffentlichen. Für eine sofortige Fehlerbehebung in Experience Manager 6.5.4 wird empfohlen, [den Hotfix](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) herunterzuladen und auf Ihrer Autoreninstanz zu installieren.

* Popup-Schemas für Metadaten sind in den Asset-Eigenschaften nicht sichtbar (CQ-4283287).

* Das Metadaten-Unterschema zeigt keine Registerkarten basierend auf dem MIME-Typ in den Asset-Eigenschaften an (CQ-4283288).

* Beim Rückgängigmachen der Veröffentlichung des Metadatenschemas wird eine Fehlermeldung angezeigt, obwohl das Schema im Backend entfernt wurde.

* Für ein veröffentlichtes Asset wird kein Bild für die Vorschau angezeigt (CQ-4285886).

* Benutzer kann Assets, die ein einzelnes Anführungszeichen im Namen enthalten (CQ-4272686), nicht veröffentlichen oder die Veröffentlichung rückgängig machen.

* Die Geschäftsbedingungen werden beim Herunterladen mehrerer Assets nicht angezeigt (CQ-4281224).

* Geringfügige Sicherheitslücken wurden behoben.

### Communities {#communities-6540}

* Das Formular &quot;Create Member&quot;wird als leere Seite angezeigt (NPR-31997).

* Der Benutzer kann den Analytics-Bericht nicht in der Autoreninstanz (NPR-30913) Ansicht werden.

### Oak- Indizierung und Abfragen {#oak-indexing-6540}

* MS Word- und MS Excel-Dokumente, die JPEG-Image enthalten, wenn mit Tika Parser analysiert werden kann, und der Fehler class not found (Klasse nicht gefunden) wird beobachtet (NPR-31952).

### Forms {#forms-6540}

>[!NOTE]
>
>Experience Manager Service Pack enthält keine Fehlerbehebungen für Experience Manager Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Darüber hinaus wird ein kumulatives Installationsprogramm veröffentlicht, das Korrekturen für Adobe Experience Manager Forms on JEE enthält. Weitere Informationen finden Sie unter [Experience Manager-Forms-Add-On installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) und [Experience Manager Forms on JEE installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

* Correspondence Management: Briefe zeigen zusätzliche Zeichen nach der Übermittlung an die Workflows an (NPR-32626).

* Correspondence Management: Briefe zeigen einen Dropdown-Platzhalter als Textkomponente an, nachdem sie an Workflows gesendet wurden (NPR-32539).

* Correspondence Management: Die in der Briefvorlage definierten Standardwerte werden nicht im Vorschau-Modus (NPR-32511) angezeigt.

* Mobile Forms: Die Senden-Schaltfläche wird beim Rendern eines XDP-Formulars in einer HTML-Version (NPR-32514) als vergrößert angezeigt.

* Dokument-Dienste: URL-Zugriffsfehler für Briefe und einige andere Seiten nach Anwendung von Service Pack 2 (NPR-32508, NPR-32509).

* Dokument-Dienste: Wenn die Anzahl der Transaktionen auf einem Server eine bestimmte Grenze überschreitet, schlägt die Konvertierung von HTML in PDF fehl und die Dateitypeinstellungen werden vom [!DNL Forms]-Server (NPR-32204) entfernt.

* Adaptives Forms: Das Tool zur Barrierefreiheit des Browsers meldet Fehler in adaptiven Formularen gemäß den Richtlinien für WCAG2 Level AA (NPR-32312, NPR-32309, CQ-4285439).

* Adaptives Forms: Chrome-Browser-Barrierefreiheitstool berichtet über einen Best Practice-Fehler (NPR-32310).

* Adaptives Forms: Übersetzungsprobleme beim Konfigurieren eines adaptiven Formulars, das in eine Experience Manager-Siteseite eingebettet ist (NPR-32168).

* Workbench: Beim Verwenden des Vorgangs &quot;PDF-Eigenschaften abrufen&quot;für den PDF Utilities-Dienst (NPR-32150) wird eine Fehlermeldung angezeigt.

* Dokument Security: Eine geschützte PDF-Datei kann nicht offline geöffnet werden, wenn die Option DisableGlobalOfflineSynchronizationData auf True (NPR-32078) eingestellt ist.

* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32547, NPR-31983, NPR-31950) ausgeblendet.

* Designer: Wenn eine Tabelle zusammengeführte Zellen enthält, schlägt der Barrierefreiheitstest für die Ausgabe-PDF-Datei fehl, die mithilfe des Ausgabediensts (CQ-4285372) aus einem XDP-Formular konvertiert wurde.

* Foundation JEE: Wenn ein Experience Manager-Forms-Server von einem Cluster getrennt ist, verhindern Cache-Probleme, dass er eine erneute Serververbindung herstellt (NPR-32412).

## Adobe Experience Manager 6.5.3.0 {#experience-manager-6530}

[!DNL Adobe Experience Manager] 6.5.3.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit der Version 6.5 im  **April 2019** veröffentlicht wurden. Es kann auf [!DNL Adobe Experience Manager] 6.5 installiert werden.

Einige der wichtigsten Highlights dieser Service Pack-Version sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.6 aktualisiert.

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Ansicht der Liste hinzugefügt.

* Die Sortierung von Assets basierend auf der Spalte &quot;Name&quot;wurde in der Ansicht &quot;Liste&quot;aktiviert.

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen.

* [!DNL Dynamic Media] unterstützt Smart Imaging.

* Möglichkeit zur Einstellung der Abwesenheitseinstellungen in [!DNL Experience Manager] Workflows.[](../forms/using/configure-out-of-office-settings.md)

* Möglichkeit zur Freigabe von Inbox- oder Posteingangselementen ](../forms/using/configure-shared-queues-osgi.md) für andere Benutzer in [!DNL Experience Manager] Workflows.[

* Möglichkeit, interaktive Kommunikation im Stapelmodus zu generieren.[](../forms/using/generate-multiple-interactive-communication-using-batch-api.md)

* Die Version von jQuery im Paket ContextHub wurde auf 3.4.1 aktualisiert.

### Assets {#assets-6530-enhancements}

**Produktverbesserungen**

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus (NPR-27573) erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wird in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Liste Ansicht (NPR-31312) hinzugefügt.

* In der Ansicht &quot;Liste&quot;können Benutzer die Liste der Assets mit der Spalte [!UICONTROL Name] (NPR-31299) sortieren.

* Die Dateien GLB, GLTF, OBJ und STL können in der Vorschau auf der Seite [!UICONTROL Asset Details] in DAM (CQ-4282277) angezeigt werden.

* `ReplicationOnModifyListener` Ereignis wird beim Hochladen von Chunk-Knoten in ausgelöst  [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen (CQ-4278995).

* [!DNL Dynamic Media] unterstützt Smart Imaging (CQ-4222249).

* Die Ansicht &quot;Suchen&quot;oder &quot;Durchsuchen&quot;wird in der Foundation-Auswahl als Standard-Ansicht festgelegt, wenn in der Anfrage Abfrage-Parameter übergeben werden (NPR-31601).

**Fehlerkorrekturen**

* Metadaten für einige PDF-Dokumente werden beim Ändern des Titels (NPR-31629) nicht aktualisiert und im PDF-Format gespeichert.

* Asset Sharing funktioniert nicht für ein Asset, das im Dateinamen ein Pluszeichen (`+`) enthält (NPR-31547).

* Änderungen im Standardsuchformular Assets Admin Search Rail funktionieren nicht wie erwartet (NPR-31502).

* Vorschläge werden nicht angezeigt, wenn Sie die Omniture-Ansicht für Assets zum Durchsuchen von Assets verwenden (NPR-31496).

* Asset-Verweise in Sammlungen werden nicht aktualisiert, wenn die referenzierten Assets an einen anderen Speicherort verschoben werden, sofern dieselben Assets von verschiedenen Benutzern durch unterschiedliche Sammlungen referenziert werden (NPR-31486).

* Duplikat-IPTC-Tags werden Asset-Metadaten hinzugefügt (NPR-31328).

* Die Anzahl der Suchergebnisse wird nicht genau aktualisiert, wenn eine Suche über die Filterleiste ausgelöst wird (NPR-31316).

* Alle Kontrollkästchen werden deaktiviert, wenn die Kontrollkästchen der zweiten Ebene im Filter &quot;Dateityp&quot;deaktiviert werden, und der Text in der Suchleiste stimmt nicht mit den ausgewählten oder nicht ausgewählten Eigenschaften überein (NPR-31287).

* Alle Mitglieder (Benutzer/Gruppen) können nicht aus dem Abschnitt &quot;Mitglieder&quot;eines Ordners entfernt werden. beim Versuch, alle Benutzer zu entfernen, wird der angemeldete Benutzer zur Liste hinzugefügt (NPR-31171).

* Assets mit Pluszeichen (`+`) im Dateinamen können nicht gelöscht werden (NPR-31162).

* Dropdown-Menü erstellen, das im oberen Menü bei Auswahl eines Ordners angezeigt wird, zeigt nicht &quot;Ordner&quot; als Erstellungsoption (NPR-30877).

* Ordnerauswahl &quot;Erstellen&quot;> &quot;DateiUpload&quot;-Aktionselement fehlt, wenn ACL für Verweigern `jcr:removeChildNodes` und `jcr:removeNode` auf Pfad für einen Benutzer angewendet wird (NPR-30840).

* DAM Workflows beim Hochladen bestimmter MP4-Assets in den Status &quot;statisch&quot;wechseln, wodurch alle verbleibenden Workflows in den Status &quot;statisch&quot;wechseln (NPR-30662).

* Fehler wegen ungenügenden Speicherplatzes werden beobachtet, wenn große PDF-Dateien (mit mehreren Gigabytes) zu DAM hochgeladen und deren Teilassets verarbeitet werden (NPR-30614).

* Die Massenbewegung von Assets schlägt fehl und es wird eine Warnmeldung angezeigt (NPR-30610).

* Asset-Namen werden in Kleinbuchstaben geändert, wenn Assets von einem Ordner in einen anderen verschoben werden, der im [!DNL Dynamic Media]-Scene7-Modus ausgeführt wird (NPR-31630).[!DNL Experience Manager]

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler behoben, da sich das Bild im Ordner befindet, der dem Namen der Scene7-Firma entspricht (NPR-31340).

* [!DNL Dynamic Media] Assets, die Verweise enthalten, werden nicht veröffentlicht (NPR-31180).

* Uploads von [!DNL Dynamic Media]7-Scene7-Modus zu [!DNL Dynamic Media Classic] dauern zu lange, bis sie abgeschlossen sind (NPR-31048).

* Hotspot, der zu einem Bild-Asset hinzugefügt wurde, ist auf der Seite mit den Asset-Details nicht über den interaktiven Bild-Viewer sichtbar (NPR-30979).

* Große Sling-Aufträge werden erstellt und Verarbeitungsbanner werden erneut angezeigt, wenn Aktionen, die auf Assets in [!DNL Experience manager Assets] durchgeführt werden, an Scene7 übergeben werden (NPR-30947).

* Beim Erstellen der Sprachkopie von Assets treten Konflikte auf, und Assets werden nicht nach Scene7 hochgeladen (NPR-30932).

* Dynamische Darstellungen, die von [!DNL Experience Manager] heruntergeladen wurden und im [!DNL Dynamic Media]-Hybrid-Modus ausgeführt werden, sind beschädigt (sie sind vom Texttyp mit Inhalt &quot;Bild kann nicht gefunden werden&quot; anstelle des Bildinhaltstyps) (NPR-30876).

* [!DNL Dynamic Media] Der Arbeitsablauf zum Kodieren von Videos kann keine Miniaturansicht für das Video generieren, das unter Adobe Experience Manager vom  [!DNL Dynamic Media Classic] zum  [!DNL Dynamic Media]Scene7-Modus migriert wird (CQ-4282011).

* IpsApiException wurde beobachtet, während Assets mithilfe unterschiedlicher Scene7-Firmen-IDs von einer Instanz in eine andere migriert wurden (CQ-4280548).

* Die 3D-Asset-Miniaturansicht ist nicht informativ, wenn ein unterstütztes 3D-Modell in [!DNL Experience Manager] (CQ-4283701) eingeschlossen wird.

* Bildlaufschaltflächen werden im Viewer angezeigt, wenn ein 3D-Asset nur über wenige Ansichten verfügt (CQ-4283322).

* Falsche Höhe des Containers eines hochgeladenen 3D-Modells, das auf der Seite &quot;Asset-Details&quot;in der Vorschau in DimensionalViewer angezeigt wird (CQ-4283309).

* Videos können nicht mit SmartCropVideoViewer in Internet Explorer 11 und Safari wiedergegeben werden (CQ-4281422).

* Die Verwendung der Schaltfläche &quot;Verschieben&quot;zum Verschieben mehrerer Assets von einem Ordner in einen anderen schlägt fehl, wenn [!DNL Experience Manager] auf [!DNL Dynamic Media]-Scene7 runmode (CQ-4280384) ausgeführt wird.

* Verzerrtes Video wird in Asset-Details angezeigt, wenn der MIME-Typ nicht MP4 ist (CQ-4279704).

* Neuaufgenommene Videos in Ordnern mit Video-Profil bleiben auch nach Abschluss der Kodierung auf 100 % im Verarbeitungszustand (CQ-4279389).

* Durch das Verschieben von Assets aus einem Ordner wird eine große Anzahl von Sling-Aufträgen (Scene7 API-Aufrufe) erzeugt, die nicht unbedingt erforderlich sind (CQ-4278664).

* Die Namen des Bildsatzes werden in Scene7 in Kleinbuchstaben geändert, wenn in DAM (CQ-4281112) Bildsatz (oder Mediaset) erstellt und mit der entsprechenden Benennungskonvention benannt wird.

* Scene7 Migrator stellt den Veröffentlichungsstatus falsch ein (CQ-4263492).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers in Inhaltsfragmenten (CQ-4282898).

* PDF-Dateien werden nicht indiziert und der Inhalt in ist nicht durchsuchbar (CQ-4278916).

* Fehler &quot;Gruppe nicht nach Benutzerauswahl aufgeführt: &quot;false to equal true&quot;wird beim Hinzufügen von geschlossenen Benutzergruppen mit verschiedenen `principalName` und `authorizableId` (CQ-4278177) beobachtet.

* Die Ansicht &quot;Assets UI Column&quot;zeigt alle Pfade unabhängig vom Stammpfad des jeweiligen Mandanten an (CQ-4278175).

* Die Suche des Asset-Selektors funktioniert nicht wie erwartet (CQ-4275886).

* Die Workflows sind fehlgeschlagen (CQ-4271928).

* DAM Ereignis Purge löscht die neuesten (`maxSavedActivities`) Ereignis-Daten und speichert die zuvor erstellten Daten (NPR-31336).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Die Aktionsleiste und die Asset-Anzahl werden nicht aktualisiert, wenn Sie alle Elemente auswählen und dann die Auswahl einiger Elemente (Ordner/einzelne Assets) in der Touch-Benutzeroberfläche (NPR-31118) aufheben.

* Eine Ausnahme wird in [!DNL Experience Manager] angezeigt, wenn nach Auftragsdetails eines Assets gefragt wird (CQ-4283569).

### Sites

* Wenn die LiveCopy-Vererbung beschädigt ist, werden auf Live-Kopierseiten anstelle von LiveCopy-Links Sprachkopie-Links angezeigt (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).
* Wenn ein Benutzer japanische oder koreanische Zeichen in die Eigenschaft description eines Menüs einfügt, werden im Menü verzerrte Zeichen für japanischen und koreanischen Text angezeigt (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen (NPR-30879).
* Standardmäßig wird der RTE-Editor (RTE) mit Gerüsten versehen. wendet die Inline-Schriftgröße unerwartet auf Elemente an (NPR-31284).
* Wenn ein Benutzer den Fokus auf Felder in der linken Schiene legt und zum Einfügen von Inhalten einen Tastaturbefehl verwendet, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31172).
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Multifeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten (NPR-30882) gespeichert.
* Die `ResponsiveGridExporter`-API gibt die `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter`-Schnittstelle nicht zurück. Das `com.day.cq.wcm.foundation.model.impl`-Paket wird als privates Paket deklariert (NPR-31398).

<!-- Review: NPR-31398 has fixVersion as 6530. However, it is mentioned twice in 6530 and 6520 as fixed. 
Remove one mention of this fix.
-->

* Wenn eine Seite mit Erlebnisfragmenten im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das Präfix `editor.html` und `wcmmode=disabled` oder im Publisher)., endet die Anforderung im HTTP-Statusfehlercode `500` (NPR-30743).
* Benutzer können ihr Kennwort nicht ändern und nicht auf ihre Profil-Seite zugreifen (NPR-31161).

### Suchen und Benutzeroberfläche {#ui-interface-and-search}

* Wenn auf einer Suchergebnisseite von der Kartenseite zur Liste-Ansicht gewechselt wird, ist ein Bildlauf erst möglich (NPR-31286).

* Das Kontrollkästchen [!UICONTROL Alle auswählen] ist in der Ansicht &quot;Liste&quot;auf der [!DNL Sites]-Benutzeroberfläche (NPR-31614) ausgeblendet.

* Die Zählung für [!UICONTROL Alle auswählen] auf einer Suchergebnisseite ist nicht korrekt (NPR-31120).

* Der Metadaten-Editor zeigt Tags an, die nicht vorhanden sind (NPR-31119).

### Übersetzung {#translation}

* Bei Auswahl der Option &quot;Fälliges Datum&quot;in einem Übersetzungsauftrag (NPR-31270) werden zwei Kalender-Popups angezeigt.

### Plattform

* Die Option &quot;Mime-Typ&quot;in der Webkonsole funktioniert nicht (NPR-31108).

* Das Clientzertifikat wird beim Konfigurieren des Single Sign-On (NPR-31165) nicht akzeptiert.

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Service werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt in xpath-Abfragen (NPR-31322) die Bestellung von `fn:name()`.

* Duplikat Aktivierung Struktur wird erstellt, wenn ein Upgrade von [!DNL Experience Manager] 6.3 (NPR-31513) durchgeführt wird.

* Bei weitergeleiteten Anforderungen werden keine Antwortheader beibehalten, die während der Sling-Authentifizierung festgelegt werden (NPR-30013).

* Die Suche innerhalb der Picker-Komponenten funktioniert nicht (NPR-31692).

* Beim Anhängen einer ZIP-Datei an einen [!DNL Experience Manager Communities] Beitrag wird aufgrund verschiedener Versionen von Apache POI und Apache Tika Bundle (NPR-31018) ein Fehler angezeigt.

* Das `org.apache.sling.distribution.api`-Bundle ist im Configuration Manager ausgeblendet und steht daher nicht für benutzerdefinierte Bundles (NPR-31720) zur Verfügung.

### Projekte

* Das Wechseln von Kalendereinstellungen funktioniert nicht (NPR-31271).

### Markenportal {#assets-brand-portal-6530}

**Produktverbesserungen**

* Der Workflow zum Importieren von Assets in [!DNL Experience Manager Assets] wurde geändert, um nur die neu erstellten Assets von [!DNL Brand Portal] bis [!DNL Experience Manager] abzurufen und die bereits im NEUEN Ordner vorhandenen Assets zu überspringen, um eine Replikation zu vermeiden (CQ-4278527).

**Fehlerkorrekturen**

* Beim Erstellen eines neuen Beitragsordners in der Asset-Sourcing-Funktion (CQ-4282825) wird ein falsches Symbol angezeigt.
* Beim Erstellen eines neuen Beitragsordners werden ein oder beide Unterordner (NEU und FREIGEGEBEN) nicht im Beitragsordner (CQ-4282424) angezeigt.
* Das System gibt eine Ausnahme aus, wenn der Benutzer versucht, den Beitragsordner von [!DNL Experience Manager] bis [!DNL Brand Portal] erneut zu veröffentlichen, nachdem er neue Assets aus dem Beitragsordner von [!DNL Brand Portal] End (CQ-4279740) erhalten hat.
* Das Erstellen eines Beitragsordners in einem Beitragsordner (verschachtelter Ordner) ist verboten, um Komplexität zu vermeiden (CQ-4278391).
* Das System gibt beim Hochladen der [!DNL Brand Portal]-Liste (.csv-Datei), die aus der [!DNL Experience Manager]-Admin Console importiert wurde, eine Ausnahme aus. Nur die Felder &quot;E-Mail&quot;, &quot;Vorname&quot;und &quot;Nachname&quot;in der .csv-Datei sind obligatorisch (CQ-4278390).

### Communities {#communities-6530}

**Fehlerkorrekturen**

* Schnelllinks zum Verwalten von Gruppen (Gruppen öffnen/bearbeiten/Veröffentlichen/Löschen) sind für Community-Administratoren nicht sichtbar (Gruppenadministrator/Site-Administrator) (NPR-31627).
* Ein gesendeter Blog wird nur angezeigt, wenn die Seite manuell aktualisiert/neu geladen wird (NPR-31599).
* Bei der von der Funktion &quot;Erwähnungen&quot;verwendeten JCR-Abfrage wird zwischen Groß- und Kleinschreibung unterschieden. Die Rückgabe der Ergebnisse dauert zu lange (NPR-31475).
* [!DNL Experience Manager] 6.5 UberJar-Datei löst Ausnahme aus,  `cq-social-translation` Bundle fehlt in  [!DNL Experience Manager] 6.5 UberJar-Datei (NPR-31186).
* Jackson Databind-Bibliotheken wurden auf Version 2.9.9.3 aktualisiert, um neue Schwachstellen zu beheben (NPR-30967).
* Die Titel der Aktivitäten und Benachrichtigungen sind inkonsistent (NPR-30941).
* Paginierung funktioniert in [!DNL Communities] Blogs (NPR-30914) nicht ordnungsgemäß.
* Analytics-Berichte werden nicht in der Umgebung [!DNL Experience Manager] Autor gefüllt, es wird eine leere Seite angezeigt (NPR-30913).

### Oak {#oak}

* Aktualisierungen des Lucene-Indexes, die dazu führen, dass der Autorenserver langsamer wird (NPR-31548).

### Forms {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für  [!DNL Experience Manager Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [Experience Manager-Forms-Add-On installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) und [Experience Manager Forms on JEE installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

#### Forms-Add-on-Paket {#forms-add-on-package-6530}

**Adaptive Formulare**

* Zeichenfolgen enthalten den Wörterbuchschlüssel beim Lokalisieren von adaptiven Formularen (NPR-31110).

**Interaktive Kommunikation**

* **MissingNode.toString()** gibt nach der Aktualisierung von Jackson-Bibliotheken auf 2.10.0 (NPR-31549) falsche Ergebnisse zurück.

* Der Texteditor entfernt nach dem Zufallsprinzip Leerzeichen aus dem aus Microsoft Word kopierten Text (NPR-31113).

**Korrespondenzverwaltung**

* Beschriftungen und QuickInfos werden beim Migrieren von Briefen von LiveCycle ES4SP1 auf [!DNL Experience Manager] 6.5 (NPR-31615) nicht angezeigt.

* **Textflussformatierung wird beim Speichern von Briefen als Entwürfe nicht mehr** unterstützt (NPR-30463).

**Arbeitsablauf**

* OSGi-Arbeitsablauf schlägt aufgrund der 100%igen CPU-Auslastung (NPR-31233) fehl.

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30909).

#### Forms on JEE-Installationsprogramm {#forms-jee-installer-6530}

**Forms - Document Services**

* Der SOAP-Webdienst, der MTOM in einem .NET-Projekt verwendet, zeigt Ausnahmen für AssemblerServiceClient-Aufrufe und HtmlToPDF2-Methoden (NPR-4281771) an.

* Sicherheitslücke 2012-5784 und 2014-3596, die mit AXIS 1.4 jar behoben wurde, und Behebung mit [AXIS1.4.1 jar](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-5/jee-patch-0014.html) (NPR-31015).

**Foundation JEE**

* Die Aktionskonfiguration lädt die Prozessnamen für Übermittlungsaktion zum Aufrufen eines Forms Workflows nicht (NPR-31478).

### Enthaltene Feature Packs {#feature-packs-included-6530}

>[!NOTE]
>
>Für [!DNL Experience Manager Forms]-Kunden ist es wichtig, das [!DNL Experience Manager Forms] Add-On-Paket nach der Installation eines [!DNL Experience Manager] Service Packs, Cumulative Fix Pack oder Feature Pack zu installieren.

#### Forms – Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Forms-Unterstützung für Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0 {#experience-manager-6520}

[!DNL Adobe Experience Manager] 6.5.2.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit von  [!DNL Adobe Experience Manager] 6.5 im  **April 2019** veröffentlicht wurden. Es kann auf [!DNL Experience Manager] 6.5 installiert werden.

Einige der wichtigsten Highlights dieser Service Pack-Version sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.3 aktualisiert.
* Es wurde eine Konfigurationseigenschaft hinzugefügt, mit der Erlebnisfragmente direkt in benutzerdefinierte Arbeitsbereiche für [!DNL Adobe Target] exportiert werden können.
* Assets-Benutzer können nach visuell ähnlichen Bildern suchen. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Siehe [Verwenden von Connected Assets](../assets/use-assets-across-connected-assets-instances.md).

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten.
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt.
* Optimierte [!DNL Dynamic Media]-Performance durch Verwendung von standardmäßigen Asset-Filtern für die Replikation.
* Für den Dynamic Media Scene 7-Modus (DMS7) wurden die Optionen zum Zuschneiden/Drehen von Assets wiederhergestellt.
* Es wurde eine Option zum Stummschalten von Videos beim Laden in VideoPlayer implementiert.
* Fehlerkorrektur – In der Spaltenansicht der Asset-Benutzeroberfläche werden jetzt nur noch mandantenspezifische Inhalte angezeigt.
* Fehlerkorrektur – Änderungen des Stilakkordeons wirken sich jetzt auf die Suchergebnisse aus.

### Assets

**Produktverbesserungen**

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Hotfix für CQ-4270245. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Experience Manager Assets] Benutzer können visuell ähnliche Bilder suchen. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

**Fehlerkorrekturen**

* Von der ACP-API generierte Asset-Pfade in URL- und Ordner-Metadaten sind nicht URL-kodiert. GRANITE-26198: Hotfix für CQ-4271814
* Das Entzippen eines Archivs mit einem Ordner, der ein Prozentzeichen (%) in seinem Namen hat, kann nicht über die [!DNL Experience Manager Assets]-Schnittstelle geöffnet werden. NPR-29989: Hotfix für CQ-4270467
* Touch-Benutzeroberfläche: Im Assistenten zum Verwalten von Veröffentlichungen werden nach der Seite im Hauptteil der Beitragsanfrage Verweise hinzugefügt, wodurch alle Assets nach der Seite veröffentlicht werden. Wenn die Seite wiedergegeben wird, werden einige Assets in der Veröffentlichungsinstanz verpasst. NPR-29985: Hotfix für CQ-4270724
* Die Funktion zum Aufheben des Bezugs zwischen Assets funktioniert nicht, wenn der Name der entsprechenden Assets Sonderzeichen (URI-kodierte Zeichen) enthält. NPR-30387: Hotfix für CQ-4274446
* Beim Bearbeiten eines Inhaltsfragments wird dessen Version mit einer falschen Benutzerangabe erstellt.
* Fehler beim Erstellen von Sammlungen auf mandantenbasiertem System. NPR-30114: Hotfix für CQ-4272948
* Die Spaltenansicht der Assets-Benutzeroberfläche berücksichtigt nicht den Stammpfad des aktuellen Mandanten, sondern greift auf die DAM-Pfade aller Mandanten zu. NPR-30636: Hotfix für CQ-4275481
* Cross-Site-Scripting-Angriff (XSS) über das Fenster für die Warnmeldung zu eingeschränktem Dateizugriff möglich, da das injizierte Bild sichtbar ist. NPR-30617: Hotfix für CQ-4270133
* MultiTenant: Mandanten, die Ordnereigenschaften speichern, beachten sowohl die Erfolgsaufforderung als auch die Fehlermeldung, dass die Aktion nicht erfolgreich war: &quot;Eigenschaften können nicht bearbeitet werden. unzureichenden Berechtigungen nicht geändert werden konnten, was für Verwirrung sorgt. NPR-30545: Hotfix für CQ-4275333
* Im Asset-Auswahldialog lässt sich keine Asset auswählen und somit auch nicht die Funktion zum Ersetzen der zugehörigen Quelle verwenden, um die Quelle zu aktualisieren. NPR-30502: Hotfix für CQ-4275029
* [!UICONTROL DAM Update ] Asset Workflow - Im Status &quot;Statisch&quot;beim Hochladen von MP4-Dateien mit großer Größe. NPR-30480: Hotfix für CQ-4271352
* Die Funktion zum Erstellen von Prüfungsaufgaben schlägt aufgrund nicht vorhandener Nutzdaten fehl, was entsprechend auch alle nachfolgenden Aktionen im Zusammenhang mit Prüfungsaufgaben fehlschlagen lässt. NPR-30468: Hotfix für CQ-4274263
* Problem bei der Verbindung mit Adobe Smart-Tag über DataPower. NPR-30026: Hotfix für CQ-4269457
* Die Spaltenansicht der Assets-Benutzeroberfläche löst einen Fehler aus, wenn versucht wird, die Filter links von der Leiste zu öffnen. NPR-30501: Hotfix für CQ-4273862
* Wenn Gruppen hinzugefügt werden, die über LDAP in den Eigenschaften der geschlossenen Benutzergruppe eines Asset-Ordners synchronisiert wurden, wird die Gruppe nicht gespeichert und abgerufen. NPR-30615: Hotfix für CQ-4274689
* In den Feldern zum Filtern der Suche nach Stil und Ausrichtung wird der automatisch vervollständigte Wert nicht auf die Suchanfrage angewendet. NPR-30620: Hotfix für CQ-4275724
* Enthält der Name eines Ordners Leerzeichen und das Zeichen „&amp;“, zeigt der ihm zugehörige Asset-Freigabe-Link bei einigen Assets leere graue Karten an. NPR-30557: Hotfix für CQ-4270187
* Das Metadatenschemaformular für Ordner erkennt den Datentyp nicht automatisch, was zur Folge hat, dass es bei der Formularübermittlung den zugehörigen TypeHint nicht erstellt. NPR-30599: Hotfix für CQ-4275227
* In der Autoren-Benutzeroberfläche für DMS7 sind die Optionen zum Zuschneiden und Drehen von Assets deaktiviert. NPR-30118: Hotfix für CQ-4273221
* Die Funktion &quot;Link freigeben&quot;funktioniert nicht bei [!DNL Experience Manager]-Instanz mit DMS7-Konfiguration. NPR-30080, NPR-30492: Hotfix für CQ-4273651
* Durch Hinzufügen der Komponente [!DNL Dynamic Media]-Scene7 zur Seite und anschließendes Veröffentlichen der Seite wird die dmscene7-Konfiguration nicht jedes Mal Trigger. NPR-30641: Hotfix für CQ-4275962
* Es wurde ein IPSJobJournal in [!DNL Experience Manager] hinzugefügt, um pro verarbeitetem Profil nur einen IPS-Auftrag (Intrusion Prevention Systems) zu erstellen. NPR-30490: Hotfix für CQ-4273614
* [!DNL Dynamic Media]: Es wurden Standard-Filter hinzugefügt, um Assets von der Replizierung auf den  [!DNL Experience Manager] Veröffentlichungsknoten auszuschließen. NPR-30538: Hotfix für CQ-4274678
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt, der die Nutzung von Ordnern als Nutzlast ermöglicht. Der Workflow umfasst zwei Schritte: Die erneute Verarbeitung von Assets ohne Handles erfolgt über die Zuordnung von Metadaten zum nächsten Schritt, das erneute Hochladen aller Assets ohne Asset-Handle zu S7 dann in einem einzelnen IPS-Auftrag. Weitere Informationen finden Sie unter [!DNL Dynamic Media]-Cloud Services konfigurieren. NPR-30489: Hotfix für CQ-4272903
* Wird nach der korrekten CSV-Datei eine falsche CSV-Datei hochgeladen, wird die korrekte CSV-Datei gelöscht. Hotfix für CQ-4277694, CQ-4277814
* Falsches Symbol für die zu entfernenden Beitragsordner. Hotfix für CQ-4277580
* Wird über die Benutzerauswahl auf der Registerkarte für Asset-Beiträge ein Benutzer ausgewählt, erscheint dessen Name nicht in der Tabelle, und auf der Eigenschaftenseite wird im Dialogfeld zum Löschen von Benutzern falscher Text angezeigt. Hotfix für CQ-4277875
* Mitwirkende können dem Asset-Beitragsordner nicht hinzugefügt werden, indem diese über die Benutzerauswahl ausgewählt werden und auf die Schaltfläche „Hinzufügen“ geklickt wird. Hotfix für CQ-4277824, CQ-4278087
* In der Benutzerauswahl funktioniert die Suche nach Benutzernamen in Kleinbuchstaben nicht. Hotfix für CQ-4277958, CQ-4277930
* Benutzer ohne Administratorrechte können Assets in einem neuen Ordner eines Asset-Beitragsordners veröffentlichen. Hotfix für CQ-4278200
* Für DAM-Benutzer (ohne Administratorrechte) besteht keine Möglichkeit, dem Asset-Beitragsordner Mitwirkende hinzuzufügen. Hotfix für CQ-4278192
* Im Asset-Beitragsordner ist die Schaltfläche „Erstellen“ sichtbar. Hotfix für CQ-4277560
* Beim Sortieren der Abfrage nach Relevanz werden [!DNL InDesign]-Dokumente zusammen mit [!DNL InDesign]-Vorlagen zurückgegeben. Hotfix für CQ-4273864
* Wenn der Benutzer über eine E-Mail-ID in Großbuchstaben verfügt, können die Benutzer nicht für die zuvor ausgecheckten Assets einchecken. Hotfix für CQ-4276575
* Der Löschvorgang gilt nur für die ausgewählten Vorgaben. Wenn der Bildschirm die Liste nach dem Vorgang automatisch aktualisiert, werden andere Vorgaben angezeigt, die bereits aktualisiert wurden. Hotfix für CQ-4261461
* Wenn Sie [!DNL Dynamic Media]-Cloud Services im [!DNL Dynamic Media]-Hybrid-Modus konfigurieren, werden mehrere leere Report Suites erstellt, die in [!DNL Analytics] erstellt wurden, ohne dass die Report Suite-ID in [!DNL Experience Manager] gespeichert ist, was zu einer Duplizierung der Report Suite führt. Hotfix für CQ-4249780
* Der Vorgang zum Umbenennen in Element [!DNL Experience Manager] kann nicht mit Scene7 synchronisiert werden. Hotfix für CQ-4276763
* Im Suchfilterbedienfeld werden nutzergenerierte Inhalte falsch angezeigt. Hotfix für CQ-4273875
* Die Option „Ähnliche suchen“ ist für TIFF-Bilder nicht verfügbar. Hotfix für CQ-4278238
* Es wurde eine Option zum Stummschalten eines Videos beim Laden in VideoPlayer implementiert. Hotfix für CQ-4266465
* Viewer - VideoViewer: poster=none funktioniert nicht korrekt, wenn ein externes Video verwendet wird. Hotfix für CQ-4265536
* Bei der Wiedergabe von Videos in IE11- und MS Edge-Browsern wird das Warten-Symbol angezeigt. Hotfix für CQ-4251539
* 3.8 SDK- und 5.13-Viewer-README-Dateien werden nicht aktualisiert und enthalten Informationen aus früheren Versionen. Hotfix für CQ-4273737
* Inhaltsfragment wird vor dem Speichern der Änderungen versioniert. NPR-30616: Hotfix für CQ-4273088
* Asset#getMetadata(String) muss durch Asset#getMetadataValueFromJcr(String) im Miniatur-Prozess ersetzt werden. NPR-30491: Hotfix für CQ-4273067
* Das Hochladen von JPG verursacht mehrere Instanzen der Meldung „ReplicateOnModifyWorker Replicating UPDATED“ für jedes Asset, wodurch die Leistung beeinträchtigt wird.
* Das Entpacken von ZIP-Archiven mithilfe der Funktion „Archiv extrahieren“ verursacht Probleme mit Ordnern, deren Name ein Prozentzeichen (%) im Titel enthält. NPR-29990: Hotfix für CQ-4270467

### Sites {#sites-6520}

* Wenn die LiveCopy-Vererbung beschädigt ist, werden auf Live-Kopierseiten anstelle von LiveCopy-Links Sprachkopie-Links angezeigt (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).
* Rich Text Editor (RTE)-Plug-In der Textkomponente zeigt verzerrte Zeichen für japanischen und koreanischen Text an (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen (NPR-30879).
* Rich Text Editor (RTE) wird standardmäßig als Inline-Schriftgröße auf Elemente angewendet, unerwartet (NPR-31284).
* Wenn sich ein Benutzer auf linke Schienenfelder konzentriert und zum Einfügen von Inhalten Tastaturbefehle verwendet, werden Inhalte der Zwischenablage des Seiteneditors anstatt des Inhalts eingefügt, der aus den Feldern der linken Leiste kopiert wurde (NPR-31172).
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Multifeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten (NPR-30882) gespeichert.
* Die `ResponsiveGridExporter`-API gibt die `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter`-Schnittstelle nicht zurück. Das `com.day.cq.wcm.foundation.model.impl`-Paket wird als privates Paket deklariert (NPR-31398).
* Wenn eine Seite mit Erlebnisfragmenten im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das Präfix `editor.html` und `wcmmode=disabled` oder im Publisher), endet die Anforderung mit dem HTTP-Statusfehlercode 500 (NPR-30743).

### WCM – Seiteneditor {#wcm-page-editor-6520}

**Produktverbesserungen**

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten. Hotfix für CQ-4270694

### Verwaltung von Inhaltsfragmenten {#content-fragment-management-6520}

* Die von der Benutzeroberfläche der Inhaltsfragmentmodelle verwendete Abfrage ist sehr langsam und führt schließlich zu einem Fehler. Hotfix für CQ-4270807

### Benutzeroberfläche – Foundation {#ui-foundation}

* Es werden Tastenkombinationen ausgelöst, was den Benutzer daran hindert, in bestimmten Benutzeroberflächen „m“, „p“ und „e“ zu verwenden. NPR-30355: Hotfix für GRANITE-26346
* Durch Schließen der Benutzeroberfläche [!DNL Experience Manager Assets] &quot;Suchen&quot;wird die linke Leiste nicht auf Inhaltsauswahl zurückgesetzt, sodass der Benutzer die Filterleiste anschließend ein zweites Mal öffnen kann. NPR-30509: Hotfix für CQ-4274716
* Umgebung mehrerer Mandanten: [!DNL Experience Manager Assets] UI-Top-Navigation ist nicht verfügbar und gibt einen JavaScript-Fehler aus. NPR-30104: Hotfix für GRANITE-26344

### Übersetzung {#translation-6520}

* Übersetzungsprobleme behoben – Maschinelle Übersetzung kommt nur noch für wenige Komponenten zum Einsatz. NPR-30079: Hotfix für CQ-4273764

### Plattform {#platform-6520}

* [!DNL Experience Manager]Der für standardmäßig verwendete E-Mail-Absender kann über TLS 1.2 keine E-Mails an einen Remote-SMTP-Server senden. NPR-30476: Hotfix für GRANITE-26605

### Projekte {#projects-6520}

* Die ThumbnailPath-Werte eines DAM-Ordners werden nicht aktualisiert und zeigen auch nach dem Löschen der Assets im Ordner noch die alten Miniaturansichten an. NPR-30424: Hotfix für CQ-4273667
* Nach Abschluss der Option „Verschieben“ bleiben Titel und Name des Assets unverändert. NPR-30647: Hotfix für CQ-4276265

### Communities {#communities-6520}

* Die Diagnose für die Benutzersynchronisierung ist fehlgeschlagen und funktioniert nicht. NPR-30004, NPR-29943: Hotfix für CQ-4270287, CQ-4271348

### Sling {#sling}

* Eine Aktualisierung der Instanz von 6.3.3.2 auf 6.5 führt zu doppelten OSGi-Konfigurationen. NPR-30130: Hotfix für CQ-4274016

### Integration

* Angepasster Content wird auf der Veröffentlichungsinstanz erst nach dem Neustart der Instanz korrekt angezeigt. NPR-30377: Hotfix für CQ-4273706
* Bei der Konfiguration von Launch auf einer Website wird der Bibliotheksadresse ein Schrägstrich (/) vorangestellt, der jedes Mal einen manuellen Eingriff verursacht. NPR-30694: Hotfix für CQ-4275501

### Forms {#forms-6520}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für  [!DNL Experience Manager Forms]. Sie werden mithilfe eines separaten [!DNL Forms] Add-On-Pakets bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [Experience Manager-Forms-Add-On installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) und [Experience Manager Forms on JEE installieren](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

Die wichtigsten Highlights für 6.5.2.0-Formulare sind:[!DNL Experience Manager]

* Einstellung &quot;Auto&quot;zu `RenderAtClient` in der API für `PDFFormRenderOptions` Forms OSGi hinzugefügt.[!DNL Experience Manager]

#### Forms-Add-on-Paket

**Back-End-Integration**

* Das Formulardatenmodell kann nicht mit einer von AWS gehosteten URL für den Lastenausgleich konfiguriert werden. NPR-30123: Hotfix für CQ-4273359
* Beim Erstellen des Formulardatenmodells (FDM) mit der Web Service Definition Language (WSDL) wird die Fehlermeldung `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` zurückgegeben: NPR-30477: Hotfix für CQ-4272921

**Korrespondenzverwaltung**

* &quot;Die Darstellung der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) schlägt gelegentlich fehl und in der Konsole wird der folgende Fehler angezeigt:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interaktive Kommunikation**

* Ein im Formulardatenmodell als erforderlich markiertes Feld wird wie in der Benutzeroberfläche „Korrespondenz erstellen“ (CCR-Benutzeroberfläche) als erforderlich angezeigt. NPR-30623: Hotfix für CQ-4274902

**Forms – Workflow**

* Nicht zugeordnete Ausgabevariablen in überwachten Ordnern führen dazu, dass der Aufruf fehlschlägt. Hotfix für CQ-4264451

**HTML5-Formulare**

* Wird ein benutzerspezifisches Code- oder Projekt-Element zum zweiten Mal bereitgestellt, wird die Seite nicht gerendert und der folgende Fehler tritt auf:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix für CQ-4272509

* Wird im Durchsuchen-Modus „NonVisual Desktop Access“ zum Lesen eines HTML5-Formulars verwendet, liest der Chrome-Browser vor jeder skalierbaren Vektorgrafik (SVG) im Formularentwurf das Wort „Grafik“. NPR-30449: Hotfix für CQ-4274732

#### Forms JEE-Installationsprogramm

**Forms - Document Security**

* Das Anwenden einer Unterschrift mit Zeitstempel schlägt mit folgender Meldung fehl: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Aufruffehler. NPR-30820: Hotfix für CQ-4275852

**Forms - Dokument Services**

* Wenn die „SubmitURL“ ein kaufmännisches Und (&amp;) enthält, werden im Protokoll Parsing-Fehler angezeigt, wenn eine POST-Anfrage an das renderpdf-Servlet gesendet wird. NPR-30865: Hotfix für CQ-4278232

**Forms – Foundation JEE**

* Der HTMLtoPDF-Dienst zeigt in der JMX-Konsole nicht maxReuseCount an. NPR-30134, NPR-30304: Hotfix für CQ-4273763
* Beim Hinzufügen oder Bearbeiten einer Webdienst-Verbindung durch Aufrufen von Webdiensten von [!DNL Experience Manager Forms] Workbench wird ein Fehler ausgegeben: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix für CQ-4273217

### Enthaltene Feature Packs

>[!NOTE]
>
>Für [!DNL Experience Manager Forms]-Kunden ist es wichtig, das [!DNL Experience Manager Forms] Add-On-Paket nach der Installation eines [!DNL Experience Manager] Service Packs, Cumulative Fix Pack oder Feature Pack zu installieren.

#### Sites {#sites-feature-packs-included}

* Es wurde eine Konfigurationseigenschaft hinzugefügt, mit der Erlebnisfragmente direkt in benutzerdefinierte Arbeitsbereiche für [!DNL Adobe Target] exportiert werden können. NPR-29189: Hotfix für CQ-4249782

#### Forms - Document Services {#forms-document-services-1}

* Einstellung &quot;Auto&quot;zu `RenderAtClient` in `PDFFormRenderOptions` API für [!DNL Experience Manager Forms] OSGi hinzugefügt. NPR-30759: Hotfix für CQ-4278193

## Adobe Experience Manager 6.5.1.0 {#experience-manager-6510}

[!DNL Adobe Experience Manager] 6.5.1.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit von  [!DNL Adobe Experience Manager] 6.5 im  *April 2019 veröffentlicht wurden.*[!DNL Experience Manager] Sie kann auf  6.5 installiert werden.

Einige der wichtigsten Highlights dieser Service Pack-Version sind:

* Dynamische Benutzeroberflächenstatus können jetzt als benutzerdefinierte Attribute in Tracking-Ereignisse einbezogen werden.
* Unterstützung für den Versand von 360-Grad-Video-Assets im [!DNL Dynamic Media]-Scene7-Modus.
* Funktion *Japanischer Wortumbruch* über das Stilplugin des Rich Text Editor aktiviert. Weitere Informationen finden Sie unter [Konfigurieren von japanischen Wortumbrüchen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Assets

* Die DAM DMGateway-Schnittstelle bietet jetzt Unterstützung für S3 Multipart. NPR-29740: Hotfix für CQ-4226303
* Die Vorschau &quot;Ausgabeformate&quot;erzeugt nach der Aktualisierung auf [!DNL Experience Manager] 6.5 den Fehler `Only empty tenantId is currently supported`. NPR-29986: Hotfix für CQ-4272353
* Da das Dialogfeld „Löschen“ nicht sichtbar ist, können Aufträge nicht gelöscht werden. NPR-29720: Hotfix für CQ-4271074
* Wenn ein Benutzer versucht, die Seite nach dem Hinzufügen des Asset-Titels auf der Eigenschaftenseite zu schließen, wird [!DNL Experience Manager] erneut geöffnet. NPR-29627: Hotfix für CQ-4264929
* VersioningTimelineEventProvider sollte die Stammversion zusammen mit dem Knoten des Typs „nt: version“ bereitstellen. Hotfix für GRANITE-26063
* Es wurde die Möglichkeit zum Hochladen und Abspielen von 360 kugelförmigen Videos im DM-Scene7-Modus implementiert. [!DNL Experience Manager] Hotfix für CQ-4265131
* Wird bei einer Live Copy die Quelle bearbeitet, wird der falsche Status abgerufen. Hotfix für CQ-4265451
* Multi-Site-Manager bietet jetzt Unterstützung für [!DNL Experience Manager Assets]. Hotfix für CQ-4271453, CQ-4268621, CQ-4257491
* [!DNL Experience Manager] -Schnittstelle sollte einen zusätzlichen Eintrag für die aktuelle Version des Assets im Zeitschienenverlauf anzeigen, in dem der neueste Eincheckkommentar angezeigt wird  [!DNL Adobe Asset Link]. Hotfix für CQ-4262864
* In der Zeitleiste des Inhaltsfragments wird eine Fehlermeldung angezeigt, wenn Eigenschaften fehlen. Hotfix für CQ-4272560
* Problem mit dem Scene7-Videoplayer, wenn er auf den Vollbildmodus erweitert wird. Hotfix für CQ-4266700
* Viewer für vertikalen Zoom: Die Schwenken-Schaltflächen sollten nicht angezeigt werden, wenn ein einzelnes Bild-Asset verwendet wird. Hotfix für CQ-4264795
* Durch das Löschen eines untergeordneten Knotens in einer Live Copy sollte die LiveRelationship getrennt werden. Hotfix für CQ-4270395
* Das Metadatenschema enthält nur Elemente aus der globalen Konfiguration und nicht die Elemente aus dem aktiven Mandanten. Selbst wenn der für „formPath“ angegebene URL-Wert geändert wird, wird er auf den Standardwert zurückgesetzt. NPR-29945: Hotfix für CQ-4262898
* Veröffentlichen von Bildvorgaben auf [!DNL Brand Portal] schlägt mit 500-Fehlercode fehl. NPR-29510: Hotfix für CQ-4268659

### Sites

* Beim Rollout werden leere Eigenschaften ebenso wie mehrere Eigenschaften von der Blueprint nicht übernommen. Das Zurücksetzen der Live Copy auf den Status der Blueprint funktioniert nicht für Komponenten. NPR-29253: Hotfix für CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI speichert bei Verwendung von `Multifield` das `fileReferenceParameter` auf Komponentenebene statt auf Multifield-Ebene. NPR-29537: Hotfix für CQ-4266129
* Verbesserung der Textkomponente und des Texteditors auf Japanisch. [!DNL Experience Manager] NPR-29785: Hotfix für CQ-4265090
* Eine mithilfe von Timewarp wiederhergestellte Seite sollte zum Zeitpunkt der Versionierung auf das korrekte Bild verweisen. NPR-29431: Hotfix für CQ-4262638
* Ein Problem mit der Vererbung von Style System-Knoten von übergeordneter zu untergeordneter Ebene. NPR-29516: Hotfix für CQ-4270330
* Eine Fehlermeldung beim Einrichten der Social-Veröffentlichung für die [!DNL Facebook]-Authentifizierung. NPR-29211: Hotfix für CQ-4266630
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* In der Coral2-Implementierung werden beim Öffnen der Registerkarte „Berechtigungen“ die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

### Commerce

* Das Ausführen einer Lazy-Content-Migration für E-Commerce löst eine ConstraintViolationException aus. NPR-29247: Hotfix für CQ-4264383

### Verwaltung von Inhaltsfragmenten

* Parsing-Fehler beim Öffnen eines Inhaltsfragments, das die Zeichen Dollarzeichen `($)` und eine offene Klammer `({)` enthält. Hotfix für CQ-4270266

### Experience Fragments

* Exportieren Sie die Erlebnisfragmente nach [!DNL Adobe Target]. [!DNL Experience Manager] Hotfix für CQ-4265469
* Der Export von Erlebnisfragmenten in die Zielgruppe schlägt mit dem intelligenten Bild fehl. Hotfix für CQ-4269606

* Der Versuch, mithilfe von Omnisearch Experience Fragments in der Kartenansicht zu verschieben, führt nicht ans Ziel. Hotfix für CQ-4263848

### WCM – Seiteneditor

* Reflektiertes Cross-Site-Scripting (XSS) bei Verwendung einer ungültigen Auswahl. Hotfix für CQ-4270397

### Replikation

* Vom Benutzer bereitgestellte Daten werden bei der Ausgabe in der Komponente `cq/replication/components/agent` nicht ausgegeben, was zu einer gespeicherten Cross-Site-Scripting- (XSS)-Schwachstelle führt. Hotfix für CQ-4266263

### Workflow

* Das Kalenderauswahlfeld des Dialogteilnehmers ist defekt. NPR-29727: Hotfix für CQ-4270423

### WCM – SPA-Editor

* Vorab gerenderte Inhalte können jetzt von einem Remote-Endpunkt abgerufen werden. Hotfix für CQ-4270238
* Warnungen in Protokollen beim Öffnen einer serverseitig gerenderten Seite mit SPA-Vorlage. Hotfix für CQ-4270238

### WCM - MSM

* Durch ein Upgrade auf [!DNL Experience Manager] 6.4.3 wird die Einführung des Multi-Site-Managers sehr lange dauern. Hotfix für CQ-4271410

### Integration

* Anmeldeversuche mit den BrightEdge-Anmeldeinformationen schlagen mit einem Verbindungsfehler fehl. NPR-29168: Hotfix für CQ-4265872

* Beim Versuch, die Startkonfiguration zu bearbeiten und zu speichern, wird eine Ausnahmemeldung angezeigt. [!DNL Experience Manager] NPR-29176: Hotfix für CQ-4265782/CQ-4266153

### Benutzeroberfläche

* Es wurde Unterstützung für das Tracking der dynamischen Benutzeroberflächenstatus als benutzerdefinierte Attribute beim Tracking bestimmter Ereignisse ergänzt. Hotfix für GRANITE-26283
* Für die Senden-Schaltfläche kann die Tracking-Funktion nicht festgelegt werden. Hotfix für GRANITE-26326
* Der Assistent kann die Tracking-Funktion nicht für die Senden-Schaltfläche festlegen. NPR-29995, NPR-30025: Hotfix für CQ-4264289

### Communities

* Auf der Seite für Mitgliederprofile können neue Kennzeichen nicht über die Dropdown-Liste ausgerichtet werden. NPR-29381: Hotfix für CQ-4267987
* Besucher und Mitglieder ohne Moderatorberechtigungen können nicht genehmigte/ausstehende Beiträge anzeigen, indem sie die entsprechende URL einfügen. NPR-29724: Hotfix für CQ-4271124, CQ-4271441
* Bei der Community-Benutzeranmeldung kommt es zu langsamen Reaktionszeiten von mitunter 40–50 Sekunden. NPR-29677: Hotfix für CQ-4269444

### Replikation

* Die Komponente „Replikationsagent“ ist anfällig für eine Sicherheitslücke, die nicht autorisierten Benutzern vertrauliche Informationen offenlegt. NPR-29611: Hotfix für GRANITE-25070

* Siztungsleck bei OAuth-Authentifizierung für jede Replikation in [!DNL Brand Portal]. NPR-30001: Hotfix für GRANITE-26196

### Projekte

* Veröffentlichen von [!DNL Experience Manager Assets] aus dem Ordner [!DNL Experience Manager] &quot;Autor /content/dam/mac&quot;in [!DNL Brand Portal] funktioniert nicht. NPR-29819: Hotfix für CQ-4271118

### Plattform

* HTMLLibraryManager löscht bei der Cache-Invalidierung alle Inhalte von crx-quickstart. NPR-29863: Hotfix für GRANITE-26197

### Felix

* Bei Verwendung von Java11 werden in der Systemkonsole keine Details zur Speichernutzung angezeigt\. NPR-29669

### Formulare

Die wichtigsten Highlights für [!DNL Experience Manager Forms] 6.5.1.0 sind:

* Nur OSGi: Es wurde ein neues Attribut `PAGECOUNT` in Output und Forms Service hinzugefügt.

* Nur OSGI: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert.
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert.
* Es wurde Unterstützung für die On-Premise-Integration von ADFS 3.0 für Dynamics ergänzt.

#### Forms-Add-on-Paket

**Backend-Integration**

* Fehler beim Abrufen von geschützter WSDL (Web Service Definition Language). NPR-29944: Hotfix für CQ-4270777
* Wenn [!DNL Experience Manager Forms] auf IBM WebSphere installiert ist, schlägt das Erstellen eines auf SOAP basierenden Formulardatenmodells fehl. Hotfix für CQ-4251134
* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. Hotfix für CQ-4270586
* Wenn der Titel einer Datenquelle geändert wird, zeigt das Formulardatenmodell den aktualisierten Titel nicht an. Hotfix für CQ-4265599
* Wenn der Name einer Entität oder eines Attributs Bindestriche oder Leerzeichen enthält, können Ausdruck diese Entitäten und Attribute nicht auswerten. Hotfix für CQ-4225129

* Falsche Ausgabe wird beobachtet, wenn ein Doppelpunkt in der Ausgabe der Primitive-Zeichenfolge vorhanden ist. Hotfix für CQ-4260825

* Auch wenn von der REST-API-Ausgabe kein Inhalt erwartet wird, löst der Aufrufvorgang des Formulardatenmodells einen Fehler aus. Hotfix für CQ-4268828

**Adaptive Formulare**

* Während des Lazy-Loading-Vorgangs kann im adaptiven Formularfragment keine neue Instanz hinzugefügt werden. NPR-29818: Hotfix für CQ-4269875
* Bei Vorlagen für Datensatzdokumente (Document of Record, DoR) protokolliert die Überprüfungskomponente keinerlei Fehler, noch zeigt sie Fehler an. Hotfix für CQ-4272999
* Unterstützung zum Deaktivieren des Layout-Editors für adaptive Formulare hinzugefügt. Hotfix für CQ-4270810
* Überprüfungsschritt für Adaptives Forms in [!DNL Experience Manager] 6.5 wiederhergestellt. Hotfix für CQ-4269583

* Fehler bei der Feldüberprüfung für adaptive Formulare: [!DNL Adobe Sign] Hotfix für CQ-4269463
* Wenn eine [!DNL Experience Manager Forms]-Instanz mehr als 20 adaptive Formularfragmente und den Namen aller Formularfragmente mit derselben Zeichenfolge enthält, gibt die Suche keine oder nur die zuletzt erstellten 20 Fragmente zurück. Hotfix für CQ-4264414, CQ-4264914

* Bei Verwendung eines großen Datensatzes in der App für adaptive Formulare treten Performance-Probleme auf. . Hotfix für CQ-4235310

* Wird über ein anonymes Konto auf eine Veröffentlichungsinstanz zugegriffen, schlägt das GuideRuntime-Skript fehl. Hotfix für CQ-4268679

**Forms – Interaktive Kommunikation**

* Die Vorlage für interaktive Kommunikation führt in der Liste der zulässigen Komponenten keine Kopf- und Fußzeilenkomponenten auf. Hotfix für CQ-4237895
* Wird eine Druckvorlage für interaktive Kommunikation erstellt, die ein Bildfeld enthält, wird für den Titel des Diagramms „leer“ festgelegt. Hotfix für CQ-4264772
* Für die Linienfarbe eines Diagramms wird beim Löschen „nicht definiert“ festgelegt. Hotfix für CQ-4264762
* Änderungen an der Layoutebene, die am Dokument-Fragment vorgenommen wurden, werden bei der Synchronisierung der Änderungen nicht mehr angezeigt. Hotfix für CQ-4266054
* Ein innerhalb eines Dokumentfragments an ein Textfeld gebundenes Formulardatenmodellelement zeigt kein Vererbungssymbol an, und es kann verknüpft werden. Hotfix für CQ-4261089
* Die API zum Rendern von Druckkanälen verfügt nicht über die Option zum Übergeben von Daten als Parameter in der API. Hotfix für CQ-4263540
* Agent-Einstellungen sind nicht sichtbar, da das Kontrollkästchen Bearbeitbar nach Agent deaktiviert wird, wenn der Bindungstyp von Textfragment in Keine/Datenmodellobjekt für das String-Feld/die String-Variable geändert wird. Hotfix für CQ-4261953
* Bei der Übermittlung der Agent-Benutzeroberfläche speichert die resultierende Web-Daten-JSON-Datei Informationen zu vererbungsabgebrochenen ungebundenen Feldern. Hotfix für CQ-4265621

**Forms – Workflow**

* Wenn ein Formular erneut aus dem Postausgang der App für adaptive Formulare gesendet wird, führt dies zu Datenverlust. NPR-28345: Hotfix für CQ-4260929
* In Fällen, in denen keine Variablen verwendet werden, werden Dokumente beim Speichern nicht geschlossen. Hotfix für CQ-4269784
* Die App für adaptive Formulare unterstützt Microsoft Windows 8.1 nicht mehr. Hotfix für CQ-4265274
* Wenn ein Bild mit mehr als 2 MB als Anlage auf Feldebene an ein Formular in der Android-Version der [!DNL Experience Manager Forms]-App angehängt wird, stürzt die App ab. Hotfix für CQ-4265578

* In der Zuweisungsaufgabe für den Druckkanal der interaktiven Kommunikation stehen jetzt Optionen zum automatischen Ausfüllen zur Verfügung. Hotfix für CQ-4265577
* Benutzer können eine freigegebene Aufgabe erst dann anzeigen, wenn sie Mitglied der Gruppe werden, der die Aufgabe zugewiesen ist. Hotfix für CQ-4248733
* Das Speichern oder Senden von JEE-Anwendungen in der App für adaptive Formulare ist unter Windows blockiert. Hotfix für CQ-4268704
* Das der Formulardatenmodellvariablen zugeordnete Formulardatenmodell ist nicht sichtbar. Hotfix für CQ-4266554
* Beim Unterzeichnen von Dokumenten mit Variablenunterstützung wird die Statusvariable nicht unterstützt. Hotfix für CQ-4266312
* Übermittlungen, die Umlaute enthalten, schlagen mit Workspace fehl. Hotfix für CQ-4263172
* In einer Umgebung, auf die ein Upgrade vorgenommen wurde, wird beim Öffnen eines Workflows zur Bearbeitung in der Benutzeroberfläche für Überwachungsordner anstelle des Workflow-Namens ein Fehler angezeigt. Hotfix für CQ-4238579

**Forms – Verwaltung**

* Wenn eine andere Erweiterung als „xsd“ oder „schema.json“ hochgeladen wird, erfolgt der Upload nicht und es wird keine Fehlermeldung ausgegeben. Hotfix für CQ-4266716

**Forms – Correspondence Management**

* [!DNL Experience Manager Forms] 6.5 Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) kann Korrespondenz, die mit  [!DNL Experience Manager Forms] 6.3 erstellt wurde, nicht öffnen. Hotfix für CQ-4266392
* Die Summenfunktion in XDP funktioniert nicht, wenn die Datenwörterbuchelemente Daten vom Typ „Zahl“ enthalten. Hotfix für CQ-4227403
* Die Invalidierungslogik des Arbeitsspeichercaches für Briefe muss aktualisiert werden, da beim Veröffentlichen eines Assets die Zeit seiner letzten Änderung nicht aktualisiert wird. Hotfix für CQ-4250465
* Dokumentfragment, Datenwörterbuch und Briefe können nicht veröffentlicht werden. Hotfix für CQ-4272893

#### Forms JEE-Installationsprogramm

**PDF Generator**

* Die Konvertierung von CAD- in PDF-Dateien schlägt mit dem 64-Bit-JDK fehl. NPR-29924, NPR-29925: Hotfix für CQ-4272113
* Die Bezeichnung „HTML-in-PDF“ für die entsprechende Konvertierung mit PhantomJS wurde durch „Web-in-PDF“ ersetzt. NPR-29933: Hotfix für CQ-4234545
* Beim Konvertieren einer ZIP- in eine PDF-Datei wird ein Fehler ausgegeben. Hotfix für CQ-4268628

**Forms – Designer**

* Wenn eine vollständige Barrierefreiheitsprüfung für die statische PDF-Datei durchgeführt wird, die mit [!DNL Experience Manager Forms Designer] erstellt wurde, schlägt die Primär Language-Prüfung fehl, da das Sprachattribut fehlt. Hotfix für CQ-4272923, CQ-4271002

**Forms - Sicherheit von Dokumenten**

* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten OSGi-Installationen nicht mit Java 11 und Java 8\. NPR-29838: Hotfix für CQ-4270441
* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten JEE-Installationen sowie allen unterstützten Anwendungsservern, d. h. JBoss und Websphere, nicht. NPR-29839: Hotfix für CQ-4266721
* Beim Überprüfen der Signaturen in einer PDF-Datei mit PAdES (PDF Advanced Electronic Signatures) wird eine InvalidOperationException generiert. NPR-29842: Hotfix für CQ-4244837
* Unterstützung für Dokument Security Extension für Office 2019\ hinzugefügt. Hotfix für CQ-4254369, CQ-4259764

**Forms - Dokument Services**

* PDF-Konvertierung in PDF/A-1b mit Formularfeld hat kein Erscheinungsbild-Diktat. NPR-29940: Hotfix für CQ-4269618

* OSGi: Die Anzahl der beim Rendern generierten Seiten kann nicht ermittelt werden. NPR-28922: Hotfix für CQ-4270870
* Unterstützung für statische PDF-Dateien mit dem Forms-Dienst in [!DNL Experience Manager Forms OSGi] aktiviert. NPR-28572: Hotfix für CQ-4270869
* Die Berechtigungen für die Datei XMLForm.exe können nicht geändert werden. NPR-29828, NPR-29237: Hotfix für Q-4267080
* Die statische PDF, die vom Ausgabemodul des Servers [!DNL Experience Manager Forms] erstellt wurde, füllt das Sprachattribut/Tag nicht mit der Sprache des erstellten Dokuments. NPR-27332: Hotfix für CQ-4271002

**Forms – Foundation JEE**

* Aufgrund eines im finalen Artefakt nicht verfügbaren pdfg_srt schlägt das Installationsprogramm fehl. NPR-29854: Hotfix für CQ-4270137
* LCBackupMode.sh funktioniert nicht. NPR-29840: Hotfix für CQ-4269424
* Die UDP-Portreferenz sollte für WebSphere aus der Benutzeroberfläche entfernt werden. Hotfix für CQ-4264782

### Enthaltende Feature Packs

#### Assets - Einbezogen

* Multi-Site-Manager bietet jetzt Unterstützung für [!DNL Experience Manager Assets]. Weitere Informationen finden Sie unter [Assets mit MSM wiederverwenden für Experience Manager Assets](https://docs.adobe.com/content/help/en/experience-manager-65/assets/using/reuse-assets-using-msm.html). NPR-29199: Hotfix für CQ-4259922

#### Sites - Einbezogen

* Exportieren Sie die Erlebnisfragmente nach [!DNL Adobe Target]. [!DNL Experience Manager] Weitere Informationen finden Sie unter [Erlebnisfragment-Link-Wiederschreibungsanbieter - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix für CQ-4265469

#### Forms - Dokument-Services - inbegriffen

* Nur OSGi: Es wurde ein neues Attribut PAGECOUNT in Output und Forms Service hinzugefügt. NPR-28922: Hotfix für CQ-4270870
* Nur OSGi: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert. NPR-28572: Hotfix für CQ-4270869
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert. NPR-29237: Hotfix für CQ-4267080

### OSGi-Bundles und Inhaltspakete

Die folgenden Dokumente Liste der OSGi-Pakete und Inhaltspakete in [!DNL Experience Manager] 6.5.1.0

Liste der OSGi-Pakete in [!DNL Experience Manager] 6.5.1.0

[Datei laden](assets/6_5-bundle-list.txt)

Liste der in [!DNL Experience Manager] 6.5.1.0 enthaltenen Inhaltspakete

[Datei laden](assets/6_5-content-package-list.txt)
