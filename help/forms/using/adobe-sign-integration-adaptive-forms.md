---
title: Integrieren von Adobe Sign mit AEM Forms
seo-title: Integrate Adobe Sign with AEM Forms
description: Erfahren Sie, wie Sie Adobe Sign für AEM Forms konfigurieren.
seo-description: Learn how to configure Adobe Sign for AEM Forms
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
feature: Adaptive Forms, Acrobat Sign
exl-id: 52146038-1582-41b8-aee0-215d04bb91d7
source-git-commit: 8f2c8964c2a6c2f0fcb446b7bca1f8cb822906f7
workflow-type: tm+mt
source-wordcount: '1972'
ht-degree: 62%

---

# Integrieren von [!DNL Adobe Sign] in AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] aktiviert für adaptive Formulare Arbeitsabläufe für E-Signaturen. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Acrobat Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Acrobat Sign] als genehmigt. AEM Forms unterstützt sowohl Adobe Acrobat Sign als auch Adobe Acrobat Sign Solutions for Government. Abhängig von Ihrer Lizenz und Ihren Anforderungen können Sie AEM Forms mit einer der folgenden Lösungen integrieren oder verbinden:

* [Verbinden von AEM Forms mit Adobe Acrobat Sign](#adobe-sign)
* [Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden](#adobe-acrobat-sign-for-government)

## Verbinden von AEM Forms mit Adobe Acrobat Sign {#adobe-sign}

Verbindung herstellen **[!DNL AEM Forms]** mit **[!DNL Adobe Acrobat Sign]**, richten Sie die im Abschnitt &quot;Voraussetzungen&quot;aufgelistete Software und Konten ein und verbinden Sie Adobe Sign mit allen AEM Forms-Autoren- und Veröffentlichungsinstanzen:

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
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container erstellt.
1. Navigieren Sie zu **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Sign]** und wählen Sie den Konfigurationscontainer aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Sie können die Schritte 1 bis 4 ausführen, um einen neuen Konfigurationscontainer und eine [!DNL Adobe Sign]-Konfiguration im Container zu erstellen, oder den vorhandenen Ordner `global` in **Tools** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Sign]** verwenden. Wenn Sie die Konfiguration im neuen Konfigurations-Container erstellen, dürfen Sie beim Erstellen eines adaptiven Formulars nicht vergessen, den Container-Namen im Feld **[!UICONTROL Konfigurations-Container]** anzugeben.

   >[!NOTE]
   >
   Stellen Sie sicher, dass die URL der Cloud Services-Konfigurationsseite mit **HTTPS**. Andernfalls müssen Sie für den AEM [!DNL Forms] Server [SSL aktivieren](/help/sites-administering/ssl-by-default.md). 

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration in AEM [!DNL Forms] zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Es ist erforderlich, das Programm [!DNL Adobe Sign] mit AEM [!DNL Forms] zu konfigurieren.

1. Auf der Registerkarte **[!UICONTROL Einstellungen]** enthält das Feld **[!UICONTROL OAuth URL]** die Standard-URL. Das Format der URL ist:

   `https://<shard>/public/oAuth/v2`

   Beispiel:
   `https://secure.na1.echosign.com/public/oauth/v2`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL  Adobe Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   Wenn Sie eine weitere [!DNL Adobe Sign]-Konfiguration für eine Funktion oder Komponente von Adobe Experience Manager erstellen, vergewissern Sie sich, dass alle [!DNL Adobe Sign]-Cloud-Konfigurationen auf dieselbe Shard verweisen.

   >[!NOTE]
   >
   Lassen Sie die Seite **Adobe Sign-Konfiguration erstellen** geöffnet. Schließen Sie sie nicht. Nachdem Sie die OAuth-Einstellungen für die Anwendung [!DNL Adobe Sign] wie in den nächsten Schritten beschrieben konfiguriert haben, können Sie die **Client-ID** und den **geheimen Client-Schlüssel** abrufen.


1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Sign]-Entwicklerkonto an.
   1. Wählen Sie das für AEM [!DNL Forms] konfigurierte Programm aus und tippen Sie auf **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Kopieren Sie **[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]** in ein Notizbuch.
   1. Fügen Sie dem Feld **[!UICONTROL Umleitungs-URL]** die HTTPS-URL hinzu, die Sie im vorherigen Schritt kopiert haben.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm und klicken Sie auf **[!UICONTROL Speichern]**.

   * Agreement_read
   * Agreement_write
   * Agreement_send
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
   >
   Stellen Sie sicher, dass die Konfigurationen der Autoren- und Veröffentlichungsinstanz auf dieselbe Shard verweisen. Wenn Sie mehrere Adobe Sign-Konfigurationen für eine Organisation erstellen, stellen Sie sicher, dass alle Konfigurationen dieselbe Shard verwenden.

1. Kehren Sie zur Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** zurück. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die **Client-ID** (auch als Anwendungs-ID bezeichnet) und den **geheimen Client-Schlüssel** an. Verwenden Sie die [Client-ID und den geheimen Client-Schlüssel der Adobe Sign-Anwendung](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret), den Sie für AEM Forms erstellt haben.

1. Wählen Sie die Option **[!UICONTROL auch für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes Adobe Sign-Dokument, das zum Signiren geschickt wurde, anzuhängen.[!DNL Adobe Sign]

1. Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Sign]-Programms verwendet wurden.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration zu erstellen.

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **[!UICONTROL Forms Common-Konfigurations-Service].**
1. Wählen Sie im Feld **[!UICONTROL Zulassen]** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **[!UICONTROL Speichern].** Autoreninstanz ist konfiguriert, um [!DNL Adobe Sign] zu verwenden.
1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie [Replikation](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html?lang=de), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt ist [!DNL Adobe Sign] mit AEM [!DNL Forms] integriert und kann in adaptiven Formularen verwendet werden. Um [Adobe Sign service in einem adaptiven Formular zu nutzen](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den Konfigurationscontainer an, der oben in den Einstellungen für adaptive Formulare erstellt wurde.

## Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#adobe-acrobat-sign-for-government}

Die Verbindung von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden ist ein mehrstufiger Prozess. Er umfasst:

* Erstellen der Umleitungs-URL für Ihre AEM-Instanzen
* Freigeben der Umleitungs-URL und des Umleitungs-Umfangs für Adobe Sign Solutions for Government-Teams
* Anmeldeinformationen vom Adobe Sign-Team erhalten
* Verwenden der erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden

![](/help/forms/using/assets/adobe-acrobat-sign-govt-workflow.png)

### Bevor Sie beginnen {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Bevor Sie mit der Verbindung von AEM Forms mit der Adobe Acrobat Sign-Lösung beginnen,

* Stellen Sie sicher, dass [Adobe Acrobat Sign Solutions für Regierungsbehörden](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) -Konto bereitgestellt wurde.
* Ihre AEM [!DNL Forms] -Server [SSL aktiviert](/help/sites-administering/ssl-by-default.md) .
* Ihre AEM [!DNL Forms] -Server verwenden [identischer Kryptoschlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) für Autoren- und Veröffentlichungsinstanzen.

### Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#connect-adobe-acrobat-sign-for-government}

#### Erstellen einer Umleitungs-URL für Ihre AEM-Instanz

1. Navigieren Sie in Ihrer AEM Forms-Instanz zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurationsbrowser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container erstellt. Stellen Sie sicher, dass der Container-/Ordnername kein Leerzeichen enthält.

1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Schritt erstellt haben. Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration in AEM Forms zu erstellen.
1. Kopieren Sie die URL Ihres aktuellen Browserfensters aus der URL in ein Notizblock. Diese URL wird als `re-direct URL`. Im nächsten Abschnitt teilen Sie die `re-direct URL` und `Scopes` mit Adobe Sign-Team und Anforderungsberechtigungen (Client-ID und Client-Geheimnis).

>[!NOTE]
>
>
* A `re-direct URL` sollte [Top-Level](https://en.wikipedia.org/wiki/Top-level_domain) Domäne. Beispiel: `https://adobe.com/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`
* Verwenden Sie keine lokale URL als `re-direct URL`. Beispiel: `https://localhost:4502/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`.


#### Freigeben der Umleitungs-URL und der Bereiche für das Adobe Sign-Team und Empfangen von Anmeldeinformationen

Das Adobe Acrobat Sign for Government Solutions-Team benötigt `re-direct URL` und die bestimmten Bereiche, die für Ihre Adobe Acrobat Sign-Anwendung aktiviert werden sollen (siehe unten), um Anmeldeinformationen (Client-ID und Client-Geheimnis) zu generieren, mit denen Sie AEM Forms mit Adobe Acrobat Sign Solutions für Behörden verbinden können.

Freigeben von `scopes` (siehe unten) und die `re-direct URL` den letzten Schritt des vorherigen Abschnitts mit Ihrem Adobe Acrobat Sign for Government Solution-Support-Mitarbeiter erstellt und vermerkt haben [Adobe Professional Services-Teammitglied](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password).

**_Bereiche_**

* [!DNL agreement_read]
* [!DNL agreement_write]
* [!DNL agreement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

Der Support-Mitarbeiter generiert Anmeldeinformationen und gibt diese für Sie frei. Im nächsten Abschnitt verwenden Sie die Anmeldeinformationen (Client-ID und Client-Geheimnis), um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden.

#### Verwenden Sie die erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden.

1. Öffnen Sie die `re-direct URL` in Ihrem Browser. Sie haben die `re-direct URL` im letzten Schritt des [Erstellen einer Umleitungs-URL auf Ihrer AEM-Instanz](#create-redirect-url) Abschnitt.

1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen **[!UICONTROL Titel]** angeben und durchsuchen, um ein **[!UICONTROL Miniaturbild]** für die Konfiguration auszuwählen. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Im **[!UICONTROL Einstellungen]** des **[!UICONTROL Adobe Sign-Konfiguration erstellen]** für die **[!UICONTROL Lösung auswählen]** auswählen [!DNL Adobe Acrobat Sign Solutions for Government].

   ![Adobe Acrobat Sign Solutions für Regierungsbehörden](/help/forms/using/assets/adobe-sign-for-govt.png)

1. Im **[!UICONTROL Email]** eingeben, geben Sie die E-Mail-Adresse an, die mit Ihrem Adobe Acrobat Sign Solutions for Government-Konto verknüpft ist.

1. Die **[!UICONTROL OAuth-URL]** gibt die Adobe Sign-Datenbank-Shard an. Das Feld enthält die Standard-URL. Ändern Sie die URL nicht.

1. Verwenden Sie die Anmeldeinformationen, die von Adobe Acrobat Sign für den Support-Mitarbeiter der Regierungslösung ([Adobe Professional Services-Teammitglied]) im vorherigen Abschnitt als [**[!UICONTROL Client-ID]** und **[!UICONTROL Client Secret]**].

1. Wählen Sie die **[!UICONTROL Adobe Acrobat Sign für Anlagen aktivieren]** Option zum Anhängen von Dateien, die an ein adaptives Formular angehängt sind, an die entsprechende [!DNL Adobe Acrobat Sign] Dokument zum Signieren gesendet.

1. Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen Benutzername und Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Acrobat Sign]-Programms verwendet wurden. Bei Aufforderung zur Bestätigung des Zugriffs auf `Adobe Acrobat Sign for Government Solutions` und klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Erfolg der Adobe Acrobat Sign Cloud-Konfiguration](/help/forms/using/assets/adobe-sign-cloud-configuration-success.png)

   Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Acrobat Sign]-Programms verwendet wurden. Bei Aufforderung zur Bestätigung des Zugriffs auf `your account`und klicken Sie auf **[!UICONTROL Zugriff erlauben]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die -Konfiguration zu erstellen.
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **[!UICONTROL Forms Common-Konfigurations-Service].**
1. Wählen Sie im Feld **[!UICONTROL Zulassen]** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **[!UICONTROL Speichern].** Autoreninstanz ist konfiguriert, um [!DNL Adobe Sign] zu verwenden.

1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie [Replikation](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html?lang=de), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt können Sie [Adobe Acrobat Sign-Felder in einem adaptiven Formular hinzufügen](working-with-adobe-sign.md) oder [AEM Workflow](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Stellen Sie sicher, dass Sie den für die Cloud Service-Konfiguration verwendeten Konfigurationscontainer zu allen adaptiven Forms hinzufügen, für die die Option aktiviert ist [!DNL Adobe Acrobat Sign]. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.


## Konfigurieren des [!DNL Adobe Sign]-Scheduler-Service, um den Signaturstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein [!DNL Adobe Sign]-fähiges adaptives Formular wird nur übermittelt, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig werden die [!DNL Adobe Sign]-Scheduler-Services so geplant, dass sie die Unterzeichnerantwort alle 24 Stunden abfragen. Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie zum Anpassen des Standardintervalls folgende Schritte durch:

1. Melden Sie sich beim AEM [!DNL Forms]-Server mit den Admin-Anmeldedaten an und gehen Sie zu **Tools** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   Sie können auch folgende URL in einem Browser-Fenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen und öffnen Sie die **[!UICONTROL Adobe Sign Configuration Service]** -Option. Geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **[!UICONTROL Status-Aktualisierungs-Scheduler-Ausdruck]** und klicken Sie auf **[!UICONTROL Speichern]**. Um beispielsweise den Konfigurations-Service täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im Feld **[!UICONTROL Ausdruck für Status-Update-Planung]** an.

Das Standardintervall für den Synchronisationsstatus von [!DNL Adobe Sign] wurde jetzt geändert.

## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign mit formularzentrierten Workflows](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/forms-and-sign/introduction.html?lang=de)
