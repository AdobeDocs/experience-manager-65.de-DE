---
title: Vordefinierte App-Handler
seo-title: Vordefinierte App-Handler
description: Folgen Sie dieser Seite, um mehr über die vordefinierten Handler für Adobe PhoneGap Enterprise mit AEM zu erfahren.
seo-description: Folgen Sie dieser Seite, um mehr über die vordefinierten Handler für Adobe PhoneGap Enterprise mit AEM zu erfahren.
uuid: 436038cb-fb76-4bb5-ae79-5d4043b81dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fec86f03-f81e-460a-9f84-d6304c95128c
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 2%

---


# Vordefinierte App-Handler{#out-of-the-box-app-handlers}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Informationen zum Entwickeln von Content Sync-Handlern finden Sie in den folgenden Richtlinien:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder durch Erweitern einer Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* erweitern
* Handler darf nur dann true melden, wenn der ContentSync-Cache aktualisiert wurde. Falsch Berichte true ermöglicht AEM ein Update zu erstellen.
* Der Handler sollte den Cache nur aktualisieren, wenn sich der Inhalt tatsächlich geändert hat. Schreiben Sie nicht in den Cache, wenn kein Weiß erforderlich ist, und vermeiden Sie eine unnötige Aktualisierung.

## Out-of-the-Box-Handler {#out-of-the-box-handlers}

Die folgenden App-Handler sind standardmäßig verfügbar:

**** mobileapagesRendert App-Seiten.

* ***type - String***  - mobileapages
* ***path - String***  - Pfad zu einer Seite
* ***extension - String*** - Extension, die in der Anforderung verwendet werden sollte. Für Seiten ist dies fast immer *html*, aber andere sind noch möglich.

* ***selector - Zeichenfolge***  - Optionale Selektoren, durch Punkt getrennt. Häufige Beispiele sind *touch* zum Rendern von mobilen Versionen einer Seite.

* ***bottom - Boolean*** - Optionale boolesche Eigenschaft, die bestimmt, ob untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* ***includeImages - Boolean*** - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

   * Standardmäßig werden nur Bildkomponenten mit einem Ressourcentyp wie Stiftung/Komponenten/Bild für die Aufnahme in Betracht gezogen.

* ***includeVideos - Boolean*** - Die optionale boolesche Eigenschaft bestimmt, ob Videos einbezogen werden sollen. Der Standardwert lautet *true*.

* ***includeModifiedPagesOnly - Boolean*** - Wenn false oder nicht angegeben, werden alle Seiten gerendert und Aktualisierungen beim Rendering überprüft. Wenn &quot;true&quot;, weicht die Basis von Änderungen an den Seiten lastModified ab.
* ***+ rewrite (Knoten)***
   ***- relativeParentPath - String***  - der Pfad zum Schreiben aller anderen Pfade relativ zu.

>[!NOTE]
>
>Der Ressourcentyp der Bild- und Videokomponenten, die von diesem Handler betroffen sind, wird durch Konfigurieren der Eigenschaften von *com.adobe.cq.mobile.platform.impl.contentsync.handler* festgelegt.*MobilePagesUpdateHandler OSGi-Dienst*.

**** mobilepageassetsErfasst App-Seiten-Assets.

**** mobilecontentlistingListet den Inhalt der ContentSync-ZIP auf. Dies wird von der clientseitigen js auf dem Gerät verwendet, um die anfängliche Datei zu kopieren, die für AEM Apps erforderlich ist.

Dieser Handler sollte jeder AEM ContentSync-Konfiguration hinzugefügt werden.

* ***type - String - mobilecontentlisting***
* ***path*** - String - leer lassen, muss vorhanden sein, um als gültiger Handler angesehen zu werden, aber der Pfad wird als aktueller ContentSync-Cache abgeleitet. Dieser Wert wird ignoriert.
* ***targetRootDirectory* -**String - das Präfix, das Pfaden als Zielgruppe-Stammordner für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**Order for ContentSync, um diesen Handler auszuführen. Diese Zahl sollte höher als alle anderen Handler wie z. B. 100 eingestellt werden. Es sollte nach traditionellen Content-Handlern ausgeführt werden.

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

**** mobilecontentpackageslistingListet das AEM Inhaltspaket in einer bestimmten App sowie die serverURL auf, an die Updateanforderungen gesendet werden sollen. Dies wird auf dem Client-seitigen JS auf dem Gerät zum Anfordern von Inhaltsaktualisierungen verwendet

Der Handler sollte auf AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String - mobilecontentpackageslisting***
* ***path **-**String*** - Pfad zu einer App-Shell (Knoten mit page-type=app-instance).
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielgruppe-Stammordner für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***order - Long* -**Order for ContentSync, um diesen Handler auszuführen. Diese Zahl sollte höher als alle anderen Handler wie z. B. 100 eingestellt werden. Es sollte nach traditionellen Content-Handlern ausgeführt werden.

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

**** widgetconfigEnthält eine aktualisierte Datei &quot;config.xml&quot;, die alle über das Command Center vorgenommenen Änderungen mit der angegebenen Datei &quot;config.xml&quot;zusammenführt. Wenn dieser Handler keine App-Details enthält, die über die Administrationsoberfläche geändert werden, werden diese nicht in den Cache aufgenommen.

Dieser Handler sollte auf einer AEM App Shell ContentSync-Konfiguration verwendet werden (Knoten mit pge-type=[app-instance]).

* ***type - String* - **widgetconfig
* ***path **-**String*** - Pfad zu einem beliebigen untergeordneten Knoten der App-Shell (Knoten mit &quot;pge-type=[app-instance]&quot;).
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielgruppe-Stammordner für die Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll.
* ***targetIconDirectory - String***  - der Ordner, in dem die Symbole für die App abgelegt werden

**** mobileADBMobileConfigJSONInschließen Sie die Datei ADBMobileConfig.JSON ein, wenn der AMS-Cloudservice konfiguriert wurde.

Dies wird zur Kompilierungszeit verwendet, um das AMS-Plugin für die Unterstützung der Analyse zu konfigurieren.

Der Handler sollte auf AEM App Shell ContentSync Config (Knoten mit page-type=app-instance) verwendet werden

* ***type - String*** - mobileADBMobileConfigJSON
* ***path - String*** - Pfad zu einer App-Shell (Knoten mit pageType=app-instance oder einer RT, die /libs/mobileapps/core/components/instance erweitert)
* ***targetRootDirectory - String***  - das Präfix, das Pfaden als Zielgruppe-Stammordner für Inhaltsaktualisierung für diesen Handler hinzugefügt werden soll

**Benachrichtigungskonfigurationen** extrahiert erforderliche Benachrichtigungskonfigurationen auf dem Gerät. Die Eigenschaften werden aus der jeweiligen mit der App verknüpften Konfiguration des Push-Dienst-Cloud-Dienstes extrahiert.

Nicht-AEM-Eigenschaften im Knoten &quot;jcr:content&quot;des Cloud-Dienstes werden extrahiert und der JSON-Datei **pge-notifications-config.json** hinzugefügt, um sie in den www-Stammordner des App-Inhalts aufzunehmen.

AEM Eigenschaften sind die Eigenschaften, die mit &quot;cq&quot;, &quot;sling&quot;oder &quot;jcr&quot;benannt werden. Andere Eigenschaften können mit der Eigenschaft &quot;excludeProperties&quot;auf dem Knoten content-sync-config ausgeschlossen werden.

* ***type - String***  - notificationsconfig
* ***excludeProperties - String[]*** - Eigenschaften, die ausgeschlossen werden sollen

**Inhalt** einer bestehenden ContentSync-Konfiguration erfassen

* ***type - String***  - contentsyncconfigcontent
* ***path - String***  - Pfad zu einem der folgenden:

   * other ContentSync config
   * zu einem Inhaltspaket (verwendet seine phonegap-exportTemplate-Eigenschaft, um die ContentSync-Konfiguration zu finden)
   * zu einer Mobile-Ressource (App-Inhalte befinden sich unter dieser Ressource und wenn diese Inhaltspakete eine page-includeInBuild-Eigenschaft haben, die true lautet, wird die phonegap-exportTemplate verwendet, um die ContentSync-Konfiguration zu finden)

* ***autoCreateFirstUpdateBeforeImport - Boolescher***  Wert - bei &quot;true&quot;erstellen Sie vor dem Import eine erste  **** Aktualisierung in der Zielgruppe, wenn diese nicht bereits vorhanden ist

* ***autoFillBeforeImport - Boolescher***  Wert - wenn true, aktualisieren/füllen Sie die Zielgruppe-Konfiguration vor dem Import
* ***configSuffix - String***  - eine Zeichenfolge, die an den in der Eigenschaft &quot;phonegap-exportTemplate&quot;von app-content angegebenen Pfad angehängt wird. Auf diese Weise lassen sich verschiedene Exportvorlagen unterscheiden. Beispielsweise kann diese Eigenschaft auf **&quot;-dev&quot;** eingestellt werden, um anzugeben, dass *&quot;/.../.../appconfig-dev&quot;* verwendet werden sollte (im Gegensatz zu *&quot;/.../..././appconfig&quot;*).

**app-** assetsUmfasst alle mit einer App-Instanz verknüpften Assets. Dieser Handler enthält alle unter dem angegebenen Pfad gefundenen Assets zusammen mit allen Assets, auf die die appAssetPath-Eigenschaft einer App-Instanz verweist.

* ***type - String*** -app-assets

* ***path **-**String*** - Pfad zu einem Speicherort unter einer App-Instanz, in der App-Assets gespeichert werden

**** mobileappoffers Ein neuer Content-Synchronisierungs-Handler wurde für den Fall &quot;Personalisierung&quot;eingeführt, mit dem zielgerichtete Inhalte wiedergegeben werden. Der Handler &quot;mobileappoffers&quot;weiß, wie die zugehörigen Zielgruppen-Angebot wiedergegeben werden, die vom Inhaltsautor erstellt wurden. Der Handler mobileappoffers erweitert den Updatehandler für abstrakte Seiten, sodass viele Eigenschaften ähnlich sind. Die Details des Handlers mobileappoffers haben die folgenden Eigenschaften.

Der Handler mobileappsoffers erweitert den Handler mobileappspages und fügt die folgenden Eigenschaften hinzu:

* ***locationRoot - Zeichenfolge***  - geben Sie den Speicherort der Mobilanwendung an
* ***includePageTypes - String*** - standardmäßig unterstützt cq/personalization/components/teaserpage und cq/personalization/components/offerproxy
* ***selector - String*** - sollte auf tandt eingestellt werden
* ***path - String*** - der Pfad zur Marke der Kampagne

**** mobileappconfigDer Content-Synchronisierungs-Handler mobileappconfig bietet eine Möglichkeit, JSON-Daten in die Datei MobileAppsConfig.json zu injizieren. Um eine Anbieterklasse zu registrieren, fügen Entwickler ihre MobileAppsInfoProvider-Klasse mit der Liste der Anbieter hinzu. Der Handler durchläuft die Liste von MobileAppsInfoProviders und ermöglicht es dem Anbieter, Daten in die resultierende JSON-Datei einzufügen. Die Liste der Eigenschaften, die dieser Handler unterstützt, lautet:

* ***path **-**String*** : Der Pfad zu einem Knoten einer App-Instanz mit &quot;pge-type=app-instance&quot;oder einer RT, die /libs/mobileapps/core/components/instance erweitert
* ***providers - String*** `[]`  - die Liste voll qualifizierter MobileAppsInfoProviders
* ***targetRootDirectory - String***  - der Ordner, in den die Datei MobileAppsConfig.json geschrieben werden soll.
* **fileName - String**  - optionaler Name der Datei, in die JSON geschrieben werden soll, standardmäßig MobileAppsConfig.json

Es ist möglich, mehrere mobileappconfig-Handler mit jeweils einem eindeutigen Satz von Providern zu konfigurieren, die in verschiedene JSON-Dateien schreiben.

### Testen der Content Sync-Handler {#testing-content-sync-handlers}

**Schritte zum Überprüfen des** IntegrityClear-Cache

* Löschen des Cache
* Ausführen des Handlers (Cache aktualisiert)
* Führen Sie den Handler erneut aus (Cache sollte nicht aktualisiert werden)

**Schritte zum Debugging**

* Führen Sie Ihre Konfiguration aus
* Konfiguration oder Überprüfung auf dem Gerät exportieren
* Wenn die Wiedergabe fehlschlägt, suchen Sie nach fehlenden *Stile/assets/libs* oder prüfen Sie, ob fehlerhafte Pfade zu *Stile/assets/libs* vorhanden sind

**** ProtokollierungContentSync-Debug-Protokollierung über OSGI-Protokollkonfigurationen im Paket aktivieren  `com.day.cq.contentsync` Dies ermöglicht Ihnen, zu verfolgen, welche Handler ausgeführt haben und ob sie den Cache aktualisiert und die Cache-Aktualisierung gemeldet haben.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Um mit der AEM Mobile-App-Entwicklung zu beginnen, klicken Sie [hier](/help/mobile/getting-started-aem-mobile.md).

