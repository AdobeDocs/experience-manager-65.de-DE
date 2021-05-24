---
title: Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren
seo-title: Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren
description: Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren
seo-description: Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren
uuid: 3f5aaf36-e6a7-4a3c-b305-e35ebcc98d0d
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 2aef9048-9d6e-4f5d-b443-5e73f8066d76
docset: aem65
exl-id: 9ef9ae75-cd8c-4adb-9bcb-e951d200d492
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 82%

---

# Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren{#content-fragments-configuring-components-for-rendering}

Es gibt mehrere [erweiterte Dienste](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) zum Rendern von Inhaltsfragmenten. Um diese Dienste zu verwenden, müssen sich die Ressourcentypen dieser Komponenten dem Inhaltsfragmente-Framework bekannt machen.

Dies erfolgt durch die Konfiguration von [OSGi-Dienst – Konfiguration der Inhaltsfragment-Komponente](#osgi-service-content-fragment-component-configuration).

>[!CAUTION]
>
>Wenn Sie die unten beschriebenen [erweiterten Dienste](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) nicht benötigen, können Sie diese Konfiguration ignorieren.

>[!CAUTION]
>
>Wenn Sie die vordefinierte(n) Komponente(n) erweitern oder verwenden, wird eine Änderung der Konfiguration nicht empfohlen.

>[!CAUTION]
>
>Sie können eine Komponente von Grund auf neu schreiben, die nur die Inhaltsfragmente-API verwendet, ohne die erweiterten Dienste zu nutzen. In einem solchen Fall müssen Sie Ihre Komponente jedoch so entwickeln, dass sie die entsprechende Verarbeitung übernimmt.
>
>Daher wird die Verwendung der Kernkomponenten empfohlen.

## Definition erweiterter Dienste, die konfiguriert werden müssen {#definition-of-advanced-services-that-need-configuration}

Die Dienste, die die Registrierung einer Komponente erfordern:

* bestimmen Abhängigkeiten während der Veröffentlichung korrekt (d. h. stellen sicher, dass Fragmente und Modelle automatisch mit einer Seite veröffentlicht werden können, wenn sie sich seit der letzten Veröffentlichung geändert haben),
* unterstützen Inhaltsfragmente in der Volltextsuche,
* verwalten/bearbeiten *Zwischeninhalte*,
* verwalten/bearbeiten *gemischte Medien-Assets*,
* Dispatcher-Flush für referenzierte Fragmente (wenn eine Seite, die ein Fragment enthält, erneut veröffentlicht wird),
* verwenden absatzbasiertes Rendering.

Wenn Sie eine oder mehrere dieser Funktionen benötigen, ist es (in der Regel) einfacher, die vordefinierte Funktion zu verwenden, anstatt sie von Grund auf neu zu entwickeln.

## OSGi-Dienst – Konfiguration der Inhaltsfragment-Komponente {#osgi-service-content-fragment-component-configuration}

Die Konfiguration muss an den OSGi-Dienst **Konfiguration der Inhaltsfragment-Komponente** gebunden sein:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) .

Beispiel:

![cfm-01](assets/cfm-01.png)

Die OSGi-Konfiguration lautet:

<table>
 <tbody>
  <tr>
   <td>Bezeichnung</td>
   <td>OSGi-Konfiguration<br /> </td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><strong>Ressourcentyp</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>Der zu registrierende Ressourcentyp; z. B. <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Verweiseigenschaft</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>Der Name der Eigenschaft, die den Verweis auf das Fragment enthält; z. B. <code>fragmentPath</code> oder <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Elementeigenschaft</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>Der Name der Eigenschaft, die die Namen der Elemente enthält, die gerendert werden sollen; z. B.<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Varianteneigenschaft</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>Der Name der Eigenschaft, die den Namen der zu rendernden Variante enthält; z. B.<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Für einige Funktionen (z. B. um nur einen Absatzbereich zu rendern) müssen Sie einige Konventionen einhalten:

<table>
 <tbody>
  <tr>
   <td>Eigenschaftsname</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Eine Zeichenfolgeneigenschaft, die den Bereich der Absätze definiert, die ausgegeben werden sollen, wenn sie sich im <em>Rendermodus für einzelne Elemente</em> befinden.</p> <p>Format:</p>
    <ul>
     <li><code>1</code> oder <code>1-3</code> oder <code>1-3;6;7-8</code> oder <code>*-3;5-*</code></li>
     <li>nur ausgewertet, wenn <code>paragraphScope</code> = <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>Eine Zeichenfolgeneigenschaft, die definiert, wie Absätze ausgegeben werden sollen, wenn sie sich im <em>Rendermodus für einzelne Elemente</em> befinden.</p> <p>Werte:</p>
    <ul>
     <li><code>all</code> : zum Rendern aller Absätze</li>
     <li><code>range</code> : zum Rendern des Bereichs der Absätze, die hier angegeben sind: <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>Eine boolesche Eigenschaft, die definiert, ob Überschriften (z. B. <code>h1</code>, <code>h2</code>, <code>h3</code>) als Absätze (<code>true</code>) oder nicht als Absätze (<code>false</code>) gezählt werden sollen</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Dies kann sich in späteren 6,5 Meilensteinen ändern.

## Beispiel {#example}

Sehen Sie sich folgendes Beispiel (in einer vordefinierten AEM-Instanz) an:

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

Es umfasst:

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```
