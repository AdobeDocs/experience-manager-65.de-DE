---
title: Entwickeln von Apps mit PhoneGap CLI
description: Erfahren Sie, wie Sie mit PhoneGap CLI Apps für Mobilgeräte mithilfe einer bootfähigen Entwicklungsumgebung entwickeln.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: fbeceb70-b199-478b-907b-253ed212ff99
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 6%

---

# Entwickeln von Apps mit PhoneGap CLI{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Als Entwickler können Sie Ihre App jederzeit auf einem Gerät oder in einem Emulator ausführen, sofern Sie Ihre Entwicklungsumgebung konfiguriert haben.

Um die folgenden Beispiele auszuführen, benötigen Sie ein System, das macOS X mit Xcode ausführt, oder ein Mac/Win/Linux-System mit installiertem Android™ SDK.

## Bootstrap Ihrer Entwicklungsumgebung {#bootstrap-your-development-environment}

Einrichten der PhoneGap-CLI (`https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface`)

Für iOS: Für die Entwicklung für iPhones und iPads benötigen Sie die Xcode-IDE von Apple.

* kostenlos herunterladen [here](https://idmsa.apple.com/IDMSWebAuth/signin?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&amp;path=%2Fdownload%2F&amp;rv=1).
* Handbuch zur PhoneGap iOS-Plattform (`https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide`)

Für Android™: Zur Entwicklung für iPhones und iPads benötigen Sie die Google Android™ Stuido IDE.

* kostenlos herunterladen [here](https://developer.android.com/studio).
* Handbuch zur PhoneGap Android™-Plattform (`https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide`)

## Quelle herunterladen {#download-the-source}

Wenn Sie Ihre Entwicklungsumgebung erfolgreich per Bootstrapping gestartet haben, laden Sie die Quelle aus der AEM App-Build-Kachel herunter:

* Klicken Sie auf den Dropdown-Chevron für die PhoneGap Build-Kachel.

![chlimage_1-45](assets/chlimage_1-45.png)

* Klicken Sie auf Quelle herunterladen .
* Wählen Sie die gewünschte Quelle aus dem Modal Quelle herunterladen aus.

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>Die Entwicklungsquelle enthält den neuesten Status Ihrer App und gleichzeitig nicht gestaffelte Änderungen. Verwenden Sie die Staging-Quelle zum Erstellen von Release-Kandidaten für das Senden an Appstore-Anbieter.
>
>Wenn Sie Ihre App nie testen, wird durch die Auswahl von Staging-Triggern der Staging-Workflow (Tipp: wird in der im AppStore und im Google PlayStore verfügbaren PhoneGap Enterprise Viewer App als gestaffelte App angezeigt).

* Klicken Sie auf Herunterladen und speichern Sie die ZIP-Datei auf Ihrem Computer.
* Extrahieren Sie die heruntergeladene ZIP-Datei in Ihren Arbeitsbereich.

## Erstellen und Laden der App (aus der Quelle) {#build-and-load-the-app-from-source}

Die PhoneGap-CLI kann ein Plattformprojekt erstellen, die Quelle kompilieren und die App in einem einzelnen Befehl bereitstellen.

>[!NOTE]
>
>Sie können alle diese Schritte separat ausführen, siehe PhoneGap-CLI-Dokumente (`https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/`).

1. Stellen Sie sicher, dass Sie PhoneGap CLI installiert haben (siehe oben).
1. Navigieren Sie in einem Konsolenfenster (oder Terminalfenster) zum Stammverzeichnis der extrahierten Quelle.
1. Geben Sie den folgenden Befehl ein:

```xml
phonegap run android

// -- or -- //

phonegap run ios
```

>[!NOTE]
>
>Wenn Sie derzeit Probleme haben, gehen Sie zurück zu den Grundlagen, um eine Fehlerbehebung durchzuführen -
>
>1. Erstellen eines Ordners (mkdir-Test)
>1. Navigieren Sie in diesen neuen Ordner (cd test).
>1. Führen Sie `phonegap create helloWorld` aus.
>1. Navigieren Sie zu helloWorld (cd helloWorld).
>1. Ausführen `phonegap run android` (oder ersetzen Sie Android™ durch iOS wie oben beschrieben).
>1. Emulator öffnet die neu erstellte PhoneGap-App mit der Meldung &quot;Device Ready&quot;, wenn die JavaScript Bridge zu nativ betriebsbereit ist.
>
>Mit dieser Fehlerbehebung wird überprüft, ob Ihre PhoneGap-CLI-Entwicklungsumgebung ordnungsgemäß ausgeführt wird.

## Debuggen von JavaScript mit Safari- und IOS-Debugging {#debug-javascripts-with-safari-and-ios-debug}

Sie können das JavaScript Ihrer App mit den Entwicklerwerkzeugen von Safari genauso debuggen wie mit einer Webanwendung.

## Aktivieren der Safari-Entwicklertools {#enable-safari-developer-tools}

So aktivieren Sie die Entwicklertools:

* Öffnen Sie die Voreinstellungen von Safari

   * Klicken Sie in der Menüleiste auf Safari
   * Klicken Sie auf Voreinstellungen

* Klicken Sie im Fenster &quot;Voreinstellung&quot;auf Erweitert .

![chlimage_1-47](assets/chlimage_1-47.png)

* Aktivieren Sie &quot;Menü &quot;Entwickeln&quot;in der Menüleiste anzeigen&quot;.
* Fenster &quot;Voreinstellung&quot;schließen

## Safari mit iOS verbinden {#connect-safari-to-ios}

Sie können Safari entweder mit einem iOS-Gerät oder -Emulator verbinden.

* Navigieren Sie in einem Konsolenfenster zum Stammverzeichnis der extrahierten Quelle.
* Geben Sie den folgenden Befehl ein, damit Sie Ihre App auf Ihrem Gerät oder Emulator starten können.

```xml
phonegap run <platform> --device

// -- or -- //

phonegap run <platform> --emulator
```

* Safari öffnen
* Klicken Sie in der Menüleiste auf Entwickeln .
* IOS Simulator-Untermenü auswählen
* Klicken Sie auf home.html

![chlimage_1-48](assets/chlimage_1-48.png)

## Debuggen von JavaScript mit dem Webinspektor von Safari {#debug-javascript-with-safari-s-web-inspector}

Sie können Haltepunkte an einer beliebigen Stelle in Ihrer Quelle festlegen. Wenn Sie mit Ihrem Emulator oder Gerät interagieren, stoppt die Ausführung Ihrer App an diesen Haltepunkten. Sie können die Ausführung schrittweise durchführen und die Werte in Variablen überprüfen.

* Klicken Sie im Fenster des Web-Inspektors auf Ressourcen .
* Navigieren Sie in der Quellstruktur und klicken Sie auf die gewünschte Quelldatei.
* Klicken Sie auf die Zeilennummer neben, um einen Haltepunkt hinzuzufügen.
* Interagieren mit dem Gerät oder Emulator

![chlimage_1-49](assets/chlimage_1-49.png)

* Verwenden Sie die Schaltflächen, um die Ausführung fortzusetzen, einen Schritt weiter zu gehen, Schritte in die Methoden einzuleiten und auszusteigen:

![Fünf verschiedene funktionierende Schaltflächen, die in einer horizontalen Zeile ausgerichtet sind.](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Bewegen Sie die Maus, um die Werte der Variablen in der aktuellen Methode anzuzeigen.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit der Entwicklung von Apps mit PhoneGap CLI vertraut gemacht haben, lesen Sie [Zugreifen auf Gerätefunktionen](/help/mobile/phonegap-access-device-features.md).
