---
title: Komponenten für Inhaltsfragmente
seo-title: Components for Content Fragments
description: AEM Inhaltsfragmente werden als seitenunabhängige Assets erstellt und verwaltet
seo-description: AEM content fragments are created and managed as page-independent assets
uuid: 81a9e0fe-ed45-4880-b36c-4f49e2598389
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: b7777dc5-a867-4799-9e2c-a1f4bb5dd96a
docset: aem65
pagetitle: Components for Content Fragments
exl-id: f2edd9b2-f231-42f3-a25e-428cd1d96c2a
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 67%

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
>Derzeit wird die [Kernkomponente für Inhaltsfragmente](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html) dafür empfohlen. Weitere Informationen finden Sie unter [Entwickeln von Kernkomponenten](https://helpx.adobe.com/de/experience-manager/core-components/using/developing.html).
>
>In diesem Abschnitt wird die ursprüngliche Komponente beschrieben, die zur Verwendung mit Inhaltsfragmenten bereitgestellt wird (**Inhaltsfragment** im **Allgemein** -Gruppe).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Inhaltsfragmente – Konfigurieren von Komponenten für das Rendering](/help/sites-developing/content-fragments-config-components-rendering.md).

Inhaltsfragmente für Adobe Experience Manager (AEM) werden [als seitenunabhängige Assets erstellt und verwaltet](/help/assets/content-fragments/content-fragments.md). Damit können Sie kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten erstellen. [Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden](/help/sites-authoring/content-fragments.md). Sie können auch ein vorhandenes Inhaltsfragment-Asset verwenden, indem Sie es vom [Asset-Browser auf die Seite ziehen](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (wie bei anderen Asset-basierten Komponenten, z. B. der Foundation-Komponente „Image“). Die vorkonfigurierte Inhaltsfragmentkomponente zeigt nur ein [Element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) des referenzierten Inhaltsfragments an. Unter Verwendung des Komponentendialogfelds können Sie das [Element, die Variante und den Bereich der Fragmentabsätze](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) definieren, die auf der Seite angezeigt werden sollen.

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

Nur der Editor der Touch-optimierten Benutzeroberfläche unterstützt Inhaltsfragmentkomponenten, einschließlich der Client-Bibliothek, vollständig:

`cq.authoring.editor.plugin.cfm`

Diese Bibliothek fügt dem Editor spezielle Funktionen für Inhaltsfragmente hinzu. Beispielsweise sind Unterstützung für das Hinzufügen und Konfigurieren von Inhaltsfragmenten auf der Seite, die Möglichkeit, im Asset-Browser nach Inhaltsfragment-Assets zu suchen und für verknüpfte Inhalte im Seitenbereich verfügbar.

### Übergangsinhalte {#in-between-content}

Die **Inhaltsfragmente** Mit der Komponente &quot;t&quot;können Sie zusätzliche Komponenten zwischen den verschiedenen Absätzen der angezeigten [element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment). Grundsätzlich besteht das angezeigte Element aus verschiedenen Absätzen (jeder Absatz ist durch einen Wagenrücklauf gekennzeichnet). Zwischen diesen Absätzen können Sie Inhalte mithilfe anderer Komponenten einfügen.

Aus technischer Sicht wird jeder Absatz des angezeigten Elements in seinem eigenen Parsys ausgeführt, und jede Komponente, die Sie zwischen den Absätzen einfügen, wird (im Verborgenen) im Parsys eingefügt.

Mit anderen Worten, wenn die Instanz der Inhaltsfragmentkomponente aus drei Absätzen besteht, hat die Komponente drei verschiedene Absatzsysteme im Repository. Der gesamte Zwischeninhalt, der zum Inhaltsfragment hinzugefügt wird, befindet sich tatsächlich in diesen ParSys.

Im Repository wird der Zwischeninhalt relativ zu seiner Position innerhalb der gesamten Absatzstruktur gespeichert, d. h. er wird nicht an den tatsächlichen Absatzinhalt angehängt.

Um dies zu veranschaulichen, sollten wir Folgendes berücksichtigen:

* Eine Instanz eines Inhaltsfragments, das aus drei Absätzen besteht
* Und dass einige Inhalte bereits nach dem zweiten Absatz eingefügt wurden

   * Das bedeutet, dass der Inhalt im zweiten parsys gespeichert wird.

Grundsätzlich, wenn sich die Absatzstruktur dieser Instanz ändert (indem die Variante, das Element oder der Bereich der angezeigten Absätze geändert wird), kann sich dies auf den Übergangsinhalt auswirken, der beim Inhalt des Inhaltsfragments angezeigt wird:

* Wird bearbeitet und vor dem zweiten Absatz wird ein weiterer Absatz eingefügt:

   * Der Übergangsinhalt wird nach dem neu erstellten Absatz angezeigt (das zweite Absatzsystem enthält nun den neu erstellten Absatz).

* Wird bearbeitet und der zweite Absatz wird entfernt:

   * Der Übergangsinhalt wird nach dem Absatz angezeigt, der zuvor der dritte war (das zweite Absatzsystem enthält jetzt den vorherigen dritten Absatz).

* Ist so konfiguriert, dass nur der erste Absatz angezeigt wird:

   * Der Zwischeninhalt wird nicht angezeigt (der zweite ParSys wird aufgrund der neuen Konfiguration nicht mehr gerendert).

### Anpassen der Inhaltsfragment-Komponente {#customizing-the-content-fragment-component}

Um die vordefinierte Inhaltsfragmentkomponente als Blueprint für die Erweiterung zu verwenden, müssen Sie den folgenden Vertrag einhalten:

* Verwenden Sie das HTL-Rendering-Skript und das zugehörige POJO erneut, um zu sehen, wie die Zwischeninhaltsfunktion implementiert ist.
* Verwenden Sie den Inhaltsfragmentknoten erneut: `cq:editConfig`

   * Die Listener `afterinsert`/ `afteredit`/ `afterdelete` werden zum Auslösen von JS-Ereignissen verwendet. Diese Ereignisse werden in der Client-Bibliothek `cq.authoring.editor.plugin.cfm` behandelt, um den zugehörigen Inhalt im Seitenbereich anzuzeigen.
   * Die `cq:dropTargets` sind so konfiguriert, dass das Ziehen von Inhaltsfragment-Assets unterstützt wird.
   * `cq:inplaceEditing` wurde konfiguriert, um das Erstellen eines Inhaltsfragments im Seiteneditor zu unterstützen. Der Editor für die Bearbeitung im Kontext für Fragmente ist in der Client-Bibliothek `cq.authoring.editor.plugin.cfm` definiert und ermöglicht eine schnelle Verknüpfung zum Öffnen [des aktuellen Elements/der aktuellen Variante](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) im [Fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md).

### Asset-Neuschreibung vor Rendern {#asset-rewriting-before-rendering}

Die Inhaltsfragmentverwaltung verwendet einen internen Renderprozess, um die endgültige HTML-Ausgabe für eine Seite zu generieren. Dies wird intern von der Inhaltsfragment-Komponente, aber auch vom Hintergrundprozess verwendet, der referenzierte Fragmente auf referenzierenden Seiten aktualisiert.

Intern wird der Sling Rewriter für dieses Rendering verwendet. Die entsprechende Konfiguration kann unter `/libs/dam/config/rewriter/cfm` gefunden und bei Bedarf angepasst werden. Weitere Informationen finden Sie unter [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html).

>[!CAUTION]
>
>Wenn Sie die Konfiguration des Rewriters anpassen/überlagern:
>
>* `/libs/dam/config/rewriter/cfm`
>
>dann **muss** der `serializerType` aktualisiert werden auf:
>
>* `serializerType="html5-serializer"`

Die Standardkonfiguration verwendet folgende Transformatoren:

* `transformer-cfm-payloadfilter` – nur für das Abrufen des `body`-Teils (`<body>...</body>`) der HTML des Fragments

* `transformer-cfm-parfilter` – filtert unerwünschte Absätze heraus, wenn ein Absatzbereich angegeben wurde (wie bei der Inhaltsfragmentkomponente möglich)
* `transformer-cfm-assetprocessor` – wird intern zum Abrufen einer Liste der Assets verwendet, die im Fragment eingebettet sind

Der Rendervorgang wird über [`com.adobe.cq.dam.cfm.content.FragmentRenderService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html) verfügbar gemacht und kann bei Bedarf (zum Beispiel) von benutzerdefinierten Komponenten genutzt werden.
