---
title: Komponenten für Inhaltsfragmente
description: Adobe Experience Manager (AEM)-Inhaltsfragmente werden als seitenunabhängige Assets erstellt und verwaltet
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
pagetitle: Components for Content Fragments
exl-id: f2edd9b2-f231-42f3-a25e-428cd1d96c2a
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 62%

---

# Komponenten für Inhaltsfragmente{#components-for-content-fragments}

## Komponenten für die Fragmentbearbeitung {#components-for-fragment-authoring}

>[!CAUTION]
>
>Es wird nicht empfohlen, die im Fragmenteditor tatsächlich verwendeten Komponenten zu erweitern oder zu ändern, da sie sich noch ändern können.

Siehe [Client-seitige API für die Inhaltsfragmentverwaltung](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side).

## Komponenten für die Seitenbearbeitung {#components-for-page-authoring}

>[!CAUTION]
>
>Derzeit wird die [Kernkomponente für Inhaltsfragmente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) dafür empfohlen. Weitere Informationen finden Sie unter [Entwickeln von Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html?lang=de).
>
>In diesem Abschnitt wird die ursprüngliche Komponente beschrieben, die zur Verwendung mit Inhaltsfragmenten bereitgestellt wird (**Inhaltsfragment** in der Gruppe **Allgemein**).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Inhaltsfragmente – Konfigurieren von Komponenten für das Rendering](/help/sites-developing/content-fragments-config-components-rendering.md).

Inhaltsfragmente für Adobe Experience Manager (AEM) werden [als seitenunabhängige Assets erstellt und verwaltet](/help/assets/content-fragments/content-fragments.md). Sie ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen. [Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden](/help/sites-authoring/content-fragments.md). Sie können auch ein vorhandenes Inhaltsfragment-Asset verwenden, indem Sie [Ziehen des Assets aus dem Asset-Browser auf die Seite](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (wie bei anderen Asset-basierten Komponenten, z. B. der Foundation-Komponente Bild). Die vorkonfigurierte Inhaltsfragmentkomponente zeigt nur ein [Element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) des referenzierten Inhaltsfragments an. Unter Verwendung des Komponentendialogfelds können Sie das [Element, die Variante und den Bereich der Fragmentabsätze](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) definieren, die auf der Seite angezeigt werden sollen.

>[!NOTE]
>
>Diese Inhaltsfragment-Komponente wurde in AEM 6.2 als erweiterte Version der nicht mehr unterstützten Artikelkomponente eingeführt.

>[!NOTE]
>
>Inhaltsfragmente werden in der klassischen Benutzeroberfläche nicht unterstützt.

### Definition {#definition}

Die **Inhaltsfragment** komponente wird verwendet, um einen Verweis auf ein Inhaltsfragment-Asset zu halten (effektiv erweiterte Text-Assets). Der Ressourcentyp für das Inhaltsfragment lautet:

`dam/cfm/components/contentfragment/contentfragment`

Die Referenz ist in der Eigenschaft definiert:

`fileReference`

Nur der Editor der Touch-optimierten Benutzeroberfläche unterstützt Inhaltsfragmentkomponenten, die die Client-Bibliothek enthalten, vollständig:

`cq.authoring.editor.plugin.cfm`

Diese Bibliothek fügt dem Editor spezielle Funktionen für Inhaltsfragmente hinzu. Beispielsweise ist Unterstützung für das Hinzufügen und Konfigurieren von Inhaltsfragmenten auf der Seite, die Möglichkeit, im Asset-Browser nach Inhaltsfragment-Assets zu suchen und für verknüpfte Inhalte im Seitenbereich verfügbar.

### Übergangsinhalte {#in-between-content}

Mit der **Inhaltsfragmentkomponente** können Sie zusätzliche Komponenten zwischen den verschiedenen Absätzen des angezeigten [Elements](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) einfügen. Grundsätzlich besteht das angezeigte Element aus verschiedenen Absätzen (jeder Absatz ist durch einen Wagenrücklauf gekennzeichnet). Zwischen diesen Absätzen können Sie Inhalte mithilfe anderer Komponenten einfügen.

Aus technischer Sicht lebt jeder Absatz des angezeigten Elements in seinem eigenen Parsys, und jede Komponente, die Sie zwischen den Absätzen einfügen, wird (im Hintergrund) in das Parsys eingefügt.

Anders ausgedrückt: Wenn die Instanz der Inhaltsfragmentkomponente aus drei Absätzen besteht, enthält die Komponente drei verschiedene Absatzsysteme im Repository. Der gesamte Zwischeninhalt, der zum Inhaltsfragment hinzugefügt wird, befindet sich tatsächlich in diesen ParSys.

Im Repository wird der Zwischeninhalt relativ zu seiner Position innerhalb der übergeordneten Absatzstruktur gespeichert, d. h. er wird nicht an den tatsächlichen Absatzinhalt angehängt.

Um dies zu veranschaulichen, beachten Sie, dass Sie Folgendes haben:

* Eine Instanz eines Inhaltsfragments, das aus drei Absätzen besteht
* Und dass einige Inhalte bereits nach dem zweiten Absatz eingefügt wurden

   * Das bedeutet, dass der Inhalt im zweiten parsys gespeichert wird.

Grundsätzlich, wenn sich die Absatzstruktur dieser Instanz ändert (indem die Variante, das Element oder der Bereich der angezeigten Absätze geändert wird), kann sich dies auf den Übergangsinhalt auswirken, der beim Inhalt des Inhaltsfragments angezeigt wird:

* Wird bearbeitet und vor dem zweiten Absatz wird ein weiterer Absatz eingefügt:

   * Der Zwischeninhalt wird nach dem neu erstellten Absatz angezeigt (der zweite Absatzsystem enthält jetzt den neu erstellten Absatz).

* Wird bearbeitet und der zweite Absatz wird entfernt:

   * Der Übergangsinhalt wird nach dem Absatz angezeigt, der zuvor der dritte war (der zweite Absatzsystem enthält jetzt den vorherigen dritten Absatz).

* Ist so konfiguriert, dass nur der erste Absatz angezeigt wird:

   * Der Zwischeninhalt wird nicht angezeigt (das zweite ParSys wird aufgrund der neuen Konfiguration nicht mehr gerendert).

### Anpassen der Inhaltsfragmentkomponente {#customizing-the-content-fragment-component}

Um die vordefinierte Inhaltsfragmentkomponente als Blueprint für die Erweiterung zu verwenden, müssen Sie folgenden Vertrag einhalten:

* Verwenden Sie das HTL-Rendering-Skript und das zugehörige POJO erneut, damit Sie sehen können, wie die Zwischeninhaltsfunktion implementiert ist.
* Verwenden Sie den Inhaltsfragmentknoten erneut: `cq:editConfig`

   * Die Listener `afterinsert`/ `afteredit`/ `afterdelete` werden zum Auslösen von JS-Ereignissen verwendet. Diese Ereignisse werden im `cq.authoring.editor.plugin.cfm` Client-Bibliothek, um den zugehörigen Inhalt im Seitenbereich anzuzeigen.
   * Die `cq:dropTargets` sind so konfiguriert, dass das Ziehen von Inhaltsfragment-Assets unterstützt wird.
   * `cq:inplaceEditing` wurde konfiguriert, um das Erstellen eines Inhaltsfragments im Seiteneditor zu unterstützen. Der Editor für die Bearbeitung im Kontext für Fragmente ist in der Client-Bibliothek `cq.authoring.editor.plugin.cfm` definiert und ermöglicht eine schnelle Verknüpfung zum Öffnen [des aktuellen Elements/der aktuellen Variante](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) im [Fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md).

### Neuschreibung eines Assets vor dem Rendern {#asset-rewriting-before-rendering}

Die Inhaltsfragmentverwaltung verwendet einen internen Renderprozess, um die endgültige HTML-Ausgabe für eine Seite zu generieren. Dies wird intern von der Inhaltsfragmentkomponente, aber auch vom Hintergrundprozess verwendet, der referenzierte Fragmente auf referenzierenden Seiten aktualisiert.

Intern wird der Sling Rewriter für dieses Rendering verwendet. Die entsprechende Konfiguration finden Sie unter `/libs/dam/config/rewriter/cfm` und bei Bedarf angepasst werden können. Weitere Informationen finden Sie unter [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html).

>[!CAUTION]
>
>Wenn Sie die Konfiguration des Rewriters anpassen/überlagern:
>
>* `/libs/dam/config/rewriter/cfm`
>
>Dann die `serializerType` **must** aktualisiert werden, um
>
>* `serializerType="html5-serializer"`

Die Standardkonfiguration verwendet folgende Transformatoren:

* `transformer-cfm-payloadfilter` – nur für das Abrufen des `body`-Teils (`<body>...</body>`) der HTML des Fragments

* `transformer-cfm-parfilter` – filtert unerwünschte Absätze heraus, wenn ein Absatzbereich angegeben wurde (wie bei der Inhaltsfragmentkomponente möglich)
* `transformer-cfm-assetprocessor` – wird intern zum Abrufen einer Liste der Assets verwendet, die im Fragment eingebettet sind

Der Rendering-Prozess wird über [`com.adobe.cq.dam.cfm.content.FragmentRenderService`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html) und kann bei Bedarf (z. B.) von benutzerdefinierten Komponenten verwendet werden.
