---
title: 'Beispiele für ContextHub-Store-Kandidaten '
seo-title: 'Beispiele für ContextHub-Store-Kandidaten '
description: ContextHub bietet mehrere Beispiele für Store-Kandidaten, die Sie in Ihren Lösungen verwenden können
seo-description: ContextHub bietet mehrere Beispiele für Store-Kandidaten, die Sie in Ihren Lösungen verwenden können
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: d8d9a799-3e30-442a-843b-d4d7ba70c557
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 100%

---

# Beispiele für ContextHub-Store-Kandidaten {#sample-contexthub-store-candidates}

ContextHub bietet mehrere Beispiele für Store-Kandidaten, die Sie in Ihren Lösungen verwenden können. Die folgenden Informationen werden für jedes Beispiel bereitgestellt:

* Gibt an, wo der Quell-Code zu finden ist, damit Sie ihn zum Lernen öffnen können.
* Wie werden die Stores konfiguriert, die Sie aus den Store-Kandidaten erstellen.
* Wie sind die Store-Daten strukturiert, dasmit Sie darauf zugreifen können.

>[!WARNING]
>
>Die Beispiele für Store-Kandidaten werden als Referenzkonfigurationen bereitgestellt, um Ihnen bei der Einrichtung einer eigenen dedizierten Konfiguration für Ihr Projekt zu helfen, und sollten daher nicht direkt verwendet werden.

## Beispiel-Store-Kandidat „aem.segmentations“{#aem-segmentation-sample-store-candidate}

Store für gelöste und ungelöste ContextHub-Segmente. Ruft automatisch Segmente aus dem ContextHub SegmentManager zurück.

### Quellpfad {#source-location-segmentation}

`/libs/settings/cloudsettings/legacy/contexthub/segmentation`

### Basisimplementierung {#base-implementation-segmentation}

[`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)Der Store-Kandidat aem.segmentations erweitert.

### Konfiguration {#configuration-segmentation}

Wenn Sie einen aem.segmentation-Store erstellen, ist es nicht erforderlich, eine detaillierte Konfiguration zur Verfügung zu stellen. Die Standardkonfiguration gibt den Speicherort der ContextHub-Segmentdefinitionen an.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"/etc/segmentation/contexthub.segment.js"
   }
}
```

## Beispiel-Store-Kandidat „contexthub.geolocations“{#contexthub-geolocation-sample-store-candidate}

Der Beispiel-Store-Kandidat „contexthub.geolocation“ verwendet Google Maps zum Abrufen und Speichern von Informationen zum Clientstandort.

### Quellpfad {#source-location-geolocation}

`/libs/settings/cloudsettings/legacy/contexthub/geolocation`

### Basisimplementierung {#base-implementation-geolocation}

Der Store-Kandidat „contexthub.geolocation“ erweitert [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore).

### Konfiguration {#configuration-geolocation}

Die Standardkonfiguration enthält Informationen zum Google-Dienst und die anfänglichen Längen- und Breitenkoordinaten.

```xml
{
        "service": {
            "jsonp": false,
            "timeout": 1000,
            "ttl": 1800000,
            "secure": false,
            "host": "maps.googleapis.com",
            "port": 80,
            "path": "/maps/api/geocode/json"
        },

        "eventDeferring": 16,

        "html5coordinatesDiscoveryAPI": {
            "timeout": 30000,
            "ttl": 900000,
            "highAccuracy": false
        },

        "initialValues": {
            "latitude": 37.331375,
            "longitude": -121.893992
        }
    }
```

### Datenelemente {#data-items-geolocation}

Der Store verwendet einen Datenbaum, der dem folgenden Beispiel ähnelt:

```xml
{
   "latitude":"37.331375",
   "longitude":"-121.893992"
}
```

>[!NOTE]
>
>Eine in Chrome 50.x eingeführte Sicherheitsrichtlinie erfordert, dass alle Geolocation-bezogenen Anrufe über eine gesicherte Verbindung erfolgen. Daher erzwingt AEM die Verwendung von https für Geolocation-API-Aufrufe, wenn AEM auch über https ausgeführt wird. Andernfalls wird http verwendet, um der Richtlinie gleichen Ursprungs zu entsprechen. In [diesem Google-Blogpost](https://developers.google.com/web/updates/2016/04/geolocation-on-secure-contexts-only) erhalten Sie weitere Informationen zu den Änderungen in Chrome.

## Beispiel-Store-Kandidat „contexthub.surferinfo“   {#contexthub-surferinfo-sample-store-candidate}

Speichert Informationen über die aktuelle Client-Umgebung wie Gerät, Fenster, Browser, Datum und Uhrzeit.

### Quellpfad {#source-location-surferinfo}

`/libs/settings/cloudsettings/legacy/contexthub/surferinfo`

### Basisimplementierung {#base-implementation-surferinfo}

Der Store-Kandidat „contexthub.datetime“ erweitert [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore).

### Konfiguration {#configuration-surferinfo}

Die Standardkonfiguration wird von `ContextHub.Store.PersistedStore` übernommen.

### Datenelemente {#data-items-surferinfo}

Stores, die diesen Store-Kandidaten verwenden, haben eine Datenstruktur, die dem folgenden Beispiel ähnelt:

```xml
{
   "display":{
      "resolution":{
         "width":1440,
         "height":900
      },
      "devicePixelRatio":1,
      "colorDepth":24,
      "nrOfColors":16777216,
      "pixelsPerInch":96,
      "orientation":{
         "mode":"landscape",
         "direction":"normal"
      }
   },
   "window":{
      "dimension":{
         "width":1395,
         "height":652
      },
      "percentageUsage":0.7
   },
   "browser":{
      "version":"39.0",
      "family":"Firefox",
      "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:39.0) Gecko/20100101 Firefox/39.0"
   },
   "device":{
      "category":"Desktop",
      "type":"Desktop",
      "model":"PC",
      "version":""
   },
   "isMobile":true,
   "os":{
      "name":"Mac OS X",
      "version":"10"
   },
   "year":2015,
   "month":7,
   "day":22,
   "hour":14,
   "minutes":1
}
```

## Beispiel-Store-Kandidat „granite.emulators“ {#granite-emulators-sample-store-candidate}

Der Beispiel-Store-Kandidat „granite.emulators“ speichert Informationen über Kundengeräte.

### Quellpfad {#source-location-emulators}

`/libs/settings/cloudsettings/legacy/contexthub/emulators`

### Basisimplementierung {#base-implementation-emulators}

Der Store-Kandidat „contexthub.geolocation“ erweitert [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore).

### Konfiguration {#configuration-emulators}

Die Standardkonfiguration enthält ein Array namens `defaultEmulators`, das Informationen über verschiedene Geräte enthält. Wenn Sie einen Store erstellen, stellen Sie verschiedene Geräteprofile nach Bedarf in der Detailkonfigurationseigenschaft mithilfe des Formats bereit, das im folgenden Beispiel veranschaulicht wird:

```xml
{
   "defaultEmulators":[
        {
            "id": "iphone-6",
            "title": "iPhone 6",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 750,
            "height": 1334,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 2
        },
        {
            "id": "iphone-6-plus",
            "title": "iPhone 6 Plus",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        },
        {
            "id": "galaxy-s4",
            "title": "Samsung Galaxy S4",
            "type": "mobile",
            "platform": "Android",
            "platformVersion": "4.4.2 KitKat",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        }
    ]
}
```

### Datenelemente {#data-items-emulators}

Der Store-Datenbaum ähnelt dem folgenden Beispiel:

```xml
{
   "devices":[
      {"id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
      },
      {"id":"ipad-3",
      "title":"iPad 3 / 4 / Air",
      "type":"tablet",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":1536,
      "height":2048,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"iphone-6",
      "title":"iPhone 6",
      "type":"mobile",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":750,
      "height":1334,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"galaxy-s4",
      "title":"Samsung Galaxy S4",
      "type":"mobile",
      "platform":"Android",
      "platformVersion":"4.4.2 KitKat",
      "width":1080,
      "height":1920,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":3
      }
   ],
   "currentDeviceId":"native",
   "orientations":[
      {"id":"landscape",
      "title":"Landscape"
      },
      {"id":"portrait",
       "title":"Portrait"
      }
   ],
   "currentDevice":{
      "id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
   }
}
```

## Beispiel-Store-Kandidat „granite.profile“   {#granite-profile-sample-store-candidate}

Informationen über den aktuellen Benutzer.

### Quellpfad {#source-location-profile}

`/libs/settings/cloudsettings/legacy/contexthub/profile`

### Basisimplementierung {#base-implementation-profile}

Der Store-Kandidat „contexthub.datetime“ erweitert [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore).

### Konfiguration {#configuration-profile}

Die folgende Standardkonfiguration wird verwendet. Sie sollten diese Konfiguration nicht ändern.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"${contexthub:/store/profile/path}.infinity.json"
   },
   "initialValues":{"path":"/home/users/a/anonymous"}
}
```

### Datenelemente {#data-items-profile}

Stores, die diesen Store-Kandidaten verwenden, haben eine Datenstruktur, die dem folgenden Beispiel ähnelt:

```xml
{
   "displayName":"anonymous",
   "path":"/home/users/6/6zavE_DGre6Ad9Y5E0Ba",
   "avatar":"/etc/designs/default/images/social/avatar.png",
   "authorizableId":"anonymous"
}
```
