---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
source-git-commit: 41ef1b05e4082bb50b93ff6511542ed56a77497c
workflow-type: tm+mt
source-wordcount: '3433'
ht-degree: 49%

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
| Version | 6.5.19.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 23. November 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.19.0 enthalten ist {#what-is-included-in-aem-6519}

[!DNL Experience Manager] 6.5.19.0 enthält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

**Wichtigste Funktionen**

* A

**Wichtige Verbesserungen**

* S

**Veraltete Funktion**

* ActiveMQ in AEM wird nicht mehr unterstützt. ActiveMQ wurde für die Kommunikation zwischen zwei AEM-Publishing-Instanzen verwendet. Adobe empfiehlt, dass Kundinnen und Kunden jetzt einen Lastenausgleich verwenden.

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 19 {#fixed-issues}

### [!DNL Sites]{#sites-6519}

* U

#### Barrierefreiheit{#sites-accessibility-6519}

* Wenn Sie auf einer AEM Sites-Seite 200 % auf der Seite vergrößern, werden die Links **[!UICONTROL Sprachkopie]** und **[!UICONTROL CSV-Bericht]** in der Leiste &quot;Verweise&quot;nicht angezeigt. (SITES-11011) NORMAL

#### Admin-Benutzeroberfläche{#sites-adminui-6519}

* AEM Screens-Kanal **[!UICONTROL Vorschau]** -Funktion nicht funktioniert oder im Dashboard angezeigt wird. (SITES-15730) CRITICAL
* Wenn während eines Seitenverschiebungsvorgangs die Benutzeroberfläche die Verweise nicht anzeigen kann, aber feststellt, dass sie automatisch erneut veröffentlicht werden, werden sie *not* erneut veröffentlicht. (SITES-16435) MAJOR
* Wenn Sie in AEM 6.5 mit Service Pack 16 oder 17 in der Listenansicht von Sites mit aktivierter Spalte &quot;Workflow&quot;die Liste nicht nach den Elementen in dieser Spalte sortieren können. Es erfolgt keine Sortierung. (SITES-15385) MAJOR
* Für eine Umleitungsseitenvorlage wurde das Umleitungsfeld als obligatorisch festgelegt. In diesen beiden Szenarien wird die Validierung für das erforderliche Feld jedoch nicht angewendet und funktioniert nicht: Wenn eine Seite ohne obligatorischen Umleitungswert erstellt wird, kann keine Umleitungsseite erstellt werden. Die Validierung funktioniert nicht bei der Navigation mit Tastaturbefehlen und wenn das Feld als ungültig markiert ist, wird der Vorgang nicht fortgesetzt. (SITES-15903) NORMAL
* Einige **Eingehende Links** wurden nicht in die angezeigte Anzahl im **Verweise** Bedienfeld. Beispielsweise zeigte das Bedienfeld **Eingehende Links (6)** aber es gab tatsächlich neun eingehende Links. (SITES-14816) NORMAL

#### Klassische Benutzeroberfläche{#sites-classicui-6519}

* Nach der Installation von Hotfix in SITES-15827 wurden Dialogfeldtitel mit Leerzeichen zwischen Wörtern durch ersetzt `" "`. Auch Zeilenumbrüche wurden entfernt. (SITES-16089) MAJOR
* Kodierte Dialogfeldtitel führen jetzt zu einer doppelten Kodierung des Titels. (SITES-15841) NORMAL
* Die Aktualisierung von AEM-Servern von Service Pack 6.5.16 auf 6.5.17 führte zu einer doppelten Kodierung von Dialogfeldtiteln der klassischen Benutzeroberfläche. (SITES-15634) NORMAL

#### [!DNL Content Fragments]{#sites-contentfragments-6519}

* Im Inhaltsfragment-Editor wird eine Meldung über einen internen Server-Fehler angezeigt. (SITES-13550) CRITICAL
* Die Aktualisierung der `org.json` -Bibliothek über NPR-41291 verursachte Datenfehlerkonversionen in der `DefaultDataTypeConverter` des `cfm-impl` Bundle Die Datentypkonvertierung muss flexibler sein. (SITES-16473) NORMAL
* Rufen Sie die Fehlermeldung auf: &quot;Diese Inhaltsfragmentversion kann aufgrund inkompatibler Inhalte nicht mit der aktuellen Version verglichen werden.&quot; Inhaltsfragmente sollten vergleichbar sein, aber nicht. (SITES-16317) NORMAL
* Die JS-URL des Asset-Wählers wurde geändert von
  `https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js`
in
  `https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js` (SITES-16068) NORMAL
* Anpassen des neuen Polaris Metadaten-API-Antwortschemas für die CFM-Polaris-Integration. (SITES-15166) NORMAL
* Alle Inhaltsfragmente sollten dort aufgeführt werden, wo auf das ausgewählte Inhaltsfragment verwiesen wird. Stattdessen zeigen Asset-Verweise im Inhaltsfragment-Referenzbereich Verweise auf 0 (Null). (SITES-15036) NORMAL

#### Core-Backend{#sites-core-backend-6519}

* Verbessern `StyleImpl`. (SITES-15164) NORMAL

<!--#### Core Components{#sites-core-components-6519}

* A -->

#### Campaign-Integration{#sites-campaign-integration-6519}

* Auf der Signaturkomponente (`/apps/fpl/components/campaign/signature`), funktionierte der Link Externalizer nicht. Die Domäne wurde nicht an die Bildquelle angehängt, wenn der HTML-Kommentar über dem Bild-Tag entfernt wurde. Dieses Problem wurde nur mit der Signaturkomponente in der Produktionsumgebung und nicht mit der Staging-Umgebung gefunden. (SITES-16120) NORMAL

<!--#### Experience Fragments{#sites-experiencefragments-6519}

* A -->

#### Foundation-Komponenten (alt){#sites-foundation-components-legacy-6519}

* Adobe Experience Manager (AEM) Sites-Suchkomponente bricht die Benutzeroberfläche ab. (SITES-15087) NORMAL

#### GraphQL-Abfrage-Editor{#sites-graphql-query-editor-6519}

* In der Benutzeroberfläche des GraphQL-Editors können Sie nicht alle gespeicherten Abfragen durchblättern, wenn eine große Anzahl von Abfragen vorliegt (z. B. mehr als 25). (SITES-16008) MAJOR
* Der GraphQL-Editor speichert den Veröffentlichungsstatus persistenter Abfragen nicht. Die Schaltfläche Veröffentlichung rückgängig machen wird im GraphQL-Editor angezeigt, aber das Symbol, das anzeigt, dass die beibehaltene Abfrage veröffentlicht wurde, wird nicht angezeigt. Das Aktualisieren der Seite zeigt, dass die persistente Abfrage noch nicht einmal veröffentlicht wurde. (SITES-15858) MAJOR

#### Launches{#sites-launches-6519}

* Änderungen im Repository werden aufgrund von `Oak0001` Konflikte, wenn mehrere Seiten bearbeitet oder Inhalt erstellt wird. Es ist normal, einen erneuten Versuch in einem solchen Ereignis durchzuführen, aber dies geschieht nicht. (SITES-14840) MAJOR

#### MSM - Live Copies{#sites-msm-live-copies-6519}

* Die MSM-Rollout-Schaltfläche funktioniert in der grafischen Touch-Benutzeroberfläche nicht. (SITES-16991) MAJOR
* Die Link-Referenz wird im Experience Fragment nicht aktualisiert, wenn eine Live Copy erstellt oder ein Experience Fragment eingeführt wird. (SITES-15460) NORMAL

#### Seiteneditor{#sites-pageeditor-6519}

* Die Auswahl mehrerer Dokumentdateitypen für den Asset-Typ-Filter funktioniert nicht in der Seitenkonsole. Es werden keine Ergebnisse gefunden, selbst wenn die Ergebnisse eines bestimmten Dateityps verfügbar sind. Daher können Autoren nicht mehrere Dokumente filtern. Sie müssen mehrere Dokumenttypen verwenden und sie müssen sie einzeln filtern. (SITES-14047) MAJOR
* Wenn Sie nach dem Upgrade einer Instanz von AEM 6.5.17 und AEM 6.5.18 im Seiteneditor auswählen, **[!UICONTROL Seite veröffentlichen]**, werden Sie zu einer URL umgeleitet, die nicht vorhanden ist. Der Benutzer sollte zum Veröffentlichungsassistenten umgeleitet werden. (SITES-15856) NORMAL
* (SITES-15704) NORMAL
* Redundante Kopie aus AEM Zwischenablage beim Einfügen aus der Zwischenablage des Betriebssystems. (SITES-15704) NORMAL
* In Assets wählen Sie **[!UICONTROL Dokumente]**, dann unter **[!UICONTROL Filtertyp]** auswählen **[!UICONTROL Microsoft® Word]** oder **[!UICONTROL Microsoft® Excel]** zeigt keine Ergebnisse an, obwohl Dateien beider Typen vorhanden sind. (SITES-14837) NORMAL

### [!DNL Assets]{#assets-6519}

* Die Veröffentlichung von Assets in Experience Manager oder Brand Portal kann nicht differenziert werden. [NPR-41320]
* Wenn Sie einen öffentlichen Ordner erstellen oder speichern, werden drei Gruppen in einem Admin-Dashboard erstellt. [ASSETS-26700]
* Wenn Sie im Suchbereich Kontrollkästchen aktivieren und die Auswahl eines dieser Kontrollkästchen aufheben, werden alle Kontrollkästchen deaktiviert. [ASSETS-26377]

#### [!DNL Dynamic Media]{#assets-dm-6519}

* Nachdem ein Asset in AEM hochgeladen wurde, wird die `update_asset` Workflow ausgelöst. Der Workflow wird nie abgeschlossen. Wenn Sie sich die Workflow-Instanzen ansehen, wird der Workflow bis zum Schritt zum Hochladen des Produkts abgeschlossen. Der nächste Schritt ist der Batch-Upload in Scene7. Der Benutzer kann sehen, dass sich das Asset in Scene7 in der Dynamic Media Classic-App befindet. (ASSETS-30443) CRITICAL
* Ein benutzerdefiniertes Servlet (API-Endpunkt) gibt einen falschen Dynamic Media (Scene7)-Dateinamen zurück. Dies tritt auf, wenn ein Asset gelöscht und durch ein Asset mit demselben Namen ersetzt wird. Das benutzerdefinierte Servlet gibt den alten Dynamic Media-Dateinamen (Scene7) zurück, während ein &quot;jcr&quot;-API-Aufruf den richtigen Dateinamen zurückgibt. (ASSETS-29476) HAUPTASPEKTE
* Selbst wenn die Synchronisierung auf Ordnerebene deaktiviert ist, zeigen die Protokolle den Trigger &quot;Scene7 ReplicateOnModifyListener&quot;. Die `ReplicateOnModifyListener/Worker` sollte die Verarbeitung von Nicht-Dynamic Media-Ordner-Assets und -Inhaltsfragmenten überspringen. (ASSETS-26705) HAUPTASPEKTE
* Personen mit Sehschwäche sind betroffen, wenn der Fokus in Dropdown-Elementen (Nur Inhalt, Ansicht, Weitere Optionen) im schwarzen und weißen Modus mit hohem Kontrast nicht sichtbar ist. (ASSETS-25759) NORMAL
* Personen mit Sehschwäche sind betroffen, wenn das Luminanzkontrastverhältnis für Text auf einer Seite unter 4,5:1 liegt. (ASSETS-25756) NORMAL
* Sprachausgabeprogramme kommentieren die angezeigte Popup-Nachricht nach dem Senden der Daten nicht. (ASSETS-25755) NORMAL
* Bildschirmlesehilfen erkennen bei der Navigation mit der Tastenkombination &quot;Landmarken/Region&quot;keine Landmarken auf der Seite (Dynamic Media; Erstellen eines Videokodierungsprofils). `D/R`. (ASSETS-25752) NORMAL
* Bildschirmlesehilfen erkennen bei der Navigation mit der Tastenkombination &quot;Landmarken/Region&quot;nicht mehrere Wahrzeichen auf der Seite (Dynamic Media; Erstellen eines interaktiven Videos). `D/R`. (ASSETS-25750) NORMAL
* Sprachausgaben (NVDA/JAWS/Erzähler) erkennen die Landmarks nicht in **Asset bearbeiten** Seite beim Navigieren mit den Tastaturbefehlen `D/R`. (ASSETS-25744) NORMAL
* Der Benutzer erhält eine leere/falsche asynchrone Auftragsmeldung, aber das verbundene Asset wurde erfolgreich veröffentlicht. (ASSETS-29342) TESTVERZEICHNIS

### [!DNL Forms]{#forms-6519}

Fehlerbehebungen in [!DNL Experience Manager] Forms wird eine Woche nach der geplanten Bereitstellung über ein separates Add-On-Paket bereitgestellt [!DNL Experience Manager] Veröffentlichungsdatum des Service Packs. In diesem Fall ist die AEM Add-On-Paket-Version 6.5.19.0 von Forms für Donnerstag, den 30. November 2023 geplant. Nach der Veröffentlichung wird diesem Abschnitt eine Liste mit Forms-Fehlerbehebungen und -Verbesserungen hinzugefügt.

* Hinzufügen der Zugriffssteuerungsliste für `fd-cloudservice` Benutzer, um die Microsoft®-Konfigurationen unter lesen oder aktualisieren zu können `cloudconfigs/microsoftoffice`. (FORMS-11142) NORMAL

<!--LEFT BULLET LIST HERE IN CASE OF REUSE BY FORMS IN THE FUTURE 
* **Document Services**
  * text
* **Adaptive Forms** 
  * text
* **Accessibility**
  * text
* **Interactive Communications**
  * text -->

<!--### Commerce{#commerce-6519}

* A -->

### Fundament{#foundation-6519}

* Beim Erstellen einer Sprachkopie auf der Sprachstammenebene werden die Pfade auf der Seite nicht angepasst. Wenn die Sprachkopie erstellt wurde, nicht für den Sprachstamm, sondern für die darunter liegenden Seiten, hat sich der Pfad korrekt geändert. (NPR-41364) MAJOR
* Die QuickInfo &quot;Darstellung des relativen Datums&quot;kann nur durch Drücken der Esc-Taste (ESC) auf der Tastatur geschlossen werden. Die QuickInfo sollte geschlossen werden, wenn der Benutzer einen beliebigen Teil der Benutzeroberfläche auswählt. (NPR-41394) NORMAL
* Nicht lokalisierte Zeichenfolge `Something went wrong while adding the private key.` beim Hinzufügen der falschen privaten Schlüsseldatei in **Benutzer bearbeiten** > **Keystore**. (NPR-41366) NORMAL
* Für Microsoft® SharePoint und Microsoft® One Drive in der AEM 6.5 sind Symbole erforderlich. (NPR-41354) NORMAL
* Nicht lokalisierte &quot;UserId/Password mismatch.&quot; Zeichenfolge in **Sicherheit** > **Benutzer** > **Erstellen** Dialogfeld. (NPR-41245) NORMAL
* Popover-Code und Ereignis-Handler werden zweimal geladen, wodurch benutzerdefinierte Coral3-basierte Benutzeroberflächen beschädigt werden. (NPR-41171) NORMAL
* Die Abwahl funktioniert nicht ordnungsgemäß, nachdem &quot;Alle auswählen&quot;in der AEM Sites-Konsole verwendet wurde. (NPR-41304) MINOR

<!--#### Content distribution{#foundation-content-distribution-6519}

* T -->

#### Integrationen{#integrations-6519}

* SMS-Links in einer AEM E-Mail-Kampagne sind nicht korrekt geschrieben; sie enthalten ein HTML-Ankerelement. (NPR-41211) MAJOR
* Die im Bildschirm zur Kontokonfiguration verwendete Aufzeichnung darf keinen neuen Berechtigungstyp verwenden. (NPR-41210) NORMAL
* Verschieben der Analytics-Berichtsimport-Planung von `ManagedPollConfig` für Sling-Aufträge. Wenn zwei verschiedene Analytics-Frameworks mit verschiedenen Report Suites an zwei verschiedene Sites angehängt wurden, `ManagedPollConfig` fragt nur einen von ihnen ab. (NPR-41209) NORMAL
* Wenn der Wert auf den Standardwert zurückgesetzt wird, bleibt die zuvor ausgewählte Zeitrahmen-Schaltfläche aktiviert. Im Insight-Dashboard von AEM wird der Zeitrahmen standardmäßig auf die Woche gesetzt und zeigt Inhaltseinblicke als wöchentliche Daten an. Wenn der Benutzer jetzt andere Zeitrahmenoptionen auswählt, z. B. Stunde, Tag, Monat und Jahr, ändern sich die Daten entsprechend dem ausgewählten Wert. Wenn die Werte jedoch zurückgesetzt werden, ist standardmäßig der sichtbare Zeitrahmen &quot;Woche&quot;, aber trotzdem die zuvor ausgewählte Zeitrahmenoption ausgewählt. (NPR-41246) MINOR

#### Oak{#oak-6519}

* Backport-Dienstprogramm, um Limit-Schreibvorgänge an AEM zu bewerten, falls die asynchrone Indizierung verzögert wird. (NPR-40985) MAJOR

#### Platform{#foundation-platform-6519}

* QueryBuilder-Abfragen mit eckigen Klammern werden fälschlicherweise in xpath übersetzt. (NPR-41298) NORMAL

<!--#### Replication{#foundation-replication-6519}

* R -->

<!--#### Sling{#foundation-sling-6519}

* W -->

#### Übersetzungsprojekte{#foundation-translation-6519}

* Beim Erstellen der Sprachkopie der Seite &quot;A&quot;sollten die Sprachkopien der referenzierten Seiten, Experience Fragments, Inhaltsfragmente und Assets automatisch erstellt werden. Außerdem sollten die Verweise auf die neu erstellte Sprachkopie der Seite &quot;A&quot;im neuen Pfad auf die entsprechenden neu erstellten Sprachkopien der Seiten, Experience Fragments, Inhaltsfragmente und Assets aktualisiert werden. (NPR-41076) NORMAL

<!--#### User interface{#foundation-ui-6519}

* A -->

<!--#### WCM{#wcm-6519}

* A -->

#### Workflow{#foundation-workflow-6519}

* Aufgabe im Posteingang kann nicht abgeschlossen werden. Beim Versuch, die Aufgabe abzuschließen und eine Aktion auszuwählen, wird im Dropdown-Menü nur ein &quot;nicht definierter&quot;Wert beobachtet. Das bedeutet, dass Benutzer das Service Pack AEM 6.5.18 nicht anwenden können. (NPR-41402) MAJOR
* Aufgaben im Posteingang können nicht abgeschlossen werden. Es gibt keinen Wert (nur &quot;nicht definiert&quot;) in der Dropdownliste, wenn versucht wird, die Aufgabe für ZIP-Dateien, Asset-Berichte, Verschieben (Erfolg oder Fehler) oder Asset-Ablauf abzuschließen. (NPR-41305) MAJOR
* Wenn ein Benutzer **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > Instanzen und wählt dann den laufenden Workflow aus. Wählen Sie dann **[!UICONTROL Payload anzeigen]**, wird eine Fehlerseite für 500 angezeigt. (NPR-41325) NORMAL


## Installieren von [!DNL Experience Manager] 6.5.18.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.19.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die Adobe-[Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.19.0 mit dem Package Manager auf einer der Authoring-Instanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.19.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs auf [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.18.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.19.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.19.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.19.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.16 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- NPR-41010 for 6.5.18.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Installation des Service Packs für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>Die AEM Forms-Funktion, z. B. Adaptive Forms, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.corp.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de), sind nur zu Forschungs- und Evaluierungszwecken bestimmt. Für die Verwendung in der Produktion ist es unerlässlich, eine gültige Lizenz für AEM Forms zu erwerben.



### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen.

Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.19.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.18/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.19</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.

## Veraltete und entfernte Funktionen{#removed-deprecated-features}

Weitere Informationen finden Sie unter [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md/).

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* **Die Seitenveröffentlichung funktioniert im Seiteneditor nicht mehr nach dem Upgrade auf Service Pack 18 (6.5.19.0)**

  <!-- https://jira.corp.adobe.com/browse/SITES-15856 REMOVE FOR 6.5.19.0--> Nach dem Upgrade einer Instanz von AEM 6.5.0.0 bis 6.5.17.0 auf AEM 6.5.19.0, werden Sie, wenn Sie innerhalb des Seiteneditors auf **Seite veröffentlichen** klicken, zu einer URL umgeleitet, die nicht existiert.

  Um dieses Problem zu umgehen, führen Sie eine der folgenden Aktionen aus:

   * Entfernen Sie die folgende „Pfad“-Eigenschaft.

     `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/publish/granite:data`

   * Fügen Sie die richtige URL direkt in den Browser ein.

     `http://localhost:4504/editor.html/libs/wcm/core/content/sites/publishpagewizard.html?item=/content/we-retail/language-masters/en/about-us.html`



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

  Beheben des Problems, `damAssetLucene` muss so konfiguriert werden, dass die folgenden beiden Eigenschaften unter `/indexRules/dam:Asset/properties`:

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

* JDK-Versionen, die höher als 1.8.0_281 sind, werden für WebLogic JEE-Server nicht unterstützt. (FORMS-8498, CQDOC-20383)
* Da [!DNL Microsoft® Windows Server 2019] weder [!DNL MySQL 5.7] noch [!DNL JBoss® EAP 7.1] unterstützt, unterstützt [!DNL Microsoft® Windows Server 2019] keine schlüsselfertigen Installationen für [!DNL Experience Manager Forms 6.5.10.0]. (CQDOC-18312)
* JDK 11.0.20 wird zur Installation des AEM Forms auf JEE-Installationsprogramms nicht unterstützt. Nur JDK 11.0.19 oder frühere Versionen werden zur Installation des AEM Forms auf JEE-Installationsprogramms unterstützt. (FORMS-10659)

#### Installation

* Auf der Plattform JBoss® 7.1.4 schlägt die Bereitstellung fehl, wenn Experience Manager 6.5.16.0 oder ein höheres Service Pack installiert wird. `adobe-livecycle-jboss.ear` (CQ-4351522, CQDOC-20159)
* Nach dem Upgrade auf AEM Forms 6.5.18.0 JBoss® Turnkey-Vollinstallationsumgebung unter Windows Server 2022 kann beim Kompilieren des Code der Ausgabe-Client-Anwendung mit Java™ 11 der folgende Kompilierungsfehler auftreten:

  ```
  error: error reading [AEM_Forms_Installation_dir]\sdk\client-libs\common\adobe-output-client.jar; java.net.URISyntaxException: 
  Illegal character in path at index 70: file:/[AEM_Forms_Installation_dir]/sdk/client-libs/common/${clover.jar.name} 1 error
  ```

  Um das Problem zu beheben, führen Sie die folgenden Schritte aus:
   1. Navigieren Sie zu `[AEM_Forms_Installation_dir]\sdk\client-libs\common\` und entpacken Sie `adobe-output-client.jar`, um die Datei `Manifest.mf` zu extrahieren.
   1. Aktualisieren Sie die Datei `Manifest.mf`, indem Sie den Eintrag `${clover.jar.name}` aus dem Attribut „class-path“ entfernen.

      >[!NOTE]
      >
      > Sie können auch ein Tool für die Bearbeitung im Kontext verwenden, z. B. 7-zip, um die Datei `Manifest.mf` zu aktualisieren.

   1. Speichern Sie die aktualisierte `Manifest.mf` im Archiv `adobe-output-client.jar`.
   1. Speichern Sie die geänderte `adobe-output-client.jar` und führen Sie das Setup erneut aus. (CQDOC-20878)
* Nach der Installation des Vollinstallationsprogramms für AEM Service Pack 6.5.19.0 schlägt die EAR-Bereitstellung auf JEE mit der JBoss®-Turnkey-Methode fehl.
Um das Problem zu beheben, suchen Sie die Datei `<AEM_Forms_Installation_dir>\jboss\bin\standalone.bat` und aktualisieren Sie alle Vorkommen von `Adobe_Adobe_JAVA_HOME` auf `Adobe_JAVA_HOME`, bevor Sie den Konfigurations-Manager ausführen. (CQDOC-20803)

#### Adaptive Formulare

* Wenn ein adaptives Formular veröffentlicht wird, werden alle Abhängigkeiten, einschließlich Richtlinien, erneut veröffentlicht, selbst wenn keine Änderungen an ihnen vorgenommen wurden. (FORMS-10454)
* Wenn Benutzende ein Feld erstmals in einem adaptiven Formular konfigurieren möchten, wird im Eigenschaften-Browser die Option zum Speichern einer Konfiguration nicht angezeigt. Das Problem lässt sich beheben, indem Sie im selben Editor ein anderes Feld des adaptiven Formulars konfigurieren.
* Wenn eine Umleitungs-URL im Guide-Container eines adaptiven Formulars festgelegt ist, funktioniert die Inline-Signatur nicht mehr. (FORMS-10493)
* Die Veröffentlichung aller Datensatzdokumentvorlagen (DoR) schlägt fehl. Es werden nur englischsprachige, gebietsschemabasierte DoR-Vorlagen und die zugehörigen Forms-basierten DoR-Vorlagen veröffentlicht. (FORMS-10535)

#### Interaktive Kommunikationen

* Nach der Aktualisierung auf AEM Service Pack 18 ist es nicht möglich, die interaktive Kommunikation mit großen Inline-Bildern im Bearbeitungsmodus zu öffnen. (FORMS-10578)
Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

   1. Laden Sie [Hotfix-FORMS-10578](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) vom SD-Link herunter.
   1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
   1. Laden Sie das Paket (.zip) über den Package Manager hoch und installieren Sie es.
   1. Öffnen Sie die Bundles des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Bundle (.jar).

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5.19.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.19.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65180_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.19.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65180_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
