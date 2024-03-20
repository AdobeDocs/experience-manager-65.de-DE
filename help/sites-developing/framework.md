---
title: AEM-Tagging-Framework
description: Tagging von Inhalten und Verwendung der AEM Tagging-Infrastruktur
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
feature: Tagging
exl-id: 53a37449-ef87-4fa6-82de-88fdc24cf988
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 47%

---


# AEM-Tagging-Framework {#aem-tagging-framework}

Tagging ermöglicht die Kategorisierung und Organisation von Inhalten. Tags können anhand eines Namespace und einer Taxonomie klassifiziert werden. Ausführliche Informationen zur Verwendung von Tags:

* Siehe Dokument . [Verwenden von Tags](/help/sites-authoring/tags.md) für Informationen zum Tagging von Inhalten als Inhaltsautor.
* Siehe Dokument . [Verwalten von Tags](/help/sites-administering/tags.md) für die Perspektive eines Administrators zum Erstellen und Verwalten von Tags und darüber, auf welche Inhalts-Tags angewendet wurden.

Dieser Artikel konzentriert sich auf das zugrunde liegende Framework, das Tagging in AEM unterstützt, und darauf, wie man es als Entwicklerin bzw. Entwickler nutzen kann.

## Einführung {#introduction}

So taggen Sie Inhalte und verwenden die AEM Tagging-Infrastruktur:

* Das Tag muss unterhalb des [Stammknotens der Taxonomie](#taxonomy-root-node) als Knoten vom Typ `[cq:Tag](#tags-cq-tag-node-type)` vorhanden sein.

* Der `NodeType` des mit Tags versehenen Inhaltsknotens muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) beinhalten.
* Die [`TagID`](#tagid) wird zum Inhaltsknoten hinzugefügt [`cq:tags`](#tagged-content-cq-tags-property) -Eigenschaft und wird in einen Knoten des Typs aufgelöst. ` [cq:Tag](#tags-cq-tag-node-type)`.

## Tags: cq:Tag-Knotentyp  {#tags-cq-tag-node-type}

Die Deklaration eines Tags wird im Repository in einem Knoten des Typs `cq:Tag`.

Ein Tag kann ein einfaches Wort sein (zum Beispiel `sky`) oder stellen eine hierarchische Taxonomie dar (z. B. `fruit/apple`, d. h. sowohl das generische `fruit` und spezifischere `apple`).

Tags werden durch eine eindeutige Tag-ID identifiziert.

Ein Tag weist optionale Metadaten auf, z. B. einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte, falls vorhanden, auf Benutzeroberflächen anstelle der Tag-ID angezeigt werden.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Website-Besuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Knotentyp ist `cq:Tag`n
* Knotenname ist eine Komponente der [TagID](#tagid).
* Die [TagID](#tagid) enthält immer eine [Namespace.](#tag-namespace)
* Die `jcr:title` -Eigenschaft (der Titel, der in der Benutzeroberfläche angezeigt werden soll) optional ist.
* Die Eigenschaft `jcr:description` ist optional.
* Wenn untergeordnete Knoten enthalten, wird das Tag als [Container-Tag.](#container-tags)
* Das Tag wird im Repository unterhalb eines Basispfads gespeichert, der als [Stammknoten der Taxonomie](#taxonomy-root-node) bezeichnet wird.

Da Tags lediglich JCR-Knoten sind, müssen die Knotennamen durch die [JCR-Namenskonvention.](naming-conventions.md)

### TagID (Tag-ID) {#tagid}

Eine Tag-ID identifiziert einen Pfad, der einen Tag-Knoten im Repository ergibt.

Normalerweise ist die TagID eine kurze Tag-ID, die mit dem Namespace beginnt, oder es kann sich um eine absolute TagID handeln, die von der [Stammknoten der Taxonomie.](#taxonomy-root-node)

Wenn Inhalt mit Tags versehen ist und noch nicht vorhanden ist, wird die `[cq:tags](#tagged-content-cq-tags-property)` -Eigenschaft zum Inhaltsknoten hinzugefügt und die TagID zum `String` Array-Wert.

Die Tag-ID besteht aus einem [Namespace](#tag-namespace) gefolgt von der lokalen Tag-ID. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Subtags können verwendet werden, um Tags zu referenzieren, die mit jeder lokalen Tag-ID übereinstimmen. Beispielsweise ist es erlaubt, Inhalte mit dem Tag `fruit` zu versehen, auch wenn es sich um ein Container-Tag mit untergeordneten Tags handelt, z. B. `fruit/apple` oder `fruit/banana`.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der Stammknoten der Taxonomie darf kein Knoten vom Typ sein `cq:Tag`.

In AEM ist der Basispfad `/content/cq:tags` und der Stammknoten ist vom Typ `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Mithilfe von Namespaces können Sie Elemente gruppieren. Der häufigste Anwendungsfall ist ein Namespace pro Site (z. B. öffentlich, intern und portal) oder pro größerer Anwendung (z. B. WCM, Assets, Communities). Namespaces können jedoch für verschiedene andere Anforderungen verwendet werden. Namespaces werden in der Benutzeroberfläche verwendet, um nur die Untergruppe von Tags anzuzeigen (d. h. die Tags eines bestimmten Namespace), die für den aktuellen Inhalt gültig ist.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt](#taxonomy-root-node). Ein Namespace ist ein Knoten des Typs `cq:Tag` , deren übergeordnetes Element nicht `cq:Tag` Knotentyp.

Alle Tags haben einen Namespace. Wenn kein Namespace angegeben ist, wird das Tag dem standardmäßigen Namespace TagID zugewiesen. `default` mit dem Titel `Standard Tags`, d. h. `/content/cq:tags/default`.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Übergabe aller Unter-Tags. Zum Beispiel Inhalte, die mit `fruit/apple` wird als mit `fruit` sowie. Das heißt, bei der Suche nach Inhalten, die mit `fruit` getaggt sind, werden auch Inhalte gefunden, die mit `fruit/apple` getaggt sind.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt enthält (`:`), trennt der Doppelpunkt den Namespace vom Tag oder der Subtaxonomie, die durch Schrägstriche (`/`). Wenn die Tag-ID keinen Doppelpunkt aufweist, wird der Standard-Namespace impliziert.

Der standardmäßige und einzige Speicherort von Tags befindet sich unter `/content/cq:tags`.

Verweisen auf nicht vorhandene Pfade oder Pfade, die nicht auf eine `cq:Tag` -Knoten werden als ungültig betrachtet und ignoriert.

Die folgende Tabelle zeigt einige Beispiel-Tag-IDs, ihre Elemente und wie die Tag-ID einen absoluten Pfad im Repository ergibt:

| TagID (Tag-ID) | Namespace | Lokale ID | Container-Tags | Leaf-Tag | Absoluter Tag-Pfad im Repository |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Ohne | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Ohne | Ohne | Kein, der Namespace | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag die optionale Titelzeichenfolge enthält ( `jcr:title`) kann der Titel für die Anzeige lokalisiert werden, indem die Eigenschaft hinzugefügt wird `jcr:title.<locale>`.

Weitere Informationen finden Sie in den folgenden Dokumenten:

* [Tags in verschiedenen Sprachen](/help/sites-developing/building.md#tags-in-different-languages); beschreibt die Verwendung der APIs
* [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages); beschreibt die Verwendung der Tagging-Konsole

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie](#taxonomy-root-node). Sie können Autoren und Site-Besuchern erlauben oder verweigern, Tags in einem bestimmten Namespace zu erstellen, indem Sie entsprechende ACLs im Repository festlegen.

Das Verweigern von Leseberechtigungen für bestimmte Tags oder Namespaces steuert auch die Möglichkeit, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Vorgehensweise umfasst Folgendes:

* Gewähren von Schreibzugriff auf alle Namespaces für die Gruppe/Rolle `tag-administrators` (unter `/content/cq:tags` hinzufügen/ändern). Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Ermöglicht Benutzern/Autoren das Schreiben von Zugriff auf die Namespaces, in denen Tags von Benutzern/Autoren frei definiert werden sollen (fügen Sie einen Knoten unter `/content/cq:tags/some_namespace`)

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwicklerinnen und -entwickler einen Inhaltstyp mit Tags versehen können, muss die Registrierung eines Knotens ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) das Mixin `cq:Taggable` oder das Mixin `cq:OwnerTaggable` umfassen.

Das Mixin `cq:OwnerTaggable`, das von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM handelt es sich hierbei nur um ein Attribut des Knotens `cq:PageContent`. Das Mixin `cq:OwnerTaggable` wird vom Tagging-Framework nicht benötigt.

>[!NOTE]
>
>Es wird empfohlen, Tags nur auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder dessen `jcr:content`-Knoten) zu aktivieren. Beispiele dafür sind:
>
>* Seiten (`cq:Page`), wobei die `jcr:content`node is type `cq:PageContent` , der Folgendes umfasst: `cq:Taggable` mixin
>* Assets ( `cq:Asset`), wobei die `jcr:content/metadata` -Knoten hat immer die `cq:Taggable` mixin
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

Die `cq:tags` -Eigenschaft ist `String` -Array, das zum Speichern einer oder mehrerer TagIDs verwendet wird, wenn diese von Autoren oder Site-Besuchern auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin `[cq:Taggable](#taggable-content-cq-taggable-mixin)` definiert wird.

>[!NOTE]
>
>Um die AEM-Tagging-Funktionalität zu nutzen, sollten benutzerdefiniert entwickelte Anwendungen keine anderen Tag-Eigenschaften als `cq:tags` definieren.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden werden die Auswirkungen im Repository beim Verschieben oder Zusammenführen von Tags mithilfe der [Tagging-Konsole](/help/sites-administering/tags.md):

* Wenn ein Tag A verschoben oder mit Tag B unter `/content/cq:tags` zusammengeführt wird:

   * Tag A wird nicht gelöscht und erhält eine `cq:movedTo` -Eigenschaft.
   * Tag B wird erstellt (wenn es eine Verschiebung gab) und erhält eine `cq:backlinks` -Eigenschaft.

* `cq:movedTo` verweist auf Tag B.

   * Diese Eigenschaft bedeutet, dass Tag A verschoben oder mit Tag B zusammengeführt wurde. Durch Verschieben von Tag B wird diese Eigenschaft entsprechend aktualisiert. Tag A ist somit ausgeblendet und wird nur im Repository beibehalten, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen. Der Tag-Garbage Collector entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr auf sie verweisen.

   * Ein spezieller Wert für `cq:movedTo` Eigenschaft ist `nirvana`. Sie wird angewendet, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, da es Untertags mit einer `cq:movedTo` die gehalten werden müssen.

  >[!NOTE]
  >
  >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
  >
  >1. Tag wird im Inhalt verwendet (d. h. es hat einen Verweis) oder
  >1. Das Tag enthält bereits verschobene untergeordnete Elemente.

* `cq:backlinks` behält die Verweise in die andere Richtung bei. Das heißt, es enthält eine Liste aller Tags, die in Tag B verschoben oder mit ihm zusammengeführt wurden. Dies ist hauptsächlich erforderlich, um `cq:movedTo` -Eigenschaften aktualisiert, wenn Tag B verschoben/zusammengeführt/gelöscht oder Tag B aktiviert wird. In diesem Fall müssen auch alle Backlinks-Tags aktiviert werden.

  >[!NOTE]
  >
  >Die `cq:backlinks`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
  >
  >1. Tag wird im Inhalt verwendet (d. h. es hat einen Verweis) ODER
  >1. Das Tag enthält bereits verschobene untergeordnete Elemente.

* Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens umfasst die folgende Auflösung:

   1. Wenn unter `/content/cq:tags` keine Übereinstimmung verfügbar ist, wird kein Tag zurückgegeben.

   1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.

      * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.

   1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

* Um eine Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der Knoten `cq:Tag` und all seine Backlinks repliziert werden. Dies geschieht automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

* Spätere Aktualisierungen der `cq:tags` -Eigenschaft die alten Verweise automatisch bereinigt. Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.

>[!NOTE]
>
>Die Verschiebung von Tags unterscheidet sich von der Migration von Tags.

## Tag-Migration {#tags-migration}

Seit Adobe Experience Manager 6.4 werden Tags unter `/content/cq:tags` In früheren Versionen wurden Tags unter `/etc/tags`.

Beim Aktualisieren eines AEM Systems von einer Version vor 6.4 müssen Tags in `/content/cq:tags`. Siehe [Allgemeine Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags) für weitere Informationen.
