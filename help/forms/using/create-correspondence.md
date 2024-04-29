---
title: Korrespondenz erstellen
description: Nachdem Sie eine Briefvorlage erstellt haben, können Sie sie dafür verwenden, in AEM Forms Korrespondenz zu erstellen, indem Sie Daten, Inhalte und Anhänge verwalten.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: da966787-a3b9-420f-8b7c-f00d05c61d43
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '3832'
ht-degree: 100%

---

# Korrespondenz erstellen{#create-correspondence}

## Korrespondenz erstellen in der Benutzeroberfläche „Korrespondenz erstellen“ {#create-correspondence-in-the-create-correspondence-user-interface}

Nachdem [in Correspondence Management eine Briefvorlage erstellt wurde](../../forms/using/create-letter.md), kann der Endbenutzer/Agent/Schadensregulierer den Brief in der Benutzeroberfläche „Korrespondenz erstellen“ öffnen und durch Eingabe von Daten, Einrichten von Inhalten und Verwalten von Anlagen eine Korrespondenz erstellen. Schließlich kann der Schadensregulierer oder Agent den Inhalt im Vorschaumodus verwalten und den Brief senden.

### Vorschau einer Korrespondenz {#preview-a-correspondence}

Wählen Sie den Brief für die Vorschau wie folgt aus:

1. Wählen Sie auf der Seite „Briefe“ die Option **Auswählen** aus.
1. Wählen Sie den entsprechenden Brief aus, indem Sie darauf tippen.

   ![Brief auswählen](assets/1_selectletter.png)

   Brief auswählen

1. Wählen Sie für einen auf einem Datenwörterbuch basierenden Brief **Vorschau** > **Vorschau**. Oder wählen Sie für einen Brief, der nicht auf einem Datenwörterbuch basiert, **Vorschau** aus. Sie können auch den Mauszeiger über einen Brief bewegen (ohne ihn auszuwählen) und das Symbol „Briefvorschau“ auswählen, um eine Vorschau zu erhalten.

   >[!NOTE]
   >
   >Wenn dem Brief kein Datenwörterbuch zugeordnet ist, wird die Briefvorschau geöffnet. Wenn der Brief jedoch auf einem Datenwörterbuch basiert, zeigt Correspondence Management im Menü „Vorschau“ die Optionen „Vorschau“ und „Benutzerdefiniert“ an, zwischen denen Sie wählen können. Sie können auch Testdaten mit einem Datenwörterbuch verknüpfen. Wenn [Testdaten mit dem Datenwörterbuch verbunden sind](../../forms/using/data-dictionary.md#p-working-with-test-data-p), wird bei Auswahl der Option „Vorschau“ die normale Vorschau, ausgefüllt mit den Testdaten, angezeigt.

1. Damit Sie eine Korrespondenz während der Vorschau rendern können, sollten Sie entweder ein Administrator oder Teil einer der folgenden Gruppen sein:

   * forms-users (zur Vorschau auf der Autoreninstanz)
   * cm-agent-users (für Rendering auf Veröffentlichungsinstanz)

   Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, bitten Sie den Administrator um den entsprechenden Zugriff. Weitere Informationen zum Erstellen und Hinzufügen von Benutzern zu Gruppen finden Sie unter [Hinzufügen von Benutzern oder Gruppen zu einer Gruppe](/help/sites-administering/security.md). Wenn Sie versuchen, ohne die entsprechende Berechtigung eine Korrespondenz zu rendern, wird die Fehlerseite 404 angezeigt.

1. Wenn Sie **Vorschau** > **Benutzerdefiniert** wählen, wird ein Dialogfeld geöffnet. Wählen Sie in diesem Dialogfeld eine dem Datenwörterbuch entsprechende Dateidatei für die Vorschau des Briefs und dann **Vorschau**. Eine Datendatei wird basierend auf einem Datenwörterbuch für einen bestimmten Brief erstellt: Weitere Informationen zur Datendatei finden Sie unter [Datenwörterbuch](../../forms/using/data-dictionary.md#p-working-with-test-data-p).

   ![Brief in der Vorschau anzeigen](assets/8_previewcustomdatafile.png)

1. Die HTML-Vorschau des Briefs (Vorschau für Formulare auf Mobilgeräten) wird geöffnet, wobei die Registerkarte „Daten“ standardmäßig aktiv ist.

   Weitere Informationen zu Formularen auf Mobilgeräten und den hierfür unterstützen Funktionen finden Sie unter[ Funktionsunterschiede zwischen Mobile Forms und PDF-Formularen](https://helpx.adobe.com/de/livecycle/help/mobile-forms/feature-differentiation-mobile-forms-pdf.html).

   Es gibt drei Registerkarten: Daten, Inhalt und Anlagen. Wenn keine Datenelemente (Platzhaltervariablen und Layout-Felder) vorhanden sind, wird der Brief direkt in der Inhaltsansicht geöffnet. Die Registerkarte „Anlagen“ ist nur verfügbar, wenn Anlagen vorhanden sind oder der Bibliothekszugriff aktiviert ist.

   >[!NOTE]
   >
   >Weitere Informationen zum Umschalten der Briefvorschau zwischen HTML- und PDF-Darstellungsmodus finden Sie unter [Ändern des Darstellungsmodus des Briefs](#changerenditionmode). Weitere Informationen zur PDF-Unterstützung in Correspondence Management und AEM finden Sie unter [Auslauf der Unterstützung für das NPAPI-Browser-Plug-in und seine Auswirkungen](https://helpx.adobe.com/de/acrobat/kb/change-in-support-for-acrobat-and-reader-plug-ins-in-modern-web-.html). <!-- and [PDF Forms to HTML5 Forms](https://helpx.adobe.com/aem-forms/kb/pdf-forms-to-html5-forms.html). THIS URL IS A 404 AND NO SUITABLE REPLACEMENT TOPIC WAS FOUND. CONSIDER DELETING OR ADDING NEW LINK. COMMENTING OUT SO USERS DON'T CLICK IT. -->

### Eingeben von Daten {#enterdata}

Füllen Sie auf der Registerkarte „Daten“ die verfügbaren Layout-Felder und Platzhalter aus.

1. Geben Sie die Daten- und Inhaltsvariablen nach Bedarf in die Felder ein. Füllen Sie alle mit einem Sternchen (&#42;) gekennzeichneten Pflichtfelder aus, um die Schaltfläche **Senden** zu aktivieren.

   Wählen Sie einen Datenfeldwert in der HTML-Briefvorschau aus, um das entsprechende Datenfeld auf der Registerkarte „Daten“ zu markieren.

   ![Eingabe von Daten in den Brief](assets/2_enterdata.png) ![2_1_enterdata](assets/2_1_enterdata.png)

### Inhalt verwalten {#managecontent}

Verwalten Sie auf der Registerkarte „Inhalt“ den Inhalt wie Dokumentfragmente und Inhaltsvariablen im Brief.

1. Wählen Sie **Inhalt**. Correspondence Management zeigt die Registerkarte „Inhalt“ des Briefes an.

   ![Registerkarte „Inhalt“ - Modul im Inhalt markieren](assets/3_content.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ nach Bedarf die Inhaltsmodule. Um den Fokus auf das relevante Inhaltsmodul in der Inhaltshierarchie zu verschieben, können Sie entweder die betreffende Zeile oder den betreffenden Absatz in der Briefvorschau auswählen oder in der Inhaltshierarchie direkt das Inhaltsmodul auswählen.

   Beispielsweise wird in der unten gezeigten Abbildung die Zeile „Wir haben geprüft…“ ausgewählt, und das entsprechende Inhaltsmodul wird auf der Registerkarte „Inhalt“ ausgewählt.

   ![4_highlightmoduleincontent](assets/4_highlightmoduleincontent.png)

   Auf der Registerkarte „Inhalt“ oder „Daten“ können Sie durch Tippen auf „Ausgewählte Module hervorheben“ (![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) oben links in der HTML-Briefvorschau die Funktionalität deaktivieren oder aktivieren, zum Inhalts-/Datenmodul zu wechseln, wenn der entsprechende Text, Absatz oder das Datenfeld in der Briefvorschau ausgewählt wird.

   Weitere Informationen zu Aktionen, die für verschiedene Module in der Benutzeroberfläche „Korrespondenz erstellen“ verfügbar sind, finden Sie unter [In der Benutzeroberfläche „Korrespondenz erstellen“ verfügbare Vorgehensweisen und Informationen](#actions-and-info-available-in-the-create-correspondence-content-tab).

1. Verwenden Sie das Feld „Suchen“, um nach Inhaltsmodulen zu suchen. Geben Sie den vollständigen oder teilweisen Namen oder Titel des Inhaltsmoduls ein, um in der Korrespondenz danach zu suchen.
1. Wählen Sie das Symbol ![Anzeigen](assets/display.png) vor einer Liste, einem Text, einer Bedingung oder einem Zielbereich aus, um das entsprechende Element in einem Brief anzuzeigen oder auszublenden.
1. Um ein Inline- oder editierbares Textmodul zu bearbeiten, wählen Sie das entsprechende Symbol zum **Bearbeiten** (![edittextmodule](assets/edittextmodule.png)) aus oder doppelklicken Sie auf das entsprechende Textmodul in der Briefvorschau.

   Das System zeigt einen Texteditor zum Bearbeiten und Formatieren des Textes an.

   Die Standard-Rechtschreibprüfung in Ihrem Browser überprüft die Rechtschreibung im Texteditor. Um die Rechtschreib- und Grammatikprüfung zu verwalten, können Sie die Rechtschreibprüfungseinstellungen Ihres Browsers bearbeiten oder Plug-ins bzw. Add-ons für den Browser installieren, um Rechtschreibung und Grammatik zu überprüfen.

   Sie können die verschiedenen Tastaturbefehle im Texteditor verwenden, um Text zu verwalten, zu bearbeiten und zu formatieren. Weitere Informationen zu den Tastaturbefehlen für den [Texteditor](/help/forms/using/keyboard-shortcuts.md#correspondence-management) finden Sie unter „Correspondence Management-Tastaturbefehle“.

   ![5_edittextmodule](assets/5_edittextmodule.png)

   Möglicherweise möchten Sie einen Absatz des Textes, der in einer anderen Anwendung des Dokuments vorhanden ist, wiederverwenden. Sie können Text direkt kopieren und einfügen, z. B. aus Microsoft Word, HTML-Seiten oder einem anderen Programm.

   Sie können einen oder mehrere Textabsätze in ein bearbeitbares Textmodul kopieren und einfügen. Sie könnten beispielsweise ein MS Word-Dokument mit einer Liste mit Aufzählungszeichen für zulässige Aufenthaltsnachweise wie das folgende haben:

   ![pastetextmsword](assets/pastetextmsword.png)

   Sie können den Text direkt aus dem MS Word-Dokument in ein bearbeitbares Textmodul kopieren. Die Formatierung (wie Liste mit Aufzählungszeichen, Schriftart und Textfarbe) wird im Textmodul beibehalten.

   ![pastetexteditablemodule](assets/pastetexteditablemodule.png)

   >[!NOTE]
   >
   >Die Formatierung des eingefügten Textes hat jedoch einige [Einschränkungen](https://helpx.adobe.com/de/aem-forms/kb/cm-copy-paste-text-limitations.html).

   Sie können den Text und die Zahlen im Brief mithilfe der Tabulatortaste einziehen. Beispielsweise können Sie die Tabulatortaste verwenden, um mehrere Textspalten in einer Liste zu einem tabellarischen Format auszurichten.

   ![tabspaces](assets/tabspaces.png)

   Beispielsweise können Sie die Tabulatortaste verwenden, um mehrere Textspalten in einer Liste in einem tabellarischen Format auszurichten.

   >[!NOTE]
   >
   >Weitere Informationen zum Einrichten von Tabulatorabständen für Ihre Textmodule und Briefe finden Sie unter [Weitere Informationen zur Verwendung von Tabulatorabständen zum Anordnen von Text](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).

1. Falls erforderlich, fügen Sie Sonderzeichen in die Korrespondenz ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

   * Währungssymbole wie €,￥ und £
   * Mathematische Symbole wie ∑, √, ∂ und ^
   * Satzzeichen wie „ und “

   ![specialcharacters](assets/specialcharacters.png)

   Correspondence Management enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](../../forms/using/custom-special-characters.md).

1. Um Teile eines Textes in einem bearbeitbaren Inline-Modul hervorzuheben, markieren Sie den Text und wählen Sie „Hervorhebungsfarbe“ aus.

   ![letterbackgroundcolor](assets/letterbackgroundcolor.png)

   Sie können entweder direkt eine Grundfarbe `**[A]**` in der Grundfarbenpalette oder **Auswählen** auswählen, nachdem Sie den Regler `**[B]**` verwendet haben, um den entsprechenden Farbton der Farbe auszuwählen.

   Optional können Sie auch auf der Registerkarte „Erweitert“ die gewünschten Werte für Farbton, Helligkeit und Sättigung `**[C]**` wählen, um die Farbe präzise festzulegen, und dann „Auswählen“ `**[D]**` auswählen, um die Farbe zum Hervorheben des Textes anzuwenden.

   ![textbackgroundcolor](assets/textbackgroundcolor.png)

1. Nehmen Sie die benötigten Änderungen an Inhalt und Format vor und wählen Sie **Speichern**. Durch Auswählen von![editnextmoduleccr](assets/editnextmoduleccr.png) wechseln Sie zwischen den bearbeitbaren Textmodulen, durch Auswählen von **Speichern und weiter** speichern Sie die Änderungen und wechseln zum nächsten bearbeitbaren Textmodul.
1. Das System zeigt auch die nicht ausgefüllten Variablen für jede der Verzweigungen an. Wenn keine nicht ausgefüllten Variablen vorhanden sind, werden nicht ausgefüllte Variablen als „0“ angezeigt. Wenn eine nicht ausgefüllte Variable vorhanden ist, können Sie eine Verzweigung auswählen, um sie zu erweitern und die nicht ausgefüllte Variable zu finden. Verwenden Sie die Symbolleiste „Inhalt“, um Inhalte zu löschen, den Einzug eines Inhalts zu vergrößern oder zu verringern und Seitenumbrüche vor oder nach einem Inhalt einzufügen.

   Sie können Seitenumbrüche sowohl vor als auch nach den Datenmodulen einfügen, selbst wenn sie Teil von Listen und Bedingungen sind.

1. Wählen Sie „Inhaltsvariable öffnen/schließen“ (![opencontentvariables](assets/opencontentvariables.png)) aus, um die Inhaltsvariablen zu öffnen und sie entsprechend auszufüllen.
1. Nachdem Sie die nicht ausgefüllte Variable korrekt ausgefüllt haben, wird die Anzahl der nicht ausgefüllten Variablen auf „0“ eingestellt.

   In der Benutzeroberfläche „Korrespondenz erstellen“ wird die Anzahl nicht ausgefüllter Variablen auf jeder Ebene der Hierarchie der Module angezeigt, die mindestens eine Variable enthalten. Wenn ein Modul nicht ausgefüllte Variablen enthält, wird deren Anzahl auf Variablen-, Modul-, Zielbereichs- und Briefvorlagenebene angezeigt.

   Die Anzahl der nicht ausgefüllten Variablen umfasst:

   * Nur ungeschützte Datenwörterbuch- und Platzhaltervariablen. Die Variablenanzahl umfasst keine Layout- oder geschützten Datenwörterbuchvariablen.
   * Obligatorische Felder.
   * Layout-Felder, wenn sie obligatorisch und an den Benutzer gebunden sind.
   * Nur eindeutige Variableninstanzen. Wenn ein Modul, ein Zielbereich oder eine Briefvorlage zwei oder mehr Instanzen derselben Variablen enthält, wird die Anzahl als „1“ (eins) angezeigt. Allerdings wird für jede der Instanzen „1“ als Anzahl angezeigt.

   Die Anzahl der nicht ausgefüllten Variablen umfasst keine nicht ausgewählten Module. Wenn ein Modul in einer Briefvorlage, aber nicht im Brief enthalten ist, wird die Anzahl der nicht ausgefüllten Variablen in diesem Modul nicht angezeigt.

   Für den Zielbereich, das Modul und die Variable wird die Anzahl rechts neben jedem Objekt in der Briefvorlage angezeigt. Für die gesamte Vorlage wird die Anzahl jedoch in der Statusleiste von „Korrespondenz erstellen“ angezeigt.

   Die Module in einer Briefvorlage zeigen die Anzahl nicht ausgefüllter Variable an wie folgt:

   * **Text**: Zeigt die Anzahl der eindeutigen nicht ausgefüllten Platzhaltervariablen und Datenwörterbuchelemente an, die im Textmodul enthalten sind.
   * **Bedingung**: Zeigt die Anzahl der eindeutigen nicht ausgefüllten Bedingungsvariablen an, die in der Bedingung enthalten sind, und der Variablen, die in den resultierenden Modulen enthalten sind.
   * **Liste**: Zeigt die Anzahl aller eindeutigen nicht ausgefüllten Variablen an, die in den Modulen enthalten sind, die der Liste zugewiesen wurden.
   * **Zielbereich**: Gibt die Anzahl aller eindeutigen nicht ausgefüllten Variablen an, die in den Modulen enthalten sind, die dem Zielbereich zugewiesen wurden.

   Beachten Sie Folgendes zu Variablen mit Standardwerten:

   * Ein boolesches Variablenfeld verwendet standardmäßig *false*. Die Variable wird jedoch als nicht ausgefüllt erfasst. Dies bedeutet, dass die Variablenanzahl alle booleschen Variablenfelder mit dem Wert *false* umfasst.

   * Ein numerisches Variablenfeld ist standardmäßig auf *0 (null)* gesetzt. Die Variable wird jedoch als nicht ausgefüllt erfasst. Dies bedeutet, dass die Variablenanzahl alle numerischen Variablenfelder mit dem Wert *0 (Null)* umfasst.

#### Auf der Registerkarte „Korrespondenzinhalt erstellen“ verfügbare Aktionen und Informationen {#actions-and-info-available-in-the-create-correspondence-content-tab}

**Zielbereich**

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Inline-Text einfügen: Fügt ein neues Textmodul ein.
* Reihenfolge sperren (Info): Gibt an, dass die Reihenfolge der Listenelemente nicht geändert werden kann.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Zielbereich an.

**Modul**

* Auswahl (Augensymbol): Schließt das Modul in den Brief ein bzw. aus ihm aus.
* Aufzählungszeichen überspringen (gilt für Listenmodule und ihre untergeordneten Module): Überspringt Aufzählungszeichen in einem bestimmten Modul.
* Seitenumbruch vor (anwendbar für untergeordnete Module des Zielbereichs): Fügt einen Seitenumbruch vor dem Modul ein.
* Seitenumbruch nach (anwendbar für untergeordnete Module des Zielbereichs): Fügt nach dem Modul einen Seitenumbruch ein.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Zielbereich an.
* Bearbeiten (nur Textmodule): Öffnet den Rich-Text-Editor, um das Textmodul zu bearbeiten.
* Datenbereich (Text- und Bedingungsmodule): Öffnet alle Variablen des Moduls.

**Listenmodul**

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Inhaltsbibliothek: Öffnet die Inhaltsbibliothek, um der Liste Module hinzuzufügen.
* Liste einrichten (nur verschachtelte Liste):
* Reihenfolge sperren (Info): Gibt an, dass die Reihenfolge der Listenelemente nicht geändert werden kann.

### Anlagen verwalten {#manage-attachments}

1. Wählen Sie **Anlagen**. Correspondence Management zeigt die verfügbaren Anhänge an, wie sie beim Erstellen der Briefvorlage eingerichtet wurden.
1. Sie können festlegen, dass keine Anlage zusammen mit dem Brief gesendet werden soll, indem Sie auf das Ansichtssymbol klicken und dann auf das Kreuz in der Anlage, um sie aus dem Brief zu löschen. Für Anlagen, die beim Erstellen der Briefvorlage als obligatorisch definiert wurden, sind die Symbole „Anzeigen“ und „Löschen“ deaktiviert.
1. Wählen Sie das Symbol „Bibliothekszugriff“ (![libraryaccess](assets/libraryaccess.png)) aus, um auf die Inhaltsbibliothek zuzugreifen und DAM-Assets als Anlagen einzufügen.

   >[!NOTE]
   >
   >Das Symbol „Bibliothekszugriff“ ist nur verfügbar, wenn der Bibliothekszugriff beim Verfassen des Briefes aktiviert wurde.

1. Wenn die Reihenfolge der Anlagen beim Erstellen der Korrespondenz nicht gesperrt war, können Sie die Reihenfolge der Anlagen neu anordnen, indem Sie eine Anlage auswählen und auf die Pfeile nach unten oder nach oben tippen.

   Weitere Informationen finden Sie unter [Anlagenübermittlung](#attachmentdelivery).

### Verwalten des Inhalts in der Vorschau und Absenden des Briefs {#manage-content-in-preview-and-submit-the-letter}

Sie können Änderungen an Layout und Inhalt des Briefs vornehmen, um sicherzustellen, dass der Brief Ihren Vorstellungen entspricht, und ihn dann an die verschiedenen nachfolgenden Prozesse übermitteln.

1. Um den gesamten bearbeitbaren Inhalt des Briefs zu markieren, wählen Sie **Bearbeitbare Bereiche markieren** aus.

   Die bearbeitbaren Inhalte des Briefs werden mit grauem Hintergrund markiert.

   ![Bearbeitbare Inhalte markieren](assets/4_highlightmoduleincontent-1.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ nach Bedarf die Inhaltsmodule. Um den Fokus auf das relevante Inhaltsmodul in der Inhaltshierarchie zu verschieben, können Sie entweder die betreffende Zeile oder den betreffenden Absatz in der Briefvorschau auswählen oder in der Inhaltshierarchie direkt das Inhaltsmodul auswählen.

   Beispielsweise ist in der folgenden Grafik die Zeile „Um uns Zugriff zu gewähren…“ ausgewählt, und das entsprechende Inhaltsmodul ist auf der Registerkarte „Inhalt“ ausgewählt.

   Durch Tippen auf „Ausgewählte Module im Inhalt hervorheben“ (![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) können Sie eine Funktion aktivieren oder deaktivieren, die bewirkt, dass beim Tippen auf den relevanten Text oder Absatz bzw. das Datenfeld in der Briefvorschau das dazugehörige Inhaltsmodul auf der Registerkarte „Inhalt“ markiert wird.

   Weitere Informationen zu Aktionen, die für verschiedene Module in der Benutzeroberfläche „Korrespondenz erstellen“ verfügbar sind, finden Sie unter [In der Benutzeroberfläche „Korrespondenz erstellen“ verfügbare Vorgehensweisen und Informationen](#actions-and-info-available-in-the-create-correspondence-content-tab).

1. Um dem Brief einen Seitenumbruch hinzuzufügen, wählen Sie die Stelle aus, an der Sie den Seitenumbruch einfügen möchten, und dann „Seitenumbruch vor“ oder „Seitenumbruch nach“ (![pagebreakbeforeafter](assets/pagebreakbeforeafter.png)).

   Es wird ein Platzhalter für einen expliziten Seitenumbruch in den Brief eingefügt. Sie können die Wirkung eines expliziten Seitenumbruchs anzeigen, indem Sie die reduzierte PDF-Vorschau aufrufen.

   >[!NOTE]
   >
   >Da Formulare auf Mobilgeräten Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Sie können jedoch explizit festlegen, dass Kopf- und Fußzeilen im Layout (pro Seite) in der Mobile Forms-Vorschau angezeigt werden. Auch leere Seiten im Brief (falls vorhanden) werden in der Mobile Forms-Vorschau nicht angezeigt.

   ![Expliziter Seitenumbruch](assets/8_pagebreak.png)

1. Um den Brief als Entwurf zu speichern, an dem Sie später weiter arbeiten können, wählen Sie „Als Entwurf speichern“ aus. Um diese Option verwenden zu können, muss Ihr Brief [veröffentlicht](../../forms/using/publishing-unpublishing-forms.md#publishanasset) sein. Weitere Informationen finden Sie unter „Entwurfsinstanz“ unter [Speichern von Entwürfen und Senden von Briefinstanzen](#savingdrafts).

   ![saveasdraft](assets/saveasdraft.png)

   Das Dialogfeld „Entwurfsbriefname“ wird mit der Briefinstanz-ID angezeigt. Sie können optional diese ID bearbeiten. Notieren Sie sich die Brief-ID und wählen Sie dann **Fertig** aus. Sie können diese ID später verwenden, um den [Briefentwurf neu zu laden](submit-letter-topostprocess.md#reloaddraft).

1. Um den Brief als reduzierte PDF-Datei mit Layout und Seitenumbrüchen exakt so in einer Vorschau anzuzeigen, wie er gesendet werden wird, wählen Sie „Vorschau“ (![preview](assets/preview.png)) aus.

   Der Brief wird als reduzierte PDF-Datei angezeigt. Die reduzierte PDF-Datei ist die genaue Darstellung des Briefs, wie er mit den richtigen Schriftarten, Umbrüchen und dem Layout des Briefs gesendet wird.

   >[!NOTE]
   >
   >Wenn Sie Mozilla Firefox und den Wiedergabetyp HTML verwenden, stellen Sie sicher, dass Sie das native Browser-Plug-in und nicht das Acrobat-Plug-in verwenden, um den Brief als reduzierte PDF-Datei in der Vorschau anzuzeigen. Um das native Browser-Plug-in auszuwählen, gehen Sie zu den Einstellungen von Mozilla Firefox und wählen Sie für den PDF-Inhaltstyp die Option „Vorschau in Firefox“.

1. Wenn die reduzierte PDF-Vorschau Ihren Vorstellungen entspricht, wählen Sie **Absenden** aus, um den Brief zu senden. Wenn den Brief ändern möchten, wählen Sie stattdessen **Vorschau beenden** aus, um zur Vorschau des Briefs in der Benutzeroberfläche „Korrespondenz erstellen“ zurückzukehren und dort die Änderungen vorzunehmen. Wenn Sie „Senden“ auswählen, wird die Instanz zum Senden von Briefen erstellt, falls die Konfiguration zum Verwalten von Briefinstanzen in der Veröffentlichungsinstanz aktiviert ist.

   Weitere Informationen finden Sie unter „Entwurfsinstanz“ unter „Speichern von Entwürfen und Senden von Briefinstanzen“.

   Sie können den Brief auch als Entwurf speichern, um ihn später zu ändern.

   Nachdem Sie die erforderlichen Änderungen vorgenommen haben, können Sie den Brief entweder über die HTML5-Vorschau senden oder erneut „Vorschau“ auswählen, um die reduzierte PDF-Ausgabe zu überprüfen.

   Weitere Informationen zu den Unterschieden zwischen HTML5-Formularen und PDF-Formularen finden Sie unter [Funktionsunterschiede zwischen HTML5-Formularen und PDF-Formularen](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md).

## Speichern von Entwürfen und Senden von Briefinstanzen {#savingdrafts}

Wenn ein Brief in der Benutzeroberfläche „Korrespondenz erstellen“ gerendert wird, können Sie den Brief so speichern, wie er angezeigt wird.

Es gibt zwei Arten von Briefinstanzen, die gespeichert werden können: Entwurfsinstanz und Sendeinstanz.

* **Entwurfsinstanz**: Die Entwurfsinstanz erfasst den aktuellen Status des Briefs, den Sie in der Vorschau anzeigen. Um eine Entwurfsinstanz zu speichern, stellen Sie zunächst sicher, dass der Brief und alle Assets, auf die der Brief verweist, den Status „Veröffentlicht“ aufweisen. Weitere Informationen zum Veröffentlichen eines Briefs finden Sie unter[ Veröffentlichen von Assets](../../forms/using/publishing-unpublishing-forms.md#publishanasset). Sie müssen einen Brief veröffentlichen, bevor Sie ihn als Entwurf speichern können, denn wenn Sie einen Brief veröffentlichen, erstellen Sie zu diesem Zeitpunkt eine Version des Briefes, seiner abhängigen Assets und seiner Daten. Die veröffentlichte Version eines Briefs kann nicht von Ihnen oder einer anderen Person bearbeitet werden und kann ohne unerwartete Abweichungen von der veröffentlichten Version zu einem späteren Zeitpunkt wiederhergestellt werden. Sie können zu einem späteren Zeitpunkt zu dieser Instanz zurückkehren und dort fortfahren, wo Sie sie verlassen haben.

* **Übermittlungsinstanz**: Übermittlungsinstanzen erfassen den Status des Briefs zum Sendezeitpunkt. Die Sendeinstanz speichert den PDF-Status der Briefinstanz, nachdem sie zusammen mit den vom Benutzer in der Benutzeroberfläche „Korrespondenz erstellen“ eingegebenen Daten nachbearbeitet wurde.

Solche Instanzen können nur gespeichert werden, wenn der Brief in der Publish-Instanz angezeigt wird. Standardmäßig ist das Speichern von Instanzen deaktiviert. Um das Speichern von Briefinstanzen zu aktivieren, führen Sie die folgenden Schritte aus.

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console-Konfiguration für Ihren Server mit der folgenden URL: https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr
1. Suchen Sie nach **[!UICONTROL Correspondence Management-Konfigurationen]** und klicken Sie darauf.
1. Überprüfen Sie die Konfiguration **[!UICONTROL Briefinstanzen im Veröffentlichungsmodus verwalten]** und klicken Sie dann auf **[!UICONTROL Speichern]**.

### Aktivieren der Funktion „Speichern von Entwürfen“ {#enable-save-draft-feature}

Bevor Sie Briefe veröffentlichen oder Entwürfe in der Veröffentlichungsinstanz speichern, führen Sie die folgenden Schritte in der Autoren- und Veröffentlichungsinstanz durch, um die Funktion „Als Entwurf speichern“ zu aktivieren:

Die Eigenschaften *cq:lastReplicationAction*, *cq:lastreplicated* und *cq:lastReplicatedBy* werden standardmäßig nicht in die Veröffentlichungsinstanz übernommen. Um die Eigenschaften *cq:lastReplicationAction*, *cq:lastreplicated* und *cq:lastReplicatedBy* in die Veröffentlichungsinstanz zu übernehmen, deaktivieren Sie die Komponente [!UICONTROL com.day.cq.replication.impl.ReplicationPropertiesFilterFactory]. So deaktivieren Sie die Komponente:

1. Öffnen Sie in der Autoreninstanz die Konsole „Adobe Experience Manager Web Console Components“. Die Standardeinstellung ist `http://author-server:port/system/console/components`

1. Suchen Sie nach der Komponente **[!UICONTROL com.day.cq.replication.impl.ReplicationPropertiesFilterFactory]**.

1. Klicken Sie auf das Symbol ![Schaltfläche deaktivieren](/help/forms/using/assets/enablebutton.png), um die Komponente [!UICONTROL com.day.cq.replication.impl.ReplicationPropertiesFilterFactory] zu deaktivieren.

![Autoreninstanz](/help/forms/using/assets/replicationproperties.png)

Um die Funktion „Als Entwurf speichern“ zu aktivieren, ersetzen Sie die vorhandene URL unter [!UICONTROL VersionRestoreManager Author URL] durch die URL Ihrer Authoreninstanz. So ersetzen Sie die URL:

1. Öffnen Sie auf der Veröffentlichungsinstanz die [!UICONTROL Adobe Experience Manager Web Console-Konfiguration]. Die Standard-URL ist `https://publish-server:port/system/console/configMgr`

1. Suchen und öffnen Sie die Komponente **[!UICONTROL Correspondence Management – Autoreninstanz Version Konfigurationen wiederherstellen]**.

1. Suchen Sie das Feld **[!UICONTROL VersionRestoreManager Autor URL]** und geben Sie die URL für die Autoreninstanz an.

1. Klicken Sie auf „Speichern“.

![Veröffentlichungsinstanz](/help/forms/using/assets/correspondencemanagement.png)

Wenn das Speichern von Briefinstanzen aktiviert ist, können Sie auswählen, wo die Briefinstanzen gespeichert werden sollen. Es gibt zwei Optionen zum Speichern der Briefinstanzen: „Lokal speichern“ und „Remote speichern“.

### Lokal speichern {#local-save}

Briefinstanzen werden in der Veröffentlichungsinstanz gespeichert und in der Autorinstanz rückwärtsrepliziert.

### Remote speichern {#remote-save}

Diese Option ist für Personen vorgesehen, die bezüglich des Speicherns von Daten in Veröffentlichungsinstanzen haben, die sich normalerweise außerhalb der Firewall des Unternehmens befinden. Wenn das Remote-Speichern aktiviert ist, werden die Briefinstanzen nicht in der Publishing-Instanz gespeichert, sondern remote in der verarbeitenden Authoring-Instanz gespeichert, die über die LiveCycle Client SDK-Konfigurationen angegeben wurde.

#### Aktivieren des Remote-Speicherns {#enable-remote-save}

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console-Konfiguration für Ihren Server mit der folgenden URL: `https://<server>:<port>/<contextpath>/system/console/configMgr`
1. Suchen Sie nach **[!UICONTROL Correspondence Management-Konfigurationen]** und klicken Sie darauf.
1. Suchen Sie die Konfiguration **[!UICONTROL Remote Speichern]**, überprüfen Sie sie und klicken Sie auf **[!UICONTROL Speichern]**.

#### Angeben der Einstellungen für Prozessautor {#specify-processing-author-settings}

1. Öffnen Sie in AEM die Adobe Experience Manager Web Console-Konfiguration für Ihren Server mit der folgenden URL: `https://<server>:<port>/system/console/configMgr`

   ![Konfiguration der Adobe Experience Manager-Web-Konsole](assets/2configmanager.png)

1. Suchen Sie auf dieser Seite Adobe LiveCycle Client SDK-Konfiguration und erweitern Sie sie durch Klicken auf.

1. Geben Sie in im Feld für die Verarbeitung der Server-URL den Namen Ihres LiveCycle-Servers sowie die Anmeldeinformationen ein und klicken Sie dann auf **Speichern**.

   ![Namen und Anmeldeinformationen Ihres LiveCycle-Servers eingeben](assets/3configmanager.png)

1. Legen Sie bei Bedarf den Benutzernamen und das Kennwort fest, mit dem Sie auf den Server zugreifen möchten.

#### Anlagenübermittlung {#attachmentdelivery}

* Die Briefanlagen sind verfügbare Nachbearbeitungen in der PDF-Datei, die nach der Briefsendung erstellt wird.
* Wenn der Brief mit Server-seitigen APIs als interaktive oder nicht interaktive PDF gerendert wird, enthält die gerenderte PDF-Datei Anlagen im PDF-Format.
* Wenn ein mit einer Briefvorlage verknüpfter Nachbearbeitungsprozess im Rahmen der Vorgänge „Senden“ oder „Korrespondenz abschließen“ mithilfe der Benutzeroberfläche „Korrespondenz erstellen“ geladen wird, werden Anlagen als die Liste &lt;com.adobe.idp.Document> im Parameter AttachmentDocs übergeben.
* Vordefinierte Versandmechanismen wie E-Mail und Drucken senden Anlagen zusammen mit der PDF der generierten Korrespondenz.

## Darstellungsmodi der Briefvorschau: Vorschau für Mobile Forms und PDF {#rendition-modes-of-letter-preview-mobile-forms-preview-and-pdf-preview}

AEM Forms Correspondence Management zeigt Briefe in der Benutzeroberfläche „Korrespondenz erstellen“ im HTML-Format an. Correspondence Management unterstützt jedoch weiterhin die Wiederherstellung der PDF-Vorschau anstelle der HTML-Vorschau. Weitere Informationen zum Wechseln zwischen HTML- und PDF-Modus für die Vorschau finden Sie unter [Ändern des Darstellungsmodus des Briefs](#changerenditionmode).

Die folgenden Vorteile und Funktionen stehen jeweils bei der HTML- und PDF-Vorschau zur Verfügung.

**Vorteile der Mobile Forms- bzw. HTML-Vorschau**

* **Markieren des zugehörigen Datenfelds durch Auswählen eines Datenfeldwertes**: Auf der Benutzeroberfläche „Korrespondenz erstellen“ können Sie auf einen Datenfeldwert im Brief tippen, um das entsprechende Datenfeld auf der Registerkarte „Daten“ zu markieren. Weitere Informationen finden Sie unter [Daten eingeben](#enterdata).

* **Browser-Unterstützung**: In Browsern wird NPAPI immer weniger unterstützt, was sich auf die PDF-Vorschau von Briefen auswirkt. Die Vorschau von Briefen in HTML bzw. Mobile Forms ist davon nicht betroffen.
* **Markieren bearbeitbarer Inhalte in einem Brief**: Auf der Benutzeroberfläche „Korrespondenz erstellen“ können Sie „Bearbeitbare Inhalte markieren“ auswählen, um den gesamten bearbeitbaren Inhalt des Briefes grau zu markieren. Weitere Informationen finden Sie unter [Verwalten von Inhalten](#managecontent).

`<li>` `<li>Benefits of HTML preview  <ul>   <li>Right to left</li>   <li>NPAPI</li>   <li>Highlight Editable Content</li>  </ul> </li>` `<li>Benefits of PDF preview  <ul>   <li>Page Break</li>   <li>Final Preview</li>  </ul> </li>`
`<li>` `<li>Benefits of HTML preview  <ul>   <li>Right to left</li>   <li>NPAPI</li>   <li>Highlight Editable Content</li>  </ul> </li>` `<li>Benefits of PDF preview  <ul>   <li>Page Break</li>   <li>Final Preview</li>  </ul> </li>`  **Vorteile der PDF-Vorschau**

* **Seitenumbruch**: In der PDF-Vorschau eine Vorschau können Sie genau erkennen, wie die Seitenumbrüche im Brief sich auf dessen Ausgabe auswirken.
* **Abschließende Vorschau**: In der PDF-Vorschau können die genaue Formatierung und das Erscheinungsbild des Briefs für die Ausgabe angezeigt werden.

Weitere Informationen zur Skriptunterstützung in PDF-Formularen finden Sie unter [Skriptunterstützung](https://help.adobe.com/de_DE/livecycle/11.0/ScriptingSupport/index.html).

Weitere Informationen zur Skriptunterstützung in HTML5-Formularen finden Sie unter [Skriptunterstützung für HTML5-Formulare](/help/forms/using/scripting-support.md).

### Ändern des Ausgabedarstellungsmodus des Briefs {#changerenditionmode}

Standardmäßig verwendet die Benutzeroberfläche „Korrespondenz erstellen“ HTML oder Mobile Forms, um die Briefvorschau zu rendern. Die Mobile Forms-Vorschau kann in beliebigen Browsern problemlos gerendert werden, da sie das native Plugin des Browsers verwendet und daher keine zusätzlichen Plugins benötigt werden. Sie können zum Briefvorschaumodus PDF wechseln. Allerdings können aufgrund von Browserbeschränkungen Probleme bei verschiedenen Funktionen der interaktiven PDF-Vorschau des Briefs auftreten.

Weitere Informationen zur Browserkompatibilität bei der Briefvorschau finden Sie unter [Auslauf der Unterstützung für das NPAPI-Browser-Plugin und Auswirkungen](https://helpx.adobe.com/de/acrobat/kb/change-in-support-for-acrobat-and-reader-plug-ins-in-modern-web-.html).

Um den Vorschaumodus des Briefs zu ändern, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu `https://[system]:'port'/system/console/configMgr` und melden Sie sich nötigenfalls als Administrator an.
1. Navigieren Sie zu **[!UICONTROL Correspondence Management-Konfigurationen]** > **[!UICONTROL Wiedergabe-Typ]** und wählen Sie **HTML-Wiedergabe** (Standard) oder **PDF-Wiedergabe**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
