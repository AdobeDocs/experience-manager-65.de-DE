---
title: Integrieren von Adobe Sign mit AEM Forms
seo-title: Integrieren Sie Adobe Sign mit AEM Forms
description: Erfahren Sie, wie Sie Adobe Sign für AEM Forms konfigurieren
seo-description: Erfahren Sie, wie Sie Adobe Sign für AEM Forms konfigurieren
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
translation-type: tm+mt
source-git-commit: f0038c1f88ea0047cbaae4fe49456a665aa67f10
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 66%

---


# Integrieren von Adobe Sign mit AEM Forms{#integrate-adobe-sign-with-aem-forms}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Szenario mit Adobe Sign und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine **Dienstleistung zu beantragen**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstanbieter gesendet. Dienstanbieter prüft den Antrag und markiert ihn mit Adobe Sign als genehmigt. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, konfigurieren Sie Adobe Sign in AEM Cloud-Diensten:

## Voraussetzungen {#prerequisites}

Um Adobe Sign mit AEM Forms zu integrieren, benötigen Sie Folgendes:

* Ein gültiges[ Adobe Sign-Entwicklerkonto.](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html) 
* Einen[ SSL aktivierten](/help/sites-administering/ssl-by-default.md) AEM Forms-Server.
* Eine[ Adobe Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Anmeldeinformationen (Client-ID und Client Secret) der Adobe Sign API-Anwendung.
* Entfernen Sie bei der Neukonfiguration die vorhandene Adobe Sign-Konfiguration aus der Autoreninstanz und der Veröffentlichungsinstanz.
* Verwenden Sie für Autoren- und Veröffentlichungsinstanzen [identischen Verschlüsselungsschlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) .

## Konfigurieren Sie Adobe Sign mit AEM Forms {#configure-adobe-sign-with-aem-forms}

Nachdem die Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um Adobe Sign mit AEM Forms in der Autoreninstanz zu konfigurieren:

1. On AEM Forms author instance, navigate to **Tools** ![hammer](assets/hammer.png) > **General** > **Configuration Browser**.
1. On the **[!UICONTROL Configuration Browser]** page, tap **[!UICONTROL Create]**.
   * See the [Configuration Browser](/help/sites-administering/configurations.md) documentation for more information.
1. In the **[!UICONTROL Create Configuration]** dialog, specify a **[!UICONTROL Title]** for the configuration, enable **[!UICONTROL Cloud Configurations]**, and tap **[!UICONTROL Create]**. Es wird ein Konfigurationscontainer für Cloud-Dienste erstellt.
1. Navigate to **Tools** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign** and select the configuration container you created in the above step.

   >[!NOTE]
   >
   >Sie können entweder die Schritte 1 bis 4 ausführen, um einen neuen Configuration Container zu erstellen und eine Adobe Sign-Konfiguration im Container zu erstellen, oder den vorhandenen `global` Ordner unter **Tools** ![Hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign** verwenden. Wenn Sie die Konfiguration im neuen Configuration Container erstellen, geben Sie beim Erstellen eines adaptiven Formulars den Container im Feld **[!UICONTROL Configuration Container]** an.

   >[!NOTE]
   Vergewissern Sie sich, dass die URL der Cloud-Dienste-Konfigurationsseite mit **HTTPS** beginnt. Ist dies nicht der Fall, [aktivieren Sie SSL](/help/sites-administering/ssl-by-default.md) für AEM Forms-Server.

1. On the configuration page, tap **[!UICONTROL Create]** to create Adobe Sign configuration in AEM Forms.
1. In the **[!UICONTROL General]** tab of the **[!UICONTROL Create Adobe Sign Configuration]** page, specify a **Name** for the configuration and tap **Next**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browserfenster auf ein Notizblock. Es ist erforderlich, die Adobe Sign-Anwendung mit AEM Forms zu konfigurieren.

1. Konfigurieren Sie OAuth-Einstellungen für die Adobe Sign-Anwendung:

   1. Öffnen Sie ein Browserfenster und melden Sie sich beim Adobe Sign-Entwicklerkonto an.
   1. Wählen Sie die für AEM Forms konfigurierte Anwendung aus und tippen Sie auf „OAuth für Anwendung konfigurieren“.
   1. Fügen Sie im Feld **Umleitungs-URL** die im vorherigen Schritt kopierte HTTPS-URL ein, und klicken Sie dann auf **Speichern**.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für die Anwendung Adobe Sign und klicken Sie auf **Speichern**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für eine Adobe Sign-Anwendung und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation [Konfigurieren von oAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

1. Kehren Sie zur Seite **Adobe Sign-Konfiguration erstellen** zurück. Auf der Registerkarte **[!UICONTROL Einstellungen]** wird im Feld **[!UICONTROL OAuth URL]** die folgende Standard-URL angegeben:

   https://secure.na1.echosign.com/public/oauth

   hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard.

   Sie können den Wert für die Datenbank-Shard ändern. Starten Sie den Server neu, um den neuen Wert für die Datenbank-Shard verwenden zu können.

1. Specify the **Client ID** (also referred to as Application ID) and **Client Secret**. Wählen Sie die Option **Adobe Sign auch für Anhänge aktivieren**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes Adobe Sign-Dokument, das zum Signiren geschickt wurde, anzuhängen.

   Tap **[!UICONTROL Connect to Adobe Sign]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen Benutzername und Kennwort des Kontos an, das bei der Erstellung der Adobe Sign-Anwendung verwendet wurde.

   Tippen Sie auf **[!UICONTROL Erstellen]**, um die Adobe Sign-Konfiguration zu erstellen.

1. Öffnen Sie die AEM Web-Konsole. The URL is `https://'[server]:[port]'/system/console/configMgr`
1. Öffnen Sie **Forms Common-Konfigurationsdienst.** 
1. In the **Allow** field, **select** All users - All the users, anonymous or logged in, can preview attachments, verify and sign forms, and click **Save.** Autoreninstanz ist konfiguriert, um Aobe Sign zu verwenden.
1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie die [Replizierung](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/replication.html) , um eine identische Konfiguration für entsprechende Veröffentlichungsinstanzen zu erstellen.

Jetzt ist Adobe Sign in AEM Forms integriert und kann in adaptiven Formularen verwendet werden. Um [Adobe Sign service in einem adaptiven Formular zu nutzen](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den Konfigurationscontainer an, der oben in den Einstellungen für adaptive Formulare erstellt wurde.



## Konfigurieren Sie den Adobe Sign-Scheduler-Dienst, um den Signaturstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein Adobe Sign-aktivirtes adaptives Formular wird nur gesendet, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig werden die Adobe Sign-Scheduler-Dienste geplant, um die Unterzeichnerantwort alle 24 Stunden zu überprüfen. Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie die folgenden Schritte aus, um das Standardintervall zu ändern:

1. Melden Sie sich beim AEM Forms-Server mit den Admin-Anmeldedaten an und navigieren Sie zu **Tools**> **Vorgänge**> **Web-Konsole**.

   Sie können auch die folgende URL in einem Browserfenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen und öffnen Sie die Option **Adobe Sign-Konfigurationsdienst**. Geben Sie einen[ Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **Status-Aktualisierungs-Scheduler-Ausdruck** und klicken Sie auf **Speichern**. Um beispielsweise den Konfigurationsdienst täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im Ausdruck **&quot;** Statusupdate-Planung&quot;an.

Das Standardintervall für den Synchronisationsstatus von Adobe Sign wurde geändert.

## Related Articles {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integrieren von Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)

