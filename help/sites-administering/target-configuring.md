---
title: Manuelles Konfigurieren der Integration mit Adobe Target
seo-title: Manuelles Konfigurieren der Integration mit Adobe Target
description: Es wird beschrieben, wie Sie die Integration mit Adobe Target manuell konfigurieren.
seo-description: Es wird beschrieben, wie Sie die Integration mit Adobe Target manuell konfigurieren.
uuid: 0bb76a65-f981-4cc5-bee8-5feb3297137c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 20c8eb1d-5847-4902-b7d3-4c3286423b46
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# Manuelles Konfigurieren der Integration mit Adobe Target {#manually-configuring-the-integration-with-adobe-target}

Sie können entweder die Konfigurationen für den Opt-in-Assistenten ändern, die Sie während der Nutzung des Assistenten vorgenommen haben, oder Sie können die Integration mit Adobe Target manuell durchführen, ohne den Assistenten zu nutzen.

## Ändern der Konfigurationen für den Opt-in-Assistenten {#modifying-the-opt-in-wizard-configurations}

The [Opt-in wizard](/help/sites-administering/opt-in.md) that [integrates AEM with Adobe Target](/help/sites-administering/target.md) automatically creates a Target cloud configuration named Provisioned Target Configuration. Außerdem erstellt der Assistent ein Target-Framework für die Cloud-Konfiguration mit dem Namen „Bereitgestelltes Target-Framework“. Sie können die Eigenschaften der Cloud-Konfiguration und des Frameworks bei Bedarf ändern.

Darüber hinaus können Sie Adobe Target auch als Quelle für die Berichterstellung für bestimmte Inhalte konfigurieren, indem Sie die „A4T-Analyse-Cloud-Konfiguration“ konfigurieren.

To locate the cloud configuration and the framework, Navigate to **Cloud Services** via **Tools** > **Deployment** > **Cloud**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)) Klicken oder tippen Sie unterhalb von Adobe Target auf **Konfigurationen anzeigen**.

### Eigenschaften der bereitgestellten Target-Konfiguration {#provisioned-target-configuration-properties}

Die folgenden Eigenschaftswerte werden in der Cloud-Konfiguration „Bereitgestellte Target-Konfiguration“ verwendet, die vom Opt-in-Assistenten erstellt wird:

* **** Client-Code: Wie im Einwahlassistenten angegeben.
* **** E-Mail: Wie im Einwahlassistenten angegeben.
* **** Kennwort: Wie im Einwahlassistenten angegeben.
* **** API-Typ: REST
* **** Segmente aus Adobe Target synchronisieren: Ausgewählt.

* **** Client-Bibliothek: mbox.js.
* **** Verwenden Sie DTM zur Bereitstellung der Client-Bibliothek: Nicht ausgewählt. Select this option if you [use DTM](/help/sites-administering/dtm.md) or another tag management system to host the mbox.js or AT.js file. Adobe empfiehlt zum Bereitstellen der Bibliothek die Verwendung von DTM anstelle von AEM.

* **** Benutzerdefinierte mbox.js: Keine angegeben, sodass die Standard-Datei &quot;mbox.js&quot;verwendet wird. Geben Sie bei Bedarf eine benutzerdefinierte Version der Datei „mbox.js“ an. Sie wird nur angezeigt, wenn Sie „mbox.js“ ausgewählt haben.
* **** Benutzerspezifische AT.js: Keine angegeben, sodass die Standard-Datei AT.js verwendet wird. Geben Sie bei Bedarf eine benutzerdefinierte Version der Datei „AT.js“ an. Sie wird nur angezeigt, wenn Sie „AT.js“ ausgewählt haben.

>[!NOTE]
>
>In AEM 6.3, you can select the Target Library file, [AT.JS](https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html), which is a new implementation library for Adobe Target that is designed for both typical web implementations and single-page applications.
>
>„AT.js“ bietet im Vergleich zur Bibliothek „mbox.js“ viele Verbesserungen, z. B.:
>
>* Verbesserte Seitenladezeiten für Web-Implementierungen
>* Verbesserte Sicherheit
>* Bessere Implementierungsoptionen für Einzelseitenanwendungen
>* „AT.js“ enthält die Komponenten, die in „target.js“ enthalten waren, sodass „target.js“ nicht mehr aufgerufen wird.
>
>
See [Target release notes](https://marketing.adobe.com/resources/help/en_US/target/rn/201604.html) for more information.

### Eigenschaften von „Bereitgestelltes Target-Framework“{#provisioned-target-framework-properties}

Das bereitgestellte Target-Framework, das vom Opt-in-Assistenten erstellt wird, ist für das Senden von Kontextdaten aus dem Profildatenspeicher konfiguriert. Die Datenelemente zu Alter und Geschlecht aus dem Speicher werden standardmäßig an Target gesendet. Es kann sein, dass für Ihre Lösung zusätzliche Parameter gesendet werden müssen.

![chlimage_1-158](assets/chlimage_1-158.png)

Sie können das Framework so konfigurieren, dass zusätzliche Kontextinformationen an Target gesendet werden, wie unter [Hinzufügen eines Target-Frameworks](/help/sites-administering/target-configuring.md#adding-a-target-framework) beschrieben.

### Konfigurieren der A4T-Analyse-Cloud-Konfiguration {#configuring-a-t-analytics-cloud-configuration}

Sie können Adobe Target so konfigurieren, dass Adobe Analytics als Quelle für die Berichterstellung zu bestimmten Inhalten verwendet wird.

Hierfür müssen Sie angeben, mit welcher A4T-Cloud-Konfiguration Ihre Adobe Target-Cloud-Konfiguration verbunden werden soll:

1. Navigate to **Cloud Services** via the **AEM logo** > **Tools** > **Deployment** > **Cloud Services**.
1. In the **Adobe Target** section, click **Configure Now**.
1. Stellen Sie erneut eine Verbindung mit Ihrer Adobe Target-Konfiguration her.
1. Wählen Sie im Dropdown-Menü **A4T-Analyse-Cloud-Konfiguration** das Framework aus.

   >[!NOTE]
   >
   >Es sind nur Analysekonfigurationen verfügbar, die für A4T aktiviert sind.
   >
   >Beim Konfigurieren von A4T mit AEM kann es vorkommen, dass der Eintrag „Konfigurationsverweis fehlt“ angezeigt wird. Gehen Sie wie folgt vor, um das Analyse-Framework auszuwählen:
   >
   >1. Navigate to **Tools** > **General** > **CRXDE Lite**.
   1. Navigate to **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   1. Set the property **disable** to **false**.
   1. Tippen oder klicken Sie auf **Alle speichern**.


   ![chlimage_1-159](assets/chlimage_1-159.png)

   Klicken Sie auf **OK**. Beim Verwenden von Adobe Target für Inhalte können Sie die [Quelle für die Berichterstellung auswählen](/help/sites-authoring/content-targeting-touch.md).

## Manuelles Integrieren mit Adobe Target {#manually-integrating-with-adobe-target}

Sie können das Integrieren mit Adobe Target auch manuell durchführen, anstatt den Opt-in-Assistenten zu verwenden.

>[!NOTE]
The Target Library file, [AT.JS](https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html), is a new implementation library for Adobe Target that is designed for both typical web implementations and single-page applications. Adobe empfiehlt, anstelle von „mbox.js“ die Datei „AT.js“ als Client-Bibliothek zu verwenden.
„AT.js“ bietet im Vergleich zur Bibliothek „mbox.js“ viele Verbesserungen, z. B.:
* Verbesserte Seitenladezeiten für Web-Implementierungen
* Verbesserte Sicherheit
* Bessere Implementierungsoptionen für Einzelseitenanwendungen
* „AT.js“ enthält die Komponenten, die in „target.js“ enthalten waren, sodass „target.js“ nicht mehr aufgerufen wird.

See [Target release notes](https://marketing.adobe.com/resources/help/en_US/target/rn/201604.html) for more information.
Sie können im Dropdown-Menü **Client-Bibliothek** die Datei „AT.js“ oder „mbox.js“ auswählen.

### Erstellen einer Target-Cloud-Konfiguration {#creating-a-target-cloud-configuration}

Erstellen Sie eine Target-Cloud-Konfiguration, um für AEM die Interaktion mit Adobe Target zu ermöglichen. Zum Erstellen der Konfiguration geben Sie den Adobe Target-Client-Code und die Benutzeranmeldeinformationen an.

Sie erstellen die Target-Cloud-Konfiguration nur einmal, da Sie die Konfiguration mehreren AEM-Kampagnen zuordnen können. Erstellen Sie eine Konfiguration für jeden Client-Code, falls Sie über mehrere Adobe Target-Client-Codes verfügen.

Sie können die Cloud-Konfiguration so konfigurieren, dass Segmente aus Adobe Target synchronisiert werden. Wenn Sie die Synchronisierung aktivieren, werden die Segmente im Hintergrund aus Target importiert, sobald die Cloud-Konfiguration gespeichert wurde.

Verwenden Sie das folgende Verfahren, um eine Target-Cloud-Konfiguration in AEM zu erstellen:

1. Navigate to **Cloud Services** via the **AEM logo** > **Tools** > **Deployment** > **Cloud Services**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   The **Adobe Marketing Cloud** overview page opens.

1. In the **Adobe Target** section, click **Configure Now**.
1. In the **Create Configuration** dialog:

   1. Give the configuration a **Title**.
   1. Select the **Adobe Target Configuration** template.
   1. Klicken Sie auf **Erstellen**.
   Das Dialogfeld „Bearbeiten“ wird geöffnet.

   ![chlimage_1-160](assets/chlimage_1-160.png)

   >[!NOTE]
   Beim Konfigurieren von A4T mit AEM kann es vorkommen, dass der Eintrag „Konfigurationsverweis fehlt“ angezeigt wird. Gehen Sie wie folgt vor, um das Analyse-Framework auszuwählen:
   1. Navigate to **Tools** > **General** > **CRXDE Lite**.
   1. Navigate to **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   1. Set the property **disable** to **false**.
   1. Tippen oder klicken Sie auf **Alle speichern**.


1. Geben Sie im Dialogfeld Werte für diese Eigenschaften an.

   * **Client-Code**: Der Client-Code des Target-Kontos.
   * **E-Mail**: Die E-Mail-Adresse des Target-Kontos.
   * **Kennwort**: Das Kennwort des Target-Kontos.
   * **API-Typ**: Entweder „REST“ oder „XML“.
   * **A4T-Analyse-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für die Berichterstellung für bestimmte Inhalte verwenden. If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](#configuring-a-t-analytics-cloud-configuration).

   * **** Verwenden Sie genaues Targeting: Standardmäßig ist dieses Kontrollkästchen aktiviert. Bei Aktivierung dieser Option wird für die Cloud Service-Konfiguration gewartet, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Siehe Hinweis unten.
   * **** Segmente aus Adobe Target synchronisieren: Wählen Sie diese Option, um Segmente herunterzuladen, die in Target definiert sind, um sie in AEM zu verwenden. Sie müssen diese Option auswählen, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Beachten Sie, dass der AEM-Begriff „Segment“ hier dem Target-Begriff „Zielgruppe“ entspricht.)
   * **** Client-Bibliothek: Wählen Sie aus, ob die Client-Bibliothek &quot;mbox.js&quot;oder &quot;AT.js&quot;verwendet werden soll.
   * **Verwenden Sie DTM zur Bereitstellung der Client-Bibliothek** - Wählen Sie diese Option, um entweder AT.js oder mbox.js aus DTM oder einem anderen Tag-Management-System zu verwenden. You must [configure the DTM integration](/help/sites-administering/dtm.md) to use this option. Adobe empfiehlt zum Bereitstellen der Bibliothek die Verwendung von DTM anstelle von AEM.
   * **Benutzerdefinierte mbox.js**: Lassen Sie dieses Feld leer, wenn Sie das Feld „DTM“ aktiviert haben oder die standardmäßige Datei „mbox.js“ verwenden möchten. Alternativ hierzu können Sie Ihre benutzerdefinierte Datei „mbox.js“ hochladen. Sie wird nur angezeigt, wenn Sie „mbox.js“ ausgewählt haben.
   * **Benutzerdefiniertes AT.js**: Lassen Sie dieses Feld leer, wenn Sie das Feld „DTM“ aktiviert haben oder die standardmäßige Datei „AT.js“ verwenden möchten. Alternativ hierzu können Sie Ihre benutzerdefinierte Datei „AT.js“ hochladen. Sie wird nur angezeigt, wenn Sie „AT.js“ ausgewählt haben.
   >[!NOTE]
   Wenn Sie den Opt-in für den Adobe Target-Konfigurationsassistenten durchführen, wird die „präzise Zielgruppenerfassung“ aktiviert.
   Präzise Zielgruppenerfassung bedeutet, dass für die Cloud Service-Konfiguration gewartet wird, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Daher kann es in Bezug auf die Leistung bei der präzisen Zielgruppenerfassung zu einer Verzögerung von einigen Millisekunden kommen, bevor das Laden des Inhalts erfolgt.
   Die präzise Zielgruppenerfassung ist auf der Autoreninstanz immer aktiviert. Auf der Veröffentlichungsinstanz können Sie die präzise Zielgruppenerfassung aber global deaktivieren, indem Sie in der Cloud Service-Konfiguration das Häkchen neben „Präzise Zielgruppenerfassung“ entfernen (**http://localhost:4502/etc/cloudservices.html**). Außerdem können Sie die präzise Zielgruppenerfassung unabhängig von Ihrer Einstellung in der Cloud Service-Konfiguration auch für einzelne Komponenten ein- oder ausschalten.
   Wenn Sie Komponenten als Ziel ***bereits*** angegeben haben und diese Einstellung dann ändern, wirken sich Ihre Änderungen nicht auf diese Komponenten aus. Sie müssen alle Änderungen an dieser Komponente direkt vornehmen.

1. Klicken Sie auf **Mit Target verbinden**, um die Verbindung mit Target zu initialisieren. If the connection is successful, the message **Connection successful** is displayed. Klicken Sie auf **OK** und dann auf **OK.**

   Falls Sie keine Verbindung mit Target herstellen können, helfen Ihnen die Informationen im Abschnitt zur [Fehlerbehebung](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) weiter.

### Hinzufügen eines Target-Frameworks {#adding-a-target-framework}

Nachdem Sie die Target-Cloud-Konfiguration konfiguriert haben, können Sie ein Target-Framework hinzufügen. Das Framework identifiziert die Standardparameter, die von den verfügbaren [ClientContext](/help/sites-administering/client-context.md)- oder [ContextHub](/help/sites-administering/contexthub-config.md)-Komponenten an Adobe Target gesendet werden. Target nutzt die Parameter, um die Segmente zu ermitteln, die für den aktuellen Kontext gelten.

Sie können für eine Target-Konfiguration mehrere Frameworks erstellen. Mehrere Frameworks sind nützlich, wenn Sie für unterschiedliche Abschnitte Ihrer Website jeweils einen anderen Parametersatz an Target senden müssen. Erstellen Sie ein Framework für jeden Parametersatz, der gesendet werden muss. Ordnen Sie die einzelnen Abschnitte Ihrer Website jeweils dem passenden Framework zu. Beachten Sie, dass für eine Webseite nur jeweils ein Framework verwendet werden kann.

1. On your Target configuration page, click the **+** (plus sign) next to Available Frameworks.
1. In the Create Framework dialog, specify a **Title**, select the **Adobe Target Framework**, and click **Create**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

   Die Framework-Seite wird geöffnet. Sidekick provides components that represent information from the [Client Context](/help/sites-administering/client-context.md) or [ContextHub](/help/sites-administering/contexthub-config.md) that you can map.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Ziehen Sie die ClientContext-Komponente mit den Daten, die Sie für die Zuordnung nutzen möchten, auf das Ablageziel. Alternativ hierzu können Sie die **ContextHub-Store**-Komponente auf das Framework ziehen.

   >[!NOTE]
   Bei der Zuordnung werden Parameter über einfache Zeichenfolgen an mbox übergeben. Es ist nicht möglich, Arrays aus ContextHub zuzuordnen.

   For example, to use **Profile Data** about your site vistors to control your Target campaign, drag the **Profile Data** component to the page. Es werden die Profildatenvariablen angezeigt, die für die Zuordnung zu Target-Parametern verfügbar sind.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Wählen Sie die Variablen aus, die für das Adobe Target-System sichtbar sein sollen, indem Sie das Kontrollkästchen **Freigeben** in den entsprechenden Spalten auswählen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

   >[!NOTE]
   Parameter können nur in einer Richtung synchronisiert werden: von AEM nach Adobe Target.

Ihr Framework wird erstellt. Verwenden Sie die Sidekick-Option **Framework aktivieren**, um das Framework auf der Veröffentlichungsinstanz zu replizieren.

### Zuordnen von Aktivitäten zur Target-Cloud-Konfiguration  {#associating-activities-with-the-target-cloud-configuration}

Associate your [AEM activities](/help/sites-authoring/activitylib.md) with your Target cloud configuration so that you can mirror the activities in [Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/target/c_manage_content.html).

>[!NOTE]
Welche Aktivitätstypen zur Verfügung stehen, hängt von folgenden Faktoren ab:
* Bei Aktivierung der Option **xt_only** im Adobe Target-Mandanten (Client-Code), der auf AEM-Seite für die Verbindung zu Adobe Target verwendet wird, können Sie in AEM ausschließlich **XT-Aktivitäten** erstellen.

* Ist die Option **xt_only** **nicht** im Adobe Target-Mandanten (Client-Code) aktiviert, können Sie in AEM **sowohl** XT- als auch A/B-Aktivitäten erstellen.

**Zusätzlicher Hinweis:** Bei der Option **xt_only** handelt es sich um eine Einstellung, die auf einen bestimmten Target-Mandanten (Clientcode) angewendet wird und nur in Adobe Target bearbeitet werden kann. Die Option kann nicht in AEM aktiviert oder deaktiviert werden.

### Zuordnen des Target-Frameworks zu Ihrer Website {#associating-the-target-framework-with-your-site}

Nachdem Sie in AEM ein Target-Framework erstellt haben, können Sie dem Framework Ihre Webseiten zuordnen. Die als Ziel angegebenen Komponenten auf den Seiten senden die per Framework definierten Daten zu Tracking-Zwecken an Adobe Target. (Siehe [Content-Targeting](/help/sites-authoring/content-targeting-touch.md).)

Wenn Sie dem Framework eine Seite zuordnen, erben die untergeordneten Seiten die Zuordnung.

1. In the **Sites** console, navigate to the site that you want to configure.
1. Using either [quick actions](/help/sites-authoring/basic-handling.md#quick-actions) or [selection mode](/help/sites-authoring/basic-handling.md), select **View Properties.**
1. Wählen Sie die Registerkarte **Cloud-Services** aus.
1. Klicken oder tippen Sie auf **Bearbeiten**.
1. Klicken oder tippen Sie unter **Cloud Service-Konfigurationen** auf **Konfiguration hinzufügen** und wählen Sie **Adobe Target** aus.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Wählen Sie das gewünschten Framework unter **Konfigurationsverweis** aus.

   >[!NOTE]
   Achten Sie darauf, dass Sie das von Ihnen erstellte **Framework** und nicht die Target-Cloud-Konfiguration auswählen, unter der die Erstellung durchgeführt wurde.

1. Klicken oder tippen Sie auf **Fertig**.
1. Aktivieren Sie die Stammseite der Website, um sie auf dem Veröffentlichungsserver zu replizieren. (Siehe [Veröffentlichen von Seiten](/help/sites-authoring/publishing-pages.md).)

   >[!NOTE]
   Falls das Framework, das Sie an die Seite angefügt haben, noch nicht aktiviert war, wird ein Assistent geöffnet, mit dem Sie hierfür die Veröffentlichung durchführen können.

## Durchführen der Fehlerbehebung für Target-Verbindungsprobleme {#troubleshooting-target-connection-problems}

Führen Sie die folgenden Aufgaben aus, um Probleme zu behandeln, die bei der Verbindungsherstellung mit Target auftreten:

* Stellen Sie sicher, dass die von Ihnen angegebenen Benutzeranmeldeinformationen korrekt sind.
* Vergewissern Sie sich, dass die AEM-Instanz eine Verbindung mit dem Target-Server herstellen kann. Achten Sie beispielsweise darauf, dass Firewallregeln nicht zu einer Blockierung von ausgehenden AEM-Verbindungen führen oder dass AEM für die Verwendung erforderlicher Proxys konfiguriert ist.
* Suchen Sie im AEM-Fehlerprotokoll nach hilfreichen Meldungen. Die Datei „error.log“ ist im Verzeichnis **crx-quickstart/logs** enthalten, in dem AEM installiert ist.
* Beim Bearbeiten der Aktivität in Adobe Target zeigt die URL auf „localhost“. Umgehen Sie dies, indem Sie den AEM-Externalizer auf die richtige URL festlegen.

