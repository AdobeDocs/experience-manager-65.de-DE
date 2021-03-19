---
title: 'Aktivieren von Asset Insights über DTM  '
description: Erfahren Sie, wie Sie Asset Insights mit Adobe Dynamic Tag Management (DTM) aktivieren können.
contentOwner: AG
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 33%

---


# Aktivieren von Asset Insights über DTM   {#enable-asset-insights-through-dtm}

Adobe Dynamic Tag Management ist ein Tool, mit dem Sie Ihre digitalen Marketingtools aktivieren können. Es wird Adobe Analytics-Kunden kostenlos bereitgestellt. Sie können Ihren Rückverfolgungscode entweder so anpassen, dass CMS-Lösungen von Drittanbietern Asset Insights verwenden können, oder Sie können DTM verwenden, um Asset Insights-Tags einzufügen. Insights werden nur für Bilder unterstützt und bereitgestellt.

>[!CAUTION]
>
>Adobe DTM wird zu Gunsten von [!DNL Adobe Experience Platform Launch] aufgegeben und wird bald [Ende des Lebenszyklus](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f) erreichen. Adobe empfiehlt, [für Asset-Einblicke ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)  [!DNL Launch] zu verwenden.

Führen Sie diese Schritte durch, um Asset Insights über DTM zu aktivieren.

1. Klicken Sie auf das Logo des Experience Managers und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Insight-Konfiguration]**.
1. [Experience Manager-Bereitstellung mit DTM Cloud Service konfigurieren](/help/sites-administering/dtm.md)

   Das API-Token sollte verfügbar sein, sobald Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) anmelden und **[!UICONTROL Kontoeinstellungen]** im Profil user besuchen. Dieser Schritt ist aus der Sicht von Asset Insights nicht erforderlich, da die Integration von Experience Manager-Sites mit Asset Insights noch in Arbeit ist.

1. Melden Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) an und wählen Sie eine Firma aus.
1. Erstellen oder Öffnen einer vorhandenen Webeigenschaft

   * Wählen Sie die Registerkarte **[!UICONTROL Webeigenschaften]** und klicken Sie dann auf **[!UICONTROL Hinzufügen Eigenschaft]**.

   * Aktualisieren Sie die Felder entsprechend und klicken Sie auf **[!UICONTROL Eigenschaft erstellen]**. Siehe [Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

   ![Webeigenschaft zum Bearbeiten](assets/Create-edit-web-property.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Regeln]** im Navigationsbereich **[!UICONTROL Seitenladeregeln]** aus und klicken Sie auf **[!UICONTROL Neue Regel erstellen]**.

   ![chlimage_1-58](assets/chlimage_1-194.png)

1. Erweitern Sie **[!UICONTROL JavaScript/Drittanbieter-Tags]**. Klicken Sie dann auf der Registerkarte **[!UICONTROL Hinzufügen Neues Skript]**, um das Dialogfeld &quot;Skript&quot;zu öffnen.****

   ![chlimage_1-59](assets/chlimage_1-195.png)

1. Klicken Sie auf das Logo des Experience Managers und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Elemente]**.
1. Klicken Sie auf **[!UICONTROL Insight Page Tracker]**, kopieren Sie den Trackercode und fügen Sie ihn dann in das Skript-Dialogfeld ein, das Sie in Schritt 6 geöffnet haben. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >* `AppMeasurement.js` entfernt. Es wird erwartet, dass es über das Adobe Analytics-Tool von DTM verfügbar ist.
   >* Der Aufruf von `assetAnalytics.dispatcher.init()` wird entfernt. Es wird erwartet, dass die Funktion erneut aufgerufen wird, sobald das Adobe Analytics-Tool von DTM vollständig geladen ist.
   >* Je nachdem, wo Asset Insights-Seitenverfolgung gehostet wird (z. B. Experience Manager, CDN usw.), muss die Herkunft der Skriptquelle möglicherweise geändert werden.
   >* Bei vom Experience Manager gehosteten Seitenaufzeichnern sollte die Quelle mit dem Hostnamen der Dispatcher-Instanz auf eine Veröffentlichungsinstanz verweisen.


1. Greife Sie auf `https://dtm.adobe.com` zu. Klicken Sie in der Web-Eigenschaft auf **[!UICONTROL Übersicht]** und dann auf **[!UICONTROL Tool hinzufügen]** oder öffnen Sie ein vorhandenes Adobe Analytics-Tool. Beim Erstellen des Tools können Sie **[!UICONTROL Konfigurationsmethode]** auf **[!UICONTROL Automatisch]** setzen.

   ![hinzufügen Adobe Analytics-Tool](assets/Add-Adobe-Analytics-Tool.png)

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
   * Wie in den Kommentaren im Insight-Seiten-Tracker-Code (**[!UICONTROL Tools > Assets > Insight Page Tracker]**) angegeben, sind die ersten drei Argumente (RSID, Tracking Server und Besucher-Namensraum) irrelevant, wenn der Seitentracker kein `AppMeasurement`-Objekt erstellt. Leere Zeichenfolgen werden stattdessen übergeben, um dies hervorzuheben.\
      Die restlichen Argumente entsprechen dem, was in der Statistiken-Konfigurationsseite konfiguriert ist (**[!UICONTROL Tools > Assets > Statistiken-Konfiguration]**).
   * Das AppMeasurement-Objekt wird abgerufen, indem `satelliteLib` für alle verfügbaren SiteCatalyst-Engines abgefragt wird. Wenn mehrere Tags konfiguriert sind, ändern Sie den Index des Array-Selektors entsprechend. Einträge im Array werden gemäß der SiteCatalyst-Tools geordnet, die in der DTM-Benutzeroberfläche verfügbar sind.

1. Speichern und schließen Sie das Fenster Code-Editor und speichern Sie die Änderungen in der Tool-Konfiguration.
1. Genehmigen Sie auf der Registerkarte **[!UICONTROL Genehmigungen]** beide ausstehenden Genehmigungen. Das DTM-Tag ist für das Einfügen auf Ihrer Webseite bereit. Weitere Informationen zum Einfügen von DTM-Tags in Webseiten finden Sie unter [Integrieren von DTM in benutzerdefinierte Seitenvorlagen](https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template/).
