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
workflow-type: ht
source-wordcount: '951'
ht-degree: 100%

---

# Integrieren von [!DNL Adobe Sign] in AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] aktiviert für adaptive Formulare Arbeitsabläufe für E-Signaturen. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um **einen Service zu beantragen**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Sign] als genehmigt. Sie können [!DNL Adobe Sign] in AEM [!DNL Forms] integrieren, um ähnliche Workflows für elektronische Signaturen zu ermöglichen.

Um [!DNL Adobe Sign] mit AEM [!DNL Forms] zu verwenden, konfigurieren Sie [!DNL Adobe Sign] in AEM Cloud Services:

## Voraussetzungen {#prerequisites}

Für die Integration von [!DNL Adobe Sign] in AEM [!DNL Forms] benötigen Sie Folgendes:

* Ein gültiges [Adobe Sign-Entwicklerkonto.](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html)
* Einen AEM [!DNL Forms]-Server, auf dem [SSL aktiviert](/help/sites-administering/ssl-by-default.md) ist.
* Eine [Adobe Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Anmeldeinformationen (Client-ID und Client Secret) der [!DNL Adobe Sign]-API-Anwendung.
* Entfernen Sie bei der Neukonfiguration die vorhandene [!DNL Adobe Sign]-Konfiguration sowohl aus der Autoren- als auch aus der Veröffentlichungsinstanz.
* Verwenden Sie [identische Schlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) für Autoren- und Veröffentlichungsinstanzen.

## Konfigurieren von [!DNL Adobe Sign] mit AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Nachdem die Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL Adobe Sign] mit AEM [!DNL Forms] in der Autoreninstanz zu konfigurieren:

1. Navigieren Sie in der AEM [!DNL Forms]-Autoreninstanz zu **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemeinl]** > **[!UICONTROL Konfigurations-Browser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurationscontainer für Cloud-Dienste erstellt.
1. Navigieren Sie zu **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Sign]** und wählen Sie den Konfigurationscontainer aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Sie können die Schritte 1 bis 4 ausführen, um einen neuen Konfigurationscontainer und eine [!DNL Adobe Sign]-Konfiguration im Container zu erstellen, oder den vorhandenen Ordner `global` in **Tools** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Sign]** verwenden. Wenn Sie die Konfiguration im neuen Konfigurations-Container erstellen, dürfen Sie beim Erstellen eines adaptiven Formulars nicht vergessen, den Container-Namen im Feld **[!UICONTROL Konfigurations-Container]** anzugeben.

   >[!NOTE]
   Vergewissern Sie sich, dass die URL der Cloud-Dienste-Konfigurationsseite mit **HTTPS** beginnt. Andernfalls müssen Sie für den AEM [!DNL Forms] Server [SSL aktivieren](/help/sites-administering/ssl-by-default.md). 

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration in AEM [!DNL Forms] zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Es ist erforderlich, das Programm [!DNL Adobe Sign] mit AEM [!DNL Forms] zu konfigurieren.

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Sign]-Entwicklerkonto an.
   1. Wählen Sie das für AEM [!DNL Forms] konfigurierte Programm aus und tippen Sie auf **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Kopieren Sie **[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]** in ein Notizbuch.
   1. Fügen Sie dem Feld **[!UICONTROL Umleitungs-URL]** die HTTPS-URL hinzu, die Sie im vorherigen Schritt kopiert haben.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm und klicken Sie auf **[!UICONTROL Speichern]**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

1. Kehren Sie zur Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** zurück. Auf der Registerkarte **[!UICONTROL Einstellungen]** wird im Feld **[!UICONTROL OAuth URL]** die folgende Standard-URL angegeben. Das Format der URL ist:

   `https://<shard>/public/oAuth/v2`

   Beispiel:
   `https://secure.na1.echosign.com/public/oauth/v2`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard.

   Sie können den Wert für die Datenbank-Shard ändern. Starten Sie den Server neu, um den neuen Wert für die Datenbank-Shard verwenden zu können.

   >[!NOTE]
   Stellen Sie sicher, dass die Konfigurationen der Autoren- und Veröffentlichungsinstanz auf dieselbe Shard verweisen. Wenn Sie mehrere Adobe Sign-Konfigurationen für eine Organisation erstellen, stellen Sie sicher, dass alle Konfigurationen dieselbe Shard verwenden.

1. Geben Sie die **Client-ID** (auch als Anwendungs-ID bezeichnet) und das in Schritt 8 kopierte **Client-Geheimnis** an. Wählen Sie die Option **[!UICONTROL auch für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes Adobe Sign-Dokument, das zum Signiren geschickt wurde, anzuhängen.[!DNL Adobe Sign]

   Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Sign]-Programms verwendet wurden.

   Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration zu erstellen.

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **[!UICONTROL Forms Common-Konfigurations-Service].**
1. Wählen Sie im Feld **[!UICONTROL Zulassen]** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **[!UICONTROL Speichern].** Autoreninstanz ist konfiguriert, um [!DNL Adobe Sign] zu verwenden.
1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie [Replikation](https://docs.adobe.com/content/help/de/experience-manager-65/deploying/configuring/replication.html), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt ist [!DNL Adobe Sign] mit AEM [!DNL Forms] integriert und kann in adaptiven Formularen verwendet werden. Um [Adobe Sign service in einem adaptiven Formular zu nutzen](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den Konfigurationscontainer an, der oben in den Einstellungen für adaptive Formulare erstellt wurde.



## Konfigurieren des [!DNL Adobe Sign]-Scheduler-Service, um den Signaturstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein [!DNL Adobe Sign]-fähiges adaptives Formular wird nur übermittelt, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig werden die [!DNL Adobe Sign]-Scheduler-Services so geplant, dass sie die Unterzeichnerantwort alle 24 Stunden abfragen. Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie zum Anpassen des Standardintervalls folgende Schritte durch:

1. Melden Sie sich beim AEM [!DNL Forms]-Server mit den Admin-Anmeldedaten an und gehen Sie zu **Tools** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   Sie können auch folgende URL in einem Browser-Fenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen und öffnen Sie die Option **[!UICONTROL Adobe Sign-Konfigurationsdienst]**. Geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **[!UICONTROL Status-Aktualisierungs-Scheduler-Ausdruck]** und klicken Sie auf **[!UICONTROL Speichern]**. Um beispielsweise den Konfigurations-Service täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im Feld **[!UICONTROL Ausdruck für Status-Update-Planung]** an.

Das Standardintervall für den Synchronisationsstatus von [!DNL Adobe Sign] wurde jetzt geändert.

## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/forms-and-sign/introduction.html?lang=de)
