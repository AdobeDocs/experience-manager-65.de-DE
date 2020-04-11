---
title: Erstellen einer interaktiven Kommunikation
seo-title: Erstellen einer interaktiven Kommunikation
description: Erstellen Sie eine interaktive Kommunikation mit dem Editor für interaktive Kommunikation. Verwenden Sie die Drag-and-Drop-Funktionalität, um die interaktive Kommunikation zu erstellen und eine Vorschau der Druck- und Webausgaben für verschiedene Gerätetypen anzuzeigen.
seo-description: Erstellen Sie eine interaktive Kommunikation mit dem Editor für interaktive Kommunikation. Verwenden Sie die Drag-and-Drop-Funktionalität, um die interaktive Kommunikation zu erstellen und eine Vorschau der Druck- und Webausgaben für verschiedene Gerätetypen anzuzeigen.
uuid: d524a3de-00b4-444f-b3c7-be443fa24ec8
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f4d98cb9-84d8-4735-91d2-b9ceec861e5e
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Erstellen einer interaktiven Kommunikation{#create-an-interactive-communication}

## Übersicht {#overview}

Mit der interaktiven Kommunikation lässt sich die Generierung, Zusammenstellung und Verteilung sicherer, personalisierter und interaktiver Schriftstücke zentralisieren und verwalten. Wenn Sie den Druck als Master-Kanal für das Web verwenden, können Sie die Aufwandsduplikation beim Erstellen der Webausgabe der interaktiven Kommunikation minimieren.

### Voraussetzungen {#prerequisites}

Die folgenden Voraussetzungen sind Voraussetzung für die Erstellung einer interaktiven Kommunikation:

* Richten Sie ein [Formulardatenmodell](/help/forms/using/data-integration.md) ein, das Testdaten oder eine tatsächliche Datenquelle enthält, z. B. eine Instanz von Microsoft® Dynamics.
* Ensure that you have the [Document fragments](/help/forms/using/document-fragments.md).
* Ensure that you have [Templates for print and web channel](/help/forms/using/web-channel-print-channel.md).
* Stellen Sie sicher, dass Sie das erforderliche [Design](/help/forms/using/themes.md) für den Webkanal haben.

## Erstellen einer interaktiven Kommunikation {#createic}

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tap **[!UICONTROL Create]** and select **[!UICONTROL Interactive Communication]**. Die Seite &quot;Interaktive Kommunikation erstellen&quot;wird angezeigt.

   ![create-interactive-communication](assets/create-interactive-communication.png)

1. Geben Sie die folgenden Informationen ein. :

   * **[!UICONTROL Titel]**: Geben Sie den Titel der interaktiven Kommunikation ein.
   * **[!UICONTROL Name]**: Der Name der interaktiven Kommunikation wird aus dem eingegebenen Titel abgeleitet. Bearbeiten Sie ihn gegebenenfalls.
   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung der interaktiven Kommunikation ein.
   * **[!UICONTROL Formulardatenmodell]**: Suchen Sie das Formulardatenmodell und wählen Sie es aus. For more information on Form Data Model, see [AEM Forms Data Integration](/help/forms/using/data-integration.md).

   * **[!UICONTROL Prefill-Dienst]**: Wählen Sie den Dienst zum Vorausfüllen aus, um die Daten abzurufen, und füllen Sie die interaktive Kommunikation im Voraus aus.
   * **[!UICONTROL Nachbearbeitungstyp]**: Sie können AEM- oder Forms-Arbeitsablauf auswählen, der beim Senden der interaktiven Kommunikation ausgelöst werden soll. Wählen Sie den Typ des auszulösenden Workflows aus.

   * **[!UICONTROL Nachbearbeitung]**: Wählen Sie den Namen des Workflows aus, der ausgelöst werden soll. Wenn Sie AEM-Workflow auswählen, geben Sie Anlagenpfad, Layoutpfad, PDF-Pfad, Druckdatenpfad und Webdatenpfad an.
   * **[!UICONTROL Tags]**: Wählen Sie die Tags aus, die auf die interaktive Kommunikation angewendet werden sollen. Sie können auch einen neuen/benutzerdefinierten Tag-Namen eingeben und die Eingabetaste drücken, um ihn zu erstellen.
   * **[!UICONTROL Autor]**: Der Name des Autors wird automatisch aus dem Benutzernamen des angemeldeten Benutzers übernommen.
   * **[!UICONTROL Veröffentlichungsdatum:]** Geben Sie das Datum ein, an dem die interaktive Kommunikation veröffentlicht werden soll.
   * **[!UICONTROL Veröffentlichungsdatum]** rückgängig machen: Geben Sie das Datum ein, ab dem die Veröffentlichung der interaktiven Kommunikation rückgängig gemacht werden soll.

1. Tippen Sie auf **[!UICONTROL Weiter]**. Der Bildschirm zur Angabe von Druck- und Webkanal-Details wird angezeigt.
1. Geben Sie Folgendes ein:

   * **[!UICONTROL Drucken]**: Wählen Sie diese Option, um den Druckkanal der interaktiven Kommunikation zu generieren.
   * **[!UICONTROL Druckvorlage]**: Suchen Sie eine XDP als Druckvorlage und wählen Sie sie aus.
   * **[!UICONTROL Web]**: Wählen Sie diese Option, um den Web-Kanal oder die interaktive Ausgabe der interaktiven Kommunikation zu generieren.
   * **[!UICONTROL Interaktive Kommunikationswebvorlage]**: Suchen und wählen Sie die Webvorlage aus.
   * **[!UICONTROL Design]** und **[!UICONTROL Design]** auswählen: Navigieren Sie zu dem Thema und wählen Sie es aus, um den Web-Kanal der interaktiven Kommunikation zu gestalten. Weitere Informationen finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).

   * **[!UICONTROL Als Master für Web-Kanal]** drucken: Wählen Sie diese Option, um den Web-Kanal synchron mit dem print-Kanal zu erstellen. Die Verwendung des Druckkanals als Master für den Webkanal stellt sicher, dass der Inhalt und die Datenbindung des Webkanals aus dem Druckkanal abgeleitet werden und dass die im Druckkanal vorgenommenen Änderungen im Webkanal widergespiegelt werden können, wenn Sie auf „Synchronisieren“ tippen. Die Autoren dürfen jedoch ggf. die Vererbung für bestimmte Komponenten im Webkanal aufheben. Weitere Informationen finden Sie unter [Synchronisieren des Webkanals mit dem Druckkanal](../../forms/using/create-interactive-communication.md#synchronize).
Wenn Sie die Option &quot;Als Master für Web-Kanal **** drucken&quot;auswählen, können Sie einen der folgenden Modi zum Generieren von Web-Kanal auswählen:

      * **[!UICONTROL Automatisches Layout]**: Wählen Sie diesen Modus aus, um automatisch Platzhalter, Inhalte und Datenbindung für Web Kanal aus dem Print Kanal zu generieren.
      * **[!UICONTROL Manuell organisieren**: Wählen Sie diesen Modus aus, um unter Verwendung des auf der Registerkarte &quot; **[!UICONTROL Datenquellen]** &quot;verfügbaren Hauptinhalts die Elemente &quot;Kanal drucken&quot;manuell auszuwählen und dem Web-Kanal hinzuzufügen. Weitere Informationen finden Sie unter [Wählen Sie Kanal drucken aus, um Webinhalte](#selectprintchannelelements)zu erstellen.
   For more information on print channel and web channel, see [Print channel and web channel](/help/forms/using/web-channel-print-channel.md).

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Die interaktive Kommunikation wird erstellt und ein Warndialog wird angezeigt. Tap **[!UICONTROL Edit]** to start building the contents of the Interactive Communication as explained in [Add contents using Interactive Communication authoring user interface](#step2). Alternatively, you can tap **[!UICONTROL Done]** and choose to edit the Interactive Communication later.

## Fügen Sie der interaktiven Kommunikation Inhalte hinzu {#step2}

Nachdem Sie eine interaktive Kommunikation erstellt haben, können Sie die Authoring-Oberfläche für interaktive Kommunikation verwenden, um deren Inhalte zu erstellen.

For more information on the Interactive Communication authoring interface, see [Introduction to Interactive Communication authoring](/help/forms/using/introduction-interactive-communication-authoring.md).

1. The Interactive Communication authoring interface is launched when you Tap Edit as mentioned in [Create Interactive Communication](#createic). Alternatively, you can navigate to an existing Interactive Communication asset on AEM, select it, and tap **[!UICONTROL Edit]** to launch the Interactive Communication authoring interface.

   Standardmäßig wird der Kanal &quot;Drucken&quot;der interaktiven Kommunikation angezeigt, es sei denn, die interaktive Kommunikation ist nur für Web-Kanal verfügbar. Im Kanal &quot;Drucken&quot;der interaktiven Kommunikation werden Zielgruppen angezeigt, die in der ausgewählten XDP-/Print-Kanal-Vorlage verfügbar sind. In diesen Zielbereichen und Feldern können Sie Komponenten oder Assets hinzufügen.

1. With the Print channel selected, select the **[!UICONTROL Components]** tab. Folgende Komponenten sind im Druckkanal verfügbar:

   | **Komponente** | **Funktion** |
   |---|---|
   | Diagramm | Fügt ein Diagramm hinzu, das Sie in der interaktiven Kommunikation für die visuelle Darstellung zweidimensionaler Daten verwenden können, die aus einer Formulardatenmodellsammlung abgerufen werden. For more information, see [Using charts in Interactive Communications](/help/forms/using/chart-component-interactive-communications.md). |
   | Dokumentfragment | Ermöglicht es Ihnen, einer interaktiven Kommunikation eine wiederverwendbare Komponente wie Text, Liste oder Bedingung hinzuzufügen. Die hinzugefügte Komponente könnte entweder auf einem Formulardatenmodell basieren oder nicht. |
   | Bild | Ermöglicht es Ihnen, ein Bild einzufügen. |

   Ziehen Sie die Komponenten per Drag &amp; Drop in Ihre interaktive Kommunikation und konfigurieren Sie sie nach Bedarf.

   Sie können die Vorgänge &quot;Rückgängig&quot;und &quot;Wiederholen&quot;auch beim Authoring einer interaktiven Kommunikation für Print- und Web-Kanal verwenden.

   Verwenden Sie den Vorgang &quot;Rückgängig&quot;, um die zuletzt ausgeführte Aktion und den Vorgang &quot;Wiederholen&quot;zu verwerfen und die verworfene Aktion erneut zu integrieren. Wenn Sie beispielsweise ein Bild in eine interaktive Kommunikation eingefügt oder eine Datenbindung erstellt haben und es verwerfen müssen, verwenden Sie den Vorgang &quot;Rückgängig&quot;.

   ![Rückgängigmachen von Aktionen](assets/undo_redo_actions_new.png)

   Die Optionen &quot;Rückgängig&quot;und &quot;Wiederholen&quot;werden auf der Symbolleiste der Authoring-Benutzeroberfläche angezeigt. Die Rückgängig-Option wird erst nach Durchführung einer Aktion angezeigt. Die Option &quot;Wiederholen&quot;wird in der Seitensymbolleiste erst angezeigt, nachdem ein Vorgang zum Rückgängigmachen durchgeführt wurde. Diese Aktionen werden beim Aktualisieren der Seite zurückgesetzt.

1. Wenn der Druckkanal ausgewählt ist, wechseln Sie zur Registerkarte **[!UICONTROL Assets]** und wenden Sie den Filter an, um nur die Assets anzuzeigen, die Sie sehen möchten.

   Mithilfe des Assets-Browsers können Sie Assets auch direkt in Bereiche der interaktiven Zielgruppe ziehen und dort ablegen.

   ![assets-documents](assets/assets-docfragments.png)

1. Ziehen Sie die Dokumentfragmente per Drag-and-Drop in die interaktive Kommunikation. Im Folgenden sind die Arten von Dokumentfragmenten aufgeführt, die Sie im Druckkanal der interaktiven Kommunikation verwenden können.

<table>
 <tbody>
  <tr>
   <td><strong>Dokumentfragmenttyp</strong></td>
   <td><strong>Beispielzweck</strong></td>
  </tr>
  <tr>
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Text</a></td>
   <td>Text zum Hinzufügen der Adresse, der E-Mail-Adresse des Empfängers und des Nachrichtentexts des Briefs </td>
  </tr>
  <tr>
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Bedingung</a></td>
   <td>Condition to add the appropriate header image to the communication based on the type of the policy: Standard or Premium. <br /> </td>
  </tr>
  <tr>
   <td>Liste</td>
   <td>Group of document fragments, including text, conditions, other lists, and images. <br /> </td>
  </tr>
 </tbody>
</table>

Sie können die Bindung auch zwischen einem Zielgruppen- und einem Dokument-Fragment ersetzen, indem Sie das neue Fragment auf der Registerkarte &quot; **Assets** &quot;im Bereich &quot;Zielgruppe&quot;ablegen. Die blaue Farbschattierung des Bereichs Zielgruppe beim Ziehen des Fragments zeigt an, dass das Dokument-Fragment in den Bereich Zielgruppe verschoben werden kann.

Weitere Informationen zu Dokumentfragmenten finden Sie unter [Dokumentfragmente](/help/forms/using/document-fragments.md).

Die Authoring-Oberfläche ermöglicht es Ihnen, in einer interaktiven Kommunikation zwischen ungebundenen und gebundenen Feldern und Variablen zu unterscheiden. Die Benutzeroberfläche hebt die ungebundenen Felder und Variablen mit einem orangefarbenen Rahmen hervor.

![unbound_fields_variables_highlight_dc](assets/unbound_fields_variables_highlights_dc.jpg)

Wenn Sie den Mauszeiger über diese Elemente bewegen, wird eine QuickInfo mit der Meldung &quot;Feld&quot;(Ungebunden) oder &quot;Variable&quot;(Ungebunden) angezeigt.

Eine in einem Dokument-Fragment verwendete ungebundene Variable wird in einigen Fällen nicht auf der Authoring-Oberfläche angezeigt. Dies kann durch eine Inline-Textregel in einem Dokument-Fragment oder bei einem Bedingungsfragment geschehen. In diesem Fall wird eine blaue QuickInfo als Teil des Dokument-Fragments angezeigt. Die QuickInfo zeigt die Anzahl der ungebundenen Variablen an, die in einem Dokument-Fragment verwendet werden.

![Ungebundene Variable](assets/df_unbound_variable_new.png)

Tippen Sie auf das Fragment Dokument, dann auf ![configure_icon](assets/configure_icon.png) (Konfigurieren) und dann auf **[!UICONTROL Eigenschaften]** im Sidekick der interaktiven Kommunikation. Im Abschnitt &quot; **[!UICONTROL Variablen und Datenmodellobjekte]** &quot;werden die Variablen, einschließlich der ausgeblendeten Variablen, und die Datenmodellobjekte, die in den Dokument-Fragmenten verwendet werden, Liste. Verwenden Sie das Symbol zum ![Bearbeiten](assets/edit.svg) (Bearbeiten) neben jedem Datenmodellobjekt oder jeder Datenvariablen, um die Eigenschaften zu bearbeiten.

1. To set up binding of variables, tap a variable and select ![configure_icon](assets/configure_icon.png) (Configure) and then set up the binding properties in the Properties panel in the sidebar.

   * **Keine:** Agent füllt hier den Wert für die Variable aus.
   * **Textfragment**: Wenn ausgewählt, können Sie ein Textdokumentfragment durchsuchen und auswählen, dessen Inhalt in dem Feld gerendert wird. Nur die Textdokumentfragmente können an Variablen gebunden werden, die keine Variablen enthalten.
   * **Datenmodellobjekt**: Wählen Sie eine Formulardatenmodell-Eigenschaft aus, deren Wert in das Feld gefüllt wird.
   * **Standardwert:** In diesem Feld können Sie einen Standardwert für die Variable definieren. Der Wert wird angezeigt, wenn Sie die Interaktive Kommunikation oder die Agent-Benutzeroberfläche Vorschau haben.
   * **Anzeigemuster:** Sie können auch ein Anzeigeformat für eine Variable definieren. Wählen Sie eine der vordefinierten Optionen aus der Dropdown-Liste &quot; **Typ** &quot;aus, um ein Anzeigeformat auf eine Variable anzuwenden. Wählen Sie **Benutzerdefiniert** , um ein Anzeigemuster zu definieren, das in der Liste nicht verfügbar ist. Weitere Informationen finden Sie unter [Datenanzeigemuster](../../forms/using/create-interactive-communication.md#datadisplaypatterns).
   Navigieren Sie zu [Variablen und Datenmodellobjekte](../../forms/using/create-interactive-communication.md#hiddenvariables) , um die Bindung ausgeblendeter Variablen im Dokument-Fragment einzurichten.

   Sie können auch Datenquellenelemente oder Textvariablen per Drag &amp; Drop verschieben, um die Variablenbindung einzurichten.  Um eine Bindung mit einem der Datenquellenelemente zu erstellen, wählen Sie die Registerkarte &quot; **Datenquellen** &quot;und ziehen Sie das Element in den Variablennamen. Das Datenquellenelement und die Variable müssen vom gleichen Typ sein, damit die Bindung erfolgreich eingerichtet werden kann. Wenn Sie ein Datenquellenelement auf eine bereits gebundene Variable ziehen und dort ablegen, ersetzt das neue Element das vorherige, um eine neue Bindung mit der Variablen zu erstellen. Wählen Sie auf ähnliche Weise die Registerkarte &quot; **Assets** &quot;und ziehen Sie das Textfragment &quot;Dokument&quot;in den Variablennamen, um die Bindung zwischen ihnen einzurichten. Das Textvariablen-Dokument-Fragment darf keine Variablen enthalten.

1. Um eine Tabelle hinzuzufügen, verwenden Sie bei ausgewähltem Druckkanal auf der Registerkarte **[!UICONTROL Assets]** den Filter, um nur die Layout-Fragmente anzuzeigen. Ziehen Sie das gewünschte Layoutfragment per Drag-and-Drop in die interaktive Kommunikation. Ein Layout-Fragment basiert auf einer XDP und kann verwendet werden, um grafische Layouts oder statische und dynamische Tabellen in der interaktiven Kommunikation zu erstellen, die mit dynamischen Daten gefüllt werden.

   Beispiel: Eine Layout-Tabelle zur Anzeige von Bruttoprämie, Treuerabatt % und Notfall-Pannenhilfe für alte und neue Richtlinien.

   Weitere Informationen zu Layout-Fragmenten finden Sie unter [Dokumentfragmente](/help/forms/using/document-fragments.md).

1. Verwenden Sie bei ausgewähltem Druckkanal auf der Registerkarte **[!UICONTROL Assets]** den Filter, um Bilder anzuzeigen. Ziehen Sie die erforderlichen Bilder per Drag &amp; Drop in die interaktive Kommunikation, z. B. für das Logo &quot;Firma&quot;.

   Verwalten Sie außerdem Folgendes in der interaktiven Kommunikation:

   * [Hinzufügen und Konfigurieren von Diagrammen](/help/forms/using/chart-component-interactive-communications.md)
   * [Synchronisieren des Webkanals mit dem Druckkanal](../../forms/using/create-interactive-communication.md#synchronize)

      * Autom. Synchronisierung
      * Vererbung abbrechen
      * Vererbung erneut aktivieren
      * Synchronisieren
   * [Anlagen und Bibliothekszugriff](../../forms/using/create-interactive-communication.md#attachmentslibrary)
   * [XDP-/Layout-Feldeigenschaften](../../forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Fügen Sie Regeln zu Komponenten hinzu](../../forms/using/create-interactive-communication.md#rules)


1. Switch to **[!UICONTROL Web Channel]**. Der Web-Kanal wird im Editor für interaktive Kommunikation angezeigt. Wenn Sie zum ersten Mal vom Print-Kanal zum Web-Kanal wechseln, erfolgt die automatische Synchronisierung. For more information, see [Synchronizing web channel from the print channel](../../forms/using/create-interactive-communication.md#synchronize).

   Da wir in diesem Beispiel Druck als Master für das Web verwenden, werden die Platzhalter, der Inhalt und die Datenbindung des Druckkanals mit dem Webkanal synchronisiert. Sie können jedoch den jeweiligen Inhalt im Web Kanal ändern und anpassen. [Die Vererbung](../../forms/using/create-interactive-communication.md#main-pars-header-103384010) für die Zielgruppen und Variablen abbrechen, die mit dem Kanal &quot;Drucken&quot;generiert wurden, um Inhalte anpassen zu können.

   ![webchannelAssets](assets/webchannelassets.png)

   Tippen Sie auf das Fragment Dokument, dann auf ![configure_icon](assets/configure_icon.png) (Konfigurieren) und dann auf **[!UICONTROL Eigenschaften]** im Sidekick der interaktiven Kommunikation. Im Abschnitt &quot; **[!UICONTROL Variablen und Datenmodellobjekte]** &quot;werden die Variablen, einschließlich der ausgeblendeten Variablen, und die Datenmodellobjekte, die in den Dokument-Fragmenten verwendet werden, Liste. Verwenden Sie das Symbol zum ![Bearbeiten](assets/edit.svg) (Bearbeiten) neben jedem Datenmodellobjekt oder jeder Datenvariablen, um die Eigenschaften zu bearbeiten. Darüber hinaus können Sie für Dokument-Fragmente, die mit Print Kanal in Web Kanal [automatisch generiert](../../forms/using/create-interactive-communication.md#main-pars-header-1213963149) wurden, neben jedem Datenmodellobjekt und jeder Datenvariable das Symbol ![](assets/cancelinheritance.png) (Vererbung abbrechen) verwenden, um die Vererbung zu [beenden und zu bearbeiten](../../forms/using/create-interactive-communication.md#main-pars-header-103384010) .

1. Um weitere Komponenten im Webkanal hinzuzufügen, tippen Sie bei dem ausgewählten Webkanal auf **[!UICONTROL Komponenten]**. Ziehen Sie Komponenten nach Bedarf per Drag &amp; Drop in den Web-Kanal Ihrer interaktiven Kommunikation und konfigurieren Sie sie.

   | Komponenten | Funktion |
   |---|---|
   | Diagramm | Fügt ein Diagramm hinzu, das Sie in der interaktiven Kommunikation für die visuelle Darstellung zweidimensionaler Daten verwenden können, die aus einer Formulardatenmodellsammlung abgerufen werden. For more information, see [Using chart component](../../forms/using/chart-component-interactive-communications.md). |
   | Dokumentfragment | Ermöglicht das Hinzufügen einer wiederverwendbaren Komponente, eines Textes, einer Liste oder einer Bedingung zu einer interaktiven Kommunikation. Die wiederverwendbare Komponente, die Sie einer interaktiven Kommunikation hinzufügen, kann entweder auf Formulardatenmodellen oder ohne Formulardatenmodell basieren. |
   | Bild | Ermöglicht es Ihnen, ein Bild einzufügen. |
   | Fenster | Damit können Sie der interaktiven Kommunikation ein [Bedienfeld](../../forms/using/create-interactive-communication.md#add-panel-component-to-the-web-channel) hinzufügen. |
   | Tabelle | Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. |
   | Zielbereich | Fügt einen Zielbereich in einen Webkanal ein, um die webkanalspezifischen Komponenten zu organisieren. Zielbereich ist ein einfacher Container, in dem Sie webkanalspezifische Komponenten gruppieren können. |
   | Text | Fügt dem Webkanal einer interaktiven Kommunikation Rich Text hinzu. Text kann auch Formulardatenmodellobjekte verwenden, um den Inhalt dynamisch zu gestalten. |
   | Schaltfläche | Damit können Sie der interaktiven Kommunikation eine [Schaltfläche](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) hinzufügen. Mit der Schaltflächenkomponente können Sie zu anderen interaktiven Mitteilungen, adaptiven Formularen, anderen Assets wie Bildern oder Fragmenten eines Dokuments oder zu einer externen URL navigieren. |
   | Trennzeichen | Ermöglicht das Einfügen einer horizontalen Linie in eine interaktive Kommunikation. Verwenden Sie diese Komponente, um zwischen Abschnitten in einer Korrespondenz zu unterscheiden. Beispielsweise können Sie mit der Komponente &quot;Trennzeichen&quot;zwischen den Abschnitten &quot;Kundendetails&quot;und &quot;Kreditkartendetails&quot;in einem Kreditkartenauszug unterscheiden. |

1. Fügen Sie nach Bedarf Assets in Ihren Webkanal ein.

   You can [preview your Interactive Communication](#previewic) to see what the print and web outputs of the Interactive Communication look like and continue making changes, as required.

## Interaktive Kommunikation in der Vorschau anzeigen {#previewic}

You can use the **Preview option** to evaluate appearance of the Interactive Communication. Der Web-Kanal der interaktiven Kommunikation bietet außerdem eine Option, um die Interaktive Kommunikation für verschiedene Geräte zu emulieren. Beispiel: iPhone, iPad und Desktop. You can use both **Preview** and **Emulator** ![ruler](assets/ruler.png) options in conjunction with each other to preview the web outputs for devices of different screen sizes. Die Musterdaten in der Vorschau werden vom angegebenen Formulardatenmodell ausgefüllt.

1. Wählen Sie den (Druck- oder Web-)Kanal aus, um eine Vorschau anzuzeigen und auf die Vorschau zu tippen. Die interaktive Kommunikation wird angezeigt.

   >[!NOTE]
   >
   >Die Vorschau wird mit den Beispieldaten des Formulardatenmodells befüllt. For more information on previewing the Interactive Communication with some other data or using the prefill service, see [Use form data model](/help/forms/using/using-form-data-model.md) and [Work with form data model](/help/forms/using/work-with-form-data-model.md).

1. For the web channel, use ![ruler](assets/ruler.png) to view how the Interactive Communication looks on various devices.

   ![webchannel-preview](assets/webchannelpreview.png)

Further, you can [Prepare and send Interactive Communication using the Agent UI](/help/forms/using/prepare-send-interactive-communication.md).

## Configure properties in Interactive Communication  {#configure-properties-in-interactive-communication}

### Anlagen und Bibliothekszugriff {#attachmentslibrary}

Im Druckkanal können Sie die Anhänge und den Bibliothekszugriff so konfigurieren, dass der Agent Anlagen in der Benutzeroberfläche für Agenten für die interaktive Kommunikation verwalten kann:

1. Markieren Sie im Druckkanal den Dokumentcontainer und tippen Sie auf **Eigenschaften**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   Der Bereich „Eigenschaften“ wird in der Seitenleiste angezeigt.

   ![propertiesAnlagen](assets/propertiesattachments.png)

1. Erweitern Sie **Anlagen** und geben Sie folgende Eigenschaften an:

   * **[!UICONTROL Bibliothekszugriff zulassen]**: Wählen Sie diese Option, um den Bibliothekszugriff für den Agenten in der Benutzeroberfläche für Agenten zu aktivieren. Wenn diese Option aktiviert ist, kann der Agent während der Vorbereitung der interaktiven Kommunikation Dateien aus der Bibliothek hinzufügen.
   * **[!UICONTROL Neuanordnung von Anlagen zulassen]**: Wählen Sie diese Option, damit der Agent die Anlagen mit der interaktiven Kommunikation neu ordnen kann.
   * **[!UICONTROL Maximale Anzahl der zulässigen Anlagen]**: Geben Sie die maximale Anzahl der Anhänge an, die mit der interaktiven Kommunikation zulässig sind.
   * **[!UICONTROL Anzuhängende]** Dateien: Tippen Sie auf **[!UICONTROL Hinzufügen]** , wählen Sie die anzuhängenden Dateien aus und geben Sie Folgendes an:

      * **[!UICONTROL Diese Datei standardmäßig an das Dokument anhängen]**: Sie können diese Option ändern, wenn nur der Anhang nicht zwingend ist.
      * **[!UICONTROL Obligatorisch:]** Der Agent kann den Anhang nicht in der Benutzeroberfläche für Agenten entfernen.
   ![Anlagen](assets/attachfiles.png)

1. Tippen Sie auf **[!UICONTROL Fertig]**.

### XDP-/Layout-Feldeigenschaften {#xdplayoutfieldproperties}

1. While editing the Print channel of an Interactive Communication, hover over a field, which is built in the Print channel template, and select ![configure_icon](assets/configure_icon.png) (Configure).

   Das Dialogfeld „Eigenschaften“ wird in der Seitenleiste angezeigt.

   ![data_display_patterns_fields](assets/data_display_patterns_fields.jpg)

1. Geben Sie Folgendes an:

   * **[!UICONTROL Name]**: JCR Knotenname.
   * **[!UICONTROL Titel]**: Geben Sie einen Titel ein, der für den Agenten in der Benutzeroberfläche für Agenten und in der Struktur des Dokumentcontainers sichtbar ist.
   * **[!UICONTROL Bindungstyp]**: Wählen Sie einen der folgenden Bindungstypen für das Feld aus.

      * Keine: Agent füllt den Wert für die Eigenschaft aus.
      * Textfragment: Wenn ausgewählt, können Sie ein Textdokumentfragment durchsuchen und auswählen, dessen Inhalt in dem Feld gerendert wird. Alternativ können Sie das Textfeldfragment per Drag &amp; Drop in den Feldnamen ziehen, um die Bindung zwischen ihnen einzurichten. Das Textvariablen-Dokument-Fragment darf keine Variablen enthalten.
      * Datenmodellobjekt: Wählen Sie eine Formulardatenmodell-Eigenschaft aus, deren Wert in das Feld gefüllt wird. Alternativ können Sie die Registerkarte &quot; **Datenquellen** &quot;auswählen und die Eigenschaft per Drag &amp; Drop in das Feld ziehen.
   * **[!UICONTROL Standardwerte]**: Der Standardwert stellt sicher, dass das Feld nicht leer ist, wenn vom angegebenen Datenmodellobjekt oder Textfragment kein Wert bereitgestellt wird. Wenn der Datenbindungstyp „Keine“ ist, wird der Standardwert im Feld vorbefüllt.
   * **[!UICONTROL Anzeigemuster]**: Sie können auch ein Anzeigeformat für ein Feld definieren. Wählen Sie eine der vordefinierten Optionen aus der Dropdown-Liste &quot; **Typ** &quot;aus, um ein Anzeigeformat auf ein Feld anzuwenden. Wählen Sie **Benutzerdefiniert** , um ein Anzeigemuster zu definieren, das in der Liste nicht verfügbar ist. Weitere Informationen finden Sie unter [Datenanzeigemuster](../../forms/using/create-interactive-communication.md#datadisplaypatterns)

   * **[!UICONTROL Bearbeitbar nach Agent]**: Wählen Sie diese Option aus, damit der Agent den Wert in dem Feld in der Benutzeroberfläche für Agenten bearbeiten kann. Diese Einstellung ist nicht anwendbar, wenn der Bindungstyp „Textfragment“ ist.
   * **[!UICONTROL Beschriftung:]** Geben Sie eine Textzeichenfolge ein, die in dem Feld in der Benutzeroberfläche für Agenten angezeigt wird. Diese Einstellung ist nicht anwendbar, wenn der Bindungstyp „Textfragment“ ist.
   * **[!UICONTROL QuickInfo]**: Geben Sie eine Textzeichenfolge ein, die beim Bewegen der Maus über den Agent in der Agent-Benutzeroberfläche sichtbar ist. Diese Einstellung ist nicht anwendbar, wenn der Bindungstyp „Textfragment“ ist.
   * **[!UICONTROL Erforderlich:]** Wählen Sie diese Option, um das Feld zu einem Pflichtfeld für den Agenten zu machen. Diese Einstellung ist nicht anwendbar, wenn der Bindungstyp „Textfragment“ ist.
   * **[!UICONTROL Mehrere Zeilen zulassen]**: Wählen Sie dieses Feld aus, um mehrere Textzeilen als Eingabe in das Feld zuzulassen. Diese Einstellung ist nicht anwendbar, wenn der Bindungstyp „Textfragment“ ist.


1. Tippen Sie auf ![done_icon](assets/done_icon.png).

### Datenanzeigemuster {#datadisplaypatterns}

Auf der Authoring-Oberfläche können Sie Anzeigemuster für Felder, Variablen und Formulardatenmodellelemente definieren, die beim Erstellen einer interaktiven Kommunikation für Druck- und Web-Kanal verfügbar sind.

Um das Datenanzeigemuster zu konfigurieren, tippen Sie auf das Element, wählen Sie &quot; ![configure_icon](assets/configure_icon.png) &quot;(Konfigurieren) und richten Sie das Anzeigemuster im Bedienfeld &quot; **[!UICONTROL Eigenschaften]** &quot;in der Seitenleiste ein. Wählen Sie eine vordefinierte Option aus der Dropdown-Liste &quot; **[!UICONTROL Typ]** &quot;aus, um das mit dem ausgewählten Typ verknüpfte Muster Ansicht. Wählen Sie **[!UICONTROL Benutzerdefiniert]** aus der Dropdown-Liste **[!UICONTROL Typ]** , um ein Muster zu definieren, das in der Liste nicht verfügbar ist. Beim Bearbeiten von Werten im Feld **[!UICONTROL Muster]** wird der Typ automatisch in **[!UICONTROL Benutzerdefiniert]** geändert.

Um das Anzeigemuster anzuwenden, muss die Anzahl der im Feld &quot;Muster&quot;definierten Zeichen oder Ziffern mit den im Wert für Felder, Variablen und Formulardatenmodellelemente definierten Zeichen oder Ziffern übereinstimmen oder darüber hinausgehen. For more information, see [example](../../forms/using/create-interactive-communication.md#greaternumberofdigits).

![data_display_pattern_example](assets/data_display_patterns_ssn_new.png)

Sie können das Anzeigemuster für ein field-, variable- oder form data model-Element neu definieren, nachdem Sie Webinhalte aus dem Print-Kanal generiert haben. Daher kann ein Element unterschiedliche Anzeigemuster für Druck- und Web-Kanal haben. Wenn Sie kein Anzeigemuster für ein Kanal in Print definieren und Webinhalt mit dem Kanal &quot;print&quot;automatisch generieren, definiert die für das Element definierte Datenbindung die in der Dropdown-Liste &quot; **[!UICONTROL Typ]** &quot;verfügbaren Anzeigemuster-Optionen. Wenn für das Element keine Bindung definiert ist, definiert der Datentyp des Elements die verfügbaren Anzeigemuster-Optionen. Wenn Sie z. B. eine Datenbindung vom Typ &quot;Number&quot;für ein Kanal in Print erstellen, sind die in der Dropdown-Liste &quot; **[!UICONTROL Typ]** &quot;verfügbaren Anzeigemuster vom Typ &quot;Number&quot;in verschiedenen Formaten verfügbar.

Wechseln Sie zum **Vorschau** -Modus oder öffnen Sie die Agent-Benutzeroberfläche, um das Anzeigemuster, das auf diese Elemente angewendet wird, Ansicht.

In der folgenden Tabelle finden Sie eine Liste der Werte, die beim Festlegen des Datenanzeigemusters für eine Variable angezeigt werden:

| Typ | Standardwert | Anzeigemuster | Anzeigewert | Beschreibung |
|---|---|---|---|---|
| Sozialversicherungsnummer | 123456789 | text{999-99-9999} | 123-45-6789 | Die Anzahl der Ziffern im Feld mit dem Standardwert stimmt mit der Anzahl der Ziffern im Feld Muster überein. Der auf dem Muster basierende Wert wird erfolgreich angezeigt. |
| Sozialversicherungsnummer | 1234567 | text{999-99-9999} | 1-23-4567 | Die Anzahl der Ziffern im Feld mit dem Standardwert ist kleiner als die Anzahl der Ziffern im Feld Muster. Das Muster gilt für die 7 verfügbaren Stellen. |
| Sozialversicherungsnummer | 1234567890 | text{999-99-9999} | 1234567890 | Die Anzahl der Ziffern im Feld mit dem Standardwert ist größer als die Anzahl der Ziffern im Feld Muster. Daher gibt es keine Änderung des Anzeigewerts. |

Wenn für eine Variable oder ein Formulardatenmodellelement kein Anzeigemuster angegeben ist, wird standardmäßig die [Konfiguration](https://helpx.adobe.com//experience-manager/6-5/forms/using/interactive-communication-configuration-properties.html) des globalen Dokuments verwendet.

Wenn Sie kein Anzeigemuster auf eine Variable des Datentyps Nummer anwenden, zeigt die Vorschau Drucken das Muster entsprechend der Konfiguration des globalen Dokument-Fragments an. Wenn Sie Änderungen an der Standardkonfiguration für das globale Dokument-Fragment vornehmen, zeigt die Agent-Benutzeroberfläche das Muster weiterhin gemäß den für das Gebietsschema definierten Standardtrennzeichen an.

Bei Feldern, in denen kein Anzeigemuster angegeben ist, wird das beim Erstellen der Druckvorlage (XDP) definierte Muster auf das Feld angewendet. Wenn beim Erstellen der Druckvorlage kein Muster vorhanden ist, werden die auf XFA-Spezifikationen basierenden Standardmuster auf die Felder angewendet.

Wenn das angegebene Anzeigemuster nicht korrekt ist oder nicht angewendet werden kann, werden die auf XFA-Spezifikationen basierenden Standardmuster auf die Felder, Variablen oder Formulardatenmodellelemente angewendet.

## Regeln auf interaktive Kommunikationskomponenten anwenden {#rules}

To conditionalize components or content in the interactive communcation, tap the component/piece of content and select ![createruleicon](assets/createruleicon.png) (Create Rule) to launch Rule Editor.

Weitere Informationen finden Sie unter:

* [Regeleditor](/help/forms/using/rule-editor.md)
* [Einführung in das Authoring interaktiver Kommunikation](/help/forms/using/introduction-interactive-communication-authoring.md)

## Tabellen verwenden {#tables}

### Dynamische Tabellen in interaktiver Kommunikation {#dynamic-tables-in-interactive-communication}

Sie können dynamische Tabellen in der interaktiven Kommunikation mithilfe von Layout-Fragmenten hinzufügen. In den folgenden Schritten wird anhand eines Beispiels einer Kreditkartenabrechnung die Verwendung eines Layout-Fragments zum Erstellen einer dynamischen Tabelle in einer interaktiven Kommunikation veranschaulicht.

1. Stellen Sie sicher, dass das erforderliche Layout-Fragment zum Erstellen der Tabelle in AEM verfügbar ist.
1. Ziehen Sie im Kanal &quot;Drucken&quot;Ihrer interaktiven Kommunikation ein Layout-Fragment (mit einer mehrspaltigen Tabelle) aus dem Asset-Browser in einen Zielgruppe-Bereich.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Eine Tabelle wird im Layout-Bereich der interaktiven Kommunikation angezeigt.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Geben Sie die Datenbindung für jede Zelle der Tabelle an. Um eine wiederholbare Zeile zu erstellen, fügen Sie die Eigenschaften des Formulardatenmodells in die Zeile ein, die zu einer allgemeinen Sammlungseigenschaft gehört.

   1. Tap a cell in the table and select ![configure_icon](assets/configure_icon.png) (Configure).

      Das Dialogfeld „Eigenschaften“ wird in der Seitenleiste angezeigt.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Konfigurieren Sie die Eigenschaften:

      * **[!UICONTROL Name]**: JCR Knotenname.
      * **[!UICONTROL Titel]**: Geben Sie einen Titel ein, der im Editor für interaktive Kommunikation angezeigt werden soll.
      * **[!UICONTROL Bindungstyp]**: Wählen Sie einen der folgenden Bindungstypen für das Feld aus.

         * **[!UICONTROL Keine]**
         * **[!UICONTROL Datenmodellobjekt]**: Der Wert einer Formulardatenmodelleigenschaft wird im Feld ausgefüllt. Alternativ können Sie die Registerkarte &quot; **Datenquellen** &quot;auswählen und die Eigenschaft per Drag &amp; Drop in das Feld ziehen.
      * **[!UICONTROL Datenmodellobjekt]**: Die Formulardatenmodelleigenschaft, deren Wert im Feld gefüllt wird.
      * **[!UICONTROL Standardwert]**: Der Standardwert stellt sicher, dass das Feld nicht leer ist, wenn kein Wert vom angegebenen Datenmodellobjekt bereitgestellt wird. Der Standardwert wird im Feld vorbefüllt.

      * **[!UICONTROL Bearbeitbar nach Agent]**: Wählen Sie diese Option aus, damit der Agent den Wert in dem Feld in der Benutzeroberfläche für Agenten bearbeiten kann.
   1. Tippen Sie auf ![done_icon](assets/done_icon.png).



1. Vorschau der interaktiven Kommunikation, um die mit den Daten wiedergegebene Tabelle anzuzeigen.

   ![lf_Vorschau](assets/lf_preview.png)

### Nur Webkanal-Tabellen {#webchanneltables}

Tippen Sie auf das Stammbedienfeld in der Webvorlage und dann auf **+** , um der interaktiven Kommunikation eine **Tabellenkomponente** hinzuzufügen. Eine Tabelle mit zwei Zeilen wird in die interaktive Kommunikation eingefügt. Die erste Zeile der Tabelle stellt die Kopfzeile der Tabelle dar.

#### Zeilen und Spalten in der Tabelle Hinzufügen {#addrowscolumnstable}

**So fügen Sie Spalten hinzu oder löschen sie:**

1. Tippen Sie auf das Standardtextfeld in der Tabellenüberschriftenzeile, um die Komponentensymbolleiste Ansicht.
1. Wählen Sie **Hinzufügen Spalte** bzw. Spalte **löschen** , um Tabellenspalten hinzuzufügen bzw. zu löschen.

![component_toolbar_table1](assets/component_toolbar_table1.png)

**So fügen Sie Zeilen hinzu oder löschen sie:**

1. Tippen Sie auf eine der Tabellenzeilen, um die Komponentensymbolleiste Ansicht. Sie können Tabellenzeilen auch über den Browser &quot;Inhalt&quot;im Sidekick der interaktiven Kommunikation auswählen.
1. Wählen Sie **Hinzufügen Zeile** bzw. **Zeile** löschen, um Tabellenzeilen hinzuzufügen bzw. zu löschen. Verwenden Sie die in der Symbolleiste verfügbaren Optionen **&quot;Nach oben** &quot;und &quot;Nach unten **** &quot;zum Neuanordnen der Tabellenzeilen.

![Komponentensymbolleiste](assets/component_toolbar_table_row_new.png)

**A.** Hinzufügen Zeile **B.** Löschen Sie Zeile **C.** Nach oben **D.** Nach unten

#### Hinzufügen oder Bearbeiten von Text in Tabellenzellen {#addedittexttable}

1. Wählen Sie das Standardtextfeld in der Tabellenzelle aus und tippen Sie auf ![](assets/edit.png) (Bearbeiten).
1. Geben Sie den Text in die Tabellenzelle ein und tippen Sie auf , ![](assets/done_icon.png) um ihn zu speichern.

#### Erstellen von Bindungen zwischen Tabellenzellen und Datenmodellobjektelementen {#createbindingtablecells}

1. Wählen Sie das Standardtextfeld in der Tabellenzeile aus und tippen Sie auf ![](assets/edit.png) (Bearbeiten).
1. Tippen Sie auf die Dropdown-Liste &quot;Datenmodellobjekte&quot;und wählen Sie die Eigenschaft aus.
1. Tippen Sie auf , um eine Bindung zwischen der Tabellenzelle und der Objekteigenschaft des Datenmodells zu speichern und zu erstellen.

![Datenbindung erstellen](assets/create_data_binding_table_new.png)

#### Erstellen eines Hyperlinks für Text in der Tabellenzelle {#createhyperlinktable}

1. Wählen Sie das Standardtextfeld in der Tabellenzelle aus und tippen Sie auf ![](assets/edit.svg) (Bearbeiten).
1. Wählen Sie den Text in der Tabellenzelle aus und tippen Sie auf das Hyperlink-Symbol.
1. Specify the URL in the **Path** field.
1. Tap ![](assets/done_icon.png) to save the hyperlink properties.

![Hyperlink erstellen](assets/create_hyperlink_table_new.png)

#### Erstellen dynamischer Tabellen {#createdynamictables}

Sie können in einer interaktiven Kommunikation eine nur für Web-Kanal dynamische Tabelle mit einer Datenmodelleigenschaft der Typerfassung erstellen. Eine solche Tabelle stellt die untergeordneten Eigenschaften einer Sammlungseigenschaft dar. Sie können nur die Formatierungseigenschaften der verschiedenen Zellen in der Tabelle bearbeiten.

1. Wechseln Sie zum Web-Kanal und wählen Sie dann die Anzeige des Datenquellen-Browsers.
1. Ziehen Sie ein Sammlungseigenschaft in ein Teilformular. Eine Tabelle wird im Teilformular erstellt.
1. Zeigen Sie die Tabelle in der Webvorschau der interaktiven Kommunikation in der Vorschau an.

#### Spalten in einer Tabelle sortieren {#sortcolumns}

Sie können Daten auf Grundlage einer beliebigen Spalte in einer Tabelle in der interaktiven Kommunikation sortieren. Die Werte in der Spalte können in auf- oder absteigender Reihenfolge sortiert werden.

Die Sortierung kann auf Tabellenspalten mit folgenden Elementen angewendet werden:

* Statischer Text
* Datenmodell, Objekteigenschaften
* Kombination von statischen Text- und Datenmodellobjekteigenschaften

So aktivieren Sie die Sortierung:

1. Select the table and tap ![](assets/configure_icon.png) (Configure). Sie können die Tabelle auch über den Browser &quot; **Inhalt** &quot;im Sidekick der interaktiven Kommunikation auswählen.
1. Wählen Sie Sortierung **aktivieren.**
1. Tap ![](assets/done_icon.png) to save the table properties. Die Sortiersymbole (Auf- und Ab-Pfeile) in Spaltenüberschriften zeigen an, dass die Sortierung aktiviert wurde.

   ![Sortieren aktivieren](assets/enable_sorting_new-1.png)

1. Wechseln Sie zum **Vorschau** -Modus, um die Ausgabe Ansicht. Die Tabelle wird automatisch nach der ersten Spalte der Tabelle sortiert.
1. Klicken Sie auf die Spaltenüberschrift, um die Werte anhand der Spalte zu sortieren.

   Eine Spaltenüberschrift mit einem Pfeil nach oben stellt Folgendes dar:

   * -Tabelle wird basierend auf dieser Spalte sortiert.
   * Werte in der Spalte werden in aufsteigender Reihenfolge angezeigt.
   ![Aufsteigende Sortierung](assets/sorting_ascending_new-1.png)

   Gleichermaßen stellt eine Spaltenüberschrift mit einem Pfeil nach unten dar, dass die Werte in der Spalte in absteigender Reihenfolge angezeigt werden.

## Eigenschaften interaktiver Kommunikation bearbeiten {#edit-interactive-communication-properties}

Nachdem Sie eine interaktive Kommunikation erstellt haben, können Sie deren Eigenschaften zu einem späteren Zeitpunkt bearbeiten.

Verwenden Sie die Seite **Eigenschaften** , um:

* Bearbeiten Sie Werte für die Felder, die beim Erstellen der interaktiven Kommunikation angegeben werden, z. B. Titel und Beschreibung.
* Hinzufügen oder löschen Sie Web Kanal für eine vorhandene interaktive Kommunikation.
* Vorschau, Herunterladen oder Löschen interaktiver Kommunikation
* Öffnen Sie die [Agent-Benutzeroberfläche](/help/forms/using/prepare-send-interactive-communication.md).

So greifen Sie auf die Seite **Eigenschaften** zu:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie die interaktive Kommunikation und klicken Sie auf **Eigenschaften**.
1. Klicken Sie auf die Registerkarte &quot; **Allgemein** &quot;, um die Felder &quot; **Titel** &quot;und &quot; **Beschreibung** &quot;zu bearbeiten.

### Hinzufügen oder löschen Sie den Web-Kanal {#add-or-delete-the-web-channel}

Führen Sie die folgenden Schritte aus, um den Web-Kanal für eine vorhandene interaktive Kommunikation hinzuzufügen:

1. Wählen Sie auf der Seite &quot; **Eigenschaften** &quot;die Registerkarte &quot; **Kanal** &quot;aus.
1. Aktivieren Sie das Kontrollkästchen &quot; **Web** &quot;und wählen Sie eine Vorlage für den Web-Kanal aus.
1. Wählen Sie &quot;Als Master für Web-Kanal **drucken&quot;** verwenden, um die Synchronisierung zwischen dem Web-Kanal und dem Print-Kanal zu aktivieren.
1. Tap **Save &amp; Close** to save the changes.

   Ebenso können Sie auf der Registerkarte &quot; **Kanal** &quot;auf das Kontrollkästchen &quot; **Web** &quot;tippen, um den Web-Kanal aus der interaktiven Kommunikation zu löschen.

## Hinzufügen der Schaltflächenkomponente für den Web-Kanal {#add-button-component-to-the-web-channel}

Sie können die Schaltfläche als Komponente zum Web-Kanal der interaktiven Kommunikation hinzufügen. Definieren Sie Regeln mithilfe des [Regeleditors](../../forms/using/rule-editor.md) , um zu anderen interaktiven Kommunikationen, adaptiven Formularen, anderen Assets wie Bildern oder Dokument-Fragmenten oder einer externen URL zu navigieren, die Sie durch Tippen auf die Schaltfläche aufrufen können.

So fügen Sie eine Schaltfläche hinzu und definieren Regeln dafür:

1. Tippen Sie auf das Stammbedienfeld in der Webvorlage und dann auf **+** , um die Komponente &quot; **Schaltfläche** &quot;zur interaktiven Kommunikation hinzuzufügen.
1. Tippen Sie auf die Schaltflächenkomponente und dann auf , ![](assets/edit-rules.png) um Regeln für das Tippen auf die Schaltfläche zu definieren.
1. Wählen Sie im Abschnitt **Wenn** im Status der Dropdown-Liste &quot;Schaltfläche&quot;die Option **Klicken** aus.
1. In the **Then** section:

   1. Wählen Sie eine Aktion aus der Dropdown-Liste. Wählen Sie beispielsweise **Navigieren** als Aktionstyp.

   1. Geben Sie die URL der interaktiven Kommunikation, des adaptiven Formulars, eines Assets oder einer Webseite an. Geben Sie beispielsweise die URL im folgenden Format an, um zu einer anderen interaktiven Kommunikation zu navigieren: https://&lt;Servername>:&lt;Anschluss>/editor.html/content/forms/af/&lt;Name der interaktiven Kommunikation>/Kanal/&lt;Name des Kanals - print oder web>.html
   1. Geben Sie die Option an, um das Asset auf derselben Registerkarte, in einer neuen Registerkarte oder in einem neuen Fenster zu öffnen.
   1. Tap **Done** and then tap **Close** to save the rule.
   Ebenso können Sie andere verfügbare Optionen aus der Dropdown-Liste &quot;Aktionstyp&quot;auswählen, z. B. &quot;Dienst aufrufen&quot;und &quot;Formular senden&quot;. For more information, see [rule editor](../../forms/using/rule-editor.md).

1. Vorschau der interaktiven Kommunikation und Tippen Sie auf die Schaltfläche, um die interaktive Kommunikation, das adaptive Formular, ein Asset oder eine Webseite gemäß Schritt 4 Buchstabe b Ansicht.

## Hinzufügen Bereichskomponente für den Web-Kanal {#add-panel-component-to-the-web-channel}

Die Bereichskomponente ist ein Platzhalter zum Gruppieren anderer Komponenten und steuert, wie eine Gruppe von Komponenten in einer interaktiven Kommunikation angeordnet wird. Mit einer Bereichskomponente können Sie auch eine Gruppe von Komponenten für den Endbenutzer wiederholbar machen, z. B. mehrere Einträge zum Ausfüllen von Bildungsnachweisen.

Führen Sie die folgenden Schritte aus, um dem Web Kanal eine Bereichskomponente hinzuzufügen:

1. Fügen Sie die **Bereichskomponente** mithilfe einer der folgenden Optionen in den Web Kanal ein:

   * Tippen Sie auf eine Komponente, klicken Sie auf **+** und wählen Sie die **Bereichskomponente** aus.

   * Ziehen Sie die Komponente &quot; **Bedienfeld** &quot;aus dem **Komponenten** -Browser in die interaktive Kommunikation.

   * Tippen Sie auf das **Bedienfeld** im Browser **Content** und dann auf **Hinzufügen untergeordnetes Bedienfeld**. Wenn Sie die Option **Hinzufügen untergeordneten Bedienfelds** auswählen, wird das Dialogfeld **Hinzufügen untergeordneten Bedienfelds** angezeigt. Geben Sie den Titel sowie eine optionale Beschreibung und einen Namen für die Bereichskomponente ein.

1. Tippen Sie im **Inhaltsbrowser** auf das Bedienfeld, um weitere Aktionen auszuführen, z. B. zum Konfigurieren, Bearbeiten von Regeln, Kopieren, Löschen und Einfügen von Komponenten.

   Sie können auch ein Bedienfeld innerhalb des **Inhalts** -Browsers per Drag &amp; Drop verschieben, um die Änderung der Struktur der interaktiven Kommunikation im rechten Bereich widerzuspiegeln.

## Synchronisierung des Webkanals mit dem Druckkanal.{#synchronize}

Wenn Sie beim Erstellen einer interaktiven Kommunikation &quot;Als Master für Web-Kanal drucken&quot;auswählen, wird der Web-Kanal synchron mit dem Print-Kanal erstellt und die Inhalts- und Datenbindung des Web-Kanals wird vom Print-Kanal abgeleitet. Die im Print-Kanal vorgenommenen Änderungen können im Web-Kanal übernommen werden, wenn Sie auf Synchronisieren tippen.

Die Autoren dürfen jedoch ggf. die Vererbung für Komponenten im Webkanal aufheben.

![Erstellen von Print Master](assets/create_ic_print_master_new-1.png) ![Print Master Web](assets/create_ic_print_master_web_new-1.png)

### Autom. Synchronisierung {#autosync}

Wenn Sie die Option &quot;Als Master für Web-Kanal **** drucken&quot;auswählen, können Sie einen der folgenden Modi zum Generieren von Web-Kanal auswählen:

* **[!UICONTROL Automatisches Layout]**: Wählen Sie diesen Modus aus, um automatisch Platzhalter, Inhalte und Datenbindung für Web Kanal aus dem Print Kanal zu generieren.
* **[!UICONTROL Manuelles Organisieren]**: Wählen Sie diesen Modus aus, um unter Verwendung des auf der Registerkarte &quot;Datenquellen&quot;verfügbaren Hauptinhalts die Elemente &quot;Kanal drucken&quot;manuell auszuwählen und dem Web-Kanal hinzuzufügen. Weitere Informationen finden Sie unter [Wählen Sie Kanal drucken aus, um Webinhalte](#selectprintchannelelements)zu erstellen.

![IC-Optionen erstellen](assets/create_ic_options_updated_new.png)

>[!NOTE]
>
>Durch das Synchronisieren der Kanäle werden nur die Dokumentfragmente, Bilder, Bedingungen, Listen und Layout-Fragmente vom Druckkanal zum Webkanal synchronisiert. Die Teilformulare oder übergeordneten Knoten, die solche Elemente enthalten, werden nicht synchronisiert.

### Wählen Sie Kanal drucken, um Web-Kanal-Inhalte zu erstellen {#selectprintchannelelements}

Wenn Sie beim Erstellen der interaktiven Kommunikation &quot;Als Master drucken&quot;auswählen und nicht die Option für die automatische Synchronisierung wählen, können Sie auch Print-Kanal-Elemente in die Authoring-Oberfläche von Web Kanal ziehen und dort ablegen.

Navigieren Sie zu **Datenquellen** > **Hauptinhalt** , um die Kanal-Elemente drucken Ansicht. Ziehen Sie die Zielgruppen, Felder oder Tabellen per Drag &amp; Drop in die Authoring-Oberfläche von Web Kanal. Ein blaues Kreissymbol neben dem Elementnamen gibt an, dass das Element Kanal drucken bereits im Web Kanal enthalten ist.

![Masterinhalt](assets/master_content.png)

### Vererbung abbrechen {#cancelinheritance}

Im Webkanal sind die Komponenten in den Zielbereichen eingebettet.

Hover over the relevant target area or variable in the web channel and select ![cancelinheritance](assets/cancelinheritance.png) (Cancel Inheritance) and then in the Cancel Inheritance dialog, tap **[!UICONTROL Yes]**.

Die Vererbung der Komponenten innerhalb des Zielbereichs wird aufgehoben und Sie können sie nun nach Bedarf bearbeiten.

### Vererbung erneut aktivieren {#re-enable-inheritance}

Wenn Sie im Webkanal die Vererbung einer Komponente abgebrochen haben, können Sie sie erneut aktivieren. To re-enable inheritance, hover over the boundary of the relevant target area, which includes the component, and tap ![reenableinheritance](assets/reenableinheritance.png).

Das Dialogfeld „Vererbung zurücksetzen“ wird angezeigt.

![revertinerbation](assets/revertinheritance.png)

Wählen Sie bei Bedarf **[!UICONTROL Synchronisieren der Seite nach dem Zurücksetzen der Vererbung]**. Wählen Sie diese Option, um die gesamte interaktive Kommunikation zu synchronisieren. Wenn Sie diese Option nicht auswählen, wird beim erneuten Installieren der Vererbung nur der entsprechende Bereich der Zielgruppe synchronisiert.

Tippen Sie auf **[!UICONTROL Ja]**.

### Synchronisieren {#synchronize-1}

Wenn Sie &quot;Als Master für Web Kanal drucken&quot;verwenden und Änderungen am Kanal &quot;Drucken&quot;vornehmen, können Sie die Inhalte synchronisieren, um die neu vorgenommenen Änderungen an den Web-Kanal zu übertragen.

1. Um den Web-Kanal mit dem Kanal &quot;Drucken&quot;zu synchronisieren, wechseln Sie zum Web-Kanal und tippen Sie auf das Symbol &quot;Mehr Optionen&quot;.

   ![Auto-Synchronisierungsoptionen](assets/auto_sync_options_new.png)

1. Tippen Sie auf eine der folgenden Optionen:

   * **[!UICONTROL Mit Drucken]** synchronisieren: Synchronisiert nur Inhalte für die Zielgruppen, in denen die Vererbung nicht abgebrochen wird.
   * **[!UICONTROL Zurücksetzen]**: Synchronisiert den Inhalt des Web-Kanals mit dem Kanal &quot;Drucken&quot;und verwirft alle am Web-Kanal vorgenommenen Änderungen.

### Verwenden der Komponenten-Symbolleiste zum Durchführen von Aktionen für geerbte Komponenten {#componenttoolbar}

Sobald Sie über die Option &quot;Synchronisieren&quot;automatisch generierte Inhalte im Web Kanal verfügen, können Sie mehr Aktionen für Komponenten durchführen, ohne die Vererbung zu beenden.

![Komponentensymbolleiste](assets/component_toolbar_inherited_web_new.png)

Tippen Sie auf die Komponente, um die folgenden Optionen Ansicht:

* **Kopieren:** Kopieren Sie eine Komponente und fügen Sie sie an anderen Stellen der interaktiven Kommunikation ein.
* **Ausschneiden:** Verschieben Sie eine Komponente in der interaktiven Kommunikation von einem Ort zum anderen.
* **Komponente einfügen:** Fügen Sie eine Komponente oberhalb der ausgewählten Komponente ein.
* **Einfügen:** Fügen Sie die Komponente ein, die Sie mithilfe der oben beschriebenen Optionen ausgeschnitten oder kopiert haben.
* **Gruppe:** Wählen Sie mehrere Komponenten aus, wenn Sie mehrere Komponenten gleichzeitig ausschneiden, kopieren oder einfügen möchten.
* **Übergeordnet:** Wählen Sie das übergeordnete Element einer Komponente aus.
* **Ansicht SOM-Ausdruck:** Ansicht des [SOM-Ausdrucks](../../forms/using/using-som-expressions-adaptive-forms.md) für die Komponente.

* **Gruppenobjekte im Bedienfeld:** Gruppieren Sie die Komponenten in einem Bereich, um Vorgänge an diesen Komponenten gleichzeitig durchführen zu können. Weitere Informationen finden Sie unter **[Objekte in Bedienfeld](../../forms/using/create-interactive-communication.md#main-pars-header-1815149576)**gruppieren.

* **Vererbung abbrechen:** Die [Vererbung](../../forms/using/create-interactive-communication.md#main-pars-header-103384010) der Komponenten im Bereich &quot;Zielgruppe&quot;abbrechen, um sie zu bearbeiten.

### Group objects in Panel {#groupobjectspanel}

Die Authoring-Oberfläche von Web Kanal erleichtert die Gruppierung der Komponenten in einem Bereich, um Vorgänge an diesen Komponenten gleichzeitig durchführen zu können. Auf der Registerkarte &quot; **Inhalt** &quot;werden die gruppierten Komponenten als untergeordnete Elemente des Bereichs in der Inhaltsstruktur Liste.

1. Tippen Sie auf eine Komponente und wählen Sie den Vorgang &quot;Gruppe ( ![Gruppe](assets/group.jpg))&quot;aus.
1. Wählen Sie mehrere Komponenten aus und tippen Sie im Bedienfeld auf **Gruppenobjekte**.

   ![Gruppenobjekte](assets/component_toolbar_group_objects_new.png)

1. Geben Sie im Dialogfeld &quot; **Gruppenobjekte im Bedienfeld** &quot;einen Namen für das Bedienfeld ein.
1. Geben Sie einen optionalen Titel und eine Beschreibung für das Bedienfeld ein.
1. Klicken Sie auf ![bullet_checkmark](assets/bullet_checkmark.png).

   Die gruppierten Komponenten werden als untergeordnete Elemente des Bedienfelds in der Inhaltsstruktur angezeigt.

   ![content_tree_grouping](assets/content_tree_grouping.png)

