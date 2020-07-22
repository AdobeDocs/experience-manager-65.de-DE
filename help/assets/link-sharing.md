---
title: URL zu freigegebenen Assets erstellen
description: In diesem Artikel wird beschrieben, wie Sie Assets, Experience Manager und Sammlungen als URL für externe Parteien freigeben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 91caca39b0b6c5c0c98b58be02f518901a3d90e3
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 51%

---


# Asset über einen Link freigeben {#asset-link-sharing}

Mit Adobe Experience Manager Assets können Sie Assets, Ordner und Sammlungen als URL für Mitglieder Ihres Unternehmens und externe Entitäten, einschließlich Partner und Anbieter, freigeben. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei Assets anmelden müssen.

>[!NOTE]
>
>Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.

## Freigeben von Assets {#sharelink}

Die URL für Assets, die Sie für Benutzer freigeben möchten, generieren Sie im Dialogfeld „Link-Freigabe“. Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind.

>[!NOTE]
>
>Bevor Sie einen Link für andere Benutzer freigeben, stellen Sie sicher, dass Day CQ Mail Service konfiguriert ist. Wenn Sie [Day CQ Mail Service](/help/assets/link-sharing.md#configmailservice) vor dem Freigeben eines Links nicht konfigurieren, tritt ein Fehler auf.

1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. From the toolbar, click the **[!UICONTROL Share Link]** ![share assets icon](assets/do-not-localize/assets_share.png).

   Im Feld **[!UICONTROL Link freigeben]** wird automatisch ein Asset-Link erstellt. Sie können diesen Link kopieren und für andere Benutzer freigeben. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   ![Dialogfeld zur Linkfreigabe](assets/Link-sharing-dialog-box.png)

   *Abbildung: Das Dialogfeld zum Freigeben von Assets als Link.*

   Alternativ dazu können Sie auch die Schritte 3 bis 7 dieses Verfahrens ausführen, um E-Mail-Empfänger hinzuzufügen, die Ablaufzeit für den Link zu konfigurieren und ihn aus dem Dialogfeld zu senden.

   >[!NOTE]
   >
   >If you want to share links from your Experience Manager Author deployment to external entities, ensure that you only expose the following URLs (which are used for link sharing) for `GET` requests only. Sperren Sie andere URLs, um die Sicherheit von Experience Manager Author zu gewährleisten.
   >
   >* http://[aem_server]:[port]/linkshare.html
   >* http://[aem_server]:[port]/linksharepreview.html
   >* http://[aem_server]:[port]/linkexpired.html


   >[!NOTE]
   >
   >Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn für die Benutzer frei.

1. Rufen Sie in der Benutzeroberfläche von Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** auf.

1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against `local`, `author`, and `publish`. For the `local` and `author` properties, provide the URL for the local and the author instance respectively. Both `local` and `author` properties have the same value if you run a single Experience Manager Author instance. For `publish`, provide the URL for the Experience Manager publish instance.

1. Geben Sie im Dialogfeld **[!UICONTROL Linkfreigabe]** in das Feld „E-Mail-Adresse“ die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können den Link auch für mehrere Benutzer freigeben.

   Wenn der Benutzer zu Ihrem Unternehmen gehört, wählen Sie die E-Mail-ID des Benutzers in den vorgeschlagenen E-Mail-IDs aus, die in der Liste unter dem Eingabebereich angezeigt werden. Geben Sie bei einem externen Benutzer die vollständige E-Mail-ID ein und wählen Sie diese dann aus der Liste aus.

   Damit E-Mails an Benutzer gesendet werden können, konfigurieren Sie die SMTP-Serverdetails in [Day CQ Mail Service](#configmailservice).

   ![Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“](assets/Asset-Sharing-LinkShareDialog.png)

   *Abbildung: Verknüpfungen zu Assets direkt über das Dialogfeld &quot;[!UICONTROL Linkfreigabe]&quot;freigeben*

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words [!UICONTROL External User] are prefixed with the email ID of the user.

1. In the **[!UICONTROL Subject]** field, enter a subject for the asset you want to share.

1. In the **[!UICONTROL Message]** field, enter an optional message.

1. Geben Sie im Feld **[!UICONTROL Ablauf]** mit der Datumsauswahl ein Ablaufdatum und eine Ablaufuhrzeit für den Link an. Standardmäßig ist das Ablaufdatum auf eine Woche nach dem Datum der Linkfreigabe gesetzt.

   ![Ablaufdatum des freigegebenen Links festlegen](assets/Set-shared-link-expiration.png)

1. Damit Benutzer das Originalbild zusammen mit den Ausgabeformaten herunterladen können, wählen Sie die Option **[!UICONTROL Download der Originaldatei zulassen]** aus.

   >[!NOTE]
   >
   >Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail für die jeweiligen Benutzer freigegeben wurde.
1. Um das freigegebene Asset Ansicht, klicken Sie auf den Link in der E-Mail, die an den Benutzer gesendet wird. Das freigegebene Asset wird auf der Seite **[!UICONTROL Adobe Marketing Cloud]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-545.png)

   Um zur Ansicht der Liste zu wechseln, klicken Sie in der Symbolleiste auf die Layoutoption.

1. Um eine Vorschau des Assets zu erstellen, klicken Sie auf das freigegebene Asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click **[!UICONTROL Parent Folder]** to return to the parent folder.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >Experience Manager unterstützt das Generieren der Vorschau von Assets dieser MIME-Typen: JPG, PNG, GIF, BMP, INDD, PDF und PPT. Für Assets anderer MIME-Typen können Sie nur die Assets herunterladen.

1. To download the shared asset, click **[!UICONTROL Select]** from the toolbar, click the asset, and then click **[!UICONTROL Download]** from the toolbar.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Um die Assets, die Sie als Links freigegeben haben, Ansicht, rufen Sie die Benutzeroberfläche &quot;Assets&quot;auf und klicken Sie auf das Logo des Experience Managers. Wählen Sie in der Liste die Option **[!UICONTROL Navigation]** aus, um das Bedienfeld „Navigation“ anzuzeigen.
1. Wählen Sie im Bedienfeld „Navigation“ die Option **[!UICONTROL Freigegebene Links]** aus, um eine Liste der freigegebenen Assets anzuzeigen.
1. To un-share an asset, select it and click **[!UICONTROL Unshare]** from the toolbar. Es folgt eine Bestätigungsmeldung. Der Eintrag für das Asset wird aus der Liste entfernt.

## Konfigurieren des Day CQ Mail Service {#configmailservice}

1. Navigieren Sie auf der Startseite Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Click **[!UICONTROL Edit]** beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der maximal zulässigen Datengröße     {#maxdatasize}

Wenn Sie Assets von der mit der Funktion &quot;Linkfreigabe&quot;freigegebenen Verknüpfung herunterladen, komprimiert Experience Manager die Asset-Hierarchie aus dem Repository und gibt das Asset dann in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, kann es bei großen komprimierten Datenmengen zu Speicherfehlern in JVM kommen. Um das System vor einem damit zusammenhängenden potenziellen DoS-Angriff zu schützen, konfigurieren Sie die Maximalgröße mithilfe des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]** für das Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager.  Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anforderungen abgelehnt. Der Standardwert lautet 100 MB.

1. Click the Experience Manager logo and then go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. From the Web Console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** im Bearbeitungsmodus und ändern Sie den Wert des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]**.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Speichern Sie die Änderungen.

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* If users cannot download the shared assets, check with your Experience Manager administrator what the [download limits](#maxdatasize) are.
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your Experience Manager administrator if the [email service](#configmailservice) is configured or not.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#sharelink).
