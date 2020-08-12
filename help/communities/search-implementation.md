---
title: Essentials suchen
seo-title: Essentials suchen
description: In Communities suchen
seo-description: In Communities suchen
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
translation-type: tm+mt
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 6%

---


# Essentials suchen {#search-essentials}

## Übersicht {#overview}

Die Suchfunktion ist ein wesentliches Merkmal von AEM Communities. Zusätzlich zu den Suchfunktionen für [AEM Plattformen](../../help/sites-deploying/queries-and-indexing.md) stellt AEM Communities die [UGC-Suchschnittstelle](#ugc-search-api) zur Verfügung, mit der benutzergenerierte Inhalte durchsucht werden können. UGC verfügt über eindeutige Eigenschaften, da es unabhängig von anderen AEM- und Benutzerdaten eingegeben und gespeichert wird.

Für Communities werden im Allgemeinen zwei Dinge gesucht:

* Veröffentlichte Inhalte von Community-Mitgliedern

   * Verwendet die UGC-Such-API von AEM Communities.

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Verwendet die Suchfunktionen der AEM Plattform.

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten erstellen, die UGC erstellen oder verwalten.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente müssen die [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) -Methoden verwendet werden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, stellen die erforderlichen [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) her und stellen sicher, dass das Mitglied über die richtigen Berechtigungen für die Anforderung verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften im Zusammenhang mit der Moderation.

Informationen zu den Dienstprogrammmethoden für den Zugriff auf UGC- und ACL-Schattenknoten finden Sie unter [SRP- und UGC Essentials](srp-and-ugc.md) .

## UGC Search API {#ugc-search-api}

Der gemeinsame [UGC-Speicher](working-with-srp.md) wird von einer Vielzahl von Datenspeicherung Resource Providern (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere Muttersprache hat. Daher sollte benutzerdefinierter Code unabhängig vom gewählten SRP Methoden aus dem [UGC-API-Paket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) verwenden, um die für das jeweilige SRP geeignete Abfrage aufzurufen.

### ASRP-Suchen {#asrp-searches}

Bei [ASRP](asrp.md)wird UGC in der Adobe Cloud gespeichert. Während UGC in CRX nicht sichtbar ist, ist die [Moderation](moderate-ugc.md) sowohl in der Autor- als auch in der Veröffentlichungs-Umgebung verfügbar. The use of the [UGC search API](#ugc-search-api) works for ASRP the same as for other SRPs.

Tools do not currently exist for managing ASRP searches.

When creating custom properties that are searchable, it is necessary to adhere to the [naming requirements](#naming-of-custom-properties).

### MSRP Searches {#msrp-searches}

For [MSRP](msrp.md), UGC is stored in MongoDB configured to use Solr for searching. UGC will not be visible in CRX, but [moderation](moderate-ugc.md) is available from both the author and publish environments.

Regarding MSRP and Solr:

* The embedded Solr for the AEM platform is not used for MSRP.
* If using a remote Solr for the AEM platform, it may be shared with MSRP, but they should use different collections.
* Solr may be configured for standard search or for multilingual search (MLS).
* For configuration details, see [Solr Configuration](msrp.md#solr-configuration) for MSRP.

Custom search features should use the [UGC search API](#ugc-search-api).

When creating custom properties that are searchable, it is necessary to adhere to the [naming requirements](#naming-of-custom-properties).

### JSRP Searches {#jsrp-searches}

For [JSRP](jsrp.md), UGC is stored in [Oak](../../help/sites-deploying/platform.md) and is visible only in the repository of the AEM author or publish instance on which it was entered.

Da UGC in der Regel in der Umgebung &quot;Veröffentlichen&quot;eingegeben wird, muss für Produktionssysteme mit mehreren Herausgebern ein [Veröffentlichungscluster](topologies.md)und nicht eine Veröffentlichungsfarm konfiguriert werden, damit die eingegebenen Inhalte von allen Herausgebern sichtbar sind.

Bei JSRP ist in der Umgebung &quot;Veröffentlichen&quot;eingegebenes UGC in der Autorenversion nie sichtbar. So finden alle [Moderations](moderate-ugc.md) -Aufgaben in der Umgebung der Veröffentlichung statt.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Suchschnittstelle](#ugc-search-api)verwenden.

#### Indizierung von Eichen {#oak-indexing}

Obwohl Oak-Indizes nicht automatisch für die AEM Plattformsuche erstellt werden, wurden sie ab AEM 6.2 für AEM Communities hinzugefügt, um die Leistung zu verbessern und Paginierung bei der Präsentation von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und die Suchvorgänge langsam sind, müssen zusätzliche Indizes für die benutzerdefinierten Eigenschaften erstellt werden, um sie leistungsfähiger zu machen. Um die Portabilität zu erhalten, müssen Sie beim Erstellen von durchsuchbaren benutzerdefinierten Eigenschaften die [Benennungsanforderungen](#naming-of-custom-properties) beachten.

Informationen zum Ändern vorhandener Indizes oder zum Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Der [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist in ACS AEM Commons verfügbar. Er umfasst:

* Eine Ansicht bestehender Indizes.
* Die Möglichkeit, eine Neuindizierung zu starten.

Zur Ansicht der bestehenden Oak-Indizes in der [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)lautet der Speicherort:

* `/oak:index/socialLucene`

![social-lucene](assets/social-lucene.png)

## Eigenschaften der indizierten Suche {#indexed-search-properties}

### Standardsucheigenschaften {#default-search-properties}

Im Folgenden sind einige der durchsuchbaren Eigenschaften aufgeführt, die für verschiedene Communities-Funktionen verwendet werden:

| **Eigenschaft** | **Datentyp** |
|---|---|
| isGekennzeichnet | *Boolesch* |
| isSpam | *Boolesch* |
| lesen | *Boolesch* |
| influence | *Boolesch* |
| attachments | *Boolesch* |
| sentiment | *Lang* |
| flagged | *Boolesch* |
| hinzugefügt | *Datum* |
| modifiedDate | *Datum* |
| state | *Zeichenfolge* |
| userIdentifier | *Zeichenfolge* |
| Antworten | *Lang* |
| jcr:title | *Zeichenfolge* |
| jcr:description | *Zeichenfolge* |
| sling:resourceType | *Zeichenfolge* |
| allowThreadedReply | *Boolesch* |
| isDraft | *Boolesch* |
| publishDate | *Datum* |
| publishJobId | *Zeichenfolge* |
| beantwortet | *Boolesch* |
| chosenanswered | *Boolesch* |
| tag | *Zeichenfolge* |
| cq:Tag | *Zeichenfolge* |
| author_display_name | *Zeichenfolge* |
| location_t | *Zeichenfolge* |
| parentPath | *Zeichenfolge* |
| parentTitle | *Zeichenfolge* |

### Naming of Custom Properties {#naming-of-custom-properties}

When adding custom properties, in order for those properties to be visible to sorts and searches created with the [UGC search API](#ugc-search-api), it is *required* to add a suffix to the property name.

The suffix is for query languages which use a schema:

* It identifies the property as searchable.
* It identifies the data type.

Solr ist ein Beispiel für eine Abfrage, die ein Schema verwendet.

| **Suffix** | **Datentyp** |
|---|---|
| _b | *Boolesch* |
| _dt | *Kalender* |
| _d | *Double* |
| _tl | *Lang* |
| _S | *Zeichenfolge* |
| _t | *Text* |

**Hinweise:**

* *Text* is a tokenized string, *String* is not. Verwenden Sie *Text* für unscharfe Suchen (mehr wie diese).

* Bei Typen mit mehreren Werten fügen Sie dem Suffix &quot;s&quot;hinzu, z. B.:

   * `viewDate_dt`: single date property
   * `viewDates_dts`: liste der Eigenschaft &quot;date&quot;

## Filter {#filters}

Komponenten, die das [Kommentarsystem](essentials-comments.md) enthalten, unterstützen den Filterparameter zusätzlich zu ihren Endpunkten.

Die Filtersyntax für AND- und OR-Logik wird wie folgt ausgedrückt (wird vor der URL-Kodierung angezeigt):

* Um OR anzugeben, verwenden Sie einen Filterparameter mit kommagetrennten Werten:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* So legen Sie und verwenden Sie mehrere Filterparameter fest:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax wie in der URL, die die Seite &quot;Suchergebnisse&quot;im Handbuch &quot; [Community-Komponenten&quot;öffnet](components-guide.md), dargestellt. Um zu experimentieren, navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filter operators are:

| EQ | Gleich |
|---|---|
| NE | nicht gleich |
| LT | Kleiner als |
| LTE | kleiner oder gleich |
| GE | Größer als |
| GTE | größer oder gleich |
| LIKE | Fuzzy Match |

Es ist wichtig, dass die URL auf die Communities-Komponente (Ressource) und nicht auf die Seite verweist, auf der die Komponente platziert wird:

* Richtig: forum-Komponente
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Falsch: Forum-Seite
   * `/content/community-components/en/forum.social.json`

## SRP-Tools {#srp-tools}

Es gibt ein Adobe Marketing Cloud GitHub-Projekt, das Folgendes enthält:

[AEM Communities SRP-Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

This repository contains tools for managing data in SRP.

Currently, there is one servlet that provides the ability to delete all UGC from any SRP.

For example, to delete all UGC in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr-Abfrage {#solr-query}

To help troubleshoot problems with a Solr query, enable DEBUG logging for

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

The actual Solr query will be displayed URL encoded in the debug log:

Query to solr is: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

The value of the `q` parameter is the query. Once the URL encoding is decoded, the query can be passed to the Solr Admin Query tool for further debugging.

## Verwandte Ressourcen {#related-resources}

* [Community Content Storage](working-with-srp.md) - Discusses the available SRP choices for a UGC common store.
* [Storage Resource Provider Overview](srp.md) - Introduction and repository usage overview.
* [Accessing UGC with SRP](accessing-ugc-with-srp.md) - Coding guidelines.
* [SocialUtils Refactoring](socialutils.md) - Utility methods for SRP that replace SocialUtils.
* [Search and Search Results components](search.md) - Adding UGC search feature to a template.

