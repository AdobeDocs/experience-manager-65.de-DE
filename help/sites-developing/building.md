---
title: Einbinden von Tagging in eine AEM-Anwendung
seo-title: Einbinden von Tagging in eine AEM-Anwendung
description: Programmatisch mit Tags oder erweiterten Tags innerhalb eines benutzerdefinierten AEM-Programms arbeiten
seo-description: Programmatisch mit Tags oder erweiterten Tags innerhalb eines benutzerdefinierten AEM-Programms arbeiten
uuid: 0549552e-0d51-4162-b418-babf4ceee046
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 032aea1f-0105-4299-8d32-ba6bee78437f
feature: Tagging
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 75%

---


# Einbinden von Tagging in eine AEM-Anwendung{#building-tagging-into-an-aem-application}

Zum Zwecke von programmatischem Arbeiten mit Tags oder zum Erweitern von Tags in einer benutzerdefinierten AEM-Anwendung wird auf dieser Seite die Verwendung der

* [Tagging-API](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html),

die mit dem

* [Tagging-Framework](/help/sites-developing/framework.md) interagiert, beschrieben.

Weitere Informationen zum Tagging finden Sie unter:

* [Verwalten von ](/help/sites-administering/tags.md) Tags, um Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags zu erhalten.
* [Verwendung von Tags](/help/sites-authoring/tags.md) für Informationen zum Markieren von Inhalt.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](/help/sites-developing/framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API . Der TagManager stellt sicher, dass Tags, die als Werte in der String-Array-Eigenschaft eingegeben wurden, nicht dupliziert werden. Er entfernt TagIDs, die auf nicht vorhandene Tags verweisen, und aktualisiert TagIDs für verschobene oder zusammengeführte Tags. `cq:tags` TagManager verwendet einen JCR Observation Listener, der alle falschen Änderungen zurückgesetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* JcrTagManagerFactory - gibt eine JCR-basierte Implementierung eines `TagManager` zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` – ermöglicht das Auflösen und Erstellen von Tags nach Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

Um eine TagManager-Instanz abzurufen, müssen Sie über eine JCR `Session` verfügen und `getTagManager(Session)` aufrufen:

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

Für die JCR-basierte Implementierung, die `Tags` auf JCR-`Nodes` abbildet, können Sie den Mechanismus `adaptTo` von Sling direkt verwenden, wenn Sie die Ressource haben (z. B. `/content/cq:tags/default/my/tag`):

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

## Tagging auf der Clientseite {#tagging-on-the-client-side}

`CQ.tagging.TagInputField` ist ein Formular-Widget zum Eingeben von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen. Der xtype ist `tags`.

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag Garbage Collector ist ein Hintergrund-Service, der die ausgeblendeten und nicht verwendeten Tags bereinigt. Ausgeblendete und nicht verwendete Tags sind Tags unterhalb von `/content/cq:tags`, die eine `cq:movedTo`-Eigenschaft haben und nicht auf einem Inhaltsknoten verwendet werden - sie haben eine Zählung von Null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil der Verschiebung oder dem Zusammenführungsvorgang aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Das Garbage Collector Tag wird standardmäßig einmal am Tag ausgeführt. Dies kann konfiguriert werden unter:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* Die Suche nach TagID sucht nach den Tags, für die die Eigenschaft `cq:movedTo` auf TagID eingestellt ist, und folgt den TagIDs von `cq:movedTo`.

* Bei der Suche nach Tag-Titel werden nur die Tags durchsucht, die keine `cq:movedTo`-Eigenschaft haben.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Wie in der Dokumentation zur Verwaltung von Tags beschrieben, kann im Abschnitt [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) ein Tag `title`in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft weist das Format `jcr:title.<locale>` auf, beispielsweise `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und &quot;_&quot;anstelle von &quot;-&quot;verwenden. Beispiel:  `de_ch`.

Wenn das Tag **Tiere** der Seite **Produkte** hinzugefügt wird, wird der Wert `stockphotography:animals` der Eigenschaft `cq:tags` des Knotens /content/geometrixx/de/products/jcr:content hinzugefügt. Die Übersetzung wird vom Tag-Knoten referenziert.

Die Server-seitige API verfügt über lokalisierte `title`-bezogene Methoden:

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

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Anwendersprache abgerufen werden:

* So rufen Sie die Seitensprache in einer JSP ab:

   * `currentPage.getLanguage(false)`

* So rufen Sie die Benutzersprache in einer JSP ab:

   * `slingRequest.getLocale()`

`currentPage` und `slingRequest` sind in einer JSP über das Tag [&lt;cq:definedObjects>](/help/sites-developing/taglib.md) verfügbar.

Beim Tagging hängt die Lokalisierung vom Kontext ab, da Tag-`titles` in der Seitensprache, in der Anwendersprache oder in jeder anderen Sprache angezeigt werden können.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“ {#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie eine neue Sprache (Finnisch) im Dialogfeld **Tag bearbeiten** hinzufügen:

1. Bearbeiten Sie in **CRXDE** die Mehrwerteigenschaft `languages` des Knotens `/content/cq:tags`.

1. Fügen Sie `fi_fi` hinzu, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Die neue Sprache (Finnisch) ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn Sie ein Tag in der **Tagging-Konsole** bearbeiten.

>[!NOTE]
>
>Die neue Sprache muss eine der von AEM erkannten Sprachen sein, d. h. sie muss als Knoten unter `/libs/wcm/core/resources/languages` verfügbar sein.

