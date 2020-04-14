---
title: Versionshinweise zu AEM 6.5 Previous Service Pack
description: Versionshinweise speziell für Adobe Experience Manager 6.5 Service Pack 3 und früher.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# In früheren Service Packs enthaltene Hotfixes und Feature Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## Adobe Experience Manager 6.5.3.0

[!DNL Adobe Experience Manager] 6.5.3.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht wurden. It can be installed on top of [!DNL Adobe Experience Manager] 6.5.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.6 aktualisiert.

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Ansicht der Liste hinzugefügt.

* Die Sortierung von Assets basierend auf der Spalte &quot;Name&quot;wurde in der Ansicht &quot;Liste&quot;aktiviert.

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen.

* [!DNL Dynamic Media] unterstützt Smart Imaging.

* Möglichkeit zur [Festlegung von Abwesenheitseinstellungen](../forms/using/configure-out-of-office-settings.md) in [!DNL Experience Manager] Workflows.

* Möglichkeit zur [Freigabe von Inbox- oder Inbox-Elementen](../forms/using/configure-shared-queues-osgi.md) für andere Benutzer in [!DNL Experience Manager] Workflows.

* Möglichkeit, interaktive Kommunikation im Stapelmodus zu [generieren](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

* Die Version von jQuery im Paket ContextHub wurde auf 3.4.1 aktualisiert.

### Assets {#assets-6530-enhancements}

**Produktverbesserungen**

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus (NPR-27573) erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM Liste Ansicht und in den Asset-Suchergebnissen in der Liste Ansicht (NPR-31312) hinzugefügt.

* Die Sortierung nach der Spalte &quot;Name&quot;ist in der Ansicht &quot;Liste&quot;zulässig (NPR-31299).

* Die Asset-Dateien GLB, GLTF, OBJ und STL unterstützen die Asset-Vorschau auf der Seite &quot;Asset-Details&quot;in DAM (CQ-4282277).

* ReplicationOnModifyListener-Ereignis wird während des Hochladevorgangs von Chunk-Knoten in ausgelöst [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen (CQ-4278995).

* [!DNL Dynamic Media] unterstützt Smart Imaging (CQ-4222249).

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

* Beim Verschieben von Assets von einem Ordner in einen anderen im [!DNL Experience Manager] [!DNL Dynamic Media]Scene7-Modus (NPR-31630) wird die Schreibweise für Asset-Namen in Kleinbuchstaben geändert.

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler festgestellt, da sich das Bild im Ordner befindet, der dem Namen der Scene7-Firma entspricht (NPR-31340).

* [!DNL Dynamic Media] Assets, die Verweise enthalten, werden nicht veröffentlicht (NPR-31180).

* Uploads vom [!DNL Dynamic Media]7-Scene7-Modus in den [!DNL Dynamic Media Classic] Vorgang nehmen zu lange in Anspruch (NPR-31048).

* Hotspot, der zu einem Bild-Asset hinzugefügt wurde, ist auf der Seite mit den Asset-Details nicht über den interaktiven Bild-Viewer sichtbar (NPR-30979).

* Es werden enorme Sling-Aufträge erstellt und das Verarbeitungsbanner wird erneut angezeigt, wenn Aktionen, die auf Assets in ausgeführt werden, an Scene7 weitergeleitet [!DNL Experience manager Assets] werden (NPR-30947).

* Beim Erstellen der Sprachkopie von Assets treten Konflikte auf, und Assets werden nicht nach Scene7 hochgeladen (NPR-30932).

* Dynamische Darstellungen, die von [!DNL Experience Manager] im [!DNL Dynamic Media]-Hybrid-Modus heruntergeladen wurden, sind beschädigt (sie sind vom Texttyp mit Inhalt &quot;Bild kann nicht gefunden werden&quot; anstelle des Bildinhaltstyps) (NPR-30876).

* [!DNL Dynamic Media] Der Arbeitsablauf für die Kodierung von Videos kann keine Miniaturansicht für das Video generieren, das in Adobe Experience Manager (CQ-4282011) vom Modus [!DNL Dynamic Media Classic] [!DNL Dynamic Media]Scene7 migriert wird.

* Bei der Migration von Assets von einer Instanz zu einer anderen mit unterschiedlichen Scene7-Firmen-IDs (CQ-4280548) wurde eine IpsApiException-Ausnahme beobachtet.

* Die 3D-Asset-Miniaturansicht ist nicht informativ, wenn ein unterstütztes 3D-Modell in integriert wird [!DNL Experience Manager] (CQ-4283701).

* Bildlaufschaltflächen werden im Viewer angezeigt, wenn ein 3D-Asset nur über wenige Ansichten verfügt (CQ-4283322).

* Falsche Höhe des Containers eines hochgeladenen 3D-Modells, das auf der Seite &quot;Asset-Details&quot;in der Vorschau in DimensionalViewer angezeigt wird (CQ-4283309).

* Videos können nicht mit SmartCropVideoViewer in Internet Explorer 11 und Safari wiedergegeben werden (CQ-4281422).

* Die Verwendung der Schaltfläche &quot;Verschieben&quot;zum Verschieben mehrerer Assets von einem Ordner in einen anderen schlägt bei der [!DNL Experience Manager] Ausführung des [!DNL Dynamic Media]Scene7-Ausführungsmodus fehl (CQ-4280384).

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

* Bei der [!DNL Experience Manager] Abfrage nach Auftragsdetails eines Assets wird eine Ausnahme angezeigt (CQ-4283569).

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

* Das Kontrollkästchen &quot;Alle auswählen&quot;ist in der Ansicht &quot;Liste&quot;auf der Benutzeroberfläche [!DNL Sites] (NPR-31614) ausgeblendet.

* Die Zählung &quot;Alle auswählen&quot;auf einer Suchergebnisseite ist nicht korrekt (NPR-31120).

* Der Metadaten-Editor zeigt Tags an, die nicht vorhanden sind (NPR-31119).

### Übersetzung {#translation}

* Bei Auswahl der Option &quot;Fälliges Datum&quot;in einem Übersetzungsauftrag (NPR-31270) werden zwei Kalender-Popups angezeigt.

### Plattform {#platform}

* Die Option &quot;Mime-Typ&quot;in der Webkonsole funktioniert nicht (NPR-31108).

* Das Clientzertifikat wird beim Konfigurieren des Single Sign-On (NPR-31165) nicht akzeptiert.

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Dienst werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt orderby ``fn:name()`` in xpath-Abfragen (NPR-31322).

* Duplikat Aktivierung Baum wird bei der Aktualisierung von [!DNL Experience Manager] 6.3 (NPR-31513) erstellt.

* Bei weitergeleiteten Anforderungen werden keine Antwortheader beibehalten, die während der Sling-Authentifizierung festgelegt werden (NPR-30013).

* Die Suche innerhalb der Picker-Komponenten funktioniert nicht (NPR-31692).

* Beim Anhängen einer ZIP-Datei an einen [!DNL Experience Manager Communities] Beitrag wird aufgrund verschiedener Versionen von Apache POI und Apache Tika Bundle (NPR-31018) ein Fehler angezeigt.

* Das ``org.apache.sling.distribution.api`` Bundle ist im Konfigurationsmanager ausgeblendet und steht daher nicht für benutzerdefinierte Bundles (NPR-31720) zur Verfügung.

### Projekte {#projects}

* Das Wechseln von Kalendereinstellungen funktioniert nicht (NPR-31271).

### Brand Portal {#assets-brand-portal}

**Produktverbesserungen**

* Der Workflow zum Importieren von Assets in [!DNL Experience Manager Assets] wird geändert, um nur die neu erstellten Assets von [!DNL Brand Portal] zu abzurufen [!DNL Experience Manager]und die bereits im Ordner &quot;NEW&quot;vorhandenen Assets zu überspringen, um eine Replizierung zu vermeiden (CQ-4278527).

**Fehlerkorrekturen**

* Beim Erstellen eines neuen Beitragsordners in der Asset-Sourcing-Funktion (CQ-4282825) wird ein falsches Symbol angezeigt.
* Beim Erstellen eines neuen Beitragsordners werden ein oder beide Unterordner (NEU und FREIGEGEBEN) nicht im Beitragsordner (CQ-4282424) angezeigt.
* Das System gibt eine Ausnahme aus, wenn der Benutzer versucht, den Beitragsordner von [!DNL Experience Manager] zu [!DNL Brand Portal] [!DNL Brand Portal] veröffentlichen, nachdem er neue Assets aus dem Beitragsordner erhalten hat (CQ-4279740).
* Das Erstellen eines Beitragsordners in einem Beitragsordner (verschachtelter Ordner) ist verboten, um Komplexität zu vermeiden (CQ-4278391).
* Das System gibt beim Hochladen der aus der [!DNL Brand Portal] Admin-Konsole importierten Liste (.csv) eine Ausnahme aus [!DNL Experience Manager] . Nur die Felder &quot;E-Mail&quot;, &quot;Vorname&quot;und &quot;Nachname&quot;in der .csv-Datei sind obligatorisch (CQ-4278390).

### Communities {#communities}

**Fehlerkorrekturen**

* Schnelllinks zum Verwalten von Gruppen (Gruppen öffnen/bearbeiten/Veröffentlichen/Löschen) sind für Community-Administratoren nicht sichtbar (Gruppenadministrator/Site-Administrator) (NPR-31627).
* Ein gesendeter Blog wird nur angezeigt, wenn die Seite manuell aktualisiert/neu geladen wird (NPR-31599).
* Bei der von der Funktion &quot;Erwähnungen&quot;verwendeten JCR-Abfrage wird zwischen Groß- und Kleinschreibung unterschieden. Die Rückgabe der Ergebnisse dauert zu lange (NPR-31475).
* [!DNL Experience Manager] 6.5 UberJar-Datei löst Ausnahme aus, `cq-social-translation` Bundle fehlt in [!DNL Experience Manager] 6.5 UberJar-Datei (NPR-31186).
* Jackson Databind-Bibliotheken wurden auf Version 2.9.9.3 aktualisiert, um neue Schwachstellen zu beheben (NPR-30967).
* Die Titel der Aktivitäten und Benachrichtigungen sind inkonsistent (NPR-30941).
* Pagination is not working properly in [!DNL Communities] Blogs (NPR-30914).
* Analytics reports are not populated in [!DNL Experience Manager] author environment, blank page appears (NPR-30913).

### Oak {#oak}

* Aktualisierungen des Lucene-Indexes, die dazu führen, dass der Autorenserver langsamer wird (NPR-31548).

### Formulare {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. Weitere Informationen finden Sie unter [Installieren des Experience Manager Forms-Add-ons](#install-aem-forms-add-on-package) und [Installieren von Experience Manager Forms on JEE](#install-aem-forms-jee-installer).

#### Forms-Add-on-Paket {#forms-add-on-package-6530}

**Adaptive Formulare**

* Zeichenfolgen enthalten den Wörterbuchschlüssel beim Lokalisieren von adaptiven Formularen (NPR-31110).

**Interaktive Kommunikation**

* **MissingNode.toString()** gibt nach der Aktualisierung der Jackson-Bibliotheken auf 2.10.0 (NPR-31549) falsche Ergebnisse zurück.

* Der Texteditor entfernt nach dem Zufallsprinzip Leerzeichen aus dem aus Microsoft Word kopierten Text (NPR-31113).

**Korrespondenzverwaltung**

* Beschriftungen und QuickInfos werden beim Migrieren von Briefen aus LiveCycle ES4SP1 auf [!DNL Experience Manager] 6.5 (NPR-31615) nicht angezeigt.

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
>For [!DNL Experience Manager Forms] customers, it is essential to install [!DNL Experience Manager Forms] add-on package after installing any [!DNL Experience Manager] Service Pack, Cumulative Fix Pack, or Feature Pack.

#### Forms – Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Forms-Unterstützung für Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0

[!DNL Adobe Experience Manager] 6.5.2.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit von [!DNL Adobe Experience Manager] 6.5 im **April 2019** veröffentlicht wurden. It can be installed on top of [!DNL Experience Manager] 6.5.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.3 aktualisiert.
* Added a configuration property to allow exporting Experience Fragments directly to user-defined workspaces for [!DNL Adobe Target].
* Assets-Benutzer können nach visuell ähnlichen Bildern suchen. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Siehe [Verwenden von Connected Assets](../assets/use-assets-across-connected-assets-instances.md).

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten.
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt.
* Optimierte [!DNL Dynamic Media] Leistung durch Verwendung von standardmäßigen Asset-Filtern für die Replikation.
* Für den Dynamic Media Scene 7-Modus (DMS7) wurden die Optionen zum Zuschneiden/Drehen von Assets wiederhergestellt.
* Es wurde eine Option zum Stummschalten von Videos beim Laden in VideoPlayer implementiert.
* Fehlerkorrektur – In der Spaltenansicht der Asset-Benutzeroberfläche werden jetzt nur noch mandantenspezifische Inhalte angezeigt.
* Fehlerkorrektur – Änderungen des Stilakkordeons wirken sich jetzt auf die Suchergebnisse aus.

### Assets {#assets}

**Produktverbesserungen**

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Hotfix für CQ-4270245. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Experience Manager Assets] Benutzer können visuell ähnliche Bilder suchen. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

**Fehlerkorrekturen**

* Von der ACP-API generierte Asset-Pfade in URL- und Ordner-Metadaten sind nicht URL-kodiert. GRANITE-26198: Hotfix für CQ-4271814
* Unzipping an archive with a folder having a percent sign (%) in its name can not be opened using [!DNL Experience Manager Assets] interface. NPR-29989: Hotfix für CQ-4270467
* Touch-Benutzeroberfläche: Im Assistenten zum Verwalten von Veröffentlichungen werden nach der Seite im Hauptteil der Beitragsanfrage Verweise hinzugefügt, wodurch alle Assets nach der Seite veröffentlicht werden. Wenn die Seite wiedergegeben wird, werden einige Assets in der Veröffentlichungsinstanz verpasst. NPR-29985: Hotfix für CQ-4270724
* Die Funktion zum Aufheben des Bezugs zwischen Assets funktioniert nicht, wenn der Name der entsprechenden Assets Sonderzeichen (URI-kodierte Zeichen) enthält. NPR-30387: Hotfix für CQ-4274446
* Beim Bearbeiten eines Inhaltsfragments wird dessen Version mit einer falschen Benutzerangabe erstellt.
* Fehler beim Erstellen von Sammlungen auf mandantenbasiertem System. NPR-30114: Hotfix für CQ-4272948
* Die Spaltenansicht der Assets-Benutzeroberfläche berücksichtigt nicht den Stammpfad des aktuellen Mandanten, sondern greift auf die DAM-Pfade aller Mandanten zu. NPR-30636: Hotfix für CQ-4275481
* Cross-Site-Scripting-Angriff (XSS) über das Fenster für die Warnmeldung zu eingeschränktem Dateizugriff möglich, da das injizierte Bild sichtbar ist. NPR-30617: Hotfix für CQ-4270133
* MultiTenant: Mandanten, die Ordnereigenschaften speichern, beachten sowohl die Erfolgsaufforderung als auch die Fehlermeldung, dass die Aktion nicht erfolgreich war: &quot;Eigenschaften können nicht bearbeitet werden. unzureichenden Berechtigungen nicht geändert werden konnten, was für Verwirrung sorgt. NPR-30545: Hotfix für CQ-4275333
* Im Asset-Auswahldialog lässt sich keine Asset auswählen und somit auch nicht die Funktion zum Ersetzen der zugehörigen Quelle verwenden, um die Quelle zu aktualisieren. NPR-30502: Hotfix für CQ-4275029
* [!UICONTROL DAM Update Asset] Workflow - Im statischen Zustand beim Hochladen großer MP4-Dateien. NPR-30480: Hotfix für CQ-4271352
* Die Funktion zum Erstellen von Prüfungsaufgaben schlägt aufgrund nicht vorhandener Nutzdaten fehl, was entsprechend auch alle nachfolgenden Aktionen im Zusammenhang mit Prüfungsaufgaben fehlschlagen lässt. NPR-30468: Hotfix für CQ-4274263
* Problem bei der Verbindung mit Adobe Smart-Tag über DataPower. NPR-30026: Hotfix für CQ-4269457
* Die Spaltenansicht der Assets-Benutzeroberfläche löst einen Fehler aus, wenn versucht wird, die Filter links von der Leiste zu öffnen. NPR-30501: Hotfix für CQ-4273862
* Wenn Gruppen hinzugefügt werden, die über LDAP in den Eigenschaften der geschlossenen Benutzergruppe eines Asset-Ordners synchronisiert wurden, wird die Gruppe nicht gespeichert und abgerufen. NPR-30615: Hotfix für CQ-4274689
* In den Feldern zum Filtern der Suche nach Stil und Ausrichtung wird der automatisch vervollständigte Wert nicht auf die Suchanfrage angewendet. NPR-30620: Hotfix für CQ-4275724
* Enthält der Name eines Ordners Leerzeichen und das Zeichen „&amp;“, zeigt der ihm zugehörige Asset-Freigabe-Link bei einigen Assets leere graue Karten an. NPR-30557: Hotfix für CQ-4270187
* Das Metadatenschemaformular für Ordner erkennt den Datentyp nicht automatisch, was zur Folge hat, dass es bei der Formularübermittlung den zugehörigen TypeHint nicht erstellt. NPR-30599: Hotfix für CQ-4275227
* In der Autoren-Benutzeroberfläche für DMS7 sind die Optionen zum Zuschneiden und Drehen von Assets deaktiviert. NPR-30118: Hotfix für CQ-4273221
* Share Link feature is not working on [!DNL Experience Manager] instance with DMS7 configuration. NPR-30080, NPR-30492: Hotfix für CQ-4273651
* Adding the [!DNL Dynamic Media]–Scene7 component to the page, and then publishing the page does not trigger the dmscene7 configuration every time. NPR-30641: Hotfix für CQ-4275962
* Added an IPSJobJournal in [!DNL Experience Manager] to create only one Intrusion Prevention Systems (IPS) job per processing profile. NPR-30490: Hotfix für CQ-4273614
* [!DNL Dynamic Media]: Es wurden Standard-Filter hinzugefügt, um Assets von der Replizierung auf den [!DNL Experience Manager] Veröffentlichungsknoten auszuschließen. NPR-30538: Hotfix für CQ-4274678
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt, der die Nutzung von Ordnern als Nutzlast ermöglicht. Der Workflow umfasst zwei Schritte: Die erneute Verarbeitung von Assets ohne Handles erfolgt über die Zuordnung von Metadaten zum nächsten Schritt, das erneute Hochladen aller Assets ohne Asset-Handle zu S7 dann in einem einzelnen IPS-Auftrag. For more details, see Configuring [!DNL Dynamic Media] Cloud Services. NPR-30489: Hotfix für CQ-4272903
* Wird nach der korrekten CSV-Datei eine falsche CSV-Datei hochgeladen, wird die korrekte CSV-Datei gelöscht. Hotfix für CQ-4277694, CQ-4277814
* Falsches Symbol für die zu entfernenden Beitragsordner. Hotfix für CQ-4277580
* Wird über die Benutzerauswahl auf der Registerkarte für Asset-Beiträge ein Benutzer ausgewählt, erscheint dessen Name nicht in der Tabelle, und auf der Eigenschaftenseite wird im Dialogfeld zum Löschen von Benutzern falscher Text angezeigt. Hotfix für CQ-4277875
* Mitwirkende können dem Asset-Beitragsordner nicht hinzugefügt werden, indem diese über die Benutzerauswahl ausgewählt werden und auf die Schaltfläche „Hinzufügen“ geklickt wird. Hotfix für CQ-4277824, CQ-4278087
* In der Benutzerauswahl funktioniert die Suche nach Benutzernamen in Kleinbuchstaben nicht. Hotfix für CQ-4277958, CQ-4277930
* Benutzer ohne Administratorrechte können Assets in einem neuen Ordner eines Asset-Beitragsordners veröffentlichen. Hotfix für CQ-4278200
* Für DAM-Benutzer (ohne Administratorrechte) besteht keine Möglichkeit, dem Asset-Beitragsordner Mitwirkende hinzuzufügen. Hotfix für CQ-4278192
* Im Asset-Beitragsordner ist die Schaltfläche „Erstellen“ sichtbar. Hotfix für CQ-4277560
* Sorting search query by relevance returns [!DNL InDesign] documents along with [!DNL InDesign] templates. Hotfix für CQ-4273864
* Wenn der Benutzer über eine E-Mail-ID in Großbuchstaben verfügt, können die Benutzer nicht für die zuvor ausgecheckten Assets einchecken. Hotfix für CQ-4276575
* Der Löschvorgang gilt nur für die ausgewählten Vorgaben. Wenn der Bildschirm die Liste nach dem Vorgang automatisch aktualisiert, werden andere Vorgaben angezeigt, die bereits aktualisiert wurden. Hotfix für CQ-4261461
* Configuring [!DNL Dynamic Media] Cloud Services in [!DNL Dynamic Media]–Hybrid mode results in multiple empty report suites created in [!DNL Analytics], and with no report suite id stored in [!DNL Experience Manager], resulting in report suite duplication. Hotfix für CQ-4249780
* Rename operation in [!DNL Experience Manager] asset to duplicated name fails to synchronize to Scene7. Hotfix für CQ-4276763
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
* Closing [!DNL Experience Manager Assets] Search UI does not reset the left rail to Content selection preventing the user from opening the filter rail the second time subsequently. NPR-30509: Hotfix für CQ-4274716
* Multi-tenant environment: [!DNL Experience Manager Assets] UI top navigation is not available and throwing JavaScript error. NPR-30104: Hotfix für GRANITE-26344

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

### Integration {#integration}

* Angepasster Content wird auf der Veröffentlichungsinstanz erst nach dem Neustart der Instanz korrekt angezeigt. NPR-30377: Hotfix für CQ-4273706
* Bei der Konfiguration von Launch auf einer Website wird der Bibliotheksadresse ein Schrägstrich (/) vorangestellt, der jedes Mal einen manuellen Eingriff verursacht. NPR-30694: Hotfix für CQ-4275501

### Formulare {#forms-6520}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. They are delivered using a separate [!DNL Forms] add-on package. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. For more information, see [Install Experience Manager Forms add-on](#install-aem-forms-add-on-package) and [Install Experience Manager Forms JEE installer](#forms-jee-installer).

The key highlights for [!DNL Experience Manager] 6.5.2.0 forms are:

* Added &#39;Auto&#39; setting to `RenderAtClient` in `PDFFormRenderOptions` API for [!DNL Experience Manager] Forms OSGi.

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
* Adding or editing a Web Service connection by invoking web services from [!DNL Experience Manager Forms] Workbench throws an error: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix für CQ-4273217

### Enthaltene Feature Packs {#feature-packs-included}

>[!NOTE]
>
>For [!DNL Experience Manager Forms] customers, it is essential to install [!DNL Experience Manager Forms] add-on package after installing any [!DNL Experience Manager] Service Pack, Cumulative Fix Pack, or Feature Pack.

#### Sites {#sites-feature-packs-included}

* Added a configuration property to allow exporting Experience Fragments directly to user-defined workspaces for [!DNL Adobe Target]. NPR-29189: Hotfix für CQ-4249782

#### Forms - Document Services {#forms-document-services-1}

* Die Einstellung &quot;Auto&quot;wurde `RenderAtClient` in der `PDFFormRenderOptions` API für [!DNL Experience Manager Forms] OSGi hinzugefügt. NPR-30759: Hotfix für CQ-4278193

## Adobe Experience Manager 6.5.1.0 {#release-6510}

[!DNL Adobe Experience Manager] 6.5.1.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit von [!DNL Adobe Experience Manager] 6.5 im *April 2019 veröffentlicht wurden.*[!DNL Experience Manager] Sie kann auf  6.5 installiert werden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Dynamische Benutzeroberflächenstatus können jetzt als benutzerdefinierte Attribute in Tracking-Ereignisse einbezogen werden.
* Included support for the delivery of 360-degree video assets in [!DNL Dynamic Media]–Scene7 mode.
* Enabled *Japanese Word Wrap* feature via the styles plugin of Rich Text Editor. Weitere Informationen finden Sie unter [Konfigurieren von japanischen Wortumbrüchen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Assets 

* Die DAM DMGGateway-Schnittstelle bietet jetzt Unterstützung für S3-Multipart. NPR-29740: Hotfix für CQ-4226303
* Renditions preview generates `Only empty tenantId is currently supported` error after upgrading to [!DNL Experience Manager] 6.5. NPR-29986: Hotfix for CQ-4272353
* Da das Dialogfeld „Löschen“ nicht sichtbar ist, können Aufträge nicht gelöscht werden. NPR-29720: Hotfix für CQ-4271074
* After adding asset title in the properties page, when a user attempts to close the page, [!DNL Experience Manager] opens the properties page again. NPR-29627: Hotfix für CQ-4264929
* VersioningTimelineEventProvider sollte die Stammversion zusammen mit dem Knoten des Typs „nt: version“ bereitstellen. Hotfix für GRANITE-26063
* Implemented the ability to upload and play 360 spherical videos in [!DNL Experience Manager] DM-Scene7 mode. Hotfix für CQ-4265131
* Wird bei einer Live Copy die Quelle bearbeitet, wird der falsche Status abgerufen. Hotfix für CQ-4265451
* Multi-Site-Manager bietet jetzt Unterstützung für [!DNL Experience Manager Assets]. Hotfix für CQ-4271453, CQ-4268621, CQ-4257491
* [!DNL Experience Manager] -Schnittstelle sollte einen zusätzlichen Eintrag für die aktuelle Version des Assets im Zeitschienenverlauf anzeigen, in dem der neueste Eincheckkommentar angezeigt wird [!DNL Adobe Asset Link]. Hotfix für CQ-4262864
* In der Zeitleiste des Inhaltsfragments wird eine Fehlermeldung angezeigt, wenn Eigenschaften fehlen. Hotfix für CQ-4272560
* Problem mit dem Scene7-Videoplayer, wenn er auf den Vollbildmodus erweitert wird. Hotfix für CQ-4266700
* Viewer für vertikalen Zoom: Die Schwenken-Schaltflächen sollten nicht angezeigt werden, wenn ein einzelnes Bild-Asset verwendet wird. Hotfix für CQ-4264795
* Durch das Löschen eines untergeordneten Knotens in einer Live Copy sollte die LiveRelationship getrennt werden. Hotfix für CQ-4270395
* Das Metadatenschema enthält nur Elemente aus der globalen Konfiguration und nicht die Elemente aus dem aktiven Mandanten. Selbst wenn der für „formPath“ angegebene URL-Wert geändert wird, wird er auf den Standardwert zurückgesetzt. NPR-29945: Hotfix für CQ-4262898
* Publish image presets to [!DNL Brand Portal] fails with 500 error code. NPR-29510: Hotfix für CQ-4268659

### Sites

* Beim Rollout werden leere Eigenschaften ebenso wie mehrere Eigenschaften von der Blueprint nicht übernommen. Das Zurücksetzen der Live Copy auf den Status der Blueprint funktioniert nicht für Komponenten. NPR-29253: Hotfix für -4264928, CQ-4264926, CQ-4267722
* CoralUI, when used with `Multifield`, stores the `fileReferenceParameter` at the component level instead of multifield level. NPR-29537: Hotfix für CQ-4266129
* Enhancement of [!DNL Experience Manager] text component and Text Editor to Japanese. NPR-29785: Hotfix für CQ-4265090
* Eine mithilfe von Timewarp wiederhergestellte Seite sollte zum Zeitpunkt der Versionierung auf das korrekte Bild verweisen. NPR-29431: Hotfix für CQ-4262638
* Ein Problem mit der Vererbung von Style System-Knoten von übergeordneter zu untergeordneter Ebene. NPR-29516: Hotfix für CQ-4270330
* An error message while setting up the social posting to [!DNL Facebook] authentication. NPR-29211: Hotfix für CQ-4266630
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* In der Coral2-Implementierung werden beim Öffnen der Registerkarte „Berechtigungen“ die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

### E-Commerce

* Das Ausführen einer Lazy-Content-Migration für E-Commerce löst eine ConstraintViolationException aus. NPR-29247: Hotfix für CQ-4264383

### Verwaltung von Inhaltsfragmenten

* Parsing error when opening a Content Fragment which has characters dollar `($)` and open brace `({)`. Hotfix für CQ-4270266

### Experience Fragments

* Exportieren Sie [!DNL Experience Manager] Erlebnisfragmente in [!DNL Adobe Target]. Hotfix für CQ-4265469
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

* Upgrade to [!DNL Experience Manager] 6.4.3 makes Multi-Site Manager take a long time to roll out. Hotfix für CQ-4271410

### Integration

* Anmeldeversuche mit den BrightEdge-Anmeldeinformationen schlagen mit einem Verbindungsfehler fehl. NPR-29168: Hotfix für CQ-4265872

* An exception message is displayed when trying to edit and save the [!DNL Experience Manager] launch configuration. NPR-29176: Hotfix für CQ-4265782/CQ-4266153

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

* Publish [!DNL Experience Manager Assets] from [!DNL Experience Manager] Author /content/dam/mac folder to [!DNL Brand Portal] doesn&#39;t work. NPR-29819: Hotfix für CQ-4271118

### Plattform

* HTMLLibraryManager löscht bei der Cache-Invalidierung alle Inhalte von crx-quickstart. NPR-29863: Hotfix für GRANITE-26197

### Felix

* Bei Verwendung von Java11 werden in der Systemkonsole keine Details zur Speichernutzung angezeigt\. NPR-29669

### Forms

The key highlights for [!DNL Experience Manager Forms] 6.5.1.0 are:

* OSGi only: Added a new attribute `PAGECOUNT` in Output and Forms Service.

* Nur OSGI: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert.
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert.
* Es wurde Unterstützung für die On-Premise-Integration von ADFS 3.0 für Dynamics ergänzt.

#### Forms-Add-On-Paket

**Backend-Integration**

* Fehler beim Abrufen von geschützter WSDL (Web Service Definition Language). NPR-29944: Hotfix für CQ-4270777
* When [!DNL Experience Manager Forms]  is installed on IBM WebSphere, creating a form data model based on SOAP fails. Hotfix für CQ-4251134
* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. Hotfix für CQ-4270586
* Wenn der Titel einer Datenquelle geändert wird, zeigt das Formulardatenmodell den aktualisierten Titel nicht an. Hotfix für CQ-4265599
* Wenn der Name einer Entität oder eines Attributs Bindestriche oder Leerzeichen enthält, können Ausdruck diese Entitäten und Attribute nicht auswerten. Hotfix für CQ-4225129

* Falsche Ausgabe wird beobachtet, wenn ein Doppelpunkt in der Ausgabe der Primitive-Zeichenfolge vorhanden ist. Hotfix für CQ-4260825

* Auch wenn von der REST-API-Ausgabe kein Inhalt erwartet wird, löst der Aufrufvorgang des Formulardatenmodells einen Fehler aus. Hotfix für CQ-4268828

**Adaptive Formulare**

* Während des Lazy-Loading-Vorgangs kann im adaptiven Formularfragment keine neue Instanz hinzugefügt werden. NPR-29818: Hotfix für CQ-4269875
* Bei Vorlagen für Datensatzdokumente (Document of Record, DoR) protokolliert die Überprüfungskomponente keinerlei Fehler, noch zeigt sie Fehler an. Hotfix für CQ-4272999
* Unterstützung zum Deaktivieren des Layout-Editors für adaptive Formulare hinzugefügt. Hotfix für CQ-4270810
* Restored the verify step for Adaptive Forms in [!DNL Experience Manager] 6.5. Hotfix for CQ-4269583

* Adaptive Form field validation failure breaks [!DNL Adobe Sign]. Hotfix für CQ-4269463
* When an [!DNL Experience Manager Forms] instance has more than 20 adaptive form fragments and name of all the form fragments starts with the same string, the search returns no or only recent 20 created fragments. Hotfix für CQ-4264414, CQ-4264914

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
* When an image of more than 2 MB is attached as a field level attachment to a form in the Android version of [!DNL Experience Manager Forms] app, the app crashes. Hotfix für CQ-4265578

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

* [!DNL Experience Manager Forms] 6.5 Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) kann Korrespondenz, die mit [!DNL Experience Manager Forms] 6.3 erstellt wurde, nicht öffnen. Hotfix für CQ-4266392
* Die Summenfunktion in XDP funktioniert nicht, wenn die Datenwörterbuchelemente Daten vom Typ „Zahl“ enthalten. Hotfix für CQ-4227403
* Die Invalidierungslogik des Arbeitsspeichercaches für Briefe muss aktualisiert werden, da beim Veröffentlichen eines Assets die Zeit seiner letzten Änderung nicht aktualisiert wird. Hotfix für CQ-4250465
* Dokumentfragment, Datenwörterbuch und Briefe können nicht veröffentlicht werden. Hotfix für CQ-4272893

#### Forms JEE-Installationsprogramm

**PDF Generator**

* Die Konvertierung von CAD- in PDF-Dateien schlägt mit dem 64-Bit-JDK fehl. NPR-29924, NPR-29925: Hotfix für CQ-4272113
* Die Bezeichnung „HTML-in-PDF“ für die entsprechende Konvertierung mit PhantomJS wurde durch „Web-in-PDF“ ersetzt. NPR-29933: Hotfix für CQ-4234545
* Beim Konvertieren einer ZIP- in eine PDF-Datei wird ein Fehler ausgegeben. Hotfix für CQ-4268628

**Forms – Designer**

* When a full accessibility check is performed on the static PDF created using [!DNL Experience Manager Forms Designer], the Primary Language check fails due to missing language attribute. Hotfix für CQ-4272923, CQ-4271002

**Forms - Document Security**

* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten OSGi-Installationen nicht mit Java 11 und Java 8\. NPR-29838: Hotfix für CQ-4270441
* Die digitale Signatur mit dem Hardware-Sicherheitsmodul (HSM) funktioniert auf Linux-basierten JEE-Installationen sowie allen unterstützten Anwendungsservern, d. h. JBoss und Websphere, nicht. NPR-29839: Hotfix für CQ-4266721
* Beim Überprüfen der Signaturen in einer PDF-Datei mit PAdES (PDF Advanced Electronic Signatures) wird eine InvalidOperationException generiert. NPR-29842: Hotfix für CQ-4244837
* Unterstützung für Dokument Security Extension für Office 2019\ hinzugefügt. Hotfix für CQ-4254369, CQ-4259764

**Forms - Document Services**

* PDF-Konvertierung in PDF/A-1b mit Formularfeld hat kein Erscheinungsbild-Diktat. NPR-29940: Hotfix für CQ-4269618

* OSGi: Die Anzahl der beim Rendern generierten Seiten kann nicht ermittelt werden. NPR-28922: Hotfix für CQ-4270870
* Unterstützung für statische PDF-Dateien mit dem Forms-Dienst in aktiviert [!DNL Experience Manager Forms OSGi]. NPR-28572: Hotfix für CQ-4270869
* Die Berechtigungen für die Datei XMLForm.exe können nicht geändert werden. NPR-29828, NPR-29237: Hotfix für Q-4267080
* The static PDF created by the [!DNL Experience Manager Forms] server’s output module does not populate the language attribute/tag with the language of the document created. NPR-27332: Hotfix für CQ-4271002

**Forms – Foundation JEE**

* Aufgrund eines im finalen Artefakt nicht verfügbaren pdfg_srt schlägt das Installationsprogramm fehl. NPR-29854: Hotfix für CQ-4270137
* LCBackupMode.sh funktioniert nicht. NPR-29840: Hotfix für CQ-4269424
* Die UDP-Portreferenz sollte für WebSphere aus der Benutzeroberfläche entfernt werden. Hotfix für CQ-4264782

### Enthaltende Feature Packs

#### Assets - einschließlich

* Multi-Site-Manager bietet jetzt Unterstützung für [!DNL Experience Manager Assets]. For more information, see [Reuse assets using MSM for Experience Manager Assets](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html). NPR-29199: Hotfix für CQ-4259922

#### Sites - Einbezogen

* Exportieren Sie [!DNL Experience Manager] Erlebnisfragmente in [!DNL Adobe Target]. For more details, see [The Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix für CQ-4265469

#### Forms – Dokumentendienste - Einbezogen

* Nur OSGi: Es wurde ein neues Attribut PAGECOUNT im Output- und Forms-Dienst hinzugefügt. NPR-28922: Hotfix für CQ-4270870
* Nur OSGi: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert. NPR-28572: Hotfix für CQ-4270869
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert. NPR-29237: Hotfix für CQ-4267080

### OSGi-Bundles und Inhaltspakete

The following text documents list the OSGi bundles and Content Packages included in [!DNL Experience Manager] 6.5.1.0

List of OSGi bundles included in [!DNL Experience Manager] 6.5.1.0

[Datei laden](assets/6_5-bundle-list.txt)

List of Content Packages included in [!DNL Experience Manager] 6.5.1.0

[Datei laden](assets/6_5-content-package-list.txt)
