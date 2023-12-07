---
title: Einbinden von Tagging in eine AEM-Anwendung
description: Programmgesteuert mit Tags oder erweiterten Tags innerhalb einer benutzerdefinierten AEM-Anwendung arbeiten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
feature: Tagging
exl-id: d885520d-d0ed-45fa-8511-faa2495d667a
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 75%

---

# Einbinden von Tagging in eine AEM-Anwendung{#building-tagging-into-an-aem-application}

Für das programmgesteuerte Arbeiten mit Tags oder das Erweitern von Tags in einem benutzerdefinierten AEM-Programm beschreibt diese Seite die Verwendung des

* [Tagging-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/tagging/package-summary.html),

Das interagiert mit dem

* [Tagging-Framework interagiert, beschrieben.](/help/sites-developing/framework.md)

Weitere Informationen zum Tagging finden Sie unter:

* [Verwalten von Tags](/help/sites-administering/tags.md) für Informationen zum Erstellen und Verwalten von Tags und darüber, auf welche Inhalts-Tags angewendet wurden.
* [Verwenden von Tags](/help/sites-authoring/tags.md) für Informationen zum Tagging von Inhalten.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](/help/sites-developing/framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. Der TagManager stellt sicher, dass Tags, die als Werte in der Zeichenfolgen-Array-Eigenschaft `cq:tags` eingegeben wurden, nicht dupliziert werden. Er entfernt TagIDs, die auf nicht vorhandene Tags verweisen, und aktualisiert TagIDs für verschobene oder zusammengefügte Tags. TagManager verwendet einen JCR Observation Listener, der alle falschen Änderungen zurücksetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* JcrTagManagerFactory – gibt eine JCR-basierte Implementierung eines `TagManager` zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` – ermöglicht das Auflösen und Erstellen von Tags nach Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

Um eine TagManager-Instanz abzurufen, benötigen Sie ein JCR `Session` und `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

Im typischen Sling-Kontext können Sie sich auch an einen `TagManager` aus dem `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Abrufen eines Tag-Objekts {#retrieving-a-tag-object}

A `Tag` kann über die `TagManager`, indem Sie entweder ein vorhandenes Tag auflösen oder eines erstellen:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Für die JCR-basierte Implementierung, die `Tags` auf JCR-`Nodes` abbildet, können Sie den Mechanismus `adaptTo` von Sling direkt verwenden, wenn Sie die Ressource haben (z. B. `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Während ein Tag nur „von“ einer Ressource (kein Knoten) konvertiert werden kann, kann ein Tag sowohl in einen Knoten als auch in eine Ressource konvertiert werden :

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Die direkte Anpassung von `Node` zu `Tag` ist nicht möglich, da `Node` die Sling-Methode `Adaptable.adaptTo(Class)` nicht implementiert.

### Abrufen und Festlegen von Tags {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Suchen nach Tags {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>Der gültige zu verwendete `RangeIterator` ist:
>
>`com.day.cq.commons.RangeIterator`

### Löschen von Tags {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Replizieren von Tags {#replicating-tags}

Es ist möglich, den Replikations-Service (`Replicator`) mit Tags zu verwenden, da Tags vom Typ `nt:hierarchyNode` sind:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tagging auf der Client-Seite {#tagging-on-the-client-side}

Das Formular-Widget `CQ.tagging.TagInputField` dient zur Eingabe von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen. Sein xtype ist `tags`.

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag Garbage Collector ist ein Hintergrund-Service, der die ausgeblendeten und nicht verwendeten Tags bereinigt. Ausgeblendete und nicht verwendete Tags sind Tags unter `/content/cq:tags`, die eine Eigenschaft `cq:movedTo` haben und nicht auf einem Inhaltsknoten verwendet werden, d. h. ihre Anzahl beträgt null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil des Verschiebungs- oder des Zusammenführungsvorgangs aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Das Garbage Collector Tag wird standardmäßig einmal am Tag ausgeführt. Sie können sie wie folgt konfigurieren:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* Die Suche nach TagID sucht nach den Tags, für die die Eigenschaft `cq:movedTo` auf TagID gesetzt ist, und folgt den `cq:movedTo`-TagIDs.

* Die Suche nach Tag-Titel sucht nur die Tags, die keine Eigenschaft `cq:movedTo` besitzen.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Wie in der Dokumentation zur Verwaltung von Tags im Abschnitt [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) beschrieben, kann ein Tag-`title` in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft weist das Format `jcr:title.<locale>` auf, beispielsweise `jcr:title.fr` für die französische Übersetzung. Die `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und &quot;_&quot;anstelle von &quot;-&quot;verwenden. Beispiel: `de_ch`.

Wenn das Tag **Animals** zur **Produktseite** hinzugefügt wird, wird der Wert `stockphotography:animals` zur Eigenschaft `cq:tags` des Knotens „/content/geometrixx/de/products/jcr:content“ hinzugefügt. Die Übersetzung wird vom Tag-Knoten referenziert.

Die Server-seitige API verfügt über lokalisierte `title`-bezogene Methoden:

* [com.day.cq.tagging.Tag](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(Locale locale)
   * getTitlePath(Locale locale)

* [com.day.cq.tagging.TagManager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, Locale locale)
   * createTagByTitle(String tagTitlePath, Locale locale)
   * resolveByTitle(String tagTitlePath, Locale locale)

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Benutzersprache abgerufen werden:

* So rufen Sie die Seitensprache in einer JSP ab:

   * `currentPage.getLanguage(false)`

* So rufen Sie die Benutzersprache in einer JSP ab:

   * `slingRequest.getLocale()`

Die `currentPage` und `slingRequest` sind in einer JSP über [&lt;cq:definedobjects>](/help/sites-developing/taglib.md) -Tag.

Beim Tagging hängt die Lokalisierung vom Kontext als Tag ab `titles`kann in der Seitensprache, in der Benutzersprache oder in einer anderen Sprache angezeigt werden.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“ {#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie eine Sprache (Finnisch) zum **Tag bearbeiten** dialog:

1. Bearbeiten Sie in **CRXDE** die Mehrwerteigenschaft `languages` des Knotens `/content/cq:tags`.

1. Fügen Sie `fi_fi` hinzu, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Die neue Sprache (Finnisch) ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn Sie ein Tag in der **Tagging-Konsole** bearbeiten.

>[!NOTE]
>
>Die neue Sprache muss eine der AEM anerkannten Sprachen sein. Das heißt, es muss als Knoten unter verfügbar sein. `/libs/wcm/core/resources/languages`.

>[!CAUTION]
>
>Durch die Installation eines Service Packs wird die Eigenschaft languages des Knotens /content/cq:tags auf den Standardwert zurückgesetzt. Daher ist es erforderlich, sie vor der Installation aus den Eigenschaften hinzuzufügen.
