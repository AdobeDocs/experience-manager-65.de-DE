---
title: Inhaltseigenschaften und Knoten
description: Auf dieser Seite erfahren Sie mehr über Inhaltseigenschaften und Knoten.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 05c8c846-69cc-4075-9149-33890b3d1e08
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 22%

---

# Inhaltseigenschaften und Knoten {#content-properties-and-nodes}

{{ue-over-mobile}}

Artikel, Banner und Sammlungen werden in AEM als cq:Pages dargestellt.

Sie verwenden dieselben gemeinsamen Eigenschaften in jeder cq:Page zusätzlich zu mehreren anderen, die unten gezeigt werden und die Metadaten und Integrationseigenschaften von Adobe Experience Manager (AEM) Mobile On-Demand-Services darstellen.

In den folgenden Tabellen werden die Inhaltseigenschaften und -knoten beschrieben.

## Allgemeine Integrationseigenschaften {#common-integration-properties}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** | **Beschreibung** |
|---|---|---|---|
| dps-id | Zeichenfolge |  | Von AEM Mobile zugewiesen und nach dem Hochladen in AEM Mobile oder dem Import aus AEM Mobile über AEM gespeichert |
| dps-resourceType | Zeichenfolge | dps:Artikel | dps:Banner | dps:Sammlung | Entitätstyp-Eigenschaft |
| dps-version | Zeichenfolge |  | Version der AEM Mobile-Entität (auch in der vollständigen AEM-ID enthalten) |
| dps-lastSynced | Datum |  | Datum der letzten Synchronisierung/des letzten Imports aus AEM Mobile in AEM |
| dps-lastUploaded | Datum |  | Datum des letzten Uploads von AEM nach AEM Mobile |
| dps-lastUploadedBy | string:userId |  | ID des Benutzers, der die letzte Upload-Anfrage von AEM an AEM Mobile ausgeführt hat |

## Core-Metadateneigenschaften {#core-metadata-properties}

| Eigenschaftsname | Typ | Standardwerte für erwartete Werte |
|--- |--- |--- |
| dps-title | Zeichenfolge |  |
| dps-shortTitle | Zeichenfolge |  |
| dps-abstract | Zeichenfolge |  |
| dps-shortAbstract | Zeichenfolge |  |
| dps-department | Zeichenfolge |  |
| dps-category | Zeichenfolge |  |
| dps-keywords | Zeichenfolge[] |  |
| dps-internalKeywords | Zeichenfolge[] |  |
| DPS-Wichtigkeit | Zeichenfolge[] | Wichtigkeit von {„niedrig“, „normal“, „hoch“} |

### Artikel {#articles}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** |
|---|---|---|
| dps-author | Zeichenfolge |  |
| dps-authorURL | Zeichenfolge |  |
| dps-hideFromBrowsePage | Boolesch |  |
| dps-access | Zeichenfolge | ProtectedAccess von {„protected“, „metered“, „free“} |
| **Sozial** |  |  |
| dps-socialShareURL | Zeichenfolge |  |
| dps-articleText | Zeichenfolge |  |
| dps-url | Zeichenfolge |  |

### Banner {#banners}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** |
|---|---|---|
| dps-tapAction |  | Tippen Sie auf Aktion aus {webLink} |
| dps-tapActionUrl |  |  |

### Sammlungen {#collections}

| Eigenschaftsname | Typ | Standardwerte für erwartete Werte |
|--- |--- |--- |
| dps-productId | Zeichenfolge |  |
| dps-readingPosition | Zeichenfolge | von {„Zurücksetzen“,„Beibehalten“} |
| dps-horizontalSwipe | Boolesch |  |
| dps-allowDownload | Boolesch |  |
| dps-openDefault | Zeichenfolge | von {„browsePage“,„contentView“} |
| dps-layout | Zeichenfolge |  |

## Inhaltsknoten {#content-nodes}

### Allgemeine Knoten {#common-nodes}

| Knotenname | Typ | Standardwerte für erwartete Werte | Beschreibung |
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
