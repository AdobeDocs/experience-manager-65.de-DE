---
title: Seitenvorlagen – statisch
description: Eine Vorlage wird verwendet, um eine Seite zu erstellen. Sie definiert, welche Komponenten im ausgewählten Umfang genutzt werden können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: b934ac41-78b9-497f-ba95-b05ef1e5660e
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1601'
ht-degree: 100%

---

# Seitenvorlagen – statisch{#page-templates-static}

Eine Vorlage wird verwendet, um eine Seite zu erstellen. Sie definiert, welche Komponenten im ausgewählten Umfang genutzt werden können. Eine Vorlage ist eine Hierarchie von Knoten, die dieselbe Struktur aufweist wie die zu erstellende Seite, aber keine Inhalte.

Jede Vorlage stellt Ihnen eine Auswahl an Komponenten bereit, die Sie verwenden können.

* Vorlagen bestehen aus [Komponenten](/help/sites-developing/components.md);
* Komponenten nutzen Widgets und bieten Zugriff auf Widgets. Mit Widgets werden die Inhalte gerendert.

>[!NOTE]
>
>[Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) sind ebenfalls verfügbar und sind der empfohlene Typ von Vorlagen für die größte Flexibilität und die neuesten Funktionen.

## Eigenschaften und untergeordnete Knoten einer Vorlage {#properties-and-child-nodes-of-a-template}

Eine Komponente ist ein Knoten vom Typ „cq:Template“ mit den folgenden Eigenschaften und untergeordneten Knoten:

<table>
 <tbody>
  <tr>
   <td><strong>Name <br /> </strong></td>
   <td><strong>Typ <br /> </strong></td>
   <td><strong>Beschreibung <br /> </strong></td>
  </tr>
  <tr>
   <td>. <br /> </td>
   <td> cq:Template</td>
   <td>Aktuelle Vorlage. Eine Vorlage weist den Knotentyp cq:Template auf<br /> </td>
  </tr>
  <tr>
   <td> allowedChildren </td>
   <td> Zeichenfolge[]</td>
   <td>Pfad einer Vorlage, die ein untergeordnetes Element dieser Vorlage sein kann.<br /> </td>
  </tr>
  <tr>
   <td> allowedParents</td>
   <td> Zeichenfolge[]</td>
   <td>Pfad einer Vorlage, die ein übergeordnetes Element dieser Vorlage sein kann.<br /> </td>
  </tr>
  <tr>
   <td> allowedPaths</td>
   <td> Zeichenfolge[]</td>
   <td>Pfad einer Seite, die auf dieser Vorlage basieren darf.<br /> </td>
  </tr>
  <tr>
   <td> jcr:created</td>
   <td> Datum</td>
   <td>Datum der Erstellung der Vorlage.<br /> </td>
  </tr>
  <tr>
   <td> jcr:description</td>
   <td> Zeichenfolge</td>
   <td>Beschreibung der Vorlage.<br /> </td>
  </tr>
  <tr>
   <td> jcr:title</td>
   <td> Zeichenfolge</td>
   <td>Titel der Vorlage.<br /> </td>
  </tr>
  <tr>
   <td> Rangfolge</td>
   <td> Long</td>
   <td>Rang der Vorlage. Wird verwendet, um die Vorlage in der Benutzeroberfläche anzuzeigen<br /> </td>
  </tr>
  <tr>
   <td> jcr:content</td>
   <td> cq:PageContent</td>
   <td>Knoten, der den Inhalt der Vorlage enthält.<br /> </td>
  </tr>
  <tr>
   <td> thumbnail.png</td>
   <td> nt:file</td>
   <td>Miniaturansicht der Vorlage.<br /> </td>
  </tr>
  <tr>
   <td> icon.png</td>
   <td> nt:file</td>
   <td>Symbol der Vorlage.<br /> </td>
  </tr>
 </tbody>
</table>

Eine Vorlage ist die Basis einer Seite.

Um eine Seite zu erstellen, müssen Sie die Vorlage (Knotenbaumstruktur `/apps/<myapp>/template/<mytemplate>`) an die entsprechende Stelle in der Website-Baumstruktur kopieren: Dies geschieht, wenn eine Seite über die Registerkarte **Websites** erstellt wird.

Über diesen Kopiervorgang erhält die Seite auch ihren anfänglichen Inhalt (in der Regel nur den Inhalt der obersten Ebene) und die Eigenschaft „sling:resourceType“, den Pfad zur Seitenkomponente, die zum Rendern der Seite verwendet wird (alles im untergeordneten Knoten „jcr:content“).

## Strukturieren von Vorlagen {#how-templates-are-structured}

Zwei Aspekte müssen berücksichtigt werden:

* die Struktur der Vorlage selbst
* die Struktur des Inhalts, der bei Verwendung einer Vorlage erstellt wird

### Die Struktur einer Vorlage {#the-structure-of-a-template}

Eine Vorlage wird unter einem Knoten vom Typ **cq:Template** erstellt.

![screen_shot_2012-02-13at63646pm](assets/screen_shot_2012-02-13at63646pm.png)

Verschiedene Eigenschaften können festgelegt werden, insbesondere:

* **jcr:title** – Titel für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt.
* **jcr:description** – Beschreibung für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt.

Dieser Knoten enthält einen Knoten „jcr:content“ (cq:PageContent), der als Basis für den Inhaltsknoten der erzeugten Seiten genutzt wird. Dabei wird mit sling:resourceType auf die Komponenten verwiesen, die für das Rendern des tatsächlichen Inhalts einer neuen Seite verwendet werden sollen.

![screen_shot_2012-02-13at64010pm](assets/screen_shot_2012-02-13at64010pm.png)

Mit dieser Komponente wird die Struktur und das Design des Inhalts definiert, wenn eine neue Seite erstellt wird.

![screen_shot_2012-02-13at64137pm](assets/screen_shot_2012-02-13at64137pm.png)

### Der von einer Vorlage erstellte Inhalt {#the-content-produced-by-a-template}

Mit Vorlagen werden Seiten des Typs `cq:Page` erstellt (wie bereits erwähnt, ist eine Seite eine besondere Art der Komponente). Jede AEM-Seite weist den strukturierten Knoten `jcr:content` auf. Dies:

* ist vom Typ „cq:PageContent“
* ist ein strukturierter Knotentyp, der eine festgelegte Inhaltsdefinition enthält
* weist die Eigenschaft `sling:resourceType` auf, die auf die Komponente verweist, welche die Sling-Skripte zum Rendern des Inhalts enthält

### Standardvorlagen {#default-templates}

AEM bietet verschiedene Standardvorlagen, die standardmäßig verfügbar sind. Mitunter können Sie die Vorlagen unverändert nutzen. In diesem Fall müssen Sie sicherstellen, dass die Vorlage für Ihre Website verfügbar ist.

AEM enthält beispielsweise verschiedene Vorlagen, darunter eine Inhaltsseite und eine Homepage.

| **Titel** | **Komponente** | **Speicherort** | **Zweck** |
|---|---|---|---|
| Startseite | homepage | geometrixx | Die Vorlage für die Geometrixx-Homepage. |
| Inhaltsseite | contentpage | geometrixx | Die Vorlage für die Geometrixx-Inhaltsseite. |

#### Anzeigen von Standardvorlagen {#displaying-default-templates}

Eine Liste aller Vorlagen im Repository können Sie wie folgt anzeigen:

1. Öffnen Sie in CRXDE Lite das Menü **Tools** und klicken Sie auf **Abfrage**.

1. Auf der Registerkarte „Abfrage“:
1. Wählen Sie als **Typ** die Option **XPath** aus.

1. Geben Sie in das Eingabefeld **Abfrage** diese Zeichenfolge ein: //element(&#42;, cq:Template)

1. Klicken Sie auf **Ausführen**. Die Liste wird im Ergebnisfeld angezeigt.

Normalerweise können Sie eine vorhandene Vorlage verwenden und auf dieser Basis eine neue Vorlage zur eigenen Verwendung entwickeln. Weitere Informationen finden Sie unter [Entwickeln von Seitenvorlagen](#developing-page-templates).

Damit eine vorhandene Vorlage für Ihre Website aktiviert und im Dialogfeld **Seite erstellen** angezeigt wird, wenn Sie eine Seite direkt unter **Websites** in der **Websites**-Konsole erstellen, legen Sie für die Eigenschaft „allowedPaths“ des Vorlagenknotens folgenden Wert fest: **/content(/.&#42;)?**

## Anwenden von Vorlagendesigns {#how-template-designs-are-applied}

Wenn Stile in der Benutzeroberfläche im [Designmodus](/help/sites-authoring/default-components-designmode.md) definiert werden, wird das Design am genauen Pfad des Inhaltsknotens, für den der Stil definiert wird, beibehalten.

>[!CAUTION]
>
>Adobe empfiehlt nur die Anwendung von Designs durch den [Designmodus](/help/sites-authoring/default-components-designmode.md).
>
>Das Ändern von Designs in CRXDE Lite ist beispielsweise nicht ratsam, und die Anwendung derartiger Designs kann von erwarteten Verhaltensweisen abweichen.

Wenn Entwürfe nur im Designmodus angewendet werden, sind die folgenden Abschnitte, [Auflösung des Designpfads](/help/sites-developing/page-templates-static.md#design-path-resolution), [Entscheidungsbaum](/help/sites-developing/page-templates-static.md#decision-tree) und das [Beispiel](/help/sites-developing/page-templates-static.md#example), nicht anwendbar.

### Auflösung des Designpfads {#design-path-resolution}

Beim Rendern von Inhalten, die auf einer statischen Vorlage basieren, versucht AEM, das relevanteste Design und die relevantesten Stile auf den Inhalt anzuwenden. Hierzu erfolgt zunächst ein Durchlauf der Inhaltshierarchie.

AEM bestimmt den relevantesten Stil für einen Inhaltsknoten in der folgenden Reihenfolge:

* Wenn ein Design für den vollständigen und genauen Pfad des Inhaltsknotens vorhanden ist (wie bei der Definition des Designs im Designmodus), verwende dieses Design.
* Wenn ein Design für den Inhaltsknoten des übergeordneten Elements vorhanden ist, verwenden dieses Design.
* Wenn sich ein Design für einen Knoten im Pfad des Inhaltsknotens befindet, verwende dieses Design.

Wenn es in den letzten beiden Fällen mehr als ein geeignetes Design gibt, verwende das Design, das dem Inhaltsknoten am nächsten ist.

### Entscheidungsbaum {#decision-tree}

Dies ist eine grafische Darstellung der Logik der [Auflösung des Designpfads](/help/sites-developing/page-templates-static.md#design-path-resolution).

![design_path_resolution](assets/design_path_resolution.png)

### Beispiel {#example}

Denken Sie an eine einfache Inhaltsstruktur wie die folgende, bei der ein Design auf jeden der Knoten angewendet werden könnte:

`/root/branch/leaf`

In der folgenden Tabelle wird beschrieben, wie AEM ein Design auswählt.

<table>
 <tbody>
  <tr>
   <td><strong>Suchen nach einem Design für<br /> </strong></td>
   <td><strong>Designs vorhanden für<br /> </strong></td>
   <td><strong>Ausgewähltes Design<br /> </strong></td>
   <td><strong>Kommentar</strong></td>
  </tr>
  <tr>
   <td><code class="code">leaf
      </code></td>
   <td><p><code>root</code></p> <p><code>branch</code></p> <p><code>leaf</code></p> </td>
   <td><code>leaf</code></td>
   <td>Es wird immer die genaueste Übereinstimmung gewählt.<br /> </td>
  </tr>
  <tr>
   <td><code>leaf</code></td>
   <td><p><code>root</code></p> <p><code>branch</code></p> </td>
   <td><code>branch</code></td>
   <td>Fallen Sie zurück auf die nächstgelegene Übereinstimmung weiter unten in der Baumstruktur.</td>
  </tr>
  <tr>
   <td><code>leaf</code></td>
   <td><code>root</code></td>
   <td><code>root</code></td>
   <td>Wenn alles andere fehlschlägt, nehmen Sie, was übrig ist.<br /> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><code>branch</code></td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>branch</code></p> <p><code class="code">leaf
       </code></p> </td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>root</code></p> <p><code class="code">branch
       </code></p> </td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>root</code></p> <p><code class="code">leaf
       </code></p> </td>
   <td><code>root</code></td>
   <td><p>Wenn es keine exakte Übereinstimmung gibt, nehmen Sie das Design ganz unten in der Baumstruktur.</p> <p>Es wird davon ausgegangen, dass dieses immer anwendbar ist, aber weiter oben im Baum zu spezifisch sein kann.<br /> </p> </td>
  </tr>
 </tbody>
</table>

## Entwickeln von Seitenvorlagen {#developing-page-templates}

AEM-Seitenvorlagen sind schlicht Modelle, die zum Erstellen von Seiten verwendet werden. Sie können anfänglich so wenig oder viel Inhalt enthalten, wie erforderlich ist. Ihre Aufgabe besteht darin, die korrekten anfänglichen Knotenstrukturen zu erstellen, wobei die benötigten Eigenschaften (v. a. „sling:resourceType“) so eingestellt werden, dass sie Bearbeitungs- und Render-Vorgänge zulassen.

### Erstellen einer Vorlage (basierend auf einer vorhandenen Vorlage) {#creating-a-new-template-based-on-an-existing-template}

Eine neue Vorlage kann komplett neu erstellt werden. Um Zeit und Aufwand zu reduzieren, können Sie stattdessen aber auch eine vorhandene Vorlage kopieren und aktualisieren. So können Sie z. B. zum Einstieg die Vorlagen von Geometrixx nutzen.

So erstellen Sie eine Vorlage basierend auf einer vorhandenen Vorlage:

1. Kopieren Sie eine vorhandene Vorlage (vorzugsweise mit einer Definition, die der von Ihnen gewünschten Definition möglichst ähnlich ist) in einen neuen Knoten.

   Vorlagen sind im Verzeichnis **/apps/&lt;Website-Name>/templates/&lt;Vorlagenname>** gespeichert.

   >[!NOTE]
   >
   >Die Liste der verfügbaren Vorlagen hängt vom Ort der neuen Seite und den Einschränkungen für die Platzierung ab, die in jeder Vorlage vorgegeben sind. Siehe [Vorlagenverfügbarkeit](#templateavailibility).

1. Ändern Sie den **jcr:title** des neuen Vorlagenknotens, um seine Rolle widerzuspiegeln. Sie können bei Bedarf außerdem die **jcr:description** aktualisieren. Stellen Sie sicher, dass Sie die Vorlagenverfügbarkeit der Seite entsprechend ändern.

   >[!NOTE]
   >
   >Damit Ihre Vorlage im Dialogfeld **Seite erstellen** angezeigt wird, wenn Sie eine Seite direkt unter **Websites** in der **Websites-Konsole** erstellen, legen Sie für die Eigenschaft `allowedPaths` folgenden Wert fest: `/content(/.*)?`

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Kopieren Sie die Komponente, auf der die Vorlage basiert (dies ist an der Eigenschaft **sling:resourceType** des Knotens **jcr:content** in der Vorlage zu erkennen), um eine neue Instanz zu erstellen.

   Komponenten sind im Verzeichnis **/apps/&lt;Website-Name>/components/&lt;Komponentenname>** gespeichert.

1. Aktualisieren Sie den **jcr:title** und die **jcr:description** der neuen Komponente.
1. Ersetzen Sie die Datei „thumbnail.png“, wenn Sie möchten, dass ein neues Miniaturbild in der Vorlagen-Auswahlliste angezeigt wird (Größe: 128 x 98 Pixel).
1. Aktualisieren Sie den **sling:resourceType** des Knotens **jcr:content** der Vorlage, um auf die neue Komponente zu verweisen.
1. Nehmen Sie weitere Änderungen an der Funktionalität oder dem Design der Vorlage, der zugrunde liegenden Komponente oder beidem vor.

   >[!NOTE]
   >
   >Änderungen, die am Knoten **/apps/&lt;Website>/templates/&lt;Vorlagenname>** vorgenommen werden, wirken sich auf die Vorlageninstanz aus (wie in der Auswahlliste).
   >
   >
   Änderungen, die am Knoten **/apps/&lt;Website>/components/&lt;Komponentenname>** vorgenommen werden, wirken sich auf die Inhaltsseite aus, die mit der Vorlage erstellt wird.

   Sie können jetzt eine Seite Ihrer Website mit der neuen Vorlage erstellen.

>[!NOTE]
>
Die Client-Bibliothek des Editors setzt voraus, dass der Namespace `cq.shared` in den Inhaltsseiten vorhanden ist. Wenn nicht, wird der JavaScript-Fehler `Uncaught TypeError: Cannot read property 'shared' of undefined` ausgegeben.
>
Alle Beispielinhaltsseiten enthalten `cq.shared`, sodass jeglicher darauf basierender Inhalt automatisch `cq.shared` umfasst. Wenn Sie sich jedoch ganz neue eigene Inhaltsseiten erstellen möchten, die nicht auf Beispielinhalt basieren, müssen Sie sicherstellen, dass Sie den Namespace `cq.shared` einbinden.
>
Weitere Informationen finden Sie unter [Verwendung Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md).

## Bereitstellen einer vorhandenen Vorlage {#making-an-existing-template-available}

Dieses Beispiel zeigt, wie Sie zulassen können, dass eine Vorlage für bestimmte Inhaltspfade genutzt werden kann. Die Vorlagen, die Autorinnen und Autoren bei der Erstellung von Seiten zur Verfügung stehen, werden durch die unter [Vorlagenverfügbarkeit](/help/sites-developing/templates.md#template-availability) definierte Logik bestimmt.

1. Navigieren Sie in CRXDE Lite zu der Vorlage, die Sie für Ihre Seite verwenden möchten, z. B. zur Newsletter-Vorlage.
1. Ändern Sie die Eigenschaft `allowedPaths` und andere Eigenschaften, die für die [Vorlagenverfügbarkeit](/help/sites-developing/templates.md#template-availability) genutzt werden. Beispielsweise `allowedPaths`: `/content/geometrixx-outdoors/[^/]+(/.*)?` bedeutet, dass diese Vorlage in jedem Pfad unter `/content/geometrixx-outdoors` zulässig ist.

   ![chlimage_1-89](assets/chlimage_1-89.png)
