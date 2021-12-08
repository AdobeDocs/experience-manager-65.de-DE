---
title: Herunterladen von Assets
description: Erfahren Sie, wie Sie Assets von herunterladen [!DNL Adobe Experience Manager] und aktivieren oder deaktivieren Sie die Download-Funktion.
contentOwner: AG
role: User
feature: Asset Management,Asset Distribution
exl-id: 6bda9e52-5a6e-446e-99c7-96793482c190
source-git-commit: f9d82edbb7469fab96629fc6cf4f138a082691fd
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 70%

---

# Herunterladen von Assets aus [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Sie können Assets einschließlich der statischen und dynamischen Ausgabedarstellungen herunterladen. Sie haben auch die Möglichkeit, eine E-Mail mit Links zu Assets direkt von [!DNL Adobe Experience Manager Assets] aus zu senden. Heruntergeladene Assets werden in einer ZIP-Datei gebündelt. Die komprimierte ZIP-Datei hat eine maximale Dateigröße von 1 GB für den Exportauftrag. Es sind maximal 500 Assets pro Exportauftrag zulässig.

>[!NOTE]
>
>Jeder Benutzer, der über Leseberechtigungen für `/var/dam/share` Der Speicherort kann auf den in der E-Mail-Nachricht freigegebenen Downloadlink zugreifen.
>
>Jeder Benutzer, der über Leserechte für `/var/dam/jobs/download` -Speicherort können Assets herunterladen.
>
>Die Asset-Typen - Bildsets, Rotationssets, gemischte Mediensets und Karussellsets können nicht heruntergeladen werden.

<!--
OLD content of the above NOTE, changed wrt CQDOC-18661.
>The email recipients must be members of the `dam-users` group to access the ZIP download link in the email message.
>
-->

**Gehen Sie wie folgt vor, um Assets herunterzuladen:**

1. Klicken Sie in der linken oberen Ecke auf das -Logo. Klicken Sie in der linken Leiste auf **[!UICONTROL Navigation]**.
1. Im [!UICONTROL Navigation] Seite, klicken Sie auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner mit den Assets, die Sie herunterladen möchten.
1. Wählen Sie den Ordner oder ein oder mehrere Assets im Ordner aus.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**.
1. Wählen Sie im Dialogfeld „Herunterladen“ die gewünschten Download-Optionen aus.

   | Export- oder Download-Option | Beschreibung |
   |---|---|
   | **[!UICONTROL Separaten Ordner für jedes Asset erstellen]** | Wählen Sie diese Option, um jedes Asset, das Sie herunterladen – einschließlich der Assets in Unterordnern, die unter dem übergeordneten Ordner des Assets verschachtelt sind – in einen Ordner auf Ihrem lokalen Computer aufzunehmen. Wenn diese Option nicht ausgewählt ist, wird standardmäßig die Ordnerhierarchie ignoriert und alle Assets werden in einen Ordner auf Ihrem lokalen Computer heruntergeladen. |
   | **[!UICONTROL E-Mail]** | Es wird eine E-Mail-Benachrichtigung an den Benutzer gesendet. Standardmäßige E-Mail-Vorlagen finden Sie in folgenden Ordnern:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Vorlagen, die Sie während der Implementierung anpassen, stehen an den folgenden Speicherorten zur Verfügung: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Sie können mandantenspezifische benutzerdefinierte Vorlagen in folgenden Ordnern speichern:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Wählen Sie diese Option, um das Asset in seiner Originalform ohne Ausgabedarstellungen herunterzuladen.<br>Die Option Unter-Assets ist verfügbar, wenn das ursprüngliche Asset Teil-Assets enthält. |
   | **[!UICONTROL Ausgabedarstellung(en)]** | Eine Ausgabedarstellung ist die binäre Darstellung eines Assets. Assets haben eine primäre Darstellung – die einer hochgeladenen Datei. Sie können außerdem mehrere Darstellungen aufweisen. <br> Mit dieser Option können Sie die Ausgabedarstellungen auswählen, die heruntergeladen werden sollen. Die verfügbaren Ausgabedarstellungen hängen vom ausgewählten Asset ab. Die Option ist verfügbar, wenn das Asset Ausgabeformate aufweist. |
   | **[!UICONTROL Smartes Zuschneiden]** | Wählen Sie diese Option, um alle Ausgabedarstellungen des ausgewählten Assets, die mit der Funktion „Smartes Zuschneiden“ erstellt wurden, aus AEM herunterzuladen. Eine ZIP-Datei mit den Ausgabedarstellungen, die mit der Funktion „Smartes Zuschneiden“ erstellt wurden, wird erstellt und auf Ihren lokalen Computer heruntergeladen. |
   | **[!UICONTROL Dynamische Ausgabedarstellung(en)]** | Wählen Sie diese Option, um eine Reihe von alternativen Ausgabedarstellungen in Echtzeit zu erstellen. Wenn Sie diese Option wählen, wählen Sie durch Auswahl aus der Liste [Bildvorgabe](image-presets.md) auch die Ausgabedarstellungen, die Sie dynamisch erstellen möchten. <br>Außerdem können Sie Größe und Einheit, Format, Farbraum, Auflösung und beliebige Bild-Modifikatoren auswählen (um das Bild z. B. umzukehren). Die Option ist nur verfügbar, wenn Sie [!DNL Dynamic Media] aktiviert haben. |

1. Klicken Sie im Dialogfeld auf **[!UICONTROL Herunterladen]**.

Wenn Sie einen Ordner zum Herunterladen auswählen, wird die komplette Asset-Hierarchie unter dem Ordner heruntergeladen. Um jedes heruntergeladene Asset (einschließlich Assets in untergeordneten Ordnern) in einem eigenen Ordner abzulegen, wählen Sie die Option **[!UICONTROL Separaten Ordner für jedes Asset erstellen]**.

## Aktivieren des Asset-Download-Servlets {#enable-asset-download-servlet}

Das standardmäßige Servlet in [!DNL Experience Manager] ermöglicht es authentifizierten Benutzern, beliebig große, gleichzeitige Download-Anfragen zum Erstellen von ZIP-Dateien mit für sie sichtbaren Assets zu stellen, die den Server und das Netzwerk überlasten können. Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, ist die `AssetDownloadServlet`-OSGi-Komponente für Veröffentlichungsinstanzen standardmäßig deaktiviert.

Um das Herunterladen von Assets aus dem DAM zuzulassen, z. B. wenn Sie die Asset-Freigabe oder eine andere portalähnliche Implementierung verwenden, aktivieren Sie das Servlet manuell über eine OSGi-Konfiguration. Adobe empfiehlt, die zulässige Download-Größe so gering wie möglich zu halten, ohne dass dabei die täglichen Download-Anforderungen beeinträchtigt werden. Ein hoher Wert kann sich auf die Leistung auswirken.

1. Erstellen Sie einen Ordner mit einer Benennungsregel, die auf den Veröffentlichungslaufmodus abzielt (`config.publish`): `/apps/<your-app-name>/config.publish`. Informationen zum Definieren von Konfigurationseigenschaften für einen Ausführungsmodus finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Erstellen Sie im Konfigurationsordner eine Datei vom Typ `nt:file` benannt `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Füllen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` wie folgt. Legt eine maximale Größe (in Byte) für den Download als Wert von `asset.download.prezip.maxcontentsize` fest. Im folgenden Beispiel wird die maximale Größe des ZIP-Downloads auf maximal 100 KB konfiguriert.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

Standardmäßig gilt für `GET` Anforderungen zum Herunterladen von Dateien, [!DNL Experience Manager] erzwingt eine Beschränkung von 50 MB auf die Download-Größe des ZIP-Archivs. Über initiierte Downloads `POST` -Anfragen oder die -Benutzeroberfläche sind von dieser Beschränkung nicht betroffen.

## Deaktivieren des Asset-Download-Servlets {#disable-asset-download-servlet}

Das `Asset Download Servlet` kann in einer [!DNL Experience Manager]-Veröffentlichungsinstanz deaktiviert werden, indem die Dispatcher-Konfiguration so aktualisiert wird, dass sie alle Asset-Download-Anfragen blockiert. Das Servlet kann auch manuell direkt über die OSGi-Konsole deaktiviert werden.

1. Um Asset-Download-Anfragen über eine Dispatcher-Konfiguration zu blockieren, bearbeiten Sie die `dispatcher.any` Konfiguration und Hinzufügen einer Regel zum [Filterabschnitt](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Um die OSGi-Komponente auf einer Veröffentlichungsinstanz zu deaktivieren, rufen Sie die OSGi-Konsole auf unter `http://[aem_server]:[port]/system/console/components`. Suchen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` und klicken Sie auf **[!UICONTROL Deaktivieren]**.

>[!MORELIKETHIS]
>
>* [Herunterladen von Assets mit Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=de)
>* [Herunterladen von DRM-geschützten Assets](drm.md).
>* [Herunterladen von Assets mit dem Experience Manager-Desktop-Programm auf einem Windows- oder Mac-Desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#download-assets).
>* [Herunterladen von Assets mit Adobe Assets Link aus den unterstützten Adobe Creative Cloud-Programmen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html).

