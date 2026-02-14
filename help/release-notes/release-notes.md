---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: 5a851bf013a4ef7e6097bf32bd3fa8fe4d635f28
workflow-type: tm+mt
source-wordcount: '9627'
ht-degree: 20%

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
| Version | 6.5.24.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;26. November 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

<!-- OLD DOWNLOAD URL
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) -->

## Was in [!DNL Experience Manager] 6.5.24.0 enthalten ist {#what-is-included-in-aem-6524}

[!DNL Experience Manager] 6.5.24.0 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->


## Wichtige Funktionen und Verbesserungen

### Forms

* **Unterstützung für die Übergabe benutzerdefinierter XCI:** Es wurde Unterstützung für die Übergabe benutzerdefinierter XCI in Parameter der Befehlszeilenanwendung xmlformcmd hinzugefügt. Dies ermöglicht es Benutzenden, benutzerdefinierte XCI-Dateien für Tests anzugeben, was die Flexibilität und Kontrolle über den Testprozess verbessert. (LC-3923248)


## Behobene Probleme im Service Pack 24 {#fixed-issues}

<!-- 6.5.24.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Assets] {#assets-sp24}

* Nach der Aktualisierung auf Version 6.5.23.0 führte das Sortieren von Ordnern nach dem Änderungsdatum in der Kartenansicht zu Schwierigkeiten beim Suchen kürzlich geänderter Assets für On-Premise-Bereitstellungen. (ASSETS-56946)
* Wiederholte Warnprotokolleinträge werden bei der Ausführung der Planung generiert. (ASSETS-52554)
* Die Sortierung von Titeln funktioniert nicht in der Listenansicht. (ASSETS-50716)
* Das Fenster Sammlungseigenschaften wird auch nach dem Klicken auf die Schaltfläche Abbrechen nicht geschlossen. (ASSETS-48504)

* Beim Versuch *Assets in AEM 6.5.22 mit Anmerkungen zu versehen,* der Fehler „Ungültige URL“ auf. (NPR-42684)
* Das Assets-Metadaten-Editor-Formular wird nach dem Ausführen von verknüpften Aktionen oder Aktionen zum Aufheben von Verknüpfungen nicht neu initialisiert. (ASSETS-52207)
* Wenn Assets aus dem Remote-DAM erneut mit den lokalen Sites synchronisiert werden, wird der veröffentlichte Status der Assets fälschlicherweise auf `Not published` aktualisiert. (ASSETS-48958)
* Beim Upgrade von der SP23-Version auf die LTS-Version 6.5 sind Probleme aufgetreten. (ASSETS-50541)

### [!DNL Sites]{#sites-6524}

#### Barrierefreiheit {#sites-accessibility-6524}

* Das Dialogfeld **Anzeigeformat wechseln** unterstützt jetzt die vollständige Tastaturbedienung. Der Fokus überspringt nicht mehr die **Anzeigeeinstellungen** und die Standardtasten (`Tab`, `Enter`, `Space`) funktionieren konsistent. (SITES-24306)
* Tastaturbenutzer können die veröffentlichten Status-Tags ohne Maus entfernen. Der Fokus landet auf jedem Tag, und die Aktivierung funktioniert mit `Enter`/`Space` und Rücktaste/Löschen. Das Tag-Steuerelement verhält sich jetzt wie eine Schaltfläche, wodurch das Feedback der Bildschirmlesehilfe verbessert wird und die WCAG 2.1.1-Tastatur erfüllt wird. (SITES-24491)
* Filtert Leisten-Reflüsse reaktionsschnell in engen Darstellungsfeldern. Die Auswahlsteuerelemente und -ergebnisse bleiben im Darstellungsfeld bei einem Zoom von 400 %, sodass horizontales Scrollen und ein Content-Cut-off entfallen. (SITES-24708)
* AEM stellt den vollständigen Tastaturzugriff auf die ContextHub-Schaltflächen „Zurücksetzen“, „Persona“ und „Gerät“ wieder her. Die Tabulatortaste und Pfeiltasten erreichen jedes Steuerelement, zeigen einen sichtbaren Fokusindikator an und aktivieren Aktionen mit `Enter` oder `Space`. Bildschirmlesehilfen geben klare Bezeichnungen an. (SITES-24939)
* Datumseingabe und -auswahl bleiben bei 320 Pixel vollständig sichtbar. Das Timewarp-Modal verwendet eine responsive Größenanpassung, sodass das Steuerelement nicht mehr auf dem kleinsten Viewport abgeschnitten oder ausgeblendet wird. (SITES-24962)
* Die Leiste „Verweise“ unterstützt jetzt einen 400%igen Browser-Zoom, ohne den Zugriff auf den Inhalt zu verlieren. Die Leiste verwendet eine responsive Größe anstelle einer festen Breite, sodass Elemente sichtbar und bei 1280:1024 × werden können. (SITES-24972)
* Die Filterleiste funktioniert jetzt mit einem Zoom von 400 %. Die Leiste ändert ihre Größe mit relativen Einheiten und blockiert oder blendet Filtersteuerelemente nicht mehr aus. Benutzer können jede Filteroption ohne horizontalen Bildlauf oder abgeschnittene Trefferziele anzeigen und auswählen. (SITES-24981)
* Tastaturbenutzer können Formatierungsmenüs im Teaser-Modal verwenden. Durch Drücken von `Enter` oder `Space` auf **Liste** oder **Absatzformat** wird das Popup-Fenster geöffnet, mit den Pfeiltasten können Sie zu den Optionen navigieren, und `Enter` wendet die Auswahl an. `Escape` schließt das Menü und stellt den Fokus auf das auslösende Steuerelement wieder her. Dies führt zu einem konsistenten Symbolleisten-Workflow. (SITES-25235)
* Das Popover der Farbfeldauswahl bleibt jetzt mit 320 Pixel im Darstellungsfeld. Das Popover zeigt alle Farbzeilen an und unterstützt das Scrollen, sodass Autoren auf kleinen Bildschirmen beliebige Farb-/Bildmuster auswählen können. (SITES-25274)
* Die Dropdown-Menüs der Demografiesymbolleiste funktionieren jetzt vollständig mit der Tastatur. Beim Öffnen eines Menüs wird der Fokus auf die erste Option verschoben, mit den Pfeiltasten durch die Liste navigiert und Esc/Tabulatortaste geschlossen oder vorwärts verschoben, ohne den Fokus auf die Symbolleiste zu verschieben. Interaktive Elemente verwenden eine korrekte Semantik, sodass NVDA und andere Leser Optionen korrekt angeben. (SITES-25310)
* Das Hinzufügen von Komponenten in der Inhaltsstruktur funktioniert wie unter AEM 6.5 SP24 entworfen. Der anfängliche Fehler stammt von fehlenden Autorenberechtigungen in einem lokalen Setup und nicht von AEM. Autoren mit Bearbeitungsrechten können die Schaltfläche aktivieren und Komponenten per Tastatur oder Maus hinzufügen. (SITES-25312)
* Der Zugriff über Tastatur und Bildschirmlesehilfe in der Demografiesymbolleiste funktioniert jetzt zuverlässig. Autoren, die NVDA verwenden, können **Commerce**, **Persona** und 88 mit Pfeilen durchlaufen, ein klares Fokus-Feedback beobachten und verstehen, welche Registerkarte aktiv ist. (SITES-25326)

* Der **Zum Inhalt wechseln**-Link verschiebt jetzt den Tastaturfokus in die Überschrift Hauptinhalt . Der Fokus bleibt auf einem eindeutig identifizierten Ziel sichtbar, sodass die Sprachausgabe den richtigen Abschnitt ankündigt. Die Änderung entspricht den WCAG-Richtlinien 2.4.1 und 2.4.3. (SITES-24061)
* Die Tastaturnavigation auf der Sites-Startseitenstruktur folgt einer logischen Reihenfolge nach der Verwendung von **Alle auswählen**. Der Fokus wechselt von **Alle auswählen** zum nächsten Steuerelement (linke Leiste öffnen), anstatt zum Seitenanfang zurückzuspringen. (SITES-24307)
* Abschnittstitel und Bearbeitungssteuerelemente im Sites-Editor reagieren auf Tastaturfokus und Aktivierung. Tastaturbenutzer zeigen denselben Titel und dieselben Aktionen an, die zuvor nur beim Bewegen des Mauszeigers angezeigt wurden. (SITES-24479)
* Schaltflächen im Sites-Editor zeigen beschreibende Namen anstelle von generischen oder fehlenden Beschriftungen an. Hilfstechnologien geben die richtige Aktion an, wodurch die Klarheit verbessert und Klickfehler reduziert werden. (SITES-24480)
* Bildschirmlesehilfen erhalten eine gesprochene „Laden“-Nachricht, während die Sites-Ansicht aktualisiert wird. Die Aktualisierung fügt eine dedizierte Live-Statusregion hinzu und schreibt die Nachricht programmgesteuert in diese, was den Fortschritt bestätigt, ohne den Fokus zu verschieben. (SITES-24481)
* Die Assets-Seitenleiste enthält jetzt eine klare **Schließen**-Steuerung und setzt den Fokus wieder auf die Umschaltfläche. Benutzer von Tastatur und Bildschirmlesehilfe verwerfen das Bedienfeld sofort, anstatt mit der Tabulatortaste durch jedes Steuerelement zu navigieren. Dadurch werden Tastenanschläge reduziert und das erwartete Bedienfeldverhalten wird übernommen. (SITES-24489)
* Die Liste der ARIA-Registerkarten im Seiten-Editor von Sites enthält einen beschreibenden Namen. Die Sprachausgabe erkennt das Steuerelement jetzt als Registerkartenliste und liest die korrekte Beschriftung, sodass Benutzende den richtigen Satz von Registerkarten finden und zuverlässig zwischen ihnen wechseln können. (SITES-24492)
* Die Suche in der Editor-Seitenleiste gibt jetzt die Ergebnisse für Sprachausgaben aus. Bei der Benutzereingabe wird eine Live-Statusmeldung angezeigt, die die Anzahl der Übereinstimmungen und Aktualisierungen ohne Fokusverschiebung angibt. Tastaturbenutzer entdecken die Ergebnisse sofort. (SITES-24506)
* Die Zeilenauswahl in der Listenansicht wurde für Benutzende von Hilfstechnologien verbessert. Das Kontrollkästchen legt einen aussagekräftigen Namen offen, der aus dem Zeilentitel abgeleitet wird, sodass Ankündigungen kurz bleiben und die Aktion korrekt beschreiben. (SITES-24514)
* Die Barrierefreiheitsnamen für die Listenansicht wurden korrigiert. Die Tabelle entfernt `aria-label` aus nicht interaktiven Elementen und weist den Titel dem umsetzbaren Link oder der umsetzbaren Schaltfläche zu. Benutzende von Bildschirmlesehilfen hören jetzt genaue, nicht duplizierte Beschriftungen in der gesamten Spalte. (SITES-24515)
* Die Sticky-Kopfzeile hörte auf, das modale Teaser-Dialogfeld während der Verwendung mit hohem Zoom zu verdecken. Der Inhalt bleibt mit 200 % und 400 % Zoom lesbar und nutzbar, mit vertikalem Fluss und ohne abgeschnittene Abschnitte. (SITES-24523)
* Durch die Eingabe in das Suchfeld wird keine vorzeitige Bekanntgabe des ersten Ergebnisses oder eine versehentliche Aktivierung mehr Trigger. Das Erlebnis gibt jetzt eine knappe Statusmeldung mit der Ergebnisanzahl aus, während der Fokus im Feld bleibt, bis der Benutzer zur Liste navigiert. (SITES-24658)
* Das Feld Alternativer Text im Hyperlink-Dialogfeld des Texteditors legt jetzt eine programmgesteuerte Beschriftung offen. Die Sprachausgabe gibt „Alternativtext“ für das Feld aus und der Fokus landet auf dem korrekt benannten Steuerelement. Diese Fehlerbehebung verbessert die Navigation für Benutzer von Tastatur und Sprache. (SITES-24675)
* Es wurde eine Live-Statusmeldung zur Leiste „Verweise“ hinzugefügt, damit Hilfstechnologien Änderungen sofort ankündigen können. Durch die Auswahl mehrerer Elemente erhalten Trigger eine deutliche Botschaft zur Referenzverfügbarkeit, die stille Statusänderungen verhindert und Wiederholungsaktionen reduziert. (SITES-24678)
* Das Dialogfeld Bild gibt jetzt über einen ARIA-Live-Bereich seinen Ladestatus aus. Die Sprachausgabe gibt die Meldung „Wird geladen, bitte warten“ aus, während das Rotationsdrucker angezeigt wird. Und ein fertiges Update, wenn der Inhalt abgeschlossen ist, damit die Benutzer wissen, wann sie interagieren können. (SITES-24697)
* Das Dialogfeld zur Link-Auswahl zeigt jetzt eine Live-Region, die Suchergebnisse ankündigt. Die Sprachausgabe hört den Status „Ergebnisse aktualisiert“ nach jeder Suche, ohne den Fokus zu verschieben, sodass Benutzende eine klare Bestätigung erhalten, dass die Suche abgeschlossen wurde. (SITES-24700)
* Das Dialogfeld Linkauswahl wird jetzt mit 320 Pixel wiedergegeben. Alle Felder und Aktionen bleiben sichtbar und verwendbar, und die horizontale Bildlaufleiste wird nicht mehr angezeigt. (SITES-24709)
* Das Dialogfeld Linkauswahl verwendet nun für den Bildschirmtext und den barrierefreien Namen bei jedem Element der Baumstruktur dieselbe Beschriftung. Die Sprachausgabe gibt jedes Element aus, während sie mit den Pfeiltasten bewegt wird, einschließlich der letzten Ebene, wodurch stille Knoten und nicht übereinstimmende Namen eliminiert werden. (SITES-24710)
* Änderungsfilter melden jetzt ihren Status als erweitert oder reduziert. Die Schaltfläche wechselt `aria-expanded` synchron zum Filterbedienfeld und zeigt einen einzelnen, leeren Namen an („Filter ändern„), wodurch das verwirrende „Filter?“ entfernt wird. Ankündigung Benutzende von Bildschirmlesehilfen können das Ergebnis der Aktivierung des Steuerelements vorhersagen. (SITES-24713)
* Modale Kopfzeilen decken Inhalte mit einer Breite von 320 Pixel nicht mehr ab. Die Kopfzeile löst sich aus dem klebrigen Zustand, und der Textkörper des Dialogfelds scrollt, sodass alle Felder und Aktionsschaltflächen sichtbar und verwendbar bleiben. Tastaturbenutzer können jedes Steuerelement ohne Fokusverlust erreichen. (SITES-24718)
* App-Navigations-Links zeigen jetzt die richtige Link-Semantik. Die Sprachausgabe gibt jedes Element als Link und nicht als Listenelement aus, wodurch die Tastaturnavigation und die Sprachsteuerung verbessert werden. Der Listen-Container behält die Listensemantik bei, während Links die fokussierbaren Ziele bleiben. (SITES-24719)
* Der Ergebnisstatus gibt Sprachausgaben jetzt wieder, wenn sich Filter ändern. Die NVDA liest sowohl die Zählung „X der Y Ergebnisse“ als auch die Nachricht „Keine Ergebnisse“. Der Paging-Status verwendet einen Live-Bereich, der aktualisiert wird, sodass Benutzende eine Bestätigung hören, ohne den Fokus zu verschieben. (SITES-24720)
* Die Drehschaltfläche im Karusselldialogfeld gibt jetzt für Sprachausgaben einen einzelnen, knappen Namen aus. Das Steuerelement wiederholt nicht mehr sowohl die Gruppenbeschriftung als auch die Eingabebeschriftung, was die Ausführlichkeit und Verwirrung für NVDA-Benutzer reduziert. (SITES-24725)
* Die Suchliste im Menü Hilfe zeigt die richtige Semantik. Der Container enthält eine Liste, und jedes Ergebnis bleibt ein Link ohne eine widersprüchliche Rolle. NVDA und JAWS geben Links genau bekannt und die Navigation bleibt konsistent. (SITES-24729)
* Adobe hat das Farbfeld-Popup in den Benutzereinstellungen korrigiert, sodass NVDA das Farbfeld im Fokus anzeigt, nicht das zuvor ausgewählte Farbfeld. Tastaturbenutzer hören beim Navigieren durch die Liste genaue Farbnamen und können die korrekte Auswahl bestätigen. (SITES-24739)
* NVDA liest nun die vollständige Beschreibung im Verzeichnis „Tree“ (Baumstruktur). Das Detailbedienfeld stellt mehrzeiligen Text als einen Wert bereit und verknüpft ihn mit der Feldbezeichnung. Tastaturbenutzer hören den vollständigen Text, während sie durch schreibgeschützte Felder navigieren. (SITES-24780)
* Im Strukturverzeichnis wird nun das Änderungsdatum ausgegeben. NVDA liest das Datum, an dem der Fokus in die Spalte Geändert wechselt. Das Raster verknüpft jedes Datum mit dem Elementnamen, damit Benutzer sowohl die Datei als auch ihre letzte Aktualisierung hören. (SITES-24782)
* Der Vorschaumodus berücksichtigt jetzt die Textabstand-Voreinstellungen des Benutzers. Die Arbeitsfläche spiegelt Änderungen an Buchstaben, Wörtern und Zeilenhöhen in allen in der Vorschau angezeigten Inhalten wider. Text bleibt bei zunehmendem Abstand nicht mehr fixiert oder Clips. Benutzer mit Tastatur und Sehschwäche lesen Inhalte ohne Layout-Unterbrechungen. (SITES-24936)
* AEM korrigiert die Registerkartenreihenfolge auf Seiten des Assets-Editors. Die Tabulatortaste wechselt nun von den Kopfzeilensteuerelementen zu den Schaltflächen der Kontaktnabe und schließlich in einer klaren Reihenfolge in die Arbeitsflächen-Werkzeuge. Die Sprachausgabe folgt derselben Reihenfolge, wodurch Verwirrung vermieden und die Tastaturnavigation beschleunigt wird. (SITES-24937)
* AEM fügt der Menüleiste für Kartenaktionen einen programmgesteuerten Namen hinzu. Bildschirmlesehilfen geben das Steuerelement korrekt an, und Sprachbenutzer können es anhand des Namens auswählen. Die Tastaturnavigation und der Fokus bleiben unverändert. (SITES-24938)
* Kartenansichtsmenüs berücksichtigen größeren Textabstand. Das Element Mehr Aktionen wächst und schneidet Beschriftungen, einschließlich „Quick Publish“, nicht mehr ab. Benutzer, die Buchstaben-, Wort- oder Zeilenabstände erhöhen, behalten vollständige Beschriftungen und den Tastaturzugriff bei. (SITES-24941)
* Die Rolle „Präsentation“ wurde entfernt, durch die die Tabelle der Sites-Startseite im Baum der Barrierefreiheit ausgeblendet wurde. Die Tabelle liest sich erneut korrekt. NVDA und JAWS erkennen die Tabelle, erkennen Kopfzeilen und kündigen während der Zeilen- und Spaltennavigation Kopfzeilenbeziehungen an. (SITES-24942)
* Das Sortieren von Feedback in der Listenansicht ist explizit und konsistent. Nach einer Sortierung legt der Header die Reihenfolge durch `aria-sort` offen. Es gibt die Änderung bekannt, während unsortierte Kopfzeilen keinen Status mehr beanspruchen, was Benutzenden von Bildschirmlesehilfen hilft, zu verfolgen, welche Spalte die Sortierung steuert. (SITES-24943)
* Die Kopfzeile „Layout bearbeiten“ zeigt keine funktionierende Schaltfläche **Bearbeiten** mehr. Das Steuerelement fungiert jetzt als statische Statusbeschriftung und bleibt außerhalb der Tabulatorreihenfolge, sodass Tastaturbenutzer keinen Tastendruck verschwenden. Verwenden **Wählen Sie einen anderen Modus aus** um den Modus zu wechseln, mit klarer Rückmeldung der Bildschirmlesehilfe. (SITES-24950)
* In der Emulator-Symbolleiste werden standardmäßig vollständige Gerätenamen angezeigt. Die Beschriftung wird beim Laden nicht mehr abgeschnitten, sodass Benutzende Geräte lesen und auswählen können, ohne zu erraten. Text skaliert sauber über Zoom-Ebenen und enge Breiten. (SITES-24952)
* Emulator-Symbolleiste für kleine Darstellungsfelder. Bei 320 Pixeln führt die Geräteliste und steuert die Anzeige ohne Beschneidung, sodass Benutzer Galaxy S7 und neuere Modelle auswählen können. Das Layout kann skaliert und umschlossen werden, um auch bei 400 % Zoom horizontales Scrollen zu vermeiden. (SITES-24953)
* Die Sprachausgabe gibt das ausgewählte Gerät und dessen Messungen im Emulator aus. NVDA liest den Linealstrom nicht mehr. Die Geräteschaltfläche verwendet eine angehängte Beschreibung für den QuickInfo-Text, wodurch Rauschen reduziert und die Navigation angeleitet wird. (SITES-24955)
* Die Filterleiste behandelt nun jedes ausgewählte Tag als Aktionsschaltfläche. Klare barrierefreie Namen und Fokusverwaltung verbessern die Ankündigungen und die Tastatursteuerung. (SITES-24980)
* Statusaktualisierungen in der Sites-Admin-Filteransicht geben Bildschirmlesehilfen bekannt. Wenn Benutzende während des Ladens von Elementen die Karte/Liste wechseln, spricht NVDA jetzt die Meldung „Bitte warten“ über eine Live-Region. Diese Anleitung verhindert zusätzliche Klicks und Verwirrung. (SITES-24992)
* Der Tastaturfokus bewegt sich jetzt in logischer Reihenfolge, wenn Benutzende die linke Leiste erweitern. Der Fokus wechselt direkt von der linken Leisten-Schaltfläche zum erweiterten Inhalt, sodass Elemente nicht rückwärts nachverfolgt oder übersprungen werden müssen. Diese Änderung verbessert die Barrierefreiheit für Benutzende von Bildschirmlesehilfen und Tastaturen. (SITES-24998)
* Das Feedback der Bildschirmlesehilfe für die Schaltfläche **Bearbeiten** stimmt jetzt mit dem Steuerelement überein. Durch Aktivieren der Schaltfläche wird die Aktion Bearbeiten anstelle einer Vorschaumeldung angekündigt, was die Klarheit verbessert und Eingabefehler für Nicht-Maus-Benutzer reduziert. (SITES-25208)
* Die Bestätigungsaktion im Teaser-Dialogfeld wird für Sprachausgaben korrekt ausgegeben. Das Steuerelement meldet „Bestätigen“, nicht die Symbolbeschreibung, und gibt Tastatur- und Bildschirmlesehilfen eine klare Anleitung. (SITES-25223)
* Die Schaltfläche Hilfe zeigt jetzt einen eindeutigen barrierefreien Namen an. Die Sprachausgabe gibt „Hilfe“ anstelle einer ausführlichen Symbolbeschreibung aus. Benutzer verstehen die Aktion und können Hilfe schneller finden. (SITES-25224)
* Das Timewarp-Modal zeigt einen klaren Fokusring auf den **`Set Date`**- und **Timewarp beenden**-Links an. Benutzer, die genau sehen, wo der Fokus liegt, und unbeabsichtigte Aktionen vermeiden. Der Ring hält mindestens 3:1 Kontrast zum Hintergrund. (SITES-25232)
* Die Sprachausgabe gibt jetzt die Steuerelemente Anmerken und Anmerken schließen in der Symbolleiste Anmerken genau aus. NVDA sagt nicht mehr „Vorschau-Schaltfläche gedrückt,“ was Autoren getäuscht und die falsche Aktion vorgeschlagen. Die Ankündigung stimmt mit der gedrückten Schaltfläche überein und hält den Workflow frei. (SITES-25234)
* Die Tastaturnavigation in der Anmerkungs-Symbolleiste verhält sich konsistent. Der Fokus springt beim Öffnen des Modus nicht mehr zu „Beenden“ und wechselt stattdessen zum Startsteuerelement, um Anmerkungen hinzuzufügen. Benutzende navigieren nacheinander durch die Steuerelemente, ohne das umgekehrte Registerkartenmuster zu verwenden. (SITES-25241)
* Die Anzeige auf dem kleinen Bildschirm funktioniert wie im Teaser-Modal erwartet. Das Dialogfeld erstellt keine horizontale Bildlaufleiste mehr mit 320 Pixel und die Symbolleiste bleibt zugänglich, ohne sie seitwärts zu schwenken. Diese Aktualisierung hilft sehbehinderten Benutzern, die die Seite vergrößern. (SITES-25242)
* Die Anzeige auf dem kleinen Bildschirm funktioniert wie im Bild-Modal erwartet. Das Dialogfeld erstellt keine horizontale Bildlaufleiste mit 320 Pixel mehr, und die Bildwerkzeuge bleiben ohne seitliches Schwenken zugänglich. Diese Aktualisierung verbessert die Navigation für Benutzer mit Sehschwäche, die die Seite zoomen. (SITES-25244)
* Das Suchmodal berücksichtigt die Textabstand-Einstellungen des Benutzers. Durch Erhöhen der Zeilenhöhe, des Absatzabstands, des Buchstabenabstands oder des Wortabstands wird Text nicht mehr abgeschnitten oder die Baumstruktur überschneidet sich. Inhaltsänderungen werden in WCAG 1.4.12 -Werten wiedergegeben und bleiben vollständig lesbar. (SITES-25245)
* Das Suchmodal passt jetzt für kleine Bildschirme, ohne das Baumverzeichnis mit 320 Pixel zu überlappen. Der Inhalt fließt innerhalb des Dialogfelds, lässt nur den vertikalen Bildlauf zu und hält Steuerelemente sichtbar. Diese Fehlerbehebung verbessert die Lesbarkeit und die Tastaturnavigation und stimmt mit dem WCAG-Reflow überein. (SITES-25246)
* Der modale Überlauf im Karussell erzwingt kein horizontales Scrollen bei Breiten im Telefonformat mehr. Die Komponente passt sich 320 Pixel an, behält den vertikalen Fluss bei und behält die Steuerelemente im Blick. Die Änderung verbessert die Lesbarkeit und den Tastaturzugriff beim Authoring. (SITES-25254)
* Anmerkungs-Workflows verlieren nicht mehr den Fokus. Das Modal legt den anfänglichen Fokus auf eine aussagekräftige Überschrift, verhindert, dass der Fokus aus dem Dialogfeld springt, und stellt den Fokus nach dem Schließen auf den Trigger wieder her. Die Ausgabe der Bildschirmlesehilfe bleibt präzise und relevant. (SITES-25257)
* Der **Anmerkung löschen** wird jetzt korrekt mit dem Tastaturfokus verarbeitet. Beim Öffnen des Dialogfelds wird der Fokus auf die Überschrift für den Kontext der Bildschirmlesehilfe verschoben, und beim Schließen wird der Fokus wieder auf die Schaltfläche **Anmerkung löschen** gesetzt, mit der es gestartet wurde. Benutzende landen nicht mehr auf nicht verwandten Steuerelementen oder hinter dem Modal. (SITES-25258)
* Die Timewarp-Datumsauswahl verwaltet den Fokus jetzt korrekt. Durch Drücken von `Esc` wird der Fokus auf die Schaltfläche **Datumsauswahl** zurückgesetzt, und durch die Auswahl eines Datums wird der Fokus auf das verknüpfte Eingabefeld verschoben. Benutzer von Tastatur und Bildschirmlesehilfe behalten den Kontext bei und landen nicht hinter dem Modal. (SITES-25264)
* Die Sprachausgabe gibt die richtigen Aktionen für die Schaltflächen **Anmerken** und **Anmerken schließen** aus. Die NVDA sagt nicht mehr „Vorschau-Schaltfläche gedrückt“; sie gibt den Namen der Schaltfläche an, damit die Benutzer wissen, wann der Anmerkungsmodus beginnt oder endet. (SITES-25268)
* Das Anmerkungsmodal zeigt jetzt eine klare **Senden** Aktion an. Autoren können einen Kommentar hinzufügen und ihn mit der Schaltfläche mit dem Stiftsymbol senden oder das Modal mit `Esc` schließen, ohne den Fluss zu erraten. (SITES-25269)
* Der Anmerkungseintrag enthält explizite Aktionsschaltflächen. Das Dialogfeld stellt **Senden** zum Speichern der Anmerkung und **Abbrechen** zum Schließen bereit, beide über die Tastatur zugänglich und von Hilfstechnologien angekündigt. Autoren müssen nicht mehr auf das Klicken außerhalb des Dialogfelds oder das Drücken von nur `Esc` klicken, um den Vorgang abzuschließen. (SITES-25281)
* Im Anmerkungsmodus bleibt der Tastaturfokus nun auf der Überlagerung und ihrer Symbolleiste. Die Seite hinter der Überlagerung erhält keinen Fokus mehr, wenn Autoren die Tabulatortaste drücken, sodass Benutzende orientiert bleiben und durch Anmerkungen navigieren können, ohne zu zugrunde liegenden Inhalten zu springen. (SITES-25282)
* Der Geräteselektor in Layout bearbeiten funktioniert wie vorgesehen. Wenn zwei Geräteoptionen ähnliche Breiten haben (z. B. iPhone 8 Plus neben Galaxy 7), zeigt die ausgewählte Schaltfläche eine QuickInfo an, um die vollständige Beschriftung anzuzeigen, während beide Schaltflächen sichtbar und zugänglich bleiben. (SITES-25285)
* Bei einem Zoom von 200 % wird die Seite durch das Layout „Bearbeiten“ nicht mehr überlaufen. Die Symbolleiste wird vollständig gerendert und bei Bedarf wird ein horizontaler Bildlauf verfügbar gemacht, wodurch der Zugriff auf zuvor ausgeblendete Steuerelemente für Benutzende mit Sehschwäche wiederhergestellt wird. (SITES-25288)
* Die Registerkartenreihenfolge in der Layout-Vorschau wechselt jetzt von der primären Symbolleiste direkt zur Demografie-Symbolleiste. Benutzer von Tastatur und Bildschirmlesehilfe können Steuerelemente in einer vorhersehbaren Reihenfolge durchlaufen, anstatt zur sekundären Symbolleiste zu springen. Die Änderung entspricht der WCAG 2.4.3-Fokusreihenfolge. (SITES-25305)
* Wenn Sie die Seite auf 200 % vergrößern, wird ein Teil der Symbolleiste Demografie nicht mehr ausgeblendet. Der Symbolleistenbereich verwaltet den Überlauf und bietet Scrollen in seinem eigenen Bereich, sodass jedes Steuerelement in hoher Vergrößerung sichtbar und bedienbar bleibt. (SITES-25309)
* Texteingaben in der Demografiesymbolleiste zeigen jetzt geeignete barrierefreie Namen an. Jedes Feld enthält eine eindeutige ID mit einer programmgesteuerten Kennzeichnung, sodass die Sprachausgabe den Zweck des Felds angibt und Benutzende nach Kennzeichnung navigieren können. Das sichtbare Etikett befindet sich in der Nähe des Steuerelements, um die Lesbarkeit bei schlechtem Sehvermögen zu verbessern. (SITES-25316)
* Mit der Schaltfläche Bearbeiten wird nun die richtige Aktion für die Sprachausgabe in der sekundären Symbolleiste ausgegeben. Wird sie aktiviert, wird „Bearbeiten“ anstelle der zugehörigen „Vorschau-Schaltfläche gedrückt“ gelesen, was Verwirrung bei der Tastaturnavigation beseitigt. (SITES-25320)
* Der Regler Warenkorb in der Demografiesymbolleiste zeigt jetzt einen richtigen barrierefreien Namen an. Die Sprachausgabe gibt den Gesamtwert des Warenkorbs aus und Spracheingabe-Tools können das Steuerelement nach Namen auswählen, wodurch die Einhaltung von WCAG 4.1.2 (Name, Rolle, Wert) verbessert wird. (SITES-25322)
* Der Regler der Demografie-Symbolleiste behält jetzt den Fokus, wenn Autoren den Wert mit den Pfeiltasten ändern. Der Fokus springt nicht mehr auf die Schaltfläche „Warenkorb“, sodass Tastaturbenutzer den Wert kontinuierlich anpassen und die Sprachausgabe jede Änderung ankündigt. (SITES-25324)
* Suchen Sie jetzt Assets Reflow sauber bei 320 px (ca. 400% Zoom). Das Modal behält Überschriften, Felder und Aktionen lesbar und überlappungsfrei, sodass Autoren ohne horizontales Scrollen suchen können. (SITES-25330)
* Das Assets-Bedienfeld im Editor folgt einer logischen Fokussequenz. Tastaturbenutzer , die mit der Tabulatortaste über jede Miniaturansicht navigieren, können auf die Bedienfeld-Exitsteuerelemente zugreifen. Durch die Änderung werden Überspringungen entfernt und die Einhaltung von WCAG 2.4.3 verbessert. (SITES-25360)
* AEM aktualisiert die Schaltflächen **Listen** und **Absätze** im Rich-Text-Editor des Teaser-Modals, um ihren erweiterten und reduzierten Status anzuzeigen. Die Schaltflächen werden nun `aria-expanded` und geben die Statusänderung an Bildschirmlesehilfen an. Autoren erhalten klares Feedback und vermeiden Raten, bevor sie die Formatmenüs öffnen oder schließen. (SITES-25365)
* AEM gibt den Ladestatus im Teaser-Modal aus. Das Modal zeigt jetzt eine Live-Statusmeldung an, während der Inhalt geladen wird, sodass NVDA und JAWS „Wird geladen, bitte warten“ sprechen. Autoren sollten klares Feedback erhalten und es vermeiden, mit dem Dialogfeld zu interagieren, bevor es bereit ist. (SITES-25366)
* Verbessert die Statusmeldung auf der Registerkarte Asset des Dialogfelds zur Link-Auswahl. Wenn ein Fehler auftritt, fügt die Komponente eine lesbare Statusaktualisierung ein und sorgt dafür, dass der Tastaturfokus stabil bleibt, sodass NVDA/JAWS die Benutzer sofort informieren kann. (SITES-25368)
* Das Verhalten der Benutzeroberfläche im Notizbedienfeld wurde für sehr schmale Darstellungsfelder korrigiert. Bei 320 Pixel stießen Titel und Steuerelement „Hinzufügen“ zuvor zusammen. Die Symbolleiste fließt nun um und behält die klare Trennung zwischen Elementen bei. Autorinnen und Autoren können die Steuerelemente ohne Informations- oder Funktionsverlust bedienen. (SITES-25376)
* Fehlerkorrektur - Der Status „Fehler“ im **Teaser**-Dialogfeld auf der Registerkarte **Links und Aktionen** wurde behoben. Nachdem die Autoren **Call to action** aktiviert und leere oder ungültige Felder korrigiert haben, werden die Fehlerformatierung und das Symbol auf der Registerkarte gelöscht und die `aria-invalid` entfernt. Die Sprachausgabe gibt einen Fehler nicht mehr aus, sobald die Felder validiert wurden. (SITES-25527)
* Die Fehlerbehandlung in den Sites-Admin-Formularen entspricht jetzt den Erwartungen an die Barrierefreiheit. Wenn die Validierung fehlschlägt, wird der Fehler sofort auf der Seite angezeigt, der Fokus wird auf ein verwendbares Nachrichtenziel verschoben, und der Text wird für Bildschirmlesehilfen wie JAWS verfügbar gemacht. (SITES-27138)
* Beim Erstellen eines Ordners in Sites wird jetzt ein klarer Bestätigungsfoast angezeigt. JAWS kündigt die Nachricht über die Live-Region an, sodass Autoren nach der Aktion sofortiges, barrierefreies Feedback erhalten. (SITES-27141)
* Es wurde eine Barrierefreiheitslücke behoben, durch die Bilder in Authoring-Dialogfeldern ohne Alt-Text gerendert wurden. Das Dialogfeld bietet jetzt bei Bedarf beschreibenden ALT-Text und leeren ALT für rein visuelle Elemente, wodurch das konforme Verhalten für JAWS und andere Bildschirmlesehilfen wiederhergestellt wird. (SITES-27153)
* Verbesserte Fehlerbehandlung in Authoring-Dialogfeldern. Wenn ein Konfigurationsfehler auftritt, zeigt die Benutzeroberfläche über einen Warnhinweisbereich expliziten Text und Trigger als Ankündigung durch die Sprachausgabe an. Autoren erhalten sofortiges Feedback und können das Problem beheben, ohne den Kontext zu verlieren. (SITES-27155)
* Fehlerkorrektur: Die Barrierefreiheit von Reflow in Sites Admin funktioniert jetzt fehlerfrei. Bei einem Browser-Zoom von 400 % überschneiden sich die Steuerelemente der Symbolleiste und des Rasters und drücken die Tastenaktionen aus dem Bildschirm, wodurch die Tastaturnavigation und die Verwendung der Sprachausgabe blockiert wurden. Das Layout wird jetzt korrekt wiedergegeben, sodass die Such-, Filter- und Aktionsschaltflächen sichtbar und mit einem Zoom von 400 % bedienbar bleiben. (SITES-27238)
* Der niedrige Kontrast in der Sperrstatusmeldung, die im Workflow zum Sperren/Entsperren der Seite angezeigt wird, wurde korrigiert. Die Nachricht erreicht jetzt ein Verhältnis von 4,5 :1 verbessert die Lesbarkeit und ADA-Konformität für Autoren. (SITES-27270)
* Es wurden barrierefreie Namen zu den Häkchensymbolen im Dialogfeld **Gültige**&quot; hinzugefügt. JAWS kündigt nun die Symbole und ihre Bedeutung an, wodurch die Tastaturnavigation und die ADA-Konformität verbessert werden. (SITES-27272)
* Die ausgeblendete Kopfzeilennavigation akzeptierte den Fokus und verwirrte sowohl sehende als auch Menschen mit Bildschirmlesehilfen. Das Update deaktiviert den Fokus auf reduzierte Steuerelemente und stellt nur sichtbare Elemente bereit. Die Navigation bleibt vorhersehbar und erfüllt WCAG 2.4.3. (SITES-35224)

* Es wurde ein Problem mit den Symbolen für die Ordnerminiaturansicht in Sites Admin behoben, damit sie sich als dekorative Bilder verhalten. Durch die Aktualisierung wird die Bildrolle entfernt und leerer Alternativtext angewendet, sodass die Hilfstechnologie die Symbole ignoriert und nur aussagekräftige Beschriftungen liest. (SITES-2852)
* Adobe hat den Farbkontrast für den Referenztext auf der Sites-Startseite erhöht. Der Text erfüllt nun WCAG 2.1 AA mit einem Verhältnis von mindestens 4,5:1 und liest sich deutlich auf hellen Themen und hellen Bildschirmen. (SITES-24755)
* Der Orientierungspunkt für die Leiste „Verweise“ gibt jetzt seinen Namen für Bildschirmlesehilfen aus. Die Region verfügt über eine eindeutige `aria-label` („Leiste „Verweise„), die die Navigation durch Orientierungspunkte verbessert und sie von anderen Regionen unterscheidet. (SITES-24973)
* Die RTE-Beschreibung blockierte die Vorwärtsregisterkartennavigation und unterbrach den Dialogfeldfluss. Der Fix stellt die standardmäßige Tastaturbewegung wieder her. Autoren setzen das Feld mit einer einzigen Registerkarte fort und halten die Auswahlreihenfolge vorhersehbar. (SITES-35228)
* Bei der Bearbeitung von Steuerelementen fehlten barrierefreie Namen und der Text mit unformatierten Symbolen, was JAWS verwirrte. Die Fehlerbehebung fügt explizite ARIA-Bezeichnungen und Standardrollen hinzu. Ankündigungen klingen korrekt und entsprechen den Erwartungen an die Barrierefreiheit. (SITES-35227)
* In der Dropdown-Liste Kategorien fehlte eine bestimmte Beschriftung, sodass JAWS ein generisches „Menü für Bildschaltflächen“ sprach. Das Update benennt das Steuerelement als „Kategorien“ und definiert seine Rolle. Benutzende von Bildschirmlesehilfen hören eine genaue Beschriftung und verstehen die verfügbaren Optionen. (SITES-35226)
* Im Dialogfeld „Eigenschaften“ wurde ein Datenraster angezeigt, das von Sprachausgaben als reiner Text behandelt wurde. JAWS und NVDA haben den Fokus verpasst und konnten keine Zeilen und Spalten ankündigen. Die Korrektur fügt echte Tabellensemantik und ARIA-Rollen hinzu. Die Sprachausgabe erkennt die Tabelle jetzt und verfolgt den Fokus korrekt. (SITES-35225)
* Der Inhaltsfragment-Texteditor wurde mit einer abgeschnittenen Aktionsleiste geladen. Symbole abgeschnitten und das Überlaufmenü wurde unerreichbar. Durch die Aktualisierung wird das Layout korrigiert, sodass die vollständige Symbolleiste sichtbar und zugänglich bleibt. (SITES-33005)
* In den Formularfeldern der Registerkarte „Allgemein“ konnte kein hilfreicher Fehlertext angezeigt werden. Das Formular zeigt jetzt klare Inline-Nachrichten an und verknüpft sie mit dem Feld für Bildschirmlesehilfen. Benutzer von Tastatur und Hilfstechnologie erhalten sofortige Anleitungen, um Eingaben zu beheben. (SITES-32480)
* Das in einer benutzerdefinierten Komponente verwendete Multifield zeigt nicht beschriftete Symbolschaltflächen und inkonsistente Registerkartenreihenfolge an. JAWS/NVDA kündigte nur „button“ oder übersprungene Steuerelemente an, die den Tastaturbetrieb blockierten. Die Aktualisierung bietet beschreibende Namen für „Hinzufügen“, „Entfernen“ und „Verschieben“, normalisiert Tabstopps und kündigt Listen-Updates an, um die ADA-Erwartungen zu erfüllen. (SITES-30660)
* Quick Publish gibt jetzt eine klare Erfolgsbenachrichtigung zurück. Das Dialogfeld wird geschlossen, ein Popup bestätigt die Aktion, und die Sprachausgabe gibt die Nachricht aus, damit Autoren das Ergebnis nicht verpassen. (SITES-26912)
* Keine Änderung erforderlich. Adobe prüfte die Behauptung, dass sich das Suchsymbol mit dem Text in der Nähe überschneidet. Die Kopfzeile enthielt eine vom Kunden hinzugefügte Beschriftung; Vanilla AEM rendert nur das Symbol. Eine bereinigte Instanz zeigt das richtige Layout mit 100 % Zoom an, sodass der Fehler außerhalb des Bereichs geschlossen wurde. (SITES-26910)
* Seitendesigns erstellen blendet den Fokusstatus nicht mehr aus. Aquatische und Wüsten -Stile rendern bei der Tastaturnavigation ein konsistentes Highlight auf der Registerkarte **Standard** und den angrenzenden Registerkarten. Diese Änderung stellt vorhersehbares, wahrnehmbares Fokus-Feedback für sehschwache Benutzende wieder her. (SITES-26907)



#### Admin-Benutzeroberfläche{#sites-adminui-6524}

Benutzende von Bildschirmlesehilfen erhielten keine Navigationshilfe im Raster **Catalog System Blueprint**. JAWS gab nur die Zellposition an und verstummte dann. Die Version fügt barrierefreie Anleitungen und Rollen hinzu, sodass JAWS den Listenkontext, das ausgewählte Element und die erforderlichen Pfeilsteuerelemente lesen kann. (SITES-30661)

#### Klassische Benutzeroberfläche{#sites-classicui-6524}

Kontrollkästchen der klassischen Benutzeroberfläche haben ihre Bezeichnungen verloren und zeigten leere Optionen an. Dialogfelder zeigen auch kodierte HTML an, z. B. `<br>`. Durch die Aktualisierung werden Kontrollkästchen-Beschriftungen wiederhergestellt und Markup decodiert, sodass Dialogfelder korrekt gelesen werden. (SITES-31822)

<!--
#### [!DNL Content Fragments]{#sites-contentfragments-6524}
-->

#### [!DNL Content Fragments] – Admin{#sites-admin-6524}

Durch Klammern im Namen eines Inhaltsfragments wurde im Bedienfeld „Verweise“ eine falsche Berichterstellung zur Nutzung durchgeführt. Autoren sahen 0, selbst wenn andere Fragmente darauf verwiesen. Die Korrektur korrigiert das Parsen des Pfads für „(“ und „)“ und zeigt die korrekten Zählungen und Einträge ungleich null an. (SITES-35078)


#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-6524}

* Die Veröffentlichung von Inhaltsfragmenten, deren DAM-Pfad Klammern enthielt, konnte nicht aufgehoben werden. Der Assistent Veröffentlichung verwalten hat „(“ und „)“ umgeschrieben und den Asset-Pfad beschädigt. Die Korrektur behält die Zeichen bei und löst das richtige Element auf, sodass die Aktion zum Rückgängigmachen der Veröffentlichung abgeschlossen ist. (SITES-35077)
* Beim Bearbeiten eines Inhaltsfragments und Zurückkehren zur Assets-Liste wird das Fragment oder der gesamte Ordner ausgeblendet. Die Liste konnte nach dem Schließen des Editors nicht aktualisiert werden. Durch die Korrektur wird die Liste nun zuverlässig aktualisiert und das bearbeitete Fragment bleibt ohne erneutes Laden sichtbar. (SITES-35374)

* Der Inhaltsfragment-Editor konnte die Polaris-Asset-Auswahl nicht öffnen, da die erforderlichen IMS-Bereiche entfernt wurden. Durch die Korrektur werden die minimalen Bereiche wiederhergestellt und die Bereitstellungsverbindung wieder hergestellt. Das Durchsuchen und Auswählen von Assets funktioniert wieder, ohne HTTP 500-Fehler. (SITES-35837)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6524}

Nach jeder Bereitstellung begannen gültige GraphQL-Abfragen, `GraphQL_QueryValidationError` zurückzugeben. Der Endpunkt behielt ein veraltetes Schema bei, bis Teams Caches leerten oder neu starteten. Durch die Fehlerbehebung werden das GraphQL-Schema und die Registrierung persistierter Abfragen während der Bereitstellung aktualisiert und normale Antworten werden sofort wiederhergestellt. (SITES-34301)

<!--
#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6524}


#### [!DNL Content Fragments] - REST API{#sites-restapi-6524}


#### Component Console{#sites-component-console-6524}


#### Core Backend{#sites-core-backend-6524}


#### Core Components{#sites-core-components-6524}


#### Campaign integration{#sites-campaign-integration-6524}
-->


#### ContentHub {#sites-contenthub-6524}

ContextHub fügt auf Veröffentlichungsseiten keine zweite jQuery-Kopie mehr ein. Die Segment-Engine-Client-Bibliothek löscht die CQ.Shared-Abhängigkeit, die jQuery 1.12.4 abgerufen hat, sodass Sites eine konsistente jQuery laden und Frontend-Code zuverlässig funktioniert. (SITES-30404)

#### Experience Fragments{#sites-experiencefragments-6524}

* Experience Fragments lokalisieren jetzt die Warnung, die angezeigt wird, wenn keine Adobe Target-Konfiguration vorhanden ist. Die Nachricht wird im Gebietsschema des Autors anstelle von Englisch angezeigt, sodass Export- und Aktivierungsschritte für globale Teams korrekt gelesen werden. (SITES-11868)
* Beim Veröffentlichen einer Experience Fragment-Variante wird jetzt eine lokalisierte Fehlermeldung angezeigt, wenn kein Cloud-Service an die Variante angehängt wird. Die Meldung wird auf der Benutzeroberfläche in der Sprache der Benutzerin bzw. des Benutzers anstelle einer reinen englischen Zeichenfolge angezeigt. (SITES-20293)
* Das Exportieren eines Experience Fragments nach Target stürzte mit `Attempt to modify attribute at illegal index: -1` ab. Web Vitals-Instrumentierung steht im Konflikt mit dem Exporter und fehlerhafte Attributbehandlung. Die Korrektur härtet die Attributverarbeitung ab und entfernt diesen Konflikt. Exportiert erfolgreich und das Fragment wird in Target gerendert. (SITES-31891)

* Experience Fragment-Eigenschaften lokalisieren jetzt die Registerkarte **Verweise** . Bezeichnungen und Spaltenüberschriften wie „Seite“, „Seitenpfad“ und „Variantentitel“ werden in der Sprache des Autors angezeigt. Durch diese Änderung werden auf Englisch beschränkte Zeichenfolgen entfernt und die Eigenschaftenansicht für globale Teams bleibt konsistent. (SITES-11203)
* Der **Varianten** > **Workflow erstellen** zeigt jetzt den vollständigen Übersetzungstext an. Das Dialogfeld verarbeitet lange Gebietsschema-Zeichenfolgen, indem Inhalte korrekt umgebrochen und skaliert werden, sodass abgeschnittene oder abgeschnittene Beschriftungen entfernt werden. (SITES-19304)
* Experience Fragment-Eigenschaften lokalisieren jetzt die Social-Media-Statuskennzeichnungen. Autoren sehen in allen Gebietsschemata Statuswerte wie „Gepostet“ und „Nicht veröffentlicht“ in der ausgewählten Sprache. Durch diese Änderung werden auf Englisch beschränkte Zeichenfolgen entfernt, die bei der Überprüfung zu Verwirrung geführt haben. (SITES-20014)

<!--
#### Foundation Components (Legacy){#sites-foundation-components-legacy-6524}
-->

#### Launches{#sites-launches-6524}

* Durch das Löschen eines sehr großen Launches wurde das Repository eingefroren. Der Auftrag hatte zu viele Entfernungen in die Warteschlange gestellt und andere Anforderungen waren knapp geworden. Die Korrektur löscht jetzt Batches und gibt zwischen Blöcken zurück, sodass die Bereinigung abgeschlossen wird, während das System responsiv bleibt. (SITES-32004)

* „Launch-Konfiguration“ > „Eigenschaften“ zeigt Dropdown-Listen für funktionierende Unternehmen und Eigenschaften an. **Speichern** und **Schließen** berücksichtigt ausgefüllte Felder, und bei der Titelvalidierung werden keine Fehler mehr für „Unternehmen“ oder „Eigenschaft“ Trigger. (CQ-4359853)
* Erforderliche Prüfungen in der IMS-Konfiguration werden bei der Aktualisierung ausgeführt, nicht nur bei der Erstellung. Leere Werte in Feldern wie Client-ID oder Client-Geheimnis zeigen einen Fehler an und halten das Speichern an, bis ein gültiger Wert eingegeben wird, wodurch die Wiederverwendung des vorherigen Werts verhindert wird. (CQ-4359938)
* Die Launch-Erstellung zeigt übersetzte Validierungs- und Fehlerzeichenfolgen an. Nur-Englisch-Nachrichten für Erstellungsfehler und fehlende Quellseiten werden nicht mehr angezeigt. Autoren sehen beim Einrichten von Launch ein klares, gebietsschemakorrektes Feedback. (SITES-13085)
* Launch-Promotion aktualisiert die Seiteneigenschaften `jcr:title`, `jcr:description` und `cq:redirectTarget` auf der Quellseite. Durch die Änderung werden Eigenschaftenausschlüsse in der MSM-Rollout-Konfiguration und der Workflow-Logik entfernt. Kampagnen, Übersetzungen und SEO sorgen für konsistente Titel, Beschreibungen und Weiterleitungen. (SITES-34509)
* Die Launch-Aktion ignorierte den Bereich und schloss Seiten ein, die dasselbe übergeordnete Element wie der Zielabschnitt hatten. Die Aktualisierung erzwingt die Grenzen der Unterstruktur und stuft nur die ausgewählte Seite und ihre untergeordneten Seiten hoch. Nicht verwandte Seiten behalten ihren vorhandenen Inhalt bei. (SITES-34344)
* Fehlerkorrektur - Verschachtelte automatische Launch-Promotion, die bei der Autoreninstanz angehalten und die Veröffentlichungsebene übersprungen wurde, wird jetzt behoben. Die automatische Promotion für einen untergeordneten Launch veröffentlicht die aktualisierten Seiten bei den konfigurierten Publishern und schließt den vollständigen Launch wie geplant ab. (SITES-30420)

<!--
#### Link Checker{#sites-link-checker-6524}
-->

#### MSM – Live Copies{#sites-msm-live-copies-6524}

* Bei einem Rollout auf Ordnerebene konnten keine Live Copies für Experience Fragments unter diesem Ordner erstellt werden. Einzelne Rollouts funktionierten, wodurch Massen-Workflows unterbrochen wurden. Durch die Änderung wird der Rollout-Ordner am Seitenverhalten ausgerichtet und Beziehungen und Verweise über die Unterstruktur verteilt. (SITES-35161)
* Nach dem Löschen einer Komponente in einer Live Copy wurde **Vererbung aktivieren** mit einem JavaScript-Fehler unterbrochen. Die Komponente blieb bis zu einem zweiten Versuch fehlend. Das Update behebt das nach dem Löschen gelöschte Neuladen, um die richtigen Parameter zu übernehmen, und ersetzt den veralteten Warnhinweis-Aufruf. Das Dialogfeld wird sauber geöffnet und die Vererbung wird beim ersten Versuch wiederhergestellt. (SITES-31387)
* Der Rollout-Assistent akzeptiert **Später** ohne Datum. Die Autoren haben einen Rollout ohne Zeitplan erstellt und erweitert. Die Aktualisierung erzwingt die Datumsauswahl und zeigt eine klare Eingabeaufforderung an. Die **Fortfahren**-Aktion bleibt deaktiviert, bis ein Datum vorhanden ist. (SITES-31374)


#### Seiteneditor{#sites-pageeditor-6524}

* Beim Öffnen der Inhaltsstruktur auf einer Seite mit einem Personalization-Container wurde ein leeres Bedienfeld und ein Konsolen-Nullverweisfehler zurückgegeben. Autoren konnten keine Komponenten auswählen oder konfigurieren. Durch die Aktualisierung wird der Fehler entfernt und die Interaktionen zwischen Baumstruktur und Komponente werden erneut aktiviert. (SITES-34336)
* Im Seiteneditor wurde durch den Wechsel des Unterbrechungsmodus für AEM 6.5 SP23 der Modus deaktiviert. Durch Klicken auf **Layout**, **Entwickler** oder **Targeting** blieb der Editor im Modus **Bearbeiten** stecken und löste eine `TypeError` aus. Die Aktualisierung stellt Änderungen am Symbolleistenmodus wieder her und löscht den Fehler. (SITES-34536)
* Der Seiteneditor ist von der Einfügemarke weggesprungen, als Autoren Komponenten in langen Containern hinzugefügt haben. Mit der Aktualisierung werden die Zeitplanung für Überlagerungen und die Scroll-Verwaltung angepasst. Die Ansicht behält ihren Platz und die neue Komponente bleibt in Sicht und kann konfiguriert werden. (SITES-32621)
* Im Seiteneditor sind benutzerdefinierte Tag-Kennzeichnungen fehlgeschlagen und in der Benutzeroberfläche wird immer „Tags“ angezeigt. Das Prädikat wertet jetzt `fieldLabel` ersten und `labelText` zweiten aus und wendet dann den Standard an. Autoren sehen die von ihnen festgelegte Beschriftung. (SITES-32278)
* Durch Abbrechen des Standortfilters in Sites wurde das OmniSearch-Symbol falsch ausgerichtet und mit dem Platzhaltertext überlagert. Das Symbol wurde unklickbar. Durch die Korrektur wird das Symbol neu ausgerichtet und der Trefferbereich wiederhergestellt, sodass Maus und Tastatur beide Trigger durchsuchen. (SITES-30946)
* Bei Auswahl von Entwickler befindet sich die Seite in einem schlechten Zustand und wurde das Authoring auf dieser Seite blockiert. Das Bedienfeld verschwand und die Benutzeroberfläche reagierte nicht mehr. Durch das Update werden die Modus-Umschalter-Logik und die Cache-Handhabung repariert, sodass die Seite bearbeitbar bleibt und Entwicklerdaten sofort angezeigt werden. (SITES-30922)
* Durch Klicken auf **Löschen** in **Neue Komponente einfügen** wurde die Suchabfrage nicht entfernt und die Liste in ein einzelnes Element (Akkordeon) gefiltert. Durch die Fehlerbehebung wird die Abfrage zurückgesetzt und die Liste aktualisiert. Alle zulässigen Komponenten werden erneut angezeigt. (SITES-30921)

<!--
#### Replication{#sites-replication-6524}
-->

#### Rich-Text-Editor{#sites-rte-6524}

* Im Vollbildmodus blendet der Rich-Text-Editor das Ergebnis der Rechtschreibprüfung hinter dem Dialogfeld aus, wenn keine Fehler vorhanden waren. Durch die Aktualisierung wird das Ergebnisfenster nach vorne verschoben und Nachrichten und Vorschläge bleiben sichtbar. Autoren können Korrekturen überprüfen und akzeptieren, ohne das Vollbild verlassen zu müssen. (SITES-32366)
* Rich-Text-Editor-Bilder berücksichtigen jetzt die ausgewählte Ausrichtung. Autorinnen und Autoren legen im Bilddialogfeld links, zentriert oder rechts fest und der Editor wendet diese Auswahl in der Ausgabe konsistent an. Die Änderung stabilisiert auch das Dialogfeld „Alternativtext“, sodass Alternativtext und Ausrichtung gespeichert und über Neubearbeitungen hinweg beibehalten werden. (SITES-30634)

#### Universeller Editor {#sites-universal-editor-6524}

Das Konfigurieren des Authentifizierungs-Handlers für Abfrage-Token verwirrte Benutzende, da die Kennzeichnungen nicht mit den Feldern übereinstimmten. Die Benutzeroberfläche hat Text aus dem Pfad abgerufen und die falschen Namen angezeigt. Die Korrektur stellt klare, genaue Beschriftungen für Service-Ranking- und Abfrage-Token-Optionen wieder her. (SITES-31305)


### [!DNL Assets]{#assets-6524}


#### [!DNL Dynamic Media]{#assets-dm-6524}

* Die **Miniaturansicht auswählen** für Videos verhält sich jetzt in AEM Assets - Dynamic Media korrekt. Durch Klicken wird das Dialogfeld geöffnet und die Auswahl einer Miniaturansicht aus Assets ermöglicht, wodurch das vorherige Deadclick-Verhalten entfällt und die Beschränkung auf die Videoframe-Extraktion aufgehoben wird. (ASSETS-58926)


### [!DNL Forms]{#forms-6524}

<!--
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, December 4, 2025. In addition, a list of Forms fixes and enhancements is added to this section.
-->

#### Forms Designer

* Benutzende hatten Probleme mit Hyperlinks, auf die in bestimmten Testfällen nicht geklickt werden konnte, was sich auf ihre Fähigkeit auswirkte, innerhalb der Anwendung zu navigieren und Links zu überprüfen. (LC-3923505)
* Benutzende hatten Probleme mit der Barrierefreiheit von PDFs, die mit AEM Forms Designer 6.5.23 für nicht lateinische Sprachen generiert wurden. Pfad-Tags wurden nicht in einem Artefakt-Container platziert, was zu Fehlern bei der PAC- und Bildschirmlesehilfe-Prüfung führte. (LC-3923295)
* Benutzende haben fehlerhafte Hyperlinks in PDF-Textfeldern (Portable Document Format) erlebt, nachdem sie von Version 6.5.21 auf 6.5.23 mit dem Ausgabe-Service gepatcht hatten. (LC-3923290)
* Benutzende hatten Probleme mit der Barrierefreiheit bei Datensatzdokument-Formularen (DoR). Wenn Eingabefelder leer waren, lesen Sprachausgaben nur die Feldbeschriftungen und nicht die Werte. Dadurch wird es für Benutzende mit Behinderungen schwierig, effektiv in den Formularen zu navigieren. (LC-3923234)
* Benutzende sahen sich mit Barrierefreiheitsproblemen in DoR PDF forms konfrontiert, wo NVDA fälschlicherweise für Kontrollkästchen, Optionsfelder und Textfelder „nicht verfügbar“ las, was häufig die Meldung wiederholte und für Benutzende der Bildschirmlesehilfe Verwirrung stiftete. (LC-3923201)
* Beim Hinzufügen neuer Felder trat in der XDP eine Diskrepanz in der Tabulatorreihenfolge auf. Die vorhandene Registerkartenreihenfolge hat sich unerwartet geändert, was sich auf die Formularnavigation ausgewirkt hat. (LC-3923183, LC-3922630)
* Benutzende hatten Probleme mit dem HTML-Rendering. Bei Verwendung des `docReady`-Ereignisses ist der Trigger in HTML nicht korrekt, sodass Skripte nicht wie erwartet ausgeführt werden. (LC-3923118)
* Benutzende hatten Probleme mit PDF-Rendering-Skripten, die nicht in der AEM Forms Cloud-Produktionsumgebung funktionierten. (LC-3923082 )
* Benutzende hatten Probleme mit schwebenden Feldern in Formularen. Bei Verwendung verschiedener Datendateien werden schwebende Felder mit einer Datei korrekt gerendert, aber nicht mit der anderen, trotz geringfügiger Unterschiede, die nicht mit den Feldern zusammenhängen. (LC-3923056)
* Benutzende erlebten eine leere spanische Musterseite, wenn in einem XDP (XML-Datenpaket) mit mehreren Musterseiten nur englischer Inhalt ausgewählt wurde. (LC-3923009)
* In der AEM Designer haben Nutzer veraltete Copyright-Jahr-Informationen beobachtet. Dies trat im Popup-Feld beim Start, im Abschnitt „Über“ und im Abschnitt „Rechtliche Hinweise“ auf, wo „2003-2024“ anstelle von „2003-2025“ angezeigt wurde. (LC-3923005)
* Benutzende entdeckten eine leere PDF-Seite bei Verwendung von Paginierung in AEM Forms Designer. Bei der Auswahl von „Anfang der nächsten Seite/Anfang der Seite“ für den WireAdvice-Header trat ein Problem auf, das das Layout von Dateniterationen störte. (LC-3922997, LC-3922830)
* Bei Benutzenden trat ein Problem auf, bei dem der filedigest-Wert für XML-Schemadefinition (Extensible Markup Language) in der 64-Bit-Version von AEM Forms Designer nicht beibehalten wurde. (LC-3922924)
* In AEM Designer 6.5.19 kam es zu einer instabilen Hyperlink-Formatierung, bei der Hyperlinks in einem Textfeld fälschlicherweise Stile aus dem umgebenden Text übernahmen, z. B. die Formatierung des ersten Zeichens. (LC-3922376)
* Bei Benutzenden traten Probleme beim Rendern von HTML-Formularen über das mobile Rendering auf MAC mit AEM Forms OSGI v6.5.22 auf. (LC-3923058)
* Bei der Verwendung von mit Designer 6.5.23 erstellten und mit PAC 2024 analysierten XDP-Vorlagen in Dateien mit Portable Document Format (PDF) traten Fehler vom Typ „Pfadobjekt ohne Tags“ auf. (LC-3923013)
* Benutzende haben einen Fehler mit der Hintergrundfarbe der Überschrift „Dati Richiedente“ in Portable Application Component (PAC) erhalten und die Nachricht „path object not tagged“ erhalten. (LC-3922912)
* Bei Benutzenden trat ein Problem auf, bei dem bestimmte Vorlagen die beabsichtigte Schriftart durch eine verkürzte Schriftart ersetzt haben. (LC-3922330)

#### Adaptive Formulare

* Benutzende hatten fehlende Optionen im Regeleditor. Wenn Autoren Regeln für Zahleneingaben geschrieben haben, waren die Optionen Abfrage, UTM und Browser-Details nicht verfügbar. (FORMS-21660)
* Bei der Interaktion mit OdataResponse kam es aufgrund einer Nullzeiger-Ausnahme zu Anwendungsabstürzen. (FORMS-20344)
* Benutzende hatten Probleme beim Erstellen von Regeln, um einen Bereich anzuzeigen und den Fokus auf ein darin enthaltenes Element zu legen. Die setFocus-Regel, die vor der Aktualisierung der Sichtbarkeit ausgeführt wurde, was dazu führte, dass die Fokusaktion fehlschlug. (FORMS-19563)
* Benutzende hatten Probleme mit der Komponentenauswahl in der AEM Forms-Autoreninstanz. Beim Navigieren zwischen Registerkarten im Bearbeitungsmodus konnten einige Container nicht mehr ausgewählt werden, was eine einfache Identifizierung und Interaktion verhinderte. (FORMS-18525)
* Beim Versuch, Assets in AEM 6.5.22 mit Anmerkungen zu versehen, ist ein Fehler „Ungültige URL“ aufgetreten. (NPR-42684)

### Foundation {#foundation-6524}


#### Apache Felix {#foundation-apachefelix-6524}

Das Felix Web Console-Bundle wurde aktualisiert und enthält jetzt FELIX-6747. Dieser Patch korrigiert die Antwortbehandlung, die zuvor das Rendern und die Authentifizierung der Seite in der OSGi-Web-Konsole beschädigt hat. Die Konsole wird konsistent geladen und löst keine IllegalStateException-Einträge mehr in den Protokollen aus. (NPR-42730)

<!--
#### Campaign{#foundation-campaign-6524}

#### Cloud Services{#foundation-cloudservices-6524}

#### Communities {#foundation-communities-6524}

#### Content distribution{#foundation-content-distribution-6524}

#### CRX {#foundation-crx-6524}
-->

#### Granite{#foundation-granite-6524}

* Unformatierte oder Nur-Englisch-Zeichenfolgen werden im Dialogfeld **Zugriffssteuerung entfernen** nicht mehr angezeigt. Das Dialogfeld stellt vollständig lokalisierte Inhalte in allen unterstützten Sprachen bereit, um eine konsistente Barrierefreiheit zu gewährleisten. (GRANITE-48479)
* Das Hilfesymbol legt jetzt eine knappe Beschriftung für Hilfstechnologien offen. JAWS liest „Hilfe-Schaltfläche“ und fügt keine überflüssige „Menü“-Formulierung mehr hinzu. Diese Aktualisierung bringt das Steuerelement in die WCAG 4.1.2-Konformität und vereinfacht die Verwendung von Tastatur und Bildschirmlesehilfe. (GRANITE-55360)
* Stellen Sie die HTL Script Engine-Factory wieder her, nachdem Sie eine Abhängigkeitsschleife in OSGi-Diensten beseitigt haben. Umgebungen starten sauber, das HTL-Rendering funktioniert auf allen Autoren-Pods, und Admins stoßen nicht mehr auf Startfehler oder fehlende Skript-Services. (GRANITE-58276)

* Das Suchfeld für die Kopfzeile überlagert nicht mehr das Lupensymbol auf dem Platzhaltertext. Der Platzhalter wird mit dem richtigen Abstand angezeigt und bleibt in allen Browsern vollständig lesbar. (GRANITE-54391)
* Autoren sehen lesbare Beschriftungen in Feldern mit automatischer Vervollständigung anstelle von Rohwerten im Dialogfeld. Die Implementierung behält den -Wert in JCR bei und verbessert die Klarheit für Konfigurationen mit einer oder mehreren Auswahlen, die Optionen dynamisch zur Quelle hinzufügen. (GRANITE-57615)
* Der Bearbeitungsmodus bleibt funktionsfähig, wenn htmlLibraryManager.debug auf „true“ gesetzt ist. Die Änderung stellt die ordnungsgemäße Auflösung und das Laden der Client-Bibliotheken wieder her, sodass Entwicklerinnen und Entwickler die Debugging-Tools von HTML Library Manager beim Authoring verwenden können. (GRANITE-58002)
* Die Seite zur Bearbeitung des Replikationsagenten gibt in der klassischen Benutzeroberfläche keinen JavaScript-Fehler mehr aus. Die Seite wird geöffnet, zeigt alle Registerkarten an und speichert Agenteneinstellungen ohne Konsolenfehler. (GRANITE-58302)
* Korrektur der Aggregation des Gesundheitsstatus in der Systemübersicht. Die Ansicht wird jetzt nach der Ausführung einzelner Prüfungen aktualisiert und zeigt die richtigen Zahlen an. Operatoren sehen „OK“, wenn die Sicherheits- und Wartungsprüfungen erfolgreich abgeschlossen werden, anstelle eines falschen Banners mit „2 Fehler“. (GRANITE-61482)
* Ausführung von `CodeUpgradeTasks` während AEM 6.5 LTS-Upgrades (Langfristiger Support) gestoppt. Das Upgrade wird jetzt ohne durch eine Aufgabe ausgelöste Repository-Änderungen oder -Neukonfigurationen fortgesetzt. Diese Fehlerbehebung reduziert das Upgrade-Risiko und verhindert vermeidbare Ausfallzeiten. (GRANITE-61486)
* In Dialogfeldern zum Authoring zeigen Pflichtfelder jetzt einen einzelnen, genauen Validierungsfehler an. Die Nachricht verwendet, sofern vorhanden, die eigene Beschriftung des Felds und greift auf eine generische Eingabeaufforderung zurück, wenn keine Beschriftung vorhanden ist. Duplizierte und nicht übereinstimmende Nachrichten werden nicht mehr in allen Feldern angezeigt. (GRANITE-59531)
* Das Dialogfeld „Seitenerstellungsassistent“ überprüft jetzt bei jeder Interaktion die erforderlichen Felder neu, einschließlich Registerkartenänderungen und Mehrfachfeld-Bearbeitungen. Die **Erstellen**-Schaltfläche bleibt deaktiviert, bis Autoren alle erforderlichen Eingaben abgeschlossen haben, und der Assistent zeigt Inline-Fehler für fehlende Werte an. (GRANITE-58826)

#### Integrationen{#foundation-integrations-6524}

Die Veröffentlichung von AEM Target-Aktivitäten schlägt nicht mehr fehl, wenn Autorinnen und Autoren das Start- und Enddatum festlegen. Die Integration sendet standardkonforme Zeitstempel, die die Zeitzone enthalten, sodass Target die Payload der Aktivität verarbeitet und die Synchronisierung erwartungsgemäß abschließt. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-6524}
-->

#### Lokalisierung{#foundation-localization-6524}

* Durch die Lokalisierung in zh-CN wird eine mehrdeutige Phrase im Status der Referenzerfassung entfernt, der bei Asset-Vorgängen wie Verschieben angezeigt wird. Die Benutzeroberfläche zeigt jetzt `正在获取对 [[0]] 项的引用` an und bietet somit eine genaue Bedeutung und konsistente Terminologie. (CQ-4354648)
* Beim Erstellen einer Smart-Sammlung werden Keywords für gespeicherte Suchen bei der Aktualisierung nicht mehr übersetzt. Autoren, die englische Begriffe eingeben, sehen, dass dieselben Begriffe beibehalten werden, und die Sammlung liefert weiterhin konsistente Ergebnisse. (NPR-43158)
* Abgeschnittener QuickInfo-Text im Bildbereich wurde korrigiert. Die Beschreibung „Beschriftung als Pop-up anzeigen“ wird vollständig in allen unterstützten Gebietsschemata gerendert, was die Anleitung für nicht-englische Autoren verbessert. (SITES-10490)
* Sites Admin-Spaltenansicht Abgeschnittene lokalisierte Kennzeichnungen in Französisch und Spanisch. „End Time“ und „Off Time“ schienen abgeschnitten und zeigten keine QuickInfo. Adobe korrigierte die Übersetzungen und stellte die QuickInfo beim Bewegen des Mauszeigers wieder her, sodass die Beschriftungen vollständig gelesen wurden. (SITES-31318)
* Das **Verschieben**-Dialogfeld in Sites zeigte rohe i18n-Schlüssel anstelle lesbarer Beschriftungen. Elemente wie „Verweisende Seiten“, „Erstellt am“, „Erstellt von“ und „Pfad“ sahen verstümmelt aus. Durch die Korrektur wird das Dialogfeld an die richtigen Wörterbücher angehängt und Übersetzungen mit einem Fallback in englischer Sprache bereitgestellt. (SITES-30881)

<!--
#### Oak {#foundation-oak-6524}
-->

#### Platform{#foundation-platform-6524}

* Bei Validierungsfehlern wird jetzt anstelle eines Symbols ein klarer, beschreibender Text angezeigt. Die Sprachausgabe gibt die Nachricht automatisch aus, wenn sie angezeigt wird, sodass Benutzende nicht zu einem Symbol navigieren müssen, um zu erfahren, was schiefgelaufen ist. (CQ-4359152)


* Mauszeiger-Beschriftungen in der Navigationsleiste bleiben nicht mehr auf dem Bildschirm, nachdem der Cursor vom Steuerelement weg bewegt wurde. Die Benutzeroberfläche blendet diese QuickInfos sofort bei ausgeblendeter Maus oder Ausblenden der Maus aus, um visuelles Durcheinander und Fehlklicks zu vermeiden. (CQ-4360030)
* In Sites erstellen Symbolleistenaktionen bei wiederholten Klicks kein zweites Popup mehr. Mit dem zweiten Klick wird das bestehende Popup geschlossen, sodass nur eine Instanz sichtbar bleibt. Überschneidungen und Ablenkungen werden vermieden. (CQ-4360038)
* Der veraltete Copyright-Text für 2024 wird nicht mehr angezeigt. Die Anmeldeseite und das **Hilfe** > **Über AEM**-Popup zeigen 2025, und AEM liest das Jahr programmgesteuert, um manuelle Bearbeitungen zu vermeiden. (CQ-4360042)
* Durch Klicken auf eine QuickInfo in der AEM-Kopfzeilenleiste wird die zugrunde liegende Aktion nicht mehr Trigger. Popups werden nur geöffnet, wenn Benutzer auf die tatsächliche Schaltfläche klicken, wodurch verhindert wird, dass bei der Interaktion mit QuickInfo-Text versehentliche Dialogfelder angezeigt werden. (CQ-4360105)
* Durch den Jahr-Rollover bleibt der Copyright-Text nicht mehr veraltet. Der Anmeldebildschirm und das Dialogfeld **Hilfe** > **Über AEM** leiten das Jahr von der Systemuhr ab und geben bei jedem Laden der Benutzeroberfläche den aktuellen Wert an. (CQ-4360173)
* Header-Pop-ups werden jetzt korrekt umgeschaltet. Wenn Sie auf dieselbe Aktion klicken (z **B.** oder **Filter**, wird das geöffnete Popup geschlossen, anstatt eine weitere Überlagerung zu öffnen. Die Änderung verhindert gestapelte Popups und kehrt zum Header-Steuerelement zurück. (NPR-42891)
* Projekte und Kalenderansicht im Posteingang werden korrekt gerendert. Durch das Wechseln der Ansichten wird die Seite nicht mehr leer angezeigt. Der Kalender wird geladen und zeigt geplante Elemente an. (NPR-42968)

<!--
#### Security{#foundation-security-6524}
-->

#### Sling{#foundation-sling-6524}

* Fehlerkorrektur - Im Bundle `org.apache.sling.scripting.jsp:2.6.0` tritt jetzt kein unerwarteter JSP-Kompilierungsfehler mehr auf. (SLING-12442)
* Die Plattform aktualisiert die Kern-Sling-Engine von 2.16.2 auf 2.16.6. Die neuere Engine härtet die Eingabevalidierung ab und stabilisiert die Anforderungsverarbeitung unter Last. (NPR-43105)

#### SPA-Editor {#foundation-spa-editor-6524}

Beim Aktivieren des Sling-Haupt **Servlets (Inhaltstyp überprüfen** werden `.model.json` Exporte in AEM 6.5 SP21/22 überschrieben. Anfragen haben HTML oder Fehler zurückgegeben, da der Exporter den Mid-Chain-Typ umgekehrt hat. Die Fehlerbehebung gibt von Anfang an JSON mit dem richtigen Typ aus, sodass `.model.json` in Autoren- und Veröffentlichungsumgebungen funktioniert. (SITES-32634)


#### Übersetzung{#foundation-translation-6524}

* Es wurde ein Neuindizierungsvorgang für den Status des Übersetzungsprojekts hinzugefügt. Administratoren können den Backing-Index neu erstellen, wenn die Statusansicht nicht mehr synchronisiert ist, Ergebnisse wiederherstellen und Oak-Durchlaufwarnungen eliminieren. Die Seite wird schneller geladen und zeigt den aktuellen Auftragsstatus an. (NPR-42699)
* Es wurde eine Regression behoben, bei der XLIFF-Importe erfolgreich waren, JSON-Wörterbuchdateien jedoch unverändert blieben. Importe zielen jetzt auf den richtigen i18n-Pfad ab und persistieren Übersetzungen, sodass die Roundtrips zur Lokalisierung ohne manuelle Bearbeitung abgeschlossen sind. (NPR-42989)


* Die XML für Übersetzungsregeln funktioniert jetzt wie konfiguriert. Das Übersetzungs-Framework berücksichtigt Ausnahmeregeln und wendet `include`- und `exclude` bei der Auftragserstellung korrekt an. Übersetzungsanfragen senden keine ausgeschlossenen Inhalte mehr. (NPR-42761)



#### Benutzeroberfläche{#foundation-ui-6524}

* Eine Benutzeroberflächen-Regression wurde behoben, durch die Eingaben im Dialogfeld Adobe Stock-Lizenz deaktiviert wurden. Das Dialogfeld verhält sich jetzt normal, akzeptiert Text in Pflichtfeldern und vervollständigt den Fluss für die Stock-Asset-Lizenzierung in der Ansicht „Asset-Details“. (NPR-42748)

* Feste Gruppensichtbarkeit in der Autorenumgebung. Die Gruppenkonsole stoppt nicht mehr bei etwa 41 Ergebnissen und gibt den vollständigen Satz der Mitgliedschaften für jede Benutzerin und jeden Benutzer zurück. Diese Fehlerbehebung stellt das konsistente Verhalten nach kumulativen Fehlerbehebungen wieder her und sorgt für eine aktuelle Sicherheitsverhärtung. (NPR-42749)


<!--
#### WCM{#foundation-wcm-6524}



#### Workflow{#foundation-workflow-6524}
-->




## Installieren von [!DNL Experience Manager] 6.5.24.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.24.0 erfordert [!DNL Experience Manager] 6.5. Detaillierte Anweisungen finden Sie in der [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md). <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.24.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.24.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Installieren des Service Packs für [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von dem [Software-Verteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie den Paket-Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Paket-Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld in der Benutzeroberfläche vom Paket-Manager wird während der Installation des Service Packs manchmal beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.24.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API vom Paket-Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.24.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.24.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

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

UberJar für [!DNL Experience Manager] 6.5.24.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.24/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.24</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.



## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Unter [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md) finden Sie eine detaillierte Liste aller Funktionen, die für AEM 6.5 eingestellt oder entfernt wurden.

### Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API {#cf-support-assets-rest-api}

AEM 6.5 LTS SP2 bietet moderne OpenAPIs für die Verwaltung von Inhaltsfragmenten und -modellen, sodass die älteren Endpunkte zur Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API jetzt nicht mehr unterstützt werden.

Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Mitteilung über das Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Verbesserungen an den veralteten Endpunkten.

### SPA-Editor {#spa-editor}

[Der SPA-Editor](/help/sites-developing/spa-overview.md) wird für neue Projekte ab Version 6.5.24 von AEM 6.5 nicht mehr unterstützt. Der SPA-Editor wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind nun:

* der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung
* der [Inhaltsfragment-Editor](/help/sites-developing/universal-editor/introduction.md) zur formularbasierten Bearbeitung

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

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

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5.0 bis 6.5.4 auf das neueste Service Pack für Java™ 11 aktualisieren, sehen Sie `RRD4JReporter`-Ausnahmen in der Datei `error.log`. Um die Ausnahmen zu beenden, starten Sie Ihre [!DNL Experience Manager]-Instanz neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

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

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6524}

Die Vorschau von Inhaltsfragmenten schlägt aufgrund des DoS-Schutzes für eine umfassende Fragment-Baumstruktur fehl. Siehe den [KB-Artikel zu den standardmäßigen GraphQL Query Executor-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6524}

* **FORMS-14521** Wenn ein(e) Benutzende(r) versucht, eine Vorschau eines Briefentwurfs mit gespeicherten XML-Daten anzuzeigen, bleibt er/sie für einige bestimmte Briefe im `Loading`-Status stecken.
* **FORMS-16603** In der Druckvorschau der Benutzeroberfläche für interaktive Kommunikationsagenten werden einige berechnete Werte nicht korrekt angezeigt.
* **FORMS-15681** Wenn der Brief in der Druckvorschau angezeigt wird, wird der Inhalt geändert. Das heißt, dass einige Leerzeichen ausgeblendet werden und bestimmte Buchstaben durch `x` ersetzt werden.
* **FORMS-15428**: Nach der Aktualisierung auf AEM Forms Service Pack 20 (6.5.20.0) mit dem Forms-Add-on funktionieren Konfigurationen nicht mehr, die auf den alten Adobe Analytics Cloud-Dienst mithilfe der auf Anmeldedaten basierten Authentifizierung angewiesen sind. Dieses Problem verhinderte die ordnungsgemäße Ausführung von Analyseregeln.
* **FORMS-16557** In der Druckvorschau der Benutzeroberfläche für interaktive Kommunikationsagenten wird das Währungssymbol (z. B. das Dollarzeichen $) nicht konsistent für alle Feldwerte angezeigt. Er wird für Werte bis 999 angezeigt, fehlt jedoch für Werte ab 1000.
* **FORMS-16575** Alle Änderungen an der XDP verschachtelter Layout-Fragmente in einer interaktiven Kommunikation werden nicht im IC-Editor übernommen.
* **FORMS-21378** Wenn die Server-seitige Validierung (SSV) aktiviert ist, können die Formularübermittlungen fehlschlagen. Wenn dieses Problem auftritt, wenden Sie sich bitte an den Adobe-Support.
* **FORMS-23722** (Dateianhänge fehlen in „Aufgabe zuweisen„): Wenn ein Formular mit einem **Dateianhang**-Feld, das „bindRef“ verwendet, an einen AEM-Workflow gesendet wird, der einen **Aufgabe zuweisen**-Schritt verwendet, werden die Anhänge nicht angezeigt, wenn die Aufgabe aus dem Posteingang geöffnet wird. Die Dateien werden korrekt im Repository gespeichert, aber in der Benutzeroberfläche des Schritts „Aufgabe zuweisen“ können die Anlagen nicht angezeigt werden.

#### Probleme mit verfügbaren Hotfixes {#aem-forms-issues-with-hotfixes}

<!-- 
>[!NOTE]
>
>Avoid upgrading to Service Pack 6.5.24.0 for issues without an available hotfix. It may lead to unexpected errors. Upgrade to Service Pack 6.5.24.0 only after the required hotfixes are released. -->

Für die folgenden Probleme ist ein Hotfix zum Herunterladen und Installieren verfügbar. Sie können [den Hotfix herunterladen und installieren](/help/release-notes/aem-forms-hotfix.md), um diese Probleme zu beheben:

* AEM Forms enthält jetzt eine Aktualisierung der Struts-Version von 2.5.33 auf 6.x für die Formularkomponente. Dieses Upgrade liefert zuvor verpasste Struts-Änderungen, die nicht in SP24 enthalten waren. Die Unterstützung wurde über einen [Hotfix](/help/release-notes/aem-forms-hotfix.md) hinzugefügt. Diesen können Sie herunterladen und installieren, um Unterstützung für die neueste Version von Struts hinzuzufügen.

* **FORMS-14926** Führen Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) die folgenden Schritte aus, um das Problem zu beheben, wenn Sie doppelte Einträge von Geode-Jars `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` im `<AEM_Forms_Installation>/lib/caching/lib`-Ordner finden:

   1. Stoppen der Locators, falls sie noch ausgeführt werden.
   2. Stoppen des AEM-Servers.
   3. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
   4. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
   5. Öffnen der Eingabeaufforderung im Administratormodus.
   6. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

* **FORMS-15256** Beim Upgrade von AEM 6.5 Forms Service Pack 18 oder 19 auf Service Pack 20 oder 21 ist ein JSP-Kompilierungsfehler aufgetreten. Dieser Fehler hinderte sie daran, adaptive Formulare zu öffnen oder zu erstellen. Er hat auch Probleme mit anderen AEM-Schnittstellen verursacht. Zu diesen Schnittstellen gehörten der Seiteneditor, die AEM Forms-Benutzeroberfläche, der Workflow-Editor und die Benutzeroberfläche „Systemübersicht“.

  Wenn ein solches Problem auftritt, führen Sie die folgenden Schritte aus, um es zu beheben:
   1. Navigieren Sie in CRXDE zum Verzeichnis `/libs/fd/aemforms/install/`.
   2. Löschen Sie das Bundle `com.adobe.granite.ui.commons-5.10.26.jar`.
   3. Starten Sie den AEM-Server neu.

* **FORMS-23703** Wenn die `contains` ohne Standardwert konfiguriert ist, schlägt die Server-seitige Validierung für ein adaptives Formular fehl. Sie können die neueste Version von [AEM Forms 6.5.24.0 Service Pack](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#aem-65-forms-releases) installieren, um das Problem zu beheben.

* Die Authentifizierung von Formulardatenmodell-Connectoren kann fehlschlagen, da die erforderlichen Schlüsselwörter und Regex-Muster standardmäßig nicht zulässig sind. Um das Problem zu beheben, fügen Sie Folgendes über den Configuration Manager (`/system/console/configmgr`) hinzu:

   * **Schlüsselwörter:** `fdm-client-secret`, `oauth-client-secret`
   * **Regex:** `^\[/conf/[^/]+(/[^/]+)?/settings/dam/cfm/models/[^,\]]+(?:,/conf/[^/]+(/[^/]+)?/settings/dam/cfm/models/[^,\]]+)*\]$`

     >[!VIDEO](https://video.tv.adobe.com/v/3479697)

* Bei der **FORMS-23979**-Konvertierung von HTML in PDF (PDFG) können zeitweise Zeitüberschreitungen auftreten. Anschließend wurde eine neuere Version des Forms-Add-ons für SP24 veröffentlicht, die die Fehlerbehebung enthält. Wenn dieses Problem auftritt, aktualisieren Sie Ihre Umgebung auf das [neueste veröffentlichte Forms-Add-on für 6.5.24.0](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#aem-65-forms-releases).

* **FORMS-23717** Nach dem Upgrade auf **AEM Forms-6.5.24.0** können `server.log` und `error.log` mit wiederholten WARNMELDUNGEN wie *Erstellung der sicheren Parserfactory fehlgeschlagen* oder *Sicherheitsattribut … wird nicht unterstützt*. Protokolle können um ca. **5-10 Zeilen pro Sekunde (** von MB pro Stunde) zunehmen, wodurch Festplatten ausgefüllt und der Produktions-Rollout blockiert werden kann. **Fehlerbehebung:** in AEM Forms **6.5.25.0** enthalten. **Bis dahin:**

  Um das Protokollvolumen zu reduzieren, legen Sie die Protokollierungsebene für `com.adobe.util.XMLSecurityUtil` in Ihrer Anwendungsserverkonfiguration oder über die JVM-`ERROR` auf `-Dlogging.level.com.adobe.util.XMLSecurityUtil=ERROR` fest. Dadurch werden nur die Nachrichten ausgeblendet, die zugrunde liegende Ursache wird nicht behoben.

* **FORMS-23875** Bei der Formulardatenmodellsuche wird ein HTML-Tag in der Benutzeroberfläche angezeigt, auch wenn keine relevante Entität vorhanden ist. Um das Problem zu beheben, laden Sie den Hotfix von [dem Link“ herunter und &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bb-expressionmanager-pkg-10.0.48.zip) Sie ihn.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.24.0](/help/release-notes/assets/65240-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE --> enthaltenen OSGi-Bundles
* [Liste der in Experience Manager 6.5.24.0](/help/release-notes/assets/65240-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE --> enthaltenen Inhaltspakete

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kundinnen und Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
