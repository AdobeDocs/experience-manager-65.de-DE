---
title: Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks
seo-title: Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks
description: Erfahren Sie mehr dazu, wie AEM mit SiteCatalyst verbunden wird und wie Frameworks erstellt werden.
seo-description: Erfahren Sie mehr dazu, wie AEM mit SiteCatalyst verbunden wird und wie Frameworks erstellt werden.
uuid: 3820dd24-4193-42ea-aef2-4669ebfeaa9d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6b545a51-3677-4ea1-ac7e-2d01ba19283e
docset: aem65
translation-type: tm+mt
source-git-commit: 4b965d8f7814816126601f6366c1ba313e404538

---


# Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks {#connecting-to-adobe-analytics-and-creating-frameworks}

Um Webdaten von Ihren AEM-Seiten in Adobe Analytics zu verfolgen, erstellen Sie eine Adobe Analytics Cloud Services-Konfiguration und ein Adobe Analytics-Framework:

* **** Adobe Analytics-Konfiguration: Informationen zu Ihrem Adobe Analytics-Konto. Mit der Adobe Analytics-Konfiguration kann AEM eine Verbindung zu Adobe Analytics herstellen. Erstellen Sie eine Adobe Analytics-Konfiguration für jedes Konto, das Sie verwenden.
* **** Adobe Analytics Framework: Eine Gruppe von Zuordnungen zwischen Adobe Analytics Report Suite-Eigenschaften und CQ-Variablen. Verwenden Sie ein Framework, um zu konfigurieren, wie Ihre Websitedaten Ihre Adobe Analytics-Berichte auffüllen. Frameworks sind mit einer Adobe Analytics-Konfiguration verknüpft. Sie können mehrere Frameworks für jede Konfiguration erstellen.

Wenn Sie eine Webseite mit einem Framework verknüpfen, führt das Framework eine Verfolgung für diese Seite und die untergeordneten Elemente dieser Seite durch. Seitenansichten können dann von Adobe Analytics abgerufen und in der Sites-Konsole angezeigt werden.

## Voraussetzungen {#prerequisites}

### Adobe Analytics-Konto {#adobe-analytics-account}

Zur Verfolgung von AEM-Daten in Adobe Analytics benötigen Sie ein gültiges Adobe Marketing Cloud Adobe Analytics-Konto.

Das Adobe Analytics-Konto muss:

* Über **Administratorrechte** verfügen
* Der Benutzergruppe **Webdienstzugriff** zugeordnet sein

>[!CAUTION]
>
>Die Bereitstellung von **Administratorrechten** (innerhalb von Adobe Analytics) reicht nicht aus, um einem Benutzer die Verbindung von AEM zu Adobe Analytics zu ermöglichen. Das Konto muss auch über **Webdienstzugriffsrechte** verfügen.

![chlimage_1-67](assets/chlimage_1-67.png)

Bevor Sie fortfahren, stellen Sie sicher, dass Ihre Anmeldeinformationen Ihnen die Anmeldung bei Adobe Analytics erlauben – und zwar über einen der folgenden Links:

* [https://marketing.adobe.com](https://marketing.adobe.com)

* [https://sc.omniture.com/login/](https://sc.omniture.com/login/)

### Konfigurieren von AEM zur Verwendung Ihrer Adobe Analytics-Datenzentren {#configuring-aem-to-use-your-adobe-analytics-data-centers}

Adobe Analytics [data centers](https://developer.omniture.com/en_US/content_page/concepts-terminology/c-how-is-data-stored) collect, process and store data associated with your Adobe Analytics report suite. Sie müssen AEM für die Verwendung des Rechenzentrums konfigurieren, das Ihre Adobe Analytics-Report Suite hostet. In der folgenden Tabelle sind die verfügbaren Datenzentren sowie deren URLs aufgeführt.

| Datenzentrum | URL |
|---|---|
| San José | https://api.omniture.com/admin/1.4/rest/ |
| Dallas | https://api2.omniture.com/admin/1.4/rest/ |
| London | https://api3.omniture.com/admin/1.4/rest/ |
| Singapur | https://api4.omniture.com/admin/1.4/rest/ |
| Oregon | https://api5.omniture.com/admin/1.4/rest/ |

AEM nutzt standardmäßig das Datenzentrum in San José (https://api.omniture.com/admin/1.4/rest/).

Verwenden Sie die [Web-Konsole zum Konfigurieren des OSGi-Bundles](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) **Adobe AEM Analytics HTTP Client**. Fügen Sie die **Datenzentrum-URL** des Datenzentrums hinzu, in dem eine Report Suite gehostet wird, für die Ihre AEM-Seiten die Daten erfassen.

![aa-07](assets/aa-07.png)

1. Öffnen Sie die Web-Konsole in Ihrem Webbrowser. ([https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Geben Sie Ihre Anmeldeinformationen ein, um auf die Konsole zuzugreifen.

   >[!NOTE]
   >
   >Wenden Sie sich an Ihren Website-Administrator, um herauszufinden, ob Sie Zugriff auf diese Konsole haben.

1. Wählen Sie das Konfigurationselement namens **Adobe AEM Analytics HTTP Client** aus.
1. To add the URL for a data center, press the + button next to the **Data Center URLs** list, and type the URL in the box.

1. Klicken Sie zum Entfernen der URL aus der Liste auf die „-“-Schaltfläche neben der URL.
1. Klicken Sie auf „Speichern“.

## Konfigurieren der Verbindung zu Adobe Analytics {#configuring-the-connection-to-adobe-analytics}

>[!CAUTION]
>
>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.
>
>The [ActivityMap plugin provided by Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used.

## Konfigurieren für die Activity Map {#configuring-for-the-activity-map}

>[!CAUTION]
>
>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.
>
>The [ActivityMap plugin provided by Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used.

## Erstellen eines Adobe Analytics-Framework {#creating-a-adobe-analytics-framework}

Für die von Ihnen verwendete Report Suite-ID (RSID) können Sie steuern, welche Serverinstanzen (Autor, Veröffentlichung oder beides) Daten zur Report Suite beitragen:

* **Alle**: Informationen sowohl von der Autoren- als auch der Veröffentlichungsinstanz werden in die Report Suite eingetragen.
* **Autor**: Nur Informationen von der Autoreninstanz werden in die Report Suite eingetragen.
* **Veröffentlichungsinstanz**: Nur Informationen von der Veröffentlichungsinstanz werden in die Report Suite eingetragen.

>[!NOTE]
>
>Die Auswahl des Serverinstanztyps beschränkt Aufrufe nicht auf Adobe Analytics, sondern regelt nur, welche Aufrufe die Report Suite-ID beinhalten.
>
>Beispielsweise wird ein Framework zur Verwendung der Report Suite *diiweretail* konfiguriert und der Autor ist die ausgewählte Serverinstanz. Wenn die Seiten zusammen mit dem Framework veröffentlicht werden, werden nach wie vor Aufrufe in Adobe Analytics getätigt, allerdings beinhalten diese Aufrufe nicht die Report Suite-ID. Nur Aufrufe von der Autoreninstanz beinhalten die Report Suite-ID.

1. Wählen Sie unter **Navigation** die Option **Tools** > **Cloud Services** und dann **Legacy-Cloud-Services** aus.
1. Scrollen Sie zu **Adobe Analytics** und klicken Sie auf **[+]** neben **Verfügbare Konfigurationen**.
1. Click the **[+]** link next to your Adobe Analytics configuration.

1. Im Dialogfeld **Framework erstellen**:

   * Geben Sie einen **Titel** an.
   * Optional können Sie auch den **Namen** zu dem Knoten angeben, der die Framework-Details im Repository speichert.
   * Select **Adobe Analytics Framework**
   und klicken Sie auf **Erstellen**.

   Das Framework wird zur Bearbeitung geöffnet.

1. Klicken Sie im Abschnitt **Report Suites** des seitlichen Pods (rechts neben dem Hauptbedienfeld) auf **Element hinzufügen**. Verwenden Sie dann das Dropdown, um die Report Suite-ID (zum Beispiel `geometrixxauth`) auszuwählen, mit der das Framework interagieren soll.

   >[!NOTE]
   >
   >Die Inhaltssuche auf der linken Seite wird mit Adobe Analytics-Variablen (SiteCatalyst-Variablen) gefüllt, wenn Sie eine Report Suite-ID auswählen.

1. Verwenden Sie dann das Dropdown **Modus ausführen** (neben der Report Suite-ID), um die Serverinstanzen auszuwählen, die Informationen an die Report Suite senden sollen.

   ![aa-framework-01](assets/aa-framework-01.png)

1. To make the framework available on the publish instance of your site, on the **Page** tab of sidekick, click **Activate Framework.**

### Konfigurieren von Servereinstellungen für Adobe Analytics {#configuring-server-settings-for-adobe-analytics}

Mit dem Framework-System können Sie die Servereinstellungen in jedem Adobe Analytics-Framework ändern.

>[!CAUTION]
>
>These settings determine where your data is sent and how, so it is imperative that you *do not tamper with these settings* and let your Adobe Analytics representative set it up instead.

Beginnen Sie mit dem Öffnen des Bedienfelds. Klicken Sie auf den Pfeil nach unten neben **Server**:

![server_001](assets/server_001.png)

* **Tracking-Server**

   * enthält die URL zum Senden von Adobe Analytics-Aufrufen

      * cname - defaults to the Adobe Analytics account&#39;s *Company name*
      * d1 – bezieht sich auf das Datenzentrum, an das die Informationen gesendet werden (entweder d1, d2 oder d3)
      * sc.omtrdc.net - Domänenname

* **Sicherer Tracking-Server**

   * Verfügt über die gleichen Segmente wie der Tracking-Server
   * Wird zum Senden von Daten von sicheren Seiten (https://) verwendet

* **Besucher-Namespace**

   * Der Namespace bestimmt den ersten Teil der Tracking-URL.
   * e.g. changing the namespace to **CNAME** will cause the calls made to Adobe Analytics to look like **CNAME.d1.omtrdc.net** instead of the default.

## Verknüpfung einer Seite mit einem Adobe Analytics-Framework {#associating-a-page-with-a-adobe-analytics-framework}

Wenn eine Seite mit einem Adobe Analytics-Framework verknüpft ist, sendet die Seite beim Laden der Seite Daten an Adobe Analytics. Variablen, die auf der Seite eingetragen werden, werden zugeordnet und von den Adobe Analytics-Variablen im Framework abgerufen. Die Seitenansichten werden beispielsweise von Adobe Analytics abgerufen.

Untergeordnete Elemente der Seite übernehmen die Verknüpfung mit dem Framework. Wenn Sie beispielsweise die Stammseite Ihrer Website mit einem Framework verknüpfen, werden alle Seiten der Website mit dem Framework verknüpft.

1. Wählen Sie in der **Sites-Konsole** die Seite aus, die Sie mit diesem Tracking einrichten möchten.
1. Öffnen Sie die **[Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md)**entweder direkt über die Konsole oder über den Seiten-Editor.
1. Öffnen Sie die Registerkarte** Cloud-Services**.

1. Use the **Add Configuration** drop down to select **Adobe Analytics** from the available options. Wenn Vererbung verwendet wird, müssen Sie dies deaktivieren, bevor die Auswahl zur Verfügung gestellt wird.

1. Die Dropdown-Auswahl zu **Adobe Analytics** wird an die verfügbaren Optionen angehängt. Verwenden Sie dies, um die erforderliche Framework-Konfiguration auszuwählen.

1. Wählen Sie **Speichern und schließen** aus.
1. **[Veröffentlichen](/help/sites-authoring/publishing-pages.md)**Sie die Seite, um die Seite und alle verbundenen Konfigurationen/Dateien zu aktivieren.
1. Der letzte Schritt ist der Besuch der Seite in der Veröffentlichungsinstanz und die Suche nach Stichwort (z. B. Aubergine) mithilfe der Komponente **Suchen**.
1. You can then check the calls made to Adobe Analytics using an appropriate tool; for example, [Adobe Marketing Cloud Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger_install.html).
1. In dem genannten Beispiel sollte der Aufruf den eingegebenen Wert (d. h. Aubergine) in eVar7 enthalten und die Ereignisliste sollte „event3“ enthalten.

### Seitenansichten {#page-views}

Wenn eine Seite mit einem Adobe Analytics-Framework verknüpft ist, kann die Anzahl der Seitenansichten in der Listenansicht der Site-Konsole angezeigt werden.

Weitere Details finden Sie unter [Anzeigen von Seitenanalysedaten](/help/sites-authoring/page-analytics-using.md).

### Konfigurieren des Importintervalls {#configuring-the-import-interval}

Konfigurieren der passenden Instanz des Diensts **Adobe AEM Managed Polling Configurations**:

* **Abrufintervall**:  Das Intervall in Sekunden, mit dem der Dienst die Seitenansichtsdaten von Adobe Analytics abruft.
Das Standardintervall beträgt 43200000 ms (12 Stunden).

* **Aktivieren**:  Aktivieren oder Deaktivieren des Diensts. Standardmäßig ist der Dienst aktiviert.

To configure this OSGi service, you can either use the [Web Console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) or an [osgiConfig node in the repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) (the service PID is `com.day.cq.polling.importer.impl.ManagedPollConfigImpl`).

## Die Bearbeitung der Adobe Analytics-Konfigurationen und/oder -Frameworks {#editing-adobe-analytics-configurations-and-or-frameworks}

Navigieren Sie wie beim Erstellen einer Adobe Analytics-Konfiguration oder eines Adobe Analytics-Frameworks zum (veralteten) Bildschirm **Cloud-Services**. Wählen Sie **Konfigurationen anzeigen** aus und klicken Sie dann auf den Link zur spezifischen Konfiguration, die Sie aktualisieren möchten.

When editing an Adobe Analytics configuration, you also need to press the **Edit** button when on the configuration page itself in order to open the **Edit Component** dialog.

## Löschen von Adobe Analytics-Frameworks {#deleting-adobe-analytics-frameworks}

Zum Löschen eines Adobe Analytics-Frameworks müssen Sie es zuerst [zur Bearbeitung öffnen](#editing-adobe-analytics-configurations-and-or-frameworks).

Wählen Sie dann **Framework löschen** auf der Registerkarte **Seite** des Sidekicks aus.

