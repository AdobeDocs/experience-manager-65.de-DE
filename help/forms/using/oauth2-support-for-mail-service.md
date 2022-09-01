---
title: OAuth2-Unterstützung für den E-Mail-Service
description: 'OAuth2-Unterstützung für den E-Mail-Dienst  '
source-git-commit: 9ee8e79777b89fbf4d6e5b5fd1dbb1ef3bc9ad5d
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 47%

---

# OAuth2-Unterstützung für den E-Mail-Service {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service bietet OAuth2-Unterstützung für seinen integrierten E-Mail-Service, um Unternehmen die Einhaltung E-Mail-Sicherheitsanforderungen zu ermöglichen.

Sie können OAuth für mehrere E-Mail-Anbieter konfigurieren. Im Folgenden finden Sie eine schrittweise Anleitung zum Konfigurieren des AEM E-Mail-Service für die Authentifizierung über OAuth2 mit Microsoft Office 365 Outlook. Andere Anbieter können auf ähnliche Weise konfiguriert werden.

## Microsoft Outlook {#microsoft-outlook}

1. Gehen Sie zu [https://portal.azure.com/](https://portal.azure.com/) und melden Sie sich an.
1. Suchen Sie in der Suchleiste nach **Azure Active Directory** und klicken Sie auf das Ergebnis. Alternativ können Sie direkt zu [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) gehen.
1. Klicken Sie auf **Registrierung einer Anwendung** – **Neue Registrierung**

   ![](/help/forms/using/assets/outh_outlook.PNG)

1. Füllen Sie die Informationen entsprechend Ihren Anforderungen aus und klicken Sie dann auf **Registrieren**
1. Wechseln Sie zur neu erstellten Anwendung und wählen Sie **API-Berechtigungen** aus.
1. Gehen Sie zu **Berechtigung hinzufügen** – **Diagrammberechtigungen** – **Zugewiesene Berechtigungen**.
1. Wählen Sie die folgenden Berechtigungen für Ihre Anwendung aus und klicken Sie dann auf **Berechtigung hinzufügen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Gehen Sie zu **Authentifizierung** – **Plattform hinzufügen** – **Web** und fügen Sie im Abschnitt **URLs umleiten** die folgenden URLs hinzu – eine mit und eine ohne Schrägstrich:
   * `http://localhost/`
   * `http://localhost`
1. Klicken Siei auf **Konfigurieren**, nachdem Sie jede URL hinzugefügt und Ihre Einstellungen Ihren Anforderungen entsprechend konfiguriert haben.
1. Navigieren Sie als Nächstes zu **Zertifikate und Geheimnisse** klicken Sie auf **Neues Client-Geheimnis** und führen Sie die Schritte auf dem Bildschirm aus, um ein Geheimnis zu erstellen. Notieren Sie sich dieses Geheimnis für die spätere Verwendung.
1. Presse **Übersicht** im linken Bereich und kopieren Sie die Werte für **Anwendungs-ID (client)** zur späteren Verwendung.

Um eine Neukodifizierung vorzunehmen, benötigen Sie die folgenden Informationen, um OAuth2 für den E-Mail-Dienst auf der AEM zu konfigurieren:

* Die Auth-URL im Formular: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/authorize`
* Die Token-URL im Formular: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/token`
* Die Aktualisieren-URL im Formular: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/token`
* Die Client-ID
* Das Client-Geheimnis

### Erzeugen des Aktualisierungstokens {#generating-the-refresh-token}

Als Nächstes müssen Sie das Aktualisierungstoken generieren, wie in einem nachfolgenden Schritt dargestellt.

Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die folgende URL im Browser, nachdem Sie `clientID` mit den für Ihr Konto spezifischen Werten:

   ```https://login.microsoftonline.com/common/oauth2/v2/authorize?client_id=<client_id>&scope=IMAP.AccessAsUser.A;;%20POP.AccessAsUser.All%20SMTP.Send%20User.Read&response_type=code&redirect-uri=http://loginmicrosoftonline.com/common/outh2/nativeclient&prompt=login```

1. Erlauben Sie die Erlaubnis, wo immer dies erforderlich ist.
1. Die URL wird an einen neuen Ort umgeleitet. Sie wird in folgendem Format erstellt: `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Kopieren Sie den Wert von `<code>` im obigen Beispiel.
1. Verwenden Sie den folgenden cURL-Befehl, um das refreshToken abzurufen. Ersetzen Sie clientID, clientSecret durch die Werte für Ihr Konto und den Wert für `<code>`:

   ```
   curl -H “ContentType application/x-www-form-urlencoded” -d 
   "client_id=<client-id>
   &scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All&code=M.R3_BAY.1bf609bf-25b3-2fcd-d910-02e02c53bc
   &grant_type=authorization_code
   &redirect_uri= https://login.microsoftonline.com/common/oauth2/nativeclient
   &client_secret=~1E8Q~cz-m6vgOb9m~SI.eF9jSVTbFUiP5f0” -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token
   ```

1. Notieren Sie sich die Werte für refreshToken und accessToken.

### Validieren der Tokens {#validating-the-tokens}

Bevor Sie mit der OAuth-Konfiguration auf der AEM-Seite fortfahren, überprüfen Sie mit dem folgenden Verfahren sowohl accessToken als auch refreshToken:

1. Erzeugen Sie das accessToken mithilfe des im vorherigen Verfahren erstellten refreshToken. Sie können dies mit der folgenden URL erreichen und die Werte für `<client_id>`,`<client_secret>` zusammen mit `<refreshToken>`:

   ```
   curl -H “ContentType application/x-www-form-urlencoded” -d 
   "client_id=<client_id>
   &scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All&code=<code>
   &grant_type=authorization_code
   &redirect_uri= https://login.microsoftonline.com/common/oauth2/nativeclient
   &client_secret=<client_secret>
   &refresh_token=<refresh_token” 
   -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token
   ```

1. Senden Sie eine E-Mail mit dem accessToken, um zu sehen, ob es ordnungsgemäß funktioniert.

>[!NOTE]
>
> Sie können die Postman-API-Sammlung von [diesem Speicherort](https://docs.microsoft.com/de-de/azure/active-directory/develop/v2-oauth2-auth-code-flow) abrufen.

### E-Mail-Dienst mit Auth2.0-Unterstützung konfigurieren {#configureemailservice}

Jetzt müssen Sie den E-Mail-Dienst auf dem neuesten JEE-Server konfigurieren, indem Sie sich in der Admin-Benutzeroberfläche anmelden:

1. Navigieren Sie zu **Startseite** - **Diensleistung** - **Anwendungen und Dienste** - **Dienstverwaltung** - **Email Service**
1. **Configuration Email Service** Fenster angezeigt, konfigurieren **SMPT** und **IMP** -Server für grundlegende Authentifizierung.
1. Um den Outlook-E-Mail-Authentifizierungsdienst zu aktivieren, wählen Sie **oAuth 2.0-Authentifizierungseinstellungen** aktivieren.
1. Kopieren Sie die Werte von **Client-ID** und **Client Secret** von Azure Portal aus.
1. Den generierten Wert kopieren **Token aktualisieren**.
1. Klicken **Speichern** , um die Details zu speichern.
1. Melden Sie sich bei Workbench an und suchen Sie nach **Email 1.0** von **Aktivitätsauswahl**.
1. Unter E-Mail 1.0 sind drei Optionen verfügbar:
   * **Mit Dokument senden**: Sendet E-Mails mit einzelnen Anhängen.
   * **Mit Zuordnung der Anhänge senden**: Sendet E-Mail mit mehreren Anhängen.
   * **Empfangen**: Erhält eine E-Mail von POP3 oder IMAP.
1. Testen Sie die Anwendung durch Auswahl von **Mit Dokument senden**
1. Bereitstellung **NACH** und **Von** Adressen.
1. Rufen Sie die Anwendung auf und E-Mail wird mit der oAuth2.0-Authentifizierung gesendet.

>[!NOTE]
>
> Wenn Sie die Authentifizierungseinstellung für Auth 2.0 in Standardauthentifizierung für einen bestimmten Prozess in einer Workbench ändern möchten, können Sie die Option **oAuth2.0-Authentifizierung** Kontrollkästchen unter **Globale Einstellungen verwenden** im **Verbindungseinstellungen** Registerkarte.

### Fehlerbehebung {#troubleshooting}

Wenn der E-Mail-Dienst nicht ordnungsgemäß funktioniert, erstellen Sie die `refreshToken` wie oben beschrieben. Es dauert einige Minuten, bis der neue Wert bereitgestellt wird.


