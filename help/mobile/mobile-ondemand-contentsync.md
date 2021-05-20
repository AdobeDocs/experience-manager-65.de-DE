---
title: Mobil mit Inhaltssynchronisierung
seo-title: Mobil mit Inhaltssynchronisierung
description: Auf dieser Seite erfahren Sie mehr über die Inhaltssynchronisierung. Seiten, die in AEM erstellt werden, können als App-Inhalt verwendet werden, selbst wenn das Gerät offline ist. Da AEM Seiten außerdem auf Webstandards basieren, funktionieren sie plattformübergreifend und ermöglichen es Ihnen, sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht es Ihnen, App-Inhalte einfach zu aktualisieren.
seo-description: Auf dieser Seite erfahren Sie mehr über die Inhaltssynchronisierung. Seiten, die in AEM erstellt werden, können als App-Inhalt verwendet werden, selbst wenn das Gerät offline ist. Da AEM Seiten außerdem auf Webstandards basieren, funktionieren sie plattformübergreifend und ermöglichen es Ihnen, sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht es Ihnen, App-Inhalte einfach zu aktualisieren.
uuid: 11f74cc5-99a5-4186-9b60-b19351305432
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 8fb70ca4-86fc-477d-9773-35b84d5e85a8
exl-id: a6e59334-09e2-4bb8-b445-1868035da556
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3057'
ht-degree: 2%

---

# Mobil mit Inhaltssynchronisierung{#mobile-with-content-sync}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Verwenden Sie die Inhaltssynchronisierung , um Inhalte zu verpacken, damit sie in nativen mobilen Anwendungen verwendet werden können. Seiten, die in AEM erstellt werden, können als App-Inhalt verwendet werden, selbst wenn das Gerät offline ist. Da AEM Seiten außerdem auf Webstandards basieren, funktionieren sie plattformübergreifend und ermöglichen es Ihnen, sie in jeden nativen Wrapper einzubetten. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht es Ihnen, App-Inhalte einfach zu aktualisieren.

Das Framework für die Inhaltssynchronisierung erstellt eine Archivdatei, die die Webinhalte enthält. Der Inhalt kann von einfachen Seiten, Bildern, PDF-Dateien oder ganzen Webanwendungen ausgehen. Die API zur Inhaltssynchronisierung bietet Zugriff auf die Archivdatei aus mobilen Apps oder Build-Prozessen, damit die Inhalte abgerufen und in die App eingefügt werden können.

Die folgende Schrittfolge zeigt einen typischen Anwendungsfall für die Inhaltssynchronisierung:

1. Der AEM-Entwickler erstellt eine Konfiguration zur Inhaltssynchronisierung, die den einzuschließenden Inhalt angibt.
1. Das Framework zur Inhaltssynchronisierung erfasst und speichert die Inhalte zwischen.
1. Auf einem Mobilgerät wird die Mobile App gestartet und fordert Inhalte vom Server an, der in einer ZIP-Datei bereitgestellt wird.
1. Der Client entpackt den ZIP-Inhalt in das lokale Dateisystem. Die Ordnerstruktur in der ZIP-Datei simuliert die Pfade, die ein Client (z. B. ein Browser) normalerweise vom Server anfordern würde.
1. Der Client öffnet den Inhalt in einem eingebetteten Browser oder verwendet ihn auf andere Weise.
1. Später fordert der Client aktualisierte Inhalte vom Server an. Das Framework zur Inhaltssynchronisierung bietet inkrementelle Updates, um die Download-Größe und -Zeit zu reduzieren, was für Mobilgeräte aufgrund begrenzter Bandbreite oder Datenvolumen wichtig sein kann.

## Entwickeln der Inhaltssynchronisierungs-Handler {#developing-the-content-sync-handlers}

Einige Richtlinien zur Entwicklung von Content Sync Handlern lauten wie folgt:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder erweitern Sie eine Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* erweitern.
* Handler dürfen nur &quot;true&quot;melden, wenn sie den ContentSync-Cache aktualisieren. Falsche Berichterstellung von &quot;true&quot;AEM eine Aktualisierung erstellen, wenn keine Aktualisierung stattgefunden hat.
* Der Handler sollte den Cache nur aktualisieren, wenn der Inhalt tatsächlich geändert wurde. Schreiben Sie nicht in den Cache, wenn kein Weiß erforderlich ist. Dadurch wird eine unnötige Aktualisierung erstellt.

>[!NOTE]
>
>Aktivieren Sie *ContentSync Debug Logging* über OSGI-Logger-Konfigurationen auf Paket *com.day.cq.contentsync*. Auf diese Weise können Sie verfolgen, welche Handler ausgeführt haben und ob sie den Cache aktualisiert und die Aktualisierung des Caches gemeldet haben.

## Konfigurieren des Inhalts-Synchronisierungsinhalts {#configuring-the-content-sync-content}

Erstellen Sie eine Konfiguration zur Inhaltssynchronisierung , um den Inhalt der ZIP-Datei anzugeben, die an den Client gesendet wird. Sie können beliebig viele Konfigurationen zur Inhaltssynchronisierung erstellen. Jede Konfiguration hat einen Namen zu Identifizierungszwecken.

Um eine Konfiguration für die Inhaltssynchronisierung zu erstellen, fügen Sie dem Repository einen Knoten `cq:ContentSyncConfig` hinzu, wobei die Eigenschaft `sling:resourceType` auf `contentsync/config` gesetzt ist. Der Knoten `cq:ContentSyncConfig` kann sich an einer beliebigen Stelle im Repository befinden. Der Knoten muss jedoch für Benutzer in der AEM Veröffentlichungsinstanz zugänglich sein. Daher sollten Sie den Knoten unter `/content` hinzufügen.

Um den Inhalt der ZIP-Datei für die Inhaltssynchronisierung anzugeben, fügen Sie dem Knoten cq:ContentSyncConfig untergeordnete Knoten hinzu. Die folgenden Eigenschaften jedes untergeordneten Knotens identifizieren ein einzuschließendes Inhaltselement und dessen Verarbeitung beim Hinzufügen:

* `path`: Der Speicherort des Inhalts.
* `type`: Der Name des Konfigurationstyps, der für die Verarbeitung des Inhalts verwendet werden soll. Verschiedene Typen sind verfügbar und werden im Abschnitt *Konfigurationstypen* beschrieben.

Weitere Informationen finden Sie unter *Beispiel für die Konfiguration der Inhaltssynchronisierung* .

Nachdem Sie die Konfiguration für die Inhaltssynchronisierung erstellt haben, wird sie in der Konsole &quot;Inhaltssynchronisierung&quot;angezeigt.

>[!NOTE]
>
>Das Framework für die Inhaltssynchronisierung prüft nicht, ob Abhängigkeiten von Assets und Entwurfsdateien in Inhaltssynchronisierungspaketen enthalten sind. Stellen Sie sicher, dass Sie alle erforderlichen Dateien in die ZIP-Datei aufnehmen.

### Konfigurieren des Zugriffs auf Downloads bei der Inhaltssynchronisierung {#configuring-access-to-content-sync-downloads}

Geben Sie einen Benutzer oder eine Gruppe an, die über die Inhaltssynchronisierung heruntergeladen werden können. Sie können den Standardbenutzer oder die Standardgruppe konfigurieren, die von allen Caches zur Inhaltssynchronisierung heruntergeladen werden können. Außerdem können Sie die Standardeinstellung überschreiben und den Zugriff für eine bestimmte Konfiguration zur Inhaltssynchronisierung konfigurieren.

Wenn AEM installiert ist, können Mitglieder der Administratorgruppe standardmäßig von der Inhaltssynchronisierung herunterladen.

#### Festlegen des Standardzugriffs für Downloads bei der Inhaltssynchronisierung {#setting-the-default-access-for-content-sync-downloads}

Der Day CQ Content Sync Manager-Dienst steuert den Zugriff auf die Inhaltssynchronisierung. Konfigurieren Sie diesen Dienst, um den Benutzer oder die Gruppe anzugeben, die standardmäßig von der Inhaltssynchronisierung heruntergeladen werden können.

Wenn Sie [den Dienst mit der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) konfigurieren, geben Sie den Namen des Benutzers oder der Gruppe als Wert der Eigenschaft &quot;Fallback Cache Authorizable&quot;ein.

Wenn Sie [im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) konfigurieren, verwenden Sie die folgenden Informationen zum Dienst:

* PID: com.day.cq.contentsync.impl.ContentSyncManagerImpl
* Eigenschaftsname: contentsync.fallback.authorizable

#### Überschreiben des Download-Zugriffs für einen Inhaltssynchronisierungs-Cache {#overriding-download-access-for-a-content-sync-cache}

Um den Download-Zugriff für eine bestimmte Konfiguration der Inhaltssynchronisierung zu konfigurieren, fügen Sie die folgende Eigenschaft zum Knoten `cq:ContentSyncConfig` hinzu:

* Name: authorizable
* Typ: String
* Wert: Der Name des Benutzers oder der Gruppe, den/die heruntergeladen werden kann.

Ihre App ermöglicht es Benutzern beispielsweise, Aktualisierungen direkt über die Inhaltssynchronisierung zu installieren. Damit alle Benutzer die Aktualisierung herunterladen können, legen Sie den Wert der Eigenschaft zum Autorisieren auf `everyone` fest.

Wenn der Knoten `cq:ContentSyncConfig` keine autorisierbare Eigenschaft aufweist, bestimmt der Standardbenutzer oder die Standardgruppe, der bzw. die für die Eigenschaft &quot;Fallback Cache Authorizable&quot;des Day CQ Content Sync Manager-Dienstes konfiguriert ist, wer herunterladen kann.

### Konfigurieren des Benutzers für die Aktualisierung eines Inhaltssynchronisierungscaches {#configuring-the-user-for-updating-a-content-sync-cache}

Wenn ein Benutzer eine Aktualisierung des Cache für die Inhaltssynchronisierung durchführt, führt ein bestimmtes Benutzerkonto die Aktion im Namen des Benutzers durch. Der anonyme Benutzer aktualisiert standardmäßig alle Caches der Inhaltssynchronisierung.

Sie können den Standardbenutzer überschreiben und einen Benutzer oder eine Gruppe angeben, der bzw. die einen bestimmten Cache zur Inhaltssynchronisierung aktualisiert.

Um den Standardbenutzer zu überschreiben, geben Sie einen Benutzer oder eine Gruppe an, der bzw. die Aktualisierungen für eine bestimmte Konfiguration der Inhaltssynchronisierung durchführt, indem Sie die folgende Eigenschaft zum Knoten cq:ContentSyncConfig hinzufügen:

* Name: `updateuser`
* Typ: `String`
* Wert: Der Name des Benutzers oder der Gruppe, der/die die Aktualisierungen durchführen kann.

Wenn der Knoten `cq:ContentSyncConfig` keine `updateuser` -Eigenschaft aufweist, aktualisiert der Standardbenutzer `anonymous` den Cache.

### Konfigurationstypen {#configuration-types}

Die Verarbeitung kann von der Darstellung einfacher JSON bis zur vollständigen Darstellung von Seiten einschließlich der referenzierten Assets reichen. In diesem Abschnitt werden die verfügbaren Konfigurationstypen und ihre spezifischen Parameter aufgelistet:

**** copyKopieren Sie einfach Dateien und Ordner.

* **path**  - Wenn der Pfad auf eine einzelne Datei verweist, wird nur die Datei kopiert. Wenn er auf einen Ordner verweist (dies schließt Seitenknoten ein), werden alle unten aufgeführten Dateien und Ordner kopiert.

**** contentRender-Inhalt mit standardmäßiger  [Sling-Anforderungsverarbeitung](/help/sites-developing/the-basics.md#sling-request-processing).

* **path**  - Pfad zur Ressource, die ausgegeben werden soll.
* **extension**  - Erweiterung, die in der Anfrage verwendet werden soll. Häufige Beispiele sind *html* und *json*, aber jede andere Erweiterung ist möglich.

* **selector**  - Optionale Selektoren, getrennt durch Punkte. Häufige Beispiele sind *touch* zum Rendern mobiler Versionen einer Seite oder *infinity* für die JSON-Ausgabe.

**** clientlibPacken Sie eine JavaScript- oder CSS-Client-Bibliothek.

* **path**  - Pfad zum Stamm der Client-Bibliothek.
* **extension**  - Typ der Client-Bibliothek. Dies sollte derzeit entweder auf *js* oder *css* gesetzt werden.

**Assets**

Erfassen Sie Original-Ausgabeformate von Assets.

* **path**  - Pfad zu einem Asset-Ordner unter /content/dam.

**** imageCollect a image.

* **path**  - Pfad zu einer Bildressource.

Der Bildtyp wird verwendet, um das We Retail-Logo in die ZIP-Datei einzuschließen.

**** pagesRendern AEM Seiten und Erfassen referenzierter Assets.

* **path**  - Pfad zu einer Seite.
* **extension**  - Erweiterung, die in der Anfrage verwendet werden soll. Für Seiten ist dies fast immer *html*, aber andere sind noch möglich.

* **selector**  - Optionale Selektoren, getrennt durch Punkte. Häufige Beispiele sind *touch* zum Rendern mobiler Versionen einer Seite.

* **deep**  - Optionale boolesche Eigenschaft, die bestimmt, ob auch untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* **includeImages**  - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

   Standardmäßig werden nur Bildkomponenten mit dem Ressourcentyp foundation/components/image zur Aufnahme berücksichtigt. Sie können weitere Ressourcentypen hinzufügen, indem Sie den **Day CQ WCM Pages Update Handler** in der Web-Konsole konfigurieren.

**** rewriteDer rewrite-Knoten definiert, wie die Links auf der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Der Knoten `rewrite` muss sich unter dem Knoten `page` befinden.

Der Knoten `rewrite` kann eine oder mehrere der folgenden Eigenschaften aufweisen:

* `clientlibs`: schreibt clientlibs-Pfade neu.

* `images`: schreibt Bildpfade neu.
* `links`: schreibt Verknüpfungspfade neu.

Jede Eigenschaft kann einen der folgenden Werte aufweisen:

* `REWRITE_RELATIVE`: schreibt den Pfad mit einer relativen Position zur .html-Datei der Seite im Dateisystem neu.

* `REWRITE_EXTERNAL`: schreibt den Pfad neu, indem er mithilfe des AEM  [Externalizer-Dienstes](/help/sites-developing/externalizer.md) auf die Ressource auf dem Server verweist.

Mit dem AEM-Dienst **PathRewriterTransformerFactory** können Sie die spezifischen HTML-Attribute konfigurieren, die umgeschrieben werden. Der Dienst kann in der Webkonsole konfiguriert werden und verfügt über eine Konfiguration für jede Eigenschaft des Knotens `rewrite` : `clientlibs`, `images` und `links`.

Diese Funktion wurde in AEM 5.5 hinzugefügt.

### Beispiel für Konfiguration der Inhaltssynchronisierung {#example-content-sync-configuration}

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

**etc.designs.default und etc.designs.** mobileDie ersten beiden Einträge der Konfiguration sollten ziemlich offensichtlich sein. Da wir einige mobile Seiten einschließen werden, benötigen wir die entsprechenden Designdateien unter /etc/designs. Da keine zusätzliche Verarbeitung erforderlich ist, reicht die Kopie aus.

**events.** plistDieser Eintrag ist ein wenig spezifisch. Wie in der Einführung erwähnt, sollte die Anwendung eine Kartenansicht mit Markierungen der Orte der Ereignisse bereitstellen. Wir werden die erforderlichen Standortinformationen als separate Datei im PLIST-Format bereitstellen. Damit dies funktioniert, verfügt die Ereignislistenkomponente, die auf der Indexseite verwendet wird, über ein Skript namens plist.jsp. Dieses Skript wird ausgeführt, wenn die Ressource der Komponente mit der Erweiterung .plist angefordert wird. Wie üblich wird der Komponentenpfad in der Pfadeigenschaft angegeben und der Typ ist auf &quot;content&quot;festgelegt, da wir die [Verarbeitung von Sling-Anforderungen](/help/sites-developing/the-basics.md#sling-request-processing) nutzen möchten.

**events.touch.** htmlNext enthält die tatsächlichen Seiten, die in der App angezeigt werden. Die Pfadeigenschaft wird auf die Stammseite der Ereignisse festgelegt. Alle Ereignisseiten unterhalb dieser Seite werden ebenfalls einbezogen, da die Deep-Eigenschaft standardmäßig auf &quot;true&quot;festgelegt ist. Wir verwenden Seiten als Konfigurationstyp, sodass alle Bilder oder andere Dateien, die von einem Bild oder einer Download-Komponente auf einer Seite referenziert werden können, einbezogen werden. Darüber hinaus erhalten Sie durch Festlegen des Touch-Selektors eine mobile Version der Seiten. Die Konfiguration im Feature Pack enthält weitere Einträge dieser Art, aber sie werden hier aus Gründen der Einfachheit nicht berücksichtigt.

**** logoDer Konfigurationstyp des Logos wurde bisher nicht erwähnt und ist keiner der integrierten Typen. Das Framework zur Inhaltssynchronisierung ist jedoch in gewissem Umfang erweiterbar. Dies ist ein Beispiel dafür, das im nächsten Abschnitt behandelt wird.

**** manifestEs ist oft wünschenswert, in die ZIP-Datei Metadaten wie beispielsweise die Startseite Ihres Inhalts aufzunehmen. Die Hartkodierung solcher Informationen verhindert jedoch, dass Sie sie später einfach ändern können. Das Framework für die Inhaltssynchronisierung unterstützt diesen Anwendungsfall, indem es nach einem Manifestknoten in der Konfiguration sucht, der einfach anhand des Namens identifiziert wird und keinen Konfigurationstyp erfordert. Jede auf diesem bestimmten Knoten definierte Eigenschaft wird einer Datei hinzugefügt, die auch &quot;manifest&quot;genannt wird und sich im Stammverzeichnis der ZIP-Datei befindet.

Im Beispiel soll die Ereignisauflistungsseite die ursprüngliche Seite sein. Diese Informationen werden in der Eigenschaft **indexPage** bereitgestellt und können daher jederzeit problemlos geändert werden. Eine zweite Eigenschaft definiert den Pfad der Datei *events.plist* . Wie wir später sehen werden, kann die Client-Anwendung jetzt das Manifest lesen und entsprechend handeln.

Sobald die Konfiguration eingerichtet ist, kann der Inhalt mit einem Browser oder einem anderen HTTP-Client heruntergeladen werden. Wenn Sie für iOS entwickeln, können Sie die dedizierte WAppKitSync-Client-Bibliothek verwenden. Der Download-Speicherort besteht aus dem Pfad der Konfiguration und der Erweiterung *.zip*, z. B. beim Arbeiten mit einer lokalen AEM-Instanz: *http://localhost:4502/content/weretail_go.zip*

### Die Content Sync-Konsole {#the-content-sync-console}

Die Konsole &quot;Inhaltssynchronisierung&quot;listet alle Konfigurationen der Inhaltssynchronisierung im Repository auf (alle Knoten des Typs `cq:ContentSyncConfig`) und ermöglicht Ihnen für jede Konfiguration Folgendes:

* Aktualisieren Sie den Cache.
* Löschen Sie den Cache.
* Laden Sie eine vollständige ZIP-Datei herunter.
* Laden Sie zwischen jetzt und einem bestimmten Datum und einer bestimmten Uhrzeit eine Vergleichstabelle herunter.

Es kann für die Entwicklung und Fehlerbehebung nützlich sein.

Auf die Konsole kann unter folgender Adresse zugegriffen werden:

`http://localhost:4502/libs/cq/contentsync/content/console.html`

Diese sieht nun wie folgt aus:

![chlimage_1-50](assets/chlimage_1-50.png)

### Erweitern des Content Sync-Frameworks {#extending-the-content-sync-framework}

Obwohl die Anzahl der Konfigurationsoptionen bereits sehr umfangreich ist, deckt sie möglicherweise nicht alle Anforderungen Ihres spezifischen Anwendungsfalls ab. In diesem Abschnitt werden die Erweiterungspunkte des Content Sync-Frameworks und die Erstellung benutzerdefinierter Konfigurationstypen beschrieben.

Für jeden Konfigurationstyp gibt es einen *Content Update Handler*, bei dem es sich um eine OSGi-Komponentenfactory handelt, die für diesen bestimmten Typ registriert ist. Diese Handler erfassen Inhalte, verarbeiten sie und fügen sie einem Cache hinzu, der vom Content Sync-Framework verwaltet wird. Implementieren Sie die folgende Schnittstelle oder abstrakte Basisklasse:

* `com.day.cq.contentsync.handler.ContentUpdateHandler` - Schnittstelle, die alle Update-Handler implementieren müssen
* `com.day.cq.contentsync.handler.AbstractSlingResourceUpdateHandler` - Eine abstrakte Klasse, die das Rendering von Ressourcen mithilfe von Sling vereinfacht

Registrieren Sie Ihre Klasse als OSGi-Komponentenfabrik und stellen Sie sie im OSGi-Container in einem Bundle bereit. Dies kann mithilfe des [Maven SCR-Plug-ins](https://felix.apache.org/site/apache-felix-maven-scr-plugin.html) entweder mit JavaDoc-Tags oder Anmerkungen erfolgen. Das folgende Beispiel zeigt die JavaDoc-Version:

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

Beachten Sie, dass die Definition *factory* die gemeinsame Schnittstelle und den benutzerdefinierten Typ enthält, getrennt durch Schrägstrich. Diese Strategie ermöglicht es dem Framework für die Inhaltssynchronisierung, eine Instanz Ihrer benutzerdefinierten Klasse zu finden und zu erstellen, da sie den benutzerdefinierten Typ in einem Konfigurationseintrag erkennt. Im nächsten Abschnitt finden Sie ein konkretes Beispiel für einen benutzerdefinierten Update-Handler.

>[!CAUTION]
>
>Beim Erstellen auf der Basis der AbstractSlingResourceUpdateHandler-Basisklasse müssen Sie die *inherit*-Definition hinzufügen. Andernfalls legt der OSGi-Container nicht die erforderlichen Verweise fest, die in der Basisklasse deklariert sind.

### Implementieren eines benutzerdefinierten Update-Handlers {#implementing-a-custom-update-handler}

Jede We.Retail Mobile-Seite enthält ein Logo in der oberen linken Ecke, das wir natürlich in die ZIP-Datei aufnehmen möchten. Zur Cache-Optimierung verweist AEM jedoch nicht auf den tatsächlichen Speicherort der Bilddatei im Repository, was verhindert, dass wir einfach den Konfigurationstyp **copy** verwenden. Stattdessen müssen wir unseren eigenen Konfigurationstyp **logo** bereitstellen, der das Bild an dem von AEM angeforderten Speicherort verfügbar macht. Die folgende Codeauflistung zeigt die vollständige Implementierung des Logupdate-Handlers:

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

Die `LogoUpdateHandler`-Klasse implementiert die `ContentUpdateHandler`-Methode der `updateCacheEntry(ConfigEntry, Long, String, Session, Session)`-Schnittstelle, die eine Reihe von Argumenten akzeptiert:

* Eine `ConfigEntry`-Instanz, die Zugriff auf den Konfigurationseintrag, für den dieser Handler aufgerufen wird, und seine Eigenschaften bietet.
* Ein `lastUpdated`-Zeitstempel, der angibt, wann die Inhaltssynchronisierung den Cache zuletzt aktualisiert hat. Inhalte, die nach diesem Zeitstempel nicht geändert wurden, sollten vom Handler nicht aktualisiert werden.
* Ein `configCacheRoot`-Argument, das den Stammpfad des Caches angibt. Alle aktualisierten Dateien müssen unter diesem Pfad gespeichert werden, damit sie der ZIP-Datei hinzugefügt werden können.
* Eine Verwaltungssitzung, die für alle zwischenspeicherbezogenen Repository-Vorgänge verwendet werden soll.
* Eine Benutzersitzung, mit der Inhalte im Kontext eines bestimmten Benutzers aktualisiert und so personalisierte Inhalte bereitgestellt werden können.

Um den benutzerdefinierten Handler zu implementieren, erstellen Sie zunächst eine Instanz der Image-Klasse basierend auf der im Konfigurationseintrag angegebenen Ressource. Dies ist im Wesentlichen das gleiche Verfahren wie die eigentliche logo-Komponente auf unseren Seiten. Dadurch wird sichergestellt, dass der Zielpfad des Bildes mit dem Pfad übereinstimmt, auf den von einer Seite aus verwiesen wird.

Überprüfen Sie anschließend, ob die Ressource seit der letzten Aktualisierung geändert wurde. Benutzerdefinierte Implementierungen sollten unnötige Aktualisierungen des Caches vermeiden und &quot;false&quot;zurückgeben, wenn sich nichts ändert. Wenn die Ressource geändert wurde, kopieren Sie das Bild in den erwarteten Zielspeicherort relativ zum Cache-Stammverzeichnis. Schließlich wird `true` zurückgegeben, um dem Framework anzuzeigen, dass der Cache aktualisiert wurde.

## Verwenden des Inhalts auf dem Client {#using-the-content-on-the-client}

Um Inhalte in einer von der Inhaltssynchronisierung bereitgestellten mobilen App verwenden zu können, müssen Sie Inhalte über eine HTTP- oder HTTPS-Verbindung anfordern. Daher können abgerufene Inhalte (in einer ZIP-Datei verpackt) lokal auf dem Mobilgerät extrahiert und gespeichert werden. Beachten Sie, dass Inhalt sich nicht nur auf Daten, sondern auch auf Logik bezieht, d. h. auf vollständige Webanwendungen; Dadurch kann der mobile Benutzer abgerufene Webanwendungen und entsprechende Daten auch ohne Netzwerkverbindung ausführen.

Die Inhaltssynchronisierung liefert Inhalte auf intelligente Weise: Es werden nur Datenänderungen seit der letzten erfolgreichen Datensynchronisation bereitgestellt, wodurch die für die Datenübertragung erforderliche Zeit verkürzt wird. Bei der ersten Ausführung einer Anwendung werden seit dem 1. Januar 1970 Datenänderungen angefordert, während anschließend nur Daten angefordert werden, die sich seit der letzten erfolgreichen Synchronisation geändert haben. AEM verwendet ein Client-Kommunikationsframework für iOS, um die Datenkommunikation und -übertragung zu vereinfachen, sodass für die Aktivierung einer iOS-basierten Webanwendung nur ein minimaler systemeigener Code erforderlich ist.

Alle übertragenen Daten können in dieselbe Verzeichnisstruktur extrahiert werden. Beim Extrahieren von Daten sind keine zusätzlichen Schritte (z. B. Abhängigkeitsprüfungen) erforderlich. Bei iOS werden alle Daten in einem Unterordner im Ordner &quot;Dokumente&quot;der iOS-App gespeichert.

Typischer Ausführungspfad einer iOS-basierten AEM Mobile-App:

* Benutzer startet die App auf iOS-Geräten.
* Das Programm versucht, eine Verbindung zum AEM-Backend herzustellen und fordert seit der letzten Ausführung Datenänderungen an.
* Der Server ruft die betreffenden Daten ab und komprimiert sie in eine Datei.
* Daten werden an das Client-Gerät zurückgegeben, auf dem sie in den Ordner &quot;Dokumente&quot;extrahiert werden.
* Die UIWebView-Komponente wird gestartet/aktualisiert.

Wenn keine Verbindung hergestellt werden konnte, werden zuvor heruntergeladene Daten angezeigt.

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten eines Administrators und eines Autors finden Sie in den folgenden Ressourcen:

* [Inhaltserstellung AEM AEM Mobile On-demand Services](/help/mobile/mobile-apps-ondemand.md)
* [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)
