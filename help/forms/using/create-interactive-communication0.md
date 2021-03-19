---
title: '"Tutorial: Erstellen einer interaktiven Kommunikation "'
seo-title: Erstellen Sie eine interaktive Kommunikation für Druck und Web
description: Erstellen Sie eine interaktive Kommunikation mit allen Bausteinen
seo-description: Erstellen Sie eine interaktive Kommunikation mit allen Bausteinen
uuid: 5ffaa86f-87c7-4673-8b41-63ec61421be2
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ac5d8d4f-fc13-4e8d-819c-c5db07fa6870
docset: aem65
feature: Interaktive Kommunikation
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 60%

---


# Tutorial: Erstellen einer interaktiven Kommunikation {#tutorial-create-interactive-communication}

![09-style-your-adaptive-form-small](assets/09-style-your-adaptive-form-small.png)

Dieses Lernprogramm ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Nachdem Sie alle Bausteine &#x200B;&#x200B;wie Formulardatenmodell, Dokumentfragmente und Vorlagen und Themen für die Webversion erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Interaktive Kommunikation kann über zwei Kanäle erfolgen: Druck und Web. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Master erstellen. Druck als Master-Option für Webkanal stellt sicher, dass Inhalt, Vererbung und Datenbindung des Webkanals vom Druckkanal abgeleitet werden. Außerdem wird sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Webkanal synchronisiert werden. Die Autoren der interaktiven Kommunikation dürfen jedoch ggf. die Vererbung für bestimmte Komponenten im Webkanal aufheben.

In diesem Tutorial werden Sie durch die Schritte zum Erstellen interaktiver Kommunikationen für Druck- und Webkanäle geführt. Am Ende dieser Schulung können Sie Folgendes:

* Erstellen Sie interaktive Kommunikation für den Druckkanal
* Erstellen Sie interaktive Kommunikation für den Webkanal
* Erstellen Sie interaktive Kommunikation für den Druck- und Webkanal mit Druck als Master

## Erstellen Sie interaktive Kommunikation für Druck und Web ohne Synchronisierung {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Erstellen einer interaktiven Kommunikation für Druckkanal {#create-interactive-communication-for-print-channel}

Im Folgenden finden Sie eine Liste der Ressourcen, die bereits in diesem Tutorial erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Druckkanal benötigt werden:

**Druckvorlage:** [create_first_ic_print_template](../../forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Fragmente von Dokumenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_Ladungen_first_ic](../../forms/using/create-document-fragments.md)

**Layout-Fragmente:** [table_lf](../../forms/using/create-templates-print-web.md)

**Bilder:** PayNow und ValueAddedServices

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation**. Der Assistent **Interaktive Kommunikation erstellen** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanal**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Select**. Vergewissern Sie sich, dass das Kontrollkästchen &quot;**Als Übergeordnet drucken für Web Kanal**&quot;nicht aktiviert ist.

   1. Geben Sie **Create_First_IC_templates** folder > **Create_First_IC_Web_Template** als Webvorlage an und tippen Sie auf **Select**.

   1. Tippen Sie auf **Erstellen**.

   Eine Bestätigungsmeldung wird angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen Sie auf **Bearbeiten**, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Gehen Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Dokument-Fragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag &amp; Drop in ihre Zielbereiche in der interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Gebühren |

   ![Fragmente von Dokumenten für interaktive Kommunikation](assets/create_first_ic_doc_fragments_new.png)

1. Tippen Sie auf den Zielbereich **Diagramme** und anschließend auf **+**, um eine Komponente **Diagramm** hinzuzufügen.
1. Tippen Sie auf die Diagrammkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren). Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Objekttyp **Calls** im Abschnitt **Y-Achse**. Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

1. Gehen Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Layout-Fragmente im linken Bereich anzuzeigen. Ziehen Sie das Layout **table_lf** per Drag-and-Drop in den Zielbereich **Einzeln aufgeführte Anrufe**.
1. Wählen Sie das Textfeld in der Spalte **Datum** aus und tippen Sie auf ![configure_icon](assets/configure_icon.png) (Konfigurieren).
1. Wählen Sie **Datenmodellobjekt** aus der Dropdown-Liste **Bindungstyp** und wählen Sie **calls** > **calldate**. Tippen Sie zweimal auf ![done_icon](assets/done_icon.png), um die Eigenschaften zu speichern.

   Erstellen Sie eine Bindung mit **calltime**, **callnumber**, **callduration** und **callcharges** für Textfelder in den Spalten **Zeit**, **Anzahl**, **Dauer** und **Kosten**.

1. Tippen Sie auf den Bereich **PayNow** Zielgruppe und dann auf **+**, um eine **Image**-Komponente hinzuzufügen.
1. Tippen Sie auf die Image-Komponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren). Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie **PayNow** als Namen des Bildes im Feld **Name** ein.
   1. Tippen Sie auf **Hochladen**, wählen Sie das im lokalen Dateisystem gespeicherte Bild aus und tippen Sie auf **Öffnen**.
   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Bildeigenschaften zu speichern.

1. Wiederholen Sie die Schritte 13 und 14, um dem Bereich **ValueAddedServices** das Bild **ValueAddedServices** der Zielgruppe hinzuzufügen.

### Erstellen Sie interaktive Kommunikation für den Webkanal {#create-interactive-communication-for-web-channel}

Im Folgenden finden Sie eine Liste der Ressourcen, die bereits in diesem Tutorial erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Webkanal benötigt werden:

**Webvorlage:** [Create_First_IC_Web_Template](../../forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Fragmente von Dokumenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_Ladungen_first_ic](../../forms/using/create-document-fragments.md)

**Bilder:** PayNowWeb und ValueAddedServicesWeb

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation**. Der Assistent **Interaktive Kommunikation erstellen** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanal**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Select**. Vergewissern Sie sich, dass das Kontrollkästchen &quot;**Als Übergeordnet drucken für Web Kanal**&quot;nicht aktiviert ist.

   1. Geben Sie **Create_First_IC_templates** folder > **Create_First_IC_Web_Template** als Webvorlage an und tippen Sie auf **Select**.

   1. Tippen Sie auf **Erstellen**.

   Eine Bestätigungsmeldung wird angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen Sie auf **Bearbeiten**, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Tippen Sie im linken Bereich auf die Registerkarte **Kanal** und dann auf **Web**.
1. Gehen Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Dokument-Fragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag &amp; Drop in ihre Zielbereiche in der interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_Ladys_first_interactive_communication | Gebühren |

1. Tippen Sie auf den Bereich **Gebührenzusammenfassung** Zielgruppe und dann auf **+**, um eine **Diagrammkomponente** hinzuzufügen.
1. Tippen Sie auf die Diagrammkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren). Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.

   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Tippen Sie auf ![done_icon](assets/done_icon.png).

   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.

   1. Wählen Sie die Eigenschaft **calltype** aus dem Objekttyp **Calls** im Abschnitt **Y-Achse**. Tippen Sie auf ![done_icon](assets/done_icon.png).

   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

1. Wählen Sie die Registerkarte **Datenquellen** aus dem linken Bereich und ziehen Sie das Datenmodellobjekt **calls** in den Zielbereich **Einzeln aufgeführte Anrufe**. Alle Eigenschaften im Datenmodellobjekt **Aufrufe** werden als Tabellenspalten im Bereich **Itemized Calls** Zielgruppe im rechten Bereich angezeigt.

   Basierend auf dem Anwendungsfall benötigen Sie die Spalten „Anrufdatum“, „Anrufzeit“, „Rufnummer“, „Anrufdauer“ und „Anrufkosten“ in der Tabelle.

   ![Tabelle für interaktive Kommunikation](assets/table_ic_web_new.png)

1. Wählen Sie **Mobilenum** Spaltenüberschrift und wählen Sie **Weitere Optionen** > **Spalte löschen**. Löschen Sie auf ähnliche Weise die Spalte **Anruftyp**.
1. Wählen Sie die Spaltenüberschrift **Aufrufdatum** aus und tippen Sie auf ![Bearbeiten](assets/edit.png) (Bearbeiten), um den Text in **Aufrufdatum** umzubenennen. Benennen Sie andere Spaltenüberschriften in der Tabelle um.
1. Fügen Sie je nach Anwendungsfall die Schaltfläche **Jetzt bezahlen** in die interaktive Kommunikation ein, die dem Benutzer die Option bietet, die Zahlung durch Klicken auf die Schaltfläche vorzunehmen. Führen Sie die folgenden Schritte aus, um die Schaltfläche einzufügen:

   1. Tippen Sie auf den Bereich **Jetzt bezahlen** Zielgruppe und dann auf **+**, um eine **Textkomponente** hinzuzufügen.

   1. Tippen Sie auf die Textkomponente und dann auf ![edit](assets/edit.png) (Bearbeiten).
   1. Benennen Sie den Text in **Jetzt bezahlen** um.
   1. Wählen Sie den Text aus und tippen Sie auf das Hyperlink-Symbol.
   1. Geben Sie die Zahlungs-URL in das Feld **Pfad** ein.
   1. Wählen Sie **Neue Registerkarte** aus der Dropdown-Liste **Ziel**.

   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Hyperlinkeigenschaften zu speichern.

1. Wählen Sie **Style** aus der Dropdown-Liste neben der Option **Vorschau**.

   ![Stilmodus für interaktive Kommunikation auswählen](assets/select_style_ic_web_new.png)

1. Gestalten Sie den Hyperlink-Text so, dass er als Schaltfläche in der interaktiven Kommunikation angezeigt wird. Gehen Sie dazu wie folgt vor:

   1. Tippen Sie auf die Textkomponente und wählen Sie ![edit](assets/edit.png) (Bearbeiten).
   1. Geben Sie im Abschnitt **Rahmen** **1.5px** als **Rahmenbreite** ein, wählen Sie **Durchgehend** als **Rahmenstil** ein und geben Sie **46px** als **Rahmenradius** ein.

   1. Wählen Sie Rot als Hintergrundfarbe für die Schaltfläche im Abschnitt **Hintergrund**.
   1. Im Feld **Rand** für **Abmessungen und Position**, tippen Sie auf das Symbol **Gleichzeitig bearbeiten**, und setzen Sie den **rechten** Rand auf **450px**. Die Felder Oben, Unten und Links werden leer gelassen.

   ![Hyperlink in interaktive Kommunikation einfügen](assets/ic_web_hyperlink_new.png)

1. Tippen Sie auf den Bereich **Jetzt bezahlen** Zielgruppe und dann auf **+**, um eine **Image**-Komponente hinzuzufügen.
1. Tippen Sie auf die Image-Komponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren). Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie **PayNow** als Namen des Bildes im Feld **Name** ein.

   1. Tippen Sie auf **Upload**, wählen Sie das **PayNowWeb**-Bild aus, das im lokalen Dateisystem gespeichert wurde, und tippen Sie auf **Öffnen**.

   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Bildeigenschaften zu speichern.

1. Fügen Sie je nach Anwendungsfall die Schaltfläche **Abonnieren** in die interaktive Kommunikation ein, mit der der Benutzer die Option zum Abonnieren der Mehrwertdienste durch Klicken auf die Schaltfläche erhält.

   Wiederholen Sie die Schritte 13 bis 17, um dem Bereich **Zielgruppe** Abonnieren **die Schaltfläche** Wertsteigernde Dienste hinzuzufügen, und fügen Sie das Bild **ValueAddedServicesWeb** hinzu.

## Erstellen Sie interaktive Kommunikation für Druck und Web mit automatischer Synchronisierung {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

Sie können auch eine interaktive Kommunikation erstellen, indem Sie die automatische Synchronisierung zwischen Druck- und Webkanälen aktivieren. Um die automatische Synchronisierung zu aktivieren, wählen Sie beim Erstellen der interaktiven Kommunikation die Option „Als Master drucken“. Die Option „Druck als Master“ stellt sicher, dass Inhalt, Vererbung und Datenbindung des Webkanals vom Druckkanal abgeleitet werden. Außerdem wird sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Webkanal vorhanden sind.

Führen Sie die folgenden Schritte aus, um den Webkanal-Inhalt mithilfe des Druckkanals abzuleiten:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation**. Der Assistent **Interaktive Kommunikation erstellen** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanal**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Select**.

   1. Aktivieren Sie das Kontrollkästchen **Als Übergeordnet für Web-Kanal** drucken.
   1. Geben Sie **Create_First_IC_templates** folder > **Create_First_IC_Web_Template** als Webvorlage an und tippen Sie auf **Select**.

   1. Tippen Sie auf **Erstellen**.

   Eine Bestätigungsmeldung wird angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen Sie auf **Bearbeiten**, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Führen Sie die Schritte 6 - 15 im Abschnitt [Interaktive Kommunikation für Print Kanal](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-print-channel) erstellen aus.
1. Tippen Sie auf die Registerkarte **Kanäle** im linken Bereich und tippen Sie auf **Web**, um automatisch generieren Inhalte für den Webkanal aus dem Druckkanal zu generieren.
1. Da in Schritt 4 das Kontrollkästchen &quot;**Als Übergeordnet für Web-Kanal verwenden**&quot;aktiviert ist, werden die Inhalte und Bindungen automatisch für Web-Kanal aus dem Print-Kanal generiert.

   Der Druckkanalinhalt wird unter dem Inhalt der Webkanalvorlage eingefügt. Um den automatisch aus dem Druckkanal generierten Webkanalinhalt zu ändern, können Sie die Vererbung für einen beliebigen Zielbereich abbrechen.

   Bewegen Sie den Mauszeiger über den entsprechenden Bereich der Zielgruppe im Web-Kanal und wählen Sie ![cancelVererbung](assets/cancelinheritance.png) (Abbrechen der Vererbung). Tippen Sie anschließend im Dialogfeld **Cancel Invererance** auf **Yes**.

   ![Vererbung abbrechen](assets/cancel_inheritance_web_channel_new.png)

   Wenn Sie die Vererbung einer Komponente abgebrochen haben, können Sie sie erneut aktivieren. Um die Vererbung erneut zu aktivieren, halten Sie den Mauszeiger über die Begrenzung des entsprechenden Komponentenbereichs, der die Zielgruppe enthält, und tippen Sie auf ![reaktivierte Vererbung](assets/reenableinheritance.png).

1. Wählen Sie die Registerkarte **Inhalt** im linken Bereich.
1. Ziehen Sie den automatisch generierten Webkanal-Inhalt mithilfe der Inhaltsstruktur in die vorhandenen Bereiche der Webvorlage. Im folgenden finden Sie die Liste der Komponenten, die neu angeordnet werden müssen:

   * Komponente „Rechnungsdetails“ im Bereich „Rechnungsdetails“
   * Komponente „Kundendetails“ im Bereich „Kundendetails“
   * Komponente „Rechnungszusammenfassung“ im Bereich „Rechnungszusammenfassung“
   * Komponente „Zusammenfassung der Gebühren“ im Bereich „Zusammenfassung der Gebühren“
   * Layoutfragment (Tabelle) für den Bereich „Einzeln aufgeführte Anrufe“

   ![Webinhalt-Struktur](assets/ic_web_content_tree_new.png)

1. Wiederholen Sie die Schritte 13 - 18 von [Interaktive Kommunikation für Webkanal erstellen](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-web-channel), um die Hyperlinks **Jetzt bezahlen** und **Abonnieren** in den Webkanal der interaktiven Kommunikation einzufügen.

