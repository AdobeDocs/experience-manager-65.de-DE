---
title: Integrieren von Adobe Sign mit AEM Forms
seo-title: Integrate Adobe Sign with AEM Forms
description: Erfahren Sie, wie Sie Adobe Sign für AEM Forms konfigurieren
seo-description: Learn how to configure Adobe Sign for AEM Forms
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
feature: Adaptive Forms, Adobe Sign
exl-id: 52146038-1582-41b8-aee0-215d04bb91d7
source-git-commit: 51801dfae47e82f31042f48b113332783464bafb
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 46%

---

# Integrieren [!DNL Adobe Sign] mit AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] aktiviert Workflows für die elektronische Signatur für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In der [!DNL Adobe Sign] und adaptiven Formularen ein Benutzer ein adaptives Formular ausfüllt, um **Dienstanmeldung**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Sign] als genehmigt. Um ähnliche Workflows für elektronische Signaturen zu aktivieren, können Sie [!DNL Adobe Sign] mit AEM [!DNL Forms].

Verwendung [!DNL Adobe Sign] mit AEM [!DNL Forms], konfigurieren [!DNL Adobe Sign] in AEM Cloud Services:

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes zur Integration [!DNL Adobe Sign] mit AEM [!DNL Forms]:

* Ein gültiges [Adobe Sign-Entwicklerkonto.](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html)
* Ein [SSL aktiviert](/help/sites-administering/ssl-by-default.md) AEM [!DNL Forms] Server.
* Eine [Adobe Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Anmeldeinformationen (Client-ID und Client Secret) der [!DNL Adobe Sign]-API-Anwendung.
* Entfernen Sie bei der Neukonfiguration das vorhandene [!DNL Adobe Sign] -Konfiguration von der Autoren- und der Veröffentlichungsinstanz aus.
* Verwenden Sie [identische Schlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) für Autoren- und Veröffentlichungsinstanzen.

## Konfigurieren [!DNL Adobe Sign] mit AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Nachdem die Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL Adobe Sign] mit AEM [!DNL Forms] in der -Autoreninstanz:

1. Bei AEM [!DNL Forms] Autoreninstanz, navigieren Sie zu **Instrumente** ![Hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurationsbrowser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurationscontainer für Cloud-Dienste erstellt.
1. Navigieren Sie zu **Instrumente** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** und wählen Sie den Konfigurationscontainer aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Sie können die Schritte 1 bis 4 ausführen, um einen neuen Konfigurationscontainer zu erstellen und eine [!DNL Adobe Sign] Konfiguration im Container oder die vorhandene `global` Ordner in **Instrumente** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Wenn Sie die Konfiguration im neuen Konfigurationscontainer erstellen, stellen Sie sicher, dass Sie den Container-Namen im **[!UICONTROL Konfigurations-Container]** Feld beim Erstellen eines adaptiven Formulars.

   >[!NOTE]
   Vergewissern Sie sich, dass die URL der Cloud-Dienste-Konfigurationsseite mit **HTTPS** beginnt. Wenn nicht, [SSL aktivieren](/help/sites-administering/ssl-by-default.md) für AEM [!DNL Forms] Server.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]** erstellen [!DNL Adobe Sign] Konfiguration in AEM [!DNL Forms].
1. Im **[!UICONTROL Allgemein]** des **[!UICONTROL Adobe Sign-Konfiguration erstellen]** Seite, geben Sie eine **[!UICONTROL Name]** für die Konfiguration und tippen Sie auf **[!UICONTROL Nächste]**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Sie müssen [!DNL Adobe Sign] Anwendung mit AEM[!DNL Forms].

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm:

   1. Öffnen Sie ein Browserfenster und melden Sie sich bei der [!DNL Adobe Sign] Entwicklerkonto.
   1. Wählen Sie die Anwendung aus, die für AEM konfiguriert ist. [!DNL Forms]und tippen Sie auf **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Kopieren Sie die **[!UICONTROL Client-ID]** und **[!UICONTROL Client Secret]** zu einem Notebook hinzufügen.
   1. Im **[!UICONTROL Umleitungs-URL]** Fügen Sie die im vorherigen Schritt kopierte HTTPS-URL hinzu.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm und klicken Sie auf **[!UICONTROL Speichern]**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

1. Kehren Sie zur Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** zurück. Im **[!UICONTROL Einstellungen]** Registerkarte, die **[!UICONTROL OAuth-URL]** -Feld gibt die Standard-URL an. Das Format der URL ist:

   `https://<shard>/public/oAuth/v2`

   Beispiel:
   `https://secure.na1.echosign.com/public/oauth/v2`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard.

   Sie können den Wert für die Datenbank-Shard ändern. Starten Sie den Server neu, um den neuen Wert für die Datenbank-Shard verwenden zu können.

   >[!NOTE]
   Stellen Sie sicher, dass die Konfigurationen der Autoren- und Veröffentlichungsinstanz auf dieselbe Shard verweisen. Wenn Sie mehrere Adobe Sign-Konfigurationen für eine Organisation erstellen, stellen Sie sicher, dass alle Konfigurationen denselben SHARD verwenden.

1. Geben Sie die **Client-ID** (auch als Anwendungs-ID bezeichnet) und **Client Secret** in Schritt 8 abgeschlossen. Wählen Sie die Option **[!UICONTROL auch für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes Adobe Sign-Dokument, das zum Signiren geschickt wurde, anzuhängen.[!DNL Adobe Sign]

   Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Sign]-Programms verwendet wurden.

   Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration zu erstellen.

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen **[!UICONTROL Forms Common Configuration Service].**
1. Im **[!UICONTROL Zulassen]** -Feld, **select** Alle Benutzer - Alle Benutzer, anonym oder angemeldet, können Anlagen in der Vorschau anzeigen, Formulare überprüfen und signieren und auf **[!UICONTROL Speichern].** Die Autoreninstanz ist für die Verwendung von [!DNL Adobe Sign].
1. Veröffentlichen Sie die Konfiguration.
1. Verwendung [Replikation](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/replication.html) , um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt [!DNL Adobe Sign] ist mit AEM integriert [!DNL Forms] und für die Verwendung in adaptiven Formularen bereit sind. Um [Adobe Sign service in einem adaptiven Formular zu nutzen](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den Konfigurationscontainer an, der oben in den Einstellungen für adaptive Formulare erstellt wurde.



## Konfigurieren [!DNL Adobe Sign] Scheduler zum Synchronisieren des Signaturstatus {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein [!DNL Adobe Sign] aktiviertes adaptives Formular wird nur gesendet, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig wird die [!DNL Adobe Sign] Die Planungsdienste sollen die Signiererantwort alle 24 Stunden überprüfen (abfragen). Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie die folgenden Schritte aus, um das Standardintervall zu ändern:

1. Anmelden bei AEM [!DNL Forms] Server mit Administratorberechtigungen und navigieren Sie zu **Instrumente** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.

   Sie können auch die folgende URL in einem Browserfenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen und öffnen Sie die Option **[!UICONTROL Adobe Sign-Konfigurationsdienst]**. Geben Sie einen[ Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **[!UICONTROL Status-Aktualisierungs-Scheduler-Ausdruck]** und klicken Sie auf **[!UICONTROL Speichern]**. Um beispielsweise den Konfigurationsdienst täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im **[!UICONTROL Ausdruck für Status-Update-Planung]** -Feld.

Standardintervall zum Synchronisieren des Status von [!DNL Adobe Sign] geändert.

## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
