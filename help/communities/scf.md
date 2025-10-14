---
title: Social Component Framework
description: Das Social Component Framework (SCF) vereinfacht das Konfigurieren, Anpassen und Erweitern von Communities-Komponenten
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 5ca58bc3-8505-4d91-9cd1-6b2e2671f1be
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1478'
ht-degree: 1%

---

# Social Component Framework {#social-component-framework}

Das Social Component Framework (SCF) vereinfacht die Konfiguration, Anpassung und Erweiterung von Communities-Komponenten sowohl auf Server- als auch auf Client-Seite.

Die Vorteile des Rahmens:

* **Funktionell**: Vorkonfigurierte, einfache Integration mit wenig oder keiner Anpassung für 80 % der Anwendungsfälle.
* **Skinnable**: Konsistente Verwendung von HTML-Attributen für CSS-Stile.
* **Erweiterbar**: Die Implementierung der Komponente ist objektorientiert und vereinfacht die Geschäftslogik - Sie können einfach inkrementelle Geschäftsanmeldungen auf dem Server hinzufügen.
* **Flexibel**: Einfache JavaScript-Vorlagen ohne Logik, die einfach überlagert und angepasst werden können.
* **Zugänglich**: Die HTTP-API unterstützt das Posten von jedem Client aus, einschließlich mobiler Apps.
* **Tragbar**: Integrieren/Einbetten in jede Web-Seite, die auf einer beliebigen Technologie basiert.

Erkunden Sie eine Autoren- oder Veröffentlichungsinstanz mit dem interaktiven [Handbuch für Community-Komponenten](components-guide.md).

## Überblick {#overview}

In SCF besteht eine Komponente aus einem SocialComponent-POJO, einer Handlebars-JS-Vorlage (zum Rendern der Komponente) und CSS (zum Gestalten der Komponente).

Eine Handlebars-JS-Vorlage kann die JS-Komponenten für das Modell/die Ansicht erweitern, um Benutzerinteraktionen mit der Komponente auf dem Client zu handhaben.

Wenn eine Komponente die Änderung von Daten unterstützen muss, kann die Implementierung der SocialComponent-API geschrieben werden, um das Bearbeiten/Speichern von Daten ähnlich dem Modell/den Datenobjekten in herkömmlichen Web-Anwendungen zu unterstützen. Darüber hinaus können Vorgänge (Controller) und ein Vorgangs-Service hinzugefügt werden, um Vorgangsanfragen zu verarbeiten, Geschäftslogik auszuführen und die APIs für das Modell/die Datenobjekte aufzurufen.

Die SocialComponent-API kann erweitert werden, um Daten bereitzustellen, die von einem Client für eine Ansichtsebene oder einen HTTP-Client benötigt werden.

### Wie Seiten für den Client gerendert werden {#how-pages-are-rendered-for-client}

![scf-page-rendering](assets/scf-overview.png)

### Komponentenanpassung und -erweiterung {#component-customization-and-extension}

Um die Komponenten anzupassen oder zu erweitern, schreiben Sie nur die Überlagerungen und Erweiterungen in Ihr Verzeichnis &quot;/apps“, was den Prozess der Aktualisierung auf zukünftige Versionen vereinfacht.

* Für die Enthäutung:
   * Nur [CSS muss bearbeitet werden](client-customize.md#skinning-css).
* Für Look-and-Feel:
   * Ändern Sie die JS-Vorlage und das CSS.
* Für Look-and-Feel und UX:
   * Ändern Sie die JS-Vorlage, das CSS und [JavaScript erweitern/überschreiben](client-customize.md#extending-javascript).
* So ändern Sie die für die JS-Vorlage oder den GET-Endpunkt verfügbaren Informationen:
   * Erweitern Sie die [SocialComponent](server-customize.md#socialcomponent-interface).
* So fügen Sie eine benutzerdefinierte Verarbeitung während der Vorgänge hinzu:
   * Schreiben Sie eine [OperationExtension](server-customize.md#operationextension-class).
* Hinzufügen eines benutzerdefinierten Vorgangs:
   * Erstellen Sie einen [Sling-POST-Vorgang](server-customize.md#postoperation-class).
   * Verwenden Sie [&#x200B; vorhandenen &#x200B;](server-customize.md#operationservice-class) nach Bedarf.
   * Fügen Sie JavaScript-Code hinzu, um Ihren Vorgang nach Bedarf Client-seitig aufzurufen.

## Server-seitiges Framework {#server-side-framework}

Das Framework stellt APIs für den Zugriff auf Funktionen auf dem Server bereit und unterstützt die Interaktion zwischen dem Client und dem Server.

### Java™-APIs {#java-apis}

Die Java™-APIs bieten abstrakte Klassen und Schnittstellen, die einfach vererbt oder unterklassifiziert werden können.

Die wichtigsten Klassen werden auf der Seite [Server-seitige Anpassung](server-customize.md) beschrieben.

Unter [Übersicht über den Speicherressourcenanbieter](srp.md) erfahren Sie mehr über die Arbeit mit benutzergenerierten Inhalten.

### HTTP-API {#http-api}

Die HTTP-API unterstützt die einfache Anpassung und Auswahl von Client-Plattformen für PhoneGap-Apps, native Apps und andere Integrationen und Mashups. Darüber hinaus ermöglicht die HTTP-API einer Community-Site, als Service ohne Client ausgeführt zu werden, sodass Framework-Komponenten in jede Web-Seite integriert werden können, die auf einer beliebigen Technologie basiert.

### HTTP-API - GET-Anfragen {#http-api-get-requests}

Für jede SocialComponent stellt das Framework einen HTTP-basierten API-Endpunkt bereit. Auf den Endpunkt wird zugegriffen, indem eine GET-Anfrage mit einem &quot;.social.json“-Selektor und einer Erweiterung an die Ressource gesendet wird. Mit Sling wird die Anfrage an den -`DefaultSocialGetServlet` übergeben.

**`DefaultSocialGetServlet`**

1. Übergibt die Ressource (resourceType) an den `SocialComponentFactoryManager` und empfängt eine SocialComponentFactory, die einen `SocialComponent` auswählen kann, der die Ressource darstellt.

1. Ruft die Factory auf und empfängt ein `SocialComponent`, das die Ressource und die Anfrage verarbeiten kann.
1. Ruft die `SocialComponent` auf, die die Anfrage verarbeitet und eine JSON-Darstellung der Ergebnisse zurückgibt.
1. Gibt die JSON-Antwort an den Client zurück.

**`GET Request`**

Ein standardmäßiges GET-Servlet überwacht .social.json-Anfragen, auf die die SocialComponent mit anpassbarem JSON antwortet.

![SCF-Framework](assets/scf-framework.png)

### HTTP-API - POST-Anfragen {#http-api-post-requests}

Zusätzlich zu den GET-(Lese-)Vorgängen definiert das Framework ein Endpunktmuster, um andere Vorgänge für eine Komponente zu aktivieren, einschließlich Erstellen, Aktualisieren und Löschen. Diese Endpunkte sind HTTP-APIs, die Eingaben akzeptieren und entweder mit einem HTTP-Status-Code oder mit einem JSON-Antwortobjekt antworten.

Dieses Framework-Endpunktmuster macht CUD-Vorgänge erweiterbar, wiederverwendbar und testbar.

**`POST Request`**

Für jeden SocialComponent-Vorgang gibt es einen Sling-Vorgang POST:operation . Die Geschäftslogik und der Wartungscode für jeden Vorgang werden in einen OperationService eingeschlossen, auf den über die HTTP-API oder von einer anderen Stelle aus als OSGi-Dienst zugegriffen werden kann. Hooks unterstützen Plug-In-Operationserweiterungen für Vor-/Nachher-Aktionen.

![SCF nach Anfrage](assets/scf-post-request.png)

### Speicherressourcenanbieter (SRP) {#storage-resource-provider-srp}

Weitere Informationen zum Umgang mit im [Community Content Store](working-with-srp.md) gespeicherten benutzergenerierten Inhalten finden Sie unter:

* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP API-Dienstprogrammmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.

### Server-seitige Anpassungen {#server-side-customizations}

Unter [Server-seitige Anpassungen](server-customize.md) finden Sie Informationen zum Anpassen der Geschäftslogik und des Verhaltens einer Communities-Komponente auf der Server-Seite.

## Handlebars JS-Vorlagensprache {#handlebars-js-templating-language}

Eine der auffälligsten Änderungen im neuen Framework ist die Verwendung der `Handlebars JS` (HBS)-Vorlagensprache, einer beliebten Open-Source-Technologie für das Server-Client-Rendering.

HBS-Skripte sind einfach, ohne Logik, auf Server und Client kompiliert, einfach zu überlagern und anzupassen und natürlich an die Client-Benutzeroberfläche zu binden, da HBS das Client-seitige Rendering unterstützt.

Das Framework stellt mehrere [Handlebars-Helper](handlebars-helpers.md) bereit, die bei der Entwicklung von SocialComponents nützlich sind.

Wenn Sling eine GET-Anfrage auflöst, identifiziert es auf dem Server das Skript, das verwendet wird, um auf die Anfrage zu reagieren. Wenn es sich bei dem Skript um eine HBS-Vorlage (.hbs) handelt, delegiert Sling die Anfrage an die Handlebars-Engine. Die Handlebars-Engine ruft dann die SocialComponent aus der entsprechenden SocialComponentFactory ab, erstellt einen Kontext und rendert die HTML.

### Keine Zugriffsbeschränkung {#no-access-restriction}

Handlebars-Vorlagendateien (HBS) (.hbs) sind analog zu .jsp- und .html-Vorlagendateien, mit der Ausnahme, dass sie zum Rendern sowohl im Client-Browser als auch auf dem Server verwendet werden können. Daher erhält ein Client-Browser, der eine Client-seitige Vorlage anfordert, eine HBS-Datei vom Server.

Dazu müssen alle HBS-Vorlagen im Sling-Suchpfad (alle .hbs-Dateien unter /libs/ oder /apps) von jedem Benutzer aus der Autoren- oder Veröffentlichungsinstanz abgerufen werden können.

Der HTTP-Zugriff auf HBS-Dateien darf nicht verboten werden.

### Hinzufügen oder Einschließen einer Communities-Komponente {#add-or-include-a-communities-component}

Die meisten Communitys-Komponenten müssen *Sling-*-Ressource hinzugefügt werden. Einige ausgewählte Communitys-Komponenten können *enthalten* als nicht vorhandene Ressource in einer Vorlage enthalten sein, um eine dynamische Einbeziehung und Anpassung des Speicherorts zu ermöglichen, an dem benutzergenerierte Inhalte (User-Generated Content, UGC) geschrieben werden sollen.

In beiden Fällen müssen die [erforderlichen Client-Bibliotheken](clientlibs.md) der Komponente ebenfalls vorhanden sein.

**Komponente hinzufügen**

Das Hinzufügen einer Komponente bezieht sich auf den Prozess des Hinzufügens einer Instanz einer Ressource (Komponente), z. B. wenn sie im Autorenbearbeitungsmodus aus dem Komponenten-Browser (Sidekick) auf eine Seite gezogen wird.

Das Ergebnis ist ein untergeordneter JCR-Knoten unter einem para-Knoten, der Sling-adressierbar ist.

**Komponente einschließen**

Das Einschließen einer Komponente bezieht sich auf den Prozess des Hinzufügens eines Verweises zu einer [&#x200B; „nicht vorhandenen“ Ressource](srp.md#for-non-existing-resources-ners) (kein JCR-Knoten) innerhalb der Vorlage, z. B. mithilfe einer Skriptsprache.

Ab Adobe Experience Manager (AEM) 6.1 ist es möglich, die Eigenschaften der Komponente im Authoring-(Design)-Modus zu bearbeiten, wenn eine Komponente dynamisch eingefügt *hinzugefügt*.

Nur einige wenige AEM Communities-Komponenten können dynamisch eingebunden werden. Sie sind:

* [Kommentare](essentials-comments.md)
* [Bewertung](rating-basics.md)
* [Bewertungen](reviews-basics.md)
* [Abstimmung](essentials-voting.md)

Das [Community-Komponentenhandbuch](components-guide.md) ermöglicht das Umschalten zwischen dem Hinzufügen und Einschließen von einschließbaren Komponenten.

**Bei Verwendung der**-Vorlagensprache von Handlebars wird die nicht vorhandene Ressource mithilfe des [include helper) eingeschlossen, &#x200B;](handlebars-helpers.md#include) Sie ihren resourceType angeben:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Bei Verwendung von JSP** wird eine Ressource mit dem Tag [cq:include](../../help/sites-developing/taglib.md#lt-cq-include):

```
<cq:include path="votes"
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Informationen dazu, wie Sie einer Seite dynamisch eine Komponente hinzufügen können, anstatt sie einer Vorlage hinzuzufügen oder in eine Vorlage einzuschließen, finden Sie unter [Komponenten-Seitenladen](sideloading.md).

### Handlebars-Helfer {#handlebars-helpers}

Eine Liste [&#x200B; benutzerdefinierten Helper, die in SCF verfügbar &#x200B;](handlebars-helpers.md), finden Sie unter „SCF Handlebars Helpers“.

## Client-seitiges Framework {#client-side-framework}

### Modellansicht JavaScript Framework {#model-view-javascript-framework}

Das Framework beinhaltet eine Erweiterung von [Backbone.js](https://backbonejs.org/), einem modellbasierten JavaScript-Framework, um die Entwicklung komplexer, interaktiver Komponenten zu erleichtern. Die objektorientierte Natur unterstützt ein erweiterbares/wiederverwendbares Framework. Die Kommunikation zwischen Client und Server wird mit der HTTP-API vereinfacht.

Das Framework verwendet Server-seitige Handlebars-Vorlagen zum Rendern der Komponenten für den Client. Die Modelle basieren auf den von der HTTP-API generierten JSON-Antworten. Die Ansichten verbinden sich mit dem von den Handlebars-Vorlagen generierten HTML und bieten Interaktivität.

### CSS-Konventionen {#css-conventions}

Im Folgenden finden Sie empfohlene Konventionen zum Definieren und Verwenden von CSS-Klassen:

* Verwenden Sie CSS-Klassenselektornamen mit klarem Namespace und vermeiden Sie generische Namen wie „Überschrift“ und „Bild“.
* Definieren Sie bestimmte Klassenauswahlstile, damit die CSS-Stylesheets gut mit anderen Elementen und Stilen auf der Seite zusammenarbeiten. Beispiel: `.social-forum .topic-list .li { color: blue; }`
* Behalten Sie die CSS-Klassen für die Formatierung getrennt von den CSS-Klassen für UX bei, die von JavaScript gesteuert werden.

### Client-seitige Anpassungen {#client-side-customizations}

Um das Erscheinungsbild und Verhalten einer Communities-Komponente Client-seitig anzupassen, verweisen Sie auf [Client-seitige Anpassungen](client-customize.md), die Informationen zu folgenden Themen enthalten:

* [Überlagerungen](client-customize.md#overlays)
* [Erweiterungen](client-customize.md#extensions)
* [HTML-Markup](client-customize.md#htmlmarkup)
* [CSS wird skindern](client-customize.md#skinning-css)
* [Erweitern von JavaScript](client-customize.md#extending-javascript)
* [Clientlibs für SCF](client-customize.md#clientlibs-for-scf)

## Grundlegende Funktionen und Komponenten {#feature-and-component-essentials}

Wesentliche Informationen für Entwickler werden im Abschnitt [Funktionen und Komponenten-Grundlagen](essentials.md) beschrieben.

Weitere Informationen für Entwickler finden Sie im Abschnitt [Kodierrichtlinien](code-guide.md) .

## Fehlerbehebung {#troubleshooting}

Häufige Probleme und bekannte Probleme werden im Abschnitt [Fehlerbehebung](troubleshooting.md) beschrieben.
