---
title: '[!DNL Experience Manager] 6.5 Service Pack - Versionshinweise'
description: Spezifische Versionshinweise zu [!DNL Adobe Experience Manager] 6.5 Service Pack 8
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 60764db23115e7f548a82a67955331da2b858973
workflow-type: tm+mt
source-wordcount: '2812'
ht-degree: 5%

---


# [!DNL Adobe Experience Manager] 6.5 Service Pack - Versionshinweise  {#aem-service-pack-release-notes}

## Versionsinformationen {#release-information}

| Produkte | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Version | 6.5.8.0 |
| Typ | Service Pack-Version |
| Datum | 11. März 2021 |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.8.zip) |

<!-- TBD: Update the SD link when SP8 is available. Same link is duplicated below in install -->

## Was ist in [!DNL Adobe Experience Manager] 6.5.8.0 {#what-s-included-in-aem} enthalten

[!DNL Adobe Experience Manager] 6.5.8.0 umfasst neue Funktionen, wichtige kundenspezifische Verbesserungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht werden. Das Service Pack ist auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.8.0 eingeführt wurden, sind:

<!-- TBD:
* Using the Connected Assets functionality, it is now possible to connect up to 3 [!DNL Sites] instances with 1 [!DNL Assets] instances. The configuration user interface now allows the administrators to provide the details of these [!DNL Sites] instances. -->

* Bei Verwendung der Funktion [Verbundene Assets](/help/assets/use-assets-across-connected-assets-instances.md) können Sie jetzt eine Liste aller [!DNL Sites]-Seiten, die das Asset verwenden, Ansicht haben. Diese Verweise auf ein Asset sind auf der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar. Dadurch erhalten Administratoren, Marketingexperten und Bibliothekare eine vollständige Ansicht der Asset-Nutzung, was eine bessere Verfolgung, Verwaltung und Markenkonsistenz ermöglicht.

* Beim Löschen eines Assets, auf das auf einer Webseite verwiesen wird, zeigt [!DNL Experience Manager] [eine Warnung](/help/assets/use-assets-across-connected-assets-instances.md#asset-usage-references) an. Sie können das Löschen eines referenzierten Assets erzwingen oder die auf der Seite [!DNL Properties] des Assets angezeigten Verweise überprüfen und ändern. Durch Klicken auf die Verweise werden die lokalen und Remote-Seiten [!DNL Sites] geöffnet.

* Sortieren der für die Aktualisierung verfügbaren Live Copy-Seiten mit den Eigenschaften [!UICONTROL Name], [!UICONTROL Letztes Änderungsdatum,] und [!UICONTROL Letztes Rollout-Datum].

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.6 aktualisiert. <!-- TBD: Mention the version -->

Eine vollständige Liste der in [!DNL Experience Manager] 6.5.8.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 8](new-features-latest-service-pack.md).

Im Folgenden finden Sie die Liste der Fehlerbehebungen in der Version 6.5.8.0.[!DNL Experience Manager]

### [!DNL Sites] {#sites-6580}

* Wenn eine Seite in den Blueprint verschoben wird, wird das Ziel der Links nicht aktualisiert (NPR-35724).
* Der Zehn-basierte Player kann sich bei bestimmten Browsern nicht authentifizieren. Das Problem tritt bei Browsern auf, die dasselbe Attribut site=none nicht unterstützen (NPR-35589).
* Ein nicht gesperrter reaktionsfähiger Container zeigt keine zulässigen Komponenten an (NPR-35565).
* Wenn Sie eine Live-Kopie einer neu hinzugefügten Seite erstellen, erstellt der Sprachcode Übergeordnet zwei Kopien für jede Domäne (NPR-35545).
* Deadlock in der SCR-Komponentenregistrierung, wenn viele Threads aufgrund des Zeitschalters `org.apache.felix.scr.impl.ComponentRegistry` blockiert werden. Infolgedessen reagiert [!DNL Experience Manager] nicht mehr auf unbestimmte Zeit (GRANITE-33125,FELIX-6252).
* Wenn Sie ein bestimmtes Asset in der Seitenleiste suchen, enthält das Ergebnis einige nicht durchsuchte Assets (NPR-35524).
* Wenn Sie SSL für eine Experience Manager-Instanz aktivieren, wird der Kontextpfad entfernt (NPR-35477).
* Wenn Sie eine Liste erstellen, Text als erstes Element hinzufügen, eine Tabelle als zweites Element hinzufügen und eine Liste in die Tabelle einfügen, verzerrt die übergeordnete Liste (NPR-35465).
* Wenn Sie verschiedene Plugins für aufeinander folgende Elemente der Liste verwenden, wird ein zusätzliches <br>-Tag zu den Elementen der Liste hinzugefügt (NPR-35464).
* Wenn eine Liste zwischen zwei Absätzen platziert wird, können Sie der Liste keine Tabelle hinzufügen (NPR-35356).
* Wenn Sie eine Aktualisierung AEM Instanz von AEM 6.3 auf AEM 6.5 durchführen, dauert die Aktualisierung länger bis zum Beginn (NPR-35323).
* Wenn Sie ein AEM Asset mit einer Klammer () replizieren. im Namen die Replizierung fehlschlägt (GRANITE-27004, NPR-35315).
* Wenn Sie Überschriften zu einem Rich-Text-Editor hinzufügen, ist die Absatzschaltfläche deaktiviert (NPR-35256).
* Wenn Sie ein Element zu einer vorhandenen Liste hinzufügen, wird die folgende reduzierbare oder umschaltbare Liste (NPR-35206) gelöscht.
* Wenn die Option &quot;Rollout-Seite&quot;ausgewählt ist, wird ein Dialogfeld mit allen verfügbaren Live-Kopien angezeigt und die automatische Rollout erfolgt. Die Live-Kopien der Seiten werden ohne Benutzeraktion in allen Regionen veröffentlicht (NPR-35138).
* Wenn Sie die Option &quot;Untergeordnete Elemente einschließen&quot;verwenden, werden nicht alle Seiten mit der Option &quot;Veröffentlichung verwalten&quot;Liste. Es werden nur 22 Seiten aufgelistet (NPR-35086).
* Wenn eine Richtlinie bearbeitet wird, behält die Textkomponente die Richtlinienänderungen nicht bei (NPR-35070).
* Beim Einzug einiger Elemente in eine nummerierte Liste behalten alle Elemente die gleiche Nummer bei, obwohl die Nummerierung bei Elementen mit demselben Einzug von 1 Beginn sein sollte (CQ-4313011).
* Wenn die Minimierung aktiviert ist, können Sie keine Seite oder Komponente bearbeiten. Die Probleme begannen nach der Installation von AEM 6.5 Service Pack 7 (CQ-4311133).
* Omni-Filter für Suche und Asset geben irrelevante oder keine Ergebnisse zurück (CQ-4312322, NPR-35793).
* Wenn mehrere Seiten gleichzeitig auf eine Client-Bibliothek zugreifen, kann der HTML-Bibliotheksmanager die Client-Bibliothek nicht laden. Dies führt zur fehlerhaften Darstellung von Seiten (NPR-35538).
* Der Kontextpfad wird automatisch entfernt, wenn Sie ein SSL in [!DNL Experience Manager] (NPR-35294) einrichten.
* Der Package Manager meldet Benutzer nicht ab, nachdem er auf die Option &quot;Abmelden&quot;geklickt hat (NPR-35160).

### [!DNL Assets] {#assets-6580}

[!DNL Adobe Experience Manager] 6.5.8.0  [!DNL Assets] behebt die folgenden Probleme und bietet die folgenden Erweiterungen.

* Beim Wiederherstellen einer früheren Version eines Assets wird das Ereignis DamEvent.Type RESTORED nicht in der OSGi-Konsole (NPR-35789) ausgelöst.
* `IndexWriter.merge` verursacht  `OutOfMemoryError` Fehler, da intelligente Tagging-Funktionen große  `/oak:index/lucene` und  `/oak:index/ntBaseLucene` Indizes erstellen (NPR-35651).
* Beim Versuch, einen Ordner mit dem Namen &quot;[!UICONTROL Asset Contribution]&quot;mit Multibyte-Zeichen im Namen zu speichern, wird eine Fehlermeldung angezeigt (NPR-35605).
* Wenn Metadaten-Untertypfelder in Kaskadenform verwendet werden, tritt der Fehler &quot;Bitte dieses Feld ausfüllen&quot;auf (NPR-35643).
* Wenn ein vorhandenes Asset auf die [!DNL Assets]-Benutzeroberfläche gezogen und eine neue Version erstellt wird, sind die Änderungen in den Metadaten nicht beständig (NPR-34940).
* Beim Erstellen von Regeln im Metadaten-Schema-Editor für ein Kaskadenmenü wiederholt die Option [!UICONTROL Abhängig von] denselben Namen (NPR-35596).
* Ähnlichkeitssuche funktioniert nach der Bearbeitung von [!UICONTROL Assets Admin Search Rail] (NPR-35588) nicht.
* Wenn Sie in einem Ordner die Asset-Suche in der linken Leiste öffnen, indem Sie auf [!UICONTROL Filter] klicken, funktioniert der Filter unter [!UICONTROL Status] > [!UICONTROL Checkout] > [!UICONTROL Checked out] nicht (NPR-35530).
* Wenn Sie versuchen, alle intelligenten Tags eines Assets zu löschen und die Änderungen zu speichern, werden die Tags nicht entfernt. Die Benutzeroberfläche zeigt jedoch an, dass die Änderungen gespeichert wurden (NPR-35519).
* Benutzer können Assets nicht in der Ansicht Liste in einem bestellbaren Ordner (NPR-35516) neu anordnen oder sortieren.
* Wenn Sie das Standard-Metadaten-Schema bearbeiten, wird das Tagfeld auf der Seite [!UICONTROL Eigenschaften] des Assets in ein Textfeld umgewandelt. Die Änderung ermöglicht es unbekannten Benutzern, On-Demand-Tags hinzuzufügen, und die Tags werden als Zeichenfolge im Repository gespeichert (NPR-35478).
* Wenn Sie beim Herunterladen eines Assets einen Namen angeben, der über keine gültige E-Mail-Adresse verfügt, ist die Option zum Herunterladen nicht verfügbar. Wenn jedoch eine andere Option im Downloaddialogfeld ausgewählt ist, ist die Schaltfläche aktiviert, es wird jedoch keine E-Mail gesendet (NPR-35365).
* Benutzer können keine Assets einchecken, nachdem sie die unter [!DNL Adobe InDesign] bearbeitet haben, und erhalten einen Fehler wegen fehlender Berechtigungen (NPR-35341).
* Die JavaScript-Bibliothek &quot;Handlebars&quot;wurde auf Version 4.7.6 (NPR-35333) aktualisiert.
* Die Benutzeroberfläche des Metadaten-Editors funktioniert nicht mehr wie erwartet, wenn Sie von der Massenbearbeitung von Metadaten und der Deaktivierung von Elementen ausgehen, bis ein einzelnes Element ausgewählt ist (NPR-35144).
* Bei der globalen Navigation wird nicht die richtige Konsole geöffnet, wenn auf eine `assets.html`-Seite geklickt wird (CQ-4312311).
* [!DNL Assets] zeigt keine RGB-Darstellung für ein Asset mit RGB-Darstellung an (CQ-4310190).
* Die Option [!UICONTROL Relate] im Menü wird auf der Seite [!UICONTROL Eigenschaften] (CQ-4310188) nicht richtig angezeigt.
* Wenn der Filter &quot;Dateityp&quot;für Dokumente verwendet wird, um Assets zu suchen und eine intelligente Sammlung zu erstellen, wird der Filter beim Zugriff auf die Sammlung nicht angewendet. Stattdessen werden alle Assets in der Suche angezeigt (NPR-35759).
* Sie können Assets nicht aus der [!DNL Assets]-Benutzeroberfläche (NPR-35901) ziehen und in einem Leuchtkasten hinzufügen.
* Wenn nach dem Auflösen des Namenskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben (CQ-4313594).
* Wenn Sie die Asset-Suche mit einem Suchfilter oder einer Vorhersage filtern, ein Asset zur Ansicht oder Bearbeitung öffnen und zur Suchergebnisseite zurückkehren, funktioniert der Filter nicht. Alle gesuchten Assets werden ungefiltert aufgeführt (NPR-35913).

#### [!DNL Dynamic Media] {#dynamic-media-6580}

* Die URL-Option für die DRM-Bildvorgabe ist auf der Seite mit den Asset-Details aktiviert. Jetzt stehen sowohl URL- als auch wiederaufladbare Optionen auf der Seite mit den Asset-Details zur Verfügung, wenn im Abschnitt &quot;Dynamische Darstellungen&quot;die Bildvorgabe wiedergegeben wird. (CQ-4311241)
* Interaktive Medienkomponente: Interaktives Video funktioniert nicht, wenn der Benutzer über [!DNL Experience Manager] mit selektiver Veröffentlichungskonfiguration verfügt (CQ-4311054).
* Wenn Sie Assets über Ordner verschieben, erfolgt die Synchronisierung zwischen [!DNL Experience Manager] und [!DNL Dynamic Media–Scene7] über die API sehr langsam (CQ-4310001).
* Bei Verwendung von Omniture Search nimmt die Größe der Protokolle signifikant zu (CQ-4309153).
* Wenn die selektive Synchronisierung aktiviert ist und ein Asset in einen Synchronisierungsordner kopiert (nicht verschoben) wird, wird es nicht wie erwartet synchronisiert (CQ-4307122).
* Bei hochgeladenen Assets, die automatisch in DM veröffentlicht werden, wird der Status nicht auf AEM veröffentlicht angezeigt. Außerdem zeigt die Statusspalte &quot;Dynamic Media Publish&quot;nicht den korrekten Status &quot;Veröffentlicht&quot;an (CQ-4306415).
* Wenn ein Asset auf [!DNL Experience Manager] veröffentlicht wird und auf [!DNL Dynamic Media] bei Aktivierung veröffentlicht wird, wird der Metadatenwert `scene7FileStatus` nicht erwartungsgemäß aktualisiert (CQ-4308269).
* Beim Bearbeiten des Profils zeigt [!DNL Experience Manager] nicht die für die Videovorgabe festgelegten Höhen- und Bitratenwerte an. Die Felder werden leer angezeigt (CQ-4311828).

### [!DNL Commerce] {#commerce-6580}

* Es kann kein benutzerdefinierter Tag für alle Produkte in Commerce erstellt werden (CQ-4310682).

* Das Update der Produktverweis-Referenz führt dazu, dass Replizierungsthreads im Wartezustand sind, bis der ProductAssetListener-Thread seine Verpflichtungen zum JCR (NPR-35269) erfüllt.

### Plattform {#platform-6580}

* Wenn Sie eine Coral Tab-Ansicht ohne Registerkarten verwenden und dann einen Foundation-Validator Trigger haben, tritt der folgende Fehler auf (NPR-35636):

   ```TXT
    Uncaught TypeError: Cannot set property 'invalid' of undefined
     at enable (foundation.js:10703)
     at foundation.js:10710
   ```

* Die SCD-Weiterreplikation schlägt beim Löschen von Ereignissen für Knoten fehl, die ein Komma im Namen enthalten (NPR-35191).

* Nach dem Upgrade auf AEM 6.5.7 ist der Beginn builds fehlgeschlagen. Der Grund dafür ist, dass eine alte Version oder kein Jackson-Core in die uber-jar (GRANITE-33006) eingebettet ist.

### Benutzeroberfläche {#ui-6580}

* Wenn Sie für Dokumente in einem Ordner in der Assets-Konsole von der Ansicht &quot;Card Ansicht&quot;zur &quot;Liste&quot;wechseln, funktioniert die Sortierung nicht ordnungsgemäß (NPR-35842).

* Wenn Sie Text in einer Textkomponente mit Hyperlinks versehen, zeigt die Suchfunktion keine geeigneten Ergebnisse an (NPR-35849).

* Wenn ein Wert nicht für ein unsichtbares Feld bereitgestellt wird, das als &quot;Erforderlich&quot;gekennzeichnet ist, wird verhindert, dass Sie eine Komponente speichern (NPR-35219).

### Integrationen {#integrations-6580}

* Wenn Sie verschiedene Werte für IMS Mandant ID und Zielgruppe Client Code verwenden, kann [!DNL Experience Manager] nicht mit [!DNL Adobe Target] (NPR-35342) integriert werden.

### Übersetzungsprojekte {#translation-6580}

* Probleme beim Exportieren oder Importieren eines Übersetzungsauftrags in [!DNL Experience Manager] (NPR-35259).

### Campaign {#campaign-6580}

* Wenn Sie in der Touch-Benutzeroberfläche eine Kampagne mit einer vordefinierten Vorlage erstellen und im Dialogfeld &quot;Seiteneigenschaften&quot;die Registerkarte &quot;E-Mail&quot;öffnen, bleibt die Personalisierungsvariable für die Betreff- und Textkörperfelder deaktiviert (CQ-4312388).

### [!DNL Communities] {#communities-6580}

* Wenn Sie einer Community-Gruppe eine Seitenstruktur hinzufügen, wird der Titel [!UICONTROL Gruppe] im Breadcrumb in den Titel der ersten [!UICONTROL Seite] (NPR-35803) geändert.
* Im Gegensatz zu Moderatoren ist ein Standard-Community-Mitglied nicht in der Lage, auf Beiträge zuzugreifen und diese zu bearbeiten (NPR-35339).
* Zugriffskontrolle und Diensteverweigerung mit DSRPReindexServlet unterbrochen, wodurch die Communities-Website heruntergefahren wird, bis die Indexierung abgeschlossen ist (NPR-35591).
* Wenn Sie [!UICONTROL Alle Benutzer] aus dem Feld [!UICONTROL Administratoren] entfernen, werden sie nicht tatsächlich aus dem Back-End entfernt (NPR-35592, NPR-35611).
* Die Komponente [!UICONTROL Nachricht erstellen] gibt kein Ergebnis zurück, wenn der eingegebene Text teilweise übereinstimmt (NPR-35666).

### [!DNL Brand Portal] {#brandportal-6580}

* Wenn Sie einem Ordner vom Typ [!UICONTROL Asset Contribution] einen Member hinzufügen, wird in der Benutzeroberfläche die Beschriftung [!UICONTROL Hinzufügen Benutzer oder Gruppe] angezeigt. Es werden jedoch nur aktive Benutzer des Markenportals unterstützt, nicht Gruppen (NPR-35332).

### [!DNL Forms] {#forms-6580}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.

Informationen zu Sicherheitsaktualisierungen finden Sie unter [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren Sie 6.5.8.0 {#install}

**Setup-Anforderungen und weitere Informationen**

* Experience Manager 6.5.8.0 erfordert Experience Manager 6.5. Detaillierte Anweisungen finden Sie in der [Aktualisierungsdokumentation](/help/sites-deploying/upgrade.md).
* Der Service Pack-Download ist auf Adobe [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.8.0 auf einer der Autoreninstanzen mit Package Manager.

>[!NOTE]
>
>Adobe rät davon ab, das [!DNL Adobe Experience Manager] 6.5.8.0-Paket zu entfernen oder zu deinstallieren.

### Dienstpaket {#install-service-pack} installieren

Gehen Sie wie folgt vor, um das Service Pack auf einer [!DNL Adobe Experience Manager] 6.5-Instanz zu installieren:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Updatemodus befindet (was der Fall ist, wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt auch einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.8.zip) herunter.

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, dass Sie auf die Stabilisierung der Fehlerprotokolle warten, bevor Sie auf die Bereitstellung zugreifen. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles, bevor Sie sicherstellen, dass die Installation erfolgreich ist. Normalerweise passiert dies bei [!DNL Safari], kann aber gelegentlich auch in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, Adobe Experience Manager 6.5.8.0 automatisch auf einer Arbeitsinstanz zu installieren:

A. Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API aus Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.8.0 unterstützt keine Bootstrap-Installation.

**Bestätigen der Installation**

1. Auf der Seite mit den Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.8.0)` unter [!UICONTROL Installierte Produkte] angezeigt.

1. Alle OSGi-Pakete sind entweder **[!UICONTROL ACTIVE]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Web-Konsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Web-Konsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für die Verwendung mit dieser Version zertifiziert sind, finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.8.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.8/) verfügbar.

Informationen zum Verwenden von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und Einbeziehen der folgenden Abhängigkeit in Ihr Projekt-POM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.8</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte stehen im Maven Central Repository anstelle der Adobe Public Maven Repository (`repo.adobe.com`) zur Verfügung. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Es gibt also kein `classifier`-Tag mit `apis` als Wert für das `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Im Folgenden finden Sie eine Liste von Funktionen, die mit [!DNL Experience Manager] 6.5.7.0 als veraltet markiert wurden. Funktionen werden zunächst als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option ist in der Regel verfügbar.

Überprüfen Sie, ob Sie eine Funktion oder eine Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm **[!UICONTROL AEM Cloud Services Opt-In]** wird nicht mehr unterstützt. Der Experience Manager- und Adobe Target-Integrationsassistent wurde in Experience Manager 6.5 aktualisiert, um die Adobe Target Standard-API zu unterstützen, die die Authentifizierung über Adobe IMS und I/O verwendet, und die wachsende Rolle, die Adobe Launch bei der Instrumentierung von Experience Manager-Seiten für Analysen und Personalisierung spielt, ist nun funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O]-Integrationen über die entsprechenden Experience Manager-Cloud-Dienste. |
| Connectoren | Die Adobe JCR Connector for Microsoft SharePoint 2010 und Microsoft SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5 auf 6.5.8.0 aktualisieren, können Sie `RRD4JReporter` Ausnahmefehler in der `error.log`-Datei Ansicht haben. Starten Sie die Instanz neu, um das Problem zu beheben.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 5 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie Ihres benutzerdefinierten Assets Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfskopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mit der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Wenden Sie sich an den Kundendienst der Adobe, wenn beim Bearbeiten und Erstellen von Kaskadenregeln im Schema [!UICONTROL Ordnermetadaten Forms Editor] und [!UICONTROL Metadaten-Schema Forms Editor] Probleme auftreten, indem Sie das Dialogfeld [!UICONTROL Regel definieren] verwenden. Die bereits erstellten und gespeicherten Regeln funktionieren erwartungsgemäß.

* Wenn ein Ordner in der Hierarchie in [!DNL Experience Manager Assets] umbenannt wird und der verschachtelte Ordner, der ein Asset enthält, in [!DNL Brand Portal] veröffentlicht wird, wird der Titel des Ordners erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Wenn der Assistent [!UICONTROL Konfiguration von verbundenen Assets] nach der Installation eine Fehlermeldung 404 zurückgibt, müssen Sie die `cq-remotedam-client-ui-content`- und `cq-remotedam-client-ui-components`-Pakete manuell mit dem Package Manager neu installieren.

* Die folgenden Fehler- und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mit der Target Standard-API (IMS-Authentifizierung) konfiguriert wird, führt das Exportieren von Erlebnisfragmenten in die Zielgruppe dazu, dass falsche Angebot erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregat-Funktionen wie SUM, MAX und MIN verwendet werden. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn das Asset über den Viewer für das kaufbare Banner in der Vorschau angezeigt wird.

## OSGi-Pakete und -Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Inhaltspakete in [!DNL Experience Manager] 6.5.8.0:

* [Liste der OSGi-Pakete in Experience Manager 6.5.8.0](assets/6580_bundles.txt)

* [Liste der in Experience Manager 6.5.8.0 enthaltenen Inhaltspakete](assets/6580_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Siehe [Kontaktieren der Adobe Kundenunterstützung](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 Versionshinweise](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] Produktseite](https://www.adobe.com/de/marketing/experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

