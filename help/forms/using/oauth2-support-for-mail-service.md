---
title: Konfigurieren der OAuth2-basierten Authentifizierung für Microsoft® (Forms JEE OAuth); Office 365-Mailserver-Protokolle
description: Konfigurieren der OAuth2-basierten Authentifizierung für Microsoft® (Forms JEE OAuth); Office 365-Mailserver-Protokolle
exl-id: cd3da71f-892c-4fde-905f-71a64fb5d4e4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '986'
ht-degree: 100%

---

# Integration von AEM Forms mit den Mailserver-Protokollen von Microsoft® Office 365 {#oauth2-support-for-the-microsoft-mail-server-protocols}

Um es Unternehmen zu ermöglichen, sichere E-Mail-Anforderungen zu erfüllen, bietet AEM Forms OAuth 2.0-Unterstützung für die Integration mit Microsoft® Office 365-Mailserver-Protokollen. Sie können den OAuth 2.0-Authentifizierungsdienst von Azure Active Directory (Azure AD) verwenden, um sich mit verschiedenen Protokollen wie IMAP, POP oder SMTP zu verbinden und auf die E-Mail-Daten von Office 365-Benutzenden zuzugreifen. Nachfolgend finden Sie eine schrittweise Anleitung zur Konfiguration der Microsoft® Office 365-Mailserver-Protokolle für die Authentifizierung über den OAuth 2.0-Dienst:

1. Melden Sie sich unter [https://portal.azure.com/](https://portal.azure.com/) an, suchen Sie in der Suchleiste nach **Azure Active Directory** und klicken Sie auf das Ergebnis.
Alternativ können Sie direkt zu [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) navigieren
1. Klicken Sie auf **Hinzufügen** > **App-Registrierung** > **Neue Registrierung**.

   ![App-Registrierung](/help/forms/using/assets/outh_outlook_microsoft_azure.png)

1. Füllen Sie die Informationen entsprechend Ihren Anforderungen aus und klicken Sie dann auf **Registrieren**.
   ![Unterstütztes Konto](/help/forms/using/assets/azure_suuportedaccountype.png) 
In dem Fall oben ist die Option **Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – Multitenant) und persönliche Microsoft®-Konten (z. B. Skype, Xbox)** ausgewählt.

   >[!NOTE]
   >
   > * Für **Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – Multitenant)** empfiehlt Adobe, dass Sie ein Arbeitskonto und kein persönliches E-Mail-Konto verwenden.
   > * Die Anwendung **Nur persönliche Microsoft®-Konten** wird nicht unterstützt.
   > * Adobe empfiehlt die Verwendung der Anwendung **Multitenant und persönliches Microsoft®-Konto**.

1. Gehen Sie dann zu **Zertifikate und geheime Schlüssel**, klicken Sie auf **Neuer geheimer Client-Schlüssel** und folgen Sie den Anweisungen auf dem Bildschirm, um einen geheimen Schlüssel zu erstellen. Notieren Sie sich den geheimen Schlüssel für die spätere Verwendung.

   ![Geheimer Schlüssel](/help/forms/using/assets/azure_secretkey.png)

1. Um Berechtigungen hinzuzufügen, gehen Sie zu der neu erstellten App und wählen Sie **API-Berechtigungen** > **Berechtigung hinzufügen** > **Microsoft® Graph** > **Delegierte Berechtigungen**.
1. Aktivieren Sie die Kontrollkästchen für die folgenden Berechtigungen für die App und klicken Sie auf **Berechtigung hinzufügen**:

   * `IMAP.AccessUser.All`
   * `Mail.Read`
   * `offline_access`
   * `POP.AccessAsUser.All`
   * `SMTP.Send`
   * `User.Read`

   ![API-Berechtigung](/help/forms/using/assets/azure_apipermission.png)

1. Wählen Sie **Authentifizierung** > **Plattform hinzufügen** > **Web**, und fügen Sie im Abschnitt **Umleitungs-URLs** eine der folgenden URIs (Universal Resource Identifier) ein:
   * `https://login.microsoftonline.com/common/oauth2/nativeclient`
   * `http://localhost`

   In diesem Fall wird `https://login.microsoftonline.com/common/oauth2/nativeclient` als Umleitungs-URI verwendet.

1. Klicken Sie auf **Konfigurieren**, nachdem Sie die einzelnen URLs hinzugefügt haben, und konfigurieren Sie die Einstellungen entsprechend Ihren Anforderungen.
   ![Umleitungs-URI](/help/forms/using/assets/azure_redirecturi.png)

   >[!NOTE]
   >
   > Es ist obligatorisch, die Kontrollkästchen **Zugriffs-Token** und **ID-Token** zu aktivieren.

1. Klicken Sie im linken Bereich auf **Übersicht** und kopieren Sie die Werte für die **Anwendungs-ID (Client-ID)**, **Verzeichnis-ID (Mandanten-ID)** und das **Client-Geheimnis** für die spätere Verwendung.

   ![Übersicht](/help/forms/using/assets/azure_overview.png)

## Generieren des Autorisierungs-Codes {#generating-the-authorization-code}

Als Nächstes müssen Sie den Autorisierungs-Code generieren, wie in den folgenden Schritten erklärt:

1. Öffnen Sie die folgende URL im Browser, nachdem Sie `clientID` durch `<client_id>` und `redirect_uri` durch den Redirect-URI Ihrer Anwendung ersetzt haben:

   ```https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=[clientid]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login```

   >[!NOTE]
   >
   > Wenn es sich um eine Einzelmandanten-Anwendung handelt, ersetzen Sie `common` durch Ihre `[tenantid]` in der folgenden URL, um den Autorisierungs-Code zu generieren: `https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/authorize?client_id=[[clientid]]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20openid%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login`

1. Wenn Sie die obige URL eingeben, werden Sie zum Anmeldebildschirm weitergeleitet:
   ![Anmeldebildschirm](/help/forms/using/assets/azure_loginscreen.png)

1. Geben Sie die E-Mail-Adresse ein, klicken Sie auf **Weiter**, und der Bildschirm für die App-Berechtigung erscheint:

   ![Berechtigung zulassen](/help/forms/using/assets/azure_permission.png)

1. Wenn Sie die Berechtigung erteilen, werden Sie auf eine neue URL umgeleitet: `https://login.microsoftonline.com/common/oauth2/nativeclient?code=<code>&session_state=[session_id]`

1. Kopieren Sie den Wert von `<code>` aus der obigen URL von `0.ASY...` nach `&session_state` in der obigen URL.

## Erzeugen des Aktualisierungs-Tokens {#generating-the-refresh-token}

Als Nächstes müssen Sie das Aktualisierungs-Token generieren, wie in den folgenden Schritten erläutert:

1. Öffnen Sie die Eingabeaufforderung und verwenden Sie den folgenden cURL-Befehl, um das Aktualisierungs-Token abzurufen.

1. Ersetzen Sie `clientID`, `client_secret` und `redirect_uri` durch die Werte für Ihre Anwendung zusammen mit dem Wert von `<code>`:

   `curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token`

   >[!NOTE]
   >
   > Verwenden Sie in einer Einzelmandantenanwendung den folgenden cURL-Befehl, um ein Aktualisierungs-Token zu generieren, und ersetzen Sie `common` mit der `[tenantid]` in:
   >`curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/token`

1. Notieren Sie sich das Aktualisierungs-Token.

## Konfigurieren des E-Mail-Dienstes mit OAuth 2.0-Unterstützung {#configureemailservice}

Konfigurieren Sie nun den E-Mail-Dienst auf dem aktuellen JEE-Server, indem Sie sich bei der Admin-Benutzeroberfläche anmelden:

1. Gehen Sie zu **Startseite** > **Service** > **Anwendung und Dienste** > **Dienstverwaltung** > **E-Mail-Dienst**. Es erscheint das Fenster **E-Mail-Dienst-Konfiguration**, die für die Standardauthentifizierung konfiguriert ist.

   >[!NOTE]
   >
   > Um den OAuth 2.0-Authentifizierungsdienst zu aktivieren, müssen Sie das Kontrollkästchen, **ob der SMTP-Server eine Authentifizierung erfordert (SMTP Authenticate)**, aktivieren.

1. Setzen Sie **OAuth 2.0-Authentifizierungseinstellungen** auf `True`.
1. Kopieren Sie die Werte von **Client-ID** und **Client-Geheimnis** aus dem Azure-Portal.
1. Kopieren Sie den Wert des generierten **Aktualisierungs-Tokens**.
1. Melden Sie sich bei **Workbench** an und suchen Sie **E-Mail 1.0** im **Aktivitätswähler**.
1. Unter E-Mail 1.0 sind drei Optionen verfügbar:
   * **Mit Dokument senden**: Sendet eine E-Mail mit einzelnen Anhängen.
   * **Mit Karte der Anhänge senden**: Sendet eine E-Mail mit mehreren Anhängen.
   * **Empfangen**: Empfängt eine E-Mail von IMAP.

   >[!NOTE]
   >
   >* Das Transport-Sicherheitsprotokoll hat folgende gültige Werte: „leer“, „SSL“ oder „TLS“. Setzen Sie die Werte von **SMTP Transport Security** und **Receive Transport Security** auf **TLS**, um den OAuth-Authentifizierungsdienst zu aktivieren.
   >* **POP3-Protokoll** wird für OAuth bei der Verwendung von E-Mail-Endpunkten nicht unterstützt.

   ![Verbindungseinstellungen](/help/forms/using/assets/oauth_connectionsettings.png)

1. Testen Sie die Anwendung, indem Sie **Mit Dokument senden** wählen.
1. Geben Sie die Adressen **An** und **Von** an.
1. Rufen Sie die Anwendung auf, und eine E-Mail wird unter Verwendung der OAuth 2.0-Authentifizierung gesendet.

   >[!NOTE]
   >
   >Bei Bedarf können Sie die Authentifizierungseinstellung für Auth 2.0 in „Standardauthentifizierung“ für einen bestimmten Prozess in einer Workbench ändern. Legen Sie dazu auf der Registerkarte **Verbindungseinstellungen** unter **Globale Einstellungen verwenden** den Wert **OAuth 2.0-Authentifizierung** als „False“ fest.

## So aktivieren Sie OAuth-Aufgabenbenachrichtigungen {#enable_oauth_task}

1. Gehen Sie zu **Startseite** > **Dienste** > **Formular-Workflow** > **Server-Einstellungen** > **E-Mail-Einstellungen**
1. Um OAuth-Aufgabenbenachrichtigungen zu aktivieren, markieren Sie das Kontrollkästchen **OAuth aktivieren**.
1. Kopieren Sie die Werte von **Client-ID** und **Client-Geheimnis** aus dem Azure-Portal.
1. Kopieren Sie den Wert des generierten **Aktualisierungs-Tokens**.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

   ![Aufgabenbenachrichtigung](/help/forms/using/assets/task_notification.png)

   >[!NOTE]
   >
   > Weitere Informationen zu den Aufgabenbenachrichtigungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints#create-an-email-endpoint-for-the-complete-task-service).

## So konfigurieren Sie den E-Mail-Endpunkt {#configure_email_endpoint}

1. Gehen Sie zu **Startseite** > **Dienste** > **Anwendung und Dienste** > **Endpunktverwaltung**
1. Um den E-Mail-Endpunkt zu konfigurieren, setzen Sie **OAuth 2.0-Authentifizierungseinstellungen** auf `True`.
1. Kopieren Sie die Werte von **Client-ID** und **Client-Geheimnis** aus dem Azure-Portal.
1. Kopieren Sie den Wert des generierten **Aktualisierungs-Tokens**.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

   ![Verbindungseinstellungen](/help/forms/using/assets/oauth_emailendpoint.png)

   >[!NOTE]
   >
   > Um weitere Informationen zur Konfiguration von E-Mail-Endpunkten zu erhalten, klicken Sie auf [E-Mail-Endpunkt konfigurieren](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints).

## Fehlerbehebung {#troubleshooting}

* Wenn der E-Mail-Dienst nicht ordnungsgemäß funktioniert, versuchen Sie, das `Refresh Token` wie oben beschrieben zu regenerieren. Es dauert ein paar Minuten, bis der neue Wert bereitgestellt wird.

* Fehler beim Konfigurieren von E-Mail-Server-Details im E-Mail-Endpunkt mit Workbench. Versuchen Sie, den Endpunkt über die Admin-Benutzeroberfläche anstelle von Workbench zu konfigurieren.
