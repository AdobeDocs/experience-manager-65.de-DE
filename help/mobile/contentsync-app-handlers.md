---
title: Vorkonfigurierte App-Handler
description: Auf dieser Seite erfahren Sie mehr über die nativen Handler für Adobe PhoneGap Enterprise mit AEM.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: e2ddf5d1-0f5b-4f3b-9666-0f388915730e
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 0%

---

# Vorkonfigurierte App-Handler{#out-of-the-box-app-handlers}

{{ue-over-mobile}}

Siehe die folgenden Richtlinien für die Entwicklung von Inhaltssynchronisierungs-Handlern:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder durch Erweiterung einer Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler erweitern*
* Handler dürfen nur dann „true“ melden, wenn sie den ContentSync-Cache aktualisiert haben. Wenn Sie fälschlicherweise „true“ melden, kann AEM eine Aktualisierung erstellen.
* Handler sollten den Cache nur aktualisieren, wenn der Inhalt tatsächlich geändert wurde. Schreiben Sie nicht in den Cache, wenn kein White erforderlich ist, und vermeiden Sie eine unnötige Update-Erstellung.

## Vorkonfigurierte Handler {#out-of-the-box-handlers}

Im Folgenden sind vordefinierte App-Handler aufgeführt:

**mobileAppages** Rendert App-Seiten.

* ***type - Zeichenfolge*** - mobileAppages
* ***path - String*** - Pfad zu einer Seite
* ***extension - String*** - Erweiterung, die in der Anfrage verwendet werden sollte. Bei Seiten ist dies fast immer *HTML*, aber andere sind immer noch möglich.

* ***selector - String*** - Optionale Selektoren, durch einen Punkt getrennt. Häufige Beispiele sind *Touch* für das Rendern mobiler Versionen einer Seite.

* ***deep - boolean*** - Optionale boolesche Eigenschaft, die bestimmt, ob auch untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* ***includeImages - Boolescher Wert*** - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

   * Standardmäßig werden nur Bildkomponenten mit dem Ressourcentyp „foundation/components/image“ für die Aufnahme berücksichtigt.

* ***includeVideos - Boolesch*** - Optionale boolesche Eigenschaft, die bestimmt, ob Videos einbezogen werden sollen. Der Standardwert lautet *true*.

* ***includeModifiedPagesOnly - Boolescher Wert*** - Wenn der Wert „false“ oder ausgelassen wird, werden alle Seiten gerendert und Aktualisierungen im Rendering überprüft. Wenn „true“, basieren die Unterschiede auf Änderungen an „lastModified“-Seiten.
* ***+ rewrite (Knoten)***
  ***- relativeParentPath - String*** - der Pfad, auf den alle anderen Pfade relativ geschrieben werden sollen.

>[!NOTE]
>
>Der Ressourcentyp der Bild- und Videokomponenten, die von diesem Handler betroffen sind, wird durch Konfigurieren der Eigenschaften von *com.adobe.cq.mobile.platform.impl.contentSync.handler* festgelegt.*MobilePagesUpdateHandler-OSGi-Dienst*.

**mobilepageassets** Erfasst Seiten-Assets für die App.

**mobilecontentlisting** Listet den Inhalt der ContentSync-Zip auf. Dies wird von Client-seitigen js auf dem Gerät verwendet, um die für AEM-Apps erforderliche erste Dateikopie durchzuführen.

Dieser Handler sollte zu jeder ContentSync-Konfiguration für AEM-Apps hinzugefügt werden.

* ***type - String - mobilecontentlisting***
* ***path*** - Zeichenfolge - leer lassen, muss vorhanden sein, um als gültiger Handler erkannt zu werden, der Pfad wird jedoch als aktueller ContentSync-Cache abgeleitet. Dieser Wert wird ignoriert.
* ***targetRootDirectory* -**&#x200B;String - Das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**&#x200B;Reihenfolge, in der ContentSync diesen Handler ausführt. Diese Zahl sollte höher als bei allen anderen Handlern (z. B. 100) eingestellt werden. Sie sollte nach herkömmlichen Inhalts-Handlern ausgeführt werden.

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

**mobilecontentpaketlisting** Listet das AEM-Inhaltspaket in einer bestimmten App und die Server-URL auf, an die Aktualisierungsanfragen gesendet werden sollen. Dies wird auf dem Client-seitigen JS-Gerät verwendet, um Inhaltsaktualisierungen anzufordern

Der Handler sollte in der ContentSync-Konfiguration der AEM-App-Shell (Knoten mit „page-type=app-instance„) verwendet werden.

* ***type - String - mobilecontentpaketlisting***
* ***path &#x200B;**-**String*** - Pfad zu einer App-Shell (Knoten mit pge-type=app-instance).
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**&#x200B;Reihenfolge für ContentSync, um diesen Handler auszuführen. Diese Zahl sollte höher als bei allen anderen Handlern (z. B. 100) eingestellt werden. Sie sollte nach herkömmlichen Inhalts-Handlern ausgeführt werden.

>[!NOTE]
>
>Der folgende Code-Block ist keine exakte Implementierung und sollte als Referenzbeispiel verwendet werden:

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

**widgetconfig** Enthält eine aktualisierte config.xml, die alle über das Command Center vorgenommenen Änderungen mit einer bereitgestellten config.xml zusammenführt. Wenn dieser Handler nicht enthalten ist, werden alle App-Details, die über die Administrationsoberfläche geändert werden, nicht in den Cache aufgenommen.

Dieser Handler sollte in einer Shell-ContentSync-Konfiguration der AEM-App verwendet werden (Knoten mit pge-type=[app-instance]).

* ***type - Zeichenfolge* - &#x200B;** widgetConfig
* ***path &#x200B;**-**String*** - Pfad zu einem beliebigen untergeordneten App-Shell-Knoten (Knoten mit pge-type=[app-instance]).
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***targetIconDirectory - String*** - der Ordner, in dem die Symbole für die App platziert werden sollen

**mobileADBMobileConfigJSON** Schließen Sie die Datei „ADBMobileConfig.JSON“ ein, wenn der AMS-Cloud-Service konfiguriert wurde.

Dies wird zur Kompilierungszeit verwendet, um das AMS-Plug-in für die Analytics-Unterstützung zu konfigurieren.

Der Handler sollte in der ContentSync-Konfiguration der AEM-App-Shell (Knoten mit „page-type=app-instance„) verwendet werden.

* ***type - Zeichenfolge*** - mobileADBMobileConfigJSON
* ***path - String*** - Pfad zu einer App-Shell (Knoten mit pge-type=app-instance oder einem RT, der /libs/mobileapps/core/components/instance erweitert)
* ***targetRootDirectory - String*** - das Präfix, das Pfaden als Zielstamm für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll

**notificationsconfig** Extrahiert die auf dem Gerät erforderlichen Benachrichtigungskonfigurationen. Die Eigenschaften werden aus der entsprechenden Push-Service-Cloud-Service-Konfiguration extrahiert, die mit der App verknüpft ist.

Nicht-AEM-Eigenschaften im Knoten „jcr:content“ des Cloud-Service werden extrahiert und der JSON-Datei &quot;**-notifications-config.json** hinzugefügt, um sie in den WWW-Stamm des App-Inhalts aufzunehmen.

AEM-Eigenschaften sind diejenigen, die durch „cq“, „sling“ oder „jcr“ mit Namensraum versehen sind. Andere Eigenschaften können mithilfe der Eigenschaft „excludeProperties“ im Knoten content-syncConfig ausgeschlossen werden.

* ***type - String*** - notificationsConfig
* ***excludeProperties - Zeichenfolge[]*** - auszuschließende Eigenschaften

**contentsyncconfigcontent** Erfasst Inhalte aus einer vorhandenen ContentSync-Konfiguration.

* ***type - String*** - contentSyncConfigContent
* ***path - String*** - Pfad zu einer der folgenden:

   * eine andere ContentSync-Konfiguration
   * zu einem Inhaltspaket hinzufügen (wird seine phonegap-exportTemplate-Eigenschaft verwenden, um seine ContentSync-Konfiguration zu finden)
   * zu einer mobilen Ressource hinzufügen (App-content wird unter dieser Ressource gefunden und wenn diese Inhaltspakete eine page-includeInBuild-Eigenschaft aufweisen, die „true“ ist, wird die phonegap-exportTemplate verwendet, um die ContentSync-Konfiguration zu finden)

* ***autoCreateFirstUpdateBeforeImport - Boolesch*** - Wenn „true“, erstellen Sie eine erste **Aktualisierung** in der Zielkonfiguration, bevor Sie importieren, falls „once“ noch nicht vorhanden ist

* ***autoFillBeforeImport - Boolesch*** - Wenn „true“, aktualisieren/füllen Sie die Zielkonfiguration vor dem Import
* ***configSuffix - String*** - eine Zeichenfolge, die an den Pfad angehängt werden soll, der in der Eigenschaft „phonegap-exportTemplate“ von app-content angegeben ist. Dies kann verwendet werden, um verschiedene Exportvorlagen zu unterscheiden. Beispielsweise kann diese Eigenschaft auf **&quot;-dev“** gesetzt werden, um anzugeben, dass *&quot;/…/…/appconfig-dev“* verwendet werden soll (im Gegensatz zu *&quot;/…/…/appconfig“*).

**app-assets** Enthält alle Assets, die mit einer App-Instanz verbunden sind. Dieser Handler enthält alle Assets, die unter dem angegebenen Pfad gefunden werden, sowie alle Assets, auf die von der appAssetPath-Eigenschaft einer Anwendungsinstanz verwiesen wird.

* ***type - Zeichenfolge*** - app-assets

* ***path &#x200B;**-**String*** - Pfad zu einem Speicherort unter einer Anwendungsinstanz, in dem Anwendungselemente gespeichert werden

**mobileAppOffers** Für den Personalization-Anwendungsfall zum Rendern zielgerichteter Inhalte wurde ein neuer Inhaltssynchronisierungs-Handler eingeführt. Der Handler &#39;mobileAppOffers&#39; weiß, wie die zugehörigen Zielangebote gerendert werden, die vom Inhaltsautor erstellt wurden. Der mobileAppOffers-Handler erweitert den Handler zur Aktualisierung abstrakter Seiten, sodass viele Eigenschaften ähnlich sind. Die Details des MobileAppOffers-Handlers haben die folgenden Eigenschaften.

Der MobileAppsOffers-Handler erweitert den MobileAppsPages-Handler und fügt die folgenden Eigenschaften hinzu:

* ***locationRoot - Zeichenfolge*** - geben Sie den Speicherort der Mobile App an.
* ***includePageTypes - String*** - unterstützt standardmäßig cq/personalization/components/teaserpage und cq/personalization/components/offerproxy
* ***selector - String*** - sollte auf Tandt gesetzt werden.
* ***path - String*** - der Pfad zur Marke der Kampagne

**mobileAppConfig** Der Inhaltssynchronisierungs-Handler für mobileAppConfig bietet eine Möglichkeit, JSON-Daten in die Datei „MobileAppsConfig.json“ einzufügen. Um eine Anbieterklasse zu registrieren, fügen Entwickler ihre MobileAppsInfoProvider-Klasse mit der Liste der Anbieter hinzu. Der Handler durchläuft die Liste der MobileAppsInfoProviders und ermöglicht es dem Provider, Daten in die resultierende JSON-Datei einzufügen. Folgende Eigenschaften werden von diesem Handler unterstützt:

* ***path &#x200B;**-**String*** - der Pfad zu einem App-Instanzknoten mit pge-type=app-instance oder einem RT, der /libs/mobileapps/core/components/instance erweitert
* ***providers - String*** `[]` - die Liste der vollständig qualifizierten MobileAppsInfoProvider
* ***targetRootDirectory - String*** - der Ordner, in den die MobileAppsConfig.json-Datei geschrieben werden soll.
* **fileName - Zeichenfolge** - Optionaler Name der Datei, in die die JSON geschrieben werden soll, standardmäßig MobileAppsConfig.json

Es ist möglich, mehrere mobileAppConfig-Handler jeweils mit einem eindeutigen Satz von Anbietern zu konfigurieren, die in verschiedene JSON-Dateien schreiben.

### Testen von Inhaltssynchronisierungs-Handlern {#testing-content-sync-handlers}

**Schritte zur Integritätsprüfung** Cache löschen

* Löschen des Cache
* Handler ausführen (Cache aktualisiert)
* Handler erneut ausführen (Cache sollte nicht aktualisiert werden)

**Schritte zum Debugging**

* Ausführen der Konfiguration
* Konfiguration exportieren oder auf dem Gerät überprüfen
* Wenn das Rendering fehlschlägt, überprüfen Sie *styles/assets/libs* oder suchen Sie nach ungültigen Pfaden zu *styles/assets/libs*

**Protokollierung** Aktivieren der ContentSync-Debug-Protokollierung über OSGi-Logger-Konfigurationen auf Package `com.day.cq.contentsync` Auf diese Weise können Sie verfolgen, welche Handler ausgeführt wurden, ob der Cache aktualisiert wurde und ob eine Aktualisierung des Caches gemeldet wurde.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Um mit der Entwicklung von AEM Mobile-Apps zu beginnen, klicken Sie [hier](/help/mobile/getting-started-aem-mobile.md).
