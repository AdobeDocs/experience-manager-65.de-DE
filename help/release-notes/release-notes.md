---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
source-git-commit: aec2eb3303ad9747f6f56ae2eb31c3c7ed7b0c24
workflow-type: tm+mt
source-wordcount: '4417'
ht-degree: 30%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/Documents/issue_tracker_sp_cfp_updates.xlsx?d=w3ea81ae4e6054153b132f2698c86f84e&csf=1&web=1&e=7yhrWb&nav=MTVfe0U0RjdDQUM3LTZCQ0EtNDk1Qy04Mjc1LTM2MUJEMzE1OEVGN30 -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, June 1, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.18.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 24. August 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.18.0 enthalten ist {#what-is-included-in-aem-6518}

[!DNL Experience Manager] 6.5.18.0 enthält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Zu den wichtigsten Funktionen und Verbesserungen in dieser Version gehören:

**Wichtigste Funktionen**

* Assets, Dynamic Media - [Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/video.md#about-msma)—Sie können jetzt einfach mehrere Untertitel und mehrere Audiospuren zu einem Hauptvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

* Assets - Aus den Suchergebnissen können Sie jetzt zum Ordnerspeicherort navigieren, der ein Asset enthält. Auf diese Weise können Sie verschiedene Asset-Management-Aufgaben ausführen. (ASSETS-23182)

**Wichtige Verbesserungen**

* Der Polaris-Picker für Sites in Inhaltsfragmenten hat die Leistung verbessert. (SITES-14092)

* Der Seiteneditor/Bildkomponentenbenutzer von Sites wurde aktiviert, um Assets aus dem Remote-Assets-Cloud Service zu referenzieren. (SITES-13448, SITES-13433)

* Um in der Listenansicht schnell ein Projekt zu finden, in dem sich möglicherweise viele Projekte in Ihrem System befinden, unterstützt Adobe jetzt die serverseitige Sortierung. Projektknoten werden nach der vom Benutzer ausgewählten Spalte im Backend sortiert, bevor sie in der Benutzeroberfläche gerendert werden. (NPR-41027)

* AEM 6.5.18.0 unterstützt MongoDB 5.0 bis 6.0.

**Veraltete Funktion**

* ActiveMQ in AEM wird nicht mehr unterstützt. ActiveMQ wurde für die Kommunikation zwischen zwei AEM Veröffentlichungsinstanzen verwendet. Adobe empfiehlt, dass Kunden jetzt den Lastenausgleich verwenden.

**Formulare**

* **[Verbesserte Fehlerbehebung mit benutzerdefinierten Fehler-Handlern im Regeleditor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html):** Sie können jetzt eine benutzerdefinierte Funktion (mithilfe der Client-Bibliothek) aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzer bereitstellen. Sie können auch bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist

* **[Verbesserter Workflow-Schritt in Adobe Sign](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html#sign-document-step):** Der Adobe Sign-Workflow-Schritt in AEM Workflows ist mit den folgenden Verbesserungen verfügbar.

   * **Verbesserte Sicherheit mit ID-basierter Authentifizierung für Adobe Sign:** Adobe Acrobat Signs Authentifizierung mit einer öffentlichen ID bietet eine zusätzliche Überprüfungsebene, indem Benutzer ihre Identität mit staatlich ausgestellten Kennungen (Führerschein, nationale Kennung, Pass) authentifizieren können. Durch die Verwendung vertrauenswürdiger Identifizierungsdokumente fügt diese Verbesserung dem Signierungsprozess ein zusätzliches Maß an Konfidenz hinzu, wodurch sie sich ideal für Szenarien eignet, die eine erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Verbesserte Transparenz mit dem Audit-Protokoll für Adobe Sign-Dokumente:** Verwenden Sie die Funktion &quot;Audit-Protokoll&quot;, um detaillierte Einblicke in den Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt einen umfassenden Datensatz aller Aktionen und Interaktionen verwalten, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie der Benutzer, der das Dokument angesehen, bearbeitet oder unterschrieben hat, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist von entscheidender Bedeutung für die Aufrechterhaltung der Compliance, die Beilegung von Streitigkeiten und die Sicherstellung der Integrität Ihrer digitalen Vereinbarungen.


   * **Die Rollen für Empfänger der Vereinbarung wurden über den Unterzeichner hinaus erweitert:** Adobe Acrobat Sign hat die Möglichkeit, die Rollen für Vertragsempfänger über den Unterzeichner hinaus zu erweitern, um die Anforderungen an den Workflow besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei der Unterzeichner die Standardeinstellung ist.


* **[AEM Forms on JEE-Vollinstallationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms.html)**: Das Service Pack enthält ein vollständiges Installationsprogramm für AEM Forms on JEE, das mehrere neue Softwarekombinationen unterstützt, darunter:
   * Microsoft Windows Server 2022
   * Microsoft Active Directory 2022
   * Oracle WebLogic 14C unter Windows Server 2022
   * RedHat JBoss 7.4.10
   * MongoDB 4.4
   * MySQL JDBC Connector 8

Wenn Sie eine Neuinstallation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms on JEE-Umgebung planen, empfiehlt Adobe die Verwendung des vollständigen Installationsprogramms für AEM 6.5.18.0 Forms on JEE. Die vollständige Liste der neu hinzugefügten und veralteten Software finden Sie in der Dokumentation zu AEM Forms on JEE oder AEM Forms on OSGi.

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 18 {#fixed-issues}

### [!DNL Sites]{#sites-6518}

* Mit dem Bulk Editor können Sie die Eigenschaften mehrerer Seiten aktualisieren, indem Sie die `tsv` Exportieren, offline durchgeführte Änderungen und Hochladen der `tsv` zurück zum Experience Manager. Auch wenn die Seiten aktualisiert wurden, wird die JCR-Eigenschaft `cq:lastModified` wurde nicht aktualisiert und in der Zeitleiste angezeigt. (SITES-14072)
* Der Link-Verweis wird in einem Experience Fragment nicht aktualisiert, wenn eine Live Copy oder ein Rollout eines Experience Fragment erstellt wird. (SITES-14759)
* Zur standardmäßigen Rollout-Konfiguration des Experience Manager-Rollouts, der &quot;Rollout-Seite und Unterseiten&quot; von der übergeordneten Seite wurde eine Workflow-Synchronisierungsaktion hinzugefügt. Async-Auftrag schlägt mit NullPointer-Ausnahme fehl. Die Quellspeicherungsseite (en-us) ist nicht im übergeordneten Element vorhanden, sondern befindet sich im Zielspeicherort (Live Copy) (en). (SITES-12207)
* Sie haben die Seite &quot;en&quot;, die enthält `jcr:description` und die Seite zur Übersetzung gesendet. Die `jcr:description` wird übersetzt und die Eigenschaft ist unter &quot;Launch&quot;vorhanden. Wenn der Launch jedoch beworben wird, `jcr:description` wird auf der Seite nicht aktualisiert. (SITES-13146)
* Lokalisierte Inhalte in Live Copy gehen nach dem Blueprint-Rollout verloren. (SITES-12602)

#### Admin-Benutzeroberfläche{#sites-adminui-6518}

* Wenn die Löschberechtigung eines Benutzers über die Benutzeradministratorkonsole entfernt wird, wird dem Benutzer die Schaltfläche &quot;Eigenschaften&quot;in der Konsole &quot;sites.html&quot;nicht mehr angezeigt (wenn er die Seite auswählt). Diese Option ist jedoch vorhanden, wenn der Benutzer den Seiteneditor öffnet. (SITES-14341)
* Wenn ein Ordner über viele Seiten verfügt, von denen jede über viele Versionen verfügt, wird bei Verwendung der Funktion zum Vergleichen der Version die Belastung der Instanz erhöht. Wenn mehrere Benutzer die Funktion gleichzeitig verwenden, kann die Instanz heruntergefahren werden. (SITES-13026)

#### [!DNL Content Fragments]{#sites-contentfragments-6518}

* Ein Problem wurde mit der Ausnahmebehandlung im `RemoteAssetClientImpl`. Wenn beim Abfragen der Metadaten eine IOException oder RuntimeException auftritt, versucht der aktuelle Thread, den freigegebenen httpClient zu schließen und neu zu erstellen, was zu einer Kaskade anderer Fehler in den Threads führen könnte. (SITES-14092)
* Wenn Autoren das Rich-Text-Editor-Feld in einem Inhaltsfragment ausfüllen und ein Bild in einen Link einfügen, wenn das Inhaltsfragment über die GraphQL-API abgefragt wird, wird die Fehlermeldung `Exception while fetching data (/genericContentByPath) : null` zurückgegeben. Dieser Fehler trat nur auf, wenn ein Link mit einem darin enthaltenen Bild vorhanden war. Wenn Sie das Bild aus dem Link entfernen, wird die Fehlermeldung entfernt. (SITES-13988)
* Die GraphQL-Implementierung von Experience Manager 6.5 war nicht mit dem Master kompatibel, und es fehlten einige wichtige Fehlerbehebungen. (SITES-13096)
* Beim Zugriff auf den Metadatendienst-Endpunkt ist ein obligatorischer HTTP-Header erforderlich. (SITES-13068)

#### Kernkomponenten{#sites-core-components-6518}

* Die Asset-Auswahl ruft keine aktualisierte Liste von Assets ab, wenn sie geschlossen und erneut geöffnet wird. Wenn neue Assets in das Repository hochgeladen werden, werden sie erst dann in der Asset-Auswahl angezeigt, wenn die Seite mit der Asset-Auswahl aktualisiert wurde. (SITES-14828)
* Die Benutzeroberfläche des Asset-Wählers, die in den Sites-Editor (CS) integriert ist, ist nicht responsiv, wenn das Fenster reduziert wird. (SITES-14127)
* Die Adobe IMS-Konfiguration (Identity Management-System) für die Asset-Wählerintegration akzeptierte falsche Werte. (SITES-13962)
* Die Asset-Auswahl sollte bei der Integration in die Sites-Bildkomponente die Auswahl von Nicht-Bild-Assets nicht zulassen. (SITES-13879)
* Nach erfolgreicher Anmeldung wird der Benutzer zum Seiteneditor weitergeleitet. Benutzer müssen die Asset-Auswahl erneut öffnen, um Remote-Assets auszuwählen. (SITES-13851)
* Der Remote-Asset-Wähler leitet immer zur Staging-Umgebung von Adobe IMS (Identity Management System) weiter. (SITES-13448, SITES-13433)

<!-- #### [!DNL Experience Fragments]{#sites-experiencefragments-6518}

* A -->

#### Seiteneditor{#sites-pageeditor-6518}

* Wenn der Autor die Seiteneigenschaften öffnet, weist das Dialogfeld eine falsche Ansicht auf. Das heißt, eine zusätzliche horizontale Bildlaufleiste und zusätzliche Ränder sind sichtbar. (SITES-14502)
* In Experience Manager 6.5, Service Pack 17, hinzugefügte Stile für Anker- und Body-Tag verursachten CSS-Probleme. Anker-Tags wurden in der -Autoreninstanz nicht unterstrichen angezeigt. (SITES-14261)

### [!DNL Assets]{#assets-6518}

* Die Bildschirmlesehilfe gibt den Erweiterungs- oder Reduzierungsstatus der [!UICONTROL Zuschneiden starten] -Option beim Bearbeiten eines Assets verwenden. (NPR-40593)
* Experience Manager zeigt Fehler- und Warnmeldungen beim Hochladen eines Assets in AEM 6.5.17.0-Instanz an. (ASSETS-26232)
* Wenn Sie ein Asset aus einem Ordner verknüpfen, der vollen Zugriff auf ein Asset aus einem Ordner mit schreibgeschütztem Zugriff hat, zeigt der Experience Manager eine Fehlermeldung an, erstellt aber dennoch eine Teilbeziehung zwischen den beiden Assets. (ASSETS-25832)
* Verbundene Assets funktionieren nicht zwischen einer AMS-Instanz und einer Cloud Service-Instanz. (ASSETS-24930)
* Beim Bearbeiten des Metadatenschema-Forms werden die Werte von [!UICONTROL Einschaltzeit] und [!UICONTROL Ausschaltzeit] werden nicht korrekt gespeichert. (ASSETS-24871)
* Beim Generieren des Smart-Tags-Berichts für die trainierten Tags werden die Tags mit niedrigen Konfidenzwerten nicht aufgeführt. (ASSETS-24109)
* In der Spaltenansicht wird in Experience Manager beim Bearbeiten und Kommentieren eines Bildes ein leerer Bildschirm angezeigt. (ASSETS-24108)
* Bildschirmlesehilfen geben beim Erstellen einer Sammlung nicht den Zweck des Felds Benutzer hinzufügen an. (ASSETS-21736)
* Die **Sammlungen** -Beschriftung nicht auf der Seite mit den Sammlungseigenschaften lokalisiert. (ASSETS-21102)
* Wenn Sie eine Regel hinzufügen oder eine vorhandene Regel mithilfe des standardmäßigen Metadatenschema-Formulars bearbeiten, werden die Sprachen in der Dropdownliste nicht lokalisiert. (ASSETS-21026)
* Experience Manager zeigt eine nicht lokalisierte Fehlermeldung beim Hinzufügen des JSON-Pfads zum Metadatenschema an. (ASSETS-21025)
* Die Timeline-Option im linken Navigationsbereich zeigt nicht das entsprechende Kontrastverhältnis an. (ASSETS-17348)
* Kalenderelemente verwenden nicht die erforderlichen ARIA-Attribute. (ASSETS-17282)
* Der linke Navigationstext zeigt nicht das entsprechende Kontrastverhältnis an. (ASSETS-17268)
* Das Lightbox-Bild wird den Benutzern der Bildschirmlesehilfe nicht ausgeblendet. (ASSETS-17263, ASSETS-17242)
* Der Status einer aktiven Benutzeroberfläche bietet kein angemessenes Kontrastverhältnis zum Hintergrund. (ASSETS-17260)
* Beim Kommentieren eines Assets erkennt die Bildschirmlesehilfe die [!UICONTROL Als Version speichern] oder [!UICONTROL Workflow starten] -Schaltflächen während der Navigation mithilfe der Tastaturpfeile. (ASSETS-17253)
* Bestimmte ARIA-Rollen enthalten nicht die entsprechenden untergeordneten Rollen auf der Assets-Startseite. (ASSETS-17248)
* Wenn Sie mit der Tastatur zu den Bearbeitungsoptionen für ein Asset des Bildtyps navigieren, wird die [!UICONTROL Startkarte] -Option nicht erkannt wird und der Tastaturfokus stattdessen auf die Schaltfläche Abbrechen . (ASSETS-17238)

#### [!DNL Dynamic Media]{#assets-dm-6518}

* Wenn der VTT-Download fehlschlägt, ist das Video nicht sichtbar. Es wird ein leerer Bildschirm angezeigt, während der Video-Scrubber vorwärts bewegt wird. (ASSETS-21909)
* Der Fokus wird nicht auf mehrere Steuerelemente verschoben, die unter dem Video bei der Navigation über die Registerkarte auf der Tastatur vorhanden sind. Sie sind daher nicht zugänglich. Verbesserte Tastaturnavigation für interaktive Videos. (ASSETS-25749)
* Es wurden deaktivierte Viewer-Vorgaben behoben, die in der Dynamic Media-Komponente angezeigt wurden. (ASSETS-22922)
* &quot;Image Serving&quot;wurde von der Registerkarte &quot;General Settings Security&quot;entfernt. (ASSETS-24618)
* Es wurden Assets behoben, die nicht in Dynamic Media und StringIndexOutOfBoundsException hochgeladen werden konnten. (ASSETS-25787)
* Es wurde ein visuelles Sternchen für das obligatorische Bearbeitungsfeld &quot;Breite&quot;auf der Registerkarte &quot;Einfach&quot;hinzugefügt. (ASSETS-25741)
* Der Download der Dynamic Media-Ausgabe von Wasserzeichen wurde behoben. (ASSETS-26173)
* Die Beschränkung von 127 Zeichen für Nicht-Video-Asset-Namen wurde neu festgelegt. (ASSETS-26074)

### [!DNL Forms]{#forms-6518}

<!-- Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the AEM 6.5.18.0 Forms add-on packages release is scheduled for Thursday, August 31, 2023. A list of Forms fixes and enhancements would be added to this section post the release. -->

* **Document Services**
   * Wenn ein Benutzer einen transformPDF-Dienst verwendet, schlägt er mit einer Ausnahme fehl: `java.lang.ClassNotFoundException: default task-158Class name com.adobe.internal.afml.AFMLExceptionInvalidParameter from package com.adobe.internal.afml` (FORMS-9957)
   * Wenn der Server während der Erstellung von PDF-Dokumenten heruntergefahren wird, werden Fehler bei der Verarbeitung von Post-Server-Startaufträgen ausgegeben. Das Argument -Dcom.adobe.livecycle.dsc.deferServiceStart=true muss beim Serverstart hinzugefügt werden. (FORMS-9836)
   * Wenn ein Benutzer versucht, PDF mithilfe der AssemblerService.Invoke-Methode zusammenzuführen, kann der Assembler die Aufgabe nicht durchführen. (FORMS-9550)
   * Wenn Sie auf AEM 6.5.15.0 Service Pack in OSGI- und JEE-Umgebungen aktualisieren, funktioniert der Assembler-Dienst mit einer bestimmten Vorlage nicht mehr. (FORMS-9355, FORMS-9445, FORMS-9408)
   * Die Java-Speicherbereinigung kann den alten Speicher auf einem AEM Forms-OSGi-Server nicht löschen, da das globale Timeout für XMLFormService nicht auf einen geeigneten Wert konfiguriert ist. (FORMS-9384, FORMS-9035)
   * Beim Rendern der PDF-Vorschau eines adaptiven Formulars werden die unerwünschten Java-Stack-Dumps in den Fehlerprotokollen angezeigt. (FORMS-8865)
   * Wenn ein Benutzer den Dokumentstatus für Dokumente im Abschnitt &quot;Dokumentdetails&quot;überprüft, wird er nicht korrekt angezeigt. (FORMS-8946, FORMS-10424)
   * Wenn ein Benutzer ein Upgrade auf AEM Forms durchführt und den sendToPrinter-Dienst verwendet, nimmt die Heap-Auslastung kontinuierlich zu. (FORMS-10148)
   * Auf dem JBoss 7.4 EAP-Server schlägt die E-Mail-Funktion mit `java.io.IOException`. (FORMS-10138)
   * Wenn ein Benutzer den transformPDF-Dienst verwendet, schlägt er mit einem Fehler fehl: `java.lang.ClassNotFoundException: default task-158Class name com.adobe.internal.afml.AFMLExceptionInvalidParameter from package com.adobe.internal.afml`(FORMS-9957)
   * Nach der Aktualisierung auf AEM Service Pack 6.5.14.0 tritt das Problem im Assembler-Dienst auf, wenn eine bestimmte Vorlage verwendet wird. (FORMS-9445, FORMS-9408)
  <!-- *  When a user configures the watched folder endpoint for PDF Generator, it fails to pick documents on JDK 11. (FORMS-10152) -->
* **Adaptive Formulare**.
   * Wenn ein Benutzer versucht, eine benutzerdefinierte Funktion aufzurufen, ohne ein Feld zu ändern, z. B. den Wert eines anderen Felds festzulegen, schlägt dies fehl. (FORMS-9921)
   * Beim Arbeiten mit der benutzerdefinierten Fehlerfunktion für den Regeleditor in einem adaptiven Formular treten die folgenden Fehler auf:
      * Wenn ein Benutzer versucht, @param zu verwenden{boolean} mit einer -Funktion verwenden, lässt der Regeleditor nicht zu, dass boolesche Werte an eine Funktion übergeben werden.
      * Wenn ein Benutzer versucht, @param zu verwenden{string} mit einer -Funktion verwenden, kann der Regeleditor die optionalen Werte nicht übergeben und gibt eine Warnung vor unvollständigen Regeln. (FORMS-9816, FORMS-9815)
   * Die Formularbenutzergruppe kann den Regeleditor in einem adaptiven Formular nicht zweimal aufrufen. (FORMS-9051)
   * Wenn ein Benutzer im Visual Editor ein Formularobjekt auswählt, wird das gesamte Feldinstanzobjekt an die benutzerdefinierte Funktion übergeben und nicht nur an den Wert des Felds. (FORMS-10015)
   * Wenn ein Benutzer ein auf einer Kernkomponente basierendes adaptives Formular erstellt und eine Texteingabekomponente hinzufügt, `Is Empty` und `Is Not Empty` im Regeleditor nicht funktionieren. (FORMS-10098)
   * Wenn ein Feld in einem auf einer Kernkomponente basierenden adaptiven Formular als ungültig markiert ist, startet es ein Änderungsereignis im Feld. (FORMS-10087)
   * Wenn ein Benutzer versucht, ein adaptives Formular mit einem komplexen JSON-Schema zu erstellen, schlägt dies fehl. Der Fehler tritt wie folgt auf:
     `GET /content/forms/af/katezeroone/testaf1.html HTTP/1.1] com.adobe.aemds.guide.service.impl.JsonObjectCreatorImpl Could not emit JSON with context java.lang.ArrayIndexOutOfBoundsException:0`. (FORMS-9639)
   * Wenn ein Benutzer in einem adaptiven Formular das Kontrollkästchen &quot;Ich stimme den Bedingungen zu&quot;deaktiviert, wird es erneut aktiviert, sobald der Benutzer nach unten scrollt. (FORMS-9458)
   * Wenn ein Benutzer ein adaptives Formular auf einem Android-Gerät mit Google Chrome/Firefox öffnet und die maximal zulässigen Zeichen in ein Textfeld eingibt, kann der Wert im Textfeld nicht gelöscht werden. (FORMS-9354)
   * Wenn die Beschriftung des Kontrollkästchens Sonderzeichen wie &#39;,&#39;, &#39;/&#39; oder &#39;.&#39; enthält, wird durch Klicken auf den Text/die Beschriftung das entsprechende Kontrollkästchen nicht aktiviert. (FORMS-9313)
   * Wenn ein Benutzer versucht, die Komponente &quot;Allgemeine Geschäftsbedingungen&quot;zu validieren, kann er nicht überprüfen, ob die Komponente nicht im Fokus ist, während die andere Komponente validiert wird. (FORMS-8725, FORMS-8913)
   * Wenn ein adaptives Formular nach der Aktualisierung auf AEM 6.5.16.0 Service Pack neu geladen wird, schlägt der Abruf der Dateianlagen fehl. (FORMS-8906)
   * Wenn in einem adaptiven Formular, das auf einer XDP basiert, eine Kontrollkästchenkomponente einen Texttitel enthält, dem ein numerischer Wert zugewiesen wurde, wird der Texttitel abgeschnitten und entspricht nicht dem zugewiesenen Wert. (FORMS-8743)
   * Wenn ein Benutzer versucht, verzögertes Laden auf ein in ein adaptives Formular eingebettetes Fragment für die Autorenumgebung zu implementieren, werden die für das Fragment definierten Regeln/Logiken nicht im Formular übernommen. (FORMS-8554, FORMS-9182)
   * Wenn Sie versuchen, ein Coral-Dialogfeld in AEM 6.5.16.0 Service Pack zu öffnen, wird das `error.log: cannot render resource` Ausnahmefehler. (FORMS-8942)
   * Wenn ein Benutzer versucht, ein Kontrollkästchen mit einer einzigen Option in einem adaptiven Formular zu übersetzen, schlägt dies fehl. (FORMS-10181)
* **Erreichbarkeit**
   * Bei Verwendung der Scribble-Signatur-Komponente in einem adaptiven Formular treten die folgenden Fehler auf:
      * Wenn nach der Scribble-Signatur-Komponente weitere Komponenten vorhanden sind, wird durch Drücken der Tabulatortaste nicht zum Signaturdialogfeld gewechselt. Stattdessen wird zur nächsten Komponente gewechselt. Erst nachdem alle Komponenten durchlaufen wurden, wird das Signaturdialogfeld geöffnet.
      * Wenn sich ein Benutzer im Signaturdialogfeld mit einer Pinsel oder Tastatur anmeldet, wird das Dialogfeld durch Drücken der Eingabetaste nicht geschlossen.
      * Der Zugriff auf das Dialogfeld zur Bestätigung einer klaren Signatur ist über eine Tastatur nicht möglich.
      * Die Sprachausgabe kann die in einem Dialogfeld eingegebenen Informationen nicht lesen.
      * Es ist nicht möglich, die Signatur ohne die Maus zu löschen.  (FORMS-9317)
   * Wenn ein Benutzer ein adaptives Formular sendet, kann die Bildschirmlesehilfe keine Fehlermeldungen für die Pflichtfelder lesen. (FORMS-9316)
   * Wenn eine Bildschirmlesehilfe ein HTML-Formular liest, tritt beim Lesen des Textes mit Kerning (Leerzeichen) das Problem auf. (FORMS-9258)
   * In einem adaptiven Formular werden die mit dem Text verknüpften Verweise/Fußnoten nicht mit der Bildschirmlesehilfe aufgerufen. (FORMS-8920)
   * Tags für die Barrierefreiheit werden in der neuesten Designer-Version nicht richtig erkannt. (FORMS-10139)
* **Interaktive Kommunikation**
   * In Correspondence Management funktioniert die Lokalisierung nicht. (FORMS-8926)
   * Der Briefentwurf kann nicht geöffnet werden, wenn der publishAll-Dienst verwendet wird. (FORMS-8589)
   * Nach dem Experience Manager wird Service Pack 16 auf den Servern installiert. Alle interaktiven Kommunikationsbriefe werden gestartet, wenn sie versuchen, diese Briefe zu bearbeiten. Wenn sie eine Beispiel-Payload bereitstellen, um die Eigenschaftenseite in der Vorschau anzuzeigen oder anzuzeigen/zu bearbeiten, funktionieren sie. Sie können die Briefe jedoch nicht bearbeiten. (FORMS-9067)


<!-- ### [!DNL Commerce]{#commerce-6518}

* A -->

### Fundament{#foundation-6518}

#### Inhaltsverteilung{#foundation-content-distribution-6518}

* Die Warteschlange zum Löschen von Assets sollte nicht blockiert werden und in der Protokolldatei sollte kein Fehler auftreten. (NPR-40570)

<!-- #### Integrations{#integrations-6518}

* A -->

<!-- #### Oak{#oak-6518}

* A -->

#### Platform{#foundation-platform-6518}

* Nach der Installation eines Vanilla-Experience Managers, Service Pack 17, treten Fehler im `stderr.log`. Vanilla-Installationen sollten keine Fehler erhalten. (CQ-4353637)
* Schaltfläche &quot;Erstellen&quot;im Bildschirm &quot;Tagging&quot;unter Berücksichtigung von ACL (Zugriffssteuerungsliste). (NPR-40973)
* Der Cache-Knoten von ContextHub auf dem Experience Manager kann weder erstellt noch darauf zugegriffen werden. (NPR-40515)

#### Replikation{#foundation-replication-6518}

* Replikationsflush löscht alle untergeordneten Elemente des angeforderten Pfads. (NPR-40569)

#### Sling{#foundation-sling-6518}

* Wenn ein Bericht zur Linkfreigabe generiert wird, enthält der Spaltenlink nicht die richtigen Werte. (NPR-40798)
* Mit AEM 6.5.15.0 werden alle Vanity-URLs, Sling-Aliase und Sling-Mapping nach einem AEM Neustart beschädigt. (NPR-40420)

#### Übersetzungsprojekte{#foundation-translation-6518}

* Übersetzung `rules.xml` wurde auf eine schlechte Art und Weise sortiert, wenn über die Benutzeroberfläche für die Übersetzungskonfiguration Regeln hinzugefügt werden. (NPR-40431)
* Unterstützung von Links mit Abfrageparametern während der Übersetzung. (NPR-40339)
* Die Wörterbuchbenutzeroberfläche wird für den Kunden nach der Aktualisierung des zusätzlichen Kontextstamms nicht geladen. (NPR-40650)
* Fehler beim Erstellen von Sprachkopien, wenn eines der Assets ein Inhaltsfragment ist, das ein Mehrfachfeld mit den Typen ReferenceFragment oder ContentFragment enthält. (NPR-40892)

#### Benutzeroberfläche{#foundation-ui-6518}

* Wie im Abschnitt [Dokumentation zum Konfigurationsbrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=en#using-configuration-browser), _Der Name wird zum Knotennamen im Repository._. Im Konfigurationsbrowser wird jedoch der Konfigurationstitel für den Pfad im CRXDE Lite verwendet und der Name der Konfiguration wird ignoriert. (NPR-40607)

<!-- #### WCM{#wcm-6518}

* A -->

#### Workflow{#foundation-workflow-6518}

* Beim Zurücksetzen einer Asset-Version bleibt der Asset-Status im Verarbeitungsmodus. (NPR-41029)
* Sortierungsproblem auf der Benutzeroberfläche &quot;Assets und Projekte&quot;. Einige haben die benutzerdefinierten Spalten auf der Benutzeroberfläche &quot;Assets&quot;und &quot;Projekte&quot;entsprechend den Geschäftsanforderungen überlagert. Sie haben eine Sortierung mithilfe der nativen Eigenschaft implementiert. `sortable=true`. Sie sehen jedoch Inkonsistenzen bei der Sortierung, wenn es viele Einträge unter der Benutzeroberfläche &quot;Projekte&quot;oder &quot;Assets&quot;gibt. (NPR-41027)
* Protokolle werden mit `NullPointerException` im `EMailNotificationService`und E-Mails, die von Workflows gesendet werden sollen, werden nicht gesendet. (NPR-40898)
<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST  * The timeline is not providing references to the selected content. (NPR-40806) -->

## Installieren von [!DNL Experience Manager] 6.5.18.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.18.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die Adobe-[Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.18.0 mit dem Package Manager auf einer der Authoring-Instanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.18.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs auf [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installation erfolgreich ist. Normalerweise tritt dieses Problem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.18.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.18.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.18.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.16 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- NPR-41010 for 6.5.18.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Installation des Service Packs für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen.

Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.18.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.18/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.18</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.

## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Siehe [Eingestellte und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md/).

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* Im Zusammenhang mit Oak From Service Pack 13 und höher wird jetzt das folgende Fehlerprotokoll angezeigt, das sich auf den Persistenzcache auswirkt:

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

  Um das Problem zu beheben, muss `damAssetLucene` so konfiguriert werden, dass die folgenden beiden Eigenschaften einbezogen werden:

   * `contentFragment`
   * `model`

  Nach Änderung der Indexdefinition ist eine Neuindizierung erforderlich (`reindex` = `true`).

  Nach diesen Schritten sollten die GraphQL-Abfragen schneller funktionieren.

* Beim Versuch, Inhaltsfragmente, Sites oder Seiten zu verschieben, zu löschen oder zu veröffentlichen, tritt ein Problem auf, wenn Inhaltsfragmentreferenzen abgerufen werden, da die Hintergrundabfrage fehlschlägt. Das heißt, die Funktionalität funktioniert nicht.
Um einen korrekten Betrieb zu gewährleisten, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten `/oak:index/damAssetLucene` hinzufügen (eine Neuindizierung ist nicht erforderlich):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5.0 bis 6.5.4 auf das neueste Service Pack für Java™ 11 aktualisieren, sehen Sie `RRD4JReporter`-Ausnahmen in der Datei `error.log`. Um die Ausnahmen zu stoppen, starten Sie Ihre Instanz von [!DNL Experience Manager] neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzende können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/source „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/ Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` – Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Ab AEM 6.5.15 weist die vom ```org.apache.servicemix.bundles.rhino```-Bundle bereitgestellte Rhino-JavaScript-Engine ein neues Hosting-Verhalten auf. Skripte, die den strikten Modus (```use strict;```) müssen ihre Variablen korrekt deklarieren, andernfalls werden sie nicht ausgeführt, sondern es wird ein Laufzeitfehler ausgegeben.

### Bekannte Probleme bei AEM Forms

#### Unterstützte Plattformen

* JDK-Versionen, die höher als 1.8.0_281 sind, werden für WebLogic JEE-Server nicht unterstützt. (FORMS-8498, CQDOC-20383)
* Da [!DNL Microsoft® Windows Server 2019] [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1] nicht unterstützt, unterstützt [!DNL Microsoft® Windows Server 2019] keine schlüsselfertigen Installationen für [!DNL Experience Manager Forms 6.5.10.0]. (CQDOC-18312)
* JDK 11.0.20 wird zur Installation des AEM Forms on JEE-Installationsprogramms nicht unterstützt. Nur JDK 11.0.19 oder frühere Versionen werden zur Installation des AEM Forms on JEE-Installationsprogramms unterstützt. (FORMS-10659)

#### Installation

* Auf der Plattform JBoss® 7.1.4 schlägt die Bereitstellung fehl, wenn Benutzende Experience Manager 6.5.16.0 oder ein höheres Service Pack installieren. `adobe-livecycle-jboss.ear` (CQ-4351522, CQDOC-20159)
* Nach der Installation des vollständigen Installationsprogramms für AEM Service Pack 6.5.18.0 schlägt die EAR-Bereitstellung auf JEE mit der JBoss-Turnkey-Methode fehl (CQDOC-20803).
Suchen Sie zum Beheben des Problems die `<AEM_Forms_Installation_dir>\jboss\bin\standalone.bat` Datei und Aktualisierung `Adobe_Adobe_JAVA_HOME` nach `Adobe_JAVA_HOME` für alle Vorkommnisse vor der Ausführung des Konfigurations-Managers.

#### Adaptive Formulare

* Wenn ein adaptives Formular veröffentlicht wird, werden alle Abhängigkeiten, einschließlich Richtlinien, erneut veröffentlicht, selbst wenn keine Änderungen an ihm vorgenommen wurden. (FORMS-10454)
* Wenn Benutzende ein Feld erstmals in einem adaptiven Formular konfigurieren möchten, wird im Eigenschaften-Browser die Option zum Speichern einer Konfiguration nicht angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.
* Wenn eine Umleitungs-URL im Guide-Container eines adaptiven Formulars festgelegt ist, funktioniert die Inline-Signatur nicht mehr. (FORMS-10493)

#### Interaktive Kommunikation

* Nach der Aktualisierung auf AEM Service Pack 18 ist es nicht möglich, interaktive Kommunikationsbriefe zu bearbeiten. (FORMS-10578) Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

   1. Herunterladen [Hotfix-FORMS-10578](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) von SD-Link aus.
   1. Extrahieren Sie die Hotfix-Archivdatei, um ein Experience Manager-Paket (.zip) und Bundle (.jar) abzurufen.
   1. Laden Sie das Paket (.zip) über den Package Manager hoch und installieren Sie es.
   1. Öffnen Sie die Konfigurations-Manager-Pakete. `https://server:host/system/console/bundles`, laden Sie das Bundle hoch und installieren Sie es (.jar).

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5.18.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.18.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65180_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.18.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65180_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
