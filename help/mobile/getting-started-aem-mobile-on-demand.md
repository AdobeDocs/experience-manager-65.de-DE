---
title: AEM Mobile On-Demand
seo-title: AEM Mobile On-Demand
description: Für den Start eines neuen AEM Mobile-App-Erlebnisses müssen mehrere Rollen kodiert werden, bevor es für die Inhaltsbearbeitung bereit ist. Auf dieser Seite erhalten Sie AEM ersten Schritte mit mobilen On-Demand-Diensten.
seo-description: Für den Start eines neuen AEM Mobile-App-Erlebnisses müssen mehrere Rollen kodiert werden, bevor es für die Inhaltsbearbeitung bereit ist. Auf dieser Seite erhalten Sie AEM ersten Schritte mit mobilen On-Demand-Diensten.
uuid: 175c609d-3cb8-4a1b-bfea-278df272e500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: dc6891cd-19cc-4dff-8bda-a41ed8af8bfb
exl-id: 4be199d8-963d-4807-b9bb-e23fa577c5f2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 5%

---

# AEM Mobile On-Demand{#aem-mobile-on-demand}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Wenn Sie AEM nicht als Inhaltsverwaltungsquelle verwenden, finden Sie weitere Informationen unter [AEM Mobile On-demand Services Help](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM bietet verschiedene Tools, mit denen Sie Ihren Inhalt in mobile Anwendungen integrieren können.

Das folgende Diagramm zeigt, wie die verschiedenen Komponenten von AEM Mobile und On-Demand Services zusammenpassen, um Inhalte für mobile Apps bereitzustellen.

AEM Preflight-App kann als Testumgebung für die Vorschau der App und des Inhalts vor der Veröffentlichung betrachtet werden. während die AEM Mobile App die endgültige App ist, die für die Verteilung entwickelt wurde.

>[!NOTE]
>
>Ausführliche Informationen zur Preflight-App finden Sie unter [Verwenden der AEM Preflight-App](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in der AEM Mobile On-demand Services-Hilfe.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>Im obigen Diagramm ist die AEM-Veröffentlichungsinstanz für ein typisches Bereitstellungsszenario in AEM Mobile On-demand Services nicht erforderlich.

## Starten einer neuen mobilen App {#starting-a-new-mobile-app}

AEM Mobile ist nur eine Säule, die die gesamte AEM bildet.

Für den Start eines neuen AEM Mobile-App-Erlebnisses müssen mehrere Rollen kodiert werden, bevor es für die Inhaltsbearbeitung bereit ist. Die folgenden Rollen bieten einen Ausgangspunkt für die Erstellung einer neuen AEM Mobile-Anwendung:

* **Administrator**
* **Entwickler**
* **Autor**

>[!NOTE]
>
>Bevor Sie mit AEM Mobile arbeiten und die Schritte in diesem Erste-Schritte-Handbuch befolgen, sollten die Benutzer mit AEM vertraut sein. Lernen Sie die Grundlagen von AEM [hier](/help/sites-deploying/deploy.md) kennen.

### Das AEM Mobile Application Dashboard {#understanding-the-aem-mobile-application-dashboard}

Bevor Sie die Rollen und Verantwortlichkeiten verstehen, sollte der Benutzer über ausreichende Kenntnisse von **AEM Mobile Control Center** oder dem **Anwendungs-Dashboard** verfügen. Klicken Sie [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) , um ein tiefes Verständnis zu erhalten.

### AEM-Administrator {#aem-administrator}

Ein ***AEM Administrator*** ist für das Hinzufügen einer neuen Anwendung zum AEM Mobile-Katalog verantwortlich, entweder durch Erstellen einer neuen App mithilfe des Erstellungsassistenten oder durch Importieren einer bestehenden Anwendung. AEM Administratoren, die eine neue App mit dem *Erstellungsassistenten* von AEM Mobile erstellen, wählen normalerweise eine der gewünschten App-Vorlagen aus unseren vordefinierten Referenzbeispielen oder (in den meisten Fällen) aus einer benutzerdefinierten App-Vorlage, die von *AEM-Entwicklern erstellt wurde.*

Ein AEM Administrator ist für die folgenden Aufgaben beim Erstellen einer App mit AEM Mobile On-demand Services verantwortlich:

* [Einrichten von AEM Mobile](/help/mobile/aem-mobile-setup.md)
* [Konfigurieren von Benutzer- und Benutzergruppen](/help/mobile/aem-mobile-configure-users.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten eines Administrators finden Sie unter [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md).

## AEM Entwickler {#aem-developer}

Ein **AEM-Entwickler** erweitert und erstellt benutzerdefinierte Webvorlagen und Komponenten, damit der *AEM-Autor *schöne und ansprechende mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die App-Welt optimiert. kommunizieren jedoch sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server) mit kanalübergreifenden Service-Endpunkten. AEM integrierte Inhaltseditor wird von *AEM-Autoren* verwendet, um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration in den Rest der Adobe Marketing Cloud.

Ein AEM-Entwickler ist für die folgenden Aufgaben beim Erstellen einer App mit AEM Mobile On-demand Services verantwortlich:

* [App-Vorlagen und -Komponenten](/help/mobile/app-templates-and-components1.md)
* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Inhaltseigenschaften und Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Entwickeln von AEM Mobile Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten von Entwicklern finden Sie unter [Entwickeln von AEM-Inhalten für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>Die Rolle *AEM Entwickler* beginnt und endet nicht mit der Entwicklung von Vorlagen und Komponenten. Ein *AEM-Entwickler* kann eine völlig neue App erstellen, anstatt einfach das native Beispiel für die Referenzimplementierung zu erweitern.

## AEM Author {#aem-author}

Ein ***AEM-Autor* (oder *Marketer*)**verwendet die benutzerdefinierten oder nativen Vorlagen und Komponenten, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag-and-Drop zu verschieben und Medien aller DAM-Typen hinzuzufügen, einschließlich Bildern, Videos und Textfragmenten (Inhaltsfragmente). AEM integrierte Inhaltseditor wird dann von *AEM-Autoren* verwendet, um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration in den Rest der Adobe Marketing Cloud.

Ein AEM Autor muss beim Erstellen einer App mit AEM Mobile On-demand Services die folgenden Themen verstehen:

* [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Erstellen und Konfigurieren von Anwendungen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Verwalten von Inhalten](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Übersicht über Content Services](/help/mobile/develop-content-as-a-service.md)

Informationen zu den ersten Schritten mit den Rollen und Verantwortlichkeiten eines Autors finden Sie unter [Inhaltserstellung AEM AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Ein AEM-Autor ist auch für die Einrichtung von Berechtigungen, die Erstellung von Karten und Layouts und das Senden von Push-Benachrichtigungen zuständig. Weitere Informationen zu den Methoden für die Inhaltserstellung finden Sie unter Verwaltung von Artikeln und Sammlungen; Erstellen von Bannern, Karten und Layouts in AEM Mobile finden Sie unter [AEM Mobile On-Demand Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).
