---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: 21d0ba51297b4e90645a9ab64d98016598c0a2be
workflow-type: tm+mt
source-wordcount: '6485'
ht-degree: 77%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, May 29, 2025. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.23.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 22. Mai 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.23.0 enthalten ist {#what-is-included-in-aem-6523}

[!DNL Experience Manager] 6.5.23.0 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

<!--### Sites {#sites}

* A () -->

<!--
### [!DNL Assets]

* A ()
-->

### Forms {#forms-sp23}

Einige wichtige Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* [Barrierefreie Hyperlinks mit Stilen für gemischten Text in statischen PDFs](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/using-designer.pdf): Hyperlinks, die Stile für gemischten Text in statischen PDFs enthalten, werden jetzt als einzelnes barrierefreies Element getaggt. Diese Verbesserung vereinfacht die Tag-Baumstruktur, verbessert die Navigation der Sprachausgabe und unterstützt eine bessere Einhaltung der Barrierefreiheitsanforderungen.

* [Aktualisierte unterstützte Plattform-Matrix](/help/forms/using/aem-forms-jee-supported-platforms.md)

  Die neueste Version führt Aktualisierungen der unterstützten Plattformmatrix ein, um die Kompatibilität mit neueren Technologien sicherzustellen.

   * IBM® Content Manager Client 8.7

   * MongoDB Enterprise 7.0

   * MySQL 8.4

   * Microsoft® SQL Server 2022

   * Microsoft® SQL Server JDBC-Treiber 12.8

   * Red Hat® Enterprise Linux® 9 (Kernel 4.x, 64-Bit) 

* [Abgehärtete Dateianhang-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment): Als Sicherheitsmaßnahme verhindert die Komponente jetzt die Übermittlung von Dateien mit geänderten Erweiterungen, die versuchen, zulässige Dateitypprüfungen zu umgehen. Solche Dateien werden während der Übermittlung blockiert, um sicherzustellen, dass nur gültige Dateitypen akzeptiert werden.

<!--* **Two-Factor authentication with SAML for AdminUI** 

  AdminUI in AEM Forms JEE now supports two-factor authentication using Security Assertion Markup Language (SAML) single sign-on (SSO), providing stronger security and a seamless login experience for administrators, similar to what is available in HTML Workspace. 

#### New GA features in AEM Forms {#ga-aem-forms-sp23}

* A ()

#### New Beta features in AEM Forms {#beta-aem-forms-sp23}
-->

## Behobene Probleme im Service Pack 23 {#fixed-issues}

<!-- 6.5.23.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-6523}

#### Barrierefreiheit {#sites-accessibility-6523}

* Die Arbeitsflächen-Abschnitte auf den Seiten des AEM-Editors unterstützen jetzt den vollständigen Zugriff auf die Tastatur. Benutzende können Abschnittstitel und Schaltflächen zum Bearbeiten nur über die Tastatur aktivieren, ohne auf den Mauszeiger angewiesen zu sein. Diese Aktualisierung stellt die Einhaltung von WCAG 2.1.1 sicher und verbessert die Benutzerfreundlichkeit über Komponenten hinweg (z. B. Teaser-, Bild-, Karussell-, Layout-, Timewarp- und Anmerkungs-Modale). (SITES-25256) <!-- 6.5 LTS SP1 -->
* Es wurde ein Problem mit der Barrierefreiheit im AEM-Seiteneditor behoben, bei dem der Tastaturfokus nach dem Aktivieren von Schaltflächen wie „Persona“, „Warenkorb“ oder „Verlassen“ unerwartet auf den Anfang der demografischen Symbolleiste zurückgesetzt wurde. Der Fokus bleibt nun auf der aktivierten Schaltfläche, um eine konsistente Tastaturnavigation und Workflows für Bildschirmlesehilfen zu unterstützen. (SITES-25306)
* Es wurde ein kritisches Problem mit der Barrierefreiheit im AEM-Seiteneditor behoben, bei dem Elemente der Arbeitsfläche über mehrere Dialogfelder und Modale hinweg (z. B. Asset-Leiste oder Layout-Vorschau) nicht nur mit der Tastatur bedient werden konnten. Alle interaktiven Elemente der Arbeitsfläche unterstützen jetzt die ausschließliche Tastaturnavigation und gewährleisten so die Einhaltung des WCAG 2.1-Erfolgskriteriums 2.1.1 (SITE-25256).
* Es wurde ein Problem mit der Barrierefreiheit in der Sites-Admin-Benutzeroberfläche behoben, bei dem interaktive Listenelemente im Popup „Erstellen“ falsche ARIA-Rollen verwendeten. Elemente, die sich wie Links verhielten, wurden `role="listitem"` statt `role="menuitem"` zugewiesen, was gegen ARIA-Design-Muster verstieß und zu Problemen mit Bildschirmlesehilfen führte. Aktualisierungen stellen sicher, dass alle Listenkomponenten den richtigen semantischen Rollen entsprechen, um die Unterstützung von Tastatur und Hilfstechnologien zu verbessern. (SITES-24493)
* Es wurde ein Problem mit der Zuordnung von Barrierefreiheits-Labels für die Felder für Seitentitel und Tags behoben. Die Benutzeroberfläche von AEM ordnet Barrierefreiheits-Labels bei der Verwendung von Bildschirmlesehilfen wie JAWS nun den Feldern „Titel“ und „Seitentitel“ zu. Die Fehlerbehebung stellt das ordnungsgemäße Lesen von Labels sicher und verbessert die ADA-Konformität für Seitenerstellung, Eigenschaften und Verschiebungs-Workflows hinweg. (SITES-27149)
* Es wurde ein Problem mit der Barrierefreiheit bei der Tabellenidentifizierung im Dialogfeld „Berechtigungen“ behoben. Die Tabelle „Berechtigungen“ in AEM verwendet jetzt die richtigen ARIA-Rollen und -Attribute, um sicherzustellen, dass Bildschirmlesehilfen wie JAWS sie ordnungsgemäß als Tabelle identifizieren. Die Fehlerbehebung verbessert die Compliance mit Barrierefreiheit und stellt sicher, dass Benutzende genaue Navigations- und Inhaltsankündigungen erhalten. (SITES-27140)
* Fehlende visuelle Labels für Felder zur Kommentareingabe in der Timeline wurden korrigiert. Fehlende visuelle Label für Eingabefelder vom Typ „Kommentar“ unter dem Abschnitt „Timeline“ wurden korrigiert, um die Barrierefreiheit zu verbessern. Durch die Aktualisierung wird sichergestellt, dass Bildschirmlesehilfen die Feld-Labels korrekt ausgeben können. Dieses Erlebnis verbessert die Navigation in und Übermittlung von Formularen für alle Benutzenden, insbesondere für diejenigen, die auf Hilfstechnologien angewiesen sind. (SITES-26903)
* Der Tastaturzugriff für die Schaltfläche mit den Auslassungspunkten in Timeline-Kommentaren wurde korrigiert. Die Tastaturnavigation für die Schaltfläche mit den Auslassungspunkten (drei Punkte) neben den Kommentaren im Abschnitt „Timeline“ wurde aktiviert. Benutzende können jetzt über die Tabulatortaste auf die Schaltfläche zugreifen und mit ihr interagieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf eine ausschließliche Tastaturnavigation angewiesen sind. (SITES-26891)
* NVDA-/Narrator-Ankündigungen für Suchergebnisse in Auswahldialogfeldern wurden verbessert. Das Feld „Auswahl-Dialogfeld öffnen“ wurde aktualisiert, um anzugeben, ob Suchergebnisse bei der Verwendung von Bildschirmlesehilfen wie NVDA oder Narrator gefunden werden oder nicht. Diese Verbesserung hilft Benutzenden, die auf Hilfstechnologien angewiesen sind, das Ergebnis ihrer Suchaktionen zu verstehen, ohne visuelle Bestätigung zu benötigen. (SITES-26883)
* Die ARIA-Rolle für das Symbol mit den Auslassungspunkten neben dem Feld zur Kommentareingabe wurde korrigiert. Das Symbol mit den Auslassungspunkten (drei Punkte) neben dem Feld zur Kommentareingabe wurde aktualisiert, damit es die richtige ARIA-Rolle verwendet. Dadurch wird sichergestellt, dass Bildschirmlesehilfen das Element genau identifizieren können. Diese Verbesserung optimiert die Compliance mit Barrierefreiheit und das Erlebnis für Benutzende, die auf Hilfstechnologien angewiesen sind. (SITES-26881)
* Ungültige ARIA-Attribute in Komponenten der Coral-Benutzeroberfläche wurden korrigiert. Die Komponenten der Coral-Benutzeroberfläche wurden aktualisiert, um sicherzustellen, dass alle ARIA-Attribute gültige Werte verwenden, wodurch die Compliance mit Barrierefreiheit verbessert wurde. Insbesondere wurden Fälle behandelt, in denen fälschlicherweise ungültige Werte wie `aria-modal="dialog"` zugewiesen wurden. Durch diese Verbesserung können Bildschirmlesehilfen Elemente von Dialogfeldern korrekt interpretieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf Hilfstechnologien angewiesen sind. (SITES-26873)
* Verbesserte Sichtbarkeit und QuickInfos für Symbole in Reflow-Szenarien. Das Verhalten bei Umfließen wurde verbessert, um sicherzustellen, dass QuickInfos für **Download**, **Assets erneut verarbeiten** und **Checkout** korrekt angezeigt werden. Der Fokus wurde auf ein Problem mit der Barrierefreiheit gerichtet, bei dem Symbole und ihre Labels unsichtbar wurden, wenn die Viewport-Größe oder die Zoom-Einstellungen des Browsers geändert wurden. Diese Fehlerbehebung unterstützt Benutzende mit geringer Sehkraft, indem sie die Sichtbarkeit aufrechterhält und während des Reflusses korrekte Symbolbeschreibungen bereitstellt. (SITES-26871)

#### Admin-Benutzeroberfläche{#sites-adminui-6523}

Die URL-Dienstausnahme des universellen Editors mit fehlenden Externalizer-Endpunkten wurde behoben. Der URL-Dienst des universellen Editors verarbeitet jetzt fehlende Autoren- und Veröffentlichungs-Endpunkte sowie lokale Externalizer-Endpunkte, ohne Ausnahmen auszulösen. Benutzende mit Administratorrechten können den Seiteneditor auch dann erfolgreich öffnen, wenn einige Externalizer-Konfigurationen unvollständig sind. (SITES-28877)  <!-- LTS -->

#### Klassische Benutzeroberfläche{#sites-classicui-6523}

* Ein Problem in Dialogfeldern der klassischen Benutzeroberfläche, bei dem durch Umschalten einer Schaltfläche ein Textbereich ausgeblendet und bei nachfolgenden Klicks nicht erneut angezeigt wird. Die Fehlerbehebung stellt sicher, dass der Textbereich beim Umschalten ordnungsgemäß wieder angezeigt wird, sodass das erwartete Verhalten wiederhergestellt wird und Unterbrechungen der Workflows dynamischer Dialogfelder verhindert werden. (SITES-30230)
* Der Fehler der Bild-Asset-Suchfunktion der klassischen Benutzeroberfläche wurde nach dem Upgrade auf Service Pack 22 behoben. Die Bild-Asset-Suche in der klassischen Benutzeroberfläche verarbeitet jetzt Asset-Namen ordnungsgemäß, die Leerzeichen oder Sonderzeichen enthalten. Diese Aktualisierung stellt sicher, dass die Asset-Suche Dateinamen korrekt codiert, wodurch Suchfehler verhindert werden und Autorinnen bzw. Autoren Bild-Assets ohne Fehler finden und auswählen können. (SITES-29151)

#### [!DNL Content Fragments]{#sites-contentfragments-6523}

* Das Fehlschlagen des Validierungstests für `DeleteVariationIT.testUpdateBasic` wurde korrigiert. Der Test `DeleteVariationIT.testUpdateBasic` schlägt während der Ausführung der Validierung des Service Packs nicht mehr fehl. Mit dieser Fehlerbehebung wird das Problem einer fehlenden Textzuordnung in der JSON-Verarbeitungslogik behoben, wodurch die Teststabilität sichergestellt und unnötige Testunterbrechungen vermieden werden. (SITES-28022)
* AEM verhindert jetzt Leistungsbeeinträchtigungen durch falsch formatierte XMP-Metadaten in Bild-Assets. Assets, die ungültige oder nicht konforme XMP-Eigenschaftsnamen enthalten, z. B. solche mit numerischen Segmenten oder ungeeigneten Strukturen, lösen während der Verarbeitung keine wiederholten Warnprotokolle mehr aus. Das System filtert problematische Metadaten heraus, um sicherzustellen, dass die Erfassung und Validierung von Assets fehlerfrei abgeschlossen wird. (SITES-30683) <!-- AEM 6.5 LTS SP1 -->


<!-- #### [!DNL Content Fragments] - Admin{#sites-admin-6523}

* A () -->


#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-6523}

Andere Autorinnen und Autoren können Inhaltsfragmente selbst dann veröffentlichen, wenn sie von einer anderen Autorin oder einem anderen Autor ausgecheckt werden, was dem beabsichtigten Verhalten der Checkout-Funktion widerspricht. Diese Fehlerbehebung verhindert, dass andere Benutzende die Schaltflächen zum Veröffentlichen in der Authoring-Oberfläche sehen oder verwenden, wenn ein Inhaltsfragment ausgecheckt wird. (SITES-30578)  <!-- LTS -->

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6523}

Der GraphQL-QueryValidationError mit Inhaltsfragmentschemata wurde behoben. Durch die Aktualisierung des Pakets `cq-dam-cfm-graphql` werden Schemavalidierungsfehler bei der Verwendung von Inhaltsfragmentreferenzen korrigiert. Durch die Fehlerbehebung wird sichergestellt, dass GraphQL-Abfragen ordnungsgemäß funktionieren, ohne dass nach der Paketbereitstellung ein manuelles Neuausrichten oder eine erneute Veröffentlichung des Schemas erforderlich ist. (SITES-27001)  <!-- LTS -->


<!-- #### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6523}

* A () -->

<!-- #### [!DNL Content Fragments] - REST API{#sites-restapi-6523}

* A () -->


#### Komponentenkonsole{#sites-component-console-6523}

Verbesserungen beim Laden der Seite „Live-Nutzung von Komponenten“. Optimiert die Seite „Live-Nutzung von Komponenten“ in AEM, um zu verhindern, dass beim Scrollen durch große Datensätze leere Zeilen angezeigt werden. Benutzende, die Komponenten mit umfangreichen Nutzungsverweisen laden, können jetzt ohne unnötige Lücken oder leere Einträge kontinuierlich Daten laden. Dieses Erlebnis verbessert die Seitennavigation, die Tracking-Genauigkeit und die Verwaltungseffizienz beim Reporting zur Komponentennutzung. (SITES-26454)

#### Core-Backend{#sites-core-backend-6523}

* Der durch ungültige Asset-Namen verursachte Fehler bei der Auflistung von Assets in der Inhaltssuche wurde behoben. Die Inhaltssuche verarbeitet Asset-Namen jetzt korrekt mit nicht codierbaren Zeichen. Die Asset-Auflistung im Seiteneditor schlägt nicht mehr fehl oder gibt Ausnahmen aus, wenn Assets mit problematischen Namen gefunden werden. (SITES-28722)
* Ein Problem, bei dem die Komponente `SearchPathLimiter` übermäßige Protokolleinträge generierte, indem für jeden Aufruf Meldungen auf FEHLER-Ebene gedruckt wurden. Dieses Verhalten begann nach Service Pack 17 und führte aufgrund extrem hoher Protokollvolumen zu Leistungsproblemen. Durch die Fehlerbehebung wird die Protokollebene auf DEBUG herabgestuft, wodurch das Protokollrauschen deutlich reduziert und die Systemüberwachung und Diagnoseeffizienz verbessert wird. (SITES-29835)
* Falsch formatierte XMP-Metadaten haben bei der Verarbeitung von Bild-Assets im `ValidationDataServlet` einen Fehler ausgelöst. Die Fehlerbehebung stellt die konforme Verarbeitung von Metadaten sicher und vermeidet redundantes Parsen ungültiger Eigenschaften. (SITE-30683)  <!-- LTS -->


<!-- #### Core Components{#sites-core-components-6523}

* A () -->

<!-- #### Campaign integration{#sites-campaign-integration-6523}

* A () -->

<!-- #### Experience Fragments{#sites-experiencefragments-6523}

* A () -->

<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6523}

* A () -->


#### Launches{#sites-launches-6523}

* Die fehlerhafte Anzeige des Startdatums zwischen dem 25. und 31. Dezember wurde behoben. Die Launches-Benutzeroberfläche zeigt jetzt Datumsangaben zwischen dem 25. und 31. Dezember mit dem richtigen Jahr an. Die Fehlerbehebung stellt sicher, dass Datumsangaben das folgende Jahr nicht mehr falsch anzeigen, um Verwirrung bei der Planung und Terminierung von Kampagnen zu vermeiden. (SITES-28706)
* Fehlerhafte AEM Launch-Vorlagen nach dem Upgrade auf Service Pack 22 wurden behoben. AEM Launch-Vorlagen werden nach einem Upgrade auf Service Pack 22 jetzt korrekt geladen. Mit der Fehlerbehebung werden ungültige Daten in internen Launch-Konfigurationen korrigiert, sodass Benutzende Launches ohne Fehler oder fehlende Felder anzeigen, bearbeiten und erstellen können. (SITES-28504)


<!-- #### Link Checker{#sites-link-checker-6523}

* A () -->

<!-- #### MSM - Live Copies{#sites-msm-live-copies-6523}

* A () -->


#### Seiteneditor{#sites-pageeditor-6523}

* Das Problem beim Laden von AssetPicker bei niedrigeren Bildschirmauflösungen wurde behoben. AssetPicker lädt Assets jetzt korrekt, wenn Benutzende bei niedrigeren Bildschirmauflösungen (1728×1117 oder niedriger) scrollen. Beim Scrollen treten keine fehlenden Assets mehr auf, was das Asset-Management über verschiedene Geräte-Breakpoints hinweg verbessert. (SITES-28065)
* Fehlende Ankündigung der Bildschirmlesehilfe für Seitensperr- und Seitenentsperraktionen wurde behoben. Der Seiteneditor gibt jetzt die Meldung „Info: Die Seite wurde gesperrt/entsperrt“ korrekt aus, wenn Benutzende die Schaltfläche zum Sperren/Entsperren aktivieren. Diese Fehlerbehebung verbessert die Compliance mit Barrierefreiheit und stellt sicher, dass Bildschirmlesehilfen während der Seitenbearbeitung dynamische Aktualisierungen erhalten. (SITES-27143)
* Das Verhalten des Tastaturfokus für Komponentenaktionen beim Authoring in AEM wurde verbessert. Die Tastaturnavigation im AEM-Author-Tool wurde verbessert, um sicherzustellen, dass der Fokus nach Aktionen wie Konfigurieren, Löschen oder Konvertieren weiterhin auf der neu erstellten oder ausgewählten Komponente liegt. Zuvor wurde der Fokus an den Anfang der Seite verschoben, was zu Problemen mit der Barrierefreiheit führte. Diese Aktualisierung verbessert das Anwendererlebnis für Personen, die eine Tastatur und Hilfstechnologie verwenden. Hierzu wird der logische Fokusverlauf innerhalb des Bearbeitungs-Workflows beibehalten. (SITES-26549)
* Die Registerkartennavigation in Author-Dialogfeldern wurde verbessert. Verbessert die Tastaturnavigation in den AEM-Author-Dialogfeldern, indem Benutzende nach Erreichen des Bearbeitungsfelds „Beschreibung“ mit der Tabulatortaste fortfahren können. Zuvor blockierte eine Fokusfalle im Feld „Beschreibung“ die weitere Navigation, ohne spezielle Tastenkombinationen zu verwenden. Die Aktualisierung stellt sicher, dass Benutzende nur mit der Tabulatortaste nahtlos durch Felder navigieren können, was die Compliance mit Barrierefreiheit und das Anwendererlebnis verbessert. (SITES-26524)
* In AEM 6.5 Service Pack 22 wurde eine Regression eingeführt, die verhinderte, dass Benutzende Leerzeichen in Launch-Titel einfügen konnten. Durch die Fehlerbehebung wird die Möglichkeit zur Verwendung von Leerzeichen wiederhergestellt, sodass Teams Launch-Namen entsprechend dem erwarteten Verhalten flexibler definieren und organisieren können. (SITES-29414)
* Es wurde ein Problem bei der Größenanpassung für Komponenten in Layout-Containern nach dem Ein- und Ausblenden behoben. Der Seiteneditor berechnet Spaltenwerte jetzt korrekt, nachdem ein Layout-Container ein- oder ausgeblendet wurde. Benutzende können die Größe von Komponenten ohne Fehler ändern, und Spalten werden bei Aktionen zur Größenanpassung korrekt angezeigt. (SITES-28463)
* Die falsche Platzierung der Schaltfläche für die Inhaltsstruktur im Seiteneditor wurde behoben. Der Seiteneditor positioniert die Konfigurationsschaltfläche für die Inhaltsstruktur jetzt korrekt unter dem vorgesehenen Dialogfeld „Head-Teaser“ anstelle des falschen Abschnitts. Durch die Fehlerbehebung wird das CSS für das Dialogfeld „Inhaltsstruktur“ so aktualisiert, dass `top:0` anstelle von `bottom:0` verwendet wird, um eine ordnungsgemäße Platzierung der Schaltfläche sicherzustellen. (SITES-28448)


<!-- #### Replication{#sites-replication-6523}

* A () -->


#### Rich-Text-Editor{#sites-rte-6523}

Korrigieren von unerwarteten `<br>`-Tags im Rich-Text-Editor mit dem Einfügemodus für normalen Text. Der Rich-Text-Editor verarbeitet Vorgänge zum Ausschneiden und Einfügen beim Verwenden von `defaultPasteMode` für normalen Text jetzt korrekt. Die Fehlerbehebung verhindert das Einfügen unerwarteter `<br>`-Tags, wenn Benutzende Text in RTE-Feldern ausschneiden und einfügen, und stellt so eine saubere Formatierung während der Inhaltsbearbeitung sicher. (SITES-27780)

#### Universeller Editor {#sites-universal-editor-6523}

* Wenn mehrere Anfragen, die den Abfrageparameter enthalten, an AEM gesendet werden, wird das Anmelde-Token-Cookie möglicherweise nicht rechtzeitig zurückgegeben, was zu einem Fehler bei der Anmeldung führen kann. (SITES-30659)  <!-- LTS -->
* Um die Kompatibilität und Unterstützung mit SAML-Handlern sicherzustellen, müssen Sie die Eigenschaft `service.ranking` so konfigurieren, dass der `Query Token Auth`-Handler *vor* dem `SAML Auth`-Handler ausgeführt wird. (SITES-29684)

### [!DNL Assets]{#assets-6523}

* Die folgenden Probleme treten auf der [!DNL AEM] On-Premise-Navigationsseite (6.5.22.0) auf, nachdem Sie ![Assets](/help/assets/assets/Smock_Asset_18_N.svg)**[!UICONTROL Assets ]**ausgewählt haben, zum Ordner**[!UICONTROL  Adobe Stock durchsuchen ]**navigiert sind und ein Stockbild ausgewählt haben:
   * Das ausgewählte Stockbild kann nicht lizenziert und gespeichert werden, da durch Klicken auf **[!UICONTROL Lizenzieren und speichern]** eine leere Dropdown-Liste angezeigt wird.
   * Wenn Sie das Stockbild auswählen oder die URL der Stock-Seite erneut eingeben, werden Sie zur [!DNL AEM]-Startseite weitergeleitet, wodurch der Zugriff auf das Adobe Stockbild verhindert wird. (ASSETS-48687)
* Probleme beim Verwalten von Ordnern, wenn der Name des Ordners einen `/` auf der Navigationsseite von [!DNL AEM] On Premise (6.5.22.0) enthält. (ASSETS-46740)
* In [!DNL AEM] 6.5 wird die Seite mit Asset-Details aufgrund einer hohen Speicherauslastung nicht über die Ansicht ![Sammlung](/help/assets/assets/Smock_Collection_18_N.svg)**[!UICONTROL Sammlungen ]**geladen. (ASSETS-46738)
* Integrationsprobleme mit [!DNL InDesign], da der Dienst `Day CQ DAM Mime Type OSGI` [!DNL InDesign]-Dateien fälschlicherweise als `x-adobe-indesign` statt als `x-indesign` identifiziert. (ASSETS-45953)
* Das Sitzungsleck in [!DNL AEM 6.5.21] wurde auf den vorkonfigurierten Workflow-Schritt **[!UICONTROL Geplante Veröffentlichung in Brand Portal]** zurückverfolgt. (ASSETS-44104)
* Fehler vom Typ **[!UICONTROL Unzureichender Arbeitsspeicher (OOM)]** werden bei der Verarbeitung und Veröffentlichung von Bildern in [!DNL AEM] angezeigt. Dieses Problem ist auf veraltete Methoden in Workflows zurückzuführen, z. B. **[!DNL Dam Asset update]** und **[!DNL Dynamic Media: Reprocess assets]**. (ASSETS-43343)
* Nachdem Sie eine kleine Änderung vorgenommen haben, z. B. den Titel aktualisiert haben, öffnen Sie die **[!DNL Connected Assets configuration]** erneut und speichern sie erneut in der lokalen Sites-Instanz. Die Remote-Instanz verliert dann ihre Verbindung zur lokalen Instanz. Daher kann keine Kommunikation mit der lokalen Sites-Instanz hergestellt werden. (ASSETS-44484)
* Wenn in [!DNL AEM 6.5.21] ein Asset-Upload in der Listenansicht abgebrochen und ein zweiter Upload durchgeführt wird, zeigt [!DNL AEM] den Fehler **[!UICONTROL 0 von NaN Assets hochgeladen]** an. (ASSETS-44124)

#### [!DNL Dynamic Media]{#assets-dm-6523}

Es wurde eine Metadateneigenschaft (`jcr:content/metadata/dam:scene7SmartCropStatus`) zu Assets hinzugefügt, um fehlgeschlagene Generierungen von intelligenten Zuschnitten zu identifizieren. Ermöglicht die effiziente Suche, Filterung und Neuverarbeitung von Assets mit Problemen mit dem intelligenten Zuschnitt durch manuelle oder automatisierte Workflows. (ASSETS-46237)

#### [!DNL Dynamic Media] – Hybridmodus {#assets-dm-hybrid-6523}

##### Dynamic Media – Hybrid-Add-on-Paket (AEM 6.5.23 und höher)

Ab AEM 6.5 Service Pack 23 ist ein neues Add-on-Paket für den Hybridmodus von Dynamic Media verfügbar. Dieses Paket enthält das `cq-scene7-imaging`-Paket, das speziell mit dem Hybrid-Ausführungsmodus von Dynamic Media kompatibel ist.

**Wichtige enthaltene Fehlerbehebung**

Es wurde ein Problem in den Hybrid-Bereitstellungen von Dynamic Media behoben, bei dem Aktualisierungen des `catalog.expiration`-Parameters unter `/conf/global/settings/dam/dm/imageserver` nicht auf den Server- oder Autoren-URLs widergespiegelt wurden, obwohl die Replikation ohne Fehler durchgeführt wurde. Die Aktualisierung stellt konsistente Ablaufwerte zwischen CRX/DE, der Server-Antwort und den öffentlichen Bereitstellungs-URLs sicher. Dadurch werden wiederum das Cache-Verhalten und die Zuverlässigkeit von Bildumwandlungen verbessert. (ASSETS-44837)

**Wichtige Aspekte**

* Das `cq-scene7-imaging`-Paket in der Basisinstallation von AEM 6.5.23 (und höher) ist *nicht kompatibel* mit dem Hybrid-Ausführungsmodus von Dynamic Media.
* Die Installation von Service Pack 23 (und höher) allein *führt nicht automatisch zur Aktualisierung* des vorhandenen `cq-scene7-imaging`-Pakets auf AEM-Instanzen, die für Hybrid-Bereitstellungen (`-r dynamicmedia`-Ausführungsmodus) von Dynamic Media konfiguriert sind.

**Wann muss das Hybrid-Add-on-Paket installiert werden?**

* Beim direkten Upgrade auf AEM 6.5.23 (und höher) von AEM 6.5.19 oder früher.
* Wenn Sie spezifische Fehlerbehebungen für die Hybrid-Funktionalität von Dynamic Media benötigen.
* Bei der Bereitstellung einer neuen Hybrid-Instanz für Dynamic Media direkt von AEM 6.5 GA (allgemeine Verfügbarkeit) auf Service Pack 23 (und höher).

**Herunterladen des Hybrid-Add-on-Pakets**

Das Hybrid-Add-on-Paket ist ab Donnerstag, dem 22. Mai 2025, mit der offiziellen AEM-Version 6.5.23 in der Adobe-Software-Verteilung öffentlich verfügbar. Benutzende finden es, indem sie in der Software-Verteilung nach **AEM 6.5 Dynamic Media Hybrid-Add-on-Paket** suchen.


### [!DNL Forms]{#forms-6523}

#### Forms Designer

* Wenn ein(e) Benutzende(r) die Daten für eine XFA-basierte PDF mit der exportDataAPI exportiert, weist die resultierende XML Diskrepanzen im Vergleich zu den XML-Daten auf, die manuell mit Acrobat Reader exportiert wurden. In der Ausgabe fehlten Werte einiger Felder im Vergleich zur Ausgabe aus Acrobat Reader. (LC-3922791)

* Wenn Sie in AEM Forms 6.5.22.0 eine getaggte PDF mit dem Ausgabe-Service in Workbench generieren, wird ein unerwartetes Beschriftungs-Tag unter dem Referenz-Tag in einem Inhaltsverzeichniselement hinzugefügt. (LC-3922756)

* Wenn Benutzende Feldbeschriftungen mit Ausrichtung unten oder rechts in AEM Forms Designer platzieren, enthält die Tag-Struktur nur die Beschriftung ohne den entsprechenden Wert, was zu unvollständigen Barrierefreiheits-Tags führt. (LC-3922619)

* Beim Upgrade von AEM Forms 6.5 Service Pack 6 auf AEM Forms Service Pack 20 werden die QR-Codes in generierten PDF-Dateien unlesbar. Der Alternativtext für die QR-Codes schlägt auch die Barrierefreiheitsprüfung fehl, was sich auf die Kompatibilität der Bildschirmlesehilfen auswirkt. (LC-3922551)

* Wenn ein(e) Benutzende(r) einen Brief in der Agent-Benutzeroberfläche auf AEM Forms Service Pack 18 rendert, kann der Inhalt aufgrund der FormService.render()-API nicht korrekt angezeigt werden. (LC-3922461)

#### Forms

* Wenn in AEM Forms „Rich Text für Titel zulassen“ im Stammbereich aktiviert ist, wird durch „Titel aus Datensatzdokument ausschließen“ in einem verschachtelten Bereich der Titel des Stammbereichs falsch ausgeblendet. Dies erfolgt im generierten Datensatzdokument. (FORMS-19696)

* Das System ignoriert die benutzerdefinierten `sling:resourceType`, die über `aem:afProperties` in einem JSON-Schema in AEM 6.5 zugewiesen wurden. Der benutzerdefinierte Ressourcentyp wird beim Rendern ignoriert. (FORMS-19691)

* Wenn ein Benutzer ein adaptives Formular mit vorausgefüllten Anhängen unter Verwendung von URIs sendet, schlägt die Formularübermittlung mit einer Null PointerException aufgrund fehlender Binärdaten fehl. (FORMS-19371) (FORMS-19486)

* Wenn ein(e) Benutzende(r) eine PDF unter dem Abschnitt &quot;Forms und Dokumente“ in AEM 6.5 Forms hochlädt, funktioniert die Zeitleisten-Funktion nicht mehr. (FORMS-19407)(FORMS-19234)

* Wenn ein(e) Benutzende(r) Dateien mit der vordefinierten Dateianhangskomponente in AEM Forms hochlädt, werden Sicherheitslücken identifiziert. Dieses Problem führt möglicherweise dazu, dass der Übermittlungsprozess durch nicht autorisierte Entitäten abgefangen wird. (FORMS-19271)

* Wenn ein(e) Benutzende(r) ein vorkonfiguriertes adaptives Formular in AEM Forms so konfiguriert, dass automatisch ein Datensatzdokument (DoR) generiert wird, wird im Feld „Titel“ in den Dokumenteigenschaften von Acrobat Reader der erfasste DoR-Titel nicht angezeigt. Standardmäßig wird der Formulartitel nicht anstelle des Dateinamens angezeigt. (FORMS-19263)

* Wenn ein(e) Benutzende(r) eine interaktive Kommunikation in der Benutzeroberfläche für Agenten öffnet, können die vorausgefüllten Daten nicht vollständig gelöscht werden. Nach dem Entfernen werden sie automatisch mit denselben Daten erneut ausgefüllt. (FORMS-19151)

* Wenn ein(e) Benutzende(r) in der Benutzeroberfläche für Agenten ein Datumsfeld in der Vorschau anzeigt, ändert sich das Datum unerwartet. Dieses Problem tritt aufgrund von Zeitzonendiskrepanzen zwischen der UTC-Einstellung der virtuellen Maschine und der Datumsinterpretation des Systems auf. (FORMS-19115)

* Wenn ein Benutzer ein Formular sendet, können Dateianhänge dupliziert werden, was zu mehreren Uploads derselben Datei führt. (FORMS-19045)(FORMS-19051)

* Das Hinzufügen von Koordinatoren zu Richtliniensätzen in AEM 6.5 Document Security schlägt sowohl in Produktions- als auch in niedrigeren Umgebungen fehl. (FORMS-18603, FORMS-18212, FORMS-19697)

* Wenn ein(e) Benutzende(r) im Desktop-Modus mit einem leeren Feld in AEM Forms Service Pack 22 auf das Symbol „Datumsauswahl-Kalender“ klickt, tritt aufgrund der nicht definierten Variablen _$focusDate ein Fehler auf, der die zugehörigen benutzerdefinierten Skripte stört. (FORMS-18483)(FORMS-18268)

* Wenn ein Kunde in AEM Forms Service Pack 19 (6.5.19.0) eine Vorschau eines Briefs anzeigt, werden im Feld „Betrag in Worten“ die Zahlenwerte nicht korrekt angezeigt oder aktualisiert, was zu einer falschen Ausrichtung und fehlenden Leerzeichen im Inhalt führt. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848, FORMS-19614, LC-3922004)

* Wenn ein Kunde einen gespeicherten Brief in AEM Forms 6.5 SP19 auf RHEL in der Vorschau anzeigt, werden der Inhalt falsch ausgerichtet, Leerzeichen fehlen und unerwartete Zeichen wie „x“ angezeigt. (FORMS-18422)(FORMS-17641)

* Wenn ein(e) Benutzende(r) in AEM Forms zwischen Registerkarten navigiert, reagiert die Auswahl von Komponenten auf der ersten Registerkarte nicht mehr. (FORMS-18345)

* Wenn ein(e) Benutzende(r) in AEM Forms 6.5.21.0 eine HTML-Datei mithilfe der Option WebToPDF in PDF konvertiert, fehlt in der Ausgabe-PDF der Kopfzeilenabschnitt einschließlich der Metadaten- und Titel-Tags. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)

* Wenn in der AEM JEE Process Manager-SDK ein(e) Benutzende(r) die retryAction(long actionOid)-Methode aufruft, versucht das System fälschlicherweise die erste Aktion in der Tabelle tb_action_instance erneut. Dieser Workflow tritt auch dann auf, wenn eine bestimmte Aktions-ID angegeben wird oder die ID null ist, was zu unbeabsichtigtem Verhalten führt. (FORMS-18187)

* Nach der Aktualisierung auf SP22 treten Probleme auf, bei denen die gespeicherten Entwurfs- und Übermittlungsfunktionen fehlschlagen, ohne dass eine Fehlermeldung angezeigt wird. (FORMS-18069)

* In AEM 6.5.21.0 verhindert der Übergang von XSD-basierten Foundation-Komponenten zu Kernkomponenten die Implementierung dateiübergreifender Verweise in JSON-Schemata, was sich auf die Migration von adaptiven Forms auswirkt. (FORMS-18065)

* Wenn ein(e) Benutzende(r) in der Benutzeroberfläche für Agenten einen Brief in der Vorschau anzeigt, wird im Datumsfeld aufgrund von IC-Zeitkonvertierungsproblemen ein falscher Wert angezeigt. Diese Diskrepanzen ergeben sich aus Zeitzonenunterschieden zwischen der VM-Umgebung und der Zeitinterpretation des Systems (UTC versus lokale Zeit). (FORMS-17988) (FORMS-17248)

* Bei der Vorschau von Briefen mithilfe von Benachrichtigungs-IC-Vorlagen in AEM Forms variieren die Generierungszeiten von PDF erheblich, von 1,5 Sekunden bis mehr als 10 Sekunden, selbst auf demselben Server. Diese Inkonsistenz wirkt sich auf geschäftskritische Workflows aus. (FORMS-17951)

* Wenn ein Benutzer ein Scribble-Signaturobjekt in einem adaptiven Formular mithilfe der Option „Datenquellen“ an eine XDP bindet, können Änderungen nicht gespeichert werden. Der Grund dafür sind anhaltende Fehler bei der Validierung des Seitenverhältnisses, selbst bei Verwendung gültiger Werte. (FORMS-17587)

* Wenn ein(e) Benutzende(r) eine bestimmte XDP-Datei mit vielen ausgeblendeten Feldern für Dokumentfragmente verwendet, erstellt AEM CRX-Knoten mit der `cm:optional`-Eigenschaft „false“, was dazu führt, dass die Übermittlung der interaktiven Kommunikation (IC) fehlschlägt. (FORMS-17538)

* Bei der Vorschau eines Briefs in AEM Forms 6.5.19.0 kann das numerische Feld negative Werte nicht korrekt verarbeiten, wenn Zifferngrenzen für Lead und Frac definiert sind. Dieses Problem tritt aufgrund der Verwendung von parseFloat auf, das das Minuszeichen als Teil der Zahl behandelt. (FORMS-17451)

* In AEM Forms 6.5 wird bei der Vorschau eines Briefs die Verwendung des Platzhalters &quot;*&quot; in der Datei &quot;Adobe.json“ bemerkt, was Bedenken hinsichtlich des Zwecks und einer möglichen Änderung aufwirft. (FORMS-17317)

* Wenn ein(e) Benutzende(r) eine Bildschirmlesehilfe im `Apply for a Fixed Rate Saver joint account` verwendet, werden die Überschriften fälschlicherweise als `clickable` angekündigt, was zu Problemen mit der Barrierefreiheit führt. (FORMS-17038)

* Wenn ein Formular eingebettet ist, fehlt im generierten iframe ein title-Attribut, was zu einem Problem mit der Barrierefreiheit führt. (FORMS-17010)

* Das Herunterladen eines Formulars über die Forms Manager-Benutzeroberfläche umfasst immer verknüpfte Abhängigkeiten wie Designs und Fragmente. (FORMS-15811)

* Wenn ein Benutzer auf Mobilgeräten (iOS und Android™) auf das Formular zugreift, sind die Schaltflächen „Weiter“ und „Zurück“ auf der ersten Seite deaktiviert. Die Bildschirmlesehilfe erkennt sie jedoch nicht als deaktiviert. (FORMS-15773)

* Wenn ein(e) Benutzende(r) ein großes Formular mit aktivierten Fragmenten und verzögertem Laden speichert, können keine Entwürfe abgerufen werden, wodurch der Workflow unterbrochen wird. (FORMS-19890, FORMS-19808)

#### FORMS JEE

* Wenn ein(e) Benutzende(r) die Datenbank in AEM Forms neu konfiguriert, schlägt die Verbindung aufgrund von hartcodierten Parametern fehl. (FORMS-19568, FORMS-17621)

* Wenn ein Benutzer AEM 6.5 mit MySQL 8.4 unter Verwendung der partiellen Turnkey-Methode einrichtet, erkennt der LiveCycle Configuration Manager (LCM) den erforderlichen MySQL-Connector-Treiber nicht. Dies führt dazu, dass der Datenbankverbindungstest und die Einrichtung fehlschlagen. (FORMS-19442)

* Wenn ein(e) Benutzende(r) LCM mit JDBC 12.8.1 unter JRE 11 in einer JEE-Umgebung ausführt, schlägt das Setup aufgrund von Inkompatibilitätsproblemen fehl. (FORMS-19276)

* Wenn ein(e) Benutzende(r) eine Aufgabe in AEM On-Premise öffnet, führt das System das Workspace-Startaktionsprofil anstelle des zugewiesenen Benutzerprofils aus. (FORMS-19065)

* Wenn ein(e) Benutzende(r) die retryAction(long actionOid)-Methode im AEM JEE Process Manager verwendet, tritt ein unerwartetes Verhalten auf. (FORMS-18357)(FORMS-18187)

* Auf AEM Forms 6.5.21.0 schlägt die PDFG-Konvertierung mit dem folgenden Fehler fehl: (FORMS-16851)(FORMS-14613)

#### Formular-Captcha {#forms-captcha-6523}

* reCAPTCHA-Warnungen in adaptiven Formularen wurden durch Aktualisierung der Übermittlungsfehler-Codes auf 400 verbessert. Außerdem wurden Protokollwarnungen verfeinert, um zwischen Timeouts, Abläufen und Fehlern bei der Bot-Erkennung zu unterscheiden und so die Genauigkeit bei der Fehlerbehebung und Systembeobachtung zu verbessern. (FORMS-19240)
* Eine nicht geschlossene `ResourceResolver`-Instanz in `ReCaptchaConfigurationServiceImpl` wurde geschlossen, um potenzielle Ressourcenlecks zu vermeiden und die Systemstabilität bei der Verwendung von reCAPTCHA-Integrationen in AEM Forms zu verbessern. (FORMS-19242)
* Die Verarbeitung von CAPTCHA-Konfigurationen für AEM Forms wurde verbessert, indem sichergestellt wurde, dass an jedes Formular die richtige Konfiguration gebunden ist, wenn mehrere Einträge im Ordner `/conf/global` vorhanden sind. Verhindert die unbeabsichtigte Verwendung falscher CAPTCHA-Einstellungen, wenn der Konfigurations-Container nicht explizit ausgewählt ist. (FORMS-19239)

<!--
#### XMLFM {#forms-xmlfm-6523}

* A () -->

<!--
#### [!DNL Adaptive Forms] {#adaptive-forms-6523}

* A () -->

<!--
#### [!DNL Forms Designer] {#forms-designer-6523}

* A () -->


### Foundation {#foundation-6523}

* Es wurde ein Problem mit Coral-Warnbannern behoben, bei dem nach dem Upgrade auf Service Pack 21 die Textfarbe nicht mehr schwarz, sondern weiß angezeigt wurde. Stellt sicher, dass die richtige Formatierung angewendet wird, um den richtigen Kontrast und die Lesbarkeit von Warnhinweisen über die gesamte Benutzeroberfläche hinweg zu gewährleisten. (NPR-42359)
* Es wurde Unterstützung für die OAuth-Integration in der Smart-Tags-Konfiguration hinzugefügt, um sie an die Abschaffung von JWT (JSON Web Token) anzupassen. Stellt die kontinuierliche Funktionalität der Smart-Tags-Funktionen mithilfe aktualisierter Authentifizierungsmethoden sicher. (NPR-42296)

#### Apache Felix {#foundation-apachefelix-6523}

Es wurde eine NullPointerException behoben, die beim Hochladen von Private Key-Dateien in ein Eigenschaftsfeld vom binären Typ in CRX auftrat. Dadurch wird die Kompatibilität wiederhergestellt, die in Service Pack 16 vorhanden war. Ermöglicht sichere Workflows zum Hochladen von Schlüsseldateien in AEM Managed Services ohne Serverfehler oder Unterbrechungen der Zertifikatsverlängerungsprozesse. (CQ-4359178)


<!--
#### Campaign{#foundation-campaign-6523}

* A () -->

<!--
#### Cloud Services{#foundation-cloudservices-6523}

* A () -->

<!--
#### Communities {#foundation-communities-6523}

* A () -->

<!--
#### Content distribution{#foundation-content-distribution-6523}

* A () -->

<!--
#### CRX {#foundation-crx-6523}

* A () -->


#### Granite{#foundation-granite-6523}

* Es wurden OSGi-Abhängigkeitszyklen zwischen Apache Sling-Skriptdiensten behoben, die nach dem Upgrade auf Service Pack 21 zu Verzögerungen oder Fehlern beim Laden von HTML-Seiten führten. Interne Dienstverweise wurden aktualisiert, um zyklische Abhängigkeiten zwischen `SightlyScriptingEngineFactory` und zugehörigen Komponenten zu beseitigen und die Zuverlässigkeit sowie das Startverhalten der Scripting-Engine zu verbessern. (GRANITE-56808)
* Aktualisierte JS-Skripte verwenden in Apache Sling Skripte, um sie nur bei Bedarf und nicht eifrig beim Start zu laden, wodurch Thread-Konflikte vermieden werden und das Risiko verringert wird, dass Veröffentlichungs-Server beim Laden nicht mehr reagieren. Diese Änderung verbessert die Server-Stabilität und die Antwortzeiten in Szenarien mit hohem Traffic, indem die durch eine frühe Skriptauflösung verursachte Ressourcensperrung verhindert wird. (GRANITE-56611)
* Es wurde ein Problem in AEM Omnisearch behoben, bei dem Platzhalter für Eingabefelder fälschlicherweise als Labels angezeigt wurden, was zu visueller Verwirrung führte. Stellt ein ordnungsgemäßes Rendern von Platzhaltern über Filterfelder hinweg sicher und wahrt ein konsistentes und barrierefreies Formularverhalten. (GRANITE-51791)
* Es wurde ein Server-Fehler behoben, der bei der Auswahl von mehr als 30 CFMs (Content Fragment Models, Inhaltsfragmentmodellen) mit Mehrfachfeldverweisen im Inhaltsfragmentmodell-Editor ausgelöst wurde. Die Filtervorschlagskomponente wurde verbessert, um POST-Vorgänge zu unterstützen. Diese Funktion ermöglicht die ordnungsgemäße Verarbeitung großer Referenzsätze während der Erstellung von Inhaltsfragmenten und verbessert die Stabilität für Modellkonfigurationen mit hohem Volumen. (GRANITE-57164)
* Es wurde ein Problem in CFMs behoben, bei dem durch Klicken neben ein Kontrollkästchen dessen Status unbeabsichtigt geändert wurde. Die Stile wurden aktualisiert, sodass die Klick-Aktivierung ausschließlich auf das Kontrollkästchenelement beschränkt bleibt. So werden versehentliche Benutzerinteraktionen verhindert und die Benutzerfreundlichkeit und Barrierefreiheit von Formularen verbessert. (GRANITE-52384)


<!--
#### Integrations{#foundation-integrations-6523}

* A () -->


#### Jetty{#foundation-jetty-6523}

Es wurde ein Problem behoben, bei dem die SNI-Validierung API-Aufrufe über HTTPS für AEM-Kundinnen und -Kunden blockierte, die Dispatcher-SSL-Konfigurationen mit benutzerdefinierten Host-Headern verwenden. Führt eine Option zur Deaktivierung der SNI-Validierung als Teil der Jetty-Konfiguration ein, um die Kompatibilität mit bestimmten Reverse-Proxy-Setups zu ermöglichen, wenn `mod_proxy` nicht praktikabel ist. (NPR-42614)


<!--
#### Localization{#foundation-localization-6523}

* A () -->

<!--
#### Oak {#foundation-oak-6523}

* A () -->


#### Platform{#foundation-platform-6523}

* Es wurde ein inkonsistentes Verhalten beim Zusammenführen von Tags korrigiert, indem sichergestellt wurde, dass der zusammengeführte Tag-Wert über Assets hinweg immer korrekt angezeigt wird, unabhängig davon, ob Tags inline oder über die standardmäßige Tag-Erstellungsmethode erstellt wurden. Verhindert, dass Restwerte aus Feldern vom Typ `EN:title` zusammengeführte Tag-Anzeigen überschreiben. (CQ-4358812)
* Die wiederholte Kodierung von kaufmännischen Und-Zeichen in Tag-Werten im Dialogfeld zur Tag-Bearbeitung wurde korrigiert. Verhindert, dass bei jedem Speichern zusätzliche „&amp;“-Entitäten angehängt werden, sodass Tag-Werte über Bearbeitungen hinweg sauber und konsistent bleiben und Anzeigefehler in erstellten Inhalten vermieden werden. (CQ-4359048)
* Es wurde ein Fehler vom Typ `ClassCastException` behoben, der den E-Mail-Versand beim Übermitteln adaptiver Formulare in AEM 6.5, das auf WebSphere® ausgeführt wird, verhinderte. Die Fehlerbehebung ermöglicht eine erfolgreiche E-Mail-Übertragung, indem sie die Kompatibilität zwischen `com.sun.mail.handlers.text_plain` und `java.activation.DataContentHandler` sicherstellt und an die E-Mail-Handler-Konfiguration anpasst, die von WebSphere®-Umgebungen erwartet wird. (NPR-42500)
* Die Fehlerbehandlung in Package Manager wurde verbessert, indem sichergestellt wurde, dass AEM eine eindeutige Meldung zeigt, wenn die Installation fehlschlägt und die Fehlerantwort ansonsten leer ist. Diese Fehlerbehebung verhindert stille Fehler und beschleunigt das Debugging bei der Paketbereitstellung. (NPR-42375)

<!--
#### Security{#foundation-security-6523}

* A -->

<!--
#### Sling{#foundation-sling-6523}

* A () -->


#### Übersetzung{#foundation-translation-6523}

Es wurde ein Problem mit der NullPointerException (NPE) behoben, das beim Aktualisieren von Inhaltsfragmenten in Workflows mit **Sprachkopie aktualisieren** ausgelöst wurde. Durch diese Fehlerbehebung wird sichergestellt, dass Workflows beim Bearbeiten von Inhalten, die mit Übersetzungsreferenzen verknüpft sind, nicht in den Status „Fehlgeschlagen“ übergehen oder im Status „Wird ausgeführt“ stecken bleiben. (NPR-42115)

#### Benutzeroberfläche{#foundation-ui-6523}

Fügt den Schaltflächen der Dialogfelder in der Coral-Benutzeroberfläche fehlende Attribute vom Typ `title` hinzu, wie **Fertig** und **Abbrechen** in Dialogfeldern zum Bearbeiten von Komponenten, um die Barrierefreiheit zu verbessern und eine automatisierte Validierung zu ermöglichen. Stellt sicher, dass Schaltflächen die erwarteten Attribute im gesamten Markup-Rendering beibehalten, sodass Fehler in Selenium-basierten Benutzeroberflächentests verhindert werden. (NPR-42412)

#### WCM{#foundation-wcm-6523}

Es wurde ein Problem behoben, das verhinderte, dass Seiten zu Übersetzungsaufträgen hinzugefügt wurden, wenn **Sprachkopie aktualisieren** in Umgebungen mit Service Pack 19 oder höher verwendet wurde. Stellt sicher, dass die Übersetzungs-Workflows erwartungsgemäß ablaufen, und ermöglicht so eine ordnungsgemäße Seitenübertragung zwischen Sprachkopien ohne manuelles Eingreifen. (CQ-4357929)

#### Workflow{#foundation-workflow-6523}

Es wurde ein Problem im `EmailNotificationServiceProcessor` behoben, bei dem die `getSegmentId`-Methode nach der Hotfix-Bereitstellung `null` zurückgibt, wodurch E-Mail-Trigger während der Workflow-Verarbeitung fehlschlugen. Stellt die richtige Logik zur Auflösung der Segment-ID wieder her, indem sichergestellt wird, dass der Prozessor die erforderlichen `SegmentInfo`-Werte abruft, um E-Mail-Benachrichtigungs-Workflows in allen AEM-Instanzen zu unterstützen. (CQ-4359755)


## Installieren von [!DNL Experience Manager] 6.5.23.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.23.0 erfordert [!DNL Experience Manager] 6.5. Detaillierte Anweisungen finden Sie in der [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md). <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.23.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.23.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Installieren des Service Packs für [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von dem [Software-Verteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld in der Benutzeroberfläche von Package Manager wird während der Installation des Service Packs manchmal beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.23.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.23.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.23.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.20 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE. CHECK WITH SAMEER DHAWAN -->

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

UberJar für [!DNL Experience Manager] 6.5.23.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.22/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.23</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.



## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Unter [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md/) finden Sie eine detaillierte Liste aller Funktionen, die für AEM 6.5 eingestellt oder entfernt wurden.

### SPA-Editor {#spa-editor}

Der [SPA-Editor](/help/sites-developing/spa-overview.md) wird ab Version 6.5.23 von AEM 6.5 für neue Projekte nicht mehr unterstützt. Für bestehende Projekte wird er weiterhin unterstützt, sollte allerdings nicht mehr für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind nun:

* der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung
* der [Inhaltsfragment-Editor](/help/sites-developing/universal-editor/introduction.md) zur formularbasierten Bearbeitung

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

* **Problem mit dem JSP-Skriptpaket in AEM 6.5.21–6.5.23 und AEM 6.5 LTS GA**
AEM 6.5.21, 6.5.22, 6.5.23 und AEM 6.5 LTS GA werden mit dem Paket `org.apache.sling.scripting.jsp:2.6.0` ausgeliefert, das ein bekanntes Problem enthält. Das Problem tritt in der Regel bei hoher Auslastung auf, wenn die AEM-Instanz viele Anfragen gleichzeitig verarbeitet.

  Wenn dieses Problem auftritt, kann eine der folgenden Ausnahmen in den Fehlerprotokollen neben Verweisen auf `org.apache.sling.scripting.jsp:2.6.0` angezeigt werden:

   * `java.io.IOException: classFile.delete() failed`
   * `java.io.IOException: tmpFile.renameTo(classFile) failed`
   * `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
   * `java.io.FileNotFoundException`

  Wenn dieser Fehler auftritt, besteht die einzige Wiederherstellungsmethode darin, die AEM-Instanz neu zu starten.

  Wenden Sie sich an den Adobe Kundensupport und referenzieren Sie diesen Versionshinweis für eine Lösung.

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

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6523}

Die Vorschau von Inhaltsfragmenten schlägt aufgrund des DoS-Schutzes für eine umfassende Fragment-Baumstruktur fehl. Siehe den [KB-Artikel zu den standardmäßigen GraphQL Query Executor-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6523}

* Wenn ein Kunde von Struts 2.x auf 6.x aktualisiert, kann eine strengere Typüberprüfung zu stillen Fehlern führen - insbesondere dann, wenn Kontrollkästchen-Komponenten „false“ zurückgeben und an eine Liste (Ganzzahl *gebunden*. Dieser Wertkonflikt muss explizit behandelt werden, um Deserialisierungsfehler zu vermeiden. (FORMS-20203)

* Die Konvertierung von HTML in PDF auf dem SUSE® Linux®-Server (SLES 15 SP6 oder höher) schlägt mit folgendem Fehler fehl:

  ```Auto configuration failed 4143511872:error:0E079065:configuration file routines:DEF_LOAD_BIO:missing equal sign:conf_def.c:362:line 57```
Legen Sie dann die folgende Umgebungsvariable fest und starten Sie den Server neu:
  `OPENSSL_CONF=/etc/ssl`

* Wenn Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) doppelte Einträge von Geode-JAR-Dateien `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` unter dem Ordner `<AEM_Forms_Installation>/lib/caching/lib` (FORMS-14926) finden, führen Sie die folgenden Schritte durch, um das Problem zu beheben:

   1. Beenden der Locators, falls sie noch ausgeführt werden.
   1. Beenden des AEM-Servers.
   1. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
   1. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
   1. Öffnen der Eingabeaufforderung im Administratormodus.
   1. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

* Wenn Benutzende versuchen, einen Briefentwurf mit gespeicherten XML-Daten in der Vorschau anzuzeigen, bleibt er für bestimmte Buchstaben im `Loading`-Zustand hängen. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (FORMS-14521)

* Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 kann der `PaperCapture`-Dienst keine OCR-Vorgänge (optische Zeichenerkennung) mehr für PDFs durchführen. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (CQDOC-21680)

* Bei Benutzenden, die von AEM 6.5 Forms Service Pack 18 oder 19 auf Service Pack 20 oder 21 aktualisiert haben, trat ein JSP-Kompilierungsfehler auf. Dieser Fehler hinderte sie daran, adaptive Formulare zu öffnen oder zu erstellen. Er hat auch Probleme mit anderen AEM-Schnittstellen verursacht. Diese Schnittstellen umfassten den Seiteneditor, die AEM Forms-Benutzeroberfläche, den Workflow-Editor und die Benutzeroberfläche der Systemübersicht. (FORMS-15256)

  Wenn ein solches Problem auftritt, führen Sie die folgenden Schritte aus, um es zu beheben:
   1. Navigieren Sie in CRXDE zum Verzeichnis `/libs/fd/aemforms/install/`.
   1. Löschen Sie das Bundle `com.adobe.granite.ui.commons-5.10.26.jar`.
   1. Starten Sie den AEM-Server neu.

* Nach der Aktualisierung auf AEM Forms Service Pack 20 (6.5.20.0) mit dem Forms-Add-on funktionieren Konfigurationen, die auf den alten Adobe Analytics Cloud-Dienst mithilfe der berechtigungsbasierten Authentifizierung angewiesen sind, nicht mehr. Dieses Problem verhinderte die ordnungsgemäße Ausführung von Analyseregeln. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (FORMS-15428)
* In der Druckvorschau der Agent-Benutzeroberfläche für interaktive Kommunikationen wird das Währungssymbol (z. B. das Dollarzeichen $) für alle Feldwerte uneinheitlich angezeigt. Es wird für Werte bis 999 angezeigt, fehlt jedoch für Werte ab 1000. (FORMS-16557)
* Änderungen am XDP von verschachtelten Layout-Fragmenten in einer interaktiven Kommunikation werden nicht im Editor für interaktive Kommunikationen angezeigt. (FORMS-16575)
* In der Druckvorschau der Agent-Benutzeroberfläche für interaktive Kommunikationen werden einige berechnete Werte nicht korrekt angezeigt. (FORMS-16603)
* Wenn der Brief in der Druckvorschau angezeigt wird, ändert sich der Inhalt. Einige Leerzeichen verschwinden und bestimmte Buchstaben werden durch `x` ersetzt. (FORMS-15681)
* Wenn Benutzende eine WebLogic 14c-Instanz konfigurieren, schlägt der PDFG-Dienst in AEM Forms Service Pack 21 (6.5.21.0) on JEE, wenn er auf JBoss® ausgeführt wird, aufgrund von Classloader-Konflikten mit der SLF4J-Bibliothek fehl. Der Fehler wird wie folgt angezeigt (CQDOC-22178):

  ```java
  Caused by: java.lang.LinkageError: loader constraint violation: when resolving method "org.slf4j.impl.StaticLoggerBinder.getLoggerFactory()Lorg/slf4j/ILoggerFactory;"
  the class loader org.ungoverned.moduleloader.ModuleClassLoader @404a2f79 (instance of org.ungoverned.moduleloader.ModuleClassLoader, child of 'deployment.adobe-livecycle-jboss.ear'
  @7e313f80 org.jboss.modules.ModuleClassLoader) of the current class, org/slf4j/LoggerFactory, and the class loader 'org.slf4j.impl@1.1.0.Final-redhat-00001' @506ab52
  (instance of org.jboss.modules.ModuleClassLoader, child of 'app' jdk.internal.loader.ClassLoaders$AppClassLoader) for the method's defining class, org/slf4j/impl/StaticLoggerBinder,
  have different Class objects for the type org/slf4j/ILoggerFactory used in the signature.
  ```


## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.23.0](/help/release-notes/assets/65230-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE --> enthaltenen OSGi-Bundles
* [Liste der in Experience Manager 6.5.23.0](/help/release-notes/assets/65230-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE --> enthaltenen Inhaltspakete

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kundinnen und Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
