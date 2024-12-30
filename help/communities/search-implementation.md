---
title: Grundlagen suchen
description: Erfahren Sie mehr über die Suchfunktion, die eine wichtige Funktion von AEM Communities ist. Communities bietet auch die Such-API für benutzergenerierte Inhalte.
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

# Grundlagen suchen {#search-essentials}

## Überblick {#overview}

Die Suchfunktion ist eine wichtige Funktion von Adobe Experience Manager (AEM) Communities. Zusätzlich zu den Funktionen der [AEM](../../help/sites-deploying/queries-and-indexing.md)Plattformsuche stellt AEM Communities die [UGC-Such-API](#ugc-search-api) für die Suche nach benutzergenerierten Inhalten (UGC) bereit. UGC verfügt über eindeutige Eigenschaften, da sie getrennt von anderen AEM-Inhalten und Benutzerdaten eingegeben und gespeichert werden.

Für Communities werden im Allgemeinen die beiden folgenden Elemente durchsucht:

* Von Community-Mitgliedern geposteter Inhalt

   * Sie verwendet die UGC-Such-API von AEM Communities.

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Sie verwendet die Suchfunktionen der AEM-Plattform.

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten zum Erstellen oder Verwalten von benutzergenerierten Inhalten erstellen.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente müssen die Methoden [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) verwendet werden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, legen die erforderlichen [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) fest und stellen sicher, dass der Member über die richtigen Berechtigungen für die Anfrage verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften, die sich auf die Moderation beziehen.

Siehe [SRP und UGC Essentials](srp-and-ugc.md) für Informationen zu Dienstprogrammmethoden, die für den Zugriff auf UGC- und ACL-Shadow-Knoten verwendet werden.

## UGC Search-API {#ugc-search-api}

Der [UGC Common Store](working-with-srp.md) wird von einem von verschiedenen Speicherressourcenanbietern (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere native Abfragesprache aufweist. Daher sollte benutzerdefinierter Code unabhängig vom ausgewählten SRP Methoden aus dem [UGC-API-Paket](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) verwenden, das die für das ausgewählte SRP geeignete Abfragesprache aufruft.

### ASRP-Suchen {#asrp-searches}

Bei [ASRP](asrp.md) wird UGC in der Adobe-Cloud gespeichert. Während benutzergenerierter Inhalt in CRX nicht sichtbar ist[ ist ](moderate-ugc.md)Moderation“ sowohl in der Authoring- als auch in der Publish-Umgebung verfügbar. Die Verwendung der [UGC Search API](#ugc-search-api) funktioniert für ASRP genauso wie für andere SRPs.

Für die Verwaltung von ASRP-Suchen gibt es derzeit keine Tools.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen Sie die [Namensanforderungen“ ](#naming-of-custom-properties).

### MSRP-Suchen {#msrp-searches}

Bei [MSRP](msrp.md) wird der UGC in MongoDB gespeichert, das für die Verwendung von Solr für die Suche konfiguriert ist. UGC ist in CRX nicht sichtbar, aber [Moderation](moderate-ugc.md) ist sowohl in der Authoring- als auch in der Publish-Umgebung verfügbar.

Zu MSRP und Solr:

* Das eingebettete Solr für die AEM-Plattform wird nicht für MSRP verwendet.
* Wenn Sie eine Remote-Solr für die AEM-Plattform verwenden, kann diese für MSRP freigegeben werden, es sollten jedoch andere Sammlungen verwendet werden.
* Solr kann für die Standardsuche oder die mehrsprachige Suche (MLS) konfiguriert werden.
* Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration](msrp.md#solr-configuration) für MSRP.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Such-API](#ugc-search-api) verwenden.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen Sie die [Namensanforderungen“ ](#naming-of-custom-properties).

### JSRP-Suchen {#jsrp-searches}

Bei [JSRP](jsrp.md) wird der benutzergenerierte Inhalt (UGC) in [Oak](../../help/sites-deploying/platform.md) gespeichert und ist nur im Repository der AEM-Autoren- oder Publish-Instanz sichtbar, in der er eingegeben wurde.

Da benutzergenerierter Inhalt normalerweise in der Publish-Umgebung eingegeben wird, ist es bei Produktionssystemen mit mehreren Herausgebern erforderlich, einen [Veröffentlichungs-Cluster](topologies.md) und keine Veröffentlichungsfarm zu konfigurieren, damit der eingegebene Inhalt von allen Herausgebern sichtbar ist.

Bei JSRP ist der in der Publish-Umgebung eingegebene benutzergenerierte Inhalt nie in der Autorenumgebung sichtbar. Daher finden alle [Moderationsaufgaben](moderate-ugc.md) in der Publish-Umgebung statt.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Such-API](#ugc-search-api) verwenden.

#### Oak-Indizierung {#oak-indexing}

Oak-Indizes werden zwar seit AEM 6.2 nicht automatisch für die AEM-Plattformsuche erstellt, aber sie wurden für AEM Communities hinzugefügt, um die Leistung zu verbessern und die Paginierung bei der Darstellung von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und Suchvorgänge langsam sind, müssen zusätzliche Indizes für die benutzerdefinierten Eigenschaften erstellt werden, um sie leistungsfähiger zu machen. Um die Portabilität zu gewährleisten, müssen Sie die [Benennungsanforderungen](#naming-of-custom-properties) beim Erstellen von benutzerdefinierten Eigenschaften beachten, die durchsuchbar sind.

Informationen zum Ändern vorhandener Indizes oder Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und -Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Der [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist über ACS AEM Commons verfügbar. Es bietet:

* Eine Ansicht der vorhandenen Indizes.
* Die Möglichkeit, eine Neuindizierung zu starten.

Um die vorhandenen Oak-Indizes in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) anzuzeigen, lautet der Speicherort:

* `/oak:index/socialLucene`

![social-lucene](assets/social-lucene.png)

## Indizierte Sucheigenschaften {#indexed-search-properties}

### Standardsucheigenschaften {#default-search-properties}

Im Folgenden finden Sie einige durchsuchbare Eigenschaften, die für verschiedene Communities-Funktionen verwendet werden:

| **Eigenschaft** | **Datentyp** |
|---|---|
| isFlagged | *Boolesch* |
| isSpam | *Boolesch* |
| lesen | *Boolesch* |
| beeinflussen | *Boolesch* |
| Anhänge | *Boolesch* |
| Überzeugung | *Lang* |
| markiert | *Boolesch* |
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
| Ausgewählte Antworten | *Boolesch* |
| tag | *Zeichenfolge* |
| cq:Tag | *Zeichenfolge* |
| author_display_name | *Zeichenfolge* |
| location_t | *Zeichenfolge* |
| parentPath | *Zeichenfolge* |
| parentTitle | *Zeichenfolge* |

### Benennung benutzerdefinierter Eigenschaften {#naming-of-custom-properties}

Wenn Sie benutzerdefinierte Eigenschaften hinzufügen, müssen diese Eigenschaften dem Eigenschaftsnamen ein Suffix hinzufügen, damit sie für Sortierungen und Suchen sichtbar sind[ ](#ugc-search-api) die mit der UGC *Such* API erstellt wurden.

Das Suffix bezieht sich auf Abfragesprachen, die ein Schema verwenden:

* Dadurch wird die Eigenschaft als durchsuchbar identifiziert.
* Er identifiziert den Datentyp.

Solr ist ein Beispiel für eine Abfragesprache, die ein Schema verwendet.

| **Suffix** | **Datentyp** |
|---|---|
| _b | *Boolesch* |
| _dt | *Kalender* |
| _d | *Doppelt* |
| _tl | *Lang* |
| _s | *Zeichenfolge* |
| _t | *Text* |

**Anmerkungen:**

* *Text* ist eine mit einem Token versehene Zeichenfolge, *String* nicht. Verwenden Sie *Text* für unscharfe Suchen (mehr wie diese).

* Bei Typen mit mehreren Werten fügen Sie dem Suffix „s“ hinzu, z. B.:

   * `viewDate_dt`: Einzeldatumseigenschaft
   * `viewDates_dts`: Liste der Datumseigenschaften

## Filter {#filters}

Komponenten, die das [Kommentarsystem](essentials-comments.md) enthalten, unterstützen den Filterparameter zusätzlich zu ihren Endpunkten.

Die Filtersyntax für die Logik AND und OR wird wie folgt ausgedrückt (vor der URL-Kodierung angezeigt):

* So geben Sie ODER an und verwenden einen Filterparameter mit durch Kommas getrennten Werten:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* So geben Sie UND an und verwenden mehrere Filterparameter:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax, die in der URL zu sehen ist, die die Seite mit den Suchergebnissen im [Community-Komponenten-Handbuch](components-guide.md) öffnet. Zum Experimentieren navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren sind:

| ÄQ | gleich |
|---|---|
| NE | Ungleich |
| LT | Weniger als |
| LTE | Kleiner oder gleich |
| GE | Größer als |
| GTE | Größer oder gleich |
| LIKE | Fuzzy Match |

Es ist wichtig, dass die URL auf die Communities-Komponente (Ressource) verweist und nicht auf die Seite, auf der die Komponente platziert ist:

* Richtig: Forenkomponente
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Falsch: Forumsseite
   * `/content/community-components/en/forum.social.json`

## SRP-Tools {#srp-tools}

Es gibt ein Adobe Experience Cloud-GitHub-Projekt, das Folgendes enthält:

[AEM Communities SRP-Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dieses Repository enthält Tools zum Verwalten von Daten in SRP.

Derzeit gibt es ein Servlet, das alle benutzergenerierten Inhalte aus jedem SRP löschen kann.

So löschen Sie beispielsweise alle benutzergenerierten Inhalte in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr-Abfrage {#solr-query}

Um Probleme mit einer Solr-Abfrage zu beheben, aktivieren Sie die DEBUG-Protokollierung für

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

Die eigentliche Solr-Abfrage wird als URL codiert im Debug-Protokoll angezeigt:

Abfrage an Solr lautet: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

Der Wert des `q` ist die Abfrage. Sobald die URL-Codierung decodiert ist, kann die Abfrage zur weiteren Fehlerbehebung an das Solr Admin Query Tool übergeben werden.

## Verwandte Ressourcen {#related-resources}

* [Community-Inhaltsspeicher](working-with-srp.md) - Erläutert die verfügbaren SRP-Optionen für einen gemeinsamen Speicher für benutzergenerierten Inhalt.
* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Komponenten „Suche und Suchergebnisse](search.md) - Hinzufügen der UGC-Suchfunktion zu einer Vorlage.
