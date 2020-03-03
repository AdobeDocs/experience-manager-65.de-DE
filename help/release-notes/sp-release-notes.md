---
title: Versionshinweise zum AEM 6.5 Service Pack
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Service Pack 3.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: 9f4a460c7f64d86e35e950e512ed5b6cda1cbf2a

---


# Versionshinweise zu Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager 6.5** |
|---|---|
| Version | 6.5.3.0 |
| Typ | Service Pack-Version |
| Datum | 12. Dezember 2019 |
| Download-URL | [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.3.0) |

## Inhalt von Adobe Experience Manager 6.5.3.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.3.0 is an important release that includes performance, stability, security, and key customer fixes and enhancements released since the general availability of 6.5 release in **April 2019**. Es kann über Adobe Experience Manager (AEM) 6.5 installiert werden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.6 aktualisiert.

* Experience Manager Assets unterstützt jetzt ZIP-Archive, die mit dem Deflate 64-Algorithmus erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Listenansicht und in den Asset-Suchergebnissen in der Listenansicht hinzugefügt.

* Die Sortierung von Assets basierend auf der Spalte Name wurde in der Listenansicht aktiviert.

* Dynamische Medien unterstützen jetzt Smart-Zuschneiden von Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen.

* Dynamische Medien unterstützen Smart Imaging.

* Möglichkeit zum [Festlegen von Abwesenheitseinstellungen](../forms/using/configure-out-of-office-settings.md) in AEM-Workflows.

* Möglichkeit, Inbox- oder Inbox-Elemente[ für andere Benutzer in AEM-Workflows zu ](../forms/using/configure-shared-queues-osgi.md)freigeben.

* Möglichkeit, interaktive Kommunikation im Stapelmodus zu [generieren](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

* Die Version von jQuery im Paket ContextHub wurde auf 3.4.1 aktualisiert.

### Liste der Änderungen   {#list-of-changes}

#### Assets {#assets-6530-enhancements}

**Produktverbesserungen**

* Experience Manager Assets unterstützt jetzt ZIP-Archive, die mit dem Deflate 64-Algorithmus (NPR-27573) erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Listenansicht und in den Asset-Suchergebnissen in der Listenansicht hinzugefügt (NPR-31312).

* Asset-Sortierung basierend auf der Spalte &quot;Name&quot;wurde in der Listenansicht zugelassen (NPR-31299).

* Die Asset-Dateien GLB, GLTF, OBJ und STL unterstützen die Asset-Vorschau auf der Seite &quot;Asset-Details&quot;in DAM (CQ-4282277).

* Das ReplicationOnModifyListener-Ereignis wird beim Hochladen von Chunk-Knoten in dynamischen Medien (CQ-4281279) ausgelöst.

* Dynamische Medien unterstützen jetzt Smart-Zuschneiden von Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen (CQ-4278995).

* Dynamic Media unterstützt Smart Imaging (CQ-4222249).

* Die Such-/Durchsuchen-Ansicht wurde als Standardansicht in der Foundation-Auswahl festgelegt, wenn Abfrageparameter in einer Anforderung übergeben werden (NPR-31601).

**Fehlerkorrekturen**

* Metadaten für einige PDF-Dokumente werden beim Ändern des Titels (NPR-31629) nicht aktualisiert und im PDF gespeichert.

* Asset Sharing funktioniert nicht für Assets, deren Name das Zeichen &quot;+&quot;enthält (NPR-31547).

* Änderungen im Standardsuchformular Assets Admin * Suchleiste funktionieren nicht wie erwartet (NPR-31502).

* Vorschläge werden nicht angezeigt, wenn Sie Omniture Search für die Asset-Ansicht zum Durchsuchen von Assets verwenden (NPR-31496).

* Asset-Verweise in Sammlungen werden nicht aktualisiert, wenn die referenzierten Assets an einen anderen Speicherort verschoben werden, sofern dieselben Assets von verschiedenen Benutzern durch unterschiedliche Sammlungen referenziert werden (NPR-31486).

* Duplizierte IPTC-Tags werden zu Asset-Metadaten hinzugefügt (NPR-31328).

* Die Suchergebnisanzahl in der oberen rechten Ecke wird nicht korrekt aktualisiert, wenn die Suche über die Filterleiste ausgelöst wird (NPR-31316).

* Alle Kontrollkästchen werden deaktiviert, wenn die Kontrollkästchen der zweiten Ebene im Filter &quot;Dateityp&quot;deaktiviert werden, und der Text in der Suchleiste ist nicht mit den ausgewählten/nicht ausgewählten Eigenschaften synchronisiert (NPR-31287).

* Alle Mitglieder (Benutzer/Gruppen) können nicht aus dem Abschnitt &quot;Mitglieder&quot;eines Ordners entfernt werden. beim Versuch, alle Benutzer zu entfernen, wird der angemeldete Benutzer zur Liste hinzugefügt (NPR-31171).

* Assets mit dem Pluszeichen &quot;+&quot;im Dateinamen können nicht gelöscht werden (NPR-31162).

* Dropdown-Menü erstellen, das im oberen Menü bei Auswahl eines Ordners angezeigt wird, zeigt nicht &quot;Ordner&quot; als Erstellungsoption (NPR-30877).

* Ordnerauswahl &quot;Erstellen&quot;> &quot;DateiUpload&quot;-Aktionselement fehlt, wenn ACL für &quot;Ablehnen&quot;(jcr:removeChildNodes) und &quot;jcr:removeNode&quot;auf Pfad für einen Benutzer angewendet werden (NPR-30840).

* DAM-Workflows werden beim Hochladen bestimmter MP4-Assets in den Status &quot;Stall&quot;versetzt, sodass alle verbleibenden Workflows in den Status &quot;Stall&quot;wechseln (NPR-30662).

* Fehler wegen ungenügenden Speicherplatzes werden beobachtet, wenn große PDF-Dateien (mit mehreren Gigabytes) zu DAM hochgeladen und deren Teilassets verarbeitet werden (NPR-30614).

* Die Massenbewegung von Assets schlägt fehl und es wird eine Warnmeldung angezeigt (NPR-30610).

* Beim Verschieben von Assets aus einem Ordner in einen anderen in AEM, das im Dynamic Media Scene7-Runmode ausgeführt wird (NPR-31630), werden die Asset-Namen in Kleinbuchstaben geändert.

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler festgestellt, da sich das Bild im Ordner befindet, der mit dem Namen des Scene7-Unternehmens identisch ist (NPR-31340).

* Dynamische Medienelemente, die Verweise enthalten, werden nicht veröffentlicht (NPR-31180).

* Uploads von AEM Dynamic Media - Scene7-Runmode zu Scene7 dauern zu lange, bis sie abgeschlossen sind (NPR-31048).

* Hotspot, der zu einem Bild-Asset hinzugefügt wurde, ist auf der Seite mit den Asset-Details nicht über den interaktiven Bild-Viewer sichtbar (NPR-30979).

* Es werden enorme Sling-Aufträge erstellt und das Verarbeitungsbanner wird erneut angezeigt, wenn Aktionen, die in AEM Assets ausgeführt werden, an Scene7 (NPR-30947) übergeben werden.

* Beim Erstellen der Sprachkopie von Assets treten Konflikte auf, und Assets werden nicht nach Scene7 hochgeladen (NPR-30932).

* Dynamische Darstellungen, die von AEM heruntergeladen wurden und im Dynamic Media Hybrid-Modus ausgeführt werden, sind beschädigt (sie sind vom Texttyp mit Inhalt, der &quot;Bild kann nicht gefunden werden&quot;anstelle des Bildinhaltstyps) (NPR-30876).

* Der Arbeitsablauf für die Videokodierung mit dynamischer Medienkodierung kann keine Miniaturansicht für das Video generieren, das aus Scene7 in den Modus für die Ausführung von Scene7 migriert wird (CQ-4282011).

* Bei der Migration von Assets von einer Instanz zu einer anderen mit unterschiedlichen Scene7-Unternehmens-IDs wurde eine IpsApiException beobachtet (CQ-4280548).

* Die Miniaturansicht von 3D-Assets ist nicht informativ, wenn ein unterstütztes 3D-Modell in AEM integriert wird (CQ-4283701).

* Bildlaufschaltflächen werden im Viewer angezeigt, wenn ein 3D-Asset nur über wenige Kameraansichten verfügt (CQ-4283322).

* Falsche Behälterhöhe eines hochgeladenen 3D-Modells, das auf der Seite &quot;Asset-Details&quot;im DimensionalViewer in der Vorschau angezeigt wird (CQ-4283309).

* Videos können nicht mit SmartCropVideoViewer in Internet Explorer 11 und Safari wiedergegeben werden (CQ-4281422).

* Die Verwendung der Schaltfläche zum Verschieben, um mehrere Assets von einem Ordner in einen anderen zu verschieben, schlägt in AEM, das auf Dynamic Media - scene7 ausgeführt wird, fehl (CQ-4280384).

* Verzerrtes Video wird in Asset-Details angezeigt, wenn der MIME-Typ nicht MP4 ist (CQ-4279704).

* Videos, die neu in Ordnern mit Videoprofil aufgenommen wurden, bleiben auch nach Abschluss der Kodierung auf 100 % im Verarbeitungszustand (CQ-4279389).

* Durch das Verschieben von Assets aus einem Ordner werden zahlreiche Sling-Aufträge (Scene7-API-Aufrufe) generiert, die im Idealfall erforderlich sind (CQ-4278664).

* Die Namen des Bildsatzes werden in Scene7 in Kleinbuchstaben geändert, wenn Bildsatz (oder Mediaset) erstellt und mit einer entsprechenden Benennungskonvention in DAM (CQ-4281112) benannt wird.

* Scene7 Migrator stellt den Veröffentlichungsstatus falsch ein (CQ-4263492).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers in Inhaltsfragmenten (CQ-4282898).

* PDF-Dateien werden nicht indiziert und der Inhalt in ist nicht durchsuchbar (CQ-4278916).

* Fehler &quot;Gruppe nicht nach Benutzerauswahl aufgeführt: &quot;false to equal true&quot;wird beim Hinzufügen von &quot;Closed User Group&quot;mit &quot;different&quot; `principalName` und `authorizableId` (CQ-4278177) beobachtet.

* Die Ansicht &quot;Assets UI-Spalte&quot;zeigt alle Pfade unabhängig vom Pfad des Stammordners (CQ-4278175) an.

* Die Suche der Asset-Auswahl funktioniert nicht wie erwartet (CQ-4275886).

* Darstellungs-Workflows funktionieren nicht (CQ-4271928).

* DAM Event Purge löscht die neuesten (maxSavedActivities) Ereignisdaten und speichert die zuvor erstellten Daten (NPR-31336).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Die Aktionsleiste und die Asset-Anzahl werden nicht aktualisiert, wenn Sie alle Elemente auswählen und dann die Auswahl einiger Elemente (Ordner/einzelne Assets) in der Touch-Benutzeroberfläche (NPR-31118) aufheben.

* Während der Abfrage nach Auftragsdetails eines Assets (CQ-4283569) wird in AEM eine Ausnahme angezeigt.

* XSS-Schwachstelle in DAM (NPR-31654).

#### Sites {#sites}

* Wenn die LiveCopy-Vererbung beschädigt ist, werden auf Live-Kopierseiten anstelle von LiveCopy-Links Sprachkopie-Links angezeigt (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).
* Wenn ein Benutzer japanische oder koreanische Zeichen in die Eigenschaft description eines Menüs einfügt, werden im Menü verzerrte Zeichen für japanischen und koreanischen Text angezeigt. (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Tabelle als Listenelement einzufügen (NPR-30879).
* Standardmäßig wird der RTE-Editor (RTE) mit Gerüsten versehen. wendet die Inline-Schriftgröße unerwartet auf Elemente an (NPR-31284).
* Wenn ein Benutzer sich auf Felder in der linken Schiene konzentriert und zum Einfügen von Inhalten einen Tastaturbefehl verwendet, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31172).
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Multifeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten (NPR-30882) gespeichert.
* Die ResponsiveGridExporter-API gibt die com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter-Schnittstelle nicht zurück. Das Paket com.day.cq.wcm.foundation.model.impl wird als privates Paket deklariert (NPR-31398).
* Wenn eine Seite mit ExperienceFragments im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das `editor.html` Präfix und `wcmmode=disabled`im Publisher)., endet die Anforderung im HTTP-Statusfehlercode 500 (NPR-30743).
* Benutzer können ihr Kennwort nicht ändern und auf ihre Profilseite zugreifen (NPR-31161).
* Eine JavaScript-Datei mit Benutzerdaten wird serverseitig generiert (NPR-30822).
* Die Benutzeroberfläche für das Authoring von AEM ermöglicht Phishing mit externen Inhalten (NPR-29745).
* Sicherheitslücke beim Spritzen von Ausdruckssprachen im AEM 6.5-Metadateneditor (NPR-31017).

#### Suchen und Benutzeroberfläche {#search-ui-interface}

* Beim Wechsel von der Kartenansicht zur Listenansicht auf einer Suchergebnisseite kommt es zu einer Verzögerung, bevor ein Bildlauf der Seite durchgeführt werden kann (NPR-31286).

* Das Kontrollkästchen &quot;Alle auswählen&quot;ist in der Listenansicht der Benutzeroberfläche &quot;Sites&quot;ausgeblendet (NPR-31614).

* Die Zählung Alle auswählen auf einer Suchergebnisseite ist nicht korrekt (NPR-31120).

* Der Metadaten-Editor zeigt Tags an, die nicht vorhanden sind (NPR-31119).

#### Übersetzung {#translation}

* Bei Auswahl der Option &quot;Fälliges Datum&quot;in einem Übersetzungsauftrag (NPR-31270) werden zwei Kalender-Popups angezeigt.

#### Plattform {#platform}

* Die Option &quot;Mime-Typ&quot;in der Webkonsole funktioniert nicht (NPR-31108).

* Das Clientzertifikat wird beim Konfigurieren des Single Sign-On (NPR-31165) nicht akzeptiert.

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Dienst werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt orderby ``fn:name()`` in xpath Abfragen (NPR-31322).

* Bei der Aktualisierung von AEM 6.3 (NPR-31513) wird eine doppelte Aktivierungsstruktur erstellt.

* Bei weitergeleiteten Anforderungen werden keine Antwortheader beibehalten, die während der Sling-Authentifizierung festgelegt werden (NPR-30013).

* Die Suche innerhalb der Picker-Komponenten funktioniert nicht (NPR-31692).

* Beim Anhängen einer ZIP-Datei an einen AEM Communities-Beitrag aufgrund verschiedener Versionen von Apache POI und Apache Tika Bundle (NPR-31018) wird ein Fehler angezeigt.

* Das ``org.apache.sling.distribution.api`` Bundle ist im Konfigurationsmanager ausgeblendet und steht daher nicht für benutzerdefinierte Bundles (NPR-31720) zur Verfügung.

#### Projekte {#projects}

* Das Wechseln von Kalenderansichten funktioniert nicht (NPR-31271).

#### Brand Portal {#assets-brand-portal}

**Produktverbesserungen**

* Der Workflow zum Importieren von Assets in AEM Assets wurde geändert, um nur die neu erstellten Assets vom Markenportal zu AEM abzurufen und die bereits vorhandenen Assets im Ordner NEW zu überspringen, um eine Replikation zu vermeiden (CQ-4278527).

**Fehlerkorrekturen**

* Beim Erstellen eines neuen Beitragsordners in der Asset-Sourcing-Funktion (CQ-4282825) wird ein falsches Symbol angezeigt.
* Beim Erstellen eines neuen Beitragsordners werden ein oder beide Unterordner (NEU und FREIGEGEBEN) nicht im Beitragsordner (CQ-4282424) angezeigt.
* System gibt eine Ausnahme aus, wenn der Benutzer versucht, den Beitragsordner von AEM in das Markenportal erneut zu veröffentlichen, nachdem er neue Assets aus dem Beitragsordner vom Markenportal-Ende (CQ-4279740) erhalten hat.
* Das Erstellen eines Beitragsordners in einem Beitragsordner (verschachtelter Ordner) ist verboten, um Komplexität zu vermeiden (CQ-4278391).
* Das System gibt beim Hochladen der aus der AEM Admin Console importierten Markenportal-Benutzerliste (.csv-Datei) eine Ausnahme aus. Nur die Felder &quot;E-Mail&quot;, &quot;Vorname&quot;und &quot;Nachname&quot;in der .csv-Datei sind obligatorisch (CQ-4278390).

#### Communities {#communities}

**Fehlerkorrekturen**

* Schnelllinks zum Verwalten von Gruppen (Gruppen öffnen/bearbeiten/Veröffentlichen/Löschen) sind für Community-Administratoren nicht sichtbar (Gruppenadministrator/Site-Administrator) (NPR-31627).
* Ein gesendeter Blog wird nur angezeigt, wenn die Seite manuell aktualisiert/neu geladen wird (NPR-31599).
* Bei der JCR-Abfrage, die von der Funktion &quot;Erwähnungen&quot;verwendet wird, wird zwischen Groß- und Kleinschreibung unterschieden. Die Rückgabe der Ergebnisse dauert zu lange (NPR-31475).
* AEM 6.5 UberJar-Datei löst eine Ausnahme aus, da das `cq-social-translation` Bundle in der AEM 6.5 UberJar-Datei (NPR-31186) fehlt.
* Jackson Databind-Bibliotheken wurden auf Version 2.9.9.3 aktualisiert, um neue Schwachstellen zu beheben (NPR-30967).
* Die Titel der Aktivitäten und Benachrichtigungen sind inkonsistent (NPR-30941).
* Die Paginierung in Communities Blogs funktioniert nicht richtig. (NPR-30914) 
* Analytics-Berichte werden nicht in der AEM-Autorenumgebung ausgefüllt, eine leere Seite wird angezeigt (NPR-30913).

#### Oak {#oak}

* Aktualisierungen des Lucene-Indexes, die dazu führen, dass der Autorenserver langsamer wird (NPR-31548).

#### Formulare {#forms-6530}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

##### Forms-Add-on-Paket {#forms-add-on-package-6530}

**Adaptive Formulare**

* Zeichenfolgen enthalten den Wörterbuchschlüssel beim Lokalisieren von adaptiven Formularen (NPR-31110).

**Interaktive Kommunikation**

* **MissingNode.toString()** gibt nach der Aktualisierung der Jackson-Bibliotheken auf 2.10.0 (NPR-31549) falsche Ergebnisse zurück.

* Im Texteditor werden Leerzeichen zufällig aus dem aus Microsoft Word kopierten Text entfernt (NPR-31113).

**Korrespondenzverwaltung**

* Beschriftungen und QuickInfos werden beim Migrieren von Briefen von LiveCycle ES4SP1 auf AEM 6.5 (NPR-31615) nicht angezeigt.

* **Textflussformatierung wird beim Speichern von Briefen als Entwürfe nicht mehr unterstützt** (NPR-30463).

**Workflow**

* OSGi-Arbeitsablauf schlägt aufgrund der 100%igen CPU-Auslastung (NPR-31233) fehl.

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30909).

##### Forms on JEE-Installationsprogramm {#forms-jee-installer-6530}

**Forms - Document Services**

* Der SOAP-Webdienst, der MTOM in einem .NET-Projekt verwendet, zeigt Ausnahmen für AssemblerServiceClient-Aufrufe und HtmlToPDF2-Methoden (NPR-4281771) an.

**Foundation JEE**

* Die Aktionskonfiguration lädt die Prozessnamen für Übermittlungsaktion &quot;Aufrufen eines Formulararbeitsablaufs&quot;(NPR-31478) nicht.
* AEM Forms on JEE-Benutzern treten beim Importieren von .lca-Dateien oder beim Einrichten von LDAP in der Admin-Konsole ähnliche Fehler auf:

   `com.ibm.ws.webcontainer.filter.FilterInstanceWrapper doFilter SRVE8109W: Uncaught exception thrown by filter um: java.lang.NoClassDefFoundError: org/apache/commons/io/IOUtils at org.apache.commons.fileupload.util.Streams.copy`

   `Error 500: javax.servlet.ServletException: java.lang.NoClassDefFoundError: org.apache.commons.io.IOUtils` (NPR-30931)


### Enthaltene Feature Packs {#feature-packs-included-6530}

>[!NOTE]
>
>AEM Forms-Kunden müssen unbedingt beachten, dass das AEM Forms-Add-on-Paket erst nach der Installation jeglicher Service Packs, Cumulative Fix Packs oder Feature Packs von AEM installiert werden darf.

#### Forms – Foundation JEE {#forms-foundation-jee-feature}

* AEM Forms-Unterstützung für Oracle 18c (NPR-29155).

## Install 6.5.3.0 {#install}

**Einrichtungsvoraussetzungen**

* AEM 6.5.3.0 requires AEM 6.5. Check [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* Der Download des Service Packs ist in Adobe Package Share verfügbar, auf das Sie direkt über die AEM 6.5-Instanz zugreifen können.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.3.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Erstellen Sie eine Momentaufnahme oder ein neues Backup Ihrer AEM-Instanz, bevor Sie das Service Pack installieren.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Dennoch wird dies empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!CAUTION]
>
>Adobe rät davon ab, das AEM 6.5.3.0-Paket zu entfernen oder zu deinstallieren.

### Installieren des Service Packs über Package Share {#install-service-pack-via-package-share}

Führen Sie folgende Schritte aus, um das Service Pack in einer vorhandenen AEM 6.5-Instanz zu installieren:

1. Login to Package Share from within AEM or directly from your browser and download the [AEM 6.5.3.0 package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.3.0).

1. Installieren Sie das heruntergeladene Paket mit Package Manager.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.5.3.0 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

**Automatische Installation**

Es gibt zwei Möglichkeiten, AEM 6.5.3.0 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..*Ordner /crx-quickstart/install* , während der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure that you use cmd=install&amp;recursive=true - so the nested packages  are  installed.

>[!NOTE]
>
>AEM 6.5.3.0 unterstützt keine Bootstrap-Installation.

**Bestätigen der Installation**

1. Auf der Seite &quot;Produktinformationen&quot;(/system/console/productinfo) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager, Version 6.5.3.0` unter &quot;Installierte Produkte&quot;angezeigt.

1. All  OSGi  bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: /system/console/bundles).
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.10.6 oder höher (Web-Konsole verwenden: /system/console/bundles).

In order to see what platforms are certified to run with this release, please refer to the [Technical Requirements](/help/sites-deploying/technical-requirements.md).

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

>[!NOTE]
>
>AEM 6.5.3.0 includes a new version of [AEM Forms Compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/AEM-FORMS-6.5.3.0-COMPAT). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf AEM 6.5.3.0 aktualisieren, installieren Sie nach der Installation des Forms Add-On-Pakets die neueste Version des AEM Forms-Kompatibilitätspakets.

1. Stellen Sie sicher, dass Sie das AEM Service Pack installiert haben.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

### Install AEM Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Korrekturen in AEM Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

For information about installing the cumulative installer for AEM Forms on JEE and post-deployment configuration, see the [release notes for patch 0007](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0007.html).

#### Workbench-Installationsprogramm

Da es sich um ein vollständiges Installationsprogramm handelt, ist die Dateigröße im Vergleich zur Patch-Version größer. Deinstallieren Sie die vorherige Workbench-Version, bevor Sie die neue Version installieren.

## UberJar {#uber-jar}

The UberJar for AEM 6.5.3.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.3/).

To use UberJar in a Maven project, refer to the article, [How to use UberJar](/help/sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.3.0</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen auf, die mit AEM 6.5.3.0 als veraltet markiert wurden. Funktionen, die in einer zukünftigen Version entfernt werden sollen, werden zuerst auf &quot;Veraltet&quot;eingestellt, wobei eine alternative Option verwendet werden muss.

Kunden wird empfohlen, zu überprüfen, ob sie die Funktion oder Funktionalität in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | The **[!UICONTROL AEM Cloud Services Opt-In]** screen has been deprecated. Mit der AEM- und Target-Integration, die in AEM 6.5 aktualisiert wurde, um die Target Standard-API zu unterstützen, die Authentifizierung über Adobe IMS und I/O verwendet, und der wachsenden Rolle von Adobe Launch bei der Instrumentierung von AEM-Seiten für Analyse und Personalisierung ist der Opt-In-Assistent nun funktional irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und Adobe I/O-Integrationen über entsprechende AEM-Cloud-Services |

## Bekannte Probleme {#known-issues}

* Wenn der Assistent zur Konfiguration **von** verknüpften Assets nach der Installation von AEM 6.5.3.0 eine Fehlermeldung 404 zurückgibt, müssen Sie die Pakete **cq-remotedam-client-ui-content** und **cq-remotedam-client-ui-components** manuell mit dem Package Manager neu installieren.
* Die folgenden Fehler- und Warnmeldungen können während der Installation von AEM 6.5.x.x angezeigt werden:
   * „Wenn die Target-Integration mit der Target Standard-API (IMS-Authentifizierung) in AEM konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * com.adobe.granite.maintenance.impl.TaskScheduler: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregationsfunktionen wie SUM, MAX und MIN verwendet werden. CQ-4274424
   * com.adobe.granite.maintenance.impl.TaskScheduler - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.

## Enthaltene OSGi-Bundles und Inhaltspakete {#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten werden die in AEM 6.5.3.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt.

Liste der in AEM 6.5.3.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6530_bundles.txt)

Liste der in AEM 6.5.3.0 enthaltenen Inhaltspakete

[Datei laden](assets/sp_6530_packages.txt)

## Hilfreiche Ressourcen {#helpful-resources}

* [Versionshinweise zu AEM 6.5](/help/release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/marketing/experience-manager.html)
* [Dokumentation zu AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Eingeschränkte Sites {#restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Support](https://daycare.day.com/public/contact.html). Weitere Informationen zum Zugriff auf das Support-Portal finden Sie unter [Zugriff auf das Support-Portal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).
