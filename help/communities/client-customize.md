---
title: Client-seitige Anpassung
description: Client-seitiges Anpassen des Verhaltens oder Erscheinungsbilds in AEM Communities
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: bf34f564-ac93-4c8c-95f7-8690d99d85cb
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---

# Client-seitige Anpassung  {#client-side-customization}

| **[⇐ Feature Essentials](essentials.md)** | **[Server-seitige ⇒](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers ⇒](handlebars-helpers.md)** |

Um das Erscheinungsbild und/oder Verhalten einer AEM Communities-Komponente Client-seitig anzupassen, gibt es mehrere Ansätze.

Zwei Hauptansätze bestehen darin, eine Komponente zu überlagern oder zu erweitern.

[Überlagern](#overlays) Eine Komponente ändert die Standardkomponente und wirkt sich auf jeden Verweis auf die Komponente aus.

[Erweitern](#extensions) Eine Komponente mit eindeutigem Namen begrenzt den Umfang der Änderungen. Der Begriff „Verlängern“ wird synonym mit „Überschreiben“ verwendet.

## Überlagerungen {#overlays}

Das Überlagern einer Komponente ist eine Methode zum Ändern einer Standardkomponente und wirkt sich auf alle Instanzen aus, die die Standardkomponente verwenden.

Die Überlagerung erfolgt durch Ändern einer Kopie der Standardkomponente im Verzeichnis /**apps** anstatt durch Ändern der ursprünglichen Komponente im Verzeichnis /**libs**. Die Komponente wird mit einem identischen relativen Pfad erstellt, mit der Ausnahme, dass „libs“ durch „apps“ ersetzt wird.

Der Ordner &quot;/apps“ ist der erste Ort, an dem gesucht wird, um Anfragen zu beheben. Wenn er nicht gefunden wird, wird die Standardversion im Ordner &quot;/libs“ verwendet.

Die Standardkomponente im Verzeichnis /libs darf niemals geändert werden, da zukünftige Patches und Upgrades das Verzeichnis /libs bei Aufrechterhaltung öffentlicher Schnittstellen in beliebiger Weise ändern können.

Dies unterscheidet sich von [Erweitern](#extensions) einer Standardkomponente, bei der Änderungen für einen bestimmten Zweck vorgenommen werden sollen, ein eindeutiger Pfad zur Komponente erstellt wird und auf die ursprüngliche Standardkomponente im Verzeichnis /libs als übergeordneten Ressourcentyp verwiesen wird.

Ein schnelles Beispiel für das Überlagern der Kommentarkomponente finden Sie im Tutorial [Überlagerungskommentarkomponente](overlay-comments.md).

## Erweiterungen {#extensions}

Das Erweitern (Überschreiben) einer Komponente ist eine Methode, um Änderungen für eine bestimmte Verwendung vorzunehmen, ohne dass sich dies auf alle Instanzen auswirkt, die die Standardeinstellung verwenden. Die erweiterte Komponente hat einen eindeutigen Namen im Ordner &quot;/apps“ und verweist auf die Standardkomponente im Ordner &quot;/libs“, sodass das Standarddesign und -verhalten einer Komponente nicht geändert wird.

Dies unterscheidet sich von [Überlagerung](#overlays) der Standardkomponente, bei der die Natur von Sling relative Verweise auf die Programme/Ordner auflöst, bevor im Ordner „libs/&quot; gesucht wird, sodass das Design oder Verhalten einer Komponente global geändert wird.

Ein kurzes Beispiel für die Erweiterung der Kommentarkomponente finden Sie im Tutorial [Kommentarkomponente erweitern](extend-comments.md).

## JavaScript-Bindung {#javascript-binding}

Das HBS-Skript für die Komponente muss an die JavaScript-Objekte, -Modelle und -Ansichten gebunden sein, die diese Funktion implementieren.

Der Wert des `data-scf-component` kann der Standardwert sein, z. B. **`social/tally/components/hbs/rating`**, oder eine erweiterte (angepasste) Komponente für angepasste Funktionen wie **weretail/components/hbs/rating**.

Um eine Komponente zu binden, muss das gesamte Komponentenskript in ein &lt;div>-Element mit den folgenden Attributen eingeschlossen werden:

* `data-component-id`=&quot;`{{id}}`&quot;

  löst die ID-Eigenschaft aus dem Kontext auf

* `data-scf-component`=&quot;*&lt;resourceType>*

Zum Beispiel von `/apps/weretail/components/hbs/rating/rating.hbs`:

```xml
<div class="we-Rating" data-component-id="`{{id}}`" data-scf-component="weretail/components/hbs/rating">

     <!-- HTML with HBS accessing the rating component -->

</div>
```

## Benutzerdefinierte Eigenschaften {#custom-properties}

Beim Erweitern oder Überlagern einer Komponente ist es möglich, Eigenschaften zu einem geänderten Dialogfeld hinzuzufügen.

Sie können auf alle Eigenschaften einer Komponente/Ressource zugreifen, indem Sie auf die Eigenschaftsschlüssel in der Handlebars-Vorlage verweisen:

`{{properties.<property_name>}}`

## CSS wird skindern {#skinning-css}

Die Anpassung von Komponenten an das allgemeine Design der Website kann durch „Skinning“ erreicht werden - Änderung von Farben, Schriftarten, Bildern, Schaltflächen, Links, Abständen und sogar Positionierung in einem gewissen Umfang.

Die Hautextrusion kann durch selektives Überschreiben der Framework-Stile oder durch das Schreiben völlig neuer Stylesheets erreicht werden. Die SCF-Komponenten definieren CSS-Klassen mit Namespace, Modular und Semantik, die sich auf die verschiedenen Elemente auswirken, aus denen eine Komponente besteht.

So hauten Sie eine Komponente ein:

1. Identifizieren Sie die Elemente, die Sie ändern möchten (z. B. Composer-Bereich, Symbolleistenschaltflächen, Nachrichtenschriftart usw.).
1. Identifizieren Sie die CSS-Klasse/-Regeln, die diese Elemente beeinflussen.
1. Erstellen Sie eine Stylesheet-Datei (.css).
1. Fügen Sie das Stylesheet in einen Client-Bibliotheksordner ([clientlibs](#clientlibs-for-scf)) für Ihre Site ein und stellen Sie sicher, dass es in Ihren Vorlagen und Seiten mit [ui:includeClientLib](../../help/sites-developing/clientlibs.md) enthalten ist.

1. Definieren Sie die CSS-Klassen und -Regeln neu, die Sie in Ihrem Stylesheet identifiziert (#2) haben, und fügen Sie Stile hinzu.

Die benutzerdefinierten Stile setzen jetzt die Standard-Framework-Stile außer Kraft und die Komponente wird mit dem neuen Design gerendert.

>[!CAUTION]
>
>Jeder CSS-Klassenname, dem das Präfix `scf-js` vorangestellt ist, hat eine bestimmte Verwendung im JavaScript-Code. Diese Klassen beeinflussen den Status einer Komponente (z. B. von ausgeblendet zu sichtbar umschalten) und sollten weder überschrieben noch entfernt werden.
>
>Während die `scf-js` Klassen keine Auswirkungen auf Stile haben, können die Klassennamen in Stylesheets verwendet werden, mit dem Vorbehalt, dass es bei der Steuerung des Zustands von Elementen zu Nebenwirkungen kommen kann.

## Erweitern von JavaScript {#extending-javascript}

Um eine JavaScript-Implementierung von zu erweitern, ist Folgendes erforderlich:

1. Erstellen Sie eine Komponente für Ihre App, wobei für „jcr:resourceSuperType“ der Wert des „jcr:resourceType“ der erweiterten Komponente festgelegt ist, z. B. social/forum/components/hbs/forum.
1. Untersuchen Sie die JavaScript der standardmäßigen SCF-Komponente, um festzustellen, welche Methoden mit SCF.registerComponent() registriert werden müssen.
1. Kopieren Sie entweder die JavaScript der erweiterten Komponente oder beginnen Sie von Grund auf neu.
1. Erweitern Sie die Methode .
1. Verwenden Sie SCF.registerComponent(), um alle Methoden mit den Standardwerten oder den benutzerdefinierten Objekten und Ansichten zu registrieren.

### forum.js: Beispielerweiterung von Forum - HBS  {#forum-js-sample-extension-of-forum-hbs}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";
    var GMForumView = SCF.ForumView.extend({
        viewName: "GMForum",
        showComposer: function(e) {
            SCF.ForumView.prototype.toggleComposer.apply(this);
            var cancel = this.$el.find('.cancel-new-topic');
            cancel.toggle();
        },
        hideComposer: function(e) {
            SCF.ForumView.prototype.toggleComposer.apply(this);
            var cancel = this.$el.find('.cancel-new-topic');
            cancel.toggle();
        }
    });

    SCF.registerComponent('social/forum/components/hbs/post', SCF.Post, SCF.PostView);
    SCF.registerComponent('social/forum/components/hbs/topic', SCF.Topic, SCF.TopicView);
    SCF.registerComponent('social/forum/components/hbs/forum', SCF.Forum, GMForumView );
})($CQ, _, Backbone, SCF);
```

## Skript-Tags {#script-tags}

Skript-Tags sind ein inhärenter Bestandteil des Client-seitigen Frameworks. Sie sind der Kleber, der dabei hilft, das auf der Server-Seite generierte Markup mit den Modellen und Ansichten auf der Client-Seite zu verbinden.

Skript-Tags in SCF-Skripten sollten beim Überlagern oder Überschreiben von Komponenten nicht entfernt werden. SCF-Skript-Tags, die automatisch für das Einfügen von JSON in die HTML erstellt wurden, werden mit dem Attribut `data-scf-json=true` gekennzeichnet.

## Clientlibs für SCF {#clientlibs-for-scf}

Die Verwendung [ Client-seitigen ](../../help/sites-developing/clientlibs.md) (clientlibs) bietet eine Möglichkeit, die JavaScript und CSS, die zum Rendern von Inhalten auf dem Client verwendet werden, zu organisieren und zu optimieren.

Die Client-Bibliotheken für SCF folgen einem sehr spezifischen Benennungsmuster für zwei Varianten, die nur durch das Vorhandensein von „author“ im Kategorienamen variieren:

| Clientlib-Variante | Muster für Kategorieneigenschaft |
|--- |--- |
| Vollständige Clientlib | cq.social.hbs.&lt;Komponentenname> |
| Autoren-Clientlib | cq.social.author.hbs.&lt;Komponentenname> |

### Vollständige Clientlibs {#complete-clientlibs}

Die vollständigen (Nicht-Autoren-)Client-Bibliotheken enthalten Abhängigkeiten und eignen sich bequem zum Einschließen in ui:includeClientLib.

Diese Versionen befinden sich in:

* `/etc/clientlibs/social/hbs/&lt;component name&gt;`

Zum Beispiel:

* Client-Ordnerknoten: `/etc/clientlibs/social/hbs/forum`
* Kategorieneigenschaft: `cq.social.hbs.forum`

Das [Handbuch für Community-Komponenten](components-guide.md) listet die vollständigen Client-Bibliotheken auf, die für jede SCF-Komponente erforderlich sind.

[Clientlibs für Communities-Komponenten](clientlibs.md) beschreibt, wie einer Seite Clientlibs hinzugefügt werden.

### Autoren-Clientlibs {#author-clientlibs}

Die Client-Bibliotheken der Autorenversion werden auf das Minimum von JavaScript reduziert, das zur Implementierung der Komponente erforderlich ist.

Diese Client-Bibliotheken sollten niemals direkt eingeschlossen werden, sondern können stattdessen in andere Client-Bibliotheken eingebettet werden, die für eine Site handgefertigt werden.

Diese Versionen befinden sich im Ordner „SCF libs“:

* `/libs/social/&lt;feature&gt;/components/hbs/&lt;component name&gt;/clientlibs`

Zum Beispiel:

* Client-Ordnerknoten: `/libs/social/forum/hbs/forum/clientlibs`
* Kategorieneigenschaft: `cq.social.author.hbs.forum`

Hinweis: Während Autoren-Client-Bibliotheken nie andere Bibliotheken einbetten, listen sie ihre Abhängigkeiten auf. Wenn die Abhängigkeiten in andere Bibliotheken eingebettet werden, werden sie nicht automatisch abgerufen und müssen ebenfalls eingebettet werden.

Die erforderlichen Autoren-Client-Bibliotheken können identifiziert werden, indem „author“ in die Client-Bibliotheken eingefügt wird, die für jede SCF-Komponente im [Community-Komponentenhandbuch“ aufgeführt ](components-guide.md).

### Überlegungen zur Verwendung {#usage-considerations}

Jede Site unterscheidet sich in der Verwaltung von Client-Bibliotheken. Zu den verschiedenen Faktoren gehören:

* Gesamtgeschwindigkeit: Möglicherweise ist es wünschenswert, dass die Site responsiv ist, aber es ist akzeptabel, dass die erste Seite etwas langsam geladen wird. Wenn viele Seiten dieselbe JavaScript verwenden, können die verschiedenen JavaScript in eine Client-Bibliothek eingebettet und von der ersten zu ladenden Seite aus referenziert werden. Die JavaScript in diesem einzelnen Download bleibt zwischengespeichert, wodurch die Datenmenge, die für nachfolgende Seiten heruntergeladen werden soll, minimiert wird.
* Kurze Zeit bis zur ersten Seite: Möglicherweise möchten Sie, dass die erste Seite schnell geladen wird. In diesem Fall befindet sich die JavaScript in mehreren kleinen Dateien, auf die nur bei Bedarf verwiesen werden kann.
* Ein Gleichgewicht zwischen dem ersten Laden der Seite und nachfolgenden Downloads.

| **[⇐ Feature Essentials](essentials.md)** | **[Server-seitige ⇒](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers ⇒](handlebars-helpers.md)** |
