---
title: hinzufügen Clientlibs
seo-title: hinzufügen Clientlibs
description: hinzufügen eines ClientLibraryFolder
seo-description: hinzufügen eines ClientLibraryFolder
uuid: 2944923d-caca-4607-81a4-4122a2ce8e41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 46f81c3f-6512-43f1-8ec1-cc717ab6f6ff
docset: aem65
translation-type: tm+mt
source-git-commit: fcdae5363e7a0070b5d6b76227e5c65efb71bc03
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 7%

---


# hinzufügen Clientlibs {#add-clientlibs}

## hinzufügen eines ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder mit dem Namen `clientlibs`, der die JS- und CSS-Dateien enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.

Der `categories`-Eigenschaftswert, der dieser Client-Bibliothek gegeben wird, ist der Bezeichner, der verwendet wird, um clientlib direkt von einer Inhaltsseite einzuschließen oder es in andere clientlibs einzubetten.

1. Erweitern Sie **CRXDE Lite**`/etc/designs`

1. Klicken Sie mit der rechten Maustaste auf `an-scf-sandbox` und wählen Sie `Create Node`

   * Name : `clientlibs`
   * Typ : `cq:ClientLibraryFolder`

1. Klicken Sie auf **OK**

![add-client-library](assets/add-client-library.png)

Geben Sie auf der Registerkarte **Properties** für den neuen Knoten `clientlibs` die Eigenschaft **Kategorien** ein:

* Name:**Kategorien**
* Typ:**String**
* Wert: **apps.an-scf-sandbox**
* Klicken Sie auf **Hinzufügen**
* Klicken Sie auf **Alle speichern**

Hinweis: dem Wert &quot;Kategorien&quot;mit &quot;Apps&quot;voranstellen. ist eine Konvention, die &#39;besitzende Anwendung&#39; als im Ordner /apps, nicht als /libs identifiziert.  WICHTIG: hinzufügen Platzhalter `js.tx`t- und **`css.txt`**-Dateien. (Es handelt sich nicht offiziell um cq:ClientLibraryFolder ohne diese.)

1. Klicken Sie mit der rechten Maustaste **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Wählen Sie **Datei erstellen...**
1. **Name:** `css.txt`
1. Wählen Sie **Datei erstellen...**
1. **Name:** `js.txt`
1. Klicken Sie auf **Alle speichern**

![clientlibs-css](assets/clientlibs-css.png)

Die erste Zeile der Dateien &quot;css.txt&quot;und &quot;js.txt&quot;gibt den Basisspeicherort an, von dem aus die folgenden Listen zu finden sind.

Versuchen Sie, den Inhalt von &quot;css.txt&quot;auf

```
#base=.
 style.css
```

Erstellen Sie dann eine Datei unter clientlibs mit dem Namen style.css und stellen Sie den Inhalt auf

`body {`

`background-color: #b0c4de;`

`}`

### SCF-Clientlibs {#embed-scf-clientlibs} einbetten

Geben Sie auf der Registerkarte **Eigenschaften** für den Knoten `clientlibs` die String-Eigenschaft mit mehreren Werten **embed** ein. Dadurch werden die erforderlichen [clientseitigen Bibliotheken (clientlibs) für SCF-Komponenten](/help/communities/client-customize.md#clientlibs-for-scf) eingebettet. Für dieses Tutorial werden viele der clientlibs hinzugefügt, die für die Communities-Komponenten erforderlich sind.

**Beachten Sie,** dass dies der gewünschte Ansatz für eine Produktionssite sein kann oder nicht, da es Hinweise zur Bequemlichkeit im Vergleich zur Größe/Geschwindigkeit der für jede Seite heruntergeladenen clientlibs gibt.

Wenn Sie nur eine Funktion auf einer Seite verwenden, könnten Sie die vollständige clientlib dieser Funktion direkt auf der Seite einfügen, z. B.

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In diesem Fall, einschließlich aller und so die einfacheren SCF clientlibs, die Autor clientlibs sind bevorzugt werden:

* Name: **`embed`**
* Typ : **`String`**
* Klicken Sie auf **`Multi`**
* Wert: **`cq.social.scf`**

   * Es erscheint ein Dialog,
Klicken Sie nach jedem Eintrag auf **`+`**, um die folgenden clientlib-Kategorien hinzuzufügen:

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

![scf-clientlibs-Ansicht](assets/scf-clientlibs1.png)

### Clientlibs in PlayPage-Vorlage einschließen {#include-clientlibs-in-playpage-template}

Ohne die `apps.an-scf-sandbox` ClientLibraryFolder-Kategorie auf der Seite einschließen zu müssen, sind die SCF-Komponenten nicht funktionsfähig oder gestylt, da die erforderlichen JavaScript(s) und Stile(s) nicht verfügbar sind.

Beispielsweise wird die Komponente &quot;SCF-Kommentare&quot;ohne Einbeziehung der clientlibs unformatiert angezeigt:

![clientlibs-comment](assets/clientlibs-comment.png)

Sobald apps.an-scf-sandbox clientlibs enthalten ist, wird die Komponente &quot;SCF-Kommentare&quot;mit einem Stil angezeigt:

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

Die include-Anweisung gehört zum Abschnitt `head` des Skripts `html`. Die Standardeinstellung **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie die Datei &quot;headlibs.jsp&quot;und schließen Sie clientlibs ein:**

1. Wählen Sie **CRXDE Lite** **`/libs/foundation/components/page/headlibs.jsp`**

1. Klicken Sie mit der rechten Maustaste und wählen Sie **Kopieren** (oder wählen Sie Kopieren aus der Symbolleiste)
1. Wählen Sie nun eine der folgenden Optionen aus **`/apps/an-scf-sandbox/components/playpage`**
1. Klicken Sie mit der rechten Maustaste und wählen Sie **Einfügen** (oder wählen Sie in der Symbolleiste Einfügen)
1. Dublette-Klicken Sie auf **`headlibs.jsp`**, um es zu öffnen
1. Fügen Sie die folgende Zeile an das Dateiende an
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

Laden Sie Ihre Website in den Browser und sehen Sie, ob der Hintergrund kein Schatten von Blau ist.

[https://localhost:4502/content/an-scf-sandbox/en/play.html](https://localhost:4502/content/an-scf-sandbox/en/play.html)

![community-play](assets/community-play.png)

### Speichern Ihrer Arbeit bisher {#saving-your-work-so-far}

An dieser Stelle gibt es eine minimalistische Sandbox, und es könnte sich lohnen, als Paket zu speichern, sodass Sie beim Abspielen, wenn Ihr Repository beschädigt wird und Sie Beginn verlieren möchten, Ihren Server ausschalten, umbenennen oder löschen können, Ihren Server einschalten, das gespeicherte Paket hochladen und installieren können, und nicht diese grundlegenden Schritte wiederholen müssen.

Dieses Paket existiert im Tutorial [Eine Beispielseite erstellen](/help/communities/create-sample-page.md) für diejenigen, die nicht darauf warten können, einfach hineinzuspringen und Beginn spielen!...

So erstellen Sie ein Paket:

* Klicken Sie in der CRXDE Lite auf das [Paketsymbol](https://localhost:4502/crx/packmgr/)
* Klicken Sie auf **Paket erstellen**

   * Paketname: an-scf-sandbox-minimal-pkg
   * Version: 0,1
   * Gruppe: `leave as default`
   * Klicken Sie auf **OK**

* Klicken Sie auf **Bearbeiten**.

   * Registerkarte **Filter** auswählen

      * Klicken Sie auf **Hinzufügen Filter**
      * Stammpfad: zu `/apps/an-scf-sandbox` navigieren
      * Klicken Sie auf **Fertig**
      * Klicken Sie auf **Hinzufügen Filter**
      * Stammpfad: zu `/etc/designs/an-scf-sandbox` navigieren
      * Klicken Sie auf **Fertig**
      * Klicken Sie auf **Hinzufügen Filter**
      * Stammpfad: zu `/content/an-scf-sandbox**` navigieren
      * Klicken Sie auf **Fertig**
   * Klicken Sie auf **Speichern**.


* Klicken Sie auf **Erstellen**

Jetzt können Sie **Download** auswählen, um es auf Festplatte und **Paket hochladen** an einer anderen Stelle zu speichern, und **Mehr > Replizieren** wählen, um die Sandbox auf eine localhost-Veröffentlichungsinstanz zu verschieben, um den Bereich Ihrer Sandbox zu erweitern.