---
title: Konfigurieren von Adobe Target Cloud Service
seo-title: Konfigurieren von Adobe Target Cloud Service
description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud-Services erstellen, die Anwendung für die Aktivität konfigurieren und schließlich Inhalte generieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud-Services erstellen, die Anwendung für die Aktivität konfigurieren und schließlich Inhalte generieren.
uuid: 569f9c6d-f521-488a-9e51-f43b7a214dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 8cd6480f-cb4f-40dd-a444-8ba463b78604
exl-id: d370d772-ef4d-4f38-826c-e90d07735822
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 2%

---

# Konfigurieren von Adobe Target Cloud Service {#configuring-adobe-target-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Dieses Dokument ist Teil des Leitfadens [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md), eines empfohlenen Ausgangspunkts für die AEM Mobile-Referenz.

Es gibt eine Reihe von Schritten, die durchgeführt werden müssen, bevor Inhaltsautoren mit der Generierung zielgerichteter Inhalte für mobile Apps beginnen können: Es gibt die richtigen Berechtigungen für Benutzer und Gruppen, das Erstellen von Cloud-Services, das Konfigurieren der Anwendung für die Aktivität und schließlich das Generieren des Inhalts.

Es wird davon ausgegangen, dass die [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) erfolgreich bereitgestellt wurde und über das AEM Mobile-Dashboard zugänglich ist.

## Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen der Gruppe `target-activity-authors` angehören. Es wird empfohlen, dass die target-activity-group im Rahmen der Benutzer- und Gruppeneinrichtung zur Gruppe apps-admins hinzugefügt wird. Durch Hinzufügen der Gruppe target-activity-authors können Benutzer den Menüeintrag Personalisierung-Navigation sehen.

Wenn Sie vergessen, der Gruppe target-activity-authors Benutzer oder Gruppen hinzuzufügen, die Zugriff auf die Personalisierungs-Admin Console haben möchten, wird Benutzern die Personalisierungskonsole nicht angezeigt.

## Cloud Services {#cloud-services}

Damit zielgerichtete Inhalte für mobile Anwendungen funktionieren, müssen zwei Dienste konfiguriert werden: Der Adobe Target-Dienst und der Adobe Mobile Services-Dienst. Der Adobe Target-Dienst stellt die Engine für die Verarbeitung von Client-Anforderungen und die Rückgabe personalisierter Inhalte bereit. Der Adobe Mobile Services-Dienst stellt die Verbindung zwischen den Adobe Services und der Mobile App über die Datei ADBMobileConfig.json her, die vom AMS Cordova-Plug-in genutzt wird. Im AEM Mobile Dashboard können Sie Ihre Anwendung konfigurieren, indem Sie die beiden Dienste hinzufügen.

## Adobe Target Cloud Service {#adobe-target-cloud-service}

Suchen Sie im AEM Mobile Dashboard die Schaltfläche Cloud Services verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-8](assets/chlimage_1-8.png)

Wählen Sie im Assistenten Cloud Service hinzufügen die Cloud Service-Karte &quot;Adobe Target&quot;aus und klicken Sie auf Weiter.

![chlimage_1-9](assets/chlimage_1-9.png)

Im Dropdown-Menü Konfiguration auswählen können Sie entweder eine neue Konfiguration erstellen oder eine vorhandene auswählen. Um eine neue Konfiguration zu erstellen, wählen Sie &quot;Konfiguration erstellen&quot;aus dem Dropdown-Menü aus. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche &quot;Überprüfen&quot;, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche Senden , um den Cloud-Dienst zu erstellen.

Der erstellte Cloud-Dienst wird über den Assistenten automatisch mit der Mobile App verknüpft. Der Eigenschaftswert cq:cloudserviceconfigs wird im Knoten jcr:content des Anwendungsgruppenknotens festgelegt. Für das Hybrid-App-Beispiel wird es unter /content/mobileapps/hybrid-reference-app/jcr:content festgelegt, wobei der Wert auf den automatisch generierten Framework-Knoten unter /etc/cloudservices/testandtarget/adobe-target—aem-apps/framework verweist. Der Framework-Knoten verfügt über zwei standardmäßig festgelegte Eigenschaften: Geschlecht und Alter. Das Framework wird nur von AEM Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel Cloud Service verwalten den Target-Cloud-Service, enthält jedoch eine Warnung zu einem fehlenden Adobe Mobile Service-Konto.

![chlimage_1-10](assets/chlimage_1-10.png)

## Adobe Mobile Service {#adobe-mobile-service}

Es ist erforderlich, auch ein Adobe Mobile Services (AMS)-Konto mit der Anwendung zu verknüpfen. Der AMS-Dienst stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Clientcode-Informationen enthält. Bevor Sie eine Verknüpfung mit dem AMS-Konto erstellen, muss das AMS-Konto von einem Benutzer geändert werden, der über Berechtigungen für AMS verfügt.

### Clientcode {#client-code}

Um sich bei den AMS-Diensten anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die Mobile App aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK-Target-Optionen , platzieren Sie den Client-Code in das Feld und klicken Sie auf Speichern .

![chlimage_1-11](assets/chlimage_1-11.png)

Nachdem der Clientcode mit der Mobile App verknüpft wurde, werden die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Service über das Adobe Mobile Dashboard konfiguriert wird.

### Adobe Mobile Service Cloud Service {#adobe-mobile-service-could-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die Mobile App im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile Dashboard die Schaltfläche Cloud Services verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-12](assets/chlimage_1-12.png)

Wählen Sie die Adobe Mobile Services -Karte aus und klicken Sie auf Weiter.

![chlimage_1-13](assets/chlimage_1-13.png)

Wählen Sie im Schritt Erstellen oder Auswählen des Assistenten die Dropdown-Liste Mobile Service und danach den Eintrag Konfiguration erstellen aus. Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Nachdem alle Felder ausgefüllt wurden, klicken Sie auf die Schaltfläche Überprüfen . Der Überprüfungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Nach erfolgreicher Überprüfung wird eine Liste mit Mobile Apps gefüllt, in der Sie die zugehörige Mobile App aus der Dropdown-Liste auswählen. Klicken Sie auf die Schaltfläche Senden , um den Assistenten abzuschließen. Der Prozess kann ein wenig Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle damit verbundenen Analysen mit der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs im Modal auf die Schaltfläche Fertig , um zum Adobe Mobile Dashboard zurückzukehren.

Kehren Sie zum Mobile Dashboard zurück und die Kachel Cloud Services verwalten enthält den AMS-Cloud-Service. Sie werden auch feststellen, dass die Kachel Metriken analysieren mit Lebenszyklusberichten gefüllt wird.

![chlimage_1-14](assets/chlimage_1-14.png)

## Handler zur Inhaltssynchronisierung in Target {#target-content-sync-handlers}

Um Inhalte für den Geräteinhalt des Benutzers bereitzustellen, werden durch Rendern der Angebote generiert, die von AEM Inhaltsautoren erstellt werden. Um das Rendering von Target-Angeboten zu verarbeiten, gibt es einen neuen Content Sync Handler, der die Angebote verarbeitet. Unter Verwendung der Hybrid-Referenzanwendung als Beispiel enthält das Inhaltspaket en (Englisch) die ContentSyncConfig mit einem [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) -Handler. Der nächste Schritt ist entscheidend für das Rendern von Angeboten an das Gerät. Der Handler mobileappoffers verfügt über eine Pfadeigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet werden soll.

Wenn sich beispielsweise eine Aktivität unter */content/campaigns/hybridref* befindet, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die Eigenschaft *path* des Handlers mobileappoffers ein.

Für die Hybrid-Referenzanwendung gibt es zwei Handler für Mobile Apps, einen für die Entwicklung und einen für Produktionen.

Nachdem der Aktivitätspfad in der Pfadeigenschaft des Handlers mobileappoffers festgelegt wurde, speichern Sie den Handler. Der Handler ist nun bereit, Angebote für unsere Mobilgeräte zu rendern.

### Render Mode {#render-mode}

Der Handler für mobileappoffers ist für Veröffentlichungs- und Entwicklungskonfigurationen anders konfiguriert. Für Veröffentlichungskonfigurationen gibt es eine Eigenschaft mit dem Namen *renderMode* mit dem Wert *publish*, die auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der Handler mobileappoffer verweist auf den renderMode und ändert, falls auf &quot;publish&quot;festgelegt, die zu erstellende Mbox-ID. Standardmäßig werden bei Mboxes, die von AEM erstellt werden, an die Mbox-ID der Wert —author angehängt. Dadurch wird festgestellt, dass die Aktivität noch nicht veröffentlicht wurde, und die nicht veröffentlichte Kampagne sollte für Angebotsauflösungen verwendet werden.

Wenn Inhalte über das Adobe Mobile Dashboard gestaffelt werden, werden Staging-Inhalte als produktionsbereite Inhalte betrachtet und über die Konfiguration der Inhaltssynchronisierung ohne Entwicklungsumgebung gerendert. Auf diese Weise wird der —author aus allen Mbox-IDs entfernt und es wird erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Bevor Sie gestaffelte Inhalte testen, stellen Sie sicher, dass die Aktivität veröffentlicht wurde.

## Erstellen von Inhalten {#creating-content}

Nachdem die Cloud-Services erstellt und der Handler für mobile Apps konfiguriert wurde, können Inhaltsautoren nun mit der Generierung zielgerichteter Erlebnisse beginnen.
