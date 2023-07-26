---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
exl-id: fed4e110-9415-4740-aba1-75da522039a9
source-git-commit: ea0f4096ac76ed11ee84a3769725f527c13fb461
workflow-type: tm+mt
source-wordcount: '3786'
ht-degree: 31%

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

[!DNL Experience Manager] 6.5.17.0 umfasst neue Funktionen, wichtige von Kunden angeforderte Verbesserungen, Fehlerbehebungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) auf [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen in dieser Version sind:

* **Verbesserungen bei der Suche** - Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:
   * Workflow erstellen
   * Version erstellen
   * Zuordnen oder Aufheben der Zuordnung von Assets

  Sie müssen nicht zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.
* **Dynamic Media _Momentaufnahme_**- Experimentieren Sie mit Testbildern oder Dynamic Media-URLs, um die Ausgabe verschiedener Bildmodifikatoren anzuzeigen, und optimieren Sie die intelligente Bildbearbeitung für Dateigröße (mit WebP- und AVIF-Bereitstellung), Netzwerkbandbreite und Gerätepixelverhältnis. Siehe [Dynamic Media-Schnappschuss](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).
* **DASH-Streaming mit Dynamic Media** - Neue Protokollunterstützung (DASH - Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in der Dynamic Media-Videobereitstellung (mit aktivierter CMAF). Jetzt für alle Regionen verfügbar, [aktiviert über ein Support-Ticket](/help/assets/video.md#enable-dash-on-your-account-enable-dash).
* **Integration von Experience Manager Sites und Inhaltsfragmenten in Assets Dynamic Media der nächsten Generation** - Benutzer von Experience Manager Assets as a Cloud Service Next-Generation Dynamic Media können diese Cloud-gehosteten Assets jetzt für die Bearbeitung und Bereitstellung mit On-Premise- oder Managed Services-Instanzen von Experience Manager Sites 6.5 verwenden.

## Verbesserungen im Service Pack 17 {#enhancements-sp17}

### Formulare{#aem-forms-6517}

* **[Adaptives Forms im AEM Seiteneditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)**: Sie können jetzt AEM Seiteneditor verwenden, um schnell mehrere Formulare zu Ihren Siteseiten zu erstellen und hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:
   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Adaptive Forms Container-Komponente im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Forms im AEM Sites-Editor, damit Sie unabhängig von einer beliebigen Sites-Seite Formulare erstellen können, damit Sie diese Formulare auf mehreren Seiten wiederverwenden können.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, optimieren Sie das Benutzererlebnis und bieten Sie mehr Flexibilität.
* **[Unterstützung von reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)**: Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms hinzugefügt, die zusätzlich zur Unterstützung von Google reCAPTCHA v2 einen verbesserten Schutz vor betrügerischer Aktivität und Spam bietet.
* **[Unterstützung von Adobe Acrobat Sign für Behörden mit Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)**: AEM Forms ist jetzt mit Adobe Acrobat Sign for Government integriert (FedRAMP-kompatibel). Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für e-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden). Durch die Integration mit Adobe Acrobat Sign for Government können Partner und Regierungskunden der Adobe elektronische Signaturen in Adaptive Forms für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig mit der Einhaltung der FedRAMP Moderate-Richtlinien konform sind, was den Regierungskunden der Adobe einen gesunden Menschenverstand verschafft.
* **Salesforce-Integration mit Experience Manager Forms für den Datenaustausch aktivieren**: Konfigurieren Sie die Integration zwischen Experience Manager Forms und der Salesforce-Anwendung mithilfe des Workflows OAuth 2.0-Client-Anmeldeinformationen. Diese Funktion ermöglicht eine sichere und direkte Authentifizierung und Autorisierung der Anwendung und ermöglicht eine nahtlose Kommunikation ohne Einbindung der Benutzer.
* **Optimierung und verbesserte Funktionalität der Workflow-Engine**: Erhöhen Sie die Leistung der Workflow-Engines, indem Sie die Anzahl der Workflow-Instanzen minimieren. Zusätzlich zu `COMPLETED` und `RUNNING` -Statuswerte unterstützt der Workflow auch drei neue Statuswerte: `ABORTED`, `SUSPENDED`, und `FAILED`.


<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 17 {#fixed-issues}

### [!DNL Sites]{#sites-6517}

* Leistungsabfall in LinkCheckerTransformer. (SITES-11661)
* Sprachkopien einer Seite wurden nicht erwartungsgemäß aktualisiert. (SITES-11191)
* Öffnen des Seitenaufrufs ohne Kampagne `targeteditor.html` unnötig. Entfernen Sie die `targeteditor` aufrufen, wenn nicht erforderlich. (SITES-12469)
* Live Copies können nicht für Seiten mit Anmerkungen erstellt werden. (SITES-12154)
* Das Rollout von Seiten funktioniert in Experience Manager 6.5.16 nicht. (SITES-12008)
* Unzureichender Speicher; hohe Speicherbereinigung aufgrund von `NotificationManagerImpl`. `NotificationManager` Bundle-Upgrade auf Experience Manager 6.5. (SITES-11440)
* Es wurden WCM-IT-Tests behoben, die Service Pack 17 blockierten. (SITES-13089)
* Das Abrufen von Sites-Verweisen schlägt beim Servlet fehl. (SITES-10901)

#### Admin-Benutzeroberfläche{#sites-adminui-6517}

* Das Vorschaufenster für die Bildauswahl für Miniaturansichten kann nicht geschlossen werden. (SITES-10459)

#### [!DNL Content Fragments]{#sites-contentfragments-6517}

* Konfiguration zum Herstellen einer Verbindung zum Polaris-Dienstobjekt (URL, Anmeldeinformationen, Callback usw.). (SITES-12149)
* Verwendung der `SemanticDataType.REFERENCE` sollte &quot;Remote-Asset-IDs&quot;unterstützen. (SITES-12127)
* Integrieren Sie Polaris Asset Selector in den Inhaltsfragment-Editor. (SITES-12125)
* Für den Zugriff auf den Metadatendienst-Endpunkt war ein obligatorischer HTTP-Header erforderlich. (SITES-13068)
* Die GraphQL-Implementierung von 6.5 entsprach nicht dem Cloud Service (primär). Identifizierte Probleme wurden behoben. (SITES-13096)
* GraphQL-Paging/Sortierung und Hybridfilterung sollten in Experience Manager 6.5/AMS verfügbar sein. (SITES-9154)

#### Kernkomponenten{#sites-core-components-6517}

* Die Eigenschaft `cq-msm-lockable` hat in der Foundation-Seitenkomponente den falschen Umleitungswert. (SITES-10904)
* Die Remote-Asset-Auswahl leitet immer zur IMS-Staging-Umgebung weiter. (SITES-13433)

#### [!DNL Experience Fragments]{#sites-experiencefragments-6517}

* Wenn Sie beim Export in Adobe Target eine Externalizer-Konfiguration in einem Experience Fragment auswählen, wird die falsche externalisierte URL gesendet. (SITES-12402)
* Entfernen Sie nicht integrative Begriffe; wenden Sie Richtlinien für inklusive Begriffe an. (SITES-11244)

#### Seiteneditor{#sites-pageeditor-6517}

* Für ein Karussellset wird in der Seitenleiste des Experience Manager Content Finders keine Miniaturansicht angezeigt. (SITES-8593)

### [!DNL Assets]{#assets-6517}

* Wenn Sie mehr als 40 PDF gleichzeitig veröffentlichen, [!DNL Experience Manager] reagiert nicht mehr und ist für einige Zeit nicht mehr verfügbar. (ASSETS-21789)
* Wenn Sie als Testbenutzer angemeldet sind, können Sie die Assets, die mit einem bestimmten Asset verknüpft sind, nicht sehen, wenn Sie auf die Eigenschaften eines Assets klicken. (ASSETS-21648)
* Beim Bearbeiten von Assets mit `Desktop Actions`, wenn Sie versuchen, mehr als fünf Assets gleichzeitig einzuchecken, `Limit Reached` angezeigt und die ausgewählten Assets ausgecheckt werden. (ASSETS-21121)
* Assets können in einer Sammlung nicht nach Namen sortiert werden. (ASSETS-20924)
* Dimensionen können nicht für Assets eines Bildformattyps festgelegt werden. (ASSETS-20835)
* Der QuickInfo-Text und der zugehörige Hintergrund im Feld E-Mail-Adresse suchen/hinzufügen zeigen beim Teilen eines Links kein angemessenes Kontrastverhältnis an. (ASSETS-17347)
* Wenn Sie `Notifications`, wird der Text aufgrund des Absatzabstands nicht richtig angezeigt. (ASSETS-17345)
* Wenn Sie ein Asset in der Sammlung kopieren, `Public Collection` nicht richtig angezeigt. (ASSETS-17343)
* Elemente verwenden ARIA-Attribute ohne Rolle. (ASSETS-17325, ASSETS-17323)
* Der Link ist beim Erweitern nicht beschreibend `Notifications`. (ASSETS-17283)
* Wenn Sie navigieren und die [!DNL Smart Crop] -Schaltfläche, erscheint der Inhalt wie eine Liste, aber nicht als ungeordnete Liste. Daher erkennt die Bildschirmlesehilfe die ungeordnete Liste nicht und liest sie nicht als Text. (ASSETS-17247)
* Die `Sort By` -Beschriftung nicht mit der entsprechenden Dropdown-Liste verknüpft ist. Daher erkennt die Bildschirmlesehilfe die Dropdown-Optionen nicht. (ASSETS-17239)
* Die Vorwärts- oder Rückwärtsbewegung kann nicht über die Tastatur-Tabulator- oder Pfeiltasten durchgeführt werden, wenn Sie versuchen, einen Benutzer mithilfe der `Add user` Kombinationsfeld. (ASSETS-17233)
* Die Informationen für den Schritt &quot;Workflows&quot;werden von der Bildschirmlesehilfe nicht korrekt bereitgestellt (ASSETS-17285).
* Wenn Sie zu `Saved Searches` -Kombinationsfeld verwenden, sind sowohl der Name als auch die Rolle nicht mit Bezeichnungen versehen. (ASSETS-17329)
* Beim Navigieren `Collection` und den Mauszeiger auf den Text bewegen *Mitglieder*, wird der Text nicht als markiert angezeigt. Daher erkennt die Bildschirmlesehilfe den Überschriftentext nicht und liest ihn nicht als Text. (ASSETS-17245)
* Zugriff nicht möglich `View Settings` -Option mit der Bildlauftaste nach unten oder nach oben über die Tastatur. (ASSETS-17257)
* Workflow kann nicht für mehrere ausgewählte Assets Trigger werden, die mithilfe von Suchfiltern gefunden werden. (ASSETS-7689)
* Wenn Sie ein Asset (oder mehrere Assets) aus den Suchergebnissen auswählen, ist die Option zum Zuordnen oder Aufheben der Zuordnung nicht sichtbar. Andernfalls ist die Option jedoch verfügbar. (ASSETS-7679)
* Der Bereich Suchfilter wird nach der Anmeldung nur einmal geöffnet und nicht geöffnet, wenn Sie die Suchseite verlassen und die Suche erneut ausführen. (ASSETS-7671)
* Das E-Mail-Kombinationsfeld zeigt beim Teilen eines Links kein angemessenes Kontrastverhältnis an. (ASSETS-17349)

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST 
* When you select any file in a Collection and click `Download`, and then navigate to the email checkbox and expand it, regular text and email link is not recognizable due to background color. (ASSETS-17349) 
* When you navigate to `Smart Crop` option, the screen reader does not announce the expand or collapse state of the button. (ASSETS-17335)-->

#### [!DNL Assets] – [!DNL Dynamic Media]{#dm-6517}

* Die Verbindung zu Dynamic Media ist unterbrochen, wenn bereits eine Dynamic Media Cloud-Konfiguration vorhanden ist. (ASSETS-23057)
* Die verbesserte Leistung beim Durchsuchen von Ordnern mit vielen Dynamic Media-Videos und gelöste Fehler beim Laden der Ordnerkartenansicht. (ASSETS-23016)
* Vorschau-Token werden aus entfernt `error.log` die verwendet werden kann, um sichere Inhalte von den sicheren Testservern anzufordern. (ASSETS-22685)
* PDF-Miniaturbild-Rendering, wodurch ein Schatten hinzugefügt wird. Gibson lib-Version 4.0.1680232194 wurde aktualisiert, um das Rendering von PDF-Miniaturansichten zu beheben. (ASSETS-22585)
* Der Dynamic Media Hybridmodus ist jetzt mit der New Relic Agent-Version 8.0.1 (ASSETS-22578) kompatibel.
* Experience Manager-ACLs (Zugriffssteuerungslisten) werden jetzt bei der Vorschau von Dynamic Media-Dateien auf Experience Manager berücksichtigt. (ASSETS-21628)
* Bildschirmlesehilfen navigieren nicht zu einem ausgeblendeten Element, wenn der Benutzer versucht, mit der Nach-unten-Taste oder der Tabulatortaste zu navigieren. (ASSETS-5617)
* Die Benutzeroberfläche des Bildprofils ist für smarte Zuschnitte mit demselben Namen, derselben Dimension oder beidem eingeschränkt. (ASSETS-16997)
* Standardbreite und -höhe für Smart-Zuschnitte auf der Benutzeroberfläche &quot;Bildprofil&quot;jetzt auf 50 Pixel eingestellt. (ASSETS-16997)

### [!DNL Forms]{#forms-6517}

* Nach der Aktualisierung auf AEM 6.5.15.0 Service Pack funktionieren die HTML5-Formulare im Edge-Browser mit dem IE-Kompatibilitätsmodus nicht oder werden nicht ordnungsgemäß geladen. (FORMS-8526, FORMS-8523)
* Wenn ein Benutzer AEM 6.5.16.0 Service Pack anwendet, kann der Regeleditor nicht geöffnet werden. (FORMS-8290)
* Wenn die maximale Anzahl von Ziffern-Validierungen auf eine Komponente vom Typ &quot;Numerisches Feld&quot;angewendet wird, schlägt dies fehl. (FORMS-7938)
* Beim Erstellen interaktiver Kommunikationsanweisungen wird die Diagrammkomponente im PDF nicht ordnungsgemäß generiert. (FORMS-7827, FORMS-8297)
* Die Java™-Speicherbereinigung kann den alten Generieren-Heap auf einem Experience Manager Forms-OSGi-Server nicht löschen. (FORMS-8207)
* Wenn ein Benutzer auf Experience Manager 6.5.16.0 Service Pack aktualisiert, fehlen die Eigenschaften der CRX-Metadaten nach der Übermittlung. (FORMS-8205)
* Wenn ein Benutzer die Komponente für die Datumsauswahl in einem adaptiven Formular deaktiviert, kann sie weiterhin bearbeitet werden. (FORMS-7804)
* Wenn ein Benutzer in Experience Manager 6.5.16.0 Forms Service Pack versucht, die Richtliniensatzkoordinatoren zu bearbeiten, bleibt der Manager Document Publisher immer deaktiviert. (FORMS-7775, FORMS-8599)
* Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.16.0 Service Pack durchführt, funktioniert die &quot;GuideNode.externalize&quot;-Methode, die zu übersetzende Strings verarbeitet, nicht mehr. (FORMS-7709)
* Im `Assign task` Schritt: Wenn ein Benutzer die &quot;Benachrichtigungs-E-Mail senden&quot;auswählt und den Workflow aufruft, wird der Text nicht ordnungsgemäß in der empfangenen E-Mail angezeigt. Die Fragezeichen werden anstelle des Textes in der empfangenen E-Mail empfangen. (FORMS-7675)
* Das Datensatzdokument wird teilweise lokalisiert. (FORMS-7674, FORMS-7573)
* Ein Benutzer kann Richtliniensätze nicht bearbeiten, selbst wenn bestimmte Berechtigungen zugewiesen wurden. (FORMS-7665)
* Wenn ein Benutzer in `forms-users` versucht, ein Formular zu erstellen, stürzt die Experience Manager Forms-Instanz ab. (FORMS-7629)
* Wenn der Benutzer in einem adaptiven Formular auf die Schaltflächen Zurücksetzen, Speichern oder Senden klickt, wird keine Nachricht auf dem Bildschirm angezeigt. (FORMS-7524)
* Um die PDFG-Konvertierung in einem Experience Manager 6.5.16.0 Service Pack zu verbessern, wird das Schlafintervall konfigurierbar gemacht. (FORMS-6752)
* Die Umschalter-Option bleibt gleich, aber die Sichtbarkeit des Felds ändert sich auch, wenn ein Benutzer den Cursor leicht zieht. (FORMS-6728)
* Wenn der Benutzer ein Upgrade auf Experience Manager 6.5.15.0 Service Pack durchführt, funktioniert die Weiterleitung nicht mehr, wenn ein adaptives Formular in Internet Explorer wiedergegeben wird. (FORMS-6725)
* Das PAC 2021-Tool für alle Hintergrundobjekte in einem PDF-Formular, das von einem Experience Manager-Designer erstellt wurde, gibt einen Fehler als `Path object not tagged`. (FORMS-6707)
* Wenn ein Benutzer einen Filter im Posteingang anwendet, wird ein `NullPointerException` Fehler. (FORMS-6706)
* Wenn ein Benutzer eine Vorlagendatei (.tds) mit referenzierten Fragmenten importiert, stürzt der Experience Manager-Designer ab. (FORMS-6702)
* Wenn der Benutzer mit dem Output-Dienst in Experience Manager Forms Designer 6.5 eine statische PDF erstellt, tritt ein Fehler auf, wenn `OCCD (optional content configuration dictionary) contains AS key`. (FORMS-6691)
* Wenn der Benutzer einen einfachen Workflow erstellt und eine einfache Variable hinzufügt, wird ein `set variable mapping` Fehler auftritt. (FORMS-5819)
* Wenn ein Benutzer versucht, eine PDF mit dem Output-Dienst zu generieren, obwohl er als `PDF/A-1a`, eine Konformitätsprüfung mit der`Preflight` -Dienst schlägt fehl. (LC-3920837)
* Nach der Installation eines Experience Manager 6.5.16.0 Service Packs kann ein Experience Manager-Designer nicht geöffnet werden. (LC-3921000)
* Wenn ein Benutzer ein Kontrollkästchen und ein Optionsfeld hinzufügt, wird die Struktur eines Tag-Baums nicht gemäß PDF-Standards generiert. (LC-3920838)
* Wenn ein Benutzer über den Ausgabedienst eine statische PDF generiert, indem er die Schriften einbettet und unterteilt, enthält die resultierende PDF nur die eingebetteten Schriften. (LC-3920963)
* Der hebräische Text wird im RTL-Format falsch angezeigt. (LC-3919632)
* Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.16.0 Service Pack auf einem JBoss® Turnkey-Server durchführt, kann der Signature-Dienst nicht aufgerufen werden. Der aufgetretene Fehler lautet: `java.lang.ClassCastException: com.adobe.xfa.TextNode cannot be cast to com.adobe.xfa.Element`. (FORMS-7833)
* Nach der Aktualisierung auf Experience Manager 6.5.14.0 Service Pack funktionieren die Workbench-Prozesse zum Verschieben eines CRX-Knotens von einem Speicherort an einen anderen nicht. Der Fehler tritt auf als `ALC-CRX-30000-000: com.adobe.ep.crx.client.exceptions.CRCException: ALC-CRX-030-000-[Internal Server Error]`. (FORMS-7713)
* Wenn ein Benutzer auf das Experience Manager 6.5.16.0 Service Pack aktualisiert, wird die `Usage Rights` nicht zutrifft. (FORMS-7892)
* Wenn ein Benutzer versucht, ein PDF-Dokument zu generieren, schlägt die PDF/A-1b-Validierung fehl. (FORMS-7615)
* Wenn ein Benutzer auf die `Configure` -Option für `Form Container` -Komponente nicht mehr reagiert. (FORMS-7605)
* Wenn ein Benutzer auf das Experience Manager Forms 6.5.16.0 Service Pack aktualisiert und versucht, die `LicenseType` nach `Production`, werden die Änderungen nicht übernommen. (FORMS-7594)
* Wenn ein Benutzer versucht, einen LCA-Prozess mit einer PDF aufzurufen, die die `Chinese Full Width Characters`, tritt ein Problem mit der `ValidateForm` -Prozess. (FORMS-7464)
* In Experience Manager Forms Designer generiert XMLFM eine ZPL-Ausgabe mit unterschiedlichen Papiergrößen wie Brief, A4 und A5 für XDP-basierte Vorlagen. (FORMS-7898)

### [!DNL Commerce]{#commerce-6517}

* Verschiebte Tags werden zwar bereinigt, werden aber dennoch von Produkten unter referenziert `/var`. (CQ-4351337)

### Fundament{#foundation-6517}

#### Integrationen{#integrations-6517}

* Beim Konvertieren einer Adobe Target IMS-Konfiguration in eine Benutzerberechtigung in Legacy-Cloud-Konfigurationen wird die `connectedWhen` -Eigenschaft ändert sich nicht. Dieses Problem führt dazu, dass alle Aufrufe so laufen, als wäre die Konfiguration noch IMS-basiert. (CQ-4352810)
* Hinzufügen `modifyProperties` Berechtigung zu `fd-cloudservice` Systembenutzer für die Adobe Sign-Konfiguration. (FORMS-6164)
* Wenn Sie eine A/B-Test-Aktivität erstellen und Experience Manager in Adobe Target integriert ist, werden die damit verbundenen Zielgruppen nicht mit Target synchronisiert. (NPR-40085)

#### Oak{#oak-6517}

Ab Service Pack 13 wird das folgende Fehlerprotokoll angezeigt, das sich auf den Persistenzcache auswirkt:

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
Neue Ordner von `cache` und `diff-cache` automatisch erstellt werden und Sie keine Ausnahme mehr im Zusammenhang mit `mvstore` im `error.log`.

#### Platform{#platform-6517}

* In der Experience Manager Tag Management-Benutzeroberfläche (/aem/tags/) werden die Namespaces und Tags in der Reihenfolge angezeigt, in der sie erstellt wurden. Wenn jedoch viele Namespaces und Tags vorhanden sind, ist es schwierig, sie anzuzeigen und zu verwalten. Das Problem liegt darin, dass sie nicht anders sortiert werden können. (NPR-39620)
* Aktualisierung der Google-Verschlussversion erforderlich, da Minification js für einige Client-Bibliotheken nicht funktioniert. (NPR-40043)

#### Sling{#sling-6517}

* Sling `ResourceMerger` verbraucht eine hohe CPU-Menge, wenn ein fiktiver Pfad zur Verfügung gestellt wird, was zu einer Dienstverweigerung führt. (NPR-40338)

#### Übersetzungsprojekte{#translation-6517}

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST * The `translationrules.xml` is sorted poorly when adding a rule to a property by way of the translation configuration user interface. (NPR-40431) -->
* Die Sprachkopie wird nicht erstellt, wenn der Benutzer keine nicht obligatorischen Felder konfiguriert. (NPR-40036)

#### Benutzeroberfläche{#ui-6517}

* Die Schaltfläche &quot;Abbrechen&quot;in den Seiteneigenschaften ist inaktiv. Sie sollten zur Benutzeroberfläche &quot;Site-Administrator&quot;gelangen. (NPR-40501)

<!-- ## WCM{#wcm-6517}

* TEXT -->

#### Workflow{#workflow-6517}

* Änderungen an der Workflow-Konsole. (NPR-40502)
* `SegmentNotfound errors` in den Protokollen in einer Produktionsautorinstanz, verursacht durch nicht geschlossene Resource Resolver in der Klasse `com.day.cq.workflow.impl.email.EMailNotificationServic`. (NPR-40187)
* Nicht verschlossen `ResourceResolver` Ausnahmefehler wird protokolliert. (ASSETS-22495)
* Experience Manager-Autor stürzt beim PSD/PDF mit riesigen `DocumentAncestors` Metadatenattribute werden hochgeladen. (ASSETS-22966)
* Sitzungsleck in der Klasse `InboxSharingCache` mit `user-reader-service`. (CQ-4352513)
* Eine unvollständige Benutzer- und Gruppenliste wird angezeigt, wenn im Schritt &quot;Workflow-Initiator-Teilnehmerauswahl&quot;die Benutzer und Gruppen für den Teilnehmer-Schritt aufgelistet werden. Dieses Problem trat auf, wenn eine Gruppe auch Mitglied einer anderen Gruppe war. (NPR-40055)
* Verbesserte Bereinigung der Workflows. (NPR-40459)

## Installieren von [!DNL Experience Manager] 6.5.17.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.17.0 erfordert [!DNL Experience Manager] 6.5. Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Download des Service Packs ist über Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip) verfügbar.
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.17.0 mit dem Package Manager auf einer der Authoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.17.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie der `crx-repository` für den Fall, dass Sie sie zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
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

Anweisungen zum Installieren des Service Packs auf Experience Manager Forms finden Sie unter [Installationsanweisungen für Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

### Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente{#install-aem-graphql-index-add-on-package}

Kunden, die GraphQL verwenden, müssen die [Experience Manager Content Fragment mit GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip).

Auf diese Weise können Sie die erforderliche Indexdefinition hinzufügen, die auf den tatsächlich verwendeten Funktionen basiert.

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
| Integrationen | Der Bildschirm **[!UICONTROL Experience Manager Cloud Services-Opt-in]** nicht mehr unterstützt wird, da die Variable [!DNL Experience Manager] und [!DNL Adobe Target] -Integration aktualisiert in [!DNL Experience Manager] 6.5. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Sie unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren, der Assistent für die Anmeldung ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime]-Integrationen über die jeweiligen [!DNL Experience Manager]-Cloud-Services. |
| Connectoren | Der Adobe JCR-Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für [!DNL Experience Manager] 6.5 nicht mehr unterstützt. | Nicht zutreffend |

## Bekannte Probleme{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* Aktualisieren Sie Ihre GraphQL-Abfragen, die möglicherweise einen benutzerdefinierten API-Namen für Ihr Inhaltsmodell verwendet haben, so, dass stattdessen der Standardname des Inhaltsmodells verwendet wird.

* Eine GraphQL-Abfrage verwendet möglicherweise den `damAssetLucene`-Index anstelle des `fragments`-Index. Diese Aktion kann dazu führen, dass GraphQL-Abfragen fehlschlagen oder dass die Ausführung lange dauert.

  Um das Problem zu beheben, muss `damAssetLucene` so konfiguriert werden, dass die folgenden beiden Eigenschaften einbezogen werden:

   * `contentFragment`
   * `model`

  Nach Änderung der Indexdefinition ist eine Neuindizierung erforderlich (`reindex` = `true`).

  Nach diesen Schritten sollten die GraphQL-Abfragen schneller funktionieren.

* Beim Versuch, Inhaltsfragmente, Sites oder Seiten zu verschieben, zu löschen oder zu veröffentlichen, tritt ein Problem beim Abrufen von Inhaltsfragmentverweisen auf, da die Hintergrundabfrage fehlschlägt. Das heißt, die Funktionalität funktioniert nicht.
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

* auf der JBoss® 7.1.4-Plattform, wenn der Benutzer Experience Manager 6.5.16.0 oder höher installiert, `adobe-livecycle-jboss.ear` Die Bereitstellung schlägt fehl.
* JDK-Versionen, die höher als 1.8.0_281 sind, werden für WebLogic JEE-Server nicht unterstützt.
* Ab AEM 6.5.15 wird die von der ```org.apache.servicemix.bundles.rhino``` Das Bundle weist ein neues Hosting-Verhalten auf. Skripte, die den strikten Modus (```use strict;```) müssen ihre Variablen korrekt deklarieren, andernfalls werden sie nicht ausgeführt, sondern es wird ein Laufzeitfehler ausgegeben.

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
