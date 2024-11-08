---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: 7939703fe7ef9382e9d1a426c0eb9f021b964d1a
workflow-type: tm+mt
source-wordcount: '4672'
ht-degree: 41%

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
| Version | 6.5.22.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Freitag, 21. November 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.22.0 enthalten ist {#what-is-included-in-aem-6522}

[!DNL Experience Manager] 6.5.22.0 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit der Version 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) für [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

### Sites {#sites}

[Der universelle Editor](/help/sites-developing/universal-editor/introduction.md) ist jetzt in AEM 6.5 für Headless-Anwendungsfälle verfügbar.


### [!DNL Forms]

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:


<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 22 {#fixed-issues}


### [!DNL Sites]{#sites-6522}


#### Barrierefreiheit {#sites-accessibility-6522}

* Der Auswahlschaltfläche für Anmerkungsmuster fehlte ein zugänglicher Name. Bei Verwendung einer Bildschirmlesehilfe gibt es also keinen verständlichen Namen für die Schaltfläche, die nach Eingabe eines neuen Hexadezimalwerts ausgewählt werden kann. (SITES-11992) MAJOR
* Die folgenden Elemente im Menü der linken Leiste erscheinen wie eine Liste, sind jedoch in der Bildschirmlesehilfe nicht als solche gekennzeichnet:

   * Site
   * Live Copy
   * Launch
   * Sprachkopie
   * Ordner
   * CSV-Bericht (SITES-2874)

* Für das AEM Core Web Content Management ist eine Zugriffsbeschriftung für Hyperlinks im Rich-Text-Editor erforderlich. Wenn ein Hyperlink in der Textkomponente verwendet wird, sollte das Verankerungs-Tag das Attribut `aria-label` enthalten, um sicherzustellen, dass Bildschirmlesehilfen den Linktext aus Gründen der Barrierefreiheit korrekt lesen und vermitteln können. (SITES-11511)
* In AEM haben interaktive Elemente in der Tabellenüberschrift in der Listenansicht nicht die erforderliche &quot;Schaltfläche&quot;-Rolle. Daher kündigt die NVDA-Bildschirmlesehilfe nicht die erwarteten Schaltflächenrollen für die folgenden Tabellenüberschriften an: Titel, Name, Geändert, Veröffentlicht, Vorschau, Vorlage, Vorgang, Workflow. Jedem interaktiven Element im Tabellenheader sollte eine &quot;Schaltflächen&quot;-Rolle zugewiesen werden, um die Kompatibilität mit Hilfstechnologien wie NVDA sicherzustellen. (SITES-10962)


#### Admin-Benutzeroberfläche{#sites-adminui-6522}

* In einigen AEM funktionierten die Funktionen für Versionsvorschau und -vergleich auf mehreren Seiten nicht erwartungsgemäß. Insbesondere gilt:

   * **Vorschauerproblem:** Beim Versuch, eine Seitenversion in der Vorschau anzuzeigen, wird zunächst ein Fehler angezeigt. Nach dem erneuten Versuch wird die Vorschau auf eine leere Seite angezeigt.
   * **Problem mit dem Versionsvergleich:** Die Funktion &quot;Mit aktueller Version vergleichen&quot;zeigte nur die aktuelle Version an, ohne Unterschiede zwischen den Versionen hervorzuheben. (SITES-23988) MAJOR

* Ein unerwartetes Tag `<br>` wird im Feld Rich-Text-Editor (RTE) angezeigt, wenn während einer Kopier- und Einfügeaktion der Wert `defaultPasteMode` auf `plaintext` gesetzt wird. Dieses Problem führt zu einem unterschiedlichen Markup für denselben Inhalt, sodass derselbe Textinhalt zweimal im Translation Memory eines Kunden übersetzt wird. (SITES-23606) MAJOR
* In AEM 6.5.20.0 trat ein Funktionsproblem mit der Funktion **Veröffentlichung verwalten** auf. Bei der Auswahl eines Knotens und der Planung seiner zukünftigen Veröffentlichung könnte beim Versuch, untergeordnete Knoten einzubeziehen, die Fehlermeldung &quot;Untergeordnete Ressourcen für ausgewählte Elemente konnten nicht abgerufen werden&quot;angezeigt werden. Dieses Problem blockierte die Verwendung der Option **Untergeordnete Elemente einschließen** und verhinderte die vollständige Veröffentlichung der beabsichtigten Inhaltshierarchie. (SITES-23000) MAJOR
* Der Zeitstempel &quot;Veröffentlicht&quot;einer Vorlage wurde in der Autorenumgebung nicht aktualisiert, obwohl die Vorlage erfolgreich in die Veröffentlichungsinstanzen repliziert wurde. Es wurde erwartet, dass der Zeitstempel in der Autoreninstanz die neueste Veröffentlichung widerspiegelt, aber diese Aktualisierung erfolgte nicht wie gewünscht. (SITES-21585) MAJOR
* In der AEM Autorenumgebung gab es eine Diskrepanz bei der Anzahl der eingehenden Links. Die linke Seitenleiste zeigte im Vergleich zur klassischen Benutzeroberfläche weniger Links. Auch einige eingehende Links, die legitim waren, funktionieren nicht. (SITES-24837)
* Beim Anzeigen von Seitenversionen in der Timeline-Ansicht von AEM wurden extrem lange Ladezeiten gemeldet. Es dauerte bis zu 19 Minuten, bis Versionen angezeigt wurden. Dieses Problem wurde seit der Aktualisierung von AEM 6.4.8 auf 6.5.18 behoben, wodurch die Workflow-Effizienz erheblich beeinträchtigt wurde. (SITES-22468 &amp; SITES-22467)

<!-- #### Classic UI{#sites-classicui-6522} 

* A -->


#### [!DNL Content Fragments]{#sites-contentfragments-6522}

* Im aktualisierten AEM 6.5.17 führte das Speichern von Inhaltsfragmenten zum folgenden Fehler: *FEHLER: Inhaltsfragment konnte nicht gespeichert werden.* (SITES-22993) KRITISCH
* Ein Problem wurde mit einem nicht geschlossenen Ressourcen-Resolver in `ContentFragmentModelOmniSearchHandler` beim Herausgeber in AEM erkannt. (SITES-24903)


#### [!DNL Content Fragments] - Admin{#sites-admin-6522}

* Durch Klicken auf den Link in der E-Mail-Benachrichtigung wird der Benutzer zum Standard-Asset-Viewer oder -Editor weitergeleitet. Dies erfolgt anstelle des Inhaltsfragment-Editors, selbst wenn das Asset im Workflow als Inhaltsfragment festgelegt wurde. (SITES-24338) MAJOR


#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6522}

* Bei der Verwendung von Inhaltsfragmenten mit mehrzeiligen Textfeldelementen behälte das bei der Abfrage mit GraphQL generierte Markup nicht die in der HTML angegebene Formatierung bei. Beispielsweise fehlte nach der Liste ein Zeilenumbruch. Die Folge war, dass der letzte Absatz in die Liste aufgenommen wurde. (SITES-23233)


<!-- #### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6522}

* A


#### [!DNL Content Fragments] - REST API{#sites-restapi-6522}

* A -->

#### Core-Backend{#sites-core-backend-6522}

* Wiederkehrende `SegmentNotFoundException` Fehler wurden in einer AEM Autoreninstanz gemeldet. Beim Neustart des Autors wurde das Problem vorübergehend behoben, es war jedoch eine langfristige Korrektur erforderlich, um weitere Vorkommnisse zu verhindern. (SITES-22573)
* Es wurde ein Problem bezüglich der Timeline-Funktionalität in AEM Sites angesprochen, insbesondere bezüglich der Handhabung fehlender `cq:lastModified`-Eigenschaften für Anmerkungen. Nach der Anwendung von AEM 6.5.20 bestand Unsicherheit darüber, ob der vorhandene Inhalt eine Behebung für die fehlende Eigenschaft benötigte oder ob die Timeline so aktualisiert wurde, dass sie ohne sie ordnungsgemäß funktionierte. (SITES-21861)


#### Kernkomponenten{#sites-core-components-6522}

* Nach einem Upgrade von AEM 6.5.18 auf 6.5.21 wurde ein Problem mit der Funktionalität identifiziert, die die Live-Nutzung von Komponenten überprüft. Beim Versuch, auf der Seite &quot;Live-Nutzung&quot;nach zusätzlichen Elementen zu scrollen, konnte die Tabelle nicht mehr Ergebnisse laden, obwohl in der Benutzeroberfläche &quot;Weitere Elemente laden&quot;angezeigt wurde. (SITES-23919)
* Bei der Validierung erforderlicher Felder in einem Dialogfeld AEM Komponente mit zwei Registerkarten wurde ein Problem gemeldet. Registerkarte 1 enthielt einen Rich-Text-Editor (RTE) und Textfelder, während Registerkarte 2 Pfadfelder und Textfelder enthielt. Obwohl alle Felder als Pflichtfelder (`required=true`) markiert sind, bleiben Fehlerbenachrichtigungen in Tab 1 falsch, auch wenn alle erforderlichen Felder ausgefüllt wurden. Im Gegensatz dazu werden Fehler in Tab 2 erwartungsgemäß gelöscht. (SITES-23243)
* Nach der Migration auf AEM 6.5.21 funktionierte die HTML Template Language `data-sly-include` -Anweisung nicht mehr wie erwartet, insbesondere nicht unterstützt die Ausdrücke `appendPath` und `prependPath`. Daher wurde die Ausgabe der eingeschlossenen Ressource nicht ordnungsgemäß gerendert, obwohl sie vor der Migration ordnungsgemäß funktionierte. Dieses Problem führte zu Rendering-Fehlern für Ressourcen, die diese Ausdrücke für Pfadmanipulationen benötigen. (GRANITE-52970)


<!-- #### Campaign integration{#sites-campaign-integration-6522}

* A -->


#### Experience Fragments{#sites-experiencefragments-6522}

* Experience Fragments sortieren nicht nach Titel, wie erwartet, wenn in der Listenansicht auf die Spaltenüberschrift **Titel** geklickt wird. Ein schnelles Flackern des Bildschirms wird beobachtet, es wird jedoch nicht sortiert. (SITES-23706) MAJOR

* In AEM 6.5.17 trat beim Konvertieren einer Seitenkomponente in ein Experience Fragment mithilfe der vordefinierten Funktion ein Problem auf. Nach der Konvertierung erschien das Experience Fragment während der Bearbeitung leer, obwohl es auf der Seite, auf der es verwendet wurde, korrekt angezeigt wurde. Das Problem resultierte aus der falschen Knotenerstellung: Der Komponentenknoten wurde außerhalb des Stammknoten/Container-Knotens platziert und verletzt somit die Struktur der Vorlage. Sie mussten den Komponentenknoten manuell in den richtigen Stamm-/Container-Knoten verschieben, um die Bearbeitbarkeit des Fragments wiederherzustellen. (SITES-22974) MAJOR

* Nach der Migration von AEM 6.5.11 auf 6.5.20 wurden Cloud-Konfigurationen für Experience Fragments nicht korrekt gespeichert. Obwohl die Konfigurationen in `crx/de` zu speichern schienen, wurden sie beim erneuten Öffnen der Konfigurationskonsole nicht angezeigt, was auf ein Problem mit Persistenz hinweist. (SITES-22287) MAJOR


<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6522}

* A -->


#### Launches{#sites-launches-6522}

* Beim Hinzufügen von Experience Fragment-Assets mithilfe des Tagging-Filters in AEM Produktionsumgebung konnte der Benutzer diese zwar auswählen, es trat jedoch nach Auswahl von **Sprachkopie erstellen** ein Fehler auf. Das erwartete Verhalten war, dass das aus dem Tagging-Filter ausgewählte Experience Fragment-Asset zum Übersetzungsprojekt hinzugefügt werden sollte. (SITES-24152) MAJOR

#### Link-Checker{#sites-link-checker-6522}

* Die Authentifizierung von LinkCheckerTask schlägt fehl, da der HTTP-Client NTLM vor der einfachen Authentifizierung versucht, wodurch der Proxy Benutzer nach mehreren fehlgeschlagenen Versuchen blockiert. Das System sollte stattdessen die Standardauthentifizierung verwenden, um sich gegen den Proxy zu authentifizieren, sodass die LinkCheckerTask-Dienste ordnungsgemäß funktionieren. (SITES-25034) MAJOR


#### MSM – Live Copies{#sites-msm-live-copies-6522}

* Wenn SEO Robots-Tags auf die primäre Kopie angewendet und auf Live Copy-Seiten bereitgestellt werden, wurden die Werte korrekt in `crx/de` angezeigt. Die Werte wurden jedoch nicht in der Benutzeroberfläche unter den Seiteneigenschaften der Live Copy-Seiten angezeigt. (SITES-23475) MAJOR
* Fehler im Zusammenhang mit Launches traten auf, wenn versucht wurde, einen Launch über die Benutzeroberfläche zu bewerben. Der Assistent Launch bewerben blieb leer, was den Abschluss des Promotion-Prozesses verhinderte. (SITES-19718)
* Es traten Probleme mit Experience Fragments in AEM nach Versuchen auf, Live Copies zu erstellen und Rollouts durchzuführen. Das Problem trat auf, wenn Benutzer beim Versuch, vom Bildschirm &quot;Rollout&quot;aus zum Bildschirm &quot;Experience Fragments-Verwaltung&quot;zurückzukehren, einen `NotFound` -Fehler bemerkten. (SITES-21933)


#### Seiteneditor{#sites-pageeditor-6522}

* Mit der Schaltfläche Rückgängig wurde die Position der Komponente geändert und der Text in die letzte Version geändert. (SITES-17465) BLOCKER
* Wenn eine kopierte Container-Komponente eingefügt wurde, erschien sie zweimal visuell, was zu drei Instanzen auf der Seite führte. Nach dem Aktualisieren der Seite verschwand das Duplikat jedoch, was darauf hindeutet, dass das Problem wahrscheinlich ein vorübergehender visueller Fehler war. (SITES-21890) MAJOR
* Beim Navigieren im linken Bereich &quot;Komponenten&quot;mithilfe der Tabulatortaste oder Umschalt+Tab der Tastatur waren mehrere Textelemente weder visuell noch im Tab-Modus deutlich sichtbar. Dieses Problem betraf die Barrierefreiheit, wodurch es schwierig war, diese Komponenten während der Tastaturnavigation zu identifizieren oder mit ihnen zu interagieren. (SITES-2266)

#### Replikation{#sites-replication-6522}

* In AEM 6.5.18 und 6.5.19 wurden beim Deaktivieren einer übergeordneten Seite für jede untergeordnete Seite mehrere Deaktivierungsanfragen generiert. Dieses Problem hat auch die Massenrückgängigmachung der Veröffentlichung der GraphQL-Endpunkte verhindert. (NPR-42075 &amp; NPR42010) CRITICAL


### [!DNL Assets]{#assets-6522}

* Bei Verwendung der Funktion &quot;Connected Assets&quot;beziehen sich die in AEM Assets vorgenommenen Aktualisierungen nicht auf die AEM Sites-Umgebung. (ASSETS-42344) MAJOR <!-- Leave the "MAJOR" status priorities in place. -->
* (ASSETS-41158) MAJOR
* Das Hochladen von Assets mit der API führt zur Fehlermeldung `unclosed resource resolver`. (ASSETS-41049) MAJOR
* (ASSETS-40384) MAJOR
* In AEM Version 6.5.19 werden beim Entfernen einer Option aus den Suchbereichsergebnissen auch alle anderen verfügbaren Kontrollkästchen deaktiviert. (ASSETS-37335) MAJOR
* Bei der Durchführung des Massen-Metadatenexports werden in der Excel-Ausgabe unbrauchbare Werte angezeigt. (ASSETS-37260) MAJOR
* Wenn Sie in AEM Version 6.5.19 eine SVG-Datei im UTF-8-Format hochladen, ist die Ausgabe verschwommen. (ASSETS-36616) MAJOR
* Die Option `Fetch original rendition for Dynamic Media Connected Assets` fehlt in der Konfiguration Connected Assets . (ASSETS-41726)
* Asset-Eigenschaften werden auch dann gespeichert, wenn Sie keinen Wert für erforderliche Felder definieren. (ASSETS-37914)

#### [!DNL Dynamic Media]{#assets-dm-6522}

* Bei einem Produktionsfehler wurde der Migrationsprozess gestört, wenn ein Video-Upload in Dynamic Media fehlschlug, was auf der Benutzeroberfläche einen Prozessfehler anzeigte. (ASSETS-36038)


### [!DNL Forms]{#forms-65220}

Die Fehlerbehebungen in [!DNL Experience Manager] Forms werden eine Woche nach dem geplanten Veröffentlichungsdatum des [!DNL Experience Manager] Service Packs über ein separates Add-on-Paket bereitgestellt. In diesem Fall ist die AEM Forms-Add-On-Paket-Version 6.5.22.0 für Donnerstag, den Freitag, 28. November 2024 geplant. Nach der Veröffentlichung wird diesem Abschnitt eine Liste mit Forms-Fehlerbehebungen und -Verbesserungen hinzugefügt.


<!-- #### [!DNL Adaptive Forms] {#forms-6522}

* A


#### [!DNL Forms Designer] {#forms-designer-6522}

* A -->


### Fundament {#foundation-6522}

* In der AEM Assets-Konsole ist beim Versuch, DITA-Dokumente neu anzuordnen, ein Problem aufgetreten. Die Breadcrumb-Leiste am oberen Rand des Dialogfelds des Pfad-Browsers zeigt fälschlicherweise den Knotennamen anstelle des Knotentitels für das Stammverzeichnis an. Der richtige Knotentitel wird nur angezeigt, nachdem ein Element im Breadcrumb ausgewählt wurde, was auf einen temporären Anzeigefehler hinweist. (NPR-42106) MAJOR


<!-- #### Apache Felix {#foundation-apachefelix-6522}


* A

#### Campaign{#foundation-campaign-6522}

* A


#### Cloud Services{#foundation-cloudservices-6522}

* A -->


#### Communities {#foundation-communities-6522}

* Nach der Aktualisierung von AEM 6.5.19 auf 6.5.20 trat ein Problem auf, bei dem `Connection evic`-Threads nach Aufrufen von `UgcSearch` nicht ordnungsgemäß geschlossen wurden. Dieses Problem, das in der Produktionsumgebung beobachtet wird, bewirkt, dass diese Threads im Laufe der Zeit bestehen bleiben und akkumulieren, was sich möglicherweise auf die Leistung auswirkt. (NPR-42019) MAJOR


<!-- #### Content distribution{#foundation-content-distribution-6522}

* A -->


#### CRX {#foundation-crx-6522}

* Die Sortierung funktionierte nicht gemäß **Gruppen** im linken Seitenmenü im CRX Package Manager. (GRANITE-53277)
* Der Package Manager in AEM beschränkt die Installation von niedrigeren Paketversionen standardmäßig, ermöglicht jedoch erzwungene Installationen älterer Versionen. Die Verwendung der Option zur erzwungenen Installation kann jedoch über die Standard-Pipeline künftige Installationen beeinträchtigen. Wenn beispielsweise Version 1.21 installiert und Version 1.24 hinzugefügt wird, ist die Installation erfolgreich und listet beide Versionen auf. Der Versuch, Version 1.22 über Version 1.24 zu installieren, schlägt jedoch fehl, wenn die Pipeline erzwungen installiert ist, und listet alle Versionen auf. Ebenso wird die Installation von Version 1.23 blockiert, wenn Version 1.24 bereits vorhanden ist, da die Pipeline keine Downgrades zulässt. (GRANITE-53263)


#### Granite{#foundation-granite-6522}

* Momentaufnahmen-Pakete wurden in AEM mit CURL-Befehlen installiert. Während der Installation hat das JCR-Installationsprogramm die Pakete über das OSGi-Installationsprogramm gescannt, um sicherzustellen, dass keine zusätzlichen OSGi-Pakete oder -Konfigurationen erforderlich sind. Wenn eine Paketversion &quot;SNAPSHOT&quot;enthielt, hat das OSGI-Installationsprogramm VLT ausgelöst, um ein entsprechendes Snapshot-Paket zu erstellen. Da jedoch jede AEM Autoreninstanz ihr eigenes OSGi-Installationsprogramm ausführt, können beide Instanzen versuchen, den Schnappschuss gleichzeitig zu generieren, was zu Sitzungskonflikten innerhalb des Repositorys führt. (NPR-42003) MAJOR
* In `ScriptDependencyResolver` gab es einen Sperrkonflikt mit AEM 6.5.21. (GRANITE-53181) MAJOR
* Nach der Aktualisierung AEM auf 6.5.21 traten Probleme auf, wenn relative Pfade in der Sightly-Syntax (HTL) verwendet wurden, z. B. `data-sly-use`. (GRANITE-53080) MAJOR


#### Integrationen{#foundation-integrations-6522}

* Es wurde eine gültige Zuordnungsanweisung für die Cloud Service-Benutzeroberfläche hinzugefügt. (FORMS-16373)
* Es wurden Leseberechtigungen für den Benutzer **fd-cloudservice** hinzugefügt, um auf die Captcha- und Turnstile-Konfigurationen zuzugreifen, sodass die Client-ID und das Client-Geheimnis abgerufen werden können, die für die Captcha-Wiedergabe und -Validierung erforderlich sind. Außerdem wurde ein Zugriffssteuerungslisten-Modell implementiert, um den Zugriff auf diese Konfigurationen zu verwalten. (FORMS-16360)


#### Lokalisierung{#foundation-localization-6522}

* In ![Hammersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Hammer_18_N.svg) Tools > **Sicherheit** > ![Benutzersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_User_18_N.svg) **Benutzer** wurden auf der Seite &quot;Benutzerverwaltung&quot;die Daten in der Spalte **Status** der Tabelle vertikal angezeigt. (GRANITE-48304)


<!-- #### Oak {#foundation-oak-6522}

* A -->


#### Platform{#foundation-platform-6522}

* Das in AEM 6.5.18 eingeführte Enterprise Information Management-Tracking verursachte Anomalien bei der Berechnung der Produktakzeptanzwerte. Die Adobe Metrics-Bibliothek hat dieses Problem verursacht, indem sie Benutzerdaten überschrieben, die von der Omega-Tracking-Bibliothek bereitgestellt wurden. Infolgedessen sind die Adoptionswerte für viele Kunden von AEM Sites und AEM Assets ab Februar 2024 auf null gesunken. (CQ-4358438) CRITICAL
* Ein kritisches Problem wurde in der Produktionsumgebung identifiziert, in der der Garbage Collector Tags nicht ordnungsgemäß verarbeitet hat. Insbesondere beim Verschieben oder Umbenennen eines Tags konnte der Garbage Collector die Eigenschaft `cq:MovedTo` nicht aktualisieren, wodurch das Tag von Seiten verschwand. (CQ-4358293) MAJOR
* Ein Problem mit ContextHub in AEM 6.5.19 führte dazu, dass Segmente falsch aufgelöst wurden, wenn einem AEM Kontextpfad hinzugefügt wurde. Das Problem betraf speziell das URL-Feld in den von der Seitenkomponente generierten JavaScript-Objekten, wo das erforderliche Kontextpfadpräfix fehlte. Diese Unterlassung verhinderte, dass Segmente erwartungsgemäß funktionieren. (SITES-21852)
* AEM Schnellstart wurde aktualisiert, um die Bibliothek `commons-collections-3.2.2-adobe-2` zu verwenden. Die Aktualisierung stellt sicher, dass die Anwendung reibungslos fortgesetzt werden kann. (NPR-42150)
* Das SMTP OAuth2-Setup in AEM 6.5 unterscheidet sich erheblich von dem, was in AEM as a Cloud Service verwendet wird. Um die Konfiguration zu optimieren und Konsistenz zu gewährleisten, musste die Einrichtung in AEM 6.5 an die in AEM as a Cloud Service verwendeten Standards angepasst werden. (GRANITE-53273)
* Wenn Sie auf das Symbol ![Kompass ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Compass_18_N.svg) > ![Projektsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Project_18_N.svg) Projekte geklickt und dann mit dem Mauszeiger über das Symbol ![Leiste links ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RailLeft_18_N.svg) ![Symbol &quot;Nach unten&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) gezeigt haben, trat ein schwerwiegender Akzent vor dem QuickInfo-Text &quot;Nur Inhalt&quot;auf. (CQ-4356633)

#### Sicherheit{#foundation-security-6522}

* Es wurden Probleme mit einer veralteten kryptografischen JSAFE-Bibliothek (Version 6.0.0) in AEM. Ein gepatchtes Bundle mit JSAFE-Version 6.2.5 ist in AEM 6.5.22 enthalten. (NPR-42006) CRITICAL
* Beim Überprüfen zulässiger Protokolle während der XSS-Prüfungen vergleichen Handler mit &quot;http&quot;und &quot;https&quot;. Die Eigenschaft `protocol` eines URL-Objekts gab diese Werte jedoch mit einem nachfolgenden Doppelpunkt zurück, z. B. `http:` und `https:`. Diese Abweichung führte zu Validierungsproblemen. Um eine genaue Analyse sicherzustellen, muss die Protokollprüfung durchgeführt werden, die erforderlich ist, um den Doppelpunkt zu berücksichtigen, oder die Vergleichslogik entsprechend angepasst werden.  (NPR-42119)
* Nach der Installation von AEM 6.5.21 (frühere Version AEM 6.5.19) auf IBM® WebSphere® Liberty Profile und Semeru Java 8.0 war es nicht möglich, Seiten zu öffnen. Fehlerprotokolle zeigten Probleme im Zusammenhang mit Servlet-Versionen an, die von verschiedenen Bundles benötigt werden. Um dieses Problem zu beheben, musste die Abhängigkeit von `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar` zurückgesetzt werden, da sie sich auf das Problem bezog. (NPR-42116)
* Mehrere Browser stellen die Unterstützung für Cookies vom Typ **SameSite=None** ein, die zum Ermöglichen des Site-übergreifenden Zugriffs auf Cookies verwendet werden. Alternativ wird **Partitionierte Cookies** eingeführt. Diese Cookies isolieren die Speicherung nach dem Kontext, in dem sie verwendet werden, und verbessern dadurch den Datenschutz und die Sicherheit, indem sie das Tracking über Sites hinweg verhindern und gleichzeitig zulassen, dass Cookies innerhalb bestimmter Partitionen funktionieren, z. B. in eingebetteten Inhalten von Drittanbietern. (GRANITE-51953)


<!-- #### Sling{#foundation-sling-6522}

* A -->


#### Übersetzung{#foundation-translation-6522}

* Unterstützung für kürzlich vorgenommene Änderungen an Kernkomponenten zu standardmäßigen Übersetzungsregeln hinzugefügt. (NPR-42029) CRITICAL
* Beim Export von XLIFF-Dateien in AEM Forms wurde ein Problem festgestellt. Bei Verwendung der Option **Auswahl als XLIFF exportieren (nur Zeichenfolgen)** wurde die Komponentensequenz nicht konsistent beibehalten. Die Sequenz bleibt jedoch beim Exportieren von XLIFF für eine bestimmte Sprache korrekt. Zwei Dateien wurden bereitgestellt, um das Problem zu demonstrieren: **DE-CH_Export.xliff** (korrekte Sequenz) und **String_Export.xliff** (falsche Sequenz). (NPR-42118) MAJOR


#### Benutzeroberfläche{#foundation-ui-6522}

* Die `coralui-component-dialog` änderte die Platzierung von `cq-dialog-actions`, was sich möglicherweise auf das Layout oder das Verhalten von Aktionsschaltflächen in Dialogfeldern in AEM auswirkte. (NPR-4294) BLOCKER
* Die Farbwählerfunktion in AEM funktionierte nicht. Beim Zugriff wurde ein leeres Modal angezeigt, das die Farbauswahl verhinderte. Dieses Problem trat nach der Installation von AEM 6.5.20 in der Staging-Umgebung auf. Die Farbauswahl funktionierte korrekt *vor* bis zur Aktualisierung. (NPR-42163)
* In ![Hammersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Hammer_18_N.svg) **Tools** > **Workflow** > **Modelle** > wählen Sie ein Modell > **Workflow starten** fehlte das Symbol Durchsuchen im Feld Payload im Dialogfeld **Workflow ausführen**. (NPR-42162)


<!-- #### WCM{#foundation-wcm-6522}

* A


#### Workflow{#foundation-workflow-6522}

* A 


## Install [!DNL Experience Manager] 6.5.22.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.22.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Service Pack-Download ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.22.0 mithilfe von Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.22.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
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
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.22.0 installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.22.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.22.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

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

UberJar für [!DNL Experience Manager] 6.5.22.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.21/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.22</version>
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

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6522}

* Inhaltsfragmente - Die Vorschau schlägt aufgrund des DoS-Schutzes für eine große Baumstruktur von Fragmenten fehl. Weitere Informationen finden Sie im Artikel [KB über die standardmäßigen Konfigurationsoptionen von GraphQL Query Executor](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934).


### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6522}


* Wenn Sie nach der Installation von AEM Forms JEE Service Pack 21 (6.5.21.0) doppelte Einträge von Geode-JAR-Dateien `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` unter dem Ordner `<AEM_Forms_Installation>/lib/caching/lib` (FORMS-14926) finden, führen Sie die folgenden Schritte durch, um das Problem zu beheben:

   1. Beenden der Locators, falls sie noch ausgeführt werden.
   1. Beenden des AEM-Servers.
   1. Wechseln zum Ordner `<AEM_Forms_Installation>/lib/caching/lib`.
   1. Entfernen aller Geode-Patch-Dateien außer `geode-*-1.15.1.2.jar`. Bestätigen, dass nur die Geode-JAR-Dateien mit `version 1.15.1.2` vorhanden sind.
   1. Öffnen der Eingabeaufforderung im Administratormodus.
   1. Installieren des Geode-Patches mithilfe der Datei `geode-*-1.15.1.2.jar`.

* Wenn Benutzende versuchen, einen Briefentwurf mit gespeicherten XML-Daten in der Vorschau anzuzeigen, bleibt er für bestimmte Buchstaben im `Loading`-Zustand hängen. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (FORMS-14521)

* Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 kann der `PaperCapture`-Dienst keine OCR-Vorgänge (Optical Character Recognition) für PDFs mehr durchführen. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (CQDOC-21680)

* Bei Benutzern, die von AEM 6.5 Forms Service Pack 18 oder 19 auf Service Pack 20 oder 21 aktualisiert wurden, trat ein JSP-Kompilierungsfehler auf. Dieser Fehler hinderte sie daran, adaptive Formulare zu öffnen oder zu erstellen. Es hat auch Probleme mit anderen AEM verursacht. Diese Schnittstellen umfassten den Seiteneditor, die AEM Forms-Benutzeroberfläche, den Workflow-Editor und die Benutzeroberfläche der Systemübersicht. (FORMS-15256)

  Wenn ein solches Problem auftritt, führen Sie die folgenden Schritte aus, um es zu beheben:
   1. Navigieren Sie in CRXDE zum Verzeichnis `/libs/fd/aemforms/install/`.
   1. Löschen Sie das Bundle `com.adobe.granite.ui.commons-5.10.26.jar`.
   1. Starten Sie den AEM-Server neu.

* Nach der Aktualisierung auf AEM Forms Service Pack 20 (6.5.20.0) mit dem Forms-Add-on funktionieren Konfigurationen, die auf den alten Adobe Analytics Cloud-Dienst mithilfe der berechtigungsbasierten Authentifizierung angewiesen sind, nicht mehr. Dieses Problem verhinderte die ordnungsgemäße Ausführung von Analytics-Regeln. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (FORMS-15428)

* Wenn ein Benutzer auf dem JEE-Server auf AEM Forms Service Pack 20 (6.5.20.0) aktualisiert und PDF mithilfe von Ausgabediensten generiert, werden die PDF mit Zugänglichkeitsproblemen gerendert. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922112)
* Wenn ein Benutzer mit dem Ausgabedienst auf JEE getaggte PDF generiert, wird die Meldung &quot;Unangemessene Strukturwarnung&quot;angezeigt. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922038)
* Wenn ein Formular auf AEM Forms JEE gesendet wird, werden die Instanzen eines sich wiederholenden XML-Elements aus den Daten entfernt. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3922017)
* Wenn ein Benutzer in einer Linux®-Umgebung ein adaptives Formular (auf JEE) auf dem HTML rendert, schlägt die Wiedergabe fehl. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921957)
* Wenn Benutzende mithilfe des Ausgabe-Services von AEM Forms JEE eine XTG-Datei in das PostScript-Format konvertieren, schlägt der Vorgang mit folgendem Fehler fehl: `AEM_OUT_001_003: Unexpected Exception: PAExecute Failure: XFA_RENDER_FAILURE`. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921720)
* Nach dem Upgrade auf AEM Forms Service Pack 18 (6.5.18.0) auf JEE Server wird ein von Benutzenden gesendetes Formular nicht als HTML5- oder PDF-Formular gerendert und XMLFM stürzt ab. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Artikel [Hotfixes für Adobe Experience Manager Forms](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms). (LC-3921718)
* In der Druckvorschau der Agent-Benutzeroberfläche für interaktive Kommunikationen wird das Währungssymbol (z. B. das Dollarzeichen $) für alle Feldwerte uneinheitlich angezeigt. Es wird für Werte bis 999 angezeigt, fehlt jedoch für Werte ab 1000. (FORMS-16557)
* Änderungen am XDP von verschachtelten Layout-Fragmenten in einer interaktiven Kommunikation werden nicht im Editor für interaktive Kommunikationen angezeigt. (FORMS-16575)
* In der Druckvorschau der Agent-Benutzeroberfläche für interaktive Kommunikationen werden einige berechnete Werte nicht korrekt angezeigt. (FORMS-16603)
* Wenn der Brief in der Druckvorschau angezeigt wird, wird der Inhalt geändert. Das heißt, einige Leerzeichen verschwinden und bestimmte Buchstaben werden durch &quot;x&quot;ersetzt (FORMS-15681).

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.22.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65210-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.22.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65210-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
