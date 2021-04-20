---
title: Freigeben von Assets über einen Link
description: Freigeben von Assets, Ordnern und Sammlungen als URL.
contentOwner: AG
role: Business Practitioner
feature: Link Sharing,Asset Management
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 40%

---


# Asset über einen Link {#asset-link-sharing} freigeben

[!DNL Adobe Experience Manager Assets]Mit können Sie Assets, Ordner und Sammlungen als URL für Mitglieder Ihres Unternehmens und externe Einheiten (z. B. Partner und Anbieter) freigeben. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei [!DNL Assets] anmelden müssen.

>[!PREREQUISITES]
>
>* Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.
>* Um E-Mails an die Benutzer zu senden, konfigurieren Sie die SMTP-Serverdetails in [Day CQ Mail Service](#configmailservice).


## Freigeben von Assets {#sharelink}

Um die URL für Assets zu erstellen, die Sie für Benutzer freigeben möchten, verwenden Sie das Dialogfeld &quot;Linkfreigabe&quot;. Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind.

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Link freigeben]** ![Assets freigeben](assets/do-not-localize/assets_share.png).

   Der Link, der nach dem Klicken auf [!UICONTROL Freigeben] erstellt wird, wird vorab im Feld [!UICONTROL Link freigeben] angezeigt. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   ![Dialogfeld zur Linkfreigabe](assets/Link-sharing-dialog-box.png)

   *Abbildung: Das Dialogfeld zum Freigeben von Assets als Link.*

   >[!NOTE]
   >
   >Wenn Sie Links von Ihrer [!DNL Experience Manager] Autorenbereitstellung für externe Entitäten freigeben möchten, stellen Sie sicher, dass Sie nur die folgenden URLs (die für die Linkfreigabe verwendet werden) für `GET`-Anforderungen bereitstellen. Blockieren Sie andere URLs aus Sicherheitsgründen.
   >
   >* `http://[aem_server]:[port]/linkshare.html`
   >* `http://[aem_server]:[port]/linksharepreview.html`
   >* `http://[aem_server]:[port]/linkexpired.html`


1. Rufen Sie in der [!DNL Experience Manager]-Schnittstelle **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Webkonsole]** auf.

1. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]** und ändern Sie die folgenden Eigenschaften im Feld **[!UICONTROL Domänen]** mit den Werten, die gegen `local`, `author` und `publish` erwähnt werden. Geben Sie für die Eigenschaften `local` und `author` die URL für die lokale und die Autoreninstanz an. Die Eigenschaften `local` und `author` haben denselben Wert, wenn Sie eine einzelne [!DNL Experience Manager] Autoreninstanz ausführen. Geben Sie für Veröffentlichungsinstanzen die URL für die Instanz im Veröffentlichungsmodus ein.[!DNL Experience Manager]

1. Geben Sie im Dialogfeld **[!UICONTROL Linkfreigabe]** in das Feld „E-Mail-Adresse“ die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können einen oder mehrere Benutzer hinzufügen.

   ![Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“](assets/Asset-Sharing-LinkShareDialog.png)

   *Abbildung: Verknüpfungen zu Assets direkt über das Dialogfeld &quot; [!UICONTROL Linkfreigabe&quot;] freigeben.*

   >[!NOTE]
   >
   >Wenn Sie eine E-Mail-ID eines Benutzers eingeben, der nicht Mitglied Ihres Unternehmens ist, wird dem Wort [!UICONTROL Externer Benutzer] die E-Mail-ID des Benutzers vorangestellt.

1. Geben Sie in das Feld **[!UICONTROL Betreff]** einen Betreff für das freizugebende Asset ein.

1. Geben Sie im Feld **[!UICONTROL Meldung]** eine optionale Meldung ein.

1. Geben Sie im Feld **[!UICONTROL Ablauf]** ein Ablaufdatum und eine Uhrzeit ein, damit der Link nicht mehr funktioniert. Standardmäßig ist das Ablaufdatum auf eine Woche nach dem Datum der Linkfreigabe gesetzt.

   ![Ablaufdatum des freigegebenen Links festlegen](assets/Set-shared-link-expiration.png)

1. Damit Benutzer das ursprüngliche Asset zusammen mit den Darstellungen herunterladen können, wählen Sie **[!UICONTROL Download der Originaldatei]** zulassen. Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail an die Benutzer weitergegeben wird.

1. Um das freigegebene Asset Ansicht, klicken Sie auf den Link in der E-Mail, die an den Benutzer gesendet wird. Das freigegebene Asset wird auf der Seite [!UICONTROL Adobe Marketing Cloud] angezeigt.

   ![Freigegebene Assets stehen in Adobe Marketing Cloud zur Verfügung](assets/chlimage_1-545.png)

1. Um eine Vorschau des Assets zu erstellen, klicken Sie auf das freigegebene Asset. Um die Vorschau zu schließen und zur Seite **[!UICONTROL Marketing Cloud]** zurückzukehren, klicken Sie in der Symbolleiste auf **[!UICONTROL Zurück]**. Wenn Sie einen Ordner freigegeben haben, klicken Sie auf **[!UICONTROL Übergeordneter Ordner]**, um zum übergeordneten Ordner zurückzukehren.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] unterstützt die Generierung der Vorschau von Assets nur  [der unterstützten Dateitypen](/help/assets/assets-formats.md). Wenn andere MIME-Typen freigegeben sind, können Sie nur die Assets herunterladen und keine Vorschau durchführen.

1. Um das freigegebene Asset herunterzuladen, klicken Sie in der Symbolleiste auf **[!UICONTROL Wählen Sie]**, klicken Sie auf das Asset und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Herunterladen]**.

   ![Werkzeugleistenoption zum Herunterladen des freigegebenen Assets](assets/chlimage_1-547.png)

1. Um die Assets, die Sie als Links freigegeben haben, Ansicht, wechseln Sie zur [!DNL Assets]-Benutzeroberfläche und klicken Sie auf das [!DNL Experience Manager]-Logo. Wählen Sie **[!UICONTROL Navigation]**. Wählen Sie im Navigationsbereich **[!UICONTROL Freigegebene Links]**, um eine Liste freigegebener Elemente anzuzeigen.

1. Um die Freigabe eines Assets aufzuheben, wählen Sie es aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Freigabe aufheben]**. Es folgt eine Bestätigungsmeldung. Der Eintrag für das Asset wird aus der Liste entfernt.

## Konfigurieren des Day CQ Mail Service {#configmailservice}

1. Navigieren Sie auf der Startseite [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Webkonsole]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** neben dem Dienst und konfigurieren Sie die folgenden Parameter für **[!UICONTROL Day CQ Mail Service]** mit den angegebenen Details zu ihren Namen:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der maximal zulässigen Datengröße  {#maxdatasize}

Wenn Sie Assets von der mit der Funktion &quot;Linkfreigabe&quot;freigegebenen Verknüpfung herunterladen, komprimiert [!DNL Experience Manager] die Asset-Hierarchie aus dem Repository und gibt das Asset dann in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, kann es bei großen komprimierten Datenmengen zu Speicherfehlern in JVM kommen. Um das System vor einem damit zusammenhängenden potenziellen DoS-Angriff zu schützen, konfigurieren Sie die Maximalgröße mithilfe des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]** für das Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager.  Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anfragen abgelehnt. Der Standardwert lautet 100 MB.

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Webkonsole]**.
1. Suchen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]**.
1. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** im Bearbeitungsmodus und ändern Sie den Wert des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]**.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Speichern Sie die Änderungen.

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem [!DNL Experience Manager]-Administrator, welche [Download-Beschränkungen](#maxdatasize) gelten.
* Wenn Sie keine E-Mail mit Links zu freigegebenen Assets senden können oder wenn andere Benutzer Ihre E-Mail nicht empfangen können, wenden Sie sich an Ihren [!DNL Experience Manager]-Administrator, wenn der [E-Mail-Dienst](#configmailservice) konfiguriert ist oder nicht.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#sharelink).
* Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn für die Benutzer frei.
