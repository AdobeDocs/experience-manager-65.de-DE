---
title: Erstellen von Mobile Apps
description: Auf dieser Seite finden Sie einen vollständigen Artikel, in dem Schritt für Schritt beschrieben wird, wie Sie eine Mobile App mit Code erstellen, der von GitHub verfügbar ist. Erstellen Sie Ihre Anwendung für die Installation auf einem Gerät oder Simulator zum Testen oder Veröffentlichen in App Stores. Sie können Anwendungen lokal mit der PhoneGap-Befehlszeilenschnittstelle oder in der Cloud mit PhoneGap Build erstellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 7c2e5ed8-9f8e-4a81-b736-589ef4089f29
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---

# Erstellen von Mobile Apps{#building-mobile-applications}

{{ue-over-mobile}}

Erstellen Sie Ihre Anwendung für die Installation auf einem Gerät oder Simulator zum Testen oder Veröffentlichen in App Stores. Sie können Anwendungen lokal mit der PhoneGap-Befehlszeilenschnittstelle oder in der Cloud mit PhoneGap Build erstellen.

Einen vollständigen Artikel mit einer schrittweisen Anleitung zum Erstellen einer Mobile App mit Code von GitHub finden Sie [hier](https://helpx.adobe.com/experience-manager/using/aem62_mobile.html).

## Verschieben der Anwendung in die Publish-Instanz {#moving-the-application-to-the-publish-instance}

Verschieben Sie Anwendungsdateien in die Veröffentlichungsinstanz, damit Sie den installierten Instanzen der Mobile App Inhaltsaktualisierungen bereitstellen und die App mit den veröffentlichten Inhalten erstellen können. Anwendungen bestehen aus zwei Knotenverzweigungen im Repository:

* `/content/phonegap/apps/<application name>`: Die Web-Seiten, die Autoren erstellen und aktivieren.
* `/content/phonegap/content/<application name>`: Anwendungskonfigurationsdateien und Inhaltssynchronisierungskonfigurationen.

>[!NOTE]
>
>Wenn Sie die Anwendungsdateien nicht in die Veröffentlichungsinstanz verschieben, können Inhaltsautoren den Inhaltssynchronisierungs-Cache nicht aktualisieren.

Sie müssen nur die Dateien in der `/content/phonegap/content/<application name>` Verzweigung in die Veröffentlichungsinstanz verschieben. Die Dateien in der `/content/phonegap/apps/<application name>` Verzweigung werden verschoben, wenn der Autor die Seiten aktiviert.

AEM bietet zwei Methoden zum Verschieben von Masseninhalten in die Veröffentlichungsinstanz:

* [Verwenden Sie den Befehl Tree aktivieren](/help/sites-authoring/publishing-pages.md) auf der Replikationskonsole.
* [Erstellen Sie ein Paket](/help/sites-administering/package-manager.md) das den Inhalt enthält, und replizieren Sie das Paket.

Beispielsweise wird eine Mobile App mit dem Namen PhoneApp erstellt. Der folgende Knoten muss in die Veröffentlichungsinstanz verschoben werden: /content/phonegap/content/phonegapapp.

**Tipp:** Um ein Paket von der Autoreninstanz in die Veröffentlichungsinstanz zu verschieben, verwenden Sie den Befehl „Replicate“ für das Paket.

![chlimage_1-16](assets/chlimage_1-16.png)

## Erstellen mit der PhoneGap-Befehlszeilenschnittstelle {#building-using-the-phonegap-command-line-interface}

Kompilieren Sie die PhoneGap-Anwendung auf Ihrem Computer mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI). Um den AEM-Inhalt in Ihr Programm aufzunehmen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer Mobile App, Inhaltssynchronisierungskonfigurationen und andere erforderliche Assets enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

### Vorbereiten der Build-Umgebung {#preparing-your-build-environment}

Um mit der PhoneGap-CLI zu erstellen, müssen Sie Node.js und das PhoneGap-Client-Dienstprogramm installieren. Sie benötigen eine Internetverbindung, um das folgende Verfahren durchzuführen.

1. Herunterladen und Installieren von [Node.js](https://nodejs.org/de).
1. Öffnen Sie ein Terminal oder eine Eingabeaufforderung und geben Sie den folgenden Knotenbefehl ein, um das PhoneGap-Dienstprogramm zu installieren:

   ```shell
   npm install -g phonegap
   ```

   Auf einem UNIX®- oder Linux®-System muss dem Befehl möglicherweise das Präfix `sudo` vorangestellt werden.

   Das Terminal zeigt die Ergebnisse einer Reihe von HTTP-GET-Befehlen an. Nach erfolgreicher Installation zeigt das Terminal ähnlich dem folgenden Beispiel an, wo die Bibliotheken installiert sind:

   ```xml
   /usr/local/bin/phonegap -> /usr/local/lib/node_modules/phonegap/bin/phonegap.js
   phonegap@3.3.0-0.19.6 /usr/local/lib/node_modules/phonegap
   ├── pluralize@0.0.4
   ├── colors@0.6.0-1
   ├── semver@1.1.0
   ├── qrcode-terminal@0.9.4
   ├── shelljs@0.1.4
   ├── optimist@0.6.0 (...)
   ├── prompt@0.2.11 (...)
   ├── phonegap-build@0.8.4 (...)
   ├── connect-phonegap@0.8.1 (...)
   └── cordova@3.3.0-0.1.1 (...)
   ```

1. (Optional) Rufen Sie die SDK für die Mobilplattform ab, auf die Sie abzielen:

   * Um Apps für die iOS-Plattform zu erstellen, installieren Sie die neueste Version von [Xcode](https://developer.apple.com/xcode/).
   * Um Android™-Apps zu erstellen, installieren Sie die [Android™-SDK](https://developer.android.com/).

### Herunterladen der ZIP-Inhaltsdatei {#downloading-the-content-zip-file}

Verschieben Sie den Inhalt Ihrer Mobile App in Ihr Dateisystem.

1. Wählen Sie auf der Seite Mobile Apps Ihre Mobile App aus.
1. (Optional) Um das Programm für vollständige Installationen zu erstellen, klicken Sie in der Symbolleiste auf Cache löschen .

   ![Cache-Symbol löschen, das durch ein fehlerhaftes Link-Symbol gekennzeichnet wird.](do-not-localize/chlimage_1.png)

   >[!NOTE]
   >
   >Der Cache enthält Inhaltsaktualisierungen für installierte Anwendungen. Durch Löschen des Cache werden alle zwischengespeicherten Aktualisierungen ungültig.

1. Klicken Sie in der Symbolleiste auf das Symbol CLI Assets herunterladen .

   ![Herunterladen des CLI-Assets-Symbols, das durch die Überlappung des Tablet-Symbols angezeigt wird.](do-not-localize/chlimage_1-1.png)

1. Nachdem Sie die ZIP-Datei gespeichert haben, klicken Sie im Dialogfeld Erfolg auf Schließen .
1. Extrahieren Sie den Inhalt der ZIP-Datei.

### Verwenden der PhoneGap-CLI zum Erstellen {#using-the-phonegap-cli-to-build}

Kompilieren und installieren Sie die Anwendung über die PhoneGap-CLI. Informationen zur Verwendung der PhoneGap-CLI finden Sie in der Dokumentation zur PhoneGap-Befehlszeilenschnittstelle (`https://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html`) .

1. Öffnen Sie ein Terminal oder eine Eingabeaufforderung und ändern Sie das aktuelle Verzeichnis in die heruntergeladene ZIP-Datei der Anwendung. Beispielsweise ändert Folgendes das Verzeichnis in die Datei „ng-app-cli.1392137825303.zip“:

   ```shell
   cd ~/Downloads/ng-app-cli.1392137825303
   ```

1. Geben Sie den PhoneGap-Befehl für die Plattform ein, auf die Sie abzielen. Der folgende Befehl erstellt beispielsweise die App für Android™:

   ```shell
   phonegap build android
   ```

## Erstellen mit PhoneGap Build {#building-using-phonegap-build}

Verwenden Sie den PhoneGap-Cloud-Service, um Ihre App zu erstellen. Um dieses Verfahren durchzuführen, müssen Sie zunächst eine PhoneGap Build-Konfiguration erstellen.

### Herstellen einer Verbindung zu PhoneGap Build {#connecting-to-phonegap-build}

Erstellen Sie eine PhoneGap Build-Konfiguration, damit Sie die PhoneGap Build-Services von AEM aus verwenden können. Geben Sie den Benutzernamen und das Kennwort des PhoneGap Build-Kontos an, das Sie zum Erstellen Ihrer Mobile Apps verwenden werden.

1. Öffnen Sie die Seite Tools . ([http://localhost:4502/tools.html](http://localhost:4502/tools.html)).
1. Klicken Sie im Bereich CQ-Vorgänge auf Cloud Service.
1. Klicken Sie auf den Link Jetzt konfigurieren für PhoneGap Build.

   ![chlimage_1-17](assets/chlimage_1-17.png)

1. Geben Sie im Dialogfeld Konfiguration erstellen einen Wert für die Eigenschaft Titel ein. Standardmäßig wird der Wert der Name-Eigenschaft aus dem Titel abgeleitet, Sie können jedoch einen Namen eingeben. Klicken Sie auf „Erstellen“.
1. Geben Sie im Dialogfeld &quot;PhoneGap Build-Konfiguration“ Ihren PhoneGap Build-Benutzernamen und Ihr Kennwort ein und klicken Sie auf „OK“.

### Verwenden von PhoneGap Build {#using-phonegap-build}

Senden Sie die Anwendungsressourcen zur Kompilierung für die verschiedenen mobilen Plattformen an PhoneGap Build.

1. Öffnen Sie auf der Seite „Mobile Apps“ Ihre Mobile App. ([http://localhost:4502/mobile.html/content/phonegap](http://localhost:4502/mobile.html/content/phonegap))
1. (Optional) Um das Programm für vollständige Installationen zu erstellen, wählen Sie das Programm aus und klicken Sie auf das Symbol Cache löschen .

   ![Cache-Symbol löschen, das durch ein fehlerhaftes Link-Symbol gekennzeichnet wird.](do-not-localize/chlimage_1-2.png)

   >[!NOTE]
   >
   >Der Cache enthält Inhaltsaktualisierungen für installierte Anwendungen. Durch Löschen des Cache werden alle zwischengespeicherten Aktualisierungen ungültig.

1. Wählen Sie die Splash-Seite aus und klicken Sie dann auf das Symbol Remote erstellen .

   ![Build Remote-Symbol durch zwei runde Zahnräder angezeigt.](do-not-localize/chlimage_1-3.png)

   **Hinweis:** Die Beta-Version von AEM Beta erstellt keine Posteingangsbenachrichtigung, wenn der Build erfolgreich abgeschlossen wurde.

1. Klicken Sie im Dialogfeld Erfolg auf PhoneGap Build , um die Seite Adobe PhoneGap Build unter `https://build.phonegap.com/apps` zu öffnen. Wenn Sie darauf warten, dass Ihre App angezeigt wird, können Sie den PhoneGap Build-Status unter `https://status.build.phonegap.com/` überprüfen.

   Informationen zum Installieren des Builds finden Sie in der [PhoneGap Build-Dokumentation](https://github.com/phonegap/phonegap-docs/tree/master/docs/4-phonegap-build).

   >[!NOTE]
   >
   >Kostenlose PhoneGap Build-Konten sind in einer privaten Anwendung erlaubt. PhoneGap-Builds schlagen fehl, wenn Sie eine zusätzliche private Anwendung erstellen.

### Die nächsten Schritte {#the-next-steps}

Der nächste Schritt nach dem Erstellungsprozess besteht darin, mehr über die [Struktur einer App](/help/mobile/phonegap-structure-an-app.md) zu erfahren.
