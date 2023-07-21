---
title: Erstellen einer vollständigen Website (JSP)
description: In diesem Tutorial erfahren Sie, wie Sie mit Adobe Experience Manager (AEM) eine Website mit vollem Funktionsumfang erstellen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: d7cf843c-c837-4b97-b6c5-0fbd6793bdd4
source-git-commit: a56d5121a6ce11b42a6c30dae9e479564d16af27
workflow-type: tm+mt
source-wordcount: '4941'
ht-degree: 45%

---

# Erstellen einer vollständigen Website (JSP){#create-a-fully-featured-website-jsp}

>[!NOTE]
>
>In diesem Artikel wird beschrieben, wie Sie eine Website mit JSP erstellen und auf der klassischen Benutzeroberfläche basieren. Adobe empfiehlt die Verwendung der neuesten Adobe Experience Manager-AEM (Technologien) für Ihre Websites, wie im Artikel ausführlich beschrieben [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md).

In diesem Tutorial können Sie eine Website mit vollständigen Funktionen mit AEM erstellen. Die Website basiert auf einer generischen Website und ist in erster Linie auf Webentwickler ausgerichtet. Die gesamte Entwicklung erfolgt in einer Autorenumgebung.

In diesem Tutorial wird Folgendes beschrieben:

1. Installieren Sie AEM.
1. Zugreifen auf CRXDE Lite (die Entwicklungsumgebung)
1. Einrichten der Projektstruktur in CRXDE Lite
1. Erstellen Sie die Vorlage, die Komponente und die Skripte, die als Grundlage für die Erstellung von Inhaltsseiten verwendet werden.
1. Erstellen Sie die Stammseite für Ihre Website und dann Inhaltsseiten.
1. Erstellen der folgenden Komponenten zur Verwendung auf den Seiten

   * topnav (Navigation oben)
   * listchildren (Untergeordnete Elemente auflisten)
   * Logo
   * Bild
   * textimage (Textbild)
   * Suchen

1. Fügen Sie verschiedene Foundation-Komponenten ein.

Nachdem Sie alle Schritte ausgeführt haben, sollten Ihre Seiten wie folgt aussehen:

![chlimage_1-24](assets/chlimage_1-24.png)

**Endergebnis herunterladen**

Laden Sie website-1.0.zip herunter, um dem Tutorial anstatt der Übungen zu folgen. Diese Datei ist ein AEM Inhaltspaket, das die Ergebnisse dieses Tutorials enthält. Verwendung [Package Manager](/help/sites-administering/package-manager.md) , um das Paket in Ihrer Autoreninstanz zu installieren.

**HINWEIS:** Bei der Installation dieses Pakets werden alle Ressourcen in Ihrer Authoring-Instanz überschrieben, die Sie mithilfe dieses Tutorials erstellt haben.

Website-Inhaltspaket

[Datei laden](assets/website-1_0.zip)

## Installieren von Adobe Experience Manager {#installing-adobe-experience-manager}

Um eine AEM-Instanz für die Entwicklung Ihrer Website zu installieren, folgen Sie den Anweisungen zum Einrichten einer [Bereitstellungsumgebung mit Erstellungs- und Veröffentlichungsinstanzen](/help/sites-deploying/deploy.md#author-and-publish-installs) oder nehmen Sie eine [allgemeine Installation](/help/sites-deploying/deploy.md#default-local-install) vor. Im Zuge einer allgemeinen Installation laden Sie die Quickstart-JAR-Datei von AEM herunter und speichern die Datei license.properties im selben Verzeichnis wie die JAR-Datei. Anschließend doppelklicken Sie auf die JAR-Datei.

Nachdem Sie AEM installiert haben, greifen Sie auf die CRXDE Lite-Entwicklungsumgebung zu, indem Sie auf der Begrüßungsseite auf den Link für CRXDE Lite klicken:

![chlimage_1-25](assets/chlimage_1-25.png)

>[!NOTE]
>
>Die URL von CRXDE Lite für eine AEM-Autoreninstanz, die lokal unter Verwendung des Standard-Ports installiert wird, lautet [https://localhost:4502/crx/de/](https://localhost:4502/crx/de/).

### Einrichten der Projektstruktur in CRXDE Lite {#setting-up-the-project-structure-in-crxde-lite}

Verwenden Sie die CRXDE Lite, um die Anwendungsstruktur von mywebsite im Repository zu erstellen:

1. Klicken Sie in der Baumstruktur links in CRXDE Lite mit der rechten Maustaste auf den Ordner **`/apps`** und klicken Sie dann auf **Erstellen** > **Ordner** **erstellen**. Geben Sie im Dialogfeld **Ordner erstellen** als Ordnernamen `mywebsite` ein und klicken Sie auf **OK**.
1. Klicken Sie mit der rechten Maustaste auf den Ordner **`/apps/mywebsite`** und klicken Sie dann auf **Erstellen** > **Ordner erstellen**. Geben Sie im Dialogfeld **Ordner erstellen** als Ordnernamen `components` ein und klicken Sie auf **OK**.
1. Klicken Sie mit der rechten Maustaste auf den Ordner **`/apps/mywebsite`** und klicken Sie dann auf **Erstellen** > **Ordner erstellen**. Geben Sie im Dialogfeld **Ordner erstellen** als Ordnernamen `templates` ein und klicken Sie auf **OK**.

   Die Struktur im Baum sollte nun in etwa so aussehen:

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Klicken Sie auf **Alle speichern**.

### Einrichten des Designs {#setting-up-the-design}

In diesem Abschnitt erstellen Sie das Design für Ihre Anwendung mit dem Designer-Tool. Das Design stellt CSS- und Bildressourcen für Ihre Website bereit.

>[!NOTE]
>
>Klicken Sie auf den folgenden Link, um mywebsite.zip herunterzuladen. Das Archiv enthält die static.css- und Bilddateien für Ihr Design.

Beispieldatei static.css und Bilder

[Datei laden](assets/mywebsite.zip)

1. Klicken Sie auf der AEM-Begrüßungsseite auf **Tools**. ([https://localhost:4502/libs/cq/core/content/welcome.html](https://localhost:4502/libs/cq/core/content/welcome.html))

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Wählen Sie in der Ordnerbaumstruktur den Ordner **Designs** aus und klicken Sie dann auf **Neu** > **Neue Seite**. Geben Sie `mywebsite` als Titel ein und klicken Sie auf **Erstellen**.

1. Wenn das Element „mywebsite“ nicht in der Tabelle aufgeführt wird, aktualisieren Sie die Baumansicht bzw. die Tabelle.

1. [Greifen Sie über WebDAV](/help/sites-administering/webdav-access.md) auf die URL unter https://localhost:4502 zu und kopieren Sie die Beispieldatei `static.css` und den Ordner `images` aus der zuvor heruntergeladenen Datei mywebsite.zip in den Ordner `/etc/designs/mywebsite`.

   ![chlimage_1-28](assets/chlimage_1-28.png)

### Erstellen von contentpage-Vorlage, -Komponente und -Skript {#creating-the-contentpage-template-component-and-script}

In diesem Abschnitt erstellen Sie Folgendes:

* Die contentpage-Vorlage, die zum Erstellen von Inhaltsseiten in der Beispiel-Website verwendet wird.
* Die contentpage-Komponente, die zum Rendern von Inhaltsseiten verwendet wird.
* Das Skript contentpage .

#### Erstellen der contentpage-Vorlage {#creating-the-contentpage-template}

Erstellen Sie eine Vorlage, die als Grundlage für die Webseiten Ihrer Site verwendet werden soll.

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Komplexe Websites können mehrere Vorlagen verwenden, um die verschiedenen Seitentypen auf der Site zu erstellen. In dieser Übung basieren alle Seiten auf einer einfachen Vorlage.

1. Klicken Sie in der Ordnerbaumstruktur von CRXDE Lite mit der rechten Maustaste auf `/apps/mywebsite/templates`. Klicken Sie dann auf **Erstellen** > **Vorlage erstellen**.

1. Geben Sie im Dialogfeld Vorlage erstellen die folgenden Werte ein und klicken Sie auf **Nächste**:

   * **Titel**: contentpage
   * **Titel**: My Website Content Page Template
   * **Beschreibung**: Dies ist meine Website-Inhaltsseitenvorlage
   * **Ressourcentyp**: mywebsite/components/contentpage

   Verwenden Sie den Standardwert für die Eigenschaft „Rangfolge“.

   ![chlimage_1-29](assets/chlimage_1-29.png)

   Der Ressourcentyp identifiziert die Komponente, die die Seite rendert. In diesem Fall werden alle Seiten, die mithilfe der contentpage-Vorlage erstellt wurden, von der Komponente `mywebsite/components/contentpage` gerendert.

1. Um die Pfade der Seiten anzugeben, die diese Vorlage verwenden können, klicken Sie auf die Schaltfläche mit dem Pluszeichen und geben Sie in das daraufhin angezeigte Textfeld `/content(/.*)?` ein. Klicken Sie dann auf **Weiter**.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Beim Wert der Eigenschaft „Zugelassene Pfade“ handelt es sich um einen *regulären Ausdruck.* Seiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In diesem Fall stimmt der reguläre Ausdruck mit dem Pfad der **/content** und allen Unterseiten.

   Wenn ein Autor eine Seite unter /content erstellt, erscheint die **contentpage**-Vorlage in einer Liste mit verfügbaren Vorlagen.

1. Klicken **Nächste** im **Zugelassene übergeordnete Elemente** und **Zugelassene Kinder** Bedienfelder und klicken **OK**. Klicken Sie in CRXDE Lite auf **Alle speichern**.

   ![chlimage_1-31](assets/chlimage_1-31.png)

#### Erstellen der contentpage-Komponente {#creating-the-contentpage-component}

Erstellen Sie die *component* definiert den Inhalt und rendert die Seiten, die die contentpage-Vorlage verwenden. Der Speicherort der Komponente muss mit dem Wert der Eigenschaft &quot;Ressourcentyp&quot;der contentpage-Vorlage übereinstimmen.

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf `/apps/mywebsite/components` und klicken Sie auf **Erstellen** > **Komponente**.
1. Geben Sie im Dialogfeld **Komponente erstellen** die folgenden Eigenschaftswerte ein:

   * **Titel**: contentpage
   * **Titel**: My Website Content Page Component
   * **Beschreibung**: Dies ist meine Website-Inhaltsseitenkomponente

   ![chlimage_1-32](assets/chlimage_1-32.png)

   Der Speicherort der neuen Komponente ist `/apps/mywebsite/components/contentpage`. Dieser Pfad entspricht dem Ressourcentyp der contentpage-Vorlage (ohne den ersten Teil **`/apps/`** des Pfads).

   Diese Entsprechung verbindet die Vorlage mit der Komponente und ist entscheidend für die ordnungsgemäße Funktionsweise der Website.

1. Klicken Sie auf **Weiter**, bis das Bedienfeld „Zugelassene untergeordnete Elemente“ angezeigt wird. Klicken Sie dann auf **OK**. Klicken Sie in CRXDE Lite auf **Alle speichern**.

   Die Struktur sieht nun wie folgt aus:

   ![chlimage_1-33](assets/chlimage_1-33.png)

#### Entwickeln des Skripts für contentpage-Komponenten {#developing-the-contentpage-component-script}

Fügen Sie dem Skript contentpage.jsp Code hinzu, um den Seiteninhalt zu definieren.

1. Öffnen Sie in CRXDE Lite die Datei `contentpage.jsp` unter `/apps/mywebsite/components/contentpage`. Die Datei enthält standardmäßig den folgenden Code:

   ```java
   <%--
   
     My Website Content Page Component component.
   
     This is My Website Content Page Component.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %><%
   %><%
       /* TODO add you code here */
   %>
   ```

1. Kopieren Sie den folgenden Code und fügen Sie ihn in contentpage.jsp nach dem Standardcode ein:

   ```java
   <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
       pageEncoding="ISO-8859-1"%>
   <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
   "https://www.w3.org/TR/html4/loose.dtd">
   <html>
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
   <title>My title</title>
   </head>
   <body>
   <div>My body</div>
   </body>
   </html>
   ```

1. Klicken Sie auf **Alle speichern**, um Ihre Änderungen zu speichern.

### Erstellen von Website-Seiten und Inhaltsseiten {#creating-your-website-page-and-content-pages}

In diesem Abschnitt wird erläutert, wie Sie die folgenden Seiten erstellen, die alle die contentpage-Vorlage verwenden: „Meine Website“, „Englisch“, „Produkte“, „Services“ und „Kunden“.

1. Klicken Sie auf der AEM-Begrüßungsseite ([https://localhost:4502/libs/cq/core/content/welcome.html](https://localhost:4502/libs/cq/core/content/welcome.html)) auf „Websites“.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Wählen Sie in der Ordnerbaumstruktur den Ordner **Websites** aus und klicken Sie dann auf **Neu** > **Neue Seite**.
1. Geben Sie im Fenster **Seite erstellen** Folgendes ein:

   * Titel: `My Website`
   * Name: `mywebsite`
   * Wählen Sie die `My Website Content Page Template`

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Klicken Sie auf **Erstellen**. Wählen Sie in der Ordnerbaumstruktur die Seite unter **/Websites/Meine Website/** aus und klicken Sie dann auf **Neu** > **Neue Seite**.
1. Geben Sie im Dialogfeld Seite erstellen die folgenden Eigenschaftswerte ein und klicken Sie auf Erstellen:

   * Titel: englisch
   * Name: en
   * Wählen Sie „My Website Content Page Template“ aus.

1. Wählen Sie in der Ordnerbaumstruktur die Seite unter **/Websites/Meine Website/Englisch** aus und klicken Sie dann auf **Neu** > **Neue Seite**.
1. Im **Seite erstellen** Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie auf **Erstellen**:

   * Titel: Produkte
   * Wählen Sie „My Website Content Page Template“ aus.

1. Wählen Sie in der Ordnerbaumstruktur die Seite unter **/Websites/Meine Website/Englisch** aus und klicken Sie dann auf **Neu** > **Neue Seite**.
1. Im **Seite erstellen** Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie auf **Erstellen**:

   * Titel: Services
   * Wählen Sie „My Website Content Page Template“ aus.

1. Wählen Sie in der Ordnerbaumstruktur die Seite unter **/Websites/Meine Website/Englisch** aus und klicken Sie dann auf **Neu** > **Neue Seite**.
1. Im **Seite erstellen** Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie auf **Erstellen**:

   * Titel: Kunden
   * Wählen Sie „My Website Content Page Template“ aus.

   Ihre Struktur sieht nun wie folgt aus:

   ![chlimage_1-36](assets/chlimage_1-36.png)

1. Um Ihre Seiten mit dem mywebsite-Design zu verknüpfen, wählen Sie in CRXDE Lite den Knoten `/content/mywebsite/en/jcr:content` aus. Geben Sie auf der Registerkarte Eigenschaften die folgenden Werte für eine neue Eigenschaft ein und klicken Sie auf Hinzufügen:

   * Name: cq:designPath
   * Typ: Zeichenfolge
   * Wert: /etc/designs/mywebsite

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. Öffnen Sie in einer neuen Registerkarte bzw. in einem neuen Fenster Ihres Webbrowsers [https://localhost:4502/content/mywebsite/en/products.html](https://localhost:4502/content/mywebsite/en/products.html), um die Seite „Produkteׅ“ anzuzeigen:

   ![chlimage_1-38](assets/chlimage_1-38.png)

### Verbessern des contentpage-Skripts {#enhancing-the-contentpage-script}

In diesem Abschnitt wird beschrieben, wie Sie das contentpage-Skript mithilfe der AEM Foundation-Komponentenskripte verbessern und eigene Skripte schreiben.

Wenn Sie fertig sind, wird die **Produkte** sollte wie folgt aussehen:

![chlimage_1](assets/chlimage_1.jpeg)

#### Verwenden von Foundation-Seitenskripten {#using-the-foundation-page-scripts}

In dieser Übung konfigurieren Sie Ihre Seitenkomponente so, dass ihr Supertyp die AEM Seitenkomponente ist. Da Komponenten die Eigenschaften ihres Supertyps erben, erbt Ihre pagecontent-Komponente die Skripte und Eigenschaften der Seitenkomponente.

Beispielsweise können Sie im JSP-Code der Komponente so auf die Skripte verweisen, die den Supertyp der Komponente bereitstellen, als wären sie in Ihrer Komponente enthalten.

1. Fügen Sie in CRXDE Lite eine Eigenschaft zum Knoten `/apps/mywebsite/components/contentpage` hinzu.

   1. Wählen Sie den Knoten `/apps/mywebsite/components/contentpage` aus.
   1. Geben Sie unten auf der Registerkarte „Eigenschaften“ die folgenden Eigenschaftswerte ein und klicken Sie dann auf „Hinzufügen“:

      * **Name:** sling:resourceSuperType
      * **Typ:** Zeichenfolge
      * **Wert:** foundation/components/page

   1. Klicken Sie auf „Alle speichern“.

1. Öffnen Sie die Datei `contentpage.jsp` unter `/apps/mywebsite/components/contentpage` und ersetzen Sie den vorhandenen Code durch den folgenden Code:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" contentType="text/html; charset=utf-8" %><%
   %><!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
   <html>
   <cq:include script="head.jsp"/>
   <cq:include script="body.jsp"/>
   </html>
   ```

1. Speichern Sie Ihre Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Sie sieht wie folgt aus:

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

   Öffnen Sie die Seitenquelle, um die JavaScript- und HTML-Elemente anzuzeigen, die von den Skripten head.jsp und body.jsp generiert wurden. Das folgende Skriptfragment öffnet den Sidekick beim Öffnen der Seite:

   ```java
   CQ.WCM.launchSidekick("/content/mywebsite/en/products",
               {propsDialog: "/libs/foundation/components/page/dialog",
                  locked: false locked: false
                });
   ```

#### Verwenden eigener Skripte {#using-your-own-scripts}

In diesem Abschnitt erstellen Sie mehrere Skripte, die jeweils einen Teil des Seitentextes generieren. Anschließend erstellen Sie die Datei body.jsp in der Komponente pagecontent , um die Datei body.jsp der AEM Seitenkomponente zu überschreiben. In der Datei body.jsp fügen Sie Ihre Skripte ein, die die verschiedenen Teile des Seitentextes generieren.

**Tipp**: Wenn eine Komponente eine Datei enthält, die denselben Namen und denselben relativen Speicherort wie eine Datei im Supertyp der Komponente aufweist, wird dies als *Überlagerung* bezeichnet.

1. Erstellen Sie in CRXDE Lite die Datei `left.jsp` unter `/apps/mywebsite/components/contentpage`:

   1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/contentpage`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Datei erstellen** aus.

   1. Geben Sie im Fenster `left.jsp` als **Name** ein und klicken Sie auf **OK**.

1. Bearbeiten Sie die Datei `left.jsp`, um den vorhandenen Inhalt zu entfernen und durch den folgenden Code zu ersetzen:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="left">
   <div>logo</div>
   <div>newslist</div>
   <div>search</div>
   </div>
   ```

1. Speichern Sie die Änderungen.
1. Erstellen Sie in CRXDE Lite die Datei `center.jsp` unter `/apps/mywebsite/components/contentpage`:

   1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/contentpage`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Datei erstellen** aus.

   1. Geben Sie im Dialogfeld in das Feld `center.jsp`Name den **Dateinamen** ein und klicken Sie auf **OK**.

1. Bearbeiten Sie die Datei `center.jsp`, um den vorhandenen Inhalt zu entfernen und durch den folgenden Code zu ersetzen:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="center">
   <div>trail</div>
   <div>title</div>
   <div>parsys</div>
   </div>
   ```

1. Speichern Sie die Änderungen.
1. Erstellen Sie in CRXDE Lite die Datei `right.jsp` unter `/apps/mywebsite/components/contentpage`:

   1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/contentpage`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Datei erstellen** aus.

   1. Geben Sie im Dialogfeld in das Feld `right.jsp`Name den **Dateinamen** ein und klicken Sie auf **OK**.

1. Bearbeiten Sie die Datei `right.jsp`, um den vorhandenen Inhalt zu entfernen und durch den folgenden Code zu ersetzen:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="right">
   <div>iparsys</div>
   </div>
   ```

1. Speichern Sie die Änderungen.
1. Erstellen Sie in CRXDE Lite die Datei `body.jsp` unter `/apps/mywebsite/components/contentpage`:
1. Bearbeiten Sie die Datei `body.jsp`, um den vorhandenen Inhalt zu entfernen und durch den folgenden Code zu ersetzen:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><body>
   <div id="CQ">
   <div class="topnav">topnav</div>
   <div class="content">
   <cq:include script="left.jsp" />
   <cq:include script="center.jsp" />
   <cq:include script="right.jsp" />
   </div>
   <div class="footer">
   <div class="toolbar">toolbar</div>
   </div>
   </div>
   </body>
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Sie sieht wie folgt aus:

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

### Erstellen der Komponente für die obere Navigationsleiste {#creating-the-top-navigation-component}

In diesem Abschnitt erstellen Sie eine Komponente, die Links zu allen Seiten der obersten Ebene der Website anzeigt, um die Navigation zu vereinfachen. Dieser Komponenteninhalt wird oben auf allen Seiten angezeigt, die mit der contentpage-Vorlage erstellt wurden.

In der ersten Version der oberen Navigationskomponente (topnav) sind die Navigationselemente nur Textlinks. In der zweiten Version implementieren Sie topnav mit Links zur Bildnavigation.

Wenn Sie fertig sind, sollte Ihre obere Navigation wie folgt aussehen:

![chlimage_1-39](assets/chlimage_1-39.png)

#### Erstellen von topnav-Komponenten {#creating-the-top-navigation-component-1}

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf `/apps/mywebsite/components`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Komponente erstellen** aus.
1. Geben Sie im Fenster **Komponente erstellen** Folgendes ein:

   * **Bezeichnung**: `topnav`

   * **Titel**: `My Top Navigation Component`

   * **Beschreibung**: `This is My Top Navigation Component`

1. Klicken **Nächste** bis Sie zum letzten Fenster kommen, in dem Sie auf **OK**. Speichern Sie Ihre Änderungen.

#### Erstellen des obersten Navigationsskripts mit Textlinks {#creating-the-top-navigation-script-with-textual-links}

Fügen Sie das Rendering-Skript zu topnav hinzu, um Textlinks zu untergeordneten Seiten zu generieren:

1. Öffnen Sie in CRXDE Lite die Datei `topnav.jsp` unter `/apps/mywebsite/components/topnav`.
1. Ersetzen Sie den vorhandenen Code durch Kopieren und Einfügen des folgenden Codes:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="java.util.Iterator,
           com.day.text.Text,
           com.day.cq.wcm.api.PageFilter, com.day.cq.wcm.api.Page" %><%
       /* get starting point of navigation */
       Page navRootPage = currentPage.getAbsoluteParent(2);
       if (navRootPage == null && currentPage != null) {
       navRootPage = currentPage;
       }
       if (navRootPage != null) {
           Iterator<Page> children = navRootPage.listChildren(new PageFilter(request));
           while (children.hasNext()) {
               Page child = children.next();
               %><a href="<%= child.getPath() %>.html"><%=child.getTitle() %></a><%
           }
       }
   %>
   ```

#### Einbinden der obersten Navigation in die contentpage-Komponente {#including-top-navigation-in-the-contentpage-component}

So fügen Sie topnav in Ihre contentpage-Komponente ein:

1. Öffnen Sie in CRXDE Lite die Datei `body.jsp` unter `/apps/mywebsite/components/contentpage` und ersetzen Sie:

   ```xml
   <div class="topnav">topnav</div>
   ```

   durch:

   ```xml
   <cq:include path="topnav" resourceType="mywebsite/components/topnav" />
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Die obere Navigation wird wie folgt angezeigt:

   ![chlimage_1-40](assets/chlimage_1-40.png)

#### Verbessern von Seiten mit Untertiteln {#enhancing-pages-with-subtitles}

Die Seitenkomponente definiert Eigenschaften, mit denen Sie Untertitel für Seiten bereitstellen können. Fügen Sie Untertitel hinzu, die Informationen zum Seiteninhalt bereitstellen.

1. Öffnen Sie in Ihrem Browser die Seite **Produkte**.
1. Klicken Sie im Sidekick auf der Registerkarte **Seite** auf **Seiteneigenschaften**.
1. Erweitern Sie im Dialogfeld auf der Registerkarte „Allgemein“ den Eintrag **Weitere Titel und Beschreibungen** und geben Sie **Was wir tun** im Feld für die Eigenschaft **Untertitel** ein. Klicken Sie auf **OK**.
1. Wiederholen Sie die vorherigen Schritte, um den Untertitel **Über unsere Services** zur Seite **Services** hinzuzufügen.
1. Wiederholen Sie die vorherigen Schritte, um den Untertitel **Warum Sie uns vertrauen können** zur Seite **Kunden** hinzuzufügen.

   **Tipp:** Wählen Sie in CRXDE Lite den Knoten /content/mywebsite/en/products/jcr:content aus, um zu sehen, dass die Eigenschaft &quot;subtitle&quot;hinzugefügt wird.

#### Verbessern der oberen Navigation mithilfe von Bildlinks {#enhance-top-navigation-by-using-image-links}

Verbessern Sie das Rendering-Skript der topnav-Komponente, sodass für die Navigationssteuerelemente Bild-Links anstelle von Hypertext verwendet werden. Das Bild enthält den Titel und den Untertitel des Link-Ziels.

Diese Übung zeigt [Verarbeitung von Sling-Anforderungen](/help/sites-developing/the-basics.md#sling-request-processing). Das Skript topnav.jsp wird geändert, um ein Skript aufzurufen, das dynamisch Bilder generiert, die für die Seitennavigationslinks verwendet werden. In dieser Übung analysiert Sling die URL der Bildquelldateien, um das Skript zu bestimmen, das zum Rendern der Bilder verwendet werden soll.

Die Quelle für den Bild-Link zur Seite „Produkte“ könnte beispielsweise https://localhost:4502/content/mywebsite/en/products.navimage.png lauten. Sling analysiert diese URL, um den Ressourcentyp und das Skript zum Rendern der Ressource zu bestimmen:

1. Sling bestimmt `/content/mwebysite/en/products.png.` als Pfad der Ressource.
1. Sling ordnet diesen Pfad dem Knoten `/content/mywebsite/en/products` zu.
1. Sling bestimmt `sling:resourceType` als `mywebsite/components/contentpage` dieses Knotens.

1. Sling findet das Skript in dieser Komponente, das die größte Übereinstimmung mit der URL-Auswahl (`navimage`) und der Dateinamenerweiterung (`png`) aufweist.

Im Rahmen dieser Übung ordnet Sling diese URLs dem Skript /apps/mywebsite/components/contentpage/navimage.png.java zu, das Sie erstellen.

1. Öffnen Sie in CRXDE Lite die Datei `topnav.jsp` unter `/apps/mywebsite/components/topnav.`. Suchen Sie den Inhalt des Ankerelements (Zeile 14):

   ```xml
   <%=child.getTitle() %>
   ```

1. Ersetzen Sie den Ankerinhalt durch den folgenden Code:

   ```xml
   <img alt="<%= child.getTitle() %>" src="<%= child.getPath() %>.navimage.png">
   ```

1. Speichern Sie die Änderungen.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/contentpage` und klicken Sie auf **Erstellen** > **Datei erstellen**.
1. Geben Sie im Fenster **Datei erstellen** in das Feld **Name** `navimage.png.java` ein.

   Die Dateinamenerweiterung .java gibt Sling an, dass die Java™-Unterstützung für Apache Sling Scripting verwendet werden sollte, um das Skript zu kompilieren und ein Servlet zu erstellen.

1. Kopieren Sie den folgenden Code nach `navimage.png.java.`. Der Code erweitert die Klasse „AbstractImageServlet“:

   * [AbstractImageServlet](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) erstellt ein ImageContext -Objekt, das die Eigenschaften der aktuellen Ressource speichert.
   * Die übergeordnete Seite der Ressource wird aus dem ImageContext-Objekt extrahiert. Dann werden der Seitentitel und der Untertitel abgerufen.
   * [ImageHelper](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/ImageHelper.html) wird verwendet, um das Bild aus der Datei &quot;navimage_bg.jpg&quot;des Site-Designs, dem Seitentitel und dem Seitentitel zu generieren.

   ```java
   package apps.mywebsite.components.contentpage;
   
   import java.awt.Color;
   import java.awt.Paint;
   import java.awt.geom.Rectangle2D;
   
   import java.io.IOException;
   import javax.jcr.RepositoryException;
   
   import com.day.cq.wcm.api.Page;
   import com.day.cq.wcm.api.PageManager;
   import com.day.cq.wcm.api.components.Component;
   import com.day.cq.wcm.api.designer.Designer;
   
   import com.day.cq.commons.SlingRepositoryException;
   import com.day.cq.wcm.commons.WCMUtils;
   import com.day.cq.wcm.commons.AbstractImageServlet;
   import com.day.cq.commons.ImageHelper;
   
   import com.day.image.Font;
   import com.day.image.Layer;
   
   import org.apache.sling.api.SlingHttpServletRequest;
   import org.apache.sling.api.SlingHttpServletResponse;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.servlets.SlingSafeMethodsServlet;
   
   /**
     * Renders the navigation image
     */
   public class navimage_png extends AbstractImageServlet {
   
         protected Layer createLayer(ImageContext ctx)
                throws RepositoryException, IOException {
            PageManager pageManager = ctx.resolver.adaptTo(PageManager.class);
            Page currentPage = pageManager.getContainingPage(ctx.resource);
   
            /* constants for image appearance */
            int scale = 6;
            int paddingX = 24;
            int paddingY = 24;
            Color bgColor = new Color(0x004a565c, true);
   
            /* obtain the page title */
            String title = currentPage.getTitle();
            if (title == null) {
                title = currentPage.getName();
            }
   
            /* format the title text */
            title = title.toUpperCase();
            Paint titleColor = Color.WHITE;
            Font titleFont = new Font("Myriad Pro", 10 * scale, Font.BOLD);
            int titleBase = 10 * scale;
   
            /* obtain and format the page subtitle */
            String subtitle = currentPage.getProperties().get("subtitle", "");
            Paint subtitleColor = new Color(0xffa9afb1, true);
            Font subTitleFont = new Font("Tahoma", 7);
            int subTitleBase = 20;
   
            /* create a layer that contains the background image from the mywebsite design */
            Designer dg = ctx.resolver.adaptTo(Designer.class);
            String imgPath = new String(dg.getDesignPath(currentPage)+"/images/navimage_bg.jpg");
            Layer bg = ImageHelper.createLayer(ctx.resolver.resolve(imgPath));
   
            /* draw the title text (4 times bigger) */
            Rectangle2D titleExtent = titleFont.getTextExtent(0, 0, 0, 0, title, Font.ALIGN_LEFT, 0, 0);
            Rectangle2D subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
   
            /* ensure subtitleExtent is wide enough */
            if ( subtitle.length() > 0 ) {
                int titleWidth = (int)titleExtent.getWidth() / scale;
                if ( subtitleExtent.getWidth() > titleWidth && subtitleExtent.getWidth() + 2 * paddingX >
    bg.getWidth() ) {
                    int charWidth = (int)subtitleExtent.getWidth() / subtitle.length();
                    int maxWidth = (bg.getWidth() > titleWidth + 2  * paddingX ? bg.getWidth() - 2 * paddingX : titleWidth);
                    int len = (maxWidth - ( 2 * charWidth) ) / charWidth;
                    subtitle = subtitle.substring(0, len) + "...";
                    subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
                }
            }
            int width = Math.max((int) titleExtent.getWidth(), (int) subtitleExtent.getWidth());
           /* create the text layer */
            Layer text = new Layer(width, (int) titleExtent.getHeight() + 40, new Color(0x01ffffff, true));
            text.setPaint(titleColor);
            text.drawText(0, titleBase, 0, 0, title, titleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0);
            text.resize(text.getWidth() / scale, text.getHeight() / scale);
            text.setX(0);
            text.setY(0);
   
            if (subtitle.length() > 0) {
                /* draw the subtitle normal sized */
                text.setPaint(subtitleColor);
                text.drawText(0, subTitleBase, 0, 0, subtitle, subTitleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0);
            }
   
            /* merge the image and text layers */
            text.setY(paddingY);
            text.setX(paddingX);
            text.setBackgroundColor(bgColor);
   
            int bgWidth = bg.getWidth();
            if ( text.getWidth() + 2 * paddingX > bgWidth ) {
                bgWidth = text.getWidth() + 2 * paddingX;
                bg.resize(bgWidth, bg.getHeight());
            }
            bg.merge(text);
   
            return bg;
        }
    }
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Die obere Navigation wird jetzt wie folgt angezeigt:

   ![screen_shot_2012-03-07at10047pm](assets/screen_shot_2012-03-07at10047pm.png)

### Erstellen der Komponente &quot;List Children&quot; {#creating-the-list-children-component}

Erstellen Sie die listchildren-Komponente, die eine Liste von Seitenlinks generiert, die den Titel, die Beschreibung und das Datum der Seiten enthalten (z. B. Produktseiten). Die Links zielen auf die untergeordneten Seiten der aktuellen Seite oder einer Stammseite ab, die im Komponentendialogfeld angegeben ist.

![chlimage_1-41](assets/chlimage_1-41.png)

#### Erstellen von Produktseiten {#creating-product-pages}

Erstellen Sie zwei Seiten unter der Seite „Produkte“. Für jede Seite, die zwei spezifische Produkte beschreibt, legen Sie einen Titel, eine Beschreibung und ein Datum fest.

1. Wählen Sie im Ordnerbaum der Seite Websites das Element Websites/My Website/English/Products aus und klicken Sie auf Neu > Neue Seite.
1. Geben Sie im Dialogfeld die folgenden Eigenschaftswerte ein und klicken Sie auf Erstellen:

   * Titel: Produkt 1.
   * Name: product1.
   * My Website Content Page Template auswählen

1. Erstellen Sie eine weitere Seite unter „Produkte“ mit den folgenden Eigenschaftswerten:

   * Titel: Produkt 2
   * Name: product2
   * My Website Content Page Template auswählen

1. Legen Sie in CRXDE Lite eine Beschreibung und ein Datum für die Seite „Product 1“ fest:

   1. Wählen Sie den Knoten `/content/mywebsite/en/products/product1/jcr:content` aus.
   1. Geben Sie auf der Registerkarte **Eigenschaften** die folgenden Werte ein:

      * Name: `jcr:description`
      * Typ: `String`
      * Wert: `This is a description of the Product 1!.`

   1. Klicken Sie auf **Hinzufügen**.
   1. Im **Eigenschaften** erstellen Sie eine weitere Eigenschaft mit den folgenden Werten:

      * Name: date
      * Typ: Zeichenfolge
      * Wert: 02/14/2008
      * Klicken Sie auf Hinzufügen.

   1. Klicken Sie auf Alle speichern.

1. Legen Sie in CRXDE Lite eine Beschreibung und ein Datum für die Seite „Product 2“ fest:

   1. Wählen Sie den Knoten /content/mywebsite/en/products/product2/jcr:content aus.
   1. Geben Sie auf der Registerkarte **Eigenschaften** die folgenden Werte ein:

      * Name: jcr:description
      * Typ: Zeichenfolge
      * Wert: This is a description of the Product 2!

   1. Klicken Sie auf **Hinzufügen**.
   1. Ersetzen Sie in denselben Textfeldern die vorherigen Werte durch die folgenden Werte:

      * Name: date
      * Typ: Zeichenfolge
      * Wert: 05/11/2012
      * Klicken Sie auf Hinzufügen.

   1. Klicken Sie auf Alle speichern.

#### Erstellen der Komponente &quot;List Children&quot; {#creating-the-list-children-component-1}

So erstellen Sie die listchildren-Komponente:

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf `/apps/mywebsite/components`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Komponente erstellen** aus.
1. Geben Sie im Dialogfeld die folgenden Eigenschaftswerte ein und klicken Sie auf &quot;Next&quot;:

   * Bezeichnung: listchildren.
   * Titel: Meine Listchildren-Komponente
   * Beschreibung: Dies ist meine Listchildren-Komponente.

1. Klicken Sie auf Weiter , bis das Bedienfeld Zulässige untergeordnete Elemente angezeigt wird, und klicken Sie dann auf OK.

#### Erstellen des untergeordneten Listenskripts {#creating-the-list-children-script}

Entwickeln Sie das Skript für die listchildren-Komponente.

1. Öffnen Sie in CRXDE Lite die Datei `listchildren.jsp` unter `/apps/mywebsite/components/listchildren`.
1. Ersetzen Sie den Standardcode durch den folgenden Code:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="java.util.Iterator,
            com.day.cq.wcm.api.PageFilter"%><%
        /* Create a new Page object using the path of the current page */
         String listroot = properties.get("listroot", currentPage.getPath());
        Page rootPage = pageManager.getPage(listroot);
        /* iterate through the child pages and gather properties */
        if (rootPage != null) {
            Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
            while (children.hasNext()) {
                Page child = children.next();
                String title = child.getTitle() == null ? child.getName() : child.getTitle();
                String date = child.getProperties().get("date","");
                %><div class="item">
                <a href="<%= child.getPath() %>.html"><b><%= title %></b></a>
                <span><%= date %></code><br>
                <%= child.getProperties().get("jcr:description","") %><br>
                </div><%
            }
        }
    %>
   ```

1. Speichern Sie die Änderungen.

#### Erstellen des Dialogfelds &quot;Untergeordnete Listen&quot; {#creating-the-list-children-dialog}

Erstellen Sie das Dialogfeld, das zum Konfigurieren der listchildren-Komponenteneigenschaften verwendet wird.

1. Erstellen Sie den Dialogknoten unter der listchildren-Komponente:

   1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/listchildren` und klicken Sie dann auf **Erstellen** > **Dialogfeld erstellen**.

   1. Geben Sie im Dialogfeld die folgenden Eigenschaftswerte ein und klicken Sie dann auf „OK“:

      * **Bezeichnung**: `dialog`

      * **Titel**: `Edit Component` und klicken Sie auf **OK**.

   ![screen_shot_2012-03-07at45818pm](assets/screen_shot_2012-03-07at45818pm.png)

   Mit den folgenden Eigenschaften:

   ![screen_shot_2012-03-07at50415pm](assets/screen_shot_2012-03-07at50415pm.png)

1. Wählen Sie den Knoten `/apps/mywebsite/components/listchildren/dialog/items/items/tab1` aus.
1. Ändern Sie auf der Registerkarte „Eigenschaften“ den Wert der Eigenschaft **Titel** in `List Children`.

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. Wählen Sie den Knoten tab1 aus und klicken Sie auf Erstellen > Knoten erstellen, geben Sie die folgenden Eigenschaftswerte ein und klicken Sie auf OK:

   * Name: items
   * Typ: cq:WidgetCollection

   ![screen_shot_2012-03-07at51018pm](assets/screen_shot_2012-03-07at51018pm.png)

1. Erstellen Sie einen Knoten unter dem Knoten items mit den folgenden Eigenschaftswerten:

   * Name: listroot
   * Typ: cq:Widget

   ![screen_shot_2012-03-07at51031pm](assets/screen_shot_2012-03-07at51031pm.png)

1. Fügen Sie Eigenschaften für den Knoten „listroot“ hinzu, um ihn als Textfeld zu konfigurieren. Jede Zeile in der folgenden Tabelle stellt eine Eigenschaft dar. Klicken Sie abschließend auf Alle speichern .

   | Name | Typ | Wert |
   |---|---|---|
   | fieldLabel | Zeichenfolge | Pfad des Listenstammverzeichnisses |
   | name | Zeichenfolge | ./listroot |
   | xtype | Zeichenfolge | textfield |

   ![screen_shot_2012-03-07at51433pm](assets/screen_shot_2012-03-07at51433pm.png)

#### Einschließen von Listenuntergründen in die contentpage-Komponente {#including-list-children-in-the-contentpage-component}

Gehen Sie wie folgt vor, um die listchildren-Komponente in Ihre contentpage-Komponente einzubeziehen:

1. Öffnen Sie in CRXDE Lite die Datei `left.jsp` unter `/apps/mywebsite/components/contentpage` und suchen Sie den folgenden Code (Zeile 4):

   ```xml
   <div>newslist</div>
   ```

1. Ersetzen Sie diesen Code durch den folgenden Code:

   ```xml
   <cq:include path="newslist" resourceType="mywebsite/components/listchildren" />
   ```

1. Speichern Sie die Änderungen.

#### Anzeigen von untergeordneten Listen auf einer Seite {#viewing-list-children-in-a-page}

Um den vollständigen Betrieb dieser Komponente anzuzeigen, können Sie die Seite Produkte anzeigen:

* wenn die übergeordnete Seite (&quot;Pfad des Listenstamms&quot;) nicht definiert ist.
* wenn die übergeordnete Seite (&quot;Pfad des Listenstamms&quot;) definiert ist.

1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Die listchildren-Komponente wird wie folgt angezeigt:

   ![chlimage_1-43](assets/chlimage_1-43.png)

1. ![chlimage_1-44](assets/chlimage_1-44.png)

1. Geben Sie im Feld „Pfad des Listenstammverzeichnisses“ `/content/mywebsite/en` ein. Klicken Sie auf „OK“. Die listchildren-Komponente auf Ihrer Seite sieht nun wie folgt aus:

   ![chlimage_1-45](assets/chlimage_1-45.png)

### Erstellen der Logokomponente {#creating-the-logo-component}

Erstellen Sie eine Komponente, die das Firmenlogo anzeigt und einen Link zur Startseite der Site bereitstellt. Die Komponente enthält ein Dialogfeld für den Designmodus, sodass Eigenschaftswerte im Site-Design (/etc/designs/mywebsite) gespeichert werden:

* Die Eigenschaftswerte gelten für alle Instanzen der Komponente, die zu Seiten hinzugefügt werden, die das Design verwenden.
* Die Eigenschaften können mit jeder Instanz der Komponente konfiguriert werden, die sich auf einer Seite befindet, die das Design verwendet.

Ihr Dialogfeld für den Designmodus enthält Eigenschaften zum Festlegen des Bildes und des Linkpfads. Die logo-Komponente wird auf der linken oberen Seite aller Seiten der Website platziert.

Wenn Sie fertig sind, sollte dies wie folgt aussehen:

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>Adobe Experience Manager bietet eine logo-Komponente mit umfassenderem Funktionsumfang ( `/libs/foundation/components/logo`).

#### Erstellen des Knotens der logo-Komponente {#creating-the-logo-component-node}

Gehen Sie wie folgt vor, um die logo-Komponente zu erstellen:

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf /apps/mywebsite/components, wählen Sie dann die Option **Erstellen** und anschließend die Option **Komponente erstellen** aus.
1. Geben Sie im Dialogfeld „Komponente erstellen“ die folgenden Eigenschaftswerte ein und klicken Sie dann auf „Weiter“:

   * Bezeichnung: `logo`.
   * Titel: `My Logo Component`.
   * Beschreibung: `This is My Logo Component`.

1. Klicken Sie auf Weiter , bis Sie zum letzten Bedienfeld des Dialogfelds gelangen, und klicken Sie dann auf **OK**.

#### Erstellen eines Logoskripts {#creating-the-logo-script}

In diesem Abschnitt wird beschrieben, wie Sie das Skript erstellen, um das Logo-Bild mit einem Link zur Homepage anzuzeigen.

1. Öffnen Sie in CRXDE Lite die Datei `logo.jsp` unter `/apps/mywebsite/components/logo`.
1. Mit dem folgenden Code wird ein Link zur Homepage der Website erstellt und einen Verweis auf das Logobild hinzufügt. Kopieren Sie den Code und fügen Sie ihn in `logo.jsp` ein:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.text.Text,
                      com.day.cq.wcm.foundation.Image,
                      com.day.cq.commons.Doctype" %><%
       /* obtain the path for home */
       long absParent = currentStyle.get("absParent", 2L);
       String home = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);
       /* obtain the image */
       Resource res = currentStyle.getDefiningResource("imageReference");
       if (res == null) {
           res = currentStyle.getDefiningResource("image");
       }
       /* if no image use text link, otherwise draw the image */
       %>
   <a href="<%= home %>.html"><%
       if (res == null) {
           %>Home<%
       } else {
           Image img = new Image(res);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out);
       }
       %></a>
   ```

1. Speichern Sie die Änderungen.

#### Erstellen des Dialogfelds &quot;Logo Design&quot; {#creating-the-logo-design-dialog}

Erstellen Sie das Dialogfeld zum Konfigurieren Ihrer logo-Komponente im Designmodus. Knoten für Designmodus-Dialogfelder müssen `design_dialog` benannt werden.

1. Erstellen Sie den Knoten „dialog“ unter der logo-Komponente:

   1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/logo` und klicken Sie dann auf **Erstellen** > **Dialogfeld erstellen**.

   1. Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie dann auf „OK“:

      * **Bezeichnung:** `design_dialog`

      * **Titel:** `Logo (Design)`

1. Klicken Sie mit der rechten Maustaste auf den Knoten tab1 im Zweig design_dialog und klicken Sie auf Löschen. Klicken Sie auf „Alle speichern“.
1. Unter dem `design_dialog/items/items`Knoten erstellen Sie einen Knoten namens `img` des Typs `cq:Widget`. Fügen Sie die folgenden Eigenschaften hinzu und klicken Sie dann auf „Alle speichern“:

   | Name | Typ | Wert |
   |---|---|---|
   | fileNameParameter | Zeichenfolge | ./imageName |
   | fileReferenceParameter | Zeichenfolge | ./imageReference |
   | name | Zeichenfolge | ./image |
   | title | Zeichenfolge | Bild |
   | xtype | Zeichenfolge | html5smartimage |

   ![chlimage_1-47](assets/chlimage_1-47.png)

#### Erstellen des Renderskripts für das Logo {#creating-the-logo-render-script}

Erstellen Sie das Skript, das das Logo-Bild abruft und auf die Seite schreibt.

1. Klicken Sie mit der rechten Maustaste auf den Knoten der logo-Komponente und klicken Sie auf Erstellen > Datei erstellen , um die Skriptdatei img.GET.java zu erstellen.
1. Öffnen Sie die Datei, kopieren Sie den folgenden Code in die Datei und klicken Sie auf Alle speichern :

```java
package apps.mywebsite.components.logo;

import java.io.IOException;
import java.io.InputStream;

import javax.jcr.RepositoryException;
import javax.jcr.Property;
import javax.servlet.http.HttpServletResponse;

import com.day.cq.wcm.foundation.Image;
import com.day.cq.wcm.commons.RequestHelper;
import com.day.cq.wcm.commons.WCMUtils;
import com.day.cq.wcm.commons.AbstractImageServlet;
import com.day.cq.commons.SlingRepositoryException;
import com.day.image.Layer;
import org.apache.commons.io.IOUtils;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ValueMap;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;

/**
 * Renders an image
 */
public class img_GET extends AbstractImageServlet {

    protected Layer createLayer(ImageContext c)
            throws RepositoryException, IOException {
        /* don't create the layer yet. handle everything later */
        return null;
    }

    protected void writeLayer(SlingHttpServletRequest req,
                              SlingHttpServletResponse resp,
                              ImageContext c, Layer layer)
            throws IOException, RepositoryException {

        Image image = new Image(c.resource);
        image.setItemName(Image.NN_FILE, "image");
        image.setItemName(Image.PN_REFERENCE, "imageReference");
        if (!image.hasContent()) {
            resp.sendError(HttpServletResponse.SC_NOT_FOUND);
            return;
        }
        /* get pure layer */
        layer = image.getLayer(false, false, false);

        /* do not re-encode layer, just spool */
        Property data = image.getData();
        InputStream in = data.getStream();
        resp.setContentLength((int) data.getLength());
        String contentType = image.getMimeType();
        if (contentType.equals("application/octet-stream")) {
            contentType=c.requestImageType;
        }
        resp.setContentType(contentType);
        IOUtils.copy(in, resp.getOutputStream());
        in.close();

        resp.flushBuffer();
    }
}
```

#### Hinzufügen der logo-Komponente zur contentpage-Komponente {#adding-the-logo-component-to-the-contentpage-component}

1. Öffnen Sie in CRXDE Lite die Datei `left.jsp` unter `/apps/mywebsite/components/contentpage file` und suchen Sie die folgende Codezeile:

   ```xml
   <div>logo</div>
   ```

1. Ersetzen Sie diesen Code durch die folgende Codezeile:

   ```xml
   <cq:include path="logo" resourceType="mywebsite/components/logo" />
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Das Logo sieht nun wie folgt aus, zeigt aber zurzeit nur den zugrundeliegenden Link:

   ![chlimage_1-48](assets/chlimage_1-48.png)

#### Festlegen des Logobilds auf einer Seite {#setting-the-logo-image-in-a-page}

In diesem Abschnitt wird beschrieben, wie Sie ein Bild mithilfe des Dialogfelds &quot;Designmodus&quot;als Logo festlegen.

1. Klicken Sie, während die Seite „Produkte“ im Browser geöffnet ist, unten im Sidekick auf die Schaltfläche „Design“, um in den Designmodus zu wechseln.

   ![Die Schaltfläche Design wird durch ein rechtes Quadrat gekennzeichnet.](do-not-localize/chlimage_1-1.png)

1. Klicken Sie in der Symbolleiste &quot;Design of logo&quot;auf Bearbeiten , um die Einstellungen für die logo-Komponente im Dialogfeld zu bearbeiten.
1. Klicken Sie im Dialogfeld in das Bedienfeld der Registerkarte &quot;Bild&quot;, suchen Sie nach dem logo.png-Bild, das Sie aus der Datei mywebsite.zip extrahiert haben, und klicken Sie auf &quot;OK&quot;.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Klicken Sie auf das Dreieck in der Titelleiste des Sidekicks, um zum Bearbeitungsmodus zurückzukehren.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

1. Wechseln Sie in CRXDE Lite zum folgenden Knoten, um die gespeicherten Eigenschaftswerte anzuzeigen:

   `/etc/designs/mywebsite/jcr:content/contentpage/logo`

### Einschließen der Breadcrumb-Komponente {#including-the-breadcrumb-component}

In diesem Abschnitt schließen Sie die Breadcrumb-Komponente (Pfad) ein, die eine der Foundation-Komponenten ist.

1. Navigieren Sie in CRXDE Lite zu `/apps/mywebsite/components/contentpage`, öffnen Sie die Datei `center.jsp`und ersetzen Sie:

   ```java
   <div>trail</div>
   ```

   durch:

   ```xml
   <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite **Produkte 1** neu. Die Trail-Komponente sieht wie folgt aus:

   ![chlimage_1-50](assets/chlimage_1-50.png)

### Einschließen der Titelkomponente {#including-the-title-component}

In diesem Abschnitt schließen Sie die title-Komponente ein, die eine der Foundation-Komponenten ist.

1. Navigieren Sie in CRXDE Lite zu `/apps/mywebsite/components/contentpage`, öffnen Sie die Datei `center.jsp`und ersetzen Sie:

   ```xml
   <div>title</div>
   ```

   durch:

   ```xml
   <cq:include path="title" resourceType="foundation/components/title" />
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Die title-Komponente sieht nun wie folgt aus:

   ![chlimage_1-51](assets/chlimage_1-51.png)

   **Hinweis**: Im Bearbeitungsmodus können Sie einen anderen Titel festlegen und den Typ und die Größe ändern.

### Einschließen der Absatzsystemkomponente {#including-the-paragraph-system-component}

Das Absatzsystem (parsys) ist ein wichtiger Teil einer Website, da es eine Liste von Absätzen verwaltet. Sie ermöglicht es Autoren, Absatzkomponenten zur Seite hinzuzufügen, und bietet eine Struktur.

Fügen Sie die parsys-Komponente (eine der Foundation-Komponenten) zu Ihrer contentpage-Komponente hinzu.

1. Navigieren Sie in CRXDE Lite zu `/apps/mywebsite/components/contentpage`, öffnen Sie die Datei `center.jsp`und suchen Sie die folgende Codezeile:

   ```xml
   <div>parsys</div>
   ```

1. Ersetzen Sie diese Codezeile durch den folgenden Code und speichern Sie die Änderungen:

   ```xml
   <cq:include path="par" resourceType="foundation/components/parsys" />
   ```

1. Aktualisieren Sie in Ihrem Browser die Seite „Produkte“. Sie verfügt jetzt über die parsys-Komponente, die wie folgt aussieht:

   ![chlimage_1-52](assets/chlimage_1-52.png)

### Erstellen der Bildkomponente {#creating-the-image-component}

Erstellen Sie eine Komponente, die ein Bild im Absatzsystem anzeigt. Um Zeit zu sparen, wird die Bildkomponente als Kopie der logo-Komponente mit einigen Eigenschaftsänderungen erstellt.

>[!NOTE]
>
>Adobe Experience Manager bietet eine image-Komponente mit umfassenderen Funktionsumfang (`/libs/foundation/components/image`).

#### Erstellen von image-Komponenten {#creating-the-image-component-1}

1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/logo` und dann auf „Kopieren“.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components` und klicken Sie dann auf „Einfügen“.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `Copy of logo`, klicken Sie auf „Umbenennen“, löschen Sie den vorhandenen Text und geben Sie `image` ein.

1. Wählen Sie den Komponentenknoten `image` aus und ändern Sie die folgenden Eigenschaftswerte:

   * `jcr:title:` Meine image-Komponente.
   * `jcr:description`: Dies ist meine image-Komponente.

1. Fügen Sie zum Knoten `image` eine Eigenschaft mit den folgenden Eigenschaftswerten hinzu:

   * Name: componentGroup
   * Typ: Zeichenfolge
   * Wert: MyWebsite

1. Benennen Sie den Knoten `image` unter dem Knoten `design_dialog` in `dialog` um.

1. Umbenennen von `logo.jsp` in `image.jsp.`

1. Öffnen Sie img.GET.java und ändern Sie das Paket in `apps.mywebsite.components.image`.

![chlimage_1-53](assets/chlimage_1-53.png)

#### Erstellen des Bildskripts {#creating-the-image-script}

In diesem Abschnitt wird beschrieben, wie Sie das Bildskript erstellen.

1. Öffnen Sie `/apps/mywebsite/components/image/` `image.jsp`
1. Ersetzen Sie den vorhandenen Code durch den folgenden Code und speichern Sie dann die Änderungen:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.cq.commons.Doctype,
                       com.day.cq.wcm.foundation.Image,
                       com.day.cq.wcm.api.components.DropTarget,
                       com.day.cq.wcm.api.components.EditConfig,
                       com.day.cq.wcm.commons.WCMUtils" %><%
    /* global.jsp provides access to the current resource through the resource object */
           Image img = new Image(resource);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out); %>
   ```

1. Speichern Sie die Änderungen.

#### Erstellen des Knotens &quot;Image cq:editConfig&quot; {#creating-the-image-cq-editconfig-node}

Über den Knoten `cq:editConfig` können Sie bestimmte Verhaltensweisen von Komponenten konfigurieren, indem Sie ihre Eigenschaften bearbeiten.

In diesem Abschnitt verwenden Sie einen Knoten cq:editConfig , mit dem Sie Assets aus dem Content Finder in Ihre Bildkomponente ziehen können.

1. Erstellen Sie in CRXDE Lite unter dem Knoten /apps/mywebsite/components/image einen Knoten wie folgt:

   * Name: cq:editConfig.
   * Typ: cq:EditConfig.

1. Erstellen Sie unter dem Knoten cq:editConfig einen Knoten wie folgt:

   * Name: cq:dropTargets.
   * Typ: cq:DropTargetConfig.

1. Erstellen Sie unter dem Knoten cq:dropTargets einen Knoten wie folgt:

   * Name: Bild.
   * Typ: nt:unstructured.

1. Legen Sie in CRXDE die Eigenschaften wie folgt fest:

| Name | Typ | Wert |
|---|---|---|
| Akzeptieren der Bedingungen | Zeichenfolge | image/(gif | jpeg | png) |
| Gruppen | Zeichenfolge | media |
| propertyName | Zeichenfolge | ./imageReference |

![chlimage_1-54](assets/chlimage_1-54.png)

#### Symbol hinzufügen {#adding-the-icon}

In diesem Abschnitt fügen Sie das Symbol hinzu, das neben der Bildkomponente angezeigt werden soll, wenn es in Sidekick aufgeführt wird:

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf die Datei `/libs/foundation/components/image/icon.png` und wählen Sie die Option **Kopieren** aus.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/mywebsite/components/image` und klicken Sie dann auf **Einfügen** und anschließend auf **Alle speichern**.

#### Verwenden von image-Komponenten {#using-the-image-component}

In diesem Abschnitt sehen Sie die **Produkte** und fügen Sie Ihre Bildkomponente zum Absatzsystem hinzu.

1. Laden Sie in Ihrem Browser die Seite **Produkte** neu.
1. Klicken Sie im Sidekick auf die **Designmodus** Symbol.
1. Klicken Sie auf die Schaltfläche Bearbeiten , um das Dialogfeld &quot;Design&quot;von par.
1. Im Dialogfeld wird eine Liste von **Zugelassene Komponenten** angezeigt wird; navigieren zu **MyWebsite**, wählen Sie die **My Image Component** und klicken Sie auf **OK.**
1. Zurück zu **Bearbeitungsmodus.**
1. Doppelklicken Sie auf den Rahmen parsys (auf **Komponenten oder Assets hierher ziehen**). Die **Neue Komponente einfügen** und **Sidekick** Selektoren sehen wie folgt aus:

   ![chlimage_1-4](assets/chlimage_1-4.jpeg)

### Einschließen der Toolbar-Komponente {#including-the-toolbar-component}

In diesem Abschnitt fügen Sie die Symbolleistenkomponente ein, die eine der Foundation-Komponenten ist.

Im Bearbeitungsmodus und im Designmodus stehen Ihnen verschiedene Optionen zur Verfügung.

1. Navigieren Sie in CRXDE Lite zu `/apps/mywebsite/components/contentpage`, öffnen Sie die `body.jsp` und suchen Sie den folgenden Code:

   ```java
   <div class="toolbar">toolbar</div>
   ```

1. Ersetzen Sie diesen Code durch den folgenden Code und speichern Sie die Änderungen:

   ```java
   <cq:include path="toolbar" resourceType="foundation/components/toolbar"/>
   ```

1. Wählen Sie im Ordnerbaum der AEM Websites die Option Websites/My Website/English und klicken Sie dann auf New > New Page. Geben Sie die folgenden Eigenschaftswerte an und klicken Sie auf Erstellen:

   * Titel: Symbolleiste
   * My Website Content Page Template auswählen

1. Klicken Sie in der Liste der Seiten mit der rechten Maustaste auf die Seite &quot;Symbolleiste&quot;und klicken Sie auf &quot;Eigenschaften&quot;. Wählen Sie &quot;In Navigation ausblenden&quot;und klicken Sie auf &quot;OK&quot;.

   Die Option In Navigation ausblenden verhindert, dass die Seite in Navigationskomponenten wie topnav und listchildren angezeigt wird.

1. Erstellen Sie unter &quot;Symbolleiste&quot;die folgenden Seiten:

   * Kontakte
   * Feedback
   * Anmeldung
   * Suchen

1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Sie sieht wie folgt aus:

   ![chlimage_1-55](assets/chlimage_1-55.png)

### Erstellen der Suchkomponente {#creating-the-search-component}

In diesem Abschnitt erstellen Sie die Komponente, um auf der Website nach Inhalten zu suchen. Diese Suchkomponente kann im Absatzsystem einer beliebigen Seite platziert werden (z. B. auf einer speziellen Suchergebnisseite).

Wenn Sie fertig sind, sollte Ihr Sucheingabefeld wie folgt aussehen: **englisch** Seite:

![chlimage_1-56](assets/chlimage_1-56.png)

#### Erstellen von search-Komponenten {#creating-the-search-component-1}

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf `/apps/mywebsite/components`, wählen Sie dann die Option **Erstellen** und anschließend die Option **Komponente erstellen** aus.
1. Verwenden Sie das Dialogfeld, um die Komponente zu konfigurieren:

   1. Geben Sie in einem ersten Bereich die folgenden Eigenschaftswerte an:

      * Bezeichnung: Suche
      * Titel: Meine Such-Komponente
      * Beschreibung: Dies ist meine Such-Komponente
      * Gruppe: MyWebsite

   1. Klicken Sie auf „Weiter“ und dann erneut auf „Weiter“.
   1. Klicken Sie im Bedienfeld „Zugelassene übergeordnete Elemente“ auf die Schaltfläche mit dem Pluszeichen und geben Sie `*/parsys` ein.
   1. Klicken Sie auf „Weiter“ und dann auf „OK“.

1. Klicken Sie auf „Alle speichern“.
1. Kopieren Sie die folgenden Knoten und fügen Sie sie in den Knoten apps/mywebsite/components/search ein:

   * `/libs/foundation/components/search/dialog`
   * `` `/libs/foundation/components/search/i18n`

   * `/libs/foundation/components/search/icon.png`

1. Klicken Sie auf „Alle speichern“.

#### Erstellen des Suchskripts {#creating-the-search-script}

In diesem Abschnitt wird beschrieben, wie Sie das search-Skript erstellen.

1. Öffnen Sie die Datei `/apps/mywebsite/components/search/search.jsp`.
1. Kopieren Sie den folgenden Code und fügen Sie ihn in `search.jsp` ein:

   ```java
   <%@ page import="com.day.cq.wcm.foundation.Search,com.day.cq.tagging.TagManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   %><cq:setContentBundle/><%
       Search search = new Search(slingRequest);
   
       String searchIn = (String) properties.get("searchIn");
       String requestSearchPath = request.getParameter("path");
       if (searchIn != null) {
           /* only allow the "path" request parameter to be used if it
            is within the searchIn path configured */
           if (requestSearchPath != null && requestSearchPath.startsWith(searchIn)) {
               search.setSearchIn(requestSearchPath);
           } else {
               search.setSearchIn(searchIn);
           }
       } else if (requestSearchPath != null) {
           search.setSearchIn(requestSearchPath);
       }
   
       pageContext.setAttribute("search", search);
       TagManager tm = resourceResolver.adaptTo(TagManager.class);
   %><c:set var="trends" value="${search.trends}"/><%
   %><center>
     <form action="${currentPage.path}.html">
       <input size="41" maxlength="2048" name="q" value="${fn:escapeXml(search.query)}"/>
       <input value="<fmt:message key="searchButtonText"/>" type="submit" />
     </form>
   </center>
   <br/>
   <c:set var="result" value="${search.result}"/>
   <c:choose>
     <c:when test="${empty result && empty search.query}">
     </c:when>
     <c:when test="${empty result.hits}">
       <c:if test="${result.spellcheck != null}">
         <p><fmt:message key="spellcheckText"/> <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${result.spellcheck}"/></c:url>"><b><c:out value="${result.spellcheck}"/></b></a></p>
       </c:if>
       <fmt:message key="noResultsText">
         <fmt:param value="${fn:escapeXml(search.query)}"/>
       </fmt:message>
     </c:when>
     <c:otherwise>
       <p class="searchmeta">Results ${result.startIndex + 1} - ${result.startIndex + fn:length(result.hits)} of ${result.totalMatches} for <b>${fn:escapeXml(search.query)}</b>. (${result.executionTime} seconds)</p>
      <br/>
   
     <div class="searchresults">
       <div class="results">
         <c:forEach var="hit" items="${result.hits}" varStatus="status">
           <div class="hit">
           <a href="${hit.URL}">${hit.title}</a>
           <div class="excerpt">${hit.excerpt}</div>
          <div class="hiturl"> ${hit.URL}<c:if test="${!empty hit.properties['cq:lastModified']}"> - <c:catch><fmt:formatDate value="${hit.properties['cq:lastModified'].time}" dateStyle="medium"/></c:catch></c:if> - <a href="${hit.similarURL}"><fmt:message key="similarPagesText"/></a>
           </div></div>
         </c:forEach>
       </div>
         <br/>
   
        <div class="searchRight">
             <c:if test="${fn:length(trends.queries) > 0}">
                 <p><fmt:message key="searchTrendsText"/></p>
                 <div class="searchTrends">
                     <c:forEach var="query" items="${trends.queries}">
                         <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${query.query}"/></c:url>"><span style="font-size:${query.size}px"><c:out value="${query.query}"/></code></a>
                     </c:forEach>
                 </div>
             </c:if>
             <c:if test="${result.facets.languages.containsHit}">
                 <p>Languages</p>
                 <c:forEach var="bucket" items="${result.facets.languages.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value='<%= new java.util.Locale((String) pageContext.getAttribute("bucketValue")).getDisplayLanguage(request.getLocale()) %>'/>
                     <c:choose>
                         <c:when test="${param.language != null}">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.tags.containsHit}">
                 <p>Tags</p>
                 <c:forEach var="bucket" items="${result.facets.tags.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="tag" value="<%= tm.resolve((String) pageContext.getAttribute("bucketValue")) %>"/>
                     <c:if test="${tag != null}">
                         <c:set var="label" value="${tag.title}"/>
                         <c:choose>
                             <c:when test="<%= request.getParameter("tag") != null && java.util.Arrays.asList(request.getParameterValues("tag")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="tag" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                             <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="tag" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                         </c:choose><br/>
                     </c:if>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.mimeTypes.containsHit}">
                 <jsp:useBean id="fileTypes" class="com.day.cq.wcm.foundation.FileTypes"/>
                 <p>File types</p>
                 <c:forEach var="bucket" items="${result.facets.mimeTypes.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value="${fileTypes[bucket.value]}"/>
                     <c:choose>
                         <c:when test="<%= request.getParameter("mimeType") != null && java.util.Arrays.asList(request.getParameterValues("mimeType")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.lastModified.containsHit}">
                 <p>Last Modified</p>
                 <c:forEach var="bucket" items="${result.facets.lastModified.buckets}">
                     <c:choose>
                         <c:when test="${param.from == bucket.from && param.to == bucket.to}">${bucket.value} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/><c:if test="${bucket.from != null}"><cq:addParam name="from" value="${bucket.from}"/></c:if><c:if test="${bucket.to != null}"><cq:addParam name="to" value="${bucket.to}"/></c:if></cq:requestURL>">${bucket.value} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
   
         <c:if test="${fn:length(search.relatedQueries) > 0}">
   
          <br/><br/><div class="related">
           <fmt:message key="relatedSearchesText"/>
           <c:forEach var="rq" items="${search.relatedQueries}">
               <a href="${currentPage.path}.html?q=${rq}"><c:out value="${rq}"/></a>
           </c:forEach></div>
         </c:if>
         </div>
   
         <c:if test="${fn:length(result.resultPages) > 1}">
           <div class="pagination">
               <fmt:message key="resultPagesText"/>
           <c:if test="${result.previousPage != null}">
             <a href="${result.previousPage.URL}"><fmt:message key="previousText"/></a>
           </c:if>
           <c:forEach var="page" items="${result.resultPages}">
             <c:choose>
               <c:when test="${page.currentPage}">${page.index + 1}</c:when>
               <c:otherwise>
                 <a href="${page.URL}">${page.index + 1}</a>
               </c:otherwise>
             </c:choose>
           </c:forEach>
           <c:if test="${result.nextPage != null}">
             <a href="${result.nextPage.URL}"><fmt:message key="nextText"/></a>
           </c:if>
           </div>
         </c:if>
         </div>
   
     </c:otherwise>
   </c:choose>
   ```

1. Speichern Sie die Änderungen.

#### Einschließen eines Suchfelds in die contentpage-Komponente {#including-a-search-box-in-the-contentpage-component}

Gehen Sie wie folgt vor, um ein Sucheingabefeld in den linken Bereich Ihrer Inhaltsseite einzuschließen:

1. Öffnen Sie in CRXDE Lite die Datei `left.jsp` unter `/apps/mywebsite/components/contentpage` und suchen Sie den folgenden Code (Zeile 2):

   ```xml
   %><div class="left">
   ```

1. Fügen Sie den folgenden Code ein **before** diese Zeile:

   ```java
   %><%@ page import="com.day.text.Text"%><%
   %><% String docroot = currentDesign.getPath();
   String home = Text.getAbsoluteParent(currentPage.getPath(), 2);%><%
   ```

1. Suchen Sie die folgende Codezeile:

   ```xml
   <div>search</div>
   ```

1. Ersetzen Sie diese Codezeile durch den folgenden Code und speichern Sie die Änderungen:

   ```java
   <div class="form_1">
        <form class="geo" action="<%= home %>/toolbar/search.html" id="form" >
             <p>
                  <input class="geo" type="text" name="q"><br>
                  <a href="<%= home %>/toolbar/search.html" class="link_1">advanced search</a>
             </p>
        </form>
   </div>
   ```

1. Laden Sie in Ihrem Browser die Seite „Produkte“ neu. Die Suchkomponente sieht wie folgt aus:

   ![chlimage_1-57](assets/chlimage_1-57.png)

#### Einschließen der Suchkomponente in die Suchseite {#including-the-search-component-in-the-search-page}

In diesem Abschnitt fügen Sie Ihre Suchkomponente zum Absatzsystem hinzu.

1. Öffnen Sie in Ihrem Browser die Seite „Produkte“.
1. Klicken Sie im Sidekick auf das Symbol Designmodus .
1. Klicken Sie im Baustein &quot;Design von par&quot;(unter dem Suchtitel) auf &quot;Bearbeiten&quot;.
1. Scrollen Sie im Dialogfeld nach unten zum  **Meine Websites** Gruppe, wählen Sie **Meine Suchkomponente** und klicken Sie auf **OK**.
1. Klicken Sie im Sidekick auf das Dreieck, um zum Bearbeitungsmodus zurückzukehren.
1. Ziehen Sie die Komponente &quot;My Search&quot;aus dem Sidekick in den Rahmen parsys . Sie sieht wie folgt aus:

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. Navigieren Sie zur Seite „Produkte“. Suchen Sie im Eingabefeld nach Kunden und drücken Sie die Eingabetaste. Sie werden zur Suchseite weitergeleitet. Wechseln Sie in den Vorschaumodus: Die Ausgabe weist folgendes Format auf:

   ![chlimage_1-59](assets/chlimage_1-59.png)

### Einschließen der Iparsys-Komponente {#including-the-iparsys-component}

In diesem Abschnitt schließen Sie die Komponente Vererbungs-Absatzsystem (iparsys) ein, die eine der Foundation-Komponenten ist. Mit dieser Komponente können Sie eine Struktur von Absätzen auf einer übergeordneten Seite erstellen und die Absätze von untergeordneten Seiten übernehmen lassen.

Für diese Komponente können Sie mehrere Parameter sowohl im Bearbeitungs- als auch im Designmodus festlegen.

1. Navigieren Sie in CRXDE Lite zu `/apps/mywebsite/components/contentpage`, öffnen Sie die Datei `right.jsp`und ersetzen Sie:

   ```java
   <div>iparsys</div>
   ```

   durch:

   ```java
   <cq:include path="rightpar" resourceType="foundation/components/iparsys" />
   ```

1. Speichern Sie die Änderungen.
1. Laden Sie in Ihrem Browser die Seite **Produkte** neu. Die Seite sieht nun insgesamt wie folgt aus:

   ![chlimage_1-5](assets/chlimage_1-5.jpeg)
