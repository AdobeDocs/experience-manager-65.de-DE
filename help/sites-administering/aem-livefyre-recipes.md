---
title: AEM Livefyre-Rezepte
seo-title: AEM Livefyre-Rezepte
description: Schrittweise Anweisungen zu allgemeinen Adobe Experience Manager Livefyre-Anwendungsfällen.
seo-description: Schrittweise Anweisungen zu allgemeinen Adobe Experience Manager Livefyre-Anwendungsfällen.
uuid: 78695a63-fca6-4990-9755-0aeaae4a7f64
contentOwner: alba
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: fdea5ede-d44f-463e-af8a-111ee7469ede
exl-id: 7ccd67a7-9945-48c1-9986-f4eaf0f2b961
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 75%

---

# AEM Livefyre-Rezepte{#aem-livefyre-recipes}

Schrittweise Anweisungen zu allgemeinen Adobe Experience Manager Livefyre-Anwendungsfällen.

## Sie können UGC mithilfe der vordefinierten Livefyre AEM-Komponenten kuratieren und mithilfe von Livefyre Media Wall anzeigen.{#curate-ugc-using-the-out-of-the-box-livefyre-aem-components-and-display-using-livefyre-media-wall}

Media Wall streamt soziale und native Livefyre-Inhalte auf eine Echtzeit-Social-Media-Pinnwand. Je nach Anwendungsfall und Anforderungen gibt es verschiedene Möglichkeiten, Media Wall in AEM zu implementieren.

Das AEM Livefyre-Paket bietet eine vorab konfigurierte Implementierungsmöglichkeit, während die herkömmliche Integration die Möglichkeit bietet, benutzerdefinierte Livefyre AEM-Komponenten zu erstellen.

### AEM-Integration  {#aem-integration}

Das Livefyre Adobe Experience Manager-Paket ist für AEM 6.1, 6.2 SP1, 6.3, 6.4 und 6.4 SP1 verfügbar. AEM 5.x und 6.0 werden nicht unterstützt. Detaillierte Anweisungen finden Sie unter [Integrieren mit Livefyre](https://helpx.adobe.com/de/experience-manager/6-4/sites/administering/using/livefyre.html).

Informationen dazu, welche Livefyre-Apps unterstützt werden, finden Sie in der [AEM Support-Matrix für Livefyre-Apps](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html#AEMSupportMatrixforLivefyreApps).

### Herkömmliche Implementierung (für benutzerdefinierte AEM-Komponenten) {#traditional-implementation-for-customized-aem-components}

Es gibt drei Möglichkeiten, Livefyre in eine benutzerdefinierte AEM-Komponente oder andere CMS-Systeme (z. B. WordPress, Sitecore oder DemandWare) zu implementieren. Eine herkömmliche Livefyre-Integration ist mit CMS kompatibel.

**Methode 1: Designer App-Implementierung**

* **Was:** Einfachste und schnellste Möglichkeit zur Integration einer Livefyre-App. Sie können innerhalb von Minuten benutzerdefinierten JavaScript-Einbettungscode zur Integration einer Media Wall-App entwerfen, konfigurieren und generieren.
* **Wie:**  [Erstellen, Anzeigen, Veröffentlichen und Einbetten einer Media Wall-App](https://docs.adobe.com/content/help/en/livefyre/using/apps/c-create-an-app.html)

* **Beispiel:** [https://codepen.io/dharafyre/pen/bvGrLo](https://codepen.io/dharafyre/pen/bvGrLo)

**Methode 2: SDK-Implementierung**

* **Was:**[Livefyre.js](https://docs.adobe.com/content/help/en/livefyre/implementation/c-livefyre_js.html) ist die Basisbibliotheksdatei für die Apps und Autorisierung auf einer Site. Sie definiert das globale *window.Livefyre*-Objekt und eine einzelne öffentliche Methode, *Livefyre.required*, die zum Laden anderer Livefyre-JavaScript-Bibliotheken verwendet werden kann. Diese sind beim Einbetten von Livefyre-Apps sowie zur Integration in Drittanbieter-Plattformen zur Benutzerauthentifizierung hilfreich.

* **Wie**: [Verwenden des Streamhub-Wall-Pakets des Livefyre JavaScript-SDK ](https://docs.adobe.com/content/help/en/livefyre/implementation/app-integrations/c-media-wall-integration.html)

* **Beispiel**: [https://codepen.io/dharafyre/pen/KZKBNv?editors=1010](https://codepen.io/dharafyre/pen/KZKBNv?editors=1010)

Informationen zu erweiterten Anpassungen mit dem SDK finden Sie unter [Streamhub-SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 3: API-Implementierung**

* Zum Erstellen benutzerdefinierter Erlebnisse und Datenvisualisierungen können Livefyre-Apps von Grund auf neu erstellt werden. Hierfür lassen sich Livefyre- und Social-Media-Daten mithilfe der [Bootstrap- und Stream-API](https://docs.adobe.com/content/help/en/livefyre/implementation/advanced-topics/bootstrap-stream-api.html) nutzen.

Beachten Sie beim Erstellen der Benutzeroberfläche für benutzergenerierte Inhalte die Anzeigerichtlinien [Twitter](https://developer.twitter.com/en/developer-terms/display-requirements.html), [Facebook](https://en.facebookbrand.com/guidelines/brand) und [Instagram](https://en.instagram-brand.com/).

### Integration von Media Wall-Authentifizierung {#media-wall-authentication-integration}

Informationen zu Media Wall-Integrationen, die Authentifizierung erfordern, finden Sie unter:

* [Anpassen der Single Sign-on-](https://helpx.adobe.com/de/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) Integration für AEM Identity Management
* [Identitätsintegration](https://docs.adobe.com/content/help/en/livefyre/implementation/identity-integration/t-about-identity-integration.html) für Authentifizierungsplattformen von Drittanbietern

### Überblick der Anwendungsbeispiele {#use-case-overview}

Als AEM-Kunde möchte ich UGC mithilfe der vordefinierten Livefyre AEM-Komponenten kuratieren und mit Livefyre Media Wall anzeigen:

So gehen Sie vor:

1. [Erste Schritte](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html)
1. [Konfigurieren von AEM für Livefyre](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html)
1. [Ziehen Sie die AEM Media Wall-Komponente per Drag-and-Drop auf Ihre Site](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html#UseLivefyrewithAEMSites)
1. [Konfigurieren von Streams und Hinzufügen von Regeln, um UGC zu kuratieren und auf der Media Wall-Komponente anzuzeigen](https://docs.adobe.com/content/help/en/livefyre/using/streams/c-streams.html)

Schulungsvideos zu Streaming-UGC finden Sie unter [Erstellen automatischer Content Streams und Suchen nach Social Content in Adobe Experience Manager Livefyre](https://helpx.adobe.com/de/experience-manager/tutorials.html).

### Kundenbeispiele {#customer-examples}

* [CNN Media Wall](https://edition.cnn.com/specials/nepal-earthquake-media-wall)
* [PGA Tour Media Wall](https://www.pgatour.com/social-hub.html)

Zum Erstellen benutzerdefinierter Erlebnisse und Datenvisualisierungen können Livefyre-Apps von Grund auf neu erstellt werden. Hierfür lassen sich Livefyre- und Social-Media-Daten mithilfe der [Bootstrap- und Stream-API](https://docs.adobe.com/content/help/en/livefyre/implementation/advanced-topics/bootstrap-stream-api.html) nutzen.

Informationen zu Livefyre-Apps, für die Authentifizierung erforderlich ist, finden Sie unter [Identitätsintegration](https://docs.adobe.com/content/help/en/livefyre/implementation/identity-integration/t-about-identity-integration.html) für Authentifizierungsplattformen von Drittanbietern.

* [PGA Tour Media Wall](https://www.pgatour.com/social-hub.html)
* [TimeOut](https://www.timeout.com/london/restaurants/forest-bar-kitchen#tab_panel_3)

## Integrieren von Livefyre Comments mithilfe von AEM-Komponenten oder herkömmlicher Livefyre-Integration  {#integrate-livefyre-comments-using-aem-components-or-traditional-livefyre-integration}

### AEM-Integration {#aem-integration-1}

Das Livefyre Adobe Experience Manager-Paket ist für AEM 6.1, 6.2 SP1, 6.3, 6.4 und 6.4 SP1 verfügbar. AEM 5.x und 6.0 werden nicht unterstützt. Detaillierte Anweisungen finden Sie unter [Integrieren mit Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

### Herkömmliche Implementierung (für benutzerdefinierte AEM-Komponenten) {#traditional-implementation-for-customized-aem-components-1}

Es gibt drei Möglichkeiten, die Livefyre Comments-App in eine benutzerdefinierte AEM-Komponente oder andere CMS-Systeme (z. B. WordPress, Sitecore oder DemandWare) zu implementieren. Eine herkömmliche Livefyre-Integration ist mit CMS kompatibel.

**Methode 1: Designer App-Implementierung**

* **Was:** Einfachste und schnellste Möglichkeit zur Integration einer Livefyre-App. Sie können innerhalb von Minuten benutzerdefinierten JavaScript-Einbettungscode zur Integration einer Media Wall-App entwerfen, konfigurieren und generieren.
* **Wie:** [Erstellen, Anzeigen, Veröffentlichen und Einbetten einer Kommentaranwendung](https://docs.adobe.com/content/help/en/livefyre/using/apps/c-create-an-app.html)

* **Beispiel:**[https://codepen.io/dharafyre/pen/oYoJdP](https://codepen.io/dharafyre/pen/oYoJdP)

**Methode 2: SDK-Implementierung**

* **Was:**[Livefyre.js](https://docs.adobe.com/content/help/en/livefyre/implementation/c-livefyre_js.html) ist die Basisbibliotheksdatei für die Apps und Autorisierung auf einer Site. Sie definiert das globale *window.Livefyre*-Objekt und eine einzelne öffentliche Methode, *Livefyre.required*, die zum Laden anderer Livefyre-JavaScript-Bibliotheken verwendet werden kann. Diese sind beim Einbetten von Livefyre-Apps sowie zur Integration in Drittanbieter-Plattformen zur Benutzerauthentifizierung hilfreich.

* **Wie:**

   * Erstellen Sie eine Sammlung/App mit dem [CollectionMeta-Token](https://docs.adobe.com/content/help/en/livefyre/implementation/getting-started/implementation-process/c-collectionmeta-tokent.html).
   * Integrieren Sie die [Comments-App](https://docs.adobe.com/content/help/en/livefyre/implementation/app-integrations/comments/c-comments-integration.html) mithilfe der Livefyre.js-Einbettungscode-Struktur in Sites.

* **Beispiel:**[https://codepen.io/dharafyre/pen/oYoJdP](https://codepen.io/dharafyre/pen/oYoJdP)

Informationen zu erweiterten Anpassungen mit dem SDK finden Sie unter [StreamHub-SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 3: API-Implementierung**

* Zum Erstellen benutzerdefinierter Erlebnisse und Datenvisualisierungen können Livefyre-Apps von Grund auf neu erstellt werden. Hierfür lassen sich Livefyre- und Social-Media-Daten mithilfe der [Bootstrap- und Stream-API](https://docs.adobe.com/content/help/en/livefyre/implementation/advanced-topics/bootstrap-stream-api.html) nutzen.

### Integration der Comments-App-Authentifizierung  {#comments-app-authentication-integration}

* [Anpassen der Single Sign-on-](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) Integration für AEM Identity Management
* [Identitätsintegration](https://docs.adobe.com/content/help/en/livefyre/implementation/identity-integration/t-about-identity-integration.html) für Authentifizierungsplattformen von Drittanbietern

### Kundenbeispiele {#customer-examples-1}

* [Poise (Kimberly Klark)](https://www.poise.com/en-us/advice-and-support/blog-and-podcast/blog/5-holiday-party-tips-for-managing-lbl)

## Verwenden der Livefyre AEM Assets-Integration zum Importieren von UGC in AEM Assets {#use-livefyre-aem-assets-integration-to-import-ugc-in-aem-assets}

**Livefyre-Einrichtung (für UGC-Kuration und Rights Management):**

1. [Konfigurieren von Streams und Hinzufügen von Regeln zum Kuratieren von UGC für Livefyre Asset-Bibliotheksordner](https://docs.adobe.com/content/help/en/livefyre/using/streams/c-streams.html)

   1. Schulungsvideos zu Streaming-UGC finden Sie unter [Erstellen automatischer Content Streams und Suchen nach Social Content in Adobe Experience Manager Livefyre](https://helpx.adobe.com/experience-manager/tutorials.html).

1. [Erfassen, Organisieren und Verwalten kuratierter UGC in Livefyre Asset-Bibliotheksordnern](https://docs.adobe.com/content/help/en/livefyre/using/library/assets/c-assets.html)

   1. Schulungsvideos zum Erstellen und Verwalten von Ordnern in der Livefyre Studio Asset Library finden Sie unter [Arbeiten mit Assets in Adobe Experience Manager Livefyre](https://helpx.adobe.com/experience-manager/tutorials.html).

1. [Anfordern von Berechtigungen für kuratierten UGC mithilfe von Livefyre Studio](https://docs.adobe.com/content/help/en/livefyre/using/rights-requests/c-how-requesting-rights-works.html)

**AEM-Einrichtung (zum Importieren von UGC in AEM Assets):**

1. [Erste Schritte](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html#GettingStarted)
1. [Konfigurieren von AEM für Livefyre](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html#ConfigureAEMtouseLivefyre)
1. [Importieren von UGC, der von Livefyre in AEM Assets kuratiert wurde](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/livefyre.html#UseLivefyrewithAEMAssets)

* [Tourism Australia](https://www.australia.com/de-de)

## Integrieren von Livefyre Reviews mithilfe von AEM-Komponenten oder herkömmlicher Livefyre-Integration  {#integrate-livefyre-reviews-using-aem-components-or-traditional-livefyre-integration}

### AEM-Integration {#aem-integration-2}

Das Livefyre Adobe Experience Manager-Paket ist für AEM 6.1, 6.2 SP1, 6.3, 6.4 und 6.4 SP1 verfügbar. AEM 5.x und 6.0 werden nicht unterstützt. Detaillierte Anweisungen finden Sie unter [Integrieren mit Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

Die Reviews-Komponente wird in AEM 6.1 nicht unterstützt. Weitere Informationen finden Sie in der [AEM-Unterstützungsmatrix für alle Livefyre-Apps](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#AEMSupportMatrixforLivefyreApps).

### Herkömmliche Implementierung (für benutzerdefinierte AEM-Komponenten)  {#traditional-implementation-for-customized-aem-components-2}

Es gibt zwei Möglichkeiten, die Livefyre Reviews-App in eine benutzerdefinierte AEM-Komponente oder andere CMS-Systeme (z. B. WordPress, Sitecore oder DemandWare) zu implementieren. Eine herkömmliche Livefyre-Integration ist mit CMS kompatibel.

**Methode 1: SDK-Implementierung**

* **Was:**[Livefyre.js](https://docs.adobe.com/content/help/en/livefyre/implementation/c-livefyre_js.html) ist die Basisbibliotheksdatei für die Apps und Autorisierung auf einer Site. Sie definiert das globale *window.Livefyre*-Objekt und eine einzelne öffentliche Methode, *Livefyre.required*, die zum Laden anderer Livefyre-JavaScript-Bibliotheken verwendet werden kann. Diese sind beim Einbetten von Livefyre-Apps sowie zur Integration in Drittanbieter-Plattformen zur Benutzerauthentifizierung hilfreich.

* **Wie:**

   * Erstellen Sie das [CollectionMeta-Token](https://docs.adobe.com/content/help/en/livefyre/implementation/app-integrations/c-reviews-integration.html), um Metadaten anzugeben, die in der Reviews-Sammlung gespeichert werden sollen.
   * Integrieren Sie die [Reviews-App](https://docs.adobe.com/content/help/en/livefyre/implementation/app-integrations/c-reviews-integration.html) mithilfe der *Livefyre.js*-Einbettungscode-Struktur in Sites.

* **Beispiel:**[https://codepen.io/dharafyre/pen/GXgvvd](https://codepen.io/dharafyre/pen/GXgvvd)

Informationen zu erweiterten Anpassungen mit dem SDK finden Sie unter [StreamHub-SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 2: API-Implementierung**

* Zum Erstellen benutzerdefinierter Erlebnisse und Datenvisualisierungen können Livefyre-Apps von Grund auf neu erstellt werden. Hierfür lassen sich Livefyre- und Social-Media-Daten mithilfe der Bootstrap- und Stream-API nutzen.

Weitere Bewertungs- und Reviews-APIs finden Sie [hier](https://api.livefyre.com/docs/apis/by-category/ratings-and-reviews).

### Integration der Comments-App-Authentifizierung {#comments-app-authentication-integration-1}

* [Anpassen der Single Sign-on-](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) Integration für AEM Identity Management
* [Identitätsintegration](https://docs.adobe.com/content/help/en/livefyre/implementation/identity-integration/t-about-identity-integration.html) für Authentifizierungsplattformen von Drittanbietern

### Kundenbeispiele {#customer-examples-2}

* [TimeOut](https://www.timeout.com/london/restaurants/forest-bar-kitchen#tab_panel_3)
* [myrecipes](https://www.myrecipes.com/recipe/shrimp-florentine-pasta)
