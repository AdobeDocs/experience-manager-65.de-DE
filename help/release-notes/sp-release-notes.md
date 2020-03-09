---
title: Versionshinweise zum AEM 6.5 Service Pack
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Service Pack 4.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: ff006375b9ac958c7a5f9adf122990bf23808834

---


# Versionshinweise zu Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager 6.5** |
|---|---|
| Version | 6.5.4.0 |
| Typ | Service Pack-Version |
| Datum | 05. März 2020 |
| Download-URL | [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0), [Software Distribution(Beta)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.4.zip) |

## Inhalt von Adobe Experience Manager 6.5.4.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.4.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Verbesserungen sowie Leistung, Stabilität und Sicherheitsverbesserungen umfasst. Dieses Update wurde seit der allgemeinen Verfügbarkeit der Version 6.5 im **April 2019** veröffentlicht. Es kann über Adobe Experience Manager (AEM) 6.5 installiert werden.

Zu den wichtigsten Funktionen und Verbesserungen, die in AEM 6.5.4.0 eingeführt wurden, zählen:

* AEM Assets wird jetzt über die Adobe I/O-Konsole mit dem Markenportal konfiguriert.

* Für AEM Forms-Arbeitsabläufe steht jetzt ein neuer Schritt zum [Generieren druckbarer Ausgabe](../forms/using/aem-forms-workflow-step-reference.md) zur Verfügung.

* [Mehrspaltige Unterstützung](../forms/using/resize-using-layout-mode.md) für den Layoutmodus für adaptive Formulare und interaktive Kommunikation.

* Unterstützung für [Rich Text](../forms/using/designing-form-template.md) in HTML5-Formularen.

* Barrierefreiheitsverbesserungen in Assets.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.10.8 aktualisiert.

Eine vollständige Liste der Funktionen, wichtigen Highlights und wichtigen Funktionen, die in früheren AEM 6.5 Service Packs eingeführt wurden, finden Sie unter [Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4](new-features-latest-service-pack.md).

### Sites {#sites-fixes}

* Wenn eine URL einer AEM-Siteseite einen Doppelpunkt enthält ( : ) oder Prozentsymbol (%), der zugrunde liegende Browser reagiert nicht mehr und die CPU-Zyklen zeigen eine Spitze (NPR-32369, NPR-31918).

* Wenn eine AEM-Siteseite zur Bearbeitung geöffnet und eine Komponente kopiert wird, bleibt die Einfügeaktion für einige Platzhalter nicht verfügbar (NPR-32317).

* Wenn der Assistent zum Verwalten von Veröffentlichungen geöffnet wird, wird ein Erlebnisfragment, das mit einer Core-Komponente verknüpft ist, nicht in den Listen der veröffentlichten Referenzen angezeigt (NPR-32233).

* Die Übersicht über Live-Kopien in der Touch-Benutzeroberfläche dauert wesentlich länger als die klassische Benutzeroberfläche (NPR-32149).

* Wenn sich die Server- und die Maschinenzeit in unterschiedlichen Zeitzonen befinden, zeigt die geplante Veröffentlichungszeit die Serverzeit in der Touch-Benutzeroberfläche an, während in der klassischen Benutzeroberfläche die Maschinenzeit angezeigt wird (NPR-32077).

* AEM-Sites können keine Seite mit einem Suffix in der URL (NPR-32072) geöffnet werden.

* Wenn ein Benutzer ein Inhaltsfragment bearbeitet, wird eine gelöschte Variante des Inhaltsfragments wiederhergestellt (NPR-32062).

* Benutzer dürfen ein Inhaltsfragment speichern, ohne in den erforderlichen Feldern Informationen anzugeben (NPR-31988).

* kernel.js und ui.js sind nicht vorab erfüllt oder zwischengespeichert. Dies führt zu zusätzlicher Zeit beim Rendern von Seiten (NPR-31891).

* Wenn PageEventAuditListener aktiviert ist, wird die Länge der Warteschlange zum Übernehmen verlängert. Es wirkt sich auf die Leistung vieler Vorgänge wie Massenveröffentlichung, Navigation, Massenbewegung von Assets aus (NPR-31890).

* Wenn Erlebnisfragmente gezogen werden, wird eine hohe Reaktionszeit beobachtet (NPR-31878).

* Wenn Sie die Option Komponente hierher ziehen im Platzhalter eines interaktiven Rasters auswählen, wird eine GET-Anforderung gesendet und die Anforderung führt zum HTTP-403-Fehler (NPR-31845).

* Wenn Sie den Inhalt innerhalb desselben Ordners verschieben, ist die Option zum Verschieben der Seite deaktiviert (NPR-31840).

* Im Strukturmodus bearbeitbarer Vorlagen zeigt die Liste der zulässigen Komponenten im Layout-Container falsche Ergebnisse an. Im Layout-Container (NPR-31816) werden nur Komponenten mit Design-Dialog angezeigt.

* Wenn eine Seite schreibgeschützte Berechtigungen für einen Benutzer hat, ist die Option &quot;Eigenschaften öffnen&quot;in sites.html, jedoch nicht in editor.html (NPR-31770) sichtbar.

* Wenn ein Benutzer auf die Schaltfläche Erstellen klickt, ist die Seitenoption nicht verfügbar (NPR-31756).

* Die Kampagne in Adobe-Kampagnen mit OOTB (Out-of-the-Box) Design Importer-Komponente (NPR-31728) kann nicht synchronisiert werden.

* Wenn Sie versuchen, eine Aufzählungsliste in eine nummerierte Liste zu ändern, werden nur die ersten beiden Elemente der Liste geändert (NPR-31636).

* Wenn eine Seite nicht verfasst ist und die untergeordnete Node ausgewählt ist, wird im Auswahldialogfeld weiterhin die ursprüngliche Node angezeigt. Wenn die Seite erstellt wird und der Benutzer auf &quot;Durchsuchen&quot;klickt, wird die Seite zum Stammknoten statt zum erstellten Knoten (NPR-31618) umgeleitet.

* Das Dialogfeld für die Ansichtskonfiguration funktioniert bei der Arbeitsablauffunktion für die Anpassung des Postfachs (NPR-32503 und NPR-32492) nicht ordnungsgemäß.

* Beim Anzeigen von Workflow-Informationen mit Inbox (CQ-4282168) wird eine Fehlermeldung angezeigt.

### Assets {#assets-6540-enhancements}

* Die Schaltfläche zum Auslösen des Workflows auf der Seite zur Asset-Sammlung ist deaktiviert (NPR-32471).

* Ein Ordner ohne Namen wird in SPS (Scene7 Publishing System) erstellt, während ein Asset in Experience Manager mit dynamischer Media Scene7-Konfiguration (NPR-32440) von einem Ordner in einen anderen verschoben wird.

* Die Aktion zum Verschieben aller Assets (mit &quot;Alle auswählen&quot;und dann &quot;Verschieben&quot;) in einen Ordner mit veröffentlichten Assets schlägt fehl (NPR-32366).

* Die Generierung von Ausgabeformaten für Assets mit ${extension} schlägt fehl (NPR-32294).

* Die URLs im Versionsverlauf werden auf der Eigenschaftenseite (NPR-31889) unter &quot;Verwiesen nach&quot;angezeigt.

* Die von DAM heruntergeladene ZIP-Datei kann nicht mit WinZip (NPR-32293) geöffnet werden.

* Ursprüngliche Berechtigungen eines Ordners werden aktualisiert, wenn Ordnereinstellungen geöffnet werden, um den Ordnertitel oder das Miniaturbild zu ändern und dann zu speichern (NPR-32292).

* Das Kalendersymbol für die geplante Aktivierung wird nicht in der Statusspalte (in der klassischen Benutzeroberfläche der DAM-Asset-Auflistung) für Assets angezeigt, deren Aktivierung für ein späteres Datum und eine spätere Uhrzeit geplant ist (NPR-32291).

* Die Erstellung von Snippets mithilfe von Snippet-Vorlagen gibt beim Erstellen von Snippets (NPR-32290) Fehler beim Suchen nach Sammlungen.

* Mehrere Suchabfragen werden ausgelöst, wenn mehrere Tags aus dem Suchfilter ausgewählt werden (NPR-32143).

* In der Benutzeroberfläche von Experience Manager Assets werden abgeschnittene Dateinamen angezeigt, wenn Assets mit mehr als 50 Zeichen im Dateinamen hochgeladen werden (NPR-32054).

* Alle Kontrollkästchen im Filterbedienfeld werden gelöscht, wenn das erste und das zweite Kontrollkästchen deaktiviert werden, wenn die Kontrollkästchen in Adobe Stock auf Stufe zwei markiert wurden (NPR-31919).

* Die Datei- und Ordnersuche mit Omniture-Facetten bildet eine Ausnahme (NPR-31872).

* Die Feldhervorhebung für die obligatorische Feldauswahl im Metadateneditor wird auch nach Auswahl des erforderlichen Felds nicht entfernt, wenn die Abhängigkeitsregeln im entsprechenden Metadatenschema-Formular (NPR-31834) festgelegt sind.

* Vollständige Namen von Tags auf Blattebene (aus der Taghierarchie) werden auf der Seite &quot;Asset-Eigenschaften&quot;nicht angezeigt (NPR-31820).

* Die Verwendung des Befehls &quot;Zurück&quot;auf der Seite &quot;Asset-Eigenschaften&quot;im Safari-Browser gibt einen Fehler zurück (NPR-31753).

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31307).

* Auf der Seite &quot;Assets-Detail&quot;von PDF-Assets werden keine Aktionsschaltflächen angezeigt, mit Ausnahme der Schaltflächen &quot;Zur Sammlung&quot;und &quot;Darstellung hinzufügen&quot;in Experience Manager, der im dynamischen Media Scene7-Ausführungsmodus ausgeführt wird (CQ-4286705).

* Assets, die größer als 2 GB sind, können jetzt in Dynamic Media-Scene7 hochgeladen werden (CQ-4286561).

* Die Verarbeitung von Assets durch den Batch-Upload von Scene7 (CQ-4286445) dauert zu lange.

* Die Schaltfläche &quot;Speichern&quot;importiert kein Remote-Set, wenn der Benutzer im Set-Editor im Dynamic Media Client keine Änderungen vorgenommen hat (CQ-4285690).

* Die Miniaturansicht von 3D-Assets ist nicht informativ, wenn ein unterstütztes 3D-Modell in AEM integriert wird (CQ-4283701).

* Der unverarbeitete Status der Viewer-Vorgabe für intelligente Beschneidung wird zweimal neben dem Vorgabennamen auf dem Bannertext angezeigt (CQ-4283517).

* Auf der Detailseite des Assets (CQ-4283309) wird eine falsche Behälterhöhe eines hochgeladenen 3D-Modells, das im 3D-Viewer in der Vorschau angezeigt wird, festgestellt.

* Karussell-Editor wird in IE 11 im dynamischen Medienmodus von Experience Manager (CQ-4255590) nicht geöffnet.

* Der Tastaturfokus wird in der Dropdown-Liste &quot;E-Mail&quot;im Dialogfeld &quot;Herunterladen&quot;in Chrome und Safari-Browsern (NPR-32067) angehalten.

* Das Kontrollkästchen &quot;Alle Inhalte synchronisieren&quot;ist nicht standardmäßig aktiviert, wenn versucht wird, eine DM-Cloud-Konfiguration in AEM hinzuzufügen (CQ-4288533).

### Foundation-Benutzeroberfläche {#foundation-ui-6540}

* Die Maussteuerung wechselt zum vorherigen Filterfeld, anstatt im vorhandenen Filterfeld zu bleiben, während Assets mit dem Filterbedienfeld (NPR-32538) gesucht werden.

* Plattform-Tagging: Die Suche nach Tags durch Eingabe in die Tag-Felder zeigt Tags außerhalb der Root-Grenzen an und berücksichtigt nicht die `rootPath` Eigenschaft von Tag-Feldern (NPR-31895).

* Plattform-Benutzeroberfläche: Pfadbrowser wird umgebrochen, wenn im Textfeld ein ungültiger Pfad hinzugefügt wird (NPR-31884).

* Die Benachrichtigung wird hinter einem fixierbaren Menü bei der Seitenauswahl (NPR-31628) versteckt.

### Plattform {#platform-sling-6540}

* (HTL) Unterstriche ersetzen Doppelpunkte im Pfadabschnitt der URL (NPR-32231).

### Projekte {#projects-6540}

* Schaltfläche &quot;Erstellen&quot;ist für den Benutzer nicht sichtbar, auch wenn der Benutzer berechtigt ist, ein Projekt im Unterordner zu erstellen (NPR-31832).

### Projektübersetzung {#projects-translation-6540}

* Bei der Erstellung von Übersetzungsprojekten wird die Benutzeroberfläche unterbrochen, wenn die Option &quot;Beschneidungsbereiche&quot;in `Apache Sling JSP Script Handler` (NPR-32154) aktiviert ist.

* Fehler in UI- und Null-Punkt-Ausnahme in Fehlerprotokollen werden beobachtet, wenn ein zu übersetzendes Tag einem Übersetzungsprojekt hinzugefügt wird (NPR-31896).

### Integrationen {#integrations-6540}

* Die URL-Erstellung der Startbibliothek basiert nur auf `path` und `library_name` Werten aus der Start-API und basiert nicht auf dem `library_path` Wert (NPR-31550).

* Während der Verarbeitung von LiveFyre-bezogenen Elementen wird eine Fehlermeldung angezeigt (FYR-12420).

### WCM-Vorlageneditor {#wcm-template-editor-6540}

* Im Strukturmodus bearbeitbarer Vorlagen zeigt die Liste der zulässigen Komponenten im Layout-Container keine Komponente der Verknüpfungsschaltfläche an (CQ-4282099).

### WCM Page Editor {#wcm-page-editor-6540}

* Fehler werden bei der Auswahl einer Überlagerung und der anschließenden Auswahl von reaktionsfähigen Raster Ziehen Sie Komponenten hierher (CQ-4283342).

### Campaign Targeting {#campaign-targeting-6540}

* Die Target-Cloud-Konfiguration schlägt fehl, wenn die Fehlermeldung &quot;get mboxes&quot;fehlgeschlagen ist (CQ-4279880).

### Brand Portal {#assets-brand-portal}

* Dropdown-Werte für Metadaten-Schemas sind in den Asset-Eigenschaften nicht sichtbar (CQ-4283287).

* Das Metadaten-Unterschema zeigt keine Registerkarten basierend auf dem MIME-Typ in den Asset-Eigenschaften an (CQ-4283288).

* Beim Rückgängigmachen der Veröffentlichung des Metadatenschemas wird eine Fehlermeldung angezeigt, obwohl das Schema im Backend entfernt wurde.

* Das Vorschaubild wird für ein veröffentlichtes Asset nicht angezeigt (CQ-4285886).

* Benutzer kann Assets, die ein einzelnes Anführungszeichen im Namen enthalten (CQ-4272686), nicht veröffentlichen oder die Veröffentlichung rückgängig machen.

* Die Geschäftsbedingungen werden beim Herunterladen mehrerer Assets nicht angezeigt (CQ-4281224).

* Geringfügige Sicherheitslücken wurden behoben.

### Communities {#communities}

* Das Formular &quot;Create Member&quot;wird als leere Seite angezeigt (NPR-31997).

* Benutzer kann den Analytics-Bericht nicht in der Autoreninstanz anzeigen (NPR-30913).

### Oak- Indizierung und Abfragen {#oak-indexing-6540}

* MS Word- und MS Excel-Dokumente, die JPEG-Bild enthalten, wenn die Analyse mit Tika Parser nicht durchgeführt werden kann und der Fehler class not found (Klasse nicht gefunden) wird beobachtet (NPR-31952).

### Formulare {#forms-6530}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on](#install-aem-forms-add-on-package) and [Install AEM Forms on JEE](#install-aem-forms-jee-installer).

* Correspondence Management: Briefe zeigen zusätzliche Zeichen an, nachdem Arbeitsabläufe für die Übermittlung an die Nachbearbeitung (NPR-32626) gesendet wurden.

* Correspondence Management: Briefe zeigen einen Dropdown-Platzhalter als Textkomponente an, nachdem sie an Workflows nach dem Prozess gesendet wurden (NPR-32539).

* Correspondence Management: Die in der Briefvorlage definierten Standardwerte werden nicht im Vorschaumodus (NPR-32511) angezeigt.

* Mobile Forms: Die Senden-Schaltfläche wird beim Rendern eines XDP-Formulars in einer HTML-Version (NPR-32514) als vergrößert angezeigt.

* Document Services: URL-Zugriffsfehler für Briefe und einige andere Seiten nach Anwendung von Service Pack 2 (NPR-32508, NPR-32509).

* Document Services: Wenn die Anzahl der Transaktionen auf einem Server eine bestimmte Grenze überschreitet, schlägt die Konvertierung von HTML in PDF fehl und die Dateitypeinstellungen werden vom AEM Forms-Server (NPR-32204) entfernt.

* Adaptive Formulare: Das Tool zur Barrierefreiheit des Browsers meldet Fehler in adaptiven Formularen gemäß den Richtlinien für WCAG2 Level AA (NPR-32312, NPR-32309, CQ-4285439).

* Adaptive Formulare: Chrome-Browser-Barrierefreiheitstool berichtet über einen Best Practice-Fehler (NPR-32310).

* Adaptive Formulare: Übersetzungsprobleme beim Konfigurieren eines adaptiven Formulars, das in eine AEM-Siteseite eingebettet ist (NPR-32168).

* Workbench: Beim Verwenden des Vorgangs &quot;PDF-Eigenschaften abrufen&quot;für den PDF Utilities-Dienst (NPR-32150) wird eine Fehlermeldung angezeigt.

* Document Security: Eine geschützte PDF-Datei kann nicht offline geöffnet werden, wenn die Option DisableGlobalOfflineSynchronizationData auf True (NPR-32078) eingestellt ist.

* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32547, NPR-31983, NPR-31950) ausgeblendet.

* Designer: Wenn eine Tabelle zusammengeführte Zellen enthält, schlägt der Barrierefreiheitstest für die Ausgabe-PDF-Datei fehl, die mithilfe des Ausgabediensts (CQ-4285372) aus einem XDP-Formular konvertiert wurde.

## Install 6.5.4.0 {#install}

**Einrichtungsvoraussetzungen**

* AEM 6.5.4.0 requires AEM 6.5. Check [upgrade documentation](/help/sites-deploying/upgrade.md) for detailed instructions.
* Der Download des Service Packs ist in Adobe Package Share verfügbar, auf das Sie direkt über die AEM 6.5-Instanz zugreifen können.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.5.4.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Erstellen Sie eine Momentaufnahme oder ein neues Backup Ihrer AEM-Instanz, bevor Sie das Service Pack installieren.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Dennoch wird dies empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!CAUTION]
>
>Adobe rät davon ab, das AEM 6.5.4.0-Paket zu entfernen oder zu deinstallieren.

### Installieren des Service Packs über Package Share {#install-service-pack-via-package-share}

Führen Sie folgende Schritte aus, um das Service Pack in einer vorhandenen AEM 6.5-Instanz zu installieren:

1. Login to Package Share from within AEM or directly from your browser and download the [AEM 6.5.4.0 package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0).

1. Installieren Sie das heruntergeladene Paket mit Package Manager.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.5.4.0 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

**Automatische Installation**

Es gibt zwei Möglichkeiten, AEM 6.5.4.0 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..*Ordner /crx-quickstart/install* , während der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure that you use cmd=install&amp;recursive=true - so the nested packages  are  installed.

>[!NOTE]
>
>AEM 6.5.4.0 unterstützt keine Bootstrap-Installation.

**Bestätigen der Installation**

1. Auf der Seite &quot;Produktinformationen&quot;(/system/console/productinfo) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager, Version 6.5.4.0` unter &quot;Installierte Produkte&quot;angezeigt.

1. All  OSGi  bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: /system/console/bundles).
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.10.6 oder höher (Web-Konsole verwenden: /system/console/bundles).

In order to see what platforms are certified to run with this release, please refer to the [Technical Requirements](/help/sites-deploying/technical-requirements.md).

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

>[!NOTE]
>
>AEM 6.5.4.0 includes a new version of [AEM Forms Compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/AEM-FORMS-6.5.3.0-COMPAT). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf AEM 6.5.4.0 aktualisieren, installieren Sie nach der Installation des Forms Add-On-Pakets die neueste Version des AEM Forms-Kompatibilitätspakets.

1. Stellen Sie sicher, dass Sie das AEM Service Pack installiert haben.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

### Install AEM Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Korrekturen in AEM Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

For information about installing the cumulative installer for AEM Forms on JEE and post-deployment configuration, see the [release notes for patch 0011](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0011.html).

#### Workbench-Installationsprogramm

Da es sich um ein vollständiges Installationsprogramm handelt, ist die Dateigröße im Vergleich zur Patch-Version größer. Deinstallieren Sie die vorherige Workbench-Version, bevor Sie die neue Version installieren.

### UberJar {#uber-jar}

The UberJar for AEM 6.5.4.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.4/).

To use UberJar in a Maven project, refer to the article, [How to use UberJar](/help/sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.4.0</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Deprecated features {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen auf, die mit AEM 6.5.4.0 als veraltet markiert wurden. Funktionen, die in einer zukünftigen Version entfernt werden sollen, werden zuerst auf &quot;Veraltet&quot;eingestellt, wobei eine alternative Option verwendet werden muss.

Kunden wird empfohlen, zu überprüfen, ob sie die Funktion oder Funktionalität in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | The **[!UICONTROL AEM Cloud Services Opt-In]** screen has been deprecated. Mit der AEM- und Target-Integration, die in AEM 6.5 aktualisiert wurde, um die Target Standard-API zu unterstützen, die Authentifizierung über Adobe IMS und I/O verwendet, und der wachsenden Rolle von Adobe Launch bei der Instrumentierung von AEM-Seiten für Analyse und Personalisierung ist der Opt-In-Assistent nun funktional irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und Adobe I/O-Integrationen über entsprechende AEM-Cloud-Services |

## Bekannte Probleme {#known-issues}

* Wenn der Konfigurationsassistent für **verbundene Assets nach der Installation die Fehlermeldung 404 zurückgibt, müssen Sie die Pakete** cq-remotedam-client-ui-content **und** cq-remotedam-client-ui-components **** manuell mit dem Package Manager neu installieren.
* Die folgenden Fehler- und Warnmeldungen können während der Installation von AEM 6.5.x.x angezeigt werden:
   * „Wenn die Target-Integration mit der Target Standard-API (IMS-Authentifizierung) in AEM konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * com.adobe.granite.maintenance.impl.TaskScheduler: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregationsfunktionen wie SUM, MAX und MIN verwendet werden. CQ-4274424
   * com.adobe.granite.maintenance.impl.TaskScheduler - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.

## OSGi bundles and content packages included {#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten werden die in AEM 6.5.4.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt.

Liste der in AEM 6.5.4.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6540_bundles.txt)

Liste der in AEM 6.5.4.0 enthaltenen Inhaltspakete

[Datei laden](assets/6540_packages.txt)

## Restricted sites {#restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Support](https://daycare.day.com/public/contact.html). Weitere Informationen zum Zugriff auf das Support-Portal finden Sie unter [Zugriff auf das Support-Portal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORE WIE DIESE]
>
>* [Versionshinweise zu AEM 6.5](/help/release-notes/release-notes.md)
>* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
>* [Dokumentation zu AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

