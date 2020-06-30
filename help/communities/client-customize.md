---
title: Clientseitige Anpassung
seo-title: Clientseitige Anpassung
description: Anpassen des Verhaltens oder Erscheinungsbilds clientseitig in AEM Communities
seo-description: Anpassen des Verhaltens oder Erscheinungsbilds clientseitig in AEM Communities
uuid: 57978c39-9a8a-4098-9001-c8bbe7ee786f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 24b6d1d2-c118-4a25-959f-2783961c4ae3
translation-type: tm+mt
source-git-commit: efa6c7be93908b2f264da4689caa9c02912c0f0a
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---


# Clientseitige Anpassung  {#client-side-customization}

| **[⇐ Essentials](essentials.md)** | **[Serverseitige Anpassung ⇒](server-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers ⇒](handlebars-helpers.md)** |

Zum Anpassen des Erscheinungsbilds und/oder Verhaltens einer AEM Communities-Komponente auf Clientseite gibt es mehrere Ansätze.

Zwei Hauptansätze sind das Überlagern oder Erweitern einer Komponente.

[Durch das Überlagern](#overlays) einer Komponente wird die Standardkomponente geändert und wirkt sich auf jeden Verweis auf die Komponente aus.

[Die Erweiterung](#extensions) einer Komponente, die eindeutig benannt ist, schränkt den Umfang der Änderungen ein. Der Begriff &quot;Erweiterung&quot; wird synonym mit &quot;Außerkraftsetzen&quot; verwendet.

## Überlagerungen {#overlays}

Das Überlagern einer Komponente ist eine Methode, um Änderungen an einer Standardkomponente vorzunehmen, die alle Instanzen betreffen, die den Standard verwenden.

Die Überlagerung erfolgt durch Ändern einer Kopie der Standardkomponente im Ordner &quot;/**apps** &quot;, anstatt die Originalkomponente im Ordner &quot;/**libs** &quot;zu ändern. Die Komponente wird mit einem identischen relativen Pfad erstellt, außer &#39;libs&#39; wird durch &#39;apps&#39; ersetzt.

Der Ordner &quot;/apps&quot;ist der erste Ort, der zum Auflösen von Anforderungen gesucht wird. Wenn er nicht gefunden wird, wird die Standardversion im Ordner &quot;/libs&quot;verwendet.

Die Standardkomponente im Verzeichnis /libs darf nie geändert werden, da zukünftige Patches und Upgrades das Verzeichnis /libs auf jede erforderliche Weise ändern können, während öffentliche Schnittstellen beibehalten werden.

Dies unterscheidet sich von der [Erweiterung](#extensions) einer Standardkomponente, bei der Änderungen für eine bestimmte Verwendung vorgenommen werden sollen, wobei ein eindeutiger Pfad zur Komponente erstellt wird und die ursprüngliche Standardkomponente im Verzeichnis /libs als Super-Ressourcentyp referenziert wird.

Ein kurzes Beispiel für das Überlagern der Komponente &quot;Kommentare&quot;finden Sie im Lernprogramm &quot; [Überlagerungskommentare&quot;](overlay-comments.md).

## Erweiterungen {#extensions}

Das Erweitern (Überschreiben) einer Komponente ist eine Methode, um Änderungen für eine bestimmte Verwendung vorzunehmen, ohne dass alle Instanzen betroffen sind, die den Standard verwenden. Die erweiterte Komponente ist eindeutig im Ordner /apps benannt und verweist auf die Standardkomponente im Ordner /libs. Daher werden Standarddesign und Standardverhalten einer Komponente nicht geändert.

Dies unterscheidet sich von der [Überlagerung](#overlays) der Standardkomponente, bei der die Art von Sling relative Verweise auf den Ordner apps/ auflöst, bevor der Ordner libs/ gesucht wird. Daher wird das Design oder Verhalten einer Komponente global geändert.

Ein kurzes Beispiel zum Erweitern der Komponente &quot;Kommentare&quot;finden Sie im Tutorial [Kommentarkomponente](extend-comments.md)erweitern.

## JavaScript-Bindung {#javascript-binding}

Das HBS-Skript für die Komponente muss an die JavaScript-Objekte, -Modelle und -Ansichten gebunden sein, die diese Funktion implementieren.

Der Wert des `data-scf-component` Attributs kann der Standardwert sein, z. B. **`social/tally/components/hbs/rating`** oder eine erweiterte (benutzerdefinierte) Komponente für benutzerdefinierte Funktionen, wie z. B. **Kleinschreibung/Komponenten/hbs/Bewertung**.

Um eine Komponente zu binden, muss das gesamte Komponentenskript in ein &lt;div>-Element mit den folgenden Attributen eingeschlossen sein:

* `data-component-id`=&quot;{{id}}&quot;

   löst die ID-Eigenschaft aus dem Kontext auf

* `data-scf-component`=&quot;*&lt;resourceType>*

Beispiel `/apps/weretail/components/hbs/rating/rating.hbs`:

```xml
<div class="we-Rating" data-component-id="{{id}}" data-scf-component="weretail/components/hbs/rating">

     <!-- HTML with HBS accessing the rating component -->

</div>
```

## Benutzerdefinierte Eigenschaften {#custom-properties}

Beim Erweitern oder Überlagern einer Komponente können Eigenschaften zu einem geänderten Dialogfeld hinzugefügt werden.

Auf alle Eigenschaften, die für eine Komponente/Ressource festgelegt sind, kann über die Eigenschaftenschlüssel in der Vorlage für die Symbolleisten zugegriffen werden:

`{{properties.<property_name>}}`

## CSS-Skins {#skinning-css}

Die Anpassung der Komponenten an das allgemeine Thema der Website kann durch &quot;Skin&quot; erreicht werden - durch eine Änderung der Farben, Schriftarten, Bilder, Schaltflächen, Links, Abstände und sogar Positionierung in einem bestimmten Umfang.

Skins lassen sich durch selektives Überschreiben der Rahmenstile oder durch komplett neue Stylesheets erzielen. Die SCF-Komponenten definieren namensespaced-, module- und semantische CSS-Klassen, die die verschiedenen Elemente einer Komponente beeinflussen.

So legen Sie eine Komponente als Skin fest:

1. Identifizieren Sie die Elemente, die Sie ändern möchten (z. B. Komponentenbereich, Symbolleistenschaltflächen, Meldungsart usw.).
1. Identifizieren Sie die CSS-Klasse/die CSS-Regeln, die sich auf diese Elemente auswirken.
1. Erstellen Sie eine Stylesheet-Datei (.css).
1. Schließen Sie das Stylesheet in einen Client-Bibliotheksordner ([clientlibs](#clientlibs-for-scf)) für Ihre Site ein und stellen Sie sicher, dass es in Ihren Vorlagen und Seiten mit [ui:includeClientLib](../../help/sites-developing/clientlibs.md)enthalten ist.

1. Definieren Sie die CSS-Klassen und -Regeln, die Sie im Stylesheet identifiziert haben (#2), neu und fügen Sie Stile hinzu.

Die benutzerdefinierten Stile überschreiben jetzt die standardmäßigen Rahmenstile und die Komponente wird mit der neuen Skin gerendert.

>[!CAUTION]
>
>Jeder CSS-Klassenname, dem ein Präfix vorangestellt wird, `scf-js` hat eine bestimmte Verwendung im JavaScript-Code. Diese Klassen wirken sich auf den Status einer Komponente aus (z. B. Umschalten von ausgeblendet zu sichtbar) und sollten weder überschrieben noch entfernt werden.
>
>Obwohl die `scf-js` Klassen keine Auswirkungen auf Stile haben, können die Klassennamen in Stylesheets mit dem Vorbehalt verwendet werden, dass, da sie die Status von Elementen steuern, es möglicherweise Nebenwirkungen geben kann.


## JavaScript erweitern {#extending-javascript}

Um eine JavaScript-Implementierung der Komponenten zu erweitern, müssen Sie:

1. Erstellen Sie eine Komponente für Ihre App, deren Wert &quot;jcr:resourceSuperType&quot;auf den Wert &quot;jcr:resourceType&quot;der erweiterten Komponente gesetzt ist, z. B. &quot;social/forum/components/hbs/forum&quot;.
1. Prüfen Sie das Javascript der Standardkomponente der SCF, um zu bestimmen, welche Methoden mit SCF.registerComponent() registriert werden müssen.
1. Kopieren Sie entweder das JavaScript oder den Beginn der erweiterten Komponente von Grund auf.
1. Erweitern Sie die Methode.
1. Verwenden Sie SCF.registerComponent(), um alle Methoden entweder mit den Standardwerten oder den angepassten Objekten und Ansichten zu registrieren.

### forum.js: Beispielerweiterung des Forums - HBS  {#forum-js-sample-extension-of-forum-hbs}

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

Skript-Tags sind ein wesentlicher Bestandteil des clientseitigen Frameworks. Sie sind der Klebstoff, der dazu beiträgt, das auf dem Server generierte Markup mit den Modellen und Ansichten auf dem Client zu verbinden.

Skript-Tags in SCF-Skripten sollten beim Überlagern oder Überschreiben von Komponenten nicht entfernt werden. SCF-Skript-Tags, die automatisch für die JSON-Injektion in HTML erstellt wurden, werden mit dem Attribut identifiziert `data-scf-json=true`.

## Clientlibs für SCF {#clientlibs-for-scf}

Die Verwendung [clientseitiger Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) bietet eine Möglichkeit, JavaScript und CSS zu organisieren und zu optimieren, die zum Rendern von Inhalten auf dem Client verwendet werden.

Die clientlibs für SCF folgen einem sehr spezifischen Benennungsmuster für zwei Varianten, die nur durch das Vorhandensein von &quot;author&quot;im Namen der Kategorie variieren:

| Clientlib-Variante | Muster für Eigenschaft &quot;Kategorien&quot; |
|--- |--- |
| complete clientlib | cq.social.hbs.&lt;Name der Komponente> |
| author clientlib | cq.social.author.hbs.&lt;Name der Komponente> |

### Vollständige Clientlibs {#complete-clientlibs}

Die vollständigen clientlibs (ohne Autor) beinhalten Abhängigkeiten und eignen sich ideal für die Verwendung mit ui:includeClientLib.

Diese Versionen finden Sie unter:

* `/etc/clientlibs/social/hbs/&lt;component name&gt;`

Beispiel:

* Client-Ordnerknoten: `/etc/clientlibs/social/hbs/forum`
* Eigenschaft &quot;Kategorien&quot;: `cq.social.hbs.forum`

Im Handbuch [&quot;](components-guide.md) Community-Komponenten&quot;werden die vollständigen clientlibs für jede SCF-Komponente Liste.

[clientlibs for Communities Components](clientlibs.md) beschreibt, wie Sie einer Seite clientlibs hinzufügen.

### Autor-Clientlibs {#author-clientlibs}

Die Autorenversion clientlibs wird auf das für die Implementierung der Komponente erforderliche JavaScript-Minimum reduziert.

Diese clientlibs sollten niemals direkt eingeschlossen werden, sondern stehen stattdessen zur Einbettung in andere clientlibs zur Verfügung, die für eine Site handgefertigt sind.

Diese Versionen befinden sich im Ordner &quot;SCF libs&quot;:

* `/libs/social/&lt;feature&gt;/components/hbs/&lt;component name&gt;/clientlibs`

Beispiel:

* Client-Ordnerknoten: `/libs/social/forum/hbs/forum/clientlibs`
* Eigenschaft &quot;Kategorien&quot;: `cq.social.author.hbs.forum`

Hinweis: Während Autor clientlibs nie andere Bibliotheken einbetten, machen sie Liste ihre Abhängigkeiten. Wenn sie in andere Bibliotheken eingebettet sind, werden die Abhängigkeiten nicht automatisch eingezogen und müssen auch eingebettet werden.

Die erforderlichen Autoren-clientlibs können identifiziert werden, indem Sie &quot;author&quot;in die clientlibs einfügen, die für jede SCF-Komponente im Handbuch [Community-Komponenten aufgeführt sind](components-guide.md).

### Überlegungen zur Nutzung {#usage-considerations}

Jede Website ist anders, wenn es darum geht, Client-Bibliotheken zu verwalten. Zu den verschiedenen Faktoren gehören:

* Gesamtgeschwindigkeit: Vielleicht möchten Sie, dass die Site reagiert, aber es ist akzeptabel, dass die erste Seite etwas langsam geladen wird. Wenn viele der Seiten dasselbe Javascript verwenden, können die verschiedenen Javascripts in eine clientlib eingebettet und von der ersten zu ladenden Seite aus referenziert werden. Das Javascript in diesem einzelnen Download bleibt zwischengespeichert, wodurch die Menge der herunterzuladenden Daten für nachfolgende Seiten minimiert wird.
* Kurzzeit bis zur ersten Seite: Vielleicht möchten Sie, dass die erste Seite schnell geladen wird. In diesem Fall befindet sich das Javascript in mehreren kleinen Dateien, auf die nur bei Bedarf verwiesen werden kann.
* Ein Gleichgewicht zwischen dem ersten Laden der Seite und nachfolgenden Downloads.

| **[⇐ Essentials](essentials.md)** | **[Serverseitige Anpassung ⇒](server-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers ⇒](handlebars-helpers.md)** |

