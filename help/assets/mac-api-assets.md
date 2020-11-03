---
title: '[!DNL Assets] HTTP-API.'
description: Erstellen, lesen, aktualisieren, löschen, verwalten Sie digitale Assets mit der HTTP-API in  [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: c3ae4447581d946554d792c68d31b47a6b67d5df
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 79%

---


# [!DNL Assets] HTTP-API {#assets-http-api}

## Überblick {#overview}

The [!DNL Assets] HTTP API allows for create-read-update-delete (CRUD) operations on digital assets, including on metadata, on renditions, and on comments, together with structured content using [!DNL Experience Manager] Content Fragments. Sie wird unter `/api/assets` bereitgestellt und als REST-API implementiert. Dazu gehört die [Unterstützung von Inhaltsfragmenten](/help/assets/assets-api-content-fragments.md).

So greifen Sie auf die API zu:

1. Öffnen Sie das Dokument zum API-Dienst unter `https://[hostname]:[port]/api.json`.
1. Follow the [!DNL Assets] service link leading to `https://[hostname]:[server]/api/assets.json`.

Die API antwortet mit einer JSON-Datei für einige MIME-Typen und einem Antwort-Code für alle MIME-Typen. Die JSON-Antwort ist optional und kann zum Beispiel nicht für PDF-Dateien verfügbar sein. Verwenden Sie den Antwortcode für weitere Analysen oder Aktionen.

Nach der [!UICONTROL Ausschaltzeit] sind ein Asset und seine Ausgabedarstellungen weder über die [!DNL Assets]-Web-Oberfläche noch über die HTTP-API verfügbar. Die API gibt die Fehlermeldung 404 zurück, wenn die [!UICONTROL Einschaltzeit] in der Zukunft oder die [!UICONTROL Ausschaltzeit] in der Vergangenheit liegt.

>[!CAUTION]
>
>[Die HTTP-API aktualisiert die Metadateneigenschaften](#update-asset-metadata) im `jcr` Namensraum. Die Metadateneigenschaften im `dc` Namensraum werden jedoch von der Benutzeroberfläche des Experience Managers aktualisiert.

## Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Er kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden. Da es einige Unterschiede zu `standard`-Assets (z. B. Bildern oder Dokumenten) gibt, gelten einige zusätzliche Regeln für die Verarbeitung von Inhaltsfragmenten.

Weitere Informationen finden Sie unter [Unterstützung von Inhaltsfragmenten in der Experience Manager Assets-HTTP-API](/help/assets/assets-api-content-fragments.md).

## Datenmodell {#data-model}

The [!DNL Assets] HTTP API exposes two major elements, folders and assets (for standard assets).

Außerdem stellt sie ausführlichere Elemente für die benutzerdefinierten Datenmodelle bereit, die strukturierte Inhalte in Inhaltsfragmenten beschreiben. Weitere Informationen finden Sie im Abschnitt [Datenmodelle für Inhaltsfragmente](/help/assets/assets-api-content-fragments.md#content-fragments).

### Ordner {#folders}

Ordner verhalten sich wie Verzeichnisse in traditionellen Dateisystemen. Sie stellen Container für andere Ordner oder Assets dar. Ordner enthalten folgende Komponenten:

**Entitäten**: Zu den Entitäten eines Ordners zählen die untergeordneten Elemente, z. B. die Ordner und Assets.

**Eigenschaften**:

* `name` ist der Name des Ordners. Dies entspricht dem letzten Segment im URL-Pfad ohne die Erweiterung.
* `title` Ist ein optionaler Titel des Ordners, der anstelle des Namens angezeigt werden kann

>[!NOTE]
>
>Einige Eigenschaften des Ordners oder Assets sind einem anderen Präfix zugeordnet. Das `jcr`-Präfix von `jcr:title`, `jcr:description` und `jcr:language` werden mit dem `dc`-Präfix ersetzt. Daher enthalten im zurückgegebenen JSON `dc:title` und `dc:description` die Werte aus `jcr:title` bzw. `jcr:description`.

**Links**-Ordner stellen drei Links bereit:

* `self`: Link zu sich selbst.
* `parent`: Link zum übergeordneten Ordner.
* `thumbnail`: (Optionaler) Link zu einem Ordnerminiaturbild.

### Assets {#assets}

Experience Managers ein Asset die folgenden Elemente enthält:

* Die Eigenschaften und Metadaten des Assets.
* Mehrere Ausgabedarstellungen, z. B. die ursprüngliche Ausgabedarstellung (das ursprünglich hochgeladene Asset), eine Miniaturansicht und viele andere Ausgabedarstellungen. Additional renditions may be images of different sizes, different video encodings, or extracted pages from PDF or [!DNL Adobe InDesign] files.
* Optionale Kommentare.

Weitere Informationen über Elemente in Inhaltsfragmenten finden Sie unter [Unterstützung von Inhaltsfragmenten in der Experience Manager Assets-HTTP-API](/help/assets/assets-api-content-fragments.md#content-fragments).

In [!DNL Experience Manager] enthält ein Ordner die folgenden Komponenten:

* Entitäten: Die untergeordneten Elemente von Assets sind die Ausgabedarstellungen.
* Eigenschaften.
* Links.

The [!DNL Assets] HTTP API includes the following features:

* [Abrufen von Ordnerauflistungen](#retrieve-a-folder-listing).
* [Erstellen eines Ordners](#create-a-folder).
* [Erstellen von Assets](#create-an-asset).
* [Aktualisieren der Asset-Binärdatei](#update-asset-binary).
* [Aktualisieren der Asset-Metadaten](#update-asset-metadata).
* [Erstellen von Asset-Ausgabedarstellungen](#create-an-asset-rendition).
* [Aktualisieren von Asset-Ausgabedarstellungen](#update-an-asset-rendition).
* [Erstellen von Asset-Kommentaren](#create-an-asset-comment).
* [Kopieren von Ordnern oder Assets](#copy-a-folder-or-asset).
* [Verschieben von Ordnern oder Assets](#move-a-folder-or-asset).
* [Löschen von Ordnern, Assets oder Ausgabedarstellungen](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Zur besseren Lesbarkeit der folgenden Beispiele wird die vollständige cURL-Notation weggelassen. Tatsächlich korreliert die Notation mit [Resty](https://github.com/micha/resty), dem Skript-Wrapper für `cURL`.

**Voraussetzungen**

* Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
* Navigate to **[!UICONTROL Adobe Granite CSRF Filter]**.
* Stellen Sie sicher, dass die Eigenschaft **[!UICONTROL Filtermethoden]** Folgendes umfasst: `POST`, `PUT`, `DELETE`.

## Abrufen von Ordnerauflistungen {#retrieve-a-folder-listing}

Ruft eine Siren-Darstellung eines vorhandenen Ordners und seiner untergeordneten Entitäten ab (Unterordner oder Assets).

**Anforderung**: `GET /api/assets/myFolder.json`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – Erfolg.
* 404 – NICHT GEFUNDEN – Ordner existiert nicht oder ist nicht zugänglich.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

**Antwort**: Die Klasse der zurückgegebenen Entität ist ein Asset oder ein Ordner. Die Eigenschaften der enthaltenen Entitäten bilden eine Teilmenge der vollständigen Eigenschaften jeder Entität. Um eine vollständige Darstellung der Entität zu erreichen, sollten Kunden den Inhalt der URL abrufen, auf die der Link mit einem `rel` von `self` verweist.

## Erstellen von Ordnern {#create-a-folder}

Erstellt einen neuen Ordner `sling`: `OrderedFolder` im festgelegten Pfad. Wenn statt eines Knotennamens ein `*` angegeben wird, verwendet das Servlet den Parameternamen als Knotennamen. Akzeptiert als Anforderungsdaten wird entweder eine Siren-Darstellung des neuen Ordners oder ein Satz von Name-Wert-Paaren, kodiert als `application/www-form-urlencoded` oder `multipart`/ `form`- `data`. Dies ist dann sinnvoll, wenn Sie einen Ordner direkt aus einem HTML-Formular erstellen. Zusätzlich können die Eigenschaften des Ordners als URL-Abfrageparameter angegeben werden.

Wenn der übergeordnete Knoten des angegebenen Pfades nicht vorhanden ist, schlägt der API-Aufruf mit einem Antwort-Code `500` fehl. Ein Aufruf gibt einen Antwort-Code `409` zurück, wenn der Ordner bereits vorhanden ist.

**Parameter**: `name` ist der Ordnername.

**Anforderung**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – bei erfolgreicher Erstellung.
* 409 – KONFLIKT – wenn der Ordner bereits existiert.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Erstellen von Assets {#create-an-asset}

Platzieren Sie die bereitgestellte Datei am angegebenen Pfad, um ein Asset im DAM-Repository zu erstellen. If a `*` is provided instead of a node name, the servlet uses the parameter name or the file name as node name.

**Parameter**: Die Parameter beziehen sich `name` auf den Asset-Namen und `file` auf den Dateiverweis.

**Anforderung**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 - ERSTELLT - wenn Asset erfolgreich erstellt wurde.
* 409 - KONFLIKT - wenn Asset bereits vorhanden.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Aktualisieren von Asset-Binärdateien {#update-asset-binary}

Aktualisiert die Binärdatei eines Assets (Darstellung mit dem Namen Original). Eine Aktualisierung löst die Ausführung des standardmäßigen Arbeitsablaufs für die Verarbeitung von Assets aus, sofern dieser konfiguriert ist.

**Anforderung**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn das Asset erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Aktualisieren der Asset-Metadaten {#update-asset-metadata}

Aktualisiert die Asset-Metadateneigenschaften. Wenn Sie eine Eigenschaft im `dc:`-Namespace aktualisieren, aktualisiert die API dieselbe Eigenschaft im `jcr`-Namespace. Die API synchronisiert die Eigenschaften unter den beiden Namespaces nicht.

**Anforderung**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn das Asset erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

### Metadaten-Aktualisierung zwischen `dc` und `jcr` Namensraum synchronisieren {#sync-metadata-between-namespaces}

Die API-Methode aktualisiert die Metadateneigenschaften im `jcr` Namensraum. Die mithilfe der Benutzeroberfläche vorgenommenen Aktualisierungen ändern die Metadateneigenschaften des `dc` Namensraums. Um die Metadatenwerte zwischen `dc` und `jcr` Namensraum zu synchronisieren, können Sie einen Workflow erstellen und Experience Manager konfigurieren, der beim Bearbeiten des Assets ausgeführt wird. Verwenden Sie ein ECMA-Skript, um die erforderlichen Metadateneigenschaften zu synchronisieren. Das folgende Beispielskript synchronisiert die Titelzeichenfolge zwischen `dc:title` und `jcr:title`.

```javascript
var workflowData = workItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH")
{
 var path = workflowData.getPayload().toString();
 var node = workflowSession.getSession().getItem(path);
 var metadataNode = node.getNode("jcr:content/metadata");
 var jcrcontentNode = node.getNode("jcr:content");
if (jcrcontentNode.hasProperty("jcr:title"))
{
 var jcrTitle = jcrcontentNode.getProperty("jcr:title");
 metadataNode.setProperty("dc:title", jcrTitle.toString());
 metadataNode.save();
}
}
```

## Erstellen von Asset-Ausgabedarstellungen {#create-an-asset-rendition}

Erstellt eine neue Asset-Ausgabedarstellung für ein Asset. Wenn der Name nicht als Anforderungsparameter angegeben wurde, wird der Dateiname als Ausgabedarstellungsname verwendet.

**Parameter**: Die Parameter sind `name` für den Namen der Ausgabedarstellung und `file` als ein Dateiverweis.

**Anforderung**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT - wenn die Ausgabedarstellung erfolgreich erstellt wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Aktualisieren von Asset-Ausgabeformaten {#update-an-asset-rendition}

Aktualisiert bzw. ersetzt ein Asset-Wiedergabeformat durch die neuen Binärdaten.

**Anforderung**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn die Ausgabedarstellung erfolgreich aktualisiert wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Hinzufügen eines Kommentars zu einem Asset {#create-an-asset-comment}

Erstellt einen neuen Asset-Kommentar.

**Parameter**: Die Parameter sind `message` für den Nachrichtentext des Kommentars und `annotationData` für die Anmerkungsdaten im JSON-Format bestimmt.

**Anforderung**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT - wenn der Kommentar erfolgreich erstellt wurde.
* 404 – NICHT GEFUNDEN – wenn das Asset nicht gefunden oder unter dem angegebenen URI nicht aufgerufen werden konnte.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Kopieren von Ordnern oder Assets {#copy-a-folder-or-asset}

Kopiert einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**: Die Parameter sind:

* `X-Destination` – ein neuer Ziel-URI im Bereich der API-Lösung, in den die Ressource kopiert werden soll.
* `X-Depth` – entweder `infinity` oder `0`. Mit `0` werden nur die Ressource und ihre Eigenschaften kopiert und nicht ihre untergeordneten Elemente.
* `X-Overwrite` – Verwenden Sie `F`, um ein Überschreiben eines Assets am vorhandenen Ziel zu verhindern.

**Anforderung**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – wenn der Ordner/das Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 – KEIN INHALT – wenn der Ordner/das Asset in ein vorhandenes Ziel kopiert wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn ein Anforderungs-Header fehlt.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Verschieben von Ordnern oder Assets {#move-a-folder-or-asset}

Verschiebt einen Ordner oder ein Asset in dem angegebenen Pfad in ein neues Ziel.

**Anforderungs-Header**: Die Parameter sind:

* `X-Destination` – ein neuer Ziel-URI im Bereich der API-Lösung, in den die Ressource kopiert werden soll.
* `X-Depth` – entweder `infinity` oder `0`. Mit `0` werden nur die Ressource und ihre Eigenschaften kopiert und nicht ihre untergeordneten Elemente.
* `X-Overwrite` Verwenden Sie entweder `T`, um das Löschen einer vorhandenen Ressource zu erzwingen, oder `F`, um das Überschreiben einer vorhandenen Ressource zu verhindern.

**Anforderung**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

Verwenden Sie nicht `/content/dam` in der URL. Ein Beispielbefehl zum Verschieben von Assets und Überschreiben vorhandener Assets:

```shell
curl -u admin:admin -X MOVE https://[aem_server]:[port]/api/assets/source/file.png -H "X-Destination: http://[aem_server]:[port]/api/assets/destination/file.png" -H "X-Overwrite: T"
```

**Antwort-Codes**: Die Antwort-Codes sind:

* 201 – ERSTELLT – wenn der Ordner/das Asset in ein nicht vorhandenes Ziel kopiert wurde.
* 204 – KEIN INHALT – wenn der Ordner/das Asset in ein vorhandenes Ziel kopiert wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn ein Anforderungs-Header fehlt.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Löschen eines Ordners, eines Assets oder einer Ausgabedarstellung {#delete-a-folder-asset-or-rendition}

Löscht eine Ressource(nstruktur) im angegebenen Pfad.

**Anforderung**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Antwort-Codes**: Die Antwort-Codes sind:

* 200 – OK – wenn der Ordner erfolgreich gelöscht wurde.
* 412 – VORBEDINGUNG FEHLGESCHLAGEN – wenn die Stammsammlung nicht gefunden oder nicht aufgerufen werden kann.
* 500 – INTERNER SERVER-FEHLER – wenn etwas anderes schief geht.

## Tipps und Einschränkungen {#tips-best-practices-limitations}

* [Die HTTP-API aktualisiert die Metadateneigenschaften](#update-asset-metadata) im `jcr` Namensraum. Die Metadateneigenschaften im `dc` Namensraum werden jedoch von der Benutzeroberfläche des Experience Managers aktualisiert.

* Die Asset-API gibt die vollständigen Metadaten nicht zurück. In der API werden die Namensraum hartcodiert und nur diese werden zurückgegeben. Wenn Sie vollständige Metadaten benötigen, prüfen Sie den Asset-Pfad `/jcr_content/metadata.json`.
