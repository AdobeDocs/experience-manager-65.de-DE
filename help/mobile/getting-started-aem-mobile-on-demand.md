---
title: Adobe Experience Manager Mobile On-Demand
description: Der Start eines neuen Adobe Experience Manager (AEM)-Erlebnisses für mobile Apps erfordert einen Benutzerkontext, bevor es zur Inhaltsbearbeitung bereit ist. Auf dieser Seite erhalten Sie AEM ersten Schritte mit mobilen On-Demand-Diensten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
exl-id: 4be199d8-963d-4807-b9bb-e23fa577c5f2
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 1%

---

# AEM Mobile On-Demand{#aem-mobile-on-demand}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Wenn Sie Adobe Experience Manager (AEM) nicht als Inhaltsverwaltungsquelle verwenden, lesen Sie [Hilfe zu AEM Mobile On-demand Services](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM bietet mehrere Tools, mit denen Sie Inhalte in mobile Anwendungen integrieren können.

Das folgende Diagramm zeigt, wie die verschiedenen Komponenten von AEM Mobile und On-Demand Services zusammenpassen, um Inhalte für mobile Apps bereitzustellen.

AEM Preflight-App kann als Testumgebung betrachtet werden, um vor der Veröffentlichung eine Vorschau der App und des Inhalts anzuzeigen. während die AEM Mobile App die endgültige App ist, die für die Verteilung entwickelt wurde.

>[!NOTE]
>
>Ausführliche Informationen zur Preflight-App finden Sie unter [Verwenden der AEM Preflight-App](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in der AEM Mobile On-demand Services-Hilfe.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>Im obigen Diagramm ist die AEM-Veröffentlichungsinstanz für ein typisches Bereitstellungsszenario in AEM Mobile On-demand Services nicht erforderlich.

## Starten einer neuen mobilen App {#starting-a-new-mobile-app}

AEM Mobile ist nur eine Säule, die die gesamte AEM bildet.

Für den Start eines neuen AEM Mobile-App-Erlebnisses müssen mehrere Rollen kodiert werden, bevor es für die Inhaltsbearbeitung bereit ist. Die folgenden Rollen bieten einen Ausgangspunkt für die Erstellung einer AEM Mobile-Anwendung:

* **Administrator**
* **Entwickler**
* **Autor**

>[!NOTE]
>
>Bevor Sie mit AEM Mobile arbeiten und die Schritte in diesem Erste-Schritte-Handbuch befolgen, sollten die Benutzer mit AEM vertraut sein. Lernen Sie die Grundlagen von AEM kennen [here](/help/sites-deploying/deploy.md).

### Grundlegendes zum AEM Mobile Application Dashboard {#understanding-the-aem-mobile-application-dashboard}

Bevor der Benutzer die Rollen und Verantwortlichkeiten versteht, sollte er über umfassende Kenntnisse in **AEM Mobile Control Center** oder **Anwendungs-Dashboard**. Klicken [here](/help/mobile/mobile-apps-ondemand-application-dashboard.md) für ein tiefes Verständnis.

### AEM-Administrator {#aem-administrator}

Ein ***AEM*** ist für das Hinzufügen einer Anwendung zum AEM Mobile-Katalog verantwortlich, entweder durch Erstellen einer App mithilfe des Erstellungsassistenten oder durch Importieren einer bestehenden Anwendung. AEM Administratoren, die eine App mit AEM Mobile erstellen *Erstellungsassistent* Wählen Sie normalerweise eine der gewünschten App-Vorlagen aus den vordefinierten Referenzbeispielen der Adobe oder (normalerweise) aus einer benutzerdefinierten App-Vorlage, die von *AEM Entwickler.*

Ein AEM Administrator ist für die folgenden Aufgaben beim Erstellen einer App mit AEM Mobile On-demand Services verantwortlich:

* [Einrichten von AEM Mobile](/help/mobile/aem-mobile-setup.md)
* [Konfigurieren von Benutzer- und Benutzergruppen](/help/mobile/aem-mobile-configure-users.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten eines Administrators finden Sie unter [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md).

## AEM Entwickler {#aem-developer}

Ein **AEM** erweitert und erstellt benutzerdefinierte Webvorlagen und -komponenten, damit der *AEM-Autor* schöne und ansprechende mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die App-Welt optimiert. kommunizieren jedoch sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server) mit kanalübergreifenden Service-Endpunkten. AEM integrierte Inhaltseditor wird von *AEM-Autoren* , um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration in die restliche Adobe Experience Cloud.

Ein AEM-Entwickler ist für die folgenden Aufgaben beim Erstellen einer App mit AEM Mobile On-demand Services verantwortlich:

* [App-Vorlagen und -Komponenten](/help/mobile/app-templates-and-components1.md)
* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Inhaltseigenschaften und Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Entwickeln von AEM Mobile Content Services](/help/mobile/developing-content-services.md)

Erste Schritte mit den Rollen und Zuständigkeiten von Entwicklern finden Sie unter [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>Ein *AEM Entwickler* -Rolle beginnt und endet nicht mit der Entwicklung von Vorlagen und Komponenten. Ein *AEM* Sie können eine völlig neue App erstellen, anstatt einfach das native Beispiel für die Referenzimplementierung zu erweitern.

## AEM Author {#aem-author}

Ein ***AEM-Autor* (oder *Marketer*)**verwendet die benutzerdefinierten oder nativen Vorlagen und Komponenten, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag-and-Drop zu verschieben und Medien aller Typen aus dem DAM hinzuzufügen, einschließlich Bildern, Videos und Textfragmenten (Inhaltsfragmente). AEM integrierte Inhaltseditor wird dann von *AEM-Autoren* , um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration in die restliche Adobe Experience Cloud.

Ein AEM Autor muss beim Erstellen einer App mit AEM Mobile On-demand Services die folgenden Themen verstehen:

* [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Erstellen und Konfigurieren von Anwendungen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Verwalten von Inhalten](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Übersicht über Content Services](/help/mobile/develop-content-as-a-service.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten eines Autors finden Sie unter [Inhaltserstellung AEM AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Ein AEM-Autor ist auch für die Einrichtung von Berechtigungen, die Erstellung von Karten und Layouts und das Senden von Push-Benachrichtigungen zuständig. Weitere Informationen zu den Methoden für die Inhaltserstellung finden Sie unter Verwaltung von Artikeln und Sammlungen; Erstellen von Bannern, Karten und Layouts in AEM Mobile, siehe [AEM Mobile On-Demand-Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).
