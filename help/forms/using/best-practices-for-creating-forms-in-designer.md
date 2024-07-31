---
title: Best Practices zum Erstellen von Formularen in Forms Designer
description: Erfahren Sie mehr über die Best Practices für Barrierefreiheit beim Erstellen von Formularen in Forms Designer.
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 3a9d7943-2c34-4e0a-9803-7ce1ef40f676
source-git-commit: 0d491be4fb2605220b1558c8c877151ab4405978
workflow-type: tm+mt
source-wordcount: '11687'
ht-degree: 0%

---

# Best Practices zum Erstellen von Formularen in Forms Designer

Mit LiveCycle Designer können Sie Rich-Form-Inhalte erstellen und die Richtlinien von Abschnitt 508 einhalten. Dieses Handbuch enthält einen Überblick über die Best Practices für die Erstellung eines barrierefreien Formulars und Richtlinien für die Implementierung dieser Best Practices mit LiveCycle Designer. Die folgenden Best Practices werden behandelt:

1. [Einfache und einfache Verwendung von Formularen](#keep-simple)
1. [Konfigurieren von Formulareigenschaften zum Generieren von Barrierefreiheitsinformationen](#configure-form-properties)
1. [Auswählen der richtigen Steuerelemente](#choose-right-controls)
1. [Angabe von Textäquivalenten für Bilder](#provide-text-equivalents)
1. [Angabe von angemessenen Beschriftungen für Formularsteuerelemente](#provide-proper-labels)
1. [Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind.](#ensure-reading-tab-order)
1. [Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind](#ensure-keyboard-accessible)
1. [Verantwortung für die Verwendung der Farbe](#use-color-responsibly)
1. [Überschriftzellen für Tabellen bereitstellen](#provide-heading-cells)
1. [Bereitstellung einer navigierbaren Formularstruktur](#provide-navigable-form)
1. [Unterbrechungsfreies Scripting vermeiden](#avoid-disruptive-scripting)
1. [Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind.](#ensure-audio-video-accessible)
1. [Ermitteln Sie die natürliche Sprache und alle Sprachänderungen.](#identify-natural-language)

## Einfache und einfache Verwendung von Formularen {#keep-simple}

Ein Formular ist nicht zugänglich, wenn es nicht einfach zu verwenden ist. Sie sollten versuchen, einfache und nutzbare Formulare zu entwerfen. Ein einfaches Layout von Steuerelementen und Feldern mit klaren, aussagekräftigen Beschriftungen und QuickInfos erleichtert allen Benutzern die Verwendung des Formulars.
Die Erstellung von Formularen, die übersichtlich und logisch angeordnet sind und klare und einfache Anweisungen enthalten, hilft allen Benutzern, Formulare möglichst einfach auszufüllen. Navigationsfunktionen wie die Tab-Reihenfolge und Tastaturbefehle sollten die logische Reihenfolge der Objekte im Formular unterstützen.

### Verschieben, Blinken oder Blinken von Inhalten vermeiden

Bei einigen Personen mit lichtempfindlicher Epilepsie kann ein Anfall auftreten, der durch eine Frequenzbewegung größer als 2 Hz (1 Hz oder Hertz, entspricht 1 Hz pro Sekunde) und kleiner als 55 Hz (55 pro Sekunde) ausgelöst wird.

Die Bewegung bei weniger als 2 Hz gilt als langsam genug, um für Personen mit photosensibler Epilepsie sicher zu sein. Eine Bewegung von mehr als 55 Hz wird als unwahrnehmbar betrachtet.

Entwickler sollten sich dieser Parameter bewusst sein, wenn sie Bewegungen von Webinhalten verwenden.

Andere Benutzer haben möglicherweise kognitive Behinderungen, die es schwierig machen, sich zu konzentrieren, wenn in der Form animierte oder blinkende Inhalte vorhanden sind.

Versuchen Sie im Allgemeinen, die Verwendung von optischen Effekten, die von Skripten eingefügt werden (z. B. blitzender Text oder Animation), in interaktiven Formularen zu vermeiden. Diese Auswirkungen verringern die Benutzerfreundlichkeit der Formulare für bestimmte Benutzer.

Verwandte Checkpoints
* Abschnitt 508 § 11934.21

   * h) Bei der Darstellung der Animation müssen die Informationen nach Wahl des Benutzers mindestens in einer nicht animierten Darstellungsform angezeigt werden können.
   * (k) Die Software darf keine blinkenden oder blinkenden Texte, Objekte oder andere Elemente mit einer Blinkfrequenz größer als 2 Hz und kleiner als 55 Hz verwenden.
* Abschnitt 508 §11934.22
   * j) Seiten müssen so ausgelegt sein, dass sie nicht dazu führen, dass der Bildschirm mit einer Frequenz größer als 2 Hz und kleiner als 55 Hz flackert.
* WCAG 1.0
   * 7.1 Bis Benutzeragenten es Benutzern erlauben, das Flackern zu kontrollieren, sollten Sie vermeiden, dass der Bildschirm flackert. (P1)
   * 7.2 Bis Benutzeragenten es Benutzern ermöglichen, das Blinken zu steuern, vermeiden Sie, dass Inhalte blinken (d. h. ändern Sie die Darstellung regelmäßig, z. B. ein- und ausschalten) (P2).
   * 7.3 Bis Benutzer mithilfe von Benutzeragenten bewegte Inhalte einfrieren können, sollten Sie das Verschieben von Seiten vermeiden.
   * 14.1 Verwenden Sie die für den Inhalt einer Site am besten geeignete und einfachste Sprache.
* WCAG 2.0
   * 2.2.2 Informationen zum Anhalten, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder automatisch aktualisierte Informationen gelten alle folgenden Bedingungen: (Stufe A)
   * 2.3.1 Grenzwert von maximal dreimaligem Flash: Webseiten enthalten nichts, das in einem Zeitraum von einer Sekunde öfter als dreimal blinkt oder der Blitz unterhalb der allgemeinen Blitzschwellen und der roten Blitzschwellen liegt. (Stufe A)
   * 2.3.2 Drei Flash: Webseiten enthalten nichts, das in einem Zeitraum von einer Sekunde mehr als dreimal blinkt. (Stufe AAA)


## Konfigurieren von Formulareigenschaften zum Generieren von Barrierefreiheitsinformationen {#configure-form-properties}

Damit ein Formular barrierefrei ist, muss es von Hilfstechnologien [wahrnehmbar](https://www.w3.org/TR/WCAG20/#perceivable) sein. Die meisten Bildschirmlesehilfen berücksichtigen beispielsweise nicht das visuelle Layout des Formulars, sondern die zugrunde liegende Struktur.

Um diese zugrunde liegende Struktur mithilfe von LiveCycle Designer zu implementieren, müssen Sie ein PDF-Formular mit Barrierefreiheitsinformationen (manchmal auch als Tags bezeichnet) erstellen, damit die Sprachausgabe oder andere Hilfstechnologien den Formulartext und die Formularkomponenten lesen können. In einem Formular mit Barrierefreiheitsinformationen enthält jedes Element Informationen über seine eigene Struktur sowie Informationen darüber, wie es mit anderen Elementen verbunden oder davon abhängig ist. Nur in PDF-Dateien mit enthaltenen Barrierefreiheitsinformationen können Bildschirmlesehilfen den Inhalt eines Dokuments genau identifizieren und beschreiben.

Um ein barrierefreies Formular zu erstellen, müssen Sie die Formulareigenschaften so konfigurieren, dass LiveCycle Designer beim Speichern des Formularentwurfs als PDF-Datei Barrierefreiheitsinformationen generiert:
1. Wählen Sie Datei > Formulareigenschaften.
1. Klicken Sie auf die Registerkarte Speicheroptionen und stellen Sie im Bereich PDF sicher, dass die Option &quot;Generate Accessibility Information (Tags) For Acrobat&quot;ausgewählt ist.
1. Klicken Sie auf „OK“.

In LiveCycle Designer ist diese Option standardmäßig aktiviert.

>[!NOTE]
> Diese Optionen gelten nur beim Speichern des Formularentwurfs als PDF-Datei. Sie gelten nicht für PDF-Dateien, die mit LiveCycle Forms erstellt wurden und über Konfigurationsoptionen verfügen, die in LiveCycle Designer von dieser Option unabhängig sind.

**Verwandte Checkpoints**

* Abschnitt 508 § 1194.21
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare ermöglicht das Formular Personen, die Hilfstechnologien nutzen, den Zugriff auf die Informationen, Feldelemente und Funktionen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Richtungen und Hinweise.
* Abschnitt 508 § 1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugang zu den Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars, einschließlich aller Richtungen und Hinweise, erforderlich sind.


## Auswählen der richtigen Steuerelemente {#choose-right-controls}

Verwenden Sie beim Entwerfen Ihrer Formulare Entwicklungsobjekte aus den Registerkarten der LiveCycle Designer-Objektbibliothek. Sie können dieses Bedienfeld anzeigen, indem Sie &quot;Fenster&quot;> &quot;Objektbibliothek&quot;wählen oder Umschalt+F12 drücken (siehe Abbildung 1).

![Objektbibliothek-Bedienfeld](/help/forms/using/assets/image-1.png)

Abbildung 1: **Objektbibliothek-Bedienfeld**

Wenn Sie andere Objekte verwenden, können diese von Hilfstechnologien ignoriert werden. Die Verwendung nur der Standardobjekte spart Ihnen den zusätzlichen Aufwand beim Definieren der Barrierefreiheitseigenschaften für selbst erstellte Objekte. Wenn Sie eigene benutzerdefinierte Objekte erstellen und verwenden, stellen Sie sicher, dass Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;Barrierefreiheitseigenschaften wie Rolle, QuickInfo, Rangfolge des Readers auf dem Bildschirm und Text für benutzerdefinierte Reader festlegen. Um die Palette &quot;Ein-/Ausgabehilfe&quot;anzuzeigen, wählen Sie &quot;Fenster&quot;> &quot;Ein-/Ausgabehilfe&quot;.

**Verwandte Checkpoints**
* Abschnitt 508 § 1194.21
   * c) Es ist eine klar definierte Bildschirmanzeige des aktuellen Fokus anzugeben, die sich zwischen den interaktiven Schnittstellenelementen bewegt, wenn sich der Eingabefokus ändert. Der Fokus muss programmatisch offen gelegt werden, damit Hilfstechnologien Fokus- und Fokusänderungen nachverfolgen können.
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare ermöglicht das Formular Personen, die Hilfstechnologien nutzen, den Zugriff auf die Informationen, Feldelemente und Funktionen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Richtungen und Hinweise.
* Abschnitt 508 § 1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugang zu den Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars, einschließlich aller Richtungen und Hinweise, erforderlich sind.

* WCAG 2.0
   * 3.2.4 Konsistente Erkennung: Komponenten, die innerhalb eines Satzes von Webseiten dieselbe Funktionalität aufweisen, werden konsistent identifiziert. (Stufe AA).
   * 4.1.2 Name, Rolle, Wert: Für alle Komponenten der Benutzeroberfläche (einschließlich, aber nicht beschränkt auf: Formularelemente, Links und Komponenten, die von Skripten generiert werden) kann der Name und die Rolle programmgesteuert bestimmt werden. Status, Eigenschaften und Werte, die vom Benutzer festgelegt werden können, können programmgesteuert festgelegt werden. Die Benachrichtigung über Änderungen an diesen Elementen steht Benutzeragenten zur Verfügung, einschließlich Hilfstechnologien. (Stufe A)


## Angabe von Textäquivalenten für Bilder {#provide-text-equivalents}

Bilder können dazu beitragen, das Verständnis für Benutzer mit bestimmten Behinderungen zu verbessern. Für Benutzer von Bildschirmlesehilfen verringern Bilder jedoch die Barrierefreiheit Ihres Formulars, wenn Sie keine Textalternative bereitstellen.

Wenn Sie Bilder verwenden möchten, geben Sie Textbeschreibungen für alle Bild- und Bildfeldobjekte an. Stellen Sie sicher, dass der Text das Objekt und seinen Zweck im Formular beschreibt. Wenn Sie eine Textalternative definieren, liest die Bildschirmlesehilfe diese Alternative, wenn das Bild auftritt. Daher muss für ein Bild, das Informationen enthält, immer eine Textalternative angegeben werden.

Sie können Textbeschreibungen mithilfe der Eigenschaften &quot;QuickInfo&quot;oder &quot;Custom Screen Reader Text&quot;in der Palette &quot;Ein-/Ausgabehilfe&quot;oder über Textfelder, Beschriftungen und Objektnamen bereitstellen, wie in der Option &quot;&quot;auf der Registerkarte &quot;Bindung&quot;angegeben. Abbildung 2 zeigt beispielsweise ein Beispiel eines Bildes, das den Text &quot;Adobe Reader abrufen&quot;enthält. Da eine Bildschirmlesehilfe keinen Reader lesen kann, der Teil eines Bildes ist, sollten Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;für dieses Objekt eine Textalternative in das Feld &quot;Text für benutzerdefinierten Bildschirmtext&quot;einfügen. In den meisten Fällen sollte der Alternativtext mit dem im Bild sichtbaren Text übereinstimmen (siehe Abbildung 2).

![Angeben von Alternativtext für ein Bild mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;](/help/forms/using/assets/image-2.png)

Abbildung 2: **Angeben von Alternativtext für ein Bild mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;**

Beachten Sie beim Festlegen des Alternativtexts Folgendes:
* Wenn das Bildobjekt oder gescannte Bild wichtige Informationen für das Formular enthält, erstellen Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;Text für das Bild, der das Objekt und seinen Zweck beschreibt. Der Text für ein Firmenlogo könnte beispielsweise aus den Worten &quot;Firmenlogo&quot;und dem Namen des Unternehmens bestehen.
* Wenn das Bildobjekt semantische Farbinformationen enthält, fügen Sie dies auch in die Beschreibung ein. Eine Beschreibung einer grünen Ampel könnte beispielsweise &quot;Übertragung erfolgreich&quot;lauten und die Beschreibung einer roten Ampel könnte &quot;Übertragung fehlgeschlagen&quot;lauten.
* Wenn Sie komplexe Grafiken wie Balkendiagramme verwenden, geben Sie die Informationen in einer anderen zugänglichen Version an, z. B. in einer Tabelle oder in einer längeren Textbeschreibung.
* Erstellen Sie keine Textbeschreibungen für statische Bilder, die nur für die Dekoration verwendet werden.
* Verwenden Sie keine gescannten Daten als Hintergrundinformationen. Dies kann vorkommen, wenn ein Designer ein Druckformular scannt und Adobe LiveCycle Designer verwendet, um dem Formular neue Felder hinzuzufügen. Bildschirmlesehilfen können die gescannten Daten in diesem Status nicht erkennen.

Wenn Sie rein dekorative grafische Inhalte in Ihre Formulare aufnehmen, sollten Sie sicherstellen, dass Bildschirmlesehilfen die Präsenz des Bildes nicht ankündigen. Für die meisten Bildschirmlesehilfen kann dies erreicht werden, indem Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;die Eigenschaft &quot;Text im Reader&quot;auf &quot;Ohne&quot;setzen. Wenn Sie dies nicht tun, können einige Bildschirmlesehilfen das Vorhandensein einer Grafik ankündigen, ohne anzugeben, was die Grafik darstellt. Stellen Sie bei dynamischen Bildern wie Bildfeldobjekten sicher, dass die Textalternativen beim Ändern des Bildes ordnungsgemäß aktualisiert werden. Erstellen Sie keine Textbeschreibungen für Bildfeldobjekte, die nur für die Dekoration verwendet werden. Sie können die FormCalc-Skriptsprache verwenden, um einem Bildfeldobjekt dynamisch Textbeschreibungen zuzuweisen. FormCalc ist die Standard-Skriptsprache von Adobe LiveCycle Designer. Betrachten Sie beispielsweise ein Formular mit einem Bildfeld namens ImageField1 und verknüpftem Text im Bildknoten der Laufzeitdaten. Sie können Skripten verwenden, um diesen Text wie folgt in einem entsprechenden Ereignis (z. B. `form:ready`) weiterzugeben:

`ImageField1.assist.toolTip = $record.imagetext.value`

Verwandte Checkpoints
* Abschnitt 508 § 1194.22
   * a) Für jedes nichttextliche Element ist ein Textäquivalent anzugeben (z. B. über &quot;alt&quot;, &quot;longdesc&quot; oder im Elementinhalt).
* WCAG 1.0
   * 1.1 Geben Sie für jedes nichttextliche Element ein Textäquivalent an (z. B. über &quot;alt&quot;, &quot;longdesc&quot;oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIF), Applets und programmatische Objekte, ascii-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Sounds (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audio-Tracks von Videos und Video (P1).
* WCAG 2.0
   * 1.1.1 Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die dem Benutzer präsentiert werden, verfügen über eine Textalternative, die dem entsprechenden Zweck entspricht, mit Ausnahme der unten aufgeführten Situationen. (Stufe A)


## Angabe von angemessenen Beschriftungen für Formularsteuerelemente{#provide-proper-labels}

Die Beschriftung oder Beschriftung eines Formularsteuerelements gibt an, was das Formularsteuerelement darstellen soll. Der Text „Vorname“ weist Benutzende zum Beispiel darauf hin, dass sie ihren Vornamen in ein Textfeld eingeben müssen. Damit Bildschirmlesehilfen darauf zugreifen können, muss die Beschriftung programmgesteuert mit dem Formularsteuerelement verknüpft sein oder das Formularsteuerelement muss mit zusätzlichen Barrierefreiheitsinformationen über die Palette &quot;Ein-/Ausgabehilfe&quot;konfiguriert werden. Es reicht nicht aus, einfach ein Textobjekt neben dem Steuerelement zu platzieren. Für sehbehinderte oder sehbehinderte Benutzer ist es wichtig, dass die Beschriftung neben dem Steuerelement richtig platziert wird. Beide Techniken werden in den folgenden Abschnitten besprochen.

### Festlegen des barrierefreien Beschriftungstextes über die Palette &quot;Ein-/Ausgabehilfe&quot;

Die Beschriftung, die von Benutzern der Sprachausgabe wahrgenommen wird, muss nicht unbedingt mit der visuellen Beschriftung übereinstimmen. In einigen Fällen möchten Sie den Zweck des Steuerelements genauer untersuchen.
Für jedes Feldobjekt in einem Formular kann über die Palette &quot;Ein-/Ausgabehilfe&quot;(siehe Abbildung 3) angegeben werden, was die Bildschirmlesehilfe zur Identifizierung des jeweiligen Formularfelds ankündigt.

Gehen Sie wie folgt vor, um die Palette &quot;Ein-/Ausgabehilfe&quot;zu verwenden:

1. Zeigen Sie die Palette &quot;Ein-/Ausgabehilfe&quot;an, indem Sie &quot;Fenster&quot;> &quot;Ein-/Ausgabehilfe&quot;wählen oder Umschalt+F6 drücken.
1. Wählen Sie ein Objekt im Formular aus. In der Palette werden die Barrierefreiheitseigenschaften des Objekts angezeigt.

![Die Palette &quot;Ein-/Ausgabehilfe&quot;](/help/forms/using/assets/image-3.png)

Abbildung 3: **Palette &quot;Ein-/Ausgabehilfe&quot;**

Wenn das Formular als PDF gespeichert wird, durchsucht LiveCycle Designer das Formular in dieser Reihenfolge nach den Eigenschaften &quot;Benutzerdefinierter Text&quot;, &quot;QuickInfo&quot;, &quot;Beschriftung&quot;und &quot;Name&quot;, um nach Text zu suchen, der von Sprachausgaben gelesen werden kann. Sie können diese Standardreihenfolge außer Kraft setzen, indem Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;die Option &quot;Rangfolge des Readers auf dem Bildschirm&quot;verwenden:

1. Wählen Sie das Objekt im Formularentwurf aus.
1. Klicken Sie auf die Palette &quot;Ein-/Ausgabehilfe&quot;.
1. Wählen Sie eine andere Option &quot;Rangfolge des Readers auf dem Bildschirm&quot;als &quot;Ohne&quot;.

Die folgenden Optionen sind verfügbar:

* **Benutzerdefinierter Reader**, den Sie im Textfeld für den benutzerdefinierten Bildschirmtext der Palette &quot;Ein-/Ausgabehilfe&quot;festlegen. Mit dieser Option können Sie jeden Text angeben, den Sie mithilfe von Hilfstechnologien wie Bildschirmlesehilfen verwenden möchten. Die Verwendung der Beschriftungseinstellung ist in den meisten Fällen am besten. Das Erstellen von benutzerdefiniertem Bildschirmtext sollte nur dann als Option betrachtet werden, wenn die Beschriftung verwendet wird oder ein ToolTip nicht möglich ist.
* **QuickInfo**, die Sie im Feld &quot;QuickInfo&quot;der Palette &quot;Ein-/Ausgabehilfe&quot;festgelegt haben. Bei den meisten Objekten werden QuickInfos zur Laufzeit angezeigt, wenn der Benutzer den Mauszeiger über das Objekt bewegt. QuickInfos werden für einige schreibgeschützte Objekte wie das Barcodeobjekt eines Papierformulars nur angezeigt, wenn eine Bildschirmlesehilfe verwendet wird.
* **Beschriftung**, wodurch LiveCycle Designer die zugehörige (visuelle) Beschriftung des Formularfelds als Bildschirmlesehilfen-Text verwendet.
* **Name**, den Sie im Feld &quot;Name&quot;der Registerkarte &quot;Bindung&quot;festgelegt haben. Beachten Sie, dass dieser Name keine Leerzeichen enthalten darf.
* **None** , wodurch das Objekt keinen Namen hat. Dies wird nie für Formularsteuerelemente empfohlen.

Beachten Sie Folgendes bei der Verwendung der Palette &quot;Ein-/Ausgabehilfe&quot;für die Beschriftung von Formularsteuerelementen:

* Wenn die Beschriftung des Formularsteuerelements das Steuerelement ordnungsgemäß beschreibt, ist es für Sprachausgaben verfügbar. Lassen Sie in diesem Fall entweder die Felder &quot;Benutzerdefinierter Reader&quot;und &quot;QuickInfo&quot;in der Palette &quot;Ein-/Ausgabehilfe&quot;leer oder ändern Sie die Rangfolge des Bildschirms in &quot;Beschriftung&quot;.
* Beim Targeting von Bildschirmlesehilfen ist es nicht sinnvoll, für dasselbe Formularsteuerelement verschiedene Textbeschreibungen anzugeben, da nur eines verwendet wird: Das erste nicht leere Feld in der Rangfolge des Screens-Readers. Beispielsweise gibt es keinen Grund, sowohl benutzerdefinierten Text als auch QuickInfo-Text für eine Bildschirmlesehilfe anzugeben.
* Standardmäßig liest die Bildschirmlesehilfe die Beschriftung, wenn im Feld &quot;QuickInfo&quot;oder im Feld &quot;Reader für benutzerdefinierten Bildschirm&quot;nichts angegeben ist.
* Verwenden Sie nicht die Palette &quot;Ein-/Ausgabehilfe&quot;, um Beschreibungen für unsichtbare Felder oder Bereiche zu erstellen.
* Wenn Sie eine Beschreibung mithilfe der Optionen &quot;QuickInfo&quot;oder &quot;Benutzerdefinierter Bildschirmtext&quot;erstellen müssen, fügen Sie immer die Beschriftung ein, die im Formular sichtbar ist, es sei denn, die sichtbare Beschriftung ist nicht aussagekräftig, z. B. wenn die Beschriftung selbst abgekürzt wird. Dies hilft Benutzern der Bildschirmlesehilfe, effektiv mit anderen Benutzern über Benutzeroberflächenelemente zu kommunizieren. Diese unterschiedlichen Benutzergruppen haben Schwierigkeiten, dasselbe Benutzeroberflächen-Element zu identifizieren, wenn sich der Beschriftungstext von der QuickInfo oder dem Text des benutzerdefinierten Readers unterscheidet.
* Bei Kontrollkästchen und Dropdown-Listensteuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe an, welche Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text Sie für das Objekt angeben. Wenn Sie die Spaltenüberschrift für den Alternativtext für diese Objekte verwenden möchten, wenn Sie sie in einer Tabelle platzieren, dürfen Sie keine Beschriftung, QuickInfo oder benutzerdefinierten Text für die Bildschirmlesehilfe angeben.
* Wenn das Steuerelement zusätzliche Anweisungen erfordert, stellen Sie sicher, dass diese ebenfalls in der Textalternative enthalten sind. Geben Sie genügend gesprochene Informationen an, damit Benutzer wissen können, welche Eingabe erwartet wird und wie das Feld korrekt ausgefüllt werden soll. Überfordern Sie Benutzer jedoch nicht mit redundanten Informationen.
* Geben Sie keine unnötigen Informationen an, die beschreiben, wie Steuerelemente verwendet werden. Lassen Sie dies von den Hilfstechnologien des Benutzers handhaben. Benutzer können die Ausführlichkeit entsprechend ihren Komfort-Levels konfigurieren.

Abbildung 4 zeigt ein Beispiel für ein Textfeld mit einer visuellen Beschriftung, die für einige Benutzer der Bildschirmlesehilfe möglicherweise unklar ist. In diesem Beispiel ist &quot;Reader des benutzerdefinierten Bildschirms&quot;auf &quot;Anzahl der Seiten&quot;und &quot;Rangfolge des Readers&quot;auf &quot;Benutzerdefinierter &quot;eingestellt. Daher wird der tatsächliche (visuelle) Beschriftungstext (&quot;# der Seiten&quot;) nicht von der Bildschirmlesehilfe verwendet. Alternativ konnte ein QuickInfo angegeben werden.

![Festlegen des Reader-Textes für benutzerdefinierte Bildschirme, wenn die sichtbare Beschriftung unzureichend ist](/help/forms/using/assets/image-4.png)

Abbildung 4: **Festlegen des Reader-Textes für benutzerdefinierte Bildschirme bei unzureichender sichtbarer Beschriftung**

### Beschriftung von Optionsfeldern

Wenn ein sehbehinderter Benutzer mit der Tabulatortaste in ein Optionsfeld wechselt, muss die Bildschirmlesehilfe zwei Dinge lesen:
* Angabe des Zwecks der Gruppe von Optionsfeldern
* Eine aussagekräftige Beschriftung für jedes Optionsfeld
So machen Sie Optionsfelder über Schaltflächenbeschriftungen zugänglich:
   1. Wählen Sie in der Palette &quot;Hierarchie&quot;die Ausschlussgruppe aus.
   1. Klicken Sie auf die Palette &quot;Ein-/Ausgabehilfe&quot;und geben Sie im Feld &quot;Reader des benutzerdefinierten Bildschirms&quot;den für die Gruppe zu lesenden  ein. Geben Sie beispielsweise für eine Ausschlussgruppe, die Optionen für die Zahlung mit verschiedenen Kreditkarten angibt, Zahlungsmethode auswählen ein.
   1. Wenn die Beschriftungen für jedes Optionsfeld Text enthalten, der beim Aussprechen durch eine Bildschirmlesehilfe aussagekräftig ist, wählen Sie in der Palette &quot;Objekt&quot;die Registerkarte &quot;Bindung&quot;aus und deaktivieren Sie die Option &quot;Elementwert angeben&quot;.

  So machen Sie Optionsfelder mit einem angegebenen Elementwert barrierefrei:
   1. Wählen Sie in der Palette &quot;Hierarchie&quot;die Ausschlussgruppe aus.
   1. Klicken Sie auf die Palette &quot;Ein-/Ausgabehilfe&quot;und geben Sie im Feld &quot;Reader des benutzerdefinierten Bildschirms&quot;den für die Gruppe zu lesenden  ein. Geben Sie beispielsweise für eine Ausschlussgruppe, die Optionen für die Zahlung mit verschiedenen Kreditkarten angibt, Zahlungsmethode auswählen ein.
   1. Wählen Sie in der Palette &quot;Hierarchie&quot;das erste Optionsfeld in der Gruppe aus.
   1. Klicken Sie in der Palette &quot;Objekt&quot;auf die Registerkarte &quot;Feld&quot;. Doppelklicken Sie im Bereich &quot;Element&quot;auf das Element und geben Sie einen aussagekräftigen Wert für das ausgewählte Optionsfeld ein. Beispielsweise können Sie für die erste Schaltfläche in einer Gruppe von Zahlungsmethoden Cash (Bargeld) eingeben.
   1. Wiederholen Sie die Schritte 3 und 4 für jedes Optionsfeld in der Ausschlussgruppe.

### Beschriften benutzerdefinierter Steuerelemente

Es wird dringend empfohlen, Standardkomponenten anstelle benutzerdefinierter Komponenten zu verwenden, da sie der Hilfstechnologie standardmäßig die richtigen Hinweise und Informationen liefern. Wenn jedoch benutzerdefinierte Steuerelemente verwendet werden, beachten Sie Folgendes:
* Ankündigung des Status von Kontrollkästchen und Optionsfeldern.
* In Listenfeldern und Dropdown-Listen können Sie das in der Liste ausgewählte Standardelement ankündigen. Stellen Sie sicher, dass der Benutzer mithilfe der Nach-oben- und Nach-unten-Taste durch die Listenelemente navigieren kann. Beachten Sie, dass durch Drücken der Tabulatortaste oder der Eingabetaste das Element in der Liste ausgewählt wird. Mithilfe von Skripten können Sie festlegen, dass das Change -Ereignis des Objekts angibt, welches Element aus der Liste ausgewählt ist.
* Informieren Sie die Benutzer über alle speziellen Tastenanschläge, die sie für eine Funktion benötigen, z. B. durch Drücken der Leertaste, um eine Schaltfläche auszuwählen, oder über die Nach-unten-Taste, um ein Element aus einem Listenfeld auszuwählen.

### Ordnungsgemäße Positionierung der Beschriftung eines Steuerelements

Die Platzierung einer Beschriftung ist wichtig, da Benutzer erwarten, dass sie neben dem Steuerelement gefunden wird. Für Benutzer mit Bildschirmvergrößerung ist dies umso wichtiger, als sie möglicherweise nicht in der Lage sind, sowohl das Steuerelement als auch die Beschriftung gleichzeitig anzuzeigen, wenn sie zu weit voneinander entfernt sind.

Wenn Sie ein Objekt erstellen, positioniert LiveCycle Designer die Beschriftung automatisch, wie durch den Objekttyp angegeben. Die Beschriftungen von Optionsfeldern werden beispielsweise rechts platziert. Diese Standardplatzierung ist immer der beste Speicherort für eine barrierefreie Beschriftung. Wenn Sie die Position des Beschriftungstextes ändern müssen, führen Sie die folgenden Schritte aus:
1. Wählen Sie das Objekt aus, indem Sie den Fokus darauf verschieben.
1. Wählen Sie in der Palette &quot;Layout&quot;unter der Option &quot;Position&quot;im Abschnitt &quot;Beschriftung&quot;unten in der Palette die Position der Objektbeschriftung aus.

Das Beispiel in Abbildung 5 zeigt ein Textfeld mit einer Beschriftung darüber. Die Position in der Palette &quot;Layout&quot;ist auf &quot;Oben&quot;eingestellt. Die Standardposition der Beschriftung befindet sich links neben dem Textfeld.

![Ändern der Positionierung von Beschriftungen mithilfe der Palette &quot;Layout&quot;](/help/forms/using/assets/image-5.png)

Abbildung 5: **Ändern der Positionierung von Beschriftungen mithilfe der Palette &quot;Layout&quot;**

Die folgende Tabelle bietet einen Überblick über die Platzierungsregeln für häufig verwendete Steuerelemente.

| Kontrolltyp | Platzierungsregeln |
|--------------|-----------------|
| Texteingabe (einschließlich Felder für Datum, Uhrzeit und Kennwort) | Platzieren Sie die Beschriftung links neben dem Steuerelement (Standard). Ist dies nicht möglich, platzieren Sie es direkt oberhalb oder unterhalb davon. Beschriftungen sollten für Benutzer mit erhöhter Vergrößerung in der Nähe des Kontrollelements positioniert werden, damit die Beschriftung und Kontrolle in der vergrößerten Ansicht mit höherer Wahrscheinlichkeit zusammen angezeigt werden. |
| Kontrollkästchen | Platzieren Sie die Beschriftung rechts neben dem Kontrollkästchen (Standard). Bei Kontrollkästchen-Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe an, welche Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text Sie für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für ein Kontrollkästchen in einer Tabelle verwenden möchten, dürfen Sie keine Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text angeben. |
| Optionsfeldgruppe | Erstellen Sie einen sichtbaren Titel für die Optionsfeld-Gruppe, indem Sie ein statisches Textelement erstellen und links von oder über der Gruppe platzieren. Platzieren Sie die Beschriftung für jedes einzelne Optionsfeld rechts (Standard). |
| Dropdown-Liste | Platzieren Sie die Beschriftung links neben dem Objekt (Standard). Ist dies nicht möglich, platzieren Sie es direkt darüber. Bei Dropdown-Listen-Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe die Beschriftung, QuickInfo oder den benutzerdefinierten Bildschirmlesehilfen-Text an, die Sie für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für diese Objekte in einer Tabelle verwenden möchten, dürfen Sie keine Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text angeben. |
| Listenfeld | Die Beschriftung wird bei der Erstellung standardmäßig über dem Listenfeld positioniert. |
| Schaltfläche | Die Beschriftung wird automatisch auf die Schaltfläche gesetzt und muss nicht manuell positioniert werden. Stellen Sie sicher, dass der Zweck der Schaltfläche durch den Beschriftungstext richtig beschrieben wird. |


### Dynamisches Ausfüllen eines QuickInfos oder benutzerspezifischen Bildschirmtext-Readers

Sie können auch die Textalternative eines Formularsteuerelements, z. B. die QuickInfo, dynamisch mit einem Wert aus einer Datenquelle ausfüllen. Sie können beispielsweise einen benutzerdefinierten QuickInfo für ein Objekt anzeigen, das in französischer Sprache ist.
Das Schema, zu dem Sie eine Verbindung herstellen, könnte die folgende Definition für eine QuickInfo enthalten:


```html
<form>
<tooltip dp_tt="tooltip1"/>
</form>
```


Die Datendatei, zu der Sie einen Verweis erstellen, könnte die folgende Definition für eine QuickInfo enthalten:

```html
<form>
<tooltip dp_tt="Quantité - Entrez un nombre inférieur ou égal à 100."/>
</form>
```

1. Klicken Sie in der Palette &quot;Objektbibliothek&quot;auf die Kategorie &quot;Standard&quot;und ziehen Sie ein Objekt auf den Formularentwurf. Fügen Sie beispielsweise ein Textfeldobjekt ein.
1. (Optional) Klicken Sie in der Palette &quot;Objekt&quot;auf die Registerkarte &quot;Feld&quot;und geben Sie im Feld &quot;Beschriftung&quot;eine Beschriftung für das Objekt ein. Geben Sie beispielsweise Quantité ein.
1. Klicken Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;auf die aktive Beschriftung QuickInfo .
1. Wählen Sie die Datenverbindung aus.
1. Klicken Sie auf das Dreieck neben dem Feld &quot;Bindung&quot;und wählen Sie eine Bindung aus. Wählen Sie beispielsweise tooltip > @dp_tt aus.

Die folgende Zeichenfolge wird im Feld &quot;Bindung&quot;angezeigt: $record.tooltip.dp_tt Tip: Sie können diese Zeichenfolge in das Feld &quot;Elemente&quot;eingeben, anstatt sie auszuwählen.
1. Klicken Sie auf „OK“.
1. Zeigen Sie das Formular auf der Registerkarte Vorschau-PDF an.

### Linktext bereitstellen

Benutzer von Hilfstechnologien können unterschiedliche Methoden zum Lesen verknüpfter Texte haben. Beispielsweise verwenden Benutzer von Bildschirmlesehilfen häufig eine Liste mit Links, wie in Abbildung 6 dargestellt, um die verfügbaren Links auf einer Seite schnell zu überprüfen.

![Das Dialogfeld &quot;JAWS-Link-Liste&quot;](/help/forms/using/assets/image-6.png)

Abbildung 6: **Dialogfeld &quot;JAWS-Link-Liste&quot;**

Aus diesem Grund müssen Links selbst beschreiben, d. h. ihre Bedeutung sollte nicht von ihrem Kontext (dem umliegenden Text) abhängen. Beispielsweise könnte das Wort &quot;Hier klicken&quot;das eigentliche Link-Element im Satz &quot;Hier klicken, um unser Antragsformular herunterzuladen&quot;sein. Ein solcher Link wäre beim Durchlesen einer Linkliste schwierig zu verstehen, insbesondere wenn mehrere Links denselben Text enthalten.

Achten Sie bei der Verwendung von Links in Ihrem Formular darauf, dass jeder Link seinen Zweck ordnungsgemäß beschreibt, ohne dass dies vom umliegenden Text oder von der Position auf der Seite abhängt. Anstatt beispielsweise einen Satz wie &quot;Click Here&quot;als Link-Text zu verwenden, verwenden Sie &quot;Download application form&quot;als Link-Text.

**Verwandte Checkpoints**

* Abschnitt 508 § 1194.21
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare ermöglicht das Formular Personen, die Hilfstechnologien nutzen, den Zugriff auf die Informationen, Feldelemente und Funktionen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Richtungen und Hinweise.
* Abschnitt 508 § 1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugang zu den Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars, einschließlich aller Richtungen und Hinweise, erforderlich sind.
* WCAG 1.0
   * 12.4 Beschriftungen explizit mit ihren Steuerelementen verknüpfen (P2).
   * 13.1 Identifizieren Sie eindeutig die Zielgruppe jedes Links (P2).
* WCAG 2.0
   * 1.1.1 Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die dem Benutzer präsentiert werden, verfügen über eine Textalternative, die dem entsprechenden Zweck entspricht, mit Ausnahme der unten aufgeführten Situationen. (Stufe A)
   * 2.4.6 Überschriften und Beschriftungen: Überschriften und Beschriftungen beschreiben ein Thema oder einen Zweck. (Stufe AA)
   * 3.2.4 Konsistente Erkennung: Komponenten, die innerhalb eines Satzes von Webseiten dieselbe Funktionalität aufweisen, werden konsistent identifiziert. (Stufe AA)
   * 3.3.2 Beschriftungen oder Anweisungen: Beschriftungen oder Anweisungen werden bereitgestellt, wenn der Inhalt Benutzereingaben erfordert. (Stufe A)
   * 4.1.2 Name, Rolle, Wert: Für alle Komponenten der Benutzeroberfläche (einschließlich, aber nicht beschränkt auf: Formularelemente, Links und Komponenten, die von Skripten generiert werden) kann der Name und die Rolle programmgesteuert bestimmt werden. Status, Eigenschaften und Werte, die vom Benutzer festgelegt werden können, können programmgesteuert festgelegt werden. Die Benachrichtigung über Änderungen an diesen Elementen steht Benutzeragenten zur Verfügung, einschließlich Hilfstechnologien. (Stufe A)


## Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind. {#ensure-reading-tab-order}

Die Sicherstellung einer sinnvollen Leserichtung ist bei der Erstellung von Formularen sehr wichtig, die für Benutzer mit Sehbehinderung oder anderen Behinderungen zugänglich sind. Diese Benutzer verwenden normalerweise keine Maus, um durch ein Formular zu navigieren, sodass sie von der Tastatur abhängig sind. Die Leserichtung bestimmt die Reihenfolge, in der Benutzer der Sprachausgabe das Formular durchlesen. Darüber hinaus können Benutzer mithilfe der Tabulatortasten schnell von einem interaktiven Formularsteuerelement zum nächsten wechseln. Eine logische Tab-Reihenfolge stellt sicher, dass sie Zugriff auf alle Felder im Formular haben und dass sie im Formular auf eine sinnvolle und effiziente Weise navigieren können.

Die Leserichtung des Formulars umfasst alle statischen Objekte (z. B. Text und Bilder) und Feldobjekte, aber nur die interaktiven Formularsteuerelemente sind Teil der Registerkartenreihenfolge.

>[!NOTE]
> In vielen Fällen hängt die Tab-Reihenfolge eng mit der Leserichtung zusammen. Der Einfachheit halber wird der Begriff &quot;Tab-Reihenfolge&quot;anstelle von &quot;Tab- oder Leserichtung&quot;in diesem Handbuch verwendet.

### Die standardmäßige Registerkartenreihenfolge in LiveCycle Designer forms

Die standardmäßige Tab-Reihenfolge wird automatisch erstellt, wenn Sie Ihr Formular als getaggtes PDF speichern. Zunächst wird die Tab-Reihenfolge in einem Formular anhand der lokalen Position der Objekte mithilfe der folgenden Regeln bestimmt:

* Alle Objekte werden von links nach rechts und von oben nach unten (lokale Reihenfolge) angeordnet, beginnend mit der linken oberen Ecke des Formulars.
* Alle von Ihnen erstellten Teilformulare werden als eigenständige Einheiten behandelt und von links nach rechts sowie von oben nach unten navigiert. Wenn sich zwei Teilformulare nebeneinander befinden, die beide Objekte enthalten, navigiert die Leserichtung durch alle Objekte im ersten Teilformular, bevor zum nächsten Teilformular gewechselt wird.

Bei einfachen Formularen (d. h. bei Formularen mit einem Layout von links nach rechts und von oben nach unten) ist die standardmäßige Registerkartenreihenfolge in der Regel korrekt. Um dies zu überprüfen, sollten Sie die standardmäßige Tab-Reihenfolge vor der Veröffentlichung des Formulars überprüfen. Sie können die Tab-Reihenfolge mit einer der folgenden Methoden sichtbar machen:

* Wählen Sie &quot;Ansicht&quot;> &quot;Tab-Reihenfolge anzeigen&quot;.
* Klicken Sie in der Palette &quot;Tab-Reihenfolge&quot;auf &quot;Reihenfolge anzeigen&quot;.

Alle Objekte werden mit einer Zahl in der oberen rechten Ecke angezeigt, die die Position des Objekts in der standardmäßigen Tab-Reihenfolge angibt. Die interaktiven Objekte in dieser Sequenz bilden die Tab-Reihenfolge. Abbildung 7 zeigt die Visualisierung der Leserichtung eines einfachen Formulars.

![Visualisierung der standardmäßigen Leserichtung für ein typisches Bestellformular](/help/forms/using/assets/image-7.png)

Abbildung 7: **Visualisierung der standardmäßigen Leserichtung für ein typisches Bestellformular**

Jede Registerreihenfolge wird farbig dargestellt. Die Formen haben die folgende Bedeutung:
* Graue Kreise (#1 und #4) werden für Objekte im Inhaltsbereich verwendet.
* Grüne Kreise (#6 und #7) werden für Masterseitenobjekte verwendet.
* Lavenerquadrate (#2 und #3) werden für Objekte in einem Fragment verwendet.

Sie können festlegen, dass nur interaktive Formularsteuerelemente (die die Registerkartenreihenfolge bilden) oder alle Objekte in der Leserichtung angezeigt werden (einschließlich statischer Objekte wie Text und Bilder). Um diese Voreinstellung zu ändern, wählen Sie &quot;Extras&quot;> &quot;Optionen&quot;> &quot;Tab-Reihenfolge&quot;und dann &quot;Nur Tab-Reihenfolge für Felder anzeigen&quot;.

In einem komplexen Formular kann es schwierig sein zu erkennen, wie die Tab-Reihenfolge von einem Objekt zum nächsten verläuft. Sie können visuelle Hilfen verwenden, um den Tab-Fluss im Formular anzuzeigen. Wenn die visuellen Hilfen aktiviert sind und Sie den Mauszeiger über das Objekt bewegen, zeigen die blauen Pfeile den Tab-Fluss für die beiden vorangehenden und zwei nachfolgenden Objekte in der Tab-Reihenfolge an (siehe Abbildung 8).

![Visuelle Hilfen zum Hervorheben der Registerkartenreihenfolge](/help/forms/using/assets/image-8.png)

Abbildung 8: **Sichtbare Hilfsmittel markieren die Tab-Reihenfolge**

Verwenden Sie die folgenden Methoden, um die visuellen Hilfsmittel zu aktivieren:
* Wählen Sie &quot;Extras&quot;> &quot;Optionen&quot;> &quot;Tab-Reihenfolge&quot;und wählen Sie im Bereich &quot;Tab-Reihenfolge&quot;die Option &quot;Zusätzliche visuelle Hilfen für Tab-Reihenfolge anzeigen&quot;.
* Wählen Sie im Menü der Palette &quot;Tab-Reihenfolge&quot;die Option &quot;Visuelle Hilfen anzeigen&quot;.

### Verwenden der Position, um die standardmäßige Tab-Reihenfolge zu beeinflussen

Um die standardmäßige Tab-Reihenfolge zu beeinflussen, können Sie die Koordinaten eines Objekts ändern, indem Sie es an eine andere Position verschieben. Beispiel: In Abbildung 9 tritt das Feld Produktname in der Tab-Reihenfolge vor dem Feld Menge auf. Um diese Reihenfolge zu ändern, können Sie das Feld Produktname so verschieben, dass es unter oder rechts vom Feld Menge platziert wird.

![Die standardmäßige Registerkartenreihenfolge ist von links nach rechts](/help/forms/using/assets/image-9.png)

Abbildung 9: **Die standardmäßige Registerkartenreihenfolge ist von links nach rechts**

Sie können die Position eines Objekts wie folgt ändern:
* Ziehen Sie es mit der Maus
* Wählen Sie es aus und verschieben Sie es mithilfe der Tastaturpfeile.

>[!NOTE]
> Es kann hilfreich sein, die Objektausrichtung beizubehalten, indem Sie &quot;Ansicht&quot;> &quot;Am Raster ausrichten&quot;wählen.

Mithilfe der Palette &quot;Layout&quot;können Sie die Koordinaten eines Objekts präziser ändern (siehe Abbildung 10). In dieser Palette können Sie die X- und Y-Koordinaten sowie die Breite und Höhe des Objekts angeben.

![Verwenden von Koordinaten zum präzisen Positionieren eines Objekts in der Palette &quot;Layout&quot;](/help/forms/using/assets/image-10.png)

Abbildung 10: **Verwenden von Koordinaten zum präzisen Positionieren eines Objekts in der Palette &quot;Layout&quot;**

>[!NOTE]
> Wenn die Beschriftung und das Steuerelement nicht zusammengeführt werden, ist die Position der Beschriftung eines Formularsteuerelements unabhängig von der Reihenfolge, in der Bildschirmlesehilfen das Objekt und seine Elemente lesen. Weitere Informationen zu Beschriftungen finden Sie in diesem Handbuch im Abschnitt 2.5 Angeben von richtigen Beschriftungen für Formularsteuerelemente.

### Teilformulare verwenden, um die standardmäßige Tab-Reihenfolge zu beeinflussen

Wie oben erwähnt, können Sie mit Teilformularen Gruppen von Objekten einfügen, die über eine eigene Registerkartenreihenfolge verfügen. Sie können ein Teilformular wie folgt erstellen:
* Wählen Sie &quot;Einfügen&quot;> &quot;Standard&quot;> &quot;Teilformular&quot;.
* Wählen Sie die Objekte in der Palette &quot;Hierarchie&quot;aus und gruppieren Sie sie in einem Teilformular, indem Sie &quot;Einfügen&quot;> &quot;In Teilformular aufnehmen&quot;wählen.
* Wählen Sie die Objekte im eigentlichen Formular aus, klicken Sie mit der rechten Maustaste auf die Auswahl und wählen Sie &quot;Umschließen in Teilformular&quot;.

Wenn zwei Teilformulare, die Feldobjekte enthalten, nebeneinander positioniert sind, durchläuft die Tab-Reihenfolge die Felder im ersten Teilformular, bevor der Wechsel zum nächsten erfolgt. Dies wird in Abbildung 11 veranschaulicht, in der zwei Teilformulare verwendet werden, um eine spaltenbasierte standardmäßige Registerkartenreihenfolge zu erstellen.

![Standardmäßige Tab-Reihenfolge mit Teilformularen](/help/forms/using/assets/image-11.png)

Abbildung 11: **Standardtabulatorreihenfolge mit Teilformularen**

Teilformulare, Optionsfelder und Inhaltsbereiche wirken sich zusammen mit der vertikalen Position der Objekte auf einer Seite und ihrer Masterseite auf die Tab-Reihenfolge aus.

### Erstellen einer benutzerdefinierten Tab-Reihenfolge mithilfe der Palette &quot;Tab-Reihenfolge&quot;

Sie können die standardmäßige Tab-Reihenfolge ändern, wenn Sie eine andere Reihenfolge im Formular benötigen und die Änderung nicht durch Positionieren oder Gruppieren in Teilformularen erreicht werden kann. Um die standardmäßige Tab-Reihenfolge zu ändern, können Sie über die Palette &quot;Tab-Reihenfolge&quot;eine benutzerdefinierte Tab-Reihenfolge erstellen.
Über die Palette &quot;Tab-Reihenfolge&quot;(siehe Abbildung 12) können Sie die Reihenfolge überprüfen und ändern, in der Objekte in Ihrem Formular mithilfe von Hilfstechnologien gelesen und durch die Tabulatortaste des Benutzers navigiert werden.

![Palette &quot;Tab-Reihenfolge&quot;](/help/forms/using/assets/image-12.png)

Abbildung 12: **Palette &quot;Tab-Reihenfolge&quot;**

Die Palette &quot;Tab-Reihenfolge&quot;bietet eine alternative Ansicht der Tab-Reihenfolge im Formular. Es zeigt alle Objekte im Formular als nummerierte Liste an, wobei jede Zahl die Position des Objekts im Tab-Fluss darstellt.
Um die Palette &quot;Tab-Reihenfolge&quot;zu öffnen, wählen Sie &quot;Fenster&quot;> &quot;Tab-Reihenfolge&quot;.


Die Palette &quot;Tab-Reihenfolge&quot;enthält die folgenden visuellen Markierungen:
* Eine graue Leiste markiert jede Seite des Formulars. Die Tab-Reihenfolge auf jeder Seite beginnt mit der Zahl 1.
* Der Buchstabe M in einem grünen Kreis zeigt Masterseitenobjekte an (nur sichtbar, wenn das Formular auf der Registerkarte &quot;Designansicht&quot;angezeigt wird).
* Ein Zahlenbereich zeigt Objekte in einem Fragment an.
* Ein gelber Hintergrund kennzeichnet das aktuell ausgewählte Element.
* Ein Sperrsymbol neben dem ersten Objekt auf der Seite zeigt an, dass das Objekt nicht in der Tab-Reihenfolge verschoben werden kann (nur sichtbar, wenn das Formular auf der Registerkarte &quot;Masterseiten&quot;angezeigt wird).

Die Liste zeigt dieselben Nummern für die Registerkartenreihenfolge an wie die Zahlen, die im Formular selbst angezeigt werden, wenn Sie &quot;Ansicht&quot;> &quot;Tab-Reihenfolge anzeigen&quot;wählen. Sie können die Position eines Objekts in der Tab-Reihenfolge ändern, indem Sie das Objekt in der Liste der Palette &quot;Tab-Reihenfolge&quot;nach oben oder unten verschieben. Sie können ein einzelnes Objekt oder eine Gruppe von Objekten verschieben. Dies kann mit einer der folgenden Methoden erreicht werden:

* Ziehen Sie das ausgewählte Objekt in der Liste nach oben oder unten und platzieren Sie es an der gewünschten Position. Ein schwarzer Griff markiert Ihre aktuelle Position in der Liste, bevor Sie das Objekt platzieren.
* Klicken Sie in der Palette &quot;Tab-Reihenfolge&quot;auf die Pfeilschaltflächen nach oben oder unten, bis sich das ausgewählte Objekt an der richtigen Position befindet. Drücken Sie alternativ Strg+Nach-oben-Taste oder Strg+Nach-unten-Taste.
* Wählen Sie im Menü der Palette &quot;Tab-Reihenfolge&quot;die Option &quot;Nach oben&quot;oder &quot;Nach unten&quot;.
* Klicken Sie in der Liste der Palette &quot;Tab-Reihenfolge&quot;auf das ausgewählte Objekt (oder wählen Sie es aus und drücken Sie F2), damit die Nummer neben dem Objektnamen bearbeitbar wird. Geben Sie dann die Nummer ein, die die neue Position des Objekts in der Tab-Reihenfolge angibt, und drücken Sie die Eingabetaste.
* Wählen Sie im Menü der Palette &quot;Tab-Reihenfolge&quot;die Option &quot;Kopieren&quot;, wählen Sie in der Liste das Objekt aus, über dem das zu verschiebende Objekt platziert werden soll, und wählen Sie dann im Menü die Option &quot;Einfügen&quot;.

Wenn Sie das Objekt an eine neue Position in der Reihenfolge verschieben, ordnet LiveCycle Designer die Ordnungszahlen der Registerkarte neu zu. Obwohl die Tab-Reihenfolge der Objekte auf einer Masterseite auf der Registerkarte &quot;Designansicht&quot;angezeigt wird, können Sie die Reihenfolge für diese Objekte nur auf der Registerkarte &quot;Masterseiten&quot;ändern. Wenn Sie Fragmentverweise in Ihrem Formular verwenden, ist die Registerkartenreihenfolge in einem Fragment sichtbar, wenn Sie die Reihenfolge für das Formular anzeigen. Um die Tab-Reihenfolge in einem Fragment zu ändern, müssen Sie die Quelldatei des Fragments zur Bearbeitung öffnen, die Änderung vornehmen und die Datei speichern. Alle Formulare, die dieses Fragment verwenden, sind von dieser Änderung betroffen.

Wenn Sie sich dafür entscheiden, die angepasste Tab-Reihenfolge in Ihrem Formular nicht zu übernehmen, können Sie schnell zur automatischen (standardmäßigen) Tab-Reihenfolge zurückkehren, indem Sie die folgenden Schritte ausführen (dabei gehen alle Änderungen an der Tab-Reihenfolge verloren):
1. Wählen Sie in der Palette &quot;Tab-Reihenfolge&quot;die Option &quot;Automatisch&quot;aus.
1. Klicken Sie im angezeigten Meldungsfeld auf Ja , um die Entfernung der benutzerdefinierten Tab-Reihenfolge zu bestätigen.

**Verwandte Checkpoints**
* Abschnitt 508 § 1194.21
   * (a) Wenn Software für die Ausführung auf einem System mit Tastatur entwickelt wird, müssen Produktfunktionen von einer Tastatur aus ausführbar sein, wobei die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell erkennbar ist.
* WCAG 1.0
   * 9.2 Stellen Sie sicher, dass jedes Element, das über eine eigene Schnittstelle verfügt, geräteunabhängig betrieben werden kann.
* WCAG 2.0
   * 1.3.2 Bedeutungstragende Reihenfolge: Wenn die Reihenfolge, in der Inhalte präsentiert werden, ihre Bedeutung beeinflusst, kann programmatisch eine korrekte Lesesequenz bestimmt werden. (Stufe A)
   * 2.1.1 Tastatur: Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für einzelne Tastenanschläge bestimmte Zeitpunkte erforderlich sind, es sei denn, die zugrunde liegende Funktion erfordert Eingaben, die vom Pfad der Bewegung des Benutzers und nicht nur von den Endpunkten abhängen. (Stufe A)
   * 2.1.3 Tastatur (keine Ausnahme): Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für einzelne Tastenanschläge bestimmte Zeiteinteilung erforderlich ist. (Stufe AAA)
   * 2.4.3 Fokus-Reihenfolge: Wenn eine Webseite sequenziell navigiert werden kann und die Navigationssequenzen die Bedeutung oder den Betrieb beeinflussen, erhalten fokussierbare Komponenten den Fokus in einer Reihenfolge, die Bedeutung und Bedienbarkeit bewahrt. (Stufe A)


## Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind{#ensure-keyboard-accessible}

Benutzer müssen das Formular vollständig mit der Tastatur oder einem gleichwertigen alternativen Eingabegerät ausfüllen können. Benutzer mit eingeschränkter Mobilität oder Sehfähigkeit haben möglicherweise keine andere Wahl, als die Tastatur zu verwenden, und viele Benutzer, die eine Maus verwenden können, bevorzugen einfach die Eingabe über die Tastatur. Indem Sie verschiedene Eingabemethoden zulassen, erstellen Sie nicht nur barrierefreie Formulare, sondern auch Formulare, die den Vorlieben aller Benutzer besser entsprechen.

In LiveCycle Designer können Sie am einfachsten sicherstellen, dass Ihre Steuerelemente über die Tastatur zugänglich sind, indem Sie die auf der Registerkarte &quot;Allgemein&quot;der Palette &quot;Objektbibliothek&quot;aufgelisteten Steuerelemente verwenden. Diese Steuerelemente reagieren standardmäßig sowohl auf die Maus- als auch auf die Tastatureingabe. Weitere Informationen finden Sie im Abschnitt 2.3 Die richtigen Steuerelemente in diesem Handbuch auswählen .

Ein weiterer wichtiger Aspekt der Barrierefreiheit der Tastatur besteht darin, sicherzustellen, dass jedes interaktive Element Teil der Registerkartenreihenfolge des Formulars ist. Dadurch kann der Benutzer den Cursor mit den Tabulator- und Umschalt-+Tabulatortasten vorwärts und rückwärts durch das Formular bewegen. Achten Sie darauf, eine logische Tab-Reihenfolge festzulegen, die alle Felder und Schaltflächen enthält. Weitere Informationen finden Sie in Abschnitt 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge in diesem Handbuch korrekt sind.

Schließlich muss sichergestellt werden, dass das skriptgesteuerte Verhalten auch über die Tastatur zugänglich ist und nicht von gerätespezifischen Ereignissen abhängig ist. Das Mausereignis MouseEnter kann beispielsweise nicht über die Tastatur ausgeführt werden. Außerdem dürfen solche Ereignishandler die Barrierefreiheit der Tastatur nicht beeinträchtigen. Achten Sie beispielsweise darauf, dass in Dropdown-Listen oder Listenfeldern verwendete Änderungs-Ereignisse keine unerwarteten Aktionen Trigger werden.

**Verwandte Checkpoints**
* Abschnitt 508 § 1194.21
   * (a) Wenn Software für die Ausführung auf einem System mit Tastatur entwickelt wird, müssen Produktfunktionen von einer Tastatur aus ausführbar sein, wobei die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell erkennbar ist.
* WCAG 1.0
   * 6.4 Stellen Sie bei Skripten und Applets sicher, dass Ereignishandler geräteunabhängig (P2) eingegeben werden.
   * 9.2 Stellen Sie sicher, dass jedes Element, das über eine eigene Schnittstelle verfügt, geräteunabhängig betrieben werden kann (P2).
   * 9.3 Geben Sie für Skripte logische Ereignishandler anstelle geräteabhängiger Ereignishandler (P2) an.
* WCAG 2.0
   * 2.1.1 Tastatur: Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für einzelne Tastenanschläge bestimmte Zeitpunkte erforderlich sind, es sei denn, die zugrunde liegende Funktion erfordert Eingaben, die vom Pfad der Bewegung des Benutzers und nicht nur von den Endpunkten abhängen. (Stufe A)
   * 2.1.2 Keine Tastaturfalle: Wenn der Tastaturfokus über eine Tastaturschnittstelle auf eine Komponente der Seite verschoben werden kann, kann der Fokus von dieser Komponente weg bewegt werden, indem nur eine Tastaturschnittstelle verwendet wird. Wenn es mehr als unveränderte Pfeil- oder Tabulatortasten oder andere standardmäßige Ausstiegsmethoden erfordert, wird der Benutzer über die Methode zum Verschieben des Fokus informiert. (Stufe A)
   * 2.1.3 Tastatur (keine Ausnahme): Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für einzelne Tastenanschläge bestimmte Zeiteinteilung erforderlich ist. (Stufe AAA)


## Verantwortung für die Verwendung der Farbe{#use-color-responsibly}

Beim Entwerfen von Formularen für Barrierefreiheit sind einige zusätzliche Richtlinien für die Verwendung von Farbe zu beachten. Designer verwenden Farben, um das Erscheinungsbild von Formularen zu verbessern, indem sie verschiedene Formularkomponenten hervorheben. Eine unsachgemäße Verwendung der Farbe kann jedoch dazu führen, dass Informationen in Ihrem Formular für Menschen mit Behinderungen schwierig oder gar nicht lesbar sind.

### Informationen nicht mit Farbe allein vermitteln

Farben können bestimmte Teile des Formulars hervorheben und erweitern, doch sollten Sie Informationen nicht nur farblich vermitteln.

Jegliche Informationen, die ausschließlich in Farbe vermittelt werden (Farben mit semantischer Bedeutung), sind für blinde Benutzer nicht zugänglich. Dasselbe gilt für Benutzer mit Farbsehmängeln oder Benutzer, die verschiedene Farbschemata verwenden, z. B. einen Farbbildschirm mit hohem Kontrast mit weißem Text oder Vordergrund auf einem schwarzen Hintergrund. Beachten Sie auch, dass Sprachausgaben Farbinformationen nicht automatisch erkennen können.

Abbildung 13 zeigt beispielsweise ein Formularfeld mit einer roten Beschriftung (die über die Palette &quot;Schrift&quot;angegeben wird), um anzugeben, dass das Formularfeld erforderlich ist. In diesem Beispiel ist die Farbe das einzige Zeichen für den Unterschied zwischen erforderlichen und optionalen Eingabefeldern, was es blinden Benutzern oder Benutzern mit bestimmten Arten von Farbblindheit unmöglich macht, sie voneinander zu unterscheiden.

![Verwenden der Farbe allein zur Informationsübermittlung](/help/forms/using/assets/image-13.png)

Abbildung 13: **Verwenden der Farbe allein zur Informationsübermittlung**

Um dieses Problem zu beheben, geben Sie auch den erforderlichen Status des Formulars im Alternativtext des Formularsteuerelements an (wie in Abschnitt 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente). Sie können beispielsweise den Text der Bildschirmlesehilfe auf &quot;Postleitzahl (erforderlich)&quot;setzen. Für Benutzer, bei denen die Farbwiedergabe in bestimmten Kombinationen schwierig ist, wird empfohlen, den Textfeldtyp auf Benutzereingabe - Erforderlich in der Palette &quot;Objekt&quot;festzulegen. Zusätzlich wird ein alternativer Text empfohlen, der anzeigt, dass das Feld erforderlich ist. Alternativ können Sie andere Bezeichnungen als Farbe verwenden, z. B. visueller Text, Textstile und Rahmenstile. Für Benutzer von Bildschirmlesehilfen müssen Sie jedoch weiterhin die erforderlichen Informationen über die Palette &quot;Ein-/Ausgabehilfe&quot;übermitteln.

Beachten Sie außerdem bei der Bereitstellung von Beschreibungen oder Anweisungen für den Formularbenutzer, dass Anweisungen, die nur auf Farbe basieren, für Benutzer mit Sehbehinderung nicht ausreichend sind. Anstelle einer Aussage wie &quot;Klicken Sie auf die grüne Schaltfläche, um fortzufahren&quot;, verwenden Sie beispielsweise eine Textbeschreibung für Aktionen wie &quot;Klicken Sie auf die Schaltfläche Weiter , um fortzufahren&quot;.

>[!NOTE]
> Diese Best Practice verbietet die Verwendung von Farbe nicht. Sie verbietet die Verwendung von Farbe als einziges Mittel zur Vermittlung wichtiger Informationen. Wenn für diese Art von Informationen weiterhin eine visuelle Anzeige gewünscht wird, kann der Designer ein Sternchen oder ein ähnliches visuelles Zeichen verwenden, um die erforderlichen Felder zu kennzeichnen.

### Sicherstellen von ausreichendem Farbkontrast

Viele sehbehinderte Benutzer benötigen einen hohen Kontrast zwischen Text und dem Hintergrund, um Formulare zu lesen. Wenn der Kontrast zwischen Hintergrund- und Vordergrundfarben nicht ausreicht, kann es für einige Benutzer schwierig, wenn nicht gar unmöglich werden, ein Formular zu lesen. Abbildung 14 zeigt ein Beispiel für ein Formular mit unzureichendem Kontrast.

![Ein Formular mit unzureichendem Farbkontrast](/help/forms/using/assets/image-14.png)

Abbildung 14: **Formular mit unzureichendem Farbkontrast**

Es wird dringend empfohlen, die standardmäßige Schriftart- und Hintergrundfarbe zu verwenden: schwarz auf einem weißen Hintergrund. Wenn Sie diese Standardfarben ändern müssen, wählen Sie eine geeignete Kombination aus kontrastreichen Farben. Verwenden Sie entweder eine dunkle Vordergrundfarbe auf einer hellen Hintergrundfarbe oder umgekehrt. Verwenden Sie ein Werkzeug (z. B. den WAT-C-Farbkontrast-Analyzer), um sicherzustellen, dass der Kontrast ausreichend ist.

Mit Adobe Reader und Adobe Acrobat können Benutzer festlegen, ob Farben entsprechend ihren visuellen Anforderungen ersetzt werden müssen. Die Benutzer können ihr eigenes Kontrastschema angeben oder ein vom Betriebssystem bereitgestelltes Schema verwenden. Darüber hinaus verfügen Adobe Reader und Adobe Acrobat über ein eigenes Kontrastschema, das aktiviert werden kann. Damit diese Optionen erfolgreich sind, sollten Sie immer Standardfarben verwenden.

Testen Sie das Formular beim Entwerfen häufig mit einer Farbschema-Einstellung, die der von vielen sehbehinderten Benutzern verwendeten ähnelt, um das Formular auszufüllen. Diese Vorgehensweise hilft Ihnen, Probleme frühzeitig im Designprozess zu erkennen und zu korrigieren.

Recommendations zur Verwendung von Farben:
* Achten Sie darauf, dass keine Informationen verloren gehen, wenn die semantische Farbe nicht sichtbar ist.
* Wenn Sie keine Standardfarben verwenden können, stellen Sie sicher, dass Ihre Farben einen hohen Kontrast aufweisen, z. B. schwarz auf einem hellen (weißen) Hintergrund. Teilsehende Benutzer benötigen im Allgemeinen einen hohen Kontrast zwischen dem Text und seinem Hintergrund, um ihn lesen zu können.
* Testen Sie die Lesbarkeit Ihrer Formulare, indem Sie Ihren Bildschirm sowohl in Windows als auch in Adobe Reader oder Adobe Acrobat auf eine kontrastreiche Anzeige umstellen. Mac OSX bietet nur einen einfachen Graustufenfilter für hohen Kontrast, sodass dies für Tests nicht ausreicht.
* Vermitteln Sie keine Informationen ausschließlich auf der Grundlage der Farbe. Verwenden Sie beispielsweise nicht nur Farbe, um wichtige Textteile hervorzuheben. Verwenden Sie auch andere Hervorhebungsmethoden und Textbeschreibungen.
* Verwenden Sie nicht zu viele Farben, da dies die tatsächlichen Informationen im Inhalt erschwert. Behalten Sie die Lesbarkeit der Informationen immer als oberste Priorität bei, wenn Sie entscheiden, welche Farben verwendet werden sollen.

**Verwandte Checkpoints**
* Abschnitt 508 § 1194.21
   * i) Farbkodierung darf nicht als einziges Mittel zur Informationsübermittlung, zur Angabe einer Aktion, zur Aufforderung einer Antwort oder zur Unterscheidung eines visuellen Elements verwendet werden.
* WCAG 1.0
   * 2.1 Stellen Sie sicher, dass alle mit Farbe vermittelten Informationen auch ohne Farbe verfügbar sind, z. B. aus Kontext oder Markup.
   * 2.2 Stellen Sie sicher, dass die Vordergrund- und Hintergrundfarbkombinationen einen ausreichenden Kontrast bieten, wenn sie von einer Person mit Farbdefiziten angezeigt werden oder auf einem Schwarzweißbildschirm angezeigt werden. [Priorität 2 für Bilder, Priorität 3 für Text] (P2).
* WCAG 2.0
   * 1.4.1 Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel zur Informationsübermittlung, zur Angabe einer Aktion, zur Aufforderung einer Antwort oder zur Unterscheidung eines visuellen Elements verwendet. (Stufe A)
   * 1.4.3 Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1, mit Ausnahme der folgenden: (Level AA)
   * 1.4.6 Kontrast (erweitert): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 7:1, mit Ausnahme der folgenden: (Stufe AAA)


## Überschriftzellen für Tabellen bereitstellen{#provide-heading-cells}

Tabellen sind eine effektive Möglichkeit, Inhalte in barrierefreien Formularen zu organisieren und darzustellen. Bei ordnungsgemäßer Verwendung bieten die Zeilen und Spalten einer Tabelle eine vorhersehbare und konsistente Struktur für Formularinhalte. Wenn ein Benutzer der Bildschirmlesehilfe beispielsweise zu einer Textzeilenzelle navigiert, gibt die Bildschirmlesehilfe die Zellenposition an und liest dann den Zelleninhalt. Die Bildschirmlesehilfe gibt die Zellenposition mithilfe einer Kombination aus Zeilen- und Spaltenüberschriften oder Zeilen- und Spaltennummern an. Da Bildschirmlesehilfen Informationen bereitstellen, die den Benutzer zum Speicherort des Inhalts in der Tabelle ausrichten, wirkt sich das Layout direkt auf die Barrierefreiheit der Tabelle aus.

Sie können die folgenden Rollen für Tabellenelemente beim Erstellen von Tabellen festlegen. Diese Rollen ermöglichen es Sprachausgabeprogrammen, mithilfe spezieller Tastaturbefehle in der Tabellenstruktur zu navigieren, und vermitteln dem Benutzer die Beziehung zwischen Tabellenzellen und den entsprechenden Kopfzeilenzellen.
* Verzeichnis
Weist dem ausgewählten Teilformular die Rolle einer Tabelle zu. Wenn der Benutzer zu diesem Teilformular navigiert, erkennen die meisten Bildschirmlesehilfen es als Tabelle und geben die Anzahl der Zeilen und Spalten an.
* Kopfzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Rolle einer Kopfzeile zu. Wenn Sie den Inhalt einer Textzeilenzelle sprechen, identifizieren die meisten Bildschirmlesehilfen zunächst den Inhalt der entsprechenden Zelle in der Kopfzeile.
* Textzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Rolle einer Textzeile zu. Wenn eine Zelle ein Teilformular enthält, sprechen Bildschirmlesehilfen normalerweise den Inhalt der entsprechenden Zelle in der Kopfzeile, gefolgt von den Feldern im Teilformular.
* Fußzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Fußzeile zu.
* (Keine)
Gibt eine Zeile an, die Informationen über die Tabelle oder ihren Inhalt vermittelt. Die Zeile wird nicht als Teil der Tabelle betrachtet. Die Bildschirmlesehilfe liest jedoch die Inhalte.

Bei ordnungsgemäßer Verwendung bieten Tabellen eine effektive Möglichkeit, tabellarische Informationen zu organisieren und darzustellen. Vermeiden Sie übermäßig komplexe Tabellen wie Tabellen mit verschachtelten Tabellen und Abschnitten.

### Barrierefreies Gestalten einfacher Tabellen

Tabellen mit einfachen Layouts werden empfohlen. Einfache Tabellen beginnen mit einer einzelnen Kopfzeile, gefolgt von den Textzeilen.

Beachten Sie beim Entwerfen einfacher Tabellen für Barrierefreiheit folgende Richtlinien:

* Die Tab-Reihenfolge einer Tabelle ist die geografische Reihenfolge, die mit der des Formulars selbst übereinstimmt. Stellen Sie sicher, dass der Tabelleninhalt so organisiert ist, dass er beim Lesen von links nach rechts und von oben nach unten sinnvoll ist.
* Die meisten Bildschirmlesehilfen interpretieren die erste Zeile einer Tabelle als Kopfzeile. Beim Lesen des Inhalts einer Textzeilenzelle lesen diese Bildschirmlesehilfen zunächst den Inhalt der zugehörigen Kopfzeilenzelle. Stellen Sie sicher, dass der Inhalt in jeder Kopfzeilenzelle den Spalteninhalt sinnvoll beschreibt.
* Vermeiden Sie Zellen, die zwei oder mehr Spalten, verschachtelte Tabellen oder Tabellenabschnitte umfassen. Einige Bildschirmlesehilfen haben Schwierigkeiten, diese Funktionen richtig zu interpretieren, oder können sie möglicherweise nicht verwenden. Wenn beispielsweise eine Zelle in einer Textzeile zwei Spalten umfasst, verweisen Bildschirmlesehilfen beim Lesen der nächsten Zelle in der Zeile möglicherweise nicht auf den richtigen Zelleninhalt in der Kopfzeile.

### Barrierefreies Gestalten komplexer Tabellen

Wenn Sie Tabellen für Barrierefreiheit entwerfen, versuchen Sie, das Tabellenlayout einfach zu halten, wobei eine Kopfzeile gefolgt von Textzeilen folgen muss. Natürlich erfordern manche Inhalte möglicherweise ein komplexeres Tabellenlayout. Beispielsweise müssen Sie möglicherweise eine Zelle verwenden, die sich über mehrere Kopfzeilen erstreckt, um den Inhalt effektiv zu vermitteln.

Sie können komplexe Tabellen erstellen, indem Sie das Tabellenobjekt verwenden oder Teilformularobjekte kombinieren. Mit dem Tabellenobjekt können Sie Funktionen verwenden, die den Designprozess unterstützen sollen, z. B. Optionen zum Einfügen und Ändern der Größe von Spalten und Zeilen.

Mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;können Sie tabellenbezogene Rollen für Teilformulare festlegen, um eine barrierefreie komplexe Tabelle zu erstellen. Je nach Design-Erlebnis und -Voreinstellungen können Sie komplexe Tabellen erstellen, indem Sie Teilformularobjekte kombinieren. Sie können beispielsweise ein Teilformular mit zwei Zeilen erstellen, dieses Teilformular als Kopfzeile für die Tabelle angeben und ein anderes Teilformular für die TabellenTextzeilen angeben.

Wenn Sie zum Erstellen von Tabellen Teilformularobjekte anstelle von Tabellenobjekten verwenden, sind die folgenden zusätzlichen Schritte erforderlich:
* Legen Sie auf der Registerkarte &quot;Teilformular&quot;für jedes Teilformular den Typ Position fest.
* Legen Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;für jedes Teilformular der Tabelle die entsprechende Teilformularrolle fest. Weisen Sie beispielsweise dem Teilformular, das als Tabellenüberschrift verwendet wird, die Rolle &quot;Kopfzeile&quot;zu.
* Weisen Sie für Zeilen, die Informationen über die Tabelle oder ihren Inhalt vermitteln, aber nicht als Teil der Tabelle betrachtet werden, die Teilformularrolle &quot;Ohne&quot;zu. Die Bildschirmlesehilfe liest den Zeileninhalt.

Die von der Bildschirmlesehilfe unterstützten Funktionen bestimmen, welche Informationen für eine komplexe Tabelle gelesen werden. Betrachten Sie beispielsweise eine Tabelle, die eine Kopfzeile und einen Abschnitt mit einer Kopfzeile enthält. Wenn der Benutzer zu einer Textzeilenzelle im Tabellenabschnitt navigiert, lesen Bildschirmlesehilfen normalerweise den folgenden Inhalt in der angegebenen Reihenfolge:
* Inhalt aus der entsprechenden Zelle in der Kopfzeile der Tabelle
* Inhalt aus der entsprechenden Zelle in der Kopfzeile des Abschnitts
* Inhalt aus der ausgewählten Zelle
Einige Bildschirmlesehilfen lesen jedoch möglicherweise keinen Inhalt aus beiden Kopfzeilen.

Erstellen Sie aussagekräftige sichtbare Namen oder Titel für Ihre Tabellen. Sie können einen Tabellennamen als statischen Text in Adobe LiveCycle Designer erstellen und ihn vor der Tabelle platzieren. Sie können eine Tabelle und ihren Namen in einem Teilformular gruppieren. Teilformulare sind besonders nützlich, wenn Sie verknüpfte Objekte in einem Layout kombinieren möchten.

Bei Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe an, welche Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text Sie für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für ein Steuerelement in einer Tabelle verwenden möchten, dürfen Sie keine Beschriftung, keine QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text angeben. Beachten Sie jedoch, dass diese Strategie für Benutzer von Bildschirmlesehilfen nicht immer so eindeutig ist, da Bildschirmlesehilfen die Spaltenüberschrift nur dann mit dem Steuerelement verknüpfen können, wenn sich der Benutzer nicht im Formularinteraktionsmodus der Bildschirmlesehilfe befindet.

**Verwandte Checkpoints**
* Abschnitt 508 § 1194.22
   * g) Für Datentabellen werden Zeilen- und Spaltenüberschriften angegeben.
   * (h) Markup wird verwendet, um Datenzellen und Kopfzeilenzellen für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften zuzuordnen.
* WCAG 1.0
   * 5.1 Identifizieren Sie bei Datentabellen Zeilen- und Spaltenüberschriften (P1).
   * 5.2 Für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften verwenden Sie Markup, um Datenzellen und Kopfzeilenzellen zuzuordnen (P1)
* WCAG 2.0
   * 1.3.1 Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmatisch bestimmt werden oder sind im Text verfügbar. (Stufe A)


## Bereitstellung einer navigierbaren Formularstruktur{#provide-navigable-form}

Wenn ein Formular lang und komplex wird, wird seine Benutzerfreundlichkeit durch die Struktur stark beeinflusst. So wie ein Buch leichter zu verstehen ist, wenn es in Kapitel und Abschnitte unterteilt ist, wird es einfacher, ein Formular zu verwenden, wenn es in Überschriften und Unterüberschriften unterteilt ist. Diese Partitionierung ist besonders für Benutzer von Bildschirmlesehilfen aus den folgenden Gründen nützlich:
* Jede Überschrift teilt dem Benutzer der Bildschirmlesehilfe mit, was im Abschnitt nach der Überschrift zu erwarten ist.
* Bildschirmlesehilfen bieten Verknüpfungen, mit denen schnell zwischen den verschiedenen Überschriften im Formular hin- und hergesprungen werden kann. Außerdem können Benutzer auf eine Liste von Überschriften zugreifen, die einen Überblick über die Dokumentstruktur bietet und eine schnelle Navigation ermöglicht.

Durch die Bereitstellung von Mechanismen, die es Benutzern ermöglichen, zu anderen Bereichen des Formulars zu springen, kann das Formular einfacher werden. Sie können Ihrem Formular mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;in LiveCycle Designer eine Überschriftenstruktur hinzufügen.

### Übersprungmechanismen bereitstellen

Sighted-Benutzer können eine Seite in beliebiger Reihenfolge scannen. Sie können damit beginnen, sich die untere rechte Ecke der Seite anzusehen und den Inhalt rückwärts zu scannen. Der Benutzer der Bildschirmlesehilfe verfügt nicht über diese Option, da die Bildschirmlesehilfe mit dem Lesen der Seite oben links (wie im Quellcode dargestellt) beginnt und sich in einer linearen Reihenfolge durchbewegt. Darüber hinaus kann der sehende Benutzer die Seite nach interessanten Links durchsuchen und sie mit der Maus aktivieren. Ein Benutzer der Bildschirmlesehilfe muss die Seite nacheinander durchlaufen.

Die einfachste und effektivste Methode zur Bereitstellung einer navigierbaren Formularstruktur besteht darin, Strukturüberschriften und ordnungsgemäß definierte Listen im Formular zu verwenden.
Sie können auch Mechanismen bereitstellen, mit denen Benutzer zu anderen Bereichen des Formulars springen können, z. B. durch Hinzufügen von Navigationsschaltflächen am oberen und unteren Rand des Formulars. Am oberen Rand eines Formulars können Sie Schaltflächen wie &quot;Datendatei öffnen&quot;, &quot;Vorherige Seite&quot;und &quot;Nächste Seite&quot;einfügen. Am unteren Rand des Formulars können Sie Schaltflächen wie &quot;Daten speichern&quot;, &quot;E-Mail-Daten&quot;, &quot;Gehe zu Seitenanfang&quot;und &quot;Drucken&quot;einfügen.

Intelligente Felder können das Ausfüllen einiger Formulare erleichtern. Ein Formular für eine Reiseanfrage kann beispielsweise mehrere Zeilen und Spalten von Feldern enthalten. Wenn eine bestimmte Zeile leer ist, kann das Drücken der Tabulatortaste für das letzte Element in dieser Zeile zum nächsten Abschnitt des Formulars springen, anstatt weiterhin durch eine Reihe von Feldern zu springen, die leer bleiben.

### Hinzufügen von Überschriften mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;

Mithilfe der Palette &quot;Ein-/Ausgabehilfe&quot;können Sie Objekten je nach Verwendungszweck des Objekts Rollen zuweisen. Diese Rollen können angewendet werden, um Überschriften auf unterschiedlichen Ebenen zu erstellen.

![Festlegen einer Überschriftenrolle in der Palette &quot;Ein-/Ausgabehilfe&quot;](/help/forms/using/assets/image-15.png)
Abbildung 15: **Festlegen einer Überschriftenrolle in der Palette &quot;Ein-/Ausgabehilfe&quot;**

Führen Sie die folgenden Schritte aus, um eine Überschrift in Ihrem Formular zu erstellen:

1. Identifizieren Sie den Anfang jedes logischen Segments Ihres Formulars mit statischen Textbeschriftungen,
1. Wählen Sie für jede Bezeichnung eine der Überschriftenoptionen in der Palette &quot;Ein-/Ausgabehilfe&quot;als Rolle aus. Die verschiedenen Überschriftenebenen (1 bis 6) ermöglichen es Ihnen, eine Überschriftenstruktur in Ihrem Formular zu erstellen. Beginnen Sie mit Ebene 1 und verwenden Sie dann Ebene 2 und so weiter für verschachtelte Unterabschnitte.

Die meisten Bildschirmlesehilfen ermöglichen es Benutzern, je nach Ebene schnell zwischen Überschriftenelementen zu navigieren. Abbildung 16 zeigt ein Formular, das mithilfe von Überschriften in kleinere Segmente unterteilt ist. In diesem Beispiel wird die folgende Überschriftenstruktur verwendet:

* Überschriftenebene 1: Produktanfrage
   * Überschriftenebene 2: Bestelldetails
      * Überschriftenebene 3: Bereitstellungsoptionen
* Überschriftenebene 2: Zusätzliche Informationen
   * Überschriftenebene 3: Persönliche Daten
   * Überschriftenebene 3: Adresse

![Strukturieren eines Formulars mit Überschriften](/help/forms/using/assets/image-16.png)

Abbildung 16: **Strukturieren eines Formulars mithilfe von Überschriften**

Diese Überschriften sind nur statische Textelemente, denen eine bestimmte Schriftgröße und eine Überschriftenrolle mit der entsprechenden Ebene zugewiesen wurde.

>[!NOTE]
> Wenn Sie einfach das Erscheinungsbild einer Textbeschriftung so ändern, dass sie wie eine Überschrift aussieht, wird sie von Sprachausgaben nicht als Überschrift erkannt. Sie müssen eine Überschriftenrolle anwenden.

Stellen Sie stets sicher, dass die Reihenfolge der Überschriftenebenen logisch ist. So muss beispielsweise ein Unterabschnitt einer Überschrift der Stufe 2 stets eine Überschrift der Stufe 3 sein; beim Markieren von Unterabschnitten sollten Sie Ebenen nie überspringen. Benutzer von Bildschirmlesehilfen verwenden die verschiedenen Ebenen, um ein besseres Verständnis der Formularstruktur zu erhalten. Wenn der Benutzer beispielsweise auf eine Überschrift der Stufe 2 trifft, kann er eine Verknüpfung verwenden, um nach Überschriften der Stufe 3 zu suchen und festzustellen, ob Unterabschnitte vorhanden sind. Wenn Sie Ebenen überspringen, hat der Benutzer Schwierigkeiten, diese Unterabschnitte zu identifizieren.

### Listen markieren

Manchmal kann es auch nützlich sein, dem Formular Listeninhalte hinzuzufügen. Listen sind nützlich, um verwandte Elemente zu gruppieren. Sie ermöglichen es Benutzern von Bildschirmlesehilfen, zu erkennen, wie viele Elemente sich in einer Liste befinden, und schnell vorbei zu navigieren. Wenn Sie Listen richtig markieren, wird die Struktur Ihres Formulars für Benutzer der Sprachausgabe klarer.

Auf der LiveCycle Designer erstellen Sie Listen mithilfe von Teilformularen mit den folgenden Schritten:

1. Wählen Sie ein Teilformular aus, das den Inhalt enthält, der als Listenelemente markiert wird.
1. Wählen Sie in der Palette &quot;Ein-/Ausgabehilfe&quot;die Option &quot;Liste&quot;als Rolle aus.
1. Wählen Sie jedes verschachtelte Teilformular im Teilformular &quot;Liste&quot;aus und legen Sie als Rolle &quot;Listenelement&quot;fest.

>[!NOTE]
> Die Rolle &quot;Listenelement&quot;kann nur einem Teilformular zugewiesen werden, das in einem Teilformular mit der Rolle &quot;Liste&quot;enthalten ist. Sie können Tabellen- oder Tabellenzeilen nicht als Listen- oder Listenelemente definieren. Ein Listenelement kann jedoch eine Tabelle enthalten.

**Verwandte Checkpoints**
* Abschnitt 508 §11934.22
   * o) Es ist ein Verfahren vorzusehen, das es den Nutzern ermöglicht, sich wiederholende Navigationslinks zu überspringen.
* WCAG 1.0
   * 3.5 Verwenden Sie Kopfzeilenelemente, um die Dokumentstruktur zu vermitteln und sie gemäß Spezifikation (P2) zu verwenden.
   * 3.6 Markieren Sie Listen und Listenelemente ordnungsgemäß. (P2).
   * 12.3 Teilen Sie große Informationsblöcke in besser verwaltbare Gruppen auf, wo es sich als normal und angemessen erweist. (P2).
   * 13.3 Informationen über das allgemeine Layout einer Site (z. B. eine Sitemap oder ein Inhaltsverzeichnis) bereitstellen.
   * 13.4 Navigationsmechanismen konsistent nutzen (P2).
* WCAG 2.0
   * 1.3.2 Bedeutungstragende Reihenfolge: Wenn die Reihenfolge, in der Inhalte präsentiert werden, ihre Bedeutung beeinflusst, kann programmatisch eine korrekte Lesesequenz bestimmt werden. (Stufe A)
   * 2.4.1 Blöcke umgehen: Es gibt einen Mechanismus, um Inhaltsblöcke zu umgehen, die auf mehreren Webseiten wiederholt werden. (Stufe A)
   * 2.4.5 Mehrere Methoden: Es gibt mehrere Möglichkeiten, eine Webseite innerhalb eines Satzes von Webseiten zu finden, es sei denn, die Webseite ist das Ergebnis eines Prozesses oder ein Schritt in diesem Prozess. (Stufe AA)
   * 2.4.6 Überschriften und Beschriftungen: Überschriften und Beschriftungen beschreiben ein Thema oder einen Zweck. (Stufe AA)
   * 2.4.10 Abschnittsüberschriften: Abschnittsüberschriften dienen zur Organisation des Inhalts. (Stufe AAA)
   * 3.2.3 Konsistente Navigation: Navigationsmechanismen, die auf mehreren Webseiten innerhalb eines Satzes von Webseiten wiederholt werden, treten jedes Mal, wenn sie wiederholt werden, in derselben relativen Reihenfolge auf, es sei denn, der Benutzer initiiert eine Änderung. (Stufe AA)


## Unterbrechungsfreies Scripting vermeiden{#avoid-disruptive-scripting}

Im Rahmen des Formularentwurfsprozesses können Formularentwickler Skripte verwenden, um ein besseres Benutzererlebnis zu bieten. Sie können Skripten zu den meisten Formularfeldern und -objekten hinzufügen. Beispielsweise können Sie einfache Skripte erstellen, um Werte in einem interaktiven Formular als Reaktion auf Benutzereingaben dynamisch zu aktualisieren.

Beachten Sie beim Erstellen von Skripten für Barrierefreiheit die folgenden allgemeinen Richtlinien:

* Der Formularinhalt sollte keine visuellen Unterbrechungen aufweisen. Vermeiden Sie beispielsweise Funktionen, die dazu führen, dass Inhalte flackern, blinken oder verschieben.
* Stellen Sie sicher, dass Popup-Fenster nur aufgrund von vom Benutzer initiierten Aktionen angezeigt werden. Ebenso dürfen Sie nicht zulassen, dass der aktuelle Fokus des Formulars (die aktuelle Ansicht des Benutzers) geändert oder der Inhalt erneut angezeigt wird, es sei denn, dies wird vom Benutzer initiiert. Wenn der Benutzer beispielsweise Felder in der unteren Hälfte des Formulars ausfüllt, dürfen Sie den Fokus nicht in die linke obere Ecke des Formulars verschieben, es sei denn, der Benutzer wählt die Option, zu dieser Position zu navigieren.
* Benutzer mit Behinderungen benötigen möglicherweise mehr Zeit für die Eingabe in Felder. Legen Sie keine zeitbasierten Antworten für Eingabefelder fest.
* Beachten Sie, dass clientseitige Skripte Bildschirmlesehilfen und Tastaturen beeinträchtigen können, wenn das Skript den Fokus der Clientanwendung ändert. Beispielsweise können die Ereignisse change und mouseEnter bei Verwendung mit Dropdown-Listen oder Listenfeldern zu unerwarteten Aktionen führen. Stellen Sie sicher, dass Ihre clientseitigen Skripte keine Probleme für Benutzer von Bildschirmlesehilfen und nur für Benutzer mit der Tastatur verursachen.
* Benutzer von Hilfstechnologien benötigen manchmal zusätzliche Zeit, um Aufgaben abzuschließen. Zeigen Sie in jedem Fall, in dem eine zeitgesteuerte Routine abläuft, eine zugängliche Nachricht an, um eine Erweiterung zu ermöglichen. Über JavaScript erstellte Warnfelder können mithilfe von Hilfstechnologien verwendet werden. Es kann auch ein neues Fenster mit einer Meldung bereitgestellt werden, in der der Benutzer auf eine bevorstehende Zeitüberschreitung hingewiesen wird.

**Verwandte Checkpoints**:
* Abschnitt 508 § 1194.22
   * (l) Wenn Seiten Skriptsprachen verwenden, um Inhalte anzuzeigen oder Schnittstellenelemente zu erstellen, werden die vom Skript bereitgestellten Informationen mit funktionalem Text identifiziert, der von Hilfstechnologien gelesen werden kann.
   * p) Ist eine zeitgesteuerte Antwort erforderlich, so ist der Benutzer zu benachrichtigen und ihm ausreichend Zeit einzuräumen, um mehr Zeit anzugeben.
* WCAG 1.0
   * 1.4 Synchronisieren Sie für jede zeitbasierte Multimediapräsentation (z. B. für einen Film oder eine Animation) gleichwertige Alternativen (z. B. Beschriftungen oder auditive Beschreibungen der visuellen Spur) mit der Präsentation (P1).
   * 6.2 Stellen Sie sicher, dass Äquivalente für dynamische Inhalte aktualisiert werden, wenn sich der dynamische Inhalt ändert.
   * 6.3 Stellen Sie sicher, dass Seiten verwendet werden können, wenn Skripte, Applets oder andere programmatische Objekte deaktiviert oder nicht unterstützt werden. Ist dies nicht möglich, stellen Sie gleichwertige Informationen auf einer alternativ zugänglichen Seite bereit.
   * 6.5 Stellen Sie sicher, dass dynamische Inhalte zugänglich sind oder eine alternative Darstellung oder Seite (P2) bereitstellen.
   * 8.1 Direkten Zugriff auf programmatische Elemente wie Skripte und Applets oder Kompatibilität mit Hilfstechnologien ermöglichen [Priorität 1, wenn Funktionalität wichtig ist und an anderer Stelle nicht vorgestellt wird], andernfalls (P2).
   * 9.3 Geben Sie für Skripte logische Ereignishandler anstelle geräteabhängiger Ereignishandler (P2) an.
   * 10.1 Solange Benutzeragenten es Benutzern nicht erlauben, erstellte Fenster zu deaktivieren, werden keine Popups oder andere Fenster angezeigt und das aktuelle Fenster wird nicht geändert, ohne den Benutzer darüber zu informieren.
* WCAG 2.0
   * 3.2.1 Bei Fokus: Wenn eine Komponente den Fokus erhält, löst dies keine Änderung des Kontexts aus. (Stufe A)
   * 3.2.2 Bei Eingabe: Wenn Sie die Einstellung einer Komponente der Benutzeroberfläche ändern, wird der Kontext nicht automatisch geändert, es sei denn, dem Benutzer wurde vor Verwendung der Komponente über das Verhalten beraten. (Stufe A)
   * 3.2.5 Änderung bei Anforderung: Kontextänderungen werden nur durch eine Benutzeranfrage initiiert oder es ist ein Mechanismus verfügbar, um solche Änderungen zu deaktivieren. (Stufe AAA)

## Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind.{#ensure-audio-video-accessible}

Wenn Ihre Formulare Audio- oder Videoinhalte enthalten, einschließlich Audio- und Videoclips, müssen Sie sicherstellen, dass dieser Inhalt zugänglich ist. Stellen Sie insbesondere sicher, dass in Formulare integrierte Videoclips Untertitel (manchmal auch als Untertitel bezeichnet) für gehörlose und schwerhörige Benutzer sowie Videobeschreibungen für blinde Benutzer enthalten. Für Audiodateien, die nicht mit Videoinhalten synchronisiert werden, reicht ein einfaches Transkript aus.
Informationen zur Bereitstellung von Untertiteln finden Sie bei Flash-basierten Medien unter [link](/help/forms/using/best-practices-for-creating-forms-in-designer.md) .

**Verwandte Checkpoints**:
* Abschnitt 508 § 1194.22
   * b) Entsprechende Alternativen für alle multimedialen Darstellungen werden mit der Präsentation synchronisiert.
* WCAG 1.0
   * 1.1 Geben Sie für jedes nichttextliche Element ein Textäquivalent an (z. B. über &quot;alt&quot;, &quot;longdesc&quot;oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIF), Applets und programmatische Objekte, ascii-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Sounds (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audio-Tracks von Videos und Video (P1).
   * 1.3 Bis Benutzeragenten automatisch das Textäquivalent eines visuellen Tracks vorlesen können, geben Sie eine auditive Beschreibung der wichtigen Informationen des visuellen Tracks einer Multimedia-Präsentation (P1).
   * 1.4 Synchronisieren Sie für jede zeitbasierte Multimediapräsentation (z. B. für einen Film oder eine Animation) gleichwertige Alternativen (z. B. Beschriftungen oder auditive Beschreibungen der visuellen Spur) mit der Präsentation (P1).
* WCAG 2.0
   * 1.2.1 Nur-Audio und Nur-Video (aufgezeichnet): Für aufgezeichnete Nur-Audio- und aufgezeichnete Nur-Video-Medien ist Folgendes wahr, es sei denn, das Audio oder Video ist eine Medienalternative für Text und ist eindeutig als solche gekennzeichnet: (Level A)
   * 1.2.2 Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, es sei denn, das Medium ist eine Medienalternative für Text und ist als solche eindeutig gekennzeichnet. (Stufe A)
   * 1.2.3 Audiobeschreibung oder Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien oder Audiobeschreibung des aufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, es sei denn, das Medium ist eine Medienalternative für Text und ist als solche eindeutig gekennzeichnet. (Stufe A)
   * 1.2.4 Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt. (Stufe AA)
   * 1.2.5 Audiobeschreibung (aufgezeichnet): Audiobeschreibung wird für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt. (Stufe AA)
   * 1.2.6 Signiersprache (aufgezeichnet): Signiersprachdolmetschen wird für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt. (Stufe AAA)
   * 1.2.7 Erweiterte Audiobeschreibung (aufgezeichnet): Wenn Pausen im Vordergrund nicht ausreichen, um Audiobeschreibungen zu ermöglichen, die den Sinn des Videos vermitteln, wird für alle aufgezeichneten Videoinhalte in synchronisierten Medien eine erweiterte Audiobeschreibung bereitgestellt. (Stufe AAA)
   * 1.2.8 Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien wird für alle aufgezeichneten synchronisierten Medien und für alle aufgezeichneten Nur-Video-Medien bereitgestellt. (Stufe AAA)
   * 1.2.9 Nur-Audio (Live): Eine Alternative für zeitbasierte Medien, die äquivalente Informationen für reinen Live-Audioinhalt präsentieren, wird bereitgestellt. (Stufe AAA)

## Ermitteln Sie die natürliche Sprache und alle Sprachänderungen.{#identify-natural-language}

Formularinhalte werden von Hilfstechnologien gelesen, die sprachspezifische Sprachsynthetiker verwenden. Daher ist es wichtig, die Primärsprache des Formulars richtig zu identifizieren, um sicherzustellen, dass die Formulare in der gewünschten Sprache gelesen werden.

Wenn der Text (oder Alternativtext) in Ihren Formularen in mehr als einer Sprache angezeigt wird, müssen Sie die Bereiche Ihres Formulars identifizieren, in denen ein Wechsel von einer Sprache zur anderen erfolgt.

In LiveCycle Designer wird das Festlegen der Primärsprache erreicht, indem die Eigenschaft &quot;Locale&quot;des Formulars und die Eigenschaft &quot;Locale&quot;für das Teilformular der obersten Ebene festgelegt werden. Um Änderungen an der Primärsprache zu identifizieren, ändern Sie die Locale-Eigenschaft für Objekte, die eine andere Sprache als die Sprache des Formulars verwenden.

So legen Sie die Locale-Eigenschaft eines Formulars fest:
1. Wählen Sie &quot;Datei&quot;> &quot;Formulareigenschaften&quot;und wählen Sie die Registerkarte &quot;Standard&quot;
2. Wählen Sie die entsprechende Sprache für das Gebietsschema des Formulars aus (siehe Abbildung 17)
3. Klicken Sie auf OK

![Ändern des Gebietsschemas für Formulareigenschaften im Dialogfeld &quot;Formulareigenschaften&quot;](/help/forms/using/assets/image-17.png)

Abbildung 17: **Ändern des Gebietsschemas für Formulareigenschaften im Dialogfeld &quot;Formulareigenschaften&quot;**

So legen Sie die Eigenschaft &quot;Local&quot;des Teilformulars der obersten Ebene oder eines Objekts fest, für das eine andere Sprache erforderlich ist:
1. Teilformular oder Objekt der obersten Ebene in der Designansicht auswählen
1. Zeigen Sie die Palette &quot;Objekt&quot;an, indem Sie &quot;Fenster&quot;> &quot;Objekt&quot;auswählen
1. Wählen Sie in der Palette &quot;Objekt&quot;die Registerkarte &quot;Feld&quot;aus und wählen Sie in der Liste &quot;Gebietsschema&quot;die Sprache aus, die für das Objekt verwendet werden soll (siehe Abbildung 18). Beachten Sie beim Anwenden verschiedener Gebietsschemaoptionen auf einzelne Objekte, dass die Objekte in Tabellen und Teilformularen automatisch dieselbe Spracheinstellung wie die Tabellen- und Teilformularobjekte erhalten.

![Ändern des Gebietsschemas eines Objekts](/help/forms/using/assets/image-18.png)

Abbildung 18: **Ändern des Gebietsschemas eines Objekts**

**Verwandte Checkpoints**:
* WCAG 1.0
   * 4.1 Identifizieren Sie eindeutig Änderungen in der natürlichen Sprache des Textes eines Dokuments und von Textäquivalenten (z. B. Beschriftungen).
* WCAG 2.0
   * 3.1.1 Sprache der Seite: Die standardmäßige menschliche Sprache jeder Webseite kann programmatisch bestimmt werden. (Stufe A)
   * 3.1.2 Sprache von Teilen: Die menschliche Sprache jedes Passes oder jeder Wortgruppe im Inhalt kann programmatisch bestimmt werden, mit Ausnahme von Eigennamen, technischen Begriffen, Wörtern unbestimmter Sprache und Wörtern oder Redewendungen, die Teil der Verlaufsform des unmittelbar umliegenden Textes geworden sind. (Stufe AA)
