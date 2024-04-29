---
title: Bedingungen in interaktiven Kommunikationen
description: Erstellen und Bearbeiten von Bedingungsfragmenten für die Verwendung in interaktiven Kommunikationen – „Bedingung“ ist dabei eine der vier Arten von Dokumentfragmenten, die zum Aufbau interaktiver Kommunikationen verwendet werden. Die anderen drei sind Texte, Listen und Layout-Fragmente.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 0c0dc6a2-b889-4516-8e08-1e9d31be2cce
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1494'
ht-degree: 100%

---

# Bedingungen in interaktiven Kommunikationen{#conditions-in-interactive-communications}

Erstellen und Bearbeiten von Bedingungsfragmenten für die Verwendung in interaktiven Kommunikationen – „Bedingung“ ist dabei eine der vier Arten von Dokumentfragmenten, die zum Aufbau interaktiver Kommunikationen verwendet werden. Die anderen drei sind Texte, Listen und Layout-Fragmente.

## Übersicht {#overview}

Bedingung ist ein Dokumentfragment, das Sie in eine interaktive Kommunikation einschließen können. Die anderen Dokumentfragmente sind [Text](../../forms/using/texts-interactive-communications.md), Liste und Layout-Fragment. Mit Bedingungen können Sie ein oder mehrere kontextabhängige Elemente definieren, die basierend auf den bereitgestellten Daten und Regeln in eine interaktive Kommunikation einbezogen werden.

Beispiele:

* Zeigen Sie auf einer Kreditkartenabrechnung die Jahresgebühr für die Kreditkarte und das Kreditkartenbild an, je nach Art der Kreditkarte der Kundin bzw. des Kunden.
* Zeigen Sie in einer fälligen Versicherungsprämie die Steuerberechnungen anhand der Steuern der Kundin bzw. des Kunden an.

Die Assets in den Bedingungen, die basierend auf den angewendeten Regeln und den an die Regel übergebenen Werten gerendert werden. Die Regeln in den Bedingungen können Werte in den folgenden Datentypen überprüfen:

* Eigenschaft des zugeordneten Formulardatenmodells
* Beliebige Variablen, die Sie in der Bedingung erstellen 
* Zeichenfolgen
* Zahlen
* Mathematische Ausdrücke
* Datumswerten

## Erstellen einer Bedingung {#createcondition}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Bedingung]**.
1. Geben Sie die folgenden Daten an:

   * **[!UICONTROL Titel]**: (Optional) Geben Sie den Titel für die Bedingung ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nicht-englische Zeichen enthalten. Bedingungen werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Eigenschaften referenziert.
   * **[!UICONTROL Name]**: Der Name der Bedingung, innerhalb eines Ordners eindeutig. Es ist nicht möglich, dass zwei Dokumentfragmente (Text, Bedingung oder Liste) mit demselben Namen vorhanden sind, ungeachtet ihres jeweiligen Status. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.

   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung der Dokumentfragmente ein.
   * **[!UICONTROL Formulardatenmodell]**: Wählen Sie optional das Optionsfeld „Formulardatenmodell“, um die Bedingung auf der Grundlage eines Formulardatenmodells zu erstellen. Wenn Sie das Optionsfeld „Formulardatenmodell“ auswählen, wird das Feld **[!UICONTROL Formulardatenmodell]** angezeigt. Suchen Sie nach einem Formulardatenmodell und wählen Sie es aus. Achten Sie bei der Erstellung der Bedingung für eine interaktive Kommunikation darauf, dass Sie das gleiche Datenmodell verwenden, das Sie auch in der interaktiven Kommunikation verwenden wollen. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration](../../forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Um optional ein benutzerdefiniertes Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Wenn Sie diese Bedingung speichern, werden die neu hinzugefügten Tags erstellt.

1. Wählen Sie **[!UICONTROL Weiter]** aus.

   Die Seite „Bedingung erstellen“ wird angezeigt.

   ![createcondition](assets/createcondition.png)

1. Wählen Sie **[!UICONTROL Assets hinzufügen]** aus.

   Die Seite „Assets auswählen“ wird angezeigt und zeigt die verfügbaren Texte, Listen, Bedingungen und Bilder an, die in der Bedingung hinzugefügt werden können.

   >[!NOTE]
   >
   >Nur nicht-basierte, neu erstellte Assets und FDM-basierte Assets (erstellt mit demselben FDM wie die zu erstellende Bedingung) werden auf der Seite „Assets auswählen“ angezeigt.

1. Wählen Sie die entsprechenden Assets für die Bedingung aus und klicken Sie dann auf **[!UICONTROL Fertig]**.

   Die Seite „Bedingung erstellen“ wird angezeigt und listet die hinzugefügten Assets auf.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   Sie können die folgenden Optionen verwenden, um Assets in einer Bedingung zu verwalten:

   ![createconditionscreenassetsaddedannotated](assets/createconditionscreenassetsaddedannotated.png)

   **[A] Änderung ablehnen.** Wählen Sie dieses Symbol aus, um die Änderungen abzulehnen, die Sie möglicherweise an dem Asset und der Regel in der Bedingung vorgenommen haben.
   **[B] Änderung akzeptieren.** Wählen Sie dieses Symbol aus, um die Änderungen zu akzeptieren, die Sie an dem Asset und der Regel in der Bedingung vorgenommen haben.
   **[C] Asset duplizieren.** Wählen Sie dieses Symbol aus, um eine Kopie des Assets zusammen mit der angewendeten Regel (falls vorhanden) in der Bedingung zu erstellen. Anschließend können Sie mit der Bearbeitung der Regel und des Assets für duplizierte Assets fortfahren. Das Duplizieren eines Assets ist für das Erstellen ähnlicher Regeln nützlich, um alternative Assets basierend auf einem bestimmten Kontext anzuzeigen.
   **[D] Vorschau anzeigen.** Wählen Sie dieses Symbol aus, um auf der Seite „Bedingungen erstellen/bearbeiten“ eine Vorschau des Assets anzuzeigen.
   **„server“ neu anordnen.** Wählen Sie dieses Symbol aus und halten Sie es, um Assets innerhalb einer Bedingung per Drag-and-Drop neu anzuordnen.

   Sie können mithilfe der folgenden Optionen festlegen, wie sich die Bedingung zur Laufzeit verhält:

   * **Bewertung mehrerer Ergebnisse deaktiviert/Bewertung mehrerer Ergebnisse aktiviert**: Wenn diese Option aktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse aktiviert”), werden alle Bedingungen ausgewertet und das Ergebnis ist die Summe aller Bedingungen, die den Status „true“ haben. Wenn diese Option deaktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse deaktiviert“), wird nur die erste Bedingung, die „true“ ergibt, ausgewertet und wird zur Ausgabe der Bedingung.

   * **Seitenumbruch**: Wählen Sie diese Option (![break](assets/break.png)), um zwischen den Assets der Bedingungen einen Seitenumbruch hinzuzufügen. Wenn diese Option nicht ausgewählt ist (![nobreak](assets/nobreak.png)) und die Bedingung in der Druckausgabe über die aktuelle Seite hinausreichen würde, wird die gesamte Bedingung auf die nächste Seite verschoben, anstatt zwischen den Assets innerhalb der Bedingung einen Seitenumbruch einzufügen.

1. Wählen Sie **[!UICONTROL Regel erstellen]** aus, um nach Bedarf Regeln zum Anzeigen oder Ausblenden der Assets hinzuzufügen. Informationen zur Verwendung von Variablen in den Regeln finden Sie unter [Erstellen von Variablen](#variables). Weitere Informationen finden Sie unter: [Hinzufügen von Regeln zur Bedingung](#ruleeditor).

   Die erstellten Regeln erscheinen in der Spalte REGEL im Bildschirm „Bedingung erstellen“.

   ![createconditionscreenrulesadded](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >Sie können Assets in Ihre Bedingung einfügen, für die bereits Regeln oder Wiederholungen gelten.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   Die Bedingung wird erstellt. Jetzt können Sie die Bedingung als Baustein beim Erstellen einer interaktiven Kommunikation verwenden.

   >[!NOTE]
   >
   >Um eine neue oder bearbeitete Bedingung zu speichern, muss mindestens eine Regel für jedes der in der Bedingung hinzugefügten Assets vorhanden sein.

## Bearbeiten einer Bedingung {#edit-a-condition}

Sie können eine Bedingung mit den folgenden Schritten bearbeiten. Sie können eine Bedingung auch in einer interaktiven Kommunikation bearbeiten, indem Sie im Popup-Menü „Fragment bearbeiten“ wählen.

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Navigieren Sie zu der Bedingung und wählen Sie sie aus.
1. Wählen Sie **[!UICONTROL Bearbeiten]** aus.
1. Nehmen Sie die erforderlichen Änderungen an der Bedingung vor. Weitere Informationen zu den Informationen, die Sie in einer Bedingung ändern können, finden Sie unter [Bedingung erstellen](#createcondition).
1. Wählen Sie **[!UICONTROL Speichern]** und dann **[!UICONTROL Schließen]** aus.

## Erstellen von Regeln in einer Bedingung {#ruleeditor}

Mit dem Regeleditor in einer Bedingung können Sie Regeln erstellen, um Assets basierend auf **voreingestellten Bedingungen** ein- oder auszublenden. Diese Bedingungen können basierend auf Folgendem erstellt werden:

* Zeichenfolgen
* Zahlen
* Mathematische Ausdrücke
* Datumswerten
* Eigenschaften des zugeordneten Formulardatenmodells
* [Variablen](#variables), die Sie ggf. erstellt haben

### Erstellen einer Regel in einer Bedingung {#create-rule-in-condition}

1. Wählen Sie beim Erstellen oder Bearbeiten einer Bedingung das Symbol ![ruleeditoricon](assets/ruleeditoricon.png) (Regel-Editor) für das betreffende Asset aus.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. Zusätzlich zu Zeichenfolge, Zahl, mathematischem Ausdruck und Datum steht im Regeleditor Folgendes zum Erstellen der Regelanweisungen zur Verfügung:

   * Eigenschaften des zugeordneten Formulardatenmodells
   * [Variablen](#variables), die Sie ggf. erstellt haben.

   ![createruledialog](assets/createruledialog.png)

   Wählen Sie die geeignete Option aus, die ausgewertet werden soll.

   >[!NOTE]
   >
   >Die Sammlungseigenschaft wird nicht zum Erstellen von Regeln zum Anzeigen von Assets unterstützt. 

1. Wählen Sie den entsprechenden Operator aus, um die Regel auszuwerten, z. B. Gleich ist, Enthält und Beginnt mit.
1. Fügen Sie den auswertenden Ausdruck, die Zeichenfolge, das Datenmodell, die Eigenschaft, die Variable oder das Datum ein.

   ![Regel, um ein Asset anzuzeigen, wenn der Richtlinientyp „Standard“ ist](assets/ruleincondition.png)

   Regel, um ein Asset anzuzeigen, wenn der Richtlinientyp „Standard“ ist

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch ![icon_resize](assets/icon_resize.png) (Größe ändern) auswählen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Der erweiterte Vollbildansichtsdialog ermöglicht das Erstellen von [Variablen](#variables) zum Erstellen von Regeln. Wählen Sie erneut „Größe ändern“ aus, um zum regulären Dialogfeld „Regel erstellen“ zurückzukehren.

   * Sie können auch mehrere Bedingungen in einer Regel erstellen.

1. Wählen Sie **[!UICONTROL Fertig]**.

   Die Regel wird auf das Asset angewendet.

## Erstellen und Verwenden von Variablen in einer Bedingung {#variables}

Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie ![icon_resize](assets/icon_resize.png) (Größe ändern) auswählen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Das erweiterte Vollbilddialogfeld ermöglicht Folgendes:

* Erstellen und Verwenden von Variablen in der Regel
* Ziehen der Eigenschaften und Variablen des Datenmodells per Drag-and-Drop in die Regel

Wählen Sie erneut „Größe ändern“ aus, um zum Dialogfeld „Regel erstellen/Regel bearbeiten“ zurückzukehren.

### Erstellen von Variablen {#create-variables}

1. Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie ![icon_resize](assets/icon_resize.png) (Größe ändern) auswählen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern.

   Der erweiterte Vollbildansichtsdialog erscheint.

   ![expandededitruledialog](assets/expandededitruledialog.png)

1. Wählen Sie im linken Bereich die Option **[!UICONTROL Variablen]** aus.

   Der Variablenbereich wird angezeigt.

   ![expandededitrulevariables](assets/expandededitrulevariables.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Der Bereich „Variablen erstellen“ wird angezeigt.

1. Geben Sie die folgenden Informationen ein und wählen Sie **[!UICONTROL Erstellen]** aus:

   * **[!UICONTROL Name]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ]**: Wählen Sie einen Typ der Variablen: Zeichenfolge, Zahl, Boolesch oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann im Feld **[!UICONTROL Werte]** durch Komma getrennte Werte an, die zulässig sind.

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in die Regel einzufügen, ziehen Sie sie in einen Platzhalter für eine Option in der Regel.
1. Nachdem Sie eine gültige Regel erstellt haben, wählen Sie **[!UICONTROL Fertig]** aus.

   Nehmen Sie ggf. weitere Änderungen in der Bedingung vor und speichern Sie sie.
