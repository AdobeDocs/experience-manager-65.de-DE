---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Suchen Sie nach Versionsinformationen, Neuigkeiten, Installationsanleitungen und einer detaillierten Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 3
source-git-commit: 937af2df46b93aab6c9010814175d72a9bd583db
workflow-type: tm+mt
source-wordcount: '3176'
ht-degree: 37%

---

# Versionshinweise zum neuesten [!DNL Adobe Experience Manager] 6.5 Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession&cid=a915e87c-369a-480c-9daf-d13efc766798 -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6,5,15,0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | 24. November 2022 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.15.0 enthalten ist {#what-is-included-in-aem-6515}

[!DNL Experience Manager] 6.5.15.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen, Fehlerbehebungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_

* Added support for password reset for Dynamic Media Classic users within Experience Manager. (ASSETS-10298) -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets] {#assets-6515}

* Wenn das Verschieben eines Assets in Experience Manager fehlschlägt, kann das Asset dennoch umbenannt werden. (NPR-38753)
* Beim Anzeigen der Assets in einer [!UICONTROL Listenansicht], fehlen einige Titel. (CQ-4345746)
* Die Sprachausgabe gibt das Untermenü der [!UICONTROL Relation] auf der Registerkarte Allgemein auf der Seite Asset-Eigenschaften . (ASSETS-6938)
* Die Bildschirmlesehilfe erkennt die Ordnersymbole auf der Assets-Navigationsseite mit der Liste der Ordner falsch. (ASSETS-6936)
* Beim Kopieren einer Sammlung fehlt dem Bild ein leeres `alt` Attribut oder role=&quot;presentation&quot;. Daher wird das Bild den Benutzern der Bildschirmlesehilfe angezeigt. (ASSETS-6932)
* Der Text, der beim Kommentieren eines Assets angezeigt wird, hat keine 4:5:1 Kontrastverhältnis im Vergleich zur Hintergrundfarbe. (ASSETS-6931)
* Wenn Sie die Seitenbreite auf der Registerkarte IPTC auf der Seite Asset-Eigenschaften anpassen, passt der Seiteninhalt nicht richtig an und führt zu horizontalem Scrollen. (ASSETS-6929)
* Wenn Sie Assets filtern, wird der Filtertext im [!UICONTROL min] und [!UICONTROL max] -Felder verschwinden, nachdem ein Wert eingegeben wurde. (ASSETS-6925)
* In Experience Manager-Sammlungen gibt die Bildschirmlesehilfe die [!UICONTROL email] auf dem Bildschirm &quot;Herunterladen&quot;ein. (ASSETS-6923)
* Beim Kommentieren der Elemente fehlt ein alternativer Text. (ASSETS-6922)
* Wenn der Text im Datumsauswahlfeld in Stunden und Minuten geschrieben wurde, wird keine Textfehlermeldung angezeigt. Der Fehler wird nur mit der Farbe Rot identifiziert. (ASSETS-6852, ASSETS-6921, ASSETS-6920, ASSETS-6907)
* Der Alternativtext in `[role='img']` im Filter Dateien fehlt. (ASSETS-6919)
* Falsche Ankündigung der Bildschirmlesehilfe für [!UICONTROL Erstellen] Untermenü. (ASSETS-6916)
* In Experience Manager-Sammlungen die Schaltfläche &quot;Entfernen&quot; `X` hat keinen Text, der für die Bildschirmlesehilfen angekündigt werden kann. (ASSETS-6912)
* Bei Verwendung von Farbkontrast-Analyzer in Experience Manager gibt es keine Farbdifferenzierung zwischen dem aktuellen Datum und dem ausgewählten Datum in der Datumsauswahl des Kalender-Widgets. Das Kontrastverhältnis von mindestens 3:1 ist im Gegensatz zu den angrenzenden Farben nicht ausreichend. (ASSETS-6911)
* In Experience Manager Files , während Sie eine der Optionen aus [!UICONTROL Planung] Optionsfeld in Veröffentlichung verwalten, Name und Status der Optionsfeldoptionen werden von der Bildschirmlesehilfe angekündigt. Die Variable **Planung** nicht angekündigt. (ASSETS-6908, ASSETS-6906)
* Der alternative Text fehlt für das Symbol Sortieren . (ASSETS-6904)
* Auf der Seite &quot;Asset-Eigenschaften&quot;den Feldnamen `Person` in den IPTC Extension-Registerkarten werden von den Bildschirmlesehilfen nicht angekündigt. Die Bildschirmlesehilfe kündigt nur bearbeitbare und derzeit leere Felder an, jedoch nicht den Titel. (ASSETS-6903, ASSETS-6848)
* Das Anmerkungs-Tool kann nicht über die Tastatur angezeigt werden. Eine Maus wird zum Zeichnen eines Bildes verwendet, um das Anmerkungs-Tool anzuzeigen. (ASSETS-6899)
* In Experience Manager-Sammlungen wird ein leeres Feld auf der **Erweitert** gibt ein falsches Kontrastverhältnis zwischen dem Rand und der benachbarten Farbe an. (ASSETS-6895)
* Falsche ARIA-Attributwerte für einige Elemente beim Bearbeiten von Assets. (ASSETS-6894)
* Die Bildschirmlesehilfe erkennt die Überschrift beim Erstellen eines Workflows nicht richtig. (ASSETS-6892)
* Beim Kopieren einer Sammlung wird die Schaltfläche zum Entfernen des SVG-Bilds `X` mit role=&quot;img&quot; fehlt role=&quot;presentation&quot;. Daher wird das Bild den Benutzern der Bildschirmlesehilfe angezeigt. (ASSETS-6890)
* Im **Allgemein** auf der Registerkarte &quot;Asset-Eigenschaften&quot;hat die Bildschirmlesehilfe den Erweiterungs- oder Reduzierungsstatus des Felds Tags nicht ordnungsgemäß angekündigt. (ASSETS-6889)
* Die **Allgemein** Registerkarte unter Asset-Eigenschaften enthält Seiten mit doppelter ID. (ASSETS-6888)
* Der Titel des Textfelds, das beim Erstellen eines Workflows einen Titel definieren soll, verschwindet, wenn Sie einen Wert im Textfeld angeben. (ASSETS-6887)
* Die Empfängerliste beim Teilen eines Links wird als Datentabelle mit Überschriften angezeigt, ist aber für die Benutzer der Bildschirmlesehilfe nicht semantisch als Datentabelle identifiziert. (ASSETS-6886)
* Es wird keine Fehlermeldung angezeigt, die ein leeres Feld darstellt in `Add Email Address` -Feld. Der Fehler wird nur in einer Farbe dargestellt. (ASSETS-6885, ASSETS-6843)
* Platzhaltertexte, Pfad und ALT-Text weisen im Vergleich zu ihrer Hintergrundfarbe kein Kontrastverhältnis von mindestens 4,5:1 auf. (ASSETS-6884, ASSETS-6865)
* Ungültige Werte für einige der ARIA-Attribute beim Speichern einer Smart-Sammlung. (ASSETS-6882)
* Wenn Sie eine Smart-Sammlung speichern, sind einige Beschriftungen nicht ordnungsgemäß mit der Bildschirmlesehilfe verknüpft. (ASSETS-6881)
* Auf der Registerkarte IPTC der Asset-Eigenschaften gibt die Bildschirmlesehilfe die Beschriftung für die Felder des Suchbegriffformulars nicht an. (ASSETS-6879)
* In Experience Manager-Sammlungen wird die [!UICONTROL Email] nicht als Pflichtfeld identifiziert und keine Fehlermeldung angezeigt, wenn Sie keinen Wert angeben. (ASSETS-6877)
* In Experience Manager Files keine Fehlermeldung in **Linkfreigabe** wird in `Add Email Address`. Der Fehler wird nur unter Verwendung einer Farbe identifiziert. (ASSETS-6876, ASSETS-6875)
* [!UICONTROL Zuschneiden und Zuordnen] -Optionen haben beim Bearbeiten eines Assets nicht die programmatischen Namen. (ASSETS-6874)
* Für den Filtertext gibt es im Vergleich zur Hintergrundfarbe keine Vertragsration von 4,5:1. (ASSETS-6873)
* Der Text für den Ordnernamen auf der Hauptnavigationsseite weist kein Kontrastverhältnis zwischen 4,5 und 1 im Vergleich zur Hintergrundfarbe auf. (ASSETS-6872)
* Beim Ausführen der [!UICONTROL Kopieren] -Vorgang für Sammlungen, die **[!UICONTROL Benutzer hinzufügen]** Das Formularsteuerelement des Kombinationsfelds ist nicht korrekt mit seiner sichtbaren Beschriftung verknüpft. (ASSETS-6870)
* Die Sprachausgabe gibt die [!UICONTROL Erstellen] Schaltflächen-Untermenüoptionen. (ASSETS-6869)
* Die Optionen Umfang, Workflows und Zeitzone weisen kein Kontrastverhältnis von 4,5:1 im Vergleich zur Hintergrundfarbe auf. (ASSETS-6868)
* Die Bildschirmlesehilfe kündigt fälschlicherweise den Reduzierungsstatus der **Timeline** Spalte. (ASSETS-6864)
* Fehlende untergeordnete Elemente für einige ARIA-Rollen beim Speichern einer Smart-Sammlung. (ASSETS-6862)
* Beim Freigeben eines Assets sind ARIA-Attribute erforderlich für `Search/Add Email Address` nicht angegeben. (ASSETS-6860)
* Die **map** kann nicht über die Tastatur angezeigt werden. Stattdessen ist ein Mausklick erforderlich, um das Zuordnungsdialogfeld anzuzeigen. (ASSETS-6859)
* Fehlende untergeordnete Elemente für einige ARIA-Rollen auf der Registerkarte &quot;Allgemein&quot;der Seite &quot;Asset-Eigenschaften&quot;. (ASSETS-6858)
* Die leeren Texteingabefelder, die auf der Registerkarte &quot;IPTC&quot;der Asset-Eigenschaften verfügbar sind, weisen kein Kontrastverhältnis von 3:1 gegenüber den angrenzenden Farben auf. (ASSETS-6854, ASSETS-6847)
* Die Profilsymbole im **Timeline** -Abschnitt von den Bildschirmlesehilfen falsch erkannt werden. (ASSETS-6850)
* Die Sprachausgabe gibt nicht an, dass das Kombinationsfeld Prüfungsstatus , das auf der Registerkarte Allgemein der Asset-Eigenschaften verfügbar ist, ein schreibgeschütztes Feld ist. (ASSETS-6849)
* Die Beschriftung der Kontrollkästchen &quot;Alle auswählen&quot;und &quot;Anmerkung&quot;wird von der Sprachausgabe nicht ordnungsgemäß angekündigt. (ASSETS-6846)
* Der Tastaturfokus überspringt die `About Adobe Experience Manager` -Option verfügbar im **Hilfe anzeigen** Menü. (ASSETS-6845)
* Sprachausgaben geben die ausgewählten Ordner beim Navigieren durch die Ordnerliste mithilfe der Tastaturpfeile in der Kartenansicht nicht richtig an. (ASSETS-6844)
* Beim Hochladen einer PDF auf den Experience Manager nimmt die Speicherbelegung ständig zu. (ASSETS-16889)
* Wenn ein Workflow eine ZIP-Datei in einen Ordnernamen in Assets konvertiert, wird die Groß-/Kleinschreibung des ZIP-Dateinamens nicht beibehalten. (ASSETS-16712)
* Beim Wechsel von Brand Portal zu Experience Manager 6.5 zeigt der Benutzerprädikatsfilter keine geeigneten Ergebnisse an, wenn Sie den Filter zum ersten Mal anwenden. (ASSETS-15932)
* Video kann nicht kommentiert werden. (ASSETS-15217)
* **Veröffentlichung verwalten** -Option für einen Benutzer ohne Replikationszugriff ausgeblendet wird und `READ` und `WRITE` Zugriff auf `ETC` und `VAR`. (ASSETS-15007)
* Die Ladezeit für die Eigenschaftsseite erhöht sich für ein Asset mit mehreren Verweisen. (ASSETS-14182)
* Wenn die Veröffentlichung eines Bildes in Brand Portal rückgängig gemacht wird, macht der Experience Manager die Veröffentlichung auch in Dynamic Media rückgängig und es wird kein Bild auf der Live-Website angezeigt. (ASSETS-14118)
* XSS-Probleme bei Smart Crop-Karten in Dynamic Media. (ASSETS-14212, ASSETS-14208, ASSETS-13704)
* XSS-Problem in Viewer-Vorgaben in Dynamic Media. (ASSETS-13822)
* Validieren Sie den Benutzerzugriff bei der Vorschau von DM-Assets auf AEM. (CQ-4314757)


## Commerce  {#commerce-6515}

* Die Erstellung einer Store-Seite schlug fehl und stoppte den gesamten Katalog-Rollout-Prozess. (CQ-4347181)

## [!DNL Forms] {#forms-6515}

>[!NOTE]
>
>Fehlerbehebungen in [!DNL Experience Manager] Forms wird eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Veröffentlichungsdatum des Service Packs. In diesem Fall werden die Add-On-Pakete am Donnerstag, dem 1. Dezember 2022 veröffentlicht. Darüber hinaus wird diesem Abschnitt eine Liste mit Fehlerbehebungen und Verbesserungen für Forms hinzugefügt.

## [!DNL Sites] {#sites-6515}

* Die Konsole &quot;Experience Manager Sites Launches&quot;wurde leer angezeigt. (NPR-39188)
* Verweise wurden nicht angepasst, wenn die Seite, die den Verweis enthielt, auch während des Seitenverschubs aktiviert werden musste. (NPR-39061)
* Wenn ein Layout-Container mit dem übergeordneten Container nicht ausgeblendet wird, werden Layout-Änderungen nicht auf alle Komponenten innerhalb des verschachtelten Containers angewendet. (NPR-39041)
* Inhalte überschneiden sich jetzt nicht mehr mit anderen Inhalten mit einer Breite von 320 Pixel. (SITES-8885)
* Der Fokus wurde nach dem Schließen eines Dialogfelds hinzugefügt. (SITES-8885)

### Barrierefreiheit {#access-6515}

<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The scrollable region of the Page Editor did not have keyboard access. (SITES-2936) -->
<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The color input field of the Page Editor is not labeled or visible on the screen. (SITES-2925) -->
<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The iframe in the Page Editor is missing a title attribute; it must have an accessible name. (SITES-2894) -->
* Die **[!UICONTROL Anmerkung]** -Schaltfläche fehlt der Name der Barrierefreiheit. (SITES-2892)
* Der Status einer ACTIVE-Benutzeroberflächenkomponente (**[!UICONTROL Ausschneiden]**, **[!UICONTROL Kopieren]**, **[!UICONTROL Einfügen]**, **[!UICONTROL Komponenten einfügen]**, **[!UICONTROL Gruppe]** usw.) nicht mindestens ein Helligkeitskontrastverhältnis von drei zu einer Helligkeit mit dem inneren oder äußeren angrenzenden Hintergrund aufweist. (SITES-8889, SITES-8756, SITES-8885)
* Statusmeldung wird nicht automatisch angekündigt. (SITES-8889, SITES-8756, SITES-8885)
* Im Textinhalt fehlt das Kontrastverhältnis 4,5:1. (SITES-8756, SITES-8885)
* Für Link- oder Schaltflächentext fehlt das Kontrastverhältnis 4,5:1 beim Bewegen oder Fokus. (SITES-8756, SITES-8885)

### [!DNL Content Fragments] {#sites-contentfragments-6515}

* GraphQL löst eine Ausnahme aus. Sie können beispielsweise keine Varianten-Tags aus einem Inhaltsfragment abrufen. Es gibt keine Variation mit dem Namen &#39;elektrisch&#39;. Dieses Problem ist auf das Aufrufen von `getVariationTags` für eine nicht vorhandene Variante, die eine Ausnahme auslöst. (SITES-8898)
* Sortieren der Titelreihenfolge in der Listenansicht, sowohl aufsteigend als auch absteigend, wie die Titel mit der Reihenfolge A, C, B. (SITES-7585)
* Unterstützung für Tagging von Inhaltsfragmentvarianten hinzugefügt. (SITES-8168)
* Odin-spezifischer Code wurde in Experience Manager 6.5 identifiziert und entfernt, der nicht erforderlich war. (SITES-3574)
* Beim Veröffentlichen eines Sprachkopiefragments über die Benutzeroberfläche des Inhaltsfragment-Editors wurden die zugehörigen Verweise unter dem Ordner &quot;Englisch&quot;veröffentlicht. (NPR-39182)
* Datumsfelder werden vorab mit einem Datum ausgefüllt. (NPR-39124)
* Tags verschwanden, wenn Sie die Optionsfeld-Option zum zweiten Mal auswählen. (NPR-39071)

### Fluid XP {#sites-fluidxp-6515}

* Aktivieren der ES6-Kompilierungsunterstützung für die Client-Bibliothek `/libs/cq/gui/components/siteadmin/admin/restoretree/clientlibs/restoretree.js`. (NPR-39067)
* Das Multifield in einem Inhaltsfragmentmodell kann nicht geleert und gespeichert werden, da die Validierung auch dann erfolgt, wenn **[!UICONTROL Erforderlich]** nicht ausgewählt ist. (NPR-39063)
* In **[!UICONTROL Kopieren]** oder **[!UICONTROL Livecopy]** Aufgaben, die `cq:targetMetadata` -Informationen falsch dupliziert wurden. Diese Funktion führte dazu, dass zwei oder mehr Experience Fragments in Experience Manager auf dasselbe in Target exportierte Angebot verweisen. (NPR-38970)
* Nach der Aktion &quot;Baum wiederherstellen&quot;wird die Nachricht `Un-publication pending. #0 in the queue` wird in der Benutzeroberfläche für eine Seite angezeigt, die nie zuvor veröffentlicht wurde. (NPR-38847)

### Seiteneditor {#sites-pageeditor-6515}

* Die letzte Änderung am Text, der zur Komponente hinzugefügt wurde, wurde nicht rückgängig gemacht. Stattdessen wurde beim Aktualisieren der Seite die gesamte Komponente gelöscht. (SITES-8597)
* Upgrade `jquery-ui` auf die neueste Version zu setzen, führte dazu, dass der Seiteneditor nicht ordnungsgemäß funktionierte. (NPR-38596)
* Inhalte überschneiden sich jetzt nicht mehr mit anderen Inhalten mit einer Breite von 320 Pixel. (SITES-8756)
* Der Fokus wurde nach dem Schließen des Dialogfelds hinzugefügt (SITES-8756).

## Sling {#sling-6515}

* `Repoinit` hat die Erstellung oder Verwaltung von Gruppen mit Leerzeichen im Hauptnamen nicht unterstützt, da der Gruppenname als Zeichenfolge behandelt wurde und das Anführungszeichen nicht unterstützt wurde. (SLING-10952)
* Protokolle werden versehentlich mit Fehlermeldungen und Ausnahmen gefüllt. (NPR-39024)

## Übersetzungsprojekte {#translation-6515}

* Die Zielseite wurde dem Übersetzungsauftrag für aktualisierte Sprachkopien über das Bedienfeld &quot;Projekte&quot;hinzugefügt. Quellseite wurde nicht aktualisiert. (NPR-39278)
* Der Übersetzungsprozess schlug beim Generieren einer Vorschau für alle Seiten in einem Übersetzungsprojekt fehl. (NPR-39059)
* Wenn das Sprachgebietsschema nicht vorhanden ist, wird es weiterhin in einem Gebietsschema-Ordner erstellt, wenn Referenzregeln für ein Ereignis konfiguriert sind. (NPR-39054)

## Benutzeroberfläche {#ui-6515}

* In der Datei treten JavaScript-Fehler auf `multifield.js` für bestimmte Felder im Inhaltsfragmentmodell im Inhaltsfragmentmodelleditor und auch im Inhaltsfragment-Editor. (NPR-39350)

## Workflow {#workflow-6515}

* Workflows, die erfolgreich in Experience Manager 6.5.11 ausgeführt wurden, wurden in 6.5.13 von Experience Manager nicht konsistent ausgeführt. (NPR-39023)

## Installieren von [!DNL Experience Manager] 6.5.15.0 {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.15.0 erfordert [!DNL Experience Manager] 6.5. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die Adobe [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.15.0 mit dem Package Manager auf einer der Authoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
>Adobe rät davon ab, die [!DNL Experience Manager] 6.5.15.0-Paket. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie der `crx-repository` für den Fall, dass Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->

### Installieren des Service Packs auf [!DNL Experience Manager] 6.5 {#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie **[!UICONTROL Paket hochladen]** , um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Der Dialog auf der Package Manager-Benutzeroberfläche wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle für die Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Normalerweise tritt dieses Problem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.15.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.15.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.15.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (Zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Paket `org.apache.jackrabbit.oak-core` ist Version 1.22.13 oder höher (Zu verwendende Webkonsole: `/system/console/bundles`). <!-- NPR-39436 for 6.5.15.0 --> <!-- OAK VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des [!DNL Experience Manager] Forms Add-On-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie [!DNL Experience Manager] Forms nicht verwenden.

<!-- 
Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.
-->

1. Installieren sie unbedingt das [!DNL Experience Manager] Service Pack.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de#forms-updates) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-on-Paket wie unter [Installieren des AEM Forms-Add-on-Pakets](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package) beschrieben.
1. Wenn Sie in Experience Manager 6.5 Forms Briefe verwenden, installieren Sie das [neueste AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates).

### Installieren von [!DNL Experience Manager] Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in [!DNL Experience Manager] Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für [!DNL Experience Manager] Forms on JEE und zur Konfiguration nach der Implementierung finden Sie in den [Versionshinweisen ](jee-patch-installer-65.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für [!DNL Experience Manager] Forms on JEE installiert haben, installieren Sie das neueste Forms-Add-on-Paket, löschen das Forms-Add-on-Paket aus dem Ordner `crx-repository\install` und starten Sie den Server neu.

### UberJar {#uber-jar}

Das UberJar für [!DNL Experience Manager] 6.5.15.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.15/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.15</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstatt im Adobe Public Maven Repository (`repo.adobe.com`) verfügbar. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die ab [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie ein Feature oder eine Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, sodass sie eine alternative Option verwendet.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der **[!UICONTROL AEM Cloud Services-Anmeldebildschirm]** ist veraltet, da die [!DNL Experience Manager]- und [!DNL Adobe Target]-Integration in [!DNL Experience Manager] 6.5 aktualisiert wurde. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Sie unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren, der Assistent für die Anmeldung ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime]-Integrationen über die jeweiligen [!DNL Experience Manager]-Cloud-Services. |
| Connectoren | Der Adobe JCR-Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für [!DNL Experience Manager] 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->

* [AEM Inhaltsfragment mit GraphQL-Indexpaket 1.0.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.5.zip)
Dieses Paket ist für Kunden erforderlich, die GraphQL verwenden. Dadurch können sie die erforderliche Indexdefinition hinzufügen, die auf den tatsächlich verwendeten Funktionen basiert.

* Da [!DNL Microsoft® Windows Server 2019] [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1] nicht unterstützt, unterstützt [!DNL Microsoft® Windows Server 2019] keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie für Ihre [!DNL Experience Manager]-Instanz ein Upgrade von der Version 6.5 auf 6.5.10.0 durchführen, können Sie `RRD4JReporter`-Ausnahmefehler in der Datei `error.log` anzeigen. Um dieses Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein früheres Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie des benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mithilfe der HTTP-API mit der Laufzeitkopie zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfiguriert, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaften-Browser angezeigt. Das Konfigurieren eines anderen Feldes des adaptiven Formulars im selben Editor behebt das Problem.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in [!DNL Experience Manager] über die Target Standard-API (IMS-Authentifizierung) und dann über den Export von Experience Fragments in Target werden falsche Angebotstypen erstellt. Anstelle des Typs &quot;Experience Fragment&quot;bzw. der Quelle &quot;Adobe Experience Manager&quot;erstellt Target mehrere Angebote mit dem Typ &quot;HTML&quot;bzw. der Quelle &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` – Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Registrierungsänderung abgeschlossen wird, um die Registrierung abzuschließen.

* Wenn Sie versuchen, entweder Inhaltsfragmente oder Websites/Seiten zu verschieben/löschen/veröffentlichen, gibt es ein Problem, wenn Inhaltsfragmentreferenzen abgerufen werden, da die Hintergrundabfrage fehlschlägt; d. h. die Funktionalität ist nicht verfügbar.
Um den korrekten Vorgang sicherzustellen, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten hinzufügen `/oak:index/damAssetLucene` (keine Neuindizierung erforderlich):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## Enthaltene OSGI-Pakete und Inhaltspakete {#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5.15.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.15.0 enthaltenen OSGi-Pakete](/help/release-notes/assets/65150_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.15.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65150_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites {#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

