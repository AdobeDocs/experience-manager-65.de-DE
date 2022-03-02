---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6,5
description: '"[!DNL Adobe Experience Manager] 6.5-Hinweise mit Versionsinformationen, Neuigkeiten, Installationsanleitungen und detaillierten Änderungslisten."'
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 6a89cb79ccfbcec7385832d5682bf61895253718
workflow-type: tm+mt
source-wordcount: '2641'
ht-degree: 4%

---

# [!DNL Adobe Experience Manager] 6.5 Neueste Service Pack - Versionshinweise {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.12.0 |
| Typ | Service Pack-Version |
| Datum | 24. Februar 2022 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip) |

## Was ist enthalten in [!DNL Adobe Experience Manager] 6,5,12,0 {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.12.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf installiert. [!DNL Adobe Experience Manager] 6.5.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.12.0 sind:

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt Vorgänge zum Aktualisieren, Löschen, Umbenennen und Verschieben von Remote-DAM-Assets oder -Ordnern durchführen. Die Updates sind mit einiger Verzögerung automatisch in der Sites-Bereitstellung verfügbar (NPR-37816).

* Push-Rollouts von einer Live Copy-Quelle an mehrere Live Copies sind jetzt standardmäßig möglich, ohne dass eine Blueprint-Konfiguration erforderlich ist (CQ-4259951).
* Der Status laufender asynchroner Vorgänge wird jetzt in der Benutzeroberfläche angezeigt, um zu verhindern, dass Benutzer versehentlich mehrere asynchrone Vorgänge auf demselben Pfad auslösen (NPR-37611).
* Unterstützung für IMS-basierte Authentifizierung für Analytics 2.0-APIs (CQ-4285474, NPR-37803, NPR-37701, NPR-37702, NPR-37703).
* API-Unterstützung für JSON-Erlebnisfragment vom Angebotstyp (NPR-37796).
* Die Angebotsanforderung wird jetzt für Löschangebot (Experience Fragment-API) in IMS bereitgestellt (NPR-37668).
* Das integrierte Repository (Apache Jackrabbit Oak) verbleibt weiterhin bei 1.22.9.

Im Folgenden finden Sie die Liste der Fehlerbehebungen in [!DNL Experience Manager] Version 6.5.12.0.

### [!DNL Sites] {#sites-65120}

Die folgenden Probleme wurden in [!DNL Sites]:

* Das Layout der Inhaltsfragmenteigenschaften ist fehlerhaft, da die Registerkarten Allgemein und Erweitert keine Ränder nach links haben (SITES-4484).
* Die Option zum Schließen von Bannern in Inhaltsfragmenten, die auf verschiedenen Seiten der Sites referenziert werden, funktioniert nicht. Dieses Banner informiert die Benutzer darüber, dass das Inhaltsfragment auf einer oder mehreren Seiten referenziert wird (SITES-4173).
* Die Kontrollkästchen werden im Dialogfeld &quot;Vererbung zurücksetzen&quot;nicht ausgerichtet (SITES-3514).
* Die Vorlagenseite auf Web-Einzelhandelssites und WKND-Sites ist fehlerhaft, da die Option &quot;Komponenten werden nicht geladen und Struktur&quot;nicht verfügbar ist, da das Servlet pageinfo.json auf LaunchManagerImpl.getLaunchStream (SITES-3489) hängt.
* Die Veröffentlichung von Benutzerknoten von der Autoren- in der Veröffentlichungsumgebung funktioniert nicht (NPR-38005).
* Der Versuch, ein Experience Fragment mit einer bearbeiteten Vorlage zu erstellen, zeigt nicht die Änderungen an den anfänglichen Seiteneigenschaften an (NPR-37962).
* Der Seitenverschiebungsvorgang auf dem Experience Manager ist langsam (NPR-37961).
* Bei der Übersetzung von Experience Fragments werden Verweise auf Sprachkopierpfade nicht aktualisiert (NPR-37953).
* Benutzer ohne Replikationsberechtigungen können Seiten nicht löschen oder verschieben, selbst wenn die Seiten nicht aktiviert sind. (NPR-37936)
* Zufällige org.apache.felix.metatype-Fehler werden auf dem Server beobachtet (NPR-37935).
* Verweise in der Sites Admin Touch-Benutzeroberfläche zeigen eingehende Links nicht korrekt an (NPR-37934).
* Launch-Pfad zum Hinzufügen neuer Seiten oder Assets ist nicht verfügbar, wenn Seiten in einem Übersetzungsauftrag ausgewählt werden. (NPR-37912)
* Referenzseiten in einer Listenkomponente, die in Experience Fragments hinzugefügt wird, werden beim Anzeigen des Launches nicht auf die Zielseite aktualisiert (NPR-37886).
* Die Autorenumgebung weist Probleme mit der Benutzeroberfläche auf, z. B. der Seitentitel im Bearbeitungsmodus ist nicht zentriert und die Komponentenauswahl im Richtlinien-Editor ist zulässig: -Gruppenkontrollkästchen nimmt die gesamte Breite des Containers ein, sodass die Beschriftung in der nächsten Zeile gerendert wird (NPR-37878).
* [Plattform] Die Versionsnummer von xmlns:metatype in der Datei metatype.xml des commons-httpclient lautet &quot;http://www.osgi.org/xmlns/metatype/v1.0.0&quot; anstelle von &quot;http://www.osgi.org/xmlns/metatype/v1.2.0&quot; (NPR-37865).
* Fehler werden beobachtet und Seiten können beim Versuch, eine Seite zu öffnen, nicht verschoben werden (NPR-37864).
* [Rich-Text-Editor] Bild wird in der klassischen Benutzeroberfläche nicht gerendert, wenn das Bild als Listenelement im Rich-Text-Editor hinzugefügt wird (NPR-37835).
* Autoren können Tags anwenden, die sich außerhalb des konfigurierten Stammpfads befinden, wenn sie das Tag-Feld in einem Dialogfeld verwenden (NPR-37834).
* Multifield wird im Layout-Container nicht korrekt gerendert und gibt einen Fehler aus (NPR-37811).
* Der Versuch, die Größe des Komponentenlayouts im Seiteneditor zu ändern, funktioniert nicht im mobilen Layout (NPR-37805).
* Bei der Übersetzung von Experience Fragment werden zyklische Verweise auf Sprachkopierpfade nicht aktualisiert (NPR-37745).
* Die Verwendung des Rich-Text-Felds cq-msm-lockable in den Seiteneigenschaften deaktiviert das Feld beim Rollout der Seite nicht und kann von den Autoren geändert werden (NPR-37714).
* Beim Aktivieren eines Experience Fragments sendet der Herausgeber viele Aktivierungsanfragen an den Dispatcher (NPR-37707).
* Bei einer Topologieänderung wird der Sling-Auftrag für die Asset-Verarbeitung zurückgesetzt, was dazu führt, dass Aufträge, die zum Zeitpunkt der Topologieänderung ausgeführt werden, ignoriert werden (NPR-37706).
* Anführungszeichen, Kreuz und Bindestrich werden nicht in CSV exportiert, wenn Benutzer von MacOS-Export-Sites und Assets-URLs exportieren (NPR-37698).
* Layout-Container in SPA Seitenvorlage können die benutzerdefinierten CSS-Klassen, die in der Vorlagenrichtlinie definiert sind, nicht registrieren, wenn Sie React-SPA-Seiten ausführen (NPR-37697).
* Das Hintergrundbild ist nicht sichtbar, wenn der Benutzer das Targeting für ein Experience Fragment auswählt, das im Container Hintergrundinformationen enthält. (NPR-37662)
* Übersetzungsauftrag für ein Experience Fragment übersetzt nicht alle Komponenten dieses Experience Fragments (NPR-37660).
* Durch die Übersetzung von Experience Fragments und der Seite mit dem Experience Fragment wird der Launch-Pfad im Experience Fragment-Link nicht aktualisiert (NPR-37659).
* Das Widget &quot;Datei-Upload&quot;zeigt den Dateinamen nicht an, wenn eine Datei hochgeladen und das Dialogfeld gespeichert wird (NPR-37634).
* Die geplante Aktivierung (Veröffentlichung) des Assets wird zum geplanten Zeitpunkt nicht Trigger, wenn der Ordner, der das Asset enthält, verschoben wird (NPR-37621).
* [Plattform] Das Dashboard des externen Link-Checkers kann Ergebnisse nicht in [!DNL Adobe Experience Manager] WCM (NPR-37614).
* Der Inhaltsfragment-Editor funktioniert nicht ordnungsgemäß, wenn beim Bearbeiten von Tags im Editor Großbuchstaben in Tag-Namen verwendet werden (NPR-37601).
* Der klassische Benutzeroberflächen-Editor zeigt keine Markierung als in der Vergleichsansicht der Touch-Benutzeroberfläche an (NPR-37588).
* Beim Hinzufügen eines Experience Fragments zu Übersetzungsaufträgen wird der zeitweise 500-Fehler protokolliert. (NPR-37587)
* Autoren können das Datumsauswahldatum selbst bei deaktivierter Datumsauswahl auswählen und verwenden (NPR-37583).
* [Stiftung] Autoren können in einer Komponentendialogstruktur für die Touch-Benutzeroberfläche einige Dezimalwerte nicht in den Ressourcentyp für Zahlenfelder eingeben (NPR-37059).
* Die Pfade im Ordner &quot;libs&quot;werden bei der Installation früherer Service Packs gelöscht (NPR-36815).
* [Handel] Die Deaktivierung eines Stammordners ändert den Deaktivierungsstatus von untergeordneten Produkten in nicht [!DNL Experience Manager Commerce] Konsole; Außerdem wird die Anzahl der untergeordneten Ordner eines Stammordners zum Zeitpunkt der Deaktivierung in der Benutzeroberfläche falsch angezeigt (CQ-4338261).
* [Lokalisierungs-Workflow] Der Inhalt für die Spaltenanpassung und Branding-Anpassung wird nicht im Dialogfeld &quot;Admin Control&quot;lokalisiert. Wählen Sie dazu das Symbol unter dem Profilsymbol in [!DNL Adobe Experience Manager] Posteingang (CQ-4334864).
* [Communities] Der Inhalt innerhalb der Tabelle für Gruppenmitglieder kann nicht angeklickt werden (CQ-4334404).
* [Oak] Der Synchronisierungsprozess für Cold-Standby funktioniert nicht und protokolliert Fehler (CQ-4333868).
* [Platform Foundation-Benutzeroberfläche] [!DNL Experience Manager] Die Startseite wird erneut angezeigt, wenn der Benutzer die [!DNL Adobe Experience Manager] -Symbol bereits auf der Startseite vorhanden ist (CQ-4317409).

### [!DNL Assets] {#assets-65120}

<!--
The following accessibility enhancements are available in [!DNL Assets]:

* enhancement 1
-->

Die folgenden Probleme wurden in [!DNL Assets]:

* Beim Hinzufügen eines Assets oder Ordners (mit `single quote` im Namen) in &quot;Connected Assets&quot;fehlschlägt der Referenzpfad fehl und führt als Ausnahme zum Ergebnis (NPR-37712).
* Beim Hinzufügen von Wasserzeichen zu einem Asset wird das Wasserzeichen unabhängig von der vom Benutzer definierten Farbe immer in schwarzer Farbe angezeigt. (NPR-37720)
* Bei der Verwendung von Connected Assets kann ein Benutzer ohne Administratorrechte nach einem Asset suchen, selbst wenn Benutzer ohne Administratorrechte auf das DAM-Repository zugreifen können (NPR-37644).
* Beim Aktualisieren von Asset-Metadaten mithilfe der Massenbearbeitung werden die auf die Dropdown-Felder angewendeten Änderungen nicht gespeichert und auf die Standardwerte zurückgesetzt. (NPR-37345)
* Löschen eines Ordners in zu langer Zeit, was sich auf die Gesamtleistung auswirkt (NPR-37107).
* Beim Anwenden von Regeln im Metadatenschema kann der Benutzer den vollständigen Wert für die Dropdown-Liste nicht anzeigen `Field Value` und `Field Choices` wenn der Wert größer als das Textfeld ist (CQ-4338074).
* Nach dem Upgrade auf Version 6.5.10.0 spiegelt die Seite mit den Asset-Eigenschaften eine unnötige HTML-Rendering-Meldung wider (CQ-4336994).
* Sortieren der Assets in `List View` funktioniert nicht effektiv (CQ-4335298).
* Beim Freigeben von Assets über den Freigabe-Link werden die Assets in separate Ordner heruntergeladen (CQ-4335000).
* Beim Überprüfen der [!DNL Experience Manager] `Inbox` -Einstellungen `Share` und `Out of office` Registerkarten zeigen nicht übersetzte Inhalte an (CQ-4334858).

* Die folgenden Fehlerkorrekturen beziehen sich auf kaskadierende Metadaten in Asset-Eigenschaften.
   * Ein obligatorisches Dropdown-Menü enthält mehrere Fehlermeldungen für jede Auswahl im Feld mit mehreren Werten (NPR-37859).
   * Für das abhängige nicht bearbeitbare Feld wird nur die letzte Auswahl des übergeordneten Felds gespeichert (NPR-37858).
   * Das abhängige Dropdown-Feld (mehrwertiges Feld) spiegelt den Standardwert für das ausgewählte übergeordnete Dropdown-Menü gelegentlich wider (NPR-37791).


### [!DNL Dynamic Media] {#dynamic-media-65120}

Die folgenden Probleme wurden in [!DNL Dynamic Media]:

* Die Assets eines Ordners, der `renditions` im Ordnernamen nicht synchronisiert werden in `Dynamic Media` (CQ-4338428).
* Beim Erstellen einer Bildvorgabe in `tiff` Format, wird die Vorgabe erstellt, das Format ändert sich jedoch in `jpeg` (CQ-4335985).
* Beim Ändern der `Progressive JPEG Scan` -Wert im Bildvorgabe-Editor wird der Dropdown-Wert immer auf `auto`(CQ-4335971).
* Die Video-Metadaten sind für die `mxf` Videos auf der Seite mit den Asset-Eigenschaften (CQ-4335499).
* Bei der erneuten Verarbeitung der Video-Assets wird die Veröffentlichung der AVS- (Adaptives Video-Set) und Videoausgabeformate vom Veröffentlichungs-Server aufgehoben (CQ-4335461).
* Die erzeugten PDF-Miniaturansichten unterscheiden sich von der ersten Seite der eigentlichen PDF. Einige Teile des Bildes fehlen in der Miniaturansicht (CQ-4315554).
* Die CDN-Invalidierung schlägt mit einer fehlerhaften URL-Antwort fehl, wenn die `companyName` und `companyRoot` unterscheiden sich (CQ-4339896).

### Workflows {#workflows-65120}

* Der Bildlauf funktioniert nicht wie erwartet, wenn Sie einen Filter für Inbox-Elemente anwenden (CQ-4333594).


### [!DNL Forms] {#forms-65120}


>[!NOTE]
>
>* [!DNL Experience Manager Forms] veröffentlicht die Add-on-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.


<!--

**Adaptive Forms**

* Accessibility – When you set the `Wizard` layout for a panel in an adaptive form, the navigation buttons do not have Aria labels and role (NPR-37613).

* Validations on a date field in an adaptive form does not work, as expected (NPR-37556).

* When the label text for the Checkbox and Radio Button components is long, the text does not fit appropriately (NPR-37294).

* When you apply styling changes to the Thank You message of the AEM Forms Container component, the changes do not replicate in the source adaptive form (NPR-37284).

* Differences in the value of the `Switch` component on the user interface and in the backend (NPR-37268).

* When you use the keyboard keys to navigate to the `Submit` option and press the `Enter` key, you can submit the adaptive form multiple times (CQ-4333993).

* The Remove operation for the File Attachment component does not work, as expected (NPR-37376).

* When a label for a field exceeds 1000 characters in an adaptive form that translates to various languages, the dictionary fails to retrieve the translation of the label (CQ-4329290).

**Document Services**

* An error displays while using the Assembler service (NPR-37606):

  ```TXT
    500 Internal Server Error
  ```

* When the document attachments are passed to the Assembler service, the following exception displays (NPR-37582):

  ```TXT
    com.adobe.livecycle.assembler.client.ProcessingException: ⁪: Failed to execute the DDX
  ```

* Missing closing parenthesis from data after converting a PDF document to a PDF-A/1B PDF document (NPR-37608).

**HTML5 Forms**

* When you install AEM 6.5.10.0, the HTML preview for an XDP form does not work (NPR-37503, CQ-4331926).

* Text overlapping issues while migrating the PDF forms to HTML 5 forms in various languages (NPR-37173).

**Letters**

* When you submit a letter and reopen it in HTML view, the position of text document fragments does not remain the same (NPR-37307).

**Forms Workflow**

* In case of embedded container workflow, you get multiple workflow completion emails even after selecting the `Notify on Complete of Container Workflow` option (NPR-37280).

**Foundation JEE**

* After installing AEM 6.5 Forms Service Pack 9, the CRX repository URLs are no longer available (NPR-37592).

**Issues fixed in AEM Forms 6.5.11.1**

>[!NOTE]
>
>If you have not upgraded to AEM 6.5.11.0 Forms, install the AEM Forms 6.5.11.1 add-on package directly. If you have installed AEM 6.5.11.0 Forms, Adobe recommends to upgrade to AEM 6.5.11.1 Forms.

* Submit actions, Send Email and Invoke an AEM Workflow stop working after installing the Forms 6.5.11.0 add-on package.
* CreatePDF operation stops converting Microsoft Word documents to PDF documents after installing the Forms 6.5.11.0 add-on package.
* (JEE Only) Critical security vulnerabilities (CVE-2021-44228 and CVE-2021-45046) reported for Apache Log4j2.
* (JEE only) Assembler DSC in 6.5.11.0 patch contains incorrect metainfo like specification version and impl version.

-->


Informationen zu Sicherheitsupdates finden Sie unter [[!DNL Experience Manager] Seite mit Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.12.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.12.0 ist Experience Manager 6.5 erforderlich. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen.
* Der Service Pack-Download ist auf Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.12.0 mithilfe des Package Managers auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, die [!DNL Adobe Experience Manager] 6.5.12.0-Paket.

### Service Pack installieren {#install-service-pack}

So installieren Sie das Service Pack auf einem [!DNL Adobe Experience Manager] 6.5-Instanz ausführen:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager] -Instanz.

1. Laden Sie das Service Pack herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip).

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. Normalerweise tritt dieses Problem in [!DNL Safari] -Browser, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, automatisch zu installieren [!DNL Experience Manager] 6.5.12.0 auf einer funktionierenden Instanz:

A. Platzieren Sie das Paket in `../crx-quickstart/install` Ordner, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwendung `cmd=install&recursive=true` damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.12.0 unterstützt nicht die Installation von Bootstraps.

**Installation überprüfen**

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge an `Adobe Experience Manager (6.5.12.0)` under [!UICONTROL Installierte Produkte].

1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für die Verwendung mit dieser Version zertifiziert sind, finden Sie in der [technische Anforderungen](/help/sites-deploying/technical-requirements.md).

<!-- 

### Install Adobe Experience Manager Forms add-on package {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Skip if you are not using Experience Manager Forms. Fixes in Experience Manager Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

1. Ensure that you have installed the Adobe Experience Manager Service Pack.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>Experience Manager 6.5.10.0 includes a new version of [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). If you are using an older version of AEM Forms Compatibility Package and updating to Experience Manager 6.5.10.0, install the latest version of the package post installation of Forms Add-On Package.

### Install Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Skip if you are not using AEM Forms on JEE. Fixes in Adobe Experience Manager Forms on JEE are delivered through a separate installer.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes](jee-patch-installer-65.md).

>[!NOTE]
>
>After installing the cumulative installer for Experience Manager Forms on JEE, install the latest Forms add-on package, delete the Forms add-on package from the `crx-repository\install` folder, and restart the server.

-->

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.12.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.12/).

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.12</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstatt im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar`. Es gibt also keine `classifier`, mit `apis` als Wert für die `dependency` -Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die als veraltet gekennzeichnet sind mit [!DNL Experience Manager] 6.5.7.0. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Die **[!UICONTROL AEM Cloud Services-Opt-in]** Der Bildschirm wird nicht mehr unterstützt, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration wurde in Experience Manager 6.5 aktualisiert. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O] und unterstützt die wachsende Rolle von Adobe Launch als Instrument [!DNL Experience Manager] Seiten für Analysen und Personalisierung verwenden, ist der Opt-in-Assistent funktionell irrelevant. | Konfigurieren von Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O] Integrationen über die entsprechenden [!DNL Experience Manager] Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Wenn Sie AEM 6.5 Service Pack 12 installieren und versuchen, die Status-ZIP-Datei herunterzuladen, lädt Experience Manager eine beschädigte Datei herunter.

   >[!CAUTION]
   >
   >Eine neue Version des Pakets &quot;Indexdefinition&quot; wird derzeit entwickelt. Der unten stehende Link wird veröffentlicht, sobald er verfügbar ist.
   >
   >Bis dahin wenden Sie sich für den Hotfix an die Kundenunterstützung .

   <!--
  Download and install [AEM Sites SEO Index Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip) on your AEM instance before downloading the ZIP file to resolve the issue.
  -->

   Laden Sie das AEM Sites SEO Index Package auf Ihre AEM-Instanz herunter und installieren Sie es, bevor Sie die ZIP-Datei herunterladen, um das Problem zu beheben.

* As [!DNL Microsoft Windows Server 2019] unterstützt nicht [!DNL MySQL 5.7] und [!DNL JBoss EAP 7.1], [!DNL Microsoft Windows Server 2019] unterstützt keine Turnkey-Installationen für [!DNL AEM Forms 6.5.10.0].

* Wenn Sie ein Upgrade [!DNL Experience Manager] -Instanz von 6.5 bis 6.5.10.0, können Sie `RRD4JReporter` Ausnahmen `error.log` -Datei. Um das Problem zu beheben, starten Sie die Instanz neu.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 10 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5, die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Benutzer können einen Ordner in einer Hierarchie in [!DNL Assets] und veröffentlichen Sie einen verschachtelten Ordner in [!DNL Brand Portal]. Der Titel des Ordners wird jedoch nicht aktualisiert in [!DNL Brand Portal] bis die Veröffentlichung des Stammordners erfolgt ist.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

* Beim Versuch, Inhaltsfragmente oder Sites/Seiten zu verschieben/zu löschen/zu veröffentlichen, tritt ein Problem beim Abrufen von Inhaltsfragmentverweisen auf, da die Hintergrundabfrage fehlschlägt. d. h. die Funktionalität funktioniert nicht.
Um den korrekten Vorgang sicherzustellen, müssen Sie die folgenden Eigenschaften zum Indexdefinitionsknoten hinzufügen `/oak:index/damAssetLucene` (Eine Neuindizierung ist nicht erforderlich) :

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-Bundles und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die in [!DNL Experience Manager] 6.5.12.0:

* [Liste der in Experience Manager 6.5.12.0 enthaltenen OSGi-Bundles](assets/65120_bundles.txt)

* [Liste der in Experience Manager 6.5.12.0 enthaltenen Inhaltspakete](assets/65120_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Siehe [Kontaktaufnahme mit dem Adobe-Support](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

