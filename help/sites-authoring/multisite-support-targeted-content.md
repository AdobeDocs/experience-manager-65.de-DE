---
title: Verwenden zielgerichteter Inhalte in Multisites
seo-title: Verwenden zielgerichteter Inhalte in Multisites
description: Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden
seo-description: Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden
uuid: acb2ffe1-d846-4580-bb69-d5af860796db
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 4dda6a03-d3ad-4e65-8b37-cee030fa4f7f
exl-id: 5e345ffd-4e9c-467f-8ebb-c798eeb61dea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2906'
ht-degree: 100%

---

# Verwenden zielgerichteter Inhalte in Multisites{#working-with-targeted-content-in-multisites}

Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden.

>[!NOTE]
>
>Bei der Multisite-Unterstützung für zielgerichtete Inhalte handelt es sich um eine erweiterte Funktion. Damit Sie diese Funktion verwenden können, sollten Sie sich mit [Site-Manager](/help/sites-administering/msm.md) und der [Adobe Target-Integration](/help/sites-administering/target.md) in AEM vertraut machen.

In diesem Dokument wird Folgendes beschrieben:

* Kurze Übersicht über die Multisite-Unterstützung für zielgerichtete Inhalte von AEM.
* Darstellung einiger möglicher Anwendungsfälle zur Verknüpfung von Sites (einer Marke).
* Schrittweise Führung durch ein Beispiel dafür, wie Marketing-Experten diese Funktion nutzen können.
* Detaillierte Anweisungen dazu, wie die Multisite-Unterstützung für zielgerichtete Inhalte integriert wird.

Gehen Sie wie folgt vor, um die Anzeige personalisierter Inhalte auf Ihren Sites einzurichten:

1. [Erstellen Sie ein neues Gebiet](#creating-new-areas) oder [erstellen Sie ein neues Gebiet als Live Copy](#creating-new-areas). Ein Gebiet enthält alle Aktivitäten, die für ein *Gebiet* der Seite verfügbar sind. Es handelt sich bei dem Gebiet um den Ort auf der Seite, auf der die Targeting-Komponente platziert wurde. Durch Erstellung eines neuen Gebiets entsteht ein leeres Gebiet, bei der Erstellung eines neuen Gebiets als Live Copy hingegen können Inhalte über Site-Strukturen hinweg übernommen werden.

1. [Verknüpfen Sie Ihre Website oder Seite](#linking-sites-to-an-area) mit einem Gebiet.

Sie können die Vererbung dabei jederzeit aussetzen oder wiederherstellen. Zudem können Sie, wenn die Vererbung nicht ausgesetzt werden soll, zusätzlich lokale Erlebnisse erstellen. Standardmäßig verweisen alle Seiten auf das primäre Gebiet, außer es wurde eigens ein anderes Gebiet festgelegt.

## Einführung in die Multisite-Unterstützung für zielgerichtete Inhalte  {#introduction-to-multisite-support-for-targeted-content}

Die Multisite-Unterstützung für zielgerichtete Inhalte ist als einsatzbereite Standardfunktion erhältlich und ermöglicht das Pushen von zielgerichteten Inhalten von der mit MSM verwalteten primären Seite an eine lokale Live Copy sowie die lokale und globale Bearbeitung solcher Inhalte.

Diese Funktion wird in einem **Gebiet** verwaltet. Gebiete trennen auf verschiedenen Sites eingesetzte zielgerichtete Inhalte (Aktivitäten, Erlebnisse und Angebote) voneinander und ermöglichen durch einen MSM-basierten Mechanismus das Erstellen und Verwalten der Vererbung zielgerichteter Inhalte sowie der Site-Vererbung. So wird verhindert, dass Sie zielgerichtete Inhalte in vererbten Seiten erneut erstellen müssen, wie das in AEM vor Version 6.2 der Fall war.

Innerhalb eines Gebiets können nur Aktivitäten, die mit diesem Gebiet verknüpft sind, an Live Copys gepusht werden. Standardmäßig ist das primäre Gebiet ausgewählt. Nach der Erstellung weiterer Gebiete lassen sich diese mit Ihren Sites oder Seiten verknüpfen, wodurch bestimmt wird, welche zielgerichteten Inhalte gepusht werden.

Eine Site oder Live Copy verweist auf ein Gebiet, das die Aktivitäten enthält, die auf dieser Site oder Live Copy zur Verfügung gestellt werden müssen. Standardmäßig ist die Site oder Live Copy mit dem Mastergebiet verknüpft, es können jedoch auch andere Gebiete zugewiesen werden.

>[!NOTE]
>
>Beachten Sie bei der Arbeit mit Multisite-Unterstützung für zielgerichtete Inhalte Folgendes:
>
>* Wenn Sie Rollouts oder Live Copys verwenden, ist eine MSM-Lizenz erforderlich.
>* Wenn Sie die Synchronisierung mit Adobe Target verwenden, ist eine Adobe Target-Lizenz erforderlich.
>



## Anwendungsfälle  {#use-cases}

Sie können die Multisite-Unterstützung für zielgerichtete Inhalte auf verschiedene Art einrichten, je nachdem, welches Szenario sich für Ihre Zwecke am besten eignet. In diesem Abschnitt wird beschrieben, wie diese Einrichtung theoretisch für eine Marke funktioniert. Zudem finden Sie in unserem [Beispiel: Inhalts-Targeting basierend auf geografischen Angaben](#example-targeting-content-based-on-geography) eine Darstellung zur praktischen Anwendung von Inhalts-Targeting auf mehreren Sites.

Zielgerichtete Inhalte werden in sogenannten Gebieten erfasst, mit denen wiederum ihr Geltungsbereich auf Sites oder Seiten bestimmt wird. Diese Gebiete werden auf Ebene der Marke definiert. Eine Marke kann mehrere Gebiete umfassen. Gebiete können sich von Marke zu Marke unterscheiden. So kann beispielsweise eine Marke nur das primäre Gebiet enthalten, das für alle Marken gilt, während eine andere Marke hingegen zeitgleich mehrere Gebiete enthält (beispielsweise mit Unterschieden je nach Region). Marken müssen somit nicht zwingend die gleichen Gebiete aufweisen.

Mithilfe der Multisite-Unterstützung für zielgerichtete Inhalte können Sie beispielsweise zwei (oder mehr) Sites **einer** Marke einrichten, die eine der folgenden Eigenschaften aufweisen:

* Vollständig *unterschiedliche* zielgerichtete Inhalte: Die Bearbeitung der Inhalte auf einer Site beeinflusst die Inhalte der anderen Site nicht. Sites, die mit verschiedenen Gebieten verknüpft sind, führen Lese- und Schreibaufgaben für getrennt konfigurierte Gebiete aus. Beispiel:

   * Site A ist mit Gebiet X verknüpft.
   * Site B ist mit Gebiet Y verknüpft.

* Ein *freigegebener* Satz von zielgerichteten Inhalten; die Bearbeitung in einer Site wirkt sich direkt auf beide Sites aus. Sie können dies einrichten, indem Sie beide Sites auf dasselbe Gebiet verweisen. Sites, die sich auf dasselbe Gebiet beziehen, teilen die zielgerichteten Inhalte dieses Gebiets. Beispiel:

   * Site A ist mit Gebiet X verknüpft.
   * Site B ist mit Gebiet X verknüpft.

* Bestimmte zielgerichtete Inhalte werden über MSM von einer anderen Site *übernommen*: Die Inhalte können unidirektional von der Quelle an die Live Copy übermittelt werden. Beispiel:

   * Site A ist mit Gebiet X verknüpft.
   * Site B ist mit Gebiet Y verknüpft (dieses Gebiet ist eine Live Copy von Gebiet X).

Sie können auch **mehrere** Marken auf einer Site einsetzen, dieses Verfahren ist jedoch komplexer als die hier dargestellten Sachverhalte.

![chlimage_1-270](assets/chlimage_1-270.png)

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-authoring/technical-multisite-targeted.md).

## Beispiel: Inhalts-Targeting basierend auf geografischen Angaben {#example-targeting-content-based-on-geography}

Mithilfe der Multisite-Unterstützung für zielgerichtete Inhalte können Sie personalisierte Inhalte isolieren oder bereitstellen. Zur Veranschaulichung der Einsatzmöglichkeiten der Funktion beschreiben wir im Folgenden ein Szenario, bei dem zielgerichteter Inhalt je nach geografischer Region des Besuchers bereitgestellt werden soll:

Abhängig von geografischen Daten gibt es für die gleiche Site vier verschiedene Versionen:

* Die Site für die **Vereinigten Staaten** befindet sich oben links und dient als primäre Site. In diesem Beispiel wurde sie im Targeting-Modus geöffnet.
* Die drei übrigen Versionen sind diejenigen für **Kanada**, **Großbritannien** und **Australien**, wobei es sich bei diesen um Live Copys handelt. Diese Sites wurden im Vorschaumodus geöffnet.

![chlimage_1-271](assets/chlimage_1-271.png)

Alle Seiten teilen sich die personalisierten Inhalte der unterschiedlichen Regionen:

* Für Kanada wird das gleiche primäre Gebiet wie für die Vereinigten Staaten verwendet.
* Die Site für Großbritannien wurde mit Europa verknüpft und übernimmt die Inhalte des europäischen Mastergebietes.
* Australien verfügt über eigene personalisierte Inhalte, da es sich auf der Südhalbkugel befindet und saisonal bedingte Produkte nicht mit Produkten für die anderen Länder übereinstimmen.

![chlimage_1-272](assets/chlimage_1-272.png)

Für die Nordhalbkugel wurde eine Winteraktivität erstellt, doch der nordamerikanische Marketing-Experte wünscht sich für den Winter ein anderes Bild, das also für die US-Site geändert wird.

![chlimage_1-273](assets/chlimage_1-273.png)

Nach Aktualisierung der Registerkarte erscheint auch auf der Site für Kanada das neue Bild, ohne dass dies eigens eingestellt werden muss. Diese Änderung geschieht, da die Site von Kanada sich auf das gleiche primäre Gebiet wie die Site der Vereinigten Staaten bezieht. Die Bilder auf den Sites für Großbritannien und Australien ändern sich hingegen nicht.

![chlimage_1-274](assets/chlimage_1-274.png)

Der Marketingexperte möchte diese Änderungen auf das europäische Gebiet übertragen und [aktiviert die Live Copy](/help/sites-administering/msm-livecopy.md), indem er auf **Seiten-Rollout** tippt oder klickt. Nach Aktualisierung der Registerkarte erscheint auf der Site für Großbritannien das neue Bild, da das europäische Gebiet dieses (nach dem Rollout) vom primären Gebiet bezieht.

![chlimage_1-275](assets/chlimage_1-275.png)

Das Bild der Site für Australien bleibt wie gewünscht unverändert, da es in Australien Sommer ist und der Marketingexperte die Inhalte für dieses Land somit nicht ändern möchte. Die Site für Australien ändert sich nicht, da sie kein Gebiet mit den anderen Regionen teilt und keine Live Copy einer der anderen Regionen darstellt. Der Marketingexperte muss sich in keinem Fall sorgen, dass die zielgerichteten Inhalte für die australische Site überschrieben werden könnten.

Zudem kann für die Site für Großbritannien, deren Gebiet eine Live Copy des primären Gebiets darstellt, der Vererbungsstatus anhand des grünen Indikators neben dem Aktivitätennamen erkannt werden. Wird eine Aktivität geerbt, kann sie nicht bearbeitet werden, solange die Live Copy nicht ausgesetzt oder deaktiviert wurde.

Die Vererbung kann jederzeit ausgesetzt oder vollständig deaktiviert werden. Zudem können Sie jederzeit lokale Erlebnisse hinzufügen, die ohne Aussetzen der Vererbung nur für diese Region verfügbar sind.

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-authoring/technical-multisite-targeted.md).

### Erstellen eines neuen Gebiets bzw. eines neuen Gebiets als Live Copy {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

In AEM haben Sie die Wahl, entweder ein neues Gebiet oder ein neues Gebiet als Live Copy zu erstellen. Bei der Erstellung eines neuen Gebiets werden Aktivitäten und zu ihnen gehörige Elemente wie Angebote, Erlebnisse usw. gruppiert. Neue Gebiete werden dann benötigt, wenn Sie entweder zielgerichtete Inhalte erstellen, die sich vollständig von anderen Inhalten unterscheiden, oder wenn Sie zielgerichtete Inhalte teilen möchten.

Sollte über MSM jedoch eine Vererbung der beiden Seiten eingerichtet sein, ist diese möglicherweise unerwünscht. In diesem Fall sollten Sie ein neues Gebiet als Live Copy erstellen, bei der Y eine Live Copy von X ist und somit alle Aktivitäten übernimmt.

>[!NOTE]
>
>Handelt es sich bei einer Seite um eine Live Copy, verknüpft mit einem Gebiet, das selbst wiederum eine mit dem Gebiet der Seitenvorlage verknüpfte Live Copy ist, werden durch den Standard-Rollout alle folgenden Rollouts der zielgerichteten Inhalte ausgelöst.

In der folgenden Darstellung finden Sie beispielsweise vier Sites, von denen sich zwei ein primäres Gebiet (sowie alle Aktivitäten dieses Gebiets) teilen, eine weitere Site über ein Gebiet verfügt, das eine Live Copy des primären Gebiets ist, sodass die Aktivitäten bei einem Rollout geteilt werden, und die letzte Site völlig eigenständig ist (und somit ein eigenes Aktivitätsgebiet benötigt).

![chlimage_1-276](assets/chlimage_1-276.png)

Gehen Sie wie folgt vor, um diese Konfiguration in AEM nachzustellen:

* Site A ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Site B und Site A teilen sich Aktivitäten usw.
* Site B ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Site B und Site A teilen sich Aktivitäten usw.
* Site C ist mit dem vererbten Gebiet verknüpft, das wiederum eine Live Copy des primären Gebiets ist – erstellen Sie ein neues Gebiet als Live Copy, wenn eine Live Copy erstellt werden soll, die auf dem primären Gebiet beruht. Im Rahmen des Rollouts übernimmt das erbende Gebiet Aktivitäten aus dem primären Gebiet.
* Site D ist mit einem eigenen, separaten Gebiet verknüpft – erstellen Sie ein Gebiet, das keine bereits festgelegten Aktivitäten erhält. Dieses isolierte Gebiet übernimmt keine Aktivitäten der anderen Sites.

## Erstellen neuer Gebiete  {#creating-new-areas}

Gebiete können aktivitäten- und angebotsübergreifend gelten. Nach der Erstellung eines Gebiets in einer der Kategorien (beispielsweise in den Aktivitäten), kann dieses Gebiet auch in der anderen (beispielsweise in den Angeboten) verfügbar gemacht werden.

>[!NOTE]
>
>Der Standardbereich „primäres Gebiet“ wird standardmäßig ausgeblendet, wenn Sie auf den Namen einer Marke tippen/klicken, **bis** Sie einen anderen Bereich erstellen. Wählen Sie entweder in der **Aktivitäts-** oder der **Angebotskonsole** eine Marke aus, wird Ihnen die **Gebietskonsole** angezeigt.

So erstellen Sie ein neues Gebiet:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf **Gebiet erstellen**.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken Sie auf das Symbol für **Gebiet** und anschließend auf **Weiter**.
1. Geben Sie im Feld **Titel** einen Namen für das neue Gebiet ein. Wählen Sie, falls gewünscht, Tags aus.
1. Tippen oder klicken Sie auf **Erstellen**.

   AEM leitet Sie auf das Markenfenster um, in dem alle erstellten Gebiete aufgelistet sind. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt in der Markenkonsole erstellen.

   ![chlimage_1-278](assets/chlimage_1-278.png)

## Erstellen neuer Gebiete als Live Copys {#creating-areas-as-live-copies}

Gebiete werden als Live Copys erstellt, damit diese über Site-Strukturen hinweg zielgerichtete Inhalte übernehmen können.

So erstellen Sie ein Gebiet als Live Copy:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf **Gebiet als Live Copy erstellen**.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Wählen Sie das Gebiet aus, von dem Sie eine Live Copy erstellen möchten, und klicken Sie auf **Weiter**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Geben Sie im Feld **Name** einen Namen für die Live Copy ein. Standardmäßig werden Unterseiten einbezogen. schließen Sie sie aus, indem Sie das Kontrollkästchen **Unterseiten ausschließen** aktivieren.

   ![chlimage_1-281](assets/chlimage_1-281.png)

1. Wählen Sie im Dropdown-Menü **Rollout-Konfigurationen** die entsprechende Konfiguration aus.

   Beschreibungen der verschiedenen Optionen finden Sie unter [Installierte Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations).

   Weitere Informationen zu Live Copys finden Sie unter [Erstellen und Synchronisieren von Live Copys](/help/sites-administering/msm-livecopy.md).

   >[!NOTE]
   >
   >Wird der Rollout einer Site für eine Live Copy durchgeführt und ist das für die Blueprint-Seite konfigurierte Gebiet auch Blueprint des Gebiets, das für die Live Copy der Seite konfiguriert wurde, löst die LiveAction **personalizationContentRollout** einen synchronen subRollout aus, der Teil der **Standard-Rollout-Konfigurationen** ist.

1. Tippen oder klicken Sie auf **Erstellen**.

   AEM leitet Sie auf das Markenfenster um, in dem alle erstellten Gebiete aufgelistet sind. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt im Markenfenster erstellen.

   ![chlimage_1-282](assets/chlimage_1-282.png)

## Verknüpfen von Sites mit Gebieten {#linking-sites-to-an-area}

Gebiete können entweder mit Seiten oder einer Site verknüpft werden. Gebiete werden von allen Unterseiten übernommen, falls diese auf der Unterseite nicht durch eine Zuordnung überschrieben werden. Im Allgemeinen erfolgen Verknüpfungen jedoch auf Site-Ebene.

Führen Sie eine Verknüpfung durch, stehen nur die Aktivitäten, Erlebnisse und Angebote des verknüpften Gebiets zur Verfügung. Somit wird eine Verwechslung mit unabhängig verwalteten Inhalten verhindert. Wird kein weiteres Gebiet konfiguriert, gilt das primäre Gebiet der jeweiligen Marke.

>[!NOTE]
>
>Seiten oder Sites, die auf dasselbe Gebiet verweisen, verwenden *denselben* freigegebenen Satz an Aktivitäten, Erlebnissen und Angeboten. Die Bearbeitung einer Aktivität, eines Erlebnisses oder eines Angebots, die bzw. das von mehreren Sites gemeinsam genutzt werden, wirkt sich auf alle Sites aus.

So verknüpfen Sie eine Site mit einem Gebiet:

1. Navigieren Sie zur Site (oder Seite), die Sie mit einem Gebiet verknüpfen möchten.
1. Wählen Sie die Site oder Seite aus und tippen oder klicken Sie auf **Eigenschaften anzeigen**.
1. Tippen oder klicken Sie auf die Registerkarte **Personalisierung**.
1. Wählen Sie im Menü **Marke** jene Marke aus, mit der das Gebiet verknüpft werden soll. Nach Auswahl der Marke werden die verfügbaren Gebiete im Menü **Gebiets-Verweis** aufgeführt.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Wählen Sie aus dem Dropdown-Menü **Gebiets-Verweis** das gewünschte Gebiet aus und klicken oder tippen Sie auf **Speichern**.

   ![chlimage_1-284](assets/chlimage_1-284.png)

## Trennen von Live Copy oder Aussetzen der Vererbung zielgerichteter Inhalte {#detaching-live-copy-or-suspending-inheritance-of-targeted-content}

Möglicherweise möchten Sie die Vererbung zielgerichteter Inhalte aussetzen oder deaktivieren. Diese Deaktivierung oder Aussetzung muss für jede Aktivität einzeln konfiguriert werden. Sie möchten beispielsweise die Erlebnisse in Ihrer Aktivität bearbeiten. Ist diese Aktivität jedoch noch immer mit der geerbten Kopie verknüpft, können Erlebnisse oder Eigenschaften der Aktivität nicht bearbeitet werden.

Das vorübergehende Aussetzen der Vererbung unterbricht diese Verbindung zeitweise, diese kann künftig aber wieder hergestellt werden. Wird die Live Copy hingegen getrennt, ist die Vererbung dauerhaft inaktiv.

Die Vererbung zielgerichteter Inhalte lässt sich aussetzen oder deaktivieren, indem der Inhalt in einer Aktivität wiederhergestellt wird. Sollte eine Site oder Seite sich auf ein Gebiet beziehen, das eine Live Copy ist, können Sie den Vererbungsstatus der Aktivität anzeigen.

Eine Aktivität, die Daten von einer anderen Site erbt, weist neben ihrem Namen eine grüne Markierung auf. Ausgesetzte Vererbungen werden rot gekennzeichnet, lokal erstellte Aktivitäten verfügen über keine eigene Kennzeichnung.

>[!NOTE]
>
>* Sie können Live Copys nur in einer Aktivität aussetzen oder deaktivieren.
>* Live Copys müssen nicht ausgesetzt oder getrennt werden, um eine geerbte Aktivität zu erweitern. Sie können jederzeit **neue** lokale Erlebnisse und Angebote für die Aktivität erstellen. Möchten Sie eine bestehende Aktivität bearbeiten, müssen Sie die Vererbung aussetzen.
>



### Aussetzen der Vererbung  {#suspending-inheritance}

So deaktivieren Sie die Vererbung zielgerichteter Inhalte oder setzen sie aus:

1. Navigieren Sie zu der Seite, auf der die Vererbung ausgesetzt oder deaktiviert werden soll, und klicken oder tippen Sie im Modus-Dropdown-Menü auf **Targeting**.
1. Ist Ihre Seite mit einem Gebiet verknüpft, das eine Live Copy darstellt, wird der Vererbungsstatus angezeigt. Tippen oder klicken Sie auf **Targeting starten**.
1. Gehen Sie wie folgt vor, um die Vererbung einer Aktivität auszusetzen:

   1. Wählen Sie ein Element der Aktivität aus, beispielsweise die Zielgruppe. AEM zeigt automatisch den Bestätigungsdialog für das Aussetzen der Live Copy an. (Sie können die Live Copy aussetzen, indem Sie während des Targeting-Verfahrens auf beliebige Elemente klicken oder tippen.)
   1. Wählen Sie **Live Copy aussetzen** aus dem Dropdown-Menü in der Symbolleiste aus.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Tippen oder klicken Sie auf **Aussetzen**, um die Aktivität zu unterbrechen. Ausgesetzte Aktivitäten werden rot markiert.

   ![chlimage_1-286](assets/chlimage_1-286.png)

### Deaktivieren der Vererbung {#breaking-inheritance}

So deaktivieren Sie die Vererbung zielgerichteter Inhalte einer Aktivität:

1. Navigieren Sie zu der Seite, deren Live Copy Sie vom primären Gebiet trennen möchten, und klicken oder tippen Sie im Modus-Dropdown-Menü auf **Targeting**.
1. Ist Ihre Seite mit einem Gebiet verknüpft, das eine Live Copy darstellt, wird der Vererbungsstatus angezeigt. Tippen oder klicken Sie auf **Targeting starten**.
1. Wählen Sie aus dem Dropdown-Menü in der Symbolleiste die Option **Live Copy trennen**. AEM bestätigt, dass Sie die Live Copy trennen möchten.
1. Tippen oder klicken Sie auf **Entfernen**, um die Live Copy von der Aktivität zu trennen. Nach der Trennung ist das Dropdown-Menü für die Vererbung nicht länger verfügbar. Die Aktivität ist jetzt eine lokale Aktivität.

   ![chlimage_1-287](assets/chlimage_1-287.png)

## Wiederherstellen der Vererbung zielgerichteter Inhalte {#restoring-inheritance-of-targeted-content}

Sollten Sie die Vererbung zielgerichteter Inhalte einer Aktivität ausgesetzt haben, kann sie jederzeit wiederhergestellt werden. Sollten Sie die Live Copy jedoch getrennt haben, ist eine Wiederherstellung nicht möglich.

So stellen Sie die Vererbung zielgerichteter Inhalte wieder her:

1. Navigieren Sie zu der Seite, auf der die Vererbung wiederhergestellt werden soll, und klicken oder tippen Sie im Modus-Dropdown-Menü auf **Targeting**.
1. Tippen oder klicken Sie auf **Targeting starten**.
1. Wählen Sie im Dropdownmenü in der Symbolleiste die Option **Live Copy fortsetzen**.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Tippen oder klicken Sie auf **Fortsetzen**, um zu bestätigen, dass Sie die Vererbung an die Live Copy wieder aufnehmen möchten. Alle Änderungen, die an der aktuellen Aktivität vorgenommen wurden, gehen bei Wiederherstellung der Vererbung verloren.

## Löschen von Gebieten  {#deleting-areas}

Löschen Sie ein Gebiet, werden sämtliche Aktivitäten dieses Gebiets ebenfalls gelöscht. Vor dem Löschen eines Gebiets werden Sie von AEM gewarnt. Sollten Sie ein Gebiet löschen, das mit einer Site verknüpft ist, wird die Marke stattdessen automatisch mit dem primären Gebiet verknüpft.

So löschen Sie Gebiete:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Tippen oder klicken Sie auf das Symbol neben dem Gebiet, das Sie löschen möchten.
1. Tippen oder klicken Sie auf **Löschen** und bestätigen Sie, dass das Gebiet gelöscht werden soll.
