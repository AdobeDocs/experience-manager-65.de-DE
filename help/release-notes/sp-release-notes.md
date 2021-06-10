---
title: '[!DNL Experience Manager] 6.5 Service Pack - Versionshinweise'
description: Spezifische Versionshinweise für  [!DNL Adobe Experience Manager] 6.5 Service Pack 9
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 2e01bb0b16728a8073e5de47deb88de69486d408
workflow-type: tm+mt
source-wordcount: '3877'
ht-degree: 5%

---

# [!DNL Adobe Experience Manager] 6.5 Service Pack - Versionshinweise  {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.9.0 |
| Typ | Service Pack-Version |
| Datum | 27. Mai 2021 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.9.zip) |

<!-- TBD: Update the SD link when SP8 is available. Same link is duplicated below in install -->

## Was ist enthalten in [!DNL Adobe Experience Manager] 6.5.9.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.9.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.9.0 eingeführt wurden, sind:

* Mit der AEM Sites Dynamic Media Foundation-Komponente können Sie jetzt die Optimierung für Geräte mit höherer Auflösung aktivieren oder deaktivieren, wenn Sie responsive Bildvorgaben oder smartes Zuschneiden verwenden.

* Um die Leistung zu verbessern, wird die Bedingung hidden=false von der JCR-Abfrage in den QueryBuilder-Auswerter verschoben. Um sicherzustellen, dass ein ausgeblendetes Prädikat nach der Änderung funktioniert, prüft Adobe Experience Manager, ob kein ausgeblendeter Ordner auf der Benutzeroberfläche angezeigt wird.

* Möglichkeit, gelöschte Seiten und Baume auf einer [!DNL Experience Manager Sites]-Seite wiederherzustellen.

* Unterstützung für einen neuen Benutzer zur Aktualisierung des Zugriffstokens mithilfe eines Aktualisierungstokens für den Mailer-Konfigurationsdienst.

* [Unterstützung für SMTP XOAUTH2](/help/sites-administering/notification.md#setting-up-oauth) -Mechanismus für den E-Mail-Konfigurationsdienst.

* Unterstützung für [!DNL MongoDB] Versionen 4.2 und 4.4.

* Vorkommen von Namen, die Hongkong, Macau und Taiwan betreffen, werden gemäß den neuen Benennungskonventionen für chinesische Gebietsschemata und Regionen aktualisiert.

* Verbesserungen der Barrierefreiheit in [!DNL Experience Manager] [Assets](#assets-accessibility-6590) und [Dynamic Media](#accessibility-dm-6590).

* Die intelligente Bildbearbeitung (Device Pixel Ratio) und die Optimierung der Netzwerkbandbreite ermöglichen eine effiziente Bereitstellung von Bildern mit der besten Qualität. auf Geräten mit hoher Auflösung angezeigt und die Netzwerkbandbreite eingeschränkt wird. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur intelligenten Bildbearbeitung](/help/assets/imaging-faq.md).

   >[!NOTE]
   >
   >Die Veröffentlichungszeitleiste für die oben genannten Verbesserungen der intelligenten Bildbearbeitung lautet:
   >
   >* Nordamerika 24. Mai 2021 in NA,
      >
      >
   * Europa, Naher Osten und Afrika, 25. Juni 2021,
      >
      >
   * Asien-Pazifik 19. Juli 2021.


* Neue Unterstützung für AVIF-Bildformat der nächsten Generation in der Dynamic Media-Bereitstellung (Fmt-URL-Modifikator). Weitere Informationen finden Sie unter [Image Serving and Rendering api fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html).

   >[!NOTE]
   >
   >Die Veröffentlichungszeitleiste für die AVIF-Unterstützung lautet:
   >
   >* Nordamerika 10. Mai 2021,
      >
      >
   * Europa, Naher Osten und Afrika 24. Mai 2021,
      >
      >
   * Asien-Pazifik 24. Juni 2021.


* Möglichkeit, eine Benachrichtigungs-E-Mail mit dem Workflow-Schritt [!UICONTROL Aufgabe zuweisen] an eine Gruppe zu senden.

* Möglichkeit, einen Entwurf für interaktive Kommunikation abzurufen, nachdem die Quelle für interaktive Kommunikation geändert wurde.

* Legen Sie den benutzerdefinierten Domänennamen für das Laden, Rendern und Überprüfen des reCAPTCHA-Dienstes in [!DNL Experience Manager Forms] fest.

* Verbesserungen der Eingabedaten für den Workflow-Schritt [!UICONTROL Formulardatenmodelldienst aufrufen] .

* Möglichkeit zur Verwendung mehrerer Übergeordneter Seiten in einer Datensatzdokumentvorlage in [!DNL Experience Manager Forms].

* Unterstützt Seitenumbrüche im Datensatzdokument in [!DNL Experience Manager Forms].

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.7 aktualisiert.

Eine vollständige Liste der in [!DNL Experience Manager] 6.5.9.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 9](new-features-latest-service-pack.md).

>[!NOTE]
>
>Ab AEM Service Pack 9 können [!DNL Experience Manager] -Kunden ihre [!DNL Experience Manager] -Anwendungen mit Distributionen der [!DNL Azul Zulu] -Builds von OpenJDK entwickeln und betreiben, die standardkonform mit Java SE sind.
>Die Unterstützung für die [!DNL Azul Zulu]-JDKs wird auch von Adobe für [!DNL Experience Manager]-Kunden bereitgestellt.
>Sie können die entsprechenden Versionen von [!DNL Azul Zulu JDKs] von [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) herunterladen.
>Die Nutzungsrechte für die Oracle Java-Technologie, wie sie von Adobe verteilt werden, laufen Ende Dezember 2022 aus. [!DNL Experience Manager] -Kunden wird empfohlen, die Verwendung für die  [!DNL Azul Zulu] JDKs bis spätestens zu diesem Datum zu planen und zu implementieren. Weitere Informationen zur Verwendung der [!DNL Oracle Java]-Technologie und der [!DNL Azul Zulu]-Technologie finden Sie in den zugehörigen [FAQs](https://experienceleague.adobe.com/docs/experience-manager-65/assets/adobe-azul-openjdk-license-agreement.pdf?lang=en).

Im Folgenden finden Sie eine Liste der Fehlerbehebungen in [!DNL Experience Manager] Version 6.5.9.0.

### [!DNL Sites] {#sites-6590}

* Veröffentlichte Seiten mit aktivierter Authentifizierungspflicht-Eigenschaft werden nicht zur Anmeldeseite umgeleitet und geben die Fehlermeldung 404 zurück (NPR-36354).

* Beim Erstellen eines Hyperlinks funktioniert die Option zum Durchsuchen eines Links nicht in der Textkomponente (NPR-35849).

* Bei Verwendung der API `com.day.cq.wcm.commons.ReferenceSearch` wird eine traversale Abfrage ausgelöst. Dies wirkt sich auf die Leistung des [!DNL Experience Manager]-Servers aus (NPR-36407).

* Verschachtelter Layout-Container in einem anderen Layout-Container, dessen Größe geändert wird, zeigt eine falsche Anzahl von Spalten für die untergeordneten Komponenten an, sodass diese Komponenten nicht am Raster ausgerichtet werden (NPR-36359).

* Der externe Link-Checker zeigt gültige externe Links als ungültige Links an (NPR-36289).

* Nachdem Sie Verweise einige Zeit angezeigt haben, zeigt das Bedienfeld Verweise eine Fehlermeldung an (NPR-36167).

* Beim Verschieben einer Komponente hat das automatisch erstellte Parsys nicht den Knoten `sling:resourceType` (NPR-36165).

* Wenn Sie versuchen, eine Live Copy zu synchronisieren (bei Verwendung der Rollout-Konfigurationen [!UICONTROL Aktivieren bei Blueprint-Aktivierung] und [!UICONTROL Deaktivieren bei Blueprint-Aktivierung]), wenn eine Komponente im Live Copy-Übergeordnete gelöscht wird, schlägt die Synchronisierung fehl und eine `NullPointerException` wird protokolliert (NPR-36127).

* Wenn ein Benutzer Ad-hoc-Text für Tags eingibt (Tag, das nicht im System vorhanden ist) und auf &quot;enter&quot;klickt, wird das Tag unter dem Feld angezeigt, aber wenn das Inhaltsfragment gespeichert und erneut geöffnet wird, verschwindet das Ad-hoc-Tag (NPR-36132).

* Der Posteingang verfügt nicht über eine Option zur Anzeige des Status asynchroner Vorgänge (NPR-36104).

* Nach der Wiederherstellung der Vererbung wird eine doppelte Komponente erstellt (NPR-36000).

* Bei Verwendung von `RemoteContentRenderingService` enthält die Anfrage an `RemoteContentRendererRequestHandler.getRequest` immer die Stammseite für `ComponentExporter`, jedoch nicht die angeforderte Seite, wenn sie nicht in das Stammmodell auf der Grundlage der Traversal-Tiefe und der Filteroptionen einbezogen wird. Die Anfrage muss immer die angeforderte Seite enthalten, damit die SPA über genügend Informationen zum Rendern einer Antwort verfügt (NPR-35961).

* onTime/offTime -Elemente aktivieren/deaktivieren nicht bei der erwarteten onTime/offTime (NPR-35936).

* Wenn Sie eine Seite veröffentlichen, die ein Experience Fragment enthält, das keine `cq:lastModified` -Eigenschaft hat, tritt ein `NullPointerException`-Fehler auf (NPR-35914).

* Wenn Sie versuchen, die Größe einer Komponente in einem Container zu ändern, ist es nicht möglich, die Größe auf die Originalgröße zurückzusetzen. Wenn die Größe des Komponenten-Containers verringert wird, ist es nicht möglich, die Größe auf das Original zurückzusetzen (NPR-35809).

* Im Rollout-Dialogfeld, das entweder im Editor oder in der Live Copy-Übersicht ausgelöst wird, liegen die Statussymbole für getrennte, ausgesetzte oder nicht erstellte Seiten falsch (NPR-35691).

* Die Rollout-On-Page-Eigenschaften des Multi-Site-Managers von Übergeordneten ignorieren das Kontrollkästchen für Rollout-Seiten und Unterseiten (NPR-35634).

* Die in der klassischen Benutzeroberfläche verfügbare Funktion zum Wiederherstellen des Baums fehlt in der Touch-optimierten Benutzeroberfläche (CQ-4315352, CQ-4309415).

* Probleme beim Zurücksetzen der Vererbung und Rollout einer Seite [!DNL Experience Manager Sites] (NPR-36033).

### [!DNL Assets] {#assets-6590}

[!DNL Adobe Experience Manager] 6.5.9.0  [!DNL Assets] behebt die folgenden Probleme.

* Die Tags, die aus einem Tag-Auswahlelement in einem [!UICONTROL Ordner-Metadatenschema] -Formular erstellt wurden, werden nicht gespeichert (NPR-36119).

* Wenn ein kleines Ellipse verwendet wird, um Assets zu kommentieren, überschneidet sich das Auslassungszeichen mit der Anzahl der Anmerkung in der Druckversion (NPR-36114).

* In der Spaltenansicht wird [!DNL Experience Manager] in einigen Fällen nicht zum Duplizieren eines Asset-Konflikts aufgefordert, wenn ein doppeltes Asset hochgeladen wird (NPR-36048).

* Das Dialogfeld Link freigeben wird nicht geschlossen, indem auf die Schaltfläche Schließen geklickt wird, wenn es geöffnet ist und keine Änderungen vorgenommen werden (NPR-36030).

* Wenn mehrere Assets ausgewählt sind, um die Eigenschaften zu aktualisieren, tritt manchmal entweder ein Fehler auf oder die Eigenschaften eines nicht ausgewählten Assets werden aktualisiert (NPR-36002).

* Wenn beim Hochladen von Assets Whitespaces am Anfang oder Ende der Asset-Dateinamen hinzugefügt werden, wobei die restlichen Zeichen dem Namen eines vorhandenen Assets im Repository entsprechen, wird das vorhandene Asset ohne Protokollierung eines Fehlers ersetzt (NPR-36001).

* Wenn das Video auf der Seite mit den Asset-Details wiedergegeben wird, funktionieren die Wiedergabe- und Pausenoptionen nicht. (NPR-35999)

* Beim Rückgängigmachen der Veröffentlichung von Assets in Batches erzeugt Brand Portal einen Fehler, der darauf hinweist, dass der Anfrage-URI zu lang ist (NPR-35954).

* Wenn ein Asset mit langen Anmerkungstext gedruckt wird, wird der Anmerkungstext abgeschnitten, selbst wenn Speicherplatz verfügbar ist (NPR-35948).

* Die Option zum Wechseln zur nächsten Seite ist bei Auswahl der Seite in der Ansicht &quot;Vorlagen&quot;auf der Seite &quot;Katalog erstellen&quot;deaktiviert (CQ-4315462).

* Wenn der Workflow zum Aktualisieren von Assets für das Video-Asset gestartet wird, wird die Seite wiederholt aktualisiert (CQ-4313375).

* DAM-Ordner können nicht gelöscht oder verschoben werden und eine Ausnahme wird protokolliert (NPR-35942).

#### Verbesserungen in Assets {#assets-enhancements}

* Die Option [!UICONTROL Keine] wurde in der Karten-, Spalten- und Insight-Ansicht eingeführt, um Assets in der Reihenfolge zu sortieren, in der sie im JCR-Knoten gespeichert sind (NPR-36356).

* Eine Option wird hinzugefügt, um die E-Mail-ID in der API-Antwort von Adobe Experience Manager in Kleinbuchstaben hinzuzufügen (CQ-4317704).

#### Verbesserungen der Barrierefreiheit in Assets {#assets-accessibility-6590}

[!DNL Adobe Experience Manager] 6.5.9.0  [!DNL Assets] bietet die folgenden Verbesserungen der Barrierefreiheit.

Der Kontrast (mit Hintergrund) des folgenden Texts und der folgenden Symbole wird verbessert, sodass Benutzer mit eingeschränkter Sehkraft und Farbwahrnehmung Folgendes verstehen können:

* Asset-Titel auf der Seite [!UICONTROL Eigenschaften] (NPR-35967).
* Sternbewertungssymbole in den Abschnitten [!UICONTROL Bewertung] an verschiedenen Stellen (NPR-36009).
* Text in der Asset- und Ordnerkartenansicht (NPR-35966).
* Platzhaltertext in der Ansicht [!UICONTROL Timeline] (NPR-35965).
* Asset-Namen in den Asset-Suchergebnissen (NPR-35964).
* Platzhaltertext im Dialogfeld [!UICONTROL Linkfreigabe] (NPR-35963).
* [!UICONTROL Metadaten],  [!UICONTROL Status] und   anderer Text in der   Liste im Dialogfeld  [!UICONTROL Anzeigeeinstellungen ] (NPR-35910).
*  Standort und  [!UICONTROL Typ für ] Platzhaltertexte in der globalen Suche (NPR-35909).
* Ein- und Ausblenden von Symbolen unter [!UICONTROL Inhaltsstruktur] (NPR-35908).
* den Text [!UICONTROL Assets] auf der Seite, auf der Asset-Ordner angezeigt werden (NPR-35905).
* Text in [!UICONTROL Asset-Metadaten], [!UICONTROL Nutzungsstatistiken] innerhalb der Option [!UICONTROL Überblick] auf der Asset-Detailseite (NPR-35904).
* Text für Tastaturbefehle für die Optionen [!UICONTROL properties] und [!UICONTROL edit] auf der Asset-Detailseite (NPR-35904).

### [!DNL Dynamic Media] {#dynamic-media-6590}

Adobe Experience Manager 6.5.9.0 Assets behebt die folgenden Probleme in [!DNL Dynamic Media]:

* Benutzerdefinierte Viewer-Vorgaben und CSS werden nicht nach [!DNL Dynamic Media] repliziert, wenn [!DNL Dynamic Media] selektiv aktiviert und durch [default](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/config-dm.html?lang=en#troubleshoot-dm-config) deaktiviert wird (NPR-36232).

* Beim Versuch, Videoausgabeformate auf der Seite mit Asset-Details anzuzeigen, werden die Videos langsam geladen (CQ-4320122).

* Die Browserseite reagiert nicht und verlangsamt sich beim Hochladen von mehr als 200 Assets mit aktivierter Funktion &quot;Duplikat-Asset-Erkennung&quot;. (CQ-4319633)

* Wenn ein Panoramabild-Asset auf einer Seite zur Panoramedienkomponente hinzugefügt wird, wird ein Fehler &quot;Uncaught Reference&quot;protokolliert (CQ-4317666).

* Wenn der interaktive Medien-Viewer mit Experience Fragment implementiert ist, wird das Experience Fragment nicht vom Publisher aus geöffnet und ein Fehler wird protokolliert. (CQ-4317655)

* Die Option In Dynamic Media veröffentlichen ist in der Schnellveröffentlichung in der Metadaten-Editor-Ansicht nicht verfügbar (CQ-4317199).

* Site-Autoren mit schreibgeschützten Berechtigungen können die Funktion für das smarte Zuschneiden auf Assets verwenden und die Ausgabedarstellungen für das smarte Zuschneiden bearbeiten. Benutzer mit schreibgeschützten Berechtigungen dürfen jedoch keine Asset-Eigenschaften in der Sites-Entwicklungsinstanz bearbeiten können (CQ-4316450).

* Videoanmerkungen funktionieren nicht für Ordnerpfade, bei denen die Dynamic Media-Konfiguration nicht aktiviert ist, auch wenn die AEM-Instanz im Dynamic Media-Modus eingerichtet ist (CQ-4314950).

* Wenn der Asset-Titel Doppelbyte-, Multibyte-, High ASCII-, Kyrillisch-, Surrogate-Paar-, Hebräisch-, Arabisch- und GB18030-Zeichen aufweist, haben beim Veröffentlichen in Dynamic Media die Asset-Titel ein Fragezeichen (?) (CQ-4311872).

#### Verbesserungen der Barrierefreiheit in Dynamic Media {#accessibility-dm-6590}

[!DNL Adobe Experience Manager] 6.5.9.0  [!DNL Assets] bietet die folgenden Verbesserungen der Barrierefreiheit in  [!DNL Dynamic Media].

* Wenn Sie das Dialogfeld zum Hinzufügen von Assets mithilfe von Tastaturbefehlen im Bildset-Editor öffnen:
   * Bildschirmlesehilfen beschreiben, dass das Dialogfeld geöffnet wird.
   * Der Tastaturfokus wechselt beim Öffnen zum Dialogfeld.
   * Der Tastaturfokus wechselt zurück zur Option Asset hinzufügen , wenn das Dialogfeld geschlossen wird (CQ-4312134).

* Sie können jetzt Hotspots zu Assets über Tastaturbefehle im Hotspot-Editor hinzufügen und bearbeiten (CQ-4305965).

* Sie können jetzt Hyperlinks über Hotspot-Verwaltung über Tastaturbefehle auf Hotspots setzen. Der Fokus der Bildschirmlesehilfe wechselt jetzt zum Feld zum Bearbeiten des URL-Pfads und zur Option zum Dialogfeld Auswahl öffnen (CQ-4290735).

* Der Kontrast (mit Hintergrund) von Text und Steuerelementen auf der Seite des Bildset-Editors wurde verbessert, sodass Benutzer mit eingeschränktem Sehvermögen und eingeschränkter Farbwahrnehmung verstehen können (CQ-4290733).

* Sie können jetzt im Viewer-Vorgabe-Editor zu Optionen zur Asset-Freigabe navigieren und die erweiterte Freigabeoption mithilfe von Tastaturtasten reduzieren (CQ-4290724).

* Sie können jetzt auf den Registerkarten Allgemein und Erweitert der Seite Videokodierung mit Tastaturbefehlen bearbeiten QuickInfos zu den Informations- und Warnsymbolen navigieren und anzeigen (CQ-4290722).

* Bildschirmlesehilfen beschreiben jetzt die Anweisungen für verschiedene Felder auf den Registerkarten Erscheinungsbild und Verhalten im Viewer-Vorgabe-Editor (CQ-4290721).

* Beim Navigieren auf der Seite Bildvorgabe bearbeiten im Formularmodus erläutert die Bildschirmlesehilfe den Zweck und die Namen verschiedener Felder und Steuerelemente. (CQ-4290717)

* Beim Navigieren zur Asset-Detailseite beschreiben Bildschirmlesehilfen jetzt den Zweck verschiedener Optionen in Viewern (CQ-4290716).

* Kontrast (mit Hintergrund) des Platzhaltertextes Alle Ausgabedarstellungen in Ausgabedarstellungen der Asset-Detailseite wurde verbessert, sodass Benutzer mit eingeschränkter Sehkraft und Wahrnehmung von Farben verstehen können (CQ-4290713).

* Visuelles Sternchen, um ein Pflichtfeld zu kennzeichnen, wird jetzt im Feld Titel des Assets im Bildset-Editor bereitgestellt und Sprachausgaben geben die erforderlichen Informationen für das Feld an (CQ-4290712).

* Bildschirmlesehilfen können jetzt auf die Asset-Detailseite zugreifen und den Zweck verschiedener interaktiver Optionen in Viewern beschreiben (CQ-4290708).

### Plattform {#platform-6590}

* Wenn Sie eine Miniaturansicht für einen Blueprint generieren und die Änderungen an der Live Copy vornehmen, funktioniert die Vererbung für einige Felder nicht (CQ-4319517).

* Wenn Sie einen Ordner erstellen, wählen Sie die Eigenschaft &quot;Orderable&quot;aus und fügen Sie dem Ordner mehr als 20 Assets hinzu. Wenn Sie alle Assets im Ordner auswählen, wird eine falsche Anzahl angezeigt (CQ-4316243).

* Wenn Sie eine Seite aktualisieren, zeigt die Sortierung von Ordnern oder Assets keine geeigneten Ergebnisse an (CQ-4316200).

* Die Handlebars-JavaScript-Bibliothek wurde auf Version 4.7.7 aktualisiert (NPR-36375).

* Benutzerdefinierte Bundles werden bei der Installation eines neuen Code-Pakets mit Package Manager nicht aktualisiert (NPR-35949).

* Ein `resourceresolver` Sling-Bundle führt dazu, dass die `Sling:alias`-Abfrage fehlschlägt (NPR-35335).

* Der Kontextpfad wird beim Einrichten von SSL in AEM entfernt (NPR-35294).

* Die `SegmentNotFound`-Ausnahme wird nach einer langwierigen Sitzung zurückgegeben (NPR-36405).

### Integrationen {#integrations-6590}

* Seiteneigenschaften können nicht gespeichert werden, wenn die Vererbung für Cloud Services Experience Fragments aktiviert ist (NPR-36107).

* Die Paginierung der IMS-Benutzeroberfläche und das verzögerte Laden zeigen keine geeigneten Ergebnisse an (NPR-36046).

* Wenn Sie eine A4T-Target-Konfiguration erstellen und die Berichtsquelle als [!DNL Adobe Analytics] auswählen, sind in der Dropdown-Liste keine Adobe Target-fähigen Report Suites verfügbar (NPR-36006).

### Projekte {#projects-6590}

* Die Eigenschaften eines Projekts können nicht gespeichert werden, da der JCR-Pfad zum Projekt aufgrund eines zusätzlichen Schrägstrichs (/), der an den Projektpfad angehängt ist, nicht aufgelöst wurde (NPR-36191).

### Screens {#screens-6590}

* [!DNL Experience Manager Screens] -Player können sich nicht authentifizieren, wenn ein benutzerdefinierter 2FA-Authentifizierungs-Handler verwendet wird (NPR-35854).

### Commerce {#commerce-6590}

* Der Assistent [!UICONTROL Commerce Catalog] lädt nicht mehr als 40 Elemente in die Spaltenansicht (CQ-4318379).

### Übersetzungsprojekte {#translation-6590}

* Die Optionen zum Aktualisieren oder Überschreiben werden beim erneuten Übersetzen einer `es`-Seite auf `es_es`-Seite nicht angezeigt. (NPR-36170)

* Wenn die Option &quot;Automatische Genehmigung&quot;für ein Projekt mit menschlicher Übersetzung ausgewählt ist, wird der Auftragsstatus als `Unknown` angezeigt (NPR-35981).

* Wenn Sie eine Seite übersetzen, wird der Referenzpfad von Experience Fragments nicht zum Ziel-Experience Fragment-Referenzpfad aktualisiert (NPR-35911).

* Wenn Sie Änderungen an den übergeordneten und untergeordneten Seiten vornehmen und die übergeordnete Seite zur Übersetzung senden, werden die untergeordneten Seiten ebenfalls falsch übersetzt (NPR-35896).

* Wenn mehrere gleichzeitige Übersetzungsprojekte für eine ausgewählte Seite vorhanden sind, verknüpft die Option [!UICONTROL Gehe zu Projekten] nicht mit dem neuesten Übersetzungsprojekt (NPR-35454).

* Wenn Sie Assets in [!DNL Dynamic Media] veröffentlichen, zeigt [!DNL Experience Manager] eine falsche Meldung für nicht veröffentlichte Tags an (CQ-4315914, CQ-4315913).

* Wenn Sie einen gelöschten Auftrag öffnen, zeigt [!DNL Experience Manager] eine falsche Meldung an (CQ-4315910).

### Workflow {#workflow-6590}

* Wenn Sie für im Posteingang verfügbare Elemente auf die Aktionen &quot;Fertig stellen&quot;, &quot;Delegieren&quot;oder &quot;Öffnen&quot;klicken, gibt es keinen visuellen Hinweis darauf, dass diese Aktionen abgeschlossen sind (NPR-36317).

### [!DNL Communities] {#communities-6590}

* Bei der Spam-Filterung verbraucht das System 100 % des JAVA-Heap-Speichers, wodurch der AEM heruntergefahren wird (NPR-36316, NPR-36493).
* In Foren werden die JCR-Sitzungsdaten aus SearchCommentSocialComponentListProvider ausgetauscht (NPR-36235).
* Das Öffnen einer bestimmten Posteingangsnachricht spiegelt alle Nachrichten mit unsachgemäßer Paginierung und anderen Problemen wider (NPR-35917).

### [!DNL Brand Portal] {#brandportal-6590}

* Das Feature Flag &quot;Asset-Beschaffung&quot;ist bei der Konfiguration von [!DNL Experience Manager Assets] mit [!DNL Brand Portal] automatisch aktiviert (NPR-36010).

### [!DNL Forms] {#forms-6590}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.
>* Sie können jetzt Anwendungen mit [!DNL Azul Zulu]-Builds von [!DNL OpenJDK] für [!DNL Experience Manager Forms] in OSGi-Bereitstellungen entwickeln und betreiben.


**Adaptive Formulare**

* Sprachinitialisierungsprobleme in [!DNL Experience Manager Forms] 6.5.7.0 beim Generieren mehrerer Übersetzungswörterbücher (NPR-36439).
* Wenn Sie eine Anlage zum adaptiven Formularfragment hinzufügen und das Formular senden, zeigt [!DNL Experience Manager Forms] die folgende Fehlermeldung an (NPR-36195):

   ```TXT
    POST /content/forms/af/attachmentissue/jcr:content/guideContainer.af.submit.jsp HTTP/1.1] com.adobe.aemds.guide.servlet.GuideSubmitServlet [AF] Invalid file name or mime type for file resulted in submission failure
   ```

* Wenn Sie mit der menschlichen Übersetzung ein Wörterbuch aktualisieren und dann ein adaptives Formular in der Vorschau anzeigen, werden die Änderungen nicht angezeigt. (NPR-36035)

**Interaktive Kommunikation**

* Wenn Sie ein Bild mit dem Druckkanal für interaktive Kommunikation hochladen und bearbeiten, ist das Bild nicht mehr sichtbar (NPR-36518).

* Beim Bearbeiten eines Text-Assets und Füllen eines Platzhalters werden alle interaktiven Elemente aus dem Navigationsbereich entfernt (NPR-35991).

**Arbeitsablauf**

* Wenn Sie den REST-Endpunkt eines [!DNL Experience Manager Forms]-Dienstes auf JBoss aufrufen, zeigt [!DNL Experience Manager] die folgende Fehlermeldung an (NPR-36305):

   ```TXT
   Invalid input. The maximum length of 2000 characters was exceeded.
   ```

**BackendIntegration**

* Es kann kein Formulardatenmodell gespeichert werden, während das Read Service-Argument an einen Literalwert gebunden wird, der einen Bindestrich enthält (NPR-36366).

**Dokumentensicherheit**

* Wenn Sie Zertifizierung und HSM für GlobalSign festlegen, zeigt [!DNL Experience Manager Forms] die Fehlermeldungen `Unsuported Algorithm` und `Invalid TSA Certificate` an, während ein Zeitstempel zu LTV hinzugefügt wird (NPR-36026, NPR-36025).

**Document Services**

* Aktualisierungen der [!DNL Gibson]-Bibliothek für die Integration mit [!DNL Experience Manager Forms] (NPR-36211).

**Foundation JEE**

* Wenn Sie Endpunktverwaltung in der AdminUI auswählen, zeigt [!DNL Experience Manager Forms] die Fehlermeldung `endpoint registry failure` an (CQ-4320249).

Informationen zu Sicherheitsupdates finden Sie auf der Seite [Experience Manager-Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.9.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.9.0 ist Experience Manager 6.5 erforderlich. Detaillierte Anweisungen finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) .
* Der Service Pack-Download ist auf der Adobe [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.9.0 mithilfe von Package Manager auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, das [!DNL Adobe Experience Manager] 6.5.9.0-Paket zu entfernen oder zu deinstallieren.

### Installieren Sie das Service Pack {#install-service-pack}

Gehen Sie wie folgt vor, um das Service Pack auf einer [!DNL Adobe Experience Manager] 6.5-Instanz zu installieren:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt auch einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.9.zip) herunter.

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. In der Regel geschieht dies auf [!DNL Safari], kann aber gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, Adobe Experience Manager 6.5.9.0 automatisch auf einer funktionierenden Instanz zu installieren:

A. Platzieren Sie das Paket im Ordner `../crx-quickstart/install` , wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true` , damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.9.0 unterstützt keine Installation von Bootstraps.

**Bestätigen der Installation**

1. Auf der Seite mit den Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.9.0)` unter [!UICONTROL Installierte Produkte] angezeigt.

1. Alle OSGi-Bundles sind entweder **[!UICONTROL ACTIVE]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Web-Konsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Installieren des Adobe Experience Manager Forms Add-On-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie Experience Manager Forms nicht verwenden. Fehlerbehebungen in Experience Manager Forms werden eine Woche nach der geplanten Veröffentlichung des Service Packs über ein separates Add-On-Paket bereitgestellt.[!DNL Experience Manager]

1. Stellen Sie sicher, dass Sie das Adobe Experience Manager Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms Add-On-Paket wie unter [Installieren von AEM Forms Add-On-Paketen](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package) beschrieben.

>[!NOTE]
>
>AEM 6.5.9.0 enthält eine neue Version von [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf AEM 6.5.9.0 aktualisieren, installieren Sie die neueste Version des Pakets nach der Installation des Forms Add-On-Pakets.

### Installieren von Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für Experience Manager Forms on JEE und zur Konfiguration nach der Bereitstellung finden Sie in den [Versionshinweisen](jee-patch-installer-65.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für Experience Manager Forms on JEE installiert haben, installieren Sie das neueste Add-On-Paket für Forms, löschen Sie das Add-On-Paket für Forms aus dem Ordner `crx-repository\install` und starten Sie den Server neu.

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.9.0 ist im [Maven Central Repository](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.9/) verfügbar.

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und Einschließen der folgenden Abhängigkeit in Ihr Projekt-POM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.9</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstelle des Adobe Public Maven-Repositorys (`repo.adobe.com`) verfügbar. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Es gibt also kein `classifier`-Tag mit `apis` als Wert für das `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Nachstehend finden Sie eine Liste der Funktionen, die mit [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und in einer zukünftigen Version später entfernt. Normalerweise wird eine alternative Option bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm **[!UICONTROL AEM Cloud Services Opt-in]** wird nicht mehr unterstützt. Da die Experience Manager- und Adobe Target-Integration in Experience Manager 6.5 aktualisiert wurde, um die Adobe Target Standard-API zu unterstützen, die die Authentifizierung über Adobe IMS und I/O verwendet, und die zunehmende Rolle von Adobe Launch bei der Instrumentierung von Experience Manager-Seiten für Analysen und Personalisierung, ist der Opt-in-Assistent funktionell irrelevant geworden. | Konfigurieren Sie Systemverbindungen, die Adobe IMS-Authentifizierung und die [!DNL Adobe I/O]-Integrationen über die entsprechenden Experience Manager-Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5 auf 6.5.9.0 aktualisieren, können Sie `RRD4JReporter` Ausnahmen in der Datei `error.log` anzeigen. Starten Sie die Instanz neu, um das Problem zu beheben.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 5 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Wenn ein Ordner in der Hierarchie in [!DNL Experience Manager Assets] umbenannt wird und der verschachtelte Ordner, der ein Asset enthält, in [!DNL Brand Portal] veröffentlicht wird, wird der Titel des Ordners erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

## OSGi-Pakete und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die OSGi-Pakete und Inhaltspakete aufgelistet, die in [!DNL Experience Manager] 6.5.9.0 enthalten sind:

* [Liste der in Experience Manager 6.5.9.0 enthaltenen OSGi-Bundles](assets/6590_bundles.txt)

* [Liste der in Experience Manager 6.5.9.0 enthaltenen Inhaltspakete](assets/6590_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Weitere Informationen finden Sie unter [Kontaktaufnahme mit der Adobe-Kundenunterstützung](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 - Versionshinweise](/help/release-notes/release-notes.md)
* [[!DNL Experience Manager] Produktseite](https://www.adobe.com/de/marketing/experience-manager.html)
* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

