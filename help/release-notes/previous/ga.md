---
title: Allgemeine Versionshinweise zu  [!DNL Adobe Experience Manager]  6.5
description: Informationen zu [!DNL Adobe Experience Manager] 6.5 mit Versionshinweisen, Angaben zu neuen Funktionen und zur Installation sowie ausführlichen Auflistungen von Änderungen.
exl-id: b3d4a527-44ca-4eb6-b393-f3e8117cf1a6
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '4675'
ht-degree: 99%

---

# Allgemeine Versionshinweise zu [!DNL Adobe Experience Manager] 6.5{#general-release-notes-for-adobe-experience-manager}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 |
| Typ | Hauptversion |
| Datum der allgemeinen Verfügbarkeit | 8. April 2019 |
| Empfohlene Updates | Siehe [neueste Updates für AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de). |

### Wissenswertes {#trivia}

Der Veröffentlichungszyklus für diese Version von [!DNL Adobe Experience Manager] begann am 4. April 2018, durchlief 23 Iterationen zur Qualitätssicherung und Fehlerbehebung und endete am 28. März 2019. Insgesamt wurden in dieser Version 1345 kundenbezogene Probleme behandelt, einschließlich Verbesserungen und neuer Funktionen.

[!DNL Adobe Experience Manager] 6.5 ist seit dem 8. April 2019 allgemein verfügbar.

![AEM 6.5-Anmeldebildschirm](/help/assets/assets/aem65-login-v4.png)

## Neue Funktionen {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 ist eine Upgrade-Version für die Code-Basis von 6.4. [!DNL Adobe Experience Manager] Die Software bietet neue und erweiterte Funktionen, wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen zur Steigerung der Stabilität des Produkts. Darüber hinaus enthält [!DNL Adobe Experience Manager] 6.4 Service Pack-Versionen bis SP4.

Die folgende Liste bietet eine Übersicht und die nachfolgenden Seiten enthalten die vollständigen Details.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.10.2.

Quickstart verwendet Eclipse Jetty 9.4.15 als Servlet-Engine.

#### Java™-Unterstützung  {#java-support}

* Neue Unterstützung für Java™ 11 und das bereits unterstützte Java™ 8.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Wartungs-Updates für Java™ 11 und Java™ 8 werden Kunden von Adobe zur Nutzung in AEM-bezogenen Projekten bereitgestellt, sofern diese nicht bei Oracle öffentlich zugänglich sind.

#### Java™-Entwicklung {#java-development}

* Es gibt jetzt [zwei Versionen des UberJar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), eine empfohlene Version mit öffentlichen Schnittstellen, die nicht als veraltet gekennzeichnet sind, sowie eine Version mit Schnittstellen, die als veraltet gekennzeichnet sind.

#### Benutzeroberfläche {#user-interface}

An der Benutzeroberfläche wurden verschiedene Verbesserungen vorgenommen, um sie produktiver und benutzerfreundlicher zu gestalten.

* Es gibt eine neue Benutzeroberfläche zur Verwaltung von Berechtigungen von Benutzern und Gruppen.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden nur geladen, wenn der Anwender zu scrollen beginnt. In der Listen- und Kartenansicht gilt dies bereits seit Version 6.0 (verbessert in Version 6.4).
* Spaltenansichten enthalten nun ggf. den Workflowstatus für Seiten/Assets.
* Die Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) ist eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Ein Warndialogfeld wird angezeigt, wenn die Aktion kein Upgrade für die Verarbeitung von Massenaktionen erhalten hat.

>[!CAUTION]
>
>Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. In AEM 6.5 ist die klassische Benutzeroberfläche integriert und Kunden und Kundinnen, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Die klassische Benutzeroberfläche ist zwar veraltet, wird aber weiterhin vollständig unterstützt. [Weitere Informationen](/help/sites-deploying/ui-recommendations.md).

#### Suche und Indizierung {#indexing-and-search}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise wird bei der Asset-Suche in der Filterleiste die geschätzte Anzahl der Ergebnisse angezeigt.
* QueryBuilder wurde erweitert und liefert nun Ergebnisse mit dynamischen Facetten.

#### Aktualisierung {#upgrade}

* Kunden mit AEM 6.2, 6.3 und 6.4 können direkt auf AEM 6.5 aktualisieren. Kunden, die 5.x oder 6.0/6.1 verwenden und ein direktes Upgrade durchführen möchten, müssen zunächst auf 6.4 aktualisieren. Aktualisieren Sie dann auf 6.5 oder aktualisieren Sie durch die Übertragung des Inhalts zwischen den Instanzen direkt auf AEM 6.5.
* Das Aktualisierungsverfahren bleibt in 6.5 größtenteils unverändert.
* Wir unterstützen auch weiterhin die in 6.4 eingeführten Funktionen „Abwärtskompatibilität“, „Bewertung der Aktualisierungskomplexität“ und „Nachhaltige Aktualisierungen“. Für diese Bereiche wurden nach Bedarf versionsspezifische Aktualisierungen durchgeführt.
* Die Paketierung für Musterdetektoren wurde vereinfacht. Es gibt ein Paket, das Upgrades auf 6.5 für die verfügbaren Quellversionen prüft.
* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

#### Projekte und Workflows {#projects-and-workflows}

* Der in Version 6.4 eingeführte neue Workflow-Modell-Editor wurde verbessert. Neben einer größeren Anzahl von Vorgängen wie Kopieren und Veröffentlichen werden nun Variablen in Workflowschritten unterstützt. Außerdem wurden `OR`- und `AND`-Teilungen optimiert.

#### Repository {#repository}

* Die Foundation-Komponente von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content Repository Apache Jackrabbit Oak 1.10.2.
* Einen Überblick über behobene Probleme finden Sie unter [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR finden Sie unter [Häufig gestellte Fragen zur Migration zu Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

#### OSGI {#osgi}

* Es wurden die Hilfsprogrammbibliotheken OSGi Promises und Converter hinzugefügt.

#### Sicherheit {#security}

* Kennwörter von Admins laufen jetzt nach einer gewissen Zeit ab.

#### Webserver {#web-server}

* Die Quickstart-Verteilung nutzt Eclipse Jetty 9.4.15 als Servlet-Engine (AEM 6.4, bereitgestellt mit 9.3.22).

### [!DNL Experience Manager] Sites {#experience-manager-sites}

#### Verwaltete Single Page Applications (SPAs) {#managed-single-page-apps}

Der Seiten-Editor ermöglicht nun kontextbezogene Inhaltsbearbeitungen und Erstell-/Layoutvorgänge in Client-seitig gerenderter Erlebnissen (auch als [SPA-Editor](/help/sites-developing/spa-architecture.md) bekannt). Vorhandene Single Page Applications, die mit den JavaScript-Frameworks React oder Angular erstellt wurden, können mit dem AEM SJ-SDK erweitert werden, damit sie für Anwendende bearbeitbar sind.

Die SPA-Unterstützung war zuerst im Lieferumfang von AEM 6.4 SP2 enthalten. Mit AEM 6.5 erhält sie folgende neue Funktionen:

* Verwenden des Vorlageneditors, um die in AEM bearbeitbaren Teile der SPA zu bearbeiten und zu konfigurieren
* Erstellen von landesbezogenen bzw. Franchise- oder White-Label-SPA-Erlebnissen durch Multi-Site-Management

#### Headless-Content-Management {#headless-content-management}

Mit AEM können Inhalte in verschiedenen Formaten und aus verschiedenen Ebenen des Stapels bereitgestellt werden. Einige gibt es bereits seit 2008, mit dem [Sling GET-](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) und [-POST-Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html). Content Services ([Sling Model Exporter](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html?lang=de)) wurde in AEM 6.3 eingeführt und ist die Methode, die vom AEM SJ-SDK verwendet wird, um SAPs einzubinden. Die [HTTP-API für Assets](/help/assets/mac-api-assets.md) ist eine CRUD-API, die für AEM 6.5 erweitert wurde.

Neue HTTP-API-Funktionen:

* Es wurde [Unterstützung von Inhaltsfragmenten in der HTTP-API für Assets](/help/assets/assets-api-content-fragments.md) zum Erstellen, Aktualisieren, Lesen und Löschen von Fragmenten hinzugefügt.
* Offenlegung von Inhaltsfragmentlisten über Content Services mit der [Kernkomponenten-Inhaltsfragmentliste](https://www.aemcomponents.dev)
* [Kernkomponentenbibliothek](https://www.aemcomponents.dev), die für jede Komponente die standardmäßige Content Services-JSON-Ausgabe anzeigt

#### Screens-Add-on {#screens-add-on}

Sie können Erlebnisse effizient entwickeln, bereitstellen und optimieren, und zwar auf allen digitalen Displays, ob interaktiver Kiosk oder digitale Beschilderung (Digital Signage).

* Vereinheitlichung von Erlebnissen und Inhalten für Digital- und In-Store-Projekte mit verbesserter Wiederverwendung von Inhalten
* Optimierte Authoring- und Genehmigung-/Publishing-Workflows mit Unterstützung für Launches
* Bearbeiten und Bereitstellen vielfältiger interaktiver Erlebnisse mit dem SPA-Editor
* Mit Launches können Sie zukünftige Inhaltsänderungen für Signage-Content planen.
* Es sind getaktete Wiedergaben in einem Sequenzkanal möglich.
* Automatisches Erstellen von Projektstrukturen anhand einer Quelldatei, z. B. einer Excel-Tabelle
* Erweiterte Medienplayer-Unterstützung für zuverlässigen Online- und Offlinebetrieb (Smart Sync), skalierbar sogar für größte Signage-Netzwerke
* Personalisieren Sie mithilfe dynamischer Platzhalter den durch Daten ausgelösten Inhalt nach Standort oder Konfiguration.
* Einheitliche Erkenntnisse durch die Integration von Adobe Analytics in den AEM Screens Player

Weitere Informationen zu Änderungen in AEM Screens finden Sie in den Versionshinweisen des [AEM Screens-Benutzerhandbuchs](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de).

#### Komponenten- und Vorlagenentwicklung {#component-amp-template-development}

* Maven-Projekt-Archetyp 18+ für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/adobe/aem-project-archetype/releases).
* Maven-Projekt-Archetyp 1.0.6+ für Einzelseitenanwendungen für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTL Version 1.4, siehe [Versionshinweise zu GitHub](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * „in“-Operator für Zeichenfolgen, Arrays und Objekte:

     ```html
     ${'a' in 'abc'}
     ${100 in myArray}
     ${'a' in myObject}
     ```

   * Variablendeklarationen mit data-sly-set:
     `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * Listen- und Wiederholungsparameter: begin, step, end:
     `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Kennungen für data-sly-unwrap:

     ```html
     <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
     text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
     </div>
     ```

   * Unterstützung negativer Zahlen

* Kernkomponenten 2.3.2+, siehe [Versionshinweise zu Github](https://github.com/adobe/aem-core-wcm-components/releases).
* Rastersystem für Layout-Container, siehe [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Client-Bibliotheken-Manager: Google Closure Compiler als Standard festgelegt, zur Minimierung von JavaScript-Client-Bibliotheken (alter Standard: Yahoo YUI), und Google Closure Compiler auf Version v20190121 aktualisiert
* Vorlagen-Editor und Richtlinien:

   * Erstellungs- und Bearbeitungsvorlagen für Single-Page-Apps, die das JS-SDK verwenden (auch als SPA-Editor bezeichnet)

* Referenz-Website We.Retail 4.0, siehe [Versionshinweise von GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Informationen zum Toolkit zum Aktualisieren vorhandener Websites, um die neuesten Editor-Funktionen nutzen zu können, finden Sie unter [Github-Repository](https://github.com/adobe/aem-modernize-tools).

>[!CAUTION]
>
>AEM umfasst Version 1.12.4 der jQuery-Bibliothek, um für größtmögliche Kompatibilität mit vorhandenem benutzerdefinierten Code zu sorgen. Adobe hat Änderungen vorgenommen, um bekannte Sicherheitsprobleme zu beheben.

#### Site-Administration {#site-administration}

* Die Leiste [Referenz](/help/sites-authoring/author-environment-tools.md#references) enthält einen neuen Abschnitt, in dem interne Links aufgelistet werden, die auf die ausgewählte Seite verweisen. Dies ist nützlich, wenn Sie planen, eine Seite offline zu schalten oder zu löschen. So können Sie sehen, welche Seiten angepasst werden müssen, bevor sie offline geschaltet werden.
* Die [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) enthält eine neue Workflow-Spalte, die den Status anzeigt, wenn sich die Seite in einem Workflow befindet.
* In den [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) können Sie nun nach vorhandenen Assets suchen, wenn Sie der Seite eine Miniaturansicht zuweisen (Registerkarte „Miniatur“).

#### Seiteneditor {#page-editor}

* Der Seiten-Editor ermöglicht kontextbezogenes Bearbeiten und Erstellen von Single-Page-Apps-Erlebnissen mit Client-seitigen React- und Angular-Komponenten, die das JS-SDK nutzen (auch als SPA-Editor bezeichnet).
* Der Strukturvorlagenmodus wird nur angezeigt, wenn auf der Seite eine Strukturvorlagenseite konfiguriert ist.

#### Inhaltsfragmente und Editor {#content-fragments-amp-editor}

* Mit der neuen Leiste [Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#viewing-editing-deleting-annotations) im Inhaltsfragmente-Editor können Sie allgemeine Kommentare erstellen und Kommentare innerhalb des Texts anzeigen (erscheinen ebenfalls in der Leiste „Timeline“).
* Es ist nun möglich, den standardmäßigen Inhaltstyp eines mehrzeiligen Textelements in einem [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md) auf einfachen Text, Rich-Text oder Markdown festzulegen.
* Hinzufügen von [Kommentaren/Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment) durch Auswahl von Text in RTE (Vollbildansicht)
* [Versionen](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) eines Inhaltsfragments über die Referenzleiste nebeneinander vergleichen
* Der heruntergeladene Bericht eines Assets zeigt nun die entsprechenden Inhaltsfragmente an.
* Hinzufügen von [Unterstützung von Inhaltsfragmenten zur HTTP-API von Assets](/help/assets/assets-api-content-fragments.md) über /api.json. Es sind APIs zum Erstellen, Aktualisieren, Lesen und Löschen von Inhaltsfragmenten vorhanden.

#### Experience Fragments  {#experience-fragments}

* Die Indizierung von [Experience Fragments](/help/sites-authoring/experience-fragments.md) wurde verbessert, sodass ihr Inhalt bei der Suche nach Seiten, auf denen sie verwendet werden, gefunden wird.
* Mit der Option [In Ziel exportieren](/help/sites-administering/experience-fragments-target.md) können Sie nun das Experience Fragment als JSON (Standard ist HTML) oder beides senden.

#### Übersetzung {#translation}

* Übersetzungsprojekte lassen sich durch Projekt-Master einfacher erstellen.
* Übersetzungsprojekte können einfacher ausgeführt werden, indem Sie für Übersetzungsaufträge standardmäßig den Status auf „Genehmigt“ festlegen.
* Sie können zulassen, dass übersetzte Seiten mit Änderungen aus dem Translation Memory von Drittanbietern aktualisiert werden.
* Sie können zulassen, dass Übersetzungsaufträge in das JSON-Format exportiert werden.
* Die Integration mit Microsoft® Translation kann zur Verwendung der V3-API aktualisiert werden.

#### Multi-Site-Management (MSM) {#multi-site-management-msm}

* Bei Rolloutkonfigurationen mit PushOnModify werden Seitenverschiebevorgänge besser verarbeitet, um einen inkonsistenten Zustand zu vermeiden..
* Durch Erstellen einer Seite in der Live Copy-Struktur wird standardmäßig eine eigenständige Seite generiert.
* Sie können MSM-Funktionen in Single-Page-Apps nutzen, die das JS-SDK verwenden (auch als SPA-Editor bezeichnet).

#### Launches {#launches}

* Neuer Prüfung- und Genehmigung-Workflow für Launches und Möglichkeit, nur genehmigte Launch-Seiten zu bewerben
* Die [Option in der Benutzeroberfläche zum Löschen des Launches direkt nach dem Promotion-Schritt](/help/sites-authoring/launches-promoting.md#promoting-launch-pages) wurde hinzugefügt.

#### Content-Targeting und -Simulation {#content-targeting-simulation}

* Die ContextHub-Datenebene und die Client-seitige JavaScript-Regel-Engine wurden so aktualisiert, dass standardmäßig jQuery 3 verwendet wird.

#### AEM und Adobe Target {#aem-amp-adobe-target}

>[!CAUTION]
>
>Aktuell:
>
>* Nur `at.js 1.x` wird unterstützt, wenn Sie Adobe Target als Targeting-Engine in der Aktivitätskonsole von AEM verwenden.
>
>* Sowohl `at.js. 1.x` ala auch `at.js 2.x` werden unterstützt, wenn Sie den Export von Experience Fragments nach Target verwenden und Aktivitäten in der Konsole von Target ausführen.

* Zur Adobe Target-Integration wird nun die Target Standard-API verwendet. Frühere AEM-Versionen nutzen die Target Classic-HTTP-API, die nun als veraltet gekennzeichnet ist.
* Adobe Target `mbox.js` Version 6.3 ist enthalten. Adobe empfiehlt ausdrücklich, die Implementierung auf `at.js` Version 1.x umzustellen.
* `at.js` Version 1.5.0 ist jetzt enthalten. Adobe empfiehlt die Verwendung von [Adobe Experience Platform Launch](https://business.adobe.com/de/products/experience-platform/launch.html), um `at.js` v1.x in der Website bereitzustellen.

#### AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` Version H.27.5 ist enthalten. Adobe empfiehlt, die Implementierung auf `AppMeasurement.js` umzustellen.
* `AppMeasurement.js` v1.8.0 ist enthalten. Adobe empfiehlt die Verwendung von [Adobe Experience Platform Launch](https://business.adobe.com/de/products/experience-platform/launch.html), um AppMeasurement.js in der Website bereitzustellen.

#### AEM and Commerce {#aem-commerce}

Verbesserungen am Commerce Integration Framework befinden sich seit AEM 6.4. in einem schnelleren Veröffentlichungszyklus. [Weitere Informationen finden Sie hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/magento.html?lang=de).

#### Communities-Add-on {#communities-add-on}

Informationen dazu, wie Sie die neueste Version erhalten, finden Sie in der Dokumentation unter dem Abschnitt zur [Bereitstellung von Communities](/help/communities/deploy-communities.md).

##### Verbesserte Community-Aktivierung {#enhancements-to-community-engagement}

Durch die **@Mentions-Unterstützung** von AEM Communities können registrierte Anwender nun im Zusammenhang mit anwendergenerierten Inhalten (User Generated Content, UGC) andere registrierte Mitglieder mit einem Tag versehen oder erwähnen („mention“), um deren Aufmerksamkeit zu erregen. Die getaggten (erwähnten) Mitglieder werden dann benachrichtigt, und zwar mit einem Deep-Link zu den entsprechenden anwendergenerierten Inhalten. Die Anwender können allerdings Web- und E-Mail-Benachrichtigungen deaktivieren/aktivieren.

![@Mentions-Unterstützung](/help/release-notes/assets/at-mentions.png)

Community-Anwender müssen nicht nach ihrem Vornamen, Nachnamen oder Anwendernamen suchen, um festzustellen, ob sich jemand an sie gewendet hat oder ihre Aufmerksamkeit benötigt. Außerdem können UGC-Autoren eine Antwort von bestimmten registrierten Anwendern anfordern, die am besten dazu geeignet sind, ein Problem zu lösen und Feedback zu geben.

Die Community-Admins müssen die Funktion **Erwähnung aktivieren** in den Community-Komponenten aktivieren, damit registrierte Anwendende die Funktion bei diesen Komponenten nutzen können.

**Gruppen-Messaging**

Registrierte Community-Mitglieder können jetzt über eine einzelne E-Mail-Komposition Direktnachrichten massenweise an Gruppen senden, anstatt dieselbe Nachricht einzeln an Gruppenmitglieder zu senden. Um [Gruppennachrichten](/help/communities/configure-messaging.md) zuzulassen, aktivieren Sie beide Instanzen des [Messaging Operations Service](/help/communities/messaging.md#group-messaging).

![Gruppennachricht](/help/release-notes/assets/group-messaging.png)

##### Verbesserte Massenmoderation {#enhancements-to-bulk-moderation}

Benutzerdefinierte Filter bei der Massenmoderation

[Benutzerdefinierte Filter](/help/communities/moderation.md#custom-filters) können jetzt entwickelt und der Benutzeroberfläche für die Massenmoderation hinzugefügt werden.

In [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) ist ein [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) verfügbar, das das Filtern nach Tags zeigt. Dieses Projekt kann als Grundlage zum Entwickeln analoger benutzerdefinierter Filter verwendet werden.

![Benutzerdefinierte Filter](/help/release-notes/assets/custom-tag-filter.png)

**Listenansicht bei der Massenmoderation**

In der Massenmoderation wurde eine neue Listenansicht mit verbesserter Benutzeroberfläche zur Anzeige benutzergenerierter Inhalte bereitgestellt.

![Massenmoderation in der Listenansicht](/help/release-notes/assets/list-view-moderation.png)

##### Verbesserungen der Site- und Gruppenverwaltung {#enhancements-to-site-and-group-management}

**Autorenseitige Site- und Gruppenadministrierende**

Communitys ab AEM 6.5 ermöglicht die dezentrale Administration (und Verwaltung) verschiedener Community-Sites und -Gruppen bzw. verschachtelter Gruppen. Organisationen, die mehrere Community-Sites und verschachtelte Gruppen hosten, können jetzt Mitglieder für Administratorrollen auf Autorenseite zum Zeitpunkt der Erstellung der Site (und Gruppe) auswählen.

![Site-Admin](/help/release-notes/assets/site-admin.png)

Site-Admins können eine Gruppe auf jeder Hierarchieebene erstellen und zu Standardadmins werden. Diese Admins können später von anderen Gruppenadmins entfernt werden. Gruppenadministrierende können ihre Gruppe G1 verwalten und eine Untergruppe erstellen, die unter G1 verschachtelt ist.

##### Verbesserungen bei der Aktivierung {#enhancements-to-enablement}

**Unterstützung für SCORM 2017.1**

Die Aktivierungsfunktion von AEM 6.5 Communities unterstützt die Engine „Shareable Content Object Reference Model“ [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/).

* Unterstützte Tastaturnavigation bei Aktivierungskomponenten
* Aktivierungskomponenten (z. B. &quot;Katalog- und Kurswiedergabe&quot;, &quot;Zuweisungen&quot;, &quot;Dateibibliothek&quot;) in AEM Communities unterstützen die Tastaturnavigation für eine verbesserte Barrierefreiheit.

##### Weitere Verbesserungen {#other-enhancements}

* Unterstützung für Solr 7
* AEM 6.5 Communities unterstützt die Apache Solr-Version 7.0 der Suchplattform beim Einrichten von MSRP und DSRP.

### [!DNL Experience Manager Assets] {#experience-manager-assets}

AEM 6.5 beinhaltet die folgenden neuen Funktionen und Erweiterungen mit denen AEM-Anwender, DAM-Anwender und Anwender mit entsprechenden Kreativ- sowie Marketingfunktionen ihre Produktivität steigern können.

#### Integration mit [!DNL Adobe Creative Cloud] und kreative Workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

[!DNL Adobe Experience Manager] bietet verschiedene Möglichkeiten, um zu integrieren und Assets für die Verwendung in Workflows freizugeben, in denen Kreativ-, Marketing- oder Business-Teams eng zusammenarbeiten. [!DNL Adobe Creative Cloud] [!DNL Experience Manager] 6.5 ermöglicht eine noch bessere Integration und stärkere Optimierung. Das Ergebnis: mehr Chancen und die Verbesserung vorhandener Methoden.

Im Folgenden werden die spezifischen Funktionen und Integrationsmöglichkeiten von [!DNL Experience Manager] 6.5 beschrieben, mit denen Sie Ihre Content-Velocity-Anwendungsfälle optimal unterstützen können.

##### Adobe Asset Link {#aal}

[!DNL Adobe Asset Link] stärkt die Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung. Kreative können auf Inhalte zugreifen, die in [!DNL Experience Manager Assets] gespeichert sind, ohne die ihnen besonders vertrauten Apps verlassen zu müssen. Kreative können mit dem In-App-Bedienfeld in [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign] Assets nahtlos (durch)suchen sowie ein- und auschecken.

[!DNL Adobe Asset Link] ist Teil des [Creative Cloud-Angebots für Unternehmen](https://www.adobe.com/creativecloud/business/enterprise.html). Weitere Informationen, einschließlich der erforderlichen Konfiguration für Ihre [!DNL Experience Manager]-Bereitstellung, finden Sie unter [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

![Suchen nach Assets in Adobe Photoshop](/help/release-notes/assets/asset_search_photoshop.png)

##### [!DNL Adobe Stock] Integration {#stock}

Ihr Unternehmen kann mit seinem [!DNL Adobe Stock]-Unternehmensabo in [!DNL Experience Manager Assets] sicherstellen, dass lizenzierte Assets für Ihre Kreativ- und Marketingprojekte zur Verfügung stehen. Mit den leistungsstarken DAM-Funktionen von [!DNL Experience Manager] können Sie schnell nach [!DNL Adobe Stock]-Assets suchen und diese im Nu in einer Vorschau anzeigen sowie lizenzieren.

Der [!DNL Adobe Stock]-Service bietet Designern und Unternehmen Zugang zu Millionen von hochwertigen, kuratierten und gebührenfreien Fotos, Vektorgrafiken, Illustrationen, Videos, Vorlagen und 3D-Assets für sämtliche Kreativprojekte.

Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets in Experience Manager Assets](/help/assets/aem-assets-adobe-stock.md).

![Vorschau von Adobe Stock-Bildern und Lizenzierung in Experience Manager Assets](/help/release-notes/assets/stock_image_preview_license_options.png)

*Abbildung: Vorschau [!DNL Adobe Stock] Bild und Lizenz von innerhalb [!DNL Experience Manager Assets].*

![Durchsuchen und Filtern der lizenzierten Adobe Stock-Bilder in Experience Manager ](/help/release-notes/assets/aem-search-filters2.jpg)

*Abbildung: Lizenzierte [!DNL Adobe Stock]-Bilder in [!DNL Experience Manager] suchen und filtern.*

##### Dynamische Verweise in [!DNL Adobe InDesign] {#dynamic-references-in-indesign}

Die in [!DNL Adobe InDesign]-Dateien verwendeten [!DNL Experience Manager Assets] sind dynamisch. Die Verweise werden automatisch aktualisiert, wenn die referenzierten Assets in das Repository verschoben werden. Weitere Informationen finden Sie unter [Verwalten von ebenenübergreifenden Assets](/help/assets/managing-linked-subassets.md).

#### Brand Portal-Funktionen {#brand-portal-capabilities}

Mit [!DNL Experience Manager Assets Brand Portal] können Sie problemlos genehmigte Assets abrufen, diese wirksam kontrollieren und sicher und geräteübergreifend an externe Anbieter/Agenturen und interne Geschäftsanwender verteilen. Brand Portal ermöglicht eine effizientere Asset-Freigabe sowie schnellere Time-to-Market für Assets und verringert das Risiko von Nicht-Compliance und unbefugtem Zugriff.

Weitere Informationen finden Sie unter [Neue Funktionen in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de).

#### Connected Assets {#connectedassets}

In großen Unternehmen ist die zur Erstellung von Websites erforderliche Infrastruktur möglicherweise verteilt. Manchmal befinden sich die Funktionen zur Website-Erstellung und die erforderlichen digitalen Assets in verschiedenen Silos.

[!DNL Experience Manager Sites] bietet Funktionen zum Erstellen von Web-Seiten, während das Digital Asset Management (DAM)-System ist, das die für Websites erforderlichen Assets bereitstellt. [!DNL Experience Manager Assets] [!DNL Experience Manager] unterstützt nun dank Integration von [!DNL Sites] und [!DNL Assets] das obige Nutzungsszenario. Siehe [Konfigurieren und Verwenden der Funktion „Connected Assets“](/help/assets/use-assets-across-connected-assets-instances.md).

![Ziehen eines Assets aus einer [!DNL Experience Manager]-Bereitstellung auf einer [!DNL Sites]-Seite einer anderen [!DNL Experience Manager]-Bereitstellung](/help/release-notes/assets/connected-assets-drag-and-drop-only.gif)

*Abbildung: Ziehen eines Assets aus einer [!DNL Experience Manager]-Bereitstellung auf einer [!DNL Sites]-Seite einer anderen [!DNL Experience Manager]-Bereitstellung.*

#### Dynamic Media {#dynamic-media}

[!DNL Dynamic Media] bietet eine erweiterte Rich-Media-Erstellung und -Bereitstellung in für beeindruckend intensive, personalisierte Erlebnisse. [!DNL Experience Manager Assets] Durch Hochladen eines einzigen hochwertigen Primär-Assets und Verwenden der erweiterten Cloudrendering-Funktion und der Viewer von Adobe können Sie eine beliebige Kombination von Ausgabedarstellungen direkt bereitstellen und so die Medienstrategie Ihres Unternehmens unterstützen.

Weitere Informationen zu neuen [!DNL Dynamic Media]-Funktionen finden Sie in den [Versionshinweisen zu Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/release-notes/s7rn2017.html?lang=de).

##### Unterstützung für 360°-Videos {#video-support}

Mit den hochmodernen Viewern können Sie 360°-Videodateien direkt in [!DNL Experience Manager] verwalten, um VR-Erlebnisse auf Desktops, Mobilgeräten und VR-Headsets bereitzustellen. Weitere Informationen finden Sie unter [Verwenden von 360°-Videos](/help/assets/360-video.md).

##### Benutzerdefinierte Videominiaturen {#custom-video-thumbnails}

Sie können nun die Miniaturen für Ihre Video-Assets mithilfe von Frames aus dem Video selbst oder aus anderen im DAM gespeicherten Inhalten anpassen. Weitere Anweisungen finden Sie unter [Informationen zu Videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

##### Verbesserte Barrierefreiheit {#accessibility-enhancements}

[!DNL Dynamic Media]-Viewer unterstützen jetzt erweiterte Barrierefreiheitsfunktionen wie Aria-Unterstützung, Bildschirmlesehilfen und Alternativtext. Weitere Informationen finden Sie im [Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html?lang=de).

#### Verbessertes Sucherlebnis {#experience-enhancement-for-searching}

Ab [!DNL Experience Manager] 6.5 können Marketing-Fachleute die gewünschten Assets schneller über die Suchergebnisseite ermitteln. Die Suchfacetten werden mit der Anzahl der Assets aktualisiert, noch bevor der Suchfilter angewendet wird. Durch Anzeige der erwarteten Anzahl nach Anwendung des Filters können Benutzer bzw. Benutzerinnen schnell und effizient durch Suchergebnisse navigieren. Weitere Informationen finden Sie unter [Suche nach Assets in Experience Manager](/help/assets/search-assets.md).

![Anzeigen der Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten](/help/assets/assets/asset_search_results_in_facets_filters.png)

*Abbildung: Anzeigen der Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten.*

#### Größere Anwenderfreundlichkeit {#usability-enhancement}

Sie können nun alle geladenen Assets in einem Ordner oder aus einem Suchergebnis in einem Schritt auswählen. Dies ermöglicht eine schnelle Verwaltung aller Assets. Mit dem Kontrollkästchen werden alle zum Szenario passenden Assets ausgewählt, beispielsweise ein Suchergebnis, und nicht nur die in der [!DNL Experience Manager]-Oberfläche angezeigten Assets.

![Auswahl aller Assets mit einem Klick über die Option „Alle auswählen“](/help/release-notes/assets/select-all-in-aem-assets.gif)

*Abbildung: Auswahl aller Assets mit einem Klick über die Option „Alle auswählen“*

#### Verbesserte Metadaten {#metadata-enhancements}

Mit [!DNL Assets] können Sie Metadatenschemata für Asset-Ordner erstellen, die die auf Seiten mit Ordnereigenschaften angezeigten Layouts und Metadaten definieren. Sie können einem vorhandenen Ordner ein Ordner-Metadatenschema zu diesem Zeitpunkt oder beim Erstellen eines Ordners zuweisen. Weitere Informationen finden Sie unter dem [Ordner „Metadatenschema“](/help/assets/metadata-config.md#folder-metadata-schema).

Beim Angeben kaskadierender Metadaten können die Optionen zur Laufzeit aus einer JSON-Datei geladen werden, anstatt sie beispielsweise manuell im Formular einzugeben. Weitere Informationen finden Sie unter [Kaskadierende Metadaten](/help/assets/metadata-schemas.md#cascading-metadata).

#### Verbessertes Reporting {#reporting-enhancements}

Die Inhaltsfragmente und Linkfreigaben sind nun im Bericht „heruntergeladen“ enthalten. Weitere Informationen finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md).

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 Forms wurde um mehrere neue Funktionen und Erweiterungen ergänzt. Hier einige der Highlights:

* Transaktionsberichte zum Nachverfolgen der Anzahl der übermittelten Formulare, verarbeiteten Dokumente und gerenderten Dokumente
* Verbesserungen der Benutzerfreundlichkeit bei interaktiver Kommunikation
* Cloud-basierte digitale Signaturen in adaptiven Formularen
* Integration adaptiver Formulare und interaktiver Kommunikation in eine Einzelseitenanwendung (Single Page Application, SPA) für AEM Sites.
* Unterstützung für Variablen in AEM-Workflows
* Unterstützung für Datenanzeigemuster bei interaktiver Kommunikation
* Sortieren adaptiver Formulare und Tabellen zu interaktiver Kommunikation
* Automatische Validierung von Eingabedaten in Formulardatenmodellen

Weitere Informationen zu neuen und verbesserten Funktionen sowie Dokumentationsressourcen finden Sie in der [Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.5 Forms](/help/forms/using/whats-new.md).

### Verwenden von kundenorientierter Entwicklung {#leverage-customer-focused-development}

Adobe verwendet ein kundenorientiertes Entwicklungsmodell, das es den Kunden ermöglicht, zu allen Phasen des Entwicklungsprozesses von der Spezifikation über die Entwicklung bis hin zum Test beizutragen. Unser Dank geht an alle beteiligten Kunden und Partner in diesem Prozess.

Adobe hält die erforderlichen Vorgehensweisen und Prozesse bereit, um die Erfassung, Priorisierung und Verfolgung kundenorientierter Fehlerbehebungen und eine auf Verbesserungswünsche bezogene Entwicklung zu ermöglichen. Das [Experience Manager-Supportportal](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home&amp;lang=de#support) ist mit dem Adobe Enhancement and Defect Tracking System integriert. Kundenprobleme werden, wenn möglich, gemeinsam mit dem Kunden-Support-Team identifiziert und gelöst. Bei einer Weiterleitung an Forschung und Entwicklung werden alle Kundeninformationen erfasst und zu Priorisierungs- und Reporting-Zwecken verwendet. Bei der Entwicklung haben bezahlter Support, Garantieprobleme sowie bezahlte Kundenerweiterungen Priorität.

Dieser Prozess der Priorisierung hat zu mehr als 750 kundenorientierten Änderungen geführt, die in AEM 6.5 vorgenommen wurden.

## Liste der Dateien, die Teil der Version sind {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Eigenständiger Schnellstart: `cq-quickstart-6.5.0.jar`.
* Anwendungsserver-Schnellstart: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 oder höher für verschiedene Webserver und Plattformen Siehe [Downloadlink](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html?lang=de)
* Plug-in für Eclipse IDE ([weitere Informationen und Download](/help/sites-developing/aem-eclipse.md))

* Erweiterung für Brackets-Code-Editor ([weitere Informationen und Download](/help/sites-developing/aem-brackets.md))
* Maven-/Gradle-Abhängigkeiten ([Downloadlink](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.0/))

**Sites**

* Kernkomponenten ([GitHub-Projekt](https://github.com/adobe/aem-core-wcm-components))
* We.Retail-Referenzimplementierung ([mehr dazu](/help/sites-developing/we-retail.md))
* Maven-Projektarchetypen:

   * Für Full-Stack-Sites: [GitHub-Projekt](https://github.com/adobe/aem-project-archetype)
   * Für Single-Page-Apps mit React/Angular: [GitHub-Projekt](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens-Player für verschiedene Zielplattformen ([Download](https://download.macromedia.com/screens/))

* Smart Content-Sprachmodelle. Englisch ist vorinstalliert, weitere Sprachen können heruntergeladen werden.

   * [Deutsch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spanisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italienisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Französisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Modernize Tools Suite, z. B. das Dialogfeldkonvertierungs-Tool. ([GitHub-Projekt](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Paket zum Hinzufügen eines erweiterten PDF Rasterizer ([mehr dazu](/help/assets/aem-pdf-rasterizer.md))
* Paket zum Hinzufügen der erweiterten Unterstützung von RAW-Bildern ([mehr dazu](/help/assets/camera-raw.md))

**Formulare**

* [Pakete für AEM Forms-Funktionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)
* [AEM Forms – OSGi Client-SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/)

## Sprachen {#languages}

Die Benutzeroberfläche ist in den folgenden Sprachen verfügbar:

* Englisch
* Deutsch
* Französisch
* Spanisch
* Italienisch
* Brasilianisches Portugiesisch
* Japanisch
* Vereinfachtes Chinesisch
* Traditionelles Chinesisch (begrenzte Unterstützung)
* Koreanisch

[!DNL Experience Manager] 6.5 ist für GB18030-2005 CITS zertifiziert und kann daher den chinesischen Kodierungsstandard verwenden.

## Installieren und Aktualisieren {#install-update}

Informationen zu Setup-Anforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene, finden Sie unter [AEM 6.5 – Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Für Oracle Java™ SE-Produkte ist Oracle ist auf ein LTS (Long Term Support)-Modell umgestiegen. Java™ 9 und 10 sind Non-LTS-Versionen von Oracle. Weitere Informationen finden Sie in der [Roadmap für den Oracle Java SE-Support](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe unterstützt LTS-Versionen von Java™ nur zum Ausführen von AEM in einer Produktionsumgebung. Java™ 11 ist die empfohlene Version für AEM 6.5.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe prüft kontinuierlich den Bedarf an Funktionen im Produkt und ersetzt ggf. Funktionen durch leistungsstärkere Versionen oder implementiert ausgewählte Teile neu, um besser auf zukünftige Erwartungen oder Erweiterungen vorbereitet zu sein.

Für [!DNL Adobe Experience Manager] 6.5 sollten Sie die [Liste veralteter und entfernter Funktionen lesen](/help/release-notes/deprecated-removed-features.md). Die Seite enthält auch Vorankündigungen für zukünftige Änderungen sowie wichtige Hinweise für Kundinnen und Kunden, die frühere Versionen aktualisieren.

## Bekannte Probleme {#known-issues}

### Plattform {#platform}

* Es wird ein Problem gemeldet, bei dem CRX-Quickstart und sein Inhalt gelöscht werden.

  Stellen Sie bei jeder dieser Aktionen sicher, dass die Eigenschaft `htmllibmanager.fileSystemOutputCacheLocation` keine leere Zeichenfolge ist:

   1. Bei einem Aufruf von `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Aktualisieren auf AEM 6.5.
   3. Ausführen von „Lazy Content Migration“ in AEM 6.5.

  Ein [Knowledgebase](https://helpx.adobe.com/de/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html)-Artikel mit weiteren Details und einer Umgehungslösung für dieses Problem ist verfügbar.

* Wenn Sie JDK 11 mit einer AEM 6.5-Instanz verwenden, werden einige der Seiten nach der Bereitstellung einiger Pakete möglicherweise als leer angezeigt. Die folgende Fehlermeldung wird in der Protokolldatei angezeigt:

  ```java
  *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
  java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
  ```

Um diesen Fehler zu beheben:

1. Halten Sie die AEM-Instanz an. Navigieren Sie zu `<aem_server_path_on_server>crx-quickstart\conf` und öffnen Sie die Datei `sling.properties`. Adobe empfiehlt, ein Backup dieser Datei zu erstellen.

1. Suchen Sie nach `org.osgi.framework.bootdelegation=`. Fügen Sie `jdk.internal.reflect,jdk.internal.reflect.*`-Eigenschaften hinzu, um das Ergebnis anzuzeigen.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Speichern Sie die Datei und starten Sie die AEM-Instanz neu.

### Sites {#sites}

* **Arbeiten mit Seitenversionen**: [Wenn eine Seite verschoben wurde, können Sie keine Vorschau von Versionen mehr anzeigen, die vor dem Verschieben erstellt wurde](/help/sites-authoring/working-with-page-versions.md#previewing-a-version).

### Assets {#assets}

* **Suche**: Die Suche gibt keine Ergebnisse zurück, wenn die Suchzeichenfolgen führende Leerzeichen enthält ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)).
* **Ordner „Metadatenschema“**: Nach dem Hinzufügen einer Auswahl-Schaltfläche werden die Felder „ID“ und „Wert“ nicht erwartungsgemäß gerendert und die Löschfunktion funktioniert nicht. (CQ-4261144)
* Beim Umbenennen eines Assets ist es nicht möglich, ein Leerzeichen im Asset-Namen zu verwenden. (CQ-4266403)

### Formulare {#forms}

* Wenn AEM Forms unter einem Linux®-Betriebssystem installiert ist, funktioniert die digitale Signatur nicht beim Modul für die Hardware-Sicherheit. (CQ-4266721)
* (Nur AEM Forms auf WebSphere®) Die Option **Forms-Workflow** > **Aufgabensuche** gibt kein Ergebnis zurück, wenn Sie nach einem **Admin** anhand des **Benutzernamens** suchen. (CQ-4266457)

* AEM Forms kann keine TIF- und TIFF-Dateien mit JPEG-Komprimierung in PDF-Dokumente konvertieren. (CQ-4265972)
* Die Optionen **AEM Forms Assets-Scanner** und **Migration von Briefen zu interaktiver Kommunikation** funktionieren auf der Seite **AEM Forms-Migration** nicht. (CQ-4266572)

* (Nur JBoss® 7) Wenn von einer früheren Version ein Upgrade auf AEM 6.5 Forms durchführen und diese frühere Version Prozesse (.lca) aufwies, die eine Kopie des standardmäßigen Submit- oder Render-Prozesses erstellt und kopiert haben, können HTML5-Formulare mit solchen Prozessen (.lca) die erforderlichen Aktionen nicht ausführen. (CQ-4243928)
* Wenn in einem adaptiven Formular ein Formulardatenmodell-Dienst vom Regeleditor aufgerufen wird, um Werte der Bildauswahlkomponente dynamisch zu aktualisieren, werden die Werte der Bildauswahlkomponente nicht aktualisiert. (CQ-4254754)
* Für das AEM Forms Designer-Installationsprogramm ist die 32-Bit-Version von [Visual C++ Redistributable Runtime Package 2012](https://docs.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170) und [Visual C++ Redistributable Runtime Package 2013](https://support.microsoft.com/de-de/topic/update-for-visual-c-2013-and-visual-c-redistributable-package-5b2ac5ab-4139-8acc-08e2-9578ec9b2cf1) erforderlich. Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind. (CQ-4265668)

* PDF Generator unterstützt keine Authentifizierung mit Smart Card. Wenn ein Admin die Gruppenrichtlinie `Interactive Logon: Require Smart card` auf einem Windows-Server aktiviert, werden alle vorhandenen PDF Generator-Benutzenden ungültig gemacht.

* Wenn ein adaptives Formular so konfiguriert ist, dass die Werte einer Komponente dynamisch aktualisiert werden, und über den Dispatcher auf die Veröffentlichungsinstanz zugegriffen wird, die das Formular hostet, kann die Funktion zum dynamischen Aktualisieren von Feldwerten nicht mehr verwendet werden. Um das Problem zu lösen, öffnen Sie CRXDE in der Veröffentlichungsinstanz, navigieren Sie zu `/libs/fd/af/runtime/clientlibs/guideChartReducer` und erstellen Sie die unten aufgeführte Eigenschaft.

   * Name: allowProxy
   * Typ: Boolean
   * Wert: true
   * Geschützt: False
   * Obligatorisch: False
   * Mehrere: False
   * Auto Created: False

  Durch diese Eigenschaft können Client-Bibliotheken unter dem Laufzeitordner auf Proxys zugreifen (CQ-4268679)

* Wenn AEM Forms gestartet wird, wird die Meldung `SAX Security Manager could not be setup` angezeigt.
* Wenn Sie eine mit AEM Forms Document Security geschützte PDF-Datei auf einem Apple iOS oder iPadOS Version 20.10.00 mit Adobe Acrobat Reader öffnen.
* Wenn Sie ein Formular mit einem Standard-HTML-Upload-Feld von einem Apple iOS-Gerät aus übermitteln, wird der Inhalt der Datei manchmal nicht gesendet und eine 0-Byte-Datei wird am anderen Ende empfangen. Apple iOS 15.1 bietet eine Korrektur für das Problem.

## Produktdownload und Support (beschränkte Websites) {#product-download-and-support-restricted-sites}

Die folgenden Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).

* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen in der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Kunden-Support über die Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Adobe-Kunden-Supporterlebnis](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).
