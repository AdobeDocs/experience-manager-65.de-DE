---
title: Konfigurieren der Segmentierung
seo-title: Configuring Segmentation
description: Erfahren Sie, wie Sie die Segmentierung für AEM Campaign konfigurieren.
seo-description: Learn how to configure segmentation for AEM Campaign.
uuid: 604ca34d-cdb9-49ff-8f75-02a44b60a8a2
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: c68d5853-684f-42f2-a215-c1eaee06f58a
docset: aem65
exl-id: 6d759907-8796-4749-bd80-306ec7f2c819
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 44%

---


# Konfigurieren der Segmentierung {#configuring-segmentation}

>[!NOTE]
>
>Dieses Dokument behandelt die Konfiguration der Segmentierung, wie sie mit ClientContext verwendet wird. Informationen zum Konfigurieren von Segmenten mit ContextHub über die Touch-Benutzeroberfläche finden Sie unter [Konfigurieren der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md).

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. Siehe [Glossar zur Segmentierung](/help/sites-authoring/segmentation-overview.md) für Informationen zur Funktionsweise der Segmentierung und zu Schlüsselbegriffen.

Je nach den von Ihnen bereits zu den Besuchern Ihrer Site erfassten Informationen sowie je nach Ihren angepeilten Zielen müssen Sie die erforderlichen Segmente und Strategien für Ihre zielgerichteten Inhalte festlegen.

Diese Segmente werden dann verwendet, um einem Besucher gezielt bestimmte Inhalte anzuzeigen. Dieser Inhalt wird im Abschnitt [Kampagnen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md) der Website verwaltet. Hier definierte Teaser-Seiten können als Teaser-Absätze auf jeder Seite eingefügt werden und definieren, für welches Besuchersegment die spezialisierten Inhalte gelten.

AEM ermöglicht Ihnen das einfache Erstellen und Aktualisieren von Segmenten, Teasern und Kampagnen. Außerdem können Sie damit die Ergebnisse Ihrer Definitionen überprüfen.

Der **Segment-Editor** ermöglicht Ihnen die einfache Definition eines Segments:

![Fenster &quot;Segment-Editor&quot;](assets/segmenteditor.png)

Sie können **Bearbeiten** jedes Segment, um eine **Titel**, **Beschreibung** und **Verstärken** Faktor. Mithilfe des Sidekicks können Sie **UND** und **ODER** Container zum Definieren der **Segmentlogik** und fügen Sie dann die erforderlichen hinzu **Segmenteigenschaften** , um die Auswahlkriterien zu definieren.

## Verstärkungsfaktor {#boost-factor}

Jedes Segment verfügt über einen Parameter zum **Verstärken**, der als Gewichtungsfaktor verwendet wird. Eine höhere Zahl zeigt an, dass das Segment bei der Auswahl gegenüber einem Segment mit einer niedrigeren Zahl bevorzugt wird.

* Mindestwert: `0`
* Höchstwert: `1000000`

## Segmentlogik {#segment-logic}

Die folgenden logischen Container sind standardmäßig verfügbar und ermöglichen es Ihnen, die Logik Ihrer Segmentauswahl zu konstruieren. Sie können aus dem Sidekick in den Editor gezogen werden:

<table>
 <tbody>
  <tr>
   <td> UND-Container<br /> </td>
   <td> Der boolesche UND-Operator.<br /> </td>
  </tr>
  <tr>
   <td> ODER-Container<br /> </td>
   <td> Der boolesche ODER-Operator.</td>
  </tr>
 </tbody>
</table>

## Segmenteigenschaften {#segment-traits}

Die folgenden Segmenteigenschaften sind standardmäßig verfügbar: sie können aus dem Sidekick in den Editor gezogen werden:

<table>
 <tbody>
  <tr>
   <td> IP-Bereich<br /> </td>
   <td>Definiert einen Bereich von IP-Adressen, den der Besucher haben kann.<br /> </td>
  </tr>
  <tr>
   <td> Seitenaufrufe<br /> </td>
   <td>Wie oft die Seite angefordert wurde. <br /> </td>
  </tr>
  <tr>
   <td> Seiteneigenschaft<br /> </td>
   <td>Jede Eigenschaft der besuchten Seite.<br /> </td>
  </tr>
  <tr>
   <td> Verweis-Schlüsselwörter<br /> </td>
   <td>Schlüsselwörter, die mit Informationen aus der verweisenden Website abgeglichen werden. <br /> </td>
  </tr>
  <tr>
   <td> Skript</td>
   <td>JavaScript-Ausdruck, der ausgewertet werden soll.<br /> </td>
  </tr>
  <tr>
   <td> Segment-Referenz <br /> </td>
   <td>Verweis auf eine andere Segmentdefinition.<br /> </td>
  </tr>
  <tr>
   <td> Tag-Cloud<br /> </td>
   <td>Tags, die mit denen der besuchten Seiten abgeglichen werden.<br /> </td>
  </tr>
  <tr>
   <td> Benutzeralter<br /> </td>
   <td>Wie aus dem Benutzerprofil übernommen.<br /> </td>
  </tr>
  <tr>
   <td> Benutzereigenschaft<br /> </td>
   <td>Alle anderen Informationen, die im Benutzerprofil verfügbar sind. </td>
  </tr>
 </tbody>
</table>

Sie können diese Eigenschaften mithilfe der booleschen Operatoren „ODER“ und „UND“ kombinieren (siehe [Erstellen eines neuen Segments](#creating-a-new-segment)), um das exakte Szenario zur Auswahl dieses Segments festzulegen.

Wenn die gesamte Anweisung mit „true“ bewertet wurde, wird dieses Segment aufgelöst. Falls mehrere Segmente zutreffen, wird außerdem der Faktor **[Verstärken](/help/sites-administering/campaign-segmentation.md#boost-factor)** verwendet.

>[!CAUTION]
>
>Der Segmenteditor prüft nicht auf Zirkelbezüge. Ein Beispiel hierfür wäre, wenn Segment A auf ein anderes Segment B verweist, das wiederum auf Segment A verweist. Sie müssen sicherstellen, dass Ihre Segmente keine Zirkelbezüge enthalten.

>[!NOTE]
>
>Eigenschaften mit dem Suffix **_i18n** werden durch ein Skript festgelegt, das Teil der clientlib zur Personalisierungsbenutzeroberfläche ist. Alle benutzeroberflächenbezogenen clientlibs werden nur dann in der Autoreninstanz geladen, wenn die Benutzeroberfläche in der Veröffentlichungsinstanz nicht benötigt wird.
>
>Daher ist es bei der Erstellung eines Segments mit solchen Eigenschaften normalerweise erforderlich, beispielsweise **browserFamily** statt **browserFamily_i18n** zu verwenden.

### Erstellen eines neuen Segments {#creating-a-new-segment}

So legen Sie Ihr neues Segment fest:

1. Wählen Sie in der Leiste **Tools > Vorgänge > Konfiguration** aus.
1. Klicken Sie auf **Segmentierung** im linken Bereich und navigieren Sie zur gewünschten Position.
1. Erstellen Sie eine [neue Seite](/help/sites-authoring/editing-content.md#creatinganewpage) mithilfe der **Segment** Vorlage.
1. Öffnen Sie die neue Seite, um den Segment-Editor anzuzeigen:

   ![Der erste Schritt zum Erstellen eines neuen Segments im Segment-Editor](assets/screen_shot_2012-02-02at101726am.png)

1. Verwenden Sie entweder den Sidekick oder das Kontextmenü (in der Regel klicken Sie mit der rechten Maustaste auf die Schaltfläche und wählen Sie dann **Neu...** , um das Fenster Neue Komponente einfügen zu öffnen), um die benötigte Segmenteigenschaft zu finden. Ziehen Sie es dann auf die **Segment-Editor** wird er in der Standardeinstellung angezeigt **UND** Container.
1. Doppelklicken Sie auf die neue Eigenschaft, um die spezifischen Parameter zu bearbeiten. z. B. Mausposition:

   ![Bearbeiten einer Komponente im Segment-Editor](assets/screen_shot_2012-02-02at103135am.png)

1. Klicken **OK** , um Ihre Definition zu speichern:
1. Sie können **Bearbeiten** die Segmentdefinition, um ihr eine **Titel**, **Beschreibung** und **[Verstärken](#boost-factor)** Faktor:

   ![Bearbeiten der Segmenteinstellungen im Segment-Editor](assets/screen_shot_2012-02-02at103547am.png)

1. Fügen Sie bei Bedarf weitere Eigenschaften hinzu. Sie können boolesche Ausdrücke mit der **UND-Container** und **ODER-Container** Komponenten gefunden unter **Segmentlogik**. Mit dem Segmenteditor können Sie nicht mehr benötigte Eigenschaften oder Container löschen oder sie an neue Positionen innerhalb der Anweisung ziehen.

### Verwenden von UND- und ODER-Containern {#using-and-and-or-containers}

Sie können komplexe Segmente in AEM erstellen. Es ist hilfreich, einige grundlegende Punkte zu beachten:

* Die oberste Ebene der Definition ist immer der ursprünglich erstellte UND-Container. Dies kann nicht verändert werden, hat allerdings auch keine Auswirkungen auf den Rest der Segmentdefinition.
* Stellen Sie sicher, dass die Verschachtelung Ihres Containers sinnvoll ist. Die Container können als die Klammern Ihres booleschen Ausdrucks betrachtet werden.

Das folgende Beispiel wird verwendet, um Besucher auszuwählen, die entweder

Männlich und zwischen 16 und 65 Jahren

ODER

Weiblich und zwischen 16 und 62 Jahren

Da der Hauptoperator ODER ist, müssen Sie mit einem **ODER-Container**. Innerhalb dieses Abschnitts verfügen Sie über 2 UND-Anweisungen, für jede dieser müssen Sie eine **UND-Container**, zu dem Sie die einzelnen Eigenschaften hinzufügen können.

![Beispiel für die UND- und ODER-Operatoren im Segmenteditor](assets/screen_shot_2012-02-02at105145am.png)

## Testen der Anwendung eines Segments {#testing-the-application-of-a-segment}

Sobald das Segment definiert wurde, können die potenziellen Ergebnisse mithilfe der **[ClientContext](/help/sites-administering/client-context.md)**:

1. Wählen Sie das zu testende Segment aus.
1. Presse **[Strg+Alt+C](/help/sites-authoring/page-authoring.md#keyboardshortcuts)** , um **[ClientContext](/help/sites-administering/client-context.md)**, der die erfassten Daten anzeigt. Zu Testzwecken können Sie bestimmte Werte **bearbeiten** oder ein anderes Profil **laden**, um dort die Auswirkungen zu sehen.

1. Je nach den definierten Eigenschaften können die zur aktuellen Seite verfügbaren Daten mit der Segmentdefinition übereinstimmen oder nicht. Der Status der Übereinstimmung wird unter der Definition angezeigt.

Eine einfache Segmentdefinition kann auf dem Alter und Geschlecht des Benutzers basieren. Das Laden eines spezifischen Profils zeigt, dass das Segment erfolgreich aufgelöst wurde:

![Verwenden des ClientContext-Fensters zum Testen eines AND-Segmentierungsvorgangs](assets/screen_shot_2012-02-02at105926am.png)

Oder nicht:

![Verwenden des ClientContext-Fensters zum Testen eines NICHT-Segmentierungsvorgangs](assets/screen_shot_2012-02-02at110019am.png)

>[!NOTE]
>
>Alle Eigenschaften werden sofort aufgelöst, obwohl sich die meisten beim Neuladen der Seite ändern. Änderungen an der Mausposition sind sofort sichtbar, sodass sie für Testzwecke nützlich sind.

Solche Tests können auch auf Inhaltsseiten und in Kombination mit **Teaser**-Komponenten durchgeführt werden.

Wenn Sie den Mauszeiger über einen Teaser-Absatz bewegen, werden die angewendeten Segmente angezeigt, unabhängig davon, ob sie derzeit aufgelöst werden und warum daher die aktuelle Teaser-Instanz ausgewählt wurde:

![Beispiel: Mauszeiger über ein Segment](assets/chlimage_1-47.png)

### Verwenden Ihres Segments {#using-your-segment}

Segmente werden derzeit in [Kampagnen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md). Sie werden verwendet, um den tatsächlichen Inhalt zu steuern, der für bestimmte Zielgruppen sichtbar ist. Siehe [Grundlegendes zu Segmenten](/help/sites-authoring/segmentation-overview.md) für weitere Informationen.
