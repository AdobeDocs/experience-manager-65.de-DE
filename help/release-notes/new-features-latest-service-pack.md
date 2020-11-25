---
title: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 7
description: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 7
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: e056d25cf16d79e8eadc80b9cb17b60b2ba8d7e1
workflow-type: tm+mt
source-wordcount: '2704'
ht-degree: 5%

---


# Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 7 {#aem-whats-new-service-pack}

![Whats-new](assets/whatsnew.jpeg)

[!DNL Adobe Experience Manager] 6.5 Service Packs bieten in vierteljährlichen Abständen neue Funktionen, kundenspezifische Verbesserungen und Verbesserungen in Bezug auf Leistung, Stabilität und Sicherheit. Die vierteljährliche Verfügbarkeit erleichtert den Zugriff auf neue Funktionen und Innovationen.

In diesem Artikel werden die Funktionen des neuesten 6.5 Service Packs, die [wichtigsten Funktionen der vorherigen 6.5 Service Packs](#key-features-previous-service-packs)und die [wichtigsten AEM seit der letzten Service Pack](#key-releases-since-last-sp) -Version hervorgehoben.

## Adobe [!DNL Experience Manager Sites] {#aem-sites}

### Für die Aktualisierung verfügbare Live Copy-Seiten sortieren {#sort-livecopy-pages}

Sie können jetzt die für die Aktualisierung verfügbaren Live Copy-Seiten mit den Eigenschaften [!UICONTROL Name], [!UICONTROL Zuletzt geändertes Datum]und [!UICONTROL Letzte Rollout-Datum] sortieren. Das [!UICONTROL letzte Rollout-Datum] für eine Seite ist eine neue Eigenschaft, die in dieser Version eingeführt wurde.

### Verfügbarkeit von Seitenverschiebungen und MSM-Rollouts als asynchrone Vorgänge {#page-moves-msm-asynchronous}

Sie können jetzt die Seitenverschiebungen und MSM-Rollouts als asynchrone Vorgänge durchführen, um ihre Auswirkungen auf die Laufzeit zu reduzieren. Sie können die Vorgänge für eine sofortige oder spätere Ausführung planen. Der Status der zugehörigen Aufträge und Prozessschritte wird in einer Konsole angezeigt, was bei der Überwachung von MSM-Rollouts in großem Maßstab hilfreich ist.

## [!DNL Adobe Experience Manager Assets] {#aem-assets}

* [!DNL Assets] und [!DNL Dynamic Media] bieten mehrere Verbesserungen an der Barrierefreiheit. Die Verbesserungen betreffen die Tastaturnavigation, die Verwendung von Bildschirmlesehilfen und ähnliche Verbesserungen, um die Verwendung von Hilfstechnologien (AT) zu ermöglichen. Siehe [[!DNL Assets] Verbesserungen](/help/release-notes/sp-release-notes.md#assets-6570) und [[!DNL Dynamic Media] Verbesserungen](/help/release-notes/sp-release-notes.md#dynamic-media-6570).

* Die Benutzer können digitale Assets in den Ansichten &quot;Karte&quot;und &quot;Spalte&quot;sortieren.

## [!DNL Adobe Experience Manager Forms] {#aem-forms}

>[!NOTE]
>
>[!DNL Experience Manager Forms] Add-On-Pakete werden eine Woche nach der geplanten [!DNL Experience Manager] Service Pack-Version zur Verfügung gestellt. [!DNL Experience Manager] 6.5 Service Pack 7 (6.5.7.0) soll am 26. November 2020 veröffentlicht werden.

## Wichtige Funktionen in vorherigen [!DNL Experience Manager] 6.5 Service Packs {#key-features-previous-service-packs}

### [!DNL Experience Manager Sites] {#aem-sites-previous-service-packs}

#### Verfügbarkeit des Seitenumbruchs im asynchronen Modus (6.5.6.0) {#page-move-asynchronous}

Der Vorgang &quot;Verschieben der Seite&quot;ist jetzt im asynchronen Modus verfügbar. Zusätzlich zur sofortigen Ausführung können Sie auch den Vorgang &quot;Verschieben der Seite&quot;für eine spätere Ausführung planen.

#### Verbesserungen der Zugänglichkeit (6.5.5.0) {#accessibility-sites}

* Verbesserter Berichte von Fehlern durch Hinzufügen von Textinformationen.

* Verbesserter Fokus der Benutzeroberfläche während der Tastaturnavigation.

* Verbessertes Kontrastverhältnis für verschiedene Elemente der Benutzeroberfläche.

* Verbesserte Konsistenz von Alt-Attributen für Seitenbilder.

* Verbesserte Konsistenz der Beschriftungen von Accessible Rich Internet Applications (ARIA).

* Verbesserte Funktionen für den Nicht-Visual Desktop Access (NVDA).

* Verbesserte Unterstützung für Bildschirmlesehilfen.

#### Weitere wichtige Verbesserungen (6.5.5.0) {#other-enhancements-sites}

* Der anonyme Zugriff auf CRXDE Lite ist nicht erlaubt, um die Sicherheit zu erhöhen. Stattdessen werden die Benutzer zum Anmeldebildschirm weitergeleitet. See [Developing with CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* Beim Kopieren oder Einfügen einer Seitenstruktur haben Sie jetzt die Möglichkeit, entweder die Stammeseite einzufügen oder die Stammeseite mit den Unterseiten der Struktur einzufügen.

* [!DNL Adobe Experience Manager Experience Fragments] in [!DNL Adobe Target] Arbeitsbereiche exportiert werden, werden nun als eindeutige Angebot- und Angebot-Quellen in angezeigt [!DNL Target].

* Multi-Site-Manager - Der Veröffentlichungsauslöser löscht jetzt eine Komponente aus der veröffentlichten Seite, wenn eine Komponente aus der Quellseite gelöscht wird.

* Multi-Site-Manager: Wenn der Name einer lokalen Komponente in einer [!UICONTROL Live Copy] mit dem Namen einer Komponente im Entwurf identisch ist und die Komponente aus dem Entwurf herausgegeben wird, `_msm_moved` wird der Begriff nun dem Namen der lokalen Komponente hinzugefügt.

#### Verbesserungen am Stilsystem (6.5.4.0) {#style-system-enhancements}

Sie können jetzt Stile im Komponentendialogfeld mit dem erweiterten Stilsystem auswählen.

#### Leistungsverbesserungen in verschiedenen Bereichen (6.5.4.0) {#performance-improvements}

* Verkürzte Ladezeit und Initialisierung von ContextHub innerhalb einer Site (`contexthub.kernel.js`). Das führt zu schnelleren Seitenladevorgängen während eines Site-Besuchs.

* Die Zeit zum Aktualisieren einer Seite nach dem Ziehen [!DNL Experience Fragments] in den [!DNL Sites] Seiten-Editor wurde verringert.

* Die Ladezeit für Einträge auf einer [!DNL Sites] Seite mit mehr als 200 Live-Kopien in der Übersicht über **[!UICONTROL Live Copy wurde verkürzt]**.

* Verbesserte Verarbeitung von unvollständigen oder ungültigen URLs. Solche URLs können den Vorlageneditor verlangsamen.

### [!DNL Adobe Experience Manager Assets] {#aem-assets-previous-service-packs}

#### Accessibility enhancements (6.5.6.0) {#accessibility-assets-6560}

* **Verbesserter Fokus der Benutzeroberfläche während der Tastaturnavigation**, z. B. auf:

   * `x` im Dialogfeld [!UICONTROL Vorschau] der Version eines Assets in der [!UICONTROL Zeitleiste].

   * Verfügbare Benutzeroberflächenoptionen.

   * E-Mail-Feld im Dialogfeld &quot; [!UICONTROL Link] freigeben&quot;und Feld zum Hinzufügen einer geschlossenen Benutzergruppe auf der Registerkarte &quot; [!UICONTROL Berechtigung] &quot;der [!UICONTROL Ordnereigenschaften].

* **Verbesserte Funktionalität mit Tastaturbefehlen**

   Die Benutzer können die Steuerelemente mithilfe der Tastatur im Metadaten-Schema-Formulareditor im Durchsuchenmodus der Bildschirmlesehilfe ziehen.

* **Verbesserte Benutzerfreundlichkeit für Bildschirmlesehilfen** durch Folgendes:

   * Bildschirmlesehilfen geben den Zweck von Video- und Audio-Playern an.

   * Bildschirmlesehilfen geben den Zweck der Optionen der Benutzeroberfläche an, die mithilfe des Dialogfelds [!UICONTROL zur Auswahl von] Tags in den Asset- [!UICONTROL Eigenschaften]ausgewählten Tags zu entfernen.

   * Bildschirmlesehilfen geben die Zeilenüberschriften und Zeileneinträge von Tabellen an, sodass Benutzer wissen, welche Einträge zu derselben Zeile gehören.

   * Beschreibende und aussagekräftige Seitentitel der Suchseite.

   * Bildschirmlesehilfen geben die Optionen im Suchfilterbedienfeld als erweiterbare Akkordeons an.

#### Weitere Verbesserungen in [!DNL Assets] (6.5.6.0) {#other-enhancements-assets-6560}

* Benutzergruppen, die Ordnern zugeordnet sind (privat und nicht privat), werden nun beim [Löschen dieser Ordner](/help/assets/private-folder.md#delete-private-folder)aus dem Repository entfernt. Die vorhandenen redundanten, verwaisten, nicht verwendeten und automatisch generierten Benutzergruppen können jedoch mit JMX aus dem Repository entfernt werden.

#### Verbesserungen der Barrierefreiheit in [!DNL Assets] (6.5.5.0) {#assets-accessibility}

[!DNL Experience Manager Assets] ist nun in Übereinstimmung mit den Web Content Accessibility Guidelines (WCAG) leichter zugänglich. Die Barrierefreiheit wurde durch die folgenden Verbesserungen verbessert:

* Viele Elemente, Steuerelemente, Seiten und Dialoge der Benutzeroberfläche sind für Bildschirmlesehilfen geeignet.

* Auf viele Elemente, Steuerelemente und Eingabefelder der Benutzeroberfläche kann über die Tastatur zugegriffen werden.

* Farbe und Kontrast einiger Elemente der Benutzeroberfläche werden aktualisiert, sodass Benutzer mit eingeschränkter Sehkraft oder Benutzer ohne Farbwahrnehmung diese Elemente der Benutzeroberfläche unterscheiden können. For example, the color of star rating icons (such as in [!UICONTROL Rating] section of [!UICONTROL Advanced] tab in asset [!UICONTROL Properties] or in card view) is changed for appropriate contrast.

   ![Bewertungssymbole mit verbessertem Kontrast](assets/star-rating-icons.png)

#### Erweiterte Ausnahmebehandlung (6.5.5.0) {#exception-handling}

[!DNL Assets] Der Benutzeroberflächenfluss bietet eine bessere Ausnahmebehandlung. Wenn ein Asset keinen Typ für seine Dimension aufweist, wird die beobachtete Ausnahme in den Protokolldateien aufgezeichnet.

#### Unterstützung für 3D-Assets in [!DNL Dynamic Media] (6.5.5.0) {#support-for-3d}

Die Unterstützung für 3D-Bilder in [!DNL Dynamic Media] ermöglicht es Kunden, 3D-Inhalte zu Webseiten und Anwendungen hinzuzufügen. Die Unterstützung umfasst:

* Veröffentlichen Sie allgemeine 3D-Asset-Formate und generieren Sie eine Asset-URL, die auf Webseiten und in anderen Anwendungen verwendet werden kann.

* Ein 3D-Web Viewer, powered by [!DNL Adobe Dimension], zur interaktiven Ansicht der veröffentlichten 3D-Assets.

* Veröffentlichen und Ansicht von gängigen 3D-Assets auf [!DNL Experience Manager Sites] Seiten mithilfe der [!DNL Sites] WCM-Komponente.

#### Konfigurieren [!DNL Experience Manager Assets] mit [!DNL Brand Portal] (6.5.4.0) {#configure-assets-bp}

Der Kanal für die Autorisierung zwischen [!DNL Experience Manager Assets] und [!DNL Brand Portal] wird geändert. Earlier, [!DNL Brand Portal] was configured in Classic UI via Legacy OAuth Gateway, which uses the JWT token exchange to obtain an IMS Access token for authorization. [!DNL Experience Manager Assets] ist jetzt mit [!DNL Brand Portal] der Adobe I/O konfiguriert, die ein IMS-Token für die Autorisierung Ihres [!DNL Brand Portal] Mieters abruft.

The steps to configure [!DNL Experience Manager Assets] with [!DNL Brand Portal] are different depending on your [!DNL Experience Manager] version, and whether you are configuring for the first time, or upgrading the existing configurations. See [Configure Experience Manager Assets with Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) for details.

#### Accessibility enhancements (6.5.4.0) {#accessibility-enhancements}

[!DNL Experience Manager Assets] umfasst die folgenden Barrierefreiheitsverbesserungen:

* Mit den Pfeiltasten auf der Tastatur können Sie Bereiche innerhalb gezoomter Bilder verschieben und schwenken. Weitere Informationen finden Sie unter [Vorschau-Assets nur](../assets/manage-assets.md#previewing-assets)mit Tastaturbefehlen.

* Die Kontrollkästchen für gemischten Status (bei denen, sofern Sie nicht alle verschachtelten Kontrollkästchen auswählen, vorausgesagt, dass die Kontrollkästchen der ersten Ebene nicht ausgewählt sind und durchgestrichen werden) im Bedienfeld &quot;Filter&quot;sind für Bildschirmlesehilfen lesbar.

* Datums- und Uhrzeitformateinschränkungen werden in den Feldbezeichnungen der Datumsfelder bereitgestellt, damit die Benutzer das Datum mit der Tastatur im korrekten Format eingeben können.
Beispiel: `On Time (MM-DD-YYYY HH:mm)`. Hier ist MM Monat im zweistelligen Format, JJJJ ist Jahr, TT ist Tag im zweistelligen Format, HH ist Stunde im 24-Stunden-Militärformat und mm ist Minute.

* Bildschirmlesehilfen geben die Option zum Entfernen ausgewählter Tags (`X` Symbol) und die Anzahl der ausgewählten Tags an.

#### Sortierbare Spalte für Erstellungsdatum von Assets in Ansicht der Liste (6.5.3.0) {#sortable-date-created-column}

Eine neue sortierbare Spalte für das Erstellungsdatum von Assets wird in der DAM-Liste-Ansicht und in den Asset-Suchergebnissen in der Liste-Ansicht hinzugefügt.

![Sortierbare Spalte für das erstellte Datum](assets/asset-created-date.png)

#### Visuelle Suche nach [!DNL Adobe Experience Manager Assets] (6.5.2.0) {#visual-search}

[!DNL Assets] Benutzer können visuell ähnliche Bilder suchen. Experience Manager zeigt die intelligenten getaggten Bilder aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. See [Visual search](../assets/search-assets.md).

### Dynamic Media {#dynamic-media-previous-service-packs}

#### Ungültige CDN-zwischengespeicherte Inhalte (6.5.6.0) {#invalidate-cdn-cached-content}

Sie können jetzt die [!DNL Dynamic Media] Benutzeroberfläche verwenden, um zwischengespeicherte Content Versand Network (CDN)-Inhalte ungültig zu machen. Die aktualisierten Assets stehen daher sofort zur Verfügung, anstatt darauf zu warten, dass der Cache abläuft. Sie können CDN für ungültig erklären, indem Sie:

* Erstellen einer Vorlage für die Ungültigmachung eines CDN: Auswählen von Assets und formularverknüpften vorlagenbasierten URLs

* Auswählen von Assets und zugehörigen Vorgaben mithilfe der Asset-Auswahl

* Hinzufügen vollständiger Asset-URLs

#### Selektives Veröffentlichen von Assets in [!DNL Experience Manager] und [!DNL Dynamic Media] (6.5.6.0) {#selective-publishing}

Sie können jetzt Assets selektiv veröffentlichen oder die Veröffentlichung rückgängig machen, entweder mit dem Assistenten &quot; [!DNL Experience Manager] Schnelle Veröffentlichung [!DNL Dynamic Media] &quot; [!UICONTROL oder mit dem Assistenten &quot;Veröffentlichung] verwalten  &quot;. Sie können auch den `Publish` Modus oder `Unpublish` Modus auf Ordnerebene festlegen.

#### Smart Imaging für dynamische Medien {#smart-imaging}

Die intelligente Bildbearbeitung nutzt die einzigartigen Ansichtsmerkmale der einzelnen Benutzer, um automatisch die richtigen Bilder bereitzustellen, die für ihr Erlebnis optimiert wurden, was zu einer besseren Leistung und Interaktion führt. Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Siehe [Smart Imaging](../assets/imaging-faq.md).

#### Smart-Zuschneiden in Video-Profilen für dynamische Medien (6.5.3.0) {#smart-crop-video}

Smartes Zuschneiden für Video – eine optionale Funktion, die in Videoprofilen verfügbar ist – ist ein Tool, das die Leistung von künstlicher Intelligenz in Adobe Sensei nutzt, um den Fokuspunkt in adaptiven oder progressiven Videos, die Sie hochgeladen haben, unabhängig von der Größe automatisch zu erkennen und zu beschneiden. See [About using smart crop in video profiles](../assets/video-profiles.md).

### Experience Manager Forms {#aem-forms-previous-service-packs}

#### Ausfüllen eines adaptiven Formulars im Client (6.5.6.0) {#prefill-merge-data-at-client}

Wenn Sie ein adaptives Formular im Voraus ausfüllen, führt der [!DNL Experience Manager Forms] Server Daten mit einem adaptiven Formular zusammen und stellt das ausgefüllte Formular für Sie bereit. Standardmäßig erfolgt die Datenzusammenführung auf dem Server.
Sie können den [!DNL Experience Manager Forms] Server jetzt so konfigurieren, dass die Datenzusammenführungsaktion auf dem Client [und nicht auf dem Server](../../help/forms/using/prepopulate-adaptive-form-fields.md) durchgeführt wird. Dadurch wird die erforderliche Zeit zum Vorausfüllen und Wiedergeben adaptiver Formulare erheblich verringert.

#### Integration des Formulardatenmodells mit RESTful-APIs auf einem Server mit Zweiweg-SSL-Implementierung (6.5.6.0) {#fdm-integration-rest-apis-two-way-ssl}

[!DNL Experience Manager Forms] Formulardatenmodell kann jetzt mit RESTful-APIs auf einem Server [integriert werden, auf dem ein bidirektionales SSL implementiert ist](../../help/forms/using/configure-data-sources.md).

#### Neue Unterstützung für [!DNL Adobe Sign] Text-Tags im Automated forms conversion-Dienst (6.5.6.0) {#sign-integration-acroform-afcs}

Wenn ein AcroForm [!DNL Adobe Sign] Text-Tags enthält, werden diese Felder jetzt erkannt und als [!DNL Adobe Sign] Felder im adaptiven Formular dargestellt, die mit [!DNL Automated Forms Conversion service]konvertiert werden. Ein Unterzeichner kann diese Felder beim Unterschreiben des adaptiven Formulars ausfüllen.

#### Support to convert colored PDF forms to adaptive forms (6.5.6.0) {#colored-PDF-forms}

Sie können farbige PDF forms [!DNL Automated Forms Conversion service] in adaptive Formulare konvertieren.

#### Unterstützung für SMB 2- und SMB 3-Protokolle (6.5.6.0) {#smb-support}

[!DNL Experience Manager Forms] unterstützt jetzt SMB 2- und SMB 3-Protokolle.

#### Verbesserte Zwischenspeicherung für übersetzte Seiten adaptiver Formulare (6.5.6.0) {#enhanced-caching-translated-adaptive-forms}

Sie können jetzt [das Gebietsschema als Selektor in der URL des adaptiven Formulars anstelle eines Arguments in der URL](../../help/forms/using/supporting-new-language-localization.md)des adaptiven Formulars angeben. Dadurch können übersetzte adaptive Formulare zwischengespeichert werden [!DNL Experience Manager Dispatcher]. Das Zwischenspeichern übersetzter adaptiver Formulare war in früheren Versionen nicht möglich. Detaillierte Informationen zum Konfigurieren der Zwischenspeicherung für die Verwendung des Gebietsschemas als Selektor in der URL des adaptiven Formulars finden Sie unter Cache für adaptive Formulare [konfigurieren beim Dispatcher](../../help/forms/using/configure-adaptive-forms-cache.md).

#### Ausgabe des Formulardatenmodelldiensts in einer Variablen speichern (6.5.6.0) {#save-fdm-service-to-variable}

Mit dem Formulardatenmodell können Sie die Ausgabe eines Formulardatenmodelldiensts in einer Variablen speichern. [!DNL Experience Manager Forms] ordnet nun automatisch den Typ des Formulardatenmodelldiensts dem Variablentyp zu.

#### Mehrere Dateien für die Dateianlagenkomponente anhängen (6.5.6.0) {#attach-multiple-files}

Sie können jetzt mehrere Dateien [an die](../../help/forms/using/introduction-forms-authoring.md) Dateianlagenkomponente [!UICONTROL adaptiver Formulare] anhängen.

#### Anpassen der Adobe Experience Manager Inbox-Spalten (6.5.5.0) {#customize-aem-inbox-columns}

Sie können einen [!DNL Experience Manager] Posteingang anpassen, um den Standardtitel einer Spalte zu ändern, die Position einer Spalte neu anzuordnen und zusätzliche Spalten basierend auf den Daten eines Workflows anzuzeigen. Mitglieder `administrators` oder `workflow-administrators` Gruppen können die Spalten anpassen. Weitere Informationen finden Sie unter [Admin-Steuerung](../sites-authoring/inbox.md#inbox-admin-control).

![Anpassen der Experience Manager-Posteingangsspalten](assets/customize-columns.gif)

#### Interaktive Kommunikation als Entwurf speichern (6.5.5.0) {#save-as-draft}

Sie können die Agent-Benutzeroberfläche verwenden, um einen oder mehrere Entwürfe für jede interaktive Kommunikation zu speichern und den Entwurf später abzurufen, um weiter daran zu arbeiten. Sie können für jeden Entwurf einen anderen Namen angeben, um ihn zu identifizieren. Weitere Informationen finden Sie unter Interaktive Kommunikation als Entwurf [speichern](../forms/using/prepare-send-interactive-communication.md#save-as-draft).

![Als Entwurf speichern](assets/save-as-draft.gif)

#### [!DNL Oracle WebLogic] Anwendungsserverunterstützung (6.5.5.0) {#weblogic-support}

Adobe Experience Manager Forms hat Unterstützung [!DNL Oracle WebLogic 12] für Adobe Experience Manager Forms on JEE hinzugefügt. Sie können von einer früheren Version aktualisieren oder ein neues Experience Manager 6.5 Forms auf dem JEE-Server auf [!DNL Oracle WebLogic] 12.2.1.4 und höher einrichten. Später entspricht den Änderungen der kleineren Version, wobei x in 12.2.1.x durch eine Versionsnummer ersetzt wird.

#### Verbesserungen der Zugänglichkeit (6.5.5.0) {#accessibility-improvements}

Adobe Experience Manager Forms umfasst die folgenden Verbesserungen der Barrierefreiheit:

* Wenn ein Benutzer ein adaptives Formular als HTML-Formular Vorschau, behält das Feld &quot; [!UICONTROL Freihandsignatur] &quot;den Fokus der Registerkarte bei.

* Die Fehlermeldungen, die beim Senden eines adaptiven Formulars angezeigt werden, enthalten jetzt das `aria-describedBy` Attribut. Das Attribut wird an die in der Fehlermeldung genannten Felder angehängt. Das `aria-describedby` Attribut gibt IDs der Elemente an, die das Objekt beschreiben. Es hilft, eine Beziehung zwischen Widgets oder Gruppen und Text, der sie beschrieben.

* Wenn ein adaptives Formular einige Pflichtfelder enthält, wird das obligatorische Attribut im ARIA-Schema auf `True` für diese Felder festgelegt.

#### X-509-Zertifikatbasierte Authentifizierung für SOAP-basierte Webdienste im Formulardatenmodell (6.5.5.0) {#x509-based-authentication-soap}

Das Formulardatenmodell unterstützt jetzt die zertifikatbasierte X-509-Authentifizierung bei Verwendung von SOAP-Webdiensten als Datenquelle. Weitere Informationen finden Sie unter SOAP-Webdienste [konfigurieren](../forms/using/configure-data-sources.md#configure-soap-web-services).

#### Weitere wichtige Verbesserungen (6.5.5.0) {#other-improvements}

* Experience Manager 6.5 Forms on JEE Dokument Security basiert jetzt auf [!DNL Apache Struts 2].

* Unterstützung für [!DNL Oracle Real Applications Cluster (RAC) 19c].

#### Druckbare Ausgabe in Experience Manager Forms Workflows (6.5.4.0) generieren {#generate-printable-output}

Mit dem Arbeitsablaufschritt &quot;Druckbare Ausgabe generieren&quot;können Sie eine Quellvorlagendatei in eine Datendatei integrieren. Mit dieser Integration können Sie verschiedene Kopien der Vorlagendatei drucken oder speichern. Der Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe. Weitere Informationen zu dieser Funktion finden Sie unter [Forms-zentrierter Arbeitsablauf auf OSGi - Schritt-Referenz](../forms/using/aem-forms-workflow-step-reference.md).

![Druckbare Ausgabe generieren](assets/generate-print-output-step.gif)

#### Unterstützung für adaptive Formulare und interaktive Kommunikation im Layoutmodus (6.5.4.0) mit mehreren Spalten {#multi-column-adaptive-forms}

Sie können jetzt die Anzahl der Spalten für ein Bedienfeld in adaptiven Formularen und in interaktiver Kommunikation definieren. Wechseln Sie zum Layoutmodus, um die neue Option für mehrere Spalten zu verwenden. Weitere Informationen finden Sie unter [Verwenden des Layoutmodus zum Ändern der Größe von Komponenten](../forms/using/resize-using-layout-mode.md).

![Mehrspaltiges Layout](assets/multi-column-layout.gif)

#### Experience Manager-Posteingangsanpassungen (6.5.4.0) {#aem-inbox}

Die neue Option &quot;Admin-Steuerung&quot;ermöglicht den Administratoren Folgendes:

* Passen Sie den Kopfzeilentext und das Logo an.

* Steuern Sie die Anzeige der in der Kopfzeile verfügbaren Navigationslinks.

Die Option &quot;Admin-Steuerung&quot;ist nur für die Mitglieder der `administrators` Gruppe oder `workflow-administrators` Gruppe sichtbar. Weitere Informationen zu dieser Funktion finden Sie unter [Ihr Posteingang](../sites-authoring/inbox.md).

#### Rich-Text-Unterstützung in HTML5-Formularen (6.5.4.0) {#rich-text-support}

Konvertieren Sie ein Textfeld in einem XFA-Formular in ein Rich-Text-Feld in einem HTML5-Formular. Weitere Informationen finden Sie unter [Entwerfen von Formularvorlagen für HTML5-Formulare](../forms/using/designing-form-template.md).

#### Accessibility enhancements (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms umfasst die folgenden Verbesserungen der Barrierefreiheit:

* Kontrollkästchen, Links, Datumsauswahl und Datumseingabefelder werden von Bildschirmlesehilfen korrekt in einem adaptiven Formular angekündigt.

* Jede Seite eines adaptiven Formulars enthält jetzt einen Titel und eine Hauptmarkenbeschriftung.

#### Freigeben und Anfordern von Inbox-Elementen eines Experience Manager Forms-Benutzers (6.5.3.0) {#share-request-access}

Sie können Ihre Inbox-Elemente für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente erhält, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern. Siehe [Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers](../forms/using/configure-shared-queues-osgi.md).

#### Abwesenheitseinstellungen für Posteingangselemente eines Experience Manager Forms-Benutzers konfigurieren (6.5.3.0) {#configure-out-of-office}

Wenn Sie planen, abwesend zu sein, können Sie angeben, was mit Artikeln geschieht, die Ihnen für diesen Zeitraum zugewiesen wurden.
Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Sie können eine Standardperson festlegen, an die alle Elemente gesendet werden sollen. Siehe Abwesenheitseinstellungen [konfigurieren](../forms/using/configure-out-of-office-settings.md).

#### Generieren mehrerer interaktiver Kommunikation mit der Batch-API für Experience Manager Forms (6.5.3.0) {#generate-multiple-ic}

Sie können die Stapel-API verwenden, um mehrere interaktive Mitteilungen aus einer Vorlage zu erstellen. Die Vorlage ist eine interaktive Kommunikation ohne Daten. Die Stapel-API kombiniert Daten mit einer Vorlage, um eine interaktive Kommunikation zu erzeugen. Die API ist bei der Massenproduktion interaktiver Kommunikation nützlich. Zum Beispiel Telefonrechnungen, Kreditkartenauszüge für mehrere Kunden. Siehe [Generieren mehrerer interaktiver Kommunikation mit der Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Wichtigste Veröffentlichungen seit Adobe Experience Manager 6.5 SP6 {#key-releases-since-last-sp}

Zwischen dem 03. September 2020 und dem 26. November 2020 veröffentlichte die Adobe zusätzlich zu den Service Packs und kumulativen Fix Packs die folgenden Inhalte:

* [!DNL Adobe Experience Manager] als Cloud Service [2020.9.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-2020-9-0.html?lang=en#release-notes) und [2020.10.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-2020-10-0.html?lang=en#release-notes).

* [[!DNL Experience Manager] Desktop-App 2.0 (2.0.3.2)](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html).

* [WKND-Referenzseite - 0.0.6](https://github.com/adobe/aem-guides-wknd/releases/tag/aem-guides-wknd-0.0.6)

* [Experience Manager Screens: Feature Pack 202008](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202008.html)

* [Adobe Asset Link v2.2](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html)

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] 6.5 Dokumentation](../user-guide/home.md)
>* [Allgemeine Versionshinweise für [!DNL Adobe Experience Manager] 6.5](release-notes.md)
>* [Versionshinweise zu Service Packs für [!DNL Adobe Experience Manager] 6.5](sp-release-notes.md)

