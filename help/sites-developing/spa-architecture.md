---
title: Entwickeln von SPAs für AEM
seo-title: Entwickeln von SPAs für AEM
description: Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn ein Front-End-Entwickler aufgefordert wird, ein SPA für AEM zu entwickeln, und gibt einen Überblick über die Architektur von AEM in Bezug auf SPAs, die bei der Bereitstellung eines entwickelten SPA auf AEM zu beachten sind.
seo-description: Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn ein Front-End-Entwickler aufgefordert wird, ein SPA für AEM zu entwickeln, und gibt einen Überblick über die Architektur von AEM in Bezug auf SPAs, die bei der Bereitstellung eines entwickelten SPA auf AEM zu beachten sind.
uuid: 6673a041-c557-4968-ae54-4cd5b9f56251
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 9584392a-d8a3-45a4-9cdf-fd211c8e6091
docset: aem65
translation-type: tm+mt
source-git-commit: 590dc4464182d4baf8293e7bb0774ce92971c0af

---


# Entwickeln von SPAs für AEM{#developing-spas-for-aem}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA-Frameworks erstellen und Autoren möchten Inhalte in AEM nahtlos für eine Site bearbeiten, die mit diesen Frameworks erstellt wurde.

Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn ein Front-End-Entwickler aufgefordert wird, ein SPA für AEM zu entwickeln, und einen Überblick über die Architektur von AEM in Bezug auf die Bereitstellung von SPAs auf AEM.

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

## SPA-Entwicklungsprinzipien für AEM {#spa-development-principles-for-aem}

Beim Entwickeln von Einzelseitenanwendungen in AEM wird davon ausgegangen, dass der Front-End-Entwickler beim Erstellen einer SPA die üblichen Best Practices beachtet. Wenn Sie als Front-End-Entwickler diese allgemeinen Best Practices sowie nur wenige AEM-spezifische Prinzipien befolgen, ist Ihr SPA mit [AEM und seinen Funktionen](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa)zum Erstellen von Inhalten kompatibel.

* **[Portabilität](/help/sites-developing/spa-architecture.md#portability)-**Wie bei allen Komponenten sollten die Komponenten so gebaut sein, dass sie möglichst tragbar sind. Die SPA sollte mit tragbaren und wiederverwendbaren Komponenten erstellt werden.
* **[AEM Drives-Site-Struktur](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)**- Der Front-End-Entwickler erstellt Komponenten und besitzt deren interne Struktur. Bei der Definition der Inhaltsstruktur der Site ist AEM jedoch darauf angewiesen.
* **[Dynamisches Rendering](/help/sites-developing/spa-architecture.md#dynamic-rendering)**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **[Dynamisches Routing](#dynamic-routing)-**Das SPA ist für das Routing verantwortlich, und AEM überwacht es und ruft es ab. Jedes Routing sollte ebenfalls dynamisch sein.

Wenn Sie diese Prinzipien bei der Entwicklung Ihrer SPA beachten, ist diese so flexibel und so flexibel wie möglich, während alle unterstützten AEM-Authoring-Funktionen aktiviert werden.

Wenn Sie keine AEM-Authoring-Funktionen unterstützen müssen, müssen Sie möglicherweise ein anderes [SPA-Designmodell](/help/sites-developing/spa-architecture.md#spa-design-models)in Betracht ziehen.

### Portabilität {#portability}

Wie bei der Entwicklung von Komponenten sollten Ihre Komponenten so gestaltet sein, dass ihre Portabilität maximiert wird. Alle Muster, die gegen die Übertragbarkeit oder Wiederverwendbarkeit der Komponenten funktionieren, sollten vermieden werden, um Kompatibilität, Flexibilität und Wartbarkeit in Zukunft sicherzustellen.

Die resultierende SPA sollte mit hochtragbaren und wiederverwendbaren Komponenten gebaut werden.

### AEM Drives-Site-Struktur {#aem-drives-site-structure}

Der Front-End-Entwickler muss sich selbst als verantwortlich für die Erstellung einer Bibliothek mit SPA-Komponenten betrachten, die zum Erstellen der App verwendet werden. Der Front-End-Entwickler hat die vollständige Kontrolle über die interne Struktur der Komponenten. [AEM besitzt jedoch jederzeit die Struktur der Site.](/help/sites-developing/spa-overview.md)

Das bedeutet, dass der Front-End-Entwickler Kundeninhalte vor oder nach dem Einstiegspunkt der Komponenten hinzufügen und auch Drittanbieter-Aufrufe innerhalb der Komponente durchführen kann. Der Front-End-Entwickler hat jedoch nicht die volle Kontrolle darüber, wie die Komponenten verschachteln.

### Dynamisches Rendering {#dynamic-rendering}

Die SPA sollte nur auf der dynamischen Wiedergabe von Inhalten basieren. Dies ist die Standarderwartung, bei der AEM alle untergeordneten Elemente der Inhaltsstruktur abruft und rendert. [](/help/sites-developing/spa-architecture.md#portability)

Jedes explizite Rendering, das auf bestimmte Inhalte verweist, gilt als statisches Rendering und ist mit den Inhaltserstellungsfunktionen von AEM nicht kompatibel. Dies widerspricht auch dem Grundsatz der [Übertragbarkeit](/help/sites-developing/spa-architecture.md#portability).

### Dynamisches Routing {#dynamic-routing}

Wie beim Rendering sollte auch das gesamte Routing dynamisch sein. In AEM sollte [die SPA stets Eigentümer des Routings](/help/sites-developing/spa-routing.md) sein, und AEM überwacht es und ruft Inhalte auf Grundlage dieses Inhalts ab.

Jedes statische Routing verstößt gegen das [Prinzip der Portabilität](/help/sites-developing/spa-architecture.md#portability) und schränkt den Autor ein, da es nicht mit Inhaltserstellungsfunktionen von AEM kompatibel ist. Bei statischem Routing muss der Autor beispielsweise den Front-End-Entwickler bitten, eine Route zu ändern oder eine Seite zu ändern.

## AEM-Projektarchetyp {#aem-project-archetype}

Jedes AEM-Projekt sollte den [AEM-Projektarchiv](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)nutzen, der SPA-Projekte mit React oder Angular unterstützt und das SPA-SDK nutzt.

## SPA-Designmodelle {#spa-design-models}

Wenn die [Prinzipien der Entwicklung von SPAs in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) befolgt werden, funktioniert Ihre SPA mit allen unterstützten AEM-Inhaltserstellungsfunktionen. [](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)

Es kann jedoch Fälle geben, in denen dies nicht ganz notwendig ist. Die folgende Tabelle gibt einen Überblick über die verschiedenen Designmodelle, ihre Vor- und Nachteile.

<table>
 <tbody>
  <tr>
   <th><strong>Designmodell<br /> </strong></th>
   <th><strong>Vorteile</strong></th>
   <th><strong>Nachteile</strong></th>
  </tr>
  <tr>
   <td>AEM wird als kopfloses CMS ohne Verwendung des <a href="/help/sites-developing/spa-reference-materials.md">SPA Editor SDK-Frameworks verwendet.</a></td>
   <td>Der Frontend-Entwickler hat die vollständige Kontrolle über die App.</td>
   <td><p>Autoren von Inhalten können das Authoring-Erlebnis von AEM nicht nutzen.</p> <p>Der Code ist weder portabel noch wiederverwendbar, wenn er statische Referenzen oder Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig. Daher muss der Front-End-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Der Front-End-Entwickler verwendet das SPA Editor SDK Framework, öffnet jedoch nur einige Bereiche für den Inhaltsersteller.</td>
   <td>Der Entwickler behält die Kontrolle über die App, indem er nur das Authoring in eingeschränkten Bereichen der App aktiviert.</td>
   <td><p>Autoren von Inhalten sind auf eine begrenzte Anzahl von AEM-Inhaltserstellungs-Erlebnissen beschränkt.</p> <p>Der Code kann weder portabel noch wiederverwendbar sein, wenn er statische Referenzen oder Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig. Daher muss der Front-End-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Das Projekt nutzt das SPA Editor SDK vollständig, und die Frontend-Komponenten werden als Bibliothek entwickelt und die Inhaltsstruktur der App wird an AEM übertragen.</td>
   <td><p>Die App ist wiederverwendbar und portabel.</p> <p>Der Autor des Inhalts kann die App mit der Inhaltserstellung in AEM bearbeiten.<br /> </p> <p>Die SPA ist mit dem Vorlageneditor kompatibel.</p> </td>
   <td><p>Der Entwickler hat keine Kontrolle über die Struktur der App und den Teil des Inhalts, der an AEM delegiert wird.</p> <p>Der Entwickler kann weiterhin Bereiche der App für Inhalte reservieren, die nicht mit AEM erstellt werden sollen.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Obwohl alle Modelle in AEM unterstützt werden, können die Inhaltsersteller nur durch Implementierung der dritten Version (und damit gemäß den empfohlenen [SPA-Entwicklungsprinzipien in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)) mit dem Inhalt der SPA in AEM interagieren und ihn wie gewohnt bearbeiten.
>[](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)

## Migrieren vorhandener SPAs zu AEM {#migrating-existing-spas-to-aem}

Wenn Ihre SPA den [SPA-Entwicklungsgrundsätzen für AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)folgt, funktioniert Ihre SPA in AEM und kann mit dem AEM SPA Editor bearbeitet werden.

Führen Sie die folgenden Schritte aus, um Ihre vorhandene SPA für die Verwendung mit AEM bereitzustellen.

1. **Machen Sie Ihre JS-Komponenten modular.**

   Machen Sie sie in beliebiger Reihenfolge, Position und Größe gerendert.
1. **Verwenden Sie die von unserem SDK bereitgestellten Container, um Ihre Komponenten auf dem Bildschirm zu platzieren.**

   AEM bietet eine Seite- und Absatzsystemkomponente, die Sie verwenden können.
1. **Erstellen Sie eine AEM-Komponente für jede JS-Komponente.**

   Die AEM-Komponenten definieren das Dialogfeld und die JSON-Ausgabe.

## Anweisungen für Front-End-Entwickler {#instructions-for-front-end-developers}

Die wichtigste Aufgabe bei der Erstellung eines SPA für AEM durch einen Front-End-Entwickler besteht darin, die Komponenten und ihre JSON-Modelle zu vereinbaren.

Im Folgenden werden die Schritte erläutert, die ein Front-End-Entwickler bei der Entwicklung einer SPA für AEM ausführen muss.

1. **Einigung über Komponenten und ihr JSON-Modell**

   Front-End-Entwickler und Back-End-AEM-Entwickler müssen sich darauf einigen, welche Komponenten erforderlich sind und ein Modell, damit eine direkte Übereinstimmung von SPA-Komponenten mit den Back-End-Komponenten besteht.

   AEM-Komponenten sind weiterhin erforderlich, um Bearbeitungsdialogfelder bereitzustellen und das Komponentenmodell zu exportieren.

1. **In React-Komponenten greifen Sie über`this.props.cqModel`**

   Sobald Komponenten vereinbart und das JSON-Modell installiert ist, kann der Front-End-Entwickler die SPA entwickeln und einfach über `this.props.cqModel`das JSON-Modell zugreifen.

1. **Implementieren der`render()`Methode der Komponente**

   Der Front-End-Entwickler implementiert die `render()` Methode nach Bedarf und kann die Felder der `cqModel` Eigenschaft verwenden. Dadurch werden das DOM und die HTML-Fragmente ausgegeben, die in die Seite eingefügt werden. Dies ist die Standardmethode zum Erstellen einer App in React.

1. **Ordnen Sie die Komponente dem AEM-Ressourcentyp zu`MapTo()`**

   Die Zuordnung speichert Komponentenklassen und wird intern von der bereitgestellten `Container` Komponente zum Abrufen und dynamischen Instanziieren von Komponenten basierend auf dem angegebenen Ressourcentyp verwendet.

   Dies dient als &quot;Kleber&quot;zwischen Front- und Back-End, sodass Editor weiß, zu welchen Komponenten die Reaktionskomponenten passen.

   Die `Page` und `ResponsiveGrid` sind gute Beispiele für Klassen, die die Basis erweitern `Container`.

1. **Definieren Sie den`EditConfig`Parameter der Komponente als`MapTo()`**

   Dieser Parameter ist erforderlich, um dem Editor mitzuteilen, wie die Komponente benannt werden soll, solange at noch nicht gerendert ist oder über keinen zu rendernden Inhalt verfügt.

1. **Erweitern der bereitgestellten`Container`Klasse für Seiten und Container**

   Seiten und Absatzsysteme sollten diese Klasse erweitern, damit die Übertragung auf innere Komponenten erwartungsgemäß funktioniert.

1. **Implementieren Sie eine Routing-Lösung, die die HTML5`History`-API verwendet.**

   Wenn die Funktion `ModelRouter` aktiviert ist, löst der Aufruf der Funktionen `pushState` und `replaceState` eine Anforderung aus, ein fehlendes Fragment des Modells abzurufen `PageModelManager` .

   Die aktuelle Version der `ModelRouter` einzigen Version unterstützt die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling Model-Einstiegspunkten zeigen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

   Das `ModelRouter` kann deaktiviert oder so konfiguriert werden, dass eine Liste von regulären Ausdrücken ignoriert wird.

## AEM-Agnostik {#aem-agnostic}

Diese Codeblöcke veranschaulichen, wie Ihre React- und Angular-Komponenten keine Adobe- oder AEM-spezifischen Elemente benötigen.

* Alles, was sich in der JavaScript-Komponente befindet, ist AEM-agnostic.
* Was jedoch für AEM spezifisch ist, ist, dass die JS-Komponente mit dem MapTo-Helfer einer AEM-Komponente zugeordnet werden muss.

![screen_shot_2018-12-11at144019](assets/screen_shot_2018-12-11at144019.png)

Der `MapTo` Helfer ist der &quot;Kleber&quot;, der eine Übereinstimmung zwischen Back-End- und Front-End-Komponenten ermöglicht:

* Er teilt dem JS-Container (oder dem JS-Absatzsystem) mit, welche JS-Komponente für die Wiedergabe der einzelnen Komponenten, die im JSON vorhanden sind, verantwortlich ist.
* Es wird ein HTML-Datenattribut zu dem HTML-Code hinzugefügt, den die JS-Komponente wiedergibt, damit der SPA-Editor weiß, welches Dialogfeld dem Autor beim Bearbeiten der Komponente angezeigt werden soll.

Weitere Informationen zum Verwenden `MapTo` und Erstellen von SPAs für AEM im Allgemeinen finden Sie im Handbuch &quot;Erste Schritte&quot;für Ihr ausgewähltes Framework.

* [Erste Schritte mit SPAs in AEM - React](/help/sites-developing/spa-getting-started-react.md)
* [Erste Schritte mit SPAs in AEM - Angular](/help/sites-developing/spa-getting-started-angular.md)

## AEM Architecture and SPAs {#aem-architecture-and-spas}

Die allgemeine Architektur von AEM einschließlich der Entwicklungs-, Authoring- und Veröffentlichungsarchitektur ändert sich nicht, wenn SPAs verwendet werden. Es ist jedoch hilfreich zu verstehen, wie die SPA-Entwicklung in diese Architektur passt.

![screen_shot_2018-12-11at145348](assets/screen_shot_2018-12-11at145348.png)

* **Umgebung erstellen**

   Hier werden die Quelle für die SPA-Anwendungsquelle und die Komponentenquelle ausgecheckt.

   * Der NPM clientlib Generator erstellt eine Client-Bibliothek aus dem SPA-Projekt.
   * Diese Bibliothek wird von Maven entnommen und vom Maven Build-Plugin zusammen mit der Komponente für den AEM Author bereitgestellt.

* **AEM Author**

   Inhalte werden auf dem AEM-Autor erstellt, einschließlich Authoring-SPAs.

   Wenn eine SPA mit dem SPA-Editor auf der Authoring-Umgebung bearbeitet wird:

   1. Die SPA fordert den äußeren HTML-Code an.
   1. Das CSS wird geladen.
   1. Das Javascript der SPA-Anwendung wird geladen.
   1. Wenn die SPA-Anwendung ausgeführt wird, wird die JSON angefordert, sodass die App das DOM der Seite einschließlich der `cq-data` Attribute erstellen kann.
   1. Diese `cq-data` Attribute ermöglichen es dem Editor, zusätzliche Seiteninformationen zu laden, damit er weiß, welche Bearbeitungskonfigurationen für die Komponenten verfügbar sind.

* **AEM Publish**

   Hier werden die erstellten Inhalte und kompilierten Bibliotheken einschließlich SPA-Anwendungsartefakten, clientlibs und Komponenten für den öffentlichen Gebrauch veröffentlicht.

* **Dispatcher/CDN**

   Der Dispatcher dient als Zwischenspeicherebene von AEM für Besucher der Site.

   * Anforderungen werden ähnlich wie im AEM-Autor verarbeitet, es gibt jedoch keine Anforderung der Seiteninformationen, da dies nur vom Editor benötigt wird.
   * JavaScript, CSS, JSON und HTML werden zwischengespeichert, wodurch die Seite für einen schnellen Versand optimiert wird.

>[!NOTE]
>
>Innerhalb von AEM müssen keine Javascript-Buildmechanismen ausgeführt oder das Javascript selbst ausgeführt werden. AEM hostet nur die kompilierten Artefakte aus der SPA-Anwendung.

## Nächste Schritte {#next-steps}

Eine Übersicht darüber, wie eine einfache SPA in AEM strukturiert ist und wie sie funktioniert, finden Sie im Handbuch &quot;Erste Schritte&quot;für [React](/help/sites-developing/spa-getting-started-react.md) und [Angular](/help/sites-developing/spa-getting-started-angular.md).

Eine schrittweise Anleitung zum Erstellen Ihrer eigenen SPA finden Sie im Lernprogramm [Erste Schritte mit dem AEM SPA Editor - WKND Ereignisses](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Weitere Informationen zum dynamischen Modell zur Komponentenzuordnung und dazu, wie es in AEM in SPAs funktioniert, finden Sie im Artikel [Dynamisches Modell zur Komponentenzuordnung für SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Wenn Sie SPAs in AEM für ein anderes Framework als &quot;React&quot;oder &quot;Angular&quot;implementieren möchten oder einfach einen tiefen Einblick in die Funktionsweise des SPA-SDK für AEM erhalten möchten, lesen Sie den Artikel [SPA Blueprint](/help/sites-developing/spa-blueprint.md) .
