---
title: AEM Mobile Setup
seo-title: AEM Mobile Setup
description: Folgen Sie dieser Seite, um AEM Mobile einzurichten und dem Benutzer so die Möglichkeit zu geben, die Inhalte in AEM zu erstellen und zu verwalten. Diese Seite enthält Informationen zur Integration der AEM Instanz in das Cloud-basierte AEM Mobile On-demand Services-Konto und -Projekt/e.
seo-description: Folgen Sie dieser Seite, um AEM Mobile einzurichten und dem Benutzer so die Möglichkeit zu geben, die Inhalte in AEM zu erstellen und zu verwalten. Diese Seite enthält Informationen zur Integration der AEM Instanz in das Cloud-basierte AEM Mobile On-demand Services-Konto und -Projekt/e.
uuid: 03bf5b56-7750-4f76-b079-43761367655a
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: 393cf504-917e-4bf6-9a8b-b7a5bd862c65
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 4%

---


# AEM Mobile SetUp{#aem-mobile-setup}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Bestehende AEM Mobile-Apps-Kunden, die von AEM 6.2 oder 6.3 auf AEM 6.5 migrieren, können weiterhin AEM Mobile-Apps verwenden, indem sie ein [Paket von PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/aem-mobile-package) herunterladen. Neue Installationen von AEM 6.5 unterstützen jedoch keine AEM Mobile Apps-Funktionen.

Um AEM für die Erstellung von Inhalten für AEM Mobile-Apps zu verwenden, müssen Sie die AEM Instanz mit dem Cloud-basierten AEM Mobile On-demand Services-Konto und den Cloud-basierten Projekten integrieren.

Führen Sie die folgenden Schritte aus, um AEM Mobile einzurichten und dem Benutzer so zu ermöglichen, die Inhalte in AEM zu erstellen und zu verwalten.

## AEM Mobile Provisioning {#aem-mobile-provisioning}

Um mit der AEM Mobile-Einrichtung zu beginnen, müssen Sie:

* **API-Schlüssel** anfordern: Für den Zugriff auf die On-Demand Services API müssen Sie einen API-Schlüssel anfordern. Um den API-Schlüssel anzufordern, füllen Sie das [PDF-Formular](https://helpx.adobe.com/de/digital-publishing-solution/help/integrating-dps.html) aus. Senden Sie das ausgefüllte Formular an den Entwicklersupport von Adobe: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Generieren Sie die Geräte-ID und das Gerätetoken**: Nachdem Sie Ihren API-Schlüssel erhalten haben, können Sie die Geräte-ID und das Gerätetoken generieren. Gehen Sie zu [https://aex.aemmobile.adobe.com](https://aex.aemmobile.adobe.com/) und führen Sie die folgenden Schritte aus:

   * API-Schlüssel bereitstellen
   * Melden Sie sich mit einem Adobe ID an, das Sie einem AEM Mobile-Projekt hinzugefügt haben, mit folgenden Berechtigungen (siehe die folgenden Schritte zum Erstellen des Projekts)

      * Administration > Projekte und Benutzer verwalten
      * Inhalt > Inhalt Hinzufügen und bearbeiten, Inhalt löschen, Ansicht, Inhalt veröffentlichen

Wenn alle Bedingungen erfüllt sind, werden eine Geräte-ID und ein Gerätetoken generiert.

>[!NOTE]
>
>Die erforderliche Adobe ID sollte Zugang zu einem AEM Mobile-Projekt erhalten. Siehe [Kontoverwaltung für AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in der Onlinehilfe.

## Erstellen von Projekten für AEM Mobile {#creating-projects-for-aem-mobile}

Beim Erstellen eines Projekts geben Sie Einstellungen für jede Plattform an, die Sie als Ziel auswählen: iOS, Android, Windows und Web Viewer für den Desktop. Viele der angegebenen Projekteinstellungen wirken sich auf das Verhalten der App aus.

Zum Erstellen eines Projekts müssen Sie sich beim On-Demand-Dienste-Portal mit einem Adobe ID anmelden, das über eine Übergeordnet verwaltete Rolle verfügt. Zum Bearbeiten eines Projekts ist entweder eine Übergeordnet verwaltete Rolle oder eine Benutzerrolle mit der Berechtigung **Projekte und Benutzer verwalten** erforderlich.

>[!NOTE]
>
>Um mehr über das Erstellen von Projekten in AEM Mobile zu erfahren, klicken Sie [hier](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## Konfigurieren eines AEM Mobile Connectors {#configuring-an-aem-mobile-connector}

AEM Setup umfasst die folgenden Schritte für die Connector-Konfiguration. Sobald die AEM Mobile Connector-Konfiguration abgeschlossen ist, kann der Benutzer Benutzergruppen und Berechtigungen einrichten.

Der AEM Mobile On-Demand-Connector wird verwendet, um AEM Mobile-verwaltete Inhalte mit den On-Demand-Diensten von Adobe Experience Manager Mobile zu verbinden. Auf diese Weise können Inhaltsersteller mit AEM Werkzeugen Material für mobile Anwendungen erstellen und verwalten und gleichzeitig die On-Demand-Dienste von AEM Mobile für die einfache Verteilung von mobilen Inhalten nutzen.

>[!NOTE]
>
>Dies ist ein einmaliger Schritt zum Einrichten der AEM Instanz.

### AEM Mobile On-demand Services Client {#configuring-aem-mobile-on-demand-services-client} konfigurieren

Sie müssen die Konfigurationsschritte ausführen, damit die AEM Mobile-Integrationen korrekt funktionieren.

1. Zu OSGI-Dienstkonfiguration wechseln

   1. AEM > Tools > Vorgänge > Web-Konsole
   1. Blättern Sie durch oder suchen Sie nach ***Experience Manager Mobile On-Demand Services Client (war Adobe Digital Publishing Solution Client)***

1. ***Experience Manager Mobile On-Demand Services Client*** bearbeiten

   1. **(Obligatorisch)** Geben Sie die erforderlichen Felder ein:

      1. Client-ID.
      1. Client-Geheimnis.
   1. **(Optional)** Bearbeiten Sie vorhandene Werte.


1. Speichern Sie die Änderungen.
1. Im Folgenden finden Sie eine Beispielkonfiguration:

![chlimage_1-53](assets/chlimage_1-53.png)

### Konfigurieren von AEM Mobile On-demand Services CloudService {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Zu Cloud Services

   1. AEM > Tools > Bereitstellung> [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Blättern Sie durch oder suchen Sie nach ***Adobe Experience Manager Mobile On-Demand-Dienste***

1. Wählen Sie ***Jetzt konfigurieren*** oder ***Konfigurationen anzeigen*** und klicken Sie auf das Symbol Neue Konfiguration hinzufügen

1. Neue Konfiguration erstellen

   1. Titel und Namen eingeben
   1. Geräte-ID eingeben
   1. Gerätetoken eingeben
   1. Wählen Sie ***Testgerätekonfiguration*** aus, um die eingegebenen Werte zu validieren.
   1. Ok auswählen

## Hinzufügen von AEM Mobile-Benutzerrollen und Zuweisen von Berechtigungen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nachdem Sie ein Projekt erstellt haben, sollten Sie Rollen erstellen und Benutzern Zugriff gewähren. Nur Übergeordnet Administratoren können Rollen erstellen und bearbeiten. Wenn Sie eine Rolle erstellen, aktivieren Sie die Funktionen (oder Berechtigungen) für die Benutzer, denen diese Berechtigungen zugewiesen wurden. Sie können beispielsweise eine Rolle mit Berechtigungen zum Erstellen von Apps und eine andere Rolle mit Berechtigungen zum Erstellen und Veröffentlichen von Inhalten erstellen.

Bei der AEM Mobile-App-Entwicklung gibt es drei verschiedene Rollen:

* Administrator


* Entwickler
* Autor

Weitere Informationen zum Erstellen von Rollen mit unterschiedlichen Berechtigungen, z. B. zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten, erhalten Sie, wenn Sie in der AEM Mobile-Hilfe auf [Benutzerrollen erstellen und Zugriff gewähren](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) klicken.

>[!NOTE]
>
>Die Verwaltung von App-Inhalten erfordert gemeinsame Anstrengungen von Entwicklern, Inhaltserstellern und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden. Schließlich veröffentlichen Administratoren den aktualisierten App-Inhalt strategisch. Durch das Einrichten AEM Gruppen und Berechtigungen werden ihre Rollen im App-Dashboard oder im Control Center definiert.
>
>Weitere Informationen zum AEM Mobile-Dashboard erhalten Sie, wenn Sie [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) klicken.

Sobald Sie mit der Erstellung von Rollen mit unterschiedlichen Berechtigungen wie dem Erstellen von Apps oder dem Erstellen und Veröffentlichen von Inhalten fertig sind, lesen Sie [**Konfigurieren Sie Ihre Benutzer- und Benutzergruppen**](/help/mobile/aem-mobile-configure-users.md), um Ihre Benutzer und Gruppen so zu konfigurieren, dass das Erstellen und Verwalten Ihrer mobilen Apps unterstützt wird.

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Verantwortlichkeiten beim Erstellen einer AEM Mobile On-demand Services-App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM Inhalte für AEM Mobile On-demand Services-Apps](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Informationen zur Vorschau der App-Inhalte, einschließlich Durchsuchen-Seiten und Artikel, finden Sie unter [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md).
