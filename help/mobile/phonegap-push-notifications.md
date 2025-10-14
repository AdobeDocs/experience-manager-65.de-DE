---
title: Push-Benachrichtigungen
description: Auf dieser Seite erfahren Sie, wie Sie Push-Benachrichtigungen in einer Adobe Experience Manager Mobile-App verwenden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 375f2f40-1b98-4e21-adee-cbea274e6a2a
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '3135'
ht-degree: 1%

---

# Push-Benachrichtigungen{#push-notifications}

{{ue-over-mobile}}

Für den Wert einer Mobile App und ihrer Marketing-Kampagnen ist es entscheidend, dass Sie Ihre Benutzenden von Adobe Experience Manager (AEM) Mobile Apps sofort mit wichtigen Benachrichtigungen benachrichtigen können. Hier werden die Schritte beschrieben, die unternommen werden müssen, damit Ihre Mobile App Push-Benachrichtigungen erhält. Außerdem erfahren Sie, wie Sie Push-Benachrichtigungen von AEM Mobile an die auf dem Smartphone installierte Mobile App konfigurieren und senden. In diesem Abschnitt wird außerdem beschrieben, wie Sie die Funktion [Deep Linking](#deeplinking) für Ihre Push-Benachrichtigungen konfigurieren.

>[!NOTE]
>
>*Push-Benachrichtigungen sind keine garantierte Zustellung, sondern ähneln Ankündigungen. Es wird alles getan, um sicherzustellen, dass jeder sie erhält, aber sie sind kein garantierter Liefermechanismus. Außerdem kann die Zeit zum Bereitstellen einer Push-Benachrichtigung von weniger als einer Sekunde bis zu einer halben Stunde variieren.*

Für die Verwendung von Push-Benachrichtigungen mit AEM sind einige verschiedene Technologien erforderlich. Zunächst muss ein Push-Benachrichtigungs-Service-Anbieter verwendet werden, um Benachrichtigungen und Geräte zu verwalten (AEM tut dies noch nicht). Zwei Anbieter sind standardmäßig mit AEM konfiguriert: [Amazon Simple Notification Service](https://aws.amazon.com/sns/) (oder SNS) und [Pushwoosh](https://www.pushwoosh.com/). Zweitens muss die Push-Technologie für das angegebene mobile Betriebssystem über den entsprechenden Service laufen - den Push Notification Service (oder APNS) von Apple für iOS-Geräte und Google Cloud Messaging (oder GCM) für Android™-Geräte. Obwohl AEM nicht direkt mit diesen plattformspezifischen Services kommuniziert, müssen einige zugehörige Konfigurationsinformationen von AEM zusammen mit den Benachrichtigungen bereitgestellt werden, damit diese Services die Push-Benachrichtigung ausführen können.

Nach der Installation und Konfiguration (wie unten beschrieben) funktioniert es wie folgt:

1. Eine Push-Benachrichtigung wird in AEM erstellt und an den Dienstleister (Amazon SNS oder Pushwoosh) gesendet.
1. Der Dienstleister empfängt sie und sendet sie an den Hauptanbieter (APNS oder GCM).
1. Der Hauptanbieter sendet die Benachrichtigung an alle Geräte, die für diese Push-Benachrichtigung registriert sind. Für jedes Gerät wird das Mobilfunknetz oder WLAN verwendet, je nachdem, was auf dem Gerät verfügbar ist.
1. Die Benachrichtigung wird auf dem Gerät angezeigt, wenn die App, für die sie registriert ist, nicht ausgeführt wird. Ein Benutzer, der auf die Benachrichtigung tippt, startet die App und zeigt die Benachrichtigung innerhalb der App an. Falls die Anwendung bereits ausgeführt wird, wird nur die In-App-Benachrichtigung angezeigt.

Diese Version von AEM unterstützt iOS und Android™-Mobilgeräte.

## Überblick und Verfahren {#overview-and-procedure}

Um Push-Benachrichtigungen in einer AEM Mobile-App zu verwenden, müssen die folgenden allgemeinen Schritte ausgeführt werden.

Normalerweise führt ein Experience Manager-Entwickler Folgendes aus:

1. Registrieren bei Apple und Google Messaging Services
1. Registrieren bei einem Push-Messaging-Service und Konfigurieren
1. Hinzufügen von Push-Unterstützung zur App
1. Vorbereiten eines Telefons für Tests

Ein Experience Manager-Administrator führt folgende Schritte aus:

1. Konfigurieren von Push-Benachrichtigungen in AEM-Apps
1. Erstellen und Bereitstellen der App
1. Push-Benachrichtigung senden
1. Deep-Linking-*konfigurieren (optional)*

### Schritt 1: Registrieren bei Apple und Google Messaging Services {#step-register-with-apple-and-google-messaging-services}

#### Verwenden des Apple Push Notification Service (APNS) {#using-the-apple-push-notification-service-apns}

Navigieren Sie zur Apple-Seite [hier](https://developer.apple.com/documentation/usernotifications#//apple_ref/doc/uid/TP40008194-CH8-SW1), um sich mit dem Apple Push Notification Service vertraut zu machen.

Um APNs zu verwenden, benötigen Sie eine **Certificate**-Datei (eine .cer-Datei), einen **Private Key** (eine .p12-Datei) und ein **Private Key Password** von Apple. Eine Anleitung dazu finden Sie [hier](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

#### Verwenden des Google Cloud Messaging-Services (GCM) {#using-the-google-cloud-messaging-gcm-service}

>[!NOTE]
>
>Google ersetzt GCM durch einen ähnlichen Dienst namens Firebase Cloud Messaging (FCM). Weitere Informationen zu FCM finden Sie [hier](https://firebase.google.com/docs/cloud-messaging/).

Navigieren Sie zur Google-Seite [hier](https://developer.android.com/google/gcm/index.html), um sich mit Google Cloud Messaging für Android vertraut zu machen™.

[Führen Sie die folgenden &#x200B;](https://developer.android.com/google/gcm/gs.html) aus **um ein Google-API-** zu erstellen, **den GCM-** zu aktivieren und **einen API-Schlüssel abzurufen**. Sie benötigen den **API-Schlüssel** um Push-Benachrichtigungen an Android™-Geräte zu senden. Notieren Sie sich auch Ihre **Projektnummer** die manchmal auch als „GCM-**&quot; bezeichnet**.

Die folgenden Schritte zeigen eine andere Methode zum Erstellen von GCM-API-Schlüsseln:

1. Melden Sie sich bei Google an und gehen Sie zur Entwicklerseite von [Google](https://developers.google.com/mobile/add?platform=android&cntapi=gcm).
1. Wählen Sie Ihre App aus der Liste aus (oder erstellen Sie eine).
1. Geben Sie unter Android™ Package Name Ihre App-ID ein, d. h. `com.adobe.cq.mobile.weretail.outdoorsapp`. (Wenn dies nicht funktioniert, versuchen Sie es erneut mit „test.test“.)
1. Klicken Sie **Weiter , um Dienste auszuwählen und zu konfigurieren**
1. Wählen Sie Cloud Messaging aus und klicken Sie dann auf **Google Cloud Messaging aktivieren**.
1. Der neue Server-API-Schlüssel und die (neue oder vorhandene) Absender-ID werden dann angezeigt.

>[!NOTE]
>
>Aufzeichnen des Server-API-Schlüssels. Dieser Wert wird auf der Site Ihres Push-Anbieters eingegeben.

### Schritt 2: Registrieren und Konfigurieren eines Push-Messaging-Service {#step-register-and-configure-a-push-messaging-service}

AEM ist so konfiguriert, dass einer von drei Services für Push-Benachrichtigungen verwendet wird:

* Amazon SNS
* Pushwoosh
* Adobe Mobile Services

Mit den Konfigurationen *Amazon SNS* und *Pushwoosh* können Sie Push-Benachrichtigungen von innerhalb von AEM-Bildschirmen senden.

Mit der Konfiguration von *Adobe Mobile Services* können Sie Push-Benachrichtigungen von innerhalb von Adobe Mobile Services aus über ein Adobe Analytics-Konto konfigurieren und senden (die App muss jedoch mit dieser Konfiguration erstellt werden, um AMS-Push-Benachrichtigungen zu aktivieren).

#### Verwenden des Amazon SNS-Messaging-Services {#using-the-amazon-sns-messaging-service}

>[!NOTE]
>
>*Informationen zu Amazon SNS und einen Link zum Erstellen eines AWS-Kontos finden Sie [hier](https://aws.amazon.com/sns/). Sie können ein kostenloses Konto für ein Jahr erhalten.*

Wenn Sie Amazon SNS nicht verwenden möchten, können Sie diese Schritte überspringen.

Führen Sie die folgenden Schritte aus, um Amazon SNS für Push-Benachrichtigungen einzurichten:

1. **Registrieren bei Amazon SNS**

   1. Zeichnen Sie Ihre Konto-ID auf. Das Format sollte 12 Ziffern ohne Leerzeichen oder Bindestriche sein, d. h. „123456789012“.
   1. Stellen Sie sicher, dass Sie sich in der Region „us-east“ oder „eu“ befinden, da ein späterer Schritt (Erstellung des Identitätspools) einen dieser Schritte erfordert.
   1. Melden Sie sich nach der Registrierung bei der Verwaltungskonsole an und wählen Sie [SNS](https://console.aws.amazon.com/sns/) (Push Notification Service) aus. Klicken Sie auf „Erste Schritte“, wenn es angezeigt wird.

1. **Zugriffsschlüssel und ID erstellen**

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie im Menü Sicherheitsberechtigungen aus.
   1. Klicken Sie auf Zugriffsschlüssel und anschließend im Bereich unten auf **Neuen Zugriffsschlüssel erstellen**.
   1. Klicken Sie **Zugriffsschlüssel anzeigen** und kopieren und speichern Sie die angezeigte Zugriffsschlüssel-ID und den geheimen Zugriffsschlüssel. Wenn Sie die Option zum Herunterladen der Schlüssel auswählen, erhalten Sie eine CSV-Datei, die dieselben Werte enthält.
   1. Andere sicherheitsbezogene Zertifikate und andere Zertifikate können auf dieser Seite verwaltet werden.

   >[!NOTE]
   >
   >Ein Zugriffsschlüssel kann für mehrere Apps verwendet werden.

   Für Organisationen, die ein &quot;AWS Sandbox“-Konto verwenden, sind die Schritte ähnlich und hier beschrieben:

   1. Klicken Sie oben rechts im Bildschirm auf Ihren Anmeldenamen und wählen Sie im Menü Meine Sicherheitsberechtigungen aus.
   1. Klicken Sie in der linken Aktionsliste auf Benutzer und wählen Sie Ihren Benutzernamen aus.
   1. Klicken Sie auf die Registerkarte Sicherheitsanmeldeinformationen .
   1. Von hier aus sehen Sie Ihre Schlüssel und erstellen neue Schlüssel. Speichern Sie die Schlüssel zur späteren Verwendung.

1. **Thema erstellen**

   1. Klicken Sie **Thema erstellen** und wählen Sie einen Themennamen aus. Zeichnen Sie alle Felder wie Themen-ARN, Themeneigentümer, Region, Anzeigename auf.
   1. Klicken Sie **Andere Themenaktionen** > **Themenrichtlinie bearbeiten**. Wählen **unter „Diesen Benutzern erlauben, dieses Thema zu abonnieren** die Option **Alle.**
   1. Klicken Sie **Richtlinie aktualisieren**.

   >[!NOTE]
   >
   >Sie können mehrere Themen für verschiedene Szenarien wie Entwicklung, Test und Demo erstellen. Der Rest der SNS-Konfiguration kann unverändert bleiben. Erstellen Sie die App mit dem anderen Thema. Push-Benachrichtigungen, die an dieses Thema gesendet werden, werden nur von der App empfangen, die mit diesem Thema erstellt wurde.

1. **Erstellen von Platform-Programmen**

   1. Klicken Sie auf Programme und dann auf Platform-Anwendung erstellen . Wählen Sie einen Namen und eine Plattform aus (APNS für iOS, GCM für Android™). Je nach Plattform. Andere Felder müssen ausgefüllt werden:

      1. Bei APNS müssen eine P12-Datei, ein Kennwort, ein Zertifikat und ein privater Schlüssel eingegeben werden. Diese sollten im Schritt „Verwenden *Apple Push Notification Service (APNS)“* werden.
      1. Für GCM muss ein API-Schlüssel eingegeben werden. Dies sollte im obigen Schritt (Verwenden *Google Cloud Messaging (GCM)-Service)* werden.

   1. Wiederholen Sie die obigen Schritte einmal für jede Plattform, die Sie unterstützen. Um sowohl auf iOS als auch auf Android™ pushen zu können, müssen zwei Platform-Anwendungen erstellt werden.

1. **Erstellen eines Identitätspools**

   1. Mit [Cognito](https://console.aws.amazon.com/cognito) können Sie einen Identitätspool erstellen, in dem die grundlegenden Daten nicht authentifizierter Benutzer gespeichert werden. Beachten Sie, dass derzeit nur die Regionen „us-east“ und „eu“ von Amazon Cognito unterstützt werden.
   1. Geben Sie ihm einen Namen und aktivieren Sie das Kontrollkästchen für „Zugriff auf nicht authentifizierte Identitäten aktivieren“.
   1. Klicken Sie auf der nächsten Seite (“*Ihre Cognito-Identitäten erfordern Zugriff auf Ihre Ressourcen*) auf „Zulassen“.
   1. Klicken Sie oben rechts auf der Seite auf den Link &quot;*Identitätspool bearbeiten“*. Die Identitätspool-ID wird angezeigt. Speichern Sie diesen Text für später.
   1. Wählen Sie auf derselben Seite das Dropdown-Menü neben „Nicht authentifizierte Rolle“ und stellen Sie sicher, dass die Rolle „Cognito_Pool_Name>UnauthRole“ ausgewählt ist. Speichern Sie Ihre Änderungen.

1. **Zugriff konfigurieren**

   1. Melden Sie sich bei [Identity and Access Management](https://console.aws.amazon.com/iam/home) (IAM) an.
   1. Rollen auswählen.
   1. Klicken Sie auf die im vorherigen Schritt erstellte Rolle namens „Cognito_&lt;yourIdentityPoolName>Unauth_Role“. Zeichnen Sie die angezeigte „Funktions-ARN“ auf.
   1. Öffnen Sie „Inline-Richtlinien“, wenn sie nicht bereits geöffnet ist. Dort sollte eine Richtlinie mit einem Namen wie oneClick_Cognito_&lt;yourIdentityPoolName>Unauth_Role_1234567890123 angezeigt werden.
   1. Klicken Sie auf „Richtlinie bearbeiten“. Ersetzen Sie den Inhalt des Richtliniendokuments durch diesen JSON-Ausschnitt:

   <table>
    <tbody>
     <tr>
     <td><p> </p> <p>{</p> <p> „Version“: „2012-10-17“,</p> <p> „Anweisung“: [</p> <p> {</p> <p> „Aktion“: [</p> <p> „mobileAnalytics:PutEvents“,</p> <p> „cognito-sync:*",</p> <p> „SNS:CreatePlatformEndpoint“,</p> <p> „SNS:Subscribe“</p> <p> ],</p> <p> „Effect“: „Allow“,</p> <p> „Ressource“: [</p> <p> "*"</p> <p> ]</p> <p> }</p> <p> ]</p> <p>}</p> <p> </p> </td>
     </tr>
    </tbody>
    </table>

   1. Klicken Sie **Richtlinie anwenden**.

#### Verwenden des Pushwoosh-Messaging-Service {#using-the-pushwoosh-messaging-service}

Wenn Sie Pushwoosh nicht verwenden möchten, können Sie diesen Schritt überspringen.

So verwenden Sie Pushwoosh:

1. **Registrieren Sie sich bei Pushwoosh**

   1. Gehen Sie zu pushwoosh.com und erstellen Sie ein Konto.

1. **Erstellen eines API-Zugriffstoken**

   1. Wechseln Sie auf der Pushwoosh-Site zum Menüelement API-Zugriff , um ein API-Zugriffs-Token zu generieren. Notieren Sie dieses Token sicher.

1. **Erstellen einer App**

   1. Für die Android™-Unterstützung müssen Sie Ihren GCM-API-Schlüssel angeben.
   1. Wählen Sie beim Konfigurieren der App Cordova als Framework.
   1. Für die iOS-Unterstützung müssen Sie die Zertifikatdatei (.cer), das Push-Zertifikat (.p12) und das Kennwort für den privaten Schlüssel angeben. Diese müssen von der APNS-Site von Apple abgerufen worden sein. Wählen Sie für Framework die Option Cordova.
   1. Pushwoosh generiert eine App-ID für diese App in der Form „XXXXX-XXXXX“, wobei jedes X ein Hexadezimalwert (0 bis F) ist.

>[!NOTE]
>
>*Wenn eine zweite App in AEM mit derselben App-ID (und anderen zugehörigen Werten: API-Zugriffstoken und GCM-ID) konfiguriert ist, werden alle Push-Benachrichtigungen, die über die zweite App in AEM gesendet werden, an jede andere App mit dieser App-ID gesendet.*

### Schritt 3: Hinzufügen von Push-Unterstützung zur App {#step-add-push-support-to-the-app}

#### Konfiguration für Inhaltssynchronisierung hinzufügen {#add-contentsync-configuration}

Erstellen Sie zwei Inhaltsknoten (einen in app-config und einen in app-config-dev) mit dem Namen notificationsConfig:

* /content/`<your app>`/shell/jcr:content/pge-app/app-config-dev/notificationsConfig
* /content/`<your app>`/shell/jcr:content/pge-app/app-config/notificationsConfig

Mit diesen Eigenschaften (.content.xml-Dateien) :
&lt;jcr:root xmlns:jcr=&quot; [https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/index.html](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/index.html)&quot; xmlns:nt=&quot; [https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/index.html](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/index.html)&quot;
jcr:primaryType=„nt:unstructured“
excludeProperties=&quot;[appAPIAccessToken]&quot;
path=&quot;../../../…“
targetRootDirectory=„www“
type=„notificationsConfig“/>

>[!NOTE]
>
>Der Inhaltssynchronisierungs-Handler sucht nach diesen Knoten. Wenn sie nicht vorhanden sind, wird die Datei „page-notifications-config.json“ nicht ausgegeben.

#### Hinzufügen von Client-Bibliotheken {#add-client-libraries}

Die Client-Bibliotheken für Push-Benachrichtigungen müssen der App hinzugefügt werden, indem die folgenden Schritte ausgeführt werden:

In CRXDE Lite:

1. Navigieren Sie zu */etc/designs/phonegap/&lt;App-Name>/clientlibsall.*
1. Doppelklicken Sie im Eigenschaftenbereich auf den Abschnitt Einbetten .
1. Fügen Sie im angezeigten Dialogfeld eine Client-Bibliothek hinzu, indem Sie auf die Schaltfläche + klicken.
1. Fügen Sie im neuen Textfeld „cq.mobile.push“ hinzu und klicken Sie auf OK.
1. Fügen Sie eine weitere mit dem Namen cq.mobile.push.amazon hinzu und klicken Sie auf OK.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Wenn Push-Benachrichtigungen entfernt oder nicht verwendet werden, um Platz in der App zu sparen und Konsolenfehlermeldungen zu vermeiden, entfernen Sie diese Client-Bibliotheken aus der App.

### Schritt 4: Vorbereiten eines Telefons für Tests {#step-prepare-a-phone-for-testing}

>[!NOTE]
>
>*Bei Push-Benachrichtigungen müssen Sie den Test auf einem tatsächlichen Gerät durchführen, da Emulatoren keine Push-Benachrichtigungen empfangen können.*

#### IOS {#ios}

Verwenden Sie für iOS einen macOS-Computer und treten Sie dem [iOS-Entwicklerprogramm](https://developer.apple.com/programs/ios/) bei. Einige Unternehmen verfügen über Unternehmenslizenzen, die möglicherweise allen Entwicklern zur Verfügung stehen.

In XCode 8.1 müssen Sie vor der Verwendung von Push-Benachrichtigungen zur Registerkarte „Funktionen“ in Ihrem Projekt wechseln und den Umschalter Push-Benachrichtigungen aktivieren.

#### Android™ {#android}

Um die App über die CLI auf einem Android™-Smartphone zu installieren (siehe unten: **Schritt 6 - App erstellen und bereitstellen**), müssen Sie das Smartphone zunächst in den „Entwicklermodus“ versetzen. Weitere [&#x200B; dazu finden Sie unter „Aktivieren &#x200B;](https://developer.android.com/tools/device.html#developer-device-options) Entwickleroptionen auf dem Gerät .

### Schritt 5: Konfigurieren von Push-Benachrichtigungen in AEM-Apps {#step-configure-push-on-aem-apps}

Vor der Erstellung und Bereitstellung auf dem konfigurierten Mobilgerät müssen Sie die Benachrichtigungseinstellungen für den Messaging-Service konfigurieren, den Sie verwenden möchten.

1. Erstellen Sie die entsprechenden Autorisierungsgruppen für Push-Benachrichtigungen.
1. Melden Sie sich als entsprechender Benutzer bei AEM an und klicken Sie auf die Registerkarte Apps .
1. Klicken Sie auf die App.
1. Suchen Sie die Kachel Cloud Service verwalten und klicken Sie auf den Stift, um Ihre Cloud-Konfigurationen zu ändern.
1. Wählen Sie Amazon SNS Connection, Pushwoosh Connection oder Adobe Mobile Services als Benachrichtigungskonfiguration.
1. Geben Sie die Eigenschaften des Anbieters ein und klicken Sie auf Senden , um sie zu speichern, und auf Fertig . Sie werden derzeit nicht remote verifiziert, es sei denn, es gibt AMS.
1. Sie sollten jetzt die Konfiguration sehen, die Sie gerade auf der Kachel Cloud Service verwalten eingegeben haben.

### Schritt 6: App erstellen und bereitstellen {#step-build-and-deploy-the-app}

**Hinweis:** Weitere Informationen finden Sie [&#x200B; Anweisungen &#x200B;](/help/mobile/building-app-mobile-phonegap.md) Erstellen von PhoneGap-Anwendungen.

Es gibt zwei Möglichkeiten, Ihre App mit PhoneGap zu erstellen und bereitzustellen.

**Hinweis:** Beim Testen von Push-Benachrichtigungen reichen Emulatoren nicht aus, da Push-Benachrichtigungen ein eigenes Protokoll zwischen dem Push-Anbieter (Apple oder Google) und dem Gerät verwenden. Aktuelle Mac/PC-Hardware und Emulatoren unterstützen dies nicht.

1. *PhoneGap Build* ist ein Service von PhoneGap, mit dem Sie Ihre App auf ihren Servern erstellen und direkt auf Ihr Gerät herunterladen können. Siehe die PhoneGap Build-Dokumentation unter `https://build.phonegap.com/`, um zu erfahren, wie Sie PhoneGap Build einrichten und verwenden.

1. Mit *PhoneGap Command Line Interface* (CLI) können Sie einen umfangreichen Satz von PhoneGap-Befehlen in Ihrer Befehlszeile zum Erstellen, Debuggen und Bereitstellen Ihrer App verwenden. Informationen zum Einrichten und Verwenden der PhoneGap-CLI finden Sie in der PhoneGap-Entwicklerdokumentation (`https://docs.phonegap.com/en/edge/guide_cli_index.md.html#The%20Command-Line%20Interface`).

### Schritt 7: Push-Benachrichtigung senden {#step-send-a-push-notification}

Gehen Sie wie folgt vor, um eine Benachrichtigung zu erstellen und zu senden.

1. Erstellen einer Benachrichtigung

   * Suchen Sie im Dashboard Ihrer AEM Mobile-App die Kachel Push-Benachrichtigungen .
   * Wählen Sie im Menü oben rechts „Erstellen“ aus. Diese Schaltfläche ist erst verfügbar, wenn die Cloud-Konfiguration festgelegt wurde.
   * Geben Sie im Assistenten zum Erstellen von Benachrichtigungen einen Titel und eine Nachricht ein und klicken Sie dann auf die Schaltfläche „Erstellen“. Ihre Benachrichtigung kann jetzt sofort oder später gesendet werden. Sie können ihn bearbeiten und die Nachricht und/oder den Titel ändern und speichern.

1. Benachrichtigung senden

   * Suchen Sie im Apps-Dashboard die Kachel Push-Benachrichtigungen .
   * Wählen Sie die Benachrichtigung aus oder klicken Sie auf die Schaltfläche Details unten rechts (. .), um die Liste der Benachrichtigungen anzuzeigen. Diese Liste zeigt auch an, ob eine Benachrichtigung versandbereit ist, bereits gesendet wurde oder ob beim Senden ein Fehler aufgetreten ist.
   * Aktivieren Sie das Kontrollkästchen für nur eine Benachrichtigung und klicken Sie auf die Schaltfläche „Benachrichtigung senden“ oberhalb der Liste. Sie haben eine Möglichkeit, die Benachrichtigung in dem angezeigten Dialogfeld zu „Abbrechen“ oder „Senden“.

1. Umgang mit den Ergebnissen

   * Wenn der Push-Benachrichtigungs-Service (Amazon SNS oder Pushwoosh) die Sendeanfrage erhält, sie als gültig bestätigt und sie erfolgreich an die nativen Provider (APNS und GCM) sendet, wird das Dialogfeld Senden ohne Meldung geschlossen. In der Benachrichtigungsliste wird der Status dieser Benachrichtigung als Gesendet aufgeführt.
   * Wenn der Push-Versand fehlschlägt, wird im Dialogfeld eine Meldung mit dem Problem angezeigt. In der Benachrichtigungsliste wird der Status dieser Benachrichtigung als Fehler aufgeführt. Wenn das Problem jedoch behoben wird, kann die Benachrichtigung erneut gesendet werden. Wenn ein Fehler auftritt, sollten zusätzliche Fehlerinformationen im Server-Fehlerprotokoll angezeigt werden.
   * Beachten Sie, dass es einige Plattformunterschiede zwischen iOS und Android™-Push-Benachrichtigungen gibt. Darunter:

      * Beim Erstellen mit CLI wird die App gestartet, nachdem sie auf Android™ bereitgestellt wurde. In iOS müssen Sie sie manuell starten. Da der Schritt zur Push-Registrierung beim Start erfolgt, können Android™-Apps Push-Benachrichtigungen sofort empfangen (da sie bereits gestartet und registriert wurden), während iOS-Apps dies nicht können.
      * In Android™ ist der Text der Schaltfläche „OK“ in Großbuchstaben (und in allen anderen Schaltflächen, die der In-App-Benachrichtigung hinzugefügt wurden), in iOS dagegen nicht.

Für AMS-Push-Benachrichtigungen müssen Benachrichtigungen vom AMS-Server erstellt und gesendet werden. AMS bietet zusätzliche Push-Benachrichtigungsfunktionen, die über die von AEM-Benachrichtigungen mit AWS und Pushwoosh bereitgestellten hinausgehen.

>[!NOTE]
>
>*Push-Benachrichtigungen sind keine garantierte Zustellung, sondern ähneln Ankündigungen. Es wird alles getan, um sicherzustellen, dass jeder es hört, aber sie sind kein garantierter Bereitstellungsmechanismus. Außerdem kann die Zeit zum Bereitstellen einer Push-Benachrichtigung von weniger als einer Sekunde bis zu einer halben Stunde variieren.*

### Konfigurieren von Deep-Linking mit Push-Benachrichtigungen {#configuring-deep-linking-with-push-notifications}

Was ist Deep-Linking? Im Kontext einer Push-Benachrichtigung ist dies eine Möglichkeit, eine App zu öffnen oder an einen bestimmten Speicherort innerhalb der App weiterzuleiten (falls geöffnet).

Wie funktioniert das? Der Autor einer Push-Benachrichtigung fügt optional eine Schaltflächenbeschriftung hinzu (d. h. „Anzeigen!„) auf die Benachrichtigung zugreifen und über einen visuellen Pfad-Browser die Seite auswählen, die in der Benachrichtigung verknüpft werden soll. Beim Versand erfolgt die Push-Benachrichtigung wie gewohnt, mit dem Unterschied, dass in der In-App-Nachricht die OK-Schaltfläche durch eine Schaltfläche „Schließen“ ersetzt und die neue Schaltfläche angegeben wird („Anzeigen!„) wird auch angezeigt. Durch Klicken auf die Schaltfläche „Neu“ wechselt die App zur angegebenen Seite innerhalb der App. Durch Klicken auf Verwerfen wird die Nachricht verworfen.

Wenn die App nicht geöffnet ist, wird der Farbton normal angezeigt. Wenn Sie eine Aktion für die Benachrichtigung im Schatten durchführen, wird die App geöffnet und den Benutzenden werden dann die Deep-Link-Schaltflächen angezeigt, die auf den in der Push-Benachrichtigung konfigurierten Elementen basieren.

Erstellen Sie die Benachrichtigung, fügen Sie einen Schaltflächentext und einen Link-Pfad für den optionalen Deep-Link hinzu:

>[!CAUTION]
>
>Gehen Sie wie folgt vor, um auf die Kachel Push-Benachrichtigung in Ihrem Dashboard zuzugreifen.

1. Klicken Sie oben rechts auf der Kachel **Cloud Service verwalten** auf Bearbeiten .

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Wählen Sie die **Pushwoosh-Verbindung**. Klicken Sie auf **Weiter**.

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. Geben Sie die Details der Eigenschaften ein und klicken Sie auf **Senden**.

   ![chlimage_1-110](assets/chlimage_1-110.png)

   Sobald Sie Ihre Konfiguration übermitteln, wird die Kachel **Push-**&quot; im Dashboard angezeigt.

   ![chlimage_1-111](assets/chlimage_1-111.png)

### Assistent zum Erstellen von Benachrichtigungen {#create-notification-wizard}

Sobald die Kachel **Push-**&quot; in Ihrem Dashboard angezeigt wird, verwenden Sie den Assistenten „Benachrichtigung erstellen“, um den Inhalt hinzuzufügen:

1. Klicken Sie auf das Hinzufügen -Symbol oben rechts in der Kachel **Push-Benachrichtigungen**, um den Assistenten **Benachrichtigung erstellen“** öffnen.

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. Durch Klicken auf das Symbol „Durchsuchen“ im Link-Pfad wird dem Benutzer die Inhaltsstruktur der App angezeigt.

   Nachdem Sie den Pfad ausgewählt haben, klicken Sie auf das Häkchensymbol.

   ![chlimage_1-113](assets/chlimage_1-113.png)

   >[!NOTE]
   >
   >Der Text der Link-Schaltfläche ist auf 20 Zeichen begrenzt.
   >
   >Wenn der Endbenutzer nicht über die neueste Version des Programms verfügt und der verknüpfte Pfad nicht verfügbar ist, wird er durch Bestätigen der Aktion des Deep-Links zur Hauptseite der App weitergeleitet.

1. Geben Sie im Assistenten **Benachrichtigung erstellen** die Option **Textdetails** ein und klicken Sie auf **Erstellen**.

   ![chlimage_1-114](assets/chlimage_1-114.png)

   Öffnen Sie die Details, indem Sie auf die von Ihnen erstellte Push-Benachrichtigung in der Kachel **Push-Benachrichtigungen** klicken.

   Sie können Eigenschaften bearbeiten, Benachrichtigungen senden oder die Benachrichtigung löschen.

   ![chlimage_1-115](assets/chlimage_1-115.png)

>[!NOTE]
>
>**Zusätzliche Informationen**:
>
>Pushwoosh und Amazon SNS werden nach Version 6.4 nicht mehr unterstützt und sind als Add-on von Package Share verfügbar.

### Die nächsten Schritte {#the-next-steps}

Sobald Sie die Details zu Push-Benachrichtigungen für Ihre App verstanden haben, lesen Sie [AEM Mobile Content Personalization](/help/mobile/phonegap-aem-mobile-content-personalization.md).
