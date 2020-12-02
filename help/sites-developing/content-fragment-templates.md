---
title: Inhaltsfragmentvorlagen
seo-title: Inhaltsfragmentvorlagen
description: Vorlagen werden ausgewählt, wenn ein Inhaltsfragment erstellt und das neue Fragment mit der grundlegenden Struktur, dem Element und der Variante versehen wird
seo-description: Vorlagen werden ausgewählt, wenn ein Inhaltsfragment erstellt und das neue Fragment mit der grundlegenden Struktur, dem Element und der Variante versehen wird
uuid: d147bac8-b710-40ed-9664-decb5ffcf8e7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: a975ea2e-5e24-4a96-bd62-63bb98836ff2
docset: aem65
translation-type: tm+mt
source-git-commit: a430c4de89bde3b907d342106465d3b5a7c75cc8
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 41%

---


# Inhaltsfragmentvorlagen{#content-fragment-templates}

>[!CAUTION]
>
>Es werden derzeit [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) zum Erstellen aller Fragmente empfohlen.
>
>Inhaltsfragmentmodelle werden für alle Beispiele in We.Retail verwendet.

Vorlagen werden beim Erstellen eines Inhaltsfragments ausgewählt. Sie verleihen dem neuen Fragment Grundstruktur, Element(e) und Variante. Die Vorlagen, die für Inhaltsfragmente verwendet werden, unterliegen dem Granite Configuration Manager.

Die im Lieferumfang enthaltenen Vorlagen befinden sich unter:

* `/libs/settings/dam/cfm/templates`

Sie können Ihre Website-spezifischen Vorlagen für Inhaltsfragmente erstellen unter:

* `/apps/settings/dam/cfm/templates`
Der Speicherort zum Überlagern von vordefinierten Vorlagen oder Bereitstellen kundenspezifischer, anwendungsweiter Vorlagen, die zur Laufzeit nicht erweitert/geändert werden sollen.

* `/conf/global/settings/dam/cfm/templates`
Der Speicherort für kundenspezifische Instanzvorlagen, die zur Laufzeit geändert werden müssen.

Die Rangfolge lautet (in absteigender Reihenfolge) `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element (d. h. wie es in `/libs` vorhanden ist) unter `/apps` neu
   >
   >
1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

>



Die grundlegende Struktur einer Vorlage befindet sich unter:

```xml
conf
  global
    settings
      dam
        cfm
          templates
            <template-name>
              ...
```

Dabei ist die bestimmte Struktur:

```xml
+ <template-name>
    - jcr:primaryType
    - jcr:title
    - jcr:description
    - initialAssociatedContent
    - precreateElements
    - version
    + elements
        - jcr:primaryType
        + <element-name>
            - jcr:primaryType
            - jcr:title
            - defaultContent
            - initialContentType
            - name
        ... + other element definitions
    + variations
        - jcr:primaryType
        + <variation-name>
            - jcr:primaryType
            - jcr:title
            - jcr:description
            - name
        ... + other variation definitions
```

Weitere Details zu den Knoten und ihren Eigenschaften sind:

* **Vorlage**

   <table>
   <tbody>
    <tr>
     <th>Name</th>
     <th>Typ</th>
     <th>Wert</th>
    </tr>
    <tr>
     <td><code>&lt;<em>template-name</em>&gt;</code></td>
     <td><code>nt:unstructured</code></td>
     <td>Dieser Knoten ist der Stamm für jede Vorlage. Er ist vorgeschrieben und muss einen eindeutigen Namen haben.</td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>required<br /> </p> </td>
     <td>Der Titel der Vorlage (angezeigt im Assistenten <strong>Fragment erstellen</strong>).</td>
    </tr>
    <tr>
     <td><code>jcr:description</code></td>
     <td><p><code>String</code></p> <p>optional</p> </td>
     <td>Ein Text, der den Zweck der Vorlage beschreibt (angezeigt im Assistenten <strong>Fragment erstellen</strong>).</td>
    </tr>
    <tr>
     <td><code>initialAssociatedContent</code></td>
     <td><p><code>String[]</code></p> <p>optional</p> </td>
     <td>Ein Array mit Pfaden zu Sammlungen, die standardmäßig mit einem neu erstellten Inhaltsfragment verknüpft werden sollen.</td>
    </tr>
    <tr>
     <td><code>precreateElements</code></td>
     <td><p><code>Boolean</code></p> <p>erforderlich</p> </td>
     <td><p><code>true</code>, wenn die Teilassets, die die Elemente (mit Ausnahme des Übergeordnet-Elements) des Inhaltsfragments darstellen, beim Erstellen des Inhaltsfragments erstellt werden sollten; <em>false</em>, wenn sie "on the fly"erstellt werden sollen.</p> <p><strong>Hinweis</strong>: Derzeit muss dieser Parameter auf  <code>true</code>.</p> </td>
    </tr>
    <tr>
     <td><code>version</code></td>
     <td><p><code>Long</code></p> <p>erforderlich</p> </td>
     <td><p>Version der Inhaltsstruktur; derzeit unterstützt:</p> <p><strong>Hinweis</strong>: Derzeit muss dieser Parameter auf  <code>2</code>.<br /> </p> </td>
    </tr>
   </tbody>
  </table>

* **Elemente**

   <table>
   <tbody>
    <tr>
     <th>Name</th>
     <th>Typ</th>
     <th>Wert</th>
    </tr>
    <tr>
     <td><code>elements</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>erforderlich</p> </td>
     <td><p>Knoten, der die Definition der Elemente des Inhaltsfragments enthält. Es ist obligatorisch und muss mindestens einen untergeordneten Knoten für das <strong>Main</strong>-Element enthalten, kann jedoch [1] enthalten.n] untergeordneten Knoten enthalten.</p> <p>Wenn die Vorlage verwendet wird, wird die Unterverzweigung "Elemente"in die Unterverzweigung "Modell"des Fragments kopiert.</p> <p>Das erste Element (wie in CRXDE Lite angezeigt) wird automatisch als <i>main</i>-Element betrachtet. der Knotenname ist irrelevant und der Knoten selbst hat keine besondere Bedeutung, abgesehen davon, dass er vom Hauptvermögen dargestellt wird; die anderen Elemente werden als Teilassets behandelt.</p> </td>
    </tr>
   </tbody>
  </table>

* **Elementname**

   <table>
   <tbody>
    <tr>
     <th>Name</th>
     <th>Typ</th>
     <th>Wert</th>
    </tr>
    <tr>
     <td><code>&lt;<i>element-name</i>&gt;</code></td>
     <td><code>nt:unstructured</code></td>
     <td>Dieser Knoten definiert ein Element. Er ist vorgeschrieben und muss einen eindeutigen Namen haben.</td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>erforderlich</p> </td>
     <td>Der Titel des Elements (angezeigt in der Elementauswahl des Fragmenteditors).</td>
    </tr>
    <tr>
     <td><code>defaultContent</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: ""</p> </td>
     <td>Anfangsinhalt des Elements; nur verwendet, wenn <code>precreateElements</code><i> = </i><code>true</code></td>
    </tr>
    <tr>
     <td><code>initialContentType</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: <code>text/html</code></p> </td>
     <td><p>Typ des anfänglichen Inhalts des Elements; nur verwendet, wenn <code>precreateElements</code><i> = </i><code>true</code>; derzeit unterstützt:</p>
      <ul>
       <li><code>text/html</code></li>
       <li><code>text/plain</code></li>
       <li><code>text/x-markdown</code></li>
      </ul> </td>
    </tr>
    <tr>
     <td><code>name</code></td>
     <td><p><code>String</code></p> <p>erforderlich</p> </td>
     <td>der interne Name des Elements; muss eindeutig für den Fragmenttyp sein.</td>
    </tr>
   </tbody>
  </table>

* **Varianten**

   <table>
   <tbody>
    <tr>
     <th>Name</th>
     <th>Typ</th>
     <th>Wert</th>
    </tr>
    <tr>
     <td><code>variations</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>optional</p> </td>
     <td>Diese optionale Node enthält die Definition der anfänglichen Variationen des Inhaltsfragments.</td>
    </tr>
   </tbody>
  </table>

* **Variantenname**

   <table>
   <tbody>
    <tr>
     <th>Name</th>
     <th>Typ</th>
     <th>Wert</th>
    </tr>
    <tr>
     <td><code>&lt;<i>variation-name</i>&gt;</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>erforderlich, wenn ein Variationsknoten vorhanden ist</p> </td>
     <td><p>Definiert eine anfängliche Änderung.<br /> Die Variante wird standardmäßig allen Elementen des Inhaltsfragments hinzugefügt.</p> <p>Die Änderung hat denselben anfänglichen Inhalt wie das entsprechende Element (siehe <code class="code">defaultContent/
       initialContentType</code>).</p> </td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>erforderlich</p> </td>
     <td>Der Titel der Variante (angezeigt im Register <strong>Variation</strong> des Fragmenteditors (linke Leiste)).</td>
    </tr>
    <tr>
     <td><code>jcr:desciption</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: ""</p> </td>
     <td>Ein Text, der eine Beschreibung der Variation <span> enthält (angezeigt auf der Registerkarte <strong>Variation</strong> des Fragmenteditors (linke Leiste)).</code></td>
    </tr>
   </tbody>
  </table>
