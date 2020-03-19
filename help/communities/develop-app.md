---
title: Sandbox-Anwendung entwickeln
seo-title: Sandbox-Anwendung entwickeln
description: Entwickeln von Anwendungen mithilfe von Stiftungsskripten
seo-description: Entwickeln von Anwendungen mithilfe von Stiftungsskripten
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
translation-type: tm+mt
source-git-commit: d6c8bbb9aa763a2eb6660b6b6755aba75241e394

---


# Sandbox-Anwendung entwickeln {#develop-sandbox-application}

In diesem Abschnitt kann die Anwendung nun, da die Vorlage im Abschnitt [Erstanwendung](initial-app.md) eingerichtet wurde und die ersten Seiten, die im Abschnitt [Erstinhalt](initial-content.md) festgelegt wurden, mithilfe von Stiftungsskripten entwickelt werden, einschließlich der Möglichkeit, das Authoring mit Communities-Komponenten zu aktivieren. Am Ende dieses Abschnitts wird die Website funktionsfähig sein.

## Using Foundation Page Scripts {#using-foundation-page-scripts}

Das Standardskript, das erstellt wird, wenn die Komponente, die die PayPal-Vorlage rendert, hinzugefügt wurde, wird geändert, um head.jsp und eine lokale body.jsp der Gründungsseite einzuschließen.

### Super Resource Type {#super-resource-type}

Der erste Schritt besteht darin, dem `/apps/an-scf-sandbox/components/playpage` Knoten eine Eigenschaft des Supertyps der Ressource hinzuzufügen, damit die Skripte und Eigenschaften des Supertyps übernommen werden.

Verwenden von CRXDE Lite:

<!--Resolve steps below-->
    Name: `sling:resourceSuperType`
    Type: `String`
    Value: `foundation/components/page`

1. Klicken Sie auf die grüne **[!UICONTROL [+]Hinzufügen]**
1. Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-231](assets/chlimage_1-231.png)

### Kopf- und Textskripte {#head-and-body-scripts}

1. Navigieren Sie im **CRXDE Lite** -Explorer-Bereich zu der Datei `/apps/an-scf-sandbox/components/playpage` und klicken Sie mit der Dublette darauf, `playpage.jsp` um sie im Bearbeitungsbereich zu öffnen.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp}

```xml
<%--

  An SCF Sandbox Play Component component.

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %><%
%><%
 // TODO add your code here
%>
```

1. Ersetzen Sie &quot; // TODO ...&quot;, da Sie sich der öffnenden/schließenden Skript-Tags bewusst sind. mit Skripten für die Kopf- und Textelemente von &lt;html>.

   Bei einem Super-Typ von `foundation/components/page`wird jedes Skript, das nicht in diesem Ordner definiert ist, in einem Skript im `/apps/foundation/components/page` Ordner (sofern vorhanden) aufgelöst, andernfalls in einem Skript im `/libs/foundation/components/page` Ordner.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp-1}

```xml
<%--

    An SCF Sandbox Play Component component: playpage.jsp

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %>
<html>
  <cq:include script="head.jsp"/>
  <cq:include script="body.jsp"/>
</html>
```

1. Das Stiftungsskript `head.jsp` muss nicht überlagert werden, aber das Stiftungsskript `body.jsp` ist leer.

   Um das Authoring einzurichten, überlagern Sie `body.jsp` mit einem lokalen Skript und fügen Sie ein Absatzsystem (parsys) in den Text ein:

   1. Navigieren Sie zu `/apps/an-scf-sandbox/components`
   1. Wählen Sie den `playpage`Knoten
   1. Right-click and select `Create > Create File...`

      * Name: **body.jsp**
   1. Klicken Sie auf **[!UICONTROL Alle speichern]**
   Öffnen `/apps/an-scf-sandbox/components/playpage/body.jsp` und fügen Sie Folgendes ein:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

**Ansicht der Seite in einem Browser im Bearbeitungsmodus:**

* Standard-Benutzeroberfläche: [http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html](http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.md)

Sie sollten nicht nur die Überschrift **Community Play** sehen, sondern auch die Benutzeroberfläche zum Bearbeiten von Seiteninhalten.

Das Seitenbedienfeld &quot;Elemente/Komponenten&quot;wird angezeigt, wenn sowohl das Seitenbedienfeld geöffnet ist als auch das Fenster breit genug ist, damit sowohl der Seiteninhalt als auch der Seiteninhalt angezeigt werden können.

![chlimage_1-232](assets/chlimage_1-232.png)

* Klassische Benutzeroberfläche: [http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html](http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html)

So wird die Wiedergabeseite in der klassischen Benutzeroberfläche angezeigt, auch mit der Inhaltssuche (siehe ):

![chlimage_1-233](assets/chlimage_1-233.png)

## Communities-Komponenten {#communities-components}

Um Communities-Komponenten für das Authoring zu aktivieren, führen Sie Beginn wie folgt aus:

* [Auf Communities-Komponenten zugreifen](basics.md#accessing-communities-components)

Für die Zwecke dieser Sandbox ist der Beginn mit diesen **Communities** -Komponenten (aktivieren, indem Sie das Kontrollkästchen aktivieren):

* Comments
* Forum
* Bewertung
* Reviews
* Bewertungszusammenfassung (Anzeige)
* Abstimmung

Wählen Sie außerdem **[!UICONTROL Allgemeine]** Komponenten, wie

* Bild
* Tabelle
* Text
* Titel (Foundation)

>[!NOTE]
>
>Die für &quot;pagePar&quot;aktivierten Komponenten werden im Repository als Wert der `components` Eigenschaft
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` Knoten.

## Landingpage {#landing-page}

In einer mehrsprachigen Umgebung enthält die Stammeseite ein Skript, das die Anforderung des Clients zur Bestimmung der bevorzugten Sprache analysiert.

In diesem einfachen Beispiel wird die Root-Landingpage statisch so eingestellt, dass sie auf die englische Seite umgeleitet wird, die in der Zukunft als Hauptseite mit einem Link zur play-Seite entwickelt werden kann.

Ändern Sie die Browser-URL in die Stammseite: [http://localhost:4502/editor.html/content/an-scf-sandbox.html](https://locahost:4502/editor.html/content/an-scf-sandbox.html)

* Symbol &quot;Seiteninformationen&quot;auswählen
* Eigenschaften **[!UICONTROL öffnen auswählen]**
* Registerkarte &quot;ERWEITERT&quot;

   * Für den Eintrag &quot;Umleitung&quot;navigieren Sie zu **[!UICONTROL Websites > SCF Sandbox-Site > SCF Sandbox]**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL OK]**

Sobald die Site veröffentlicht wurde, führt das Browsen zur Root-Seite in einer Veröffentlichungsinstanz eine Umleitung zur englischen Seite durch.

Der letzte Schritt vor der Wiedergabe mit den Communities SCF-Komponenten ist, einen Client Library Folder (clientlibs) hinzuzufügen .... [Hinzufügen Clienlibs](add-clientlibs.md)