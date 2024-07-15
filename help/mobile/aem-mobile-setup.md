---
title: AEM Mobile-Einrichtung
description: Auf dieser Seite erfahren Sie, wie Sie AEM Mobile einrichten und damit Benutzer Inhalte in Adobe Experience Manager (AEM) erstellen und verwalten können. Auf dieser Seite finden Sie Informationen zur Integration der AEM-Instanz in das Cloud-basierte AEM Mobile On-demand Services-Konto und -Projekte.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
exl-id: 0ead982d-2315-4947-b762-596aa2aa42a1
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 3%

---

# AEM Mobile-Einrichtung{#aem-mobile-setup}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Bestehende Adobe Experience Manager (AEM) Mobile Apps-Kunden, die von AEM 6.2 oder 6.3 auf AEM 6.5 migrieren, können weiterhin AEM Mobile-Apps verwenden, indem sie ein Paket von Package Share herunterladen. Neue Installationen von AEM 6.5 unterstützen jedoch nicht die Funktionalität von AEM Mobile Apps.

Um AEM zur Erstellung von Inhalten für AEM Mobile-Apps zu verwenden, müssen Sie die AEM-Instanz in das Cloud-basierte AEM Mobile On-demand Services-Konto und die Cloud-basierten-Projekte integrieren.

Führen Sie die folgenden Schritte aus, um AEM Mobile einzurichten und es dem Benutzer zu ermöglichen, Inhalte in AEM zu erstellen und zu verwalten.

## AEM Mobile-Bereitstellung {#aem-mobile-provisioning}

Um mit der Einrichtung von AEM Mobile zu beginnen, müssen Sie:

* **API-Schlüssel anfordern**: Um auf die On-Demand Services API zuzugreifen, müssen Sie einen API-Schlüssel anfordern. Um den API-Schlüssel anzufordern, füllen Sie das [PDF-Formular](https://helpx.adobe.com/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html) aus. Senden Sie das ausgefüllte Formular an den Adobe Developer-Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Generieren Sie die Geräte-ID und das Geräte-Token**: Nachdem Sie Ihren API-Schlüssel erhalten haben, können Sie die Geräte-ID und das Geräte-Token generieren. Gehen Sie zu `https://aex.aemmobile.adobe.com` und führen Sie folgende Schritte aus:

   * API-Schlüssel angeben
   * Melden Sie sich mit einer Adobe ID an, die Sie einem AEM Mobile-Projekt mit den folgenden Berechtigungen hinzugefügt haben (siehe die folgenden Schritte zum Erstellen eines Projekts)

      * Administration > Projekte und Benutzer verwalten
      * Inhalt > Inhalt hinzufügen und bearbeiten, Inhalt löschen, Inhalt anzeigen, Publish-Inhalt

Wenn alle Bedingungen erfüllt sind, werden eine Geräte-ID und ein Geräte-Token generiert.

>[!NOTE]
>
>Der benötigten Adobe ID sollte Zugriff auf ein AEM Mobile-Projekt gewährt werden. Siehe [Kontoverwaltung für AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html) in der Onlinehilfe.

## Erstellen von Projekten für AEM Mobile {#creating-projects-for-aem-mobile}

Wenn Sie ein Projekt erstellen, legen Sie Einstellungen für jede Plattform fest, die Sie als Ziel auswählen: iOS, Android™, Windows und Web Viewer für den Desktop. Viele der von Ihnen angegebenen Projekteinstellungen beeinflussen das Verhalten der App.

Zum Erstellen eines Projekts müssen Sie sich über eine Adobe ID mit der Master-Administratorrolle beim On-Demand-Dienstportal anmelden. Für die Bearbeitung eines Projekts ist entweder eine Master-Administratorrolle oder eine Benutzerrolle mit der Berechtigung **Projekte und Benutzer verwalten** erforderlich.

>[!NOTE]
>
>Um mehr über das Erstellen von Projekten in AEM Mobile zu erfahren, klicken Sie auf [hier](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## Konfigurieren eines AEM Mobile Connectors {#configuring-an-aem-mobile-connector}

AEM Einrichtung umfasst die folgenden Schritte zur Connector-Konfiguration. Sobald die Konfiguration des AEM Mobile-Connectors abgeschlossen ist, kann der Benutzer Benutzergruppen und Berechtigungen einrichten.

Der AEM Mobile On-Demand-Connector wird verwendet, um AEM Mobile-verwaltete Inhalte mit den On-Demand-Diensten von Adobe Experience Manager Mobile zu verbinden. Auf diese Weise können Inhaltsautoren mithilfe AEM Tools Material für mobile Anwendungen erstellen und verwalten und gleichzeitig die On-Demand-Dienste von AEM Mobile zur einfachen Verteilung mobiler Inhalte nutzen.

>[!NOTE]
>
>Dies ist ein einmaliger Schritt zum Einrichten der AEM-Instanz.

### Konfigurieren des AEM Mobile On-demand Services Client {#configuring-aem-mobile-on-demand-services-client}

Führen Sie die Konfigurationsschritte aus, damit die AEM Mobile-Integrationen ordnungsgemäß funktionieren.

1. Navigieren Sie zur OSGi-Dienstkonfiguration .

   1. AEM > Tools > Vorgänge > Web-Konsole
   1. Scrollen oder suchen Sie nach ***Experience Manager Mobile On-Demand Services Client (war Adobe Digital Publishing Solution Client)***

1. Bearbeiten von ***Experience Manager Mobile On-Demand Services Client***

   1. **(Obligatorisch)** Geben Sie die erforderlichen Felder ein:

      1. Client-ID.
      1. Client Secret.

   1. **(Optional)** Vorhandene Werte bearbeiten.

1. Speichern Sie die Änderungen.
1. Im Folgenden finden Sie eine Beispielkonfiguration:

![chlimage_1-53](assets/chlimage_1-53.png)

### Konfigurieren von AEM Mobile On-demand Services Cloud Service {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Gehe zu Cloud Services.

   1. AEM > Tools > Bereitstellung > [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Scrollen oder suchen Sie nach ***Adobe Experience Manager Mobile On-Demand-Services***

1. Wählen Sie ***Jetzt konfigurieren*** oder ***Konfigurationen anzeigen*** aus und wählen Sie das Symbol zum Hinzufügen der Konfiguration aus.

1. Erstellen einer Konfiguration

   1. Geben Sie einen Titel und Namen ein
   1. Geräte-ID eingeben
   1. Geräte-Token eingeben
   1. Wählen Sie ***Gerätekonfiguration testen*** aus, damit Sie die eingegebenen Werte überprüfen können
   1. OK auswählen

## Hinzufügen von AEM Mobile-Benutzerrollen und Zuweisen von Berechtigungen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nachdem Sie ein Projekt erstellt haben, sollten Sie Rollen erstellen und Benutzern Zugriff gewähren. Nur Hauptadministratoren können Rollen erstellen und bearbeiten. Wenn Sie eine Rolle erstellen, aktivieren Sie die Funktionen (oder Berechtigungen) für die Benutzer, denen diese Berechtigungen zugewiesen sind. Sie können beispielsweise eine Rolle erstellen, die Berechtigungen zum Erstellen von Apps enthält, und eine andere Rolle, die Berechtigungen zum Erstellen und Veröffentlichen von Inhalten enthält.

Bei der Entwicklung von AEM Mobile-Apps gibt es drei verschiedene Rollen:

* Administrator
* Entwicklerin oder Entwickler
* Author

Weitere Informationen zum Erstellen von Rollen mit unterschiedlichen Berechtigungen wie zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten finden Sie unter &quot;AEM Mobile-Hilfe&quot;auf [Erstellen von Benutzerrollen und Gewähren von Zugriff](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) .

>[!NOTE]
>
>Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden. Schließlich veröffentlichen Administratoren strategisch den aktualisierten App-Inhalt. Durch das Einrichten von AEM Gruppen und Berechtigungen werden deren Rollen im App-Dashboard oder im Control Center definiert.
>
>Siehe [AEM Mobile Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Wenn Sie die Erstellung von Rollen mit unterschiedlichen Berechtigungen abgeschlossen haben, z. B. zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten, finden Sie weitere Informationen unter [**Konfigurieren von Benutzern und Benutzergruppen**](/help/mobile/aem-mobile-configure-users.md). Auf diese Weise können Sie Ihre Benutzer und Gruppen so konfigurieren, dass die Erstellung und Verwaltung Ihrer mobilen Apps unterstützt wird.

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten beim Erstellen einer AEM Mobile On-demand Services App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Inhaltserstellung AEM AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Informationen zur Vorschau der App-Inhalte, einschließlich Durchsuchen-Seiten und Artikeln, finden Sie unter [Vorschau mit Preflight anzeigen](/help/mobile/aem-mobile-manage-ondemand-services.md).
