---
title: Identifizieren zu übersetzender Inhalte
seo-title: Identifizieren zu übersetzender Inhalte
description: Erfahren Sie, wie sich zu übersetzende Inhalte identifizieren lassen.
seo-description: Erfahren Sie, wie sich zu übersetzende Inhalte identifizieren lassen.
uuid: 81b9575c-1c7a-4955-b03f-3f26cbd4f956
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: eedff940-4a46-4c24-894e-a5aa1080d23d
feature: Sprachkopie
exl-id: 8ca7bbcc-413a-49a8-a836-7083a9cadda1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 87%

---

# Identifizieren zu übersetzender Inhalte{#identifying-content-to-translate}

Die Übersetzungsregeln identifizieren die zu übersetzenden Inhalte für Seiten, Komponenten und Assets, die in die Übersetzungsprojekte integriert oder von diesen ausgeschlossen sind. Wenn eine Seite oder ein Asset übersetzt wird, extrahiert AEM diese Inhalte, sodass sie an den Übersetzungsdienstleister gesendet werden können.

Die Seiten und Assets werden als Knoten im JCR-Repository dargestellt. Bei dem extrahierten Inhalt handelt es sich um einen oder mehrere Eigenschaftswerte des Knotens. Die Übersetzungsregeln identifizieren die Eigenschaften, die den zu extrahierenden Inhalt enthalten.

Übersetzungsregeln werden im XML-Format ausgedrückt und an folgenden Orten gespeichert:

* `/libs/settings/translation/rules/translation_rules.xml`
* `/apps/settings/translation/rules/translation_rules.xml`
* `/conf/global/settings/translation/rules/translation_rules.xml`

Die Datei gilt für alle Übersetzungsprojekte.

>[!NOTE]
>
>Nach einer Aktualisierung auf 6.4 wird empfohlen, die Datei aus /etc zu verschieben. Weitere Informationen finden Sie unter [Allgemeine Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-rules) .

Die Regeln umfassen die folgenden Informationen:

* Den Pfad des Knotens, auf den die Regel angewendet wird. Die Regel gilt auch für die nachfolgenden Elemente des Knotens.
* Die Namen der Knoteneigenschaften, die den zu übersetzenden Inhalt enthalten. Die Eigenschaft kann sich speziell auf einen bestimmten Ressourcentyp oder auf alle Ressourcentypen beziehen.

Sie können zum Beispiel eine Regel erstellen, die den von den Autoren hinzugefügten Inhalt für alle AEM Foundation-Textkomponenten auf Ihren Seiten übersetzt. Die Regel kann den Knoten `/content` und die Eigenschaft `text` für die Komponente `foundation/components/text` identifizieren.

Es gibt eine eigene [Konsole](#translation-rules-ui), die für die Konfiguration von Übersetzungsregeln hinzugefügt wurde. Die Definitionen in der Benutzeroberfläche füllen die Datei für Sie auf.

Einen Überblick über die Funktionen zur Übersetzung von Inhalten in AEM erhalten Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md).

>[!NOTE]
>
>AEM unterstützt die 1-zu-1-Zuordnung zwischen Ressourcentypen und Bezugsattributen für die Übersetzung von referenziertem Inhalt auf einer Seite.

## Regelsyntax für Seiten, Komponenten und Assets {#rule-syntax-for-pages-components-and-assets}

Eine Regel ist ein `node`-Element mit einem oder mehreren untergeordneten `property`-Elementen und keinem oder mehreren untergeordneten `node`-Elementen:

```xml
<node path="content path">
          <property name="property name" [translate="false"]/>
          <node resourceType="component path" >
               <property name="property name" [translate="false"]/>
          </node>
</node>
```

Jedes dieser `node`-Elemente hat die folgenden Eigenschaften:

* Das `path`-Attribut enthält den Pfad zum Stammknoten des Zweigs, für den die Regeln gelten.
* Die untergeordneten `property`-Elemente identifizieren die Knoteneigenschaften, die für alle Ressourcentypen zu übersetzen sind:

   * Das Attribut `name` enthält den Eigenschaftsnamen.
   * Das optionale Attribut `translate` ist gleich `false`, wenn die Eigenschaft nicht übersetzt ist. Standardmäßig lautet der Wert `true`. Dieses Attribut ist nützlich für die Außerkraftsetzung vorheriger Regeln.

* Die untergeordneten `node`-Elemente identifizieren die Knoteneigenschaften, die für bestimmte Ressourcentypen zu übersetzen sind:

   * Das Attribut `resourceType` enthält den Pfad, der zu der für die Implementierung des Ressourcentyps verantwortlichen Komponente führt.
   * Die untergeordneten `property`-Elemente identifizieren die zu übersetzende Knoteneigenschaft. Verwenden Sie diesen Knoten auf dieselbe Art und Weise wie die untergeordneten `property`-Elemente zu den Knotenregeln.

Die folgende Beispielregel veranlasst, dass alle `text`-Eigenschaften für alle Seiten unter dem Knoten `/content` übersetzt werden. Die Regel gilt für jede Komponente, die Inhalt in einer `text`-Eigenschaft speichert, so zum Beispiel die Foundation-Textkomponente und die Foundation-Bildkomponente.

```xml
<node path="/content">
          <property name="text"/>
</node>
```

Das folgende Beispiel übersetzt den Inhalt aller `text`-Eigenschaften sowie andere Eigenschaften der Foundation-Bildkomponente. Wenn andere Komponenten über Eigenschaften mit demselben Namen verfügen, gilt die Regel nicht für sie.

```xml
<node path="/content">
      <property name="text"/>
      <node resourceType="foundation/components/textimage">
         <property name="image/alt"/>
         <property name="image/jcr:description"/>
         <property name="image/jcr:title"/>
      </node>
</node>
```

## Regelsyntax für die Extrahierung von Assets von Seiten   {#rule-syntax-for-extracting-assets-from-pages}

Verwenden Sie die folgende Regelsyntax, um in andere Komponenten integrierte oder durch andere Komponenten referenzierte Assets einzubeziehen:

```xml
<assetNode resourceType="path to component" assetReferenceAttribute="property that stores asset"/>
```

Jedes `assetNode`-Element hat die folgenden Merkmale:

* Ein `resourceType`-Attribut, das dem zu der Komponente führenden Pfad entspricht.
* Ein dem Namen der Eigenschaft entsprechendes `assetReferenceAttribute`, das (bei integrierten Assets) die Binärdaten des Assets oder den Pfad zum referenzierten Asset enthält.

Das folgende Beispiel extrahiert Bilder aus der Foundation-Bildkomponente:

```xml
<assetNode resourceType="foundation/components/image" assetReferenceAttribute="fileReference"/>
```

## Außerkraftsetzungsregeln {#overriding-rules}

Die Datei translation_rules.xml besteht aus einem `nodelist`-Element mit mehreren untergeordneten `node`-Elementen. AEM liest die Knotenliste von oben nach unten. Wenn mehrere Regeln auf denselben Knoten abzielen, wird die in der Datei weiter unten aufgeführte Regel verwendet. Beispielsweise veranlassen die folgenden Regeln, dass alle Inhalte in den `text`-Eigenschaften übersetzt werden, außer dem Seitenzweig `/content/mysite/en`:

```xml
<nodelist>
     <node path="/content”>
           <property name="text" />
     </node>
     <node path=“/content/mysite/en”>
          <property name=“text” translate=“false" />
     </node>
<nodelist>
```

## Filtern von Eigenschaften {#filtering-properties}

Mit dem`filter`-Element können Sie auf Knoten mit einer spezifischen Eigenschaft filtern.

Beispielsweise veranlassen die folgenden Regeln, dass alle Inhalte in `text`-Eigenschaften übersetzt werden – mit Ausnahme der Knoten, bei denen die Eigenschaft `draft` auf `true` eingestellt ist.

```xml
<nodelist>
    <node path="/content”>
     <filter>
   <node containsProperty="draft" propertyValue="true" />
     </filter>
        <property name="text" />
    </node>
<nodelist>
```

## Benutzeroberfläche für Übersetzungsregeln {#translation-rules-ui}

Zum Konfigurieren von Übersetzungsregeln steht auch eine Konsole zur Verfügung.

So können Sie darauf zugreifen:

1. Navigieren Sie zu **Tools** und dann zu **Allgemein**.

   ![chlimage_1-55](assets/chlimage_1-55.jpeg)

1. Wählen Sie **Übersetzungskonfiguration** aus.

   ![chlimage_1-56](assets/chlimage_1-56.jpeg)

Von hier aus können Sie **Kontext** hinzufügen. Dies ermöglicht Ihnen das Hinzufügen eines Pfads.

![chlimage_1-57](assets/chlimage_1-57.jpeg)

Anschließend müssen Sie Ihren Kontext auswählen und dann auf **Bearbeiten** klicken. Hierdurch wird der Editor für Übersetzungsregeln geöffnet.

![chlimage_1-58](assets/chlimage_1-58.jpeg)

Es gibt vier Attribute, die Sie über die Benutzeroberfläche ändern können: `isDeep`, `inherit`, `translate` und `updateDestinationLanguage`.

**** isDeepDieses Attribut gilt für Knotenfilter und ist standardmäßig &quot;true&quot;. Es prüft, ob der Knoten oder seine Vorgängerelemente die Eigenschaft mit dem im Filter angegebenen Eigenschaftswert enthalten. Bei „false“ wird die Überprüfung nur für den aktuellen Knoten durchgeführt.

Beispielsweise werden untergeordnete Knoten zu einem Übersetzungsauftrag hinzugefügt, selbst wenn für den übergeordneten Knoten die Eigenschaft `draftOnly` auf &quot;true&quot;gesetzt ist, um Entwurfsinhalte zu kennzeichnen. Hier kommt `isDeep` ins Spiel, prüft, ob bei den übergeordneten Knoten die Eigenschaft `draftOnly` auf „true“ eingestellt ist, und schließt diese untergeordneten Knoten aus.

Im Editor können Sie **Is Deep** auf der Registerkarte **Filter** aktivieren/deaktivieren.

![chlimage_1-59](assets/chlimage_1-59.jpeg)

Im folgenden Beispiel ist die xml dargestellt, die generiert wird, wenn **Is Deep** in der Benutzeroberfläche deaktiviert ist:

```xml
 <filter>
    <node containsProperty="draftOnly" isDeep="false" propertyValue="true"/>
</filter>
```

**** inheritDies gilt für Eigenschaften. Standardmäßig werden alle Eigenschaften übernommen. Sollten Sie jedoch wünschen, dass manche Eigenschaften nicht für das untergeordnete Element übernommen werden, können Sie diese Eigenschaft als „false“ markieren, sodass sie nur auf diesen spezifischen Knoten angewendet wird.

In der Benutzeroberfläche können Sie **Übernehmen** auf der Registerkarte **Eigenschaften** aktivieren/deaktivieren.

![chlimage_1-60](assets/chlimage_1-60.jpeg)

**** translateDas Attribut &quot;translate&quot;dient einfach dazu, anzugeben, ob eine Eigenschaft übersetzt werden soll oder nicht.

In der Benutzeroberfläche können Sie **Übersetzen** auf der Registerkarte **Eigenschaften** aktivieren/deaktivieren.

**** updateDestinationLanguageDieses Attribut wird für Eigenschaften verwendet, die keinen Text, sondern Sprachcodes enthalten, z. B. jcr:language. Der Benutzer übersetzt keinen Text, sondern das Sprachschema von der Quelle ins Ziel. Solche Eigenschaften werden nicht zur Übersetzung versendet.

In der Benutzeroberfläche können Sie **Übersetzen** auf der Registerkarte **Eigenschaften** aktivieren/deaktivieren, jedoch für die spezifischen Eigenschaften, die Sprachcodes als Wert haben.

Der Unterschied zwischen `updateDestinationLanguage` und `translate` lässt sich hier anhand eines einfachen Beispiels für einen Kontext mit zwei Regeln veranschaulichen:

![chlimage_1-61](assets/chlimage_1-61.jpeg)

Das Ergebnis in der xml sieht wie folgt aus:

```xml
<property inherit="true" name="text" translate="true" updateDestinationLanguage="false"/>
<property inherit="true" name="jcr:language" translate="false" updateDestinationLanguage="true"/>
```

## Manuelles Bearbeiten der Regeldatei  {#editing-the-rules-file-manually}

Die in AEM installierte Datei translation_rules.xml enthält einen Standardsatz an Übersetzungsregeln. Sie können die Datei bearbeiten, damit die Anforderungen Ihrer Übersetzungsprojekte erfüllt werden. Sie können zum Beispiel Regeln hinzufügen, sodass die Inhalte Ihrer benutzerdefinierten Komponenten übersetzt werden.

Wenn Sie die Datei translation_rules.xml bearbeiten, speichern Sie zuvor eine Sicherungskopie im Inhaltspaket. Durch die Installation von AEM Service Packs oder die erneute Installation bestimmter AEM-Pakete kann die aktuelle Datei translation_rules.xml durch das Original ersetzt werden. Um in dieser Situation die Regeln wiederherzustellen, können Sie das Paket installieren, das Ihre Sicherungskopie enthält.

>[!NOTE]
>
>Erstellen Sie das Paket nach der Erstellung des Inhaltspakets bei jeder Bearbeitung der Datei neu.

## Beispiel für eine Datei mit Übersetzungsregeln  {#example-translation-rules-file}

```xml
<nodelist>
    <!-- translation rules for Geometrixx Demo site (example) -->
    <node path="/content/geometrixx">
        <!-- list all node properties that should be translated -->
        <property name="jcr:title" /> <!-- translation workflows running on content saved in /content/geometrixx, will extract jcr:title values independent of the component. -->
        <property name="jcr:description" />
        <node resourceType ="foundation/components/image"> <!-- translation workflows running on content saved in /content/geometrixx, will extract alternateText values only for Image component. -->
            <property name="alternateText"/>
        </node>
        <node resourceType ="geometrixx/components/title">
            <property name="richText"/>
            <property name="jcr:title" translate="false"/> <!-- translation workflows running on content saved in /content/geometrixx, will not extract jcr:title for Title component, but instead use richText. -->
        </node>
        <node pathContains="/cq:annotations">
            <property name="text" translate="false"/> <!-- translation workflows running on content saved in /content/geometrixx, will not extract text if part of cq:annotations node. -->
        </node>
    </node>
    <!-- translation rules for Geometrixx Outdoors site (example) -->
    <node path="/content/geometrixx-outdoors">
        <node resourceType ="foundation/components/image">
            <property name="alternateText"/>
            <property name="jcr:title" />
        </node>
        <node resourceType ="geometrixx-outdoors/components/title">
            <property name="richText"/>
        </node>
    </node>
    <!-- translation rules for ASSETS (example) -->
    <node path="/content/dam">
        <!-- configure list of metadata properties here -->
        <property name="dc:title" />
        <property name="dc:description" />
    </node>
    <!-- translation rules for extracting ASSETS from SITES content, configure all components that embed or reference assets -->
    <assetNode resourceType="foundation/components/image" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="foundation/components/video" assetReferenceAttribute="asset"/>
    <assetNode resourceType="foundation/components/download" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="foundation/components/mobileimage" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="wcm/foundation/components/image" assetReferenceAttribute="fileReference"/>
</nodelist>
```
