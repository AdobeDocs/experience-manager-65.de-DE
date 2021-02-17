---
title: Push-Benachrichtigungen
seo-title: Push-Benachrichtigungen
description: Auf dieser Seite erfahren Sie, wie Sie Push-Benachrichtigungen in einer AEM Mobile-App verwenden.
seo-description: Auf dieser Seite erfahren Sie, wie Sie Push-Benachrichtigungen in einer AEM Mobile-App verwenden.
uuid: 0ed8b183-ef81-487f-8f35-934d74ec82af
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: ed8c51d2-5aac-4fe8-89e8-c175d4ea1374
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d
workflow-type: tm+mt
source-wordcount: '3291'
ht-degree: 2%

---


# Push-Benachrichtigungen{#push-notifications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Möglichkeit, Ihre AEM Mobile-App-Benutzer umgehend mit wichtigen Benachrichtigungen zu benachrichtigen, ist für den Wert einer mobilen App und deren Marketing-Kampagnen von entscheidender Bedeutung. Hier werden die Schritte beschrieben, die unternommen werden müssen, damit Ihre App Push-Benachrichtigungen empfangen kann, sowie die Konfiguration und das Senden von Push-Benachrichtigungen von AEM Mobile an die App, die auf dem Smartphone installiert ist. In diesem Abschnitt wird außerdem beschrieben, wie Sie die Funktion [Deep Linking](#deeplinking) für Ihre Push-Benachrichtigungen konfigurieren.

>[!NOTE]
>
>*Push-Benachrichtigungen werden nicht als Versand garantiert. sie sind eher wie Mitteilungen. Es wird alles getan, um sicherzustellen, dass jeder sie erhält, aber sie stellen keinen garantierten Versand dar. Außerdem kann die Bereitstellungszeit für einen Push von weniger als einer Sekunde bis zu einer halben Stunde variieren.*

Die Verwendung von Push-Benachrichtigungen mit AEM erfordert einige verschiedene Technologien. Zunächst muss ein Push-Benachrichtigungs-Dienstleister zur Verwaltung von Benachrichtigungen und Geräten verwendet werden (AEM tut dies noch nicht). Zwei Anbieter sind standardmäßig mit AEM konfiguriert: [Amazon Simple Notification Service](https://aws.amazon.com/sns/) (oder SNS) und [Pushwoosh](https://www.pushwoosh.com/). Zweitens muss die Push-Technologie für das jeweilige mobile Betriebssystem den entsprechenden Dienst durchlaufen — Apple&#39;s Push Notification Service (APNS) für iOS-Geräte; und Google Cloud Messaging (oder GCM) für Android-Geräte. Obwohl AEM nicht direkt mit diesen plattformspezifischen Diensten kommuniziert, müssen einige zugehörige Konfigurationsinformationen von AEM zusammen mit den Benachrichtigungen bereitgestellt werden, damit diese Dienste den Push ausführen können.

Nach der Installation und Konfiguration (wie unten beschrieben) funktioniert es wie folgt:

1. Eine Push-Benachrichtigung wird in AEM erstellt und an den Dienstleister (Amazon SNS oder Pushwoosh) gesendet.
1. Der Dienstleister empfängt ihn und sendet ihn an den Hauptanbieter (APNS oder GCM).
1. Der Hauptanbieter leitet die Benachrichtigung an alle Geräte weiter, die für diesen Push registriert sind. Für jedes Gerät verwendet es das zelluläre Datennetzwerk oder WiFi, je nachdem, welches Gerät aktuell verfügbar ist.
1. Die Benachrichtigung wird auf dem Gerät angezeigt, wenn die App, für die sie registriert ist, nicht ausgeführt wird. Wenn ein Benutzer auf die Benachrichtigung tippt, wird die App Beginn und die Benachrichtigung in der App angezeigt. Wenn die Anwendung bereits ausgeführt wird, wird nur die In-App-Benachrichtigung angezeigt.

Diese Version von AEM unterstützt iOS- und Android-Mobilgeräte.

## Übersicht und Verfahren {#overview-and-procedure}

Um Push-Benachrichtigungen in einer AEM Mobile-App zu verwenden, müssen die folgenden Schritte auf hoher Ebene durchgeführt werden.

Normalerweise hat ein AEM Entwickler folgende Aufgaben:

1. Melden Sie sich bei Apple und Google Messaging Services an
1. Registrieren Sie sich bei einem Push-Nachrichten-Dienst und konfigurieren Sie ihn
1. hinzufügen Push-Unterstützung für die App
1. Vorbereiten eines Telefons für Tests

Ein AEM Administrator wird

1. Push-Vorgänge für AEM-Apps konfigurieren
1. Erstellen und Bereitstellen der App
1. Push-Benachrichtigung senden
1. Deep-Linking konfigurieren *(optional)*

### Schritt 1: Melden Sie sich bei Apple und Google Messaging Services {#step-register-with-apple-and-google-messaging-services} an

#### Verwenden des Apple Push Notification Service (APNS) {#using-the-apple-push-notification-service-apns}

Rufen Sie die Apple-Seite [hier](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html) auf, um sich mit dem Apple Push Notification Service vertraut zu machen.

Für die Verwendung von APNS benötigen Sie eine **Zertifikat**-Datei (eine .cer-Datei), einen Push **Private Key** (eine .p12-Datei) und ein **Private Key Password** von Apple. Anweisungen dazu finden Sie hier [hier](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ProvisioningDevelopment.html).

#### Verwenden des Google Cloud Messaging-Dienstes {#using-the-google-cloud-messaging-gcm-service}

>[!NOTE]
>
>Google ersetzt GCM durch einen ähnlichen Dienst namens Firebase Cloud Messaging (FCM). Weitere Informationen zu FCM erhalten Sie, wenn Sie [hier](https://developers.google.com/cloud-messaging/faq) klicken.

Gehen Sie zur Google-Seite [hier](https://developer.android.com/google/gcm/index.html), um sich mit Google Cloud Messaging für Android vertraut zu machen.

Sie müssen die Schritte [hier](https://developer.android.com/google/gcm/gs.html) bis **Google API-Projekt erstellen**, **GCM-Dienst aktivieren** und **Einen API-Schlüssel abrufen** ausführen. Sie benötigen den **API-Schlüssel**, um Push-Benachrichtigungen an Android-Geräte zu senden. Zeichnen Sie auch die **Projektnummer** auf, die auch manchmal als **GCM Sender-ID** bezeichnet wird.

Die folgenden Schritte zeigen eine andere Methode zum Erstellen von GCM-API-Schlüsseln:

1. Melden Sie sich bei Google an und gehen Sie zur Google-Entwicklerseite [Google.](https://developers.google.com/mobile/add?platform=android&amp;cntapi=gcm)
1. Wählen Sie Ihre App aus der Liste aus (oder erstellen Sie eine neue).
1. Geben Sie unter &quot;Android Package Name&quot;Ihre App-ID ein, d. h. `com.adobe.cq.mobile.weretail.outdoorsapp`. (Wenn dies nicht funktioniert, versuchen Sie es erneut mit &quot;test.test&quot;.)
1. Klicken Sie auf **Weiter zur Auswahl und Konfiguration der Dienste**
1. Wählen Sie Cloud Messaging und klicken Sie dann auf **Google Cloud Messaging aktivieren**.
1. Anschließend werden der neue Server-API-Schlüssel und die (neue oder vorhandene) Sender-ID angezeigt.

>[!NOTE]
>
>Zeichnen Sie den Server-API-Schlüssel auf. Dieser Wert wird auf der Site Ihres Push-Providers eingegeben.

### Schritt 2: Registrieren und Konfigurieren eines Push-Benachrichtigungsdiensts {#step-register-and-configure-a-push-messaging-service}

AEM ist für die Verwendung eines der drei Dienste für Push-Benachrichtigungen konfiguriert:

* Amazon SNS
* Pushwoosh
* Adobe Mobile Services

*Amazon* SNS- und  ** Pushwooshs-Konfigurationen ermöglichen Ihnen das Senden von Push-Benachrichtigungen von AEM Bildschirmen.

*Mit der Konfiguration von Adobe Mobile* Services können Sie Push-Benachrichtigungen von Adobe Mobile Services aus mit einem Adobe Analytics-Konto konfigurieren und senden (die App muss jedoch mit diesem Konfigurationssatz erstellt werden, damit AMS-Push-Benachrichtigungen aktiviert werden).

#### Verwenden des Amazon SNS-Nachrichtendienstes {#using-the-amazon-sns-messaging-service}

>[!NOTE]
>
>*Informationen zum Amazon SNS und einen Link zum Erstellen eines neuen AWS-Kontos finden Sie  [hier](https://aws.amazon.com/sns/). Sie können ein kostenloses Konto für ein Jahr erhalten.*

Wenn Sie Amazon SNS nicht verwenden möchten, können Sie diese Schritte überspringen.

Führen Sie die folgenden Schritte aus, um Amazon SNS für Push-Benachrichtigungen einzurichten:

1. **Bei Amazon SNS registrieren**

   1. Notieren Sie Ihre Konto-ID. Das Format sollte zwölf Ziffern ohne Leerzeichen oder Bindestriche haben. &quot;123456789012&quot;.
   1. Stellen Sie sicher, dass Sie sich in der Region &quot;us-east&quot;oder &quot;eu&quot;befinden, da ein späterer Schritt (Identity Pool Creation) einen dieser Schritte erfordert.
   1. Melden Sie sich nach der Registrierung bei der Verwaltungskonsole an und wählen Sie [SNS](https://console.aws.amazon.com/sns/) (Push Notification Service). Klicken Sie auf &quot;Erste Schritte&quot;, wenn es angezeigt wird.

1. **Zugriffsschlüssel und ID erstellen**

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie im Menü Sicherheitsdaten.
   1. Klicken Sie auf Zugriffstasten und klicken Sie im unten stehenden Bereich auf **Neuen Zugriffsschlüssel erstellen**.
   1. Klicken Sie auf **Zugriffsschlüssel anzeigen** und kopieren Sie die angezeigte Zugriffsschlüssel-ID und den geheimen Zugriffsschlüssel und speichern Sie sie. Wenn Sie die Option zum Herunterladen der Schlüssel wählen, erhalten Sie eine CSV-Datei, die dieselben Werte enthält.
   1. Andere sicherheitsbezogene Zertifikate und andere können auf dieser Seite verwaltet werden.

   >[!NOTE]
   >
   >Ein Zugriffsschlüssel kann für mehrere Apps verwendet werden.

   Für Organisationen, die ein AWS-Sandbox-Konto verwenden, sind die Schritte sehr ähnlich und werden hier beschrieben:

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie Meine Sicherheitsdaten aus dem Menü.
   1. Klicken Sie in der linken Liste der Aktionen auf Benutzer und wählen Sie Ihren Benutzernamen.
   1. Klicken Sie auf die Registerkarte Sicherheitsberechtigungen.
   1. Von hier aus sehen Sie Ihre Schlüssel und erstellen Sie neue Schlüssel. Speichern Sie die Schlüssel zur späteren Verwendung.


1. **Thema erstellen**

   1. Klicken Sie auf **Thema erstellen** und wählen Sie einen Themennamen. Zeichnen Sie alle Felder wie Themen-ARN, Themeneigentümer, Region und Anzeigename auf.
   1. Klicken Sie auf **Andere Themenaktionen** > **Themenrichtlinie bearbeiten**. Wählen Sie unter **Zulassen, dass diese Benutzer dieses Thema** abonnieren, **Alle.**
   1. Klicken Sie auf **Richtlinie aktualisieren**.

   >[!NOTE]
   >
   >Sie können mehrere Themen für verschiedene Szenarien erstellen, z. B. für dev, test, demo usw. Der Rest der SNS-Konfiguration kann unverändert bleiben. Erstellen Sie die App mit einem anderen Thema. Push-Benachrichtigungen, die an dieses Thema gesendet werden, werden nur von der mit diesem Thema erstellten App empfangen.

1. **Plattformanwendungen erstellen**

   1. Klicken Sie auf Anwendungen und dann auf Plattformanwendung erstellen. Wählen Sie einen Namen und eine Plattform (APNS für iOS, GCM für Android). Je nach Plattform müssen andere Felder ausgefüllt werden:

      1. Bei APNS müssen eine P12-Datei, ein Kennwort, ein Zertifikat und ein privater Schlüssel eingegeben werden. Diese sollten im Schritt *Verwenden des Apple Push Notification Service (APNS)* oben abgerufen werden.
      1. Für GCM muss ein API-Schlüssel eingegeben werden. Dies sollte im obigen Schritt *Verwenden des Google Cloud Messaging-Dienstes (GCM)* erreicht werden.
   1. Wiederholen Sie den obigen Schritt einmal für jede Plattform, die Sie unterstützen möchten. Damit sowohl iOS als auch Android per Push gesendet werden können, müssen zwei Plattformanwendungen erstellt werden.


1. **Identitätspool erstellen**

   1. Verwenden Sie [Cognito](https://console.aws.amazon.com/cognito), um einen Identitäts-Pool zu erstellen, in dem grundlegende Daten von nicht authentifizierten Benutzern gespeichert werden. Amazon Cognito unterstützt derzeit nur die Regionen &quot;us-east&quot;und &quot;eu&quot;.
   1. Geben Sie einen Namen ein und aktivieren Sie das Kontrollkästchen &quot;Zugriff auf nicht authentifizierte Identitäten aktivieren&quot;.
   1. Klicken Sie auf der nächsten Seite (&quot;*Ihre Kognito-Identitäten erfordern Zugriff auf Ihre Ressourcen*&quot;) auf Zulassen.
   1. Klicken Sie oben rechts auf der Seite auf den Link &quot;*Identitätspool bearbeiten&quot;*. Die Identitäts-Pool-ID wird angezeigt. Speichern Sie diesen Text für später.
   1. Wählen Sie auf derselben Seite die Dropdown-Liste neben &quot;Nicht authentifizierte Rolle&quot;und stellen Sie sicher, dass die Rolle &quot;Kognito_&lt;Poolname>UnauthRole&quot;ausgewählt ist. Speichern Sie Ihre Änderungen.

1. **Zugriff konfigurieren**

   1. Melden Sie sich bei [Identitäts- und Zugriffsverwaltung](https://console.aws.amazon.com/iam/home) (IAM) an.
   1. Rollen auswählen
   1. Klicken Sie auf die Rolle, die im vorherigen Schritt erstellt wurde, mit dem Namen Cognito_&lt;yourIdentityPoolName>Unauth_Role. Zeichnen Sie die angezeigte Rolle ARN auf.
   1. Öffnen Sie &quot;Inline-Richtlinien&quot;, wenn sie noch nicht geöffnet sind. Sie sollten dort eine Richtlinie mit einem Namen wie oneClick_Cognito_&lt;yourIdentityPoolName>Unauth_Role_1234567890123 sehen.
   1. Klicken Sie auf &quot;Richtlinie bearbeiten&quot;. Ersetzen Sie den Inhalt des Policy-Dokuments durch dieses JSON-Snippet:

   <table>
    <tbody>
     <tr>
     <td><p> </p> <p>{</p> <p> "Version": "2012-10-17",</p> <p> "Aussage": [</p> <p> {</p> <p> "Aktion": [</p> <p> "mobileanalytics:PutEvents",</p> <p> "cognito-sync:*",</p> <p> "SNS:CreatePlatformEndpoint",</p> <p> "SNS:Subscribe"</p> <p> ],</p> <p> "Effekt": "Allow",</p> <p> "Resource": [</p> <p> "*"</p> <p> ]</p> <p> }</p> <p> ]</p> <p>}</p> <p> </p> </td>
     </tr>
    </tbody>
    </table>

   1. Klicken Sie auf **Richtlinie anwenden**


#### Verwenden des Pushwoosh-Nachrichtendienstes {#using-the-pushwoosh-messaging-service}

Wenn Sie Pushwoosh nicht verwenden möchten, können Sie diesen Schritt überspringen.

So verwenden Sie Pushwoosh:

1. **Registrieren mit Pushwoosh**

   1. Gehen Sie zu pushwoosh.com und erstellen Sie ein neues Konto.

1. **API-Zugriffstoken erstellen**

   1. Rufen Sie auf der Pushwoosh-Site das Menüelement &quot;API-Zugriff&quot;auf, um ein API-Zugriffstoken zu generieren. Sie müssen das sicher aufzeichnen.

1. **Neue App erstellen**

   1. Zur Unterstützung von Android müssen Sie Ihren GCM-API-Schlüssel angeben.
   1. Wählen Sie beim Konfigurieren der App Cordova als Framework.
   1. Zur iOS-Unterstützung müssen Sie die Zertifikatdatei (.cer), das Push-Zertifikat (.p12) und das Kennwort für den privaten Schlüssel angeben. Diese hätten von der APNS-Site von Apple bezogen werden müssen. Wählen Sie als Framework Cordova.
   1. Pushwoosh generiert eine App-ID für diese App im Format &quot;XXXXX-XXXXX&quot;, wobei jedes X ein Hexadezimalwert (0 bis F) ist.

>[!NOTE]
>
>*Wenn eine zweite App in AEM mit derselben App-ID (und anderen zugehörigen Werten) konfiguriert ist: API-Zugriffstoken und GCM-ID) werden Push-Benachrichtigungen, die über die zweite App am AEM gesendet werden, an jede andere App mit dieser App-ID gesendet.*

### Schritt 3: hinzufügen Push-Unterstützung für die App {#step-add-push-support-to-the-app}

#### hinzufügen ContentSync-Konfiguration {#add-contentsync-configuration}

Erstellen Sie zwei Inhaltsknoten (einen in app-config und einen in app-config-dev) mit dem Namen notificationsConfig:

* /content/`<your app>`/shell/jcr:content/pge-app/app-config-dev/notificationsConfig
* /content/`<your app>`/shell/jcr:content/pge-app/app-config/notificationsConfig

Mit diesen Eigenschaften (.content.xml-Dateien):
&lt;jcr:root xmlns:jcr=&quot; [https://www.jcp.org/jcr/1.0](https://www.jcp.org/jcr/1.0)&quot; xmlns:nt=&quot; [https://www.jcp.org/jcr/nt/1.0](https://www.jcp.org/jcr/nt/1.0)&quot;
jcr:primaryType=&quot;nt:unstructured&quot;
excludeProperties=&quot;[appAPIAccessToken]&quot;
path=&quot;../../../...&quot;
targetRootDirectory=&quot;www&quot;
type=&quot;notificationsconfig&quot;/>

>[!NOTE]
>
>Der Content Sync-Handler sucht nach diesen Knoten. Wenn sie nicht vorhanden sind, schreibt er die Datei &quot;pge-notifications-config.json&quot;nicht.

#### hinzufügen Client-Bibliotheken {#add-client-libraries}

Die Clientbibliotheken für Push-Benachrichtigungen müssen der App wie folgt hinzugefügt werden:

In CRXDE Lite:

1. Navigieren Sie zu */etc/designs/phonegap//clientlibsall.*
1. Klicken Sie in der Dublette auf den Einbettungsabschnitt im Eigenschaftenbereich.
1. Fügen Sie im angezeigten Dialogfeld eine neue Client-Bibliothek hinzu, indem Sie auf die Schaltfläche + klicken.
1. Fügen Sie im neuen Textfeld &quot;cq.mobile.push&quot;hinzu und klicken Sie auf &quot;OK&quot;.
1. hinzufügen eine weitere namens cq.mobile.push.amazon und klicken Sie auf OK.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Wenn Push-Benachrichtigungen aus Platzgründen in der App entfernt oder nicht verwendet werden und um Meldungen mit Konsolenfehlern zu vermeiden, entfernen Sie diese clientlibs aus der App.

### Schritt 4: Vorbereitung eines Telefons für Tests {#step-prepare-a-phone-for-testing}

>[!NOTE]
>
>*Für Push-Benachrichtigungen müssen Sie auf einem tatsächlichen Gerät testen, da Emulatoren keine Push-Benachrichtigungen empfangen können.*

#### IOS {#ios}

Für iOS müssen Sie einen Mac OS-Computer verwenden und dem [iOS Developer-Programm](https://developer.apple.com/programs/ios/) beitreten. Einige Unternehmen verfügen über Unternehmenslizenzen, die möglicherweise allen Entwicklern zur Verfügung stehen.

Mit XCode 8.1 müssen Sie vor der Verwendung von Push-Benachrichtigungen auf die Registerkarte &quot;Funktionen&quot;Ihres Projekts wechseln und den Umschalter &quot;Push-Benachrichtigungen&quot;aktivieren.

#### Android {#android}

So installieren Sie die App über die CLI auf einem Android-Smartphone (siehe unten) **Schritt 6 - Erstellen und Bereitstellen der App**), müssen Sie zunächst das Telefon in den &quot;Entwicklermodus&quot;setzen. Weitere Informationen dazu finden Sie unter [Aktivieren der Entwickleroptionen auf dem Gerät](https://developer.android.com/tools/device.html#developer-device-options).

### Schritt 5: Push-Vorgänge für AEM-Apps {#step-configure-push-on-aem-apps} konfigurieren

Vor dem Erstellen und Bereitstellen auf Ihrem konfigurierten Mobilgerät müssen Sie die Benachrichtigungseinstellungen für den Nachrichtendienst konfigurieren, den Sie verwendet haben.

1. Erstellen Sie die entsprechenden Autorisierungsgruppen für Push-Benachrichtigungen.
1. Melden Sie sich bei AEM als passender Benutzer an und klicken Sie auf die Registerkarte &quot;Apps&quot;.
1. Klicken Sie auf die App.
1. Suchen Sie die Kachel Cloud Services verwalten und klicken Sie auf den Stift, um Ihre Cloud-Konfigurationen zu ändern.
1. Wählen Sie als Benachrichtigungskonfiguration &quot;Amazon SNS-Verbindung&quot;, &quot;Pushwoosh-Verbindung&quot;oder &quot;Adobe Mobile Services&quot;aus.
1. Geben Sie die Provider-Eigenschaften ein und klicken Sie auf &quot;Senden&quot;, um sie zu speichern, und auf &quot;Fertig&quot;. Sie werden derzeit nicht remote überprüft, außer im Falle von AMS.
1. Sie sollten nun die Konfiguration sehen, die Sie gerade in der Kachel Cloud Services verwalten eingegeben haben.

### Schritt 6: Erstellen und Bereitstellen der App {#step-build-and-deploy-the-app}

**Hinweis:** Lesen Sie auch unsere Anweisungen  [](/help/mobile/building-app-mobile-phonegap.md) hier zum Erstellen von PhoneGap-Anwendungen.

Es gibt zwei Möglichkeiten, Ihre App mit PhoneGap zu erstellen und bereitzustellen.

**Hinweis:** Für Tests von Push-Benachrichtigungen reichen Emulatoren nicht aus, da Push-Benachrichtigungen ein anderes Protokoll zwischen dem Push-Provider (Apple oder Google) und dem Gerät verwenden. Die aktuelle Mac-/PC-Hardware und Emulatoren unterstützen dies nicht.

1. *PhoneGap* Builder ist ein von PhoneGap angebotener Dienst, mit dem Sie Ihre App auf den Servern erstellen und direkt auf Ihr Gerät herunterladen können. Informationen zum Einrichten und Verwenden von PhoneGap Build finden Sie in der [PhoneGap Build-Dokumentation](https://build.phonegap.com/).

1. *Mit der PhoneGap-Befehlszeilenschnittstelle*  (CLI) können Sie einen umfangreichen Satz an PhoneGap-Befehlen in der Befehlszeile verwenden, um Ihre App zu erstellen, zu debuggen und bereitzustellen. Informationen zum Einrichten und Verwenden der PhoneGap-CLI finden Sie in der [PhoneGap-Entwicklerdokumentation](https://docs.phonegap.com/en/edge/guide_cli_index.md.html#The%20Command-Line%20Interface).

### Schritt 7: Push-Benachrichtigung senden {#step-send-a-push-notification}

Gehen Sie wie folgt vor, um eine neue Benachrichtigung zu erstellen und zu senden.

1. Neue Benachrichtigung erstellen

   * Suchen Sie im Dashboard Ihrer AEM Mobile-App die Kachel &quot;Push-Benachrichtigungen&quot;.
   * Wählen Sie im Menü rechts oben &quot;Erstellen&quot;. Beachten Sie, dass diese Schaltfläche erst verfügbar ist, wenn die Cloud-Konfiguration zum ersten Mal festgelegt wurde.
   * Geben Sie im Assistenten zum Erstellen von Benachrichtigungen einen Titel und eine Nachricht ein und klicken Sie dann auf die Schaltfläche &quot;Erstellen&quot;. Ihre Benachrichtigung kann jetzt sofort oder später gesendet werden. Es kann bearbeitet und die Nachricht und/oder der Titel geändert und gespeichert werden.

1. Benachrichtigung senden

   * Suchen Sie im Dashboard &quot;Apps&quot;die Kachel &quot;Push-Benachrichtigungen&quot;.
   * Wählen Sie die Benachrichtigung aus oder klicken Sie auf die Detailschaltfläche unten rechts (. . .), um die Liste der Benachrichtigungen anzuzeigen. Diese Liste zeigt auch an, ob eine Benachrichtigung gesendet werden kann, bereits gesendet wurde oder ob beim Senden ein Fehler aufgetreten ist.
   * Aktivieren Sie das Kontrollkästchen für eine Benachrichtigung (nur) und klicken Sie auf die Schaltfläche &quot;Benachrichtigung senden&quot;oberhalb der Liste. Sie haben die Möglichkeit, die Benachrichtigung im angezeigten Dialogfeld &quot;Abbrechen&quot;oder &quot;Senden&quot;zu senden.

1. Umgang mit den Ergebnissen

   * Wenn der Push-Benachrichtigungsdienst (Amazon SNS oder Pushwoosh) die Senden-Anforderung empfängt, sie als gültig bestätigt und erfolgreich an die nativen Anbieter (APNS und GCM) sendet, wird das Dialogfeld &quot;Senden&quot;ohne Meldung geschlossen. In der Liste &quot;Benachrichtigung&quot;wird der Status dieser Benachrichtigung als &quot;Gesendet&quot;aufgeführt.
   * Wenn der Push-Senden fehlschlägt, wird im Dialogfeld eine Meldung angezeigt, die das Problem angibt. In der Benachrichtigungs-Liste wird der Status dieser Benachrichtigung als &quot;Fehler&quot;aufgelistet, aber wenn das Problem behoben wird, kann die Benachrichtigung erneut gesendet werden. Im Ereignis eines Fehlers sollten zusätzliche Fehlerinformationen im Serverfehlerprotokoll angezeigt werden.
   * Beachten Sie, dass es zwischen iOS- und Android-Push-Benachrichtigungen einige Plattformunterschiede gibt. Dazu gehören:

      * Beim Erstellen mit CLI wird die App nach der Bereitstellung auf Android Beginn. Unter iOS müssen Sie den Beginn manuell ausführen. Da der Schritt zur Push-Registrierung beim Start ausgeführt wird, können Android-Apps Push-Benachrichtigungen sofort empfangen (da sie gestartet und registriert wurden), iOS-Apps dagegen nicht.
      * Unter Android befindet sich der Text für die Schaltfläche &quot;OK&quot;in Großbuchstaben (und in anderen Schaltflächen, die in der In-App-Benachrichtigung hinzugefügt werden), unter iOS jedoch nicht.

Bei AMS-Push-Benachrichtigungen müssen Benachrichtigungen zusammengestellt und vom AMS-Server gesendet werden. AMS bietet zusätzliche Push-Benachrichtigungsfunktionen, die über die von AEM mit AWS und Pushwoosh bereitgestellten Funktionen hinausgehen.

>[!NOTE]
>
>*Push-Benachrichtigungen werden nicht als Versand garantiert. sie sind eher wie Mitteilungen. Es wird alles getan, um sicherzustellen, dass jeder es hört, aber es handelt sich nicht um einen garantierten Versand-Mechanismus. Außerdem kann die Bereitstellungszeit für einen Push von weniger als einer Sekunde bis zu einer halben Stunde variieren.*

### Deep-Linking mit Push-Benachrichtigungen konfigurieren {#configuring-deep-linking-with-push-notifications}

Was ist Deep Linking? Im Kontext einer Push-Benachrichtigung ist es eine Möglichkeit, das Öffnen oder Weiterleiten einer App an eine angegebene Position innerhalb der App zuzulassen (sofern diese geöffnet ist).

Wie funktioniert das? Der Autor einer Push-Benachrichtigung fügt optional eine Schaltflächenbeschriftung hinzu (d.h. &quot;Zeig mir!&quot;) zur Benachrichtigung hinzugefügt und wählt die Seite, die in der Benachrichtigung verknüpft werden soll, über einen visuellen Pfadbrowser. Wenn der Push gesendet wird, erfolgt der Push normal, außer dass die In-App-Nachricht die Schaltfläche OK durch die Schaltfläche &quot;Schließen&quot;ersetzt und die neue Schaltfläche angegeben wird (&quot;Anzeigen!&quot;). angezeigt. Durch Klicken auf die neue Schaltfläche wird die App zur angegebenen Seite in der App. Wenn Sie auf &quot;Schließen&quot;klicken, wird die Nachricht einfach geschlossen.

Wenn die App nicht geöffnet ist, wird die Schattierung als normal angezeigt. Wenn Sie die Benachrichtigung im Schatten bearbeiten, wird die App geöffnet und dem Benutzer dann die Deep-Link-Schaltflächen entsprechend der Konfiguration in der Push-Benachrichtigung angezeigt.

Erstellen Sie die Benachrichtigung, fügen Sie einen Schaltflächentext und einen Link-Pfad für den optionalen Deep Link hinzu:

>[!CAUTION]
>
>.Gehen Sie wie unten beschrieben vor, um auf die Push-Benachrichtigungskachel in Ihrem Dashboard zuzugreifen.

1. Klicken Sie auf die Bearbeitung oben rechts in der Kachel **Cloud Services verwalten**.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Wählen Sie **Pushwoosh Connection**. Klicken Sie auf **Weiter**.

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. Geben Sie die Details der Eigenschaften ein und klicken Sie auf **Senden**.

   ![chlimage_1-110](assets/chlimage_1-110.png)

   Wenn Sie die Konfiguration senden, wird im Dashboard die Kachel **Push Notifications** angezeigt.

   ![chlimage_1-111](assets/chlimage_1-111.png)

### Assistent zum Erstellen von Benachrichtigungen {#create-notification-wizard}

Sobald die Kachel **Push-Benachrichtigungen** in Ihrem Dashboard angezeigt wird, verwenden Sie den Assistenten zum Erstellen von Benachrichtigungen, um den Inhalt hinzuzufügen:

1. Klicken Sie auf das Symbol zum Hinzufügen oben rechts in der Kachel **Push Notifications**, um den **Assistenten zum Erstellen von Benachrichtigungen** zu öffnen.

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. Durch Klicken auf das Durchsuchen-Symbol im Link-Pfad wird dem Benutzer die Inhaltsstruktur der App angezeigt.

   Klicken Sie nach Auswahl des Pfads auf das Häkchen.

   ![chlimage_1-113](assets/chlimage_1-113.png)

   >[!NOTE]
   >
   >Der Text der Schaltfläche &quot;Verknüpfen&quot;ist auf 20 Zeichen begrenzt.
   >
   >Wenn der Endbenutzer nicht über die neueste Version der Anwendung verfügt und der verknüpfte Pfad nicht verfügbar ist, führt die Bestätigung der Aktion des Deep Links dazu, dass der Benutzer zur Hauptseite der App gelangt.

1. Geben Sie die **Textdetails** in den **Assistenten zum Erstellen von Benachrichtigungen** ein und klicken Sie auf **Erstellen**.

   ![chlimage_1-114](assets/chlimage_1-114.png)

   Öffnen Sie die Details, indem Sie auf die Push-Benachrichtigung klicken, die Sie aus der Kachel **Push-Benachrichtigungen** erstellt haben.

   Sie können Eigenschaften bearbeiten, Benachrichtigungen senden oder die Benachrichtigung löschen.

   ![chlimage_1-115](assets/chlimage_1-115.png)

>[!NOTE]
>
>**Zusätzliche Informationen**:
>
>Pushwoosh und Amazon SNS werden nach Version 6.4 nicht mehr unterstützt und sind als Add-On von Package Share verfügbar.

### Die nächsten Schritte {#the-next-steps}

Sobald Sie die Details zu Push-Benachrichtigungen für Ihre App kennen, finden Sie unter [AEM Mobile Content Personalization](/help/mobile/phonegap-aem-mobile-content-personalization.md).

