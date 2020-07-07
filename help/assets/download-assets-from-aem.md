---
title: Laden Sie digitale Assets herunter [!DNL Adobe Experience Manager].
description: Learn how to download assets from [!DNL Adobe Experience Manager] and enable or disable the download functionality.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b59f7471ab9f3c5e6eb3365122262b592c8e6244
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 39%

---


# Download assets from [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Sie können Assets einschließlich der statischen und dynamischen Ausgabeformate herunterladen. Alternatively, you can send emails with links to assets directly from [!DNL Adobe Experience Manager Assets]. Heruntergeladene Assets werden in einer ZIP-Datei gebündelt. Die komprimierte ZIP-Datei hat eine maximale Dateigröße von 1 GB für den Exportauftrag. Es sind maximal 500 Assets pro Exportauftrag zulässig.

>[!NOTE]
>
>Empfänger von E-Mails müssen Mitglieder der Gruppe `dam-users` sein, um auf den ZIP-Download-Link in der E-Mail zugreifen zu können. Um die Assets herunterladen zu können, müssen diese Mitglieder über die Berechtigung zum Starten von Workflows verfügen, die das Herunterladen von Assets auslösen.

Die Asset-Typen „Bildset“, „Rotationsset“ „Gemischtes Medienset“ und „Karussellset“ können nicht heruntergeladen werden.

**So laden Sie Assets herunter,**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Navigation]**.
1. Tippen Sie auf der Navigationsseite auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien.]**
1. Navigieren Sie zu einem Ordner mit den Assets, die Sie herunterladen möchten.
1. Wählen Sie den Ordner oder einen oder mehrere Assets im Ordner aus.
1. On the toolbar, tap **[!UICONTROL Download.]**

   ![Verfügbare Optionen beim Herunterladen von Assets aus Experience Managern](/help/assets/assets/asset-download1.png)

   *Abbildung: Optionen des Dialogfelds &quot;Herunterladen&quot;.*

1. Wählen Sie im Dialogfeld &quot;Herunterladen&quot;die gewünschten Download-Optionen aus.

   | Download-Option | Beschreibung |
   |---|---|
   | **[!UICONTROL Separaten Ordner für jedes Asset erstellen]** | Wählen Sie diese Option, um alle Assets, die Sie herunterladen, einschließlich Assets in untergeordneten Ordnern, die im übergeordneten Ordner des Assets verschachtelt sind, in einen Ordner auf Ihrem lokalen Computer einzuschließen. Wenn diese Option *nicht* ausgewählt ist, wird standardmäßig die Ordnerhierarchie ignoriert und alle Assets werden in einen Ordner auf Ihrem lokalen Computer heruntergeladen. |
   | **[!UICONTROL E-Mail]** | Wählen Sie diese Option, um eine E-Mail-Benachrichtigung an den Empfänger zu senden. Standardmäßige E-Mail-Vorlagen finden Sie in folgenden Ordnern:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Vorlagen, die Sie während der Bereitstellung anpassen, stehen an den folgenden Speicherorten zur Verfügung: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Sie können benutzerdefinierte Vorlagen für Mandanten an folgenden Speicherorten speichern:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Wählen Sie diese Option, um das Asset in seinem ursprünglichen Formular ohne Darstellungen herunterzuladen.<br>Die Option für Teilassets ist verfügbar, wenn das ursprüngliche Asset Teilassets enthält. |
   | **[!UICONTROL Ausgabeformat(e)]** | Das Ausgabeformat ist die binäre Darstellung eines Assets. Assets haben eine primäre Darstellung – die einer hochgeladenen Datei. Sie können außerdem mehrere Darstellungen aufweisen. <br> Mit dieser Option können Sie die Ausgabeformate auswählen, die heruntergeladen werden sollen. Die verfügbaren Darstellungen hängen vom ausgewählten Asset ab. |
   | **[!UICONTROL Intelligentes Zuschneiden]** | Wählen Sie diese Option, um alle Smart-Schnittdarstellungen des ausgewählten Assets aus AEM herunterzuladen. Eine ZIP-Datei mit den Smart-Zuschneidedarstellungen wird erstellt und auf Ihren lokalen Computer heruntergeladen. |
   | **[!UICONTROL Dynamische Ausgabe(n)]** | Wählen Sie diese Option, um eine Reihe von alternativen Darstellungen in Echtzeit zu erstellen. When you select this option, you also select the renditions that you want to create dynamically by selecting from the [Image Preset](image-presets.md) list. <br>Darüber hinaus können Sie die Größe und Maßeinheit, das Format, den Farbraum, die Auflösung und optionale Bildmodifikatoren wie das Invertieren des Bildes auswählen. Die Option ist nur verfügbar, wenn Sie [!DNL Dynamic Media] aktiviert haben. |

1. Tippen Sie im Dialogfeld auf **[!UICONTROL Herunterladen.]**.

## Aktivieren des Asset-Download-Servlets {#enable-asset-download-servlet}

The default servlet in [!DNL Experience Manager] allows authenticated users to issue arbitrarily large, concurrent download requests for creating ZIP files of assets visible to them that can overload the server and the network. Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, ist die `AssetDownloadServlet`-OSGi-Komponente für Veröffentlichungsinstanzen standardmäßig deaktiviert.

Um das Herunterladen von Assets aus dem DAM zuzulassen, z. B. wenn Sie die Asset-Freigabe oder eine andere portalähnliche Implementierung verwenden, aktivieren Sie das Servlet manuell über eine OSGi-Konfiguration. Adobe empfiehlt, die zulässige Download-Größe so gering wie möglich zu halten, ohne dass dabei die täglichen Download-Anforderungen beeinträchtigt werden. Ein hoher Wert kann sich auf die Leistung auswirken.

1. Create a folder with a naming convention that targets the publish runmode (`config.publish`): `/apps/<your-app-name>/config.publish`. Informationen zum Definieren der Konfigurationseigenschaften für einen Ausführungsmodus finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).

1. In the configuration folder, create a file of type `nt:file` named `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Füllen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` wie folgt. Legt eine maximale Größe (in Byte) für den Download als Wert von `asset.download.prezip.maxcontentsize` fest. Im folgenden Beispiel wird die maximale Größe des ZIP-Downloads auf maximal 100 KB konfiguriert.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Deaktivieren des Asset-Download-Servlets {#disable-asset-download-servlet}

The `Asset Download Servlet` can be disabled on an [!DNL Experience Manager] Publish instances by updating the dispatcher configuration to block any asset download requests. Das Servlet kann auch manuell direkt über die OSGi-Konsole deaktiviert werden.

1. To block asset download requests via a dispatcher configuration, edit the `dispatcher.any` configuration and add a rule to the [filter section](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Disable the OSGi component on a Publish instance by navigating to the OSGi Console at `http://[aem_server]:[port]/system/console/components`. Suchen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` und klicken Sie auf **[!UICONTROL Deaktivieren]**.

>[!MORELIKETHIS]
>
>* [Herunterladen von DRM-geschützten Assets](drm.md).
>* [Herunterladen von Assets mit der Experience Manager-Desktop-App auf einem Win- oder Mac-Desktop](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html).
>* [Herunterladen von Assets mit Adobe Assets Link aus den unterstützten Adobe Creative Cloud-Programmen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html).

