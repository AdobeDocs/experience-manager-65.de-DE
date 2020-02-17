---
title: Inhaltsfragmente Konfigurieren von Komponenten für die Wiedergabe
seo-title: Inhaltsfragmente Konfigurieren von Komponenten für die Wiedergabe
description: Inhaltsfragmente Konfigurieren von Komponenten für die Wiedergabe
seo-description: Inhaltsfragmente Konfigurieren von Komponenten für die Wiedergabe
uuid: 3f5aaf36-e6a7-4a3c-b305-e35ebcc98d0d
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 2aef9048-9d6e-4f5d-b443-5e73f8066d76
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Inhaltsfragmente Konfigurieren von Komponenten für die Wiedergabe{#content-fragments-configuring-components-for-rendering}

Es gibt mehrere [erweiterte Dienste](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) zum Rendern von Inhaltsfragmenten. Um diese Dienste zu verwenden, müssen sich die Ressourcentypen dieser Komponenten dem Inhaltsfragmente-Framework bekannt machen.

Dies erfolgt durch Konfiguration der [OSGi-Dienst - Inhaltsfragment-Komponentenkonfiguration](#osgi-service-content-fragment-component-configuration).

>[!CAUTION]
>
>Wenn Sie die unten beschriebenen [erweiterten Dienste](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) nicht benötigen, können Sie diese Konfiguration ignorieren.

>[!CAUTION]
>
>Wenn Sie die vordefinierte(n) Komponente(n) erweitern oder verwenden, wird eine Änderung der Konfiguration nicht empfohlen.

>[!CAUTION]
>
>Sie können eine Komponente von Grund auf neu schreiben, die nur die Content Fragments API verwendet, ohne erweiterte Dienste. In einem solchen Fall müssen Sie Ihre Komponente jedoch so entwickeln, dass sie die entsprechende Verarbeitung übernimmt.
>
>Daher wird die Verwendung der Kernkomponenten empfohlen.

## Definition erweiterter Dienste, die konfiguriert werden müssen {#definition-of-advanced-services-that-need-configuration}

Die Dienste, für die die Registrierung einer Komponente erforderlich ist, sind:

* Abhängigkeiten während der Veröffentlichung korrekt ermitteln (d. h. sicherstellen, dass Fragmente und Modelle automatisch mit einer Seite veröffentlicht werden können, wenn sie sich seit der letzten Veröffentlichung geändert haben).
* Unterstützung von Inhaltsfragmenten bei der Volltextsuche.
* Verwaltung/Bearbeitung von *Inhalten zwischen*
* Verwaltung/Bearbeitung von *gemischten Medienelementen.*
* Dispatcher-Flush für referenzierte Fragmente (wenn eine Seite, die ein Fragment enthält, erneut veröffentlicht wird).
* Absatzbasiertes Rendering.

Wenn Sie eine oder mehrere dieser Funktionen benötigen, ist es in der Regel einfacher, die vordefinierte Funktion zu verwenden, anstatt sie von Grund auf zu entwickeln.

## OSGi-Dienst - Konfiguration der Inhaltsfragment-Komponente {#osgi-service-content-fragment-component-configuration}

Die Konfiguration muss an die OSGi-Dienst- **Inhaltsfragment-Komponentenkonfiguration** gebunden sein:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>See [Configuring OSGi](/help/sites-deploying/configuring-osgi.md) for further details.

Beispiel:

![cfm-01](assets/cfm-01.png)

Die OSGi-Konfiguration lautet:

<table>
 <tbody>
  <tr>
   <td>Etikett</td>
   <td>OSGi-Konfiguration<br /> </td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><strong>Ressourcentyp</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>Der zu registrierende Ressourcentyp;z. B. <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Referenz-Eigenschaft</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>Der Name der Eigenschaft, die den Verweis auf das Fragment enthält; z. B. <code>fragmentPath</code> oder <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Element(e)-Eigenschaft</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>Der Name der Eigenschaft, die die Namen der zu rendernden Elemente enthält;z. B.<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Varianteneigenschaft</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>Der Name der Eigenschaft, die den Namen der zu rendernden Variante enthält;z. B.<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Für einige Funktionen (z. B. zum Rendern eines Absatzbereichs) müssen Sie einige Konventionen einhalten:

<table>
 <tbody>
  <tr>
   <td>Eigenschaftsname</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Eine Zeichenfolgeneigenschaft, die den Bereich der Absätze definiert, die ausgegeben werden sollen, wenn sie sich im Rendermodus für <em>einzelne Elemente befinden</em>.</p> <p>Format:</p>
    <ul>
     <li><code>1</code> oder <code>1-3</code> oder <code>1-3;6;7-8</code> <code>*-3;5-*</code></li>
     <li>nur ausgewertet, wenn <code>paragraphScope</code> auf <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>Eine Zeichenfolgeneigenschaft, die definiert, wie Absätze ausgegeben werden sollen, wenn sie sich im Rendermodus für <em>einzelne Elemente befinden</em>.</p> <p>Werte:</p>
    <ul>
     <li><code>all</code> : zum Rendern aller Absätze</li>
     <li><code>range</code> : zur Darstellung des durch <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>Eine boolesche Eigenschaft, die definiert, ob Überschriften (z. B. <code>h1</code>, <code>h2</code>oder <code>h3</code>) als Absätze (<code>true</code>) oder nicht gezählt werden (<code>false</code>)</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Dies kann sich in späteren 6,5 Meilensteinen ändern.

## Beispiel {#example}

Ein Beispiel: Sehen Sie sich Folgendes an (bei einer vordefinierten AEM-Instanz):

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

Dies umfasst:

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```

