---
title: Layout-Design
description: In den Layout-Design-Details wird erläutert, wie Sie Layouts für Ihre Briefe oder interaktive Kommunikation erstellen können.
content-type: reference
topic-tags: correspondence-management, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Correspondence Management
exl-id: 9e1b0067-c7dc-4bbb-a209-d674592be858
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2171'
ht-degree: 100%

---

# Layout-Design{#layout-design}

XFA-Formularvorlagen oder XDPs sind die Vorlagen für:

* [Briefe](/help/forms/using/create-letter.md)
* [Druckkanal](/help/forms/using/web-channel-print-channel.md#printchannel) von [Interaktiver Kommunikation](/help/forms/using/interactive-communications-overview.md)

* Layout-Fragmente

Eine XDP wird mit Adobe Forms Designer entwickelt. In diesem Artikel finden Sie Informationen zum Erstellen von XDPs und zum Erstellen einer effektiven Korrespondenz/interaktiven Kommunikation, z. B. wo Formularfelder oder Zielbereiche verwendet werden und wann Layout-Fragmente verwendet werden sollten.

## Erstellen eines Layouts für Briefe oder für den Druckkanal von interaktiver Kommunikation {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Ein Layout bestimmt das grafische Layout eines Briefs/Druckkanals einer interaktiven Kommunikation. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenznummer“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche darstellen. Erstellen Sie das Layout im Formulardesigner. Danach lädt es der Anwendungsspezialist auf den AEM-Server. Dort können Sie das Layout beim Erstellen einer Korrespondenzvorlage oder eines Druckkanals einer interaktiven Kommunikation auswählen.

![Designer: Layout erstellen](assets/claimsubrogationlayout.png)

Führen Sie die folgenden Schritte aus, um Layouts für Briefe/Druckkanäle der interaktiven Kommunikation zu erstellen:

1. Prüfen Sie das Layout und legen Sie den Inhalt fest, der auf allen Seiten wiederholt wird. Normalerweise fallen Seitenkopf und -fußzeile in diese Kategorie. Dieser Inhalt wird auf Layout-Musterseiten hinterlegt. Der restliche Inhalt wird auf Layout-Hauptteilseiten übertragen. In einer Richtlinienhülle können das Logo und die Firmenadresse zur Kopf- und Fußzeile der Musterseite hinzugefügt werden. Dasselbe Layout wird z. B. von der Abbruchsmitteilung genutzt.
1. Unterteilen Sie beim Entwerfen von Hauptteilseiten den Seiteninhalt in Abschnitte. Jeder Abschnitt wird als Teilformular konzipiert, das in das Layout selbst oder als Fragment-Layout eingebettet wird. Wenn der Abschnitt eine Tabelle enthält, modellieren Sie ihn als Layout-Fragment.
1. Ein Layout kann wie folgt gestaltet werden:

   1. Machen Sie jeden Abschnitt zu einem separaten Teilformular, das alle Elemente des Abschnitts enthält.
   1. Machen Sie jeden Abschnitt zu einem untergeordneten Teilformular des gleichen übergeordneten Teilformulars. Das Layout des übergeordneten Teilformulars ist auf „Fluss“ eingestellt, damit die Abschnitte nach unten verschoben werden können, wenn in vorherigen Abschnitten große Datenmengen zusammengeführt werden.
   1. Der primäre Standortabschnitt kann für andere Layouts wiederverwendet werden. Erstellen Sie es als Fragment-Layout.
   1. Die Details des zusätzlichen Abschnitts enthalten nur zwei Elemente, die untereinander platziert sind, können große Daten enthalten und sind als „Fluss“ konzipiert.
   1. Andere Abschnitte enthalten Elemente an bestimmten Positionen und sind somit als positioniertes Layout konzipiert.
   1. Teilen Sie einen Abschnitt in Teilformulare auf, wenn der Abschnitt Elemente an bestimmten Positionen enthält und diese Elemente große Datenmengen umfassen. Ordnen Sie dann die Teilformulare so an, dass das gewünschte Verhalten erzielt wird.
   1. Fügen Sie für den primären Standortabschnitt einen Platzhalter-Zielbereich hinzu. Dieser Platzhalter ist zum Zeitpunkt der Erstellung des Briefs/der interaktiven Kommunikation an den primären Fragmentstandort gebunden.
   1. Laden Sie das Layout (und ggf. das Fragment, das das Layout verwendet) auf den AEM Forms-Server hoch.

### Verwenden eines Teilformulars in einer XDP-Vorlage {#usesubformxdp}

Nachdem Sie das für die Erstellung der interaktiven Kommunikation erforderliche Layout analysiert haben, können Sie mithilfe von Forms Designer Teilformulare in der XDP-Vorlage erstellen. Leere Teilformularkomponenten, die in der XDP-Vorlage verwendet werden, führen zur Anzeige von Zielbereichen im Druckkanal der interaktiven Kommunikation.

>[!NOTE]
>
>Fügen Sie Inhalte zum Druckkanal der interaktiven Kommunikation hinzu, anstatt Inhalte zur Teilformularkomponente in der XDP-Vorlage hinzuzufügen. Fügen Sie den Zielbereichen im Druckkanal mithilfe von [Dokumentfragmenten, Diagrammen, Bildern](create-interactive-communication.md#step2) und Layout-Fragmenten Inhalte hinzu.

Führen Sie die folgenden Schritte durch, um das Teilformular in einer XDP-Vorlage zu verwenden:

1. Öffnen Sie Forms Designer und wählen Sie **Datei** > **Neu** > **Leeres Formular verwenden**, **Weiter** und dann **Beenden**, um das Formular für die Vorlagenerstellung zu öffnen.

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

   Wiederholen Sie die Schritte 2 bis 5, um weitere Teilformulare zur XDP-Vorlage hinzuzufügen. Fügen Sie [Text, Dokumentfragmente, Bilder und Diagramme](create-interactive-communication.md#step2) nur während des Verfassens der interaktiven Kommunikation zu den Zielbereichen hinzu.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie einen Namen für die XDP-Vorlage an.
   1. Wählen Sie aus der Dropdown-Liste **Dateityp** die Option **.xdp** aus.

   1. Wählen Sie **Speichern** aus.

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
   1. Wählen Sie **OK** aus.

1. Wählen Sie **+** im linken Bereich neben dem Namen der Tabelle aus, klicken Sie mit der rechten Maustaste auf die Zellennamen in der Kopfzeile und in anderen Zeilen und wählen Sie **Objekt umbenennen** aus, um die Tabellenzellen umzubenennen.
1. Klicken Sie auf die Textfelder für die Tabellenkopfzeilen in der **Design-Ansicht** und benennen Sie sie um.
1. Ziehen Sie in der **Design-Ansicht** die **Textfeldkomponente** per Drag-and-Drop aus der **Objektbibliothek** auf jede Tabellenzelle. Führen Sie diesen Schritt aus, um Tabellenzellen bei der Erstellung der interaktiven Kommunikation an die Formulardatenmodellobjekte zu binden.

   ![Textfelder in einer Tabelle](assets/text_fields_table_new.png)

1. Klicken Sie auf den Namen der Zeile im linken Bereich und wählen Sie **Objekt** > **Bindung** > **Zeile für jedes Datenelement wiederholen**. Führen Sie diesen Schritt aus, um sicherzustellen, dass die Tabellenzeile für jedes in der Datenbank verfügbare Datenelement automatisch wiederholt wird, wenn eine Bindung zwischen den Tabellenzellen dieser Zeile mit Formulardatenmodellobjekten des Sammlungstyps erstellt wird.

   Geben Sie Text in die Tabellenzellen ein oder [erstellen Sie Bindungen mit Formulardatenmodellobjekten](create-interactive-communication.md#step2) nur während des Verfassens der interaktiven Kommunikation.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen für die XDP-Vorlage an.
   1. Wählen Sie aus der Dropdown-Liste **Dateityp** die Option **.xdp** aus.

   1. Wählen Sie **Speichern** aus.

### Hochladen einer XDP-Vorlage auf den AEM Forms-Server {#uploadxdptemplate}

Nachdem Sie eine XDP-Vorlage mit dem Forms-Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server hochladen, damit die Vorlage beim Erstellen der interaktiven Kommunikation verwendet werden kann.

1. Wählen Sie **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie **Erstellen** > **Datei hochladen** aus.
1. Navigieren Sie zum Speicherort der XDP-Vorlage auf dem lokalen Dateisystem und wählen Sie **Öffnen** aus, um die XDP-Vorlage auf den AEM Forms-Server zu importieren.

## Schema verwenden {#using-schema}

Sie können ein Schema in einem Layout oder Fragment-Layout verwenden. Das ist aber nicht erforderlich. Wenn Sie ein Schema verwenden, stellen Sie Folgendes sicher:

1. Das Layout und alle Fragment-Layouts, die in einem Brief/einer interaktiven Kommunikation verwendet werden, verwenden das gleiche Schema wie der Brief/die interaktive Kommunikation.
1. Alle Felder, die mit Daten gefüllt werden müssen, sind an das Schema gebunden.

## Erstellen verknüpfungsfähiger Felder {#creating-relatable-fields}

Standardmäßig werden alle Felder als verknüpfungsfähig mit vielen anderen Datenquellen betrachtet. Wenn das Layout Felder enthält, die nicht mit einer Datenquelle verknüpfungsfähig sind, fügen Sie den Namen dieser Felder das Suffix „_int“ (intern) hinzu, z. B. „pageCount_int“.

Ein verknüpfungsfähiges Feld muss folgende Voraussetzungen erfüllen:

* es muss ein XFA &lt;field> oder &lt;exclGroup> sein
* Es muss einen XFA-Bindungsverweis haben.
* Wenn es sich um &lt;exclGroup> handelt, muss es über mindestens ein untergeordnetes Feld für ein Optionsfeld verfügen. Andernfalls kann der Werttyp nicht ermittelt werden.

Ein verknüpfungsfähiges Feld muss folgende Voraussetzungen erfüllen:

* Es muss einen Namen haben.

Auf ein verknüpfungsfähiges Feld darf Folgendes nicht zutreffen:

* An den Namen ist das Suffix „_int“ angehängt.
* Im Bindungsfeld ist keine Bindung festgelegt.
* es muss ein untergeordnetes Element eines &lt;exclGroup>-Elements sein

Solange ein verknüpfbares Feld die oben genannten Kriterien erfüllt, kann es sich im Layout an jeder beliebigen Position und in jeder Verschachtelungstiefe befinden. Verknüpfungsfähige Felder lassen sich auf Musterseiten verwenden.

Felder sind in Bezug auf ihre Layout-Konfiguration flexibler als Teilformulare, die als Zielbereich fungieren. Allerdings sind Felder an einen einzigen Werttyp gebunden. Sie können ein Feld in die Breite ziehen oder es mit einer festen Breite oder Höhe einrichten usw. Das aufgelöste Modul- oder Regelergebnis wird im Feld übernommen.

## Wann sollten Teilformulare, wann Felder verwendet werden {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Verwenden Sie ein Teilformular, um Inhalte aus mehreren Modulen in einem von oben nach unten angeordneten, vertikal verlaufenden Layout (mehrere Absätze oder Bilder) zu erfassen. Die Höhe eines Teilformulars nimmt zu, damit es den vorgesehenen Inhalt fassen kann: Achten Sie darauf, dass Ihr Layout damit zurechtkommt. Wenn Sie nicht sicher sein können, dass der mit dem Teilformular/Zielbereich verknüpfte Inhalt niemals mehr Raum einnimmt, als für das Teilformular im Layout vorgesehen ist, erstellen Sie das Teilformular als untergeordnetes Element eines fließenden Teilformular-Containers. Damit stellen Sie sicher, dass Layout-Objekte unterhalb des Teilformulars nach unten rücken, wenn die Höhe des Teilformulars zunimmt.

Verwenden Sie ein Feld, wenn Sie Moduldaten oder Datenlexikonelement-Daten in das Schema Ihres Layouts aufnehmen möchten (da Felder an Daten gebunden sind) oder wenn Modulinhalte auf einer Musterseite angezeigt werden sollen. Beachten Sie, dass sich die Position von Inhalten auf einer Masterseite nicht an die Inhalte einer Hauptteilseite anpasst; stellen Sie also sicher, dass ein Bildfeld als Kopfzeilenlogo verwendet wird. Die folgende Tabelle enthält weitere Kriterien für die Entscheidung, wann ein Teilformular und wann ein Feld im Layout verwendet werden sollte.

<table>
 <tbody>
  <tr>
   <td><p><strong>Voraussetzungen zur Verwendung eines Unterformulars</strong></p> </td>
   <td><p><strong>Voraussetzungen zur Verwendung eines Textfeldes</strong></p> </td>
  </tr>
  <tr>
   <td><p>Es enthält eine Kombination einzelner Elemente, z. B. Vorname und Nachname.</p> </td>
   <td><p>Es enthält ein einzelnes Element, z. B. eine Policennummer.</p> </td>
  </tr>
  <tr>
   <td><p>Es enthält mehrere Absätze.</p> </td>
   <td><p>Text wird umgebrochen und ausgerichtet.</p> </td>
  </tr>
  <tr>
   <td><p>Sich wiederholende, optionale und bedingte Datengruppen sind an Teilformulare gebunden, um das Risiko von Design-Fehlern zu verringern, wie sie auftreten könnten, wenn Sie für dasselbe Ergebnis Skripte verwenden würden.</p> </td>
   <td><p>Elemente wie das Logo und die Adresse Ihres Unternehmens werden auf allen Seiten eines Brief/einer interaktiven Kommunikation angezeigt. Erstellen Sie in einem solchen Fall Formularfelder für die betreffenden Elemente und ordnen Sie die Felder auf der Musterseite an. Wenn Sie das Bindungsfeld auf „Keine Datenbindung“ einstellen, werden im Editor für Briefe/interaktive Kommunikationen keine Felder als verknüpfungsfähig angezeigt. Wenn Sie mit diesen Feldern jedoch bestimmte Inhaltstypen verknüpfen möchten, muss der Bindungstyp im Bindungsfeld entsprechend eingerichtet werden.</p> <p>Wenn die Firmenadresse mehr als eine Datenzeile umfasst, verwenden Sie das Textfeld mit der Option „Mehrere Zeilen zulassen“, um die Adresse im Layout darzustellen.</p> <p>Wenn der Datentyp eines Textfelds auf Nur-Text eingestellt ist, wird die Nur-Text-Version der Modulausgabe anstelle der Rich-Text-Version verwendet (d. h., alle Formatierungen gehen verloren). Wenn die Formatierungen erhalten bleiben sollen, stellen Sie den Datentyp des Textfelds auf Rich-Text ein.</p> </td>
  </tr>
  <tr>
   <td><p>Text wird fortlaufend eingefügt (Textfluss).</p> </td>
   <td><p>Textfelder und Bildfelder werden auf primären Seiten verwendet. Auf primären Seiten können Teilformulare nicht als Zielbereiche verwendet werden.</p> </td>
  </tr>
  <tr>
   <td><p>Objekte werden gruppiert und organisiert, ohne das Teilformular mit einem Datenelement zu verknüpfen.</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Innerhalb des Teilformulars ist ein Textfeld vorhanden.  Das Teilformular kann an Größe zunehmen, ohne darunter angeordnete Layout-Objekte zu überschreiben.</p> </td>
   <td><p>Sie benötigen einen einfachen Zugriff auf die Daten im Nachbearbeitungsprozess.</p> </td>
  </tr>
 </tbody>
</table>

## Einrichten sich wiederholender Elemente {#setting-up-repetitive-elements}

Wenn Elemente wie das Logo und die Adresse Ihres Unternehmens auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt werden, erstellen Sie Formularfelder für diese Elemente und platzieren Sie diese auf der primären Seite.  Nehmen Sie die Bindung für diese Felder über den Feldnamen vor.

## Festlegen des Server-Render-Formats {#specify-the-server-nbsp-render-format}

Verwenden Sie das Server-Render-Format des Layouts für das dynamische XML-Formular. Andernfalls können Briefe/interaktive Kommunikation, die auf diesem Layout basieren, nicht korrekt gerendert werden.  Das Server-Renderformat ist in Forms Designer standardmäßig auf das dynamische XML-Formular eingestellt. Sicherstellen, dass das richtige Format verwendet wird:

* Klicken Sie in Designer auf **Datei** > **Formulareigenschaften** > **Standard**, und vergewissern Sie sich, dass „PDF-Wiedergabeformat“ auf „Dynamisches XML-Formular“ eingestellt ist.
