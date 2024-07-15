---
title: Entwickeln von Sandbox-Anwendungen
description: Erfahren Sie, wie Sie eine Sandbox-Anwendung entwickeln, die Foundation-Skripte verwendet und die Möglichkeit bietet, das Authoring mit Communities-Komponenten zu aktivieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 7ac0056c-a742-49f4-8312-2cf90ab9f23a
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 5%

---

# Entwickeln von Sandbox-Anwendungen  {#develop-sandbox-application}

In diesem Abschnitt können Sie jetzt, da die Vorlage im Abschnitt [Initial application](initial-app.md) eingerichtet ist und die ersten Seiten, die im Abschnitt [Initialinhalt](initial-content.md) erstellt wurden, die Anwendung entwickeln. Dies geschieht mithilfe von Foundation-Skripten, die die Möglichkeit bieten, das Authoring mit Communities-Komponenten zu aktivieren. Am Ende dieses Abschnitts befindet sich eine voll funktionsfähige Website.

## Verwenden von Foundation-Seitenskripten {#using-foundation-page-scripts}

Das Standardskript, das erstellt wird, wenn die Komponente, die die PayPage-Vorlage rendert, hinzugefügt wurde, umfasst die head.jsp der Foundation-Seite und eine lokale body.jsp.

### Superressourcentyp {#super-resource-type}

Der erste Schritt besteht darin, dem Knoten `/apps/an-scf-sandbox/components/playpage` eine Eigenschaft vom Typ &quot;resource super type&quot;hinzuzufügen, damit er die Skripte und Eigenschaften des Supertyps übernimmt.

Verwenden von CRXDE Lite:

1. Wählen Sie den Knoten `/apps/an-scf-sandbox/components/playpage` aus.
1. Geben Sie auf der Registerkarte &quot;Eigenschaften&quot;eine neue Eigenschaft mit den folgenden Werten ein:

   Name: `sling:resourceSuperType`

   Typ: `String`

   Wert: `foundation/components/page`

1. Klicken Sie auf die grüne Schaltfläche **[!UICONTROL +Add]**.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   ![page-script](assets/page-script.png)

### Kopf- und Textskripte {#head-and-body-scripts}

1. Navigieren Sie im Explorer-Bereich **CRXDE Lite** zu `/apps/an-scf-sandbox/components/playpage` und doppelklicken Sie auf die Datei `playpage.jsp`, um sie im Bearbeitungsfenster zu öffnen.

   `/apps/an-scf-sandbox/components/playpage/playpage.jsp`

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

1. Ersetzen Sie &quot; // TODO ...&quot; durch &quot;`includes`&quot; von Skripten für die Kopf- und Textteile von &lt;html>, da Sie Skript-Tags zum Öffnen/Schließen kennen.

   Mit dem Supertyp `foundation/components/page` wird jedes Skript, das nicht in diesem Ordner definiert ist, in ein Skript im Ordner `/apps/foundation/components/page` aufgelöst (sofern vorhanden) oder in ein Skript im Ordner `/libs/foundation/components/page`.

   `/apps/an-scf-sandbox/components/playpage/playpage.jsp`

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

1. Das Überlagern des Foundation-Skripts `head.jsp` ist nicht erforderlich, aber das Foundation-Skript `body.jsp` ist leer.

   Um dies für die Bearbeitung einzurichten, überlagern Sie `body.jsp` mit einem lokalen Skript und fügen Sie ein Absatzsystem (parsys) in den Text ein:

   1. Navigieren Sie zu `/apps/an-scf-sandbox/components`.
   1. Wählen Sie den `playpage`-Knoten aus.
   1. Klicken Sie mit der rechten Maustaste und wählen Sie `Create > Create File...` aus.

      * Name: **body.jsp**

   1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   Öffnen Sie `/apps/an-scf-sandbox/components/playpage/body.jsp` und fügen Sie im folgenden Text ein:

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

1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

**Zeigen Sie die Seite in einem Browser im Bearbeitungsmodus an:**

* Standardbenutzeroberfläche: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

Sie sollten nicht nur die Überschrift **Community-Wiedergabe** sehen, sondern auch die Benutzeroberfläche zum Bearbeiten von Seiteninhalten.

Das seitliche Bedienfeld Assets/Komponente wird angezeigt, wenn sowohl das seitliche Bedienfeld geöffnet ist als auch das Fenster breit genug ist, um sowohl den Seiteninhalt als auch den Seiteninhalt anzuzeigen.

![view-page](assets/view-page.png)

* Klassische Benutzeroberfläche: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Im Folgenden wird gezeigt, wie die Wiedergabeseite in der klassischen Benutzeroberfläche einschließlich des Content Finders (cf) angezeigt wird:

![play-page-view](assets/play-page-view.png)

## Communities-Komponenten {#communities-components}

Um Communities-Komponenten für das Authoring zu aktivieren, befolgen Sie die folgenden Anweisungen:

* [Zugreifen auf Communities-Komponenten](basics.md#accessing-communities-components)

Beginnen Sie für diese Sandbox mit den folgenden **Communities**-Komponenten (aktivieren Sie sie, indem Sie das Kontrollkästchen aktivieren):

* Kommentare
* Forum
* Bewertung
* Bewertungen
* Bewertungszusammenfassung (Anzeige)
* Abstimmung

Wählen Sie außerdem die Komponenten **[!UICONTROL Allgemein]** aus, z. B.

* Bild
* Tabelle
* Text
* Titel (Foundation)

>[!NOTE]
>
>Die für die Seitenpar aktivierten Komponenten werden im Repository als Wert der Eigenschaft `components` der Variablen
>
>Knoten `/etc/designs/an-scf-sandbox/jcr:content/playpage/par`.

## Landingpage {#landing-page}

In einer mehrsprachigen Umgebung würde die Stammseite ein Skript enthalten, das die Anfrage vom Client analysiert, um die bevorzugte Sprache zu bestimmen.

In diesem Beispiel wird die Stammseite statisch so eingestellt, dass sie zur englischen Seite weitergeleitet wird, die in Zukunft als Haupt-Landingpage mit einem Link zur Wiedergabeseite entwickelt werden kann.

Ändern Sie die Browser-URL in die Stammseite: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Symbol Seiteninformationen auswählen
* Wählen Sie **[!UICONTROL Eigenschaften öffnen]**
* Auf der Registerkarte ERWEITERT

   * Navigieren Sie für den Umleitungs-Eintrag zu **[!UICONTROL Websites]** > **[!UICONTROL SCF Sandbox Site]** > **[!UICONTROL SCF Sandbox]**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL OK]**

Nachdem die Site veröffentlicht wurde, wird beim Navigieren zur Stammseite in einer Veröffentlichungsinstanz die englische Seite umgeleitet.

Der letzte Schritt vor dem Abspielen mit den Communities-SCF-Komponenten besteht darin, einen Client-Bibliotheksordner (clientlibs) hinzuzufügen ... [Clientlibs hinzufügen](add-clientlibs.md)
