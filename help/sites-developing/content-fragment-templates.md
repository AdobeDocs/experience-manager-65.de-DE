---
title: Inhaltsfragmentvorlagen
seo-title: Content Fragment Templates
description: Vorlagen werden ausgewählt, wenn ein Inhaltsfragment erstellt und das neue Fragment mit der grundlegenden Struktur, dem Element und der Variante versehen wird
seo-description: Templates are selected when creating a content fragmen and provide the new fragment with the basic structure, element, and variation
uuid: d147bac8-b710-40ed-9664-decb5ffcf8e7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: a975ea2e-5e24-4a96-bd62-63bb98836ff2
docset: aem65
exl-id: 1b75721c-b223-41f0-88d9-bd855b529f31
source-git-commit: a2b1bd5462ae1837470e31cfeb87a95af1c69be5
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 34%

---

# Inhaltsfragmentvorlagen{#content-fragment-templates}

>[!CAUTION]
>
>[Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) werden für die Erstellung aller neuen Inhaltsfragmente empfohlen.
>
>Inhaltsfragmentmodelle werden für alle Beispiele in WKND verwendet.

>[!NOTE]
>
>Vor AEM 6.3 wurden Inhaltsfragmente basierend auf Vorlagen statt auf Modellen erstellt.
>
>Inhaltsfragmentvorlagen werden jetzt nicht mehr unterstützt. Sie können weiterhin zum Erstellen von Fragmenten verwendet werden. Es wird jedoch empfohlen, stattdessen Inhaltsfragmentmodelle zu verwenden. Fragmentvorlagen werden keine neuen Funktionen hinzugefügt und in einer zukünftigen Version entfernt.

Vorlagen werden beim Erstellen eines Inhaltsfragments ausgewählt. Sie verleihen dem neuen Fragment Grundstruktur, Element(e) und Variante. Die Vorlagen, die für Inhaltsfragmente verwendet werden, unterliegen dem Granite Configuration Manager.

Die im Lieferumfang enthaltenen Vorlagen befinden sich unter:

* `/libs/settings/dam/cfm/templates`

Sie können Ihre Website-spezifischen Vorlagen für Inhaltsfragmente erstellen unter:

* `/apps/settings/dam/cfm/templates`
Der Speicherort für die Überlagerung von nativen Vorlagen oder die Bereitstellung kundenspezifischer, anwendungsweiter Vorlagen, die zur Laufzeit nicht erweitert/geändert werden sollen.

* `/conf/global/settings/dam/cfm/templates`
Der Speicherort für instanzweite kundenspezifische Vorlagen, die zur Laufzeit geändert werden müssen.

Die Rangfolge lautet (in absteigender Reihenfolge). `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element (d. h. wie es in vorhanden ist) neu. `/libs`) unter `/apps`
>
>1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

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
     <td>Der Titel der Vorlage (angezeigt im <strong>Fragment erstellen</strong> Assistent).</td>
    </tr>
    <tr>
     <td><code>jcr:description</code></td>
     <td><p><code>String</code></p> <p>optional</p> </td>
     <td>Ein Text, der den Zweck der Vorlage beschreibt (angezeigt im <strong>Fragment erstellen</strong> Assistent).</td>
    </tr>
    <tr>
     <td><code>initialAssociatedContent</code></td>
     <td><p><code>String[]</code></p> <p>optional</p> </td>
     <td>Ein Array mit Pfaden zu Sammlungen, die standardmäßig mit einem neu erstellten Inhaltsfragment verknüpft werden sollen.</td>
    </tr>
    <tr>
     <td><code>precreateElements</code></td>
     <td><p><code>Boolean</code></p> <p>required</p> </td>
     <td><p><code>true</code>, wenn die Teil-Assets, die die Elemente des Inhaltsfragments darstellen (mit Ausnahme des Übergeordneten Elements), bei der Erstellung des Inhaltsfragments erstellt werden sollen; <em>false</em> , wenn sie "on the fly" erstellt werden sollen.</p> <p><strong>Hinweis</strong>: Dieser Parameter muss derzeit auf <code>true</code>.</p> </td>
    </tr>
    <tr>
     <td><code>version</code></td>
     <td><p><code>Long</code></p> <p>erforderlich</p> </td>
     <td><p>Version der Inhaltsstruktur; derzeit unterstützt:</p> <p><strong>Hinweis</strong>: Dieser Parameter muss derzeit auf <code>2</code>.<br /> </p> </td>
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
     <td><p>Knoten, der die Definition der Elemente des Inhaltsfragments enthält. Sie ist obligatorisch und muss mindestens einen untergeordneten Knoten für die <strong>Main</strong> -Element, kann jedoch [1..n] untergeordneten Knoten enthalten.</p> <p>Wenn die Vorlage verwendet wird, wird der Unterzweig Elemente in den Modellunterzweig des Fragments kopiert.</p> <p>Das erste Element (wie in CRXDE Lite angezeigt) wird automatisch als <i>main</i> Element; der Knotenname ist irrelevant und der Knoten selbst hat keine besondere Bedeutung, abgesehen von der Tatsache, dass er durch das Haupt-Asset dargestellt wird. die anderen Elemente werden als Teil-Assets behandelt.</p> </td>
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
     <td>Der Titel des Elements (wird in der Elementauswahl des Fragment-Editors angezeigt).</td>
    </tr>
    <tr>
     <td><code>defaultContent</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: ""</p> </td>
     <td>Anfänglicher Inhalt des Elements; nur verwendet, wenn <code>precreateElements</code><i> = </i><code>true</code></td>
    </tr>
    <tr>
     <td><code>initialContentType</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: <code>text/html</code></p> </td>
     <td><p>Art des anfänglichen Inhalts des Elements; nur verwendet, wenn <code>precreateElements</code><i> = </i><code>true</code>; derzeit unterstützt:</p>
      <ul>
       <li><code>text/html</code></li>
       <li><code>text/plain</code></li>
       <li><code>text/x-markdown</code></li>
      </ul> </td>
    </tr>
    <tr>
     <td><code>name</code></td>
     <td><p><code>String</code></p> <p>erforderlich</p> </td>
     <td>Interner Name des Elements; muss für den Fragmenttyp eindeutig sein.</td>
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
     <td>Dieser optionale Knoten enthält die Definition der anfänglichen Varianten des Inhaltsfragments.</td>
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
     <td><p><code>nt:unstructured</code></p> <p>erforderlich, wenn ein Variantenknoten vorhanden ist</p> </td>
     <td><p>Definiert eine anfängliche Variante.<br /> Die Variante wird standardmäßig allen Elementen des Inhaltsfragments hinzugefügt.</p> <p>Die Variante hat denselben anfänglichen Inhalt wie das entsprechende Element (siehe <code class="code">defaultContent/
       initialContentType</code>)</p> </td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>erforderlich</p> </td>
     <td>Der Titel der Variante (der im Fragment-Editor in der <strong>Variante</strong> Registerkarte (linke Leiste).</td>
    </tr>
    <tr>
     <td><code>jcr:desciption</code></td>
     <td><p><code>String</code></p> <p>optional</p> <p>default: ""</p> </td>
     <td>Ein Text mit einer Beschreibung der Variante <span>(wird im Fragment-Editor in der <strong>Variante</strong> Registerkarte (linke Leiste).</code></td>
    </tr>
   </tbody>
  </table>
