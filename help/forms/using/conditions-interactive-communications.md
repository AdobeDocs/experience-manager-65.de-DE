---
title: Bedingungen in interaktiven Kommunikationen
description: Erstellen und Bearbeiten von Bedingungsfragmenten für die Verwendung in interaktiven Kommunikationen – „Bedingung“ ist dabei eine der vier Arten von Dokumentfragmenten, die zum Aufbau interaktiver Kommunikationen verwendet werden. Die anderen drei sind Texte, Listen und Layout-Fragmente.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 0c0dc6a2-b889-4516-8e08-1e9d31be2cce
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1494'
ht-degree: 79%

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

   * **[!UICONTROL Tags]**: Um optional ein benutzerdefiniertes Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und wählen Sie die Option &quot;Eingabetaste&quot;aus. Wenn Sie diese Bedingung speichern, werden die neu hinzugefügten Tags erstellt.

1. Wählen Sie **[!UICONTROL Weiter]** aus.

   Die Seite „Bedingung erstellen“ wird angezeigt.

   ![createcondition](assets/createcondition.png)

1. Auswählen **[!UICONTROL Hinzufügen von Assets]**.

   Die Seite „Assets auswählen“ wird angezeigt und zeigt die verfügbaren Texte, Listen, Bedingungen und Bilder an, die in der Bedingung hinzugefügt werden können.

   >[!NOTE]
   >
   >Auf der Seite &quot;Assets auswählen&quot;werden nur nicht-basierte, neu erstellte Assets und FDM-basierte Assets angezeigt (die mit demselben FDM wie die zu erstellende Bedingung erstellt wurden).

1. Wählen Sie die entsprechenden Assets aus, die Sie in die Bedingung aufnehmen möchten, und wählen Sie dann **[!UICONTROL Fertig]**.

   Die Seite „Bedingung erstellen“ wird angezeigt und listet die hinzugefügten Assets auf.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   Sie können die folgenden Optionen verwenden, um Assets in einer Bedingung zu verwalten:

   ![createconditionscreenassetsaddedannotated](assets/createconditionscreenassetsaddedannotated.png)

   **[A] Änderung ablehnen.** Wählen Sie dieses Symbol aus, um die Änderungen abzulehnen, die Sie am Asset und an der Regel in der Bedingung vorgenommen haben.
   **[B] Änderung akzeptieren.** Wählen Sie dieses Symbol aus, um die Änderungen zu akzeptieren, die Sie in der Bedingung am Asset und an der Regel vorgenommen haben.
   **[C] Asset duplizieren.** Wählen Sie dieses Symbol aus, um eine Kopie des Assets zusammen mit der angewendeten Regel (falls vorhanden) in der Bedingung zu erstellen. Anschließend können Sie mit der Bearbeitung der Regel und des Assets für duplizierte Assets fortfahren. Das Duplizieren eines Assets ist für das Erstellen ähnlicher Regeln nützlich, um alternative Assets basierend auf einem bestimmten Kontext anzuzeigen.
   **[D] Vorschau anzeigen.** Wählen Sie dieses Symbol aus, um auf der Seite &quot;Bedingung erstellen/bearbeiten&quot;eine Vorschau des Assets anzuzeigen.
   **„server“ neu anordnen.** Wählen Sie dieses Symbol aus und halten Sie es gedrückt, um Assets per Drag-and-Drop in einer Bedingung neu anzuordnen.

   Sie können mithilfe der folgenden Optionen festlegen, wie sich die Bedingung zur Laufzeit verhält:

   * **Bewertung mehrerer Ergebnisse deaktiviert/Bewertung mehrerer Ergebnisse aktiviert**: Wenn diese Option aktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse aktiviert”), werden alle Bedingungen ausgewertet und das Ergebnis ist die Summe aller Bedingungen, die den Status „true“ haben. Wenn diese Option deaktiviert ist (angezeigt als „Bewertung mehrerer Ergebnisse deaktiviert“), wird nur die erste Bedingung, die „true“ ergibt, ausgewertet und wird zur Ausgabe der Bedingung.

   * **Seitenumbruch**: Wählen Sie diese Option (![break](assets/break.png)), um zwischen den Assets der Bedingungen einen Seitenumbruch hinzuzufügen. Wenn diese Option nicht ausgewählt ist (![nobreak](assets/nobreak.png)) und die Bedingung in der Druckausgabe über die aktuelle Seite hinausreichen würde, wird die gesamte Bedingung auf die nächste Seite verschoben, anstatt zwischen den Assets innerhalb der Bedingung einen Seitenumbruch einzufügen.

1. Auswählen **[!UICONTROL Regel erstellen]** , um nach Bedarf Regeln zum Anzeigen oder Ausblenden der Assets hinzuzufügen. Informationen zur Verwendung von Variablen in den Regeln finden Sie unter [Erstellen von Variablen](#variables). Weitere Informationen finden Sie unter: [Hinzufügen von Regeln zur Bedingung](#ruleeditor).

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
1. Auswählen **[!UICONTROL Speichern]** und wählen Sie **[!UICONTROL Schließen]**.

## Erstellen von Regeln in einer Bedingung {#ruleeditor}

Mit dem Regeleditor in einer Bedingung können Sie Regeln erstellen, um Assets basierend auf **voreingestellten Bedingungen** ein- oder auszublenden. Diese Bedingungen können basierend auf Folgendem erstellt werden:

* Zeichenfolgen
* Zahlen
* Mathematische Ausdrücke
* Datumswerten
* Eigenschaften des zugeordneten Formulardatenmodells
* [Variablen](#variables), die Sie ggf. erstellt haben

### Erstellen einer Regel in einer Bedingung {#create-rule-in-condition}

1. Wählen Sie beim Erstellen oder Bearbeiten einer Bedingung ![ruleeditoricon](assets/ruleeditoricon.png) (Regeleditor) für das relevante Asset.

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

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch ![icon_resize](assets/icon_resize.png) (Größe ändern), um das Dialogfeld Regel erstellen/Regel bearbeiten zu erweitern. Der erweiterte Vollbildansichtsdialog ermöglicht das Erstellen von [Variablen](#variables) zum Erstellen von Regeln. Wählen Sie erneut Größe ändern aus, um zum normalen Dialogfeld Regel erstellen zurückzukehren.

   * Sie können auch mehrere Bedingungen in einer Regel erstellen.

1. Wählen Sie **[!UICONTROL Fertig]**.

   Die Regel wird auf das Asset angewendet.

## Erstellen und Verwenden von Variablen in einer Bedingung {#variables}

Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie ![icon_resize](assets/icon_resize.png) (Größe ändern), um das Dialogfeld Regel erstellen/Regel bearbeiten zu erweitern. Das erweiterte Vollbilddialogfeld ermöglicht Folgendes:

* Erstellen und Verwenden von Variablen in der Regel
* Ziehen der Eigenschaften und Variablen des Datenmodells per Drag-and-Drop in die Regel

Wählen Sie erneut Größe ändern aus, um zum Dialogfeld Regel erstellen/Regel bearbeiten zurückzukehren.

### Erstellen von Variablen {#create-variables}

1. Beim Erstellen oder Bearbeiten einer Regel in einer Bedingung können Sie ![icon_resize](assets/icon_resize.png) (Größe ändern), um das Dialogfeld Regel erstellen/Regel bearbeiten zu erweitern.

   Der erweiterte Vollbildansichtsdialog erscheint.

   ![expandededitruledialog](assets/expandededitruledialog.png)

1. Wählen Sie im linken Bereich die Option **[!UICONTROL Variablen]**.

   Der Variablenbereich wird angezeigt.

   ![expandededitrulevariables](assets/expandededitrulevariables.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Der Bereich „Variablen erstellen“ wird angezeigt.

1. Geben Sie die folgenden Informationen ein und wählen Sie **[!UICONTROL Erstellen]**:

   * **[!UICONTROL Name]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ]**: Wählen Sie einen Typ der Variablen: Zeichenfolge, Zahl, Boolesch oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann im Feld **[!UICONTROL Werte]** durch Komma getrennte Werte an, die zulässig sind.

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in die Regel einzufügen, ziehen Sie sie in einen Platzhalter für eine Option in der Regel.
1. Nachdem Sie eine gültige Regel erstellt haben, wählen Sie **[!UICONTROL Fertig]**.

   Fahren Sie mit den notwendigen Änderungen in der Bedingung fort und speichern Sie sie.
