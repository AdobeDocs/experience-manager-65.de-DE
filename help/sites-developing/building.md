---
title: Einbinden von Tagging in eine AEM-Anwendung
seo-title: Einbinden von Tagging in eine AEM-Anwendung
description: Programmatisch mit Tags oder erweiterten Tags innerhalb einer benutzerdefinierten AEM-Anwendung arbeiten
seo-description: Programmatisch mit Tags oder erweiterten Tags innerhalb einer benutzerdefinierten AEM-Anwendung arbeiten
uuid: 0549552e-0d51-4162-b418-babf4ceee046
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 032aea1f-0105-4299-8d32-ba6bee78437f
translation-type: tm+mt
source-git-commit: 1493b301ecf4c25f785495e11ead352de600ddb7
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 50%

---


# Einbinden von Tagging in eine AEM-Anwendung{#building-tagging-into-an-aem-application}

Zum Zwecke von programmatischem Arbeiten mit Tags oder zum Erweitern von Tags in einer benutzerdefinierten AEM-Anwendung wird auf dieser Seite die Verwendung der

* [Tagging-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html),

die mit der

* [Tagging-Framework](/help/sites-developing/framework.md) interagiert, beschrieben.

Weitere Informationen zum Tagging finden Sie unter:

* [Tags](/help/sites-administering/tags.md) verwalten, um Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags zu erhalten.
* [Verwendung von Tags](/help/sites-authoring/tags.md) für Informationen zum Markieren von Inhalt.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](/help/sites-developing/framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. The TagManager ensures that tags entered as values on the `cq:tags` string array property are not duplicated, it removes TagIDs pointing to non-existing tags and updates TagIDs for moved or merged tags. TagManager verwendet einen JCR Observation Listener, der alle falschen Änderungen zurückgesetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* JcrTagManagerFactory - returns a JCR-based implementation of a `TagManager`. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` - ermöglicht das Auflösen und Erstellen von Tags anhand von Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

To retrieve a TagManager instance, you need to have a JCR `Session` and to call `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

Im typischen Sling-Kontext können Sie sich auch mit dem `TagManager` an einen `ResourceResolver` anpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Abrufen eines Tag-Objekts {#retrieving-a-tag-object}

Ein `Tag` kann über den `TagManager` abgerufen werden, indem entweder ein vorhandenes Tag aufgelöst oder ein neues erstellt wird:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

For the JCR-based implementation, which maps `Tags` onto JCR `Nodes`, you can directly use Sling&#39;s `adaptTo` mechanism if you have the resource (e.g. such as `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Obwohl ein Tag nur aus *einer Ressource (kein Knoten) konvertiert werden kann, kann ein Tag *in *sowohl eine Node als auch eine Ressource konvertiert werden:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Directly adapting from `Node` to `Tag` is not possible, because `Node` does not implement the Sling `Adaptable.adaptTo(Class)` method.

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

It is possible to use the replication service ( `Replicator`) with tags because tags are of type `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tagging auf der Clientseite {#tagging-on-the-client-side}

`CQ.tagging.TagInputField` ist ein Formular-Widget zum Eingeben von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen. Its xtype is `tags`.

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag-Müll-Collector ist ein Hintergrunddienst, der die Tags bereinigt, die ausgeblendet und nicht verwendet werden. Hidden and unused tags are tags below `/content/cq:tags` that have a `cq:movedTo` property and are not used on a content node - they have a count of zero. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil der Verschiebung oder dem Zusammenführungsvorgang aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Das Garbage Collector Tag wird standardmäßig einmal am Tag ausgeführt. Dies kann konfiguriert werden unter:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* The search for TagID searches for the tags that have the property `cq:movedTo` set to TagID and follows through the `cq:movedTo` TagIDs.

* The search for tag Title only searches the tags that do not have a `cq:movedTo` property.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

As described in the documentation for administering tags, in the section [Managing Tags in Different Languages](/help/sites-administering/tags.md#managing-tags-in-different-languages), a tag `title`can be defined in different languages. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft hat das Format `jcr:title.<locale>`, z.B. `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und &quot;_&quot;anstelle von &quot;-&quot;verwenden. Beispiel: `de_ch`.

When the **Animals** tag is added to the **Products** page, the value `stockphotography:animals` is added to the property `cq:tags` of the node /content/geometrixx/en/products/jcr:content. Die Übersetzung wird vom Tag-Knoten referenziert.

The server-side API has localized `title`-related methods:

* [com.day.cq.tagging.Tag](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(Locale locale)
   * getTitlePath(Locale locale)

* [com.day.cq.tagging.TagManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, Locale locale)
   * createTagByTitle(String tagTitlePath, Locale locale)
   * resolveByTitle(String tagTitlePath, Locale locale)

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Benutzersprache abgerufen werden:

* So rufen Sie die Seitensprache in einer JSP ab:

   * `currentPage.getLanguage(false)`

* So rufen Sie die Benutzersprache in einer JSP ab:

   * `slingRequest.getLocale()`

`currentPage` und `slingRequest` sind in einer JSP über das Tag [&lt;cq:definedObjects>](/help/sites-developing/taglib.md) verfügbar.

For tagging, localization depends on the context as tag `titles`can be displayed in the page language, in the user language or in any other language.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“{#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie eine neue Sprache (Finnisch) im Dialogfeld **Tag bearbeiten** hinzufügen:

1. In **CRXDE**, edit the multi-value property `languages` of the node `/content/cq:tags`.

1. Fügen Sie `fi_fi` hinzu, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Die neue Sprache (Finnisch) ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn Sie ein Tag in der **Tagging-Konsole** bearbeiten.

>[!NOTE]
>
>The new language needs to be one of the AEM recognized languages, i.e. it needs to be available as a node below `/libs/wcm/core/resources/languages`.

