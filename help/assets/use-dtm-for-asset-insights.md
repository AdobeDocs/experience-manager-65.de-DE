---
title: Aktivieren von Assets Insights über DTM
description: Erfahren Sie, wie Sie mit Adobe Dynamic Tag Management (DTM) Assets Insights aktivieren können.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 80e8f84e-3235-4212-9dcd-6acdb9067893
source-git-commit: afc72fb6b324cf2e0ad8168f783d9c1a6f96c614
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 30%

---

# Aktivieren von Assets Insights über DTM {#enable-asset-insights-through-dtm}

Adobe Dynamic Tag Management ist ein Tool, mit dem Sie Ihre digitalen Marketingtools aktivieren können. Es wird Adobe Analytics-Kunden kostenlos bereitgestellt. Sie können entweder Ihren Trackingcode anpassen, um CMS-Lösungen von Drittanbietern die Verwendung von Assets Insights zu ermöglichen, oder Sie können DTM zum Einfügen von Assets Insights-Tags verwenden. Insights werden nur für Bilder unterstützt und bereitgestellt.

>[!CAUTION]
>
>Adobe DTM wird nicht mehr zugunsten von [!DNL Adobe Experience Platform] unterstützt und wird bald [Ende des Lebenszyklus](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f) erreichen. Adobe empfiehlt, [ [!DNL Adobe Experience Platform] für Asset-Einblicke](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html) zu verwenden.

Führen Sie diese Schritte aus, um Assets Insights über DTM zu aktivieren.

1. Klicken Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Insights-Konfiguration]**.
1. [Konfigurieren der Experience Manager-Bereitstellung mit DTM Cloud Service](/help/sites-administering/dtm.md)

   Das API-Token sollte verfügbar sein, sobald Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) anmelden und **[!UICONTROL Kontoeinstellungen]** im Benutzerprofil aufrufen. Dieser Schritt ist aus Sicht von Assets Insights nicht erforderlich, da die Integration von Experience Manager Sites mit Assets Insights noch in Arbeit ist.

1. Melden Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) an und wählen Sie ggf. ein Unternehmen aus.
1. Erstellen oder Öffnen einer vorhandenen Webeigenschaft

   * Wählen Sie die Registerkarte **[!UICONTROL Webeigenschaften]** und klicken Sie dann auf **[!UICONTROL Eigenschaft hinzufügen]**.

   * Aktualisieren Sie die Felder entsprechend und klicken Sie auf **[!UICONTROL Eigenschaft erstellen]**. Siehe [Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

   ![Webeigenschaft &quot;Bearbeiten&quot;erstellen](assets/Create-edit-web-property.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Regeln]** die Option **[!UICONTROL Seitenladeregeln]** aus dem Navigationsbereich und klicken Sie auf **[!UICONTROL Neue Regel erstellen]**.

   ![chlimage_1-58](assets/chlimage_1-194.png)

1. Erweitern Sie **[!UICONTROL JavaScript/Drittanbieter-Tags]**. Klicken Sie dann auf der Registerkarte **[!UICONTROL Sequenzielles HTML]** auf Neues Skript hinzufügen ]**, um das Dialogfeld &quot;Skript&quot;zu öffnen.**[!UICONTROL 

   ![chlimage_1-59](assets/chlimage_1-195.png)

1. Klicken Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.
1. Klicken Sie auf **[!UICONTROL Insights Page Tracker]**, kopieren Sie den Tracker-Code und fügen Sie ihn dann in das Dialogfeld &quot;Skript&quot;ein, das Sie in Schritt 6 geöffnet haben. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >* `AppMeasurement.js` entfernt. Es wird erwartet, dass es über das Adobe Analytics-Tool von DTM verfügbar ist.
   >* Der Aufruf von `assetAnalytics.dispatcher.init()` wird entfernt. Es wird erwartet, dass die Funktion erneut aufgerufen wird, sobald das Adobe Analytics-Tool von DTM vollständig geladen ist.
   >* Je nachdem, wo der Asset Insights-Seitenverfolgung gehostet wird (z. B. Experience Manager, CDN usw.), muss der Ursprung der Skriptquelle möglicherweise geändert werden.
   >* Bei vom Experience Manager gehosteter Seitenverfolgung sollte die Quelle mit dem Hostnamen der Dispatcher-Instanz auf eine Veröffentlichungsinstanz verweisen.


1. Greife Sie auf `https://dtm.adobe.com` zu. Klicken Sie in der Web-Eigenschaft auf **[!UICONTROL Übersicht]** und dann auf **[!UICONTROL Tool hinzufügen]** oder öffnen Sie ein vorhandenes Adobe Analytics-Tool. Beim Erstellen des Tools können Sie **[!UICONTROL Konfigurationsmethode]** auf **[!UICONTROL Automatisch]** setzen.

   ![Adobe Analytics-Tool hinzufügen](assets/Add-Adobe-Analytics-Tool.png)

   Wählen Sie die Report Suites „Bereitstellung/Produktion“ nach Bedarf.

1. Erweitern Sie **[!UICONTROL Bibliotheksverwaltung]** und stellen Sie sicher, dass **[!UICONTROL Bibliothek laden unter]** auf **[!UICONTROL Seitenanfang]** eingestellt ist.

   ![chlimage_1-61](assets/chlimage_1-197.png)

1. Erweitern Sie **[!UICONTROL Seiten-Code anpassen]** und klicken Sie auf **[!UICONTROL Editor öffnen]**.

   ![chlimage_1-62](assets/chlimage_1-198.png)

1. Fügen Sie den folgenden Code in das Fenster ein:

   ```Java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * Die Seitenladeregel in DTM enthält nur den Code `pagetracker.js`. Alle `assetAnalytics`-Felder überschreiben die Standardwerte. Sie sind nicht standardmäßig erforderlich.
   * Der Code ruft `assetAnalytics.dispatcher.init()` auf, nachdem sichergestellt wurde, dass `_satellite.getToolsByType('sc')[0].getS()` initialisiert und `assetAnalytics,dispatcher.init` verfügbar ist. Daher müssen Sie sie in Schritt 11 nicht notwendigerweise hinzufügen.
   * Wie in Kommentaren im Insights-Seitenverfolgungs-Code (**[!UICONTROL Tools > Assets > Insights-Seitenverfolgung]**) angegeben, sind die ersten drei Argumente (RSID, Tracking Server und Besucher-Namespace) irrelevant, wenn der Seitenverfolgung kein `AppMeasurement`-Objekt erstellt. Leere Zeichenfolgen werden stattdessen übergeben, um dies hervorzuheben.\
      Die restlichen Argumente entsprechen dem, was in der Statistiken-Konfigurationsseite konfiguriert ist (**[!UICONTROL Tools > Assets > Statistiken-Konfiguration]**).
   * Das AppMeasurement-Objekt wird abgerufen, indem `satelliteLib` für alle verfügbaren SiteCatalyst-Engines abgefragt wird. Wenn mehrere Tags konfiguriert sind, ändern Sie den Index des Array-Selektors entsprechend. Einträge im Array werden gemäß der SiteCatalyst-Tools geordnet, die in der DTM-Benutzeroberfläche verfügbar sind.

1. Speichern und schließen Sie das Fenster des Code-Editors und speichern Sie dann die Änderungen in der Tool-Konfiguration.
1. Genehmigen Sie auf der Registerkarte **[!UICONTROL Validierungen]** die beiden ausstehenden Genehmigungen. Das DTM-Tag ist für das Einfügen auf Ihrer Webseite bereit.
