---
title: Suchgrundlagen
seo-title: Search Essentials
description: Suchen in Communities
seo-description: Search in Communities
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
exl-id: 8af5ee58-19d7-47b6-b45d-e88006703a5d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 7%

---

# Suchgrundlagen {#search-essentials}

## Übersicht {#overview}

Die Suchfunktion ist ein wesentliches Merkmal von AEM Communities. Zusätzlich zu den [AEM Plattformsuche](../../help/sites-deploying/queries-and-indexing.md) Funktionen bietet AEM Communities die [UGC-Such-API](#ugc-search-api) für die Suche nach benutzergenerierten Inhalten (UGC). UGC verfügt über eindeutige Eigenschaften, da es separat von anderen AEM-Inhalten und Benutzerdaten eingegeben und gespeichert wird.

Für Communities werden im Allgemeinen zwei Dinge gesucht:

* Inhalt von Community-Mitgliedern

   * Verwendet die UGC-Such-API von AEM Communities.

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Verwendet die Suchfunktionen der AEM Plattform.

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten erstellen, die benutzergenerierte Inhalte erstellen oder verwalten.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente muss die [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) -Methoden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, stellen die erforderlichen [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) und stellen Sie sicher, dass das Mitglied über die richtigen Berechtigungen für die Anfrage verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften im Zusammenhang mit der Moderation.

Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md) für Informationen zu Dienstprogrammmethoden, die für den Zugriff auf UGC- und ACL-Shadow-Knoten verwendet werden.

## UGC Search API {#ugc-search-api}

Die [UGC Common Store](working-with-srp.md) wird von einem von verschiedenen Speicherressourcenanbietern (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere Muttersprache hat. Daher sollte benutzerdefinierter Code unabhängig vom gewählten SRP Methoden aus dem [UGC API-Paket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*), wodurch die für das ausgewählte SRP geeignete Abfragesprache aufgerufen wird.

### ASRP-Suchvorgänge {#asrp-searches}

Für [ASRP](asrp.md), wird UGC in der Adobe Cloud gespeichert. Während UGC in CRX nicht sichtbar ist, [Moderation](moderate-ugc.md) ist sowohl in der Autoren- als auch in der Veröffentlichungsumgebung verfügbar. Die Verwendung der [UGC-Such-API](#ugc-search-api) funktioniert für ASRP genauso wie für andere SRPs.

Es gibt derzeit keine Tools für die Verwaltung von ASRP-Suchen.

Beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, müssen Sie die [Namensanforderungen](#naming-of-custom-properties).

### MSRP-Suchvorgänge {#msrp-searches}

Für [MSRP](msrp.md), wird UGC in MongoDB gespeichert, das für die Verwendung von Solr für die Suche konfiguriert ist. UGC ist in CRX nicht sichtbar, aber [Moderation](moderate-ugc.md) ist sowohl in der Autoren- als auch in der Veröffentlichungsumgebung verfügbar.

MSRP und Solr:

* Der eingebettete Solr für die AEM Plattform wird nicht für MSRP verwendet.
* Wenn Sie einen Remote-Solr für die AEM-Plattform verwenden, kann er für MSRP freigegeben werden, sollte jedoch unterschiedliche Sammlungen verwenden.
* Solr kann für die Standardsuche oder für die mehrsprachige Suche (MLS) konfiguriert werden.
* Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration](msrp.md#solr-configuration) für MSRP.

Benutzerdefinierte Suchfunktionen sollten [UGC-Such-API](#ugc-search-api).

Beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, müssen Sie die [Namensanforderungen](#naming-of-custom-properties).

### JSRP-Suchvorgänge {#jsrp-searches}

Für [JSRP](jsrp.md), wird UGC in gespeichert. [Oak](../../help/sites-deploying/platform.md) und ist nur im Repository der AEM- oder Veröffentlichungsinstanz sichtbar, in der sie eingegeben wurde.

Da UGC in der Regel in die Veröffentlichungsumgebung eingegeben wird, muss für Produktionssysteme mit mehreren Herausgebern ein [Veröffentlichungscluster](topologies.md), nicht eine Veröffentlichungsfarm, sodass der eingegebene Inhalt für alle Herausgeber sichtbar ist.

Bei JSRP sind in der Veröffentlichungsumgebung eingegebene benutzergenerierte Inhalte in der Autorenumgebung nie sichtbar. Daher alle [Moderation](moderate-ugc.md) Aufgaben finden in der Veröffentlichungsumgebung statt.

Benutzerdefinierte Suchfunktionen sollten [UGC-Such-API](#ugc-search-api).

#### Oak-Indizierung {#oak-indexing}

Oak-Indizes werden zwar nicht automatisch für die AEM-Plattformsuche erstellt, wurden aber seit AEM 6.2 für AEM Communities hinzugefügt, um die Leistung zu verbessern und die Paginierung bei der Präsentation von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und die Suchvorgänge langsam sind, müssen zusätzliche Indizes für die benutzerdefinierten Eigenschaften erstellt werden, um sie leistungsfähiger zu machen. Um die Portabilität zu wahren, halten Sie die [Namensanforderungen](#naming-of-custom-properties) beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind.

Informationen zum Ändern vorhandener Indizes oder Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Die [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist in ACS AEM Commons verfügbar. Es bietet:

* Eine Ansicht der vorhandenen Indizes.
* Die Möglichkeit, die Neuindizierung zu starten.

So zeigen Sie die vorhandenen Oak-Indizes in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md), lautet der Speicherort:

* `/oak:index/socialLucene`

![social-lucene](assets/social-lucene.png)

## Indexierte Sucheigenschaften {#indexed-search-properties}

### Standardsucheigenschaften {#default-search-properties}

Im Folgenden finden Sie einige der durchsuchbaren Eigenschaften, die für verschiedene Communities-Funktionen verwendet werden:

| **Eigenschaft** | **Datentyp** |
|---|---|
| isGekennzeichnet | *Boolesch* |
| isSpam | *Boolesch* |
| lesen | *Boolesch* |
| Einfluss | *Boolesch* |
| attachments | *Boolesch* |
| sentiment | *Lang* |
| markiert | *Boolesch* |
| hinzugefügt | *Datum* |
| modifiedDate | *Datum* |
| state | *Zeichenfolge* |
| userIdentifier | *Zeichenfolge* |
| antworten | *Lang* |
| jcr:title | *Zeichenfolge* |
| jcr:description | *Zeichenfolge* |
| sling:resourceType | *Zeichenfolge* |
| allowThreadedReply | *Boolesch* |
| isDraft | *Boolesch* |
| publishDate | *Datum* |
| publishJobId | *Zeichenfolge* |
| beantwortet | *Boolesch* |
| chosenantwortet | *Boolesch* |
| tag | *Zeichenfolge* |
| cq:Tag | *Zeichenfolge* |
| author_display_name | *Zeichenfolge* |
| location_t | *Zeichenfolge* |
| parentPath | *Zeichenfolge* |
| parentTitle | *Zeichenfolge* |

### Benennung von benutzerdefinierten Eigenschaften {#naming-of-custom-properties}

Wenn Sie benutzerdefinierte Eigenschaften hinzufügen, damit diese Eigenschaften für Sortierungen und Suchen sichtbar sind, die mit der [UGC-Such-API](#ugc-search-api), ist es *erforderlich* , um dem Eigenschaftsnamen ein Suffix hinzuzufügen.

Das Suffix richtet sich an Abfragesprachen, die ein Schema verwenden:

* Sie identifiziert die Eigenschaft als durchsuchbar.
* Er identifiziert den Datentyp.

Solr ist ein Beispiel für eine Abfragesprache, die ein Schema verwendet.

| **Suffix** | **Datentyp** |
|---|---|
| _b | *Boolesch* |
| _dt | *Kalender* |
| _d | *Double* |
| _tl | *Lang* |
| _S | *Zeichenfolge* |
| _t | *Text* |

**Anmerkungen:**

* *Text* eine tokenisierte Zeichenfolge ist, *Zeichenfolge* ist nicht. Verwendung *Text* für unscharfe (mehr wie diese) Suchen.

* Fügen Sie dem Suffix für Typen mit mehreren Werten &quot;s&quot;hinzu, z. B.:

   * `viewDate_dt`: Einzeldatumseigenschaft
   * `viewDates_dts`: Liste der Datumseigenschaften

## Filter {#filters}

Komponenten, die die [Kommentarsystem](essentials-comments.md) unterstützt den Filterparameter, der zu seinen Endpunkten hinzugefügt wird.

Die Filtersyntax für die UND- und ODER-Logik lautet wie folgt (wird angezeigt, bevor sie URL-codiert wird):

* So geben Sie OR einen Filterparameter mit kommagetrennten Werten an:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* So legen Sie UND mehrere Filterparameter fest:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax, wie in der URL zu sehen ist, die die Seite &quot;Suchergebnisse&quot;in der [Handbuch zu Community-Komponenten](components-guide.md). Um zu experimentieren, navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren sind:

| EQ | Gleich |
|---|---|
| NE | nicht gleich |
| LT | Kleiner als |
| LTE | kleiner oder gleich |
| GE | Größer als |
| GTE | größer oder gleich |
| LIKE | Fuzzy Match |

Es ist wichtig, dass die URL auf die Communities-Komponente (Ressource) verweist und nicht auf die Seite, auf der die Komponente platziert wird:

* Richtig: Forumskomponente
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Falsch: Forumsseite
   * `/content/community-components/en/forum.social.json`

## SRP-Tools {#srp-tools}

Es gibt ein Adobe Marketing Cloud GitHub-Projekt, das Folgendes enthält:

[AEM Communities SRP-Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dieses Repository enthält Tools zum Verwalten von Daten in SRP.

Derzeit gibt es ein Servlet, das die Möglichkeit bietet, alle benutzergenerierten Inhalte aus einem SRP zu löschen.

So löschen Sie beispielsweise alle benutzergenerierten Inhalte in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr Query {#solr-query}

Um Probleme mit einer Solr-Abfrage zu beheben, aktivieren Sie die DEBUG-Protokollierung für

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

Die tatsächliche Solr-Abfrage wird im Debug-Protokoll als URL-kodiert angezeigt:

Die Abfrage an Solr lautet: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

Der Wert der `q` -Parameter ist die Abfrage. Sobald die URL-Kodierung dekodiert wurde, kann die Abfrage zur weiteren Fehlerbehebung an das Solr Admin Query Tool übergeben werden.

## Verwandte Ressourcen {#related-resources}

* [Community-Inhaltsspeicherung](working-with-srp.md) - Beschreibt die verfügbaren SRP-Optionen für einen gemeinsamen UGC-Speicher.
* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Kodierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Komponenten für Such- und Suchergebnisse](search.md) - Hinzufügen der UGC-Suchfunktion zu einer Vorlage.
