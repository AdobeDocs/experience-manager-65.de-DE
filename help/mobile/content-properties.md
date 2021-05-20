---
title: Inhaltseigenschaften und Knoten
seo-title: Inhaltseigenschaften und Knoten
description: Auf dieser Seite erfahren Sie mehr über Inhaltseigenschaften und -knoten.
seo-description: Auf dieser Seite erfahren Sie mehr über Inhaltseigenschaften und -knoten.
uuid: 2dad52c8-5b6c-4b90-8498-62217a9a27fc
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: f5721ddc-df5c-496c-be61-38d1cab63ad4
exl-id: 05c8c846-69cc-4075-9149-33890b3d1e08
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 26%

---

# Inhaltseigenschaften und Knoten {#content-properties-and-nodes}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Artikel, Banner und Sammlungen werden in AEM als cq:Pages dargestellt.

Sie verwenden dieselben allgemeinen Eigenschaften, die in jeder cq:Page vorhanden sind, sowie mehrere andere, die unten angezeigt werden und die Adobe Experience Manager (AEM) Mobile On-Demand Services-Metadaten und Integrationsunterstützungseigenschaften darstellen.

In den folgenden Tabellen werden die Inhaltseigenschaften und -knoten beschrieben.

## Allgemeine Integrationseigenschaften {#common-integration-properties}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** | **Beschreibung** |
|---|---|---|---|
| dps-id | Zeichenfolge |  | von AEM Mobile zugewiesen und nach dem Hochladen in AEM Mobile von AEM gespeichert oder aus AEM Mobile importiert |
| dps-resourceType | Zeichenfolge | dps:Artikel | dps:Banner | dps:Sammlung | Entitätstyp-Eigenschaft |
| dps-version | Zeichenfolge |  | Version der AEM Mobile-Entität (ebenfalls in der vollständigen aemm-id enthalten) |
| dps-lastSynced | Datum |  | Datum der letzten Synchronisierung/des letzten Imports aus AEM Mobile in AEM |
| dps-lastUploaded | Datum |  | Datum des letzten Uploads von AEM in AEM Mobile |
| dps-lastUploadedBy | Zeichenfolge: userid |  | ID-Benutzer, der die letzte Upload-Anfrage von AEM auf AEM Mobile ausgeführt hat |

## Core-Metadateneigenschaften {#core-metadata-properties}

| Eigenschaftsname | Typ | Standardwerte oder erwartete Werte |
|--- |--- |--- |
| dps-title | Zeichenfolge |  |
| dps-shortTitle | Zeichenfolge |  |
| dps-abstract | Zeichenfolge |  |
| dps-shortAbstract | Zeichenfolge |  |
| dps-department | Zeichenfolge |  |
| dps-category | Zeichenfolge |  |
| dps-keywords | Zeichenfolge[] |  |
| dps-internalKeywords | Zeichenfolge[] |  |
| dps-important | Zeichenfolge[] | Wichtigkeit von {&quot;low&quot;, &quot;normal&quot;, &quot;high&quot;} |

### Artikel {#articles}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** |
|---|---|---|
| dps-author | Zeichenfolge |  |
| dps-authorURL | Zeichenfolge |  |
| dps-hideFromBrowsePage | Boolesch |  |
| dps-access | Zeichenfolge | ProtectedAccess von {&quot;protected&quot;, &quot;metered&quot;, &quot;free&quot;} |
| **Social** |  |  |
| dps-socialShareURL | Zeichenfolge |  |
| dps-articleText | Zeichenfolge |  |
| dps-url | Zeichenfolge |  |

### Banner {#banners}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** |
|---|---|---|
| dps-tapAction |  | Tippen Sie auf Aktion von {webLink} |
| dps-tapActionUrl |  |  |

### Sammlungen {#collections}

| Eigenschaftsname | Typ | Standardwerte oder erwartete Werte |
|--- |--- |--- |
| dps-productId | Zeichenfolge |  |
| dps-readingPosition | Zeichenfolge | von {&quot;reset&quot;,&quot;keep&quot;} |
| dps-horizontalSwipe | Boolesch |  |
| dps-allowDownload | Boolesch |  |
| dps-openDefault | Zeichenfolge | von {&quot;browsePage&quot;,&quot;contentView&quot;} |
| dps-layout | Zeichenfolge |  |

## Inhaltsknoten {#content-nodes}

### Allgemeine Knoten {#common-nodes}

| Knotenname | Typ | Standardwerte oder erwartete Werte | Beschreibung |
|--- |--- |--- |--- |
| image | jcr:primaryType=nt:unstructured <br> sling:resourceType=foundation/components/image |  |  |

### Entitäten {#entities}

#### Artikel {#articles-1}

| Knotenname | Typ | Standardwerte für erwartete Werte | Beschreibung |
|--- |--- |--- |--- |
| social-share-image |  | jcr:primaryType=nt:unstructured <br> sling:resourceType=foundation/components/image |  |

#### Banner {#banners-1}

| Knotenname | Typ | Standardwerte für erwartete Werte | Beschreibung |
|---|---|---|---|
| nicht vorhanden |  |  |  |

#### Sammlungen {#collections-1}

| Knotenname | Typ | Standardwerte für erwartete Werte | Beschreibung |
|--- |--- |--- |--- |
| background-image | jcr:primaryType=nt:unstructured <br> sling:resourceType=foundation/components/image |  |  |
