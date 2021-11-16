---
title: '[!DNL Experience Manager] 6.5 Service Pack - Versionshinweise'
description: Spezifische Versionshinweise für [!DNL Adobe Experience Manager] 6.5 Service Pack 10
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 0a35b26c5f790d67db55421b8f3e98e5ddb30528
workflow-type: tm+mt
source-wordcount: '4430'
ht-degree: 6%

---

# [!DNL Adobe Experience Manager] 6.5 Service Pack - Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.10.0 |
| Typ | Service Pack-Version |
| Datum | 26. August 2021 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip) |

## Was ist enthalten in [!DNL Adobe Experience Manager] 6,5,10,0 {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.10.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf installiert. [!DNL Adobe Experience Manager] 6.5.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.10.0 sind:

* **Verbesserte [!DNL Content Fragment] Modelle und Editor**: Sie können jetzt komplexe und benutzerdefinierte Modelle für strukturierte Inhalte mit verschachtelten Inhalten erstellen [!DNL Content Fragment] Modelle. Inhaltsstrukturen werden in grundlegende Elemente modularisiert, die als Unterfragmente modelliert werden. Fragmente mit einer höheren Ebene verweisen auf diese Unterfragmente. Mehr Datentypverbesserungen wie erweiterte Validierungsregeln erhöhen die Flexibilität der Inhaltsmodellierung mit [!DNL Content Fragments]. Die [!DNL Experience Manager] [!DNL Content Fragment] Der Editor unterstützt verschachtelte Fragmentstrukturen in einer allgemeinen Editor-Sitzung, mit Verbesserungen wie Strukturbaumansicht und Registerkarten-Breadcrumb-Navigation durch Fragmenthierarchien.

* **GraphQL-API für[!DNL Content Fragments]**: Die neue GraphQL-API ist die Standardmethode zur Bereitstellung strukturierter Inhalte im JSON-Format. Mit GraphQL-Abfragen können Kunden nur die relevanten Inhaltselemente anfordern, um ein Erlebnis zu rendern. Durch eine solche Auswahl wird die Überbereitstellung von Inhalten (Möglichkeit mit HTTP-REST-APIs) eliminiert, die das Parsen von Inhalten auf Client-Seite erfordert. GraphQL-Schemata werden von [!DNL Content Fragment] -Modelle und API-Antworten werden im JSON-Format erstellt. In [!DNL Experience Manager] as a [!DNL Cloud Service], [GraphQL-Abfragen bleiben bestehen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) und verarbeiten Sie Cache-freundliche GET-Anfragen. Es ist noch nicht möglich in [!DNL Experience Manager] 6.5.10.0.

* **Hierarchieverwaltung und künftige Vorschau**: Benutzer haben jetzt eine Benutzeroberfläche, über die sie auf die Inhaltsstrukturen ihrer [!DNL Experience Manager] Launches, einschließlich der Möglichkeit, Seiten in einem Launch hinzuzufügen und zu entfernen. Diese Funktion erhöht die Flexibilität von [!DNL Experience Manager] Starts zum Erstellen von Inhaltsversionen, die für die zukünftige Veröffentlichung vorgesehen sind. [Zeitwarp-Funktion](/help/sites-authoring/working-with-page-versions.md#timewarp) ermöglicht Benutzern die Vorschau von Launches als zukünftiger Inhaltsstatus.

* **Connected Assets**: [!DNL Experience Manager] erweitert die [!DNL Connected Assets] zur Verwendung von [!DNL Dynamic Media] Bilder in den entsprechenden Kernkomponenten. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* **Optionen zur Linkfreigabe zum Herunterladen von Assets oder Ausgabeformaten**: Beim Freigeben von Assets und Sammlungen als Link können Benutzer auswählen, ob sie den Download von Original-Assets oder deren Ausgabedarstellungen oder beide über den freigegebenen Link zulassen möchten. Außerdem erhalten Benutzer, die die über einen Link freigegebenen Assets herunterladen, die Option, nur die Original-Assets, nur die Ausgabeformate oder beides herunterzuladen.

* **Generierte Unter-Assets begrenzen**: Administratoren können die Anzahl der Teil-Assets begrenzen, die [!DNL Experience Manager] generiert für ebenenübergreifende Assets wie PDF-, PowerPoint-, InDesign- und Keynote-Dateien. Siehe [Verwalten von ebenenübergreifenden Assets](/help/assets/managing-linked-subassets.md#generate-subassets).

* **Camera Raw Unterstützung**: Eine neue [!DNL Camera Raw] -Paket verfügbar, das [!DNL Adobe Camera Raw] v10.4. Siehe [Bilder mithilfe von [!DNL Camera Raw]](/help/assets/camera-raw.md).

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.8 aktualisiert.

* **Verbesserte Barrierefreiheit**:

   * [!DNL Dynamic Media] bietet viele Verbesserungen der Barrierefreiheit für Viewer. Siehe [[!DNL Dynamic Media] Updates](#dynamic-media-65100).

   * Platform bietet einige Verbesserungen hinsichtlich der Barrierefreiheit. Siehe [Plattformaktualisierungen](#platform-65100).

* **Verbesserungen der Benutzerfreundlichkeit**:

   * [!DNL Experience Manager] zeigt direkt eine Liste aller Inhaltsmodelle unter einem Ordner an, ohne dass Inhaltsautoren durch die Dateistruktur navigieren müssen. Die Funktion erfordert jetzt weniger Klicks und verbessert die Authoring-Effizienz.

   * Pathfield in [!DNL Sites] Mit dem Editor können Autoren Assets aus [!DNL Content Finder].

* Hinzugefügte Unterstützung für `GuideBridge#getGuidePath` API in [!DNL AEM Forms].

* Sie können jetzt den Automated forms conversion-Dienst für [Konvertieren von PDF forms in die Sprachen Französisch, Deutsch, Spanisch, Italienisch und Portugiesisch](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html#language-specific-meta-model) in adaptive Formulare.

* **Fehlermeldungen im Eigenschaften-Browser**: Es wurden Fehlermeldungen für jede Eigenschaft im Eigenschaften-Browser für adaptive Formulare hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

* **Unterstützung für die Verwendung der Literaloption zum Festlegen eines Werts für eine JSON-Typvariable**: Sie können die Literaloption verwenden, um Werte für eine JSON-Typvariable im Schritt &quot;set variable&quot;eines AEM-Workflows festzulegen. Mit der Option „Literal“ können Sie eine JSON in Form einer Zeichenfolge angeben.

* [Plattformaktualisierungen](../forms/using/aem-forms-jee-supported-platforms.md): [!DNL Adobe Experience Manager Forms] on JEE unterstützt nun die folgenden Plattformen:
   * [!DNL Adobe Acrobat 2020]
   * [!DNL Ubuntu 20.04]
   * [!DNL Open Office 4.1.10]
   * [!DNL Microsoft Office 2019]
   * [!DNL Microsoft Windows Server 2019]
   * [!DNL RHEL8]

Für eine Liste aller in [!DNL Experience Manager] 6.5.10.0, siehe [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 10](new-features-latest-service-pack.md).

Im Folgenden finden Sie die Liste der Fehlerbehebungen in [!DNL Experience Manager] Version 6.5.10.0.

### [!DNL Sites] {#sites-65100}

* Der Fokus wechselt beim Eingeben der **[!UICONTROL Standardwert]** Feld unter **[!UICONTROL Eigenschaften]** Registerkarte des Inhaltsfragment-Editors (NPR-36992).

* Beim Filtern [!DNL Content Fragment] Modelle unter einem angegebenen Pfad, [!DNL Experience Manager] search gibt alle Knoten mit zurück. `cq:Template` anstatt nur Pfade und Knoten für die [!DNL Content Fragment] -Modell (SITES-1453).
* [!DNL Content Fragments] return `null` als Status von Ordnern (SITES-1157).
* [!DNL Experience Manager] verhindert nicht, dass Benutzer [!DNL Content Fragment] Modelle (SITES-1088).
* Wenn ein Benutzer wechselt, wird er umbenannt oder gelöscht [!DNL Content Fragments] oder Medien-Assets, die referenziert werden [!DNL Content Fragments] werden nicht automatisch aktualisiert (SITES-196).
* Das Einfügen von Komponenten von einer Seite auf eine andere führt zu JavaScript-Fehlern (NPR-37030).
* Wenn Seiteneigenschaften schnell angezeigt werden, werden Seiteneigenschaften für eine andere Seite geöffnet (NPR-37025).
* Mit dem Inhaltsfragment kann das Inhaltsfragment auf sich selbst verweisen. Der Picker unterstützt den Vorgang nicht (NPR-36993).
* Nach dem Upgrade auf Service Pack 9 können einige Benutzer keine Ordner in Experience Manager verschieben und Fehler in den Protokollen sehen (SITES-1481).
* Beim Anpassen der Breite der Komponente im Layout-Container im Bearbeitungsmodus wird ein Flackern beobachtet (NPR-36961).
* Beim Bewerben eines Launches werden die Änderungen im beworbenen Launch für die anderen Launches doppelt bereitgestellt. Wenn ein Benutzer den doppelten Rollout-Launch fördert, wird der doppelte Inhalt auf der Quellseite angezeigt (NPR-36893).
* [!DNL Experience Manager] fügt einigen PNG-Bildern einen grauen Rahmen mit Transparenz hinzu, wenn Sie die Bilder mithilfe der Bild-Kernkomponente zu einer Seite hinzufügen oder wenn Sie die Größe mithilfe der Foundation-Bildkomponente ändern (NPR-36879).
* [!DNL Experience Manager Sites] Die Administrator-Benutzeroberfläche mit einer hohen Anzahl von Vorlagen führt zu langsamer Navigation (NPR-36870).
* Webseiten werden nicht gerendert, wenn ihre Links von benutzerdefinierten Servlet-Filterbundles geändert werden (NPR-36857).
* Die `ContextHubImpl` -Methode erstellt eine `ResourceResolver` nicht geschlossen ist. Dies führt zu Warnmeldungen über langwierige Vorgänge `ResourceResolver` und der Dienst gibt manchmal unerwartete Ergebnisse zurück (NPR-36853).
* Beim Synchronisieren einer einzelnen Live Copy aus den Eigenschaften der Blueprint-Seite werden auch alle anderen Live Copies synchronisiert (NPR-36829, NPR-36522).
* Wenn nur der XLS-MIME-Typ verwendet wird, funktioniert die Datei-Upload-Funktion nicht wie erwartet (NPR-36785).
* Neue Tags mit Groß-/Kleinschreibung und alle Wörter in Großbuchstaben werden nicht im Tag-Feld in [!DNL Content Fragments] (NPR-36742).
* Die Option Einzelnes Textelement beim Hinzufügen eines [!DNL Content Fragment] verursacht das Fehlen von Text und erstellt ungerade Formatierungen im Zusammenhang mit Listen und verschachtelten Listen (NPR-36565).
* Wenn ein Autor eine Komponente auf einer Seite kommentiert, die Komponente löscht und den Löschvorgang rückgängig macht, tritt beim Versuch, die Timeline-Daten für die Seite in der Sites-Konsole anzuzeigen, ein Fehler auf (NPR-36528).
* Seiteneigenschaften im Bulk Editor [!UICONTROL Speichern und schließen] speichert Änderungen, schließt den Editor jedoch nicht (NPR-36527).
* Wenn ein Benutzer versucht, eine neue Textkomponente per Drag-and-Drop auf eine Seite zu ziehen, wird die Komponente sofort ausgeblendet (NPR-36442).
* Wenn ein Benutzer in ein On-Demand-Tag eingibt, das Leerzeichen enthält (das Tag, das nicht im System vorhanden ist), und die Eingabetaste drückt, wird das Tag unter dem Feld angezeigt. Wenn die Variable [!DNL Content Fragment] gespeichert und erneut geöffnet wird, wird das On-Demand-Tag nicht angezeigt (NPR-36441).
* Die Vorlage kann nicht gelöscht werden, wenn auf die Instanz über den Dispatcher zugegriffen wird (NPR-36385).
* Wenn eine Seite verschoben wird, ist eine manuelle Aktualisierung des Browsers erforderlich, um die Änderungen zu rendern (NPR-36381).
* Wenn Sie eine Komponente auswählen, können Sie sie mit Strg+X oder Strg+C (und Befehl+X oder Befehl+C in Mac) ausschneiden oder kopieren. Wenn Sie auf eine andere Komponente klicken, können Sie sie mit der Symbolleiste einfügen, nicht jedoch mit der Tastatur (Strg+V oder Befehl+V) (NPR-36379).
* Wenn ein Benutzer versucht, Komponenten mithilfe des Schere-Symbols zu schneiden, um sie an eine andere Stelle zu verschieben, tritt ein Konsolenfehler auf. Außerdem wird beim Einfügen nur eine Komponente verschoben (NPR-36378).
* [!DNL Experience Manager] über eine Abfrage ohne Index auf WCM oder Benachrichtigungen verfügt, verlangsamt sie die Leistung (NPR-36303).
* Wenn ein Autor die Vererbung für die gelöschte geerbte Komponente wiederherstellt, besteht die verfügbare Option darin, den gesamten Seiteninhalt zu synchronisieren. Die Inhaltsautoren müssen die gesamte Seite synchronisieren, selbst wenn die Vererbung nur für eine Komponente wiederhergestellt wird. Eine vollständige Synchronisierung kann dazu führen, dass unerwünschte Inhalte synchronisiert werden (NPR-34456, CQ-4310183).
* Die Live-Nutzung einer Komponente in der -Autoreninstanz zeigt nicht alle Vorkommen an. Einige Komponenten werden auf mehr als 1000 Seiten verwendet, der Bericht zeigt jedoch nur etwa 40 Seiten an (CQ-4323724).
* Wenn es eine Site-Struktur mit vielen Unterseiten gibt, dauert das Laden der Unterseiten in der Spaltenansicht in Experience Manager 6.5.8 im Vergleich zu Experience Manager 6.4.8.2 (CQ-4322766) länger.
* Das Deaktivieren von &quot;Alle&quot;funktioniert nicht bei der Option &quot;Rollout-Seite&quot;(NPR-37070).
* Beim Öffnen einer vorhandenen v3-Komponentenversion einer Seite wird das Dialogfeld &quot;Seiteneigenschaften&quot;nicht geöffnet und eine `NullPointerException` wird protokolliert (SITES-1830).

### [!DNL Assets] {#assets-65100}

Die folgenden Probleme wurden in [!DNL Assets]:

* Der -Wert der Eigenschaft `jcr:title` wird nach dem Verschieben eines Ordners nicht auf der Veröffentlichungsinstanz aktualisiert. Beim Umbenennen und erneuten Veröffentlichen eines Ordners innerhalb eines Autors wird die `jcr:title` -Eigenschaftswert des gleichen Werts in der Veröffentlichungsinstanz (NPR-36369).

* Wenn zwei oder mehr Assets ausgewählt und ein oder mehrere Metadatenfelder bearbeitet werden, schlägt der Speichervorgang mit dem Fehlercode 500 im Safari-Browser fehl (NPR-36413).

* Der Massenimport von Metadaten schlägt aufgrund eines falschen Datumsformats fehl (NPR-36428).

* Wenn eine Auswahl im [!UICONTROL Eigenschaften] -Seite, um Metadaten zu aktualisieren, reagiert die Benutzeroberfläche nur langsam, wenn das Schema viele Optionen bereitstellt (NPR-36430).

* Suchfilter mit [!UICONTROL Gültigkeitsstatus] -Prädikat funktioniert nicht (NPR-36436).

* Das Popup-Menü für verschiedene Felder in [!UICONTROL Ordnermetadaten] -Eigenschaften zeigen nicht die zuletzt ausgewählten Werte an (NPR-36937, CQ-4314429).

* Wenn der Benutzer bei der Suche nach Dateien und Ordnern einen Filter anwendet und [!UICONTROL Dateien und Ordner], werden nur die Dateien angezeigt, aber nicht der Ordner (CQ-4319543, NPR-36627).

* Die Symbolleistenoptionen unterscheiden sich, wenn dieselbe Sammlung aus einem Ordner ausgewählt und aus einem Suchergebnis ausgewählt wird (NPR-36620).

* Die [!UICONTROL Quick Publish] ist auf der Suchergebnisseite nicht verfügbar (NPR-36904, CQ-4317748).

* Wenn Benutzer eine Live Copy eines Assets erstellen, ohne dessen Erweiterung anzugeben, ist die Live Copy-Datei nach dem Herunterladen nicht verwendbar (NPR-36903, CQ-4326305).

* Wenn ein Benutzer als Eigentümer eines untergeordneten Ordners hinzugefügt wird, erhält der Benutzer auch die Eigentümerberechtigung für den übergeordneten Ordner und somit für die anderen untergeordneten Ordner des übergeordneten Ordners. Außerdem wird der Benutzer beim Versuch, ihn zu entfernen, nicht als Eigentümer des übergeordneten Ordners entfernt. (NPR-36801, CQ-4323737).

* [!DNL Experience Manager] generiert eine Speicherausnahme, wenn Sie versuchen, Teil-Assets für ebenenübergreifende Assets wie eine PowerPoint-Präsentation zu erstellen (NPR-36668).

* Wenn Benutzer ein Asset verschieben, das bereits auf einer veröffentlichten Siteseite verwendet wird, wird die Siteseite erneut veröffentlicht, auch wenn die Option zum Veröffentlichen nicht ausgewählt ist (NPR-36636, CQ-4323500).

* Bei Verwendung der Funktion zur Erkennung des Apache Tika MIME-Typs werden die Assets hochgeladen, die mit dem `AssetManager.createAsset` -Methode eine temporäre Datei mit dem Namen `apache-tika-*.tmp` -Datei im temporären Verzeichnis. Diese temporäre Datei verwendet den gesamten verfügbaren freien Speicherplatz (NPR-36545).

* Alle DRM-geschützten Assets werden heruntergeladen und die Benutzerauswahl zum Herunterladen bestimmter Assets wird nicht befolgt. (CQ-4327422)

* Assets können nicht in `pathfield` auf der Benutzeroberfläche (NPR-36849).

* Wenn Sie ein Asset in der Spaltenansicht auswählen, wird das Bedienfeld &quot;Asset-Details&quot;ausgeblendet (NPR-36667).

### [!DNL Dynamic Media] {#dynamic-media-65100}

**Verbesserte Barrierefreiheit**

Die folgenden Verbesserungen der Barrierefreiheit sind verfügbar in [!DNL Dynamic Media Viewers].

* Bildschirmlesehilfen kommentieren jetzt den Platzhaltertext, um E-Mail-Adresse als erforderliches Feld in einem Dialogfeld zum Freigeben von Assets als Link zu suchen und hinzuzufügen. Außerdem wird die [!UICONTROL Bitte füllen Sie dieses Feld aus] tooltip (CQ-4327761).

* Bildschirmlesehilfen kommentieren nun die Namen und Ziele verschiedener Felder im [!UICONTROL Bildvorgabeneditor] über den Zugriff auf die Felder der Benutzeroberfläche über die Tastatur (CQ-4325677).

* Der Tastaturfokus wechselt nun entsprechend zur Suchregisterkarte von [!UICONTROL Viewer-Vorgaben] Dialogfeld aus der Asset-Auswahl von [!UICONTROL Rich-Media-Typ] (CQ-4324736).

* Beim Navigieren im Formularmodus mithilfe der Tastaturbefehle kommentieren die Bildschirmlesehilfen die Beschriftungen, die den Optionen zum Erhöhen und Verringern unter [!UICONTROL Erstellen] Tab von [!UICONTROL Bildvorgaben] (CQ-4323900).

* Sprachausgaben kündigen jetzt die [!UICONTROL E-Mail-Adresse suchen und hinzufügen] Option zum Freigeben von Assets als Link-Dialogfeld (CQ-4323352).

* Der Tastaturfokus wird in der Symbolleiste beim Navigieren in Assets mit Tastaturtasten beibehalten (CQ-4322037).

* Bildschirmlesehilfen kommentieren jetzt die neu hinzugefügten [!UICONTROL Bearbeiten] Feldinformationen nach Auswahl von [!UICONTROL Zuschneiden hinzufügen] -Option innerhalb der [!UICONTROL Responsive Bildbeschneidung] on [!UICONTROL Bildverarbeitungsprofil bearbeiten] Seite (CQ-4290734).

* on [!UICONTROL Bildvorgabe bearbeiten] und [!UICONTROL Interaktives Video erstellen] Seiten, zeigen Bildschirmlesehilfen jetzt die Seitenüberschrift entsprechend an, wenn Sie auf den Seiten mithilfe der Tastaturbefehle für Überschriften navigieren (CQ-4290730) (CQ-4290701).

* Bildschirmlesehilfen können jetzt die verschiedenen Bereiche des Bildschirms (z. B. den rechten Bereich, den linken Bereich, die Aktionssymbolleiste, das Wahrzeichen der Viewer-Symbolleiste und das Zoombare Bild-Wahrzeichen) mithilfe von Tastaturbefehlen für Wahrzeichen und Regionen erkennen, wenn sie auf den folgenden Seiten navigieren.

   * [!UICONTROL Viewer-Vorgabeneditor] (CQ-4290729)

   * [!UICONTROL Bildset-Editor] (CQ-4290710)

   * [!UICONTROL Interaktives Video erstellen] (CQ-4290702).

* Bildschirmlesehilfen geben jetzt den Namen für die Freigabeoption im Videoframe an, wenn sie mit der Pfeiltaste nach unten navigieren (CQ-4290728).

* Bildschirmlesehilfen kommentieren jetzt die Namen für verschiedene Optionen in [!UICONTROL Sprite] und [!UICONTROL Hintergrund] Registerkarten [!UICONTROL Erscheinungsbild] Registerkarte in [!UICONTROL Viewer-Vorgabeneditor] (CQ-4290727).

* Obligatorische Felder, z. B. das zu bearbeitende Feld [!UICONTROL Breite]in der [!UICONTROL Allgemein] Tab von [!UICONTROL Videokodierung bearbeiten] -Seite nun ein Sternchen-Symbol (*) enthält (CQ-4290725).

* Bildschirmlesehilfen geben jetzt den Titel für die Optionen an [!UICONTROL Bildprofile] Seite (CQ-4290723).

* Windows-Benutzer können jetzt aus dem erweiterten CSS-Editor unter [!UICONTROL Viewer-Vorgabeneditor] wenn der Schwerpunkt auf dem CSS-Editor liegt (CQ-4290720).

* on [!UICONTROL Allgemein] Tab von [!UICONTROL Bildvorgabe bearbeiten] Beim Navigieren im Formularmodus kommentieren die Bildschirmlesehilfen jetzt die Beschriftungen für verschiedene Bearbeitungsfelder und Optionen. (CQ-4290717)

* Bildschirmlesehilfen beschreiben jetzt die Rolle und den Status (ausgewählt oder nicht ausgewählt) für Benutzeroberflächenoptionen auf der linken Navigationsleiste auf der Detailseite der Assets (CQ-4290709).

* Bildschirmlesehilfen kommentieren jetzt den Status (ausgewählt oder nicht ausgewählt) und die Verknüpfung für das Bild in der [!UICONTROL Inhalt] Tab von [!UICONTROL Interaktives Video erstellen] Seite (CQ-4290707).

* Bildschirmlesehilfen kommentieren jetzt bei der Navigation mit der Pfeiltaste nach unten den Namen, die Rolle und den Status verschiedener Segmente in der Skala der Video-Timeline richtig. [!UICONTROL Interaktives Video erstellen] Seite (CQ-4290706).

* Bildschirmlesehilfen kommentieren jetzt den Namen, die Rolle, den Standardstatus (ausgewählt oder nicht ausgewählt) und die Eigenschaft beim Navigieren in den Optionen unter [!UICONTROL Interaktives Video erstellen] Seite (CQ-4290704).

* Bildschirmlesehilfen kommentieren jetzt den Namen, die Rolle und den Standardstatus (ausgewählt oder nicht ausgewählt) der Optionen in [!UICONTROL Alle Assets] und [!UICONTROL Alle Sammlungen] Optionen beim Navigieren in der [!UICONTROL Veröffentlichen] Seite (CQ-4290705).

* Wenn Sie ein nicht unterstütztes Videoformat (außer MP4) in [!UICONTROL Interaktives Video erstellen] -Seite, zeigt Experience Manager Fehlermeldungen an und kündigt diese an (CQ-4290700).

* Der Kontrast der Zahlen (Zeit in Sekunden) in der Zeitleistenskalierung auf [!UICONTROL Interaktives Video erstellen] -Seite erfüllen nun das erforderliche minimale Leuchtdichteverhältnis, sodass Benutzer mit eingeschränkter Farbwahrnehmung problemlos lesen können (CQ-4290699).

* Bildschirmlesehilfen geben jetzt den Titel für die [!UICONTROL Produktname] beim Navigieren in der [!UICONTROL Interaktives Video erstellen] Seite (CQ-4290697).

**Behobene Probleme**

Die folgenden Fehlerbehebungen sind in verfügbar: [!DNL Dynamic Media].

* Hochgeladene Videos in [!DNL Experience Manager] display `Process failed` after `dynamicmedia_scene7` runmode ist aktiviert und die Synchronisierung ist deaktiviert (CQ-4327791).

### Plattform {#platform-65100}

In diesem Service Pack werden die folgenden Verbesserungen bereitgestellt:

* Wenn ein Benutzer ein Element in der Baumansicht auswählt, geben die Bildschirmlesehilfen die Auswahl und die Symbolleistenoptionen an, die oben angezeigt werden (NPR-36504).
* Einige Text- und Kontrollnamen sind für Benutzer mit Sehproblemen leichter lesbar, da das Lichtstärkenverhältnis das erforderliche Mindestverhältnis von 4,5:1 erreicht (NPR-36503).
* Wenn ein Benutzer die Kalendersteuerelemente verwendet, liest die Bildschirmlesehilfe die beschreibenden Informationen zu Datum, Monat und Wochentag. Wenn ein Benutzer die Kalenderverknüpfung verwendet, liest die Bildschirmlesehilfe die Änderung in Datum, Monat und Jahr vor (NPR-36498).
* Unterstützung für die Ausführung von benutzerdefiniertem JavaScript `Clientlibs` Verwendung von ECMAScript 6-Funktionen ohne Einhaltung des strikten Modus. Insbesondere gilt Folgendes: `emitUseStrict` -Markierung wird zum `GCCScriptProcessor` (NPR-36411).

Die folgenden Fehlerbehebungen sind Teil dieses Service Packs:

* Benutzerdefinierte Konsistenzprüfungen werden häufiger als geplant ausgeführt (NPR-36985).
* Die `Resourceresolver map` -Methode gibt ein falsches Ergebnis für Alias-Seiten zurück (NPR-36767).
* [!DNL Experience Manager] Das Starten wird aufgrund von Lade-Workflows verzögert. (NPR-36615)

### Integrationen {#integrations-65100}

* Experience Manager reagiert nicht mehr, wenn der primäre MongoDB-Knoten zu einem anderen Knoten wechselt (NPR-36566).
* [!DNL Sling content distribution] schlägt bei der Ausführung des Löschvorgangs des Sammlungsmitglieds fehl (NPR-36521, CQ-4323578).

### Benutzeroberfläche {#user-interface-65100}

* Die **[!UICONTROL Verweise]** Seitenbereich zeigt keine Asset- und Site-Referenzen an (GRANITE-35078, GRANITE-34892).

### Übersetzungsprojekte {#translation-65100}

* Zusätzliche Unterseiten in einer Sprachkopie eines Projekts mit mehreren Übersetzungen werden gelöscht (NPR-36622).

### Workflow {#workflow-65100}

* Wenn der Server eine Abwesenheitsnachricht erhält, meldet er Speicherwarnungen und reagiert nicht mehr. (NPR-36768)

### [!DNL Communities] {#communities-65100}

* Community-Site-Seiten werden in geöffnet `LoggedIn` state für anonyme Gastbenutzer (NPR-36908).

* Wenn mehr als eine Seite im **[!UICONTROL Community]** > **[!UICONTROL Ideen]** > **[!UICONTROL Kommentare]** Seite, funktioniert die Seitennavigation nicht (NPR-36541).

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


[!DNL AEM 6.5.10.0 Forms] umfasst die folgenden Fehlerbehebungen:

* Bei der Installation [!DNL AEM 6.5 Forms], werden die folgenden Drittanbieterbibliotheken automatisch installiert (CQDOC-18373):
   * [!DNL Microsoft Visual C++ 2008 Service Pack 1 (x86)]
   * [!DNL Microsoft Visual C++ 2010 Service Pack 1 (x86)]

**Adaptive Formulare**

* Wenn die für die Feldwerte in einem adaptiven Formular durchgeführten Überprüfungen erfolgreich sind, [!DNL AEM Forms] kann das Formulardatenmodell nicht aufrufen (CQ-4325491).

* Wenn Sie einem Übersetzungsprojekt ein Sprachwörterbuch hinzufügen und dann das Projekt öffnen, [!DNL AEM Forms] zeigt eine Fehlermeldung an (CQ-4324933):

   ```TXT
   Uncaught TypeError: Cannot read property 'PROJECT_LISTING_PATH' of undefined
   at openButtonClickHandler (clientlibs.js:245)
   at HTMLButtonElement.onclick (clientlibs.js:258)
   ```

* Leistungsprobleme nach der Installation [!DNL AEM Forms] Service Pack 7 (CQ-4326828).

* Fehlerkorrektur – Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird der Inhalt der Datei jetzt zuverlässig gesendet. Apple iOS 15.1 bietet eine Fehlerbehebung (CQ-4325361).

**Korrespondenzverwaltung**

* Verzögerung bei der Anzeige von Zeichen in der [!UICONTROL Daten] sowie in der HTML-Briefvorschau (NPR-37020).

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

* Screen Reader kann keine unverankerten Felddaten lesen, die innerhalb einer Textbeschriftung auf der Übergeordneten Seite oder auf Teilformularseiten in einer dynamischen PDF platziert werden (CQ-4321587).

**Document Services**

* Wenn Sie XDP-Dateien in PDF-Dateien konvertieren und dann die resultierende PDF assemblieren, schlägt die PDF-Generierung fehl und zeigt die folgende Fehlermeldung an:

   ```TXT
   Caused by: com.adobe.fd.assembler.client.AssemblerException$ClientException: Document is in a disposed state!
   ```

**Formular-Workflow**

* Ein Formular kann nach der Aktualisierung auf AEM Forms Service Pack 8 nicht an einen Workbench-Prozess gesendet werden (CQ-4325846).

**HTML5-Formulare**

* Wenn Sie den Wert für `mfAllowAttachments` Eigenschaft als `True` im CRX DE-Repository die `dataXml` wird beim Senden des HTML5-Formulars beschädigt (NPR-37035).

* Wenn Sie eine XDP als HTML rendern, verwenden Sie `dataXml`, [!DNL AEM Forms] zeigt eine `Page Unresponsive` Fehler (NPR-36631).

### Commerce {#commerce-65100}

* Der Wert im **[!UICONTROL Veröffentlicht von]** in der Spaltenansicht falsch angezeigt werden (NPR-36902).
* Wenn ein Katalog eingeführt wird, werden neue Produkte fälschlicherweise als geänderte Produkte gekennzeichnet (NPR-36666).
* Wenn Sie ein gelöschtes Produkt neu erstellen, wird die Produktseite nicht neu erstellt (NPR-36665).
* Geänderte Seiten werden aktualisiert, aber die entsprechenden verknüpften Produkte werden beim Rollout des Katalogs nicht aktualisiert (CQ-4321409, NPR-36422).
* Die **[!UICONTROL Später veröffentlichen]** und **[!UICONTROL Spätere Veröffentlichung rückgängig machen]** Workflows funktionieren nicht (CQ-4327679).

Informationen zu Sicherheitsupdates finden Sie unter [[!DNL Experience Manager] Seite mit Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.10.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.10.0 ist Experience Manager 6.5 erforderlich. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen.
* Der Service Pack-Download ist auf Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.10.0 mithilfe des Package Managers auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, die [!DNL Adobe Experience Manager] 6.5.10.0-Paket.

### Service Pack installieren {#install-service-pack}

So installieren Sie das Service Pack auf einem [!DNL Adobe Experience Manager] 6.5-Instanz ausführen:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager] -Instanz.

1. Laden Sie das Service Pack herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip).

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. Normalerweise tritt dieses Problem in [!DNL Safari] -Browser, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, automatisch zu installieren [!DNL Experience Manager] 6.5.10.0 auf einer funktionierenden Instanz:

A. Platzieren Sie das Paket in `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwendung `cmd=install&recursive=true` damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.10.0 unterstützt nicht die Installation von Bootstraps.

**Installation überprüfen**

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge an `Adobe Experience Manager (6.5.10.0)` under [!UICONTROL Installierte Produkte].

1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für die Verwendung mit dieser Version zertifiziert sind, finden Sie in der [technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Adobe Experience Manager Forms Add-On-Paket installieren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diese Option, wenn Sie Experience Manager Forms nicht verwenden. Fehlerbehebungen in Experience Manager Forms werden eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Service Pack-Version.

1. Stellen Sie sicher, dass Sie das Adobe Experience Manager Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-On-Paket wie unter [Installieren von Add-On-Paketen für AEM Forms](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>Experience Manager 6.5.10.0 enthält eine neue Version von [AEM Forms-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf Experience Manager 6.5.10.0 aktualisieren, installieren Sie die neueste Version des Pakets nach der Installation des Forms-Add-On-Pakets.

### Installieren von Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für Experience Manager Forms on JEE und zur Konfiguration nach der Bereitstellung finden Sie in der [Versionshinweise](jee-patch-installer-65.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für Experience Manager Forms on JEE installiert haben, installieren Sie das neueste Add-On-Paket für Forms und löschen Sie das Add-On-Paket für Forms aus dem `crx-repository\install` und starten Sie den Server neu.


### UberJar {#uber-jar}

UberJar für Experience Manager 6.5.10.0 ist im [Maven Central Repository](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.10/).

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

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
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstatt im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar`. Es gibt also keine `classifier`, mit `apis` als Wert für die `dependency` -Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die als veraltet gekennzeichnet sind mit [!DNL Experience Manager] 6.5.7.0. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Die **[!UICONTROL AEM Cloud Services-Opt-in]** Der Bildschirm wird nicht mehr unterstützt, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration wurde in Experience Manager 6.5 aktualisiert. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O] und unterstützt die wachsende Rolle von Adobe Launch als Instrument [!DNL Experience Manager] Seiten für Analysen und Personalisierung verwenden, ist der Opt-in-Assistent funktionell irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O] Integrationen über die entsprechenden [!DNL Experience Manager] Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* As [!DNL Microsoft Windows Server 2019] unterstützt nicht [!DNL MySQL 5.7] und [!DNL JBoss EAP 7.1], [!DNL Microsoft Windows Server 2019] unterstützt keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie ein Upgrade [!DNL Experience Manager] -Instanz von 6.5 bis 6.5.10.0, können Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5, die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] und veröffentlichen Sie einen verschachtelten Ordner in [!DNL Brand Portal]. Der Titel des Ordners wird jedoch nicht aktualisiert in [!DNL Brand Portal] bis die Veröffentlichung des Stammordners erfolgt ist.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die in [!DNL Experience Manager] 6.5.10.0:

* [Liste der in Experience Manager 6.5.10.0 enthaltenen OSGi-Bundles](assets/65100_bundles.txt)

* [Liste der in Experience Manager 6.5.10.0 enthaltenen Inhaltspakete](assets/65100_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Siehe [Kontaktaufnahme mit dem Adobe-Support](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 - Versionshinweise](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

