---
title: Verwenden zielgerichteter Inhalte in Multisites
seo-title: Working with Targeted Content in Multisites
description: Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden
seo-description: If you need to manage targeted content, such as activities, experiences, and offers between your sites, you can take advantage of AEM's built-in multisite support for targeted content
uuid: acb2ffe1-d846-4580-bb69-d5af860796db
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 4dda6a03-d3ad-4e65-8b37-cee030fa4f7f
exl-id: 5e345ffd-4e9c-467f-8ebb-c798eeb61dea
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '2871'
ht-degree: 49%

---

# Verwenden zielgerichteter Inhalte in Multisites{#working-with-targeted-content-in-multisites}

Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden.

>[!NOTE]
>
>Bei der Multisite-Unterstützung für zielgerichtete Inhalte handelt es sich um eine erweiterte Funktion. Damit Sie diese Funktion verwenden können, sollten Sie sich mit [Site-Manager](/help/sites-administering/msm.md) und der [Adobe Target-Integration](/help/sites-administering/target.md) in AEM vertraut machen.

Dieses Dokument beschäftigt sich mit den folgenden Themen:

* Bietet einen kurzen Überblick über AEM Multisite-Unterstützung für zielgerichtete Inhalte.
* Beschreibt einige mögliche Nutzungsszenarien dazu, wie Sie Sites (in einer Marke) verknüpfen können.
* Schrittweise Führung durch ein Beispiel dafür, wie Marketing-Experten diese Funktion nutzen können.
* Detaillierte Anweisungen zur Implementierung der Multisite-Unterstützung für zielgerichtete Inhalte.

Um festzulegen, wie Ihre Sites personalisierte Inhalte teilen, müssen Sie die folgenden Schritte ausführen:

1. [Neues Gebiet erstellen](#creating-new-areas) oder [Erstellen eines neuen Bereichs als Live Copy](#creating-new-areas). Ein Gebiet umfasst alle Aktivitäten, die für eine *area* der Seite, d. h. die Position auf der Seite, auf der die Komponente als Ziel ausgewählt wird. Wenn Sie ein neues Gebiet erstellen, wird ein leeres Gebiet erstellt, während Sie durch die Erstellung eines neuen Gebiets als Live Copy Inhalte über Site-Strukturen hinweg übernehmen können.

1. [Website oder Seite verknüpfen](#linking-sites-to-an-area) in ein Gebiet.

Sie können die Vererbung jederzeit aussetzen oder wiederherstellen. Wenn Sie die Vererbung nicht aussetzen möchten, können Sie auch lokale Erlebnisse erstellen. Standardmäßig verweisen alle Seiten auf das primäre Gebiet, außer es wurde eigens ein anderes Gebiet festgelegt.

## Einführung in die Multisite-Unterstützung für zielgerichtete Inhalte {#introduction-to-multisite-support-for-targeted-content}

Die Multisite-Unterstützung für zielgerichtete Inhalte ist als einsatzbereite Standardfunktion erhältlich und ermöglicht das Pushen von zielgerichteten Inhalten von der mit MSM verwalteten primären Seite an eine lokale Live Copy sowie die lokale und globale Bearbeitung solcher Inhalte.

Diese Funktion wird in einem **Gebiet** verwaltet. Bereiche trennen zielgerichteten Content (Aktivitäten, Erlebnisse und Angebote), der auf verschiedenen Sites eingesetzt wird, und ermöglichen durch einen MSM-basierten Mechanismus das Erstellen und Verwalten der Vererbung zielgerichteter Inhalte sowie der Site-Vererbung. Dadurch wird verhindert, dass Sie zielgerichtete Inhalte in vererbten Sites neu erstellen müssen, wie es in AEM vor 6.2 erforderlich war.

Innerhalb eines Gebiets können nur Aktivitäten, die mit diesem Gebiet verknüpft sind, an Live Copies gepusht werden. Standardmäßig ist das primäre Gebiet ausgewählt. Nachdem Sie weitere Bereiche erstellt haben, können Sie diese mit Ihren Sites oder Seiten verknüpfen, um anzugeben, welche zielgerichteten Inhalte weitergeleitet werden.

Eine Site oder Live Copy verlinkt zu einem Gebiet, das die Aktivitäten enthält, die auf dieser Site oder Live Copy verfügbar sein müssen. Standardmäßig ist die Site oder Live Copy mit dem primären Gebiet verknüpft, es können jedoch auch andere Gebiete zugewiesen werden.

>[!NOTE]
>
>Beachten Sie Folgendes bei der Verwendung der Multisite-Unterstützung für zielgerichtete Inhalte:
>
>* Wenn Sie Rollouts oder Live Copies verwenden, ist eine MSM-Lizenz erforderlich.
>* Wenn Sie die Synchronisierung mit Adobe Target verwenden, ist eine Adobe Target-Lizenz erforderlich.
>

## Anwendungsfälle {#use-cases}

Je nach Anwendungsfall können Sie für zielgerichtete Inhalte auf verschiedene Arten Multisite-Unterstützung einrichten. In diesem Abschnitt wird beschrieben, wie dies theoretisch mit einer Marke funktioniert. Darüber hinaus [Beispiel: Inhalts-Targeting basierend auf Geografie](#example-targeting-content-based-on-geography)können Sie eine reale Anwendung von Targeting-Inhalten auf mehreren Sites sehen.

Zielgerichtete Inhalte werden in so genannte Bereiche eingeschlossen, die den Umfang für Sites oder Seiten definieren. Diese Bereiche werden auf Markenebene definiert. Eine Marke kann mehrere Bereiche enthalten. Bereiche können sich von Marke zu Marke unterscheiden. So kann beispielsweise eine Marke nur das primäre Gebiet enthalten, das für alle Marken gilt, während eine andere Marke hingegen zeitgleich mehrere Gebiete enthält (beispielsweise mit Unterschieden je nach Region). Marken müssen daher nicht die Bereiche zwischen ihnen widerspiegeln.

Dank der Multisite-Unterstützung für zielgerichtete Inhalte können Sie beispielsweise zwei (oder mehr) Sites mit **one** Marken, die eine der folgenden Eigenschaften aufweisen:

* Vollständig *unterschiedliche* zielgerichtete Inhalte: Die Bearbeitung der Inhalte auf einer Site beeinflusst die Inhalte der anderen Site nicht. Sites, die mit verschiedenen Gebieten verknüpft sind, führen Lese- und Schreibaufgaben für getrennt konfigurierte Gebiete aus. Beispiel:

   * Site A verlinkt zu Bereich X
   * Site B verlinkt zu Bereich Y

* Ein *freigegebener* Satz von zielgerichteten Inhalten; die Bearbeitung in einer Site wirkt sich direkt auf beide Sites aus. Sie können dies einrichten, indem Sie beide Sites auf dasselbe Gebiet verweisen. Sites, die sich auf dasselbe Gebiet beziehen, teilen die zielgerichteten Inhalte dieses Gebiets. Beispiel:

   * Site A verlinkt zu Bereich X
   * Site B verweist auf Bereich X

* Bestimmte zielgerichtete Inhalte werden über MSM von einer anderen Site *übernommen*: Die Inhalte können unidirektional von der Quelle an die Live Copy übermittelt werden. Beispiel:

   * Site A verlinkt zu Bereich X
   * Site B ist mit Gebiet Y verknüpft (eine Live Copy des Gebiets X)

Sie können auch **multiple** Marken, die auf einer Site verwendet werden, was komplexer sein könnte als dieses Beispiel.

![chlimage_1-270](assets/chlimage_1-270.png)

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-authoring/technical-multisite-targeted.md).

## Beispiel: Inhalts-Targeting basierend auf geografischen Angaben {#example-targeting-content-based-on-geography}

Durch die Verwendung von Multisite für zielgerichtete Inhalte können Sie Personalisierungsinhalte freigeben, einführen oder isolieren. Um besser zu veranschaulichen, wie diese Funktion verwendet wird, sollten Sie wie im folgenden Szenario steuern, wie zielgerichtete Inhalte basierend auf geografischen Daten bereitgestellt werden:

Es gibt vier Versionen derselben Site, die auf der geografischen Lage basieren:

* Die Site für die **Vereinigten Staaten** befindet sich oben links und dient als primäre Site. In diesem Beispiel ist er im Targeting-Modus geöffnet.
* Die drei übrigen Versionen sind diejenigen für **Kanada**, **Großbritannien** und **Australien**, wobei es sich bei diesen um Live Copies handelt. Diese Sites sind im Vorschaumodus geöffnet.

![chlimage_1-271](assets/chlimage_1-271.png)

Jede Site teilt personalisierte Inhalte in geografischen Regionen:

* Für Kanada wird das gleiche primäre Gebiet wie für die Vereinigten Staaten verwendet.
* Die Site für Großbritannien wurde mit Europa verknüpft und übernimmt die Inhalte des primären europäischen Gebiets.
* Australien verfügt über eigene personalisierte Inhalte, da es sich auf der Südhalbkugel befindet und saisonal bedingte Produkte nicht mit Produkten für die anderen Länder übereinstimmen.

![chlimage_1-272](assets/chlimage_1-272.png)

Für die Nordhalbkugel wurde eine Winteraktivität erstellt, doch der nordamerikanische Marketing-Experte wünscht sich für den Winter ein anderes Bild, das also für die US-Site geändert wird.

![chlimage_1-273](assets/chlimage_1-273.png)

Nach Aktualisierung der Registerkarte ändert sich die kanadische Site in das neue Bild, ohne dass wir etwas unternehmen müssen. Diese Änderung geschieht, da die Site von Kanada sich auf das gleiche primäre Gebiet wie die Site der Vereinigten Staaten bezieht. Auf den Sites für Großbritannien und Australien ändert sich das Bild nicht.

![chlimage_1-274](assets/chlimage_1-274.png)

Der Marketer möchte diese Änderungen in die europäische Region einführen und [Rollout der Live Copy](/help/sites-administering/msm-livecopy.md) durch Tippen oder Klicken **Rollout-Seite**. Nach Aktualisierung der Registerkarte erscheint auf der Site für Großbritannien das neue Bild, da das europäische Gebiet dieses (nach dem Rollout) vom primären Gebiet bezieht.

![chlimage_1-275](assets/chlimage_1-275.png)

Das Bild auf der Site &quot;Australia&quot;bleibt unverändert, was das gewünschte Verhalten ist, da es in Australien Sommer ist und der Marketing-Experte diesen Inhalt nicht ändern möchte. Die Site Australiens ändert sich nicht, da es weder ein Gebiet mit einer anderen Region teilt noch eine Live Copy einer anderen Region ist. Der Marketing-Experte muss sich nie Gedanken darüber machen, dass die zielgerichteten Inhalte der australischen Site überschrieben werden.

Zudem kann für die Site für Großbritannien, deren Gebiet eine Live Copy des primären Gebiets darstellt, der Vererbungsstatus anhand des grünen Indikators neben dem Aktivitätennamen erkannt werden. Wenn eine Aktivität vererbt wurde, können Sie sie nur ändern, wenn Sie die Live Copy aussetzen oder trennen.

Sie können die Vererbung jederzeit aussetzen oder die Vererbung vollständig trennen. Sie können auch immer lokale Erlebnisse hinzufügen, die nur für dieses Erlebnis verfügbar sind, ohne die Vererbung auszusetzen.

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-authoring/technical-multisite-targeted.md).

### Erstellen eines neuen Gebiets bzw. eines neuen Gebiets als Live Copy {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

In AEM haben Sie die Möglichkeit, einen neuen Bereich zu erstellen oder neue Bereiche als Live Copy zu erstellen. Beim Erstellen eines neuen Bereichs werden Aktivitäten und alles, was zu diesen Aktivitäten gehört, wie Angebote, Erlebnisse usw. gruppiert. Sie erstellen einen neuen Bereich, wenn Sie entweder einen völlig eigenen Satz zielgerichteter Inhalte erstellen oder wenn Sie einen Satz zielgerichteter Inhalte freigeben möchten.

Wenn Sie jedoch über MSM eine Vererbung zwischen den beiden Sites eingerichtet haben, sollten Sie die Aktivitäten übernehmen. In diesem Fall erstellen Sie ein neues Gebiet als Live Copy, wobei Y eine Live Copy von X ist und daher alle Aktivitäten übernimmt.

>[!NOTE]
>
>Handelt es sich bei einer Seite um eine Live Copy, verknüpft mit einem Gebiet, das selbst wiederum eine mit dem Gebiet der Seitenvorlage verknüpfte Live Copy ist, werden durch den Standard-Rollout alle folgenden Rollouts der zielgerichteten Inhalte ausgelöst.

In der folgenden Darstellung finden Sie beispielsweise vier Sites, von denen sich zwei ein primäres Gebiet (sowie alle Aktivitäten dieses Gebiets) teilen, eine weitere Site über ein Gebiet verfügt, das eine Live Copy des primären Gebiets ist, sodass die Aktivitäten bei einem Rollout geteilt werden, und die letzte Site völlig eigenständig ist (und somit ein eigenes Aktivitätsgebiet benötigt).

![chlimage_1-276](assets/chlimage_1-276.png)

Um dies in AEM zu erreichen, gehen Sie folgendermaßen vor:

* Site A ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Site A und B teilen Aktivitäten usw.
* Site B ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Site A und B teilen Aktivitäten usw.
* Site C ist mit dem vererbten Gebiet verknüpft, das wiederum eine Live Copy des primären Gebiets ist – erstellen Sie ein neues Gebiet als Live Copy, wenn eine Live Copy erstellt werden soll, die auf dem primären Gebiet beruht. Im Rahmen des Rollouts übernimmt das erbende Gebiet Aktivitäten aus dem primären Gebiet.
* Site D verlinkt zu seinem eigenen isolierten Bereich - Bereich erstellen , in dem Sie einen völlig neuen Bereich erstellen, für den noch keine Aktivitäten definiert sind. Das isolierte Gebiet wird keine Aktivitäten mit anderen Standorten teilen.

## Erstellen neuer Gebiete {#creating-new-areas}

Bereiche können Aktivitäten und Angebote umfassen. Nachdem Sie einen Bereich in einem dieser Bereiche erstellt haben (z. B. Aktivitäten), steht Ihnen auch das Gebiet in dem anderen Bereich zur Verfügung (z. B. Angebote).

>[!NOTE]
>
>Der Standardbereich „primäres Gebiet“ wird standardmäßig ausgeblendet, wenn Sie auf den Namen einer Marke tippen/klicken, **bis** Sie einen anderen Bereich erstellen. Wählen Sie entweder in der **Aktivitäts-** oder der **Angebotskonsole** eine Marke aus, wird Ihnen die **Gebietskonsole** angezeigt.

So erstellen Sie ein neues Gebiet:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf **Gebiet erstellen**.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken Sie auf **Bereich** Symbol und klicken Sie auf **Nächste**.
1. Im **Titel** ein, geben Sie einen Namen für das neue Gebiet ein. Wählen Sie optional Tags aus.
1. Tippen oder klicken Sie auf **Erstellen**.

   AEM leitet Sie zum Markenfenster um, in dem alle erstellten Bereiche aufgelistet werden. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt in der Markenkonsole erstellen.

   ![chlimage_1-278](assets/chlimage_1-278.png)

## Erstellen neuer Gebiete als Live Copies {#creating-areas-as-live-copies}

Gebiete werden als Live Copies erstellt, damit diese über Site-Strukturen hinweg zielgerichtete Inhalte übernehmen können.

So erstellen Sie einen Bereich als Live Copy:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf **Gebiet als Live Copy erstellen**.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Wählen Sie das Gebiet aus, von dem Sie eine Live Copy erstellen möchten, und klicken Sie auf **Weiter**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Geben Sie im Feld **Name** einen Namen für die Live Copy ein. Standardmäßig werden Unterseiten einbezogen. schließen Sie sie aus, indem Sie das Kontrollkästchen **Unterseiten ausschließen** aktivieren.

   ![chlimage_1-281](assets/chlimage_1-281.png)

1. Wählen Sie im Dropdown-Menü **Rollout-Konfigurationen** die entsprechende Konfiguration aus.

   Siehe [Installierte Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations) für Beschreibungen der einzelnen Optionen.

   Weitere Informationen zu Live Copies finden Sie unter [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md).

   >[!NOTE]
   >
   >Wird der Rollout einer Site für eine Live Copy durchgeführt und ist das für die Blueprint-Seite konfigurierte Gebiet auch Blueprint des Gebiets, das für die Live Copy der Seite konfiguriert wurde, löst die LiveAction **personalizationContentRollout** einen synchronen subRollout aus, der Teil der **Standard-Rollout-Konfigurationen** ist.

1. Tippen oder klicken Sie auf **Erstellen**.

   AEM leitet Sie zum Markenfenster um, in dem alle erstellten Bereiche aufgelistet werden. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt im Markenfenster erstellen.

   ![chlimage_1-282](assets/chlimage_1-282.png)

## Verknüpfen von Sites mit Gebieten {#linking-sites-to-an-area}

Gebiete können entweder mit Seiten oder einer Site verknüpft werden. Gebiete werden von allen Unterseiten übernommen, es sei denn, diese Seiten werden durch eine Zuordnung auf einer Unterseite überlagert. Im Allgemeinen erfolgen Verknüpfungen jedoch auf Site-Ebene.

Beim Verknüpfen sind nur die Aktivitäten, Erlebnisse und Angebote aus dem ausgewählten Bereich verfügbar. Dies verhindert eine versehentliche Mischung von unabhängig verwalteten Inhalten. Wird kein weiteres Gebiet konfiguriert, gilt das primäre Gebiet der jeweiligen Marke.

>[!NOTE]
>
>Seiten oder Sites, die auf dasselbe Gebiet verweisen, verwenden *denselben* freigegebenen Satz an Aktivitäten, Erlebnissen und Angeboten. Die Bearbeitung einer Aktivität, eines Erlebnisses oder eines Angebots, die bzw. das von mehreren Sites gemeinsam genutzt werden, wirkt sich auf alle Sites aus.

So verknüpfen Sie eine Site mit einem Gebiet:

1. Navigieren Sie zu der Site (oder Seite), die Sie mit einem Bereich verknüpfen möchten.
1. Wählen Sie die Site oder Seite aus und tippen oder klicken Sie auf **Eigenschaften anzeigen**.
1. Tippen oder klicken Sie auf die Registerkarte **Personalisierung**.
1. Im **Marke** auswählen, wählen Sie die Marke aus, mit der Sie Ihr Gebiet verknüpfen möchten. Nach Auswahl der Marke sind die verfügbaren Bereiche im **Gebiets-Referenz** Menü.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Wählen Sie aus dem Dropdown-Menü **Gebiets-Verweis** das gewünschte Gebiet aus und klicken oder tippen Sie auf **Speichern**.

   ![chlimage_1-284](assets/chlimage_1-284.png)

## Trennen von Live Copy oder Aussetzen der Vererbung zielgerichteter Inhalte {#detaching-live-copy-or-suspending-inheritance-of-targeted-content}

Sie können die Vererbung zielgerichteter Inhalte aussetzen oder deaktivieren. Das Aussetzen oder Trennen der Live Copy erfolgt pro Aktivität. Sie können beispielsweise Erlebnisse in Ihrer Aktivität ändern. Wenn diese Aktivität jedoch weiterhin mit einer geerbten Kopie verknüpft ist, können Sie das Erlebnis oder die Eigenschaften der Aktivität nicht ändern.

Wenn Sie die Live Copy aussetzen, wird die Vererbung vorübergehend unterbrochen. In Zukunft können Sie jedoch die Vererbung wiederherstellen. Wenn Sie die Live Copy trennen, wird die Vererbung dauerhaft unterbrochen.

Die Vererbung zielgerichteter Inhalte lässt sich aussetzen oder deaktivieren, indem der Inhalt in einer Aktivität wiederhergestellt wird. Sollte eine Site oder Seite sich auf ein Gebiet beziehen, das eine Live Copy ist, können Sie den Vererbungsstatus der Aktivität anzeigen.

Eine Aktivität, die Daten von einer anderen Site erbt, weist neben ihrem Namen eine grüne Markierung auf. Eine ausgesetzte Vererbung wird rot markiert und eine lokal erstellte Aktivität hat kein Symbol.

>[!NOTE]
>
>* Sie können Live Copies nur in einer Aktivität aussetzen oder deaktivieren.
>* Live Copies müssen nicht ausgesetzt oder getrennt werden, um eine geerbte Aktivität zu erweitern. Sie können jederzeit **new** lokale Erlebnisse und Angebote für diese Aktivität. Wenn Sie eine vorhandene Aktivität ändern möchten, müssen Sie die Vererbung aussetzen.
>

### Aussetzen der Vererbung {#suspending-inheritance}

So setzen Sie die Vererbung zielgerichteter Inhalte in einer Aktivität aus oder lösen sie aus:

1. Navigieren Sie zu der Seite, auf der Sie die Vererbung trennen oder aussetzen möchten, und tippen oder klicken Sie auf **Targeting** im Modus-Dropdown-Menü.
1. Wenn Ihre Seite mit einem Gebiet verknüpft ist, das eine Live Copy ist, wird der Vererbungsstatus angezeigt. Tippen oder klicken Sie auf **Targeting starten**.
1. Führen Sie einen der folgenden Schritte aus, um eine Aktivität auszusetzen:

   1. Wählen Sie ein Element der Aktivität aus, z. B. die Zielgruppe. AEM zeigt automatisch das Bestätigungsfeld Live Copy aussetzen an. (Sie können die Live Copy aussetzen, indem Sie während des Targeting-Prozesses auf ein beliebiges Element tippen oder klicken.)
   1. Auswählen **Live Copy aussetzen** aus dem Dropdown-Menü in der Symbolleiste.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Tippen oder klicken Sie auf **Aussetzen**, um die Aktivität zu unterbrechen. Ausgesetzte Aktivitäten werden rot markiert.

   ![chlimage_1-286](assets/chlimage_1-286.png)

### Deaktivieren der Vererbung {#breaking-inheritance}

So unterbrechen Sie die Vererbung zielgerichteter Inhalte in einer Aktivität:

1. Navigieren Sie zu der Seite, deren Live Copy Sie vom primären Gebiet trennen möchten, und klicken oder tippen Sie im Modus-Dropdown-Menü auf **Targeting**.
1. Wenn Ihre Seite mit einem Gebiet verknüpft ist, das eine Live Copy ist, wird der Vererbungsstatus angezeigt. Tippen oder klicken Sie auf **Targeting starten**.
1. Wählen Sie aus dem Dropdown-Menü in der Symbolleiste die Option **Live Copy trennen**. AEM bestätigt, dass Sie die Live Copy trennen möchten.
1. Tippen oder klicken **Trennen** , um die Live Copy von der Aktivität zu trennen. Nach dem Trennen wird das Dropdown-Menü zur Vererbung nicht mehr angezeigt. Die Aktivität ist jetzt eine lokale Aktivität.

   ![chlimage_1-287](assets/chlimage_1-287.png)

## Wiederherstellen der Vererbung von zielgerichtetem Content {#restoring-inheritance-of-targeted-content}

Wenn Sie die Vererbung zielgerichteter Inhalte in einer Aktivität ausgesetzt haben, können Sie diese jederzeit wiederherstellen. Wenn Sie die Live Copy jedoch getrennt haben, können Sie die Vererbung nicht wiederherstellen.

So stellen Sie die Vererbung zielgerichteter Inhalte in einer Aktivität wieder her:

1. Navigieren Sie zu der Seite, auf der die Vererbung wiederhergestellt werden soll, und klicken oder tippen Sie im Modus-Dropdown-Menü auf **Targeting**.
1. Tippen oder klicken Sie auf **Targeting starten**.
1. Wählen Sie im Dropdownmenü in der Symbolleiste die Option **Live Copy fortsetzen**.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Tippen oder klicken **Fortsetzen** , um zu bestätigen, dass Sie die Live Copy-Vererbung fortsetzen möchten. Änderungen an der aktuellen Aktivität gehen verloren, wenn Sie die Vererbung fortsetzen.

## Löschen von Gebieten {#deleting-areas}

Wenn Sie einen Bereich löschen, löschen Sie alle Aktivitäten in diesem Bereich. AEM warnt Sie, bevor Sie einen Bereich löschen können. Sollten Sie ein Gebiet löschen, das mit einer Site verknüpft ist, wird die Marke stattdessen automatisch mit dem primären Gebiet verknüpft.

So löschen Sie Gebiete:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf das Symbol neben dem Bereich, den Sie löschen möchten.
1. Tippen oder klicken **Löschen** und bestätigen Sie, dass Sie den Bereich löschen möchten.
