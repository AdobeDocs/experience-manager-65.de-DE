---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
contentOwner: Rick Brough
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 56b13809475a59f188750b86503e316e69171fe1
workflow-type: tm+mt
source-wordcount: '7273'
ht-degree: 15%
---
# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!--
DO NOT DELETE THIS HIDDEN NOTE!      DO NOT DELETE THIS HIDDEN NOTE!
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, May 29, 2025. In addition, a list of Forms fixes and enhancements is added to this section.
-->

## Versionsübersicht {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.26.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;12. November 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.26.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |


<!-- REWRITE AI GENERATED SUMMARY OF NOTES BELOW FOR EACH NEW SERVICE PACK RELEASE -->

Experience Manager 6.5.26.0 enthält neue Funktionen, wichtige von Kundschaft angeforderte Verbesserungen und Fehlerbehebungen. Sie umfasst außerdem Verbesserungen in den Bereichen Barrierefreiheit, Lokalisierung, Leistung, Stabilität und Sicherheit, die auf der seit April 2019 verfügbaren 6.5-Foundation basieren.

Zu den wichtigsten Merkmalen von Service Pack 26 gehören die folgenden:

* Sicherheit. Zwei kritische Fehlerbehebungen schließen eine Schwachstelle beim Einschleusen von Server-seitigen Vorlagen im Metadaten-Editor und Verstöße gegen Cross-Site-Scripting (XSS) in Coral-Servlets der Benutzeroberfläche.
* C2PA-Konformität. Assets erkennt jetzt C2PA-Anmeldeinformationen und signiert Ausgabedarstellungen, die der Workflow zum Aktualisieren von Assets generiert. Das Signieren wird in jeder Instanz lokal ausgeführt und dedizierte oder kundeneigene Signaturinfrastrukturen werden nicht unterstützt.
* Barrierefreiheit Über 25 Fehlerbehebungen helfen der Seiteneditor- und der Sites-Konsole, die WCAG-Anforderungen an Kontrast, Tastatur und Bildschirmlesehilfe zu erfüllen.
* Lokalisierung. Dutzende von Fehlerbehebungen übersetzen Zeichenfolgen und korrigieren Layout-Probleme in Sites, Assets, Sicherheit und Vorgängen.
* Zuverlässigkeit. Fehlerbehebungen zur Behebung von GraphQL-Sperrkonflikten bei Veröffentlichungsinstanzen, MSM-Rollouts, Symbolleistenaktionen des Rich-Text-Editors und Seitenaktivierung in der klassischen Benutzeroberfläche.
* Analytics. Die Launch-Integration verwendet die Adobe Analytics 2.0-API vor dem Ende der Nutzungsdauer von Analytics 1.4 am 31. August 2026.


<!-- UPDATE FOR EACH NEW RELEASE -->

## Behobene Probleme, Verbesserungen und Verbesserungen in Service Pack 26 {#fixed-issues}

<!-- 6.5.25.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->


### [!DNL Sites]{#sites-6526}

#### Barrierefreiheit {#sites-accessibility-6526}

* Autoren können Komponenten nur über die Tastatur hinzufügen, verschieben und entfernen. Für die Drag-and-Drop-Interaktion war ein Zeiger erforderlich, sodass das Tastaturkriterium WCAG 2.1.1 nicht erfüllt war. Der Editor bietet jetzt das Popup-Fenster „Komponente einfügen“, Ausschneiden und Einfügen sowie Löschen als Tastaturäquivalente. (SITES-25359)

* Autoren können jetzt die Schaltfläche für das aktive Format („T„) im Inline-Menü der Textkomponente sehen. Nachdem Autoren fett oder kursiv formatiert hatten, blieb das Schaltflächensymbol vor einem dunkelgrauen Hintergrund dunkel und verpasste das WCAG 2.1 AA-Kontrastverhältnis von mindestens 4,5:1. Das aktualisierte CSS hellt das Symbol auf, wodurch der Kontrast wiederhergestellt wird, den frühere Service Packs bereitgestellt haben. (SITES-51864)

* Auf der Registerkarte Assets im Seiteneditor wird jetzt eine übersetzte Zeichenfolge in der Dropdown-Liste Komponenten auswählen angezeigt, nachdem Sie im Dropdown-Menü Bilder die Option Absätze ausgewählt haben. Zuvor erschien die Zeichenfolge „OTHER“ auf Englisch, da sie in den Lokalisierungsressourcen fehlte. Das aktualisierte Wörterbuch liefert die Übersetzung in allen Gebietsschemata. (SITES-24525)




* Der ContextHub-IFrame im Seiteneditor verfügt jetzt über ein beschreibendes Titelattribut. Zuvor hatte das `contexthub-ui-iframe`-Element keinen Titel, sodass Benutzende der Bildschirmlesehilfe es nicht identifizieren konnten, wenn der Fokus darauf verschoben wurde. Der Titel wird jetzt auf jeder Editor-Seite und in jeder Editor-Ansicht angezeigt, einschließlich Arbeitsfläche, Seitenleiste und Layout-Vorschau. (SITES-24650)
* Die Schaltfläche „Filter“ in der Filterleiste der Sites-Konsole fügt keine sichtbaren Beschriftungen über den Feldern „Gespeicherte Suchen“ und „Suchverzeichnis auswählen“ hinzu. Bei einer Prüfung wurde gemeldet, dass Beschriftungen angezeigt wurden, wenn der Fokus die Schaltfläche verließ, eine Taste gedrückt wurde oder auf die Schaltfläche geklickt wurde. Beim Testen konnte das Verhalten nicht reproduziert werden, sodass keine Änderung erforderlich war. (SITES-24706)
* Links in der Sites-Konsole App-Navigation stechen jetzt deutlicher hervor. Der Link-Text entsprach dem Kontrastverhältnis von 4,5:1, aber das geringe Schriftgewicht und die geringe Größe machten die Links schwer zu erkennen. Eine größere Schriftgröße und ein größeres Schriftgewicht machen den Text für Benutzer mit Sehbehinderungen leichter lesbar. (SITES-24723)
* Die Sprachausgabe gibt vor dem QuickInfo-Inhalt im Modal „Benutzereinstellungen“ nicht mehr „leer“ aus. Zuvor wurde das Informationssymbol `role="tooltip"` mit einem `aria-labelledby` verwendet, sodass die NVDA zuerst eine leere Bezeichnung las. Das Symbol verwendet jetzt `role="button"` und eine `aria-label` von „Informationen“, und die Änderung gilt für die Coral-Formularkomponenten, die das Muster gemeinsam haben. (SITES-24732)
* Die Schaltfläche Löschen im Modal Löschen erfüllt jetzt die WCAG 1.4.3-Kontrastanforderung von 4,5:1. Zuvor ergab weißer Text auf rotem Hintergrund ein Verhältnis von 3,9:1, nachdem Autoren ein Element ausgewählt und in der Aktionssymbolleiste auf Löschen geklickt hatten. Die dunklere Schaltflächenfarbe macht die Beschriftung für Autoren mit Sehbehinderungen lesbar. (SITES-24772)
* Die Überschrift Verweise in der Leiste Verweise der Sites-Konsole verwendet jetzt ein Überschriftenelement anstelle eines `div`. Zuvor konnte der Text von der Sprachausgabe nicht als Überschrift angekündigt werden, sodass Benutzende nicht nach Überschriften navigieren konnten. Die Überschrift wird auch oben in der Ansicht der anfänglichen Verweise angezeigt. (SITES-24967)
* Die Fokusanzeige für Akkordeon-Schaltflächen in der Filterleiste der Sites-Konsole erfüllt jetzt die WCAG 1.4.11-Kontrastanforderung von 3:1. Zuvor zeigte der blaue Indikator ein Verhältnis von 2,3:1 im Hintergrund, wodurch die Akkordeon-Schaltfläche Tags für Tastaturbenutzer schwer zu finden war. Die aktualisierte Farbe gibt Tastaturbenutzern einen klaren Fokus. (SITES-24986)
* Die Fokusanzeige für Optionsfelder in der Filterleiste der Sites-Konsole erfüllt jetzt die WCAG 1.4.11-Kontrastanforderung 3:1. Zuvor zeigte der hellblaue Indikator ein Verhältnis von 1,7:1 vor dem Hintergrund. Tastaturbenutzer können jetzt ihre Position im Akkordeon Geändert am nachverfolgen. (SITES-24987)
* Die Schaltfläche Auswählen neben den Feldern Pfad und Tags in der Seitenleiste des Seiteneditors verwendet kein Kontrollkästchen-Symbol mehr. Zuvor wurde durch das Symbol ein Umschalter vorgeschlagen, aber durch Aktivieren der Schaltfläche wurde ein Modal geöffnet, das das Verzeichnis „Baumstruktur“ enthält. Die Schaltfläche Auswählen kommuniziert nun ihre Funktion korrekt, und dasselbe gilt für das Bild- und Teaser-Modal. (SITES-25210)
* Bildschirmlesehilfen überspringen jetzt die Miniaturbilder von Assets in der Seitenleiste des Seiteneditors. Zuvor enthielt jedes Bild alternativen Text, der den Namen des sichtbaren Assets duplizierte, sodass Benutzende denselben Text zweimal hörten. Ein leeres `alt` kennzeichnet das Bild als dekorativ und behält den Namen im Kartentitel bei. (SITES-25213)
* Bildschirmlesehilfen erkennen die Liste der Seitenleisten-Komponenten als Liste. Bei einer Prüfung wurden die Elemente als nicht verwandte Elemente gemeldet, beim Testen wurde jedoch bestätigt, dass das Markup ein Listenelement und Listenelemente verwendet. Es war keine Code-Änderung erforderlich. (SITES-25214)
* Die Informationssymbole für Komponenten in der Seitenleiste des Seiteneditors sind größer und leichter zu erkennen. Zuvor verwendeten die Symbole die extra kleine Größe von etwa 12 px, die Benutzer mit Sehbehinderungen schwer zu sehen fanden. Für die Symbole wird jetzt die mittlere Größe verwendet. (SITES-25217)
* Die Fokusanzeige auf der Schaltfläche Farbfeld im Anmerkungsmodal hebt sich jetzt von der Schaltfläche ab. Zuvor entsprach der Indikator der Farbfeldfarbe. Dadurch war es für Tastaturbenutzer schwierig zu erkennen, welche Schaltfläche den Fokus hatte. Ein Versatz gibt dem Indikator genügend Kontrast zum Hintergrund und hält ihn deutlich sichtbar. (SITES-25253)
* Das Datumsfeld im Timewarp-Modal wird nicht mehr `aria-haspopup="dialog"`. Zuvor gab die Sprachausgabe an, dass das Feld ein Dialogfeld öffnet, obwohl dies nicht der Fall ist. Durch Entfernen des Attributs erhalten Benutzende von Bildschirmlesehilfen genaue Informationen. (SITES-25263)
* Textbeschriftungen in der Demografie-Symbolleiste, z. B. „Empfohlen“, erfüllen jetzt die WCAG 1.4.3-Kontrastanforderung 4,5:1. Zuvor ergab grauer Text auf dunkelgrauem Hintergrund im Vorschaumodus ein Verhältnis von 2,8:1. Je nach Hintergrund wird jede Beschriftung durch dunkleren oder helleren Text lesbar. (SITES-25307)
* Die Fokusanzeige auf den Schaltflächen &quot;Commerce&quot;, „Persona“ und „Gerät“ in der Symbolleiste „Demografie“ erfüllt jetzt die Kontrastanforderung von 3:1 für WCAG 1.4.11. Zuvor wies der Indikator ein Verhältnis von 1,9:1 gegenüber dem Symbolleistenhintergrund auf. Tastaturbenutzer können jetzt ihre Position verfolgen. (SITES-25308)
* Text, den Autorinnen und Autoren in die Textfelder der Demografie-Symbolleiste eingeben, erfüllt jetzt die WCAG 1.4.3-Kontrastanforderung von 4,5:1. Zuvor ergab weißer Text auf grauem Hintergrund ein Verhältnis von 2,9:1 in Feldern, wie z. B. dem Dropdown-`displayName` Profil im Vorschaumodus. Die aktualisierten Farben machen eingegebene Werte für Autoren mit Sehbehinderungen lesbar. (SITES-25318)
* Die Sprachausgabe liest jetzt die QuickInfo Beschreibung , wenn der Fokus die Kontrollkästchen in den Dialogfeldern Teaser, Bild und Karussell erreicht. Zuvor war der Text nicht programmgesteuert mit dem Kontrollkästchen verknüpft, sodass die Benutzenden die Anweisung nicht hören konnten. Ein `aria-describedby`-Attribut verknüpft nun jedes Kontrollkästchen mit seiner Beschreibung. (SITES-25364)
* Die Sprachausgabe gibt jetzt an, welche Schaltfläche für Absatzformate im Rich-Text-Editor aktiv ist. Zuvor gab die Auswahl einer Option aus der Liste keinen Hinweis auf die aktuelle Auswahl für die Hilfstechnologie. Die aktive Schaltfläche enthält jetzt `aria-current="true"`, und die Option Aktives Hyperlink-Ziel `aria-selected="true"`. (SITES-25367)
* Die Sortierschaltflächen in der Tabellenkopfzeile der Listenansicht der Sites-Konsole erfüllen jetzt die WCAG 1.4.11-Kontrastanforderung 3:1. Zuvor wiesen die hellgrauen Symbole ein Verhältnis von 1,5:1 gegenüber dem Kopfzeilenhintergrund auf. Die dunklere Symbolfarbe macht die Schaltflächen für Autoren mit Sehbehinderungen sichtbar. (SITES-25372)
* Die Assets-Registerkarte in der Seitenleiste des Seiteneditors wird nicht mehr neu geladen, wenn der Fokus auf das Filterfeld verschoben wird. Zuvor löste das Wechseln zum leeren Feld ein erneutes Laden aus, und die Sprachausgabe gab jedes Mal eine Lademeldung aus. Die Registerkarte wird jetzt erst neu geladen, nachdem Sie den Filterwert geändert und die Eingabetaste gedrückt haben. (SITES-25377)
* Das ausgewählte Farbfeldsymbol im Anmerkungsmodal erfüllt jetzt die WCAG 1.4.11-Kontrastanforderung von 3:1. Zuvor wies das weiße Häkchen ein Verhältnis von nur 1,58:1 gegenüber gelben, orangen und grünen Farbfeldern auf. Das aktualisierte Symbol gibt Autoren mit Sehbehinderungen einen klaren Indikator. (SITES-25523)
* Die Komponentenliste im Seitenbereich des Seiteneditors nimmt den Tastaturfokus nicht mehr ein. Tastaturbenutzer wählen Komponenten mit den Steuerelementen im Inhaltsfenster aus, sodass die Liste des Seitenbereichs die Funktion wiederholt. Ein Hinweis unter dem Komponentenfilter informiert Tastaturbenutzer darüber, wo die Steuerelemente zu finden sind. (SITES-40752)


#### Admin-Benutzeroberfläche{#sites-adminui-6526}


#### Klassische Benutzeroberfläche{#sites-classicui-6526}

* Autoren können Seiten in der Sites-Konsole der klassischen Benutzeroberfläche (`siteadmin.html`) erneut aktivieren. Zuvor wurde mit der Schaltfläche Seite aktivieren ein unbefristeter „Lade“-Spinner angezeigt und die Replikation wurde nie ausgelöst, da ein fehlgeschlagenes Tracking-Skript den Klick-Handler angehalten hat. Der Klick-Handler wird jetzt fehlerfrei ausgeführt und schließt die Aktivierung ab. (SITES-52165)
* Der indonesische Sprach-Code wird jetzt in den Eigenschaften der Sprachkopie als ID angezeigt. Zuvor wurde in der Leiste „Verweise“ der Legacy-Code in für Seiten unter dem indonesischen Sprachstamm angezeigt. Die Aktualisierung des Bundles cq-wcm-core korrigiert den Wert, sodass der Code dem ISO-Standard entspricht. (SITES-4491)

<!--
#### Component Console{#sites-component-console-6526}



#### [!DNL Content Fragments]{#sites-contentfragments-6526}



#### [!DNL Content Fragments] - Admin{#sites-admin-6526}
-->


#### [!DNL Content Fragments] - Fragment-Editor{#sites-fragments-editor-6526}

* Die Schaltfläche Inhaltsfragment bearbeiten wird sofort für jeden Mehrfachfeld-Verweis im Inhaltsfragment-Editor angezeigt. Zuvor blieb die Schaltfläche ausgeblendet, bis Autoren das übergeordnete Fragment gespeichert hatten, und sie führte nach dem Öffnen des Pfad-Browsers keine Aktion aus. Der Editor erstellt die Aktionsliste jetzt beim ersten Rendern, sodass Autoren referenzierte Fragmente ohne zusätzliche Schritte öffnen. (SITES-43733)

* Chinesische, japanische und koreanische Zeichen werden im Platzhalter im Dialogfeld Inhaltsfragment erstellen nicht mehr kursiv angezeigt. Zuvor wurde der Kursivstil auf CJK-Zeichen unter **Assets** > **Files** angewendet, wodurch der Text schwer lesbar wurde. Die aktualisierten Stile überspringen Kursivformatierung für CJK-Sprachen. (SITES-43548)
* Der Inhaltsfragment-Editor validiert Felder nach der Aktualisierung der Granite-Benutzeroberfläche korrekt. Eine kürzlich vorgenommene Änderung an der Granite-Benutzeroberfläche führte zu einer Regression, sodass die Client-Bibliotheken des Editors nicht mehr dem neuen Validierungsverhalten entsprachen. Die angepassten Bibliotheken und Tests beheben die Nichtübereinstimmung. (SITES-46650)


#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6526}

* GraphQL-Abfragen zu Inhaltsfragmenten erkennen jetzt RemoteRef-Verweise auf Dynamic Media mit OpenAPI Assets. Zuvor schlugen Abfragen mit dem Fehler „Validierung der persistierten Abfrage“ fehl und gaben keine Asset-Daten zurück, wenn AEM 6.5 Sites AEM as a Cloud Service Assets nutzte. Antworten enthalten jetzt die Repository-ID und die Asset-ID, sodass Clients Versand-URLs erstellen können. (SITES-48507)

* Veröffentlichungsinstanzen reagieren auch bei hohem Traffic durch GraphQL. Sperren Sie Konflikte in `GraphQLServiceImpl` Threads mit verzögerter Anforderungsverarbeitung bei den Schemamethoden, wodurch Anforderungen verlangsamt und Neustarts erforderlich werden. Durch die verbesserte Synchronisierung werden die Leistungseinschränkungen behoben und die Verfügbarkeit von Sites und mobilen Apps aufrechterhalten. (SITES-48699)

* Die Meldung auf der Seite &quot;GraphQL-Endpunkte“ bleibt nach dem Neuladen der Seite lokalisiert. Zuvor wurde beim Erstellen und Löschen der Endpunkte die Meldung „Keine Endpunkte gefunden“ in Ihrer Sprache angezeigt, sie wurde jedoch nach dem Neuladen auf Englisch zurückgesetzt. Die Seite lädt nun bei jedem Besuch die übersetzte Zeichenfolge. (SITES-43586)


<!--
#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6526}
-->


#### [!DNL Content Fragments] - Modelle und Modell-Editor{#sites-models-model-editor-6526}

* Miniaturansichten für Inhaltsfragmentmodelle werden unter **Tools** > **Allgemein** > **Inhaltsfragmentmodelle** angezeigt, wenn der Konfigurationsname lokalisierte Zeichen enthält, z. B. „español &quot;. Zuvor wurde die hochgeladene Miniaturansicht nicht angezeigt, da die Zeichen einen Fehler im Pfad verursacht haben. Die aktualisierte Handhabung codiert den Namen korrekt. (SITES-39242)

* Die Zeichenfolge Feldbezeichnung auf der Arbeitsfläche des Inhaltsfragmentmodell-Editors wird jetzt in der Benutzersprache angezeigt. Zuvor blieb die Beschriftung in englischer Sprache, nachdem Autoren eine Komponente auf die Arbeitsfläche gezogen hatten, und sie wurde erst übersetzt, nachdem sie das Modell gespeichert und erneut geöffnet hatten. Die Beschriftung wird jetzt sofort übersetzt, wobei sie mit dem Bedienfeld Eigenschaften übereinstimmt. (SITES-45383)


<!--
#### [!DNL Content Fragments] - REST API{#sites-restapi-6526}

#### ContextHub{#sites-contexthub-6526}
-->


#### Core-Backend{#sites-core-backend-6526}

* Die geplante Seitenaktivierung über die Ein-Aus-Zeit wird jetzt nur mehr ausgeführt, wenn erforderlich. `OnOffTriggerProcessor` hat zuvor zu oft Replikations- und Cache-Invalidierung ausgelöst, was Autoren gezwungen hat, Inhalte manuell erneut zu veröffentlichen. Durch die Backport-Fehlerbehebung wird die unnötige Verarbeitung eliminiert und eine zuverlässige geplante Veröffentlichung wiederhergestellt. (SITES-48483)

* Der Datei-Upload funktioniert für Remote-Assets aus dem Asset-Management der nächsten Generation in einem Multifield. Zuvor schlug der Upload fehl, wenn Autoren ein Remote-Asset für ein Feld in einem Mehrfachfeld auswählten. Die Aktualisierung der Kernkomponenten stellt den Upload-Fluss wieder her, sodass das Feld das Asset akzeptiert. (SITES-44266)


#### Kernkomponenten{#sites-core-components-6526}

* Die Remote-Asset-Auswahl speichert das Bild jedes Mehrfachfeld-Elements separat. Wenn Sie zuvor ein Bild in einem Mehrfachfeld-Element ausgewählt haben, wurde es auf jedes andere Element angewendet, und die Remote-Asset-Referenz wurde nicht gespeichert. Jedes Element verfügt jetzt über eine eigene Auswahl, und der Verweis bleibt nach dem Speichern des Dialogfelds bestehen. (SITES-42376)

* Diese Version enthält Fehlerbehebungen für Commerce, Kernkomponenten, Foundation-Komponenten (veraltet), Launches und MSM-Live Copies. Die Korrekturen beheben Sicherheitslücken, Cross-Site-Scripting (XSS)-Verletzungen, das Verhalten beim Hochladen von Dateien und das Verhalten bei Live Copies. Die Backports bringen AEM 6.5 und AEM 6.5 LTS in Einklang mit Fehlerbehebungen, die zuvor in AEM as a Cloud Service bereitgestellt wurden. (SITES-43738)


<!--
#### Campaign integration{#sites-campaign-integration-6526}

#### ContentHub {#sites-contenthub-6526}

#### Crosswalk {#sites-crosswalk-6526}

#### Experience Fragments{#sites-experiencefragments-6526}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-6526}
-->


#### Headless - Admin {#sites-headless-admin-6526}

Verbesserung: Die Vorschau im Headless-Admin übergibt jetzt den ausgewählten Variantenpfad an die Vorschaukomponente. Durch diese Änderung wird sichergestellt, dass in der Vorschau von Inhaltsfragmenten mit mehreren Varianten Inhalte aus der richtigen Variante geladen werden. Das `draftFragmentIds`-Array enthält den Variantenparameter. (SITES-42714)


#### Launches{#sites-launches-6526}

* Zeitleisten-Einträge für hochgestufte Launches werden jetzt in der Sprache des Benutzers angezeigt. Zuvor blieben die Zeichenfolgen „Erstellte Version von“ und „Vor dem Bewerben des Starts“ auf Englisch, nachdem Autoren einen Launch beworben und die Zeitleiste für die Site in Sites geöffnet hatten. Die aktualisierten Ressourcen enthalten die Übersetzungen in allen Gebietsschemata. (SITES-13389)
* Der Platzhalter Pfad des Launch-Source auswählen im Filterfeld Launches wird vollständig angezeigt. Zuvor war der Text in lokalisierten Schnittstellen wie Französisch, Italienisch und Portugiesisch abgeschnitten, weil er nicht in das Feld passte. Das aktualisierte Layout zeigt den vollständigen Platzhalter an. (SITES-42792)
* Die Spalte Live-Datum in Tools > Sites > Launches zeigt nicht mehr AM oder PM in den Gebietsschemata Deutsch, Französisch, Spanisch, Italienisch, Portugiesisch (Brasilien) und Traditionelles Chinesisch an. Zuvor verwendete die Spalte ein 12-Stunden-Format, das nicht mit diesen Gebietsschemata übereinstimmt. Die Spalte zeigt jetzt das 24-Stunden-Format an. (SITES-43178)


<!--
#### Link Checker{#sites-link-checker-6526}
-->


#### Lokalisierung{#sites-localization-6526}

* Zeichenfolgen auf den Seiten für Konsistenzberichte unter **Tools** > **Vorgänge** werden jetzt in der Sprache des Benutzers angezeigt. Zuvor wurden Meldungen zu Ressourcensuchpfad, Wartung, Replikationswarteschlange, Protokollfehlern, aktiven Bundles und Anfrageleistung weiterhin in englischer Sprache angezeigt. Aktualisierte i18n-Ressourcen liefern die Übersetzungen, und eine Fallback-Datei hält die Zeichenfolgen verfügbar. (NPR-44279)

* Die Fehlermeldung „Einstellungen zum &#39;JSON-Pfad&#39; werden ignoriert, wenn die Option &#39;Manuell hinzufügen&#39; aktiviert ist“ wird jetzt in der Benutzersprache in der Konsole **Tools** > **Assets** > **Metadatenschemata** angezeigt. Zuvor blieb die Nachricht in englischer Sprache, nachdem Autoren ein Dropdown-Element hinzugefügt, über den JSON-Pfad hinzugefügt und zu Manuell hinzufügen gewechselt hatten. Die aktualisierten Ressourcen liefern die Übersetzungen. (ASSETS-31575)
* Die Zeichenfolge „Hochgestuft“ in **Assets** > **Verwalten**-Tags wird jetzt in der Benutzersprache angezeigt. Zuvor blieb die Zeichenfolge auf Englisch, wenn Sie den Mauszeiger über ein Smart-Tag bewegten, nachdem Sie „Bewerben“ ausgewählt hatten. Die aktualisierten Ressourcen liefern die Übersetzung in allen Gebietsschemata. (ASSETS-36070)
* Die Schaltflächenbeschriftung Hinzufügen überschneidet sich nicht mehr mit der Schaltfläche in **Ordnereigenschaften** > **Asset-Beitrag**. Zuvor kollidierte der Text in der deutschen, italienischen und brasilianischen portugiesischen Benutzeroberfläche mit der Schaltfläche, nachdem Sie einen Ordner mit der Einstellung „Asset-Beitrag“ erstellt hatten. Aktualisierte Stile geben den längeren übersetzten Beschriftungen genügend Platz. (ASSETS-36746)
* Spaltentitel werden in der Assets-Listenansicht jetzt horizontal in der japanischen Benutzeroberfläche angezeigt. Zuvor wurden die Titel vertikal in der Listenansicht unter **Assets** > **Dateien** und in der Kartenansicht des Inhaltsfragment-Editors angezeigt. Das aktualisierte `cq-dam-content` korrigiert die Textrichtung. (ASSETS-43105)
* Der Veröffentlichungsstatus „Für später geplant“ in der Spaltenansicht von Assets wird jetzt in der Benutzersprache angezeigt. Zuvor blieb die Zeichenfolge in englischer Sprache, nachdem Autoren ein Asset ausgewählt, **Veröffentlichung verwalten**, die Option **Später** ausgewählt, ein Datum hinzugefügt und veröffentlicht hatten. Das aktualisierte `cq-dam-content`-Paket stellt die Übersetzungen in allen Gebietsschemata bereit. (ASSETS-43307)
* Zeichenfolgen auf der Registerkarte **Smart-Tags** Konfiguration) werden jetzt für Französisch- und brasilianisches Portugiesisch vollständig angezeigt. Zuvor war der Text abgeschnitten, nachdem Sie auf **Erstellen** unter **Tools** > **Cloud Services** > **Smart Tag** geklickt hatten. Um den Text ohne QuickInfo zu lesen, verwenden Sie die CSS-Aktualisierung, die ausreichend Platz bietet. (ASSETS-68045)
* Die Zeichenfolge „Multi Path Value Property Predicate“ in der Assets Admin-Suchleiste wird jetzt in der Sprache des Benutzers angezeigt. Zuvor blieb die Zeichenfolge auf Englisch, als Admins das Suchformular unter **Tools** > **Allgemein** > **Suche** bearbeiteten und das Prädikat auf das Formular zogen. Das aktualisierte `cq-dam-content`-Paket stellt die Übersetzungen bereit. (CQ-4336103)
* Aria-Kennzeichnungen werden in der Projektansicht jetzt in der Benutzersprache angezeigt. Zuvor hatte die Schaltfläche Aktionen auf jeder Projektkachel keinen barrierefreien Namen, und die Aktion Kachel konfigurieren verwendete eine hartcodierte englische Beschriftung, während gleichrangige Beschriftungen lokalisiert wurden. Das aktualisierte Kachelskript liefert eine lokalisierte Bezeichnung für beide Aktionen. (CQ-4352359)
* Smart-Sammlungen mit chinesischen, japanischen oder koreanischen Zeichen im Namen werden jetzt korrekt gespeichert. Zuvor ist das Speichern einer Sammlung aus **Assets** > **Dateien** > **Filter** mit „Suche speichern fehlgeschlagen - Ungültige Anfrage, doppelte Sammlung nicht zulässig“ fehlgeschlagen, wenn der Name CJK-Zeichen enthielt. Bei der Duplikatsprüfung werden jetzt die Sammlungstitel anstelle der Knotennamen verglichen, sodass Sammlungen mit unterschiedlichen CJK-Titeln nicht mehr in Konflikt stehen. (GRANITE-62592)
* In der Dropdown-Liste **Land/Region** > **Benutzer** > **Erstellen** werden Namen nun alphabetisch nach der Sprache der Person sortiert. Zuvor sortierte die Liste die Namen in englischer Reihenfolge, während sie lokalisierte Namen anzeigte, sodass Länder in Gebietsschemata wie Japanisch ungeordnet erschienen. Das aktualisierte `com.adobe.granite.security.content`-Bundle sortiert nach Gebietsschema-fähigen Regeln. (GRANITE-67789)
* Der Haftungsausschluss für die AuditLog-Wartungsaufgabe unter **Tools** > **Vorgänge** > **Wartung** wird jetzt in der Sprache des Benutzers angezeigt. Zuvor wurde die Warnung zu Auditprotokolllöschung und Compliance-Anforderungen in englischer Sprache angezeigt, nachdem auf das Haftungsausschlusssymbol im wöchentlichen Wartungsfenster geklickt wurde. Die aktualisierten Ressourcen liefern die Übersetzung in allen Gebietsschemata. (NPR-44189)
* Berechtigungsnamen in **Sicherheit** > **Berechtigungen** > **Audit-Ansicht** werden jetzt in der Sprache des Benutzers angezeigt. Zuvor erschienen die Namen auf Englisch, weil die Übersetzungen fehlten. Das aktualisierte `com.adobe.granite.platform.i18n`-Bundle stellt sie bereit. (NPR-44477)
* Das Dialogfeld Konsistenzprüfung unter **Sicherheit** > **Adobe IMS-Konfigurationen** wird jetzt in der Benutzersprache angezeigt. Zuvor wurden im Dialogfeld englische Zeichenfolgen in lokalisierten Benutzeroberflächen angezeigt, da die Übersetzungen fehlten. Das aktualisierte `com.adobe.granite.platform.i18n`-Bundle stellt sie bereit. (NPR-44479)
* Zeichenfolgen im Tool für die Benutzersynchronisierungsdiagnose unter **Tools** > **Vorgänge** > **Diagnose** werden jetzt in der Sprache des Benutzers angezeigt. Zuvor zeigte das Tool englischen Text in lokalisierten Benutzeroberflächen. Das aktualisierte `com.adobe.granite.platform.i18n` liefert die Übersetzungen. (NPR-44481)
* Konfigurationsflüsse zeigen jetzt benutzerfreundliche Fehlermeldungen in der Sprache des Benutzers an. Zuvor führten Fehler auf den Konfigurationsseiten von AEM zu technischem oder unübersetztem Text. Das aktualisierte `com.adobe.granite.ui.content` behandelt die Fehler und liefert lokalisierte Nachrichten. (NPR-44840)
* Die Fehlermeldung, die angezeigt wird, wenn Sie die Eigenschaften einer gelöschten Gruppe unter **Sicherheit** > **Gruppen** ändern, wird jetzt in der Sprache der Benutzerin bzw. des Benutzers angezeigt. Zuvor blieb die Nachricht für lokalisierte Schnittstellen auf Englisch. Das aktualisierte `com.adobe.granite.security.content` liefert die Übersetzungen. (NPR-44841)
* Die Fehlermeldung „Beim Speichern der Änderungen in der Gruppe ist ein Fehler aufgetreten!“ wird jetzt in der Benutzersprache in der Konsole **Sicherheit** > **Gruppen** > **Gruppe bearbeiten** angezeigt. Zuvor blieb die Nachricht für lokalisierte Schnittstellen auf Englisch. Das aktualisierte `com.adobe.granite.security.content` liefert die Übersetzungen. (NPR-44842)
* Chinesische, japanische und koreanische Zeichen werden in der Fehlermeldung zum Posteingangssymbol nicht mehr kursiv angezeigt. Zuvor verzerrte der kursive Stil die Zeichen und erschwerte die Lesbarkeit des Textes. Das aktualisierte `com.adobe.granite.ui.coralui3` entfernt den Stil für diese Sprachen. (NPR-44843)
* Zahlen in **Vorgänge** > **Überwachung** folgen jetzt dem Gebietsschemaformat des Benutzers. Zuvor wurden auf der Seite Zahlen in einem festen Format angezeigt, unabhängig von der Sprache der Benutzeroberfläche. Das aktualisierte `com.adobe.granite.monitoring.dashboard`-Bundle wendet die richtigen Trennzeichen und das richtige Format an. (NPR-44844)
* Auf der Registerkarte Abfrage erläutern wird jetzt das „Query Builder Debugger-Tool“ angezeigt. Link in der Sprache des Benutzers. Zuvor fehlte der Link-Text in lokalisierten Schnittstellen, da die Zeichenfolge nicht externalisiert wurde. Das aktualisierte `com.adobe.granite.monitoring.dashboard`-Bundle stellt es wieder her. (NPR-44845)
* Der Text im Dialogfeld Query Builder Debugger-Tool wird jetzt auf der Registerkarte Abfrage erläutern in der Sprache des Benutzers angezeigt. Zuvor blieben mehrere Strings auf Englisch, da sie nicht externalisiert wurden. Das aktualisierte `cq-platform-content` liefert die Übersetzungen. (NPR-44846)
* Der Text auf der Ergebnisseite der Konsistenzprüfung wird jetzt in der Sprache des Benutzers angezeigt. Zuvor erschienen mehrere Strings auf Englisch, weil sie nicht externalisiert wurden. Das aktualisierte `com.adobe.granite.operations.ui.core` liefert die Übersetzungen. (NPR-44847)
* Das Überwachungsdiagramm zeigt jetzt Monat- und Wochen-Beschriftungen in der Sprache des Benutzers an. Zuvor waren die Kennzeichnungen in Englisch hartcodiert, sodass das Diagramm das Gebietsschema der Benutzeroberfläche ignorierte. Das aktualisierte `com.adobe.granite.monitoring.dashboard` externalisiert die Zeichenfolgen, und Übersetzungen werden jetzt angezeigt. (NPR-44848)
* Im Dropdown-Menü „Land/Region“ unter **Sicherheit** > **Benutzer** > **Erstellen** werden Einträge jetzt korrekt sortiert. Zuvor waren die lokalisierten Ländernamen für einige Sprachen in der falschen Reihenfolge. Das aktualisierte `com.adobe.granite.security.content`-Bundle wendet eine gebietsschemasensitive Sortierung an. (NPR-44942)
* QuickInfos im Dialogfeld für die Schaltflächenkomponente werden jetzt in der Benutzersprache angezeigt. Zuvor war der Informationstext für die Schaltflächentext-, Link-, Symbol-, HTML-ID- und `aria-label`-Felder auf Englisch verfügbar, obwohl die Zeichenfolgen im Lokalisierungsdienst vorhanden waren. Das aktualisierte Wörterbuch liefert die Übersetzungen in allen unterstützten Gebietsschemata. (SITES-7579)
* QuickInfos im Eigenschaftenabschnitt der Inhaltsfragmentlisten-Komponente werden jetzt in der Sprache des Benutzers angezeigt. Zuvor blieb der Informationstext für die Felder „Inhaltsfragmentmodell“, „Tags“, „Maximale Anzahl von Elementen“, „Übergeordneter Pfad“, „Sortierreihenfolge“ und „Sortieren nach“ in englischer Sprache. Das aktualisierte Wörterbuch enthält Übersetzungen für alle unterstützten Gebietsschemata. (SITES-14969)
* Die Hilfe-Links für Kernkomponenten im Vorlageneditor führen jetzt zu lokalisierten Dokumentationsseiten. Wenn Sie zuvor im Dialogfeld für die Komponentenkonfiguration auf Hilfe geklickt haben, wurde die englische Seite unabhängig von der Sprache der Benutzeroberfläche geöffnet. Aktualisierte URLs leiten Benutzer jetzt zur Seite für ihr Gebietsschema weiter. (SITES-15058)
* Die QuickInfos im Dialogfeld Inhaltsfragment werden jetzt in der Sprache des Benutzers angezeigt. Zuvor wurde der QuickInfo-Text für die Modi Einzelnes Textelement und Mehrere Elemente sowie für den Pfad des Inhaltsfragments in englischer Sprache angezeigt. Ein aktualisiertes Wörterbuch bietet Übersetzungen für alle Gebietsschemata. (SITES-17333)
* Fehlermeldungen im Komponenten-Editor des Vorlageneditors werden jetzt in der Benutzersprache angezeigt. Zuvor blieben die Nachrichten „Ressource {resource} ist nicht veränderbar“ und „Knoten kann nicht erstellt werden bei“ auf Englisch, wenn Autoren eine Komponentenrichtlinie bearbeitet oder eine neue erstellt hatten. Die aktualisierten Ressourcen enthalten Übersetzungen für alle unterstützten Gebietsschemata. (SITES-17475)
* Auf der Registerkarte Assets im Seiteneditor wird jetzt eine übersetzte Zeichenfolge in der Dropdown-Liste Komponenten auswählen angezeigt, nachdem Sie im Dropdown-Menü Bilder die Option Absätze ausgewählt haben. Zuvor erschien die Zeichenfolge „OTHER“ auf Englisch, da sie in den Lokalisierungsressourcen fehlte. Das aktualisierte Wörterbuch liefert die Übersetzung in allen Gebietsschemata. (SITES-21481)
* QuickInfos im Komponentendialogfeld „Seiteneditor konfigurieren“ zeigen keinen zusätzlichen Zeilenumbruch mehr an. Zuvor waren QuickInfos für Komponenten wie den PDF-Viewer und die Fortschrittsleiste in mehreren Gebietsschemata umschlossen. Die QuickInfos werden jetzt korrekt umgebrochen, und die Worttrennung funktioniert wie erwartet. (SITES-38567)
* Die QuickInfo „Zum Beenden des Texteditors die Esc-Taste drücken“ wird jetzt in der Benutzersprache im Dialogfeld zum Konfigurieren der Textkomponente angezeigt. Zuvor wurde die Zeichenfolge auf Englisch angezeigt, da sie in den Lokalisierungsressourcen fehlte. Die QuickInfo wird jetzt in allen Gebietsschemata übersetzt. (SITES-43186)
* Die Bezeichnung STRUKTUR im Vorlageneditor wird nun in der Benutzersprache angezeigt. Zuvor blieb die Beschriftung auf Englisch, als Autoren eine Vorlage für ein adaptives Formular öffneten, da die Zeichenfolge in den Lokalisierungsressourcen fehlte. Die Bezeichnung wird nun in alle Gebietsschemata übersetzt. (SITES-43599)


#### MSM – Live Copies{#sites-msm-live-copies-6526}

* Das Dialogfeld MSM-Rollout lädt die Live Copy-Liste nach einem Upgrade erneut. Zuvor hatte ein `NullPointerException` in `AsyncOperationServlet.doGet` das Dialogfeld auf einem Zahlenauswahlfeld angehalten, sodass die Autoren keine Zielgebietsschemata auswählen oder den Rollout starten konnten. Ein aktualisiertes `com.adobe.granite.jobs.async` verarbeitet die fehlenden Auftragsdaten und beendet die Anfrage. (SITES-43116)
* Der Rollout von der bearbeitbaren Symbolleiste auf einer Blueprint-Seite funktioniert wieder. Die Symbolleistenaktion ist mit „Eigenschaften von nicht definierten Elementen können nicht gelesen werden (Lesen von „doRollout„)“ fehlgeschlagen, da die `MSM.Rollout` Client-Bibliothek nicht geladen wurde. Die aktualisierte Seite lädt jetzt die Bibliothek, sodass der Rollout-Vorgang beginnt und die Änderungen die Live Copies erreichen. (SITES-46052)

* Die Batch-Deaktivierung einer Blueprint-Seite und ihrer untergeordneten Seiten sendet keine doppelten Rollout-Ereignisse mehr. Wenn Sie ein übergeordnetes Element und dessen untergeordnete Elemente in einer Anfrage deaktiviert haben, gab das Replikationssystem fünf Ereignisse anstelle von drei aus, und jede untergeordnete Seite wurde zweimal ausgerollt. Die Deduplizierung im Rollout-Manager sendet jetzt einen Rollout pro Seite, sodass Live Copies keine redundanten Pakete erhalten. (SITES-44988)


#### Seiteneditor{#sites-pageeditor-6526}

* Der ausgewählte Stil bleibt nach dem Scrollen durch die Liste im Dialogfeld zur Auswahl des Seiteneditor-Stils hervorgehoben. Zuvor wurde ein Stil hervorgehoben, als Sie ihn auswählten, aber die Hervorhebung verschwand, wenn Sie auf die Bildlaufleiste klickten. Diese Regression begann nach SP22, und das Dialogfeld hält nun den ausgewählten Status sichtbar. (SITES-30874)

* Autoren können Seiten im Layout-Modus bearbeiten, wenn übergeordnete und untergeordnete Komponenten unterschiedliche responsive Breakpoints definieren. Die Funktion getResponsiveCssClasses ist zuvor mit einem TypeError für Komponenten fehlgeschlagen, bei denen die cq::responsive-Telefonbreite weggelassen wurde. Die Funktion kehrt jetzt auf verfügbare Werte zurück und wird weiter gerendert. (SITES-46681)
* Benutzerdefinierte Zuschnittverhältnisse werden jetzt im hybriden Inline-Bearbeitungsmodus für Komponenten mit mehreren Bildablagezielen geladen. Zuvor initialisierte der Bildeditor eine generische ipeConfig für alle Ablageziele, sodass der Editor nur die Standardverhältnisse zeigte und die Seitenverhältnisse jedes Ziels ignorierte. Der Editor liest jetzt die Konfiguration für das ausgewählte Ablageziel und der Zuschnitt gilt sowohl in der Inline- als auch in der Vollbildansicht. (SITES-45771)
* Durch Drücken der Rücktaste im Rich-Text-Editor werden dem Text keine zusätzlichen Inline-Stile hinzugefügt. Ein Kunde meldete, dass beim Entfernen eines Zeilenumbruchs nach fett gedrucktem Text style=„font-size: 0.8125rem; background-color: transparent;“ zu dem fett gedruckten Tag hinzugefügt wurde. Beim Testen mit dem neuesten Service Pack konnte das Verhalten nicht reproduziert werden, sodass keine Änderung erforderlich war. (SITES-15883)


<!--
#### Replication{#sites-replication-6526}
-->


#### Rich-Text-Editor{#sites-rte-6526}

* Die Rich-Text-Editor-Symbolleistenschaltflächen funktionieren im responsiven Ansicht- und Layout-Modus. Zuvor wurden die beim Klicken hervorgehobenen Schaltflächen markiert, aber die Auswahl blieb unverändert und es wurde kein Dialogfeld geöffnet. Das aktualisierte Editor-Skript wendet die Formatierung an und stimmt damit mit dem Verhalten im Bearbeitungsmodus überein. (SITES-44233)
* Autoren können Währungs- und Markensymbole zu Textkomponenten hinzufügen, ohne sie zu verlieren. Das Plug-in Sonderzeichen hat die Symbole eingefügt, sie werden jedoch sowohl im Editor als auch in der veröffentlichten Ausgabe als Leerzeichen angezeigt. Die korrigierte Handhabung rendert jedes Symbol wie eingegeben. (SITES-46532)
* Das Vollbildsymbol in der Rich-Text-Editor-Symbolleiste erweitert den Editor erneut. Zuvor führte das Klicken auf das Symbol in der Kerntextkomponente zu keiner Änderung, und der Editor blieb auf seiner Inline-Größe. Autoren haben jetzt einen fokussierten Arbeitsbereich für langfristige Inhalte sowohl in der Inline- als auch in der Dialogfeldbearbeitung. (SITES-46396)


#### Site-Admin-Benutzeroberfläche{#sites-admin-ui-6526}

Durch das Zurücksetzen eines Assets auf eine frühere Version wird jetzt die Miniaturansicht seiner Karte aktualisiert. Eine URL-Kodierungsänderung in der Zeitleisten-Client-Bibliothek führte zu einer Pfadabweichung, sodass die Kartensuche fehlgeschlagen ist und die Miniaturansicht veraltet blieb. Durch Abgleichen der kodierten und der Rohpfade wird die Aktualisierung wiederhergestellt. (SITES-46590)

<!--
#### Universal editor {#sites-universal-editor-6526}
-->

#### Workflow-Erweiterungen {#sites-workflow-extensions-6526}

Payload anzeigen öffnet jetzt den Paket-Editor der Touch-optimierten Benutzeroberfläche für Workflows, mit denen „Veröffentlichung verwalten“ für mehrere Seiten gestartet wird. Zuvor wurde durch die Aktion der veraltete Paket-Editor der klassischen Benutzeroberfläche geöffnet, obwohl Autoren den Workflow in der Touch-optimierten Benutzeroberfläche gestartet hatten. Autoren überprüfen jetzt die Payload, ohne die Touch-optimierte Benutzeroberfläche zu verlassen. (SITES-40928)


### [!DNL Assets] {#assets-6526}

* Verbesserung: AEM Assets 6.5 unterstützt die Einhaltung der Coalition for Content Provenance and Authenticity (C2PA)-Richtlinien für generative KI-Inhalte. Der Workflow zum Aktualisieren von Assets erkennt C2PA-Anmeldeinformationen, extrahiert die Metadaten und signiert Ausgabedarstellungen, die der Workflow neu generiert. Die Signatur wird in jeder AEM-Instanz lokal ausgeführt, sodass Kunden keine dedizierte Signaturinfrastruktur benötigen. (ASSETS-75868)

* Dokumentationsverbesserung: In der neuen öffentlichen Dokumentation wird erläutert, wie Sie die Asset-Verarbeitungs-Pipeline anpassen und dabei die C2PA-Konformität beibehalten können. In der Dokumentation wird beschrieben, wie Sie den Schritt „C2PA-Anmeldeinformationen erkennen“ vor den Schritten der Ausgabedarstellung positionieren und wie das Signieren lokal in den einzelnen AEM-Instanzen ausgeführt wird. In der Dokumentation wird auch die Einschränkung für dedizierte oder kundeneigene Signaturinfrastrukturen angegeben. (ASSETS-76100)
* Das Dropdown-Menü Hilfe in der Shell-Kopfzeile bleibt jetzt geöffnet, wenn Sie den Mauszeiger über die Links in AEM 6.5 SP26-Umgebungen bewegen. Zuvor wurde die Dropdown-Liste geschlossen, wenn der Mauszeiger auf die Liste zugegriffen hat, sodass Autoren nicht auf Dokumentations-, Community- oder Support-Links klicken konnten. Das aktualisierte `com.adobe.granite.ui.content`-Bundle verschiebt die Fokusprüfung, sodass das Menü nur geschlossen wird, wenn der Fokus wirklich beendet wird. (ASSETS-65676)

<!--
#### [!DNL Dynamic Media]{#assets-dm-6526}
-->

### [!DNL Forms]{#forms-6526}

* Neue Funktion: Unterstützung für Barrierefreiheits-Tags in Listen in Rich-Text. Zuvor wurden Listen-Tags nur dann in der Tag-Struktur für Barrierefreiheit angezeigt, wenn die Vorlage einer bestimmten Struktur folgte. Die Anfrage wurde als Duplikat eines zugehörigen Tickets geschlossen, das die Funktion bereitstellt. (LC-3923202)


<!--
#### Forms JEE {#forms-jee-6526}

#### Forms Designer {#forms-designer-6526}
-->


### Fundament {#foundation-6526}

* Die Zeichenfolge „Land/Region“ im Benutzerdialogfeld **Sicherheit** > **Benutzer** > **Erstellen** wird jetzt in der Benutzersprache angezeigt. Zuvor blieb das Label für lokalisierte Schnittstellen in englischer Sprache. Das aktualisierte `com.adobe.granite.security.content` liefert die Übersetzungen. (NPR-43882)
* Das Dropdown-Menü Hilfe in der Shell-Kopfzeile bleibt jetzt geöffnet, wenn Sie den Mauszeiger über die Links in AEM 6.5 SP26-Umgebungen bewegen. Zuvor wurde die Dropdown-Liste geschlossen, wenn der Mauszeiger auf die Liste zugegriffen hat, sodass Autoren nicht auf Dokumentations-, Community- oder Support-Links klicken konnten. Das aktualisierte `com.adobe.granite.ui.content`-Bundle verschiebt die Fokusprüfung, sodass das Menü nur geschlossen wird, wenn der Fokus wirklich beendet wird. (NPR-44686)
* Verbesserung: Die `HtmlLibraryManagerImpl` Abfrage enthält jetzt ein Tag des Knotentyps, sodass die Abfrage immer den erwarteten Index verwendet. Der Service protokolliert auch einen FEHLER, wenn er keine Client-Bibliotheken findet, was Admins auf das Problem hinweist. Durch das Update wird die Version des `com.adobe.granite.clientlibs`-Pakets im Service Pack angestoßen. (NPR-44698)


<!--
#### Apache Felix {#foundation-apachefelix-6526}
-->


#### Authentifizierung {#foundation-authentication-6526}

Speichern und schließen im Benutzer-Editor kehrt jetzt zu den Suchergebnissen der aktuellen Suche zurück. Nachdem Autoren in Omnisearch nach einem zweiten Benutzer gesucht, Eigenschaften bearbeitet und auf Speichern und schließen geklickt haben, wurden stattdessen die Eigenschaften des ersten Benutzers geöffnet. Das aktualisierte Skript „UserProperties.js“ stellt die erwartete Navigation wieder her. (NPR-44774)

<!--
#### Campaign{#foundation-campaign-6526}

#### Cloud Services{#foundation-cloudservices-6526}

#### Communities {#foundation-communities-6526}

#### Content distribution{#foundation-content-distribution-6526}

#### Adobe CRX {#foundation-crx-6526}
-->


#### Granite{#foundation-granite-6526}

* Der Platzhalter „Inhaltsfragmentmodell“ im Assets Omnisearch-Filter wird jetzt vollständig angezeigt. Zuvor war der Text abgeschnitten, nachdem Sie zu Assets gegangen sind, auf das Filter- oder Suchsymbol geklickt und das Feld Inhaltsfragmentmodell erweitert haben. Aktualisierter Stil gibt dem Platzhalter ausreichend Platz. (GRANITE-54387)
* Das Dropdown-Menü Hilfe in der Shell-Kopfzeile bleibt nun geöffnet, wenn Sie den Mauszeiger über die entsprechenden Links bewegen. Zuvor wurde die Dropdown-Liste geschlossen, sobald der Mauszeiger auf die Liste der Dokumentations-, Community- und Support-Links zeigte, wodurch die Links mit der Maus unerreichbar wurden. Der Fokus-Handler verschiebt seine Prüfung jetzt auf den nächsten Animationsrahmen, sodass das Bewegen des Mauszeigers nicht mehr als Fokus aus dem Menü gezählt wird. (GRANITE-70978)

<!--
#### Jetty{#foundation-jetty-6526}
-->

#### Integrationen starten{#foundation-launch-integrations-6526}

Verbesserung: Die Adobe Analytics-Integration mit Adobe Experience Manager Launch verwendet die Analytics 2.0-API. Die Analytics 1.4-API erreicht am 31. August 2026 das Ende der Lebensdauer. Die Migration sorgt dafür, dass die Reporting- und Launch-Integrationen nach diesem Datum funktionieren. (CQ-4365074, CQ-4365080)

<!--
#### Localization{#foundation-localization-6526}

#### Oak {#foundation-oak-6526}
-->

#### Plattform{#foundation-platform-6526}

* Der Hilfe-Link in der Fußzeile der AEM-Anmeldeseite öffnet jetzt eine Arbeitsseite. Zuvor verwies der Link auf eine marketing.adobe.com URL, die nicht mehr vorhanden ist. Die Fußzeilenkonfiguration verwendet jetzt die [Adobe Experience Manager-Dokumentations](https://experienceleague.adobe.com/de/docs/experience-manager)-URL. (NPR-44388)
* Verbesserung: Eine Kundenanfrage, die nach der Microsoft Graph API als Alternative zum SMTP gefragt wird, wenn AEM E-Mails sendet. Das Ticket wurde als Duplikat aufgelöst, da ein anderes Ticket bereits den Graph-API-Fluss implementiert. SMTP mit OAuth 2.0 bleibt für Kunden verfügbar, die von der SMTP-Standardauthentifizierung abrücken müssen. (GRANITE-57478)

* Die Zeichenfolgen im Dialogfeld Gültige Berechtigungen sind jetzt im Browser **Tools** > **Allgemein** > **Konfiguration** korrekt ausgerichtet. Zuvor wurde eine Zeichenfolge offline angezeigt, nachdem Sie einen Ordner ausgewählt, auf „Eigenschaften“ geklickt und auf „Gültige Berechtigungen“ geklickt hatten. Aktualisierte Layout-Regeln stellen die Ausrichtung wieder her. (CQ-4359166)


#### Projekte {#foundation-projects-6526}

Die Zeichenfolge „Stammverzeichnis auswählen“ im Dialogfeld i18n-Wörterbuch auswählen wird jetzt vollständig angezeigt. Zuvor war der Text in mehreren lokalisierten Schnittstellen abgeschnitten, nachdem Sie ein Übersetzungsprojekt erstellt und ein i18n-Wörterbuch hinzugefügt haben. Das aktualisierte `cq-projects-translation-content`-Paket lässt der Zeichenfolge genügend Platz. (CQ-4355405)

<!--
#### Security{#foundation-security-6526}

#### Sling{#foundation-sling-6526}

#### SPA editor {#foundation-spa-editor-6526}
-->


#### Übersetzung{#foundation-translation-6526}

Die Stiloptionen für die Listenkomponente werden jetzt in der Benutzersprache angezeigt. Zuvor blieben Zeichenfolgen wie Block und Raster im Menü Stile auf Englisch, nachdem Autoren die Listenkomponente zu einem Experience Fragment hinzugefügt hatten. Die aktualisierten Ressourcen enthalten die Übersetzungen, einschließlich der Schnittstellen für Koreanisch, vereinfachtes Chinesisch und Traditionelles Chinesisch. (CQ-4349666)

<!--
#### User interface{#foundation-ui-6526}

#### WCM{#foundation-wcm-6526}
-->

#### Workflow{#foundation-workflow-6526}

Verbesserung: Der Seiteneditor der Touch-optimierten Benutzeroberfläche rendert jetzt die Inhaltsstruktur und unterstützt die Bearbeitung von Ressourcendefinitionskomponenten auf Workflow-Paketseiten. Zuvor wurde auf Seiten unter `/etc/workflow/packages/`, die **Veröffentlichung verwalten** > **Später** erstellen, im linken Bereich keine Inhaltsstruktur angezeigt, und Autoren konnten die Komponenten zur Ressourcendefinition nicht bearbeiten. Genehmigende Personen überprüfen jetzt Seiten und Assets innerhalb einer Workflow-Payload in der Touch-optimierten Benutzeroberfläche und passen so das Verhalten der klassischen Benutzeroberfläche an. (GRANITE-65620)

## Installieren von [!DNL Experience Manager] 6.5.26.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.26.0 erfordert [!DNL Experience Manager] 6.5. Detaillierte Anweisungen finden [&#x200B; in &#x200B;](/help/sites-deploying/upgrade.md)Upgrade-Dokumentation“. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.26.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.26.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe empfiehlt, das Paket [!DNL Experience Manager] 6.5.26.0 nicht zu entfernen oder zu deinstallieren. Erstellen Sie vor der Installation des Pakets eine Sicherungskopie des `crx-repository`, um das Paket bei Bedarf zurückzusetzen. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Installieren des Service Packs für [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.26.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie den Paket-Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Package Manager-Benutzeroberfläche wird manchmal während der Installation des Service Packs geschlossen. Adobe empfiehlt, abzuwarten, bis keine Fehlerprotokolle mehr geändert werden, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle zur Deinstallation des Aktualisierungspakets, bevor Sie bestätigen, dass die Installation erfolgreich war. Dieses Problem tritt im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.26.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API vom Paket-Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.26.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Die Plattformen, die für die Verwendung mit dieser Version zertifiziert sind, finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.26.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Pakete sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Paket `org.apache.jackrabbit.oak-core` hat die Version 1.22.20 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE. CHECK WITH SAMEER DHAWAN -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Service Pack-Installation für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/deploying/deploy), dient nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da die Adaptive Forms-Funktionalität eine entsprechende Lizenzierung erfordert.

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie basierend auf den verwendeten Funktionen die erforderliche Indexdefinition hinzufügen.

Wenn dieses Paket nicht installiert wird, führt dies zu langsamen oder fehlgeschlagenen GraphQL-Abfragen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.26.0 ist im [Maven Central-Repository](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.26/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE FROM MADHULIKA SINGH -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.26</version>
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

Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Mitteilung über das Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Erweiterungen für die veralteten Endpunkte.

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
     Neue Ordner für `cache` und `diff-cache` werden automatisch erstellt und es tritt keine Ausnahme mehr im Zusammenhang mit der `mvstore` im `error.log` auf.

* Aktualisieren Sie Ihre GraphQL-Abfragen, die einen benutzerdefinierten API-Namen für Ihr Inhaltsmodell verwendet haben, sodass stattdessen der Standardname des Inhaltsmodells verwendet wird.

* Eine GraphQL-Abfrage verwendet den `damAssetLucene`-Index anstelle des `fragments`. Diese Aktion führt zu GraphQL-Abfragen, deren Ausführung fehlschlägt oder lange dauert.

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

  Nach diesen Schritten führen die GraphQL-Abfragen eine höhere Geschwindigkeit aus.

* Beim Versuch, Inhaltsfragmente, Sites oder Seiten zu verschieben, zu löschen oder zu veröffentlichen, tritt ein Problem auf, wenn Inhaltsfragmentreferenzen abgerufen werden. Die Hintergrundabfrage schlägt fehl; die Funktion funktioniert nicht.
Um einen korrekten Betrieb zu gewährleisten, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten `/oak:index/damAssetLucene` hinzufügen (eine Neuindizierung ist nicht erforderlich):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5.0 bis 6.5.4 auf das neueste Service Pack für Java™ 11 aktualisieren, sehen Sie `RRD4JReporter`-Ausnahmen in der Datei `error.log`. Um die Ausnahmen zu stoppen, starten Sie Ihre Instanz von [!DNL Experience Manager] neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzer können einen Ordner in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Die folgenden Fehler und Warnmeldungen werden während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt:
  * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/source „Adobe Target Classic“.
  * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
  * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
  * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter `granite/operations/maintenance` gefunden.
  * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
  * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Ab AEM 6.5.15 weist die vom Paket `org.apache.servicemix.bundles.rhino` bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten auf. Skripte, die den Strict-Modus (`use strict;`) verwenden, müssen ihre korrekten Variablen deklarieren. Andernfalls werden sie nicht ausgeführt und geben am Ende einen Laufzeitfehler zurück.

* Wenn Sie Tagging-bezogene Standardinhalte über ein offizielles Aktualisierungspaket installieren, wird die Languages-Eigenschaft des `/content/cq:tags`-Knotens auf den Standardwert zurückgesetzt. Diese Aktion gilt für Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, Patches usw. Daher ist es notwendig, es vor der Installation zu den Eigenschaften hinzuzufügen.

### Bekanntes Problem bei AEM Sites {#known-issues-aem-sites-6526}

* **Bekanntes Problem mit einem Hotfix, der für AEM Foundation verfügbar ist**

  Nach dem Upgrade von einem früheren Service Pack auf Experience Manager 6.5.26.0 kann die Sortierung der CRXDE Lite-Bundle verhindern, dass Experience Manager das beabsichtigte Bundle auswählt. Um die Versionsreihenfolge zu korrigieren, installieren Sie Service Pack 26, und laden Sie dann das Hotfix [`CRXDE Lite hotfix GRANITE-76725`](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq660%2Fhotfixes%2Fgranite-76725%2Fcq-6.5.26-hotfix-GRANITE-76725-1.0.zip) von Software Distribution herunter. Der Hotfix ist ein reines Versionsupdate. Es enthält keinen Code oder funktionale Änderungen. (GRANITE-76725)

* Die Vorschau von Inhaltsfragmenten schlägt aufgrund des DoS-Schutzes bei einer umfangreichen Fragmentstruktur fehl. Siehe den [KB-Artikel zu den standardmäßigen GraphQL Query Executor-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6526}

* Wenn ein Formular mit einem Feld **Dateianhang**, das `bindref` verwendet, an einen AEM-Workflow mit dem Schritt **Aufgabe zuweisen** gesendet wird, werden die Anlagen nicht angezeigt. Daher werden sie nicht angezeigt, wenn die Aufgabe aus dem Posteingang geöffnet wird. Die Dateien werden korrekt im Repository gespeichert, aber in der Benutzeroberfläche des Schritts „Aufgabe zuweisen“ können die Anlagen nicht angezeigt werden. (FORMS-23722)

* Wenn eine digital signierte PDF an eine Aufgabe in AEM Forms JEE Workspace angehängt wird, bleibt der Upload im Upload-Status hängen oder schlägt mit der Fehlermeldung „Ungültige Datei“ fehl. Daher können der Aufgabe keine größeren, signierten PDF-Anhänge hinzugefügt werden. Dieses Problem wurde in einer späteren Version behoben. Wenden Sie sich für einen Hotfix zur Version an den Adobe-Support. (FORMS-28517)

#### Bekannte Probleme mit verfügbaren Hotfixes {#aem-forms-issues-with-hotfixes}

Für die folgenden Probleme ist ein Hotfix zum Herunterladen und Installieren verfügbar. Sie können [den Hotfix herunterladen und installieren](/help/release-notes/aem-forms-hotfix.md), um diese Probleme zu beheben:

* Wenn Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) doppelte Einträge von Geode-Jars `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` im `<AEM_Forms_Installation>/lib/caching/lib` finden, führen Sie die folgenden Schritte aus, um das Problem zu beheben (FORMS-14926):

  1. Stoppen der Locators, falls sie noch ausgeführt werden.
  1. Stoppen des AEM-Servers.
  1. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
  1. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
  1. Öffnen Sie die Eingabeaufforderung im Administratormodus.
  1. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

Die folgenden ZIP-Dateien enthalten die Textdokumente, in denen die in dieser Version [!DNL Experience Manager] 6.5 Service Pack enthaltenen OSGi-Bundles und Inhaltspakete aufgelistet sind:

* [Liste der in Experience Manager 6.5.26.0](/help/release-notes/assets/65260-bundles.zip) enthaltenen OSGi-Bundles
<!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.26.0](/help/release-notes/assets/65260-packages.zip) enthaltenen Inhaltspakete
<!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kundinnen und Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produkt-Download unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience#).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/de/subscription/priority-product-update.html)




