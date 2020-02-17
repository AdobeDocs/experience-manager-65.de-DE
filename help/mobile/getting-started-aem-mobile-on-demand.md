---
title: AEM Mobile On-Demand
seo-title: AEM Mobile On-Demand
description: Das Starten einer neuen AEM Mobile-App erfordert einen Zusammenhalt von Rollen, bevor sie zur Inhaltsbearbeitung bereit ist. Folgen Sie dieser Seite, um mit den AEM Mobile-On-Demand-Diensten zu beginnen.
seo-description: Das Starten einer neuen AEM Mobile-App erfordert einen Zusammenhalt von Rollen, bevor sie zur Inhaltsbearbeitung bereit ist. Folgen Sie dieser Seite, um mit den AEM Mobile-On-Demand-Diensten zu beginnen.
uuid: 175c609d-3cb8-4a1b-bfea-278df272e500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: dc6891cd-19cc-4dff-8bda-a41ed8af8bfb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM Mobile On-Demand{#aem-mobile-on-demand}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Wenn Sie AEM nicht als Inhaltsverwaltungsquelle verwenden, lesen Sie die Hilfe zu [AEM Mobile-On-Demand-Diensten](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM bietet verschiedene Tools, mit denen Sie Ihren Inhalt in mobile Anwendungen integrieren können.

Das folgende Diagramm zeigt, wie die verschiedenen Komponenten von AEM Mobile und On-Demand Services zusammenpassen, um Inhalte für mobile Apps bereitzustellen.

Die AEM Preflight-App kann als Testumgebung zur Vorschau der App und des Inhalts vor der Veröffentlichung betrachtet werden. während die AEM Mobile-App die endgültige App ist, die für die Distribution erstellt wurde.

>[!NOTE]
>
>Detaillierte Informationen zur Preflight-App finden Sie unter [Verwenden der AEM Preflight-App](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in der Hilfe zu AEM Mobile-On-Demand-Diensten.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>Im obigen Diagramm ist die AEM Publish-Instanz für ein typisches Bereitstellungsszenario für AEM Mobile-On-Demand-Dienste nicht erforderlich.

## Starten einer neuen mobilen App {#starting-a-new-mobile-app}

AEM Mobile ist nur eine Säule, die die gesamte AEM-Plattform ausmacht.

Das Starten einer neuen AEM Mobile-App erfordert einen Zusammenhalt von Rollen, bevor sie zur Inhaltsbearbeitung bereit ist. Die folgenden Rollen sind ein Ausgangspunkt für die Erstellung einer neuen AEM Mobile-Anwendung:

* **Administrator**
* **Entwickler**
* **Autor**

>[!NOTE]
>
>Bevor Sie mit AEM Mobile arbeiten und den Schritten in diesem Handbuch für die ersten Schritte folgen, sollten Benutzer mit AEM vertraut sein. Learn the basics of AEM [here](/help/sites-deploying/deploy.md).

### Das AEM Mobile Application Dashboard {#understanding-the-aem-mobile-application-dashboard}

Vor dem Verständnis der Rollen und Verantwortlichkeiten sollte der Benutzer über ausreichende Kenntnisse im **AEM Mobile Control Center** oder im **Application Dashboard** verfügen. Klicken Sie [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) , um eine detaillierte Beschreibung zu erhalten.

### AEM-Administrator {#aem-administrator}

Ein ***AEM-Administrator*** ist dafür verantwortlich, dem AEM Mobile-Katalog eine neue Anwendung hinzuzufügen, entweder durch Erstellen einer neuen App mit dem Erstellungsassistenten oder durch Importieren einer vorhandenen Anwendung. AEM-Administratoren, die eine neue App mit dem *Erstellungsassistenten* von AEM Mobile erstellen, wählen in der Regel eine der gewünschten App-Vorlagen aus unseren vordefinierten Referenzbeispielen oder (in den meisten Fällen) aus einer benutzerdefinierten App-Vorlage, die von *AEM-Entwicklern erstellt wurde.*

Beim Erstellen einer App mit AEM Mobile-On-Demand-Diensten ist ein AEM-Administrator für die folgenden Aufgaben zuständig:

* [Einrichten von AEM Mobile](/help/mobile/aem-mobile-setup.md)
* [Konfigurieren von Benutzer- und Benutzergruppen](/help/mobile/aem-mobile-configure-users.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Verwalten von Content Services](/help/mobile/developing-content-services.md)

Informationen zu den ersten Schritten mit den Rollen und Verantwortlichkeiten eines Administrators finden Sie unter [Verwalten von Inhalten für die Verwendung von AEM Mobile-On-Demand-Diensten](/help/mobile/aem-mobile.md).

## AEM Developer {#aem-developer}

Ein **AEM-Entwickler** erweitert und erstellt benutzerdefinierte Webvorlagen und Komponenten, um *AEM Author *zu ermöglichen, schöne und ansprechende mobile Erlebnisse zu erstellen. Diese Vorlagen und Komponenten sind nicht nur für die mobile App-Welt optimiert. kommunizieren Sie jedoch sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server), um Endpunkte des Mehrkanal-Dienstes zu erreichen. Der integrierte Content-Editor von AEM wird von *AEM-Autoren* verwendet, um umfangreiche und relevante Erlebnisse in der App zu erstellen, einschließlich der Integration mit dem Rest der Adobe Marketing Cloud.

Beim Erstellen einer App mit AEM Mobile-On-Demand-Diensten ist ein AEM-Entwickler für die folgenden Aufgaben verantwortlich:

* [App-Vorlagen und Komponenten](/help/mobile/app-templates-and-components1.md)
* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Inhaltseigenschaften und Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Entwickeln von AEM Mobile Content Services](//help/mobile/developing-content-services.md)

Erste Schritte mit den Rollen und Verantwortlichkeiten von Entwicklern finden Sie unter [Entwickeln von AEM Content für AEM Mobile-On-Demand-Dienste](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>Die Rolle eines *AEM-Entwicklers* beginnt und endet nicht mit der Entwicklung von Vorlagen und Komponenten. Ein *AEM-Entwickler* kann eine komplett neue App erstellen, anstatt einfach das standardmäßige Beispiel für die Implementierung der Referenz zu erweitern.

## AEM Author {#aem-author}

Ein ***AEM-Autor *(oder*Marketer *)**verwendet die benutzerdefinierten entwickelten oder vordefinierten Vorlagen und Komponenten, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag &amp; Drop hinzuzufügen und Medien aller Typen aus dem DAM hinzuzufügen, einschließlich Bilder, Videos und Textfragmente (Inhaltsfragmente). Der integrierte Content-Editor von AEM wird dann von*AEM-Autoren *verwendet, um umfangreiche und relevante Erlebnisse in der App zu erstellen, einschließlich der Integration mit dem Rest der Adobe Marketing Cloud.

AEM-Autoren müssen beim Erstellen einer App mit AEM Mobile-On-Demand-Diensten die folgenden Themen verstehen:

* [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Erstellen und Konfigurieren von Anwendungen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Verwalten von Inhalten](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Übersicht über Content Services](/help/mobile/develop-content-as-a-service.md)

Informationen zu den ersten Schritten mit den Rollen und Verantwortlichkeiten eines Autors finden Sie unter [Authoring von AEM Content für AEM Mobile On-Demand Services-App](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Ein AEM-Autor ist auch für das Einrichten der Berechtigung, das Erstellen von Karten und Layouts und das Senden von Push-Benachrichtigungen zuständig. Weitere Informationen zu den Methoden zum Authoring von Inhalten finden Sie unter Verwalten von Artikeln und Sammlungen; Erstellen von Bannern, Karten und Layouts in AEM Mobile finden Sie unter [AEM Mobile-On-Demand-Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).

