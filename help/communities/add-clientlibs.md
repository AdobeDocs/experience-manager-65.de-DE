---
title: Clientlibs hinzufügen
description: Erfahren Sie, wie Sie einen ClientLibraryFolder (clientlibs) hinzufügen, der verwendet wird, um die JavaScript- und Cascading Style Sheets zu enthalten, die zum Rendern der Seiten Ihrer Site verwendet werden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 569f2052-b4fe-4f7f-aec9-657217cba091
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 7%

---

# Clientlibs hinzufügen {#add-clientlibs}

## Hinzufügen eines ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder mit dem Namen `clientlibs` enthält die JavaScript (JS)- und Cascading Styles Tabellen (CSS), die zum Rendern der Seiten Ihrer Site verwendet werden.

Die `categories` Der Eigenschaftswert, der dieser Client-Bibliothek zugewiesen wird, ist die Kennung, die verwendet wird, um diese Client-Bibliothek direkt von einer Inhaltsseite aus oder um sie in andere Client-Bibliotheken einzubetten.

1. Verwenden **CRXDE Lite**, erweitern `/etc/designs`

1. Rechtsklick `an-scf-sandbox` und wählen `Create Node`

   * Name : `clientlibs`
   * Typ : `cq:ClientLibraryFolder`

1. Klicken Sie auf **OK**

![add-client-library](assets/add-client-library.png)

Im **Eigenschaften** Registerkarte für die neue `clientlibs` Knoten, geben Sie die **categories** Eigenschaft:

* Name : **categories**
* Typ:**String**
* Wert : **apps.an-scf-sandbox**
* Klicken Sie auf **Hinzufügen**
* Klicken Sie auf **Alle speichern**

Hinweis: dem Kategoriewert &quot;apps&quot;voranstellen. ist eine Konvention, die die &#39;owning application&#39; als im Ordner /apps, nicht /libs identifiziert. WICHTIG: Platzhalter hinzufügen `js.tx`t und **`css.txt`** -Dateien. (Es handelt sich nicht offiziell um einen cq:ClientLibraryFolder ohne diese Ordner.)

1. Klicken Sie mit der rechten Maustaste **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Auswählen **Datei erstellen...**
1. Eingabe **Name:** `css.txt`
1. Auswählen **Datei erstellen...**
1. Eingabe **Name:** `js.txt`
1. Klicken Sie auf **Alle speichern**

![clientlibs-css](assets/clientlibs-css.png)

Die erste Zeile von css.txt und js.txt identifiziert den Basisspeicherort, von dem aus die folgenden Dateilisten zu finden sind.

Versuchen Sie, den Inhalt von css.txt auf

```
#base=.
 style.css
```

Erstellen Sie dann eine Datei unter clientlibs namens style.css und setzen Sie den Inhalt auf

`body {`

`background-color: #b0c4de;`

`}`

### Einbetten von SCF Clientlibs {#embed-scf-clientlibs}

Im **Eigenschaften** Registerkarte für die `clientlibs` Knoten, geben Sie die String-Eigenschaft mit mehreren Werten ein. **embed**. Dadurch werden die erforderlichen [Client-seitige Bibliotheken (clientlibs) für SCF-Komponenten](/help/communities/client-customize.md#clientlibs-for-scf). Für dieses Tutorial werden viele der clientlibs hinzugefügt, die für die Communities-Komponenten erforderlich sind.

Dies kann der gewünschte Ansatz für eine Produktions-Site sein oder auch nicht, da Überlegungen zur Benutzerfreundlichkeit im Vergleich zur Größe/Geschwindigkeit der für jede Seite heruntergeladenen Clientlibs vorliegen.

Wenn Sie nur eine Funktion auf einer Seite verwenden, können Sie die vollständige clientlib dieser Funktion direkt auf der Seite einfügen, z. B.

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In diesem Fall werden die einfacheren SCF-Clientlibs, die die Autoren-Clientlibs sind, einschließlich aller bevorzugt:

* Name : **`embed`**
* Typ : **`String`**
* Klicken Sie auf **`Multi`**
* Wert: **`cq.social.scf`**

   * Es wird ein Dialogfeld angezeigt, klicken Sie auf **`+`** nach jedem Eintrag, um die folgenden clientlib-Kategorien hinzuzufügen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Klicken Sie auf **OK**

* Klicken Sie auf **Alle speichern**

![scf-clientlibs](assets/scf-clientlibs.png)

So `/etc/designs/an-scf-sandbox/clientlibs` sollte nun im Repository angezeigt werden:

![scf-clientlibs-view](assets/scf-clientlibs1.png)

### Einschließen von Clientlibs in die PlayPage-Vorlage {#include-clientlibs-in-playpage-template}

Ohne Einbeziehung der `apps.an-scf-sandbox` ClientLibraryFolder auf der Seite verwenden, sind die SCF-Komponenten nicht funktionsfähig und formatiert, da die erforderlichen JavaScript- und CSS-Stile nicht verfügbar sind.

Ohne die clientlibs einschließen zu müssen, wird die SCF-Kommentar-Komponente beispielsweise nicht formatiert angezeigt:

![clientlibs-comment](assets/clientlibs-comment.png)

Sobald apps.an-scf-sandbox clientlibs enthalten ist, wird die SCF-Kommentar-Komponente formatiert angezeigt:

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

Die Include-Anweisung gehört in die `head` Abschnitt `html` Skript. Die Standardeinstellung **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie headlibs.jsp und fügen Sie clientlibs ein:**

1. Verwenden **CRXDE Lite** auswählen **`/libs/foundation/components/page/headlibs.jsp`**

1. Rechtsklicken Sie auf und wählen Sie **Kopieren** (oder wählen Sie in der Symbolleiste Kopieren aus)
1. Klicken Sie auf **`/apps/an-scf-sandbox/components/playpage`**
1. Rechtsklicken Sie auf und wählen Sie **Einfügen** (oder wählen Sie in der Symbolleiste Einfügen aus)
1. Doppelklicken **`headlibs.jsp`** damit Sie sie öffnen können
1. Hängen Sie die folgende Zeile an das Ende der Datei an
   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klicken Sie auf **Alle speichern**

```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Laden Sie Ihre Website in den Browser und überprüfen Sie, ob der Hintergrund kein Blau ist.

[https://localhost:4502/content/an-scf-sandbox/en/play.html](https://localhost:4502/content/an-scf-sandbox/en/play.html)

![community-play](assets/community-play.png)

### Ihre Arbeit bisher retten {#saving-your-work-so-far}

An dieser Stelle gibt es eine minimalistische Sandbox. Es kann sich lohnen, als Paket zu speichern, damit Sie während der Wiedergabe den Server ausschalten können, wenn Ihr Repository beschädigt wird und Sie einen Neustart durchführen möchten. Benennen oder löschen Sie dann den Ordner crx-quickstart/, schalten Sie Ihren Server ein, laden Sie dieses gespeicherte Paket hoch und installieren Sie es, und müssen Sie diese grundlegenden Schritte nicht wiederholen.

Dieses Paket befindet sich auf der [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) Tutorial für diejenigen, die nicht warten können, zu springen und zu spielen!...

So erstellen Sie ein Paket:

* Klicken Sie unter CRXDE Lite auf das [Paketsymbol](https://localhost:4502/crx/packmgr/)
* Klicken Sie auf **Paket erstellen**

   * Paketname: an-scf-sandbox-minimal-pkg
   * Version: 0.1
   * Gruppe: `leave as default`
   * Klicken Sie auf **OK**

* Klicken Sie auf **Bearbeiten**

   * Auswählen **Filter** tab

      * Klicks **Filter hinzufügen**
      * Stammpfad: navigieren Sie zu `/apps/an-scf-sandbox`
      * Klicken Sie auf **Fertig**
      * Klicks **Filter hinzufügen**
      * Stammpfad: navigieren Sie zu `/etc/designs/an-scf-sandbox`
      * Klicken Sie auf **Fertig**
      * Klicks **Filter hinzufügen**
      * Stammpfad: navigieren Sie zu `/content/an-scf-sandbox**`
      * Klicken Sie auf **Fertig**

   * Klicken Sie auf **Speichern**.

* Klicken Sie auf **Aufbauen**

Jetzt können Sie **Herunterladen** , um es auf der Festplatte zu speichern und **Paket hochladen** an einer anderen Stelle und wählen Sie **Mehr > Replizieren** , um die Sandbox an eine localhost-Veröffentlichungsinstanz zu senden, um den Bereich Ihrer Sandbox zu erweitern.
