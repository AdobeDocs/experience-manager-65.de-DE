---
title: AEM Mobile Application Dashboard
description: Sie können Ihre App- und App-Inhalte über das AEM Mobile Application Dashboard oder das Control Center verwalten. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: daafc8b8-3c01-4c97-a14b-f1b706600249
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 9%

---

# AEM Mobile Application Dashboard {#aem-mobile-application-dashboard}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Sie können Ihre App- und App-Inhalte über das AEM Mobile Application Dashboard oder das Control Center verwalten.

Sie können die einzelnen Kacheln im Control Center im Drilldown-Verfahren betrachten, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;..&quot;in der rechten unteren Ecke klicken.

![chlimage_1-54](assets/chlimage_1-54.png)

>[!NOTE]
>
>Sie können die Reihenfolge der Kacheln neu anordnen, indem Sie auf das Grabsymbol der Kachel klicken (9 Punkte links oben). Die Bestelländerung ist benutzerspezifisch und für einzelne Benutzer unterschiedlich.

Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.

Schließlich veröffentlichen Administratoren strategisch den aktualisierten App-Inhalt.

## Die Kachel App verwalten {#the-manage-app-tile}

Die **App verwalten** In der Kachel werden verfügbare Anwendungsinformationen angezeigt:

* Titel
* Beschreibung
* Symbol
* Zuletzt geändert
* Zuletzt geändert von

![chlimage_1-55](assets/chlimage_1-55.png)

## Kachel &quot;Verbindung verwalten&quot; {#the-manage-connection-tile}

Die **Verbindung verwalten** -Kachel zeigt die AEM Mobile On-demand Services-Verbindungsinformationen an:

* Name der Cloud-Konfiguration
* Projektname und ID
* Verbindungsstatus

>[!NOTE]
>
>Klicken Sie oben rechts auf das Zahnrad, um eine Mobile On-Demand Cloud-Konfiguration einzurichten.
>
>Siehe [Mobile On-Demand Services konfigurieren](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md) für Details.

![chlimage_1-56](assets/chlimage_1-56.png)

## Verwalten von Entitäten {#managing-entities}

Diese drei Kacheln bieten einen Überblick über den Status des Inhalts einer App:

* **Banner**
* **Artikel**
* **Sammlungen**

Jede Kachel kann erweitert werden, um eine detailliertere Listenansicht bereitzustellen, indem Sie auf die Auslassungspunkte (...) in der rechten unteren Ecke klicken. Diese Listenansichten bieten eine alternative Möglichkeit zum Zugriff auf allgemeine Mobile On Demand-Aktionen wie das Löschen, Hochladen und Bearbeiten von Eigenschaften.

### Die Kachel Banner verwalten {#the-manage-banners-tile}

Die **Banner verwalten** -Kachel ermöglicht die Verwaltung des Inhalts eines Banners. Die folgenden Informationen werden für ein Banner angezeigt:

* image
* **TITEL**: Name des Banners
* **GEÄNDERT**: zuletzt geändert in AEM
* **HOCHGELADEN**: zuletzt von AEM hochgeladen
* **VERÖFFENTLICHT**: AEM des zuletzt veröffentlichten Anforderungsformulars
* **QUELLE**: Quelle (AEM lokal oder remote von Mobile On Demand)

Die folgende Abbildung zeigt die **Banner verwalten** Kachel im AEM Mobile Application Dashboard:

![chlimage_1-57](assets/chlimage_1-57.png)

>[!NOTE]
>
>Siehe **[Banner verwalten](/help/mobile/mobile-on-demand-managing-banners.md)** zum Erstellen, Löschen oder Aktualisieren der Banner.

### Die Kachel Artikel verwalten {#the-manage-articles-tile}

Die **Artikel verwalten** -Kachel ermöglicht die Verwaltung des Inhalts eines Artikels. Die folgenden Informationen werden für einen Artikel angezeigt:

* image
* **TITEL**: Name des Artikels
* **GEÄNDERT**: zuletzt geändert in AEM
* **HOCHGELADEN**: zuletzt von AEM hochgeladen
* **VERÖFFENTLICHT**: AEM des zuletzt veröffentlichten Anforderungsformulars
* **QUELLE**: Quelle (AEM lokal oder remote von Mobile On-Demand)

Die folgende Abbildung zeigt die **Artikel verwalten** Kachel im AEM Mobile Application Dashboard:

![chlimage_1-58](assets/chlimage_1-58.png)

>[!NOTE]
>
>Siehe [**Verwalten von Artikeln**](/help/mobile/mobile-on-demand-managing-articles.md) zum Erstellen, Löschen oder Aktualisieren der Artikel.

### Die Kachel Sammlungen verwalten {#the-manage-collections-tile}

Die **Verwalten von Sammlungen** -Kachel ermöglicht die Verwaltung des Inhalts einer Sammlung. Die folgenden Informationen werden für eine Sammlung angezeigt:

* image
* **TITEL**: Name der Sammlung
* **GEÄNDERT**: zuletzt geändert in AEM
* **HOCHGELADEN**: zuletzt von AEM hochgeladen
* **VERÖFFENTLICHT**: AEM des zuletzt veröffentlichten Anforderungsformulars
* **QUELLE**: Quelle (AEM lokal oder remote von Mobile On-Demand)

Die folgende Abbildung zeigt die **Verwalten von Sammlungen** Kachel im AEM Mobile Application Dashboard:

![chlimage_1-59](assets/chlimage_1-59.png)

>[!NOTE]
>
>Siehe **[Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)** zum Erstellen, Löschen oder Aktualisieren der Sammlungen.

### Die nächsten Schritte {#the-next-steps}

Sobald Sie sich mit dem Anwendungs-Dashboard vertraut gemacht haben, sehen Sie sich die folgenden Ressourcen an, um eine Mobile App zu erstellen:

* [Erstellen und Konfigurieren von Anwendungen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Verknüpfen einer On-Demand-App mit einer Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Content Management-Aktionen](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)
