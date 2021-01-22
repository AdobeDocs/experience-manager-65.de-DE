---
title: Entwickeln von Apps mit der PhoneGap-CLI
seo-title: Entwickeln von Apps mit der PhoneGap-CLI
description: Auf dieser Seite erfahren Sie mehr über das Entwickeln von Apps mit der PhoneGap-CLI.
seo-description: Auf dieser Seite erfahren Sie mehr über das Entwickeln von Apps mit der PhoneGap-CLI.
uuid: 9a66171d-19af-40db-9c07-f5dd9561e1b5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 4a034e15-3394-4be3-9e8e-bc894668946a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 4%

---


# Entwickeln von Apps mit PhoneGap CLI{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Als Entwickler können Sie Ihre App jederzeit auf einem Gerät oder in einem Emulator ausführen, sofern Sie Ihre Entwicklungs-Umgebung konfiguriert haben.

Um die folgenden Beispiele auszuführen, benötigen Sie ein System, das OSx (Mac) mit Xcode oder ein Mac/Win/Linux-System mit installiertem Android SDK ausführt.

## Bootstrap Ihrer Umgebung für Entwicklung {#bootstrap-your-development-environment}

[Setup PhoneGap CLI](https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)

Für iOS: Zur Entwicklung für iPhones und iPads benötigen Sie die Xcode-IDE von Apple.

* Laden Sie es kostenlos [hier](https://developer.apple.com/xcode/downloads/) herunter.
* [Handbuch zur PhoneGap iOS-Plattform](https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)

Für Android: Für die Entwicklung für iPhones und iPads benötigen Sie die Google Android Stuido IDE.

* Laden Sie es kostenlos [hier](https://developer.android.com/sdk/index.html) herunter.
* [Handbuch zur PhoneGap Android-Plattform](https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide)

## Quelle herunterladen {#download-the-source}

Laden Sie die Umgebung nach dem erfolgreichen Hochladen der App-Entwicklung aus der AEM App-Build-Kachel herunter:

* Klicken Sie auf das PhoneGap Build Dropdown Chevron.

![chlimage_1-45](assets/chlimage_1-45.png)

* Klicken Sie auf Quelle herunterladen.
* Wählen Sie die gewünschte Quelle aus dem Modal Quelle herunterladen.

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>Die Entwicklungsquelle enthält den neuesten Status Ihrer App und enthält gleichzeitig nicht gestaffelte Änderungen. Verwenden Sie die Staging-Quelle, um Versionskandidaten zu erstellen, die an App Store-Anbieter übermittelt werden sollen.
>
>Wenn Sie Ihre App nie posten, wird durch Auswahl von Staging der Staging-Workflow Trigger (Hinweis: wird als gestaffelte App in der PhoneGap Enterprise Viewer-App angezeigt, die im AppStore und Google PlayStore verfügbar ist.

* Klicken Sie auf Herunterladen und speichern Sie die ZIP auf Ihrem Computer.
* Extrahieren Sie die heruntergeladene ZIP-Datei in Ihren Arbeitsbereich.

## Erstellen und laden Sie die App (aus der Quelle) {#build-and-load-the-app-from-source}

PhoneGap CLI kann ein Plattformprojekt erstellen, die Quelle kompilieren und die App in einem einzigen Befehl bereitstellen.

>[!NOTE]
>
>Sie können alle diese Schritte separat durchführen, siehe [PhoneGap-CLI-Dokumente](https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/).

1. Vergewissern Sie sich, dass Sie PhoneGap CLI installiert haben (siehe oben).
1. Navigieren Sie in einem Konsolenfenster (oder Terminalfenster) zum Stammverzeichnis der extrahierten Quelle.
1. Geben Sie den folgenden Befehl ein:

```xml
phonegap run android

// -- or -- //

phonegap run ios
```

>[!NOTE]
>
>Wenn Sie Probleme haben, gehen Sie zu den Grundlagen zurück, um Probleme zu schießen -
>
>1. Erstellen eines neuen Ordners (mkdir-Test)
>1. In diesen neuen Ordner navigieren (cd-Test)
>1. Führen Sie &#39;phonegap create helloWorld&#39; aus
>1. Navigieren Sie in helloWorld (cd helloWorld)
>1. Führen Sie &quot;phonegap run android (oder ersetzen Sie android durch ios wie oben).
>1. Emulator öffnet Ihre neu erstellte PhoneGap-App, wobei &quot;Device Ready&quot;steht, wenn die JavaScript-Brücke zu native aktiv ist.

>
>
Dadurch wird sichergestellt, dass die PhoneGap-Umgebung für die CLI-Entwicklung ordnungsgemäß ausgeführt wird.

## Debuggen von Javascripts mit Safari- und IOS-Debugging {#debug-javascripts-with-safari-and-ios-debug}

Sie können die JavaScripts Ihrer App mit den Entwicklerwerkzeugen von Safari debuggen, genau wie bei einer Webanwendung.

## Safari Developer Tools {#enable-safari-developer-tools} aktivieren

So aktivieren Sie die Entwicklerwerkzeuge:

* Safari-Voreinstellungen öffnen

   * Klicken Sie in der Menüleiste auf Safari
   * Klicken Sie auf Voreinstellungen

* Klicken Sie im Fenster &quot;Voreinstellungen&quot;auf Erweitert

![chlimage_1-47](assets/chlimage_1-47.png)

* Aktivieren Sie &quot;Entwicklungsmenü in der Menüleiste anzeigen&quot;.
* Fenster &quot;Voreinstellungen&quot;schließen

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
* Klicken Sie in der Menüleiste auf Entwickeln
* Untermenü &quot;iOS Simulator&quot;auswählen
* Klicken Sie auf home.html

![chlimage_1-48](assets/chlimage_1-48.png)

## Debuggen von JavaScript mit dem Webinspektor von Safari {#debug-javascript-with-safari-s-web-inspector}

Sie können Haltepunkte an einer beliebigen Stelle in der Quelle festlegen. Wenn Sie mit Ihrem Emulator oder Gerät interagieren, wird die Ausführung der App an diesen Haltepunkten beendet. Sie können die Ausführung schrittweise durchführen und die Werte in Variablen überprüfen.

* Klicken Sie im Fenster des Webinspektors auf &quot;Ressourcen&quot;
* Navigieren Sie zur Quellstruktur und klicken Sie auf die gewünschte Quelldatei
* Klicken Sie auf die Zeilennummer neben, um einen Haltepunkt hinzuzufügen
* Mit Gerät oder Emulator interagieren

![chlimage_1-49](assets/chlimage_1-49.png)

* Verwenden Sie die Steuerungsschaltflächen, um die Ausführung fortzusetzen, einen Schritt über die Methoden zu führen, Schritte zu gehen und die Methoden zu verlassen:

![](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Um die Werte der Variablen anzuzeigen, bewegen Sie in der aktuellen Methode den Mauszeiger über.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie Informationen zum Entwickeln von Apps mit der PhoneGap-CLI erhalten haben, finden Sie unter [Zugreifen auf Gerätefunktionen](/help/mobile/phonegap-access-device-features.md).
