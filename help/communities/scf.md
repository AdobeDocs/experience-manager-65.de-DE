---
title: Social Component Framework
seo-title: Social Component Framework
description: Das Social Component Framework (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten
seo-description: Das Social Component Framework (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten
uuid: 23b4418d-b91c-46fc-bf42-1154ef79fe5a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d7b5b5e3-2d84-4a6b-bcc2-d490882ff3ed
exl-id: 5ca58bc3-8505-4d91-9cd1-6b2e2671f1be
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 0%

---

# Social Component Framework {#social-component-framework}

Das Social Component Framework (SCF) vereinfacht die Konfiguration, Anpassung und Erweiterung von Communities-Komponenten auf Server- und Client-Seite.

Vorteile des Frameworks:

* **Funktionell**: Native Integration mit wenig oder gar keiner Anpassung für 80 % der Anwendungsfälle.
* **Skinable**: Konsistente Verwendung von HTML-Attributen für CSS-Stile.
* **Erweiterbar**: Die Komponentenimplementierung ist objektorientiert und basiert auf der Geschäftslogik - einfach hinzuzufügen, inkrementelle Geschäftsanmeldungen auf dem Server.
* **Flexibel**: Einfache JavaScript-Vorlagen ohne Logik, die einfach überlagert und angepasst werden können.
* **Zugänglich**: Die HTTP-API unterstützt das Posten von jedem Client, einschließlich mobiler Apps.
* **Tragbar**: Integrieren/einbetten Sie in jede Webseite, die auf einer beliebigen Technologie basiert.

Erkunden Sie eine Autoren- oder Veröffentlichungsinstanz mithilfe des interaktiven Leitfadens [Community-Komponenten](components-guide.md).

## Überblick {#overview}

In SCF besteht eine Komponente aus einem SocialComponent POJO, einer Handlebars-JS-Vorlage (zum Rendern der Komponente) und CSS (zum Formatieren der Komponente).

Eine Handlebars-JS-Vorlage kann die JS-Komponenten model/view erweitern, um die Benutzerinteraktion mit der Komponente auf dem Client zu handhaben.

Wenn eine Komponente die Änderung von Daten unterstützen muss, kann die Implementierung der SocialComponent-API geschrieben werden, um die Bearbeitung/Speicherung von Daten ähnlich den Modell-/Datenobjekten in herkömmlichen Webanwendungen zu unterstützen. Darüber hinaus können Vorgänge (Controller) und ein Vorgangsdienst hinzugefügt werden, um Vorgangsanfragen zu verarbeiten, Geschäftslogik auszuführen und die APIs für die Modell-/Datenobjekte aufzurufen.

Die SocialComponent-API kann erweitert werden, um Daten bereitzustellen, die von einem Client für eine Ansichtsebene oder einen HTTP-Client benötigt werden.

### Darstellung von Seiten für Client {#how-pages-are-rendered-for-client}

![scf-page-rendering](assets/scf-overview.png)

### Komponentenanpassung und -erweiterung {#component-customization-and-extension}

Um die Komponenten anzupassen oder zu erweitern, schreiben Sie nur die Überlagerungen und Erweiterungen in Ihr Verzeichnis /apps , wodurch die Aktualisierung auf zukünftige Versionen vereinfacht wird.

* Für Skinning:
   * Nur das CSS [muss bearbeitet werden](client-customize.md#skinning-css).
* Für Look and Feel:
   * Ändern Sie die JS-Vorlage und CSS.
* Für Look, Feel und UX:
   * Ändern Sie die JS-Vorlage, CSS und [Javascript erweitern/überschreiben](client-customize.md#extending-javascript).
* So ändern Sie die Informationen, die für die JS-Vorlage oder für den GET-Endpunkt verfügbar sind:
   * Erweitern Sie die [SocialComponent](server-customize.md#socialcomponent-interface).
* So fügen Sie benutzerdefinierte Verarbeitung während Vorgängen hinzu:
   * Schreiben Sie eine [OperationExtension](server-customize.md#operationextension-class).
* So fügen Sie einen neuen benutzerdefinierten Vorgang hinzu:
   * Erstellen Sie einen neuen [Sling Post Operation](server-customize.md#postoperation-class).
   * Verwenden Sie bei Bedarf vorhandene [OperationServices](server-customize.md#operationservice-class).
   * Fügen Sie nach Bedarf JavaScript-Code hinzu, um den Vorgang von der Clientseite aus aufzurufen.

## Server-seitiges Framework {#server-side-framework}

Das Framework stellt APIs für den Zugriff auf Funktionen auf dem Server und die Interaktion zwischen Client und Server bereit.

### Java-APIs {#java-apis}

Die Java-APIs bieten abstrakte Klassen und Schnittstellen, die einfach geerbt oder unterteilt werden können.

Die Hauptklassen werden auf der Seite [Serverseitige Anpassung](server-customize.md) beschrieben.

Besuchen Sie [Übersicht über den Speicheranbieter](srp.md), um mehr über die Arbeit mit UGC zu erfahren.

### HTTP-API {#http-api}

Die HTTP-API unterstützt die einfache Anpassung und Auswahl von Client-Plattformen für PhoneGap-Apps, native Apps und andere Integrationen und Mashups. Darüber hinaus ermöglicht die HTTP-API es einer Community-Site, als Dienst ohne Client ausgeführt zu werden, sodass Framework-Komponenten in jede auf einer beliebigen Technologie aufbauende Webseite integriert werden können.

### HTTP-API - GET Requests {#http-api-get-requests}

Für jede SocialComponent stellt das Framework einen HTTP-basierten API-Endpunkt bereit. Der Zugriff auf den Endpunkt erfolgt durch Senden einer GET-Anfrage an die Ressource mit der Selektor + Erweiterung &quot;.social.json&quot;. Mit Sling wird die Anfrage an `DefaultSocialGetServlet` übergeben.

**`DefaultSocialGetServlet`**

1. Übergibt die Ressource (resourceType) an `SocialComponentFactoryManager` und erhält eine SocialComponentFactory, die eine `SocialComponent`-Ressource auswählen kann, die die Ressource darstellt.

1. Ruft die Factory auf und erhält einen `SocialComponent` , der die Ressource und Anforderung verarbeiten kann.
1. Ruft `SocialComponent` auf, wodurch die Anfrage verarbeitet und eine JSON-Darstellung der Ergebnisse zurückgegeben wird.
1. Gibt die JSON-Antwort an den Client zurück.

**`GET Request`**

Ein standardmäßiges GET-Servlet überwacht .social.json -Anfragen, auf die die SocialComponent mit anpassbarer JSON antwortet.

![scf-framework](assets/scf-framework.png)

### HTTP-API - POST Requests {#http-api-post-requests}

Zusätzlich zu den GET (Lesen)-Vorgängen definiert das Framework ein Endpunktmuster, um andere Vorgänge für eine Komponente zu aktivieren, darunter Erstellen, Aktualisieren und Löschen. Diese Endpunkte sind HTTP-APIs, die Eingaben akzeptieren und entweder mit HTTP-Statuscodes oder mit einem JSON-Antwortobjekt antworten.

Dieses Framework-Endpunktmuster macht CUD-Vorgänge erweiterbar, wiederverwendbar und prüfbar.

**`POST Request`**

Für jeden Vorgang &quot;SocialComponent&quot;gibt es einen Sling-Vorgang POST:operation. Die Geschäftslogik und der Wartungscode für jeden Vorgang sind in einen OperationService eingeschlossen, auf den über die HTTP-API oder von einem anderen Ort aus als OSGi-Dienst zugegriffen werden kann. Erweiterungen von Plug-ins für Vor-/Nach-Aktionen werden über Erweiterungen von Erweiterungen bereitgestellt.

![scf-post-request](assets/scf-post-request.png)

### Storage Resource Provider (SRP) {#storage-resource-provider-srp}

Informationen zur Handhabung von UGC, die im [Community-Inhaltsspeicher](working-with-srp.md) gespeichert sind, finden Sie unter:

* [Übersicht über den Speicheranbieter](srp.md)  - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - Methoden und Beispiele für SRP-API-Dienstprogramme.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Coding Guidelines.

### Serverseitige Anpassungen {#server-side-customizations}

Unter [Serverseitige Anpassungen](server-customize.md) finden Sie Informationen zum Anpassen der Geschäftslogik und des Verhaltens einer Communities-Komponente auf der Server-Seite.

## Handlebars JS-Vorlagensprache {#handlebars-js-templating-language}

Eine der auffälligeren Änderungen im neuen Framework ist die Verwendung der [Handlebars JS-Vorlagensprache (HBS)](https://www.handlebarsjs.com/), einer beliebten Open-Source-Technologie für Server-Client-Rendering.

HBS-Skripte sind einfach, logiklos, auf dem Server und Client kompiliert, einfach zu überlagern und anzupassen und sind natürlich mit der Client-UX verbunden, da HBS das Client-seitige Rendering unterstützt.

Das Framework stellt mehrere [Handlebars-Helfer](handlebars-helpers.md) bereit, die bei der Entwicklung von SocialComponents nützlich sind.

Wenn Sling auf dem Server eine GET-Anfrage auflöst, identifiziert er das Skript, das zur Beantwortung der Anfrage verwendet wird. Wenn das Skript eine HBS-Vorlage (.hbs) ist, delegiert Sling die Anforderung an die Handlebars-Engine. Die Handlebars-Engine ruft dann die SocialComponent von der entsprechenden SocialComponentFactory ab, erstellt einen Kontext und rendert den HTML-Code.

### Keine Zugriffsbeschränkung {#no-access-restriction}

Handlebars (HBS)-Vorlagendateien (.hbs) entsprechen .jsp- und .html-Vorlagendateien, können jedoch sowohl im Client-Browser als auch auf dem Server für die Wiedergabe verwendet werden. Daher erhält ein Client-Browser, der eine clientseitige Vorlage anfordert, eine .hbs-Datei vom Server.

Dies erfordert, dass alle HBS-Vorlagen im Sling-Suchpfad (alle .hbs-Dateien unter /libs/ oder /apps) von jedem Benutzer aus der Autoren- oder Veröffentlichungsinstanz abgerufen werden können.

HTTP-Zugriff auf .hbs-Dateien ist möglicherweise nicht verboten.

### Hinzufügen oder Einschließen einer Communities-Komponente {#add-or-include-a-communities-component}

Die meisten Communities-Komponenten müssen *added* als adressierbare Sling-Ressource sein. Einige Communitys-Komponenten können *enthalten* in einer Vorlage als nicht vorhandene Ressource sein, um eine dynamische Einbindung und Anpassung des Speicherorts zu ermöglichen, an dem benutzergenerierte Inhalte geschrieben werden (UGC).

In beiden Fällen müssen auch die [erforderlichen Client-Bibliotheken der Komponente](clientlibs.md) vorhanden sein.

**Hinzufügen einer Komponente**

Das Hinzufügen einer Komponente bezieht sich auf den Prozess des Hinzufügens einer Instanz einer Ressource (Komponente), z. B. wenn diese aus dem Komponenten-Browser (Sidekick) auf eine Seite im Bearbeitungsmodus für Autoren gezogen wird.

Das Ergebnis ist ein untergeordneter JCR-Knoten unter einem par -Knoten, der Sling-adressierbar ist.

**Komponente einschließen**

Das Einschließen einer Komponente bezieht sich auf den Prozess zum Hinzufügen eines Verweises auf eine [&quot;nicht vorhandene&quot;Ressource](srp.md#for-non-existing-resources-ners) (kein JCR-Knoten) innerhalb der Vorlage, z. B. mithilfe einer Skriptsprache.

Ab AEM 6.1 ist es möglich, die Eigenschaften der Komponente im Authoring *design *mode zu bearbeiten, wenn eine Komponente dynamisch eingeschlossen statt hinzugefügt wird.

Es können nur einige ausgewählte AEM Communities-Komponenten dynamisch eingeschlossen werden. Sie sind:

* [Kommentare](essentials-comments.md)
* [Bewertung](rating-basics.md)
* [Reviews](reviews-basics.md)
* [Abstimmung](essentials-voting.md)

Im [Community Components Guide](components-guide.md) können einbeziehbare Komponenten umgeschaltet werden, sodass sie nicht hinzugefügt werden.

**Bei Verwendung der** Vorlagensprache Handlebarstemplating wird die nicht vorhandene Ressource mit dem  [include-](handlebars-helpers.md#include) Helperby eingeschlossen, indem der Ressourcentyp angegeben wird:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Bei Verwendung von JSP** wird eine Ressource mit dem Tag  [cq:include](../../help/sites-developing/taglib.md#lt-cq-include) eingeschlossen:

```
<cq:include path="votes"
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Informationen zum dynamischen Hinzufügen einer Komponente zu einer Seite finden Sie unter [Komponenten-Sideloading](sideloading.md), anstatt sie in eine Vorlage hinzuzufügen oder einzufügen.

### Handlebars Helpers {#handlebars-helpers}

Eine Liste und Beschreibung der in SCF verfügbaren benutzerdefinierten Helfer finden Sie unter [SCF Handlebars Helpers](handlebars-helpers.md) .

## Client-seitiges Framework {#client-side-framework}

### JavaScript-Framework für Modellansichten {#model-view-javascript-framework}

Das Framework umfasst eine Erweiterung von [Backbone.js](https://www.backbonejs.org/), einem JavaScript-Framework für Modellansichten, um die Entwicklung von komplexen, interaktiven Komponenten zu erleichtern. Die objektorientierte Natur unterstützt ein erweiterbares/wiederverwendbares Framework. Die Kommunikation zwischen Client und Server wird mithilfe der HTTP-API vereinfacht.

Das Framework nutzt serverseitige Handlebars-Vorlagen, um die Komponenten für den Client zu rendern. Die Modelle basieren auf den von der HTTP-API generierten JSON-Antworten. Die Ansichten binden sich an HTML, das von den Handlebars-Vorlagen generiert wurde, und bieten Interaktivität.

### CSS-Konventionen {#css-conventions}

Die folgenden Konventionen werden zum Definieren und Verwenden von CSS-Klassen empfohlen:

* Verwenden Sie eindeutig Namespace-CSS-Klassenselektornamen und vermeiden Sie allgemeine Namen wie &quot;Überschrift&quot;, &quot;Bild&quot;usw.
* Definieren Sie bestimmte Stile für Klassenselektoren, damit die CSS-Stylesheets mit anderen Elementen und Stilen auf der Seite gut funktionieren. Beispiel: `.social-forum .topic-list .li { color: blue; }`
* Halten Sie CSS-Klassen für die Formatierung getrennt von CSS-Klassen für UX, die von JavaScript gesteuert werden.

### Clientseitige Anpassungen {#client-side-customizations}

Um das Erscheinungsbild und Verhalten einer Communities-Komponente Client-seitig anzupassen, verweisen Sie auf [Client-seitige Anpassungen](client-customize.md), die Informationen zu folgenden Themen enthalten:

* [Überlagerungen](client-customize.md#overlays)
* [Erweiterungen](client-customize.md#extensions)
* [HTML-Markup](client-customize.md#htmlmarkup)
* [Gestalten von CSS](client-customize.md#skinning-css)
* [JavaScript erweitern](client-customize.md#extending-javascript)
* [Clientlibs für SCF](client-customize.md#clientlibs-for-scf)

## Funktionen und Komponenten {#feature-and-component-essentials}

Grundlegende Informationen für Entwickler werden im Abschnitt [Funktionen und Komponenten-Grundlagen](essentials.md) beschrieben.

Weitere Entwicklerinformationen finden Sie im Abschnitt [Coding Guidelines](code-guide.md) .

## Fehlerbehebung {#troubleshooting}

Allgemeine Probleme und bekannte Probleme werden im Abschnitt [Fehlerbehebung](troubleshooting.md) beschrieben.
