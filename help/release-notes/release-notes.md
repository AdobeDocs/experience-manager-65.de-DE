---
title: Versionshinweise für [!DNL Adobe Experience Manager] 6.5
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für [!DNL Adobe Experience Manager] 6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 14b52e7763c4d83a4dcce593f155cb1bb8f56b97
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 55%

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
| Version | 6,5,21,0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | Freitag, 23. Mai 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Was in [!DNL Experience Manager] 6.5.21.0 enthalten ist {#what-is-included-in-aem-6521}

[!DNL Experience Manager] 6.5.21.0 umfasst neue Funktionen, wichtige von Kunden angeforderte Verbesserungen, Fehlerbehebungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install) on [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

## Wichtige Funktionen und Verbesserungen

<!-- * _6.5.21.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* Eine neue, benutzerfreundlichere Berechtigung für die Server-zu-Server-Authentifizierung, die die vorhandene JWT-Berechtigung (Service Account) ersetzt. (NPR-41994) MAJOR

### [!DNL Forms]

* A

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Behobene Probleme im Service Pack 21 {#fixed-issues}

### [!DNL Sites]{#sites-6521}

#### Barrierefreiheit {#sites-accessibility-6521}

* Die **[!UICONTROL Gespeicherte Suchen]** -Beschriftung nicht persistent ist. Der Platzhalter wird als einzige visuelle Bezeichnung für ein Textfeld verwendet. (SITES-3050)

#### Admin-Benutzeroberfläche{#sites-adminui-6521}

* Wenn Sie auf **[!UICONTROL Sites]** > **[!UICONTROL Kernkomponenten]** > **[!UICONTROL Eigenschaften]** > **[!UICONTROL Berechtigungen]** tab > **[!UICONTROL Effektive Berechtigung]**, die **Effektive Berechtigungen** -Dialogfeld wird nicht geöffnet. (SITES-17378)

#### Klassische Benutzeroberfläche{#sites-classicui-6521}

* T

#### [!DNL Content Fragments]{#sites-contentfragments-6521}

* Die doppelte Einbeziehung der Formularelemente wurde korrigiert. (SITES-21109) BLOCKER
* Beim Erstellen eines Inhaltsfragments reagiert die Schaltfläche Schließen manchmal nicht mehr, wodurch die gesamte Seite eingefroren wird und eine Seitenaktualisierung erforderlich ist, um das Inhaltsfragment zu schließen. Was das Problem bei der Versionserstellung betrifft, erstellt das System eine neue Version eines Inhaltsfragments. Dies geschieht auch dann, wenn der Benutzer keine Änderungen vorgenommen hat, indem er einfach mit dem RTE oder einem Textfeld interagiert. (SITES-21187) MAJOR


#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-6521}

* Bei der Aktualisierung von Adobe Experience Manager von 6.5.19.0 auf 6.5.20.0 ist der Pfad `/libs/cq/graphql/sites/graphiql` wurde gelöscht. (SITES-20098) CRITICAL




#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6521}

* Mi

#### [!DNL Content Fragments] – REST-API{#sites-restapi-6521}

* Mi

#### Core-Backend{#sites-core-backend-6521}

* Mi

#### Kernkomponenten{#sites-core-components-6521}

* I

#### Campaign-Integration{#sites-campaign-integration-6521}

* A

#### Experience Fragments{#sites-experiencefragments-6521}

* Rollout von Experience Fragments aus `masters/language` nach `country/language` aktualisiert keine Querverweise. (SITES-20559) BLOCKER
* Nicht nur in der Variablen `cq:allowedTemplates`, jedoch Vorlagen mit `allowedPaths` auf Vorlagenebene konfiguriert werden, werden beim Erstellen eines neuen Experience Fragment als Optionen angezeigt. (SITES-20855) MAJOR

#### Foundation-Komponenten (veraltete Version){#sites-foundation-components-legacy-6521}

* T

#### Launches{#sites-launches-6521}

* Die `sourceRootResource` in der Launch-Konfiguration innerhalb von CRXDE Lite auf nicht mehr vorhandene Inhalte verweist, was zu einer Funktionsstörung führt, wenn versucht wird, Launches zu löschen. Löschen wird auch dann gestartet, wenn die Seite gelöscht wird oder wenn der Pfad nicht derselbe ist. (SITES-20750)

#### MSM – Live Copies{#sites-msm-live-copies-6521}

* Die Seitenkomponente wurde überlagert, um in den Seiteneigenschaften Registerkarten hinzuzufügen. Einer davon ist die Seitenkonfiguration und verfügt über eine Eigenschaft zum Hinzufügen einer Experience Fragment-URL. Der in den Seiteneigenschaften für das Experience Fragment konfigurierte Link ändert sich für keine Sprachkopien, die für diese Seite erstellt wurden. Der konfigurierte Link sollte sich mit der Sprachkopie-URL ändern. (SITES-19580) MAJOR

#### Seiteneditor{#sites-pageeditor-6521}

* Im Bearbeitungsmodus wird ein grauer Hintergrund inkonsistent angewendet, was nicht den WCAG-Farbkontraststandards (Web Content Accessibility Guidelines) entspricht. (SITES-20060)

### [!DNL Assets]{#assets-6521}

* U

#### [!DNL Dynamic Media]{#assets-dm-6521}

* Ab dem 1. Mai 2024 wird Adobe Dynamic Media die Unterstützung für Folgendes einstellen:
   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 und 1.1
   * Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

### [!DNL Forms]{#forms-6521}

<!--Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the AEM 6.5.21.0 Forms add-on package release is scheduled for Thursday, May 30, 2024. A list of Forms fixes and enhancements is added to this section post the release.-->

#### [!DNL Adaptive Forms]

* 
  <!-- THIS BUG WAS ALREADY REPORTED IN 6.5.20.0 RELEASE NOTES. IS IT NEEDED AGAIN IN THE 6.5.21.0 RELEASE NOTES? (AEM Forms on JEE Only) The PDF Generator service fails to enumerate the fonts available on the server. Consequently, the font selection panel on the Adobe PDF Settings page in the PDFG Admin UI remains empty, effectively preventing (un)embedding of chosen fonts. (FORMS-12095) -->


#### [!DNL Forms Designer] {#forms-designer-6521}

* Mi


### Fundament {#foundation-6521}

#### Apache Felix {#felix-6521}

* Aktualisierungsproblem mit AEM 6.5 Service Pack 19 (SP19), bei dem der Kontextstammpfad des Anwendungsservers für nicht autorisierte Anfragen an Apache Felix nach der Installation von SP19 fehlt. Aktualisierung auf Apache Felix Web Management Console 4.9.8. (NPR-41933)

* U

#### Campaign{#campaign-6521}

* AEM 6.5 Service Pack 15 erzeugt kontinuierliche Fehlerprotokolle mit signifikanten Einträgen. Die folgenden Probleme wurden gemeldet:

   * 404 INFO-Fehler wegen fehlender Ressource im Pfad `/libs/granite/ui/content/shell/start.html`
   * Fehlerprotokolleintrag für eine nicht abgefangene SlingException aufgrund von `NullPointerException` at `CampaignsDataSourceServlet.java:147`

  Fehlerprotokolle sollten nicht mit häufigen und umfangreichen Fehlereinträgen gefüllt werden. Die AEM-Instanz sollte ohne Probleme im Zusammenhang mit fehlenden Ressourcen oder Ausnahmen funktionieren. (CQ-4357064)

#### Communities {#communities-6521}

* U

#### Inhaltsverteilung{#foundation-content-distribution-6521}

* T

#### Granite{#granite-6521}

* **Löschen** oder **Ändern** Berechtigungen können nicht ohne **Durchsuchen** -Berechtigung im Konfigurationsbrowser. (GRANITE-51002)

#### Integrationen{#integrations-6521}

* Bezüglich `cq-target-integration`, müssen Sie die Verwendung von Google Guava, die nicht getestet wurde, entfernen. (CQ-4357101)
* Ersetzen von Service-Konto-Anmeldeinformationen (JSON Web Token oder JWT) durch OAuth2-Server-zu-Server-Anmeldeinformationen (auch als Service Principals bezeichnet).(NPR-41994) MAJOR
* Die Anforderung &quot;Zielgruppe erstellen&quot;schlägt mit der IMS-Konfiguration (Identity Management-System) fehl. (NPR-41888) MAJOR
* Wenn ein Kunde versucht, die Payload-Seite anzuzeigen, wird der Inhalt aufgrund einer fehlerhaften URL nicht richtig angezeigt. Es wird ein 404-Fehler angezeigt. Der Fehler wird durch verursacht, wenn vor den Abfrageparametern in der URL ein Fragezeichen-Symbol fehlt. Bei diesem Problem muss der Kunde das Fragezeichen-Symbol manuell einfügen, um die Payload-Seite korrekt anzuzeigen. (NPR-41957)
* Entfernen Sie den Code und die Abhängigkeiten von Adobe Search&amp;Promote aus AEM 6.5, die erreicht wurden. [Ende der Nutzungsdauer September 2022 gemäß Bekanntmachung](https://experienceleague.adobe.com/en/docs/discontinued/using/search-promote). (NPR-41855)


#### Lokalisierung{#localization-6521}

* Im Vorlageneditor wird die Textzeichenfolge *`No video available.`* nicht lokalisiert ist. (SITES-13190)
* Zeichenfolge nach der Aktivierung oder Deaktivierung eines Benutzers wird nicht lokalisiert in **Instrumente** > **Sicherheit** > **Benutzer** > *any_user_name* > **Aktivieren** > **OK** und wählen Sie *any_user_name* > **Deaktivieren** > **OK**. (NPR-41737)

#### Platform{#foundation-platform-6521}

* Die `Unclosed resource resolver` ein Fehler aufgetreten ist für `com.day.cq.mailer.impl.DefaultMailService`. Die `MessageGatewayService` -Klasse, die nativ ist, ohne Ressourcen-Resolver verwendet wurde. Das Problem trat auf jeder Seite auf, auf der eine Formularsendeschaltfläche vorhanden war, die eine E-Mail mit dieser Klasse sendet. (NPR-41853)

#### Sling{#foundation-sling-6521}

* T

#### Übersetzung{#foundation-translation-6521}

* Ein Problem, bei dem der standardmäßige Übersetzungsstatus von AEM 6.5.19 nicht wie für einen Launch erwartet aktualisiert wurde. Nachdem Sie eine übersetzte Datei in einen Übersetzungsauftrag importiert haben, der mit einem AEM Launch verknüpft ist, wurde erwartet, dass sich der Status in `Approved`. Stattdessen ändert sich der Status in `Ready for Review`, was nicht das erwartete Verhalten ist. (NPR-41756) MAJOR
* Beim Erstellen mehrerer Konfigurationen und Navigieren zu den Konfigurationen für Übersetzungs-Cloud Service werden nicht alle Elemente in der Benutzeroberfläche angezeigt. Es werden nur die ersten 40 Elemente/Ordner angezeigt. Lazy Loading wird ausgelöst, es werden jedoch keine weiteren Inhalte hinzugefügt. (NPR-41829)
* Auf der Seite &quot;Berechtigungen&quot;in der Touch-Benutzeroberfläche treten bei Japanisch unleserliche Zeichen auf. (NPR-41794)

#### Benutzeroberfläche{#foundation-ui-6521}

* In Tools > Sicherheit > Benutzer > &lt;user_name> > Profile in der **Benutzereinstellungen bearbeiten** -Dialogfeld wird das Dialogfeld nicht geschlossen, wenn Sie auf Abbrechen klicken. (NPR-41793) MAJOR
* Die Granite `pathfield` Komponente bei `/libs/granite/ui/components/coral/foundation/form/pathfield` schlägt fehl, um die **[!UICONTROL Auswählen]** Schaltfläche, wenn ein Asset ausgewählt ist. Nachdem das Pfadfeld ausgefüllt wurde und der Benutzer das Asset-Kontrollkästchen aktiviert hat, wird das **[!UICONTROL Auswählen]** -Schaltfläche nicht aktiviert ist; sie ändert sich nicht von grau in blau. (NPR-41970)
* Es gibt ein Problem mit dem Referenzfeld für das Inhaltsfragmentmodell (CFM) in AEM. Obwohl das CFM-Referenzfeld als obligatorisch festgelegt wurde, können Benutzer in bestimmten Szenarien auf Speichern klicken, um Inhalte mit Nicht-CFM-Werten zu speichern. Die Schaltfläche Speichern sollte abgeblendet sein (nicht verfügbar). (NPR-41894)
* Die Standarddialogfelder der Coral-Benutzeroberfläche, in denen die `successresponse` -Aktion muss eine Erfolgsantwort nach der -Aktion Trigger werden. In AEM 6.5 Service Pack 19 wird die Neuladungsaktion jedoch nicht aufgerufen und es wird keine Meldung angezeigt. (NPR-41797)
* AEM Benachrichtigungslinks funktionieren nicht in AEM 6.5 Service Pack 18. Bei der Aktualisierung auf Service Pack 18 funktionieren die Links für AEM Benachrichtigungen nicht, wenn die Nachrichten über die Schaltfläche Benachrichtigungen ausgewählt werden. (NPR-41792)

#### WCM{#wcm-6521}

* T

#### Workflow{#foundation-workflow-6521}

* In AEM 6.5.18 wiederholte Fehler beim Entfernen aus dem Benutzermetadaten-Cache während der Bereinigung. (NPR-41762)

## Installieren von [!DNL Experience Manager] 6.5.21.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.21.0 erfordert [!DNL Experience Manager] 6.5. Siehe die [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) für detaillierte Anweisungen. <!-- UPDATE FOR EACH NEW RELEASE -->
* Der Service Pack-Download ist unter Adobe verfügbar. [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip).
* Bei einer Bereitstellung mit MongoDB und mehreren Instanzen installieren Sie [!DNL Experience Manager] 6.5.21.0 mit dem Package Manager auf einer der Autoreninstanzen.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe rät davon ab, das Paket [!DNL Experience Manager] 6.5.21.0 zu entfernen oder zu deinstallieren. Daher sollten Sie vor der Installation des Pakets eine Sicherungskopie von `crx-repository` erstellen, falls Sie es zurücksetzen müssen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installieren Sie das Service Pack auf [!DNL Experience Manager] 6,5{#install-service-pack}

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.

1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.

1. Herunterladen des Service Sacks von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um den S3-Connector zu aktualisieren, stoppen Sie die Instanz nach der Installation des Service Packs, ersetzen Sie den vorhandenen Connector durch eine neue Binärdatei, die im Installationsordner bereitgestellt wird, und starten Sie die Instanz neu. Weitere Informationen finden Sie unter [Amazon S3-Datenspeicher](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation des Service Packs beendet. Adobe empfiehlt, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Bereitstellung zugegriffen wird. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installation erfolgreich war. Dieses Problem tritt vor allem im [!DNL Safari]-Browser auf, kann jedoch gelegentlich in jedem Browser auftreten.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie [!DNL Experience Manager] 6.5.21.0 automatisch installieren können.<!-- UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md#package-share). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

>[!NOTE]
>
>Experience Manager 6.5.21.0 unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (6.5.21.0)` unter [!UICONTROL Installierte Produkte] an.<!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.18 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installieren des Service Packs für [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Anweisungen zum Installieren des Service Packs auf Experience Manager Forms finden Sie unter [Installationsanweisungen für Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

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

UberJar für [!DNL Experience Manager] 6.5.21.0 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.20/) verfügbar. <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Um UberJar in einem Maven-Projekt zu verwenden, lesen Sie bitte [Verwendung von UberJar](/help/sites-developing/ht-projects-maven.md) und nehmen Sie die folgende Abhängigkeit in Ihr Projekt-POM auf: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.21</version>
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

* Wenn Sie Ihre [!DNL Experience Manager] von 6.5.0 bis 6.5.4 bis zum neuesten Service Pack auf Java™ 11 sehen Sie `RRD4JReporter` Ausnahmen in `error.log` -Datei. Um die Ausnahmen zu beenden, starten Sie Ihre Instanz von [!DNL Experience Manager] neu. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Benutzende können einen Ordner in einer Hierarchie in [!DNL Assets] umbenennen und einen verschachtelten Ordner in [!DNL Brand Portal] veröffentlichen. Der Titel des Ordners wird jedoch erst dann in [!DNL Brand Portal] aktualisiert, wenn der Stammordner erneut veröffentlicht wird.

* Die folgenden Fehler und Warnmeldungen können während der Installation von [!DNL Experience Manager] 6.5.x.x angezeigt werden:
   * „Wenn die Adobe Target-Integration mithilfe der Target Standard-API (IMS-Authentifizierung) in [!DNL Experience Manager] konfiguriert wird, führt der Export von Experience Fragments nach Target dazu, dass falsche Angebotstypen erstellt werden.“ Anstelle des Typs „Experience Fragment“/source „Adobe Experience Manager“ erstellt Target mehrere Angebote mit dem Typ „HTML“/ Quelle „Adobe Target Classic“.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Die Server-seitige Validierung des adaptiven Formulars schlägt fehl, wenn Aggregatfunktionen wie SUM, MAX und MIN verwendet werden. (CQ-4274424)
   * `com.adobe.granite.maintenance.impl.TaskScheduler` – Keine Wartungsfenster unter granite/operations/maintenance gefunden.
   * Der Hotspot in einem interaktiven Dynamic Media-Bild ist nicht sichtbar, wenn Sie eine Vorschau des Assets mit dem Viewer für Banner mit Shopping-Funktion anzeigen.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`: Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.

* Ab AEM 6.5.15 weist die vom Bundle ```org.apache.servicemix.bundles.rhino``` bereitgestellte Rhino-JavaScript-Engine ein neues Hoisting-Verhalten auf. Skripte, die den strikten Modus (```use strict;```) verwenden, müssen ihre Variablen korrekt deklarieren, sonst werden sie nicht ausgeführt, sondern geben einen Laufzeitfehler aus.

* Durch die Installation von Tag-bezogenen, vorkonfigurierten Inhalten über ein offizielles Update-Paket (einschließlich Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, Patches usw.) wird die Spracheigenschaft des Knotens „`/content/cq:tags`“ auf den Standardwert zurückgesetzt. Daher ist es erforderlich, sie vor der Installation aus den Eigenschaften hinzuzufügen.

### Bekannte Probleme bei AEM Sites {#known-issues-aem-sites-6521}

* SITES-17934 – Inhaltsfragmente – Vorschau schlägt aufgrund des DoS-Schutzes für eine umfassende Fragmentbaumstruktur fehl; Siehe [KB-Artikel zu den standardmäßigen Konfigurationsoptionen von GraphQL Query Executor](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23945)

### Bekannte Probleme bei AEM Forms {#known-issues-aem-forms-6521}

* T

## Enthaltene OSGi-Bundles und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5.Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5.21.0 enthaltenen OSGi-Bundles](/help/release-notes/assets/65200-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5.21.0 enthaltenen Inhaltspakete](/help/release-notes/assets/65200-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Produktseite](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] Dokumentation zu 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
>* [Abonnieren von Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)
