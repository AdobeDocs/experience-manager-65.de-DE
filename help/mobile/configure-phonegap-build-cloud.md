---
title: 'Konfigurieren des Adobe PhoneGap Build-Cloud-Service '
seo-title: 'Konfigurieren des Adobe PhoneGap Build-Cloud-Service '
description: Folgen Sie dieser Seite, um die Cloud-Dienste zu konfigurieren und Ihre Anwendung mit PhoneGap Build zu erstellen.
seo-description: Folgen Sie dieser Seite, um die Cloud-Dienste zu konfigurieren und Ihre Anwendung mit PhoneGap Build zu erstellen.
uuid: 59aa99c3-1425-4cc5-9839-a57a6a545d45
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 3c84f4ec-d89b-4ad4-802e-ee3e2d49d916
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 19%

---


# Konfigurieren des Adobe PhoneGap Build-Cloud-Service{#configure-your-adobe-phonegap-build-cloud-service} 

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die **PhoneGap Build Kachel** im Dashboard der Anwendung bietet die Möglichkeit, Ihre PhoneGap-Mobilanwendung über den Adobe PhoneGap Build-Dienst zu erstellen und zu verteilen.

Alle unterstützten Plattformen, die in der Kachel **App verwalten** definiert sind, werden mit PhoneGap Build erstellt, wenn ein Remote-Build mit der Kachel **PhoneGap Build** verschoben wird.

Sie können einen Remote-Build an [https://build.phonegap.com](https://build.phonegap.com) verschieben oder die Quelle herunterladen, um lokal mit [PhoneGap CLI](https://docs.phonegap.com/references/phonegap-cli/) zu erstellen.

![Bereich „PhoneGap-Build“](assets/chlimage_1-60.png)

## Konfigurieren des Cloud-Dienstes {#configuring-the-cloud-service}

Um PhoneGap Build nutzen zu können, müssen Sie den AEM PhoneGap Build-Cloud-Service mit den Kontoinformationen für PhoneGap Build konfigurieren.

Wenn Sie derzeit kein Konto haben, navigieren Sie zu [https://build.phonegap.com](https://build.phonegap.com) und melden Sie sich an! Wenn Sie über eine Adobe Creative Cloud-Mitgliedschaft verfügen, können Sie bis zu 25 private Apps (nicht Open-Source-Apps) unterstützen.

Nachdem Sie sich vergewissert haben, dass Ihr PhoneGap Build aktiv ist, navigieren Sie zu Ihrer AEM Cloud Management Console, insbesondere zum [PhoneGap Build](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Verwenden Sie die Kachel **Cloud Services verwalten**, um eine neue Cloud-Dienstkonfiguration zu konfigurieren.

### Cloud Services verwalten: Kachel {#using-manage-cloud-services-tile}

Bevor Sie mit dem Erstellen der App mit der Kachel **PhoneGap Build** beginnen, müssen Sie Ihre Cloud-Dienste mithilfe der Kachel **Cloud Services verwalten** aus dem AEM Mobile-Dashboard konfigurieren.

Gehen Sie wie folgt vor, um Cloud-Dienste für Ihre App zu konfigurieren:

1. Klicken Sie oben rechts in der Kachel **Cloud Services verwalten**.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Wählen Sie die Option **PhoneGap Build** im Bildschirm **Hinzufügen oder Cloud Service bearbeiten**.

   Klicken Sie auf **Weiter**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Geben Sie Ihre Anmeldedaten ein, um eine neue Cloud-Konfiguration zu erstellen.

   Klicken Sie nach der Überprüfung auf **Senden**. Diese konfigurierte Cloud-Konfiguration wird jetzt in der Kachel **Cloud Services verwalten** angezeigt.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Erstellen einer App mit PhoneGap Build {#building-your-application-with-phonegap-build}

Nachdem Sie die Cloud-Dienste konfiguriert haben, können Sie Ihre Anwendung mit der Kachel **PhoneGap Build** erstellen. Klicken Sie oben rechts, um aus den Optionen **Remote erstellen** oder **Quelle herunterladen** auszuwählen.

![chlimage_1-64](assets/chlimage_1-64.png)

Um einen Remote-Build mit Adobe PhoneGap Build aufzurufen, klicken Sie auf **Build Remote**.

>[!NOTE]
>
>Wenn die Erstellung des Builds aus irgendeinem Grund fehlschlägt (das rote iOS-Symbol unten zeigt einen Fehler für diese Plattform an), können Sie den Mauszeiger über das Symbol bewegen, um die Fehlermeldung anzuzeigen. Alternativ können Sie auf den dreifachen Punkt, &#39;...&#39; klicken. am unteren Rand der Kachel, um direkt zu https://build.phonegap.com zu navigieren (Sie müssen sich authentifizieren) und Ihren Build direkt zu überwachen und zu verwalten.

### Erstellen Ihrer Anwendung mit PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap bietet eine Befehlszeilenschnittstelle zum lokalen Aufbau der Anwendung.

Kompilieren Sie die PhoneGap-Anwendung mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI) auf Ihrem Computer. Um den AEM Inhalt in Ihre Anwendung einzubeziehen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer mobilen Anwendung, die Inhaltssynchronisierungskonfigurationen und andere erforderliche Elemente enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

Um die Befehlszeilenschnittstelle von PhoneGap nutzen zu können, müssen Sie Ihre lokale Umgebung wie folgt einrichten:

1. Plattform-SDK (iOS, Android, WindowsPhone usw.)
1. PhoneGap-CLI

Lesen Sie mehr [hier](https://docs.phonegap.com/references/phonegap-cli/).

Nachdem Sie die Voraussetzungen installiert haben, testen Sie sie anhand eines einfachen Tests, indem Sie eine einfache App erstellen und sie entweder im Simulator oder besser noch auf Ihrem Gerät ausführen lassen. Versuchen Sie es über ein Terminal:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>fügen Sie —emulate am Ende dieser Zeile hinzu, wenn Sie sie nicht auf Ihrem angeschlossenen Gerät ausführen möchten.

Nachdem Sie überprüft haben, ob die oben genannten Funktionen funktionieren, verwenden Sie die Kachel **PhoneGap Build** Kachel zu **Download-Quelle**. Speichern und entzippen Sie die Datei auf Ihr lokales System. Danach:

* zu dieser gespeicherten Datei navigieren (Ordner)
* Führen Sie &#39;phonegap run ios&#39; (oder android usw.) aus.

### Zusätzliche Ressourcen {#additional-resources}

Informationen über die Rollen und Zuständigkeiten von Autoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
