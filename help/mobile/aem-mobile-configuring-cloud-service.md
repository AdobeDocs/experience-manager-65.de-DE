---
title: Adobe Target Cloud-Dienst konfigurieren
seo-title: Adobe Target Cloud-Dienst konfigurieren
description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud-Dienste erstellen, die Anwendung für die Aktivität konfigurieren und schließlich Inhalte generieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie die richtigen Berechtigungen für Benutzer und Gruppen erhalten, Cloud-Dienste erstellen, die Anwendung für die Aktivität konfigurieren und schließlich Inhalte generieren.
uuid: 569f9c6d-f521-488a-9e51-f43b7a214dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 8cd6480f-cb4f-40dd-a444-8ba463b78604
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Adobe Target Cloud-Dienst konfigurieren {#configuring-adobe-target-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>This document is part of the [Getting Started with AEM Mobile](/help/mobile/getting-started-aem-mobile.md) Guide, a recommended starting point for AEM Mobile reference.

Es müssen eine Reihe von Schritten durchgeführt werden, bevor Autoren von Inhalten beginnen können, zielgerichtete Inhalte für mobile Apps zu erstellen: Sie erhalten die richtigen Berechtigungen für Benutzer und Gruppen, erstellen Cloud-Dienste, konfigurieren die Anwendung für die Aktivität und generieren den Inhalt schließlich.

Es wird davon ausgegangen, dass die [AEM Mobile-Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) erfolgreich bereitgestellt wurde und über das AEM Mobile-Dashboard zugänglich ist.

## Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen Teil der `target-activity-authors` Gruppe sein. Es wird empfohlen, dass die target-activity-Gruppe im Rahmen der Benutzer- und Gruppeneinrichtung der Gruppe apps-admins hinzugefügt wird. Wenn Sie die Gruppe target-activity-authors hinzufügen, können Benutzer den Eintrag im Navigationsmenü &quot;Personalisierung&quot;sehen.

Wenn Sie vergessen haben, der Gruppe target-activity-authors Benutzer oder Gruppen hinzuzufügen, die Zugriff auf die Personalisierungskonsole haben möchten, wird verhindert, dass Benutzer die Personalisierungskonsole sehen.

## Cloud-Services {#cloud-services}

Damit zielgerichtete Inhalte für mobile Anwendungen verwendet werden können, müssen zwei Dienste konfiguriert werden: Der Adobe Target-Dienst und der Adobe Mobile Services-Dienst. Der Adobe Target-Dienst stellt die Engine für die Verarbeitung von Clientanforderungen und die Rückgabe personalisierter Inhalte bereit. Der Adobe Mobile Services-Dienst stellt die Verbindung zwischen den Adobe-Diensten und der mobilen Anwendung über die Datei ADBMobileConfig.json bereit, die vom AMS-Cordova-Zusatzmodul genutzt wird. Über das AEM Mobile Dashboard können Sie Ihre Anwendung konfigurieren, indem Sie die beiden Dienste hinzufügen.

## Adobe Target Cloud-Dienst {#adobe-target-cloud-service}

Suchen Sie im AEM Mobile Dashboard die Option Cloud-Dienste verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-8](assets/chlimage_1-8.png)

Wählen Sie im Assistenten zum Hinzufügen von Cloud-Diensten die Cloud-Dienstkarte &quot;Adobe Target&quot;und klicken Sie auf Weiter.

![chlimage_1-9](assets/chlimage_1-9.png)

Im Dropdownmenü Konfiguration auswählen können Sie entweder eine neue Konfiguration erstellen oder aus einer vorhandenen auswählen. Um eine neue Konfiguration zu erstellen, wählen Sie &quot;Konfiguration erstellen&quot; aus der Dropdownliste. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche &quot;Überprüfen&quot;, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche &quot;Senden&quot;, um den Cloud-Dienst zu erstellen.

Der Cloud-Dienst, der erstellt wird, wird über den Assistenten automatisch mit der mobilen Anwendung verknüpft. Der Wert der Eigenschaft cq:cloudserviceConfigs wird auf dem Knoten jcr:content des Knoten apps group festgelegt. Für das Hybrid-App-Beispiel wird es unter &quot;/content/mobileapps/hybrid-reference-app/jcr:content&quot;festgelegt. Der Wert verweist auf den automatisch generierten Framework-Knoten unter &quot;/etc/cloudservices/testandtarget/adobe-target—aem-apps/framework&quot;. Der Framework-Knoten verfügt über zwei Eigenschaften, die standardmäßig festgelegt sind: Geschlecht und Alter. Das Framework wird nur von der AEM-Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel &quot;Cloud-Dienst verwalten&quot;den Target-Cloud-Dienst, enthält jedoch eine Warnung über ein fehlendes Adobe Mobile Service-Konto.

![chlimage_1-10](assets/chlimage_1-10.png)

## Adobe Mobile Service {#adobe-mobile-service}

Es ist erforderlich, ein Adobe Mobile Services (AMS)-Konto auch mit der Anwendung zu verknüpfen. Der AMS-Dienst stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Clientcodeinformationen enthält. Vor dem Erstellen einer Verbindung mit dem AMS-Konto muss das AMS-Konto von einem Benutzer geändert werden, der über die Berechtigung für AMS verfügt.

### Client-Code {#client-code}

Um sich bei den AMS-Diensten anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die mobile Anwendung aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK-Target-Optionen, platzieren Sie den Clientcode in das Feld und klicken Sie auf Speichern.

![chlimage_1-11](assets/chlimage_1-11.png)

Nachdem der Clientcode mit der mobilen Anwendung verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Dienst über das Adobe Mobile Dashboard konfiguriert wird.

### Adobe Mobile Service könnte {#adobe-mobile-service-could-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die mobile Anwendung im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile Dashboard die Option Cloud-Dienste verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-12](assets/chlimage_1-12.png)

Wählen Sie die Adobe Mobile Services-Karte und klicken Sie auf Weiter.

![chlimage_1-13](assets/chlimage_1-13.png)

Wählen Sie im Schritt Erstellen oder Auswählen des Assistenten das Dropdown-Menü Mobile Service und wählen Sie den Eintrag Konfiguration erstellen. Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Klicken Sie nach dem Ausfüllen aller Felder auf die Schaltfläche Überprüfen. Der Überprüfungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Bei erfolgreicher Überprüfung wird eine Liste mit Mobilanwendungen gefüllt, in der Sie die zugehörige Mobilanwendung aus der Dropdownliste auswählen. Klicken Sie auf die Schaltfläche &quot;Senden&quot;, um den Assistenten abzuschließen. Der Prozess kann einige Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle damit verbundenen Analysen der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs im Modal auf die Schaltfläche Fertig, um zum Adobe Mobile Dashboard zurückzukehren.

Bei Rückkehr zum Mobile Dashboard enthält die Kachel &quot;Cloud-Dienste verwalten&quot;den AMS-Cloud-Dienst. Sie werden außerdem feststellen, dass die Kachel &quot;Analytics-Metriken&quot;mit Lebenszyklusberichten gefüllt wird.

![chlimage_1-14](assets/chlimage_1-14.png)

## Handler zur Inhaltssynchronisierung in Target {#target-content-sync-handlers}

Die Bereitstellung von Inhalten für den Geräteinhalt des Benutzers wird durch die Wiedergabe der von AEM-Inhaltserstellern erstellten Angebote generiert. Zur Verarbeitung der Wiedergabe von Zielangeboten gibt es einen neuen Content-Synchronisierungs-Handler, der die Angebote verarbeitet. Mit der Hybrid-Referenzanwendung als Beispiel enthält das en-Inhaltspaket (Englisch) ContentSyncConfig mit einem [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) -Handler. Der nächste Schritt ist entscheidend für die Wiedergabe von Angeboten an das Gerät. Der Handler mobileappoffers verfügt über eine Pfadeigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet werden soll.

Wenn sich beispielsweise eine Aktivität unter */content/campaigns/hybridref* befindet, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die *path* -Eigenschaft des Handlers mobileappoffers ein.

Für die Hybrid-Referenzanwendung gibt es zwei Handler für mobileappoffers: einen für den dev und einen für Produktionen.

Nachdem der Aktivitätspfad in der pfadeigenschaft des Handlers mobileappoffers festgelegt wurde, speichern Sie den Handler. Der Handler ist nun bereit, Angebote für unsere Mobilgeräte zu rendern.

### Rendermodus {#render-mode}

Der Handler mobileappoffers wird für Veröffentlichungs- und Entwicklungs-Setups anders konfiguriert. Für Veröffentlichungseinstellungen gibt es die Eigenschaft *renderMode* mit dem Wert *publish* , der auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der Handler mobileappoffers verweist auf den renderMode und ändert, wenn er auf &quot;publish&quot;eingestellt ist, die erstellte mbox-ID. Standardmäßig wird an die mbox-ID ein —author-Wert angehängt, der von AEM erstellt wird. Dadurch wird festgestellt, dass die Aktivität noch nicht veröffentlicht wurde, und die unveröffentlichte Kampagne sollte für Angebotsauflösungen verwendet werden.

Wenn Inhalte über das Adobe Mobile Dashboard gestaffelt werden, werden gestaffelte Inhalte als produktionsfertige Inhalte betrachtet und über die Content Sync-Konfiguration ohne Entwicklungsabgleich wiedergegeben. Bei einer solchen Wiedergabe wird —author aus allen mbox-IDs entfernt und erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Bevor Sie gestaffelte Inhalte testen, stellen Sie sicher, dass die Aktivität veröffentlicht wurde.

## Erstellen von Inhalten {#creating-content}

Nachdem die Cloud-Dienste erstellt und der Handler für mobileappoffers konfiguriert wurden, können Inhaltsersteller jetzt mit der Generierung zielgerichteter Erlebnisse beginnen.
