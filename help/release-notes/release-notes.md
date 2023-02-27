---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 3
source-git-commit: 78aa7aac838dabc1c4f0329520092e4755541322
workflow-type: tm+mt
source-wordcount: '2196'
ht-degree: 52%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/Documents/issue_tracker_sp_cfp_updates.xlsx?d=w3ea81ae4e6054153b132f2698c86f84e&csf=1&web=1&e=WRAZ43&nav=MTVfezk2OTJDQTNFLUI4QTQtNDY2RS05NEVCLUQ5QjcyNEVENkJDNn0 -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.16.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 23. Februar 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[..]be/packages/cq650/servicepack/aem-service-pkg-6.5.16.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.16.0 enthalten ist {#what-is-included-in-aem-6516}

[!DNL Experience Manager] 6.5.16.0 enhält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Eine wesentliche Verbesserung in Dynamic Media ist die folgende:

Neue Protokoll-DASH-Unterstützung (dynamisches adaptives Streaming über HTTP) für adaptives Bitratenstreaming in Dynamic Media-Videobereitstellung (mit CMAF) [Allgemeines Medienanwendungsformat] aktiviert).

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Anwendererlebnis bei der Videoanzeige.
* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet.
* Jetzt in Nordamerika verfügbar (über Support-Ticket möglich), in Kürze in Asien-Pazifik und Europa-Naher Osten-Afrika.

Siehe [DASH in Ihrem Konto aktivieren](/help/assets/video.md#enable-dash).

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets] {#assets-6516}

* Connected Assets: Wenn Sie die Optionen für smartes Zuschneiden für Bilder auf Remote-DAM aktivieren, Bilder in einen Ordner hochladen und den Ordner mit lokalen Sites synchronisieren, wird der Ordner nicht in der lokalen Sites-Bereitstellung geöffnet. (NPR-39912)
* Beim Sortieren einer Sammlung nach Namen funktioniert die Listenansicht nicht ordnungsgemäß. (ASSETS-19401)
* Wenn eine große Mediendatei (JPEG) in Sammlungen hochgeladen wird, reagiert Experience Manager nicht mehr. (ASSETS-19387)
* Im Inhaltsbaum-Bereich ist der angezeigte Asset-Name falsch, da der Speicherort des Assets nicht ordnungsgemäß wiedergegeben wird. (ASSETS-18870)
* Beim Teilen einer Sammlung mithilfe eines Links stimmen die Daten in der URL nicht mit der Kombination aus Karten- und Listenansicht überein. (ASSETS-18758)
* Wenn Sie eine Omnisearch mithilfe eines Filters für den Ordnertyp durchführen, sind die Suchergebnisse inkonsistent. (ASSETS-18227)
* Die `dam:size` -Eigenschaft nach XMP Writeback nicht aktualisiert wird, was dazu führt, dass falsche Informationen von der `/platform/path/to/asset.jpg;resource=metadata` API. (ASSETS-17631)
* Nicht geschlossener Ressourcen-Resolver für alle Experience Manager-Instanzen. (ASSETS-16904)
* Es kann keine Version für ein Asset erstellt werden, selbst wenn Ihnen die `create` und `modify` Berechtigungen. (ASSETS-15956)
* Die `move` -Schaltfläche beim Verschieben eines Assets von einem Punkt an einen anderen zufällig deaktiviert wird. (ASSETS-14889)
* Bildschirmlesehilfen können Überschriften nicht identifizieren, da der Text nicht innerhalb von Überschriften-Tags, sondern als allgemeiner Text definiert ist. (ASSETS-6924)
* Der Alternativtext unter dem Bild ist nicht obligatorisch, aber der unter dem Bild angezeigte Text wiederholt sich mit einem `Type` -Attribut. (ASSETS-6915)


## [!DNL Assets] - [!DNL Dynamic Media] {#dm-6516}

* Das Formularelement enthält keine Beschriftung. Bei Bildschirmlesehilfen wie NVDA und JAWS werden Informationen zur Formularbeschriftung nicht ordnungsgemäß angekündigt. (CQ-4344078)
* Dropdown-Listen werden nicht geschlossen, wenn die Variable `Escape` -Taste auf einer Tastatur verwendet wird. (CQ-4344077)
* Das Informationssymbol (der Buchstabe &quot;i&quot;), das nach Eingabe einer ungültigen Eingabe für den Inline-Fehlervorschlag angezeigt wird, kann nicht über eine Tastatur aufgerufen werden. (CQ-4344076)
* `getManifestURI` gibt null zurück, da eine JCR-Eigenschaft als gelesen wird `toString` anstelle von `getString`. (ASSETS-18674)
* Die SmartCrop-Videokomponente verhält sich nicht korrekt. Die Komponente führt die Wiedergabe anstelle von Streaming durch, und VTT-Aufrufe schlagen fehl und geben einen 404-Fehler zurück. (ASSETS-18468)
* Auswählen **[!UICONTROL Eigenschaften]** auf der Viewer-Seite eines Assets verursacht eine Null-Pointer-Ausnahme. (ASSETS-18420)
* [!DNL Experience Manager] Änderungen an der Benutzeroberfläche für DASH-Streaming, die Folgendes enthalten:
   * über ein sichtbares CMAF-Feld (Common Media Application Format) im Videoprofil-Editor verfügen.
   * Wenn der Video-Upload-Prozess eine CMAF-Markierung sendet.
   * die Optionen **[!UICONTROL auto]**, **[!UICONTROL hls]** und **[!UICONTROL dash]** sind jetzt in der Dropdown-Liste &quot;Wiedergabe&quot;im Editor für Viewer-Vorgaben verfügbar **[!UICONTROL Verhalten]** Registerkarte.
(ASSETS-17428)
* Wenn Sie in der Navigation **[!UICONTROL Assets]** > **[!UICONTROL Dateien]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Karussellset]**, wird das Bildsymbol mit der Textzeichenfolge &quot;Folie 1&quot;überlagert. (ASSETS-18578)
* Nicht veröffentlichte Assets werden erneut veröffentlicht. (ASSETS-16428)
* Die Experience Manager-Autoreninstanz wird aufgrund eines Ladeproblems heruntergefahren, was zur Erstellung eines synthetischen Warnhinweises führt. (ASSETS-15937)
* Auf der Seite &quot;Allgemeine Dynamic Media-Einstellungen&quot;wird eine nicht übersetzte Fehlermeldung angezeigt. `Failed to fetch data` angezeigt. (ASSETS-15617)

## [!DNL Forms] {#forms-6516}

>[!NOTE]
>
>Fehlerbehebungen in [!DNL Experience Manager] Forms wird eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Veröffentlichungsdatum des Service Packs. In diesem Fall werden die Add-On-Pakete am Donnerstag, 2. März 2023 veröffentlicht. Darüber hinaus wird diesem Abschnitt eine Liste mit Fehlerbehebungen und Verbesserungen für Forms hinzugefügt.

<!--
### [!DNL Forms] Fixes {#forms-fixes-6516}
-->

## Integrationen {#integrations-6516}

* Entfernen Sie den Code und die Abhängigkeit der Adobe-Search&amp;Promote aus Experience Manager 6.5. Adobe Search&amp;Promote hat das Ende des Diensts im September 2022 erreicht. Siehe [Ankündigung zum Ende der Adobe-Search&amp;Promote](https://experienceleague.adobe.com/docs/discontinued/using/search-promote.html?lang=en). (NPR-39706)

## [!DNL Sites] {#sites-6516}

* Aktuell `cq-wcm-core` Die Werksfreigabe verfügt nicht über das POM. (SITES-10983)
* Die zu erstellende Seite sollte bei der Rollout-Vorschauaktion nicht aufgelistet werden. (SITES-10355, CQ-4266213)
* Rollout nach MSM-Trennen erstellt die separate Seite. (SITES-9841)
* Beim Erstellen eines Launches wird der Zeitablauf überschritten. Der Benutzer muss auf einem Ladebildschirm viele Minuten warten, bevor die Anfrage eine Zeitüberschreitung aufweist. (SITES-9051)
* In der Benutzeroberfläche &quot;Rollout-Seite&quot;werden nicht vorhandene Pfade übergeordneter Seiten angezeigt. Sie können die Seite mit einer Erfolgsmeldung einführen, aber die untergeordnete Seite wird nicht ausgerollt, da die übergeordnete Seite überhaupt nicht eingeführt wird. (SITES-8621)

### [!DNL Sites] - Kernkomponenten {#sites-core-components-6516}

* Zentralisieren Sie die Link-Verarbeitung auf E-Mail-Seiten, sodass Modellanpassungen nicht mehr erforderlich sind. (SITES-9002)

### [!DNL Sites] - Admin-Benutzeroberfläche {#sites-adminui-6516}

* CSV-Export exportiert nicht alle Seiten unter der ausgewählten Seite. (SITES-9390)

### [!DNL Sites] - [!DNL Content Fragments] {#sites-contentfragments-6516}

* Die JSON eines Inhaltsfragments kann nicht gedruckt werden. Der Grund dafür ist, dass die GraphQL-Abfrage beim Öffnen der Vorschauseite des Inhaltsfragments nicht generiert werden kann. (SITES-8619)
* Beim erneuten Öffnen des Inhaltsfragmentmodell-Editors müssen alle **[!UICONTROL Datum und Uhrzeit]** -Felder sind standardmäßig vom Typ Datum und Uhrzeit . (SITES-8401)

### [!DNL Sites] - [!DNL Experience Fragments] {#sites-experiencefragments-6516}

* Sie können ein Experience Fragment nicht in einen anderen Ordner verschieben, selbst wenn die Vorlage unter den zulässigen Vorlagen aufgeführt ist. (SITES-8601)
* (SITES-7989)


### [!DNL Sites] - Seiteneditor {#sites-pageeditor-6516}

* Aktualisierung der Abhängigkeiten für die Verbesserung des Ressourcen-Resolvers in SITES-8464, bei der das Seiten-Rendering im Authoring-Modus eine hohe Anzahl von `TemplatedResourceImpl` Objekte. (SITES-9350)


## Sling {#sling-6516}

* Experience Manager wird beim Start gesperrt. (NPR-39832)
* Wenn im Versionsspeicher des Experience Managers viele Vanity-Pfade vorhanden sind, kann der Experience Manager nicht gestartet werden. (NPR-38955)


## Übersetzungsprojekte {#translation-6516}

* In `MicrosoftTranslationServiceImpl`, der Abfragezeichenfolgenparameter `Category` ist falsch. (NPR-39828)
* Beim Erstellen eines Übersetzungsprojekts wird der Fehler angezeigt *Übergeordnete Seitenressource nicht vorhanden*; das Übersetzungsprojekt nicht erstellt wurde. (NPR-39762)
* Es kann kein Fälligkeitsdatum für ein Übersetzungsprojekt festgelegt werden, das einen menschlichen Übersetzungs-Connector verwendet. (NPR-39593)

## Benutzeroberfläche {#ui-6516}

* Beim Ändern in eine kleinere Auflösung wird der DatePicker nicht angezeigt und die AM/PM-Auswahl wird nicht angezeigt oder ändert sich nicht sichtbar. (NPR-39948)
* Wenn &quot;js minify&quot;(Minimierung von JavaScript) verwendet wird, wird die Minimierung aufgrund eines Parsing-Fehlers nicht verarbeitet. (NPR-39650)
* Tag-Feld (`/libs/cq/gui/components/coral/common/form/tagfield`) mit der Timeline in Konflikt. (CQ-4350751)


## WCM {#wcm-6516}

* Die zu erstellende Seite sollte bei der Rollout-Vorschauaktion nicht aufgelistet werden. (CQ-4266213, SITES-10355)

## Workflow {#workflow-6516}

* Manuelles Löschen des bearbeitbaren Workflow-Modells aus `/conf` lässt eine verbleibende Laufzeitmodellinstanz ohne bearbeitbares Modell. (CQ-4349365)


## Installieren von [!DNL Experience Manager] 6.5.16.0 {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.16.0 erfordert [!DNL Experience Manager] 6.5. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.16.0 mit dem Package Manager auf einer der Authoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.16.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie des `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for AEM Forms, see [AEM Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs auf [!DNL Experience Manager] 6.5 {#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle für die Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Normalerweise tritt dieses Problem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.16.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.16.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.16.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.14 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- NPR-39939 for 6.5.16.0 --> <!-- NPR-39436 for 6.5.15.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie [!DNL Experience Manager] Forms nicht verwenden.

Fehlerbehebungen in [!DNL Experience Manager] Forms werden über ein separates Add-on-Paket eine Woche nach der geplanten Veröffentlichung des [!DNL Experience Manager] Service Packs bereitgestellt.

<!-- 

For instructions to install the service pack on AEM Forms, see [AEM Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).
-->

### UberJar {#uber-jar}

Das UberJar für [!DNL Experience Manager] 6.5.16.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.15/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

>[!NOTE]
>
>In Experience Manager 6.5.16.0 bleibt die UberJar-Version (6.5.15.0) mit der vorherigen Version identisch.


Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.15</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die ab [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie ein Feature oder eine Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, sodass sie eine alternative Option verwendet.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der **[!UICONTROL AEM Cloud Services-Anmeldebildschirm]** ist veraltet, da die [!DNL Experience Manager]- und [!DNL Adobe Target]-Integration in [!DNL Experience Manager] 6.5 aktualisiert wurde. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Sie unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren, der Assistent für die Anmeldung ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime]-Integrationen über die jeweiligen [!DNL Experience Manager]-Cloud-Services. |
| Connectoren | Der Adobe JCR-Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für [!DNL Experience Manager] 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* [AEM-Inhaltsfragment mit GraphQL Index Package 1.0.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.5.zip)
Dieses Paket ist für Kundinnen und Kunden erforderlich, die GraphQL verwenden. Dadurch können sie die erforderliche Indexdefinition hinzufügen, die auf den tatsächlich verwendeten Funktionen basiert.

* Aktualisieren Sie Ihre GraphQL-Abfragen, die möglicherweise einen benutzerdefinierten API-Namen für Ihr Inhaltsmodell verwendet haben, so, dass stattdessen der Standardname des Inhaltsmodells verwendet wird.

* Da [!DNL Microsoft® Windows Server 2019] [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1] nicht unterstützt, unterstützt [!DNL Microsoft® Windows Server 2019] keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie Ihre [!DNL Experience Manager] von 6.5.0 bis 6.5.4 bis zum neuesten Service Pack auf Java™ 11 sehen Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um die Ausnahmen zu beenden, starten Sie Ihre Instanz von neu [!DNL Experience Manager]. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzende können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn Benutzende ein Feld erstmals in einem adaptiven Formular konfigurieren möchten, wird im Eigenschaften-Browser die Option zum Speichern einer Konfiguration nicht angezeigt. Das Konfigurieren eines anderen Feldes des adaptiven Formulars im selben Editor behebt das Problem.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/source „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/ Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` – Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Wenn Sie versuchen, entweder Inhaltsfragmente oder Websites/Seiten zu verschieben/löschen/veröffentlichen, gibt es ein Problem, wenn Inhaltsfragmentreferenzen abgerufen werden, da die Hintergrundabfrage fehlschlägt. Dies bedeutet, dass die Funktionalität nicht verfügbar ist.
Um einen korrekten Betrieb zu gewährleisten, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten `/oak:index/damAssetLucene` hinzufügen (eine Neuindizierung ist nicht erforderlich):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## Enthaltene OSGi-Bundles und Inhaltspakete {#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5.16.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.16.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65160_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.16.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65160_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites {#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

