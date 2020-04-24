---
title: Laden Sie digitale Assets von [!DNL Adobe Experience Manager] herunter.
description: Erfahren Sie, wie Sie Assets von [!DNL Adobe Experience Manager] herunterladen und die Download-Funktion aktivieren oder deaktivieren können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# Download assets from [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Sie können Assets einschließlich der statischen und dynamischen Wiedergabeformate herunterladen. Alternatively, you can send emails with links to assets directly from [!DNL Adobe Experience Manager Assets]. Heruntergeladene Assets werden in einer ZIP-Datei gebündelt. Die komprimierte ZIP-Datei hat eine maximale Dateigröße von 1 GB für den Exportauftrag. Maximal 500 Gesamt-Assets pro Exportauftrag sind zulässig.

>[!NOTE]
>
>Empfänger von E-Mails müssen Mitglieder der Gruppe `dam-users` sein, um auf den ZIP-Download-Link in der E-Mail zugreifen zu können. Um die Assets herunterladen zu können, müssen diese Mitglieder über die Berechtigung zum Starten von Workflows verfügen, die das Herunterladen von Assets auslösen.

To download assets, navigate to an asset, select the asset, and tap **[!UICONTROL Download]** from the toolbar. Geben Sie im dann angezeigten Dialogfeld die Download-Optionen an.

Die Asset-Typen „Bildset“, „Rotationsset“ „Gemischtes Medienset“ und „Karussellset“ können nicht heruntergeladen werden.

![Verfügbare Optionen beim Herunterladen von Assets aus Experience Manager Assets](assets/asset_download_dialog.png)

*Abbildung: Verfügbare Optionen beim Herunterladen von Assets[!DNL Experience Manager Assets].*

Im Folgenden finden Sie die Export-/Download-Optionen. Dynamische Ausgabeformate gibt es nur in Dynamic Media. Damit können Sie Ausgabeformate zusätzlich zum ausgewählten Asset direkt generieren. Diese Option steht nur zur Verfügung, wenn Sie Dynamic Media aktiviert haben.

| Export- oder Download-Optionen | Beschreibungen |
|---|---|
| [!UICONTROL Assets] | Wählen Sie diese Option, um das Asset in seiner Originalform ohne Ausgabeformate herunterzuladen. |
| [!UICONTROL Ausgabeformate] | Das Ausgabeformat ist die binäre Darstellung eines Assets. Assets haben eine primäre Darstellung – die einer hochgeladenen Datei. Sie können außerdem mehrere Darstellungen aufweisen. <br> Mit dieser Option können Sie die Ausgabeformate auswählen, die heruntergeladen werden sollen. Die verfügbaren Ausgabeformate hängen von dem von Ihnen ausgewählten Asset ab. |
| [!UICONTROL Dynamische Ausgabeformate] | Ein dynamisches Ausgabeformat generiert direkt andere Ausgabeformate. When you select this option, you also select the renditions you want to create dynamically by selecting from the [Image Preset](image-presets.md) list. <br>Außerdem können Sie Größe und Einheit, Format, Farbraum, Auflösung und beliebige Bild-Modifikatoren auswählen (um das Bild z. B. umzukehren). |
| [!UICONTROL E-Mail] | Es wird eine E-Mail-Benachrichtigung an den Benutzer gesendet. Standardmäßige E-Mail-Vorlagen finden Sie in folgenden Ordnern:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> Vorlagen, die Sie in Ihrer Implementierung anpassen, sollten sich in folgenden Ordnern befinden: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul>Sie können mandantenspezifische benutzerdefinierte Vorlagen in folgenden Ordnern speichern:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> |
| [!UICONTROL Separaten Ordner für jedes Asset erstellen] | Wählen Sie diese Option aus, um die Ordnerhierarchie beim Herunterladen der Assets beizubehalten. Standardmäßig wird die Ordnerhierarchie ignoriert und alle Assets werden in einen Ordner auf Ihrem lokalen System heruntergeladen. |

Die Option „Ausgabeformate“ ist verfügbar, wenn das Asset über Ausgabeformate verfügt. Die Option „Teilassets“ ist verfügbar, wenn das Asset Teilassets enthält.

Wenn Sie einen Ordner zum Herunterladen auswählen, wird die komplette Asset-Hierarchie unter dem Ordner heruntergeladen. Um jedes heruntergeladene Asset (einschließlich Assets in untergeordneten Ordnern) in einem eigenen Ordner abzulegen, wählen Sie die Option **[!UICONTROL Separaten Ordner für jedes Asset erstellen]**.

## Aktivieren des Asset-Download-Servlets {#enable-asset-download-servlet}

The default servlet in [!DNL Experience Manager] allows authenticated users to issue arbitrarily-large, concurrent download requests for creating ZIP files of assets visible to them that can overload the server and the network. Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, ist die `AssetDownloadServlet`-OSGi-Komponente für Veröffentlichungsinstanzen standardmäßig deaktiviert.

Um das Herunterladen von Assets aus dem DAM zuzulassen, z. B. wenn Sie die Asset-Freigabe oder eine andere portalähnliche Implementierung verwenden, aktivieren Sie das Servlet manuell über eine OSGi-Konfiguration. Adobe empfiehlt, die zulässige Download-Größe so gering wie möglich zu halten, ohne dass dabei die täglichen Download-Anforderungen beeinträchtigt werden. Ein hoher Wert kann sich auf die Leistung auswirken.

1. Erstellen Sie einen Ordner mit einer Benennungsregel, die auf den Veröffentlichungslaufmodus zielt, d. h. `config.publish`:

   `/apps/<your-app-name>/config.publish`

   Weitere Informationen zum Definieren der Konfigurationseigenschaften für einen Ausführungsmodus finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode) .

1. Erstellen Sie im Konfigurationsordner eine neue Datei des Typs `nt:file` mit dem Namen `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Füllen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` wie folgt. Legt eine maximale Größe (in Byte) für den Download als Wert von `asset.download.prezip.maxcontentsize` fest. Im folgenden Beispiel wird die maximale Größe des ZIP-Downloads auf maximal 100 KB konfiguriert.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Deaktivieren des Asset-Download-Servlets {#disable-asset-download-servlet}

The `Asset Download Servlet` can be disabled on an [!DNL Experience Manager] Publish instances by updating the dispatcher configuration to block any asset download requests. Das Servlet kann auch manuell direkt über die OSGi-Konsole deaktiviert werden.

1. Um Asset-Download-Anforderungen über eine Dispatcher-Konfiguration zu blockieren, bearbeiten Sie die Konfiguration `dispatcher.any` und fügen Sie dem [Filterabschnitt](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter) eine neue Regel hinzu.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Sie können die OSGi-Komponente auf einer Veröffentlichungsinstanz manuell deaktivieren, indem Sie die OSGi-Konsole unter `<aem-host>/system/console/components` aufrufen. Suchen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` und klicken Sie auf **[!UICONTROL Deaktivieren]**.

>[!MORELIKETHIS]
>
>* [Herunterladen von DRM-geschützten Assets](drm.md)
>* [Herunterladen von Assets mit der Experience Manager-Desktop-App auf dem Windows- oder Mac-Desktop](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html)
>* [Herunterladen von Assets mit Adobe Assets Link aus den unterstützten Adobe Creative Cloud-Programmen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html)

