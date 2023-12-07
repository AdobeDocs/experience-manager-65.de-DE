---
title: Integrieren von Adobe Sign mit AEM Forms
description: Erfahren Sie, wie Sie Adobe Sign für Ihre AEM adaptive Forms konfigurieren. Adobe Sign verbessert den Arbeitsablauf und die Verarbeitung der Dokumente in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung und vielen weiteren Bereichen.
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Acrobat Sign
exl-id: 52146038-1582-41b8-aee0-215d04bb91d7
source-git-commit: ab40115c373cc06a7600494288b2670deb914e1a
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 78%

---

# Integrieren von [!DNL Adobe Sign] in AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms.html?lang=en#adobe-acrobat-sign-for-government) |
| AEM 6.5 | Dieser Artikel |

[!DNL Adobe Sign] aktiviert für adaptive Formulare Arbeitsabläufe für E-Signaturen. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Acrobat Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Acrobat Sign] als genehmigt. AEM Forms unterstützt sowohl Adobe Acrobat Sign als auch Adobe Acrobat Sign Solutions für Behörden. Je nach Ihrer Lizenz und Ihren Anforderungen können Sie AEM Forms mit einer der folgenden Lösungen integrieren oder verbinden:

* [Verbinden von AEM Forms mit Adobe Acrobat Sign](#adobe-sign)
* [Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden](#adobe-acrobat-sign-for-government)

## Verbinden von AEM Forms mit Adobe Acrobat Sign {#adobe-sign}

Um **[!DNL AEM Forms]** mit **[!DNL Adobe Acrobat Sign]** zu verbinden, richten Sie die Software und Konten ein, die im Abschnitt „Voraussetzungen“ aufgeführt sind, und verbinden Sie Adobe Sign mit allen Authoring- und Publishing-Instanzen in AEM Forms:

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
1. Im **[!UICONTROL Konfigurationsbrowser]** Seite, auswählen **[!UICONTROL Erstellen]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
1. Im **[!UICONTROL Konfiguration erstellen]** Dialogfeld angeben, **[!UICONTROL Titel]** für die Konfiguration aktivieren **[!UICONTROL Cloud-Konfigurationen]** und wählen Sie **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container erstellt.
1. Navigieren Sie zu **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Sign]** und wählen Sie den Konfigurationscontainer aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Sie können die Schritte 1 bis 4 ausführen, um einen Konfigurationscontainer zu erstellen und eine [!DNL Adobe Sign] Konfiguration im Container oder die vorhandene `global` Ordner in **Instrumente** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL Adobe Sign]**. Wenn Sie die Konfiguration im neuen Konfigurationscontainer erstellen, stellen Sie sicher, dass Sie den Container-Namen im **[!UICONTROL Konfigurations-Container]** beim Erstellen eines adaptiven Formulars ein.

   >[!NOTE]
   >
   Vergewissern Sie sich, dass die URL der Cloud-Services-Konfigurationsseite mit **HTTPS** beginnt. Andernfalls müssen Sie für den AEM [!DNL Forms] Server [SSL aktivieren](/help/sites-administering/ssl-by-default.md). 


1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration in AEM [!DNL Forms] zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.
1. Jetzt haben Sie die Option **[!UICONTROL Lösung auswählen]** und können [!DNL Adobe Acrobat Sign] auswählen.

   ![Adobe Acrobat Sign Solutions](/help/forms/using/assets/adobe-sign-solution.png)

1. Kopieren Sie die URL in das aktuelle Browser-Fenster auf ein Notebook und entfernen Sie den Teil /`ui#/aem` von der URL aus. Die geänderte URL wird benötigt, um in einem späteren Schritt die [!DNL Adobe Acrobat Sign]-Anwendung mit [!DNL AEM Forms] zu konfigurieren. Tippen Sie auf [!UICONTROL Weiter].

1. Im **[!UICONTROL Einstellungen]** Registerkarte,
   * die **[!UICONTROL OAuth-URL]** enthält die Standard-URL, die die Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/public/oauth/v2`

     Beispiel:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * die **[!UICONTROL Zugriffstoken-URL]** enthält die Standard-URL, die die Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/oauth/v2/token`

     Beispiel:
     `https://api.na1.echosign.com/oauth/v2/token`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL  Adobe Acrobat Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   >[!NOTE]
   >
   * Lassen Sie die Seite **Erstellen einer Konfiguration für Adobe Acrobat Sign** geöffnet. Schließen Sie sie nicht. Nachdem Sie die OAuth-Einstellungen für die Anwendung [!DNL Adobe Acrobat Sign] wie in den nächsten Schritten beschrieben konfiguriert haben, können Sie die **Client-ID** und den **geheimen Client-Schlüssel** abrufen.
   * Navigieren Sie nach der Anmeldung bei Ihrem Adobe Sign-Konto zu **[!UICONTROL Acrobat Sign-API]** > **[!UICONTROL API-Informationen]** > **[!UICONTROL Dokumentation zu REST-API-Methoden]** > **[!UICONTROL OAuth-Zugriffstoken]** , um auf Informationen im Zusammenhang mit der OAuth-URL von Adobe Sign und der Zugriffstoken-URL zuzugreifen.

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Sign]-Entwicklerkonto an.
   1. Wählen Sie die Anwendung aus, die für AEM konfiguriert ist. [!DNL Forms]und wählen Sie **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Kopieren Sie **[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]** in ein Notizbuch.
   1. Fügen Sie dem Feld **[!UICONTROL Umleitungs-URL]** die HTTPS-URL hinzu, die Sie im vorherigen Schritt kopiert haben.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm und klicken Sie auf **[!UICONTROL Speichern]**.

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_write
   * workflow_read

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

<!--
1. Go back to the **[!UICONTROL Create Adobe Sign Configuration]** page. In the **[!UICONTROL Settings]** tab, the **[!UICONTROL OAuth URL]** field mentions the  default URL. The format of the URL is:

   `https://<shard>/public/oAuth/v2`

   For example: 
   `https://secure.na1.echosign.com/public/oauth/v2`

   where:

   **na1** refers to the default database shard.

   You can modify the value for the database shard. Restart the server to be able to use the new value for the database shard.

   >[!NOTE]
   >
   >Ensure that your author and publish instance configurations point to the same shard. If you create multiple Adobe Sign configurations for an organization, ensure all the configurations utilize the same shard. -->

1. Kehren Sie zur Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** zurück. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die **Client-ID** (auch als Anwendungs-ID bezeichnet) und den **geheimen Client-Schlüssel** an. Verwenden Sie die [Client-ID und den geheimen Client-Schlüssel der Adobe Sign-Anwendung](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret), den Sie für AEM Forms erstellt haben.

1. Wählen Sie die Option **[!UICONTROL auch für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes Adobe Sign-Dokument, das zum Signiren geschickt wurde, anzuhängen.[!DNL Adobe Sign]

1. Auswählen **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Sign]-Programms verwendet wurden.

   ![Cloud-Konfiguration für Adobe Acrobat Sign erfolgreich](assets/adobe-sign-cloud-configuration-success.png)

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration zu erstellen.
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **[!UICONTROL Forms Common-Konfigurations-Service].**
1. Wählen Sie im Feld **[!UICONTROL Zulassen]** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **[!UICONTROL Speichern].** Autoreninstanz ist konfiguriert, um [!DNL Adobe Sign] zu verwenden.
1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie [Replikation](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html?lang=de), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt ist [!DNL Adobe Sign] mit AEM [!DNL Forms] integriert und kann in adaptiven Formularen verwendet werden. Um [Adobe Sign service in einem adaptiven Formular zu nutzen](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den Konfigurationscontainer an, der oben in den Einstellungen für adaptive Formulare erstellt wurde.

>[!NOTE]
>
Um die Adobe Sign-Sandbox zu konfigurieren, führen Sie dieselben Konfigurationsschritte aus wie unter [Adobe Sign](#adobe-sign).

## Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#adobe-acrobat-sign-for-government}

Das Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden ist ein mehrstufiger Prozess. Er umfasst:

* Erstellen einer Umleitungs-URL für Ihre AEM-Instanzen
* Weitergeben der Umleitungs-URL und des Umfangs an das Team von Adobe Sign Solutions für Behörden
* Erhalten von Anmeldedaten vom Adobe Sign-Team
* Verwenden der erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden

![adobe-acrobat-sign-govt-workflow](/help/forms/using/assets/adobe-acrobat-sign-govt-workflow.png)

### Bevor Sie beginnen {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Bevor Sie mit der Verbindung von AEM Forms mit Adobe Acrobat Sign Solutions beginnen, stellen Sie sicher, dass

* das Konto für [Adobe Acrobat Sign Solutions für Behörden](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) bereitgestellt wurde.
* Ihre AEM [!DNL Forms]-Server [SSL aktiviert](/help/sites-administering/ssl-by-default.md) haben.
* Ihre AEM [!DNL Forms]-Server einen [identischen Kryptoschlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) für Authoring und Publishing-Instanz verwenden.

### Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#connect-adobe-acrobat-sign-for-government}

#### Erstellen einer Umleitungs-URL für Ihre AEM-Instanz

1. Navigieren Sie in Ihrer AEM Forms-Instanz zu **[!UICONTROL Tools]** ![Hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Im **[!UICONTROL Konfigurationsbrowser]** Seite, auswählen **[!UICONTROL Erstellen]**.
1. Im **[!UICONTROL Konfiguration erstellen]** Dialogfeld angeben, **[!UICONTROL Titel]** für die Konfiguration aktivieren **[!UICONTROL Cloud-Konfigurationen]** und wählen Sie **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container erstellt. Achten Sie darauf, dass der Name des Containers/Ordners keine Leerzeichen enthält.

1. Navigieren Sie zu **[!UICONTROL Tools]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** und öffnen Sie den Konfigurations-Container, den Sie im vorherigen Schritt erstellt haben. Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Wählen Sie auf der Konfigurationsseite **[!UICONTROL Erstellen]** erstellen [!DNL Adobe Acrobat Sign] Konfiguration in AEM Forms.
1. Kopieren Sie die URL Ihres aktuellen Browser-Fensters in ein Notepad-Fenster. Diese URL wird als `re-direct URL` bezeichnet. Im nächsten Abschnitt geben Sie `re-direct URL` und `Scopes` für das Adobe Sign-Team frei und fordern die Anmeldeinformationen (Client-ID und Client-Geheimnis) an.

>[!NOTE]
>
>
* Ein `re-direct URL` sollte eine [Top-Level](https://de.wikipedia.org/wiki/Top-Level-Domain)-Domain enthalten. Zum Beispiel: `https://adobe.com/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`
* Verwenden Sie keine lokale URL als `re-direct URL`. Zum Beispiel: `https://localhost:4502/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`.


#### Freigeben der Umleitungs-URL und der Bereiche für das Adobe Sign-Team und Empfangen von Anmeldeinformationen

Das Adobe Acrobat Sign for Government Solutions-Team benötigt `re-direct URL` und die bestimmten Bereiche, die für Ihre Adobe Acrobat Sign-Anwendung aktiviert werden sollen (siehe unten), um Anmeldeinformationen (Client-ID und Client-Geheimnis) zu generieren, über die Sie AEM Forms mit Adobe Acrobat Sign Solutions für Behörden verbinden können.

Geben Sie die `scopes` (unten aufgelistet) und die `re-direct URL`, die Sie im letzten Schritt des vorherigen Abschnitts erstellt und notiert haben, an Ihre [Ansprechperson im Adobe Professional Services-Team](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password) für Adobe Acrobat Sign Solutions für Behörden weiter.

**_Bereiche_**

* [!DNL agreement_read]
* [!DNL agreement_write]
* [!DNL agreement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

Die Kontaktperson generiert Anmeldeinformationen und teilt Ihnen diese mit. Im nächsten Abschnitt verwenden Sie die Anmeldeinformationen (Client-ID und Client-Geheimnis), um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden.

#### Verwenden Sie die erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden.

1. Öffnen Sie die `re-direct URL` in Ihrem Browser. Sie haben die `re-direct URL` im letzten Schritt des Abschnitts [Erstellen einer Umleitungs-URL in Ihrer AEM-Instanz](#create-redirect-url) erstellt und notiert.

1. Im **[!UICONTROL Allgemein]** des **[!UICONTROL Adobe Sign-Konfiguration erstellen]** Seite, geben Sie eine **[!UICONTROL Name]** für die Konfiguration und wählen Sie **[!UICONTROL Nächste]**. Sie können optional einen **[!UICONTROL Titel]** angeben und eine **[!UICONTROL Miniaturansicht]** für die Konfiguration suchen. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** für **[!UICONTROL Lösung auswählen]** die Option [!DNL Adobe Acrobat Sign Solutions for Government] aus.

   ![Adobe Acrobat Sign Solutions für Behörden](/help/forms/using/assets/adobe-sign-for-govt.png)

1. Im **[!UICONTROL Email]** Geben Sie die E-Mail-Adresse an, die mit Ihrem Adobe Acrobat Sign Solutions for Government-Konto verknüpft ist.

1. Im **[!UICONTROL Einstellungen]** Registerkarte,
   * die **[!UICONTROL OAuth-URL]** enthält die Standard-URL, die die Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Beispiel:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * die **[!UICONTROL Zugriffstoken-URL]** enthält die Standard-URL, die die Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Beispiel:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL  Adobe Acrobat Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   >[!NOTE]
   >
   * Navigieren Sie nach der Anmeldung bei Ihrem Adobe Sign-Konto zu **[!UICONTROL Acrobat Sign-API]** > **[!UICONTROL API-Informationen]** > **[!UICONTROL Dokumentation zu REST-API-Methoden]** > **[!UICONTROL OAuth-Zugriffstoken]** , um auf Informationen im Zusammenhang mit der OAuth-URL von Adobe Sign und der Zugriffstoken-URL zuzugreifen.

1. Verwenden Sie die Anmeldeinformationen, die die Kontaktperson für Adobe Acrobat Sign for Government Solutions ([Mitglied des Adobe Professional Services-Teams]) im vorherigen Abschnitt als [**[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]**] geteilt hat.

1. Wählen Sie die Option **[!UICONTROL Adobe Acrobat Sign für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes [!DNL Adobe Acrobat Sign]-Dokument anzuhängen, das zum Signieren versandt wird.

1. Auswählen **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung der [!DNL Adobe Acrobat Sign]-Anwendung verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `Adobe Acrobat Sign for Government Solutions` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Adobe Acrobat Sign-Cloud-Konfiguration erfolgreich](/help/forms/using/assets/adobe-sign-cloud-configuration-success.png)

   Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung der [!DNL Adobe Acrobat Sign]-Anwendung verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `your account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**.

1. Auswählen **[!UICONTROL Erstellen]** , um die Konfiguration zu erstellen.
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **[!UICONTROL Forms Common-Konfigurations-Service].**
1. Wählen Sie im Feld **[!UICONTROL Zulassen]** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **[!UICONTROL Speichern].** Autoreninstanz ist konfiguriert, um [!DNL Adobe Sign] zu verwenden.

1. Veröffentlichen Sie die Konfiguration.
1. Verwenden Sie [Replikation](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html?lang=de), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt können Sie [Felder mit Adobe Acrobat Sign in einem adaptiven Formular](working-with-adobe-sign.md) oder [AEM-Workflow](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step) verwenden. Stellen Sie sicher, dass Sie den für die Cloud-Service-Konfiguration verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL Adobe Acrobat Sign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.


## Konfigurieren des [!DNL Adobe Sign]-Scheduler-Service, um den Signaturstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein [!DNL Adobe Sign]-fähiges adaptives Formular wird nur übermittelt, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig werden die [!DNL Adobe Sign]-Scheduler-Services so geplant, dass sie die Unterzeichnerantwort alle 24 Stunden abfragen. Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie zum Anpassen des Standardintervalls folgende Schritte durch:

1. Melden Sie sich beim AEM [!DNL Forms]-Server mit den Admin-Anmeldedaten an und gehen Sie zu **Tools** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   Sie können auch folgende URL in einem Browser-Fenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen Sie die Option **[!UICONTROL Adobe Sign-Konfigurationsdienst]** und öffnen Sie sie. Geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **[!UICONTROL Status-Aktualisierungs-Scheduler-Ausdruck]** und klicken Sie auf **[!UICONTROL Speichern]**. Um beispielsweise den Konfigurations-Service täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im Feld **[!UICONTROL Ausdruck für Status-Update-Planung]** an.

Das Standardintervall für den Synchronisationsstatus von [!DNL Adobe Sign] wurde jetzt geändert.

## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign mit formularorientierten Workflows](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)
* [Verwenden von Adobe Sign mit AEM Forms (Video)](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/forms-and-sign/introduction.html?lang=de)
