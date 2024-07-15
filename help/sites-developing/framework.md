---
title: AEM-Tagging-Framework
description: Versehen von Inhalten mit Tags und Verwenden der AEM-Tagging-Infrastruktur
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
feature: Developing,Tagging
exl-id: 53a37449-ef87-4fa6-82de-88fdc24cf988
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 100%

---


# AEM-Tagging-Framework {#aem-tagging-framework}

Tagging ermöglicht die Kategorisierung und Organisation von Inhalten. Tags können anhand eines Namespace und einer Taxonomie klassifiziert werden. Ausführliche Informationen zur Verwendung von Tags:

* Informationen zum Tagging von Inhalten als Inhaltsautorin oder Inhaltsautor finden Sie im Dokument [Verwenden von Tags](/help/sites-authoring/tags.md).
* Informationen zur Erstellung und Verwaltung von Tags durch Admins sowie dazu, welchen Inhalten Tags zugewiesen werden, finden Sie im Dokument [Verwalten von Tags](/help/sites-administering/tags.md).

Dieser Artikel konzentriert sich auf das zugrunde liegende Framework, das Tagging in AEM unterstützt, und darauf, wie man es als Entwicklerin bzw. Entwickler nutzen kann.

## Einführung {#introduction}

Taggen von Inhalten und Verwenden der AEM-Tagging-Infrastruktur:

* Das Tag muss unterhalb des [Stammknotens der Taxonomie](#taxonomy-root-node) als Knoten vom Typ `[cq:Tag](#tags-cq-tag-node-type)` vorhanden sein.

* Der `NodeType` des mit Tags versehenen Inhaltsknotens muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) beinhalten.
* Die [`TagID`](#tagid) wird zur Eigenschaft [`cq:tags`](#tagged-content-cq-tags-property) des Inhaltsknotens hinzugefügt, was einen Knoten vom Typ ` [cq:Tag](#tags-cq-tag-node-type)` ergibt.

## Tags: cq:Tag-Knotentyp  {#tags-cq-tag-node-type}

Die Deklaration eines Tags wird im Repository in einem Knoten vom Typ `cq:Tag` erfasst

Ein Tag kann ein einfaches Wort) sein (z. B. `sky`) oder eine hierarchische Taxonomie darstellen (z. B. `fruit/apple`, womit sowohl `fruit` im Allgemeinen als auch `apple` im Speziellen gemeint ist).

Tags werden anhand einer eindeutigen Tag-ID identifiziert.

Ein Tag weist optionale Metadaten auf, z. B. einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte, falls vorhanden, auf Benutzeroberflächen anstelle der Tag-ID angezeigt werden.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Website-Besuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Knotentyp ist `cq:Tag`n
* Knotenname ist eine Komponente der [Tag-ID](#tagid).
* Die [Tag-ID](#tagid) umfasst immer einen [Namespace](#tag-namespace).
* Die Eigenschaft `jcr:title` (der Titel, der auf der Benutzeroberfläche angezeigt werden soll) ist optional.
* Die Eigenschaft `jcr:description` ist optional.
* Wird als [Container-Tag](#container-tags) bezeichnet, wenn untergeordnete Knoten enthalten sind.
* Das Tag wird im Repository unterhalb eines Basispfads gespeichert, der als [Stammknoten der Taxonomie](#taxonomy-root-node) bezeichnet wird.

Da Tags lediglich JCR-Knoten sind, müssen die Knotennamen der [JCR-Namenskonvention](naming-conventions.md) entsprechen.

### TagID (Tag-ID) {#tagid}

Eine Tag-ID identifiziert einen Pfad, der einen Tag-Knoten im Repository ergibt.

Normalerweise ist die Tag-ID eine kurze Tag-ID, die mit dem Namespace beginnt. Sie kann auch eine absolute Tag-ID sein, die mit dem [Stammknoten der Taxonomie](#taxonomy-root-node) beginnt.

Wenn Inhalte mit Tags versehen werden, wird, sofern noch nicht vorhanden, die Eigenschaft `[cq:tags](#tagged-content-cq-tags-property)` zum Inhaltsknoten und die Tag-ID zum `String`-Array-Wert hinzugefügt.

Die Tag-ID besteht aus einem [Namespace](#tag-namespace) gefolgt von der lokalen Tag-ID. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Untergeordnete Tags können dazu verwendet werden, auf Tags sowie auf andere lokale Tag-IDs zu verweisen. Beispielsweise ist es erlaubt, Inhalte mit dem Tag `fruit` zu versehen, auch wenn es sich um ein Container-Tag mit untergeordneten Tags handelt, z. B. `fruit/apple` oder `fruit/banana`.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der Stammknoten der Taxonomie darf kein Knoten vom Typ `cq:Tag` sein.

In AEM ist der Basispfad `/content/cq:tags` und der Stammknoten ist vom Typ `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Mithilfe von Namespaces können Sie Elemente gruppieren. Der vorherrschende Anwendungsfall besteht darin, einen Namespace pro Site (z. B. öffentlich, intern und Portal) oder pro größerer Anwendung (z. B. WCM, Assets oder Communitys) zu verwenden. Namespaces können aber auch anderweitig eingesetzt werden. Namespaces werden in der Benutzeroberfläche verwendet, um nur die Untergruppe von Tags (d. h. die Tags eines bestimmten Namespace) anzuzeigen, die auf den aktuellen Inhalt anwendbar sind.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt](#taxonomy-root-node). Ein Namespace ist ein Knoten vom Typ `cq:Tag`, dessen übergeordnetes Element nicht vom Knotentyp `cq:Tag` ist.

Alle Tags haben einen Namespace. Wenn kein Namespace angegeben ist, wird das Tag dem standardmäßigen Namespace zugeordnet, der Tag-ID `default` mit dem Titel `Standard Tags`, d. h `/content/cq:tags/default`.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Oberbegriff aller untergeordneten Tags. Beispielsweise werden Inhalte, die mit `fruit/apple` getaggt sind, auch als mit `fruit` getaggt erachtet. Das heißt, bei der Suche nach Inhalten, die mit `fruit` getaggt sind, werden auch Inhalte gefunden, die mit `fruit/apple` getaggt sind.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt (`:`) enthält, trennt der Doppelpunkt den Namespace vom Tag oder der Untertaxonomie, die dann mit Schrägstrichen (`/`) weiter voneinander getrennt werden. Wenn in der Tag-ID kein Doppelpunkt vorkommt, wird vom Standard-Namespace ausgegangen.

Der standardmäßige und einzige Speicherort von Tags befindet sich unter `/content/cq:tags`.

Tags, die auf nicht vorhandene Pfade oder auf Pfade verweisen, an deren Ende sich kein `cq:Tag`-Knoten befindet, werden als ungültig betrachtet und ignoriert.

Die folgende Tabelle zeigt einige Beispiel-Tag-IDs, ihre Elemente und wie die Tag-ID einen absoluten Pfad im Repository ergibt:

| TagID (Tag-ID) | Namespace | Lokale ID | Container-Tags | Leaf-Tag | Absoluter Tag-Pfad im Repository |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Ohne | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Ohne | Ohne | Ohne, der Namespace | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag die optionale Titelzeichenfolge enthält (`jcr:title`), ist es möglich, den Titel zur Anzeige zu lokalisieren, indem die Eigenschaft `jcr:title.<locale>` hinzugefügt wird.

Weitere Informationen finden Sie in den folgenden Dokumenten:

* [Tags in verschiedenen Sprachen](/help/sites-developing/building.md#tags-in-different-languages) (beschreibt die Verwendung der APIs)
* [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) (beschreibt die Verwendung der Tagging-Konsole)

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie](#taxonomy-root-node). Sie erlauben oder verweigern Autorinnen und Autoren sowie Besucherinnen und Besuchern von Sites die Erstellung von Tags in einem bestimmten Namespace, indem im Repository entsprechende ACLs festgelegt werden.

Durch das Verweigern von Leseberechtigungen für bestimmte Tags oder Namespaces wird die Möglichkeit gesteuert, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Vorgehensweise umfasst Folgendes:

* Gewähren von Schreibzugriff auf alle Namespaces für die Gruppe/Rolle `tag-administrators` (unter `/content/cq:tags` hinzufügen/ändern). Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Gewähren von Schreibzugriff für Benutzerinnen und Benutzer bzw. Autorinnen und Autoren auf die Namespaces, bei denen Tags durch Benutzerinnen und Benutzer bzw. Autorinnen und Autoren frei definierbar sein müssen (Hinzufügen eines Knotens unter `/content/cq:tags/some_namespace`).

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwicklerinnen und -entwickler einen Inhaltstyp mit Tags versehen können, muss die Registrierung eines Knotens ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) das Mixin `cq:Taggable` oder das Mixin `cq:OwnerTaggable` umfassen.

Das Mixin `cq:OwnerTaggable`, das von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM handelt es sich hierbei nur um ein Attribut des Knotens `cq:PageContent`. Das Mixin `cq:OwnerTaggable` wird vom Tagging-Framework nicht benötigt.

>[!NOTE]
>
>Es wird empfohlen, Tags nur auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder dessen `jcr:content`-Knoten) zu aktivieren. Beispiele dafür sind:
>
>* Seiten (`cq:Page`), deren Knoten `jcr:content` vom Typ `cq:PageContent` ist, der das Mixin `cq:Taggable` umfasst
>* Assets (`cq:Asset`), deren Knoten `jcr:content/metadata` immer das Mixin `cq:Taggable` umfasst
>

### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. Die CND-Notation wird als Teil der JCR-Dokumentation [hier](https://jackrabbit.apache.org/jcr/node-type-notation.html) definiert.

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

Die Eigenschaft `cq:tags` ist ein `String`-Array, das zum Speichern mindestens einer Tag-ID verwendet wird, wenn diese von Autorinnen und Autoren oder Besucherinnen und Besuchern von Sites auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin `[cq:Taggable](#taggable-content-cq-taggable-mixin)` definiert wird.

>[!NOTE]
>
>Um die AEM-Tagging-Funktionalität zu nutzen, sollten benutzerdefiniert entwickelte Anwendungen keine anderen Tag-Eigenschaften als `cq:tags` definieren.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der [Tagging-Konsole](/help/sites-administering/tags.md) verschieben oder zusammenführen:

* Wenn ein Tag A verschoben oder mit Tag B unter `/content/cq:tags` zusammengeführt wird:

   * Tag A wird nicht gelöscht und erhält eine `cq:movedTo`-Eigenschaft.
   * Tag B wird erstellt (im Falle einer Verschiebung) und erhält eine `cq:backlinks`-Eigenschaft.

* `cq:movedTo` verweist auf Tag B.

   * Diese Eigenschaft bedeutet, dass Tag A verschoben oder mit Tag B zusammengeführt wurde. Wird Tag B verschoben, wird diese Eigenschaft entsprechend aktualisiert. Tag A ist somit ausgeblendet und wird nur im Repository behalten, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen. Der Garbage Collector für Tags entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr darauf verweisen.

   * Ein spezieller Wert für die Eigenschaft `cq:movedTo` ist `nirvana`. Er wird angewendet, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, weil untergeordnete Tags mit `cq:movedTo` vorhanden sind, die beibehalten werden müssen.

  >[!NOTE]
  >
  >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
  >
  >1. Tag wird im Inhalt verwendet (was bedeutet, dass es einen Verweis hat).
  >1. Das Tag enthält bereits verschobene untergeordnete Elemente.

* `cq:backlinks` behält die Verweise in die andere Richtung bei. Die Eigenschaft enthält also eine Liste aller Tags, die verschoben oder mit Tag B zusammengeführt wurden. Dies ist hauptsächlich erforderlich, um `cq:movedTo`-Eigenschaften auf dem aktuellen Stand zu halten, wenn Tag B auch verschoben/zusammengeführt/gelöscht oder aktiviert wird. In diesem Fall müssen all seine backlinks-Tags ebenso aktiviert werden.

  >[!NOTE]
  >
  >Die Eigenschaft `cq:backlinks` wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
  >
  >1. Tag wird im Inhalt verwendet (was bedeutet, dass es einen Verweis hat).
  >1. Das Tag enthält bereits verschobene untergeordnete Elemente.

* Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens umfasst die folgende Auflösung:

   1. Wenn unter `/content/cq:tags` keine Übereinstimmung verfügbar ist, wird kein Tag zurückgegeben.

   1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.

      * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.

   1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

* Um eine Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der Knoten `cq:Tag` und all seine Backlinks repliziert werden. Dies geschieht automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

* Spätere Aktualisierungen der `cq:tags`-Eigenschaft der Seite bereinigen automatisch die alten Verweise. Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.

>[!NOTE]
>
>Die Verschiebung von Tags unterscheidet sich von der Migration von Tags.

## Tag-Migration {#tags-migration}

Seit Adobe Experience Manager 6.4 werden Tags unter `/content/cq:tags` gespeichert, in früheren Versionen unter `/etc/tags`.

Beim Aktualisieren eines AEM-Systems von einer früheren Version als 6.4 müssen Tags zu `/content/cq:tags` migriert werden. Weitere Informationen finden Sie unter [Repository-Neustrukturierung für alle Lösungen in AEM 6.5](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags).
