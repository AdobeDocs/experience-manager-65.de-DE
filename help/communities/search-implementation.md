---
title: Suchgrundlagen
description: Erfahren Sie mehr über die Suchfunktion, die eine wichtige Funktion von AEM Communities ist. Communities stellen auch die Such-API für benutzergenerierte Inhalte bereit.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8af5ee58-19d7-47b6-b45d-e88006703a5d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 4%

---

# Suchgrundlagen {#search-essentials}

## Überblick {#overview}

Die Suchfunktion ist eine wesentliche Funktion von Adobe Experience Manager (AEM) Communities. Zusätzlich zu den Funktionen für die [AEM Plattformsuche](../../help/sites-deploying/queries-and-indexing.md) stellt AEM Communities die [UGC-Such-API](#ugc-search-api) für die Suche nach benutzergenerierten Inhalten (UGC) bereit. UGC verfügt über eindeutige Eigenschaften, da es separat von anderen AEM-Inhalten und Benutzerdaten eingegeben und gespeichert wird.

Für Communities werden im Allgemeinen zwei Dinge gesucht:

* Inhalt von Community-Mitgliedern

   * Es verwendet die UGC-Such-API von AEM Communities.

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Es verwendet die Suchfunktionen der AEM Plattform.

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten erstellen, die benutzergenerierte Inhalte erstellen oder verwalten.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente müssen die Methoden [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) verwendet werden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, stellen die erforderlichen [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) her und stellen sicher, dass das Mitglied über die richtigen Berechtigungen für die Anfrage verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften im Zusammenhang mit der Moderation.

Informationen zu Dienstprogrammmethoden, die für den Zugriff auf UGC- und ACL-Shadow-Knoten verwendet werden, finden Sie unter [SRP und UGC Essentials](srp-and-ugc.md) .

## UGC Search API {#ugc-search-api}

Der gemeinsame Speicher [UGC](working-with-srp.md) wird von einem der verschiedenen Speicherressourcenanbieter (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere Muttersprache hat. Daher sollte benutzerdefinierter Code unabhängig vom ausgewählten SRP Methoden aus dem [UGC API-Paket](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) verwenden, die die für das ausgewählte SRP geeignete Abfragesprache aufrufen.

### ASRP-Suchvorgänge {#asrp-searches}

Für [ASRP](asrp.md) wird UGC in der Adobe-Cloud gespeichert. Während UGC in CRX nicht sichtbar ist, ist [Moderation](moderate-ugc.md) sowohl in der Autoren- als auch in der Publish-Umgebung verfügbar. Die Verwendung der [UGC Search API](#ugc-search-api) funktioniert für ASRP genauso wie für andere SRPs.

Es gibt derzeit keine Tools für die Verwaltung von ASRP-Suchen.

Beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, müssen die [Benennungsanforderungen](#naming-of-custom-properties) erfüllt werden.

### MSRP-Suchvorgänge {#msrp-searches}

Für [MSRP](msrp.md) wird UGC in MongoDB gespeichert, das für die Verwendung von Solr für die Suche konfiguriert ist. UGC ist in CRX nicht sichtbar, aber [Moderation](moderate-ugc.md) ist sowohl in der Autoren- als auch in der Publish-Umgebung verfügbar.

MSRP und Solr:

* Der eingebettete Solr für die AEM Plattform wird nicht für MSRP verwendet.
* Wenn Sie einen Remote-Solr für die AEM-Plattform verwenden, kann er für MSRP freigegeben werden, sollte jedoch unterschiedliche Sammlungen verwenden.
* Solr kann für die Standardsuche oder für die mehrsprachige Suche (MLS) konfiguriert werden.
* Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration](msrp.md#solr-configuration) für MSRP.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Such-API](#ugc-search-api) verwenden.

Beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, müssen die [Benennungsanforderungen](#naming-of-custom-properties) erfüllt werden.

### JSRP-Suchvorgänge {#jsrp-searches}

Für [JSRP](jsrp.md) wird UGC in [Oak](../../help/sites-deploying/platform.md) gespeichert und ist nur im Repository der AEM- oder Publish-Instanz sichtbar, in der sie eingegeben wurde.

Da UGC in der Regel in die Publish-Umgebung eingegeben wird, muss für Produktionssysteme mit mehreren Herausgebern ein [Veröffentlichungs-Cluster](topologies.md) konfiguriert werden, nicht eine Veröffentlichungsfarm, damit der eingegebene Inhalt für alle Herausgeber sichtbar ist.

Bei JSRP sind in der Publish-Umgebung eingegebene benutzergenerierte Inhalte nie in der Autorenumgebung sichtbar. Daher finden alle [Moderationsaufgaben](moderate-ugc.md) in der Publish-Umgebung statt.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Such-API](#ugc-search-api) verwenden.

#### Oak-Indizierung {#oak-indexing}

Oak-Indizes werden zwar ab AEM 6.2 nicht automatisch für die AEM-Plattformsuche erstellt, doch wurden sie für AEM Communities hinzugefügt, um die Leistung zu verbessern und die Paginierung bei der Präsentation von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und die Suchvorgänge langsam sind, müssen zusätzliche Indizes für die benutzerdefinierten Eigenschaften erstellt werden, um sie leistungsfähiger zu machen. Um die Portabilität zu wahren, halten Sie beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, die [Namensanforderungen](#naming-of-custom-properties) ein.

Informationen zum Ändern vorhandener Indizes oder Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und -Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Der [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist in ACS AEM Commons verfügbar. Es bietet:

* Eine Ansicht der vorhandenen Indizes.
* Die Möglichkeit, die Neuindizierung zu starten.

Um die vorhandenen Oak-Indizes in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) anzuzeigen, lautet der Speicherort:

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
| Anlagen | *Boolesch* |
| sentiment | *Long* |
| markiert | *Boolesch* |
| hinzugefügt | *Datum* |
| modifiedDate | *Datum* |
| state | *Zeichenfolge* |
| userIdentifier | *Zeichenfolge* |
| antworten | *Long* |
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

### Benennung benutzerdefinierter Eigenschaften {#naming-of-custom-properties}

Wenn Sie benutzerdefinierte Eigenschaften hinzufügen, damit diese Eigenschaften für Sorten und Suchen sichtbar sind, die mit der [UGC-Such-API](#ugc-search-api) erstellt wurden, muss *erforderlich* ein Suffix zum Eigenschaftsnamen hinzugefügt werden.

Das Suffix richtet sich an Abfragesprachen, die ein Schema verwenden:

* Sie identifiziert die Eigenschaft als durchsuchbar.
* Er identifiziert den Datentyp.

Solr ist ein Beispiel für eine Abfragesprache, die ein Schema verwendet.

| **Suffix** | **Datentyp** |
|---|---|
| _b | *Boolesch* |
| _dt | *Kalender* |
| _d | *Double* |
| _tl | *Long* |
| _s | *Zeichenfolge* |
| _t | *Text* |

**Anmerkungen:**

* *Text* ist eine tokenisierte Zeichenfolge, *String* nicht. Verwenden Sie *Text* für unscharfe Suchen (mehr wie diese).

* Fügen Sie dem Suffix für Typen mit mehreren Werten &quot;s&quot;hinzu, beispielsweise:

   * `viewDate_dt`: Eigenschaft für ein einzelnes Datum
   * `viewDates_dts`: list of dates property

## Filter {#filters}

Komponenten, die das [Kommentarsystem](essentials-comments.md) enthalten, unterstützen den Filterparameter zusätzlich zu den Endpunkten.

Die Filtersyntax für die UND- und ODER-Logik lautet wie folgt (wird angezeigt, bevor sie URL-codiert wird):

* So geben Sie OR einen Filterparameter mit kommagetrennten Werten an:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* So geben Sie UND verwenden mehrere Filterparameter an:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax, wie sie in der URL angezeigt wird, die die Seite &quot;Suchergebnisse&quot;im [Leitfaden zu Community-Komponenten](components-guide.md) öffnet. Um zu experimentieren, navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren sind:

| EQ | gleich |
|---|---|
| NE | nicht gleich |
| LT | kleiner als |
| LTE | kleiner als oder gleich |
| GE | größer als |
| GTE | größer als oder gleich |
| LIKE | Fuzzy Match |

Es ist wichtig, dass die URL auf die Communities-Komponente (Ressource) verweist und nicht auf die Seite, auf der die Komponente platziert wird:

* Richtig: Forumkomponente
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Falsch: Forumsseite
   * `/content/community-components/en/forum.social.json`

## SRP-Tools {#srp-tools}

Es gibt ein Adobe Experience Cloud GitHub-Projekt, das Folgendes enthält:

[AEM Communities SRP-Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dieses Repository enthält Tools zum Verwalten von Daten in SRP.

Derzeit gibt es ein Servlet, das alle benutzergenerierten Inhalte aus einem beliebigen SRP löschen kann.

So löschen Sie beispielsweise alle benutzergenerierten Inhalte in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr Query {#solr-query}

Um Probleme mit einer Solr-Abfrage zu beheben, aktivieren Sie DEBUG-Protokollierung für

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

Die tatsächliche Solr-Abfrage wird in der URL angezeigt, die im Debug-Protokoll kodiert ist:

Die zu lösende Abfrage lautet: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

Der Wert des Parameters `q` ist die Abfrage. Sobald die URL-Kodierung dekodiert wurde, kann die Abfrage zur weiteren Fehlerbehebung an das Solr Admin Query Tool übergeben werden.

## Verwandte Ressourcen {#related-resources}

* [Community-Inhaltsspeicher](working-with-srp.md) - Beschreibt die verfügbaren SRP-Optionen für einen gemeinsamen UGC-Speicher.
* [Übersicht über den Speicheranbieter](srp.md) - Übersicht über die Einführung und die Repository-Nutzung.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Komponenten für Suche und Suchergebnisse](search.md) - Hinzufügen der UGC-Suchfunktion zu einer Vorlage.
