---
title: Adobe Experience Manager Mobile On-Demand
description: Für den Start einer neuen Adobe Experience Manager (AEM)-Mobile-App ist eine Zusammenführung von Rollen erforderlich, bevor sie zur Inhaltsbearbeitung bereit ist. Auf dieser Seite finden Sie Informationen zu den ersten Schritten mit AEM Mobile On-Demand-Services.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
exl-id: 4be199d8-963d-4807-b9bb-e23fa577c5f2
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---

# AEM Mobile On-Demand{#aem-mobile-on-demand}

{{ue-over-mobile}}

>[!NOTE]
>
>Wenn Sie Adobe Experience Manager (AEM) nicht als Inhaltsverwaltungsquelle verwenden, finden Sie weitere Informationen in der [AEM Mobile On-demand Services-Hilfe](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM bietet mehrere Tools, mit denen Sie Ihre Inhalte in mobile Anwendungen integrieren können.

Die folgende Abbildung zeigt, wie die verschiedenen Komponenten von AEM Mobile und On-Demand-Services zusammenpassen, um Inhalte für Mobile Apps bereitzustellen.

Die AEM Preflight-App kann als Testumgebung betrachtet werden, um die App und den Inhalt vor der Veröffentlichung in der Vorschau anzuzeigen, während die AEM Mobile-App die endgültige App ist, die für die Verteilung erstellt wird.

>[!NOTE]
>
>Ausführliche Informationen zur Preflight-App finden Sie unter [Verwenden der AEM Preflight-App](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in der AEM Mobile On-demand Services-Hilfe.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>Im obigen Diagramm ist die AEM Publish-Instanz für ein typisches Bereitstellungsszenario in AEM Mobile On-demand Services nicht erforderlich.

## Starten einer neuen Mobile App {#starting-a-new-mobile-app}

AEM Mobile ist nur eine Säule der gesamten AEM-Plattform.

Um ein neues AEM Mobile-App-Erlebnis zu starten, müssen mehrere Personen mit unterschiedlichen Rollen zusammenarbeiten. Die folgenden Rollen bieten einen Ausgangspunkt für die Erstellung eines AEM Mobile-Programms:

* **Administrator**
* **Entwickler**
* **Autor**

>[!NOTE]
>
>Bevor Sie mit AEM Mobile arbeiten und die Schritte in diesem Erste-Schritte-Handbuch befolgen, sollten Benutzerinnen und Benutzer mit AEM vertraut sein. Lernen Sie die Grundlagen der AEM [hier](/help/sites-deploying/deploy.md) kennen.

### Das Dashboard der AEM Mobile-Anwendung {#understanding-the-aem-mobile-application-dashboard}

Bevor Sie die Rollen und Zuständigkeiten verstehen, sollten Sie über fundierte Kenntnisse des **AEM Mobile Control Center** oder des **Anwendungs-Dashboards** verfügen. Klicken Sie [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md), um eine detaillierte Übersicht zu erhalten.

### AEM-Admin {#aem-administrator}

Ein ***AEM-Administrator*** ist für das Hinzufügen einer Anwendung zum AEM Mobile-Katalog verantwortlich, entweder durch Erstellen einer Anwendung mit dem Erstellungsassistenten oder durch Importieren einer vorhandenen Anwendung. AEM-Administratoren, die eine App mit dem *Erstellungsassistenten* von AEM Mobile erstellen, wählen in der Regel eine der gewünschten App-Vorlagen entweder aus den vordefinierten Referenzbeispielen der Adobe oder (in der Regel) aus einer benutzerdefinierten App-Vorlage, die von *AEM-Entwicklerinnen und -Entwicklern erstellt wurde.*

Ein AEM-Administrator ist beim Erstellen einer App mit AEM Mobile On-demand Services für die folgenden Aufgaben verantwortlich:

* [Einrichten von AEM Mobile](/help/mobile/aem-mobile-setup.md)
* [Konfigurieren von Benutzenden und Benutzergruppen](/help/mobile/aem-mobile-configure-users.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten eines Administrators finden Sie unter [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md).

## AEM Developer {#aem-developer}

Ein **AEM-Entwickler** erweitert und erstellt benutzerdefinierte Web-Vorlagen und -Komponenten, damit der *AEM-Autor* ansprechende mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die Welt der mobilen App optimiert, sondern kommunizieren sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server) an Omni-Channel-Service-Endpunkte. Der integrierte Inhaltseditor von AEM wird von *AEM-Autorinnen und -* verwendet, um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration mit dem Rest der Adobe Experience Cloud.

Ein AEM-Entwickler ist beim Erstellen einer App mit AEM Mobile On-demand Services für die folgenden Aufgaben verantwortlich:

* [Programmvorlagen und -komponenten](/help/mobile/app-templates-and-components1.md)
* [Mobile mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Inhaltseigenschaften und Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Entwickeln von AEM Mobile Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten von Entwicklern finden Sie unter [Entwickeln von AEM-Inhalten für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>Die Rolle eines *AEM* Entwicklers beginnt und endet nicht mit der Entwicklung von Vorlagen und Komponenten. Ein *AEM* Entwickler kann eine völlig neue App erstellen, anstatt einfach das vorkonfigurierte Beispiel für die Referenzimplementierung zu erweitern.

## AEM Author {#aem-author}

Ein ***AEM-Autor* (oder *Marketer*)**&#x200B;verwendet die benutzerdefinierten oder vordefinierten Vorlagen und Komponenten, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag-and-Drop zu verschieben und Medien aller Art aus dem DAM hinzuzufügen, einschließlich Bildern, Videos und Textfragmenten (Inhaltsfragmenten). Der integrierte Inhaltseditor von AEM wird dann von *AEM-Autorinnen und -* verwendet, um umfangreiche und relevante Erlebnisse innerhalb der App zu erstellen, einschließlich der Integration mit dem Rest der Adobe Experience Cloud.

AEM-Autorinnen und -Autoren müssen beim Erstellen einer App mit AEM Mobile On-demand Services die folgenden Themen verstehen:

* [AEM Mobile-Anwendungs-Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Anwendungserstellungs- und Konfigurationsaktionen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Verwalten von Inhalt](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Übersicht über Content Services](/help/mobile/develop-content-as-a-service.md)

Informationen zu den ersten Schritten mit den Rollen und Zuständigkeiten eines Autors finden Sie unter [Authoring von AEM-Inhalten für die AEM Mobile On-demand Services-App](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Ein AEM-Autor ist auch für die Einrichtung von Berechtigungen, die Erstellung von Karten und Layouts sowie das Senden von Push-Benachrichtigungen verantwortlich. Weitere Informationen zu den Methoden zum Erstellen von Inhalten, Verwalten von Artikeln und Sammlungen, Erstellen von Bannern, Karten und Layouts in AEM Mobile finden Sie unter [AEM Mobile On-Demand-Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).
