---
title: Dokumentfragmente in AEM
description: Dokumentfragmente wie Text, Listen, Bedingungen und Layout-Fragmente ermöglichen es Ihnen in Correspondence Management, die statischen, dynamischen und wiederholbaren Komponenten der Kundenkorrespondenz zu bilden.
uuid: 4273323d-14f5-4b3b-8fed-80beef641efe
topic-tags: correspondence-management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0d5436c6-1976-496c-b9a7-7dc6e830bb5d
docset: aem65
feature: Correspondence Management
exl-id: 71754e41-45d7-4cc5-ba49-0748bd51c0cf
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '6904'
ht-degree: 97%

---

# Dokumentfragmente{#document-fragments}

## Dokumentfragmente {#document-fragments-1}

Dokumentfragmente sind wiederverwendbare Teile/Komponenten einer Korrespondenz, mit der Sie Briefe/Korrespondenz erstellen können. Es gibt Dokumentfragmente der folgenden Typen:

* **Text**: Ein Textelement ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein.
* **Liste**: Eine Liste ist eine Gruppe von Dokumentfragmenten, einschließlich Text, Listen, Bedingungen und Bildern. Die Reihenfolge der Listenelemente kann festgelegt sein oder bearbeitet werden. Beim Erstellen eines Briefs können Sie einige oder alle Listenelemente verwenden, um ein wiederverwendbares Muster von Elementen zu replizieren.
* **Bedingung**: Bedingungen ermöglichen es Ihnen zu definieren, welche Inhalte zur Erstellungszeit der Korrespondenz je nach den angegebenen Daten einbezogen werden sollen. Die Bedingung wird in Form von Steuerungsvariablen beschrieben. Eine Steuerungsvariable kann entweder ein Datenwörterbuchelement oder ein Platzhalter sein.
* **Layout-Fragment**: Unter einem Layout-Fragment versteht man ein Layout, das mit einem oder mehreren Briefen verwendet werden kann. Ein Layout-Fragment wird verwendet, um wiederholbare Muster, insbesondere dynamische Tabellen, zu erstellen. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenznummer“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche kennzeichnen. Die Layouts (XDP-Dateien) werden in Designer erstellt und können dann in AEM Forms hochgeladen werden.

## Text {#text}

Ein Textelement ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein. Ein dynamischer Absatz enthält Verweise auf Datenelemente, deren Werte zur Laufzeit bereitgestellt werden. So könnte beispielsweise der Kundenname in einer Grußformel ein dynamisches Datenelement sein, dessen Wert zur Laufzeit bereitgestellt wird. Durch Änderung dieser Werte kann dieselbe Briefvorlage verwendet werden, um Briefe für verschiedene Kundinnen oder Kunden zu generieren.

Die Lösung „Correspondence Management“ unterstützt zwei Arten von dynamischen Datenelementen (Variablendaten):

* **Elemente eines Datenwörterbuchs**: Diese Elemente sind an das Datenwörterbuch gebunden und erhalten ihre Werte aus der bereitgestellten Datenquelle. Eine Datenwörterbuchvariable kann geschützt oder ungeschützt sein. Bei der Korrespondenzerstellung kann für ungeschützte Datenwörterbuchvariablen der Standardwert geändert werden, nicht jedoch für geschützte Variablen.
* **Platzhalter**: Hierbei handelt es sich um Variablen, die nicht an eine Back-End-Datenquelle gebunden sind. Die Benutzerin bzw. der Benutzer muss bei der Korrespondenzerstellung einen Wert eingeben. Die Platzhalter sind standardmäßig ungeschützt.

>[!NOTE]
>
>Die Correspondence Management-Vorlagen zwingen Sie nicht, beim Erstellen von Platzhaltern eindeutige Namen zu erstellen. Wenn Sie zwei Platzhalter mit demselben Namen, wie etwa einen Text und eine Bedingung, erstellen und beide in einer Briefvorlage verwenden, werden die Werte des zuletzt eingefügten Platzhalters für beide Platzhalter verwendet. Wenn zwei Platzhalter denselben Namen haben, werden ihre Typen verglichen. Wenn die Typen unterschiedlich sind, wird deren Typ auf „String“ festgelegt. Innerhalb eines Moduls können Sie jedoch nicht mehrere Platzhalter mit demselben Namen erstellen.

### Text erstellen {#create-text}

1. Wählen Sie **Formulare** > **Dokumentfragmente**.
1. Tippen Sie auf **Erstellen** > **Text**, oder wählen Sie ein Textelement und tippen Sie auf **Bearbeiten**.
1. Geben Sie folgende Informationen für den Text an:

   * **Titel: (Optional)**: Geben Sie den Titel für das Textelement ein. Titel müssen nicht eindeutig sein und können Sonderzeichen und nichtenglische Zeichen enthalten. Texte werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Asset-Eigenschaften referenziert.
   * **Name**: Der eindeutige Name für das Textelement. Es können nicht zwei Assets (Text, Bedingung oder Liste) in beliebigen Status mit demselben Namen vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **Beschreibung**: Geben Sie eine Beschreibung des Assets ein.
   * **Datenwörterbuch**: Wählen Sie optional das Datenwörterbuch aus, dem das Element zugeordnet werden soll. Mit diesem Attribut können Sie Verweise auf Datenwörterbuchelemente im Text-Asset hinzufügen.
   * **Tags**: Um optional einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Sie können den Tag unterhalb des Textfeldes der Tags sehen. Wenn Sie diesen Text speichern, werden auch die neu hinzugefügten Tags erstellt.

1. Tippen Sie auf **Weiter**. Correspondence Management zeigt die Editor-Seite an, auf der Sie Textabsätze und Datenelemente zu dem Text hinzufügen können.

   Die Standard-Rechtschreibprüfung in Ihrem Browser überprüft die Rechtschreibung im Texteditor. Um die Rechtschreib- und Grammatikprüfung zu verwalten, können Sie die Rechtschreibprüfungseinstellungen Ihres Browsers bearbeiten oder Plug-ins bzw. Add-ons für den Browser installieren, um Rechtschreibung und Grammatik zu überprüfen.

   Sie können die verschiedenen Tastaturbefehle im Texteditor verwenden, um Text zu verwalten, zu bearbeiten und zu formatieren. Weitere Informationen zu Tastaturbefehlen des [Texteditors](/help/forms/using/keyboard-shortcuts.md#p-formatting-p) finden Sie unter „Correspondence Management-Tastaturbefehle“.

1. Ein Texteditor wird geöffnet. Geben Sie hier den gewünschten Text ein. Verwenden Sie die Symbolleiste oben auf der Seite, um den Text zu formatieren, Bedingungen, Links und Seitenumbrüche einzufügen.

   ![Symbolleiste](assets/advancedediting.png)

   * **Link**: Fügen Sie eine [Hypertextverknüpfung](#insert-hyperlink) in den Text ein.
   * **Wiederholen**: Mit diesem Befehl wird ein Collection-Element unter Verwendung eines Trennzeichens in ein Datenwörterbuch gedruckt.
   * **Bedingung**: Antippen, um eine Bedingung einzufügen. Text wird auf der Grundlage einer Bedingung eingefügt. Wenn die Bedingung erfüllt ist, ist der Text im Brief sichtbar, andernfalls nicht.
   * **Beschreibung hinzufügen**: Hinzufügen einer Anmerkung zu einem Textabschnitt. Es handelt sich hierbei um Metadaten, die nur für den Autor sichtbar und nicht Teil des erstellten Briefs sind.
   * **Seitenumbruch**: Wenn Sie das Seitenumbruch-Attribut eines Textmoduls auf „false“ setzen, wird das Textmodul nicht auf mehreren Seiten angezeigt.

   Ein Texteditor wird geöffnet. Geben Sie den Text ein. Die Symbolleiste ändert sich je nach dem Typ der Bearbeitung, die Sie vornehmen: Absatz, Ausrichtung oder Auflistung:

   ![Symbolleistentyp auswählen](assets/toolbarselection.png)

   Wählen Sie den Typ der Symbolleiste aus: Absatz, Ausrichtung oder Auflistung

   ![Absatz-Symbolleiste](assets/fonteditingtoolbar.png)

   Absatz-Symbolleiste
   [![Ausrichtungs-Symbolleiste](assets/paragrapheditingtoolbar.png)](assets/paragrapheditingtoolbar-1.png)Ausrichtungs-Symbolleiste

   ![Auflistungs-Symbolleiste](assets/bulleteditingtoolbar.png)

   Auflistungs-Symbolleiste (Klicken Sie hier, um Bild in voller Größe zu öffnen)

1. Um einen oder mehrere Textabsätze wiederzuverwenden, die in einer anderen Anwendung vorhanden sind, z. B. von Microsoft Word- oder HTML-Seiten, kopieren Sie den Text und fügen Sie ihn in den Text-Editor ein. Die Formatierung des kopierten Texts wird im Texteditor beibehalten.

   Sie können einen oder mehrere Textabsätze in ein bearbeitbares Textmodul kopieren und einfügen. Sie könnten beispielsweise ein MS Word-Dokument mit einer Liste mit Aufzählungszeichen für zulässige Aufenthaltsnachweise wie das folgende haben:

   ![pastetextmsword-1](assets/pastetextmsword-1.png)

   Sie können den Text direkt aus dem MS Word-Dokument in ein bearbeitbares Textmodul kopieren. Die Formatierung (wie Liste mit Aufzählungszeichen, Schriftart und Textfarbe) wird im Textmodul beibehalten.

   ![pastetexttextmodule](assets/pastetexttextmodule.png)

   >[!NOTE]
   >
   >Die Formatierung des eingefügten Textes hat jedoch einige[ Einschränkungen](https://helpx.adobe.com/de/aem-forms/kb/cm-copy-paste-text-limitations.html).

1. Fügen Sie bei Bedarf Sonderzeichen in das Dokumentfragment ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

   * Währungssymbole wie €,￥ und £
   * Mathematische Symbole wie ∑, √, ∂ und ^
   * Satzzeichen wie „ und “

   ![specialcharacters-1](assets/specialcharacters-1.png)

   Correspondence Management enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](/help/forms/using/custom-special-characters.md).

1. Um Teile eines Textes in einem bearbeitbaren Inline-Modul hervorzuheben, wählen Sie den Text aus und tippen Sie auf „Hervorhebungsfarbe“.

   ![textbackgroundcolorapplied](assets/textbackgroundcolorapplied.png)

   Sie können entweder direkt auf eine Grundfarbe `**[A]**` in der Grundfarbenpalette tippen oder auf **Auswählen** tippen, nachdem Sie mit dem Schieberegler `**[B]**` die gewünschte Farbschattierung gewählt haben.

   Optional können Sie auch auf der Registerkarte „Erweitert“ die gewünschten Werte für Farbton, Helligkeit und Sättigung `**[C]**` wählen, um die Farbe präzise festzulegen, und dann auf „Auswählen“ `**[D]**` tippen, um die Farbe zum Hervorheben des Textes anzuwenden.

   ![textbackgroundcolor-1](assets/textbackgroundcolor-1.png)

1. Ziehen Sie aus dem Daten-Panel Datenwörterbuchelemente und Platzhalterelemente per Drag-and-Drop in den Text.

   An:

   * Um ein Datenwörterbuchelement im Text einzufügen, wählen Sie ein Datenelement in der Liste aus und klicken Sie auf „Einfügen“ (![insert](assets/insert.png)). Wenn Sie Geschützt auswählen, ist das Datenlexikonelement schreibgeschützt und wird im Briefeditor, aber nicht in der Benutzeroberfläche „Korrespondenz erstellen“ oder in der Korrespondenzerstellung angezeigt.
   * Um ein Platzhalterelement im Text einzufügen, klicken Sie im Bereich „Datenelemente“ auf „Neu erstellen“. geben Sie die Details des neuen Datenelements ein und klicken Sie auf „Erstellen“, um das neue Element der Liste hinzuzufügen. Der neue Platzhalter kann auf dieselbe Weise in den Text eingefügt werden wie das Datenwörterbuchelement. Um einen Platzhalter zu bearbeiten, wählen Sie einen Platzhalter aus und tippen Sie auf „Bearbeiten“.

   ![Platzhalterelemente](assets/placeholder_elements_in_xmldata.png)

   Platzhalterelemente, wie in der von Ihnen erstellten Musterdatendatei eines Datenwörterbuchs angegeben

   ![Platzhalterelemente im Brief](assets/placeholder_elements_in_text.png)

   Platzhalterelementwerte in der CCR-Ansicht wurden von den Datenwörterbuchvariablen aufgefüllt, wie in der von Ihnen erstellten Musterdatendatei angegeben

   Sie können auch das @-Symbol verwenden, um Datenwörterbuch- und Platzhalterelemente zu suchen und zum Texteditor hinzuzufügen. Platzieren Sie den Cursor an die Stelle, an der das Element eingefügt werden soll. Geben Sie @ ein, gefolgt von der Suchzeichenfolge. Der Texteditor führt den Suchvorgang für alle Datenwörterbuch- und Platzhalterelemente durch, die im Textdokumentfragment verfügbar sind. Der Suchvorgang ruft die Elemente ab, die die Suchzeichenfolge enthalten, und zeigt sie als Dropdown-Liste an. Navigieren Sie durch die Suchergebnisse und klicken Sie auf das Element, das Sie an der Position des Mauszeigers einfügen möchten. Drücken Sie Esc, um die Suchergebnisse auszublenden.

1. Sie können Inline-Bedingungen verwenden und wiederholen, um den Brief sehr kontextabhängig und gut strukturiert zu machen. Weitere Informationen zu Inline-Bedingungen erhalte Sie unter [Inline-Bedingungen und Wiederholung in Briefen](/help/forms/using/cm-inline-condition.md).
1. Tippen Sie auf **Speichern**.

#### Einfügen eines Hyperlinks in einen Text {#insert-hyperlink}

Führen Sie die folgenden Schritte aus, um einen Hyperlink in einem Textelement zu erstellen:

1. Wählen Sie den Text oder das Datenmodellobjekt im Texteditor aus.

2. Tippen Sie auf **[!UICONTROL Link]**. Tippen Sie auf das Feld **[!UICONTROL Alt-Text]**, um den vorhandenen Datenmodellobjektnamen oder -text zu entfernen.

3. Geben Sie die URL an und tippen Sie auf ![Speichern](assets/save_icon.svg).

![Erstellen eines Hyperlinks in einem Textelement](assets/text-create-hyperlink.png)

#### Text suchen und ersetzen {#searching-and-replacing-text}

Bei der Arbeit mit Textelementen, die einen großen Textkörper enthalten, müssen Sie nach einer bestimmten Textzeichenfolge suchen. Möglicherweise müssen Sie auch eine bestimmte Textfolge durch eine alternative Zeichenfolge ersetzen.

Mit der Funktion &quot;Suchen und Ersetzen&quot;können Sie nach einer beliebigen Zeichenfolge in einem Textelement suchen (und diese ersetzen). Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken.

#### Suchen nach Text in einem Textmodul {#to-search-text-in-a-text-module}

1. Öffnen Sie das Textmodul im Texteditor.

1. Tippen Sie auf „Suchen und Ersetzen“.
1. Geben Sie den zu suchenden Text in das Textfeld „Suchen“ ein und klicken Sie auf „Suchen“. Der gesuchte Text wird im Textmodul hervorgehoben.
1. Um nach der nächsten Instanz des Texts zu suchen, klicken Sie erneut auf „Suchen“.

   Wenn Sie weiter auf die Schaltfläche „Suchen“ klicken, wird die Suche nach unten fortgesetzt. Nachdem die letzte Instanz des Textes gefunden wurde, gibt die Meldung **Ende des Moduls erreicht** an, dass keine weiteren Suchergebnisse gefunden wurden.

   Wenn allerdings keine Instanz des gesuchten Texts im Textmodul gefunden wird, lautet die angezeigte Meldung: **Übereinstimmung nicht gefunden**.

1. Wenn Sie erneut auf „Suchen“ klicken, wird die Suche am Anfang der Seite fortgesetzt.

#### Suchoptionen {#search-options}

**Groß-/Kleinschreibung berücksichtigen**: Die Suche gibt nur Ergebnisse mit derselben Groß- bzw. Kleinschreibung zurück.

**Ganzes Wort:** Die Suche gibt nur ganze Wörter zurück.

>[!NOTE]
>
>Wenn Sie Sonderzeichen in das Textfeld „Suchen“ eingeben, wird die Option „Ganzes Wort“ deaktiviert.

**Reguläre Ausdrücke:** Suche mithilfe regulärer Ausdrücke. Beispielsweise kann mithilfe des folgenden regulären Ausdrucks nach E-Mail-Adressen in einem Textelement gesucht werden:

`[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}`

#### Suchen und Ersetzen von Text in einem Textmodul {#to-search-and-replace-text-in-a-text-module}

1. Öffnen Sie das Textmodul im Texteditor.
1. Tippen Sie auf „Suchen und Ersetzen“.
1. Geben Sie den zu suchenden Text in das Textfeld „Suchen“ ein, geben Sie den Text ein, der den gefundenen Text ersetzen soll, und drücken Sie auf „Ersetzen“.
1. Wenn der Suchtext gefunden wird, wird er durch den Ersetzungstext ersetzt.

   * Wenn eine andere Instanz des Suchtextes gefunden wird, wird diese Instanz im Textmodul hervorgehoben. Wenn Sie erneut auf „Ersetzen“ klicken, wird die hervorgehobene Instanz ersetzt und der Cursor bewegt sich weiter, falls eine dritte Instanz gefunden wird.
   * Wenn keine andere Instanz gefunden wird, hält der Cursor an der zuletzt ersetzten Instanz an.

1. Wenn Sie erneut auf „Suchen“ klicken, wird die Suche am Anfang der Seite fortgesetzt.

   Verwenden Sie die Option „Alle ersetzen“, um alle Instanzen des Texts im Textmodul zu ersetzen. Wenn Sie `` verwenden, wird die Anzahl der Ersetzungen als Meldung im Dialogfeld „Suchen und Ersetzen“ angezeigt.

#### Best Practices/Tipps und Tricks für Textmodule {#best-practices-tips-and-tricks-for-text-modules}

* Verwenden Sie eine konsistente Benennungskonvention, um Duplizierungen zu vermeiden.
* Verwenden Sie die entsprechende Datenwörterbuchbindung in Textmodulen.
* Die folgenden Regeln gelten für die Verwendung des Texteditors beim Ändern eines Text-Assets:

   * **Variablen hinzufügen:** Zulässig
   * **Variablen entfernen:** Zulässig
   * **Eigenschaften aktualisieren:** Zulässig
   * **Datenwörterbuch ändern:** Zulässig, solange das Datenwörterbuchelement nicht verwendet wird. Das Datenwörterbuch kann bei einer Aktualisierung nicht geändert werden.

## Liste {#list}

Eine Liste ist eine Gruppe von Dokumentfragmenten, einschließlich Text, (anderen) Listen, Bedingungen und Bildern. Die Reihenfolge der Listenelemente kann festgelegt sein oder bearbeitet werden. Beim Erstellen eines Briefs können Sie einige oder alle Listenelemente verwenden, um ein wiederverwendbares Muster von Elementen zu replizieren. Listen verhalten sich generell wie Ziele, die in anderen Ziele verschachtelt werden können.

### Implementieren von Listen {#implementing-lists}

Die Implementierung von Listen erfolgt in zwei Schritten:

1. Definieren von Kerneigenschaften wie Name, Beschreibung und Datenwörterbuch.
1. Auswählen des Inhalts, der Teil der Liste ist, und dann Festlegen der Eigenschaften wie Sperren der Reihenfolge und Bibliothekszugriff für die Liste.

### Erstellen einer Liste {#create-a-list}

Eine Liste ist eine Gruppe von zusammenhängenden Inhalten, die in einer Briefvorlage als eine Einheit verwendet werden können. Zu einer Liste kann jede Art von Inhalt hinzugefügt werden. Listen können auch verschachtelt sein. Listenmodule können wie folgt angegeben werden:

* **GEORDNET**: Die Reihenfolge kann zum Zeitpunkt der Korrespondenzerstellung nicht geändert werden.
* **Bibliothekszugriff**: Benutzer können der Liste Module hinzufügen. Dieses Flag gibt an, ob der Bibliothekszugriff aktiviert ist. Ist dieser aktiviert (geöffnet), können Module zur Liste hinzugefügt werden, während der Brief in der Vorschau angezeigt wird.
* Beim Erstellen einer Liste können Sie einen Typ angeben, z. B.:
* **Einfach**: Auf die Liste wird keine weitere Stilformatierung angewendet.
* **Aufzählungszeichen**: Eine mit einem einfachen Aufzählungszeichen formatierte Liste.
* **Nummeriert**: Eine numerische Liste mit den Zahlenformaten Standard (1,2,…), römische Großbuchstaben (I, II, …) oder römische Kleinbuchstaben (i, ii,…).
* **Mit Buchstaben**: Eine alphabetische Liste mit der Buchstabenformatierung als Kleinbuchstaben (a, b, …) oder Großbuchstaben (A, B, …).
* **Benutzerdefiniert**: Sie können beliebige Zahlen-/Buchstabentypen sowie Präfix- und Suffixwerte Ihrer Wahl erstellen.

1. Wählen Sie **Formulare** > **Dokumentfragmente**.

1. Wählen Sie **Erstellen** > **Liste**.

1. Geben Sie folgende Informationen für die Liste an:

   * **Titel (Optional):** Geben Sie den Titel für die Liste ein. Der Titel muss nicht eindeutig sein und kann Sonderzeichen und nichtenglische Zeichen enthalten. Listen werden durch ihre Titel (falls verfügbar) referenziert, wie beispielsweise in Miniaturansichten und Asset-Eigenschaften.
   * **Name:** Der eindeutige Name der Liste. Es können nicht zwei Assets (Text, Bedingung oder Liste) in beliebigen Status mit demselben Namen vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch mit dem Wert im Feld „Titel“ ausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **Beschreibung (Optional)**: Geben Sie eine Beschreibung des Assets ein.
   * **Datenelement (Optional)**: Wählen Sie optional das Datenelement aus, mit dem das Element verknüpft werden soll. Es können nur Elemente der Liste hinzugefügt werden, die das gleiche Datenwörterbuch verwenden wie die Liste oder denen kein Datenwörterbuch zugewiesen ist. Das Zuweisen eines Datenwörterbuchs zu einer Liste erleichtert es der Erstellerin bzw. dem Ersteller einer Briefvorlage, die entsprechende Liste zu finden.
   * **Tags (Optional)**: Wählen Sie die Tags aus, die angewendet werden sollen. Sie können auch den Namen eines neuen Tags eingeben und es erstellen. (Das neue Tag wird erstellt, wenn Sie auf **Speichern** tippen.)

1. Tippen Sie auf **Weiter**.
1. Tippen Sie auf **Asset hinzufügen**.
1. Um der Liste Assets hinzufügen, wählen Sie sie auf der Seite „Assets auswählen“ aus und tippen Sie auf **Fertig**.

   ![Assets zum Hinzufügen zur Liste auswählen](assets/selectassets.png)

1. Die Assets werden der Seite „Listenelemente“ hinzugefügt.
Um die Reihenfolge der Assets innerhalb der Liste zu ändern, tippen Sie auf das Pfeilsymbol (![dragndrop](assets/dragndrop.png)), halten Sie die Taste gedrückt und verwenden Sie die Drag-and-Drop-Funktion. Wenn der Benutzer auf der Benutzeroberfläche „Korrespondenz erstellen“ eine Briefvorlage öffnet, wird der Inhalt in der hier festgelegten Reihenfolge zusammengestellt.

   ![Assets in einer Liste neu anordnen und konfigurieren](assets/listitems.png)

1. Sie können die folgenden Optionen auswählen, um festzulegen, wie sich die Liste in der CCR-Benutzeroberfläche verhält:

   * **Bibliothekszugriff**: Um den Bibliothekszugriff für das Hinzufügen von Assets zu aktivieren, tippen Sie auf „Bibliothekszugriff“. Wenn der Bibliothekszugriff aktiviert ist, kann der Schadensregulierer der Liste weitere Inhalte hinzufügen. Andernfalls ist der Schadensregulierer auf den Inhalt beschränkt, den Sie für die Liste definiert haben.
   * **Reihenfolgesperren**: Zum Sperren der Reihenfolge der Assets in der Liste, sodass der Schadensregulierer sie nicht ändern kann, tippen Sie auf „Reihenfolge sperren“. Wenn Sie diese Option nicht aktivieren, kann der Schadensregulierer die Reihenfolge der Listenelemente ändern.

   * **Aufzählungszeichen hinzufügen**: Verwenden Sie diese Option, um dem Modul einen Aufzählungs- oder Nummerierungsstil hinzuzufügen. Sie können entweder einen vorgefertigten oder einen benutzerdefinierten Listenstil verwenden. Sie können auch den vor und nach jedem der Listenelemente anzuzeigenden Text festlegen.
   * **Seitenumbruch**: Wählen Sie diese Option (![Umbruch](assets/break.png)), um zwischen den Listeninhalten einen Seitenumbruch einzufügen. Wenn diese Option (![kein Umbruch](assets/nobreak.png)) nicht ausgewählt ist, wird, wenn der Inhalt der Liste auf die nächste Seite übergeht, die gesamte Liste auf die nächste Seite verschoben, anstatt auf der Seite inmitten der Liste umzubrechen.

   * **Zuweisungskonfiguration**: Verwenden Sie diese Option, um die Mindest- und Höchstanzahl der Assets anzugeben, die der Liste hinzugefügt werden können.

1. Sie können mithilfe der folgenden Optionen festlegen, wie sich jedes Element in der Liste zur Laufzeit verhält:

   * **Bearbeitbar:** Wenn diese Option aktiviert ist, kann der Inhalt in der Benutzeroberfläche „Korrespondenz erstellen“ bearbeitet werden. (Diese Option steht für Listen- und Bildmodule nicht zur Verfügung.)
   * **Obligatorisch:** Wenn diese Option aktiviert ist, ist der Inhalt in der Benutzeroberfläche „Korrespondenz erstellen“ erforderlich.
   * **Ausgewählt:** Wenn diese Option aktiviert ist, ist der Inhalt der Benutzeroberfläche „Korrespondenz erstellen“ vorab ausgewählt.
   * **Stil überspringen:** Wenn diese Option aktiviert ist, werden Aufzählungszeichen und Nummerierungen in der Benutzeroberfläche „Korrespondenz erstellen“ übersprungen. (Diese Option steht für Bildmodule nicht zur Verfügung. Außerdem kann von den Optionen „Stil überspringen“, „Zusammengesetzte Nummerierung“ und „Listenstil ignorieren“ immer nur eine auf ein Modul angewendet werden. Eine dieser Optionen kann für ein Modul verwendet werden, wenn Sie für ein Modul die Option „Aufzählungszeichen hinzufügen“ auswählen.)
   * **Einzug:** Sie können den Einzug von allen Modulen/Inhalten ändern, die als Teil der Liste ausgewählt wurden. Einzüge werden in Form von Ebenen angegeben (beginnend bei null), wobei jede Einzugsebene einer Auffüllung von 36 pt entspricht.
   * **Zusammengesetzt:** Wenn diese Option aktiviert ist, wird die zusammengesetzte Nummerierung als Kombination aus dem Stil der äußeren (übergeordneten) Liste und ihrem eigenen Stil angewendet. Die zusammengesetzte Nummerierung in dieser verschachtelten Liste beruht auf der Position, an der sich diese verschachtelte Liste in der Reihenfolge der äußeren Liste befindet.
   * **Listenstil ignorieren:** Wenn die Option „Zusammengesetzte Nummerierung“ nicht aktiviert ist, dann ist die Option „Listenstil ignorieren“ aktiviert. Bei dieser Auswahl wird der eigene Stil der verschachtelten Liste ignoriert, und die Nummerierung wird von der äußeren Liste aus fortgesetzt. Daher werden die Module der verschachtelten Liste als Teil der äußeren Liste selbst behandelt, ungeachtet der Stile, die in der verschachtelten Liste angegeben sind. Wenn die Option „Listenstil ignorieren“ für eine verschachtelte Liste deaktiviert ist, haben die Module, die Teil dieser verschachtelten Liste sind, ihren eigenen Nummerierungsstil.
   * **Nächste beibehalten:** Legt den Seitenumbruch für die in einer Liste enthaltenen Assets fest. Wenn Sie die Eigenschaft „Nächste beibehalten“ eines Elements einer Liste auf **Ein** festlegen, werden dieses Element und das nächste auf derselben Seite angezeigt. Dies bedeutet, dass der Inhalt des ausgewählten Assets und des nächsten Assets nicht über zwei Seiten verteilt ist.

1. Tippen Sie auf **Speichern**.

### Best Practices/Tipps und Tricks {#best-practices-tips-and-tricks}

* Verwenden Sie eine konsistente Benennungskonvention, um Duplizierungen zu vermeiden.
* Verwenden einer geeigneten Datenwörterbuchbindung
* Die folgenden Regeln gelten für die Verwendung des Listeneditors zum Ändern einer Liste:

   * Eigenschaften aktualisieren: Zulässig
   * **Ändern des Datenwörterbuchs:** Zulässig, solange kein Element, das das Datenwörterbuch verwendet, damit verknüpft ist. Das Datenwörterbuch kann bei einer Aktualisierung nicht geändert werden.

## Bedingungen {#conditions}

Mit Hilfe von Bedingungen können Sie festlegen, welche Inhalte zum Zeitpunkt der Dokumenterstellung je nach den bereitgestellten Daten in das Schriftstück bzw. den Brief einbezogen werden sollen. Die Bedingung wird in Form von Steuerungsvariablen beschrieben. Beim Hinzufügen einer Bedingung haben Sie die Möglichkeit, ein Asset einzubeziehen, das auf dem Wert beruht, den die Steuerungsvariable hat.

Basierend auf den von Ihnen gewählten Optionen wird entweder nur der erste Ausdruck, der „true“ ergibt, basierend auf der aktuellen Bedingungsvariablen ausgewertet oder die gesamte Bedingung. Wenn sie den Brief in „Korrespondenz erstellen“ (CCR) füllen, verhalten sich Bedingungen wie „weiße Kästchen“. Wenn die Bedingung zu einer Liste führt, werden alle obligatorischen und vorab ausgewählten Elemente der Liste ausgegeben. Wenn eines dieser Elemente selbst eine Bedingung oder Liste ist, wird der resultierende Inhalt ebenfalls ausgegeben, und zwar als flache Liste von Text- und Bildinhalten in der Reihenfolge von oben nach unten mit Tiefensuche. Die Ergebnisse von Bedingungen können jeder Art sein (Text, Liste, Bedingung oder Bild).

### Implementieren von Bedingungen {#implementing-conditions}

Der Bedingungseditor enthält eine [Expression Builder](/help/forms/using/expression-builder.md)-Benutzeroberfläche, die das Erstellen von Ausdrücken mit mehreren Platzhaltern und Datenwörterbuchelementen unterstützt. Sie können in solchen Ausdrücken allgemeine Operanden und lokale/globale Funktionen verwenden. Jeder Ausdruck kann mit bestimmten Inhalten verknüpft werden. Optional kann es einen Standardabschnitt geben für den Fall, dass keiner der Ausdrücke als „true“ ausgewertet wird. Alle Ausdrücke werden in der Reihenfolge ausgewertet, in der sie definiert sind. Die ersten Ausdrücke, die als „true“ zurückgeben werden, werden ausgewählt, und der zugehörige Inhalt wird von diesem bedingten Modul zurückgegeben.

Wenn sich beispielsweise der Text der Geschäftsbedingungen in einem Brief je nach US-Bundesstaat der Kundin bzw. des Kunden unterscheidet und das Datenwörterbuch ein Element namens „state“ enthält, könnten Sie die Bedingung wie folgt hinzufügen:
* state = NY, select T&amp;C_NY Text-Absatz
* state = NC, select T&amp;C_NC Text-Absatz

Mit dem Bedingungseditor können Sie eine Standardbedingung festlegen. Wenn der Wert der Steuerungsvariablen keiner der Bedingungen entspricht, wird der mit der Standardbedingung verknüpfte Inhalt verwendet. Im Rahmen des oben genannten Beispiel ließe sich folgende Bedingungszeile hinzufügen:

* Default, select T&amp;C_Rest

### Erstellen einer Bedingung {#create-a-condition}

1. Wählen Sie **Formulare** > **Dokumentfragmente**.
1. Wählen Sie **Erstellen > Bedingung**.
1. Geben Sie folgende Informationen für die Liste an:

   * **Titel (Optional):** Geben Sie den Titel für die Bedingung ein. Der Titel muss nicht eindeutig sein und kann Sonderzeichen und nichtenglische Zeichen enthalten. Bedingungen werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Asset-Eigenschaften referenziert.
   * **Name:** Der eindeutige Name der Bedingung. Es können nicht zwei Assets (Text, Bedingung oder Liste) in beliebigen Status mit demselben Namen vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **Beschreibung (Optional)**: Geben Sie eine Beschreibung der Bedingung ein.
   * **Datenelement (Optional)**: Wählen Sie optional das Datenelement aus, mit dem das Element verknüpft werden soll. Es können nur Elemente der Liste hinzugefügt werden, die das gleiche Datenwörterbuch verwenden wie die Bedingung oder denen kein Datenwörterbuch zugewiesen ist. Das Zuweisen eines Datenwörterbuchs zu einer Liste erleichtert es der Person, die eine Briefvorlage erstellt, die passende Bedingung zu finden.
   * **Tags (Optional)**: Wählen Sie optional die Tags aus, die angewendet werden sollen. Sie können auch den Namen eines neuen Tags eingeben und es erstellen. (Das neue Tag wird erstellt, wenn Sie auf **Speichern** tippen.)

1. Tippen Sie auf **Weiter**.
1. Tippen Sie auf **Asset hinzufügen**.
1. Um ein Asset zur Bedingung hinzuzufügen, wählen Sie es auf der Seite „Assets auswählen“ aus und tippen Sie auf **Fertig**. Die Assets werden dem Bereich „Ausdruck“ hinzugefügt.
1. Sie können mithilfe der folgenden Optionen festlegen, wie sich die Bedingung zur Laufzeit verhält:

   * **Auswertung mehrerer Ergebnisse deaktivieren/Auswertung mehrerer Ergebnisse aktivieren**: Wenn diese Option aktiviert ist (angezeigt als „Auswertung...aktivieren”), werden alle Bedingungen ausgewertet, und das Ergebnis ist die Summe aller wahren Bedingungen. Wenn diese Option deaktiviert ist (angezeigt als „Auswertung...deaktivieren“), wird nur die erste Bedingung, die „true“ ergibt, ausgewertet und wird zur Ausgabe der Bedingung.
   * **Seitenumbruch**: Wählen Sie diese Option (![break](assets/break.png)), um zwischen den Modulen der Bedingungen einen Seitenumbruch hinzuzufügen. Wenn diese Option nicht ausgewählt ist (![nobreak](assets/nobreak.png)) und die Bedingung über die aktuelle Seite hinausreichen würde, wird die ganze Bedingung auf die nächste Seite verschoben, anstatt innerhalb der Bedingung einen Seitenumbruch einzufügen.

1. Um die Reihenfolge der Assets innerhalb der Bedingung zu ändern, tippen Sie auf das Pfeilsymbol eines Assets (![dragndrop](assets/dragndrop.png)), halten Sie es gedrückt und verwenden Sie die Drag-and-Drop-Funktion. Wenn der Benutzer auf der Benutzeroberfläche „Korrespondenz erstellen“ eine Briefvorlage öffnet, wird der Inhalt in der hier festgelegten Reihenfolge zusammengestellt.
1. Tippen Sie auf **Löschen**, um die Zeile zu löschen. Wenn Sie für die Standardzeile auf „Löschen“ tippen, werden nur die Asset-Informationen gelöscht.
1. Klicken Sie auf **Kopieren**, um eine Zeile zu duplizieren.
1. Tippen Sie auf **Bearbeiten**, um das Asset zu ändern oder den Ausdruck zu bearbeiten.

   Weiter:

   * Um das Asset zu aktualisieren, tippen Sie unter der Spalte „Asset“ auf das Ordnersymbol.
   * Um den Expression Builder zum Einfügen eines Ausdrucks zu öffnen, tippen Sie unter der Spalte „Ausdruck“ auf das Ordnersymbol. Weitere Informationen zum Expression Builder finden Sie unter [Expression Builder](/help/forms/using/expression-builder.md).

### Best Practices/Tipps und Tricks {#best-practices-tips-and-tricks-1}

* Verwenden Sie eine konsistente Namenskonvention, um die Suche zu erleichtern und Duplizierungen zu vermeiden.
* Bedingungen verhalten sich wie „case“-Anweisungen, daher ist die Reihenfolge der Bedingungen wichtig. Die erste Übereinstimmung wird zurückgegeben.
* Verwenden einer geeigneten Datenwörterbuchbindung
* Die folgenden Regeln gelten für die Verwendung des Bedingungseditors zum Bearbeiten einer Bedingung:

   * **Variablen hinzufügen:** Zulässig
   * **Variablen entfernen:** Zulässig
   * **Eigenschaften aktualisieren:** Zulässig
   * **Datenwörterbuch ändern:** Zulässig, solange das Datenwörterbuchelement nicht verwendet wird.

## Layout-Fragmente {#layoutfragments}

Ein Layout-Fragment basiert auf in Designer erstellten XDPs. Zum Erstellen von Layout-Fragmenten müssen Sie die XDPs erstellen und sie [auf AEM Forms hochladen](/help/forms/using/import-export-forms-templates.md).

Ein oder mehrere Layout-Fragmente können Teile eines Briefs bilden und das grafische Layout dieser Teile definieren. Ein Layout-Fragment kann typische Formularfelder wie „Adresse“ und „Referenz“ sowie leere Unterformulare, die Zielbereiche kennzeichnen, enthalten. Darüber hinaus können Sie mit Layout-Fragmenten Tabellen erstellen und sie in Briefe einfügen.

Ein gängiger Anwendungsfall besteht darin, wiederverwendbare Layout-Muster in Briefen zu suchen und Layout-Fragmente dafür zu erstellen. Beispiel: Anrede, Adresse und Betreff eines Briefs kommen in derselben Reihenfolge in mehreren Briefen vor. Ein weiteres Beispiel könnte eine Tabelle mit immer ähnlicher Anzahl von Zeilen und Spalten sein, die in mehreren Briefen verwendet wird.

Sie können ein Layout-Fragment basierend auf einer vorhandenen XDP erstellen. Ein Layout-Fragment kann entweder aus Feldern und Zielbereichen oder aus mindestens einer Tabelle bestehen. Die Tabellen in einem Layout können statisch oder dynamisch sein. Eine XDP wird in Designer erstellt und in [AEM Forms hochgeladen](/help/forms/using/import-export-forms-templates.md). Eine XDP kann die Struktur eines Layout-Fragments oder die Struktur eines Briefs bilden. Weitere Informationen finden Sie unter [Erstellung von Layouts](/help/forms/using/layout-design-details.md).

Wenn Sie Fragmente verwenden, die mit Zielbereichen verbunden sind, kann der Brief zum Zeitpunkt des Verfassens geändert werden. Es können Layout-Fragmente mit verschiedenen Abmessungen erstellt werden, und das geeignete Fragment kann mit dem Zielbereich verbunden werden. Mit Layout-Fragmenten können Sie auch einige Tabelleneigenschaften anpassen:

1. Sie können die Zeilen- und Spaltenanzahl erhöhen.
1. Sie können den Kopf- und Fußzeilentext für weitere Zeilen und Spalten angeben.
1. Sie können das Verhältnis der Tabellenspaltenbreite definieren. Zur Laufzeit wird die Größe der Tabellenspalten gemäß dem definierten Verhältnis und dem verfügbaren Platz angepasst. Das Breitenverhältnis muss in der Summe 100 betragen. Andernfalls ist es nicht gültig.
1. Falls eine Tabelle ein Platzhalter ist (enthält nur eine einzige leere Zelle), können Sie den Typ (Zielbereich/-feld) der neuen Spalten definieren.
1. Sie können Kopf- und Fußzeilen ausblenden.

Bevor Sie dieses Verfahren durchführen, erstellen Sie mithilfe von Designer ein XFA-Fragment. Das Fragment kann Tabellen zum Organisieren von Feldern und Zielbereichen enthalten. Designer ermöglicht die Erstellung zweier Tabellentypen: statisch und dynamisch. Statische Tabellen enthalten eine feste Anzahl von Zeilen. Statische Tabellen können Zielbereiche und -felder enthalten. Diese Zielbereiche und -felder können nicht an wiederholende DDEs gebunden werden. Eine dynamische Tabelle kann auch eine einzelne Zeile aufweisen. Die an Tabellenzellen gebundenen Daten bestimmen die Anzahl der Zeilen für dynamische Tabellen. Eine dynamische Tabelle kann ausschließlich Felder enthalten. DDEs können wiederholend oder nicht wiederholend sein.

Beachten Sie beim Entwerfen von Tabellen die folgenden Punkte:

1. Tabellen können zum Zeitpunkt der Layout-Fragmenterstellung angepasst werden. Die Option zum Anpassen ist allerdings nur verfügbar, wenn das übergeordnete Teilformular der Tabelle fließend ist.
1. Für dynamische Tabellen verwenden alle Felder, wiederholbaren Zeilen und Tabellen die Bindung „Name verwenden“ für die ordnungsgemäße Datenzusammenführung.
1. Für dynamische Tabellen sind alle wiederholenden DDEs, die an die Tabellenfelder gebunden sind, Teil der gleichen Hierarchie. Für nicht wiederholende DDEs gibt es keine solche Einschränkung.
1. Zum Zeitpunkt der Zusammenführung des Layout-Fragments und des übergeordneten Zielbereichs wird die Größe der Tabellen gemäß dem verfügbaren Platz angepasst. Die Größenänderung findet allerdings nur statt, wenn das Layout-Fragment keinen Zielbereich und kein Zielfeld direkt im Unterformular der obersten Ebene enthält. Zielbereiche und -felder innerhalb einer Tabelle sind zulässig.
1. Sie können Platzhaltertabellen erstellen. Platzhaltertabellen enthalten nur eine einzige leere Zelle.

* Für Platzhaltertabellen können Sie folgende Eigenschaften zum Zeitpunkt der Fragmenterstellung anpassen.

   * Zeilenanzahl
   * Spaltenanzahl
   * Kopf- und Fußzeile für die einzelnen Spalten
   * Typ (Zielbereich/-feld) der einzelnen Spalten
   * Breitenverhältnis der einzelnen Spalten

* Für eine Nicht-Platzhaltertabelle können Sie die folgenden Eigenschaften anpassen:

   * Zeilenanzahl
   * Spaltenanzahl
   * Kopf- und Fußzeile für zusätzliche Spalte
   * Breitenverhältnis der einzelnen Spalten

Sie können Fragmente in einem Brief verschachteln. Dies bedeutet, dass Sie ein Fragment innerhalb eines Fragments hinzufügen können. Die Correspondence Management-Lösung unterstützt bis zu vier Verschachtelungsebenen in einem Brief: **Brief *>*Fragment *>*Fragment *>*Fragment *>*Fragment.**

Ein detailliertes Beispiel der Verwendung von statischen und dynamischen Tabellen in Layout-Fragmenten finden Sie unter [Beispiel mit Beispieldateien: Verwendung von statischen und dynamischen Tabellen in einem Brief](#examplewithsamplefiles).

### Layout-Fragment erstellen {#creating-a-layout-fragment}

1. Wählen Sie **Erstellen** > **Layout-Fragment**.
1. Correspondence Management zeigt die verfügbaren XDP-Dateien an. Wählen Sie die XDP-Datei aus, auf der Ihr Layout-Fragment basieren soll, und tippen Sie auf **Weiter**.
1. Geben Sie folgende Informationen für das Layout an:

   * **Titel (Optional):** Geben Sie den Titel für das Layout-Fragment ein. Der Titel muss nicht eindeutig sein und kann Sonderzeichen und nichtenglische Zeichen enthalten. Layout-Fragmente werden durch ihre Titel (falls verfügbar), wie etwa in Miniaturansichten und Asset-Eigenschaften, referenziert.
   * **Name**: Der eindeutige Name des Layout-Fragments. Es können nicht zwei Assets (Text, Bedingung oder Liste) in beliebigen Status mit demselben Namen vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten. Dieser Name wird auf der Benutzeroberfläche „Elemente verwalten“ in der Liste angezeigt.
   * **Beschreibung (Optional)**: Beschreibung, die auf der Benutzeroberfläche „Elemente verwalten“ in der Liste angezeigt wird.
   * **Tags (Optional)**: Wählen Sie optional die Tags aus, die auf die Bedingung angewendet werden sollen. Sie können auch den Namen eines neuen Tags eingeben und es erstellen.

1. Tippen Sie auf die Registerkarte **Tabelle** und geben Sie die folgenden Informationen für das Layout an:

   * **Konfiguration für**: Wählen Sie die zu konfigurierende Tabelle aus. Als Suffix des Tabellennamens wird in der Dropdown-Liste „(Statisch)“ angezeigt, wenn die Tabelle statisch ist, oder „(Dynamisch)“, wenn es sich um eine dynamische Tabelle handelt. Statische Tabellen enthalten eine feste Anzahl von Zeilen. Statische Tabellen können Zielbereiche und -felder enthalten. Diese Zielbereiche und -felder können nicht an wiederholende DDEs gebunden werden. Die an Tabellenzellen gebundenen Daten bestimmen die Anzahl der Zeilen für dynamische Tabellen.

   * **Zeilen**: Wählen Sie die Anzahl der Zeilen für das Layout aus. Die konfigurierte Zeilenanzahl muss größer oder gleich der ursprünglichen Zeilenanzahl sein.
   * **Spalten**: Wählen Sie die Anzahl der Spalten für das Layout aus. Die konfigurierte Spaltenanzahl muss größer oder gleich der ursprünglichen Spaltenanzahl sein.

   Für jede Spalte sind folgende Details erforderlich:

   * **Kopfzeile**: Text, der für die Kopfzeile angezeigt werden soll
   * **Fußzeile**: Text, der für die Fußzeile angezeigt werden soll
   * **Typ**: Typ der zusätzlichen Spalte. Feld- oder Zielbereich. Der Typ ist für statische Platzhaltertabellen aktiviert. Der Typ kann auf Spaltenebene definiert werden, nicht auf Zellenebene. Alle Zellen in einer erweiterten Spalte weisen den gleichen Typ auf. Für eine dynamische Tabelle haben alle Spalten den Typ „Feld“. Bei Nicht-Platzhaltertabellen können Sie den Typ der zusätzlichen Spalten nicht definieren. In diesem Fall ist der Typ der zusätzlichen Zellen in einer erweiterten Spalte identisch mit dem Typ der letzten Spalte in dieser Zeile. Der Typ der Zelle in der zusätzlichen Zeile ist identisch mit dem Typ der letzten Zelle in dieser Spalte.
   * **Breitenverhältnis**: Verhältnis der Tabellenspaltenbreiten.

   Ein detailliertes Beispiel der Verwendung von statischen und dynamischen Tabellen in Layout-Fragmenten finden Sie unter [Beispiel mit Beispieldateien: Verwendung von statischen und dynamischen Tabellen in einem Brief](#examplewithsamplefiles).

1. Tippen Sie auf **Speichern**.

### Hochladen einer XDP-Datei in Correspondence Management {#upload-an-xdp-to-correspondence-management}

Anweisungen zum Hochladen/Importieren einer XDP in Correspondence Management finden Sie unter [Importieren und Exportieren von Assets in AEM Forms](/help/forms/using/import-export-forms-templates.md).

### Best Practices/Tipps und Tricks {#best-practices-tips-and-tricks-2}

#### Festlegen der Standardbindung für Teilformulare {#set-the-default-subform-binding}

Bei der Erstellung von Zielbereichen in Designer ist es hilfreich, die Standardbindung für alle neuen Teilformulare auf „Ohne“ einzustellen.

So legen Sie die Standardbindung fest:

1. Tippen Sie in Designer auf **Tools** > **Optionen** > **Datenbindungen** > **Teilformularbindung**.

1. Wählen Sie in der Liste „Standardbindung für neue Teilformulare“ die Option **Keine Datenbindung** aus.

Dadurch stellen Sie sicher, dass für Teilformulare, die Sie mit dem Befehl „Einfügen“ > „Teilformular“ oder per Drag &amp; Drop aus der Objektpalette einfügen, die Bindungsmethode standardmäßig auf „Ohne“ eingestellt ist. Dadurch ist ein neues Teilformular standardmäßig ein Zielbereich, außer Sie fügen Inhalte hinzu, ändern die Bindungseinstellung oder fügen das Suffix „_int“ an den Namen des Teilformulars an.

#### Konformität mit Abschnitt 508 {#section-compliance}

Wenn ein auf der Benutzeroberfläche „Korrespondenz erstellen“ erstellter Brief in einem späteren Workflow-Schritt mit Daten gefüllt wird, halten Sie sich bei der Erstellung des Layouts an folgende Empfehlungen in Bezug auf Abschnitt 508. Andernfalls dient die PDF-Datei des Briefes der Anzeige und Sie können diese Empfehlungen ignorieren:

* Alle als Zielbereich fungierenden Teilformulare und alle Felder in einem Layout haben eine Aktivierreihenfolge.
* Felder mit Beschriftungen sind standardmäßig mit Abschnitt 508 konform. Das Feldattribut /field/assist/speak@priority ist standardmäßig auf „custom“ gesetzt, d. h. sofern kein benutzerdefinierter Text für eine Bildschirmlesehilfe bereitgestellt wird, liest die Bildschirmlesehilfe die Beschriftung des Feldes.
* Legen Sie bei Feldern ohne Beschriftungen eine QuickInfo fest und weisen Sie Bildschirmlesehilfen an, die QuickInfo zu lesen, indem Sie

`/field/assist/speak@priority="toolTip"` festlegen und in `/field/assist/toolTip` den QuickInfo-Text angeben.

#### Datumsformate in Designer und Asset Configuration Manager {#date-formats-in-designer-and-asset-configuration-manager}

Stellen Sie beim Entwerfen eines Layouts in Designer sicher, dass die Formate für Datumsfelder mit den Datumsanzeigeformaten in den [Konfigurationseigenschaften von Correspondence Management](/help/forms/using/cm-configuration-properties.md) übereinstimmen. Weitere Informationen finden Sie unter „Formatieren von Feldwerten und Verwenden von Mustern“ in der Designer-Hilfe.

#### Erfassen von Datumsbereichen {#capturing-date-ranges}

Wenn eine Datumskombination einzufügen ist, z. B. „startDate“ bis „endDate“, verwenden Sie ein einzelnes Teilformular, um eine korrekte Ausrichtung im endgültigen Brief sicherzustellen und die Anzahl der Felder möglichst gering zu halten.

#### Festlegen von Bindungen auf Formularebene {#setting-form-level-binding}

Wenn ein Layout viele Felder und Zielbereiche enthält, die einzelnen XML-Elementen zugeordnet sind, verwenden Sie die Bindung auf Formularebene und erstellen Sie für jedes Element einen separaten Knoten. Felder, die auf Formularebene gebunden sind, werden bei der Zuordnung von Daten in Correspondence Management ignoriert.

#### Verwenden Sie auf einer Musterseite keine Teilformulare als Zielbereiche. {#do-not-use-subform-target-areas-in-a-master-page}

Teilformulare als Zielbereiche auf einer Musterseite sind in der Benutzeroberfläche „Assets verwalten“ nicht sichtbar, sodass ihnen keine Daten zugeordnet werden können.

#### Auswählen der geeigneten Positionen und Typen für Zielbereiche {#choosing-appropriate-positions-and-types-for-target-areas}

Wählen Sie Teilformulare beim Entwerfen des Layouts sorgfältig aus. Wenn ein Layout ein einzelnes Teilformular enthält, kann es sich um eine Fließform handeln. Wenn Sie Felder in dem Teilformular platziert haben, können Sie es in ein anderes Teilformular einbetten, sodass das eingebettete Teilformular auch die Fließform annimmt und das Layout nicht beeinträchtigt wird.

#### Platzieren von Feldern auf Musterseiten {#placing-fields-on-master-pages}

Beachten Sie Folgendes, wenn Sie ein Feld auf eine Musterseite platzieren:

* Legen Sie die Bindung von Musterseitenfeldern auf „Globale Daten verwenden“ fest.
* Platzieren Sie das Feld nicht direkt unter der Stamm-PageArea der Musterseite.
* Betten Sie das Feld in ein benanntes Teilformular ein und stellen Sie sicher, dass die Bindung des benannten Teilformulars auf „Name verwenden“ festgelegt ist.

## Erstellen von Tabellen mithilfe von Layout-Fragmenten {#creating-tables-using-layout-fragments}

Viele Briefvorlagen enthalten Tabellen. Tabellen können statisch sein, z. B. eine Tabelle mit Nutzungsbedingungen, in der jede Zeile eine Bedingung darstellt und jeder Teil in einer separaten Spalte angezeigt wird. Tabellen können auch dynamisch sein, z. B. Kontoinformationen, die Informationen wie Kundenname, Kontonummer, Transaktionsnummer und Transaktionsbetrag enthalten.

* **Statische Tabellen**: Tabellen werden manchmal mit Zeilen erstellt, die eine andere Anzahl von Spalten aufweisen, wie etwa bei einer Tabelle mit Nutzungsbedingungen. Dort stellt jede Zeile eine Bedingung dar und jede Bedingung kann verschiedene Unterteile aufweisen. Jeder Teil wird in einer separaten Spalte angezeigt.
* **Dynamische Tabellen**: Layout-Fragmente stellen die Möglichkeit bereit, die Felder einer dynamischen Tabelle an Sammlungs-DDEs zu binden. Zum Zeitpunkt der Brieferstellung werden Tabellenzeilen entsprechend der Größe der Sammlungs-DDEs generiert.

Das DD hat ein Sammlungselement Nominee_details, das Composite-Element mit drei primitiven Elementen enthält: Nominee_name, Nominee_address und Nominee_gender.
Dynamische XDP verfügen außerdem über die gleichen Kopfzeilen. So können Sie die dynamischen XDP-Felder mit den oben genannten Felder von DD zuordnen.

### Beispiel mit Beispieldateien: Verwenden von statischen und dynamischen Tabellen in einem Brief {#examplewithsamplefiles}

Dieses Beispiels zeigt, wie Sie eine dynamische und eine statische Tabelle erstellen, die dynamische Tabelle an DDEs binden und dann einen Brief erstellen, der diese beiden Tabellen enthält. Während Sie mit diesem Beispiel arbeiten, können Sie Dateien entweder neu erstellen oder die in den Schritten bereitgestellten Eingabedateien verwenden.

1. Erstellen Sie ein Datenwörterbuch (DD), das Sie im Beispiel verwenden möchten, wie in der Grafik dargestellt.

   Wählen Sie dann das Datenwörterbuch aus und exportieren Sie Beispieldaten. Die XML-Datei, die Sie erhalten, enthält Mitarbeiterdaten und drei Instanzen für „Nominee_details“ (standardmäßig werden 3 Instanzen heruntergeladen. Sie können Instanzen je nach Bedarf hinzufügen oder löschen. Aktualisieren Sie die Werte und importieren Sie dann Testdaten in das Datenwörterbuch. Die CMP-Datei ist das Paket und enthält das Datenwörterbuch. Importieren Sie also das Datenwörterbuch in Correspondence Management.

   Weitere Informationen zum Arbeiten mit Datenwörterbüchern und Testdaten finden Sie unter [Datenwörterbuch](/help/forms/using/data-dictionary.md#p-working-with-test-data-p).

   ![Datenwörterbuchstruktur](assets/dd.jpeg)

[Datei laden](assets/exportpackage_1431709897770.cmp.zip)

1. Erstellen Sie in Designer zwei XDPs (Layout-Fragmente): eine dynamische Tabelle und eine statische Tabelle. Für beide Layouts:

   * Fügen Sie der Tabellenspalte ein Teilformular hinzu. Stellen Sie sicher, dass Sie das Layout des übergeordneten Teilformulars der Tabelle auf Fluss ändern, und entfernen Sie die Bindungen des Teilformulars in der Tabelle.
   * Fügen Sie der Tabellenzelle ein Teilformular hinzu. Stellen Sie sicher, dass Sie das Layout des übergeordneten Teilformulars der Tabelle auf Fluss ändern, und entfernen Sie die Bindungen des Teilformulars in der Tabelle.

   Oder verwenden Sie die hier angehängten statischen und dynamischen XDPs.

   Weitere Informationen zum Arbeiten mit Layout-Fragmenten finden Sie unter [Layout-Fragmente](#layoutfragments).
Weitere Informationen zum Entwerfen von Layouts finden Sie unter [Designer-Hilfe](https://help.adobe.com/de_DE/AEMForms/6.1/DesignerHelp/).

[Datei abrufen](assets/static.xdp.zip)

[Datei abrufen](assets/dynamic.xdp.zip)

1. Laden Sie die XDP-Dateien auf AEM Forms hoch.
1. Erstellen Sie ein Layout-Fragment basierend auf der dynamischen XDP. Die Registerkarte „Tabelle“ der Eigenschaften zeigt an, dass die Tabelle dynamisch ist (Feld „Konfiguration für“). Die Anzahl der Zeilen (1) und Spalten (3) wird aus dem XDP-/Layout-Fragment abgeleitet.

   Die Felder des Layouts werden später an das importierte Datenwörterbuch gebunden, und im Brief wird die Anzahl der Zeilen basierend auf der Anzahl der Datensätze in der Testdatendatei (die an das Datenwörterbuch angehängte Datendatei) dynamisch erstellt. 

   ![Bildschirm zum Erstellen eines Layout-Fragments](assets/dynamictableproperties.png)

   Klicken Sie hier, um Bilder in voller Größe zu öffnen

1. Erstellen Sie ein Layout-Fragment basierend auf der statischen XDP. Die Registerkarte „Tabelle“ der Eigenschaften zeigt an, dass die Tabelle statisch ist (Feld „Konfiguration für“). Die Anzahl der Zeilen (1) und Spalten (3) wird aus dem XDP-/Layout-Fragment abgeleitet.

   Sie können die Anzahl der Spalten und Zeilen hier ändern. Je nach Ihrer Auswahl auf diesem Bildschirm bleibt die Anzahl von Zeilen und Spalten einer statischen Tabelle in einem mit diesem Layout erstellten Brief unverändert.
   [![Bildschirm zum Erstellen eines Layout-Fragments](assets/statictableproperties.png)](assets/statictableproperties-1.png)

1. Erstellen Sie einen Brief unter Verwendung beider Layout-Fragmente darin. Wenn Sie eine dynamische XDP in den Brief einfügen, legen Sie die Bindung seiner Felder auf die Sammlungselemente des Datenwörterbuchs fest.

   Weitere Informationen zum Erstellen von Briefen und Briefvorlagen finden Sie unter [Erstellen eines Briefes](/help/forms/using/create-letter.md).

1. Speichern Sie den Brief und zeigen Sie ihn in der Vorschau an. Wenn Sie den Brief in der Vorschau anzeigen, werden die Werte aus dem Datenwörterbuch im Brief angezeigt. Für die dynamische Tabelle sind drei Zeilen vorhanden. Dies liegt daran, dass die Testdaten drei Datensätze für diese Zeilen aufweisen.

   Für die statische Tabelle sind so viele Zeilen und Spalten vorhanden, wie von Ihnen bei der Erstellung des Layout-Fragments festgelegt.

   ![Statische Tabelle im Brief](assets/statictableletter.png)

   Für die dynamische Tabelle werden die drei Zeilen entsprechend der Anzahl der Datensätze in der Testdatendatei angezeigt. Dies verhält sich so, weil Sie beim Hinzufügen des Layouts zum Brief eine Bindung zwischen den Feldern der dynamischen Tabelle und den Collection-Elementen des Datenwörterbuchs erstellt haben. Die Werte „Name“, „Adresse“ und „Geschlecht“ werden aus der von Ihnen verwendeten Testdatendatei gefüllt.

   ![Dynamische Tabelle im Brief](assets/dynamictableletter.png)

## Erstellen einer Kopie eines Dokumentfragments {#create-a-copy-of-a-document-fragment}

Um ein Dokumentfragment mit Eigenschaften und Inhalten schnell zu erstellen, das einem vorhandenen Dokumentfragment ähnlich ist, können Sie es kopieren und einfügen.

1. Wählen Sie in der Liste der Dokumentfragmente ein oder mehrere Dokumentfragmente aus. Auf der Benutzeroberfläche wird das Symbol „Kopieren“ angezeigt.
1. Tippen Sie auf Kopieren. Auf der Benutzeroberfläche wird das Symbol „Einfügen“ angezeigt. Sie können vor dem Einfügen auch in einen Ordner wechseln. Verschiedene Ordner können Assets mit demselben Namen enthalten. Weitere Informationen zu Ordnern finden Sie unter [Ordner und Organisieren von Assets](/help/forms/using/import-export-forms-templates.md#folders-and-organizing-assets).
1. Tippen Sie auf „Einfügen“. Das Dialogfeld „Einfügen“ wird angezeigt. Wenn Sie die Dokumentfragmente kopieren und an derselben Stelle einfügen, weist das System den neuen Kopien automatisch Namen und Titel zu, Sie können diese jedoch ändern.
1. Bearbeiten Sie bei Bedarf den Titel und den Namen, mit denen Sie die Kopie des Dokumentfragments speichern möchten.
1. Tippen Sie auf „Einfügen“. Die Kopie des Dokumentfragments wird erstellt.
