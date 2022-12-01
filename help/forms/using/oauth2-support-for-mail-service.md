---
title: Konfigurieren der OAuth2-basierten Authentifizierung für Microsoft® Office 365-Mail-Serverprotokolle
description: Konfigurieren der OAuth2-basierten Authentifizierung für Microsoft® Office 365-Mail-Serverprotokolle
source-git-commit: 35595ffca9d2f6fd80bfe93bade247f5b4600469
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 3%

---

# Integration mit den Mailserver-Protokollen von Microsoft® Office 365 {#oauth2-support-for-the-microsoft-mail-server-protocols}

Um es Unternehmen zu ermöglichen, sichere E-Mail-Anforderungen zu erfüllen, bietet AEM Forms OAuth 2.0-Unterstützung für die Integration mit Microsoft® Office 365-E-Mail-Serverprotokollen. Sie können den Authentifizierungsdienst von Azure Active Directory (Azure AD) OAuth 2.0 verwenden, um eine Verbindung mit verschiedenen Protokollen wie IMAP, POP oder SMTP herzustellen und auf E-Mail-Daten für Office 365-Benutzer zuzugreifen. Im Folgenden finden Sie eine schrittweise Anleitung zum Konfigurieren der Microsoft® Office 365-E-Mail-Serverprotokolle für die Authentifizierung über den OAuth 2.0-Dienst:

1. Anmelden [https://portal.azure.com/](https://portal.azure.com/) und suchen Sie nach **Azure Active Directory** in der Suchleiste und klicken Sie auf das Ergebnis.
Alternativ können Sie direkt zu [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) gehen.
1. Klicken **Hinzufügen** > **App-Registrierung** > **Neue Registrierung**

   ![App-Registrierung](/help/forms/using/assets/outh_outlook_microsoft_azure.png)

1. Füllen Sie die Informationen entsprechend Ihren Anforderungen aus und klicken Sie auf **registrieren**.
   ![Unterstütztes Konto](/help/forms/using/assets/azure_suuportedaccountype.png)
Im oben genannten Fall 
**Konten in einem beliebigen Organisationsverzeichnis (Beliebiges Azure AD-Verzeichnis - Multitenant) und persönlichen Microsoft®-Konten (z. B. Skype, Xbox)** ausgewählt ist.

   >[!NOTE]
   >
   > * Für **Konten in einem beliebigen Organisationsverzeichnis (Beliebiges Azure AD-Verzeichnis - Multitenant)** -Anwendung verwenden, wird empfohlen, anstelle des persönlichen E-Mail-Kontos ein Arbeitskonto zu verwenden.
   > * **Nur persönliche Microsoft®-Konten** und **Einzelmandant** -Anwendungen werden nicht unterstützt.
   > * Es wird empfohlen, **Microsoft®-Konto für mehrere Mandanten und Personen** Anwendung.


1. Navigieren Sie als Nächstes zu **Zertifikate und Geheimnisse** klicken **Neues Client-Geheimnis** und führen Sie die Schritte auf dem Bildschirm aus, um ein Geheimnis zu erstellen. Notieren Sie sich diesen Wert des Geheimnisses für die spätere Verwendung.

   ![Geheimer Schlüssel](/help/forms/using/assets/azure_secretkey.png)

1. Um Berechtigungen hinzuzufügen, wechseln Sie zur neu erstellten App und wählen Sie **API-Berechtigungen** > **Berechtigungen hinzufügen** > **Microsoft® Diagramm** > **Delegierte Berechtigungen**
1. Aktivieren Sie die Kontrollkästchen für die folgenden Berechtigungen für die App und klicken Sie auf **Berechtigung hinzufügen**:

   * `IMAP.AccessUser.All`
   * `Mail.Read`
   * `offline_access`
   * `POP.AccessAsUser.All`
   * `SMTP.Send`
   * `User.Read`

   ![API-Berechtigung](/help/forms/using/assets/azure_apipermission.png)

1. Auswählen **Authentifizierung** > **Plattform hinzufügen** > **Web** und im **Umleitungs-URLs** fügen Sie einen der folgenden URIs (Universal Resource Identifier) als hinzu:
   * `https://login.microsoftonline.com/common/oauth2/nativeclient`
   * `http://localhost`

   In diesem Fall `https://login.microsoftonline.com/common/oauth2/nativeclient` wird als Umleitungs-URI verwendet.

1. Klicken **Konfigurieren** nach dem Hinzufügen der einzelnen URLs und der Konfiguration Ihrer Einstellungen entsprechend Ihren Anforderungen.
   ![Umleitungs-URI](/help/forms/using/assets/azure_redirecturi.png)

   >[!NOTE]
   >
   > Die Auswahl von **Zugriffstoken** und **ID-Token** Kontrollkästchen.

1. Klicken **Übersicht** im linken Bereich und kopieren Sie die Werte für **Anwendungs-ID (client)**, **Verzeichnis-ID (Mandanten-ID)** und **Client Secret** zur späteren Verwendung.

   ![Übersicht](/help/forms/using/assets/azure_overview.png)

## Erstellen des Autorisierungscodes {#generating-the-authorization-code}

Als Nächstes müssen Sie den Autorisierungscode generieren, der in den folgenden Schritten erläutert wird:

1. Öffnen Sie die folgende URL im Browser, nachdem Sie `clientID` mit dem `<client_id>` und `redirect_uri` mit Ihrem Umleitungs-URI Ihrer Anwendung:

   ```https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=[clientid]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login```

1. Wenn Sie die oben genannte URL eingeben, werden Sie zum Anmeldebildschirm weitergeleitet:
   ![Anmeldebildschirm](/help/forms/using/assets/azure_loginscreen.png)

1. Geben Sie die E-Mail ein und klicken Sie auf **Nächste** und der Bildschirm mit den App-Berechtigungen wird angezeigt:

   ![Berechtigung zulassen](/help/forms/using/assets/azure_permission.png)

1. Nachdem Sie die Berechtigung erteilt haben, werden Sie wie folgt zu einer neuen URL umgeleitet: `https://login.microsoftonline.com/common/oauth2/nativeclient?code=<code>&session_state=[session_id]`

1. Kopieren Sie den Wert von `<code>` von der obigen URL aus `0.ASY...` nach `&session_state` in der obigen URL.

## Erzeugen des Aktualisierungstokens {#generating-the-refresh-token}

Als Nächstes müssen Sie das Aktualisierungstoken generieren, das in den folgenden Schritten erläutert wird:

1. Öffnen Sie die Eingabeaufforderung und verwenden Sie den folgenden cURL-Befehl, um das refreshToken abzurufen.

1. Ersetzen Sie die `clientID`, `client_secret` und `redirect_uri` mit den Werten für Ihre Anwendung zusammen mit dem Wert von `<code>`:

   `curl -H “ContentType application/x-www-form-urlencoded” -d “client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]” -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token`

1. Notieren Sie sich das Aktualisierungs-Token.

## E-Mail-Dienst mit OAuth 2.0-Unterstützung konfigurieren {#configureemailservice}

Jetzt müssen Sie den E-Mail-Dienst auf dem neuesten JEE-Server konfigurieren, indem Sie sich in der Admin-Benutzeroberfläche anmelden:

1. Navigieren Sie zu **Startseite** > **Diensleistung** > **Anwendungen und Dienste** > **Dienstverwaltung** > **Email Service**, die **Configuration Email Service** angezeigt, das für die einfache Authentifizierung konfiguriert wurde.

   >[!NOTE]
   >
   > Um den oAuth 2.0-Authentifizierungsdienst zu aktivieren, müssen Sie **Ob der SMTP-Server Authentifizierung (SMTP Authenticate) erfordert** aktivieren.

1. Satz **oAuth 2.0-Authentifizierungseinstellungen** as `True`.
1. Kopieren Sie die Werte von **Client-ID** und **Client Secret** von Azure Portal aus.
1. Den generierten Wert kopieren **Token aktualisieren**.
1. Anmelden bei **Workbench** und Suchen **Email 1.0** von **Aktivitätsauswahl**.
1. Unter E-Mail 1.0 sind drei Optionen verfügbar:
   * **Mit Dokument senden**: Sendet E-Mails mit einzelnen Anhängen.
   * **Mit Zuordnung der Anhänge senden**: Sendet E-Mail mit mehreren Anhängen.
   * **Empfangen**: Erhält eine E-Mail von IMAP.

   >[!NOTE]
   >
   >* Das Transport Security-Protokoll hat gültige Werte wie: &quot;blank&quot;, &quot;SSL&quot;oder &quot;TLS&quot;. Sie müssen die Werte von **SMTP Transport Security** und **Transport Security empfangen** nach **TLS** zur Aktivierung des oAuth-Authentifizierungsdienstes.
   >* **POP3-Protokoll** wird für OAuth nicht unterstützt.


   ![Verbindungseinstellungen](/help/forms/using/assets/oauth_connectionsettings.png)

1. Testen Sie die Anwendung durch Auswahl von **Mit Dokument senden**.
1. Bereitstellung **NACH** und **Von** Adressen.
1. Rufen Sie die Anwendung auf und E-Mail wird mit der 0Auth 2.0-Authentifizierung gesendet.

   >[!NOTE]
   >
   >Wenn Sie die Authentifizierungseinstellung für Auth 2.0 in Standardauthentifizierung für einen bestimmten Prozess in einer Workbench ändern möchten, können Sie die **OAuth 2.0-Authentifizierung** Wert als &quot;False&quot;unter **Globale Einstellungen verwenden** im **Verbindungseinstellungen** Registerkarte.

## So aktivieren Sie OAuth-Aufgabenbenachrichtigungen {#enable_oauth_task}

1. Navigieren Sie zu **Startseite** > **Dienste** > **Formular-Workflow** > **Servereinstellungen** > **E-Mail-Einstellungen**
1. Um OAuth-Aufgabenbenachrichtigungen zu aktivieren, wählen Sie die **oAuth aktivieren** aktivieren.
1. Kopieren Sie die Werte von **Client-ID** und **Client Secret** von Azure Portal aus.
1. Den generierten Wert kopieren **Token aktualisieren**.
1. Klicken **Speichern** , um die Details zu speichern.

   ![Aufgabenbenachrichtigung](/help/forms/using/assets/task_notification.png)

   >[!NOTE]
   >
   > Weitere Informationen zu Aufgabenbenachrichtigungen finden Sie unter [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/manage-endpoints/configuring-email-endpoints.html#create-an-email-endpoint-for-the-complete-task-service).

## So konfigurieren Sie den E-Mail-Endpunkt {#configure_email_endpoint}

1. Navigieren Sie zu **Startseite** > **Dienste** > **Anwendungen und Dienste** > **Endpunktverwaltung**
1. Um den E-Mail-Endpunkt zu konfigurieren, legen Sie **oAuth 2.0-Authentifizierungseinstellungen** as `True`.
1. Kopieren Sie die Werte von **Client-ID** und **Client Secret** von Azure Portal aus.
1. Den generierten Wert kopieren **Token aktualisieren**.
1. Klicken **Speichern** , um die Details zu speichern.

   ![Verbindungseinstellungen](/help/forms/using/assets/oauth_emailendpoint.png)

   >[!NOTE]
   >
   > Um weitere Informationen zum Konfigurieren von E-Mail-Endpunkten zu erhalten, klicken Sie auf [E-Mail-Endpunkt konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/manage-endpoints/configuring-email-endpoints.html).

## Fehlerbehebung {#troubleshooting}

* Wenn der E-Mail-Dienst nicht ordnungsgemäß funktioniert. Versuchen Sie, die `Refresh Token` wie oben beschrieben. Es dauert einige Minuten, bis der neue Wert bereitgestellt wird.

* Fehler beim Konfigurieren von E-Mail-Serverdetails im E-Mail-Endpunkt mit Workbench. Versuchen Sie, den Endpunkt über die Admin-Benutzeroberfläche anstatt über Workbench zu konfigurieren.

