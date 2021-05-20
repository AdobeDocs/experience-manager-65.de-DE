---
title: Vordefinierte App-Handler
seo-title: Vordefinierte App-Handler
description: Auf dieser Seite erfahren Sie mehr über die vordefinierten Handler für Adobe PhoneGap Enterprise mit AEM.
seo-description: Auf dieser Seite erfahren Sie mehr über die vordefinierten Handler für Adobe PhoneGap Enterprise mit AEM.
uuid: 436038cb-fb76-4bb5-ae79-5d4043b81dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fec86f03-f81e-460a-9f84-d6304c95128c
exl-id: e2ddf5d1-0f5b-4f3b-9666-0f388915730e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 2%

---

# Vordefinierte App-Handler{#out-of-the-box-app-handlers}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Beachten Sie die folgenden Richtlinien für die Entwicklung von Content Sync Handlern:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder erweitern Sie eine Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* erweitern.
* Handler dürfen nur &quot;true&quot;melden, wenn sie den ContentSync-Cache aktualisiert haben. Falsche Berichterstellung &quot;true&quot;ermöglicht AEM die Erstellung einer Aktualisierung.
* Der Handler sollte den Cache nur aktualisieren, wenn der Inhalt tatsächlich geändert wurde. Schreiben Sie nicht in den Cache, wenn kein Leerzeichen erforderlich ist, und vermeiden Sie eine unnötige Aktualisierung.

## Vordefinierte Handler {#out-of-the-box-handlers}

Im Folgenden werden vordefinierte App-Handler aufgeführt:

**** mobileapppagesRenders app pages.

* ***type - String***  - mobileappages
* ***path - String***  - Pfad zu einer Seite
* ***extension - String***  - Erweiterung, die in der Anfrage verwendet werden soll. Für Seiten ist dies fast immer *html*, aber andere sind noch möglich.

* ***selector - String***  - Optionale Selektoren, getrennt durch Punkt. Häufige Beispiele sind *touch* zum Rendern mobiler Versionen einer Seite.

* ***deep - Boolesch***  - Optionale boolesche Eigenschaft, die bestimmt, ob auch untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* ***includeImages - Boolesch***  - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

   * Standardmäßig werden nur Bildkomponenten mit dem Ressourcentyp foundation/components/image zur Aufnahme berücksichtigt.

* ***includeVideos - Boolesch***  - Die optionale boolesche Eigenschaft bestimmt, ob Videos einbezogen werden sollen. Der Standardwert lautet *true*.

* ***includeModifiedPagesOnly - Boolesch***  - Wenn false oder nicht angegeben, werden alle Seiten gerendert und Aktualisierungen beim Rendering überprüft. Wenn &quot;true&quot;, unterscheidet sich die Basis von Änderungen an Seiten lastModified.
* ***+ rewrite (Knoten)***
   ***- relativeParentPath - String***  - der Pfad zum Schreiben aller anderen Pfade relativ zu.

>[!NOTE]
>
>Der Ressourcentyp der Bild- und Videokomponenten, die von diesem Handler betroffen sind, wird durch Konfigurieren der Eigenschaften von *com.adobe.cq.mobile.platform.impl.contentsync.handler* festgelegt.*MobilePagesUpdateHandler OSGi-Dienst*.

**** mobilepageassetsErfasst App-Seiten-Assets.

**** mobilecontentlistingListet den Inhalt der ContentSync-ZIP auf. Dies wird von der clientseitigen js auf dem Gerät verwendet, um die anfängliche Dateikopie zu erstellen, die für AEM Apps erforderlich ist.

Dieser Handler sollte jeder AEM Apps ContentSync-Konfiguration hinzugefügt werden.

* ***type - String - mobilecontentlisting***
* ***path***  - Zeichenfolge - leer lassen, muss als gültiger Handler vorhanden sein, aber der Pfad wird als aktueller ContentSync-Cache abgeleitet. Dieser Wert wird ignoriert.
* ***targetRootDirectory* -**String - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**Order for ContentSync , um diesen Handler auszuführen. Diese Zahl sollte höher als alle anderen Handler wie 100 eingestellt werden. Sie sollte nach herkömmlichen Content-Handlern ausgeführt werden.

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

**** mobilecontentpackageslistingListet das AEM Inhaltspaket in einer bestimmten App sowie die serverURL auf, an die Aktualisierungsanfragen gestellt werden sollen. Dies wird Client-seitig js auf dem Gerät verwendet, um Inhaltsaktualisierungen anzufordern

Der Handler sollte in AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String - mobilecontentpackageslisting***
* ***path **-**String***  - Pfad zu einer App-Shell (Knoten mit page-type=app-instance).
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long*  - **Order for ContentSync , um diesen Handler auszuführen. Diese Zahl sollte höher als alle anderen Handler wie 100 eingestellt werden. Sie sollte nach herkömmlichen Content-Handlern ausgeführt werden.

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

**** widgetconfigEnthält eine aktualisierte config.xml , die alle über das Command Center vorgenommenen Änderungen mit einer bereitgestellten config.xml zusammenführt. Wenn dieser Handler keine App-Details enthält, die über die Administrationsoberfläche geändert wurden, werden sie nicht im Cache gespeichert.

Dieser Handler sollte in einer AEM App Shell ContentSync-Konfiguration verwendet werden (Knoten mit page-type=[app-instance]).

* ***type - String* - **widgetconfig
* ***path **-**String***  - Pfad zu einem beliebigen untergeordneten Knoten der App-Shell (Knoten mit page-type=[app-instance]).
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***targetIconDirectory - String***  - der Ordner, in dem die Symbole für die App platziert werden sollen

**** mobileADBMobileConfigJSONI Schließen Sie die Datei ADBMobileConfig.JSON ein, wenn der AMS-Cloud-Service konfiguriert wurde.

Dies wird zur Kompilierungszeit verwendet, um das AMS-Plug-in für die Analyseunterstützung zu konfigurieren.

Der Handler sollte in AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String***  - mobileADBMobileConfigJSON
* ***path - String***  - Pfad zu einer App-Shell (Knoten mit page-type=app-instance oder einem RT, der /libs/mobileapps/core/components/instance erweitert)
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll

**** notificationsconfigExtrahiert auf dem Gerät erforderliche Benachrichtigungskonfigurationen. Die Eigenschaften werden aus der entsprechenden Push-Dienst-Cloud-Service-Konfiguration extrahiert, die mit der App verknüpft ist.

AEM Eigenschaften, die nicht im Knoten jcr:content des Cloud-Dienstes enthalten sind, werden extrahiert und der JSON-Datei **pge-notifications-config.json** hinzugefügt, um sie in den www-Stamm des App-Inhalts aufzunehmen.

AEM Eigenschaften sind diejenigen, die mit &quot;cq&quot;, &quot;sling&quot;oder &quot;jcr&quot;benannt werden. Andere Eigenschaften können mithilfe der Eigenschaft &quot;excludeProperties&quot;im Konfigurationsknoten content-sync ausgeschlossen werden.

* ***type - String***  - notificationsConfig
* ***excludeProperties - String[]***  - Eigenschaften, die ausgeschlossen werden sollen

**** contentsyncconfigcontentErfasst Inhalte aus einer vorhandenen ContentSync-Konfiguration.

* ***type - String***  - contentsyncconfigcontent
* ***path - String***  - Pfad zu einem der folgenden Elemente:

   * andere ContentSync-Konfiguration
   * zu einem Inhaltspaket hinzu (verwendet seine phonegap-exportTemplate-Eigenschaft, um die ContentSync-Konfiguration zu finden)
   * zu einer Mobile-Ressource (App-Content&#39;s finden Sie unter dieser Ressource und wenn diese Inhaltspakete über eine page-includeInBuild -Eigenschaft verfügen, die wahr ist, wird die phonegap-exportTemplate verwendet, um die ContentSync-Konfiguration zu finden).

* ***autoCreateFirstUpdateBeforeImport - Boolesch***  - wenn &quot;true&quot;, erstellen Sie eine erste  **** Aktualisierung in der Zielkonfiguration, bevor Sie importieren, falls noch nicht vorhanden.

* ***autoFillBeforeImport - Boolesch***  - wenn &quot;true&quot;, aktualisieren/füllen Sie die Zielkonfiguration vor dem Import aus.
* ***configSuffix - String***  - eine Zeichenfolge, die an den Pfad angehängt wird, der in der Eigenschaft &quot;phonegap-exportTemplate&quot;von app-content angegeben ist. Dies kann verwendet werden, um verschiedene Exportvorlagen zu unterscheiden. Beispielsweise kann diese Eigenschaft auf **&quot;-dev&quot;** gesetzt werden, um anzugeben, dass *&quot;/../../../appconfig-dev&quot;* verwendet werden sollte (im Gegensatz zu *&quot;/../.././appconfig&quot;*).

**app-** assetsUmfasst alle mit einer App-Instanz verknüpften Assets. Dieser Handler enthält alle unter dem angegebenen Pfad gefundenen Assets sowie alle Assets, die von der appAssetPath -Eigenschaft einer App-Instanz referenziert werden.

* ***type - String***  - app-assets

* ***path **-**String***  - Pfad zu einem Speicherort unter einer App-Instanz, in der App-Assets gespeichert sind

**** mobileappoffersFür den Anwendungsfall Personalisierung wurde ein neuer Content-Synchronisierungs-Handler eingeführt, der zielgerichtete Inhalte rendert. Der Handler &quot;mobileappoffers&quot;weiß, wie die zugehörigen Zielangebote gerendert werden, die vom Inhaltsautor erstellt wurden. Der Handler mobileappoffers erweitert den Aktualisierungs-Handler für abstrakte Seiten, weshalb viele der Eigenschaften ähnlich sind. Die Details des Handlers mobileappoffers haben die folgenden Eigenschaften.

Der Handler mobileappsoffers erweitert den Handler mobileappspages und fügt die folgenden Eigenschaften hinzu:

* ***locationRoot - String***  - Geben Sie den Speicherort der Mobile App an
* ***includePageTypes - String***  - standardmäßig unterstützt cq/personalization/components/teaserpage und cq/personalization/components/offerProxy
* ***selector - String***  - should be set to tandt
* ***path - String*** - der Pfad zur Marke der Kampagne

**** mobileappconfigDer Content-Synchronisierungs-Handler mobileappconfig bietet eine Möglichkeit, JSON-Daten in die MobileAppsConfig.json einzufügen. Um eine Anbieterklasse zu registrieren, fügen Entwickler ihre MobileAppsInfoProvider-Klasse mit der Liste der Anbieter hinzu. Der Handler durchläuft die Liste der MobileAppsInfoProviders und ermöglicht es dem Provider, Daten in die resultierende JSON-Datei einzufügen. Die Liste der Eigenschaften, die dieser Handler unterstützt, lautet:

* ***path **-**String***  - der Pfad zu einem App-Instanzknoten mit page-type=app-instance oder einer RT, die /libs/mobileapps/core/components/instance erweitert
* ***providers - String*** `[]`  - die Liste der vollständig qualifizierten MobileAppsInfoProviders
* ***targetRootDirectory - String***  - der Ordner, in den die Datei MobileAppsConfig.json geschrieben werden soll.
* **fileName - Zeichenfolge**  - optionaler Name der Datei, in die die JSON geschrieben werden soll, standardmäßig MobileAppsConfig.json

Es ist möglich, mehrere mobileAppconfig-Handler zu konfigurieren, die jeweils einen eindeutigen Satz von Providern enthalten, die in verschiedene JSON-Dateien schreiben.

### Testen der Inhaltssynchronisierungs-Handler {#testing-content-sync-handlers}

**Schritte zum Überprüfen des** IntegrityClear-Cache

* Löschen des Cache
* Führen Sie Ihren Handler aus (Cache aktualisiert)
* Führen Sie den Handler erneut aus (Cache sollte nicht aktualisiert werden).

**Schritte zum Debugging**

* Ausführen der Konfiguration
* Exportieren Sie Ihre Konfiguration oder Überprüfung auf dem Gerät
* Wenn das Rendern fehlschlägt, suchen Sie nach fehlenden *styles/assets/libs* oder überprüfen Sie, ob die Pfade zu *styles/assets/libs* fehlen.

**** ProtokollierungAktivieren der ContentSync Debug-Protokollierung über OSGi-Logger-Konfigurationen im Paket  `com.day.cq.contentsync` Dies ermöglicht Ihnen, zu verfolgen, welche Handler ausgeführt haben und ob sie den Cache aktualisiert und den Cache aktualisiert haben.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Um mit der Entwicklung von AEM Mobile-Apps zu beginnen, klicken Sie [hier](/help/mobile/getting-started-aem-mobile.md).
