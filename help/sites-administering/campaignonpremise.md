---
title: Integration mit Adobe Campaign Classic
seo-title: Integrating with Adobe Campaign Classic
description: Erfahren Sie, wie Sie AEM mit Adobe Campaign Classic integrieren
seo-description: Learn how to integrate AEM with Adobe Campaign Classic
uuid: 3c998b0e-a885-4aa9-b2a4-81b86f9327d3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: df94dd1b-1b65-478b-a28d-81807a8084b1
exl-id: a7281ca0-461f-4762-a631-6bb539596200
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2256'
ht-degree: 68%

---

# Integration mit Adobe Campaign Classic{#integrating-with-adobe-campaign-classic}

>[!NOTE]
>
>Diese Dokumentation beschreibt die Integration von AEM mit der On-Premise-Lösung Adobe Campaign Classic. Wenn Sie Adobe Campaign Standard verwenden, lesen Sie sich für diese Anweisungen das Dokument [Integration mit Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) durch.

Adobe Campaign ermöglicht die Verwaltung von Inhalten und Formularen für die Übermittlung per E-Mail direkt in Adobe Experience Manager.

Um beide Lösungen gleichzeitig nutzen zu können, müssen Sie sie zunächst so konfigurieren, dass sie miteinander verbunden sind. Dies umfasst Konfigurationsschritte in Adobe Campaign und Adobe Experience Manager. Diese Schritte werden in diesem Dokument detailliert beschrieben.

Das Arbeiten mit Adobe Campaign in AEM bietet die Möglichkeit, E-Mails über Adobe Campaign zu versenden, und wird näher im Abschnitt [Arbeiten mit Adobe Campaign](/help/sites-authoring/campaign.md) beschrieben. Dies bezieht sich auch auf die Verwendung von Formularen auf AEM-Seiten, um so Daten zu bearbeiten.

Des Weiteren sind unter Umständen die folgenden Themen relevant, wenn Sie AEM mit [Adobe Campaign](https://helpx.adobe.com/support/campaign/classic.html) integrieren:

* [Best Practices für E-Mail-Vorlagen](/help/sites-administering/best-practices-for-email-templates.md)
* [Fehlerbehebung bei der Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md)

Hinsichtlich der Erweiterung einer Adobe Campaign-Integration sind folgende Seiten empfehlenswert:

* [Erstellen benutzerspezifischer Erweiterungen](/help/sites-developing/extending-campaign-extensions.md)
* [Erstellen benutzerdefinierter Formularzuordnungen](/help/sites-developing/extending-campaign-form-mapping.md)

## Workflow für die Integration von AEM und Adobe Campaign {#aem-and-adobe-campaign-integration-workflow}

Dieser Abschnitt beschreibt einen typischen Workflow zwischen AEM und Adobe Campaign beim Erstellen von Kampagnen und dem Bereitstellen von Inhalten.

Der typische Workflow umfasst Folgendes und ist hier näher beschrieben:

1. Beginnen Sie mit dem Erstellen der Kampagne (sowohl in Adobe Campaign als auch in AEM).
1. Bevor Sie die Inhalte und die Bereitstellung verknüpfen, personalisieren Sie die Inhalte in AEM und erstellen Sie eine Bereitstellung in Adobe Campaign.
1. Verknüpfen Sie die Inhalte und die Bereitstellung in Adobe Campaign.

### Beginnen Sie mit dem Erstellen der Kampagne {#start-building-your-campaign}

Sie können jederzeit mit dem Erstellen einer Kampagne beginnen. Bevor Sie den Inhalt verknüpfen, sollten Sie wissen, dass AEM und AC unabhängig sind. Dies bedeutet, dass Vermarkter mit dem Erstellen ihrer Kampagnen und dem Targeting in Adobe Campaign beginnen können, während die Ersteller von Inhalten in AEM am Design arbeiten.

### Vor dem Verknüpfen von Inhalten und der Bereitstellung {#before-linking-content-and-delivery}

Bevor Sie die Inhalte verknüpfen und einen Bereitstellungsmechanismus erstellen, müssen Sie folgende Schritte ausführen:

**In AEM**

* Personalisieren Sie mithilfe der Personalisierungsfelder in der Komponente **Text &amp; Personalisierung**.

**In Adobe Campaign **

* Erstellen Sie eine Bereitstellung vom Typ **aemContent**.

### Verknüpfen von Inhalten und Einstellungsbereitstellung {#linking-content-and-setting-delivery}

Nachdem Sie den Inhalt für die Verknüpfung und Bereitstellung vorbereitet haben, legen Sie genau fest, wie und wo die Inhalte verknüpft werden sollen.

All diese Schritte werden in Adobe Campaign ausgeführt.

1. Legen Sie fest, welche AEM-Instanz verwendet werden soll.
1. Synchronisieren Sie die Inhalte durch Klicken auf die Schaltfläche „Synchronisieren“.
1. Öffnen Sie die Inhaltsauswahl zur Auswahl des Inhalts.

### Wenn Sie zum ersten Mal mit AEM arbeiten {#if-you-are-new-to-aem}

Wenn Sie zum ersten Mal mit AEM arbeiten, finden Sie die folgenden Links möglicherweise für das Verständnis von AEM hilfreich:

* [Starten von AEM](/help/sites-deploying/deploy.md)
* [Verstehen von Replikations-Agenten](/help/sites-deploying/replication.md)
* [Suchen von und Arbeiten mit Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)

## Konfigurieren von Adobe Campaign {#configuring-adobe-campaign}

Die Konfiguration von Adobe Campaign umfasst Folgendes:

1. Installieren des AEM-Integrationspakets in Adobe Campaign
1. Konfigurieren eines externen Kontos
1. Sicherstellen, dass der AEMResourceTypeFilter korrekt konfiguriert ist

Darüber hinaus gibt es erweiterte Konfigurationen, die Sie definieren können, z. B.:

* Verwalten von Inhaltsblöcken
* Verwalten von Personalisierungsfeldern

Siehe [Erweiterte Konfigurationen](#advanced-configurations).

>[!NOTE]
>
>Um diese Vorgänge auszuführen, müssen Sie über die **Administration** Rolle in Adobe Campaign.

### Voraussetzungen {#prerequisites}

Stellen Sie im Voraus sicher, dass Sie über die folgenden Elemente verfügen:

* [Eine AEM-Autoreninstanz](/help/sites-deploying/deploy.md#getting-started)
* [Eine AEM-Veröffentlichungsinstanz](/help/sites-deploying/deploy.md#author-and-publish-installs)
* [Eine Adobe Campaign Classic-Instanz](https://helpx.adobe.com/support/campaign/classic.html) - einschließlich eines Clients und eines Servers
* Internet Explorer 11

>[!NOTE]
>
>Wenn Sie eine frühere Version als Adobe Campaign Classic Build 8640 ausführen, finden Sie weitere Informationen unter [Upgrade-Dokumentation](https://docs.campaign.adobe.com/doc/AC6.1/de/PRO_Updating_Adobe_Campaign_Upgrading.html) für weitere Informationen. Beachten Sie, dass der Client und die Datenbank auf denselben Build aktualisiert werden müssen.

>[!CAUTION]
>
>Die im Abschnitt [Konfigurieren von Adobe Campaign](#configuring-adobe-campaign) und [Konfigurieren von Adobe Experience Manager](#configuring-adobe-experience-manager) -Abschnitte sind erforderlich, damit die Integrationsfunktionen zwischen AEM und Adobe Campaign ordnungsgemäß funktionieren.

### Installieren von AEM-Integrationspaketen {#installing-the-aem-integration-package}

Sie müssen die **AEM** -Paket in Adobe Campaign. Gehen Sie hierfür wie folgt vor:

1. Wechseln Sie zu der Adobe Campaign-Instanz, die Sie gern mit AEM verknüpfen möchten.
1. Auswählen *Instrumente* > *Erweitert* > *Package importieren..*.

   ![chlimage_1-132](assets/chlimage_1-132a.png)

1. Klicken **Standardpaket installieren** und wählen Sie dann die **AEM** Paket.

   ![chlimage_1-133](assets/chlimage_1-133a.png)

1. Klicken **Nächste**, und dann **Starten**.

   Dieses Paket enthält die **aemserver** -Operator, der verwendet wird, um den AEM-Server mit Adobe Campaign zu verbinden.

   >[!CAUTION]
   >
   >Standardmäßig ist für diesen Operator keine Sicherheitszone konfiguriert. Um die Verknüpfung über AEM mit Adobe Campaign herzustellen, müssen Sie eine Option auswählen.
   >
   >Im **serverConf.xml** -Datei, die **allowUserPassword** -Attribut der ausgewählten Sicherheitszone muss auf **true** , um AEM zu autorisieren, Adobe Campaign über Login/Passwort zu verbinden.
   >
   >Wir empfehlen Ihnen dringend, eine speziell AEM zugewiesene Sicherheitszone zu erstellen, um jegliche Sicherheitsprobleme zu vermeiden. Weitere Informationen hierzu finden Sie im Abschnitt [Installationshandbuch](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html).

   ![chlimage_1-134](assets/chlimage_1-134a.png)

### Konfigurieren von externen AEM-Konten {#configuring-an-aem-external-account}

Sie müssen ein externes Konto konfigurieren, das es Ihnen ermöglicht, Adobe Campaign mit Ihrer AEM-Instanz zu verknüpfen.

>[!NOTE]
>
>* Bei der Installation der **AEM** -Paket, wird ein externes AEM erstellt. Von diesem Konto aus können Sie die Verbindung mit der AEM-Instanz konfigurieren oder Sie können eine neue anlegen.
>* Stellen Sie in AEM sicher, dass Sie das Kennwort für den Benutzer „campaign-remote“ festlegen. Sie müssen dieses Kennwort festlegen, um Adobe Campaign mit AEM zu verknüpfen. Melden Sie sich als Administrator an und wählen Sie an der Benutzeradministrationskonsole den Benutzer „campaign-remote“. Klicken Sie dann auf **Kennwort festlegen**.
>


So konfigurieren Sie externe AEM-Konten:

1. Navigieren Sie zu **Administration** > **Plattform** > **Externe Konten** Knoten.
1. Erstellen Sie ein neues externes Konto und wählen Sie die **AEM** Typ.
1. Geben Sie die Zugangsparameter für die AEM-Autoreninstanz ein: die Serveradresse sowie die ID und das Kennwort für die Verbindung mit dieser Instanz. Das Kennwort für das Benutzerkonto „campaign-api“ ist dasselbe wie für den Benutzer „campaign-remote“, für den Sie in AEM ein Kennwort festgelegt haben.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass die Serveradresse **nicht** in einem Schrägstrich endet. Geben Sie beispielsweise `https://yourserver:4502` anstelle von `https://yourserver:4502/`

   ![chlimage_1-135](assets/chlimage_1-135a.png) ![chlimage_1-136](assets/chlimage_1-136a.png)

1. Stellen Sie sicher, dass die Variable **Aktiviert** aktiviert ist.

### Überprüfen der Option „AEMResourceTypeFilter“ {#verifying-the-aemresourcetypefilter-option}

Die **AEMResourceTypeFilter** wird verwendet, um AEM Ressourcentypen zu filtern, die in Adobe Campaign verwendet werden können. Dies ermöglicht Adobe Campaign das Abrufen von AEM-Inhalten, die speziell für die ausschließliche Verwendung in Adobe Campaign entwickelt wurden.

Diese Option sollte vorkonfiguriert sein. Wenn Sie diese Option jedoch ändern, kann es sein, dass die Integration am Ende nicht funktioniert.

Überprüfen Sie wie folgt, ob die Option **AEMResourceTypeFilter** konfiguriert ist:

1. Navigieren Sie zu **Plattform** > **Optionen**.
1. Im **AEMResourceTypeFilter** aktivieren, überprüfen Sie, ob die Pfade korrekt sind. Dieses Feld muss den Wert enthalten:

   **mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter**

   In einigen Fällen ist der Wert wie folgt:

   **mcm/campaign/components/newsletter**

   ![chlimage_1-137](assets/chlimage_1-137a.png)

## Konfigurieren von Adobe Experience Manager {#configuring-adobe-experience-manager}

Zum Konfigurieren von AEM müssen Sie folgende Schritte ausführen:

* Konfigurieren Sie die Replikation zwischen Instanzen.
* Verbinden Sie AEM über Cloud-Services mit Adobe Campaign.
* Konfigurieren Sie den Externalizer.

### Konfigurieren der Replikation zwischen AEM-Instanzen {#configuring-replication-between-aem-instances}

Inhalte, die in der AEM-Autoreninstanz erstellt werden, werden zunächst zur Veröffentlichungsinstanz gesendet. Sie müssen so veröffentlichen, dass die Bilder im Newsletter auf der Veröffentlichungsinstanz und für Newsletter-Empfänger verfügbar sind. Der Replikationsagent muss deshalb so konfiguriert werden, dass er aus der AEM-Autoreninstanz in die AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Wenn Sie nicht die Replikations-URL, sondern stattdessen die öffentlich zugängliche URL verwenden möchten, können Sie die **Öffentliche URL** in der folgenden Konfigurationseinstellung im OSGi (**AEM** >  **Instrumente** Symbol >  **Aktivitäten** > **Web-Konsole** > **OSGi-Konfiguration** > **AEM Campaign-Integration - Konfiguration**):
**Öffentliche URL:** com.day.cq.mcm.campaign.impl.IntegrationConfigImpl#aem.mcm.campaign.publicUrl

Dieser Schritt ist auch erforderlich, um bestimmte Autoreninstanzkonfigurationen in die Veröffentlichungsinstanz zu replizieren.

So konfigurieren Sie die Replikation zwischen AEM-Instanzen:

1. Wählen Sie in der Authoring-Instanz **AEM**> **Instrumente** Symbol > **Implementierung** > **Replikation** > **Agenten für Autor** Klicken Sie auf **Standardagent**.

   ![chlimage_1-138](assets/chlimage_1-138a.png)

   >[!NOTE]
   Verwenden Sie nach Möglichkeit nicht localhost (eine lokale Kopie von AEM), wenn Sie die Integration mit Adobe Campaign konfigurieren, außer die Veröffentlichungs- und Autoreninstanz befinden sich auf demselben Computer.

1. Tippen oder klicken Sie auf **Bearbeiten** und wählen Sie dann **Verkehr** Registerkarte.
1. Konfigurieren Sie den URI, indem Sie **localhost** durch die IP-Adresse oder die Adresse der AEM-Veröffentlichungsinstanz ersetzen.

   ![chlimage_1-139](assets/chlimage_1-139a.png)

### Verknüpfen von AEM mit Adobe Campaign {#connecting-aem-to-adobe-campaign}

Bevor Sie AEM und Adobe Campaign zusammen verwenden können, müssen Sie die beiden Lösungen verknüpfen, damit sie miteinander kommunizieren können.

1. Stellen Sie eine Verbindung mit Ihrer AEM-Autoreninstanz her.
1. Auswählen **AEM** > **Instrumente** Symbol > **Implementierung** > **Cloud Services**, dann **Jetzt konfigurieren** im Abschnitt &quot;Adobe Campaign&quot;.

   ![chlimage_1-140](assets/chlimage_1-140a.png)

1. Erstellen Sie eine neue Konfiguration durch Eingabe einer **Titel** und klicken Sie auf **Erstellen** oder wählen Sie die vorhandene Konfiguration aus, die Sie mit Ihrer Adobe Campaign-Instanz verknüpfen möchten.
1. Passen Sie die Konfiguration so an, dass sie den Parametern Ihrer Adobe Campaign-Instanz entspricht.

   * **Benutzername**: **aemserver**, der für die Herstellung der Verbindung zwischen den beiden Lösungen verwendete Adobe Campaign AEM Integrationspaket-Operator.
   * **Kennwort**: Das Adobe Campaign-Kennwort des aemserver-Operators. Unter Umständen müssen Sie das Kennwort für diesen Operator direkt in Adobe Campaign erneut angeben.
   * **API-Endpunkt**: URL der Adobe Campaign-Instanz.

1. Auswählen **Verbindung zu Adobe Campaign herstellen** und klicken Sie auf **OK**.

   ![chlimage_1-141](assets/chlimage_1-141a.png)

   >[!NOTE]
   Nachdem Sie [die E-Mail erstellt und veröffentlicht haben](/help/sites-authoring/campaign.md), müssen Sie die Konfiguration auf der Veröffentlichungsinstanz erneut veröffentlichen.

   ![chlimage_1-142](assets/chlimage_1-142a.png)

>[!NOTE]
Prüfen Sie Folgendes, falls die Verbindung nicht hergestellt werden kann:
* Möglicherweise tritt ein Zertifikatfehler auf, wenn Sie eine sichere Verbindung (https) mit einer Adobe Campaign-Instanz herstellen. Sie müssen das Adobe Campaign-Instanzzertifikat zum **cacerts** -Datei des JDK Ihrer AEM-Instanz.
* Für den [aemserver-Operator](#connecting-aem-to-adobe-campaign) muss eine Sicherheitszone in Adobe Campaign konfiguriert werden. Darüber hinaus wird im **serverConf.xml** -Datei, die **allowUserPassword** -Attribut der Sicherheitszone muss auf **true** , um AEM Verbindung mit Adobe Campaign mithilfe des Anmelde-/Kennwortmodus zu autorisieren.
>
Weitere Informationen finden Sie in [Fehlerbehebung bei der AEM/Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md).

### Konfigurieren des Externalizers {#configuring-the-externalizer}

Sie müssen [den Externalizer](/help/sites-developing/externalizer.md) in AEM auf der Autoreninstanz konfigurieren. Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade in externe, absolute URLs umzuwandeln. Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs.

Allgemeine Anweisungen finden Sie unter [Konfigurieren des Externalizers](/help/sites-developing/externalizer.md). Stellen Sie für die Adobe Campaign-Integration sicher, dass Sie den Veröffentlichungsserver unter `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`nicht auf `localhost:4503` aber auf einen Server, der über die Adobe Campaign-Konsole erreichbar ist.

Wenn er auf `localhost:4503` oder einen anderen Server, den Adobe Campaign nicht erreichen kann, verweist, werden Ihre Bilder auf der Adobe Campaign-Konsole nicht angezeigt.

![chlimage_1-143](assets/chlimage_1-143a.png)

## Erweiterte Konfigurationen {#advanced-configurations}

Sie können zudem einige erweiterte Konfigurationen vornehmen, wie:

* Das Verwalten von Personalisierungsfeldern und -blöcken.
* Das Deaktivieren eines Personalisierungsblocks.
* Das Verwalten von Zielerweiterungsdaten.

### Verwalten von Personalisierungsfeldern und -blöcken {#managing-personalization-fields-and-blocks}

Die zum Hinzufügen einer Personalisierung zu Ihrem E-Mail-Inhalt in AEM verfügbaren Felder und Blöcke werden von Adobe Campaign verwaltet.

Eine Standardliste wird bereitgestellt, kann jedoch geändert werden. Sie können Personalisierungsfelder und -blöcke auch hinzufügen oder ausblenden.

#### Hinzufügen eines Personalisierungsfelds {#adding-a-personalization-field}

Um ein neues Personalisierungsfeld zu den bereits verfügbaren Personalisierungsfeldern hinzuzufügen, müssen Sie Adobe Campaign erweitern **nms:seedMember** Schema wie folgt:

>[!CAUTION]
Das Feld, das Sie hinzufügen müssen, muss bereits über eine Empfängerschemaerweiterung hinzugefügt worden sein (**nms:recipient**). Weitere Informationen finden Sie unter [Konfiguration](https://docs.campaign.adobe.com/doc/AC6.1/de/CFG_Editing_schemas_Editing_schemas.html) Handbuch.

1. Navigieren Sie zu **Administration** > **Konfiguration** > **Datenschemata** -Knoten in der Adobe Campaign-Navigation.
1. Auswählen **Neu**.

   ![chlimage_1-144](assets/chlimage_1-144a.png)

1. Wählen Sie im Popup-Fenster **Daten in der Tabelle mithilfe eines Erweiterungsschemas erweitern** und klicken Sie auf **Nächste**.

   ![chlimage_1-145](assets/chlimage_1-145a.png)

1. Geben Sie die verschiedenen Parameter des erweiterten Schemas ein:

   * **Schema**: wählen Sie die **nms:seedMember** Schema. Die anderen Felder im Fenster werden automatisch ausgefüllt.
   * **Namespace**: Personalisieren Sie den Namespace des erweiterten Schemas.

1. Bearbeiten Sie den XML-Code des Schemas, um das Feld anzugeben, das Sie dort hinzufügen möchten. Weitere Informationen zum Erweitern von Schemata in Adobe Campaign finden Sie im Abschnitt [Konfigurationshandbuch](https://docs.campaign.adobe.com/doc/AC6.1/de/CFG_Editing_schemas_Extending_a_schema.html).
1. Speichern Sie Ihr Schema und aktualisieren Sie dann die Adobe Campaign-Datenbankstruktur über die **Instrumente** > **Erweitert** > **Datenbankstruktur aktualisieren** in der Konsole.
1. Trennen Sie die Verbindung zur Adobe Campaign-Konsole und stellen Sie die Verbindung wieder her, um die Änderungen zu speichern. Das neue Feld wird nun in der Liste der in AEM verfügbaren Personalisierungsfelder angezeigt.

#### Beispiel {#example}

So fügen Sie eine **Registrierungsnummer** -Feld müssen die folgenden Elemente vorhanden sein:

* Die **nms:recipient** Schemaerweiterung **cus:recipient** enthält:

```xml
<element desc="Recipient table (profiles)" img="nms:recipient.png" label="Recipients" labelSingular="Recipient" name="recipient">

  <attribute dataPolicy="smartCase" desc="Recipient registration number"
  label="Registration Number"
  length="50" name="registrationNumber" type="string"/>

</element>
```

Die **nms:seedMember** Schemaerweiterung **cus:seedMember** enthält:

```xml
<element desc="Seed to insert in the export files" img="nms:unknownad.png" label="Seed addresses" labelSingular="Seed" name="seedMember">

  <element name="custom_nms_recipient">
    <attribute name="registrationNumber"
    template="cus:recipient:recipient/@registrationNumber"/>
  </element>

</element>
```

Die **Registrierungsnummer** -Feld ist jetzt Teil der verfügbaren Personalisierungsfelder:

![chlimage_1-146](assets/chlimage_1-146.png)

#### Ausblenden eines Personalisierungsfelds  {#hiding-a-personalization-field}

Um ein Personalisierungsfeld unter den bereits verfügbaren Personalisierungsfeldern auszublenden, müssen Sie die Adobe Campaign erweitern **nms:seedMember** Schema wie im Abschnitt [Personalisierungsfeld hinzufügen](#adding-a-personalization-field) Abschnitt. Führen Sie die folgenden Schritte aus:

1. Kopieren Sie das Feld, das Sie aus dem Schema **nms:seedMember** in das erweiterte Schema (beispielsweise **cus:seedMember**) übernehmen möchten.
1. Fügen Sie die **advanced=&quot;true&quot;** XML-Attribut auf das Feld. Es wird nicht mehr in der Liste der in AEM verfügbaren Personalisierungsfelder angezeigt.

   Um beispielsweise die **Middle name** -Feld, die **cud:seedMember** schema muss das folgende Element enthalten:

   ```xml
   <element desc="Seed to insert in the export files" img="nms:unknownad.png" label="Seed addresses" labelSingular="Seed" name="seedMember">
   
     <element name="custom_nms_recipient">
       <attribute advanced="true" name="middleName"/>
     </element>
   
   </element>
   ```

### Deaktivieren eines Personalisierungsblocks {#deactivating-a-personalization-block}

So deaktivieren Sie einen Personalisierungsblock unter den vorhandenen Personalisierungsblöcken:

1. Navigieren Sie zu **Ressourcen** > **Campaign Management** > **Gestaltungsbausteine** -Knoten in der Adobe Campaign-Navigation.
1. Wählen Sie den Personalisierungsblock aus, den Sie in AEM deaktivieren möchten.
1. Löschen Sie die **In den Personalisierungsmenüs sichtbar** und speichern Sie Ihre Änderungen. Der Block wird nicht mehr in der Liste der Personalisierungsblöcke, die in Adobe Campaign verfügbar sind, angezeigt.

   ![chlimage_1-147](assets/chlimage_1-147a.png)

### Verwalten von Zielerweiterungsdaten {#managing-target-extension-data}

Sie können zudem Zielerweiterungsdaten für die Personalisierung eingeben. Zielerweiterungsdaten (auch als „Zieldaten“ bezeichnet) stammen aus dem Erweitern oder Hinzufügen von Daten, beispielsweise bei einer Abfrage in einem Kampagnen-Workflow. Weitere Informationen finden Sie im Abschnitt [Abfragen erstellen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_About_queries_in_Campaign.html) und [Daten anreichern](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Enriching_data.html) Abschnitte.

>[!NOTE]
Die Zieldaten sind nur verfügbar, wenn die AEM-Inhalte mit einer Adobe Campaign-Bereitstellung synchronisiert sind. Siehe [Synchronisieren von in AEM erstellten Inhalten mit einem Versand von Adobe Campaign](/help/sites-authoring/campaign.md#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic).

![chlimage_1-148](assets/chlimage_1-148a.png)
