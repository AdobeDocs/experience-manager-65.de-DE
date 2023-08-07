---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
exl-id: fed4e110-9415-4740-aba1-75da522039a9
source-git-commit: ea0f4096ac76ed11ee84a3769725f527c13fb461
workflow-type: tm+mt
source-wordcount: '3786'
ht-degree: 99%

---

# Versionshinweise zum aktuellen Service Pack für [!DNL Adobe Experience Manager] Version 6.5 {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/Documents/issue_tracker_sp_cfp_updates.xlsx?d=w3ea81ae4e6054153b132f2698c86f84e&csf=1&web=1&e=7yhrWb&nav=MTVfe0U0RjdDQUM3LTZCQ0EtNDk1Qy04Mjc1LTM2MUJEMzE1OEVGN30 -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, June 1, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.17.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Donnerstag, 25. Mai 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.17.0 enthalten ist {#what-is-included-in-aem-6517}

[!DNL Experience Manager] 6.5.17.0 enthält neue Funktionen, wichtige von Kundinnen und Kunden angeregte Verbesserungen, Fehlerkorrekturen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* **Verbesserungen des Sucherlebnisses** – Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:
   * Workflow erstellen
   * Version erstellen
   * Zuordnung für Assets herstellen oder aufheben

  Sie müssen nicht erst zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.
* **Dynamic Media _Snapshot_**– Experimentieren Sie mit Testbildern oder Dynamic Media-URLs, um die Ausgabe verschiedener Bildmodifikatoren zu sehen, und optimieren Sie die intelligente Bildbearbeitung für Dateigröße (mit WebP- und AVIF-Bereitstellung), Netzwerkbandbreite und Pixel-Seitenverhältnis der Geräte. Siehe [Dynamic Media Snapshot](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=de).
* **DASH Streaming mit Dynamic Media** – Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF). Ist jetzt für alle Regionen verfügbar und [kann über ein Support-Ticket aktiviert werden](/help/assets/video.md#enable-dash-on-your-account-enable-dash).
* **Integration von Experience Manager Sites und Inhaltsfragmenten in Assets der nächsten Generation für Dynamic Media** – Benutzerinnen und Benutzer von Experience Manager Assets as a Cloud Service für Dynamic Media der nächsten Generation können diese in der Cloud gehosteten Assets jetzt für die Bearbeitung und Bereitstellung mit On-Premise- oder Managed Services-Instanzen von Experience Manager Sites 6.5 verwenden.

## Verbesserungen im Service Pack 17 {#enhancements-sp17}

### Formulare{#aem-forms-6517}

* **[Adaptive Formulare im AEM-Seiteneditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)**: Sie können jetzt den AEM-Seiteneditor verwenden, um schnell mehrere Formulare zu Ihren Site-Seiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, eine nahtlose Datenerfassung innerhalb von Sites-Seiten zu erstellen, indem sie die Leistungsfähigkeit adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:
   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Komponente „Container für adaptive Formulare“ im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Formulare im AEM Sites-Editor, damit Sie unabhängig von einer beliebigen Sites-Seite Formulare erstellen können und diese Formulare auch auf mehreren Seiten wiederverwenden können.
   * Optimieren Sie das Anwendererlebnis und bieten Sie mehr Flexibilität, indem Sie mehrere Formulare zu einer Sites-Seite hinzufügen.
* **[Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)**: Es wurde Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms hinzugefügt, um zusätzlich zur bestehenden Google reCAPTCHA v2-Unterstützung weiteren Schutz vor betrügerischen Aktivitäten und Spam zu bieten.
* **[Unterstützung für Adobe Acrobat Sign für Regierungsbehörden mit Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)**: AEM Forms kann jetzt mit Adobe Acrobat Sign für Regierungsbehörden (FedRAMP-konform) integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden). Durch die Integration mit Adobe Acrobat Sign für Behörden können Partnerinnen oder Partner und Regierungskundschaft von Adobe elektronische Signaturen in adaptiven Formularen für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig mit der Einhaltung der FedRAMP Moderate Compliance konform sind, sodass die Regierungskundschaft von Adobe beruhigt sein kann.
* **Aktivieren der Salesforce-Integration mit Experience Manager Forms für den Datenaustausch**: Konfigurieren Sie die Integration zwischen Experience Manager Forms und der Salesforce-Applikation unter Verwendung des OAuth 2.0-Client-Anmeldedatenflusses. Diese Funktion ermöglicht eine sichere und direkte Authentifizierung und Autorisierung der Anwendung und ermöglicht eine nahtlose Kommunikation ohne Einbindung der Benutzenden.
* **Optimierung und verbesserte Funktionalität der Workflow-Engine**: Erhöhen Sie die Leistung der Workflow-Engines, indem Sie die Anzahl der Workflow-Instanzen minimieren. Zusätzlich zu den Statuswerten `COMPLETED` und `RUNNING` unterstützt der Workflow auch drei neue Statuswerte: `ABORTED`, `SUSPENDED`, und `FAILED`.


<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 17 {#fixed-issues}

### [!DNL Sites]{#sites-6517}

* Leistungsabfall in LinkCheckerTransformer. (SITES-11661)
* Sprachkopien einer Seite wurden nicht erwartungsgemäß aktualisiert. (SITES-11191)
* Das Öffnen von Nicht-Kampagnenseiten ruft unnötigerweise `targeteditor.html` auf. Entfernen Sie den Aufruf `targeteditor`, wenn er nicht benötigt wird. (SITES-12469)
* Live Copies können nicht für Seiten mit Anmerkungen erstellt werden. (SITES-12154)
* Das Rollout von Seiten funktioniert in Experience Manager 6.5.16 nicht. (SITES-12008)
* Nicht genügend Arbeitsspeicher; hohe Speicherbereinigungs-Aktivität aufgrund von `NotificationManagerImpl`. `NotificationManager` Bundle-Upgrade auf Experience Manager 6.5. (SITES-11440)
* Es wurden WCM-IT-Tests behoben, die Service Pack 17 blockierten. (SITES-13089)
* Das Abrufen von Sites-Verweisen schlägt beim Servlet fehl. (SITES-10901)

#### Admin-Benutzeroberfläche{#sites-adminui-6517}

* Das Vorschaufenster für die Bildauswahl der Miniaturansichten kann nicht geschlossen werden. (SITES-10459)

#### [!DNL Content Fragments]{#sites-contentfragments-6517}

* Konfiguration zum Herstellen einer Verbindung zum Polaris-Dienstobjekt (URL, Anmeldeinformationen, Callback usw.). (SITES-12149)
* Die Verwendung von `SemanticDataType.REFERENCE` sollte „Remote-Asset-IDs“ unterstützen. (SITES-12127)
* Integriert Polaris Asset Selector in den Inhaltsfragment-Editor. (SITES-12125)
* Für den Zugriff auf den Endpunkt des Metadatendienstes war ein obligatorischer HTTP-Header erforderlich. (SITES-13068)
* Die GraphQL-Implementierung von 6.5 entsprach nicht dem Cloud Service (primär); identifizierte Probleme wurden behoben. (SITES-13096)
* GraphQL-Paging/Sortierung und Hybridfilterung sollten in Experience Manager 6.5/AMS verfügbar sein. (SITES-9154)

#### Kernkomponenten{#sites-core-components-6517}

* Die Eigenschaft `cq-msm-lockable` hat den falschen Umleitungswert in der Foundation-Seitenkomponente. (SITES-10904)
* Die Remote-Asset-Auswahl leitet immer zur IMS-Staging-Umgebung weiter. (SITES-13433)

#### [!DNL Experience Fragments]{#sites-experiencefragments-6517}

* Wenn beim Export in Adobe Target eine Externalizer-Konfiguration in einem Experience Fragment ausgewählt wird, wird die falsche externalisierte URL gesendet. (SITES-12402)
* Nicht inklusive Begriffe entfernen; Richtlinien für inklusive Begriffe anwenden. (SITES-11244)

#### Seiteneditor{#sites-pageeditor-6517}

* Für ein Karussell-Set wird in der Seitenleiste der Experience Manager-Inhaltssuche keine Miniaturansicht angezeigt. (SITES-8593)

### [!DNL Assets]{#assets-6517}

* Wenn Sie mehr als 40 PDFs gleichzeitig veröffentlichen, reagiert [!DNL Experience Manager] nicht mehr und ist für einige Zeit nicht mehr verfügbar. (ASSETS-21789)
* Wenn Sie als Testbenutzende angemeldet sind, können Sie die Assets, die mit einem bestimmten Asset verknüpft sind, nicht sehen, wenn Sie auf die Eigenschaften eines Assets klicken. (ASSETS-21648)
* Wenn Sie bei der Bearbeitung von Assets mit `Desktop Actions` versuchen, mehr als fünf Assets auf einmal einzuchecken, wird der Fehler `Limit Reached` angezeigt und die ausgewählten Assets werden ausgecheckt. (ASSETS-21121)
* Assets können in einer Sammlung nicht nach Namen sortiert werden. (ASSETS-20924)
* Bei Assets eines Bildformattyps können die Dimensionen nicht festgelegt werden. (ASSETS-20835)
* Der QuickInfo-Text und der zugehörige Hintergrund im Feld „E-Mail-Adresse suchen/hinzufügen“ zeigen beim Teilen eines Links kein angemessenes Kontrastverhältnis an. (ASSETS-17347)
* Beim Erweitern von `Notifications` wird der Text aufgrund des Absatzabstands nicht richtig angezeigt. (ASSETS-17345)
* Wenn Sie ein Asset in eine Sammlung kopieren, wird das Kontrollkästchen `Public Collection` nicht richtig angezeigt. (ASSETS-17343)
* Elemente verwenden ARIA-Attribute ohne Rolle. (ASSETS-17325, ASSETS-17323)
* Der Link ist nicht beschreibend, wenn Sie `Notifications` erweitern. (ASSETS-17283)
* Wenn Sie navigieren und die Schaltfläche [!DNL Smart Crop] erweitern, wird der Inhalt wie eine Liste angezeigt, aber nicht als ungeordnete Liste gekennzeichnet. Daher erkennt die Bildschirmlesehilfe die ungeordnete Liste nicht und liest sie als normalen Text. (ASSETS-17247)
* Die Beschriftung `Sort By` ist nicht mit der entsprechenden Dropdown-Liste verknüpft. Daher erkennt die Bildschirmlesehilfe die Dropdown-Optionen nicht. (ASSETS-17239)
* Es ist nicht möglich, sich mit den Tabulator- oder Pfeiltasten der Tastatur vorwärts oder rückwärts zu bewegen, wenn Sie versuchen, Benutzende über das Kombinationsfeld `Add user` hinzuzufügen. (ASSETS-17233)
* Die Informationen für den Workflows-Schritt werden von der Bildschirmlesehilfe nicht korrekt dargestellt (ASSETS-17285).
* Wenn Sie zum Kombinationsfeld `Saved Searches` navigieren, haben sowohl Name als auch Rolle keine zugewiesenen Bezeichnungen. (ASSETS-17329)
* Wenn Sie zu `Collection` navigieren und sich der Mauszeiger über dem Text *Mitglieder* befindet, erscheint der Text nicht als markiert. Daher erkennt die Bildschirmlesehilfe den Überschriftentext nicht und liest ihn als normalen Text. (ASSETS-17245)
* Der Zugriff auf die Option `View Settings` ist nicht möglich, wenn per Tastatur nach unten oder oben gescrollt wird. (ASSETS-17257)
* Es ist nicht möglich, einen Workflow für mehrere ausgewählte Assets auszulösen, die mit Suchfiltern gefunden wurden. (ASSETS-7689)
* Wenn Sie ein Asset (oder mehrere Assets) aus den Suchergebnissen auswählen, ist die Option zum Zuordnen oder Aufheben der Zuordnung nicht sichtbar. Ansonsten ist die Option jedoch verfügbar. (ASSETS-7679)
* Der Suchfilter-Bereich wird nur einmal nach der Anmeldung geöffnet, aber nicht, wenn Sie die Suchseite verlassen und die Suche erneut ausführen. (ASSETS-7671)
* Das E-Mail-Kombinationsfeld zeigt beim Teilen eines Links kein angemessenes Kontrastverhältnis an. (ASSETS-17349)

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST 
* When you select any file in a Collection and click `Download`, and then navigate to the email checkbox and expand it, regular text and email link is not recognizable due to background color. (ASSETS-17349) 
* When you navigate to `Smart Crop` option, the screen reader does not announce the expand or collapse state of the button. (ASSETS-17335)-->

#### [!DNL Assets] – [!DNL Dynamic Media]{#dm-6517}

* Die Verbindung zu Dynamic Media ist unterbrochen, wenn bereits eine Dynamic Media Cloud-Konfiguration vorhanden ist. (ASSETS-23057)
* Die Leistung beim Durchsuchen von Ordnern mit vielen Dynamic Media-Videos wurde verbessert und das Problem des fehlgeschlagenen Ladevorgangs in der Ordnerkartenansicht behoben. (ASSETS-23016)
* Vorschau-Token werden aus `error.log` entfernt, die zum Anfordern sicherer Inhalte von den sicheren Test-Servern verwendet werden können. (ASSETS-22685)
* Rendering von PDF-Miniaturbildern mit Hinzufügen eines Schattens. Gibson lib-Version 4.0.1680232194 wurde aktualisiert, um das Problem beim Rendering von PDF-Miniaturansichten zu beheben. (ASSETS-22585)
* Der Hybridmodus von Dynamic Media ist jetzt mit der New Relic Agent-Version 8.0.1 kompatibel. (ASSETS-22578)
* Experience Manager-ACLs (Zugriffssteuerungslisten) werden jetzt bei der Vorschau von Dynamic Media-Dateien auf Experience Manager berücksichtigt. (ASSETS-21628)
* Bildschirmlesehilfen navigieren nicht zu einem ausgeblendeten Element, wenn Benutzende versuchen, mit der Nach-unten-Pfeiltaste oder der Tabulatortaste zu navigieren. (ASSETS-5617)
* Die Benutzeroberfläche des Bildprofils ist für smarte Zuschnitte mit demselben Namen, derselben Dimension oder beidem eingeschränkt. (ASSETS-16997)
* Standardbreite und -höhe für smarte Zuschnitte auf der Bildprofil-Benutzeroberfläche sind jetzt auf 50 Pixel eingestellt. (ASSETS-16997)

### [!DNL Forms]{#forms-6517}

* Nach der Aktualisierung auf AEM 6.5.15.0 Service Pack funktionieren die HTML5-Formulare im Edge-Browser mit dem IE-Kompatibilitätsmodus nicht oder werden nicht ordnungsgemäß geladen. (FORMS-8526, FORMS-8523)
* Wenn Benutzende AEM 6.5.16.0 Service Pack anwenden, kann der Regeleditor nicht geöffnet werden. (FORMS-8290)
* Wenn die Überprüfung der maximalen Anzahl von Ziffern auf eine Komponente vom Typ „Numerisches Feld“ angewendet wird, schlägt sie fehl. (FORMS-7938)
* Beim Erstellen interaktiver Kommunikationsanweisungen wird die Diagrammkomponente im PDF nicht ordnungsgemäß generiert. (FORMS-7827, FORMS-8297)
* Die Java™-Speicherbereinigung ist nicht in der Lage, den alten Gen-Heap auf einem Experience Manager Forms-OSGi-Server zu löschen. (FORMS-8207)
* Wenn Benutzende auf das Experience Manager 6.5.16.0 Service Pack aktualisieren, fehlen nach der Übermittlung die Eigenschaften der CRX-Metadaten. (FORMS-8205)
* Wenn Benutzende die Komponente für die Datumsauswahl in einem adaptiven Formular deaktivieren, kann sie trotzdem weiterhin bearbeitet werden. (FORMS-7804)
* Wenn Benutzende in Experience Manager 6.5.16.0 Forms Service Pack versuchen, die Richtliniensatz-Koordinatorinnen und -Koordinatoren zu bearbeiten, bleibt der Manager Document Publisher immer deaktiviert. (FORMS-7775, FORMS-8599)
* Wenn Benutzende auf das Experience Manager 6.5.16.0 Service Pack aktualisieren, funktioniert die Methode „GuideNode.externalize“, die zu übersetzende Strings verarbeiten soll, nicht mehr. (FORMS-7709)
* Wenn Benutzende im Schritt `Assign task` die Option „E-Mail-Benachrichtigung senden“ auswählen und den Workflow aufrufen, wird der Text in der empfangenen E-Mail nicht ordnungsgemäß angezeigt. Anstelle des Textes in der empfangenen E-Mail werden Fragezeichen empfangen. (FORMS-7675)
* Das Datensatzdokument wird teilweise lokalisiert. (FORMS-7674, FORMS-7573)
* Benutzende können Richtliniensätze nicht bearbeiten, selbst wenn bestimmte Berechtigungen zugewiesen wurden. (FORMS-7665)
* Wenn Benutzende der Gruppe `forms-users` versuchen, ein Formular zu erstellen, stürzt die Experience Manager Forms-Instanz ab. (FORMS-7629)
* Wenn Benutzende in einem adaptiven Formular auf die Schaltflächen „Zurücksetzen“, „Speichern“ oder „Senden“ klicken, wird keine Meldung auf dem Bildschirm angezeigt. (FORMS-7524)
* Um die PDFG-Konversion in einem Experience Manager 6.5.16.0 Service Pack zu verbessern, wird das Schlafintervall konfigurierbar gemacht. (FORMS-6752)
* Die Umschaltoption bleibt gleich, aber die Sichtbarkeit des Felds ändert sich selbst dann, wenn Benutzende den Cursor leicht ziehen. (FORMS-6728)
* Wenn Benutzende ein Upgrade auf Experience Manager 6.5.15.0 Service Pack durchführen, funktioniert die Weiterleitung nicht mehr, wenn ein adaptives Formular im Internet Explorer gerendert wird. (FORMS-6725)
* Das PAC 2021-Tool für alle Hintergrundobjekte in einem PDF-Formular, das von Experience Manager Designer erstellt wurde, gibt einen Fehler als `Path object not tagged` zurück. (FORMS-6707)
* Wenn Benutzende einen Filter im Posteingang anwenden, wird ein `NullPointerException`-Fehler ausgelöst. (FORMS-6706)
* Wenn Benutzende eine Vorlagendatei (.tds) mit referenzierten Fragmenten importieren, stürzt Experience Manager Designer ab. (FORMS-6702)
* Wenn Benutzende mit dem Output-Dienst in Experience Manager Forms Designer 6.5 eine statische PDF-Datei erstellen, tritt ein Fehler `OCCD (optional content configuration dictionary) contains AS key` auf. (FORMS-6691)
* Wenn Benutzende einen einfachen Workflow erstellen und eine einfache Variable hinzufügen, tritt ein `set variable mapping`-Fehler auf. (FORMS-5819)
* Wenn Benutzende versuchen, eine PDF mit dem Ausgabe-Service zu generieren, obwohl sie als `PDF/A-1a` markiert ist, schlägt eine Konformitätsprüfung mit dem `Preflight`-Service fehl. (LC-3920837)
* Nach der Installation eines Experience Manager 6.5.16.0 Service Packs kann Experience Manager Designer nicht geöffnet werden. (LC-3921000)
* Wenn Benutzende ein Kontrollkästchen und ein Optionsfeld hinzufügen, wird die Struktur eines Tag-Baums nicht gemäß PDF-Standards generiert. (LC-3920838)
* Wenn Benutzende über den Ausgabe-Service eine statische PDF-Datei generieren, indem sie die Schriften einbetten und unterteilen, enthält die resultierende PDF-Datei nur die eingebetteten Schriften. (LC-3920963)
* Der hebräische Text wird im RTL-Format falsch angezeigt. (LC-3919632)
* Wenn Benutzende auf das Experience Manager 6.5.16.0 Service Pack auf einem JBoss® Turnkey-Server aktualisieren, kann der Signaturdienst nicht aufgerufen werden. Der aufgetretene Fehler lautet: `java.lang.ClassCastException: com.adobe.xfa.TextNode cannot be cast to com.adobe.xfa.Element`. (FORMS-7833)
* Nach der Aktualisierung auf das Experience Manager 6.5.14.0 Service Pack funktionieren die Workbench-Prozesse zum Verschieben eines CRX-Knotens von einem Speicherort an einen anderen nicht. Der Fehler wird als `ALC-CRX-30000-000: com.adobe.ep.crx.client.exceptions.CRCException: ALC-CRX-030-000-[Internal Server Error]` angezeigt. (FORMS-7713)
* Wenn Benutzende auf das Experience Manager 6.5.16.0 Service Pack aktualisieren, kann `Usage Rights` nicht angewendet werden. (FORMS-7892)
* Wenn Benutzende versuchen, ein PDF-Dokument zu generieren, schlägt die PDF/A-1b-Validierung fehl. (FORMS-7615)
* Wenn Benutzende auf die Option `Configure` für die Komponente `Form Container` klicken, reagiert der Browser nicht mehr. (FORMS-7605)
* Wenn Benutzende auf das Experience Manager Forms 6.5.16.0 Service Pack aktualisieren und versuchen, die `LicenseType` in `Production` zu ändern, werden die Änderungen nicht übernommen. (FORMS-7594)
* Wenn Benutzende versuchen, einen LCA-Prozess mit einer PDF-Datei aufzurufen, die die `Chinese Full Width Characters` enthält, tritt ein Problem mit dem Prozess `ValidateForm` auf. (FORMS-7464)
* In Experience Manager Forms Designer generiert XMLFM eine ZPL-Ausgabe mit unterschiedlichen Papiergrößen wie Letter, A4 und A5 für XDP-basierte Vorlagen. (FORMS-7898)

### [!DNL Commerce]{#commerce-6517}

* Verschobene Tags werden zwar bereinigt, aber dennoch von Produkten unter `/var` referenziert. (CQ-4351337)

### Fundament{#foundation-6517}

#### Integrationen{#integrations-6517}

* Bei der Konvertierung einer Adobe Target-IMS-Konfiguration in Benutzeranmeldeinformationen in veralteten Cloud-Konfigurationen wird die Eigenschaft `connectedWhen` nicht geändert. Dieses Problem führt dazu, dass alle Aufrufe so laufen, als wäre die Konfiguration noch IMS-basiert. (CQ-4352810)
* Hinzufügen der Berechtigung `modifyProperties` zum Systembenutzer `fd-cloudservice` für die Adobe Sign-Konfiguration. (FORMS-6164)
* Wenn Sie eine AB-Test-Aktivität erstellen und Experience Manager in Adobe Target integriert ist, werden die damit verbundenen Zielgruppen nicht mit Target synchronisiert. (NPR-40085)

#### Oak{#oak-6517}

Ab Service Pack 13 wird das folgende Fehlerprotokoll angezeigt, das sich auf den Persistenz-Cache auswirkt:

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

#### Platform{#platform-6517}

* In der Experience Manager-Tag-Management-Benutzeroberfläche (/aem/tags/) werden die Namespaces und Tags in der Reihenfolge angezeigt, in der sie erstellt wurden. Wenn jedoch viele Namespaces und Tags vorhanden sind, ist es schwierig, sie anzuzeigen und zu verwalten. Das Problem liegt darin, dass sie nicht anders sortiert werden können. (NPR-39620)
* Aktualisierung der Google-Verschlussversion erforderlich, da Minification js für einige Client-Bibliotheken nicht funktioniert. (NPR-40043)

#### Sling{#sling-6517}

* Sling `ResourceMerger` verbraucht eine große Menge an CPU, wenn ein fiktiver Pfad angegeben wird, da dies zu einem Denial-of-Service führt. (NPR-40338)

#### Übersetzungsprojekte{#translation-6517}

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST * The `translationrules.xml` is sorted poorly when adding a rule to a property by way of the translation configuration user interface. (NPR-40431) -->
* Sprachkopie wird nicht erstellt, wenn Benutzende keine nicht obligatorischen Felder konfigurieren. (NPR-40036)

#### Benutzeroberfläche{#ui-6517}

* Die Schaltfläche „Abbrechen“ in den Seiteneigenschaften ist inaktiv. Sie sollten dadurch eigentlich zur Site-Admin-Benutzeroberfläche gelangen. (NPR-40501)

<!-- ## WCM{#wcm-6517}

* TEXT -->

#### Workflow{#workflow-6517}

* Änderungen an der Workflow-Konsole. (NPR-40502)
* `SegmentNotfound errors` in den Protokollen einer produktiven Autoreninstanz, verursacht durch einen nicht geschlossenen Ressourcen-Resolver in Klasse `com.day.cq.workflow.impl.email.EMailNotificationServic`. (NPR-40187)
* Es wird eine geschlossene, nicht geschlossene `ResourceResolver`-Ausnahme protokolliert. (ASSETS-22495)
* Experience Manager Author stürzt ab, wenn eine PSD/PDF mit großen `DocumentAncestors`-Metadatenattributen hochgeladen wird. (ASSETS-22966)
* Sitzungsleck in der Klasse `InboxSharingCache` mit `user-reader-service`. (CQ-4352513)
* Eine unvollständige Benutzer- und Gruppenliste wird angezeigt, wenn im Schritt „Workflow-Initiator-Teilnehmerauswahl“ die Benutzenden und Gruppen für den Teilnehmer-Schritt aufgelistet werden. Dieses Problem trat auf, wenn eine Gruppe auch Mitglied einer anderen Gruppe war. (NPR-40055)
* Verbesserte Bereinigung von Workflows. (NPR-40459)

## Installieren von [!DNL Experience Manager] 6.5.17.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.17.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über die Adobe-[Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.17.0 mit dem Package Manager auf einer der Authoring-Instanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.17.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren des Service Packs auf [!DNL Experience Manager] 6.5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Laden Sie das Service Pack von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle für die Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Normalerweise tritt dieses Problem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.17.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.17.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.17.0)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.15 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- NPR-40398 for 6.5.17.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zur Installation des Service Packs für Experience Manager Forms finden Sie unter [Installationsanweisungen für das Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kundinnen und Kunden, die GraphQL verwenden, müssen das [Experience Manager-Inhaltsfragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installieren.

Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen.

Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

### UberJar{#uber-jar}

UberJar für [!DNL Experience Manager] 6.5.17.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.17/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.17</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar und die anderen zugehörigen Artefakte sind im Maven Central Repository und nicht im Adobe Public Maven Repository verfügbar (`repo.adobe.com`). Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Es gibt also keinen `classifier` mit `apis` als Wert für den `dependency`-Tag.

## Veraltete Funktionen{#removed-deprecated-features}

Im Folgenden finden Sie eine Liste der Funktionen, die ab [!DNL Experience Manager] 6.5.7.0 als veraltet gekennzeichnet sind. Funktionen werden als veraltet markiert und später in einer zukünftigen Version entfernt. Eine alternative Option wird bereitgestellt.

Überprüfen Sie, ob Sie ein Feature oder eine Funktion in einer Bereitstellung verwenden. Planen Sie außerdem, die Implementierung zu ändern, sodass sie eine alternative Option verwendet.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integrationen | Der Bildschirm **[!UICONTROL Experience Manager Cloud Services Opt-in]** ist veraltet, da die Integration mit [!DNL Experience Manager] und [!DNL Adobe Target] in [!DNL Experience Manager] 6.5 aktualisiert wird. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Sie unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren, der Assistent für die Anmeldung ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime]-Integrationen über die jeweiligen [!DNL Experience Manager]-Cloud-Services. |
| Connectoren | Der Adobe JCR-Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für [!DNL Experience Manager] 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* Aktualisieren Sie Ihre GraphQL-Abfragen, die möglicherweise einen benutzerdefinierten API-Namen für Ihr Inhaltsmodell verwendet haben, und verwenden Sie stattdessen den Standardnamen des Inhaltsmodells.

* Eine GraphQL-Abfrage verwendet möglicherweise den `damAssetLucene`-Index anstelle des `fragments`-Index. Diese Aktion kann dazu führen, dass GraphQL-Abfragen fehlschlagen oder lange brauchen, um ausgeführt zu werden.

  Um das Problem zu beheben, muss `damAssetLucene` so konfiguriert werden, dass die folgenden beiden Eigenschaften einbezogen werden:

   * `contentFragment`
   * `model`

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

* Da [!DNL Microsoft® Windows Server 2019] [!DNL MySQL 5.7] und [!DNL JBoss® EAP 7.1] nicht unterstützt, unterstützt [!DNL Microsoft® Windows Server 2019] keine schlüsselfertigen Installationen für [!DNL Experience Manager Forms 6.5.10.0].

* Wenn Sie Ihre [!DNL Experience Manager]-Instanz von 6.5.0 bis 6.5.4 auf das neueste Service Pack für Java™ 11 aktualisieren, sehen Sie `RRD4JReporter`-Ausnahmen in der Datei `error.log`. Um die Ausnahmen zu stoppen, starten Sie Ihre Instanz von [!DNL Experience Manager] neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzende können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Wenn Benutzende ein Feld erstmals in einem adaptiven Formular konfigurieren möchten, wird im Eigenschaften-Browser die Option zum Speichern einer Konfiguration nicht angezeigt. Das Konfigurieren eines anderen Feldes des adaptiven Formulars im selben Editor behebt das Problem.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/source „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/ Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` – Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Auf der Plattform JBoss® 7.1.4 schlägt die Bereitstellung fehl, wenn Benutzende Experience Manager 6.5.16.0 oder ein höheres Service Pack installieren. `adobe-livecycle-jboss.ear`
* JDK-Versionen, die höher als 1.8.0_281 sind, werden für WebLogic JEE-Server nicht unterstützt.
* Ab AEM 6.5.15 hat die von dem ```org.apache.servicemix.bundles.rhino```-Bundle bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten. Skripte, die den strikten Modus (```use strict;```) müssen ihre Variablen korrekt deklarieren, andernfalls werden sie nicht ausgeführt, sondern es wird ein Laufzeitfehler ausgegeben.

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5.17.0 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5.17.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65170_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.17.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65170_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
