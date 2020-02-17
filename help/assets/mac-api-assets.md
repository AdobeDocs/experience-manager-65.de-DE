---
title: Assets-HTTP-API
description: Erfahren Sie mehr über die Implementierung, Datenmodelle und Funktionen der Assets-HTTP-API. Verwenden Sie die Assets-HTTP-API, um verschiedene Aufgaben rund um Assets auszuführen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Assets-HTTP-API {#assets-http-api}

## Überblick {#overview}

Die Assets HTTP-API ermöglicht die Erstellung, das Lesen, das Aktualisieren und Löschen (CRUD) von Vorgängen für Assets, einschließlich Binärdateien, Metadaten, Darstellungen und Kommentaren, sowie strukturierte Inhalte mit AEM Content Fragments. Es wird unter bereitgestellt `/api/assets` und als REST-API implementiert. Dazu gehört die [Unterstützung von Inhaltsfragmenten](/help/assets/assets-api-content-fragments.md).

So greifen Sie auf die API zu:

1. Open the API service document at `https://[hostname]:[port]/api.json`.
1. Follow the Assets service link leading to `https://[hostname]:[server]/api/assets.json`.

Die API-Antwort ist eine JSON-Datei für einige Mime-Typen und ein Antwortcode für alle Mime-Typen. Die JSON-Antwort ist optional und kann zum Beispiel nicht für PDF-Dateien verfügbar sein. Verwenden Sie den Antwortcode für weitere Analysen oder Aktionen.

Nach der [!UICONTROL Abschaltzeit]sind ein Asset und seine Darstellungen weder über die Assets-Weboberfläche noch über die HTTP-API verfügbar. Die API gibt die Fehlermeldung 404 zurück, wenn die [!UICONTROL On-Zeit] in der Zukunft liegt oder die [!UICONTROL Off-Zeit] in der Vergangenheit liegt.

## Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments.md) ist ein spezieller Asset-Typ. Er kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

Weitere Informationen finden Sie unter [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/assets-api-content-fragments.md). 

## Datenmodell {#data-model}

Die Assets-HTTP-API stellt zwei wichtige Elemente bereit: Ordner und Assets (für Standard-Assets).

Außerdem stellt sie ausführlichere Elemente für die benutzerdefinierten Datenmodelle bereit, die strukturierte Inhalte in Inhaltsfragmenten beschreiben. Weitere Informationen finden Sie im Abschnitt [Datenmodelle für Inhaltsfragmente](/help/assets/assets-api-content-fragments.md#content-fragments).

### Ordner {#folders}

Ordner sind wie Ordner in herkömmlichen Dateisystemen. Sie stellen Container für andere Ordner oder Assets dar. Ordner enthalten folgende Komponenten:

**Einrichtungen**: Bei den Entitäten eines Ordners handelt es sich um untergeordnete Elemente, bei denen es sich um Ordner und Assets handeln kann.

**Eigenschaften**:
* `name`  — Name des Ordners. Dies ist dasselbe wie das letzte Segment im URL-Pfad ohne Erweiterung
* `title` — Optionaler Titel des Ordners, der anstelle des Namens angezeigt werden kann

>[!NOTE]
>
>Einige Funktionen des Ordners oder des Assets sind einem anderen Präfix zugeordnet. Das `jcr` Präfix `jcr:title`, `jcr:description`und `jcr:language` werden durch das `dc` Präfix ersetzt. Hence in the returned JSON, `dc:title` and `dc:description` contain the values of `jcr:title` and `jcr:description`, respectively.

**Links** Ordner stellen drei Links offen:
* `self`: Link zu sich selbst
* `parent`: Link zum übergeordneten Ordner
* `thumbnail`: (Optional) Link zu einem Ordnerminiaturbild

### Assets {#assets}

In AEM enthalten Assets die folgenden Elemente:

* Die Eigenschaften und Metadaten des Assets
* Mehrere Wiedergabeformate, z. B. das ursprüngliche Wiedergabeformat (das ursprünglich hochgeladene Asset), eine Miniaturansicht und viele andere Wiedergabeformate. Bei den zusätzlichen Wiedergabeformaten kann es sich um Bilder unterschiedlicher Größe, unterschiedliche Videokodierungen oder aus PDF- oder InDesign-Dateien extrahierte Seiten handeln.
* Optionale Kommentare

Weitere Informationen über Elemente in Inhaltsfragmenten finden Sie unter [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/assets-api-content-fragments.md#content-fragments). 

In AEM enthält ein Ordner die folgenden Komponenten:

* Einrichtungen: Die untergeordneten Elemente von Assets sind ihre Darstellungen.
* Eigenschaften
* Links

Die Assets-HTTP-API bietet die folgenden Funktionen:

* Abrufen von Ordnerauflistungen
* Erstellen von Ordnern
* Erstellen von Assets
* Aktualisieren der Asset-Binärdatei
* Aktualisieren der Asset-Metadaten
* Erstellen von Asset-Wiedergabeformaten
* Aktualisieren von Asset-Wiedergabeformaten
* Erstellen von Asset-Kommentaren
* Kopieren von Ordnern oder Assets
* Verschieben von Ordnern oder Assets
* Löschen von Ordnern, Assets oder Wiedergabeformaten

>[!NOTE]
>
>Zur besseren Lesbarkeit der folgenden Beispiele wird die vollständige cURL-Notation weggelassen. In fact the notation does correlate with [Resty](https://github.com/micha/resty) which is a script wrapper for `cURL`.

**Voraussetzungen**

* Wechseln zu `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.

## Abrufen von Ordnerauflistungen {#retrieve-a-folder-listing}

Ruft eine Siren-Darstellung eines vorhandenen Ordners und seiner untergeordneten Entitäten ab (Unterordner oder Assets).

**Anforderung**

```
GET /api/assets/myFolder.json
```

**Antwortcodes**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**Antwort**

Die zurückgegebene Entitätsklasse lautet assets/folder.

Die Eigenschaften der enthaltenen Entitäten bilden eine Untergruppe der vollständigen Eigenschaften einer jeden Entität. In order to obtain a full representation of the entity, clients should retrieve the contents of the URL pointed to by the link with a `rel` of `self`.

## Erstellen eines Ordners {#create-a-folder}

Creates a new `sling`: `OrderedFolder` at the given path. Wenn ein * anstelle eines Knotennamens angegeben wird, verwendet das Servlet den Parameternamen als Knotenname. Accepted as request data is either a Siren representation of the new folder or a set of name-value pairs, encoded as `application/www-form-urlencoded` or `multipart`/ `form`- `data`, useful for creating a folder directly from an HTML form. Zusätzlich können die Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

The operation will fail with a `500` response code if the parent node of the given path does not exist. If the folder already exists a `409` response code is returned.

**Parameter**

* `name` - Ordnername

**Anforderung**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

 oder  ermöglichen.

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**Antwortcodes**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Assets {#create-an-asset}

Erstellt ein DAM-Asset in dem angegebenen Pfad mit der angegebenen Datei. Wenn ein * anstelle eines Knotennamens angegeben wird, verwendet das Servlet den Parameternamen oder den Dateinamen als Knotennamen.

**Parameter**

* `name` - Asset-Name
* `file` - Dateireferenz

**Anforderung**

```
POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"
```

 oder  ermöglichen.

```
POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"
```

**Antwortcodes**

```
201 - CREATED - if Asset has been created successfully
409 - CONFLICT - if Asset already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aktualisieren der Asset-Binärdatei {#update-asset-binary}

Aktualisiert eine Asset-Binärdatei (Darstellung mit dem Namen Original). Dadurch wird der standardmäßige Asset-Workflow ausgelöst, wenn er entsprechend konfiguriert ist.

**Anforderung**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png
```

**Antwortcodes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aktualisieren der Asset-Metadaten {#update-asset-metadata}

Aktualisiert die Asset-Metadateneigenschaften. Wenn Sie eine Eigenschaft im `dc:` Namespace aktualisieren, aktualisiert die API dieselbe Eigenschaft im `jcr` -Namespace. Die API synchronisiert die Eigenschaften nicht unter den beiden Namespaces.

**Anforderung**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**Antwortcodes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Asset-Wiedergabeformaten {#create-an-asset-rendition}

Erstellt ein neues Asset-Wiedergabeformat für ein Asset. Wenn der Parametername der Anforderung nicht angegeben ist, wird der Dateiname als Darstellungsname verwendet.

**Parameter**

* `name` - Name der Darstellung
* `file` - Dateireferenz

**Anforderung**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

 oder  ermöglichen.

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**Antwortcodes**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aktualisieren von Asset-Wiedergabeformaten {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt ein Asset-Wiedergabeformat durch die neuen Binärdaten.

**Anforderung**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**Antwortcodes**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Erstellen von Asset-Kommentaren {#create-an-asset-comment}

Erstellt einen neuen Asset-Kommentar.

**Parameter**

* `message` - Nachricht
* `annotationData` - Anmerkungsdaten (JSON)

**Anforderung**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**Antwortcodes**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Kopieren von Ordnern oder Assets {#copy-a-folder-or-asset}

Kopiert einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**Anforderung**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**Antwortcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Verschieben von Ordnern oder Assets {#move-a-folder-or-asset}

Verschiebt einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**Anforderung**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**Antwortcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Löschen von Ordnern, Assets oder Wiedergabeformaten {#delete-a-folder-asset-or-rendition}

Löscht eine Ressource (Struktur) in dem angegebenen Pfad.

**Anforderung**

```
DELETE /api/assets/myFolder
```

 oder  ermöglichen.

```
DELETE /api/assets/myFolder/myAsset.png
```

 oder  ermöglichen.

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**Antwortcodes**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```
