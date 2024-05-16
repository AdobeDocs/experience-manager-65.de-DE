---
title: "Tutorial: Erstellen einer interaktiven Kommunikation "
description: Erstellen Sie eine interaktive Kommunikation mit allen Bausteinen
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: aaacee66-6bbe-498b-91b1-3a9545ff1aeb
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1884'
ht-degree: 100%

---

# Tutorial: Erstellen einer interaktiven Kommunikation {#tutorial-create-interactive-communication}

![09-style-your-adaptive-form-small](assets/09-style-your-adaptive-form-small.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, die Serie in chronologischer Reihenfolge zu durchlaufen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, durchzuführen und zu demonstrieren.

Nachdem Sie alle Bausteine wie Formulardatenmodell, Dokumentfragmente und Vorlagen und Themen für die Webversion erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Eine interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: den Druckkanal und den Web-Kanal. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Primär erstellen. Die Option zum Drucken als Primär für den Web-Kanal stellt sicher, dass Inhalt, Vererbung und Datenbindung des Web-Kanals vom Druckkanal abgeleitet werden. Hierdurch wird außerdem sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Web-Kanal synchronisiert werden. Die Autorinnen und Autoren der interaktiven Kommunikation dürfen jedoch ggf. die Vererbung für bestimmte Komponenten im Web-Kanal aufheben.

Dieses Tutorial führt Sie durch die Schritte zum Erstellen interaktiver Mitteilungen für Print- und Web-Kanäle. Am Ende dieses Tutorials können Sie Folgendes:

* Erstellen einer interaktiven Kommunikation für den Druckkanal
* Erstellen einer interaktiven Kommunikation für den Web-Kanal
* Erstellen einer interaktiven Kommunikation für den Druck- und Web-Kanal mit der Option zum Drucken als Primär

## Erstellen einer interaktiven Kommunikation für den Druck- und Web-Kanal ohne Synchronisierung {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Erstellen einer interaktiven Kommunikation für den Druckkanal {#create-interactive-communication-for-print-channel}

Die folgende Liste führt die Ressourcen auf, die in diesem Tutorial bereits erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Druckkanal benötigt werden:

**Druckvorlage:** [create_first_ic_print_template](../../forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Dokumentfragmente:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Layout-Fragmente:** [table_lf](../../forms/using/create-templates-print-web.md)

**Bilder:** PayNow und ValueAddedServices

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und dann **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie als Druckvorlage **create_first_ic_print_template** an und wählen Sie **Auswählen** aus. Stellen Sie sicher, dass das Kontrollkästchen **Druck als Primärkanal für Web-Kanal verwenden** nicht aktiviert ist.

   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Web-Vorlage ein und wählen Sie **Auswählen** aus.

   1. Wählen Sie **Erstellen** aus.

   Es wird eine Bestätigungsmeldung darüber angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Wählen Sie **Bearbeiten** aus, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Wechseln Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Dokumentfragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag-and-Drop in die entsprechenden Zielbereiche der Interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Gebühren |

   ![Dokumentfragmente für interaktive Kommunikation](assets/create_first_ic_doc_fragments_new.png)

1. Wählen Sie den Zielbereich **Diagramme** und anschließend **+** aus, um eine Komponente **Diagramm** hinzuzufügen.
1. Wählen Sie die Diagrammkomponente und ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Wählen Sie ![done_icon](assets/done_icon.png) aus.
   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **Y-Achse** aus. Wählen Sie ![done_icon](assets/done_icon.png) aus.
   1. Wählen Sie ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

1. Wechseln Sie zur Registerkarte **Elemente** und wenden Sie den Filter an, um nur die Layout-Fragmente im linken Bereich anzuzeigen. Ziehen Sie das Layout **table_lf** per Drag-and-Drop in den Zielbereich **Einzeln aufgeführte Anrufe**.
1. Wählen Sie das Textfeld in der Spalte **Datum** und ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus.
1. Wählen Sie **Datenmodellobjekt** aus der Dropdown-Liste **Bindungstyp** und wählen Sie **calls** > **calldate**. Zum Speichern der Eigenschaften wählen Sie zweimal ![done_icon](assets/done_icon.png) aus.

   Erstellen Sie eine Bindung mit **calltime**, **callnumber**, **callduration** und **callcharges** für Textfelder in den Spalten **Zeit**, **Anzahl**, **Dauer** und **Kosten**.

1. Um eine **Bildkomponente** hinzuzufügen, wählen Sie den Zielbereich **PayNow** und anschließend **+** aus.
1. Wählen Sie die Bildkomponente und ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie **PayNow** als Namen des Bilds im Feld **Name** ein.
   1. Wählen Sie **Hochladen**, dann das im lokalen Dateisystem gespeicherte Bild und schließlich **Öffnen** aus.
   1. Wählen Sie ![done_icon](assets/done_icon.png) aus, um die Bildeigenschaften zu speichern.

1. Um das Bild **ValueAddedServices** dem Zielbereich **ValueAddedServices** hinzuzufügen, wiederholen Sie die Schritte 13 und 14.

### Erstellen einer interaktiven Kommunikation für den Web-Kanal {#create-interactive-communication-for-web-channel}

Die folgende Liste führt die Ressourcen auf, die in diesem Tutorial bereits erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Web-Kanal benötigt werden:

**Webvorlage:** [Create_First_IC_Web_Template](../../forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Dokumentfragmente:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Bilder:** PayNowWeb und ValueAddedServicesWeb

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und dann **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie als Druckvorlage **create_first_ic_print_template** an und wählen Sie **Auswählen** aus. Stellen Sie sicher, dass das Kontrollkästchen **Druck als Primärkanal für Web-Kanal verwenden** nicht aktiviert ist.

   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Web-Vorlage ein und wählen Sie **Auswählen** aus.

   1. Wählen Sie **Erstellen** aus.

   Es wird eine Bestätigungsmeldung darüber angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Wählen Sie **Bearbeiten** aus, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Wählen Sie die Registerkarte **Kanäle** im linken Bereich und dann **Web** aus.
1. Wechseln Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Dokumentfragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag-and-Drop in die entsprechenden Zielbereiche der Interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Gebühren |

1. Wählen Sie den Zielbereich **Zusammenfassung der Gebühren** und anschließend **+** aus, um eine **Diagrammkomponente** hinzuzufügen.
1. Wählen Sie die Diagrammkomponente und dann ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.

   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Wählen Sie ![done_icon](assets/done_icon.png) aus.

   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.

   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **Y-Achse** aus. Wählen Sie ![done_icon](assets/done_icon.png) aus.

   1. Wählen Sie ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

1. Wählen Sie die Registerkarte **Datenquellen** aus dem linken Bereich und ziehen Sie das Datenmodellobjekt **calls** in den Zielbereich **Einzeln aufgeführte Anrufe**. Alle Eigenschaften im Datenmodellobjekt **calls** werden als Tabellenspalten im Zielbereich **Einzeln aufgeführte Anrufe** im rechten Bereich angezeigt.

   Basierend auf dem Anwendungsfall benötigen Sie die Spalten „Anrufdatum“, „Anrufzeit“, „Rufnummer“, „Anrufdauer“ und „Anrufkosten“ in der Tabelle.

   ![Tabelle für interaktive Kommunikation](assets/table_ic_web_new.png)

1. Wählen Sie die Tabellenspaltenüberschrift **Mobilenum** und dann **Weitere Optionen** > **Spalte löschen** aus. Löschen Sie auf ähnliche Weise die Spalte **Anruftyp**.
1. Wählen Sie die Tabellenspaltenüberschrift **Calldate** und dann ![edit](assets/edit.png) (Bearbeiten) aus, um den Text in **Anrufdatum** zu ändern. Benennen Sie auf diese Weise auch die anderen Spaltenüberschriften in der Tabelle um.
1. Fügen Sie je nach Anwendungsfall die Schaltfläche **Jetzt bezahlen** in die interaktive Kommunikation ein, die Benutzenden die Option bietet, die Zahlung durch Klicken auf die Schaltfläche vorzunehmen. Führen Sie die folgenden Schritte aus, um die Schaltfläche einzufügen:

   1. Wählen Sie den Zielbereich **Jetzt bezahlen** und anschließend **+** aus, um eine **Textkomponente** hinzuzufügen.

   1. Wählen Sie die Textkomponente und dann ![edit](assets/edit.png) (Bearbeiten) aus.
   1. Ändern Sie den Text in **Jetzt bezahlen**.
   1. Wählen Sie den Text und dann das Hyperlink-Symbol aus.
   1. Geben Sie die Zahlungs-URL in das Feld **Pfad** ein.
   1. Wählen Sie aus der Dropdown-Liste **Ziel** die Option **Neue Registerkarte** aus.

   1. Wählen Sie ![done_icon](assets/done_icon.png) aus, um die Hyperlink-Eigenschaften zu speichern.

1. Wählen Sie **Style** aus der Dropdown-Liste neben der Option **Vorschau**.

   ![Auswählen des Stilmodus für interaktive Kommunikation](assets/select_style_ic_web_new.png)

1. Gestalten Sie den Hyperlink-Text so, dass er als Schaltfläche in der interaktiven Kommunikation angezeigt wird. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie die Textkomponente und dann ![edit](assets/edit.png) (Bearbeiten) aus.
   1. Geben Sie im Abschnitt **Rahmen** **1.5px** als **Rahmenbreite** ein, wählen Sie **Durchgehend** als **Rahmenstil** ein und geben Sie **46px** als **Rahmenradius** ein.

   1. Wählen Sie im Abschnitt **Hintergrund** die Farbe Rot als Hintergrundfarbe für die Schaltfläche aus.
   1. Wählen Sie im Feld **Rand** für **Abmessungen und Position** das Symbol **Gleichzeitig bearbeiten** aus und legen Sie für den **rechten** Rand **450 Pixel** fest. Die Felder Oben, Unten und Links werden leer gelassen.

   ![Einfügen eines Hyperlinks in interaktive Kommunikation](assets/ic_web_hyperlink_new.png)

1. Wählen Sie den Zielbereich **Jetzt bezahlen** und anschließend **+** aus, um eine **Bildkomponente** hinzuzufügen.
1. Wählen Sie die Bildkomponente und dann ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie **PayNow** als Namen des Bildes im Feld **Name** an.

   1. Wählen Sie **Hochladen**, dann das im lokalen Dateisystem gespeicherte Bild **PayNowWeb** und schließlich **Öffnen** aus.

   1. Wählen Sie ![done_icon](assets/done_icon.png) aus, um die Bildeigenschaften zu speichern.

1. Fügen Sie je nach Anwendungsfall die Schaltfläche **Abonnieren** in die interaktive Kommunikation ein, die dem Benutzer die Option bietet, den Mehrwert-Service durch Klicken auf die Schaltfläche zu abonnieren.

   Wiederholen Sie die Schritte 13 bis 17, um eine Schaltfläche **Abonnieren** zum Zielbereich **Mehrwert - Service** hinzuzufügen und das Bild **ValueAddedServicesWeb** hinzufügen.

## Erstellen interaktiver Kommunikation für Druck- und Web-Kanäle mit automatischer Synchronisierung {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

Sie können eine interaktive Kommunikation auch erstellen, indem Sie die automatische Synchronisierung zwischen Druck- und Web-Kanälen aktivieren. Um die automatische Synchronisierung zu aktivieren, wählen Sie beim Erstellen der interaktiven Kommunikation die Option „Print als Master“ aus. Die Option „Print als Master“ stellt sicher, dass Inhalt, Vererbung und Datenbindung des Web-Kanals vom Druckkanal abgeleitet werden. Darüber hinaus wird sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Web-Kanal widergespiegelt werden.

Führen Sie die folgenden Schritte aus, um den Inhalt des Web-Kanals mithilfe des Druckkanals abzuleiten:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und dann **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und wählen Sie **Auswählen** aus.

   1. Aktivieren Sie das Kontrollkästchen **Druck als Primärkanal für Web-Kanal verwenden**.
   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Web-Vorlage an und wählen Sie **Auswählen** aus.

   1. Wählen Sie **Erstellen** aus.

   Es wird eine Bestätigungsmeldung darüber angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Wählen Sie **Bearbeiten** aus, um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Führen Sie die Schritte 6–15 des Abschnitts [Erstellen einer interaktiven Kommunikation für den Druckkanal](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-print-channel) aus.
1. Wählen Sie im linken Bereich die Registerkarte **Kanäle** und dann **Web** aus, um anhand des Druckkanals automatisch Inhalte für den Web-Kanal zu generieren.
1. Da Sie in Schritt 4 das Kontrollkästchen **Druck als Master für Webkanal verwenden** aktiviert haben, werden Inhalt und Bindungen für den Webkanal automatisch aus dem Druckkanal generiert.

   Der Inhalt des Druckkanals wird unterhalb des Inhalts der Web-Kanalvorlage eingefügt. Um den anhand des Druckkanals automatisch generierten Web-Kanalinhalt zu ändern, können Sie die Vererbung für jeden beliebigen Zielbereich abbrechen.

   Bewegen Sie den Mauszeiger über den entsprechenden Zielbereich im Web-Kanal, wählen Sie ![cancelinheritance](assets/cancelinheritance.png) (Vererbung abbrechen) und dann im Dialogfeld **Vererbung abbrechen** die Option **Ja** aus.

   ![Vererbung abbrechen](assets/cancel_inheritance_web_channel_new.png)

   Wenn Sie die Vererbung einer Komponente abgebrochen haben, können Sie sie erneut aktivieren. Um die Vererbung erneut zu aktivieren, bewegen Sie den Mauszeiger über die Grenze des entsprechenden Zielbereichs, der die Komponente enthält, und wählen Sie ![reenableinheritance](assets/reenableinheritance.png) aus.

1. Wählen Sie im linken Bereich die Registerkarte **Inhalt** aus.
1. Ziehen Sie den automatisch generierten Web-Kanalinhalt mithilfe der Inhaltsstruktur in die vorhandenen Bedienfelder der Web-Vorlage. Nachfolgend sehen Sie die Liste der Komponenten, die neu angeordnet werden müssen:

   * Komponente „Rechnungsdetails“ zum Bedienfeld „Rechnungsdetails“
   * Komponente „Kundendetails“ zum Bedienfeld „Kundendetails“
   * Komponente „Rechnungsübersicht“ zum Bedienfeld „Rechnungsübersicht“
   * Komponente „Zusammenfassung der Gebühren“ zum Bedienfeld „Zusammenfassung der Gebühren“
   * Layout-Fragment (Tabelle) zum Bedienfeld „Einzeln aufgeführte Anrufe“

   ![Webinhaltsstruktur](assets/ic_web_content_tree_new.png)

1. Wiederholen Sie die Schritte 13 - 18 von [Interaktive Kommunikation für Webkanal erstellen](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-web-channel), um die Hyperlinks **Jetzt bezahlen** und **Abonnieren** in den Webkanal der interaktiven Kommunikation einzufügen.
