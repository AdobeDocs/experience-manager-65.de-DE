---
title: '[!DNL Adobe Experience Manager] 6.5 Service Pack  – Versionshinweise.'
description: Release notes specific to [!DNL Adobe Experience Manager] 6.5 Service Pack 7.
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: e056d25cf16d79e8eadc80b9cb17b60b2ba8d7e1
workflow-type: tm+mt
source-wordcount: '3796'
ht-degree: 5%

---


# [!DNL Adobe Experience Manager] 6.5 Service Pack  – Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.7.0 |
| Typ | Service Pack-Version |
| Datum | 26. November 2020 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.7.zip) |

<!-- TBD: Update the SD link when SP7 is available. -->

## What&#39;s included in [!DNL Adobe Experience Manager] 6.5.7.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.7.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Verbesserungen sowie Verbesserungen in den Bereichen Leistung, Stabilität und Sicherheit umfasst. Diese Verbesserungen wurden seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht. Das Service Pack ist auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.7.0 eingeführt wurden, umfassen:

* Sortieren der für die Aktualisierung verfügbaren Live Copy-Seiten mithilfe der Eigenschaften [!UICONTROL Name],  Zuletzt geändert und [!UICONTROL Letztes Rollout] .

* Durchführen von Seitenverschiebungen und MSM-Rollouts als asynchrone Vorgänge, um deren Auswirkungen auf die Laufzeitleistung zu reduzieren.

* Die Benutzer können digitale Assets in den Ansichten &quot;Karte&quot;und &quot;Spalte&quot;sortieren.

* [!DNL Assets] und [!DNL Dynamic Media] bieten mehrere Verbesserungen an der Barrierefreiheit. Die Verbesserungen betreffen die Tastaturnavigation, die Verwendung von Bildschirmlesehilfen und die Verwendung ähnlicher Hilfstechnologien (AT). Siehe [[!DNL Assets] Verbesserungen](#assets-6570) und [[!DNL Dynamic Media] Verbesserungen](#dynamic-media-6570).

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.22.5 aktualisiert.

Eine vollständige Liste der in [!DNL Experience Manager] 6.5.7.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 7](new-features-latest-service-pack.md).

Im Folgenden finden Sie die Liste der Fehlerbehebungen in Version [!DNL Experience Manager] 6.5.7.0.

### [!DNL Sites] {#sites-6570}

* Wenn Sie die Option &quot; [!UICONTROL Zeitumbruch] &quot;für eine Seite öffnen, die Option für die Seitenleiste der Zeitleiste geöffnet lassen und zur [!UICONTROL Sites] -Konsole navigieren, tritt der `Failed to Load` Fehler auf (NPR-34951).

* Die [!UICONTROL Option &quot;Zeitumbruch] &quot;zeigt keine Bilder für den ausgewählten Datums- und Zeitbereich an (NPR-34951).

* Wenn ein Filter `getHeader()` von einer Seite mit einem Inhaltsfragment aufgerufen wird, tritt der `java.lang.AbstractMethodError` Fehler auf (NPR-34942).

* Wenn der Pfad einer Seite mehrere Inhaltszeichenfolgen enthält, können Vorschauen nicht gerendert werden, und die Versionsvergleichsfunktion schlägt ebenfalls fehl (NPR-34740).

* Wenn Sie einen numerischen Wert für die `String` Typbeschriftungseigenschaft einer Komponente festlegen, können Sie die Komponente löschen und den Löschvorgang rückgängig machen. Nachdem Sie den Löschvorgang rückgängig gemacht haben, ändert sich die Eigenschaft label von `String` in `Long` (NPR-34739).

* Beim Hinzufügen eines Erlebnisfragments basierend auf einer Vorlage mit einem gesperrten Layout zu einer Seite (NPR-34632) tritt die folgende Ausnahme auf:

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.mozilla.javascript.EcmaError: TypeError: Cannot call method "getChildren" of null
   ```

* Wenn Sie einen Ordner verschieben, treten Querschnittsprobleme auf, und der folgende Fehler tritt auf (NPR-34554):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript. org.apache.jackrabbit.oak.query.RuntimeNodeTraversalException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped
   ```

* Wenn neue Assets erstellt, veröffentlicht und an einen neuen Speicherort verschoben werden, wird der `Request to complete move operation` Workflow erstellt und führt zu einem Abbruch. Das Hochladen eines neuen Assets und das Ausführen eines `move` Vorgangs führt dazu, dass der `Request to complete move operation` Workflow im Status &quot;Ausstehend&quot;erstellt wird (NPR-34543).

* Wenn Sie ein Erlebnisfragment aus der Umgebung [!DNL Experience Manager] 6.5.2 in [!DNL Target] Standard exportieren, schlägt der API-Aufruf fehl, da die Workspace-Eigenschaft nicht für [!DNL Target] Standard (NPR-34557) verfügbar ist.

* Benutzer können keine Seiten über die [!UICONTROL Option &quot;Veröffentlichung] verwalten&quot;veröffentlichen, da die Option &quot; [!UICONTROL Veröffentlichen] &quot;nicht mehr angezeigt wird (NPR-34542).

* Wenn Sie dem Text einige Stile hinzufügen, wird dem Text ein `<div>` -Tag hinzugefügt, und der Stil kann nicht mehr auf den Text angewendet werden (NPR-34531).

* Wenn Sie ein Element in einem Popupmenü auswählen und die erforderlichen Dateien aktualisieren, ist es nicht möglich, Dialogfeldwerte zu speichern, da das andere Menü ein leeres erforderliches Feld enthält (NPR-34529).

* Wenn Sie eine Seite aus einer benutzerdefinierten Vorlage erstellen und sie in die Blueprint-Hierarchie verschieben, werden die Beginn der Seite, die sich auf der Seite befinden, früher aus der Live-Kopierhierarchie gelöscht (NPR-34527).

* Wenn ein Artikelstil auf einen Inhalt angewendet wurde, kann er nicht entfernt werden (NPR-34486).

* Alle Live-Kopien und -Kopien eines Erlebnisfragments verweisen auf dieselbe [!DNL Adobe Target] Angebot-ID (NPR-34469).

* Elemente mit Aufzählungszeichen werden zusätzlich zur nummerierten Liste (NPR-34455) angezeigt.

* Die Option &quot;Mit Quelle vergleichen&quot;zeigt nicht den Unterschied zwischen der Quellseite und der bearbeiteten Version einer Seite (NPR-34285).

* Wenn Sie eine Seite löschen, sind die Versionsdetails nicht konfigurierbar (NPR-34159).

* Wenn ein Benutzer die Option &quot;Auswahl [!UICONTROL öffnen] &quot;auswählt, wird der Tastaturfokus auf das ausgeblendete Steuerelement auf der Seite verschoben (CQ-4307779, CQ-4293601).

* Wenn Sie einen veröffentlichten Ordner im Autor verschieben, werden die Ordnerpfade in der Veröffentlichungsinstanz nicht entsprechend aktualisiert (CQ-4305144).

* Wenn ein Benutzer die `Enter` Taste in der Option &quot;Alle [!UICONTROL auswählen] &quot;auswählt, wird der Tastaturfokus nicht zur Option &quot;Steuerung  erstellen&quot;verschoben (CQ-4293599).

* Wenn Sie den `Esc` Schlüssel auswählen, wird der Fokus nicht wieder auf das übergeordnete Steuerelement (CQ-4293593, CQ-4293590) zurückgesetzt.

* Verbesserte WCAG-Kompatibilität für [!DNL Sites] UI- und Core-Komponenten (CQ-4293448).

* [!UICONTROL Die Funktionen &quot;Zoom] &quot;und &quot; [!UICONTROL Skalierung] &quot;sind für die [!DNL Sites Editor] Seite deaktiviert (CQ-4282353).

* Wenn Sie die Option &quot;Nach rechts drehen&quot;verwenden, beendet die Bildschirmlesehilfe die Narratisierung des aktuellen Drehungs- oder Drehstatus (CQ-4282128).

* Die Schaltflächen zum Konfigurieren des Dialogfelds &quot;Fertig&quot;und &quot;Abbrechen&quot;verfügen über mehr als einen Tabstopp (CQ-4274601).

* Das Verschieben von Seiten mit einem ähnlichen Namen auf derselben Ebene ist nicht zulässig (NPR-35041).

* Nach Auswahl der Option Löschen (x) wird der Tastaturfokus nicht in das Feld [!UICONTROL Filter] verschoben (CQ-4293581).

* Wenn Sie auf [!DNL Experience Manager] 6.5.6.0 aktualisieren, ändert sich das Verhalten des geerbten Absatzsystems und funktioniert nicht ordnungsgemäß (NPR-35117).

* Tastaturbenutzer können den Registerfokus nicht in der richtigen Reihenfolge verschieben, nachdem sie den Abschnitt &quot; [!UICONTROL Aktion] &quot;auf einer [!DNL AEM Sites] Seite ausgewählt haben (CQ-4307786).

* Nachdem Sie beim Bearbeiten eines Inhaltsfragments in der Liste &quot;Zielgruppe&quot;der RTE-Symbolleiste eine Option ausgewählt haben, wird das Dialogfeld &quot;Autor des Inhaltsfragments&quot;flackern (CQ-4305532).

* Tastaturbenutzer können die Optionen in der Dropdown-Liste &quot; [!UICONTROL Hinzufügen Komponente] &quot;nicht mithilfe der Nach-unten-Taste (CQ-4295097) auswählen.

* Der Tabulatorfokus ändert sich nicht in der richtigen Reihenfolge, wenn ein Datum aus dem Menü Kalender auf der Registerkarte [!UICONTROL Assets] einer [!DNL Sites] Seite ausgewählt wird (CQ-4293600).

* Der Tabulatorfokus wechselt nicht zu den nächsten oder vorherigen Optionen für Tastaturbenutzer, nachdem die beim Bearbeiten einer Siteseite verfügbaren Link- oder Textoptionen gelöscht wurden (CQ-4293597).

* Tastaturbenutzer können den Fokus auf Registerkarten nicht wieder auf Mehr Optionen im Abschnitt [!UICONTROL Aktionen] verschieben, nachdem sie die verfügbaren Optionen angezeigt und die `Esc` Taste gedrückt haben (CQ-4293592).

* Wenn Sie die Option &quot; [!UICONTROL Drehen] &quot;für ein Bild im [!UICONTROL Bearbeitungsmodus] aktivieren, wechselt der Tabulatorfokus, anstatt beim Drehen zu bleiben, zur [!UICONTROL Wiederholungsoption] für die Tastaturbenutzer (CQ-4293587).

* Im Dialogfeld &quot;Auswahl  öffnen&quot;auf der Registerkarte &quot; [!UICONTROL Link und Aktionen] &quot;wechselt der Registerfokus nach der Option &quot; [!UICONTROL Abbrechen] &quot;(CQ-4293579) zu ausgeblendeten Elementen auf der Seite.

* Wenn Tastaturbenutzer ein Bild bearbeiten, zur Option &quot; [!UICONTROL Fertig stellen] &quot;navigieren und die Eingabetaste drücken, wird die Fertigstellung nicht angekündigt (CQ-4282351).

* Die Optionen &quot;Nach oben&quot;und &quot;Nach unten&quot;im Dialogfeld &quot; [!UICONTROL Link und Aktionen] &quot;stehen Bildschirmlesehilfen- und Tastaturbenutzern nicht zur Verfügung (CQ-4281120).

* Tastaturbenutzer können den Registerfokus nicht wiederherstellen, nachdem sie auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;zur Option &quot;Schließen (X)&quot;navigiert sind (CQ-4293581, NPR-34653).

### [!DNL Assets] {#assets-6570}

[!DNL Adobe Experience Manager] 6.5.7.0 [!DNL Assets] behebt die folgenden Probleme und bietet die folgenden Erweiterungen.

* Die folgenden Erweiterungen wurden für die Barrierefreiheit in [!DNL Experience Manager Assets] dieser Version vorgenommen. Weitere Informationen finden Sie unter [Zugänglichkeitsfunktionen in [!DNL Assets]](/help/assets/accessibility.md).

   * Beim Navigieren in der Zeitleiste mit einer Tastatur kann die `Esc` Taste die Option &quot;Alle [!UICONTROL anzeigen] &quot;ausblenden, ohne den Fokus zu verlieren (CQ-4293598).
   * Beim Navigieren mit der Tastatur-Tabulatortaste behält das Tag-Feld den Fokus (NPR-35109) bei, nachdem das letzte Tag aus den hinzugefügten Tags entfernt wurde.
   * [!DNL Experience Manager] Komponenten enthalten nun entsprechende Informationen für Namen, Rolle und Wert, die von Bildschirmlesehilfen verwendet werden sollen (NPR-34255).
   * Nachdem Sie das Kombinationsfeld &quot;Typ/Größe&quot;, das Kombinationsfeld &quot;Verknüpfen&quot;, das Sprachkombinationsfeld oder das Textfeld zum Bearbeiten gelöscht haben, kehrt der Tastaturfokus zu den nächsten oder vorherigen Elementen der Benutzeroberfläche oder zu einem relevanteren Element der Benutzeroberfläche zurück (CQ-4293585).
   * Wenn Sie den Mauszeiger über verschiedene Optionen bewegen, werden die Tipps wie &quot;Auswählen&quot;und &quot;Herunterladen&quot;angezeigt. Benutzer, die die Bildschirmvergrößerung verwenden, haben möglicherweise Schwierigkeiten, die Dateiminiaturen anzuzeigen, da der Inhalt durch Bewegen des Mauszeigers angezeigt wird. Es ist jetzt möglich, den Fokus beizubehalten, nachdem die Option mithilfe eines `Escape` Schlüssels entfernt wurde (CQ-4293554).
   * Wenn Sie eine Rasterzelle aus dem Raster auf der Seite auswählen, wird der Fokus auf die Aktionsleiste verschoben, die auf dem Bildschirm angezeigt wird (CQ-4282127).
   * Visuelle Benutzer können zwischen Normaltext und einem Link unterscheiden, da visuelle Hinweise (Unterstreichung und Chevron-Symbol) für Links zu allen Lösungen in der [!DNL Experience Manager] Startseite angezeigt werden (CQ-4282072).

* Die folgende Verbesserung der Benutzererfahrung erfolgt in [!DNL Assets]:

   * Sortieren von Assets in der Karten- und Spalten-Ansicht (NPR-35097) aktivieren.

* Wenn nach der Aktualisierung auf 6.5 eine JSON-Datei mit der Assets HTTP API generiert wird, treten Probleme mit der in der Datei verwendeten Kodierung auf (NPR-35129).

* Benutzer einer Gruppe, denen keine Berechtigung zum Erstellen von Sammlungen erteilt wurde (Option &quot;Sammlung erstellen&quot;ist nicht verfügbar) können weiterhin Sammlungen erstellen, indem sie direkt auf die URL zugreifen `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/collections/createcollectionwizard.html/content/dam/collections?contentPath=/content/dam/collections` (NPR-35115).

* Wenn die gesuchten Assets nach Namen sortiert werden, wird zwischen Groß- und Kleinschreibung unterschieden. Dadurch werden zwei separate sortierte Listen erstellt, die auf dem Gehäuse basieren, das in den Suchergebnissen geordnet angezeigt wird (NPR-35068).

* Wenn ein Inhaltsfragment im Editor geöffnet wird, werden Warnmeldungen (`Invalid value specified for a metadata property`) in den Fehlerprotokollen (NPR-35012) protokolliert.

* Benutzer ohne Administratorberechtigung können abgelaufene Assets mit der [Experience Manager] -Desktop-App bearbeiten. (NPR-34993).

* Wenn dasselbe Asset in die Benutzeroberfläche &quot;Assets&quot;gezogen und eine neue Version erstellt wird, sind die Änderungen in den Metadaten nicht beständig (NPR-34940).

* Beim Bearbeiten von Sammlungen kann ein Benutzer den Titel der Sammlung löschen und die Änderungen erfolgreich speichern (NPR-34889).

* Beim Hochladen eines Duplikat-Bildes wird eine Löschoption angezeigt. Wenn Sie &quot;Löschen&quot;wählen, können die Bilder hochgeladen werden. DAM Update Asset Workflow wird ebenfalls ausgelöst (NPR-34744).

* Bei Verwendung [!DNL Adobe Asset Link] mit [!DNL Adobe InDesign]enthalten die Suchergebnisse keine Ordner und Sammlungen, sondern nur Assets (NPR-34699, CQ-4303666).

* Wenn Sie den Mauszeiger über die Ansicht der Karte bewegen, wird der Bildlauf durch (automatische) Fokussierung auf die Schnellaktionen durchgeführt, die auf der Karte verfügbar sind (NPR-34514).

* Wenn Sie die Eigenschaften mehrerer Assets stapelweise bearbeiten, wird durch Auswahl der Option [!UICONTROL Speichern] die Ansicht des Masseneditors geschlossen und zur Hauptseite [!DNL Assets] weitergeleitet. Dieses Verhalten ist mit dem Verhalten der Option [!UICONTROL Speichern und Schließen] identisch und wird nicht erwartet (NPR-34546).

* Die intelligente Sammlung zeigt nach dem Speichern nicht die richtige Benutzeroberflächeneinstellung an. Die Abfrage wird ordnungsgemäß gespeichert, aber die Oberfläche zeigt immer die zuletzt hinzugefügte Option Predicate (NPR-34539) an.

* Beim Hinzufügen von Assets zu werden [!DNL Experience Manager]die Metadaten ohne Namensraum nicht importiert (NPR-34530).

* Wenn Sie ein Asset in einen Ordner ziehen, um es zu verschieben, zeigt die Benutzeroberfläche auch die Option zum [!UICONTROL Ablegen in Leuchtkasten] und zum [!UICONTROL Ablegen in Sammlung]an. Auch wenn der Verschiebungsvorgang abgebrochen wird, zeigt die Benutzeroberfläche weiterhin die beiden letztgenannten Optionen an (NPR-34526).

* Das Symbol `%>` wird auf der Sammlungsseite angezeigt (NPR-34499).

* In der Ansicht der Spalte werden [!DNL Assets] die Namen der Duplikate und Assets angezeigt, wenn ein Bildlauf nach oben oder nach unten durchgeführt wird, bevor alle Assets angezeigt werden (NPR-34464).

* Wenn Sie unmittelbar nach dem Erstellen eines öffentlichen Ordners einen privaten Ordner erstellen, verwendet der öffentliche Ordner die Einstellungen für den privaten Ordner (NPR-34415).

* In der Ansicht sind die Karten nicht in alphabetischer Reihenfolge aufgeführt und können nicht alphabetisch sortiert werden (NPR-34234).

* Beim erneuten Öffnen von Kaskadenregeln werden die Optionen auf der Benutzeroberfläche nicht beibehalten (CQ-4301452).

#### [!DNL Dynamic Media] {#dynamic-media-6570}

* Die folgenden Verbesserungen wurden für Barrierefreiheit in [!DNL Dynamic Media] (CQ-4290306) vorgenommen. Weitere Informationen finden Sie unter [Zugänglichkeitsfunktionen [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).

   * Bildschirmlesehilfen (JAWS, Erzähler) beschreiben den Namen, die Rolle und den Status der Menüelemente in der Menüoption &quot;Größe einbetten&quot;(CQ-4290927).
   * Benutzer können mithilfe des `Tab` Schlüssels (CQ-4290926) im Dialogfeld &quot;E-Mail-Link&quot;navigieren.
   * Der Arbeitsablauf zum Erstellen von Videokodierungs-Profilen ist benutzerfreundlicher, da die Bildschirmlesehilfe verbessert wurde (CQ-4290623, CQ-4290622).
   * Beim Navigieren mit `Tab` der Taste wird der Fokus auf die entsprechenden Elemente der Benutzeroberfläche im Workflow verschoben, um ein interaktives Video zu erstellen (CQ-4290621, CQ-4290620, CQ-4290619).
   * Die Seiten &quot;Veröffentlichen&quot;, &quot;Asset bearbeiten&quot;, &quot;Smart Crops bearbeiten&quot;und &quot;Bildsatz-Editor&quot;wurden verbessert, um Webstandards zu entsprechen. Hilfstechnologie (AT)-Benutzer können jetzt einfach durch diese Seiten navigieren und Aktionen wie das Zuschneiden von Bildern ausführen (CQ-4290617, CQ-4290616, CQ-4290613, CQ-4290612, CQ-422 90610, CQ-4290614).
   * Die Viewer wurden verbessert, damit Benutzer mit einer Tastatur navigieren können (CQ-4290615).
   * Die Benutzer der Tastatur und der Bildschirmlesehilfe können die Funktion zum Beschneiden verwenden (CQ-4290609).
   * Die Tastaturbenutzer können die Hotspots besser verwalten (CQ-4290604, CQ-4290603).

* Remote-Bildsätze können nicht bearbeitet werden, [!DNL Experience Manager] wenn der Name der Firma und der Ordnername identisch sind (NPR-31340).

* Die z-Indexreihenfolge ist nicht korrekt, wenn Sie versuchen, die Ausgabe nach dem Hinzufügen eines Hotspots zu einem [!DNL Dynamic Media] Bild oder nach der Bearbeitung eines [!DNL Dynamic Media] Videos oder eines [!DNL Experience Fragment] Bildes (CQ-4307267) Vorschau.

* [!DNL Dynamic Media] Die Synchronisierung schlägt fehl, wenn gemischte Mediensets erneut verarbeitet werden (CQ-4307184).

* Wenn ein Asset in einen Ordner verschoben wird, in dem die automatische Synchronisierung konfiguriert [!DNL Dynamic Media] ist, wird das Asset nicht synchronisiert (CQ-4307122).

* [!DNL Dynamic Media] Videos werden auf iOS-Geräten mit den nativen HTML5-Video-Steuerelementen (CQ-4306977, CQ-4306727) nicht wiedergegeben.

* Bilder, auf die SmartCrop angewendet wird, können nicht heruntergeladen werden (CQ-4304558).

* Ordner können nicht selektiv für dynamische Medien veröffentlicht werden (CQ-4304526).

* Wenn Sie die Veröffentlichung einer Videodatei rückgängig machen, heben Sie die Veröffentlichung des adaptiven Videosets nicht von einer konfigurierten Scene7-Bereitstellung auf (CQ-4304405). [!DNL Experience Manager]

* Das Hinzufügen eines Panorama-Bild-Assets zu einer Panorama-Medienkomponente und das Aktualisieren der Seite führt zu einem `Uncaught ReferenceError: $ is not defined` Fehler (CQ-4302810).

* Im [!UICONTROL Viewer-Vorgabeneditor]ist die Modifikatorbeschriftung &quot; [!UICONTROL PanoramicImage/PanoramicImage_VR] &quot;in der `PanoramicView` `PANORAMICVIEW_AUTOROTATE` Komponente nicht verfügbar, wenn Sie die Vorgabe &quot;PanoramicImage/PanoramicImage_VR&quot;bearbeiten (CQ-4302443).

* Videobeschriftungen werden nicht angezeigt, wenn das Video nicht das erste in einem MixedMediaSet (CQ-4298161) ist.

* Der HTML5-E-Katalog-Viewer auf iPhones-Mobilgeräten kann die Seiten nicht drehen oder blättern (CQ-4296611).

* Beim Bildlauf von Farbfeldern auf einem Mobilgerät werden die Farbfelder einige Sekunden lang nach rechts und aus dem Sichtbereich blättert, bevor sie wieder in die Ansicht scrollen (CQ-4296439).

* Wenn ein Viewer-Vorgabe-Übergeordnet-Datensatz erstellt wird, werden das CSS und die Grafik nicht veröffentlicht und nur die Viewer-Vorgabe wird veröffentlicht (CQ-4262205).

* Beim Versuch, ein Erlebnisfragment für einen bestimmten Hotspot in der Komponente &quot; [!UICONTROL Interaktives Video/Bilder] &quot;zu verknüpfen, wird der ausgewählte Pfad zum Erlebnisfragment nicht angezeigt. Stattdessen wird ein leerer Wert aus dem Pfadfeld zurückgegeben (NPR-35146, CQ-4298136).

* Kann kein Erlebnisfragment im IVV-Editor (CQ-4308560) Vorschau werden.

* Wenn Sie einem Bild einen Hotspot hinzufügen und ein Erlebnisfragment auswählen, ist es nicht möglich, die Unterordner und Varianten des Erlebnisfragments (CQ-4307455) auszuwählen.

* Die Nicht-Bild-Assets werden nach dem Hochladen nicht als veröffentlicht angezeigt (CQ-4306415).

#### [!DNL Experience Manager] 3D-Assets {#three-d-assets-6570}

* `DAM CQ MIME Type` -Dienst wendet falsche MIME-Typen auf 3D-Assets an, was zu einem fehlerhaften Rendering führt (NPR-34731).

### [!DNL Commerce] {#commerce-6570}

* Die Benutzeroberfläche für die Commerce-Produktsammlung Liste nicht mehr als 15 Produkte innerhalb einer Sammlung (NPR-34502).

### Plattform {#platform-6570}

* Eine HTTP-Sitzung über HTTPS ist nicht ungültig (NPR-35083).
* Beim Starten von täglichen oder wöchentlichen Aufgaben der Benutzerschnittstelle (NPR-34953) `NullPointerException` wird ein Fehler zurückgegeben.
* Der W3C-Validator meldet Warnungen für konforme JavaScript-Clientbibliotheksdateien (NPR-34898).
* Die `AudienceOmniSearchHandler` Funktion verwendet einen veralteten Index (NPR-34870).
* Beim Abmelden von Experience Manager werden die Cookies nicht gelöscht (NPR-34743).
* Die `findByTitle` Funktion der `TagManager` API funktioniert nicht, wenn der Tag-Name ein Sonderzeichen enthält (NPR-34357).
* Der Vorgang zum Importieren des Synchronisierungspakets für Benutzer ist fehlgeschlagen (NPR-34399).
* Unterstützung für `ariaLabel` und `ariaLabelledby` Eigenschaften zur `Coral.Masonry` Komponente hinzugefügt (GRANITE-29962).
* Der Dispatcher-Cache wird für Seiten mit Inhaltsfragmenten nach der Installation der neuesten Core-Komponenten-Pakete (CQ-4306788) nicht aktualisiert.
* Lokalisierte Tag-Namen mit Anführungszeichen (`"`) werden auf der Benutzeroberfläche nicht richtig angezeigt (CQ-4305439).

### Benutzeroberfläche {#ui-6570}

* Das Feld &quot; [!UICONTROL Link zu] &quot;in den Komponenteneigenschaften zeigt Vorschläge zur automatischen Vervollständigung an, die nicht mit der angegebenen Zeichenfolge übereinstimmen (NPR-34865).

* AEM zeigt die folgende Fehlermeldung an, wenn Sie ein tägliches Wartungsfenster planen, das zwischen 2 Tagen verteilt wird (NPR-35280):

   ```TXT
   ERROR The start time must precede (be less than) the end time
   ```

### Integrationen {#integrations-6570}

* Die Bearbeitung einer vorhandenen [!DNL Adobe Launch] Konfiguration schlägt fehl (NPR-35045).
* Kann nicht exportiert [!DNL Experience Fragments] werden, [!DNL Adobe Target] wenn IMS-Konfiguration und - [!DNL Adobe Target Standard] Umgebung (NPR-34555) verwendet wird.
* Die Option &quot; [!UICONTROL Erstellen] &quot;wird auf der Seite &quot; [!UICONTROL Audiencen] &quot;angezeigt, wenn Sie von einem Ordner zur Seite &quot; [!UICONTROL Audiencen] &quot;navigieren (NPR-35151).

### Sling {#sling-6570}

* Bei der Standardüberprüfung des Anmeldestatus werden die Anmeldeinformationen eines Benutzers überprüft, der nicht vorhanden ist (NPR-34686).

### Übersetzungsprojekte {#translation-6570}

* Beim Stornieren eines Übersetzungsprojekts in wird [!DNL Experience Manager]die Anfrage zur Stornierung nicht an den Übersetzungsdienstleister gesendet (NPR-34433).

### [!DNL Communities] {#communities-6570}

* Alle Fälle ungleicher Terminologie im Produkt werden durch anerkannte Entsprechungen ersetzt (NPR-34311).
* [!DNL Google+] wird aus der Liste der Social Sharing-Optionen entfernt (NPR-33877).

### [!DNL Brand Portal] {#brandportal-6570}

* Die Benutzeroberfläche reagiert nicht, wenn die Assets in der Ansicht  Liste ausgewählt wurden (NPR-34728).

### [!DNL Forms] {#forms-6570}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten [!DNL Experience Manager] Service Pack-Veröffentlichungsdatum.

Informationen zu Sicherheitsaktualisierungen finden Sie auf der Seite [zu Sicherheitsbulletins für](https://helpx.adobe.com/security/products/experience-manager.html)Experience Manager.

## Install 6.5.7.0 {#install}

**Setup-Anforderungen und weitere Informationen**

* AEM 6.5.7.0 requires AEM 6.5. See [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* Der Service Pack-Download ist auf Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)verfügbar.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.7.0 mithilfe von Package Manager auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe does not recommend removing or uninstalling the [!DNL Adobe Experience Manager] 6.5.7.0 package.

### Installieren des Service Packs {#install-service-pack}

Führen Sie die folgenden Schritte aus, um das Service Pack auf einer vorhandenen Adobe Experience Manager 6.5-Instanz zu installieren:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Updatemodus befindet (was der Fall ist, wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt auch einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [Experience Manager] -Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.7.zip)herunter.

1. Open Package Manager and click **[!UICONTROL Upload Package]** to upload the package. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Select the package and click **[!UICONTROL Install]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. See [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, dass Sie auf die Stabilisierung der Fehlerprotokolle warten, bevor Sie auf die Bereitstellung zugreifen. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles, bevor Sie sicherstellen, dass die Installation erfolgreich ist. Typically, this happens on [!DNL Safari] but can intermittently happen on any browser.

**Automatische Installation**

Es gibt zwei Möglichkeiten, Adobe Experience Manager 6.5.7.0 automatisch auf einer Arbeitsinstanz zu installieren:

A. Platzieren Sie das Paket in den `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API aus Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html). Verwenden Sie diese Option, `cmd=install&recursive=true` um die verschachtelten Pakete zu installieren.

>[!NOTE]
>
>Adobe Experience Manager 6.5.7.0 unterstützt keine Bootstrap-Installation.

**Bestätigen der Installation**

1. Auf der Seite mit den Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.7.0)` unter &quot; [!UICONTROL Installierte Produkte]&quot;angezeigt.

1. All OSGi bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Web-Konsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

### Adobe Experience Manager Forms Add-On-Paket installieren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten [!DNL Experience Manager] Service Pack-Veröffentlichungsdatum.

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms werden über ein separates Add-On-Paket bereitgestellt.

1. Stellen Sie sicher, dass das Adobe Experience Manager Service Pack installiert ist.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

### Installieren von Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes](jee-patch-installer-65.md).

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.7.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.7/)verfügbar.

Um UberJar in einem Maven-Projekt zu verwenden, [verwenden Sie UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.7</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und andere zugehörige Artefakte stehen im Maven Central Repository anstelle der Adobe Public Maven Repository (`repo.adobe.com`) zur Verfügung. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar`. Es gibt also keinen `classifier`Wert `apis` für das `dependency` -Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die mit [!DNL Experience Manager] 6.5.7.0 als veraltet markiert wurden. Funktionen werden zunächst als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option ist in der Regel verfügbar.

Überprüfen Sie, ob Sie eine Funktion oder eine Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm &quot; **[!UICONTROL AEM Cloud-Services-Teilnahme]** &quot;wird nicht mehr unterstützt. Mit der in AEM 6.5 aktualisierten AEM- und Zielgruppe-Integration zur Unterstützung der Target Standard-API, die die Authentifizierung über Adobe IMS und I/O verwendet, und der wachsenden Rolle des Adobe Launch bei der Instrumentierung AEM Seiten für Analyse und Personalisierung ist der Opt-In-Assistent funktional irrelevant geworden. | Konfigurieren Sie Systemverbindungen, Adobe-IMS-Authentifizierung und Adobe-I/O-Integrationen über die jeweiligen AEM-Cloud-Dienste. |
| Connectoren | Die Adobe JCR Connector for Microsoft SharePoint 2010 und Microsoft SharePoint 2013 wird für AEM 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Ignorieren Sie die folgenden Fehler in der `error.log` Datei während der Installation von Experience Manager 6.5.7.0:

   ```TXT
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy(1314)] : Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy(1316)] : Could not load implementation object class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy(1315)] : Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy)
   ```

* Wenn Sie Ihre [!DNL Experience Manager] Instanz von 6.5 auf 6.5.7.0 aktualisieren, können Sie `RRD4JReporter` Ausnahmen in der `error.log` Datei Ansicht. Starten Sie die Instanz neu, um das Problem zu beheben.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 5 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie des benutzerdefinierten Assets Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfskopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mit der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Wenden Sie sich an den Kundendienst der Adobe, wenn beim Bearbeiten und Erstellen von Kaskadenregeln im Schema [!UICONTROL Ordnermetadaten Forms Editor] und [!UICONTROL Metadata Schema Forms Editor] Probleme auftreten, die das Dialogfeld Regel  definieren verwenden. Die bereits erstellten und gespeicherten Regeln funktionieren erwartungsgemäß.

* If a folder in the hierarchy is renamed in [!DNL Experience Manager Assets] and the nested folder containing an asset is published to [!DNL Brand Portal], the title of the folder is not updated in [!DNL Brand Portal] until the root folder is published again.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Wenn der Konfigurationsassistent für [!UICONTROL verbundene Assets nach der Installation die Fehlermeldung 404 zurückgibt, müssen Sie die Pakete] und `cq-remotedam-client-ui-content` `cq-remotedam-client-ui-components` Pakete manuell mit dem Package Manager neu installieren.

* Die folgenden Fehler und Warnmeldungen können während der Installation von AEM 6.5.x.x angezeigt werden:
   * „Wenn die Target-Integration mit der Target Standard-API (IMS-Authentifizierung) in AEM konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregat-Funktionen wie SUM, MAX und MIN verwendet werden. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Bild für dynamische Medien ist nicht sichtbar, wenn das Asset über den Viewer für ein kaufbares Banner in der Vorschau angezeigt wird.

## OSGi bundles and content packages included {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Content Packages in AEM 6.5.7.0:

* [Liste der in AEM 6.5.7.0 enthaltenen OSGi-Bundles](assets/6570_bundles.txt)

* [Liste der in AEM 6.5.7.0 enthaltenen Inhaltspakete](assets/6570_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Erfahren Sie, [wie Sie sich an den Kundensupport](https://experienceleague.adobe.com/docs/customer-one/using/home.html)wenden.

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 Versionshinweise](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] Produktseite](https://www.adobe.com/de/marketing/experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

