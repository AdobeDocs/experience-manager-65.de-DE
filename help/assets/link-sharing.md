---
title: Freigeben von Assets über einen Link
description: Freigeben von Assets, Ordnern und Sammlungen als URL.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1f6da1c69ea3b3c3f07e8ac10fd8e1e9c7208158
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 35%

---


# Asset über einen Link freigeben {#asset-link-sharing}

[!DNL Adobe Experience Manager Assets]Mit können Sie Assets, Ordner und Sammlungen als URL für Mitglieder Ihres Unternehmens und externe Einheiten (z. B. Partner und Anbieter) freigeben. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to [!DNL Assets].

>[!PREREQUISITES]
>
>* Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.
>* Um E-Mails an die Benutzer zu senden, konfigurieren Sie die SMTP-Serverdetails im [Day CQ Mail Service](#configmailservice).


## Freigeben von Assets {#sharelink}

Um die URL für Assets zu erstellen, die Sie für Benutzer freigeben möchten, verwenden Sie das Dialogfeld &quot;Linkfreigabe&quot;. Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind.

1. In the [!DNL Assets] user interface, select the asset to share as a link.
1. From the toolbar, click the **[!UICONTROL Share Link]** ![share assets icon](assets/do-not-localize/assets_share.png).

   Der Link, der nach dem Klicken auf [!UICONTROL Freigeben] erstellt wird, wird im Voraus im Feld [!UICONTROL Link] freigeben angezeigt. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   ![Dialogfeld zur Linkfreigabe](assets/Link-sharing-dialog-box.png)

   *Abbildung: Das Dialogfeld zum Freigeben von Assets als Link.*

   >[!NOTE]
   >
   >If you want to share links from your [!DNL Experience Manager] Author deployment to external entities, ensure that you only expose the following URLs (which are used for link sharing) for `GET` requests only. Blockieren Sie andere URLs aus Sicherheitsgründen.
   >
   >* `http://[aem_server]:[port]/linkshare.html`
   >* `http://[aem_server]:[port]/linksharepreview.html`
   >* `http://[aem_server]:[port]/linkexpired.html`


1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** auf.

1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against `local`, `author`, and `publish`. For the `local` and `author` properties, provide the URL for the local and the author instance respectively. Both `local` and `author` properties have the same value if you run a single [!DNL Experience Manager] author instance. For Publish instances, provide the URL for the [!DNL Experience Manager] publish instance.

1. Geben Sie im Dialogfeld **[!UICONTROL Linkfreigabe]** in das Feld „E-Mail-Adresse“ die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können einen oder mehrere Benutzer hinzufügen.

   ![Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“](assets/Asset-Sharing-LinkShareDialog.png)

   *Abbildung: Verknüpfungen zu Assets direkt über das Dialogfeld &quot; [!UICONTROL Linkfreigabe] &quot;freigeben*

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words [!UICONTROL External User] are prefixed with the email ID of the user.

1. Geben Sie im Feld **[!UICONTROL Betreff]** eine Betreffzeile ein.

1. In the **[!UICONTROL Message]** field, enter an optional message.

1. In the **[!UICONTROL Expiration]** field, specify an expiration date and time for the link to stop working. Standardmäßig ist das Ablaufdatum auf eine Woche nach dem Datum der Linkfreigabe gesetzt.

   ![Ablaufdatum des freigegebenen Links festlegen](assets/Set-shared-link-expiration.png)

1. To let users download the original asset along with the renditions, select **[!UICONTROL Allow download of original file]**. Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail an die Benutzer weitergegeben wird.

1. Um das freigegebene Asset Ansicht, klicken Sie auf den Link in der E-Mail, die an den Benutzer gesendet wird. Das freigegebene Asset wird auf der Seite **[!UICONTROL Adobe Marketing Cloud]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-545.png)

1. Um eine Vorschau des Assets zu erstellen, klicken Sie auf das freigegebene Asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click **[!UICONTROL Parent Folder]** to return to the parent folder.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] unterstützt die Generierung der Vorschau von Assets nur [der unterstützten Dateitypen](/help/assets/assets-formats.md). Wenn andere MIME-Typen freigegeben sind, können Sie nur die Assets herunterladen und keine Vorschau durchführen.

1. To download the shared asset, click **[!UICONTROL Select]** from the toolbar, click the asset, and then click **[!UICONTROL Download]** from the toolbar.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Um die Assets, die Sie als Links freigegeben haben, Ansicht, wechseln Sie zur [!DNL Assets] Benutzeroberfläche und klicken Sie auf das [!DNL Experience Manager] Logo. Wählen Sie **[!UICONTROL Navigation]**. In the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.

1. To un-share an asset, select it and click **[!UICONTROL Unshare]** from the toolbar. Es folgt eine Bestätigungsmeldung. Der Eintrag für das Asset wird aus der Liste entfernt.

## Konfigurieren des Day CQ Mail Service {#configmailservice}

1. Navigieren Sie auf der [!DNL Experience Manager] Startseite zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Click **[!UICONTROL Edit]** beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der maximal zulässigen Datengröße     {#maxdatasize}

When you download assets from the link shared using the Link Sharing feature, [!DNL Experience Manager] compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, kann es bei großen komprimierten Datenmengen zu Speicherfehlern in JVM kommen. Um das System vor einem damit zusammenhängenden potenziellen DoS-Angriff zu schützen, konfigurieren Sie die Maximalgröße mithilfe des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]** für das Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager.  Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anforderungen abgelehnt. Der Standardwert lautet 100 MB.

1. Click the [!DNL Experience Manager] logo and then go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. From the Web Console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** im Bearbeitungsmodus und ändern Sie den Wert des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]**.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Speichern Sie die Änderungen.

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* If users cannot download the shared assets, check with your [!DNL Experience Manager] administrator what the [download limits](#maxdatasize) are.
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your [!DNL Experience Manager] administrator if the [email service](#configmailservice) is configured or not.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#sharelink).
* Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn für die Benutzer frei.
