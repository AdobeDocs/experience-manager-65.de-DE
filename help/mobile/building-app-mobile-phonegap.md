---
title: Erstellen von Mobilanwendungen
seo-title: Erstellen von Mobilanwendungen
description: Auf dieser Seite finden Sie einen vollständigen Schritt-für-Schritt-Artikel zum Erstellen einer mobilen Anwendung mit dem von GitHub verfügbaren Code. Erstellen Sie Ihre Anwendung, um sie auf einem Gerät oder Simulator zu installieren, um sie zu testen oder in App Stores zu veröffentlichen. Sie können Anwendungen lokal über die PhoneGap-Befehlszeilenschnittstelle oder in der Cloud mithilfe von PhoneGap Build erstellen.
seo-description: Auf dieser Seite finden Sie einen vollständigen Schritt-für-Schritt-Artikel zum Erstellen einer mobilen Anwendung mit dem von GitHub verfügbaren Code. Erstellen Sie Ihre Anwendung, um sie auf einem Gerät oder Simulator zu installieren, um sie zu testen oder in App Stores zu veröffentlichen. Sie können Anwendungen lokal über die PhoneGap-Befehlszeilenschnittstelle oder in der Cloud mithilfe von PhoneGap Build erstellen.
uuid: 1ff6fe1a-24cc-4973-a2cd-8d356bc649b0
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b2778086-8280-4306-bf3a-f6ec2a0e04df
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 5%

---


# Erstellen von Mobilanwendungen{#building-mobile-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Erstellen Sie Ihre Anwendung, um sie auf einem Gerät oder Simulator zum Testen oder zur Veröffentlichung in App Stores zu installieren. Sie können Anwendungen lokal über die PhoneGap-Befehlszeilenschnittstelle oder in der Cloud mithilfe von PhoneGap Build erstellen.

Ein vollständiger Schritt-für-Schritt-Artikel zum Erstellen einer Mobilanwendung mit dem von GitHub verfügbaren Code ist [hier](https://helpx.adobe.com/experience-manager/using/aem62_mobile.html) verfügbar.

## Verschieben der Anwendung in die Veröffentlichungsinstanz {#moving-the-application-to-the-publish-instance}

Verschieben Sie Anwendungsdateien in die Veröffentlichungsinstanz, damit Sie Inhaltsaktualisierungen zu den installierten Instanzen der mobilen Anwendung bereitstellen und die Anwendung mit den veröffentlichten Inhalten erstellen können. Anwendungen bestehen aus zwei Knotenverzweigungen im Repository:

* `/content/phonegap/apps/<application name>`: Die Webseiten, die Autoren erstellen und aktivieren.
* `/content/phonegap/content/<application name>`: Anwendungskonfigurationsdateien und Inhaltssynchronisierungskonfigurationen.

>[!NOTE]
>
>Wenn Sie die Anwendungsdateien nicht in die Veröffentlichungsinstanz verschieben, können Inhaltsersteller den Content Sync-Cache nicht aktualisieren.

Sie müssen nur die Dateien in der Verzweigung `/content/phonegap/content/<application name>` in die Veröffentlichungsinstanz verschieben. Die Dateien in der Verzweigung `/content/phonegap/apps/<application name>` werden verschoben, wenn der Autor die Seiten aktiviert.

AEM bietet zwei Methoden zum Verschieben von Masseninhalten in die Veröffentlichungsinstanz:

* [Verwenden Sie den ](/help/sites-authoring/publishing-pages.md) Befehl &quot;Tree aktivieren&quot;in der Replizierungskonsole.
* [Erstellen Sie ein ](/help/sites-administering/package-manager.md) Paket, das den Inhalt enthält, und replizieren Sie das Paket.

Beispielsweise wird eine mobile Anwendung namens phonegapapp erstellt. Der folgende Knoten muss in die Veröffentlichungsinstanz verschoben werden: /content/phonegap/content/phonegapapp.

**Tipp:** Um ein Paket von der Autoreninstanz in die Veröffentlichungsinstanz zu verschieben, verwenden Sie den Befehl &quot;Replizieren&quot;im Paket.

![chlimage_1-16](assets/chlimage_1-16.png)

## Erstellen mit der PhoneGap-Befehlszeilenschnittstelle {#building-using-the-phonegap-command-line-interface}

Das Kompilieren der PhoneGap-App erfolgt auf Ihrem Computer mithilfe der PhoneGap-Befehlszeilenoberfläche (Command Line Interface, CLI). Um den AEM Inhalt in Ihre Anwendung einzubeziehen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer mobilen Anwendung, die Inhaltssynchronisierungskonfigurationen und andere erforderliche Elemente enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

### Vorbereiten der Build-Umgebung {#preparing-your-build-environment}

Um mit der PhoneGap-CLI zu erstellen, müssen Sie Node.js und das PhoneGap-Client-Dienstprogramm installieren. Sie benötigen eine Internetverbindung, um das folgende Verfahren auszuführen.

1. Laden Sie [Node.js](https://nodejs.org/) herunter und installieren Sie es.
1. Öffnen Sie ein Terminal oder eine Eingabeaufforderung und geben Sie den folgenden Knotenbefehl ein, um das PhoneGap-Dienstprogramm zu installieren:

   ```shell
   npm install -g phonegap
   ```

   Unter Unix oder Linux müssen Sie dem Befehl eventuell `sudo` voranstellen.

   Das Terminal zeigt die Ergebnisse einer Reihe von HTTP-GET an. Wenn die Installation erfolgreich ist, zeigt das Terminal an, wo die Bibliotheken ähnlich dem folgenden Beispiel installiert werden:

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

1. (Optional) SDK für die mobile Plattform abrufen, die Sie als Ziel auswählen:

   * Um Apps für die iOS-Plattform zu erstellen, installieren Sie die neueste Version von [Xcode](https://developer.apple.com/xcode/).
   * Um Android-Apps zu erstellen, installieren Sie das [Android SDK](https://developer.android.com/).

### Herunterladen der Content ZIP-Datei {#downloading-the-content-zip-file}

Verschieben Sie den Inhalt Ihrer mobilen Anwendung in Ihr Dateisystem.

1. Wählen Sie auf der Seite &quot;Mobilanwendungen&quot;Ihre Anwendung aus.
1. (Optional) Um die Anwendung für vollständige Installationen zu erstellen, klicken Sie in der Symbolleiste auf das Symbol Cache löschen oder tippen Sie auf das Symbol Cache löschen.

   ![](do-not-localize/chlimage_1.png)

   >[!NOTE]
   >
   >Der Cache enthält Inhaltsaktualisierungen für installierte Anwendungen. Beim Löschen des Zwischenspeichers werden alle zwischengespeicherten Aktualisierungen ausgeschlossen.

1. Klicken Sie in der Symbolleiste auf das Symbol &quot;CLI-Assets herunterladen&quot;oder tippen Sie darauf.

   ![](do-not-localize/chlimage_1-1.png)

1. Nachdem Sie die ZIP-Datei gespeichert haben, klicken Sie im Dialogfeld Erfolg auf Schließen.
1. Extrahieren Sie den Inhalt der ZIP-Datei.

### Verwenden der PhoneGap-CLI zum Erstellen von {#using-the-phonegap-cli-to-build}

Verwenden Sie die PhoneGap-CLI, um die Anwendung zu kompilieren und zu installieren. Informationen zur Verwendung der PhoneGap-CLI finden Sie in der Dokumentation PhoneGap [Befehlszeilenschnittstelle](https://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html).

1. Öffnen Sie ein Terminal oder eine Eingabeaufforderung und ändern Sie den aktuellen Ordner in die heruntergeladene ZIP-Datei der Anwendung. Beispielsweise wird im folgenden Beispiel der Ordner in die Datei &quot;ng-app-cli.1392137825303.zip&quot;geändert:

   ```shell
   cd ~/Downloads/ng-app-cli.1392137825303
   ```

1. Geben Sie den Befehl phonegap für die Plattform ein, die Sie als Ziel auswählen. Mit dem folgenden Befehl wird beispielsweise die App für Android erstellt:

   ```shell
   phonegap build android
   ```

## Erstellen mit PhoneGap Build {#building-using-phonegap-build}

Verwenden Sie den PhoneGap-Cloud-Dienst, um Ihre App zu erstellen. Um dieses Verfahren auszuführen, müssen Sie zunächst eine PhoneGap Build erstellen.

### Verbindung zu PhoneGap Build {#connecting-to-phonegap-build}

Erstellen Sie eine PhoneGap Build, damit Sie die PhoneGap Build von AEM aus verwenden können. Geben Sie den Benutzernamen und das Kennwort des PhoneGap Build an, das Sie zum Erstellen Ihrer Mobilanwendungen verwenden werden.

1. Öffnen Sie die Seite &quot;Tools&quot;. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html)).
1. Klicken Sie im Bereich &quot;CQ-Vorgänge&quot;auf Cloud Services.
1. Klicken Sie auf den Link Jetzt konfigurieren für PhoneGap Build.

   ![chlimage_1-17](assets/chlimage_1-17.png)

1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Wert für die Eigenschaft &quot;Titel&quot;ein. Standardmäßig wird der Wert der Eigenschaft Name vom Titel abgeleitet, Sie können jedoch einen Namen eingeben. Klicken Sie auf Erstellen.
1. Geben Sie im Dialogfeld &quot;PhoneGap Build-Konfiguration&quot;Ihren Benutzernamen und Ihr Kennwort ein und klicken Sie auf &quot;OK&quot;.

### Verwenden von PhoneGap Build {#using-phonegap-build}

Senden Sie Ihre Anwendungsressourcen zur Kompilierung für die verschiedenen mobilen Plattformen an PhoneGap Build.

1. Öffnen Sie auf der Seite &quot;Mobilanwendungen&quot;Ihre Mobilanwendung. ([http://localhost:4502/mobile.html/content/phonegap](http://localhost:4502/mobile.html/content/phonegap))
1. (Optional) Um die Anwendung für vollständige Installationen zu erstellen, wählen Sie die Anwendung aus und klicken Sie auf das Symbol &quot;Cache löschen&quot;.

   ![](do-not-localize/chlimage_1-2.png)

   >[!NOTE]
   >
   >Der Cache enthält Inhaltsaktualisierungen für installierte Anwendungen. Beim Löschen des Zwischenspeichers werden alle zwischengespeicherten Aktualisierungen ausgeschlossen.

1. Wählen Sie die Begrüßungsseite und klicken Sie dann auf das Symbol &quot;Remote erstellen&quot;.

   ![](do-not-localize/chlimage_1-3.png)

   **Hinweis:** Die Beta-Version von AEM Beta erstellt keine Inbox-Benachrichtigung, wenn der Build erfolgreich abgeschlossen wurde.

1. Klicken Sie im Dialogfeld Erfolg auf PhoneGap Build, um die Seite Adobe PhoneGap Build unter [https://build.phonegap.com/apps](https://build.phonegap.com/apps) zu öffnen. Wenn Sie darauf warten, dass Ihre App angezeigt wird, können Sie die Seite [PhoneGap Build Status](https://status.build.phonegap.com/) überprüfen.

   Informationen zum Installieren des Builds finden Sie in der [PhoneGap Build Documentation](https://docs.build.phonegap.com/en_US/3.1.0/#googtrans%28en%29).

   >[!NOTE]
   >
   >Kostenlose PhoneGap Build sind nur für eine Privatanwendung zulässig. PhoneGap-Builds schlagen fehl, wenn Sie eine zusätzliche private Anwendung erstellen.

### Die nächsten Schritte {#the-next-steps}

Der nächste Schritt nach dem Erstellen ist das Erlernen der [Struktur einer App](/help/mobile/phonegap-structure-an-app.md).
