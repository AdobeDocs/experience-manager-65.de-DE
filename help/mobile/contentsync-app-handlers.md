---
title: Vordefinierte App-Handler
seo-title: Out of the Box App Handlers
description: Auf dieser Seite erfahren Sie mehr über die vordefinierten Handler für Adobe PhoneGap Enterprise mit AEM.
seo-description: Follow this page to learn about the out-of-the-box handlers for Adobe PhoneGap Enterprise with AEM.
uuid: 436038cb-fb76-4bb5-ae79-5d4043b81dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fec86f03-f81e-460a-9f84-d6304c95128c
exl-id: e2ddf5d1-0f5b-4f3b-9666-0f388915730e
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 0%

---

# Vordefinierte App-Handler{#out-of-the-box-app-handlers}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Beachten Sie die folgenden Richtlinien für die Entwicklung von Content Sync Handlern:

* Handler müssen implementieren *com.day.cq.contentsync.handler.ContentUpdateHandler* (entweder direkt oder erweitert eine Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler*
* Der Handler darf nur &quot;true&quot;melden, wenn er den ContentSync-Cache aktualisiert hat. Falsche Berichterstellung &quot;true&quot;ermöglicht AEM die Erstellung einer Aktualisierung.
* Der Handler sollte den Cache nur aktualisieren, wenn der Inhalt tatsächlich geändert wurde. Schreiben Sie nicht in den Cache, wenn kein Leerzeichen erforderlich ist, und vermeiden Sie eine unnötige Aktualisierung.

## Vordefinierte Handler {#out-of-the-box-handlers}

Im Folgenden werden vordefinierte App-Handler aufgeführt:

**mobileapppages** Gibt App-Seiten wieder.

* ***type - String*** - mobileAppages
* ***path - String*** - Pfad zu einer Seite
* ***extension - String*** - Erweiterung, die in der Anfrage verwendet werden soll. Für Seiten ist dies fast immer *html*, aber andere sind noch möglich.

* ***selector - String*** - Optionale Selektoren, getrennt durch Punkt. Häufige Beispiele *touch* zum Rendern mobiler Versionen einer Seite.

* ***deep - Boolesch*** - Optionale boolesche Eigenschaft, die bestimmt, ob auch untergeordnete Seiten einbezogen werden sollen. Der Standardwert ist *wahr.*

* ***includeImages - Boolean*** - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert ist *true*.

   * Standardmäßig werden nur Bildkomponenten mit dem Ressourcentyp foundation/components/image zur Aufnahme berücksichtigt.

* ***includeVideos - Boolean*** - Optionale boolesche Eigenschaft bestimmt, ob Videos einbezogen werden sollen. Der Standardwert ist *true*.

* ***includeModifiedPagesOnly - Boolean*** - Wenn false oder ausgelassen, werden alle Seiten gerendert und Aktualisierungen im Rendering überprüft. Wenn &quot;true&quot;, unterscheidet sich die Basis von Änderungen an Seiten lastModified.
* ***+ rewrite (Knoten)***
  ***- relativeParentPath - String*** - der Pfad zum Schreiben aller anderen Pfade relativ zu.

>[!NOTE]
>
>Der Ressourcentyp der Bild- und Videokomponenten, die von diesem Handler betroffen sind, wird durch Konfigurieren der Eigenschaften des *com.adobe.cq.mobile.platform.impl.contentsync.handler*.*MobilePagesUpdateHandler OSGi-Dienst*.

**mobilepageassets** Erfasst App-Seiten-Assets.

**mobilecontentlisting** Führt den Inhalt der ZIP-Datei ContentSync auf. Dies wird von der clientseitigen js auf dem Gerät verwendet, um die anfängliche Dateikopie zu erstellen, die für AEM Apps erforderlich ist.

Dieser Handler sollte zu jeder AEM Apps ContentSync-Konfiguration hinzugefügt werden.

* ***type - String - mobilecontentlisting***
* ***path*** - Zeichenfolge - Leer bleiben, muss als gültiger Handler vorhanden sein, aber der Pfad wird als aktueller ContentSync-Cache abgeleitet. Dieser Wert wird ignoriert.
* ***targetRootDirectory* -**Zeichenfolge - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**Reihenfolge für ContentSync zum Ausführen dieses Handlers. Diese Zahl sollte höher als alle anderen Handler wie 100 eingestellt werden. Sie sollte nach herkömmlichen Content-Handlern ausgeführt werden.

```xml
{
  "files": [
    "config.xml",
    "res/screens/ios/screen-ipad-portrait-2x.png",
    "res/screens/ios/screen-ipad-landscape.png",
    "res/screens/ios/screen-iphone-portrait-2x.png",
    "res/screens/ios/screen-iphone-landscape.png",
    "res/screens/ios/screen-iphone-portrait.png",
    "apps/weretail-app/components/splash-page/clientlibs.css",
    ...
    "pge-content-packages.json"
  ],
  "count": 382,
  "lastModified": 1422902754733
}
```

**mobilecontentpackageslisting** Listet das AEM Inhaltspaket in einer bestimmten App und die serverURL auf, an die Aktualisierungsanfragen gestellt werden sollen. Dies wird Client-seitig js auf dem Gerät verwendet, um Inhaltsaktualisierungen anzufordern

Der Handler sollte in AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String - mobilecontentpackageslisting***
* ***path **-**Zeichenfolge*** - Pfad zu einer App-Shell (Knoten mit page-type=app-instance).
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**Reihenfolge für ContentSync zum Ausführen dieses Handlers. Diese Zahl sollte höher als alle anderen Handler wie 100 eingestellt werden. Sie sollte nach herkömmlichen Content-Handlern ausgeführt werden.

>[!NOTE]
>
>Der folgende Codeblock ist keine exakte Implementierung und sollte als Referenzbeispiel verwendet werden:

```xml
{
  "content": [
    {
      "name": "en",
      "title": "We Retail Mobile App - English",
      "type": "CONTENT",
      "path": "/content/phonegap/weretail-outdoors/en",
      "updatePath": "/content/phonegap/weretail/en/jcr:content/pge-app/app-config"
    },
    {
      "name": "shell",
      "title": "We Retail Mobile App",
      "type": "INSTANCE",
      "path": "/content/phonegap/weretail-outdoors/shell",
      "updatePath": "/content/phonegap/weretail/shell/jcr:content/pge-app/app-config"
    }
  ],
  "serverURL": "http://localhost:4503/"
}
```

**widgetconfig** Enthält eine aktualisierte config.xml , die alle über das Command Center vorgenommenen Änderungen mit der bereitgestellten config.xml zusammenführt. Wenn dieser Handler keine App-Details enthält, die über die Administrationsoberfläche geändert wurden, werden sie nicht im Cache gespeichert.

Dieser Handler sollte in einer AEM App Shell ContentSync-Konfiguration verwendet werden (Knoten mit page-type=[app-instance]).

* ***type - String* - **widgetconfig
* ***path **-**Zeichenfolge*** - Pfad zu jedem untergeordneten Knoten der App-Shell (Knoten mit page-type=[app-instance]).
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***targetIconDirectory - String*** - das Verzeichnis, in dem die Symbole für die App platziert werden sollen

**mobileADBMobileConfigJSON** Schließen Sie die Datei ADBMobileConfig.JSON ein, wenn der AMS-Cloud-Service konfiguriert wurde.

Dies wird zur Kompilierungszeit verwendet, um das AMS-Plug-in für die Analyseunterstützung zu konfigurieren.

Der Handler sollte in AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String*** - mobileADBMobileConfigJSON
* ***path - String*** - Pfad zu einer App-Shell (Knoten mit page-type=app-instance oder einer RT, die /libs/mobileapps/core/components/instance erweitert)
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll

**notificationsconfig** Extrahiert die auf dem Gerät erforderlichen Benachrichtigungskonfigurationen. Die Eigenschaften werden aus der entsprechenden Push-Dienst-Cloud-Service-Konfiguration extrahiert, die mit der App verknüpft ist.

Nicht AEM-Eigenschaften im Knoten jcr:content des Cloud-Dienstes werden extrahiert und zum Knoten **pge-notifications-config.json** JSON-Datei zur Aufnahme in den www-Stamm des App-Inhalts.

AEM Eigenschaften sind diejenigen, die mit &quot;cq&quot;, &quot;sling&quot;oder &quot;jcr&quot;benannt werden. Andere Eigenschaften können mithilfe der Eigenschaft &quot;excludeProperties&quot;im Konfigurationsknoten content-sync ausgeschlossen werden.

* ***type - String*** - notificationsconfig
* ***excludeProperties - String[]*** - Eigenschaften, die ausgeschlossen werden

**contentsyncconfigcontent** Erfasst Inhalte aus einer vorhandenen ContentSync-Konfiguration.

* ***type - String*** - contentsyncconfigcontent
* ***path - String*** - Pfad zu einem von:

   * andere ContentSync-Konfiguration
   * zu einem Inhaltspaket hinzu (verwendet seine phonegap-exportTemplate-Eigenschaft, um die ContentSync-Konfiguration zu finden)
   * zu einer mobilen Ressource (App-Inhalte befinden sich unter dieser Ressource und wenn diese Inhaltspakete über eine Eigenschaft &quot;page-includeInBuild&quot;verfügen, die &quot;true&quot;ist, wird die phonegap-exportTemplate verwendet, um die ContentSync-Konfiguration zu finden).

* ***autoCreateFirstUpdateBeforeImport - Boolean*** - Wenn &quot;true&quot;, erstellen Sie eine erste **update** in der Zielkonfiguration vor dem Import, falls noch nicht einmal vorhanden

* ***autoFillBeforeImport - Boolean*** - Wenn &quot;true&quot;, aktualisieren/füllen Sie die Zielkonfiguration vor dem Import.
* ***configSuffix - String*** - eine Zeichenfolge, die an den in der Eigenschaft &quot;phonegap-exportTemplate&quot;von app-content angegebenen Pfad angehängt wird. Dies kann verwendet werden, um verschiedene Exportvorlagen zu unterscheiden. Diese Eigenschaft kann beispielsweise auf **&quot;-dev&quot;** um anzugeben, dass *&quot;/../../../appconfig-dev&quot;* verwendet werden (im Gegensatz zu *&quot;/../../../appconfig&quot;*).

**app-assets** Umfasst alle mit einer App-Instanz verknüpften Assets. Dieser Handler enthält alle unter dem angegebenen Pfad gefundenen Assets sowie alle Assets, die von der appAssetPath -Eigenschaft einer App-Instanz referenziert werden.

* ***type - String*** - app-assets

* ***path **-**Zeichenfolge*** - Pfad zu einem Speicherort unter einer App-Instanz, in der App-Assets gespeichert sind

**mobileappoffers** Für das Anwendungsbeispiel Personalisierung wurde ein neuer Content-Synchronisierungs-Handler eingeführt, um zielgerichtete Inhalte wiederzugeben. Der Handler &quot;mobileappoffers&quot;weiß, wie die zugehörigen Zielangebote gerendert werden, die vom Inhaltsautor erstellt wurden. Der Handler mobileappoffers erweitert den Aktualisierungs-Handler für abstrakte Seiten, weshalb viele der Eigenschaften ähnlich sind. Die Details des Handlers mobileappoffers haben die folgenden Eigenschaften.

Der Handler mobileappsoffers erweitert den Handler mobileappspages und fügt die folgenden Eigenschaften hinzu:

* ***locationRoot - String*** - den Speicherort der Mobile App angeben
* ***includePageTypes - String*** - unterstützt standardmäßig cq/personalization/components/teaserpage und cq/personalization/components/offerProxy
* ***selector - String*** - sollte auf &quot;Standard&quot;gesetzt werden
* ***path - String***- Pfad zur Marke der Kampagne

**mobileappconfig** Der Content-Synchronisierungs-Handler mobileappconfig bietet eine Möglichkeit, JSON-Daten in die Datei MobileAppsConfig.json einzufügen. Um eine Anbieterklasse zu registrieren, fügen Entwickler ihre MobileAppsInfoProvider-Klasse mit der Liste der Anbieter hinzu. Der Handler durchläuft die Liste der MobileAppsInfoProviders und ermöglicht es dem Provider, Daten in die resultierende JSON-Datei einzufügen. Die Liste der Eigenschaften, die dieser Handler unterstützt, lautet:

* ***path **-**Zeichenfolge*** - der Pfad zu einem App-Instanzknoten mit pageType=app-instance oder einem RT, der /libs/mobileapps/core/components/instance erweitert
* ***providers - String*** `[]` - die Liste der vollständig qualifizierten MobileAppsInfoProviders
* ***targetRootDirectory - String*** - das Verzeichnis, in das die Datei MobileAppsConfig.json geschrieben werden soll.
* **fileName - String** - optionaler Name der Datei, in die die JSON geschrieben werden soll, standardmäßig MobileAppsConfig.json

Es ist möglich, mehrere mobileAppconfig-Handler zu konfigurieren, die jeweils einen eindeutigen Satz von Providern enthalten, die in verschiedene JSON-Dateien schreiben.

### Inhaltssynchronisierungs-Handler testen {#testing-content-sync-handlers}

**Schritte zum Überprüfen der Integrität** Cache löschen

* Löschen des Cache
* Führen Sie Ihren Handler aus (Cache aktualisiert)
* Führen Sie den Handler erneut aus (Cache sollte nicht aktualisiert werden).

**Schritte zum Debugging**

* Ausführen der Konfiguration
* Exportieren Sie Ihre Konfiguration oder Überprüfung auf dem Gerät
* Wenn das Rendern fehlschlägt, suchen Sie nach fehlenden *styles/assets/libs* oder überprüfen Sie, ob der Pfad zu *styles/assets/libs*

**Protokollierung** Aktivieren Sie die ContentSync-Debug-Protokollierung über OSGi-Logger-Konfigurationen im Paket `com.day.cq.contentsync` Auf diese Weise können Sie verfolgen, welche Handler ausgeführt haben und ob sie den Cache aktualisiert und den Cache aktualisiert haben.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Um mit der Entwicklung von AEM Mobile-Apps zu beginnen, klicken Sie auf [here](/help/mobile/getting-started-aem-mobile.md).
