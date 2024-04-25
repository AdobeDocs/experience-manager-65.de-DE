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

In diesem Abschnitt wird die Vorlage jetzt im [Erstanwendung](initial-app.md) und den in der [anfänglicher Inhalt](initial-content.md) können Sie die Anwendung entwickeln. Dies geschieht mithilfe von Foundation-Skripten, die die Möglichkeit bieten, das Authoring mit Communities-Komponenten zu aktivieren. Am Ende dieses Abschnitts befindet sich eine voll funktionsfähige Website.

## Verwenden von Foundation-Seitenskripten {#using-foundation-page-scripts}

Das Standardskript, das erstellt wird, wenn die Komponente, die die PayPage-Vorlage rendert, hinzugefügt wurde, umfasst die head.jsp der Foundation-Seite und eine lokale body.jsp.

### Superressourcentyp {#super-resource-type}

Der erste Schritt besteht darin, eine Eigenschaft vom Typ Ressource Supertype zum `/apps/an-scf-sandbox/components/playpage` -Knoten, damit er die Skripte und Eigenschaften des Supertyps übernimmt.

Verwenden von CRXDE Lite:

1. Knoten auswählen `/apps/an-scf-sandbox/components/playpage`.
1. Geben Sie auf der Registerkarte &quot;Eigenschaften&quot;eine neue Eigenschaft mit den folgenden Werten ein:

   Name: `sling:resourceSuperType`

   Typ: `String`

   Wert: `foundation/components/page`

1. Klicken Sie auf Grün **[!UICONTROL +Hinzufügen]** Schaltfläche.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   ![page-script](assets/page-script.png)

### Kopf- und Textskripte {#head-and-body-scripts}

1. In **CRXDE Lite** Explorer-Bereich, navigieren Sie zu `/apps/an-scf-sandbox/components/playpage` und doppelklicken Sie auf die Datei `playpage.jsp` , um es im Bearbeitungsfenster zu öffnen.

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

1. Da Sie Skript-Tags zum Öffnen/Schließen kennen, ersetzen Sie &quot; // TODO ...&quot;durch . `includes` von Skripten für die Kopf- und Körperteile von &lt;html>.

   Mit einem Supertyp von `foundation/components/page`, wird jedes Skript, das nicht in diesem Ordner definiert ist, in ein Skript in aufgelöst. `/apps/foundation/components/page` Ordner (sofern vorhanden) oder ein Skript in `/libs/foundation/components/page` Ordner.

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

1. Überlagern des Foundation-Skripts `head.jsp` ist nicht erforderlich, aber das Foundation-Skript `body.jsp` leer ist.

   So richten Sie für das Authoring eine Überlagerung ein `body.jsp` mit einem lokalen Skript und ein Absatzsystem (parsys) im Text einschließen:

   1. Navigieren Sie zu `/apps/an-scf-sandbox/components`.
   1. Wählen Sie den `playpage`-Knoten aus.
   1. Rechtsklicken Sie auf und wählen Sie `Create > Create File...`

      * Name: **body.jsp**

   1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

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

1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

**Zeigen Sie die Seite in einem Browser im Bearbeitungsmodus an:**

* Standardbenutzeroberfläche: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

Sie sollten nicht nur die Überschrift sehen **Community Play**, aber auch die Benutzeroberfläche zum Bearbeiten des Seiteninhalts.

Das seitliche Bedienfeld &quot;Assets/Komponente&quot;wird angezeigt, wenn das seitliche Bedienfeld geöffnet ist und das Fenster breit genug ist, um sowohl den Seiteninhalt als auch den Seiteninhalt anzuzeigen.

![view-page](assets/view-page.png)

* Klassische Benutzeroberfläche: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Im Folgenden wird gezeigt, wie die Wiedergabeseite in der klassischen Benutzeroberfläche einschließlich des Content Finders (cf) angezeigt wird:

![play-page-view](assets/play-page-view.png)

## Communities-Komponenten {#communities-components}

Um Communities-Komponenten für das Authoring zu aktivieren, befolgen Sie die folgenden Anweisungen:

* [Zugreifen auf Communities-Komponenten](basics.md#accessing-communities-components)

Beginnen Sie für die Zwecke dieser Sandbox mit diesen **Communities** Komponenten (aktivieren, indem Sie das Kontrollkästchen aktivieren):

* Kommentare
* Forum
* Bewertung
* Bewertungen
* Bewertungszusammenfassung (Anzeige)
* Abstimmung

Wählen Sie außerdem **[!UICONTROL Allgemein]** Komponenten wie

* Bild
* Tabelle
* Text
* Titel (Foundation)

>[!NOTE]
>
>Die für die Seitenpar aktivierten Komponenten werden im Repository als Wert der Variablen `components` -Eigenschaft der
>
>Knoten `/etc/designs/an-scf-sandbox/jcr:content/playpage/par`.

## Landingpage {#landing-page}

In einer mehrsprachigen Umgebung würde die Stammseite ein Skript enthalten, das die Anfrage vom Client analysiert, um die bevorzugte Sprache zu bestimmen.

In diesem Beispiel wird die Stammseite statisch so eingestellt, dass sie zur englischen Seite weitergeleitet wird, die in Zukunft als Haupt-Landingpage mit einem Link zur Wiedergabeseite entwickelt werden kann.

Ändern Sie die Browser-URL in die Stammseite: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Symbol Seiteninformationen auswählen
* Auswählen **[!UICONTROL Eigenschaften öffnen]**
* Auf der Registerkarte ERWEITERT

   * Navigieren Sie zum Eintrag Umleiten zu **[!UICONTROL Websites]** > **[!UICONTROL SCF-Sandbox-Site]** > **[!UICONTROL SCF-Sandbox]**
   * Klicks **[!UICONTROL OK]**

* Klicks **[!UICONTROL OK]**

Nachdem die Site veröffentlicht wurde, wird beim Navigieren zur Stammseite in einer Veröffentlichungsinstanz die englische Seite umgeleitet.

Der letzte Schritt vor dem Abspielen mit den Communities-SCF-Komponenten besteht darin, einen Client-Bibliotheksordner (clientlibs) hinzuzufügen ... [Clientlibs hinzufügen](add-clientlibs.md)
