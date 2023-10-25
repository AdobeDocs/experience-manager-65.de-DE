---
title: Konfigurieren von E-Mail-Benachrichtigungen
seo-title: Configuring Email Notification
description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen in Adobe Experience Manager konfigurieren.
seo-description: Learn how to configure Email Notification in AEM.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
exl-id: 918fcbbc-a78a-4fab-a933-f183ce6a907f
source-git-commit: b703f356f9475eeeafb1d5408c650d9c6971a804
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 95%

---


# Konfigurieren von E-Mail-Benachrichtigungen{#configuring-email-notification}

AEM sendet E-Mail-Benachrichtigungen an Benutzerinnen und Benutzer, die:

* Seitenereignisse wie Änderungen oder Replikationen abonniert haben. Im Abschnitt [Benachrichtigungs-Posteingang](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) ist beschrieben, wie solche Ereignisse abonniert werden können.

* Forumsveranstaltungen abonniert haben.
* Einen Schritt in einem Workflow ausführen müssen. Im Abschnitt [Teilnehmerschritt](/help/sites-developing/workflows-step-ref.md#participant-step) wird beschrieben, wie E-Mail-Benachrichtigungen in einem Workflow ausgelöst werden können.

Voraussetzungen:

* Für die Benutzerinnen und Benutzer muss im Profil eine gültige E-Mail-Adresse definiert sein.
* Der **Day CQ Mail Service** muss ordnungsgemäß konfiguriert sein.

Wenn Benutzende benachrichtigt werden, erhalten sie eine E-Mail in der Sprache, die in ihrem Profil definiert ist. Jede Sprache verfügt über eine eigene Vorlage, die angepasst werden kann. Für neue Sprachen können neue E-Mail-Vorlagen hinzugefügt werden.

>[!NOTE]
>
>Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Konfigurieren des E-Mail-Dienstes {#configuring-the-mail-service}

Damit AEM E-Mails versenden kann, muss der **Day CQ-E-Mail-Dienst** ordnungsgemäß konfiguriert sein. Sie können die Konfiguration in der Web-Konsole anzeigen. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Es gelten die folgenden Beschränkungen:

* Der **SMTP-Server-Port** muss 25 oder höher sein.

* Der **SMTP-Server-Hostname** darf nicht leer sein.
* Die **„Von“-Adresse** darf nicht leer sein.

Zum Debuggen eines Problems mit dem **Day CQ Mail Service** können Sie die Protokolle des Dienstes betrachten:

`com.day.cq.mailer.DefaultMailService`

Die Konfiguration sieht in der Web-Konsole wie folgt aus:

![Das OSGi-Konfigurationsfenster des Day CQ Mail Service](assets/chlimage_1-276.png)

## Konfigurieren des E-Mail-Benachrichtigungskanals {#configuring-the-email-notification-channel}

Wenn Sie entweder Benachrichtigungen zu Seiten- oder Forenereignissen abonniert haben, ist die „Von“-E-Mail-Adresse standardmäßig auf `no-reply@acme.com` eingestellt. Sie können diesen Wert durch die Konfiguration des Diensts **Benachrichtigungs-E-Mail-Kanal** in der Web-Konsole ändern.

Fügen Sie zum Konfigurieren der „Von“-E-Mail-Adresse einen `sling:OsgiConfig`-Knoten zum Repository hinzu. Verwenden Sie das folgende Verfahren, um den Knoten direkt mithilfe von CRXDE Lite hinzuzufügen:

1. Fügen Sie in CRXDE Lite einen Ordner mit dem Namen `config` unter Ihrem Programmordner hinzu.
1. Fügen Sie im Konfigurationsordner einen Knoten mit folgendem Namen hinzu:

   `com.day.cq.wcm.notification.email.impl.EmailChannel` vom Typ `sling:OsgiConfig`

1. Fügen Sie eine `String`-Eigenschaft zum Knoten mit dem Namen `email.from` hinzu. Geben Sie als Wert die E-Mail-Adresse an, die Sie verwenden möchten.

1. Klicken Sie auf **Alle speichern**.

Gehen Sie wie folgt vor, um den Knoten in den Quellordnern des Inhaltspakets zu definieren:

1. Erstellen Sie in `jcr_root/apps/*app_name*/config folder` eine Datei mit dem Namen `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`.

1. Fügen Sie die folgende XML für den Knoten hinzu:

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. Ersetzen Sie den Wert des Attributs `email.from` (`name@server.com`) durch Ihre E-Mail-Adresse.

1. Speichern Sie die Datei.

## Konfigurieren des E-Mail-Benachrichtigungsdiensts für Workflows {#configuring-the-workflow-email-notification-service}

Wenn Sie E-Mail-Benachrichtigungen durch den Workflow erhalten, werden sowohl die E-Mail-Adresse als auch das Host-URL-Präfix auf Standardwerte gesetzt. Sie können diese Werte ändern, indem Sie den **Day CQ-E-Mail-Benachrichtigungsdienst für Workflows** in der Web-Konsole konfigurieren. Falls Sie dies tun, wird empfohlen, die Änderung im Repository beizubehalten.

Die Standardkonfiguration sieht in der Web-Konsole wie folgt aus:

![Das Konfigurationsfenster des Day CQ Workflow Email Notification Service](assets/chlimage_1-277.png)

### E-Mail-Vorlagen für die Seitenbenachrichtigung {#email-templates-for-page-notification}

E-Mail-Vorlagen für Seitenbenachrichtigungen finden Sie unten:

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

Die standardmäßige englische Vorlage (`en.txt`) wird wie folgt definiert:

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Seitenbenachrichtigung {#customizing-email-templates-for-page-notification}

Die englische E-Mail-Vorlage für die Seitenbenachrichtigung können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. Ändern Sie die Datei nach Bedarf.
1. Speichern Sie die Änderungen.

Die Vorlage muss das folgende Format aufweisen:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Dabei kann &lt;text_x> ein Mix von statischem Text und dynamischen Zeichenfolgenvariablen sein. Die folgenden Variablen können innerhalb der E-Mail-Vorlage für Seitenbenachrichtigungen verwendet werden:

* `${time}`, Ereignisdatum und -uhrzeit

* `${userFullName}`, der vollständige Name des Benutzers, der das Ereignis ausgelöst hat

* `${userId}`, die ID des Benutzers, der das Ereignis ausgelöst hat
* `${modifications}`, beschreibt den Typ des Seitenereignisses und den Seitenpfad im folgenden Format:

  &lt;Seitenereignistyp> => &lt;Seitenpfad>

  Beispiel:

  PageModified => /content/geometrixx/en/products

### E-Mail-Vorlagen für die Workflow-Benachrichtigung {#email-templates-for-workflow-notification}

Die E-Mail-Vorlage für Workflow-Benachrichtigungen (Englisch) befindet sich unter:

`/libs/settings/workflow/notification/email/default/en.txt`

Sie ist wie folgt definiert:

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Workflow-Benachrichtigung {#customizing-email-templates-for-workflow-notification}

Die englische E-Mail-Vorlage für die Benachrichtigung über ein Workflow-Ereignis können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/libs/settings/workflow/notification/email/default/en.txt`

1. Ändern Sie die Datei nach Bedarf.
1. Speichern Sie die Änderungen.

Die Vorlage muss das folgende Format aufweisen:

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>Dabei kann `<text_x>` ein Mix von statischem Text und dynamischen Zeichenfolgenvariablen sein. Jede Zeile eines `<text_x>`-Elements muss mit einem umgekehrten Schrägstrich (`\`) enden, außer der letzten Instanz, wo das Fehlen des umgekehrten Schrägstrichs das Ende der `<text_x>`-Zeichenfolgenvariable anzeigt.
>
>Weitere Informationen zum Vorlagenformat werden von der Methode [javadocs der Properties.load()](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-)-Methode bereitgestellt.

Die Methode `${payload.path.open}` legt den Pfad zur Payload des Arbeitselements offen. Bei einer Seite in Sites würde `payload.path.open` dann `/bin/wcmcommand?cmd=open&path=…`ähneln, das den Server-Namen nicht enthält. Aus diesem Grund stellt die Vorlage diesem `${host.prefix}` voran.

Die folgenden Variablen können innerhalb der E-Mail-Vorlage verwendet werden:

* `${event.EventType}`, Ereignistyp
* `${event.TimeStamp}`, Datum und Uhrzeit des Ereignisses
* `${event.User}`, der Benutzer, der das Ereignis ausgelöst hat
* `${initiator.home}`, der Knotenpfad des Initiators

* `${initiator.name}`, der Name des Initiators

* `${initiator.email}`, die E-Mail-Adresse des Initiators
* `${item.id}`, die ID des Arbeitselements
* `${item.node.id}`, die ID des Knotens innerhalb des Workflow-Modells, das mit diesem Arbeitselement verknüpft ist
* `${item.node.title}`, der Titel des Arbeitselements
* `${participant.email}`, die E-Mail-Adresse des Teilnehmers
* `${participant.name}`, der Vorname des Teilnehmers
* `${participant.familyName}`, der Familienname des Teilnehmers
* `${participant.id}`, die ID des Teilnehmers
* `${participant.language}`, die Sprache des Teilnehmers
* `${instance.id}`, die ID des Workflows
* `${instance.state}`, der Status des Workflows
* `${model.title}`, der Titel des Workflow-Modells
* `${model.id}`, die ID des Workflow-Modells

* `${model.version}`, die Version des Workflow-Modells
* `${payload.data}`, die Payload

* `${payload.type}`, der Typ der Payload
* `${payload.path}`, der Pfad der Payload
* `${host.prefix}`, Host-Präfix, z. B.: `http://localhost:4502`

### Hinzufügen einer E-Mail-Vorlage für eine neue Sprache {#adding-an-email-template-for-a-new-language}

So fügen Sie eine Vorlage für eine neue Sprache hinzu:

1. Fügen Sie in CRXDE eine Datei `<language-code>.txt` hinzu unter:

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page`: für Seitenbenachrichtigungen
   * `/libs/settings/workflow/notification/email/default`: für Workflow-Benachrichtigungen

1. Passen Sie die Datei an die Sprache an.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Der `<language-code>`, der als Dateiname der E-Mail-Vorlage verwendet wird, muss ein von AEM anerkannter, aus zwei Kleinbuchstaben bestehender Sprach-Code sein. AEM nutzt die Sprach-Codes gemäß ISO-639-1.

## Konfigurieren von E-Mail-Benachrichtigungen zu AEM Assets {#assetsconfig}

Wenn Sammlungen in AEM Assets freigegeben oder nicht freigegeben werden, können Benutzerinnen und Benutzer E-Mail-Benachrichtigungen von AEM erhalten. Gehen Sie wie folgt vor, um E-Mail-Benachrichtigungen zu konfigurieren.

1. Konfigurieren Sie den E-Mail-Dienst, wie oben unter [Konfigurieren des Mail-Dienstes](/help/sites-administering/notification.md#configuring-the-mail-service) beschrieben.
1. Melden Sie sich in AEM als Admin an. Klicken Sie auf **Tools** > **Vorgänge** > **Web-Konsole**, um die Konfiguration der Web-Konsole zu öffnen.
1. Bearbeiten Sie das **Day CQ DAM-Ressourcensammlungs-Servlet**. Wählen Sie **E-Mail senden** aus. Klicken Sie auf **Speichern**.

## Einrichten von OAuth {#setting-up-oauth}

AEM bietet OAuth2-Unterstützung für seinen integrierten E-Mail-Service, um Unternehmen die Einhaltung von E-Mail-Sicherheitsanforderungen zu ermöglichen.

Sie können OAuth für mehrere E-Mail-Anbieter konfigurieren, wie unten beschrieben.

>[!NOTE]
>
>Dieses Verfahren ist ein Beispiel für eine Veröffentlichungsinstanz. Wenn Sie E-Mail-Benachrichtigungen auf einer Autoreninstanz aktivieren möchten, müssen Sie die gleichen Schritte auf der Autoreninstanz durchführen.

### Gmail {#gmail}

1. Erstellen Sie Ihr Projekt unter `https://console.developers.google.com/projectcreate`.
1. Wählen Sie Ihr Projekt aus und gehen Sie dann zu **APIs und Dienste** – **Dashboard – Anmeldedaten**.
1. Konfigurieren Sie den OAuth-Einverständnisbildschirm entsprechend Ihren Anforderungen.
1. Fügen Sie auf dem folgenden Aktualisierungsbildschirm diese beiden Bereiche hinzu:
   * `https://mail.google.com/`
   * `https://www.googleapis.com//auth/gmail.send`
1. Nachdem Sie die Bereiche hinzugefügt haben, gehen Sie zurück zu **Anmeldedaten** im Menü links und dann zu **Erstellen von Anmeldedaten** > **OAuth-Client-ID** > **Desktop-Programm**.
1. Daraufhin wird ein neues Fenster mit der Client-ID und dem Client-Geheimnis geöffnet.
1. Speichern Sie diese Anmeldedaten.

**AEM-Seitenkonfigurationen**

>[!NOTE]
>
>Adobe Managed Service-Kunden können diese Änderungen an Produktionsumgebungen gemeinsam mit ihrem Customer Service Engineer vornehmen

Konfigurieren Sie zunächst den E-Mail-Dienst:

1. Öffnen Sie die AEM-Web-Konsole, indem Sie zu `http://serveraddress:serverport/system/console/configMgr` gehen.
1. Suchen Sie nach **Day CQ Mail Service** und klicken Sie darauf.
1. Fügen Sie die folgenden Einstellungen hinzu:
   * SMTP-Server-Host-Name: `smtp.gmail.com`
   * SMTP-Server-Port: `25` oder `587`, abhängig von den Anforderungen
   * Markieren Sie die Kontrollkästchen für **SMPT verwendet StarTLS** und **SMTP erfordert StarTLS**.
   * Markieren Sie **OAuth-Fluss** und klicken Sie auf **Speichern**.

Konfigurieren Sie anschließend Ihren SMTP OAuth-Provider wie unten beschrieben:

1. Öffnen Sie die AEM-Web-Konsole, indem Sie zu `http://serveraddress:serverport/system/console/configMgr` gehen.
1. Suchen Sie nach **CQ Mailer SMTP OAuth2 Provider** und klicken Sie darauf.
1. Füllen Sie die erforderlichen Informationen wie folgt aus:
   * Autorisierungs-URL: `https://accounts.google.com/o/oauth2/auth`
   * Token-URL: `https://accounts.google.com/o/oauth2/token`
   * Bereiche: `https://www.googleapis.com/auth/gmail.send` und `https://mail.google.com/`. Sie können mehrere Bereiche hinzufügen, indem Sie auf die Schaltfläche **+** rechts von jedem konfigurierten Bereich klicken.
   * Client-ID und Client-Geheimnis: Konfigurieren Sie diese Felder mit den Werten, die Sie wie im obigen Absatz beschrieben abgerufen haben.
   * URL für aktualisierten Token: `https://accounts.google.com/o/oauth2/token`
   * Token-Ablauf aktualisieren: nie
1. Klicken Sie auf **Speichern**.

<!-- clarify refresh token expiry, currently not present in the UI -->

Nach der Konfiguration sollten die Einstellungen wie folgt aussehen:

![Das Konfigurationsfenster des CQ Mailer SMTP Oauth2 Provider](assets/oauth-smtpprov2.png)

Aktivieren Sie jetzt die OAuth-Komponenten. Gehen Sie dazu wie folgt vor:

1. Rufen Sie die Komponentenkonsole auf, indem Sie diese URL aufrufen: `http://serveraddress:serverport/system/console/components`
1. Suchen Sie nach den folgenden Komponenten.
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeGenerateServlet`
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeAccessTokenGenerator`
1. Klicken Sie links neben den Komponenten auf das Wiedergabesymbol.

   ![Liste der Komponenten, die OAuthCodeGenerateServlet und OAuthCodeAccessTokenGenerator anzeigen](assets/oauth-components-play.png)

Bestätigen Sie abschließend die Konfiguration, indem Sie:

1. Zur Adresse der Veröffentlichungsinstanz wechseln und sich als Admin anmelden
1. eine neue Registerkarte im Browser öffnen und zu `http://serveraddress:serverport/services/mailer/oauth2/authorize` navigieren. Dadurch werden Sie zur Seite Ihres SMTP-Anbieters weitergeleitet, in diesem Fall Gmail.
1. Anmelden und Einverständnis zur Erteilung der erforderlichen Berechtigungen
1. Nach der Zustimmung wird das Token im Repository gespeichert. Sie können es unter `accessToken` aufrufen, indem Sie direkt auf diese URL auf Ihrer Veröffentlichungsinstanz zugreifen: `http://serveraddress:serverport/crx/de/index.jsp#/conf/global/settings/mailer/oauth`
1. Wiederholen Sie die obigen Schritte für jede Veröffentlichungsinstanz

<!-- clarify if the ip/server address in the last procedure is that of the publish instance -->

### Microsoft Outlook {#microsoft-outlook}

1. Gehen Sie zu [https://portal.azure.com/](https://portal.azure.com/) und melden Sie sich an.
1. Suchen Sie in der Suchleiste nach **Azure Active Directory** und klicken Sie auf das Ergebnis. Alternativ können Sie direkt zu [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) gehen.
1. Klicken Sie auf **Registrierung einer Anwendung** – **Neue Registrierung**

   ![Die neue Registrierungsschaltfläche beim Konfigurieren von Microsoft Outlook](assets/oauth-outlook1.png)

1. Füllen Sie die Informationen entsprechend Ihren Anforderungen aus und klicken Sie dann auf **Registrieren**
1. Wechseln Sie zur neu erstellten Anwendung und wählen Sie **API-Berechtigungen** aus.
1. Gehen Sie zu **Berechtigung hinzufügen** – **Diagrammberechtigungen** – **Zugewiesene Berechtigungen**.
1. Wählen Sie die folgenden Berechtigungen für Ihre Anwendung aus und klicken Sie dann auf **Berechtigung hinzufügen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Gehen Sie zu **Authentifizierung** > **Plattform hinzufügen** > **Web** und fügen Sie im Abschnitt **Umleitungs-URLs** die folgende URL für die Umleitung des OAuth-Codes hinzu und klicken Sie dann auf **Konfigurieren**:
   * `http://localhost:4503/services/mailer/oauth2/token`
1. Wiederholen Sie die obigen Schritte für jede Veröffentlichungsinstanz
1. Konfigurieren Sie die Einstellungen entsprechend Ihren Anforderungen.
1. Gehen Sie dann zu **Zertifikate und Geheimnisse**, klicken Sie auf **Neues Client-Geheimnis** und führen Sie die Schritte auf dem Bildschirm aus, um ein Geheimnis zu erstellen. Notieren Sie sich dieses Geheimnis für die spätere Verwendung.
1. Klicken Sie auf **Überblick** im linken Bereich und kopieren Sie die Werte für **Anwendungs (Client) ID** und **Directory (Mandant) ID** zur späteren Verwendung.

Zusammenfassend benötigen Sie die folgenden Informationen, um OAuth2 für den E-Mail-Service auf der AEM-Seite zu konfigurieren:

* Die Auth-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* Die Token-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Die Aktualisierungs-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Die Client-ID
* Das Client-Geheimnis

**AEM-Seitenkonfigurationen**

Integrieren Sie anschließend Ihre OAuth2-Einstellungen mit AEM:

1. Gehen Sie zur Web-Konsole Ihrer lokalen Instanz, indem Sie zu `http://serveraddress:serverport/system/console/configMgr` navigieren.
1. Suchen Sie nach **Day CQ Mail Service** und klicken Sie darauf.
1. Fügen Sie die folgenden Einstellungen hinzu:
   * SMTP-Server-Host-Name: `smtp.office365.com`
   * SMTP-Benutzer: Ihr Benutzername im E-Mail-Format
   * „Von“-Adresse: Die E-Mail-Adresse, die im Feld „Von“ von Nachrichten verwendet werden soll, die vom E-Mail-Service versendet werden
   * SMTP-Server-Port: `25` oder `587`, je nach den Anforderungen
   * Markieren Sie die Kontrollkästchen für **SMPT verwendet StarTLS** und **SMTP erfordert StarTLS**.
   * Markieren Sie **OAuth-Fluss** und klicken Sie auf **Speichern**.
1. Suchen Sie nach **CQ Mailer SMTP OAuth2 Provider** und klicken Sie darauf.
1. Füllen Sie die erforderlichen Informationen wie folgt aus:
   * Füllen Sie die Autorisierungs-URL, Token-URL und Aktualisierungstoken-URL aus, indem Sie sie wie unter [Ende dieses Verfahrens](#microsoft-outlook) beschrieben dekonstruieren.
   * Client-ID und Client-Geheimnis: Konfigurieren Sie diese Felder mit den Werten, die Sie wie oben beschrieben abgerufen haben.
   * Fügen Sie der Konfiguration die folgenden Umfänge hinzu:
      * openid
      * offline_access
      * `https://outlook.office365.com/Mail.Send`
      * `https://outlook.office365.com/Mail.Read`
      * `https://outlook.office365.com/SMTP.Send`
   * AuthCode-Umleitungs-URL: `http://localhost:4503/services/mailer/oauth2/token`
   * Aktualisieren der Token-URL: diese sollte denselben Wert wie die Token-URL oben haben.
1. Klicken Sie auf **Speichern**.

Nach der Konfiguration sollten die Einstellungen wie folgt aussehen:

![Die abgeschlossene CQ Mailer SMTP OAuth2-Konfiguration](assets/oauth-outlook-smptconfig.png)

Aktivieren Sie jetzt die OAuth-Komponenten. Gehen Sie dazu wie folgt vor:

1. Rufen Sie die Komponentenkonsole auf, indem Sie diese URL aufrufen: `http://serveraddress:serverport/system/console/components`
1. Suchen Sie nach den folgenden Komponenten.
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeGenerateServlet`
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeAccessTokenGenerator`
1. Klicken Sie links neben den Komponenten auf das Wiedergabesymbol.

![Ein Codeausschnitt der Komponentenliste, der OAuthCodeGenerateServlet und OAuthCodeAccessTokenGenerator enthält](assets/oauth-components-play.png)

Bestätigen Sie abschließend die Konfiguration, indem Sie:

1. Zur Adresse der Veröffentlichungsinstanz wechseln und sich als Admin anmelden
1. eine neue Registerkarte im Browser öffnen und zu `http://serveraddress:serverport/services/mailer/oauth2/authorize` navigieren. Dadurch werden Sie auf die Seite Ihres SMTP-Anbieters, in diesem Fall Outlook, weitergeleitet.
1. Anmelden und Einverständnis zur Erteilung der erforderlichen Berechtigungen
1. Nach der Zustimmung wird das Token im Repository gespeichert. Sie können es unter `accessToken` aufrufen, indem Sie direkt auf diese URL auf Ihrer Veröffentlichungsinstanz zugreifen: `http://serveraddress:serverport/crx/de/index.jsp#/conf/global/settings/mailer/oauth`
