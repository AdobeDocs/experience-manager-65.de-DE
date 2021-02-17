---
title: Inhaltseigenschaften und Knoten
seo-title: Inhaltseigenschaften und Knoten
description: Folgen Sie dieser Seite, um mehr über Inhaltseigenschaften und Knoten zu erfahren.
seo-description: Folgen Sie dieser Seite, um mehr über Inhaltseigenschaften und Knoten zu erfahren.
uuid: 2dad52c8-5b6c-4b90-8498-62217a9a27fc
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: f5721ddc-df5c-496c-be61-38d1cab63ad4
translation-type: tm+mt
source-git-commit: 50c0bdfc3203410d392e53536bc7cd00245406e5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 26%

---


# Inhaltseigenschaften und Knoten {#content-properties-and-nodes}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Artikel, Banner und Sammlungen werden in AEM als &quot;cq:Pages&quot;dargestellt.

Sie verwenden dieselben allgemeinen Eigenschaften, die in jeder beliebigen Datei &quot;cq:Page&quot;enthalten sind, sowie weitere, unten dargestellte Eigenschaften, die die Metadaten für Adobe Experience Manager (AEM) Mobile On-Demand-Dienste und für die Integration unterstützende Eigenschaften darstellen.

Die folgenden Tabellen beschreiben die Inhaltseigenschaften und -knoten.

## Allgemeine Integrationseigenschaften {#common-integration-properties}

| **Eigenschaftsname** | **Typ** | **Standardwerte oder erwartete Werte** | **Beschreibung** |
|---|---|---|---|
| dps-id | Zeichenfolge |  | von AEM Mobile zugewiesen und von AEM nach dem Hochladen in AEM Mobile oder Import aus AEM Mobile gespeichert |
| dps-resourceType | Zeichenfolge | dps:Artikel | dps:Banner | dps:Sammlung | entity type-Eigenschaft |
| dps-version | Zeichenfolge |  | Version der AEM Mobile-Entität (auch in der vollständigen aemm-id enthalten) |
| dps-lastSynced | Datum  |  | Datum der letzten Synchronisierung/des letzten Imports aus AEM Mobile in AEM |
| dps-lastUploaded | Datum  |  | Datum des letzten Uploads von AEM nach AEM Mobile |
| dps-lastUploadedBy | Zeichenfolge:userid |  | ID-Benutzer, der die letzte Upload-Anforderung von AEM nach AEM Mobile ausgeführt hat |

## Core-Metadateneigenschaften {#core-metadata-properties}

| Eigenschaftsname | Typ | Standardwerte oder erwartete Werte |
|--- |--- |--- |
| dps-title | Zeichenfolge |  |
| dps-shortTitle | Zeichenfolge |  |
| dps-abstract | Zeichenfolge |  |
| dps-shortAbstract | Zeichenfolge |  |
| dps-department | Zeichenfolge |  |
| dps-Kategorie | Zeichenfolge |  |
| dps-keywords | Zeichenfolge[] |  |
| dps-internalKeywords | Zeichenfolge[] |  |
| dps-wichtig | Zeichenfolge[] | Wichtigkeit von {&quot;low&quot;, &quot;normal&quot;, &quot;high&quot;} |

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
| dps-tapAction |  | TapAction von {webLink} |
| dps-tapActionUrl |  |  |

### Sammlungen {#collections}

| Eigenschaftsname | Typ | Standardwerte oder erwartete Werte |
|--- |--- |--- |
| dps-productId | Zeichenfolge |  |
| dps-readingPosition | Zeichenfolge | von {&quot;reset&quot;,&quot;preserve&quot;} |
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
