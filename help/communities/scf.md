---
title: Social Component Framework
seo-title: Social Component Framework
description: Das Framework für soziale Komponenten (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten
seo-description: Das Framework für soziale Komponenten (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten
uuid: 23b4418d-b91c-46fc-bf42-1154ef79fe5a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d7b5b5e3-2d84-4a6b-bcc2-d490882ff3ed
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 0%

---


# Social Component Framework {#social-component-framework}

Das Framework für Social-Komponenten (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten sowohl serverseitig als auch clientseitig.

Vorteile des Rahmens:

* **Funktionell**: Standardmäßige Integration mit wenig oder gar keiner Anpassung für 80 % der Anwendungsfälle.
* **Skinierbar**: Konsistente Verwendung von HTML-Attributen für die CSS-Formatierung.
* **Erweiterbar**: Die Komponentenimplementierung ist objektorientiert und basiert auf der Geschäftslogik - einfach, inkrementelle Geschäftsanmeldung auf dem Server hinzuzufügen.
* **Flexibel**: Einfache JavaScript-Vorlagen ohne Logik, die einfach überlagert und angepasst werden können.
* **Verfügbar**: Die HTTP-API unterstützt das Posten von jedem Client, einschließlich mobilen Apps.
* **Tragbar**: Integrieren/Einbetten in jede Webseite, die auf einer beliebigen Technologie basiert.

Entdecken Sie eine Instanz im Autoren- oder Veröffentlichungsmodus mithilfe des interaktiven [Handbuchs &quot;Community-Komponenten&quot;](components-guide.md).

## Überblick {#overview}

In SCF besteht eine Komponente aus einem SocialComponent-POJO, einer Handlebars-JS-Vorlage (zum Rendern der Komponente) und einem CSS (zum Formatieren der Komponente).

Eine Handlebars-JS-Vorlage kann die JS-Komponenten des Modells/der Ansicht erweitern, um die Benutzerinteraktion mit der Komponente auf dem Client zu verarbeiten.

Wenn eine Komponente eine Datenänderung unterstützen muss, kann die Implementierung der SocialComponent-API geschrieben werden, um die Bearbeitung/Speicherung von Daten zu unterstützen, die dem Modell/den Datenobjekten in herkömmlichen Webanwendungen ähnlich sind. Darüber hinaus können Vorgänge (Controller) und ein Vorgangsdienst hinzugefügt werden, um Vorgangsanforderungen zu bearbeiten, Geschäftslogik auszuführen und die APIs auf den Modell-/Datenobjekten aufzurufen.

Die SocialComponent-API kann erweitert werden, um Daten bereitzustellen, die von einem Client für eine Ansichten- oder HTTP-Client benötigt werden.

### Seitenwiedergabe für Client {#how-pages-are-rendered-for-client}

![scf-page-rendering](assets/scf-overview.png)

### Komponentenanpassung und Erweiterung {#component-customization-and-extension}

Um die Komponenten anzupassen oder zu erweitern, schreiben Sie nur die Überlagerungen und Erweiterungen in Ihren /apps-Ordner, was die Aktualisierung auf zukünftige Versionen vereinfacht.

* Für Skins:
   * Nur das CSS muss bearbeitet werden](client-customize.md#skinning-css).[
* Für Look and Feel:
   * Ändern Sie die JS-Vorlage und die CSS.
* Für Look, Feel und UX:
   * Ändern Sie JS-Vorlage, CSS und [Javascript erweitern/überschreiben](client-customize.md#extending-javascript).
* So ändern Sie die verfügbaren Informationen für die JS-Vorlage oder den GET-Endpunkt:
   * Erweitern Sie die [SocialComponent](server-customize.md#socialcomponent-interface).
* So fügen Sie benutzerdefinierte Verarbeitung während der Vorgänge hinzu:
   * Schreiben Sie eine [OperationExtension](server-customize.md#operationextension-class).
* So fügen Sie einen neuen benutzerdefinierten Vorgang hinzu:
   * Erstellen Sie einen neuen [Sling Post-Vorgang](server-customize.md#postoperation-class).
   * Verwenden Sie nach Bedarf vorhandene [OperationServices](server-customize.md#operationservice-class).
   * hinzufügen Sie Javascript-Code, um den Vorgang nach Bedarf vom Client aus aufzurufen.

## Server-Side Framework {#server-side-framework}

Das Framework stellt APIs zum Zugriff auf Funktionen auf dem Server und zur Unterstützung der Interaktion zwischen Client und Server bereit.

### Java-APIs {#java-apis}

Die Java-APIs bieten abstrakte Klassen und Schnittstellen, die leicht geerbt oder unterklassifiziert werden können.

Die Hauptklassen werden auf der Seite [Serverseitige Anpassung](server-customize.md) beschrieben.

Informationen zum Arbeiten mit UGC finden Sie unter [Übersicht über den Ressourcenanbieter der Datenspeicherung](srp.md).

### HTTP-API {#http-api}

Die HTTP-API unterstützt die einfache Anpassung und Auswahl von Client-Plattformen für PhoneGap-Apps, native Apps und andere Integrationen und Mashups. Darüber hinaus ermöglicht die HTTP-API es einer Community-Site, als Dienst ohne Client zu laufen, sodass Framework-Komponenten in jede Webseite integriert werden können, die auf einer beliebigen Technologie basiert.

### HTTP-API - GET Anfragen {#http-api-get-requests}

Für jede SocialComponent stellt das Framework einen HTTP-basierten API-Endpunkt bereit. Der Zugriff auf den Endpunkt erfolgt durch Senden einer GET an die Ressource mit der Auswahl &quot;.social.json&quot; + Erweiterung. Mit Sling wird die Anfrage an das `DefaultSocialGetServlet` übergeben.

**`DefaultSocialGetServlet`**

1. Übergibt die Ressource (resourceType) an das `SocialComponentFactoryManager` und empfängt eine SocialComponentFactory, die eine `SocialComponent` auswählen kann, welche die Ressource darstellt.

1. Ruft die Factory auf und empfängt ein `SocialComponent`, das die Ressource und Anforderung bearbeiten kann.
1. Ruft das `SocialComponent` auf, das die Anforderung verarbeitet und eine JSON-Darstellung der Ergebnisse zurückgibt.
1. Gibt die JSON-Antwort an den Client zurück.

**`GET Request`**

Ein standardmäßiges GET-Servlet überwacht Anforderungen vom Typ .social.json, auf die die SocialComponent mit anpassbarer JSON-Datei reagiert.

![scf-framework](assets/scf-framework.png)

### HTTP-API - POST-Anfragen {#http-api-post-requests}

Zusätzlich zu den Vorgängen &quot;GET (Lesen)&quot;definiert das Framework ein Endpunktmuster, um andere Vorgänge für eine Komponente zu aktivieren, einschließlich Erstellen, Aktualisieren und Löschen. Diese Endpunkte sind HTTP-APIs, die Eingaben akzeptieren und entweder mit HTTP-Statuscodes oder mit einem JSON-Antwortobjekt reagieren.

Dieses Framework-Endpunktmuster macht CUD-Vorgänge erweiterbar, wiederverwendbar und prüfbar.

**`POST Request`**

Für jeden SocialComponent-Vorgang gibt es eine Sling POST:operation. Die Geschäftslogik und der Wartungscode für jeden Vorgang werden in einen OperationService eingeschlossen, auf den über die HTTP-API oder von einem anderen Ort aus als OSGi-Dienst zugegriffen werden kann. Haken werden bereitgestellt, die Plug-In-Operationserweiterungen für Vor-/Nach-Aktionen unterstützen.

![scf-post-request](assets/scf-post-request.png)

### Datenspeicherung Resource Provider (SRP) {#storage-resource-provider-srp}

Informationen zum Umgang mit UGC, die im [Community Content Store](working-with-srp.md) gespeichert sind, finden Sie unter:

* [Übersicht über](srp.md)  den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - Methoden und Beispiele des SRP API-Dienstprogramms.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien.

### Serverseitige Anpassungen {#server-side-customizations}

Informationen zum Anpassen der Geschäftslogik und des Verhaltens einer Communities-Komponente auf Serverseite finden Sie unter [Serverseitige Anpassungen](server-customize.md).

## Handlebars JS-Vorlagensprache {#handlebars-js-templating-language}

Eine der auffälligsten Änderungen im neuen Framework ist die Verwendung der [Handlebars JS-Vorlagenstufe (HBS)](https://www.handlebarsjs.com/), einer beliebten Open-Source-Technologie zum Rendern von Server-Clients.

HBS-Skripten sind einfach, logisch-frei, kompiliert auf Server und Client, leicht zu überlagern und anzupassen und natürlich mit dem Client-UX zu binden, da HBS das clientseitige Rendering unterstützt.

Das Framework stellt mehrere [Handlebars Helpers](handlebars-helpers.md) bereit, die bei der Entwicklung von SocialComponents nützlich sind.

Wenn Sling auf dem Server eine GET auflöst, identifiziert er das Skript, das zur Beantwortung der Anforderung verwendet wird. Wenn es sich bei dem Skript um eine HBS-Vorlage (.hbs) handelt, leitet Sling die Anforderung an die Handlebars-Engine weiter. Die Handlebars-Engine ruft dann die SocialComponent aus der entsprechenden SocialComponentFactory ab, erstellt einen Kontext und gibt den HTML-Code wieder.

### Keine Zugriffsbeschränkung {#no-access-restriction}

Handlebars (HBS)-Vorlagendateien (.hbs) sind mit .jsp- und .html-Vorlagendateien identisch, können jedoch sowohl im Client-Browser als auch auf dem Server gerendert werden. Daher erhält ein Client-Browser, der eine clientseitige Vorlage anfordert, eine HB-Datei vom Server.

Dies erfordert, dass alle HBS-Vorlagen im sling-Suchpfad (alle .hbs-Dateien unter /libs/ oder /apps) von jedem Benutzer aus dem Autor oder der Veröffentlichung abgerufen werden können.

HTTP-Zugriff auf .hbs-Dateien ist möglicherweise nicht verboten.

### Eine Communities-Komponente {#add-or-include-a-communities-component} Hinzufügen oder einschließen

Die meisten Communities-Komponenten müssen *hinzugefügt* als adressierbare Sling-Ressource sein. Einige der Communities-Komponenten können *in einer Vorlage als nicht vorhandene Ressource enthalten sein, um eine dynamische Einbindung und Anpassung des Ortes zu ermöglichen, an dem benutzergenerierte Inhalte geschrieben werden (UGC).*

In beiden Fällen müssen auch die erforderlichen Client-Bibliotheken der Komponente [vorhanden sein.](clientlibs.md)

**hinzufügen einer Komponente**

Das Hinzufügen einer Komponente bezieht sich auf den Prozess, bei dem eine Instanz einer Ressource (Komponente) hinzugefügt wird, z. B. wenn sie vom Komponenten-Browser (Sidekick) auf eine Seite im Authoring-Bearbeitungsmodus gezogen wird.

Das Ergebnis ist ein untergeordneter JCR-Knoten unter einem par-Knoten, der Sling adressierbar ist.

**Komponente einschließen**

Das Einschließen einer Komponente bezieht sich auf den Prozess, bei dem innerhalb der Vorlage eine Referenz zu einer nicht vorhandenen Ressource [ (kein JCR-Knoten) hinzugefügt wird, z. B. mithilfe einer Skriptsprache.](srp.md#for-non-existing-resources-ners)

Ab AEM 6.1 ist es möglich, die Eigenschaften der Komponente im Autorenmodus *design *mode zu bearbeiten, wenn eine Komponente dynamisch eingeschlossen und nicht hinzugefügt wird.

Es können nur einige ausgewählte AEM Communities-Komponenten dynamisch eingeschlossen werden. Sie sind:

* [Kommentare](essentials-comments.md)
* [Bewertung](rating-basics.md)
* [Beurteilungen](reviews-basics.md)
* [Abstimmung](essentials-voting.md)

Das [Community-Komponentenleitfaden](components-guide.md) ermöglicht das Umschalten zwischen den Einschlüssen von inklusiven Komponenten.

**Bei Verwendung der** Handlebarstemplersprache wird die nicht vorhandene Ressource mit der  [include-](handlebars-helpers.md#include) Hilfe eingeschlossen, indem der resourceType angegeben wird:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Bei Verwendung von JSP** wird eine Ressource mit dem Tag  [cq:include](../../help/sites-developing/taglib.md#lt-cq-include) eingeschlossen:

```
<cq:include path="votes"
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Informationen zum dynamischen Hinzufügen einer Komponente zu einer Seite finden Sie unter [Komponenten-Sideloading](sideloading.md).

### Handlebars Helpers {#handlebars-helpers}

Eine Liste und Beschreibung der in SCF verfügbaren benutzerdefinierten Helfer finden Sie unter [SCF Handlebars Helpers](handlebars-helpers.md).

## Client-Side Framework {#client-side-framework}

### Model-Ansicht Javascript Framework {#model-view-javascript-framework}

Das Framework umfasst eine Erweiterung von [Backbone.js](https://www.backbonejs.org/), einem JavaScript-Framework für Modell-Ansichten, um die Entwicklung von Rich-Interaktive-Komponenten zu erleichtern. Die objektorientierte Natur unterstützt ein erweiterbares/wiederverwendbares Framework. Die Kommunikation zwischen Client und Server wird mithilfe der HTTP-API vereinfacht.

Das Framework nutzt serverseitige Handlebars-Vorlagen, um die Komponenten für den Client wiederzugeben. Die Modelle basieren auf den JSON-Antworten, die von der HTTP-API generiert wurden. Die Ansichten binden sich an HTML, das von den Handlebars-Vorlagen generiert wurde, und bieten Interaktivität.

### CSS-Konventionen {#css-conventions}

Die folgenden Konventionen werden zur Definition und Verwendung von CSS-Klassen empfohlen:

* Verwenden Sie eindeutig benannte CSS-Klassenselektornamen und vermeiden Sie generische Namen wie &quot;heading&quot;, &quot;image&quot;usw.
* Definieren Sie spezifische Stile für Klassenselektoren, damit die CSS-Stylesheets mit anderen Elementen und Stilen auf der Seite gut funktionieren. Beispiel: `.social-forum .topic-list .li { color: blue; }`
* Halten Sie CSS-Klassen für die Formatierung getrennt von CSS-Klassen für UX, die von JavaScript gesteuert werden.

### Clientseitige Anpassungen {#client-side-customizations}

Zum Anpassen des Erscheinungsbilds und Verhaltens einer Communities-Komponente auf Clientseite verweisen Sie auf [Clientseitige Anpassungen](client-customize.md), die Informationen zu folgenden Themen enthalten:

* [Überlagerungen](client-customize.md#overlays)
* [Erweiterungen](client-customize.md#extensions)
* [HTML-Markup](client-customize.md#htmlmarkup)
* [CSS-Skins](client-customize.md#skinning-css)
* [JavaScript erweitern](client-customize.md#extending-javascript)
* [Clientlibs für SCF](client-customize.md#clientlibs-for-scf)

## Feature und Component Essentials {#feature-and-component-essentials}

Grundlegende Informationen für Entwickler werden im Abschnitt [Feature und Component Essentials](essentials.md) beschrieben.

Weitere Entwicklerinformationen finden Sie im Abschnitt [Coding Guidelines](code-guide.md).

## Fehlerbehebung {#troubleshooting}

Allgemeine Probleme und bekannte Probleme werden im Abschnitt [Fehlerbehebung](troubleshooting.md) beschrieben.

