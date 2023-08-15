---
title: Entwickeln von Sandbox-Anwendungen
seo-title: Develop Sandbox Application
description: Entwickeln von Anwendungen mithilfe von Foundation-Skripten
seo-description: Develop application using foundation scripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: 7ac0056c-a742-49f4-8312-2cf90ab9f23a
source-git-commit: 10227bcfcfd5a9b0f126fee74dce6ec7842f5e95
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 7%

---

# Entwickeln von Sandbox-Anwendungen  {#develop-sandbox-application}

In diesem Abschnitt wurde die Vorlage jetzt im [Erstanwendung](initial-app.md) und den in der [anfänglicher Inhalt](initial-content.md) kann die Anwendung mithilfe von Foundation-Skripten entwickelt werden, einschließlich der Möglichkeit, das Authoring mit Communities-Komponenten zu aktivieren. Am Ende dieses Abschnitts wird die Website funktionieren.

## Verwenden von Foundation-Seitenskripten {#using-foundation-page-scripts}

Das Standardskript, das erstellt wird, wenn die Komponente, die die PayPage-Vorlage rendert, hinzugefügt wurde, wird geändert, um die head.jsp der Foundation-Seite und eine lokale body.jsp einzuschließen.

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

1. Ersetzen Sie &quot; // TODO ...&quot;durch Skripte für den Kopf- und Hauptteil von &lt;html>.

   Mit einem Supertyp von `foundation/components/page`, wird jedes Skript, das nicht in diesem Ordner definiert ist, in ein Skript in `/apps/foundation/components/page` Ordner (sofern vorhanden), andernfalls ein Skript in `/libs/foundation/components/page` Ordner.

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

1. Das Foundation-Skript `head.jsp` muss nicht überlagert werden, aber das Foundation-Skript `body.jsp` leer ist.

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

* Standard-Benutzeroberfläche: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

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
* Titel (Fundament)

>[!NOTE]
>
>Die für die Seitenpar aktivierten Komponenten werden im Repository als Wert der Variablen `components` -Eigenschaft der
>
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` Knoten.

## Landingpage {#landing-page}

In einer mehrsprachigen Umgebung würde die Stammseite ein Skript enthalten, das die Anfrage vom Client analysiert, um die bevorzugte Sprache zu bestimmen.

In diesem einfachen Beispiel wird die Stammseite statisch so eingestellt, dass sie zur englischen Seite weitergeleitet wird, die in Zukunft als Haupt-Landingpage mit einem Link zur Wiedergabeseite entwickelt werden kann.

Ändern Sie die Browser-URL in die Stammseite: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Symbol Seiteninformationen auswählen
* Auswählen **[!UICONTROL Eigenschaften öffnen]**
* Auf der Registerkarte ERWEITERT

   * Navigieren Sie zum Eintrag Umleiten zu **[!UICONTROL Websites]** > **[!UICONTROL SCF-Sandbox-Site]** > **[!UICONTROL SCF-Sandbox]**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL OK]**

Sobald die Site veröffentlicht wurde, wird das Browsen zur Stammseite in einer Veröffentlichungsinstanz zur englischen Seite weitergeleitet.

Der letzte Schritt vor dem Abspielen mit den SCF-Communities-Komponenten besteht darin, einen Client Library Folder (clientlibs) hinzuzufügen ... [Hinzufügen von ClientLibs](add-clientlibs.md)
