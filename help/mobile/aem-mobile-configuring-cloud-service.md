---
title: Konfigurieren von Adobe Target Cloud Service
description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud-Services erstellen, die Anwendung für die Aktivität konfigurieren und schließlich Inhalte generieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: d370d772-ef4d-4f38-826c-e90d07735822
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 1%

---

# Konfigurieren von Adobe Target Cloud Service {#configuring-adobe-target-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Dieses Dokument ist Teil der [Erste Schritte mit Adobe Experience Manager (AEM) Mobile](/help/mobile/getting-started-aem-mobile.md) Guide, ein empfohlener Ausgangspunkt für die AEM Mobile-Referenz.

Es gibt mehrere Schritte, die zusammenkommen müssen, bevor Inhaltsautoren beginnen können, zielgerichtete Inhalte für mobile Apps zu generieren: Es gibt die richtigen Berechtigungen für Benutzer und Gruppen, das Erstellen von Cloud-Services, das Konfigurieren der Anwendung für die Aktivität und das Generieren des Inhalts.

Die Annahme, dass die [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) wurde erfolgreich bereitgestellt und kann über das AEM Mobile-Dashboard aufgerufen werden.

## Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen `target-activity-authors` hinzugefügt. Es wird empfohlen, dass die target-activity-group im Rahmen der Benutzer- und Gruppeneinrichtung zur Gruppe apps-admins hinzugefügt wird. Durch Hinzufügen der Gruppe target-activity-authors können Benutzer den Menüeintrag Personalisierung-Navigation sehen.

Wenn Sie vergessen, die Benutzer oder Gruppen, die Sie auf die Personalisierungskonsole zugreifen möchten, zur Gruppe target-activity-authors hinzuzufügen, wird verhindert, dass die Personalisierungskonsole angezeigt wird.

## Cloud Services {#cloud-services}

Damit zielgerichtete Inhalte für mobile Anwendungen funktionieren, müssen zwei Dienste konfiguriert werden: der Adobe Target-Dienst und der Adobe Mobile Services-Dienst. Der Adobe Target-Dienst stellt die Engine für die Verarbeitung von Client-Anforderungen und die Rückgabe personalisierter Inhalte bereit. Der Adobe Mobile Services-Dienst stellt die Verbindung zwischen den Adobe-Diensten und der Mobile App über die Datei ADBMobileConfig.json her, die vom AMS-Cordova-Plug-in genutzt wird. Im AEM Mobile Dashboard können Sie Ihre Anwendung konfigurieren, indem Sie die beiden Dienste hinzufügen.

## Adobe Target Cloud Service {#adobe-target-cloud-service}

Suchen Sie im AEM Mobile Dashboard die Schaltfläche Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-8](assets/chlimage_1-8.png)

Wählen Sie im Assistenten Cloud Service hinzufügen die Cloud Service-Karte &quot;Adobe Target&quot;aus und klicken Sie auf Weiter.

![chlimage_1-9](assets/chlimage_1-9.png)

In der Dropdown-Liste Konfiguration auswählen können Sie entweder eine Konfiguration erstellen oder eine vorhandene auswählen. Um eine Konfiguration zu erstellen, wählen Sie &quot;Konfiguration erstellen&quot;aus dem Dropdown-Menü aus. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche &quot;Überprüfen&quot;, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche Senden , um den Cloud-Dienst zu erstellen.

Der erstellte Cloud-Dienst wird über den Assistenten automatisch mit der Mobile App verknüpft. Der Eigenschaftswert cq:cloudserviceconfigs wird im Knoten jcr:content des Anwendungsgruppenknotens festgelegt. Für das Hybrid-App-Beispiel wird es unter /content/mobileapps/hybrid-reference-app/jcr:content festgelegt, wobei der Wert, der auf den automatisch generierten Framework-Knoten verweist, unter /etc/cloudservices/testandtarget/adobe-target—aem-apps/framework steht. Der Framework-Knoten verfügt über zwei standardmäßig festgelegte Eigenschaften: Geschlecht und Alter. Das Framework wird nur von AEM Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel Cloud Service verwalten den Target-Cloud-Service, enthält jedoch eine Warnung zu einem fehlenden Adobe Mobile Service-Konto.

![chlimage_1-10](assets/chlimage_1-10.png)

## Adobe Mobile Service {#adobe-mobile-service}

Es ist erforderlich, auch ein Adobe Mobile Services (AMS)-Konto mit der Anwendung zu verknüpfen. Der AMS-Dienst stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Clientcode-Informationen enthält. Bevor Sie eine Verknüpfung mit dem AMS-Konto erstellen, muss das AMS-Konto von einem Benutzer geändert werden, der über Berechtigungen für AMS verfügt.

### Client-Code {#client-code}

Um sich bei AMS-Diensten anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die Mobile App aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK-Target-Optionen , platzieren Sie den Client-Code in das Feld und klicken Sie auf Speichern .

![chlimage_1-11](assets/chlimage_1-11.png)

Nachdem der Clientcode mit der Mobile App verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Service über das Adobe Mobile Dashboard konfiguriert wird.

### Adobe Mobile Service Cloud Service {#adobe-mobile-service-could-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die Mobile App im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile Dashboard die Schaltfläche Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-12](assets/chlimage_1-12.png)

Wählen Sie die Adobe Mobile Services -Karte aus und klicken Sie auf Weiter.

![chlimage_1-13](assets/chlimage_1-13.png)

Wählen Sie im Schritt Erstellen oder Auswählen des Assistenten die Dropdown-Liste Mobile Service aus und wählen Sie den Eintrag Konfiguration erstellen . Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Nachdem alle Felder ausgefüllt sind, klicken Sie auf **Überprüfen**. Der Überprüfungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Nach erfolgreicher Überprüfung wird eine Liste mit Mobile Apps gefüllt, in der Sie die zugehörige Mobile App aus der Dropdown-Liste auswählen. Klicken Sie auf die Schaltfläche Senden , um den Assistenten abzuschließen. Der Prozess kann ein wenig Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle damit verbundenen Analysen mit der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs auf **Fertig** aus dem Modal zurück, um zum Adobe Mobile Dashboard zurückzukehren.

Kehren Sie zum Mobile Dashboard zurück und die Kachel Cloud Service verwalten enthält den AMS-Cloud-Service. Außerdem wird die Kachel Metriken analysieren mit Lebenszyklusberichten gefüllt.

![chlimage_1-14](assets/chlimage_1-14.png)

## Handler zur Inhaltssynchronisierung in Target {#target-content-sync-handlers}

Um Inhalte auf dem Gerät des Benutzers bereitzustellen, werden Inhalte durch Rendering der Angebote generiert, die von AEM Inhaltsautoren erstellt werden. Um das Rendering von Target-Angeboten zu verarbeiten, gibt es einen neuen Content Sync-Handler, der die Angebote verarbeitet. Unter Verwendung der Hybrid-Referenzanwendung als Beispiel enthält das Inhaltspaket en (Englisch) die ContentSyncConfig mit einer [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) Handler. Der nächste Schritt ist entscheidend für das Rendern von Angeboten an das Gerät. Der Handler mobileappoffers verfügt über eine Pfadeigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet wird.

Wenn beispielsweise eine Aktivität unter */content/campaigns/hybridref*, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in den *path* -Eigenschaft des Handlers mobileappoffers .

Für die Hybrid-Referenzanwendung gibt es zwei Handler für Mobile Apps, einen für die Entwicklungsumgebung und einen für Produktionen.

Nachdem der Aktivitätspfad in der Pfadeigenschaft des Handlers mobileappoffers festgelegt wurde, speichern Sie den Handler. Der Handler ist jetzt bereit, Angebote für Mobilgeräte zu rendern.

### Rendermodus {#render-mode}

Der Handler für mobileappoffers ist für Veröffentlichungs- und Entwicklungskonfigurationen anders konfiguriert. Für Veröffentlichungskonfigurationen gibt es eine Eigenschaft mit dem Namen *renderMode* mit dem Wert *publish* auf den Knoten cq:ContentSyncConfig eingestellt ist. Der Handler mobileappoffer verweist auf den renderMode und bearbeitet, falls auf &quot;publish&quot;festgelegt, die zu erstellende Mbox-ID. Standardmäßig werden bei Mboxes, die von AEM erstellt werden, an die Mbox-ID der Wert —author angehängt. Dadurch wird festgestellt, dass die Aktivität noch nicht veröffentlicht wurde, und die nicht veröffentlichte Kampagne sollte für Angebotsauflösungen verwendet werden.

Wenn Inhalte über das Adobe Mobile Dashboard gestaffelt werden, werden Staging-Inhalte als produktionsbereite Inhalte betrachtet und über die Konfiguration für die Inhaltssynchronisierung ohne Entwicklungsumgebung gerendert. Auf diese Weise wird —author aus allen Mbox-IDs entfernt und es wird erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Bevor Sie gestaffelte Inhalte testen, stellen Sie sicher, dass die Aktivität veröffentlicht ist.

## Erstellen von Inhalten {#creating-content}

Nachdem die Cloud-Services erstellt und der Handler für mobile Apps konfiguriert wurde, können Inhaltsautoren nun mit der Generierung zielgerichteter Erlebnisse beginnen.
