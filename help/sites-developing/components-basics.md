---
title: Adobe Experience Manager-Komponenten - Grundlagen
description: Wenn Sie mit der Entwicklung neuer Komponenten beginnen, müssen Sie die Grundlagen ihrer Struktur und Konfiguration kennen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
legacypath: /content/docs/en/aem/6-0/develop/components/components-develop
exl-id: 7ff92872-697c-4e66-b654-15314a8cb429
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '4843'
ht-degree: 61%

---

# Adobe Experience Manager-Komponenten (AEM) - Grundlagen{#aem-components-the-basics}

Wenn Sie mit der Entwicklung neuer Komponenten beginnen, müssen Sie die Grundlagen ihrer Struktur und Konfiguration kennen.

Dieser Prozess umfasst das Lesen der Theorie und das Betrachten der breiten Palette von Komponentenimplementierungen in einer AEM Standardinstanz. Dieser letztgenannte Ansatz wird etwas dadurch erschwert, dass AEM zwar auf eine neue standardmäßige, moderne, Touch-optimierte Benutzeroberfläche umgestellt wurde, die klassische Benutzeroberfläche jedoch weiterhin unterstützt.

## Übersicht {#overview}

In diesem Abschnitt werden zentrale Konzepte und Schwierigkeiten erläutert. Er bietet so einen guten Einstieg in die Entwicklung eigener Komponenten.

### Planung {#planning}

Bevor Sie beginnen, Ihre Komponente zu konfigurieren oder zu kodieren, sollten Sie Folgendes fragen:

* Was genau soll die neue Komponente tun?
   * Eine klare Spezifikation hilft in allen Phasen der Entwicklung, Tests und Übergabe. Details können sich im Laufe der Zeit ändern, woraufhin die Spezifikation jedoch aktualisiert werden kann (Änderungen sollten jedoch ebenso dokumentiert werden).
* Müssen Sie die Komponente komplett neu entwickeln oder können Sie die Grundlagen von einer vorhandenen Komponente übernehmen?
   * Sie müssen das Rad nicht neu erfinden.
   * Es gibt mehrere Mechanismen, die von AEM bereitgestellt werden, mit denen Sie Details von einer anderen Komponentendefinition erben und erweitern können, einschließlich Überschreiben, Überlagerung und [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md).
* Ist für Ihre Komponente eine Logik zum Auswählen oder Bearbeiten des Inhalts erforderlich?
   * Die Logik sollte getrennt von der Ebene der Benutzeroberfläche aufbewahrt werden. HTL dient dazu, dies sicherzustellen.
* Benötigt Ihre Komponente eine CSS-Formatierung?
   * Eine CSS-Formatierung sollte getrennt von den Komponentendefinitionen aufbewahrt werden. Legen Sie Konventionen für die Benennung der HTML-Elemente fest, damit Sie sie über externe CSS-Dateien modifizieren können.
* Welche Sicherheitsaspekte sollte ich beachten?
   * Siehe [Sicherheitscheckliste - Best Practices für die Entwicklung](/help/sites-administering/security-checklist.md#development-best-practices) für weitere Details.

### Touch-optimierte und klassische Benutzeroberfläche {#touch-enabled-vs-classic-ui}

Bevor ernsthafte Diskussionen über die Entwicklung von Komponenten beginnen, müssen Sie wissen, welche Benutzeroberfläche Ihre Autoren verwenden:

* **Touch-optimierte Benutzeroberfläche**
  [Die Standardbenutzeroberfläche](/help/sites-developing/touch-ui-concepts.md) basiert auf dem einheitlichen Benutzererlebnis für die Adobe Experience Cloud und verwendet dabei die zugrunde liegenden Technologien von [Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui) und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui).
* **Klassische Benutzeroberfläche**
Eine auf der ExtJS-Technologie basierende Benutzeroberfläche, die seit AEM 6.4 veraltet ist.

Siehe [Benutzeroberfläche Recommendations für Kunden](/help/sites-deploying/ui-recommendations.md) für weitere Details.

Komponenten können implementiert werden, um die Touch-optimierte Benutzeroberfläche, die klassische Benutzeroberfläche oder beides zu unterstützen. Eine Standardinstanz umfasst auch vorkonfigurierte Komponenten, die ursprünglich für die klassische oder die Touch-optimierte Benutzeroberfläche oder beide Versionen entwickelt wurden.

Die Grundlagen von beiden werden auf dieser Seite behandelt und wie sie erkannt werden.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung der Touch-optimierten Benutzeroberfläche, um von der neuesten Technologie zu profitieren. [AEM-Modernisierungs-Tools](modernization-tools.md) können die Migration vereinfachen.

### Inhaltslogik und Rendering-Markup  {#content-logic-and-rendering-markup}

Adobe empfiehlt, den für das Markup und Rendering verantwortlichen Code von dem Code getrennt zu halten, der die Logik steuert, mit der der Komponenteninhalt ausgewählt wird.

Diese Philosophie wird von [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de): eine Vorlagensprache, die gezielt darauf beschränkt ist, sicherzustellen, dass eine echte Programmiersprache zur Definition der zugrunde liegenden Geschäftslogik verwendet wird. Diese (optionale) Logik wird von HTL mit einem bestimmten Befehl aufgerufen. Dieser Mechanismus hebt den Code hervor, der für eine bestimmte Ansicht aufgerufen wird, und lässt bei Bedarf eine spezifische Logik für unterschiedliche Ansichten derselben Komponente zu.

### HTL vs. JSP {#htl-vs-jsp}

HTL ist eine HTML-Vorlagensprache, die mit AEM 6.0 eingeführt wurde.

Die Diskussion darüber, ob [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) oder JSP (Java™ Server Pages) bei der Entwicklung eigener Komponenten sollten unkompliziert sein, da HTL jetzt die empfohlene Skriptsprache für AEM ist.

Sowohl HTL als auch JSP können für die Entwicklung von Komponenten für die klassische und die Touch-optimierte Benutzeroberfläche verwendet werden. Zwar wird häufig angenommen, dass HTL nur für die Touch-optimierte und JSP für die klassische Benutzeroberfläche ist, doch diese Vermutung ist falsch und wohl Die Touch-optimierte Benutzeroberfläche und die HTL wurden in AEM ungefähr im selben Zeitraum integriert. Da HTL nun die empfohlene Sprache ist, wird sie für neue Komponenten verwendet, die meistens für die Touch-optimierte Benutzeroberfläche ausgelegt sind.

>[!NOTE]
>
>Ausnahme hiervon sind die Foundation-Formularfelder der Granite-Benutzeroberfläche (wie sie in Dialogfeldern verwendet werden). Für sie ist die Verwendung von JSP erforderlich.

### Entwickeln eigener Komponenten {#developing-your-own-components}

Informationen zum Erstellen eigener Komponenten für die entsprechende Benutzeroberfläche finden Sie unter (nach dem Lesen dieser Seite):

* [AEM-Komponenten für die Touch-optimierte Benutzeroberfläche](/help/sites-developing/developing-components.md)
* [AEM-Komponenten für die klassische Benutzeroberfläche](/help/sites-developing/developing-components-classic.md)

Eine schnelle Möglichkeit für den Einstieg ist das Kopieren einer vorhandenen Komponente und das anschließende Vornehmen der gewünschten Änderungen. Informationen zum Erstellen eigener Komponenten und Hinzufügen zum Absatzsystem finden Sie unter:

* [Entwickeln von Komponenten](/help/sites-developing/developing-components-samples.md) (Fokus auf der Touch-optimierten Benutzeroberfläche)

### Verschieben von Komponenten in die Veröffentlichungsinstanz {#moving-components-to-the-publish-instance}

Die Komponenten, die Inhalte rendern, müssen auf derselben AEM Instanz bereitgestellt werden wie der Inhalt. Daher müssen alle Komponenten, die für das Authoring und Rendern von Seiten in der Autoreninstanz verwendet werden, auf der Veröffentlichungsinstanz bereitgestellt werden. Nach der Bereitstellung sind die Komponenten zum Rendern aktivierter Seiten verfügbar.

Verwenden Sie die folgenden Tools, um Ihre Komponenten in die Veröffentlichungsinstanz zu verschieben:

* [Mit Package Manager](/help/sites-administering/package-manager.md) können Sie Ihre Komponenten zu einem Paket hinzufügen und in eine andere AEM-Instanz verschieben.
* [Verwenden des Replikations-Tools Tree aktivieren](/help/sites-authoring/publishing-pages.md#manage-publication) , um die Komponenten zu replizieren.

>[!NOTE]
>
>Diese Mechanismen können auch verwendet werden, um Ihre Komponente zwischen anderen Instanzen zu übertragen, z. B. von Ihrer Entwicklung auf Ihre Testinstanz.

### Komponenten, die von Anfang an zu beachten sind {#components-to-be-aware-of-from-the-start}

* Seite:

   * AEM verfügt über die Komponente *Seite* ( `cq:Page`).
   * Dies ist ein spezifischer Ressourcentyp, der für das Content Management wichtig ist.
      * Eine Seite entspricht einer Webseite mit Inhalten für Ihre Website.

* Absatzsysteme:

   * Das Absatzsystem ist ein wichtiger Teil einer Website, da es eine Liste von Absätzen verwaltet. Sie wird verwendet, um die einzelnen Komponenten zu speichern und zu strukturieren, die den tatsächlichen Inhalt enthalten.
   * Sie können Absätze im Absatzsystem erstellen, verschieben, kopieren und löschen.
   * Sie können auch die Komponenten auswählen, die in einem bestimmten Absatzsystem verwendet werden können.
   * In einer Standardinstanz stehen verschiedene Absatzsysteme zur Verfügung (z. B. `parsys`, ` [responsivegrid](/help/sites-authoring/responsive-layout.md)`).

## Struktur {#structure}

Die Struktur einer AEM-Komponente ist leistungsstark und flexibel. Die wichtigsten Aspekte sind:

* Ressourcentyp
* Komponentendefinition
* Eigenschaften und untergeordnete Knoten einer Komponente
* Dialogfelder
* Design-Dialogfelder
* Verfügbarkeit von Komponenten
* Komponenten und die von ihnen erstellten Inhalte

### Ressourcentyp {#resource-type}

Ein zentrales Element der Struktur ist der Ressourcentyp.

* Die Inhaltsstruktur deklariert Absichten.
* Der Ressourcentyp implementiert sie.

Dies ist eine Abstraktion, die sicherstellt, dass die Absicht auch dann die Zeit bleibt, wenn sich das Erscheinungsbild im Laufe der Zeit ändert.

### Komponentendefinition {#component-definition}

#### Grundlagen zu Komponenten {#component-basics}

Die Definition einer Komponente lässt sich wie folgt aufschlüsseln:

* AEM-Komponenten basieren auf [Sling](https://sling.apache.org/documentation.html).
* AEM Komponenten befinden sich (in der Regel) unter:

   * HTL: `/libs/wcm/foundation/components`
   * JSP: `/libs/foundation/components`

* Projekt- bzw. Website-spezifische Komponenten befinden sich (in der Regel) unter:

   * `/apps/<myApp>/components`

* AEM-Standardkomponenten sind als `cq:Component` definiert und haben die folgenden zentralen Elemente:

   * JCR-Eigenschaften:

     Eine Liste von jcr-Eigenschaften. Diese sind variabel und einige können optional sein, obwohl die grundlegende Struktur eines Komponentenknotens, seiner Eigenschaften und Unterknoten durch die Variable `cq:Component` Definition

   * Ressourcen:

     Sie definieren statische Elemente, die von der Komponente genutzt werden.

   * Skripte:

  Sie werden verwendet, um das Verhalten der entstandenen Instanz der Komponente zu implementieren.

* **Stammknoten**:

   * `<mycomponent> (cq:Component)` – Hierarchieknoten der Komponente.

* **Wichtige Eigenschaften**:

   * `jcr:title` – Komponententitel; wird beispielsweise als Kennzeichnung genutzt, wenn die Komponente im Komponenten-Browser oder Sidekick aufgeführt wird
   * `jcr:description` – Beschreibung der Komponente; kann als Mouseover-Hinweis im Komponenten-Browser oder Sidekick genutzt werden
   * Klassische Benutzeroberfläche:

      * `icon.png` – Symbol für diese Komponente
      * `thumbnail.png` – Bild, das angezeigt wird, wenn diese Komponente im Absatzsystem aufgeführt wird

   * Touch-optimierte Benutzeroberfläche

      * Siehe Abschnitt . [Komponentensymbol in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) für Details.

* **Wichtige untergeordnete Knoten**:

   * `cq:editConfig (cq:EditConfig)` – Definiert die Bearbeitungseigenschaften der Komponente und ermöglicht es, dass die Komponente im Komponenten-Browser oder Sidekick aufgeführt wird.

     Hinweis: Wenn die Komponente über ein Dialogfeld verfügt, wird sie automatisch im Komponenten-Browser oder Sidekick aufgeführt, selbst wenn die cq:editConfig nicht vorhanden ist.

   * `cq:childEditConfig (cq:EditConfig)` – Steuert Aspekte der Autoren-Benutzeroberfläche für untergeordnete Komponenten, die keine eigene `cq:editConfig` definieren.
   * Touch-optimierte Benutzeroberfläche:

      * `cq:dialog` ( `nt:unstructured`) – Dialogfeld für diese Komponente. Definiert die Oberfläche, über die Benutzer die Komponente konfigurieren und/oder Inhalte bearbeiten können.
      * `cq:design_dialog` ( `nt:unstructured`) – Design-Bearbeitung für diese Komponente.

   * Klassische Benutzeroberfläche:

      * `dialog` ( `cq:Dialog`) – Dialogfeld für diese Komponente. Definiert die Benutzeroberfläche, über die der Benutzer die Komponente konfigurieren, Inhalte bearbeiten oder beides.
      * `design_dialog` ( `cq:Dialog`) – Design-Bearbeitung für diese Komponente.

#### Komponentensymbol in der Touch-optimierten Benutzeroberfläche {#component-icon-in-touch-ui}

Das Symbol oder die Abkürzung für die Komponente wird mit JCR-Eigenschaften der Komponente definiert, wenn die Komponente vom Entwickler erstellt wird. Diese Eigenschaften werden in der folgenden Reihenfolge ausgewertet und die erste erkannte gültige Eigenschaft wird verwendet.

1. `cq:icon` – Zeichenfolgeneigenschaft, die auf ein Standardsymbol in der [Bibliothek der Coral-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/Coral.Icon.html) verweist, das im Komponenten-Browser angezeigt werden soll.
   * Verwenden Sie den Wert des HTML-Attributs des Coral-Symbols.
1. `abbreviation` – Zeichenfolgeneigenschaft, die die Abkürzung des Komponentennamens im Komponenten-Browser anpasst.
   * Die Abkürzung sollte auf zwei Zeichen beschränkt sein.
   * Wenn Sie eine leere Zeichenfolge angeben, wird die Abkürzung aus den ersten beiden Zeichen der `jcr:title` -Eigenschaft.
      * Beispiel: „Gr“ für „Grafik“
      * Zum Erstellen der Abkürzung wird der lokalisierte Titel verwendet.
   * Die Abkürzung wird nur übersetzt, wenn die Komponente die Eigenschaft `abbreviation_commentI18n` aufweist, die dann als Anweisung für eine Übersetzung genutzt wird.
1. `cq:icon.png` oder `cq:icon.svg` – Symbol für diese Komponente, das im Komponenten-Browser angezeigt wird.
   * Symbole von Standardkomponenten haben eine Größe von 20 x 20 Pixeln.
      * Größere Symbole werden (Client-seitig) herunterskaliert.
   * Die empfohlene Farbe ist rgb(112, 112, 112) > #707070.
   * Der Hintergrund von Symbolen von Standardkomponenten ist transparent.
   * Es werden nur `.png`- und `.svg`-Dateien unterstützt.
   * Wenn Sie über das Eclipse-Plug-in aus dem Dateisystem importieren, müssen Dateinamen als `_cq_icon.png` oder `_cq_icon.svg` zum Beispiel.
   * Wenn beide Formate vorliegen, hat `.png` Vorrang vor `.svg`

Wenn keine der oben genannten Eigenschaften ( `cq:icon`, `abbreviation`, `cq:icon.png`oder `cq:icon.svg`) finden Sie in der Komponente:

* Das System sucht nach denselben Eigenschaften für die übergeordneten Komponenten, die dem `sling:resourceSuperType` -Eigenschaft.
* Wenn auf der übergeordneten Komponentenebene nichts oder eine leere Abkürzung gefunden wird, erstellt das System die Abkürzung aus den ersten Buchstaben des `jcr:title` -Eigenschaft der aktuellen Komponente.

Um die Vererbung von Symbolen aus übergeordneten Komponenten abzubrechen, legen Sie eine leere `abbreviation` -Eigenschaft in der Komponente wird auf das Standardverhalten zurückgesetzt.

Die [Komponentenkonsole](/help/sites-authoring/default-components-console.md#component-details) zeigt an, wie das Symbol für eine bestimmte Komponente definiert ist.

#### Beispiel: SVG-Symbol {#svg-icon-example}

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" id="Layer_1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink" x="0px" y="0px"
     width="20px" height="20px" viewBox="0 0 20 20" enable-background="new 0 0 20 20" xml:space="preserve">
    <ellipse cx="5" cy="5" rx="3" ry="3" fill="#707070"/>
    <ellipse cx="15" cy="5" rx="4" ry="4" fill="#707070"/>
    <ellipse cx="5" cy="15" rx="5" ry="5" fill="#707070"/>
    <ellipse cx="15" cy="15" rx="4" ry="4" fill="#707070"/>
</svg>
```

### Eigenschaften und untergeordnete Knoten einer Komponente {#properties-and-child-nodes-of-a-component}

Viele der Knoten/Eigenschaften, die zum Definieren einer Komponente erforderlich sind, sind für beide Benutzeroberflächen gleich. Die Unterschiede bleiben dabei unabhängig, sodass Ihre Komponente in beiden Umgebungen funktionieren kann.

Eine Komponente ist ein Knoten des Typs `cq:Component` mit den folgenden Eigenschaften und untergeordneten Knoten:

<table>
 <tbody>
  <tr>
   <td><strong>Name <br /> </strong></td>
   <td><strong>Typ <br /> </strong></td>
   <td><strong>Beschreibung <br /> </strong></td>
  </tr>
  <tr>
   <td>.<br /> </td>
   <td><code>cq:Component</code></td>
   <td>Aktuelle Komponente. Eine Komponente weist den Knotentyp <code>cq:Component</code> auf.<br /> </td>
  </tr>
  <tr>
   <td><code>componentGroup</code></td>
   <td><code>String</code></td>
   <td>Gruppe, aus der die Komponente im Komponenten-Browser (Touch-optimierte Benutzeroberfläche) oder Sidekick (klassische Benutzeroberfläche) ausgewählt werden kann.<br /> Der Wert <code>.hidden</code> wird für Komponenten genutzt, die nicht zur Auswahl über die Benutzeroberfläche verfügbar sind, z. B. die tatsächlichen Absatzsysteme.</td>
  </tr>
  <tr>
   <td><code>cq:isContainer</code></td>
   <td><code>Boolean</code></td>
   <td>Gibt an, ob es sich bei der Komponente um eine Containerkomponente handelt, die andere Komponenten wie ein Absatzsystem enthalten kann.</td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><code>cq:dialog</code></td>
   <td><code>nt:unstructured</code><br /> </td>
   <td>Definition des Bearbeitungsdialogfelds für die Touch-optimierte Benutzeroberfläche</td>
  </tr>
  <tr>
   <td><code>dialog</code></td>
   <td><code>cq:Dialog</code></td>
   <td>Definition des Bearbeitungsdialogfelds für die klassische Benutzeroberfläche</td>
  </tr>
  <tr>
   <td><code>cq:design_dialog</code></td>
   <td><code>nt:unstructured</code></td>
   <td>Definition des Design-Dialogfelds für die Touch-optimierte Benutzeroberfläche</td>
  </tr>
  <tr>
   <td><code>design_dialog</code></td>
   <td><code>cq:Dialog </code></td>
   <td>Definition des Design-Dialogfelds für die klassische Benutzeroberfläche<br /> </td>
  </tr>
  <tr>
   <td><code>dialogPath</code></td>
   <td><code>String</code></td>
   <td>Pfad zu einem Dialogfeld, wenn die Komponente keinen Dialogfeldknoten aufweist<br /> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><code>cq:cellName</code></td>
   <td><code>String</code></td>
   <td>Wenn festgelegt, wird diese Eigenschaft als Cell ID verwendet. Weitere Informationen finden Sie im Knowledge Base-Artikel . <a href="https://helpx.adobe.com/de/experience-manager/kb/DesigneCellId.html">Wie werden Design Cell IDs erstellt?</a>.<br /> </td>
  </tr>
  <tr>
   <td><code>cq:childEditConfig</code></td>
   <td><code>cq:EditConfig</code></td>
   <td>Wenn die Komponente ein Container ist, z. B. ein Absatzsystem, wird die Bearbeitungskonfiguration der untergeordneten Knoten gesteuert.<br /> </td>
  </tr>
  <tr>
   <td><code>cq:editConfig</code></td>
   <td><code>cq:EditConfig</code></td>
   <td><a href="#edit-behavior">Bearbeitungskonfiguration der Komponente</a>.<br /> </td>
  </tr>
  <tr>
   <td><code>cq:htmlTag</code></td>
   <td><code>nt:unstructured </code></td>
   <td>Gibt zusätzliche Tag-Attribute zurück, die zum umgebenden HTML-Tag hinzugefügt werden. Ermöglicht das Hinzufügen von Attributen zu den automatisch generierten div-Tags.</td>
  </tr>
  <tr>
   <td><code>cq:noDecoration</code></td>
   <td><code>Boolean</code></td>
   <td>Wenn "true", wird die Komponente nicht mit automatisch generierten div- und css-Klassen gerendert.<br /> </td>
  </tr>
  <tr>
   <td><code>cq:template</code></td>
   <td><code>nt:unstructured</code></td>
   <td>Wenn dieser Knoten gefunden wird, wird er als Inhaltsvorlage verwendet, wenn die Komponente vom Komponenten-Browser oder Sidekick hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><code>cq:templatePath</code></td>
   <td><code>String</code></td>
   <td>Pfad zu einem Knoten, der als Inhaltsvorlage verwendet werden soll, wenn die Komponente vom Komponenten-Browser oder Sidekick hinzugefügt wird. Dies muss ein absoluter Pfad sein, nicht relativ zum Komponentenknoten.<br /> Wenn Sie keine bereits an anderer Stelle verfügbaren Inhalte wiederverwenden möchten, ist dies nicht erforderlich und <code>cq:template</code> ausreichend (siehe unten).</td>
  </tr>
  <tr>
   <td><code>jcr:created</code></td>
   <td><code>Date</code></td>
   <td>Datum der Erstellung der Komponente<br /> </td>
  </tr>
  <tr>
   <td><code>jcr:description</code></td>
   <td><code>String</code></td>
   <td>Beschreibung der Komponente<br /> </td>
  </tr>
  <tr>
   <td><code>jcr:title</code></td>
   <td><code>String</code></td>
   <td>Titel der Komponente<br /> </td>
  </tr>
  <tr>
   <td><code>sling:resourceSuperType</code></td>
   <td><code>String</code></td>
   <td>Wenn dieser Wert festgelegt ist, erbt die Komponente von dieser Komponente.<br /> </td>
  </tr>
  <tr>
   <td><code>virtual</code></td>
   <td><code>sling:Folder</code></td>
   <td>Aktiviert das Erstellen von virtuellen Komponenten. Ein Beispiel finden Sie in der Kontaktkomponente unter:<br /> <code>/libs/foundation/components/profile/form/contact</code></td>
  </tr>
  <tr>
   <td><code>&lt;breadcrumb.jsp&gt;</code></td>
   <td><code>nt:file</code><br /> </td>
   <td>Skriptdatei<br /> </td>
  </tr>
  <tr>
   <td><code>icon.png</code></td>
   <td><code>nt:file</code></td>
   <td>Symbol der Komponente, wird neben dem Titel im Sidekick angezeigt<br /> </td>
  </tr>
  <tr>
   <td><code>thumbnail.png</code></td>
   <td><code>nt:file</code></td>
   <td>Optionale Miniaturansicht, die angezeigt wird, während die Komponente von Sidekick an ihre Position gezogen wird.<br /> </td>
  </tr>
 </tbody>
</table>

Wenn Sie sich die **Text** -Komponente (beide Versionen) sehen Sie die folgenden Elemente:

* HTL ( `/libs/wcm/foundation/components/text`)

  ![chlimage_1-241](assets/chlimage_1-241.png)

* JSP ( `/libs/foundation/components/text`)

  ![screen_shot_2012-02-13at60457pm](assets/screen_shot_2012-02-13at60457pm.png)

Zu den wichtigen Eigenschaften gehören:

* `jcr:title` – Titel der Komponente; dient zur Identifizierung der Komponente, z. B. in der Komponentenliste im Komponenten-Browser oder Sidekick
* `jcr:description` – Beschreibung der Komponente; kann als Mouseover-Hinweis in der Komponentenliste im Sidekick genutzt werden
* `sling:resourceSuperType` – gibt den Pfad der Vererbung bei der Erweiterung einer Komponente an (durch Überschreiben einer Definition)

Zu den wichtigen untergeordneten Knoten gehören:

* `cq:editConfig` ( `cq:EditConfig`) – steuert visuelle Aspekte; definiert z. B. das Aussehen einer Leiste oder eines Widgets oder fügt angepasste Steuerelemente hinzu
* `cq:childEditConfig` ( `cq:EditConfig`) – steuert die visuellen Aspekte für untergeordnete Komponenten, die keine eigenen Definitionen aufweisen
* Touch-optimierte Benutzeroberfläche:
   * `cq:dialog` ( `nt:unstructured`) – definiert das Dialogfeld für die Bearbeitung von Inhalten dieser Komponente
   * `cq:design_dialog` ( `nt:unstructured`) – legt die Design-Bearbeitungsoptionen für diese Komponente fest
* Klassische Benutzeroberfläche:
   * `dialog` ( `cq:Dialog`) – definiert das Dialogfeld zum Bearbeiten von Inhalten dieser Komponente (speziell für die klassische Benutzeroberfläche)
   * `design_dialog` ( `cq:Dialog`) – legt die Design-Bearbeitungsoptionen für diese Komponente fest
   * `icon.png` – Grafikdatei, die als Symbol für die Komponente im Sidekick genutzt werden soll
   * `thumbnail.png` – Grafikdatei, die als Miniaturansicht der Komponente beim Ziehen aus dem Sidekick genutzt werden soll

### Dialogfelder {#dialogs}

Dialogfelder sind ein Schlüsselelement Ihrer Komponente, da sie eine Benutzeroberfläche bieten, über die Autoren diese Komponente konfigurieren und Eingaben bereitstellen können.

Je nach Komplexität der Komponente kann Ihr Dialogfeld eine oder mehrere Registerkarten benötigen, um das Dialogfeld kurz zu halten und die Eingabefelder zu sortieren.

Dialogdefinitionen sind spezifisch für die Benutzeroberfläche:

>[!NOTE]
>
>* Aus Kompatibilitätsgründen kann die Touch-optimierte Benutzeroberfläche die Definition eines Dialogfelds der klassischen Benutzeroberfläche verwenden, wenn für die Touch-optimierte Benutzeroberfläche kein Dialogfeld definiert wurde.
>* Die [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md) unterstützen Sie beim Erweitern/Konvertieren von Komponenten, bei denen nur Dialogfelder für die klassische Benutzeroberfläche festgelegt wurden.
>

* Touch-optimierte Benutzeroberfläche
   * `cq:dialog` ( `nt:unstructured`) Knoten:
      * definieren das Dialogfeld für die Bearbeitung von Inhalten dieser Komponente
      * speziell für die Touch-optimierte Benutzeroberfläche
      * werden mithilfe von Granite-UI-Komponenten definiert
      * weisen die Eigenschaft `sling:resourceType` als standardmäßige Sling-Inhaltsstruktur auf
      * kann über eine Eigenschaft verfügen `helpPath` , um die kontextsensitive Hilferessource (absoluter oder relativer Pfad) zu definieren, auf die beim Zugriff auf das Hilfesymbol (das `?` -Symbol) ausgewählt ist.
         * Bei vordefinierten Komponenten verweist dies häufig auf eine Seite in der Dokumentation.
         * Wenn kein `helpPath` festgelegt ist, wird die Standard-URL (Übersichtsseite der Dokumentation) angezeigt.

  ![chlimage_1-242](assets/chlimage_1-242.png)

  In diesem Dialogfeld werden einzelne Felder definiert:

  ![screen_shot_2012-02-13at60937pm](assets/screen_shot_2012-02-13at60937pm.png)

* Klassische Benutzeroberfläche
   * `dialog` ( `cq:Dialog`) Knoten
      * definieren das Dialogfeld für die Bearbeitung von Inhalten dieser Komponente
      * speziell für die klassische Benutzeroberfläche
      * werden mit ExtJS-Widgets definiert
      * weisen die Eigenschaft `xtype` auf, die auf ExtJS verweist
      * kann über eine Eigenschaft verfügen `helpPath` zur Definition der kontextsensitiven Hilferessource (absoluter oder relativer Pfad), auf die beim Zugriff auf die Variable **Hilfe** Schaltfläche ausgewählt ist.
         * Bei vordefinierten Komponenten verweist dies häufig auf eine Seite in der Dokumentation.
         * Wenn kein `helpPath` festgelegt ist, wird die Standard-URL (Übersichtsseite der Dokumentation) angezeigt.

  ![chlimage_1-243](assets/chlimage_1-243.png)

  In diesem Dialogfeld werden einzelne Felder definiert:

  ![chlimage_1-244](assets/chlimage_1-244.png)

  Innerhalb eines klassischen Dialogfelds:

   * können Sie Dialogfeld wie `cq:Dialog` erstellen, die eine einzige Registerkarte aufweisen, wie in der Text-Komponente. Wenn Sie mehrere Registerkarten benötigen, wie in der Textbild-Komponente, können Sie das Dialogfeld als `cq:TabPanel` definieren.
   * wird eine `cq:WidgetCollection` ( `items`) genutzt, um eine Basis für Eingabefelder (`cq:Widget`) oder weitere Registerkarten (`cq:Widget`) bereitzustellen. Diese Hierarchie kann erweitert werden.

### Design-Dialogfelder {#design-dialogs}

Designdialogfelder ähneln den Dialogfeldern, die zum Bearbeiten und Konfigurieren von Inhalten verwendet werden. Sie stellen jedoch die Oberfläche bereit, über die Autoren Designdetails für diese Komponente konfigurieren und bereitstellen können.

[Designdialogfelder sind im Designmodus verfügbar](/help/sites-authoring/default-components-designmode.md), obwohl sie z. B. nicht für alle Komponenten benötigt werden **Titel** und **Bild** beide über Designdialogfelder verfügen, während **Text** nicht.

Das Dialogfeld &quot;Design&quot;für das Absatzsystem (z. B. parsys) ist ein Sonderfall, da es dem Benutzer ermöglicht, bestimmte andere Komponenten zur Auswahl (aus dem Komponenten-Browser oder Sidekick) auf der Seite verfügbar zu machen.

### Hinzufügen Ihrer Komponente zum Absatzsystem {#adding-your-component-to-the-paragraph-system}

Nachdem eine Komponente definiert wurde, muss sie zur Verwendung verfügbar gemacht werden. Um eine Komponente für die Verwendung in einem Absatzsystem verfügbar zu machen, können Sie entweder:

1. Öffnen Sie den [Design-Modus](/help/sites-authoring/default-components-designmode.md) für eine Seite und aktivieren Sie die benötigte Komponente.
1. Fügen Sie die erforderlichen Komponenten zum `components` -Eigenschaft Ihrer Vorlagendefinition unter:

   `/etc/designs/<*yourProject*>/jcr:content/<*yourTemplate*>/par`

   Ein Beispiel finden Sie unter:

   `/etc/designs/geometrixx/jcr:content/contentpage/par`

   ![chlimage_1-245](assets/chlimage_1-245.png)

### Komponenten und die von ihnen erstellten Inhalte {#components-and-the-content-they-create}

Wenn Sie eine Instanz der **Titel** -Komponente auf der Seite: `<content-path>/Prototype.html`

* Touch-optimierte Benutzeroberfläche

  ![chlimage_1-246](assets/chlimage_1-246.png)

* Klassische Benutzeroberfläche

  ![screen_shot_2012-02-01at34257pm](assets/screen_shot_2012-02-01at34257pm.png)

Anschließend können Sie die Struktur des Inhalts sehen, der im Repository erstellt wurde:

![screen_shot_2012-02-13at61405pm](assets/screen_shot_2012-02-13at61405pm.png)

Sehen Sie sich besonders den tatsächlichen Text für eine **Titel**-Komponente an:

* Die Definition (für beide Benutzeroberflächen) verfügt über die Eigenschaft `name`= `./jcr:title`

   * `/libs/foundation/components/title/cq:dialog/content/items/column/items/title`
   * `/libs/foundation/components/title/dialog/items/title`

* Innerhalb des Inhalts wird dadurch die Eigenschaft `jcr:title` erstellt, die den Inhalt des Autors enthält.

Die definierten Eigenschaften hängen von den jeweiligen Definitionen ab. Sie können zwar komplexer sein als oben, folgen aber dennoch den gleichen Grundprinzipien.

## Komponentenhierarchie und Vererbung {#component-hierarchy-and-inheritance}

Komponenten in AEM unterliegen drei verschiedenen Hierarchien:

* **Ressourcentyphierarchie**

  Diese wird verwendet, um Komponenten mit der `sling:resourceSuperType`-Eigenschaft zu erweitern. Dies aktiviert die Vererbung für die Komponente. Beispielsweise erbt eine Textkomponente verschiedene Attribute von der Standardkomponente.

   * Skripte (von Sling aufgelöst)
   * Dialogfelder
   * Beschreibungen (einschließlich Miniaturansichten und Symbolen)

* **Container-Hierarchie**

  Hiermit werden Konfigurationseinstellungen an untergeordnete Komponenten weitergegeben. Gängig ist dies vor allem bei parsys-Szenarien.

  So können Sie beispielsweise Konfigurationseinstellungen für die Schaltflächen auf der Bearbeitungsleiste, das Layout von Steuerungen (Bearbeitungsleiste, Rollover) oder von Dialogfeldern (eingebunden, unverankert) auf der übergeordneten Komponente definieren und an die untergeordneten Komponenten übergeben.

  Konfigurationseinstellungen (für die Bearbeitungsfunktion) in `cq:editConfig` und `cq:childEditConfig` werden weitergegeben.

* **Einschlusshierarchie**

  Diese Hierarchie wird zur Laufzeit durch eine Folge an Einschlüssen eingeführt.

  Diese Hierarchie wird vom Designer verwendet, der als Basis für die verschiedenen Designaspekte des Rendering fungiert; einschließlich Layout-Angaben, CSS-Informationen, verfügbaren Komponenten in einem parsys usw.

## Bearbeitungsverhalten {#edit-behavior}

In diesem Abschnitt wird beschrieben, wie Sie das Bearbeitungsverhalten einer Komponente konfigurieren. Dazu gehören Attribute wie für die Komponente verfügbare Aktionen, Eigenschaften des Editors für die Bearbeitung im Kontext und Listener, die sich auf Ereignisse in der Komponente beziehen.

Die Konfiguration gilt dabei sowohl für die Touch-optimierte als auch für die klassische Benutzeroberfläche, wenn auch mit gewissen Unterschieden.

Um das Bearbeitungsverhalten einer Komponente zu konfigurieren, fügen Sie einen `cq:editConfig`-Knoten des Typs `cq:EditConfig` unter dem Komponentenknoten (des Typs `cq:Component`) hinzu sowie spezifische Eigenschaften und untergeordnete Knoten. Die folgenden Funktionen und untergeordneten Knoten sind verfügbar:

* [`cq:editConfig` Knoteneigenschaften](#configuring-with-cq-editconfig-properties):

   * `cq:actions` ( `String array`): legt die Aktionen fest, die für die Komponente durchgeführt werden
   * `cq:layout` ( `String`): definiert, wie die Komponente in der klassischen Benutzeroberfläche bearbeitet wird.
   * `cq:dialogMode` ( `String`): definiert, wie das Komponentendialogfeld in der klassischen Benutzeroberfläche geöffnet wird

      * In der Touch-optimierten Benutzeroberfläche sind die Dialogfelder im Desktop-Modus immer unverankert und werden im mobilen Modus immer im Vollbild geöffnet.

   * `cq:emptyText` ( `String`): definiert den Text, der angezeigt wird, wenn keine visuellen Inhalte vorhanden sind
   * `cq:inherit` ( `Boolean`): legt fest, ob fehlende Werte von der Komponente geerbt werden, von der die Vererbung erfolgt
   * `dialogLayout` (String): legt fest, wie das Dialogfeld geöffnet werden soll

* Untergeordnete [`cq:editConfig`-Knoten](#configuring-with-cq-editconfig-child-nodes):

   * `cq:dropTargets` (Knotentyp `nt:unstructured`): definiert eine Liste von Ablagezielen, die eine Ablage von einem Asset aus dem Content Finder annehmen können.

      * Mehrere Ablageziele sind nur in der klassischen Benutzeroberfläche verfügbar.
      * In der Touch-optimierten Benutzeroberfläche ist ein einzelnes Ablageziel zulässig.

   * `cq:actionConfigs` (Knotentyp `nt:unstructured`): definiert eine Liste mit neuen Aktionen, die an die cq:actions-Liste angehängt wird
   * `cq:formParameters` (Knotentyp `nt:unstructured`): definiert zusätzliche Parameter, die zum Dialogfeldformular hinzugefügt werden
   * `cq:inplaceEditing` (Knotentyp `cq:InplaceEditingConfig`): definiert eine Kontextbearbeitungsfunktion für die Komponente
   * `cq:listeners` (Knotentyp `cq:EditListenersConfig`): Legt fest, was geschieht, bevor oder nachdem eine Aktion auf der Komponente stattfindet.

>[!NOTE]
>
>Auf dieser Seite wird ein Knoten (Eigenschaften und untergeordnete Knoten) als XML dargestellt, wie im folgenden Beispiel gezeigt.

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:dialogMode="floating"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afteredit="REFRESH_PAGE"/>
</jcr:root>
```

Es gibt viele vorhandene Konfigurationen im Repository. Sie können einfach nach bestimmten Eigenschaften oder untergeordneten Knoten suchen:

* So suchen Sie nach einer Eigenschaft des `cq:editConfig` Knoten, z. B. `cq:actions`, können Sie das Abfragetool in **CRXDE Lite** und suchen Sie mit der folgenden XPath-Abfragezeichenfolge:

  `//element(cq:editConfig, cq:EditConfig)[@cq:actions]`

* So suchen Sie nach einem untergeordneten Knoten von `cq:editConfig`, können Sie beispielsweise nach `cq:dropTargets`, der vom Typ `cq:DropTargetConfig`; Sie können das Abfragetool in &quot;CRXDE Lite&quot;verwenden und mit der folgenden XPath-Abfragezeichenfolge suchen:

  `//element(cq:dropTargets, cq:DropTargetConfig)`

### Komponenten-Platzhalter {#component-placeholders}

Komponenten müssen immer HTML-Inhalte wiedergeben, die für den Autor sichtbar sind, auch wenn die Komponente keinen Inhalt hat. Andernfalls kann es visuell aus der Benutzeroberfläche des Editors verschwinden, sodass es technisch vorhanden, aber auf der Seite und im Editor nicht sichtbar ist. In einem solchen Fall können die Autoren die leere Komponente nicht auswählen und damit interagieren.

Aus diesem Grund sollten Komponenten einen Platzhalter darstellen, solange sie beim Rendern der Seite im Seiteneditor (wenn der WCM-Modus `edit` oder `preview` ist) keine sichtbare Ausgabe erzeugen.
Das typische HTML-Markup für einen Platzhalter sieht wie folgt aus:

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

Das typische HTL-Skript, das den obigen Platzhalter-HTML-Code rendert, lautet wie folgt:

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

Im vorherigen Beispiel ist `isEmpty` eine Variable, die nur dann wahr ist, wenn die Komponente keinen Inhalt hat und für den Autor unsichtbar ist.

Um Wiederholungen zu vermeiden, empfiehlt Adobe den Implementierern von Komponenten, eine HTL-Vorlage für diese Platzhalter zu verwenden, [wie sie von den Kernkomponenten bereitgestellt wird.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

Die Verwendung der Vorlage im vorherigen Link erfolgt dann mit der folgenden HTL-Zeile:

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

Im vorherigen Beispiel ist `model.text` die Variable, die nur dann wahr ist, wenn die Komponente einen Inhalt hat und sichtbar ist.

Eine beispielhafte Verwendung dieser Vorlage ist in den Kernkomponenten zu sehen, [wie z. B. in der Titelkomponente.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### Konfigurieren mit cq:EditConfig-Eigenschaften {#configuring-with-cq-editconfig-properties}

### cq:actions {#cq-actions}

Die Eigenschaft `cq:actions` (`String array`) definiert eine Aktion oder mehrere Aktionen, die auf der Komponente ausgeführt werden kann/können. Folgende Werte stehen für die Konfiguration zur Verfügung:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftswert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><code>text:&lt;some text&gt;</code></td>
   <td>Zeigt den statischen Textwert &lt;some text&gt;<br /> an. Nur in der klassischen Benutzeroberfläche sichtbar. Die Touch-optimierte Benutzeroberfläche zeigt keine Aktionen in einem Kontextmenü an; daher trifft dieser Eigenschaftswert für sie nicht zu.</td>
  </tr>
  <tr>
   <td>-</td>
   <td>Fügt ein Leerzeichen hinzu.<br /> Nur in der klassischen Benutzeroberfläche sichtbar. Die Touch-optimierte Benutzeroberfläche zeigt keine Aktionen in einem Kontextmenü an; daher trifft dieser Eigenschaftswert für sie nicht zu.</td>
  </tr>
  <tr>
   <td><code>edit</code></td>
   <td>Fügt eine Schaltfläche zum Bearbeiten der Komponente hinzu.</td>
  </tr>
      <tr>
    <td><code>editannotate</code></td>
    <td>Fügt eine Schaltfläche hinzu, um die Komponente zu bearbeiten und <a href="/help/sites-authoring/annotations.md">Anmerkungen</a>.</td>
   </tr>
  <tr>
   <td><code>delete</code></td>
   <td>Fügt eine Schaltfläche zum Löschen der Komponente hinzu.</td>
  </tr>
  <tr>
   <td><code>insert</code></td>
   <td>Fügt eine Schaltfläche hinzu, um eine neue Komponente vor der aktuellen einzufügen.</td>
  </tr>
  <tr>
   <td><code>copymove</code></td>
   <td>Fügt eine Schaltfläche zum Kopieren und Ausschneiden der Komponente hinzu.</td>
  </tr>
 </tbody>
</table>

Mit der folgenden Konfiguration werden der Bearbeitungsleiste der Komponente eine Bearbeitungsschaltfläche, ein Abstand, eine Lösch- und eine Einfüge-Schaltfläche hinzugefügt:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit,-,delete,insert]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig"/>
```

Die folgende Konfiguration fügt den Text „Vom Basis-Framework geerbte Konfigurationen“ zur Bearbeitungsleiste der Komponente hinzu:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[text:Inherited Configurations from Base Framework]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig"/>
```

### cq:layout (nur klassische Benutzeroberfläche) {#cq-layout-classic-ui-only}

Die Eigenschaft `cq:layout` (`String`) legt fest, die wie Komponente in der klassischen Benutzeroberfläche bearbeitet werden kann. Die folgenden Werte sind verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftswert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><code>rollover</code></td>
   <td>Standardwert. Die Komponentenbearbeitung ist beim Darüberfahren mit der Maus durch Anklicken und/oder über das Kontextmenü zugänglich.<br /> Für eine erweiterte Verwendung lautet das entsprechende clientseitige Objekt: <code>CQ.wcm.EditRollover</code>.</td>
  </tr>
  <tr>
   <td><code>editbar</code></td>
   <td>Auf die Komponentenbearbeitung kann über eine Symbolleiste zugegriffen werden.<br /> Für eine erweiterte Verwendung lautet das entsprechende clientseitige Objekt: <code>CQ.wcm.EditBar</code>.</td>
  </tr>
  <tr>
   <td><code>auto</code></td>
   <td>Die Auswahl bleibt dem clientseitigen Code überlassen.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Konzepte von rollover und editbar können in der Touch-optimierten Benutzeroberfläche nicht angewendet werden.

Die folgenden Konfigurationen fügen eine Bearbeitungsschaltfläche zur Bearbeitungsleiste der Komponente hinzu:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
</jcr:root>
```

### cq:dialogMode (nur klassische Benutzeroberfläche) {#cq-dialogmode-classic-ui-only}

Die Komponente kann mit einem Dialogfeld &quot;Bearbeiten&quot;verknüpft werden. Die `cq:dialogMode` Eigenschaft ( `String`) definiert, wie das Komponentendialogfeld in der klassischen Benutzeroberfläche geöffnet wird. Die folgenden Werte sind verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftswert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><code>floating</code></td>
   <td>Das Dialogfeld ist unverankert.<br /> </td>
  </tr>
  <tr>
   <td><code>inline</code></td>
   <td>(Standardwert). Das Dialogfeld wird über der Komponente verankert.<br /> </td>
  </tr>
  <tr>
   <td><code>auto</code></td>
   <td>Wenn die Komponentenbreite kleiner ist als die clientseitige <code>CQ.themes.wcm.EditBase.INLINE_MINIMUM_WIDTH</code> -Wert, ist das Dialogfeld schwebend, andernfalls ist es inline.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>In der Touch-optimierten Benutzeroberfläche sind die Dialogfelder im Desktopmodus immer unverankert und werden im mobilen Modus immer im Vollbild geöffnet.

Die folgende Konfiguration definiert eine Bearbeitungsleiste mit einer Bearbeitungsschaltfläche und einem unverankerten Dialogfeld:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:dialogMode="floating"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
</jcr:root>
```

### cq:emptyText {#cq-emptytext}

Die Eigenschaft `cq:emptyText` (`String`) definiert den Text, der angezeigt wird, wenn keine visuellen Inhalte vorhanden sind. Standardwert ist: `Drag components or assets here`.

### cq:inherit {#cq-inherit}

Die Eigenschaft `cq:inherit` (`boolean`) legt fest, ob fehlende Werte von der Komponente geerbt werden, von der die Vererbung erfolgt. Standardwert ist `false`.

### dialogLayout {#dialoglayout}

Die Eigenschaft `dialogLayout` legt fest, wie ein Dialogfeld standardmäßig geöffnet werden soll.

* Beim Wert `fullscreen` wird das Dialogfeld im Vollbildschirmmodus geöffnet.
* Bei einem leeren Wert oder einer fehlenden Eigenschaft wird das Dialogfeld standardmäßig normal geöffnet.
* Der Benutzer kann den Vollbildmodus im Dialogfeld immer umschalten.
* Gilt nicht für die klassische Benutzeroberfläche.

### Konfigurieren mit untergeordneten cq:EditConfig-Knoten {#configuring-with-cq-editconfig-child-nodes}

### cq:dropTargets {#cq-droptargets}

Der Knoten `cq:dropTargets` (Knotentyp `nt:unstructured`) definiert eine Liste von Ablagezielen, die eine Ablage von einem Asset aus der Inhaltssuche annehmen können. Er dient als Sammlung von Knoten des Typs `cq:DropTargetConfig`.

>[!NOTE]
>
>Mehrere Ablageziele sind nur in der klassischen Benutzeroberfläche verfügbar.
>
>In der Touch-optimierten Benutzeroberfläche wird nur das erste Ziel verwendet.

Jeder untergeordnete Knoten des Typs `cq:DropTargetConfig` definiert ein Ablageziel in der Komponente. Der Knotenname ist wichtig, da er im JSP wie folgt verwendet werden muss, um den CSS-Klassennamen zu erzeugen, der dem DOM-Element zugewiesen wird, das das effektive Ablageziel ist:

```
<drop target css class> = <drag and drop prefix> +
 <node name of the drop target in the edit configuration>
```

Die `<drag and drop prefix>` wird durch die Java™-Eigenschaft definiert:

`com.day.cq.wcm.api.components.DropTarget.CSS_CLASS_PREFIX`.

Beispielsweise wird der Klassenname wie folgt im JSP der Download-Komponente (`/libs/foundation/components/download/download.jsp`) definiert. Dabei ist `file` der Knotenname des Ablageziels in der Bearbeitungskonfiguration der Download-Komponente:

`String ddClassName = DropTarget.CSS_CLASS_PREFIX + "file";`

Der Knoten des Typs `cq:DropTargetConfig` muss die folgenden Eigenschaften aufweisen:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Eigenschaftswert<br /> </strong></td>
  </tr>
  <tr>
   <td><code>accept</code></td>
   <td>Auf den Asset-MIME-Typ angewendeter regulärer Ausdruck, der überprüft, ob das Ablegen zulässig ist.</td>
  </tr>
  <tr>
   <td><code>groups</code></td>
   <td>Array von Ablagezielgruppen. Jede Gruppe muss mit dem Gruppentyp übereinstimmen, der in der Content Finder-Erweiterung definiert wurde und der bei den Assets angehängt ist.</td>
  </tr>
  <tr>
   <td><code>propertyName</code></td>
   <td>Name der Eigenschaft, die nach einer gültigen Ablage aktualisiert wird.</td>
  </tr>
 </tbody>
</table>

Die folgende Konfiguration entstammt der Download-Komponente. Sie ermöglicht es, dass jedes Asset (der MIME-Typ kann jeder beliebige String sein) aus der Gruppe `media` vom Content Finder in der Komponente abgelegt werden kann. Nach der Ablage wird die Komponenteneigenschaft `fileReference` aktualisiert:

```
    <cq:dropTargets jcr:primaryType="nt:unstructured">
        <file
            jcr:primaryType="cq:DropTargetConfig"
            accept="[.*]"
            groups="[media]"
            propertyName="./fileReference"/>
    </cq:dropTargets>
```

### cq:actionConfigs (nur klassische Benutzeroberfläche) {#cq-actionconfigs-classic-ui-only}

Der Knoten `cq:actionConfigs` (Knotentyp `nt:unstructured`) definiert eine Liste mit neuen Aktionen, die an die Liste angehängt werden, die von der Eigenschaft `cq:actions` festgelegt wird. Jeder untergeordnete Knoten von `cq:actionConfigs`definiert eine Aktion, indem er ein Widget definiert.

Die folgende Beispielkonfiguration definiert eine neue Schaltfläche (mit einem Trennzeichen für die klassische Benutzeroberfläche):

* ein Trennzeichen, definiert durch den xtype `tbseparator`;

   * Dies wird nur von der klassischen Benutzeroberfläche verwendet.
   * Diese Definition wird von der Touch-optimierten Benutzeroberfläche ignoriert, weil xtypes ignoriert werden (und Trennzeichen unnötig sind, da die Aktionssymbolleiste in der Touch-optimierten Benutzeroberfläche anders aufgebaut ist).

* eine Schaltfläche **Manage comments** (Kommentare verwalten), die die Handler-Funktion `CQ_collab_forum_openCollabAdmin()` ausführt.

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    cq:actions="[EDIT,COPYMOVE,DELETE,INSERT]"
    jcr:primaryType="cq:EditConfig">
    <cq:actionConfigs jcr:primaryType="nt:unstructured">
        <separator0
            jcr:primaryType="nt:unstructured"
            xtype="tbseparator"/>
        <manage
            jcr:primaryType="nt:unstructured"
            handler="function(){CQ_collab_forum_openCollabAdmin();}"
            text="Manage comments"/>
    </cq:actionConfigs>
</jcr:root>
```

>[!NOTE]
>
>Ein Beispiel für die Touch-optimierte Benutzeroberfläche finden Sie unter [Hinzufügen neuer Aktionen zu Komponenten-Symbolleisten](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar).

### cq:formParameters {#cq-formparameters}

Der Knoten `cq:formParameters` (Knotentyp `nt:unstructured`) definiert zusätzliche Parameter, die zum Dialogfeldformular hinzugefügt werden. Jede Eigenschaft wird einem Formularparameter zugeordnet.

Die folgende Konfiguration fügt einen Parameter namens `name` mit dem Wert `photos/primary` zum Dialogfeldformular hinzu:

```
    <cq:formParameters
        jcr:primaryType="nt:unstructured"
        name="photos/primary"/>
```

### cq:inplaceEditing {#cq-inplaceediting}

Der Knoten `cq:inplaceEditing` (Knotentyp `cq:InplaceEditingConfig`) definiert eine Inplace-Bearbeitungsfunktion für die Komponente. Er kann die folgenden Eigenschaften aufweisen:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Eigenschaftswert<br /> </strong></td>
  </tr>
  <tr>
   <td><code>active</code></td>
   <td>(<code>boolean</code>) True, um die Inplace-Bearbeitung zu aktivieren.</td>
  </tr>
  <tr>
   <td><code>configPath</code></td>
   <td>(<code>String</code>) Pfad der Editor-Konfiguration. Die Konfiguration kann durch einen Konfigurationsknoten festgelegt werden.</td>
  </tr>
  <tr>
   <td><code>editorType</code></td>
   <td><p>(<code>String</code>) Editor-Typ. Die verfügbaren Typen sind:</p>
    <ul>
     <li>plaintext: zur Verwendung für Nicht-HTML-Inhalt.<br /> </li>
     <li>title: ein erweiterter Texteditor, der grafische Titel in Klartext umwandelt, bevor die Bearbeitung beginnt; wird von der Geometrixx-Titel-Komponente genutzt<br /> </li>
     <li>text: wird für HTML-Inhalte genutzt (verwendet den Rich-Text-Editor).<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Die folgende Konfiguration aktiviert die Kontextbearbeitung der Komponente und legt `plaintext` als Editor-Typ fest:

```
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### cq:listeners {#cq-listeners}

Der Knoten `cq:listeners` (Knotentyp `cq:EditListenersConfig`) legt fest, was geschieht, bevor oder nachdem eine Aktion auf der Komponente stattfindet. In der folgenden Tabelle sind die möglichen Eigenschaften aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Eigenschaftswert<br /> </strong></td>
   <td><p><strong>Standardwert</strong></p> <p>(Nur klassische Benutzeroberfläche)</p> </td>
  </tr>
  <tr>
   <td><code>beforedelete</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente entfernt wird.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><code>beforeedit</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente bearbeitet wird.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>beforecopy</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente kopiert wird.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>beforemove</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente verschoben wird.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>beforeinsert</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente eingefügt wird.<br /> Funktioniert nur bei der Touch-optimierten Benutzeroberfläche.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>beforechildinsert</code></td>
   <td>Der Handler wird ausgelöst, bevor die Komponente in eine andere Komponente eingefügt wird (nur Container).</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>afterdelete</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente entfernt wurde.</td>
   <td><code>REFRESH_SELF</code></td>
  </tr>
  <tr>
   <td><code>afteredit</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente bearbeitet wurde.</td>
   <td><code>REFRESH_SELF</code></td>
  </tr>
  <tr>
   <td><code>aftercopy</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente kopiert wurde.</td>
   <td><code>REFRESH_SELF</code></td>
  </tr>
  <tr>
   <td><code>afterinsert</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente eingefügt wurde.</td>
   <td><code>REFRESH_INSERTED</code></td>
  </tr>
  <tr>
   <td><code>aftermove</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente verschoben wurde.</td>
   <td><code>REFRESH_SELFMOVED</code></td>
  </tr>
  <tr>
   <td><code>afterchildinsert</code></td>
   <td>Der Handler wird ausgelöst, nachdem die Komponente in eine andere Komponente eingefügt wurde (nur Container).</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Handler `REFRESH_INSERTED` und `REFRESH_SELFMOVED` stehen nur in der klassischen Benutzeroberfläche zur Verfügung.

>[!NOTE]
>
>Standardwerte für die Listener werden nur in der klassischen Benutzeroberfläche festgelegt.

>[!NOTE]
>
>Wenn verschachtelte Komponenten vorhanden sind, gibt es bestimmte Einschränkungen für Aktionen, die als Eigenschaften für die `cq:listeners` node:
>
>* Bei geschachtelten Komponenten *müssen* die Werte der folgenden Eigenschaften `REFRESH_PAGE` sein: >
>  * `aftermove`
>  * `aftercopy`

Der Ereignis-Handler kann mit einer angepassten Implementierung implementiert werden. Beispiel: wobei `project.customerAction` ist eine statische Methode:

`afteredit = "project.customerAction"`

Das folgende Beispiel entspricht der `REFRESH_INSERTED`-Konfiguration:

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

>[!NOTE]
>
>Informationen dazu, welche Parameter in den Handlern verwendet werden können, finden Sie in der klassischen Benutzeroberfläche unter `before<action>` und `after<action>` Ereignisabschnitt des [`CQ.wcm.EditBar`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditBar) und [`CQ.wcm.EditRollover`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditRollover) Widget-Dokumentation.

Mit der folgenden Konfiguration wird die Seite aktualisiert, nachdem die Komponente gelöscht, bearbeitet, eingefügt oder verschoben wurde:

```
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```
