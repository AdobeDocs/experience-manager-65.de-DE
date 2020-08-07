---
title: Adobe Experience Manager 6.5 Previous Service Pack Release Notes
description: Versionshinweise speziell für Adobe Experience Manager 6.5 Service Pack 3 und früher.
contentOwner: AK
translation-type: tm+mt
source-git-commit: d6f48896a56950d44dfe0d1f9b712157951af83c
workflow-type: tm+mt
source-wordcount: '8108'
ht-degree: 37%

---


# In früheren Service Packs enthaltene Hotfixes und Feature Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## Adobe Experience Manager 6.5.4.0 {#experience-manager-6540}

Adobe Experience Manager 6.5.4.0 is an important update that includes new features, key customer requested enhancements and performance, stability, security improvements, released since the general availability of 6.5 release in **April 2019**. It can be installed on top of Adobe Experience Manager 6.5.

Some key features and enhancements introduced in Adobe Experience Manager 6.5.4.0 include:

* Adobe Experience Manager Assets is now configured with Brand Portal through Adobe I/O Console.

* Für Adobe Experience Manager Forms Workflows ist jetzt ein neuer [Druckausgabe](../forms/using/aem-forms-workflow-step-reference.md) -Schritt Generieren verfügbar.

* [Multi-column support](../forms/using/resize-using-layout-mode.md) for layout mode for adaptive forms and Interactive Communications.

* Unterstützung für [Rich Text](../forms/using/designing-form-template.md) in HTML5-Formularen.

* [Barrierefreiheitsverbesserungen](new-features-latest-service-pack.md#accessibility-enhancements) in Experience Manager Assets.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.8 aktualisiert.

* You can now sync selective content subtrees to *Dynamic Media - Scene7 mode* instead of all available at `content/dam`.

* Die Integration des Formulardatenmodells mit dem SOAP-Webdienst unterstützt jetzt Auswahlgruppen oder Attribute für Elemente.

* SOAP input or output and complex data structures now support Dynamic Group Substitution.

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

* kernel.js and ui.js are not pre-complied or cached. Dies führt zu zusätzlicher Zeit beim Rendern von Seiten (NPR-31891).

* Wenn PageEventAuditListener aktiviert ist, wird die Länge der Warteschlange zum Übernehmen verlängert. It impacts the performance of many operations such as bulk publishing, navigation, bulk asset movement (NPR-31890).

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

* Die Schaltfläche zum Auslösen des Workflows auf der Seite zur Asset-Sammlung ist deaktiviert (NPR-32471).

* Ein Ordner ohne Namen wird in SPS (Scene7 Publishing System) erstellt, während ein Asset in Experience Manager mit der Scene7-Konfiguration für dynamische Medien (NPR-32440) von einem Ordner in einen anderen verschoben wird.

* Die Aktion zum Verschieben aller Assets (mit &quot;Alle auswählen&quot;und dann &quot;Verschieben&quot;) in einen Ordner mit veröffentlichten Assets schlägt fehl (NPR-32366).

* Die Generierung von Ausgabeformaten für Assets mit ${extension} schlägt fehl (NPR-32294).

* Die URLs im Versionsverlauf werden auf der Eigenschaftenseite (NPR-31889) unter &quot;Verwiesen nach&quot;angezeigt.

* Die von DAM heruntergeladene ZIP-Datei kann nicht mit WinZip (NPR-32293) geöffnet werden.

* Ursprüngliche Berechtigungen eines Ordners werden aktualisiert, wenn Ordnereinstellungen geöffnet werden, um den Ordnertitel oder das Miniaturbild zu ändern und dann zu speichern (NPR-32292).

* Das Kalendersymbol für geplante Aktivierungen wird nicht in der Statusspalte (in der Classic UI der DAM-Asset-Auflistung) für Assets angezeigt, deren Aktivierung für ein späteres Datum und eine spätere Uhrzeit geplant ist (NPR-32291).

* Snippet creation using snippet templates gives error on searching for collections during the snippet creation process (NPR-32290).

* Multiple search queries get fired when multiple tags are selected from search filter (NPR-32143).

* In der Benutzeroberfläche &quot;Experience Manager Assets&quot;werden abgeschnittene Dateinamen angezeigt, wenn Assets mit mehr als 50 Zeichen im Dateinamen hochgeladen werden (NPR-32054).

* Alle Kontrollkästchen im Filterbedienfeld werden gelöscht, wenn das erste und das zweite Kontrollkästchen geleert werden, wenn in Adobe Stock die Kontrollkästchen der Stufe 2 aktiviert wurden (NPR-31919).

* Die Datei- und Ordnersuche mit Omniture-Facetten bildet eine Ausnahme (NPR-31872).

* Die Feldhervorhebung für die obligatorische Feldauswahl im Metadateneditor wird auch nach Auswahl des erforderlichen Schemas nicht entfernt, wenn die Abhängigkeitsregeln im entsprechenden Metadaten-Formular (NPR-31834) festgelegt sind.

* Vollständige Namen von Tags auf Blattebene (aus der Taghierarchie) werden auf der Seite &quot;Asset-Eigenschaften&quot;nicht angezeigt (NPR-31820).

* Die Verwendung des Befehls &quot;Zurück&quot;auf der Seite &quot;Asset-Eigenschaften&quot;im Safari-Browser gibt einen Fehler zurück (NPR-31753).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Auf der Seite &quot;Assets-Detail&quot;von PDF-Assets werden keine Aktionsschaltflächen angezeigt, außer den Schaltflächen &quot;An Sammlung&quot;und &quot;Hinzufügen Darstellung&quot;in Experience Manager, der im Scene7-Ausführungsmodus für dynamische Medien ausgeführt wird (CQ-4286705).

* Die Verarbeitung von Assets durch den Batch-Upload von Scene7 (CQ-4286445) dauert zu lange.

* Save button does not import Remote Set when user has not made any changes in Set Editor in Dynamic Media Client (CQ-4285690).

* Die Miniaturansicht von 3D-Assets ist nicht informativ, wenn ein unterstütztes 3D-Modell in Experience Manager integriert wird (CQ-4283701).

* The unprocessed status of smart crop video viewer preset appears twice on the banner text alongside the preset name (CQ-4283517).

* Incorrect container height of an uploaded 3D model previewed in 3D viewer is observed on asset’s details page (CQ-4283309).

* Carousel Editor does not open in IE 11 on Experience Manager Dynamic Media Hybrid mode (CQ-4255590).

* Keyboard focus gets stuck in Email drop-down in Download dialog, in Chrome and Safari browsers (NPR-32067).

* Sync all content checkbox is not enabled by default while trying to add DM cloud config on Experience Manager (CQ-4288533).

### Foundation UI {#foundation-ui-6540}

* Mouse control shifts to previous filter field instead of staying in the existing filter field while searching assets using Filter panel (NPR-32538).

* Platform Tagging: Search for tags by typing in the tag fields shows tags outside the root boundaries and does not respect the `rootPath` property of tag fields (NPR-31895).

* Plattform-Benutzeroberfläche: Pfadbrowser wird umgebrochen, wenn im Textfeld ein ungültiger Pfad hinzugefügt wird (NPR-31884).

* Die Benachrichtigung wird hinter einem fixierbaren Menü bei der Seitenauswahl (NPR-31628) versteckt.

### Plattform {#platform-sling-6540}

* (HTL) Unterstriche ersetzen Doppelpunkte im Pfadabschnitt der URL (NPR-32231).

### Projekte {#projects-6540}

* Schaltfläche &quot;Erstellen&quot;ist für den Benutzer nicht sichtbar, auch wenn der Benutzer berechtigt ist, ein Projekt im Unterordner zu erstellen (NPR-31832).

### Projects Translation {#projects-translation-6540}

* Translation project creation breaks the UI when the Trim Spaces option is activated in `Apache Sling JSP Script Handler` (NPR-32154).

* Fehler in UI- und Null-Punkt-Ausnahme in Fehlerprotokollen werden beobachtet, wenn ein zu übersetzendes Tag einem Übersetzungsprojekt hinzugefügt wird (NPR-31896).

### Integrationen {#integrations-6540}

* Die URL-Erstellung der Startbibliothek basiert nur auf `path` und `library_name` Werten aus der Start-API und basiert nicht auf dem `library_path` Wert (NPR-31550).

* Während der Verarbeitung von LiveFyre-bezogenen Elementen wird eine Fehlermeldung angezeigt (FYR-12420).

* ReportSuitesServlet ist anfällig für SSRF (NPR-32156).

### WCM-Vorlageneditor {#wcm-template-editor-6540}

* Im Strukturmodus für bearbeitbare Vorlagen zeigt die Liste für zulässige Komponenten im Layout-Container keine Komponente für die Verknüpfungsschaltfläche an (CQ-4282099).

### WCM Page Editor {#wcm-page-editor-6540}

* Fehler werden bei der Auswahl einer Überlagerung und der anschließenden Auswahl von reaktionsfähigen Raster Ziehen Sie Komponenten hierher (CQ-4283342).

### Campaign Targeting {#campaign-targeting-6540}

* Die Konfiguration der Zielgruppe Cloud schlägt fehl, wenn die Fehlermeldung &quot;get mboxes&quot;fehlgeschlagen ist (CQ-4279880).

### Brand Portal {#assets-brand-portal-6540}

* Brand Portal users are not able to publish contribution folder assets to [!DNL Assets] on upgrading to Adobe I/O on Experience Manager 6.5.4 (CQDOC-15655). For an immediate fix on Experience Manager 6.5.4, it is recommended to [download the hotfix](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) and install on your author instance.

* Popup-Schemas für Metadaten sind in den Asset-Eigenschaften nicht sichtbar (CQ-4283287).

* Das Metadaten-Unterschema zeigt keine Registerkarten basierend auf dem MIME-Typ in den Asset-Eigenschaften an (CQ-4283288).

* Beim Rückgängigmachen der Veröffentlichung des Metadatenschemas wird eine Fehlermeldung angezeigt, obwohl das Schema im Backend entfernt wurde.

* Preview image do not display for a published asset (CQ-4285886).

* User is unable to publish or unpublish assets containing single quote in the name (CQ-4272686).

* Die Geschäftsbedingungen werden beim Herunterladen mehrerer Assets nicht angezeigt (CQ-4281224).

* Geringfügige Sicherheitslücken wurden behoben.

### Communities {#communities-6540}

* Das Formular &quot;Create Member&quot;wird als leere Seite angezeigt (NPR-31997).

* Der Benutzer kann den Analytics-Bericht nicht in der Autoreninstanz (NPR-30913) Ansicht werden.

### Oak- Indexing and Queries {#oak-indexing-6540}

* MS Word and MS Excel documents, containing JPEG image, when parsed with Tika parser fail to parse and class not found error is observed (NPR-31952).

### Formulare {#forms-6540}

>[!NOTE]
>
>Experience Manager Service Pack enthält keine Fehlerbehebungen für Experience Manager Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Darüber hinaus wird ein kumulatives Installationsprogramm veröffentlicht, das Korrekturen für Adobe Experience Manager Forms on JEE enthält. Weitere Informationen finden Sie unter [Installieren des Experience Manager Forms-Add-ons](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) und [Installieren von Experience Manager Forms on JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

* Correspondence Management: Briefe zeigen zusätzliche Zeichen nach der Übermittlung an die Workflows an (NPR-32626).

* Correspondence Management: Briefe zeigen einen Dropdown-Platzhalter als Textkomponente an, nachdem sie an Workflows gesendet wurden (NPR-32539).

* Correspondence Management: Die in der Briefvorlage definierten Standardwerte werden nicht im Vorschau-Modus (NPR-32511) angezeigt.

* Mobile Forms: Die Senden-Schaltfläche wird beim Rendern eines XDP-Formulars in einer HTML-Version (NPR-32514) als vergrößert angezeigt.

* Dokument-Dienste: URL-Zugriffsfehler für Briefe und einige andere Seiten nach Anwendung von Service Pack 2 (NPR-32508, NPR-32509).

* Dokument-Dienste: Wenn die Anzahl der Transaktionen auf einem Server eine bestimmte Grenze überschreitet, schlägt die Konvertierung von HTML in PDF fehl und die Dateitypeinstellungen werden vom [!DNL Forms] Server entfernt (NPR-32204).

* Adaptives Forms: Das Tool zur Barrierefreiheit des Browsers meldet Fehler in adaptiven Formularen gemäß den Richtlinien für WCAG2 Level AA (NPR-32312, NPR-32309, CQ-4285439).

* Adaptives Forms: Chrome-Browser-Barrierefreiheitstool berichtet über einen Best Practice-Fehler (NPR-32310).

* Adaptives Forms: Übersetzungsprobleme beim Konfigurieren eines adaptiven Formulars, das in eine Experience Manager-Siteseite eingebettet ist (NPR-32168).

* Workbench: Beim Verwenden des Vorgangs &quot;PDF-Eigenschaften abrufen&quot;für den PDF Utilities-Dienst (NPR-32150) wird eine Fehlermeldung angezeigt.

* Dokument Security: Eine geschützte PDF-Datei kann nicht offline geöffnet werden, wenn die Option DisableGlobalOfflineSynchronizationData auf True (NPR-32078) eingestellt ist.

* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32547, NPR-31983, NPR-31950) ausgeblendet.

* Designer: Wenn eine Tabelle zusammengeführte Zellen enthält, schlägt der Barrierefreiheitstest für die Ausgabe-PDF-Datei fehl, die mithilfe des Ausgabediensts (CQ-4285372) aus einem XDP-Formular konvertiert wurde.

* Foundation JEE: Wenn ein Experience Manager-Forms-Server von einem Cluster getrennt ist, verhindern Cache-Probleme, dass er eine erneute Serververbindung herstellt (NPR-32412).

## Adobe Experience Manager 6.5.3.0 {#experience-manager-6530}

[!DNL Adobe Experience Manager] 6.5.3.0 ist eine wichtige Version, die Leistungsverbesserungen, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen von Kunden umfasst, die seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht wurden. It can be installed on top of [!DNL Adobe Experience Manager] 6.5.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.6 aktualisiert.

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Ansicht der Liste hinzugefügt.

* Die Sortierung von Assets basierend auf der Spalte &quot;Name&quot;wurde in der Ansicht &quot;Liste&quot;aktiviert.

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen.

* [!DNL Dynamic Media] supports Smart Imaging.

* Möglichkeit zur [Festlegung von Abwesenheitseinstellungen](../forms/using/configure-out-of-office-settings.md) in [!DNL Experience Manager] Workflows.

* Ability to [share Inbox or Inbox items](../forms/using/configure-shared-queues-osgi.md) with other users in [!DNL Experience Manager] workflows.

* Möglichkeit, interaktive Kommunikation im Stapelmodus zu [generieren](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

* Die Version von jQuery im Paket ContextHub wurde auf 3.4.1 aktualisiert.

### Assets {#assets-6530-enhancements}

**Produktverbesserungen**

* [!DNL Experience Manager Assets] unterstützt jetzt ZIP-Archive, die mit dem Deflate64-Algorithmus (NPR-27573) erstellt wurden.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wird in der DAM-Liste Ansicht und in den Asset-Suchergebnissen in der Liste Ansicht (NPR-31312) hinzugefügt.

* In der Ansicht &quot;Liste&quot;können Benutzer die Liste der Assets mithilfe der Spalte &quot; [!UICONTROL Name] &quot;sortieren (NPR-31299).

* Die Dateien GLB, GLTF, OBJ und STL können in DAM (CQ-4282277) auf der Seite &quot; [!UICONTROL Asset-Details] &quot;in der Vorschau angezeigt werden.

* `ReplicationOnModifyListener` ereignis wird beim Hochladen von Chunk-Knoten in ausgelöst [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] unterstützt jetzt Smart Crop-Video-Assets. Smart Crop ist eine maschinelle lerngesteuerte Funktion, die ein Video beim Verschieben des Rahmens neu beschneidet, um dem Brennpunkt der Szene zu folgen (CQ-4278995).

* [!DNL Dynamic Media] supports Smart Imaging (CQ-4222249).

* Search or browse view is set as the default view in Foundation picker if query parameters are passed in request (NPR-31601).

**Fehlerkorrekturen**

* Metadata for some PDF documents is not updated and saved to the PDF when its title is modified (NPR-31629).

* Asset sharing does not work for an asset that has plus character (`+`) in the file name (NPR-31547).

* Edits in the default search form Assets Admin Search Rail do not work as expected (NPR-31502).

* Suggestions are not displayed when using Omnisearch on assets view for searching assets (NPR-31496).

* Asset references within collections are not updated when the referenced assets are moved to another location, in cases where the same assets are referenced by different collection by different users (NPR-31486).

* Duplicate IPTC tags are added to asset metadata (NPR-31328).

* The search result count does not update accurately when a search is triggered from the filter rail (NPR-31316).

* All the check boxes are cleared on deselecting the second-level check boxes in the File Type filter, and text in the search bar is not in sync with the selected or deselected properties (NPR-31287).

* All the members (users/ groups) cannot be removed from the Members section of a folder; on attempting to remove all the users, logged in user gets added to the list (NPR-31171).

* Assets mit Pluszeichen (`+`) im Dateinamen können nicht gelöscht werden (NPR-31162).

* Dropdown-Menü erstellen, das im oberen Menü bei Auswahl eines Ordners angezeigt wird, zeigt nicht &quot;Ordner&quot; als Erstellungsoption (NPR-30877).

* Ordnerauswahl &quot;Erstellen&quot;> &quot;DateiUpload&quot;-Aktionselement fehlt, wenn ACL für Verweigern `jcr:removeChildNodes` und `jcr:removeNode` auf Pfad für einen Benutzer angewendet werden (NPR-30840).

* DAM workflows go into stale state when certain mp4 assets are uploaded, causing all the remaining workflows to go into stale state (NPR-30662).

* Out of Memory Error is observed when a large PDF files (of several Gigabytes) is uploaded to DAM and its sub-assets are processed (NPR-30614).

* Die Massenbewegung von Assets schlägt fehl und es wird eine Warnmeldung angezeigt (NPR-30610).

* Beim Verschieben von Assets von einem Ordner in einen anderen im [!DNL Experience Manager] [!DNL Dynamic Media]Scene7-Modus (NPR-31630) werden die Asset-Namen in Kleinbuchstaben geändert.

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler behoben, da sich das Bild im Ordner befindet, der dem Namen der Scene7-Firma entspricht (NPR-31340).

* [!DNL Dynamic Media] assets containing references are not getting published (NPR-31180).

* Uploads vom [!DNL Dynamic Media]7-Scene7-Modus zum [!DNL Dynamic Media Classic] Ausführen dauern zu lange (NPR-31048).

* Hotspot, der zu einem Bild-Asset hinzugefügt wurde, ist auf der Seite mit den Asset-Details nicht über den interaktiven Bild-Viewer sichtbar (NPR-30979).

* Huge sling jobs are created and Processing banner re-appears when actions done on assets in [!DNL Experience manager Assets] are passed to Scene7 (NPR-30947).

* Conflict occurs on creating Language Copy of assets and assets are not uploaded to Scene7 (NPR-30932).

* Dynamic renditions downloaded from [!DNL Experience Manager] running in [!DNL Dynamic Media]–Hybrid mode are broken (they are of text type with content &#39;unable to find image&#39; instead of image content type) (NPR-30876).

* [!DNL Dynamic Media] Encode Video workflow is failing to generate thumbnail for the video that is migrated from [!DNL Dynamic Media Classic] to [!DNL Dynamic Media]–Scene7 mode on Adobe Experience Manager (CQ-4282011).

* IpsApiException observed while migrating assets from one instance to another using different Scene7 company IDs (CQ-4280548).

* 3D Asset thumbnail is not informative, when a supported 3D model is ingested into [!DNL Experience Manager] (CQ-4283701).

* Scroll buttons are displayed in viewer, if a 3D asset has few camera views (CQ-4283322).

* Incorrect container height of an uploaded 3D model previewed in DimensionalViewer on Asset Details page (CQ-4283309).

* Videos cannot be played with SmartCropVideoViewer on Internet Explorer 11 and Safari (CQ-4281422).

* Use of move button to move multiple assets, from one folder to another, fails in [!DNL Experience Manager] running on [!DNL Dynamic Media]–Scene7 runmode (CQ-4280384).

* Distorted video is seen on asset details when MIME type is other than MP4 (CQ-4279704).

* Videos newly ingested in folders with video profile remain in processing state even after encode percentage completes to 100% (CQ-4279389).

* Durch das Verschieben von Assets aus einem Ordner wird eine große Anzahl von Sling-Aufträgen (Scene7 API-Aufrufe) erzeugt, die nicht unbedingt erforderlich sind (CQ-4278664).

* Die Namen des Bildsatzes werden in Scene7 in Kleinbuchstaben geändert, wenn in DAM (CQ-4281112) Bildsatz (oder Mediaset) erstellt und mit der entsprechenden Benennungskonvention benannt wird.

* Scene7 Migrator stellt den Veröffentlichungsstatus falsch ein (CQ-4263492).

* Touch UI search (done through Omnisearch) results page automatically scrolls up and loses user&#39;s scroll position in Content Fragments (CQ-4282898).

* PDF files are not indexed and content within is not searchable (CQ-4278916).

* Fehler &quot;Gruppe nicht nach Benutzerauswahl aufgeführt: &quot;false to equal true&quot;wird beim Hinzufügen von &quot;Closed User Group&quot;mit &quot;different&quot; `principalName` und `authorizableId` (CQ-4278177) beobachtet.

* Die Ansicht &quot;Assets UI Column&quot;zeigt alle Pfade unabhängig vom Stammpfad des jeweiligen Mandanten an (CQ-4278175).

* Asset selector’s search is not working as expected (CQ-4275886).

* Die Workflows sind fehlgeschlagen (CQ-4271928).

* DAM Ereignis Purge löscht die neuesten (`maxSavedActivities`) Ereignis-Daten und speichert die zuvor erstellten Daten (NPR-31336).

* Touch UI search (done through Omnisearch) results page automatically scrolls up and loses user&#39;s scroll position (NPR-31307).

* The action bar and asset count are not updating on selecting all and then deselecting some items (folders/individual assets) in Touch UI (NPR-31118).

* An exception displays in [!DNL Experience Manager] while polling for job details of an Asset (CQ-4283569).

### Sites {#sites}

* If the LiveCopy inheritance is broken, live copy pages display language copy links instead of LiveCopy links (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint displays blank lines for the rest of the records (NPR-31182).
* When a user adds Japanese or Korean characters in the description property of a menu, the menu displays distorted characters for Japanese and Korean language text (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen (NPR-30879).
* Standardmäßig wird der RTE-Editor (RTE) mit Gerüsten versehen. applies inline font-size to elements, unexpectedly (NPR-31284).
* Wenn ein Benutzer sich auf Felder in der linken Schiene konzentriert und zum Einfügen von Inhalten einen Tastaturbefehl verwendet, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31172).
* When a user adds a File Upload field to a multi-field, the image path is stored in the component node instead of the multi-field node (NPR-30882).
* The `ResponsiveGridExporter` API does not return `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` interface. The `com.day.cq.wcm.foundation.model.impl` package is declared as a private package (NPR-31398).

<!-- Review: NPR-31398 has fixVersion as 6530. However, it is mentioned twice in 6530 and 6520 as fixed. 
Remove one mention of this fix.
-->

* When a page containing some Experience Fragments is opened in non-editor mode (either in Author without the `editor.html` prefix and `wcmmode=disabled`, or in Publisher)., the request ends in HTTP status error code `500` (NPR-30743).
* Benutzer können ihr Kennwort nicht ändern und nicht auf ihre Profil-Seite zugreifen (NPR-31161).

### Search and user interface {#ui-interface-and-search}

* When switching from the card view to the list view on a search results page, there is a lag before the page can be scrolled (NPR-31286).

* The [!UICONTROL Select All] checkbox is hidden in the list view on [!DNL Sites] user interface (NPR-31614).

* The [!UICONTROL Select All] count on a search result page is incorrect (NPR-31120).

* The metadata editor displays tags that do not exist (NPR-31119).

### Übersetzung {#translation}

* Two calendar pop-ups appear on selecting the Due Date option in a Translation Job (NPR-31270).

### Plattform {#platform}

* The Mime type option in the Web console does not work (NPR-31108).

* Client certificate is not accepted when configuring single sign-on (NPR-31165).

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Dienst werden nicht gespeichert (NPR-30925).

* QueryBuilder now supports orderby `fn:name()` in xpath queries (NPR-31322).

* Duplicate activation tree is created on upgrading from [!DNL Experience Manager] 6.3 (NPR-31513).

* Forwarded requests do not preserve response headers that are set during sling authentication (NPR-30013).

* Search within the picker components does not work (NPR-31692).

* An error is displayed when attaching a ZIP file to an [!DNL Experience Manager Communities] post due to different versions of Apache POI and Apache Tika bundle (NPR-31018).

* The `org.apache.sling.distribution.api` bundle is hidden in the configuration manager and therefore not available to custom bundles (NPR-31720).

### Projekte {#projects}

* Switching calendar views does not work (NPR-31271).

### Brand Portal {#assets-brand-portal-6530}

**Produktverbesserungen**

* Asset Sourcing import workflow in [!DNL Experience Manager Assets] is modified to fetch only the newly created assets from [!DNL Brand Portal] to [!DNL Experience Manager], and skip the assets that already exist in the NEW folder to avoid replication (CQ-4278527).

**Fehlerkorrekturen**

* Incorrect icon appears on creating a new Contribution folder in Asset Sourcing feature (CQ-4282825).
* On creating a new Contribution folder, one or both subfolders (NEW and SHARED) does not appear inside the Contribution folder (CQ-4282424).
* System throws an exception if the user tries to republish Contribution folder from [!DNL Experience Manager] to [!DNL Brand Portal] after receiving new assets in the Contribution folder from [!DNL Brand Portal] end (CQ-4279740).
* Creation of Contribution folder within a Contribution folder (nested folder) is prohibited to avoid complexity (CQ-4278391).
* System throws an exception on uploading the [!DNL Brand Portal] user list (.csv file) imported from [!DNL Experience Manager] Admin Console. Only Email, FirstName, and LastName fields in the .csv file are mandatory (CQ-4278390).

### Communities {#communities-6530}

**Fehlerkorrekturen**

* Quick links to manage groups (Open/Edit/Publish/Delete Groups) are not visible to the Community administrators (Group admin/Site admin) (NPR-31627).
* A submitted blog is not displayed unless the page is manually refreshed/reload (NPR-31599).
* The JCR query used by the &quot;Mentions&quot; feature is case sensitive and takes too long to return results (NPR-31475).
* [!DNL Experience Manager] 6.5 UberJar file throws exception, `cq-social-translation` bundle missing from [!DNL Experience Manager] 6.5 UberJar file (NPR-31186).
* Jackson Databind libraries updated to version 2.9.9.3 to address new vulnerabilities (NPR-30967).
* Die Titel der Aktivitäten und Benachrichtigungen sind inkonsistent (NPR-30941).
* Pagination is not working properly in [!DNL Communities] Blogs (NPR-30914).
* Analytics reports are not populated in [!DNL Experience Manager] author environment, blank page appears (NPR-30913).

### Oak {#oak}

* Lucene index updates causing author server to slow down (NPR-31548).

### Formulare {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. For more information, see [Install Experience Manager Forms add-on](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) and [Install Experience Manager Forms on JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

#### Forms-Add-on-Paket {#forms-add-on-package-6530}

**Adaptive Formulare**

* Strings contain the dictionary key while localizing adaptive forms (NPR-31110).

**Interaktive Kommunikation**

* **MissingNode.toString()** gibt nach der Aktualisierung der Jackson-Bibliotheken auf 2.10.0 (NPR-31549) falsche Ergebnisse zurück.

* Text editor randomly removes space characters from the text copied from Microsoft Word (NPR-31113).

**Korrespondenzverwaltung**

* Captions and tooltips do not display while migrating letters from LiveCycle ES4SP1 to [!DNL Experience Manager] 6.5 (NPR-31615).

* **Textflow formatting is no more supported** error message displays while saving letters as drafts (NPR-30463).

**Arbeitsablauf**

* OSGi workflow fails due to 100% CPU utilization (NPR-31233).

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30909).

#### Forms on JEE installer {#forms-jee-installer-6530}

**Forms - Document Services**

* SOAP web service using MTOM in a .NET project displays exceptions for AssemblerServiceClient invoke and HtmlToPDF2 methods (NPR-4281771).

* [Axis jar versions 1.4 and 1.4.1](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-5/jee-patch-0014.html) include a security vulnerability (NPR-31015).

**Foundation JEE**

* Action configuration does not load the process names for Invoke a Forms Workflow submit action (NPR-31478).

### Enthaltene Feature Packs {#feature-packs-included-6530}

>[!NOTE]
>
>For [!DNL Experience Manager Forms] customers, it is essential to install [!DNL Experience Manager Forms] add-on package after installing any [!DNL Experience Manager] Service Pack, Cumulative Fix Pack, or Feature Pack.

#### Forms – Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Forms support for Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0 {#experience-manager-6520}

[!DNL Adobe Experience Manager] 6.5.2.0 is an important release that includes performance, stability, security, and key customer fixes and enhancements released since the general availability of [!DNL Adobe Experience Manager] 6.5 in **April 2019**. It can be installed on top of [!DNL Experience Manager] 6.5.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.3 aktualisiert.
* Added a configuration property to allow exporting Experience Fragments directly to user-defined workspaces for [!DNL Adobe Target].
* Assets-Benutzer können nach visuell ähnlichen Bildern suchen. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Visuelle Suche](../assets/search-assets.md#visualsearch).

* Die Funktionalität von Connected Assets wurde dahingehend erweitert, dass jetzt auch das Abrufen von Dokumenten aus Remote-DAM-Implementierungen unterstützt wird. Site-Autoren können jetzt die Inhaltssuche verwenden, um unterstützte Dokumenttypen zu durchsuchen und zu filtern. Die Remote-Dokumente können der Download-Komponente auf Webseiten hinzugefügt werden. Siehe [Verwenden von Connected Assets](../assets/use-assets-across-connected-assets-instances.md).

* EnhanceDokumenttyp-Filter mit mehr MIME-Typen zur Unterstützung von Optionen mit mehreren Werten.
* Ein Workflow zur erneuten, externen Verarbeitung wurde zur Unterstützung für mehrere Ressourcen eingeführt.
* Optimized [!DNL Dynamic Media] performance by using default asset filters for replication.
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
* MultiTenant: Tenants saving folder properties observe both success prompt and error message describing action was not successful, &quot;Unable to edit properties. unzureichenden Berechtigungen nicht geändert werden konnten, was für Verwirrung sorgt. NPR-30545: Hotfix für CQ-4275333
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

* If the LiveCopy inheritance is broken, live copy pages display language copy links instead of LiveCopy links (NPR-30980).
* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).
* Rich Text Editor (RTE)-Plug-In der Textkomponente zeigt verzerrte Zeichen für japanischen und koreanischen Text an (NPR-31331).
* Rich Text Editor (RTE) erlaubt nicht, eine eingebettete Liste als Element einzufügen (NPR-30879).
* Rich Text Editor (RTE) wird standardmäßig als Inline-Schriftgröße auf Elemente angewendet, unerwartet (NPR-31284).
* Wenn sich ein Benutzer auf linke Schienenfelder konzentriert und zum Einfügen von Inhalten Tastaturbefehle verwendet, werden Inhalte der Zwischenablage des Seiteneditors anstatt des Inhalts eingefügt, der aus den Feldern der linken Leiste kopiert wurde (NPR-31172).
* Wenn ein Benutzer ein Feld zum Hochladen von Dateien zu einem Multifeld hinzufügt, wird der Bildpfad im Komponentenknoten und nicht im Multifield-Knoten (NPR-30882) gespeichert.
* Die `ResponsiveGridExporter` API gibt keine `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` Schnittstelle zurück. Das `com.day.cq.wcm.foundation.model.impl` Paket wird als privates Paket (NPR-31398) deklariert.
* Wenn eine Seite mit Erlebnisfragmenten im Nicht-Editor-Modus geöffnet wird (entweder im Autorenmodus ohne das `editor.html` Präfix und `wcmmode=disabled`im Publisher), endet die Anforderung mit dem HTTP-Statusfehlercode 500 (NPR-30743).

### WCM – Seiteneditor {#wcm-page-editor-6520}

**Produktverbesserungen**

* EnhanceDocument type filters with more MIME Types to support multi valued options. Hotfix für CQ-4270694

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
>[!DNL Experience Manager] Service Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. They are delivered using a separate [!DNL Forms] add-on package. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. For more information, see [Install Experience Manager Forms add-on](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) and [Install Experience Manager Forms JEE installer](#forms-jee-installer).

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

## Adobe Experience Manager 6.5.1.0 {#experience-manager-6510}

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
* [!DNL Experience Manager] interface should display an additional entry for the current version of the asset in the timeline history, displaying the latest check-in comment from [!DNL Adobe Asset Link]. Hotfix für CQ-4262864
* Content Fragment Timeline displays an error message when properties are missing. Hotfix für CQ-4272560
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
* An issue with the inheritance of Style System nodes from parent to child. NPR-29516: Hotfix für CQ-4270330
* An error message while setting up the social posting to [!DNL Facebook] authentication. NPR-29211: Hotfix für CQ-4266630
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* In der Coral2-Implementierung werden beim Öffnen der Registerkarte „Berechtigungen“ die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

### E-Commerce

* Das Ausführen einer Lazy-Content-Migration für E-Commerce löst eine ConstraintViolationException aus. NPR-29247: Hotfix für CQ-4264383

### Verwaltung von Inhaltsfragmenten

* Parsing error when opening a Content Fragment which has characters dollar `($)` and open brace `({)`. Hotfix für CQ-4270266

### Experience Fragments

* Exportieren Sie [!DNL Experience Manager] Erlebnisfragmente in [!DNL Adobe Target]. Hotfix für CQ-4265469
* Experience Fragments export to target fails with smart image. Hotfix für CQ-4269606

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

### Formulare

The key highlights for [!DNL Experience Manager Forms] 6.5.1.0 are:

* OSGi only: Added a new attribute `PAGECOUNT` in Output and Forms Service.

* Nur OSGI: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert.
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert.
* Es wurde Unterstützung für die On-Premise-Integration von ADFS 3.0 für Dynamics ergänzt.

#### Forms-Add-On-Paket

**Backend-Integration**

* Fehler beim Abrufen von geschützter WSDL (Web Service Definition Language). NPR-29944: Hotfix für CQ-4270777
* When [!DNL Experience Manager Forms] is installed on IBM WebSphere, creating a form data model based on SOAP fails. Hotfix für CQ-4251134
* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. Hotfix für CQ-4270586
* Wenn der Titel einer Datenquelle geändert wird, zeigt das Formulardatenmodell den aktualisierten Titel nicht an. Hotfix für CQ-4265599
* If name of an entity or attribute contains hyphen or space, expressions fail to evaluate such entities and attributes. Hotfix für CQ-4225129

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
* Layout layer changes made on Document Fragment disappear on performing keep changes sync. Hotfix für CQ-4266054
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

* [!DNL Experience Manager Forms] 6.5 Create Correspondence UI (CCR UI) fails to open correspondence created with [!DNL Experience Manager Forms] 6.3. Hotfix for CQ-4266392
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

#### Assets - Included

* Multi-Site-Manager bietet jetzt Unterstützung für [!DNL Experience Manager Assets]. For more information, see [Reuse assets using MSM for Experience Manager Assets](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html). NPR-29199: Hotfix für CQ-4259922

#### Sites - Included

* Export [!DNL Experience Manager] Experience Fragments to [!DNL Adobe Target]. For more details, see [The Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix für CQ-4265469

#### Forms – Dokumentendienste - Included

* OSGi only: Added a new attribute PAGECOUNT in Output and Forms Service.. NPR-28922: Hotfix für CQ-4270870
* Nur OSGi: Unterstützung zum Erstellen von statischen PDF-Dateien mit dem Forms-Dienst aktiviert. NPR-28572: Hotfix für CQ-4270869
* Für Administratoren und Root-Benutzer wurden Berechtigungen für XMLForm.exe aktiviert. NPR-29237: Hotfix für CQ-4267080

### OSGi-Bundles und Inhaltspakete

The following text documents list the OSGi bundles and Content Packages included in [!DNL Experience Manager] 6.5.1.0

List of OSGi bundles included in [!DNL Experience Manager] 6.5.1.0

[Datei laden](assets/6_5-bundle-list.txt)

List of Content Packages included in [!DNL Experience Manager] 6.5.1.0

[Datei laden](assets/6_5-content-package-list.txt)
