---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6,5
description: '"[!DNL Adobe Experience Manager] 6.5-Hinweise mit Versionsinformationen, Neuigkeiten, Installationsanleitungen und detaillierten Änderungslisten."'
mini-toc-levels: 3
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 6b75c41cf796b28409c263175cf3f3a2044422ff
workflow-type: tm+mt
source-wordcount: '3733'
ht-degree: 7%

---

# [!DNL Adobe Experience Manager] 6.5 Neueste Service Pack - Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.13.0 |
| Typ | Service Pack-Version |
| Datum | 26. Mai 2022 |
| Download-URL | [Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.13.0.zip) |

## Was ist enthalten in [!DNL Experience Manager] 6,5,13,0 {#what-is-included-in-aem}

[!DNL Experience Manager] 6.5.13.0 umfasst neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Dieses Service Pack installieren](#install) on [!DNL Experience Manager] 6.5.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.13.0 sind:

* Unsichtbares CAPTCHA in einem adaptiven Formular verwenden: Sie können jetzt ein unsichtbares CAPTCHA verwenden, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen. Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Herausforderung nicht angezeigt. Sie hilft bei der Bewertung der Fertigstellung menschlicher Formulare ohne Checkbox-Anforderungen, reduziert Anpassungsbemühungen und verbessert das Benutzererlebnis für Endbenutzer. (NPR-38500)

* Unterstützung zum Abrufen von Antwortheadern im Nachbearbeitungsprogramm des Formulardatenmodells für REST-Endpunkte hinzugefügt. (NPR-38275)

* Beim Generieren einer Übersetzungsdatei für ein adaptives Formular ist nun dieselbe Textsequenz wie die generierte XLIFF-Datei mit der Komponentensequenz im entsprechenden adaptiven Formular identisch. (NPR-37700)

* Wenn Sie ein adaptives Formular lokalisieren und selbst eine kleine Änderung am Text der Basissprache vornehmen, fehlt die vollständige Übersetzung für alle anderen Sprachen. Das Problem wurde in [!DNL Experience Manager] 6.5.13.0. (NPR-37189)

* Verbesserungen der Barrierefreiheit für Forms:

   * Neue Unterstützung für Bildschirmlesehilfen zur Erkennung von Kopf- und Textkörper einer Tabelle als Fortsetzung und verbundene Entitäten. Dadurch wird Bildschirmlesehilfen die korrekte Navigation in den Tabellen erleichtert. (NPR-37139)
   * Bildschirmlesehilfen können jetzt die Navigation in HTML Workspace beenden, bis ein Dialogfeld geöffnet ist. (NPR-37134)
   * Es wurde die Möglichkeit hinzugefügt, in Forms Designer &quot;Reader für Hyperlinks&quot;festzulegen.(NPR-36221)

Die folgenden Fehlerbehebungen, Schlüsselfunktionen und Verbesserungen wurden in [!DNL Experience Manager] 6.5.13.0:

<!-- The following issues are fixed in [!DNL Experience Manager] 6.5.13.0: -->

## [!DNL Assets] {#assets-6513}

* Beim Versuch, ein schreibgeschütztes Dropdown-Feld zu bearbeiten, wird der Dropdown-Wert auf &quot;leer&quot;zurückgesetzt. (NPR-38389)
* Der Benutzer kann ein Video-Asset (.mp4) nicht erfassen, wenn die Videodatei kein Audio enthält. Der Workflow &quot;DAM-Update-Asset&quot;schlägt fehl und spiegelt eine Fehlermeldung wider. (NPR-38116)
* Wenn Sie den Assistenten zum Verschieben von Assets verwenden, um einen Ordner mit Assets zu verschieben, schlägt der Workflow fehl und spiegelt eine Fehlermeldung wider. (NPR-38061)
* Fehlschlagen des FFmpeg-Transkodierungs-Workflows für das FLV-Videoprofil. (CQ-4343249)
* Nach der Aktualisierung auf [!DNL Experience Manager] 6.5 SP10 funktioniert der Asset-Metadaten-Editor nicht ordnungsgemäß. (CQ-4341359)
* Beim Öffnen einer Smart-Sammlung, die mit dem Suchfilter &quot;Veröffentlichen&quot;gespeichert wird, ändert sich der Suchfilter automatisch in Veröffentlichung rückgängig machen. (CQ-4341191)
* Beim Wechseln der Sprache in **[!UICONTROL Benutzerpräferenz]**, den Titel **[!UICONTROL Sortieren nach]**, Dropdown-Schaltfläche und andere Optionen in den Sortieroptionen auf der Asset-Startseite werden nicht in der ausgewählten Sprache angezeigt. (CQ-4339306)
* Beim Hinzufügen einer Regel zu einem Dropdown-Feld in **[!UICONTROL Metadatenschema]**, die **[!UICONTROL Abhängig von]** Die Liste spiegelt nicht die Feldbezeichnung der Dropdown-Liste wider. (ASSETS-9442)
* Dropdown-Liste Assets-Metadaten deaktiviert, Werte werden nicht beibehalten. (ASSETS-8918)
* Beim Anzeigen des Assets mit **[!UICONTROL Weitere Details]** Option in **[!UICONTROL Spalte]** -Ansicht werden falsche Anmerkungen angezeigt. (ASSETS-8851)
* Beim Erstellen eines doppelten Assets mit einer anderen Version werden die Ausgabedarstellungen nicht generiert. (ASSETS-8607)

* Ein Benutzer ohne Administratorrechte kann ein Asset veröffentlichen, das bereits von einem anderen Benutzer ausgecheckt wurde. (NPR-38128)
* Der Dimensional-Viewer funktioniert nicht in Chrome 97. (CQ-4340456)
* Die Schaltfläche zum Herunterladen von Assets zeigt auf der Seite &quot;Asset-Details&quot;das vollständige Menü nicht an. (CQ-4336703)
* Bei Verwendung von Linkfreigabe werden einige Zeichenfolgen im Fenster zur Linkfreigabe nicht lokalisiert. (CQ-4330540)
* Beim Hinzufügen von Elementen in &quot;Veröffentlichung verwalten&quot;wird die Zeichenfolge, die die Anzahl der ausgewählten Elemente widerspiegelt, nicht lokalisiert. (CQ-4330491)

### [!DNL Dynamic Media] {#dynamic-media-6513}

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Zero day exploit with the Java™ Spring Core Framework (CVE-2022-22963) impacting Experience Manager 6.5.12. (ASSETS-9031) -->
* Token-basierte sichere Vorschau für Dynamic Media-Assets in AEM-Autoren. (ASSETS-4995)
* Beim Erstellen einer Bildvorgabe für Dynamic Media in [!DNL Experience Manager]festgelegt ist, ist das zulässige Maximum in der Benutzeroberfläche auf 2000 x 2000 Pixel begrenzt. Wenn der Wert für Breite oder Höhe auf 2001 Pixel erhöht wird, wird die **[!UICONTROL Speichern]** -Schaltfläche deaktiviert ist. (ASSETS-5691)
* Benutzer können verhindern, dass bestimmte Dateiformate in Dynamic Media hochgeladen werden. (ASSETS-5693)
* Barrierefreiheit - Sehbehinderte Benutzer, die auf Bildschirmlesehilfen angewiesen sind, werden beeinträchtigt, wenn das Alt-Attribut nicht auf der Benutzeroberfläche &quot;Bildvorgaben&quot;für ein Bild implementiert ist. (ASSETS-9817)
* Barrierefreiheit - Bildschirmlesehilfen sind betroffen, da Bildschirmlesehilfen nicht gekennzeichnete Bilder für die Bilder darstellen, die im &quot;Timeline-Segment&quot;und auf der Registerkarte &quot;Aktionen&quot;vorhanden sind, wenn sie im Abwärtspfeilmodus zu navigieren. (ASSETS-5651)
* Barrierefreiheit - Bildschirmlesehilfen werden dadurch beeinträchtigt, dass Bildschirmlesehilfen (NVDA/JAWS) den beschreibenden Namen (E-Mail senden) für die Schaltfläche &quot;E-Mail senden&quot;im Dialogfeld &quot;E-Mail-Link&quot;im Video-Player nicht vorlesen, während sie mit dem Modus (Durchsuchen/Cursor) navigieren. (ASSETS-5641)
* Barrierefreiheit - Der Tastaturfokus wird nicht auf die Schaltfläche &quot;Wiederherstellen&quot;verschoben, die nach dem Aufrufen der Schaltfläche &quot;Rückgängig&quot;im Bildset-Editor angezeigt wird, während Sie mit der TAB-Taste auf der Tastatur navigieren. (ASSETS-5582)
* Barrierefreiheit - Benutzer, die auf Bildschirmlesehilfen angewiesen sind, werden beeinträchtigt, da das Alt-Attribut für ein Bildset-Bild, das unter der Überschrift Eigenschaften vorhanden ist, nicht bereitgestellt wird. (ASSETS-5576)
* Barrierefreiheit - Bildschirmlesehilfen erzählen nicht die Überschriftenrolle für `Cannot save this set` Text im `Cannot save this set` Warnhinweis beim Navigieren mit der Tastenkombination &quot;Überschrift&quot; `H`und die Nach-unten-Taste. (ASSETS-5569)
* Barrierefreiheit - Benutzer, die auf Bildschirmlesehilfen angewiesen sind, werden beim Navigieren durch die Formulare beeinträchtigt. Sie haben Schwierigkeiten, die Informationen zu den Formularsteuerelementen zu verstehen, wenn NVDA die Beschriftungsinformationen für die Steuerelemente &quot;Breite und Höhe&quot;nicht liest. Diese Steuerelemente sind unter der Kopfzeile des responsiven Bild-Zuschnitts während der Navigation im NVDA-Formularmodus &quot;F&quot;vorhanden. (ASSETS-5393)
* Nachdem Sie eine Dynamic Media-Komponente auf einer Site hinzugefügt haben und nachdem Sie die Seite veröffentlicht haben, ist das neu hinzugefügte Dynamic Media-Asset nicht auf der veröffentlichten Seite sichtbar und auch nicht auf der Vorschauseite sichtbar. Dieses Problem trat sowohl bei Bild- als auch bei Video-Asset-Typen auf. (ASSETS-9467)

## Commerce  {#commerce-6513}

* &quot;everyone&quot;hat jcr:write für `/content/usergenerated/etc/commerce/smartlists`. (NPR-35230)
* Die lokale Sortierung von Commerce-Produkten funktioniert nicht mehr. (CQ-4343750)
* Nach dem Ändern von Eigenschaften kann ein Produkt nicht in der Suchergebnisseite veröffentlicht werden. (CQ-4343318)

## CRX {#crx-6513}

* Ein Paket kann nicht heruntergeladen werden, wenn es das Sonderzeichen enthält `+` im Paketnamen. (NPR-38102)

## [!DNL Forms] {#forms-65130}

<!-- * When you use the prefill service to fill an adaptive form that contains a fragment and the fragment contains a Text box that supports rich text, the form fails to submit, and the following error occurs:

  `[AF] [AEM-AF-901-004]: Encountered an internal error while submitting the form.` (NPR-38542) -->

* Die Komponenten &quot;Radio&quot;, &quot;Checkbox&quot;und &quot;File Upload&quot;werden nicht korrekt von der deutschen Sprache in die englische Sprache übersetzt. (NPR-38527)
* Die PDF417-Barcode-Kodierung, erstellt von [!DNL Experience Manager] Forms ist für eine Optionsfeldgruppe ungültig. (NPR-38525)
* Beim Senden eines adaptiven Formulars tritt der folgende Fehler auf.
   `WARN [10.172.114.236 [1650871578492] POST /lc/content/forms/af/public/DHS-3754-ENG/jcr:content/guideContainer.af.internalsubmit.jsp HTTP/1.1] com.adobe.aemds.guide.internal.impl.utils.SubmitDataCollector TemplateKey not found in merge json:cq:responsive` (NPR-38520)
* Die Option Ausgeblendete Felder aus Datensatzdokument ausschließen funktioniert nicht. (NPR-38512)
* Nachdem Sie eine Forms-Container-Komponente zu einer Sites-Seite hinzugefügt haben, können Benutzer nicht zu einer anderen Sites-Seite navigieren, und die Sites-Seite hängt gelegentlich. Das Problem tritt gelegentlich auf. (NPR-38506)
* Benutzer erleben überlappenden Text in Adaptive Forms nach der Anwendung [!DNL Experience Manager] 6.5 Service Pack 11. (NPR-38376, CQ-4342472)
* Benutzer stoßen beim Verschieben adaptiver Formularbedienfelder in ein neues responsives Layout auf eine Ausnahme. (NPR-38369)
* Die Unterstützung von ECMASCRIPT 6 (ES6) ist für die Client-Bibliothek nicht aktiviert ` /libs/fd/expeditor/clientlibs/view`. (NPR-38358)
* Wenn Sie eine [!DNL Experience Manager] Workflow zum Senden einer E-Mail in hebräischer Sprache enthält die am Ende des Benutzers erhaltene E-Mail Fragezeichen (??) anstelle des hebräischen Sprachtexts (NPR-38296).
* Benutzer werden zufällig von [!DNL Experience Manager] Veröffentlichungsinstanzen und ein adaptives Formular können nicht gesendet werden. Das Problem wird in [!DNL Experience Manager] Instanzen, die den Dispatcher verwenden. (NPR-38285)
* Wenn Sie die Option getFormDataString in der Regel eines Adobe Launch verwenden, um die adaptiven Formulardaten zu erfassen, gibt die Option keine adaptiven Forms-Daten zurück. (NPR-38283)
* [!DNL Experience Manager] 6.5 Die nicht mehr unterstützte Java.acl.Group-API von Forms und die folgenden Fehlermeldungen werden in der Datei error.log angezeigt:
   ` *WARN* [default task-36] org.apache.jackrabbit.oak.spi.security.principal.AclGroupDeprecation use of deprecated java.acl.Group-related API - this method is going to be removed in future Oak releases - see OAK-7358 for details` (NPR-38282)
* Forms, das in deutscher Sprache erstellt wurde, kann nicht ins Englische oder in eine andere Sprache übersetzen. (NPR-38280)
* Wenn Sie eine lokalisierte Version eines adaptiven Formulars verwenden, wird das entsprechende Datensatzdokument (DoR) nicht lokalisiert. (NPR-38235)
* Wenn Sie den Schritt E-Mail senden verwenden, um einen Anhang zusammen mit einer E-Mail zu senden, behält der Anhang den im Schritt Workflow angegebenen Namen nicht bei. (NPR-38216)
* Wenn eine neue Version des Briefs veröffentlicht wird, können Benutzer den Briefentwurf für frühere Versionen der Briefe nicht öffnen. (NPR-38215, CQ-4342515)
* Beim Aufrufen einer SOAP-Endpunkt-Dienstmethode des AEM Forms JEE-Dienstes auf einem Schaltflächenklick, der als Regel für adaptives Formular konfiguriert wurde, schlägt der SOAP-Dienst mit der folgenden Ausnahme fehl:
   `ERROR* [0:0:0:0:0:0:0:1 [1624362360493] POST /content/forms/af/testsoapwsdl/jcr:content/guideContainer.af.dermis HTTP/1.1] com.adobe.aemds.guide.addon expeditor.servlet.ExpEditorServiceManager Error while making web service related call java.lang.Exception: createSOAPParam: JSONException`
* Bei Verwendung von com.adobe.fd.pdfutility.services.PDFUtilityService#convertPDFtoXDP zum Konvertieren einer PDF in das XDP-Format wird eine ungültige XDP-Datei zurückgegeben. (NPR-38140, CQ-4342099)
* Wenn mehrere Benutzer Correspondence Management verwenden, um verschiedene Briefe zu generieren, wird einigen Benutzern bei der Vorschau ein falscher Brief angezeigt. (NPR-38134)
* Die in die SITES-Seite eingebettete AEM Forms-Komponente verwendet das Breitenattribut, das den Wert in % aufweist und gemäß W3C-HTML-Validierung ungültig ist. Bei der HTML-Validierung tritt ein falscher Parsing-Fehler auf. (NPR-38124)
* Optionsfeld- und Kontrollkästchen-Elemente für die meisten OOTB-Designs in adaptiven Formularen sind nicht Teil der Tab-Reihenfolge (NPR-38108)
* Wenn ein Benutzer beim Ausführen eines Workflows dem Kommentarabschnitt HTML-Tags hinzufügt, werden die HTML-Tags gerendert. (NPR-37591)
* Beim Importieren und Veröffentlichen eines Briefs, der eine neue XDP-Datei enthält, schlagen die Briefe in der Veröffentlichungsinstanz fehl. Wenn die Briefe jedoch ein zweites Mal mit derselben CMP-Datei importiert und veröffentlicht werden, werden die Briefe erfolgreich in der Vorschau angezeigt. (CQ-4343599)
* Ein Formular mit der Eigenschaft &quot;Prepare data process&quot;kann in HTML Workspace nicht gerendert werden. (CQ-4343294)
* Bei statischen PDF forms, die mit Forms 6.5 Designer erstellt wurden, schlägt die PDF-Barrierefreiheit mit einem Fehler fehl `Tab order entry in page with annotations not set to "S"`. (CQ-4343117)
* Es ist nicht möglich, ein Bild mithilfe des PDFG-Dienstes mit OCR in eine PDF zu konvertieren, nachdem der AEMForms-6.5.0-0038-Patch (log4jv2.16) angewendet wurde. (CQ-4342450)
* Für den Barcode SSCC-18 wird ein falscher Wert angezeigt. Auf Forms-Servern wird der Wert im rechten Teil des Barcodes weggelassen. (CQ-4342400)
* Eine Microsoft® Word-Datei kann nicht in Forms Designer importiert werden. Benutzer stößt auf Fehler `Word (version XP or onwards) could not be found on the machine`. (CQ-4342146)
* Wenn Sie in Forms 6.5 Designer ein mit Forms 6.1 Designer erstelltes Formular öffnen und ein Textfeld bearbeiten, überschreitet der Absatzabstand den angegebenen Platz. Alle vorherigen Einstellungen des Bereichs werden entfernt und eine manuelle Neuformatierung des Textfelds ist erforderlich. (CQ-4341899)
* Der Benutzer kann die benutzerdefinierte Zeit in der Zeitplanung für die Auftragsbereinigung nicht festlegen. (CQ-4339192)
* Der Benutzer kann keine Konfiguration in der Benutzeroberfläche für die Endpunktverwaltung aktualisieren und tritt auf einen Fehler ` Uncaught ReferenceError: updateEndpoint_required is not defined`. (CQ-4331523)
* Bei ungültigen Tags funktioniert die ordnungsgemäße Verarbeitung der Fehlermeldung nicht erwartungsgemäß. (NPR-38106 und CQ-4337173)

>[!NOTE]
>
>* [!DNL Experience Manager Forms] veröffentlicht die Add-on-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.


## Granite {#granite-6513}

* Omnisearch gibt das Ergebnis für Benutzer ohne Leserechte zurück. (NPR-38373)
* Aktivieren Sie ES6 für `/libs/granite/configurations/clientlibs/confbrowser`. (NPR-38300)

## Integrationen {#integrations-6513}

* Leak of resource resolver sessions on Test and Target service from deprecated UserInfoServlet. (NPR-38112)

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * AEM‑OP‑13 ‑ HTTP Parameter Pollution in `com.day.cq.searchpromote.impl.servlet`. (NPR-38033) -->
<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Analytics 2.0 IMS support added to Experience Manager 6.5. (NPR-37914) -->

## Oak - Indizierung und Abfragen {#oak-6513}

* Die Oak-Version für 6.5.13.0 wurde auf Version 1.22.11 aktualisiert. (NPR-38084) -->

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Create a CFP based on latest 6.5.12 and update Oak-related bundle versions. (NPR-38144) -->

## Plattform {#platform-6513}

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * RTC : Universal XSS through cq-rewriter HtmlParser. (NPR-38064) -->
* Upgrade der Abhängigkeit von `org.apache.httpcomponents.httpclient` in [!DNL Experience Manager] 6.5. (NPR-37999)
* Hohe Autorenlast aufgrund von Pfadfeldvorschlägen. (CQ-4341826)
* Benutzer müssen die Seite aktualisieren, wenn sie das Projekt von der Kartenansicht in die Kalenderansicht ändern. (CQ-4340368)
* Tags gehen aufgrund von Berechtigungsbeschränkungen verloren. (CQ-4339543)
* Mehrere Probleme, die mit der Suche und dem Filter in der Pfadauswahl gemeldet wurden, funktionieren nicht. (CQ-4339402)
* Beenden Sie die Verwendung von DTM in 6.5 - wechseln Sie zu Launch für Omega Instrumentation und fügen Sie Gainsight-Unterstützung hinzu. (CQ-4337809)
* Beschränken Sie die Suchfunktion der pathfield-Komponente auf der Grundlage der festgelegten Filtereigenschaft für das Pfadfeld. (CQ-4309556)
* [!DNL Experience Manager] Plattform 6.5: Fehlerkorrekturen für die chinesische Gebietsschema-Benennung. (CQ-4308978)
* Wechseln Sie für Omega-Instrumentation zu Launch . (NPR-38377)
* [!DNL Experience Manager] Plattform 6.5: Fehlerkorrekturen für die chinesische Gebietsschema-Benennung. (CQ-4308978)

## Replikation {#replication-6513}

* Veröffentlichen des Benutzerknotens, der vom Autor an den Herausgeber fehlschlägt. (NPR-38005)

## [!DNL Sites] {#sites-6513}

### Admin {#sites-admin-6513}

* Mit SP 12 eingeführte Regression korrigiert, die beim Verschieben von Seiten möglicherweise ein Problem verursacht hat. (SITES-5298)

### Klassische Benutzeroberfläche {#sites-classicui-6513}

* RTE: Das aktualisierte Bild ist nicht sichtbar, wenn ein neues Bild auf ein vorhandenes Bild gezogen wird. (NPR-38141)

<!-- version 2 of description above * Updated Image is not visible When a new image is dragged on top of an existing image the updated image is not visible in RTE - Classic UI. (NPR-38141) -->

### Inhaltsfragmente {#sites-contentfragments-6513}

* Unterstützung der Erstellung von Inhaltsfragmentmodellen in Unterkonfigurationen. (NPR-38054)

<!-- version 2 of description above * The Configuration Manager now allows you to set the Content Fragment Model config on a sub-config folder. (NPR-38054) -->
* Verbessern Sie die Leistung bei Verwendung der Validierung &quot;Eindeutiges Feld&quot;im Inhaltsfragmentmodell. (NPR-38142)

<!-- version 2 of description above * The unique field validation query is now fixed. (NPR-38142) -->
* Verbessern Sie die Antwortzeit beim Öffnen des Inhaltsfragmentmodell-Editors. Kunden mit zahlreichen Fragmenten in Assets haben beim Öffnen möglicherweise Fehler gesehen. (SITES-6284)

<!-- version 2 of description above * If the customer is trying to access the editor of the content fragment models, they get a query error because of too many fragments on the dam. (SITES-6284) -->
* Bei der Aktualisierung von 6.5.11 auf 6.5.12 wurde eine Regression korrigiert, die möglicherweise Fehler im Inhaltsfragmentmodell-Editor verursacht hat. (SITES-5088 und SITES-4967)

<!-- version 2 of description above * Paths were getting deleted when AEM 6.5.12.0 was installed on existing 6.5.11.0 instance. (SITES-5088)
* Apple 6.5.10 system crashing when using CF model editor, due to erroneous feature toggle check. (SITES-4967) -->
* Verbessern Sie die Lokalisierung der Benutzeroberfläche des Inhaltsfragmentmodell-Editors. (NPR-38126)

<!-- version 2 of description above * Some strings in the Content Fragment Model editor are not localized. (NPR-38126) -->
* Es wurde ein Fehler behoben, der beim Schließen des Inhaltsfragment-Editors zu einem Fehler führen konnte, wenn der Autorenserver mit dem Dispatcher verwendet wurde. (NPR-38205)

<!-- version 2 of description above * Update of Content Fragment references is returning an invalid JSON response via Dispatcher. (NPR-38205) -->
* Es wurde ein Fehler behoben, der dazu führte, dass das Speichern eines Modells nicht möglich war, wenn die Validierung in einem RTE-Feld verwendet wurde. (NPR-38210)

<!--version 2 of description above * Content Fragment Model Rich Text Validation Prevents Blocks Saving a Content Fragment Model. (NPR-38210) -->
* Problem mit Inhaltsfragmenten, bei dem die boolesche Eigenschaft keinen Feldtext in &quot;title&quot;anzeigt, sondern &quot;Eigenschaftsname&quot;. (NPR-38244)
* Fehler beim Ausführen einer persistenten Abfrage mit einer Abfragevariablen über Postman. (NPR-38251, NPR-38057)
<!--version 2 of description above * An unexpected error message is coming in Postman, when executing the graphQL persisted query having query variables. (NPR-38251) -->
* Inhaltsfragment-Komponente: Die Regression in der Option &quot;Überschriften als Absätze behandeln&quot;wurde korrigiert und war 6.5 SP7. (NPR-38055)

<!--version 2 of description above * After applying SP11 to the Publish instance of AEM 6.5.6, the display result of the Content Fragment set in the published page changes. (NPR-38055) -->
* In Version 6.5.11 eingeführte Regression behoben, die zu Fehlern bei der Asset-Suche geführt haben konnte. (SITES-4784)

<!--version 2 of description above * Adapt external index package to use selection Policy (fragment versus asset index). (SITES-4784) -->
* Verwenden **[!UICONTROL Bearbeiten]** aus den Suchergebnissen eine `Not Found` Fehler. (NPR-37810)

<!--version 2 of description above * When editing Content Fragment from the Assets Search Rail results page, it throws 'Not Found' error. (NPR-37810) -->

### ContentHub {#sites-contenthub-6513}

* Die Benutzeroberflächenmodelle des ContextHub werden ohne eine Aktualisierung der Seite nicht ordnungsgemäß dargestellt. (NPR-38212)

### E-Mail-Editor {#sites-emaileditor-6513}

* Unterstützung für bevorstehende Version von E-Mail-Kernkomponenten aktivieren [https://github.com/adobe/aem-core-email-components](https://github.com/adobe/aem-core-email-components). (NPR-38445 und NPR-38204)

<!-- version 2 of description above * Allow new email templated under campaign and ambit. (NPR-38445) * The "Approve for Adobe Campaign" workflow was only running for pages which are of type or extending the resource types: "mcm/neolane/components/newsletter", "mcm/campaign/components/newsletter" and "mcm/campaign/components/campaign_newsletterpage". (NPR-38204) -->

### Experience Fragments  {#sites-experiencefragments-6513}

* Wenn Sie die Aktion &quot;Zur Seite navigieren&quot;in den Verweisen für ein Experience Fragment verwenden, wird die falsche Seite geöffnet. (NPR-38062)
* Layout-Eigenschaften, die von einer XF-Vorlage stammen, werden nicht innerhalb einer Seite angezeigt. (NPR-38214)
* Verbesserte Leistung bei der XF-Referenzberechnung. (NPR-38269)

<!-- version 2 of description above * Job queue configuration is incorrect - The OSGi configuration for the reference updater job queue has not been ported back to 6.5. This issue leads to jobs being run in the main queue, which has a higher priority and allows more jobs to run in parallel. This flow can lead to CPU exhaustion. (NPR-38269) -->

### Seiteneditor {#sites-pageeditor-6513}

* Verbessern Sie die Rückgängigmachung für Komponenten, die nicht über die Funktion inlineEditing oder dropTarget verfügen in `cq:editConfig`. (NPR-38361)

<!-- version 2 of the description above * When out of the box components that don't have inlineEditing or dropTarget feature in the _cq_editConfig file (navigation, breadcrumb, embed) are deleted > undeleted (by way of Undo), all configurations are lost and empty placeholder reappears. Component must be reconfigured from scratch. (NPR-38361) -->
* Die Dropdown-Liste &quot;Stilsystem&quot;wurde möglicherweise oben auf der Seite platziert und nicht im Kontext der Komponente - für Komponenten, die `cq:editConfig` &quot;afteredit: REFRESH_PAGE&quot;. Dieses Problem wurde nun behoben. (NPR-38384)

<!-- version 2 of description above* When selecting a style option on a component, the Styles box shifts to the upper left corner of the screen, rather than staying put below the style icon. Happens for components that have  cq:editConfig “afteredit: REFRESH_PAGE”. (NPR-38384) -->
* Die Textkomponente ist beim Hinzufügen zu verschachtelten Layout-Containern falsch ausgerichtet. (NPR-38193)
* Es wurde eine leere Stilregisterkarte angezeigt, wenn keine Stilsystemkonfiguration für eine Komponente vorhanden war. Die Registerkarte ist jetzt ausgeblendet, wenn keine Konfiguration vorhanden ist. (NPR-38218)
<!-- version 2 of description above * Style tab is blank on components without styles/policies. (NPR-38218) -->
* Die Eigenschaft `useLegacyResponsiveBehaviour` funktioniert nur bei der Authentifizierung. (NPR-37996)
* Die Aktualisierung von jquery-ui auf die neueste Version führte dazu, dass der Editor fehlschlug. (SITES-5647)

### Sicherheit {#sites-security-6513}

* In der Benutzeroberfläche &quot;Benutzergruppenverwaltung&quot;konnten Benutzer manchmal nicht entfernt werden, insbesondere in Gruppen mit +20 Benutzern. (NPR-38041)

<!--version 2 of description above * Cannot remove users from user groups. (NPR-38041) -->

### SEO {#sites-seo-6513}

* Sitemap Generator und Canonical-Tag unterstützen URLs ohne HTML-Code. (CIF-2647)
* Fügen Sie Unterstützung für das Entfernen alternativer Sprachen mithilfe der noindex-Konfiguration hinzu. (CIF-2496)
* Fügen Sie Unterstützung hinzu, um eine benutzerdefinierte URL bereitzustellen, um die standardmäßige kanonische URL für Seiten mit nahezu identischem Inhalt zu überschreiben. (CIF-2747)

### SPA Editor und SDK {#sites-spa-sdk-6513}

* Ab Version 6.5.13 müssen Sie den Container-Komponentenknoten nicht mehr in JCR erstellen, bevor Sie Änderungen über den SPA Editor vornehmen. A `virtual container` wird erstellt, bevor sie über das SDK gespeichert wird. (SITES-5762)

<!-- version 2 of description above * Virtual container support - Adding a child component to a virtual container that is not yet present in the database implies the creation of a node to represent the container in content structure. (SITES-5762) -->

### Vorlageneditor {#sites-templateeditor-6513}

* Regression behoben, dass beim Veröffentlichen einer geänderten Vorlage nicht alle Abhängigkeiten veröffentlicht wurden. (NPR-38274)

<!-- version 2 of description above * Template changes do not get published until you publish a page that uses that template. (NPR-38274) -->
* TemplatedResource valueMap sollte tiefgehende Lesevorgänge gemäß der ValueMap-API zulassen. (NPR-38439)

## Sling {#sling-6513}

<!-- OBSOLETE BASED ON CQDOC-19400 * Memory leak in `DiscoveryLiteDescriptor`. (NPR-38288) -->
* Aktualisieren `sling-javax.activation` Bundle mit Fehlerbehebung von SLING-8777. (NPR-38077)

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Security issues reported under `org.apache.sling.scripting.jst`. (NPR-38067) -->

## Übersetzungsprojekte {#translation-6513}

* Mehrere Launches werden für referenzierte Seiten/xf erstellt. (NPR-38263)
* Das Verhalten beim Hinzufügen von Seiten zu Übersetzungsprojekten seit Service Pack 10 wurde geändert. Das Übersetzungsprojekt enthält keine neu erstellte Seite [z. B.: test-page-women-2] in der Liste, wenn das übergeordnete Element der neu erstellten Seite ausgewählt wurde [nicht direkt die neu erstellte Seite]. (NPR-38256)
* Hinzufügen `cq:isTranslationLaunch` -Eigenschaft in vom Übersetzungsprojekt erstellten Launches. (NPR-38224)
* Launch wird für eine Seite erstellt, auf der ein referenziertes XF vorhanden ist, das ein Asset enthält. (NPR-38199)
* [!DNL Experience Manager] Aktualisierung des Translation Memory funktioniert nicht. (NPR-38196)
* Aktivieren Sie ES6 für `/libs/cq/gui/components/projects/admin/translation/job/addcontent/clientlibs.js`. (NPR-38306)
* Neuestes 18n-Paket für Übersetzungen für [!DNL Experience Manager] 6.5. (CQ-4339505)

## Benutzeroberfläche {#ui-6513}

* Wenn Sie sich auf der Startseite befinden > Abschnitt &quot;Tools&quot;und klicken Sie auf [!DNL Experience Manager] das Symbol [!DNL Experience Manager] Der Navigationsbildschirm sollte angezeigt werden. (NPR-38417)
* Aktivieren Sie ES6 für `/libs/granite/ui/references/clientlibs/coral/references`. (NPR-38303)
* Aktivieren Sie ES6 für `/libs/granite/datavisualization/clientlibs/d3-3.x`. (NPR-38302)

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * AEM‑OP‑09 ‑ Persistent cross‑site scripting selecting paths in templates. (NPR-38301) -->
* Die Datumsauswahl in der Touch-Benutzeroberfläche wird auf Koreanisch angezeigt. (NPR-38079)
* Bearbeitungsdialogfeld mit mehreren Feldern bei der Neuanordnung der Felder, die den Auswahlwert für die Optionsfelder verlieren. (NPR-38063)

## WCM {#wcm-6513}

* [!DNL Experience Manager] MCM (Campaign) 6.5: Fehlerkorrekturen für die chinesische Gebietsschema-Benennung. (CQ-4308973)
* Unclosed ResourceResolver in com.day.cq.wcm.workflow.impl.WcmWorkflowServiceImpl.autoSubmitPageAfterModification (NPR-38286)

## Installieren [!DNL Experience Manager] 6,5,13,0 {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback -->

* [!DNL Experience Manager] 6.5.13.0 erfordert [!DNL Experience Manager] 6.5. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen.
* Der Service Pack-Download ist auf Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen [!DNL Experience Manager] 6.5.13.0 auf einer der Autoreninstanzen, die Package Manager verwenden.

>[!NOTE]
>
>Adobe rät davon ab, die [!DNL Experience Manager] 6.5.13.0-Paket.

### Installieren Sie das Service Pack auf [!DNL Experience Manager] 6,5 {#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager] -Instanz.

1. Laden Sie das Service Pack herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.13.0.zip).

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. Normalerweise tritt dieses Problem in [!DNL Safari] -Browser, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie automatisch installieren können [!DNL Experience Manager] 6.5.13.0.

* Platzieren Sie das Paket in `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwendung `cmd=install&recursive=true` damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>[!DNL Experience Manager] 6.5.13.0 unterstützt keine Installation von Bootstraps.

**Installation überprüfen**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in der [technische Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge an `Adobe Experience Manager (6.5.13.0)` under [!UICONTROL Installierte Produkte].

1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).


### Installieren [!DNL Experience Manager] Forms Add-On-Paket {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen, wenn Sie [!DNL Experience Manager] Forms. Fehlerbehebungen in [!DNL Experience Manager] Forms wird eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Service Pack-Version.

1. Stellen Sie sicher, dass Sie die [!DNL Experience Manager] Service Pack.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-On-Paket wie unter [Installieren von Add-On-Paketen für AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).
1. Wenn Sie Briefe in Experience Manager 6.5 Forms verwenden, installieren Sie die [neuestes AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates).

### Installieren [!DNL Experience Manager] Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in [!DNL Experience Manager] Forms on JEE wird über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für [!DNL Experience Manager] Informationen zur Konfiguration von Forms on JEE und nach der Bereitstellung finden Sie unter [Versionshinweise](jee-patch-installer-65.md).

>[!NOTE]
>
>Nach der Installation des kumulativen Installationsprogramms für [!DNL Experience Manager] Forms on JEE, installieren Sie das neueste Add-On-Paket für Forms, löschen Sie das Add-On-Paket für Forms aus dem `crx-repository\install` und starten Sie den Server neu.

### UberJar {#uber-jar}

Das UberJar für [!DNL Experience Manager] 6.5.13.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.13/)(https://).

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.13</version>
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
| Integrationen | Die **[!UICONTROL AEM Cloud Services-Opt-in]** Der Bildschirm wird nicht mehr unterstützt, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration aktualisiert in [!DNL Experience Manager] 6.5. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O]. Es unterstützt die wachsende Rolle von Adobe Launch bei der Instrumentierung [!DNL Experience Manager] Seiten für Analysen und Personalisierung verwenden, ist der Opt-in-Assistent funktionell irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O] Integrationen über die entsprechenden [!DNL Experience Manager] Cloud-Services. |
| Connectoren | Der Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird nicht mehr unterstützt für [!DNL Experience Manager] 6.5. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THE LIST.
 -->

<!-- VULNERABILITY ISSUE - REMOVED MAY 23, 2022 AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * If you are using Content Fragments and GraphQL, Adobe recommends that you install the following packages on top of 6.5.12.0:

  * [AEM 6.5.12 Sites HotFix-NPR-38144](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Faem-service-pkg-6.5.12.0-NPR-38144-B0002.zip) (this hot fix replaces SP12, but can be installed on top of SP12) -->

* [AEM Inhaltsfragment mit GraphQL-Indexpaket 1.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.3.zip)

* As [!DNL Microsoft® Windows Server 2019] unterstützt nicht [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] unterstützt keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie ein Upgrade [!DNL Experience Manager] -Instanz von 6.5 bis 6.5.10.0, können Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5, die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] und veröffentlichen Sie einen verschachtelten Ordner in [!DNL Brand Portal]. Der Titel des Ordners wird jedoch nicht aktualisiert in [!DNL Brand Portal] bis die Veröffentlichung des Stammordners erfolgt ist.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wenn die Adobe Target-Integration in [!DNL Experience Manager] über die Target Standard-API (IMS-Authentifizierung) und dann über den Export von Experience Fragments in Target werden falsche Angebotstypen erstellt. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

* Beim Versuch, Inhaltsfragmente oder Sites/Seiten zu verschieben/zu löschen/zu veröffentlichen, tritt ein Problem beim Abrufen von Inhaltsfragmentverweisen auf, da die Hintergrundabfrage fehlschlägt. d. h. die Funktionalität funktioniert nicht.
Um den korrekten Vorgang sicherzustellen, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten hinzufügen `/oak:index/damAssetLucene` (Eine Neuindizierung ist nicht erforderlich):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die in [!DNL Experience Manager] 6.5.13.0:

* [Liste der in Experience Manager 6.5.13.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65130_bundles.txt)

* [Liste der in Experience Manager 6.5.13.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65130_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Support für Adobe kontaktieren](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

