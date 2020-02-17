---
title: Mobil mit Inhaltssynchronisierung
seo-title: Mobil mit Inhaltssynchronisierung
description: Folgen Sie dieser Seite, um mehr über die Inhaltssynchronisierung zu erfahren. In AEM erstellte Seiten können als App-Inhalt verwendet werden, auch wenn das Gerät offline ist. Da AEM-Seiten zudem auf Webstandards basieren, können sie plattformübergreifend verwendet werden, um sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht Ihnen die einfache Aktualisierung von App-Inhalten.
seo-description: Folgen Sie dieser Seite, um mehr über die Inhaltssynchronisierung zu erfahren. In AEM erstellte Seiten können als App-Inhalt verwendet werden, auch wenn das Gerät offline ist. Da AEM-Seiten zudem auf Webstandards basieren, können sie plattformübergreifend verwendet werden, um sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht Ihnen die einfache Aktualisierung von App-Inhalten.
uuid: 11f74cc5-99a5-4186-9b60-b19351305432
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 8fb70ca4-86fc-477d-9773-35b84d5e85a8
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Mobil mit Inhaltssynchronisierung{#mobile-with-content-sync}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Verwenden Sie die Inhaltssynchronisierung, um Inhalte zu verpacken, damit sie in nativen mobilen Anwendungen verwendet werden können. In AEM erstellte Seiten können als App-Inhalt verwendet werden, auch wenn das Gerät offline ist. Da AEM-Seiten zudem auf Webstandards basieren, können sie plattformübergreifend verwendet werden, um sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht Ihnen die einfache Aktualisierung von App-Inhalten.

Das Content Sync-Framework erstellt eine Archivdatei, die den Webinhalt enthält. Der Inhalt kann alles Mögliche sein, von einfachen Seiten, Bildern, PDF-Dateien oder ganzen Webanwendungen. Die Content Sync-API bietet Zugriff auf die Archivdatei aus mobilen Apps oder Erstellungsprozessen, damit die Inhalte abgerufen und in die App eingeschlossen werden können.

Die folgende Schrittfolge zeigt einen typischen Anwendungsfall für die Inhaltssynchronisierung:

1. Der AEM-Entwickler erstellt eine Inhaltssynchronisierungskonfiguration, die den einzuschließenden Inhalt angibt.
1. Das Content Sync-Framework erfasst und speichert den Inhalt zwischen.
1. Auf einem Mobilgerät wird die mobile Anwendung gestartet und fordert Inhalte vom Server an, der in einer ZIP-Datei bereitgestellt wird.
1. Der Client entpackt den ZIP-Inhalt in das lokale Dateisystem. Die Ordnerstruktur in der ZIP-Datei simuliert die Pfade, die ein Client (z. B. ein Browser) normalerweise vom Server anfordert.
1. Der Client öffnet den Inhalt in einem eingebetteten Browser oder verwendet ihn auf andere Weise.
1. Später fordert der Client aktualisierte Inhalte vom Server an. Das Content Sync-Framework bietet inkrementelle Updates, um die Downloadgröße und -zeit zu reduzieren. Dies kann bei Mobilgeräten aufgrund der begrenzten Bandbreite oder des begrenzten Datenvolumens wichtig sein.

## Entwicklung der Content Sync-Handler {#developing-the-content-sync-handlers}

Einige der Richtlinien zum Entwickeln von Content Sync Handlers lauten wie folgt:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder erweitern Sie eine Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler erweitern*
* Handler darf nur dann true melden, wenn der ContentSync-Cache aktualisiert wird. Bei der falschen Berichterstellung &quot;true&quot;erstellt AEM ein Update, wenn kein Update tatsächlich vorgenommen wurde.
* Der Handler sollte den Cache nur aktualisieren, wenn sich der Inhalt tatsächlich geändert hat. Schreiben Sie nicht in den Cache, wenn kein Weiß erforderlich ist. Dadurch wird ein unnötiges Update erstellt.

>[!NOTE]
>
>Aktivieren Sie die *ContentSync-Debug-Protokollierung* über OSGI-Protokollkonfigurationen auf dem Paket *com.day.cq.contentsync*. Auf diese Weise können Sie verfolgen, welche Handler ausgeführt haben und ob sie den Cache aktualisiert und Berichte zur Aktualisierung des Cache erstellt haben.

## Content Sync Content konfigurieren {#configuring-the-content-sync-content}

Erstellen Sie eine Content Sync-Konfiguration, um den Inhalt der ZIP-Datei anzugeben, die an den Client gesendet wird. Sie können beliebig viele Konfigurationen für die Inhaltssynchronisierung erstellen. Jede Konfiguration hat einen Namen zur Identifizierung.

Um eine Content Sync-Konfiguration zu erstellen, fügen Sie dem Repository einen `cq:ContentSyncConfig` Knoten hinzu, wobei die `sling:resourceType` Eigenschaft auf `contentsync/config`festgelegt ist. Der `cq:ContentSyncConfig` Knoten kann sich an einer beliebigen Stelle im Repository befinden, der Knoten muss jedoch für Benutzer in der AEM-Veröffentlichungsinstanz zugänglich sein. Daher sollten Sie den unten stehenden Knoten hinzufügen `/content`.

Um den Inhalt der ZIP-Datei für die Inhaltssynchronisierung anzugeben, fügen Sie dem Knoten &quot;cq:ContentSyncConfig&quot;untergeordnete Knoten hinzu. Die folgenden Eigenschaften jeder untergeordneten Node geben an, welche Inhaltselemente einbezogen und wie sie beim Hinzufügen verarbeitet werden sollen:

* `path`: Der Speicherort des Inhalts.
* `type`: Der Name des Konfigurationstyps, der für die Verarbeitung des Inhalts verwendet wird. Es stehen verschiedene Typen zur Verfügung und werden im Abschnitt *Konfigurationstypen* beschrieben.

Weitere Informationen finden Sie unter *Beispielkonfiguration* für Inhaltssynchronisierung.

Nachdem Sie die Konfiguration für die Inhaltssynchronisierung erstellt haben, wird sie in der Inhaltssynchronisierungskonsole angezeigt.

>[!NOTE]
>
>Das Content Sync-Framework überprüft nicht, ob Abhängigkeiten von Assets und designbezogenen Dateien in Content Sync-Paketen enthalten sind. Stellen Sie sicher, dass alle erforderlichen Dateien in die ZIP-Datei aufgenommen werden.

### Konfigurieren des Zugriffs auf Inhaltssynchronisierungs-Downloads {#configuring-access-to-content-sync-downloads}

Geben Sie einen Benutzer oder eine Gruppe an, die von der Inhaltssynchronisierung heruntergeladen werden kann. Sie können den Standardbenutzer oder die Standardgruppe konfigurieren, die von allen Content Sync-Caches heruntergeladen werden kann. Außerdem können Sie den Standard überschreiben und den Zugriff für eine bestimmte Content Sync-Konfiguration konfigurieren.

Wenn AEM installiert ist, können Mitglieder der Administratorgruppe standardmäßig von der Inhaltssynchronisierung herunterladen.

#### Festlegen des Standardzugriffs für Inhaltssynchronisierungs-Downloads {#setting-the-default-access-for-content-sync-downloads}

Der Day CQ Content Sync Manager-Dienst steuert den Zugriff auf die Inhaltssynchronisierung. Konfigurieren Sie diesen Dienst, um den Benutzer oder die Gruppe anzugeben, die standardmäßig von der Inhaltssynchronisierung heruntergeladen werden kann.

Wenn Sie den Dienst mit der Webkonsole[](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console)konfigurieren, geben Sie den Namen des Benutzers oder der Gruppe als Wert der Authorizable-Eigenschaft des Fallback-Cache ein.

Wenn Sie im Repository [konfigurieren](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository), verwenden Sie die folgenden Informationen zum Dienst:

* PID: com.day.cq.contentsync.impl.ContentSyncManagerImpl
* Eigenschaftsname: contentsync.fallback.autorizable

#### Download-Zugriff für einen Inhaltssynchronisierungscache überschreiben {#overriding-download-access-for-a-content-sync-cache}

Um den Downloadzugriff für eine bestimmte Content Sync-Konfiguration zu konfigurieren, fügen Sie die folgende Eigenschaft zum `cq:ContentSyncConfig` Knoten hinzu:

* Name: autorizable
* Typ: String
* Wert: Der Name des Benutzers oder der Gruppe, der/die heruntergeladen werden kann.

Beispielsweise können Benutzer mit Ihrer App Updates direkt über die Inhaltssynchronisierung installieren. Damit alle Benutzer die Aktualisierung herunterladen können, legen Sie den Wert der Eigenschaft authorized auf `everyone`.

Wenn der `cq:ContentSyncConfig` Knoten keine autorisierbare Eigenschaft hat, bestimmt der Standardbenutzer oder die Standardgruppe, die für die Authorizable-Eigenschaft des Day CQ Content Sync Manager-Dienstes konfiguriert ist, wer heruntergeladen werden kann.

### Konfigurieren des Benutzers zum Aktualisieren eines Inhaltssynchronisierungscache {#configuring-the-user-for-updating-a-content-sync-cache}

Wenn ein Benutzer eine Aktualisierung des Inhalts-Synchronisierungs-Cache ausführt, führt ein bestimmtes Benutzerkonto die Aktion im Auftrag des Benutzers durch. Der anonyme Benutzer aktualisiert standardmäßig alle Inhaltssynchronisierungs-Caches.

Sie können den Standardbenutzer außer Kraft setzen und einen Benutzer oder eine Gruppe angeben, der bzw. die einen bestimmten Content Sync-Cache aktualisiert.

Um den Standardbenutzer zu überschreiben, geben Sie einen Benutzer oder eine Gruppe an, die bzw. die Aktualisierungen für eine bestimmte Content Sync-Konfiguration durchführt, indem Sie die folgende Eigenschaft zum Knoten cq:ContentSyncConfig hinzufügen:

* Name: `updateuser`
* Typ: `String`
* Wert: Der Name des Benutzers oder der Gruppe, der bzw. die die Aktualisierungen durchführen kann.

Wenn der `cq:ContentSyncConfig` Knoten keine `updateuser` Eigenschaft hat, aktualisiert der standardmäßige `anonymous` Benutzer den Cache.

### Konfigurationstypen {#configuration-types}

Die Verarbeitung kann von der Darstellung einfacher JSON bis zur vollständigen Darstellung von Seiten einschließlich der referenzierten Assets reichen. In diesem Abschnitt werden die verfügbaren Konfigurationstypen und ihre spezifischen Parameter aufgelistet:

**Kopieren** Sie einfach Dateien und Ordner.

* **path** - Wenn der Pfad auf eine einzelne Datei verweist, wird nur die Datei kopiert. Wenn er auf einen Ordner verweist (einschließlich Seitenknoten), werden alle unten aufgeführten Dateien und Ordner kopiert.

**Inhalt** Render-Inhalt mit standardmäßiger [Sling-Anforderungsverarbeitung](/help/sites-developing/the-basics.md#sling-request-processing).

* **path** - Pfad zur Ressource, die ausgegeben werden soll.
* **extension** - Erweiterung, die in der Anforderung verwendet werden sollte. Häufige Beispiele sind *html* und *json*, aber jede andere Erweiterung ist möglich.

* **selector** - Optionale Selektoren, durch Punkt getrennt. Häufige Beispiele sind *Berührungen* zum Rendern von mobilen Versionen einer Seite oder *Unendlichkeit* für die JSON-Ausgabe.

**clientlib** Eine JavaScript- oder CSS-Client-Bibliothek verpacken.

* **path** - Pfad zum Stammordner der Client-Bibliothek.
* **extension** - Typ der Client-Bibliothek. Dies sollte derzeit entweder auf *js* oder auf *css* eingestellt sein.

**Assets**

Sammelt ursprüngliche Darstellungen von Assets.

* **path** - Pfad zu einem Asset-Ordner unter /content/dam.

**Bild** erfasst ein Bild.

* **path** - Pfad zu einer Bildressource.

Der Bildtyp wird verwendet, um das We Retail-Logo in die ZIP-Datei einzuschließen.

**Seiten** rendern Sie AEM-Seiten und erfassen Sie referenzierte Assets.

* **path** - Pfad zu einer Seite.
* **extension** - Erweiterung, die in der Anforderung verwendet werden sollte. Für Seiten ist dies fast immer *html*, aber andere sind noch möglich.

* **selector** - Optionale Selektoren, durch Punkt getrennt. Häufige Beispiele sind *Berührungen* zum Rendern von mobilen Versionen einer Seite.

* **ep** - Optionale boolesche Eigenschaft, die bestimmt, ob untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* **includeImages** - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

   Standardmäßig werden nur Bildkomponenten mit einem Ressourcentyp wie Stiftung/Komponenten/Bild für die Aufnahme in Betracht gezogen. Sie können weitere Ressourcentypen hinzufügen, indem Sie den **Day CQ WCM Pages Update Handler** in der Webkonsole konfigurieren.

**rewrite** Der rewrite-Knoten definiert, wie die Links auf der exportierten Seite umgeschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Der `rewrite` Knoten muss sich unter dem `page` Knoten befinden.

Der `rewrite` Knoten kann eine oder mehrere der folgenden Eigenschaften haben:

* `clientlibs`: überschreibt clientlibs-Pfade.

* `images`: Erstellt Bildpfade neu.
* `links`: Umschreibt Verknüpfungspfade.

Jede Eigenschaft kann einen der folgenden Werte haben:

* `REWRITE_RELATIVE`: überschreibt den Pfad mit einer relativen Position zur Datei &quot;page.html&quot;im Dateisystem.

* `REWRITE_EXTERNAL`: schreibt den Pfad unter Verwendung des AEM [Externalizer-Dienstes](/help/sites-developing/externalizer.md)neu, indem er auf die Ressource auf dem Server verweist.

Mit dem AEM-Dienst **PathRewriterTransformerFactory** können Sie die spezifischen HTML-Attribute konfigurieren, die umgeschrieben werden. Der Dienst kann in der Webkonsole konfiguriert werden und verfügt über eine Konfiguration für jede Eigenschaft des `rewrite` Knotens: `clientlibs`, `images` und `links`.

Diese Funktion wurde in AEM 5.5 hinzugefügt.

### Beispiel für die Synchronisierung von Inhalten {#example-content-sync-configuration}

Die folgende Liste zeigt eine Beispielkonfiguration für die Inhaltssynchronisierung.

```xml
+ weretail_go [cq:ContentSyncConfig]
  - sling:resourceType = "contentsync/config"

  + etc.designs.default [nt:unstructured]
    - path = "/etc/designs/default"
    - type = "copy"

  + etc.designs.mobile [nt:unstructured]
    - path = "/etc/designs/mobile"
    - type = "copy"

  + events.plist [nt:unstructured]
    - path = "/content/weretail_mobile/en/events/jcr:content/par/events"
    - type = "content"
    - extension = "plist"

  + events.touch.html [nt:unstructured]
    - path = "/content/weretail_mobile/en/events"
    - type = "pages"
    - extension = "html"
    - selector = "touch"

  + logo [nt:unstructured]
    - path = "/etc/designs/mobile/jcr:content/mobilecontentpage/logo"
    - type = "logo"

  + manifest [nt:unstructured]
    - indexPage = "/content/weretail_mobile/en/events.touch.html"
    - metadataPlist = "/content/weretail_mobile/en/events/_jcr_content/par/events.plist"

  + ...
```

**etc.designs.default und etc.designs.mobile** Die ersten beiden Einträge der Konfiguration sollten ziemlich offensichtlich sein. Da wir einige mobile Seiten einbeziehen werden, benötigen wir die entsprechenden Designdateien unter /etc/designs. Da keine zusätzliche Verarbeitung erforderlich ist, ist eine Kopie ausreichend.

**events.plist** Dieser Eintrag ist etwas Besonderes. Wie in der Einleitung erwähnt, sollte die Anwendung eine Landkartenansicht mit Markern der Veranstaltungsorte bereitstellen. Wir werden die erforderlichen Standortinformationen als separate Datei im PLIST-Format bereitstellen. Damit dies funktioniert, verfügt die Ereignislistenkomponente, die auf der Indexseite verwendet wird, über ein Skript mit dem Namen plist.jsp. Dieses Skript wird ausgeführt, wenn die Ressource der Komponente mit der Erweiterung .plist angefordert wird. Wie üblich wird der Komponentenpfad in der Eigenschaft path angegeben und der Typ ist auf content eingestellt, da wir die [Sling-Anforderungsverarbeitung](/help/sites-developing/the-basics.md#sling-request-processing)nutzen möchten.

**events.touch.html** Als Nächstes werden die tatsächlichen Seiten angezeigt, die in der App angezeigt werden. Die Pfadeigenschaft wird auf die Stamm-Seite der Ereignisse festgelegt. Alle Ereignisseiten unterhalb dieser Seite werden ebenfalls einbezogen, da die Eigenschaft Deep standardmäßig auf true gesetzt ist. Wir verwenden Seiten als Konfigurationstyp, sodass alle Bilder oder andere Dateien, auf die von einem Bild oder einer Downloadkomponente auf einer Seite verwiesen werden kann, einbezogen werden. Darüber hinaus erhalten Sie durch Festlegen des Touchselektors eine mobile Version der Seiten. Die Konfiguration im Feature Pack enthält mehr Einträge dieser Art, aber sie werden hier aus Gründen der Einfachheit nicht berücksichtigt.

**logo** Der Logo-Konfigurationstyp wurde bisher nicht erwähnt und ist keiner der eingebauten Typen. Das Inhaltssynchronisierungs-Framework ist jedoch in gewissem Maße erweiterbar. Dies ist ein Beispiel dafür, das im nächsten Abschnitt behandelt wird.

**manifest** Es ist oft wünschenswert, dass in der ZIP-Datei eine Art von Metadaten enthalten ist, wie zum Beispiel die Startseite Ihres Inhalts. Die Hartkodierung solcher Informationen verhindert jedoch, dass Sie sie später leicht ändern können. Das Content Sync-Framework unterstützt diesen Anwendungsfall, indem es nach einem Manifestknoten in der Konfiguration sucht, der einfach anhand des Namens identifiziert wird und keinen Konfigurationstyp erfordert. Jede auf diesem Knoten definierte Eigenschaft wird einer Datei hinzugefügt, die auch als manifest bezeichnet wird und sich im Stammverzeichnis der ZIP-Datei befindet.

In diesem Beispiel sollte die Seite zur Ereignisaufzählung die Anfangsseite sein. Diese Informationen werden in der Eigenschaft **indexPage** bereitgestellt und können daher jederzeit problemlos geändert werden. Eine zweite Eigenschaft definiert den Pfad der Datei &quot; *events.plist* &quot;. Wie wir später sehen werden, kann die Client-Anwendung jetzt das Manifest lesen und entsprechend handeln.

Sobald die Konfiguration eingerichtet ist, können die Inhalte mit einem Browser oder einem anderen HTTP-Client heruntergeladen werden oder wenn Sie für iOS entwickeln, können Sie die dedizierte WAppKitSync-Client-Bibliothek verwenden. Der Downloadspeicherort besteht aus dem Pfad der Konfiguration und der Erweiterung *.zip* , z. B. beim Arbeiten mit einer lokalen AEM-Instanz: *http://localhost:4502/content/weretail_go.zip*

### Die Inhaltssynchronisierungskonsole {#the-content-sync-console}

In der Content Sync-Konsole werden alle Inhaltssynchronisierungskonfigurationen im Repository (alle Knoten des Typs `cq:ContentSyncConfig`) aufgelistet. Für jede Konfiguration haben Sie folgende Möglichkeiten:

* Aktualisieren Sie den Cache.
* Löschen Sie den Cache.
* Laden Sie eine vollständige ZIP-Datei herunter.
* Laden Sie eine ZIP-Datei bis zu einem bestimmten Datum und einer bestimmten Uhrzeit herunter.

Es kann für die Entwicklung und Fehlerbehebung nützlich sein.

Die Konsole ist abrufbar unter:

`http://localhost:4502/libs/cq/contentsync/content/console.html`

Diese sieht nun wie folgt aus:

![chlimage_1-50](assets/chlimage_1-50.png)

### Erweitern des Content Sync-Frameworks {#extending-the-content-sync-framework}

Obwohl die Anzahl der Konfigurationsoptionen bereits sehr umfangreich ist, deckt sie möglicherweise nicht alle Anforderungen Ihres spezifischen Anwendungsfalls ab. In diesem Abschnitt werden die Erweiterungspunkte des Content Sync-Frameworks und die Erstellung benutzerdefinierter Konfigurationstypen beschrieben.

Für jeden Konfigurationstyp gibt es einen *Content Update Handler*, eine OSGi-Komponentenfabrik, die für diesen bestimmten Typ registriert ist. Diese Handler erfassen Inhalte, verarbeiten sie und fügen sie einem Cache hinzu, der vom Content Sync-Framework verwaltet wird. Implementieren Sie die folgende Schnittstelle oder abstrakte Basisklasse:

* `com.day.cq.contentsync.handler.ContentUpdateHandler` - Schnittstelle, die alle Aktualisierungshandler implementieren müssen
* `com.day.cq.contentsync.handler.AbstractSlingResourceUpdateHandler` - Eine abstrakte Klasse, die die Darstellung von Ressourcen mithilfe von Sling vereinfacht

Registrieren Sie Ihre Klasse als OSGi-Komponentenfabrik und stellen Sie sie im OSGi-Container in einem Bundle bereit. Dies kann mithilfe des [Maven SCR-Plugins](https://felix.apache.org/site/apache-felix-maven-scr-plugin.html) entweder mit JavaDoc-Tags oder mit Anmerkungen erfolgen. Das folgende Beispiel zeigt die JavaDoc-Version:

```java
/*
 * @scr.component metatype="no"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/customtype"
 */
public class CustomTypeUpdateHandler implements ContentUpdateHandler {
    // add your code here
}

/*
 * @scr.component metatype="no" inherit="true"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/othertype"
 */
public class OtherTypeUpdateHandler extends AbstractSlingResourceUpdateHandler {
    // add your code here
}
```

Beachten Sie, dass die *Factory* -Definition die allgemeine Schnittstelle und den benutzerdefinierten Typ, durch Schrägstrich getrennt, enthält. Mit dieser Strategie kann das Content Sync-Framework eine Instanz Ihrer benutzerdefinierten Klasse suchen und erstellen, da der benutzerdefinierte Typ in einem Konfigurationseintrag erkannt wird. Im nächsten Abschnitt finden Sie ein konkretes Beispiel eines benutzerdefinierten Aktualisierungshandlers.

>[!CAUTION]
>
>Beim Aufbau auf der AbstractSlingResourceUpdateHandler-Basisklasse müssen Sie die *inherit* -Definition hinzufügen. Andernfalls legt der OSGi-Container nicht die erforderlichen Verweise fest, die in der Basisklasse deklariert werden.

### Implementieren eines benutzerdefinierten Aktualisierungshandlers {#implementing-a-custom-update-handler}

Jede We.Retail Mobile Seite enthält ein Logo in der oberen linken Ecke, das wir natürlich in die ZIP-Datei aufnehmen möchten. Zur Cacheoptimierung verweist AEM jedoch nicht auf den tatsächlichen Speicherort der Bilddatei im Repository, was verhindert, dass wir einfach den Konfigurationstyp **copy** verwenden. Stattdessen müssen wir unseren eigenen **Logo** -Konfigurationstyp bereitstellen, der das Bild an dem von AEM angeforderten Speicherort verfügbar macht. Die folgende Codeauflistung zeigt die vollständige Implementierung des Logoupdate-Handlers:

#### LogoUpdateHandler.java {#logoupdatehandler-java}

```java
package com.day.cq.wcm.apps.weretail.impl;

import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.day.cq.commons.jcr.JcrUtil;
import com.day.cq.contentsync.config.ConfigEntry;
import com.day.cq.contentsync.handler.ContentUpdateHandler;
import com.day.cq.wcm.foundation.Image;
import com.day.text.Text;

/**
 * The <code>LogoUpdateHandler</code> is used to update the content sync cache
 * with a page logo added using a logo component.
 *
 * @scr.component metatype="no"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/logo"
 */
public class LogoUpdateHandler implements ContentUpdateHandler {

    private static final Logger log = LoggerFactory.getLogger(LogoUpdateHandler.class);

    /** @scr.reference policy="static" */
    protected JcrResourceResolverFactory resolverFactory;

    public boolean updateCacheEntry(ConfigEntry configEntry, Long lastUpdated, String configCacheRoot, Session admin, Session session) {
        ResourceResolver resolver = resolverFactory.getResourceResolver(admin);
        Resource resource = resolver.getResource(configEntry.getContentPath());

        Image img = new Image(resource);
        img.setItemName(Image.NN_FILE, "image");
        img.setItemName(Image.PN_REFERENCE, "imageReference");
        img.setSelector("img");

        try {
            if(img.getLastModified() == null || lastUpdated < img.getLastModified().getTime().getTime()) {
                String src = img.getSrc();
                String parentPath = configCacheRoot + Text.getRelativeParent(src, 1);

                Node parent = JcrUtil.createPath(parentPath, "sling:Folder", admin);
                Node image = resolver.getResource(resource.getPath() + "/image").adaptTo(Node.class);
                JcrUtil.copy(image, parent, Text.getName(src));

                admin.save();

                return true;
            }
        } catch (RepositoryException e) {
            log.error("Unexpected error while updating logo: ", e);
        }

        return false;
    }
}
```

Die `LogoUpdateHandler` Klasse implementiert die `ContentUpdateHandler` Methode der `updateCacheEntry(ConfigEntry, Long, String, Session, Session)` Schnittstelle, die eine Reihe von Argumenten akzeptiert:

* Eine `ConfigEntry` Instanz, die Zugriff auf den Konfigurationseintrag, für den dieser Handler aufgerufen wird, und seine Eigenschaften bietet.
* Ein `lastUpdated` Zeitstempel, der angibt, wann die Inhaltssynchronisierung ihren Cache zuletzt aktualisiert hat. Inhalte, die nach diesem Zeitstempel nicht geändert wurden, sollten vom Handler nicht aktualisiert werden.
* Ein `configCacheRoot` Argument, das den Stammpfad des Cache angibt. Alle aktualisierten Dateien müssen unter diesem Pfad gespeichert werden, um der ZIP-Datei hinzugefügt zu werden.
* Eine Verwaltungssitzung, die für alle Cache-bezogenen Repository-Vorgänge verwendet werden sollte.
* Eine Benutzersitzung, die dazu verwendet werden kann, Inhalte im Kontext eines bestimmten Benutzers zu aktualisieren und damit eine Art personalisierter Inhalte bereitzustellen.

Um den benutzerdefinierten Handler zu implementieren, erstellen Sie zunächst eine Instanz der Image-Klasse basierend auf der im Konfigurationseintrag angegebenen Ressource. Dies ist im Grunde das gleiche Verfahren wie die eigentliche Logo-Komponente auf unseren Seiten. Dadurch wird sichergestellt, dass der Zielpfad des Bildes mit dem Pfad einer Seite übereinstimmt, auf die verwiesen wird.

Überprüfen Sie dann, ob die Ressource seit der letzten Aktualisierung geändert wurde. Benutzerdefinierte Implementierungen sollten unnötige Aktualisierungen des Cache vermeiden und &quot;false&quot;zurückgeben, wenn sich nichts ändert. Wenn die Ressource geändert wurde, kopieren Sie das Bild in den erwarteten Zielort relativ zum Cache-Stammordner. Schließlich `true` wird zurückgegeben, um dem Framework anzuzeigen, dass der Cache aktualisiert wurde.

## Verwenden des Inhalts auf dem Client {#using-the-content-on-the-client}

Um Inhalte in einer mobilen App zu verwenden, die von Content Sync bereitgestellt wird, müssen Sie Inhalte über eine HTTP- oder HTTPS-Verbindung anfordern. Daher können abgerufene Inhalte (in einer ZIP-Datei verpackt) extrahiert und lokal auf dem Mobilgerät gespeichert werden. Beachten Sie, dass Inhalt nicht nur auf Daten, sondern auch auf Logik, d. h. vollständige Webanwendungen, verweist; Dadurch kann der Mobilbenutzer abgerufene Webanwendungen und zugehörige Daten auch ohne Netzwerkverbindung ausführen.

Die Inhaltssynchronisierung bietet Inhalte auf intelligente Weise: Es werden nur Datenänderungen seit der letzten erfolgreichen Datensynchronisierung bereitgestellt, wodurch die für die Datenübertragung erforderliche Zeit verringert wird. Beim ersten Ausführen einer Anwendung werden seit dem 1. Januar 1970 Datenänderungen angefordert, während anschließend nur Daten angefordert werden, die sich seit der letzten erfolgreichen Synchronisierung geändert haben. AEM nutzt ein Client-Kommunikationsframework für iOS, um die Datenkommunikation und -übertragung zu vereinfachen, sodass für die Aktivierung einer iOS-basierten Webanwendung eine Mindestmenge an nativem Code erforderlich ist.

Alle übertragenen Daten können in dieselbe Verzeichnisstruktur extrahiert werden. Es sind keine weiteren Schritte (z.B. Abhängigkeitsprüfungen) beim Extrahieren von Daten erforderlich. Bei iOS werden alle Daten in einem Unterordner im Ordner &quot;Dokumente&quot;der iOS-App gespeichert.

Typischer Ausführungspfad einer iOS-basierten AEM Mobile-App:

* Benutzer startet die App auf einem iOS-Gerät.
* App versucht, eine Verbindung zum AEM-Backend herzustellen und fordert Datenänderungen seit der letzten Ausführung an.
* Der Server ruft die fraglichen Daten ab und komprimiert sie in eine Datei.
* Daten werden an das Clientgerät zurückgegeben, wo sie in den Dokumentenordner extrahiert werden.
* Die UIWebView-Komponente wird gestartet/aktualisiert.

Wenn keine Verbindung hergestellt werden konnte, werden zuvor heruntergeladene Daten angezeigt.

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Autoren finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Authoring von AEM Content für AEM Mobile-On-Demand-Dienste](/help/mobile/mobile-apps-ondemand.md)
* [Verwalten von Inhalten für die Verwendung von AEM Mobile-On-Demand-Diensten](/help/mobile/aem-mobile.md)

