---
title: Clientseitige Anpassung
description: Clientseitiges Verhalten oder Erscheinungsbild in AEM Communities anpassen
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

# Clientseitige Anpassung  {#client-side-customization}

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Serverseitige Anpassung](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

Um das Erscheinungsbild und/oder Verhalten einer AEM Communities-Komponente Client-seitig anzupassen, gibt es mehrere Ansätze.

Zwei Hauptansätze sind das Überlagern oder Erweitern einer Komponente.

[Überlagern](#overlays): Eine Komponente ändert die Standardkomponente und wirkt sich auf jeden Verweis auf die Komponente aus.

[Die Erweiterung](#extensions) einer Komponente, die eindeutig benannt ist, beschränkt den Umfang der Änderungen. Der Begriff &quot;Erweiterung&quot;wird synonym mit &quot;Überschreibung&quot;verwendet.

## Überlagerungen {#overlays}

Das Überlagern einer Komponente ist eine Methode, Änderungen an einer Standardkomponente vorzunehmen und alle Instanzen zu betreffen, die den Standard verwenden.

Die Überlagerung erfolgt durch Ändern einer Kopie der Standardkomponente im Verzeichnis /**apps** , anstatt die Originalkomponente im Verzeichnis /**libs** zu ändern. Die Komponente wird mit einem identischen relativen Pfad erstellt, mit der Ausnahme, dass &quot;libs&quot;durch &quot;apps&quot;ersetzt wird.

Das Verzeichnis /apps ist der erste Ort, der zum Auflösen von Anforderungen gesucht wird. Wenn es nicht gefunden wird, wird die Standardversion im Verzeichnis /libs verwendet.

Die Standardkomponente im Verzeichnis /libs darf nie geändert werden, da zukünftige Patches und Upgrades das Verzeichnis /libs auf jede erforderliche Weise ändern können, während öffentliche Schnittstellen beibehalten werden.

Dies unterscheidet sich von [Erweitern](#extensions) einer Standardkomponente, bei der Änderungen für eine bestimmte Verwendung vorgenommen werden sollen, indem ein eindeutiger Pfad zur Komponente erstellt wird und auf die Referenzierung der ursprünglichen Standardkomponente im Verzeichnis /libs als Superressourcentyp zurückgegriffen wird.

Ein kurzes Beispiel für das Überlagern der Kommentarkomponente finden Sie im Tutorial [Kommentar-Komponente überlagern](overlay-comments.md) .

## Erweiterungen {#extensions}

Das Erweitern (Überschreiben) einer Komponente ist eine Methode, um Änderungen für einen bestimmten Verwendungszweck vorzunehmen, ohne dass sich dies auf alle Instanzen auswirkt, die den Standard verwenden. Die erweiterte Komponente ist eindeutig im Ordner /apps benannt und verweist auf die Standardkomponente im Ordner /libs . Daher werden das Standarddesign und -verhalten einer Komponente nicht geändert.

Dies unterscheidet sich von [overlay](#overlays) der Standardkomponente, bei der die Art von Sling relative Verweise auf den Ordner apps/ auflöst, bevor die Suche im Ordner libs/ stattfindet. Daher wird das Design oder Verhalten einer Komponente global geändert.

Ein kurzes Beispiel für die Erweiterung der Kommentarkomponente finden Sie im Tutorial [Kommentar-Komponente erweitern](extend-comments.md) .

## JavaScript-Bindung {#javascript-binding}

Das HBS-Skript für die Komponente muss an die JavaScript-Objekte, -Modelle und -Ansichten gebunden sein, die diese Funktion implementieren.

Der Wert des Attributs `data-scf-component` kann der Standardwert wie **`social/tally/components/hbs/rating`** oder eine erweiterte (angepasste) Komponente für benutzerdefinierte Funktionen wie **weretail/components/hbs/rating** sein.

Um eine Komponente zu binden, muss das gesamte Komponentenskript in ein &lt;div> -Element mit den folgenden Attributen eingeschlossen sein:

* `data-component-id`=&quot;`{{id}}`&quot;

  wird aus dem Kontext in die ID-Eigenschaft aufgelöst

* `data-scf-component`=&quot;*&lt;resourceType>*

Beispiel: von `/apps/weretail/components/hbs/rating/rating.hbs`:

```xml
<div class="we-Rating" data-component-id="`{{id}}`" data-scf-component="weretail/components/hbs/rating">

     <!-- HTML with HBS accessing the rating component -->

</div>
```

## Benutzerdefinierte Eigenschaften {#custom-properties}

Beim Erweitern oder Überlagern einer Komponente können Eigenschaften zu einem geänderten Dialogfeld hinzugefügt werden.

Auf alle Eigenschaften einer Komponente/Ressource kann über die Eigenschaftenschlüssel in der Handlebars-Vorlage zugegriffen werden:

`{{properties.<property_name>}}`

## Gestalten von CSS {#skinning-css}

Das Anpassen von Komponenten an das allgemeine Thema der Website kann durch eine &quot;Skinning&quot;-Funktion erreicht werden - das Ändern von Farben, Schriftarten, Bildern, Schaltflächen, Links, Abständen und sogar der Positionierung in einem bestimmten Umfang.

Skinning kann durch selektives Überschreiben der Framework-Stile oder durch Schreiben völlig neuer Stylesheets erreicht werden. Die SCF-Komponenten definieren Namespace-, modulare und semantische CSS-Klassen, die sich auf die verschiedenen Elemente auswirken, aus denen eine Komponente besteht.

So erstellen Sie eine Komponente:

1. Identifizieren Sie die Elemente, die Sie ändern möchten (z. B. Komponentenbereich, Symbolleistenschaltflächen, Nachrichtenschriftart usw.).
1. Identifizieren Sie die CSS-Klasse(n), die sich auf diese Elemente auswirkt.
1. Erstellen Sie eine Stylesheet-Datei (.css).
1. Schließen Sie das Stylesheet in einen Client-Bibliotheksordner ([clientlibs](#clientlibs-for-scf)) für Ihre Site ein und stellen Sie sicher, dass es aus Ihren Vorlagen und Seiten mit [ui:includeClientLib](../../help/sites-developing/clientlibs.md) enthalten ist.

1. Definieren Sie die CSS-Klassen und Regeln, die Sie in Ihrem Stylesheet (#2) identifiziert haben, neu und fügen Sie Stile hinzu.

Die benutzerdefinierten Stile überschreiben jetzt die standardmäßigen Framework-Stile und die Komponente wird mit der neuen Skin gerendert.

>[!CAUTION]
>
>Jeder CSS-Klassenname, dem `scf-js` vorangestellt ist, hat eine bestimmte Verwendung im JavaScript-Code. Diese Klassen wirken sich auf den Status einer Komponente aus (z. B. Umschalten von ausgeblendet auf sichtbar) und sollten weder überschrieben noch entfernt werden.
>
>Auch wenn die `scf-js` -Klassen keine Auswirkungen auf Stile haben, können die Klassennamen in Stylesheets mit dem Vorbehalt verwendet werden, dass es bei der Kontrolle der Status von Elementen möglicherweise zu Nebenwirkungen kommt.

## Erweitern von JavaScript {#extending-javascript}

Um eine JavaScript-Implementierung der Komponenten zu erweitern, gehen Sie folgendermaßen vor:

1. Erstellen Sie eine Komponente für Ihre App, deren jcr:resourceSuperType auf den Wert des jcr:resourceType der erweiterten Komponente festgelegt ist, z. B. social/forum/components/hbs/forum.
1. Untersuchen Sie die JavaScript der standardmäßigen SCF-Komponente, um festzustellen, welche Methoden mit SCF.registerComponent() registriert werden müssen.
1. Kopieren Sie entweder die JavaScript der erweiterten Komponente oder beginnen Sie von Grund auf neu.
1. Erweitern Sie die -Methode.
1. Verwenden Sie SCF.registerComponent() , um alle Methoden entweder mit den Standardeinstellungen oder mit den angepassten Objekten und Ansichten zu registrieren.

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

Skript-Tags sind ein wesentlicher Bestandteil des clientseitigen Frameworks. Sie sind der Kleber, der dazu beiträgt, das auf der Server-Seite generierte Markup mit den Modellen und Ansichten auf der Client-Seite zu binden.

Skript-Tags in SCF-Skripten sollten beim Überlagern oder Überschreiben von Komponenten nicht entfernt werden. SCF-Skript-Tags, die automatisch zum Einfügen von JSON in die HTML erstellt werden, werden mit dem Attribut `data-scf-json=true` identifiziert.

## Clientlibs für SCF {#clientlibs-for-scf}

Die Verwendung von [clientseitigen Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) bietet eine Möglichkeit, die JavaScript und das CSS, die zum Rendern von Inhalten auf dem Client verwendet werden, zu organisieren und zu optimieren.

Die clientlibs für SCF folgen einem sehr spezifischen Benennungsmuster für zwei Varianten, die nur durch das Vorhandensein von &quot;author&quot;im Kategorienamen variieren:

| Clientlib-Variante | Muster für Kategorieneigenschaft |
|--- |--- |
| complete clientlib | cq.social.hbs.&lt;Komponentenname> |
| author clientlib | cq.social.author.hbs.&lt;Komponentenname> |

### Vollständige Clientlibs {#complete-clientlibs}

Die vollständigen clientlibs (ohne Autoreninstanz) enthalten Abhängigkeiten und sind für die Verwendung mit ui:includeClientLib praktisch.

Diese Versionen finden Sie unter:

* `/etc/clientlibs/social/hbs/&lt;component name&gt;`

Zum Beispiel:

* Client-Ordnerknoten: `/etc/clientlibs/social/hbs/forum`
* Kategorieneigenschaft: `cq.social.hbs.forum`

Im [Handbuch zu Community-Komponenten](components-guide.md) werden die vollständigen clientlibs aufgelistet, die für jede SCF-Komponente erforderlich sind.

[Clientlibs für Communities-Komponenten](clientlibs.md) beschreibt, wie Clientlibs zu einer Seite hinzugefügt werden.

### Autor-Clientlibs {#author-clientlibs}

Die clientlibs für die Autorenversion werden auf das für die Implementierung der Komponente erforderliche Mindestmaß an JavaScript heruntergefahren.

Diese Client-seitigen Bibliotheken sollten niemals direkt eingeschlossen werden, sondern stehen stattdessen zur Einbettung in andere Client-Bibliotheken zur Verfügung, die für eine Site handgefertigt sind.

Diese Versionen befinden sich im Ordner &quot;SCF libs&quot;:

* `/libs/social/&lt;feature&gt;/components/hbs/&lt;component name&gt;/clientlibs`

Zum Beispiel:

* Client-Ordnerknoten: `/libs/social/forum/hbs/forum/clientlibs`
* Kategorieneigenschaft: `cq.social.author.hbs.forum`

Hinweis: Während Client-Bibliotheken von Autoren nie andere Bibliotheken einbetten, werden ihre Abhängigkeiten aufgelistet. Wenn sie in andere Bibliotheken eingebettet sind, werden die Abhängigkeiten nicht automatisch abgerufen und müssen auch eingebettet werden.

Die erforderlichen Autoren-Client-Bibliotheken können identifiziert werden, indem &quot;author&quot;in die clientlibs eingefügt wird, die für jede SCF-Komponente im [Handbuch zu Community-Komponenten](components-guide.md) aufgelistet sind.

### Überlegungen zur Verwendung {#usage-considerations}

Jede Site verwaltet Client-Bibliotheken anders. Verschiedene Faktoren sind:

* Gesamtgeschwindigkeit: Vielleicht ist der Wunsch, dass die Site responsiv ist, aber es ist akzeptabel, dass die erste Seite etwas langsam geladen wird. Wenn viele Seiten dieselbe JavaScript verwenden, können die verschiedenen JavaScript in eine Client-Bibliothek eingebettet und von der ersten zu ladenden Seite aus referenziert werden. Die JavaScript in diesem einzigen Download bleibt zwischengespeichert, wodurch die Menge der herunterzuladenden Daten für nachfolgende Seiten minimiert wird.
* Short Time to First Page: Vielleicht ist der Wunsch, dass die erste Seite schnell geladen wird. In diesem Fall befindet sich die JavaScript in mehreren kleinen Dateien, auf die nur bei Bedarf verwiesen wird.
* Ein Gleichgewicht zwischen dem ersten Seitenladevorgang und nachfolgenden Downloads.

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Serverseitige Anpassung](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |
