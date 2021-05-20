---
title: 'Konfigurieren des Adobe PhoneGap Build-Cloud-Service '
seo-title: 'Konfigurieren des Adobe PhoneGap Build-Cloud-Service '
description: Auf dieser Seite finden Sie Informationen zum Konfigurieren der Cloud-Services und zum Erstellen Ihrer Anwendung mit PhoneGap-Build.
seo-description: Auf dieser Seite finden Sie Informationen zum Konfigurieren der Cloud-Services und zum Erstellen Ihrer Anwendung mit PhoneGap-Build.
uuid: 59aa99c3-1425-4cc5-9839-a57a6a545d45
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 3c84f4ec-d89b-4ad4-802e-ee3e2d49d916
exl-id: d91a00d1-12fa-4c84-a426-49413f61c126
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 19%

---

# Konfigurieren des Adobe PhoneGap Build-Cloud-Service{#configure-your-adobe-phonegap-build-cloud-service} 

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Der Bereich **PhoneGap Build** im Anwendungs-Dashboard bietet die Möglichkeit, Ihre PhoneGap-Mobile App über den Adobe PhoneGap Build-Dienst zu erstellen und zu verteilen.

Alle unterstützten Plattformen, die in der Kachel **App verwalten** definiert sind, werden beim Pushen eines Remote-Builds mit der Kachel **PhoneGap Build** mit PhoneGap Build erstellt.

Sie können einen Remote-Build an [https://build.phonegap.com](https://build.phonegap.com) pushen oder die Quelle herunterladen, um sie lokal mit [PhoneGap CLI](https://docs.phonegap.com/references/phonegap-cli/) zu erstellen.

![Bereich „PhoneGap-Build“](assets/chlimage_1-60.png)

## Konfigurieren des Cloud-Dienstes {#configuring-the-cloud-service}

Um PhoneGap Build nutzen zu können, müssen Sie den AEM PhoneGap Build-Cloud-Service mit den Kontoinformationen für PhoneGap Build konfigurieren.

Wenn Sie derzeit kein Konto haben, navigieren Sie zu [https://build.phonegap.com](https://build.phonegap.com) und melden Sie sich an! Wenn Sie über eine Adobe Creative Cloud-Mitgliedschaft verfügen, können Sie bis zu 25 private Apps (Nicht-Open-Source-Apps) unterstützen.

Nachdem Sie überprüft haben, ob Ihr PhoneGap Build-Konto aktiv ist, navigieren Sie zu Ihrer AEM Cloud Management Console, insbesondere zum [PhoneGap Build](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Verwenden Sie die Kachel **Cloud Services verwalten** , um eine neue Cloud Service-Konfiguration zu konfigurieren.

### Verwenden der Kachel Cloud Services verwalten {#using-manage-cloud-services-tile}

Bevor Sie mit der Erstellung Ihrer App mithilfe der Kachel **PhoneGap Build** beginnen, müssen Sie Ihre Cloud-Services mithilfe der Kachel **Cloud Services verwalten** im AEM Mobile-Dashboard konfigurieren.

Gehen Sie wie folgt vor, um Cloud-Services für Ihre App zu konfigurieren:

1. Klicken Sie oben rechts in der Kachel **Cloud Services verwalten** .

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Wählen Sie die Option **PhoneGap Build** im Bildschirm **Cloud Service hinzufügen oder bearbeiten** aus.

   Klicken Sie auf **Weiter**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Geben Sie Ihre Anmeldedaten ein, um eine neue Cloud-Konfiguration zu erstellen.

   Klicken Sie nach der Überprüfung auf **Submit**. Diese konfigurierte Cloud-Konfiguration wird jetzt in der Kachel **Cloud Services verwalten** angezeigt.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Erstellen einer App mit PhoneGap Build {#building-your-application-with-phonegap-build}

Nachdem Sie die Cloud-Services konfiguriert haben, können Sie Ihre Anwendung mit der Kachel **PhoneGap Build** erstellen. Klicken Sie in der oberen rechten Ecke auf die Option **Remote erstellen** oder **Quelle herunterladen** .

![chlimage_1-64](assets/chlimage_1-64.png)

Um einen Remote-Build mit Adobe PhoneGap Build aufzurufen, klicken Sie auf **Build Remote**.

>[!NOTE]
>
>Wenn die Erstellung des Builds aus irgendeinem Grund fehlschlägt (das rote iOS-Symbol unten zeigt einen Fehler für diese Plattform an), können Sie den Mauszeiger über das Symbol bewegen, um die Fehlermeldung anzuzeigen. Alternativ können Sie auf den dreifachen Punkt &#39;...&#39; klicken unten in der Kachel, um direkt zu https://build.phonegap.com zu navigieren (Sie müssen sich authentifizieren) und Ihren Build direkt zu beobachten und zu verwalten.

### Erstellen Ihrer Anwendung mit PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap bietet eine Befehlszeilenschnittstelle zum lokalen Erstellen Ihrer Anwendung.

Kompilieren Sie die PhoneGap-Anwendung mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI) auf Ihrem Computer. Um den AEM Inhalt in Ihre Anwendung aufzunehmen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer Mobile App, Konfigurationen zur Inhaltssynchronisierung und andere erforderliche Assets enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

Um die Befehlszeilenschnittstelle von PhoneGap nutzen zu können, müssen Sie Ihre lokale Umgebung so einrichten, dass Folgendes enthalten ist:

1. Plattform-SDK (iOS, Android, WindowsPhone usw.)
1. PhoneGap-CLI

Sie können mehr [hier](https://docs.phonegap.com/references/phonegap-cli/) lesen.

Nachdem Sie die Voraussetzungen installiert haben, testen Sie sie anhand eines einfachen Tests, indem Sie eine einfache App erstellen und sie entweder in Ihrem Simulator oder besser auf Ihrem Gerät ausführen lassen, und zwar von einem Terminal aus:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>Fügen Sie am Ende dieser Zeile —emulate hinzu, wenn Sie sie nicht auf Ihrem verbundenen Gerät ausführen möchten.

Nachdem Sie überprüft haben, ob das oben beschriebene funktioniert, verwenden Sie die Kachel **PhoneGap Build** in **Download-Quelle**. Speichern und entzippen Sie die Datei auf Ihr lokales System. Danach:

* Navigieren zu dieser gespeicherten Datei (Ordner)
* Führen Sie &#39;phonegap run ios&#39; aus (oder android usw.)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Autoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
