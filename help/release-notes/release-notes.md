---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6,5
description: Suchen Sie nach Versionsinformationen, Neuigkeiten, Installationsanleitungen und einer detaillierten Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 3
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 48f898a774d2ddd6d2c31f6a4107c71e4032cfc2
workflow-type: tm+mt
source-wordcount: '3281'
ht-degree: 5%

---

# [!DNL Adobe Experience Manager] 6.5 Neueste Service Pack - Versionshinweise {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession&cid=a915e87c-369a-480c-9daf-d13efc766798 -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.14.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | 25. August 2022 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.14.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was ist enthalten in [!DNL Experience Manager] 6.5.14.0 {#what-is-included-in-aem-6514}

[!DNL Experience Manager] 6.5.14.0 umfasst neue Funktionen, wichtige von Kunden angeforderte Verbesserungen, Fehlerbehebungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Dieses Service Pack installieren](#install) on [!DNL Experience Manager] 6.5. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_

* Added support for password reset for Dynamic Media Classic users within Experience Manager. (ASSETS-10298) -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets] {#assets-6514}

* Tags für PDF-Dateien können nicht hinzugefügt oder angezeigt werden. (NPR-38452)
* Wenn Sie Connected Assets konfigurieren, die Konfiguration speichern, die Konfigurationsseite erneut öffnen und die bereits gespeicherte Konfiguration testen, schlägt die Testverbindung fehl. (NPR-38507)
* Benutzer mit numerischer Benutzer-ID können nicht zu Sammlungen hinzugefügt werden. (NPR-38538)
* Experience Manager kann die auf der Autoreninstanz installierte FFmpeg nicht verarbeiten. (NPR-38568)
* Die PDF-Verarbeitung schlägt mit einer `NoClassDefFoundError` Fehlermeldung. (NPR-38741)
* Die Schaltfläche Hinzufügen unter Benutzerdefinierte Spalten wird beim Erstellen eines Asset-Berichts für `de_DE` Gebietsschema. (ASSETS-10641)
* Wenn Sie ein doppeltes Asset in das Digital Asset Management-Repository hochladen und Experience Manager eine Option zum Löschen des doppelten Assets erkennt und bereitstellt, wird das ursprüngliche Asset auch aus dem Repository gelöscht. (ASSETS-10826)
* Experience Manager speichert die Ordnermetadaten nicht ordnungsgemäß, wenn Sie Sonderzeichen in mehreren Feldern angeben. (ASSETS-10721)
* Asset-Eigenschaften können erst gespeichert werden, wenn Sie auf **[!UICONTROL Speichern und schließen]** zweimal. (ASSETS-12040)
* Die Bildschirmlesehilfe kündigt nur die `Relate` Schaltfläche. Die Variable `Relate` -Schaltfläche enthält auch ein Untermenü und kann erweitert und reduziert werden. (ASSETS-6938)
* Erforderliche ARIA-Attribute (Accessible Rich Internet Applications) `aria-expanded` für `role="combo box"` fehlt. (ASSETS-6928)
* In der Kartenansicht im Hauptnavigationsbereich für die Datei wird der Textinhalt **[!UICONTROL Sortieren nach]** hat nicht mindestens ein Kontrastverhältnis von 4,5:1 gegenüber der Hintergrundfarbe. (ASSETS-6926)
* Experience Manager identifiziert nicht **[!UICONTROL Workflow-Modell auswählen]** Dropdown-Liste als erforderliches Feld beim Erstellen eines Workflow-Modells. (ASSETS-6871)

>[!NOTE]
>
>Smart Content Services stehen neuen On-Premise-Kunden von Experience Manager Assets ab dem 1. September 2022 nicht mehr zur Verfügung. Keine Auswirkungen auf bestehende On-Premise- und Adobe Managed Services-Kunden, für die diese Funktion bereits aktiviert ist.

### [!DNL Dynamic Media] {#dynamic-media-6514}

* Unterstützung für das Zurücksetzen des Kennworts für Dynamic Media Classic-Benutzer in Experience Manager hinzugefügt. (ASSETS-10298)
* Smartes Zuschneiden für Bilder mit transparentem Hintergrund hat weißen Hintergrund. (ASSETS-13148)
* Dynamic Media generiert keine Miniaturansichten für EPS-Dateien. (ASSETS-10959)
* Assets werden aufgrund des fehlenden Upload-Parameters nicht in das Dynamic Media-Konto hochgeladen. (ASSETS-13165)
* Assets mit Namen von mehr als 127 Zeichen dürfen in Dynamic Media hochgeladen werden. (ASSETS-9991)
* Aktivierung von JavaScript ES6 (ECMAScript 6) für Dynamic Media-Viewer in Experience Manager 6.5.14.0. (NPR-38393)
* Konfigurieren der Optionen in Dynamic Media **[!UICONTROL Allgemeine Einstellungen]** und **[!UICONTROL Veröffentlichungseinstellungen]** sollten für Benutzer ohne Administratorrechte nicht zugänglich sein. (ASSETS-8628)
* Dynamic Media **[!UICONTROL Allgemeine Einstellungen]** -Seite zeigt die bereits konfigurierten Upload-Parameter nicht korrekt an. (ASSETS-10245)
* In der Benutzeroberfläche des Experience Managers wird keine Fehlermeldung angezeigt, falls die Erstellung/Aktualisierung eines Sets fehlschlägt. (ASSETS-10264)
* Eine gespeicherte Richtlinie kann nicht auf einen der Container einer bearbeitbaren Vorlage angewendet werden, damit Sie Dynamic Media-Komponenten hinzufügen können. (ASSETS-11044)
* Assets werden nicht in das Dynamic Media-Konto hochgeladen, nachdem der Dynamic Media-Workflow zur erneuten Verarbeitung von Assets für Assets mit falschem Auftragsbearbeitung ausgeführt wurde. (ASSETS-12084, ASSETS-9877)
* Benutzer von Bildschirmlesehilfen sind von der `title` -Attribut nicht angegeben `<frame>` und `<iframe>` im **[!UICONTROL Typ zur Suche]** Dialogfeld. (ASSETS-5483)
* In Bildschirmlesehilfen, verwandte und aussagekräftige `alt=` -Wert für mehrere Bilder angegeben werden, die unter **[!UICONTROL Assets]** im linken Bereich. (ASSETS-5644)
* Sprachausgabe wird nicht gelesen **[!UICONTROL Stummschaltung]** und **[!UICONTROL Unmute]** Schaltfläche im Video mit der Dynamic Media-Komponente. (ASSETS-10169)

## Commerce  {#commerce-6514}

* Commerce-Produkte werden nicht mithilfe der Spaltenüberschrift sortiert und werden verwendet _remote_ Sortiermodus; Stattdessen sollten Commerce-Produkte mithilfe von Spaltenüberschriften mit _lokal_ Sortiermodus. (CQ-4343750, NPR-38498)



## [!DNL Forms] {#forms-6514}

<!--

>[!NOTE]
>
> Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

>[!NOTE]
>
>* [!DNL Experience Manager Forms] releases the add-on packages one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages will release Thursday, September 1, 2022. In addition, a list of Forms fixes and enhancements will also be added to this section.

-->

* Wenn eine Datei an ein adaptives Formular mit mehreren Bereichen angehängt und ein Entwurf des adaptiven Formulars gespeichert wird, tritt ein Fehler auf. (NPR-38978)
* Wenn ein RGB-Profil mithilfe der Java-API createPDF2 mit AdobePDF-Einstellungen in ein CMYK-Profil konvertiert wird, funktioniert die Option nicht mit der Java-API. Die Option funktioniert problemlos mit der eigenständigen DistillerClient-Anwendung. (NPR-38858, CQ-4346181)
* Nach der Installation von AEM 6.5 Forms Service Pack 12 (6.5.12.0) sind alle Optionen außer zum Schließen der Aufgabe im Schritt &quot;Aufgabe zuweisen&quot;von AEM Workflows nicht mehr verfügbar. (NPR-38743)
* In Datensatzdokumenten (DoR) werden einige Werte in einer Tabelle abgeschnitten. (NPR-38657)
* Bei der Vorschau von FormSet mit Daten-XML werden bei XDP-Dateien mit schwebenden Feldern bei der Vorschau eines Formularsatzes keine Daten angezeigt, aber bei Verwendung der Option Vorschau-PDF werden Daten angezeigt.
* In Adaptive Forms befinden sich Optionsfelder und Kontrollkästchen nicht in der Tab-Reihenfolge. (NPR-38645)
* Wenn Sie `Summary Step` zum Generieren des Datensatzdokuments (DoR) für ein übersetztes adaptives Formular nach der Übermittlung wird nicht in die lokalisierte Sprache übersetzt. (NPR-38567)
* Die Option Neuversuch deaktivieren in AEM Workflow-Schritten funktioniert nicht erwartungsgemäß. Das Problem tritt gelegentlich auf. (NPR-38547)
* Wenn das adaptive Formular mit dem Feld Rich-Text gesendet wird, wird die `an Internal Error while Submitting a Form` Fehler auftreten. Wenn der Benutzer den Fokus auf das Rich-Text-Feld legt, tritt der Fehler nicht vor der Übermittlung des Formulars auf. (NPR-38542)
* Fehler `sling-default-3-AdobeSignRefreshTokenScheduleJob com.adobe.forms.foundation.oauth.model.OAuthConfigSlingModel Refresh Token not present for: /conf/gws-eform/cashlite/settings/cloudconfigs/fdm/cashlite/jcr:content occurs` wird protokolliert. (NPR-38541)
* Wenn ein Benutzer eine PDF in ein adaptives Formular hochlädt, reagiert der AEM Forms-Server nicht mehr. (NPR-38398)
* Wenn Sie auf einem AEM Forms on OSGi-Server die Document Service-API zum Zertifizieren von PDF verwenden, schlägt der Fehler fehl: com.adobe.fd.signatures.truststore.errors.exception.CredentialRetrievalException: AEM-DSS-311. (CQ-4346252)
* Bei der Übermittlung der Briefentwürfe muss die `Could not upload asset from xml input` Fehler auftritt. Dies hat keine Auswirkungen auf die Funktionalität. Wenn Sie einen Entwurf öffnen, wird der Brief korrekt gerendert. (CQ-4345979, CQ-4344418)
* Wenn ein Datum im deutschen Format eingegeben wird und die Variable `Preview with Data` für einen Brief verwendet wird, wird das Datumsfeld nicht gerendert. (CQ-4345783)
* Beim Erstellen eines Webportals und Generieren der datenbasierten Barcodes werden einige Barcodes nicht korrekt dekodiert. (CQ-4345743)
* Die Postscript-Konvertierung in die PDF gibt kein Ausgabedokument mit erwarteten Farben wieder. (CQ-4345074)
* Der Ressourcen-Resolver verursacht zeitweise Fehler bei der Übermittlung und führt dazu, dass dieselbe Stacktrace mehrmals für eine einzelne Übermittlung angezeigt wird. (CQ-4344764)
* Benutzer können die geänderten Entwurfsbriefe, die die `cmDataUrl` Parameter. Die Entwürfe werden zum ersten Mal in Ordnung gebracht. Die Probleme treten in nachfolgenden Versuchen auf. (CQ-4344418)
* Wenn der Benutzer `&` -Symbol in einer interaktiven Kommunikation (IC), kann der Entwurf der entsprechenden IC nicht geladen werden. (CQ-4343969)
* Wenn Sie Stiloptionen in AEM Forms Designer zum Generieren von PCL-Dateien verwenden, wird der angegebene Stil nicht auf die generierten Dateien angewendet. (CQ-4339573)
* Wenn die Seitenzahl größer als 15 ist, schlägt die automatische Konvertierung dynamischer XDP-Formulare in adaptive Formulare fehl. Dies funktioniert einwandfrei, wenn die Seitenzahl kleiner als 15 ist. (NPR-35337)
* Wenn die Option Zu Favoriten hinzufügen verwendet wird, zeigt sie nicht den Status des Umschalters zur Bildschirmlesehilfe an. (NPR-37137)
* Im Formulardatenmodell werden die Werte nach der Dezimalzahl im datenbankgestützten Formulardatenmodell für Geld und Kleingeld gekürzt. . (CQDOC-19509)
* Wenn Sie einen Navigationslink für einen Workflow in HTML Workspace auswählen, wird nicht angegeben, dass der Navigationslink ausgewählt ist. (NPR-37138)
* Die Funktion für Scribble-Signaturen ist nicht mit den Richtlinien für Barrierefreiheit kompatibel. (NPR-37596)
* AEM Forms verwendet log4j 1.x. Die Unterstützung für log4j 1.x wurde eingestellt. (NPR-38273)
* Wenn Sie die MSSQL-Datenbank als Datenquelle in einem Formulardatenmodell verwenden und Werte abrufen, werden die Zahlen nach der Dezimalzahl in den Abrufwerten abgeschnitten. (CQ-4346190)
* Wenn Sie in Forms 6.5 Designer ein mit Forms 6.1 Designer erstelltes Formular öffnen und ein Textfeld bearbeiten, überschreitet der Absatzabstand den angegebenen Platz. Alle vorherigen Einstellungen des Bereichs werden entfernt und eine manuelle Neuformatierung des Textfelds ist erforderlich. (CQ-4341899)
* Für den Barcode SSCC-18 wird ein falscher Wert angezeigt. Auf Forms-Servern wird der Wert im rechten Teil des Barcodes weggelassen. (CQ-4342400)
* Bei statischen PDF forms, die mit Forms 6.5 Designer erstellt wurden, schlägt die PDF-Barrierefreiheit mit einem Fehler fehl `Tab order entry in page with annotations not set to "S"`. (CQ-4343117)
* Es wurde die Möglichkeit hinzugefügt, in Forms Designer &quot;Reader für Hyperlinks&quot;festzulegen.(NPR-36221)
* Wenn Sie einem adaptiven Formular ohne XFA wiederholbare Bereiche hinzufügen und die Anzahl der wiederholbaren Bereiche in einem Nicht-XFA-Formular mehr als 15 beträgt, kann das Hinzufügen einer neuen Instanz bis zu 7-8 Sekunden dauern. (NPR-37346)

## Integrationen {#integrations-6514}

* JavaScript ES6 (ECMAScript6-Modus oder höher)-Kompilierungsunterstützung für die Minimierung der `/libs/cq/analytics/widgets.js` -Bibliothek. (NPR-38433)
* JavaScript ES6 (ESMAScript6-Modus oder höher)-Kompilierungsunterstützung für die Minimierung der `/libs/cq/testandtarget/clientlibs/testandtarget/util.js` -Bibliothek. (NPR-38435)
* Je mehr Inhalt es in `/content/campaigns`, je länger der Aufruf von `targeteditor.html` (`/libs/cq/personalization/touch-ui/content/targeteditor.html`) wird beim Öffnen des Seiteneditors ausgeführt. (NPR-38663)

## Plattform {#platform-6514}

* Die Anmeldung bei Package Manager zur Bereitstellung von Updates ist nicht möglich. (NPR-38646)
* In der Benutzeroberfläche der Asset-Tag-Auswahl werden Tags in der Reihenfolge angezeigt, in der sie erstellt wurden. Wenn jedoch viele Tags vorhanden sind, ist es schwierig, die Tags anzuzeigen und zu verwalten, da sie nicht sortiert werden können. (CQ-4344279)
* Erstellen Sie eine Benachrichtigung in der Benutzeroberfläche, wenn ein Benutzer von einem Administrator stellvertretend agiert wird oder jemand, der die **[!UICONTROL Identität annehmen als]** -Feld. (CQ-4345288)
* In einer Smart-Sammlung wurden beim Filtern mit einer gespeicherten Suche alle Assets angezeigt. (CQ-4345326)
* Eine falsche Anzahl ausgewählter Assets wird angezeigt für **[!UICONTROL Zu Sammlung hinzufügen]** when **[!UICONTROL Alle auswählen]** ausgewählt ist. (CQ-4345424)
* Bei Verwendung der **[!UICONTROL Identität annehmen als]** mit einer Gruppe oder einem nicht vorhandenen Benutzer. (CQ-4346098)

## [!DNL Sites] {#sites-6514}

* Beim Aktualisieren von Experience Manager von 6.5.12.0 auf 6.5.13.0 sind unerwartete Pfadlöschungen aufgetreten. (NPR-38532)

### Barrierefreiheit {#access-6514}

* Wenn Sie in Experience Manager Sites die **[!UICONTROL Anzeigeformat wechseln und Anzeigeeinstellung anpassen]** Schaltfläche und wählen Sie **[!UICONTROL Listenansicht]**, die **[!UICONTROL Drag &amp; Drop]** -Schaltfläche fehlt ein zugänglicher Name. (SITES-2863, NPR-38760)
* Die Bildschirmlesehilfe muss den zugänglichen Namen ankündigen, z. B. `Show description for Archive` oder `Show description for mini shopping cart`. Der aktuelle barrierefreie Name wird jedoch als `Info Circle button show description` für _all_ die Schaltflächen für QuickInfo-Informationen. (SITES-3104)
* Verbessern Sie die Rückgängigmachung für Komponenten, die nicht über die Funktion inlineEditing oder dropTarget verfügen in `cq:editConfig`. (NPR-38361) <!-- version 2 (old) of the description above * When out of the box components that don't have inlineEditing or dropTarget feature in the _cq_editConfig file (navigation, breadcrumb, embed) are deleted > undeleted (by way of Undo), all configurations are lost and empty placeholder reappears. Component must be reconfigured from scratch. (NPR-38361) -->
* Die Dropdown-Liste &quot;Stilsystem&quot;wurde möglicherweise oben auf der Seite anstelle der Komponente im Kontext positioniert - für Komponenten, die `cq:editConfig` &quot;afteredit: REFRESH_PAGE&quot;. (NPR-38384) <!-- version 2 (old) of description above* When selecting a style option on a component, the Styles box shifts to the upper left corner of the screen, rather than staying put below the style icon. Happens for components that have  cq:editConfig "afteredit: REFRESH_PAGE". (NPR-38384) -->
* Die Textkomponente ist beim Hinzufügen zu verschachtelten Layout-Containern falsch ausgerichtet. (NPR-38193)
* Es wurde eine leere Stilregisterkarte angezeigt, wenn keine Stilsystemkonfiguration für eine Komponente vorhanden war. Die Registerkarte ist jetzt ausgeblendet, wenn keine Konfiguration vorhanden ist. (NPR-38218) <!-- version 2 (old) of description above * Style tab is blank on components without styles/policies. (NPR-38218) -->
* Die Eigenschaft `useLegacyResponsiveBehaviour` funktioniert nur bei der Authentifizierung. (NPR-37996)

### [!DNL Content Fragments] {#sites-contentfragments-6514}

* Bei der Überprüfung des Auflistungsfelds für Inhaltsfragmente tritt beim ersten Laden des Inhaltsfragments ein Fehler auf. (SITES-7140)
* Es müssen Personalisierungsfelder für Campaign im Rich-Text-Editor des Inhaltsfragmente-Editors hinzugefügt werden. (NPR-38526)
* Beim Erstellen oder Bearbeiten eines neuen Inhaltsfragments im Inhaltsfragment-Editor wird das Inhaltsfragmentmodell über den Dispatcher nicht gespeichert. Darüber hinaus wird der Inhaltsfragment-Editor nicht geschlossen und im Browserprotokoll wird ein Fehler angezeigt. (NPR-38691)
* Validierungsfehler bei persistenten Abfragen. (NPR-38523)
* Im Dialogfeld &quot;Inhaltsfragment&quot;unter **[!UICONTROL Eigenschaften]**, die **[!UICONTROL Inhaltsfragment]** Der gespeicherte Pfad wird im Auswahl-Popup nicht beibehalten. (NPR-38632)
* Wenn Sie ein Inhaltsfragmentmodell erstellen und ein Auflistungsfeld des Dropdown-Typs hinzufügen, wird die richtige Validierung für _`is required`_fehlschlägt. (NPR-38237)

### Kernkomponenten {#sites-corecomponents-6514}

* Die neue Komponente &quot;Seiten-E-Mail&quot;sollte Sie beim Bearbeiten nicht in die klassische Benutzeroberfläche zwingen `/etc`. (NPR-38648)

### Seiteneditor {#sites-pageeditor-6514}

* Der Benutzer kann die Größe der Komponente nicht auf die gewünschte Anzahl von Spalten ändern. (NPR-38688)

### Vorlageneditor {#sites-templateeditor-6514}

* Fehlt **[!UICONTROL Löschen]** und **[!UICONTROL Ausschneiden]** Schaltflächen in der Menüleiste in einer bearbeitbaren Vorlage nach einer `cq:actions` -Eigenschaft angepasst wurde. (NPR-38521)
* Wenn eine Komponente eine andere Komponente enthält, ist es nicht möglich, die Komponente innerhalb der Vorlagenstruktur zu löschen, da die **[!UICONTROL Löschen]** in der Menüleiste fehlt. (NPR-38585)

## Sling {#sling-6514}

* Die Anzahl offener Dateien in der Produktion stieg aufgrund eines Speicherlecks im Modul `DiscoveryLiteDescriptor` in `org.apache.sling.discovery.commons`, Version 1.0.20. (NPR-38288)
* Im Experience Manager von **[!UICONTROL Aktivitäten]** > **[!UICONTROL Diagnose]** bei der Auswahl von **[!UICONTROL Status-ZIP herunterladen]** > **[!UICONTROL Download]**. (NPR-38514)

## Übersetzungsprojekte {#translation-6514}

* Launch für Unterseiten, die als Verweis auf einer übergeordneten Seite hinzugefügt wurden, wurden nicht beworben, wenn die `isDeep` -Eigenschaft auf `false`. (NPR-38531)

## Benutzeroberfläche {#ui-6514}

* Bei Verwendung von **[!UICONTROL Alle auswählen]** > **[!UICONTROL Quick Publish]**, hat der Experience Manager nicht alle Assets veröffentlicht oder angezeigt, wie viele Assets in veröffentlicht würden. **[!UICONTROL Karte]** Ansicht oder **[!UICONTROL Liste]** anzeigen. (NPR-38546)
* Falsche Anzahl ausgewählter Assets wird für angezeigt. **[!UICONTROL Zu Sammlung hinzufügen]** in **[!UICONTROL Alle auswählen]** Fall. (NPR-38633)
* Deaktivierte Benutzer können weiterhin Sammlungen und Projekten hinzugefügt werden. (NPR-38651)
* Wenn Sie einen Filter löschen, ohne das Suchformular zu speichern, wird ein Fehler erzeugt. (NPR-38698)
* Die Sitzung eines Benutzers kann keine `ModifiableValueMap` -Instanz für die Gruppen, um die direkte Gruppenmitgliedschaft einzurichten. (NPR-38710)

## Workflow {#workflow-6514}

* JavaScript ES6 (ESMAScript6-Modus oder höher)-Kompilierungsunterstützung für die Minimierung der `/libs/cq/inbox/gui/components/inbox/clientlibs/commons.js` -Bibliothek. (NPR-38304)
* Nachdem der Workflow ausgeführt und die Prozessschritte abgeschlossen sind, wird derselbe Kommentar mehrmals wiederholt. (NPR-38364)

## Installieren [!DNL Experience Manager] 6.5.14.0 {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.14.0 erfordert [!DNL Experience Manager] 6.5. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Service Pack-Download ist auf Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen [!DNL Experience Manager] 6.5.14.0 auf einer der Autoreninstanzen, die Package Manager verwenden.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!NOTE]
>
>Adobe rät davon ab, die [!DNL Experience Manager] 6.5.14.0-Paket. <!-- UPDATE FOR EACH NEW RELEASE -->

### Installieren Sie das Service Pack auf [!DNL Experience Manager] 6,5 {#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager] -Instanz.

1. Laden Sie das Service Pack herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.14.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie **[!UICONTROL Paket hochladen]** , um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. Normalerweise tritt dieses Problem in [!DNL Safari] -Browser, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie automatisch installieren können [!DNL Experience Manager] 6.5.14.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwendung `cmd=install&recursive=true` damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.14.0 unterstützt nicht die Installation von Bootstraps. <!-- UPDATE FOR EACH NEW RELEASE -->

**Installation überprüfen**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in der [technische Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge an `Adobe Experience Manager (6.5.14.0)` under [!UICONTROL Installierte Produkte]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.12 oder höher (Webkonsole verwenden: `/system/console/bundles`). <!-- NPR-38747 -->

### Installieren [!DNL Experience Manager] Forms Add-On-Paket {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen, wenn Sie [!DNL Experience Manager] Forms.

<!-- 

Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

-->

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

Das UberJar für [!DNL Experience Manager] 6.5.13.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.13/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

>[!NOTE]
>
>Beachten Sie in Experience Manager 6.5.14.0, dass die UberJar-Version (6.5.13.0) mit der vorherigen Version identisch bleibt.

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

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
| Integrationen | Die **[!UICONTROL AEM Cloud Services-Opt-in]** Der Bildschirm wird nicht mehr unterstützt, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration aktualisiert in [!DNL Experience Manager] 6.5. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Es unterstützt die wachsende Rolle von Adobe Launch bei der Instrumentierung [!DNL Experience Manager] Seiten für Analysen und Personalisierung verwenden, ist der Opt-in-Assistent funktionell irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime] Integrationen über die entsprechenden [!DNL Experience Manager] Cloud-Services. |
| Connectoren | Der Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird nicht mehr unterstützt für [!DNL Experience Manager] 6.5. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THE LIST.
 -->

* [AEM Inhaltsfragment mit GraphQL-Indexpaket 1.0.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.5.zip)
Dieses Paket ist für Kunden erforderlich, die GraphQL verwenden. Dadurch können sie die erforderliche Indexdefinition hinzufügen, die auf den tatsächlich verwendeten Funktionen basiert.

* As [!DNL Microsoft® Windows Server 2019] unterstützt nicht [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] unterstützt keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie ein Upgrade [!DNL Experience Manager] -Instanz von 6.5 bis 6.5.10.0, können Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5, die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] und veröffentlichen Sie einen verschachtelten Ordner in [!DNL Brand Portal]. Der Titel des Ordners wird jedoch nicht aktualisiert in [!DNL Brand Portal] bis die Veröffentlichung des Stammordners erfolgt ist.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wenn die Adobe Target-Integration in [!DNL Experience Manager] über die Target Standard-API (IMS-Authentifizierung) und dann über den Export von Experience Fragments in Target werden falsche Angebotstypen erstellt. Anstelle des Typs &quot;Experience Fragment&quot;bzw. der Quelle &quot;Adobe Experience Manager&quot;erstellt Target mehrere Angebote mit dem Typ &quot;HTML&quot;bzw. der Quelle &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Registrierungsänderung abgeschlossen wird, um die Registrierung abzuschließen.

* Beim Versuch, Inhaltsfragmente oder Sites/Seiten zu verschieben/zu löschen/zu veröffentlichen, tritt ein Problem beim Abrufen von Inhaltsfragmentverweisen auf, da die Hintergrundabfrage fehlschlägt. d. h. die Funktionalität funktioniert nicht.
Um den korrekten Vorgang sicherzustellen, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten hinzufügen `/oak:index/damAssetLucene` (keine Neuindizierung erforderlich):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die in [!DNL Experience Manager] 6.5.14.0: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.14.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65140_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.14.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65140_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Support für Adobe kontaktieren](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

