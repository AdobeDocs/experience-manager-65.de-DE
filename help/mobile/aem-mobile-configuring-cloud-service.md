---
title: Konfigurieren von Adobe Target Cloud Service
description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud Services erstellen, die Anwendung für die Aktivität konfigurieren und schließlich den Inhalt generieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: d370d772-ef4d-4f38-826c-e90d07735822
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 3%

---

# Konfigurieren von Adobe Target Cloud Service {#configuring-adobe-target-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Dieses Dokument ist Teil des Handbuchs [Erste Schritte mit Adobe Experience Manager (AEM) Mobile](/help/mobile/getting-started-aem-mobile.md), ein empfohlener Ausgangspunkt für die AEM Mobile-Referenz.

Es gibt mehrere Schritte, die zusammengeführt werden müssen, bevor Inhaltsautorinnen und -autoren mit der Generierung zielgerichteter Inhalte für mobile Apps beginnen können: Es gibt den richtigen Berechtigungssatz für Benutzende und Gruppen, die Erstellung von Cloud-Services, die Konfiguration der Anwendung für die Aktivität und schließlich die Erstellung des Inhalts.

Es wird davon ausgegangen, dass die [AEM Mobile Hybrid Reference Application](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) erfolgreich bereitgestellt wurde und über das AEM Mobile Dashboard zugänglich ist.

## Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen Teil der `target-activity-authors` sein. Es wird empfohlen, die target-activity-group im Rahmen der Benutzer- und Gruppeneinrichtung der Gruppe apps-admins hinzuzufügen. Durch Hinzufügen der Gruppe target-activity-authors können Benutzerinnen und Benutzer den Menüeintrag Personalization-Navigation sehen.

Wenn Sie vergessen haben, die Benutzenden oder Gruppen, auf die Sie Zugriff haben möchten, zur Admin Console target-activity-authors hinzuzufügen, wird verhindert, dass Benutzende die Personalisierungskonsole sehen.

## Cloud Services {#cloud-services}

Damit zielgerichtete Inhalte für Mobile Apps funktionieren, müssen zwei Services konfiguriert werden: der Adobe Target-Service und der Adobe Mobile Services-Service. Der Adobe Target-Service stellt die Engine zum Verarbeiten von Client-Anfragen und Zurückgeben der personalisierten Inhalte bereit. Der Service Adobe Mobile Services stellt die Verbindung zwischen den Adobe-Services und der Mobile App über die Datei ADBMobileConfig.json her, die vom AMS Cordova-Plug-in genutzt wird. Über das AEM Mobile-Dashboard können Sie Ihr Programm konfigurieren, indem Sie die beiden Services hinzufügen.

## Adobe Target Cloud Service {#adobe-target-cloud-service}

Suchen Sie im AEM Mobile-Dashboard nach der Option Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-8](assets/chlimage_1-8.png)

Wählen Sie im Assistenten &quot;Cloud Service hinzufügen“ die Cloud Service-Karte &quot;Adobe Target&quot; aus und klicken Sie auf Weiter.

![chlimage_1-9](assets/chlimage_1-9.png)

In der Dropdown-Liste Konfiguration auswählen können Sie entweder eine Konfiguration erstellen oder aus einer vorhandenen auswählen. Um eine Konfiguration zu erstellen, wählen Sie aus dem Dropdown-Menü „Konfiguration erstellen“ aus. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie den Clientcode, die E-Mail-Adresse und das Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche „Überprüfen“, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche Senden , um den Cloud-Service zu erstellen.

Der erstellte Cloud-Service wird über den Assistenten automatisch mit der Mobile App verknüpft. Der Wert der Eigenschaft cq:cloudserviceconfigs wird auf dem Knoten jcr:content des Gruppenknotens apps festgelegt. Für das Beispiel der Hybrid-App wird unter /content/mobileapps/hybrid-reference-app/jcr:content festgelegt, wobei der Wert, der auf den automatisch generierten Framework-Knoten verweist, unter /etc/cloudservices/testandtarget/adobe-target—aem-apps/framework zu finden ist. Für den Framework-Knoten sind standardmäßig zwei Eigenschaften festgelegt: Geschlecht und Alter. Das Framework wird nur von der AEM-Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel Cloud Service verwalten den Target-Cloud-Service, jedoch eine Warnung zu einem fehlenden Adobe Mobile Service-Konto.

![chlimage_1-10](assets/chlimage_1-10.png)

## Adobe Mobile Service {#adobe-mobile-service}

Es ist auch erforderlich, ein Adobe Mobile Services (AMS)-Konto mit der Anwendung zu verknüpfen. Der AMS-Service stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Client-Code-Informationen enthält. Bevor Sie eine Verknüpfung mit dem AMS-Konto erstellen, muss das AMS-Konto von einem Benutzer geändert werden, der über Berechtigungen für AMS verfügt.

### Client-Code {#client-code}

Um sich bei den AMS-Services anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die Mobile App aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK Target-Optionen , platzieren Sie den Client-Code in das Feld und klicken Sie auf Speichern .

![chlimage_1-11](assets/chlimage_1-11.png)

Nachdem der Client-Code mit der Mobile App verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Service über das Dashboard für mobile Adobe-Geräte konfiguriert ist.

### Adobe Mobile Service konnte Dienste bereitstellen {#adobe-mobile-service-could-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die Mobile App im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile-Dashboard nach der Option Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-12](assets/chlimage_1-12.png)

Wählen Sie die Karte Adobe Mobile Services aus und klicken Sie auf Weiter.

![chlimage_1-13](assets/chlimage_1-13.png)

Wählen Sie im Schritt Erstellen oder Assistenten auswählen die Dropdown-Liste Mobile Service und dann den Eintrag Konfiguration erstellen aus. Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Nachdem alle Felder ausgefüllt wurden, klicken Sie auf **Überprüfen**. Der Verifizierungsprozess geht an AMS und überprüft die Anmeldeinformationen für das Konto. Nach erfolgreicher Validierung wird eine Liste der Mobile Apps ausgefüllt, in der Sie die zugehörige Mobile App aus der Dropdown-Liste auswählen. Klicken Sie auf Senden , um den Assistenten abzuschließen. Der Vorgang kann einige Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle zugehörigen Analysen der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs im Modal auf **Fertig**, um zum Dashboard für mobile Adobe-Geräte zurückzukehren.

Zurück zum mobilen Dashboard enthält die Kachel Cloud Service verwalten den AMS-Cloud-Service. Außerdem wird die Kachel Metriken analysieren mit Lebenszyklusberichten gefüllt.

![chlimage_1-14](assets/chlimage_1-14.png)

## Target Content Sync Handler {#target-content-sync-handlers}

Um Inhalte auf dem Gerät des Benutzers bereitzustellen, werden Inhalte durch das Rendern von Angeboten generiert, die von AEM-Inhaltsautoren erstellt wurden. Für das Rendering von Target-Angeboten gibt es einen neuen Inhaltssynchronisierungs-Handler, der die Angebote verarbeitet. Unter Verwendung der Hybrid-Referenzanwendung als Beispiel enthält das Inhaltspaket en (Englisch) den ContentSyncConfig mit einem [mobileAppOffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml)-Handler. Der nächste Schritt ist wichtig, um Angebote auf dem Gerät zu rendern. Der mobileAppOffers-Handler verfügt über eine path-Eigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet wird.

Wenn beispielsweise eine Aktivität unter */content/campaigns/hybridref* vorhanden ist, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die Eigenschaft *path* des MobileAppOffers-Handlers ein.

Für die Hybrid-Referenzanwendung gibt es zwei mobile App-Handler, einen für die Entwicklung und einen für Produktionen.

Nachdem der Aktivitätspfad in der Path-Eigenschaft des MobileAppOffers-Handlers festgelegt wurde, speichern Sie den Handler. Der Handler ist jetzt bereit, um mit dem Rendern von Angeboten für Mobilgeräte zu beginnen.

### Render-Modus {#render-mode}

Der MobileAppOffers-Handler ist für Veröffentlichungs- und Entwicklungs-Setups unterschiedlich konfiguriert. Bei Veröffentlichungseinstellungen gibt es eine Eigenschaft mit dem Namen *renderMode* mit dem Wert *publish*, der auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der mobileAppOffers-Handler verweist auf den renderMode und bearbeitet, wenn er auf publish festgelegt ist, die erstellte mbox id. Standardmäßig wird bei Mboxes, die von AEM erstellt werden, ein —author-Wert an die mbox-ID angehängt. Dadurch wird erkannt, dass die Aktivität nicht veröffentlicht wurde und die nicht veröffentlichte Kampagne zur Angebotsauflösung verwenden sollte.

Wenn Inhalte über das Dashboard für mobile Adobe-Geräte bereitgestellt werden, werden bereitgestellte Inhalte als produktionsbereite Inhalte betrachtet und über die Konfiguration der Inhaltssynchronisierung ohne Entwicklung gerendert. Durch dieses Rendering wird —author aus allen mbox-IDs entfernt und erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Stellen Sie vor dem Testen von Staging-Inhalten sicher, dass die Aktivität veröffentlicht wurde.

## Erstellen von Inhalten {#creating-content}

Nachdem die Cloud-Services erstellt und der MobileAppOffers-Handler konfiguriert wurde, können Inhaltsautorinnen und -autoren jetzt mit der Generierung zielgerichteter Erlebnisse beginnen.
