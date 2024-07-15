---
title: Konfigurieren des Adobe PhoneGap Build-Cloud Service
description: Auf dieser Seite erfahren Sie, wie Sie die Cloud-Services konfigurieren und Ihre Anwendung mit PhoneGap Build erstellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: d91a00d1-12fa-4c84-a426-49413f61c126
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 5%

---

# Konfigurieren des Adobe PhoneGap Build-Cloud Service {#configure-your-adobe-phonegap-build-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit dem PhoneGap Build **Kachel** im Anwendungs-Dashboard können Sie Ihre PhoneGap-Mobile App über den Adobe PhoneGap Build-Dienst erstellen und verteilen.

Alle unterstützten Plattformen, die in der Kachel **App verwalten** definiert sind, werden beim Pushen eines Remote-Builds in die Kachel **PhoneGap Build** mit PhoneGap Build erstellt.

Sie können einen Remote-Build an `https://build.phonegap.com` übertragen oder die Quelle herunterladen, um mit der PhoneGap-CLI unter `https://docs.phonegap.com/references/phonegap-cli/` lokal zu erstellen.

![PhoneGap Build Tile](assets/chlimage_1-60.png)

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um die Vorteile von PhoneGap Build nutzen zu können, müssen Sie den AEM-PhoneGap Build mit Ihren PhoneGap Build-Kontoinformationen konfigurieren.

Wenn Sie derzeit kein Konto haben, navigieren Sie zu `https://build.phonegap.com` und melden Sie sich an! Wenn Sie über eine Adobe Creative Cloud-Mitgliedschaft verfügen, können Sie bis zu 25 private Apps (Nicht-Open-Source-Apps) unterstützen.

Nachdem Sie überprüft haben, ob Ihr PhoneGap Build-Konto aktiv ist, navigieren Sie zu Ihrer AEM Cloud Management Console, insbesondere zum [PhoneGap Build](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Verwenden Sie die Kachel **Cloud Service verwalten** , um eine neue Cloud Service-Konfiguration zu konfigurieren.

### Verwenden der Kachel Cloud Service verwalten {#using-manage-cloud-services-tile}

Bevor Sie mit der Erstellung Ihrer App mithilfe der Kachel **PhoneGap Build** beginnen, müssen Sie Ihre Cloud-Services mithilfe der Kachel **Cloud Service verwalten** im AEM Mobile-Dashboard konfigurieren.

Gehen Sie wie folgt vor, um Cloud-Services für Ihre App zu konfigurieren:

1. Klicken Sie oben rechts auf der Kachel **Cloud Service verwalten** .

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Wählen Sie die Option **PhoneGap Build** im Bildschirm **Cloud Service hinzufügen oder bearbeiten** aus.

   Klicken Sie auf **Weiter**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Geben Sie Ihre Anmeldedaten ein, damit Sie eine Cloud-Konfiguration erstellen können.

   Klicken Sie nach der Überprüfung auf **Senden**. Diese konfigurierte Cloud-Konfiguration wird jetzt in der Kachel **Cloud Service verwalten** angezeigt.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Erstellen einer Anwendung mit PhoneGap Build {#building-your-application-with-phonegap-build}

Nachdem Sie die Cloud-Services konfiguriert haben, können Sie Ihre Anwendung mit der Kachel **PhoneGap Build** erstellen. Klicken Sie oben rechts auf , damit Sie aus den Optionen **Remote erstellen** oder **Source herunterladen** auswählen können.

![chlimage_1-64](assets/chlimage_1-64.png)

Um einen Remote-Build mit Adobe PhoneGap Build aufzurufen, klicken Sie auf **Remote erstellen**.

>[!NOTE]
>
>Wenn der Build aus irgendeinem Grund fehlschlägt (das rote iOS-Symbol unten zeigt an, dass die Plattform fehlgeschlagen ist), können Sie den Mauszeiger über das Symbol bewegen, um die Fehlermeldung zu erhalten. Alternativ können Sie auf den dreifachen Punkt (&quot;...&quot;) am unteren Rand der Kachel klicken, um direkt zu &quot;`https://build.phonegap.com`&quot;(Sie müssen sich authentifizieren) zu navigieren und Ihren Build direkt zu beobachten und zu verwalten.

### Erstellen Ihrer Anwendung mit PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap bietet eine Befehlszeilenschnittstelle zum lokalen Erstellen Ihrer Anwendung.

Kompilieren Sie die PhoneGap-Anwendung mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI) auf Ihrem Computer. Um den AEM Inhalt in Ihre Anwendung aufzunehmen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer Mobile App, Konfigurationen zur Inhaltssynchronisierung und andere erforderliche Assets enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

Um die CLI von PhoneGap nutzen zu können, müssen Sie Ihre lokale Umgebung so einrichten, dass Folgendes enthalten ist:

1. Platform SDK (iOS, Android™, Windows Phone, ...) und
1. PhoneGap-CLI

Weitere Informationen finden Sie hier unter `https://docs.phonegap.com/references/phonegap-cli/`.

Nachdem Sie die Voraussetzungen installiert haben, testen Sie sie anhand eines einfachen Tests, indem Sie eine einfache App erstellen und sie entweder in Ihrem Simulator oder besser auf Ihrem Gerät ausführen lassen, und zwar von einem Terminal aus:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>Fügen Sie —emulate am Ende dieser Zeile hinzu, wenn Sie sie nicht auf Ihrem verbundenen Gerät ausführen möchten.

Nachdem Sie überprüft haben, ob das oben beschriebene funktioniert, verwenden Sie die Kachel **PhoneGap Build** in **Source herunterladen** . Speichern und entpacken Sie die Datei auf Ihrem lokalen System. Danach:

* Navigieren zu dieser gespeicherten Datei (Ordner)
* Führen Sie &quot;phonegap run ios&quot;aus (oder android usw.)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Autoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
