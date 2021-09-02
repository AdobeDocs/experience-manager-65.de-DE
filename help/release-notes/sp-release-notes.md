---
title: '[!DNL Experience Manager] 6.5 Service Pack - Versionshinweise'
description: Spezifische Versionshinweise für [!DNL Adobe Experience Manager] 6.5 Service Pack 10
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 496516f7f4b0e59bbfdae4cbe061a793f28449d2
workflow-type: tm+mt
source-wordcount: '4438'
ht-degree: 5%

---

# [!DNL Adobe Experience Manager] 6.5 Service Pack - Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.10.0 |
| Typ | Service Pack-Version |
| Datum | 26. August 2021 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip) |

## Was ist in [!DNL Adobe Experience Manager] 6.5.10.0 enthalten? {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.10.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.10.0 eingeführt wurden, sind:

* **Erweiterte  [!DNL Content Fragment] Modelle und Editor**: Sie können jetzt komplexe und benutzerdefinierte Modelle für strukturierte Inhalte mit verschachtelten  [!DNL Content Fragment] Modellen erstellen. Inhaltsstrukturen werden in grundlegende Elemente modularisiert, die als Unterfragmente modelliert werden. Fragmente mit einer höheren Ebene verweisen auf diese Unterfragmente. Weitere Verbesserungen des Datentyps, wie erweiterte Validierungsregeln, verbessern die Flexibilität der Inhaltsmodellierung mit [!DNL Content Fragments]. Der Editor [!DNL Experience Manager] [!DNL Content Fragment] unterstützt verschachtelte Fragmentstrukturen in einer gängigen Editorsitzung mit Verbesserungen wie Strukturbaumansicht und Registerkarten-Breadcrumb-Navigation durch Fragmenthierarchien.

* **GraphQL-API für[!DNL Content Fragments]**: Die neue GraphQL-API ist die Standardmethode zur Bereitstellung strukturierter Inhalte im JSON-Format. Mit GraphQL-Abfragen können Kunden nur die relevanten Inhaltselemente anfordern, um ein Erlebnis zu rendern. Durch eine solche Auswahl wird die Überbereitstellung von Inhalten (Möglichkeit mit HTTP-REST-APIs) eliminiert, die das Parsen von Inhalten auf Client-Seite erfordert. GraphQL-Schemas werden von [!DNL Content Fragment]-Modellen abgeleitet und API-Antworten werden im JSON-Format erstellt. In [!DNL Experience Manager] als [!DNL Cloud Service] bleiben [GraphQL-Abfragen bestehen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) und verarbeiten Cache-freundliche GET Anforderungen. In [!DNL Experience Manager] 6.5.10.0 ist dies noch nicht möglich.

* **Hierarchieverwaltung und zukünftige Vorschau**: Benutzer haben jetzt eine Benutzeroberfläche, über die sie auf die Inhaltsstrukturen ihrer  [!DNL Experience Manager] Launches zugreifen können, einschließlich der Möglichkeit, Seiten in einem Launch hinzuzufügen und zu entfernen. Diese Funktion verbessert die Flexibilität von [!DNL Experience Manager]-Launches beim Erstellen von Inhaltsversionen, die für die zukünftige Veröffentlichung vorgesehen sind. [Zeitwarp-](/help/sites-authoring/working-with-page-versions.md#timewarp) Funktionen ermöglichen Benutzern, Launches als künftigen Inhaltsstatus in der Vorschau anzuzeigen.

* **Connected Assets**:  [!DNL Experience Manager] erweitert die  [!DNL Connected Assets] Funktionalität auf die Verwendung von  [!DNL Dynamic Media] Bildern in den entsprechenden Kernkomponenten. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* **Optionen zur Linkfreigabe zum Herunterladen von Assets oder Ausgabeformaten**: Beim Freigeben von Assets und Sammlungen als Link können Benutzer auswählen, ob sie den Download von Original-Assets oder deren Ausgabedarstellungen oder beide über den freigegebenen Link zulassen möchten. Außerdem erhalten Benutzer, die die über einen Link freigegebenen Assets herunterladen, die Option, nur die Original-Assets, nur die Ausgabeformate oder beides herunterzuladen.

* **Beschränken der erzeugten** Unter-Assets: Administratoren können die Anzahl der Teil-Assets einschränken, die für ebenenübergreifende Assets wie PDF-, PowerPoint-, InDesign- und Keynote-Dateien  [!DNL Experience Manager] generiert werden. Siehe [Verwalten von ebenenübergreifenden Assets](/help/assets/managing-linked-subassets.md#generate-subassets).

* **Camera Raw Unterstützung**: Es ist ein neues  [!DNL Camera Raw] Paket verfügbar, das  [!DNL Adobe Camera Raw] v10.4 unterstützt. Siehe  [Verarbeiten von Bildern mit [!DNL Camera Raw]](/help/assets/camera-raw.md).

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.8 aktualisiert.

* **Verbesserte Barrierefreiheit**:

   * [!DNL Dynamic Media] bietet viele Verbesserungen der Barrierefreiheit für Viewer. Siehe [[!DNL Dynamic Media] updates](#dynamic-media-65100).

   * Platform bietet einige Verbesserungen hinsichtlich der Barrierefreiheit. Siehe [Plattformaktualisierungen](#platform-65100).

* **Verbesserungen** der Benutzererfahrung:

   * [!DNL Experience Manager] zeigt direkt eine Liste aller Inhaltsmodelle unter einem Ordner an, ohne dass Inhaltsautoren durch die Dateistruktur navigieren müssen. Die Funktion erfordert jetzt weniger Klicks und verbessert die Authoring-Effizienz.

   * Das Pfadfeld im Editor [!DNL Sites] ermöglicht es Autoren, Assets aus [!DNL Content Finder] zu ziehen.

* Unterstützung für `GuideBridge#getGuidePath` API in [!DNL AEM Forms] hinzugefügt.

* Sie können jetzt den Service für die automatisierte Formularkonvertierung nutzen, um [PDF-Formulare in deutscher, französischer und spanischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#language-specific-meta-model) in adaptive Formulare umzuwandeln.

* **Fehlermeldungen im Eigenschaften-Browser**: Es wurden Fehlermeldungen für jede Eigenschaft im Eigenschaften-Browser für adaptive Formulare hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

* **Unterstützung für die Verwendung der Literaloption zum Festlegen des Werts für eine JSON-Typvariable**: Sie können die Literaloption verwenden, um Werte für eine JSON-Typvariable im Schritt &quot;set variable&quot;eines AEM-Workflows festzulegen. Mit der Option „Literal“ können Sie eine JSON in Form einer Zeichenfolge angeben.

* [Plattformaktualisierungen](../forms/using/aem-forms-jee-supported-platforms.md):  [!DNL Adobe Experience Manager Forms] on JEE unterstützt nun die folgenden Plattformen:
   * [!DNL Adobe Acrobat 2020]
   * [!DNL Ubuntu 20.04]
   * [!DNL Open Office 4.1.10]
   * [!DNL Microsoft Office 2019]
   * [!DNL Microsoft Windows Server 2019]
   * [!DNL RHEL8]

Eine Liste aller Funktionen und Verbesserungen, die in [!DNL Experience Manager] 6.5.10.0 eingeführt wurden, finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 10](new-features-latest-service-pack.md).

Im Folgenden finden Sie eine Liste der Fehlerbehebungen in [!DNL Experience Manager] 6.5.10.0-Version.

### [!DNL Sites] {#sites-65100}

* Der Fokus wird bei der Eingabe in das Feld **[!UICONTROL Standardwert]** unter der Registerkarte **[!UICONTROL Eigenschaften]** des Inhaltsfragmente-Editors (NPR-36992) auf ein anderes Feld verschoben.

* Beim Filtern von [!DNL Content Fragment]-Modellen unter einem angegebenen Pfad gibt die [!DNL Experience Manager]-Suche alle Knoten mit `cq:Template` zurück, anstatt nur Pfade und Knoten für das [!DNL Content Fragment]-Modell zurückzugeben (SITES-1453).
* [!DNL Content Fragments] gibt  `null` den Status von Ordnern zurück (SITES-1157).
* [!DNL Experience Manager] lässt Benutzer  [!DNL Content Fragment] Modelle nicht deaktivieren und aktivieren (SITES-1088).
* Wenn ein Benutzer [!DNL Content Fragments]- oder Medien-Assets verschiebt, umbenennt oder löscht, werden die referenzierten [!DNL Content Fragments] nicht automatisch aktualisiert (SITES-196).
* Das Einfügen von Komponenten von einer Seite auf eine andere führt zu JavaScript-Fehlern (NPR-37030).
* Wenn Seiteneigenschaften schnell angezeigt werden, werden Seiteneigenschaften für eine andere Seite geöffnet (NPR-37025).
* Mit dem Inhaltsfragment kann das Inhaltsfragment auf sich selbst verweisen. Der Picker unterstützt den Vorgang nicht (NPR-36993).
* Nach dem Upgrade auf Service Pack 9 können einige Benutzer keine Ordner in Experience Manager verschieben und Fehler in den Protokollen sehen (SITES-1481).
* Beim Anpassen der Breite der Komponente im Layout-Container im Bearbeitungsmodus wird ein Flackern beobachtet (NPR-36961).
* Beim Bewerben eines Launches werden die Änderungen im beworbenen Launch für die anderen Launches doppelt bereitgestellt. Wenn ein Benutzer den doppelten Rollout-Launch fördert, wird der doppelte Inhalt auf der Quellseite angezeigt (NPR-36893).
* [!DNL Experience Manager] fügt einigen PNG-Bildern einen grauen Rahmen mit Transparenz hinzu, wenn Sie die Bilder mithilfe der Bild-Kernkomponente zu einer Seite hinzufügen oder wenn Sie die Größe mithilfe der Foundation-Bildkomponente ändern (NPR-36879).
* [!DNL Experience Manager Sites] Die Administrator-Benutzeroberfläche mit einer hohen Anzahl von Vorlagen führt zu langsamer Navigation (NPR-36870).
* Ein Upgrade auf Service Pack 9 verhindert das Authoring einiger Komponenten. Dieses Problem erlaubt [!DNL Sites] Benutzern nicht, neue Seiten zu erstellen (NPR-36857).
* Die `ContextHubImpl`-Methode erstellt ein `ResourceResolver` , das nicht geschlossen ist. Dies führt zu Warnmeldungen über langwierige `ResourceResolver` und der Dienst gibt manchmal unerwartete Ergebnisse zurück (NPR-36853).
* Beim Synchronisieren einer einzelnen Live Copy aus den Eigenschaften der Blueprint-Seite werden auch alle anderen Live Copies synchronisiert (NPR-36829, NPR-36522).
* Wenn nur der XLS-MIME-Typ verwendet wird, funktioniert die Datei-Upload-Funktion nicht wie erwartet (NPR-36785).
* Neue Tags mit Groß-/Kleinschreibung und alle Wörter in Großbuchstaben werden nicht im Tag-Feld unter [!DNL Content Fragments] angezeigt. (NPR-36742)
* Die Option Einzelnes Textelement beim Hinzufügen eines [!DNL Content Fragment] führt dazu, dass Text fehlt, und erstellt ungerade Formatierungen im Zusammenhang mit Listen und verschachtelten Listen (NPR-36565).
* Wenn ein Autor eine Komponente auf einer Seite kommentiert, die Komponente löscht und den Löschvorgang rückgängig macht, tritt beim Versuch, die Timeline-Daten für die Seite in der Sites-Konsole anzuzeigen, ein Fehler auf (NPR-36528).
* Seiteneigenschaften Die Option [!UICONTROL Speichern und schließen] des Bulk Editors speichert Änderungen, schließt den Editor jedoch nicht (NPR-36527).
* Wenn ein Benutzer versucht, eine neue Textkomponente per Drag-and-Drop auf eine Seite zu ziehen, wird die Komponente sofort ausgeblendet (NPR-36442).
* Wenn ein Benutzer in ein On-Demand-Tag eingibt, das Leerzeichen enthält (das Tag, das nicht im System vorhanden ist), und die Eingabetaste drückt, wird das Tag unter dem Feld angezeigt. Wenn [!DNL Content Fragment] jedoch gespeichert und erneut geöffnet wird, wird das On-Demand-Tag nicht angezeigt (NPR-36441).
* Die Vorlage kann nicht gelöscht werden, wenn auf die Instanz über den Dispatcher zugegriffen wird (NPR-36385).
* Wenn eine Seite verschoben wird, ist eine manuelle Aktualisierung des Browsers erforderlich, um die Änderungen zu rendern (NPR-36381).
* Wenn Sie eine Komponente auswählen, können Sie sie mit Strg+X oder Strg+C ausschneiden oder kopieren (und Befehl+X oder Befehl+C unter Mac). Wenn Sie auf eine andere Komponente klicken, können Sie sie mit der Symbolleiste einfügen, nicht jedoch mit der Tastatur (Strg+V oder Befehl+V) (NPR-36379).
* Wenn ein Benutzer versucht, Komponenten mithilfe des Schere-Symbols zu schneiden, um sie an eine andere Stelle zu verschieben, tritt ein Konsolenfehler auf. Außerdem wird beim Einfügen nur eine Komponente verschoben (NPR-36378).
* [!DNL Experience Manager] über eine Abfrage ohne Index auf WCM oder Benachrichtigungen verfügt, verlangsamt sie die Leistung (NPR-36303).
* Wenn ein Autor die Vererbung für die gelöschte geerbte Komponente wiederherstellt, besteht die verfügbare Option darin, den gesamten Seiteninhalt zu synchronisieren. Die Inhaltsautoren müssen die gesamte Seite synchronisieren, selbst wenn die Vererbung nur für eine Komponente wiederhergestellt wird. Eine vollständige Synchronisierung kann dazu führen, dass unerwünschte Inhalte synchronisiert werden (NPR-34456, CQ-4310183).
* Die Live-Nutzung einer Komponente in der -Autoreninstanz zeigt nicht alle Vorkommen an. Einige Komponenten werden auf mehr als 1000 Seiten verwendet, der Bericht zeigt jedoch nur etwa 40 Seiten an (CQ-4323724).
* Wenn es eine Site-Struktur mit vielen Unterseiten gibt, dauert das Laden der Unterseiten in der Spaltenansicht in Experience Manager 6.5.8 im Vergleich zu Experience Manager 6.4.8.2 (CQ-4322766) länger.
* Das Deaktivieren von &quot;Alle&quot;funktioniert nicht bei der Option &quot;Rollout-Seite&quot;(NPR-37070).
* Beim Öffnen einer vorhandenen v3-Komponentenversion einer Seite wird das Dialogfeld &quot;Seiteneigenschaften&quot;nicht geöffnet und ein `NullPointerException` wird protokolliert (SITES-1830).

### [!DNL Assets] {#assets-65100}

Die folgenden Probleme wurden in [!DNL Assets] behoben:

* Der Wert der Eigenschaft `jcr:title` wird nach dem Verschieben eines Ordners nicht auf der Veröffentlichungsinstanz aktualisiert. Beim Umbenennen und erneuten Veröffentlichen eines Ordners innerhalb des Autors wird der Eigenschaftswert `jcr:title` in der Veröffentlichungsinstanz nicht aktualisiert (NPR-36369).

* Wenn zwei oder mehr Assets ausgewählt und ein oder mehrere Metadatenfelder bearbeitet werden, schlägt der Speichervorgang mit dem Fehlercode 500 im Safari-Browser fehl (NPR-36413).

* Der Massenimport von Metadaten schlägt aufgrund eines falschen Datumsformats fehl (NPR-36428).

* Wenn eine Auswahl auf der Seite [!UICONTROL Eigenschaften] getroffen wird, um Metadaten zu aktualisieren, reagiert die Oberfläche langsam, wenn das Schema viele Optionen bereitstellt (NPR-36430).

* Suchfilter mit dem Prädikat [!UICONTROL Ablaufstatus] funktioniert nicht (NPR-36436).

* Das Popup-Menü für verschiedene Felder in den Eigenschaften [!UICONTROL Ordner-Metadaten] zeigt nicht die zuletzt ausgewählten Werte an (NPR-36937, CQ-4314429).

* Wenn der Benutzer bei der Suche nach Dateien und Ordnern einen Filter anwendet und [!UICONTROL Dateien und Ordner] auswählt, werden nur die Dateien angezeigt, jedoch nicht der Ordner (CQ-4319543, NPR-36627).

* Die Symbolleistenoptionen unterscheiden sich, wenn dieselbe Sammlung aus einem Ordner ausgewählt und aus einem Suchergebnis ausgewählt wird (NPR-36620).

* Die Option [!UICONTROL Quick Publish] ist nicht auf der Suchergebnisseite verfügbar (NPR-36904, CQ-4317748).

* Wenn Benutzer eine Live Copy eines Assets erstellen, ohne dessen Erweiterung anzugeben, ist die Live Copy-Datei nach dem Herunterladen nicht verwendbar (NPR-36903, CQ-4326305).

* Wenn ein Benutzer als Eigentümer eines untergeordneten Ordners hinzugefügt wird, erhält der Benutzer auch die Eigentümerberechtigung für den übergeordneten Ordner und somit für die anderen untergeordneten Ordner des übergeordneten Ordners. Außerdem wird der Benutzer beim Versuch, ihn zu entfernen, nicht als Eigentümer des übergeordneten Ordners entfernt. (NPR-36801, CQ-4323737).

* [!DNL Experience Manager] generiert eine Speicherausnahme, wenn Sie versuchen, Teil-Assets für ebenenübergreifende Assets wie eine PowerPoint-Präsentation zu erstellen (NPR-36668).

* Wenn Benutzer ein Asset verschieben, das bereits auf einer veröffentlichten Siteseite verwendet wird, wird die Siteseite erneut veröffentlicht, auch wenn die Option zum Veröffentlichen nicht ausgewählt ist (NPR-36636, CQ-4323500).

* Bei Verwendung der Funktion zur Erkennung des Apache Tika MIME-Typs lassen die mit der Methode `AssetManager.createAsset` hochgeladenen Assets eine temporäre Datei mit dem Namen `apache-tika-*.tmp` im temporären Verzeichnis. Diese temporäre Datei verwendet den gesamten verfügbaren freien Speicherplatz (NPR-36545).

* Alle DRM-geschützten Assets werden heruntergeladen und die Benutzerauswahl zum Herunterladen bestimmter Assets wird nicht befolgt. (CQ-4327422)

* Assets können nicht in `pathfield` auf die Benutzeroberfläche gezogen werden (NPR-36849).

* Wenn Sie ein Asset in der Spaltenansicht auswählen, wird das Bedienfeld &quot;Asset-Details&quot;ausgeblendet (NPR-36667).

### [!DNL Dynamic Media] {#dynamic-media-65100}

**Verbesserte Barrierefreiheit**

Die folgenden Verbesserungen der Barrierefreiheit sind in [!DNL Dynamic Media Viewers] verfügbar.

* Bildschirmlesehilfen kommentieren jetzt den Platzhaltertext, um E-Mail-Adresse als erforderliches Feld für freigegebene Assets als Link-Dialogfeld zu suchen und hinzuzufügen. Außerdem wird das [!UICONTROL Bitte füllen Sie dieses Feld] QuickInfo aus (CQ-4327761).

* Bildschirmlesehilfen kommentieren nun die Namen und Zwecke verschiedener Felder im [!UICONTROL Bildvorgabeneditor] beim Zugriff auf die Felder der Benutzeroberfläche über die Tastatur korrekt (CQ-4325677).

* Der Tastaturfokus wechselt nun entsprechend zur Registerkarte &quot;Suche&quot;des Dialogfelds [!UICONTROL Viewer-Vorgaben] aus der Asset-Auswahl der Option [!UICONTROL Rich-Media-Typ] (CQ-4324736).

* Beim Navigieren im Formularmodus mithilfe von Tastaturbefehlen kommentieren die Bildschirmlesehilfen die Beschriftungen, die den Inkrement- und Dekrementoptionen auf der Registerkarte [!UICONTROL Erstellen] von [!UICONTROL Bildvorgaben] entsprechen. (CQ-4323900)

* Bildschirmlesehilfen geben jetzt die Option [!UICONTROL E-Mail-Adresse suchen und hinzufügen] im Dialogfeld &quot;Assets als Link freigeben&quot;an (CQ-4323352).

* Der Tastaturfokus wird in der Symbolleiste beim Navigieren in Assets mit Tastaturtasten beibehalten (CQ-4322037).

* Bildschirmlesehilfen kommentieren jetzt die neu hinzugefügten [!UICONTROL Bearbeiten]-Feldinformationen, nachdem sie die Option [!UICONTROL Zuschneiden hinzufügen] auf der Seite [!UICONTROL Responsives Bild zuschneiden] auf [!UICONTROL Bildverarbeitungsprofil bearbeiten] ausgewählt haben (CQ-4290734).

* Auf den Seiten [!UICONTROL Bildvorgabe bearbeiten] und [!UICONTROL Interaktives Video erstellen] geben Bildschirmlesehilfen jetzt die Seitenüberschrift beim Navigieren auf den Seiten mit Überschriften-Tastaturbefehlstaste (CQ-4290730) entsprechend an (CQ-4290701).

* Bildschirmlesehilfen können jetzt die verschiedenen Bereiche des Bildschirms (z. B. den rechten Bereich, den linken Bereich, die Aktionssymbolleiste, das Wahrzeichen der Viewer-Symbolleiste und das Zoombare Bild-Wahrzeichen) mithilfe von Tastaturbefehlen für Wahrzeichen und Regionen erkennen, wenn sie auf den folgenden Seiten navigieren.

   * [!UICONTROL Viewer-Vorgabeneditor]  (CQ-4290729)

   * [!UICONTROL Bildset-Editor]  (CQ-4290710)

   * [!UICONTROL Interaktives Video erstellen]  (CQ-4290702).

* Bildschirmlesehilfen geben jetzt den Namen für die Freigabeoption im Videoframe an, wenn sie mit der Pfeiltaste nach unten navigieren (CQ-4290728).

* Bildschirmlesehilfen kommentieren jetzt die Namen für verschiedene Optionen in den Registerkarten [!UICONTROL Sprite] und [!UICONTROL Hintergrund] auf der Registerkarte [!UICONTROL Erscheinungsbild] in [!UICONTROL Viewer-Vorgabe-Editor] (CQ-4290727).

* Obligatorische Felder, wie das zu bearbeitende Feld [!UICONTROL Breite] auf der Registerkarte [!UICONTROL Einfach] von [!UICONTROL Videokodierung bearbeiten] haben jetzt ein Sternchen-Symbol (*) (CQ-4290725).

* Bildschirmlesehilfen geben nun die Beschriftung für die Optionen auf der Seite [!UICONTROL Bildprofile] an (CQ-4290723).

* Windows-Benutzer können nun im [!UICONTROL Viewer-Vorgabeneditor] aus dem erweiterten CSS-Editor navigieren, wenn der Fokus auf dem CSS-Editor liegt (CQ-4290720).

* Auf der Registerkarte [!UICONTROL Einfach] von [!UICONTROL Bildvorgabe bearbeiten] beim Navigieren im Formularmodus beschreiben die Bildschirmlesehilfen jetzt die Beschriftungen für verschiedene Bearbeitungsfelder und Optionen (CQ-4290717).

* Bildschirmlesehilfen beschreiben jetzt die Rolle und den Status (ausgewählt oder nicht ausgewählt) für Benutzeroberflächenoptionen auf der linken Navigationsleiste auf der Detailseite der Assets (CQ-4290709).

* Bildschirmlesehilfen kommentieren jetzt den Status (ausgewählt oder nicht ausgewählt) und den Link für die Bildumschalter auf der Registerkarte [!UICONTROL Inhalt] der Seite [!UICONTROL Interaktives Video erstellen] korrekt (CQ-4290707).

* Bildschirmlesehilfen kommentieren jetzt den Namen, die Rolle und den Status verschiedener Segmente in der Skala der Video-Timeline korrekt, wenn sie mit der Pfeiltaste nach unten auf der Seite [!UICONTROL Interaktives Video erstellen] navigieren (CQ-4290706).

* Bildschirmlesehilfen kommentieren jetzt den Namen, die Rolle und den Standardstatus (ausgewählt oder nicht ausgewählt) sowie die Eigenschaft beim Navigieren zu den Optionen auf der Seite [!UICONTROL Interaktives Video erstellen] (CQ-4290704).

* Bildschirmlesehilfen beschreiben jetzt den Namen, die Rolle und den Standardstatus (ausgewählt oder nicht ausgewählt) der Optionen in den Optionen [!UICONTROL Alle Assets] und [!UICONTROL Alle Sammlungen] bei der Navigation auf der Seite [!UICONTROL Veröffentlichen] (CQ-4290705).

* Wenn Sie ein nicht unterstütztes Videoformat (außer MP4) auf die Seite [!UICONTROL Interaktives Video erstellen] hochladen, zeigt Experience Manager Fehlermeldungen an und kündigt sie an (CQ-4290700).

* Der Kontrast der Zahlen (Zeit in Sekunden) in der Zeitleistenskala auf der Seite [!UICONTROL Interaktives Video erstellen] erreicht jetzt das erforderliche minimale Luminanzverhältnis, sodass Benutzer mit eingeschränkter Farbwahrnehmung problemlos lesen können (CQ-4290699).

* Bildschirmlesehilfen geben jetzt die Beschriftung für das Feld [!UICONTROL Produktname] an, wenn sie durch die Seite [!UICONTROL Interaktives Video erstellen] navigieren (CQ-4290697).

**Behobene Probleme**

Die folgenden Fehlerbehebungen sind in [!DNL Dynamic Media] verfügbar.

* Hochgeladene Videos in [!DNL Experience Manager] zeigen `Process failed` an, nachdem der Ausführungsmodus `dynamicmedia_scene7` aktiviert und die Synchronisierung deaktiviert ist (CQ-4327791).

### Plattform {#platform-65100}

In diesem Service Pack werden die folgenden Verbesserungen bereitgestellt:

* Wenn ein Benutzer ein Element in der Baumansicht auswählt, geben die Bildschirmlesehilfen die Auswahl und die Symbolleistenoptionen an, die oben angezeigt werden (NPR-36504).
* Einige Text- und Kontrollnamen sind für Benutzer mit Sehproblemen leichter lesbar, da das Lichtstärkenverhältnis das erforderliche Mindestverhältnis von 4,5:1 erreicht (NPR-36503).
* Wenn ein Benutzer die Kalendersteuerelemente verwendet, liest die Bildschirmlesehilfe die beschreibenden Informationen zu Datum, Monat und Wochentag. Wenn ein Benutzer die Kalenderverknüpfung verwendet, liest die Bildschirmlesehilfe die Änderung in Datum, Monat und Jahr vor (NPR-36498).
* Unterstützung für die Ausführung von benutzerdefiniertem JavaScript `Clientlibs` mit ECMAScript 6-Funktionen, ohne den strikten Modus einzuhalten. Insbesondere wird das `emitUseStrict`-Flag zum `GCCScriptProcessor` (NPR-36411) hinzugefügt.

Die folgenden Fehlerbehebungen sind Teil dieses Service Packs:

* Benutzerdefinierte Konsistenzprüfungen werden häufiger als geplant ausgeführt (NPR-36985).
* Die `Resourceresolver map`-Methode gibt ein falsches Ergebnis für Alias-Seiten zurück (NPR-36767).
* [!DNL Experience Manager] Das Starten wird aufgrund von Lade-Workflows verzögert. (NPR-36615)

### Integrationen {#integrations-65100}

* Experience Manager reagiert nicht mehr, wenn der primäre MongoDB-Knoten zu einem anderen Knoten wechselt (NPR-36566).
* [!DNL Sling content distribution] schlägt bei der Ausführung des Löschvorgangs des Sammlungsmitglieds fehl (NPR-36521, CQ-4323578).

### Benutzeroberfläche {#user-interface-65100}

* Das seitliche Bedienfeld **[!UICONTROL Verweise]** zeigt keine Asset- und Site-Verweise an (GRANITE-35078, GRANITE-34892).

### Übersetzungsprojekte {#translation-65100}

* Zusätzliche Unterseiten in einer Sprachkopie eines Projekts mit mehreren Übersetzungen werden gelöscht (NPR-36622).

### Workflow {#workflow-65100}

* Wenn der Server eine Abwesenheitsnachricht erhält, meldet er Speicherwarnungen und reagiert nicht mehr. (NPR-36768)

### [!DNL Communities] {#communities-65100}

* Die Seiten der Community-Site werden im Status `LoggedIn` für anonyme Gastbenutzer geöffnet (NPR-36908).

* Wenn sich auf der Seite **[!UICONTROL Community]** > **[!UICONTROL Ideen]** > **[!UICONTROL Kommentare]** mehr als eine Seite befindet, funktioniert die Seitennavigation nicht (NPR-36541).

<!--
Need to verify with Engineering, the status is currently showing as Resolved
-->


<!--
### [!DNL Brand Portal] {#brandportal-65100}

*
-->

### [!DNL Forms] {#forms-65100}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.


**Adaptive Formulare**

* Wenn die für die Feldwerte in einem adaptiven Formular durchgeführten Überprüfungen erfolgreich sind, kann [!DNL AEM Forms] das Formulardatenmodell nicht aufrufen. (CQ-4325491)

* Wenn Sie ein Sprachwörterbuch zu einem Übersetzungsprojekt hinzufügen und dann das Projekt öffnen, zeigt [!DNL AEM Forms] eine Fehlermeldung an (CQ-4324933):

   ```TXT
   Uncaught TypeError: Cannot read property 'PROJECT_LISTING_PATH' of undefined
   at openButtonClickHandler (clientlibs.js:245)
   at HTMLButtonElement.onclick (clientlibs.js:258)
   ```

* Leistungsprobleme nach der Installation von [!DNL AEM Forms] Service Pack 7 (CQ-4326828).

**Korrespondenzverwaltung**

* Verzögerung bei der Anzeige von Zeichen auf der Registerkarte [!UICONTROL Daten] sowie in der HTML-Briefvorschau (NPR-37020).

* Wenn Sie ein Textdokumentfragment bearbeiten, werden die neuen Wörter nach dem Speichern des Fragments als HTML-Tags angezeigt (NPR-36837).

* Die als Entwürfe gespeicherten Briefe können nicht angezeigt werden. (NPR-36816)

* Wenn Sie ein Textdokumentfragment bearbeiten und dann eine Vorschau des Briefs anzeigen, zeigt AEM Forms die Ausdruckssprache in der HTML-Briefvorschau an (CQ-4322331).

* Probleme beim Rendern von Daten mit einer Self-Service-Briefvorlage (NPR-37161).


**Interaktive Kommunikation**

* Jedes Mal, wenn Sie eine Vorschau einer interaktiven Kommunikation nach der Bearbeitung eines Textdokumentfragments drucken, wird ein Tabulatorzeichen zwischen zwei Wörtern dupliziert. (NPR-37021)

* [!DNL AEM Forms] zeigt einen Fehler an, wenn Sie ein Textdokumentfragment speichern, das die maximale Größenbeschränkung überschreitet (NPR-36874).

* Wenn Sie ein Bild zu einer interaktiven Kommunikation hinzufügen, wird nach dem Bild ein zusätzlicher leerer Block angezeigt (NPR-36659).

* Wenn Sie den gesamten Text in einem Editor auswählen, können Sie den Schriftarttext nicht in Arial ändern (NPR-36646).

* Wenn Sie eine URL in einem Editor erstellen und eine Vorschau der Änderungen anzeigen, wird anstelle des URL-Textes ein schwarzer Hintergrund angezeigt (NPR-36640).

* Beim Kopieren und Einfügen von Text in einen Editor treten beim Ändern der Schriftart in Arial für Aufzählungszeichen im Dokument Probleme auf (NPR-36628).

* Einzugsprobleme für Aufzählungszeichen im Texteditor (NPR-36513).

**Designer**

* Screen Reader kann keine unverankerten Felddaten lesen, die innerhalb einer Textbeschriftung auf der Übergeordneten Seite oder auf Teilformularseiten in einer dynamischen PDF-Datei platziert wurden (CQ-4321587).

**Document Services**

* Wenn Sie XDP-Dateien in PDF-Dateien konvertieren und dann die resultierende PDF-Datei zusammenführen, schlägt die Generierung der PDF-Datei fehl und zeigt die folgende Fehlermeldung an:

   ```TXT
   Caused by: com.adobe.fd.assembler.client.AssemblerException$ClientException: Document is in a disposed state!
   ```

**Formular-Workflow**

* Ein Formular kann nach der Aktualisierung auf AEM Forms Service Pack 8 nicht an einen Workbench-Prozess gesendet werden (CQ-4325846).

**HTML5-Formulare**

* Wenn Sie den Wert für die `mfAllowAttachments`-Eigenschaft auf `True` im CRX DE-Repository festlegen, wird `dataXml` beim Senden des HTML5-Formulars beschädigt (NPR-37035).

* Wenn Sie eine XDP mit `dataXml` als HTML rendern, zeigt [!DNL AEM Forms] einen `Page Unresponsive`-Fehler an (NPR-36631).

### Commerce {#commerce-65100}

* Der Wert im Feld **[!UICONTROL Veröffentlicht von]** ist in der Spaltenansicht nicht korrekt (NPR-36902).
* Wenn ein Katalog eingeführt wird, werden neue Produkte fälschlicherweise als geänderte Produkte gekennzeichnet (NPR-36666).
* Wenn Sie ein gelöschtes Produkt neu erstellen, wird die Produktseite nicht neu erstellt (NPR-36665).
* Geänderte Seiten werden aktualisiert, aber die entsprechenden verknüpften Produkte werden beim Rollout des Katalogs nicht aktualisiert (CQ-4321409, NPR-36422).
* Die Workflows **[!UICONTROL Später veröffentlichen]** und **[!UICONTROL Veröffentlichung später rückgängig machen]** funktionieren nicht. (CQ-4327679)

Informationen zu Sicherheitsupdates finden Sie auf der [[!DNL Experience Manager] Seite mit Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.10.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.10.0 ist Experience Manager 6.5 erforderlich. Detaillierte Anweisungen finden Sie unter [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) .
* Der Service Pack-Download ist auf der Adobe [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.10.0 mithilfe des Package Managers auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, das [!DNL Adobe Experience Manager] 6.5.10.0-Paket zu entfernen oder zu deinstallieren.

### Service Pack installieren {#install-service-pack}

Gehen Sie wie folgt vor, um das Service Pack auf einer [!DNL Adobe Experience Manager] 6.5-Instanz zu installieren:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip) herunter.

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. In der Regel tritt dieses Problem im Browser [!DNL Safari] auf, kann aber gelegentlich auch in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, [!DNL Experience Manager] 6.5.10.0 automatisch auf einer funktionierenden Instanz zu installieren:

A. Platzieren Sie das Paket im Ordner `../crx-quickstart/install` , wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true` , damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.10.0 unterstützt nicht die Installation von Bootstraps.

**Installation überprüfen**

1. Auf der Seite mit den Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.10.0)` unter [!UICONTROL Installierte Produkte] angezeigt.

1. Alle OSGi-Bundles sind entweder **[!UICONTROL ACTIVE]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Web-Konsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Adobe Experience Manager Forms Add-On-Paket installieren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie Experience Manager Forms nicht verwenden. Fehlerbehebungen in Experience Manager Forms werden eine Woche nach der geplanten Veröffentlichung des Service Packs über ein separates Add-On-Paket bereitgestellt.[!DNL Experience Manager]

1. Stellen Sie sicher, dass Sie das Adobe Experience Manager Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms Add-On-Paket wie unter [Installieren von AEM Forms Add-On-Paketen](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package) beschrieben.

>[!NOTE]
>
>Experience Manager 6.5.10.0 enthält eine neue Version von [AEM Forms-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf Experience Manager 6.5.10.0 aktualisieren, installieren Sie die neueste Version des Pakets nach der Installation des Forms-Add-On-Pakets.

### Installieren von Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für Experience Manager Forms on JEE und zur Konfiguration nach der Bereitstellung finden Sie in den [Versionshinweisen](jee-patch-installer-65.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für Experience Manager Forms on JEE installiert haben, installieren Sie das neueste Add-On-Paket für Forms, löschen Sie das Add-On-Paket für Forms aus dem Ordner `crx-repository\install` und starten Sie den Server neu.


### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.10.0 ist im [Maven Central Repository](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.10/) verfügbar.

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und Einschließen der folgenden Abhängigkeit in Ihr Projekt-POM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.10</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstelle des Adobe Public Maven-Repositorys (`repo.adobe.com`) verfügbar. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Es gibt also kein `classifier`-Tag mit `apis` als Wert für das `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Nachstehend finden Sie eine Liste der Funktionen, die mit [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und in einer zukünftigen Version später entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm **[!UICONTROL AEM Cloud Services Opt-in]** wird nicht mehr unterstützt, da die Integration von [!DNL Experience Manager] und [!DNL Adobe Target] in Experience Manager 6.5 aktualisiert wurde. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über die Adobe IMS und [!DNL Adobe I/O] und unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren. Der Opt-in-Assistent ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, die Adobe IMS-Authentifizierung und die [!DNL Adobe I/O] Integrationen über die entsprechenden [!DNL Experience Manager]-Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* (Nur für JBoss unter Microsoft Windows) Um den Dienst &quot;PDF erstellen&quot;unter [!DNL AEM Forms on JEE] weiterhin zu verwenden, laden Sie [omniORB_4.1.1_x86_win32_vc10.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/omniORB_4.1.1_x86_win32_vc10.zip) aus Softwareverteilung herunter, extrahieren Sie den Ordner in der ZIP-Datei und kopieren Sie ihn an den folgenden Speicherort:
   `[AEM Forms Installation]\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\CommonNatives\lib`

* Da [!DNL Microsoft Windows Server 2019] [!DNL MySQL 5.7] und [!DNL JBoss EAP 7.1] nicht unterstützt, unterstützt [!DNL Microsoft Windows Server 2019] keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5 auf 6.5.10.0 aktualisieren, können Sie `RRD4JReporter` Ausnahmen in der Datei `error.log` anzeigen. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die OSGi-Pakete und Inhaltspakete aufgelistet, die in [!DNL Experience Manager] 6.5.10.0 enthalten sind:

* [Liste der in Experience Manager 6.5.10.0 enthaltenen OSGi-Bundles](assets/65100_bundles.txt)

* [Liste der in Experience Manager 6.5.10.0 enthaltenen Inhaltspakete](assets/65100_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Weitere Informationen finden Sie unter [Kontaktaufnahme mit der Adobe-Kundenunterstützung](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 - Versionshinweise](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

