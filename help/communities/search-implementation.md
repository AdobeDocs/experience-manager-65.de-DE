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
source-git-commit: 9a4ae73c08657195da2741cccdb196bd7f7142c9
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 6%

---


# Essentials suchen {#search-essentials}

## Überblick {#overview}

Die Suchfunktion ist ein wesentliches Merkmal von AEM Communities. Zusätzlich zu den Funktionen [AEM Plattformsuche](../../help/sites-deploying/queries-and-indexing.md) stellt AEM Communities die [UGC-Such-API](#ugc-search-api) zum Durchsuchen benutzergenerierter Inhalte (UGC) bereit. UGC verfügt über eindeutige Eigenschaften, da es unabhängig von anderen AEM- und Benutzerdaten eingegeben und gespeichert wird.

Für Communities werden im Allgemeinen zwei Dinge gesucht:

* Veröffentlichte Inhalte von Community-Mitgliedern

   * Verwendet die UGC-Such-API von AEM Communities.

* Benutzer und Benutzergruppen (Benutzerdaten)

   * Verwendet die Suchfunktionen der AEM Plattform.

Dieser Abschnitt der Dokumentation ist für Entwickler von Interesse, die benutzerdefinierte Komponenten erstellen, die UGC erstellen oder verwalten.

## Sicherheits- und Schattenknoten {#security-and-shadow-nodes}

Für eine benutzerdefinierte Komponente müssen Sie die Methoden [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) verwenden. Die Dienstprogrammmethoden, die UGC erstellen und suchen, stellen die erforderlichen [shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) her und stellen sicher, dass das Mitglied über die richtigen Berechtigungen für die Anforderung verfügt.

Was nicht über die SRP-Dienstprogramme verwaltet wird, sind Eigenschaften im Zusammenhang mit der Moderation.

Weitere Informationen zu Dienstprogrammmethoden für den Zugriff auf UGC- und ACL-Schattenknoten finden Sie unter [SRP und UGC Essentials](srp-and-ugc.md).

## UGC Search API {#ugc-search-api}

Der gemeinsame Speicher [UGC](working-with-srp.md) wird von einem von verschiedenen Datenspeicherung Resource Providern (SRPs) bereitgestellt, von denen jeder möglicherweise eine andere Sprache für die native Abfrage hat. Deshalb sollte benutzerdefinierter Code unabhängig von der gewählten SRP Methoden aus dem [UGC API-Paket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) verwenden, das die für die jeweilige SRP geeignete Abfrage aufruft.

### ASRP-Suchen {#asrp-searches}

Für [ASRP](asrp.md) wird UGC in der Adobe-Cloud gespeichert. Während UGC in CRX nicht sichtbar ist, ist [Moderation](moderate-ugc.md) sowohl in der Autor- als auch in der Veröffentlichungs-Umgebung verfügbar. Die Verwendung der [UGC-Such-API](#ugc-search-api) funktioniert für ASRP genauso wie für andere SRPs.

Es gibt derzeit keine Tools zur Verwaltung von ASRP-Suchen.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen Sie die [Benennungsanforderungen](#naming-of-custom-properties) einhalten.

### MSRP-Suchen {#msrp-searches}

Für [MSRP](msrp.md) wird UGC in MongoDB gespeichert, das für die Suche mit Solr konfiguriert ist. UGC ist in CRX nicht sichtbar, aber [Moderation](moderate-ugc.md) ist sowohl in der Autor- als auch in der Veröffentlichungs-Umgebung verfügbar.

Zu MSRP und Solr:

* Der eingebettete Solr für die AEM Plattform wird nicht für MSRP verwendet.
* Wenn Sie einen Remote-Solr für die AEM Plattform verwenden, kann er für MSRP freigegeben werden, sollte jedoch verschiedene Sammlungen verwenden.
* Solr kann für die Standardsuche oder für die mehrsprachige Suche (MLS) konfiguriert werden.
* Konfigurationsdetails finden Sie unter [Solr-Konfiguration](msrp.md#solr-configuration) für MSRP.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Suchschnittstelle](#ugc-search-api) verwenden.

Beim Erstellen benutzerdefinierter Eigenschaften, die durchsuchbar sind, müssen Sie die [Benennungsanforderungen](#naming-of-custom-properties) einhalten.

### JSRP-Suchen {#jsrp-searches}

Für [JSRP](jsrp.md) wird UGC in [Oak](../../help/sites-deploying/platform.md) gespeichert und ist nur im Repository der AEM- oder Veröffentlichungsinstanz sichtbar, in der sie eingegeben wurde.

Da UGC in der Regel in der Veröffentlichungs-Umgebung eingegeben wird, muss für Produktionssysteme mit mehreren Herausgebern ein [Veröffentlichungs-Cluster](topologies.md) und nicht eine Veröffentlichungsfarm konfiguriert werden, damit der eingegebene Inhalt von allen Herausgebern sichtbar ist.

Bei JSRP ist in der Umgebung &quot;Veröffentlichen&quot;eingegebenes UGC in der Autorenversion nie sichtbar. Daher finden alle [Moderation](moderate-ugc.md)-Aufgaben in der Veröffentlichungs-Umgebung statt.

Benutzerdefinierte Suchfunktionen sollten die [UGC-Suchschnittstelle](#ugc-search-api) verwenden.

#### Oak Indizierung {#oak-indexing}

Obwohl Oak-Indizes nicht automatisch für die AEM Plattformsuche erstellt werden, wurden sie ab AEM 6.2 für AEM Communities hinzugefügt, um die Leistung zu verbessern und Paginierung bei der Präsentation von UGC-Suchergebnissen zu unterstützen.

Wenn benutzerdefinierte Eigenschaften verwendet werden und die Suche langsam ist, müssen zusätzliche Indizes erstellt werden, damit die benutzerdefinierten Eigenschaften leistungsfähiger werden. Um die Portabilität zu erhalten, sollten Sie beim Erstellen von benutzerdefinierten Eigenschaften, die durchsuchbar sind, die [Benennungsanforderungen](#naming-of-custom-properties) beachten.

Informationen zum Ändern vorhandener Indizes oder zum Erstellen benutzerdefinierter Indizes finden Sie unter [Oak-Abfragen und Indizierung](../../help/sites-deploying/queries-and-indexing.md).

Der [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) ist in ACS AEM Commons verfügbar. Er umfasst:

* Eine Ansicht vorhandener Indizes.
* Die Möglichkeit, eine Neuindizierung zu starten.

Zur Ansicht der vorhandenen Oak-Indizes in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) lautet der Speicherort:

* `/oak:index/socialLucene`

![social-lucene](assets/social-lucene.png)

## Indizierte Sucheigenschaften {#indexed-search-properties}

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

### Benennung der benutzerdefinierten Eigenschaften {#naming-of-custom-properties}

Wenn Sie benutzerdefinierte Eigenschaften hinzufügen, damit diese Eigenschaften für mit der [UGC-Such-API](#ugc-search-api) erstellte Sorten und Suchen sichtbar sind, muss *ein Suffix zum Eigenschaftsnamen hinzugefügt werden.*

Das Suffix ist für Abfragen gedacht, die ein Schema verwenden:

* Er identifiziert die Eigenschaft als durchsuchbar.
* Er identifiziert den Datentyp.

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

* ** Textis eine tokenisierte Zeichenfolge,  ** Stringis nicht. Verwenden Sie *Text* für unscharfe (mehr wie diese) Suchen.

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

Die Standardimplementierung der [Suchkomponente](search.md) verwendet diese Syntax wie in der URL, die die Seite &quot;Suchergebnisse&quot;im [Community-Komponenten-Handbuch](components-guide.md) öffnet. Um zu experimentieren, navigieren Sie zu [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren sind:

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

Dieses Repository enthält Tools zum Verwalten von Daten in SRP.

Derzeit gibt es ein Servlet, das die Möglichkeit bietet, alle UGC aus einem SRP zu löschen.

So löschen Sie z. B. alle UGC in ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Fehlerbehebung {#troubleshooting}

### Solr-Abfrage {#solr-query}

Aktivieren Sie die DEBUG-Protokollierung für

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

Die tatsächliche SOR-Abfrage wird im Debug-Protokoll kodiert angezeigt:

Abfrage zu lösen ist: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

Der Wert des Parameters `q` ist die Abfrage. Nachdem die URL-Kodierung entschlüsselt wurde, kann die Abfrage zur weiteren Debugging an das Tool zur Abfrage der Administratoren weitergeleitet werden.

## Verwandte Ressourcen {#related-resources}

* [Community Content Datenspeicherung](working-with-srp.md)  - Behandelt die verfügbaren SRP-Optionen für einen UGC Common Store.
* [Übersicht über](srp.md)  den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien.
* [SocialUtils Refactoring](socialutils.md)  - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Komponenten](search.md)  für Suche und Suchergebnisse - Hinzufügen der UGC-Suchfunktion zu einer Vorlage.

