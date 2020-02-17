---
title: Grundlagen
seo-title: Grundlagen
description: In Communities suchen
seo-description: In Communities suchen
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Grundlagen {#search-essentials}

## Überblick {#overview}

Die Suchfunktion ist eine wesentliche Funktion von AEM Communities. Zusätzlich zu den Suchfunktionen für die [AEM-Plattform](../../help/sites-deploying/queries-and-indexing.md) stellt AEM Communities die [UGC-Such-API](#ugc-search-api) zur Verfügung, um benutzerdefinierte Inhalte zu suchen. UGC verfügt über eindeutige Eigenschaften, da es separat von anderen AEM-Inhalten und Benutzerdaten eingegeben und gespeichert wird.

Für Communities werden im Allgemeinen zwei Dinge gesucht:

* Veröffentlichte Inhalte von Community-Mitgliedern

   * Verwendet die UGC-Such-API von AEM Communities

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Verwendet die Suchfunktionen der AEM-Plattform

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten erstellen, die UGC erstellen oder verwalten.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente müssen die [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) -Methoden verwendet werden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, stellen die erforderlichen [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) her und stellen sicher, dass das Mitglied über die richtigen Berechtigungen für die Anforderung verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften im Zusammenhang mit der Moderation.

Informationen zu den Dienstprogrammmethoden für den Zugriff auf UGC- und ACL-Schattenknoten finden Sie unter [SRP- und UGC Essentials](srp-and-ugc.md) .

## UGC Search API {#ugc-search-api}

Der gemeinsame [UGC-Speicher](working-with-srp.md) wird von einem von mehreren Speicherressourcenanbietern (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere Muttersprache hat. Daher sollte benutzerdefinierter Code unabhängig vom gewählten SRP Methoden aus dem [UGC API-Paket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) verwenden, um die für das ausgewählte SRP geeignete Abfragesprache aufzurufen.

### ASRP-Suchen {#asrp-searches}

Für [ASRP](asrp.md)wird UGC in der Adobe Cloud gespeichert. Während UGC in CRX nicht sichtbar ist, ist die [Moderation](moderate-ugc.md) sowohl in der Autor- als auch in der Veröffentlichungsumgebung verfügbar. Die Verwendung der [UGC-Such-API](#ugc-search-api) funktioniert für ASRP genauso wie für andere SRPs.

Es gibt derzeit keine Tools zur Verwaltung von ASRP-Suchen.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen die [Benennungsanforderungen](#naming-of-custom-properties)eingehalten werden.

### MSRP-Suchen {#msrp-searches}

Für [MSRP](msrp.md)wird UGC in MongoDB gespeichert, das für die Suche mit Solr konfiguriert ist. UGC ist in CRX nicht sichtbar, aber die [Moderation](moderate-ugc.md) ist sowohl in der Autor- als auch in der Veröffentlichungsumgebung verfügbar.

Zu MSRP und Solr:

* Der eingebettete SOL für die AEM-Plattform wird nicht für MSRP verwendet
* Wenn Sie einen Remote-Support für die AEM-Plattform verwenden, kann dieser für MSRP freigegeben werden, sollte jedoch unterschiedliche Sammlungen verwenden
* Solr kann für die Standardsuche oder für die mehrsprachige Suche konfiguriert werden.
* Weitere Informationen zur Konfiguration finden Sie unter [SOFTWARE-Konfiguration](msrp.md#solr-configuration) für MSRP

Benutzerdefinierte Suchfunktionen sollten die [UGC-Suchschnittstelle](#ugc-search-api)verwenden.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen die [Benennungsanforderungen](#naming-of-custom-properties)eingehalten werden.

### JSRP-Suchen {#jsrp-searches}

Bei [JSRP](jsrp.md)wird UGC in [Oak](../../help/sites-deploying/platform.md) gespeichert und ist nur im Repository der AEM-Autor- oder Veröffentlichungsinstanz sichtbar, in der es eingegeben wurde.

Da UGC in der Regel in der Veröffentlichungsumgebung für Produktionssysteme mit mehreren Herausgebern eingegeben wird, muss ein [Veröffentlichungscluster](topologies.md)und nicht eine Veröffentlichungsfarm konfiguriert werden, damit der eingegebene Inhalt von allen Herausgebern sichtbar ist.

Bei JSRP ist in der Veröffentlichungsumgebung eingegebener UGC in der Autorenumgebung nie sichtbar. Somit finden alle [Moderationsaufgaben](moderate-ugc.md) in der Veröffentlichungsumgebung statt.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Suchschnittstelle](#ugc-search-api)verwenden.

#### Indizierung von Eichen {#oak-indexing}

Obwohl Oak-Indizes nicht automatisch für die AEM-Plattformsuche erstellt werden, wurden sie seit AEM 6.2 für AEM Communities hinzugefügt, um die Leistung zu verbessern und die Paginierung bei der Präsentation von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und die Suchvorgänge langsam sind, müssen zusätzliche Indizes für die benutzerdefinierten Eigenschaften erstellt werden, damit sie leistungsfähiger werden. Um die Portabilität zu erhalten, müssen Sie beim Erstellen von durchsuchbaren benutzerdefinierten Eigenschaften die [Benennungsanforderungen](#naming-of-custom-properties) beachten.

Informationen zum Ändern vorhandener Indizes oder zum Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Der [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist in ACS AEM Commons verfügbar. Er umfasst:

* Überblick über vorhandene Indizes
* Möglichkeit zum Initiieren der Neuindizierung

Um die vorhandenen Oak-Indizes in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)anzuzeigen, lautet der Speicherort:

* `/oak:index/socialLucene`

![chlimage_1-235](assets/chlimage_1-235.png)

## Eigenschaften der indizierten Suche {#indexed-search-properties}

### Standardsucheigenschaften {#default-search-properties}

Im Folgenden sind einige der durchsuchbaren Eigenschaften aufgeführt, die für verschiedene Communities-Funktionen verwendet werden:

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
| modifyDate | *Datum* |
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
| chosenantwortet | *Boolesch* |
| tag | *Zeichenfolge* |
| cq:Tag | *Zeichenfolge* |
| author_display_name | *Zeichenfolge* |
| location_t | *Zeichenfolge* |
| parentPath | *Zeichenfolge* |
| parentTitle | *Zeichenfolge* |

### Benennung benutzerdefinierter Eigenschaften {#naming-of-custom-properties}

Wenn Sie benutzerdefinierte Eigenschaften hinzufügen, damit diese Eigenschaften für mit der [UGC-Such-API](#ugc-search-api)erstellte Sorten und Suchen sichtbar sind, ist *erforderlich *um dem Eigenschaftsnamen ein Suffix hinzuzufügen.

Das Suffix ist für Abfragesprachen bestimmt, die ein Schema verwenden:

* Er identifiziert die Eigenschaft als durchsuchbar
* Er identifiziert den Datentyp

Solr ist ein Beispiel für eine Abfragesprache, die ein Schema verwendet.

| **Suffix** | **Datentyp** |
|---|---|
| _b | *Boolesch* |
| _dt | *Kalender* |
| _d | *Double* |
| _tl | *Lang* |
| _S | *Zeichenfolge* |
| _t | *Text* |

**Hinweise:**

* *Text* ist eine tokenisierte Zeichenfolge, *String* nicht. Verwenden Sie *Text* für unscharfe Suchen (mehr wie diese).

* Bei Typen mit mehreren Werten fügen Sie dem Suffix &quot;s&quot;hinzu, z. B.:

   * `viewDate_dt`: single date property
   * `viewDates_dts`: Liste der Datumseigenschaft

## Filter {#filters}

Komponenten, die das [Kommentarsystem](essentials-comments.md) enthalten, unterstützen den Filterparameter zusätzlich zu ihren Endpunkten.

Die Filtersyntax für AND- und OR-Logik wird wie folgt ausgedrückt (wird vor der URL-Kodierung angezeigt):

* Um OR anzugeben, verwenden Sie einen Filterparameter mit kommagetrennten Werten:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* So legen Sie und verwenden Sie mehrere Filterparameter fest:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax wie in der URL, die die Seite &quot;Suchergebnisse&quot;im Handbuch &quot; [Community-Komponenten&quot;öffnet](components-guide.md). Um zu experimentieren, navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren sind:

| EQ | Gleich |
|---|---|
| NE | nicht gleich |
| LT | Kleiner als |
| LTE | kleiner oder gleich |
| GE | Größer als |
| GTE | größer oder gleich |
| WIE | Fuzzy Match |

Es ist wichtig, dass die URL auf die Communities-Komponente (Ressource) und nicht auf die Seite verweist, auf der die Komponente platziert wird:

* Richtig: forum-Komponente
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Falsch: Forum-Seite
   * `/content/community-components/en/forum.social.json`

## SRP-Tools {#srp-tools}

Es gibt ein Adobe Marketing Cloud GitHub-Projekt, das Folgendes enthält:

[AEM Communities SRP Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dieses Repository enthält Tools zum Verwalten von Daten in SRP.

Derzeit gibt es ein Servlet, das die Möglichkeit bietet, alle UGC aus einem SRP zu löschen.

So löschen Sie beispielsweise alle UGC in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr-Abfrage {#solr-query}

Aktivieren Sie die DEBUG-Protokollierung für

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

Die tatsächliche SOR-Abfrage wird im Debug-Protokoll kodiert angezeigt:

Abfrage zum lösen ist: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

Der Wert des `q` Parameters ist die Abfrage. Nach der Dekodierung der URL-Kodierung kann die Abfrage zur weiteren Debugging an das Tool für die Solr-Admin-Abfrage weitergeleitet werden.

## Verwandte Ressourcen {#related-resources}

* [Community-Inhaltsspeicher](working-with-srp.md) - Beschreibt die verfügbaren SRP-Optionen für einen gemeinsamen UGC-Speicher
* [Übersicht über](srp.md) den Speicherressourcen-Provider - Einführung und Übersicht über die Repository-Nutzung
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien
* [SocialUtils Refactoring](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen
* [Komponenten](search.md) für die Suche und Suche - Hinzufügen der UGC-Suchfunktion zu einer Vorlage

