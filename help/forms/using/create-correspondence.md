---
title: Korrespondenz erstellen
seo-title: Korrespondenz erstellen
description: Nachdem Sie eine Briefvorlage erstellt haben, können Sie diese verwenden, um Korrespondenz in AEM Forms zu erstellen, indem Sie Daten, Inhalte und Anhänge verwalten.
seo-description: Nachdem Sie eine Briefvorlage erstellt haben, können Sie diese verwenden, um Korrespondenz in AEM Forms zu erstellen, indem Sie Daten, Inhalte und Anhänge verwalten.
uuid: 48cf2b26-c9b4-4127-9ea0-1b36addbff60
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 87742cb2-357b-421f-b79d-e355887ddec0
docset: aem65
feature: Korrespondenzverwaltung
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '3722'
ht-degree: 67%

---


# Korrespondenz erstellen{#create-correspondence}

## Verwenden Sie zum Erstellen von Korrespondenz die Benutzeroberfläche „Korrespondenz erstellen“.{#create-correspondence-in-the-create-correspondence-user-interface}

Nachdem eine [Briefvorlage in Correspondence Management](../../forms/using/create-letter.md) erstellt wurde, kann der Endbenutzer/Agent/Schadensregulierer den Brief in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;öffnen und durch Eingabe von Daten, Einrichten von Inhalten und Verwalten von Anlagen eine Korrespondenz erstellen. Schließlich kann der Schadensregulierer oder Agent den Inhalt im Vorschaumodus verwalten und den Brief senden.

### Vorschau von Korrespondenz {#preview-a-correspondence}

Wählen Sie den Brief für die Vorschau wie folgt aus:

1. Tippen Sie auf der Seite &quot;Briefe&quot;auf **Auswählen**.
1. Wählen Sie den entsprechenden Brief aus, indem Sie darauf tippen.

   ![Brief auswählen](assets/1_selectletter.png)

   Brief auswählen

1. Wählen Sie für einen datenwörterbuchbasierten Brief **Vorschau** > **Vorschau**. Oder wählen Sie für einen auf ein Nicht-Daten-Wörterbuch basierenden Brief **Vorschau**. Sie können auch die Maus über einen Brief bewegen (ohne ihn auszuwählen) und auf das Symbol „Briefvorschau“ tippen, um davon eine Vorschau anzuzeigen.

   >[!NOTE]
   >
   >Wenn kein Datenwörterbuch mit den Brief verknüpft ist, wird die Briefvorschau geöffnet. Andernfalls zeigt Correspondence Management im Menü &quot;Vorschau&quot;die Optionen &quot;Vorschau&quot;und &quot;Benutzerdefiniert&quot;an, wenn der Brief auf einem Datenwörterbuch basiert, und Sie können eine der beiden Optionen auswählen. Sie können auch Testdaten mit einem Datenwörterbuch verknüpfen. Wenn mit dem [Datenwörterbuch Testdaten](../../forms/using/data-dictionary.md#p-working-with-test-data-p) verknüpft sind, wird bei Auswahl der Option &quot;Vorschau&quot;die normale Vorschau mit den ausgefüllten Testdaten geöffnet.

1. Um eine Korrespondenz während der Vorschau wiedergeben zu können, müssen Sie entweder Administrator oder Teil einer der folgenden Gruppen sein:

   * forms-users (zur Vorschau auf der Autoreninstanz)
   * cm-agent-users (für Rendering auf Veröffentlichungsinstanz)

   Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, bitten Sie den Administrator um den entsprechenden Zugriff. Weitere Informationen zum Erstellen und Hinzufügen von Benutzern zu Gruppen finden Sie unter [Hinzufügen von Benutzern oder Gruppen zu einer Gruppe](/help/sites-administering/security.md). Wenn Sie versuchen, eine Korrespondenz ohne die entsprechenden Berechtigungen wiederzugeben, wird die 404-Fehlerseite angezeigt.

1. Wenn Sie **Vorschau**> **Benutzerdefiniert** wählen, wird ein Dialogfeld geöffnet. Wählen Sie im Dialogfeld eine Datendatei entsprechend dem Datenwörterbuch aus, mit der der Brief Vorschau werden soll, und wählen Sie **Vorschau**. Eine Datendatei wird basierend auf einem Datenwörterbuch für einen bestimmten Brief erstellt: Weitere Informationen zur Datendatei finden Sie unter [Datenwörterbuch](../../forms/using/data-dictionary.md#p-working-with-test-data-p).

   ![Brief in der Vorschau anzeigen](assets/8_previewcustomdatafile.png)

1. Die HTML-Vorschau des Briefs (Vorschau für Formulare auf Mobilgeräten) wird geöffnet, wobei die Registerkarte „Daten“ standardmäßig aktiv ist.

   Weitere Informationen zu Formularen für Mobilgeräte und den von ihnen unterstützten Funktionen finden Sie unter [Funktionsunterschiede zwischen Mobile Forms und PDF forms](https://helpx.adobe.com/de/livecycle/help/mobile-forms/feature-differentiation-mobile-forms-pdf.html).

   Es gibt drei Registerkarten: Daten, Inhalt und Anlagen. Wenn keine Datenelemente (Platzhaltervariablen und Layout-Felder) vorhanden sind, wird der Brief direkt in der Inhaltsansicht geöffnet. Die Registerkarte „Anlagen“ ist nur verfügbar, wenn Anlagen vorhanden sind oder der Bibliothekszugriff aktiviert ist.

   >[!NOTE]
   >
   >Weitere Informationen zum Wechseln zwischen HTML- oder PDF-Darstellungsmodus der Brief-Vorschau finden Sie unter [Ändern des Darstellungsmodus des Briefs](#changerenditionmode). Weitere Informationen zur PDF-Unterstützung in Correspondence Management und AEM finden Sie unter [Beendigung der NPAPI-Browser-Plugins und deren Auswirkungen auf ](https://helpx.adobe.com/de/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html) und [PDF forms auf HTML5 Forms](https://helpx.adobe.com/de/aem-forms/kb/pdf-forms-to-html5-forms.html).

### Daten eingeben {#enterdata}

Füllen Sie auf der Registerkarte „Daten“ die verfügbaren Layout-Felder und Platzhalter aus.

1. Geben Sie die Daten und Inhaltsvariablen wie benötigt in den Feldern ein. Füllen Sie alle erforderlichen Felder (mit einem Sternchen (*) gekennzeichnet) aus, um die Schaltfläche **Senden** zu aktivieren.

   Tippen Sie auf einen Datenfeldwert in der HTML-Briefvorschau, um das entsprechende Datenfeld in der Registerkarte „Daten“ zu markieren.

   ![Geben Sie Daten in den Brief](assets/2_enterdata.png) ![2_1_enterdata ein](assets/2_1_enterdata.png)

### Inhalt verwalten {#managecontent}

In der Registerkarte verwalten Sie den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen im Brief.

1. Wählen Sie **Inhalt**. Correspondence Management zeigt die Registerkarte &quot;Inhalt&quot;des Briefs an.

   ![Registerkarte „Inhalt“ - Modul im Inhalt markieren](assets/3_content.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ die Inhaltsmodule wie benötigt. Um den Fokus auf das relevante Inhaltsmodul in der Inhaltshierarchie zu verlegen, können Sie entweder auf die betreffende Zeile oder den betreffenden Absatz in der Briefvorschau oder direkt auf das Inhaltsmodul in der Inhaltshierarchie tippen.

   Beispielsweise ist die Zeile „Wir haben … geprüft“ in der unten stehenden Grafik ausgewählt und das zutreffenden Inhaltsmodul wird auf der Registerkarte „Inhalt“ ausgewählt.

   ![4_highlightmoduleincontent](assets/4_highlightmoduleincontent.png)

   Wenn Sie auf der Registerkarte &quot;Inhalt&quot;oder &quot;Daten&quot;links oben in der HTML-Vorschau auf &quot;Ausgewählte Module markieren&quot;( ![highlightsselectedModuleIncontentccr](assets/highlightselectedmodulesincontentccr.png)) tippen, können Sie die Funktion deaktivieren oder aktivieren, um zum Inhalts-/Datenmodul zu wechseln, wenn der entsprechende Text, Absatz oder das Datenfeld in der Vorschau &quot;Brief&quot;ausgewählt ist.

   Weitere Informationen zu den Aktionen, die für verschiedene Module in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;verfügbar sind, finden Sie unter [Aktionen und Informationen in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;](#actions-and-info-available-in-the-create-correspondence-content-tab).

1. Verwenden Sie zum Suchen nach Inhaltsmodulen das Suchfeld. Geben den Namen oder Titel des Inhaltsmoduls ganz oder teilweise ein, um in der Korrespondenz nach diesem zu suchen.
1. Tippen Sie auf das Symbol &quot;Anzeigen&quot;( ![display](assets/display.png)) vor einer Liste, einem Text-, Bedingungs- oder Zielgruppe-Bereich, um sie im Brief ein- oder auszublenden.
1. Um ein Inline- oder bearbeitbares Textmodul zu bearbeiten, tippen Sie auf das entsprechende **Bearbeitungssymbol ( ![edittextmodule](assets/edittextmodule.png)) oder klicken Sie bei Dublette auf das entsprechende Textmodul in der Vorschau.**

   Das System zeigt einen Texteditor zum Bearbeiten und Formatieren des Textes an.

   Die normale Rechtschreibprüfung Ihres Browsers überprüft die Rechtschreibung im Texteditor. Um die Rechtschreib- und Grammatikprüfung zu verwalten, können Sie die Einstellungen für die Rechtschreibprüfung in Ihrem Browser bearbeiten oder Browser-Plugins/-Addons für die Prüfung von Rechtschreibung und Grammatik installieren.

   Sie können auch die verschiedenen Tastaturbefehle im Texteditor verwenden, um Text zu verwalten, zu bearbeiten und zu formatieren. Weitere Informationen zu den Tastaturbefehlen [Texteditor](/help/forms/using/keyboard-shortcuts.md#correspondence-management) in Correspondence Management-Tastaturbefehlen.

   ![5_edittextmodule](assets/5_edittextmodule.png)

   Möglicherweise möchten Sie einen Absatz des Textes, der in einer anderen Anwendung des Dokuments vorhanden ist, wiederverwenden. Sie können Text direkt kopieren und einfügen, z. B. von MS Word, HTML-Seiten oder von einer anderen Anwendung.

   Sie können einen Textabsatz in ein Textmodul kopieren. Beispielsweise haben Sie ein MS-Word-Dokument mit einer Liste mit Aufzählungszeichen mit Aufenthaltsnachweisen:

   ![pastetextmsword](assets/pastetextmsword.png)

   Sie können den Text direkt aus dem MS Word-Dokument in ein bearbeitbares Textmodul kopieren. Die Formatierung wie die Liste mit Aufzählungszeichen, die Schriftart und Textfarbe wird im Textmodul beibehalten.

   ![pastetexteditablemodule](assets/pastetexteditablemodule.png)

   >[!NOTE]
   >
   >Die Formatierung des eingefügten Textes hat jedoch einige[ Einschränkungen](https://helpx.adobe.com/aem-forms/kb/cm-copy-paste-text-limitations.html).

   Sie können den Text und die Zahlen im Brief mithilfe der Tabulatortaste einziehen. Beispielsweise können Sie die Tabulatortaste verwenden, um mehrere Textspalten in einer Liste in einem tabellarischen Format auszurichten.

   ![tabspaces](assets/tabspaces.png)

   Beispielsweise können Sie die Tabulatortaste verwenden, um mehrere Textspalten in einer Liste in einem tabellarischen Format auszurichten.

   >[!NOTE]
   >
   >Weitere Informationen zum Einrichten des Tabulatorabstands für Textmodule und Buchstaben finden Sie unter [Weitere Informationen zum Anordnen von Text](https://helpx.adobe.com/aem-forms/kb/cm-tab-spacing-limitations.html) mithilfe des Tabulatorabstands.

1. Falls erforderlich, fügen Sie Sonderzeichen in die Korrespondenz ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

   * Währungssymbole wie €,¥ und £
   * Mathematische Symbole wie z. B. □, , ^ und ^
   * Interpunktionssymbole wie ‟ und&quot;

   ![Sonderzeichen](assets/specialcharacters.png)

   Correspondence Management enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung](../../forms/using/custom-special-characters.md) hinzufügen.

1. Um Teile eines Textes in einem bearbeitbaren Inline-Modul hervorzuheben, wählen Sie den Text aus und tippen Sie auf „Hervorhebungsfarbe“.

   ![letterbackgroundcolor](assets/letterbackgroundcolor.png)

   Sie können entweder direkt auf eine Grundfarbe `**[A]**` in der Palette &quot;Grundfarben&quot;tippen oder auf **Wählen Sie**, nachdem Sie den Schieberegler `**[B]**` verwendet haben, um die entsprechende Farbschattierung auszuwählen.

   Optional können Sie auch auf der Registerkarte &quot;Erweitert&quot;die gewünschte Farbe für Farbton, Helligkeit und Sättigung `**[C]**` auswählen, um die exakte Farbe zu erstellen, und dann auf `**[D]**` tippen, um die Farbe anzuwenden und den Text zu markieren.

   ![textbackgroundcolor](assets/textbackgroundcolor.png)

1. Nehmen Sie die gewünschten Änderungen an Inhalt und Format vor und tippen Sie auf **Speichern**. Tippen Sie auf ( ![editnextmoduleccr](assets/editnextmoduleccr.png)), um zwischen bearbeitbaren Textmodulen zu wechseln, oder auf **Speichern und Weiter**, um die Änderungen zu speichern und zum nächsten bearbeitbaren Textmodul zu wechseln.
1. Das System zeigt auch die nicht ausgefüllten Variablen für jeden der Zweige an. Wenn es keine nicht ausgefüllten Variablen gibt, werden nicht ausgefüllte Variablen als „0“ angegeben. Wenn eine nicht ausgefüllte Variable vorhanden ist, können Sie auf einen Zweig tippen, um ihn zu erweitern und die nicht ausgefüllte Variable zu finden. Verwenden Sie die Symbolleiste &quot;Inhalt&quot;, um Inhalte zu löschen, den Einzug des Inhalts zu erhöhen/zu verringern und Seitenumbrüche vor/nach dem Inhalt einzufügen.

   Sie können Seitenumbrüche sowohl vor als auch nach den Datenmodulen einfügen, selbst wenn sie Teil von Listen und Bedingungen sind.

1. Tippen Sie auf Inhaltsvariable öffnen/schließen ( ![opencontentvariables](assets/opencontentvariables.png)), um die Inhaltsvariablen zu öffnen und sie entsprechend zu füllen.
1. Nachdem Sie die nicht ausgefüllte Variable korrekt ausgefüllt haben, wird die Anzahl der nicht ausgefüllten Variablen auf „0“ eingestellt.

   In der Benutzeroberfläche „Korrespondenz erstellen“ wird die Anzahl nicht ausgefüllter Variablen auf jeder Ebene der Hierarchie der Module angezeigt, die mindestens eine Variable enthalten. Wenn ein Modul nicht ausgefüllte Variablen enthält, wird deren Anzahl auf Variablen-, Modul-, Zielbereichs- und Briefvorlagenebene angezeigt.

   Die Anzahl der nicht ausgefüllten Variablen umfasst:

   * Nur ungeschützte Datenwörterbuch und Platzhaltervariablen. Die Variablenanzahl umfasst nicht Layout- oder geschützte Datenwörterbuchvariablen.
   * Obligatorische Felder.
   * Layout-Felder, wenn sie obligatorisch und an den Benutzer gebunden sind.
   * Nur eindeutige Variableninstanzen. Wenn ein Modul, Zielbereich oder eine Briefvorlage zwei oder mehr Instanzen derselben Variable enthält, wird die Anzahl als „1“ (eins) angezeigt. Allerdings wird für jede der Instanzen „1“ als Anzahl angezeigt.

   Die Anzahl der nicht ausgefüllten Variablen umfasst keine deaktivierten Module. Wenn ein Modul in einer Briefvorlage aber nicht im Brief enthalten ist, wird die Anzahl der nicht ausgefüllten Variablen in diesem Modul nicht angezeigt.

   Für Zielbereich, Modul und Variable wird die Anzahl auf der rechten Seite jedes Objekts in der Briefvorlage angezeigt. Für die gesamte Vorlage wird die Anzahl jedoch in der Statusleiste &quot;Korrespondenz erstellen&quot;angezeigt.

   Die Module in einer Briefvorlage zeigen die Anzahl nicht ausgefüllter Variable an wie folgt:

   * **** TextZeigt die Summe der eindeutigen nicht ausgefüllten Platzhaltervariablen und Datenwörterbuchelemente im Textmodul an.
   * **** BedingungZeigt die Summe der eindeutigen nicht ausgefüllten Bedingungsvariablen an, die in der Bedingung enthalten sind, und der Variablen, die in den resultierenden Modulen enthalten sind.
   * **** ListZeigt die Summe aller eindeutigen nicht ausgefüllten Variablen an, die in den der Liste zugewiesenen Modulen enthalten sind.
   * **Zielgruppe** areaZeigt die Summe aller eindeutigen nicht ausgefüllten Variablen an, die in den Modulen enthalten sind, die dem Zielgruppen-Bereich zugewiesen sind.

   Beachten Sie Folgendes zu Variablen mit Standardwerten:

   * Ein boolesches Variablenfeld ergibt standardmäßig *false*. Die Variable wird jedoch als nicht ausgefüllt erfasst. Dies bedeutet, dass die Variablenanzahl alle booleschen Variablenfelder mit dem Wert *false* enthält.

   * Ein numerisches Variablenfeld ergibt standardmäßig *0 (Null)*. Die Variable wird jedoch als nicht ausgefüllt erfasst. Dies bedeutet, dass die Variablenanzahl alle numerischen Variablenfelder mit dem Wert *0 (Null)* umfasst.



#### Aktionen und Informationen auf der Registerkarte „Inhalt“ in „Korrespondenz erstellen“{#actions-and-info-available-in-the-create-correspondence-content-tab}

**Zielbereich**

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Inline-Text einfügen: Fügt neues Textmodul ein.
* Reihenfolge sperren (Info): Gibt an, dass die Reihenfolge der Inhalte nicht geändert werden kann.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Zielbereich an.

**Modul**

* Auswahl (Augenauswahl): Schließt Modul aus dem Brief ein oder aus.
* Aufzählungszeichen überspringen (gilt für Listenmodule und ihre untergeordneten Module): Überspringt Aufzählungszeichen in einem bestimmten Modul.
* Seitenumbruch bevor (anwendbar für untergeordnete Module des Zielbereichs): Fügt Seitenumbruch vor dem Modul ein.
* Seitenumbruch nach (gilt für untergeordnete Module des Bereichs Zielgruppe): Fügt einen Seitenumbruch vor dem Modul ein.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Zielbereich an.
* Bearbeiten (nur Textmodule): Öffnen Sie den Rich-Text-Editor zum Bearbeiten des Textmoduls.
* Datenformat (Text- und Bedingungsmodule): Öffnen Sie alle Variablen des Moduls.

**Listenmodul**

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Inhaltsbibliothek: Öffnet die Inhaltsbibliothek, um der Liste Module hinzuzufügen.
* Liste einrichten (nur verschachtelte Liste):
* Reihenfolge sperren (Info): Gibt an, dass die Reihenfolge der Listenelemente nicht geändert werden kann.

### Anlagen verwalten {#manage-attachments}

1. Wählen Sie **Anlagen**. Correspondence Management zeigt die verfügbaren Anlagen an, die beim Erstellen der Briefvorlage eingerichtet wurden.
1. Sie können festlegen, dass keine Anhänge mit dem Brief versendet werden sollen, indem Sie auf das Symbol für Anzeige tippen, und Sie können auf das Kreuz im Anhang tippen, um ihn aus dem Brief zu entfernen. Für Anhänge, die beim Erstellen der Briefvorlage als Obligatorisch definiert wurden, sind die Symbole „Anzeigen“ und „Löschen“ deaktiviert.
1. Tippen Sie auf das Symbol &quot;Bibliothekszugriff&quot;( ![Bibliothekszugriff](assets/libraryaccess.png)), um auf die Inhaltsbibliothek zuzugreifen und DAM-Assets als Anlagen einzufügen.

   >[!NOTE]
   >
   >Das Symbol „Bibliothekszugriff“ ist nur verfügbar, wenn der Bibliothekszugriff beim Verfassen des Briefes aktiviert wurde.

1. Wenn die Reihenfolge der Anlagen beim Erstellen der Korrespondenz nicht gesperrt war, können Sie die Reihenfolge der Anlagen neu anordnen, indem Sie eine Anlage auswählen und auf die Pfeile nach unten oder nach oben tippen.

   Weitere Informationen finden Sie unter[ Anlagenübermittlung](#attachmentdelivery).

### Inhalte in der Vorschau verwalten und Brief übermitteln  {#manage-content-in-preview-and-submit-the-letter}

Sie können Ihren Zwecken entsprechende Änderungen an Layout und Inhalt des Briefs vornehmen und diesen an verschiedene nachfolgende Prozesse übermitteln.

1. Um den gesamten bearbeitbaren Inhalt im Brief hervorzuheben, tippen Sie auf **Bearbeitbare Abschnitte markieren**.

   Die bearbeitbaren Inhalte des Briefs werden mit grauem Hintergrund markiert.

   ![Bearbeitbare Inhalte markieren](assets/4_highlightmoduleincontent-1.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ die Inhaltsmodule wie benötigt. Um den Fokus auf das relevante Inhaltsmodul in der Inhaltshierarchie zu verlegen, können Sie entweder auf die betreffende Zeile oder den betreffenden Absatz in der Briefvorschau oder direkt auf das Inhaltsmodul in der Inhaltshierarchie tippen.

   Beispielsweise wurde in der unten gezeigten Abbildung auf die Zeile „Um uns Zugriff zu gewähren...“ ausgewählt und das dazugehörige Inhaltsmodul auf der Registerkarte „Inhalt“ ausgewählt.

   Durch Tippen auf &quot;Markieren Sie ausgewählte Module im Inhalt&quot;( ![marklightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) können Sie die Funktion deaktivieren oder aktivieren, um das Inhaltsmodul auf der Registerkarte &quot;Inhalt&quot;zu markieren, wenn auf den entsprechenden Text, Absatz oder das Datenfeld in der Vorschau &quot;Brief&quot;getippt wird.

   Weitere Informationen zu den Aktionen, die für verschiedene Module in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;verfügbar sind, finden Sie unter [Aktionen und Informationen in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;](#actions-and-info-available-in-the-create-correspondence-content-tab).

1. Um dem Brief einen Seitenumbruch hinzuzufügen, tippen Sie auf die Stelle, an der Sie einen Seitenumbruch einfügen möchten, und wählen Sie &quot;Seitenumbruch vor&quot;bzw. &quot;Seitenumbruch nach&quot;( ![Seitenumbruch nach](assets/pagebreakbeforeafter.png)).

   Ein Platzhalter für einen expliziten Seitenumbruch wird in den Brief eingefügt. Sie können die Wirkung eines expliziten Seitenumbruchs anzeigen, indem Sie die reduzierte PDF-Vorschau aufrufen.

   >[!NOTE]
   >
   >Da Mobile Forms Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Es ist allerdings möglich, Kopf- und Fußzeilen explizit im Layout (pro Seite) festzulegen, sodass sie in der Mobile Forms-Vorschau angezeigt werden. Auch leere Seiten im Brief (falls vorhanden) werden nicht in der Vorschau für Mobile Forms angezeigt.

   ![Expliziter Seitenumbruch](assets/8_pagebreak.png)

1. Um den Brief als Entwurf zu speichern, an dem Sie später weiter arbeiten können, tippen Sie auf „Als Entwurf speichern“. Diese Option können Sie nur verwenden, wenn der Brief[ veröffentlicht werden soll](../../forms/using/publishing-unpublishing-forms.md#publishanasset). Weitere Informationen finden Sie unter[ Speichern von Entwürfen und Einreichen von Entwurfsinstanzen](#savingdrafts).

   ![Saveasdraft](assets/saveasdraft.png)

   Das Dialogfeld „Entwurfsbriefname“ wird mit der Briefinstanz-ID angezeigt. Sie können optional diese ID bearbeiten. Notieren Sie sich die Brief-ID und tippen Sie anschließend auf **Fertig**. Sie können diese ID später verwenden, um den [Briefentwurf neu zu laden](submit-letter-topostprocess.md#reloaddraft).

1. Um den Brief als reduzierte PDF-Datei mit exaktem Layout und Seitenumbrüchen wie gesendet Vorschau, tippen Sie auf ( ![Vorschau](assets/preview.png))-Vorschau.

   Der Brief wird als reduzierte PDF-Datei angezeigt. Das reduzierte PDF ist die genaue Darstellung des Briefs mit den richtigen Schriftarten, Umbrüchen und dem Layout in der Form, in der er gesendet wird.  

   >[!NOTE]
   >
   >Wenn Sie Mozilla Firefox und den HTML-Darstellungstyp verwenden, achten Sie für die Vorschau des Briefs als reduzierte PDF-Datei darauf, nicht das Acrobat-Plugin, sondern das native Browser-Plugin zu verwenden. Um das native Browser-Plugin auszuwählen, wählen Sie in den Einstellungen von Mozilla Firefox die Option „Vorschau in Firefox“ für den PDF-Inhaltstyp.

1. Wenn die reduzierte PDF-Vorschau zufriedenstellend ist, tippen Sie auf **Senden**, um den Brief zu senden. Wenn Sie Änderungen am Brief vornehmen möchten, tippen Sie auf **Vorschau beenden**, um zur Vorschau &quot;Korrespondenz erstellen&quot;des Briefs zurückzukehren und Änderungen am Brief vorzunehmen. Wenn Sie auf &quot;Senden&quot;tippen und die Konfiguration &quot;Briefinstanz verwalten&quot;in der Veröffentlichungsinstanz aktiviert ist, wird die Briefinstanz &quot;Senden&quot;generiert.

   Weitere Informationen finden Sie unter Speichern von Entwürfen und Einreichen von Entwurfsinstanzen.

   Sie können den Brief auch als Entwurf speichern, um später Änderungen daran vorzunehmen.

   Nachdem Sie die erforderlichen Änderungen vorgenommen haben, können Sie den Brief von der HTML5-Vorschau aus senden oder erneut auf „Vorschau“ klicken, um die reduzierte PDF-Ausgabe zu prüfen.

   Informationen zu Unterschieden zwischen HTML5-Formularen und PDF forms finden Sie unter [Funktionsunterschiede zwischen HTML5-Formularen und PDF forms](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md).

## Speichern von Entwürfen und Senden von Briefinstanzen {#savingdrafts}

Wenn ein Brief in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;wiedergegeben wird, können Sie den Brief als angezeigt speichern.

Es gibt zwei Arten von Briefinstanzen, die gespeichert werden können: Entwurfsinstanz und Sendeinstanz.

* **Entwurfsinstanz**: Entwurfsinstanz erfasst den aktuellen Status des Briefs, den Sie in der Vorschau anzeigen. Um eine Entwurfsinstanz zu speichern, muss zuerst sichergestellt werden, dass der Brief und alle Assets, die der Brief referenziert im Status „Veröffentlicht“ sind. Weitere Informationen zum Veröffentlichen eines Briefs finden Sie unter[ Veröffentlichen von Assets](../../forms/using/publishing-unpublishing-forms.md#publishanasset). Sie müssen einen Brief veröffentlichen, bevor Sie ihn als Entwurf speichern können, da Sie, wenn Sie einen Brief veröffentlichen, eine Version des Briefs, der abhängige Assets und Daten erstellen. Die veröffentlichte Version eines Briefs kann nicht von Ihnen oder einem anderen Benutzer bearbeitet werden und kann ohne unerwartete Diskrepanzen von der veröffentlichten Version zu einem späteren Zeitpunkt wiederhergestellt werden. Sie können zu einem späteren Zeitpunkt zu dieser Instanz zurückkehren und von Ihrem Schritt aus fortfahren.

* **Sendeinstanz**: Sendeinstanzen erfassen den Status des Briefes zum Sendezeitpunkt. Die Sendeinstanz speichert den PDF-Status der Briefinstanz, nachdem sie zusammen mit den vom Benutzer in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;eingegebenen Daten nachbearbeitet wurde.

Solche Instanzen können nur gespeichert werden, wenn der Brief in der öffentlichen Instanz angezeigt wird. Das Speichern von Instanzen ist standardmäßig deaktiviert. Führen Sie die folgenden Schritte durch, um das Speichern von Briefinstanzen zu aktivieren.

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console Configuration für Ihren Server unter Verwendung der folgenden URL: https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr
1. Suchen Sie nach **[!UICONTROL Correspondence Management Configurations]** und klicken Sie darauf.
1. Überprüfen Sie die Konfiguration **[!UICONTROL Briefinstanzen im Veröffentlichungsmodus verwalten]** und klicken Sie dann auf **[!UICONTROL Speichern]**.

Wenn das Speichern von Briefinstanzen gespeichert ist, können Sie wählen, wo Sie die Briefinstanzen speichern möchten. Zum Speichern der Briefinstanzen gibt es zwei Optionen: „Lokal speichern“ oder „Remote speichern“.

### Lokal speichern {#local-save}

Briefinstanzen werden in der Veröffentlichungsinstanz gespeichert und in der Autorinstanz rückwärtsrepliziert.

### Remote Speichern {#remote-save}

Diese Option ist für Personen vorgesehen, die bezüglich des Speicherns von Daten in Veröffentlichungsinstanzen haben, die sich normalerweise außerhalb der Firewall des Unternehmens befinden. Wenn die Option „Remote Speichern“ aktiviert ist, werden die Instanzen nicht in der Veröffentlichungsoptionen gespeichert. Sie werden remote vom verarbeitenden Autor gespeichert, der über die LiveCycle Client SDK-Konfigurationen angegeben wird.

#### Aktivieren von „Remote Speichern“  {#enable-remote-save}

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console Configuration für Ihren Server unter Verwendung der folgenden URL: `https://<server>:<port>/<contextpath>/system/console/configMgr`
1. Suchen Sie nach **[!UICONTROL Correspondence Management Configurations]** und klicken Sie darauf.
1. Suchen Sie die Konfiguration **[!UICONTROL Remote Speichern]**, überprüfen Sie sie und klicken Sie auf **[!UICONTROL Speichern]**.

#### Angeben der Einstellungen für Prozessautor {#specify-processing-author-settings}

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console Configuration für Ihren Server unter Verwendung der folgenden URL: `https://<server>:<port>/<contextpath>/system/console/configMgr`

   ![Konfiguration der Adobe Experience Manager-Web-Konsole](assets/2configmanager.png)

1. Suchen Sie auf dieser Seite Adobe LiveCycle Client SDK-Konfiguration und erweitern Sie sie durch Klicken auf.

1. Geben Sie in der URL des Verarbeitungsservers den Namen Ihres LiveCycle-Servers ein, geben Sie die Anmeldeinformationen ein und klicken Sie dann auf **Speichern**.

   ![Namen und Anmeldeinformationen Ihres LiveCycle-Servers eingeben](assets/3configmanager.png)

1. Legen Sie bei Bedarf den Benutzernamen und das Kennwort fest, mit dem Sie auf den Server zugreifen möchten.

#### Anlagenübermittlung {#attachmentdelivery}

* Die Briefanlagen sind verfügbare Nachbearbeitungen in der PDF-Datei, die nach der Briefsendung erstellt wird.
* Wenn der Brief mit serverseitigen APIs als interaktive oder nicht interaktive PDF gerendert wird, enthält er PDF-Anlagen.
* Wenn ein mit einer Briefvorlage verknüpfter Nachbearbeitungsprozess beim Senden oder Abschließen der Korrespondenz in der Benutzeroberfläche „Korrespondenz erstellen“ aufgerufen wird, werden die Anlagen als Parameter List&lt;com.adobe.idp.Document> in AttachmentDocs übergeben.
* Vordefinierte Übermittlungsmechanismen, wie z. B. E-Mail und Drucken, übermitteln Anhänge zusammen mit einer PDF der generierten Korrespondenz.

## Darstellungsmodi der Briefvorschau: Mobile Forms- und PDF-Vorschau  {#rendition-modes-of-letter-preview-mobile-forms-preview-and-pdf-preview}

AEM Forms Correspondence Management zeigt Briefe in der Benutzeroberfläche „Korrespondenz erstellen“ im HTML-Format an. Correspondence Management unterstützt jedoch weiterhin die Wiederherstellung der PDF-Vorschau anstelle der HTML-Vorschau. Weitere Informationen zum Wechseln zwischen HTML- und PDF-Modus für die Vorschau finden Sie unter [Ändern des Darstellungsmodus des Briefs](#changerenditionmode).

Die folgenden Vorteile und Funktionen stehen jeweils bei der HTML- und PDF-Vorschau zur Verfügung.

**Vorteile der Mobile Forms-/HTML-Vorschau**

* **Markieren des zugehörigen Datenfelds durch Tippen auf einen Datenfeldwert**: Indem Sie in der Benutzeroberfläche „Korrespondenz erstellen“ auf den Wert eines Datenfelds im Brief tippen, können Sie das dazugehörige Datenfeld auf der Registerkarte „Daten“ markieren. Weitere Informationen finden Sie unter [Daten eingeben](#enterdata).

* **Browserunterstützung**: In Browsern wird NPAPI immer weniger unterstützt, was sich auf die PDF-Vorschau von Briefen auswirkt. Die HTML-/Mobile Forms-Vorschau von Briefen ist davon nicht betroffen.
* **Markieren bearbeitbarer Inhalte in einem Brief**: In der Benutzeroberfläche „Korrespondenz erstellen“ können Sie durch Klicken auf „Bearbeitbare Inhalte markieren“ den gesamten bearbeitbaren Inhalt in Grau hervorheben. Weitere Informationen finden Sie unter [Inhalt verwalten](#managecontent).

`<li>` `<li>Benefits of HTML preview  <ul>   <li>Right to left</li>   <li>NPAPI</li>   <li>Highlight Editable Content</li>  </ul> </li>` `<li>Benefits of PDF preview  <ul>   <li>Page Break</li>   <li>Final Preview</li>  </ul> </li>`
`<li>` `<li>Benefits of HTML preview  <ul>   <li>Right to left</li>   <li>NPAPI</li>   <li>Highlight Editable Content</li>  </ul> </li>` `<li>Benefits of PDF preview  <ul>   <li>Page Break</li>   <li>Final Preview</li>  </ul> </li>`  **Vorteile der PDF-Vorschau**

* **Seitenumbruch**: In der PDF-Vorschau eine Vorschau können Sie genau erkennen, wie die Seitenumbrüche im Brief sich auf dessen Ausgabe auswirken.
* **Abschließende Vorschau**: In der PDF-Vorschau können die genaue Formatierung und das Erscheinungsbild des Briefs für die Ausgabe angezeigt werden.

Weitere Informationen zur Skriptunterstützung in PDF-Formularen finden Sie unter [Skriptunterstützung](https://help.adobe.com/en_US/livecycle/11.0/ScriptingSupport/index.html).

Weitere Informationen zur Skriptunterstützung in HTML5-Formularen finden Sie unter [Skriptunterstützung für HTML5-Formulare](/help/forms/using/scripting-support.md).

### Ändern des Darstellungsmodus des Briefs {#changerenditionmode}

In der Benutzeroberfläche „Korrespondenz erstellen“ wird standardmäßig HTML oder Mobile Forms zum Rendern der Briefvorschau verwendet. Die Mobile Forms-Vorschau kann in beliebigen Browsern problemlos gerendert werden, da sie das native Plugin des Browsers verwendet und daher keine zusätzlichen Plugins benötigt werden. Sie können zum Briefvorschaumodus PDF wechseln. Allerdings können aufgrund von Browserbeschränkungen Probleme bei verschiedenen Funktionen der interaktiven PDF-Vorschau des Briefs auftreten.

Weitere Informationen zur Browserkompatibilität mit der Briefinterstellung finden Sie unter [Abbruch der NPAPI-Browser-Plugins und deren Auswirkungen](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html).

Um den Vorschaumodus des Briefs zu ändern, führen Sie die folgenden Schritte aus:

1. Gehen Sie zu `https://[system]:'port'/system/console/configMgr` und melden Sie sich bei Bedarf als Administrator an.
1. Wechseln Sie zu **[!UICONTROL Correspondence Management-Konfigurationen]** > **[!UICONTROL Darstellungstyp]** und wählen Sie **HTML-Darstellung** (Standard) oder **PDF-Darstellung**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

