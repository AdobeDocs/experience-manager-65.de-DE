---
title: AEM-Tagging-Framework
seo-title: AEM Tagging Framework
description: Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur,
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: f80a2cb1-359f-41dd-a70b-626d92cc3d4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: f69db472-9f5c-4c0d-9292-2920ef69feeb
docset: aem65
feature: Tagging
exl-id: 53a37449-ef87-4fa6-82de-88fdc24cf988
source-git-commit: efb4f9f8a97baf8d3d02160226e4f4d3f8f64c89
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 100%

---

# AEM-Tagging-Framework {#aem-tagging-framework}

Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur wie folgt:

* Das Tag muss unterhalb des ` [cq:Tag](#tags-cq-tag-node-type)`Stammknotens der Taxonomie[ als Knoten vom Typ ](#taxonomy-root-node) vorhanden sein

* Der NodeType des mit Tags versehenen Inhaltsknotens muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) beinhalten.
* Die [TagID](#tagid) wird der Eigenschaft [ `cq:tags`](#tagged-content-cq-tags-property) des Inhaltsknotens hinzugefügt und zu einem Knoten vom Typ ` [cq:Tag](#tags-cq-tag-node-type)` aufgelöst.

## Tags: cq:Tag-Knotentyp  {#tags-cq-tag-node-type}

Die Funktion eines Tags wird im Repository in einem Knoten vom Typ `cq:Tag.` erfasst.

Ein Tag kann ein einfaches Wort (z. B. Himmel) sein oder eine hierarchische Taxonomie (z. B. Frucht/Apfel, womit sowohl die Frucht im Allgemeinen als auch der Apfel im Speziellen gemeint sind) darstellen.

Tags werden anhand einer eindeutigen Tag-ID identifiziert.

Ein Tag weist optionale Metadaten auf, z. B. einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte, falls vorhanden, auf Benutzeroberflächen anstelle der Tag-ID angezeigt werden.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Website-Besuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Knotentyp ist `cq:Tag`
* Knotenname ist eine Komponente der ` [TagID](#tagid)`
* Die ` [TagID](#tagid)` umfasst immer einen [Namespace](#tag-namespace)

* optionale `jcr:title`-Eigenschaft (der auf der Benutzeroberfläche anzuzeigende Titel)

* optionale `jcr:description`-Eigenschaft

* wird als Container-Tag bezeichnet, wenn [untergeordnete Knoten](#container-tags) enthalten sind
* wird im Repository unterhalb eines Basispfads gespeichert, der als [Stammknoten der Taxonomie](#taxonomy-root-node) bezeichnet wird

### TagID (Tag-ID) {#tagid}

Eine Tag-ID identifiziert einen Pfad, der einen Tag-Knoten im Repository ergibt.

Normalerweise ist die Tag-ID eine kurze Tag-ID, die mit dem Namespace beginnt. Sie kann auch eine absolute Tag-ID sein, die mit dem [Stammknoten der Taxonomie](#taxonomy-root-node) beginnt.

Wenn Inhalte mit Tags versehen werden, aber noch nicht vorhanden sind, wird dem Inhaltsknoten die Eigenschaft ` [cq:tags](#tagged-content-cq-tags-property)` und dem String-Array-Wert die Tag-ID hinzugefügt.

Die Tag-ID besteht aus einem [Namespace](#tag-namespace) gefolgt von der lokalen Tag-ID. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Untergeordnete Tags können dazu verwendet werden, auf Tags genau wie auf andere lokale Tag-IDs zu verweisen. Beispielsweise ist es erlaubt, Inhalte mit dem Tag „Frucht“ zu versehen, auch wenn es sich um ein Container-Tag mit untergeordneten Tags handelt, z. B. „Frucht/Apfel“ oder „Frucht/Banane“.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der Stammknoten der Taxonomie darf *kein* Knoten vom Typ `  cq   :Tag` sein.

In AEM ist der Basispfad `/content/  cq   :tags` und der Stammknoten ist vom Typ `  cq   :Folder`.

### Tag-Namespace {#tag-namespace}

Namespaces ermöglichen das Gruppieren von Elementen. Der vorherrschende Anwendungsfall besteht darin, einen Namespace pro Website (z. B. öffentlich, intern, Portal) oder pro größerer Anwendung (z. B. WCM, Assets, Communities) zu verwenden, aber Namespaces können auch anderweitig eingesetzt werden. Namespaces werden in der Benutzeroberfläche verwendet, um nur die Untergruppe von Tags (d. h. die Tags eines bestimmten Namespace) anzuzeigen, die auf den aktuellen Inhalt anwendbar sind.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt](#taxonomy-root-node). Ein Namespace ist ein Knoten vom Typ `cq:Tag`, dessen übergeordnetes Element nicht vom Knotentyp `cq:Tag` ist.

Alle Tags haben einen Namespace. Wenn kein Namespace angegeben ist, wird das Tag dem standardmäßigen Namespace zugeordnet, der Tag-ID `default` lautet (Titell ist `Standard Tags),`, d. h `/content/cq:tags/default.`)

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Untersummierung aller untergeordneten Tags: Beispielsweise werden Inhalte, die mit dem Tag „Frucht/Apfel“ versehen sind, auch als mit dem Tag „Frucht“ versehen betrachtet. Wenn also nach Inhalten gesucht wird, die mit dem Tag „Frucht“ versehen sind, werden auch Inhalte mit dem Tag „Frucht/Apfel“ gefunden.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt enthält, trennt der Doppelpunkt den Namespace vom Tag oder der Untertaxonomie, die dann mit normalen Schrägstrichen voneinander getrennt werden. Wenn in der Tag-ID kein Doppelpunkt vorkommt, ist der Standard-Namespace impliziert.

Der standardmäßige und einzige Speicherort von Tags befindet sich unter /content/cq:tags.

Tags, die auf nicht vorhandene Pfade oder auf Pfade verweisen, an deren Ende sich kein cq:Tag-Knoten befindet, werden als ungültig betrachtet und werden ignoriert.

Die folgende Tabelle zeigt einige Beispiel-Tag-IDs, ihre Elemente und wie die Tag-ID einen absoluten Pfad im Repository ergibt:

Die folgende Tabelle zeigt einige Beispiel-Tag-IDs, ihre Elemente und wie die Tag-ID einen absoluten Pfad im Repository ergibt:

<table>
 <tbody>
  <tr>
   <td><strong>TagID (Tag-ID)<br /> </strong></td>
   <td><strong>Namespace</strong></td>
   <td><strong>Lokale ID</strong></td>
   <td><strong>Container-Tag(s)</strong></td>
   <td><strong>Leaf-Tag</strong></td>
   <td><strong>Absoluter Tag-Pfad im Repository<br /></strong></td>
  </tr>
  <tr>
   <td>dam:fruit/apple/braeburn</td>
   <td>dam</td>
   <td>fruit/apple/braeburn</td>
   <td>Obst, Apfel</td>
   <td>Braeburn</td>
   <td>/content/cq:tags/dam/fruit/apple/braeburn</td>
  </tr>
  <tr>
   <td>color/red</td>
   <td>default</td>
   <td>color/red</td>
   <td>color</td>
   <td>red</td>
   <td>/content/cq:tags/default/color/red</td>
  </tr>
  <tr>
   <td>sky</td>
   <td>default</td>
   <td>Himmel</td>
   <td>(keins)</td>
   <td>Himmel</td>
   <td>/content/cq:tags/default/sky</td>
  </tr>
  <tr>
   <td>dam:</td>
   <td>dam</td>
   <td>(keins)</td>
   <td>(keins)</td>
   <td>(keins, der Namespace)</td>
   <td>/content/cq:tags/dam</td>
  </tr>
  <tr>
   <td>/content/cq:tags/category/car</td>
   <td>category</td>
   <td>car</td>
   <td>Auto</td>
   <td>Auto</td>
   <td>/content/cq:tags/category/car</td>
  </tr>
 </tbody>
</table>

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag den optionalen Titelstring enthält (`jcr:title`) ist es möglich, den Titel zur Anzeige zu lokalisieren, indem die Eigenschaft `jcr:title.<locale>` > hinzugefügt wird.

Weitere Informationen finden Sie unter

* [Tags in verschiedenen Sprachen](/help/sites-developing/building.md#tags-in-different-languages) (beschreibt die Verwendung der APIs)
* [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) (beschreibt die Verwendung der Tagging-Konsole)

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie](#taxonomy-root-node). Sie erlauben oder verweigern Autoren und Websitebesuchern die Erstellung von Tags in einem jeweiligen Namespace, indem Sie im Repository entpsrechende ACLs festlegen.

Außerdem können Sie die Fähigkeit zur Anwendung von Tags auf bestimmte Inhalte steuern, indem Sie Leseberechtigungen für bestimmte Tags oder Namespaces einschränken.

Eine typische Vorgehensweise umfasst Folgendes:

* Gewähren von Schreibzugriff auf alle Namespaces für die Gruppe/Rolle `tag-administrators` (unter `/content/cq:tags` hinzufügen/ändern). Diese Gruppe enthält AEM standardmäßig.

* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Gewähren von Schreibzugriff für Benutzer/Autoren auf die Namespaces, bei denen Tags durch Benutzer/Autoren frei definierbar sein müssen (add_node unter `/content/cq:tags/some_namespace`).

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwickler einen Inhaltstyp mit Tags versehen können, muss die Registrierung eines Knotens ([CND](https://jackrabbit.apache.org/node-type-notation.html)) das Mixin `cq:Taggable` oder das Mixin `cq:OwnerTaggable` umfassen.

Das Mixin `cq:OwnerTaggable`, das von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM handelt es sich hierbei nur um ein Attribut des Knotens `cq:PageContent`. Das Mixin `cq:OwnerTaggable` wird vom Tagging-Framework nicht benötigt.

>[!NOTE]
>
>Es wird empfohlen, Tags nur auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder dessen jcr:content-Knoten) zu aktivieren. Beispiele dafür sind:
>
>* Seiten (`cq:Page`), deren Knoten `jcr:content` vom Typ `cq:PageContent` sind, der das Mixin `cq:Taggable` umfasst
>
>* Assets (`cq:Asset`), deren Knoten `jcr:content/metadata` immer das Mixin `cq:Taggable` umfassen
>


### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. Die CND-Notation wird als Teil der JCR-Dokumentation [hier](https://jackrabbit.apache.org/node-type-notation.html) definiert.

Die wichtigsten Definitionen für die Knotentypen in AEM sind wie folgt:

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Inhalt mit Tags: cq:tags-Eigenschaft {#tagged-content-cq-tags-property}

Die Eigenschaft `cq:tags` ist ein String-Array, das zum Speichern mindestens einer Tag-ID verwendet wird, wenn diese von Autoren oder Websitebesuchern auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin `[cq:Taggable](#taggable-content-cq-taggable-mixin)` definiert wird.

>[!NOTE]
>
>Um die AEM-Tagging-Funktionalität zu nutzen, sollten benutzerdefinierte entwickelte Anwendungen keine anderen Tag-Eigenschaften als `cq:tags` definieren.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der [Tagging-Konsole](/help/sites-administering/tags.md) verschieben oder zusammenführen:

* Wenn ein Tag A verschoben oder mit Tag B unter `/content/cq:tags` zusammengeführt wird:

   * Tag A wird nicht gelöscht und erhält eine `cq:movedTo`-Eigenschaft.
   * Tag B wird erstellt (im Falle einer Verschiebung) und erhält eine `cq:backlinks`-Eigenschaft.

* `cq:movedTo` verweist auf Tag B.
Diese Eigenschaft bedeutet, dass Tag A verschoben oder mit Tag B zusammengeführt wurde. Wird Tag B verschoben, wird diese Eigenschaft entsprechend aktualisiert. Tag A ist somit ausgeblendet und wird nur im Repository behalten, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen. Der Garbage Collector für Tags entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr darauf verweisen.
Ein spezieller Wert für die Eigenschaft `cq:movedTo` ist `nirvana`: Er wird angewendet, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, weil untergeordnete Tags mit `cq:movedTo` vorhanden sind, die nicht entfernt werden dürfen.

   >[!NOTE]
   >
   >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
   >
   >1. Das Tag wird im Inhalt verwendet (d. h. es wird darauf verwiesen) ODER
   >1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* `cq:backlinks` speichert Verweise in die andere Richtung, d. h. sie enthält eine Liste aller Tags, die verschoben oder mit Tag B zusammengeführt wurden. Dies ist hauptsächlich erforderlich, um `cq:movedTo`-Eigenschaften auf dem aktuellen Stand zu halten, wenn Tag B auch verschoben/zusammengeführt/gelöscht oder aktiviert wird. In diesem Fall müssen all seine backlinks-Tags ebenso aktiviert werden.

   >[!NOTE]
   >
   >Die `cq:backlinks`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
   >
   >1. Das Tag wird im Inhalt verwendet (d. h. es wird darauf verwiesen) ODER
   >1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens umfasst die folgenden Auflösungen:

   1. Wenn unter `/content/cq:tags` keine Übereinstimmung verfügbar ist, wird kein Tag zurückgegeben.
   1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.
Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.

   1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

* Um eine Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der Knoten `cq:Tag` und all seine Backlinks repliziert werden. Dies geschieht automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

* Spätere Aktualisierungen der `cq:tags`-Eigenschaft der Seite bereinigen automatisch die „alten“ Verweise. Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.

>[!NOTE]
>
>Die Verschiebung von Tags unterscheidet sich von der Migration von Tags.

## Migration von Tags {#tags-migration}

Ab Experience Manager 6.4 werden Tags, die zuvor unter `/etc/tags` gespeichert wurden, unter `/content/cq:tags` gespeichert. In Fällen, in denen Adobe Experience Manager ein Upgrade von der vorherigen Version erhielt, sind die Tags jedoch immer noch unter dem alten Speicherort `/etc/tags` vorhanden. In Systemen mit Upgrade müssen Tags unter `/content/cq:tags` migriert werden.

>[!NOTE]
>
>Auf der Seite „Seiteneigenschaften der Tags“ wird empfohlen, Tag-ID (`geometrixx-outdoors:activity/biking`) anstatt des festen Kodierens des Tag-Basispfads (z. B. `/etc/tags/geometrixx-outdoors/activity/biking`) zu verwenden.
>
>Zum Auflisten von Tags kann `com.day.cq.tagging.servlets.TagListServlet` verwendet werden.

>[!NOTE]
>
>Es wird empfohlen, die Tag-Manager-API als Ressource zu verwenden.

### Wenn die upgegradete AEM-Instanz die TagManager-API unterstützt {#upgraded-instance-support-tagmanager-api}

1. Beim Start der Komponente erkennt die TagManager-API, ob es sich um eine upgegradete AEM-Instanz handelt. In einem System mit Upgrade werden Tags unter `/etc/tags` gespeichert.

1. Die TagManager-API wird dann im Abwärtskompatibilitätsmodus ausgeführt, d. h. die API verwendet `/etc/tags` als Basispfad. Wenn nicht, wird ein neuer Speicherort `/content/cq:tags` verwendet.

1. Aktualisieren Sie den Tag-Speicherort.

1. Führen Sie nach der Migration von Tags an den neuen Speicherort das folgende Skript aus:

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
  def tagPath = node.path;
  println "tag = ${tagPath}";

  if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags"))
    {
     def movedTo = node.getProperty("cq:movedTo").getValue().toString();

     println "cq:movedTo = ${movedTo} \n";

     movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
     node.setProperty("cq:movedTo",movedTo);
     } else if(node.hasProperty("cq:backlinks")){

     String[] backLinks = node.getProperty("cq:backlinks").getValues();
     int count = 0;

     backLinks.each { value ->
             if(value.startsWith("/etc/tags")){
                     println "cq:backlinks = ${value}\n";
                     backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
             count++;
     }

    node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

Das Skript ruft alle Tags ab, die `/etc/tags` im Wert der `cq:movedTo/cq:backLinks`-Eigenschaft haben. Anschließend wird der abgerufene Ergebnissatz schrittweise durchlaufen und die Eigenschaftswerte `cq:movedTo` und `cq:backlinks` werden in `/content/cq:tags` Pfade aufgelöst (in dem Fall, dass `/etc/tags` im Wert erkannt wird).

### Wenn die upgegradete AEM-Instanz auf der klassischen Benutzeroberfläche ausgeführt wird {#upgraded-instance-runs-classic-ui}

>[!NOTE]
>
>Die klassische Benutzeroberfläche ist nicht kompatibel mit dem Konzept von null Ausfallzeiten und unterstützt keinen neuen Tag-Basispfad. Wenn Sie die klassische Benutzeroberfläche verwenden möchten, muss `/etc/tags` erstellt werden, gefolgt von einem Neustart der Komponente `cq-tagging`.

Im Falle von upgegradeten AEM-Instanzen, die von der TagManager-API unterstützt werden und in der klassischen Benutzeroberfläche ausgeführt werden:

1. Sobald Verweise auf den alten Tag-Basispfad `/etc/tags` durch die Verwendung von tagId oder den neuen Tag-Speicherort `/content/cq:tags` ersetzt wurden, können Sie Tags an den neuen Speicherort `/content/cq:tags` in CRX migrieren und anschließend die Komponente neu starten.

1. Nachdem Sie Tags an den neuen Speicherort migriert haben, führen Sie das oben genannte Skript aus.
