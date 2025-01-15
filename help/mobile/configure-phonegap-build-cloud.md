---
title: Konfigurieren des Adobe PhoneGap Build-Cloud Service
description: Auf dieser Seite finden Sie Informationen zum Konfigurieren der Cloud Services und zum Erstellen Ihres Programms mit PhoneGap Build.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: d91a00d1-12fa-4c84-a426-49413f61c126
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---

# Konfigurieren des Adobe PhoneGap Build-Cloud Service {#configure-your-adobe-phonegap-build-cloud-service}

{{ue-over-mobile}}

Mit der **PhoneGap Build-Kachel** im Anwendungs-Dashboard können Sie Ihre PhoneGap-Mobile-App über den Adobe PhoneGap Build-Service erstellen und verteilen.

Alle unterstützten Plattformen, die in der Kachel **Programm verwalten** definiert sind, werden mit PhoneGap Build erstellt, wenn ein Remote-Build mit der Kachel **PhoneGap Build}** wird.

Sie können einen Remote-Build per Push `https://build.phonegap.com` oder die Quelle herunterladen, um mit PhoneGap CLI unter `https://docs.phonegap.com/references/phonegap-cli/` lokal zu erstellen.

![PhoneGap Build-Kachel](assets/chlimage_1-60.png)

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um die Vorteile von PhoneGap Build nutzen zu können, müssen Sie den AEM-PhoneGap Build-Cloud Service mit Ihren PhoneGap Build-Kontoinformationen konfigurieren.

Wenn Sie derzeit noch kein Konto haben, navigieren Sie zu `https://build.phonegap.com` und melden Sie sich an! Wenn Sie Adobe Creative Cloud-Mitglied sind, unterstützen Sie möglicherweise bis zu 25 private Apps (Nicht-Open-Source-Apps).

Nachdem Sie sich vergewissert haben, dass Ihr PhoneGap Build-Konto aktiv ist, navigieren Sie zu Ihrer AEM Cloud Management Console, insbesondere zum [PhoneGap Build Cloud Service ](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Verwenden Sie die Kachel **Cloud Service verwalten**, um eine neue Cloud Service-Konfiguration zu konfigurieren.

### Verwenden der Kachel Cloud Service verwalten {#using-manage-cloud-services-tile}

Bevor Sie mit der Erstellung Ihrer App mit der Kachel **PhoneGap Build** beginnen, müssen Sie Ihre Cloud-Services mithilfe der Kachel **Cloud Service verwalten** im AEM Mobile-Dashboard konfigurieren.

Gehen Sie wie folgt vor, um Cloud Services für Ihre App zu konfigurieren:

1. Klicken Sie oben rechts auf der Kachel **Cloud Service verwalten**.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. PhoneGap Build Wählen Sie **** Option auf dem Bildschirm **Cloud Service hinzufügen oder bearbeiten**.

   Klicken Sie auf **Weiter**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Geben Sie Ihre Anmeldedaten ein, damit Sie eine Cloud-Konfiguration erstellen können.

   Klicken Sie nach der Überprüfung auf **Senden**. Diese konfigurierte Cloud-Konfiguration wird jetzt in der Kachel **Cloud Service verwalten** angezeigt.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Erstellen einer Anwendung mit PhoneGap Build {#building-your-application-with-phonegap-build}

Nachdem Sie die Cloud-Services konfiguriert haben, können Sie Ihre Anwendung mit der Kachel **PhoneGap Build** erstellen. Klicken Sie auf die rechte obere Ecke, um zwischen den Optionen **Remote erstellen** oder **Source herunterladen** zu wählen.

![chlimage_1-64](assets/chlimage_1-64.png)

Um einen Remote-Build mit Adobe PhoneGap Build aufzurufen, klicken Sie auf **Remote erstellen**.

>[!NOTE]
>
>Wenn der Build aus irgendeinem Grund fehlschlägt (das rote iOS-Symbol unten zeigt an, dass Platform fehlgeschlagen ist), können Sie den Mauszeiger über das Symbol bewegen, um die Fehlermeldung zu erhalten. Alternativ können Sie auf den dreifachen Punkt, &quot;…“ am unteren Rand der Kachel klicken, um direkt zu `https://build.phonegap.com` zu navigieren (Sie müssen sich authentifizieren) und Ihren Build direkt anzusehen und zu verwalten.

### Erstellen Ihrer Anwendung mit PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap stellt eine Befehlszeilenschnittstelle bereit, um die Anwendung lokal zu erstellen.

Kompilieren Sie die PhoneGap-Anwendung auf Ihrem Computer mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI). Um den AEM-Inhalt in Ihr Programm aufzunehmen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer Mobile App, Inhaltssynchronisierungskonfigurationen und andere erforderliche Assets enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

Um die CLI von PhoneGap nutzen zu können, müssen Sie Ihre lokale Umgebung so einrichten, dass Folgendes enthalten ist:

1. Platform SDK (iOS, Android™, WindowsPhone, …) und
1. PhoneGap CLI

Weitere Informationen finden Sie hier unter `https://docs.phonegap.com/references/phonegap-cli/`.

Sobald Sie die Voraussetzungen installiert haben, testen Sie sie einfach, indem Sie eine einfache App erstellen und sie entweder in Ihrem Simulator oder besser noch auf Ihrem Gerät von einem Terminal aus ausführen:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>Fügen Sie am Ende dieser Zeile —emulate hinzu, wenn Sie sie nicht auf dem verbundenen Gerät ausführen möchten.

PhoneGap Build Nachdem Sie sich vergewissert haben, dass das oben Genannte funktioniert, verwenden Sie die Kachel **** zum **Herunterladen von Source**. Speichern und entpacken Sie die Datei auf Ihrem lokalen System. Sobald dies geschehen ist:

* Navigieren Sie zu dieser gespeicherten Datei (Ordner)
* &#39;PhoneGap Run iOS&#39; (oder Android usw.) ausführen

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Autoren- und Entwicklerinnen bzw. Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
