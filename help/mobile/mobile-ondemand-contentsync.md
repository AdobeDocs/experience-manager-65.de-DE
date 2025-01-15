---
title: Mobile mit Inhaltssynchronisierung
description: Auf dieser Seite erfahren Sie mehr über die Inhaltssynchronisierung. In Adobe Experience Manager (AEM) erstellte Seiten können als App-Inhalte verwendet werden, auch wenn das Gerät offline ist. Da AEM-Seiten auf Web-Standards basieren, funktionieren sie außerdem plattformübergreifend, sodass Sie sie in jeden nativen Wrapper einbetten können. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht es Ihnen, App-Inhalte einfach zu aktualisieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: a6e59334-09e2-4bb8-b445-1868035da556
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '2950'
ht-degree: 1%

---

# Mobile mit Inhaltssynchronisierung{#mobile-with-content-sync}

{{ue-over-mobile}}

Verwenden Sie die Inhaltssynchronisierung, um Inhalte zu verpacken, damit sie in nativen Mobile Apps verwendet werden können. In Adobe Experience Manager (AEM) erstellte Seiten können als App-Inhalte verwendet werden, auch wenn das Gerät offline ist. Da AEM-Seiten auf Web-Standards basieren, funktionieren sie außerdem plattformübergreifend, sodass Sie sie in jeden nativen Wrapper einbetten können. Diese Strategie reduziert den Entwicklungsaufwand und ermöglicht es Ihnen, App-Inhalte einfach zu aktualisieren.

Das Inhaltssynchronisierungs-Framework erstellt eine Archivdatei, die den Web-Inhalt enthält. Bei den Inhalten kann es sich um einfache Seiten, Bilder und PDF-Dateien oder ganze Web-Anwendungen handeln. Die Content Sync-API bietet Zugriff auf die Archivdatei von Mobile Apps oder Build-Prozessen, damit der Inhalt abgerufen und in die App eingefügt werden kann.

Die folgende Sequenz von Schritten zeigt einen typischen Anwendungsfall für die Inhaltssynchronisierung:

1. Der AEM-Entwickler erstellt eine Inhaltssynchronisierungskonfiguration, die den einzuschließenden Inhalt angibt.
1. Das Inhaltssynchronisierungs-Framework erfasst und speichert den Inhalt zwischen.
1. Auf einem Mobilgerät wird die Mobile App gestartet und fordert Inhalte vom Server an, die in einer ZIP-Datei bereitgestellt werden.
1. Der Client entpackt den ZIP-Inhalt in das lokale Dateisystem. Die Ordnerstruktur in der ZIP-Datei simuliert die Pfade, die ein Client (z. B. ein Browser) normalerweise vom Server anfordern würde.
1. Der Client öffnet den Inhalt in einem eingebetteten Browser oder verwendet ihn auf andere Weise.
1. Später fordert der Client aktualisierte Inhalte vom Server an. Das Inhaltssynchronisierungs-Framework bietet inkrementelle Aktualisierungen, um die Download-Größe und -Zeit zu reduzieren. Dies kann aufgrund der begrenzten Bandbreite oder des begrenzten Datenvolumens für Mobilgeräte wichtig sein.

## Entwickeln der Inhaltssynchronisierungs-Handler {#developing-the-content-sync-handlers}

Einige der Richtlinien für die Entwicklung von Inhaltssynchronisierungs-Handlern lauten wie folgt:

* Handler müssen *com.day.cq.contentsync.handler.ContentUpdateHandler* implementieren (entweder direkt oder durch Erweiterung einer Klasse, die dies tut)
* Handler können *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler erweitern*
* Handler dürfen nur dann „true“ melden, wenn sie den ContentSync-Cache aktualisieren. Wenn „true“ fälschlicherweise gemeldet wird, erstellt AEM eine Aktualisierung, obwohl keine Aktualisierung stattgefunden hat.
* Handler sollten den Cache nur aktualisieren, wenn der Inhalt geändert wurde. Schreiben Sie nicht in den Cache, wenn kein Leerzeichen erforderlich ist. Dies führt dazu, dass ein unnötiges Update erstellt wird.

>[!NOTE]
>
>Aktivieren Sie *ContentSync Debug-Protokollierung* über OSGi-Logger-Konfigurationen für Paket *com.day.cq.contentsync*. Auf diese Weise können Sie verfolgen, welche Handler ausgeführt haben, ob sie den Cache aktualisiert und die Aktualisierung des Caches gemeldet haben.

## Konfigurieren des Inhaltssynchronisierungsinhalts {#configuring-the-content-sync-content}

Erstellen Sie eine Content-Sync-Konfiguration, um den Inhalt der ZIP-Datei anzugeben, die an den Client gesendet wird. Sie können eine beliebige Anzahl von Inhaltssynchronisierungskonfigurationen erstellen. Jede Konfiguration verfügt über einen Namen zu Identifizierungszwecken.

Um eine Inhaltssynchronisierungskonfiguration zu erstellen, fügen Sie dem Repository einen `cq:ContentSyncConfig` Knoten hinzu, wobei die `sling:resourceType` Eigenschaft auf `contentsync/config` festgelegt ist. Der `cq:ContentSyncConfig` Knoten kann sich an einer beliebigen Stelle im Repository befinden, der Knoten muss jedoch für Benutzende in der AEM-Veröffentlichungsinstanz zugänglich sein. Daher sollten Sie den Knoten unter `/content` hinzufügen.

Um den Inhalt der ZIP-Datei für die Inhaltssynchronisierung anzugeben, fügen Sie dem Knoten cq:ContentSyncConfig untergeordnete Knoten hinzu. Die folgenden Eigenschaften jedes untergeordneten Knotens identifizieren ein einzuschließendes Inhaltselement und dessen Verarbeitung beim Hinzufügen:

* `path`: Der Speicherort des Inhalts.
* `type`: Der Name des Konfigurationstyps, der für die Verarbeitung des Inhalts verwendet werden soll. Es stehen verschiedene Typen zur Verfügung, die im Abschnitt *Konfigurationstypen“* werden.

Weitere Informationen finden *unter* für die Inhaltssynchronisierung .

Nachdem Sie die Konfiguration für die Inhaltssynchronisierung erstellt haben, wird sie in der Konsole für die Inhaltssynchronisierung angezeigt.

>[!NOTE]
>
>Das Inhaltssynchronisierungs-Framework überprüft nicht, ob Abhängigkeiten von Assets und designbezogene Dateien in Inhaltssynchronisierungspaketen enthalten sind. Stellen Sie sicher, dass Sie alle erforderlichen Dateien in die ZIP-Datei einschließen.

### Konfigurieren des Zugriffs auf Downloads der Inhaltssynchronisierung {#configuring-access-to-content-sync-downloads}

Geben Sie einen Benutzer oder eine Gruppe an, der bzw. die von der Inhaltssynchronisierung herunterladen kann. Sie können den Standardbenutzer oder die Standardgruppe konfigurieren, die aus allen Content Sync-Caches heruntergeladen werden kann. Außerdem können Sie den Standardzugriff überschreiben und den Zugriff für eine bestimmte Content Sync-Konfiguration konfigurieren.

Wenn AEM installiert ist, können Mitglieder der Administratorgruppe standardmäßig von der Inhaltssynchronisierung herunterladen.

#### Festlegen des Standardzugriffs für Downloads von Inhaltssynchronisierungen {#setting-the-default-access-for-content-sync-downloads}

Der Day CQ Content Sync Manager-Service steuert den Zugriff auf die Inhaltssynchronisierung. Konfigurieren Sie diesen Dienst, um den Benutzer oder die Gruppe anzugeben, der bzw. die standardmäßig von der Inhaltssynchronisierung herunterladen kann.

Wenn Sie [den Dienst mithilfe der Web-Konsole konfigurieren](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) geben Sie den Namen des Benutzers oder der Gruppe als Wert der autorisierbaren Fallback-Cache-Eigenschaft ein.

Wenn Sie [im Repository konfigurieren](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) verwenden Sie die folgenden Informationen zum Service:

* PID: com.day.cq.contentsync.impl.ContentSyncManagerImpl
* Eigenschaftsname: contentSync.fallback.authorizable

#### Überschreiben des Download-Zugriffs für einen Inhaltssynchronisierungs-Cache {#overriding-download-access-for-a-content-sync-cache}

Um den Downloadzugriff für eine bestimmte Inhaltssynchronisierungskonfiguration zu konfigurieren, fügen Sie die folgende Eigenschaft zum `cq:ContentSyncConfig` hinzu:

* Name: authorizable
* Typ: String
* Wert: Der Name des Benutzers oder der Gruppe, der bzw. die den Download durchführen kann.

Beispielsweise ermöglicht es Ihre App Benutzern, Updates direkt über die Inhaltssynchronisierung zu installieren. Damit alle Benutzer die Aktualisierung herunterladen können, legen Sie den Wert der Authorizable-Eigenschaft auf `everyone` fest.

Wenn der `cq:ContentSyncConfig` Knoten keine autorisierbare Eigenschaft hat, bestimmt der Standardbenutzer oder die Standardgruppe, die für die autorisierbare Eigenschaft des Day CQ Content Sync Manager-Dienstes konfiguriert ist, wer herunterladen kann.

### Konfigurieren des Benutzers für die Aktualisierung eines Inhaltssynchronisierungs-Cache {#configuring-the-user-for-updating-a-content-sync-cache}

Wenn ein(e) Benutzende(r) eine Aktualisierung des Inhaltssynchronisierungs-Caches durchführt, wird die Aktion von einem bestimmten Benutzerkonto im Namen des/r Benutzenden ausgeführt. Der anonyme Benutzer aktualisiert standardmäßig alle Content Sync-Caches.

Sie können den Standardbenutzer überschreiben und einen Benutzer oder eine Gruppe angeben, die einen bestimmten Inhaltssynchronisierungs-Cache aktualisiert.

Um den Standardbenutzer zu überschreiben, geben Sie einen Benutzer oder eine Gruppe an, die Aktualisierungen für eine bestimmte Inhaltssynchronisierungskonfiguration durchführt, indem Sie die folgende Eigenschaft zum Knoten cq:ContentSyncConfig hinzufügen:

* Name: `updateuser`
* Typ: `String`
* Wert: Der Name des Benutzers oder der Gruppe, der bzw. die die Aktualisierungen durchführen kann.

Wenn der `cq:ContentSyncConfig` keine `updateuser` hat, aktualisiert der `anonymous` den Cache.

### Konfigurationstypen {#configuration-types}

Die Verarbeitung kann vom Rendern einfacher JSON-Dateien bis zum vollständigen Rendern von Seiten einschließlich ihrer referenzierten Assets reichen. In diesem Abschnitt werden die verfügbaren Konfigurationstypen und ihre spezifischen Parameter aufgeführt:

**copy** - Dateien und Ordner kopieren.

* **path** - Wenn der Pfad auf eine einzelne Datei verweist, wird nur die Datei kopiert. Wenn er auf einen Ordner verweist (dies umfasst Seitenknoten), werden alle Dateien und Ordner unter kopiert.

**content** Rendern von Inhalten mit der standardmäßigen [Sling-Anfrageverarbeitung](/help/sites-developing/the-basics.md#sling-request-processing).

* **path** - Pfad zur Ressource, die ausgegeben werden soll.
* **extension** - Erweiterung, die in der Anfrage verwendet werden soll. Häufige Beispiele sind *html* und *json*, aber jede andere Erweiterung ist möglich.

* **selector** - Optionale Selektoren, durch einen Punkt getrennt. Häufige Beispiele sind *Touch* für das Rendern mobiler Versionen einer Seite oder *Infinity* für die JSON-Ausgabe.

**clientlib**: Verpacken Sie eine JavaScript- oder CSS-Client-Bibliothek.

* **path** - Pfad zum Stamm der Client-Bibliothek.
* **extension** - Typ der Client-Bibliothek. Dieser sollte derzeit entweder auf *js* oder *css* gesetzt werden.

**Assets**

Erfassen von Original-Ausgabedarstellungen von Assets.

* **path** - Pfad zu einem Asset-Ordner unter /content/dam.

**image** - Erfassen Sie ein Bild.

* **path** - Pfad zu einer Bildressource.

Der Bildtyp wird verwendet, um das We.Retail-Logo in die ZIP-Datei aufzunehmen.

**pages** - Rendern von AEM-Seiten und Erfassen referenzierter Assets.

* **path** - Pfad zu einer Seite.
* **extension** - Erweiterung, die in der Anfrage verwendet werden soll. Bei Seiten ist dies fast immer *HTML*, aber andere sind immer noch möglich.

* **selector** - Optionale Selektoren, durch einen Punkt getrennt. Häufige Beispiele sind *Touch* für das Rendern mobiler Versionen einer Seite.

* **deep** - Optionale boolesche Eigenschaft, die bestimmt, ob auch untergeordnete Seiten einbezogen werden sollen. Der Standardwert lautet *true.*

* **includeImages** - Optionale boolesche Eigenschaft, die bestimmt, ob Bilder einbezogen werden sollen. Der Standardwert lautet *true*.

  Standardmäßig werden nur Bildkomponenten mit dem Ressourcentyp „foundation/components/image“ für die Aufnahme berücksichtigt. Sie können weitere Ressourcentypen hinzufügen, indem Sie den **Day CQ WCM Pages Update Handler** in der Web-Konsole konfigurieren.

**rewrite** - Der Knoten rewrite definiert, wie die Links in der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Der `rewrite` Knoten muss sich unter dem `page` Knoten befinden.

Der `rewrite` kann eine oder mehrere der folgenden Eigenschaften aufweisen:

* `clientlibs`: schreibt Clientlibs-Pfade neu.

* `images`: schreibt Bildpfade neu.
* `links`: schreibt Link-Pfade neu.

Jede Eigenschaft kann einen der folgenden Werte aufweisen:

* `REWRITE_RELATIVE`: Schreibt den Pfad mit einer relativen Position zur HTML-Datei der Seite im Dateisystem neu.

* `REWRITE_EXTERNAL`: schreibt den Pfad neu, indem er auf die Ressource auf dem Server verweist, indem er den AEM-[Externalizer-Service) ](/help/sites-developing/externalizer.md).

Mit dem AEM-Dienst **PathRewriterTransformerFactory** können Sie bestimmte HTML-Attribute konfigurieren, die neu geschrieben werden. Der Dienst kann in der Web-Konsole konfiguriert werden und verfügt über eine Konfiguration für jede Eigenschaft des `rewrite`: `clientlibs`, `images` und `links`.

Diese Funktion wurde in AEM 5.5 hinzugefügt.

### Beispielhafte Konfiguration der Inhaltssynchronisierung {#example-content-sync-configuration}

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

**etc.designs.default und etc.designs.mobile** - Die ersten beiden Einträge der Konfiguration sind offensichtlich. Da Sie mehrere mobile Seiten einbinden werden, benötigen Sie die zugehörigen Design-Dateien unter /etc/designs. Und da keine zusätzliche Verarbeitung erforderlich ist, reicht eine Kopie aus.

**events.plist** - Dieser Eintrag ist etwas Besonderes. Wie in der Einführung erwähnt, sollte die Anwendung eine Kartenansicht mit Markierungen der Orte der Ereignisse bereitstellen. Die erforderlichen Ortsinformationen werden als separate Datei im PLIST-Format bereitgestellt. Dazu verfügt die Ereignislisten-Komponente, die auf der Indexseite verwendet wird, über ein Skript namens plist.jsp. Dieses Skript wird ausgeführt, wenn die Ressource der Komponente mit der `.plist` angefordert wird. Wie üblich wird der Komponentenpfad in der Pfadeigenschaft angegeben und der Typ ist auf „Inhalt“ festgelegt, da Sie die [Sling-Anfrageverarbeitung) verwenden ](/help/sites-developing/the-basics.md#sling-request-processing).

**events.touch.html** - Als Nächstes kommen die tatsächlichen Seiten, die in der App angezeigt werden. Die Pfadeigenschaft wird auf die Stammseite der Ereignisse festgelegt. Alle Ereignisseiten unterhalb dieser Seite werden ebenfalls eingeschlossen, da die Deep-Eigenschaft standardmäßig auf „true“ festgelegt ist. Sie verwenden Seiten als Konfigurationstyp, damit alle Bilder oder anderen Dateien, auf die von einer Bild- oder Download-Komponente auf einer Seite verwiesen wird, einbezogen werden. Darüber hinaus erhalten wir durch Festlegen des Touch-Selektors eine mobile Version der Seiten. Die Konfiguration im Feature Pack enthält weitere Einträge dieser Art, die hier jedoch der Einfachheit halber weggelassen werden.

**logo** - Der Konfigurationstyp des Logos wurde noch nicht erwähnt und ist keiner der integrierten Typen. Das Inhaltssynchronisierungs-Framework ist jedoch bis zu einem gewissen Grad erweiterbar. Dies ist ein Beispiel dafür, das im nächsten Abschnitt behandelt wird.

**manifest** - Es ist oft wünschenswert, dass eine Art von Metadaten in der ZIP-Datei enthalten ist, wie z. B. die Startseite Ihres Inhalts. Eine Hartkodierung solcher Informationen verhindert jedoch, dass Sie sie später einfach ändern können. Das Inhaltssynchronisierungs-Framework unterstützt diesen Anwendungsfall, indem in der Konfiguration nach einem Manifestknoten gesucht wird, der anhand des Namens identifiziert wird und keinen Konfigurationstyp erfordert. Jede Eigenschaft, die für diesen bestimmten Knoten definiert ist, wird einer Datei hinzugefügt, die auch als Manifest bezeichnet wird und sich im Stammverzeichnis der ZIP-Datei befindet.

Im Beispiel sollte die Ereignisauflistungsseite die Anfangsseite sein. Diese Informationen werden in der Eigenschaft **indexPage** bereitgestellt und können daher jederzeit einfach geändert werden. Eine zweite Eigenschaft definiert den Pfad der Datei *events.plist*. Wie Sie später sehen, kann die Client-Anwendung jetzt das Manifest lesen und entsprechend handeln.

Wenn die Konfiguration eingerichtet ist, kann der Inhalt mit einem Browser oder einem anderen HTTP-Client heruntergeladen werden. Wenn Sie für iOS entwickeln, können Sie die dedizierte WAppKitSync-Client-Bibliothek verwenden. Der Download-Speicherort besteht aus dem Pfad der Konfiguration und der Erweiterung *.zip*, z. B. wenn mit einer lokalen AEM-Instanz gearbeitet wird: *http://localhost:4502/content/weretail_go.zip*

### Die Konsole zur Inhaltssynchronisierung {#the-content-sync-console}

In der Konsole „Inhaltssynchronisierung“ werden alle Inhaltssynchronisierungskonfigurationen im Repository (alle Knoten vom Typ &quot;`cq:ContentSyncConfig`„) aufgelistet. Für jede Konfiguration haben Sie folgende Möglichkeiten:

* Aktualisieren Sie den Cache.
* Löschen Sie den Cache.
* Laden Sie eine vollständige Zip herunter.
* Laden Sie eine Zip-Datei für Unterschiede zwischen dem aktuellen Datum und der Uhrzeit herunter.

Dies kann für die Entwicklung und Fehlerbehebung nützlich sein.

Der Zugriff auf die Konsole ist möglich unter:

`http://localhost:4502/libs/cq/contentsync/content/console.html`

Dies sieht wie folgt aus:

![chlimage_1-50](assets/chlimage_1-50.png)

### Erweitern des Content Sync-Frameworks {#extending-the-content-sync-framework}

Obwohl die Anzahl der Konfigurationsoptionen bereits sehr umfangreich ist, deckt sie möglicherweise nicht alle Anforderungen Ihres spezifischen Anwendungsfalls ab. In diesem Abschnitt werden die Erweiterungspunkte des Content Sync-Frameworks und die Erstellung benutzerdefinierter Konfigurationstypen beschrieben.

Für jeden Konfigurationstyp gibt es einen *Content Update Handler*, eine OSGi-Komponentenfactory, die für diesen bestimmten Typ registriert ist. Diese Handler erfassen Inhalte, verarbeiten sie und fügen sie einem Cache hinzu, der vom Inhaltssynchronisierungs-Framework verwaltet wird. Implementieren Sie die folgende Schnittstelle oder abstrakte Basisklasse:

* `com.day.cq.contentsync.handler.ContentUpdateHandler` - Schnittstelle, die alle Update-Handler implementieren müssen
* `com.day.cq.contentsync.handler.AbstractSlingResourceUpdateHandler` - Eine abstrakte Klasse, die das Rendering von Ressourcen mithilfe von Sling vereinfacht

Registrieren Sie Ihre Klasse als OSGi-Komponenten-Factory und stellen Sie sie im OSGi-Container in einem Bundle bereit. Dies kann mit dem Maven[SCR-Plug-in ](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/apache-felix-maven-scr-plugin-use.html) JavaDoc-Tags oder -Anmerkungen erfolgen. Das folgende Beispiel zeigt die JavaDoc-Version:

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

Beachten Sie, dass *factory*-Definition die gemeinsame Schnittstelle und den benutzerdefinierten Typ enthält, getrennt durch einen Schrägstrich. Diese Strategie ermöglicht es dem Inhaltssynchronisierungs-Framework, eine Instanz der benutzerdefinierten Klasse zu finden und zu erstellen, während es den benutzerdefinierten Typ in einem Konfigurationseintrag erkennt. Im nächsten Abschnitt finden Sie ein konkretes Beispiel für einen benutzerdefinierten Aktualisierungs-Handler.

>[!CAUTION]
>
>Beim Aufbauen auf der AbstractSlingResourceUpdateHandler-Basisklasse müssen Sie die Definition *inherit* hinzufügen. Andernfalls legt der OSGi-Container die erforderlichen Verweise, die in der Basisklasse deklariert sind, nicht fest.

### Implementieren eines benutzerdefinierten Update-Handlers {#implementing-a-custom-update-handler}

Jede We.Retail Mobile-Seite enthält ein Logo in der oberen linken Ecke, das in die ZIP-Datei aufgenommen werden sollte. Für die Cache-Optimierung verweist AEM jedoch nicht auf den tatsächlichen Speicherort der Bilddatei im Repository, was verhindert, dass wir einfach den Konfigurationstyp **copy** verwenden. Stattdessen müssen Sie einen eigenen Konfigurationstyp **logo** bereitstellen, der das Bild an dem von AEM angeforderten Speicherort verfügbar macht. Die folgende Code-Liste zeigt die vollständige Implementierung des Logo-Update-Handlers:

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

Die `LogoUpdateHandler`-Klasse implementiert die `updateCacheEntry(ConfigEntry, Long, String, Session, Session)`-Methode der `ContentUpdateHandler`-Schnittstelle, die mehrere Argumente benötigt:

* Eine `ConfigEntry`-Instanz, die Zugriff auf den Konfigurationseintrag, für den dieser Handler aufgerufen wird, und seine Eigenschaften bietet.
* Ein `lastUpdated` Zeitstempel, der angibt, wann die Inhaltssynchronisierung ihren Cache zuletzt aktualisiert hat. Inhalte, die nach diesem Zeitstempel nicht geändert wurden, sollten vom -Handler nicht aktualisiert werden.
* Ein `configCacheRoot`, das den Stammpfad des Caches angibt. Alle aktualisierten Dateien müssen unter diesem Pfad gespeichert werden, damit sie der ZIP-Datei hinzugefügt werden können.
* Eine Verwaltungssitzung, die für alle Cache-bezogenen Repository-Vorgänge verwendet werden sollte.
* Eine Benutzersitzung, die verwendet werden kann, um Inhalte im Kontext eines bestimmten Benutzers zu aktualisieren und so eine Art personalisierten Inhalt bereitzustellen.

Um den benutzerdefinierten Handler zu implementieren, erstellen Sie zunächst eine Instanz der Image-Klasse basierend auf der Ressource, die im Konfigurationseintrag angegeben ist. Dies ist das gleiche Verfahren, das die eigentliche Logo-Komponente auf unseren Seiten durchführt. Dadurch wird sichergestellt, dass der Zielpfad des Bildes mit dem von einer Seite referenzierten Pfad übereinstimmt.

Überprüfen Sie anschließend, ob die Ressource seit der letzten Aktualisierung geändert wurde. Benutzerdefinierte Implementierungen sollten unnötige Aktualisierungen des Caches vermeiden und „false“ zurückgeben, wenn sich nichts ändert. Wenn die Ressource geändert wurde, kopieren Sie das Bild an den erwarteten Zielspeicherort relativ zum Cache-Stamm. Schließlich wird `true` zurückgegeben, um dem Framework anzugeben, dass der Cache aktualisiert wurde.

## Verwenden des Inhalts auf dem Client {#using-the-content-on-the-client}

Um Inhalte in einer Mobile App zu verwenden, die von Content Sync bereitgestellt wird, müssen Sie Inhalte über eine HTTP- oder HTTPS-Verbindung anfordern. Daher können abgerufene Inhalte (gepackt in einer ZIP-Datei) extrahiert und lokal auf dem Mobilgerät gespeichert werden. Inhalte beziehen sich nicht nur auf Daten, sondern auch auf Logik, d. h. vollständige Web-Anwendungen. Dadurch kann der mobile Benutzer abgerufene Web-Anwendungen und entsprechende Daten auch ohne Netzwerkverbindung ausführen.

Die Inhaltssynchronisierung stellt Inhalte auf intelligente Weise bereit: Nur Datenänderungen seit der letzten erfolgreichen Datensynchronisierung werden bereitgestellt, wodurch die für die Datenübertragung benötigte Zeit verkürzt wird. Bei der ersten Ausführung einer Anwendung werden seit dem 01. Januar 1970 Datenänderungen angefordert, während später nur Daten angefordert werden, die sich seit der letzten erfolgreichen Synchronisierung geändert haben. AEM verwendet ein Client-Kommunikations-Framework für iOS, um die Datenkommunikation und -übertragung zu vereinfachen, sodass für eine iOS-basierte Web-Anwendung nur ein minimaler nativer Code erforderlich ist.

Alle übertragenen Daten können in dieselbe Verzeichnisstruktur extrahiert werden, es sind keine zusätzlichen Schritte (z. B. Abhängigkeitsprüfungen) beim Extrahieren von Daten erforderlich. Wenn iOS vorhanden ist, werden alle Daten in einem Unterordner im Ordner Dokumente der iOS-App gespeichert.

Typischer Ausführungspfad einer iOS-basierten AEM Mobile-App:

* Benutzer startet App auf iOS-Gerät.
* Die App versucht, eine Verbindung zum AEM-Backend herzustellen und fordert Datenänderungen seit der letzten Ausführung an.
* Der Server ruft die betreffenden Daten ab und packt sie in eine Datei.
* Die Daten werden an das Client-Gerät zurückgegeben, wo sie in den Ordner „Dokumente“ extrahiert werden.
* Die UIWebView-Komponente wird gestartet/aktualisiert.

Wenn zuvor keine Verbindung hergestellt werden konnte, werden heruntergeladene Daten angezeigt.

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Admins und Autoren finden Sie in den folgenden Ressourcen:

* [Authoring von AEM-Inhalten für AEM Mobile On-demand Services](/help/mobile/mobile-apps-ondemand.md)
* [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)
