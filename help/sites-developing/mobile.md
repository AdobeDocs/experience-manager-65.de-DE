---
title: Erstellen von Websites für Mobilgeräte
seo-title: Erstellen von Websites für Mobilgeräte
description: Das Erstellen einer mobilen Website ähnelt dem Erstellen einer Standardwebsite, da auch Vorlagen und Komponenten erstellt werden müssen
seo-description: Das Erstellen einer mobilen Website ähnelt dem Erstellen einer Standardwebsite, da auch Vorlagen und Komponenten erstellt werden müssen
uuid: 6b19042c-03f1-4e33-970e-475f9fb8c5fb
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 0aabfb0a-ef9c-4b06-b698-61cad101c3c1
docset: aem65
legacypath: /content/docs/en/aem/6-0/develop/mobile/mobile
exl-id: 21b2037a-685a-441d-aecd-865884253e03
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3864'
ht-degree: 69%

---

# Erstellen von Websites für Mobilgeräte{#creating-sites-for-mobile-devices}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md).

Das Erstellen einer mobilen Website ähnelt dem Erstellen einer Standardwebsite, da auch Vorlagen und Komponenten erstellt werden müssen Weitere Informationen zum Erstellen von Vorlagen und Komponenten finden Sie auf den folgenden Seiten: [Vorlagen](/help/sites-developing/templates.md), [Komponenten](/help/sites-developing/components.md) und [Erste Schritte Entwickeln von AEM Sites](/help/sites-developing/getting-started.md). Der Hauptunterschied besteht darin, die AEM integrierten mobilen Funktionen innerhalb der Site zu aktivieren. Dies wird erreicht, indem eine Vorlage erstellt wird, die auf der mobilen Seitenkomponente basiert.

Sie sollten auch in Betracht ziehen, [responsives Design](/help/sites-developing/responsive.md) zu verwenden und eine einzelne Website zu erstellen, die mehrere Bildschirmgrößen unterstützt.

Um zu beginnen, können Sie sich die Website **We.Retail Mobile Demos** ansehen, die in AEM verfügbar ist.

Um eine mobile Website zu erstellen, gehen Sie folgendermaßen vor:

1. Erstellen Sie die Seitenkomponente:

   * Legen Sie die Eigenschaft `sling:resourceSuperType` auf `wcm/mobile/components/page` fest.
Auf diese Weise verlässt sich die Komponente auf die mobile Seitenkomponente.

   * Erstellen Sie die Datei `body.jsp` mit der projektspezifischen Logik.

1. Erstellen Sie die Seitenvorlage:

   * Legen Sie die Eigenschaft `sling:resourceType` auf die neu erstellte Seitenkomponente fest.
   * Legen Sie die Eigenschaft `allowedPaths` fest.

1. Erstellen Sie die Designseite für die Website .
1. Erstellen Sie die Site-Stammseite unter dem Knoten `/content` :

   * Legen Sie die Eigenschaft `cq:allowedTemplates` fest.
   * Legen Sie die Eigenschaft `cq:designPath` fest.

1. Legen Sie in den Seiteneigenschaften der Website-Root-Seite die Gerätegruppen auf der Registerkarte **Mobile** fest.
1. Erstellen Sie die Website-Seiten mithilfe der neuen Vorlage.

Die mobile Seitenkomponente ( `/libs/wcm/mobile/components/page`):

* Fügt die Registerkarte **Mobile** zum Dialogfeld „Seiteneigenschaften“ hinzu.
* Über das `head.jsp` ruft es die aktuelle Mobilgerätegruppe aus der Anforderung ab und verwendet, wenn eine Gerätegruppe gefunden wird, die `drawHead()` -Methode der Gruppe, um die zugehörige Emulator-Init-Komponente der Gerätegruppe (nur im Autorenmodus) und das Rendering-CSS der Gerätegruppe einzubeziehen.

>[!NOTE]
>
>Die Root-Seite der mobilen Website muss sich auf der Ebene 1 der Knotenhierarchie befinden. Es wird empfohlen, dass sie sich unterhalb des Knotens/Inhalt befindet.

## Erstellen einer mobilen Website mit dem Multi-Site-Manager {#creating-a-mobile-site-with-the-multi-site-manager}

Verwenden Sie den Multi-Site-Manager (MSM), um eine mobile Live Copy von einer Standardseite zu erstellen. Die Standardseite wird automatisch in eine mobile Website umgewandelt: Die mobile Site weist alle Funktionen der mobilen Websites auf (z. B. die Bearbeitung in einem Emulator) und kann synchron mit der Standard-Site verwaltet werden. Weitere Informationen finden Sie im Abschnitt [Erstellen einer Live Copy für verschiedene Kanäle](/help/sites-administering/msm.md) auf der Seite Multi Site Manager .

## Serverseitige Mobile-API {#server-side-mobile-api}

Die Java-Pakete, welche die mobilen Klassen enthalten, sind:

* [com.day.cq.wcm.mobile.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html)  - definiert MobileConstants.
* [com.day.cq.wcm.mobile.api.device](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/package-summary.html)  - definiert Device, DeviceGroup und DeviceGroupList.
* [com.day.cq.wcm.mobile.api.device.function](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html)  - definiert DeviceCapability.
* [com.day.cq.wcm.mobile.api.wurfl](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/api/package-summary.html)  - definiert WurflQueryEngine.
* [com.day.cq.wcm.mobile.core](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/core/package-summary.html)  - definiert MobileUtil, das verschiedene Dienstprogrammmethoden rund um WCM Mobile bereitstellt.

### Mobile Komponenten {#mobile-components}

Die **We.Retail Mobile Demo Site** verwendet die folgenden mobilen Komponenten, die sich unter `/libs/foundation/components` befinden:

<table>
 <tbody>
  <tr>
   <td>Name</td>
   <td>Gruppe</td>
   <td>Eigenschaften</td>
  </tr>
  <tr>
   <td>mobilefooter</td>
   <td>hidden</td>
   <td>- Fußzeile</td>
  </tr>
  <tr>
   <td>mobileimage</td>
   <td>Mobilgerät</td>
   <td>- basierend auf der BildFoundation-Komponente<br /> - rendert ein Bild, wenn das Gerät fähig ist<br /> </td>
  </tr>
  <tr>
   <td>mobilelist</td>
   <td>Mobilgerät</td>
   <td>- basierend auf der list foundation component<br /> - listitem_teaser.jsp rendert ein Bild, wenn das Gerät fähig ist<br /> </td>
  </tr>
  <tr>
   <td>mobilelogo</td>
   <td>ausgeblendet</td>
   <td>- basierend auf der logo foundation component<br /> - rendert ein Bild, wenn das Gerät fähig ist<br /> </td>
  </tr>
  <tr>
   <td>mobilereferenz</td>
   <td>Mobilgerät</td>
   <td><p>- ähnlich der Referenz-Foundation-Komponente</p> <p>- ordnet eine textimage-Komponente einer mobiletextimage-Komponente und eine image-Komponente einer mobilen Bildkomponente zu</p> </td>
  </tr>
  <tr>
   <td>mobiletextimage</td>
   <td>Mobilgerät</td>
   <td>- basierend auf der textimage foundation component<br /> - rendert ein Bild, wenn das Gerät fähig ist</td>
  </tr>
  <tr>
   <td>mobiletopnav</td>
   <td>ausgeblendet</td>
   <td><p>- basierend auf der topnav-Foundation-Komponente</p> <p>- Nur Text wird gerendert</p> </td>
  </tr>
 </tbody>
</table>

#### Erstellen einer mobilen Komponente {#creating-a-mobile-component}

Das AEM-Mobile-Framework ermöglicht die Entwicklung von Komponenten, die für das Gerät, das die Anfrage erteilt, empfindlich sind. Die folgenden Codebeispiele zeigen, wie Sie die AEM-Mobile-API in einer Komponente jsp verwenden und insbesondere wie Sie:

* Rufen Sie das Gerät aus der Anfrage ab:
   `Device device = slingRequest.adaptTo(Device.class);`

* Gerätegruppe abrufen:
   `DeviceGroup deviceGroup = device.getDeviceGroup();`

* Abrufen der Gerätegruppenfunktionen:
   `Collection<DeviceCapability> capabilities = deviceGroup.getCapabilities();`

* Rufen Sie die Geräteattribute ab (rohe Funktionsschlüssel/Werte aus der WURFL-Datenbank):
   `Map<String,String> deviceAttributes = device.getAttributes();`

* Abrufen des Gerätebenutzers/Agenten:
   `String userAgent = device.getUserAgent();`

* Rufen Sie die Gerätegruppenliste (Gerätegruppen, die der Site vom Autor zugewiesen wurden) von der aktuellen Seite ab:
   `DeviceGroupList deviceGroupList = currentPage.adaptTo(DeviceGroupList.class);`

* Überprüfen Sie, ob die Gerätegruppe Bilder unterstützt.
   `if (deviceGroup.hasCapability(DeviceCapability.CAPABILITY_IMAGES)) {`
...
ODER

...   `if MobileUtil.hasCapability(request, DeviceCapability.CAPABILITY_IMAGES) {`
...

>[!NOTE]
>
>In einer JSP ist `slingRequest` über das Tag `<sling:defineObjects>` und `currentPage` über das Tag `<cq:defineObjects>` verfügbar.

### Emulatoren {#emulators}

Emulator-basiertes Authoring bietet Autoren die Möglichkeit, Inhaltsseiten für mobile Clients zu erstellen. Das Authoring mobiler Inhalte folgt dem gleichen Prinzip der direkten WYSIWYG-Bearbeitung. Damit Autoren die Seitenerscheinung auf einem mobilen Gerät erkennen können, wird eine mobile Inhaltsseite mithilfe eines Geräteemulators bearbeitet.

Mobilgeräte-Emulatoren basieren auf dem generischen Emulator-Framework. Weitere Informationen finden Sie auf der Seite [Emulatoren](/help/sites-developing/emulators.md).

Der Geräteemulator zeigt das tragbare Gerät auf der Seite, während die übliche Bearbeitung (parsys, Komponenten) auf dem Gerätebildschirm erfolgt. Der Geräteemulator hängt von den Gerätegruppen ab, die für die Seite konfiguriert wurden. Mehrere Emulatoren können einer Gerätegruppe zugewiesen werden. Alle Emulatoren sind dann auf der Inhaltsseite verfügbar. Standardmäßig wird der erste Emulator angezeigt, der der ersten Gerätegruppe zugewiesen ist, die der Seite zugewiesen ist. Emulatoren können entweder über das Emulator-Karussell am oberen Rand der Seite oder über die Schaltfläche „Bearbeiten“ des Sidekicks geschaltet werden.

**Erstellen eines Emulators**

Informationen zum Erstellen eines Emulators finden Sie im Abschnitt [Erstellen eines benutzerdefinierten mobilen Emulators](/help/sites-developing/emulators.md) auf der allgemeinen Seite zu Emulatoren.

**Hauptmerkmale von mobilen Emulatoren**

* Eine Gerätegruppe besteht aus einem oder mehreren Emulatoren: die Gerätegruppenkonfigurationsseite, z. B. /etc/mobile/groups/touch, enthält die Eigenschaft `emulators` unter dem Knoten `jcr:content` .
Hinweis: Obwohl es möglich ist, dass derselbe Emulator zu mehreren Gerätegruppen gehört, hat das wenig Sinn.

* Über das Konfigurationsdialogfeld der Gerätegruppe wird die Eigenschaft `emulators` mit dem Pfad der gewünschten Emulatoren festgelegt. Beispiel: `/libs/wcm/mobile/components/emulators/iPhone4`.

* Die Emulator-Komponenten (z. B. `/libs/wcm/mobile/components/emulators/iPhone4`) Erweitern Sie die mobile Basisemulatorkomponente ( `/libs/wcm/mobile/components/emulators/base`).

* Jede Komponente, die den mobilen Basisemulator erweitert, kann beim Konfigurieren einer Gerätegruppe ausgewählt werden. Benutzerdefinierte Emulatoren können daher problemlos erstellt oder erweitert werden.
* Zur Zeit der Anforderung im Bearbeitungsmodus wird die Emulatorimplementierung zum Rendern der Seite verwendet.
* Wenn die Vorlage der Seite auf der mobilen Seitenkomponente basiert, werden die Emulatorfunktionalitäten automatisch in die Seite integriert (über die `head.jsp` der mobilen Seitenkomponente).

### Gerätegruppen {#device-groups}

Mobilgerätegruppen ermöglichen die Segmentierung von Mobilgeräten basierend auf den Gerätefunktionen. Eine Gerätegruppe stellt die Informationen bereit, die für das emulatorbasierte Authoring auf der Autoreninstanz und für das korrekte Rendern von Inhalten in der Veröffentlichungsinstanz erforderlich sind: Sobald Autoren der mobilen Seite Inhalt hinzugefügt und veröffentlicht haben, kann die Seite in der Veröffentlichungsinstanz angefordert werden. Dort wird die Inhaltsseite anstelle der Bearbeitungsansicht des Emulators mit einer der konfigurierten Gerätegruppen gerendert. Die Auswahl der Gerätegruppe erfolgt basierend auf der [Erkennung mobiler Geräte](#devicedetection). Die passende Gerätegruppe liefert dann die notwendigen Styling-Informationen.

Gerätegruppen werden als Inhaltsseiten unter `/etc/mobile/devices` definiert und verwenden die Vorlage **Mobilgerätegruppe** . Die Gerätegruppenvorlage dient als Konfigurationsvorlage für Gerätegruppendefinitionen in Form von Inhaltsseiten. Die wichtigsten Eigenschaften sind:

* Standort: `/libs/wcm/mobile/templates/devicegroup`
* Zulässiger Pfad: `/etc/mobile/groups/*`
* Seitenkomponente: `wcm/mobile/components/devicegroup`

#### Zuweisung von Gerätegruppen auf Ihrer Seite {#assigning-device-groups-to-your-site}

Wenn Sie eine mobile Seite erstellen, müssen Sie Ihrer Seite Gerätegruppen zuweisen. AEM stellt je nach den HTML- und JavaScript-Rendering-Funktionen des Geräts drei Gerätegruppen zur Verfügung:

* **Featurephones**, für Feature-Geräte wie das Sony Ericsson W800 mit Unterstützung für grundlegende HTML aber keine Unterstützung für Bilder und JavaScript.
* **** Smartphones, für Geräte wie Blackberry mit Unterstützung für einfaches HTML und Bilder, aber ohne Unterstützung für JavaScript.

* **Touchphones**, für Geräte wie das iPad mit voller Unterstützung für HTML, Bilder, JavaScript und Geräte-Rotation.

Da Emulatoren einer Gerätegruppe zugeordnet werden können (siehe Abschnitt [Erstellen einer Gerätegruppe](#creating-a-device-group)), können Autoren durch Zuweisen einer Gerätegruppe zu einer Site zwischen den Emulatoren auswählen, die der Gerätegruppe zugeordnet sind, um die Seite zu bearbeiten.

So weisen Sie Ihrer Site eine Gerätegruppe zu:

1. Rufen Sie im Browser die Konsole **Siteadmin** auf.
1. Öffnen Sie die Stammseite Ihrer mobilen Website unter **Websites**.
1. Öffnen Sie die Seiteneigenschaften.
1. Wählen Sie die Registerkarte **Mobile**:

   * Definieren Sie die Gerätegruppen.
   * Klicken Sie auf **OK**.

>[!NOTE]
>
>Wenn die Gerätegruppen für eine Website definiert wurden, werden sie von allen Seiten der Website übernommen.

#### Gerätegruppenfilter:  {#device-group-filters}

Gerätegruppenfilter definieren funktionsgestützte Kriterien, um zu bestimmen, ob ein Gerät zu der Gruppe gehört. Wenn Sie eine Gerätegruppe erstellt haben, können Sie die Filter auswählen, um sie zur Gerätebewertung zu verwenden.

Zur Laufzeit, wenn AEM eine HTTP-Anforderung von einem Gerät empfängt, vergleicht jeder Filter, der einer Gruppe zugeordnet ist, die Gerätefunktionen mit bestimmten Kriterien. Das Gerät wird als zu der Gruppe gehörend betrachtet, wenn es über alle Funktionen verfügt, die von den Filtern benötigt werden. Die Funktionen werden aus der WURFL™-Datenbank abgerufen.

Gerätegruppen können null oder mehr Filter zur Erkennung von Funktionen verwenden. Außerdem kann ein Filter mit mehreren Gerätegruppen verwendet werden. AEM stellt einen Standardfilter bereit, der bestimmt, ob das Gerät über die Funktionen verfügt, die für eine Gruppe ausgewählt sind:

* CSS
* JPG- und PNG-Dateien
* JavaScript
* Gerätedrehung

Wenn die Gerätegruppe keinen Filter verwendet, sind die ausgewählten Funktionen, die für die Gruppe konfiguriert sind, die einzigen Funktionen, die ein Gerät benötigt.

Weitere Informationen hierzu finden Sie unter [Erstellen von Gerätegruppenfiltern](/help/sites-developing/groupfilters.md).

#### Erstellen einer Gerätegruppe {#creating-a-device-group}

Erstellen Sie eine Gerätegruppe, wenn die von AEM installierten Gruppen Ihren Anforderungen nicht entsprechen.

1. Rufen Sie im Browser die Konsole **Tools** auf.
1. Erstellen Sie eine neue Seite unter **Tools** > **Mobile** > **Gerätegruppen**. Im Dialogfeld **Seite erstellen**:

   * Geben Sie unter **Title** `Special Phones` ein.

   * Geben Sie unter **Name** `special` ein.

   * Wählen Sie die **Vorlage für Mobilgerätegruppen** aus.
   * Klicken Sie auf **Erstellen**.

1. Fügen Sie in CRXDE eine **static.css**-Datei hinzu, die die Stile für die Gerätegruppe unter dem Knoten `/etc/mobile/groups/special` enthält.

1. Öffnen Sie die Seite **Spezielle Telefone** .
1. Klicken Sie zum Konfigurieren der Gerätegruppe auf die Schaltfläche **Bearbeiten** neben **Einstellungen**.
Auf der Registerkarte **Allgemein**:

   * **Titel**: den Namen der Mobilgerätegruppe.
   * **Beschreibung** Beschreibung der Gruppe.
   * **Benutzeragent**: user-agent-String, mit dem die Geräte abgeglichen werden. Dieser ist optional, kann eine regex sein. Beispiel: `BlackBerryZ10`
   * **Funktionen**: Definiert, ob die Gruppe Bilder, CSS, JavaScript oder Gerätedrehungen verarbeiten kann.
   * **Minimale Bildschirmbreite** und **-höhe**
   * **Emulator deaktivieren**: Zum Aktivieren/Deaktivieren des Emulators während der Inhaltsbearbeitung.

   Auf der Registerkarte **Emulatoren**:

   * **Emulatoren**: Wählen Sie die Emulatoren aus, die dieser Gerätegruppe zugewiesen sind.

   Auf der Registerkarte **Filter**:

   * Um einen Filter hinzuzufügen, klicken Sie auf „Objekt hinzufügen“ und wählen Sie einen Filter aus der Dropdown-Liste aus.
   * Filter werden in der Reihenfolge ausgewertet, in der sie erscheinen. Wenn ein Gerät die Kriterien eines Filters nicht erfüllt, werden nachfolgende Filter in der Liste nicht ausgewertet.



1. Klicken Sie auf OK.

Das Konfigurationsdialogfeld für die Mobilgerätegruppe sieht folgendermaßen aus:

![screen_shot_2012-02-01at22043pm](assets/screen_shot_2012-02-01at22043pm.png)

#### Benutzerdefiniertes CSS pro Gerätegruppe {#custom-css-per-device-group}

Wie bereits zuvor beschrieben, ist es möglich, ein benutzerdefiniertes CSS mit einer Gerätegruppenseite zu verknüpfen, ähnlich wie das CSS einer Designseite. Dieses CSS wird verwendet, um das gerätegruppespezifische Rendern des Seiteninhalts beim in der Autoren- und Veröffentlichungsinstanz zu beeinflussen. Dieses CSS ist dann automatisch enthalten:

* Auf der Seite der Autoreninstanz für jeden Emulator, der von dieser Gerätegruppe verwendet wird.
* Auf der Seite der Veröffentlichungsinstanz, wenn der Benutzeragent der Anfrage mit einem Mobilgerät in dieser bestimmten Gerätegruppe übereinstimmt.

## Serverseitige Geräterkennung {#server-side-device-detection}

Verwenden Sie Filter und eine Bibliothek mit Gerätespezifikationen, um die Funktionen des Geräts zu bestimmen, das die HTTP-Anforderung ausführt.

### Entwickeln von Gerätegruppenfiltern  {#develop-device-group-filters}

Erstellen Sie einen Gerätegruppenfilter, um eine Reihe von Gerätefunktionsanforderungen zu definieren. Erstellen Sie so viele Filter, wie Sie benötigen, um auf die erforderlichen Gruppen von Gerätefunktionen zu zielen.

Entwerfen Sie Ihre Filter so, dass Sie Kombinationen von ihnen verwenden können, um die Gruppen von Funktionen zu definieren. In der Regel gibt es eine Überlappung der Funktionen verschiedener Gerätegruppen. Daher könnten Sie einige Filter mit mehreren Gerätegruppendefinitionen verwenden.

Nachdem Sie einen Filter erstellt haben, können Sie ihn in der Gruppenkonfiguration verwenden.

Weitere Informationen hierzu finden Sie unter [Erstellen von Gerätegruppenfiltern](/help/sites-developing/groupfilters.md).

### Verwenden der WURFL™-Datenbank  {#using-the-wurfl-database}

AEM verwendet eine abgeschnittene Version der [WURFL](https://wurfl.sourceforge.net/)™-Datenbank, um Gerätefunktionen wie Bildschirmauflösung oder JavaScript-Unterstützung basierend auf dem Benutzeragenten des Geräts abzurufen.

Der XML-Code der WURFL™-Datenbank wird als Knoten unter `/var/mobile/devicespecs` dargestellt, indem die `wurfl.xml`Datei unter `/libs/wcm/mobile/devicespecs/wurfl.xml.` analysiert wird. Die Erweiterung auf Knoten erfolgt beim ersten Starten des `cq-mobile-core`-Bundles.

Gerätefunktionen werden als Knoteneigenschaften gespeichert, und Knoten stellen Gerätemodelle dar. Sie können Abfragen verwenden, um die Funktionen eines Geräts oder eines Benutzeragenten abzurufen.

Da sich die WURFL™-Datenbank weiterentwickelt, müssen Sie sie möglicherweise anpassen oder ersetzen. Um die Mobilgerätedatenbank zu aktualisieren, haben Sie folgende Optionen:

* Ersetzen Sie die Datei durch die neueste Version, wenn Sie über eine Lizenz verfügen, die diese Verwendung zulässt. Siehe „Installieren einer anderen WURFL-Datenbank“.
* Verwenden Sie die Version, die in AEM verfügbar ist, und konfigurieren Sie eine Regex, die Ihren Benutzeragenten-Strings entspricht und auf ein vorhandenes WURFL™ -Gerät verweist. Siehe [Hinzufügen einer regexp-basierten Benutzeragenten-Übereinstimmung](#adding-a-regexp-based-user-agent-matching).

#### Testen der Zuordnung eines Benutzeragenten zu WURFL™-Funktionen {#testing-the-mapping-of-a-user-agent-to-wurfl-capabilities}

Wenn ein Gerät auf Ihre mobile Website zugreift, erkennt AEM das Gerät, ordnet es gemäß seiner Funktionen einer Gerätegruppe zu und sendet eine Ansicht der Seite, die der Gerätegruppe entspricht. Die passende Gerätegruppe liefert die notwendigen Styling-Informationen. Die Zuordnungen können auf der Testseite Mobile User-Agent getestet werden:

`https://localhost:4502/etc/mobile/useragent-test.html`

#### Installieren einer anderen WURFL™-Datenbank {#installing-a-different-wurfl-database}

Die reduzierte WURFL™-Datenbank, die mit AEM installiert wird, ist eine Veröffentlichung, die vor dem 30. August 2011 vorlag. Wenn Ihre Version von WURFL nach dem 30. August 2011 veröffentlicht wurde, vergewissern Sie sich, dass Ihre Verwendung Ihrer Lizenz entspricht.

So installieren Sie eine WURFL™-Datenbank:

1. Erstellen Sie in CRXDE Lite den folgenden Ordner: `/apps/wcm/mobile/devicespecs`
1. Kopieren Sie die WURFL™-Datei in den Ordner.
1. Benennen Sie die Datei in `wurfl.xml` um.

AEM analysiert die Datei `wurfl.xml` automatisch und aktualisiert die Knoten unter `/var/mobile/devicespecs`.

>[!NOTE]
>
>Wenn die vollständige WURFL™-Datenbank aktiviert ist, kann das Analysieren und die Aktivierung einige Minuten dauern. Sie können die Protokolle zu Fortschrittsinformationen ansehen.

#### Hinzufügen eines Regex-basierten Benutzeragenten-Abgleichs  {#adding-a-regexp-based-user-agent-matching}

Fügen Sie einen Benutzeragenten als regulären Ausdruck unter /apps/wcm/mobile/devicespecs/wurfl/regexp hinzu, um auf einen vorhandenen WURFL™-Gerätetyp zu verweisen.

1. Erstellen Sie in **CRXDE Lite** einen Knoten unterhalb von /apps/wcm/mobile/devicespecs/regexp, z. B. apple_ipad_ver1.
1. Fügen Sie dem Knoten  folgende Eigenschaften hinzu:

   * **regexp**: regulärer Ausdruck, der Benutzeragenten definiert, z. B.: .*Mozilla.*iPad.*AppleWebKit.*Safari.*
   * **deviceId**: die Geräte-ID, wie in der wurfl.xml definiert, z. B.: apple_ipad_ver1

Die obige Konfiguration bewirkt, dass Geräte, für die der User-Agent mit dem bereitgestellten regulären Ausdruck übereinstimmt, der WURFL™-Geräte-ID apple_ipad_ver1 zugeordnet werden, sofern vorhanden.

## Clientseitige Geräterkennung {#client-side-device-detection}

In diesem Abschnitt wird beschrieben, wie Sie die clientseitige Erkennung von AEM auf dem Gerät verwenden, um das Seitenrendering zu optimieren oder dem Client alternative Websiteversionen bereitzustellen.

AEM unterstützt die Client-seitige Erkennung von Geräten basierend auf `BrowserMap`. `BrowserMap` wird in AEM als Client-Bibliothek unter bereitgestellt  `/etc/clientlibs/browsermap`.

`BrowserMap` bietet Ihnen drei Strategien, die Sie verwenden können, um einem Client eine alternative Website bereitzustellen, die in der folgenden Reihenfolge verwendet wird:

1. [Alternative Links](#providing-alternate-links)
1. [Gerätegruppenspezifische URL](#definingdevicegroupspecificurl)
1. [Selektorbasierte URL](#defining-selector-based-urls)

>[!NOTE]
>
>Weitere Informationen zur Integration von Client-Bibliotheken finden Sie im Abschnitt [Verwendung clientseitiger HTML-Bibliotheken](/help/sites-developing/clientlibs.md).

### Bereitstellen alternativer Links {#providing-alternate-links}

Der OSGi-Dienst `PageVariantsProvider` kann alternative Links für Sites generieren, die zur gleichen Familie gehören. Um Websites zu konfigurieren, die vom Dienst berücksichtigt werden, muss ein Knoten `cq:siteVariant` zum Knoten `jcr:content` aus dem Stammverzeichnis der Seite hinzugefügt werden.

Der Knoten `cq:siteVariant` muss die folgenden Eigenschaften aufweisen:

* `cq:childNodesMapTo` - bestimmt, welchem Attribut des Link-Elements die untergeordneten Knoten zugeordnet werden; Es wird empfohlen, den Inhalt Ihrer Website so zu organisieren, dass die untergeordneten Elemente des Stammknotens den Stamm für eine Sprachvariante Ihrer globalen Website darstellen (z. B.  `/content/mysite/en`,  `/content/mysite/de`); in diesem Fall  `cq:childNodesMapTo` sollte der Wert des  `hreflang`sein;
* `cq:variantDomain` - gibt an, welche `Externalizer`-Domäne zum Generieren der absoluten URLs der Seitenvarianten verwendet wird. Wenn dieser Wert nicht gesetzt ist, werden die Seitenvarianten mit relativen Links erzeugt;
* `cq:variantFamily` - gibt an, zu welcher Familie von Websites diese Seite gehört; mehrere gerätespezifische Darstellungen derselben Website sollten derselben Familie angehören;
* `media` - speichert die Werte des Medienattributs des Link-Elements; Es wird empfohlen, den Namen der `BrowserMap`-registrierten `DeviceGroups` zu verwenden, damit die `BrowserMap`-Bibliothek die Clients automatisch an die richtige Variante der Website weiterleiten kann.

#### PageVariantsProvider und Externalizer {#pagevariantsprovider-and-externalizer}

Wenn der Wert der `cq:variantDomain`-Eigenschaft eines `cq:siteVariant`-Knotens nicht leer ist, generiert der `PageVariantsProvider`-Dienst absolute Links, die diesen Wert als konfigurierte Domäne für den `Externalizer`-Dienst verwenden. Stellen Sie sicher, dass Sie den `Externalizer`-Dienst entsprechend Ihren Einstellungen konfigurieren.

>[!NOTE]
>
>Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

### Definieren einer gerätegruppenspezifischen URL  {#defining-a-device-group-specific-url}

Wenn Sie keine alternativen Links verwenden möchten, können Sie für jede `DeviceGroup` eine globale URL konfigurieren. Wir empfehlen, eine eigene Client-Bibliothek zu erstellen, die die Client-Bibliothek `browsermap.standard` einbettet, die Gerätegruppen jedoch neu definiert.

 ist so konzipiert, dass Gerätegruppendefinitionen überschrieben werden können, indem eine neue Gerätegruppe mit demselben Namen für das `BrowserMap`BrowserMap-Objekt aus Ihrer angepassten Client-Bibliothek erstellt und hinzugefügt wird.

>[!NOTE]
>
>Für weitere Details lesen Sie den Abschnitt [Angepasste BrowserMap](#creatingacustomisedbrowsermap).

### Definieren selektorbasierter URLs  {#defining-selector-based-urls}

Wenn keiner der vorherigen Mechanismen verwendet wurde, um eine alternative Website für `BrowserMap` anzugeben, werden Selektoren, die die Namen der `DeviceGroups` verwenden, zu den `URL`s hinzugefügt. In diesem Fall sollten Sie Ihre eigenen Servlets bereitstellen, die die Anfragen bearbeiten .

Beispiel: Ein Gerät, das `www.example.com/index.html` durchsucht und von BrowserMap als `smartphone` identifiziert wird, wird an `www.example.com/index.smartphone.html.` weitergeleitet.

### Verwenden von BrowserMap auf Ihren Seiten {#using-browsermap-on-your-pages}

Um die standardmäßige BrowserMap-Client-Bibliothek auf einer Seite verwenden zu können, müssen Sie die `/libs/wcm/core/browsermap/browsermap.jsp`-Datei mit einem `cq:include`Tag im `head`-Abschnitt Ihrer Seite einfügen.

```xml
<cq:include script="/libs/wcm/core/browsermap/browsermap.jsp" />
```

Neben dem Hinzufügen der `BrowserMap`-Client-Bibliothek zu Ihren `JSP`-Dateien müssen Sie auch eine `cq:deviceIdentificationMode` String-Eigenschaft hinzufügen, die auf `client-side` gesetzt ist, um den Knoten `jcr:content` unterhalb des Stammverzeichnisses Ihrer Website zu erweitern.

### Überschreiben des Standardverhaltens von BrowserMap {#overriding-browsermap-s-default-behaviour}

Wenn Sie `BrowserMap` anpassen möchten, indem Sie die `DeviceGroups` überschreiben oder weitere Untersuchungen hinzufügen, sollten Sie Ihre eigene clientseitige Bibliothek erstellen, in die Sie die clientseitige Bibliothek `browsermap.standard` einbetten.

Außerdem müssen Sie die `BrowserMap.forwardRequest()`-Methode in Ihrem `JavaScript`-Code manuell aufrufen.

>[!NOTE]
>
>Weitere Informationen zur Integration von Client-Bibliotheken finden Sie im Abschnitt [Verwendung clientseitiger HTML-Bibliotheken](/help/sites-developing/clientlibs.md).

Nachdem Sie Ihre benutzerdefinierte `BrowserMap`-Client-Bibliothek erstellt haben, schlagen wir folgenden Ansatz vor:

1. Erstellen Sie eine Datei `browsermap.jsp` in Ihrer Anwendung

   ```xml
   <%@include file="/libs/foundation/global.jsp" %>
   <%@ taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
   <%@ page import="
       com.day.cq.wcm.api.variants.PageVariant,
       com.day.cq.wcm.api.variants.PageVariantsProvider,
       com.day.cq.wcm.api.devicedetection.DeviceIdentificationMode,
       com.day.cq.wcm.api.WCMMode"
   %>
   <%
       final PageVariantsProvider p = sling.getService(PageVariantsProvider.class);
       if(p == null) {
           throw new IllegalStateException("Missing PageVariantsProvider service");
       }
       for(PageVariant v : p.getVariants(currentPage, slingRequest)) {
           final String curVar = v.getAttributes().get("data-current-variant");
           String media = v.getAttributes().get("media");
           if (media != null) {
               media = media.replaceAll(" ", "");
           }
   %>
       <link
           rel="alternate"
           data-cq-role="site.variant"
           title="<%= xssAPI.encodeForHTMLAttr(v.getTitle()) %>"
           hreflang="<%= xssAPI.encodeForHTMLAttr(v.getAttributes().get("hreflang")) %>"
           media="<%= xssAPI.encodeForHTMLAttr(media) %>"
           href="<%= xssAPI.getValidHref(v.getURL()) %>"
           <% if(curVar != null) { %> data-current-variant="<%= curVar %>"<% } %>
       />
   <%
       }
       Boolean browserMapEnabled = true;
       final DeviceIdentificationMode dim = sling.getService(DeviceIdentificationMode.class);
       String[] selectors  = slingRequest.getRequestPathInfo().getSelectors();
       boolean isPortletRequest = false;
       for (int i = 0; i < selectors.length; i++) {
           if ("portlet".equals(selectors[i])) {
               isPortletRequest = true;
               break;
           }
       }
       if (isPortletRequest) {
           log.debug("Request was made by a portlet container - BrowserMap will not be embedded");
       } else {
           final WCMMode wcmMode = WCMMode.fromRequest(slingRequest);
           boolean shouldIncludeClientLib = false;
           if (WCMMode.EDIT != wcmMode && WCMMode.PREVIEW != wcmMode && WCMMode.DESIGN != wcmMode) {
               if (dim != null) {
                   final String mode = dim.getDeviceIdentificationModeForPage(currentPage);
                   shouldIncludeClientLib = DeviceIdentificationMode.CLIENT_SIDE.equals(mode);
                   if (shouldIncludeClientLib) {
                       browserMapEnabled = (Boolean) request.getAttribute("browsermap.enabled");
                       if (browserMapEnabled == null) {
                           browserMapEnabled = true;
                       }
                   }
               }
           }
   %>
           <c:if test="<%= !browserMapEnabled %>">
               <meta name="browsermap.enabled" content="false">
           </c:if>
           <c:if test="<%= shouldIncludeClientLib %>">
               <meta name="viewport" content="width=device-width, initial-scale=1.0">
               <cq:includeClientLib categories="browsermap.custom"/>
           </c:if>
   <%
       }
   %>
   ```

1. Fügen Sie die Datei `broswermap.jsp` in Ihren Kopfabschnitt ein.

   ```xml
   <cq:include script="browsermap.jsp" />
   ```

### Ausschließen von BrowserMap von bestimmten Seiten {#excluding-browsermap-from-certain-pages}

Wenn Sie die BrowserMap-Bibliothek von einigen Ihrer Seiten ausschließen möchten, auf denen Sie keine Client-Erkennung benötigen, können Sie ein Anforderungsattribut hinzufügen:

```xml
<%
request.setAttribute("browsermap.enabled", false);
%>
```

Dadurch wird das `/libs/wcm/core/browsermap/browsermap.jsp`-Skript dazu gebracht, der Seite ein Meta-Tag hinzuzufügen, das `BrowserMap` veranlasst, keine Erkennung durchzuführen:

```xml
<meta name="browsermap.enabled" content="false">
```

### Testen einer bestimmten Version einer Website {#testing-a-specific-version-of-a-web-site}

Normalerweise leitet das BrowserMap-Skript die Besucher immer an die am besten geeignete Version der Website weiter. Normalerweise werden Besucher bei Bedarf auf die Desktop- oder auf die mobile Seite umgeleitet.

Sie können das Gerät einer beliebigen Anforderung erzwingen, um eine bestimmte Version einer Website zu testen, indem Sie den Parameter `device` zu Ihrer URL hinzufügen. Die folgende URL stellt die mobile Version der Geometrixx Outdoors-Website dar.

`https://localhost:4502/content/geometrixx-outdoors/en.html?wcmmode=disabled&device=smartphone`

>[!NOTE]
>
>Der Parameter `wcmmode` ist auf `disabled` festgelegt, um das Verhalten einer Veröffentlichungsinstanz zu simulieren.

Der überschriebene Gerätewert wird in einem Cookie gespeichert, sodass Sie Ihre Website durchsuchen können, ohne den `device`-Parameter zu jeder `URL` hinzuzufügen.

Als Konsequenz müssen Sie dieselbe `URL` aufrufen, wenn `device` auf `browser` eingestellt ist, um zur Desktop-Version der Website zurückzukehren.

>[!NOTE]
>
>BrowserMap speichert den überschriebenen Gerätewert in einem Cookie namens `BMAP_device`. Durch das Löschen dieses Cookies wird sichergestellt, dass CQ die entsprechende Version der Website gemäß Ihrem aktuellen Gerät (z. B. Desktop oder Mobile) bereitstellt.

## Mobile Anfrageverarbeitung  {#mobile-request-processing}

AEM verarbeitet eine Anfrage, die von einem Mobilgerät ausgegeben wird, das zur Touch-Gerätegruppe gehört, wie folgt:

1. Ein iPad sendet eine Anfrage an die AEM Veröffentlichungsinstanz, z. B. `https://localhost:4503/content/geometrixx_mobile/en/products.html`
1. AEM ermittelt, ob die Site der angeforderten Seite eine mobile Site ist (indem überprüft wird, ob die Seite der ersten Ebene `/content/geometrixx_mobile` die mobile Seitenkomponente erweitert). Wenn ja:
1. AEM sucht die Gerätefunktionen basierend auf dem Benutzeragenten im Anfrageheader.
1. AEM ordnet die Gerätefunktionen der Gerätegruppe zu und legt `touch` als Gerätegruppenauswahl fest.
1. AEM leitet die Anfrage an `https://localhost:4503/content/geometrixx_mobile/en/products.touch.html.` weiter.
1. AEM sendet die Antwort an das iPad:

   * `products.touch.html` wird auf die übliche Weise gerendert und kann zwischengespeichert werden.
   * Die Rendering-Komponenten verwenden Selektoren, um die Präsentation anzupassen.
   * AEM fügt die mobile Auswahl automatisch zu allen internen Links auf der Seite hinzu.

### Statistiken {#statistics}

Sie erhalten Statistiken über die Anzahl der Anfragen, die von Mobilgeräten an den AEM Server gestellt wurden. Die Anzahl der Anfragen kann wie folgt aufgeteilt werden:

* pro Gerätegruppe und Gerät
* pro Jahr, Monat und Tag

So zeigen Sie die Statistiken an:

1. Gehen Sie zur **Tools-Konsole**.
1. Öffnen Sie die Seite **Gerätestatistik** unter **Tools** > **Mobile**.
1. Klicken Sie auf den Link, um die Statistiken für ein bestimmtes Jahr, einen bestimmten Monat oder einen bestimmten Tag anzuzeigen.

Die **Statistikseite** sieht folgendermaßen aus:

![screen_shot_2012-02-01at24353pm](assets/screen_shot_2012-02-01at24353pm.png)

>[!NOTE]
>
>Die Seite **Statistics** wird erstellt, wenn ein Mobilgerät zum ersten Mal auf AEM zugreift und erkannt wird. Zuvor ist sie nicht verfügbar.

Wenn Sie einen Eintrag in der Statistik generieren müssen, können Sie folgendermaßen vorgehen:

1. Verwenden Sie ein Mobilgerät oder einen Emulator (z. B. https://chrispederick.com/work/user-agent-switcher/ in Firefox).
1. Fordern Sie eine mobile Seite in der Autoreninstanz an, indem Sie den Bearbeitungsmodus deaktivieren, z. B.:
   `https://localhost:4502/content/geometrixx_mobile/en/products.html?wcmmode=disabled`

Die **Statistikseite** ist jetzt verfügbar.

### Unterstützen von Seiten-Caching für „Link an einen Freund senden“{#supporting-page-caching-for-send-link-to-a-friend-links}

Mobilseiten sind im Allgemeinen im Dispatcher zwischenspeicherbar, da für eine Gerätegruppe gerenderte Seiten in der Seiten-URL durch die Gerätegruppenauswahl unterschieden werden, z. B. `/content/mobilepage.touch.html`. Eine Anfrage an eine mobile Seite ohne einen Selektor wird niemals zwischengespeichert, da in diesem Fall die Geräteerkennung arbeitet und schließlich zu der entsprechenden Gerätegruppe (oder „Nomatch“) umgeleitet wird. Eine mit einem Gerätegruppenselektor gerenderte mobile Seite wird vom Link-Rewriter verarbeitet, der alle Links innerhalb der Seite so umschreibt, dass sie auch den Gerätegruppenselektor enthält. Dadurch wird verhindert, dass die Geräteerkennung bei jedem Klick auf eine bereits qualifizierte Seite erneut durchgeführt wird.

Daher könnte das folgende Szenario eintreten:

Benutzerin Alice wird zu `coolpage.feature.html` umgeleitet und sendet diese URL an einen Freund Bob, der mit einem anderen Client, der in die `touch`-Gerätegruppe fällt, darauf zugreift.

Wenn `coolpage.feature.html` von einem Front-End-Cache geliefert wird, erhält AEM keine Chance, die Anfrage zu analysieren, um herauszufinden, dass der mobile Selektor nicht mit dem neuen Benutzeragenten übereinstimmt, und Bob erhält die falsche Darstellung.

Um dieses Problem zu lösen, können Sie auf den Seiten eine einfache Auswahlbenutzeroberfläche einfügen, über die Endbenutzer die Gerätegruppe überschreiben können, die von AEM ausgewählt wurde. Im obigen Beispiel ermöglicht ein Link (oder ein Symbol) auf der Seite dem Endbenutzer, zu `coolpage.touch.html` zu wechseln, wenn er denkt, dass sein Gerät gut genug ist dafür.
