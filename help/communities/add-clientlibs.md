---
title: Clientlibs hinzufügen
description: Erfahren Sie, wie Sie einen ClientLibraryFolder (clientlibs) hinzufügen, der die JavaScript und kaskadierenden Stylesheets enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 569f2052-b4fe-4f7f-aec9-657217cba091
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Clientlibs hinzufügen {#add-clientlibs}

## Hinzufügen eines Client-Bibliotheksordners (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder mit dem Namen `clientlibs`, der die JavaScript (JS)- und Cascading Stylesheets (CSS) enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.

Der dieser Client-Bibliothek übergebene `categories`-Eigenschaftswert ist die Kennung, die verwendet wird, um diese Client-Bibliothek direkt von einer Inhaltsseite einzuschließen oder sie in andere Client-Bibliotheken einzubetten.

1. Mit **CRXDE Lite** erweitern Sie `/etc/designs`

1. Klicken Sie mit der rechten Maustaste auf `an-scf-sandbox` und wählen Sie `Create Node`

   * Name : `clientlibs`
   * Typ : `cq:ClientLibraryFolder`

1. Klicken Sie auf **OK**

![add-client-library](assets/add-client-library.png)

Geben Sie auf **Registerkarte** Eigenschaften“ für den neuen `clientlibs` die Eigenschaft **Kategorien** ein:

* Name : **categories**
* Typ : **Zeichenfolge**
* Wert : **apps.an-scf-sandbox**
* Klicken Sie auf **Hinzufügen**
* Klicken Sie **Alle speichern**

Hinweis: Stellen Sie dem Kategoriewert das Präfix „apps“ voran. ist eine Konvention, um festzulegen, dass sich die „besitzende Anwendung“ im Ordner &quot;/apps“ und nicht in &quot;/libs“ befindet. WICHTIG: Fügen Sie Platzhalterdateien `js.tx` und **`css.txt`**. (Es handelt sich hierbei nicht um einen offiziellen cq:ClientLibraryFolder ohne sie.)

1. Rechtsklick auf **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Wählen Sie **Datei erstellen…**
1. Enter **name:** `css.txt`
1. Wählen Sie **Datei erstellen…**
1. Enter **name:** `js.txt`
1. Klicken Sie **Alle speichern**

![clientlibs-css](assets/clientlibs-css.png)

Die erste Zeile von css.txt und js.txt gibt den Basisspeicherort an, von dem aus die folgenden Dateilisten zu finden sind.

Versuchen Sie, den Inhalt von css.txt auf Folgendes festzulegen

```
#base=.
 style.css
```

Erstellen Sie dann unter „clientlibs“ eine Datei mit dem Namen „style.css“ und legen Sie den Inhalt auf fest.

`body {`

`background-color: #b0c4de;`

`}`

### SCF-Clientlibs einbetten {#embed-scf-clientlibs}

Geben **auf der** „Eigenschaften“ für den `clientlibs` die String-Eigenschaft mit mehreren Werten ein **embed**. Dadurch werden die erforderlichen [Client-seitigen Bibliotheken (clientlibs) für SCF-Komponenten &#x200B;](/help/communities/client-customize.md#clientlibs-for-scf). In diesem Tutorial werden viele der Client-Bibliotheken hinzugefügt, die für die Communities-Komponenten erforderlich sind.

Dies kann der gewünschte Ansatz für eine Produktions-Site sein, muss aber nicht, da es Überlegungen zur Benutzerfreundlichkeit im Verhältnis zur Größe/Geschwindigkeit der heruntergeladenen Clientlibs für jede Seite gibt.

Wenn Sie nur eine Funktion auf einer Seite verwenden, können Sie die vollständige Clientlib dieser Funktion direkt auf der Seite einfügen, z. B.

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In diesem Fall, einschließlich aller , werden die einfacheren SCF-Client-Bibliotheken, bei denen es sich um die Autoren-Client-Bibliotheken handelt, bevorzugt:

* Name : **`embed`**
* Typ : **`String`**
* **`Multi`** klicken
* Wert: **`cq.social.scf`**

   * Es wird ein Dialogfeld angezeigt,
Klicken Sie nach jedem Eintrag auf **`+`** , um die folgenden Clientlib-Kategorien hinzuzufügen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Klicken Sie auf **OK**

* Klicken Sie **Alle speichern**

![scf-clientlibs](assets/scf-clientlibs.png)

So sollten `/etc/designs/an-scf-sandbox/clientlibs` jetzt im Repository angezeigt werden:

![scf-clientlibs-view](assets/scf-clientlibs1.png)

### Clientlibs in PlayPage-Vorlage einschließen {#include-clientlibs-in-playpage-template}

Ohne Einbeziehung der `apps.an-scf-sandbox` ClientLibraryFolder -Kategorie auf der Seite sind die SCF-Komponenten nicht funktionsfähig und auch nicht für die Formatierung geeignet, da die erforderlichen JavaScript- und CSS-Stile nicht verfügbar sind.

Ohne Client-Bibliotheken zum Beispiel erscheint die Komponente „SCF-Kommentare“ unformatiert:

![clientlibs-comment](assets/clientlibs-comment.png)

Sobald apps.js-scf-sandbox-clientlibs eingeschlossen ist, erscheint die Komponente SCF-Kommentare mit dem Stil :

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

Die Include-Anweisung gehört in den `head` des `html`. Die **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie „headlibs.jsp“ und schließen Sie clientlibs:** ein

1. Wählen Sie mithilfe von **&#x200B;**&#x200B;CRXDE Lite **`/libs/foundation/components/page/headlibs.jsp`**

1. Klicken Sie mit der rechten Maustaste und wählen **Kopieren** (oder wählen Sie Kopieren in der Symbolleiste)
1. Klicken Sie auf **`/apps/an-scf-sandbox/components/playpage`**
1. Klicken Sie mit der rechten Maustaste und wählen **Einfügen** (oder wählen Sie Einfügen aus der Symbolleiste)
1. Doppelklicken Sie auf **`headlibs.jsp`** , um es zu öffnen
1. Hängen Sie die folgende Zeile an das Ende der Datei an
   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klicken Sie **Alle speichern**

```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Laden Sie Ihre Website im Browser und prüfen Sie, ob der Hintergrund kein Blautöne aufweist.

[https://localhost:4502/content/an-scf-sandbox/en/play.html](https://localhost:4502/content/an-scf-sandbox/en/play.html)

![Community-Play](assets/community-play.png)

### Speichern Sie Ihre bisherige Arbeit {#saving-your-work-so-far}

An diesem Punkt gibt es eine minimalistische Sandbox. Es könnte sich lohnen, ihn als Paket zu speichern, sodass Sie Ihren Server während der Wiedergabe ausschalten können, wenn Ihr Repository beschädigt wird und Sie von vorne beginnen möchten. Benennen oder löschen Sie dann den Ordner „crx-quickstart/&quot;, schalten Sie Ihren Server ein, laden Sie dieses gespeicherte Paket hoch und installieren Sie es, und müssen Sie nicht die grundlegendsten Schritte wiederholen.

Dieses Paket ist im Tutorial [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) für diejenigen enthalten, die nicht warten können, bis sie loslegen und mit der Wiedergabe beginnen.

So erstellen Sie ein Paket:

* Klicken Sie auf dem CRXDE Lite auf [Paketsymbol](https://localhost:4502/crx/packmgr/)
* Klicken Sie auf **Paket erstellen**

   * Paketname: an-scf-sandbox-minimal-pkg
   * Version: 0.1
   * Gruppe: `leave as default`
   * Klicken Sie auf **OK**

* Klicken Sie auf **Bearbeiten**

   * Wählen Sie **Registerkarte** Filter“

      * Klicken Sie **Filter hinzufügen**
      * Stammverzeichnis: Navigieren Sie zu `/apps/an-scf-sandbox`
      * Klicken Sie auf **Fertig**.
      * Klicken Sie **Filter hinzufügen**
      * Stammverzeichnis: Navigieren Sie zu `/etc/designs/an-scf-sandbox`
      * Klicken Sie auf **Fertig**.
      * Klicken Sie **Filter hinzufügen**
      * Stammverzeichnis: Navigieren Sie zu `/content/an-scf-sandbox**`
      * Klicken Sie auf **Fertig**.

   * Klicken Sie auf **Speichern**.

* Klicken Sie auf **Erstellen**

Jetzt können Sie auf **Herunterladen** klicken, um die Sandbox auf der Festplatte zu speichern und **Paket hochzuladen** und auf **Mehr > Replizieren** klicken, um die Sandbox auf eine localhost-Veröffentlichungsinstanz zu pushen und den Bereich Ihrer Sandbox zu erweitern.
