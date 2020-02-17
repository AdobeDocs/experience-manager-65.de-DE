---
title: URL zu freigegebenen Assets erstellen
description: In diesem Artikel wird beschrieben, wie Assets, Ordner und Sammlungen im AEM Assets-Repository als URL für externe Parteien freigegeben werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Asset über einen Link freigeben {#asset-link-sharing}

Mit Adobe Experience Manager (AEM) Assets können Sie Assets, Ordner und Sammlungen als URL für Mitglieder Ihres Unternehmens und externe Einheiten (z. B. Partner und Anbieter) freigeben. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei AEM Assets anmelden müssen.

>[!NOTE]
>
>Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.

## Freigeben von Assets {#sharelink}

Sie generieren die URL für Assets, die Sie für Benutzer freigeben möchten, im Dialogfeld „Linkfreigabe“. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them.

>[!NOTE]
>
>Bevor Sie einen Link für andere Benutzer freigeben, stellen Sie sicher, dass Day CQ Mail Service konfiguriert ist. Wenn Sie [Day CQ Mail Service](/help/assets/link-sharing.md#configmailservice) vor dem Freigeben eines Links nicht konfigurieren, tritt ein Fehler auf.

1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. From the toolbar, click/tap the **[!UICONTROL Share Link]** ![assets_share](assets/assets_share.png).

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Sie können diesen Link kopieren und für andere Benutzer freigeben. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   ![Dialogfeld zur Linkfreigabe](assets/Link-sharing-dialog-box.png)

   *Abbildung: Dialogfeld mit der Linkfreigabe*

   Alternativ dazu können Sie auch die Schritte 3 bis 7 dieses Verfahrens ausführen, um E-Mail-Empfänger hinzuzufügen, die Ablaufzeit für den Link zu konfigurieren und ihn aus dem Dialogfeld zu senden.

   >[!NOTE]
   >
   >If you want to share links from your AEM Author instance to external entities, ensure that you only expose the following URLs (which are used for link sharing) for `GET` requests only. Blockieren Sie andere URLs, um die Sicherheit von AEM Author sicherzustellen.
   >
   >* http://&lt;aem_server>:&lt;port>/linkshare.html
   * http://&lt;aem_server>:&lt;port>/linksharepreview.html
   * http://&lt;aem_server>:&lt;port>/linkexpired.html


   >[!NOTE]
   Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn erneut für die Benutzer frei.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

   * local
   * Autor
   * veröffentlichen
   Für die Eigenschaften „local“ und „author“ geben Sie die URL für die entsprechenden Instanzen an. Wenn Sie eine einzelne AEM-Autoreninstanz ausführen, haben die Eigenschaften „local“ und „author“ denselben Wert. Geben Sie für die Eigenschaft „publish“ die URL für die Veröffentlichungsinstanz an.

1. Geben Sie im E-Mail-Feld des Dialogfelds **[!UICONTROL Linkfreigabe]** die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können den Link auch für mehrere Benutzer freigeben.

   Wenn der Benutzer zu Ihrem Unternehmen gehört, wählen Sie die E-Mail-ID des Benutzers in den vorgeschlagenen E-Mail-IDs aus, die in der Liste unter dem Eingabebereich angezeigt werden. Geben Sie bei einem externen Benutzer die vollständige E-Mail-ID ein und wählen Sie diese dann aus der Liste aus.

   Damit E-Mails an Benutzer gesendet werden können, konfigurieren Sie die SMTP-Serverdetails in [Day CQ Mail Service](#configmailservice).

   ![Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“](assets/Asset-Sharing-LinkShareDialog.png)

   Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“

   >[!NOTE]
   Wenn Sie die E-Mail-ID eines Benutzers eingeben, der nicht zu Ihrem Unternehmen gehört, wird den Worten „Externer Benutzer“ die E-Mail-ID des Benutzers vorangestellt.

1. Geben Sie in das Feld **[!UICONTROL Betreff]** einen Betreff für das freizugebende Asset ein.
1. Geben Sie im Feld **[!UICONTROL Meldung]** eine optionale Meldung ein.
1. Geben Sie im Feld **[!UICONTROL Ablauf]** mit der Datumsauswahl ein Ablaufdatum und eine Ablaufuhrzeit für den Link an. Standardmäßig ist das Ablaufdatum auf eine Woche nach dem Datum der Linkfreigabe gesetzt.

   ![Ablaufdatum des freigegebenen Links festlegen](assets/Set-shared-link-expiration.png)

1. Damit Benutzer das Originalbild zusammen mit den Ausgabeformaten herunterladen können, wählen Sie die Option **[!UICONTROL Download der Originaldatei zulassen]** aus.

   >[!NOTE]
   Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail für die jeweiligen Benutzer freigegeben wurde.
1. Um das freigegebene Asset anzeigen, klicken/tippen Sie auf den Link in der E-Mail, die dem Benutzer gesendet wird. Das freigegebene Asset wird auf der Seite **[!UICONTROL Adobe Marketing Cloud]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-545.png)

   Um zur Listenansicht zu wechseln, klicken bzw. tippen Sie auf die Layoutoption in der Symbolleiste.

1. Klicken oder tippen Sie auf das freigegebene Asset, um eine Vorschau des Assets zu generieren. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. Wenn Sie einen Ordner freigegeben haben, klicken oder tippen Sie auf **[!UICONTROL Übergeordneter Ordner]**, um zum übergeordneten Ordner zurückzukehren.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   AEM unterstützt das Generieren der Vorschau von Assets dieser MIME-Typen: JPG, PNG, GIF, BMP, INDD, PDF und PPT. Für Assets anderer MIME-Typen können Sie nur die Assets herunterladen.

1. To download the shared asset, tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Um die Assets anzuzeigen, die Sie als Links freigegeben haben, wechseln Sie zur Benutzeroberfläche &quot;Assets&quot;und tippen Sie auf das Experience Manager-Logo. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. Wählen Sie im Bedienfeld „Navigation“ die Option **[!UICONTROL Freigegebene Links]** aus, um eine Liste der freigegebenen Assets anzuzeigen.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar. Es folgt eine Bestätigungsmeldung. Der Eintrag für das Asset wird aus der Liste entfernt.

## Konfigurieren des Day CQ Mail Service {#configmailservice}

1. Navigieren Sie auf der Startseite von Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Tap **[!UICONTROL Edit]** beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password
   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der maximal zulässigen Datengröße {#maxdatasize}

Wenn Sie Assets herunterladen, die mithilfe der Linkfreigabe-Funktion freigegeben wurden, komprimiert AEM die Asset-Hierarchie aus dem Repository und gibt anschließend das Asset in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, führt das bei großen komprimierten Datenmengen zu Speicherfehlern in JVM. To secure the system from a potential denial of service attack due to this situation, configure the maximum size using the **[!UICONTROL Max Content Size (uncompressed)]** parameter for [!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet] in Configuration Manager. Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anforderungen abgelehnt. Der Standardwert lautet 100 MB.

1. Klicken oder tippen Sie auf das AEM-Logo und navigieren Sie anschließend zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the Web Console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Speichern Sie die Änderungen.

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem AEM-Administrator nach den [Download-Beschränkungen](#maxdatasize).
* Wenn Sie keine E-Mail mit Links zu freigegebenen Assets senden können oder die anderen Benutzer Ihre E-Mail nicht empfangen können, fragen Sie Ihren AEM-Administrator, ob der [E-Mail-Dienst](#configmailservice) konfiguriert wurde.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#sharelink).
