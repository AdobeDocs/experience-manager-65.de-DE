---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
source-git-commit: 19fe527ce44d8ec5be50ebd32b46f13df96c52cc
workflow-type: tm+mt
source-wordcount: '2928'
ht-degree: 58%

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
| Version | 6,5,20,0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Freitag, 22. Februar 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.20.0 enthalten ist {#what-is-included-in-aem-6520}

[!DNL Experience Manager] 6.5.20.0 enthält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

<!-- * _6.5.20.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* Dynamic Media unterstützt jetzt verlustfreies HEIC-Bildformat für Apple iOS/iPadOS. Siehe [fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html?lang=en) in der Dynamic Media Image Serving and Rendering API.

* Der Multisite Manager (MSM) unterstützt jetzt Experience Fragment-Strukturen, einschließlich Ordnern und Unterordnern, für eine effiziente Massenaktualisierung von Experience Fragments in Live Copies.

<!-- ### [!DNL Forms]

* text -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 20 {#fixed-issues}

### [!DNL Sites]{#sites-6520}

<!--#### Accessibility{#sites-accessibility-6520}

* text -->

#### Admin-Benutzeroberfläche{#sites-adminui-6520}

* Die `Workflow Title` -Feld mit `*` nach Bedarf, aber es gibt keine Validierung. (SITES-16491) NORMAL

<!--#### Classic UI{#sites-classicui-6520}

* text -->

#### [!DNL Content Fragments]{#sites-contentfragments-6520}

* Verschachtelte Konfigurationsordner wurden nicht mehr unterstützt und Inhaltsfragmentmodellordner waren nach der Aktualisierung auf AEM 6.5.18 oder auf AEM 6.5.19 nicht mehr sichtbar. (SITES-18110) MAJOR
* Einige Unterordner können nicht aus geerbten Inhaltsfragmentmodellen auswählen. Es muss Ordner unterstützen, ohne dass eine `jcr:content` -Eigenschaft, auch wenn die über die Benutzeroberfläche erstellten DAM-Ordner einen solchen Knoten aufweisen. (SITES-17943) NORMAL

#### [!DNL Content Fragments] - GraphQL-API {#sites-graphql-api-6520}

<!-- REMOVED AS PER EMAIL FROM SAMEER DHAWAN FEBRUARY 19, 2024 * When upgrading AEM from 6.5.19.0 to 6.5.20.0, the path `/libs/cq/graphql/sites/graphiql` was getting deleted. (SITES-19530) CRITICAL -->
* Beim Ausführen einer GraphQL-Abfrage in [Filterergebnisse](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#filtering) Verwendung optionaler Variablen, wenn ein bestimmter Wert **not** für die optionale Variable angegeben ist, wird die Variable bei der Filterbewertung ignoriert. (SITES-17051) NORMAL

<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6520}

* text -->

#### [!DNL Content Fragments] - REST-API{#sites-restapi-6520}

* Mit der Aktualisierung der `org.json` -Bibliothek wurde die Deserialisierung von Dezimalzahlen geändert. Bevor sie &quot;standardmäßig&quot;in &quot;Dubletten&quot;und jetzt in &quot;BigDecimals&quot;umgewandelt wurden. Stattdessen sollten die Metadaten-Eigenschaftswerte, die über die REST-API gespeichert werden, aus BigDecimal in Double konvertiert werden. (SITES-16857) NORMAL

#### Core-Backend{#sites-core-backend-6520}

* Wenn die Funktion &quot;Quick Publish&quot;eines Inhaltsfragments verwendet wird, wird das Fragment weiter geladen und nicht veröffentlicht. Das heißt, Quick Publish funktioniert nach einem Service Pack-Upgrade von AEM 6.5.7 auf AEM 6.5.17 nicht für Inhaltsfragmente. Als der Benutzer die verwaltete Veröffentlichung versuchte, funktionierte sie. Als sie jedoch Quick Publish ausprobierten, wurde es nicht veröffentlicht. Insbesondere gilt: `com.day.cq.wcm.core.impl.reference.ActivationReferenceSearchBuilder` verursacht hat, dass das System verprügelte. (SITES-17311) MAJOR
* Inhaltsfragmente können mit Jackson Exporter nicht serialisiert werden: Das Laden der Seite bricht ab, wenn ein Inhaltsfragment auf einer Seite referenziert ist (verwendet Jackson Exporter-Code) und ein beliebiges Tag, das zu einem Inhaltsfragment hinzugefügt wurde. (SITES-18096) NORMAL

#### Kernkomponenten{#sites-core-components-6520}

* Installieren CIF Kernkomponenten-Pakets auf AEM Ursachen `:type` Wert vorhandener Komponenten, die geändert werden sollen. Die Änderung bedeutet, dass sie nicht mehr auf Seiten gerendert werden, zu denen sie hinzugefügt wurden. (SITES-17601) MAJOR

#### Campaign-Integration{#sites-campaign-integration-6520}

* AEM verwendet eine Zulassungsliste, auch bekannt als `whitelist`-aufgrund eines Verwundbarkeitsberichts. Die Zulassungsliste vom Typ &quot;&quot;hinderte Kunden daran, die benötigten Funktionen zu verwenden. (SITES-16822) CRITICAL

#### Experience Fragments{#sites-experiencefragments-6520}

* MSM für Experience Fragments unterstützt jetzt den Massen-Rollout für Experience Fragment-Inhaltsstrukturen, einschließlich Ordnern und Unterordnern. (SITES-16004) MAJOR

<!--#### Foundation Components (Legacy){#sites-foundation-components-legacy-6520}

* text

#### Launches{#sites-launches-6520}

* text -->

#### MSM – Live Copies{#sites-msm-live-copies-6520}

* Ein &quot;`Is not modifiable`&quot;Ausnahme wird beim Rollout der Komponente ausgelöst. Insbesondere wird ein `org.apache.sling.servlets.post.impl.operations.ModifyOperation` Ausnahmeerscheinungen während der Reaktionsverarbeitung auftreten. (SITES-18809) MAJOR
* Es können keine Änderungen an bestimmten Live Copies von Experience Fragments vorgenommen werden. (SITES-17930) MAJOR
* Wenn ein Benutzer einer Komponente auf einer Blueprint-Seite eine Anmerkung hinzufügt und sie dann ausrollt, wird die Anzahl der Anmerkungen auf der Live Copy falsch angezeigt. (SITES-17099) MAJOR
* Die Schaltfläche &quot;MSM-Rollout&quot;von der übergeordneten Seite zur untergeordneten Seite ist in der Touch-grafischen Benutzeroberfläche fehlerhaft. Bei Auswahl dieser Option wird der folgende Fehler angezeigt: `Uncaught TypeError: _g.shared is undefined`. (SITES-16991) MAJOR

#### Seiteneditor{#sites-pageeditor-6520}

* Die Vorschau des Forms Design-Editors ist fehlerhaft. Wenn Vorschau ausgewählt ist, wird nur ein Ladesymbol angezeigt. (SITES-17164) BLOCKER

### [!DNL Assets]{#assets-6520}

* Regelbasierte Felder können nicht im Metadateneditor-Hilfsprogramm validiert werden und es wird eine Fehlermeldung &quot;Fehlende erforderliche Felder&quot;angezeigt. (ASSETS-31396) MAJOR
* Nachdem eine PDF an einen anderen Ort verschoben wurde, wird die **[!UICONTROL Seite anzeigen]** -Option verschwindet. (ASSETS-30538) MAJOR
* Bild mit Leseberechtigungen kann nicht ausgewählt werden. (ASSETS-32199) NORMAL
* Die Kartengröße kann in den Anzeigeeinstellungen nicht geändert werden. (ASSETS-31667) NORMAL
* Upload schlägt beim Hochladen des Dateityps .oft fehl. (ASSETS-30109) NORMAL
* Wenn Sie versuchen, ein benutzerdefiniertes Metadatenfeld als zusätzliche Spalte zum Bericht hinzuzufügen, werden die Kontrollkästchen nicht aktiviert. (ASSETS-31671) MINOR
* Der Vorgang zum Verschieben von Assets funktioniert in Experience Manager Service Pack 16 nicht ordnungsgemäß. (ASSETS-30598) MINOR

#### [!DNL Dynamic Media]{#assets-dm-6520}

* Wenn ein Asset in AEM hochgeladen wird, wird die `Update_asset` Workflow ausgelöst. Der Workflow wird jedoch nie abgeschlossen. Der Workflow wird nur bis zum Schritt zum Hochladen des Produkts abgeschlossen. Der nächste Schritt ist der Scene7-Batch-Upload, aber dieser Prozess wird nicht in AEM übertragen. (ASSETS-30443) CRITICAL
* Benötigen Sie eine bessere Möglichkeit, Nicht-Dynamic Media-Videos in der Dynamic Media-Komponente mit Ansehen zu behandeln. Dieses Problem führte zu einer Ausnahmeinstanz `dynamicmedia_sly.js`. (ASSETS-31301) MAJOR
* Die Vorschau funktioniert für alle Assets, adaptiven Videosets und Videos. Es wird jedoch ein 403-Fehler für `.m3u8` -Dateien (die übrigens noch über öffentliche Links funktionieren). (ASSETS-31882) MAJOR
* Die `scene7SmartCropProcessingStatus` Status korrigiert. Smartes Zuschneiden von Videometadaten, die verwendet werden, um Fehler zu zeigen, selbst wenn sie erfolgreich waren. (ASSETS-31255) MINOR

### [!DNL Forms]{#forms-6520}

Die Fehlerbehebungen in [!DNL Experience Manager] Forms werden eine Woche nach dem geplanten Veröffentlichungsdatum des [!DNL Experience Manager] Service Packs über ein separates Add-on-Paket bereitgestellt. In diesem Fall ist die AEM Forms-Add-On-Paket-Version 6.5.20.0 für Donnerstag, den Freitag, 29. Februar 2024 geplant. In diesem Abschnitt wird nach der Veröffentlichung eine Liste der Forms-Fehlerbehebungen und -Verbesserungen hinzugefügt.

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

#### [!DNL Forms Designer]{#forms-designer-6520}

* text

<!-- ### Foundation{#foundation-6520}

* text -->

#### Communitys {#communities-6520}

* Die Diagnose der Benutzersynchronisierung schlägt nach der erfolgreichen Konfiguration der Benutzersynchronisierung fehl. (NPR-41693) NORMAL

<!-- #### Content distribution{#foundation-content-distribution-6520}

* text -->

#### Integrationen{#integrations-6520}

* Entfernen Sie sämtlichen Code und alle Abhängigkeiten von Adobe Search&amp;Promote aus AEM 6.5. (NPR-40856) NORMAL

#### Lokalisierung{#localization-6520}

* Aria-label &quot;close&quot;ist nicht lokalisiert in **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**, wählen Sie einen Ordner aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]** > **[!UICONTROL Berechtigungen]** tab > Mitgliedsname. (NPR-41705) MAJOR
* Es gibt eine abgeschnittene QuickInfo für die **[!UICONTROL Key Store Password]** auf der SSL-Setup-Seite für die Gebietsschemata ENG, FRA, KOR, DEU und PTB. (NPR-41367) NORMAL

<!-- #### Oak{#oak-6520}

* text -->

#### Platform{#foundation-platform-6520}

* Problem bei der Integration von Campaign mit AEM, die durch das /api-Servlet verursacht wurden, das nicht das richtige Schema in der href json zurückgibt. Der Grund dafür war, dass AEM den Header X-Forward-Proto nicht erhielt, der die Anfrage zwang, mit einem HTTP-Schema anstelle von HTTPS zu antworten. Daher sollte die Möglichkeit hinzugefügt werden, die Schemaauswahl basierend auf einer OSGi-Konfiguration umzuschalten. (GRANITE-48454) MAJOR

<!-- #### Replication{#foundation-replication-6520}

* text -->

#### Sling{#foundation-sling-6520}

* Die `org.apache.sling.resourceMerger` Bundle 1.4.2 gibt eine Ausnahme von AEM 6.5, Service Pack 17 und höher aus. Der Sling Resource Merger 1.4.4 sollte im Service Pack 20 enthalten sein. (NPR-41630) NORMAL

#### Übersetzung{#foundation-translation-6520}

* Nach der Bereitstellung von AEM 6.5 Service Pack 18 trat ein Problem mit der Registerkarte Filter im Editor für Übersetzungsregeln auf. Wenn ein Kontext ausgewählt ist und auf Bearbeiten > Speichern klickt, wird beim nächsten Öffnen desselben Kontexts ein doppeltes Anführungszeichen als HTML angezeigt. Im Grunde wurden die Übersetzungsregeln nicht korrekt gespeichert. (NPR-41624) MAJOR
* Probleme im Zusammenhang mit Inhaltsfragmentübersetzungen, bei denen die übersetzten Zeichenfolgen vom Übersetzungsanbieter an AEM zurückgesendet werden, aber bei der `/content/projects` und nicht die Aktualisierung der Inhaltsfragmente. (NPR-41516) MAJOR
* Beim Erstellen einer Sprachkopie wird eine Fehlermeldung angezeigt. Sie tritt auf einer Seite auf, auf die mithilfe von Inhaltsfragmentmodellen in einer Seiteneigenschaft auf ein Inhaltsfragment verwiesen wird. (NPR-41441) MAJOR
* Links in Experience Fragments werden während der Sprachkopie nicht an die richtige Sprache angepasst. Stattdessen verweist das Experience Fragment auf das primäre Gebietsschema. (NPR-41343) NORMAL

#### Benutzeroberfläche{#foundation-ui-6520}

* Nach einem Upgrade auf AEM 6.5 Service Pack 18 tritt ein Konsolenfehler auf. Der Fehler befindet sich im `coralUI3.js` und wird angezeigt, wenn Sie ein beliebiges Dropdown-Menü in AEM auswählen. Insbesondere geschieht dies mit einem `onOverlayToggle` -Ereignis. Der Fehler `Uncaught TypeError: Cannot read properties of null (reading 'innerText')` angezeigt. (NPR-41467) MAJOR
* AEM **[!UICONTROL Instrumente]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Tagging]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Tag erstellen]**, wobei nicht lateinische Zeichen in die **Titel** -Feld verursacht die **Name** -Feld, das nur mit dem Bindestrichzeichen ( `-` ). (NPR-41623) NORMAL
* Das Copyright-Jahr ist in der `About Adobe Experience Manager` Dialogfeld. (NPR-41526) NORMAL
* Unübersetzt **[!UICONTROL Profileigenschaften]** Zeichenfolgen beim Bearbeiten von Benutzereinstellungen. Tritt in allen Gebietsschemata auf. (NPR-41365) NORMAL

<!-- #### WCM{#wcm-6520}

* text

#### Workflow{#foundation-workflow-6520}

* text -->

## Installieren von [!DNL Experience Manager] 6.5.20.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.20.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.20.0 mit dem Package Manager auf einer der Authoring-Instanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

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

1. Das OSGi-Paket `org.apache.jackrabbit.oak-core` ist Version 1.22.18 oder höher (Webkonsole verwenden: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Installation des Service Packs für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/deploying/deploy.html), dient nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

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

#### Unterstützte Plattformen

* JDK 11.0.20 wird zur Installation des AEM Forms auf JEE-Installationsprogramms nicht unterstützt. Nur JDK 11.0.19 oder frühere Versionen werden zur Installation des AEM Forms auf JEE-Installationsprogramms unterstützt. (FORMS-10659)

#### Installation

* Auf der Plattform JBoss® 7.1.4 schlägt die Bereitstellung fehl, wenn Experience Manager 6.5.16.0 oder ein höheres Service Pack installiert wird. `adobe-livecycle-jboss.ear` (CQ-4351522, CQDOC-20159)

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
    1. Save the modified `adobe-output-client.jar` file and rerun the setup. (CQDOC-20878) -->

* Nach der Installation des vollständigen Installationsprogramms für AEM Service Pack 6.5.20.0 schlägt die EAR-Bereitstellung auf JEE mit JBoss® Turnkey fehl. <!-- UPDATE FOR EACH NEW RELEASE -->

Um das Problem zu beheben, suchen Sie die Datei `<AEM_Forms_Installation_dir>\jboss\bin\standalone.bat` und aktualisieren Sie alle Vorkommen von `Adobe_Adobe_JAVA_HOME` auf `Adobe_JAVA_HOME`, bevor Sie den Konfigurations-Manager ausführen. (CQDOC-20803)

#### Installation des Servlet-Fragments (AEM Service Pack 6.5.14.0 oder früher)

* Wenn Sie ein Upgrade auf AEM Service Pack 6.5.15.0 oder höher durchführen und Ihre AEM-Instanz auf Tomcat 8.5.88 läuft, müssen Sie das Servlet-Fragment installieren. Führen Sie diese Installation durch *before* Sie fahren mit der Installation von Service Pack 6.5.15.0 oder höher fort.
* Die Installation des Servlet-Fragments ist obligatorisch für alle Anwendungs-Server, mit Ausnahme derer, die auf JBoss® EAP 7.4.0 laufen.

**So installieren Sie das Servlet-Fragment:**

1. Laden Sie das Servlet-Fragment von der [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) herunter.
1. Starten Sie den Anwendungs-Server.
1. Warten Sie, bis sich die Protokolle stabilisieren, und überprüfen Sie den Status des Bundles.
1. Öffnen Sie Web-Konsole Bundles. Die Standard-URL ist `http://[Server]:[Port]/system/console/bundles`.
1. Klicken Sie auf **[!UICONTROL Installieren]** oder **[!UICONTROL Aktualisieren]**.
1. Wählen Sie das heruntergeladene Fragment aus
   `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`
1. Klicken Sie auf **[!UICONTROL Installieren]** oder **[!UICONTROL Aktualisieren]**.
1. Warten Sie, bis sich der Anwendungs-Server stabilisiert hat.
1. Stoppen Sie den Anwendungs-Server.

#### Adaptive Formulare

* Wenn ein adaptives Formular veröffentlicht wird, werden alle Abhängigkeiten, einschließlich Richtlinien, erneut veröffentlicht, selbst wenn keine Änderungen an ihnen vorgenommen wurden. (FORMS-10454)
* Wenn Benutzende ein Feld erstmals in einem adaptiven Formular konfigurieren möchten, wird im Eigenschaften-Browser die Option zum Speichern einer Konfiguration nicht angezeigt. Das Problem lässt sich beheben, indem Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren.
* Wenn Benutzende die Sendeaktion durchführen, schlägt die Übermittlung mit einer Fehlermeldung fehl:
  `javax.servlet.ServletException: java.lang.NoSuchMethodError`
Um das Problem zu beheben, [kompilieren Sie die Sling-Skripte wie JSP, Java und Sightly neu](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=de#resolution). (FORMS-8542)
* Nach der Installation von AEM Service Pack 6.5.14.0 und höher können Benutzende beim Navigieren zu `Home` > `Services` > `PDF Generator` > `Adobe PDF Settings` keine Schriftart aus der JEE-Admin-Benutzeroberfläche für PDF-Dokumente auswählen, da die Schriftartenliste leer erscheint. (FORMS-12095)
<!-- When a form is signed using the OOTB Scribble Signature component, it appears in the image dialogue but does not preview and appears blank when you click on it. (FORMS-12073). A hotfix is available for this issue. To download and install the hotfix, see [Adobe Experience Manager Forms Hotfixes](/help/release-notes/aem-forms-hotfix.md) -->
* Unter AEM Forms on JEE kann die HTML5 Forms, die den Kontextpfad verwenden, nicht gerendert werden. (FORMS-12485, FORMS-12691) Für dieses Problem ist ein Hotfix verfügbar. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie unter [Adobe Experience Manager Forms-Hotfixes](/help/release-notes/aem-forms-hotfix.md).
* Mit adaptiven Formularen können Sie benutzerdefinierte Funktionen mit ECMAScript Version 5 oder früher verwenden. Wenn eine benutzerdefinierte Funktion ECMAScript-Version 6 oder höher verwendet, z. B. „let“, „const“ oder Pfeilfunktionen, wird der Regeleditor möglicherweise nicht ordnungsgemäß geöffnet.

#### AEM Forms für JEE

* Für Struts 2 RCE, ein beliebtes Open-Source-Webanwendungs-Framework für die Entwicklung von Java™ EE-Webanwendungen, wurden kritische Sicherheitslücken gemeldet. Adobe hat das [AEM 6.5 Service Pack 19.1 (6.5.19.1)](/help/forms/using/mitigating-struts-2-rce-vulnerabilities-for-experience-manager-manager-form.md) veröffentlicht, um die Sicherheitslücke in AEM Forms auf JEE zu beheben.

<!--The font enumeration fails due to the missing Ps2Pdf service file.-->

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die darin enthaltenen OSGi-Pakete und Inhaltspakete aufgeführt. [!DNL Experience Manager] 6.5 Service Pack-Version:

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
