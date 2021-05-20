---
title: Freigeben von Assets über einen Link
description: Freigeben von Assets, Ordnern und Sammlungen als URL.
contentOwner: AG
role: Business Practitioner
feature: Linkfreigabe, Asset-Verwaltung
exl-id: 20370b00-862e-4d04-af2f-7d1c74a842dd
source-git-commit: 3ec39279d001297dcc11ebd1110bb452de8ca980
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 38%

---

# Freigeben von Assets über einen Link {#asset-link-sharing}

[!DNL Adobe Experience Manager Assets]Mit können Sie Assets, Ordner und Sammlungen als URL für Mitglieder Ihres Unternehmens und externe Einheiten (z. B. Partner und Anbieter) freigeben. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei [!DNL Assets] anmelden müssen.

>[!PREREQUISITES]
>
>* Sie benötigen die Berechtigung ACL bearbeiten für den Ordner oder das Asset, das Sie als Link freigeben möchten.
>* Um E-Mails an Benutzer zu senden, konfigurieren Sie die SMTP-Serverdetails in [Day CQ Mail Service](#configmailservice).


## Freigeben von Assets {#share-assets}

Um die URL für Assets zu generieren, die Sie für Benutzer freigeben möchten, verwenden Sie das Dialogfeld Linkfreigabe . Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind.

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Link freigeben]** ![Assets freigeben](assets/do-not-localize/assets_share.png). Der Link, der nach dem Klicken auf **[!UICONTROL Share]** erstellt wird, wird im Feld [!UICONTROL Link freigeben] im Voraus angezeigt. Der Link wird erst erstellt, wenn Sie auf **[!UICONTROL Submit]** klicken.

   ![Dialogfeld zur Linkfreigabe](assets/Link-sharing-dialog-box.png)

   *Abbildung: Das Dialogfeld zum Freigeben von Assets als Link.*

1. Geben Sie im Dialogfeld **[!UICONTROL Linkfreigabe]** in das Feld „E-Mail-Adresse“ die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können einen oder mehrere Benutzer hinzufügen.

   ![Freigeben von Links zu Assets direkt über das Dialogfeld „Linkfreigabe“](assets/Asset-Sharing-LinkShareDialog.png)

   *Abbildung: Geben Sie Links zu Assets direkt über das Dialogfeld  [!UICONTROL Linkfreigabe ] frei.*

   >[!NOTE]
   >
   >Wenn Sie eine E-Mail-ID eines Benutzers eingeben, der nicht Mitglied Ihres Unternehmens ist, wird den Wörtern [!UICONTROL Externer Benutzer] die E-Mail-ID des Benutzers vorangestellt.

1. Geben Sie in das Feld **[!UICONTROL Betreff]** einen Betreff für das freizugebende Asset ein.

1. Geben Sie im Feld **[!UICONTROL Meldung]** eine optionale Meldung ein.

1. Geben Sie im Feld **[!UICONTROL Expiration]** ein Ablaufdatum und eine Ablaufzeit an, damit der Link nicht mehr funktioniert. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   ![Ablaufdatum des freigegebenen Links festlegen](assets/Set-shared-link-expiration.png)

1. Damit Benutzer das Original-Asset zusammen mit den Ausgabeformaten herunterladen können, wählen Sie **[!UICONTROL Download der Originaldatei zulassen]** aus. Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail für die Benutzer freigegeben wurde.

1. Um das freigegebene Asset anzuzeigen, klicken Sie auf den Link in der E-Mail, die an den Benutzer gesendet wird. Um eine Vorschau des Assets zu generieren, klicken Sie auf das freigegebene Asset. Um die Vorschau zu schließen, klicken Sie auf **[!UICONTROL Zurück]**. Wenn Sie einen Ordner freigegeben haben, klicken Sie auf **[!UICONTROL Übergeordneter Ordner]** , um zum übergeordneten Ordner zurückzukehren.

   ![Vorschau eines freigegebenen Assets](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] unterstützt nur das Generieren der Asset-Vorschau von  [den unterstützten Dateitypen](/help/assets/assets-formats.md). Wenn andere MIME-Typen freigegeben sind, können Sie nur die Assets herunterladen und keine Vorschau anzeigen.

1. Um das freigegebene Asset herunterzuladen, klicken Sie in der Symbolleiste auf **[!UICONTROL Auswählen]**, klicken Sie auf das Asset und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Herunterladen]** .

   ![Symbolleistenoption zum Herunterladen des freigegebenen Assets](assets/chlimage_1-547.png)

1. Um die Assets anzuzeigen, die Sie als Links freigegeben haben, wechseln Sie zur [!DNL Assets] -Benutzeroberfläche und klicken Sie auf das [!DNL Experience Manager] -Logo. Wählen Sie **[!UICONTROL Navigation]**. Wählen Sie im Navigationsfenster **[!UICONTROL Freigegebene Links]** aus, um eine Liste der freigegebenen Assets anzuzeigen.

1. Um die Freigabe eines Assets aufzuheben, wählen Sie es aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Freigabe aufheben]**. Es folgt eine Bestätigungsmeldung. Der Eintrag für das Asset wird aus der Liste entfernt.

## Konfigurieren von Day CQ Mail Service {#configure-day-cq-mail-service}

1. Navigieren Sie auf der Homepage [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Klicken Sie neben dem Dienst auf **[!UICONTROL Bearbeiten]** und konfigurieren Sie die folgenden Parameter für **[!UICONTROL Day CQ Mail Service]** mit den entsprechenden Details:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der maximal zulässigen Datengröße  {#configure-maximum-data-size}

Wenn Sie Assets von dem Link herunterladen, der über die Funktion &quot;Linkfreigabe&quot;freigegeben wurde, komprimiert [!DNL Experience Manager] die Asset-Hierarchie aus dem Repository und gibt das Asset dann in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, kann es bei großen komprimierten Datenmengen zu Speicherfehlern in JVM kommen. Um das System vor einem damit zusammenhängenden potenziellen DoS-Angriff zu schützen, konfigurieren Sie die Maximalgröße mithilfe des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]** für das Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager. **** Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anfragen abgelehnt. Der Standardwert lautet 100 MB.

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Suchen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** .
1. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** im Bearbeitungsmodus und ändern Sie den Wert des Parameters **[!UICONTROL Maximale Größe von Inhalten (unkomprimiert)]**.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Speichern Sie die Änderungen.

## Best Practices und Fehlerbehebung {#best-practices-and-troubleshooting}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem [!DNL Experience Manager]-Administrator nach den [Download-Beschränkungen](#configure-maximum-data-size).
* Wenn Sie keine E-Mail mit Links zu freigegebenen Assets senden können oder die anderen Benutzer Ihre E-Mail nicht empfangen können, fragen Sie bei Ihrem [!DNL Experience Manager] -Administrator nach, ob der [E-Mail-Dienst](#configure-day-cq-mail-service) konfiguriert ist oder nicht.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#share-assets).
* Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn für die Benutzer frei.

* Wenn Sie Links aus Ihrer [!DNL Experience Manager] -Autorenbereitstellung für externe Entitäten freigeben möchten, stellen Sie sicher, dass Sie nur die folgenden URLs verfügbar machen, die nur für `GET`-Anfragen verwendet werden. Blockieren Sie aus Sicherheitsgründen andere URLs.

   * `http://[aem_server]:[port]/linkshare.html`
   * `http://[aem_server]:[port]/linksharepreview.html`
   * `http://[aem_server]:[port]/linkexpired.html`
   Rufen Sie in der [!DNL Experience Manager]-Benutzeroberfläche **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** auf. Öffnen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]** und ändern Sie die folgenden Eigenschaften im Feld **[!UICONTROL Domänen]** mit den Werten für `local`, `author` und `publish`. Geben Sie für die Eigenschaften `local` und `author` die URL für die lokale und die Autoreninstanz an. Wenn Sie eine einzelne [!DNL Experience Manager] -Autoreninstanz ausführen, verwenden Sie denselben Wert für `local` - und `author` -Eigenschaften. Geben Sie für Veröffentlichungsinstanzen die URL der Veröffentlichungsinstanz [!DNL Experience Manager] an.
