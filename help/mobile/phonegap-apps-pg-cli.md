---
title: Entwickeln von Apps mit PhoneGap CLI
seo-title: Entwickeln von Apps mit PhoneGap CLI
description: Auf dieser Seite erfahren Sie mehr über die Entwicklung von Apps mit PhoneGap CLI.
seo-description: Auf dieser Seite erfahren Sie mehr über die Entwicklung von Apps mit PhoneGap CLI.
uuid: 9a66171d-19af-40db-9c07-f5dd9561e1b5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 4a034e15-3394-4be3-9e8e-bc894668946a
exl-id: fbeceb70-b199-478b-907b-253ed212ff99
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 4%

---

# Entwickeln von Apps mit PhoneGap CLI{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Als Entwickler können Sie Ihre App jederzeit auf einem Gerät oder in einem Emulator ausführen, sofern Sie Ihre Entwicklungsumgebung konfiguriert haben.

Um die folgenden Beispiele auszuführen, benötigen Sie ein System, das OSx (Mac) mit Xcode ausführt, oder ein Mac/Win/Linux-System mit installiertem Android-SDK.

## Bootstrap Ihrer Entwicklungsumgebung {#bootstrap-your-development-environment}

[Einrichten der PhoneGap-CLI](https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)

Für iOS: Für die Entwicklung für iPhones und iPads benötigen Sie die Xcode-IDE von Apple.

* Laden Sie es kostenlos [hier](https://developer.apple.com/xcode/downloads/) herunter.
* [Handbuch zur PhoneGap iOS-Plattform](https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)

Für Android: Für die Entwicklung für iPhones und iPads benötigen Sie die Android Stuido IDE von Google.

* Laden Sie es kostenlos [hier](https://developer.android.com/sdk/index.html) herunter.
* [Handbuch zur PhoneGap Android-Plattform](https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide)

## Quelle herunterladen {#download-the-source}

Nachdem Sie die Entwicklungsumgebung erfolgreich gebootet haben, laden Sie die Quelle aus der Kachel zum Erstellen der AEM App herunter:

* Klicken Sie auf den Dropdown-Chevron der PhoneGap Build-Kachel.

![chlimage_1-45](assets/chlimage_1-45.png)

* Klicken Sie auf Quelle herunterladen .
* Wählen Sie die gewünschte Quelle aus dem Modal Quelle herunterladen aus.

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>Die Entwicklungsquelle enthält den neuesten Status Ihrer App, einschließlich nicht gestaffelter Änderungen. Verwenden Sie die Staging-Quelle zum Erstellen von Release-Kandidaten für das Senden an Appstore-Anbieter.
>
>Wenn Sie Ihre App nie testen, wird durch die Auswahl von Staging der Staging-Workflow Trigger (Tipp: wird als gestaffelte App in der PhoneGap Enterprise Viewer App angezeigt, die im AppStore und im Google Play Store verfügbar ist.

* Klicken Sie auf Herunterladen und speichern Sie die ZIP auf Ihrem Computer.
* Extrahieren Sie die heruntergeladene ZIP-Datei in Ihren Arbeitsbereich.

## Erstellen und laden Sie die App (aus der Quelle) {#build-and-load-the-app-from-source}

Die PhoneGap-CLI kann ein Plattformprojekt erstellen, die Quelle kompilieren und die App in einem einzelnen Befehl bereitstellen.

>[!NOTE]
>
>Sie können alle diese Schritte separat ausführen, siehe [PhoneGap CLI docs](https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/).

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
>Wenn Sie derzeit Probleme haben, gehen Sie zurück zu den Grundlagen zu Trommelschießen -
>
>1. Erstellen eines neuen Ordners (mkdir test)
>1. Navigieren Sie in diesen neuen Ordner (cd test).
>1. Führen Sie &#39;phonegap create helloWorld&#39; aus.
>1. Navigieren Sie zu helloWorld (cd helloWorld).
>1. Führen Sie &#39;phonegap run android (oder ersetzen Sie android durch ios wie oben).
>1. Emulator öffnet die neu erstellte PhoneGap-App mit der Meldung &quot;Device Ready&quot;, wenn die JavaScript-Verbindung zum nativen Gerät betriebsbereit ist.

>
>
Dadurch wird sichergestellt, dass die PhoneGap-CLI-Entwicklungsumgebung ordnungsgemäß ausgeführt wird.

## Debuggen von Javascripts mit Safari und IOS-Debugging {#debug-javascripts-with-safari-and-ios-debug}

Sie können die JavaScripts Ihrer App mit den Entwicklertools von Safari debuggen, so wie bei einer Webanwendung.

## Aktivieren Sie Safari Developer Tools {#enable-safari-developer-tools}

So aktivieren Sie die Entwicklertools:

* Öffnen Sie die Voreinstellungen von Safari.

   * Klicken Sie in der Menüleiste auf Safari
   * Klicken Sie auf Voreinstellungen

* Klicken Sie im Fenster &quot;Voreinstellung&quot;auf Erweitert .

![chlimage_1-47](assets/chlimage_1-47.png)

* Aktivieren Sie &quot;Menü &quot;Entwickeln&quot;in der Menüleiste anzeigen&quot;.
* Fenster &quot;Voreinstellung&quot;schließen

## Verbinden von Safari mit iOS {#connect-safari-to-ios}

Sie können Safari entweder mit einem iOS-Gerät oder Emulator verbinden.

* Navigieren Sie in einem Konsolenfenster zum Stammverzeichnis der extrahierten Quelle.
* Geben Sie den folgenden Befehl ein, um Ihre App auf Ihrem Gerät oder Emulator zu starten.

```xml
phonegap run <platform> --device

// -- or -- //

phonegap run <platform> --emulator
```

* Safari öffnen
* Klicken Sie in der Menüleiste auf Entwickeln .
* iOS Simulator-Untermenü auswählen
* Auf home.html klicken

![chlimage_1-48](assets/chlimage_1-48.png)

## Debuggen von JavaScript mit dem Webinspektor von Safari {#debug-javascript-with-safari-s-web-inspector}

Sie können Haltepunkte an einer beliebigen Stelle in Ihrer Quelle festlegen. Wenn Sie mit Ihrem Emulator oder Gerät interagieren, stoppt die Ausführung Ihrer App an diesen Haltepunkten. Sie können die Ausführung schrittweise durchführen und die Werte in Variablen überprüfen.

* Klicken Sie im Fenster des Web-Inspektors auf Ressourcen .
* Navigieren Sie in der Quellstruktur und klicken Sie auf die gewünschte Quelldatei
* Klicken Sie auf die Zeilennummer neben, um einen Haltepunkt hinzuzufügen.
* Interagieren mit dem Gerät oder Emulator

![chlimage_1-49](assets/chlimage_1-49.png)

* Verwenden Sie die Kontrollschaltflächen, um die Ausführung fortzusetzen, Schritt für Schritt vorzunehmen, Schritte in die Methoden einzuleiten und auszusteigen:

![](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Um die Werte der Variablen anzuzeigen, bewegen Sie in der aktuellen Methode den Mauszeiger über.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit der Entwicklung von Apps mit PhoneGap CLI vertraut gemacht haben, lesen Sie [Zugriff auf Gerätefunktionen](/help/mobile/phonegap-access-device-features.md).
