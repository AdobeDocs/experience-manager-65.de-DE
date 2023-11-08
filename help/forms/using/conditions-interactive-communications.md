---
title: Bedingungen in interaktiven Kommunikationen
seo-title: Conditions in Interactive Communications
description: Erstellen und Bearbeiten von Bedingungsfragmenten, die in interaktiver Kommunikation verwendet werden sollen - Bedingung ist einer der vier Arten von Dokumentfragmenten, die zum Erstellen interaktiver Kommunikation verwendet werden. Die anderen drei sind Texte, Listen und Layout-Fragmente.
seo-description: Creating and editing conditions to be used in Interactive Communications
uuid: c98f02d5-1769-46dd-ab35-6e8145a24939
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fe59d260-d392-4d6f-bb7e-2f2a1d701f51
docset: aem65
feature: Interactive Communication
exl-id: 0c0dc6a2-b889-4516-8e08-1e9d31be2cce
source-git-commit: 941e5d7574d31622f50e50e717c21cd2eba2e602
workflow-type: tm+mt
source-wordcount: '1498'
ht-degree: 64%

---

# Bedingungen in interaktiven Kommunikationen{#conditions-in-interactive-communications}

Erstellen und Bearbeiten von Bedingungsfragmenten, die in interaktiver Kommunikation verwendet werden sollen - Bedingung ist einer der vier Arten von Dokumentfragmenten, die zum Erstellen interaktiver Kommunikation verwendet werden. Die anderen drei sind Texte, Listen und Layout-Fragmente.

## Übersicht {#overview}

Bedingung ist ein Dokumentfragment, das Sie in eine interaktive Kommunikation aufnehmen können. Die anderen Dokumentfragmente sind [text](../../forms/using/texts-interactive-communications.md), Liste und Layout-Fragment. Mit Bedingungen können Sie ein oder mehrere kontextabhängige Elemente definieren, die basierend auf den bereitgestellten Daten und Regeln in eine interaktive Kommunikation einbezogen werden.

Beispiele:

* Zeigen Sie in einem Kreditkartenauszug die jährliche Kreditkartengebühr und das Kreditkartenbild basierend auf der Art der Kreditkarte des Kunden an.
* Zeigen Sie in einer fälligen Versicherungsprämie die Steuerberechnungen anhand der Steuern des Kunden an.

Die Assets in den Bedingungen, die basierend auf den angewendeten Regeln und den an die Regel übergebenen Werten gerendert werden. Die Regeln in den Bedingungen können Werte in den folgenden Datentypen überprüfen:

* Eigenschaft des zugeordneten Formulardatenmodells
* Beliebige Variablen, die Sie in der Bedingung erstellen 
* Zeichenfolgen
* Zahlen
* Mathematische Ausdrücke
* Datumsangaben

## Bedingung erstellen {#createcondition}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Bedingung]**.
1. Geben Sie die folgenden Daten an:

   * **[!UICONTROL Titel]**: (Optional) Geben Sie den Titel für die Bedingung ein. Titel müssen nicht eindeutig sein und können Sonderzeichen und nichtenglische Zeichen enthalten. Bedingungen werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Eigenschaften referenziert.
   * **[!UICONTROL Name]**: Der Name der Bedingung, innerhalb eines Ordners eindeutig. Es ist nicht möglich, dass zwei Dokumentfragmente (Text, Bedingung oder Liste) mit demselben Namen vorhanden sind, ungeachtet ihres jeweiligen Status. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.

   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung des Dokumentfragments ein.
   * **[!UICONTROL Formulardatenmodell]**: Wählen Sie optional das Optionsfeld Formulardatenmodell aus, um die Bedingung basierend auf einem Formulardatenmodell zu erstellen. Wenn Sie das Optionsfeld „Formulardatenmodell“ auswählen, wird das Feld **[!UICONTROL Formulardatenmodell]** angezeigt. Suchen Sie nach einem Formulardatenmodell und wählen Sie es aus. Stellen Sie beim Erstellen der Bedingung für eine interaktive Kommunikation sicher, dass Sie dasselbe Datenmodell verwenden, das Sie in der interaktiven Kommunikation verwenden möchten. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration](../../forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Um optional einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Wenn Sie diese Bedingung speichern, werden die neu hinzugefügten Tags erstellt.

1. Tippen Sie auf **[!UICONTROL Weiter]**.

   Die Seite „Bedingung erstellen“ wird angezeigt.

   ![createcondition](assets/createcondition.png)

1. Tippen Sie auf **[!UICONTROL Assets hinzufügen]**.

   Die Seite „Assets auswählen“ wird angezeigt und zeigt die verfügbaren Texte, Listen, Bedingungen und Bilder an, die in der Bedingung hinzugefügt werden können.

   >[!NOTE]
   >
   >Auf der Seite &quot;Assets auswählen&quot;werden nur nicht-basierte, neu erstellte Assets und FDM-basierte Assets angezeigt (die mit demselben FDM wie die zu erstellende Bedingung erstellt wurden).

1. Tippen Sie auf die entsprechenden Assets, um sie zur Aufnahme in die Bedingung auszuwählen, und tippen Sie dann auf **[!UICONTROL Fertig]**.

   Die Seite Bedingung erstellen wird angezeigt und listet die hinzugefügten Assets auf.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   Sie können die folgenden Optionen verwenden, um Assets in einer Bedingung zu verwalten:

   ![createconditionscreenassetsaddedannotated](assets/createconditionscreenassetsaddedannotated.png)

   **[A] Änderung ablehnen.** Tippen Sie auf dieses Symbol, um die Änderungen abzulehnen, die Sie möglicherweise an dem Asset und der Regel in der Bedingung vorgenommen haben.
   **[B] Änderung akzeptieren.** Tippen Sie auf dieses Symbol, um die Änderungen zu akzeptieren, die Sie an dem Asset und der Regel in der Bedingung vorgenommen haben.
   **[C] Asset duplizieren.** Tippen Sie auf dieses Symbol, um eine Kopie des Assets zusammen mit der angewendeten Regel (falls vorhanden) in der Bedingung zu erstellen. Anschließend können Sie mit der Bearbeitung der Regel und des Assets für duplizierte Assets fortfahren. Das Duplizieren eines Assets ist für das Erstellen ähnlicher Regeln nützlich, um alternative Assets basierend auf einem bestimmten Kontext anzuzeigen.
   **[D] Vorschau anzeigen.** Tippen Sie auf dieses Symbol, um auf der Seite „Bedingungen erstellen/bearbeiten“ eine Vorschau des Assets anzuzeigen.
   **„server“ neu anordnen.** Tippen und halten Sie dieses Symbol, um Assets innerhalb einer Bedingung per Drag-and-Drop neu anzuordnen.

   Sie können mithilfe der folgenden Optionen festlegen, wie sich die Bedingung zur Laufzeit verhält:

   * **Bewertung mehrerer Ergebnisse deaktiviert/Bewertung mehrerer Ergebnisse aktiviert**: Wenn diese Option aktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse aktiviert”), werden alle Bedingungen ausgewertet und das Ergebnis ist die Summe aller Bedingungen, die den Status „true“ haben. Wenn diese Option deaktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse deaktiviert“), wird nur die erste Bedingung, die „true“ ergibt, ausgewertet und wird zur Ausgabe der Bedingung.

   * **Seitenumbruch**: Wählen Sie diese Option (![break](assets/break.png)), um zwischen den Assets der Bedingungen einen Seitenumbruch hinzuzufügen. Wenn diese Option nicht ausgewählt ist (![nobreak](assets/nobreak.png)) und die Bedingung in der Druckausgabe über die aktuelle Seite hinausreichen würde, wird die gesamte Bedingung auf die nächste Seite verschoben, anstatt zwischen den Assets innerhalb der Bedingung einen Seitenumbruch einzufügen.

1. Tippen **[!UICONTROL Regel erstellen]** , um nach Bedarf Regeln zum Anzeigen oder Ausblenden der Assets hinzuzufügen. Informationen zur Verwendung von Variablen in den Regeln finden Sie unter [Erstellen von Variablen](#variables). Weitere Informationen finden Sie unter: [Hinzufügen von Regeln zur Bedingung](#ruleeditor).

   Die erstellten Regeln erscheinen in der Spalte REGEL im Bildschirm „Bedingung erstellen“.

   ![createconditionscreenrulesadded](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >Sie können Assets in Ihre Bedingung einfügen, für die bereits Regeln oder Wiederholungen gelten.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

   Die Bedingung wird erstellt. Jetzt können Sie die Bedingung als Baustein beim Erstellen einer interaktiven Kommunikation verwenden.

   >[!NOTE]
   >
   >Um eine neue oder bearbeitete Bedingung zu speichern, muss mindestens eine Regel für jedes der in der Bedingung hinzugefügten Assets vorhanden sein.

## Bedingung bearbeiten {#edit-a-condition}

Sie können eine Bedingung mit den folgenden Schritten bearbeiten. Sie können eine Bedingung auch in einer interaktiven Kommunikation bearbeiten, indem Sie im Popup-Menü „Fragment bearbeiten“ wählen.

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Navigieren Sie zu der Bedingung und wählen Sie sie aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Nehmen Sie die erforderlichen Änderungen an der Bedingung vor. Weitere Informationen zu den Informationen, die Sie in einer Bedingung ändern können, finden Sie unter [Bedingung erstellen](#createcondition).
1. Tippen Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**.

## Erstellen von Regeln in Bedingung {#ruleeditor}

Mit dem Regeleditor in einer Bedingung können Sie Regeln erstellen, um Assets basierend auf **voreingestellte Bedingungen**. Diese Bedingungen können wie folgt konfiguriert werden:

* Zeichenfolgen
* Zahlen
* Mathematische Ausdrücke
* Datumsangaben
* Eigenschaften des zugehörigen Formulardatenmodells
* Alle [variables](#variables) möglicherweise von Ihnen erstellte

### Regel in Bedingung erstellen {#create-rule-in-condition}

1. Tippen Sie beim Erstellen oder Bearbeiten einer Bedingung auf das Symbol ![ruleeditoricon](assets/ruleeditoricon.png) (Regel-Editor) für das betreffende Asset.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. Zusätzlich zu Zeichenfolge, Zahl, mathematischem Ausdruck und Datum stehen im Regeleditor auch folgende Elemente zum Erstellen von Anweisungen der Regeln zur Verfügung:

   * Eigenschaften des zugehörigen Formulardatenmodells
   * Alle [variables](#variables) die Sie erstellt haben.

   ![createruledialog](assets/createruledialog.png)

   Wählen Sie die geeignete Option aus, die ausgewertet werden soll.

   >[!NOTE]
   >
   >Die Sammlungseigenschaft wird nicht zum Erstellen von Regeln zum Anzeigen von Assets unterstützt. 

1. Wählen Sie den entsprechenden Operator aus, um die Regel auszuwerten, z. B. Gleich ist, Enthält und Beginnt mit.
1. Fügen Sie den auswertenden Ausdruck, die Zeichenfolge, das Datenmodell, die Eigenschaft, die Variable oder das Datum ein.

   ![Regel, um ein Asset anzuzeigen, wenn der Richtlinientyp „Standard“ ist](assets/ruleincondition.png)

   Regel, um ein Asset anzuzeigen, wenn der Richtlinientyp „Standard“ ist

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch auf ![icon_resize](assets/icon_resize.png) (Größe ändern) tippen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Über das erweiterte Vollbilddialogfeld können Sie [variables](#variables) , um Regeln zu erstellen. Tippen Sie erneut auf „Größe ändern“, um zum regulären Dialogfeld „Regel erstellen“ zurückzukehren.

   * Sie können auch mehrere Bedingungen in einer Regel erstellen.

1. Tippen Sie auf **[!UICONTROL Fertig]**.

   Die Regel wird auf das Asset angewendet.

## Erstellen und Verwenden von Variablen in einer Bedingung {#variables}

Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie auf ![icon_resize](assets/icon_resize.png) (Größe ändern) tippen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Das erweiterte Vollbilddialogfeld ermöglicht Folgendes:

* Erstellen und Verwenden von Variablen in der Regel
* Ziehen der Eigenschaften und Variablen des Datenmodells per Drag-and-Drop in die Regel

Tippen Sie erneut auf Größe ändern , um zum Dialogfeld Regel erstellen/Regel bearbeiten zurückzukehren.

### Erstellen von Variablen {#create-variables}

1. Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie auf ![icon_resize](assets/icon_resize.png) (Größe ändern) tippen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern.

   Der erweiterte Vollbildansichtsdialog erscheint.

   ![expandededitruledialog](assets/expandededitruledialog.png)

1. Tippen Sie im linken Bereich auf **[!UICONTROL Variablen]**.

   Der Variablenbereich wird angezeigt.

   ![expandededitrulevariables](assets/expandededitrulevariables.png)

1. Tippen Sie auf **[!UICONTROL Erstellen]**.

   Der Bereich Variablen erstellen wird angezeigt.

1. Geben Sie die folgenden Informationen ein und tippen Sie auf **[!UICONTROL Erstellen]**:

   * **[!UICONTROL Name]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ]**: Wählen Sie einen Typ der Variablen: Zeichenfolge, Zahl, Boolesch oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann im Feld **[!UICONTROL Werte]** durch Komma getrennte Werte an, die zulässig sind.

1. Tippen Sie auf **[!UICONTROL Erstellen]**.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in die Regel einzufügen, ziehen Sie sie in einen Platzhalter für eine Option in der Regel.
1. Nachdem Sie eine gültige Regel erstellt haben, tippen Sie auf **[!UICONTROL Fertig]**.

   Fahren Sie mit den notwendigen Änderungen in der Bedingung fort und speichern Sie sie.
