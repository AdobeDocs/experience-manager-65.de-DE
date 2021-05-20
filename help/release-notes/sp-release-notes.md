---
title: '[!DNL Experience Manager] 6.5 Service Pack - Versionshinweise'
description: Spezifische Versionshinweise für  [!DNL Adobe Experience Manager] 6.5 Service Pack 8
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 024f03c04a980c544ac59e736caeaa24f7565582
workflow-type: tm+mt
source-wordcount: '3409'
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

## Was ist enthalten in [!DNL Adobe Experience Manager] 6.5.8.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.8.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen sowie Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der Veröffentlichung der Version 6.5 im April 2019 veröffentlicht wurden. Das Service Pack ist auf [!DNL Adobe Experience Manager] 6.5 installiert.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.5.8.0 eingeführt wurden, sind:

<!-- TBD:
* Using the Connected Assets functionality, it is now possible to connect up to 3 [!DNL Sites] instances with 1 [!DNL Assets] instances. The configuration user interface now allows the administrators to provide the details of these [!DNL Sites] instances. -->

* Bei Verwendung der Funktion [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md) können Sie jetzt eine Liste aller [!DNL Sites]-Seiten anzeigen, die das Asset verwenden. Diese Verweise auf ein Asset sind auf der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar. Dadurch erhalten Administratoren, Marketing-Experten und Bibliothekare einen vollständigen Überblick über die Asset-Nutzung, was eine bessere Nachverfolgung, Verwaltung und Markenkonsistenz ermöglicht.

* Beim Löschen eines Assets, auf das auf einer Webseite verwiesen wird, zeigt [!DNL Experience Manager] [eine Warnung](/help/assets/use-assets-across-connected-assets-instances.md#asset-usage-references) an. Sie können das Löschen eines referenzierten Assets erzwingen oder die Verweise überprüfen und ändern, die auf der Seite [!DNL Properties] des Assets angezeigt werden. Durch Klicken auf die Verweise werden die lokalen und Remote-Seiten [!DNL Sites] geöffnet.

* Sortieren der für den Rollout verfügbaren Live Copy-Seiten mithilfe der Eigenschaften [!UICONTROL Name], [!UICONTROL Letztes Änderungsdatum,] und [!UICONTROL Letztes Rollout-Datum].

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf  1.22.6 aktualisiert. <!-- TBD: Mention the version -->

Eine vollständige Liste der in [!DNL Experience Manager] 6.5.8.0 eingeführten Funktionen und Verbesserungen finden Sie unter [Neue Funktionen in [!DNL Adobe Experience Manager] 6.5 Service Pack 8](new-features-latest-service-pack.md).

Im Folgenden finden Sie eine Liste der Fehlerbehebungen in [!DNL Experience Manager] Version 6.5.8.0.

### [!DNL Sites] {#sites-6580}

* Wenn eine Seite in einen Blueprint verschoben wird, wird das Ziel der Links nicht aktualisiert (NPR-35724).
* Der Tizen-basierte Player kann bei bestimmten Browsern nicht authentifiziert werden. Das Problem tritt bei Browsern auf, die das Attribut &quot;samesite=none&quot;nicht unterstützen (NPR-35589).
* Ein entsperrter responsiver Container zeigt keine zulässigen Komponenten an (NPR-35565).
* Wenn Sie eine Live Copy einer neu hinzugefügten Seite erstellen, erstellt der Übergeordnete Sprachcode zwei Kopien für jede Domäne (NPR-35545).
* Sperre in der SCR Component Registry, wenn viele Threads aufgrund von `org.apache.felix.scr.impl.ComponentRegistry` Timer blockiert werden. Daher reagiert [!DNL Experience Manager] nicht länger auf unbestimmte Zeit (GRANITE-33125,FELIX-6252).
* Wenn Sie ein bestimmtes Asset in der Seitenleiste suchen, enthält das Ergebnis einige nicht durchsuchte Assets (NPR-35524).
* Wenn Sie SSL für eine Experience Manager-Instanz aktivieren, wird der Kontextpfad entfernt (NPR-35477).
* Wenn Sie eine Liste erstellen, Text als erstes Element hinzufügen, eine Tabelle als zweites Element hinzufügen und eine Liste innerhalb der Tabelle hinzufügen, verzerrt die übergeordnete Liste (NPR-35465).
* Wenn Sie verschiedene Plugins für aufeinander folgende Listenelemente verwenden, wird den Listenelementen ein zusätzliches <br>-Tag hinzugefügt (NPR-35464).
* Wenn eine Liste zwischen zwei Absätzen platziert wird, können Sie der Liste keine Tabelle hinzufügen (NPR-35356).
* Wenn Sie ein Upgrade der AEM-Instanz von AEM 6.3 auf AEM 6.5 starten, dauert es länger, bis die Aktualisierungsinstanz gestartet wird (NPR-35323).
* Wenn Sie ein AEM Asset replizieren, das eine Klammer () enthält. im Namen schlägt die Replikation fehl (GRANITE-27004, NPR-35315).
* Wenn Sie einem Rich-Text-Editor Überschriften hinzufügen, ist die Absatzschaltfläche deaktiviert (NPR-35256).
* Wenn Sie ein Element zu einer vorhandenen Liste hinzufügen, wird die folgende ausblendbare oder umschaltbare Liste gelöscht (NPR-35206).
* Wenn die Option &quot;Rollout-Seite&quot;ausgewählt ist, wird ein Dialogfeld mit allen verfügbaren Live Copies angezeigt und der automatische Rollout erfolgt. Die Live Copies von Seiten werden für alle Regionen ohne Benutzeraktion bereitgestellt. (NPR-35138)
* Wenn Sie die Option Untergeordnete Elemente einschließen verwenden, werden nicht alle Seiten in der Option Veröffentlichung verwalten aufgelistet. Es werden nur 22 Seiten aufgelistet (NPR-35086).
* Wenn eine Richtlinie bearbeitet wird, behält die Textkomponente die Richtlinienänderungen nicht bei (NPR-35070).
* Beim Einzug einiger Elemente in eine nummerierte Liste behalten alle Elemente dieselbe Nummer bei, obwohl die Nummerierung für Artikel mit demselben Einzug bei 1 beginnen sollte (CQ-4313011).
* Wenn die Minimierung aktiviert ist, können Sie keine Seite oder Komponente bearbeiten. Die Probleme begannen nach der Installation von AEM 6.5 Service Pack 7 (CQ-4311133).
* Omni-Such- und Asset-Filter geben irrelevante oder keine Ergebnisse zurück (CQ-4312322, NPR-35793).
* Wenn mehrere Seiten gleichzeitig auf eine Client-Bibliothek zugreifen, kann der HTML-Bibliotheksmanager die Client-Bibliothek nicht laden. Dies führt zur falschen Darstellung von Seiten (NPR-35538).
* Der Kontextpfad wird automatisch entfernt, wenn Sie eine SSL in [!DNL Experience Manager] einrichten (NPR-35294).
* Der Paketmanager meldet Benutzer nicht ab, nachdem er auf die Option &quot;Abmelden&quot;geklickt hat (NPR-35160).

### [!DNL Assets] {#assets-6580}

[!DNL Adobe Experience Manager] 6.5.8.0  [!DNL Assets] behebt die folgenden Probleme und bietet die folgenden Verbesserungen.

* Beim Wiederherstellen einer vorherigen Version eines Assets wird das Ereignis DamEvent.Type RESTORED nicht in der OSGi-Konsole ausgelöst (NPR-35789).
* `IndexWriter.merge` verursacht  `OutOfMemoryError` Fehler, da Smart-Tagging-Funktionen große  `/oak:index/lucene` und  `/oak:index/ntBaseLucene` Indizes erstellen (NPR-35651).
* Beim Speichern eines Ordners vom Typ [!UICONTROL Asset-Beitrag] mit Multibyte-Zeichen im Namen wird eine Fehlermeldung angezeigt (NPR-35605).
* Wenn kaskadierende Metadaten-Untertypfelder verwendet werden, tritt der Fehler &quot;Bitte dieses Feld ausfüllen&quot;auf (NPR-35643).
* Wenn ein vorhandenes Asset in die [!DNL Assets]-Benutzeroberfläche gezogen und eine neue Version erstellt wird, sind die Änderungen in den Metadaten nicht persistent (NPR-34940).
* Beim Erstellen von Regeln im Metadatenschema-Editor für ein kaskadierendes Menü wiederholt die Option [!UICONTROL Abhängig von] denselben Namen (NPR-35596).
* Ähnlichkeitssuche funktioniert nicht nach der Bearbeitung von [!UICONTROL Asset-Admin-Suchschiene] (NPR-35588).
* Wenn Sie in einem Ordner die Asset-Suche in der linken Leiste öffnen, indem Sie auf [!UICONTROL Filter] klicken, funktioniert der Filter in [!UICONTROL Status] > [!UICONTROL Checkout] > [!UICONTROL Ausgecheckt] nicht (NPR-35530).
* Wenn Sie versuchen, alle Smart-Tags eines Assets zu löschen und die Änderungen zu speichern, werden die Tags nicht entfernt. Die Benutzeroberfläche zeigt jedoch an, dass die Änderungen gespeichert werden (NPR-35519).
* Benutzer können Assets in der Listenansicht nicht in einem sortierbaren Ordner neu anordnen oder sortieren (NPR-35516).
* Wenn Sie das Standard-Metadatenschema bearbeiten, wird das Feld &quot;Tags&quot;auf der Seite [!UICONTROL Eigenschaften] des Assets in ein Textfeld geändert. Die Änderung ermöglicht es unbekannten Benutzern, On-Demand-Tags hinzuzufügen, und die Tags werden als Zeichenfolge im Repository gespeichert (NPR-35478).
* Wenn Sie beim Herunterladen eines Assets einen Namen angeben, der keine gültige E-Mail-Adresse aufweist, ist die Download-Option nicht verfügbar. Wenn jedoch eine andere Option im Download-Dialogfeld ausgewählt ist, ist die Schaltfläche aktiviert, aber keine E-Mail gesendet (NPR-35365).
* Benutzer können keine Assets einchecken, nachdem sie diese in [!DNL Adobe InDesign] bearbeitet haben, und erhalten einen Fehler wegen fehlender Berechtigungen. (NPR-35341)
* Die Handlebars-JavaScript-Bibliothek wurde auf Version 4.7.6 aktualisiert (NPR-35333).
* Die Benutzeroberfläche des Metadaten-Editors funktioniert nicht mehr wie erwartet, wenn Sie mit der Massenbearbeitung von Metadaten beginnen und die Auswahl von Elementen aufheben, bis ein einzelnes Element ausgewählt bleibt (NPR-35144).
* Die globale Navigation öffnet nicht die richtige Konsole, wenn von der Seite `assets.html` aus darauf geklickt wird (CQ-4312311).
* [!DNL Assets] zeigt keine RGB-Wiedergabe für ein Asset mit RGB-Wiedergabe an (CQ-4310190).
* Die Option [!UICONTROL Relate] im Menü wird auf der Seite [!UICONTROL Eigenschaften] nicht richtig angezeigt (CQ-4310188).
* Wenn der Dateitypfilter für Dokumente verwendet wird, um Assets zu suchen und eine Smart-Sammlung zu erstellen, wird der Filter beim Zugriff auf die Sammlung nicht angewendet. Stattdessen werden alle Asset-Typen bei der Suche angezeigt (NPR-35759).
* Sie können keine Assets in eine Lightbox aus der [!DNL Assets]-Benutzeroberfläche ziehen (NPR-35901).
* Wenn nach dem Auflösen des Namenskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben. (CQ-4313594)
* Wenn Sie die Asset-Suche mit einem Suchfilter oder einer Eigenschaft filtern, ein Asset öffnen, um es anzuzeigen oder zu bearbeiten, und zur Seite mit den Suchergebnissen zurückkehren, funktioniert der Filter nicht. Alle gesuchten Assets werden ungefiltert aufgelistet (NPR-35913).

#### [!DNL Dynamic Media] {#dynamic-media-6580}

* Die URL-Option für die Bildvorgabe RESS ist auf der Asset-Detailseite aktiviert. Jetzt sind die Optionen URL und RESS auf der Seite mit den Asset-Details verfügbar, wenn die Bildvorgabe RESS im Abschnitt Dynamische Ausgabeformate ausgewählt ist. (CQ-4311241)
* Interaktive Medienkomponente: Interaktives Video funktioniert nicht, wenn der Benutzer über [!DNL Experience Manager] mit selektiver Veröffentlichungskonfiguration verfügt (CQ-4311054).
* Wenn Sie Assets über Ordner hinweg verschieben, erfolgt die Synchronisation zwischen [!DNL Experience Manager] und [!DNL Dynamic Media–Scene7] über die API nur sehr langsam (CQ-4310001).
* Bei Verwendung von Omnisearch nimmt die Größe der Protokolle erheblich zu (CQ-4309153).
* Wenn die selektive Synchronisierung aktiviert ist und ein Asset in einen Synchronisierungsordner kopiert (nicht verschoben) wird, wird es nicht wie erwartet synchronisiert. (CQ-4307122)
* Bei hochgeladenen Assets, die automatisch in DM veröffentlicht werden, zeigt der Status nicht Veröffentlicht auf AEM an. Außerdem zeigt die Statusspalte Dynamic Media-Veröffentlichung nicht den richtigen Veröffentlichungsstatus an (CQ-4306415).
* Wenn ein Asset auf [!DNL Experience Manager] veröffentlicht und bei Aktivierung auf [!DNL Dynamic Media] veröffentlicht wird, wird der Metadatenwert `scene7FileStatus` nicht erwartungsgemäß aktualisiert (CQ-4308269).
* Beim Bearbeiten des Videoprofils zeigt [!DNL Experience Manager] nicht die für die Videovorgabe festgelegten Höhen- und Bitratenwerte an. Die Felder erscheinen leer (CQ-4311828).

### [!DNL Commerce] {#commerce-6580}

* Es kann kein benutzerdefiniertes Tag für alle Produkte in Commerce erstellt werden (CQ-4310682).

* Die Aktualisierung der Produkt-Asset-Referenz führt dazu, dass Replikations-Threads sich im Wartezustand befinden, bis der ProductAssetListener-Thread seine Verpflichtungen zum JCR erfüllt (NPR-35269).

### Plattform {#platform-6580}

* Wenn Sie eine Coral Tab View-Komponente ohne Registerkarten verwenden und dann einen Foundation-Validator Trigger haben, tritt der folgende Fehler auf (NPR-35636):

   ```TXT
    Uncaught TypeError: Cannot set property 'invalid' of undefined
     at enable (foundation.js:10703)
     at foundation.js:10710
   ```

* Die Vorwärtsreplikation von SCD schlägt für Löschereignisse für Knoten fehl, die ein Komma im Namen enthalten (NPR-35191).

* Nach dem Upgrade auf AEM 6.5.7 schlagen die Builds fehl. Der Grund dafür ist, dass eine alte Version oder kein Jackson-Core in das uber-jar eingebettet ist (GRANITE-33006).

### Benutzeroberfläche {#ui-6580}

* Wenn Sie von der Karten- zur Listenansicht für Dokumente in einem Ordner in der Assets-Konsole wechseln, funktioniert die Sortierung nicht ordnungsgemäß. (NPR-35842)

* Wenn Sie Text in einer Textkomponente per Hyperlink verknüpfen, zeigt die Suchfunktion keine geeigneten Ergebnisse an (NPR-35849).

* Wenn ein Wert nicht für ein ausgeblendetes Feld bereitgestellt wird, das als erforderlich markiert ist, verhindert er das Speichern einer Komponente (NPR-35219).

### Integrationen {#integrations-6580}

* Wenn Sie verschiedene Werte für die IMS-Mandanten-ID und den Target-Client-Code verwenden, kann [!DNL Experience Manager] nicht mit [!DNL Adobe Target] integriert werden (NPR-35342).

### Übersetzungsprojekte {#translation-6580}

* Probleme beim Exportieren oder Importieren eines Übersetzungsauftrags in [!DNL Experience Manager] (NPR-35259).

### Campaign {#campaign-6580}

* Wenn Sie eine Kampagnenseite mit einer nativen Vorlage in der Touch-optimierten Benutzeroberfläche erstellen und die Registerkarte &quot;E-Mail&quot;im Dialogfeld &quot;Seiteneigenschaften&quot;öffnen, bleibt die Personalisierungsvariable für die Betreff- und Textkörperfelder deaktiviert (CQ-4312388).

### [!DNL Communities] {#communities-6580}

* Beim Hinzufügen einer Seitenstruktur zu einer Community-Gruppe wird der Titel [!UICONTROL Gruppe] im Breadcrumb in den Titel der ersten [!UICONTROL Seite] geändert (NPR-35803).
* Im Gegensatz zu Moderatoren kann ein Standard-Community-Mitglied keinen Beitragsentwurf aufrufen und bearbeiten (NPR-35339).
* Beschädigte Zugriffskontrolle und Dienstverweigerung mit `DSRPReindexServlet`, wodurch die Communities-Site heruntergefahren wird, bis die Indizierung abgeschlossen ist (NPR-35591).
* Wenn Sie [!UICONTROL Alle Benutzer] aus dem Feld [!UICONTROL Administratoren] entfernen, werden sie nicht tatsächlich aus dem Backend entfernt (NPR-35592, NPR-35611).
* Die Komponente [!UICONTROL Nachricht erstellen] gibt kein Ergebnis zurück, wenn der eingegebene Text eine Teilübereinstimmung aufweist (NPR-35666).

* Sie werden möglicherweise einige Leistungseinbußen und Langsamkeit bemerken, wenn Sie versuchen, Tags zu einem neuen Blog hinzuzufügen, indem Sie **[!UICONTROL Tags hinzufügen]** auswählen. Um die Leistung zu verbessern, installieren Sie [cqTagLucene-0.0.1.zip hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/cqTagLucene-0.0.1.zip).

### [!DNL Brand Portal] {#brandportal-6580}

* Beim Hinzufügen eines Mitglieds zu einem Ordner vom Typ [!UICONTROL Asset-Beitrag] wird in der Benutzeroberfläche die Beschriftung [!UICONTROL Benutzer oder Gruppe hinzufügen] angezeigt, obwohl nur aktive Brand Portal-Benutzer unterstützt werden und keine Gruppen (NPR-35332).

### [!DNL Forms] {#forms-6580}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Service Packs.

**Adaptive Formulare**

* Wenn Sie eine Tabelle mit einer wiederholbaren Zeile in ein wiederholbares Bedienfeld einfügen, das mehrere Instanzen in einem adaptiven Formular hat, wird die Tabelle immer zur ersten Instanz des Bedienfelds hinzugefügt (NPR-35635).

* Wenn der Tabulatorfokus die CAPTCHA-Komponente erneut erreicht, nachdem er sie einmal in einem adaptiven Formular erfolgreich überprüft hat, zeigt [!DNL Experience Manager Forms] die Fehlermeldung `Provide Captcha phrase to proceed` an (NPR-35539).

**Interaktive Kommunikation**

* Wenn Sie ein übersetztes Formular senden, werden die Übermittlungsnachrichten auf Englisch angezeigt und nicht in die entsprechende Sprache übersetzt (NPR-35808).

* Wenn Sie eine Bedingung zum Ausblenden in die angehängte XDP- oder Dokumentfragmente einfügen, kann die interaktive Kommunikation nicht geladen werden. (NPR-35745)

**Korrespondenzverwaltung**

* Wenn Sie einen Brief bearbeiten, dauert das Laden der Module mit Bedingungen länger (NPR-35325).

* Wenn Sie ein Asset aus dem linken Navigationsbereich auswählen, das nicht in einem Brief enthalten ist, und dann das nächste Asset auswählen, wird die blaue Markierung nicht aus dem zuvor ausgewählten Asset entfernt (NPR-35851).

* Wenn Sie Textfelder in einem Brief bearbeiten, zeigt [!DNL Experience Manager Forms] die Fehlermeldung `Text Edit Failed` an (CQ-4313770).

**Arbeitsablauf**

* Wenn Sie versuchen, ein adaptives Formular in einer [!DNL Experience Manager Forms] Mobile App für iOS zu öffnen, reagiert die Anwendung nicht mehr. (CQ-4314825)

* Die Registerkarte [!UICONTROL To-do] im HTML-Arbeitsbereich zeigt HTML-Zeichen an (NPR-35298).

**XMLFM**

* Wenn Sie ein XML-Dokument mit dem Output-Dienst generieren, tritt der `OutputServiceException`-Fehler für einige der XML-Dateien auf (CQ-4311341, CQ-4313893).

* Wenn Sie die Eigenschaft &quot;Hochgestellt&quot;auf das erste Zeichen des Aufzählungszeichens anwenden, wird die Aufzählungsgröße kleiner (CQ-4306476).

* Die mit dem Output-Dienst generierten PDF forms enthalten keine Rahmen (CQ-4312564).

**Designer**

* Wenn Sie eine XDP-Datei in [!DNL Experience Manager Forms] Designer öffnen, wird eine Datei &quot;designer.log&quot;im selben Ordner wie die XDP-Datei generiert (CQ-4309427, CQ-4310865).

**HTML5-Formulare**

* Wenn Sie ein Kontrollkästchen in einem adaptiven Formular im Webbrowser [!DNL Safari] für [!DNL iOS 14.1 or 14.2] aktivieren, werden keine zusätzlichen Felder angezeigt (NPR-35652).

**Forms-Verwaltung**

* Keine Bestätigungsmeldung zum erfolgreichen Massen-Upload von XDP-Dateien in das CRX-Repository (NPR-35546).

**Dokumentensicherheit**

* Mehrere Probleme wurden für die Option [!UICONTROL Richtlinie bearbeiten] auf AdminUI gemeldet (NPR-35747).

Informationen zu Sicherheitsupdates finden Sie auf der Seite [Experience Manager-Sicherheitsbulletins](https://helpx.adobe.com/security/products/experience-manager.html).

## Installieren von Version 6.5.8.0 {#install}

**Einrichtungsanforderungen und weitere Informationen**

* Für Experience Manager 6.5.8.0 ist Experience Manager 6.5 erforderlich. Detaillierte Anweisungen finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) .
* Der Service Pack-Download ist auf der Adobe [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar.
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen Experience Manager 6.5.8.0 mithilfe von Package Manager auf einer der Autoreninstanzen.

>[!NOTE]
>
>Adobe rät davon ab, das [!DNL Adobe Experience Manager] 6.5.8.0-Paket zu entfernen oder zu deinstallieren.

### Installieren Sie das Service Pack {#install-service-pack}

Gehen Sie wie folgt vor, um das Service Pack auf einer [!DNL Adobe Experience Manager] 6.5-Instanz zu installieren:

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt auch einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation einen Schnappschuss oder eine neue Sicherung Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.8.zip) herunter.

1. Öffnen Sie Package Manager und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, beenden Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Siehe [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. In der Regel geschieht dies auf [!DNL Safari], kann aber gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei Möglichkeiten, Adobe Experience Manager 6.5.8.0 automatisch auf einer funktionierenden Instanz zu installieren:

A. Platzieren Sie das Paket im Ordner `../crx-quickstart/install` , wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true` , damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Adobe Experience Manager 6.5.8.0 unterstützt keine Installation von Bootstraps.

**Bestätigen der Installation**

1. Auf der Seite mit den Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.8.0)` unter [!UICONTROL Installierte Produkte] angezeigt.

1. Alle OSGi-Bundles sind entweder **[!UICONTROL ACTIVE]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Web-Konsole verwenden: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.3 oder höher (Webkonsole verwenden: `/system/console/bundles`).

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Installieren des Adobe Experience Manager Forms Add-On-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie Experience Manager Forms nicht verwenden. Fehlerbehebungen in Experience Manager Forms werden eine Woche nach der geplanten Veröffentlichung des Service Packs über ein separates Add-On-Paket bereitgestellt.[!DNL Experience Manager]

1. Stellen Sie sicher, dass Sie das Adobe Experience Manager Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms Add-On-Paket wie unter [Installieren von AEM Forms Add-On-Paketen](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package) beschrieben.

>[!NOTE]
>
>AEM 6.5.8.0 enthält eine neue Version von [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf AEM 6.5.8.0 aktualisieren, installieren Sie die neueste Version des Pakets nach der Installation des Forms Add-On-Pakets.

### Installieren von Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in Adobe Experience Manager Forms on JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für Experience Manager Forms on JEE und zur Konfiguration nach der Bereitstellung finden Sie in den [Versionshinweisen](jee-patch-installer-65.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für Experience Manager Forms on JEE installiert haben, installieren Sie das neueste Add-On-Paket für Forms, löschen Sie das Add-On-Paket für Forms aus dem Ordner `crx-repository\install` und starten Sie den Server neu.

### UberJar {#uber-jar}

Das UberJar für Experience Manager 6.5.8.0 ist im [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.8/) verfügbar.

Informationen zur Verwendung von UberJar in einem Maven-Projekt finden Sie unter [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und Einschließen der folgenden Abhängigkeit in Ihr Projekt-POM:

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
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository anstelle des Adobe Public Maven-Repositorys (`repo.adobe.com`) verfügbar. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Es gibt also kein `classifier`-Tag mit `apis` als Wert für das `dependency`-Tag.

## Veraltete Funktionen {#removed-deprecated-features}

Nachstehend finden Sie eine Liste der Funktionen, die mit [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und in einer zukünftigen Version später entfernt. Normalerweise wird eine alternative Option bereitgestellt.

Überprüfen Sie, ob Sie eine Funktion oder Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, um eine alternative Option zu verwenden.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm **[!UICONTROL AEM Cloud Services Opt-in]** wird nicht mehr unterstützt. Da die Experience Manager- und Adobe Target-Integration in Experience Manager 6.5 aktualisiert wurde, um die Adobe Target Standard-API zu unterstützen, die die Authentifizierung über Adobe IMS und I/O verwendet, und die zunehmende Rolle von Adobe Launch bei der Instrumentierung von Experience Manager-Seiten für Analysen und Personalisierung, ist der Opt-in-Assistent funktionell irrelevant geworden. | Konfigurieren Sie Systemverbindungen, die Adobe IMS-Authentifizierung und die [!DNL Adobe I/O]-Integrationen über die entsprechenden Experience Manager-Cloud-Services. |
| Connectoren | Die Adobe JCR Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013 wird für Experience Manager 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme {#known-issues}

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5 auf 6.5.8.0 aktualisieren, können Sie `RRD4JReporter` Ausnahmen in der Datei `error.log` anzeigen. Starten Sie die Instanz neu, um das Problem zu beheben.

* Wenn Sie [!DNL Experience Manager] 6.5 Service Pack 5 oder ein vorheriges Service Pack auf [!DNL Experience Manager] 6.5 installieren, wird die Laufzeitkopie Ihres benutzerdefinierten Asset-Workflow-Modells (erstellt in `/var/workflow/models/dam`) gelöscht.
Um Ihre Laufzeitkopie abzurufen, empfiehlt Adobe, die Entwurfszeitkopie des benutzerdefinierten Workflow-Modells mit der Laufzeitkopie mithilfe der HTTP-API zu synchronisieren:
   `<designModelPath>/jcr:content.generate.json`.

* Wenden Sie sich an die Kundenunterstützung von Adobe, wenn Sie beim Bearbeiten und Erstellen kaskadierender Regeln in [!UICONTROL Ordner-Metadatenschema-Forms-Editor] und [!UICONTROL Metadatenschema-Forms-Editor] Probleme mit dem Dialogfeld [!UICONTROL Regel definieren] haben. Die bereits erstellten und gespeicherten Regeln funktionieren erwartungsgemäß.

* Wenn ein Ordner in der Hierarchie in [!DNL Experience Manager Assets] umbenannt wird und der verschachtelte Ordner, der ein Asset enthält, in [!DNL Brand Portal] veröffentlicht wird, wird der Titel des Ordners erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn ein Benutzer ein Feld zum ersten Mal in einem adaptiven Formular konfigurieren möchte, wird die Option zum Speichern einer Konfiguration nicht im Eigenschaftenbrowser angezeigt. Wenn Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren, wird das Problem behoben.

* Wenn der Assistent [!UICONTROL Konfiguration von Connected Assets] nach der Installation eine Fehlermeldung vom Typ 404 zurückgibt, müssen Sie die Pakete `cq-remotedam-client-ui-content` und `cq-remotedam-client-ui-components` mithilfe des Package Manager manuell neu installieren.

* Die folgenden Fehler und Warnmeldungen können während der Installation von Experience Manager 6.5.x.x angezeigt werden:
   * &quot;Wenn die Adobe Target-Integration in Experience Manager mithilfe der Target Standard-API (IMS-Authentifizierung) konfiguriert ist, führt der Export von Experience Fragments in Target dazu, dass falsche Angebotstypen erstellt werden. Anstelle des Typs „Experience Fragment“/der Quelle „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/der Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die serverseitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Hotspot in einem interaktiven Dynamic Media-Bild ist bei der Vorschau des Assets über den Viewer für Shop-fähige Banner nicht sichtbar.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung, die darauf wartet, dass die Reg-Änderung abgeschlossen und die Registrierung aufgehoben wird.

## OSGi-Pakete und Inhaltspakete enthalten {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten werden die OSGi-Pakete und Inhaltspakete aufgelistet, die in [!DNL Experience Manager] 6.5.8.0 enthalten sind:

* [Liste der in Experience Manager 6.5.8.0 enthaltenen OSGi-Bundles](assets/6580_bundles.txt)

* [Liste der in Experience Manager 6.5.8.0 enthaltenen Inhaltspakete](assets/6580_packages.txt)

## Eingeschränkte Websites {#restricted-sites}

Diese Websites stehen nur Kunden zur Verfügung. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* Weitere Informationen finden Sie unter [Kontaktaufnahme mit der Adobe-Kundenunterstützung](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 - Versionshinweise](/help/release-notes/release-notes.md)
* [[!DNL Experience Manager] Produktseite](https://www.adobe.com/de/marketing/experience-manager.html)
* [[!DNL Experience Manager] 6.5 Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

