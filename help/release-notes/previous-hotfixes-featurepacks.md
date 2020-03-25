---
title: Versionshinweise zu AEM 6.5 Previous Service Pack
description: Versionshinweise speziell für Adobe Experience Manager 6.5 Service Pack 3 und früher.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: 7345d629aa628c2e2e094a8194d9306d7c3d2d60

---


# In früheren Service Packs enthaltene Hotfixes und Feature Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## AEM 6.5.3.0

Adobe Experience Manager 6.5.3.0 is an important release that includes performance, stability, security, and key customer fixes and enhancements released since the general availability of 6.5 release in **April 2019**. Es kann über Adobe Experience Manager (AEM) 6.5 installiert werden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.6 aktualisiert.

* Adobe Experience Manager Assets unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Ansicht der Liste hinzugefügt.

* Die Sortierung von Assets basierend auf der Spalte &quot;Name&quot;wurde in der Ansicht &quot;Liste&quot;aktiviert.

* Dynamische Medien unterstützen jetzt Smart-Zuschneiden von Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen.

* Dynamische Medien unterstützen Smart Imaging.

* Möglichkeit zum [Festlegen von Abwesenheitseinstellungen](../forms/using/configure-out-of-office-settings.md) in AEM Workflows.

* Möglichkeit zur [Freigabe von Inbox- oder Inbox-Elementen](../forms/using/configure-shared-queues-osgi.md) für andere Benutzer in AEM Workflows.

* Möglichkeit, interaktive Kommunikation im Stapelmodus zu [generieren](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

* Die Version von jQuery im Paket ContextHub wurde auf 3.4.1 aktualisiert.

### Assets {#assets-6530-enhancements}

**Produktverbesserungen**

* Experience Manager Assets unterstützt jetzt ZIP-Archive, die mit dem Deflate 64-Algorithmus (NPR-27573) erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM Liste Ansicht und in den Asset-Suchergebnissen in der Liste Ansicht (NPR-31312) hinzugefügt.

* Die Sortierung nach der Spalte &quot;Name&quot;ist in der Ansicht &quot;Liste&quot;zulässig (NPR-31299).

* Die Asset-Dateien GLB, GLTF, OBJ und STL unterstützen die Asset-Vorschau auf der Seite &quot;Asset-Details&quot;in DAM (CQ-4282277).

* ReplicationOnModifyListener-Ereignis wird beim Hochladen von Segmenten in dynamischen Medien (CQ-4281279) für Chunk-Knoten ausgelöst.

* Dynamische Medien unterstützen jetzt Smart-Zuschneiden von Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen (CQ-4278995).

* Dynamic Media unterstützt Smart Imaging (CQ-4222249).

* Die Ansicht &quot;Suchen/Durchsuchen&quot;wurde in der Foundation-Auswahl als Standard-Ansicht festgelegt, wenn Abfrage-Parameter in der Anforderung übergeben werden (NPR-31601).

**Fehlerkorrekturen**

* Metadaten für einige PDF-Dokumente werden beim Ändern des Titels (NPR-31629) nicht aktualisiert und im PDF-Format gespeichert.

* Asset Sharing funktioniert nicht für Assets, deren Name das Pluszeichen &quot;+&quot;enthält (NPR-31547).

* Änderungen im Standardsuchformular Assets Admin * Suchleiste funktionieren nicht wie erwartet (NPR-31502).

* Vorschläge werden nicht angezeigt, wenn Sie die Omniture-Ansicht für Assets zum Durchsuchen von Assets verwenden (NPR-31496).

* Asset-Verweise in Sammlungen werden nicht aktualisiert, wenn die referenzierten Assets an einen anderen Speicherort verschoben werden, sofern dieselben Assets von verschiedenen Benutzern durch unterschiedliche Sammlungen referenziert werden (NPR-31486).

* Duplikat-IPTC-Tags werden Asset-Metadaten hinzugefügt (NPR-31328).

* Die Suchergebnisanzahl in der oberen rechten Ecke wird nicht korrekt aktualisiert, wenn die Suche über die Filterleiste ausgelöst wird (NPR-31316).

* Alle Kontrollkästchen werden deaktiviert, wenn die Kontrollkästchen der zweiten Ebene im Filter &quot;Dateityp&quot;deaktiviert werden, und der Text in der Suchleiste ist nicht mit den ausgewählten/nicht ausgewählten Eigenschaften synchronisiert (NPR-31287).

* Alle Mitglieder (Benutzer/Gruppen) können nicht aus dem Bereich &quot;Mitglieder&quot;eines Ordners entfernt werden. beim Versuch, alle Benutzer zu entfernen, wird der angemeldete Benutzer zur Liste hinzugefügt (NPR-31171).

* Assets mit dem Pluszeichen &quot;+&quot;im Dateinamen können nicht gelöscht werden (NPR-31162).

* Dropdown-Menü erstellen, das im oberen Menü bei Auswahl eines Ordners angezeigt wird, zeigt nicht &quot;Ordner&quot; als Erstellungsoption (NPR-30877).

* Ordnerauswahl &quot;Erstellen&quot;> &quot;DateiUpload&quot;-Aktionselement fehlt, wenn ACL für &quot;Ablehnen&quot;(jcr:removeChildNodes) und &quot;jcr:removeNode&quot;auf Pfad für einen Benutzer angewendet werden (NPR-30840).

* DAM Workflows beim Hochladen bestimmter MP4-Assets in den Status &quot;statisch&quot;wechseln, wodurch alle verbleibenden Workflows in den Status &quot;statisch&quot;wechseln (NPR-30662).

* Fehler wegen ungenügenden Speicherplatzes werden beobachtet, wenn große PDF-Dateien (mit mehreren Gigabytes) zu DAM hochgeladen und deren Teilassets verarbeitet werden (NPR-30614).

* Die Massenbewegung von Assets schlägt fehl und es wird eine Warnmeldung angezeigt (NPR-30610).

* Beim Verschieben von Assets aus einem Ordner in einen anderen in AEM, das im Dynamic Media Scene7-Runmode ausgeführt wird (NPR-31630), werden die Asset-Namen in Kleinbuchstaben geändert.

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler festgestellt, da sich das Bild im Ordner befindet, der dem Namen der Scene7-Firma entspricht (NPR-31340).

* Dynamische Medienelemente, die Verweise enthalten, werden nicht veröffentlicht (NPR-31180).

* Uploads von AEM Dynamic Media - Scene7-Runmode zu Scene7 dauern zu lange, bis sie abgeschlossen sind (NPR-31048).

* Hotspot, der zu einem Bild-Asset hinzugefügt wurde, ist auf der Seite mit den Asset-Details nicht über den interaktiven Bild-Viewer sichtbar (NPR-30979).

* Es werden enorme Sling-Aufträge erstellt und das Verarbeitungsbanner wird erneut angezeigt, wenn Aktionen, die in AEM Assets ausgeführt werden, an Scene7 (NPR-30947) übergeben werden.

* Beim Erstellen der Sprachkopie von Assets treten Konflikte auf, und Assets werden nicht nach Scene7 hochgeladen (NPR-30932).

* Dynamische Darstellungen, die von AEM heruntergeladen wurden und im Dynamic Media Hybrid-Modus ausgeführt werden, sind beschädigt (sie sind vom Texttyp mit Inhalt, der &quot;Bild kann nicht gefunden werden&quot;anstelle des Bildinhaltstyps) (NPR-30876).

* Der Arbeitsablauf für die Videokodierung mit dynamischer Medienkodierung kann keine Miniaturansicht für das Video generieren, das aus Scene7 in den Modus für die Ausführung von Scene7 migriert wird (CQ-4282011).

* Bei der Migration von Assets von einer Instanz zu einer anderen mit unterschiedlichen Scene7-Firmen-IDs (CQ-4280548) wurde eine IpsApiException-Ausnahme beobachtet.

* Die Miniaturansicht von 3D-Assets ist nicht informativ, wenn ein unterstütztes 3D-Modell in AEM integriert wird (CQ-4283701).

* Bildlaufschaltflächen werden im Viewer angezeigt, wenn ein 3D-Asset nur über wenige Ansichten verfügt (CQ-4283322).

* Falsche Höhe des Containers eines hochgeladenen 3D-Modells, das auf der Seite &quot;Asset-Details&quot;in der Vorschau in DimensionalViewer angezeigt wird (CQ-4283309).

* Videos können nicht mit SmartCropVideoViewer in Internet Explorer 11 und Safari wiedergegeben werden (CQ-4281422).

* Die Verwendung der Schaltfläche zum Verschieben, um mehrere Assets von einem Ordner in einen anderen zu verschieben, schlägt in AEM, das auf Dynamic Media - scene7 ausgeführt wird, fehl (CQ-4280384).

* Verzerrtes Video wird in Asset-Details angezeigt, wenn der MIME-Typ nicht MP4 ist (CQ-4279704).

* Neuaufgenommene Videos in Ordnern mit Video-Profil bleiben auch nach Abschluss der Kodierung auf 100 % im Verarbeitungszustand (CQ-4279389).

* Durch das Verschieben von Assets aus einem Ordner werden zahlreiche Sling-Aufträge (Scene7-API-Aufrufe) generiert, die im Idealfall erforderlich sind (CQ-4278664).

* Die Namen des Bildsatzes werden in Scene7 in Kleinbuchstaben geändert, wenn Bildsatz (oder Mediaset) erstellt und mit einer entsprechenden Benennungskonvention in DAM (CQ-4281112) benannt wird.

* Scene7 Migrator stellt den Veröffentlichungsstatus falsch ein (CQ-4263492).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers in Inhaltsfragmenten (CQ-4282898).

* PDF-Dateien werden nicht indiziert und der Inhalt in ist nicht durchsuchbar (CQ-4278916).

* Fehler &quot;Gruppe nicht nach Benutzerauswahl aufgeführt: &quot;false to equal true&quot;wird beim Hinzufügen von &quot;Closed User Group&quot;mit &quot;different&quot; `principalName` und `authorizableId` (CQ-4278177) beobachtet.

* Die Ansicht &quot;Assets UI Column&quot;zeigt alle Pfade unabhängig vom Stammpfad des jeweiligen Mandanten an (CQ-4278175).

* Die Suche des Asset-Selektors funktioniert nicht wie erwartet (CQ-4275886).

* Die Workflows sind fehlgeschlagen (CQ-4271928).

* DAM Ereignis Purge löscht die neuesten (maxSavedActivities) Ereignis-Daten und speichert die zuvor erstellten Daten (NPR-31336).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Die Aktionsleiste und die Asset-Anzahl werden nicht aktualisiert, wenn Sie alle Elemente auswählen und dann die Auswahl einiger Elemente (Ordner/einzelne Assets) in der Touch-Benutzeroberfläche (NPR-31118) aufheben.

* Während der Abfrage nach Auftragsdetails eines Assets (CQ-4283569) wird in AEM eine Ausnahme angezeigt.

### Sites {#sites}

* Wenn die LiveCopy-Vererbung beschädigt ist, werden auf Live-Kopierseiten anstelle von LiveCopy-Links Sprachkopie-Links angezeigt (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).
* Wenn ein Benutzer japanische oder koreanische Zeichen in die Eigenschaft description eines Menüs einfügt, werden im Menü verzerrte Zeichen für japanischen und koreanischen Text angezeigt. (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen (NPR-30879).
* Standardmäßig wird der RTE-Editor (RTE) mit Gerüsten versehen. wendet die Inline-Schriftgröße unerwartet auf Elemente an (NPR-31284).
* Wenn ein Benutzer sich auf Felder in der linken Schiene konzentriert und zum Einfügen von Inhalten einen Tastaturbefehl verwendet, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31172).
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Multifeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten (NPR-30882) gespeichert.
* Die ResponsiveGridExporter-API gibt die com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter-Schnittstelle nicht zurück. Das Paket com.day.cq.wcm.foundation.model.impl wird als privates Paket deklariert (NPR-31398).
* Wenn eine Seite mit ExperienceFragments im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das `editor.html` Präfix und `wcmmode=disabled`im Publisher)., endet die Anforderung im HTTP-Statusfehlercode 500 (NPR-30743).
* Benutzer können ihr Kennwort nicht ändern und nicht auf ihre Profil-Seite zugreifen (NPR-31161).

### Suchen und Benutzeroberfläche {#search-ui-interface}

* Beim Wechsel von der Card-Ansicht zur Liste-Ansicht auf einer Suchergebnisseite kommt es zu einer Verzögerung, bevor ein Bildlauf durchgeführt werden kann (NPR-31286).

* Das Kontrollkästchen &quot;Alle auswählen&quot;ist in der Ansicht &quot;Liste&quot;auf der Benutzeroberfläche der Sites (NPR-31614) ausgeblendet.

* Die Zählung &quot;Alle auswählen&quot;auf einer Suchergebnisseite ist nicht korrekt (NPR-31120).

* Der Metadaten-Editor zeigt Tags an, die nicht vorhanden sind (NPR-31119).

### Übersetzung {#translation}

* Bei Auswahl der Option &quot;Fälliges Datum&quot;in einem Übersetzungsauftrag (NPR-31270) werden zwei Kalender-Popups angezeigt.

### Plattform {#platform}

* Die Option &quot;Mime-Typ&quot;in der Webkonsole funktioniert nicht (NPR-31108).

* Das Clientzertifikat wird beim Konfigurieren des Single Sign-On (NPR-31165) nicht akzeptiert.

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Dienst werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt orderby ``fn:name()`` in xpath-Abfragen (NPR-31322).

* Die Struktur der Duplikat-Aktivierung wird beim Aktualisieren von AEM 6.3 (NPR-31513) erstellt.

* Bei weitergeleiteten Anforderungen werden keine Antwortheader beibehalten, die während der Sling-Authentifizierung festgelegt werden (NPR-30013).

* Die Suche innerhalb der Picker-Komponenten funktioniert nicht (NPR-31692).

* Beim Anhängen einer ZIP-Datei an einen AEM Communities-Beitrag aufgrund verschiedener Versionen von Apache POI und Apache Tika Bundle (NPR-31018) wird ein Fehler angezeigt.

* Das ``org.apache.sling.distribution.api`` Bundle ist im Konfigurationsmanager ausgeblendet und steht daher nicht für benutzerdefinierte Bundles (NPR-31720) zur Verfügung.

### Projekte {#projects}

* Das Wechseln von Kalendereinstellungen funktioniert nicht (NPR-31271).

### Brand Portal {#assets-brand-portal}

**Produktverbesserungen**

* Der Workflow zum Importieren von Assets in AEM Assets wurde geändert, um nur die neu erstellten Assets vom Markenportal zu AEM abzurufen und die bereits vorhandenen Assets im Ordner NEW zu überspringen, um eine Replikation zu vermeiden (CQ-4278527).

**Fehlerkorrekturen**

* Beim Erstellen eines neuen Beitragsordners in der Asset-Sourcing-Funktion (CQ-4282825) wird ein falsches Symbol angezeigt.
* Beim Erstellen eines neuen Beitragsordners werden ein oder beide Unterordner (NEU und FREIGEGEBEN) nicht im Beitragsordner (CQ-4282424) angezeigt.
* System gibt eine Ausnahme aus, wenn der Benutzer versucht, den Beitragsordner von AEM in das Markenportal erneut zu veröffentlichen, nachdem er neue Assets aus dem Beitragsordner vom Markenportal-Ende (CQ-4279740) erhalten hat.
* Das Erstellen eines Beitragsordners in einem Beitragsordner (verschachtelter Ordner) ist verboten, um Komplexität zu vermeiden (CQ-4278391).
* Das System gibt beim Hochladen der aus der AEM Admin Console importierten Markenportal-Liste (.csv-Datei) eine Ausnahme aus. Nur die Felder &quot;E-Mail&quot;, &quot;Vorname&quot;und &quot;Nachname&quot;in der .csv-Datei sind obligatorisch (CQ-4278390).

### Communities {#communities}

**Fehlerkorrekturen**

* Schnelllinks zum Verwalten von Gruppen (Gruppen öffnen/bearbeiten/Veröffentlichen/Löschen) sind für Community-Administratoren nicht sichtbar (Gruppenadministrator/Site-Administrator) (NPR-31627).
* Ein gesendeter Blog wird nur angezeigt, wenn die Seite manuell aktualisiert/neu geladen wird (NPR-31599).
* Bei der von der Funktion &quot;Erwähnungen&quot;verwendeten JCR-Abfrage wird zwischen Groß- und Kleinschreibung unterschieden. Die Rückgabe der Ergebnisse dauert zu lange (NPR-31475).
* AEM 6.5 UberJar-Datei löst eine Ausnahme aus, da das `cq-social-translation` Bundle in der AEM 6.5 UberJar-Datei (NPR-31186) fehlt.
* Jackson Databind-Bibliotheken wurden auf Version 2.9.9.3 aktualisiert, um neue Schwachstellen zu beheben (NPR-30967).
* Die Titel der Aktivitäten und Benachrichtigungen sind inkonsistent (NPR-30941).
* Die Paginierung in Communities Blogs funktioniert nicht richtig. (NPR-30914) 
* Analytics-Berichte werden nicht in der AEM-Autorenumgebung ausgefüllt, eine leere Seite wird angezeigt (NPR-30913).

### Oak {#oak}

* Aktualisierungen des Lucene-Indexes, die dazu führen, dass der Autorenserver langsamer wird (NPR-31548).

### Formulare {#forms-6530}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

#### Forms-Add-on-Paket {#forms-add-on-package-6530}

**Adaptive Formulare**

* Zeichenfolgen enthalten den Wörterbuchschlüssel beim Lokalisieren von adaptiven Formularen (NPR-31110).

**Interaktive Kommunikation**

* **MissingNode.toString()** gibt nach der Aktualisierung der Jackson-Bibliotheken auf 2.10.0 (NPR-31549) falsche Ergebnisse zurück.

* Der Texteditor entfernt nach dem Zufallsprinzip Leerzeichen aus dem aus Microsoft Word kopierten Text (NPR-31113).

**Korrespondenzverwaltung**

* Beschriftungen und QuickInfos werden beim Migrieren von Briefen von LiveCycle ES4SP1 auf AEM 6.5 (NPR-31615) nicht angezeigt.

* **Textflussformatierung wird beim Speichern von Briefen als Entwürfe nicht mehr unterstützt** (NPR-30463).

**Arbeitsablauf**

* OSGi-Arbeitsablauf schlägt aufgrund der 100%igen CPU-Auslastung (NPR-31233) fehl.

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30909).

#### Forms on JEE-Installationsprogramm {#forms-jee-installer-6530}

**Forms - Document Services**

* Der SOAP-Webdienst, der MTOM in einem .NET-Projekt verwendet, zeigt Ausnahmen für AssemblerServiceClient-Aufrufe und HtmlToPDF2-Methoden (NPR-4281771) an.

**Foundation JEE**

* Die Aktionskonfiguration lädt die Prozessnamen für Übermittlungsaktion &quot;Aufrufen eines Formulararbeitsablaufs&quot;(NPR-31478) nicht.

### Enthaltene Feature Packs {#feature-packs-included-6530}

>[!NOTE]
>
>AEM Forms-Kunden müssen unbedingt beachten, dass das AEM Forms-Add-on-Paket erst nach der Installation jeglicher Service Packs, Cumulative Fix Packs oder Feature Packs von AEM installiert werden darf.

#### Forms – Foundation JEE {#forms-foundation-jee-feature}

* AEM Forms-Unterstützung für Oracle 18c (NPR-29155).

## AEM 6.5.2.0

AEM 6.5.2.0 is an important release that includes performance, stability, security, and key customer fixes and enhancements released since the general availability of AEM 6.5 in **April 2019**. Sie kann auf AEM 6.5 installiert werden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.3 aktualisiert.
* Es wurde eine Konfigurationseigenschaft hinzugefügt, anhand derer Experience Fragments direkt in benutzerdefinierte Workspaces für Adobe Target exportiert werden können.
* Assets-Benutzer können nach visuell ähnlichen Bildern suchen. AEM zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Siehe [Verwenden von Connected Assets](../assets/use-assets-across-connected-assets-instances.md).

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten.
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt.
* Anhand von Asset-Standardfiltern für die Replikation wird die Performance von Dynamic Media optimiert.
* Für den Dynamic Media Scene 7-Modus (DMS7) wurden die Optionen zum Zuschneiden/Drehen von Assets wiederhergestellt.
* Es wurde eine Option zum Stummschalten von Videos beim Laden in VideoPlayer implementiert.
* Fehlerkorrektur – In der Spaltenansicht der Asset-Benutzeroberfläche werden jetzt nur noch mandantenspezifische Inhalte angezeigt.
* Fehlerkorrektur – Änderungen des Stilakkordeons wirken sich jetzt auf die Suchergebnisse aus.

### Assets {#assets}

**Produktverbesserungen**

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Hotfix für CQ-4270245. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* Assets-Benutzer können nach visuell ähnlichen Bildern suchen. AEM zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

**Fehlerkorrekturen**

* Von der ACP-API generierte Asset-Pfade in URL- und Ordner-Metadaten sind nicht URL-kodiert. GRANITE-26198: Hotfix für CQ-4271814
* Enthält ein Archiv einen Ordner mit einem Prozentzeichen (%) im Namen, kann es über die Assets-Oberfläche nicht entpackt werden. NPR-29989: Hotfix für CQ-4270467
* Touch-Benutzeroberfläche: Im Assistenten zum Verwalten von Veröffentlichungen werden nach der Seite im Hauptteil der Beitragsanfrage Verweise hinzugefügt, wodurch alle Assets nach der Seite veröffentlicht werden. Wenn die Seite wiedergegeben wird, werden einige Assets in der Veröffentlichungsinstanz verpasst. NPR-29985: Hotfix für CQ-4270724
* Die Funktion zum Aufheben des Bezugs zwischen Assets funktioniert nicht, wenn der Name der entsprechenden Assets Sonderzeichen (URI-kodierte Zeichen) enthält. NPR-30387: Hotfix für CQ-4274446
* Beim Bearbeiten eines Inhaltsfragments wird dessen Version mit einer falschen Benutzerangabe erstellt.
* Fehler beim Erstellen von Sammlungen auf mandantenbasiertem System. NPR-30114: Hotfix für CQ-4272948
* Die Spaltenansicht der Assets-Benutzeroberfläche berücksichtigt nicht den Stammpfad des aktuellen Mandanten, sondern greift auf die DAM-Pfade aller Mandanten zu. NPR-30636: Hotfix für CQ-4275481
* Cross-Site-Scripting-Angriff (XSS) über das Fenster für die Warnmeldung zu eingeschränktem Dateizugriff möglich, da das injizierte Bild sichtbar ist. NPR-30617: Hotfix für CQ-4270133
* MultiTenant: Mandanten, die Ordnereigenschaften speichern, beachten sowohl die Erfolgsaufforderung als auch die Fehlermeldung, dass die Aktion nicht erfolgreich war: &quot;Eigenschaften können nicht bearbeitet werden. unzureichenden Berechtigungen nicht geändert werden konnten, was für Verwirrung sorgt. NPR-30545: Hotfix für CQ-4275333
* Im Asset-Auswahldialog lässt sich keine Asset auswählen und somit auch nicht die Funktion zum Ersetzen der zugehörigen Quelle verwenden, um die Quelle zu aktualisieren. NPR-30502: Hotfix für CQ-4275029
* Der Workflow „DAM-Update-Asset“ beim Hochladen großer mp4-Dateien den Status „veraltet“. NPR-30480: Hotfix für CQ-4271352
* Die Funktion zum Erstellen von Prüfungsaufgaben schlägt aufgrund nicht vorhandener Nutzdaten fehl, was entsprechend auch alle nachfolgenden Aktionen im Zusammenhang mit Prüfungsaufgaben fehlschlagen lässt. NPR-30468: Hotfix für CQ-4274263
* Problem bei der Verbindung mit Adobe Smart-Tag über DataPower. NPR-30026: Hotfix für CQ-4269457
* Die Spaltenansicht der Assets-Benutzeroberfläche löst einen Fehler aus, wenn versucht wird, die Filter links von der Leiste zu öffnen. NPR-30501: Hotfix für CQ-4273862
* Wenn Gruppen hinzugefügt werden, die über LDAP in den Eigenschaften der geschlossenen Benutzergruppe eines Asset-Ordners synchronisiert wurden, wird die Gruppe nicht gespeichert und abgerufen. NPR-30615: Hotfix für CQ-4274689
* In den Feldern zum Filtern der Suche nach Stil und Ausrichtung wird der automatisch vervollständigte Wert nicht auf die Suchanfrage angewendet. NPR-30620: Hotfix für CQ-4275724
* Enthält der Name eines Ordners Leerzeichen und das Zeichen „&amp;“, zeigt der ihm zugehörige Asset-Freigabe-Link bei einigen Assets leere graue Karten an. NPR-30557: Hotfix für CQ-4270187
* Das Metadatenschemaformular für Ordner erkennt den Datentyp nicht automatisch, was zur Folge hat, dass es bei der Formularübermittlung den zugehörigen TypeHint nicht erstellt. NPR-30599: Hotfix für CQ-4275227
* In der Autoren-Benutzeroberfläche für DMS7 sind die Optionen zum Zuschneiden und Drehen von Assets deaktiviert. NPR-30118: Hotfix für CQ-4273221
* Die Funktion „Link freigeben“ funktioniert nicht auf einer AEM-Instanz mit DMS7-Konfiguration. NPR-30080, NPR-30492: Hotfix für CQ-4273651
* Das Hinzufügen der Dynamic Media Scene7-Komponente zur Seite und das anschließende Veröffentlichen der Seite lösen nicht jedes Mal die Konfiguration von dmscene7 aus. NPR-30641: Hotfix für CQ-4275962
* In AEM wurde ein IPSJobJournal ergänzt, damit pro Verarbeitungsprofil nur ein IPS-Auftrag (Intrusion Prevention System) erstellt wird. NPR-30490: Hotfix für CQ-4273614
* Dynamische Medien: Es wurden Standard-Filter hinzugefügt, um Assets von der Replizierung auf den AEM-Veröffentlichungsknoten auszuschließen. NPR-30538: Hotfix für CQ-4274678
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt, der die Nutzung von Ordnern als Nutzlast ermöglicht. Der Workflow umfasst zwei Schritte: Die erneute Verarbeitung von Assets ohne Handles erfolgt über die Zuordnung von Metadaten zum nächsten Schritt, das erneute Hochladen aller Assets ohne Asset-Handle zu S7 dann in einem einzelnen IPS-Auftrag. Weitere Informationen finden Sie unter „Konfigurieren von Dynamic Media Cloud Services“. NPR-30489: Hotfix für CQ-4272903
* Wird nach der korrekten CSV-Datei eine falsche CSV-Datei hochgeladen, wird die korrekte CSV-Datei gelöscht. Hotfix für CQ-4277694, CQ-4277814
* Falsches Symbol für die zu entfernenden Beitragsordner. Hotfix für CQ-4277580
* Wird über die Benutzerauswahl auf der Registerkarte für Asset-Beiträge ein Benutzer ausgewählt, erscheint dessen Name nicht in der Tabelle, und auf der Eigenschaftenseite wird im Dialogfeld zum Löschen von Benutzern falscher Text angezeigt. Hotfix für CQ-4277875
* Mitwirkende können dem Asset-Beitragsordner nicht hinzugefügt werden, indem diese über die Benutzerauswahl ausgewählt werden und auf die Schaltfläche „Hinzufügen“ geklickt wird. Hotfix für CQ-4277824, CQ-4278087
* In der Benutzerauswahl funktioniert die Suche nach Benutzernamen in Kleinbuchstaben nicht. Hotfix für CQ-4277958, CQ-4277930
* Benutzer ohne Administratorrechte können Assets in einem neuen Ordner eines Asset-Beitragsordners veröffentlichen. Hotfix für CQ-4278200
* Für DAM-Benutzer (ohne Administratorrechte) besteht keine Möglichkeit, dem Asset-Beitragsordner Mitwirkende hinzuzufügen. Hotfix für CQ-4278192
* Im Asset-Beitragsordner ist die Schaltfläche „Erstellen“ sichtbar. Hotfix für CQ-4277560
* Beim Sortieren der Suchanfrage nach Relevanz werden InDesign-Dokumente zusammen mit InDesign-Vorlagen zurückgegeben. Hotfix für CQ-4273864
* Wenn der Benutzer über eine E-Mail-ID in Großbuchstaben verfügt, können die Benutzer nicht für die zuvor ausgecheckten Assets einchecken. Hotfix für CQ-4276575
* Der Löschvorgang gilt nur für die ausgewählten Vorgaben. Wenn der Bildschirm die Liste nach dem Vorgang automatisch aktualisiert, werden andere Vorgaben angezeigt, die bereits aktualisiert wurden. Hotfix für CQ-4261461
* Die Konfiguration der Dynamic Media Cloud Services im DMHybrid-Modus führt dazu, dass mehrere leere Report Suites in Analytics erstellt werden und keine Report Suite-ID in AEM gespeichert wird, was zu einer Duplizierung der Report Suite führt. Hotfix für CQ-4249780
* Der Vorgang zum Umbenennen in AEM Assets zum Duplizieren des Namens kann nicht mit Scene7 synchronisiert werden. Hotfix für CQ-4276763
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

* Wenn die LiveCopy-Vererbung beschädigt ist, werden auf Live Copy-Seiten Sprachkopie-Links anstelle von LiveCopy-Links angezeigt. (NPR-30980)
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an. (NPR-31182)
* Rich Text Editor (RTE)-Plug-In der Textkomponente zeigt verzerrte Zeichen für japanischen und koreanischen Text an. (NPR-31331)
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen. (NPR-30879)
* Rich Text Editor (RTE) wird standardmäßig auf Elemente mit Inline-Schriftgröße angewendet, was unerwartet geschieht. (NPR-31284)
* Wenn sich ein Benutzer auf linke Schienenfelder konzentriert und zum Einfügen von Inhalten Tastaturbefehle verwendet, werden Inhalte der Zwischenablage des Seiteneditors anstatt des Inhalts eingefügt, der aus den Feldern der linken Leiste kopiert wurde. (NPR-31172)
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Mehrfachfeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten gespeichert. (NPR-30882)
* Die ResponsiveGridExporter-API gibt die com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter-Schnittstelle nicht zurück. Das Paket com.day.cq.wcm.foundation.model.impl wird als privates Paket deklariert. (NPR-31398)
* Wenn eine Seite mit ExperienceFragments im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das `editor.html` Präfix und `wcmmode=disabled`im Publisher), endet die Anforderung mit dem HTTP-Statusfehlercode 500. (NPR-30743)

### WCM – Seiteneditor {#wcm-page-editor-6520}

**Produktverbesserungen**

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten. Hotfix für CQ-4270694

### Verwaltung von Inhaltsfragmenten {#content-fragment-management-6520}

* Die von der Benutzeroberfläche der Inhaltsfragmentmodelle verwendete Abfrage ist sehr langsam und führt schließlich zu einem Fehler. Hotfix für CQ-4270807

### Benutzeroberfläche – Foundation {#ui-foundation}

* Es werden Tastenkombinationen ausgelöst, was den Benutzer daran hindert, in bestimmten Benutzeroberflächen „m“, „p“ und „e“ zu verwenden. NPR-30355: Hotfix für GRANITE-26346
* Beim Schließen der Benutzeroberfläche &quot;Asset-Suche&quot;wird die linke Leiste nicht auf Inhaltsauswahl zurückgesetzt, sodass der Benutzer die Filterleiste anschließend ein zweites Mal öffnen kann. NPR-30509: Hotfix für CQ-4274716
* Mandantenfähige Umgebung: In der Asset-Benutzeroberfläche ist der obere Navigationsbereich nicht verfügbar und es wird ein JavaScript-Fehler ausgelöst. NPR-30104: Hotfix für GRANITE-26344

### Übersetzung {#translation-6520}

* Übersetzungsprobleme behoben – Maschinelle Übersetzung kommt nur noch für wenige Komponenten zum Einsatz. NPR-30079: Hotfix für CQ-4273764

### Plattform {#platform-6520}

* Der für AEM standardmäßig verwendete E-Mail-Absender kann über TLS 1.2 keine E-Mails an einen Remote-SMTP-Server senden. NPR-30476: Hotfix für GRANITE-26605

### Projekte {#projects-6520}

* Die ThumbnailPath-Werte eines DAM-Ordners werden nicht aktualisiert und zeigen auch nach dem Löschen der Assets im Ordner noch die alten Miniaturansichten an. NPR-30424: Hotfix für CQ-4273667
* Nach Abschluss der Option „Verschieben“ bleiben Titel und Name des Assets unverändert. NPR-30647: Hotfix für CQ-4276265

### Communities {#communities-6520}

* Die Diagnose für die Benutzersynchronisierung ist fehlgeschlagen und funktioniert nicht. NPR-30004, NPR-29943: Hotfix für CQ-4270287, CQ-4271348

### Sling {#sling}

* Eine Aktualisierung der Instanz von 6.3.3.2 auf 6.5 führt zu doppelten OSGi-Konfigurationen. NPR-30130: Hotfix für CQ-4274016

### Integration {#integration}

* Angepasster Content wird auf der Veröffentlichungsinstanz erst nach dem Neustart der Instanz korrekt angezeigt. NPR-30377: Hotfix für CQ-4273706
* Bei der Konfiguration von Launch auf einer Website wird der Bibliotheksadresse ein Schrägstrich (/) vorangestellt, der jedes Mal einen manuellen Eingriff verursacht. NPR-30694: Hotfix für CQ-4275501

### Formulare {#forms-6520}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [Installieren des AEM Forms-Add-ons](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#forms-jee-installer).

Zu den wichtigsten Merkmalen von AEM 6.5.2.0 Forms gehören:

* Die Einstellung „Auto“ wurde zu `RenderAtClient` in der `PDFFormRenderOptions`-API für AEM Forms-OSGi hinzugefügt.

#### Forms-Add-on-Paket {#forms-add-on-package}

**Back-End-Integration**

* Das Formulardatenmodell kann nicht mit einer von AWS gehosteten URL für den Lastenausgleich konfiguriert werden. NPR-30123: Hotfix für CQ-4273359
* While creating the Form Data Model (FDM) with the Web Service Definition Language (WSDL), the error message `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` is returned: NPR-30477: Hotfix for CQ-4272921

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

#### Forms JEE-Installationsprogramm {#forms-jee-installer}

**Forms - Document Security**

* Das Anwenden einer Unterschrift mit Zeitstempel schlägt mit folgender Meldung fehl: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Aufruffehler. NPR-30820: Hotfix für CQ-4275852

**Forms - Document Services**

* Wenn die „SubmitURL“ ein kaufmännisches Und (&amp;) enthält, werden im Protokoll Parsing-Fehler angezeigt, wenn eine POST-Anfrage an das renderpdf-Servlet gesendet wird. NPR-30865: Hotfix für CQ-4278232

**Forms – Foundation JEE**

* Der HTMLtoPDF-Dienst zeigt in der JMX-Konsole nicht maxReuseCount an. NPR-30134, NPR-30304: Hotfix für CQ-4273763
* Beim Hinzufügen oder Bearbeiten einer Webdienstverbindung durch Aufrufen von Webdiensten aus AEM Forms Workbench wird ein Fehler ausgegeben: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix für CQ-4273217

### Enthaltene Feature Packs {#feature-packs-included}

>[!NOTE]
>
>AEM Forms-Kunden müssen unbedingt beachten, dass das AEM Forms-Add-on-Paket erst nach der Installation jeglicher Service Packs, Cumulative Fix Packs oder Feature Packs von AEM installiert werden darf.

#### Sites {#sites-feature-packs-included}

* Es wurde eine Konfigurationseigenschaft hinzugefügt, anhand derer Experience Fragments direkt in benutzerdefinierte Workspaces für Adobe Target exportiert werden können. NPR-29189: Hotfix für CQ-4249782

#### Forms - Document Services {#forms-document-services-1}

* Die Einstellung „Auto“ wurde zu `RenderAtClient` in der `PDFFormRenderOptions`-API für AEM Forms-OSGi hinzugefügt. NPR-30759: Hotfix für CQ-4278193

## AEM 6.5.1.0 {#release-6510}

AEM 6.5.1.0 is an important release that includes performance, stability, security, and key customer fixes and enhancements released since the general availability of AEM 6.5 in *April 2019.* Sie kann auf AEM 6.5 installiert werden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Dynamische Benutzeroberflächenstatus können jetzt als benutzerdefinierte Attribute in Tracking-Ereignisse einbezogen werden.
* Der Dynamic Media Scene7-Modus bietet jetzt Unterstützung für 360-Grad-Video-Assets.
* Enabled *Japanese Word Wrap* feature via the styles plugin of Rich Text Editor. Weitere Informationen finden Sie unter [Konfigurieren von japanischen Wortumbrüchen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Assets

* Die DAM DMGGateway-Schnittstelle bietet jetzt Unterstützung für S3-Multipart. NPR-29740: Hotfix für CQ-4226303
* Die Vorschau &quot;Ausgabeformate&quot;erzeugt nach der Aktualisierung auf AEM 6.5\ `Only empty tenantId is currently supported` Fehler. NPR-29986: Hotfix für CQ-4272353
* Da das Dialogfeld „Löschen“ nicht sichtbar ist, können Aufträge nicht gelöscht werden. NPR-29720: Hotfix für CQ-4271074
* Wenn ein Benutzer nach dem Hinzufügen des Asset-Titels auf der Eigenschaftenseite versucht, die Seite zu schließen, öffnet AEM die Eigenschaftenseite erneut. NPR-29627: Hotfix für CQ-4264929
* VersioningTimelineEventProvider sollte die Stammversion zusammen mit dem Knoten des Typs „nt: version“ bereitstellen. Hotfix für GRANITE-26063
* Der AEM DM-Scene7-Modus wurde um die Möglichkeit zum Hochladen und Abspielen von 360-Grad-Videos mit Sphären-Effekten erweitert. Hotfix für CQ-4265131
* Wird bei einer Live Copy die Quelle bearbeitet, wird der falsche Status abgerufen. Hotfix für CQ-4265451
* Multi-Site-Manager bietet jetzt Unterstützung für Assets. Hotfix für CQ-4271453, CQ-4268621, CQ-4257491
* In der AEM-Oberfläche sollte ein zusätzlicher Eintrag für die aktuelle Version des Assets im Timeline-Verlauf angezeigt werden, der den neuesten Eincheckkommentar von Adobe Asset Link enthält. Hotfix für CQ-4262864
* In der Zeitleiste des Inhaltsfragments wird eine Fehlermeldung angezeigt, wenn Eigenschaften fehlen. Hotfix für CQ-4272560
* Problem mit dem Scene7-Videoplayer, wenn er auf den Vollbildmodus erweitert wird. Hotfix für CQ-4266700
* Viewer für vertikalen Zoom: Die Schwenken-Schaltflächen sollten nicht angezeigt werden, wenn ein einzelnes Bild-Asset verwendet wird. Hotfix für CQ-4264795
* Durch das Löschen eines untergeordneten Knotens in einer Live Copy sollte die LiveRelationship getrennt werden. Hotfix für CQ-4270395
* Das Metadatenschema enthält nur Elemente aus der globalen Konfiguration und nicht die Elemente aus dem aktiven Mandanten. Selbst wenn der für „formPath“ angegebene URL-Wert geändert wird, wird er auf den Standardwert zurückgesetzt. NPR-29945: Hotfix für CQ-4262898
* Das Veröffentlichen von Bildvorgaben in Brand Portal schlägt mit dem Fehlercode 500 fehl. NPR-29510: Hotfix für CQ-4268659

### Sites

* Beim Rollout werden leere Eigenschaften ebenso wie mehrere Eigenschaften von der Blueprint nicht übernommen. Das Zurücksetzen der Live Copy auf den Status der Blueprint funktioniert nicht für Komponenten. NPR-29253: Hotfix für -4264928, CQ-4264926, CQ-4267722
* CoralUI, when used with `Multifield`, stores the `fileReferenceParameter` at the component level instead of multifield level. NPR-29537: Hotfix für CQ-4266129
* Verbesserung der AEM-Textkomponente und des Texteditors auf Japanisch. NPR-29785: Hotfix für CQ-4265090
* Eine mithilfe von Timewarp wiederhergestellte Seite sollte zum Zeitpunkt der Versionierung auf das korrekte Bild verweisen. NPR-29431: Hotfix für CQ-4262638
* Ein Problem mit der Vererbung von Style System-Knoten von übergeordneter zu untergeordneter Ebene. NPR-29516: Hotfix für CQ-4270330
* Beim Einrichten eines Social-Media-Postings für die Facebook-Authentifizierung wird eine Fehlermeldung angezeigt. NPR-29211: Hotfix für CQ-4266630
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* In der Coral2-Implementierung werden beim Öffnen der Registerkarte „Berechtigungen“ die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

### E-Commerce

* Das Ausführen einer Lazy-Content-Migration für E-Commerce löst eine ConstraintViolationException aus. NPR-29247: Hotfix für CQ-4264383

### Verwaltung von Inhaltsfragmenten

* Parsing error when opening a Content Fragment which has characters dollar `($)` and open brace `({)`. Hotfix für CQ-4270266

### Experience Fragments

* Exportieren von AEM Experience Fragments nach Adobe Target. Hotfix für CQ-4265469
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

### WCM – MSM

* Nach einem Upgrade auf AEM 6.4.3 benötigt Multi-Site-Manager außergewöhnlich lange für den Rollout. Hotfix für CQ-4271410

### Integration

* Anmeldeversuche mit den BrightEdge-Anmeldeinformationen schlagen mit einem Verbindungsfehler fehl. NPR-29168: Hotfix für CQ-4265872

* Beim Versuch, die AEM Launch-Konfiguration zu bearbeiten und zu speichern, wird eine Ausnahmemeldung angezeigt. NPR-29176: Hotfix für CQ-4265782/CQ-4266153

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

* Siztungsleck bei OAuth-Authentifizierung für jede Replikation in Brand Portal. NPR-30001: Hotfix für GRANITE-26196

### Projekte

* Das Veröffentlichen von Assets in Brand Portal funktioniert nicht aus dem Ordner „/content/dam/mac“ der AEM-Autoreninstanz. NPR-29819: Hotfix für CQ-4271118

### Plattform

* HTMLLibraryManager löscht bei der Cache-Invalidierung alle Inhalte von crx-quickstart. NPR-29863: Hotfix für GRANITE-26197

### Felix

* Bei Verwendung von Java11 werden in der Systemkonsole keine Details zur Speichernutzung angezeigt\. NPR-29669

### Forms

Zu den wichtigsten Merkmalen von AEM 6.5.1.0 Forms gehören:

* OSGi only: Added a new attribute `PAGECOUNT` in Output and Forms Service.

* Nur OSGI: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert.
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert.
* Es wurde Unterstützung für die On-Premise-Integration von ADFS 3.0 für Dynamics ergänzt.

#### Forms-Add-On-Paket

**Backend-Integration**

* Fehler beim Abrufen von geschützter WSDL (Web Service Definition Language). NPR-29944: Hotfix für CQ-4270777
* Wenn AEM Forms auf IBM WebSphere installiert ist, schlägt das Erstellen eines SOAP-basierten Formulardatenmodells fehl. Hotfix für CQ-4251134
* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. Hotfix für CQ-4270586
* Wenn der Titel einer Datenquelle geändert wird, zeigt das Formulardatenmodell den aktualisierten Titel nicht an. Hotfix für CQ-4265599
* Wenn der Name einer Entität oder eines Attributs Bindestriche oder Leerzeichen enthält, können Ausdruck diese Entitäten und Attribute nicht auswerten. Hotfix für CQ-4225129

* Falsche Ausgabe wird beobachtet, wenn ein Doppelpunkt in der Ausgabe der Primitive-Zeichenfolge vorhanden ist. Hotfix für CQ-4260825

* Auch wenn von der REST-API-Ausgabe kein Inhalt erwartet wird, löst der Aufrufvorgang des Formulardatenmodells einen Fehler aus. Hotfix für CQ-4268828

**Adaptive Formulare**

* Während des Lazy-Loading-Vorgangs kann im adaptiven Formularfragment keine neue Instanz hinzugefügt werden. NPR-29818: Hotfix für CQ-4269875
* Bei Vorlagen für Datensatzdokumente (Document of Record, DoR) protokolliert die Überprüfungskomponente keinerlei Fehler, noch zeigt sie Fehler an. Hotfix für CQ-4272999
* Unterstützung zum Deaktivieren des Layout-Editors für adaptive Formulare hinzugefügt. Hotfix für CQ-4270810
* Überprüfungsschritt für adaptive Formulare in AEM 6.5 wurde wiederhergestellt. Hotfix für CQ-4269583

* Aufgrund eines Fehlers bei der Feldüberprüfung für adaptive Formulare funktioniert Adobe Sign nicht. Hotfix für CQ-4269463
* Wenn eine AEM Forms-Instanz über mehr als 20 adaptive Formularfragmente verfügt und der Name aller Formularfragmente mit derselben Zeichenfolge beginnt, gibt die Suche keine oder nur die 20 zuletzt erstellten Fragmente zurück. Hotfix für CQ-4264414, CQ-4264914

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
* Die App für adaptive Formulare unterstützt Microsoft Windows 8.1\ nicht mehr. Hotfix für CQ-4265274
* Die Android-Version der AEM Forms-App stürzt ab, wenn auf Feldebene eines Formulars ein Bild mit mehr als 2 MB angehängt wird. Hotfix für CQ-4265578

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

* Die Benutzeroberfläche „Korrespondenz erstellen“ (CCR-Benutzeroberfläche) in AEM 6.5 Forms kann Korrespondenz, die mit AEM 6.3 Forms erstellt wurde, nicht öffnen. Hotfix für CQ-4266392
* Die Summenfunktion in XDP funktioniert nicht, wenn die Datenwörterbuchelemente Daten vom Typ „Zahl“ enthalten. Hotfix für CQ-4227403
* Die Invalidierungslogik des Arbeitsspeichercaches für Briefe muss aktualisiert werden, da beim Veröffentlichen eines Assets die Zeit seiner letzten Änderung nicht aktualisiert wird. Hotfix für CQ-4250465
* Dokumentfragment, Datenwörterbuch und Briefe können nicht veröffentlicht werden. Hotfix für CQ-4272893

#### Forms JEE-Installationsprogramm

**PDF Generator**

* Die Konvertierung von CAD- in PDF-Dateien schlägt mit dem 64-Bit-JDK fehl. NPR-29924, NPR-29925: Hotfix für CQ-4272113
* Die Bezeichnung „HTML-in-PDF“ für die entsprechende Konvertierung mit PhantomJS wurde durch „Web-in-PDF“ ersetzt. NPR-29933: Hotfix für CQ-4234545
* Beim Konvertieren einer ZIP- in eine PDF-Datei wird ein Fehler ausgegeben. Hotfix für CQ-4268628

**Forms – Designer**

* Beim Durchführen einer vollständigen Barrierefreiheitsprüfung für eine mit AEM Form Designer erstellte statische PDF-Datei schlägt die Prüfung der primären Sprache aufgrund eines fehlenden Sprachattributs fehl. Hotfix für CQ-4272923, CQ-4271002

**Forms - Document Security**

* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten OSGi-Installationen nicht mit Java 11 und Java 8\. NPR-29838: Hotfix für CQ-4270441
* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten JEE-Installationen sowie allen unterstützten Anwendungsservern, d. h. JBoss und Websphere, nicht. NPR-29839: Hotfix für CQ-4266721
* Beim Überprüfen der Signaturen in einer PDF-Datei mit PAdES (PDF Advanced Electronic Signatures) wird eine InvalidOperationException generiert. NPR-29842: Hotfix für CQ-4244837
* Unterstützung für Dokument Security Extension für Office 2019\ hinzugefügt. Hotfix für CQ-4254369, CQ-4259764

**Forms - Document Services**

* PDF-Konvertierung in PDF/A-1b mit Formularfeld hat kein Erscheinungsbild-Diktat. NPR-29940: Hotfix für CQ-4269618

* OSGi: Die Anzahl der beim Rendern generierten Seiten kann nicht ermittelt werden. NPR-28922: Hotfix für CQ-4270870
* Unterstützung für statische PDF-Dateien mit dem Forms-Dienst in AEM Forms OSGi aktiviert. NPR-28572: Hotfix für CQ-4270869
* Die Berechtigungen für die Datei XMLForm.exe können nicht geändert werden. NPR-29828, NPR-29237: Hotfix für Q-4267080
* Bei einer vom Ausgabemodul des AEM Forms-Servers erstellten statischen PDF-Datei wird das Sprachattribut/Tag nicht mit der Sprache des erstellten Dokuments ausgefüllt. NPR-27332: Hotfix für CQ-4271002

**Forms – Foundation JEE**

* Aufgrund eines im finalen Artefakt nicht verfügbaren pdfg_srt schlägt das Installationsprogramm fehl. NPR-29854: Hotfix für CQ-4270137
* LCBackupMode.sh funktioniert nicht. NPR-29840: Hotfix für CQ-4269424
* Die UDP-Portreferenz sollte für WebSphere aus der Benutzeroberfläche entfernt werden. Hotfix für CQ-4264782

### Enthaltende Feature Packs

#### Assets - Einbezogen

* Multi-Site-Manager bietet jetzt Unterstützung für Assets. For more information, see [Reuse assets using MSM for Assets](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html). NPR-29199: Hotfix für CQ-4259922

#### Sites - Einbezogen

* Exportieren von AEM Experience Fragments nach Adobe Target. For more details, see [The Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix für CQ-4265469

#### Forms – Dokumentendienste - Einbezogen

* Nur OSGi: Es wurde ein neues Attribut PAGECOUNT im Output- und Forms-Dienst hinzugefügt. NPR-28922: Hotfix für CQ-4270870
* Nur OSGi: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert. NPR-28572: Hotfix für CQ-4270869
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert. NPR-29237: Hotfix für CQ-4267080

### OSGi-Bundles und Inhaltspakete

In den nachfolgenden Textdokumenten werden die in AEM 6.5.1.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt.

Liste der in AEM 6.5.1.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6_5-bundle-list.txt)

Liste der in AEM 6.5.1.0 enthaltenen Inhaltspakete

[Datei laden](assets/6_5-content-package-list.txt)
