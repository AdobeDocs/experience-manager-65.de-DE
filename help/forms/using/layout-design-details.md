---
title: Layout-Design
description: In den Layoutdesigndetails wird erläutert, wie Sie Layouts erstellen können, die für Ihre Briefe oder interaktive Kommunikation verwendet werden können.
content-type: reference
topic-tags: correspondence-management, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Correspondence Management
exl-id: 9e1b0067-c7dc-4bbb-a209-d674592be858
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '2170'
ht-degree: 48%

---

# Layout-Design{#layout-design}

XFA-Formularvorlagen oder XDPs sind Vorlagen für:

* [Briefe](/help/forms/using/create-letter.md)
* [Druckkanal](/help/forms/using/web-channel-print-channel.md#printchannel) von [Interaktiver Kommunikation](/help/forms/using/interactive-communications-overview.md)

* Layout-Fragmente

Eine XDP wird mit Adobe Forms Designer entwickelt. In diesem Artikel finden Sie Informationen zum Erstellen von XDPs und zum Erstellen einer effektiven Korrespondenz/interaktiven Kommunikation, z. B. wo Formularfelder oder Zielbereiche verwendet werden und wann Layout-Fragmente verwendet werden sollten.

## Erstellen eines Layouts für Briefe oder für den Druckkanal von interaktiver Kommunikation {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Ein Layout bestimmt das grafische Layout eines Briefs/Druckkanals einer interaktiven Kommunikation. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenznummer“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche darstellen. Erstellen Sie das Layout im Formulardesigner. Danach lädt es der Anwendungsspezialist auf den AEM-Server. Von dort können Sie das Layout beim Erstellen einer Korrespondenzvorlage oder eines Druckkanals einer interaktiven Kommunikation auswählen.

![Designer: Layout erstellen](assets/claimsubrogationlayout.png)

Führen Sie die folgenden Schritte aus, um Layouts für Briefe/Druckkanäle der interaktiven Kommunikation zu erstellen:

1. Analysieren Sie das Layout und bestimmen Sie den Inhalt, der über alle Seiten hinweg wiederholt wird. Normalerweise fallen Seitenkopf und -fußzeile in diese Kategorie. Dieser Inhalt wird auf Masterseiten des Layouts platziert. Der restliche Inhalt wird auf die Textseiten des Layouts übertragen. In einer Richtlinienjacke können das Logo und die Firmenadresse zur Kopf- und Fußzeile der Masterseite hinzugefügt werden. Beispielsweise verwendet der Hinweis auf den Abbruch dasselbe Layout.
1. Unterteilen Sie beim Entwerfen von Textseiten den Seiteninhalt in Abschnitte. Jeder Abschnitt ist als Teilformular konzipiert, das in das Layout selbst oder als Fragment-Layout eingebettet ist. Wenn der Abschnitt eine Tabelle enthält, modellieren Sie den Abschnitt als Layout-Fragment.
1. Ein Layout kann wie folgt gestaltet werden:

   1. Machen Sie jeden Abschnitt zu einem separaten Teilformular, das alle Elemente des Abschnitts enthält.
   1. Weisen Sie jedem Abschnitt ein untergeordnetes Teilformular desselben übergeordneten Teilformulars zu. Das Layout des übergeordneten Teilformulars ist auf Fluss eingestellt, damit die Abschnitte unter verschoben werden können, wenn große Daten in vorherigen Abschnitten zusammengeführt werden.
   1. Der Primäre Bereich kann auch für andere Layouts wiederverwendet werden. Erstellen Sie es als Fragment-Layout.
   1. Die Details des zusätzlichen Abschnitts enthalten nur zwei Elemente, die untereinander platziert sind, können große Daten enthalten und sind als Fluss konzipiert.
   1. Andere Abschnitte enthalten Elemente an bestimmten Positionen, sodass sie als positioniertes Layout konzipiert sind.
   1. Teilen Sie einen Abschnitt in Teilformulare auf, wenn der Abschnitt Elemente an bestimmten Positionen enthält und diese Elemente große Datenmengen enthalten. Ordnen Sie dann die Teilformulare an, um das gewünschte Verhalten zu erzielen.
   1. Fügen Sie für den Abschnitt &quot;Primärer Aufenthalt&quot;einen Platzhalter-Zielbereich hinzu. Dieser Platzhalter ist zum Zeitpunkt der Erstellung des Briefs/der interaktiven Kommunikation an den Primären Fragmentspeicherort gebunden.
   1. Laden Sie das Layout (und gegebenenfalls das Fragment, das das Layout verwendet) auf den AEM Forms-Server hoch.

### Verwenden eines Teilformulars in einer XDP-Vorlage {#usesubformxdp}

Nachdem Sie das für die Erstellung der interaktiven Kommunikation erforderliche Layout analysiert haben, können Sie mithilfe von Forms Designer Teilformulare in der XDP-Vorlage erstellen. Leere Teilformularkomponenten, die in der XDP-Vorlage verwendet werden, führen zur Anzeige von Zielbereichen im Druckkanal der interaktiven Kommunikation.

>[!NOTE]
>
>Fügen Sie Inhalte zum Druckkanal der interaktiven Kommunikation hinzu, anstatt Inhalte zur Teilformularkomponente in der XDP-Vorlage hinzuzufügen. Fügen Sie den Zielbereichen im Druckkanal mithilfe von [Dokumentfragmenten, Diagrammen, Bildern](create-interactive-communication.md#step2) und Layout-Fragmenten Inhalte hinzu.

Führen Sie die folgenden Schritte durch, um das Teilformular in einer XDP-Vorlage zu verwenden:

1. Öffnen Sie den Forms Designer, wählen Sie **Datei** > **Neu** > **Leeres Formular verwenden**, tippen Sie auf **Weiter** und dann auf **Beenden**, um das Formular für die Vorlagenerstellung zu öffnen.

   Stellen Sie sicher, dass die **Objektbibliothek** und die Option **Objekt** im Menü **Fenster** ausgewählt werden.

1. Ziehen Sie die Komponente **Teilformular** aus der **Objektbibliothek** in das Formular.

   ![Komponenten-Designer](assets/subform_component_designer_new.png)

1. Wählen Sie das Teilformular aus, um die Optionen für das Teilformular im Fenster **Objekt** im rechten Bereich anzuzeigen.
1. Wählen Sie die Registerkarte **Teilformular** und wählen Sie **Textfluss** aus der Dropdown-Liste **Inhalt** aus. Ziehen Sie den linken Endpunkt des Teilformulars, um die Länge anzupassen.

   ![Teilformular mit Textfluss](assets/object_subform_flowed_new.png)

1. Auf der Registerkarte **Bindung**:

   1. Geben Sie einen Namen für das Teilformular im Feld **Name** an.
   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

1. Wählen Sie auf ähnliche Weise das Stammteilformular aus dem linken Bereich aus.

   ![Stammteilformular](assets/root_subform_designer_new.png)

1. Wählen Sie die Registerkarte **Teilformular**, und wählen Sie **Textfluss** aus der Dropdown-Liste **Inhalt**. Führen Sie auf der Registerkarte **Bindungen** folgende Schritte aus:

   1. Geben Sie einen Namen für das Teilformular im Feld **Name** an.
   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

   Wiederholen Sie die Schritte 2 bis 5, um der XDP-Vorlage weitere Teilformulare hinzuzufügen. Fügen Sie [Text, Dokumentfragmente, Bilder und Diagramme](create-interactive-communication.md#step2) nur während des Verfassens der interaktiven Kommunikation zu den Zielbereichen hinzu.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie einen Namen für die XDP-Vorlage an.
   1. Auswählen **.xdp** aus dem **Dateityp** Dropdown-Liste.

   1. Tippen Sie auf **Speichern**.

### Verwenden der Bildfeldkomponente in einer XDP-Vorlage {#use-image-field-component-in-an-xdp-template}

Verwenden Sie die Bildfeld- oder Teilformularkomponente in der XDP-Vorlage, um während des Erstellens der interaktiven Kommunikation ein Bild hinzuzufügen.

>[!NOTE]
>
>Fügen Sie ein Bild zum Druckkanal der interaktiven Kommunikation hinzu, anstatt ein Bild zur Bildfeld- oder Teilformularkomponente in der XDP-Vorlage hinzuzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Inhalten zur interaktiven Kommunikation](../../forms/using/create-interactive-communication.md#step2).

Führen Sie die folgenden Schritte aus, um die Bildfeldkomponente in einer XDP-Vorlage zu verwenden:

1. Ziehen Sie die **Bildfeldkomponente** per Drag-and-Drop aus der **Objektbibliothek** in das Formular.
1. Wählen Sie das Teilformular aus, um die Optionen für das Teilformular im Fenster **Objekt** im rechten Bereich anzuzeigen.
1. Auf der Registerkarte **Bindung**:

   1. Geben Sie einen Namen für das Bildfeld im Feld **Name** an.
   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

### XDP-Vorlage für Layoutfragmente erstellen {#xdplayoutfragments}

Verwenden Sie die Tabellenkomponente in Forms Designer, um Layout-Fragmente zu erstellen, und verwenden Sie diese dann, um Tabellen zu erstellen, während Sie den Druckkanal der interaktiven Kommunikation verfassen. Durch die Verwendung von Layout-Fragmenten zur Erstellung von Tabellen wird sichergestellt, dass der Tabelleninhalt seine Struktur behält, wenn der Web-Kanal automatisch mithilfe des Druckkanals generiert wird.

>[!NOTE]
>
>Geben Sie Text in die Tabellenzellen ein oder [erstellen Sie Bindungen mit Formulardatenmodellobjekten](create-interactive-communication.md#step2) nur während des Verfassens der interaktiven Kommunikation.

Führen Sie die folgenden Schritte aus, um in der XDP-Vorlage die Tabellenkomponente mithilfe von Forms Designer zu verwenden:

1. Ziehen Sie die **Tabellenkomponente** per Drag-and-Drop aus der **Objektbibliothek** auf das Formular.
1. Im Dialogfeld **Tabelle einfügen**:

   1. Geben Sie die Anzahl der Zeilen und Spalten für die Tabelle an.
   1. Aktivieren Sie das Kontrollkästchen **Kopfzeile in Tabelle einschließen**, um eine Zeile für die Tabellenkopfzeile einzufügen.
   1. Tippen Sie auf **OK**.

1. Tippen Sie auf **+** im linken Bereich neben dem Namen der Tabelle, klicken Sie mit der rechten Maustaste auf die Zellennamen in der Kopfzeile und in anderen Zeilen und wählen Sie **Objekt umbenennen**, um die Tabellenzellen umzubenennen.
1. Klicken Sie auf die Textfelder für die Tabellenkopfzeilen in der **Design-Ansicht** und benennen Sie sie um.
1. Ziehen Sie in der **Design-Ansicht** die **Textfeldkomponente** per Drag-and-Drop aus der **Objektbibliothek** auf jede Tabellenzelle. Führen Sie diesen Schritt aus, um Tabellenzellen bei der Erstellung der interaktiven Kommunikation an die Formulardatenmodellobjekte zu binden.

   ![Textfelder in einer Tabelle](assets/text_fields_table_new.png)

1. Klicken Sie auf den Namen der Zeile im linken Bereich und wählen Sie **Objekt** > **Bindung** > **Zeile für jedes Datenelement wiederholen**. Führen Sie diesen Schritt aus, um sicherzustellen, dass die Tabellenzeile für jedes in der Datenbank verfügbare Datenelement automatisch wiederholt wird, wenn eine Bindung zwischen den Tabellenzellen dieser Zeile mit Formulardatenmodellobjekten des Sammlungstyps erstellt wird.

   Geben Sie Text in die Tabellenzellen ein oder [erstellen Sie Bindungen mit Formulardatenmodellobjekten](create-interactive-communication.md#step2) nur während des Verfassens der interaktiven Kommunikation.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen für die XDP-Vorlage an.
   1. Auswählen **.xdp** aus dem **Dateityp** Dropdown-Liste.

   1. Tippen Sie auf **Speichern**.

### Hochladen einer XDP-Vorlage auf den AEM Forms-Server {#uploadxdptemplate}

Nachdem Sie eine XDP-Vorlage mit Forms Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server hochladen, damit die Vorlage beim Erstellen der interaktiven Kommunikation verwendet werden kann.

1. Wählen Sie **Formulare** > **Formulare &amp; Dokumente**.
1. Tippen Sie auf **Erstellen** > **Datei hochladen**.
1. Navigieren Sie zum Speicherort der XDP-Vorlage im lokalen Dateisystem und tippen Sie auf **Öffnen**, um die XDP-Vorlage auf den AEM Forms-Server zu importieren.

## Schema verwenden {#using-schema}

Sie können ein Schema in einem Layout oder Layout-Fragment verwenden, es ist jedoch nicht erforderlich. Wenn Sie ein Schema verwenden, stellen Sie Folgendes sicher:

1. Layout und alle Fragmentlayouts, die in einem Brief/interaktiver Kommunikation verwendet werden, verwenden dasselbe Schema wie der Brief/interaktive Kommunikation.
1. Alle Felder, die mit Daten gefüllt werden müssen, sind an das Schema gebunden.

## Verknüpfungsfähige Felder erstellen {#creating-relatable-fields}

Standardmäßig werden alle Felder als mit verschiedenen anderen Datenquellen verknüpfungsfähig betrachtet. Wenn Ihr Layout Felder enthält, die nicht mit einer Datenquelle verknüpfungsfähig sind, geben Sie dem Feld das Suffix &quot;_int&quot;(intern) an, z. B. pageCount_int.

Ein verknüpfungsfähiges Feld muss:

* es muss ein XFA &lt;field> oder &lt;exclGroup> sein
* über einen XFA-Bindungsverweis verfügen
* wenn es sich um eine &lt;exclgroup>muss mindestens ein untergeordnetes Optionsfeld vorhanden sein; andernfalls kann der Werttyp nicht bestimmt werden.

Ein verknüpfungsfähiges Feld muss:

* einen Namen haben

Ein verknüpfungsfähiges Feld darf nicht:

* Fügen Sie ein &quot;_int&quot;-Suffix in seinen Namen ein.
* haben Bindungssatz &quot;none&quot;
* es muss ein untergeordnetes Element eines &lt;exclGroup>-Elements sein

Solange ein verknüpfungsfähiges Feld die oben beschriebenen Kriterien erfüllt, kann es sich an einer beliebigen Position und in jeder Verschachtelungstiefe im Layout befinden. Verknüpfungsfähige Felder können auf Masterseiten verwendet werden.

Felder sind in ihrer Layoutkonfiguration flexibler als Zielbereich-Teilformulare; sie sind jedoch an einen einzigen Werttyp gebunden. Sie können ein Feld vergrößern oder auf eine feste Breite und Höhe usw. festlegen. Das aufgelöste Modul- oder Regelergebnis wird in das Feld übertragen.

## Festlegen der Verwendung von Teilformularen und Textfeldern {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Verwenden Sie ein Teilformular, wenn Sie mehrere Modulinhalte in einem vertikalen Textfluss-Layout von oben nach unten (mehrere Absätze oder Bilder) erfassen möchten. Ihr Layout muss die Tatsache handhaben, dass das Teilformular an die Inhaltsgröße angepasst wird. Wenn Sie nicht sicher sein können, dass die Länge des mit dem Teilformular/der Zielgruppe verknüpften Inhalts nie den für das Teilformular im Layout reservierten Platz überschreitet, erstellen Sie das Teilformular als untergeordnetes Element in einem Container mit einem fließenden Teilformular. Dadurch wird sichergestellt, dass Layout-Objekte unterhalb des Teilformulars beim Vergrößern des Teilformulars nach unten fließen.

Verwenden Sie ein Feld, wenn Sie Moduldaten oder Datenwörterbuchelementdaten im Schema Ihres Layouts erfassen möchten (da Felder an Daten gebunden sind) oder um Modulinhalte auf einer Masterseite anzuzeigen. Beachten Sie, dass sich die Position von Inhalten auf einer Masterseite nicht an die Inhalte einer Hauptteilseite anpasst; stellen Sie also sicher, dass ein Bildfeld als Kopfzeilenlogo verwendet wird. Diese Tabelle enthält weitere Kriterien für die Entscheidung, wann ein Teilformular oder ein Feld in einem Layout verwendet werden soll.

<table>
 <tbody>
  <tr>
   <td><p><strong>Voraussetzungen zur Verwendung eines Unterformulars</strong></p> </td>
   <td><p><strong>Voraussetzungen zur Verwendung eines Textfeldes</strong></p> </td>
  </tr>
  <tr>
   <td><p>Es enthält eine Kombination von Elementen, z. B. einen Nachnamen und einen Vornamen</p> </td>
   <td><p>Es enthält ein einzelnes Element, z. B. eine Richtliniennummer.</p> </td>
  </tr>
  <tr>
   <td><p>Es enthält mehrere Absätze</p> </td>
   <td><p>Text wird umschlossen und ausgerichtet</p> </td>
  </tr>
  <tr>
   <td><p>Sich wiederholende, optionale und bedingte Datengruppen sind an Teilformulare gebunden, um das Risiko von Designfehlern zu verringern, die auftreten könnten, wenn Skripte zum Erzielen der gleichen Ergebnisse verwendet werden</p> </td>
   <td><p>Elemente wie das Logo und die Adresse Ihres Unternehmens werden auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt. Erstellen Sie in diesem Fall Formularfelder für diese Elemente und platzieren Sie sie auf der Masterseite. Wenn Sie die Feldbindung auf "Keine Datenbindung"setzen, werden die Felder "Keine Datenbindung"im Brief-/interaktiven Kommunikations-Editor als verknüpfungsfähige Felder angezeigt. Wenn Sie diesen Feldern einen bestimmten Inhaltstyp zuordnen möchten, müssen sie über Bindungen verfügen.</p> <p>Wenn Ihre Firmenadresse mehr als eine Datenzeile enthält, verwenden Sie das Textfeld mit der Option "Mehrere Zeilen zulassen", um die Adresse im Layout darzustellen.</p> <p>Wenn der Datentyp eines Textfelds auf Nur-Text festgelegt ist, wird die Textversion der Modulausgabe anstelle der Rich-Text-Version verwendet (alle Formatierungen werden verworfen). Damit die Formatierung erhalten bleibt, legen Sie für den Datentyp des Textfelds Rich-Text fest.</p> </td>
  </tr>
  <tr>
   <td><p>Textfluss</p> </td>
   <td><p>Textfelder und Bildfelder werden auf Masterseiten verwendet. Masterseiten können keine Teilformulare als Zielbereiche verwenden.</p> </td>
  </tr>
  <tr>
   <td><p>Objekte werden gruppiert und organisiert, ohne das Teilformular an ein Datenelement zu binden</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Innerhalb des Teilformulars befindet sich ein Textfeld. Das Teilformular kann vergrößert werden und darf andere Objekte unterhalb des Layouts nicht überschreiben.</p> </td>
   <td><p>Sie benötigen einfachen Zugriff auf die Daten in der Nachbearbeitung.</p> </td>
  </tr>
 </tbody>
</table>

## Sich wiederholende Elemente einrichten {#setting-up-repetitive-elements}

Wenn Elemente wie das Logo und die Adresse Ihres Unternehmens auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt werden, erstellen Sie Formularfelder für diese Elemente und platzieren Sie sie auf der Masterseite. Nehmen Sie die Bindung für diese Felder über den Feldnamen vor.

## Festlegen des Server-Render-Formats {#specify-the-server-nbsp-render-format}

Verwenden Sie das Server-Renderformat des Layouts in das dynamische XML-Formular. Andernfalls können Briefe/interaktive Kommunikation, die auf diesem Layout basieren, nicht richtig dargestellt werden. Das Server-Renderformat ist in Forms Designer standardmäßig auf das dynamische XML-Formular eingestellt. So stellen Sie sicher, dass Sie das richtige Format verwenden:

* Klicken Sie in Designer auf **Datei** > **Formulareigenschaften** > **Standard**, und vergewissern Sie sich, dass „PDF-Wiedergabeformat“ auf „Dynamisches XML-Formular“ eingestellt ist.
