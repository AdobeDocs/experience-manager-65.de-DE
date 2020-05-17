---
title: Assets-HTTP-API in [!DNL Adobe Experience Manager].
description: Erstellen, lesen, aktualisieren, löschen, verwalten Sie digitale Assets mit der HTTP-API in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5d66bf75a6751e41170e6297d26116ad33c2df44
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 38%

---


# Assets-HTTP-API {#assets-http-api}

## Überblick {#overview}

The Assets HTTP API allows for create-read-update-delete (CRUD) operations on digital assets, including on metadata, on renditions, and on comments, together with structured content using [!DNL Experience Manager] Content Fragments. Sie wird unter `/api/assets` bereitgestellt und als REST-API implementiert. Dazu gehört die [Unterstützung von Inhaltsfragmenten](/help/assets/assets-api-content-fragments.md).

So greifen Sie auf die API zu:

1. Öffnen Sie das Dokument zum API-Dienst unter `https://[hostname]:[port]/api.json`.
1. Folgen Sie dem Link zum Assets-Dienst, der zu `https://[hostname]:[server]/api/assets.json` führt.

Die API antwortet mit einer JSON-Datei für einige MIME-Typen und einem Antwort-Code für alle MIME-Typen. Die JSON-Antwort ist optional und kann zum Beispiel nicht für PDF-Dateien verfügbar sein. Verwenden Sie den Antwortcode für weitere Analysen oder Aktionen.

After the [!UICONTROL Off Time], an asset and its renditions are not available via the [!DNL Assets] web interface and through the HTTP API. Die API gibt die Fehlermeldung 404 zurück, wenn die [!UICONTROL Einschaltzeit] in der Zukunft oder die [!UICONTROL Ausschaltzeit] in der Vergangenheit liegt.

## Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments.md) ist ein spezieller Asset-Typ. Er kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

For further information see [Content Fragments Support in the Experience Manager Assets HTTP API](/help/assets/assets-api-content-fragments.md).

## Datenmodell {#data-model}

Die Assets-HTTP-API stellt zwei wichtige Elemente bereit: Ordner und Assets (für Standard-Assets).

Außerdem stellt sie ausführlichere Elemente für die benutzerdefinierten Datenmodelle bereit, die strukturierte Inhalte in Inhaltsfragmenten beschreiben. Weitere Informationen finden Sie im Abschnitt [Datenmodelle für Inhaltsfragmente](/help/assets/assets-api-content-fragments.md#content-fragments).

### Ordner {#folders}

Ordner verhalten sich wie Verzeichnisse in traditionellen Dateisystemen. Sie stellen Container für andere Ordner oder Assets dar. Ordner enthalten folgende Komponenten:

**Entitäten**: Zu den Entitäten eines Ordners zählen die untergeordneten Elemente, z. B. die Ordner und Assets.

**Eigenschaften**:

* `name` ist der Name des Ordners. Dies entspricht dem letzten Segment im URL-Pfad ohne die Erweiterung.
* `title` ist ein optionaler Titel des Ordners, der anstelle seines Namens angezeigt werden kann.

>[!NOTE]
>
>Einige Eigenschaften des Ordners oder Assets sind einem anderen Präfix zugeordnet. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Links**-Ordner stellen drei Links bereit:

* `self`: Link zu sich selbst.
* `parent`: Link zum übergeordneten Ordner.
* `thumbnail`: (Optionaler) Link zu einem Ordnerminiaturbild.

### Assets {#assets}

In Experience Manager enthält ein Asset die folgenden Elemente:

* Die Eigenschaften und Metadaten des Assets.
* Mehrere Wiedergabeformate, z. B. das ursprüngliche Wiedergabeformat (das ursprünglich hochgeladene Asset), eine Miniaturansicht und viele andere Wiedergabeformate. Weitere Darstellungen können Bilder unterschiedlicher Größe, verschiedene Videokodierungen oder extrahierte Seiten aus PDF- oder Adobe InDesign-Dateien sein.
* Optionale Kommentare.

For information about elements in Content Fragments see [Content Fragments Support in Experience Manager Assets HTTP API](/help/assets/assets-api-content-fragments.md#content-fragments).

In Experience Manager verfügt ein Ordner über die folgenden Komponenten:

* Einrichtungen: Die untergeordneten Elemente von Assets sind ihre Darstellungen.
* Eigenschaften.
* Links.

Die Assets-HTTP-API bietet die folgenden Funktionen:

* Abrufen von Ordnerauflistungen.
* Erstellen von Ordnern.
* Erstellen von Assets.
* Aktualisieren der Asset-Binärdatei.
* Aktualisieren der Asset-Metadaten.
* Erstellen von Asset-Ausgabeformaten.
* Aktualisieren von Asset-Ausgabeformaten.
* Erstellen von Asset-Kommentaren.
* Kopieren von Ordnern oder Assets.
* Verschieben von Ordnern oder Assets.
* Löschen von Ordnern, Assets oder Wiedergabeformaten.

>[!NOTE]
>
>Zur besseren Lesbarkeit der folgenden Beispiele wird die vollständige cURL-Notation weggelassen. Tatsächlich korreliert die Notation mit [Resty](https://github.com/micha/resty), dem Skript-Wrapper für `cURL`.

**Voraussetzungen**

1. Wechseln zu `https://[aem_server]:[port]/system/console/configMgr`.
1. Navigate to **Adobe Granite CSRF Filter**.
1. Make sure the property **Filter Methods** includes: POST, PUT, DELETE.

## Abrufen von Ordnerauflistungen {#retrieve-a-folder-listing}

Ruft eine Siren-Darstellung eines vorhandenen Ordners und seiner untergeordneten Entitäten ab (Unterordner oder Assets).

**Anforderung**: `GET /api/assets/myFolder.json`

**Antwortcodes**: Die Antwortcodes sind:

* 200 - OK - Erfolg.
* 404 - NICHT GEFUNDEN - Ordner ist nicht vorhanden oder nicht verfügbar.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

**Antwort**: Die zurückgegebene Entitätsklasse ist ein Asset oder ein Ordner. Die Eigenschaften von enthaltenen Entitäten sind eine Untergruppe des gesamten Eigenschaftensatzes jeder Entität. Um eine vollständige Darstellung der Entität zu erreichen, sollten Kunden den Inhalt der URL abrufen, auf die der Link mit einem `rel` von `self` verweist.

## Erstellen von Ordnern {#create-a-folder}

Erstellt einen neuen Ordner `sling`: `OrderedFolder` im festgelegten Pfad. If a `*` is provided instead of a node name, the servlet uses the parameter name as node name. Akzeptiert als Anforderungsdaten wird entweder eine Siren-Darstellung des neuen Ordners oder ein Satz von Name-Wert-Paaren, kodiert als `application/www-form-urlencoded` oder `multipart`/ `form`- `data`. Dies ist dann sinnvoll, wenn Sie einen Ordner direkt aus einem HTML-Formular erstellen. Zusätzlich können die Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

Ein API-Aufruf schlägt mit einem `500` Antwortcode fehl, wenn der übergeordnete Knoten des angegebenen Pfads nicht vorhanden ist. Ein Aufruf gibt einen Antwortcode zurück, `409` wenn der Ordner bereits vorhanden ist.

**Parameter**: `name` ist der Ordnername.

**Anforderung**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwortcodes**: Die Antwortcodes sind:

* 201 - CREATED - bei erfolgreicher Erstellung.
* 409 - KONFLIKT - wenn bereits Ordner vorhanden.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Erstellen von Assets {#create-an-asset}

Platzieren Sie die bereitgestellte Datei am angegebenen Pfad, um ein Asset im DAM-Repository zu erstellen. If a `*` is provided instead of a node name, the servlet uses the parameter name or the file name as node name.

**Parameter**: Die Parameter beziehen sich `name` auf den Asset-Namen und `file` auf den Dateiverweis.

**Anforderung**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Antwortcodes**: Die Antwortcodes sind:

* 201 - ERSTELLT - wenn Asset erfolgreich erstellt wurde.
* 409 - KONFLIKT - wenn Asset bereits vorhanden.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Aktualisieren von Asset-Binärdateien {#update-asset-binary}

Aktualisiert die Binärdatei eines Assets (Darstellung mit dem Namen Original). Eine Aktualisierung löst die Ausführung des standardmäßigen Arbeitsablaufs für die Verarbeitung von Assets aus, sofern dieser konfiguriert ist.

**Anforderung**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Antwortcodes**: Die Antwortcodes sind:

* 200 - OK - wenn Asset erfolgreich aktualisiert wurde.
* 404 - NICHT GEFUNDEN - wenn Asset nicht gefunden oder unter dem angegebenen URI aufgerufen werden konnte.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Aktualisieren der Asset-Metadaten {#update-asset-metadata}

Aktualisiert die Asset-Metadateneigenschaften. Wenn Sie eine Eigenschaft im `dc:` Namensraum aktualisieren, aktualisiert die API dieselbe Eigenschaft im `jcr` Namensraum. Die API synchronisiert die Eigenschaften nicht unter den beiden Namensräumen.

**Anforderung**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwortcodes**: Die Antwortcodes sind:

* 200 - OK - wenn Asset erfolgreich aktualisiert wurde.
* 404 - NICHT GEFUNDEN - wenn Asset nicht gefunden oder unter dem angegebenen URI aufgerufen werden konnte.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Erstellen von Asset-Ausgabeformaten {#create-an-asset-rendition}

Erstellen Sie eine neue Asset-Darstellung für ein Asset. Wenn der Parametername der Anforderung nicht angegeben wird, wird der Dateiname als Darstellungsname verwendet.

**Parameter** Die Parameter werden `name` für den Namen der Darstellung und `file` als Dateiverweis verwendet.

**Anforderung**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwort-Codes**

* 201 - ERSTELLT - wenn die Darstellung erfolgreich erstellt wurde.
* 404 - NICHT GEFUNDEN - wenn Asset nicht gefunden oder unter dem angegebenen URI aufgerufen werden konnte.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Aktualisieren von Asset-Ausgabeformaten {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt ein Asset-Wiedergabeformat durch die neuen Binärdaten.

**Anforderung**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwortcodes** Die Antwortcodes sind:

* 200 - OK - wenn die Darstellung erfolgreich aktualisiert wurde.
* 404 - NICHT GEFUNDEN - wenn Asset nicht gefunden oder unter dem angegebenen URI aufgerufen werden konnte.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Hinzufügen eines Kommentars zu einem Asset {#create-an-asset-comment}

Erstellt einen neuen Asset-Kommentar.

**Parameter**: Die Parameter sind `message` für den Nachrichtentext des Kommentars und `annotationData` für die Anmerkungsdaten im JSON-Format bestimmt.

**Anforderung**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwortcodes**: Die Antwortcodes sind:

* 201 - ERSTELLT - wenn Kommentar erfolgreich erstellt wurde.
* 404 - NICHT GEFUNDEN - wenn Asset nicht gefunden oder unter dem angegebenen URI aufgerufen werden konnte.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Kopieren von Ordnern oder Assets {#copy-a-folder-or-asset}

Kopiert einen Ordner oder ein Asset, der unter dem angegebenen Pfad zu einem neuen Ziel verfügbar ist.

**Anforderungsheader**: Die Parameter sind:

* `X-Destination` - ein neuer Ziel-URI im API-Lösungsbereich, in den die Ressource kopiert werden soll.
* `X-Depth` - entweder `infinity` oder `0`. Die Verwendung kopiert `0` nur die Ressource und ihre Eigenschaften und nicht die untergeordneten Elemente.
* `X-Overwrite` - Verwenden Sie diese Option, `F` um zu verhindern, dass ein Asset am vorhandenen Ziel überschrieben wird.

**Anforderung**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwortcodes**: Die Antwortcodes sind:

* 201 - CREATED - wenn Ordner/Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 - KEIN INHALT - wenn der Ordner/das Asset an ein vorhandenes Ziel kopiert wurde.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn ein Anforderungsheader fehlt.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Verschieben von Ordnern oder Assets {#move-a-folder-or-asset}

Verschiebt einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**: Die Parameter sind:

* `X-Destination` - ein neuer Ziel-URI im API-Lösungsbereich, in den die Ressource kopiert werden soll.
* `X-Depth` - entweder `infinity` oder `0`. Die Verwendung kopiert `0` nur die Ressource und ihre Eigenschaften und nicht die untergeordneten Elemente.
* `X-Overwrite` - Verwenden Sie entweder `T` zum erzwingen des Löschens einer vorhandenen Ressource oder `F` um zu verhindern, dass eine vorhandene Ressource überschrieben wird.

**Anforderung**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Antwortcodes**: Die Antwortcodes sind:

* 201 - CREATED - wenn Ordner/Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 - KEIN INHALT - wenn der Ordner/das Asset an ein vorhandenes Ziel kopiert wurde.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn ein Anforderungsheader fehlt.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.

## Löschen eines Ordners, eines Assets oder eines Ausgabeformats {#delete-a-folder-asset-or-rendition}

Löscht eine Ressource (-tree) am angegebenen Pfad.

**Anforderung**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Antwortcodes**: Die Antwortcodes sind:

* 200 - OK - wenn der Ordner erfolgreich gelöscht wurde.
* 412 - PRECONDITION FEHLGESCHLAGEN - wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 - INTERNER SERVER-FEHLER - wenn etwas Anderes schiefgeht.
