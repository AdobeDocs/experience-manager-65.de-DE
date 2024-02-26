---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
source-git-commit: 210299acf9f853a19bd513c84c1678e44ba81729
workflow-type: tm+mt
source-wordcount: '2456'
ht-degree: 98%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, November 30, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.20.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 22. Februar 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.20.0 enthalten ist {#what-is-included-in-aem-6520}

[!DNL Experience Manager] 6.5.20.0 enthält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

<!-- * _6.5.20.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* Dynamic Media unterstützt jetzt das verlustfreie HEIC-Bildformat für Apple iOS/iPadOS. Siehe [fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html?lang=de) in der Bildbereitstellungs- und Rendering-API von Dynamic Media.

* Der Multisite Manager (MSM) unterstützt jetzt Experience Fragment-Strukturen, einschließlich Ordnern und Unterordnern, für ein effizientes Massen-Rollout von Experience Fragments in Live Copies.

<!-- ### [!DNL Forms]

* text -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 20 {#fixed-issues}

### [!DNL Sites]{#sites-6520}

<!--#### Accessibility{#sites-accessibility-6520}

* text -->

#### Admin-Benutzeroberfläche{#sites-adminui-6520}

* Das Feld `Workflow Title` wird nach Bedarf mit `*` markiert, aber es gibt keine Validierung. (SITES-16491)

<!--#### Classic UI{#sites-classicui-6520}

* text -->

#### [!DNL Content Fragments]{#sites-contentfragments-6520}

* Verschachtelte Konfigurationsordner wurden nicht mehr unterstützt und Inhaltsfragment-Modellordner waren nach der Aktualisierung auf AEM 6.5.18 oder auf AEM 6.5.19 nicht mehr sichtbar. (SITES-18110)
* Einige Unterordner können nicht aus geerbten Inhaltsfragment-Modellen auswählen. Sie müssen Ordner unterstützen, ohne über eine `jcr:content`-Eigenschaft zu verfügen, auch wenn die über die Benutzeroberfläche erstellten DAM-Ordner einen solchen Knoten aufweisen. (SITES-17943)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6520}

<!-- REMOVED AS PER EMAIL FROM SAMEER DHAWAN FEBRUARY 19, 2024 * When upgrading AEM from 6.5.19.0 to 6.5.20.0, the path `/libs/cq/graphql/sites/graphiql` was getting deleted. (SITES-19530) CRITICAL -->
* Wenn eine GraphQL-Abfrage zum [Filtern von Ergebnissen](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#filtering) mit optionalen Variablen ausgeführt wird und **kein** bestimmter Wert für die optionale Variable angegeben ist, wird die Variable bei der Filterbewertung ignoriert. (SITES-17051)

<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6520}

* text -->

#### [!DNL Content Fragments] – REST-API{#sites-restapi-6520}

* Mit der Aktualisierung der `org.json`-Bibliothek wurde die Deserialisierung von Dezimalzahlen geändert. Vorher wurden sie „standardmäßig“ in „Double“ und jetzt in „BigDecimals“ umgewandelt.  Stattdessen sollten die Metadaten-Eigenschaftswerte, die über die REST-API gespeichert werden, von „BigDecimal“ in „Double“ konvertiert werden. (SITES-16857)

#### Core-Backend{#sites-core-backend-6520}

* Wenn die Funktion „Quick Publish“ eines Inhaltsfragments verwendet wird, wird das Fragment weiter geladen und nicht veröffentlicht. Das heißt, nach einer Service Pack-Aktualisierung von AEM 6.5.7 auf AEM 6.5.17 funktioniert die Funktion „Quick Publish“ nicht für Inhaltsfragmente. Als die Person es mit einer verwalteten Veröffentlichung versuchte, funktionierte dies zwar,  als sie jedoch versuchte, die Funktion „Quick Publish“ zu verwenden, wurde die Veröffentlichung nicht durchgeführt.  Genau gesagt: `com.day.cq.wcm.core.impl.reference.ActivationReferenceSearchBuilder` hat den Absturz des Systems verursacht. (SITES-17311)
* Inhaltsfragmente können mit Jackson Exporter nicht serialisiert werden: Das Laden der Seite bricht ab, wenn ein Inhaltsfragment auf einer Seite referenziert ist (verwendet Jackson Exporter-Code) und ein beliebiges Tag zu einem Inhaltsfragment hinzugefügt wird. (SITES-18096)

#### Kernkomponenten{#sites-core-components-6520}

* Das Installieren des CIF-Kernkomponenten-Pakets auf AEM führt dazu, dass sich der Wert `:type` von vorhandenen Komponenten ändert. Diese Änderung bedeutet, dass sie nicht mehr auf Seiten gerendert werden, zu denen sie hinzugefügt wurden. (SITES-17601)

#### Campaign-Integration{#sites-campaign-integration-6520}

* AEM verwendete eine Zulassungsliste – auch bekannt als `whitelist` – aufgrund eines Berichts über Sicherheitslücken. Die Zulassungsliste hinderte Kundinnen und Kunden daran, die benötigten Funktionen zu verwenden. (SITES-16822)

#### Experience Fragments{#sites-experiencefragments-6520}

* MSM für Experience Fragments unterstützt jetzt den Massen-Rollout für Experience Fragment-Inhaltsstrukturen, einschließlich Ordnern und Unterordnern. (SITES-16004)

<!--#### Foundation Components (Legacy){#sites-foundation-components-legacy-6520}

* text

#### Launches{#sites-launches-6520}

* text -->

#### MSM – Live Copies{#sites-msm-live-copies-6520}

* Beim Rollout der Komponente wird eine Ausnahme „`Is not modifiable`“ ausgelöst. Während der Reaktionsverarbeitung tritt insbesondere eine Ausnahme `org.apache.sling.servlets.post.impl.operations.ModifyOperation` auf. (SITES-18809)
* Es können keine Änderungen an bestimmten Live Copies von Experience Fragments vorgenommen werden. (SITES-17930)
* Wenn jemand einer Komponente auf einer Blueprint-Seite eine Anmerkung hinzufügt und sie dann ausrollt, wird die Anzahl der Anmerkungen auf der Live Copy falsch angezeigt. (SITES-17099)
* Die Schaltfläche „MSM-Rollout“ von der übergeordneten Seite zur untergeordneten Seite ist in der grafischen Touch-Benutzeroberfläche fehlerhaft. Bei Auswahl der Schaltfläche wird der folgende Fehler angezeigt: `Uncaught TypeError: _g.shared is undefined`. (SITES-16991)

#### Seiteneditor{#sites-pageeditor-6520}

* Die Vorschau des Forms Design-Editors ist fehlerhaft. Wenn die Vorschau ausgewählt ist, wird nur ein Ladesymbol angezeigt. (SITES-17164)

### [!DNL Assets]{#assets-6520}

* Regelbasierte Felder können nicht im Metadateneditor-Hilfsprogramm validiert werden und es wird eine Fehlermeldung „Fehlende erforderliche Felder“ angezeigt. (ASSETS-31396)
* Nachdem eine PDF-Datei an einen anderen Speicherort verschoben wurde, verschwindet die Option **[!UICONTROL Seite anzeigen]**. (ASSETS-30538)
* Ein Bild mit Leseberechtigungen kann nicht ausgewählt werden. (ASSETS-32199)
* Die Kartengröße kann in den Anzeigeeinstellungen nicht geändert werden. (ASSETS-31667)
* Upload schlägt beim Hochladen einer .oft-Datei fehl. (ASSETS-30109)
* Beim Versuch, ein benutzerdefiniertes Metadatenfeld als zusätzliche Spalte zum Bericht hinzuzufügen, werden die Kontrollkästchen nicht aktiviert. (ASSETS-31671)
* Der Vorgang zum Verschieben von Assets funktioniert in Experience Manager Service Pack 16 nicht ordnungsgemäß. (ASSETS-30598)

#### [!DNL Dynamic Media]{#assets-dm-6520}

* Nachdem ein Asset in AEM hochgeladen wurde, wird der Workflow `Update_asset` ausgelöst. Der Workflow wird aber nie abgeschlossen. Der Workflow wird nur bis zum Schritt zum Hochladen des Produkts abgeschlossen. Der nächste Schritt ist der Scene7-Batch-Upload, aber dieser Prozess wird nicht in AEM übertragen. (ASSETS-30443)
* Es besteht Bedarf für eine bessere Möglichkeit zur angemessenen Handhabung von Nicht-Dynamic Media-Videos in der Dynamic Media-Komponente. Dieses Problem führte zu einer Ausnahme, bei der `dynamicmedia_sly.js` instanziiert wurde.  (ASSETS-31301)
* Die Vorschau funktioniert für alle Assets, adaptiven Videosets und Videos. Es wird jedoch ein 403-Fehler für `.m3u8`-Dateien ausgelöst (die übrigens über öffentliche Links noch funktionieren). (ASSETS-31882)
* Der Status `scene7SmartCropProcessingStatus` wurde korrigiert. Beim intelligenten Zuschneiden von Videometadaten wurde ein Fehler angezeigt, selbst wenn der Vorgag erfolgreich war. (ASSETS-31255)

### [!DNL Forms]{#forms-6520}

Die Fehlerbehebungen in [!DNL Experience Manager] Forms werden eine Woche nach dem geplanten Veröffentlichungsdatum des [!DNL Experience Manager] Service Packs über ein separates Add-on-Paket bereitgestellt. In diesem Fall ist die Paket-Version des AEM Forms-Add-Ons 6.5.20.0 für Donnerstag, den 29. Februar 2024 geplant. Nach der Veröffentlichung wird diesem Abschnitt eine Liste mit Forms-Fehlerbehebungen und -Verbesserungen hinzugefügt.

<!-- #### [!DNL Adaptive Forms] -->

<!--LEFT BULLET LIST HERE IN CASE OF REUSE BY FORMS IN THE FUTURE 
* **Document Services**
  * text
* **Adaptive Forms** 
  * text
* **Accessibility**
  * text
* **Interactive Communications**
  * text -->

<!--### Commerce{#commerce-6520}

* text -->

### Fundament {#foundation-6520}

#### Communities {#communities-6520}

* Die Diagnose der Benutzersynchronisierung schlägt nach einer erfolgreichen Konfiguration der Benutzersynchronisierung fehl. (NPR-41693)

<!-- #### Content distribution{#foundation-content-distribution-6520}

* text -->

#### Integrationen{#integrations-6520}

* Entfernen Sie sämtlichen Code und alle Abhängigkeiten von Adobe Search&amp;Promote aus AEM 6.5. (NPR-40856)

#### Lokalisierung{#localization-6520}

* Aria-label „close“ ist in „**[!UICONTROL Assets]** > **[!UICONTROL Dateien]**“ nicht lokalisiert. Wählen Sie einen Ordner und dann in der Symbolleiste **[!UICONTROL Eigenschaften]** > Registerkarte **[!UICONTROL Berechtigungen]** > Mitgliedsname aus. (NPR-41705)
* Es gibt eine abgeschnittene QuickInfo für das Feld **[!UICONTROL Keystore-Kennwort]** auf der SSL-Setup-Seite für die Gebietsschemata ENG, FRA, KOR, DEU und PTB. (NPR-41367)

#### Platform{#foundation-platform-6520}

* Problem bei der Integration von Campaign mit AEM, welches durch das /api-Servlet verursacht wurde, das nicht das richtige Schema in der href json zurückgibt. Der Grund dafür war, dass AEM den Header „X-Forward-Proto“ nicht empfing, was die Anfrage zwang, mit einem HTTP-Schema anstelle von HTTPS zu antworten. Daher sollte die Möglichkeit zum Umschalten der Schemaauswahl basierend auf einer OSGi-Konfiguration hinzugefügt werden. (GRANITE-48454)

#### Sling{#foundation-sling-6520}

* Das `org.apache.sling.resourceMerger`-Bundle 1.4.2 löst eine Ausnahme bei AEM 6.5, Service Pack 17 und höher aus. Der Sling Resource Merger 1.4.4 sollte im Service Pack 20 enthalten sein. (NPR-41630)

#### Übersetzung{#foundation-translation-6520}

* Nach der Bereitstellung von AEM 6.5 Service Pack 18 trat ein Problem mit der Registerkarte „Filter“ im Editor für Übersetzungsregeln auf. Wenn ein Kontext ausgewählt ist, erscheint durch Klicken auf „Bearbeiten“ > „Speichern“ beim nächsten Öffnen desselben Kontexts ein doppeltes Anführungszeichen als HTML-Zeichen.  Im Grunde wurden die Übersetzungsregeln nicht korrekt gespeichert. (NPR-41624)
* Probleme im Zusammenhang mit Inhaltsfragment-Übersetzungen, bei denen die übersetzten Zeichenfolgen vom Übersetzungsanbieter an AEM zurückgesendet werden, aber auf der Ebene `/content/projects` stecken bleiben und die Inhaltsfragmente nicht aktualisiert wurden. (NPR-41516)
* Beim Erstellen einer Sprachkopie wird eine Fehlermeldung angezeigt. Sie tritt auf einer Seite auf, die ein Inhaltsfragment enthält, auf das mit Inhaltsfragmentmodellen in einer Seiteneigenschaft verwiesen wird.  (NPR-41441)
* Links in Experience Fragments werden während der Sprachkopie nicht an die richtige Sprache angepasst. Stattdessen verweist das Experience Fragment auf das primäre Gebietsschema. (NPR-41343)

#### Benutzeroberfläche{#foundation-ui-6520}

* Nach einem Upgrade auf AEM 6.5 Service Pack 18 tritt ein Konsolenfehler auf. Der Fehler befindet sich in der Datei `coralUI3.js` und tritt auf, wenn Sie ein beliebiges Dropdown-Menü in AEM auswählen. Dies tritt insbesondere bei einem `onOverlayToggle`-Ereignis auf. Der Fehler `Uncaught TypeError: Cannot read properties of null (reading 'innerText')` wird angezeigt. (NPR-41467)
* Werden in AEM unter **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Tagging]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Tag erstellen]** nicht-lateinische Zeichen im Feld **Titel** eingegeben, führt dies dazu, dass das Feld **Name** nur mit dem Bindestrichzeichen ( `-` ) ausgefüllt wird. (NPR-41623)
* Das Copyright-Jahr im Dialogfeld `About Adobe Experience Manager` ist falsch. (NPR-41526)
* Beim Bearbeiten von Benutzereinstellungen gibt es unübersetzte **[!UICONTROL Profileigenschaften]**-Zeichenfolgen. Tritt in allen Gebietsschemata auf. (NPR-41365)

<!-- #### WCM{#wcm-6520}

* text

#### Workflow{#foundation-workflow-6520}

* text -->

## Installieren von [!DNL Experience Manager] 6.5.20.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.20.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.20.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.20.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs auf [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) herunter.<!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.20.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.20.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.20.0)` unter [!UICONTROL Installierte Produkte] an.<!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.18 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Installation des Service Packs für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/deploying/deploy.html?lang=de), dient nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen.

Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.20.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.20/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.20</version>
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

* Ab AEM 6.5.15 weist die vom Bundle ```org.apache.servicemix.bundles.rhino``` bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten auf. Skripte, die den strikten Modus (```use strict;```) verwenden, müssen ihre Variablen korrekt deklarieren, sonst werden sie nicht ausgeführt, sondern es wird ein Laufzeitfehler ausgegeben.

### Bekannte Probleme bei AEM Forms

Bekannte Probleme in [!DNL Experience Manager] Forms wird eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Veröffentlichungsdatum des Service Packs. In diesem Fall ist die Paket-Version des AEM Forms-Add-Ons 6.5.20.0 für Donnerstag, den 29. Februar 2024 geplant. Eine Liste bekannter Probleme für Formulare wird diesem Abschnitt nach der Veröffentlichung hinzugefügt.

<!--

#### Supported platforms 

* JDK 11.0.20 is not supported to install AEM Forms on JEE Installer. Only JDK 11.0.19 or earlier versions are supported to install AEM Forms on JEE Installer. (FORMS-10659)

#### Installation 

* On JBoss&reg; 7.1.4 platform, when user installs Experience Manager 6.5.16.0 or later service pack, `adobe-livecycle-jboss.ear` deployment fails. (CQ-4351522, CQDOC-20159)

<!-- 
* After upgrading to AEM Forms 6.5.18.0 JBoss&reg; Turnkey full installer environment on Windows Server 2022, when compiling Output client application code using Java&trade; 11, the following compilation error may occur:
  
  ```
  error: error reading [AEM_Forms_Installation_dir]\sdk\client-libs\common\adobe-output-client.jar; java.net.URISyntaxException: 
  Illegal character in path at index 70: file:/[AEM_Forms_Installation_dir]/sdk/client-libs/common/${clover.jar.name} 1 error
  
  ```
  
  To resolve the issue, perform the following steps:
    1. Navigate to `[AEM_Forms_Installation_dir]\sdk\client-libs\common\` and unzip `adobe-output-client.jar` to extract the `Manifest.mf` file.
    1. Update the `Manifest.mf` file by removing the entry `${clover.jar.name}` from the class-path attribute. 

        >[!NOTE]
        >
        > You can also use an in-place editing tool, for example, 7-zip, to update the `Manifest.mf` file.  

    1. Save the updated the `Manifest.mf` in the `adobe-output-client.jar` archive. 
    1. Save the modified `adobe-output-client.jar` file and rerun the setup. (CQDOC-20878) 

* After installing AEM Service Pack 6.5.20.0 full installer, the EAR deployment fails on JEE using JBoss&reg; Turnkey. UPDATE FOR EACH NEW RELEASE To resolve the issue, locate the AEM_Forms_Installation_dir\jboss\bin\standalone.bat file and update `Adobe_Adobe_JAVA_HOME` to `Adobe_JAVA_HOME` for all occurrences before running the configuration manager. (CQDOC-20803).

#### Install the servlet fragment (AEM Service Pack 6.5.14.0 or earlier)

* If you are upgrading to AEM Service Pack 6.5.15.0 or higher, and your AEM instance is operating on Tomcat 8.5.88, it is mandatory that you install the servlet fragment. Do this install *before* you proceed with the installation of Service Pack 6.5.15.0 or higher.
* It is mandatory that you install the servlet fragment for all application servers except those running on JBoss&reg; EAP 7.4.0.

**To install the servlet fragment:**

1. Download the servlet fragment from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).
1. Start the application server. 
1. Wait for the logs to stabilize and check the bundle state.
1. Open Web Console Bundles. The default URL is `http://[Server]:[Port]/system/console/bundles`.
1. Select **[!UICONTROL Install]** or **[!UICONTROL Update]**. 
1. Select the downloaded fragment 
`org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar` 
1. Select **[!UICONTROL Install]** or **[!UICONTROL Update]**. 
1. Wait for the application server to stabilize.
1. Stop the application server.

#### Adaptive Forms

* When an Adaptive Form is published, all its dependencies, including policies, get republished, even if no modifications have been made to them. (FORMS-10454)
* When a user selects to configure a field for the first time in an adaptive form, the option to save a configuration does not display in Properties Browser. Selecting to configure some other field of the Adaptive Form in the same editor resolves the issue. 
* When users perform the submit action, the submission fails with an error: 
`javax.servlet.ServletException: java.lang.NoSuchMethodError`
To resolve the issue, [recompile the Sling scripts such as JSP, Java&trade;, and Sightly](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html#resolution). (FORMS-8542)
* After installing AEM Service Pack 6.5.14.0 and onwards, users are unable to select a font from the JEE Admin UI for PDF documents when navigating to `Home` > `Services` > `PDF Generator` > `Adobe PDF Settings`, as the font list appears empty. (FORMS-12095)
 When a form is signed using the OOTB Scribble Signature component, it appears in the image dialogue but does not preview and appears blank when you click on it. (FORMS-12073). A hotfix is available for this issue. To download and install the hotfix, see [Adobe Experience Manager Forms Hotfixes](/help/release-notes/aem-forms-hotfix.md) 
* On AEM Forms on JEE, the HTML5 Forms that use the context path, fail to render. (FORMS-12485, FORMS-12691). A hotfix is available for this issue. To download and install the hotfix, see [Adobe Experience Manager Forms Hotfixes](/help/release-notes/aem-forms-hotfix.md).
* Adaptive Forms let you use custom functions with ECMAScript version 5 or earlier. When a custom function uses ECMAScript version 6 or later, like 'let', 'const', or arrow functions, the rule editor might not open properly.

#### AEM Forms on JEE 

* Critical security vulnerabilities have been reported for Struts 2 RCE, a popular and open-source web application framework for developing Java&trade; EE web applications. Adobe has released [AEM 6.5 Service Pack 19.1 (6.5.19.1)](/help/forms/using/mitigating-struts-2-rce-vulnerabilities-for-experience-manager-manager-form.md) to address the vulnerability in AEM Forms on JEE. 

The font enumeration fails due to the missing Ps2Pdf service file.-->

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.20.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65200-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.20.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65200-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
