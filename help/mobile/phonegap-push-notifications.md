---
title: Push-Benachrichtigungen
seo-title: Push Notifications
description: Auf dieser Seite erfahren Sie, wie Sie Push-Benachrichtigungen in einer AEM Mobile-App verwenden.
seo-description: Follow this page to learn about how to use push notifications in an AEM Mobile app.
uuid: 0ed8b183-ef81-487f-8f35-934d74ec82af
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: ed8c51d2-5aac-4fe8-89e8-c175d4ea1374
exl-id: 375f2f40-1b98-4e21-adee-cbea274e6a2a
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '3273'
ht-degree: 2%

---

# Push-Benachrichtigungen{#push-notifications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Möglichkeit, Ihre AEM Mobile-App-Benutzer sofort mit wichtigen Benachrichtigungen zu benachrichtigen, ist für den Wert einer App und ihrer Marketingkampagnen von entscheidender Bedeutung. In unserem Beispiel werden die Schritte beschrieben, die unternommen werden müssen, damit Ihre App Push-Benachrichtigungen empfangen kann, sowie die Konfiguration und der Versand von Push-Benachrichtigungen von AEM Mobile an die am Telefon installierte App. Außerdem wird in diesem Abschnitt beschrieben, wie Sie die [Deep-Linking](#deeplinking) -Funktion für Ihre Push-Benachrichtigungen verwenden.

>[!NOTE]
>
>*Push-Benachrichtigungen werden nicht garantiert. sie sind eher wie Ankündigungen. Es wird alles daran gesetzt, sicherzustellen, dass jeder sie erhält, aber sie kein garantierter Bereitstellungsmechanismus sind. Außerdem kann die Bereitstellungszeit für eine Push-Benachrichtigung zwischen weniger als einer Sekunde und bis zu einer halben Stunde variieren.*

Die Verwendung von Push-Benachrichtigungen mit AEM erfordert einige verschiedene Technologien. Zunächst muss ein Push-Benachrichtigungs-Dienstleister zur Verwaltung von Benachrichtigungen und Geräten verwendet werden (AEM tut dies noch nicht). Zwei Anbieter sind standardmäßig mit AEM konfiguriert: [Amazon Simple Notification Service](https://aws.amazon.com/sns/) (oder SNS) und [Pushwoosh](https://www.pushwoosh.com/). Zweitens muss die Push-Technologie für das jeweilige mobile Betriebssystem den entsprechenden Dienst (Apple Push Notification Service (APNS) für iOS-Geräte) durchlaufen. und Google Cloud Messaging (oder GCM) für Android-Geräte. Obwohl AEM nicht direkt mit diesen plattformspezifischen Diensten kommuniziert, müssen einige zugehörige Konfigurationsinformationen von AEM zusammen mit den Benachrichtigungen bereitgestellt werden, damit diese Dienste den Push-Vorgang ausführen können.

Nach der Installation und Konfiguration (wie unten beschrieben) funktioniert dies wie folgt:

1. In AEM wird eine Push-Benachrichtigung erstellt und an den Dienstleister (Amazon SNS oder Pushwoosh) gesendet.
1. Der Dienstleister erhält sie und sendet sie an den Hauptanbieter (APNS oder GCM).
1. Der Hauptanbieter sendet die Benachrichtigung an alle Geräte, die für diese Push-Benachrichtigung registriert sind. Für jedes Gerät wird das Mobilfunknetz für Daten oder WiFi verwendet, je nachdem, was derzeit auf dem Gerät verfügbar ist.
1. Die Benachrichtigung wird auf dem Gerät angezeigt, wenn die App, für die sie registriert ist, nicht ausgeführt wird. Ein Benutzer, der auf die Benachrichtigung tippt, startet die App und zeigt die Benachrichtigung in der App an. Wenn die Anwendung bereits ausgeführt wird, wird nur die In-App-Benachrichtigung angezeigt.

Diese Version von AEM unterstützt Mobilgeräte mit iOS und Android.

## Überblick und Verfahren {#overview-and-procedure}

Um Push-Benachrichtigungen in einer AEM Mobile-App zu verwenden, müssen die folgenden allgemeinen Schritte ausgeführt werden.

Normalerweise führt ein AEM-Entwickler Folgendes durch:

1. Bei Apple- und Google-Messaging-Diensten registrieren
1. Registrieren Sie sich bei einem Push-Messaging-Dienst und konfigurieren Sie ihn.
1. Push-Unterstützung zur App hinzufügen
1. Vorbereiten eines Telefons auf Tests

Ein AEM Administrator wird Folgendes tun:

1. Push-Benachrichtigungen für AEM Apps konfigurieren
1. Erstellen und Bereitstellen der App
1. Push-Benachrichtigung senden
1. Deep-Linking konfigurieren *(optional)*

### Schritt 1: Bei Apple- und Google-Messaging-Diensten registrieren {#step-register-with-apple-and-google-messaging-services}

#### Verwenden des Apple Push Notification Service (APNS) {#using-the-apple-push-notification-service-apns}

Navigieren Sie zur Apple-Seite [here](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html) , um sich mit dem Push-Benachrichtigungsdienst von Apple vertraut zu machen.

Für die Verwendung von APNS benötigen Sie eine **Zertifikat** Datei (eine .cer-Datei), eine Push-Datei **Privater Schlüssel** (eine .p12-Datei) und **Passwort für privaten Schlüssel** aus Apple. Anweisungen dazu finden Sie [here](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ProvisioningDevelopment.html).

#### Verwenden des Google Cloud Messaging-Dienstes (GCM) {#using-the-google-cloud-messaging-gcm-service}

>[!NOTE]
>
>Google ersetzt GCM durch einen ähnlichen Dienst namens Firebase Cloud Messaging (FCM). Weitere Informationen zu FCM finden Sie unter [here](https://developers.google.com/cloud-messaging/faq).

Navigieren Sie zur Google-Seite [here](https://developer.android.com/google/gcm/index.html) , um sich mit Google Cloud Messaging für Android vertraut zu machen.

Führen Sie die folgenden Schritte aus [here](https://developer.android.com/google/gcm/gs.html) nach **Erstellen eines Google-API-Projekts**, **Aktivieren des GCM-Dienstes** und **Abrufen eines API-Schlüssels**. Sie benötigen die **API-Schlüssel** , um Push-Benachrichtigungen an Android-Geräte zu senden. Zeichnen Sie außerdem Ihre **Projektnummer**, was manchmal auch als **GCM Sender Id**.

Die folgenden Schritte zeigen eine andere Methode zum Erstellen von GCM-API-Schlüsseln:

1. Melden Sie sich bei Google an und wechseln Sie zur [Googles Entwicklerseite](https://developers.google.com/mobile/add?platform=android&amp;cntapi=gcm).
1. Wählen Sie Ihre App aus der Liste aus (oder erstellen Sie eine neue).
1. Geben Sie unter Android Package Name Ihre App-ID ein, d. h. `com.adobe.cq.mobile.weretail.outdoorsapp`. (Wenn dies nicht funktioniert, versuchen Sie es erneut mit &quot;test.test&quot;.)
1. Klicken **Weiter zur Auswahl und Konfiguration von Diensten**
1. Wählen Sie Cloud Messaging und klicken Sie dann auf **Google Cloud Messaging aktivieren**.
1. Daraufhin werden der neue Server-API-Schlüssel und die (neue oder vorhandene) Sender-ID angezeigt.

>[!NOTE]
>
>Notieren Sie sich den Server-API-Schlüssel. Dieser Wert wird auf der Site Ihres Push-Providers eingegeben.

### Schritt 2: Registrieren und Konfigurieren eines Push-Messaging-Dienstes {#step-register-and-configure-a-push-messaging-service}

AEM ist für die Verwendung eines der drei Dienste für Push-Benachrichtigungen konfiguriert:

* Amazon SNS
* Pushwoosh
* Adobe Mobile Services

*Amazon SNS* und *Pushwoosh* -Konfigurationen ermöglichen es Ihnen, Push-Benachrichtigungen von AEM Bildschirmen aus zu senden.

*Adobe Mobile Services* Mit der -Konfiguration können Sie Push-Benachrichtigungen von Adobe Mobile Services mithilfe eines Adobe Analytics-Kontos konfigurieren und senden (die App muss jedoch mit dieser Konfiguration erstellt werden, um AMS-Push-Benachrichtigungen zu aktivieren).

#### Verwenden des Amazon SNS-Messaging-Dienstes {#using-the-amazon-sns-messaging-service}

>[!NOTE]
>
>*Informationen zu Amazon SNS und einem Link zum Erstellen eines neuen AWS-Kontos finden Sie unter [here](https://aws.amazon.com/sns/). Sie können ein kostenloses Konto für ein Jahr erhalten.*

Wenn Sie Amazon SNS nicht verwenden möchten, können Sie diese Schritte überspringen.

Führen Sie die folgenden Schritte aus, um Amazon SNS für Push-Benachrichtigungen einzurichten:

1. **Bei Amazon SNS registrieren**

   1. Notieren Sie Ihre Konto-ID. Das Format sollte zwölf Ziffern ohne Leerzeichen oder Gedankenstriche aufweisen, d. h. &quot;123456789012&quot;.
   1. Stellen Sie sicher, dass Sie sich in der Region &quot;us-east&quot;oder &quot;eu&quot;befinden, da für einen späteren Schritt (Erstellung eines Identitäts-Pools) eine dieser Voraussetzungen erforderlich ist.
   1. Melden Sie sich nach der Registrierung bei der Verwaltungskonsole an und wählen Sie [SNS](https://console.aws.amazon.com/sns/) (Push-Benachrichtigungsdienst). Klicken Sie auf &quot;Erste Schritte&quot;, wenn es angezeigt wird.

1. **Zugriffsschlüssel und -kennung erstellen**

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie im Menü Sicherheitsberechtigungen aus.
   1. Klicken Sie auf Zugriffsschlüssel und klicken Sie in der unten stehenden Platzierung auf **Neuen Zugriffsschlüssel erstellen**.
   1. Klicken **Zugriffsschlüssel anzeigen**, kopieren und speichern Sie die angezeigte Zugriffsschlüssel-ID und den geheimen Zugriffsschlüssel. Wenn Sie die Option zum Herunterladen der Schlüssel auswählen, erhalten Sie eine CSV-Datei, die dieselben Werte enthält.
   1. Andere sicherheitsbezogene Zertifikate und andere können auf dieser Seite verwaltet werden.

   >[!NOTE]
   >
   >Ein Zugriffsschlüssel kann für mehrere Apps verwendet werden.

   Für Organisationen, die ein &quot;AWS Sandbox&quot;-Konto verwenden, sind die Schritte sehr ähnlich und werden hier beschrieben:

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie im Menü Meine Sicherheitsanmeldeinformationen aus.
   1. Klicken Sie in der linken Aktionsliste auf Benutzer und wählen Sie Ihren Benutzernamen aus.
   1. Klicken Sie auf die Registerkarte Sicherheitsberechtigungen .
   1. Hier sehen Sie Ihre Schlüssel und erstellen neue Schlüssel. Speichern Sie die Schlüssel zur späteren Verwendung.


1. **Thema erstellen**

   1. Klicken **Thema erstellen** und wählen Sie einen Themennamen. Notieren Sie alle Felder wie Themenbereich-ARN, Themeneigentümer, Region, Anzeigename.
   1. Klicken **Andere Themenaktionen** > **Themenrichtlinie bearbeiten**. under **Diese Benutzer können dieses Thema abonnieren** auswählen **Alle.**
   1. Klicken **Richtlinie aktualisieren**.

   >[!NOTE]
   >
   >Sie können mehrere Themen für verschiedene Szenarien wie Entwicklung, Test, Demo usw. erstellen. Der Rest der SNS-Konfiguration kann unverändert bleiben. Erstellen Sie die App mit dem anderen Thema. Push-Benachrichtigungen, die an dieses Thema gesendet werden, werden nur von der mit diesem Thema erstellten App empfangen.

1. **Erstellen von Platform-Anwendungen**

   1. Klicken Sie auf Anwendungen und dann auf Platform Application erstellen. Wählen Sie einen Namen und eine Plattform (APNS für iOS, GCM für Android). Je nach Plattform müssen andere Felder ausgefüllt werden:

      1. Bei APNS müssen eine P12-Datei, ein Kennwort, ein Zertifikat und ein privater Schlüssel eingegeben werden. Diese hätten im Laufe des Schritts erreicht werden müssen *Verwenden des Apple Push Notification Service (APNS)* höher.
      1. Für GCM muss ein API-Schlüssel eingegeben werden. Dies hätte im Rahmen des Schritts erreicht werden müssen *Verwenden des Google Cloud Messaging-Dienstes (GCM)* höher.
   1. Wiederholen Sie den obigen Schritt einmal für jede Plattform, die Sie unterstützen. Um sowohl an iOS als auch an Android pushen zu können, müssen zwei Plattformanwendungen erstellt werden.


1. **Erstellen eines Identitäts-Pools**

   1. Verwendung [Kognito](https://console.aws.amazon.com/cognito) , um einen Identitäts-Pool zu erstellen, in dem grundlegende Daten nicht authentifizierter Benutzer gespeichert werden. Amazon Cognito unterstützt derzeit nur die Regionen &quot;us-east&quot;und &quot;eu&quot;.
   1. Geben Sie ihm einen Namen und aktivieren Sie das Kontrollkästchen &quot;Zugriff auf nicht authentifizierte Identitäten aktivieren&quot;.
   1. Auf der nächsten Seite (&quot;*Ihre Kognito-Identitäten benötigen Zugriff auf Ihre Ressourcen*&quot;) klicken Sie auf Zulassen.
   1. Klicken Sie oben rechts auf der Seite auf den Link &quot;*Identitäts-Pool bearbeiten&quot;*. Die Identitäts-Pool-ID wird angezeigt. Speichern Sie diesen Text für später.
   1. Wählen Sie auf derselben Seite das Dropdown-Menü neben &quot;Nicht authentifizierte Rolle&quot;aus und stellen Sie sicher, dass sie die Rolle &quot;Kognito_&quot;hat.&lt;pool name=&quot;&quot;>UnauthRole ausgewählt. Speichern Sie Ihre Änderungen.

1. **Zugriff konfigurieren**

   1. Anmelden bei [Identitäts- und Zugriffsverwaltung](https://console.aws.amazon.com/iam/home) (IAM)
   1. Rollen auswählen
   1. Klicken Sie auf die im vorherigen Schritt erstellte Rolle namens Cognito_&lt;youridentitypoolname>Unauth_Role. Notieren Sie sich die angezeigte Rolle ARN.
   1. Öffnen Sie &quot;Inline-Richtlinien&quot;, falls sie noch nicht geöffnet sind. Dort sollte eine Richtlinie mit einem Namen wie &quot;oneClick_Cognito_&quot;angezeigt werden.&lt;youridentitypoolname>Unauth_Role_1234567890123.
   1. Klicken Sie auf &quot;Richtlinie bearbeiten&quot;. Ersetzen Sie den Inhalt des Richtliniendokuments durch dieses JSON-Snippet:

   <table>
    <tbody>
     <tr>
     <td><p> </p> <p>{</p> <p> "Version": "10.10.2012",</p> <p> "Aussage": [</p> <p> {</p> <p> "Aktion": [</p> <p> "mobileanalytics:PutEvents",</p> <p> "cognito-sync:*",</p> <p> "SNS:CreatePlatformEndpoint",</p> <p> "SNS:Subscribe"</p> <p> ],</p> <p> "Effekt": "Allow",</p> <p> "Ressource": [</p> <p> "*"</p> <p> ]</p> <p> }</p> <p> ]</p> <p>}</p> <p> </p> </td>
     </tr>
    </tbody>
    </table>

   1. Klicken Sie auf **Richtlinie anwenden**


#### Pushwoosh-Messaging-Dienst verwenden {#using-the-pushwoosh-messaging-service}

Wenn Sie Pushwoosh nicht verwenden möchten, können Sie diesen Schritt überspringen.

So verwenden Sie Pushwoosh:

1. **Registrieren bei Pushwoosh**

   1. Gehen Sie zu pushwoosh.com und erstellen Sie ein neues Konto.

1. **API-Zugriffstoken erstellen**

   1. Rufen Sie auf der Pushwoosh-Site das Menüelement API-Zugriff auf auf auf, um ein API-Zugriffstoken zu generieren. Sie müssen dies sicher aufzeichnen.

1. **Neue App erstellen**

   1. Zur Unterstützung von Android müssen Sie Ihren GCM-API-Schlüssel angeben.
   1. Wählen Sie beim Konfigurieren der App Cordova als Framework.
   1. Für den iOS-Support müssen Sie die Zertifikatdatei (.cer), das Push-Zertifikat (.p12) und das Kennwort für den privaten Schlüssel angeben. Diese sollten von der APNS-Site von Apple abgerufen worden sein. Wählen Sie für Framework Cordova aus.
   1. Pushwoosh generiert eine App-ID für diese App im Format &quot;XXXXX-XXXXX&quot;, wobei jedes X ein hexadezimaler Wert (0 bis F) ist.

>[!NOTE]
>
>*Wenn eine zweite App in AEM mit derselben App-ID (und anderen zugehörigen Werten) konfiguriert ist: API-Zugriffstoken und GCM-ID) werden alle Push-Benachrichtigungen, die über die zweite App am AEM gesendet werden, an jede andere App mit dieser App-ID gesendet.*

### Schritt 3: Push-Unterstützung zur App hinzufügen {#step-add-push-support-to-the-app}

#### Hinzufügen der ContentSync-Konfiguration {#add-contentsync-configuration}

Erstellen Sie zwei Inhaltsknoten (einen in app-config und einen in app-config-dev) namens notificationsConfig:

* /content/`<your app>`/shell/jcr:content/page-app/app-config-dev/notificationsConfig
* /content/`<your app>`/shell/jcr:content/page-app/app-config/notificationsConfig

Mit diesen Eigenschaften (.content.xml files) :
&lt;jcr:root xmlns:jcr=&quot; &lt;span id=&quot; translate=&quot;no&quot; />https://www.jcp.org/jcr/1.0](https://www.jcp.org/jcr/1.0)&quot; xmlns:nt=&quot; [https://www.jcp.org/jcr/nt/1.0](https://www.jcp.org/jcr/nt/1.0)&quot; jcr:primaryType=&quot;nt:unstructured&quot; excludeProperties=&quot;[appAPIAccessToken]&quot; path=&quot;../../../...&quot;
[
targetRootDirectory=&quot;www&quot; type=&quot;notificationsConfig&quot;/>

>[!NOTE]
>
>Der Content Sync-Handler sucht nach diesen Knoten, und wenn sie nicht vorhanden sind, schreibt er nicht die Datei &quot;page-notifications-config.json&quot;.

#### Client-Bibliotheken hinzufügen {#add-client-libraries}

Die Client-Bibliotheken der Push-Benachrichtigung müssen der App hinzugefügt werden, indem Sie die folgenden Schritte ausführen:

In CRXDE Lite:

1. Navigieren Sie zu */etc/designs/phonegap/&lt;app name=&quot;&quot;>/clientlibsall.*
1. Doppelklicken Sie im Eigenschaftenbereich auf den Einbettungsabschnitt.
1. Fügen Sie im angezeigten Dialogfeld eine neue Client-Bibliothek hinzu, indem Sie auf die Schaltfläche + klicken.
1. Fügen Sie im neuen Textfeld &quot;cq.mobile.push&quot;hinzu und klicken Sie auf &quot;OK&quot;.
1. Fügen Sie eine weitere mit dem Namen cq.mobile.push.amazon hinzu und klicken Sie auf &quot;OK&quot;.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Wenn Push-Benachrichtigungen aus Platzgründen in der App entfernt oder nicht verwendet werden und um Konsolenfehlermeldungen zu vermeiden, entfernen Sie diese Clientlibs aus Ihrer App.

### Schritt 4: Vorbereiten eines Telefons für Tests {#step-prepare-a-phone-for-testing}

>[!NOTE]
>
>*Für Push-Benachrichtigungen müssen Sie auf einem eigentlichen Gerät testen, da Emulatoren keine Push-Benachrichtigungen empfangen können.*

#### iOS {#ios}

Für iOS müssen Sie einen Mac OS-Computer verwenden und der [iOS Developer Program](https://developer.apple.com/programs/ios/). Einige Unternehmen verfügen über Unternehmenslizenzen, die für alle Entwickler verfügbar sein können.

In XCode 8.1 müssen Sie vor der Verwendung von Push-Benachrichtigungen in Ihrem Projekt zur Registerkarte Funktionen wechseln und den Umschalter Push-Benachrichtigungen aktivieren aktivieren.

#### Android {#android}

So installieren Sie die App über CLI auf einem Android-Telefon (siehe unten): **Schritt 6: Erstellen und Bereitstellen des Programms**), müssen Sie zunächst das Telefon in den &quot;Entwicklermodus&quot;stellen. Siehe [Aktivieren der Entwickleroptionen auf dem Gerät](https://developer.android.com/tools/device.html#developer-device-options) für weitere Informationen.

### Schritt 5: Push-Benachrichtigungen für AEM Apps konfigurieren {#step-configure-push-on-aem-apps}

Vor der Erstellung und Bereitstellung auf Ihrem konfigurierten Mobilgerät müssen Sie die Benachrichtigungseinstellungen für den Messaging-Dienst konfigurieren, den Sie verwenden möchten.

1. Erstellen Sie die entsprechenden Berechtigungsgruppen für Push-Benachrichtigungen.
1. Melden Sie sich bei AEM als passender Benutzer an und klicken Sie auf die Registerkarte Apps .
1. Klicken Sie auf die App.
1. Suchen Sie die Kachel Cloud Services verwalten und klicken Sie auf das Stiftsymbol, um Ihre Cloud-Konfigurationen zu ändern.
1. Wählen Sie als Benachrichtigungskonfiguration Amazon SNS Connection, Pushwoosh Connection oder Adobe Mobile Services aus.
1. Geben Sie die Eigenschaften des Providers ein und klicken Sie auf Senden , um sie zu speichern, und auf Fertig . Sie werden derzeit nicht remote überprüft, außer im Falle von AMS.
1. Jetzt sollte die Konfiguration angezeigt werden, die Sie gerade in der Kachel Cloud Services verwalten eingegeben haben.

### Schritt 6: Erstellen und Bereitstellen der App {#step-build-and-deploy-the-app}

**Hinweis:** Lesen Sie auch unsere Anweisungen [here](/help/mobile/building-app-mobile-phonegap.md) zum Erstellen von PhoneGap-Anwendungen.

Es gibt zwei Möglichkeiten, Ihre App mit PhoneGap zu erstellen und bereitzustellen.

**Hinweis:** Für Push-Benachrichtigungstests reichen Emulatoren nicht aus, da Push-Benachrichtigungen ein bestimmtes Protokoll zwischen dem Push-Provider (Apple oder Google) und dem Gerät verwenden. Die aktuelle Mac-/PC-Hardware und -Emulatoren unterstützen dies nicht.

1. *PhoneGap Build* ist ein von PhoneGap angebotener Dienst, mit dem Sie Ihre App auf ihren Servern erstellen und direkt auf Ihr Gerät herunterladen können. Siehe Abschnitt [Dokumentation zu PhoneGap Build](https://build.phonegap.com/) , um zu erfahren, wie Sie PhoneGap Build einrichten und verwenden.

1. *PhoneGap-Befehlszeilenschnittstelle* (CLI) ermöglicht Ihnen die Verwendung einer Vielzahl von PhoneGap-Befehlen in Ihrer Befehlszeile zum Erstellen, Debuggen und Bereitstellen Ihrer App. Siehe Abschnitt [Dokumentation für PhoneGap-Entwickler](https://docs.phonegap.com/en/edge/guide_cli_index.md.html#The%20Command-Line%20Interface) , um zu erfahren, wie Sie PhoneGap CLI einrichten und verwenden.

### Schritt 7: Push-Benachrichtigung senden {#step-send-a-push-notification}

Gehen Sie wie folgt vor, um eine neue Benachrichtigung zu erstellen und zu senden.

1. Neue Benachrichtigung erstellen

   * Suchen Sie im Dashboard Ihrer AEM Mobile-App die Kachel Push-Benachrichtigungen .
   * Wählen Sie im Menü rechts oben &quot;Erstellen&quot;. Beachten Sie, dass diese Schaltfläche erst verfügbar ist, wenn die Cloud-Konfiguration zum ersten Mal festgelegt wurde.
   * Geben Sie im Assistenten zum Erstellen von Benachrichtigungen einen Titel und eine Nachricht ein und klicken Sie dann auf die Schaltfläche &quot;Erstellen&quot;. Ihre Benachrichtigung kann jetzt sofort oder später gesendet werden. Es kann bearbeitet und die Nachricht und/oder der Titel geändert und gespeichert werden.

1. Benachrichtigung senden

   * Suchen Sie im Apps-Dashboard die Kachel Push-Benachrichtigungen .
   * Wählen Sie die Benachrichtigung aus oder klicken Sie auf die Detailschaltfläche unten rechts (). . .), um die Liste der Benachrichtigungen anzuzeigen. Diese Liste gibt auch an, ob eine Benachrichtigung versandbereit oder bereits gesendet werden kann oder ob beim Versand ein Fehler aufgetreten ist.
   * Aktivieren Sie das Kontrollkästchen für eine Benachrichtigung (nur) und klicken Sie auf die Schaltfläche &quot;Benachrichtigung senden&quot; oberhalb der Liste. Sie haben die Möglichkeit, die Benachrichtigung im angezeigten Dialogfeld &quot;Abbrechen&quot;oder &quot;Senden&quot;zu senden.

1. Umgang mit den Ergebnissen

   * Wenn der Push-Benachrichtigungsdienst (Amazon SNS oder Pushwoosh) die Sendeanforderung erhält, sie als gültig bestätigt und erfolgreich an die nativen Provider (APNS und GCM) sendet, wird das Dialogfeld &quot;Senden&quot;ohne Nachricht geschlossen. In der Benachrichtigungsliste wird der Status dieser Benachrichtigung als Gesendet angezeigt.
   * Wenn der Push-Versand fehlschlägt, wird im Dialogfeld eine Meldung angezeigt, die das Problem angibt. In der Benachrichtigungsliste wird der Status dieser Benachrichtigung als Fehler aufgeführt. Wenn das Problem behoben wurde, kann die Benachrichtigung erneut gesendet werden. Im Falle eines Fehlers sollten zusätzliche Fehlerinformationen im Serverfehlerprotokoll angezeigt werden.
   * Beachten Sie, dass es einige Plattformunterschiede zwischen Push-Benachrichtigungen in iOS und Android gibt. Dazu gehören:

      * Die Erstellung mit CLI startet die App, nachdem sie auf Android bereitgestellt wurde. In iOS müssen Sie es manuell starten. Da der Schritt zur Push-Registrierung beim Start erfolgt, können Android-Apps Push-Benachrichtigungen sofort empfangen (da er gestartet und registriert sein wird), iOS-Apps hingegen nicht.
      * Unter Android befindet sich der Text der Schaltfläche OK in Großbuchstaben (und in allen anderen Schaltflächen, die in der In-App-Benachrichtigung hinzugefügt werden), in iOS nicht.

Bei AMS-Push-Benachrichtigungen müssen Benachrichtigungen erstellt und vom AMS-Server gesendet werden. AMS bietet zusätzliche Push-Benachrichtigungsfunktionen, die über die Funktionen AEM Benachrichtigungen mit AWS und Pushwoosh hinausgehen.

>[!NOTE]
>
>*Push-Benachrichtigungen werden nicht garantiert. sie sind eher wie Ankündigungen. Es wird versucht sicherzustellen, dass jeder es hört, aber es sich nicht um einen garantierten Bereitstellungsmechanismus handelt. Außerdem kann die Bereitstellungszeit für eine Push-Benachrichtigung zwischen weniger als einer Sekunde und bis zu einer halben Stunde variieren.*

### Konfigurieren von Deep-Linking mit Push-Benachrichtigungen {#configuring-deep-linking-with-push-notifications}

Was ist Deep Linking? Im Kontext einer Push-Benachrichtigung ist dies eine Möglichkeit, das Öffnen oder Weiterleiten einer App an eine angegebene Position innerhalb der App zu ermöglichen (sofern diese geöffnet ist).

Wie funktioniert es? Der Autor einer Push-Benachrichtigung fügt optional eine Schaltflächenbeschriftung hinzu (d. h. &quot;Zeig mir!&quot;) in die Benachrichtigung ein und wählt über einen visuellen Pfad-Browser die Seite aus, die in der Benachrichtigung verknüpft werden soll. Beim Senden erfolgt der Push-Vorgang wie gewohnt. In der In-App-Nachricht wird die Schaltfläche OK durch die Schaltfläche &quot;Beenden&quot;ersetzt und die neue Schaltfläche angegeben (&quot;Anzeigen!&quot;) angezeigt. Wenn Sie auf die neue Schaltfläche klicken, wird die App zur angegebenen Seite innerhalb der App weitergeleitet. Wenn Sie auf Beenden klicken, wird die Nachricht einfach verworfen.

Wenn die App nicht geöffnet ist, wird die Schattierung normal angezeigt. Wenn Sie die Benachrichtigung im Schatten bearbeiten, wird die App geöffnet und dem Benutzer dann die Deep-Link-Schaltflächen entsprechend der Konfiguration in der Push-Benachrichtigung angezeigt.

Erstellen Sie die Benachrichtigung, fügen Sie einen Schaltflächentext und einen Link-Pfad für den optionalen Deep-Link hinzu:

>[!CAUTION]
>
>.Gehen Sie wie folgt vor, um auf die Kachel Push-Benachrichtigung in Ihrem Dashboard zuzugreifen.

1. Klicken Sie oben rechts im **Cloud Services verwalten** Kachel.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Wählen Sie die **Pushwoosh-Verbindung**. Klicken Sie auf **Weiter**.

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. Geben Sie die Details der Eigenschaften ein und klicken Sie auf **Einsenden**.

   ![chlimage_1-110](assets/chlimage_1-110.png)

   Wenn Sie Ihre Konfiguration übermitteln, wird die **Push-Benachrichtigungen** wird im Dashboard angezeigt.

   ![chlimage_1-111](assets/chlimage_1-111.png)

### Assistent zum Erstellen von Benachrichtigungen {#create-notification-wizard}

Einmal **Push-Benachrichtigungen** in Ihrem Dashboard angezeigt werden, verwenden Sie den Assistenten zur Erstellung von Benachrichtigungen, um den Inhalt hinzuzufügen:

1. Klicken Sie oben rechts im **Push-Benachrichtigungen** -Kachel zum Öffnen **Benachrichtigungsassistent erstellen**.

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. Durch Klicken auf das Symbol &quot;Durchsuchen&quot;im Link-Pfad wird dem Benutzer die Inhaltsstruktur der App angezeigt.

   Nachdem Sie den Pfad ausgewählt haben, klicken Sie auf das Häkchensymbol.

   ![chlimage_1-113](assets/chlimage_1-113.png)

   >[!NOTE]
   >
   >Der Text der Link-Schaltfläche ist auf 20 Zeichen begrenzt.
   >
   >Wenn der Endbenutzer nicht über die neueste Version der Anwendung verfügt und der verknüpfte Pfad nicht verfügbar ist, führt die Bestätigung der Deep-Link-Aktion dazu, dass der Benutzer zur Hauptseite der App gelangt.

1. Geben Sie die **Textdetails** im **Benachrichtigungsassistent erstellen** und klicken Sie auf **Erstellen**.

   ![chlimage_1-114](assets/chlimage_1-114.png)

   Öffnen Sie die Details, indem Sie auf die von Ihnen erstellte Push-Benachrichtigung im **Push-Benachrichtigungen** Kachel.

   Sie können Eigenschaften bearbeiten, Benachrichtigungen senden oder die Benachrichtigung löschen.

   ![chlimage_1-115](assets/chlimage_1-115.png)

>[!NOTE]
>
>**Zusätzliche Informationen**:
>
>Pushwoosh und Amazon SNS werden nach Version 6.4 nicht mehr unterstützt und sind als Add-On über Package Share verfügbar.

### Die nächsten Schritte {#the-next-steps}

Sobald Sie die Details zu Push-Benachrichtigungen für Ihre App kennen, lesen Sie [AEM Mobile Content Personalization](/help/mobile/phonegap-aem-mobile-content-personalization.md).
