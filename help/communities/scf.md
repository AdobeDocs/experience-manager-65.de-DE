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
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 0%

---


# Social Component Framework {#social-component-framework}

The social component framework (SCF) simplifies the process of configuring, customizing, and extending Communities components on both server-side and client-side.

Vorteile des Rahmens:

* **Funktionell**: Standardmäßige Integration mit wenig oder gar keiner Anpassung für 80 % der Anwendungsfälle.
* **Skinnable**: Consistent use of HTML attributes for CSS styling.
* **Extensible**: Component implementation is object-oriented and light on business logic - easy to add incremental business login on server.
* **Flexible**: Simple logic-less javascript templates that are easily overlayed and customized.
* **Verfügbar**: Die HTTP-API unterstützt das Posten von jedem Client, einschließlich mobilen Apps.
* **Tragbar**: Integrieren/Einbetten in Webseiten, die auf einer beliebigen Technologie basieren.

Entdecken Sie eine Instanz im Autoren- oder Veröffentlichungsmodus mithilfe des Handbuchs &quot;Interaktive [Community-Komponenten&quot;](components-guide.md).

## Übersicht {#overview}

In SCF besteht eine Komponente aus einem SocialComponent-POJO, einer Handlebars-JS-Vorlage (zum Rendern der Komponente) und einem CSS (zum Formatieren der Komponente).

Eine Handlebars-JS-Vorlage kann die JS-Komponenten des Modells/der Ansicht erweitern, um die Benutzerinteraktion mit der Komponente auf dem Client zu verarbeiten.

Wenn eine Komponente eine Datenänderung unterstützen muss, kann die Implementierung der SocialComponent-API geschrieben werden, um die Bearbeitung/Speicherung von Daten zu unterstützen, die dem Modell/den Datenobjekten in herkömmlichen Webanwendungen ähnlich sind. In addition, operations (controllers) and an operation service may be added to handle operation requests, perform business logic, and invoke the APIs on the model/data objects.

Die SocialComponent-API kann erweitert werden, um Daten bereitzustellen, die von einem Client für eine Ansichten- oder HTTP-Client benötigt werden.

### Seitenwiedergabe für Client {#how-pages-are-rendered-for-client}

![scf-page-rendering](assets/scf-overview.png)

### Komponentenanpassung und Erweiterung {#component-customization-and-extension}

Um die Komponenten anzupassen oder zu erweitern, schreiben Sie nur die Überlagerungen und Erweiterungen in Ihren /apps-Ordner, was die Aktualisierung auf zukünftige Versionen vereinfacht.

* Für Skins:
   * Nur das [CSS muss bearbeitet](client-customize.md#skinning-css)werden.
* Für Look and Feel:
   * Ändern Sie die JS-Vorlage und die CSS.
* For Look, Feel and UX:
   * Ändern Sie die JS-Vorlage und CSS und [erweitern/überschreiben Sie JavaScript](client-customize.md#extending-javascript).
* To modify the information availble to the JS Template or to the GET endpoint:
   * Extend the [SocialComponent](server-customize.md#socialcomponent-interface).
* To add custom processing during operations:
   * Eine OperationExtension [schreiben](server-customize.md#operationextension-class).
* So fügen Sie einen neuen benutzerdefinierten Vorgang hinzu:
   * Erstellen Sie einen neuen [Sling Post-Vorgang](server-customize.md#postoperation-class).
   * Verwenden Sie bei Bedarf vorhandene [OperationServices](server-customize.md#operationservice-class) .
   * hinzufügen Sie Javascript-Code, um den Vorgang nach Bedarf vom Client aus aufzurufen.

## Serverseitiges Framework {#server-side-framework}

Das Framework stellt APIs zum Zugriff auf Funktionen auf dem Server und zur Unterstützung der Interaktion zwischen Client und Server bereit.

### Java-APIs {#java-apis}

Die Java-APIs bieten abstrakte Klassen und Schnittstellen, die leicht geerbt oder unterklassifiziert werden können.

Die Hauptklassen werden auf der Seite [Serverseitige Anpassung](server-customize.md) beschrieben.

Informationen zum Arbeiten mit UGC finden Sie unter Übersicht über [den](srp.md) Datenspeicherung Resource Provider.

### HTTP-API {#http-api}

Die HTTP-API unterstützt die einfache Anpassung und Auswahl von Client-Plattformen für PhoneGap-Apps, native Apps und andere Integrationen und Mashups. Darüber hinaus ermöglicht die HTTP-API es einer Community-Site, als Dienst ohne Client zu laufen, sodass Framework-Komponenten in jede Webseite integriert werden können, die auf einer beliebigen Technologie basiert.

### HTTP API - GET Requests {#http-api-get-requests}

For every SocialComponent, the framework provides an HTTP-based API endpoint. The endpoint is accessed by sending a GET request to the resource with a &#39;.social.json&#39; selector + extension. Mit Sling wird der Antrag an die `DefaultSocialGetServlet`Bank übergeben.

**`DefaultSocialGetServlet`**

1. Übergibt die Ressource (resourceType) an die Ressource `SocialComponentFactoryManager` und empfängt eine SocialComponentFactory, die eine `SocialComponent` Darstellung der Ressource auswählen kann.

1. Ruft die Factory auf und empfängt eine `SocialComponent` , die die Ressource und Anforderung handhaben kann.
1. Ruft die `SocialComponent`auf, die die Anforderung verarbeitet und eine JSON-Darstellung der Ergebnisse zurückgibt.
1. Gibt die JSON-Antwort an den Client zurück.

**`GET Request`**

Ein standardmäßiges GET-Servlet überwacht Anforderungen vom Typ .social.json, auf die die SocialComponent mit anpassbarer JSON-Datei reagiert.

![scf-framework](assets/scf-framework.png)

### HTTP API - POST Requests {#http-api-post-requests}

In addition to the GET (Read) operations, the framework defines an endpoint pattern to enable other operations on a component, including Create, Update and Delete. Diese Endpunkte sind HTTP-APIs, die Eingaben akzeptieren und entweder mit HTTP-Statuscodes oder mit einem JSON-Antwortobjekt reagieren.

Dieses Framework-Endpunktmuster macht CUD-Vorgänge erweiterbar, wiederverwendbar und prüfbar.

**`POST Request`**

Für jeden SocialComponent-Vorgang gibt es eine Sling POST:operation. Die Geschäftslogik und der Wartungscode für jeden Vorgang werden in einen OperationService eingeschlossen, auf den über die HTTP-API oder von einem anderen Ort aus als OSGi-Dienst zugegriffen werden kann. Haken werden bereitgestellt, die Plug-In-Operationserweiterungen für Vor-/Nach-Aktionen unterstützen.

![scf-post-request](assets/scf-post-request.png)

### Datenspeicherung Resource Provider (SRP) {#storage-resource-provider-srp}

To learn about handling UGC stored in the [community content store](working-with-srp.md), see:

* [Übersicht über](srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP and UGC Essentials](srp-and-ugc.md) - SRP API utility methods and examples.
* [Accessing UGC with SRP](accessing-ugc-with-srp.md) - Coding guidelines.

### Serverseitige Anpassungen {#server-side-customizations}

Visit [Server-Side Customizations](server-customize.md) for information on customizing the business logic and behavior of a Communities component on the server-side.

## Handlebars JS - Vorlagensprache {#handlebars-js-templating-language}

Eine der bemerkenswerteren Änderungen im neuen Framework ist die Verwendung der [Handlebars JS-Vorlagenerstellungs-Sprache (HBS)](https://www.handlebarsjs.com/), einer beliebten Open-Source-Technologie für die Server-Client-Wiedergabe.

HBS-Skripten sind einfach, logisch-frei, kompiliert auf Server und Client, leicht zu überlagern und anzupassen und natürlich mit dem Client-UX zu binden, da HBS das clientseitige Rendering unterstützt.

Das Framework bietet mehrere [Handlebars-Helfer](handlebars-helpers.md) , die bei der Entwicklung von SocialComponents nützlich sind.

Wenn Sling auf dem Server eine GET auflöst, identifiziert er das Skript, das zur Beantwortung der Anforderung verwendet wird. Wenn es sich bei dem Skript um eine HBS-Vorlage (.hbs) handelt, leitet Sling die Anforderung an die Handlebars-Engine weiter. Die Handlebars-Engine ruft dann die SocialComponent aus der entsprechenden SocialComponentFactory ab, erstellt einen Kontext und gibt den HTML-Code wieder.

### No Access Restriction {#no-access-restriction}

Handlebars (HBS)-Vorlagendateien (.hbs) sind mit .jsp- und .html-Vorlagendateien identisch, können jedoch sowohl im Client-Browser als auch auf dem Server gerendert werden. Daher erhält ein Client-Browser, der eine clientseitige Vorlage anfordert, eine HB-Datei vom Server.

Dies erfordert, dass alle HBS-Vorlagen im sling-Suchpfad (alle .hbs-Dateien unter /libs/ oder /apps) von jedem Benutzer aus dem Autor oder der Veröffentlichung abgerufen werden können.

HTTP-Zugriff auf .hbs-Dateien ist möglicherweise nicht verboten.

### Eine Communities-Komponente Hinzufügen oder einschließen {#add-or-include-a-communities-component}

Die meisten Communities-Komponenten müssen als adressierbare Sling-Ressource *hinzugefügt* werden. Einige ausgewählte Communities-Komponenten können als nicht vorhandene Ressource in eine Vorlage *aufgenommen* werden, um eine dynamische Einbindung und Anpassung des Ortes zu ermöglichen, an dem benutzergenerierte Inhalte (UGC) geschrieben werden.

In beiden Fällen müssen auch die [erforderlichen Client-Bibliotheken](clientlibs.md) der Komponente vorhanden sein.

**Add a Component**

Das Hinzufügen einer Komponente bezieht sich auf den Prozess, bei dem eine Instanz einer Ressource (Komponente) hinzugefügt wird, z. B. wenn sie vom Komponenten-Browser (Sidekick) auf eine Seite im Authoring-Bearbeitungsmodus gezogen wird.

The result is a JCR child node under a par node, which is Sling addressable.

**Include a Component**

Including a component refers to the process of adding a reference to a [&quot;non-existing&quot; resource](srp.md#for-non-existing-resources-ners) (no JCR node) within the template, such as using a scripting language.

As of AEM 6.1, when a component is dynamically included instead of added, it is possible to edit the component&#39;s properties in author *design *mode.

Es können nur einige ausgewählte AEM Communities-Komponenten dynamisch eingeschlossen werden. Sie sind:

* [Kommentare](essentials-comments.md)
* [Bewertung](rating-basics.md)
* [Beurteilungen](reviews-basics.md)
* [Abstimmung](essentials-voting.md)

Das [Community-Komponentenleitfaden](components-guide.md) ermöglicht es, inklusive Komponenten vom Hinzufügen zum Einfügen zu umschalten.

**Bei Verwendung der Vorlagensprache Handlebars** wird die nicht vorhandene Ressource mit dem [Include-Helper](handlebars-helpers.md#include) eingeschlossen, indem der resourceType angegeben wird:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Bei Verwendung von JSP** wird eine Ressource mit dem Tag [cq:include](../../help/sites-developing/taglib.md#lt-cq-include)eingeschlossen:

```
<cq:include path="votes"
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Informationen zum dynamischen Hinzufügen einer Komponente zu einer Seite finden Sie unter [Komponenten-Sideloading](sideloading.md), anstatt sie einer Vorlage hinzuzufügen oder hinzuzufügen.


### Handlebar-Helfer {#handlebars-helpers}

Eine Liste und Beschreibung der in SCF verfügbaren benutzerdefinierten Helfer finden Sie unter [SCF Handlebars Helpers](handlebars-helpers.md) .

## Clientseitiges Framework {#client-side-framework}

### Model-Ansicht Javascript Framework {#model-view-javascript-framework}

Das Framework umfasst eine Erweiterung von [Backbone.js](https://www.backbonejs.org/), einem JavaScript-Framework für Modellanwendungen, um die Entwicklung von Rich-Ansicht-Komponenten zu erleichtern. Die objektorientierte Natur unterstützt ein erweiterbares/wiederverwendbares Framework. Die Kommunikation zwischen Client und Server wird mithilfe der HTTP-API vereinfacht.

The framework leverages server side Handlebars templates to render the components for the client. The models are based on the JSON responses generated by the HTTP API. The views bind themselves to HTML generated by the Handlebars templates and provide interactivity.

### CSS Conventions {#css-conventions}

Die folgenden Konventionen werden zur Definition und Verwendung von CSS-Klassen empfohlen:

* Verwenden Sie eindeutig benannte CSS-Klassenselektornamen und vermeiden Sie generische Namen wie &quot;heading&quot;, &quot;image&quot;usw.
* Definieren Sie spezifische Stile für Klassenselektoren, damit die CSS-Stylesheets mit anderen Elementen und Stilen auf der Seite gut funktionieren. Beispiel: `.social-forum .topic-list .li { color: blue; }`
* Halten Sie CSS-Klassen für die Formatierung getrennt von CSS-Klassen für UX, die von JavaScript gesteuert werden.

### Clientseitige Anpassungen {#client-side-customizations}

Zum Anpassen des Erscheinungsbilds und Verhaltens einer Communities-Komponente auf Client-Seite verweisen Sie auf [clientseitige Anpassungen](client-customize.md), die Informationen zu folgenden Themen enthalten:

* [Überlagerungen](client-customize.md#overlays)
* [Extensions](client-customize.md#extensions)
* [HTML Markup](client-customize.md#htmlmarkup)
* [CSS-Skins](client-customize.md#skinning-css)
* [JavaScript erweitern](client-customize.md#extending-javascript)
* [Clientlibs für SCF](client-customize.md#clientlibs-for-scf)

## Funktionen und Komponenten {#feature-and-component-essentials}

Grundlegende Informationen für Entwickler finden Sie im Abschnitt [Funktionen und Komponenten](essentials.md) .

Weitere Entwicklerinformationen finden Sie im Abschnitt [Kodierungsrichtlinien](code-guide.md) .

## Fehlerbehebung {#troubleshooting}

Allgemeine Probleme und bekannte Probleme werden im Abschnitt [Fehlerbehebung](troubleshooting.md) beschrieben.

