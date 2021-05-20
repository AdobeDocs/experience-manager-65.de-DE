---
title: Clientlibs hinzufügen
seo-title: Clientlibs hinzufügen
description: Hinzufügen eines ClientLibraryFolder
seo-description: Hinzufügen eines ClientLibraryFolder
uuid: 2944923d-caca-4607-81a4-4122a2ce8e41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 46f81c3f-6512-43f1-8ec1-cc717ab6f6ff
docset: aem65
exl-id: 569f2052-b4fe-4f7f-aec9-657217cba091
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 7%

---

# Clientlibs hinzufügen {#add-clientlibs}

## Hinzufügen eines ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder mit dem Namen `clientlibs` , der die JS- und CSS-Dateien enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.

Der dieser Client-Bibliothek übergebene Eigenschaftswert `categories` ist der Bezeichner, der verwendet wird, um diese Client-Bibliothek direkt von einer Inhaltsseite aus oder in andere Client-Bibliotheken einzubetten.

1. Erweitern Sie `/etc/designs` mithilfe von **CRXDE Lite**.

1. Klicken Sie mit der rechten Maustaste auf `an-scf-sandbox` und wählen Sie `Create Node` aus.

   * Name : `clientlibs`
   * Typ : `cq:ClientLibraryFolder`

1. Klicken Sie auf **OK**

![add-client-library](assets/add-client-library.png)

Geben Sie auf der Registerkarte **Eigenschaften** für den neuen Knoten `clientlibs` die Eigenschaft **categories** ein:

* Name:**Kategorien**
* Typ:**String**
* Wert : **apps.an-scf-sandbox**
* Klicken Sie auf **Hinzufügen**
* Klicken Sie auf **Alle speichern**

Hinweis : dem Kategoriewert &quot;apps&quot;voranstellen. ist eine Konvention, die die &#39;owning application&#39; als im Ordner /apps, nicht /libs identifiziert.  WICHTIG : Fügen Sie Platzhalter für `js.tx`t- und **`css.txt`**-Dateien hinzu. (Es handelt sich nicht offiziell um einen cq:ClientLibraryFolder ohne diese Ordner.)

1. Klicken Sie mit der rechten Maustaste **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Wählen Sie **Datei erstellen...**
1. Geben Sie **Name:** `css.txt` ein.
1. Wählen Sie **Datei erstellen...**
1. Geben Sie **Name:** `js.txt` ein.
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

Geben Sie auf der Registerkarte **Eigenschaften** für den Knoten `clientlibs` die String-Eigenschaft mit mehreren Werten **embed** ein. Dadurch werden die erforderlichen [Client-seitigen Bibliotheken (clientlibs) für SCF-Komponenten](/help/communities/client-customize.md#clientlibs-for-scf) eingebettet. Für dieses Tutorial werden viele der clientlibs hinzugefügt, die für die Communities-Komponenten erforderlich sind.

**** Beachten Sie, dass dies möglicherweise der gewünschte Ansatz für eine Produktions-Site ist oder nicht, da Überlegungen zur Benutzerfreundlichkeit im Vergleich zur Größe/Geschwindigkeit der für jede Seite heruntergeladenen Clientlibs vorliegen.

Wenn Sie nur eine Funktion auf einer Seite verwenden, können Sie die vollständige clientlib dieser Funktion direkt auf der Seite einfügen, z. B.

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In diesem Fall werden die grundlegenden SCF-Clientlibs, die die Autoren-Clientlibs sind, einschließlich aller bevorzugt:

* Name : **`embed`**
* Typ : **`String`**
* Klicken Sie auf **`Multi`**
* Wert: **`cq.social.scf`**

   * Es wird ein Dialogfeld angezeigt,
Klicken Sie nach jedem Eintrag auf **`+`** , um die folgenden clientlib-Kategorien hinzuzufügen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Klicken Sie auf **OK**

* Klicken Sie auf **Alle speichern**

![scf-clientlibs](assets/scf-clientlibs.png)

So sollte `/etc/designs/an-scf-sandbox/clientlibs` jetzt im Repository angezeigt werden:

![scf-clientlibs-view](assets/scf-clientlibs1.png)

### Clientlibs in PlayPage-Vorlage einschließen {#include-clientlibs-in-playpage-template}

Ohne Einbeziehung der Kategorie `apps.an-scf-sandbox` ClientLibraryFolder auf der Seite sind die SCF-Komponenten nicht funktionsfähig und gestylt, da die erforderlichen JavaScript(s) und Stile(s) nicht verfügbar sind.

Ohne die clientlibs einschließen zu müssen, wird die SCF-Kommentar-Komponente beispielsweise nicht formatiert angezeigt:

![clientlibs-comment](assets/clientlibs-comment.png)

Sobald apps.an-scf-sandbox clientlibs enthalten ist, wird die SCF-Kommentar-Komponente formatiert angezeigt:

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

Die Include-Anweisung gehört zum Abschnitt `head` des Skripts `html` . Der Standard **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie headlibs.jsp und fügen Sie clientlibs ein:**

1. Wählen Sie **CRXDE Lite** **`/libs/foundation/components/page/headlibs.jsp`** aus.

1. Klicken Sie mit der rechten Maustaste und wählen Sie **Copy** (oder wählen Sie in der Symbolleiste die Option Kopieren aus)
1. Wählen Sie nun eine der folgenden Optionen aus **`/apps/an-scf-sandbox/components/playpage`**
1. Klicken Sie mit der rechten Maustaste und wählen Sie **Paste** aus (oder wählen Sie in der Symbolleiste Einfügen aus).
1. Doppelklicken Sie auf **`headlibs.jsp`** , um es zu öffnen.
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

### Speichern Sie Ihre Arbeit bisher {#saving-your-work-so-far}

An dieser Stelle gibt es eine minimalistische Sandbox, und es kann sich lohnen, als Paket zu speichern, damit Sie während der Wiedergabe den Ordner crx-quickstart/ deaktivieren, ihn hochladen und installieren können, wenn Ihr Repository beschädigt wird und Sie ihn neu starten möchten, den Server deaktivieren, umbenennen oder löschen, den Server einschalten, hochladen und installieren können und nicht diese grundlegendsten Schritte wiederholen müssen.

Dieses Paket existiert im Tutorial [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) für diejenigen, die nicht warten können, einfach hineinzuspringen und mit dem Spielen zu beginnen...

So erstellen Sie ein Paket:

* Klicken Sie in der CRXDE Lite auf das [Paketsymbol](https://localhost:4502/crx/packmgr/)
* Klicken Sie auf **Paket erstellen**

   * Paketname: an-scf-sandbox-minimal-pkg
   * Version: 0,1
   * Gruppe: `leave as default`
   * Klicken Sie auf **OK**

* Klicken Sie auf **Bearbeiten**.

   * Registerkarte **Filter** auswählen

      * Klicken Sie auf **Filter** hinzufügen
      * Stammpfad: zu `/apps/an-scf-sandbox` navigieren
      * Klicken Sie auf **Fertig**
      * Klicken Sie auf **Filter** hinzufügen
      * Stammpfad: zu `/etc/designs/an-scf-sandbox` navigieren
      * Klicken Sie auf **Fertig**
      * Klicken Sie auf **Filter** hinzufügen
      * Stammpfad: zu `/content/an-scf-sandbox**` navigieren
      * Klicken Sie auf **Fertig**
   * Klicken Sie auf **Speichern**.


* Klicken Sie auf **Erstellen**

Jetzt können Sie **Herunterladen** auswählen, um es auf der Festplatte und **Paket** an einer anderen Stelle hochzuladen, und **Mehr > Replizieren** auswählen, um die Sandbox an eine localhost-Veröffentlichungsinstanz zu senden, um den Bereich Ihrer Sandbox zu erweitern.
