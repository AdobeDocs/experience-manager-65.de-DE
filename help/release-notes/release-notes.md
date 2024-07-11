---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: a52311b9-ed7a-432e-8f35-d045c0d8ea4c
source-git-commit: fb689e86deaabcc4033ed75f615086b630a9a525
workflow-type: tm+mt
source-wordcount: '4332'
ht-degree: 95%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, November 30, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.21.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 6. Juni 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.21.0 enthalten ist {#what-is-included-in-aem-6521}

[!DNL Experience Manager] 6.5.21.0 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) für [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

<!-- * _6.5.21.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

### [!DNL Forms]

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* **Unterstützung für OAuth-Anmeldedaten**: Neue, benutzerfreundlichere Anmeldedaten für die Server-zu-Server-Authentifizierung, die den vorhandenen Anmeldedatentyp „Service-Konto (JWT)“ ersetzt. (NPR-41994)
* [Verbesserungen des Regeleditors in AEM Forms](/help/forms/using/rule-editor-core-components.md):
   * Unterstützung für die Implementierung verschachtelter Bedingungen mit `When-then-else`-Funktionalität.
   * Überprüfen oder Zurücksetzen von Panels und Formularen, einschließlich Feldern.
   * Unterstützung für moderne JavaScript-Funktionen wie Let- und Pfeilfunktionen (ES10-Unterstützung) innerhalb der benutzerdefinierten Funktionen.
* [AutoTag-API für PDF-Barrierefreiheit](/help/forms/using/aem-document-services-programmatically.md#doc-utility-services-doc-utility-services): AEM Forms auf OSGi unterstützt jetzt die neue AutoTag-API zur Verbesserung von PDFs entsprechend den Barrierefreiheitsstandards durch Hinzufügen von Tags: Absätze und Listen. Dadurch werden PDFs für Benutzende mit Hilfstechnologien leichter zugänglich.
* **16-Bit-PNG-Unterstützung**: Der ImageToPdf-Dienst von PDF Generator unterstützt jetzt die Konversion von PNGs mit einer 16-Bit-Farbtiefe.
* **Anwenden von Artefakten auf einzelne Textblöcke in XDPs**: Mit Forms Designer können Benutzende jetzt Einstellungen für einzelne Textblöcke in XDP-Dateien konfigurieren. Mit dieser Funktion können Sie die Elemente steuern, die in den resultierenden PDFs als Artefakte behandelt werden. Diese Elemente – wie Kopf- und Fußzeilen – werden für Hilfstechnologien verfügbar gemacht. Zu den Hauptfunktionen gehören das Markieren von Textbausteinen als Artefakte und das Einbetten dieser Einstellungen in die XDP-Metadaten. Der Ausgabe-Service von Forms wendet diese Einstellungen während der PDF-Erstellung an und stellt dabei ein ordnungsgemäßes PDF/UA-Tagging sicher.
* **AEM Forms Designer ist nach dem Standard `GB18030:2022` zertifiziert**: Mit der Zertifizierung `GB18030:2022` unterstützt Forms Designer jetzt den chinesischen Unicode-Zeichensatz, was die Eingabe chinesischer Zeichen in alle bearbeitbaren Felder und Dialogfelder ermöglicht.
* [Unterstützung für WebToPDF-Route in JEE Server](/help/forms/using/admin-help/configure-service-settings.md#generate-pdf-service-settings-generate-pdf-service-settings) Die Verwendung des PDF Generator-Dienstes unterstützt jetzt die WebToPDF-Route zum Konvertieren von HTML-Dateien in PDF-Dokumente auf JEE, zusätzlich zu den bestehenden Webkit- und WebCapture-Routen (nur Windows). Während die WebToPDF-Route bereits auf OSGi verfügbar und auf JEE erweitert ist. Jetzt unterstützt der PDF Generator-Dienst auf JEE- und OSGi-Plattformen die folgenden Routen über verschiedene Betriebssysteme hinweg:
   * **Windows**: Webkit, WebCapture, WebToPDF
   * **Linux®**: Webkit, WebToPDF

### [!DNL Assets]

#### Verbesserungen

Im Folgenden finden Sie die Liste der Fehlerbehebungen in dieser Version.

* Die Registerkarte „IPTC“ bietet nun Unterstützung für die Textfelder [!UICONTROL Alternativtext] und [!UICONTROL Erweiterte Beschreibung]. (ASSETS-34918)

#### Fehlerbehebungen für die Barrierefreiheit

Im Folgenden finden Sie eine Liste der in dieser Version enthaltenen Fehlerbehebungen für die Barrierefreiheit:

* Wenn der Verarbeitungsstatus eines Assets „Fehlgeschlagen“ oder „Metadaten fehlgeschlagen“ lautet, funktioniert die Benutzeroberfläche „Untertitel und Audiospuren“ nicht ordnungsgemäß. (ASSETS-37281)
* Wenn Sie Asset-Metadaten speichern und bearbeiten möchten, wird die Sprachbezeichnung nicht angezeigt. (ASSETS-37281)

<!-- ### [!DNL Forms]
* A -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 21 {#fixed-issues}

### [!DNL Sites]{#sites-6521}

#### Barrierefreiheit {#sites-accessibility-6521}

* Die Beschriftung **[!UICONTROL Gespeicherte Suchen]** ist nicht persistent. Der Platzhalter wird als einzige visuelle Kennzeichnung für ein Textfeld verwendet. (SITES-3050)

#### Admin-Benutzeroberfläche{#sites-adminui-6521}

* Wenn Sie auf **[!UICONTROL Sites]** > **[!UICONTROL Kernkomponenten]** > **[!UICONTROL Eigenschaften]** > Registerkarte **[!UICONTROL Berechtigungen]** > **[!UICONTROL Effektive Berechtigungen]** klicken, wird das Dialogfeld **Effektive Berechtigungen** nicht geöffnet. (SITES-17378)

<!-- #### Classic UI{#sites-classicui-6521} 

* A -->

#### [!DNL Content Fragments]{#sites-contentfragments-6521}

* Die doppelte Einbeziehung der Formularelemente wurde korrigiert. (SITES-21109)
* Beim Erstellen eines Inhaltsfragments reagiert die Schaltfläche „Schließen“ manchmal nicht mehr. Die gesamte Seite friert dadurch ein und es ist eine Seitenaktualisierung erforderlich, um das Inhaltsfragment zu schließen. Was das Problem bei der Versionserstellung betrifft, erstellt das System eine neue Version eines Inhaltsfragments. Dieses Problem tritt auch dann auf, wenn die Benutzerin oder der Benutzer keine Änderungen vorgenommen, sondern einfach mit dem RTE oder einem Textfeld interagiert hat. (SITES-21187)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6521}

* Beim Upgrade von Adobe Experience Manager 6.5.19.0 auf 6.5.20.0 wurde der Pfad `/libs/cq/graphql/sites/graphiql` gelöscht. (SITES-20098)

<!-- #### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6521}

* W -->

<!-- #### [!DNL Content Fragments] - REST API{#sites-restapi-6521}

* W -->

<!-- #### Core Backend{#sites-core-backend-6521}

* W -->

<!-- #### Core Components{#sites-core-components-6521}

* I -->

<!-- #### Campaign integration{#sites-campaign-integration-6521}

* A -->

#### Experience Fragments{#sites-experiencefragments-6521}

* Beim Rollout von Experience Fragments von `masters/language` nach `country/language` werden keine Querverweise aktualisiert. (SITES-21172)
* Nicht nur die in `cq:allowedTemplates` angegebenen Vorlagen, sondern auch Vorlagen, bei denen `allowedPaths` auf Vorlagenebene konfiguriert ist, werden beim Erstellen eines neuen Experience Fragments als Optionen angezeigt. (SITES-20855)

<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6521}

* T -->

<!-- #### Launches{#sites-launches-6521} -->


<!-- ### [!DNL Forms]-->

<!-- DELETED MAY 22, 2024 FROM TOTAL RELEASE CANDIDATE ISSUES * The `sourceRootResource` configured in the Launch configuration within CRXDE Lite points to content that no longer exists, leading to a malfunction when attempts are made to delete launches. Delete launches even if the page is deleted or if the path is not the same. (SITES-20750) -->


#### MSM – Live Copies{#sites-msm-live-copies-6521}

* Die Seitenkomponente wird überlagert, um in den Seiteneigenschaften Registerkarten hinzuzufügen. In einem Fall handelt es sich dabei um die Seitenkonfiguration, die über eine Eigenschaft zum Hinzufügen einer Experience Fragment-URL verfügt. Der in den Seiteneigenschaften für das Experience Fragment konfigurierte Link ändert sich für keine Sprachkopien, die für diese Seite erstellt wurden. Der konfigurierte Link sollte sich mit der Sprachkopie-URL ändern. (SITES-19580)

#### Seiteneditor{#sites-pageeditor-6521}

* Im Bearbeitungsmodus wird ein grauer Hintergrund inkonsistent angewendet, was nicht den Farbkontraststandards der Leitlinien für die Barrierefreiheit von Web-Inhalten (Web Content Accessibility Guidelines, WCAG) entspricht. (SITES-20060)

### [!DNL Assets]{#assets-6521}

* Wenn ein Asset in Brand Portal veröffentlicht wird, bleibt der Veröffentlichungsstatus inkonsistent. (ASSETS-36807)
* Assets werden nicht gelöscht, wenn Sie sie mithilfe eines API-Aufrufs aus einer Instanz löschen. (ASSETS-35131)
* Wenn Sie versuchen, Metadaten zu importieren, werden eingefügte Zeichen in einer anderen Sprache als Englisch durch ein `question mark (?)` ersetzt.  (ASSETS-35091)
* Wenn die Eigenschaft `dc:title` mit einer Datentypzeichenfolge verwendet wird, funktioniert die Asset-Inhaltsstruktur nach der Service Pack 6.5.19-Installation nicht ordnungsgemäß. (ASSETS-34684)
* Wenn ein Asset-Name ein Sonderzeichen enthält, wird ein Fehler angezeigt. (ASSETS-33248)

#### [!DNL Dynamic Media]{#assets-dm-6521}

* In AEM 6.5.18 werden beim Bearbeiten von Hotspots nicht alle Hotspots angezeigt, die einem Asset hinzugefügt wurden. Alle Hotspots funktionieren allerdings in einem veröffentlichten Asset, können jedoch später im Bedarfsfall nicht mehr bearbeitet werden. (ASSETS-33609)
* Mit den neuesten EPS-Dateien, die hochgeladen werden, werden nach der erneuten Verarbeitung keine Miniaturansichten generiert. (ASSETS-32617)
* Unter „Tools“ > „Assets“ > „Veröffentlichungs-Setup für Dynamic Media“ > Registerkarte „Anfrage-Attribute“ sehen die Eingaben `Width(px)` und `Height(px)` in Spanisch, Italienisch und Portugiesisch anders aus. Sie sind hier nicht aufeinander abgestimmt. (ASSETS-31896)
* Seit dem 1. Mai 2024 unterstützt Adobe Dynamic Media Folgendes nicht mehr:
   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 und 1.1
   * Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

### [!DNL Forms]{#forms-6521}

#### [!DNL Adaptive Forms] {#forms-6520}

* Wenn ein adaptives Formular aus einer Adobe Experience Manager-Veröffentlichungsinstanz an einen Adobe Experience Manager-Workflow gesendet wird, können die Anlagen nicht vom Workflow gespeichert werden. (FORMS-14209)
* Wenn Benutzende auf OSGi im AEM Forms Service Pack 15 (6.5.15.0) auf die Schaltfläche **Als PDF drucken** klicken, schlägt die Client-seitige Validierung fehl. Dies wird durch die Fehlermeldungen im Fenster der Developer Tools Console deutlich. (FORMS-14029)
* Wenn Benutzende ein Formular mit dem AEM 6.5 Forms Service Pack 17 (6.5.17.0) oder Service Pack 18 (6.5.18.0) oder Service Pack 19 (6.5.19.0) senden, funktioniert die Übersetzung von „Vielen Dank“-Nachrichten nicht ordnungsgemäß. Die Nachrichten sind jedoch korrekt im Wörterbuch übersetzt. (FORMS-13846)
* Wenn Benutzende die Vorschau eines Formulars mit einer Komponente für die Datumsauswahl anzeigen, wird das Feld für die Datumsauswahl nicht richtig mit den anderen Formularfeldern ausgerichtet. (FORMS-13763)
* Wenn Benutzende in der Umgebung von AEM Forms Service Pack 19 (6.5.19.0) die API aufrufen, um Zahlen zu formatieren, werden die formatierten Zahlen nicht mit den entsprechenden Gebietsschemata abgestimmt. Daher werden die Währungszeichen nicht korrekt angezeigt. Das Problem bleibt unabhängig davon bestehen, ob der Gebietsschemaparameter auf „de_DE“ oder „en_US“ festgelegt ist. (FORMS-13759)
* Wenn Benutzende in der Umgebung von AEM Forms Service Pack 19 (6.5.19.0) 16-Bit-PNGs mithilfe des Img2Pdf PDFG-Dienstes in PDF konvertieren, schlägt dieser Vorgang fehl und der Dienst „Acrobat Image Conversion verwenden“ kann nicht verwendet werden. (FORMS-13754)
* Wenn Benutzende in AEM Forms Service Pack 19 (6.5.19.1) eine vorhandene JobOptions-Datei im Bereich „Dienste/PDF Generator/Adobe PDF-Einstellungen“ von adminui von AEM Forms JEE hochladen möchten, schlägt dies fehl. Außerdem wird die folgende Fehlermeldung angezeigt (FORMS-13597):
  `"An error has occurred while processing your request. Please use the breadcrumb links to navigate to another page."`
* Wenn Benutzende von AEM Forms Service Pack 15 (6.5.15.0) auf AEM Forms Service Pack (6.5.17.0) oder AEM Forms Service Pack (6.5.19.0) migrieren, wird der FD-Schlüssel dupliziert, wodurch die Formulare nicht richtig übersetzt werden. (FORMS-13461)
* Wenn Benutzende Dispatcher vor die Autoreninstanzen stellen, die von der Bereitstellungstopologie auf AMS unterstützt werden, hängt die Übermittlung von „Aufgabe zuweisen“ bzw. schlägt fehl. (FORMS-8010)
* Fehlerbehebungen zur Barrierefreiheit:
   * Auf die Symbole auf der Seite „formsanddocuments“ kann jetzt gemäß dem ANDI-Standard zugegriffen werden. (FORMS-13094)
   * Benutzende können über die Tastatur auf die Symbolleiste zugreifen, um Inhalte auf der Bearbeitungsseite zu speichern oder zu bearbeiten. Die Symbolleiste wird entsprechend dem ANDI-Standard erweitert. (FORMS-13102)
   * Auf die Formularfelder „Erforderlich“ bzw. „Obligatorisch“ kann gemäß dem ANDI-Standard zugegriffen werden. (FORMS-13097)

* Wenn Benutzende versuchen, ein Formular beim Laden der Seite anzuzeigen, schlägt das Rendern fehl. (FORMS-13594)
* Die Feldkomponente zur Datumseingabe funktioniert im Kompatibilitätsmodus mit Internet Explorer nicht ordnungsgemäß in Microsoft Edge. (FORMS-13170)
* Eine angehaltene E-Mail-Benachrichtigung mit Anhang konnte nicht gesendet werden, wenn die Fehlerbehebung für [Zusätzliche Schritte zum Abrufen von E-Mails mit Anhängen](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/troubleshooting/additional-steps-to-use-email-with-attachments) auf dem Server ausgeführt wurde. (FORMS-14227)
* Wenn Benutzende in AEM Forms Workspace in Service Pack 18 (6.5.18.0) Kommentare zu einem hochgeladenen Dokument senden, führt dies dazu, dass die Dokumentdatei beschädigt wird. (FORMS-13735)
* Wenn Benutzende versuchen, im seitlichen Bedienfeld nach einem adaptiven Formular zu suchen, schlägt die Suche in AEM Forms Service Pack 18 (6.5.18.0) und Service Pack 19 (6.5.19.0) und Service Pack 20 (6.5.20.0) fehl. (FORMS-14117)
* Wenn Benutzende ein Formular bearbeiten, das auf Deutsch erstellt und ins Englische übersetzt wurde, wird die Sprache zwischen den Modi „Vorschau“ und „Bearbeiten“ inkonsistent angezeigt. Dadurch werden die Komponenten „RadioButton“ und „Checkbox“ im Vorschaumodus korrekterweise auf Deutsch, im Bearbeitungsmodus jedoch auf Englisch angezeigt.  (FORMS-13910)
* Das Prozess-Tool „Prozess bereinigen“ schlägt mit dem Fehler `NoClassDefFoundError: org/omg/CORBA/UserException` fehl. (FORMS-13751)
* Wenn Benutzende versuchen, unter Verwendung eines Einbettungs-Containers ein adaptives Formular (AF) in eine externe Web-Seite oder in AEM Sites einzubetten, führt der Guide-Container für das adaptive Formular ein ARIA-LABEL ein. Das Label hat role=&quot;main&quot; für das eingebettete Formular. Gemäß den ARIA-Richtlinien sollte pro Seite nur eine role=&quot;main&quot; vorhanden sein. Wenn Benutzende für den Hauptinhalt ihrer Seite eine weitere role=&quot;main&quot; hinzufügen, wird diese daher als Problem mit der Barrierefreiheit gekennzeichnet. (FORMS-13538)
* Bei Verwendung der Dropdown-Komponente in einem adaptiven Formular unter AEM Forms Service Pack 19 (6.5.19.0) behalten die Dropdown-Komponenten mit Platzhaltertext den Wert `id="emptyValue"` bei. Wenn also ein Formular mehrere Dropdown-Komponenten enthält, verfügt jede über `id="emptyValue"`, was gemäß den ARIA-Richtlinien nicht korrekt ist. (FORMS-13370).
* Wenn Benutzende eine interaktive Kommunikation neu laden, nachdem die Daten über XML gesendet wurden, enthält die generierte PDF ein Leerzeichen zwischen dem Textblock. (FORMS-13481)
* Während der Ausführung von ConfigurationManager fehlt IPH für den Bildschirm „Schritt für die DSC-Bereitstellung vorbereiten“. (FORMS-10699)
* Wenn Benutzende ein neues Wörterbuch hinzufügen, um ein Formular mit vorhandenen Wörterbüchern zu übersetzen, werden die alten Übersetzungen ungültig. Es treten folgende Probleme auf: (FORMS-13576)
   * Einige Felder können nicht mit den übersetzten Daten ausgefüllt werden.
   * Einige Felder werden nicht in die neue Sprache übersetzt, obwohl die Daten erfolgreich im Wörterbuch gespeichert wurden.

#### [!DNL Forms Designer] {#forms-desgner-6521}

* Wenn Benutzende mit AEM Forms Designer in der Umgebung von AEM Forms Service Pack 19 (6.5.19.0) eine neue Tabelle in einem vorhandenen Formular hinzufügen, stürzt es ab. (LC-3921978)
* Wenn Benutzende ein adaptives Formular in einer Linux®-Umgebung rendern, entsteht ein zusätzlicher Abstand zwischen den Feldkomponenten. (LC-3921957)
* Wenn Benutzende mithilfe des Ausgabe-Services eine XTG-Datei in das PostScript-Format konvertieren, schlägt der Vorgang mit folgendem Fehler fehl:           `(AEM_OUT_001_003:Unexpected Exception: PAExecute Failure: XFA_RENDER_FAILURE)`. (LC-3921720)

  So beheben Sie das Problem:
Überprüfen Sie, ob die Daten Sonderzeichen wie „Zero Width Space (0x200b)“ enthalten. Wenn ja, verwenden Sie das Flag, indem Sie das Tag `<behaviorOverride>patch-LC3921720:1</behaviorOverride>` in der XCI-Datei, wie in der Datei [custom_xfa.xci](/help/forms/using/assets/custom_xfa.xci) angegeben, hinzufügen.

* Bei Verwendung von AEM Forms Service Pack 18 (6.5.18.0) in einer Linux®-Umgebung stürzt XMLFM auf CPUs ab, die keine AVX-/AVX2-Anweisungen mit AMD®-Prozessoren unterstützen. (LC-3921718)
* Wenn Benutzende mithilfe des Forms-Ausgabe-Services eine PDF aus einer XDP erstellen, lassen sich „Einstellungen“ für „einzelne Textblöcke“ in der XDP nicht konfigurieren, um zu steuern, was als „Artifakte“ gilt. (LC-3921954)

<!--
Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the AEM 6.5.21.0 Forms add-on package release is scheduled for Thursday, June 13, 2024. A list of Forms fixes and enhancements is added to this section post the release.

-->


<!-- #### [!DNL Adaptive Forms]

* THIS BUG WAS ALREADY REPORTED IN THE 6.5.20.0 RELEASE NOTES. IS IT NEEDED AGAIN IN THE 6.5.21.0 RELEASE NOTES? (AEM Forms on JEE Only) The PDF Generator service fails to enumerate the fonts available on the server. Consequently, the font selection panel on the Adobe PDF Settings page in the PDFG Admin UI remains empty, effectively preventing (un)embedding of chosen fonts. (FORMS-12095) -->


<!-- #### [!DNL Forms Designer] {#forms-designer-6521}

* W -->

### Fundament {#foundation-6521}

#### Apache Felix {#foundation-apachefelix-6521}


* Upgrade-Problem bei AEM 6.5 Service Pack 19 (SP19), bei dem der Kontextstammpfad des Anwendungs-Servers für nicht autorisierte Anfragen an Apache Felix nach der Installation von SP19 fehlt. Aktualisieren Sie auf Apache Felix Web Management Console 4.9.8. (NPR-41933)

#### Campaign{#foundation-campaign-6521}

* AEM 6.5 Service Pack 15 erzeugt kontinuierliche Fehlerprotokolle mit signifikanten Einträgen. Die folgenden Probleme wurden gemeldet:
   * „404 INFO“-Fehler wegen fehlender Ressource im Pfad `/libs/granite/ui/content/shell/start.html`
   * Fehlerprotokolleintrag für eine nicht abgefangene SlingException aufgrund von `NullPointerException` bei `CampaignsDataSourceServlet.java:147`

  Fehlerprotokolle sollten nicht mit häufigen und umfangreichen Fehlereinträgen gefüllt werden. Die AEM-Instanz sollte ohne Probleme funktionieren, die im Zusammenhang mit fehlenden Ressourcen oder Ausnahmen stehen. (CQ-4357064)

#### Cloud Services{#foundation-cloudservices-6521}

* Entfernen Sie Google Guava aus AEM-Cloud-Services. (CQ-4356436)

<!-- #### Communities {#foundation-communities-6521}

* U -->


<!-- #### Content distribution{#foundation-content-distribution-6521}

* T -->

#### Granite{#foundation-granite-6521}

* Sie können **Löschen** oder **Verändern** ohne die Berechtigung **Durchsuchen** nicht im Konfigurations-Browser auswählen. (GRANITE-51002)

#### Integrationen{#foundation-integrations-6521}

* In Bezug auf `cq-target-integration` muss die ungetestete Verwendung von Google Guava entfernt werden. (CQ-4357101)
* Ersetzen von Service-Konto-Anmeldeinformationen (JSON-Webtoken bzw. JWT) durch OAuth2-Server-zu-Server-Anmeldeinformationen (auch als Dienstprinzipale bezeichnet). (NPR-41994)
* Die Anfrage „Zielgruppe erstellen“ schlägt mit der Identity Management System(IMS)-Konfiguration fehl. (NPR-41888)
* Wenn eine Kundin oder ein Kunde versucht, die Payload-Seite anzuzeigen, wird der Inhalt aufgrund einer fehlerhaften URL nicht richtig angezeigt und der Fehler 404 angezeigt. Der Fehler wurde durch ein fehlendes Fragezeichensymbol in der URL, vor den Abfrageparametern, verursacht. Bei diesem Problem muss die Kundin oder der Kunde das Fragezeichensymbol einfügen, um die Payload-Seite korrekt anzuzeigen. (NPR-41957)
* Entfernen Sie den Code und die Abhängigkeiten von Adobe Search&amp;Promote aus AEM 6.5, das [gemäß Bekanntmachung im September 2022](https://experienceleague.adobe.com/de/docs/discontinued/using/search-promote) das Ende seiner Nutzungsdauer erreicht hat. (NPR-41855)

#### Lokalisierung{#foundation-localization-6521}

* Im Vorlageneditor ist die Textzeichenfolge *`No video available.`* nicht lokalisiert. (SITES-13190)
* Zeichenfolgen nach der Aktivierung oder Deaktivierung einer Person sind unter **Tools** > **Sicherheit** > **Benutzer** > *beliebiger_Benutzername* > **Aktivieren** > **OK** und bei Auswahl von *beliebiger_Benutzername* > **Deaktivieren** > **OK** nicht lokalisiert. (NPR-41737)

#### Oak {#foundation-oak-6521}

* Behebung von Performance-Regressionen: Vermeiden von Bereichsabfragen bei Like-Bedingungen. (OAK-9481)
* Die neue Oak-Version ist 1.22.20.

#### Platform{#foundation-platform-6521}

* Der Fehler `Unclosed resource resolver` tritt bei `com.day.cq.mailer.impl.DefaultMailService` auf. Die vorkonfigurierte Klasse `MessageGatewayService` wurde ohne Ressourcen-Resolver verwendet. Das Problem ist auf jeder Seite mit einer Schaltfläche zur Formularübermittlung aufgetreten, die eine E-Mail mithilfe dieser Klasse sendet. (NPR-41853)
* Im Dialogfeld **Info zu Adobe Experience Manager** wird 2023 nach wie vor als Copyright-Jahr angezeigt. (CQ-4356349)


<!-- #### Sling{#foundation-sling-6521}

* T -->

#### Übersetzung{#foundation-translation-6521}

* Der standardmäßige Übersetzungsstatus von AEM 6.5.19 wird nicht wie für einen Launch erwartet aktualisiert. Nachdem eine übersetzte Datei in einen Übersetzungsauftrag importiert wird, der mit einem AEM-Launch verknüpft ist, sollte sich der Status in `Approved` ändern. Stattdessen ändert sich der Status in `Ready for Review`, was nicht dem erwarteten Verhalten entspricht. (NPR-41756)
* Beim Erstellen mehrerer Konfigurationen und Navigieren zu den Konfigurationen für Übersetzungs-Cloud-Services werden nicht alle Elemente in der Benutzeroberfläche angezeigt. Es werden nur die ersten 40 Elemente/Ordner angezeigt. Lazy Loading wird ausgelöst, es werden jedoch keine weiteren Inhalte hinzugefügt. (NPR-41829)
* Auf der Seite „Berechtigungen“ in der Touch-Benutzeroberfläche werden im Japanischen unleserliche Zeichen angezeigt. (NPR-41794)
* AEM 6.5.14 und 6.5.9 senden kein Emoji zur Übersetzung. (CQ-4357000)

#### Benutzeroberfläche{#foundation-ui-6521}

* Unter „Tools“ > „Sicherheit“ > „Benutzer“ > &lt;Benutzername> > „Profile“ wird das Dialogfeld **Benutzereinstellungen bearbeiten** beim Klicken auf „Abbrechen“ nicht geschlossen. (NPR-41793)
* Die `pathfield`-Granite-Komponente bei `/libs/granite/ui/components/coral/foundation/form/pathfield` aktiviert die Schaltfläche **[!UICONTROL Auswählen]** nicht, wenn ein Asset ausgewählt ist. Nachdem das Pfadfeld eingeblendet wurde und die Benutzerin oder der Benutzer das Asset-Kontrollkästchen aktiviert hat, wird die Schaltfläche **[!UICONTROL Auswählen]** nicht aktiviert und bleibt grau, anstatt blau zu werden. (NPR-41970)
* Es gibt ein Problem mit dem Referenzfeld für das Inhaltsfragmentmodell (Content Fragment Model, CFM) in AEM. Obwohl das CFM-Referenzfeld als obligatorisch festgelegt wurde, können Benutzende unter bestimmten Umständen auf „Speichern“ klicken, um Inhalte mit Nicht-CFM-Werten zu speichern. Die Schaltfläche „Speichern“ sollte abgeblendet (nicht verfügbar) sein. (NPR-41894)
* Die Standarddialogfelder der Coral-Benutzeroberfläche, die die Aktion `successresponse` verwenden, müssen nach der Aktion eine Erfolgsantwort auslösen. In AEM 6.5 Service Pack 19 wird die Neuladeaktion jedoch nicht aufgerufen und es wird keine Meldung angezeigt. (NPR-41797)
* AEM-Benachrichtigungs-Links funktionieren nicht in AEM 6.5 Service Pack 18. Beim Upgrade auf Service Pack 18 funktionieren die Links für AEM-Benachrichtigungen nicht, wenn die Nachrichten über die Schaltfläche „Benachrichtigungen“ ausgewählt werden. (NPR-41792)

<!-- #### WCM{#foundation-wcm-6521}

* T -->

#### Workflow{#foundation-workflow-6521}

* In AEM 6.5.18 treten wiederholt Fehler auf, wenn während der Bereinigung Elemente aus dem Benutzermetadaten-Cache entfernt werden. (NPR-41762)

## Installieren von [!DNL Experience Manager] 6.5.21.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.21.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Service Pack-Download ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.21.0 mithilfe von Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.21.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs für [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von dem [Software-Verteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld in der Benutzeroberfläche von Package Manager wird manchmal während der Service Pack-Installation beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.21.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.21.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.21.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.20 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Service Pack-Installation für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/deploying/deploy), dient nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen.

Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.21.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.21/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.21</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.


## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Weitere Informationen finden Sie unter [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md/).

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.-->

<!-- * **Page publishing not working in Page Editor after upgrading to Service Pack 18 (6.5.18.0)** -->

<!-- https://jira.corp.adobe.com/browse/SITES-15856 REMOVE FOR 6.5.19.0 -->
<!-- After you upgrade an instance of AEM 6.5.0.0&mdash;6.5.17.0 to AEM 6.5.19.0, when you click **Publish Page** inside the Page Editor, you are redirected to a URL that does not exist.

  To work around this issue, do one of the following:

  * Remove the following "path" property.

       `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/publish/granite:data`

  * Paste the correct URL directly into the browser.

       `http://localhost:4504/editor.html/libs/wcm/core/content/sites/publishpagewizard.html?item=/content/we-retail/language-masters/en/about-us.html` -->


* **Bezogen auf Oak
Ab Service Pack 13 wird das folgende Fehlerprotokoll angezeigt, das sich auf den Persistenz-Cache auswirkt:**

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.0.202/5]
  at org.h2.mvstore.DataUtils.newMVStoreException(DataUtils.java:1004)
      at org.h2.mvstore.MVStore.getUnsupportedWriteFormatException(MVStore.java:1059)
      at org.h2.mvstore.MVStore.readStoreHeader(MVStore.java:878)
      at org.h2.mvstore.MVStore.<init>(MVStore.java:455)
      at org.h2.mvstore.MVStore$Builder.open(MVStore.java:4052)
      at org.h2.mvstore.db.Store.<init>(Store.java:129)
  ```

  Oder

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.1.214/5].
  ```

  Gehen Sie wie folgt vor, um diese Ausnahme zu beheben:

   1. Löschen Sie die beiden folgenden Ordner aus `crx-quickstart/repository/`

      * `cache`
      * `diff-cache`

   1. Installieren Sie das Service Pack oder starten Sie Experience Manager as a Cloud Service neu.
Neue Ordner `cache` und `diff-cache` werden automatisch erstellt und es gibt keine Ausnahme mehr in Bezug auf `mvstore` in `error.log`.

* Aktualisieren Sie Ihre GraphQL-Abfragen, die möglicherweise einen benutzerdefinierten API-Namen für Ihr Inhaltsmodell verwendet haben, und verwenden Sie stattdessen den Standardnamen des Inhaltsmodells.

* Eine GraphQL-Abfrage verwendet möglicherweise den `damAssetLucene`-Index anstelle des `fragments`-Index. Diese Aktion kann dazu führen, dass GraphQL-Abfragen fehlschlagen oder lange brauchen, um ausgeführt zu werden.

  Um das Problem zu beheben, muss `damAssetLucene` so konfiguriert werden, dass die folgenden beiden Eigenschaften unter `/indexRules/dam:Asset/properties` aufgenommen werden:

   * `contentFragment`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/contentFragment"`
      * `propertyIndex="{Boolean}true"`
      * `type="Boolean"`
   * `model`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/data/cq:model"`
      * `ordered="{Boolean}true"`
      * `propertyIndex="{Boolean}true"`
      * `type="String"`

  Nach Änderung der Indexdefinition ist eine Neuindizierung erforderlich (`reindex` = `true`).

  Nach diesen Schritten sollten die GraphQL-Abfragen schneller funktionieren.

* Beim Versuch, Inhaltsfragmente, Sites oder Seiten zu verschieben, zu löschen oder zu veröffentlichen, tritt ein Problem auf, wenn Inhaltsfragmentreferenzen abgerufen werden. Die Hintergrundabfrage schlägt fehl. Das heißt, die Funktionalität funktioniert nicht.
Um einen korrekten Betrieb zu gewährleisten, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten `/oak:index/damAssetLucene` hinzufügen (eine Neuindizierung ist nicht erforderlich):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5.0 bis 6.5.4 auf das neueste Service Pack für Java™ 11 aktualisieren, sehen Sie `RRD4JReporter`-Ausnahmen in der Datei `error.log`. Um die Ausnahmen zu beenden, starten Sie Ihre Instanz von [!DNL Experience Manager] neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzende können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/source „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/ Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Ab AEM 6.5.15 weist die vom Bundle ```org.apache.servicemix.bundles.rhino``` bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten auf. Skripte, die den Strict-Modus (```use strict;```) verwenden, müssen ihre korrekten Variablen deklarieren. Andernfalls werden sie nicht ausgeführt und geben am Ende einen Laufzeitfehler zurück.

* Durch die Installation von Tagging-bezogenen, vorkonfigurierten Inhalten mithilfe eines offiziellen Aktualisierungspakets wird die Spracheigenschaft des Knotens `/content/cq:tags` auf den Standard zurückgesetzt. Diese Aktion gilt für Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, Patches usw. Daher ist es erforderlich, sie vor der Installation aus den Eigenschaften hinzuzufügen.

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6521}

* SITES-17934 – Inhaltsfragmente – Vorschau schlägt aufgrund des DoS-Schutzes für eine umfassende Fragment-Baumstruktur fehl. Siehe den [KB-Artikel zu den standardmäßigen GraphQL Query Executor-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945)

<!--

### Known issues for AEM Forms {#known-issues-aem-forms-6521}
-->

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6521}


* Wenn Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) doppelte Einträge von Geode-JAR-Dateien `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` unter dem Ordner `<AEM_Forms_Installation>/lib/caching/lib` (FORMS-14926) finden, führen Sie die folgenden Schritte durch, um das Problem zu beheben:

   1. Beenden der Locators, falls sie noch ausgeführt werden.
   1. Beenden des AEM-Servers.
   1. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
   1. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
   1. Öffnen der Eingabeaufforderung im Administratormodus.
   1. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

* Wenn Benutzende versuchen, einen Briefentwurf mit gespeicherten XML-Daten in der Vorschau anzuzeigen, bleibt er für bestimmte Buchstaben im `Loading`-Zustand hängen. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (FORMS-14521)

* Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 kann der `PaperCapture`-Dienst keine OCR-Vorgänge (Optical Character Recognition) für PDFs mehr durchführen. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (CQDOC-21680)

* Wenn Benutzende von AEM 6.5 Forms Service Pack 18 (6.5.18.0) oder AEM 6.5 Forms Service Pack 19 (6.5.19.0) auf AEM 6.5 Forms Service Pack 20 (6.5.20.0) oder AEM 6.5 Forms Service Pack 21 (6.5.21.0) aktualisieren, tritt ein JSP-Kompilierungsfehler auf. Dieser verhindert, dass adaptive Formulare geöffnet oder erstellt werden, und führt außerdem zu Fehlern mit anderen AEM-Benutzeroberflächen wie dem Seiteneditor, der AEM Forms-Benutzeroberfläche und dem AEM-Workflow-Editor. (FORMS-15256)

  Wenn ein solches Problem auftritt, führen Sie die folgenden Schritte aus, um es zu beheben:
   1. Navigieren Sie in CRXDE zum Verzeichnis `/libs/fd/aemforms/install/`.
   1. Löschen Sie das Bundle `com.adobe.granite.ui.commons-5.10.26.jar`.
   1. Starten Sie den AEM-Server neu.

* Wenn ein Benutzer auf dem JEE-Server auf AEM Forms Service Pack 20 (6.5.20.0) aktualisiert und PDF mithilfe von Ausgabediensten generiert, werden die PDF mit Zugänglichkeitsproblemen gerendert. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922112)
* Wenn ein Benutzer mit dem Ausgabedienst auf JEE getaggte PDF generiert, wird &quot;Warnung bezüglich unangemessener Struktur&quot;angezeigt. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922038)
* Wenn ein Formular auf AEM Forms JEE gesendet wird, werden die Instanzen eines sich wiederholenden XML-Elements aus den Daten entfernt. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922017)
* Wenn ein Benutzer in einer Linux-Umgebung ein adaptives Formular (auf JEE) auf dem HTML rendert, schlägt die Wiedergabe fehl. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921957)
* Wenn ein Benutzer mithilfe des Output-Dienstes auf AEM Forms JEE eine XTG-Datei in das PostScript-Format konvertiert, schlägt der Fehler fehl: `AEM_OUT_001_003: Unexpected Exception: PAExecute Failure: XFA_RENDER_FAILURE`. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921720)
* Nach der Aktualisierung auf AEM Forms Service Pack 18 (6.5.18.0) auf dem JEE-Server kann ein Benutzer beim Senden eines Formulars HTML5 oder PDF forms nicht rendern und XMLFM stürzt ab. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921718)

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.21.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65210-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.21.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65210-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
