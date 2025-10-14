---
title: AEM Mobile-Setup
description: Auf dieser Seite können Sie AEM Mobile einrichten und dem Benutzer somit ermöglichen, Inhalte in Adobe Experience Manager (AEM) zu erstellen und zu verwalten. Auf dieser Seite finden Sie Informationen zur Integration der AEM-Instanz mit dem Cloud-basierten AEM Mobile On-demand Services-Konto und Projekten.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
exl-id: 0ead982d-2315-4947-b762-596aa2aa42a1
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---

# AEM Mobile-Setup{#aem-mobile-setup}

{{ue-over-mobile}}

>[!CAUTION]
>
>Bestehende Kunden von Adobe Experience Manager (AEM) Mobile Apps, die von AEM 6.2 oder 6.3 auf AEM 6.5 migrieren, können AEM Mobile Apps weiterhin verwenden, indem sie ein Paket von Package Share herunterladen. Neue Installationen von AEM 6.5 unterstützen jedoch nicht die Funktionen von AEM Mobile Apps.

Um AEM zur Erstellung von Inhalten für AEM Mobile-Apps zu verwenden, müssen Sie die AEM-Instanz mit dem Cloud-basierten AEM Mobile On-demand Services-Konto und den -Projekten integrieren.

Führen Sie diese Schritte aus, um AEM Mobile einzurichten und es Benutzenden zu ermöglichen, den Inhalt in AEM zu erstellen und zu verwalten.

## AEM Mobile-Bereitstellung {#aem-mobile-provisioning}

Um mit der Einrichtung von AEM Mobile zu beginnen, müssen Sie:

* **API-Schlüssel anfordern**: Um auf die On-Demand-Services-API zuzugreifen, müssen Sie einen API-Schlüssel anfordern. Um den API-Schlüssel anzufordern, füllen Sie das Formular [PDF aus](https://helpx.adobe.com/de/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html). Senden Sie das ausgefüllte Formular an den Adobe Developer-Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Generieren der Geräte-ID und des Geräte** Tokens: Nachdem Sie Ihren API-Schlüssel erhalten haben, können Sie die Geräte-ID und das Geräte-Token generieren. Gehen Sie zu `https://aex.aemmobile.adobe.com` und führen Sie folgende Schritte aus:

   * API-Schlüssel bereitstellen
   * Melden Sie sich mit einer Adobe ID an, die Sie einem AEM Mobile-Projekt mit den folgenden Berechtigungen hinzugefügt haben (siehe Schritte unten zum Erstellen eines Projekts)

      * Administration > Projekte und Benutzer verwalten
      * Inhalt > Inhalt hinzufügen und bearbeiten, Inhalt löschen, Inhalt anzeigen, Publish-Inhalt

Wenn alle Bedingungen erfüllt sind, werden eine Geräte-ID und ein Geräte-Token generiert.

>[!NOTE]
>
>Der erforderlichen Adobe ID sollte Zugriff auf ein AEM Mobile-Projekt gewährt werden. Siehe [Kontoverwaltung für AEM Mobile](https://helpx.adobe.com/de/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html) in der Online-Hilfe.

## Erstellen von Projekten für AEM Mobile {#creating-projects-for-aem-mobile}

Wenn Sie ein Projekt erstellen, geben Sie die Einstellungen für jede Zielplattform an: iOS, Android™, Windows und Desktop Web Viewer. Viele der von Ihnen angegebenen Projekteinstellungen wirken sich auf das Verhalten der App aus.

Zum Erstellen eines Projekts müssen Sie sich beim On-Demand-Service-Portal mit einer Adobe ID anmelden, die über eine Master-Administratorrolle verfügt. Zum Bearbeiten eines Projekts ist entweder eine Master-Administratorrolle oder eine Benutzerrolle mit der Berechtigung **Projekte und Benutzer verwalten** erforderlich.

>[!NOTE]
>
>Weitere Informationen zum Erstellen von Projekten in AEM Mobile finden Sie [hier](https://helpx.adobe.com/de/digital-publishing-solution/help/creating-projects.html).

## Konfigurieren eines AEM Mobile-Connectors {#configuring-an-aem-mobile-connector}

Die AEM-Einrichtung umfasst die folgenden Schritte für die Connector-Konfiguration. Sobald die Konfiguration des AEM Mobile-Connectors abgeschlossen ist, kann der Benutzer Benutzergruppen und Berechtigungen einrichten.

Der AEM Mobile On-Demand-Connector wird verwendet, um in AEM Mobile verwaltete Inhalte an die On-Demand-Services von Adobe Experience Manager Mobile zu binden. Dadurch können Inhaltsautorinnen und -autoren mithilfe der AEM-Tools Material für mobile Anwendungen erstellen und verwalten und gleichzeitig AEM Mobile On-Demand-Services für die einfache Verteilung mobiler Inhalte nutzen.

>[!NOTE]
>
>Dies ist ein einmaliger Schritt zum Einrichten der AEM-Instanz.

### Konfigurieren des AEM Mobile On-demand Services-Clients {#configuring-aem-mobile-on-demand-services-client}

Führen Sie die Konfigurationsschritte aus, damit die AEM Mobile-Integrationen ordnungsgemäß funktionieren.

1. Zur OSGi-Dienstkonfiguration

   1. AEM > Tools > Vorgänge > Web-Konsole
   1. Scrollen oder suchen Sie nach ***Experience Manager Mobile On-Demand Services Client (war Adobe Digital Publishing Solution Client)***

1. ***Experience Manager Mobile On-Demand Services-Client bearbeiten***

   1. **(Obligatorisch)** Geben Sie die erforderlichen Felder ein:

      1. Client-ID.
      1. Client-Geheimnis.

   1. **(Optional)** Bearbeiten Sie vorhandene Werte.

1. Speichern Sie die Änderungen.
1. Im Folgenden finden Sie eine Beispielkonfiguration:

![chlimage_1-53](assets/chlimage_1-53.png)

### Konfigurieren von AEM Mobile On-demand Services Cloud Service {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Zu Cloud Services gehen.

   1. AEM > Tools > Bereitstellung [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Scrollen oder suchen Sie nach ***Adobe Experience Manager Mobile On-Demand-Services***

1. Wählen Sie ***Jetzt konfigurieren*** oder ***Konfigurationen anzeigen*** und klicken Sie auf das Symbol Konfiguration hinzufügen .

1. Erstellen einer Konfiguration

   1. Titel und Namen eingeben
   1. Geräte-ID eingeben
   1. Geräte-Token eingeben
   1. Wählen Sie ***Gerätekonfiguration testen*** aus, damit Sie die eingegebenen Werte überprüfen können
   1. Klicken Sie auf OK

## Hinzufügen von AEM Mobile-Benutzerrollen und Zuweisen von Berechtigungen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nach dem Erstellen eines Projekts sollten Sie Rollen erstellen und Benutzern Zugriff gewähren. Nur Master-Administratoren können Rollen erstellen und bearbeiten. Wenn Sie eine Rolle erstellen, aktivieren Sie Funktionen (oder Berechtigungen) für die Benutzer, denen diese Berechtigungen zugewiesen werden. Sie können beispielsweise eine Rolle erstellen, die Berechtigungen für die App-Erstellung und eine andere Rolle, die Berechtigungen für die Erstellung und Veröffentlichung von Inhalten enthält.

Bei der Entwicklung von AEM Mobile-Apps gibt es drei verschiedene Rollen:

* Administrator
* Entwicklerin oder Entwickler
* Author

Weitere Informationen zum Erstellen von Rollen mit unterschiedlichen Berechtigungen, z. B. für die Erstellung von Apps oder zum Erstellen und Veröffentlichen von Inhalten, finden Sie [&#x200B; der Hilfe zu AEM Mobile &#x200B;](https://helpx.adobe.com/de/digital-publishing-solution/help/account-admin-dps.html)Erstellen von Benutzerrollen und Gewähren von Zugriff“.

>[!NOTE]
>
>Die Verwaltung von App-Inhalten erfordert eine gemeinsame Anstrengung von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden. Schließlich veröffentlichen Admins den aktualisierten App-Inhalt strategisch. Durch das Einrichten von AEM-Gruppen und -Berechtigungen werden deren Rollen im App-Dashboard oder Control Center definiert.
>
>Siehe [AEM Mobile-Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Wenn Sie mit dem Erstellen von Rollen mit verschiedenen Berechtigungen fertig sind, z. B. für die Erstellung von Apps oder für das Erstellen und Veröffentlichen von Inhalten, finden Sie weitere [**unter „Konfigurieren von Benutzern und Benutzergruppen**](/help/mobile/aem-mobile-configure-users.md). Auf diese Weise können Sie Ihre Benutzer und Gruppen so konfigurieren, dass sie die Erstellung und Verwaltung Ihrer Mobile Apps unterstützen.

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten beim Erstellen einer AEM Mobile On-demand Services-App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM-Inhalten für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Authoring von AEM-Inhalten für die AEM Mobile On-demand Services-App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Um eine Vorschau des App-Inhalts anzuzeigen, einschließlich Durchsuchen von Seiten und Artikeln, siehe [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md).
