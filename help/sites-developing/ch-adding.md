---
title: Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher
description: Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen.
translation-type: tm+mt
source-git-commit: a8ba56849f6bb9f0cf6571fc51f4b5cae71620e0
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 67%

---


# Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher {#adding-contexthub-to-pages-and-accessing-stores}

hinzufügen Sie ContextHub auf Ihre Seiten, um die ContextHub-Funktionen zu aktivieren und Links zu den ContextHub-Javascript-Bibliotheken zu erstellen.

Die ContextHub-JavaScript-API ermöglicht den Zugriff auf die von ContextHub verwalteten Kontextdaten. Auf dieser Seite werden die Hauptfunktionen der API für den Zugriff auf und die Bearbeitung von Kontextdaten kurz beschrieben. Ausführlichere Informationen und Codebeispiele finden Sie unter den Links zur API-Referenzdokumentation.

## Hinzufügen von ContextHub zu einer Seitenkomponente {#adding-contexthub-to-a-page-component}

Um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-Javascript-Bibliotheken herzustellen, fügen Sie die Komponente `contexthub` im Abschnitt `head` Ihrer Seite ein. Der HTML-Code für Ihre Seitenkomponente sollte dem folgenden Beispiel entsprechen:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Beachten Sie, dass Sie auch konfigurieren müssen, ob die ContextHub-Symbolleiste im Vorschaumodus angezeigt werden soll. Siehe [Ein- und Ausblenden der ContextHub-Benutzeroberfläche](ch-configuring.md#showing-and-hiding-the-contexthub-ui).

## Informationen zu ContextHub-Speichern  {#about-contexthub-stores}

Verwenden Sie ContextHub-Speicher, um Kontextdaten beizubehalten. ContextHub bietet folgende Arten von Speichern, die die Grundlage für alle Speichertypen bilden:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle Speichertypen sind Erweiterungen der Klasse [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core). Weitere Informationen zur Erstellung eines neuen Speichertyps finden Sie unter [Erstellen benutzerdefinierter Speicher](ch-extend.md#creating-custom-store-candidates). Weitere Informationen zu Beispielspeichertypen finden Sie unter [Beispielkandidaten für ContextHub-Speicher](ch-samplestores.md).

### Beibehaltungsmodi  {#persistence-modes}

ContextHub-Speicher verwenden einen der folgenden Beibehaltungsmodi:

* **Lokal:** Verwendet „localStorage“ (HTML5), um Daten beizubehalten. Lokaler Speicher wird im Browser sitzungsübergreifend beibehalten.
* **Sitzung:** Verwendet HTML5-sessionStorage, um Daten zu erhalten. Sitzungsspeicher wird für die Dauer der Browsersitzung beibehalten und steht für alle Browserfenster zur Verfügung.
* **Cookie:** Verwendet die native Cookie-Unterstützung des Browsers für die Datenspeicherung. Cookie-Daten werden in HTTP-Anforderungen an den bzw. vom Server gesendet.
* **Window.name:** Verwendet die Eigenschaft „window.name“, um Daten beizubehalten.
* **Speicher:** Verwendet ein JavaScript-Objekt, um Daten beizubehalten.

ContextHub verwendet standardmäßig den lokalen Beibehaltungsmodus. Falls der Browser „localStorage“ (HTML5) nicht unterstützt oder nicht zulässt, wird die Sitzungsbeibehaltung verwendet. Falls der Browser „sessionStorage“ (HTML5) nicht unterstützt oder nicht zulässt, wird die Beibehaltung vom Typ „Window.name“ verwendet.

### Store-Daten {#store-data}

Store-Daten bilden intern eine Baumstruktur. Dadurch können Werte als primäre Typen oder als komplexe Objekte hinzugefügt werden. Wenn Sie Stores komplexe Objekte hinzufügen, bilden die Objekteigenschaften Verzweigungen in der Datenstruktur. Beispielsweise wird das folgende komplexe Objekt einem leeren Store mit dem Namen &quot;Speicherort&quot;hinzugefügt:

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

Die Baumstruktur der Store-Daten kann wie folgt dargestellt werden:

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

Die Baumstruktur definiert Datenelemente im Store als Schlüssel-Wert-Paare. Im obigen Beispiel entspricht der Schlüssel `/number` dem Wert `321` und der Schlüssel `/data/country` dem Wert `Switzerland`.

### Bearbeiten von Objekten {#manipulating-objects}

ContextHub bietet die [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree)-Klasse zum Manipulieren von JavaScript-Objekten. Mithilfe der Funktionen dieser Klasse können Sie JavaScript-Objekte bearbeiten, bevor Sie sie einem Store hinzufügen oder nachdem Sie sie aus einem Store abgerufen haben.

Darüber hinaus stellt die [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json)-Klasse Funktionen zum Serialisieren von Objekten in Stinge und Deserialisieren von Zeichenfolgen zu Objekten bereit. Verwenden Sie diese Klasse zur Verarbeitung von JSON-Daten, um Browser zu unterstützen, die die Funktionen `JSON.parse` und `JSON.stringify` nicht nativ enthalten.

## Interagieren mit ContextHub-Stores {#interacting-with-contexthub-stores}

Verwenden Sie das JavaScript-Objekt [`ContextHub`](contexthub-api.md#ui-event-constants), um einen Store als JavaScript-Objekt abzurufen. Nach dem Abrufen des Store-Objekts können Sie die darin enthaltenen Daten bearbeiten. Verwenden Sie die Funktion [`getAllStores`](contexthub-api.md#getallstores) oder [`getStore`](contexthub-api.md#getstore-name), um den Store abzurufen.

### Zugreifen auf Store-Daten {#accessing-store-data}

Die JavaScript-Klasse [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) definiert mehrere Funktionen zur Interaktion mit Speicherdaten. Die folgenden Funktionen ermöglichen das Speichern und Abrufen mehrerer in Objekten enthaltener Datenelemente:

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

Einzelne Datenelemente werden als Schlüssel-Wert-Paare gespeichert. Zum Speichern und Abrufen von Werten muss der entsprechende Schlüssel angegeben werden:

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

Beachten Sie, dass benutzerdefinierte Speicherkandidaten weitere Funktionen definieren können, die den Zugriff auf Store-Daten ermöglichen.

>[!NOTE]
>
>Standardmäßig sind ContextHub die derzeit bei Veröffentlichungsservern angemeldeten Benutzer nicht bekannt und solche Benutzer werden von ContextHub als anonyme Benutzer betrachtet.
>
>Sie können ContextHub über angemeldete Benutzer informieren, indem Sie den Profil Store laden. Siehe [Beispielcode für GitHub hier](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub-Ereignisse {#contexthub-eventing}

ContextHub enthält ein Ereignisframework, das automatische Reaktionen auf Store-Ereignisse ermöglicht. Jedes Storeobjekt enthält ein Objekt vom Typ [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing), das als Eigenschaft [`eventing`](contexthub-api.md#eventing) des Stores verfügbar ist. Verwenden Sie die Funktion [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) oder [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents), um eine JavaScript-Funktion an ein Store-Ereignis zu binden.

## Bearbeiten von Cookies mithilfe von ContextHub {#using-context-hub-to-manipulate-cookies}

Die ContextHub-API bietet browserübergreifende Unterstützung für die Behandlung von Browser-Cookies. Der [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie)-Namensraum definiert mehrere Funktionen zum Erstellen, Bearbeiten und Löschen von Cookies.

## Ermitteln aufgelöster ContextHub-Segmente {#determining-resolved-contexthub-segments}

Mit der ContextHub-Segment-Engine können Sie ermitteln, welche der registrierten Segmente im aktuellen Kontext aufgelöst werden. Verwenden Sie die Funktion „getResolvedSegments“ der Klasse [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager), um aufgelöste Segmente abzurufen. Verwenden Sie dann die Funktion `getName` oder `getPath` der Klasse [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment), um ein Segment zu testen.

### ContextHub-Segmente {#contexthub-segments}

ContextHub-Segmente werden unter dem Knoten `/conf/<site>/settings/wcm/segments` installiert.

Die folgenden Segmente werden mit der Tutorial-Site [WKND installiert.](getting-started.md)

* summer
* winter

Die Regeln zur Auflösung dieser Segmente werden wie folgt zusammengefasst:

* Zuerst wird der Speicher [geolocation](ch-samplestores.md#contexthub-geolocation-sample-store-candidate) verwendet, um die Breite des Benutzers zu bestimmen.
* Dann bestimmt das Datenelement für den Monat des [surferinfo store](ch-samplestores.md#contexthub-surferinfo-sample-store-candidate), in welcher Jahreszeit es sich in diesem Breitengrad befindet.

>[!WARNING]
>
>Die installierten Segmente werden als Referenzkonfigurationen bereitgestellt, um Ihnen bei der Erstellung Ihrer eigenen dedizierten Konfiguration für Ihr Projekt zu helfen und sollten daher nicht direkt verwendet werden.

## Debuggen von ContextHub {#debugging-contexthub}

Es gibt eine Reihe von Optionen zum Debugging von ContextHub, einschließlich der Erstellung von Protokollen. Weitere Informationen finden Sie unter [ContextHub konfigurieren.](ch-configuring.md#logging-debug-messages-for-contexthub)

## Überblick über das ContextHub-Framework {#see-an-overview-of-the-contexthub-framework}

ContextHub bietet eine [Diagnoseseite](ch-diagnostics.md), auf der Sie sich einen Überblick über das ContextHub-Framework verschaffen können.
