---
title: Konfigurieren von ContextHub
description: Erfahren Sie, wie man ContextHub konfiguriert.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 61208bd5-475b-40be-ba00-31bbbc952adf
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 98%

---

# Konfigurieren von ContextHub {#configuring-contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Ausführlichere Informationen zu ContextHub finden Sie in der [Entwicklerdokumentation](/help/sites-developing/contexthub.md). In der Touch-optimierten Benutzeroberfläche wird [Client Context](/help/sites-administering/client-context.md) durch ContextHub ersetzt.

Sie können die [ContextHub](/help/sites-developing/contexthub.md)-Symbolleiste konfigurieren, um unter Verwendung der Touch-optimierten Benutzeroberfläche zu steuern, ob sie im Vorschaumodus angezeigt wird, ContextHub-Stores zu erstellen und UI-Module hinzuzufügen.

## Deaktivieren von ContextHub {#disabling-contexthub}

In einer AEM-Installation ist ContextHub standardmäßig aktiviert. ContextHub kann deaktiviert werden, um zu verhindern, dass js/css geladen und initialisiert wird.

<!--
There are two options to disable ContextHub:

* Edit the ContextHub's configuration and check the option **Disable ContextHub**

    1. In the rail click or tap **Tools &gt; Sites &gt; ContextHub**
    1. Click or tap the appropriate **Configuration Container**
    1. Select the **ContextHub Configuration** and click or tap **Edit Selected Element**
    1. Click or tap **Disable ContextHub** and click or tap **Save**

or
-->

* Verwenden Sie dazu CRXDE Lite, um die Eigenschaft `disabled` unter `/libs/settings/cloudsettings/legacy/contexthub` auf **true** festzulegen.

>[!NOTE]
>
>[Aufgrund der Repository-Umstrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) wurde der Speicherort der ContextHub-Konfigurationen von `/etc/cloudsettings` wie folgt geändert:
>
>* `/libs/settings/cloudsettings`
>* `/conf/global/settings/cloudsettings`
>* `/conf/<tenant>/settings/cloudsettings`

## Ein- und Ausblenden der ContextHub-Benutzeroberfläche {#showing-and-hiding-the-contexthub-ui}

Konfigurieren Sie den Adobe Granite ContextHub-OSGi-Service, um die [ContextHub-Benutzeroberfläche](/help/sites-authoring/ch-previewing.md) auf Ihren Seiten ein- oder auszublenden. Die PID dieses Service lautet `com.adobe.granite.contexthub.impl.ContextHubImpl.`.

Der Service kann entweder mithilfe der [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oder mit einem [JCR-Knoten im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) konfiguriert werden:

* **Web-Konsole:** Um die Benutzeroberfläche anzuzeigen, wählen Sie die Eigenschaft „Benutzeroberfläche anzeigen“ aus. Um die Benutzeroberfläche auszublenden, heben Sie die Auswahl dieser Eigenschaft aus.
* **JCR-Knoten:** Legen Sie die boolesche Eigenschaft `com.adobe.granite.contexthub.show_ui` auf `true` fest, um die Benutzeroberfläche anzuzeigen. Legen Sie die Eigenschaft auf `false` fest, um die Benutzeroberfläche auszublenden.

Wenn die ContextHub-Benutzeroberfläche angezeigt wird, erscheint sie nur auf den Seiten von AEM-Authoring-Instanzen. Auf Seiten von Publishing-Instanzen wird die Benutzeroberfläche nicht angezeigt.

## Hinzufügen von ContextHub-UI-Modi und -Modulen {#adding-contexthub-ui-modes-and-modules}

Konfigurieren Sie die UI-Modi und -Module, die in der ContextHub-Symbolleiste im Vorschaumodus angezeigt werden:

* UI-Modi: Gruppen verwandter Module
* Module: Widgets, die Kontextdaten aus einem Store bereitstellen und Autorinnen und Autoren die Bearbeitung des Kontexts ermöglichen

UI-Modi werden als eine Reihe von Symbolen auf der linken Seite der Symbolleiste angezeigt. Wenn diese Option aktiviert ist, werden die Module eines UI-Modus rechts angezeigt.

![chlimage_1-319](assets/chlimage_1-319.png)

Bei Symbolen handelt es sich um Verweise aus der [Coral-Bibliothek mit Benutzeroberflächensymbolen](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons).

### Hinzufügen eines UI-Modus {#adding-a-ui-mode}

Fügen Sie einen UI-Modus hinzu, um verwandte ContextHub-Module zu gruppieren. Wenn Sie den UI-Modus erstellen, geben Sie den Titel und das Symbol an, die in der ContextHub-Symbolleiste angezeigt werden.

1. Klicken oder tippen Sie in der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den standardmäßigen Konfigurations-Container.
1. Klicken oder tippen Sie auf die ContextHub-Konfiguration.
1. Klicken oder tippen Sie auf die Schaltfläche „Erstellen“ und dann auf „ContextHub-UI-Modus“.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Geben Sie Werte für die folgenden Eigenschaften an:

   * UI-Modustitel: Der Titel, mit dem der UI-Modus identifiziert wird.
   * Modussymbol: Die Auswahl für das zu verwendende [Coral-UI-Symbol](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons), z. B. `coral-Icon--user`.
   * Aktiviert: Wählen Sie diese Option aus, um den UI-Modus in der ContextHub-Symbolleiste anzuzeigen.

1. Klicken oder tippen Sie auf „Speichern“.

### Hinzufügen eines UI-Moduls {#adding-a-ui-module}

Fügen Sie einem UI-Modus ein ContextHub-UI-Modul hinzu, damit es in der ContextHub-Symbolleiste zur Vorschau von Seiteninhalten angezeigt wird. Wenn Sie ein UI-Modul hinzufügen, erstellen Sie eine Instanz eines Modultyps, der bei ContextHub registriert ist. Um ein UI-Modul hinzufügen zu können, müssen Sie den Namen des zugehörigen Modultyps kennen.

AEM bietet einen grundlegenden UI-Modultyp sowie mehrere Beispiel-UI-Modultypen, auf denen Sie ein UI-Modul aufbauen können. Die folgende Tabelle enthält eine kurze Beschreibung der einzelnen Typen. Informationen zum Entwickeln eines benutzerdefinierten UI-Moduls finden Sie unter [Erstellen von ContextHub-UI-Modulen](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Die Eigenschaften des UI-Moduls enthalten eine Detailkonfiguration, in der Sie Werte für modulspezifische Eigenschaften angeben können. Die Detailkonfiguration stellen Sie im JSON-Format bereit. Die Spalte „Modultyp“ in der Tabelle enthält Links zu Informationen über den JSON-Code, der für jeden UI-Modultyp erforderlich ist.

| Modultyp | Beschreibung | Store |
|---|---|---|
| [contexthub.base](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) | Ein generischer UI-Modultyp | In den Eigenschaften des UI-Modusl konfiguriert |
| [contexthub.browserinfo](/help/sites-developing/ch-samplemodules.md#contexthub-browserinfo-ui-module-type) | Zeigt Informationen zum Browser an | surferinfo |
| [contexthub.datetime](/help/sites-developing/ch-samplemodules.md#contexthub-datetime-ui-module-type) | Zeigt Informationen zu Datum und Uhrzeit an | datetime |
| [contexthub.device](/help/sites-developing/ch-samplemodules.md#contexthub-device-ui-module-type) | Zeigt das Client-Gerät an | emulators |
| [contexthub.location](/help/sites-developing/ch-samplemodules.md#contexthub-location-ui-module-type) | Zeigt den Breiten- und Längengrad des Clients sowie den Standort auf einer Karte an. Sie können den Standort ändern. | geolocation |
| [contexthub.screen-orientation](/help/sites-developing/ch-samplemodules.md#contexthub-screen-orientation-ui-module-type) | Zeigt die Bildschirmausrichtung des Geräts (Querformat oder Hochformat) an | emulators |
| [contexthub.tagcloud](/help/sites-developing/ch-samplemodules.md#contexthub-tagcloud-ui-module-type) | Zeigt Statistiken zu Seiten-Tags an | tagcloud |
| [granite.profile](/help/sites-developing/ch-samplemodules.md#granite-profile-ui-module-type) | Zeigt Informationen zum Profil des aktuellen Benutzers an, einschließlich authorizableID, displayName und familyName. Sie können den Wert von displayName und familyName ändern. | Profil |

1. Klicken oder tippen Sie in der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den Konfigurations-Container, dem Sie ein UI-Modul hinzufügen möchten.
1. Klicken Sie oder geben Sie die ContextHub-Konfiguration ein, der Sie das UI-Modul hinzufügen möchten.
1. Klicken oder tippen Sie auf den UI-Modus, dem Sie das UI-Modul hinzufügen.
1. Klicken oder tippen Sie auf die Schaltfläche „Erstellen“ und dann auf „ContextHub-UI-Modul (generisch)“.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Geben Sie Werte für die folgenden Eigenschaften an:

   * Titel des UI-Moduls: Ein Titel, der das UI-Modul bezeichnet
   * Modultyp: Der Modultyp
   * Aktiviert: Wählen Sie diese Option, um das UI-Modul in der ContextHub-Symbolleiste anzuzeigen.

1. (Optional) Geben Sie ein JSON-Objekt ein, um das UI-Modul zu konfigurieren und so die Standardkonfiguration für den Store außer Kraft zu setzen.
1. Klicken oder tippen Sie auf „Speichern“.

## Erstellen eines ContextHub-Store {#creating-a-contexthub-store}

Erstellen Sie einen ContextHub-Store, um Benutzerdaten beizubehalten und nach Bedarf auf die Daten zuzugreifen. ContextHub-Stores basieren auf registrierten Store-Kandidaten. Wenn Sie den Store erstellen, benötigen Sie den Wert von „storeType“, mit dem der Store-Kandidat registriert wurde. (Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Store-Kandidaten](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).)

### Store-Detailkonfiguration {#detailed-store-configuration}

Beim Konfigurieren eines Stores können Sie über die Eigenschaft „Detailkonfiguration“ Werte für Store-spezifische Eigenschaften angeben. Der Wert basiert auf dem Parameter `config` der Store-Funktion `init`. Es hängt daher vom Store ab, ob dieser Wert angegeben werden muss und welches Format der Wert haben muss.

Der Wert der Eigenschaft „Detailkonfiguration“ ist ein `config`-Objekt im JSON-Format.

### Beispiele für Store-Kandidaten {#sample-store-candidates}

In AEM werden die folgenden Beispiele für Store-Kandidaten bereitgestellt, die Sie als Basis für einen Store verwenden können.

| Filialtyp | Beschreibung |
|---|---|
| [aem.segmentation](/help/sites-developing/ch-samplestores.md#aem-segmentation-sample-store-candidate) | Store für gelöste und ungelöste ContextHub-Segmente. Ruft automatisch Segmente aus dem ContextHub SegmentManager zurück |
| [aem.resolvedsegments](/help/sites-developing/ch-samplestores.md#aem-resolvedsegments-sample-store-candidate) | Speichert die aktuell aufgelösten Segmente. Hört automatisch auf den ContextHub SegmentManager-Dienst, um den Store automatisch zu aktualisieren |
| [contexthub.geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) | Speichert den Breiten- und Längengrad des Browser-Standorts. |
| [contexthub.datetime](/help/sites-developing/ch-samplestores.md#contexthub-datetime-sample-store-candidate) | Speichert das aktuelle Datum, die aktuelle Uhrzeit und die aktuelle Jahreszeit für den Browser-Standort |
| [granite.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate) | Definiert Eigenschaften und Funktionen für eine Reihe von Geräten und erkennt das aktuelle Client-Gerät. |
| [contexthub.generic-jsonp](/help/sites-developing/ch-samplestores.md#contexthub-generic-jsonp-sample-store-candidate) | Ruft Daten von einem JSONP-Dienst ab und speichert sie |
| [granite.profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) | Speichert die Profildaten für den aktuellen Benutzer. |
| [contexthub.surferinfo](/help/sites-developing/ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) | Speichert die Informationen zum Client, z. B. Geräteinformationen, Browser-Typ und Fensterausrichtung. |
| [contexthub.tagcloud](/help/sites-developing/ch-samplestores.md#contexthub-tagcloud-sample-data-store) | Speichert Seiten-Tags und die Tag-Anzahl |

1. Klicken oder tippen Sie in der Experience Manager-Leiste auf „Tools“ > „Sites“ > „ContextHub“.
1. Klicken oder tippen Sie auf den standardmäßigen Konfigurations-Container.
1. Klicken oder tippen Sie auf „ContextHub-Konfiguration“.
1. Klicken oder tippen Sie zum Hinzufügen eines Stores auf das Symbol „Erstellen“ und dann auf „ContextHub-Store-Konfiguration“.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Geben Sie Werte für die grundlegenden Konfigurationseigenschaften ein und klicken oder tippen Sie auf „Weiter“:

   * **Konfigurationstitel:** Der Titel, der den Store bezeichnet
   * **Store-Typ:** Der Wert der Eigenschaft „storeType“ des Store-Kandidaten, auf dem der Store basieren soll
   * **Erforderlich:** Wählen Sie diese Option aus.
   * **Aktiviert:** Wählen Sie diese Option aus, um den Store zu aktivieren

1. (Optional) Geben Sie ein JSON-Objekt in das Feld „Detailkonfiguration (JSON)“ ein, um die standardmäßige Store-Konfiguration zu überschreiben.
1. Klicken oder tippen Sie auf „Speichern“.

## Beispiel: Verwenden eines JSONP-Service  {#example-using-a-jsonp-service}

In diesem Beispiel wird veranschaulicht, wie Sie einen Store konfigurieren und die Daten in einem UI-Modul anzeigen. In diesem Beispiel wird der MD5-Service der Website „jsontest.com“ als Datenquelle für einen Store verwendet. Der Service gibt den MD5-Hashcode einer bestimmten Zeichenfolge im JSON-Format zurück.

Der Store „contexthub.generic-jsonp“ wird so konfiguriert, dass Daten für den Service-Aufruf `https://md5.jsontest.com/?text=%22text%20to%20md5%22` gespeichert werden. Der Service gibt die folgenden Daten zurück, die in einem UI-Modul angezeigt werden:

```xml
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### Erstellen des Stores „contexthub.generic-jsonp“ {#creating-a-contexthub-generic-jsonp-store}

Mit dem Store-Beispielkandidaten „contexthub.generic-jsonp“ können Sie Daten aus einem JSONP-Service oder einem Webservice abrufen, der JSON-Daten zurückgibt. Verwenden Sie für diesen Store-Kandidaten die Store-Konfiguration, um Details zu dem JSONP-Service anzugeben, der genutzt werden soll.

Die [init](/help/sites-developing/contexthub-api.md#init-name-config) Funktion der `ContextHub.Store.JSONPStore` Die JavaScript-Klasse definiert eine `config` -Objekt, das diesen Store-Kandidaten initialisiert. Das `config`-Objekt enthält ein `service`-Objekt mit Details zum JSONP-Service. Zum Konfigurieren des Stores geben Sie das `service`-Objekt im JSON-Format als Wert für die Eigenschaft „Detailkonfiguration“ an.

Verwenden Sie zum Speichern von Daten aus dem MD5-Service der Website „jsontest.com“ das Verfahren unter [Erstellen eines ContextHub-Store](/help/sites-developing/ch-configuring.md#creating-a-contexthub-store) mit den folgenden Eigenschaften:

* **Konfigurationstitel:** md5
* **Store-Typ:** contexthub.generic-jsonp
* **Erforderlich:** Wählen Sie diese Option aus.
* **Aktiviert:** Wählen Sie diese Option aus.
* **Detailkonfiguration (JSON):**

  ```xml
  {
   "service": {
   "jsonp": false,
   "timeout": 1000,
   "ttl": 1800000,
   "secure": false,
   "host": "md5.jsontest.com",
   "port": 80,
   "params":{
   "text":"text to md5"
       }
     }
   }
  ```

### Hinzufügen eines Benutzeroberflächenmoduls für die md5-Daten {#adding-a-ui-module-for-the-md-data}

Fügen Sie der ContextHub-Symbolleiste ein UI-Modul hinzu, um die Daten anzuzeigen, die im md5-Beispiel-Store gespeichert sind. In diesem Beispiel wird das Modul „contexthub.base“ verwendet, um das folgende UI-Modul zu erstellen:

![chlimage_1-323](assets/chlimage_1-323.png)

Nutzen Sie das Verfahren unter [Hinzufügen eines Benutzeroberflächenmoduls](#adding-a-ui-module), um das Benutzeroberflächenmodul einem vorhandenen Benutzeroberflächenmodus hinzuzufügen, z. B. dem Beispiel-Benutzeroberflächenmodus „Perona“. Verwenden Sie für das UI-Modul die folgenden Eigenschaftswerte:

* **Titel des UI-Moduls:** MD5
* **Modultyp:** contexthub.base
* **Detailkonfiguration (JSON):**

  ```xml
  {
   "icon": "coral-Icon--data",
   "title": "MD5 Converstion",
   "storeMapping": { "md5": "md5" },
   "template": "<p> {{md5.original}}</p>;
                <p>{{md5.md5}}</p>"
  }
  ```

## Debuggen von ContextHub {#debugging-contexthub}

Ein Debugging-Modus für ContextHub kann aktiviert werden, um die Fehlerbehebung zu ermöglichen. Der Debugging-Modus kann entweder über die ContextHub-Konfiguration oder über CRXDE aktiviert werden.

### Per Konfiguration {#via-the-configuration}

Bearbeiten Sie die Konfiguration von ContextHub und aktivieren Sie die Option **Debuggen**.

1. Klicken oder tippen Sie in der Leiste auf **„Tools“ > „Sites“ > „ContextHub“**
1. Klicken oder tippen Sie auf den standardmäßigen **Konfigurations-Container**.
1. Wählen Sie die **ContextHub-Konfiguration** aus und klicken oder tippen Sie auf **Ausgewähltes Element bearbeiten**.
1. Klicken oder tippen Sie auf **Debuggen** und dann auf **Speichern**.

### Per CRXDE {#via-crxde}

Verwenden Sie CRXDE Lite, um die Eigenschaft `debug` unter auf **true** festzulegen:

* `/conf/global/settings/cloudsettings` oder
* `/conf/<tenant>/settings/cloudsettings`

>[!NOTE]
>
>Bei ContextHub-Konfigurationen, die sich noch unter ihren veralteten Pfaden befinden, wird der Speicherort festgelegt, unter dem die `debug property` is `/libs/settings/cloudsettings/legacy/contexthub`.

### Unbeaufsichtigter Modus {#silent-mode}

Im unbeaufsichtigten Modus werden alle Debug-Informationen unterdrückt. Im Gegensatz zur normalen Debug-Option, die für jede ContextHub-Konfiguration einzeln festgelegt werden kann, ist der unbeaufsichtigte Modus eine globale Einstellung, die Vorrang vor allen Debug-Einstellungen auf der Ebene der ContextHub-Konfiguration hat.

Dies ist für Ihre Veröffentlichungsinstanz hilfreich, für die Sie keine Debug-Informationen benötigen. Da es sich um eine globale Einstellung handelt, wird sie per OSGi aktiviert.

1. Öffnen Sie die **Konfiguration der Adobe Experience Manager-Web-Konsole** unter `http://<host>:<port>/system/console/configMgr`.
1. Suchen Sie nach **Adobe Granite ContextHub**.
1. Klicken Sie auf die Konfiguration **Adobe Granite ContextHub**, um die Eigenschaften zu bearbeiten.
1. Aktivieren Sie die Option für den **unbeaufsichtigten Modus** und klicken Sie auf **Speichern**.

## Wiederherstellen von ContextHub-Konfigurationen nach einem Upgrade {#recovering-contexthub-configurations-after-upgrading}

Wenn ein [Upgrade für AEM](/help/sites-deploying/upgrade.md) durchgeführt wird, werden die ContextHub-Konfigurationen gesichert und an einem sicheren Speicherort gespeichert. Während des Upgrades werden die standardmäßigen ContextHub-Konfigurationen installiert. Sie ersetzen dabei die vorhandenen Konfigurationen. Die Sicherung ist erforderlich, um alle Änderungen oder Ergänzungen beizubehalten, die Sie vorgenommen haben.

ContextHub-Konfigurationen werden in einem Ordner mit dem Namen `contexthub` unter den folgenden Knoten gespeichert:

* `/conf/global/settings/cloudsettings`
* `/conf/<tenant>/settings/cloudsettings`

Nach einem Upgrade wird die Sicherung in einem Ordner mit dem Namen `contexthub` unter einem Knoten mit dem folgenden Namen gespeichert:

`/conf/global/settings/cloudsettings/default-pre-upgrade_yyyymmdd_xxxxxxx` oder
`/conf/<tenant>/settings/cloudsettings/default-pre-upgrade_yyyymmdd_xxxxxxx`

Der Teil `yyyymmdd` des Knotennamens ist das Datum, an dem das Upgrade durchgeführt wurde.

Verwenden Sie zum Wiederherstellen Ihrer ContextHub-Konfigurationen CRXDE Lite, um die Knoten mit Ihren Stores, Benutzeroberflächenmodi und Benutzeroberflächenmodulen von `default-pre-upgrade_yyyymmdd_xxxxxx` unter den folgenden Knoten zu kopieren:

* `/conf/global/settings/cloudsettings` oder
* `/conf/<tenant>/settings/cloudsettings`
