---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Informationen zu neuen Funktionen, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: 15bdc427d138101a429aeb0c46059ad0492d7739
workflow-type: tm+mt
source-wordcount: '7111'
ht-degree: 24%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!--
DO NOT DELETE THIS HIDDEN NOTE!      DO NOT DELETE THIS HIDDEN NOTE!
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, May 29, 2025. In addition, a list of Forms fixes and enhancements is added to this section.
-->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.25.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;21. Mai 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.25.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

<!--
OLD DOWNLOAD URL
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip)
-->

## Was in [!DNL Experience Manager] 6.5.25.0 enthalten ist {#what-is-included-in-aem-6525}

[!DNL Experience Manager] 6.5.25.0 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- ## Key features and enhancements -->


## Behobene Probleme in Service Pack 25 {#fixed-issues}

<!-- 6.5.25.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->


### [!DNL Sites]{#sites-6525}

#### Barrierefreiheit {#sites-accessibility-6525}

* Drag-and-Drop-Steuerelemente für Tabellenzeilen in der Sites-Listenansicht funktionieren jetzt mit der Tastaturnavigation. Benutzende von Bildschirmlesehilfen und Tastaturen können Zeilen neu anordnen und während der Aktion Feedback erhalten. (SITES-24946)

* Die Symbolleiste Layout bearbeiten zeigt jetzt kleinere Bildschirm- und Tablet-Beschriftungen in einer aussagekräftigen Bildschirmlesehilfe an. Benutzer hören die Beschriftungen mit den zugehörigen Linealmessungen, anstatt sie ungeordnet zu hören. (SITES-25291)
* Das Farbfelder-Popover-Modal verwaltet jetzt den Fokus korrekt, wenn es über das Modal „Anmerkung“ geöffnet wird. Der Fokus beginnt mit der modalen Überschrift, anstatt direkt zur ausgewählten Farbfeld-Schaltfläche zu wechseln. (SITES-25275)
* Das Teaser-Modal bietet jetzt eine barrierefreie Möglichkeit, das Dialogfeld mit einer Tastatur zu verschieben. Benutzende benötigen keine Maus mehr, um das Modal auf der Seite neu zu positionieren. (SITES-25226)
* Kartenansicht verbessert die Barrierefreiheit, indem unnötiges ARIA-Rasterverhalten entfernt wird. Benutzende von Bildschirmlesehilfen erhalten klarere Karteninformationen ohne Steuerelemente für die Rasternavigation, die nicht mit dem visuellen Layout übereinstimmen. (SITES-24933)
* QuickInfos im Modal „Löschen“ werden jetzt nach wiederholten Mausbewegungen-Aktionen konsistent angezeigt. Benutzer können den Mauszeiger weg bewegen und zum Symbol zurückkehren, um die QuickInfo erneut zu lesen. (SITES-24778)
* Die linke Leiste erhält jetzt den Fokus in der erwarteten Reihenfolge, nachdem sie von Benutzenden über die Sites-Startseite geöffnet wurde. Benutzer von Tastatur- und Bildschirmlesehilfen können von der Konfigurationsschaltfläche zum Inhalt der Leiste wechseln, ohne den erweiterten Bereich zu überspringen. (SITES-24754)
* Die Fokusverwaltung funktioniert jetzt im modalen Dialogfeld „Karussell“ konsistent. Benutzer von Tastatur- und Bildschirmlesehilfen können mit der modalen Überschrift beginnen und zum ursprünglichen Steuerelement zurückkehren, nachdem das Dialogfeld geschlossen wurde. (SITES-24716)
* Das Dialogfeld Linkauswahl fokussiert nun auf das Steuerelement, das geöffnet wurde, nachdem Benutzer das Dialogfeld geschlossen haben. Benutzende von Tastatur- und Bildschirmlesehilfen verlieren nach dem Schließen des Dialogfelds nicht mehr ihre Position. (SITES-24707)
* Das Bild-Modal verschiebt den Fokus nicht mehr auf die erste Registerkarte oder das Wahrzeichen der Hauptseite, wenn Autoren das Dialogfeld öffnen oder schließen. Der Fokus wechselt zuerst zur Dialogfeldüberschrift und kehrt dann zu dem Steuerelement zurück, das das Dialogfeld geöffnet hat. (SITES-24693)
* Die Leiste „Verweise“ verwaltet den Fokus jetzt korrekt, wenn ein modales Dialogfeld geöffnet wird. Benutzende, die Tastatur und Bildschirmlesehilfen verwenden, bleiben im Dialogfeld, bis es geschlossen wird, und fahren dann mit der Navigation fort, ohne den Kontext zu verlieren. (SITES-24683)
* Das Modal zur Auswahl des Hyperlink-Pfads verschiebt den Fokus nicht mehr auf das falsche Feld oder Steuerelement, wenn Autoren es öffnen oder schließen. Der Fokus beginnt bei der modalen Überschrift und kehrt zur Schaltfläche zurück, die das modale Fenster geöffnet hat. (SITES-24672)
* Das Teaser-Modal verschiebt den Fokus nicht mehr auf die erste Registerkarte oder den Anfang der Seite, wenn Autoren sie öffnen oder schließen. Der Fokus folgt nun dem erwarteten Dialogfeldfluss und reduziert unnötige Ankündigungen der Bildschirmlesehilfe. (SITES-24522)

* Die Schaltfläche zum Sperren des Seiteneditors bietet jetzt eine präzisere Rückmeldung durch die Bildschirmlesehilfe. Bildschirmlesehilfen verwenden das Titelattribut, sofern verfügbar, wodurch ausführliche Ankündigungen für Autoren reduziert werden, die Hilfstechnologien verwenden. (SITES-41431)
* Die Tastaturnavigation überspringt jetzt ausgeblendete Inhalte. Benutzer können durch sichtbare Elemente der Benutzeroberfläche navigieren, ohne den Fokus auf Inhalte zu verschieben, die sie nicht sehen können. (SITES-41430)
* Der Tastaturfokus kehrt jetzt zum auslösenden Element zurück, nachdem Benutzende eine Überlagerung geschlossen haben. Der Seiteneditor sendet den Fokus nicht mehr zurück an die Überlagerung, wodurch die Navigation für Tastaturbenutzer verbessert wird. (SITES-40819)
* Die Symbolleiste des Seiteneditors zeigt jetzt Beschriftungen wie QuickInfos an, wenn Benutzer mit der Tastatur durch Symbolleistenelemente navigieren. Benutzer können jede Symbolleistenaktion verstehen, wenn der Fokus von einem Element zum anderen wechselt. (SITES-40751)
* Wenn Sie den Mauszeiger über Komponenten-Browser-Elemente bewegen, wird der Fokus nicht mehr von einer aktiven Textkomponente entfernt. Autoren können Text ohne Unterbrechung bearbeiten, und der Tastaturfokus bleibt vorhersehbar. (SITES-35370)
* Die Sprachausgabe gibt jetzt die Schaltfläche Modale Sortierrichtung suchen deutlicher wieder. Die Schaltflächenbeschriftung wiederholt nicht mehr dieselbe Richtung und beschreibt das Umschaltverhalten besser. (SITES-25534)
* Das Suchmodal zeigt jetzt einen visuellen Indikator für die ausgewählte Option im Listenfeld Datei oder Ordner ändern an. Benutzende können die aktuelle Breadcrumb-Option identifizieren, ohne sich allein auf den Fokus zu verlassen. (SITES-25532)
* Das Suchmodal erhöht jetzt den Kontrast für die Beschriftung Sortieren nach . Der Text erfüllt Barrierefreiheitsanforderungen und verbessert die Lesbarkeit für Benutzende mit Sehschwäche. (SITES-25531)
* Die Geräteauswahl-Schaltflächen zeigen nun in der Symbolleiste Layout bearbeiten die richtigen Informationen zum aktuellen Status an. Benutzende von Bildschirmlesehilfen können das aktive Gerät identifizieren, ohne den Umschaltstatus irreführend zu hören. (SITES-25524)
* Die Navigation über Tastatur und Bildschirmlesehilfe schließt jetzt das Menü Posteingang , wenn der Fokus ihn verlässt. Benutzende vermeiden den verwirrenden Status, in dem das Menü offen bleibt, während der Fokus an eine andere Stelle verschoben wird. (SITES-25518)
* Die Navigation über Tastatur und Bildschirmlesehilfe schließt jetzt das Hilfemenü, wenn der Fokus beendet wird. Der Fokus wechselt nicht mehr zu Inhalten außerhalb des Menüs, während das Menü offen bleibt. (SITES-25517)
* Die Startseite für Inhaltsfragmente bietet jetzt eine konsistente, barrierefreie Beschriftung für Seitenleisten-Registerkarten. NVDA gibt die Registerkartenbeschriftung korrekt aus, wenn Benutzer durch die Registerkartensteuerelemente navigieren. (SITES-25509)
* Fokussierte Optionen im Menü Seiteninformationen erfüllen jetzt die minimalen Kontrastanforderungen. Der verbesserte Kontrast hilft Benutzenden mit schlechtem Sehvermögen, das aktive Menüelement zu erkennen. (SITES-25321)
* Bei der Tastaturnavigation werden jetzt ausgeblendete Steuerelemente in der reduzierten Symbolleiste „Demografie“ übersprungen. Der Fokus bleibt auf sichtbaren interaktiven Elementen, wodurch die Navigationsreihenfolge in der Layout-Vorschau verbessert wird. (SITES-25304)
* Die Schaltfläche „Gerät drehen“ bietet jetzt in der Symbolleiste „Layout bearbeiten“ eine klarere Sprachausgabe. Die Sprachausgabe gibt die aktuelle Ausrichtung und die Aktion, die sie ändert, aus. (SITES-25292)
* Die Symbolleiste Layout bearbeiten zeigt jetzt für die Desktop-Schaltfläche einen leeren ausgewählten Status an. Die Desktop-Option entspricht den anderen Geräteschaltflächen und erleichtert die Identifizierung der aktiven Ansicht. (SITES-25290)
* Die Symbolleiste Layout bearbeiten kennzeichnet jetzt den Linealbereich für Hilfstechnologien. Benutzende von Bildschirmlesehilfen stoßen während der Layout-Bearbeitung nicht mehr auf unbeschriftete Messwerte. (SITES-25287)
* In der Symbolleiste Layout bearbeiten wird jetzt die vollständige iPhone 8 Plus-Schaltflächenbeschriftung deaktiviert angezeigt. Die Beschriftung wird nicht mehr abgeschnitten, wenn genügend Platz um die Schaltfläche vorhanden ist. (SITES-25284)
* Das gemeldete Problem beschrieb einen Fokusindikator in der Symbolleiste Layout bearbeiten , der mehrere Gerätesteuerelemente abzudecken schien. Die Sorge konzentrierte sich auf Tastaturbenutzer, die den Überblick über das aktive Steuerelement verlieren könnten, wenn die Fokuskontur angrenzende Schaltflächen enthielt. Das Problem funktionierte wie vorgesehen. (SITES-25283)
* Das gemeldete Problem beschrieb modale Schaltflächen von Anmerkungen, die vor jeder Schaltflächenbeschriftung eine Anmerkung ankündigten. Die Sorge konzentrierte sich auf die unklare Ausgabe von Bildschirmlesehilfen für Aktionen wie Anmerkungen, Farbfelder und Löschen. (SITES-25277)
* Der Text der Anmerkungsschaltfläche verwendet jetzt im Anmerkungsmodal einen ausreichenden Kontrast. Diese Aktualisierung verbessert die Lesbarkeit für Benutzende mit Sehschwäche und unterstützt WCAG-Kontrastanforderungen. (SITES-25267)
* Die Sprachausgabe erhält jetzt Statusaktualisierungen, wenn Benutzende die Liste Neue Komponente einfügen filtern. Das Modal gibt Ergebnisänderungen aus, sodass Benutzende verstehen, dass sich die Liste während der Eingabe geändert hat. (SITES-25251)
* Das protokollierte Problem beschreibt die fehlende Überschriftensemantik für den modalen Titel der Anmerkung. Die Bedenken konzentrierten sich auf die Navigation durch Bildschirmlesehilfen und die Fähigkeit, die modale Struktur zu verstehen. (SITES-25248)
* Die Überschriftenebenen in der Seitenleiste des Seiteneditors folgen jetzt einer klareren Inhaltshierarchie. Der Abschnitt „Linke Leiste“ wird nicht mehr als Überschrift der Hauptseite für Hilfstechnologien angezeigt. (SITES-25222)
* Die Schaltfläche Bearbeiten in der linken Leiste von Assets hat jetzt ein größeres Touch-Ziel. Benutzer mit Mobilitätsanforderungen können die Schaltfläche leichter aktivieren und nahe gelegene Steuerelemente vermeiden. (SITES-25221)
* Die linke Leiste von Assets identifiziert jetzt, wenn die Schaltfläche Bearbeiten eine neue Browser-Registerkarte öffnet. Benutzer können die Navigationsänderung vorhersehen, anstatt den Kontext unerwartet zu verlieren. (SITES-25220)
* Komponententitel werden jetzt korrekt angezeigt, wenn Benutzer größeren Textabstand anwenden. Die Seitenleiste behält lesbare Beschriftungen bei und unterstützt WCAG-Textabstandsanforderungen. (SITES-25219)
* Das Filterfeld in den Komponenten der Seitenleiste zeigt jetzt einen richtigen barrierefreien Namen an. Diese Aktualisierung hilft Benutzenden von Bildschirmlesehilfen, das Feld ohne Verwendung von Platzhaltertext zu identifizieren. (SITES-25212)
* Das gemeldete Problem beschrieb eine unlogische Fokussequenz im Anmerkungsmodus. Tastaturbenutzer haben Berichten zufolge die Anmerkungssymbolleiste verpasst, es sei denn, sie haben nach der Aktivierung des Modus Umschalt+Tab verwendet. (SITES-24996)
* Die Arbeitsfläche des Editors stellt den Titel der oberen Leiste als Überschrift bereit. Die Sprachausgabe kann den Titel mit der richtigen Struktur ausgeben, was die Navigation und das Seitenverständnis verbessert. (SITES-24993)
* Der Barrierefreiheitsbericht stellte einen unzureichenden Kontrast für die Ladestatusmeldung fest, die angezeigt wird, wenn Benutzer die Ansichten wechseln. Die Sorge konzentrierte sich auf die Lesbarkeit für Benutzende mit Sehschwäche oder Farbenblindheit. (SITES-24991)
* Im Bericht zur Barrierefreiheit wurde festgestellt, dass Kartenverknüpfungen nicht-beschreibenden Text enthalten. Der Schwerpunkt lag darauf, Benutzenden von Bildschirmlesehilfen zu helfen, jedes Link-Ziel ohne zusätzlichen Kontext zu verstehen. (SITES-24975)
* Die Sites-Listenansicht zeigt jetzt Live Copy-Text mit stärkerem Kontrast an. Die Aktualisierung verbessert die Lesbarkeit für Autoren mit schlechtem Sehvermögen und für Benutzer, die unter hellen Bildschirmbedingungen arbeiten. (SITES-24956)
* Die Tastaturnavigation verschiebt jetzt den Fokus in das Emulator-Menü, nachdem sie von Benutzenden erweitert wurde. Dieses Verhalten hilft Benutzenden von Bildschirmlesehilfen und Tastaturen, in der erwarteten Reihenfolge auf die Menüoptionen zuzugreifen. (SITES-24954)
* Die Sites-Listenansicht verbessert jetzt die Sichtbarkeit von Drag-and-Drop-Schaltflächen in Tabellenzeilen. Autoren können das Steuerelement leichter identifizieren, wenn sie Inhalte neu anordnen. (SITES-24951)
* Eine Karte stellt nicht mehr sowohl den Bild- als auch den Überschriften-Link als separate Links bereit, wenn sie dasselbe Ziel teilen. Die Aktualisierung reduziert die Ausführlichkeit der Sprachausgabe und verbessert die Navigationseffizienz. (SITES-24947)
* Schaltflächen im Kopfzeilenmenü verwenden jetzt genauere Barrierefreiheitsattribute. Die Sprachausgabe gibt die Schaltflächen als erweiterbare Steuerelemente aus, anstatt Dialogfelder zu öffnen. (SITES-24742)
* Der Posteingang markiert jetzt verwandte Links mit semantischem Listen-Markup. Benutzende von Bildschirmlesehilfen können die Anzahl und Gruppierung von Inbox-Links leichter verstehen. (SITES-24730)
* Beschriftungen für Kopfzeilen-Schaltflächen vermeiden jetzt ausführliche barrierefreie Namen. Benutzende von Bildschirmlesehilfen erhalten klarere Ankündigungen ohne doppelte Rolleninformationen aus dem Symboltext. (SITES-24715)
* Die Schaltfläche CSV-Bericht liefert nun ein klareres Feedback zum Verhalten bei neuen Registerkarten. Benutzer*innen können verstehen, dass durch Klicken auf die Schaltfläche eine neue Browser-Registerkarte geöffnet wird, bevor sie sie aktivieren. (SITES-24704)
* Modale Dialogfelder verwenden jetzt genaueres Barrierefreiheits-Markup für Header-Steuerelemente. Die Schaltflächen Hilfe und Umschalten im Vollbildmodus bleiben interaktive Steuerelemente und werden für Bildschirmlesehilfen nicht mehr als Überschriften angezeigt. (SITES-24696)
* Das Wahrzeichen der Filterleiste verwendet jetzt eine eindeutige Beschriftung, die ihren Zweck kennzeichnet. Benutzende von Bildschirmlesehilfen können sicherer durch Seiten mit mehreren ähnlichen Orientierungspunkten navigieren. (SITES-24686)
* Verweise : Meldungen in der Leiste bieten jetzt eine bessere Lesbarkeit für Benutzende, die auf einen ausreichenden Textkontrast angewiesen sind. Das gemeldete Problem betraf Auswahl- und Mehrfachauswahl-Nachrichten, die vor ihrem Hintergrund zu hell erschienen. (SITES-24666)
* Das Suchmodal bietet jetzt größere Touch-Ziele für die Schaltflächen „Standort entfernen“ und „Schließen“. Diese Änderung hilft Benutzenden mit Handzittern, Spasmen oder Sehschwäche, die beabsichtigte Kontrolle zu aktivieren. (SITES-24530)
* Der Adobe Experience Manager-Kopfzeilen-Link verwendete ein falsches ARIA-Attribut. Beim Testen wurde bestätigt, dass der Link erweiterbare Inhalte steuert, sodass der vorhandene barrierefreie Status angemessen bleibt. (SITES-24528)
* Die Fokusanzeige für die Autorenzeilenschaltfläche wird in der Komponentenliste nicht mehr abgeschnitten angezeigt. Der sichtbare Umriss hilft Tastaturbenutzern, ihre Position im Editor zu verfolgen. (SITES-24503)
* Ein gemeldetes Problem beschrieb eine fehlende Textalternative für das Informations-QuickInfo-Symbol im Bedienfeld „Komponenten“. Das Problem wurde nicht reproduziert, aber die Überprüfung bestätigte, dass informative Symbole einen klaren barrierefreien Namen offenlegen müssen. (SITES-24500)
* Der Seiteneditor stellt nicht mehr mehrere Regions-Orientierungspunkte mit derselben Beschriftung bereit. Jedes Wahrzeichen hat jetzt einen eindeutigen barrierefreien Namen, sodass Benutzende der Bildschirmlesehilfe die aktuelle Region identifizieren können. (SITES-24497)
* Das Steuerelement „Datei ändern“ oder „Ordner ändern“ trennt jetzt die Steuerelementbeschriftung von den Statusinformationen. Benutzende von Bildschirmlesehilfen hören einen kürzeren, klareren Namen, wenn sie durch das Header-Steuerelement navigieren. (SITES-24496)
* Interaktive Steuerelemente in der Admin-Tabelle für Inhaltsfragmente unterstützen jetzt die standardmäßige Tastaturnavigation. Tastaturbenutzer können mit der Tabulatortaste zu Schaltflächen und Links wechseln, anstatt sie nur über die Pfeiltasten-Navigation zu erkennen. (SITES-24285)
* Die Admin-Benutzeroberfläche von Sites behandelt dekorative Globussymbole jetzt für Bildschirmlesehilfen korrekt. Die Symbole verwenden leeren Alternativtext, sodass Benutzende nur aussagekräftige Inhalte der Benutzeroberfläche hören. (SITES-3057)

#### Admin-Benutzeroberfläche{#sites-adminui-6525}

Die Sites-Konsole zeigt jetzt die gespeicherten **Listenansicht** Spalteneinstellungen korrekt an. Ausgewählte Spalten bleiben aktiviert, wenn Autoren das Dialogfeld Einstellungen erneut öffnen, und die Anzahl der aktiven Spalten bleibt korrekt. (SITES-38576)

#### Klassische Benutzeroberfläche{#sites-classicui-6525}

Die Dialogfelder der Textkomponente der klassischen Benutzeroberfläche zeigen jetzt Rich-Text-Editor (RTE)-Inhalte als formatierten Text anstelle von unbearbeitetem HTML an. Autorinnen und Autoren können vorhandenen Text bearbeiten, ohne in den Source-Modus zu wechseln oder Markup manuell zu entfernen. (SITES-38709)

#### Komponentenkonsole{#sites-component-console-6525}

* Benutzer können jetzt die Komponentenkonsole mit lokalisierten Zeichen oder Multibyte-Zeichen durchsuchen. Die Konsole zeigt auch eine lokalisierte **Entfernen**-Beschriftung anstelle der nicht übersetzten englischen Zeichenfolge an. (SITES-39747)
* Die Seite Komponenteneigenschaften lokalisiert jetzt Zeichenfolgen in „Tools“ > „Komponenten“ > „Komponenteneigenschaften“. Benutzer sehen in lokalisierten Authoring-Oberflächen keine unübersetzten englischen Bezeichnungen mehr. (SITES-39745)

#### [!DNL Content Fragments]{#sites-contentfragments-6525}

Die Assets-Suche reagiert jetzt korrekt, wenn Benutzende Filter auswählen oder ändern. Der gefilterte Ergebnissatz wird erwartungsgemäß aktualisiert, wodurch die zuverlässige Suchverfeinerung in der Assets-Konsole wiederhergestellt wird. (SITES-38686)

#### [!DNL Content Fragments] – Admin{#sites-admin-6525}

* Die Assets-Listenansicht zeigt jetzt für gesperrte Inhaltsfragmente eine lokalisierte QuickInfo Ausgecheckt von . Diese Fehlerbehebung verbessert die Lokalisierungskonsistenz, wenn Autoren Workflow-Zeilen überprüfen. (SITES-42531)

* AEM lokalisiert jetzt die Hauptbeschriftung im Dialogfeld zum Herunterladen von Inhaltsfragmenten. Durch die Korrektur wird der Download-Workflow über nicht englische Gebietsschemata hinweg konsistent gehalten. (SITES-42534)
* AEM übersetzt jetzt die `Later`-Statusbeschriftung, wenn Autorinnen und Autoren die Veröffentlichung von Inhaltsfragmenten in Assets planen. Diese Fehlerbehebung sorgt dafür, dass die Spalte Veröffentlicht über lokalisierte Schnittstellen hinweg konsistent bleibt. (SITES-42532)
* Bei der Erstellung von Inhaltsfragmenten wird jetzt eine lokalisierte Validierungsmeldung angezeigt, wenn Autoren ungültige Zeichen in das Feld Titel eingeben. Im Dialogfeld wird die nicht lokalisierte Zeichenfolge „Ungültiger Name angegeben“ nicht mehr angezeigt. (SITES-19796)
* Die Seite „Inhaltsfragment bearbeiten“ verwendet jetzt lokalisierte Bezeichnungen für Tags und Sammlungen. Autoren sehen übersetzte Feldnamen anstelle von nicht lokalisierten englischen Zeichenfolgen. (SITES-977)

#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-6525}

* Zugehörige Inhalte im Inhaltsfragment-Editor zeigen jetzt die richtige lokalisierte Zeichenfolge an, wenn Autoren Inhalte aus einer Sammlung entfernen. Das Dialogfeld ersetzt nicht mehr den Inhaltsnamen durch „undefiniert“. (SITES-33675)
* Der Inhaltsfragment-Editor zeigt jetzt eine übersetzte allgemeine Beschriftung für Registerkarten ohne konfigurierten Platzhalter an. Lokalisierte Schnittstellen zeigen die nicht übersetzte englische Zeichenfolge in diesem Editor-Bereich nicht mehr an. (SITES-30715)
* Die Auswahl der Inhaltsreferenz im Inhaltsfragment-Editor zeigt jetzt lokalisierte Beschriftungen für zulässige Asset-Typen an. Lokalisierte Schnittstellen zeigen keine englischen Typnamen für unterstützte Asset-Kategorien mehr an. (SITES-29699)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6525}

* GraphQL-JSON-Antworten enthalten jetzt eingebettete Bildverweise aus Rich-Text-Feldern von Inhaltsfragmenten, wenn DAM-Dateinamen Leerzeichen oder Nicht-ASCII-Zeichen enthalten. Diese Fehlerbehebung hilft Programmen, referenzierte Bilder zu rendern, ohne dass Autoren Assets umbenennen müssen. (SITES-42191)
* GraphQL-Antworten für Inhaltsfragmente verarbeiten jetzt persistierte Abfragen zuverlässiger. Die Aktualisierungen korrigieren doppelte Cache-Kopfzeilen, verbessern die Verarbeitung kodierter Variablen und geben klarere Antworten für fehlende Inhalte oder fehlgeschlagene Abfragen zurück. (SITES-40159)
* Persistierte Abfragen von GraphQL werden jetzt ohne unnötige FEHLER- und WARNMELDUNGEN in den Protokollen ausgeführt. AEM verarbeitet kodierte Variablen korrekt, sodass erfolgreiche Abfragen keine irreführenden `PersistedQueryServlet` mehr erzeugen. (SITES-39354)

* Das Dialogfeld GraphQL-Endpunkt bearbeiten lokalisiert jetzt seine Schnittstellenzeichenfolgen. Benutzer sehen nicht mehr, dass das nicht übersetzte GraphQL-Schema aus der Konfigurationsmeldung in lokalisierten Benutzeroberflächen übernommen wird. (SITES-34018)

#### [!DNL Content Fragments] – GraphQL-Abfrage-Editor{#sites-graphql-query-editor-6525}

Benutzende können jetzt den Abfrage-Editor von GraphQL öffnen, wenn der ausgewählte Konfigurationsbrowser-Name CJK- oder Kyrillische Zeichen enthält. Der Editor zeigt persistierte Abfragen für den Endpunkt an, anstatt einen Fehler anzuzeigen. (SITES-31616)

#### [!DNL Content Fragments] - Modelle und Modell-Editor{#sites-models-model-editor-6525}

* Benutzern wird jetzt eine lokalisierte Validierungsmeldung im Inhaltsfragmentmodell-Editor angezeigt, wenn ein ausgewählter Wert einen gültigen Modelltyp benötigt. Der Editor zeigt die nicht übersetzte englische Meldung nicht mehr in lokalisierten Benutzeroberflächen an. (SITES-41117)
* Der Filterbereich des Inhaltsfragmentmodells lokalisiert jetzt seine Status- und Titelzeichenfolgen. Benutzende sehen keine unübersetzten Beschriftungen wie Modelltitel, Status, Entwurf, Aktiviert und Deaktiviert mehr. (SITES-30863)

<!-- #### [!DNL Content Fragments] - REST API{#sites-restapi-6525} -->

#### ContextHub{#sites-contexthub-6525}

ContextHub wird jetzt ohne JavaScript-Fehler geladen, der die Personalisierung unterbrochen hat. Teaser und andere personalisierte Erlebnisse können auf betroffenen Seiten korrekt gerendert werden. (SITES-38430)

<!-- #### Core Backend{#sites-core-backend-6525} -->

#### Kernkomponenten{#sites-core-components-6525}

* AEM generiert keine wiederholten ThumbnailServlet-Fehler mehr, wenn eine Anfrage auf eine fehlende DAM-Ressource abzielt. Das Servlet stoppt die Verarbeitung nach der Umleitung, wodurch verhindert wird, dass das Fehlerprotokoll von NullPointerException-Einträgen überflutet wird. (SITES-41238)
* AEM kennzeichnet optionale Dialogfelder nicht mehr als erforderlich, wenn Autoren Komponentendialogfelder erneut öffnen. Das Dialogfeld behält die Validierung auf Felder, die tatsächlich eine Eingabe erfordern, wodurch irreführende Fehler auf Registerkartenebene verhindert werden. (SITES-40449)

* AEM umfasst mehrere Backport-Sicherheitskorrekturen, die Sites und zugehörige Cloud Services-Komponenten stärken. Diese Korrekturen reduzieren das Risiko von Cross-Site-Scripting und verbessern die Anfragebearbeitung über die betroffenen Authoring-Pfade hinweg. (SITES-38314)
* Das Dialogfeld für die Konfiguration der Bild-v3-Komponente lokalisiert jetzt Zeichenfolgen im Seiteneditor. Autoren sehen keine unübersetzten Beschriftungen mehr, wenn sie Bildkomponenten in lokalisierten Benutzeroberflächen konfigurieren. (SITES-38726)

<!-- #### Campaign integration{#sites-campaign-integration-6525} -->

<!-- #### ContentHub {#sites-contenthub-6525} -->

#### Fußgängerüberweg {#sites-crosswalk-6525}

* Crosswalk benötigt nach der Installation kein separates Paket und keine Konfiguration mehr. AEM umfasst die erforderlichen Bundles, Inhaltspakete, Systembenutzer, Service-Benutzerzuordnungen und Funktions-Umschalter im vordefinierten Paket. (SITES-41417)
* Crosswalk-Workflows funktionieren jetzt mit der erforderlichen cq-wcm-core-Unterstützung in AEM 6.5. Autoren können die Aktionen Vorlage erstellen und Universellen Editor öffnen ohne separate Aktualisierungen des Kernpakets verwenden. (SITES-37666)

#### Experience Fragments{#sites-experiencefragments-6525}

AEM lädt jetzt die richtigen Vorlagen, wenn Autorinnen und Autoren Varianten von Experience Fragments erstellen und über die ersten 40 Ergebnisse hinausscrollen. Die Vorlagenauswahl behält den ausgewählten Experience Fragment-Pfad während der Paginierung bei. (SITES-41531)

<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6525} -->

#### Launches{#sites-launches-6525}

* Die Sites-Zeitleiste lokalisiert jetzt die Nachricht, die angezeigt wird, wenn AEM eine Version erstellt, bevor ein Launch hochgestuft wird. Benutzer sehen die nicht übersetzte englische Zeichenfolge in lokalisierten Benutzeroberflächen nicht mehr. (SITES-39157)
* Die Launch-Liste zeigt jetzt die richtige Beschreibung für Launches an, die ohne Vorlagen- oder Live Copy-Vererbung erstellt wurden. Benutzern wird die irreführende, überschriebene Vorlagenbeschriftung nicht mehr angezeigt. (SITES-34229)

<!-- #### Link Checker{#sites-link-checker-6525} -->

#### Lokalisierung{#sites-localization-6525}

* Die Eigenschaften der Textkomponente in Experience Fragments verwenden jetzt lokalisierte Bezeichnungen. Im Menü Format werden nicht mehr lokalisierte Zeichenfolgen für Absatz-, Überschriften-, Anführungszeichen- oder vorformatierte Textauswahlen angezeigt. (SITES-15091)

* Der Text des Vorlagenstatus wird jetzt korrekt unter **Tools** > **Allgemein** > **Vorlagen** ausgerichtet. Die Statuskennzeichnungen „Aktualisiert“, „Aktiviert“ und „Veröffentlicht“ werden in einer horizontalen Linie angezeigt. (SITES-36797)
* Das Dialogfeld Seite verschieben zeigt jetzt die vollständige Beschriftung Datum und Uhrzeit auswählen an. Die Bezeichnung wird in lokalisierten Benutzeroberflächen wie dem Französischen nicht mehr abgeschnitten. (SITES-36795)
* Der Abschnitt Assets im Vorlageneditor zeigt jetzt die Bezeichnung Übersetzte Tags an. Lokalisierte Authoring-Oberflächen bieten bei der Vorlagenkonfiguration konsistente Bezeichnungen. (SITES-33770)
* Beschreibungen der Seitenrichtlinien werden jetzt im Vorlageneditor korrekt gerendert. Benutzende können die vollständige Anleitung zu Standard-CSS-Klassen ohne abgeschnittenen Text auf der Registerkarte Stile lesen. (SITES-29724)
* Der Vorlageneditor zeigt jetzt einen lokalisierten Fehler an, wenn ein Autor versucht, eine Komponente auf eine gelöschte Vorlage zu ziehen. Die Nachricht wird während der Verarbeitung nicht mehr als unübersetzte Zeichenfolge angezeigt. (SITES-19313)
* Die Bezeichnung „Target“ im Fenster Teaser-Konfiguration wird jetzt mit lokalisiertem Text angezeigt. Der Abschnitt Hyperlink zeigt die englische Zeichenfolge in nicht englischen Gebietsschemata nicht mehr an. (SITES-18622)
* Das Dialogfeld Workflow starten im Seiteneditor zeigt jetzt lokalisierte Workflow-Aktionsbezeichnungen an. Autoren sehen keine englischen Zeichenfolgen mehr für Workflow-Optionen wie Genehmigung, Veröffentlichung, Anfrage und Aktionen zum Rückgängigmachen der Veröffentlichung. (SITES-18103)
* Das Dropdownmenü Übergeordnetes Element im Bedienfeld Trennzeichen zeigt jetzt lokalisierte Zeichenfolgen ohne Abschneiden an. Autoren können die vollständige Bezeichnung bei der Konfiguration der Komponente überprüfen. (SITES-17480)
* Im Seiteneditor werden jetzt lokalisierte Beschriftungen für „Vollständige Breite“ und „Feste Breite“ im Menü Container-Komponentenstile angezeigt. Autoren, die unterstützte Gebietsschemata verwenden, sehen diese Zeichenfolgen nicht mehr auf Englisch. (SITES-17478)
* Autoren können jetzt die vollständige QuickInfo im Bereich Navigationseigenschaften der Vorlagenkonsole lesen. Die Benutzeroberfläche hält die QuickInfo ausgerichtet und verhindert das Abschneiden von Text während der Vorlagenbearbeitung. (SITES-15480)
* Autoren können jetzt die vollständige Beschriftung &quot;Forms und Dokumente mit Vorlage“ im Seitenbereich „Verweise“ lesen. Die Vorlagenkonsole schneidet die Zeichenfolge für unterstützte Gebietsschemata nicht mehr ab. (SITES-13167)
* Die Ansicht Verweise verwendet jetzt lokalisierten Text für die Aktualisierungsfehlermeldung. Autoren sehen übersetzte Nachrichten, wenn AEM die Verweisliste nicht aktualisieren kann. (SITES-13102)
* Die Formularvalidierung identifiziert jetzt das Feld, das einen ungültigen Zeitwert enthält. Das Zeitsprung -Modal zeigt eine klarere Fehlermeldung an, damit Autoren das betroffene Stunden- oder Minutenfeld korrigieren können. (SITES-10980)
* Die Vorlagenkonsole zeigt jetzt im Dialogfeld Bild auswählen eine lokalisierte Assets-Beschriftung an. Die Beschriftung wird korrekt angezeigt, wenn Autoren Assets aus den Vorlageneigenschaften durchsuchen. (SITES-8113)

#### MSM – Live Copies{#sites-msm-live-copies-6525}

* Mit der Live Copy-Übersicht werden Datumsformate jetzt in der Ansicht Beziehungsstatus lokalisiert. Die Felder **Letzte Änderung“,**&#x200B;**Letzte Änderung der Live Copy** und **Letztes Rollout** zeigen Datumsangaben, die mit dem Gebietsschema des Benutzers übereinstimmen. (SITES-40756)
* MSM protokolliert jetzt weitere Details für Push-on-Modify-Ereignisse. Mit den hinzugefügten Ereignisinformationen können Teams Rollout-Aktivitäten verfolgen und die Quelle unerwarteter Seitenänderungen identifizieren. (SITES-38029)

#### Seiteneditor{#sites-pageeditor-6525}

* Autoren können jetzt Tags erstellen, die Großbuchstaben oder Leerzeichen enthalten, und diese beim Speichern der ersten Seiteneigenschaften anwenden. AEM erstellt das Tag und schreibt im selben Vorgang den richtigen Wert in die Seitenmetadaten. (SITES-42550)

* Autoren können jetzt Inhaltsfragmente in DAM-Ordnern erstellen, deren Namen ein Apostroph enthalten. AEM verarbeitet den codierten Ordnerpfad korrekt und gibt während der Erstellung keinen NullPointerException-Trigger mehr aus. (SITES-38653)

* AEM unterstützt jetzt Kopieren und Einfügen für konfigurierte Inhaltsfragmentkomponenten im Seiteneditor. Die Komponente behält ihren Inhaltsfragmentverweis bei, sodass Autorinnen und Autoren Inhalte duplizieren können, ohne sie manuell neu erstellen zu müssen. (SITES-41586)
* Im Seiteneditor werden jetzt QuickInfos für Erstfeldbeschreibungen in Komponentendialogfeldern korrekt angezeigt. Lange Beschreibungen bleiben sichtbar, sodass Autoren Feldanweisungen überprüfen können, ohne Text oben in der QuickInfo zu verlieren. (SITES-39937)
* Autorinnen und Autoren können jetzt das Dialogfeld Rich-Text-Editor-Link öffnen, wenn sie AEM über HTTP verwenden. Die Fehlerbehebung stellt die Link-Bearbeitung für On-Premise-Umgebungen wieder her, die keine HTTPS verwenden. (SITES-39467)

<!-- #### Replication{#sites-replication-6525} -->

<!-- #### Rich Text Editor{#sites-rte-6525} -->

#### Universeller Editor {#sites-universal-editor-6525}

* Der universelle Editor wird nicht mehr standardmäßig im Vorschaumodus geöffnet. AEM sendet Benutzende an die universelle Produktionsumgebung des Editors, es sei denn, sie fordern explizit das Vorschauverhalten an. (SITES-37193)
* Der universelle Editor wird jetzt im Vorschaumodus für AEM-Entwicklungs-, schnelle Entwicklungs- und Staging-Umgebungen geöffnet. Der Befehl Öffnen verwendet das richtige Vorschauverhalten für Nicht-Produktionsinstanzen. (SITES-33839)

### [!DNL Assets] {#assets-6525}

* Die Client-Bibliothek „Meine Freigaben“ verarbeitet jetzt geteilte Asset-Titeldaten sicher, bevor sie zum Seiten-Markup hinzugefügt werden. Generierte Freigabeseiten setzen Benutzer nicht mehr der Skripteinfügung durch bearbeitete Asset-Metadaten aus. (ASSETS-60898)

* Die Adobe Stock-Lizenzierung funktioniert jetzt in der Benutzeroberfläche von Assets ordnungsgemäß. Die Lizenzschaltfläche bleibt nicht mehr deaktiviert, nachdem AEM das Stock-Asset-Profil und die Berechtigungsdaten geladen hat. (ASSETS-62610)
* Die vordefinierte Ablaufbenachrichtigung von Assets verarbeitet jetzt Fast-Ablaufdaten korrekt. Erinnerungs-E-Mails werden ausgeführt, wenn die verbleibende Zeit den konfigurierten Schwellenwert erreicht, anstatt Assets mit einem Ablauf von acht Tagen zu überspringen. (ASSETS-57857)

* AEM Assets stellt jetzt die Tastaturnavigation wieder her, nachdem Benutzende eine gespeicherte Suche ausgewählt haben. Auf der Benutzeroberfläche können Benutzer das Dropdown-Menü verlassen, ohne die Assets-Ansicht zu aktualisieren oder neu zu starten. (ASSETS-52061)

* Der Download-Workflow der Admin-Ansicht behält jetzt die ZIP-Dateinamen korrekt bei. Beim Herunterladen eines ZIP-Assets wird kein Dateiname mit der doppelten ZIP-Erweiterung mehr erstellt. (ASSETS-62207)
* Der Assets-Referenz-Workflow verarbeitet jetzt Leerzeichen in Dateinamen korrekt. Zugehörige Asset-Aktualisierungen schlagen nicht mehr fehl, wenn ein ausgewählter Dateiname ein oder mehrere Leerzeichen enthält. (ASSETS-56418)

#### [!DNL Dynamic Media]{#assets-dm-6525}

Das Dropdown-Menü Untertitel und Audiospuren zeigt jetzt Arabisch als unterstützte Sprache in Dynamic Media an. Mit diesem Update können Benutzer arabische Untertitelspuren ohne benutzerdefinierte Problemumgehungen hinzufügen. (ASSETS-61771)

### [!DNL Forms]{#forms-6525}

>[!NOTE]
>
>Fehlerbehebungen in [!DNL Experience Manager] Forms werden über ein separates Add-on-Paket eine Woche nach dem geplanten Veröffentlichungsdatum des [!DNL Experience Manager] Service Packs bereitgestellt. In diesem Fall ist geplant, das -Add-on-Paket am Donnerstag, dem 28. Mai 2026, zu veröffentlichen. Darüber hinaus wird diesem Abschnitt eine Liste mit Forms-Korrekturen und -Verbesserungen hinzugefügt.



<!-- ALL THE FORMS BUG FIXES LISTED BELOW GO WITH AEM 6.5.25 FORMS MAY 28 2026 RELEASE!! UNHIDE THEM!! -->




<!-- #### Forms Designer {#forms-designer-6525} -->

<!-- 
* The Output API now handles dynamic form content consistently when PDF generation uses client rendering. Generated PDFs retain scripted description text across affected sections instead of leaving some fields blank. (LC-3928858)
* Document of Record generation now handles repeated panel pagination correctly when parent and child panels use the same "Place Top of Next Page" configuration. Authors no longer lose child panel data during the first repeated panel instance in generated output documents. (LC-3923274)
* Long multiline text fields in PDF preview now flow correctly across pages. The generated PDF no longer duplicates page content or drops hidden text during printing. (LC-3924324)
* Fillable PDFs now reset accessibility data when users clear form fields. Screen readers announce the cleared state correctly instead of reading old field values that no longer appear in the form. (LC-3923872)
* The Accessibility Checker now handles Nepali text correctly during PDF validation. Users can check Nepali-language documents without false accessibility errors tied to character encoding. (LC-3922988) 
-->

<!-- #### XMLFM {#forms-xmlfm-6525} -->

<!-- 
* Generated PDFs now include proper tags for supported form fields that use borders in the template. Screen readers can identify numeric fields, date fields, text fields, and checkboxes more reliably. (LC-3923534)
* Document of Record output now applies the correct tag structure to supported fields that include borders in the template. Numeric, date, text, and checkbox fields remain accessible in the generated PDF. (LC-3923265)
-->

<!-- #### XTG {#forms-xtg-6525} -->

<!-- 
* Forms output now merges XML data correctly when generatePDFOutputBatch generates PDFs in batch mode. The batch process no longer creates documents with blank or missing merged fields. (LC-3924192) 
* Document of Record output now includes nested child panels in the first occurrence of a repeatable panel. Forms that use Top of Next Page pagination no longer drop child panel data from the generated output. (LC-3923923)
* Custom bullet characters in XDP templates now map correctly for accessible PDF output. PAC validation no longer reports that text object characters cannot map to Unicode. (LC-3923079) 
-->


### Foundation {#foundation-6525}

#### Apache Felix {#foundation-apachefelix-6525}

Der CredentialsSupport-Service wird jetzt beim Start korrekt für die Felix-basierte Authentifizierung verkabelt. Dadurch werden Abhängigkeitsfehler verhindert, die sich beim Start von AEM auf die Token-Authentifizierung auswirken können. (GRANITE-63186)

<!-- #### Campaign{#foundation-campaign-6525} -->

<!-- #### Cloud Services{#foundation-cloudservices-6525} -->

<!-- #### Communities {#foundation-communities-6525} -->

<!-- #### Content distribution{#foundation-content-distribution-6525} -->

#### CRX {#foundation-crx-6525}

Die JSP-Dateibearbeitung funktioniert nach AEM 6.5-Upgrades jetzt wie erwartet in CRXDE Lite. Der CodeMirror-Editor lädt den Dateiinhalt, anstatt die Registerkarte „JSP“ leer zu lassen. (GRANITE-64333)

<!-- #### Granite{#foundation-granite-6525} -->

<!-- #### Integrations{#foundation-integrations-6525} -->

<!-- #### Jetty{#foundation-jetty-6525} -->

#### Lokalisierung{#foundation-localization-6525}

* Das Dialogfeld zum Hochladen von Zertifikaten unter Sicherheit > Trust Store zeigt jetzt lokalisierte Beschriftungen für Datenformate an. Benutzende sehen beim Hinzufügen eines Zertifikats keine nicht lokalisierten englischen Bezeichnungen mehr. (NPR-43412)

* Das Dialogfeld KeyStore erstellen richtet nun die Schaltfläche Abbrechen an den anderen Dialogfeldschaltflächen aus. Das Schaltflächen-Layout bleibt konsistent und verlagert sich nicht mehr aus der Ausrichtung heraus. (NPR-43291)
* Das Dialogfeld Überprüfen unter **Sicherheit** > **-IMS-Konfigurationen** jetzt lokalisierten Bestätigungstext an. Die Nachrichten zum Überprüfen und Löschen werden nicht mehr als nicht lokalisierte englische Zeichenfolgen angezeigt. (NPR-43289)
* Lokalisierte UI-Kennzeichnungen werden jetzt korrekt in betroffenen Dialogfeldern und auf der Registerkarte „Keystore“ angezeigt. Aria-Kennzeichnungswerte verwenden übersetzte Zeichenfolgen, und Kennzeichnungen für Kennwortfelder werden ohne Abschneiden angezeigt. (NPR-43285)
* Der Workflow Neuen Benutzer erstellen zeigt jetzt lokalisierte Validierungsfehler für ungültige Zeichen an. Benutzer erhalten eine klare, übersetzte Nachricht anstelle einer nicht lokalisierten IllegalArgumentException-Zeichenfolge. (GRANITE-52920)

<!-- #### Oak {#foundation-oak-6525} -->

#### Platform{#foundation-platform-6525}

* Die Schaltfläche Tag-Verweise anzeigen zeigt jetzt die Anzahl der Verweise für das ausgewählte Tag an. Dieses Update hilft Benutzenden, die Tag-Nutzung ohne zusätzliche Navigation zu verstehen. (CQ-4355509)
* Das Dialogfeld Verschieben in Tagging positioniert nun die Validierungsmeldungen korrekt. Der Fehlertext behandelt das Suchpfadsymbol nicht mehr, wenn Benutzer das Dialogfeld mit einem leeren Pflichtfeld senden. (CQ-4353009)

#### Sicherheit{#foundation-security-6525}

AEM auf die Zulassungsliste setzt jetzt zusätzliche Keywords, die das Client-Geheimnis enthalten. Die Konfigurationserstellung schlägt nicht mehr fehl, wenn unterstützte Integrationen diese Client-Geheimnis-Namensmuster verwenden. (GRANITE-66495)

<!-- #### Sling{#foundation-sling-6525} -->

<!-- #### SPA editor {#foundation-spa-editor-6525} -->

#### Übersetzung{#foundation-translation-6525}

Die Statuswerte des Übersetzungsprojekts werden jetzt nach dem Upgrade korrekt aktualisiert. Autoren können Entwürfe, laufende Prozesse und vollständige Werte überprüfen, ohne auf veraltete Metadaten aus früheren Service Pack-Verhaltensweisen angewiesen zu sein. (NPR-43418)

#### Benutzeroberfläche{#foundation-ui-6525}

* Manuell eingegebene URLs der Sites-Konsole werden jetzt in den vorgesehenen Seiten- oder Ordnerpfad aufgelöst. Die Inhaltshierarchie bleibt nach der Aktualisierung konsistent und fällt nicht mehr auf die Basis-URL zurück. (NPR-43688)
* Die CRX Package Manager-Test-Suite schlägt nicht mehr fehl, nachdem eine AEM 6.5 LTS SP1-Instanz auf LTS SP2 aktualisiert wurde. Der Test des Servlets für die Miniaturansicht wird jetzt erwartungsgemäß abgeschlossen. (NPR-43534)

* Die Inhaltsstruktur der Sites-Konsole wird jetzt nach jeder Browser-Aktualisierung konsistent geladen. Autoren sehen keine leere linke Leiste oder Meldung „Es gibt kein Element“ mehr, wenn Inhalt vorhanden ist. (NPR-43442)

<!-- #### WCM{#foundation-wcm-6525} -->

#### Workflow{#foundation-workflow-6525}

* Der Workflow-Modell-Editor validiert jetzt mandantenspezifische Workflow-Modellpfade korrekt. Kunden, die Workflow-Modelle unter /conf-Pfaden auf Mandantenebene speichern, können diese Modelle bearbeiten, ohne sie in globale Konfigurationspfade zu verschieben. (GRANITE-65376)

* Der Workflow-Modell-Editor normalisiert jetzt Windows-Dateipfade während der Pfadüberprüfung. Autoren können Workflow-Modelle auf Windows-Servern bearbeiten, ohne auf Fehler zugreifen zu müssen, die Modellaktualisierungen blockieren. (GRANITE-63692)
* Die Aufgabenerstellung umfasst jetzt eine Server-seitige Validierung für Fälligkeitsdaten. Benutzende können keine Aufgaben mit einem Fälligkeitsdatum erstellen, das vor dem Startdatum liegt, wodurch die Daten der Posteingangsaufgabe konsistent bleiben. (CQ-4362253)
* Bei der Namespace-Erstellung wird lokalisierter Text jetzt korrekt verarbeitet. Benutzer können nicht-lateinische Zeichen in das Feld Titel eingeben und den Namespace ohne Validierungsfehler erstellen. (CQ-4355587)

## Installieren von [!DNL Experience Manager] 6.5.25.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.25.0 erfordert [!DNL Experience Manager] 6.5. Detaillierte Anweisungen finden [&#x200B; in &#x200B;](/help/sites-deploying/upgrade.md)Upgrade-Dokumentation“. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.25.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.25.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.25.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Installieren des Service Packs für [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.25.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie den Paket-Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Paket-Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld in der Benutzeroberfläche vom Paket-Manager wird während der Installation des Service Packs manchmal beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.25.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API vom Paket-Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.25.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.25.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

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

UberJar für [!DNL Experience Manager] 6.5.25.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.25/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.25</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.



## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Unter [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md) finden Sie eine detaillierte Liste aller Funktionen, die für AEM 6.5 eingestellt oder entfernt wurden.

### Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API {#cf-support-assets-rest-api}

AEM 6.5 LTS SP2 bietet moderne OpenAPIs für die Verwaltung von Inhaltsfragmenten und -modellen. Daher wurden die älteren Endpunkte zur Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API jetzt eingestellt.

Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Mitteilung über das Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Verbesserungen an den veralteten Endpunkten.

### SPA-Editor {#spa-editor}

[Der SPA-Editor](/help/sites-developing/spa-overview.md) wird für neue Projekte ab Version 6.5.25 von AEM 6.5 nicht mehr unterstützt. Der SPA-Editor wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind nun:

* der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung
* der [Inhaltsfragment-Editor](/help/sites-developing/universal-editor/introduction.md) zur formularbasierten Bearbeitung

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

* **Verwandt mit Oak**
Ab Service Pack 13 und höher wird das folgende Fehlerprotokoll angezeigt, das sich auf den Persistenz-Cache auswirkt:

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

* Beim Versuch, Inhaltsfragmente, Sites oder Seiten zu verschieben, zu löschen oder zu veröffentlichen, tritt ein Problem auf, wenn Inhaltsfragmentreferenzen abgerufen werden. Die Hintergrundabfrage schlägt fehl; die Funktion funktioniert nicht.
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
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Ab AEM 6.5.15 weist die vom Bundle ```org.apache.servicemix.bundles.rhino``` bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten auf. Skripte, die den Strict-Modus (```use strict;```) verwenden, müssen ihre korrekten Variablen deklarieren. Andernfalls werden sie nicht ausgeführt und geben am Ende einen Laufzeitfehler zurück.

* Durch die Installation von Tagging-bezogenen, vorkonfigurierten Inhalten mithilfe eines offiziellen Aktualisierungspakets wird die Spracheigenschaft des Knotens `/content/cq:tags` auf den Standard zurückgesetzt. Diese Aktion gilt für Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, Patches usw. Daher ist es erforderlich, sie vor der Installation aus den Eigenschaften hinzuzufügen.

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6525}

Die Vorschau von Inhaltsfragmenten schlägt aufgrund des DoS-Schutzes für eine umfassende Fragment-Baumstruktur fehl. Siehe den [KB-Artikel zu den standardmäßigen GraphQL Query Executor-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6525}

* **FORMS-14521** Wenn ein(e) Benutzende(r) versucht, eine Vorschau eines Briefentwurfs mit gespeicherten XML-Daten anzuzeigen, bleibt er/sie für einige bestimmte Briefe im `Loading`-Status stecken.
* **FORMS-16603** In der Druckvorschau der Benutzeroberfläche für interaktive Kommunikationsagenten werden einige berechnete Werte nicht korrekt angezeigt.
* **FORMS-15681** Wenn der Brief in der Druckvorschau angezeigt wird, wird der Inhalt geändert. Einige Leerzeichen verschwinden und bestimmte Buchstaben werden durch `x` ersetzt.
* **FORMS-15428** Nach der Aktualisierung auf AEM Forms Service Pack 20 (6.5.20.0) mit dem Forms-Add-on funktionieren Konfigurationen, die auf dem veralteten Adobe Analytics Cloud-Service basieren und eine berechtigungsbasierte Authentifizierung verwenden, nicht mehr. Dieses Problem verhinderte die ordnungsgemäße Ausführung von Analyseregeln.
* **FORMS-16557** In der Druckvorschau der Benutzeroberfläche für interaktive Kommunikationsagenten wird das Währungssymbol (z. B. das Dollarzeichen $) nicht konsistent für alle Feldwerte angezeigt. Es wird für Werte bis 999 angezeigt, fehlt jedoch für Werte ab 1000.
* **FORMS-16575** Alle Änderungen an der XDP verschachtelter Layout-Fragmente in einer interaktiven Kommunikation werden nicht im IC-Editor übernommen.
* **FORMS-21378** Wenn die Server-seitige Validierung (SSV) aktiviert ist, können die Formularübermittlungen fehlschlagen. Wenn dieses Problem auftritt, wenden Sie sich bitte an den Adobe-Support.
* **FORMS-23722** Wenn ein Formular mit einem Feld **Dateianhang**, das `bindref` verwendet, an einen AEM-Workflow mit dem Schritt **Aufgabe zuweisen** gesendet wird, werden die Anlagen nicht angezeigt. Daher werden sie nicht angezeigt, wenn die Aufgabe aus dem Posteingang geöffnet wird. Die Dateien werden korrekt im Repository gespeichert, aber in der Benutzeroberfläche des Schritts „Aufgabe zuweisen“ können die Anlagen nicht angezeigt werden.
* **Benutzerdefinierte FORMS-23802**-Funktionen können nicht in der Vorschau geladen oder veröffentlicht werden, wenn ein adaptives Formular in eine Sites-Seite eingebettet ist. Dieses Problem tritt auf, wenn die **aem-forms-core-component**-Bibliotheksversion vor 1.1.76 liegt. Möglicherweise wird ein Fehler wie `InvalidFormContainerException: No form container found` in den Protokollen angezeigt. Um dieses Problem zu beheben[&#x200B; laden Sie den Hotfix für &#x200B;](/help/release-notes/aem-forms-hotfix.md) SP24 (AddOn 6.0.1454) herunter und installieren Sie ihn.

#### Bekannte Probleme mit verfügbaren Hotfixes {#aem-forms-issues-with-hotfixes}

<!--
>[!NOTE]
>
>Avoid upgrading to Service Pack 6.5.25.0 for issues without an available hotfix. It may lead to unexpected errors. Upgrade to Service Pack 6.5.25.0 only after the required hotfixes are released.
-->

Für die folgenden Probleme ist ein Hotfix zum Herunterladen und Installieren verfügbar. Sie können [den Hotfix herunterladen und installieren](/help/release-notes/aem-forms-hotfix.md), um diese Probleme zu beheben:

* **FORMS-23881** Bei AEM Forms-JEE-Bereitstellungen, die mit dem 6.5.23.0-Vollinstallationsprogramm eingerichtet wurden, kann der Ausgabe-Service Anfragen nicht verarbeiten, wenn beim Aufruf eine benutzerdefinierte XCI-Datei angegeben wird. Um dieses Problem zu beheben, installieren Sie das neueste Service Pack von AEM 6.5.25.0 Forms über das [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html)-Portal.
* **FORMS-23789** (nur AEM Forms auf JEE): Bei Benutzenden traten Probleme mit Log4j in AEM Forms auf JEE SP24 auf, was zu Störungen bei der Protokollierung und Überwachung für Unternehmenskunden führte. Um dieses Problem zu beheben, [&#x200B; Sie unter „Herunterladen und Installieren des &#x200B;](/help/release-notes/aem-forms-hotfix.md)&quot; für AEM Forms on JEE Service Pack 6.5.25.0.
* **Benutzerdefinierte FORMS-23802**-Funktionen werden nicht in der Vorschau- oder Veröffentlichungsinstanz geladen, wenn sich das Formular auf einer Sites-Seite mit einer älteren Version der Kernkomponente „aem-forms-core-component“ (&lt;1.1.76) befindet. Um dieses Problem zu beheben, installieren Sie den [AEM Forms-AddOn-Hotfix 6.0.1454](/help/release-notes/aem-forms-hotfix.md) für SP24.
* **FORMS-23789** (nur AEM Forms auf JEE): Bei Benutzenden traten Probleme mit Log4j in AEM Forms auf JEE SP24 auf, was zu Störungen bei der Protokollierung und Überwachung für Unternehmenskunden führte. Um dieses Problem zu beheben, [&#x200B; Sie unter „Herunterladen und Installieren des &#x200B;](/help/release-notes/aem-forms-hotfix.md)&quot; für AEM Forms on JEE Service Pack 6.5.25.0.
* **Benutzerdefinierte FORMS-23802**-Funktionen werden nicht in der Vorschau- oder Veröffentlichungsinstanz geladen, wenn sich das Formular auf einer Sites-Seite mit einer älteren Version der Kernkomponente „aem-forms-core-component“ (&lt;1.1.76) befindet. Um dieses Problem zu beheben, installieren Sie den [AEM Forms-AddOn-Hotfix 6.0.1454](/help/release-notes/aem-forms-hotfix.md) für SP24.
* AEM Forms enthält jetzt eine Aktualisierung der Struts-Version von 2.5.33 auf 6.x für die Formularkomponente. Dieses Upgrade liefert zuvor verpasste Struts-Änderungen, die nicht in SP24 enthalten waren. Die Unterstützung wurde über einen [Hotfix](/help/release-notes/aem-forms-hotfix.md) hinzugefügt. Diesen können Sie herunterladen und installieren, um Unterstützung für die neueste Version von Struts hinzuzufügen.
* **FORMS-14926** Führen Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) die folgenden Schritte aus, um das Problem zu beheben, wenn Sie doppelte Einträge von Geode-Jars `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` im `<AEM_Forms_Installation>/lib/caching/lib`-Ordner finden:

   1. Stoppen der Locators, falls sie noch ausgeführt werden.
   2. Stoppen des AEM-Servers.
   3. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
   4. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
   5. Öffnen der Eingabeaufforderung im Administratormodus.
   6. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

* **FORMS-15256** Beim Upgrade von AEM 6.5 Forms Service Pack 18 oder 19 auf Service Pack 20 oder 21 ist ein JSP-Kompilierungsfehler aufgetreten. Dieser Fehler hinderte sie daran, adaptive Formulare zu öffnen oder zu erstellen. Er hat auch Probleme mit anderen AEM-Schnittstellen verursacht. Diese Schnittstellen umfassten den Seiteneditor, die AEM Forms-Benutzeroberfläche, den Workflow-Editor und die Benutzeroberfläche der Systemübersicht.

  Wenn ein solches Problem auftritt, führen Sie die folgenden Schritte aus, um es zu beheben:
   1. Navigieren Sie in CRXDE zum Verzeichnis `/libs/fd/aemforms/install/`.
   2. Löschen Sie das Bundle `com.adobe.granite.ui.commons-5.10.26.jar`.
   3. Starten Sie den AEM-Server neu.

* **FORMS-23703** Wenn die `contains` ohne Standardwert konfiguriert ist, schlägt die Server-seitige Validierung für ein adaptives Formular fehl. Sie können die neueste Version von [AEM Forms 6.5.25.0 Service Pack](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#aem-65-forms-releases) installieren, um das Problem zu beheben.
* **GRANITE-63681** Formulardatenmodell-Connectoren können möglicherweise nicht authentifiziert werden, da die erforderlichen Schlüsselwörter und Regex-Muster standardmäßig nicht zulässig sind. Um das Problem zu beheben, laden Sie den Hotfix vom (Link[&#x200B; herunter und installieren &#x200B;](/help/release-notes/aem-forms-hotfix.md) ihn.
* Bei der **FORMS-23979**-Konvertierung von HTML in PDF (PDFG) können zeitweise Zeitüberschreitungen auftreten. Anschließend wurde eine neuere Version des Forms-Add-ons für SP24 veröffentlicht, die die Fehlerbehebung enthält. Wenn dieses Problem auftritt, aktualisieren Sie Ihre Umgebung auf das [neueste veröffentlichte Forms-Add-on für 6.5.25.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#aem-65-forms-releases).
* **FORMS-23717** Nach dem Upgrade auf **AEM Forms-6.5.25.0** können `server.log` und `error.log` mit wiederholten WARNMELDUNGEN wie *Erstellung der sicheren Parserfactory fehlgeschlagen* oder *Sicherheitsattribut … wird nicht unterstützt*. Protokolle können um ca. **5-10 Zeilen pro Sekunde (** von MB pro Stunde) zunehmen, wodurch Festplatten ausgefüllt und der Produktions-Rollout blockiert werden kann.

Um das Protokollvolumen zu reduzieren, legen Sie in Ihrer Anwendungsserverkonfiguration oder über die JVM-`-Dlogging.level.com.adobe.util.XMLSecurityUtil=ERROR` die Protokollierungsebene für `com.adobe.util.XMLSecurityUtil` auf `ERROR` fest. Diese Funktion blendet nur die Nachrichten aus und behebt nicht die zugrunde liegende Ursache.

* **FORMS-23875** Bei der Formulardatenmodellsuche wird ein HTML-Tag in der Benutzeroberfläche angezeigt, auch wenn keine relevante Entität vorhanden ist. Um das Problem zu beheben, laden Sie den Hotfix von [dem Link“ herunter und &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bb-expressionmanager-pkg-10.0.48.zip) Sie ihn.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.25.0enthaltenen OSGi-Pakete](/help/release-notes/assets/65250-bundles.zip)
<!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.25.0enthaltenen Inhaltspakete](/help/release-notes/assets/65250-packages.zip)
<!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kundinnen und Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produkt-Download unter „licensing.adobe.com“](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience#).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)



